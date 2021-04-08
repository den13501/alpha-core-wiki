A very simple way to backup your database in Debian is to use cronjob. Debian got 4 cronjob catalogs. **cron.hourly**, **cron.daily**, **cron.weekly**, **cron.monthly** or you can write your own cronjob with crontab. To run a script regularly, simply add it to any of the folders I listed. One remark, don't use any file ending or the script will be ignored. 



Below is a script for backing up all databases from one MySQL user. So just create the file and add it to any cron directory. Don't forget to run **chmod + <script name>**.

```bash
#!/bin/sh

USER=""
PASSWORD=""
HOST="localhost"
MYSQL="$(which mysql)"
MYSQLDUMP="$(which mysqldump)"
OUTPUT_DIR=""

dd=`date +_%Y%m%d`

DBS="$($MYSQL -u $USER -h $HOST -p$PASSWORD -Bse 'show databases')"
for db in $DBS
do
    if [ $db != "information_schema" ]; then
  FILE=$OUTPUT_DIR/$db$dd.sql.gz
        mysqldump -u $USER -h $HOST -p$PASSWORD --skip-lock-tables $db | gzip > $FILE
    fi
done

# Delete all backups older than 7 days
find $OUTPUT_DIR -mtime +7 -exec rm -f {} \;
```



The above script only saves it locally, it won't do any good if the computer crashes and your hard drives get corrupted. But luckily it's simple to save files on another computer. I guess you could use dropbox and things alike, but if you got another linux computer we can use scp. 



First you need to create a key file, because we want to automate this.

```Bash
ssh-keygen -t rsa
```

Now we got a keyfile  **~/.ssh/id_rsa** remember to run the command on the user which gonna be sending the files. **Don't use root**. 



Now you can create a file and add it to a cronjob. Just remember to check if the user got access to the remote machine, and if you got write permission on the remote machine.

```Bash
#!/bin/sh

HOST=""
USER=""
KEYFILE=""
BACKUP_DIR=""
REMOTE_DIR=""
PORT=""

# copy entire directory to a remote host.
scp -v -P $PORT -i $KEYFILE -r $BACKUP_DIR $USER@$HOST:$REMOTE_DIR
```