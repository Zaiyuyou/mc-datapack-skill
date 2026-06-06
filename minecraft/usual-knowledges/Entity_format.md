# Entity format

From Minecraft Wiki

[Jump to navigation](#mw-head)
[Jump to search](#searchInput)

[![](/images/Information_icon.svg?15c1c)](https://minecraft.wiki/w/File%3AInformation_icon.svg "File:Information icon.svg")

This feature is exclusive to [*Java Edition*](https://minecraft.wiki/w/Java_Edition "Java Edition").

Entities are stored in the entities folder of respective dimension folders. It is stored like *Minecraft* [Anvil format](https://minecraft.wiki/w/Anvil_format "Anvil format") files, which are named in the form `r.x.z.mca`.

[ ]

## Contents

- [Entity format](#entity-format)
  - [Contents](#contents)
  - [Directory structure](#directory-structure)
  - [Entity inheritance](#entity-inheritance)
    - [Abstract classes](#abstract-classes)
    - [Interfaces](#interfaces)
  - [NBT structure](#nbt-structure)
  - [Entity format](#entity-format-1)
    - [Mobs](#mobs)
      - [Mob-specific data](#mob-specific-data)
    - [Projectiles](#projectiles)
    - [Items and XP Orbs](#items-and-xp-orbs)
    - [Vehicles](#vehicles)
    - [Dynamic tiles](#dynamic-tiles)
    - [Display](#display)
    - [Other](#other)
  - [History](#history)
  - [References](#references)
  - [Navigation](#navigation)
  - [Navigation menu](#navigation-menu)
    - [Personal tools](#personal-tools)
    - [associated-pages](#associated-pages)
    - [Views](#views)

## Directory structure


See also: [World § Storage location](https://minecraft.wiki/w/World#Storage_location "World")

* ![File directory.png: Sprite image for directory in Minecraft](/images/thumb/File_directory.png/16px-File_directory.png?8a409) *world save directory*
  + ![File directory.png: Sprite image for directory in Minecraft](/images/thumb/File_directory.png/16px-File_directory.png?8a409) entities: Contains entity files for the [Overworld](https://minecraft.wiki/w/Overworld "Overworld"). These used to be part of region.
    - ![File file.png: Sprite image for file in Minecraft](/images/thumb/File_file.png/16px-File_file.png?e19ce) r.<x>.<z>.mca
  + ![File directory.png: Sprite image for directory in Minecraft](/images/thumb/File_directory.png/16px-File_directory.png?8a409) DIM-1: Contains region files of the [Nether](https://minecraft.wiki/w/Nether "Nether").
    - ![File directory.png: Sprite image for directory in Minecraft](/images/thumb/File_directory.png/16px-File_directory.png?8a409) entities
      * ![File file.png: Sprite image for file in Minecraft](/images/thumb/File_file.png/16px-File_file.png?e19ce) r.<x>.<z>.mca
  + ![File directory.png: Sprite image for directory in Minecraft](/images/thumb/File_directory.png/16px-File_directory.png?8a409) DIM1: Contains region files of [the End](https://minecraft.wiki/w/The_End "The End").
    - ![File directory.png: Sprite image for directory in Minecraft](/images/thumb/File_directory.png/16px-File_directory.png?8a409) entities
      * ![File file.png: Sprite image for file in Minecraft](/images/thumb/File_file.png/16px-File_file.png?e19ce) r.<x>.<z>.mca

## Entity inheritance


Most entities share similar functionalities with each other from abstract classes or interfaces. For instance, horses (and their undead variants), donkeys, camels, mules, and llamas all inherit from Abstract Horse, which share some of its horse-like behaviors and properties to their inheritance. This inheritance can be seen under the [game's code](https://minecraft.wiki/w/Tutorial%3ASee_Minecraft%27s_code "Tutorial:See Minecraft's code") for all of its entities.

An entity that inherits from an abstract class or other entity share their implementation and functionalities with each other, while an entity that inherits from an interface may not necessarily share its functionalities, rather implement the required behaviors from the interface itself. As such, an entity's implementation of the interface may be different from other entities. Any entity may implement multiple interfaces, while only inheriting a single abstract class or other entity.

[![](/images/Information_icon.svg?15c1c)](https://minecraft.wiki/w/File%3AInformation_icon.svg "File:Information icon.svg")

This article is missing information about: Where are sulfur cubes placed?

Please expand the article to include this information. Further details may exist on the [talk page](https://minecraft.wiki/w/Talk%3AEntity_format).

### Abstract classes


* Entity
  + [![](/images/EntitySprite_area-effect-cloud.png?f4c3c)](https://minecraft.wiki/w/Area_Effect_Cloud "Area Effect Cloud")[Area Effect Cloud](https://minecraft.wiki/w/Area_Effect_Cloud "Area Effect Cloud")
  + [![](/images/EntitySprite_end-crystal.png?139be)](https://minecraft.wiki/w/End_Crystal "End Crystal")[End Crystal](https://minecraft.wiki/w/End_Crystal "End Crystal")
  + [![](/images/EntitySprite_evoker-fangs.png?f48c2)](https://minecraft.wiki/w/Evoker_Fangs "Evoker Fangs")[Evoker Fangs](https://minecraft.wiki/w/Evoker_Fangs "Evoker Fangs")
  + [![](/images/EntitySprite_experience-orb.png?7ef2b)](https://minecraft.wiki/w/Experience_Orb "Experience Orb")[Experience Orb](https://minecraft.wiki/w/Experience_Orb "Experience Orb")
  + [![](/images/EntitySprite_eye-of-ender.png?57d43)](https://minecraft.wiki/w/Eye_of_Ender "Eye of Ender")[Eye of Ender](https://minecraft.wiki/w/Eye_of_Ender "Eye of Ender")
  + [![](/images/EntitySprite_all-falling-blocks.png?2d297)](https://minecraft.wiki/w/Falling_Block "Falling Block")[Falling Block Entity](https://minecraft.wiki/w/Falling_Block "Falling Block")
  + [![](/images/BlockSprite_air.png?037f8)](https://minecraft.wiki/w/Interaction "Interaction")[Interaction](https://minecraft.wiki/w/Interaction "Interaction")
  + [![](/images/EnvSprite_item.png?89d23)](https://minecraft.wiki/w/Item_%28entity%29 "Item (entity)")[Item Entity](https://minecraft.wiki/w/Item_%28entity%29 "Item (entity)")
  + [![](/images/BlockSprite_air.png?037f8)](https://minecraft.wiki/w/Marker "Marker")[Marker](https://minecraft.wiki/w/Marker "Marker")
  + [![](/images/EntitySprite_primed-tnt.png?5d12c)](https://minecraft.wiki/w/Primed_TNT "Primed TNT")[Primed TNT](https://minecraft.wiki/w/Primed_TNT "Primed TNT")
  + [![](/images/BlockSprite_air.png?037f8)](https://minecraft.wiki/w/Display "Display")[Display](https://minecraft.wiki/w/Display "Display")
    - [Block Display](https://minecraft.wiki/w/Display "Display")
    - [Item Display](https://minecraft.wiki/w/Display "Display")
    - [Text Display](https://minecraft.wiki/w/Display "Display")
  + Hanging Entity
    - [![](/images/EntitySprite_empty-item-frame.png?22742)](https://minecraft.wiki/w/Item_Frame "Item Frame")[Item Frame](https://minecraft.wiki/w/Item_Frame "Item Frame")
      * [![](/images/EntitySprite_empty-glow-item-frame.png?e240d)](https://minecraft.wiki/w/Glow_Item_Frame "Glow Item Frame")[Glow Item Frame](https://minecraft.wiki/w/Glow_Item_Frame "Glow Item Frame")
    - [![](/images/EntitySprite_leash-knot.png?2d6a1)](https://minecraft.wiki/w/Leash_Knot "Leash Knot")[Leash Fence Knot Entity](https://minecraft.wiki/w/Leash_Knot "Leash Knot")
    - [![](/images/EntitySprite_kebab.png?c74c1)](https://minecraft.wiki/w/Painting "Painting")[Painting](https://minecraft.wiki/w/Painting "Painting")
  + Living Entity

    - [![](/images/EntitySprite_armor-stand.png?6a1bf)](https://minecraft.wiki/w/Armor_Stand "Armor Stand")[Armor Stand](https://minecraft.wiki/w/Armor_Stand "Armor Stand")
    - [![](/images/EntitySprite_alex.png?d5812)](https://minecraft.wiki/w/Mannequin "Mannequin")[Mannequin](https://minecraft.wiki/w/Mannequin "Mannequin")
    - [Mob](https://minecraft.wiki/w/Mob "Mob")
      * [![](/images/EntitySprite_ender-dragon.png?4a397)](https://minecraft.wiki/w/Ender_Dragon "Ender Dragon")[Ender Dragon](https://minecraft.wiki/w/Ender_Dragon "Ender Dragon")
      * Ambient Creature
        + [![](/images/EntitySprite_bat.png?4b561)](https://minecraft.wiki/w/Bat "Bat")[Bat](https://minecraft.wiki/w/Bat "Bat")
      * Flying Mob
        + [![](/images/EntitySprite_ghast.png?f81fc)](https://minecraft.wiki/w/Ghast "Ghast")[Ghast](https://minecraft.wiki/w/Ghast "Ghast")
        + [![](/images/EntitySprite_phantom.png?332bd)](https://minecraft.wiki/w/Phantom "Phantom")[Phantom](https://minecraft.wiki/w/Phantom "Phantom")
      * Pathfinder Mob
        + [![](/images/EntitySprite_allay.png?a939b)](https://minecraft.wiki/w/Allay "Allay")[Allay](https://minecraft.wiki/w/Allay "Allay")
        + Abstract Golem
          - [![](/images/EntitySprite_copper-golem.png?e837d)](https://minecraft.wiki/w/Copper_Golem "Copper Golem")[Copper Golem](https://minecraft.wiki/w/Copper_Golem "Copper Golem")
          - [![](/images/EntitySprite_iron-golem.png?bb037)](https://minecraft.wiki/w/Iron_Golem "Iron Golem")[Iron Golem](https://minecraft.wiki/w/Iron_Golem "Iron Golem")
          - [![](/images/EntitySprite_shulker.png?ca1f9)](https://minecraft.wiki/w/Shulker "Shulker")[Shulker](https://minecraft.wiki/w/Shulker "Shulker")
          - [![](/images/EntitySprite_pumpkin-snow-golem.png?e81b0)](https://minecraft.wiki/w/Snow_Golem "Snow Golem")[Snow Golem](https://minecraft.wiki/w/Snow_Golem "Snow Golem")
        + Ageable Mob
          - Abstract Villager
            * [![](/images/EntitySprite_villager.png?05433)](https://minecraft.wiki/w/Villager "Villager")[Villager](https://minecraft.wiki/w/Villager "Villager")
            * [![](/images/EntitySprite_wandering-trader.png?0f9fa)](https://minecraft.wiki/w/Wandering_Trader "Wandering Trader")[Wandering Trader](https://minecraft.wiki/w/Wandering_Trader "Wandering Trader")
          - [Animal](https://minecraft.wiki/w/Animal "Animal")

            * [![](/images/EntitySprite_armadillo.png?89a6e)](https://minecraft.wiki/w/Armadillo "Armadillo")[Armadillo](https://minecraft.wiki/w/Armadillo "Armadillo")
            * [![](/images/EntitySprite_axolotl.png?0b5f0)](https://minecraft.wiki/w/Axolotl "Axolotl")[Axolotl](https://minecraft.wiki/w/Axolotl "Axolotl")
            * [![](/images/EntitySprite_bee.png?5d625)](https://minecraft.wiki/w/Bee "Bee")[Bee](https://minecraft.wiki/w/Bee "Bee")
            * [![](/images/EntitySprite_chicken.png?be6aa)](https://minecraft.wiki/w/Chicken "Chicken")[Chicken](https://minecraft.wiki/w/Chicken "Chicken")
            * [![](/images/EntitySprite_fox.png?91c80)](https://minecraft.wiki/w/Fox "Fox")[Fox](https://minecraft.wiki/w/Fox "Fox")
            * [![](/images/EntitySprite_frog.png?15793)](https://minecraft.wiki/w/Frog "Frog")[Frog](https://minecraft.wiki/w/Frog "Frog")
            * [![](/images/EntitySprite_goat.png?f85ec)](https://minecraft.wiki/w/Goat "Goat")[Goat](https://minecraft.wiki/w/Goat "Goat")
            * [![](/images/EntitySprite_happy-ghast.png?45cc0)](https://minecraft.wiki/w/Happy_Ghast "Happy Ghast")[Happy Ghast](https://minecraft.wiki/w/Happy_Ghast "Happy Ghast")
            * [![](/images/EntitySprite_hoglin.png?06402)](https://minecraft.wiki/w/Hoglin "Hoglin")[Hoglin](https://minecraft.wiki/w/Hoglin "Hoglin")
            * [![](/images/EntitySprite_ocelot.png?e0135)](https://minecraft.wiki/w/Ocelot "Ocelot")[Ocelot](https://minecraft.wiki/w/Ocelot "Ocelot")
            * [![](/images/EntitySprite_normal-panda.png?ef307)](https://minecraft.wiki/w/Panda "Panda")[Panda](https://minecraft.wiki/w/Panda "Panda")
            * [![](/images/EntitySprite_pig.png?5435e)](https://minecraft.wiki/w/Pig "Pig")[Pig](https://minecraft.wiki/w/Pig "Pig")
            * [![](/images/EntitySprite_polar-bear.png?41cea)](https://minecraft.wiki/w/Polar_Bear "Polar Bear")[Polar Bear](https://minecraft.wiki/w/Polar_Bear "Polar Bear")
            * [![](/images/EntitySprite_brown-rabbit.png?18569)](https://minecraft.wiki/w/Rabbit "Rabbit")[Rabbit](https://minecraft.wiki/w/Rabbit "Rabbit")
            * [![](/images/EntitySprite_sheep.png?bd14e)](https://minecraft.wiki/w/Sheep "Sheep")[Sheep](https://minecraft.wiki/w/Sheep "Sheep")
            * [![](/images/EntitySprite_sniffer.png?502b1)](https://minecraft.wiki/w/Sniffer "Sniffer")[Sniffer](https://minecraft.wiki/w/Sniffer "Sniffer")
            * [![](/images/EntitySprite_strider.png?c3ab9)](https://minecraft.wiki/w/Strider "Strider")[Strider](https://minecraft.wiki/w/Strider "Strider")
            * [![](/images/EntitySprite_turtle.png?75264)](https://minecraft.wiki/w/Turtle "Turtle")[Turtle](https://minecraft.wiki/w/Turtle "Turtle")
            * Abstract Horse
              + [![](/images/EntitySprite_camel.png?73196)](https://minecraft.wiki/w/Camel "Camel")[Camel](https://minecraft.wiki/w/Camel "Camel")
                - [![](/images/EntitySprite_camel-husk.png?304cb)](https://minecraft.wiki/w/Camel_Husk "Camel Husk")[Camel Husk](https://minecraft.wiki/w/Camel_Husk "Camel Husk")
              + [![](/images/EntitySprite_creamy-horse.png?3d52b)](https://minecraft.wiki/w/Horse "Horse")[Horse](https://minecraft.wiki/w/Horse "Horse")
              + [![](/images/EntitySprite_skeleton-horse.png?3cde9)](https://minecraft.wiki/w/Skeleton_Horse "Skeleton Horse")[Skeleton Horse](https://minecraft.wiki/w/Skeleton_Horse "Skeleton Horse")
              + [![](/images/EntitySprite_zombie-horse.png?f1a1f)](https://minecraft.wiki/w/Zombie_Horse "Zombie Horse")[Zombie Horse](https://minecraft.wiki/w/Zombie_Horse "Zombie Horse")
              + Abstract Chested Horse
                - [![](/images/EntitySprite_donkey.png?1910f)](https://minecraft.wiki/w/Donkey "Donkey")[Donkey](https://minecraft.wiki/w/Donkey "Donkey")
                - [![](/images/EntitySprite_mule.png?a1576)](https://minecraft.wiki/w/Mule "Mule")[Mule](https://minecraft.wiki/w/Mule "Mule")
                - [![](/images/EntitySprite_creamy-llama.png?0657f)](https://minecraft.wiki/w/Llama "Llama")[Llama](https://minecraft.wiki/w/Llama "Llama")
                  * [![](/images/EntitySprite_creamy-trader-llama.png?6d474)](https://minecraft.wiki/w/Trader_Llama "Trader Llama")[Trader Llama](https://minecraft.wiki/w/Trader_Llama "Trader Llama")
            * [![](/images/EntitySprite_cow.png?893cf)](https://minecraft.wiki/w/Cow "Cow")[Cow](https://minecraft.wiki/w/Cow "Cow")
              + [![](/images/EntitySprite_mooshroom.png?92493)](https://minecraft.wiki/w/Mooshroom "Mooshroom")[Mushroom Cow](https://minecraft.wiki/w/Mooshroom "Mooshroom")
            * Tamable Animal
              + [![](/images/EntitySprite_cat.png?b3c67)](https://minecraft.wiki/w/Cat "Cat")[Cat](https://minecraft.wiki/w/Cat "Cat")
              + [![](/images/EntitySprite_wolf.png?77c1e)](https://minecraft.wiki/w/Wolf "Wolf")[Wolf](https://minecraft.wiki/w/Wolf "Wolf")
              + Abstract Nautilus
                - [![](/images/EntitySprite_nautilus.png?3bfe0)](https://minecraft.wiki/w/Nautilus "Nautilus")[Nautilus](https://minecraft.wiki/w/Nautilus "Nautilus")
                - [![](/images/EntitySprite_zombie-nautilus.png?56e70)](https://minecraft.wiki/w/Zombie_Nautilus "Zombie Nautilus")[Zombie Nautilus](https://minecraft.wiki/w/Zombie_Nautilus "Zombie Nautilus")
              + Shoulder Riding Entity
                - [![](/images/EntitySprite_parrot.png?8ab80)](https://minecraft.wiki/w/Parrot "Parrot")[Parrot](https://minecraft.wiki/w/Parrot "Parrot")
        + [Monster](https://minecraft.wiki/w/Monster "Monster")

          - [![](/images/EntitySprite_blaze.png?43a55)](https://minecraft.wiki/w/Blaze "Blaze")[Blaze](https://minecraft.wiki/w/Blaze "Blaze")
          - [![](/images/EntitySprite_breeze.png?cd2af)](https://minecraft.wiki/w/Breeze "Breeze")[Breeze](https://minecraft.wiki/w/Breeze "Breeze")
          - [![](/images/EntitySprite_creaking.png?6b7fb)](https://minecraft.wiki/w/Creaking "Creaking")[Creaking](https://minecraft.wiki/w/Creaking "Creaking")
          - [![](/images/EntitySprite_creeper.png?703e9)](https://minecraft.wiki/w/Creeper "Creeper")[Creeper](https://minecraft.wiki/w/Creeper "Creeper")
          - [![](/images/EntitySprite_enderman.png?c703a)](https://minecraft.wiki/w/Enderman "Enderman")[Enderman](https://minecraft.wiki/w/Enderman "Enderman")
          - [![](/images/EntitySprite_endermite.png?71743)](https://minecraft.wiki/w/Endermite "Endermite")[Endermite](https://minecraft.wiki/w/Endermite "Endermite")
          - [![](/images/EntitySprite_zombie.png?ce11f)](https://minecraft.wiki/w/Giant "Giant")[Giant](https://minecraft.wiki/w/Giant "Giant")
          - [![](/images/EntitySprite_silverfish.png?0656c)](https://minecraft.wiki/w/Silverfish "Silverfish")[Silverfish](https://minecraft.wiki/w/Silverfish "Silverfish")
          - [![](/images/EntitySprite_vex.png?646cb)](https://minecraft.wiki/w/Vex "Vex")[Vex](https://minecraft.wiki/w/Vex "Vex")
          - [![](/images/EntitySprite_warden.png?d9d2f)](https://minecraft.wiki/w/Warden "Warden")[Warden](https://minecraft.wiki/w/Warden "Warden")
          - [![](/images/EntitySprite_wither.png?fb756)](https://minecraft.wiki/w/Wither "Wither")[Wither Boss](https://minecraft.wiki/w/Wither "Wither")
          - [![](/images/EntitySprite_zoglin.png?09afa)](https://minecraft.wiki/w/Zoglin "Zoglin")[Zoglin](https://minecraft.wiki/w/Zoglin "Zoglin")
          - Abstract Piglin
            * [![](/images/EntitySprite_piglin.png?5435e)](https://minecraft.wiki/w/Piglin "Piglin")[Piglin](https://minecraft.wiki/w/Piglin "Piglin")
            * [![](/images/EntitySprite_piglin-brute.png?56ccd)](https://minecraft.wiki/w/Piglin_Brute "Piglin Brute")[Piglin Brute](https://minecraft.wiki/w/Piglin_Brute "Piglin Brute")
          - Abstract Skeleton
            * [![](/images/EntitySprite_bogged.png?2cf56)](https://minecraft.wiki/w/Bogged "Bogged")[Bogged](https://minecraft.wiki/w/Bogged "Bogged")
            * [![](/images/EntitySprite_parched.png?e7709)](https://minecraft.wiki/w/Parched "Parched")[Parched](https://minecraft.wiki/w/Parched "Parched")
            * [![](/images/EntitySprite_skeleton.png?ff904)](https://minecraft.wiki/w/Skeleton "Skeleton")[Skeleton](https://minecraft.wiki/w/Skeleton "Skeleton")
            * [![](/images/EntitySprite_stray.png?f338b)](https://minecraft.wiki/w/Stray "Stray")[Stray](https://minecraft.wiki/w/Stray "Stray")
            * [![](/images/EntitySprite_wither-skeleton.png?8b1cd)](https://minecraft.wiki/w/Wither_Skeleton "Wither Skeleton")[Wither Skeleton](https://minecraft.wiki/w/Wither_Skeleton "Wither Skeleton")
          - [![](/images/EntitySprite_guardian.png?da544)](https://minecraft.wiki/w/Guardian "Guardian")[Guardian](https://minecraft.wiki/w/Guardian "Guardian")
            * [![](/images/EntitySprite_elder-guardian.png?17494)](https://minecraft.wiki/w/Elder_Guardian "Elder Guardian")[Elder Guardian](https://minecraft.wiki/w/Elder_Guardian "Elder Guardian")
          - Patrolling Monster
            * Raider
              + [![](/images/EntitySprite_ravager.png?40196)](https://minecraft.wiki/w/Ravager "Ravager")[Ravager](https://minecraft.wiki/w/Ravager "Ravager")
              + [![](/images/EntitySprite_witch.png?3daa8)](https://minecraft.wiki/w/Witch "Witch")[Witch](https://minecraft.wiki/w/Witch "Witch")
              + Abstract Illager
                - [![](/images/EntitySprite_evoker.png?f236e)](https://minecraft.wiki/w/Pillager "Pillager")[Pillager](https://minecraft.wiki/w/Pillager "Pillager")
                - [![](/images/EntitySprite_johnny.png?6d568)](https://minecraft.wiki/w/Vindicator "Vindicator")[Vindicator](https://minecraft.wiki/w/Vindicator "Vindicator")
                - Spellcaster Illager
                  * [![](/images/EntitySprite_evoker.png?f236e)](https://minecraft.wiki/w/Evoker "Evoker")[Evoker](https://minecraft.wiki/w/Evoker "Evoker")
                  * [![](/images/EntitySprite_illusioner.png?e50b9)](https://minecraft.wiki/w/Illusioner "Illusioner")[Illusioner](https://minecraft.wiki/w/Illusioner "Illusioner")
          - [![](/images/EntitySprite_spider.png?4ee43)](https://minecraft.wiki/w/Spider "Spider")[Spider](https://minecraft.wiki/w/Spider "Spider")
            * [![](/images/EntitySprite_cave-spider.png?3e94c)](https://minecraft.wiki/w/Cave_Spider "Cave Spider")[Cave Spider](https://minecraft.wiki/w/Cave_Spider "Cave Spider")
          - [![](/images/EntitySprite_zombie.png?ce11f)](https://minecraft.wiki/w/Zombie "Zombie")[Zombie](https://minecraft.wiki/w/Zombie "Zombie")
            * [![](/images/EntitySprite_drowned.png?ef369)](https://minecraft.wiki/w/Drowned "Drowned")[Drowned](https://minecraft.wiki/w/Drowned "Drowned")
            * [![](/images/EntitySprite_husk.png?99086)](https://minecraft.wiki/w/Husk "Husk")[Husk](https://minecraft.wiki/w/Husk "Husk")
            * [![](/images/EntitySprite_zombie-villager.png?8183e)](https://minecraft.wiki/w/Zombie_Villager "Zombie Villager")[Zombie Villager](https://minecraft.wiki/w/Zombie_Villager "Zombie Villager")
            * [![](/images/EntitySprite_zombified-piglin.png?8dfea)](https://minecraft.wiki/w/Zombified_Piglin "Zombified Piglin")[Zombified Piglin](https://minecraft.wiki/w/Zombified_Piglin "Zombified Piglin")
        + Water Animal
          - [![](/images/EntitySprite_dolphin.png?1910f)](https://minecraft.wiki/w/Dolphin "Dolphin")[Dolphin](https://minecraft.wiki/w/Dolphin "Dolphin")
          - Abstract Fish
            * [![](/images/EntitySprite_pufferfish.png?08be3)](https://minecraft.wiki/w/Pufferfish "Pufferfish")[Pufferfish](https://minecraft.wiki/w/Pufferfish "Pufferfish")
            * [![](/images/EntitySprite_tadpole.png?532f2)](https://minecraft.wiki/w/Tadpole "Tadpole")[Tadpole](https://minecraft.wiki/w/Tadpole "Tadpole")
            * Abstract Schooling Fish
              + [![](/images/EntitySprite_cod.png?dc4af)](https://minecraft.wiki/w/Cod "Cod")[Cod](https://minecraft.wiki/w/Cod "Cod")
              + [![](/images/EntitySprite_salmon.png?d308d)](https://minecraft.wiki/w/Salmon "Salmon")[Salmon](https://minecraft.wiki/w/Salmon "Salmon")
              + [![](/images/EntitySprite_tropical-fish.png?ee953)](https://minecraft.wiki/w/Tropical_Fish "Tropical Fish")[Tropical Fish](https://minecraft.wiki/w/Tropical_Fish "Tropical Fish")
          - [![](/images/EntitySprite_squid.png?b1318)](https://minecraft.wiki/w/Squid "Squid")[Squid](https://minecraft.wiki/w/Squid "Squid")
            * [![](/images/EntitySprite_glow-squid.png?4b4d8)](https://minecraft.wiki/w/Glow_Squid "Glow Squid")[Glow Squid](https://minecraft.wiki/w/Glow_Squid "Glow Squid")
      * [![](/images/EntitySprite_slime.png?1c782)](https://minecraft.wiki/w/Slime "Slime")[Slime](https://minecraft.wiki/w/Slime "Slime")
        + [![](/images/EntitySprite_magma-cube.png?0a89c)](https://minecraft.wiki/w/Magma_Cube "Magma Cube")[Magma Cube](https://minecraft.wiki/w/Magma_Cube "Magma Cube")
    - [![](/images/EntitySprite_steve.png?856f8)](https://minecraft.wiki/w/Player "Player")[Player](https://minecraft.wiki/w/Player "Player")
      * Server Player
      * Abstract Client Player
        + Local Player
        + Remote Player
  + [Projectile](https://minecraft.wiki/w/Projectile "Projectile")

    - [![](/images/ItemSprite_firework-rocket.png?9f724)](https://minecraft.wiki/w/Firework_Rocket "Firework Rocket")[Firework Rocket Entity](https://minecraft.wiki/w/Firework_Rocket "Firework Rocket")
    - [![](/images/EntitySprite_fishing-bobber.png?26df9)](https://minecraft.wiki/w/Fishing_Bobber "Fishing Bobber")[Fishing Hook](https://minecraft.wiki/w/Fishing_Bobber "Fishing Bobber")
    - [![](/images/EntitySprite_llama-spit.png?10b82)](https://minecraft.wiki/w/Llama_Spit "Llama Spit")[Llama Spit](https://minecraft.wiki/w/Llama_Spit "Llama Spit")
    - [![](/images/EntitySprite_shulker-bullet.png?1b532)](https://minecraft.wiki/w/Shulker_Bullet "Shulker Bullet")[Shulker Bullet](https://minecraft.wiki/w/Shulker_Bullet "Shulker Bullet")
    - Abstract Arrow
      * [![](/images/EntitySprite_arrow.png?123f9)](https://minecraft.wiki/w/Arrow "Arrow")[Arrow](https://minecraft.wiki/w/Arrow "Arrow")
      * [![](/images/EntitySprite_spectral-arrow.png?fcc49)](https://minecraft.wiki/w/Spectral_Arrow "Spectral Arrow")[Spectral Arrow](https://minecraft.wiki/w/Spectral_Arrow "Spectral Arrow")
      * [![](/images/EntitySprite_trident.png?b634b)](https://minecraft.wiki/w/Trident "Trident")[Thrown Trident](https://minecraft.wiki/w/Trident "Trident")
    - Abstract Hurting Projectile
      * [![](/images/EntitySprite_dragon-fireball.png?24df0)](https://minecraft.wiki/w/Dragon_Fireball "Dragon Fireball")[Dragon Fireball](https://minecraft.wiki/w/Dragon_Fireball "Dragon Fireball")
      * [![](/images/EntitySprite_wither-skull.png?0be34)](https://minecraft.wiki/w/Wither#Wither_Skull "Wither")[Wither Skull Entity](https://minecraft.wiki/w/Wither#Wither_Skull "Wither")
      * Abstract Wind Charge
        + [![](/images/EntitySprite_wind-charge.png?cd158)](https://minecraft.wiki/w/Breeze_Wind_Charge "Breeze Wind Charge")[Breeze Wind Charge](https://minecraft.wiki/w/Breeze_Wind_Charge "Breeze Wind Charge")
        + [![](/images/EntitySprite_wind-charge.png?cd158)](https://minecraft.wiki/w/Wind_Charge "Wind Charge")[Wind Charge](https://minecraft.wiki/w/Wind_Charge "Wind Charge")
      * [Fireball](https://minecraft.wiki/w/Fireball "Fireball")
        + [![](/images/EntitySprite_fireball.png?ffb0c)](https://minecraft.wiki/w/Fireball "Fireball")[Large Fireball](https://minecraft.wiki/w/Fireball "Fireball")
        + [![](/images/EntitySprite_fireball.png?ffb0c)](https://minecraft.wiki/w/Small_Fireball "Small Fireball")[Small Fireball](https://minecraft.wiki/w/Small_Fireball "Small Fireball")
    - Throwable Projectile
      * Throwable Item Projectile
        + [![](/images/ItemSprite_snowball.png?f4d05)](https://minecraft.wiki/w/Snowball "Snowball")[Thrown Snowball](https://minecraft.wiki/w/Snowball "Snowball")
        + [![](/images/ItemSprite_egg.png?2d314)](https://minecraft.wiki/w/Egg "Egg")[Thrown Egg](https://minecraft.wiki/w/Egg "Egg")
        + [![](/images/ItemSprite_ender-pearl.png?af209)](https://minecraft.wiki/w/Ender_Pearl "Ender Pearl")[Thrown Ender Pearl](https://minecraft.wiki/w/Ender_Pearl "Ender Pearl")
        + [![](/images/ItemSprite_eye-of-ender.png?9614f)](https://minecraft.wiki/w/Eye_of_Ender "Eye of Ender")[Thrown Eye of Ender](https://minecraft.wiki/w/Eye_of_Ender "Eye of Ender")
        + [![](/images/ItemSprite_bottle-o%27-enchanting.png?e5746)](https://minecraft.wiki/w/Bottle_o%27_Enchanting "Bottle o' Enchanting")[Thrown Experience Bottle](https://minecraft.wiki/w/Bottle_o%27_Enchanting "Bottle o' Enchanting")
        + [![](/images/ItemSprite_splash-water-bottle.png?24203)](https://minecraft.wiki/w/Splash_Potion "Splash Potion")[Thrown Potion](https://minecraft.wiki/w/Splash_Potion "Splash Potion")
  + Vehicle Entity

    - Abstract Minecart
      * [![](/images/EntitySprite_minecart.png?23526)](https://minecraft.wiki/w/Minecart "Minecart")[Minecart](https://minecraft.wiki/w/Minecart "Minecart")
      * [![](/images/EntitySprite_minecart-command-block.png?fedfd)](https://minecraft.wiki/w/Minecart_with_Command_Block "Minecart with Command Block")[Minecart Command Block](https://minecraft.wiki/w/Minecart_with_Command_Block "Minecart with Command Block")
      * [![](/images/EntitySprite_minecart-furnace.png?87f22)](https://minecraft.wiki/w/Minecart_with_Furnace "Minecart with Furnace")[Minecart Furnace](https://minecraft.wiki/w/Minecart_with_Furnace "Minecart with Furnace")
      * [![](/images/EntitySprite_minecart-monster-spawner.png?e5c66)](https://minecraft.wiki/w/Minecart_with_Spawner "Minecart with Spawner")[Minecart Spawner](https://minecraft.wiki/w/Minecart_with_Spawner "Minecart with Spawner")
      * [![](/images/EntitySprite_minecart-tnt.png?26bb0)](https://minecraft.wiki/w/Minecart_with_TNT "Minecart with TNT")[Minecart TNT](https://minecraft.wiki/w/Minecart_with_TNT "Minecart with TNT")
      * Abstract Minecart Container
        + [![](/images/EntitySprite_minecart-chest.png?fedfd)](https://minecraft.wiki/w/Minecart_with_Chest "Minecart with Chest")[Minecart Chest](https://minecraft.wiki/w/Minecart_with_Chest "Minecart with Chest")
        + [![](/images/EntitySprite_minecart-hopper.png?e5c66)](https://minecraft.wiki/w/Minecart_with_Hopper "Minecart with Hopper")[Minecart Hopper](https://minecraft.wiki/w/Minecart_with_Hopper "Minecart with Hopper")
    - [![](/images/EntitySprite_all-boats.png?6b19e)](https://minecraft.wiki/w/Boat "Boat")[Boat](https://minecraft.wiki/w/Boat "Boat")
      * [![](/images/EntitySprite_all-boats-with-chests.png?6b19e)](https://minecraft.wiki/w/Boat_with_Chest "Boat with Chest")[Chest Boat](https://minecraft.wiki/w/Boat_with_Chest "Boat with Chest")

* [![](/images/EntitySprite_ender-dragon.png?4a397)](https://minecraft.wiki/w/Ender_Dragon "Ender Dragon")[Ender Dragon](https://minecraft.wiki/w/Ender_Dragon "Ender Dragon")
* Ambient Creature
  + [![](/images/EntitySprite_bat.png?4b561)](https://minecraft.wiki/w/Bat "Bat")[Bat](https://minecraft.wiki/w/Bat "Bat")
* Flying Mob
  + [![](/images/EntitySprite_ghast.png?f81fc)](https://minecraft.wiki/w/Ghast "Ghast")[Ghast](https://minecraft.wiki/w/Ghast "Ghast")
  + [![](/images/EntitySprite_phantom.png?332bd)](https://minecraft.wiki/w/Phantom "Phantom")[Phantom](https://minecraft.wiki/w/Phantom "Phantom")
* Pathfinder Mob
  + [![](/images/EntitySprite_allay.png?a939b)](https://minecraft.wiki/w/Allay "Allay")[Allay](https://minecraft.wiki/w/Allay "Allay")
  + Abstract Golem
    - [![](/images/EntitySprite_copper-golem.png?e837d)](https://minecraft.wiki/w/Copper_Golem "Copper Golem")[Copper Golem](https://minecraft.wiki/w/Copper_Golem "Copper Golem")
    - [![](/images/EntitySprite_iron-golem.png?bb037)](https://minecraft.wiki/w/Iron_Golem "Iron Golem")[Iron Golem](https://minecraft.wiki/w/Iron_Golem "Iron Golem")
    - [![](/images/EntitySprite_shulker.png?ca1f9)](https://minecraft.wiki/w/Shulker "Shulker")[Shulker](https://minecraft.wiki/w/Shulker "Shulker")
    - [![](/images/EntitySprite_pumpkin-snow-golem.png?e81b0)](https://minecraft.wiki/w/Snow_Golem "Snow Golem")[Snow Golem](https://minecraft.wiki/w/Snow_Golem "Snow Golem")
  + Ageable Mob
    - Abstract Villager
      * [![](/images/EntitySprite_villager.png?05433)](https://minecraft.wiki/w/Villager "Villager")[Villager](https://minecraft.wiki/w/Villager "Villager")
      * [![](/images/EntitySprite_wandering-trader.png?0f9fa)](https://minecraft.wiki/w/Wandering_Trader "Wandering Trader")[Wandering Trader](https://minecraft.wiki/w/Wandering_Trader "Wandering Trader")
    - [Animal](https://minecraft.wiki/w/Animal "Animal")

      * [![](/images/EntitySprite_armadillo.png?89a6e)](https://minecraft.wiki/w/Armadillo "Armadillo")[Armadillo](https://minecraft.wiki/w/Armadillo "Armadillo")
      * [![](/images/EntitySprite_axolotl.png?0b5f0)](https://minecraft.wiki/w/Axolotl "Axolotl")[Axolotl](https://minecraft.wiki/w/Axolotl "Axolotl")
      * [![](/images/EntitySprite_bee.png?5d625)](https://minecraft.wiki/w/Bee "Bee")[Bee](https://minecraft.wiki/w/Bee "Bee")
      * [![](/images/EntitySprite_chicken.png?be6aa)](https://minecraft.wiki/w/Chicken "Chicken")[Chicken](https://minecraft.wiki/w/Chicken "Chicken")
      * [![](/images/EntitySprite_fox.png?91c80)](https://minecraft.wiki/w/Fox "Fox")[Fox](https://minecraft.wiki/w/Fox "Fox")
      * [![](/images/EntitySprite_frog.png?15793)](https://minecraft.wiki/w/Frog "Frog")[Frog](https://minecraft.wiki/w/Frog "Frog")
      * [![](/images/EntitySprite_goat.png?f85ec)](https://minecraft.wiki/w/Goat "Goat")[Goat](https://minecraft.wiki/w/Goat "Goat")
      * [![](/images/EntitySprite_happy-ghast.png?45cc0)](https://minecraft.wiki/w/Happy_Ghast "Happy Ghast")[Happy Ghast](https://minecraft.wiki/w/Happy_Ghast "Happy Ghast")
      * [![](/images/EntitySprite_hoglin.png?06402)](https://minecraft.wiki/w/Hoglin "Hoglin")[Hoglin](https://minecraft.wiki/w/Hoglin "Hoglin")
      * [![](/images/EntitySprite_ocelot.png?e0135)](https://minecraft.wiki/w/Ocelot "Ocelot")[Ocelot](https://minecraft.wiki/w/Ocelot "Ocelot")
      * [![](/images/EntitySprite_normal-panda.png?ef307)](https://minecraft.wiki/w/Panda "Panda")[Panda](https://minecraft.wiki/w/Panda "Panda")
      * [![](/images/EntitySprite_pig.png?5435e)](https://minecraft.wiki/w/Pig "Pig")[Pig](https://minecraft.wiki/w/Pig "Pig")
      * [![](/images/EntitySprite_polar-bear.png?41cea)](https://minecraft.wiki/w/Polar_Bear "Polar Bear")[Polar Bear](https://minecraft.wiki/w/Polar_Bear "Polar Bear")
      * [![](/images/EntitySprite_brown-rabbit.png?18569)](https://minecraft.wiki/w/Rabbit "Rabbit")[Rabbit](https://minecraft.wiki/w/Rabbit "Rabbit")
      * [![](/images/EntitySprite_sheep.png?bd14e)](https://minecraft.wiki/w/Sheep "Sheep")[Sheep](https://minecraft.wiki/w/Sheep "Sheep")
      * [![](/images/EntitySprite_sniffer.png?502b1)](https://minecraft.wiki/w/Sniffer "Sniffer")[Sniffer](https://minecraft.wiki/w/Sniffer "Sniffer")
      * [![](/images/EntitySprite_strider.png?c3ab9)](https://minecraft.wiki/w/Strider "Strider")[Strider](https://minecraft.wiki/w/Strider "Strider")
      * [![](/images/EntitySprite_turtle.png?75264)](https://minecraft.wiki/w/Turtle "Turtle")[Turtle](https://minecraft.wiki/w/Turtle "Turtle")
      * Abstract Horse
        + [![](/images/EntitySprite_camel.png?73196)](https://minecraft.wiki/w/Camel "Camel")[Camel](https://minecraft.wiki/w/Camel "Camel")
          - [![](/images/EntitySprite_camel-husk.png?304cb)](https://minecraft.wiki/w/Camel_Husk "Camel Husk")[Camel Husk](https://minecraft.wiki/w/Camel_Husk "Camel Husk")
        + [![](/images/EntitySprite_creamy-horse.png?3d52b)](https://minecraft.wiki/w/Horse "Horse")[Horse](https://minecraft.wiki/w/Horse "Horse")
        + [![](/images/EntitySprite_skeleton-horse.png?3cde9)](https://minecraft.wiki/w/Skeleton_Horse "Skeleton Horse")[Skeleton Horse](https://minecraft.wiki/w/Skeleton_Horse "Skeleton Horse")
        + [![](/images/EntitySprite_zombie-horse.png?f1a1f)](https://minecraft.wiki/w/Zombie_Horse "Zombie Horse")[Zombie Horse](https://minecraft.wiki/w/Zombie_Horse "Zombie Horse")
        + Abstract Chested Horse
          - [![](/images/EntitySprite_donkey.png?1910f)](https://minecraft.wiki/w/Donkey "Donkey")[Donkey](https://minecraft.wiki/w/Donkey "Donkey")
          - [![](/images/EntitySprite_mule.png?a1576)](https://minecraft.wiki/w/Mule "Mule")[Mule](https://minecraft.wiki/w/Mule "Mule")
          - [![](/images/EntitySprite_creamy-llama.png?0657f)](https://minecraft.wiki/w/Llama "Llama")[Llama](https://minecraft.wiki/w/Llama "Llama")
            * [![](/images/EntitySprite_creamy-trader-llama.png?6d474)](https://minecraft.wiki/w/Trader_Llama "Trader Llama")[Trader Llama](https://minecraft.wiki/w/Trader_Llama "Trader Llama")
      * [![](/images/EntitySprite_cow.png?893cf)](https://minecraft.wiki/w/Cow "Cow")[Cow](https://minecraft.wiki/w/Cow "Cow")
        + [![](/images/EntitySprite_mooshroom.png?92493)](https://minecraft.wiki/w/Mooshroom "Mooshroom")[Mushroom Cow](https://minecraft.wiki/w/Mooshroom "Mooshroom")
      * Tamable Animal
        + [![](/images/EntitySprite_cat.png?b3c67)](https://minecraft.wiki/w/Cat "Cat")[Cat](https://minecraft.wiki/w/Cat "Cat")
        + [![](/images/EntitySprite_wolf.png?77c1e)](https://minecraft.wiki/w/Wolf "Wolf")[Wolf](https://minecraft.wiki/w/Wolf "Wolf")
        + Abstract Nautilus
          - [![](/images/EntitySprite_nautilus.png?3bfe0)](https://minecraft.wiki/w/Nautilus "Nautilus")[Nautilus](https://minecraft.wiki/w/Nautilus "Nautilus")
          - [![](/images/EntitySprite_zombie-nautilus.png?56e70)](https://minecraft.wiki/w/Zombie_Nautilus "Zombie Nautilus")[Zombie Nautilus](https://minecraft.wiki/w/Zombie_Nautilus "Zombie Nautilus")
        + Shoulder Riding Entity
          - [![](/images/EntitySprite_parrot.png?8ab80)](https://minecraft.wiki/w/Parrot "Parrot")[Parrot](https://minecraft.wiki/w/Parrot "Parrot")
  + [Monster](https://minecraft.wiki/w/Monster "Monster")

    - [![](/images/EntitySprite_blaze.png?43a55)](https://minecraft.wiki/w/Blaze "Blaze")[Blaze](https://minecraft.wiki/w/Blaze "Blaze")
    - [![](/images/EntitySprite_breeze.png?cd2af)](https://minecraft.wiki/w/Breeze "Breeze")[Breeze](https://minecraft.wiki/w/Breeze "Breeze")
    - [![](/images/EntitySprite_creaking.png?6b7fb)](https://minecraft.wiki/w/Creaking "Creaking")[Creaking](https://minecraft.wiki/w/Creaking "Creaking")
    - [![](/images/EntitySprite_creeper.png?703e9)](https://minecraft.wiki/w/Creeper "Creeper")[Creeper](https://minecraft.wiki/w/Creeper "Creeper")
    - [![](/images/EntitySprite_enderman.png?c703a)](https://minecraft.wiki/w/Enderman "Enderman")[Enderman](https://minecraft.wiki/w/Enderman "Enderman")
    - [![](/images/EntitySprite_endermite.png?71743)](https://minecraft.wiki/w/Endermite "Endermite")[Endermite](https://minecraft.wiki/w/Endermite "Endermite")
    - [![](/images/EntitySprite_zombie.png?ce11f)](https://minecraft.wiki/w/Giant "Giant")[Giant](https://minecraft.wiki/w/Giant "Giant")
    - [![](/images/EntitySprite_silverfish.png?0656c)](https://minecraft.wiki/w/Silverfish "Silverfish")[Silverfish](https://minecraft.wiki/w/Silverfish "Silverfish")
    - [![](/images/EntitySprite_vex.png?646cb)](https://minecraft.wiki/w/Vex "Vex")[Vex](https://minecraft.wiki/w/Vex "Vex")
    - [![](/images/EntitySprite_warden.png?d9d2f)](https://minecraft.wiki/w/Warden "Warden")[Warden](https://minecraft.wiki/w/Warden "Warden")
    - [![](/images/EntitySprite_wither.png?fb756)](https://minecraft.wiki/w/Wither "Wither")[Wither Boss](https://minecraft.wiki/w/Wither "Wither")
    - [![](/images/EntitySprite_zoglin.png?09afa)](https://minecraft.wiki/w/Zoglin "Zoglin")[Zoglin](https://minecraft.wiki/w/Zoglin "Zoglin")
    - Abstract Piglin
      * [![](/images/EntitySprite_piglin.png?5435e)](https://minecraft.wiki/w/Piglin "Piglin")[Piglin](https://minecraft.wiki/w/Piglin "Piglin")
      * [![](/images/EntitySprite_piglin-brute.png?56ccd)](https://minecraft.wiki/w/Piglin_Brute "Piglin Brute")[Piglin Brute](https://minecraft.wiki/w/Piglin_Brute "Piglin Brute")
    - Abstract Skeleton
      * [![](/images/EntitySprite_bogged.png?2cf56)](https://minecraft.wiki/w/Bogged "Bogged")[Bogged](https://minecraft.wiki/w/Bogged "Bogged")
      * [![](/images/EntitySprite_parched.png?e7709)](https://minecraft.wiki/w/Parched "Parched")[Parched](https://minecraft.wiki/w/Parched "Parched")
      * [![](/images/EntitySprite_skeleton.png?ff904)](https://minecraft.wiki/w/Skeleton "Skeleton")[Skeleton](https://minecraft.wiki/w/Skeleton "Skeleton")
      * [![](/images/EntitySprite_stray.png?f338b)](https://minecraft.wiki/w/Stray "Stray")[Stray](https://minecraft.wiki/w/Stray "Stray")
      * [![](/images/EntitySprite_wither-skeleton.png?8b1cd)](https://minecraft.wiki/w/Wither_Skeleton "Wither Skeleton")[Wither Skeleton](https://minecraft.wiki/w/Wither_Skeleton "Wither Skeleton")
    - [![](/images/EntitySprite_guardian.png?da544)](https://minecraft.wiki/w/Guardian "Guardian")[Guardian](https://minecraft.wiki/w/Guardian "Guardian")
      * [![](/images/EntitySprite_elder-guardian.png?17494)](https://minecraft.wiki/w/Elder_Guardian "Elder Guardian")[Elder Guardian](https://minecraft.wiki/w/Elder_Guardian "Elder Guardian")
    - Patrolling Monster
      * Raider
        + [![](/images/EntitySprite_ravager.png?40196)](https://minecraft.wiki/w/Ravager "Ravager")[Ravager](https://minecraft.wiki/w/Ravager "Ravager")
        + [![](/images/EntitySprite_witch.png?3daa8)](https://minecraft.wiki/w/Witch "Witch")[Witch](https://minecraft.wiki/w/Witch "Witch")
        + Abstract Illager
          - [![](/images/EntitySprite_evoker.png?f236e)](https://minecraft.wiki/w/Pillager "Pillager")[Pillager](https://minecraft.wiki/w/Pillager "Pillager")
          - [![](/images/EntitySprite_johnny.png?6d568)](https://minecraft.wiki/w/Vindicator "Vindicator")[Vindicator](https://minecraft.wiki/w/Vindicator "Vindicator")
          - Spellcaster Illager
            * [![](/images/EntitySprite_evoker.png?f236e)](https://minecraft.wiki/w/Evoker "Evoker")[Evoker](https://minecraft.wiki/w/Evoker "Evoker")
            * [![](/images/EntitySprite_illusioner.png?e50b9)](https://minecraft.wiki/w/Illusioner "Illusioner")[Illusioner](https://minecraft.wiki/w/Illusioner "Illusioner")
    - [![](/images/EntitySprite_spider.png?4ee43)](https://minecraft.wiki/w/Spider "Spider")[Spider](https://minecraft.wiki/w/Spider "Spider")
      * [![](/images/EntitySprite_cave-spider.png?3e94c)](https://minecraft.wiki/w/Cave_Spider "Cave Spider")[Cave Spider](https://minecraft.wiki/w/Cave_Spider "Cave Spider")
    - [![](/images/EntitySprite_zombie.png?ce11f)](https://minecraft.wiki/w/Zombie "Zombie")[Zombie](https://minecraft.wiki/w/Zombie "Zombie")
      * [![](/images/EntitySprite_drowned.png?ef369)](https://minecraft.wiki/w/Drowned "Drowned")[Drowned](https://minecraft.wiki/w/Drowned "Drowned")
      * [![](/images/EntitySprite_husk.png?99086)](https://minecraft.wiki/w/Husk "Husk")[Husk](https://minecraft.wiki/w/Husk "Husk")
      * [![](/images/EntitySprite_zombie-villager.png?8183e)](https://minecraft.wiki/w/Zombie_Villager "Zombie Villager")[Zombie Villager](https://minecraft.wiki/w/Zombie_Villager "Zombie Villager")
      * [![](/images/EntitySprite_zombified-piglin.png?8dfea)](https://minecraft.wiki/w/Zombified_Piglin "Zombified Piglin")[Zombified Piglin](https://minecraft.wiki/w/Zombified_Piglin "Zombified Piglin")
  + Water Animal
    - [![](/images/EntitySprite_dolphin.png?1910f)](https://minecraft.wiki/w/Dolphin "Dolphin")[Dolphin](https://minecraft.wiki/w/Dolphin "Dolphin")
    - Abstract Fish
      * [![](/images/EntitySprite_pufferfish.png?08be3)](https://minecraft.wiki/w/Pufferfish "Pufferfish")[Pufferfish](https://minecraft.wiki/w/Pufferfish "Pufferfish")
      * [![](/images/EntitySprite_tadpole.png?532f2)](https://minecraft.wiki/w/Tadpole "Tadpole")[Tadpole](https://minecraft.wiki/w/Tadpole "Tadpole")
      * Abstract Schooling Fish
        + [![](/images/EntitySprite_cod.png?dc4af)](https://minecraft.wiki/w/Cod "Cod")[Cod](https://minecraft.wiki/w/Cod "Cod")
        + [![](/images/EntitySprite_salmon.png?d308d)](https://minecraft.wiki/w/Salmon "Salmon")[Salmon](https://minecraft.wiki/w/Salmon "Salmon")
        + [![](/images/EntitySprite_tropical-fish.png?ee953)](https://minecraft.wiki/w/Tropical_Fish "Tropical Fish")[Tropical Fish](https://minecraft.wiki/w/Tropical_Fish "Tropical Fish")
    - [![](/images/EntitySprite_squid.png?b1318)](https://minecraft.wiki/w/Squid "Squid")[Squid](https://minecraft.wiki/w/Squid "Squid")
      * [![](/images/EntitySprite_glow-squid.png?4b4d8)](https://minecraft.wiki/w/Glow_Squid "Glow Squid")[Glow Squid](https://minecraft.wiki/w/Glow_Squid "Glow Squid")
* [![](/images/EntitySprite_slime.png?1c782)](https://minecraft.wiki/w/Slime "Slime")[Slime](https://minecraft.wiki/w/Slime "Slime")
  + [![](/images/EntitySprite_magma-cube.png?0a89c)](https://minecraft.wiki/w/Magma_Cube "Magma Cube")[Magma Cube](https://minecraft.wiki/w/Magma_Cube "Magma Cube")

* [![](/images/ItemSprite_firework-rocket.png?9f724)](https://minecraft.wiki/w/Firework_Rocket "Firework Rocket")[Firework Rocket Entity](https://minecraft.wiki/w/Firework_Rocket "Firework Rocket")
* [![](/images/EntitySprite_fishing-bobber.png?26df9)](https://minecraft.wiki/w/Fishing_Bobber "Fishing Bobber")[Fishing Hook](https://minecraft.wiki/w/Fishing_Bobber "Fishing Bobber")
* [![](/images/EntitySprite_llama-spit.png?10b82)](https://minecraft.wiki/w/Llama_Spit "Llama Spit")[Llama Spit](https://minecraft.wiki/w/Llama_Spit "Llama Spit")
* [![](/images/EntitySprite_shulker-bullet.png?1b532)](https://minecraft.wiki/w/Shulker_Bullet "Shulker Bullet")[Shulker Bullet](https://minecraft.wiki/w/Shulker_Bullet "Shulker Bullet")
* Abstract Arrow
  + [![](/images/EntitySprite_arrow.png?123f9)](https://minecraft.wiki/w/Arrow "Arrow")[Arrow](https://minecraft.wiki/w/Arrow "Arrow")
  + [![](/images/EntitySprite_spectral-arrow.png?fcc49)](https://minecraft.wiki/w/Spectral_Arrow "Spectral Arrow")[Spectral Arrow](https://minecraft.wiki/w/Spectral_Arrow "Spectral Arrow")
  + [![](/images/EntitySprite_trident.png?b634b)](https://minecraft.wiki/w/Trident "Trident")[Thrown Trident](https://minecraft.wiki/w/Trident "Trident")
* Abstract Hurting Projectile
  + [![](/images/EntitySprite_dragon-fireball.png?24df0)](https://minecraft.wiki/w/Dragon_Fireball "Dragon Fireball")[Dragon Fireball](https://minecraft.wiki/w/Dragon_Fireball "Dragon Fireball")
  + [![](/images/EntitySprite_wither-skull.png?0be34)](https://minecraft.wiki/w/Wither#Wither_Skull "Wither")[Wither Skull Entity](https://minecraft.wiki/w/Wither#Wither_Skull "Wither")
  + Abstract Wind Charge
    - [![](/images/EntitySprite_wind-charge.png?cd158)](https://minecraft.wiki/w/Breeze_Wind_Charge "Breeze Wind Charge")[Breeze Wind Charge](https://minecraft.wiki/w/Breeze_Wind_Charge "Breeze Wind Charge")
    - [![](/images/EntitySprite_wind-charge.png?cd158)](https://minecraft.wiki/w/Wind_Charge "Wind Charge")[Wind Charge](https://minecraft.wiki/w/Wind_Charge "Wind Charge")
  + [Fireball](https://minecraft.wiki/w/Fireball "Fireball")
    - [![](/images/EntitySprite_fireball.png?ffb0c)](https://minecraft.wiki/w/Fireball "Fireball")[Large Fireball](https://minecraft.wiki/w/Fireball "Fireball")
    - [![](/images/EntitySprite_fireball.png?ffb0c)](https://minecraft.wiki/w/Small_Fireball "Small Fireball")[Small Fireball](https://minecraft.wiki/w/Small_Fireball "Small Fireball")
* Throwable Projectile
  + Throwable Item Projectile
    - [![](/images/ItemSprite_snowball.png?f4d05)](https://minecraft.wiki/w/Snowball "Snowball")[Thrown Snowball](https://minecraft.wiki/w/Snowball "Snowball")
    - [![](/images/ItemSprite_egg.png?2d314)](https://minecraft.wiki/w/Egg "Egg")[Thrown Egg](https://minecraft.wiki/w/Egg "Egg")
    - [![](/images/ItemSprite_ender-pearl.png?af209)](https://minecraft.wiki/w/Ender_Pearl "Ender Pearl")[Thrown Ender Pearl](https://minecraft.wiki/w/Ender_Pearl "Ender Pearl")
    - [![](/images/ItemSprite_eye-of-ender.png?9614f)](https://minecraft.wiki/w/Eye_of_Ender "Eye of Ender")[Thrown Eye of Ender](https://minecraft.wiki/w/Eye_of_Ender "Eye of Ender")
    - [![](/images/ItemSprite_bottle-o%27-enchanting.png?e5746)](https://minecraft.wiki/w/Bottle_o%27_Enchanting "Bottle o' Enchanting")[Thrown Experience Bottle](https://minecraft.wiki/w/Bottle_o%27_Enchanting "Bottle o' Enchanting")
    - [![](/images/ItemSprite_splash-water-bottle.png?24203)](https://minecraft.wiki/w/Splash_Potion "Splash Potion")[Thrown Potion](https://minecraft.wiki/w/Splash_Potion "Splash Potion")

### Interfaces


* Bucketable

  + [![](/images/EntitySprite_axolotl.png?0b5f0)](https://minecraft.wiki/w/Axolotl "Axolotl")[Axolotl](https://minecraft.wiki/w/Axolotl "Axolotl")
  + Abstract Fish
    - [![](/images/EntitySprite_pufferfish.png?08be3)](https://minecraft.wiki/w/Pufferfish "Pufferfish")[Pufferfish](https://minecraft.wiki/w/Pufferfish "Pufferfish")
    - [![](/images/EntitySprite_tadpole.png?532f2)](https://minecraft.wiki/w/Tadpole "Tadpole")[Tadpole](https://minecraft.wiki/w/Tadpole "Tadpole")
    - Abstract Schooling Fish
      * [![](/images/EntitySprite_cod.png?dc4af)](https://minecraft.wiki/w/Cod "Cod")[Cod](https://minecraft.wiki/w/Cod "Cod")
      * [![](/images/EntitySprite_salmon.png?d308d)](https://minecraft.wiki/w/Salmon "Salmon")[Salmon](https://minecraft.wiki/w/Salmon "Salmon")
      * [![](/images/EntitySprite_tropical-fish.png?ee953)](https://minecraft.wiki/w/Tropical_Fish "Tropical Fish")[Tropical Fish](https://minecraft.wiki/w/Tropical_Fish "Tropical Fish")
* Container User

  + [![](/images/EntitySprite_copper-golem.png?e837d)](https://minecraft.wiki/w/Copper_Golem "Copper Golem")[Copper Golem](https://minecraft.wiki/w/Copper_Golem "Copper Golem")
* Enemy

  + [![](/images/EntitySprite_ender-dragon.png?4a397)](https://minecraft.wiki/w/Ender_Dragon "Ender Dragon")[Ender Dragon](https://minecraft.wiki/w/Ender_Dragon "Ender Dragon")
  + [![](/images/EntitySprite_ghast.png?f81fc)](https://minecraft.wiki/w/Ghast "Ghast")[Ghast](https://minecraft.wiki/w/Ghast "Ghast")
  + [![](/images/EntitySprite_phantom.png?332bd)](https://minecraft.wiki/w/Phantom "Phantom")[Phantom](https://minecraft.wiki/w/Phantom "Phantom")
  + [![](/images/EntitySprite_shulker.png?ca1f9)](https://minecraft.wiki/w/Shulker "Shulker")[Shulker](https://minecraft.wiki/w/Shulker "Shulker")
  + [![](/images/EntitySprite_hoglin.png?06402)](https://minecraft.wiki/w/Hoglin "Hoglin")[Hoglin](https://minecraft.wiki/w/Hoglin "Hoglin")
  + [Monster](https://minecraft.wiki/w/Monster "Monster")

    - [![](/images/EntitySprite_blaze.png?43a55)](https://minecraft.wiki/w/Blaze "Blaze")[Blaze](https://minecraft.wiki/w/Blaze "Blaze")
    - [![](/images/EntitySprite_breeze.png?cd2af)](https://minecraft.wiki/w/Breeze "Breeze")[Breeze](https://minecraft.wiki/w/Breeze "Breeze")
    - [![](/images/EntitySprite_creaking.png?6b7fb)](https://minecraft.wiki/w/Creaking "Creaking")[Creaking](https://minecraft.wiki/w/Creaking "Creaking")
    - [![](/images/EntitySprite_creeper.png?703e9)](https://minecraft.wiki/w/Creeper "Creeper")[Creeper](https://minecraft.wiki/w/Creeper "Creeper")
    - [![](/images/EntitySprite_enderman.png?c703a)](https://minecraft.wiki/w/Enderman "Enderman")[Enderman](https://minecraft.wiki/w/Enderman "Enderman")
    - [![](/images/EntitySprite_endermite.png?71743)](https://minecraft.wiki/w/Endermite "Endermite")[Endermite](https://minecraft.wiki/w/Endermite "Endermite")
    - [![](/images/EntitySprite_zombie.png?ce11f)](https://minecraft.wiki/w/Giant "Giant")[Giant](https://minecraft.wiki/w/Giant "Giant")
    - [![](/images/EntitySprite_silverfish.png?0656c)](https://minecraft.wiki/w/Silverfish "Silverfish")[Silverfish](https://minecraft.wiki/w/Silverfish "Silverfish")
    - [![](/images/EntitySprite_vex.png?646cb)](https://minecraft.wiki/w/Vex "Vex")[Vex](https://minecraft.wiki/w/Vex "Vex")
    - [![](/images/EntitySprite_warden.png?d9d2f)](https://minecraft.wiki/w/Warden "Warden")[Warden](https://minecraft.wiki/w/Warden "Warden")
    - [![](/images/EntitySprite_wither.png?fb756)](https://minecraft.wiki/w/Wither "Wither")[Wither](https://minecraft.wiki/w/Wither "Wither")
    - [![](/images/EntitySprite_zoglin.png?09afa)](https://minecraft.wiki/w/Zoglin "Zoglin")[Zoglin](https://minecraft.wiki/w/Zoglin "Zoglin")
    - Abstract Piglin
      * [![](/images/EntitySprite_piglin.png?5435e)](https://minecraft.wiki/w/Piglin "Piglin")[Piglin](https://minecraft.wiki/w/Piglin "Piglin")
      * [![](/images/EntitySprite_piglin-brute.png?56ccd)](https://minecraft.wiki/w/Piglin_Brute "Piglin Brute")[Piglin Brute](https://minecraft.wiki/w/Piglin_Brute "Piglin Brute")
    - Abstract Skeleton
      * [![](/images/EntitySprite_bogged.png?2cf56)](https://minecraft.wiki/w/Bogged "Bogged")[Bogged](https://minecraft.wiki/w/Bogged "Bogged")
      * [![](/images/EntitySprite_parched.png?e7709)](https://minecraft.wiki/w/Parched "Parched")[Parched](https://minecraft.wiki/w/Parched "Parched")
      * [![](/images/EntitySprite_skeleton.png?ff904)](https://minecraft.wiki/w/Skeleton "Skeleton")[Skeleton](https://minecraft.wiki/w/Skeleton "Skeleton")
      * [![](/images/EntitySprite_stray.png?f338b)](https://minecraft.wiki/w/Stray "Stray")[Stray](https://minecraft.wiki/w/Stray "Stray")
      * [![](/images/EntitySprite_wither-skeleton.png?8b1cd)](https://minecraft.wiki/w/Wither_Skeleton "Wither Skeleton")[Wither Skeleton](https://minecraft.wiki/w/Wither_Skeleton "Wither Skeleton")
    - [![](/images/EntitySprite_guardian.png?da544)](https://minecraft.wiki/w/Guardian "Guardian")[Guardian](https://minecraft.wiki/w/Guardian "Guardian")
      * [![](/images/EntitySprite_elder-guardian.png?17494)](https://minecraft.wiki/w/Elder_Guardian "Elder Guardian")[Elder Guardian](https://minecraft.wiki/w/Elder_Guardian "Elder Guardian")
    - Patrolling Monster
      * Raider
        + [![](/images/EntitySprite_ravager.png?40196)](https://minecraft.wiki/w/Ravager "Ravager")[Ravager](https://minecraft.wiki/w/Ravager "Ravager")
        + [![](/images/EntitySprite_witch.png?3daa8)](https://minecraft.wiki/w/Witch "Witch")[Witch](https://minecraft.wiki/w/Witch "Witch")
        + Abstract [Illager](https://minecraft.wiki/w/Illager "Illager")
          - [![](/images/EntitySprite_evoker.png?f236e)](https://minecraft.wiki/w/Pillager "Pillager")[Pillager](https://minecraft.wiki/w/Pillager "Pillager")
          - [![](/images/EntitySprite_johnny.png?6d568)](https://minecraft.wiki/w/Vindicator "Vindicator")[Vindicator](https://minecraft.wiki/w/Vindicator "Vindicator")
          - Spellcaster Illager
            * [![](/images/EntitySprite_evoker.png?f236e)](https://minecraft.wiki/w/Evoker "Evoker")[Evoker](https://minecraft.wiki/w/Evoker "Evoker")
            * [![](/images/EntitySprite_illusioner.png?e50b9)](https://minecraft.wiki/w/Illusioner "Illusioner")[Illusioner](https://minecraft.wiki/w/Illusioner "Illusioner")
    - [![](/images/EntitySprite_spider.png?4ee43)](https://minecraft.wiki/w/Spider "Spider")[Spider](https://minecraft.wiki/w/Spider "Spider")
      * [![](/images/EntitySprite_cave-spider.png?3e94c)](https://minecraft.wiki/w/Cave_Spider "Cave Spider")[Cave Spider](https://minecraft.wiki/w/Cave_Spider "Cave Spider")
    - [![](/images/EntitySprite_zombie.png?ce11f)](https://minecraft.wiki/w/Zombie "Zombie")[Zombie](https://minecraft.wiki/w/Zombie "Zombie")
      * [![](/images/EntitySprite_drowned.png?ef369)](https://minecraft.wiki/w/Drowned "Drowned")[Drowned](https://minecraft.wiki/w/Drowned "Drowned")
      * [![](/images/EntitySprite_husk.png?99086)](https://minecraft.wiki/w/Husk "Husk")[Husk](https://minecraft.wiki/w/Husk "Husk")
      * [![](/images/EntitySprite_zombie-villager.png?8183e)](https://minecraft.wiki/w/Zombie_Villager "Zombie Villager")[Zombie Villager](https://minecraft.wiki/w/Zombie_Villager "Zombie Villager")
      * [![](/images/EntitySprite_zombified-piglin.png?8dfea)](https://minecraft.wiki/w/Zombified_Piglin "Zombified Piglin")[Zombified Piglin](https://minecraft.wiki/w/Zombified_Piglin "Zombified Piglin")
  + [![](/images/EntitySprite_slime.png?1c782)](https://minecraft.wiki/w/Slime "Slime")[Slime](https://minecraft.wiki/w/Slime "Slime")
    - [![](/images/EntitySprite_magma-cube.png?0a89c)](https://minecraft.wiki/w/Magma_Cube "Magma Cube")[Magma Cube](https://minecraft.wiki/w/Magma_Cube "Magma Cube")
* Flying Animal

  + [![](/images/EntitySprite_bee.png?5d625)](https://minecraft.wiki/w/Bee "Bee")[Bee](https://minecraft.wiki/w/Bee "Bee")
  + [![](/images/EntitySprite_parrot.png?8ab80)](https://minecraft.wiki/w/Parrot "Parrot")[Parrot](https://minecraft.wiki/w/Parrot "Parrot")
* Has Custom Inventory Screen

  + [![](/images/EntitySprite_all-boats-with-chests.png?6b19e)](https://minecraft.wiki/w/Boat_with_Chest "Boat with Chest")[Chest Boat](https://minecraft.wiki/w/Boat_with_Chest "Boat with Chest")
  + Abstract Horse

    - [![](/images/EntitySprite_camel.png?73196)](https://minecraft.wiki/w/Camel "Camel")[Camel](https://minecraft.wiki/w/Camel "Camel")
      * [![](/images/EntitySprite_camel-husk.png?304cb)](https://minecraft.wiki/w/Camel_Husk "Camel Husk")[Camel Husk](https://minecraft.wiki/w/Camel_Husk "Camel Husk")
    - [![](/images/EntitySprite_creamy-horse.png?3d52b)](https://minecraft.wiki/w/Horse "Horse")[Horse](https://minecraft.wiki/w/Horse "Horse")
    - [![](/images/EntitySprite_skeleton-horse.png?3cde9)](https://minecraft.wiki/w/Skeleton_Horse "Skeleton Horse")[Skeleton Horse](https://minecraft.wiki/w/Skeleton_Horse "Skeleton Horse")
    - [![](/images/EntitySprite_zombie-horse.png?f1a1f)](https://minecraft.wiki/w/Zombie_Horse "Zombie Horse")[Zombie Horse](https://minecraft.wiki/w/Zombie_Horse "Zombie Horse")
    - Abstract Chested Horse
      * [![](/images/EntitySprite_donkey.png?1910f)](https://minecraft.wiki/w/Donkey "Donkey")[Donkey](https://minecraft.wiki/w/Donkey "Donkey")
      * [![](/images/EntitySprite_mule.png?a1576)](https://minecraft.wiki/w/Mule "Mule")[Mule](https://minecraft.wiki/w/Mule "Mule")
      * [![](/images/EntitySprite_creamy-llama.png?0657f)](https://minecraft.wiki/w/Llama "Llama")[Llama](https://minecraft.wiki/w/Llama "Llama")
        + [![](/images/EntitySprite_creamy-trader-llama.png?6d474)](https://minecraft.wiki/w/Trader_Llama "Trader Llama")[Trader Llama](https://minecraft.wiki/w/Trader_Llama "Trader Llama")
* Inventory Carrier

  + [![](/images/EntitySprite_allay.png?a939b)](https://minecraft.wiki/w/Allay "Allay")[Allay](https://minecraft.wiki/w/Allay "Allay")
  + [![](/images/EntitySprite_piglin.png?5435e)](https://minecraft.wiki/w/Piglin "Piglin")[Piglin](https://minecraft.wiki/w/Piglin "Piglin")
  + [![](/images/EntitySprite_evoker.png?f236e)](https://minecraft.wiki/w/Pillager "Pillager")[Pillager](https://minecraft.wiki/w/Pillager "Pillager")
  + Abstract Villager
    - [![](/images/EntitySprite_villager.png?05433)](https://minecraft.wiki/w/Villager "Villager")[Villager](https://minecraft.wiki/w/Villager "Villager")
    - [![](/images/EntitySprite_wandering-trader.png?0f9fa)](https://minecraft.wiki/w/Wandering_Trader "Wandering Trader")[Wandering Trader](https://minecraft.wiki/w/Wandering_Trader "Wandering Trader")
* Item Steerable

  + [![](/images/EntitySprite_pig.png?5435e)](https://minecraft.wiki/w/Pig "Pig")[Pig](https://minecraft.wiki/w/Pig "Pig")
  + [![](/images/EntitySprite_strider.png?c3ab9)](https://minecraft.wiki/w/Strider "Strider")[Strider](https://minecraft.wiki/w/Strider "Strider")
* Item Supplier

  + [![](/images/EntitySprite_eye-of-ender.png?57d43)](https://minecraft.wiki/w/Eye_of_Ender "Eye of Ender")[Eye of Ender](https://minecraft.wiki/w/Eye_of_Ender "Eye of Ender")
  + [![](/images/ItemSprite_firework-rocket.png?9f724)](https://minecraft.wiki/w/Firework_Rocket "Firework Rocket")[Firework Rocket Entity](https://minecraft.wiki/w/Firework_Rocket "Firework Rocket")
  + Abstract Wind Charge
    - [![](/images/EntitySprite_wind-charge.png?cd158)](https://minecraft.wiki/w/Breeze_Wind_Charge "Breeze Wind Charge")[Breeze Wind Charge](https://minecraft.wiki/w/Breeze_Wind_Charge "Breeze Wind Charge")
    - [![](/images/EntitySprite_wind-charge.png?cd158)](https://minecraft.wiki/w/Wind_Charge "Wind Charge")[Wind Charge](https://minecraft.wiki/w/Wind_Charge "Wind Charge")
  + [Fireball](https://minecraft.wiki/w/Fireball "Fireball")
    - [![](/images/EntitySprite_fireball.png?ffb0c)](https://minecraft.wiki/w/Fireball "Fireball")[Large Fireball](https://minecraft.wiki/w/Fireball "Fireball")
    - [![](/images/EntitySprite_fireball.png?ffb0c)](https://minecraft.wiki/w/Small_Fireball "Small Fireball")[Small Fireball](https://minecraft.wiki/w/Small_Fireball "Small Fireball")
  + Throwable Item Projectile

    - [![](/images/ItemSprite_snowball.png?f4d05)](https://minecraft.wiki/w/Snowball "Snowball")[Snowball](https://minecraft.wiki/w/Snowball "Snowball")
    - [![](/images/ItemSprite_egg.png?2d314)](https://minecraft.wiki/w/Egg "Egg")[Thrown Egg](https://minecraft.wiki/w/Egg "Egg")
    - [![](/images/ItemSprite_ender-pearl.png?af209)](https://minecraft.wiki/w/Ender_Pearl "Ender Pearl")[Thrown Ender Pearl](https://minecraft.wiki/w/Ender_Pearl "Ender Pearl")
    - [![](/images/ItemSprite_eye-of-ender.png?9614f)](https://minecraft.wiki/w/Eye_of_Ender "Eye of Ender")[Thrown Eye of Ender](https://minecraft.wiki/w/Eye_of_Ender "Eye of Ender")
    - [![](/images/ItemSprite_bottle-o%27-enchanting.png?e5746)](https://minecraft.wiki/w/Bottle_o%27_Enchanting "Bottle o' Enchanting")[Thrown Experience Bottle](https://minecraft.wiki/w/Bottle_o%27_Enchanting "Bottle o' Enchanting")
    - [![](/images/ItemSprite_splash-water-bottle.png?24203)](https://minecraft.wiki/w/Splash_Potion "Splash Potion")[Thrown Potion](https://minecraft.wiki/w/Splash_Potion "Splash Potion")
* Neutral Mob

  + [![](/images/EntitySprite_bee.png?5d625)](https://minecraft.wiki/w/Bee "Bee")[Bee](https://minecraft.wiki/w/Bee "Bee")
  + [![](/images/EntitySprite_enderman.png?c703a)](https://minecraft.wiki/w/Enderman "Enderman")[Enderman](https://minecraft.wiki/w/Enderman "Enderman")
  + [![](/images/EntitySprite_iron-golem.png?bb037)](https://minecraft.wiki/w/Iron_Golem "Iron Golem")[Iron Golem](https://minecraft.wiki/w/Iron_Golem "Iron Golem")
  + [![](/images/EntitySprite_polar-bear.png?41cea)](https://minecraft.wiki/w/Polar_Bear "Polar Bear")[Polar Bear](https://minecraft.wiki/w/Polar_Bear "Polar Bear")
  + [![](/images/EntitySprite_wolf.png?77c1e)](https://minecraft.wiki/w/Wolf "Wolf")[Wolf](https://minecraft.wiki/w/Wolf "Wolf")
  + [![](/images/EntitySprite_zombified-piglin.png?8dfea)](https://minecraft.wiki/w/Zombified_Piglin "Zombified Piglin")[Zombified Piglin](https://minecraft.wiki/w/Zombified_Piglin "Zombified Piglin")
* Ownable Entity

  + Tamable Animal
    - [![](/images/EntitySprite_cat.png?b3c67)](https://minecraft.wiki/w/Cat "Cat")[Cat](https://minecraft.wiki/w/Cat "Cat")
    - [![](/images/EntitySprite_wolf.png?77c1e)](https://minecraft.wiki/w/Wolf "Wolf")[Wolf](https://minecraft.wiki/w/Wolf "Wolf")
    - Shoulder Riding Entity
      * [![](/images/EntitySprite_parrot.png?8ab80)](https://minecraft.wiki/w/Parrot "Parrot")[Parrot](https://minecraft.wiki/w/Parrot "Parrot")
* Player Rideable

  + Player Rideable Jumping
    - Abstract Horse
      * [![](/images/EntitySprite_camel.png?73196)](https://minecraft.wiki/w/Camel "Camel")[Camel](https://minecraft.wiki/w/Camel "Camel")
        + [![](/images/EntitySprite_camel-husk.png?304cb)](https://minecraft.wiki/w/Camel_Husk "Camel Husk")[Camel Husk](https://minecraft.wiki/w/Camel_Husk "Camel Husk")
      * [![](/images/EntitySprite_creamy-horse.png?3d52b)](https://minecraft.wiki/w/Horse "Horse")[Horse](https://minecraft.wiki/w/Horse "Horse")
      * [![](/images/EntitySprite_skeleton-horse.png?3cde9)](https://minecraft.wiki/w/Skeleton_Horse "Skeleton Horse")[Skeleton Horse](https://minecraft.wiki/w/Skeleton_Horse "Skeleton Horse")
      * [![](/images/EntitySprite_zombie-horse.png?f1a1f)](https://minecraft.wiki/w/Zombie_Horse "Zombie Horse")[Zombie Horse](https://minecraft.wiki/w/Zombie_Horse "Zombie Horse")
      * Abstract Chested Horse
        + [![](/images/EntitySprite_donkey.png?1910f)](https://minecraft.wiki/w/Donkey "Donkey")[Donkey](https://minecraft.wiki/w/Donkey "Donkey")
        + [![](/images/EntitySprite_mule.png?a1576)](https://minecraft.wiki/w/Mule "Mule")[Mule](https://minecraft.wiki/w/Mule "Mule")
        + [![](/images/EntitySprite_creamy-llama.png?0657f)](https://minecraft.wiki/w/Llama "Llama")[Llama](https://minecraft.wiki/w/Llama "Llama")
          - [![](/images/EntitySprite_creamy-trader-llama.png?6d474)](https://minecraft.wiki/w/Trader_Llama "Trader Llama")[Trader Llama](https://minecraft.wiki/w/Trader_Llama "Trader Llama")
    - Abstract Nautilus
      * [![](/images/EntitySprite_nautilus.png?3bfe0)](https://minecraft.wiki/w/Nautilus "Nautilus")[Nautilus](https://minecraft.wiki/w/Nautilus "Nautilus")
      * [![](/images/EntitySprite_zombie-nautilus.png?56e70)](https://minecraft.wiki/w/Zombie_Nautilus "Zombie Nautilus")[Zombie Nautilus](https://minecraft.wiki/w/Zombie_Nautilus "Zombie Nautilus")
* Powerable Mob

  + [![](/images/EntitySprite_creeper.png?703e9)](https://minecraft.wiki/w/Creeper "Creeper")[Creeper](https://minecraft.wiki/w/Creeper "Creeper")
  + [![](/images/EntitySprite_wither.png?fb756)](https://minecraft.wiki/w/Wither "Wither")[Wither](https://minecraft.wiki/w/Wither "Wither")
* Ranged Attack Mob

  + [![](/images/EntitySprite_drowned.png?ef369)](https://minecraft.wiki/w/Drowned "Drowned")[Drowned](https://minecraft.wiki/w/Drowned "Drowned")
  + [![](/images/EntitySprite_illusioner.png?e50b9)](https://minecraft.wiki/w/Illusioner "Illusioner")[Illusioner](https://minecraft.wiki/w/Illusioner "Illusioner")
  + [![](/images/EntitySprite_pumpkin-snow-golem.png?e81b0)](https://minecraft.wiki/w/Snow_Golem "Snow Golem")[Snow Golem](https://minecraft.wiki/w/Snow_Golem "Snow Golem")
  + [![](/images/EntitySprite_witch.png?3daa8)](https://minecraft.wiki/w/Witch "Witch")[Witch](https://minecraft.wiki/w/Witch "Witch")
  + [![](/images/EntitySprite_wither.png?fb756)](https://minecraft.wiki/w/Wither "Wither")[Wither](https://minecraft.wiki/w/Wither "Wither")
  + Abstract Skeleton
    - [![](/images/EntitySprite_bogged.png?2cf56)](https://minecraft.wiki/w/Bogged "Bogged")[Bogged](https://minecraft.wiki/w/Bogged "Bogged")
    - [![](/images/EntitySprite_parched.png?e7709)](https://minecraft.wiki/w/Parched "Parched")[Parched](https://minecraft.wiki/w/Parched "Parched")
    - [![](/images/EntitySprite_skeleton.png?ff904)](https://minecraft.wiki/w/Skeleton "Skeleton")[Skeleton](https://minecraft.wiki/w/Skeleton "Skeleton")
    - [![](/images/EntitySprite_stray.png?f338b)](https://minecraft.wiki/w/Stray "Stray")[Stray](https://minecraft.wiki/w/Stray "Stray")
    - [![](/images/EntitySprite_wither-skeleton.png?8b1cd)](https://minecraft.wiki/w/Wither_Skeleton "Wither Skeleton")[Wither Skeleton](https://minecraft.wiki/w/Wither_Skeleton "Wither Skeleton")
  + Crossbow Attack Mob
    - [![](/images/EntitySprite_piglin.png?5435e)](https://minecraft.wiki/w/Piglin "Piglin")[Piglin](https://minecraft.wiki/w/Piglin "Piglin")
    - [![](/images/EntitySprite_evoker.png?f236e)](https://minecraft.wiki/w/Pillager "Pillager")[Pillager](https://minecraft.wiki/w/Pillager "Pillager")
  + [![](/images/EntitySprite_creamy-llama.png?0657f)](https://minecraft.wiki/w/Llama "Llama")[Llama](https://minecraft.wiki/w/Llama "Llama")
    - [![](/images/EntitySprite_creamy-trader-llama.png?6d474)](https://minecraft.wiki/w/Trader_Llama "Trader Llama")[Trader Llama](https://minecraft.wiki/w/Trader_Llama "Trader Llama")
* Saddleable

  + [![](/images/EntitySprite_pig.png?5435e)](https://minecraft.wiki/w/Pig "Pig")[Pig](https://minecraft.wiki/w/Pig "Pig")
  + [![](/images/EntitySprite_strider.png?c3ab9)](https://minecraft.wiki/w/Strider "Strider")[Strider](https://minecraft.wiki/w/Strider "Strider")
  + Abstract Horse

    - [![](/images/EntitySprite_camel.png?73196)](https://minecraft.wiki/w/Camel "Camel")[Camel](https://minecraft.wiki/w/Camel "Camel")
      * [![](/images/EntitySprite_camel-husk.png?304cb)](https://minecraft.wiki/w/Camel_Husk "Camel Husk")[Camel Husk](https://minecraft.wiki/w/Camel_Husk "Camel Husk")
    - [![](/images/EntitySprite_creamy-horse.png?3d52b)](https://minecraft.wiki/w/Horse "Horse")[Horse](https://minecraft.wiki/w/Horse "Horse")
    - [![](/images/EntitySprite_skeleton-horse.png?3cde9)](https://minecraft.wiki/w/Skeleton_Horse "Skeleton Horse")[Skeleton Horse](https://minecraft.wiki/w/Skeleton_Horse "Skeleton Horse")
    - [![](/images/EntitySprite_zombie-horse.png?f1a1f)](https://minecraft.wiki/w/Zombie_Horse "Zombie Horse")[Zombie Horse](https://minecraft.wiki/w/Zombie_Horse "Zombie Horse")
    - Abstract Chested Horse
      * [![](/images/EntitySprite_donkey.png?1910f)](https://minecraft.wiki/w/Donkey "Donkey")[Donkey](https://minecraft.wiki/w/Donkey "Donkey")
      * [![](/images/EntitySprite_mule.png?a1576)](https://minecraft.wiki/w/Mule "Mule")[Mule](https://minecraft.wiki/w/Mule "Mule")
      * [![](/images/EntitySprite_creamy-llama.png?0657f)](https://minecraft.wiki/w/Llama "Llama")[Llama](https://minecraft.wiki/w/Llama "Llama")
        + [![](/images/EntitySprite_creamy-trader-llama.png?6d474)](https://minecraft.wiki/w/Trader_Llama "Trader Llama")[Trader Llama](https://minecraft.wiki/w/Trader_Llama "Trader Llama")
* Shearable

  + [![](/images/EntitySprite_copper-golem.png?e837d)](https://minecraft.wiki/w/Copper_Golem "Copper Golem")[Copper Golem](https://minecraft.wiki/w/Copper_Golem "Copper Golem")
  + [![](/images/EntitySprite_mooshroom.png?92493)](https://minecraft.wiki/w/Mooshroom "Mooshroom")[Mooshroom](https://minecraft.wiki/w/Mooshroom "Mooshroom")
  + [![](/images/EntitySprite_sheep.png?bd14e)](https://minecraft.wiki/w/Sheep "Sheep")[Sheep](https://minecraft.wiki/w/Sheep "Sheep")
  + [![](/images/EntitySprite_pumpkin-snow-golem.png?e81b0)](https://minecraft.wiki/w/Snow_Golem "Snow Golem")[Snow Golem](https://minecraft.wiki/w/Snow_Golem "Snow Golem")
* Variant Holder

  + [![](/images/EntitySprite_axolotl.png?0b5f0)](https://minecraft.wiki/w/Axolotl "Axolotl")[Axolotl](https://minecraft.wiki/w/Axolotl "Axolotl")
  + [![](/images/EntitySprite_cat.png?b3c67)](https://minecraft.wiki/w/Cat "Cat")[Cat](https://minecraft.wiki/w/Cat "Cat")
  + [![](/images/EntitySprite_fox.png?91c80)](https://minecraft.wiki/w/Fox "Fox")[Fox](https://minecraft.wiki/w/Fox "Fox")
  + [![](/images/EntitySprite_frog.png?15793)](https://minecraft.wiki/w/Frog "Frog")[Frog](https://minecraft.wiki/w/Frog "Frog")
  + [![](/images/EntitySprite_creamy-horse.png?3d52b)](https://minecraft.wiki/w/Horse "Horse")[Horse](https://minecraft.wiki/w/Horse "Horse")
  + [![](/images/EntitySprite_mooshroom.png?92493)](https://minecraft.wiki/w/Mooshroom "Mooshroom")[Mooshroom](https://minecraft.wiki/w/Mooshroom "Mooshroom")
  + [![](/images/EntitySprite_brown-rabbit.png?18569)](https://minecraft.wiki/w/Rabbit "Rabbit")[Rabbit](https://minecraft.wiki/w/Rabbit "Rabbit")
  + [![](/images/EntitySprite_shulker.png?ca1f9)](https://minecraft.wiki/w/Shulker "Shulker")[Shulker](https://minecraft.wiki/w/Shulker "Shulker")
  + [![](/images/EntitySprite_tropical-fish.png?ee953)](https://minecraft.wiki/w/Tropical_Fish "Tropical Fish")[Tropical Fish](https://minecraft.wiki/w/Tropical_Fish "Tropical Fish")
  + [![](/images/EntitySprite_creamy-llama.png?0657f)](https://minecraft.wiki/w/Llama "Llama")[Llama](https://minecraft.wiki/w/Llama "Llama")
    - [![](/images/EntitySprite_creamy-trader-llama.png?6d474)](https://minecraft.wiki/w/Trader_Llama "Trader Llama")[Trader Llama](https://minecraft.wiki/w/Trader_Llama "Trader Llama")
  + Villager Data Holder
    - [![](/images/EntitySprite_villager.png?05433)](https://minecraft.wiki/w/Villager "Villager")[Villager](https://minecraft.wiki/w/Villager "Villager")
    - [![](/images/EntitySprite_zombie-villager.png?8183e)](https://minecraft.wiki/w/Zombie_Villager "Zombie Villager")[Zombie Villager](https://minecraft.wiki/w/Zombie_Villager "Zombie Villager")
  + [![](/images/EntitySprite_zombie-nautilus.png?56e70)](https://minecraft.wiki/w/Zombie_Nautilus "Zombie Nautilus")[Zombie Nautilus](https://minecraft.wiki/w/Zombie_Nautilus "Zombie Nautilus")

## NBT structure


Every [entity](https://minecraft.wiki/w/Entity "Entity") is an unnamed [NBT Compound / JSON Object] compound contained in the Entities list of a chunk file. The sole exception is the Player entity, stored in [level.dat](https://minecraft.wiki/w/Java_Edition_level_format#level.dat_format "Java Edition level format"), or in [<player>.dat](https://minecraft.wiki/w/Player.dat_format "Player.dat format") files on servers.

* [NBT Compound / JSON Object] The root tag.
  + [Int] DataVersion: Version of the chunk data.
  + [Int Array] Position: Position of this chunk.
    - [Int]: X coordinate.
    - [Int]: Z coordinate.
  + [NBT List / JSON Array] Entities: All the entities. Each compound in this list defines an entity in this chunk.
    - [NBT Compound / JSON Object]: An entity. See [#Entity format](#Entity_format) below.

## Entity format


All entities are with the following structure:

* [NBT Compound / JSON Object] Entity data

* + [Short] Air: How much air the entity has, in game ticks. Decreases when unable to breathe (except suffocating in a block). Increases when it can breathe. [Short] Air being `<= -20` game ticks (while still unable to breathe) on a given game tick causes the entity to immediately lose 1 health to [drowning](https://minecraft.wiki/w/Drowning "Drowning") damage. This resets [Short] Air to 0 game ticks. Most mobs can have a maximum of 300 game ticks (15 seconds) of [Short] Air, while dolphins can reach up to 4800 game ticks (240 seconds), and axolotls have 6000 game ticks (300 seconds).
  + [NBT Compound / JSON Object][NBT List / JSON Array][String] CustomName: The custom name [text component](https://minecraft.wiki/w/Text_component "Text component") of this entity. Appears in player death messages and villager trading interfaces, as well as above the entity when the player's cursor is over it. May be empty or not exist. Represents the [`minecraft:custom_name`](https://minecraft.wiki/w/Data_component_format#custom_name "Data component format") component.
  + [Boolean] CustomNameVisible: `1` or `0` (`true`/`false`) - if `true`, and this entity has a custom name, the name always appears above the entity, regardless of where the cursor points. If the entity does not have a custom name, a default name is shown. May not exist.
  + [NBT Compound / JSON Object] data: Optional arbitrary NBT data. Is removed if empty. Represents the [`minecraft:custom_data`](https://minecraft.wiki/w/Data_component_format#custom_data "Data component format") component.
  + [Double] fall\_distance: Distance the entity has fallen. Larger values cause more damage when the entity lands.
  + [Short] Fire: Number of game ticks until the fire is put out. Negative values reflect how long the entity can stand in fire before burning. Default to -20 when not on fire.
  + [Boolean] Glowing: `1` or `0` (`true`/`false`) - if `true`, the entity has a glowing outline.
  + [Boolean] HasVisualFire: `1` or `0` (`true`/`false`) - if `true`, the entity visually appears on fire, even if it is not actually on fire.
  + [String] id: [Namespaced ID](https://minecraft.wiki/w/Resource_location#Conversion_to_string "Resource location") of the entity's [entity type](https://minecraft.wiki/w/Java_Edition_data_values#Entities "Java Edition data values"). Does not exist for entities in the world, only stored entities (such as in [data components](https://minecraft.wiki/w/Data_components "Data components")).
  + [Boolean] Invulnerable: `1` or `0` (`true`/`false`) - if `true`, the entity should not take damage. This applies to living and nonliving entities alike: mobs should not take damage from any source (including potion effects), and cannot be moved by fishing rods, attacks, explosions, or projectiles, and objects such as vehicles and item frames cannot be destroyed unless their supports are removed. Invulnerable player entities are also ignored by any hostile mobs. Note that these entities can be damaged by players in Creative mode.
  + [NBT List / JSON Array] Motion: List of 3 [Double] doubles describing the current `dX`, `dY`, and `dZ` velocity of the entity in meters per game tick. Only allows between 10.0 and -10.0 (inclusive), else resets to 0.
  + [Boolean] NoGravity: `1` or `0` (`true`/`false`) - if `true`, the entity does not fall down naturally. Does not exist if set to false. Set to `true` by striders in lava.
  + [Boolean] OnGround: `1` or `0` (`true`/`false`) - if `true`, the entity is touching the ground.
  + [NBT List / JSON Array] Passengers: The data of the entities that are riding this entity.
    - [NBT Compound / JSON Object]: The same as this format (recursive). Note that each passenger entity, and the ridden entity (the vehicle) have equal control of the movement of the ridden entity. The topmost entity controls spawning conditions when the vehicle entity is created by a mob spawner.

      * Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
      * Tags unique to this passenger entity.
  + [Int] PortalCooldown: The number of game ticks before which the entity may be teleported back through a nether portal. Initially starts at 300 game ticks (15 seconds) after teleportation and counts down to 0.
  + [NBT List / JSON Array] Pos: List of 3 [Double] doubles describing the current X, Y, and Z position ([coordinates](https://minecraft.wiki/w/Coordinates "Coordinates")) of the entity.
  + [NBT List / JSON Array] Rotation: List of 2 [Float] floats representing the entity's server-side rotation (facing direction). This does not necessarily match with the direction that the mob is looking in on the client's side. The yaw and pitch are stored inverted for most projectile entities.
    - [Float] 0: The entity's **yaw**. Yaw is rotation about the Y axis. It is measured in degrees and ranges from -180 to +180. The yaw increases as the entity turns clockwise (*right* from their perspective). A yaw of 0 means the entity is facing south. See table of specific values here: [Rotation (yaw)](https://minecraft.wiki/w/Chunk_format/Entity/Rotation_%28yaw%29 "Chunk format/Entity/Rotation (yaw)").
    - [Float] 1: The entity's **pitch**. Pitch is rotation about the local X axis after yaw is applied. It is measured in degrees and ranges from -90 to +90. A pitch of 0 means the entity is facing parallel to the ground or directly towards the horizon. The pitch increases as the entity looks downwards, so a pitch of 90 is facing directly down and a pitch of -90 facing directly up.
  + [Boolean] Silent: `1` or `0` (`true`/`false`) - if `true`, this entity is silenced. May not exist.
  + [NBT List / JSON Array] Tags: List of [scoreboard tags](https://minecraft.wiki/w/Scoreboard#Tags "Scoreboard") of this entity. It is not preserved if it is removed.
  + [Int] TicksFrozen: Optional. How many game ticks the entity has been [freezing](https://minecraft.wiki/w/Powder_Snow#Freezing "Powder Snow"). Although this tag is defined for all entities, it is actually only used by [mobs](https://minecraft.wiki/w/Mob "Mob") that are not in the `freeze_immune_entity_types` [entity type tag](https://minecraft.wiki/w/Entity_type_tag "Entity type tag"). Increases while in [powder snow](https://minecraft.wiki/w/Powder_snow "Powder snow"), even partially, up to a maximum of 300 game ticks (15 seconds), and decreases at double speed while not in powder snow.
  + [Int Array] UUID: This entity's [Universally Unique IDentifier](https://minecraft.wiki/w/Universally_Unique_IDentifier "Universally Unique IDentifier"). The 128-bit UUID is stored as four 32-bit integers ([Int] Ints), ordered from most to least significant.

### Mobs


Mobs are a subclass of Living Entity with additional tags to store their health, attacking/damaged state, potion effects, and more depending on the mob. [Players](https://minecraft.wiki/w/Player.dat_format#NBT_structure "Player.dat format") and [armor stands](https://minecraft.wiki/w/Armor_stand "Armor stand") are a subclass of living entities.

* [NBT Compound / JSON Object] Mob data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")

* + [Float] AbsorptionAmount: number of extra health added by Absorption effect.
  + [NBT List / JSON Array] active\_effects: The list of status effects on this mob. May not exist.
    - [NBT Compound / JSON Object] Each item is a [status effect](https://minecraft.wiki/w/Status_effect "Status effect")
      * [Boolean] ambient: `1` or `0` (`true`/`false`) - if `true`, this effect is provided by a Beacon and therefore should be less intrusive on screen.
      * [Byte] amplifier: The status effect level. `0` is level 1.
      * [Int] duration: The number of [game ticks](https://minecraft.wiki/w/Game_tick "Game tick") before the effect wears off. `-1` means infinite duration.
      * [NBT Compound / JSON Object] hidden\_effect: Lower amplifier effect of the same type, this replaces the above effect when it expires. (The duration of the effect still decreases in here too)
      * [String] id: The [effect name](https://minecraft.wiki/w/Status_effect#Effect_list "Status effect").
      * [Boolean] show\_icon: `1` or `0` (`true`/`false`) - if `true`, effect icon is shown; if `false`, no icon is shown.
      * [Boolean] show\_particles: `1` or `0` (`true`/`false`) - if `true`, particles are shown (affected by `ambient`); if `false`, no particles are shown.
  + [NBT List / JSON Array] attributes: A list of [Attributes](https://minecraft.wiki/w/Attribute "Attribute") for this mob. These are used for many purposes in internal calculations, and can be considered a mob's "statistics". Valid attributes for a given mob are listed in the [main article](https://minecraft.wiki/w/Attribute "Attribute").
    - [NBT Compound / JSON Object] An individual attribute.
      * [String] id: The name of this attribute.
      * [Double] base: The base value of this attribute.
      * [NBT List / JSON Array] modifiers: A list of [Modifiers](https://minecraft.wiki/w/Attribute#Modifiers "Attribute") acting on this attribute. Modifiers alter the base value in internal calculations, without changing the original copy. Note that a modifier never modifies base to be higher than its maximum or lower than its minimum for a given attribute.
        + [NBT Compound / JSON Object] An individual modifier.
          - [Double] amount: The amount by which this modifier modifies the base value in calculations.
          - [String] id: A [Resource location](https://minecraft.wiki/w/Resource_location "Resource location") unique to this modifier. Used to identify the modifier so that the correct modifier can be added or removed.
          - [String] operation: `add_value`, `add_multiplied_base`, `add_multiplied_total`. Defines the operation this modifier executes on the attribute's base value.
            * `add_value`: Increment `X``Amount`.
            * `add_multiplied_base`: `Y``X * Amount`.
            * `add_multiplied_total`: Set `Y = Y * (1 + Amount)` (equivalent to Increment `Y``Y * Amount`).
        + The specified modifiers are applied to the attribute, probably whenever the attribute is modified.​[*[more information needed](https://minecraft.wiki/w/Special%3ATalkPage/Entity_format "Special:TalkPage/Entity format")*] To compute the effective value of the attribute, the game:
          1. Sets `X = Base`.
          2. Executes all add\_value modifiers.
          3. Sets `Y = X`.
          4. Executes all add\_multiplied\_base modifiers.
          5. Executes all add\_multiplied\_total modifiers.
          - The value Y is the final effective value of the attribute.​[*[more information needed](https://minecraft.wiki/w/Special%3ATalkPage/Entity_format "Special:TalkPage/Entity format")*]
  + [NBT Compound / JSON Object] Brain: Everything this entity has to keep in mind.
    - [NBT Compound / JSON Object] memories: Used for complex behaviors.​[*[more information needed](https://minecraft.wiki/w/Special%3ATalkPage/Entity_format "Special:TalkPage/Entity format")*] The only mobs that have this tag are described below.

      * [![](/images/EntitySprite_allay.png?a939b)](https://minecraft.wiki/w/Allay "Allay")[Allay](https://minecraft.wiki/w/Allay "Allay") memories: see [Template:Nbt inherit/allay\_memories/template](https://minecraft.wiki/w/Template%3ANbt_inherit/allay_memories/template "Template:Nbt inherit/allay memories/template")
      * [![](/images/EntitySprite_axolotl.png?0b5f0)](https://minecraft.wiki/w/Axolotl "Axolotl")[Axolotl](https://minecraft.wiki/w/Axolotl "Axolotl") memories: see [Template:Nbt inherit/axolotl\_memories/template](https://minecraft.wiki/w/Template%3ANbt_inherit/axolotl_memories/template "Template:Nbt inherit/axolotl memories/template")
      * [![](/images/EntitySprite_camel.png?73196)](https://minecraft.wiki/w/Camel "Camel")[Camel](https://minecraft.wiki/w/Camel "Camel") memories: see [Template:Nbt inherit/camel\_memories/template](https://minecraft.wiki/w/Template%3ANbt_inherit/camel_memories/template "Template:Nbt inherit/camel memories/template")
      * [![](/images/EntitySprite_copper-golem.png?e837d)](https://minecraft.wiki/w/Copper_Golem "Copper Golem")[Copper Golem](https://minecraft.wiki/w/Copper_Golem "Copper Golem") memories: see [Template:Nbt inherit/copper\_golem\_memories/template](https://minecraft.wiki/w/Template%3ANbt_inherit/copper_golem_memories/template "Template:Nbt inherit/copper golem memories/template")
      * [![](/images/EntitySprite_frog.png?15793)](https://minecraft.wiki/w/Frog "Frog")[Frog](https://minecraft.wiki/w/Frog "Frog") memories: see [Template:Nbt inherit/frog\_memories/template](https://minecraft.wiki/w/Template%3ANbt_inherit/frog_memories/template "Template:Nbt inherit/frog memories/template")
      * [![](/images/EntitySprite_goat.png?f85ec)](https://minecraft.wiki/w/Goat "Goat")[Goat](https://minecraft.wiki/w/Goat "Goat") memories: see [Template:Nbt inherit/goat\_memories/template](https://minecraft.wiki/w/Template%3ANbt_inherit/goat_memories/template "Template:Nbt inherit/goat memories/template")
      * [![](/images/EntitySprite_piglin.png?5435e)](https://minecraft.wiki/w/Piglin "Piglin")[Piglin](https://minecraft.wiki/w/Piglin "Piglin") memories: see [Template:Nbt inherit/piglin\_memories/template](https://minecraft.wiki/w/Template%3ANbt_inherit/piglin_memories/template "Template:Nbt inherit/piglin memories/template")
      * [![](/images/EntitySprite_piglin-brute.png?56ccd)](https://minecraft.wiki/w/Piglin_Brute "Piglin Brute")[Piglin Brute](https://minecraft.wiki/w/Piglin_Brute "Piglin Brute") memories: see [Template:Nbt inherit/piglin\_brute\_memories/template](https://minecraft.wiki/w/Template%3ANbt_inherit/piglin_brute_memories/template "Template:Nbt inherit/piglin brute memories/template")
      * [![](/images/EntitySprite_sniffer.png?502b1)](https://minecraft.wiki/w/Sniffer "Sniffer")[Sniffer](https://minecraft.wiki/w/Sniffer "Sniffer") memories: see [Template:Nbt inherit/sniffer\_memories/template](https://minecraft.wiki/w/Template%3ANbt_inherit/sniffer_memories/template "Template:Nbt inherit/sniffer memories/template")
      * [![](/images/EntitySprite_villager.png?05433)](https://minecraft.wiki/w/Villager "Villager")[Villager](https://minecraft.wiki/w/Villager "Villager") memories: see [Template:Nbt inherit/villager\_memories/template](https://minecraft.wiki/w/Template%3ANbt_inherit/villager_memories/template "Template:Nbt inherit/villager memories/template")
      * [![](/images/EntitySprite_warden.png?d9d2f)](https://minecraft.wiki/w/Warden "Warden")[Warden](https://minecraft.wiki/w/Warden "Warden") memories: see [Template:Nbt inherit/warden\_memories/template](https://minecraft.wiki/w/Template%3ANbt_inherit/warden_memories/template "Template:Nbt inherit/warden memories/template")
  + [Boolean] CanPickUpLoot: `1` or `0` (`true`/`false`) - if `true`, the mob can pick up loot (wear armor it picks up, use weapons it picks up).
  + Tags common to all mobs with drops from loot tables see [Template:Nbt inherit/death\_lootable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/death_lootable/template "Template:Nbt inherit/death lootable/template")
  + [Short] DeathTime: Number of ticks the mob has been dead for. Controls death animations. 0 when alive.
  + [NBT Compound / JSON Object] drop\_chances: A map between equipment slot type and chance value. Each entry specifies the chance that the item in that slot is dropped when the mob dies. If not specified or removed, chance is assumed as default (0.085f). A chance value between 0.0f and 1.0f applies a [random](https://minecraft.wiki/w/Drops#Equipped_items "Drops") damage value if dropped and it's only drops if the mob is killed by a player or a tamed wolf. For values higher than 1.0f, the item damage is preserved and it's always dropped. Equipment picked up by mobs is set to 2.0f. Each entry is also used to calculate the chance the item in dropped when swap for a more preferred one[[1]](#cite_note-1), but not directly. If the value is 0.0f or less, the drop chance is 0%, if the value is greater than 0.0f, the drop chance is the value +10% and the item damage is preserved.
    - [Float] head : Chance value for the head item to drop.
    - [Float] chest : Chance value for the chest item to drop.
    - [Float] legs : Chance value for the legs item to drop.
    - [Float] feet : Chance value for the feet item to drop.
    - [Float] mainhand : Chance value for the mainhand item to drop.
    - [Float] offhand : Chance value for the offhand item to drop.
    - [Float] body : Chance value for the body item to drop.
    - [Float] saddle : Chance value for the saddle item to drop.
  + [NBT Compound / JSON Object] equipment: Map between equipment slot type and item stack. Does not exist if the inventory is empty.
    - [NBT Compound / JSON Object] head: The item being held in mob's head slot.
    - [NBT Compound / JSON Object] chest: The item being held in the mob's chest slot.
    - [NBT Compound / JSON Object] legs: The item being held in the mob's legs slot.
    - [NBT Compound / JSON Object] feet: The item being held in the mob's feet slot.
    - [NBT Compound / JSON Object] mainhand: The item being held in the mob's main hand.
    - [NBT Compound / JSON Object] offhand: The item being held in the mob's off hand.
    - [NBT Compound / JSON Object] body: The item being held in the mob's body slot.
    - [NBT Compound / JSON Object] saddle: The item being held in the mob's saddle slot.

      * A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")
  + [Byte] FallFlying: Setting to 1 for non-player entities causes the entity to glide as long as they are wearing elytra in the chest slot. Can be used to detect when the player is gliding without using scoreboard statistics.
  + [Float] Health: number of health the entity has.
  + [Int Array] home\_pos: The mob's "home" position. Mobs will limit their pathfinding to stay within the indicated area. Some mobs, like bats, slimes, magma cubes, phantoms and ender dragons may ignore it. Interacting with leashes or riding may change the home position of the mob. For [creakings](https://minecraft.wiki/w/Creaking "Creaking"), this is the position of their [creaking heart](https://minecraft.wiki/w/Creaking_heart "Creaking heart").
  + [Int] home\_radius: Max radius of the data `home_pos`.
  + [Int] HurtByTimestamp: The last time the mob was damaged, measured in the number of ticks since the mob's creation. Updates to a new value whenever the mob is damaged, then updates again 101 ticks later for reasons unknown. Can be changed with [commands](https://minecraft.wiki/w/Commands "Commands"), but the specified value does not affect natural updates in any way, and is overwritten if the mob receives damage.
  + [Short] HurtTime: Number of ticks the mob turns red for after being hit. 0 when not recently hit.
  + [Int Array] last\_hurt\_by\_mob: The UUID of the last mob that attacked this mob. Clears when the attacking mob dies or despawns.
  + [Int Array] last\_hurt\_by\_player: The UUID of the last player that attacked this mob.
  + [Int] last\_hurt\_by\_player\_memory\_time: (when [Int Array] last\_hurt\_by\_player exists and is valid) Gets set to 100 game ticks (5 seconds) when attacked by a player, and decreases by 1 for every game tick. Clears [Int Array] last\_hurt\_by\_player when the value reaches 0.
  + [NBT Compound / JSON Object][Int Array] leash: Information about where this leash connects to. Does not exist if the entity is not leashed.
    - The int array form ([Int Array]) represents the block location of the fence post that the leash is attached to (3 integers representing the X, Y, and Z coordinates respectively), or a compound containing information about the entity the leash is attached to.
    - The compound form ([NBT Compound / JSON Object]) contains the UUID of the entity that the leash is attached to.
    - [Int Array] UUID: This [Universally Unique IDentifier](https://minecraft.wiki/w/Universally_Unique_IDentifier "Universally Unique IDentifier") of the entity that the leash is attached to.
  + [Boolean] LeftHanded: `1` or `0` (`true`/`false`) - if `true`, the mob renders the main hand as being left.
  + [NBT Compound / JSON Object] locator\_bar\_icon: The waypoint's icon visual data in the [locator bar](https://minecraft.wiki/w/Locator_bar "Locator bar").
    - [Int] color: The waypoint's color stored as 32-bit signed integer using [two's complement](https://en.wikipedia.org/wiki/two%27s_complement "wikipedia:two's complement"), assuming the color is fully opaque.
    - [String] style: The waypoint's style name from `[waypoint_style](https://minecraft.wiki/w/Waypoint_style "Waypoint style")` directory in a [resource pack](https://minecraft.wiki/w/Resource_pack "Resource pack").
  + [Boolean] NoAI: `1` or `0` (`true`/`false`) - Setting to `true` disables the mob's AI. The mob does not and cannot move, to the extent of not falling when normally able.
  + [Boolean] PersistenceRequired: `1` or `0` (`true`/`false`) - if `true`, the mob must not despawn naturally.
  + [Int Array] sleeping\_pos: The coordinate of where the entity is sleeping, absent if not sleeping.
  + [String] Team: This tag is actually not part of the NBT data of a mob, but instead used when spawning it, so it cannot be tested for. It makes the mob instantly join the [scoreboard](https://minecraft.wiki/w/Scoreboard "Scoreboard") team with that name.
  + [Int] ticks\_since\_last\_hurt\_by\_mob: (when [Int Array] last\_hurt\_by\_mob exists and is valid) The number of game ticks since the last time the mob was attacked by the mob described by [Int Array] last\_hurt\_by\_mob.

#### Mob-specific data


Many mobs additionally have individual data.

[![](/images/EntitySprite_allay.png?a939b)](https://minecraft.wiki/w/Allay "Allay")[**allay**](https://minecraft.wiki/w/Allay "Allay")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Long] DuplicationCooldown: The allay's duplication cooldown in ticks. This is set to 6000 game ticks (5 minutes) when the allay duplicates.
  + [NBT List / JSON Array] Inventory: List of items the allay has picked up. This list can contain at most one compound tag. The item given by the player to the allay is stored in its `equipment.mainhand` tag, not here.

    - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")
  + [NBT Compound / JSON Object] listener: The vibration event listener of this allay.
    - [Int] distance: Nonnegative integer.
    - [NBT Compound / JSON Object] event: Optional.
      * [Int] distance: Nonnegative integer.
      * [String] game\_event: A resource location of the game event.
      * [NBT List / JSON Array] pos: Three doubles representing the X, Y, and Z coordinates.
      * [Int Array] projectile\_owner: Optional. The projectile owner's [UUID](https://minecraft.wiki/w/UUID "UUID"). The 128-bit UUID is stored as four 32-bit integers, ordered from most to least significant.
      * [Int Array] source: Optional. The source entity's [UUID](https://minecraft.wiki/w/UUID "UUID"). The 128-bit UUID is stored as four 32-bit integers, ordered from most to least significant.
    - [Int] event\_delay: Nonnegative integer.
    - [Int] event\_distance: Nonnegative integer.
    - [Int] range: Nonnegative integer.
    - [NBT Compound / JSON Object] source: Position source.
      * [String] type: A resource location of the position source type.
      * For type `block`
        + [Int Array] pos: X, Y, and Z coordinates.
      * For type `entity`
        + [Int Array] source\_entity: The entity's [UUID](https://minecraft.wiki/w/UUID "UUID"). The 128-bit UUID is stored as four 32-bit integers, ordered from most to least significant.
        + [Float] y\_offset:

[![](/images/EntitySprite_armadillo.png?89a6e)](https://minecraft.wiki/w/Armadillo "Armadillo")[**armadillo**](https://minecraft.wiki/w/Armadillo "Armadillo")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Int] scute\_time: The number of ticks until the armadillo drops a scute. A scute is dropped at 0 and this timer gets reset to a new random value between 6000 and 12000.
  + [String] state: The name for the armadillo's current posture. `state:"idle"` means the armadillo is standing normally and is not rolled up. `state:"scared"` means the armadillo has rolled up as it feels threatened by a nearby mob or player. `state:"unrolling"` means the armadillo is playing its unrolling animation, exiting its scared state. Any other string for `state` defaults to the same behavior as "idle".

[![](/images/EntitySprite_armor-stand.png?6a1bf)](https://minecraft.wiki/w/Armor_Stand "Armor Stand")[**armor\_stand**](https://minecraft.wiki/w/Armor_Stand "Armor Stand")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + Tags common to mobs except `LeftHanded`, `DeathLootTable`, `DeathLootTableSeed`, `drop_chances`, `home_pos`, `home_radius`, `NoAI`, `leash`, `CanPickUpLoot` and `PersistenceRequired`.
  + [Int] DisabledSlots: Bit field allowing disable place/replace/remove of armor elements. For example, the value `16191` or`4144959` disables placing, removing and replacing of all equipment. These can be found using the bitwise OR operator.
  + [Byte] Invisible: 1 or 0 (true/false) - if true, ArmorStand is invisible, although items on it still display.
  + [Byte] Marker: 1 or 0 (true/false) - if true, ArmorStand's size is set to 0, has a tiny hitbox, and disables interactions with it. May not exist.
  + [Byte] NoBasePlate: 1 or 0 (true/false) - if true, ArmorStand does not display the base beneath it.
  + [NBT Compound / JSON Object] Pose: Rotation values for the ArmorStand's pose. All values are in degrees.
    - [NBT List / JSON Array] Body: Body-specific rotations.
      * [Float]: x-rotation.
      * [Float]: y-rotation.
      * [Float]: z-rotation.
    - [NBT List / JSON Array] Head: Head-specific rotations.
      * [Float]: x-rotation.
      * [Float]: y-rotation.
      * [Float]: z-rotation.
    - [NBT List / JSON Array] LeftArm: Left Arm-specific rotations.
      * [Float]: x-rotation.
      * [Float]: y-rotation.
      * [Float]: z-rotation.
    - [NBT List / JSON Array] LeftLeg: Left Leg-specific rotations.
      * [Float]: x-rotation.
      * [Float]: y-rotation.
      * [Float]: z-rotation.
    - [NBT List / JSON Array] RightArm: Right Arm-specific rotations.
      * [Float]: x-rotation.
      * [Float]: y-rotation.
      * [Float]: z-rotation.
    - [NBT List / JSON Array] RightLeg: Right Leg-specific rotations.
      * [Float]: x-rotation.
      * [Float]: y-rotation.
      * [Float]: z-rotation.
  + [Byte] ShowArms: 1 or 0 (true/false) - if true, ArmorStand displays full wooden arms. If false, also place and replace interactions with the hand item slot are disabled.
  + [Byte] Small: 1 or 0 (true/false) - if true, ArmorStand is much smaller, similar to the size of a baby zombie.

Disabled slots

| Binary | Integer number | Result |
| --- | --- | --- |
| 2^0 | 1 | Disable adding or changing mainhand item |
| 2^1 | 2 | Disable adding or changing boots item |
| 2^2 | 4 | Disable adding or changing leggings item |
| 2^3 | 8 | Disable adding or changing chestplate item |
| 2^4 | 16 | Disable adding or changing helmet item |
| 2^5 | 32 | Disable adding or changing offhand item |
| 2^8 | 256 | Disable removing or changing mainhand item |
| 2^9 | 512 | Disable removing or changing boots item |
| 2^10 | 1024 | Disable removing or changing leggings item |
| 2^11 | 2048 | Disable removing or changing chestplate item |
| 2^12 | 4096 | Disable removing or changing helmet item |
| 2^13 | 8192 | Disable removing or changing offhand item |
| 2^16 | 65536 | Disable adding mainhand item |
| 2^17 | 131072 | Disable adding boots item |
| 2^18 | 262144 | Disable adding leggings item |
| 2^19 | 524288 | Disable adding chestplate item |
| 2^20 | 1048576 | Disable adding helmet item |
| 2^21 | 2097152 | Disable adding offhand item |

[![](/images/EntitySprite_axolotl.png?0b5f0)](https://minecraft.wiki/w/Axolotl "Axolotl")[**axolotl**](https://minecraft.wiki/w/Axolotl "Axolotl")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] FromBucket: 1 or 0 (`true`/`false`) – if `true`, indicates the axolotl has been released from a bucket.
  + [Int] Variant: ID of the axolotl's variant. Represents the [`minecraft:axolotl/variant`](https://minecraft.wiki/w/Data_component_format#axolotl/variant "Data component format") component.

| Variant | Numerical ID | Identifier |
| --- | --- | --- |
| [![](/images/thumb/Lucy_Axolotl_JE2.png/32px-Lucy_Axolotl_JE2.png?90400)](https://minecraft.wiki/w/File%3ALucy_Axolotl_JE2.png) Lucy | `0` | `lucy` |
| [![](/images/thumb/Wild_Axolotl_JE1.png/32px-Wild_Axolotl_JE1.png?da91b)](https://minecraft.wiki/w/File%3AWild_Axolotl_JE1.png) Wild | `1` | `wild` |
| [![](/images/thumb/Gold_Axolotl_JE2.png/32px-Gold_Axolotl_JE2.png?14db1)](https://minecraft.wiki/w/File%3AGold_Axolotl_JE2.png) Gold | `2` | `gold` |
| [![](/images/thumb/Cyan_Axolotl_JE2.png/32px-Cyan_Axolotl_JE2.png?9461c)](https://minecraft.wiki/w/File%3ACyan_Axolotl_JE2.png) Cyan | `3` | `cyan` |
| [![](/images/thumb/Blue_Axolotl_JE2.png/32px-Blue_Axolotl_JE2.png?2e14d)](https://minecraft.wiki/w/File%3ABlue_Axolotl_JE2.png) Blue | `4` | `blue` |

[![](/images/EntitySprite_bat.png?4b561)](https://minecraft.wiki/w/Bat "Bat")[**bat**](https://minecraft.wiki/w/Bat "Bat")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] BatFlags: 1 or 0 (true/false) - true if the bat is hanging upside-down from a block, false if the bat is flying.

[![](/images/EntitySprite_bee.png?5d625)](https://minecraft.wiki/w/Bee "Bee")[**bee**](https://minecraft.wiki/w/Bee "Bee")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can become angry see [Template:Nbt inherit/angerable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/angerable/template "Template:Nbt inherit/angerable/template")
  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Int] CannotEnterHiveTicks: Time left in ticks until the bee can enter a beehive. Used when the bee is angered and released from the hive by a player, but the hive is smoked by a [campfire](https://minecraft.wiki/w/Campfire "Campfire").
  + [Int] CropsGrownSincePollination: How many crops the bee has grown since its last pollination. Used to limit number of crops it can grow.
  + [Int Array] flower\_pos: Block location, as 3 integers, of the flower that the bee is circling.
  + [Boolean] HasNectar: 1 or 0 (true/false) - true if the bee is carrying nectar.
  + [Boolean] HasStung: 1 or 0 (true/false) - true if the bee has stung a mob or player.
  + [Int Array] hive\_pos: Block location, as 3 integers, of the bee's [hive](https://minecraft.wiki/w/Bee_hive "Bee hive").
  + [Int] TicksSincePollination: Number of ticks passed since the bee's last pollination.

[![](/images/EntitySprite_blaze.png?43a55)](https://minecraft.wiki/w/Blaze "Blaze")[**blaze**](https://minecraft.wiki/w/Blaze "Blaze")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")

[![](/images/EntitySprite_bogged.png?2cf56)](https://minecraft.wiki/w/Bogged "Bogged")[**bogged**](https://minecraft.wiki/w/Bogged "Bogged")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")

[![](/images/EntitySprite_breeze.png?cd2af)](https://minecraft.wiki/w/Breeze "Breeze")[**breeze**](https://minecraft.wiki/w/Breeze "Breeze")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")

[![](/images/EntitySprite_camel.png?73196)](https://minecraft.wiki/w/Camel "Camel")[**camel**](https://minecraft.wiki/w/Camel "Camel")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] Bred: 1 or 0 (true/false) – Unknown. Remains 0 after breeding. If true, causes it to stay near other horses with this flag set.
  + [Byte] EatingHaystack: 1 or 0 (true/false) – true if the mob is eating grass.
  + [Int Array] Owner: The [UUID](https://minecraft.wiki/w/UUID "UUID") of the entity that tamed the mob, stored as four ints. Has no effect on behavior. Does not exist if there is no owner.
  + [Byte] Tame: 1 or 0 (true/false) – true if the mob is tamed.
  + [Int] Temper: Ranges from 0 to 100; increases with feeding. Higher values make a mob easier to tame.
  + [Long] LastPoseTick: The tick when the camel started changing its pose.

[![](/images/EntitySprite_camel-husk.png?304cb)](https://minecraft.wiki/w/Camel_Husk "Camel Husk")[**camel\_husk**](https://minecraft.wiki/w/Camel_Husk "Camel Husk")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] Bred: 1 or 0 (true/false) – Unknown. Remains 0 after breeding. If true, causes it to stay near other horses with this flag set.
  + [Byte] EatingHaystack: 1 or 0 (true/false) – true if the mob is eating grass.
  + [Int Array] Owner: The [UUID](https://minecraft.wiki/w/UUID "UUID") of the entity that tamed the mob, stored as four ints. Has no effect on behavior. Does not exist if there is no owner.
  + [Byte] Tame: 1 or 0 (true/false) – true if the mob is tamed.
  + [Int] Temper: Ranges from 0 to 100; increases with feeding. Higher values make a mob easier to tame.
  + [Long] LastPoseTick: The tick when the camel husk started changing its pose.

[![](/images/EntitySprite_cat.png?b3c67)](https://minecraft.wiki/w/Cat "Cat")[**cat**](https://minecraft.wiki/w/Cat "Cat")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can be tamed by players see [Template:Nbt inherit/tameable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/tameable/template "Template:Nbt inherit/tameable/template")
  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] CollarColor: The color of the cat's collar. Present even for stray cats (but does not render); default value is 14. Represents the [`minecraft:cat/collar`](https://minecraft.wiki/w/Data_component_format#cat/collar "Data component format") component.
  + [String] variant: The [resource location](https://minecraft.wiki/w/Resource_location "Resource location") of the variant of the cat. Represents the [`minecraft:cat/variant`](https://minecraft.wiki/w/Data_component_format#cat/variant "Data component format") component.

| Variant | Resource location (Java Edition) | Data Value (Bedrock) |
| --- | --- | --- |
| [![](/images/thumb/White_Cat.png/32px-White_Cat.png?86826)](https://minecraft.wiki/w/File%3AWhite_Cat.png) White | `minecraft:white` | `0` |
| [![](/images/thumb/Tuxedo_Cat_JE2_BE2.png/32px-Tuxedo_Cat_JE2_BE2.png?311fe)](https://minecraft.wiki/w/File%3ATuxedo_Cat_JE2_BE2.png) Tuxedo | `minecraft:black` | `1` |
| [![](/images/thumb/Red_Cat.png/32px-Red_Cat.png?41351)](https://minecraft.wiki/w/File%3ARed_Cat.png) Ginger | `minecraft:red` | `2` |
| [![](/images/thumb/Siamese_Cat_JE3.png/32px-Siamese_Cat_JE3.png?3b2f8)](https://minecraft.wiki/w/File%3ASiamese_Cat_JE3.png) Siamese | `minecraft:siamese` | `3` |
| [![](/images/thumb/British_Shorthair_Cat.png/32px-British_Shorthair_Cat.png?4be7c)](https://minecraft.wiki/w/File%3ABritish_Shorthair_Cat.png) British Shorthair | `minecraft:british_shorthair` | `4` |
| [![](/images/thumb/Calico_Cat.png/32px-Calico_Cat.png?2555e)](https://minecraft.wiki/w/File%3ACalico_Cat.png) Calico | `minecraft:calico` | `5` |
| [![](/images/thumb/Persian_Cat.png/32px-Persian_Cat.png?d625e)](https://minecraft.wiki/w/File%3APersian_Cat.png) Persian | `minecraft:persian` | `6` |
| [![](/images/thumb/Ragdoll_Cat.png/32px-Ragdoll_Cat.png?7933f)](https://minecraft.wiki/w/File%3ARagdoll_Cat.png) Ragdoll | `minecraft:ragdoll` | `7` |
| [![](/images/thumb/Tabby_Cat.png/32px-Tabby_Cat.png?ea9ab)](https://minecraft.wiki/w/File%3ATabby_Cat.png) Tabby | `minecraft:tabby` | `8` |
| [![](/images/thumb/Black_Cat.png/32px-Black_Cat.png?95035)](https://minecraft.wiki/w/File%3ABlack_Cat.png) Black | `minecraft:all_black` | `9` |
| [![](/images/thumb/Jellie_Cat.png/32px-Jellie_Cat.png?e5d99)](https://minecraft.wiki/w/File%3AJellie_Cat.png) Jellie | `minecraft:jellie` | `10` |

| Color | Data value |
| --- | --- |
| ![BlockSprite white-concrete.png: Sprite image for white-concrete in Minecraft](/images/BlockSprite_white-concrete.png?52c10) White | `0` |
| ![BlockSprite orange-concrete.png: Sprite image for orange-concrete in Minecraft](/images/BlockSprite_orange-concrete.png?bdca4) Orange | `1` |
| ![BlockSprite magenta-concrete.png: Sprite image for magenta-concrete in Minecraft](/images/BlockSprite_magenta-concrete.png?dd106) Magenta | `2` |
| ![BlockSprite light-blue-concrete.png: Sprite image for light-blue-concrete in Minecraft](/images/BlockSprite_light-blue-concrete.png?eece2) Light Blue | `3` |
| ![BlockSprite yellow-concrete.png: Sprite image for yellow-concrete in Minecraft](/images/BlockSprite_yellow-concrete.png?37c9d) Yellow | `4` |
| ![BlockSprite lime-concrete.png: Sprite image for lime-concrete in Minecraft](/images/BlockSprite_lime-concrete.png?579cf) Lime | `5` |
| ![BlockSprite pink-concrete.png: Sprite image for pink-concrete in Minecraft](/images/BlockSprite_pink-concrete.png?86d2e) Pink | `6` |
| ![BlockSprite gray-concrete.png: Sprite image for gray-concrete in Minecraft](/images/BlockSprite_gray-concrete.png?c4b36) Gray | `7` |
| ![BlockSprite light-gray-concrete.png: Sprite image for light-gray-concrete in Minecraft](/images/BlockSprite_light-gray-concrete.png?3aa76) Light Gray | `8` |
| ![BlockSprite cyan-concrete.png: Sprite image for cyan-concrete in Minecraft](/images/BlockSprite_cyan-concrete.png?e906d) Cyan | `9` |
| ![BlockSprite purple-concrete.png: Sprite image for purple-concrete in Minecraft](/images/BlockSprite_purple-concrete.png?1d8b2) Purple | `10` |
| ![BlockSprite blue-concrete.png: Sprite image for blue-concrete in Minecraft](/images/BlockSprite_blue-concrete.png?a5e2e) Blue | `11` |
| ![BlockSprite brown-concrete.png: Sprite image for brown-concrete in Minecraft](/images/BlockSprite_brown-concrete.png?95446) Brown | `12` |
| ![BlockSprite green-concrete.png: Sprite image for green-concrete in Minecraft](/images/BlockSprite_green-concrete.png?48eac) Green | `13` |
| ![BlockSprite red-concrete.png: Sprite image for red-concrete in Minecraft](/images/BlockSprite_red-concrete.png?569d8) Red | `14` |
| ![BlockSprite black-concrete.png: Sprite image for black-concrete in Minecraft](/images/BlockSprite_black-concrete.png?a04f0) Black | `15` |

[![](/images/EntitySprite_chicken.png?be6aa)](https://minecraft.wiki/w/Chicken "Chicken")[**chicken**](https://minecraft.wiki/w/Chicken "Chicken")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Int] EggLayTime: Number of ticks until the chicken lays its egg. Laying occurs at 0 and this timer gets reset to a new random value between 6000 and 12000.
  + [Boolean] IsChickenJockey: 1 or 0 (true/false) - Whether or not the chicken is a jockey for a baby zombie. If true, the chicken can naturally despawn, drops 10 experience upon death instead of 1-3 and cannot lay eggs. Baby zombies can still control a ridden chicken even if this is set false.
  + [String] variant: The variant of the chicken. Represents the [`minecraft:chicken/variant`](https://minecraft.wiki/w/Data_component_format#chicken/variant "Data component format") component.

[![](/images/EntitySprite_cod.png?dc4af)](https://minecraft.wiki/w/Cod "Cod")[**cod**](https://minecraft.wiki/w/Cod "Cod")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] FromBucket: 1 or 0 (`true`/`false`) - Whether the fish had ever been released from a bucket.

[![](/images/EntitySprite_copper-golem.png?e837d)](https://minecraft.wiki/w/Copper_Golem "Copper Golem")[**copper\_golem**](https://minecraft.wiki/w/Copper_Golem "Copper Golem")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [String] weather\_state: `unaffected`, `exposed`, `weathered`, or `oxidized` - the oxidation level of the copper golem
  + [Long] next\_weather\_age: The number of ticks `gametime` must reach for the copper golem's oxidation level to change. Setting the value to `-1` automatically sets the oxidation time randomly from `504000` to `552000` + the current `gametime`. If the value is `-2`, the copper golem is waxed (it remains unchanged over time).

[![](/images/EntitySprite_cow.png?893cf)](https://minecraft.wiki/w/Cow "Cow")[**cow**](https://minecraft.wiki/w/Cow "Cow")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [String] variant: The variant of the cow. Represents the [`minecraft:cow/variant`](https://minecraft.wiki/w/Data_component_format#cow/variant "Data component format") component.

[![](/images/EntitySprite_creaking.png?6b7fb)](https://minecraft.wiki/w/Creaking "Creaking")[**creaking**](https://minecraft.wiki/w/Creaking "Creaking")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")

[![](/images/EntitySprite_creeper.png?703e9)](https://minecraft.wiki/w/Creeper "Creeper")[**creeper**](https://minecraft.wiki/w/Creeper "Creeper")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] ExplosionRadius: The [power](https://minecraft.wiki/w/Explosion#Block_destruction "Explosion") of the explosion (default value is 3). Despite the name, this represents the [explosion power](https://minecraft.wiki/w/Explosion#Block_destruction "Explosion") value, so the true *radius* varies and its maximum is approximately 4/3 times this value.
  + [Short] Fuse: States the initial value of the creeper's internal fuse timer (does not affect creepers that fall and explode upon impacting their victim). The internal fuse timer returns to this value if the creeper is no longer within attack range. Default 30.
  + [Byte] ignited: 1 or 0 (true/false) - Whether the creeper has been ignited by [flint and steel](https://minecraft.wiki/w/Flint_and_steel "Flint and steel").
  + [Byte] powered: 1 or 0 (true/false) - May not exist. True if the creeper is charged from being struck by lightning.

[![](/images/EntitySprite_dolphin.png?1910f)](https://minecraft.wiki/w/Dolphin "Dolphin")[**dolphin**](https://minecraft.wiki/w/Dolphin "Dolphin")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Int] Moistness: How moist this dolphin is. Set to 2400 when in water or rain. Decreases by 1 every tick otherwise. The dolphin takes damage when 0 or below.
  + [Byte] GotFish: 1 or 0 (true/false) - if true, this dolphin got fish from a player.

[![](/images/EntitySprite_donkey.png?1910f)](https://minecraft.wiki/w/Donkey "Donkey")[**donkey**](https://minecraft.wiki/w/Donkey "Donkey")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] Bred: 1 or 0 (true/false) – Unknown. Remains 0 after breeding. If true, causes it to stay near other horses with this flag set.
  + [Byte] EatingHaystack: 1 or 0 (true/false) – true if the mob is eating grass.
  + [Int Array] Owner: The [UUID](https://minecraft.wiki/w/UUID "UUID") of the entity that tamed the mob, stored as four ints. Has no effect on behavior. Does not exist if there is no owner.
  + [Byte] Tame: 1 or 0 (true/false) – true if the mob is tamed.
  + [Int] Temper: Ranges from 0 to 100; increases with feeding. Higher values make a mob easier to tame.
  + [Byte] ChestedHorse: 1 or 0 (true/false) - true if the horse has chests. A chested horse that is not a donkey or a mule crashes the game.
  + [NBT List / JSON Array] Items: List of items. Exists only if ChestedHorse is true.
    - [NBT Compound / JSON Object] An item, including the Slot tag. Slots are numbered 2 to 16 for donkeys and mules, and none exist for all other horses.

      * An item stack in a container slot see [Template:Nbt inherit/item/template](https://minecraft.wiki/w/Template%3ANbt_inherit/item/template "Template:Nbt inherit/item/template")

[![](/images/EntitySprite_drowned.png?ef369)](https://minecraft.wiki/w/Drowned "Drowned")[**drowned**](https://minecraft.wiki/w/Drowned "Drowned")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] CanBreakDoors: 1 or 0 (true/false) - true if the zombie can break doors (default value is 0).
  + [Int] DrownedConversionTime: The number of ticks until this zombie converts to a drowned, or husk to zombie. (default value is -1, when no conversion is under way).
  + [Int] InWaterTime: The number of ticks this zombie or husk has been under water, used to start the drowning conversion. (default value is -1, when no conversion is under way).
  + [Byte] IsBaby: 1 or 0 (true/false) - true if this zombie is a baby. May be absent.

[![](/images/EntitySprite_elder-guardian.png?17494)](https://minecraft.wiki/w/Elder_Guardian "Elder Guardian")[**elder\_guardian**](https://minecraft.wiki/w/Elder_Guardian "Elder Guardian")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")

[![](/images/EntitySprite_ender-dragon.png?4a397)](https://minecraft.wiki/w/Ender_Dragon "Ender Dragon")[**ender\_dragon**](https://minecraft.wiki/w/Ender_Dragon "Ender Dragon")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Int] DragonDeathTime: Number of ticks the dragon has been dead for. At 150, the dragon begins spawning experience orbs every 5 ticks (first drop at 155). Removes dragon at values 200 and higher. 0 when alive.
  + [Int] DragonPhase: A number indicating the dragon's current state. `0` means circling. `1` means strafing (preparing to shoot a fireball). `2` means flying to the portal to land (part of transition to landed state). `3` means landing on the portal (part of transition to landed state). `4` means taking off from the portal (part of transition out of landed state). `5` means landed, performing breath attack. `6` means landed, looking for a player for breath attack. `7` means landed, roar before beginning breath attack. `8` means charging player. `9` means flying to portal to die. `10` means hovering (flapping wings while pacing around a fixed point) (default when using the `/[summon](https://minecraft.wiki/w/Commands/summon "Commands/summon")` command).

[![](/images/EntitySprite_enderman.png?c703a)](https://minecraft.wiki/w/Enderman "Enderman")[**enderman**](https://minecraft.wiki/w/Enderman "Enderman")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can become angry see [Template:Nbt inherit/angerable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/angerable/template "Template:Nbt inherit/angerable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [NBT Compound / JSON Object] carriedBlockState: Optional. The block carried by the enderman.

    - Block state see [Template:Nbt inherit/block state/template](https://minecraft.wiki/w/Template%3ANbt_inherit/block_state/template "Template:Nbt inherit/block state/template")

[![](/images/EntitySprite_endermite.png?71743)](https://minecraft.wiki/w/Endermite "Endermite")[**endermite**](https://minecraft.wiki/w/Endermite "Endermite")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Int] Lifetime: How long the endermite has existed in ticks. Disappears when this reaches around 2400.

[![](/images/EntitySprite_evoker.png?f236e)](https://minecraft.wiki/w/Evoker "Evoker")[**evoker**](https://minecraft.wiki/w/Evoker "Evoker")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + Tags common to all mobs spawnable in raids see [Template:Nbt inherit/raidable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/raidable/template "Template:Nbt inherit/raidable/template")
  + [Int] SpellTicks: Number of ticks until a spell can be cast. Set to a positive value when a spell is cast, and decreases by 1 per tick.

[![](/images/EntitySprite_fox.png?91c80)](https://minecraft.wiki/w/Fox "Fox")[**fox**](https://minecraft.wiki/w/Fox "Fox")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] Crouching: 1 or 0 (true/false) – Whether the fox is crouching.
  + [Byte] Sitting: 1 or 0 (true/false) – Whether the fox is sitting.
  + [Byte] Sleeping: 1 or 0 (true/false) – Whether the fox is sleeping.
  + [NBT List / JSON Array] Trusted: A list of players that the fox trusts. For a list with more than 2 elements, only the first and the last are considered.
    - [Int Array]: The [UUID](https://minecraft.wiki/w/UUID "UUID") of each trusted player, stored as four ints.
  + [String] Type: ID of the fox's type. Represents the [`minecraft:fox/variant`](https://minecraft.wiki/w/Data_component_format#fox/variant "Data component format") component.

| Variant | Identifier |
| --- | --- |
| [![](/images/thumb/Fox_JE1_BE1.png/32px-Fox_JE1_BE1.png?ebd36)](https://minecraft.wiki/w/File%3AFox_JE1_BE1.png) Red | `red` |
| [![](/images/thumb/Snow_Fox_JE1_BE1.png/32px-Snow_Fox_JE1_BE1.png?97a92)](https://minecraft.wiki/w/File%3ASnow_Fox_JE1_BE1.png) Snow | `snow` |

[![](/images/EntitySprite_frog.png?15793)](https://minecraft.wiki/w/Frog "Frog")[**frog**](https://minecraft.wiki/w/Frog "Frog")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [String] variant: ID of the frog's variant. Represents the [`minecraft:frog/variant`](https://minecraft.wiki/w/Data_component_format#frog/variant "Data component format") component.

| Variant | Data value |
| --- | --- |
| [![](/images/thumb/Temperate_Frog_JE1_BE1.png/32px-Temperate_Frog_JE1_BE1.png?41fba)](https://minecraft.wiki/w/File%3ATemperate_Frog_JE1_BE1.png) Temperate | `minecraft:temperate` |
| [![](/images/thumb/Warm_Frog_JE1.png/32px-Warm_Frog_JE1.png?664cd)](https://minecraft.wiki/w/File%3AWarm_Frog_JE1.png) Warm | `minecraft:warm` |
| [![](/images/thumb/Cold_Frog_JE1_BE1.png/32px-Cold_Frog_JE1_BE1.png?c5168)](https://minecraft.wiki/w/File%3ACold_Frog_JE1_BE1.png) Cold | `minecraft:cold` |

[![](/images/EntitySprite_ghast.png?f81fc)](https://minecraft.wiki/w/Ghast "Ghast")[**ghast**](https://minecraft.wiki/w/Ghast "Ghast")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] ExplosionPower: The radius of the explosion created by the fireballs the ghast fires. Default value is 1.

[![](/images/EntitySprite_zombie.png?ce11f)](https://minecraft.wiki/w/Giant "Giant")[**giant**](https://minecraft.wiki/w/Giant "Giant")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")

[![](/images/EntitySprite_glow-squid.png?4b4d8)](https://minecraft.wiki/w/Glow_Squid "Glow Squid")[**glow\_squid**](https://minecraft.wiki/w/Glow_Squid "Glow Squid")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Int] DarkTicksRemaining: Countdown of ticks remaining until the glow squid starts glowing. Not glowing while positive, glowing when countdown reaches zero.

[![](/images/EntitySprite_goat.png?f85ec)](https://minecraft.wiki/w/Goat "Goat")[**goat**](https://minecraft.wiki/w/Goat "Goat")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] HasLeftHorn: 1 or 0 (true/false) – if true, indicates this goat has the left horn.
  + [Byte] HasRightHorn: 1 or 0 (true/false) – if true, indicates this goat has the right horn.
  + [Byte] IsScreamingGoat: 1 or 0 (true/false) – if true, indicates this is a screaming goat.

[![](/images/EntitySprite_guardian.png?da544)](https://minecraft.wiki/w/Guardian "Guardian")[**guardian**](https://minecraft.wiki/w/Guardian "Guardian")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")

[![](/images/EntitySprite_happy-ghast.png?45cc0)](https://minecraft.wiki/w/Happy_Ghast "Happy Ghast")[**happy\_ghast**](https://minecraft.wiki/w/Happy_Ghast "Happy Ghast")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Int] still\_timeout: Prevents the Happy Ghast from moving when greater than 0. Set to 10 when a player is less than 2 blocks above and decreases by 1 per tick otherwise. Movement resumes when it reaches 0.

[![](/images/EntitySprite_hoglin.png?06402)](https://minecraft.wiki/w/Hoglin "Hoglin")[**hoglin**](https://minecraft.wiki/w/Hoglin "Hoglin")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Boolean] CannotBeHunted: 1 or 0 (true/false) - if true, piglins do not attack the hoglin. Set to true for hoglins spawned as a part of bastion remnants.
  + [Boolean] IsImmuneToZombification: 1 or 0 (true/false) – if true, the hoglin does not transform to a zoglin when in the Overworld and `TimeInOverworld` does not increment.
  + [Int] TimeInOverworld: The number of ticks that the hoglin has existed in the Overworld; the hoglin converts to a zoglin when this is greater than 300.

[![](/images/EntitySprite_creamy-horse.png?3d52b)](https://minecraft.wiki/w/Horse "Horse")[**horse**](https://minecraft.wiki/w/Horse "Horse")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] Bred: 1 or 0 (true/false) – Unknown. Remains 0 after breeding. If true, causes it to stay near other horses with this flag set.
  + [Byte] EatingHaystack: 1 or 0 (true/false) – true if the mob is eating grass.
  + [Int Array] Owner: The [UUID](https://minecraft.wiki/w/UUID "UUID") of the entity that tamed the mob, stored as four ints. Has no effect on behavior. Does not exist if there is no owner.
  + [Byte] Tame: 1 or 0 (true/false) – true if the mob is tamed.
  + [Int] Temper: Ranges from 0 to 100; increases with feeding. Higher values make a mob easier to tame.
  + [Int] Variant: The variant and markings of the horse. Encoded as `variant | (markings << 8)`. Unused values lead to white horses. The encoded variant field represents the [`minecraft:horse/variant`](https://minecraft.wiki/w/Data_component_format#horse/variant "Data component format") component.

|  | White | Creamy | Chestnut | Brown | Black | Gray | Dark Brown |
| --- | --- | --- | --- | --- | --- | --- | --- |
| None | 0 | 1 | 2 | 3 | 4 | 5 | 6 |
| White | 256 | 257 | 258 | 259 | 260 | 261 | 262 |
| White Field | 512 | 513 | 514 | 515 | 516 | 517 | 518 |
| White Dots | 768 | 769 | 770 | 771 | 772 | 773 | 774 |
| Black Dots | 1024 | 1025 | 1026 | 1027 | 1028 | 1029 | 1030 |

Variant names taken from the names of the texture file they correspond to.

Summoning a horse without specifying the Variant value results in a white horse. Summoning a horse with a correct color byte but an incorrect marking byte results in a horse of the corresponding color but no markings. Summoning a horse with a correct marking byte but an incorrect color byte results in a white horse with the corresponding markings.

[![](/images/EntitySprite_husk.png?99086)](https://minecraft.wiki/w/Husk "Husk")[**husk**](https://minecraft.wiki/w/Husk "Husk")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] CanBreakDoors: 1 or 0 (true/false) - true if the zombie can break doors (default value is 0).
  + [Int] DrownedConversionTime: The number of ticks until this zombie converts to a drowned, or husk to zombie. (default value is -1, when no conversion is under way).
  + [Int] InWaterTime: The number of ticks this zombie or husk has been under water, used to start the drowning conversion. (default value is -1, when no conversion is under way).
  + [Byte] IsBaby: 1 or 0 (true/false) - true if this zombie is a baby. May be absent.

[![](/images/EntitySprite_illusioner.png?e50b9)](https://minecraft.wiki/w/Illusioner "Illusioner")[**illusioner**](https://minecraft.wiki/w/Illusioner "Illusioner")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + Tags common to all mobs spawnable in raids see [Template:Nbt inherit/raidable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/raidable/template "Template:Nbt inherit/raidable/template")
  + [Int] SpellTicks: Number of ticks until a spell can be cast. Set to a positive value when a spell is cast, and decreases by 1 per tick.

[![](/images/EntitySprite_iron-golem.png?bb037)](https://minecraft.wiki/w/Iron_Golem "Iron Golem")[**iron\_golem**](https://minecraft.wiki/w/Iron_Golem "Iron Golem")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can become angry see [Template:Nbt inherit/angerable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/angerable/template "Template:Nbt inherit/angerable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] PlayerCreated: 1 or 0 (true/false) - if true, this golem is player-created and never attacks players.

[![](/images/EntitySprite_creamy-llama.png?0657f)](https://minecraft.wiki/w/Llama "Llama")[**llama**](https://minecraft.wiki/w/Llama "Llama")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] Bred: 1 or 0 (true/false) – Unknown. Remains 0 after breeding. If true, causes it to stay near other horses with this flag set.
  + [Byte] EatingHaystack: 1 or 0 (true/false) – true if the mob is eating grass.
  + [Int Array] Owner: The [UUID](https://minecraft.wiki/w/UUID "UUID") of the entity that tamed the mob, stored as four ints. Has no effect on behavior. Does not exist if there is no owner.
  + [Byte] Tame: 1 or 0 (true/false) – true if the mob is tamed.
  + [Int] Temper: Ranges from 0 to 100; increases with feeding. Higher values make a mob easier to tame.
  + [Byte] ChestedHorse: 1 or 0 (true/false) - true if the llama has chests.
  + [Int] DespawnDelay: A timer for trader llamas to despawn, present only in `trader_llama`. The trader llama despawns when this value reaches 0.
  + [NBT List / JSON Array] Items: List of items. Exists only if `ChestedHorse` is true.
    - [NBT Compound / JSON Object] An item, including the Slot tag.

      * An item stack in a container slot see [Template:Nbt inherit/item/template](https://minecraft.wiki/w/Template%3ANbt_inherit/item/template "Template:Nbt inherit/item/template")
  + [Int] Strength: Ranges from 1 to 5, defaults to 3. Determines the number of items the llama can carry (items = 3 × strength). Also increases the tendency of wolves to run away when attacked by llama spit. Strengths 4 and 5 always causes a wolf to flee.
  + [Int] Variant: The variant of the llama. Represents the [minecraft:llama/variant](https://minecraft.wiki/w/Data_component_format#llama/variant "Data component format") component.

| Variant | Numerical ID | Identifier |
| --- | --- | --- |
| [![](/images/thumb/Creamy_Llama_JE2_BE2.png/32px-Creamy_Llama_JE2_BE2.png?45d8c)](https://minecraft.wiki/w/File%3ACreamy_Llama_JE2_BE2.png) Creamy | `0` | `creamy` |
| [![](/images/thumb/White_Llama_JE2_BE2.png/32px-White_Llama_JE2_BE2.png?c9d61)](https://minecraft.wiki/w/File%3AWhite_Llama_JE2_BE2.png) White | `1` | `white` |
| [![](/images/thumb/Brown_Llama_JE2_BE2.png/32px-Brown_Llama_JE2_BE2.png?3b960)](https://minecraft.wiki/w/File%3ABrown_Llama_JE2_BE2.png) Brown | `2` | `brown` |
| [![](/images/thumb/Gray_Llama_JE2_BE2.png/32px-Gray_Llama_JE2_BE2.png?0d6f5)](https://minecraft.wiki/w/File%3AGray_Llama_JE2_BE2.png) Gray | `3` | `gray` |

[![](/images/EntitySprite_magma-cube.png?0a89c)](https://minecraft.wiki/w/Magma_Cube "Magma Cube")[**magma\_cube**](https://minecraft.wiki/w/Magma_Cube "Magma Cube")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + Tags common to all cube mobs see [Template:Nbt inherit/cube mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/cube_mob/template "Template:Nbt inherit/cube mob/template")

[![](/images/EntitySprite_alex.png?d5812)](https://minecraft.wiki/w/Mannequin "Mannequin")[**mannequin**](https://minecraft.wiki/w/Mannequin "Mannequin")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + **except for** the tags: `CanPickUpLoot`, `DeathLootTable`, `DeathLootTableSeed`, `drop_chances`, `home_pos`, `home_radius`, `leash`, `LeftHanded`, `NoAI`, and `PersistenceRequired`.
  + [String][NBT Compound / JSON Object] profile The textures and/or player profile used to render the mannequin's player model. Cannot be removed, and is always saved as a [NBT Compound / JSON Object] compound. If specified as a string, it corresponds to [String] name. Represents the [`minecraft:profile`](https://minecraft.wiki/w/Data_component_format#profile "Data component format") component.

    - A player profile and/or textures object see [Template:Nbt inherit/profile/template](https://minecraft.wiki/w/Template%3ANbt_inherit/profile/template "Template:Nbt inherit/profile/template")
  + [NBT List / JSON Array] hidden\_layers - List of outer skin layers to hide.
    - Valid entries: `cape`, `jacket`, `left_sleeve`, `right_sleeve`, `left_pants_leg`, `right_pants_leg`, `hat`.
  + [String] main\_hand - Which hand is the main hand of the mannequin.
    - One of `left` and `right`.
  + [String] pose - The pose of the mannequin.
    - Valid entries: `standing`, `crouching`, `swimming`, `fall_flying`, `sleeping`
  + [Boolean] immovable - Optional boolean specifying that the mannequin cannot be moved (defaults to `false`).
  + [String][NBT List / JSON Array][NBT Compound / JSON Object] description - Optional [text component](https://minecraft.wiki/w/Text_component "Text component") shown where a [Player](https://minecraft.wiki/w/Player "Player")'s `below_name` score would show.
    - The default "NPC" (`entity.minecraft.mannequin.label`) text is shown if omitted.
  + [Boolean] hide\_description - Optional boolean specifying that no description should be shown at all.
    - A mannequin with the description hidden displays as if a [Player](https://minecraft.wiki/w/Player "Player") had no `below_name` display.

[![](/images/EntitySprite_mooshroom.png?92493)](https://minecraft.wiki/w/Mooshroom "Mooshroom")[**mooshroom**](https://minecraft.wiki/w/Mooshroom "Mooshroom")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [NBT List / JSON Array] stew\_effects: The effects applied to the [suspicious stew](https://minecraft.wiki/w/Suspicious_stew "Suspicious stew") from milking the mooshroom.
    - [NBT Compound / JSON Object]
      * [String] id: Optional. The [Effect identifier](https://minecraft.wiki/w/Effect#Effect_list "Effect") of the status effect the brown mooshroom may give to a suspicious stew.
      * [Int] duration: Optional. An integer indicating the duration of the status effect the brown mooshroom may give to a suspicious stew.
  + [String] Type: ID of the mooshroom's type. Represents the [`minecraft:mooshroom/variant`](https://minecraft.wiki/w/Data_component_format#mooshroom/variant "Data component format") component.

| Variant | Identifier |
| --- | --- |
| [![](/images/thumb/Red_Mooshroom_JE5_BE3.png/32px-Red_Mooshroom_JE5_BE3.png?de6c9)](https://minecraft.wiki/w/File%3ARed_Mooshroom_JE5_BE3.png) Red | `red` |
| [![](/images/thumb/Brown_Mooshroom_JE3_BE2.png/32px-Brown_Mooshroom_JE3_BE2.png?a419e)](https://minecraft.wiki/w/File%3ABrown_Mooshroom_JE3_BE2.png) Brown | `brown` |

[![](/images/EntitySprite_mule.png?a1576)](https://minecraft.wiki/w/Mule "Mule")[**mule**](https://minecraft.wiki/w/Mule "Mule")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] Bred: 1 or 0 (true/false) – Unknown. Remains 0 after breeding. If true, causes it to stay near other horses with this flag set.
  + [Byte] EatingHaystack: 1 or 0 (true/false) – true if the mob is eating grass.
  + [Int Array] Owner: The [UUID](https://minecraft.wiki/w/UUID "UUID") of the entity that tamed the mob, stored as four ints. Has no effect on behavior. Does not exist if there is no owner.
  + [Byte] Tame: 1 or 0 (true/false) – true if the mob is tamed.
  + [Int] Temper: Ranges from 0 to 100; increases with feeding. Higher values make a mob easier to tame.
  + [Byte] ChestedHorse: 1 or 0 (true/false) - true if the horse has chests. A chested horse that is not a donkey or a mule crashes the game.
  + [NBT List / JSON Array] Items: List of items. Exists only if ChestedHorse is true.
    - [NBT Compound / JSON Object] An item, including the Slot tag. Slots are numbered 2 to 16 for donkeys and mules, and none exist for all other horses.

      * An item stack in a container slot see [Template:Nbt inherit/item/template](https://minecraft.wiki/w/Template%3ANbt_inherit/item/template "Template:Nbt inherit/item/template")

[![](/images/EntitySprite_nautilus.png?3bfe0)](https://minecraft.wiki/w/Nautilus "Nautilus")[**nautilus**](https://minecraft.wiki/w/Nautilus "Nautilus")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")

[![](/images/EntitySprite_ocelot.png?e0135)](https://minecraft.wiki/w/Ocelot "Ocelot")[**ocelot**](https://minecraft.wiki/w/Ocelot "Ocelot")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] Trusting: 1 or 0 (true/false) - true if the ocelot trusts players.

[![](/images/EntitySprite_normal-panda.png?ef307)](https://minecraft.wiki/w/Panda "Panda")[**panda**](https://minecraft.wiki/w/Panda "Panda")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [String] HiddenGene: The secondary gene this panda has, that can transfer to the child.
  + [String] MainGene: The primary gene this panda has, that determines the behavior and appearance of the panda and that can transfer to the child.

| Gene | Data value |
| --- | --- |
| [![](/images/thumb/Panda_JE1_BE1.png/32px-Panda_JE1_BE1.png?31d00)](https://minecraft.wiki/w/File%3APanda_JE1_BE1.png) Normal | `normal` |
| [![](/images/thumb/Lazy_Panda_JE1_BE1.png/32px-Lazy_Panda_JE1_BE1.png?14f6b)](https://minecraft.wiki/w/File%3ALazy_Panda_JE1_BE1.png) Lazy | `lazy` |
| [![](/images/thumb/Worried_Panda_JE1_BE1.png/32px-Worried_Panda_JE1_BE1.png?1cd0c)](https://minecraft.wiki/w/File%3AWorried_Panda_JE1_BE1.png) Worried | `worried` |
| [![](/images/thumb/Playful_Panda_JE1_BE1.png/32px-Playful_Panda_JE1_BE1.png?ba90c)](https://minecraft.wiki/w/File%3APlayful_Panda_JE1_BE1.png) Playful | `playful` |
| [![](/images/thumb/Brown_Panda_JE1_BE1.png/32px-Brown_Panda_JE1_BE1.png?5fd31)](https://minecraft.wiki/w/File%3ABrown_Panda_JE1_BE1.png) Brown | `brown` |
| [![](/images/thumb/Weak_Panda_JE1_BE1.png/32px-Weak_Panda_JE1_BE1.png?88552)](https://minecraft.wiki/w/File%3AWeak_Panda_JE1_BE1.png) Weak | `weak` |
| [![](/images/thumb/Aggressive_Panda_JE1_BE2.png/32px-Aggressive_Panda_JE1_BE2.png?c7fc0)](https://minecraft.wiki/w/File%3AAggressive_Panda_JE1_BE2.png) Aggressive | `aggressive` |

[![](/images/EntitySprite_parrot.png?8ab80)](https://minecraft.wiki/w/Parrot "Parrot")[**parrot**](https://minecraft.wiki/w/Parrot "Parrot")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can be tamed by players see [Template:Nbt inherit/tameable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/tameable/template "Template:Nbt inherit/tameable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Int] Variant: Specifies the color variant of the parrot, default is 0. Represents the [`minecraft:parrot/variant`](https://minecraft.wiki/w/Data_component_format#parrot/variant "Data component format") component.

| Variant | Numerical ID | Identifier |
| --- | --- | --- |
| [![](/images/thumb/Red_Parrot_JE1_BE1.png/32px-Red_Parrot_JE1_BE1.png?90904)](https://minecraft.wiki/w/File%3ARed_Parrot_JE1_BE1.png) Red | `0` | `red_blue` |
| [![](/images/thumb/Blue_Parrot_JE1_BE1.png/32px-Blue_Parrot_JE1_BE1.png?a534a)](https://minecraft.wiki/w/File%3ABlue_Parrot_JE1_BE1.png) Blue | `1` | `blue` |
| [![](/images/thumb/Green_Parrot_JE1_BE1.png/32px-Green_Parrot_JE1_BE1.png?10e01)](https://minecraft.wiki/w/File%3AGreen_Parrot_JE1_BE1.png) Green | `2` | `green` |
| [![](/images/thumb/Cyan_Parrot_JE1_BE1.png/32px-Cyan_Parrot_JE1_BE1.png?73087)](https://minecraft.wiki/w/File%3ACyan_Parrot_JE1_BE1.png) Cyan | `3` | `yellow_blue` |
| [![](/images/thumb/Gray_Parrot_JE1_BE1.png/32px-Gray_Parrot_JE1_BE1.png?1975d)](https://minecraft.wiki/w/File%3AGray_Parrot_JE1_BE1.png) Gray | `4` | `gray` |

[![](/images/EntitySprite_phantom.png?332bd)](https://minecraft.wiki/w/Phantom "Phantom")[**phantom**](https://minecraft.wiki/w/Phantom "Phantom")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Int] size: The size of the phantom. Ranges from `0` to `64`, similar to [slimes](https://minecraft.wiki/w/Slime "Slime"). Unlike slimes, phantoms always have a constant 20HP![❤️](/images/Heart_%28icon%29.png?faf83) × 10 HP, and deal 6HP![❤️](/images/Heart_%28icon%29.png?faf83)![❤️](/images/Heart_%28icon%29.png?faf83)![❤️](/images/Heart_%28icon%29.png?faf83)+`Size` damage. Naturally spawned phantoms are always size 0.
  + [Int Array] anchor\_pos: The phantom, when not actively attacking, attempts to circle around X,Y,Z. Appears to reset to a point above the target player every time the phantom flies up after a swoop. Set to spawn location if not specified.

[![](/images/EntitySprite_pig.png?5435e)](https://minecraft.wiki/w/Pig "Pig")[**pig**](https://minecraft.wiki/w/Pig "Pig")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [String] variant: the variant of the pig. Represents the [`minecraft:pig/variant`](https://minecraft.wiki/w/Data_component_format#pig/variant "Data component format") component.

[![](/images/EntitySprite_piglin.png?5435e)](https://minecraft.wiki/w/Piglin "Piglin")[**piglin**](https://minecraft.wiki/w/Piglin "Piglin")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] CannotHunt: `1` or `0` (`true`/`false`) – if `true`, the piglin does not attack [hoglins](https://minecraft.wiki/w/Hoglin "Hoglin"). Set to true for piglins spawned as a part of bastion remnants during world generation.
  + [NBT List / JSON Array] Inventory: Each compound tag in this list is an item in the piglin's inventory. It can hold a maximum of 8 items.
    - [NBT Compound / JSON Object] An item in the inventory, excluding the `Slot` tag.

      * A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")
  + [Byte] IsBaby: `1` or `0` (`true`/`false`) – `true` if the piglin is a baby. May not exist.
  + [Byte] IsImmuneToZombification: `1` or `0` (`true`/`false`) – if `true`, the piglin does not transform to a [zombified piglin](https://minecraft.wiki/w/Zombified_piglin "Zombified piglin") when in the [Overworld](https://minecraft.wiki/w/Overworld "Overworld").
  + [Int] TimeInOverworld: The number of [ticks](https://minecraft.wiki/w/Tick "Tick") that the piglin has existed in the Overworld; the piglin converts to a zombified piglin when this is greater than 300.

[![](/images/EntitySprite_piglin-brute.png?56ccd)](https://minecraft.wiki/w/Piglin_Brute "Piglin Brute")[**piglin\_brute**](https://minecraft.wiki/w/Piglin_Brute "Piglin Brute")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] IsImmuneToZombification: 1 or 0 (true/false) – if true, the piglin brute does not transform to a zombified piglin when in the Overworld.
  + [Int] TimeInOverworld: The number of ticks that the piglin brute has existed in the Overworld; the piglin brute converts to a zombified piglin when this is greater than 300.

[![](/images/EntitySprite_evoker.png?f236e)](https://minecraft.wiki/w/Pillager "Pillager")[**pillager**](https://minecraft.wiki/w/Pillager "Pillager")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + Tags common to all mobs spawnable in raids see [Template:Nbt inherit/raidable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/raidable/template "Template:Nbt inherit/raidable/template")
  + [NBT List / JSON Array] Inventory: Each compound tag in this list is an item in the pillager's inventory, up to a maximum of 5 slots. Items in two or more slots that can be stacked together are automatically be condensed into one slot. Pillagers don't change their inventory automatically or drop items from it upon death. The inventory is currently unused.​[*[more information needed](https://minecraft.wiki/w/Special%3ATalkPage/Entity_format "Special:TalkPage/Entity format")*]
    - [NBT Compound / JSON Object] An item in the inventory, excluding the Slot tag.

      * A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")

[![](/images/EntitySprite_steve.png?856f8)](https://minecraft.wiki/w/Player "Player")[**player**](https://minecraft.wiki/w/Player "Player")

* [NBT Compound / JSON Object] The root tag. In [level.dat](https://minecraft.wiki/w/Java_Edition_level_format "Java Edition level format") files, this tag is called `Player`.

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + **except for** the tags: `CustomName`, `CustomNameVisible`, and `Glowing`.
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + **except for** the tags:, `CanPickUpLoot`, `LeftHanded`, `PersistenceRequired`, `Leash`, `drop_chances`.
  + [NBT Compound / JSON Object] abilities: The abilities this player has.
    - [Byte] flying: 1 or 0 (`true`/`false`) - `true` if the player is currently flying.
    - [Float] flySpeed: The flying speed, set to `0.05`.
    - [Byte] instabuild: 1 or 0 (`true`/`false`) - If `true`, the player can place blocks without depleting them. This is `true` for Creative mode, and `false` for other game modes.
    - [Byte] invulnerable: 1 or 0 (`true`/`false`) - Behavior is not the same as the invulnerable tag on other entities. If `true`, the player is immune to all damage and harmful effects except for [void](https://minecraft.wiki/w/Void "Void") damage and `/[kill](https://minecraft.wiki/w/Commands/kill "Commands/kill")`. Also, all mobs, whether hostile or not, are passive to the player. `true` when in Creative or Spectator mode, and `false` when in Survival or Adventure mode.
    - [Byte] mayBuild: 1 or 0 (`true`/`false`) - If `true`, the player can place blocks. `true` when in Creative or Survival mode, and `false` when in Spectator or Adventure mode.
    - [Byte] mayfly: 1 or 0 (`true`/`false`) - If `true`, the player can fly and doesn't take fall damage. `true` when in Creative and Spectator modes, and `false` when in Survival and Adventure modes.
    - [Float] walkSpeed: The walking speed, set to `0.1`.
  + [NBT List / JSON Array] current\_explosion\_impact\_pos: Position where the player was when the last explosion happened. Used for [wind charge](https://minecraft.wiki/w/Wind_charge "Wind charge") fall damage reduction.
  + [Int] DataVersion: Version of the player NBT structure. Is increased with every new snapshot and release. See [Data version](https://minecraft.wiki/w/Data_version "Data version").
  + [String] Dimension: The [ID](https://minecraft.wiki/w/Resource_location "Resource location") of the dimension the player is in. Used to store the player's last known location along with `Pos`.
  + [NBT List / JSON Array] EnderItems: Each compound tag in this list is an item in the player's 27-slot ender chest inventory. When empty, list type may have [unexpected value](https://minecraft.wiki/w/NBT_format#Usage "NBT format").
    - [NBT Compound / JSON Object] An item in the inventory.
      * Includes the [Byte] Slot tag - slots are numbered `0`–`26`, inclusive.
      * See [Item\_format § NBT\_structure](https://minecraft.wiki/w/Item_format#NBT_structure "Item format").
  + [NBT List / JSON Array] entered\_nether\_pos: May not exist. A list of 3 doubles, describing the [Overworld](https://minecraft.wiki/w/Overworld "Overworld") position from which the player entered the [Nether](https://minecraft.wiki/w/The_Nether "The Nether"). Used by the `[nether_travel](https://minecraft.wiki/w/Advancement/JSON_format#minecraft:nether_travel "Advancement/JSON format")` [advancement](https://minecraft.wiki/w/Advancement "Advancement") trigger. Set every time the player passes through [a portal](https://minecraft.wiki/w/Nether_portal "Nether portal") from the Overworld to the Nether. When entering a dimension other than the nether *(not by respawning)* this tag is removed. Entering the Nether without using a portal does not update this tag.
    - [Double] x: The X coordinate in the Overworld.
    - [Double] y: The Y coordinate in the Overworld.
    - [Double] z: The Z coordinate in the Overworld.
  + [Float] foodExhaustionLevel: See [Hunger § Mechanics](https://minecraft.wiki/w/Hunger#Mechanics "Hunger").
  + [Int] foodLevel: The value of the hunger bar. Referred to as **hunger**. See [Hunger](https://minecraft.wiki/w/Hunger "Hunger").
  + [Float] foodSaturationLevel: Referred to as **saturation**. See [Hunger § Mechanics](https://minecraft.wiki/w/Hunger#Mechanics "Hunger").
  + [Int] foodTickTimer: See [Hunger](https://minecraft.wiki/w/Hunger "Hunger").
  + [Boolean] ignore\_fall\_damage\_from\_current\_explosion: 1 or 0 (`true`/`false`) - `true` if the current explosion should apply a fall damage reduction. Only used by explosions from [wind charges](https://minecraft.wiki/w/Wind_charges "Wind charges").
  + [NBT List / JSON Array] Inventory: Each compound tag in this list is an item in the player's inventory. (Note: when empty, list type may have [unexpected value](https://minecraft.wiki/w/NBT_format#Usage "NBT format").)
    - [NBT Compound / JSON Object] An item in the inventory.
      * See [Item\_format § NBT\_structure](https://minecraft.wiki/w/Item_format#NBT_structure "Item format").
  + [NBT Compound / JSON Object] LastDeathLocation: May not exist. Location of the player's last death.
    - [String] dimension: Dimension of last death.
    - [Int Array] pos: Coordinates of last death.
  + [Int] playerGameType: The current game mode of the player. `0` means [Survival](https://minecraft.wiki/w/Survival "Survival"), `1` means [Creative](https://minecraft.wiki/w/Creative "Creative"), `2` means [Adventure](https://minecraft.wiki/w/Adventure "Adventure"), and `3` means [Spectator](https://minecraft.wiki/w/Spectator "Spectator").
  + [Int] previousPlayerGameType: The previous game mode of the player.
  + [NBT Compound / JSON Object] recipeBook: Contains a JSON object detailing recipes the player has unlocked.

    - Tags related to the recipe book see [Template:Nbt inherit/Recipe Book/template](https://minecraft.wiki/w/Template%3ANbt_inherit/Recipe_Book/template "Template:Nbt inherit/Recipe Book/template")
  + [NBT Compound / JSON Object] RootVehicle: May not exist. The root entity that the player is riding.
    - [Int Array] Attach: The [UUID](https://minecraft.wiki/w/UUID "UUID") of the entity the player is riding, stored as four ints.
    - [NBT Compound / JSON Object] Entity: The NBT data of the root vehicle.
      * See Entity format.
  + [Int] Score: The score displayed upon death.
  + [Byte] seenCredits: 1 or 0 (`true`/`false`) - `true` if the player has entered the [exit portal](https://minecraft.wiki/w/Exit_portal "Exit portal") in the [End](https://minecraft.wiki/w/The_End "The End") at least once.
  + [NBT Compound / JSON Object] SelectedItem: Data of the item currently being held by the player, excluding the [Slot](https://minecraft.wiki/w/Player.dat_format#Inventory_slot_numbers "Player.dat format") tag. Only exists when using the /data command, this value is not saved in the [player.dat format](https://minecraft.wiki/w/Player.dat_format "Player.dat format").
    - See [item format](https://minecraft.wiki/w/Item_format "Item format").
  + [Int] SelectedItemSlot: The selected hotbar slot of the player. Values are 0-indexed, so the leftmost slot is 0 and the rightmost slot is 8.
  + [NBT Compound / JSON Object] ShoulderEntityLeft: The entity that is on the player's left shoulder. Always displays as a parrot.
    - See Entity format.
  + [NBT Compound / JSON Object] ShoulderEntityRight: The entity that is on the player's right shoulder. Always displays as a parrot.
    - See Entity format.
  + [Short] SleepTimer: The number of [game ticks](https://minecraft.wiki/w/Game_tick "Game tick") the player had been in bed. `0` when the player is not sleeping. When in bed, increases up to 100 ticks, then stops. Skips the night after enough players in beds have reached 100 (see [Bed § Passing the night](https://minecraft.wiki/w/Bed#Passing_the_night "Bed")). When getting out of bed, instantly changes to 100 ticks and then increases for another 9 ticks (up to 109 ticks) before returning to 0 ticks.
  + [NBT Compound / JSON Object] respawn: May not exist. The respawn information of the player. Removed when the player attempts to respawn with no valid bed or respawn anchor to spawn at these coordinates. They are unaffected by breaking a bed or respawn anchor at these coordinates, and are unaffected by the player's death.
    - [Int Array] pos: block position to spawn at
    - [Float] yaw: angle to spawn with (default: 0.0)
    - [String] dimension: dimension id to spawn in (default minecraft:overworld) (required)
    - [Float] pitch: pitch to spawn with. (required)
    - [Boolean] forced: true if this spawn was set through commands (default: false)
  + [NBT Compound / JSON Object] warden\_spawn\_tracker: Contains data about the [warden](https://minecraft.wiki/w/Warden "Warden") spawning process for this player.
    - [Int] warning\_level: A warning level between `0`, and `3` (inclusive). The warden spawns at level 3.
    - [Int] cooldown\_ticks: The number of game ticks before the `warning_level` can be increased again. Decreases by 1 every tick. It is set to 200 game ticks (10 seconds) every time the warning level is increased.
    - [Int] ticks\_since\_last\_warning: The number of game ticks since the player was warned for warden spawning. Increases by 1 every tick. After 12000 game ticks (10 minutes) it resets to level 3, and the `warning_level` decreases by 1 level.
  + [Int] XpLevel: The level shown on the [experience](https://minecraft.wiki/w/Experience "Experience") bar.
  + [Float] XpP: The progress across the experience bar to the next level, stored as a percentage.[*[verify](https://minecraft.wiki/w/Special%3ATalkPage/Entity_format "Special:TalkPage/Entity format")*]
  + [Int] XpSeed: The seed used for the next enchantment in [enchanting tables](https://minecraft.wiki/w/Enchanting_Table "Enchanting Table").
  + [Int] XpTotal: The total amount of experience the player has collected over time; used for the score upon death.

[![](/images/EntitySprite_polar-bear.png?41cea)](https://minecraft.wiki/w/Polar_Bear "Polar Bear")[**polar\_bear**](https://minecraft.wiki/w/Polar_Bear "Polar Bear")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can become angry see [Template:Nbt inherit/angerable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/angerable/template "Template:Nbt inherit/angerable/template")
  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")

[![](/images/EntitySprite_pufferfish.png?08be3)](https://minecraft.wiki/w/Pufferfish "Pufferfish")[**pufferfish**](https://minecraft.wiki/w/Pufferfish "Pufferfish")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] FromBucket: 1 or 0 (`true`/`false`) - if `true`, the fish has been released from a bucket.
  + [Int] PuffState: A value from 0–2.
    - `0` means the fish is deflated
    - `1` means it is halfway puffed-up
    - `2` means it is fully puffed-up

[![](/images/EntitySprite_brown-rabbit.png?18569)](https://minecraft.wiki/w/Rabbit "Rabbit")[**rabbit**](https://minecraft.wiki/w/Rabbit "Rabbit")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Int] MoreCarrotTicks: Set to 40 when a carrot crop is eaten, decreases by 0–2 every tick until it reaches 0. Rabbit can eat another crop only when it reaches 0.
  + [Int] RabbitType: Determines the skin of the rabbit. Also determines if rabbit should be hostile. Represents the [`minecraft:rabbit/variant`](https://minecraft.wiki/w/Data_component_format#rabbit/variant "Data component format") component.

| Variant | Numerical ID | Identifier |
| --- | --- | --- |
| [![](/images/thumb/Brown_Rabbit_BE4.png/25px-Brown_Rabbit_BE4.png?235b9)](https://minecraft.wiki/w/File%3ABrown_Rabbit_BE4.png) Brown | `0` | `brown` |
| [![](/images/thumb/White_Rabbit_JE3_BE3.png/25px-White_Rabbit_JE3_BE3.png?e4389)](https://minecraft.wiki/w/File%3AWhite_Rabbit_JE3_BE3.png) White | `1` | `white` |
| [![](/images/thumb/Black_Rabbit_JE3_BE3.png/25px-Black_Rabbit_JE3_BE3.png?12c32)](https://minecraft.wiki/w/File%3ABlack_Rabbit_JE3_BE3.png) Black | `2` | `black` |
| [![](/images/thumb/White_Splotched_Rabbit_JE4_BE3.png/25px-White_Splotched_Rabbit_JE4_BE3.png?fec92)](https://minecraft.wiki/w/File%3AWhite_Splotched_Rabbit_JE4_BE3.png) White Splotched | `3` | `white_splotched` |
| [![](/images/thumb/Gold_Rabbit_BE4.png/25px-Gold_Rabbit_BE4.png?235b9)](https://minecraft.wiki/w/File%3AGold_Rabbit_BE4.png) Gold | `4` | `gold` |
| [![](/images/thumb/Salt_Rabbit_BE4.png/25px-Salt_Rabbit_BE4.png?235b9)](https://minecraft.wiki/w/File%3ASalt_Rabbit_BE4.png) Salt | `5` | `salt` |
| [![](/images/thumb/The_Killer_Bunny_JE6.png/25px-The_Killer_Bunny_JE6.png?0d361)](https://minecraft.wiki/w/File%3AThe_Killer_Bunny_JE6.png) The Killer Bunny | `99` | `evil` |
| [![](/images/thumb/Toast_Rabbit_JE3_BE3.png/25px-Toast_Rabbit_JE3_BE3.png?35acd)](https://minecraft.wiki/w/File%3AToast_Rabbit_JE3_BE3.png) Toast | none | none |

[![](/images/EntitySprite_ravager.png?40196)](https://minecraft.wiki/w/Ravager "Ravager")[**ravager**](https://minecraft.wiki/w/Ravager "Ravager")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + Tags common to all mobs spawnable in raids see [Template:Nbt inherit/raidable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/raidable/template "Template:Nbt inherit/raidable/template")
  + [Int] AttackTick: Attack cooldown for this ravager.
  + [Int] RoarTick: Roar attack cooldown for this ravager.
  + [Int] StunTick: Stun attack cooldown for this ravager.

[![](/images/EntitySprite_salmon.png?d308d)](https://minecraft.wiki/w/Salmon "Salmon")[**salmon**](https://minecraft.wiki/w/Salmon "Salmon")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] FromBucket: 1 or 0 (`true`/`false`) - Whether the fish had ever been released from a bucket.
  + [String] type: Can be `small`, `medium`, or `large`. The size of the salmon. Represents the [`minecraft:salmon/size`](https://minecraft.wiki/w/Data_component_format#salmon/size "Data component format") component.

[![](/images/EntitySprite_sheep.png?bd14e)](https://minecraft.wiki/w/Sheep "Sheep")[**sheep**](https://minecraft.wiki/w/Sheep "Sheep")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] Color: The color of the sheep. Default is 0. Represents the [`minecraft:sheep/color`](https://minecraft.wiki/w/Data_component_format#sheep/color "Data component format") component.
  + [Byte] Sheared: 1 or 0 (true/false) - true if the sheep has been shorn.

| Color | Data value |
| --- | --- |
| [![](/images/thumb/White_Sheep_JE5.png/32px-White_Sheep_JE5.png?a5000)](https://minecraft.wiki/w/File%3AWhite_Sheep_JE5.png) White | `0` |
| [![](/images/thumb/Orange_Sheep_JE6.png/32px-Orange_Sheep_JE6.png?33cbb)](https://minecraft.wiki/w/File%3AOrange_Sheep_JE6.png) Orange | `1` |
| [![](/images/thumb/Magenta_Sheep_JE6.png/32px-Magenta_Sheep_JE6.png?26216)](https://minecraft.wiki/w/File%3AMagenta_Sheep_JE6.png) Magenta | `2` |
| [![](/images/thumb/Light_Blue_Sheep_JE6.png/32px-Light_Blue_Sheep_JE6.png?07acc)](https://minecraft.wiki/w/File%3ALight_Blue_Sheep_JE6.png) Light Blue | `3` |
| [![](/images/thumb/Yellow_Sheep_JE6.png/32px-Yellow_Sheep_JE6.png?c0a25)](https://minecraft.wiki/w/File%3AYellow_Sheep_JE6.png) Yellow | `4` |
| [![](/images/thumb/Lime_Sheep_JE6.png/32px-Lime_Sheep_JE6.png?bbf5e)](https://minecraft.wiki/w/File%3ALime_Sheep_JE6.png) Lime | `5` |
| [![](/images/thumb/Pink_Sheep_JE6.png/32px-Pink_Sheep_JE6.png?de607)](https://minecraft.wiki/w/File%3APink_Sheep_JE6.png) Pink | `6` |
| [![](/images/thumb/Gray_Sheep_JE6.png/32px-Gray_Sheep_JE6.png?c659d)](https://minecraft.wiki/w/File%3AGray_Sheep_JE6.png) Gray | `7` |
| [![](/images/thumb/Light_Gray_Sheep_JE6.png/32px-Light_Gray_Sheep_JE6.png?c5f26)](https://minecraft.wiki/w/File%3ALight_Gray_Sheep_JE6.png) Light Gray | `8` |
| [![](/images/thumb/Cyan_Sheep_JE6.png/32px-Cyan_Sheep_JE6.png?d5735)](https://minecraft.wiki/w/File%3ACyan_Sheep_JE6.png) Cyan | `9` |
| [![](/images/thumb/Purple_Sheep_JE6.png/32px-Purple_Sheep_JE6.png?07ae1)](https://minecraft.wiki/w/File%3APurple_Sheep_JE6.png) Purple | `10` |
| [![](/images/thumb/Blue_Sheep_JE6.png/32px-Blue_Sheep_JE6.png?2f5a1)](https://minecraft.wiki/w/File%3ABlue_Sheep_JE6.png) Blue | `11` |
| [![](/images/thumb/Brown_Sheep_JE6.png/32px-Brown_Sheep_JE6.png?69936)](https://minecraft.wiki/w/File%3ABrown_Sheep_JE6.png) Brown | `12` |
| [![](/images/thumb/Green_Sheep_JE6.png/32px-Green_Sheep_JE6.png?f3819)](https://minecraft.wiki/w/File%3AGreen_Sheep_JE6.png) Green | `13` |
| [![](/images/thumb/Red_Sheep_JE6.png/32px-Red_Sheep_JE6.png?9d6c2)](https://minecraft.wiki/w/File%3ARed_Sheep_JE6.png) Red | `14` |
| [![](/images/thumb/Black_Sheep_JE6.png/32px-Black_Sheep_JE6.png?c51be)](https://minecraft.wiki/w/File%3ABlack_Sheep_JE6.png) Black | `15` |

[![](/images/EntitySprite_shulker.png?ca1f9)](https://minecraft.wiki/w/Shulker "Shulker")[**shulker**](https://minecraft.wiki/w/Shulker "Shulker")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] AttachFace: Which face of its block the shulker is attached to. The shulker also opens up in the direction going from the center of the block to that face. `0b` means the top face. `1b` means the bottom face. `2b` means the north face. `3b` means the south face. `4b` means the west face. `5b` means the east face.
  + [Byte] Color: The color of the shulker. Default is 0. Shulkers spawned by eggs or as part of End cities have value 16. Represents the [`minecraft:shulker/color`](https://minecraft.wiki/w/Data_component_format#shulker/color "Data component format") component, with 16 encoding the absence of the component.
  + [Byte] Peek: Percentage of the shulker's way through the process of opening to fully (timewise).
    - The "height" of the shulker at any Peek value is calculated via the equation 1.5 - (cos((((Peek - 128) % 256) - 128) \* pi / 100) / 2) with % being the modulo function.​[*[more information needed](https://minecraft.wiki/w/Special%3ATalkPage/Entity_format "Special:TalkPage/Entity format")*]
    - This "height" goes in the direction that the shulker is facing according to `AttachFace`.​[*[more information needed](https://minecraft.wiki/w/Special%3ATalkPage/Entity_format "Special:TalkPage/Entity format")*]

| Color | Data value |
| --- | --- |
| [![](/images/thumb/White_Shulker.png/32px-White_Shulker.png?d673e)](https://minecraft.wiki/w/File%3AWhite_Shulker.png) White | `0` |
| [![](/images/thumb/Orange_Shulker.png/32px-Orange_Shulker.png?f1aa0)](https://minecraft.wiki/w/File%3AOrange_Shulker.png) Orange | `1` |
| [![](/images/thumb/Magenta_Shulker.png/32px-Magenta_Shulker.png?29a15)](https://minecraft.wiki/w/File%3AMagenta_Shulker.png) Magenta | `2` |
| [![](/images/thumb/Light_Blue_Shulker.png/32px-Light_Blue_Shulker.png?27840)](https://minecraft.wiki/w/File%3ALight_Blue_Shulker.png) Light Blue | `3` |
| [![](/images/thumb/Yellow_Shulker.png/32px-Yellow_Shulker.png?748a6)](https://minecraft.wiki/w/File%3AYellow_Shulker.png) Yellow | `4` |
| [![](/images/thumb/Lime_Shulker.png/32px-Lime_Shulker.png?14e9c)](https://minecraft.wiki/w/File%3ALime_Shulker.png) Lime | `5` |
| [![](/images/thumb/Pink_Shulker.png/32px-Pink_Shulker.png?8d84c)](https://minecraft.wiki/w/File%3APink_Shulker.png) Pink | `6` |
| [![](/images/thumb/Gray_Shulker.png/32px-Gray_Shulker.png?13d11)](https://minecraft.wiki/w/File%3AGray_Shulker.png) Gray | `7` |
| [![](/images/thumb/Light_Gray_Shulker.png/32px-Light_Gray_Shulker.png?859da)](https://minecraft.wiki/w/File%3ALight_Gray_Shulker.png) Light Gray | `8` |
| [![](/images/thumb/Cyan_Shulker.png/32px-Cyan_Shulker.png?3497e)](https://minecraft.wiki/w/File%3ACyan_Shulker.png) Cyan | `9` |
| [![](/images/thumb/Purple_Shulker.png/32px-Purple_Shulker.png?4f519)](https://minecraft.wiki/w/File%3APurple_Shulker.png) Purple | `10` |
| [![](/images/thumb/Blue_Shulker.png/32px-Blue_Shulker.png?d8e92)](https://minecraft.wiki/w/File%3ABlue_Shulker.png) Blue | `11` |
| [![](/images/thumb/Brown_Shulker.png/32px-Brown_Shulker.png?cb47b)](https://minecraft.wiki/w/File%3ABrown_Shulker.png) Brown | `12` |
| [![](/images/thumb/Green_Shulker.png/32px-Green_Shulker.png?a86d5)](https://minecraft.wiki/w/File%3AGreen_Shulker.png) Green | `13` |
| [![](/images/thumb/Red_Shulker.png/32px-Red_Shulker.png?db344)](https://minecraft.wiki/w/File%3ARed_Shulker.png) Red | `14` |
| [![](/images/thumb/Black_Shulker.png/32px-Black_Shulker.png?0c5ec)](https://minecraft.wiki/w/File%3ABlack_Shulker.png) Black | `15` |
| [![](/images/thumb/Shulker_JE1_BE1.png/32px-Shulker_JE1_BE1.png?02a87)](https://minecraft.wiki/w/File%3AShulker_JE1_BE1.png) Default | `16` |

[![](/images/EntitySprite_silverfish.png?0656c)](https://minecraft.wiki/w/Silverfish "Silverfish")[**silverfish**](https://minecraft.wiki/w/Silverfish "Silverfish")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")

[![](/images/EntitySprite_skeleton.png?ff904)](https://minecraft.wiki/w/Skeleton "Skeleton")[**skeleton**](https://minecraft.wiki/w/Skeleton "Skeleton")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Int] StrayConversionTime: The number of ticks until this skeleton converts to a stray (default value is -1, when no conversion is under way).

[![](/images/EntitySprite_skeleton-horse.png?3cde9)](https://minecraft.wiki/w/Skeleton_Horse "Skeleton Horse")[**skeleton\_horse**](https://minecraft.wiki/w/Skeleton_Horse "Skeleton Horse")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] Bred: 1 or 0 (true/false) – Unknown. Remains 0 after breeding. If true, causes it to stay near other horses with this flag set.
  + [Byte] EatingHaystack: 1 or 0 (true/false) – true if the mob is eating grass.
  + [Int Array] Owner: The [UUID](https://minecraft.wiki/w/UUID "UUID") of the entity that tamed the mob, stored as four ints. Has no effect on behavior. Does not exist if there is no owner.
  + [Byte] Tame: 1 or 0 (true/false) – true if the mob is tamed.
  + [Int] Temper: Ranges from 0 to 100; increases with feeding. Higher values make a mob easier to tame.
  + [Byte] SkeletonTrap: 1 or 0 (true/false) - true if the horse is a trapped [skeleton horse](https://minecraft.wiki/w/Skeleton_horse "Skeleton horse"). Does not affect horse type.
  + [Int] SkeletonTrapTime: Incremented each tick when SkeletonTrap is set to 1. The horse automatically despawns when it reaches 18000 (15 minutes).

[![](/images/EntitySprite_slime.png?1c782)](https://minecraft.wiki/w/Slime "Slime")[**slime**](https://minecraft.wiki/w/Slime "Slime")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + Tags common to all cube mobs see [Template:Nbt inherit/cube mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/cube_mob/template "Template:Nbt inherit/cube mob/template")

[![](/images/EntitySprite_sniffer.png?502b1)](https://minecraft.wiki/w/Sniffer "Sniffer")[**sniffer**](https://minecraft.wiki/w/Sniffer "Sniffer")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")

[![](/images/EntitySprite_pumpkin-snow-golem.png?e81b0)](https://minecraft.wiki/w/Snow_Golem "Snow Golem")[**snow\_golem**](https://minecraft.wiki/w/Snow_Golem "Snow Golem")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] Pumpkin : 1 or 0 (true/false) - whether or not the Snow Golem has a pumpkin on its head.

[![](/images/EntitySprite_spider.png?4ee43)](https://minecraft.wiki/w/Spider "Spider")[**spider**](https://minecraft.wiki/w/Spider "Spider")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")

[![](/images/EntitySprite_strider.png?c3ab9)](https://minecraft.wiki/w/Strider "Strider")[**strider**](https://minecraft.wiki/w/Strider "Strider")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")

[![](/images/EntitySprite_squid.png?b1318)](https://minecraft.wiki/w/Squid "Squid")[**squid**](https://minecraft.wiki/w/Squid "Squid")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")

[![](/images/EntitySprite_stray.png?f338b)](https://minecraft.wiki/w/Stray "Stray")[**stray**](https://minecraft.wiki/w/Stray "Stray")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")

[![](/images/EntitySprite_sulfur-cube.png?ad68d)](https://minecraft.wiki/w/Sulfur_Cube "Sulfur Cube")[**sulfur\_cube**](https://minecraft.wiki/w/Sulfur_Cube "Sulfur Cube")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + Only on sulfur cubes, the `equipment.body` tag represents the [`minecraft:sulfur_cube_content`](https://minecraft.wiki/w/Data_component_format#sulfur_cube_content "Data component format") component in [predicates](https://minecraft.wiki/w/Predicates "Predicates") and [loot functions](https://minecraft.wiki/w/Loot_function "Loot function").
  + Tags common to all cube mobs see [Template:Nbt inherit/cube mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/cube_mob/template "Template:Nbt inherit/cube mob/template")
  + [Int] pickup\_timer: The ticks left before the sulfur cube will pick up items from the ground. Is set to 100 when the item is removed using shears, then ticks down until it reaches 0.
  + [Byte] from\_bucket: 1 or 0 (true/false) - 1 if the sulfur cube was spawned by using a [Bucket of Sulfur Cube](https://minecraft.wiki/w/Bucket_of_Sulfur_Cube "Bucket of Sulfur Cube"), 0 if not.
  + [Int] fuse: The number of ticks before the sulfur cube explodes. For sulfur cubes that are not ignited, this value is -1.

[![](/images/EntitySprite_tadpole.png?532f2)](https://minecraft.wiki/w/Tadpole "Tadpole")[**tadpole**](https://minecraft.wiki/w/Tadpole "Tadpole")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Int] Age: Represents the age of the tadpole in ticks. When greater than or equal to 24000 game ticks (20 minutes), the tadpole grows up to a frog.
  + [Byte] FromBucket: 1 or 0 (true/false) - Whether the tadpole had ever been released from a bucket.

[![](/images/EntitySprite_creamy-trader-llama.png?6d474)](https://minecraft.wiki/w/Trader_Llama "Trader Llama")[**trader\_llama**](https://minecraft.wiki/w/Trader_Llama "Trader Llama")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] Bred: 1 or 0 (true/false) – Unknown. Remains 0 after breeding. If true, causes it to stay near other horses with this flag set.
  + [Byte] EatingHaystack: 1 or 0 (true/false) – true if the mob is eating grass.
  + [Int Array] Owner: The [UUID](https://minecraft.wiki/w/UUID "UUID") of the entity that tamed the mob, stored as four ints. Has no effect on behavior. Does not exist if there is no owner.
  + [Byte] Tame: 1 or 0 (true/false) – true if the mob is tamed.
  + [Int] Temper: Ranges from 0 to 100; increases with feeding. Higher values make a mob easier to tame.
  + [Byte] ChestedHorse: 1 or 0 (true/false) - true if the llama has chests.
  + [Int] DespawnDelay: A timer for trader llamas to despawn, present only in `trader_llama`. The trader llama despawns when this value reaches 0.
  + [NBT List / JSON Array] Items: List of items. Exists only if `ChestedHorse` is true.
    - [NBT Compound / JSON Object] An item, including the Slot tag.

      * An item stack in a container slot see [Template:Nbt inherit/item/template](https://minecraft.wiki/w/Template%3ANbt_inherit/item/template "Template:Nbt inherit/item/template")
  + [Int] Strength: Ranges from 1 to 5, defaults to 3. Determines the number of items the llama can carry (items = 3 × strength). Also increases the tendency of wolves to run away when attacked by llama spit. Strengths 4 and 5 always causes a wolf to flee.
  + [Int] Variant: The variant of the llama. Represents the [minecraft:llama/variant](https://minecraft.wiki/w/Data_component_format#llama/variant "Data component format") component.

| Variant | Numerical ID | Identifier |
| --- | --- | --- |
| [![](/images/thumb/Creamy_Llama_JE2_BE2.png/32px-Creamy_Llama_JE2_BE2.png?45d8c)](https://minecraft.wiki/w/File%3ACreamy_Llama_JE2_BE2.png) Creamy | `0` | `creamy` |
| [![](/images/thumb/White_Llama_JE2_BE2.png/32px-White_Llama_JE2_BE2.png?c9d61)](https://minecraft.wiki/w/File%3AWhite_Llama_JE2_BE2.png) White | `1` | `white` |
| [![](/images/thumb/Brown_Llama_JE2_BE2.png/32px-Brown_Llama_JE2_BE2.png?3b960)](https://minecraft.wiki/w/File%3ABrown_Llama_JE2_BE2.png) Brown | `2` | `brown` |
| [![](/images/thumb/Gray_Llama_JE2_BE2.png/32px-Gray_Llama_JE2_BE2.png?0d6f5)](https://minecraft.wiki/w/File%3AGray_Llama_JE2_BE2.png) Gray | `3` | `gray` |

[![](/images/EntitySprite_tropical-fish.png?ee953)](https://minecraft.wiki/w/Tropical_Fish "Tropical Fish")[**tropical\_fish**](https://minecraft.wiki/w/Tropical_Fish "Tropical Fish")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] FromBucket: 1 or 0 (true/false) - Whether the fish had ever been released from a bucket.
  + [Int] Variant: A 4-byte integer. Encodes the [`minecraft:tropical_fish/base_color`](https://minecraft.wiki/w/Data_component_format#tropical_fish/base_color "Data component format"), [`minecraft:tropical_fish/pattern`](https://minecraft.wiki/w/Data_component_format#tropical_fish/pattern "Data component format"), and [`minecraft:tropical_fish/pattern_color`](https://minecraft.wiki/w/Data_component_format#tropical_fish/pattern_color "Data component format") components.
    - The least significant byte has a value of either 0 for a small fish, or 1 for a large fish. Values above 1 result in an invisible fish.
    - The next byte has a value from 0–5, representing the pattern on the fish. Values above 5 result in a fish with no pattern.
    - The next byte has a value from 0–15, representing the color of the fish's body.
    - The most significant byte has a value from 0–15, representing the color of the fish's pattern.

| Color | Data value |
| --- | --- |
| ![BlockSprite white-concrete.png: Sprite image for white-concrete in Minecraft](/images/BlockSprite_white-concrete.png?52c10) White | `0` |
| ![BlockSprite orange-concrete.png: Sprite image for orange-concrete in Minecraft](/images/BlockSprite_orange-concrete.png?bdca4) Orange | `1` |
| ![BlockSprite magenta-concrete.png: Sprite image for magenta-concrete in Minecraft](/images/BlockSprite_magenta-concrete.png?dd106) Magenta | `2` |
| ![BlockSprite light-blue-concrete.png: Sprite image for light-blue-concrete in Minecraft](/images/BlockSprite_light-blue-concrete.png?eece2) Light Blue | `3` |
| ![BlockSprite yellow-concrete.png: Sprite image for yellow-concrete in Minecraft](/images/BlockSprite_yellow-concrete.png?37c9d) Yellow | `4` |
| ![BlockSprite lime-concrete.png: Sprite image for lime-concrete in Minecraft](/images/BlockSprite_lime-concrete.png?579cf) Lime | `5` |
| ![BlockSprite pink-concrete.png: Sprite image for pink-concrete in Minecraft](/images/BlockSprite_pink-concrete.png?86d2e) Pink | `6` |
| ![BlockSprite gray-concrete.png: Sprite image for gray-concrete in Minecraft](/images/BlockSprite_gray-concrete.png?c4b36) Gray | `7` |
| ![BlockSprite light-gray-concrete.png: Sprite image for light-gray-concrete in Minecraft](/images/BlockSprite_light-gray-concrete.png?3aa76) Light Gray | `8` |
| ![BlockSprite cyan-concrete.png: Sprite image for cyan-concrete in Minecraft](/images/BlockSprite_cyan-concrete.png?e906d) Cyan | `9` |
| ![BlockSprite purple-concrete.png: Sprite image for purple-concrete in Minecraft](/images/BlockSprite_purple-concrete.png?1d8b2) Purple | `10` |
| ![BlockSprite blue-concrete.png: Sprite image for blue-concrete in Minecraft](/images/BlockSprite_blue-concrete.png?a5e2e) Blue | `11` |
| ![BlockSprite brown-concrete.png: Sprite image for brown-concrete in Minecraft](/images/BlockSprite_brown-concrete.png?95446) Brown | `12` |
| ![BlockSprite green-concrete.png: Sprite image for green-concrete in Minecraft](/images/BlockSprite_green-concrete.png?48eac) Green | `13` |
| ![BlockSprite red-concrete.png: Sprite image for red-concrete in Minecraft](/images/BlockSprite_red-concrete.png?569d8) Red | `14` |
| ![BlockSprite black-concrete.png: Sprite image for black-concrete in Minecraft](/images/BlockSprite_black-concrete.png?a04f0) Black | `15` |

The fish sizes and patterns are depicted in the following table, with white body color and dark-gray pattern color.

|  |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  | | second-least byte | | | | | |
| 0 | 1 | 2 | 3 | 4 | 5 |
| least byte | 1 | |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  | | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | | |  |  |  |  |  |  |  |  |  |  |  |  |  | | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | | Flopper | | |  | Glitter | | |  | Betty | | |  | | |  | | Stripey | | |  | Blockfish | | |  | Clayfish | | | | | [![](/images/thumb/Tropical_Fish_Patterns.png/300px-Tropical_Fish_Patterns.png?8385e)](https://minecraft.wiki/w/File%3ATropical_Fish_Patterns.png) | | |  |  |  |  |  |  |  |  |  |  |  |  |  | | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | | Kob | | |  | Snooper | | |  | Brinely | | |  | | |  | | Sunstreak | | |  | Dasher | | |  | Spotty | | | | | | | | | |
| 0 |

The 22 varieties of tropical fish most commonly found throughout the world have `Variant` tag values from the following table, which also lists what color/shape/patterns come from that value.

| Shape | Pattern | Base color | Pattern color | Variant | Type | Name |
| --- | --- | --- | --- | --- | --- | --- |
| 0 | 0 | 1 | 0 | 65536 | Orange-White Kob | *Clownfish* |
| 0 | 1 | 7 | 0 | 459008 | Gray-White Sunstreak | *Triggerfish* |
| 0 | 0 | 14 | 0 | 917504 | Red-White Kob | *Tomato Clownfish* |
| 1 | 3 | 14 | 0 | 918273 | Red-White Blockfish | *Red Snapper* |
| 1 | 4 | 14 | 0 | 918529 | Red-White Betty | *Red Cichlid* |
| 1 | 5 | 0 | 1 | 16778497 | White-Orange Clayfish | *Ornate Butterflyfish* |
| 0 | 4 | 5 | 3 | 50660352 | Lime-Light Blue Brinely | *Queen Angelfish* |
| 0 | 5 | 6 | 3 | 50726144 | Pink-Light Blue Spotty | *Cotton Candy Betta* |
| 1 | 0 | 0 | 4 | 67108865 | White-Yellow Flopper | *Threadfin* |
| 0 | 5 | 0 | 4 | 67110144 | White-Yellow Spotty | *Goatfish* |
| 1 | 0 | 4 | 4 | 67371009 | Yellow Flopper | *Yellow Tang* |
| 0 | 3 | 9 | 4 | 67699456 | Cyan-Yellow Dasher | *Yellowtail Parrotfish* |
| 1 | 3 | 10 | 4 | 67764993 | Purple-Yellow Blockfish | *Dottyback* |
| 0 | 3 | 9 | 6 | 101253888 | Cyan-Pink Dasher | *Parrotfish* |
| 1 | 2 | 0 | 7 | 117441025 | White-Gray Glitter | *Moorish Idol* |
| 1 | 5 | 0 | 7 | 117441793 | White-Gray Clayfish | *Butterflyfish* |
| 1 | 1 | 1 | 7 | 117506305 | Orange-Gray Stripey | *Anemone* |
| 1 | 0 | 7 | 7 | 117899265 | Gray Flopper | *Black Tang* |
| 0 | 1 | 11 | 7 | 118161664 | Blue-Gray SunStreak | *Cichlid* |
| 1 | 0 | 7 | 11 | 185008129 | Gray-Blue Flopper | *Blue Tang* |
| 1 | 5 | 0 | 14 | 234882305 | White-Red Clayfish | *Emperor Red Snapper* |
| 0 | 2 | 7 | 14 | 235340288 | Gray-Red Snooper | *Red Lipped Blenny* |

The variant number is the sum of the most significant byte × 224 + second most significant byte × 216 + second least significant byte × 28 + least significant byte.

[![](/images/EntitySprite_turtle.png?75264)](https://minecraft.wiki/w/Turtle "Turtle")[**turtle**](https://minecraft.wiki/w/Turtle "Turtle")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] has\_egg: `1`, or `0` (`true`/`false`) - `true` means the turtle is currently pregnant.

[![](/images/EntitySprite_vex.png?646cb)](https://minecraft.wiki/w/Vex "Vex")[**vex**](https://minecraft.wiki/w/Vex "Vex")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Int Array] bound\_pos: When a vex is idle, it wanders, selecting air blocks from within a 15×11×15 cuboid range centered at X,Y,Z. This central spot is the location of the evoker when it summoned the vex, or if an evoker was not involved, `bound_pos` do not exist.
  + [Int] life\_ticks: Ticks of life remaining, decreasing by 1 per tick. When it reaches zero, the vex starts taking damage and `life_ticks` is set to 20.
  + [Int Array] owner: The [UUID](https://minecraft.wiki/w/UUID "UUID") of the evoker this vex was spawned by, stored as four ints. May not exist.

[![](/images/EntitySprite_villager.png?05433)](https://minecraft.wiki/w/Villager "Villager")[**villager**](https://minecraft.wiki/w/Villager "Villager")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [NBT List / JSON Array] Gossips: Pieces of [gossip](https://minecraft.wiki/w/Villager#Gossiping "Villager") that can be exchanged between villagers when they meet. Is not preserved when removed.
    - [NBT Compound / JSON Object] A piece of gossip.
      * [Int] Value: The strength of the gossip.
        + for `major_negative`: weight -5, max 100, +25 if the villager sees you kill another villager, -10 every 20min, -10 when shared
        + for `minor_negative`: weight -1, max 200, +25 when hit, -20 every 20min, -20 when shared
        + for `major_positive`: weight 5, max 20, +20 when cured, does not decrease and never shared
        + for `minor_positive`: weight 1, max 200, +25 when cured, -1 every 20min, -5 when shared
        + for `trading`: weight 1, max 25, +2 per trade, -2 every 20min, -20 when shared
      * [Int Array] Target The [UUID](https://minecraft.wiki/w/UUID "UUID") of the player who caused the gossip, stored as four ints.
      * [String] Type: An ID value indicating the type of gossip. The possible values are `major_negative`, `minor_negative`, `major_positive`, `minor_positive`, and `trading`.
  + [NBT Compound / JSON Object] Offers: Is generated when the trading menu is opened for the first time.
    - [NBT List / JSON Array] Recipes: List of trade options.
      * [NBT Compound / JSON Object] A trade option.
        + [NBT Compound / JSON Object] buy: The first 'cost' item, without the Slot tag.

          - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")
        + [NBT Compound / JSON Object] buyB: Optional. The second 'cost' item, without the Slot tag.

          - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")
        + [Int] demand: The price adjuster of the first 'cost' item based on demand. Updated when a villager resupply.
        + [Int] maxUses: The maximum number of times this trade can be used before it is disabled. Increases by a random amount from 2 to 12 when offers are refreshed.
        + [Float] priceMultiplier: The multiplier on the [Int] demand price adjuster; the final adjusted price is added to the first 'cost' item's price.
        + [Byte] rewardExp: 1 or 0 (true/false) – Whether this trade provides XP orb drops. All trades from naturally-generated villagers in Java Edition reward XP orbs.
        + [NBT Compound / JSON Object] sell: The item being sold for each set of cost items, without the Slot tag.

          - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")
        + [Int] specialPrice: A modifier added to the original price of the first 'cost' item.
        + [Int] uses: The number of times this trade has been used. The trade becomes disabled when this is greater or equal to maxUses.
        + [Int] xp: How much experience the villager gets from this trade.
  + [NBT Compound / JSON Object] VillagerData: Information about the villager’s type, profession, and level.
    - [Int] level: The current level of this villager's profession. Influences the trading options generated by the villager. If it is greater than their profession's maximum level, no new offers are generated. Increments when the villager fills his trading xp bar. Also used for badge rendering.
      * 1: Novice
      * 2: Apprentice
      * 3: Journeyman
      * 4: Expert
      * 5: Master
    - [String] profession: A [resource location](https://minecraft.wiki/w/Resource_location "Resource location") indicating the villager's profession; see [Villager § Professions](https://minecraft.wiki/w/Villager#Professions "Villager").
    - [String] type: A [resource location](https://minecraft.wiki/w/Resource_location "Resource location") indicating the villager's type; see [Villager § Appearance](https://minecraft.wiki/w/Villager#Appearance "Villager"). Represents the [`minecraft:villager/variant`](https://minecraft.wiki/w/Data_component_format#villager/variant "Data component format") component.
  + [Int] Xp: How much experience the villager currently has, increases with trading in various amounts.
    - 0 to 9: Novice
    - 10 to 69: Apprentice
    - 70 to 149: Journeyman
    - 150 to 249: Expert
    - 250 and more: Master
  + [NBT List / JSON Array] Inventory: Each compound tag in this list is an item in the villager's inventory, up to a maximum of 8 slots. Items in two or more slots that can be stacked together are automatically condensed into one slot. If there are more than 8 slots, the last slot is removed until the total is 8. If there are 9 slots but two previous slots can be condensed, the last slot returns after the two other slots are combined.
    - [NBT Compound / JSON Object] An item in the inventory, excluding the Slot tag.

      * A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")
  + [Long] LastRestock: The last tick the villager went to their job site block to resupply their trades.
  + [Long] LastGossipDecay: The last tick all gossip of the villager has decreased strength naturally.
  + [Int] RestocksToday: The number of restocks a villager has done in 10 minutes from the last restock, or `0` if the villager has not restocked in the last 10 minutes. When a villager has restocked twice in less than 10 minutes, it waits at least 10 minutes for another restock.
  + [Byte] Willing: 1 or 0 (true/false) – true if the villager is willing to mate. Becomes true after certain trades (those that would cause offers to be refreshed), and false after mating.

| Type | Data value |
| --- | --- |
| [![](/images/thumb/Desert_Villager_Base_JE2.png/32px-Desert_Villager_Base_JE2.png?744cf)](https://minecraft.wiki/w/File%3ADesert_Villager_Base_JE2.png) [Desert](https://minecraft.wiki/w/Desert "Desert") | `minecraft:desert` |
| [![](/images/thumb/Jungle_Villager_Base_JE2.png/32px-Jungle_Villager_Base_JE2.png?5869f)](https://minecraft.wiki/w/File%3AJungle_Villager_Base_JE2.png) [Jungle](https://minecraft.wiki/w/Jungle "Jungle") | `minecraft:jungle` |
| [![](/images/thumb/Plains_Villager_Base_JE2.png/32px-Plains_Villager_Base_JE2.png?a2fcc)](https://minecraft.wiki/w/File%3APlains_Villager_Base_JE2.png) [Plains](https://minecraft.wiki/w/Plains "Plains") | `minecraft:plains` |
| [![](/images/thumb/Savanna_Villager_Base_JE2.png/32px-Savanna_Villager_Base_JE2.png?80a98)](https://minecraft.wiki/w/File%3ASavanna_Villager_Base_JE2.png) Savanna | `minecraft:savanna` |
| [![](/images/thumb/Snowy_Villager_Base_JE2.png/32px-Snowy_Villager_Base_JE2.png?b51b3)](https://minecraft.wiki/w/File%3ASnowy_Villager_Base_JE2.png) Snowy | `minecraft:snow` |
| [![](/images/thumb/Swamp_Villager_Base_JE2.png/32px-Swamp_Villager_Base_JE2.png?3f630)](https://minecraft.wiki/w/File%3ASwamp_Villager_Base_JE2.png) [Swamp](https://minecraft.wiki/w/Swamp "Swamp") | `minecraft:swamp` |
| [![](/images/thumb/Taiga_Villager_Base_JE2.png/32px-Taiga_Villager_Base_JE2.png?c95f1)](https://minecraft.wiki/w/File%3ATaiga_Villager_Base_JE2.png) [Taiga](https://minecraft.wiki/w/Taiga "Taiga") | `minecraft:taiga` |

| Profession | Data value |
| --- | --- |
| [![](/images/thumb/Plains_Armorer.png/32px-Plains_Armorer.png?0dee1)](https://minecraft.wiki/w/File%3APlains_Armorer.png) Armorer | `minecraft:armorer` |
| [![](/images/thumb/Plains_Butcher.png/32px-Plains_Butcher.png?795c2)](https://minecraft.wiki/w/File%3APlains_Butcher.png) Butcher | `minecraft:butcher` |
| [![](/images/thumb/Plains_Cartographer.png/32px-Plains_Cartographer.png?f6b50)](https://minecraft.wiki/w/File%3APlains_Cartographer.png) Cartographer | `minecraft:cartographer` |
| [![](/images/thumb/Plains_Cleric.png/32px-Plains_Cleric.png?817d6)](https://minecraft.wiki/w/File%3APlains_Cleric.png) Cleric | `minecraft:cleric` |
| [![](/images/thumb/Plains_Farmer.png/32px-Plains_Farmer.png?b8e42)](https://minecraft.wiki/w/File%3APlains_Farmer.png) Farmer | `minecraft:farmer` |
| [![](/images/thumb/Plains_Fisherman.png/32px-Plains_Fisherman.png?2e0a5)](https://minecraft.wiki/w/File%3APlains_Fisherman.png) Fisherman | `minecraft:fisherman` |
| [![](/images/thumb/Plains_Fletcher.png/32px-Plains_Fletcher.png?cacd0)](https://minecraft.wiki/w/File%3APlains_Fletcher.png) Fletcher | `minecraft:fletcher` |
| [![](/images/thumb/Plains_Leatherworker.png/32px-Plains_Leatherworker.png?b6aae)](https://minecraft.wiki/w/File%3APlains_Leatherworker.png) Leatherworker | `minecraft:leatherworker` |
| [![](/images/thumb/Plains_Librarian.png/32px-Plains_Librarian.png?f9177)](https://minecraft.wiki/w/File%3APlains_Librarian.png) Librarian | `minecraft:librarian` |
| [![](/images/thumb/Plains_Nitwit.png/32px-Plains_Nitwit.png?01c04)](https://minecraft.wiki/w/File%3APlains_Nitwit.png) Nitwit | `minecraft:nitwit` |
| [![](/images/thumb/Plains_Villager_Base_JE2.png/32px-Plains_Villager_Base_JE2.png?a2fcc)](https://minecraft.wiki/w/File%3APlains_Villager_Base_JE2.png) Unemployed | `minecraft:none` |
| [![](/images/thumb/Plains_Mason.png/32px-Plains_Mason.png?59e6b)](https://minecraft.wiki/w/File%3APlains_Mason.png) Mason | `minecraft:mason` |
| [![](/images/thumb/Plains_Shepherd.png/32px-Plains_Shepherd.png?5b307)](https://minecraft.wiki/w/File%3APlains_Shepherd.png) Shepherd | `minecraft:shepherd` |
| [![](/images/thumb/Plains_Toolsmith.png/32px-Plains_Toolsmith.png?d03a0)](https://minecraft.wiki/w/File%3APlains_Toolsmith.png) Toolsmith | `minecraft:toolsmith` |
| [![](/images/thumb/Plains_Weaponsmith.png/32px-Plains_Weaponsmith.png?e38a6)](https://minecraft.wiki/w/File%3APlains_Weaponsmith.png) Weaponsmith | `minecraft:weaponsmith` |

[![](/images/EntitySprite_johnny.png?6d568)](https://minecraft.wiki/w/Vindicator "Vindicator")[**vindicator**](https://minecraft.wiki/w/Vindicator "Vindicator")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + Tags common to all mobs spawnable in raids see [Template:Nbt inherit/raidable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/raidable/template "Template:Nbt inherit/raidable/template")
  + [Byte] Johnny: 1 or 0 (true/false) - if true, causes the vindicator to exhibit [Johnny behavior](https://minecraft.wiki/w/Vindicator#Behavior "Vindicator"). Setting to false prevents the vindicator exhibiting Johnny behavior, even if named *Johnny*. Optional.

[![](/images/EntitySprite_wandering-trader.png?0f9fa)](https://minecraft.wiki/w/Wandering_Trader "Wandering Trader")[**wandering\_trader**](https://minecraft.wiki/w/Wandering_Trader "Wandering Trader")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + The `Age` tag cannot be set to a negative number, making it impossible for them to be a baby.
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Int] DespawnDelay: The number of ticks counted down until this wandering trader is forced to despawn. The wandering trader despawns when this value reaches 1.
  + [NBT Compound / JSON Object] Offers: Is generated when the trading menu is opened for the first time.
    - [NBT List / JSON Array] Recipes: List of trade options.
      * [NBT Compound / JSON Object] A trade option.
        + [NBT Compound / JSON Object] buy: The first 'cost' item, without the Slot tag.

          - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")
        + [NBT Compound / JSON Object] buyB: May not exist. The second 'cost' item, without the Slot tag.

          - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")
        + [Int] maxUses: The maximum number of times this trade can be used before it is disabled. Increases by a random amount from 2 to 12 when offers are refreshed.
        + [Byte] rewardExp: 1 or 0 (true/false) - true if this trade provides XP orb drops. All trades from naturally-generated villagers in Java Edition reward XP orbs.
        + [NBT Compound / JSON Object] sell: The item being sold for each set of cost items, without the Slot tag.

          - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")
        + [Int] uses: The number of times this trade has been used. The trade becomes disabled when this is greater or equal to maxUses.
  + [Int Array] wander\_target: The block location that the trader wanders toward.
  + [NBT List / JSON Array] Inventory: Each compound tag in this list is an item in the wandering trader's inventory, up to a maximum of 8 slots. Items in two or more slots that can be stacked together are automatically be condensed into one slot. If there are more than 8 slots, the last slot is removed until the total is 8. If there are 9 slots but two previous slots can be condensed, the last slot returns after the two other slots are combined. Wandering traders don't change their inventory automatically or drop items from it upon death. The inventory is currently unused.
    - [NBT Compound / JSON Object] An item in the inventory, excluding the Slot tag.

      * A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")

[![](/images/EntitySprite_warden.png?d9d2f)](https://minecraft.wiki/w/Warden "Warden")[**warden**](https://minecraft.wiki/w/Warden "Warden")

* [NBT Compound / JSON Object]: Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [NBT Compound / JSON Object] anger: Anger management of the warden.
    - [NBT List / JSON Array] suspects: List of suspects that have angered the warden.
      * [NBT Compound / JSON Object]: A suspect.
        + [Int] anger: The level of anger. It has a maximum value of 150 and decreases by 1 every second.
        + [Int Array] uuid: The [UUID](https://minecraft.wiki/w/UUID "UUID") of the entity that is associated with the anger, stored as four ints.
  + [NBT Compound / JSON Object] listener: The vibration event listener for this warden.
    - [NBT Compound / JSON Object] event: Exists only if there is an incoming vibration.
      * [Float] distance: The distance between this vibration's source and the block.
      * [String] game\_event: The [resource location](https://minecraft.wiki/w/Resource_location "Resource location") of the vibration event that caused the current incoming vibration.
      * [NBT List / JSON Array] pos: The coordinates of the source of this vibration.
        + [Double]: X coordinate.
        + [Double]: Y coordinate.
        + [Double]: Z coordinate.
      * [Int Array] projectile\_owner: If the vibration was caused by a projectile, this is the [UUID](https://minecraft.wiki/w/UUID "UUID") of the entity that launched the projectile. Does not exist if vibration was not caused by a projectile.
      * [Int Array] source: The [UUID](https://minecraft.wiki/w/UUID "UUID") of the entity that caused the vibration. Does not exist if vibration was not caused by an entity.
    - [Int] event\_delay: How many ticks remain until triggered by the vibration. Set to 0 if there is no incoming vibration
    - [NBT Compound / JSON Object] selector: The data of the vibration selector.​[*[more information needed](https://minecraft.wiki/w/Special%3ATalkPage/Entity_format "Special:TalkPage/Entity format")*]
      * [Long] tick: The game time when the vibration occurs, or -1 if there is no vibration to choose from.​[*[more information needed](https://minecraft.wiki/w/Special%3ATalkPage/Entity_format "Special:TalkPage/Entity format")*]
      * [NBT Compound / JSON Object] event: Candidate game event, with the same structure as the [NBT Compound / JSON Object] event tag above.​[*[more information needed](https://minecraft.wiki/w/Special%3ATalkPage/Entity_format "Special:TalkPage/Entity format")*]

[![](/images/EntitySprite_witch.png?3daa8)](https://minecraft.wiki/w/Witch "Witch")[**witch**](https://minecraft.wiki/w/Witch "Witch")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + Tags common to all mobs spawnable in raids see [Template:Nbt inherit/raidable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/raidable/template "Template:Nbt inherit/raidable/template")

[![](/images/EntitySprite_wither.png?fb756)](https://minecraft.wiki/w/Wither "Wither")[**wither**](https://minecraft.wiki/w/Wither "Wither")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Int] Invul: The number of ticks of invulnerability left after being initially created. 0 once invulnerability has expired.

[![](/images/EntitySprite_wither-skeleton.png?8b1cd)](https://minecraft.wiki/w/Wither_Skeleton "Wither Skeleton")[**wither\_skeleton**](https://minecraft.wiki/w/Wither_Skeleton "Wither Skeleton")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")

[![](/images/EntitySprite_wolf.png?77c1e)](https://minecraft.wiki/w/Wolf "Wolf")[**wolf**](https://minecraft.wiki/w/Wolf "Wolf")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can become angry see [Template:Nbt inherit/angerable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/angerable/template "Template:Nbt inherit/angerable/template")
  + Additional fields for mobs that can be tamed by players see [Template:Nbt inherit/tameable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/tameable/template "Template:Nbt inherit/tameable/template")
  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] CollarColor: The color of the wolf's collar. Present even for wild wolves (but does not render). Default value is 14 (red). Represents the [`minecraft:wolf/collar`](https://minecraft.wiki/w/Data_component_format#wolf/collar "Data component format") component.
  + [String] variant: The variant of this wolf. Default value is "minecraft:pale". Represents the [`minecraft:wolf/variant`](https://minecraft.wiki/w/Data_component_format#wolf/variant "Data component format") component.
  + [String] sound\_variant: The sound variation for this wolf. Represents the [`minecraft:wolf/sound_variant`](https://minecraft.wiki/w/Data_component_format#wolf/sound_variant "Data component format") component.

| Color | Data value |
| --- | --- |
| [![](/images/thumb/Tamed_Wolf_with_White_Collar_JE3_BE4.png/32px-Tamed_Wolf_with_White_Collar_JE3_BE4.png?ccbae)](https://minecraft.wiki/w/File%3ATamed_Wolf_with_White_Collar_JE3_BE4.png) White | `0` |
| [![](/images/thumb/Tamed_Wolf_with_Orange_Collar_JE3_BE4.png/32px-Tamed_Wolf_with_Orange_Collar_JE3_BE4.png?1353f)](https://minecraft.wiki/w/File%3ATamed_Wolf_with_Orange_Collar_JE3_BE4.png) Orange | `1` |
| [![](/images/thumb/Tamed_Wolf_with_Magenta_Collar_JE3_BE4.png/32px-Tamed_Wolf_with_Magenta_Collar_JE3_BE4.png?60c61)](https://minecraft.wiki/w/File%3ATamed_Wolf_with_Magenta_Collar_JE3_BE4.png) Magenta | `2` |
| [![](/images/thumb/Tamed_Wolf_with_Light_Blue_Collar_JE3_BE4.png/32px-Tamed_Wolf_with_Light_Blue_Collar_JE3_BE4.png?b0cd5)](https://minecraft.wiki/w/File%3ATamed_Wolf_with_Light_Blue_Collar_JE3_BE4.png) Light Blue | `3` |
| [![](/images/thumb/Tamed_Wolf_with_Yellow_Collar_JE3_BE4.png/32px-Tamed_Wolf_with_Yellow_Collar_JE3_BE4.png?40eaf)](https://minecraft.wiki/w/File%3ATamed_Wolf_with_Yellow_Collar_JE3_BE4.png) Yellow | `4` |
| [![](/images/thumb/Tamed_Wolf_with_Lime_Collar_JE3_BE4.png/32px-Tamed_Wolf_with_Lime_Collar_JE3_BE4.png?d99ad)](https://minecraft.wiki/w/File%3ATamed_Wolf_with_Lime_Collar_JE3_BE4.png) Lime | `5` |
| [![](/images/thumb/Tamed_Wolf_with_Pink_Collar_JE3_BE4.png/32px-Tamed_Wolf_with_Pink_Collar_JE3_BE4.png?28938)](https://minecraft.wiki/w/File%3ATamed_Wolf_with_Pink_Collar_JE3_BE4.png) Pink | `6` |
| [![](/images/thumb/Tamed_Wolf_with_Gray_Collar_JE3_BE4.png/32px-Tamed_Wolf_with_Gray_Collar_JE3_BE4.png?9a71d)](https://minecraft.wiki/w/File%3ATamed_Wolf_with_Gray_Collar_JE3_BE4.png) Gray | `7` |
| [![](/images/thumb/Tamed_Wolf_with_Light_Gray_Collar_JE3_BE4.png/32px-Tamed_Wolf_with_Light_Gray_Collar_JE3_BE4.png?e249a)](https://minecraft.wiki/w/File%3ATamed_Wolf_with_Light_Gray_Collar_JE3_BE4.png) Light Gray | `8` |
| [![](/images/thumb/Tamed_Wolf_with_Cyan_Collar_JE3_BE4.png/32px-Tamed_Wolf_with_Cyan_Collar_JE3_BE4.png?e84d8)](https://minecraft.wiki/w/File%3ATamed_Wolf_with_Cyan_Collar_JE3_BE4.png) Cyan | `9` |
| [![](/images/thumb/Tamed_Wolf_with_Purple_Collar_JE3_BE4.png/32px-Tamed_Wolf_with_Purple_Collar_JE3_BE4.png?c7f50)](https://minecraft.wiki/w/File%3ATamed_Wolf_with_Purple_Collar_JE3_BE4.png) Purple | `10` |
| [![](/images/thumb/Tamed_Wolf_with_Blue_Collar_JE3_BE4.png/32px-Tamed_Wolf_with_Blue_Collar_JE3_BE4.png?42382)](https://minecraft.wiki/w/File%3ATamed_Wolf_with_Blue_Collar_JE3_BE4.png) Blue | `11` |
| [![](/images/thumb/Tamed_Wolf_with_Brown_Collar_JE3_BE4.png/32px-Tamed_Wolf_with_Brown_Collar_JE3_BE4.png?23725)](https://minecraft.wiki/w/File%3ATamed_Wolf_with_Brown_Collar_JE3_BE4.png) Brown | `12` |
| [![](/images/thumb/Tamed_Wolf_with_Green_Collar_JE3_BE4.png/32px-Tamed_Wolf_with_Green_Collar_JE3_BE4.png?ebc39)](https://minecraft.wiki/w/File%3ATamed_Wolf_with_Green_Collar_JE3_BE4.png) Green | `13` |
| [![](/images/thumb/Tamed_Wolf_with_Red_Collar_JE3_BE4.png/32px-Tamed_Wolf_with_Red_Collar_JE3_BE4.png?0eac6)](https://minecraft.wiki/w/File%3ATamed_Wolf_with_Red_Collar_JE3_BE4.png) Red | `14` |
| [![](/images/thumb/Tamed_Wolf_with_Black_Collar_JE3_BE4.png/32px-Tamed_Wolf_with_Black_Collar_JE3_BE4.png?16e57)](https://minecraft.wiki/w/File%3ATamed_Wolf_with_Black_Collar_JE3_BE4.png) Black | `15` |

Variants

* `pale` (default)
* `ashen`
* `black`
* `chestnut`
* `rusty`
* `snowy`
* `spotted`
* `striped`
* `woods`

Sound Variants

* `classic`
* `angry`
* `big`
* `cute`
* `grumpy`
* `puglin`
* `sad`

[![](/images/EntitySprite_zoglin.png?09afa)](https://minecraft.wiki/w/Zoglin "Zoglin")[**zoglin**](https://minecraft.wiki/w/Zoglin "Zoglin")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] IsBaby: 1 or 0 (true/false) - true if the zoglin is a baby. May not exist.

[![](/images/EntitySprite_zombie.png?ce11f)](https://minecraft.wiki/w/Zombie "Zombie")[**zombie**](https://minecraft.wiki/w/Zombie "Zombie")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] CanBreakDoors: 1 or 0 (true/false) - true if the zombie can break doors (default value is 0).
  + [Int] DrownedConversionTime: The number of ticks until this zombie converts to a drowned, or husk to zombie. (default value is -1, when no conversion is under way).
  + [Int] InWaterTime: The number of ticks this zombie or husk has been under water, used to start the drowning conversion. (default value is -1, when no conversion is under way).
  + [Byte] IsBaby: 1 or 0 (true/false) - true if this zombie is a baby. May be absent.

[![](/images/EntitySprite_zombie-horse.png?f1a1f)](https://minecraft.wiki/w/Zombie_Horse "Zombie Horse")[**zombie\_horse**](https://minecraft.wiki/w/Zombie_Horse "Zombie Horse")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can breed see [Template:Nbt inherit/breedable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/breedable/template "Template:Nbt inherit/breedable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] Bred: 1 or 0 (true/false) – Unknown. Remains 0 after breeding. If true, causes it to stay near other horses with this flag set.
  + [Byte] EatingHaystack: 1 or 0 (true/false) – true if the mob is eating grass.
  + [Int Array] Owner: The [UUID](https://minecraft.wiki/w/UUID "UUID") of the entity that tamed the mob, stored as four ints. Has no effect on behavior. Does not exist if there is no owner.
  + [Byte] Tame: 1 or 0 (true/false) – true if the mob is tamed.
  + [Int] Temper: Ranges from 0 to 100; increases with feeding. Higher values make a mob easier to tame.

[![](/images/EntitySprite_zombie-nautilus.png?56e70)](https://minecraft.wiki/w/Zombie_Nautilus "Zombie Nautilus")[**zombie\_nautilus**](https://minecraft.wiki/w/Zombie_Nautilus "Zombie Nautilus")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can be tamed by players see [Template:Nbt inherit/tameable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/tameable/template "Template:Nbt inherit/tameable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [String] variant: the variant of the nautilus. Represents the [minecraft:zombie\_nautilus/variant](https://minecraft.wiki/w/Data_component_format#zombie_nautilus/variant "Data component format") component.[[note 1]](#cite_note-2)

1. [↑](#cite_ref-2) `minecraft:warm` for the coral variant, `minecraft:temperate` or anything else for the temperate variant.

[![](/images/EntitySprite_zombie-villager.png?8183e)](https://minecraft.wiki/w/Zombie_Villager "Zombie Villager")[**zombie\_villager**](https://minecraft.wiki/w/Zombie_Villager "Zombie Villager")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [NBT List / JSON Array] Gossips: Pieces of [gossip](https://minecraft.wiki/w/Villager#Gossiping "Villager") that can be exchanged between villagers when they meet. Is not preserved when removed.
    - [NBT Compound / JSON Object] A piece of gossip.
      * [Int] Value: The strength of the gossip.
        + for `major_negative`: weight -5, max 100, +25 if the villager sees you kill another villager, -10 every 20min, -10 when shared
        + for `minor_negative`: weight -1, max 200, +25 when hit, -20 every 20min, -20 when shared
        + for `major_positive`: weight 5, max 20, +20 when cured, does not decrease and never shared
        + for `minor_positive`: weight 1, max 200, +25 when cured, -1 every 20min, -5 when shared
        + for `trading`: weight 1, max 25, +2 per trade, -2 every 20min, -20 when shared
      * [Int Array] Target The [UUID](https://minecraft.wiki/w/UUID "UUID") of the player who caused the gossip, stored as four ints.
      * [String] Type: An ID value indicating the type of gossip. The possible values are `major_negative`, `minor_negative`, `major_positive`, `minor_positive`, and `trading`.
  + [NBT Compound / JSON Object] Offers: Is generated when the trading menu is opened for the first time.
    - [NBT List / JSON Array] Recipes: List of trade options.
      * [NBT Compound / JSON Object] A trade option.
        + [NBT Compound / JSON Object] buy: The first 'cost' item, without the Slot tag.

          - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")
        + [NBT Compound / JSON Object] buyB: Optional. The second 'cost' item, without the Slot tag.

          - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")
        + [Int] demand: The price adjuster of the first 'cost' item based on demand. Updated when a villager resupply.
        + [Int] maxUses: The maximum number of times this trade can be used before it is disabled. Increases by a random amount from 2 to 12 when offers are refreshed.
        + [Float] priceMultiplier: The multiplier on the [Int] demand price adjuster; the final adjusted price is added to the first 'cost' item's price.
        + [Byte] rewardExp: 1 or 0 (true/false) – Whether this trade provides XP orb drops. All trades from naturally-generated villagers in Java Edition reward XP orbs.
        + [NBT Compound / JSON Object] sell: The item being sold for each set of cost items, without the Slot tag.

          - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")
        + [Int] specialPrice: A modifier added to the original price of the first 'cost' item.
        + [Int] uses: The number of times this trade has been used. The trade becomes disabled when this is greater or equal to maxUses.
        + [Int] xp: How much experience the villager gets from this trade.
  + [NBT Compound / JSON Object] VillagerData: Information about the villager’s type, profession, and level.
    - [Int] level: The current level of this villager's profession. Influences the trading options generated by the villager. If it is greater than their profession's maximum level, no new offers are generated. Increments when the villager fills his trading xp bar. Also used for badge rendering.
      * 1: Novice
      * 2: Apprentice
      * 3: Journeyman
      * 4: Expert
      * 5: Master
    - [String] profession: A [resource location](https://minecraft.wiki/w/Resource_location "Resource location") indicating the villager's profession; see [Villager § Professions](https://minecraft.wiki/w/Villager#Professions "Villager").
    - [String] type: A [resource location](https://minecraft.wiki/w/Resource_location "Resource location") indicating the villager's type; see [Villager § Appearance](https://minecraft.wiki/w/Villager#Appearance "Villager"). Represents the [`minecraft:villager/variant`](https://minecraft.wiki/w/Data_component_format#villager/variant "Data component format") component.
  + [Int] Xp: How much experience the villager currently has, increases with trading in various amounts.
    - 0 to 9: Novice
    - 10 to 69: Apprentice
    - 70 to 149: Journeyman
    - 150 to 249: Expert
    - 250 and more: Master
  + [Byte] CanBreakDoors: 1 or 0 (true/false) - true if the zombie can break doors (default value is 0).
  + [Int] DrownedConversionTime: The number of ticks until this zombie converts to a drowned, or husk to zombie. (default value is -1, when no conversion is under way).
  + [Int] InWaterTime: The number of ticks this zombie or husk has been under water, used to start the drowning conversion. (default value is -1, when no conversion is under way).
  + [Byte] IsBaby: 1 or 0 (true/false) - true if this zombie is a baby. May be absent.
  + [Int] ConversionTime: -1 when not being converted back to a villager, positive for the number of ticks until conversion back into a villager. The regeneration effect parallels this.
  + [Int Array] ConversionPlayer: The [UUID](https://minecraft.wiki/w/UUID "UUID") of the player who started curing the zombie, stored as four ints.

| Type | Data value |
| --- | --- |
| [![](/images/thumb/Desert_Zombie_Villager_Base.png/32px-Desert_Zombie_Villager_Base.png?01255)](https://minecraft.wiki/w/File%3ADesert_Zombie_Villager_Base.png) Desert | `minecraft:desert` |
| [![](/images/thumb/Jungle_Zombie_Villager_Base.png/32px-Jungle_Zombie_Villager_Base.png?ce898)](https://minecraft.wiki/w/File%3AJungle_Zombie_Villager_Base.png) Jungle | `minecraft:jungle` |
| [![](/images/thumb/Plains_Zombie_Villager_Base_JE1_BE1.png/32px-Plains_Zombie_Villager_Base_JE1_BE1.png?7882a)](https://minecraft.wiki/w/File%3APlains_Zombie_Villager_Base_JE1_BE1.png) Plains | `minecraft:plains` |
| [![](/images/thumb/Savanna_Zombie_Villager_Base.png/32px-Savanna_Zombie_Villager_Base.png?90501)](https://minecraft.wiki/w/File%3ASavanna_Zombie_Villager_Base.png) Savanna | `minecraft:savanna` |
| [![](/images/thumb/Snowy_Zombie_Villager_Base.png/32px-Snowy_Zombie_Villager_Base.png?a188f)](https://minecraft.wiki/w/File%3ASnowy_Zombie_Villager_Base.png) Snowy | `minecraft:snow` |
| [![](/images/thumb/Swamp_Zombie_Villager_Base.png/32px-Swamp_Zombie_Villager_Base.png?86bb3)](https://minecraft.wiki/w/File%3ASwamp_Zombie_Villager_Base.png) Swamp | `minecraft:swamp` |
| [![](/images/thumb/Taiga_Zombie_Villager_Base.png/32px-Taiga_Zombie_Villager_Base.png?547ab)](https://minecraft.wiki/w/File%3ATaiga_Zombie_Villager_Base.png) Taiga | `minecraft:taiga` |

| Profession | Data value |
| --- | --- |
| [![](/images/thumb/Plains_Zombie_Armorer.png/32px-Plains_Zombie_Armorer.png?9235a)](https://minecraft.wiki/w/File%3APlains_Zombie_Armorer.png) Armorer | `minecraft:armorer` |
| [![](/images/thumb/Plains_Zombie_Butcher.png/32px-Plains_Zombie_Butcher.png?6920d)](https://minecraft.wiki/w/File%3APlains_Zombie_Butcher.png) Butcher | `minecraft:butcher` |
| [![](/images/thumb/Plains_Zombie_Cartographer.png/32px-Plains_Zombie_Cartographer.png?8a44d)](https://minecraft.wiki/w/File%3APlains_Zombie_Cartographer.png) Cartographer | `minecraft:cartographer` |
| [![](/images/thumb/Plains_Zombie_Cleric.png/32px-Plains_Zombie_Cleric.png?aeea4)](https://minecraft.wiki/w/File%3APlains_Zombie_Cleric.png) Cleric | `minecraft:cleric` |
| [![](/images/thumb/Plains_Zombie_Farmer.png/32px-Plains_Zombie_Farmer.png?8b275)](https://minecraft.wiki/w/File%3APlains_Zombie_Farmer.png) Farmer | `minecraft:farmer` |
| [![](/images/thumb/Plains_Zombie_Fisherman.png/32px-Plains_Zombie_Fisherman.png?2e928)](https://minecraft.wiki/w/File%3APlains_Zombie_Fisherman.png) Fisherman | `minecraft:fisherman` |
| [![](/images/thumb/Plains_Zombie_Fletcher.png/32px-Plains_Zombie_Fletcher.png?14a4f)](https://minecraft.wiki/w/File%3APlains_Zombie_Fletcher.png) Fletcher | `minecraft:fletcher` |
| [![](/images/thumb/Plains_Zombie_Leatherworker.png/32px-Plains_Zombie_Leatherworker.png?5de0f)](https://minecraft.wiki/w/File%3APlains_Zombie_Leatherworker.png) Leatherworker | `minecraft:leatherworker` |
| [![](/images/thumb/Plains_Zombie_Librarian.png/32px-Plains_Zombie_Librarian.png?62a1a)](https://minecraft.wiki/w/File%3APlains_Zombie_Librarian.png) Librarian | `minecraft:librarian` |
| [![](/images/thumb/Plains_Zombie_Nitwit.png/32px-Plains_Zombie_Nitwit.png?e273a)](https://minecraft.wiki/w/File%3APlains_Zombie_Nitwit.png) Nitwit | `minecraft:nitwit` |
| [![](/images/thumb/Plains_Zombie_Villager_Base_JE1_BE1.png/32px-Plains_Zombie_Villager_Base_JE1_BE1.png?7882a)](https://minecraft.wiki/w/File%3APlains_Zombie_Villager_Base_JE1_BE1.png) Unemployed | `minecraft:none` |
| [![](/images/thumb/Plains_Zombie_Mason.png/32px-Plains_Zombie_Mason.png?6df18)](https://minecraft.wiki/w/File%3APlains_Zombie_Mason.png) Mason | `minecraft:mason` |
| [![](/images/thumb/Plains_Zombie_Shepherd.png/32px-Plains_Zombie_Shepherd.png?b7d89)](https://minecraft.wiki/w/File%3APlains_Zombie_Shepherd.png) Shepherd | `minecraft:shepherd` |
| [![](/images/thumb/Plains_Zombie_Toolsmith.png/32px-Plains_Zombie_Toolsmith.png?734f0)](https://minecraft.wiki/w/File%3APlains_Zombie_Toolsmith.png) Toolsmith | `minecraft:toolsmith` |
| [![](/images/thumb/Plains_Zombie_Weaponsmith_JE3.png/32px-Plains_Zombie_Weaponsmith_JE3.png?21598)](https://minecraft.wiki/w/File%3APlains_Zombie_Weaponsmith_JE3.png) Weaponsmith | `minecraft:weaponsmith` |

[![](/images/EntitySprite_zombified-piglin.png?8dfea)](https://minecraft.wiki/w/Zombified_Piglin "Zombified Piglin")[**zombified\_piglin**](https://minecraft.wiki/w/Zombified_Piglin "Zombified Piglin")

* [NBT Compound / JSON Object] Entity data

  + Additional fields for mobs that can become angry see [Template:Nbt inherit/angerable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/angerable/template "Template:Nbt inherit/angerable/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all mobs see [Template:Nbt inherit/mob/template](https://minecraft.wiki/w/Template%3ANbt_inherit/mob/template "Template:Nbt inherit/mob/template")
  + [Byte] CanBreakDoors: 1 or 0 (true/false) - true if the zombie can break doors (default value is 0).
  + [Int] DrownedConversionTime: The number of ticks until this zombie converts to a drowned, or husk to zombie. (default value is -1, when no conversion is under way).
  + [Int] InWaterTime: The number of ticks this zombie or husk has been under water, used to start the drowning conversion. (default value is -1, when no conversion is under way).
  + [Byte] IsBaby: 1 or 0 (true/false) - true if this zombie is a baby. May be absent.

### Projectiles


Projectiles are a subclass of Entity.

[![](/images/EntitySprite_arrow.png?123f9)](https://minecraft.wiki/w/Arrow "Arrow")[**arrow**](https://minecraft.wiki/w/Arrow "Arrow")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all arrows see [Template:Nbt inherit/arrow/template](https://minecraft.wiki/w/Template%3ANbt_inherit/arrow/template "Template:Nbt inherit/arrow/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all projectiles see [Template:Nbt inherit/projectile/template](https://minecraft.wiki/w/Template%3ANbt_inherit/projectile/template "Template:Nbt inherit/projectile/template")

[![](/images/EntitySprite_wind-charge.png?cd158)](https://minecraft.wiki/w/Wind_Charge "Wind Charge")[**breeze\_wind\_charge**](https://minecraft.wiki/w/Wind_Charge "Wind Charge")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all projectiles see [Template:Nbt inherit/projectile/template](https://minecraft.wiki/w/Template%3ANbt_inherit/projectile/template "Template:Nbt inherit/projectile/template")
  + Tags common to all hurting projectiles see [Template:Nbt inherit/hurting projectile/template](https://minecraft.wiki/w/Template%3ANbt_inherit/hurting_projectile/template "Template:Nbt inherit/hurting projectile/template")

[![](/images/EntitySprite_dragon-fireball.png?24df0)](https://minecraft.wiki/w/Ender_Dragon "Ender Dragon")[**dragon\_fireball**](https://minecraft.wiki/w/Ender_Dragon "Ender Dragon")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all fireballs see [Template:Nbt inherit/fireball/template](https://minecraft.wiki/w/Template%3ANbt_inherit/fireball/template "Template:Nbt inherit/fireball/template")
  + Tags common to all projectiles see [Template:Nbt inherit/projectile/template](https://minecraft.wiki/w/Template%3ANbt_inherit/projectile/template "Template:Nbt inherit/projectile/template")

[![](/images/EntitySprite_egg.png?5154b)](https://minecraft.wiki/w/Egg "Egg")[**egg**](https://minecraft.wiki/w/Egg "Egg")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all projectiles see [Template:Nbt inherit/projectile/template](https://minecraft.wiki/w/Template%3ANbt_inherit/projectile/template "Template:Nbt inherit/projectile/template")
  + [NBT Compound / JSON Object] Item: The item to render as, may be absent.

    - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")

[![](/images/EntitySprite_ender-pearl.png?71743)](https://minecraft.wiki/w/Ender_Pearl "Ender Pearl")[**ender\_pearl**](https://minecraft.wiki/w/Ender_Pearl "Ender Pearl")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all projectiles see [Template:Nbt inherit/projectile/template](https://minecraft.wiki/w/Template%3ANbt_inherit/projectile/template "Template:Nbt inherit/projectile/template")
  + [NBT Compound / JSON Object] Item: The item to render as, may be absent.

    - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")

[![](/images/EntitySprite_eexperience-bottle.png?0cf33)](https://minecraft.wiki/w/Bottle_o%27_Enchanting "Bottle o' Enchanting")[**experience\_bottle**](https://minecraft.wiki/w/Bottle_o%27_Enchanting "Bottle o' Enchanting")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all projectiles see [Template:Nbt inherit/projectile/template](https://minecraft.wiki/w/Template%3ANbt_inherit/projectile/template "Template:Nbt inherit/projectile/template")
  + [NBT Compound / JSON Object] Item: The item to render as, may be absent.

    - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")

[![](/images/EntitySprite_fireball.png?ffb0c)](https://minecraft.wiki/w/Fireball "Fireball")[**fireball**](https://minecraft.wiki/w/Fireball "Fireball")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all projectiles see [Template:Nbt inherit/projectile/template](https://minecraft.wiki/w/Template%3ANbt_inherit/projectile/template "Template:Nbt inherit/projectile/template")
  + Tags common to all hurting projectiles see [Template:Nbt inherit/hurting projectile/template](https://minecraft.wiki/w/Template%3ANbt_inherit/hurting_projectile/template "Template:Nbt inherit/hurting projectile/template")
  + [Byte] ExplosionPower: The power and size of the explosion created by the fireball upon impact. Default value 1.
  + [NBT Compound / JSON Object] Item: The item to render as, may be absent.

    - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")

[![](/images/EntitySprite_firework-rocket.png?cb404)](https://minecraft.wiki/w/Firework_Rocket "Firework Rocket")[**firework\_rocket**](https://minecraft.wiki/w/Firework_Rocket "Firework Rocket")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all projectiles see [Template:Nbt inherit/projectile/template](https://minecraft.wiki/w/Template%3ANbt_inherit/projectile/template "Template:Nbt inherit/projectile/template")
  + [NBT Compound / JSON Object] FireworksItem: The crafted [firework rocket](https://minecraft.wiki/w/Firework_rocket "Firework rocket").

    - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")
  + [Int] Life: The number of ticks this fireworks rocket has been flying for.
  + [Int] LifeTime: The number of ticks before this fireworks rocket explodes. This value is randomized when the firework is launched: ((Flight + 1) \* 10 + random(0 to 5) + random(0 to 6))
  + [Boolean] ShotAtAngle: `1` or `0` (`true`/`false`) - If `true`, this firework was shot from a crossbow or dispenser.

[![](/images/EntitySprite_lingering-potion.png?e894d)](https://minecraft.wiki/w/Lingering_Potion "Lingering Potion")[**lingering\_potion**](https://minecraft.wiki/w/Lingering_Potion "Lingering Potion")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all projectiles see [Template:Nbt inherit/projectile/template](https://minecraft.wiki/w/Template%3ANbt_inherit/projectile/template "Template:Nbt inherit/projectile/template")
  + [NBT Compound / JSON Object] Item: The item to render as.

    - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")

[![](/images/EntitySprite_llama-spit.png?10b82)](https://minecraft.wiki/w/Llama_Spit "Llama Spit")[**llama\_spit**](https://minecraft.wiki/w/Llama_Spit "Llama Spit")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all projectiles see [Template:Nbt inherit/projectile/template](https://minecraft.wiki/w/Template%3ANbt_inherit/projectile/template "Template:Nbt inherit/projectile/template")

[![](/images/EntitySprite_shulker-bullet.png?1b532)](https://minecraft.wiki/w/Shulker "Shulker")[**shulker\_bullet**](https://minecraft.wiki/w/Shulker "Shulker")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all projectiles see [Template:Nbt inherit/projectile/template](https://minecraft.wiki/w/Template%3ANbt_inherit/projectile/template "Template:Nbt inherit/projectile/template")
  + [Int] Steps: How many "steps" it takes to attack to the target. The higher it is, the further out of the way the bullet travels to get to the target. If set to 0, it makes no attempt to attack the target and instead uses TXD/TYD/TZD in a straight line.
  + [Int Array] Target: The [UUID](https://minecraft.wiki/w/UUID "UUID") of the target of this shulker bullet, stored as four ints. Is not preserved when removed.
  + [Double] TXD: The offset in the X direction to travel in accordance with its target. Is not preserved when removed.
  + [Double] TYD: The offset in the Y direction to travel in accordance with its target. Is not preserved when removed.
  + [Double] TZD: The offset in the Z direction to travel in accordance with its target. Is not preserved when removed.

[![](/images/EntitySprite_fireball.png?ffb0c)](https://minecraft.wiki/w/Small_Fireball "Small Fireball")[**small\_fireball**](https://minecraft.wiki/w/Small_Fireball "Small Fireball")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all fireballs see [Template:Nbt inherit/fireball/template](https://minecraft.wiki/w/Template%3ANbt_inherit/fireball/template "Template:Nbt inherit/fireball/template")
  + Tags common to all projectiles see [Template:Nbt inherit/projectile/template](https://minecraft.wiki/w/Template%3ANbt_inherit/projectile/template "Template:Nbt inherit/projectile/template")
  + [NBT Compound / JSON Object] Item: The item to render as, may be absent.

    - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")

[![](/images/EntitySprite_snowball.png?02a86)](https://minecraft.wiki/w/Snowball "Snowball")[**snowball**](https://minecraft.wiki/w/Snowball "Snowball")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all projectiles see [Template:Nbt inherit/projectile/template](https://minecraft.wiki/w/Template%3ANbt_inherit/projectile/template "Template:Nbt inherit/projectile/template")
  + [NBT Compound / JSON Object] Item: The item to render as, may be absent.

    - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")

[![](/images/EntitySprite_spectral-arrow.png?fcc49)](https://minecraft.wiki/w/Spectral_Arrow "Spectral Arrow")[**spectral\_arrow**](https://minecraft.wiki/w/Spectral_Arrow "Spectral Arrow")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all arrows see [Template:Nbt inherit/arrow/template](https://minecraft.wiki/w/Template%3ANbt_inherit/arrow/template "Template:Nbt inherit/arrow/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all projectiles see [Template:Nbt inherit/projectile/template](https://minecraft.wiki/w/Template%3ANbt_inherit/projectile/template "Template:Nbt inherit/projectile/template")
  + [Int] Duration: The time in ticks that the Glowing effect persists.

[![](/images/EntitySprite_splash-potion.png?11164)](https://minecraft.wiki/w/Splash_Potion "Splash Potion")[**splash\_potion**](https://minecraft.wiki/w/Splash_Potion "Splash Potion")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all projectiles see [Template:Nbt inherit/projectile/template](https://minecraft.wiki/w/Template%3ANbt_inherit/projectile/template "Template:Nbt inherit/projectile/template")
  + [NBT Compound / JSON Object] Item: The item to render as.

    - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")

[![](/images/EntitySprite_trident.png?b634b)](https://minecraft.wiki/w/Trident "Trident")[**trident**](https://minecraft.wiki/w/Trident "Trident")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all arrows see [Template:Nbt inherit/arrow/template](https://minecraft.wiki/w/Template%3ANbt_inherit/arrow/template "Template:Nbt inherit/arrow/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all projectiles see [Template:Nbt inherit/projectile/template](https://minecraft.wiki/w/Template%3ANbt_inherit/projectile/template "Template:Nbt inherit/projectile/template")
  + [Boolean] DealtDamage: `1` or `0` (`true`/`false`) - If `true`, the trident has already damaged an entity or been stuck in the ground for more than 4 ticks, in which case subsequent collisions with entities deal no damage and Loyalty tridents begin to return to the player.
  + [NBT Compound / JSON Object] item: The tag representing the item that is given when the entity is picked up.

    - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")

[![](/images/EntitySprite_wind-charge.png?cd158)](https://minecraft.wiki/w/Wind_Charge "Wind Charge")[**wind\_charge**](https://minecraft.wiki/w/Wind_Charge "Wind Charge")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all projectiles see [Template:Nbt inherit/projectile/template](https://minecraft.wiki/w/Template%3ANbt_inherit/projectile/template "Template:Nbt inherit/projectile/template")
  + Tags common to all hurting projectiles see [Template:Nbt inherit/hurting projectile/template](https://minecraft.wiki/w/Template%3ANbt_inherit/hurting_projectile/template "Template:Nbt inherit/hurting projectile/template")

[![](/images/EntitySprite_wither-skull.png?0be34)](https://minecraft.wiki/w/Wither "Wither")[**wither\_skull**](https://minecraft.wiki/w/Wither "Wither")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all fireballs see [Template:Nbt inherit/fireball/template](https://minecraft.wiki/w/Template%3ANbt_inherit/fireball/template "Template:Nbt inherit/fireball/template")
  + Tags common to all projectiles see [Template:Nbt inherit/projectile/template](https://minecraft.wiki/w/Template%3ANbt_inherit/projectile/template "Template:Nbt inherit/projectile/template")
  + [Boolean] dangerous[[note 1]](#cite_note-4): `1` or `0` (`true`/`false`) - If `true`, the wither skull renders as blue, moves more slowly, and ignores the hardness values of most blocks upon exploding.

### Items and XP Orbs


Items and XPOrbs are a subclass of Entity.

[![](/images/EntitySprite_experience-orb.png?7ef2b)](https://minecraft.wiki/w/Experience "Experience")[**experience\_orb**](https://minecraft.wiki/w/Experience "Experience")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + [Short] Age: The number of ticks the XP orb has been "untouched". After 6000 ticks (5 minutes) the orb despawns.
  + [Int] Count: The remaining number of times that the orb can be picked up. When the orb is picked up, the value decreases by 1. When multiple orbs are merged, their values are added up to result orb. When the value reaches 0, the orb is depleted.
  + [Short] Health: The health of XP orbs. XP orbs take damage from fire, lava, falling anvils, and explosions. The orb is destroyed when its health reaches 0.
  + [Short] Value: The amount of experience the orb gives when picked up.

[![](/images/EnvSprite_item.png?89d23)](https://minecraft.wiki/w/Item_%28entity%29 "Item (entity)")[**item**](https://minecraft.wiki/w/Item_%28entity%29 "Item (entity)")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + [Short] Age: The number of ticks the item has been "untouched". After 6000 ticks (5 minutes) the item is destroyed. If set to -32768, the Age does not increase, preventing the item from despawning automatically.
  + [Short] Health: The health of the item, which starts at 5. Items take damage from fire, lava, cacti and explosions. The item is destroyed when its health reaches 0.
  + [NBT Compound / JSON Object] Item: The inventory item, without the Slot tag.

    - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")
  + [Int Array] Owner: If present, only the player with this [UUID](https://minecraft.wiki/w/UUID "UUID") can pick up the item. Used by the [give command](https://minecraft.wiki/w/Commands/give "Commands/give") (and can be set in a summon command) to prevent the wrong player from picking up the spawned item entity. Is not preserved when removed.
  + [Short] PickupDelay: The number of ticks the item cannot be picked up. Decreases by 1 per tick. If set to 32767, the PickupDelay does not decrease, preventing the item from being picked up.
  + [Int Array] Thrower: The [UUID](https://minecraft.wiki/w/UUID "UUID") of the entity who dropped the item. Is not preserved when removed.

### Vehicles


Vehicles are subclasses of Entity.

[![](/images/EntitySprite_all-boats.png?6b19e)](https://minecraft.wiki/w/Boat "Boat")[**boat**](https://minecraft.wiki/w/Boat "Boat")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")

[![](/images/EntitySprite_all-boats-with-chests.png?6b19e)](https://minecraft.wiki/w/Boat_with_Chest "Boat with Chest")[**chest\_boat**](https://minecraft.wiki/w/Boat_with_Chest "Boat with Chest")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all container entities see [Template:Nbt inherit/container entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/container_entity/template "Template:Nbt inherit/container entity/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")

[![](/images/EntitySprite_minecart.png?23526)](https://minecraft.wiki/w/Minecart "Minecart")[**minecart**](https://minecraft.wiki/w/Minecart "Minecart")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all minecarts see [Template:Nbt inherit/vehicle/template](https://minecraft.wiki/w/Template%3ANbt_inherit/vehicle/template "Template:Nbt inherit/vehicle/template")

[![](/images/EntitySprite_minecart-chest.png?fedfd)](https://minecraft.wiki/w/Minecart_with_Chest "Minecart with Chest")[**chest\_minecart**](https://minecraft.wiki/w/Minecart_with_Chest "Minecart with Chest")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all container entities see [Template:Nbt inherit/container entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/container_entity/template "Template:Nbt inherit/container entity/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all minecarts see [Template:Nbt inherit/vehicle/template](https://minecraft.wiki/w/Template%3ANbt_inherit/vehicle/template "Template:Nbt inherit/vehicle/template")

[![](/images/EntitySprite_minecart-command-block.png?fedfd)](https://minecraft.wiki/w/Minecart_with_Command_Block "Minecart with Command Block")[**command\_block\_minecart**](https://minecraft.wiki/w/Minecart_with_Command_Block "Minecart with Command Block")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all minecarts see [Template:Nbt inherit/vehicle/template](https://minecraft.wiki/w/Template%3ANbt_inherit/vehicle/template "Template:Nbt inherit/vehicle/template")
  + [String] Command: The command entered into the minecart.
  + [String] LastOutput: The last line of output generated by the minecart. Still stored even if the [gamerule](https://minecraft.wiki/w/Gamerule "Gamerule") commandBlockOutput is false. Appears in the GUI of the minecart when right-clicked, and includes a timestamp of when the output was produced.
  + [Int] SuccessCount: Represents the strength of the analog signal output by redstone comparators attached to this minecart. Only updated when the minecart is activated with an activator rail.
  + [Boolean] TrackOutput: `1` or `0` (`true`/`false`) - Determines whether the LastOutput is stored. Can be toggled in the GUI by clicking a button near the "Previous Output" textbox. Caption on the button indicates current state: "O" if true,"X" if false.

[![](/images/EntitySprite_minecart-furnace.png?87f22)](https://minecraft.wiki/w/Minecart_with_Furnace "Minecart with Furnace")[**furnace\_minecart**](https://minecraft.wiki/w/Minecart_with_Furnace "Minecart with Furnace")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all minecarts see [Template:Nbt inherit/vehicle/template](https://minecraft.wiki/w/Template%3ANbt_inherit/vehicle/template "Template:Nbt inherit/vehicle/template")
  + [Short] Fuel: The number of ticks until the minecart runs out of fuel.
  + [Double] PushX: Force along X axis, used for smooth acceleration/deceleration.
  + [Double] PushZ: Force along Z axis, used for smooth acceleration/deceleration.

[![](/images/EntitySprite_minecart-hopper.png?e5c66)](https://minecraft.wiki/w/Minecart_with_Hopper "Minecart with Hopper")[**hopper\_minecart**](https://minecraft.wiki/w/Minecart_with_Hopper "Minecart with Hopper")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all container entities see [Template:Nbt inherit/container entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/container_entity/template "Template:Nbt inherit/container entity/template")
  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all minecarts see [Template:Nbt inherit/vehicle/template](https://minecraft.wiki/w/Template%3ANbt_inherit/vehicle/template "Template:Nbt inherit/vehicle/template")
  + [Boolean] Enabled: `1` or `0` (`true`/`false`) - If `true`, the minecart hopper picks up items into its inventory.

[![](/images/EntitySprite_minecart-monster-spawner.png?e5c66)](https://minecraft.wiki/w/Minecart_with_Monster_Spawner "Minecart with Monster Spawner")[**spawner\_minecart**](https://minecraft.wiki/w/Minecart_with_Monster_Spawner "Minecart with Monster Spawner")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all minecarts see [Template:Nbt inherit/vehicle/template](https://minecraft.wiki/w/Template%3ANbt_inherit/vehicle/template "Template:Nbt inherit/vehicle/template")
  + [Short] Delay: Ticks until next spawn. If 0, it spawns immediately when a player enters its range. If set to -1 (this state never occurs in a natural spawner; it seems to be a feature accessed only via NBT editing), the spawner resets this and `SpawnData` as though it had just completed a successful spawn cycle, immediately when a player enters its range. Setting this to -1 can be useful if the player wants the game to properly randomize the spawner's `Delay` and `SpawnData`, rather than starting with pre-defined values.
  + [Short] MaxNearbyEntities: Overrides the maximum number of nearby (within a box of `SpawnRange`\*2+1 × `SpawnRange`\*2+1 × 8 centered around the spawner block) entities whose IDs match this spawner's entity ID. This is relative to a mob's hitbox, not its physical position. Also, all entities within all chunk sections (16×16×16 cubes) overlapped by this box are tested for their ID and hitbox overlap, rather than just entities within the box, meaning that a large amount of entities outside the box (or within it, of course) can cause substantial lag.
  + [Short] MaxSpawnDelay: The maximum random delay for the next spawn delay. Requires the `MinSpawnDelay` and `SpawnCount` properties to also be set.
  + [Short] MinSpawnDelay: The minimum random delay for the next spawn delay. May be equal to `MaxSpawnDelay`. Requires the `SpawnCount` property to also be set, otherwise it defaults to 0.
  + [Short] RequiredPlayerRange: Overrides the block radius of the sphere of activation by players for this spawner. For every gametick, a spawner checks all players in the current world to test whether a player is within this sphere. Requires the `MaxNearbyEntities` property to also be set.
  + [Short] SpawnCount: How many mobs to attempt to spawn each time. Requires the `MinSpawnDelay` property to also be set.
  + [NBT Compound / JSON Object] SpawnData: Contains tags to copy to the *next* spawned entity(s) *after* spawning. *Any* of the entity or mob tags may be used. If a spawner specifies any of these tags, almost all variable data such as mob equipment, villager profession, sheep wool color, etc., are not automatically generated, and must also be manually specified (that this does not apply to position data, which are randomized as normal unless Pos is specified. Similarly, unless Size and Health are specified for a Slime or Magma Cube, these are still randomized). This also determines the appearance of the miniature entity spinning in the spawner cage. **Warning:** If `SpawnPotentials` exists, this tag gets overwritten after the next spawning attempt: see above for more details.
  + [NBT List / JSON Array] SpawnPotentials: Optional. List of possible entities to spawn. If this tag does not exist, but `SpawnData` exists, Minecraft generates it the next time the spawner tries to spawn an entity. The generated list contains a single entry derived from the `SpawnData` tag.
    - [NBT Compound / JSON Object]: A potential future spawn. *After* the spawner makes an attempt at spawning, it chooses one of these entries at random and uses it to prepare for the next spawn, overwriting `SpawnData`.
      * [Int] weight: The chance that this spawn gets picked in comparison to other spawn weights. Must be positive and at least 1.
      * [NBT Compound / JSON Object] data

        + Spawn Data see [Template:Nbt inherit/spawn data/template](https://minecraft.wiki/w/Template%3ANbt_inherit/spawn_data/template "Template:Nbt inherit/spawn data/template")
  + [Short] SpawnRange: The radius around which the spawner attempts to place mobs randomly. The spawn area is square, includes the block the spawner is in, and is centered around the spawner's x,z coordinates - not the spawner itself. It is 2 blocks high, centered around the spawner's y coordinate (its bottom), allowing mobs to spawn as high as its top surface and as low as 1 block below its bottom surface. Vertical spawn coordinates are integers, while horizontal coordinates are floating point and weighted toward values near the spawner itself. Default value is 4.

[![](/images/EntitySprite_minecart-tnt.png?26bb0)](https://minecraft.wiki/w/Minecart_with_TNT "Minecart with TNT")[**tnt\_minecart**](https://minecraft.wiki/w/Minecart_with_TNT "Minecart with TNT")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all minecarts see [Template:Nbt inherit/vehicle/template](https://minecraft.wiki/w/Template%3ANbt_inherit/vehicle/template "Template:Nbt inherit/vehicle/template")
  + [Int] fuse: Time until explosion or -1 if not activated.
  + [Float] explosion\_power: A value from 0 to 128. Additional [explosion power](https://minecraft.wiki/w/Explosion#Block_destruction "Explosion"), which is added to the speed-based explosion power. Defaults to 4.0. If set to the default value, this field is not saved to the entity's NBT.
  + [Float] explosion\_speed\_factor: Controls the amount of added damage depending on the speed of the Minecart. Defaults to 1.0. If set to the default value, this field is not saved to the entity's NBT.

### Dynamic tiles


Dynamic tiles are a subclass of Entity and are used to simulate realistically moving blocks.

[![](/images/EntitySprite_all-falling-blocks.png?2d297)](https://minecraft.wiki/w/Falling_Block "Falling Block")[**falling\_block**](https://minecraft.wiki/w/Falling_Block "Falling Block")

* [NBT Compound / JSON Object] Dynamic block entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + [NBT Compound / JSON Object] BlockState: The falling block represented by this entity.

    - Block state see [Template:Nbt inherit/block state/template](https://minecraft.wiki/w/Template%3ANbt_inherit/block_state/template "Template:Nbt inherit/block state/template")
  + [NBT Compound / JSON Object] TileEntityData: Optional. The tags of the block entity for this block.

    - Tags common to all block entities see [Template:Nbt inherit/blockentity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/blockentity/template "Template:Nbt inherit/blockentity/template")
  + [Byte] CancelDrop: 1 or 0 (true/false) - true if the block should be destroyed instead of placed after landing on a solid block. When true, the block is not dropped as an item, even if the `DropItem` tag is set to true. However, if the entity is deleted due to its `Time` value being too high, this tag is ignored and an item is dropped depending on the `DropItem` tag. `CancelDrop` defaults to 1 for falling [suspicious sand](https://minecraft.wiki/w/Suspicious_sand "Suspicious sand") and [suspicious gravel](https://minecraft.wiki/w/Suspicious_gravel "Suspicious gravel"), and 0 for the other vanilla falling blocks and any summoned falling block.
  + [Byte] DropItem: 1 or 0 (true/false) – true if the block should drop as an item when it breaks. Any block that does not have an item form *with the same ID as the block* does not drop even if this is set.
  + [Float] FallHurtAmount: Multiplied by the `FallDistance` to calculate the amount of damage to inflict. By default this value is 2HP![❤️](/images/Heart_%28icon%29.png?faf83) for anvils, and 6HP![❤️](/images/Heart_%28icon%29.png?faf83)![❤️](/images/Heart_%28icon%29.png?faf83)![❤️](/images/Heart_%28icon%29.png?faf83) for pointed dripstone.
  + [Int] FallHurtMax: The maximum hit points of damage to inflict on entities that intersect this falling block. For vanilla falling blocks, always 40HP![❤️](/images/Heart_%28icon%29.png?faf83) × 20.
  + [Byte] HurtEntities: 1 or 0 (true/false) – true if the block should hurt entities it falls on. Defaults to 1 for [anvils](https://minecraft.wiki/w/Anvil "Anvil") and [pointed dripstone](https://minecraft.wiki/w/Pointed_Dripstone "Pointed Dripstone") and to 0 for the other vanilla falling blocks and any summoned falling block.
  + [Int] Time: The number of ticks the entity has existed. When `Time` goes above 600, or above 100 while the block is at Y=-64 or is outside building height, the entity is deleted.

[![](/images/EntitySprite_primed-tnt.png?5d12c)](https://minecraft.wiki/w/TNT "TNT")[**tnt**](https://minecraft.wiki/w/TNT "TNT")

* [NBT Compound / JSON Object] Dynamic block entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + [Short] fuse: Ticks until explosion. Defaults to 80.
  + [NBT Compound / JSON Object] block\_state: The block model to use. defaults to tnt if not specified.
    - [String] Name: The [resource location](https://minecraft.wiki/w/Resource_location "Resource location") of the block.
    - [NBT Compound / JSON Object] Properties: Optional. The [block states](https://minecraft.wiki/w/Block_states "Block states") of the block.
      * [String] *Name*: The block state name and its value.
  + [Float] explosion\_power: A value from 0 to 128. The [power](https://minecraft.wiki/w/Explosion#Block_destruction "Explosion") of the explosion. Defaults to 4.0. If set to the default value, this field is not saved to the entity's NBT.
  + [Int Array] owner: The [UUID](https://minecraft.wiki/w/UUID "UUID") of the entity this TNT was lit by, stored as four ints. May not exist.

### Display


Display entities are subclasses of Entity.

[![](/images/BlockSprite_air.png?037f8)](https://minecraft.wiki/w/Display "Display")[**block\_display**](https://minecraft.wiki/w/Display "Display")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all display entities see [Template:Nbt inherit/display entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/display_entity/template "Template:Nbt inherit/display entity/template")
  + [NBT Compound / JSON Object] block\_state: The block state to display.

    - Block state see [Template:Nbt inherit/block state/template](https://minecraft.wiki/w/Template%3ANbt_inherit/block_state/template "Template:Nbt inherit/block state/template")

[![](/images/BlockSprite_air.png?037f8)](https://minecraft.wiki/w/Display "Display")[**item\_display**](https://minecraft.wiki/w/Display "Display")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all display entities see [Template:Nbt inherit/display entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/display_entity/template "Template:Nbt inherit/display entity/template")
  + [NBT Compound / JSON Object] item: The item to display.

    - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")
  + [String] item\_display: The model to display. Describes item model transform applied to item (as defined in `display` field in [model](https://minecraft.wiki/w/Model "Model") JSON). Can be `none`, `thirdperson_lefthand`, `thirdperson_righthand`, `firstperson_lefthand`, `firstperson_righthand`, `head`, `gui`, `ground`, and `fixed`.[*[verify](https://minecraft.wiki/w/Special%3ATalkPage/Entity_format "Special:TalkPage/Entity format")*] Defaults to `none`.

[![](/images/BlockSprite_air.png?037f8)](https://minecraft.wiki/w/Display "Display")[**text\_display**](https://minecraft.wiki/w/Display "Display")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all display entities see [Template:Nbt inherit/display entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/display_entity/template "Template:Nbt inherit/display entity/template")
  + [String] alignment: Text alignment direction. Can be `center`, `left`, and `right`. Defaults to `center`.
  + [Int] background: The background color, arranged by ARGB. Since pixels with an alpha channel less than 0.1 are discarded when rendering in vanilla [shader](https://minecraft.wiki/w/Shader "Shader"), the background becomes fully transparent when A is less than 26 (0x1A). Defaults to 1073741824 (0x40000000). Interpolated.
  + [Boolean] default\_background: If true, rendering uses default text background color (same as in chat), which overrides [Int] background. Defaults to `false`.
  + [Int] line\_width: Maximum line width used to split lines (note: new line can be also added with `\n` characters). Defaults to 200.
  + [Boolean] see\_through: Whether the text is visible through blocks. Defaults to `false`.
  + [Boolean] shadow: Whether the text is displayed with shadow. Defaults to `false`.
  + [String] text: The text to be displayed in the format of [raw JSON text](https://minecraft.wiki/w/Raw_JSON_text "Raw JSON text"), which are resolved with the context of the display entity.
  + [Byte] text\_opacity: Alpha value of rendered text. Value ranges from 0 to 255. Values up to 3 are treated as fully opaque (255). Similar to the background, the text rendering is discarded for values between 4 and 26. NBT stores the value as signed byte, -128 to 127. Defaults to -1, which represents 255 and is completely opaque. SNBT to NBT handles conversion from unsigned to signed, but if needed, replace values greater than 127 with `alpha-256` or `alphaUB`. Interpolated.

### Other


Other entity types that are a subclass of Entity but do not fit into any of the above categories.

[![](/images/EntitySprite_area-effect-cloud.png?f4c3c)](https://minecraft.wiki/w/Lingering_Potion "Lingering Potion")[**area\_effect\_cloud**](https://minecraft.wiki/w/Lingering_Potion "Lingering Potion")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + [Int] Age: Age of the field. Increases by 1 every tick. When this is bigger than `Duration` + `WaitTime` the area effect cloud dissipates.
  + [Int] Color: The color of the displayed particle. Uses the same format as the **color** tag from [Display Properties](https://minecraft.wiki/w/Player.dat_format#Display_Properties "Player.dat format").
  + [Int] Duration: The maximum age of the field after `WaitTime`.
  + [Int] DurationOnUse: The amount the duration of the field changes upon applying the effect.
  + [String][NBT Compound / JSON Object] potion\_contents: The potion and custom effects contained in this area effect cloud. Represents the [`minecraft:potion_contents`](https://minecraft.wiki/w/Data_component_format#potion_contents "Data component format") component. If set to a string, it is converted to a compound, with the string corresponding to [String] potion.

    - A custom potion contents object see [Template:Nbt inherit/potion\_contents/template](https://minecraft.wiki/w/Template%3ANbt_inherit/potion_contents/template "Template:Nbt inherit/potion contents/template")
  + [Int Array] Owner: The [UUID](https://minecraft.wiki/w/UUID "UUID") of the entity who created the cloud, stored as four ints. Is not preserved when removed.
  + [NBT Compound / JSON Object] custom\_particle: The [particle](https://minecraft.wiki/w/Particle "Particle") displayed by the field.
    - [String] type: The id of the particle type, see [Particles (Java Edition)](https://minecraft.wiki/w/Particles_%28Java_Edition%29 "Particles (Java Edition)") for valid options.
    - Additional fields based on the type, see [Particle format](https://minecraft.wiki/w/Particle_format#Configurations_of_particle_types "Particle format").
  + [Float] potion\_duration\_scale: The duration of the potion effect applied is scaled by this factor. (defaults to 1.0). Area Effect Clouds created by Lingering Potions will have a scale of 0.25. Represents the [`minecraft:potion_duration_scale`](https://minecraft.wiki/w/Data_component_format#potion_duration_scale "Data component format") component.
  + [Float] Radius: The field's radius.
  + [Float] RadiusOnUse: The amount the radius changes upon applying the effect. Normally negative.
  + [Float] RadiusPerTick: The amount the radius changes per tick. Normally negative.
  + [Int] ReapplicationDelay: The number of ticks before reapplying the effect.
  + [Int] WaitTime: The time before deploying the field. The `Radius` is ignored, meaning that any specified effects is not applied and specified particles appear only at the center of the field, until `Age` hits this number.

[![](/images/EntitySprite_end-crystal.png?139be)](https://minecraft.wiki/w/End_Crystal "End Crystal")[**end\_crystal**](https://minecraft.wiki/w/End_Crystal "End Crystal")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + [Int Array] beam\_target: The block location, as 3 integers, that its beam points to.
  + [Byte] ShowBottom: 1 or 0 (true/false) – if true, the end crystal shows the bedrock slate underneath. Defaults to false when placing by hand, and true when naturally generated or using `/[summon](https://minecraft.wiki/w/Commands/summon "Commands/summon")`.

[![](/images/EntitySprite_evoker-fangs.png?f48c2)](https://minecraft.wiki/w/Evoker "Evoker")[**evoker\_fangs**](https://minecraft.wiki/w/Evoker "Evoker")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + [Int Array] Owner: The [UUID](https://minecraft.wiki/w/UUID "UUID") of the entity that that fired the fangs, stored as four ints. If the entity is an [Illager](https://minecraft.wiki/w/Illager "Illager"), the fangs do not damage other Illagers. Is not preserved when removed.
  + [Int] Warmup: Time in ticks until the fangs appear. The fangs appear and begin to close as soon as this value becomes zero or less; negative values simply result in no delay. The value continues ticking down while the closing animation is playing, reaching -20 on naturally spawned fangs.

[![](/images/EntitySprite_eye-of-ender.png?57d43)](https://minecraft.wiki/w/Eye_of_Ender "Eye of Ender")[**eye\_of\_ender**](https://minecraft.wiki/w/Eye_of_Ender "Eye of Ender")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + [NBT Compound / JSON Object] Item: The item to render as, may be absent.

    - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")

[![](/images/EntitySprite_fishing-bobber.png?26df9)](https://minecraft.wiki/w/Fishing_Rod "Fishing Rod")[**fishing\_bobber**](https://minecraft.wiki/w/Fishing_Rod "Fishing Rod")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")

[![](/images/EntitySprite_empty-glow-item-frame.png?e240d)](https://minecraft.wiki/w/Glow_Item_Frame "Glow Item Frame")[**glow\_item\_frame**](https://minecraft.wiki/w/Glow_Item_Frame "Glow Item Frame")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all block entities that can hang from blocks see [Template:Nbt inherit/hangable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/hangable/template "Template:Nbt inherit/hangable/template")
  + [Boolean] Fixed: `1`, or `0` (`true`/`false`) - If `true`: the item frame does not drop when it has no support block, it can not be moved by pistons, and it won't take damage (except from creative players). An item cannot be placed in or removed from a fixed item frame. The item in a fixed item frame (if any) can not be rotated.
  + [Boolean] Invisible: `1`, or `0` (`true`/`false`) - Whether the item frame (background) is invisible. An item or map inside an invisible item frame is still visible.
  + [NBT Compound / JSON Object] Item: The item in the item frame (no slot tag). If the item frame is empty, this tag does not exist.

    - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")
  + [Float] ItemDropChance: The chance for the item to drop when the item frame breaks. This is a 100% chance by default.
  + [Byte] ItemRotation: The current angle or rotation of the item, as a multiple of 45 degrees, going clockwise. `0` means the item is upright, `1` means the item is turned 45 degrees clockwise from the upright orientation. This value can only ever be between `0` and `7`, just like its redstone output when measured with a [comparator](https://minecraft.wiki/w/Comparator "Comparator").

[![](/images/BlockSprite_air.png?037f8)](https://minecraft.wiki/w/Interaction "Interaction")[**interaction**](https://minecraft.wiki/w/Interaction "Interaction")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + [Float] width: The width of the entity's bounding box. Defaults to 1.
  + [Float] height: The height of the entity's bounding box. Defaults to 1.
  + [Byte] response: 1 or 0 (true/false). Specifies whether an interaction should trigger a response (hand animation). Defaults to 0 (false).
  + [NBT Compound / JSON Object] attack: The last attack (left click) to hit the entity.
    - [Int Array] player: The UUID of the player that attacked the entity. The 128-bit UUID is stored as four 32-bit integers, ordered from most to least significant.
    - [Long] timestamp: When the attack took place.
  + [NBT Compound / JSON Object] interaction: The last interaction (right click) to hit the entity.
    - [Int Array] player: The UUID of the player that interacted with the entity. The 128-bit UUID is stored as four 32-bit integers, ordered from most to least significant.
    - [Long] timestamp: When the interaction took place.

[![](/images/EntitySprite_empty-item-frame.png?22742)](https://minecraft.wiki/w/Item_Frame "Item Frame")[**item\_frame**](https://minecraft.wiki/w/Item_Frame "Item Frame")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all block entities that can hang from blocks see [Template:Nbt inherit/hangable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/hangable/template "Template:Nbt inherit/hangable/template")
  + [Boolean] Fixed: `1`, or `0` (`true`/`false`) - If `true`: the item frame does not drop when it has no support block, it can not be moved by pistons, and it won't take damage (except from creative players). An item cannot be placed in or removed from a fixed item frame. The item in a fixed item frame (if any) can not be rotated.
  + [Boolean] Invisible: `1`, or `0` (`true`/`false`) - Whether the item frame (background) is invisible. An item or map inside an invisible item frame is still visible.
  + [NBT Compound / JSON Object] Item: The item in the item frame (no slot tag). If the item frame is empty, this tag does not exist.

    - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")
  + [Float] ItemDropChance: The chance for the item to drop when the item frame breaks. This is a 100% chance by default.
  + [Byte] ItemRotation: The current angle or rotation of the item, as a multiple of 45 degrees, going clockwise. `0` means the item is upright, `1` means the item is turned 45 degrees clockwise from the upright orientation. This value can only ever be between `0` and `7`, just like its redstone output when measured with a [comparator](https://minecraft.wiki/w/Comparator "Comparator").

[![](/images/EntitySprite_leash-knot.png?2d6a1)](https://minecraft.wiki/w/Lead "Lead")[**leash\_knot**](https://minecraft.wiki/w/Lead "Lead")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")

[![](/images/EntitySprite_lightning.png?8359f)](https://minecraft.wiki/w/Thunderstorm "Thunderstorm")[**lightning\_bolt**](https://minecraft.wiki/w/Thunderstorm "Thunderstorm")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")

[![](/images/BlockSprite_air.png?037f8)](https://minecraft.wiki/w/Marker "Marker")[**marker**](https://minecraft.wiki/w/Marker "Marker")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")

[![](/images/EntitySprite_ominous-item-spawner.png?fb527)](https://minecraft.wiki/w/Ominous_Item_Spawner "Ominous Item Spawner")[**ominous\_item\_spawner**](https://minecraft.wiki/w/Ominous_Item_Spawner "Ominous Item Spawner")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + [NBT Compound / JSON Object] item: The item to display and dispense.

    - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")
  + [Long] spawn\_item\_after\_ticks: Total time in ticks to display the item, before dispensing it.

[![](/images/EntitySprite_kebab.png?c74c1)](https://minecraft.wiki/w/Painting "Painting")[**painting**](https://minecraft.wiki/w/Painting "Painting")

* [NBT Compound / JSON Object] Entity data

  + Tags common to all entities see [Template:Nbt inherit/entity/template](https://minecraft.wiki/w/Template%3ANbt_inherit/entity/template "Template:Nbt inherit/entity/template")
  + Tags common to all block entities that can hang from blocks see [Template:Nbt inherit/hangable/template](https://minecraft.wiki/w/Template%3ANbt_inherit/hangable/template "Template:Nbt inherit/hangable/template")
  + **except for** the tag: `Facing`
  + [Byte] facing: The direction the painting faces: 0 is south, 1 is west, 2 is north, 3 is east
  + [String] variant: One [painting variant](https://minecraft.wiki/w/Painting_variant_definition "Painting variant definition") (an [String] [ID](https://minecraft.wiki/w/Resource_location "Resource location")). Represents the [`minecraft:painting/variant`](https://minecraft.wiki/w/Data_component_format#painting/variant "Data component format") component.

## History


| [*Java Edition*](https://minecraft.wiki/w/Java_Edition_version_history "Java Edition version history") | | | | | | | |
| --- | --- | --- | --- | --- | --- | --- | --- |
| [1.4.2](https://minecraft.wiki/w/Java_Edition_1.4.2 "Java Edition 1.4.2") | | | [1.4.1](https://minecraft.wiki/w/Java_Edition_1.4.1 "Java Edition 1.4.1") | | | | Added `PersistenceRequired`. |
| [1.9](https://minecraft.wiki/w/Java_Edition_1.9 "Java Edition 1.9") | | | [15w31a](https://minecraft.wiki/w/Java_Edition_15w31a "Java Edition 15w31a") | | | | Added tags `HandItems`, `ArmorItems`, `HandDropChances`, and `ArmorDropChances` to `Living`. |
| The Tag `Equipment` (under `Living`) has become deprecated. |
| The Tag `DropChances` (under `Living`) has become deprecated. |
| [1.17](https://minecraft.wiki/w/Java_Edition_1.17 "Java Edition 1.17") | | | [20w45a](https://minecraft.wiki/w/Java_Edition_20w45a "Java Edition 20w45a") | | | | Entities have been extracted from main (terrain) chunks and are now stored in separate entities directory (similar to [POI storage](https://minecraft.wiki/w/Point_of_Interest_format "Point of Interest format")). Those new files are still region files with NBT. |
| [1.19](https://minecraft.wiki/w/Java_Edition_1.19 "Java Edition 1.19") | | | [22w11a](https://minecraft.wiki/w/Java_Edition_22w11a "Java Edition 22w11a") | | | | The `Id` tag for each effect in a mob's `ActiveEffects` tag is now a [Int] TAG\_Integer instead of a [Byte] TAG\_Byte. |
| [1.20.2](https://minecraft.wiki/w/Java_Edition_1.20.2 "Java Edition 1.20.2") | | | [23w32a](https://minecraft.wiki/w/Java_Edition_23w32a "Java Edition 23w32a") | | | | In NBT format for entity type `mooshroom`, removed `EffectId` and `EffectDuration`, and added `stew_effects`, with the same format as `effects` field in `suspicious_stew` item format. |
| In NBT format for entity type `area_effect_cloud`, renamed `Effects` to `effects`. |
| In NBT format for entity type `arrow`, renamed `CustomPotionEffects` to `custom_potion_effects`. |
| In NBT format for living entities (players, armor stands, and all mobs), renamed `ActiveEffects` to `active_effects`, and inside that renamed `Ambient` to `ambient`, `Amplifier` to `amplifier`, `Duration` to `duration`, `HiddenEffect` to `hidden_effect`, `Id` to `id`, `ShowIcon` to `show_icon`, `ShowParticles` to `show_particles`, and changed `id` from a [Int] TAG\_Integer to a [String] TAG\_String. |
| [1.20.3](https://minecraft.wiki/w/Java_Edition_1.20.3 "Java Edition 1.20.3") | | | [23w42a](https://minecraft.wiki/w/Java_Edition_23w42a "Java Edition 23w42a") | | | | In NBT format for entity type `tnt`, added `block_state`, and renamed `Fuse` to `fuse`. |
| [23w43a](https://minecraft.wiki/w/Java_Edition_23w43a "Java Edition 23w43a") | | | | In NBT format for entity type `arrow` and `spectral_arrow`, added `item`. |
| In NBT format for entity type `trident`, renamed `Trident` to `item`. |
| [1.20.5](https://minecraft.wiki/w/Java_Edition_1.20.5 "Java Edition 1.20.5") | | | [23w51a](https://minecraft.wiki/w/Java_Edition_23w51a "Java Edition 23w51a") | | | | Added [Byte] armor tag in [wolf](https://minecraft.wiki/w/Wolf "Wolf") to denote whether a wolf is wearing [wolf armor](https://minecraft.wiki/w/Wolf_armor "Wolf armor"). |
| [24w05a](https://minecraft.wiki/w/Java_Edition_24w05a "Java Edition 24w05a") | | | | Replaced [NBT Compound / JSON Object] ArmorItem tag in [horse](https://minecraft.wiki/w/Horse "Horse") with [NBT Compound / JSON Object] body\_armor\_item. |
| Replaced [NBT Compound / JSON Object] DecorItem tag in [llama](https://minecraft.wiki/w/Llama "Llama") with [NBT Compound / JSON Object] body\_armor\_item. |
| Replaced [Byte] armor tag in [wolf](https://minecraft.wiki/w/Wolf "Wolf") with [NBT Compound / JSON Object] body\_armor\_item. |
| [24w06a](https://minecraft.wiki/w/Java_Edition_24w06a "Java Edition 24w06a") | | | | All block positions are now stored as an array of 3 integers instead of a map of X, Y, and Z. |
| `Leash` in all leashable entities has been renamed to `leash`. |
| `PatrolTarget` in patrolling mobs has been renamed to `patrol_target`. |
| [1.21.4](https://minecraft.wiki/w/Java_Edition_1.21.4 "Java Edition 1.21.4") | | | [24w44a](https://minecraft.wiki/w/Java_Edition_24w44a "Java Edition 24w44a") | | | | In NBT format for entity type `tnt_minecart`, added optional field `explosion_speed_factor`. |
| The `TNTFuse` field of minecarts with TNT has been renamed to `fuse`. |
| [1.21.5](https://minecraft.wiki/w/Java_Edition_1.21.5 "Java Edition 1.21.5") | | | [25w02a](https://minecraft.wiki/w/Java_Edition_25w02a "Java Edition 25w02a") | | | | The [NBT Compound / JSON Object] ArmorDropChances, [NBT Compound / JSON Object] HandDropChances, and [NBT Compound / JSON Object] body\_armor\_drop\_chance fields have been merged into a [NBT Compound / JSON Object] drop\_chances field. |
| Drop chances with a default value will no longer be stored, and the [NBT Compound / JSON Object] drop\_chances field is removed entirely if all defaults. |
| Area effect clouds have a new field: [Float] potion\_duration\_scale. |
| [25w03a](https://minecraft.wiki/w/Java_Edition_25w03a "Java Edition 25w03a") | | | | The [NBT Compound / JSON Object] ArmorItems, [NBT Compound / JSON Object] HandItems, and [NBT Compound / JSON Object] body\_armor\_item fields have been merged into an [NBT Compound / JSON Object] equipment field. |
| [25w07a](https://minecraft.wiki/w/Java_Edition_25w07a "Java Edition 25w07a") | | | | `Pos`, `Motion`, and `Rotation` values without the correct number of components (3, 3, and 2 respectively) will now be fully discarded, instead of only selecting the specified components. |
| The [Int] SleepingX, [Int] SleepingY, and [Int] SleepingZ fields have been collected into a single [Int Array] sleeping\_pos field |
| [25w09a](https://minecraft.wiki/w/Java_Edition_25w09a "Java Edition 25w09a") | | | | The `FallFlying` field will no longer be preserved if removed. |
| The `Health` and `Air` fields now default to their respective maximum value if not specified. |
| [25w10a](https://minecraft.wiki/w/Java_Edition_25w10a "Java Edition 25w10a") | | | | Custom data (previously present only on [markers](https://minecraft.wiki/w/Marker "Marker")) is now available on all entities. |
| [1.21.6](https://minecraft.wiki/w/Java_Edition_1.21.6 "Java Edition 1.21.6") | | | [25w15a](https://minecraft.wiki/w/Java_Edition_25w15a "Java Edition 25w15a") | | | | `area_effect_cloud`: the `Particle` field has been renamed to `custom_particle`, and now always functions as an exact override for the default colored `entity_effect` particle. |
| [25w18a](https://minecraft.wiki/w/Java_Edition_25w18a "Java Edition 25w18a") | | | | Added `home_pos` and `home_radius` fields to all mobs. |
| [25w19a](https://minecraft.wiki/w/Java_Edition_25w19a "Java Edition 25w19a") | | | | `tnt`: The entity that primed the TNT is now stored in an optional `owner` field (UUID of Living entity). |
| `vex`: The owner of a vex is now stored in an optional `owner` field (UUID of Mob). |
| [1.21.9](https://minecraft.wiki/w/Java_Edition_1.21.9 "Java Edition 1.21.9") | | | [25w32a](https://minecraft.wiki/w/Java_Edition_25w32a "Java Edition 25w32a") | | | | `copper_golem`: The `weather_state` field now expects a string id instead of integer id.. |
| [pre1](https://minecraft.wiki/w/Java_Edition_1.21.9-pre1 "Java Edition 1.21.9-pre1") | | | | `minecraft:player` has received several changes to the `respawn` object. |
| [1.21.11](https://minecraft.wiki/w/Java_Edition_1.21.11 "Java Edition 1.21.11") | | | [25w41a](https://minecraft.wiki/w/Java_Edition_25w41a "Java Edition 25w41a") | | | | The `AngryAt` field has been renamed to `angry_at`. |
| The `AngerTime` field has been removed. |
| An `anger_end_time` (long) field has been added, containing the time anger ends in game ticks. |
| [26.1](https://minecraft.wiki/w/Java_Edition_26.1 "Java Edition 26.1") | | | [snap2](https://minecraft.wiki/w/Java_Edition_26.1_Snapshot_2 "Java Edition 26.1 Snapshot 2") | | | | The `current_explosion_impact_pos` and `current_impulse_context_reset_grace_time` fields from players have been added to all mobs and the [armor stand](https://minecraft.wiki/w/Armor_stand "Armor stand"). |
| The `ignore_fall_damage_from_current_explosion` field on players has been removed. |

## References


1. [↑](#cite_ref-1) [MC-279832](https://bugs.mojang.com/browse/MC-279832 "mojira:MC-279832") – resolved as "Works As Intended".
2. [↑](#cite_ref-3) [MC-81656](https://bugs.mojang.com/browse/MC-81656 "mojira:MC-81656")

1. [↑](#cite_ref-4) Although blue wither skulls have existed since [12w37a](https://minecraft.wiki/w/Java_Edition_12w37a "Java Edition 12w37a"), this field was not present until [23w41a](https://minecraft.wiki/w/Java_Edition_23w41a "Java Edition 23w41a").[[2]](#cite_note-3)

## Navigation


| * [v](https://minecraft.wiki/w/Template%3ANavbox_Java_Edition_technical "Template:Navbox Java Edition technical") * [t](https://minecraft.wiki/w/Special%3ATalkPage/Template%3ANavbox_Java_Edition_technical "Special:TalkPage/Template:Navbox Java Edition technical") * [e](https://minecraft.wiki/w/Special%3AEditPage/Template%3ANavbox_Java_Edition_technical "Special:EditPage/Template:Navbox Java Edition technical") *[Java Edition](https://minecraft.wiki/w/Java_Edition "Java Edition")* technical | |
| --- | --- |
| | General | | | --- | --- | | Concepts | * [![](/images/BlockSprite_chest.png?15d81)](https://minecraft.wiki/w/Block_entity "Block entity")[Block entity](https://minecraft.wiki/w/Block_entity "Block entity") * [![](/images/EnvSprite_map.png?b863e)](https://minecraft.wiki/w/Coordinates "Coordinates")[Coordinates](https://minecraft.wiki/w/Coordinates "Coordinates") * [![](/images/EffectSprite_infested.png?4562a)](https://minecraft.wiki/w/Crash "Crash")[Crashes](https://minecraft.wiki/w/Crash "Crash") * [String] [Loot context](https://minecraft.wiki/w/Loot_context "Loot context") * [![](/images/EntitySprite_cow.png?893cf)](https://minecraft.wiki/w/Mob_AI "Mob AI")[Mob AI](https://minecraft.wiki/w/Mob_AI "Mob AI") * [![](/images/BlockSprite_lodestone.png?00f1a)](https://minecraft.wiki/w/Point_of_Interest "Point of Interest")[Point of Interest](https://minecraft.wiki/w/Point_of_Interest "Point of Interest") * ![File directory.png: Sprite image for directory in Minecraft](/images/thumb/File_directory.png/16px-File_directory.png?8a409) [Identifier](https://minecraft.wiki/w/Identifier "Identifier") * [![](/images/BlockSprite_camera.png?7ee99)](https://minecraft.wiki/w/Screenshot "Screenshot")[Screenshot](https://minecraft.wiki/w/Screenshot "Screenshot") * [![](/images/EnvSprite_scoreboard.png?38feb)](https://minecraft.wiki/w/Statistics "Statistics")[Statistics](https://minecraft.wiki/w/Statistics "Statistics") * [![](/images/ItemSprite_book.png?791a5)](https://minecraft.wiki/w/Telemetry "Telemetry")[Telemetry](https://minecraft.wiki/w/Telemetry "Telemetry") * [![](/images/ItemSprite_clock.png?30324)](https://minecraft.wiki/w/Tick "Tick")[Tick](https://minecraft.wiki/w/Tick "Tick") * [![](/images/ItemSprite_wheat-seeds.png?b83e5)](https://minecraft.wiki/w/Random_Tick "Random Tick")[Random Tick](https://minecraft.wiki/w/Random_Tick "Random Tick") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/UUID "UUID")[UUID](https://minecraft.wiki/w/UUID "UUID") * [![](/images/BlockSprite_computer.png?e0c37)](https://minecraft.wiki/w/JSON "JSON")[JSON](https://minecraft.wiki/w/JSON "JSON") | | [General format](https://minecraft.wiki/w/Development_resources "Development resources") | * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Java_Edition_data_values "Java Edition data values")[Data values](https://minecraft.wiki/w/Java_Edition_data_values "Java Edition data values")   + [![](/images/LegacyBlockSprite_bricks-je1.png?9a58b)](https://minecraft.wiki/w/Java_Edition_Classic_data_values "Java Edition Classic data values")[Classic](https://minecraft.wiki/w/Java_Edition_Classic_data_values "Java Edition Classic data values")     - [Remake](https://minecraft.wiki/w/Classic_remake_data_values "Classic remake data values")   + [![](/images/EntitySprite_rana.png?3f2f9)](https://minecraft.wiki/w/Java_Edition_Indev_data_values "Java Edition Indev data values")[Indev](https://minecraft.wiki/w/Java_Edition_Indev_data_values "Java Edition Indev data values")   + [![](/images/BlockSprite_stone.png?e9a91)](https://minecraft.wiki/w/Java_Edition_pre-flattening_data_values "Java Edition pre-flattening data values")[Pre-flattening](https://minecraft.wiki/w/Java_Edition_pre-flattening_data_values "Java Edition pre-flattening data values") * [![](/images/EnvSprite_item.png?89d23)](https://minecraft.wiki/w/Data_component_format "Data component format")[Data component format](https://minecraft.wiki/w/Data_component_format "Data component format")   + [![](/images/BlockSprite_test-block-start.png?35191)](https://minecraft.wiki/w/Data_component_predicate "Data component predicate")[Predicate](https://minecraft.wiki/w/Data_component_predicate "Data component predicate") * [![](/images/EnvSprite_entities.png?94711)](https://minecraft.wiki/w/Entity_format "Entity format")Entity format * [![](/images/BlockSprite_chest.png?15d81)](https://minecraft.wiki/w/Block_entity_format "Block entity format")[Block entity format](https://minecraft.wiki/w/Block_entity_format "Block entity format") * [![](/images/ItemSprite_map.png?05f8c)](https://minecraft.wiki/w/Map_item_format "Map item format")[Map item format](https://minecraft.wiki/w/Map_item_format "Map item format") * [NBT Compound / JSON Object] [NBT format](https://minecraft.wiki/w/NBT_format "NBT format") * [![](/images/EffectSprite_particle-healing.png?1357a)](https://minecraft.wiki/w/Particle_format "Particle format")[Particle format](https://minecraft.wiki/w/Particle_format "Particle format") * [![](/images/ItemSprite_book-and-quill.png?f190b)](https://minecraft.wiki/w/Text_component_format "Text component format")[Text component format](https://minecraft.wiki/w/Text_component_format "Text component format") * [§](https://minecraft.wiki/w/Formatting_codes "Formatting codes") [Formatting codes](https://minecraft.wiki/w/Formatting_codes "Formatting codes") * [![](/images/thumb/Movement_hint.png/16px-Movement_hint.png?92667)](https://minecraft.wiki/w/Key_codes "Key codes")[Key codes](https://minecraft.wiki/w/Key_codes "Key codes") * [![](/images/thumb/Dice.png/14px-Dice.png?a4e84)](https://minecraft.wiki/w/Random_sequence_format "Random sequence format")[Random sequence](https://minecraft.wiki/w/Random_sequence_format "Random sequence format") * [![](/images/BlockSprite_structure-block.png?381fc)](https://minecraft.wiki/w/Structure_file "Structure file")[Structure file format](https://minecraft.wiki/w/Structure_file "Structure file")   + [![](/images/EnvSprite_chunk.png?b2cf1)](https://minecraft.wiki/w/Schematic_file_format "Schematic file format")[Schematic file format](https://minecraft.wiki/w/Schematic_file_format "Schematic file format") | | [World](https://minecraft.wiki/w/World "World") | * [![](/images/EnvSprite_altitude.png?9b274)](https://minecraft.wiki/w/Heightmap "Heightmap")[Heightmap](https://minecraft.wiki/w/Heightmap "Heightmap") * [![](/images/EnvSprite_mountain.png?2e0ae)](https://minecraft.wiki/w/World_seed "World seed")[Seed](https://minecraft.wiki/w/World_seed "World seed")   + [Anomalous](https://minecraft.wiki/w/Anomalous_world_seeds "Anomalous world seeds") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Data_version "Data version")[Data version](https://minecraft.wiki/w/Data_version "Data version")  |  |  | | --- | --- | | Legacy | * [![](/images/EnvSprite_chunk.png?b2cf1)](https://minecraft.wiki/w/Spawn_chunk "Spawn chunk")[Spawn chunk](https://minecraft.wiki/w/Spawn_chunk "Spawn chunk") | | [Level format](https://minecraft.wiki/w/Java_Edition_level_format "Java Edition level format") | * [![](/images/BlockSprite_anvil.png?a26c9)](https://minecraft.wiki/w/Anvil_file_format "Anvil file format")[Anvil file format](https://minecraft.wiki/w/Anvil_file_format "Anvil file format") * [![](/images/EnvSprite_chunk.png?b2cf1)](https://minecraft.wiki/w/Chunk_format "Chunk format")[Chunk format](https://minecraft.wiki/w/Chunk_format "Chunk format") * [![](/images/EntitySprite_steve.png?856f8)](https://minecraft.wiki/w/Player.dat_format "Player.dat format")[Player format](https://minecraft.wiki/w/Player.dat_format "Player.dat format") * [![](/images/BlockSprite_lodestone.png?00f1a)](https://minecraft.wiki/w/Point_of_Interest_format "Point of Interest format")[Point of Interest format](https://minecraft.wiki/w/Point_of_Interest_format "Point of Interest format") * [![](/images/EntitySprite_ravager.png?40196)](https://minecraft.wiki/w/Raids.dat_format "Raids.dat format")[raids.dat format](https://minecraft.wiki/w/Raids.dat_format "Raids.dat format") * [![](/images/BlockSprite_chain-command-block.png?0afa8)](https://minecraft.wiki/w/Command_storage_format "Command storage format")[Command storage format](https://minecraft.wiki/w/Command_storage_format "Command storage format") * [![](/images/EnvSprite_scoreboard.png?38feb)](https://minecraft.wiki/w/Scoreboard#NBT_format "Scoreboard")[Scoreboard format](https://minecraft.wiki/w/Scoreboard#NBT_format "Scoreboard")  |  |  | | --- | --- | | Legacy | * [![](/images/LegacyBlockSprite_bricks-je1.png?9a58b)](https://minecraft.wiki/w/Java_Edition_Classic_level_format "Java Edition Classic level format")[Classic level format](https://minecraft.wiki/w/Java_Edition_Classic_level_format "Java Edition Classic level format") * [Classic server protocol](https://minecraft.wiki/w/Classic_server_protocol "Classic server protocol") * [![](/images/EntitySprite_rana.png?3f2f9)](https://minecraft.wiki/w/Java_Edition_Indev_level_format "Java Edition Indev level format")[Indev level format](https://minecraft.wiki/w/Java_Edition_Indev_level_format "Java Edition Indev level format") * [![](/images/EnvSprite_nether-portal.png?47646)](https://minecraft.wiki/w/Java_Edition_Alpha_level_format "Java Edition Alpha level format")[Alpha level format](https://minecraft.wiki/w/Java_Edition_Alpha_level_format "Java Edition Alpha level format")   + [![](/images/LegacyItemSprite_oak-door-revision-1.png?b7426)](https://minecraft.wiki/w/Zone_file_format "Zone file format")[Zone file format](https://minecraft.wiki/w/Zone_file_format "Zone file format") * [![](/images/ItemSprite_locked-map.png?c4112)](https://minecraft.wiki/w/Region_file_format "Region file format")[Region file format](https://minecraft.wiki/w/Region_file_format "Region file format") * [![](/images/Servers.png?b1dc2)](https://minecraft.wiki/w/Server_level.dat "Server level.dat")[server\_level.dat format](https://minecraft.wiki/w/Server_level.dat "Server level.dat") * [![](/images/EnvSprite_new-village.png?3e8a5)](https://minecraft.wiki/w/Villages.dat_format "Villages.dat format")[villages.dat format](https://minecraft.wiki/w/Villages.dat_format "Villages.dat format") * [![](/images/EnvSprite_abandoned-mineshaft.png?fab65)](https://minecraft.wiki/w/Generated_structures_data_file_format "Generated structures data file format")[Generated structures format](https://minecraft.wiki/w/Generated_structures_data_file_format "Generated structures data file format") | | | | [.minecraft](https://minecraft.wiki/w/.minecraft ".minecraft") | * ![File archive.png: Sprite image for archive in Minecraft](/images/thumb/File_archive.png/16px-File_archive.png?5ba7d) [client.jar](https://minecraft.wiki/w/Client.jar "Client.jar")   + [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Version.json "Version.json")[version.json](https://minecraft.wiki/w/Version.json "Version.json") * [![](/images/ItemSprite_book-and-quill.png?f190b)](https://minecraft.wiki/w/Client.json "Client.json")[client.json](https://minecraft.wiki/w/Client.json "Client.json") * [![](/images/BlockSprite_command-block.png?e7078)](https://minecraft.wiki/w/Command_history.txt "Command history.txt")[command\_history.txt](https://minecraft.wiki/w/Command_history.txt "Command history.txt") * [![](/images/BlockSprite_chest.png?15d81)](https://minecraft.wiki/w/Launcher_profiles.json "Launcher profiles.json")[launcher\_profiles.json](https://minecraft.wiki/w/Launcher_profiles.json "Launcher profiles.json") * [![](/images/Chat_settings_gear.png?6a179)](https://minecraft.wiki/w/Options.txt "Options.txt")[options.txt](https://minecraft.wiki/w/Options.txt "Options.txt") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Version_manifest.json "Version manifest.json")[version\_manifest.json](https://minecraft.wiki/w/Version_manifest.json "Version manifest.json") * [![](/images/ItemSprite_paper.png?565a1)](https://minecraft.wiki/w/Hotbar.nbt_format "Hotbar.nbt format")[hotbar.nbt format](https://minecraft.wiki/w/Hotbar.nbt_format "Hotbar.nbt format") * [![](/images/Servers.png?b1dc2)](https://minecraft.wiki/w/Servers.dat_format "Servers.dat format")[Server list format](https://minecraft.wiki/w/Servers.dat_format "Servers.dat format") | | Tools | * `F3` [Debug screen](https://minecraft.wiki/w/Debug_screen "Debug screen")   + [hotkey](https://minecraft.wiki/w/Debug_hotkey "Debug hotkey")   + [renderer](https://minecraft.wiki/w/Debug_renderer "Debug renderer") * [![](/images/Mojang_logo.svg?0b294)](https://minecraft.wiki/w/Java_developer_tools "Java developer tools")[Developer Tools](https://minecraft.wiki/w/Java_developer_tools "Java developer tools")   + [![](/images/BlockSprite_test-instance-block.png?27a39)](https://minecraft.wiki/w/GameTest "GameTest")[GameTest](https://minecraft.wiki/w/GameTest "GameTest")   + [DataFixerUpper](https://minecraft.wiki/w/DataFixerUpper "DataFixerUpper")   + [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Debug_property "Debug property")[Debug properties](https://minecraft.wiki/w/Debug_property "Debug property")  |  |  | | --- | --- | | Legacy | * [![](/images/BlockSprite_computer.png?e0c37)](https://minecraft.wiki/w/Obfuscation_map "Obfuscation map")[Obfuscation map](https://minecraft.wiki/w/Obfuscation_map "Obfuscation map") | | | Sound | * [![](/images/BlockSprite_jukebox-side.png?8477e)](https://minecraft.wiki/w/Block_sound_type "Block sound type")[Block sound type](https://minecraft.wiki/w/Block_sound_type "Block sound type") * [![](/images/EnvSprite_chat.png?0dd92)](https://minecraft.wiki/w/Closed_captions "Closed captions")[Closed captions](https://minecraft.wiki/w/Closed_captions "Closed captions") * [![](/images/EnvSprite_ambience.png?d7c92)](https://minecraft.wiki/w/Sounds.json "Sounds.json")[sounds.json](https://minecraft.wiki/w/Sounds.json "Sounds.json") | | [Commands](https://minecraft.wiki/w/Commands "Commands") | * [Brigadier](https://minecraft.wiki/w/Brigadier "Brigadier") * [![](/images/BlockSprite_repeating-command-block.png?1dad0)](https://minecraft.wiki/w/Function_%28Java_Edition%29 "Function (Java Edition)")[Functions](https://minecraft.wiki/w/Function_%28Java_Edition%29 "Function (Java Edition)")   **[All commands](https://minecraft.wiki/w/Template%3ANavbox_commands "Template:Navbox commands")** | | [Launching](https://minecraft.wiki/w/Minecraft_Launcher "Minecraft Launcher") | * [Mojang API](https://minecraft.wiki/w/Mojang_API "Mojang API") * [![](/images/Microsoft_logo.svg?7e87a)](https://minecraft.wiki/w/Microsoft_authentication "Microsoft authentication")[Microsoft authentication](https://minecraft.wiki/w/Microsoft_authentication "Microsoft authentication") * [![](/images/thumb/Java_Edition_icon_3.png/16px-Java_Edition_icon_3.png?f7112)](https://minecraft.wiki/w/Quick_Play "Quick Play")[Quick Play](https://minecraft.wiki/w/Quick_Play "Quick Play")  |  |  | | --- | --- | | Legacy | * [Legacy Minecraft authentication](https://minecraft.wiki/w/Legacy_Minecraft_authentication "Legacy Minecraft authentication") * [Yggdrasil](https://minecraft.wiki/w/Yggdrasil "Yggdrasil") | | | [Protocol](https://minecraft.wiki/w/Java_Edition_protocol "Java Edition protocol") | * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Protocol_version "Protocol version")[Protocol version](https://minecraft.wiki/w/Protocol_version "Protocol version") * [![](/images/ItemSprite_bundle.png?9eb9f)](https://minecraft.wiki/w/Java_Edition_protocol/Packets "Java Edition protocol/Packets")[Packets](https://minecraft.wiki/w/Java_Edition_protocol/Packets "Java Edition protocol/Packets") * [Data types](https://minecraft.wiki/w/Java_Edition_protocol/Data_types "Java Edition protocol/Data types") * [![](/images/BlockSprite_computer.png?e0c37)](https://minecraft.wiki/w/Java_Edition_protocol/Encryption "Java Edition protocol/Encryption")[Encryption](https://minecraft.wiki/w/Java_Edition_protocol/Encryption "Java Edition protocol/Encryption") | | [Server](https://minecraft.wiki/w/Server "Server") | * ![File archive.png: Sprite image for archive in Minecraft](/images/thumb/File_archive.png/16px-File_archive.png?5ba7d) [server.jar](https://minecraft.wiki/w/Server.jar "Server.jar") * [![](/images/BlockSprite_test-instance-block.png?27a39)](https://minecraft.wiki/w/Server.properties "Server.properties")[server.properties](https://minecraft.wiki/w/Server.properties "Server.properties") * [![](/images/BlockSprite_test-instance-block.png?27a39)](https://minecraft.wiki/w/Server/Requirements "Server/Requirements")[Server requirements](https://minecraft.wiki/w/Server/Requirements "Server/Requirements") * [![](/images/BlockSprite_test-block-accept.png?08355)](https://minecraft.wiki/w/Whitelist "Whitelist")[Whitelist](https://minecraft.wiki/w/Whitelist "Whitelist") * [Operator list](https://minecraft.wiki/w/Server#Operator_list "Server")  |  |  | | --- | --- | | Protocols | * [Query](https://minecraft.wiki/w/Query "Query") * [RCON](https://minecraft.wiki/w/RCON "RCON") * [Server Management Protocol](https://minecraft.wiki/w/Minecraft_Server_Management_Protocol "Minecraft Server Management Protocol") | | | Legacy | * [al\_version](https://minecraft.wiki/w/Al_version "Al version") * [![](/images/EnvSprite_item.png?89d23)](https://minecraft.wiki/w/Item_format "Item format")[Item format](https://minecraft.wiki/w/Item_format "Item format") | | |
| | [Data pack](https://minecraft.wiki/w/Data_pack "Data pack") | | | --- | --- | | Components | * [pack.mcmeta](https://minecraft.wiki/w/Pack.mcmeta "Pack.mcmeta") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Pack_format "Pack format")[Pack format](https://minecraft.wiki/w/Pack_format "Pack format") * [![](/images/ItemSprite_map.png?05f8c)](https://minecraft.wiki/w/Advancement_definition "Advancement definition")[Advancements](https://minecraft.wiki/w/Advancement_definition "Advancement definition") * [![](/images/BlockSprite_repeating-command-block.png?1dad0)](https://minecraft.wiki/w/Function_%28Java_Edition%29 "Function (Java Edition)")[Functions](https://minecraft.wiki/w/Function_%28Java_Edition%29 "Function (Java Edition)") * [![](/images/BlockSprite_red-banner.png?8b4d0)](https://minecraft.wiki/w/Item_modifier "Item modifier")[Item modifier](https://minecraft.wiki/w/Item_modifier "Item modifier") * [![](/images/ItemSprite_diamond.png?8f019)](https://minecraft.wiki/w/Loot_table "Loot table")[Loot tables](https://minecraft.wiki/w/Loot_table "Loot table") * [![](/images/BlockSprite_test-block-start.png?35191)](https://minecraft.wiki/w/Predicate "Predicate")[Predicate](https://minecraft.wiki/w/Predicate "Predicate") * [![](/images/BlockSprite_crafting-table.png?6e126)](https://minecraft.wiki/w/Recipe_%28Java_Edition%29 "Recipe (Java Edition)")[Recipe](https://minecraft.wiki/w/Recipe_%28Java_Edition%29 "Recipe (Java Edition)") * [![](/images/EffectSprite_strength.png?05e79)](https://minecraft.wiki/w/Damage_type "Damage type")[Damage type](https://minecraft.wiki/w/Damage_type "Damage type") * [![](/images/EnvSprite_chat.png?0dd92)](https://minecraft.wiki/w/Chat_type "Chat type")[Chat type](https://minecraft.wiki/w/Chat_type "Chat type") * [![](/images/ItemSprite_enchanted-book.png?b7877)](https://minecraft.wiki/w/Enchantment_definition "Enchantment definition")[Enchantment](https://minecraft.wiki/w/Enchantment_definition "Enchantment definition") * [![](/images/BlockSprite_enchanting-table.png?45e2c)](https://minecraft.wiki/w/Enchantment_provider "Enchantment provider")[Enchantment provider](https://minecraft.wiki/w/Enchantment_provider "Enchantment provider") * [![](/images/ItemSprite_painting.png?55d20)](https://minecraft.wiki/w/Painting_variant_definition "Painting variant definition")[Painting variant](https://minecraft.wiki/w/Painting_variant_definition "Painting variant definition") * [![](/images/BlockSprite_white-banner.png?8b4d0)](https://minecraft.wiki/w/Banner_pattern_definition "Banner pattern definition")[Banner pattern](https://minecraft.wiki/w/Banner_pattern_definition "Banner pattern definition") * [![](/images/ItemSprite_goat-horn.png?e5a9f)](https://minecraft.wiki/w/Instrument_definition "Instrument definition")[Instrument](https://minecraft.wiki/w/Instrument_definition "Instrument definition") * [![](/images/BlockSprite_jukebox.png?86205)](https://minecraft.wiki/w/Jukebox_song_definition "Jukebox song definition")[Jukebox song](https://minecraft.wiki/w/Jukebox_song_definition "Jukebox song definition") * [![](/images/BlockSprite_trial-spawner.png?0a3dc)](https://minecraft.wiki/w/Trial_spawner_configuration "Trial spawner configuration")[Trial spawner configuration](https://minecraft.wiki/w/Trial_spawner_configuration "Trial spawner configuration") * [![](/images/EntitySprite_pig.png?5435e)](https://minecraft.wiki/w/Mob_variant_definitions "Mob variant definitions")[Mob variants](https://minecraft.wiki/w/Mob_variant_definitions "Mob variant definitions") * [![](/images/ItemSprite_paper.png?565a1)](https://minecraft.wiki/w/Dialog "Dialog")[Dialog](https://minecraft.wiki/w/Dialog "Dialog") * [![](/images/ItemSprite_wayfinder-armor-trim.png?ffaf0)](https://minecraft.wiki/w/Armor_trim_definition "Armor trim definition")[Armor trim](https://minecraft.wiki/w/Armor_trim_definition "Armor trim definition") * [![](/images/ItemSprite_footprint.png?1c844)](https://minecraft.wiki/w/Slot_sources "Slot sources")[Slot sources](https://minecraft.wiki/w/Slot_sources "Slot sources") * [![](/images/ItemSprite_clock.png?30324)](https://minecraft.wiki/w/Timeline "Timeline")[Timeline](https://minecraft.wiki/w/Timeline "Timeline") * [![](/images/EntitySprite_villager.png?05433)](https://minecraft.wiki/w/Villager_trade_definition "Villager trade definition")[Villager trade](https://minecraft.wiki/w/Villager_trade_definition "Villager trade definition") * [Trade set](https://minecraft.wiki/w/Trade_set "Trade set") * [World Clock](https://minecraft.wiki/w/World_Clock "World Clock") * [![](/images/EntitySprite_sulfur-cube.png?ad68d)](https://minecraft.wiki/w/Sulfur_cube_archetype_definition "Sulfur cube archetype definition")[Sulfur cube archetype](https://minecraft.wiki/w/Sulfur_cube_archetype_definition "Sulfur cube archetype definition")​[*upcoming: [JE 26.2](https://minecraft.wiki/w/Java_Edition_26.2 "Java Edition 26.2")*]  |  |  | | --- | --- | | [Tag](https://minecraft.wiki/w/Tag_%28Java_Edition%29 "Tag (Java Edition)") | * [![](/images/BlockSprite_grass-block.png?97c2e)](https://minecraft.wiki/w/Block_tag_%28Java_Edition%29 "Block tag (Java Edition)")[Block](https://minecraft.wiki/w/Block_tag_%28Java_Edition%29 "Block tag (Java Edition)") * [![](/images/EnvSprite_item.png?89d23)](https://minecraft.wiki/w/Item_tag_%28Java_Edition%29 "Item tag (Java Edition)")[Item](https://minecraft.wiki/w/Item_tag_%28Java_Edition%29 "Item tag (Java Edition)") * [![](/images/BlockSprite_repeating-command-block.png?1dad0)](https://minecraft.wiki/w/Function_tag_%28Java_Edition%29 "Function tag (Java Edition)")[Function](https://minecraft.wiki/w/Function_tag_%28Java_Edition%29 "Function tag (Java Edition)") * [![](/images/ItemSprite_water-bucket.png?6e72b)](https://minecraft.wiki/w/Fluid_tag_%28Java_Edition%29 "Fluid tag (Java Edition)")[Fluid](https://minecraft.wiki/w/Fluid_tag_%28Java_Edition%29 "Fluid tag (Java Edition)") * [![](/images/EnvSprite_entities.png?94711)](https://minecraft.wiki/w/Entity_type_tag_%28Java_Edition%29 "Entity type tag (Java Edition)")[Entity type](https://minecraft.wiki/w/Entity_type_tag_%28Java_Edition%29 "Entity type tag (Java Edition)") * [![](/images/BlockSprite_sculk-sensor.png?ccbdb)](https://minecraft.wiki/w/Game_event_tag_%28Java_Edition%29 "Game event tag (Java Edition)")[Game event](https://minecraft.wiki/w/Game_event_tag_%28Java_Edition%29 "Game event tag (Java Edition)") * [![](/images/BiomeSprite_forest.png?98e29)](https://minecraft.wiki/w/Biome_tag_%28Java_Edition%29 "Biome tag (Java Edition)")[Biome](https://minecraft.wiki/w/Biome_tag_%28Java_Edition%29 "Biome tag (Java Edition)") * [![](/images/EnvSprite_superflat.png?54c14)](https://minecraft.wiki/w/Flat_level_generator_preset_tag_%28Java_Edition%29 "Flat level generator preset tag (Java Edition)")[Flat level generator preset](https://minecraft.wiki/w/Flat_level_generator_preset_tag_%28Java_Edition%29 "Flat level generator preset tag (Java Edition)") * [![](/images/EnvSprite_mountain.png?2e0ae)](https://minecraft.wiki/w/World_preset_tag_%28Java_Edition%29 "World preset tag (Java Edition)")[World preset](https://minecraft.wiki/w/World_preset_tag_%28Java_Edition%29 "World preset tag (Java Edition)") * [![](/images/EnvSprite_jungle-pyramid.png?736e3)](https://minecraft.wiki/w/Structure_tag_%28Java_Edition%29 "Structure tag (Java Edition)")[Structure](https://minecraft.wiki/w/Structure_tag_%28Java_Edition%29 "Structure tag (Java Edition)") * [![](/images/BlockSprite_lodestone.png?00f1a)](https://minecraft.wiki/w/Point_of_interest_type_tag_%28Java_Edition%29 "Point of interest type tag (Java Edition)")[Point of interest type](https://minecraft.wiki/w/Point_of_interest_type_tag_%28Java_Edition%29 "Point of interest type tag (Java Edition)") * [![](/images/ItemSprite_painting.png?55d20)](https://minecraft.wiki/w/Painting_variant_tag_%28Java_Edition%29 "Painting variant tag (Java Edition)")[Painting variant](https://minecraft.wiki/w/Painting_variant_tag_%28Java_Edition%29 "Painting variant tag (Java Edition)") * [![](/images/BlockSprite_white-banner.png?8b4d0)](https://minecraft.wiki/w/Banner_pattern_tag_%28Java_Edition%29 "Banner pattern tag (Java Edition)")[Banner pattern](https://minecraft.wiki/w/Banner_pattern_tag_%28Java_Edition%29 "Banner pattern tag (Java Edition)") * [![](/images/ItemSprite_goat-horn.png?e5a9f)](https://minecraft.wiki/w/Instrument_tag_%28Java_Edition%29 "Instrument tag (Java Edition)")[Instrument](https://minecraft.wiki/w/Instrument_tag_%28Java_Edition%29 "Instrument tag (Java Edition)") * ![❤️](/images/Heart_%28icon%29.png?faf83) [Damage type](https://minecraft.wiki/w/Damage_type_tag_%28Java_Edition%29 "Damage type tag (Java Edition)") * [![](/images/ItemSprite_enchanted-book.png?b7877)](https://minecraft.wiki/w/Enchantment_tag_%28Java_Edition%29 "Enchantment tag (Java Edition)")[Enchantment](https://minecraft.wiki/w/Enchantment_tag_%28Java_Edition%29 "Enchantment tag (Java Edition)") * [![](/images/ItemSprite_paper.png?565a1)](https://minecraft.wiki/w/Dialog_tag_%28Java_Edition%29 "Dialog tag (Java Edition)")[Dialog](https://minecraft.wiki/w/Dialog_tag_%28Java_Edition%29 "Dialog tag (Java Edition)") * [![](/images/ItemSprite_clock.png?30324)](https://minecraft.wiki/w/Timeline_tag_%28Java_Edition%29 "Timeline tag (Java Edition)")[Timeline](https://minecraft.wiki/w/Timeline_tag_%28Java_Edition%29 "Timeline tag (Java Edition)") * [![](/images/ItemSprite_water-bottle.png?fe7c2)](https://minecraft.wiki/w/Potion_tag_%28Java_Edition%29 "Potion tag (Java Edition)")[Potion](https://minecraft.wiki/w/Potion_tag_%28Java_Edition%29 "Potion tag (Java Edition)") * [![](/images/EntitySprite_villager.png?05433)](https://minecraft.wiki/w/Villager_trade_tag_%28Java_Edition%29 "Villager trade tag (Java Edition)")[Villager trade](https://minecraft.wiki/w/Villager_trade_tag_%28Java_Edition%29 "Villager trade tag (Java Edition)") * [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Configured_feature_tag_%28Java_Edition%29 "Configured feature tag (Java Edition)")[Configured feature](https://minecraft.wiki/w/Configured_feature_tag_%28Java_Edition%29 "Configured feature tag (Java Edition)") | | [GameTest](https://minecraft.wiki/w/GameTest "GameTest") | * [![](/images/BlockSprite_test-block-start.png?35191)](https://minecraft.wiki/w/Test_environment_definition "Test environment definition")[Test environment](https://minecraft.wiki/w/Test_environment_definition "Test environment definition") * [![](/images/BlockSprite_test-instance-block.png?27a39)](https://minecraft.wiki/w/Test_instance_definition "Test instance definition")[Test instance](https://minecraft.wiki/w/Test_instance_definition "Test instance definition") | | [World generation](https://minecraft.wiki/w/Custom_world_generation "Custom world generation") | * [Dimension](https://minecraft.wiki/w/Dimension_definition "Dimension definition") * [![](/images/EnvSprite_nether-portal.png?47646)](https://minecraft.wiki/w/Dimension_type "Dimension type")[Dimension type](https://minecraft.wiki/w/Dimension_type "Dimension type") * [![](/images/EnvSprite_mountain.png?2e0ae)](https://minecraft.wiki/w/World_preset_definition "World preset definition")[World preset](https://minecraft.wiki/w/World_preset_definition "World preset definition") * [![](/images/EnvSprite_biomes.png?0a976)](https://minecraft.wiki/w/Biome_definition "Biome definition")[Biomes](https://minecraft.wiki/w/Biome_definition "Biome definition") * [![](/images/EnvSprite_cave.png?47a17)](https://minecraft.wiki/w/Carver_definition "Carver definition")[Carver](https://minecraft.wiki/w/Carver_definition "Carver definition") * [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Configured_feature "Configured feature")[Configured feature](https://minecraft.wiki/w/Configured_feature "Configured feature")   + [![](/images/EnvSprite_oak.png?742a4)](https://minecraft.wiki/w/Tree_definition "Tree definition")[Tree](https://minecraft.wiki/w/Tree_definition "Tree definition") * [![](/images/EnvSprite_map.png?b863e)](https://minecraft.wiki/w/Placed_feature "Placed feature")[Placed feature](https://minecraft.wiki/w/Placed_feature "Placed feature") * [Environment attribute](https://minecraft.wiki/w/Environment_attribute "Environment attribute")  |  |  | | --- | --- | | [Noise settings](https://minecraft.wiki/w/Noise_settings "Noise settings") | * [![](/images/EnvSprite_mountain.png?2e0ae)](https://minecraft.wiki/w/Noise_router "Noise router")[Noise router](https://minecraft.wiki/w/Noise_router "Noise router") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Density_function "Density function")[Density function](https://minecraft.wiki/w/Density_function "Density function") * [Noises](https://minecraft.wiki/w/Noise "Noise") * [![](/images/EnvSprite_surface.png?75bf7)](https://minecraft.wiki/w/Surface_rule "Surface rule")[Surface rule](https://minecraft.wiki/w/Surface_rule "Surface rule") | | [Structures](https://minecraft.wiki/w/Structure_definition "Structure definition") | * [![](/images/EnvSprite_abandoned-mineshaft.png?fab65)](https://minecraft.wiki/w/Structure_set "Structure set")[Structure set](https://minecraft.wiki/w/Structure_set "Structure set") * [![](/images/BlockSprite_jigsaw.png?ec5e3)](https://minecraft.wiki/w/Template_pool "Template pool")[Template pool](https://minecraft.wiki/w/Template_pool "Template pool") * [![](/images/BlockSprite_cracked-stone-bricks.png?f3f1d)](https://minecraft.wiki/w/Processor_list "Processor list")[Processor list](https://minecraft.wiki/w/Processor_list "Processor list") * [![](/images/EnvSprite_nether-fossil.png?93621)](https://minecraft.wiki/w/Structure_file "Structure file")[Structure templates](https://minecraft.wiki/w/Structure_file "Structure file") | | Removed | * [![](/images/ItemSprite_iron-pickaxe.png?77536)](https://minecraft.wiki/w/Configured_surface_builder "Configured surface builder")[Configured surface builder](https://minecraft.wiki/w/Configured_surface_builder "Configured surface builder") | | | | Data packs | * [![](/images/BlockSprite_deepslate.png?d7361)](https://minecraft.wiki/w/Caves_%26_Cliffs_Prototype_Data_Pack "Caves & Cliffs Prototype Data Pack")[Caves & Cliffs Prototype Data Pack](https://minecraft.wiki/w/Caves_%26_Cliffs_Prototype_Data_Pack "Caves & Cliffs Prototype Data Pack") * [![](/images/ItemSprite_magical-painting.png?b0bf0)](https://minecraft.wiki/w/Phantom_Frames "Phantom Frames")[Phantom Frames](https://minecraft.wiki/w/Phantom_Frames "Phantom Frames") | | Tutorials | * [![](/images/thumb/EnvSprite_autosave.png/16px-EnvSprite_autosave.png?a55e7)](https://minecraft.wiki/w/Tutorial%3AImporting_a_data_pack "Tutorial:Importing a data pack")[Importing](https://minecraft.wiki/w/Tutorial%3AImporting_a_data_pack "Tutorial:Importing a data pack") * [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Tutorial%3ACreating_a_data_pack "Tutorial:Creating a data pack")[Creating](https://minecraft.wiki/w/Tutorial%3ACreating_a_data_pack "Tutorial:Creating a data pack") * [Optimizing](https://minecraft.wiki/w/Tutorial%3AOptimizing_a_data_pack "Tutorial:Optimizing a data pack") * [![](/images/BlockSprite_command-block.png?e7078)](https://minecraft.wiki/w/Tutorial%3ACommand_blocks_and_functions "Tutorial:Command blocks and functions")[Command blocks and functions](https://minecraft.wiki/w/Tutorial%3ACommand_blocks_and_functions "Tutorial:Command blocks and functions") * [Repairing a world corrupted by a data pack](https://minecraft.wiki/w/Tutorial%3ARepairing_a_world_corrupted_by_a_data_pack "Tutorial:Repairing a world corrupted by a data pack")  |  |  | | --- | --- | | Content | * [![](/images/ItemSprite_enchanted-book.png?b7877)](https://minecraft.wiki/w/Tutorial%3AAdding_custom_enchantments "Tutorial:Adding custom enchantments")[Custom enchantments](https://minecraft.wiki/w/Tutorial%3AAdding_custom_enchantments "Tutorial:Adding custom enchantments") * [![](/images/ItemSprite_painting.png?55d20)](https://minecraft.wiki/w/Tutorial%3AAdding_custom_paintings "Tutorial:Adding custom paintings")[Custom paintings](https://minecraft.wiki/w/Tutorial%3AAdding_custom_paintings "Tutorial:Adding custom paintings") * [![](/images/ItemSprite_armor-trim.png?1d672)](https://minecraft.wiki/w/Tutorial%3AAdding_custom_trims "Tutorial:Adding custom trims")[Custom trims](https://minecraft.wiki/w/Tutorial%3AAdding_custom_trims "Tutorial:Adding custom trims") | | World generation | * [![](/images/EnvSprite_other-portal.png?ca57b)](https://minecraft.wiki/w/Tutorial%3AAdding_a_new_dimension "Tutorial:Adding a new dimension")[New dimension](https://minecraft.wiki/w/Tutorial%3AAdding_a_new_dimension "Tutorial:Adding a new dimension") * [![](/images/EnvSprite_lunar-base.png?648e4)](https://minecraft.wiki/w/Tutorial%3ACustom_structures "Tutorial:Custom structures")[Custom structures](https://minecraft.wiki/w/Tutorial%3ACustom_structures "Tutorial:Custom structures") | | | |
| | [Resource pack](https://minecraft.wiki/w/Resource_pack "Resource pack") | | | --- | --- | | Components | * [pack.mcmeta](https://minecraft.wiki/w/Pack.mcmeta "Pack.mcmeta") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Pack_format "Pack format")[Pack format](https://minecraft.wiki/w/Pack_format "Pack format") * [![](/images/EnvSprite_language.png?39da2)](https://minecraft.wiki/w/Resource_pack#Language "Resource pack")[Language](https://minecraft.wiki/w/Resource_pack#Language "Resource pack") * [![](/images/EntitySprite_creeper.png?703e9)](https://minecraft.wiki/w/Model "Model")[Models](https://minecraft.wiki/w/Model "Model") * [![](/images/BlockSprite_double-stone-slab.png?62750)](https://minecraft.wiki/w/Blockstates_definition "Blockstates definition")[Blockstates](https://minecraft.wiki/w/Blockstates_definition "Blockstates definition") * [![](/images/EnvSprite_item.png?89d23)](https://minecraft.wiki/w/Items_model_definition "Items model definition")[Items](https://minecraft.wiki/w/Items_model_definition "Items model definition") * [![](/images/EnvSprite_ambience.png?d7c92)](https://minecraft.wiki/w/Sound "Sound")[Sounds](https://minecraft.wiki/w/Sound "Sound") ([sounds.json](https://minecraft.wiki/w/Sounds.json "Sounds.json")) * [Shaders](https://minecraft.wiki/w/Shader "Shader") * [![](/images/EnvSprite_texture-pack.png?a4213)](https://minecraft.wiki/w/Resource_pack#Textures "Resource pack")[Textures](https://minecraft.wiki/w/Resource_pack#Textures "Resource pack") * [![](/images/ItemSprite_compass.png?2364d)](https://minecraft.wiki/w/Atlas "Atlas")[Atlases](https://minecraft.wiki/w/Atlas "Atlas") * [Aa](https://minecraft.wiki/w/Font "Font") [Fonts](https://minecraft.wiki/w/Font "Font") * [![](/images/BlockSprite_oak-leaves.png?81553)](https://minecraft.wiki/w/Resource_pack#Colormaps "Resource pack")[Colormaps](https://minecraft.wiki/w/Resource_pack#Colormaps "Resource pack") * ![File file.png: Sprite image for file in Minecraft](/images/thumb/File_file.png/16px-File_file.png?e19ce) [Texts](https://minecraft.wiki/w/Resource_pack#Texts "Resource pack") * [![](/images/Locator_Bar_icon_bowtie.png?a8cd8)](https://minecraft.wiki/w/Waypoint_style "Waypoint style")[Waypoint styles](https://minecraft.wiki/w/Waypoint_style "Waypoint style") * [regional\_compliancies.json](https://minecraft.wiki/w/Resource_pack#Regional_compliancies_warnings "Resource pack") * [![](/images/ItemSprite_all-iron-armor.png?87e31)](https://minecraft.wiki/w/Equipment "Equipment")[Equipment](https://minecraft.wiki/w/Equipment "Equipment") | | Debug | * [Missing font character](https://minecraft.wiki/w/Missing_font_character "Missing font character") * [![](/images/BlockSprite_missingno.png?031f4)](https://minecraft.wiki/w/Missing_model "Missing model")[Missing model](https://minecraft.wiki/w/Missing_model "Missing model") * [![](/images/BlockSprite_missingno.png?031f4)](https://minecraft.wiki/w/Missing_texture "Missing texture")[Missing texture](https://minecraft.wiki/w/Missing_texture "Missing texture") | | Tools | * [Slicer](https://minecraft.wiki/w/Slicer "Slicer")  |  |  | | --- | --- | | Legacy | * [Texture Ender](https://minecraft.wiki/w/Texture_Ender "Texture Ender") * [Unstitcher](https://minecraft.wiki/w/Unstitcher "Unstitcher") | | | Tutorials | * [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Tutorial%3ACreating_a_resource_pack "Tutorial:Creating a resource pack")[Creating](https://minecraft.wiki/w/Tutorial%3ACreating_a_resource_pack "Tutorial:Creating a resource pack") * [![](/images/Download.png?048e3)](https://minecraft.wiki/w/Tutorial%3ALoading_a_resource_pack "Tutorial:Loading a resource pack")[Loading](https://minecraft.wiki/w/Tutorial%3ALoading_a_resource_pack "Tutorial:Loading a resource pack") * [![](/images/EnvSprite_fluids.png?58a6a)](https://minecraft.wiki/w/Tutorial%3AModels "Tutorial:Models")[Models](https://minecraft.wiki/w/Tutorial%3AModels "Tutorial:Models") * [![](/images/EnvSprite_ambience.png?d7c92)](https://minecraft.wiki/w/Tutorial%3ASound_directory "Tutorial:Sound directory")[Sound directory](https://minecraft.wiki/w/Tutorial%3ASound_directory "Tutorial:Sound directory") | | |

Retrieved from "<https://minecraft.wiki/w/Entity_format?oldid=3564296>"

[Categories](https://minecraft.wiki/w/Special%3ACategories "Special:Categories"):

* [Java Edition](https://minecraft.wiki/w/Category%3AJava_Edition "Category:Java Edition")
* [Java Edition technical](https://minecraft.wiki/w/Category%3AJava_Edition_technical "Category:Java Edition technical")
* [Development](https://minecraft.wiki/w/Category%3ADevelopment "Category:Development")

Hidden categories:

* [Articles to be expanded](https://minecraft.wiki/w/Category%3AArticles_to_be_expanded "Category:Articles to be expanded")
* [Information needed](https://minecraft.wiki/w/Category%3AInformation_needed "Category:Information needed")
* [Verify](https://minecraft.wiki/w/Category%3AVerify "Category:Verify")

## Navigation menu

### Personal tools

* [Create account](https://minecraft.wiki/w/Special%3ACreateAccount?returnto=Entity+format "You are encouraged to create an account and log in; however, it is not mandatory")
* [Log in](https://minecraft.wiki/w/Special%3AUserLogin?returnto=Entity+format "You are encouraged to log in; however, it is not mandatory [o]")

### associated-pages

* [Page](https://minecraft.wiki/w/Entity_format "View the content page [c]")
* [Talk](https://minecraft.wiki/w/Talk%3AEntity_format "Talk about the content page [t]")

[ ]

English

### Views

* [Read](https://minecraft.wiki/w/Entity_format)
* [Edit](https://minecraft.wiki/w/Entity_format?veaction=edit "Edit this page [v]")
* [Edit source](https://minecraft.wiki/w/Entity_format?action=edit "Edit the source code of this page [e]")
* [View history](https://minecraft.wiki/w/Entity_format?action=history "Past revisions of this page [h]")
