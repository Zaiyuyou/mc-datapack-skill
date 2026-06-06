# Java Edition data values

From Minecraft Wiki

[Jump to navigation](#mw-head)
[Jump to search](#searchInput)

![](/images/Disambig_color.svg?2db52) This article is about values from *Minecraft: Java Edition* since Java Edition 1.13. For values until Java Edition 1.12.2, see [Java Edition pre-flattening data values](https://minecraft.wiki/w/Java_Edition_pre-flattening_data_values "Java Edition pre-flattening data values"). For values from Classic, see [Java Edition Classic data values](https://minecraft.wiki/w/Java_Edition_Classic_data_values "Java Edition Classic data values"). For values from Indev, see [Java Edition Indev data values](https://minecraft.wiki/w/Java_Edition_Indev_data_values "Java Edition Indev data values").

[![](/images/Information_icon.svg?15c1c)](https://minecraft.wiki/w/File%3AInformation_icon.svg "File:Information icon.svg")

This feature is exclusive to [*Java Edition*](https://minecraft.wiki/w/Java_Edition "Java Edition").

These **data values** refer to the different types of blocks, items and other features on *[Java Edition](https://minecraft.wiki/w/Java_Edition "Java Edition")* and are used in many places in *Minecraft*. [Block IDs](#Blocks) are used to define blocks placed in the world. [Item IDs](#Items) are valid only for items (including items in chests and items dropped in the world). All block IDs that do not have a gray background in this page are also valid item IDs. There are also [entity IDs](#Entities) for entities such as mobs and projectiles.

[ ]

## Contents

- [Java Edition data values](#java-edition-data-values)
  - [Contents](#contents)
  - [IDs](#ids)
    - [Blocks](#blocks)
    - [Fluids](#fluids)
    - [Items](#items)
    - [Entities](#entities)
    - [Effects](#effects)
    - [Enchantments](#enchantments)
    - [Biomes](#biomes)
    - [Particles](#particles)
    - [Dimensions](#dimensions)
    - [Chunk generators](#chunk-generators)
    - [Biome sources](#biome-sources)
    - [Structures](#structures)
    - [Features](#features)
  - [Block states](#block-states)
  - [Protocol and data versions](#protocol-and-data-versions)
  - [Navigation](#navigation)
  - [Navigation menu](#navigation-menu)
    - [Personal tools](#personal-tools)
    - [associated-pages](#associated-pages)
    - [Views](#views)

## IDs


These IDs are in the [resource location](https://minecraft.wiki/w/Resource_location "Resource location") format, with their [`minecraft` namespace](https://minecraft.wiki/w/Resource_location#minecraft_namespace "Resource location") omitted. The game accepts these [resource locations](https://minecraft.wiki/w/Resource_location "Resource location") either with or without the `minecraft:` prefix.

### Blocks

Main article: [Java Edition data values/Blocks](https://minecraft.wiki/w/Java_Edition_data_values/Blocks "Java Edition data values/Blocks")

[[edit](https://minecraft.wiki/w/Special%3AEditPage/Java_Edition_data_values/Blocks "Special:EditPage/Java Edition data values/Blocks")]

### Fluids


| Fluid | [Resource location](https://minecraft.wiki/w/Resource_location "Resource location") |
| --- | --- |
| [Empty](https://minecraft.wiki/w/Air "Air") | `empty` |
| [![](/images/thumb/Lava_JE19.gif/30px-Lava_JE19.gif?792cb)](https://minecraft.wiki/w/File%3ALava_JE19.gif) [Flowing Lava](https://minecraft.wiki/w/Flowing_Lava "Flowing Lava") | `flowing_lava` |
| [![](/images/thumb/Water_JE16.png/30px-Water_JE16.png?29c5b)](https://minecraft.wiki/w/File%3AWater_JE16.png) [Flowing Water](https://minecraft.wiki/w/Flowing_Water "Flowing Water") | `flowing_water` |
| [![](/images/thumb/Lava_JE19.gif/30px-Lava_JE19.gif?792cb)](https://minecraft.wiki/w/File%3ALava_JE19.gif) [Lava](https://minecraft.wiki/w/Lava "Lava") | `lava` |
| [![](/images/thumb/Water_JE16.png/30px-Water_JE16.png?29c5b)](https://minecraft.wiki/w/File%3AWater_JE16.png) [Water](https://minecraft.wiki/w/Water "Water") | `water` |

### Items

Main article: [Java Edition data values/Items](https://minecraft.wiki/w/Java_Edition_data_values/Items "Java Edition data values/Items")

[[edit](https://minecraft.wiki/w/Special%3AEditPage/Java_Edition_data_values/Items "Special:EditPage/Java Edition data values/Items")]

### Entities

Main article: [Java Edition data values/Entities](https://minecraft.wiki/w/Java_Edition_data_values/Entities "Java Edition data values/Entities")

[[edit](https://minecraft.wiki/w/Special%3AEditPage/Java_Edition_data_values/Entities "Special:EditPage/Java Edition data values/Entities")]

### Effects

Main article: [Java Edition data values/Effects](https://minecraft.wiki/w/Java_Edition_data_values/Effects "Java Edition data values/Effects")

[[edit](https://minecraft.wiki/w/Special%3AEditPage/Java_Edition_data_values/Effects "Special:EditPage/Java Edition data values/Effects")]

### Enchantments


| Enchantment | [Resource location](https://minecraft.wiki/w/Resource_location "Resource location") |
| --- | --- |
| [Aqua Affinity](https://minecraft.wiki/w/Aqua_Affinity "Aqua Affinity") | `aqua_affinity` |
| [Bane of Arthropods](https://minecraft.wiki/w/Bane_of_Arthropods "Bane of Arthropods") | `bane_of_arthropods` |
| [Curse of Binding](https://minecraft.wiki/w/Curse_of_Binding "Curse of Binding") | `binding_curse` |
| [Blast Protection](https://minecraft.wiki/w/Blast_Protection "Blast Protection") | `blast_protection` |
| [Breach](https://minecraft.wiki/w/Breach "Breach") | `breach` |
| [Channeling](https://minecraft.wiki/w/Channeling "Channeling") | `channeling` |
| [Density](https://minecraft.wiki/w/Density "Density") | `density` |
| [Depth Strider](https://minecraft.wiki/w/Depth_Strider "Depth Strider") | `depth_strider` |
| [Efficiency](https://minecraft.wiki/w/Efficiency "Efficiency") | `efficiency` |
| [Feather Falling](https://minecraft.wiki/w/Feather_Falling "Feather Falling") | `feather_falling` |
| [Fire Aspect](https://minecraft.wiki/w/Fire_Aspect "Fire Aspect") | `fire_aspect` |
| [Fire Protection](https://minecraft.wiki/w/Fire_Protection "Fire Protection") | `fire_protection` |
| [Flame](https://minecraft.wiki/w/Flame "Flame") | `flame` |
| [Fortune](https://minecraft.wiki/w/Fortune "Fortune") | `fortune` |
| [Frost Walker](https://minecraft.wiki/w/Frost_Walker "Frost Walker") | `frost_walker` |
| [Impaling](https://minecraft.wiki/w/Impaling "Impaling") | `impaling` |
| [Infinity](https://minecraft.wiki/w/Infinity "Infinity") | `infinity` |
| [Knockback](https://minecraft.wiki/w/Knockback "Knockback") | `knockback` |
| [Looting](https://minecraft.wiki/w/Looting "Looting") | `looting` |
| [Loyalty](https://minecraft.wiki/w/Loyalty "Loyalty") | `loyalty` |
| [Luck of the Sea](https://minecraft.wiki/w/Luck_of_the_Sea "Luck of the Sea") | `luck_of_the_sea` |
| [Lunge](https://minecraft.wiki/w/Lunge "Lunge") | `lunge` |
| [Lure](https://minecraft.wiki/w/Lure "Lure") | `lure` |
| [Mending](https://minecraft.wiki/w/Mending "Mending") | `mending` |
| [Multishot](https://minecraft.wiki/w/Multishot "Multishot") | `multishot` |
| [Piercing](https://minecraft.wiki/w/Piercing "Piercing") | `piercing` |
| [Power](https://minecraft.wiki/w/Power "Power") | `power` |
| [Projectile Protection](https://minecraft.wiki/w/Projectile_Protection "Projectile Protection") | `projectile_protection` |
| [Protection](https://minecraft.wiki/w/Protection "Protection") | `protection` |
| [Punch](https://minecraft.wiki/w/Punch "Punch") | `punch` |
| [Quick Charge](https://minecraft.wiki/w/Quick_Charge "Quick Charge") | `quick_charge` |
| [Respiration](https://minecraft.wiki/w/Respiration "Respiration") | `respiration` |
| [Riptide](https://minecraft.wiki/w/Riptide "Riptide") | `riptide` |
| [Sharpness](https://minecraft.wiki/w/Sharpness "Sharpness") | `sharpness` |
| [Silk Touch](https://minecraft.wiki/w/Silk_Touch "Silk Touch") | `silk_touch` |
| [Smite](https://minecraft.wiki/w/Smite "Smite") | `smite` |
| [Soul Speed](https://minecraft.wiki/w/Soul_Speed "Soul Speed") | `soul_speed` |
| [Sweeping Edge](https://minecraft.wiki/w/Sweeping_Edge "Sweeping Edge") | `sweeping_edge` |
| [Swift Sneak](https://minecraft.wiki/w/Swift_Sneak "Swift Sneak") | `swift_sneak` |
| [Thorns](https://minecraft.wiki/w/Thorns "Thorns") | `thorns` |
| [Unbreaking](https://minecraft.wiki/w/Unbreaking "Unbreaking") | `unbreaking` |
| [Curse of Vanishing](https://minecraft.wiki/w/Curse_of_Vanishing "Curse of Vanishing") | `vanishing_curse` |
| [Wind Burst](https://minecraft.wiki/w/Wind_Burst "Wind Burst") | `wind_burst` |

### Biomes

Main article: [Java Edition data values/Biomes](https://minecraft.wiki/w/Java_Edition_data_values/Biomes "Java Edition data values/Biomes")

[[edit](https://minecraft.wiki/w/Special%3AEditPage/Java_Edition_data_values/Biomes "Special:EditPage/Java Edition data values/Biomes")]

### Particles

Main article: [Java Edition data values/Particles](https://minecraft.wiki/w/Java_Edition_data_values/Particles "Java Edition data values/Particles")

[[edit](https://minecraft.wiki/w/Special%3AEditPage/Java_Edition_data_values/Particles "Special:EditPage/Java Edition data values/Particles")]

### Dimensions


| Dimension | [Resource location](https://minecraft.wiki/w/Resource_location "Resource location") | Numeric ID |
| --- | --- | --- |
| ![EnvSprite overworld.png: Sprite image for overworld in Minecraft](/images/EnvSprite_overworld.png?1a94a) [Overworld](https://minecraft.wiki/w/Overworld "Overworld") | `overworld` | 0 |
| ![EnvSprite the-nether.png: Sprite image for the-nether in Minecraft](/images/EnvSprite_the-nether.png?68bec) [The Nether](https://minecraft.wiki/w/The_Nether "The Nether") | `the_nether` | -1 |
| ![EnvSprite the-end.png: Sprite image for the-end in Minecraft](/images/EnvSprite_the-end.png?95a60) [The End](https://minecraft.wiki/w/The_End "The End") | `the_end` | 1 |

### Chunk generators


Main article: [Dimension definition § Generator types](https://minecraft.wiki/w/Dimension_definition#Generator_types "Dimension definition")

Used for creating [custom dimension](https://minecraft.wiki/w/Custom_dimension "Custom dimension"), [Single Biome](https://minecraft.wiki/w/Single_Biome "Single Biome") world type, and internally when generating any world.

| [Resource location](https://minecraft.wiki/w/Resource_location "Resource location") | Image |
| --- | --- |
| `noise` | [![](/images/thumb/Plains_tree.png/150px-Plains_tree.png?c7970)](https://minecraft.wiki/w/File%3APlains_tree.png) |
| `flat` | [![](/images/thumb/Default_Superflat_world.png/150px-Default_Superflat_world.png?a0fc8)](https://minecraft.wiki/w/File%3ADefault_Superflat_world.png) |
| `debug` | [![](/images/thumb/Debug_world_preset.png/150px-Debug_world_preset.png?4753d)](https://minecraft.wiki/w/File%3ADebug_world_preset.png) |

### Biome sources


Main article: [Dimension definition § Biome sources](https://minecraft.wiki/w/Dimension_definition#Biome_sources "Dimension definition")

Used for creating custom dimension, Single Biome world type, and internally when generating any world.

| [Resource location](https://minecraft.wiki/w/Resource_location "Resource location") | Image |
| --- | --- |
| `fixed` | [![](/images/thumb/Voidland.png/150px-Voidland.png?edf31)](https://minecraft.wiki/w/File%3AVoidland.png) |
| `checkerboard` | [![](/images/thumb/Checkerboard_Buffet.png/150px-Checkerboard_Buffet.png?26ded)](https://minecraft.wiki/w/File%3ACheckerboard_Buffet.png) |
| `the_end` | [![](/images/thumb/EnderIslandsRender.jpg/150px-EnderIslandsRender.jpg?6dd63)](https://minecraft.wiki/w/File%3AEnderIslandsRender.jpg) |
| `multi_noise` | This one is very complicated and can't be shown clearly just with a single image |

### Structures


| Name | [Resource location](https://minecraft.wiki/w/Resource_location "Resource location") |
| --- | --- |
| [Jungle pyramid](https://minecraft.wiki/w/Jungle_pyramid "Jungle pyramid") | `jungle_pyramid` |
| [Plains](https://minecraft.wiki/w/Plains "Plains") [Village](https://minecraft.wiki/w/Village "Village") | `village_plains` |
| [Snowy](https://minecraft.wiki/w/Snowy_Plains "Snowy Plains") [Village](https://minecraft.wiki/w/Village "Village") | `village_snowy` |
| [Savanna](https://minecraft.wiki/w/Savanna "Savanna") [Village](https://minecraft.wiki/w/Village "Village") | `village_savanna` |
| [Desert](https://minecraft.wiki/w/Desert "Desert") [Village](https://minecraft.wiki/w/Village "Village") | `village_desert` |
| [Taiga](https://minecraft.wiki/w/Taiga "Taiga") [Village](https://minecraft.wiki/w/Village "Village") | `village_taiga` |
| [End City](https://minecraft.wiki/w/End_City "End City") | `end_city` |
| [Ruined Portal](https://minecraft.wiki/w/Ruined_Portal "Ruined Portal") | `ruined_portal` |
| [Desert](https://minecraft.wiki/w/Desert "Desert") [Ruined Portal](https://minecraft.wiki/w/Ruined_Portal "Ruined Portal") | `ruined_portal_desert` |
| [Jungle](https://minecraft.wiki/w/Jungle "Jungle") [Ruined Portal](https://minecraft.wiki/w/Ruined_Portal "Ruined Portal") | `ruined_portal_jungle` |
| [Mountain](https://minecraft.wiki/w/Windswept_Hills "Windswept Hills") [Ruined Portal](https://minecraft.wiki/w/Ruined_Portal "Ruined Portal") | `ruined_portal_mountain` |
| [Nether](https://minecraft.wiki/w/The_Nether "The Nether") [Ruined Portal](https://minecraft.wiki/w/Ruined_Portal "Ruined Portal") | `ruined_portal_nether` |
| [Ocean](https://minecraft.wiki/w/Ocean "Ocean") [Ruined Portal](https://minecraft.wiki/w/Ruined_Portal "Ruined Portal") | `ruined_portal_ocean` |
| [Swamp](https://minecraft.wiki/w/Swamp "Swamp") [Ruined Portal](https://minecraft.wiki/w/Ruined_Portal "Ruined Portal") | `ruined_portal_swamp` |
| [Igloo](https://minecraft.wiki/w/Igloo "Igloo") | `igloo` |
| [Stronghold](https://minecraft.wiki/w/Stronghold "Stronghold") | `stronghold` |
| [Bastion Remnant](https://minecraft.wiki/w/Bastion_Remnant "Bastion Remnant") | `bastion_remnant` |
| [Desert pyramid](https://minecraft.wiki/w/Desert_pyramid "Desert pyramid") | `desert_pyramid` |
| [Nether Fossil](https://minecraft.wiki/w/Nether_Fossil "Nether Fossil") | `nether_fossil` |
| [Buried Treasure](https://minecraft.wiki/w/Buried_Treasure "Buried Treasure") | `buried_treasure` |
| [Woodland Mansion](https://minecraft.wiki/w/Woodland_Mansion "Woodland Mansion") | `mansion` |
| [Shipwreck](https://minecraft.wiki/w/Shipwreck "Shipwreck") | `shipwreck` |
| Beached shipwreck | `shipwreck_beached` |
| [Ocean Monument](https://minecraft.wiki/w/Ocean_Monument "Ocean Monument") | `monument` |
| [Swamp hut](https://minecraft.wiki/w/Swamp_hut "Swamp hut") | `swamp_hut` |
| [Nether Fortress](https://minecraft.wiki/w/Nether_Fortress "Nether Fortress") | `fortress` |
| [Pillager Outpost](https://minecraft.wiki/w/Pillager_Outpost "Pillager Outpost") | `pillager_outpost` |
| [Warm](https://minecraft.wiki/w/Ocean#Warm_Ocean "Ocean") [Ocean Ruins](https://minecraft.wiki/w/Ocean_Ruins "Ocean Ruins") | `ocean_ruin_warm` |
| [Cold](https://minecraft.wiki/w/Ocean#Cold_Ocean "Ocean") [Ocean Ruins](https://minecraft.wiki/w/Ocean_Ruins "Ocean Ruins") | `ocean_ruin_cold` |
| [Mineshaft](https://minecraft.wiki/w/Mineshaft "Mineshaft") | `mineshaft` |
| [Badlands](https://minecraft.wiki/w/Badlands "Badlands") [Mineshaft](https://minecraft.wiki/w/Mineshaft "Mineshaft") | `mineshaft_mesa` |
| [Ancient City](https://minecraft.wiki/w/Ancient_City "Ancient City") | `ancient_city` |
| [Trail Ruins](https://minecraft.wiki/w/Trail_Ruins "Trail Ruins") | `trail_ruins` |
| [Trial Chambers](https://minecraft.wiki/w/Trial_Chambers "Trial Chambers") | `trial_chambers` |

### Features


:   | Feature | [Resource location](https://minecraft.wiki/w/Resource_location "Resource location") |
    | --- | --- |
    | [Acacia](https://minecraft.wiki/w/Acacia "Acacia") tree | `acacia` |
    | [Amethyst geode](https://minecraft.wiki/w/Amethyst_Geode "Amethyst Geode") | `amethyst_geode` |
    | [Azalea tree](https://minecraft.wiki/w/Azalea_tree "Azalea tree") | `azalea_tree` |
    | [Bamboo](https://minecraft.wiki/w/Bamboo "Bamboo") (no podzol) | `bamboo_no_podzol` |
    | Bamboo (have podzol) | `bamboo_some_podzol` |
    | Bamboo [jungle trees](https://minecraft.wiki/w/Jungle_tree "Jungle tree") | `bamboo_vegetation` |
    | [Basalt](https://minecraft.wiki/w/Basalt "Basalt") [blobs](https://minecraft.wiki/w/Blob "Blob") in [netherrack](https://minecraft.wiki/w/Netherrack "Netherrack") | `basalt_blobs` |
    | [Basalt pillar](https://minecraft.wiki/w/Basalt_pillar "Basalt pillar") | `basalt_pillar` |
    | [Birch](https://minecraft.wiki/w/Birch "Birch") tree | `birch` |
    | Birch tree (0.2% bee nest) | `birch_bees_0002` |
    | Birch tree (2% bee nest) | `birch_bees_002` |
    | Birch tree (5% bee nest) | `birch_bees_005` |
    | Birch trees ([old growth birch forest](https://minecraft.wiki/w/Birch_Forest#Old_Growth_Birch_Forest "Birch Forest")) | `birch_tall` |
    | [Blackstone](https://minecraft.wiki/w/Blackstone "Blackstone") [blobs](https://minecraft.wiki/w/Blob "Blob") in [netherrack](https://minecraft.wiki/w/Netherrack "Netherrack") | `blackstone_blobs` |
    | [Blue ice](https://minecraft.wiki/w/Blue_Ice "Blue Ice") patch | `blue_ice` |
    | [Bonus chest](https://minecraft.wiki/w/Bonus_Chest "Bonus Chest") | `bonus_chest` |
    | [Cave vines](https://minecraft.wiki/w/Glow_Berries "Glow Berries") | `cave_vine` |
    | Cave vines in moss | `cave_vine_in_moss` |
    | [Cherry](https://minecraft.wiki/w/Cherry "Cherry") tree | `cherry` |
    | Cherry tree (5% bee nest) | `cherry_bees_005` |
    | [Chorus plant](https://minecraft.wiki/w/Chorus_plant "Chorus plant") | `chorus_plant` |
    | Clay pool with [dripleaves](https://minecraft.wiki/w/Dripleaf "Dripleaf") | `clay_pool_with_dripleaves` |
    | Clay with dripleaves | `clay_with_dripleaves` |
    | [Crimson forest](https://minecraft.wiki/w/Crimson_Forest "Crimson Forest") vegetation | `crimson_forest_vegetation` |
    | Crimson forest vegetation (grown from [bone meal](https://minecraft.wiki/w/Bone_Meal "Bone Meal")) | `crimson_forest_vegetation_bonemeal` |
    | [Huge crimson fungus](https://minecraft.wiki/w/Huge_fungus "Huge fungus") | `crimson_fungus` |
    | Huge crimson fungus (planted) | `crimson_fungus_planted` |
    | [Dark forest](https://minecraft.wiki/w/Dark_Forest "Dark Forest") trees and [huge mushrooms](https://minecraft.wiki/w/Huge_mushroom "Huge mushroom") | `dark_forest_vegetation` |
    | [Dark oak](https://minecraft.wiki/w/Dark_oak "Dark oak") tree | `dark_oak` |
    | [Basalt](https://minecraft.wiki/w/Basalt "Basalt") delta | `delta` |
    | [Desert well](https://minecraft.wiki/w/Desert_Well "Desert Well") | `desert_well` |
    | [Clay](https://minecraft.wiki/w/Clay "Clay") [disk](https://minecraft.wiki/w/Disk "Disk") | `disk_clay` |
    | [Grass block](https://minecraft.wiki/w/Grass_block "Grass block") disk | `disk_grass` |
    | [Gravel](https://minecraft.wiki/w/Gravel "Gravel") disk | `disk_gravel` |
    | [Sand](https://minecraft.wiki/w/Sand "Sand") disk | `disk_sand` |
    | [Dripleaf](https://minecraft.wiki/w/Dripleaf "Dripleaf") | `dripleaf` |
    | [Dripstone cluster](https://minecraft.wiki/w/Dripstone_cluster "Dripstone cluster") | `dripstone_cluster` |
    | [End gateway](https://minecraft.wiki/w/End_gateway "End gateway") (delayed) | `end_gateway_delayed` |
    | [End gateway](https://minecraft.wiki/w/End_gateway "End gateway") (exit) | `end_gateway_return` |
    | End island | `end_island` |
    | [End spike](https://minecraft.wiki/w/End_spike "End spike") | `end_spike` |
    | Fancy [oak](https://minecraft.wiki/w/Oak "Oak") tree | `fancy_oak` |
    | Fancy oak tree with [beehive](https://minecraft.wiki/w/Beehive "Beehive") | `fancy_oak_bees` |
    | Fancy oak tree (0.2% bee nest) | `fancy_oak_bees_0002` |
    | Fancy oak tree (2% bee nest) | `fancy_oak_bees_002` |
    | Fancy oak tree (5% bee nest) | `fancy_oak_bees_005` |
    | [Pink petal](https://minecraft.wiki/w/Pink_petal "Pink petal") patch | `flower_cherry` |
    | [Flower](https://minecraft.wiki/w/Flower "Flower") patch (default) | `flower_default` |
    | Flower patch ([flower forest](https://minecraft.wiki/w/Forest#Flower_Forest "Forest")) | `flower_flower_forest` |
    | Flower patch ([meadow](https://minecraft.wiki/w/Mountains#Meadow "Mountains")) | `flower_meadow` |
    | Flower patch ([plains](https://minecraft.wiki/w/Plains "Plains")) | `flower_plain` |
    | [Blue orchid](https://minecraft.wiki/w/Flower "Flower") patch | `flower_swamp` |
    | Flower patch ([forest](https://minecraft.wiki/w/Forest "Forest")) | `forest_flowers` |
    | [Forest rock](https://minecraft.wiki/w/Forest_rock "Forest rock") | `forest_rock` |
    | [Fossil](https://minecraft.wiki/w/Fossil "Fossil") (coal ore) | `fossil_coal` |
    | [Fossil](https://minecraft.wiki/w/Fossil "Fossil") (diamond ore) | `fossil_diamonds` |
    | Freeze surface | `freeze_top_layer` |
    | [Glow lichen](https://minecraft.wiki/w/Glow_Lichen "Glow Lichen") | `glow_lichen` |
    | [Glowstone blob](https://minecraft.wiki/w/Glowstone_blob "Glowstone blob") | `glowstone_extra` |
    | [Huge brown mushroom](https://minecraft.wiki/w/Huge_mushroom "Huge mushroom") | `huge_brown_mushroom` |
    | [Huge red mushroom](https://minecraft.wiki/w/Huge_mushroom "Huge mushroom") | `huge_red_mushroom` |
    | [Ice patch](https://minecraft.wiki/w/Ice_Patch "Ice Patch") | `ice_patch` |
    | [Ice spike](https://minecraft.wiki/w/Ice_spike "Ice spike") | `ice_spike` |
    | [Iceberg](https://minecraft.wiki/w/Iceberg "Iceberg") ([blue ice](https://minecraft.wiki/w/Blue_Ice "Blue Ice")) | `iceberg_blue` |
    | Iceberg ([packed ice](https://minecraft.wiki/w/Packed_Ice "Packed Ice")) | `iceberg_packed` |
    | [Jungle bush](https://minecraft.wiki/w/Jungle_Bush "Jungle Bush") | `jungle_bush` |
    | [Jungle tree](https://minecraft.wiki/w/Jungle_tree "Jungle tree") | `jungle_tree` |
    | Jungle tree (no [vines](https://minecraft.wiki/w/Vines "Vines")) | `jungle_tree_no_vine` |
    | [Kelp](https://minecraft.wiki/w/Kelp "Kelp") plant | `kelp` |
    | [Lava lake](https://minecraft.wiki/w/Lava_lake "Lava lake") | `lake_lava` |
    | Large [basalt columns](https://minecraft.wiki/w/Basalt_columns "Basalt columns") | `large_basalt_columns` |
    | Large [dripstone](https://minecraft.wiki/w/Dripstone "Dripstone") | `large_dripstone` |
    | [Lush cave](https://minecraft.wiki/w/Lush_Caves "Lush Caves") clay surface | `lush_caves_clay` |
    | [Mangrove](https://minecraft.wiki/w/Mangrove "Mangrove") | `mangrove` |
    | Mangrove vegetation | `mangrove_vegetation` |
    | [Meadow](https://minecraft.wiki/w/Mountains "Mountains") trees | `meadow_trees` |
    | Giant [jungle tree](https://minecraft.wiki/w/Jungle_tree "Jungle tree") | `mega_jungle_tree` |
    | Giant [spruce](https://minecraft.wiki/w/Spruce "Spruce") tree (pine-shaped) | `mega_pine` |
    | Giant [spruce](https://minecraft.wiki/w/Spruce "Spruce") tree (spruce-shaped) | `mega_spruce` |
    | [Dungeon](https://minecraft.wiki/w/Dungeon "Dungeon") | `monster_room` |
    | [Moss](https://minecraft.wiki/w/Moss_Block "Moss Block") patch | `moss_patch` |
    | Moss patch (grown from bone meal) | `moss_patch_bonemeal` |
    | Moss patch on ceilings | `moss_patch_ceiling` |
    | Moss vegetation | `moss_vegetation` |
    | [Huge mushrooms](https://minecraft.wiki/w/Huge_mushroom "Huge mushroom") ([mushroom fields](https://minecraft.wiki/w/Mushroom_Fields "Mushroom Fields")) | `mushroom_island_vegetaation` |
    | [Nether sprouts](https://minecraft.wiki/w/Nether_Sprouts "Nether Sprouts") | `nether_sprouts` |
    | Nether sprouts (grown from bone meal) | `nether_sprouts_bonemeal` |
    | [Oak](https://minecraft.wiki/w/Oak "Oak") tree | `oak` |
    | Oak tree (0.2% bee nest) | `oak_bees_0002` |
    | Oak tree (2% bee nest) | `oak_bees_002` |
    | Oak tree (5% bee nest) | `oak_bees_005` |
    | [Ancient debris](https://minecraft.wiki/w/Ancient_debris "Ancient debris") (large) | `ore_ancient_debris_large` |
    | Ancient debris (small) | `ore_ancient_debris_small` |
    | [Andesite](https://minecraft.wiki/w/Andesite "Andesite") [ore blob](https://minecraft.wiki/w/Ore_%28feature%29 "Ore (feature)") | `ore_andesite` |
    | [Blackstone](https://minecraft.wiki/w/Blackstone "Blackstone") blob | `ore_blackstone` |
    | [Clay](https://minecraft.wiki/w/Clay "Clay") blob | `ore_clay` |
    | [Coal ore](https://minecraft.wiki/w/Coal_ore "Coal ore") blob | `ore_coal` |
    | Coal ore (reduced air exposure) | `ore_coal_buried` |
    | Large [copper ore](https://minecraft.wiki/w/Copper_ore "Copper ore") blob | `ore_copper_large` |
    | Copper ore blob | `ore_copper_small` |
    | [Diamond ore](https://minecraft.wiki/w/Diamond_ore "Diamond ore") (no air exposure) | `ore_diamond_buried` |
    | Small diamond ore blob | `ore_diamond_large` |
    | Medium diamond ore blob | `ore_diamond_medium` |
    | Large diamond ore blob | `ore_diamond_small` |
    | [Diorite](https://minecraft.wiki/w/Diorite "Diorite") blob | `ore_diorite` |
    | [Dirt](https://minecraft.wiki/w/Dirt "Dirt") blob | `ore_dirt` |
    | [Emerald ore](https://minecraft.wiki/w/Emerald_Ore "Emerald Ore") blob | `ore_emerald` |
    | [Gold ore](https://minecraft.wiki/w/Gold_Ore "Gold Ore") blob | `ore_gold` |
    | [Gold ore](https://minecraft.wiki/w/Gold_Ore "Gold Ore") (reduced air exposure) | `ore_gold_buried` |
    | [Granite](https://minecraft.wiki/w/Granite "Granite") blob | `ore_granite` |
    | [Gravel](https://minecraft.wiki/w/Gravel "Gravel") blob (nether) | `ore_gravel` |
    | [Gravel](https://minecraft.wiki/w/Gravel "Gravel") blob | `ore_gravel_nether` |
    | [Infested stone](https://minecraft.wiki/w/Infested_Block "Infested Block") blob | `ore_infested` |
    | [Iron ore](https://minecraft.wiki/w/Iron_Ore "Iron Ore") blob | `ore_iron` |
    | Small iron ore blob | `ore_iron_small` |
    | [Lapis lazuli ore](https://minecraft.wiki/w/Lapis_Lazuli_Ore "Lapis Lazuli Ore") blob | `ore_lapis` |
    | Lapis lazuli ore (no air exposure) | `ore_lapis_buried` |
    | [Magma block](https://minecraft.wiki/w/Magma_Block "Magma Block") blob | `ore_magma` |
    | [Nether gold ore](https://minecraft.wiki/w/Nether_Gold_Ore "Nether Gold Ore") blob | `ore_nether_gold` |
    | [Nether quartz ore](https://minecraft.wiki/w/Nether_Quartz_Ore "Nether Quartz Ore") blob | `ore_quartz` |
    | [Redstone ore](https://minecraft.wiki/w/Redstone_Ore "Redstone Ore") blob | `ore_redstone` |
    | [Soul sand](https://minecraft.wiki/w/Soul_Sand "Soul Sand") blob | `ore_soul_sand` |
    | [Tuff](https://minecraft.wiki/w/Tuff "Tuff") blob | `ore_tuff` |
    | [Sweet berry](https://minecraft.wiki/w/Sweet_Berries "Sweet Berries") bush patch | `patch_berry_bush` |
    | Brown [mushroom](https://minecraft.wiki/w/Mushroom "Mushroom") patch | `patch_brown_mushroom` |
    | [Cactus](https://minecraft.wiki/w/Cactus "Cactus") patch | `patch_cactus` |
    | [Crimson root](https://minecraft.wiki/w/Crimson_root "Crimson root") patch | `patch_crimson_roots` |
    | [Dead bush](https://minecraft.wiki/w/Dead_Bush "Dead Bush") patch | `patch_dead_bush` |
    | [Fire](https://minecraft.wiki/w/Fire "Fire") patch | `patch_fire` |
    | [Grass](https://minecraft.wiki/w/Grass "Grass") patch | `patch_grass` |
    | [Grass](https://minecraft.wiki/w/Grass "Grass") and fern patch ([jungle](https://minecraft.wiki/w/Jungle "Jungle")) | `patch_grass_jungle` |
    | Large fern patch | `patch_large_fern` |
    | [Melon](https://minecraft.wiki/w/Melon "Melon") patch | `patch_melon` |
    | [Pumpkin](https://minecraft.wiki/w/Pumpkin "Pumpkin") patch | `patch_pumpkin` |
    | Red [mushroom](https://minecraft.wiki/w/Mushroom "Mushroom") Patch | `patch_red_mushroom` |
    | Soul [fire](https://minecraft.wiki/w/Fire "Fire") patch | `patch_soul_fire` |
    | [Sugar cane](https://minecraft.wiki/w/Sugar_Cane "Sugar Cane") patch | `patch_sugar_cane` |
    | [Sunflower](https://minecraft.wiki/w/Flower "Flower") patch | `patch_sunflower` |
    | [Grass](https://minecraft.wiki/w/Grass "Grass") and fern patch ([taiga](https://minecraft.wiki/w/Taiga "Taiga")) | `patch_taiga_grass` |
    | Tall [grass](https://minecraft.wiki/w/Grass "Grass") patch | `patch_tall_grass` |
    | [Lily pad](https://minecraft.wiki/w/Lily_Pad "Lily Pad") patch | `patch_waterlily` |
    | [Pile](https://minecraft.wiki/w/Pile "Pile") of [hay bales](https://minecraft.wiki/w/Hay_Bale "Hay Bale") | `pile_hay` |
    | Pile of [packed](https://minecraft.wiki/w/Packed_Ice "Packed Ice") and [blue ice](https://minecraft.wiki/w/Blue_Ice "Blue Ice") | `pile_ice` |
    | [Melon](https://minecraft.wiki/w/Melon "Melon") pile | `pile_melon` |
    | [Pumpkin](https://minecraft.wiki/w/Pumpkin "Pumpkin") pile | `pile_pumpkin` |
    | [Snow](https://minecraft.wiki/w/Snow "Snow") pile | `pile_snow` |
    | [Spruce](https://minecraft.wiki/w/Spruce "Spruce") tree (pine-shaped) | `pine` |
    | [Pointed dripstone](https://minecraft.wiki/w/Pointed_Dripstone "Pointed Dripstone") | `pointed_dripstone` |
    | Rooted [azalea tree](https://minecraft.wiki/w/Azalea_tree "Azalea tree") | `rooted_azalea_tree` |
    | [Sculk](https://minecraft.wiki/w/Sculk_family "Sculk family") patch ([ancient city](https://minecraft.wiki/w/Ancient_city "Ancient city")) | `sculk_patch_ancient_city` |
    | Sculk patch ([deep dark](https://minecraft.wiki/w/Deep_dark "Deep dark")) | `sculk_patch_deep_dark` |
    | [Sculk vein](https://minecraft.wiki/w/Sculk_vein "Sculk vein") | `sculk_vein` |
    | [Sea pickles](https://minecraft.wiki/w/Sea_Pickle "Sea Pickle") | `sea_pickle` |
    | [Seagrass](https://minecraft.wiki/w/Seagrass "Seagrass") (60% tall) | `seagrass_mid` |
    | [Seagrass](https://minecraft.wiki/w/Seagrass "Seagrass") (30% tall) | `seagrass_short` |
    | [Seagrass](https://minecraft.wiki/w/Seagrass "Seagrass") (short) | `seagrass_simple` |
    | [Seagrass](https://minecraft.wiki/w/Seagrass "Seagrass") (40% tall) | `seagrass_slightly_less_short` |
    | [Seagrass](https://minecraft.wiki/w/Seagrass "Seagrass") (80% tall) | `seagrass_tall` |
    | Single [grass](https://minecraft.wiki/w/Grass "Grass") plant | `single_piece_of_grass` |
    | Small [basalt columns](https://minecraft.wiki/w/Basalt_columns "Basalt columns") | `small_basalt_columns` |
    | [Spore blossom](https://minecraft.wiki/w/Spore_Blossom "Spore Blossom") | `spore_blossom` |
    | [Lava](https://minecraft.wiki/w/Lava "Lava") [spring](https://minecraft.wiki/w/Spring "Spring") (snow and packed ice) | `spring_lava_frozen` |
    | [Lava](https://minecraft.wiki/w/Lava "Lava") [spring](https://minecraft.wiki/w/Spring "Spring") (nether) | `spring_lava_nether` |
    | [Lava](https://minecraft.wiki/w/Lava "Lava") [spring](https://minecraft.wiki/w/Spring "Spring") (overworld) | `spring_lava_overworld` |
    | Nether lava spring (hidden) | `spring_nether_closed` |
    | Nether lava spring (visible) | `spring_nether_open` |
    | [Water](https://minecraft.wiki/w/Water "Water") [spring](https://minecraft.wiki/w/Spring "Spring") | `spring_water` |
    | [Spruce](https://minecraft.wiki/w/Spruce "Spruce") tree (spruce-shaped) | `spruce` |
    | Tall [birch](https://minecraft.wiki/w/Birch "Birch") tree with [bee nest](https://minecraft.wiki/w/Bee_nest "Bee nest") | `super_birch_bees` |
    | Tall [birch](https://minecraft.wiki/w/Birch "Birch") tree (0.2% bee nest) | `super_birch_bees_0002` |
    | [Oak](https://minecraft.wiki/w/Oak "Oak") tree (swamp) | `swamp_oak` |
    | Tall mangrove | `tall_mangrove` |
    | [Birch](https://minecraft.wiki/w/Birch "Birch") and [oak](https://minecraft.wiki/w/Oak "Oak") trees | `trees_birch_and_oak` |
    | Trees ([flower forest](https://minecraft.wiki/w/Forest#Flower_Forest "Forest")) | `trees_flower_forest` |
    | Trees ([grove](https://minecraft.wiki/w/Mountains#Grove "Mountains")) | `trees_grove` |
    | Trees ([jungle](https://minecraft.wiki/w/Jungle "Jungle")) | `trees_jungle` |
    | Trees ([old growth pine taiga](https://minecraft.wiki/w/Old_Growth_Taiga#Old_Growth_Pine_Taiga "Old Growth Taiga")) | `trees_old_growth_pine_taiga` |
    | Trees ([old growth spruce taiga](https://minecraft.wiki/w/Old_Growth_Taiga#Old_Growth_Spruce_Taiga "Old Growth Taiga")) | `trees_old_growth_spruce_taiga` |
    | Trees ([plains](https://minecraft.wiki/w/Plains "Plains")) | `trees_plains` |
    | Trees ([savanna](https://minecraft.wiki/w/Savanna "Savanna")) | `trees_savanna` |
    | Sparse [jungle trees](https://minecraft.wiki/w/Jungle_tree "Jungle tree") | `trees_sparse_jungle` |
    | Trees ([taiga](https://minecraft.wiki/w/Taiga "Taiga")) | `trees_taiga` |
    | Waterside trees | `trees_water` |
    | Trees ([windswept hills](https://minecraft.wiki/w/Windswept_Hills "Windswept Hills")) | `trees_windswept_hills` |
    | [Twisting vines](https://minecraft.wiki/w/Twisting_Vines "Twisting Vines") | `twisting_vines` |
    | Twisting vines (grown from bone meal) | `twisting_vines_bonemeal` |
    | Underwater [magma blocks](https://minecraft.wiki/w/Magma_Block "Magma Block") | `underwater_magma` |
    | [Vines](https://minecraft.wiki/w/Vines "Vines") | `vines` |
    | [Void start platform](https://minecraft.wiki/w/Void_Start_Platform "Void Start Platform") | `void_start_platform` |
    | [Coral Reef](https://minecraft.wiki/w/Coral_Reef "Coral Reef") | `warm_ocean_vegetation` |
    | [Warped forest](https://minecraft.wiki/w/Warped_Forest "Warped Forest") vegetation | `warped_forest_vegetation` |
    | Warped forest vegetation (grown from [bone meal](https://minecraft.wiki/w/Bone_Meal "Bone Meal")) | `warped_forest_vegetation_bonemeal` |
    | [Huge warped fungus](https://minecraft.wiki/w/Huge_fungus "Huge fungus") | `warped_fungus` |
    | Huge warped fungus (planted) | `warped_fungus_planted` |
    | [Weeping vines](https://minecraft.wiki/w/Weeping_Vines "Weeping Vines") | `weeping_vines` |

## Block states


Main article: [Block states § List of block states](https://minecraft.wiki/w/Block_states#List_of_block_states "Block states")

## Protocol and data versions

Main article: [Java Edition data values/Protocol and data versions](https://minecraft.wiki/w/Java_Edition_data_values/Protocol_and_data_versions "Java Edition data values/Protocol and data versions")

[[edit](https://minecraft.wiki/w/Special%3AEditPage/Java_Edition_data_values/Protocol_and_data_versions "Special:EditPage/Java Edition data values/Protocol and data versions")]

## Navigation


| * [v](https://minecraft.wiki/w/Template%3ANavbox_Java_Edition_technical "Template:Navbox Java Edition technical") * [t](https://minecraft.wiki/w/Special%3ATalkPage/Template%3ANavbox_Java_Edition_technical "Special:TalkPage/Template:Navbox Java Edition technical") * [e](https://minecraft.wiki/w/Special%3AEditPage/Template%3ANavbox_Java_Edition_technical "Special:EditPage/Template:Navbox Java Edition technical") *[Java Edition](https://minecraft.wiki/w/Java_Edition "Java Edition")* technical | |
| --- | --- |
| | General | | | --- | --- | | Concepts | * [![](/images/BlockSprite_chest.png?15d81)](https://minecraft.wiki/w/Block_entity "Block entity")[Block entity](https://minecraft.wiki/w/Block_entity "Block entity") * [![](/images/EnvSprite_map.png?b863e)](https://minecraft.wiki/w/Coordinates "Coordinates")[Coordinates](https://minecraft.wiki/w/Coordinates "Coordinates") * [![](/images/EffectSprite_infested.png?4562a)](https://minecraft.wiki/w/Crash "Crash")[Crashes](https://minecraft.wiki/w/Crash "Crash") * [String] [Loot context](https://minecraft.wiki/w/Loot_context "Loot context") * [![](/images/EntitySprite_cow.png?893cf)](https://minecraft.wiki/w/Mob_AI "Mob AI")[Mob AI](https://minecraft.wiki/w/Mob_AI "Mob AI") * [![](/images/BlockSprite_lodestone.png?00f1a)](https://minecraft.wiki/w/Point_of_Interest "Point of Interest")[Point of Interest](https://minecraft.wiki/w/Point_of_Interest "Point of Interest") * ![File directory.png: Sprite image for directory in Minecraft](/images/thumb/File_directory.png/16px-File_directory.png?8a409) [Identifier](https://minecraft.wiki/w/Identifier "Identifier") * [![](/images/BlockSprite_camera.png?7ee99)](https://minecraft.wiki/w/Screenshot "Screenshot")[Screenshot](https://minecraft.wiki/w/Screenshot "Screenshot") * [![](/images/EnvSprite_scoreboard.png?38feb)](https://minecraft.wiki/w/Statistics "Statistics")[Statistics](https://minecraft.wiki/w/Statistics "Statistics") * [![](/images/ItemSprite_book.png?791a5)](https://minecraft.wiki/w/Telemetry "Telemetry")[Telemetry](https://minecraft.wiki/w/Telemetry "Telemetry") * [![](/images/ItemSprite_clock.png?30324)](https://minecraft.wiki/w/Tick "Tick")[Tick](https://minecraft.wiki/w/Tick "Tick") * [![](/images/ItemSprite_wheat-seeds.png?b83e5)](https://minecraft.wiki/w/Random_Tick "Random Tick")[Random Tick](https://minecraft.wiki/w/Random_Tick "Random Tick") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/UUID "UUID")[UUID](https://minecraft.wiki/w/UUID "UUID") * [![](/images/BlockSprite_computer.png?e0c37)](https://minecraft.wiki/w/JSON "JSON")[JSON](https://minecraft.wiki/w/JSON "JSON") | | [General format](https://minecraft.wiki/w/Development_resources "Development resources") | * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Java_Edition_data_values "Java Edition data values")Data values   + [![](/images/LegacyBlockSprite_bricks-je1.png?9a58b)](https://minecraft.wiki/w/Java_Edition_Classic_data_values "Java Edition Classic data values")[Classic](https://minecraft.wiki/w/Java_Edition_Classic_data_values "Java Edition Classic data values")     - [Remake](https://minecraft.wiki/w/Classic_remake_data_values "Classic remake data values")   + [![](/images/EntitySprite_rana.png?3f2f9)](https://minecraft.wiki/w/Java_Edition_Indev_data_values "Java Edition Indev data values")[Indev](https://minecraft.wiki/w/Java_Edition_Indev_data_values "Java Edition Indev data values")   + [![](/images/BlockSprite_stone.png?e9a91)](https://minecraft.wiki/w/Java_Edition_pre-flattening_data_values "Java Edition pre-flattening data values")[Pre-flattening](https://minecraft.wiki/w/Java_Edition_pre-flattening_data_values "Java Edition pre-flattening data values") * [![](/images/EnvSprite_item.png?89d23)](https://minecraft.wiki/w/Data_component_format "Data component format")[Data component format](https://minecraft.wiki/w/Data_component_format "Data component format")   + [![](/images/BlockSprite_test-block-start.png?35191)](https://minecraft.wiki/w/Data_component_predicate "Data component predicate")[Predicate](https://minecraft.wiki/w/Data_component_predicate "Data component predicate") * [![](/images/EnvSprite_entities.png?94711)](https://minecraft.wiki/w/Entity_format "Entity format")[Entity format](https://minecraft.wiki/w/Entity_format "Entity format") * [![](/images/BlockSprite_chest.png?15d81)](https://minecraft.wiki/w/Block_entity_format "Block entity format")[Block entity format](https://minecraft.wiki/w/Block_entity_format "Block entity format") * [![](/images/ItemSprite_map.png?05f8c)](https://minecraft.wiki/w/Map_item_format "Map item format")[Map item format](https://minecraft.wiki/w/Map_item_format "Map item format") * [NBT Compound / JSON Object] [NBT format](https://minecraft.wiki/w/NBT_format "NBT format") * [![](/images/EffectSprite_particle-healing.png?1357a)](https://minecraft.wiki/w/Particle_format "Particle format")[Particle format](https://minecraft.wiki/w/Particle_format "Particle format") * [![](/images/ItemSprite_book-and-quill.png?f190b)](https://minecraft.wiki/w/Text_component_format "Text component format")[Text component format](https://minecraft.wiki/w/Text_component_format "Text component format") * [§](https://minecraft.wiki/w/Formatting_codes "Formatting codes") [Formatting codes](https://minecraft.wiki/w/Formatting_codes "Formatting codes") * [![](/images/thumb/Movement_hint.png/16px-Movement_hint.png?92667)](https://minecraft.wiki/w/Key_codes "Key codes")[Key codes](https://minecraft.wiki/w/Key_codes "Key codes") * [![](/images/thumb/Dice.png/14px-Dice.png?a4e84)](https://minecraft.wiki/w/Random_sequence_format "Random sequence format")[Random sequence](https://minecraft.wiki/w/Random_sequence_format "Random sequence format") * [![](/images/BlockSprite_structure-block.png?381fc)](https://minecraft.wiki/w/Structure_file "Structure file")[Structure file format](https://minecraft.wiki/w/Structure_file "Structure file")   + [![](/images/EnvSprite_chunk.png?b2cf1)](https://minecraft.wiki/w/Schematic_file_format "Schematic file format")[Schematic file format](https://minecraft.wiki/w/Schematic_file_format "Schematic file format") | | [World](https://minecraft.wiki/w/World "World") | * [![](/images/EnvSprite_altitude.png?9b274)](https://minecraft.wiki/w/Heightmap "Heightmap")[Heightmap](https://minecraft.wiki/w/Heightmap "Heightmap") * [![](/images/EnvSprite_mountain.png?2e0ae)](https://minecraft.wiki/w/World_seed "World seed")[Seed](https://minecraft.wiki/w/World_seed "World seed")   + [Anomalous](https://minecraft.wiki/w/Anomalous_world_seeds "Anomalous world seeds") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Data_version "Data version")[Data version](https://minecraft.wiki/w/Data_version "Data version")  |  |  | | --- | --- | | Legacy | * [![](/images/EnvSprite_chunk.png?b2cf1)](https://minecraft.wiki/w/Spawn_chunk "Spawn chunk")[Spawn chunk](https://minecraft.wiki/w/Spawn_chunk "Spawn chunk") | | [Level format](https://minecraft.wiki/w/Java_Edition_level_format "Java Edition level format") | * [![](/images/BlockSprite_anvil.png?a26c9)](https://minecraft.wiki/w/Anvil_file_format "Anvil file format")[Anvil file format](https://minecraft.wiki/w/Anvil_file_format "Anvil file format") * [![](/images/EnvSprite_chunk.png?b2cf1)](https://minecraft.wiki/w/Chunk_format "Chunk format")[Chunk format](https://minecraft.wiki/w/Chunk_format "Chunk format") * [![](/images/EntitySprite_steve.png?856f8)](https://minecraft.wiki/w/Player.dat_format "Player.dat format")[Player format](https://minecraft.wiki/w/Player.dat_format "Player.dat format") * [![](/images/BlockSprite_lodestone.png?00f1a)](https://minecraft.wiki/w/Point_of_Interest_format "Point of Interest format")[Point of Interest format](https://minecraft.wiki/w/Point_of_Interest_format "Point of Interest format") * [![](/images/EntitySprite_ravager.png?40196)](https://minecraft.wiki/w/Raids.dat_format "Raids.dat format")[raids.dat format](https://minecraft.wiki/w/Raids.dat_format "Raids.dat format") * [![](/images/BlockSprite_chain-command-block.png?0afa8)](https://minecraft.wiki/w/Command_storage_format "Command storage format")[Command storage format](https://minecraft.wiki/w/Command_storage_format "Command storage format") * [![](/images/EnvSprite_scoreboard.png?38feb)](https://minecraft.wiki/w/Scoreboard#NBT_format "Scoreboard")[Scoreboard format](https://minecraft.wiki/w/Scoreboard#NBT_format "Scoreboard")  |  |  | | --- | --- | | Legacy | * [![](/images/LegacyBlockSprite_bricks-je1.png?9a58b)](https://minecraft.wiki/w/Java_Edition_Classic_level_format "Java Edition Classic level format")[Classic level format](https://minecraft.wiki/w/Java_Edition_Classic_level_format "Java Edition Classic level format") * [Classic server protocol](https://minecraft.wiki/w/Classic_server_protocol "Classic server protocol") * [![](/images/EntitySprite_rana.png?3f2f9)](https://minecraft.wiki/w/Java_Edition_Indev_level_format "Java Edition Indev level format")[Indev level format](https://minecraft.wiki/w/Java_Edition_Indev_level_format "Java Edition Indev level format") * [![](/images/EnvSprite_nether-portal.png?47646)](https://minecraft.wiki/w/Java_Edition_Alpha_level_format "Java Edition Alpha level format")[Alpha level format](https://minecraft.wiki/w/Java_Edition_Alpha_level_format "Java Edition Alpha level format")   + [![](/images/LegacyItemSprite_oak-door-revision-1.png?b7426)](https://minecraft.wiki/w/Zone_file_format "Zone file format")[Zone file format](https://minecraft.wiki/w/Zone_file_format "Zone file format") * [![](/images/ItemSprite_locked-map.png?c4112)](https://minecraft.wiki/w/Region_file_format "Region file format")[Region file format](https://minecraft.wiki/w/Region_file_format "Region file format") * [![](/images/Servers.png?b1dc2)](https://minecraft.wiki/w/Server_level.dat "Server level.dat")[server\_level.dat format](https://minecraft.wiki/w/Server_level.dat "Server level.dat") * [![](/images/EnvSprite_new-village.png?3e8a5)](https://minecraft.wiki/w/Villages.dat_format "Villages.dat format")[villages.dat format](https://minecraft.wiki/w/Villages.dat_format "Villages.dat format") * [![](/images/EnvSprite_abandoned-mineshaft.png?fab65)](https://minecraft.wiki/w/Generated_structures_data_file_format "Generated structures data file format")[Generated structures format](https://minecraft.wiki/w/Generated_structures_data_file_format "Generated structures data file format") | | | | [.minecraft](https://minecraft.wiki/w/.minecraft ".minecraft") | * ![File archive.png: Sprite image for archive in Minecraft](/images/thumb/File_archive.png/16px-File_archive.png?5ba7d) [client.jar](https://minecraft.wiki/w/Client.jar "Client.jar")   + [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Version.json "Version.json")[version.json](https://minecraft.wiki/w/Version.json "Version.json") * [![](/images/ItemSprite_book-and-quill.png?f190b)](https://minecraft.wiki/w/Client.json "Client.json")[client.json](https://minecraft.wiki/w/Client.json "Client.json") * [![](/images/BlockSprite_command-block.png?e7078)](https://minecraft.wiki/w/Command_history.txt "Command history.txt")[command\_history.txt](https://minecraft.wiki/w/Command_history.txt "Command history.txt") * [![](/images/BlockSprite_chest.png?15d81)](https://minecraft.wiki/w/Launcher_profiles.json "Launcher profiles.json")[launcher\_profiles.json](https://minecraft.wiki/w/Launcher_profiles.json "Launcher profiles.json") * [![](/images/Chat_settings_gear.png?6a179)](https://minecraft.wiki/w/Options.txt "Options.txt")[options.txt](https://minecraft.wiki/w/Options.txt "Options.txt") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Version_manifest.json "Version manifest.json")[version\_manifest.json](https://minecraft.wiki/w/Version_manifest.json "Version manifest.json") * [![](/images/ItemSprite_paper.png?565a1)](https://minecraft.wiki/w/Hotbar.nbt_format "Hotbar.nbt format")[hotbar.nbt format](https://minecraft.wiki/w/Hotbar.nbt_format "Hotbar.nbt format") * [![](/images/Servers.png?b1dc2)](https://minecraft.wiki/w/Servers.dat_format "Servers.dat format")[Server list format](https://minecraft.wiki/w/Servers.dat_format "Servers.dat format") | | Tools | * `F3` [Debug screen](https://minecraft.wiki/w/Debug_screen "Debug screen")   + [hotkey](https://minecraft.wiki/w/Debug_hotkey "Debug hotkey")   + [renderer](https://minecraft.wiki/w/Debug_renderer "Debug renderer") * [![](/images/Mojang_logo.svg?0b294)](https://minecraft.wiki/w/Java_developer_tools "Java developer tools")[Developer Tools](https://minecraft.wiki/w/Java_developer_tools "Java developer tools")   + [![](/images/BlockSprite_test-instance-block.png?27a39)](https://minecraft.wiki/w/GameTest "GameTest")[GameTest](https://minecraft.wiki/w/GameTest "GameTest")   + [DataFixerUpper](https://minecraft.wiki/w/DataFixerUpper "DataFixerUpper")   + [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Debug_property "Debug property")[Debug properties](https://minecraft.wiki/w/Debug_property "Debug property")  |  |  | | --- | --- | | Legacy | * [![](/images/BlockSprite_computer.png?e0c37)](https://minecraft.wiki/w/Obfuscation_map "Obfuscation map")[Obfuscation map](https://minecraft.wiki/w/Obfuscation_map "Obfuscation map") | | | Sound | * [![](/images/BlockSprite_jukebox-side.png?8477e)](https://minecraft.wiki/w/Block_sound_type "Block sound type")[Block sound type](https://minecraft.wiki/w/Block_sound_type "Block sound type") * [![](/images/EnvSprite_chat.png?0dd92)](https://minecraft.wiki/w/Closed_captions "Closed captions")[Closed captions](https://minecraft.wiki/w/Closed_captions "Closed captions") * [![](/images/EnvSprite_ambience.png?d7c92)](https://minecraft.wiki/w/Sounds.json "Sounds.json")[sounds.json](https://minecraft.wiki/w/Sounds.json "Sounds.json") | | [Commands](https://minecraft.wiki/w/Commands "Commands") | * [Brigadier](https://minecraft.wiki/w/Brigadier "Brigadier") * [![](/images/BlockSprite_repeating-command-block.png?1dad0)](https://minecraft.wiki/w/Function_%28Java_Edition%29 "Function (Java Edition)")[Functions](https://minecraft.wiki/w/Function_%28Java_Edition%29 "Function (Java Edition)")   **[All commands](https://minecraft.wiki/w/Template%3ANavbox_commands "Template:Navbox commands")** | | [Launching](https://minecraft.wiki/w/Minecraft_Launcher "Minecraft Launcher") | * [Mojang API](https://minecraft.wiki/w/Mojang_API "Mojang API") * [![](/images/Microsoft_logo.svg?7e87a)](https://minecraft.wiki/w/Microsoft_authentication "Microsoft authentication")[Microsoft authentication](https://minecraft.wiki/w/Microsoft_authentication "Microsoft authentication") * [![](/images/thumb/Java_Edition_icon_3.png/16px-Java_Edition_icon_3.png?f7112)](https://minecraft.wiki/w/Quick_Play "Quick Play")[Quick Play](https://minecraft.wiki/w/Quick_Play "Quick Play")  |  |  | | --- | --- | | Legacy | * [Legacy Minecraft authentication](https://minecraft.wiki/w/Legacy_Minecraft_authentication "Legacy Minecraft authentication") * [Yggdrasil](https://minecraft.wiki/w/Yggdrasil "Yggdrasil") | | | [Protocol](https://minecraft.wiki/w/Java_Edition_protocol "Java Edition protocol") | * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Protocol_version "Protocol version")[Protocol version](https://minecraft.wiki/w/Protocol_version "Protocol version") * [![](/images/ItemSprite_bundle.png?9eb9f)](https://minecraft.wiki/w/Java_Edition_protocol/Packets "Java Edition protocol/Packets")[Packets](https://minecraft.wiki/w/Java_Edition_protocol/Packets "Java Edition protocol/Packets") * [Data types](https://minecraft.wiki/w/Java_Edition_protocol/Data_types "Java Edition protocol/Data types") * [![](/images/BlockSprite_computer.png?e0c37)](https://minecraft.wiki/w/Java_Edition_protocol/Encryption "Java Edition protocol/Encryption")[Encryption](https://minecraft.wiki/w/Java_Edition_protocol/Encryption "Java Edition protocol/Encryption") | | [Server](https://minecraft.wiki/w/Server "Server") | * ![File archive.png: Sprite image for archive in Minecraft](/images/thumb/File_archive.png/16px-File_archive.png?5ba7d) [server.jar](https://minecraft.wiki/w/Server.jar "Server.jar") * [![](/images/BlockSprite_test-instance-block.png?27a39)](https://minecraft.wiki/w/Server.properties "Server.properties")[server.properties](https://minecraft.wiki/w/Server.properties "Server.properties") * [![](/images/BlockSprite_test-instance-block.png?27a39)](https://minecraft.wiki/w/Server/Requirements "Server/Requirements")[Server requirements](https://minecraft.wiki/w/Server/Requirements "Server/Requirements") * [![](/images/BlockSprite_test-block-accept.png?08355)](https://minecraft.wiki/w/Whitelist "Whitelist")[Whitelist](https://minecraft.wiki/w/Whitelist "Whitelist") * [Operator list](https://minecraft.wiki/w/Server#Operator_list "Server")  |  |  | | --- | --- | | Protocols | * [Query](https://minecraft.wiki/w/Query "Query") * [RCON](https://minecraft.wiki/w/RCON "RCON") * [Server Management Protocol](https://minecraft.wiki/w/Minecraft_Server_Management_Protocol "Minecraft Server Management Protocol") | | | Legacy | * [al\_version](https://minecraft.wiki/w/Al_version "Al version") * [![](/images/EnvSprite_item.png?89d23)](https://minecraft.wiki/w/Item_format "Item format")[Item format](https://minecraft.wiki/w/Item_format "Item format") | | |
| | [Data pack](https://minecraft.wiki/w/Data_pack "Data pack") | | | --- | --- | | Components | * [pack.mcmeta](https://minecraft.wiki/w/Pack.mcmeta "Pack.mcmeta") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Pack_format "Pack format")[Pack format](https://minecraft.wiki/w/Pack_format "Pack format") * [![](/images/ItemSprite_map.png?05f8c)](https://minecraft.wiki/w/Advancement_definition "Advancement definition")[Advancements](https://minecraft.wiki/w/Advancement_definition "Advancement definition") * [![](/images/BlockSprite_repeating-command-block.png?1dad0)](https://minecraft.wiki/w/Function_%28Java_Edition%29 "Function (Java Edition)")[Functions](https://minecraft.wiki/w/Function_%28Java_Edition%29 "Function (Java Edition)") * [![](/images/BlockSprite_red-banner.png?8b4d0)](https://minecraft.wiki/w/Item_modifier "Item modifier")[Item modifier](https://minecraft.wiki/w/Item_modifier "Item modifier") * [![](/images/ItemSprite_diamond.png?8f019)](https://minecraft.wiki/w/Loot_table "Loot table")[Loot tables](https://minecraft.wiki/w/Loot_table "Loot table") * [![](/images/BlockSprite_test-block-start.png?35191)](https://minecraft.wiki/w/Predicate "Predicate")[Predicate](https://minecraft.wiki/w/Predicate "Predicate") * [![](/images/BlockSprite_crafting-table.png?6e126)](https://minecraft.wiki/w/Recipe_%28Java_Edition%29 "Recipe (Java Edition)")[Recipe](https://minecraft.wiki/w/Recipe_%28Java_Edition%29 "Recipe (Java Edition)") * [![](/images/EffectSprite_strength.png?05e79)](https://minecraft.wiki/w/Damage_type "Damage type")[Damage type](https://minecraft.wiki/w/Damage_type "Damage type") * [![](/images/EnvSprite_chat.png?0dd92)](https://minecraft.wiki/w/Chat_type "Chat type")[Chat type](https://minecraft.wiki/w/Chat_type "Chat type") * [![](/images/ItemSprite_enchanted-book.png?b7877)](https://minecraft.wiki/w/Enchantment_definition "Enchantment definition")[Enchantment](https://minecraft.wiki/w/Enchantment_definition "Enchantment definition") * [![](/images/BlockSprite_enchanting-table.png?45e2c)](https://minecraft.wiki/w/Enchantment_provider "Enchantment provider")[Enchantment provider](https://minecraft.wiki/w/Enchantment_provider "Enchantment provider") * [![](/images/ItemSprite_painting.png?55d20)](https://minecraft.wiki/w/Painting_variant_definition "Painting variant definition")[Painting variant](https://minecraft.wiki/w/Painting_variant_definition "Painting variant definition") * [![](/images/BlockSprite_white-banner.png?8b4d0)](https://minecraft.wiki/w/Banner_pattern_definition "Banner pattern definition")[Banner pattern](https://minecraft.wiki/w/Banner_pattern_definition "Banner pattern definition") * [![](/images/ItemSprite_goat-horn.png?e5a9f)](https://minecraft.wiki/w/Instrument_definition "Instrument definition")[Instrument](https://minecraft.wiki/w/Instrument_definition "Instrument definition") * [![](/images/BlockSprite_jukebox.png?86205)](https://minecraft.wiki/w/Jukebox_song_definition "Jukebox song definition")[Jukebox song](https://minecraft.wiki/w/Jukebox_song_definition "Jukebox song definition") * [![](/images/BlockSprite_trial-spawner.png?0a3dc)](https://minecraft.wiki/w/Trial_spawner_configuration "Trial spawner configuration")[Trial spawner configuration](https://minecraft.wiki/w/Trial_spawner_configuration "Trial spawner configuration") * [![](/images/EntitySprite_pig.png?5435e)](https://minecraft.wiki/w/Mob_variant_definitions "Mob variant definitions")[Mob variants](https://minecraft.wiki/w/Mob_variant_definitions "Mob variant definitions") * [![](/images/ItemSprite_paper.png?565a1)](https://minecraft.wiki/w/Dialog "Dialog")[Dialog](https://minecraft.wiki/w/Dialog "Dialog") * [![](/images/ItemSprite_wayfinder-armor-trim.png?ffaf0)](https://minecraft.wiki/w/Armor_trim_definition "Armor trim definition")[Armor trim](https://minecraft.wiki/w/Armor_trim_definition "Armor trim definition") * [![](/images/ItemSprite_footprint.png?1c844)](https://minecraft.wiki/w/Slot_sources "Slot sources")[Slot sources](https://minecraft.wiki/w/Slot_sources "Slot sources") * [![](/images/ItemSprite_clock.png?30324)](https://minecraft.wiki/w/Timeline "Timeline")[Timeline](https://minecraft.wiki/w/Timeline "Timeline") * [![](/images/EntitySprite_villager.png?05433)](https://minecraft.wiki/w/Villager_trade_definition "Villager trade definition")[Villager trade](https://minecraft.wiki/w/Villager_trade_definition "Villager trade definition") * [Trade set](https://minecraft.wiki/w/Trade_set "Trade set") * [World Clock](https://minecraft.wiki/w/World_Clock "World Clock") * [![](/images/EntitySprite_sulfur-cube.png?ad68d)](https://minecraft.wiki/w/Sulfur_cube_archetype_definition "Sulfur cube archetype definition")[Sulfur cube archetype](https://minecraft.wiki/w/Sulfur_cube_archetype_definition "Sulfur cube archetype definition")​[*upcoming: [JE 26.2](https://minecraft.wiki/w/Java_Edition_26.2 "Java Edition 26.2")*]  |  |  | | --- | --- | | [Tag](https://minecraft.wiki/w/Tag_%28Java_Edition%29 "Tag (Java Edition)") | * [![](/images/BlockSprite_grass-block.png?97c2e)](https://minecraft.wiki/w/Block_tag_%28Java_Edition%29 "Block tag (Java Edition)")[Block](https://minecraft.wiki/w/Block_tag_%28Java_Edition%29 "Block tag (Java Edition)") * [![](/images/EnvSprite_item.png?89d23)](https://minecraft.wiki/w/Item_tag_%28Java_Edition%29 "Item tag (Java Edition)")[Item](https://minecraft.wiki/w/Item_tag_%28Java_Edition%29 "Item tag (Java Edition)") * [![](/images/BlockSprite_repeating-command-block.png?1dad0)](https://minecraft.wiki/w/Function_tag_%28Java_Edition%29 "Function tag (Java Edition)")[Function](https://minecraft.wiki/w/Function_tag_%28Java_Edition%29 "Function tag (Java Edition)") * [![](/images/ItemSprite_water-bucket.png?6e72b)](https://minecraft.wiki/w/Fluid_tag_%28Java_Edition%29 "Fluid tag (Java Edition)")[Fluid](https://minecraft.wiki/w/Fluid_tag_%28Java_Edition%29 "Fluid tag (Java Edition)") * [![](/images/EnvSprite_entities.png?94711)](https://minecraft.wiki/w/Entity_type_tag_%28Java_Edition%29 "Entity type tag (Java Edition)")[Entity type](https://minecraft.wiki/w/Entity_type_tag_%28Java_Edition%29 "Entity type tag (Java Edition)") * [![](/images/BlockSprite_sculk-sensor.png?ccbdb)](https://minecraft.wiki/w/Game_event_tag_%28Java_Edition%29 "Game event tag (Java Edition)")[Game event](https://minecraft.wiki/w/Game_event_tag_%28Java_Edition%29 "Game event tag (Java Edition)") * [![](/images/BiomeSprite_forest.png?98e29)](https://minecraft.wiki/w/Biome_tag_%28Java_Edition%29 "Biome tag (Java Edition)")[Biome](https://minecraft.wiki/w/Biome_tag_%28Java_Edition%29 "Biome tag (Java Edition)") * [![](/images/EnvSprite_superflat.png?54c14)](https://minecraft.wiki/w/Flat_level_generator_preset_tag_%28Java_Edition%29 "Flat level generator preset tag (Java Edition)")[Flat level generator preset](https://minecraft.wiki/w/Flat_level_generator_preset_tag_%28Java_Edition%29 "Flat level generator preset tag (Java Edition)") * [![](/images/EnvSprite_mountain.png?2e0ae)](https://minecraft.wiki/w/World_preset_tag_%28Java_Edition%29 "World preset tag (Java Edition)")[World preset](https://minecraft.wiki/w/World_preset_tag_%28Java_Edition%29 "World preset tag (Java Edition)") * [![](/images/EnvSprite_jungle-pyramid.png?736e3)](https://minecraft.wiki/w/Structure_tag_%28Java_Edition%29 "Structure tag (Java Edition)")[Structure](https://minecraft.wiki/w/Structure_tag_%28Java_Edition%29 "Structure tag (Java Edition)") * [![](/images/BlockSprite_lodestone.png?00f1a)](https://minecraft.wiki/w/Point_of_interest_type_tag_%28Java_Edition%29 "Point of interest type tag (Java Edition)")[Point of interest type](https://minecraft.wiki/w/Point_of_interest_type_tag_%28Java_Edition%29 "Point of interest type tag (Java Edition)") * [![](/images/ItemSprite_painting.png?55d20)](https://minecraft.wiki/w/Painting_variant_tag_%28Java_Edition%29 "Painting variant tag (Java Edition)")[Painting variant](https://minecraft.wiki/w/Painting_variant_tag_%28Java_Edition%29 "Painting variant tag (Java Edition)") * [![](/images/BlockSprite_white-banner.png?8b4d0)](https://minecraft.wiki/w/Banner_pattern_tag_%28Java_Edition%29 "Banner pattern tag (Java Edition)")[Banner pattern](https://minecraft.wiki/w/Banner_pattern_tag_%28Java_Edition%29 "Banner pattern tag (Java Edition)") * [![](/images/ItemSprite_goat-horn.png?e5a9f)](https://minecraft.wiki/w/Instrument_tag_%28Java_Edition%29 "Instrument tag (Java Edition)")[Instrument](https://minecraft.wiki/w/Instrument_tag_%28Java_Edition%29 "Instrument tag (Java Edition)") * ![❤️](/images/Heart_%28icon%29.png?faf83) [Damage type](https://minecraft.wiki/w/Damage_type_tag_%28Java_Edition%29 "Damage type tag (Java Edition)") * [![](/images/ItemSprite_enchanted-book.png?b7877)](https://minecraft.wiki/w/Enchantment_tag_%28Java_Edition%29 "Enchantment tag (Java Edition)")[Enchantment](https://minecraft.wiki/w/Enchantment_tag_%28Java_Edition%29 "Enchantment tag (Java Edition)") * [![](/images/ItemSprite_paper.png?565a1)](https://minecraft.wiki/w/Dialog_tag_%28Java_Edition%29 "Dialog tag (Java Edition)")[Dialog](https://minecraft.wiki/w/Dialog_tag_%28Java_Edition%29 "Dialog tag (Java Edition)") * [![](/images/ItemSprite_clock.png?30324)](https://minecraft.wiki/w/Timeline_tag_%28Java_Edition%29 "Timeline tag (Java Edition)")[Timeline](https://minecraft.wiki/w/Timeline_tag_%28Java_Edition%29 "Timeline tag (Java Edition)") * [![](/images/ItemSprite_water-bottle.png?fe7c2)](https://minecraft.wiki/w/Potion_tag_%28Java_Edition%29 "Potion tag (Java Edition)")[Potion](https://minecraft.wiki/w/Potion_tag_%28Java_Edition%29 "Potion tag (Java Edition)") * [![](/images/EntitySprite_villager.png?05433)](https://minecraft.wiki/w/Villager_trade_tag_%28Java_Edition%29 "Villager trade tag (Java Edition)")[Villager trade](https://minecraft.wiki/w/Villager_trade_tag_%28Java_Edition%29 "Villager trade tag (Java Edition)") * [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Configured_feature_tag_%28Java_Edition%29 "Configured feature tag (Java Edition)")[Configured feature](https://minecraft.wiki/w/Configured_feature_tag_%28Java_Edition%29 "Configured feature tag (Java Edition)") | | [GameTest](https://minecraft.wiki/w/GameTest "GameTest") | * [![](/images/BlockSprite_test-block-start.png?35191)](https://minecraft.wiki/w/Test_environment_definition "Test environment definition")[Test environment](https://minecraft.wiki/w/Test_environment_definition "Test environment definition") * [![](/images/BlockSprite_test-instance-block.png?27a39)](https://minecraft.wiki/w/Test_instance_definition "Test instance definition")[Test instance](https://minecraft.wiki/w/Test_instance_definition "Test instance definition") | | [World generation](https://minecraft.wiki/w/Custom_world_generation "Custom world generation") | * [Dimension](https://minecraft.wiki/w/Dimension_definition "Dimension definition") * [![](/images/EnvSprite_nether-portal.png?47646)](https://minecraft.wiki/w/Dimension_type "Dimension type")[Dimension type](https://minecraft.wiki/w/Dimension_type "Dimension type") * [![](/images/EnvSprite_mountain.png?2e0ae)](https://minecraft.wiki/w/World_preset_definition "World preset definition")[World preset](https://minecraft.wiki/w/World_preset_definition "World preset definition") * [![](/images/EnvSprite_biomes.png?0a976)](https://minecraft.wiki/w/Biome_definition "Biome definition")[Biomes](https://minecraft.wiki/w/Biome_definition "Biome definition") * [![](/images/EnvSprite_cave.png?47a17)](https://minecraft.wiki/w/Carver_definition "Carver definition")[Carver](https://minecraft.wiki/w/Carver_definition "Carver definition") * [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Configured_feature "Configured feature")[Configured feature](https://minecraft.wiki/w/Configured_feature "Configured feature")   + [![](/images/EnvSprite_oak.png?742a4)](https://minecraft.wiki/w/Tree_definition "Tree definition")[Tree](https://minecraft.wiki/w/Tree_definition "Tree definition") * [![](/images/EnvSprite_map.png?b863e)](https://minecraft.wiki/w/Placed_feature "Placed feature")[Placed feature](https://minecraft.wiki/w/Placed_feature "Placed feature") * [Environment attribute](https://minecraft.wiki/w/Environment_attribute "Environment attribute")  |  |  | | --- | --- | | [Noise settings](https://minecraft.wiki/w/Noise_settings "Noise settings") | * [![](/images/EnvSprite_mountain.png?2e0ae)](https://minecraft.wiki/w/Noise_router "Noise router")[Noise router](https://minecraft.wiki/w/Noise_router "Noise router") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Density_function "Density function")[Density function](https://minecraft.wiki/w/Density_function "Density function") * [Noises](https://minecraft.wiki/w/Noise "Noise") * [![](/images/EnvSprite_surface.png?75bf7)](https://minecraft.wiki/w/Surface_rule "Surface rule")[Surface rule](https://minecraft.wiki/w/Surface_rule "Surface rule") | | [Structures](https://minecraft.wiki/w/Structure_definition "Structure definition") | * [![](/images/EnvSprite_abandoned-mineshaft.png?fab65)](https://minecraft.wiki/w/Structure_set "Structure set")[Structure set](https://minecraft.wiki/w/Structure_set "Structure set") * [![](/images/BlockSprite_jigsaw.png?ec5e3)](https://minecraft.wiki/w/Template_pool "Template pool")[Template pool](https://minecraft.wiki/w/Template_pool "Template pool") * [![](/images/BlockSprite_cracked-stone-bricks.png?f3f1d)](https://minecraft.wiki/w/Processor_list "Processor list")[Processor list](https://minecraft.wiki/w/Processor_list "Processor list") * [![](/images/EnvSprite_nether-fossil.png?93621)](https://minecraft.wiki/w/Structure_file "Structure file")[Structure templates](https://minecraft.wiki/w/Structure_file "Structure file") | | Removed | * [![](/images/ItemSprite_iron-pickaxe.png?77536)](https://minecraft.wiki/w/Configured_surface_builder "Configured surface builder")[Configured surface builder](https://minecraft.wiki/w/Configured_surface_builder "Configured surface builder") | | | | Data packs | * [![](/images/BlockSprite_deepslate.png?d7361)](https://minecraft.wiki/w/Caves_%26_Cliffs_Prototype_Data_Pack "Caves & Cliffs Prototype Data Pack")[Caves & Cliffs Prototype Data Pack](https://minecraft.wiki/w/Caves_%26_Cliffs_Prototype_Data_Pack "Caves & Cliffs Prototype Data Pack") * [![](/images/ItemSprite_magical-painting.png?b0bf0)](https://minecraft.wiki/w/Phantom_Frames "Phantom Frames")[Phantom Frames](https://minecraft.wiki/w/Phantom_Frames "Phantom Frames") | | Tutorials | * [![](/images/thumb/EnvSprite_autosave.png/16px-EnvSprite_autosave.png?a55e7)](https://minecraft.wiki/w/Tutorial%3AImporting_a_data_pack "Tutorial:Importing a data pack")[Importing](https://minecraft.wiki/w/Tutorial%3AImporting_a_data_pack "Tutorial:Importing a data pack") * [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Tutorial%3ACreating_a_data_pack "Tutorial:Creating a data pack")[Creating](https://minecraft.wiki/w/Tutorial%3ACreating_a_data_pack "Tutorial:Creating a data pack") * [Optimizing](https://minecraft.wiki/w/Tutorial%3AOptimizing_a_data_pack "Tutorial:Optimizing a data pack") * [![](/images/BlockSprite_command-block.png?e7078)](https://minecraft.wiki/w/Tutorial%3ACommand_blocks_and_functions "Tutorial:Command blocks and functions")[Command blocks and functions](https://minecraft.wiki/w/Tutorial%3ACommand_blocks_and_functions "Tutorial:Command blocks and functions") * [Repairing a world corrupted by a data pack](https://minecraft.wiki/w/Tutorial%3ARepairing_a_world_corrupted_by_a_data_pack "Tutorial:Repairing a world corrupted by a data pack")  |  |  | | --- | --- | | Content | * [![](/images/ItemSprite_enchanted-book.png?b7877)](https://minecraft.wiki/w/Tutorial%3AAdding_custom_enchantments "Tutorial:Adding custom enchantments")[Custom enchantments](https://minecraft.wiki/w/Tutorial%3AAdding_custom_enchantments "Tutorial:Adding custom enchantments") * [![](/images/ItemSprite_painting.png?55d20)](https://minecraft.wiki/w/Tutorial%3AAdding_custom_paintings "Tutorial:Adding custom paintings")[Custom paintings](https://minecraft.wiki/w/Tutorial%3AAdding_custom_paintings "Tutorial:Adding custom paintings") * [![](/images/ItemSprite_armor-trim.png?1d672)](https://minecraft.wiki/w/Tutorial%3AAdding_custom_trims "Tutorial:Adding custom trims")[Custom trims](https://minecraft.wiki/w/Tutorial%3AAdding_custom_trims "Tutorial:Adding custom trims") | | World generation | * [![](/images/EnvSprite_other-portal.png?ca57b)](https://minecraft.wiki/w/Tutorial%3AAdding_a_new_dimension "Tutorial:Adding a new dimension")[New dimension](https://minecraft.wiki/w/Tutorial%3AAdding_a_new_dimension "Tutorial:Adding a new dimension") * [![](/images/EnvSprite_lunar-base.png?648e4)](https://minecraft.wiki/w/Tutorial%3ACustom_structures "Tutorial:Custom structures")[Custom structures](https://minecraft.wiki/w/Tutorial%3ACustom_structures "Tutorial:Custom structures") | | | |
| | [Resource pack](https://minecraft.wiki/w/Resource_pack "Resource pack") | | | --- | --- | | Components | * [pack.mcmeta](https://minecraft.wiki/w/Pack.mcmeta "Pack.mcmeta") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Pack_format "Pack format")[Pack format](https://minecraft.wiki/w/Pack_format "Pack format") * [![](/images/EnvSprite_language.png?39da2)](https://minecraft.wiki/w/Resource_pack#Language "Resource pack")[Language](https://minecraft.wiki/w/Resource_pack#Language "Resource pack") * [![](/images/EntitySprite_creeper.png?703e9)](https://minecraft.wiki/w/Model "Model")[Models](https://minecraft.wiki/w/Model "Model") * [![](/images/BlockSprite_double-stone-slab.png?62750)](https://minecraft.wiki/w/Blockstates_definition "Blockstates definition")[Blockstates](https://minecraft.wiki/w/Blockstates_definition "Blockstates definition") * [![](/images/EnvSprite_item.png?89d23)](https://minecraft.wiki/w/Items_model_definition "Items model definition")[Items](https://minecraft.wiki/w/Items_model_definition "Items model definition") * [![](/images/EnvSprite_ambience.png?d7c92)](https://minecraft.wiki/w/Sound "Sound")[Sounds](https://minecraft.wiki/w/Sound "Sound") ([sounds.json](https://minecraft.wiki/w/Sounds.json "Sounds.json")) * [Shaders](https://minecraft.wiki/w/Shader "Shader") * [![](/images/EnvSprite_texture-pack.png?a4213)](https://minecraft.wiki/w/Resource_pack#Textures "Resource pack")[Textures](https://minecraft.wiki/w/Resource_pack#Textures "Resource pack") * [![](/images/ItemSprite_compass.png?2364d)](https://minecraft.wiki/w/Atlas "Atlas")[Atlases](https://minecraft.wiki/w/Atlas "Atlas") * [Aa](https://minecraft.wiki/w/Font "Font") [Fonts](https://minecraft.wiki/w/Font "Font") * [![](/images/BlockSprite_oak-leaves.png?81553)](https://minecraft.wiki/w/Resource_pack#Colormaps "Resource pack")[Colormaps](https://minecraft.wiki/w/Resource_pack#Colormaps "Resource pack") * ![File file.png: Sprite image for file in Minecraft](/images/thumb/File_file.png/16px-File_file.png?e19ce) [Texts](https://minecraft.wiki/w/Resource_pack#Texts "Resource pack") * [![](/images/Locator_Bar_icon_bowtie.png?a8cd8)](https://minecraft.wiki/w/Waypoint_style "Waypoint style")[Waypoint styles](https://minecraft.wiki/w/Waypoint_style "Waypoint style") * [regional\_compliancies.json](https://minecraft.wiki/w/Resource_pack#Regional_compliancies_warnings "Resource pack") * [![](/images/ItemSprite_all-iron-armor.png?87e31)](https://minecraft.wiki/w/Equipment "Equipment")[Equipment](https://minecraft.wiki/w/Equipment "Equipment") | | Debug | * [Missing font character](https://minecraft.wiki/w/Missing_font_character "Missing font character") * [![](/images/BlockSprite_missingno.png?031f4)](https://minecraft.wiki/w/Missing_model "Missing model")[Missing model](https://minecraft.wiki/w/Missing_model "Missing model") * [![](/images/BlockSprite_missingno.png?031f4)](https://minecraft.wiki/w/Missing_texture "Missing texture")[Missing texture](https://minecraft.wiki/w/Missing_texture "Missing texture") | | Tools | * [Slicer](https://minecraft.wiki/w/Slicer "Slicer")  |  |  | | --- | --- | | Legacy | * [Texture Ender](https://minecraft.wiki/w/Texture_Ender "Texture Ender") * [Unstitcher](https://minecraft.wiki/w/Unstitcher "Unstitcher") | | | Tutorials | * [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Tutorial%3ACreating_a_resource_pack "Tutorial:Creating a resource pack")[Creating](https://minecraft.wiki/w/Tutorial%3ACreating_a_resource_pack "Tutorial:Creating a resource pack") * [![](/images/Download.png?048e3)](https://minecraft.wiki/w/Tutorial%3ALoading_a_resource_pack "Tutorial:Loading a resource pack")[Loading](https://minecraft.wiki/w/Tutorial%3ALoading_a_resource_pack "Tutorial:Loading a resource pack") * [![](/images/EnvSprite_fluids.png?58a6a)](https://minecraft.wiki/w/Tutorial%3AModels "Tutorial:Models")[Models](https://minecraft.wiki/w/Tutorial%3AModels "Tutorial:Models") * [![](/images/EnvSprite_ambience.png?d7c92)](https://minecraft.wiki/w/Tutorial%3ASound_directory "Tutorial:Sound directory")[Sound directory](https://minecraft.wiki/w/Tutorial%3ASound_directory "Tutorial:Sound directory") | | |

Retrieved from "<https://minecraft.wikihttps://minecraft.wiki/w/Java_Edition_data_values?oldid=3568506>"

[Categories](https://minecraft.wiki/w/Special%3ACategories "Special:Categories"):

* [Java Edition](https://minecraft.wiki/w/Category%3AJava_Edition "Category:Java Edition")
* [Java Edition technical](https://minecraft.wiki/w/Category%3AJava_Edition_technical "Category:Java Edition technical")
* [Development](https://minecraft.wiki/w/Category%3ADevelopment "Category:Development")

## Navigation menu

### Personal tools

* [Create account](https://minecraft.wiki/w/Special%3ACreateAccount?returnto=Java+Edition+data+values "You are encouraged to create an account and log in; however, it is not mandatory")
* [Log in](https://minecraft.wiki/w/Special%3AUserLogin?returnto=Java+Edition+data+values "You are encouraged to log in; however, it is not mandatory [o]")

### associated-pages

* [Page](https://minecraft.wiki/w/Java_Edition_data_values "View the content page [c]")
* [Talk](https://minecraft.wiki/w/Talk%3AJava_Edition_data_values "Talk about the content page [t]")

[ ]

English

### Views

* [Read](https://minecraft.wiki/w/Java_Edition_data_values)
* [Edit](https://minecraft.wiki/w/Java_Edition_data_values?veaction=edit "Edit this page [v]")
* [Edit source](https://minecraft.wiki/w/Java_Edition_data_values?action=edit "Edit the source code of this page [e]")
* [View history](https://minecraft.wiki/w/Java_Edition_data_values?action=history "Past revisions of this page [h]")
