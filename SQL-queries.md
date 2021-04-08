```sql
-- Get spawn info about a creature, .cinfo guid is equal to spawn_id
select * from spawns_creatures where spawn_id = '79670'; -- One guard in SW

-- Get info about creature group (hp, level, speed etc.)
-- Stormwind City Guards
-- 68 Can be used in wowhead, Allakhazam
select * from creature_template where entry = '68';
-- This is the name over the NPC
select * from creature_template where name = 'Stormwind City Guard'; 

-- Scale etc. ID is uqyal to display_id1 from creature_template.
-- creature still spawn if it's missing an ID here.
select * from CreatureDisplayInfo where ID = '3167';
```





## Display model (SQL)

  - To prevent creatures (and gobjects) from spawning you can set `ignored = 1` in `spawns_creatures` or `spawns_gameobjects`
  - .cinfo - guid is same as spawn_id in spawns_creature
  - spawn_entry1 (spawns_creature) is equal to entry (creature_template)
  - ID (CreatureDisplayInfo) is equal to display_id1 (creature_template)


