# Data component format

From Minecraft Wiki

[Jump to navigation](#mw-head)
[Jump to search](#searchInput)

![](/images/Disambig_color.svg?2db52) This article is about the format in *[Java Edition](https://minecraft.wiki/w/Java_Edition "Java Edition")*. For the legacy format, see [Item format/Before 1.20.5](https://minecraft.wiki/w/Item_format/Before_1.20.5 "Item format/Before 1.20.5"). For the format in *[Bedrock Edition](https://minecraft.wiki/w/Bedrock_Edition "Bedrock Edition")*, see [Item components](https://minecraft.wiki/w/Item_components "Item components").

![](/images/Disambig_color.svg?2db52) For other uses, see [Component](https://minecraft.wiki/w/Component "Component").

[![](/images/Information_icon.svg?15c1c)](https://minecraft.wiki/w/File%3AInformation_icon.svg "File:Information icon.svg")

This feature is exclusive to [*Java Edition*](https://minecraft.wiki/w/Java_Edition "Java Edition").

**Data components**, or simply **components**, are structured data used to store information and define behavior. Their IDs are [namespaced identifiers](https://minecraft.wiki/w/Namespaced_identifier "Namespaced identifier"), and their values can be any data type – see [§ List of components](#List_of_components).

When used by [items](https://minecraft.wiki/w/Item "Item"), they are referred as **item components** or **item stack components**. They can exist anywhere that an item is stored, such as the [player's inventory](https://minecraft.wiki/w/Player.dat_format "Player.dat format"), container [block entities](https://minecraft.wiki/w/Block_entity_format "Block entity format"), and [structure files](https://minecraft.wiki/w/Structure_file "Structure file"). Importantly, not all characteristics of items are covered by data components, and remain as fixed properties associated with the item ID; the behaviour cannot be removed from the item, nor applied to a different item that does not have that behaviour by default. For a reasonably comprehensive list of such properties associated with items in the latest version, see [Java Edition hardcoded item properties](https://minecraft.wiki/w/Java_Edition_hardcoded_item_properties "Java Edition hardcoded item properties").

Data components are only partly implemented for [block entities](https://minecraft.wiki/w/Block_entities "Block entities"). They partially replace the [NBT format](https://minecraft.wiki/w/NBT_format "NBT format") and allow some block data to be read or copied through predicates and loot functions.

Similarly, entities can interact with data components through predicates and loot functions, however they still strictly use the [NBT format](https://minecraft.wiki/w/NBT_format "NBT format") and other older internal systems to store their data in memory, not data components.

[ ]

## Contents

- [Data component format](#data-component-format)
  - [Contents](#contents)
  - [Usage](#usage)
    - [Command format](#command-format)
    - [Item format](#item-format)
    - [Block entity format](#block-entity-format)
  - [List of components](#list-of-components)
    - [attack\_range](#attack_range)
    - [attribute\_modifiers](#attribute_modifiers)
    - [banner\_patterns](#banner_patterns)
    - [base\_color](#base_color)
    - [bees](#bees)
    - [block\_entity\_data](#block_entity_data)
    - [block\_state](#block_state)
    - [blocks\_attacks](#blocks_attacks)
    - [break\_sound](#break_sound)
    - [bucket\_entity\_data](#bucket_entity_data)
    - [bundle\_contents](#bundle_contents)
    - [can\_break](#can_break)
    - [can\_place\_on](#can_place_on)
    - [charged\_projectiles](#charged_projectiles)
    - [consumable](#consumable)
    - [container](#container)
    - [container\_loot](#container_loot)
    - [custom\_data](#custom_data)
    - [custom\_model\_data](#custom_model_data)
    - [custom\_name](#custom_name)
    - [damage](#damage)
    - [damage\_resistant](#damage_resistant)
    - [damage\_type](#damage_type)
    - [death\_protection](#death_protection)
    - [debug\_stick\_state](#debug_stick_state)
    - [dye](#dye)
    - [dyed\_color](#dyed_color)
    - [enchantable](#enchantable)
    - [enchantment\_glint\_override](#enchantment_glint_override)
    - [enchantments](#enchantments)
    - [entity\_data](#entity_data)
    - [equippable](#equippable)
    - [firework\_explosion](#firework_explosion)
    - [fireworks](#fireworks)
    - [food](#food)
    - [glider](#glider)
    - [instrument](#instrument)
    - [intangible\_projectile](#intangible_projectile)
    - [item\_model](#item_model)
    - [item\_name](#item_name)
    - [jukebox\_playable](#jukebox_playable)
    - [kinetic\_weapon](#kinetic_weapon)
    - [lock](#lock)
    - [lodestone\_tracker](#lodestone_tracker)
    - [lore](#lore)
    - [map\_color](#map_color)
    - [map\_decorations](#map_decorations)
    - [map\_id](#map_id)
    - [max\_damage](#max_damage)
    - [max\_stack\_size](#max_stack_size)
    - [minimum\_attack\_charge](#minimum_attack_charge)
    - [note\_block\_sound](#note_block_sound)
    - [ominous\_bottle\_amplifier](#ominous_bottle_amplifier)
    - [piercing\_weapon](#piercing_weapon)
    - [pot\_decorations](#pot_decorations)
    - [potion\_contents](#potion_contents)
    - [potion\_duration\_scale](#potion_duration_scale)
    - [profile](#profile)
    - [provides\_banner\_patterns](#provides_banner_patterns)
    - [provides\_trim\_material](#provides_trim_material)
    - [rarity](#rarity)
    - [recipes](#recipes)
    - [repair\_cost](#repair_cost)
    - [repairable](#repairable)
    - [stored\_enchantments](#stored_enchantments)
    - [sulfur\_cube\_content](#sulfur_cube_content)
    - [suspicious\_stew\_effects](#suspicious_stew_effects)
    - [swing\_animation](#swing_animation)
    - [tool](#tool)
    - [tooltip\_display](#tooltip_display)
    - [tooltip\_style](#tooltip_style)
    - [trim](#trim)
    - [unbreakable](#unbreakable)
    - [use\_cooldown](#use_cooldown)
    - [use\_effects](#use_effects)
    - [use\_remainder](#use_remainder)
    - [weapon](#weapon)
    - [writable\_book\_content](#writable_book_content)
    - [written\_book\_content](#written_book_content)
  - [Entity variant components](#entity-variant-components)
    - [axolotl/variant](#axolotlvariant)
    - [cat/collar](#catcollar)
    - [cat/variant](#catvariant)
    - [chicken/variant](#chickenvariant)
    - [cow/variant](#cowvariant)
    - [fox/variant](#foxvariant)
    - [frog/variant](#frogvariant)
    - [horse/variant](#horsevariant)
    - [llama/variant](#llamavariant)
    - [mooshroom/variant](#mooshroomvariant)
    - [painting/variant](#paintingvariant)
    - [parrot/variant](#parrotvariant)
    - [pig/variant](#pigvariant)
    - [rabbit/variant](#rabbitvariant)
    - [salmon/size](#salmonsize)
    - [sheep/color](#sheepcolor)
    - [shulker/color](#shulkercolor)
    - [tropical\_fish/base\_color](#tropical_fishbase_color)
    - [tropical\_fish/pattern](#tropical_fishpattern)
    - [tropical\_fish/pattern\_color](#tropical_fishpattern_color)
    - [villager/variant](#villagervariant)
    - [wolf/collar](#wolfcollar)
    - [wolf/sound\_variant](#wolfsound_variant)
    - [wolf/variant](#wolfvariant)
  - [Non-encoded components](#non-encoded-components)
    - [additional\_trade\_cost](#additional_trade_cost)
    - [creative\_slot\_lock](#creative_slot_lock)
    - [map\_post\_processing](#map_post_processing)
  - [Exclusive to joke versions](#exclusive-to-joke-versions)
    - [24w14potato](#24w14potato)
      - [clicks](#clicks)
      - [contacts\_messages](#contacts_messages)
      - [explicit\_foil](#explicit_foil)
      - [fletching](#fletching)
      - [heat](#heat)
      - [hovered](#hovered)
      - [lubrication](#lubrication)
      - [potato\_bane](#potato_bane)
      - [resin](#resin)
      - [secret\_message](#secret_message)
      - [snek](#snek)
      - [undercover\_id](#undercover_id)
      - [views](#views)
      - [xp](#xp)
    - [25w14craftmine](#25w14craftmine)
      - [dimension\_id](#dimension_id)
      - [exchange\_value](#exchange_value)
      - [instant\_room](#instant_room)
      - [mine\_active](#mine_active)
      - [mine\_completed](#mine_completed)
      - [mob\_trophy/type](#mob_trophytype)
      - [sky](#sky)
      - [special\_mine](#special_mine)
      - [trophy/type](#trophytype)
      - [world\_effect\_uhint](#world_effect_uhint)
      - [world\_effect\_unlock](#world_effect_unlock)
      - [world\_modifiers](#world_modifiers)
    - [26w14a](#26w14a)
      - [follow](#follow)
  - [History](#history)
  - [Notes](#notes)
  - [Navigation](#navigation)

## Usage


### Command format


Data components can be used in the [item\_stack](https://minecraft.wiki/w/Argument_types#minecraft:item_stack "Argument types") and [item\_predicate](https://minecraft.wiki/w/Argument_types#minecraft:item_predicate "Argument types") argument types.

In commands that take an item\_stack argument, such as `/[give](https://minecraft.wiki/w/Commands/give "Commands/give")`, items are represented in the format `item_id[component1=value,component2=value]`, with *component* being the [namespaced ID](https://minecraft.wiki/w/Namespaced_ID "Namespaced ID") of a component, and the *value* being the value of the component written in [SNBT format](https://minecraft.wiki/w/NBT_format#SNBT_format "NBT format"). Components can be removed by prefixing them with an exclamation mark, like `item_id[!component3]`. Any components that are not specified are implicitly set to the component's default value for that item type. If no components are specified, the square brackets can be removed, leaving just the item ID. See [item\_stack](https://minecraft.wiki/w/Argument_types#minecraft:item_stack "Argument types") for details.

In commands that take an item\_predicate argument, such as `/[clear](https://minecraft.wiki/w/Commands/clear "Commands/clear")` and `/[execute](https://minecraft.wiki/w/Commands/execute "Commands/execute") if items`, item predicates are represented in the format `item_type[list of tests]`, with each *test* either checking if a component exists with any value, checking for an exact component value match, or checking for a [data component predicate](https://minecraft.wiki/w/Data_component_predicate "Data component predicate"). See [item\_predicate](https://minecraft.wiki/w/Argument_types#minecraft:item_predicate "Argument types") for details.

### Item format


![](/images/Disambig_color.svg?2db52) For the legacy format before 1.20.5, see [Item format/Before 1.20.5](https://minecraft.wiki/w/Item_format/Before_1.20.5 "Item format/Before 1.20.5").

Every item type (item ID) has a set of *default* data components. Item stacks must specify an item ID, which implicitly sets these default components, but they may be overridden by that individual item stack. Default components are not saved on individual item stacks.

When saved in the [NBT format](https://minecraft.wiki/w/NBT_format "NBT format"), items are written as a compound with the following tags:

* [NBT Compound / JSON Object] The root tag.
  + [String] id: The [resource location](https://minecraft.wiki/w/Resource_location "Resource location") of the item. Must not be `minecraft:air`.
  + [Int] count: Number of [items](https://minecraft.wiki/w/Item "Item") stacked in this inventory slot. Any item can be stacked, even if unstackable through normal means. Defaults to 1 if not specified.
  + [NBT Compound / JSON Object] components: Optional map of additional (non-default) data components.
    - See the [list of components below](#List_of_components).

In containers that do not use the data component format (such as container blocks and entity inventories), an additional [Byte] Slot tag is used to specify the slot the item is in e.g. `{Slot:0b,id:"stone"}`. This is not a part of the item stack format so is not present anywhere else where individual items are stored (such as single-slot containers, unstructured lists of items, etc.). In the data component format, slot numbers and item stacks are stored as separate fields e.g. `{slot:0,item:{id:"stone"}}`.

### Block entity format


Main article: [Block entity format](https://minecraft.wiki/w/Block_entity_format "Block entity format")

Block entities are stored in the [NBT format](https://minecraft.wiki/w/NBT_format "NBT format"). While they still use NBT tags for their individual properties, any non-default data components that exist on the item used to place the block will be saved.

Some NBT data on block entities are treated as data components when transferring data between items and blocks. For example, the `Items` field in a chest is interpreted as the `minecraft:container` component, despite being labeled and structured differently.

* [NBT Compound / JSON Object] The root tag.

* + [String] id: Block entity ID
  + [Boolean] keepPacked: 1 or 0 (`true`/`false`) - If `true`, this is an invalid block entity, and this block is not immediately placed when a loaded chunk is loaded. If `false`, this is a normal block entity that can be immediately placed.
  + [Int] x: X coordinate of the block entity.
  + [Int] y: Y coordinate of the block entity.
  + [Int] z: Z coordinate of the block entity.
  + [NBT Compound / JSON Object] components: Optional map of data components that are not represented by additional fields.
    - See [Data component format § List of components](#List_of_components).
  + Additional tags depending on the block entity ID. See [Block entity format](https://minecraft.wiki/w/Block_entity_format "Block entity format").

For example, if a `chest` was given to a player with the components `minecraft:custom_data={foo:1}` and `minecraft:container=[{slot:0,item:{id:"stone"}}]]`, then placed the block on the ground, the block will be saved (omitting some fields) as:

`{id:"minecraft:chest", Items:[{count:1,id:"minecraft:stone",Slot:0b}], components:{"minecraft:custom_data":{foo:1}}}`

with `minecraft:container` saved as the `Items` tag, and `minecraft:custom_data` separated as it is not used by chest block entities.

## List of components


* [![](/images/ItemSprite_copper-spear.png?55458)](#attack_range)[attack\_range](#attack_range)
* [![](/images/BlockSprite_chain-command-block.png?0afa8)](#attribute_modifiers)[attribute\_modifiers](#attribute_modifiers)
* [![](/images/BlockSprite_white-banner.png?8b4d0)](#banner_patterns)[banner\_patterns](#banner_patterns)
* [![](/images/ItemSprite_shield.png?5aa3c)](#base_color)[base\_color](#base_color)
* [![](/images/BlockSprite_bee-nest.png?6c008)](#bees)[bees](#bees)
* [![](/images/BlockSprite_monster-spawner.png?81e6b)](#block_entity_data)[block\_entity\_data](#block_entity_data)
* [![](/images/BlockSprite_oak-stairs.png?b2ee6)](#block_state)[block\_state](#block_state)
* [![](/images/ItemSprite_shield.png?5aa3c)](#blocks_attacks)[blocks\_attacks](#blocks_attacks)
* [![](/images/ItemSprite_wooden-sword.png?fb7c0)](#break_sound)[break\_sound](#break_sound)
* [![](/images/ItemSprite_bucket-of-tropical-fish.png?57595)](#bucket_entity_data)[bucket\_entity\_data](#bucket_entity_data)
* [![](/images/ItemSprite_bundle.png?9eb9f)](#bundle_contents)[bundle\_contents](#bundle_contents)
* [![](/images/ItemSprite_stone-pickaxe.png?7a740)](#can_break)[can\_break](#can_break)
* [![](/images/BlockSprite_cobblestone.png?897e0)](#can_place_on)[can\_place\_on](#can_place_on)
* [![](/images/ItemSprite_crossbow.png?6a299)](#charged_projectiles)[charged\_projectiles](#charged_projectiles)
* [![](/images/ItemSprite_golden-apple.png?f22fc)](#consumable)[consumable](#consumable)
* [![](/images/BlockSprite_shulker-box.png?ed4f7)](#container)[container](#container)
* [![](/images/BlockSprite_chest.png?15d81)](#container_loot)[container\_loot](#container_loot)
* [![](/images/BlockSprite_barrier.png?8d91a)](#custom_data)[custom\_data](#custom_data)
* [![](/images/ItemSprite_diamond.png?8f019)](#custom_model_data)[custom\_model\_data](#custom_model_data)
* [![](/images/ItemSprite_name-tag.png?8de62)](#custom_name)[custom\_name](#custom_name)
* [![](/images/ItemSprite_iron-axe.png?51f8b)](#damage)[damage](#damage)
* [![](/images/ItemSprite_netherite-ingot.png?fb529)](#damage_resistant)[damage\_resistant](#damage_resistant)
* [![](/images/ItemSprite_stone-sword.png?1c050)](#damage_type)[damage\_type](#damage_type)
* [![](/images/ItemSprite_totem-of-undying.png?2aad1)](#death_protection)[death\_protection](#death_protection)
* [![](/images/ItemSprite_stick.png?3a040)](#debug_stick_state)[debug\_stick\_state](#debug_stick_state)
* [![](/images/ItemSprite_blue-dye.png?2b470)](#dye)[dye](#dye)
* [![](/images/ItemSprite_leather-tunic.png?99a6c)](#dyed_color)[dyed\_color](#dyed_color)
* [![](/images/ItemSprite_diamond-boots.png?a8ac4)](#enchantable)[enchantable](#enchantable)
* [![](/images/EntitySprite_eexperience-bottle.png?0cf33)](#enchantment_glint_override)[enchantment\_glint\_override](#enchantment_glint_override)
* [![](/images/ItemSprite_book.png?791a5)](#enchantments)[enchantments](#enchantments)
* [![](/images/ItemSprite_armor-stand.png?a9a9e)](#entity_data)[entity\_data](#entity_data)
* [![](/images/ItemSprite_saddle.png?f079a)](#equippable)[equippable](#equippable)
* [![](/images/ItemSprite_firework-star.png?011a4)](#firework_explosion)[firework\_explosion](#firework_explosion)
* [![](/images/ItemSprite_firework-rocket.png?9f724)](#fireworks)[fireworks](#fireworks)
* [![](/images/ItemSprite_steak.png?528f8)](#food)[food](#food)
* [![](/images/ItemSprite_elytra.png?047ea)](#glider)[glider](#glider)
* [![](/images/ItemSprite_goat-horn.png?e5a9f)](#instrument)[instrument](#instrument)
* [![](/images/ItemSprite_arrow.png?a9b69)](#intangible_projectile)[intangible\_projectile](#intangible_projectile)
* [![](/images/ItemSprite_emerald.png?14ced)](#item_model)[item\_model](#item_model)
* [![](/images/ItemSprite_name-tag.png?8de62)](#item_name)[item\_name](#item_name)
* [![](/images/ItemSprite_music-disc-5.png?0012d)](#jukebox_playable)[jukebox\_playable](#jukebox_playable)
* [![](/images/ItemSprite_iron-spear.png?a0090)](#kinetic_weapon)[kinetic\_weapon](#kinetic_weapon)
* [![](/images/BlockSprite_tripwire-hook.png?51ecf)](#lock)[lock](#lock)
* [![](/images/ItemSprite_lodestone-compass.png?e096c)](#lodestone_tracker)[lodestone\_tracker](#lodestone_tracker)
* [![](/images/ItemSprite_paper.png?565a1)](#lore)[lore](#lore)
* [![](/images/ItemSprite_map.png?05f8c)](#map_color)[map\_color](#map_color)
* [![](/images/ItemSprite_ocean-explorer-map.png?1c9f1)](#map_decorations)[map\_decorations](#map_decorations)
* [![](/images/ItemSprite_map.png?05f8c)](#map_id)[map\_id](#map_id)
* [![](/images/ItemSprite_diamond-axe.png?88cd2)](#max_damage)[max\_damage](#max_damage)
* [![](/images/ItemSprite_egg.png?2d314)](#max_stack_size)[max\_stack\_size](#max_stack_size)
* [![](/images/ItemSprite_stone-spear.png?dd810)](#minimum_attack_charge)[minimum\_attack\_charge](#minimum_attack_charge)
* [![](/images/BlockSprite_jukebox-side.png?8477e)](#note_block_sound)[note\_block\_sound](#note_block_sound)
* [![](/images/ItemSprite_ominous-bottle.png?2b418)](#ominous_bottle_amplifier)[ominous\_bottle\_amplifier](#ominous_bottle_amplifier)
* [![](/images/ItemSprite_diamond-spear.png?e0f60)](#piercing_weapon)[piercing\_weapon](#piercing_weapon)
* [![](/images/ItemSprite_danger-pottery-sherd.png?b8147)](#pot_decorations)[pot\_decorations](#pot_decorations)
* [![](/images/ItemSprite_water-bottle.png?fe7c2)](#potion_contents)[potion\_contents](#potion_contents)
* [![](/images/ItemSprite_lingering-water-bottle.png?b95e8)](#potion_duration_scale)[potion\_duration\_scale](#potion_duration_scale)
* [![](/images/BlockSprite_player-head.png?f544c)](#profile)[profile](#profile)
* [![](/images/ItemSprite_creeper-charge-banner-pattern.png?b4158)](#provides_banner_patterns)[provides\_banner\_patterns](#provides_banner_patterns)
* [![](/images/ItemSprite_raiser-armor-trim.png?6fd9b)](#provides_trim_material)[provides\_trim\_material](#provides_trim_material)
* [![](/images/ItemSprite_nether-star.png?afee9)](#rarity)[rarity](#rarity)
* [![](/images/ItemSprite_knowledge-book.png?4c237)](#recipes)[recipes](#recipes)
* [![](/images/EntitySprite_experience-orb.png?7ef2b)](#repair_cost)[repair\_cost](#repair_cost)
* [![](/images/BlockSprite_anvil.png?a26c9)](#repairable)[repairable](#repairable)
* [![](/images/ItemSprite_enchanted-book.png?b7877)](#stored_enchantments)[stored\_enchantments](#stored_enchantments)
* [![](/images/ItemSprite_bucket-of-sulfur-cube.png?cb304)](#sulfur_cube_content)[sulfur\_cube\_content](#sulfur_cube_content)​[*upcoming: [JE 26.2](https://minecraft.wiki/w/Java_Edition_26.2 "Java Edition 26.2")*]
* [![](/images/ItemSprite_suspicious-stew.png?2f0b4)](#suspicious_stew_effects)[suspicious\_stew\_effects](#suspicious_stew_effects)
* [![](/images/ItemSprite_netherite-spear.png?c24fc)](#swing_animation)[swing\_animation](#swing_animation)
* [![](/images/ItemSprite_diamond-shovel.png?3117b)](#tool)[tool](#tool)
* [![](/images/ItemSprite_item-frame.png?a577d)](#tooltip_display)[tooltip\_display](#tooltip_display)
* [![](/images/ItemSprite_painting.png?55d20)](#tooltip_style)[tooltip\_style](#tooltip_style)
* [![](/images/ItemSprite_spire-armor-trim.png?161f0)](#trim)[trim](#trim)
* [![](/images/BlockSprite_bedrock.png?75357)](#unbreakable)[unbreakable](#unbreakable)
* [![](/images/ItemSprite_ender-pearl.png?af209)](#use_cooldown)[use\_cooldown](#use_cooldown)
* [![](/images/ItemSprite_golden-spear.png?dbca7)](#use_effects)[use\_effects](#use_effects)
* [![](/images/ItemSprite_milk-bucket.png?634b5)](#use_remainder)[use\_remainder](#use_remainder)
* [![](/images/ItemSprite_diamond-sword.png?96eff)](#weapon)[weapon](#weapon)
* [![](/images/ItemSprite_book-and-quill.png?f190b)](#writable_book_content)[writable\_book\_content](#writable_book_content)
* [![](/images/ItemSprite_written-book.png?502b1)](#written_book_content)[written\_book\_content](#written_book_content)

### attack\_range


* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object] minecraft:attack\_range: Determines the [attack range](https://minecraft.wiki/w/Attack_range "Attack range") and [hitbox margin](https://minecraft.wiki/w/Hitbox_margin "Hitbox margin") of a weapon.
    - [Float] min\_reach: The minimum distance in blocks from the attacker to the target to be considered valid. Defaults to 0.0, valid from 0.0 to 64.0.
    - [Float] max\_reach: The maximum distance in blocks from the attacker to the target to be considered valid. Defaults to 3.0, valid from 0.0 to 64.0.
    - [Float] min\_creative\_reach: The minimum distance in blocks from the attacker to the target to be considered valid in [Creative](https://minecraft.wiki/w/Creative "Creative") mode. Defaults to 0.0, valid from 0.0 to 64.0.
    - [Float] max\_creative\_reach: The maximum distance in blocks from the attacker to the target to be considered valid in Creative mode. Defaults to 5.0, valid from 0.0 to 64.0.
    - [Float] hitbox\_margin: The margin applied to the target bounding box when checking for valid hitbox collision. Defaults to 0.3, valid from 0.0 to 1.0.
    - [Float] mob\_factor: The multiplier applied to `min_range` and `max_range` when checking for valid distance if item is used by a mob. Defaults to 1.0, valid from 0.0 to 2.0.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s diamond[attack_range={max_reach:5.0}]`

* Gives a diamond that has an attack range of 5 blocks.

### attribute\_modifiers


* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT List / JSON Array] minecraft:attribute\_modifiers: A list of [attribute modifiers](https://minecraft.wiki/w/Attribute_modifiers "Attribute modifiers") which, if present on an item, may be applied to a player or mob that has equipped the item. If the item is not in the correct equipment slot, it has no effect. The modifiers are removed from the entity once the item is moved out of that slot or is deleted. Any attribute modifiers specified are listed in the item's tooltip (unless hidden).
    - [NBT Compound / JSON Object]: A single attribute modifier and its tooltip display type.
      * [String] id: A [namespaced ID](https://minecraft.wiki/w/Namespaced_ID "Namespaced ID") to identify this modifier. It must be unique from other modifiers of the same attribute.
      * [String] type: The [namespaced ID](https://minecraft.wiki/w/Namespaced_ID "Namespaced ID") of the [attribute](https://minecraft.wiki/w/Attribute "Attribute") this modifier is to act upon.
      * [String] slot: The equipment slot/slots the item must be in for the modifier to take effect. Can be `any`, `hand`, `armor`, `mainhand`, `offhand`, `head`, `chest`, `legs`, `feet`, `body`, or `saddle`. Defaults to `any`. Note: `any` refers to any *equipment* slot, not any inventory slot.
      * [String] operation: Modifier operation. Can be `add_value`, `add_multiplied_base`, or `add_multiplied_total`. See [Attribute Modifiers](https://minecraft.wiki/w/Attribute#Modifiers "Attribute") for info.
      * [Double] amount: The value used in the modifier's operation.
      * [NBT Compound / JSON Object] display: How the modifier is displayed in an item's tooltip. Optional.
        + [String] type: Display type. Can be `default`, `hidden` or `override`.
        + [NBT Compound / JSON Object][NBT List / JSON Array][String] value (only present if [String] type is `override`): A [text component](https://minecraft.wiki/w/Text_component "Text component") to show for this attribute modifier entry.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s stick[attribute_modifiers=[{type:"minecraft:scale",slot:"hand",id:"example:grow",amount:4,operation:"add_multiplied_base"}]]`

* Gives a stick that causes the player to grow 4x when holding it.

### banner\_patterns


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT List / JSON Array] minecraft:banner\_patterns: List of all patterns applied to the banner or the shield. If used on a shield and the `[minecraft:base_color](#base_color)` component is not specified, then *white* is used as the base banner color.
    - [NBT Compound / JSON Object]: A single pattern.
      * [String] color: Dye color of the section.
      * [String][NBT Compound / JSON Object] pattern: One [banner pattern](https://minecraft.wiki/w/Banner_pattern_definition "Banner pattern definition") (an [String] [ID](https://minecraft.wiki/w/Resource_location "Resource location"), or a new [NBT Compound / JSON Object] banner pattern definition).

        + A banner pattern see [Template:Nbt inherit/banner pattern/template](https://minecraft.wiki/w/Template%3ANbt_inherit/banner_pattern/template "Template:Nbt inherit/banner pattern/template")

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s black_banner[banner_patterns=[{pattern:"triangle_top",color:"red"},{pattern:"cross",color:"white"}]]`

* Gives a black banner with a red triangle and white cross pattern.

### base\_color


* [NBT Compound / JSON Object] components: Parent tag.
  + [String] minecraft:base\_color: The base dye color of the banner applied on a shield. If neither this nor `[minecraft:banner_patterns](#banner_patterns)` is specified, then the shield model will show its normal wooden texture. If the `[minecraft:banner_patterns](#banner_patterns)` component is specified but this component is not, then *white* is used as the base banner color. If present on a [shield](https://minecraft.wiki/w/Shield "Shield") item, the item name is overridden as "<color> Shield" (e.g. if set to `green`, the name will be "Green Shield").

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s shield[base_color="lime"]`

* Gives a lime shield.

### bees


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT List / JSON Array] minecraft:bees: A list of the entities currently in the beehive or bee nest. If present on an item, text is added to the item's tooltip that says how many entries are in the list (e.g. if there are two entries, the tooltip will say "Bees: 2 / 3") and each item is considered a full stack for the [`minecraft:bundle_contents`](#bundle_contents) components. Despite the tooltip suggesting there is a maximum of 3 entries, there is no limit to the size of this component.
    - [NBT Compound / JSON Object]: A single entity.
      * [NBT Compound / JSON Object] entity\_data: Must include `id` tag. If the `id` is not `minecraft:bee` then the entity will never leave the hive. The `Passengers`, `Pos`, `Rotation`, and `UUID` tags are ignored when the bee spawns (the bee will always spawn in front of the hive with a random UUID, facing south, and without any passengers).
        + See [Entity format](https://minecraft.wiki/w/Entity_format "Entity format").
      * [Int] min\_ticks\_in\_hive: The minimum amount of time in ticks for this entity to stay in the hive.
      * [Int] ticks\_in\_hive: The amount of ticks the entity has stayed in the hive.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s bee_nest[bees=[{entity_data:{id:"bee",CustomName:"Maya"},min_ticks_in_hive:60,ticks_in_hive:0}]]`

* Gives a bee nest containing a single bee named *Maya*, which exits the bee nest in 3 seconds.

### block\_entity\_data


* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object] minecraft:block\_entity\_data: [Block entity](https://minecraft.wiki/w/Block_entity "Block entity") NBT applied when this block is placed. Depending on the block type that this item places, and the block entity ID specified in this component, this component may add a red message to the item's tooltip (for operator players only) warning the player that placing it may result in command execution.
    - See [Block entity format](https://minecraft.wiki/w/Block_entity_format "Block entity format"). Must include `id` tag. Excludes `x`, `y`, `z`, `components` and `keepPacked` tags.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s spawner[block_entity_data={id:"mob_spawner",SpawnData:{entity:{id:"spider"}}}]`

* Gives a spider spawner. Placing this spawner requires the player to have [operator permissions](https://minecraft.wiki/w/Permission_level "Permission level").

### block\_state


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:block\_state: The block state properties to apply when placing this block. When present on an item, regardless of the item type, if the `honey_level` property is specified then a gray "Honey: `<honey_level>` / 5" text is added to the tooltip.
    - [String] *<block state>*: A key-value pair, where the key is a block state key and the value is a block state value to force place for this block, for example `facing: "east"`.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s bamboo_slab[block_state={type:"top"}]`

* Gives a bamboo slab that is always placed in the top half of the block.

### blocks\_attacks


* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object] minecraft:blocks\_attacks: When present, this item can be used like a shield to block attacks to the holding player.
    - [Float] block\_delay\_seconds: The amount of time (in seconds) that use must be held before successfully blocking attacks. Defaults to `0`.
    - [Float] disable\_cooldown\_scale: The multiplier applied to the cooldown time for the item when attacked by a disabling attack (the multiplier for [Float] disable\_blocking\_for\_seconds on the [`minecraft:weapon`](#weapon) component). If set to `0`, this item can never be disabled by attacks. Defaults to `1`.
    - [NBT List / JSON Array] damage\_reductions: A set of rules for how much and what kinds damage should be blocked in a given attack. Defaults to `[{base:0,factor:1,horizontal_blocking_angle:90}]` which blocks all damage within a 90 degree angle.
      * [NBT Compound / JSON Object]: A damage reduction field
        + [String][NBT List / JSON Array] type: Any number of [damage type](https://minecraft.wiki/w/Damage_type "Damage type")(s) (an [String] [ID](https://minecraft.wiki/w/Resource_location "Resource location"), or a [String] [tag](https://minecraft.wiki/w/Tag "Tag") with `#`, or an [NBT List / JSON Array] array containing [String] IDs) to block. Defaults to all damage types.
        + [Float] base: The constant amount of damage to be blocked. This is a required field.
        + [Float] factor: The fraction of the dealt damage to be blocked. This is a required field.
        + [Float] horizontal\_blocking\_angle: strictly positive float — The maximum angle between the users facing direction and the direction of the incoming attack to be blocked. Defaults to `90`.
    - [NBT Compound / JSON Object] item\_damage: Controls how much damage should be applied to the item from a given attack.
      * [Float] threshold: The minimum amount of damage dealt by the attack before item damage is applied to the item. Defaults to `0`.
      * [Float] base: The constant amount of damage applied to the item, if threshold is passed. Defaults to `0`.
      * [Float] factor: The fraction of the dealt damage that should be applied to the item, if threshold is passed. Defaults to `1.5`.
    - [String][NBT Compound / JSON Object] block\_sound: One [sound event](https://minecraft.wiki/w/Sound_event "Sound event") (an [String] [ID](https://minecraft.wiki/w/Resource_location "Resource location"), or a new [NBT Compound / JSON Object] sound event definition) to play when an attack is successfully blocked. Defaults to none.

      * A sound event see [Template:Nbt inherit/sound event/template](https://minecraft.wiki/w/Template%3ANbt_inherit/sound_event/template "Template:Nbt inherit/sound event/template")
    - [String][NBT Compound / JSON Object] disabled\_sound: One [sound event](https://minecraft.wiki/w/Sound_event "Sound event") (an [String] [ID](https://minecraft.wiki/w/Resource_location "Resource location"), or a new [NBT Compound / JSON Object] sound event definition) to play when the item goes on its disabled cooldown due to an attack. Defaults to none.

      * A sound event see [Template:Nbt inherit/sound event/template](https://minecraft.wiki/w/Template%3ANbt_inherit/sound_event/template "Template:Nbt inherit/sound event/template")
    - [String] bypassed\_by: a damage type [tag](https://minecraft.wiki/w/Tag "Tag") with `#` of [damage types](https://minecraft.wiki/w/Damage_types "Damage types") that bypass the blocking. Defaults to none.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s diamond_sword[blocks_attacks={disable_cooldown_scale:0,damage_reductions:[{types:[mob_attack,arrow,explosion],base:0,factor:0.5}],block_sound:block.anvil.place}]`

* Gives a diamond sword that can block half of the damage from mob attacks, arrows, and explosions, cannot be disabled by a disabling attack, and plays the anvil place sound upon successful blocking.

### break\_sound


* [NBT Compound / JSON Object] components: Parent tag.

* + [String][NBT Compound / JSON Object] minecraft:break\_sound: One [sound event](https://minecraft.wiki/w/Sound_event "Sound event") (an [String] [ID](https://minecraft.wiki/w/Resource_location "Resource location"), or a new [NBT Compound / JSON Object] sound event definition) to play when the item runs out of durability and breaks.

    - A sound event see [Template:Nbt inherit/sound event/template](https://minecraft.wiki/w/Template%3ANbt_inherit/sound_event/template "Template:Nbt inherit/sound event/template")

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s diamond_sword[break_sound="item.wolf_armor.break"]`

* Gives a diamond sword that when runs out of durability, it plays the wolf armor break sound.

### bucket\_entity\_data


* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object] minecraft:bucket\_entity\_data: NBT applied to an [entity](https://minecraft.wiki/w/Entity "Entity") when placed from this bucket. Only tags below are applied.
    - [Boolean] NoAI: Turns into `NoAI` entity tag for all bucketable entities.
    - [Boolean] Silent: Turns into `Silent` entity tag for all bucketable entities.
    - [Boolean] NoGravity: Turns into `NoGravity` entity tag for all bucketable entities.
    - [Boolean] Glowing: Turns into `Glowing` entity tag for all bucketable entities.
    - [Boolean] Invulnerable: Turns into `Invulnerable` entity tag for all bucketable entities.
    - [Boolean] AgeLocked: Turns into `AgeLocked` entity tag for [axolotls](https://minecraft.wiki/w/Axolotl "Axolotl") and [tadpoles](https://minecraft.wiki/w/Tadpole "Tadpole").
    - [Float] Health: Turns into `Health` entity tag for all bucketable entities.
    - [Int] Age: Turns into `Age` entity tag for [axolotls](https://minecraft.wiki/w/Axolotl "Axolotl") and [tadpoles](https://minecraft.wiki/w/Tadpole "Tadpole").
    - [Long] HuntingCooldown: Turns into the expiry time of the memory module `has_hunting_cooldown` for [axolotls](https://minecraft.wiki/w/Axolotl "Axolotl").

Other tags such as the entity's name or variant are stored as separate item components such as `minecraft:custom_name` and `minecraft:tropical_fish/pattern`.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s axolotl_bucket[bucket_entity_data={Health:3.0f},axolotl/variant="wild",custom_name="Bob"]`

* Gives a bucket of axolotl that has 3 health, the [Wild](https://minecraft.wiki/w/Axolotl#Colors "Axolotl") type, and is named "Bob".

### bundle\_contents


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT List / JSON Array] minecraft:bundle\_contents: The items stored inside this [bundle](https://minecraft.wiki/w/Bundle "Bundle"). Adding this component to any item other than a bundle does nothing. If this component is removed from a [bundle](https://minecraft.wiki/w/Bundle "Bundle"), it cannot be used by the player and the usual instruction and fullness bar does not appear in the tooltip.
    - [NBT Compound / JSON Object]: A single item stack.

      * A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s bundle[bundle_contents=[{id:"diamond",count:2}]]`

* Gives a bundle containing exactly 2 diamonds.

### can\_break


When present, the player holding the item can break the specified blocks in [Adventure](https://minecraft.wiki/w/Adventure "Adventure") mode.

* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object][NBT List / JSON Array] minecraft:can\_break: The only blocks this item may break when used by a player in [Adventure](https://minecraft.wiki/w/Adventure "Adventure") mode. If defined as a compound, corresponds to [NBT Compound / JSON Object] A single block predicate. Items are listed in the tooltip in the order specified.
    - [NBT Compound / JSON Object]: A single block predicate.
      * [String][NBT List / JSON Array] blocks: Can be a single block ID, a list of block IDs, or a block tag with a `#`. The names of included blocks are displayed in the tooltip.
      * [NBT Compound / JSON Object] nbt: [Block entity](https://minecraft.wiki/w/Block_entity "Block entity") NBT to match. See [Block entity format](https://minecraft.wiki/w/Block_entity_format "Block entity format").
      * [NBT Compound / JSON Object] state: The block state properties to match.
        + [String] *<block state>*: A key-value pair, where the key is a block state key and the value is a block state value to match, for example `facing: "east"`.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s netherite_pickaxe[can_break={blocks:['black_concrete','coal_ore','iron_ore','gold_ore','diamond_ore','emerald_ore']}]`

* Gives a netherite pickaxe that can only mine some ores, as well as black concrete.

### can\_place\_on


When present, the player holding the item can place the held block item on any sides of the specified blocks in [Adventure](https://minecraft.wiki/w/Adventure "Adventure") mode.

* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object][NBT List / JSON Array] minecraft:can\_place\_on: Determines which blocks that blocks with this component can be placed against in [Adventure](https://minecraft.wiki/w/Adventure "Adventure") mode. If defined as a compound, corresponds to [NBT Compound / JSON Object] A single block predicate. Items are listed in the tooltip in the order specified.
    - [NBT Compound / JSON Object]: A single block predicate.
      * [String][NBT List / JSON Array] blocks: Can be a single block ID, a list of block IDs, or a block tag with a `#`. The names of included blocks are displayed in the tooltip.
      * [NBT Compound / JSON Object] nbt: [Block entity](https://minecraft.wiki/w/Block_entity "Block entity") NBT to match. See [Block entity format](https://minecraft.wiki/w/Block_entity_format "Block entity format").
      * [NBT Compound / JSON Object] state: The block state properties to match.
        + [String] *<block state>*: A key-value pair, where the key is a block state key and the value is a block state value to match, for example `facing: "east"`.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s target[can_place_on={blocks:'sandstone'}]`

* Gives a target block that can only be placed on sandstone.

### charged\_projectiles


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT List / JSON Array] minecraft:charged\_projectiles: The items loaded as projectiles into this crossbow. If there are item stacks in this component, the item name for item stack is listed in the tooltip of the item as "Projectile: [`<name>`]", and any duplicate item stack entries are grouped together as "Projectile: `N` x [`<name>`]". If not present, this crossbow is not charged.
    - [NBT Compound / JSON Object]: A single projectile item stack.

      * A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s crossbow[charged_projectiles=[{id:"spectral_arrow"}]]`

* Gives a crossbow that is already charged with a spectral arrow.

Note: Adding an invalid projectile or item id charges an arrow that, when collected, grants the wrong item. Ex: wind\_charge causes it to fire an arrow that grants a wind charge when collected.

### consumable


If present, the item can be consumed. Its options can also be modified.

* If the item already has an existing right-click functionality (like placing a block), it keeps that functionality.
* If the [`food`](#food), [`potion_contents`](#potion_contents), [`ominous_bottle_amplifier`](#ominous_bottle_amplifier) or [`suspicious_stew_effects`](#suspicious_stew_effects) components are also present on this item, consuming it applies the stats and effects of those components.
* If the [`food`](#food) component are also present on this item, [foxes](https://minecraft.wiki/w/Fox "Fox") consider the item as consumable food.

* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object] minecraft:consumable: If present, this item can be consumed on use.
    - [Float] consume\_seconds: The amount of seconds it takes for a player to consume the item. Defaults to 1.6.
    - [String] animation: The animation used during consumption of the item. Must be one of `none`, `eat`, `drink`, `block`, `bow`, `spear`, `crossbow`, `spyglass`, `toot_horn`, `brush`, `bundle`, or `trident`. Defaults to `eat`.
    - [String][NBT Compound / JSON Object] sound: One [sound event](https://minecraft.wiki/w/Sound_event "Sound event") (an [String] [ID](https://minecraft.wiki/w/Resource_location "Resource location"), or a new [NBT Compound / JSON Object] sound event definition) used during and on completion of the item's consumption. Defaults to `entity.generic.eat`.

      * A sound event see [Template:Nbt inherit/sound event/template](https://minecraft.wiki/w/Template%3ANbt_inherit/sound_event/template "Template:Nbt inherit/sound event/template")
    - [Boolean] has\_consume\_particles: Whether consumption particles are emitted while consuming this item. Defaults to `true`.
    - [NBT List / JSON Array] on\_consume\_effects: A list of effects which take place as a result of consuming this item. Optional.
      * [NBT Compound / JSON Object]: A single consume effect.

        + Consume effect see [Template:Nbt inherit/consume effect/template](https://minecraft.wiki/w/Template%3ANbt_inherit/consume_effect/template "Template:Nbt inherit/consume effect/template")

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s gold_ingot[consumable={consume_seconds:3.0, animation:'eat', sound:'entity.generic.eat', has_consume_particles:true, on_consume_effects:[{type:'minecraft:clear_all_effects'}]}]`

* Gives a gold ingot that can be eaten in 3 seconds and upon consuming, clears all effects.

### container


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT List / JSON Array] minecraft:container: The items contained in this [container](https://minecraft.wiki/w/Container "Container")'s slots. If present on an item, the first 5 item slots in the container are listed in the tooltip, and the number of any extra slots are listed as "*and `<N>` more...*" underneath (only seen on shulker boxes in normal gameplay or ctrl-middle-clicked containers in creative mode). This component supports up to 256 item slots but, when present on some block entities, the number of slots may be artificially limited based on the number of slots the block needs (e.g. 1 for decorated pots, and 27 for chests).
    - [NBT Compound / JSON Object]: A single item.
      * [NBT Compound / JSON Object] item: The item stack in this slot.

        + A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")
      * [Int] slot: A slot in this container. Can be from 0 to 255 (inclusive).

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s barrel[container=[{slot:0,item:{id:apple}}]]`

* Gives a barrel with an apple in the first slot.

### container\_loot


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:container\_loot: The unresolved loot table and seed of this container item.
    - [String] loot\_table: The ID of a [loot table](https://minecraft.wiki/w/Loot_table "Loot table").
    - [Long] seed: The pseudorandom seed to resolve the loot table with. If not specified or 0, a seed is randomly chosen by the game.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s chest[container_loot={loot_table:"chests/desert_pyramid"}]`

* Gives a chest that contains the desert pyramid loot when opened.

### custom\_data


* [NBT Compound / JSON Object] components: Parent tag.
  + [String][NBT Compound / JSON Object] minecraft:custom\_data: Contains key-value pairs of any custom data not used by the game, either as an object or a [SNBT](https://minecraft.wiki/w/SNBT "SNBT") string.
    - [Undefined] *<key>*: A key-value pair, where the value can have any data type, including another compound.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s iron_sword[custom_data={foo:1}]`

* Gives an iron sword with custom data `{foo:1}`.

### custom\_model\_data


* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object] minecraft:custom\_model\_data: A list of values used by [items model definitions](https://minecraft.wiki/w/Items_model_definition "Items model definition") for model selection and coloring.
    - [NBT List / JSON Array] floats: A list of [Float] floats for the `range_dispatch` model type. Missing values return the `fallback` model.
    - [Byte Array] flags: A list of [Boolean] booleans for the `condition` model type. Missing value returns the `is_false` model.
    - [NBT List / JSON Array] strings: A list of [String] strings for the `select` model type. Missing value returns the `fallback` model.
    - [NBT List / JSON Array][Int Array] colors: A list of RGB values for the `model` model type's `tints`. Missing values return the `default` value provided by the item model definition. Each entry can either be a list of floats or an integer. Any provided lists automatically convert to an integer, so the component is saved as an int array.
      * [Int]: An RGB color code converted to a decimal number. It can be calculated from the Red, Green and Blue components using this formula:
        **Red[<<](https://en.wikipedia.org/wiki/Logical_shift "wikipedia:Logical shift")16 + Green<<8 + Blue**

        An interactive widget is being loaded. If this does not work for you, please reload the page or check if JavaScript is working or enabled.
      * [NBT List / JSON Array]: A list containing 3 floats corresponding to red, green, and blue values as a fraction (ranged 0 to 1, inclusive). Automatically converted to the integer format when saved.

*Example:*

:   `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s bone[custom_model_data={floats:[4.0, 5.6, 99.1],strings:["foo:bar"],colors:[8323327, [0.5,0,1], 0x7F00FF]}]`

* Gives a bone with custom model data. The `colors` list shows three possible representations of the same violet color.

### custom\_name


Used to specify an item, block, or entity's custom name. This component can be added, changed, or removed by any player with the item who has access to an anvil.

* [NBT Compound / JSON Object] components: Parent tag.

* + [String][NBT List / JSON Array][NBT Compound / JSON Object] **minecraft:custom\_name**: The player-assigned name of this item, block, or entity, typically assigned with an [anvil](https://minecraft.wiki/w/Anvil "Anvil") or a [name tag](https://minecraft.wiki/w/Name_tag "Name tag"). See [Text component format](https://minecraft.wiki/w/Text_component_format "Text component format").
  + If present on an *item*, this component has highest priority to display as the item's name, and appears italic unless overridden by the text component format.
  + If present on an *entity*, it will replace the entity's name tag, will show the name tag to players when they hover over the entity (unless invisible), and will appear as that entity's name in commands and chat messages.
  + If present on a *block* with a GUI (such as a container), this replaces the name at the top of the GUI.
  + If present on a [command block](https://minecraft.wiki/w/Command_block "Command block"), this replaces the execution context name when the command is ran.

*Example:*

:   `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s stick[custom_name={text:"Magic Wand",color:"light_purple",italic:false}]`

* Gives a stick named "Magic Wand" in light purple non-italicized text.

### damage


* [NBT Compound / JSON Object] components: Parent tag.
  + [Int] minecraft:damage: The number of uses *consumed* (not remaining) of the item's [durability](https://minecraft.wiki/w/Durability "Durability"). Must be a non-negative integer, defaults to 0. If not present, the item cannot take damage. If this component is present on an item, its value is non-zero, the [`minecraft:max_damage`](#max_damage) is also present on the item, and the player hovering over the item has [advanced tooltips](https://minecraft.wiki/w/Advanced_tooltips "Advanced tooltips") on, then white text is added to the tooltip showing "Durability: `<durability>` / `<max_damage>`".

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s diamond_axe[damage=500]`

* Gives a diamond axe with 500 points of damage.

### damage\_resistant


* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object] minecraft:damage\_resistant: If specified, this item is invulnerable to the specified damage types when in [entity form](https://minecraft.wiki/w/Item_%28entity%29 "Item (entity)") or equipped.
    - [String] types: A [damage type tag](https://minecraft.wiki/w/Damage_type_tag_%28Java_Edition%29 "Damage type tag (Java Edition)") prefixed with `#`.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s cake[damage_resistant={types:"#minecraft:is_fire"}]`

* Gives a cake that is immune to all types of fire damage.

### damage\_type


* [NBT Compound / JSON Object] components: Parent tag.

* + [String] minecraft:damage\_type: Specifies the [damage type](https://minecraft.wiki/w/Damage_type "Damage type") this item deals

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s diamond_sword[damage_type="minecraft:campfire"]`

* Gives a diamond sword that deals "campfire" type damage.

### death\_protection


* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object] minecraft:death\_protection: If present, this item protects the holder from dying by restoring a single [health](https://minecraft.wiki/w/Health "Health") point.
    - [NBT List / JSON Array] death\_effects: A list of consume effects that are applied when the item protects the holder. Optional.
      * [NBT Compound / JSON Object]: A single consume effect.

        + Consume effect see [Template:Nbt inherit/consume effect/template](https://minecraft.wiki/w/Template%3ANbt_inherit/consume_effect/template "Template:Nbt inherit/consume effect/template")

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s nether_star[death_protection={death_effects:[{type:'minecraft:clear_all_effects'}]}]`

* Gives a nether star that protects the holder from death and removes all status effects from the holder.

### debug\_stick\_state


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:debug\_stick\_state: The selected block state properties used by this [debug stick](https://minecraft.wiki/w/Debug_stick "Debug stick").
    - [String] *<block ID>*: A key-value pair, where the key is a block ID and the value is a block state key to edit on the block, for example `"minecraft:oak_fence": "east"`.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s debug_stick[debug_stick_state={"minecraft:oak_fence": "west", "minecraft:candle": "lit"}]`

* Gives a debug stick with the [oak fence](https://minecraft.wiki/w/Oak_fence "Oak fence") block state property set to `west` and the [candle](https://minecraft.wiki/w/Candle "Candle") block state property set to `lit`.

### dye


* [NBT Compound / JSON Object] components: Parent tag.
  + [String] minecraft:dye: When present on an item, stores the color of dye that this item can be used as for the purpose of crafting recipes and mob or block interactions. Can be one of `white`, `orange`, `magenta`, `light_blue`, `yellow`, `lime`, `pink`, `gray`, `light_gray`, `cyan`, `purple`, `blue`, `brown`, `green`, `red`, or `black`.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s blue_dye[dye="red"]`

* Gives a blue dye item that acts like a red dye.

### dyed\_color


* [NBT Compound / JSON Object] components: Parent tag.
  + [Int] minecraft:dyed\_color: The RGB color of the tint applied to a dyed item, typically as a result of combining the item with dyes in a `minecraft:crafting_dyed` type crafting recipe. More generally, this component is used as the `minecraft:dye` color provider in [item model definitions](https://minecraft.wiki/w/Item_model_definition "Item model definition") (so only item models that explicitly use this color provider will be tinted). If present on an item, gray text is added to the tooltip showing either an italic "Dyed" when [advanced tooltips](https://minecraft.wiki/w/Advanced_tooltips "Advanced tooltips") is *off*, or a non-italic "Color: #`<hex color code>`"[[note 1]](#cite_note-1) instead when [advanced tooltips](https://minecraft.wiki/w/Advanced_tooltips "Advanced tooltips") is *on*. The color is stored as an integer which packs the color's red, green and blue channels using this formula:
    `(
     Red << 16) + (
     Green << 8) +
     Blue`[[note 2]](#cite_note-2)

    An interactive widget is being loaded. If this does not work for you, please reload the page or check if JavaScript is working or enabled.
  + [NBT List / JSON Array] minecraft:dyed\_color: An alternative format. A list of 3 floats, ranging from 0.0 to 1.0 (inclusive)[[note 3]](#cite_note-3), corresponding to the red, green and blue channels of the color. This format is automatically packed into the integer format by multiplying each float by 255, converting them to unsigned bytes (equivalent to taking the floor and then applying modulo 256), then using the formula `-16777216 + (
     Red << 16) + (
     Green << 8) +
     Blue` due to the alpha channel being implicitly set to 255, resulting in a negative integer.[[note 4]](#cite_note-4).

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s leather_helmet[dyed_color=8388403]`

*or:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s leather_helmet[dyed_color=0x7FFF33]`

*or:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s leather_helmet[dyed_color=[0.5, 1.0, 0.2]]`

* Gives a blueish-green leather helmet.

### enchantable


* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object] minecraft:enchantable: If this and `[minecraft:enchantments](#enchantments)` are present on an item, and applicable enchantments are available, the item can be enchanted in an enchanting table.
    - [Int] value: Positive integer representing the item's [enchantability](https://minecraft.wiki/w/Enchanting_mechanics#How_enchantments_are_chosen "Enchanting mechanics"). A higher value allows enchantments with a higher cost to be picked.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s elytra[enchantable={value:15}]`

* Gives a pair of elytra that can be enchanted in an enchanting table with an enchantability of 15.

### enchantment\_glint\_override


* [NBT Compound / JSON Object] components: Parent tag.
  + [Boolean] minecraft:enchantment\_glint\_override: Overrides the enchantment glint effect on this item. When `true`, this item displays a glint, even without enchantments. When `false`, this item does not display a glint, even with enchantments.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s experience_bottle[enchantment_glint_override=false]`

* Gives an experience bottle without the visual enchantment glint, which is otherwise applied by default.

### enchantments


* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object] minecraft:enchantments: Contains a map of each of this item's [enchantments](https://minecraft.wiki/w/Enchantment "Enchantment") to its enchantment level. This and `[minecraft:enchantable](#enchantable)` must exist on an item for it to be able to be enchanted in an enchanting table. If present on an item, the color of the item name is aqua if its rarity is `common` or `uncommon`, and light purple if its rarity is `rare` or `epic`. If present on an item, the enchantments are listed in the item's tooltip. The order of the enchantments in the tooltip is defined by the `[#minecraft:tooltip_order](https://minecraft.wiki/w/Enchantment_tag_%28Java_Edition%29#tooltip_order "Enchantment tag (Java Edition)")` enchantment tag.
    - [Int] *<enchantment ID>*: A single key-value pair, where the key is the [resource location](https://minecraft.wiki/w/Resource_location "Resource location") of an enchantment, and the value is the level.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s wooden_sword[enchantments={sharpness:3,knockback:2}]`

* Gives a wooden sword with sharpness III and knockback II.

*Note*: This component adds active enchantments and should not be confused with the [`stored_enchantments`](#stored_enchantments) component, which is used to add inactive enchantments, such as with [enchanted books](https://minecraft.wiki/w/Enchanted_Book "Enchanted Book").

To illustrate the difference, hitting an entity with an `enchanted_book[enchantments={knockback:2}]` would knock any entity hit per knockback II while hitting an entity with an `enchanted_book[stored_enchantments={knockback:2}]` would not.

Furthermore the latter would be able to add knockback II to an enchantable item in an anvil, while the former would not.

### entity\_data


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:entity\_data: NBT applied to an [entity](https://minecraft.wiki/w/Entity "Entity") when created from an item. Depending on the entity type that this item spawns, and the entity ID specified in this component, this component may add a red message to the item's tooltip (for operator players only) warning the player that using it may result in command execution.
    - See [Entity format](https://minecraft.wiki/w/Entity_format "Entity format"). Must include `id` tag. Excludes `UUID` and `Passengers`.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s armor_stand[entity_data={id:"armor_stand",Small:1b}]`

* Gives an armor stand that is small when placed down.

### equippable


* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object] minecraft:equippable: If present, this item can be equipped in the specified slot.
    - [String] slot: The slot to put the item on. Can be one of `head`, `chest`, `legs`, `feet`, `body`, `mainhand`, `offhand`, or `saddle`
    - [String][NBT Compound / JSON Object] equip\_sound: One [sound event](https://minecraft.wiki/w/Sound_event "Sound event") (an [String] [ID](https://minecraft.wiki/w/Resource_location "Resource location"), or a new [NBT Compound / JSON Object] sound event definition) to play when the item is equipped. Defaults to `item.armor.equip_generic`.

      * A sound event see [Template:Nbt inherit/sound event/template](https://minecraft.wiki/w/Template%3ANbt_inherit/sound_event/template "Template:Nbt inherit/sound event/template")
    - [String] asset\_id: The [resource location](https://minecraft.wiki/w/Resource_location "Resource location") of the [equipment model](https://minecraft.wiki/w/Equipment_model "Equipment model") to use when equipped. The directory this refers to is `assets/<namespace>/equipment/<id>.json`. If not specified, falls back to rendering as the item itself when in the head slot (if not applicable, the item does not render).
    - [String][NBT List / JSON Array] allowed\_entities: Entity ID, Entity Tag, or list of Entity IDs to limit which entities can equip this item. Defaults to all entities.
    - [Boolean] dispensable: Whether the item can be dispensed by using a [dispenser](https://minecraft.wiki/w/Dispenser "Dispenser").[[note 5]](#cite_note-5) Defaults to `true`.
    - [Boolean] swappable: Whether the item can be equipped into the relevant slot by right-clicking. Defaults to `true`.
    - [Boolean] damage\_on\_hurt: Whether this item is damaged when the wearing entity is damaged. Defaults to `true`.
    - [Boolean] equip\_on\_interact: Whether this item can be equipped onto a target mob by pressing use on it (as long as this item can be equipped on the target at all). Defaults to `false`.
    - [String] camera\_overlay: The [resource location](https://minecraft.wiki/w/Resource_location "Resource location") of the overlay texture to use when equipped. The directory this refers to is `assets/<namespace>/textures/<id>`. Assets which do not exist will use the [missing texture](https://minecraft.wiki/w/Missing_texture "Missing texture"), rather than falling back to a default such as the pumpkin overlay.
    - [Boolean] can\_be\_sheared: Whether this item can be unequipped from a target mob by right-clicking with Shears. Defaults to `false`.
    - [String][NBT Compound / JSON Object] shearing\_sound: One [sound event](https://minecraft.wiki/w/Sound_event "Sound event") (an [String] [ID](https://minecraft.wiki/w/Resource_location "Resource location"), or a new [NBT Compound / JSON Object] sound event definition) to play when the item is sheared. Defaults to `item.shears.snip`.

*Example 1:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s glass[equippable={slot:"head",equip_sound:"block.glass.break",dispensable:true}]`

* Gives a glass block that can be equipped in the helmet slot.

*Example 2:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s leather_leggings[equippable={slot:legs,asset_id:"minecraft:diamond"}]`

* Gives a pair of leather pants that appear as diamond leggings when worn.

### firework\_explosion


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:firework\_explosion: The explosion effect stored by this [firework star](https://minecraft.wiki/w/Firework_star "Firework star").
    - [String] shape: The shape of the explosion. Can be `small_ball`, `large_ball`, `star`, `creeper`, or `burst`.
    - [NBT List / JSON Array] colors: The colors of the initial particles of the explosion, randomly selected from.
      * [Int] A color as a packed integer
    - [NBT List / JSON Array] fade\_colors: The colors of the fading particles of the explosion, randomly selected from.
      * [Int] A color as a packed integer
    - [Boolean] has\_trail: Whether or not the explosion has a trail effect (diamond).
    - [Boolean] has\_twinkle: Whether or not the explosion has a twinkle effect (glowstone dust).

### fireworks


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:fireworks
    - [Byte] flight\_duration: The flight duration of this firework rocket (and the number of gunpowders used to craft it). Must be an integer between -128 and 127. Defaults to 1. If specified, gray "Flight Duration: `<flight_duration>`" text is added to the item's tooltip.
    - [NBT List / JSON Array] explosions: List of the explosion effects caused by this [firework rocket](https://minecraft.wiki/w/Firework_rocket "Firework rocket"). Has a maximum of 256 explosions. Each explosion is listed in the item's tooltip as its shape on the first line, then additional information such as color indented on further lines.
      * [NBT Compound / JSON Object]: A single explosion effect.
        + [String] shape: The shape of the explosion. Can be `small_ball`, `large_ball`, `star`, `creeper`, or `burst`.
        + [NBT List / JSON Array] colors: The colors of the initial particles of the explosion, randomly selected from.
          - [Int][NBT List / JSON Array] A color as a packed integer or list of three floats.
        + [NBT List / JSON Array] fade\_colors: The colors of the fading particles of the explosion, randomly selected from.
          - [Int][NBT List / JSON Array] A color as a packed integer or list of three floats.
        + [Boolean] has\_trail: Whether or not the explosion has a trail effect (diamond).
        + [Boolean] has\_twinkle: Whether or not the explosion has a twinkle effect (glowstone dust).

### food


If present and the [`consumable`](#consumable) component are also present on this item, [foxes](https://minecraft.wiki/w/Fox "Fox") consider the item as consumable food.

* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:food: The food stats applied to the mob or player upon consuming this item.
    - [Int] nutrition: The number of food points restored by this item when the player eats. The number of health points restored by this item when used to feed cats. Wolfs, nautilus and zombie nautilus restored the twice the value. Must be a non-negative integer.
    - [Float] saturation: The amount of saturation restored by this item when eaten.
    - [Boolean] can\_always\_eat: If `true`, this item can be eaten even if the player is not hungry. Defaults to `false`.

*Example 1:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s melon_slice[food={nutrition:3,saturation:1,can_always_eat:true}]`

* Gives a melon slice that can be eaten at any time and restores 3 food points and 1 saturation.

*Example 2:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s minecraft:sponge[consumable={consume_seconds:2.4},food={nutrition:5,saturation:5,can_always_eat:true}]`

* Gives a sponge that can be eaten at any time, takes 2.4 seconds to consume, and restores 5 food points and 5 saturation.

### glider


* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object] minecraft:glider: If present, this item allows living entities to glide (as with [elytra](https://minecraft.wiki/w/Elytra "Elytra")) when equipped. If the item is damageable, it will only allow entities to glide if it has [`minecraft:damage`](#damage) < [`minecraft:max_damage`](#max_damage) − 1. Every second while an entity is gliding, the game will select a random equipped glider item that isn't too damaged to function and try to apply one point of durability damage.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s nether_star[equippable={slot:"head"},glider={}]`

* Gives a nether star that can be equipped in the head slot, and if is placed on the head, it allows the player to glide.

### instrument


* [NBT Compound / JSON Object] components: Parent tag.

* + [String][NBT Compound / JSON Object] minecraft:instrument: One [instrument](https://minecraft.wiki/w/Instrument_definition "Instrument definition") (an [String] [ID](https://minecraft.wiki/w/Resource_location "Resource location"), or a new [NBT Compound / JSON Object] instrument definition). If present on an item, the description of the instrument is shown in the item's tooltip as gray text.

    There are actually two unique states of this component that both register in usage as the `minecraft:ponder_goat_horn` instrument ID, but they do not stack with each other, only one of them matches a component comparison for that ID, and only one of them gets serialised while the other does not.

    - [NBT Compound / JSON Object] description: A [text component](https://minecraft.wiki/w/Text_component "Text component") that is used as a description in tooltips.
    - [String][NBT Compound / JSON Object] sound\_event: One [sound event](https://minecraft.wiki/w/Sound_event "Sound event") (an [String] [ID](https://minecraft.wiki/w/Resource_location "Resource location"), or a new [NBT Compound / JSON Object] sound event definition)

      * A sound event see [Template:Nbt inherit/sound event/template](https://minecraft.wiki/w/Template%3ANbt_inherit/sound_event/template "Template:Nbt inherit/sound event/template")
    - [Float] use\_duration: A non-negative float for how long the use duration is.
    - [Float] range: A non-negative float for the range of the sound.

*Example 1:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s goat_horn[instrument="feel_goat_horn"]`

* Gives a [goat horn](https://minecraft.wiki/w/Goat_horn "Goat horn") that uses the *Feel* instrument.

*Example 2:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s goat_horn[instrument={description: "prank!", sound_event: "entity.creeper.primed", use_duration:2, range:30}]`

* Gives a goat horn that plays the *entity.creeper.primed* sound.

### intangible\_projectile


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:intangible\_projectile: If present on an item that can be used as a projectile without breaking upon impact (such as arrows and tridents), the projectile cannot be picked up by a player once fired, unless they are in [creative mode](https://minecraft.wiki/w/Creative_mode "Creative mode"). When present on any item, a line of gray text that says "Intangible" is added to the item's tooltip.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s arrow[intangible_projectile={}]`

* Gives an arrow that cannot be picked up by players in [Survival](https://minecraft.wiki/w/Survival "Survival") mode.

### item\_model


* [NBT Compound / JSON Object] components: Parent tag.

* + [String] minecraft:item\_model: The [resource location](https://minecraft.wiki/w/Resource_location "Resource location") of the item, which references the item model definition `/assets/<namespace>/items/<id>` without the `.json` suffix. Referencing nonexistent models will cause the [missing model](https://minecraft.wiki/w/Missing_model "Missing model") to be used, rather than falling back to the item ID's default model.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s netherite_sword[item_model="minecraft:diamond_sword"]`

* Gives a netherite sword that looks like a diamond sword.

### item\_name


* [NBT Compound / JSON Object] components: Parent tag.

* + [String][NBT List / JSON Array][NBT Compound / JSON Object] minecraft:item\_name: The default name of this item, as a [text component](https://minecraft.wiki/w/Text_component "Text component"), present on all items by default. Unlike the [`minecraft:custom_name`](#custom_name) component, this name cannot be erased using an anvil, is not italicized, and does not appear in some labels, such as banner markers and item frames.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s diamond[minecraft:item_name="Dirt"]`

* Gives a diamond that is named "Dirt".

### jukebox\_playable


* [NBT Compound / JSON Object] components: Parent tag.

* + [String] minecraft:jukebox\_playable: One [jukebox song](https://minecraft.wiki/w/Jukebox_song_definition "Jukebox song definition") (an [String] [ID](https://minecraft.wiki/w/Resource_location "Resource location")) to play when inserted into a jukebox. If present on an item, the item can be inserted into a [jukebox](https://minecraft.wiki/w/Jukebox "Jukebox") to play the specified song. If present on an item, the artist and the title of the song are added to the item's tooltip as gray text.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s diamond[minecraft:jukebox_playable="pigstep"]`

* Gives a diamond that plays Pigstep when inserted into a jukebox

### kinetic\_weapon


* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object] minecraft:kinetic\_weapon: Enables a charge-type attack when using the item where, while being used, the damage is dealt along a ray every tick based on the relative speed of the entities
    - [Int] delay\_ticks: The time in ticks required before weapon is effective. Defaults to 0.
    - [NBT Compound / JSON Object] damage\_conditions: The condition under which the charge attack deals damage.

      * Kinetic weapon conditions: see [Template:Nbt inherit/kinetic\_weapon\_conditions/template](https://minecraft.wiki/w/Template%3ANbt_inherit/kinetic_weapon_conditions/template "Template:Nbt inherit/kinetic weapon conditions/template")
    - [NBT Compound / JSON Object] dismount\_conditions: The condition under which the charge attack dismounts the target.

      * Kinetic weapon conditions: see [Template:Nbt inherit/kinetic\_weapon\_conditions/template](https://minecraft.wiki/w/Template%3ANbt_inherit/kinetic_weapon_conditions/template "Template:Nbt inherit/kinetic weapon conditions/template")
    - [NBT Compound / JSON Object] knockback\_conditions: The condition under which the charge attack deals knockback.

      * Kinetic weapon conditions: see [Template:Nbt inherit/kinetic\_weapon\_conditions/template](https://minecraft.wiki/w/Template%3ANbt_inherit/kinetic_weapon_conditions/template "Template:Nbt inherit/kinetic weapon conditions/template")
    - [Float] forward\_movement: The distance the item moves out of the wielder's hand during its animation. Defaults to 0.0.
    - [Float] damage\_multiplier: The multiplier for the final damage from the relative speed.[[note 6]](#cite_note-6) Defaults to 1.0.
    - [String][NBT Compound / JSON Object] sound: Optional [sound event](https://minecraft.wiki/w/Sound_event "Sound event") to play when the weapon is engaged.

      * A sound event see [Template:Nbt inherit/sound event/template](https://minecraft.wiki/w/Template%3ANbt_inherit/sound_event/template "Template:Nbt inherit/sound event/template")
    - [String][NBT Compound / JSON Object] hit\_sound: Optional [sound event](https://minecraft.wiki/w/Sound_event "Sound event") to play when the weapon hits an entity.

      * A sound event see [Template:Nbt inherit/sound event/template](https://minecraft.wiki/w/Template%3ANbt_inherit/sound_event/template "Template:Nbt inherit/sound event/template")

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s amethyst_shard[kinetic_weapon={forward_movement:0.0,delay_ticks:20,damage_conditions:{max_duration_ticks:60},knockback_conditions:{max_duration_ticks:40},dismount_conditions:{max_duration_ticks:20},hit_sound:"block.amethyst_cluster.step"}]`

* Gives an amethyst shard which can perform a charge attack after a 1-second delay. The attack can damage entities for 3 seconds, knock them back for the first 2 seconds and dismount them for the first second. Hitting a target with the attack plays an amethyst sound.

### lock


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:lock: An item predicate representing the "key" to open this container. If present on a block, players must have an item that passes this predicate in their main hand in order to open the container. If they do not, interacting with the container will play a sound and display a message in the actionbar.

    - item predicate see [Template:Nbt inherit/conditions/item/template](https://minecraft.wiki/w/Template%3ANbt_inherit/conditions/item/template "Template:Nbt inherit/conditions/item/template")

*Example 1:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @p chest[minecraft:lock={components:{"minecraft:item_model":"minecraft:diamond"}}]`

* Gives a chest that is locked, opening only if the player is holding an item with the same model as a Diamond.

*Example 2:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @p furnace[minecraft:lock={components:{"minecraft:custom_name":"Furnace Key"}}]`

* Gives a furnace that opens only if the player is holding an item with the custom name "Furnace Key".

*Example 3:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @p barrel[minecraft:lock={items:["minecraft:oak_planks","minecraft:diamond"],count:6,predicates:{custom_data:{bar:foo}}}]`

* Gives a barrel that opens only if the player is holding exactly 6 [oak planks](https://minecraft.wiki/w/Planks#Oak "Planks") or 6 [diamonds](https://minecraft.wiki/w/Diamond "Diamond") that has the custom data `bar:foo`

### lodestone\_tracker


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:lodestone\_tracker: Stores information about the [lodestone](https://minecraft.wiki/w/Lodestone "Lodestone") this [compass](https://minecraft.wiki/w/Compass "Compass") should point toward. If present on a compass item, the base item name will be overridden as "Lodestone Compass". While `tracked` in a player's inventory, a compass with this component will do active polling to see if the position of its lodestone is loaded, and if it is and the lodestone has been destroyed then this component is removed.
    - [NBT Compound / JSON Object] target: Information about the lodestone. Optional. If not set, this compass spins randomly.
      * [Int Array] pos: The integer coordinates of the lodestone.
      * [String] dimension: The ID of the dimension of the lodestone.
    - [Boolean] tracked: If `true`, the component is removed when the lodestone is broken. If `false`, the component is kept. Defaults to `true`.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s compass[minecraft:lodestone_tracker={target:{pos:[I;1,2,3],dimension:"overworld"}}]`

* Gives a compass that points toward a lodestone that is located in the Overworld at x=1,y=2,z=3

### lore


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT List / JSON Array] minecraft:lore: List of additional lines to display in this item's tooltip. Has a maximum of 256 lines.
    - [String][NBT List / JSON Array][NBT Compound / JSON Object]: Text component representing a line of text. See [Text component format](https://minecraft.wiki/w/Text_component_format "Text component format").

*Example 1:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @p stick[lore=[{text:"This Stick is very sticky."}]]`

* Gives a stick with lore in its tooltip.

*Example 2:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @p diamond[lore=[{text:"A shiny Diamond!",italic:false,color:"gold"}]]`

* Gives a diamond that has lore in its tooltip. The color of the lore is gold, and its italics have been removed.

*Example 3:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @p emerald[lore=[{text:"A shiny Emerald!","italic":false,"color":"gold"}, {text:"Maybe share it with a friend?",italic:false,color:"yellow"}]]`

* Gives an emerald that has 2 lines of lore in its tooltip. The first line has a golden color, and the second has a yellow color. Both lines have had their italics removed.

### map\_color


* [NBT Compound / JSON Object] components: Parent tag.
  + [Int] minecraft:map\_color: The color code for the `minecraft:map_color` color provider in [item model definitions](https://minecraft.wiki/w/Items_model_definition "Items model definition"). Normally used by the `minecraft:filled_map` item model.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s filled_map[map_color=16711680]`

* Gives a filled map with red markings on item texture.

An interactive widget is being loaded. If this does not work for you, please reload the page or check if JavaScript is working or enabled.

### map\_decorations


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:map\_decorations: Contains key-value pairs of the icons to display on this [filled map](https://minecraft.wiki/w/Filled_map "Filled map").
    - [NBT Compound / JSON Object] *<key>*: The key-value pair of a single icon, where the key is an arbitrary unique string identifying the decoration.
      * [String] type: The type of the icon. Can be `player`, `frame`, `red_marker`, `blue_marker`, `target_x`, `target_point`, `player_off_map`, `player_off_limits`, `mansion`, `monument`, `banner_white`, `banner_orange`, `banner_magenta`, `banner_light_blue`, `banner_yellow`, `banner_lime`, `banner_pink`, `banner_gray`, `banner_light_gray`, `banner_cyan`, `banner_purple`, `banner_blue`, `banner_brown`, `banner_green`, `banner_red`, `banner_black`, `red_x`, `village_desert`, `village_plains`, `village_savanna`, `village_snowy`, `village_taiga`, `jungle_temple`, or `swamp_hut`.
      * [Double] x: The X world coordinate of the decoration.
      * [Double] z: The Z world coordinate of the decoration.
      * [Float] rotation: The rotation of the icon, ranging from 0.0 to 360.0, rotated clockwise from north in degrees.

### map\_id


* [NBT Compound / JSON Object] components: Parent tag.
  + [Int] minecraft:map\_id: The [number](https://minecraft.wiki/w/Map_item_format#Data_folder_structure "Map item format") of this [filled map](https://minecraft.wiki/w/Filled_map "Filled map"), representing the shared state holding map contents and markers.

### max\_damage


* [NBT Compound / JSON Object] components: Parent tag.

* + [Int] minecraft:max\_damage: The maximum amount of damage that this item can take. If not set, this item cannot take damage. Must be a non-zero positive integer. Cannot be combined with `[minecraft:max_stack_size](#max_stack_size)` if it has a value greater than 1 (if the item can be stacked). For the durability bar to appear, the damage component must have a value. Example `damage=0`.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s diamond_pickaxe[max_damage=4]`

* Gives a diamond pickaxe that can only be used 4 times before breaking.

### max\_stack\_size


* [NBT Compound / JSON Object] components: Parent tag.
  + [Int] minecraft:max\_stack\_size: The maximum number of items that can fit in a stack. Must be a positive integer between 1 and 99 (inclusive). If it has a value greater than 1 (if the item can be stacked), cannot be combined with `[minecraft:max_damage](#max_damage)`. If this component is removed, it will behave as though it was set to 1.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s acacia_boat[max_stack_size=64] 5`

* Gives a stack of 5 acacia boats all in a single slot.

### minimum\_attack\_charge


* [NBT Compound / JSON Object] components: Parent tag.

* + [Float] minecraft:minimum\_attack\_charge: Sets the minimum attack charge on the attack indicator required to attack with this item. Must be a non-negative float between 0.0 and 1.0

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s diamond_sword[minimum_attack_charge=0.5] 1`

* Gives a diamond sword that can only attack once the attack indicator is at least half full.

### note\_block\_sound


* [NBT Compound / JSON Object] components: Parent tag.
  + [String] minecraft:note\_block\_sound: The ID of the sound event played by a note block when this [player head](https://minecraft.wiki/w/Player_head "Player head") is placed above.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @p minecraft:player_head[minecraft:profile=minecraftWiki,minecraft:note_block_sound=entity.item.pickup]`

* Gives a Player Head of the minecraftWiki. If placed on a Note Block, the Note Block plays the "Item Pickup" sound every time it's activated.

### ominous\_bottle\_amplifier


* [NBT Compound / JSON Object] components: Parent tag.
  + [Int] minecraft:ominous\_bottle\_amplifier: The amplifier of the [Bad Omen](https://minecraft.wiki/w/Bad_Omen "Bad Omen") effect given to the player or mob upon consuming this item (normally an [ominous bottle](https://minecraft.wiki/w/Ominous_bottle "Ominous bottle")). Must be a non-negative integer from 0 to 4 (inclusive). The duration of the effect is always 120000 ticks (1 hour and 40 minutes at the normal tick rate) and `[minecraft:potion_duration_scale](#potion_duration_scale)` is ignored. If present on an item, information about the mob effect is added to the tooltip, in the same format as the `[minecraft:potion_contents](#potion_contents)` component.

### piercing\_weapon


* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object] minecraft:piercing\_weapon: Melee attacks using this item damage multiple entities along a ray, instead of only a single entity. Also prevents this item from being used to mine blocks.
    - [Boolean] deals\_knockback: Whether the attack deals knockback. Defaults to true.
    - [Boolean] dismounts: Whether the attack dismounts the target. Defaults to false.
    - [String][NBT Compound / JSON Object] sound: Optional [sound event](https://minecraft.wiki/w/Sound_event "Sound event") to play when a player attacks with the weapon.

      * A sound event see [Template:Nbt inherit/sound event/template](https://minecraft.wiki/w/Template%3ANbt_inherit/sound_event/template "Template:Nbt inherit/sound event/template")
    - [String][NBT Compound / JSON Object] hit\_sound: Optional [sound event](https://minecraft.wiki/w/Sound_event "Sound event") to play when the weapon hits an entity.

      * A sound event see [Template:Nbt inherit/sound event/template](https://minecraft.wiki/w/Template%3ANbt_inherit/sound_event/template "Template:Nbt inherit/sound event/template")

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s minecraft:blaze_rod[minecraft:piercing_weapon={sound:"entity.blaze.hurt",hit_sound:"entity.lightning_bolt.impact"}]`

* Gives a blaze rod which whose melee attack pierces targets, dealing 1 damage to each, with fiery and explosive sounds accompanying the attacks.

### pot\_decorations


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT List / JSON Array] minecraft:pot\_decorations: A list of the items (typically pottery sherds or bricks) applied on each face of this [decorated pot](https://minecraft.wiki/w/Decorated_pot "Decorated pot"). If the list is specified with less than 4 entries, the remaining ones default to `"minecraft:brick"`. The first entry is the front face of the pot, and subsequent entries are the faces going clockwise around the pot. If this component is present on an item, the item's tooltip will list the translated names of each of the items in the same order.
    - [String]: The ID of an item. Can be either `brick` or a [sherd](https://minecraft.wiki/w/Sherd "Sherd").

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s decorated_pot[pot_decorations=["skull_pottery_sherd","heart_pottery_sherd","blade_pottery_sherd","brick"]]`

* Gives a [decorated pot](https://minecraft.wiki/w/Decorated_pot "Decorated pot") with sherds: skull, heart and blade on its faces

### potion\_contents


* [NBT Compound / JSON Object] components: Parent tag.

* + [String][NBT Compound / JSON Object] minecraft:potion\_contents: The base potion, custom list of [mob effects](https://minecraft.wiki/w/Mob_effects "Mob effects"), and custom color contained in this [potion](https://minecraft.wiki/w/Potion "Potion"), [splash potion](https://minecraft.wiki/w/Splash_potion "Splash potion"), [lingering potion](https://minecraft.wiki/w/Lingering_potion "Lingering potion"), [tipped arrow](https://minecraft.wiki/w/Tipped_arrow "Tipped arrow"), or [area effect cloud](https://minecraft.wiki/w/Area_effect_cloud "Area effect cloud"). When present on an item, the [mob effects](https://minecraft.wiki/w/Mob_effects "Mob effects") are listed in the item's tooltip. If this and a `[minecraft:consumable](#consumable)` component are present on an item, consuming the item will apply all of the effects from this component to the player or mob that consumed it. If defined as a string, corresponds to [String] potion.

    - A custom potion contents object see [Template:Nbt inherit/potion\_contents/template](https://minecraft.wiki/w/Template%3ANbt_inherit/potion_contents/template "Template:Nbt inherit/potion contents/template")

An interactive widget is being loaded. If this does not work for you, please reload the page or check if JavaScript is working or enabled.

### potion\_duration\_scale


* [NBT Compound / JSON Object] components: Parent tag.

* + [Float] minecraft:potion\_duration\_scale: When present on an item or [area effect cloud](https://minecraft.wiki/w/Area_effect_cloud "Area effect cloud") that has the [`minecraft:potion_contents`](#potion_contents) component, the duration of the applied effects is scaled by this factor.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @p potion[potion_contents={potion:swiftness},potion_duration_scale=2]`

* Gives a Potion of Swiftness that has its default time doubled from 3 Minutes to 6 Minutes.

### profile


* [NBT Compound / JSON Object] components: Parent tag.

* + [String][NBT Compound / JSON Object] minecraft:profile: Provides the textures needed for rendering player models ([player head](https://minecraft.wiki/w/Player_head "Player head") blocks, [player head](https://minecraft.wiki/w/Player_head "Player head") item models, and [mannequins](https://minecraft.wiki/w/Mannequin "Mannequin")) and [player face sprites](https://minecraft.wiki/w/Text_component##Player_Object_Type "Text component"). Each texture can be provided either as the namespaced path to a texture in a resource pack, or from a player profile. A player profile can be specified either as player information whose profile properties must be requested on the fly, or a list of already-resolved profile properties.
  + If specified as a string, it corresponds to [String] name.
  + If present on a *player head* item, and the [String] name field is specified, the base item name is overridden as "`name`'s Head".
  + If present on any item, *exactly one* of either [String] name or [Int Array] id is specified, and [NBT List / JSON Array] properties is not specified, a gray "Dynamic" text is shown in the item's tooltip.

    - [String] name: A username with a maximum length of 16, and only consisting of username-allowed characters​[*[more information needed](https://minecraft.wiki/w/Special%3ATalkPage/Data_component_format "Special:TalkPage/Data component format")*]. If no other profile fields are specified, this is used to dynamically request the profile of a player with that username from Mojang's servers. Once received, that profile's properties (such as its skin, cape, and elytra textures) can be used for rendering. If the profile does not exist, a random default skin is provided. Optional.
    - [Int Array] id: A [UUID](https://minecraft.wiki/w/UUID "UUID"). If no other profile fields are specified, this is used to dynamically request the profile of a player with that UUID from Mojang's servers. Once received, that profile's properties (such as its skin, cape, and elytra textures) can be used for rendering. If the profile does not exist, a random default skin is provided. Optional.
    - [NBT List / JSON Array] properties: A non-empty list of user profile properties. If this is specified, the dynamic profile fields are ignored, and a custom profile with these properties is used instead. If set to an empty list, the field is removed rather than invalidating the whole component. Optional.
      * [NBT Compound / JSON Object]: A single property.
        + [String] name: The name of the property. Can only be `"textures"`.
        + [String] value: The [texture data json](https://minecraft.wiki/w/Mojang_API#Query_player's_skin_and_cape "Mojang API"), encoded in [base64](https://en.wikipedia.org/wiki/base64 "wikipedia:base64").
        + [String] signature: Optional. Mojang's [signature](https://en.wikipedia.org/wiki/Digital_signature "wikipedia:Digital signature") of the value, encoded in base64.
    - [String] texture: Namespaced path to a player skin texture, relative to the `textures` folder in a resource pack. If specified, this texture is used when rendering a player model or skin, overriding the skin texture provided by a profile. This skin texture may have transparent pixels on the inner body layers whereas resolved skins' are always opaque. If omitted and no skin is provided by a profile, the slim [Alex](https://minecraft.wiki/w/Alex "Alex") skin is used (`minecraft:entity/player/slim/alex`). Optional.
    - [String] cape: Namespaced path to a [cape](https://minecraft.wiki/w/Cape "Cape") texture, relative to the `textures` folder in a resource pack. If specified, this texture is used when rendering a cape, overriding the cape texture provided by a profile. If the resolved profile (or lack thereof) does not have a cape, it will gain one. This does not affect the elytra texture. If Optional.
    - [String] elytra: Namespaced path to an [elytra](https://minecraft.wiki/w/Elytra "Elytra") texture, relative to the `textures` folder in a resource pack. If specified, this texture is used when rendering an elytra, overriding the elytra texture provided by a profile. This does not affect the cape texture. If omitted and no elytra texture is provided by a profile, the normal elytra texture is used (`minecraft:entity/equipment/wings/elytra`). Optional.
    - [String] model: The type of player model to use. Either `"wide"` or `"slim"`. If specified, this overrides the model type provided by a profile. If omitted and no model type is provided by a profile, a `slim` model type is used. Optional.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @p player_head[profile=MinecraftWiki]`

* Gives a player head of MinecraftWiki.

An interactive widget is being loaded. If this does not work for you, please reload the page or check if JavaScript is working or enabled.

### provides\_banner\_patterns


* [NBT Compound / JSON Object] components: Parent tag.

* + [String] minecraft:provides\_banner\_patterns: When present, this item can be placed in the pattern slot of a loom and provides the specified banner pattern tag. Must be a tag prefixed with `#`.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @p diamond[provides_banner_patterns='#minecraft:pattern_item/globe']`

* Gives a diamond that can provide the globe banner pattern to a banner.

### provides\_trim\_material


* [NBT Compound / JSON Object] components: Parent tag.

* + [String] minecraft:provides\_trim\_material: When present, this item provides the specified trim material when used in a trimming recipe.[[note 7]](#cite_note-7)

### rarity


* [NBT Compound / JSON Object] components: Parent tag.
  + [String] minecraft:rarity: Sets the [rarity](https://minecraft.wiki/w/Rarity "Rarity") of this item, which affects the default color of its name. Can be `common`, `uncommon`, `rare`, or `epic`. If this component does not exist on the item, then `common` is used.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @p iron_sword[rarity=epic]`

* Gives an iron sword with a light purple name.

### recipes


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT List / JSON Array] minecraft:recipes: The recipes that a player unlocks when this [knowledge book](https://minecraft.wiki/w/Knowledge_book "Knowledge book") is used.
    - [String]: The ID of a [recipe](https://minecraft.wiki/w/Recipe "Recipe").

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @p knowledge_book[recipes=["minecraft:end_crystal","minecraft:diamond","minecraft:stone_sword","minecraft:blast_furnace"]]`

* Gives a knowledge book that, when used, gives the player the recipes listed inside the component.

### repair\_cost


* [NBT Compound / JSON Object] components: Parent tag.
  + [Int] minecraft:repair\_cost: The number of experience levels to add to the base level cost when repairing, combining, or renaming this item with an [anvil](https://minecraft.wiki/w/Anvil "Anvil"). Must be a non-negative integer, defaults to 0.

### repairable


* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object] minecraft:repairable: Allows the item to be repaired, if damageable, in an anvil using the specified ingredient. Also repairs equipped items in the body slot of a tamed wolf.
    - [String][NBT List / JSON Array] items: Item, list of Items, or hash-prefixed Item Tag matching what can be used to repair this item.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @p diamond_sword[repairable={items:"stick"}]`

* Gives a diamond sword that can be repaired with sticks in an anvil.

### stored\_enchantments


* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object] minecraft:stored\_enchantments: Contains a map of inactive [enchantments](https://minecraft.wiki/w/Enchantment "Enchantment") and their levels. Adding this component to any item other than an [enchanted book](https://minecraft.wiki/w/Enchanted_book "Enchanted book") does nothing except add text to the item's tooltip. If this component is removed from an enchanted book, the item can no longer be combined with other enchanted books. If present on an item, the enchantments are listed in the item's tooltip. The order of the enchantments in the tooltip is defined by the `[#minecraft:tooltip_order](https://minecraft.wiki/w/Enchantment_tag_%28Java_Edition%29#tooltip_order "Enchantment tag (Java Edition)")` enchantment tag.
    - [Int] *<enchantment ID>*: A single key-value pair, where the key is the [resource location](https://minecraft.wiki/w/Resource_location "Resource location") of an enchantment, and the value is the level.

### sulfur\_cube\_content


[![](/images/thumb/Crafting_Table_JE4_BE3.png/16px-Crafting_Table_JE4_BE3.png?5767f)](https://minecraft.wiki/w/File%3ACrafting_Table.png "File:Crafting Table.png")

This section describes content that is currently in development for *[Java Edition](https://minecraft.wiki/w/Java_Edition "Java Edition")*.

This content has appeared in development versions for [Java Edition 26.2](https://minecraft.wiki/w/Java_Edition_26.2 "Java Edition 26.2"), but the full update adding it has not been released yet.

* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] sulfur\_cube\_content: The item stored inside the [sulfur cube](https://minecraft.wiki/w/Sulfur_cube "Sulfur cube"). When present on a sulfur cube entity, this component doubles as the `armor.body` slot (`body` equipment slot). When present on an item, gray italic text is added to the tooltip that says "Contains: `<item>`".

    - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")

### suspicious\_stew\_effects


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT List / JSON Array] minecraft:suspicious\_stew\_effects: A list of unamplified [mob effects](https://minecraft.wiki/w/Mob_effects "Mob effects") given to the player or mob upon consuming this item (normally a [suspicious stew](https://minecraft.wiki/w/Suspicious_stew "Suspicious stew")). `[minecraft:potion_duration_scale](#potion_duration_scale)` is ignored. When present on an item, text is added to the item's tooltip only when it is inside of the [item selection screen](https://minecraft.wiki/w/Creative_inventory "Creative inventory").
    - [NBT Compound / JSON Object]: A single custom effect.
      * [String] id: The ID of the effect.
      * [Int] duration: The duration of the effect in [ticks](https://minecraft.wiki/w/Tick "Tick"). Defaults to 160.

### swing\_animation


* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object] minecraft:swing\_animation: Allows modification of the swinging animation.
    - [String] type: The type of swinging animation. Can be `none`, `whack`, `stab`. Defaults to `whack`.
    - [Int] duration: A positive integer that determines the animation's duration in [ticks](https://minecraft.wiki/w/Tick "Tick"). Defaults to `6`.

### tool


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:tool: If set, this item is considered as a [tool](https://minecraft.wiki/w/Tool "Tool").
    - [Float] default\_mining\_speed: The default mining speed of this tool, used if no rules override it. Defaults to 1.0.
    - [Int] damage\_per\_block: The amount of durability to remove each time a block is broken with this tool. Must be a non-negative integer. Defaults to 1.
    - [Boolean] can\_destroy\_blocks\_in\_creative: Whether players can break blocks while holding this tool in Creative mode. Defaults to `true`.
    - [NBT List / JSON Array] rules: A list of rules for the blocks that this tool has a special behavior with. If a field is overridden by multiple matched rules, the one that comes first in the list is chosen.
      * [NBT Compound / JSON Object]: A single rule.
        + [String][NBT List / JSON Array] blocks: The blocks to match with. Can be a block ID or a block tag with a `#`, or a list of block IDs.
        + [Float] speed: If the blocks match, overrides the default mining speed. Optional.
        + [Boolean] correct\_for\_drops: If the blocks match, overrides whether or not this tool is considered correct to mine at its most efficient speed, and to drop items if the block's loot table requires it. If not set by any rules, defaults to `false`. Optional.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @p oak_fence[max_stack_size=1,max_damage=350,damage=0,tool={default_mining_speed:1.5,damage_per_block:2,rules:[{blocks:"#mineable/pickaxe",speed:6,correct_for_drops:true}]}]`

* Gives an oak fence that has the properties of a pickaxe.

### tooltip\_display


* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object] minecraft:tooltip\_display: Allows the tooltips provided specifically by any given item component to be suppressed.
    - [Boolean] hide\_tooltip: If true, the item has no tooltip when hovered.
    - [NBT List / JSON Array] hidden\_components: The tooltips provided by any component in this list are hidden. If that component provides no tooltip, it has no effect.
      * [String]: The [resource location](https://minecraft.wiki/w/Resource_location "Resource location") of a component

*Example 1:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @p diamond_sword[tooltip_display={hidden_components:["minecraft:enchantments"]},enchantments={sharpness:1}]`

* Gives a diamond sword that is enchanted with Sharpness I, but doesn't show the enchantments in the tooltip.

*Example 2:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @p diamond_sword[tooltip_display={hide_tooltip:1b}]`

* Gives a diamond sword that when hovered, it shows no tooltip at all.

### tooltip\_style


* [NBT Compound / JSON Object] components: Parent tag.

* + [String] minecraft:tooltip\_style: The [resource location](https://minecraft.wiki/w/Resource_location "Resource location") of the custom sprites for the [tooltip](https://minecraft.wiki/w/Tooltip "Tooltip") background and frame which references textures `/assets/<namespace>/textures/gui/sprites/tooltip/<id>_background` and `/assets/<namespace>/textures/gui/sprites/tooltip/<id>_frame`. Instead of falling back to the default value, invalid specifications will use the [missing texture](https://minecraft.wiki/w/Missing_texture "Missing texture").

### trim


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:trim: Contains the trim applied to this [armor](https://minecraft.wiki/w/Armor "Armor") piece. If present on an item, information about the armor trim is added to the item's tooltip.
    - [String] pattern: The ID of the trim pattern.
    - [String] material: The ID of the trim material, which applies a color to the trim.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @p minecraft:leather_leggings[trim={"pattern":"host","material":"emerald"}] 1`

* Gives [leather pants](https://minecraft.wiki/w/Leather_pants "Leather pants") with the "host" pattern made of emerald.

### unbreakable


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:unbreakable: If present on an item, the item cannot lose durability, its durability bar is hidden, and a blue "Unbreakable" text is added to its tooltip.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @p` `wooden_spear[unbreakable={}]`

### use\_cooldown


* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object] minecraft:use\_cooldown: If present, this item applies a [use cooldown](https://minecraft.wiki/w/Use_cooldown "Use cooldown") to all items of the same type when it has been used.
    - [Float] seconds: The use cooldown duration in seconds.
    - [String] cooldown\_group: The unique [resource location](https://minecraft.wiki/w/Resource_location "Resource location") to identify this cooldown group. If present, the item is included in a use cooldown group and no longer shares cooldowns with its base item type, but instead with any other items that are part of the same use cooldown group. Optional.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @p ender_pearl[use_cooldown={seconds:10,cooldown_group:"foo:bar"}]`

* Gives an ender pearl that has a 10 second cooldown after being used, and also applies that cooldown to *any* item that shares its `cooldown_group`.
  + If other items in the inventory share the same `cooldown_group`, but have different `seconds`, then using that item applies the `seconds` of *itself* to all other items in the inventory, rather than each item applying their own `seconds` to themselves.
* Items can have their cooldowns disabled completely by removing the component with `[!use_cooldown]`.

### use\_effects


* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object] minecraft:use\_effects: Defines the vibrations and player movement penalties when an item with a continuous use action is being used.
    - [Boolean] can\_sprint: If the player can sprint during use. Defaults to `false`.
    - [Float] speed\_multiplier: A ranged float (0.0-1.0 inclusive) speed multiplier inflicted during use. Defaults to `0.2`.
    - [Boolean] interact\_vibrations: Whether using this item emits the `minecraft:item_interact_start` and `minecraft:item_interact_finish` [game events](https://minecraft.wiki/w/Game_event "Game event"). Defaults to `true`.

### use\_remainder


* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object] minecraft:use\_remainder: If present, replaces the item with a remainder item if its stack count has decreased after use.

    - A single item stack see [Template:Nbt inherit/itemnoslot/template](https://minecraft.wiki/w/Template%3ANbt_inherit/itemnoslot/template "Template:Nbt inherit/itemnoslot/template")

*Example 1:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @p splash_potion[use_remainder={id:"minecraft:gunpowder"}]`

* Gives a splash potion, which after being thrown, leaves gunpowder.

*Example 2:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @p cooked_chicken[use_remainder={id:"minecraft:bone",components:{custom_name:{text:"Chicken Bone"}},count:2}]`

* Gives a cooked chicken, which after being used, turns into 2 bones named "Chicken Bone".

### weapon


If present, the item acts as a weapon. For attack damage see the [`attribute_modifiers`](#attribute_modifiers) component.

* [NBT Compound / JSON Object] components: Parent tag.

* + [NBT Compound / JSON Object] minecraft:weapon: When present, the specified amount of damage can be done to the item with each attack. Additionally, the 'Item Used' statistic is incremented for each attack with the item.
    - [Int] item\_damage\_per\_attack: The amount to damage the item for each attack performed. Defaults to `1`.
    - [Float] disable\_blocking\_for\_seconds: The amount of seconds that this item can disable a blocking shield on successful attack. If set to 0, this item cannot disable a blocking shield. Defaults to `0`.

*Example 1:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @p minecraft:stick[weapon={},max_damage=10,max_stack_size=1,damage=0]`

* Gives a stick that has 10 durability, and loses 1 durability for each attack performed.

*Example 2:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @p iron_sword[minecraft:weapon={disable_blocking_for_seconds:5,item_damage_per_attack:10}]`

* Gives an iron sword that disables shields for 5 seconds when used on them, but loses 10 durability for each attack performed.

### writable\_book\_content


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:writable\_book\_content: The contents of this [book and quill](https://minecraft.wiki/w/Book_and_quill "Book and quill"). Adding this component to any item other than a `writable_book` does nothing. If this component is removed from a `writable_book` item, attempting to use the item will still swing the arm and increment its `used` statistic, but no UI will appear.
    - [NBT List / JSON Array] pages: A list of the pages in the book.
      * [String][NBT Compound / JSON Object] title: The title of this written book. If set to a string, it corresponds to [String] raw.
        + [String] raw: The plain text content of the page.
        + [String] filtered: The filtered text of the page. Optional. Shown only to players with chat filter enabled, instead of [String] raw.

### written\_book\_content


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:written\_book\_content: The contents and metadata of this [written book](https://minecraft.wiki/w/Written_book "Written book"). Adding this component to any item other than a `written_book` does nothing except add text to the item tooltip. If this component is removed from a `written_book` item, attempting to use the item will still swing the arm and increment its `used` statistic, but no UI will appear.
    - [NBT List / JSON Array] pages: A list of the pages in the book.
      * [NBT Compound / JSON Object] or [String][NBT List / JSON Array][NBT Compound / JSON Object]: A single page. If set to a string, list, or compound with no `raw` or `filtered` tags in it, it corresponds to [String][NBT List / JSON Array][NBT Compound / JSON Object] raw.
        + [String][NBT List / JSON Array][NBT Compound / JSON Object] raw: A [text component](https://minecraft.wiki/w/Text_component "Text component") representing the text content of the page. See [Text component format](https://minecraft.wiki/w/Text_component_format "Text component format").
        + [String][NBT List / JSON Array][NBT Compound / JSON Object] filtered: A [text component](https://minecraft.wiki/w/Text_component "Text component") representing the filtered text of the page. Optional. Shown only to players with chat filter enabled, instead of [String] raw.
    - [String][NBT Compound / JSON Object] title: The title of this written book. Overrides the base item name. If set to an empty string, it is ignored and does not override the base item name. If set to a string, it corresponds to [String] raw.
      * [String] raw: The plain text title. Has a maximum length of 32 characters.
      * [String] filtered: The filtered title. Optional. Shown only to players with chat filter enabled, instead of [String] raw.
    - [String] author: The author of this written book. This is shown in the item tooltip.
    - [Int] generation: The number of times this written book has been copied. 0 = original, 1 = copy of original, 2 = copy of copy, 3 = tattered. Defaults to 0. If the value is greater than 1, the book cannot be copied. If specified, this is shown in the item tooltip.
    - [Boolean] resolved: If `true`, the [text components](https://minecraft.wiki/w/Text_component "Text component") have already been resolved by the server. If `false`, they are resolved either when the book is opened by an operator, when the book is placed into a lectern by an operator, or when the item stack is written to a lectern's `Book` tag by a command. Defaults to `false`.

## Entity variant components


[![](/images/thumb/Gear_icon.png/16px-Gear_icon.png?94611)](https://minecraft.wiki/w/File%3AGear_icon.png "File:Gear icon.png")

This section is a work in progress.

Please help [expand and improve](https://minecraft.wiki/w/Special%3AEditPage/Data_component_format "Special:EditPage/Data component format") it. The [talk page](https://minecraft.wiki/w/Special%3ATalkPage/Data_component_format "Special:TalkPage/Data component format") may contain suggestions.
**Note:**

Add more information about entity variant components (in general)

Entity variant components are a group of components that are present in items like spawn eggs, mob buckets, paintings, item frames, etc. These components modify some of the properties of the entity stored within those items.

Here is a list of all entity variant components:

* [![](/images/EntitySprite_axolotl.png?0b5f0)](#axolotl/variant)[axolotl/variant](#axolotl/variant)
* [![](/images/EntitySprite_cat.png?b3c67)](#cat/collar)[cat/collar](#cat/collar)
* [![](/images/EntitySprite_cat.png?b3c67)](#cat/variant)[cat/variant](#cat/variant)
* [![](/images/EntitySprite_chicken.png?be6aa)](#chicken/variant)[chicken/variant](#chicken/variant)
* [![](/images/EntitySprite_cow.png?893cf)](#cow/variant)[cow/variant](#cow/variant)
* [![](/images/EntitySprite_fox.png?91c80)](#fox/variant)[fox/variant](#fox/variant)
* [![](/images/EntitySprite_frog.png?15793)](#frog/variant)[frog/variant](#frog/variant)
* [![](/images/EntitySprite_creamy-horse.png?3d52b)](#horse/variant)[horse/variant](#horse/variant)
* [![](/images/EntitySprite_creamy-llama.png?0657f)](#llama/variant)[llama/variant](#llama/variant)
* [![](/images/EntitySprite_mooshroom.png?92493)](#mooshroom/variant)[mooshroom/variant](#mooshroom/variant)
* [![](/images/EntitySprite_kebab.png?c74c1)](#painting/variant)[painting/variant](#painting/variant)
* [![](/images/EntitySprite_parrot.png?8ab80)](#parrot/variant)[parrot/variant](#parrot/variant)
* [![](/images/EntitySprite_pig.png?5435e)](#pig/variant)[pig/variant](#pig/variant)
* [![](/images/EntitySprite_brown-rabbit.png?18569)](#rabbit/variant)[rabbit/variant](#rabbit/variant)
* [![](/images/EntitySprite_salmon.png?d308d)](#salmon/size)[salmon/size](#salmon/size)
* [![](/images/EntitySprite_sheep.png?bd14e)](#sheep/color)[sheep/color](#sheep/color)
* [![](/images/EntitySprite_shulker.png?ca1f9)](#shulker/color)[shulker/color](#shulker/color)
* [![](/images/EntitySprite_tropical-fish.png?ee953)](#tropical_fish/base_color)[tropical\_fish/base\_color](#tropical_fish/base_color)
* [![](/images/EntitySprite_tropical-fish.png?ee953)](#tropical_fish/pattern)[tropical\_fish/pattern](#tropical_fish/pattern)
* [![](/images/EntitySprite_tropical-fish.png?ee953)](#tropical_fish/pattern_color)[tropical\_fish/pattern\_color](#tropical_fish/pattern_color)
* [![](/images/EntitySprite_villager.png?05433)](#villager/variant)[villager/variant](#villager/variant)
* [![](/images/EntitySprite_wolf.png?77c1e)](#wolf/collar)[wolf/collar](#wolf/collar)
* [![](/images/EntitySprite_wolf.png?77c1e)](#wolf/sound_variant)[wolf/sound\_variant](#wolf/sound_variant)
* [![](/images/EntitySprite_wolf.png?77c1e)](#wolf/variant)[wolf/variant](#wolf/variant)

### axolotl/variant


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:axolotl/variant: `lucy`, `wild`, `gold`, `cyan`, or `blue` — The variant of the [axolotl](https://minecraft.wiki/w/Axolotl "Axolotl")

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s axolotl_spawn_egg[axolotl/variant="blue"]`

* Gives a axolotl spawn egg that spawns a blue axolotl.

### cat/collar


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:cat/collar: A [dye color](https://minecraft.wiki/w/Dye#Color_values "Dye") — The color of the collar of the cat

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s cat_spawn_egg[cat/collar="blue"]`

* Gives a cat spawn egg that spawns a cat with a blue collar (once tamed).

### cat/variant


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:cat/variant: One [cat variant](https://minecraft.wiki/w/Cat_variant_definition "Cat variant definition") (an [String] [ID](https://minecraft.wiki/w/Resource_location "Resource location")) — The variant of the cat

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s cat_spawn_egg[cat/variant="jellie"]`

* Gives a cat spawn egg that spawns a Jellie (gray and white) cat.

### chicken/variant


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:chicken/variant: One [chicken variant](https://minecraft.wiki/w/Chicken_variant_definition "Chicken variant definition") (an [String] [ID](https://minecraft.wiki/w/Resource_location "Resource location")) — The variant of the chicken

*Example 1:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s chicken_spawn_egg[chicken/variant="cold"]`

* Gives a chicken spawn egg that spawns a cold chicken.

*Example 2:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s egg[chicken/variant="cold"]`

* Gives an egg that has a chance to hatch a cold chicken.

### cow/variant


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:cow/variant: One [cow variant](https://minecraft.wiki/w/Cow_variant_definition "Cow variant definition") (an [String] [ID](https://minecraft.wiki/w/Resource_location "Resource location")) — The variant of the cow

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s cow_spawn_egg[cow/variant="cold"]`

* Gives a cow spawn egg that spawns a cold cow.

### fox/variant


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:fox/variant: `red` or `snow` — The variant of the [fox](https://minecraft.wiki/w/Fox "Fox")

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s fox_spawn_egg[fox/variant="snow"]`

* Gives a fox spawn egg that spawns a snow fox.

### frog/variant


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:frog/variant: One [frog variant](https://minecraft.wiki/w/Frog_variant_definition "Frog variant definition") (an [String] [ID](https://minecraft.wiki/w/Resource_location "Resource location")) — The variant of the frog

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s frog_spawn_egg[frog/variant="cold"]`

* Gives a frog spawn egg that spawns a cold frog.

### horse/variant


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:horse/variant: `white`, `creamy`, `chestnut`, `brown`, `black`, `gray`, or `dark_brown` — The variant of the [horse](https://minecraft.wiki/w/Horse "Horse")

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s horse_spawn_egg[horse/variant="chestnut"]`

* Gives a horse spawn egg that spawns a chestnut horse.

### llama/variant


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:llama/variant: `creamy`, `white`, `brown`, or `gray` — The variant of the [llama](https://minecraft.wiki/w/Llama "Llama")

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s llama_spawn_egg[llama/variant="gray"]`

* Gives a llama spawn egg that spawns a gray llama.

### mooshroom/variant


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:mooshroom/variant: `red` or `brown` — The variant of the [mooshroom](https://minecraft.wiki/w/Mooshroom "Mooshroom")

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s mooshroom_spawn_egg[mooshroom/variant="brown"]`

* Gives a mooshroom spawn egg that spawns a brown mooshroom.

### painting/variant


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:painting/variant: One [painting variant](https://minecraft.wiki/w/Painting_variant_definition "Painting variant definition") (an [String] [ID](https://minecraft.wiki/w/Resource_location "Resource location")) — The variant of the [painting](https://minecraft.wiki/w/Painting "Painting"). If present on an item, the item's tooltip will display: the painting's name (in yellow), the artist's name (in gray), and the painting's width & height in blocks (in white). Not all paintings have an artist attributed to them.

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s painting[painting/variant="plant"]`

* Gives a painting that places the "Paradisträd" painting.

### parrot/variant


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:parrot/variant: `red_blue`, `blue`, `green`, `yellow_blue`, or `gray` — The variant of the [parrot](https://minecraft.wiki/w/Parrot "Parrot")

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s parrot_spawn_egg[parrot/variant="blue"]`

* Gives a parrot spawn egg that spawns a blue parrot.

### pig/variant


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:pig/variant: One [pig variant](https://minecraft.wiki/w/Pig_variant_definition "Pig variant definition") (an [String] [ID](https://minecraft.wiki/w/Resource_location "Resource location")) — The variant of the pig

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s pig_spawn_egg[pig/variant="warm"]`

* Gives a pig spawn egg that spawns a warm pig.

### rabbit/variant


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:rabbit/variant: `brown`, `white`, `black`, `white_splotched`, `gold`, `salt`, or `evil` — The variant of the [rabbit](https://minecraft.wiki/w/Rabbit "Rabbit")

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s rabbit_spawn_egg[rabbit/variant="evil"]`

* Gives a rabbit spawn egg that spawns an evil rabbit.

### salmon/size


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:salmon/size: `small`, `medium`, `large` — The size of the [salmon](https://minecraft.wiki/w/Salmon "Salmon")

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s salmon_spawn_egg[salmon/size="large"]`

* Gives a salmon spawn egg that spawns a large salmon.

### sheep/color


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:sheep/color: A [dye color](https://minecraft.wiki/w/Dye#Color_values "Dye") — The color of the wool of the [sheep](https://minecraft.wiki/w/Sheep "Sheep")

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s sheep_spawn_egg[sheep/color="blue"]`

* Gives a sheep spawn egg that spawns a sheep with blue wool.

### shulker/color


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:shulker/color: A [dye color](https://minecraft.wiki/w/Dye#Color_values "Dye") — The color the [shulker](https://minecraft.wiki/w/Shulker "Shulker")

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s shulker_spawn_egg[shulker/color="red"]`

* Gives a shulker spawn egg that spawns a red shulker.

### tropical\_fish/base\_color


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:tropical\_fish/base\_color: A [dye color](https://minecraft.wiki/w/Dye#Color_values "Dye") — The base color of the [tropical fish](https://minecraft.wiki/w/Tropical_fish "Tropical fish")

### tropical\_fish/pattern


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:tropical\_fish/pattern: `kob`, `sunstreak`, `snooper`, `dasher`, `brinely`, `spotty`, `flopper`, `stripey`, `glitter`, `blockfish`, `betty`, or `clayfish` — The pattern of the [tropical fish](https://minecraft.wiki/w/Tropical_fish "Tropical fish")

### tropical\_fish/pattern\_color


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:tropical\_fish/pattern\_color: A [dye color](https://minecraft.wiki/w/Dye#Color_values "Dye") — The pattern color of the [tropical fish](https://minecraft.wiki/w/Tropical_fish "Tropical fish")

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s tropical_fish_spawn_egg[tropical_fish/pattern="snooper", tropical_fish/base_color="red", tropical_fish/pattern_color="blue"]`

* Gives a tropical fish spawn egg that spawns a red-blue snooper tropical fish.

### villager/variant


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:villager/variant: `desert`, `jungle`, `plains`, `savanna`, `snow`, `swamp`, or `taiga` — The variant of the [villager](https://minecraft.wiki/w/Villager "Villager")

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s villager_spawn_egg[villager/variant="desert"]`

* Gives a villager spawn egg that spawns a desert villager.

### wolf/collar


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:wolf/collar: A [dye color](https://minecraft.wiki/w/Dye#Color_values "Dye") — The color of the collar of the [wolf](https://minecraft.wiki/w/Wolf "Wolf")

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s wolf_spawn_egg[wolf/collar="blue"]`

* Gives a wolf spawn egg that spawns a wolf with a blue collar (when tamed).

### wolf/sound\_variant


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:wolf/sound\_variant: wolf sound variant definition — The sound variant of the [wolf](https://minecraft.wiki/w/Wolf "Wolf")

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s wolf_spawn_egg[wolf/sound_variant="cute"]`

* Gives a wolf spawn egg that spawns a cute wolf.

### wolf/variant


* [NBT Compound / JSON Object] components: Parent tag.

  + [String] minecraft:wolf/variant: One [wolf variant](https://minecraft.wiki/w/Wolf_variant_definition "Wolf variant definition") (an [String] [ID](https://minecraft.wiki/w/Resource_location "Resource location")) — The variant of the [wolf](https://minecraft.wiki/w/Wolf "Wolf")

*Example:* `/[give](https://minecraft.wiki/w/Commands/give "Commands/give") @s wolf_spawn_egg[wolf/variant="rusty"]`

* Gives a wolf spawn egg that spawns a rusty wolf.

## Non-encoded components


These data components exist and are used by the game internally, but are not encoded on items. Therefore, they cannot be used in commands, nor seen with `/[data](https://minecraft.wiki/w/Commands/data "Commands/data")`.

### additional\_trade\_cost


* [NBT Compound / JSON Object] components: Parent tag.
  + [Int] minecraft:additional\_trade\_cost: Used on the `gives` item of a [villager trade](https://minecraft.wiki/w/Villager_trade_definition "Villager trade definition") to add to the `count` of the `wants` item.

### creative\_slot\_lock


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:creative\_slot\_lock: Only used internally to lock the informational [paper](https://minecraft.wiki/w/Paper "Paper") items in the [creative inventory](https://minecraft.wiki/w/Creative_inventory "Creative inventory"). If set, this item cannot be taken out of its slot.

### map\_post\_processing


* [NBT Compound / JSON Object] components: Parent tag.
  + [Int] minecraft:map\_post\_processing: Only used internally when this [filled map](https://minecraft.wiki/w/Filled_map "Filled map") has been duplicated or locked in a [crafting table](https://minecraft.wiki/w/Crafting_table "Crafting table") or a [cartography table](https://minecraft.wiki/w/Cartography_table "Cartography table"). Can be 0 (lock) or 1 (scale), adding the "Locked" line or "Scale" line in this item's tooltip, respectively.

## Exclusive to joke versions


The following components were added and used in [April Fools' Day joke](https://minecraft.wiki/w/April_Fools%27_Day_jokes "April Fools' Day jokes") snapshots.

### [24w14potato](https://minecraft.wiki/w/24w14potato "24w14potato")


List of the components

#### clicks


* [NBT Compound / JSON Object] components: Parent tag.
  + [Int] minecraft:clicks: The number of times this [poisonous potato plant](https://minecraft.wiki/w/Poisonous_potato_plant "Poisonous potato plant") has been clicked in the inventory.

#### contacts\_messages


* [NBT Compound / JSON Object] components: Parent tag.
  + [Long Array] minecraft:contacts\_messages: Used by the [poisonous potato plant](https://minecraft.wiki/w/Poisonous_potato_plant "Poisonous potato plant").

#### explicit\_foil


* [NBT Compound / JSON Object] components: Parent tag.
  + [Boolean] minecraft:explicit\_foil: Whether or not this item should display a glint.

#### fletching


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:fletching: Information about this [fletching table](https://minecraft.wiki/w/Fletching_table "Fletching table").
    - [String] quality: A single character defining the quality of this block.
    - [String] impurities: A single character defining the impurity of this block.
    - [String] next\_level\_impurities: A single character defining the impurity of the next level of this block.
    - [Short] processs\_time [*[sic](https://en.wikipedia.org/wiki/Sic)*]: The process time of this block, in ticks.
    - [Boolean] explored: Whether this block has been explored.

#### heat


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:heat: Information about this [hot potato](https://minecraft.wiki/w/Hot_potato "Hot potato").
    - [Int] heat: The amount of heat. Has a maximum value of 200.
    - [Int] slot: The inventory slot this item is in.
    - [Int Array] owner: The UUID of the entity currently holding this item.

#### hovered


* [NBT Compound / JSON Object] components: Parent tag.
  + [Boolean] minecraft:hovered: Whether or not this [poisonous potato plant](https://minecraft.wiki/w/Poisonous_potato_plant "Poisonous potato plant") is the last item stack hovered in the inventory.

#### lubrication


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:lubrication
    - [Int] level: The level of slipperiness this item has when thrown on the ground.

#### potato\_bane


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:potato\_bane: Used by the [potato peeler](https://minecraft.wiki/w/Potato_peeler "Potato peeler").
    - [Float] damage\_boost: The amount of bonus damage applied to potato mobs.

#### resin


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:resin: Information about this [toxic resin](https://minecraft.wiki/w/Toxic_resin "Toxic resin").
    - [String] quality: A single character defining the quality of this item. Used to prefix the "Clarity" line on the tooltip.
    - [String] impurities: A single character defining the impurity of this item. Used to prefix the "Impurities" line on the tooltip.

#### secret\_message


* [NBT Compound / JSON Object] components: Parent tag.
  + [Long] minecraft:secret\_message: Used by the [poisonous potato plant](https://minecraft.wiki/w/Poisonous_potato_plant "Poisonous potato plant").

#### snek


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:snek: Information about this [snektato](https://minecraft.wiki/w/Snektato "Snektato").
    - [Boolean] revealed: Whether or not this item has been eaten yet. When `true`, its name is "Venomous Potato" and its texture is different.

#### undercover\_id


* [NBT Compound / JSON Object] components: Parent tag.
  + [Int] minecraft:undercover\_id: Used by the [poisonous potato plant](https://minecraft.wiki/w/Poisonous_potato_plant "Poisonous potato plant").

#### views


* [NBT Compound / JSON Object] components: Parent tag.
  + [Int] minecraft:views: Used by the [poisonous potato plant](https://minecraft.wiki/w/Poisonous_potato_plant "Poisonous potato plant").

#### xp


* [NBT Compound / JSON Object] components: Parent tag.
  + [Int] minecraft:xp: The amount of experience points granted by this [potato of knowledge](https://minecraft.wiki/w/Potato_of_knowledge "Potato of knowledge").

### [25w14craftmine](https://minecraft.wiki/w/25w14craftmine "25w14craftmine")


List of the components

#### dimension\_id


* [NBT Compound / JSON Object] components: Parent tag.
  + [String] minecraft:dimension\_id: The resource location of the dimension this [mine](https://minecraft.wiki/w/Mine_%28item%29 "Mine (item)") item will teleport the player to when placed on a [mine revisitor](https://minecraft.wiki/w/Mine_revisitor "Mine revisitor") and used.

#### exchange\_value


* [NBT Compound / JSON Object] components: Parent tag.
  + [Float] minecraft:exchange\_value: The value of the item, which is used to determine how much experience the player gains from it when exiting a mine.

#### instant\_room


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:instant\_room: The room this [shimmering key](https://minecraft.wiki/w/Shimmering_key "Shimmering key") opens.
    - [String] structure: The resource location of the structure. The key can only open a room if a structure file with the specified name exists inside the `hub/room/` folder under the specified namespace in a [data pack](https://minecraft.wiki/w/Data_pack "Data pack").

#### mine\_active


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:mine\_active: Is set on the [mine](https://minecraft.wiki/w/Mine_%28item%29 "Mine (item)") item in the [mine crafter](https://minecraft.wiki/w/Mine_crafter "Mine crafter") when the player is inside a mine.

#### mine\_completed


* [NBT Compound / JSON Object] components: Parent tag.
  + [Boolean] minecraft:mine\_completed: Whether the mine this [mine](https://minecraft.wiki/w/Mine_%28item%29 "Mine (item)") item refers to was completed. Determines the color of the glint on the item (green if completed, red if failed).

#### mob\_trophy/type


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:mob\_trophy/type: Information about this [mob trophy](https://minecraft.wiki/w/Mob_trophy "Mob trophy").
    - [Boolean] shiny: Whether the mob inside this mob trophy has an enchantment glint on it. Also adds the text "Oooh, shiny!" to the tooltip.
    - [String] type: The resource location for the entity type inside this mob trophy.

#### sky


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:sky: Information about this [sky box](https://minecraft.wiki/w/Sky_box "Sky box").
    - [String] type: The type of sky that [sky](https://minecraft.wiki/w/Sky_%28block%29 "Sky (block)") blocks render. Must be one of `overworld`, `end`, `cube`, `panorama`, `code`.
    - If the value is `cube`, there are additional fields that are required:
    - [String] texture: A resource location pointing to a texture asset.
    - [Int] repeats: The number of times the texture will be tiled horizontally and vertically on each plane of the cube.
    - [Float] size: Is set to 400.0 for [sky boxes](https://minecraft.wiki/w/Sky_box "Sky box") in the boiler room.​[*[more information needed](https://minecraft.wiki/w/Special%3ATalkPage/Data_component_format "Special:TalkPage/Data component format")*]
    - [String][NBT List / JSON Array][NBT Compound / JSON Object] name: A text component that will be shown as the name of the sky in the "Sky:" line of the tooltip.

#### special\_mine


* [NBT Compound / JSON Object] components: Parent tag.
  + [String] minecraft:special\_mine: The resource location of the special mine this [mine](https://minecraft.wiki/w/Mine_%28item%29 "Mine (item)") item teleports the player to.

#### trophy/type


* [NBT Compound / JSON Object] components: Parent tag.
  + [String] minecraft:trophy/type: The type of this [trophy](https://minecraft.wiki/w/Trophy_%28April_Fools%27_joke%29 "Trophy (April Fools' joke)"). Must be one of `gold`, `mega_spud`, `no_medal`.

#### world\_effect\_uhint


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:world\_effect\_uhint: ​[*[more information needed](https://minecraft.wiki/w/Special%3ATalkPage/Data_component_format "Special:TalkPage/Data component format")*]

#### world\_effect\_unlock


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:world\_effect\_unlock: ​[*[more information needed](https://minecraft.wiki/w/Special%3ATalkPage/Data_component_format "Special:TalkPage/Data component format")*]

#### world\_modifiers


* [NBT Compound / JSON Object] components: Parent tag.
  + [NBT Compound / JSON Object] minecraft:world\_modifiers: The [mine ingredients](https://minecraft.wiki/w/Mine_ingredient "Mine ingredient") included in the mine this [mine](https://minecraft.wiki/w/Mine_%28item%29 "Mine (item)") item teleports the player to.
    - [NBT List / JSON Array] effects: List of resource locations of world modifiers included in the mine.
      * [String]: A world modifier.
    - [Boolean] include\_description: Whether to show the mine ingredients in the tooltip of this mine item.

### [26w14a](https://minecraft.wiki/w/26w14a "26w14a")


List of the components

#### follow


* [NBT Compound / JSON Object] components: Parent tag.
  + [Boolean] minecraft:follow: ​[*[more information needed](https://minecraft.wiki/w/Special%3ATalkPage/Data_component_format "Special:TalkPage/Data component format")*]

## History


[![](/images/Information_icon.svg?15c1c)](https://minecraft.wiki/w/File%3AInformation_icon.svg "File:Information icon.svg")

This section is missing information about: later 26.1 changes

Please expand the section to include this information. Further details may exist on the [talk page](https://minecraft.wiki/w/Talk%3AData_component_format).

| [*Java Edition*](https://minecraft.wiki/w/Java_Edition_version_history "Java Edition version history") | | | | | | | |
| --- | --- | --- | --- | --- | --- | --- | --- |
| [1.20.5](https://minecraft.wiki/w/Java_Edition_1.20.5 "Java Edition 1.20.5") | | | [24w09a](https://minecraft.wiki/w/Java_Edition_24w09a "Java Edition 24w09a") | | | | Replaced [NBT Compound / JSON Object] tag tag and all underlying item-specific tags with data components. |
| Replaced [Byte] Count with [Int] count. |
| [24w10a](https://minecraft.wiki/w/Java_Edition_24w10a "Java Edition 24w10a") | | | | Renamed `lodestone_target` component to `lodestone_tracker`, and moved [Int Array] pos and [String] dimension fields to [NBT Compound / JSON Object] target. |
| `profile`, `dyed_color`, `attribute_modifiers`, `potion_contents`, `enchantments`, and `stored_enchantments` components can now optionally be defined in simpler formats. |
| `lore` and `fireworks` components now allow up to 256 entries in their list. |
| `container` component now applies to all [containers](https://minecraft.wiki/w/Container "Container"), instead of only [shulker boxes](https://minecraft.wiki/w/Shulker_box "Shulker box"). |
| [String] name is no longer required in `profile` component. |
| [24w12a](https://minecraft.wiki/w/Java_Edition_24w12a "Java Edition 24w12a") | | | | Added `food`, `max_stack_size`, `max_damage`, `fire_resistant`, `rarity`, `tool`, and `hide_tooltip` components. |
| The old `{...}` item format has been removed, and can no longer be used as a shortcut for `custom_data` component. |
| [24w13a](https://minecraft.wiki/w/Java_Edition_24w13a "Java Edition 24w13a") | | | | Added `item_name`, and `ominous_bottle_amplifier` components. |
| Components with non-default values on block items are now stored on block entities when placed. |
| [24w14a](https://minecraft.wiki/w/Java_Edition_24w14a "Java Edition 24w14a") | | | | Renamed [String] text to [String] raw in `writable_book_content`, and `written_book_content` components. |
| [Pre-Release 1](https://minecraft.wiki/w/Java_Edition_1.20.5_Pre-Release_1 "Java Edition 1.20.5 Pre-Release 1") | | | | Renamed [Float] saturation\_modifier to [Float] saturation in `food` component. |
| `max_damage`, and `max_stack_size` components can no longer be put together. |
| [1.21](https://minecraft.wiki/w/Java_Edition_1.21 "Java Edition 1.21") | | | [24w19a](https://minecraft.wiki/w/Java_Edition_24w19a "Java Edition 24w19a") | | | | `custom_data` component can now be defined as a SNBT string. |
| Added [NBT Compound / JSON Object] using\_converts\_to in `food` component. |
| [24w21a](https://minecraft.wiki/w/Java_Edition_24w21a "Java Edition 24w21a") | | | | Added `jukebox_playable` component. |
| Changed `attribute_modifiers` component: removed [String] name and [Int Array] uuid fields, added [String] id field. |
| [1.21.2](https://minecraft.wiki/w/Java_Edition_1.21.2 "Java Edition 1.21.2") | | | [24w33a](https://minecraft.wiki/w/Java_Edition_24w33a "Java Edition 24w33a") | | | | Added `repairable` and `enchantable` components. |
| The title specified in the `written_book_content` component is now prioritized over `custom_name` and `item_name` for any item with a non-empty title in this component. |
| [24w34a](https://minecraft.wiki/w/Java_Edition_24w34a "Java Edition 24w34a") | | | | Added `consumable`, `use_cooldown` and `use_remainder` components. |
| The `food` component has been changed to become a data container that holds only the food stats applied when the item is consumed. The component no longer gives the item the ability to be consumed. Removed the [Float] eat\_seconds, [NBT Compound / JSON Object] using\_converts\_to and [NBT List / JSON Array] effects fields from `food`. |
| [24w36a](https://minecraft.wiki/w/Java_Edition_24w36a "Java Edition 24w36a") | | | | Added `equippable`, `item_model`, `glider` and `tooltip_style` components. |
| The `item_name` component is now always present on every item. |
| [24w37a](https://minecraft.wiki/w/Java_Edition_24w37a "Java Edition 24w37a") | | | | Added `death_protection` component. |
| Renamed `fire_resistant` component to `damage_resistant`, and added [String] types field. |
| The name provided by the `item_name` component now always has the lowest priority. |
| Added [String] custom\_name in `potion_contents` component. |
| Added [Boolean] swappable and [Boolean] damage\_on\_hurt in `equippable` component. |
| [24w39a](https://minecraft.wiki/w/Java_Edition_24w39a "Java Edition 24w39a") | | | | The `lock` component is now a compound that represents an item predicate. |
| [Pre-Release 1](https://minecraft.wiki/w/Java_Edition_1.21.2_Pre-Release_1 "Java Edition 1.21.2 Pre-Release 1") | | | | Added [String] camera\_overlay in `equippable` component. |
| [1.21.4](https://minecraft.wiki/w/Java_Edition_1.21.4 "Java Edition 1.21.4") | | | [24w45a](https://minecraft.wiki/w/Java_Edition_24w45a "Java Edition 24w45a") | | | | `custom_model_data` now has more fields to accommodate new uses by various model property getters: `floats`, `flags`, `strings` and `colors`. |
| `item_model` now uses `assets/[namespace]/items/`, rather than `assets/[namespace]/models/item`. |
| The `equippable` component had its field `model` renamed to `asset_id`. |
| [1.21.5](https://minecraft.wiki/w/Java_Edition_1.21.5 "Java Edition 1.21.5") | | | [25w02a](https://minecraft.wiki/w/Java_Edition_25w02a "Java Edition 25w02a") | | | | Added `weapon` and `potion_duration_scale` components. |
| Added new optional field [Boolean] can\_destroy\_blocks\_in\_creative to `tool` component. |
| [25w03a](https://minecraft.wiki/w/Java_Edition_25w03a "Java Edition 25w03a") | | | | [Int] damage\_per\_attack field in `weapon` component was renamed to [Int] item\_damage\_per\_attack |
| `equippable` component can now apply to saddle slot, and has a new optional field: [Boolean] equip\_on\_interact. |
| Added 21 components, all of which are entity variant components. |
| [25w04a](https://minecraft.wiki/w/Java_Edition_25w04a "Java Edition 25w04a") | | | | Added the `blocks_attacks`, `break_sound`, `provides_banner_patterns`, `provides_trim_material` and `tooltip_display` components. |
| Removed the `hide_tooltip` and `hide_additional_tooltip` components in favor of the new `tooltip_display` component. |
| Removed the [Boolean] show\_in\_tooltip field from all components that previously had it in favor of the new `tooltip_display` component. |
| [Boolean] can\_disable\_blocking field in `weapon` component was renamed to [Float] disable\_blocking\_for\_seconds. |
| Most components that used to have two fields (one of them being the [Boolean] show\_in\_tooltip field) now always use their simplified form, with the other one field inlined to top-level. For example: `enchantments={levels:{sharpness:2}}` ->  `enchantments={sharpness:2}` |
| [25w05a](https://minecraft.wiki/w/Java_Edition_25w05a "Java Edition 25w05a") | | | | Added [String] bypassed\_by field to `blocks_attacks` component. |
| Added [Float] horizontal\_blocking\_angle field to objects within [NBT List / JSON Array] damage\_reduction field to `blocks_attacks` component. |
| Added `cow/variant` entity variant component. |
| [25w06a](https://minecraft.wiki/w/Java_Edition_25w06a "Java Edition 25w06a") | | | | Added `chicken/variant` entity variant component. |
| [25w08a](https://minecraft.wiki/w/Java_Edition_25w08a "Java Edition 25w08a") | | | | Added `wolf/sound_variant` entity variant component. |
| [1.21.6](https://minecraft.wiki/w/Java_Edition_1.21.6 "Java Edition 1.21.6") | | | [25w15a](https://minecraft.wiki/w/Java_Edition_25w15a "Java Edition 25w15a") | | | | Added optional [NBT Compound / JSON Object] display field to `attributes_modifiers`. |
| [25w16a](https://minecraft.wiki/w/Java_Edition_25w16a "Java Edition 25w16a") | | | | The `painting/variant` component no longer allows inline paining variant definitions. |
| [25w20a](https://minecraft.wiki/w/Java_Edition_25w20a "Java Edition 25w20a") | | | | Added optional [Boolean] can\_be\_sheared and [String][NBT Compound / JSON Object] shearing\_sound fields to `equippable`. |
| [1.21.9](https://minecraft.wiki/w/Java_Edition_1.21.9 "Java Edition 1.21.9") | | | [25w34a](https://minecraft.wiki/w/Java_Edition_25w34a "Java Edition 25w34a") | | | | Player profiles in data components and block entities no longer resolve automatically. |
| The `minecraft:profile` component has now two behaviors, Static or Dynamic, depending on which fields are specified. |
| [Pre-Release 1](https://minecraft.wiki/w/Java_Edition_1.21.9_Pre-Release_1 "Java Edition 1.21.9 Pre-Release 1") | | | | `minecraft:profile`: Profiles can now also have additional fields that can replace various values used for rendering; if any of the fields are omitted, the value from the resolved profile is used, even if the profile resolved to the default skin. |
| [1.21.11](https://minecraft.wiki/w/Java_Edition_1.21.11 "Java Edition 1.21.11") | | | [25w41a](https://minecraft.wiki/w/Java_Edition_25w41a "Java Edition 25w41a") | | | | Added `minecraft:damage_type`, `minecraft:kinetic_weapon`, `minecraft:minimum_attack_charge`, `minecraft:piercing_weapon`, `minecraft:swing_animation` and `minecraft:use_effects` item components. |
| `minecraft:consumable`: The animation field has been updated. |
| `minecraft:intangible`: Items with this component now show information about it in their tooltip. |
| [25w42a](https://minecraft.wiki/w/Java_Edition_25w42a "Java Edition 25w42a") | | | | `minecraft:kinetic_weapon`: Added new field, `contact_cooldown_ticks`. |
| [25w45a](https://minecraft.wiki/w/Java_Edition_25w45a "Java Edition 25w45a") | | | | `minecraft:piercing_weapon` and `minecraft:kinetic_weapon` data components now have bounds on their reach parameters. |
| [25w46a](https://minecraft.wiki/w/Java_Edition_25w46a "Java Edition 25w46a") | | | | Added food properties to the following fish bucket items: `minecraft:cod_bucket`, `minecraft:salmon_bucket`, `minecraft:pufferfish_bucket`, and `minecraft:tropical_fish_bucket`. |
| `minecraft:use_effects`: added field `interact_vibrations`. |
| [pre1](https://minecraft.wiki/w/Java_Edition_1.21.11-pre1 "Java Edition 1.21.11-pre1") | | | | `min_reach`, `max_reach` and `hitbox_margin` have been moved from `minecraft:piercing_weapon` and `minecraft:kinetic_weapon` into a new component `minecraft:attack_range` to allow all melee weapon types to use them. |
| [pre4](https://minecraft.wiki/w/Java_Edition_1.21.11-pre4 "Java Edition 1.21.11-pre4") | | | | `minecraft:attack_range`: Added fields `min_creative_reach` and `max_creative_reach`. |
| [26.1](https://minecraft.wiki/w/Java_Edition_26.1 "Java Edition 26.1") | | | [snap1](https://minecraft.wiki/w/Java_Edition_26.1_Snapshot_1 "Java Edition 26.1 Snapshot 1") | | | | Added `minecraft:additional_trade_cost`. |
| [snap5](https://minecraft.wiki/w/Java_Edition_26.1_Snapshot_5 "Java Edition 26.1 Snapshot 5") | | | | Added `minecraft:dye`. |
| [pre1](https://minecraft.wiki/w/Java_Edition_26.1-pre1 "Java Edition 26.1-pre1") | | | | `minecraft:provides_banner_patterns`: The component now also accepts an ID or a list of IDs in addition to a tag. |
| `minecraft:blocks_attacks`: The field `bypassed_by` now also accepts an ID or a list of IDs in addition to a tag. |
| `minecraft:damage_resistant`: The field types now also accepts an ID or a list of IDs in addition to a tag. |
| [Upcoming *Java Edition*](https://minecraft.wiki/w/Planned_versions#Java_Edition "Planned versions") | | | | | | | |
| [26.2](https://minecraft.wiki/w/Java_Edition_26.2 "Java Edition 26.2") | | | [snap1](https://minecraft.wiki/w/Java_Edition_26.2_Snapshot_1 "Java Edition 26.2 Snapshot 1") | | | | Added `sulfur_cube_content` component. |

## Notes


1. [↑](#cite_ref-1) The hexadecimal number is always at least 6 digits (with leading zeroes if needed), with additional digits if the alpha channel is included, despite the alpha channel having no effect on the tint color.
2. [↑](#cite_ref-2) For positive values larger than `0x00FFFFFF`, the most significant byte encodes the alpha channel (opacity), however this is effectively ignored when providing the tint color to the item model, as the tint does not affect opacity.
3. [↑](#cite_ref-3) Float values outside of this range are accepted, but clamped from 0 to 255 by modulo 256 after being multiplied by 255. For example, -1.0 is equivalent to 0.00392156862 (or 1/255).
4. [↑](#cite_ref-4) This can result in an item that is not normally obtainable and it affects the hexadecimal code that is shown in the (advanced) tooltip. For example `dyed_color=0x000000` shows "#000000" but `dyed_color=[0,0,0]` shows "#FF000000" despite them both representing the same pure black RGB color.
5. [↑](#cite_ref-5) If the item type has special dispenser behavior, this has no effect.
6. [↑](#cite_ref-6) The damage dealt is calculated as `floor(relative_speed * damage_multiplier)`, where `relative_speed` is the difference of speed vectors of the attacker and the target as projected onto the axis of the attacker's view vector. Any additional damage from enchantments or attribute modifiers is added after this calculation.
7. [↑](#cite_ref-7) To be used in the built-in smithing recipes, the item must also be in the `#trim_material` tag.

## Navigation


| * [v](https://minecraft.wiki/w/Template%3ANavbox_Java_Edition_technical "Template:Navbox Java Edition technical") * [t](https://minecraft.wiki/w/Special%3ATalkPage/Template%3ANavbox_Java_Edition_technical "Special:TalkPage/Template:Navbox Java Edition technical") * [e](https://minecraft.wiki/w/Special%3AEditPage/Template%3ANavbox_Java_Edition_technical "Special:EditPage/Template:Navbox Java Edition technical") *[Java Edition](https://minecraft.wiki/w/Java_Edition "Java Edition")* technical | |
| --- | --- |
| | General | | | --- | --- | | Concepts | * [![](/images/BlockSprite_chest.png?15d81)](https://minecraft.wiki/w/Block_entity "Block entity")[Block entity](https://minecraft.wiki/w/Block_entity "Block entity") * [![](/images/EnvSprite_map.png?b863e)](https://minecraft.wiki/w/Coordinates "Coordinates")[Coordinates](https://minecraft.wiki/w/Coordinates "Coordinates") * [![](/images/EffectSprite_infested.png?4562a)](https://minecraft.wiki/w/Crash "Crash")[Crashes](https://minecraft.wiki/w/Crash "Crash") * [String] [Loot context](https://minecraft.wiki/w/Loot_context "Loot context") * [![](/images/EntitySprite_cow.png?893cf)](https://minecraft.wiki/w/Mob_AI "Mob AI")[Mob AI](https://minecraft.wiki/w/Mob_AI "Mob AI") * [![](/images/BlockSprite_lodestone.png?00f1a)](https://minecraft.wiki/w/Point_of_Interest "Point of Interest")[Point of Interest](https://minecraft.wiki/w/Point_of_Interest "Point of Interest") * ![File directory.png: Sprite image for directory in Minecraft](/images/thumb/File_directory.png/16px-File_directory.png?8a409) [Identifier](https://minecraft.wiki/w/Identifier "Identifier") * [![](/images/BlockSprite_camera.png?7ee99)](https://minecraft.wiki/w/Screenshot "Screenshot")[Screenshot](https://minecraft.wiki/w/Screenshot "Screenshot") * [![](/images/EnvSprite_scoreboard.png?38feb)](https://minecraft.wiki/w/Statistics "Statistics")[Statistics](https://minecraft.wiki/w/Statistics "Statistics") * [![](/images/ItemSprite_book.png?791a5)](https://minecraft.wiki/w/Telemetry "Telemetry")[Telemetry](https://minecraft.wiki/w/Telemetry "Telemetry") * [![](/images/ItemSprite_clock.png?30324)](https://minecraft.wiki/w/Tick "Tick")[Tick](https://minecraft.wiki/w/Tick "Tick") * [![](/images/ItemSprite_wheat-seeds.png?b83e5)](https://minecraft.wiki/w/Random_Tick "Random Tick")[Random Tick](https://minecraft.wiki/w/Random_Tick "Random Tick") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/UUID "UUID")[UUID](https://minecraft.wiki/w/UUID "UUID") * [![](/images/BlockSprite_computer.png?e0c37)](https://minecraft.wiki/w/JSON "JSON")[JSON](https://minecraft.wiki/w/JSON "JSON") | | [General format](https://minecraft.wiki/w/Development_resources "Development resources") | * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Java_Edition_data_values "Java Edition data values")[Data values](https://minecraft.wiki/w/Java_Edition_data_values "Java Edition data values")   + [![](/images/LegacyBlockSprite_bricks-je1.png?9a58b)](https://minecraft.wiki/w/Java_Edition_Classic_data_values "Java Edition Classic data values")[Classic](https://minecraft.wiki/w/Java_Edition_Classic_data_values "Java Edition Classic data values")     - [Remake](https://minecraft.wiki/w/Classic_remake_data_values "Classic remake data values")   + [![](/images/EntitySprite_rana.png?3f2f9)](https://minecraft.wiki/w/Java_Edition_Indev_data_values "Java Edition Indev data values")[Indev](https://minecraft.wiki/w/Java_Edition_Indev_data_values "Java Edition Indev data values")   + [![](/images/BlockSprite_stone.png?e9a91)](https://minecraft.wiki/w/Java_Edition_pre-flattening_data_values "Java Edition pre-flattening data values")[Pre-flattening](https://minecraft.wiki/w/Java_Edition_pre-flattening_data_values "Java Edition pre-flattening data values") * [![](/images/EnvSprite_item.png?89d23)](https://minecraft.wiki/w/Data_component_format "Data component format")Data component format   + [![](/images/BlockSprite_test-block-start.png?35191)](https://minecraft.wiki/w/Data_component_predicate "Data component predicate")[Predicate](https://minecraft.wiki/w/Data_component_predicate "Data component predicate") * [![](/images/EnvSprite_entities.png?94711)](https://minecraft.wiki/w/Entity_format "Entity format")[Entity format](https://minecraft.wiki/w/Entity_format "Entity format") * [![](/images/BlockSprite_chest.png?15d81)](https://minecraft.wiki/w/Block_entity_format "Block entity format")[Block entity format](https://minecraft.wiki/w/Block_entity_format "Block entity format") * [![](/images/ItemSprite_map.png?05f8c)](https://minecraft.wiki/w/Map_item_format "Map item format")[Map item format](https://minecraft.wiki/w/Map_item_format "Map item format") * [NBT Compound / JSON Object] [NBT format](https://minecraft.wiki/w/NBT_format "NBT format") * [![](/images/EffectSprite_particle-healing.png?1357a)](https://minecraft.wiki/w/Particle_format "Particle format")[Particle format](https://minecraft.wiki/w/Particle_format "Particle format") * [![](/images/ItemSprite_book-and-quill.png?f190b)](https://minecraft.wiki/w/Text_component_format "Text component format")[Text component format](https://minecraft.wiki/w/Text_component_format "Text component format") * [§](https://minecraft.wiki/w/Formatting_codes "Formatting codes") [Formatting codes](https://minecraft.wiki/w/Formatting_codes "Formatting codes") * [![](/images/thumb/Movement_hint.png/16px-Movement_hint.png?92667)](https://minecraft.wiki/w/Key_codes "Key codes")[Key codes](https://minecraft.wiki/w/Key_codes "Key codes") * [![](/images/thumb/Dice.png/14px-Dice.png?a4e84)](https://minecraft.wiki/w/Random_sequence_format "Random sequence format")[Random sequence](https://minecraft.wiki/w/Random_sequence_format "Random sequence format") * [![](/images/BlockSprite_structure-block.png?381fc)](https://minecraft.wiki/w/Structure_file "Structure file")[Structure file format](https://minecraft.wiki/w/Structure_file "Structure file")   + [![](/images/EnvSprite_chunk.png?b2cf1)](https://minecraft.wiki/w/Schematic_file_format "Schematic file format")[Schematic file format](https://minecraft.wiki/w/Schematic_file_format "Schematic file format") | | [World](https://minecraft.wiki/w/World "World") | * [![](/images/EnvSprite_altitude.png?9b274)](https://minecraft.wiki/w/Heightmap "Heightmap")[Heightmap](https://minecraft.wiki/w/Heightmap "Heightmap") * [![](/images/EnvSprite_mountain.png?2e0ae)](https://minecraft.wiki/w/World_seed "World seed")[Seed](https://minecraft.wiki/w/World_seed "World seed")   + [Anomalous](https://minecraft.wiki/w/Anomalous_world_seeds "Anomalous world seeds") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Data_version "Data version")[Data version](https://minecraft.wiki/w/Data_version "Data version")  |  |  | | --- | --- | | Legacy | * [![](/images/EnvSprite_chunk.png?b2cf1)](https://minecraft.wiki/w/Spawn_chunk "Spawn chunk")[Spawn chunk](https://minecraft.wiki/w/Spawn_chunk "Spawn chunk") | | [Level format](https://minecraft.wiki/w/Java_Edition_level_format "Java Edition level format") | * [![](/images/BlockSprite_anvil.png?a26c9)](https://minecraft.wiki/w/Anvil_file_format "Anvil file format")[Anvil file format](https://minecraft.wiki/w/Anvil_file_format "Anvil file format") * [![](/images/EnvSprite_chunk.png?b2cf1)](https://minecraft.wiki/w/Chunk_format "Chunk format")[Chunk format](https://minecraft.wiki/w/Chunk_format "Chunk format") * [![](/images/EntitySprite_steve.png?856f8)](https://minecraft.wiki/w/Player.dat_format "Player.dat format")[Player format](https://minecraft.wiki/w/Player.dat_format "Player.dat format") * [![](/images/BlockSprite_lodestone.png?00f1a)](https://minecraft.wiki/w/Point_of_Interest_format "Point of Interest format")[Point of Interest format](https://minecraft.wiki/w/Point_of_Interest_format "Point of Interest format") * [![](/images/EntitySprite_ravager.png?40196)](https://minecraft.wiki/w/Raids.dat_format "Raids.dat format")[raids.dat format](https://minecraft.wiki/w/Raids.dat_format "Raids.dat format") * [![](/images/BlockSprite_chain-command-block.png?0afa8)](https://minecraft.wiki/w/Command_storage_format "Command storage format")[Command storage format](https://minecraft.wiki/w/Command_storage_format "Command storage format") * [![](/images/EnvSprite_scoreboard.png?38feb)](https://minecraft.wiki/w/Scoreboard#NBT_format "Scoreboard")[Scoreboard format](https://minecraft.wiki/w/Scoreboard#NBT_format "Scoreboard")  |  |  | | --- | --- | | Legacy | * [![](/images/LegacyBlockSprite_bricks-je1.png?9a58b)](https://minecraft.wiki/w/Java_Edition_Classic_level_format "Java Edition Classic level format")[Classic level format](https://minecraft.wiki/w/Java_Edition_Classic_level_format "Java Edition Classic level format") * [Classic server protocol](https://minecraft.wiki/w/Classic_server_protocol "Classic server protocol") * [![](/images/EntitySprite_rana.png?3f2f9)](https://minecraft.wiki/w/Java_Edition_Indev_level_format "Java Edition Indev level format")[Indev level format](https://minecraft.wiki/w/Java_Edition_Indev_level_format "Java Edition Indev level format") * [![](/images/EnvSprite_nether-portal.png?47646)](https://minecraft.wiki/w/Java_Edition_Alpha_level_format "Java Edition Alpha level format")[Alpha level format](https://minecraft.wiki/w/Java_Edition_Alpha_level_format "Java Edition Alpha level format")   + [![](/images/LegacyItemSprite_oak-door-revision-1.png?b7426)](https://minecraft.wiki/w/Zone_file_format "Zone file format")[Zone file format](https://minecraft.wiki/w/Zone_file_format "Zone file format") * [![](/images/ItemSprite_locked-map.png?c4112)](https://minecraft.wiki/w/Region_file_format "Region file format")[Region file format](https://minecraft.wiki/w/Region_file_format "Region file format") * [![](/images/Servers.png?b1dc2)](https://minecraft.wiki/w/Server_level.dat "Server level.dat")[server\_level.dat format](https://minecraft.wiki/w/Server_level.dat "Server level.dat") * [![](/images/EnvSprite_new-village.png?3e8a5)](https://minecraft.wiki/w/Villages.dat_format "Villages.dat format")[villages.dat format](https://minecraft.wiki/w/Villages.dat_format "Villages.dat format") * [![](/images/EnvSprite_abandoned-mineshaft.png?fab65)](https://minecraft.wiki/w/Generated_structures_data_file_format "Generated structures data file format")[Generated structures format](https://minecraft.wiki/w/Generated_structures_data_file_format "Generated structures data file format") | | | | [.minecraft](https://minecraft.wiki/w/.minecraft ".minecraft") | * ![File archive.png: Sprite image for archive in Minecraft](/images/thumb/File_archive.png/16px-File_archive.png?5ba7d) [client.jar](https://minecraft.wiki/w/Client.jar "Client.jar")   + [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Version.json "Version.json")[version.json](https://minecraft.wiki/w/Version.json "Version.json") * [![](/images/ItemSprite_book-and-quill.png?f190b)](https://minecraft.wiki/w/Client.json "Client.json")[client.json](https://minecraft.wiki/w/Client.json "Client.json") * [![](/images/BlockSprite_command-block.png?e7078)](https://minecraft.wiki/w/Command_history.txt "Command history.txt")[command\_history.txt](https://minecraft.wiki/w/Command_history.txt "Command history.txt") * [![](/images/BlockSprite_chest.png?15d81)](https://minecraft.wiki/w/Launcher_profiles.json "Launcher profiles.json")[launcher\_profiles.json](https://minecraft.wiki/w/Launcher_profiles.json "Launcher profiles.json") * [![](/images/Chat_settings_gear.png?6a179)](https://minecraft.wiki/w/Options.txt "Options.txt")[options.txt](https://minecraft.wiki/w/Options.txt "Options.txt") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Version_manifest.json "Version manifest.json")[version\_manifest.json](https://minecraft.wiki/w/Version_manifest.json "Version manifest.json") * [![](/images/ItemSprite_paper.png?565a1)](https://minecraft.wiki/w/Hotbar.nbt_format "Hotbar.nbt format")[hotbar.nbt format](https://minecraft.wiki/w/Hotbar.nbt_format "Hotbar.nbt format") * [![](/images/Servers.png?b1dc2)](https://minecraft.wiki/w/Servers.dat_format "Servers.dat format")[Server list format](https://minecraft.wiki/w/Servers.dat_format "Servers.dat format") | | Tools | * `F3` [Debug screen](https://minecraft.wiki/w/Debug_screen "Debug screen")   + [hotkey](https://minecraft.wiki/w/Debug_hotkey "Debug hotkey")   + [renderer](https://minecraft.wiki/w/Debug_renderer "Debug renderer") * [![](/images/Mojang_logo.svg?0b294)](https://minecraft.wiki/w/Java_developer_tools "Java developer tools")[Developer Tools](https://minecraft.wiki/w/Java_developer_tools "Java developer tools")   + [![](/images/BlockSprite_test-instance-block.png?27a39)](https://minecraft.wiki/w/GameTest "GameTest")[GameTest](https://minecraft.wiki/w/GameTest "GameTest")   + [DataFixerUpper](https://minecraft.wiki/w/DataFixerUpper "DataFixerUpper")   + [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Debug_property "Debug property")[Debug properties](https://minecraft.wiki/w/Debug_property "Debug property")  |  |  | | --- | --- | | Legacy | * [![](/images/BlockSprite_computer.png?e0c37)](https://minecraft.wiki/w/Obfuscation_map "Obfuscation map")[Obfuscation map](https://minecraft.wiki/w/Obfuscation_map "Obfuscation map") | | | Sound | * [![](/images/BlockSprite_jukebox-side.png?8477e)](https://minecraft.wiki/w/Block_sound_type "Block sound type")[Block sound type](https://minecraft.wiki/w/Block_sound_type "Block sound type") * [![](/images/EnvSprite_chat.png?0dd92)](https://minecraft.wiki/w/Closed_captions "Closed captions")[Closed captions](https://minecraft.wiki/w/Closed_captions "Closed captions") * [![](/images/EnvSprite_ambience.png?d7c92)](https://minecraft.wiki/w/Sounds.json "Sounds.json")[sounds.json](https://minecraft.wiki/w/Sounds.json "Sounds.json") | | [Commands](https://minecraft.wiki/w/Commands "Commands") | * [Brigadier](https://minecraft.wiki/w/Brigadier "Brigadier") * [![](/images/BlockSprite_repeating-command-block.png?1dad0)](https://minecraft.wiki/w/Function_%28Java_Edition%29 "Function (Java Edition)")[Functions](https://minecraft.wiki/w/Function_%28Java_Edition%29 "Function (Java Edition)")   **[All commands](https://minecraft.wiki/w/Template%3ANavbox_commands "Template:Navbox commands")** | | [Launching](https://minecraft.wiki/w/Minecraft_Launcher "Minecraft Launcher") | * [Mojang API](https://minecraft.wiki/w/Mojang_API "Mojang API") * [![](/images/Microsoft_logo.svg?7e87a)](https://minecraft.wiki/w/Microsoft_authentication "Microsoft authentication")[Microsoft authentication](https://minecraft.wiki/w/Microsoft_authentication "Microsoft authentication") * [![](/images/thumb/Java_Edition_icon_3.png/16px-Java_Edition_icon_3.png?f7112)](https://minecraft.wiki/w/Quick_Play "Quick Play")[Quick Play](https://minecraft.wiki/w/Quick_Play "Quick Play")  |  |  | | --- | --- | | Legacy | * [Legacy Minecraft authentication](https://minecraft.wiki/w/Legacy_Minecraft_authentication "Legacy Minecraft authentication") * [Yggdrasil](https://minecraft.wiki/w/Yggdrasil "Yggdrasil") | | | [Protocol](https://minecraft.wiki/w/Java_Edition_protocol "Java Edition protocol") | * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Protocol_version "Protocol version")[Protocol version](https://minecraft.wiki/w/Protocol_version "Protocol version") * [![](/images/ItemSprite_bundle.png?9eb9f)](https://minecraft.wiki/w/Java_Edition_protocol/Packets "Java Edition protocol/Packets")[Packets](https://minecraft.wiki/w/Java_Edition_protocol/Packets "Java Edition protocol/Packets") * [Data types](https://minecraft.wiki/w/Java_Edition_protocol/Data_types "Java Edition protocol/Data types") * [![](/images/BlockSprite_computer.png?e0c37)](https://minecraft.wiki/w/Java_Edition_protocol/Encryption "Java Edition protocol/Encryption")[Encryption](https://minecraft.wiki/w/Java_Edition_protocol/Encryption "Java Edition protocol/Encryption") | | [Server](https://minecraft.wiki/w/Server "Server") | * ![File archive.png: Sprite image for archive in Minecraft](/images/thumb/File_archive.png/16px-File_archive.png?5ba7d) [server.jar](https://minecraft.wiki/w/Server.jar "Server.jar") * [![](/images/BlockSprite_test-instance-block.png?27a39)](https://minecraft.wiki/w/Server.properties "Server.properties")[server.properties](https://minecraft.wiki/w/Server.properties "Server.properties") * [![](/images/BlockSprite_test-instance-block.png?27a39)](https://minecraft.wiki/w/Server/Requirements "Server/Requirements")[Server requirements](https://minecraft.wiki/w/Server/Requirements "Server/Requirements") * [![](/images/BlockSprite_test-block-accept.png?08355)](https://minecraft.wiki/w/Whitelist "Whitelist")[Whitelist](https://minecraft.wiki/w/Whitelist "Whitelist") * [Operator list](https://minecraft.wiki/w/Server#Operator_list "Server")  |  |  | | --- | --- | | Protocols | * [Query](https://minecraft.wiki/w/Query "Query") * [RCON](https://minecraft.wiki/w/RCON "RCON") * [Server Management Protocol](https://minecraft.wiki/w/Minecraft_Server_Management_Protocol "Minecraft Server Management Protocol") | | | Legacy | * [al\_version](https://minecraft.wiki/w/Al_version "Al version") * [![](/images/EnvSprite_item.png?89d23)](https://minecraft.wiki/w/Item_format "Item format")[Item format](https://minecraft.wiki/w/Item_format "Item format") | | |
| | [Data pack](https://minecraft.wiki/w/Data_pack "Data pack") | | | --- | --- | | Components | * [pack.mcmeta](https://minecraft.wiki/w/Pack.mcmeta "Pack.mcmeta") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Pack_format "Pack format")[Pack format](https://minecraft.wiki/w/Pack_format "Pack format") * [![](/images/ItemSprite_map.png?05f8c)](https://minecraft.wiki/w/Advancement_definition "Advancement definition")[Advancements](https://minecraft.wiki/w/Advancement_definition "Advancement definition") * [![](/images/BlockSprite_repeating-command-block.png?1dad0)](https://minecraft.wiki/w/Function_%28Java_Edition%29 "Function (Java Edition)")[Functions](https://minecraft.wiki/w/Function_%28Java_Edition%29 "Function (Java Edition)") * [![](/images/BlockSprite_red-banner.png?8b4d0)](https://minecraft.wiki/w/Item_modifier "Item modifier")[Item modifier](https://minecraft.wiki/w/Item_modifier "Item modifier") * [![](/images/ItemSprite_diamond.png?8f019)](https://minecraft.wiki/w/Loot_table "Loot table")[Loot tables](https://minecraft.wiki/w/Loot_table "Loot table") * [![](/images/BlockSprite_test-block-start.png?35191)](https://minecraft.wiki/w/Predicate "Predicate")[Predicate](https://minecraft.wiki/w/Predicate "Predicate") * [![](/images/BlockSprite_crafting-table.png?6e126)](https://minecraft.wiki/w/Recipe_%28Java_Edition%29 "Recipe (Java Edition)")[Recipe](https://minecraft.wiki/w/Recipe_%28Java_Edition%29 "Recipe (Java Edition)") * [![](/images/EffectSprite_strength.png?05e79)](https://minecraft.wiki/w/Damage_type "Damage type")[Damage type](https://minecraft.wiki/w/Damage_type "Damage type") * [![](/images/EnvSprite_chat.png?0dd92)](https://minecraft.wiki/w/Chat_type "Chat type")[Chat type](https://minecraft.wiki/w/Chat_type "Chat type") * [![](/images/ItemSprite_enchanted-book.png?b7877)](https://minecraft.wiki/w/Enchantment_definition "Enchantment definition")[Enchantment](https://minecraft.wiki/w/Enchantment_definition "Enchantment definition") * [![](/images/BlockSprite_enchanting-table.png?45e2c)](https://minecraft.wiki/w/Enchantment_provider "Enchantment provider")[Enchantment provider](https://minecraft.wiki/w/Enchantment_provider "Enchantment provider") * [![](/images/ItemSprite_painting.png?55d20)](https://minecraft.wiki/w/Painting_variant_definition "Painting variant definition")[Painting variant](https://minecraft.wiki/w/Painting_variant_definition "Painting variant definition") * [![](/images/BlockSprite_white-banner.png?8b4d0)](https://minecraft.wiki/w/Banner_pattern_definition "Banner pattern definition")[Banner pattern](https://minecraft.wiki/w/Banner_pattern_definition "Banner pattern definition") * [![](/images/ItemSprite_goat-horn.png?e5a9f)](https://minecraft.wiki/w/Instrument_definition "Instrument definition")[Instrument](https://minecraft.wiki/w/Instrument_definition "Instrument definition") * [![](/images/BlockSprite_jukebox.png?86205)](https://minecraft.wiki/w/Jukebox_song_definition "Jukebox song definition")[Jukebox song](https://minecraft.wiki/w/Jukebox_song_definition "Jukebox song definition") * [![](/images/BlockSprite_trial-spawner.png?0a3dc)](https://minecraft.wiki/w/Trial_spawner_configuration "Trial spawner configuration")[Trial spawner configuration](https://minecraft.wiki/w/Trial_spawner_configuration "Trial spawner configuration") * [![](/images/EntitySprite_pig.png?5435e)](https://minecraft.wiki/w/Mob_variant_definitions "Mob variant definitions")[Mob variants](https://minecraft.wiki/w/Mob_variant_definitions "Mob variant definitions") * [![](/images/ItemSprite_paper.png?565a1)](https://minecraft.wiki/w/Dialog "Dialog")[Dialog](https://minecraft.wiki/w/Dialog "Dialog") * [![](/images/ItemSprite_wayfinder-armor-trim.png?ffaf0)](https://minecraft.wiki/w/Armor_trim_definition "Armor trim definition")[Armor trim](https://minecraft.wiki/w/Armor_trim_definition "Armor trim definition") * [![](/images/ItemSprite_footprint.png?1c844)](https://minecraft.wiki/w/Slot_sources "Slot sources")[Slot sources](https://minecraft.wiki/w/Slot_sources "Slot sources") * [![](/images/ItemSprite_clock.png?30324)](https://minecraft.wiki/w/Timeline "Timeline")[Timeline](https://minecraft.wiki/w/Timeline "Timeline") * [![](/images/EntitySprite_villager.png?05433)](https://minecraft.wiki/w/Villager_trade_definition "Villager trade definition")[Villager trade](https://minecraft.wiki/w/Villager_trade_definition "Villager trade definition") * [Trade set](https://minecraft.wiki/w/Trade_set "Trade set") * [World Clock](https://minecraft.wiki/w/World_Clock "World Clock") * [![](/images/EntitySprite_sulfur-cube.png?ad68d)](https://minecraft.wiki/w/Sulfur_cube_archetype_definition "Sulfur cube archetype definition")[Sulfur cube archetype](https://minecraft.wiki/w/Sulfur_cube_archetype_definition "Sulfur cube archetype definition")​[*upcoming: [JE 26.2](https://minecraft.wiki/w/Java_Edition_26.2 "Java Edition 26.2")*]  |  |  | | --- | --- | | [Tag](https://minecraft.wiki/w/Tag_%28Java_Edition%29 "Tag (Java Edition)") | * [![](/images/BlockSprite_grass-block.png?97c2e)](https://minecraft.wiki/w/Block_tag_%28Java_Edition%29 "Block tag (Java Edition)")[Block](https://minecraft.wiki/w/Block_tag_%28Java_Edition%29 "Block tag (Java Edition)") * [![](/images/EnvSprite_item.png?89d23)](https://minecraft.wiki/w/Item_tag_%28Java_Edition%29 "Item tag (Java Edition)")[Item](https://minecraft.wiki/w/Item_tag_%28Java_Edition%29 "Item tag (Java Edition)") * [![](/images/BlockSprite_repeating-command-block.png?1dad0)](https://minecraft.wiki/w/Function_tag_%28Java_Edition%29 "Function tag (Java Edition)")[Function](https://minecraft.wiki/w/Function_tag_%28Java_Edition%29 "Function tag (Java Edition)") * [![](/images/ItemSprite_water-bucket.png?6e72b)](https://minecraft.wiki/w/Fluid_tag_%28Java_Edition%29 "Fluid tag (Java Edition)")[Fluid](https://minecraft.wiki/w/Fluid_tag_%28Java_Edition%29 "Fluid tag (Java Edition)") * [![](/images/EnvSprite_entities.png?94711)](https://minecraft.wiki/w/Entity_type_tag_%28Java_Edition%29 "Entity type tag (Java Edition)")[Entity type](https://minecraft.wiki/w/Entity_type_tag_%28Java_Edition%29 "Entity type tag (Java Edition)") * [![](/images/BlockSprite_sculk-sensor.png?ccbdb)](https://minecraft.wiki/w/Game_event_tag_%28Java_Edition%29 "Game event tag (Java Edition)")[Game event](https://minecraft.wiki/w/Game_event_tag_%28Java_Edition%29 "Game event tag (Java Edition)") * [![](/images/BiomeSprite_forest.png?98e29)](https://minecraft.wiki/w/Biome_tag_%28Java_Edition%29 "Biome tag (Java Edition)")[Biome](https://minecraft.wiki/w/Biome_tag_%28Java_Edition%29 "Biome tag (Java Edition)") * [![](/images/EnvSprite_superflat.png?54c14)](https://minecraft.wiki/w/Flat_level_generator_preset_tag_%28Java_Edition%29 "Flat level generator preset tag (Java Edition)")[Flat level generator preset](https://minecraft.wiki/w/Flat_level_generator_preset_tag_%28Java_Edition%29 "Flat level generator preset tag (Java Edition)") * [![](/images/EnvSprite_mountain.png?2e0ae)](https://minecraft.wiki/w/World_preset_tag_%28Java_Edition%29 "World preset tag (Java Edition)")[World preset](https://minecraft.wiki/w/World_preset_tag_%28Java_Edition%29 "World preset tag (Java Edition)") * [![](/images/EnvSprite_jungle-pyramid.png?736e3)](https://minecraft.wiki/w/Structure_tag_%28Java_Edition%29 "Structure tag (Java Edition)")[Structure](https://minecraft.wiki/w/Structure_tag_%28Java_Edition%29 "Structure tag (Java Edition)") * [![](/images/BlockSprite_lodestone.png?00f1a)](https://minecraft.wiki/w/Point_of_interest_type_tag_%28Java_Edition%29 "Point of interest type tag (Java Edition)")[Point of interest type](https://minecraft.wiki/w/Point_of_interest_type_tag_%28Java_Edition%29 "Point of interest type tag (Java Edition)") * [![](/images/ItemSprite_painting.png?55d20)](https://minecraft.wiki/w/Painting_variant_tag_%28Java_Edition%29 "Painting variant tag (Java Edition)")[Painting variant](https://minecraft.wiki/w/Painting_variant_tag_%28Java_Edition%29 "Painting variant tag (Java Edition)") * [![](/images/BlockSprite_white-banner.png?8b4d0)](https://minecraft.wiki/w/Banner_pattern_tag_%28Java_Edition%29 "Banner pattern tag (Java Edition)")[Banner pattern](https://minecraft.wiki/w/Banner_pattern_tag_%28Java_Edition%29 "Banner pattern tag (Java Edition)") * [![](/images/ItemSprite_goat-horn.png?e5a9f)](https://minecraft.wiki/w/Instrument_tag_%28Java_Edition%29 "Instrument tag (Java Edition)")[Instrument](https://minecraft.wiki/w/Instrument_tag_%28Java_Edition%29 "Instrument tag (Java Edition)") * ![❤️](/images/Heart_%28icon%29.png?faf83) [Damage type](https://minecraft.wiki/w/Damage_type_tag_%28Java_Edition%29 "Damage type tag (Java Edition)") * [![](/images/ItemSprite_enchanted-book.png?b7877)](https://minecraft.wiki/w/Enchantment_tag_%28Java_Edition%29 "Enchantment tag (Java Edition)")[Enchantment](https://minecraft.wiki/w/Enchantment_tag_%28Java_Edition%29 "Enchantment tag (Java Edition)") * [![](/images/ItemSprite_paper.png?565a1)](https://minecraft.wiki/w/Dialog_tag_%28Java_Edition%29 "Dialog tag (Java Edition)")[Dialog](https://minecraft.wiki/w/Dialog_tag_%28Java_Edition%29 "Dialog tag (Java Edition)") * [![](/images/ItemSprite_clock.png?30324)](https://minecraft.wiki/w/Timeline_tag_%28Java_Edition%29 "Timeline tag (Java Edition)")[Timeline](https://minecraft.wiki/w/Timeline_tag_%28Java_Edition%29 "Timeline tag (Java Edition)") * [![](/images/ItemSprite_water-bottle.png?fe7c2)](https://minecraft.wiki/w/Potion_tag_%28Java_Edition%29 "Potion tag (Java Edition)")[Potion](https://minecraft.wiki/w/Potion_tag_%28Java_Edition%29 "Potion tag (Java Edition)") * [![](/images/EntitySprite_villager.png?05433)](https://minecraft.wiki/w/Villager_trade_tag_%28Java_Edition%29 "Villager trade tag (Java Edition)")[Villager trade](https://minecraft.wiki/w/Villager_trade_tag_%28Java_Edition%29 "Villager trade tag (Java Edition)") * [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Configured_feature_tag_%28Java_Edition%29 "Configured feature tag (Java Edition)")[Configured feature](https://minecraft.wiki/w/Configured_feature_tag_%28Java_Edition%29 "Configured feature tag (Java Edition)") | | [GameTest](https://minecraft.wiki/w/GameTest "GameTest") | * [![](/images/BlockSprite_test-block-start.png?35191)](https://minecraft.wiki/w/Test_environment_definition "Test environment definition")[Test environment](https://minecraft.wiki/w/Test_environment_definition "Test environment definition") * [![](/images/BlockSprite_test-instance-block.png?27a39)](https://minecraft.wiki/w/Test_instance_definition "Test instance definition")[Test instance](https://minecraft.wiki/w/Test_instance_definition "Test instance definition") | | [World generation](https://minecraft.wiki/w/Custom_world_generation "Custom world generation") | * [Dimension](https://minecraft.wiki/w/Dimension_definition "Dimension definition") * [![](/images/EnvSprite_nether-portal.png?47646)](https://minecraft.wiki/w/Dimension_type "Dimension type")[Dimension type](https://minecraft.wiki/w/Dimension_type "Dimension type") * [![](/images/EnvSprite_mountain.png?2e0ae)](https://minecraft.wiki/w/World_preset_definition "World preset definition")[World preset](https://minecraft.wiki/w/World_preset_definition "World preset definition") * [![](/images/EnvSprite_biomes.png?0a976)](https://minecraft.wiki/w/Biome_definition "Biome definition")[Biomes](https://minecraft.wiki/w/Biome_definition "Biome definition") * [![](/images/EnvSprite_cave.png?47a17)](https://minecraft.wiki/w/Carver_definition "Carver definition")[Carver](https://minecraft.wiki/w/Carver_definition "Carver definition") * [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Configured_feature "Configured feature")[Configured feature](https://minecraft.wiki/w/Configured_feature "Configured feature")   + [![](/images/EnvSprite_oak.png?742a4)](https://minecraft.wiki/w/Tree_definition "Tree definition")[Tree](https://minecraft.wiki/w/Tree_definition "Tree definition") * [![](/images/EnvSprite_map.png?b863e)](https://minecraft.wiki/w/Placed_feature "Placed feature")[Placed feature](https://minecraft.wiki/w/Placed_feature "Placed feature") * [Environment attribute](https://minecraft.wiki/w/Environment_attribute "Environment attribute")  |  |  | | --- | --- | | [Noise settings](https://minecraft.wiki/w/Noise_settings "Noise settings") | * [![](/images/EnvSprite_mountain.png?2e0ae)](https://minecraft.wiki/w/Noise_router "Noise router")[Noise router](https://minecraft.wiki/w/Noise_router "Noise router") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Density_function "Density function")[Density function](https://minecraft.wiki/w/Density_function "Density function") * [Noises](https://minecraft.wiki/w/Noise "Noise") * [![](/images/EnvSprite_surface.png?75bf7)](https://minecraft.wiki/w/Surface_rule "Surface rule")[Surface rule](https://minecraft.wiki/w/Surface_rule "Surface rule") | | [Structures](https://minecraft.wiki/w/Structure_definition "Structure definition") | * [![](/images/EnvSprite_abandoned-mineshaft.png?fab65)](https://minecraft.wiki/w/Structure_set "Structure set")[Structure set](https://minecraft.wiki/w/Structure_set "Structure set") * [![](/images/BlockSprite_jigsaw.png?ec5e3)](https://minecraft.wiki/w/Template_pool "Template pool")[Template pool](https://minecraft.wiki/w/Template_pool "Template pool") * [![](/images/BlockSprite_cracked-stone-bricks.png?f3f1d)](https://minecraft.wiki/w/Processor_list "Processor list")[Processor list](https://minecraft.wiki/w/Processor_list "Processor list") * [![](/images/EnvSprite_nether-fossil.png?93621)](https://minecraft.wiki/w/Structure_file "Structure file")[Structure templates](https://minecraft.wiki/w/Structure_file "Structure file") | | Removed | * [![](/images/ItemSprite_iron-pickaxe.png?77536)](https://minecraft.wiki/w/Configured_surface_builder "Configured surface builder")[Configured surface builder](https://minecraft.wiki/w/Configured_surface_builder "Configured surface builder") | | | | Data packs | * [![](/images/BlockSprite_deepslate.png?d7361)](https://minecraft.wiki/w/Caves_%26_Cliffs_Prototype_Data_Pack "Caves & Cliffs Prototype Data Pack")[Caves & Cliffs Prototype Data Pack](https://minecraft.wiki/w/Caves_%26_Cliffs_Prototype_Data_Pack "Caves & Cliffs Prototype Data Pack") * [![](/images/ItemSprite_magical-painting.png?b0bf0)](https://minecraft.wiki/w/Phantom_Frames "Phantom Frames")[Phantom Frames](https://minecraft.wiki/w/Phantom_Frames "Phantom Frames") | | Tutorials | * [![](/images/thumb/EnvSprite_autosave.png/16px-EnvSprite_autosave.png?a55e7)](https://minecraft.wiki/w/Tutorial%3AImporting_a_data_pack "Tutorial:Importing a data pack")[Importing](https://minecraft.wiki/w/Tutorial%3AImporting_a_data_pack "Tutorial:Importing a data pack") * [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Tutorial%3ACreating_a_data_pack "Tutorial:Creating a data pack")[Creating](https://minecraft.wiki/w/Tutorial%3ACreating_a_data_pack "Tutorial:Creating a data pack") * [Optimizing](https://minecraft.wiki/w/Tutorial%3AOptimizing_a_data_pack "Tutorial:Optimizing a data pack") * [![](/images/BlockSprite_command-block.png?e7078)](https://minecraft.wiki/w/Tutorial%3ACommand_blocks_and_functions "Tutorial:Command blocks and functions")[Command blocks and functions](https://minecraft.wiki/w/Tutorial%3ACommand_blocks_and_functions "Tutorial:Command blocks and functions") * [Repairing a world corrupted by a data pack](https://minecraft.wiki/w/Tutorial%3ARepairing_a_world_corrupted_by_a_data_pack "Tutorial:Repairing a world corrupted by a data pack")  |  |  | | --- | --- | | Content | * [![](/images/ItemSprite_enchanted-book.png?b7877)](https://minecraft.wiki/w/Tutorial%3AAdding_custom_enchantments "Tutorial:Adding custom enchantments")[Custom enchantments](https://minecraft.wiki/w/Tutorial%3AAdding_custom_enchantments "Tutorial:Adding custom enchantments") * [![](/images/ItemSprite_painting.png?55d20)](https://minecraft.wiki/w/Tutorial%3AAdding_custom_paintings "Tutorial:Adding custom paintings")[Custom paintings](https://minecraft.wiki/w/Tutorial%3AAdding_custom_paintings "Tutorial:Adding custom paintings") * [![](/images/ItemSprite_armor-trim.png?1d672)](https://minecraft.wiki/w/Tutorial%3AAdding_custom_trims "Tutorial:Adding custom trims")[Custom trims](https://minecraft.wiki/w/Tutorial%3AAdding_custom_trims "Tutorial:Adding custom trims") | | World generation | * [![](/images/EnvSprite_other-portal.png?ca57b)](https://minecraft.wiki/w/Tutorial%3AAdding_a_new_dimension "Tutorial:Adding a new dimension")[New dimension](https://minecraft.wiki/w/Tutorial%3AAdding_a_new_dimension "Tutorial:Adding a new dimension") * [![](/images/EnvSprite_lunar-base.png?648e4)](https://minecraft.wiki/w/Tutorial%3ACustom_structures "Tutorial:Custom structures")[Custom structures](https://minecraft.wiki/w/Tutorial%3ACustom_structures "Tutorial:Custom structures") | | | |
| | [Resource pack](https://minecraft.wiki/w/Resource_pack "Resource pack") | | | --- | --- | | Components | * [pack.mcmeta](https://minecraft.wiki/w/Pack.mcmeta "Pack.mcmeta") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Pack_format "Pack format")[Pack format](https://minecraft.wiki/w/Pack_format "Pack format") * [![](/images/EnvSprite_language.png?39da2)](https://minecraft.wiki/w/Resource_pack#Language "Resource pack")[Language](https://minecraft.wiki/w/Resource_pack#Language "Resource pack") * [![](/images/EntitySprite_creeper.png?703e9)](https://minecraft.wiki/w/Model "Model")[Models](https://minecraft.wiki/w/Model "Model") * [![](/images/BlockSprite_double-stone-slab.png?62750)](https://minecraft.wiki/w/Blockstates_definition "Blockstates definition")[Blockstates](https://minecraft.wiki/w/Blockstates_definition "Blockstates definition") * [![](/images/EnvSprite_item.png?89d23)](https://minecraft.wiki/w/Items_model_definition "Items model definition")[Items](https://minecraft.wiki/w/Items_model_definition "Items model definition") * [![](/images/EnvSprite_ambience.png?d7c92)](https://minecraft.wiki/w/Sound "Sound")[Sounds](https://minecraft.wiki/w/Sound "Sound") ([sounds.json](https://minecraft.wiki/w/Sounds.json "Sounds.json")) * [Shaders](https://minecraft.wiki/w/Shader "Shader") * [![](/images/EnvSprite_texture-pack.png?a4213)](https://minecraft.wiki/w/Resource_pack#Textures "Resource pack")[Textures](https://minecraft.wiki/w/Resource_pack#Textures "Resource pack") * [![](/images/ItemSprite_compass.png?2364d)](https://minecraft.wiki/w/Atlas "Atlas")[Atlases](https://minecraft.wiki/w/Atlas "Atlas") * [Aa](https://minecraft.wiki/w/Font "Font") [Fonts](https://minecraft.wiki/w/Font "Font") * [![](/images/BlockSprite_oak-leaves.png?81553)](https://minecraft.wiki/w/Resource_pack#Colormaps "Resource pack")[Colormaps](https://minecraft.wiki/w/Resource_pack#Colormaps "Resource pack") * ![File file.png: Sprite image for file in Minecraft](/images/thumb/File_file.png/16px-File_file.png?e19ce) [Texts](https://minecraft.wiki/w/Resource_pack#Texts "Resource pack") * [![](/images/Locator_Bar_icon_bowtie.png?a8cd8)](https://minecraft.wiki/w/Waypoint_style "Waypoint style")[Waypoint styles](https://minecraft.wiki/w/Waypoint_style "Waypoint style") * [regional\_compliancies.json](https://minecraft.wiki/w/Resource_pack#Regional_compliancies_warnings "Resource pack") * [![](/images/ItemSprite_all-iron-armor.png?87e31)](https://minecraft.wiki/w/Equipment "Equipment")[Equipment](https://minecraft.wiki/w/Equipment "Equipment") | | Debug | * [Missing font character](https://minecraft.wiki/w/Missing_font_character "Missing font character") * [![](/images/BlockSprite_missingno.png?031f4)](https://minecraft.wiki/w/Missing_model "Missing model")[Missing model](https://minecraft.wiki/w/Missing_model "Missing model") * [![](/images/BlockSprite_missingno.png?031f4)](https://minecraft.wiki/w/Missing_texture "Missing texture")[Missing texture](https://minecraft.wiki/w/Missing_texture "Missing texture") | | Tools | * [Slicer](https://minecraft.wiki/w/Slicer "Slicer")  |  |  | | --- | --- | | Legacy | * [Texture Ender](https://minecraft.wiki/w/Texture_Ender "Texture Ender") * [Unstitcher](https://minecraft.wiki/w/Unstitcher "Unstitcher") | | | Tutorials | * [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Tutorial%3ACreating_a_resource_pack "Tutorial:Creating a resource pack")[Creating](https://minecraft.wiki/w/Tutorial%3ACreating_a_resource_pack "Tutorial:Creating a resource pack") * [![](/images/Download.png?048e3)](https://minecraft.wiki/w/Tutorial%3ALoading_a_resource_pack "Tutorial:Loading a resource pack")[Loading](https://minecraft.wiki/w/Tutorial%3ALoading_a_resource_pack "Tutorial:Loading a resource pack") * [![](/images/EnvSprite_fluids.png?58a6a)](https://minecraft.wiki/w/Tutorial%3AModels "Tutorial:Models")[Models](https://minecraft.wiki/w/Tutorial%3AModels "Tutorial:Models") * [![](/images/EnvSprite_ambience.png?d7c92)](https://minecraft.wiki/w/Tutorial%3ASound_directory "Tutorial:Sound directory")[Sound directory](https://minecraft.wiki/w/Tutorial%3ASound_directory "Tutorial:Sound directory") | | |

Retrieved from "<https://minecraft.wiki/w/Data_component_format?oldid=3609505>"

[Categories](https://minecraft.wiki/w/Special%3ACategories "Special:Categories"):

* [Java Edition](https://minecraft.wiki/w/Category%3AJava_Edition "Category:Java Edition")
* [Data component format subpages](https://minecraft.wiki/w/Category%3AData_component_format_subpages "Category:Data component format subpages")
* [In development](https://minecraft.wiki/w/Category%3AIn_development "Category:In development")
* [In development Java Edition](https://minecraft.wiki/w/Category%3AIn_development_Java_Edition "Category:In development Java Edition")
* [Java Edition technical](https://minecraft.wiki/w/Category%3AJava_Edition_technical "Category:Java Edition technical")
* [Development](https://minecraft.wiki/w/Category%3ADevelopment "Category:Development")

Hidden categories:

* [Upcoming](https://minecraft.wiki/w/Category%3AUpcoming "Category:Upcoming")
* [Java Edition upcoming tag](https://minecraft.wiki/w/Category%3AJava_Edition_upcoming_tag "Category:Java Edition upcoming tag")
* [Pages using calculator](https://minecraft.wiki/w/Category%3APages_using_calculator "Category:Pages using calculator")
* [Information needed](https://minecraft.wiki/w/Category%3AInformation_needed "Category:Information needed")
* [Minecraft Work in progress](https://minecraft.wiki/w/Category%3AMinecraft_Work_in_progress "Category:Minecraft Work in progress")
* [Minecraft Work in progress with a note](https://minecraft.wiki/w/Category%3AMinecraft_Work_in_progress_with_a_note "Category:Minecraft Work in progress with a note")
* [Articles to be expanded](https://minecraft.wiki/w/Category%3AArticles_to_be_expanded "Category:Articles to be expanded")
* [Java Edition upcoming](https://minecraft.wiki/w/Category%3AJava_Edition_upcoming "Category:Java Edition upcoming")
