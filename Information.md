## Is creature present in Alpha?

- You can check the entry, if it's below 3000 or 4000, it was most likely present in 0.5.3

- From 4000 to 5000 it *could be* that they were present in 0.5.3

- Higher than that, most likely not

- 4185 is the highest entry in DBC (taken from CreatureDisplayInfo.dbc)

  

## Clients

- **Alpha 0.5.3** https://archive.org/download/World_of_Warcraft_Client_and_Installation_Archive/ISO/WoW-0.5.3.3368_install_enUS.iso

- **Classic 1.12.1** https://www.dkpminus.com/blog/vanilla-wow-download-1-12-1-client/

- **Archive** https://archive.org/download/World_of_Warcraft_Client_and_Installation_Archive/ISO/

- **Archive** https://wowdl.net/fichiers/clients

- **Linux client** https://www.youtube.com/watch?v=a5JuVccgXOw

  - https://discord.com/channels/628574828038717470/628574828538101800/720220894190108683
  
  

### Client modifications and dev mode

- **DarkModeMod** https://www.ownedcore.com/forums/world-of-warcraft/world-of-warcraft-model-editing/599581-dark-nights-mod-vanilla-1-12-1-a.html

- **Moded 0.5.3 client** http://www.mediafire.com/file/wjbk1ovyyb6ry7l/Mods.zip/file

- **WTF folder** https://cdn.discordapp.com/attachments/628575819496947712/708419490743976013/WTF.7z

- **Old addons archive** https://www.fukt.bsnet.se/~k/wow/cosmos/oldcosmos/

  

  

##  Emulators/ sandboxes (old)

- https://www.ownedcore.com/forums/world-of-warcraft/world-of-warcraft-emulator-servers/235886-history-of-wow-emulation.html

- https://github.com/barncastle/Alpha-WoW/

- https://github.com/mynew6/wowdaemon-reborn?files=1
- https://github.com/barncastle/AIO-Sandbox
- https://github.com/SSandbox/SSandbox/releases/tag/v0.1-alpha
- https://github.com/zdroid9770/ArctiumAlpha (old alpha server)



## Graphics

- **Old fansite kit** http://web.archive.org/web/20060427041033/http://download.blizzard.com:80/pub/wow/other/fansite_kit.zip ( )
- **Icons used in Alpha** https://cdn.discordapp.com/attachments/628575889176920064/697969053435822150/alphaicons.7z
-  **10 things never added** https://www.youtube.com/watch?v=0TNhhKMSaz4
-  **Alpha display ID** https://drive.google.com/uc?export=download&id=1zS-qk0awRK6tU3nAK3TEOL2hV39i-Tme
- **Alpha Maps** https://www.dropbox.com/s/pzzxg7eycpw63fi/4x_upscale_053_worldmaps-rebuild.zip?dl=0



## Interface

Example structure for Interface. To add anything you need to edit FrameXML.toc the path MUST start with Interface etc. 

```bash
  Interface
  └── FrameXML
      ├── FrameXML.toc
      ├── QATests
      │   ├── QAMenu.lua
      │   ├── QAMenu.xml
      │   ├── QAMenu_ItemTests.lua
      │   ├── QAMenu_ReloadUI.lua
      │   ├── QAMenu_SpellTests.lua
      │   └── QAMenu_UnitTests.lua
      └── UIOverhaul
          ├── README.md
          ├── UIOverhaul.lua
          └── UIOverhaul.xml
```



## Linux commands

```Bash
netstat -tulpn # show all open ports and which program using them
```



## Resourses

Places to find information about creatures and NPC's

- [Alpha-Project Archive](https://github.com/The-Alpha-Project/Alpha-Project-Archive)
- [Web Archive - Allakhazam](https://web.archive.org/web/20041114104933/http://wow.allakhazam.com/db/mob.html?wmob=1752) 
  
  - Replace the number in `wmob` with the mob entry you wanna check
- [wowhead classic](https://classic.wowhead.com/npc=)
- [WoW.tools](https://wow.tools/)
- https://classicdb.ch/?spell=10318
- https://www.mediafire.com/file/vl4a5qe843mz5e0/WoW_Visual_Database_Beta.zip/file



## Other

```wow
/script ChatFrame:AddMessage(UnitHealth("player"))
```

- https://www.hashgenerator.de/
- [wow developing console](https://www.ownedcore.com/forums/world-of-warcraft/world-of-warcraft-guides/156999-guide-opening-wow-developers-console.html?)
- [old wow commands](https://web.archive.org/web/20040603040959/http://www.wowforge.net/view.php?post=21326)
- https://www.markdownguide.org/tools/github-pages/ - markdown guide
- https://www.youtube.com/watch?v=9hIShZxAJ-Q 21 wow music
- https://cdn.discordapp.com/attachments/628575819496947712/825198018700640276/Cosmos_Alpha_Interface_2004_10_05.zip
- https://www.amazon.com/WoW-Diary-Journal-Computer-Development/dp/B07LB927QF
- https://www.mangosrumors.org/



```Bash
 ctrl + y - statistic window in client
 save in wow-console save player
```



## Programs

- [WDBX.Editor](https://github.com/WowDevTools/WDBXEditor) - edit DB Blizzard client DB files
- [wow-mdx-viewer-win32-x64](https://github.com/barncastle/wow-mdx-viewer) - model viewer
- [mpqeditor_en](https://www.softpedia.com/get/Programming/File-Editors/Ladik-s-MPQ-Editor.shtml) - Access, manage and edit MPQ archives
- https://github.com/mjollna-wow/gillijimproject
- https://wowdev.wiki/MDX
- https://github.com/barncastle/WoWFormatParser
- https://github.com/barncastle/MDX-Parser
- https://github.com/elishacloud/dxwrapper
- https://github.com/noggaholic/bugcraft-studio
- https://model-changing.net/files/file/123-wow-alpha-mdx-obj-converterviewer/
- http://www.zezula.net/en/mpq/download.html
- https://games.softpedia.com/get/Tools/3D-Analyze.shtml



### Other

**Dia Diagram Editor** http://dia-installer.de/index.html.en

**editor** https://atom.io/

**markdown editor** https://typora.io/



## Programming resources

- https://wowdev.wiki/Alpha
- https://cdn.discordapp.com/attachments/628575889176920064/700460386742173716/Wow_15662_OSX.7z (cataclysm 4.1.0 mac, all functions named)
- https://cdn.discordapp.com/attachments/628575889176920064/700460261592662086/Wow_15662_OSX.7z (pandaria beta, with all functions named)
- https://cdn.discordapp.com/attachments/628575889176920064/700456011278057472/export.h (export.h all structures/classes from alpha, 34k lines)
- https://cdn.discordapp.com/attachments/628575889176920064/700455124706918510/PacketStructures.h (packet structure leak from wod)
- http://www.bloodwinterclan.com/forums/viewtopic.php?t=2925 (patch notes 0.5.3)
- [wow roadmap](https://i.gyazo.com/dc3d9382c8f881d48dc6282acac8c098.png)
- http://nyarly.fr/WoWExplore/alphawdt/index.php



## Python

- **Discord bot** https://realpython.com/how-to-make-a-discord-bot-python/
- **SQLAchamy** https://hackersandslackers.com/python-database-management-sqlalchemy
- **Networking** https://docs.python.org/3/library/struct.html#byte-order-size-and-alignment
- **Old Python emulator** https://github.com/FreakX/FrostCoreOldPython
- **Pywowlib** https://github.com/WowDevTools/pywowlib?files=1



## Windows

- https://stackoverflow.com/q/48198/4208583 (open ports in windows)

- https://www.howtogeek.com/howto/28609/how-can-i-tell-what-is-listening-on-a-tcpip-port-in-windows/

  

## WTF



- you can add realmlist.wtf to wtf dir

  - set realmlist <address>

- config.wtf

  - SET realmName "alphacore"
  - SET realmList "localhost"
  - SET realmAddress "192.168.1.10"

