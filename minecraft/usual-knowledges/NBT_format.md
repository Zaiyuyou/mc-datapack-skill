# NBT format

From Minecraft Wiki

[Jump to navigation](#mw-head)
[Jump to search](#searchInput)

![](/images/Disambig_color.svg?2db52) For NBT path format, see [NBT path](https://minecraft.wiki/w/NBT_path "NBT path").

The **Named Binary Tag** (**NBT**) is a [tree data structure](https://en.wikipedia.org/wiki/Tree_%28data_structure%29 "wikipedia:Tree (data structure)") used by *Minecraft* in many [save files](https://minecraft.wiki/w/Java_Edition_level_format "Java Edition level format") to store arbitrary data. The format comprises a handful of *tags*. Tags have a numeric type ID, a name, and a [payload](https://en.wikipedia.org/wiki/payload_%28computing%29 "wikipedia:payload (computing)"). A user-accessible version in the form of [strings](https://en.wikipedia.org/wiki/string_%28computer_science%29 "wikipedia:string (computer science)") is the **stringified Named Binary Tag** (**SNBT**) format.

[ ]

## Contents

* [1 SNBT format](#SNBT_format)
  + [1.1 Data types](#Data_types)
  + [1.2 Number format](#Number_format)
    - [1.2.1 Signedness suffixes](#Signedness_suffixes)
  + [1.3 Escape sequences](#Escape_sequences)
  + [1.4 Operations](#Operations)
* [2 NBT object](#NBT_object)
  + [2.1 Generating NBT object](#Generating_NBT_object)
  + [2.2 Conversion to SNBT](#Conversion_to_SNBT)
  + [2.3 Conversion from SNBT](#Conversion_from_SNBT)
  + [2.4 Modifying entity/block based on NBT object](#Modifying_entity/block_based_on_NBT_object)
  + [2.5 Testing NBT tags](#Testing_NBT_tags)
* [3 Binary format](#Binary_format)
  + [3.1 TAG definition](#TAG_definition)
  + [3.2 Usage](#Usage)
    - [3.2.1 Uses](#Uses)
* [4 JSON and NBT](#JSON_and_NBT)
  + [4.1 Conversion from JSON](#Conversion_from_JSON)
  + [4.2 Conversion to JSON](#Conversion_to_JSON)
* [5 Official software](#Official_software)
* [6 History](#History)
* [7 Notes](#Notes)
* [8 References](#References)
* [9 External links](#External_links)
* [10 Navigation](#Navigation)

## SNBT format


[![](/images/thumb/Gear_icon.png/16px-Gear_icon.png?94611)](https://minecraft.wiki/w/File%3AGear_icon.png "File:Gear icon.png")

This section is a work in progress.

Please help [expand and improve](https://minecraft.wiki/w/Special%3AEditPage/NBT_format "Special:EditPage/NBT format") it. The [talk page](https://minecraft.wiki/w/Special%3ATalkPage/NBT_format "Special:TalkPage/NBT format") may contain suggestions.
**Note:**

Some sections might have to be written differently.

[![](/images/Information_icon.svg?15c1c)](https://minecraft.wiki/w/File%3AInformation_icon.svg "File:Information icon.svg")

This feature is exclusive to [*Java Edition*](https://minecraft.wiki/w/Java_Edition "Java Edition").

String Named Binary Tag (SNBT), is the stringified representation of any NBT data tag. It is often used in commands in [*Java Edition*](https://minecraft.wiki/w/Java_Edition "Java Edition"). The root tag is most commonly a map, also known as a **compound** holding [key-value pairs](https://en.wikipedia.org/wiki/Name%E2%80%93value_pair "wikipedia:Name–value pair") enclosed in curly braces (see below for details). An example of SNBT is specifying complex data for entities with commands.

:   *Example:*

    ```
    {
      key1: 123,
      'key2': 'somevalue1',
      "key3": {
        subkey1: 0x1C8,
        "subkey2": "somevalue2"
      }
    }
    ```

### Data types


SNBT Data Types

| Type | Description | Format | Example |
| --- | --- | --- | --- |
| [Byte] Byte | A signed 8-bit integer, ranging from -128 to 127 (inclusive). | `<number>b` or `<number>B` | `34B`, `-20b` |
| [Boolean] Boolean | NBT has no boolean data type, but byte value 0 and 1 can be represented as `true`, `false`. When a byte field is used as a boolean value, [Boolean] icon is shown. | `true`, `false` | `true` |
| [Short] Short | A signed 16-bit integer, ranging from -32,768 to 32,767 (inclusive). | `<number>s` or `<number>S` | `31415s`, `-27183s` |
| [Int] Int | A signed 32-bit integer, ranging from -2,147,483,648 and 2,147,483,647 (inclusive). | `<integer_number>`, `<number>i` or `<number>I` | `31415926` |
| [Long] Long | A signed 64-bit integer, ranging from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 (inclusive). | `<number>l` or `<number>L` | `31415926l` |
| [Float] Float | A 32-bit, single-precision floating-point number, ranging from -3.4E38 to +3.4E38. See [IEEE floating point](https://en.wikipedia.org/wiki/IEEE_floating_point "wikipedia:IEEE floating point") for details. | `<number>f` or `<number>F` | `3.1415926f` |
| [Double] Double | A 64-bit, double-precision floating-point, ranging from -1.79E308 to +1.79E308. See [IEEE floating point](https://en.wikipedia.org/wiki/IEEE_floating_point "wikipedia:IEEE floating point") for details. | `<decimal_number>`, `<number>d` or `<number>D` | `3.1415926` |
| [String] String | A sequence of characters | A string of characters, enclosed in double quotes `"` or single quotes `'`. Quote enclosure is optional if the string contains only `0-9`, `A-Z`, `a-z`, `_`, `-`, `.`, and `+` characters, and if the string does not begin with `0-9`, `-`, `.`, or `+`.  Nested quotes of the same type used for enclosure can be included within the string by *escaping* the character with a backslash (`\"` or `\'`). Backslashes can be included in a string by escaping them with a second backslash (`\\`).  Strings enclosed in quotes also accept a number of other escape sequences for representing characters such as `\n` for line feeds. See [§ Escape sequences](#Escape_sequences) for more information.  `<[a-zA-Z0-9_\-\.\+] text>`, `"<text>"` (`"` within needs to be escaped to `\"`), or `'<text>'` (`'` within needs to be escaped to `\'`) | `"Hello \"World!\""`  `'Hello "World!"'`  `'Hello \'World!\''`  `"Hello 'World!'"` |
| [NBT List / JSON Array] List | An ordered list of tags of the same type\*. | Unnamed tags enclosed in square brackets and delimited by commas. In SNBT, heterogenous lists (a list containing more than one type of tag) may be written and are handled as expected at runtime; but when saved to NBT, any non-compound entries are saved as a compound with a single empty key paired with that value. For example, `[1,"abc"]` represents `[{"":1},{"":"abc"}]`.  `[<value>,<value>,...]` | `[3.2,64.5,129.5]` |
| [NBT Compound / JSON Object] Compound | An unordered list of attribute-value pairs. Each tag can be of any type. | Named tags enclosed in double quotes `"` or single quotes `'` The key (tag name) can be unquoted if it contains only `0-9`, `A-Z`, `a-z`, `_`, `-`, `.`, and `+` characters. Otherwise, the key should be quoted and use the same formatting rules as strings.  `{<[a-zA-Z0-9_\-\.\+] tag_name>:<value>,"<tag name>":<value>,...}` | `{X:3,Y:64,Z:129}` `{foo: 1, bar: "abc", baz: {}}` |
| [Byte Array] Byte Array | An ordered list of 8-bit integers. Note that `[B;1b,2b,3b]` and `[1b,2b,3b]` are considered different types: the second one is a [NBT List / JSON Array] list. | `B;` followed by an ordered list of byte tags, delimited by commas. Tag is enclosed in square brackets. `[B;<byte>b,<byte>B,true,false...]` | `[B;1b,2b,3b]` |
| [Int Array] Int Array | An ordered list of 32-bit integers. Note that `[I;1,2,3]` and `[1,2,3]` are considered different types: the second one is a [NBT List / JSON Array] list. | `I;` followed by an ordered list of int tags, delimited by commas. Byte and short tags may also be used. Tag is enclosed in square brackets. `[I;<integer>,<integer>i,...]` | `[I;1,2,3]` `[I;1b,2s,3i]` |
| [Long Array] Long Array | An ordered list of 64-bit integers. Note that `[L;1l,2l,3l]` and `[1l,2l,3l]` are considered different types: the second one is a [NBT List / JSON Array] list. | `L;` followed by an ordered list of long tags, delimited by commas. Byte, short, and int tags may also be used. Tag is enclosed in square brackets. `[L;<long>l,<long>L,...]` | `[L;1l,2l,3l]` `[L;1b,2s,3i,4l]` |

### Number format


There are many other ways to represent a number:

* Either whole or fraction parts of a float number can be omitted (e.g. `.1` and `1.`).
* Float numbers can use [E notation](https://en.wikipedia.org/wiki/Scientific_notation#E_notation "wikipedia:Scientific notation") (e.g. `1.2e3`, `87E48`, and `0.1e-1`).
* Integer numbers can be prefixed with `0x` or `0b` to represent a hexadecimal number or a binary number, respectively (e.g. `0xbad`, `0xCAFE`, and `0b101`)[[note 1]](#cite_note-1).
* Numbers can contain `_` character between sequences of digits, but not at the start or the end of sequence (e.g. `0b10_01`, `0xAB_CD`, `1_2.3_4__5f`, and `1_2e3_4`).

#### Signedness suffixes


Besides the data type suffixes (i.e. `b` for byte, `L` for long, etc), there is also [signedness](https://en.wikipedia.org/wiki/signedness "wikipedia:signedness") suffixes (`u` and `U` for unsigned integers, `s` and `S` for signed integers). These suffixes cannot be used on decimal numbers; only integers. The method used for representing signed integers is [Two's complement](https://en.wikipedia.org/wiki/Two%27s_complement "wikipedia:Two's complement").

If these suffixes are used, there must always be a data type suffix after the signedness suffix. If not used, defaults to signed.

If two suffixes are present on an integer, from left to right, the first suffix represents the signedness of the value and the second suffix represents the data type. If only one suffix is present, the suffix represents the data type.

Examples:

* `-16b`, `-16sb`, and `240uB` all represent byte value `-16`.
* `15s`, `15sS`, and `15Us` all represent short value `15`.
* `82u`, `-87uI`, `30bu`, and `253sb` are all incorrect and give errors.

### Escape sequences


Minecraft supports 13 escape sequences. Here is a list of all of them:

| Escape sequence | Hex value in [ASCII](https://en.wikipedia.org/wiki/ASCII "wikipedia:ASCII") | Character represented |
| --- | --- | --- |
| \b[[note 2]](#cite_note-unsupported_es-2) | 08 | [Backspace](https://en.wikipedia.org/wiki/Backspace "wikipedia:Backspace") |
| \f[[note 2]](#cite_note-unsupported_es-2) | 0C | [Formfeed](https://en.wikipedia.org/wiki/Formfeed "wikipedia:Formfeed") |
| \n | 0A | [Newline](https://en.wikipedia.org/wiki/Newline "wikipedia:Newline") (Line Feed) |
| \r[[note 2]](#cite_note-unsupported_es-2) | 0D | [Carriage Return](https://en.wikipedia.org/wiki/Carriage_Return "wikipedia:Carriage Return") |
| \s | 20 | Space () |
| \t[[note 2]](#cite_note-unsupported_es-2) | 09 | [Horizontal Tab](https://en.wikipedia.org/wiki/Horizontal_Tab "wikipedia:Horizontal Tab") |
| \\ | 5C | [Backslash](https://en.wikipedia.org/wiki/Backslash "wikipedia:Backslash") (`\`) |
| \' | 27 | [Apostrophe](https://en.wikipedia.org/wiki/Apostrophe "wikipedia:Apostrophe") or single quotation mark (`'`) |
| \" | 22 | Double [quotation mark](https://en.wikipedia.org/wiki/quotation_mark "wikipedia:quotation mark") (`"`) |
| \x*hh* | *hh* | Unicode [code point](https://en.wikipedia.org/wiki/code_point "wikipedia:code point") below 100 hexadecimal (e.g. `\x42` for U+0042) |
| \u*hhhh* | *non-ASCII* | Unicode code point below 10,000 hexadecimal (e.g. `\u2604` for U+2604) |
| \U*hhhhhhhh* | *non-ASCII* | Unicode code point below 100,000,000 hexadecimal (e.g. `\U00051020` for U+51020) |
| \N{*<name>*} | *non-ASCII* | The character with the specified name (e.g. `\N{Snowman}`) |

### Operations


SNBT currently only supports 2 operations:

* `bool(arg)` - Converts argument to boolean. Argument can only be a number or a boolean.
  + If argument is a boolean value, returns value directly.
  + If argument is a number value, returns false if it's 0, otherwise returns true.
  + Examples:
    - `bool(true)` -> `true`
    - `bool(5)` -> `true`
    - `bool(0)` -> `false`
    - `bool("foo")` -> error
* `uuid(str)` - Converts string representation of [UUID](https://minecraft.wiki/w/UUID "UUID") to integer array.
  + Example: `uuid("f81d4fae-7dec-11d0-a765-00a0c91e6bf6")` -> `[I; -132296786, 2112623056, -1486552928, -920753162]`

## NBT object


When the game is running, entities and block entities in loading chunks are stored in the memory. They are not stored with NBT, as it is a serialization format.

When processing NBT operations, the game generates NBT objects from entities/block entities, parses the provided SNBT into NBT, and then modify the entities/blocks using it.

### Generating NBT object


When generating NBT from an entity/block, the entity/block's properties are added into programmatic NBT object.

Note that not all properties are added. For example, the value of whether a player is opening a chest won't be added into NBT object.

A value is added with certain data type. For example, a resource location is [converted to a string value](https://minecraft.wiki/w/Resource_location#Conversion_to_string "Resource location").

These NBT objects are also stored into game's save files as NBT files when the game quits or automatically saves. So the data structures that NBT tags describe and the data type for each tag are basically the same ones used in game's save files. These data structures are described in other articles and commands expect data tags to use the same attribute names (which are case-sensitive):

Data Structure Specification Links

| Objects | Examples |
| --- | --- |
| [Block entities](https://minecraft.wiki/w/Block_entity_format "Block entity format") | chests, furnaces, command blocks, mob spawners, signs, etc. |
| [Items](https://minecraft.wiki/w/Player.dat#Item_structure "Player.dat") | items in inventories (includes specifications for enchantments, lore, custom names, etc.) |
| [Item entities](https://minecraft.wiki/w/Entity_format#Items_and_XP_Orbs "Entity format") | items on the ground |
| [Mobs](https://minecraft.wiki/w/Entity_format#Mobs "Entity format") | creepers, cows, villagers, etc. |
| [Projectiles](https://minecraft.wiki/w/Entity_format#Projectiles "Entity format") | arrows, fireballs, thrown potions, etc. |
| [Vehicles](https://minecraft.wiki/w/Entity_format#Vehicles "Entity format") | boats, minecarts, etc. |
| [Dynamic tiles](https://minecraft.wiki/w/Entity_format#Dynamic_Tiles "Entity format") | primed TNT, falling sand/gravel/concrete powder/anvils |
| [Other entities](https://minecraft.wiki/w/Entity_format#Other "Entity format") | firework rockets, paintings, and item frames |

### Conversion to SNBT


[![](/images/Information_icon.svg?15c1c)](https://minecraft.wiki/w/File%3AInformation_icon.svg "File:Information icon.svg")

This feature is exclusive to [*Java Edition*](https://minecraft.wiki/w/Java_Edition "Java Edition").

A programmatic NBT object would be converted to a SNBT when trying to get it with `/[data](https://minecraft.wiki/w/Commands/data "Commands/data") get` etc.

After converted, a number is always followed by a letter (lowercase for b, s, f, d, and uppercase for L) except [Int] Integer. For example, `3s` for a short, `3.2f` for a float, etc.

And a string is always enclosed by double or single quotes. If the string does not contain any quote marks, double quotes are used. If the string contains a double quote then single quotes are used, and vice versa. If the string contains both then the opposite of the first instance of either in the string is used (e.g. if a `"` appears before a `'` then the string will be enclosed in single quotes)

Other data types are expressed as the [#Data types](#Data_types) table above.

### Conversion from SNBT


[![](/images/Information_icon.svg?15c1c)](https://minecraft.wiki/w/File%3AInformation_icon.svg "File:Information icon.svg")

This feature is exclusive to [*Java Edition*](https://minecraft.wiki/w/Java_Edition "Java Edition").

An SNBT is converted to a programmatic NBT object when parsed by the game.

A number that followed by a letter (B, S, L, F, D, or their lowercase) is resolved to corresponding data type. For example, `3s` for a short, `3.2f` for a float, etc. The letter can be uppercase or lowercase. When no letter is used, it assumes double if there's a decimal point, int if there's no decimal point.

A heterogeneous list (i.e. ones where elements are not of the same type) is converted to a non-heterogeneous list. ​[*[more information needed](https://minecraft.wiki/w/Special%3ATalkPage/NBT_format "Special:TalkPage/NBT format")*]

A square-bracketed literal is assumed to be a list unless an identifier is used: `[B;1B,2B,3B]` for a byte array, `[I;1,2,3]` for an int array and `[L;1L,2L,3L]` for a long array.

`true` and `false` are converted as `1b` and `0b` respectively.

### Modifying entity/block based on NBT object


[![](/images/Information_icon.svg?15c1c)](https://minecraft.wiki/w/File%3AInformation_icon.svg "File:Information icon.svg")

This feature is exclusive to [*Java Edition*](https://minecraft.wiki/w/Java_Edition "Java Edition").

Modifying entity/block based on a programmatic NBT object is not a simple process. All certain tags need to be resolved before changing properties of a block/entity. Note that only certain properties can be changed. For example, when using `/[data](https://minecraft.wiki/w/Commands/data "Commands/data")` command to modify a block entity, its coordinates cannot be changed.

If a property needs a value of resource location and gets a [String] string tag, the string is [converted to a resource location](https://minecraft.wiki/w/Resource_location#Conversion_from_string "Resource location").

If a property needs a value of JSON text and gets a [String] string tag, the string is parsed into JSON text object.

If a property needs a boolean value and gets a numeric tag, true if the number is not 0 after some rounding operation and conversion to byte.

If a property needs a boolean value and gets a non-numeric tag, the property becomes false.

If a property needs a numeric value of certain type and gets a numeric tag of wrong type, the value gets some rounding operation and converts to the required type.

If a property needs a numeric value and gets a non-numeric tag, the number becomes 0.

If a property needs a string value and gets a non-string tag, the string becomes an empty string.

If a property needs a list or array of certain type and gets a wrong-type tag, an empty list/array is got.

If a property needs a compound tag and gets a non-compound tag, an empty compound tag is got.

### Testing NBT tags


[![](/images/Information_icon.svg?15c1c)](https://minecraft.wiki/w/File%3AInformation_icon.svg "File:Information icon.svg")

This feature is exclusive to [*Java Edition*](https://minecraft.wiki/w/Java_Edition "Java Edition").

In some places - such as the `/[execute](https://minecraft.wiki/w/Commands/execute "Commands/execute") if data` command, [the `nbt` argument in target selector](https://minecraft.wiki/w/Target_selectors#Selecting_targets_by_NBT_data "Target selectors"), and the [custom\_data](https://minecraft.wiki/w/Data_component_format "Data component format") component predicate - an SNBT compound is used to test for an NBT compound object *partially matching* with it. When this happens, the game converts SNBT into a programmatic NBT object, gets the programmatic NBT object from block/entity/storage/component, then compares the two NBT objects.

The test only checks for the presence of the SNBT's tags in the target entity/block/storage/component. This means that the entity/block/storage can have additional tags and still match, hence this is often referred to as a "partial" match and can be thought of as checking if the source object contains some subset of tags. For example, `{foo:1,bar:2}` can be tested for with either `{foo:1}`, `{bar:2}`, `{foo:1,bar:2}`, or even `{}`.

This is true even for lists. The order and number of elements in a list are not considered, and as long as every requested element is in the list, it matches even if there are additional elements. For example, an entity with data `{Pos:[1d,2d,3d],Tags:["a","b"]}` can be targeted by `@e[nbt={Pos:[3d,2d,1d]}]` or even just `@e[nbt={Pos:[2d]}]` even though the former represents a totally different position and the latter is not a valid position at all. Note that whilst empty compounds match with any compound, an empty list only matches with another empty list, so `@e[nbt={Tags:[]}]` will not match, because the `Tags` list has some elements.

However, the order and number of elements in a byte/long/int array **is** acknowledged.

The requested data tags in the target entity/block/storage/component must match *exactly* for the provided tags to pass, including the data type (e.g. `1`, an int, does not match `1d`, a double). Namespaces also cannot be omitted because, in NBT objects, it is just a plain string that won't be resolved into a resource location (e.g. `@e[nbt={Item:{id:"stone"}}]` does not match a stone item entity, it must be `@e[nbt={Item:{id:"minecraft:stone"}}]`).

## Binary format


An NBT file is a zipped Compound tag. Some of the files utilized by *Minecraft* may be uncompressed, but in most cases, the files follow Notch's original specification and are compressed with GZip.

### TAG definition


A tag is an individual part of the data tree. The first byte in a tag is the tag type (ID), followed by a two byte big-endian unsigned 16-bit integer (ushort) for the length of the name, then the name as a string in UTF-8 format (Note TAG\_End is not named and does not contain the extra 2 bytes; the name is assumed to be empty). Finally, depending on the type of the tag, the bytes that follow are part of that tag's *payload*. This table describes each of the 13 known tags in version 19133 of the NBT format:

| ID | HEX | Icon | Tag Type | Payload | Description | Storage Capacity |
| --- | --- | --- | --- | --- | --- | --- |
| **0** | **0x00** |  | TAG\_**End** | - | Used to mark the end of compound tags. This tag **does not have a name**, so it is always a single byte 0. It may also be the type of empty List tags. | N/A |
| **1** | **0x01** | [Byte] | TAG\_**Byte** | 1 byte / 8 bits, signed | A signed integer type. Sometimes used for booleans. | Full range of -(27) to (27 - 1) (-128 to 127). |
| **2** | **0x02** | [Short] | TAG\_**Short** | 2 bytes / 16 bits, signed, big endian | A signed integer type. | Full range of -(215) to (215 - 1) (-32,768 to 32,767). |
| **3** | **0x03** | [Int] | TAG\_**Int** | 4 bytes / 32 bits, signed, big endian | A signed integer type. | Full range of -(231) to (231 - 1) (-2,147,483,648 to 2,147,483,647). |
| **4** | **0x04** | [Long] | TAG\_**Long** | 8 bytes / 64 bits, signed, big endian | A signed integer type. | Full range of -(263) to (263 - 1) (-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807). |
| **5** | **0x05** | [Float] | TAG\_**Float** | 4 bytes / 32 bits, signed, big endian, IEEE 754-2008, binary32 | A signed floating point type. | Precision varies throughout number line; See [Single-precision floating-point format](https://en.wikipedia.org/wiki/Single-precision_floating-point_format "wikipedia:Single-precision floating-point format"). Maximum value ~ ±3.4E38. |
| **6** | **0x06** | [Double] | TAG\_**Double** | 8 bytes / 64 bits, signed, big endian, IEEE 754-2008, binary64 | A signed floating point type. | Precision varies throughout number line; See [Double-precision floating-point format](https://en.wikipedia.org/wiki/Double-precision_floating-point_format "wikipedia:Double-precision floating-point format"). Maximum value ~ ±1.79E308. |
| **7** | **0x07** | [Byte Array] | TAG\_**Byte**\_**Array** | 4 bytes / 32 bits, signed, big endian for *size*, then the bytes of length *size* | An array of bytes. | Maximum number of elements ranges between (231 - 9) and (231 - 1) (2,147,483,639 and 2,147,483,647), depending on the specific JVM. |
| **8** | **0x08** | [String] | TAG\_**String** | 2 bytes / 16 bits, **unsigned**, big endian for *size*, then the bytes of length *size* as UTF-8 formatted character data. **not null-terminated** | A UTF-8 string. It has a size, rather than being null terminated. | 65,535 bytes interpretable as UTF-8 (see [modified UTF-8 format](https://en.wikipedia.org/wiki/UTF-8#Modified_UTF-8 "wikipedia:UTF-8"); most commonly-used characters are a single byte). |
| **9** | **0x09** | [NBT List / JSON Array] | TAG\_**List** | 1 byte / 8 bits for the **tag ID** of the list's contents, then 4 bytes / 32 bits, big-endian for *size*. Followed by length *size* number of items of *tag id* | A list of tag payloads, without tag IDs or names, apart from the one before the length. | Due to JVM limitations and the implementation of ArrayList, the maximum number of list elements is (231 - 9), or 2,147,483,639. Also note that List and Compound tags may not be nested beyond a depth of 512. |
| **10** | **0x0A** | [NBT Compound / JSON Object] | TAG\_**Compound** | Contains any number of tags, delimited by **TAG\_End**. Each tag consisting of 1 byte / 8 bits **tag ID**, followed by 2 bytes / 16 bits, unsigned, big-endian for *size*, then an UTF-8 formatted string containing the tag name. Lastly, the payload data. | A list of fully formed tags, including their IDs, names, and payloads. No two tags may have the same name. | Unlike lists, there is no hard limit to the number of tags within a Compound (of course, there is always the implicit limit of virtual memory). Note, however, that Compound and List tags may not be nested beyond a depth of 512. |
| **11** | **0x0B** | [Int Array] | TAG\_**Int**\_**Array** | 4 bytes / 32 bits, signed, big-endian for *size*, then *size* number of *TAG\_Int* payloads. | An array of TAG\_Int's payloads. | Maximum number of elements ranges between (231 - 9) and (231 - 1) (2,147,483,639 and 2,147,483,647), depending on the specific JVM. |
| **12** | **0x0C** | [Long Array] | TAG\_**Long**\_**Array** | 4 bytes / 32 bits, signed, big-endian for *size*, then *size* number of *TAG\_Long* payloads. | An array of TAG\_Long's payloads. | Maximum number of elements ranges between (231 - 9) and (231 - 1) (2,147,483,639 and 2,147,483,647), depending on the specific JVM. |

The List and Compound tags can be and often are recursively nested. It should also be noted that, in a list of lists, each of the sub-lists can list a different kind of tag.

### Usage


*Minecraft* sometimes uses the NBT format inconsistently; in some instances, empty lists may be represented as a list of Byte tags rather than a list of the correct type, or as a list of End tags in newer versions of Minecraft, which can break some older NBT tools.

In most cases, the files follow Notch's original specification and are compressed with GZip. But some of the files utilized by Minecraft may be uncompressed, or with [zlib](https://en.wikipedia.org/wiki/zlib "wikipedia:zlib") (aka DEFLATE with a few bytes extra).

All NBT files created by *Minecraft* have either a [NBT Compound / JSON Object] compound or sometimes a [NBT List / JSON Array] list‌[*[Bedrock Edition](https://minecraft.wiki/w/Bedrock_Edition "Bedrock Edition") only*] as the root tag, this tag has a name but is often the [empty string](https://en.wikipedia.org/wiki/empty_string "wikipedia:empty string").

In [*Bedrock Edition*](https://minecraft.wiki/w/Bedrock_Edition "Bedrock Edition"), all numbers are encoded in little-endian. This includes the size prefix before tag names, [String] string values and [NBT List / JSON Array] list or [Byte Array][Int Array][Long Array] array values, as well as values in all numeric tags.

In [*Bedrock Edition*](https://minecraft.wiki/w/Bedrock_Edition "Bedrock Edition"), the [level.dat](https://minecraft.wiki/w/Bedrock_Edition_level_format#level.dat_format "Bedrock Edition level format") is uncompressed NBT file with an 8-byte header, consisting of a little-endian 4-byte integer indicating the version of the tool used to save the file. It is followed by another integer containing the length of the file, minus the header.

#### Uses


[![](/images/Information_icon.svg?15c1c)](https://minecraft.wiki/w/File%3AInformation_icon.svg "File:Information icon.svg")

This section is missing information about: Bedrock Edition NBTs

Please expand the section to include this information. Further details may exist on the [talk page](https://minecraft.wiki/w/Talk%3ANBT_format).

* `[level.dat](https://minecraft.wiki/w/Level.dat "Level.dat")` is stored in compressed NBT format.
* `[<player>.dat](https://minecraft.wiki/w/Player.dat_format "Player.dat format")` files are stored in compressed NBT format.
* `[idcounts.dat](https://minecraft.wiki/w/Idcounts.dat "Idcounts.dat")` is stored in compressed NBT format.
* `[villages.dat](https://minecraft.wiki/w/Villages.dat "Villages.dat")` is stored in compressed NBT format.
* `[raids.dat](https://minecraft.wiki/w/Raids.dat_format "Raids.dat format")` is stored in compressed NBT format.
* `[map_<#>.dat](https://minecraft.wiki/w/Map_item_format "Map item format")` files are stored in compressed NBT format.
* `[servers.dat](https://minecraft.wiki/w/Servers.dat_format "Servers.dat format")`, which is used to store the list of saved multiplayer servers as uncompressed NBT.
* `[hotbar.nbt](https://minecraft.wiki/w/Hotbar.nbt_format "Hotbar.nbt format")`, which is used to save hotbars as uncompressed NBT format.
* [Chunks](https://minecraft.wiki/w/Chunk_format "Chunk format") are stored in compressed NBT format within [Region](https://minecraft.wiki/w/Region_file_format "Region file format") files.
* `[scoreboard.dat](https://minecraft.wiki/w/Scoreboard#NBT_format "Scoreboard")` is stored in compressed NBT format.
* [Generated structures](https://minecraft.wiki/w/Generated_structures_data_file_format "Generated structures data file format") are stored in compressed NBT format.
* [Saved structures](https://minecraft.wiki/w/Structure_file "Structure file") are stored in compressed NBT format.

## JSON and NBT


See also: [JSON](https://minecraft.wiki/w/JSON "JSON")

JSON as a format is very different from NBT. NBT is a data structure which can be represented as a binary stream *or* as text, while JSON is a text-only format designed for data-interchange. There are only six data types in JSON: JsonString, JsonNumber, JsonBoolean, JsonNull, JsonObject, and JsonArray. In NBT, there are multiple numeric types, and there are no null and boolean data types. Arrays in NBT must be homogeneous; they cannot contain elements of different types. However, in JSON, the elements of a JsonArray may be of any type. The keys of tags in SNBT are allowed to be unquoted, while the keys of name-value pairs in JSON must be double-quoted.

Due to the differences between the two formats, conversion from NBT to JSON may result in a loss of information and precision. However, this conversion is still used in [*Java Edition*](https://minecraft.wiki/w/Java_Edition "Java Edition") on occasion, currently only for the ambient particles of [custom biomes](https://minecraft.wiki/w/Custom_biome "Custom biome") and the `rule` processor type of [processor lists](https://minecraft.wiki/w/Processor_list "Processor list").

### Conversion from JSON


[![](/images/Information_icon.svg?15c1c)](https://minecraft.wiki/w/File%3AInformation_icon.svg "File:Information icon.svg")

This feature is exclusive to [*Java Edition*](https://minecraft.wiki/w/Java_Edition "Java Edition").

| Data type in JSON | Converts to |
| --- | --- |
| JsonString | [String] string |
| JsonBoolean | [Byte] byte |
| JsonNumber | * If in the range of byte (e.g. 0, 1.0, 1.27e2), converts to a [Byte] byte. * Otherwise, if in the range of short (e.g. 128, 1234), converts to a [Short] short. * Otherwise, if in the range of int (e.g. 12345678.0, -1.23e8), converts to an [Int] int. * Otherwise, if in the range of long (e.g. 2147483649), converts to a [Long] long. * Otherwise, if it can be stored precisely by float (e.g. 0.5, 31.75), converts to a [Float] float. * Otherwise, converts to a [Double] double. |
| JsonNull | Cannot be converted. |
| JsonArray | The conversion from JsonArray to NBT is a little buggy. First converts all the elements in the array to NBT, if their data types are different, this array cannot be converted into NBT. That means arrays like [0,1,true] and [5e-1,0.25] can be converted to NBT successfully, while [0,1,128], [0.5, 0.6], and [0.0, 0.1] cannot be converted to NBT.  And when it can be converted to NBT:   * If the elements are converted to byte, the array is converted to a [Byte Array] byte array. * If the elements are converted to int, the array is converted to an [Int Array] int array. * If the elements are converted to long, the array is converted to a [Long Array] long array. * Otherwise, the array is converted to a [NBT List / JSON Array] list.   For example, [true, 127] is converted to [B; 1B, 127B]. |
| JsonObject | [NBT Compound / JSON Object] compound |

### Conversion to JSON


[![](/images/Information_icon.svg?15c1c)](https://minecraft.wiki/w/File%3AInformation_icon.svg "File:Information icon.svg")

This feature is exclusive to [*Java Edition*](https://minecraft.wiki/w/Java_Edition "Java Edition").

| Data type in NBT | Converts to |
| --- | --- |
| [String] string | JsonString |
| [Byte] byte [Short] short [Int] int [Long] long [Float] float [Double] double | JsonNumber |
| [Byte Array] byte array [Int Array] int array  [Long Array] long array [NBT List / JSON Array] list | JsonArray |
| [NBT Compound / JSON Object] compound | JsonObject |

## Official software


See also: [Tutorial:Running the data generator](https://minecraft.wiki/w/Tutorial%3ARunning_the_data_generator "Tutorial:Running the data generator")

Mojang has provided sample Java NBT classes for developers to use and reference as part of the source code for the [MCRegion](https://minecraft.wiki/w/MCRegion "MCRegion") to [Anvil file format](https://minecraft.wiki/w/Anvil_file_format "Anvil file format") converter.[[1]](#cite_note-3) Since [Java Edition 1.13](https://minecraft.wiki/w/Java_Edition_1.13 "Java Edition 1.13"), *Minecraft* includes a built-in converter between the SNBT format and compressed NBT format, which comes with both the [client](https://minecraft.wiki/w/Client.jar "Client.jar") and official server.[[2]](#cite_note-4)

The data generator from *Minecraft* is able to convert uncompressed Stringified NBT files with `.snbt` extension in an input folder to GZip compressed NBT format files with `.nbt` extension in an output folder, and vice versa.

The vanilla data generator can convert any GZip compressed NBT format to SNBT format. The file extension of a file can simply be changed, such as `[level.dat](https://minecraft.wiki/w/Level.dat "Level.dat")` to `level.nbt` and put in the input folder, and the generator then decodes the GZip compressed NBT data.

## History


The NBT file format was described by [Notch](https://minecraft.wiki/w/Notch "Notch") in a brief specification.[[3]](#cite_note-5)

The NBT file format dates all the way back to [Indev](https://minecraft.wiki/w/Indev "Indev") with tags 0 to 10 in use.

| [*Java Edition*](https://minecraft.wiki/w/Java_Edition_version_history "Java Edition version history") | | | | | | | |
| --- | --- | --- | --- | --- | --- | --- | --- |
| [1.0.0](https://minecraft.wiki/w/Java_Edition_1.0.0 "Java Edition 1.0.0") | | | [September 28, 2011](https://twitter.com/notch/status/119296531592515584) | | | | Notch works on "saving arbitrary data with item instances." |
| [1.2.1](https://minecraft.wiki/w/Java_Edition_1.2.1 "Java Edition 1.2.1") | | | [12w07a](https://minecraft.wiki/w/Java_Edition_12w07a "Java Edition 12w07a") | | | | Added [Int Array] int array tags. |
| [1.8](https://minecraft.wiki/w/Java_Edition_1.8 "Java Edition 1.8") | | | [14w03a](https://minecraft.wiki/w/Java_Edition_14w03a "Java Edition 14w03a") | | | | NBT data in commands now supports using string IDs (*names* of blocks/items) rather than numerical IDs. |
| [1.12](https://minecraft.wiki/w/Java_Edition_1.12 "Java Edition 1.12") | | | [17w18a](https://minecraft.wiki/w/Java_Edition_17w18a "Java Edition 17w18a") | | | | Added [Long Array] long array tags. |
| [1.13](https://minecraft.wiki/w/Java_Edition_1.13 "Java Edition 1.13") | | | [18w01a](https://minecraft.wiki/w/Java_Edition_18w01a "Java Edition 18w01a") | | | | Added a data generator to both the *Minecraft* [client](https://minecraft.wiki/w/Client.jar "Client.jar") and the default multiplayer software. |
| [1.14](https://minecraft.wiki/w/Java_Edition_1.14 "Java Edition 1.14") | | | [19w08a](https://minecraft.wiki/w/Java_Edition_19w08a "Java Edition 19w08a") | | | | [String] String tags and names of tags in compound in SNBT can now be within single quotes `'` in addition to double quotes `"`.[[4]](#cite_note-6) |
| [1.16](https://minecraft.wiki/w/Java_Edition_1.16 "Java Edition 1.16") | | | [20w21a](https://minecraft.wiki/w/Java_Edition_20w21a "Java Edition 20w21a") | | | | Added conversion function between NBT and JSON. |
| [1.20.5](https://minecraft.wiki/w/Java_Edition_1.20.5 "Java Edition 1.20.5") | | | [24w09a](https://minecraft.wiki/w/Java_Edition_24w09a "Java Edition 24w09a") | | | | When heterogenous (differently-typed) lists are written to the `custom_data` component using a JSON file (such as a loot table), any entries in the list that are not compounds are saved as compounds with empty keys containing the value. |
| [1.21.5](https://minecraft.wiki/w/Java_Edition_1.21.5 "Java Edition 1.21.5") | | | [25w04a](https://minecraft.wiki/w/Java_Edition_25w04a "Java Edition 25w04a") | | | | SNBT (textual representation of NBT-like data) has been expanded to accept heterogenous lists, i.e. ones where elements are not of the same type. |
| [25w09a](https://minecraft.wiki/w/Java_Edition_25w09a "Java Edition 25w09a") | | | | SNBT now supports freeform numeric literals. This means that `.1`, `2e3`, `123_456` are now all valid number literals. |
| SNBT now supports writing numbers in hexadecial (e.g. `0xABCD`) and binary (e.g. `0b1001`). |
| SNBT now supports 's' and 'u' suffixes (for signed and unsigned representation, respectively) (e.g., `240ub` is equal to `-16sb`). |
| SNBT now supports string escape sequences (such as `\n` for newline, etc.), as well as Unicode escape sequences such as `\x42`, `\u0048`, and `\N{Snowman}`. |
| SNBT now allows trailing commas.[*[verify](https://minecraft.wiki/w/Special%3ATalkPage/NBT_format "Special:TalkPage/NBT format")*] |
| All NBT components now supports heterogenous (differently-typed) lists (e.g., `[1, "abc"]`). Any entries in the list that are not compounds are saved to NBT as compounds with a single empty key containing that value. |
| Empty keys in NBT paths are no longer valid |
| [25w10a](https://minecraft.wiki/w/Java_Edition_25w10a "Java Edition 25w10a") | | | | SNBT now supports `bool(arg)` to convert an argument to a boolean value and `uuid(string)` to convert a string UUID into its array representation. |

## Notes


1. [↑](#cite_ref-1) Since `b` is also a valid hexadecimal digit, byte sized hexadecimal values can only be written with a signed suffix, like `0x11ub` or `0x11sb`
2. ↑ [a](#cite_ref-unsupported_es_2-0) [b](#cite_ref-unsupported_es_2-1) [c](#cite_ref-unsupported_es_2-2) [d](#cite_ref-unsupported_es_2-3) This escape sequence is useless, since Minecraft doesn't support these characters anyways.[*[verify](https://minecraft.wiki/w/Special%3ATalkPage/NBT_format "Special:TalkPage/NBT format")*]

## References


1. [↑](#cite_ref-3) [https://web.archive.org/web/0/https://www.mojang.com/2012/02/new-minecraft-map-format-anvil/](https://web.archive.org/web/0/https%3A//www.mojang.com/2012/02/new-minecraft-map-format-anvil/)
2. [↑](#cite_ref-4) [MCW:Projects/wiki.vg merge/Data Generators § NBT converters](https://minecraft.wiki/w/Minecraft_Wiki%3AProjects/wiki.vg_merge/Data_Generators#NBT_converters "Minecraft Wiki:Projects/wiki.vg merge/Data Generators")
3. [↑](#cite_ref-5) [http://web.archive.org/web/20110723210920/http://www.minecraft.net/docs/NBT.txt](http://web.archive.org/web/20110723210920/http%3A//www.minecraft.net/docs/NBT.txt) specification
4. [↑](#cite_ref-6) ["Allow single quote in strings by boq · Pull Request #52"](https://github.com/Mojang/brigadier/pull/52) – Mojang/brigadier – GitHub.

## External links


* [nbt](https://github.com/BitBuf/nbt), Java library for working with the NBT format.
* [NBT](https://minecraft.wiki/w/Minecraft_Wiki%3AProjects/wiki.vg_merge/NBT "Minecraft Wiki:Projects/wiki.vg merge/NBT") on wiki.vg
* [NBTEditor](https://github.com/Howaner/NBTEditor/), a lightweight NBT editor.
* [NBTExplorer](http://www.minecraftforum.net/topic/840677-nbtexplorer/), a tool for viewing and editing NBT files.
* [NBT Studio](https://github.com/tryashtar/nbt-studio), successor to NBTExplorer that includes additional features like Bedrock support and SNBT.
* [webNBT](http://irath96.github.io/webNBT/), an online tool for viewing and editing NBT files.
* [XNBTEdit](https://github.com/Foresteam/XNBTEdit/), GUI/CLI XML NBT editor and converter (not tested on MC 1.21).

## Navigation


| * [v](https://minecraft.wiki/w/Template%3ANavbox_Java_Edition_technical "Template:Navbox Java Edition technical") * [t](https://minecraft.wiki/w/Special%3ATalkPage/Template%3ANavbox_Java_Edition_technical "Special:TalkPage/Template:Navbox Java Edition technical") * [e](https://minecraft.wiki/w/Special%3AEditPage/Template%3ANavbox_Java_Edition_technical "Special:EditPage/Template:Navbox Java Edition technical") *[Java Edition](https://minecraft.wiki/w/Java_Edition "Java Edition")* technical | |
| --- | --- |
| | General | | | --- | --- | | Concepts | * [![](/images/BlockSprite_chest.png?15d81)](https://minecraft.wiki/w/Block_entity "Block entity")[Block entity](https://minecraft.wiki/w/Block_entity "Block entity") * [![](/images/EnvSprite_map.png?b863e)](https://minecraft.wiki/w/Coordinates "Coordinates")[Coordinates](https://minecraft.wiki/w/Coordinates "Coordinates") * [![](/images/EffectSprite_infested.png?4562a)](https://minecraft.wiki/w/Crash "Crash")[Crashes](https://minecraft.wiki/w/Crash "Crash") * [String] [Loot context](https://minecraft.wiki/w/Loot_context "Loot context") * [![](/images/EntitySprite_cow.png?893cf)](https://minecraft.wiki/w/Mob_AI "Mob AI")[Mob AI](https://minecraft.wiki/w/Mob_AI "Mob AI") * [![](/images/BlockSprite_lodestone.png?00f1a)](https://minecraft.wiki/w/Point_of_Interest "Point of Interest")[Point of Interest](https://minecraft.wiki/w/Point_of_Interest "Point of Interest") * ![File directory.png: Sprite image for directory in Minecraft](/images/thumb/File_directory.png/16px-File_directory.png?8a409) [Identifier](https://minecraft.wiki/w/Identifier "Identifier") * [![](/images/BlockSprite_camera.png?7ee99)](https://minecraft.wiki/w/Screenshot "Screenshot")[Screenshot](https://minecraft.wiki/w/Screenshot "Screenshot") * [![](/images/EnvSprite_scoreboard.png?38feb)](https://minecraft.wiki/w/Statistics "Statistics")[Statistics](https://minecraft.wiki/w/Statistics "Statistics") * [![](/images/ItemSprite_book.png?791a5)](https://minecraft.wiki/w/Telemetry "Telemetry")[Telemetry](https://minecraft.wiki/w/Telemetry "Telemetry") * [![](/images/ItemSprite_clock.png?30324)](https://minecraft.wiki/w/Tick "Tick")[Tick](https://minecraft.wiki/w/Tick "Tick") * [![](/images/ItemSprite_wheat-seeds.png?b83e5)](https://minecraft.wiki/w/Random_Tick "Random Tick")[Random Tick](https://minecraft.wiki/w/Random_Tick "Random Tick") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/UUID "UUID")[UUID](https://minecraft.wiki/w/UUID "UUID") * [![](/images/BlockSprite_computer.png?e0c37)](https://minecraft.wiki/w/JSON "JSON")[JSON](https://minecraft.wiki/w/JSON "JSON") | | [General format](https://minecraft.wiki/w/Development_resources "Development resources") | * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Java_Edition_data_values "Java Edition data values")[Data values](https://minecraft.wiki/w/Java_Edition_data_values "Java Edition data values")   + [![](/images/LegacyBlockSprite_bricks-je1.png?9a58b)](https://minecraft.wiki/w/Java_Edition_Classic_data_values "Java Edition Classic data values")[Classic](https://minecraft.wiki/w/Java_Edition_Classic_data_values "Java Edition Classic data values")     - [Remake](https://minecraft.wiki/w/Classic_remake_data_values "Classic remake data values")   + [![](/images/EntitySprite_rana.png?3f2f9)](https://minecraft.wiki/w/Java_Edition_Indev_data_values "Java Edition Indev data values")[Indev](https://minecraft.wiki/w/Java_Edition_Indev_data_values "Java Edition Indev data values")   + [![](/images/BlockSprite_stone.png?e9a91)](https://minecraft.wiki/w/Java_Edition_pre-flattening_data_values "Java Edition pre-flattening data values")[Pre-flattening](https://minecraft.wiki/w/Java_Edition_pre-flattening_data_values "Java Edition pre-flattening data values") * [![](/images/EnvSprite_item.png?89d23)](https://minecraft.wiki/w/Data_component_format "Data component format")[Data component format](https://minecraft.wiki/w/Data_component_format "Data component format")   + [![](/images/BlockSprite_test-block-start.png?35191)](https://minecraft.wiki/w/Data_component_predicate "Data component predicate")[Predicate](https://minecraft.wiki/w/Data_component_predicate "Data component predicate") * [![](/images/EnvSprite_entities.png?94711)](https://minecraft.wiki/w/Entity_format "Entity format")[Entity format](https://minecraft.wiki/w/Entity_format "Entity format") * [![](/images/BlockSprite_chest.png?15d81)](https://minecraft.wiki/w/Block_entity_format "Block entity format")[Block entity format](https://minecraft.wiki/w/Block_entity_format "Block entity format") * [![](/images/ItemSprite_map.png?05f8c)](https://minecraft.wiki/w/Map_item_format "Map item format")[Map item format](https://minecraft.wiki/w/Map_item_format "Map item format") * [NBT Compound / JSON Object] NBT format * [![](/images/EffectSprite_particle-healing.png?1357a)](https://minecraft.wiki/w/Particle_format "Particle format")[Particle format](https://minecraft.wiki/w/Particle_format "Particle format") * [![](/images/ItemSprite_book-and-quill.png?f190b)](https://minecraft.wiki/w/Text_component_format "Text component format")[Text component format](https://minecraft.wiki/w/Text_component_format "Text component format") * [§](https://minecraft.wiki/w/Formatting_codes "Formatting codes") [Formatting codes](https://minecraft.wiki/w/Formatting_codes "Formatting codes") * [![](/images/thumb/Movement_hint.png/16px-Movement_hint.png?92667)](https://minecraft.wiki/w/Key_codes "Key codes")[Key codes](https://minecraft.wiki/w/Key_codes "Key codes") * [![](/images/thumb/Dice.png/14px-Dice.png?a4e84)](https://minecraft.wiki/w/Random_sequence_format "Random sequence format")[Random sequence](https://minecraft.wiki/w/Random_sequence_format "Random sequence format") * [![](/images/BlockSprite_structure-block.png?381fc)](https://minecraft.wiki/w/Structure_file "Structure file")[Structure file format](https://minecraft.wiki/w/Structure_file "Structure file")   + [![](/images/EnvSprite_chunk.png?b2cf1)](https://minecraft.wiki/w/Schematic_file_format "Schematic file format")[Schematic file format](https://minecraft.wiki/w/Schematic_file_format "Schematic file format") | | [World](https://minecraft.wiki/w/World "World") | * [![](/images/EnvSprite_altitude.png?9b274)](https://minecraft.wiki/w/Heightmap "Heightmap")[Heightmap](https://minecraft.wiki/w/Heightmap "Heightmap") * [![](/images/EnvSprite_mountain.png?2e0ae)](https://minecraft.wiki/w/World_seed "World seed")[Seed](https://minecraft.wiki/w/World_seed "World seed")   + [Anomalous](https://minecraft.wiki/w/Anomalous_world_seeds "Anomalous world seeds") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Data_version "Data version")[Data version](https://minecraft.wiki/w/Data_version "Data version")  |  |  | | --- | --- | | Legacy | * [![](/images/EnvSprite_chunk.png?b2cf1)](https://minecraft.wiki/w/Spawn_chunk "Spawn chunk")[Spawn chunk](https://minecraft.wiki/w/Spawn_chunk "Spawn chunk") | | [Level format](https://minecraft.wiki/w/Java_Edition_level_format "Java Edition level format") | * [![](/images/BlockSprite_anvil.png?a26c9)](https://minecraft.wiki/w/Anvil_file_format "Anvil file format")[Anvil file format](https://minecraft.wiki/w/Anvil_file_format "Anvil file format") * [![](/images/EnvSprite_chunk.png?b2cf1)](https://minecraft.wiki/w/Chunk_format "Chunk format")[Chunk format](https://minecraft.wiki/w/Chunk_format "Chunk format") * [![](/images/EntitySprite_steve.png?856f8)](https://minecraft.wiki/w/Player.dat_format "Player.dat format")[Player format](https://minecraft.wiki/w/Player.dat_format "Player.dat format") * [![](/images/BlockSprite_lodestone.png?00f1a)](https://minecraft.wiki/w/Point_of_Interest_format "Point of Interest format")[Point of Interest format](https://minecraft.wiki/w/Point_of_Interest_format "Point of Interest format") * [![](/images/EntitySprite_ravager.png?40196)](https://minecraft.wiki/w/Raids.dat_format "Raids.dat format")[raids.dat format](https://minecraft.wiki/w/Raids.dat_format "Raids.dat format") * [![](/images/BlockSprite_chain-command-block.png?0afa8)](https://minecraft.wiki/w/Command_storage_format "Command storage format")[Command storage format](https://minecraft.wiki/w/Command_storage_format "Command storage format") * [![](/images/EnvSprite_scoreboard.png?38feb)](https://minecraft.wiki/w/Scoreboard#NBT_format "Scoreboard")[Scoreboard format](https://minecraft.wiki/w/Scoreboard#NBT_format "Scoreboard")  |  |  | | --- | --- | | Legacy | * [![](/images/LegacyBlockSprite_bricks-je1.png?9a58b)](https://minecraft.wiki/w/Java_Edition_Classic_level_format "Java Edition Classic level format")[Classic level format](https://minecraft.wiki/w/Java_Edition_Classic_level_format "Java Edition Classic level format") * [Classic server protocol](https://minecraft.wiki/w/Classic_server_protocol "Classic server protocol") * [![](/images/EntitySprite_rana.png?3f2f9)](https://minecraft.wiki/w/Java_Edition_Indev_level_format "Java Edition Indev level format")[Indev level format](https://minecraft.wiki/w/Java_Edition_Indev_level_format "Java Edition Indev level format") * [![](/images/EnvSprite_nether-portal.png?47646)](https://minecraft.wiki/w/Java_Edition_Alpha_level_format "Java Edition Alpha level format")[Alpha level format](https://minecraft.wiki/w/Java_Edition_Alpha_level_format "Java Edition Alpha level format")   + [![](/images/LegacyItemSprite_oak-door-revision-1.png?b7426)](https://minecraft.wiki/w/Zone_file_format "Zone file format")[Zone file format](https://minecraft.wiki/w/Zone_file_format "Zone file format") * [![](/images/ItemSprite_locked-map.png?c4112)](https://minecraft.wiki/w/Region_file_format "Region file format")[Region file format](https://minecraft.wiki/w/Region_file_format "Region file format") * [![](/images/Servers.png?b1dc2)](https://minecraft.wiki/w/Server_level.dat "Server level.dat")[server\_level.dat format](https://minecraft.wiki/w/Server_level.dat "Server level.dat") * [![](/images/EnvSprite_new-village.png?3e8a5)](https://minecraft.wiki/w/Villages.dat_format "Villages.dat format")[villages.dat format](https://minecraft.wiki/w/Villages.dat_format "Villages.dat format") * [![](/images/EnvSprite_abandoned-mineshaft.png?fab65)](https://minecraft.wiki/w/Generated_structures_data_file_format "Generated structures data file format")[Generated structures format](https://minecraft.wiki/w/Generated_structures_data_file_format "Generated structures data file format") | | | | [.minecraft](https://minecraft.wiki/w/.minecraft ".minecraft") | * ![File archive.png: Sprite image for archive in Minecraft](/images/thumb/File_archive.png/16px-File_archive.png?5ba7d) [client.jar](https://minecraft.wiki/w/Client.jar "Client.jar")   + [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Version.json "Version.json")[version.json](https://minecraft.wiki/w/Version.json "Version.json") * [![](/images/ItemSprite_book-and-quill.png?f190b)](https://minecraft.wiki/w/Client.json "Client.json")[client.json](https://minecraft.wiki/w/Client.json "Client.json") * [![](/images/BlockSprite_command-block.png?e7078)](https://minecraft.wiki/w/Command_history.txt "Command history.txt")[command\_history.txt](https://minecraft.wiki/w/Command_history.txt "Command history.txt") * [![](/images/BlockSprite_chest.png?15d81)](https://minecraft.wiki/w/Launcher_profiles.json "Launcher profiles.json")[launcher\_profiles.json](https://minecraft.wiki/w/Launcher_profiles.json "Launcher profiles.json") * [![](/images/Chat_settings_gear.png?6a179)](https://minecraft.wiki/w/Options.txt "Options.txt")[options.txt](https://minecraft.wiki/w/Options.txt "Options.txt") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Version_manifest.json "Version manifest.json")[version\_manifest.json](https://minecraft.wiki/w/Version_manifest.json "Version manifest.json") * [![](/images/ItemSprite_paper.png?565a1)](https://minecraft.wiki/w/Hotbar.nbt_format "Hotbar.nbt format")[hotbar.nbt format](https://minecraft.wiki/w/Hotbar.nbt_format "Hotbar.nbt format") * [![](/images/Servers.png?b1dc2)](https://minecraft.wiki/w/Servers.dat_format "Servers.dat format")[Server list format](https://minecraft.wiki/w/Servers.dat_format "Servers.dat format") | | Tools | * `F3` [Debug screen](https://minecraft.wiki/w/Debug_screen "Debug screen")   + [hotkey](https://minecraft.wiki/w/Debug_hotkey "Debug hotkey")   + [renderer](https://minecraft.wiki/w/Debug_renderer "Debug renderer") * [![](/images/Mojang_logo.svg?0b294)](https://minecraft.wiki/w/Java_developer_tools "Java developer tools")[Developer Tools](https://minecraft.wiki/w/Java_developer_tools "Java developer tools")   + [![](/images/BlockSprite_test-instance-block.png?27a39)](https://minecraft.wiki/w/GameTest "GameTest")[GameTest](https://minecraft.wiki/w/GameTest "GameTest")   + [DataFixerUpper](https://minecraft.wiki/w/DataFixerUpper "DataFixerUpper")   + [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Debug_property "Debug property")[Debug properties](https://minecraft.wiki/w/Debug_property "Debug property")  |  |  | | --- | --- | | Legacy | * [![](/images/BlockSprite_computer.png?e0c37)](https://minecraft.wiki/w/Obfuscation_map "Obfuscation map")[Obfuscation map](https://minecraft.wiki/w/Obfuscation_map "Obfuscation map") | | | Sound | * [![](/images/BlockSprite_jukebox-side.png?8477e)](https://minecraft.wiki/w/Block_sound_type "Block sound type")[Block sound type](https://minecraft.wiki/w/Block_sound_type "Block sound type") * [![](/images/EnvSprite_chat.png?0dd92)](https://minecraft.wiki/w/Closed_captions "Closed captions")[Closed captions](https://minecraft.wiki/w/Closed_captions "Closed captions") * [![](/images/EnvSprite_ambience.png?d7c92)](https://minecraft.wiki/w/Sounds.json "Sounds.json")[sounds.json](https://minecraft.wiki/w/Sounds.json "Sounds.json") | | [Commands](https://minecraft.wiki/w/Commands "Commands") | * [Brigadier](https://minecraft.wiki/w/Brigadier "Brigadier") * [![](/images/BlockSprite_repeating-command-block.png?1dad0)](https://minecraft.wiki/w/Function_%28Java_Edition%29 "Function (Java Edition)")[Functions](https://minecraft.wiki/w/Function_%28Java_Edition%29 "Function (Java Edition)")   **[All commands](https://minecraft.wiki/w/Template%3ANavbox_commands "Template:Navbox commands")** | | [Launching](https://minecraft.wiki/w/Minecraft_Launcher "Minecraft Launcher") | * [Mojang API](https://minecraft.wiki/w/Mojang_API "Mojang API") * [![](/images/Microsoft_logo.svg?7e87a)](https://minecraft.wiki/w/Microsoft_authentication "Microsoft authentication")[Microsoft authentication](https://minecraft.wiki/w/Microsoft_authentication "Microsoft authentication") * [![](/images/thumb/Java_Edition_icon_3.png/16px-Java_Edition_icon_3.png?f7112)](https://minecraft.wiki/w/Quick_Play "Quick Play")[Quick Play](https://minecraft.wiki/w/Quick_Play "Quick Play")  |  |  | | --- | --- | | Legacy | * [Legacy Minecraft authentication](https://minecraft.wiki/w/Legacy_Minecraft_authentication "Legacy Minecraft authentication") * [Yggdrasil](https://minecraft.wiki/w/Yggdrasil "Yggdrasil") | | | [Protocol](https://minecraft.wiki/w/Java_Edition_protocol "Java Edition protocol") | * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Protocol_version "Protocol version")[Protocol version](https://minecraft.wiki/w/Protocol_version "Protocol version") * [![](/images/ItemSprite_bundle.png?9eb9f)](https://minecraft.wiki/w/Java_Edition_protocol/Packets "Java Edition protocol/Packets")[Packets](https://minecraft.wiki/w/Java_Edition_protocol/Packets "Java Edition protocol/Packets") * [Data types](https://minecraft.wiki/w/Java_Edition_protocol/Data_types "Java Edition protocol/Data types") * [![](/images/BlockSprite_computer.png?e0c37)](https://minecraft.wiki/w/Java_Edition_protocol/Encryption "Java Edition protocol/Encryption")[Encryption](https://minecraft.wiki/w/Java_Edition_protocol/Encryption "Java Edition protocol/Encryption") | | [Server](https://minecraft.wiki/w/Server "Server") | * ![File archive.png: Sprite image for archive in Minecraft](/images/thumb/File_archive.png/16px-File_archive.png?5ba7d) [server.jar](https://minecraft.wiki/w/Server.jar "Server.jar") * [![](/images/BlockSprite_test-instance-block.png?27a39)](https://minecraft.wiki/w/Server.properties "Server.properties")[server.properties](https://minecraft.wiki/w/Server.properties "Server.properties") * [![](/images/BlockSprite_test-instance-block.png?27a39)](https://minecraft.wiki/w/Server/Requirements "Server/Requirements")[Server requirements](https://minecraft.wiki/w/Server/Requirements "Server/Requirements") * [![](/images/BlockSprite_test-block-accept.png?08355)](https://minecraft.wiki/w/Whitelist "Whitelist")[Whitelist](https://minecraft.wiki/w/Whitelist "Whitelist") * [Operator list](https://minecraft.wiki/w/Server#Operator_list "Server")  |  |  | | --- | --- | | Protocols | * [Query](https://minecraft.wiki/w/Query "Query") * [RCON](https://minecraft.wiki/w/RCON "RCON") * [Server Management Protocol](https://minecraft.wiki/w/Minecraft_Server_Management_Protocol "Minecraft Server Management Protocol") | | | Legacy | * [al\_version](https://minecraft.wiki/w/Al_version "Al version") * [![](/images/EnvSprite_item.png?89d23)](https://minecraft.wiki/w/Item_format "Item format")[Item format](https://minecraft.wiki/w/Item_format "Item format") | | |
| | [Data pack](https://minecraft.wiki/w/Data_pack "Data pack") | | | --- | --- | | Components | * [pack.mcmeta](https://minecraft.wiki/w/Pack.mcmeta "Pack.mcmeta") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Pack_format "Pack format")[Pack format](https://minecraft.wiki/w/Pack_format "Pack format") * [![](/images/ItemSprite_map.png?05f8c)](https://minecraft.wiki/w/Advancement_definition "Advancement definition")[Advancements](https://minecraft.wiki/w/Advancement_definition "Advancement definition") * [![](/images/BlockSprite_repeating-command-block.png?1dad0)](https://minecraft.wiki/w/Function_%28Java_Edition%29 "Function (Java Edition)")[Functions](https://minecraft.wiki/w/Function_%28Java_Edition%29 "Function (Java Edition)") * [![](/images/BlockSprite_red-banner.png?8b4d0)](https://minecraft.wiki/w/Item_modifier "Item modifier")[Item modifier](https://minecraft.wiki/w/Item_modifier "Item modifier") * [![](/images/ItemSprite_diamond.png?8f019)](https://minecraft.wiki/w/Loot_table "Loot table")[Loot tables](https://minecraft.wiki/w/Loot_table "Loot table") * [![](/images/BlockSprite_test-block-start.png?35191)](https://minecraft.wiki/w/Predicate "Predicate")[Predicate](https://minecraft.wiki/w/Predicate "Predicate") * [![](/images/BlockSprite_crafting-table.png?6e126)](https://minecraft.wiki/w/Recipe_%28Java_Edition%29 "Recipe (Java Edition)")[Recipe](https://minecraft.wiki/w/Recipe_%28Java_Edition%29 "Recipe (Java Edition)") * [![](/images/EffectSprite_strength.png?05e79)](https://minecraft.wiki/w/Damage_type "Damage type")[Damage type](https://minecraft.wiki/w/Damage_type "Damage type") * [![](/images/EnvSprite_chat.png?0dd92)](https://minecraft.wiki/w/Chat_type "Chat type")[Chat type](https://minecraft.wiki/w/Chat_type "Chat type") * [![](/images/ItemSprite_enchanted-book.png?b7877)](https://minecraft.wiki/w/Enchantment_definition "Enchantment definition")[Enchantment](https://minecraft.wiki/w/Enchantment_definition "Enchantment definition") * [![](/images/BlockSprite_enchanting-table.png?45e2c)](https://minecraft.wiki/w/Enchantment_provider "Enchantment provider")[Enchantment provider](https://minecraft.wiki/w/Enchantment_provider "Enchantment provider") * [![](/images/ItemSprite_painting.png?55d20)](https://minecraft.wiki/w/Painting_variant_definition "Painting variant definition")[Painting variant](https://minecraft.wiki/w/Painting_variant_definition "Painting variant definition") * [![](/images/BlockSprite_white-banner.png?8b4d0)](https://minecraft.wiki/w/Banner_pattern_definition "Banner pattern definition")[Banner pattern](https://minecraft.wiki/w/Banner_pattern_definition "Banner pattern definition") * [![](/images/ItemSprite_goat-horn.png?e5a9f)](https://minecraft.wiki/w/Instrument_definition "Instrument definition")[Instrument](https://minecraft.wiki/w/Instrument_definition "Instrument definition") * [![](/images/BlockSprite_jukebox.png?86205)](https://minecraft.wiki/w/Jukebox_song_definition "Jukebox song definition")[Jukebox song](https://minecraft.wiki/w/Jukebox_song_definition "Jukebox song definition") * [![](/images/BlockSprite_trial-spawner.png?0a3dc)](https://minecraft.wiki/w/Trial_spawner_configuration "Trial spawner configuration")[Trial spawner configuration](https://minecraft.wiki/w/Trial_spawner_configuration "Trial spawner configuration") * [![](/images/EntitySprite_pig.png?5435e)](https://minecraft.wiki/w/Mob_variant_definitions "Mob variant definitions")[Mob variants](https://minecraft.wiki/w/Mob_variant_definitions "Mob variant definitions") * [![](/images/ItemSprite_paper.png?565a1)](https://minecraft.wiki/w/Dialog "Dialog")[Dialog](https://minecraft.wiki/w/Dialog "Dialog") * [![](/images/ItemSprite_wayfinder-armor-trim.png?ffaf0)](https://minecraft.wiki/w/Armor_trim_definition "Armor trim definition")[Armor trim](https://minecraft.wiki/w/Armor_trim_definition "Armor trim definition") * [![](/images/ItemSprite_footprint.png?1c844)](https://minecraft.wiki/w/Slot_sources "Slot sources")[Slot sources](https://minecraft.wiki/w/Slot_sources "Slot sources") * [![](/images/ItemSprite_clock.png?30324)](https://minecraft.wiki/w/Timeline "Timeline")[Timeline](https://minecraft.wiki/w/Timeline "Timeline") * [![](/images/EntitySprite_villager.png?05433)](https://minecraft.wiki/w/Villager_trade_definition "Villager trade definition")[Villager trade](https://minecraft.wiki/w/Villager_trade_definition "Villager trade definition") * [Trade set](https://minecraft.wiki/w/Trade_set "Trade set") * [World Clock](https://minecraft.wiki/w/World_Clock "World Clock") * [![](/images/EntitySprite_sulfur-cube.png?ad68d)](https://minecraft.wiki/w/Sulfur_cube_archetype_definition "Sulfur cube archetype definition")[Sulfur cube archetype](https://minecraft.wiki/w/Sulfur_cube_archetype_definition "Sulfur cube archetype definition")​[*upcoming: [JE 26.2](https://minecraft.wiki/w/Java_Edition_26.2 "Java Edition 26.2")*]  |  |  | | --- | --- | | [Tag](https://minecraft.wiki/w/Tag_%28Java_Edition%29 "Tag (Java Edition)") | * [![](/images/BlockSprite_grass-block.png?97c2e)](https://minecraft.wiki/w/Block_tag_%28Java_Edition%29 "Block tag (Java Edition)")[Block](https://minecraft.wiki/w/Block_tag_%28Java_Edition%29 "Block tag (Java Edition)") * [![](/images/EnvSprite_item.png?89d23)](https://minecraft.wiki/w/Item_tag_%28Java_Edition%29 "Item tag (Java Edition)")[Item](https://minecraft.wiki/w/Item_tag_%28Java_Edition%29 "Item tag (Java Edition)") * [![](/images/BlockSprite_repeating-command-block.png?1dad0)](https://minecraft.wiki/w/Function_tag_%28Java_Edition%29 "Function tag (Java Edition)")[Function](https://minecraft.wiki/w/Function_tag_%28Java_Edition%29 "Function tag (Java Edition)") * [![](/images/ItemSprite_water-bucket.png?6e72b)](https://minecraft.wiki/w/Fluid_tag_%28Java_Edition%29 "Fluid tag (Java Edition)")[Fluid](https://minecraft.wiki/w/Fluid_tag_%28Java_Edition%29 "Fluid tag (Java Edition)") * [![](/images/EnvSprite_entities.png?94711)](https://minecraft.wiki/w/Entity_type_tag_%28Java_Edition%29 "Entity type tag (Java Edition)")[Entity type](https://minecraft.wiki/w/Entity_type_tag_%28Java_Edition%29 "Entity type tag (Java Edition)") * [![](/images/BlockSprite_sculk-sensor.png?ccbdb)](https://minecraft.wiki/w/Game_event_tag_%28Java_Edition%29 "Game event tag (Java Edition)")[Game event](https://minecraft.wiki/w/Game_event_tag_%28Java_Edition%29 "Game event tag (Java Edition)") * [![](/images/BiomeSprite_forest.png?98e29)](https://minecraft.wiki/w/Biome_tag_%28Java_Edition%29 "Biome tag (Java Edition)")[Biome](https://minecraft.wiki/w/Biome_tag_%28Java_Edition%29 "Biome tag (Java Edition)") * [![](/images/EnvSprite_superflat.png?54c14)](https://minecraft.wiki/w/Flat_level_generator_preset_tag_%28Java_Edition%29 "Flat level generator preset tag (Java Edition)")[Flat level generator preset](https://minecraft.wiki/w/Flat_level_generator_preset_tag_%28Java_Edition%29 "Flat level generator preset tag (Java Edition)") * [![](/images/EnvSprite_mountain.png?2e0ae)](https://minecraft.wiki/w/World_preset_tag_%28Java_Edition%29 "World preset tag (Java Edition)")[World preset](https://minecraft.wiki/w/World_preset_tag_%28Java_Edition%29 "World preset tag (Java Edition)") * [![](/images/EnvSprite_jungle-pyramid.png?736e3)](https://minecraft.wiki/w/Structure_tag_%28Java_Edition%29 "Structure tag (Java Edition)")[Structure](https://minecraft.wiki/w/Structure_tag_%28Java_Edition%29 "Structure tag (Java Edition)") * [![](/images/BlockSprite_lodestone.png?00f1a)](https://minecraft.wiki/w/Point_of_interest_type_tag_%28Java_Edition%29 "Point of interest type tag (Java Edition)")[Point of interest type](https://minecraft.wiki/w/Point_of_interest_type_tag_%28Java_Edition%29 "Point of interest type tag (Java Edition)") * [![](/images/ItemSprite_painting.png?55d20)](https://minecraft.wiki/w/Painting_variant_tag_%28Java_Edition%29 "Painting variant tag (Java Edition)")[Painting variant](https://minecraft.wiki/w/Painting_variant_tag_%28Java_Edition%29 "Painting variant tag (Java Edition)") * [![](/images/BlockSprite_white-banner.png?8b4d0)](https://minecraft.wiki/w/Banner_pattern_tag_%28Java_Edition%29 "Banner pattern tag (Java Edition)")[Banner pattern](https://minecraft.wiki/w/Banner_pattern_tag_%28Java_Edition%29 "Banner pattern tag (Java Edition)") * [![](/images/ItemSprite_goat-horn.png?e5a9f)](https://minecraft.wiki/w/Instrument_tag_%28Java_Edition%29 "Instrument tag (Java Edition)")[Instrument](https://minecraft.wiki/w/Instrument_tag_%28Java_Edition%29 "Instrument tag (Java Edition)") * ![❤️](/images/Heart_%28icon%29.png?faf83) [Damage type](https://minecraft.wiki/w/Damage_type_tag_%28Java_Edition%29 "Damage type tag (Java Edition)") * [![](/images/ItemSprite_enchanted-book.png?b7877)](https://minecraft.wiki/w/Enchantment_tag_%28Java_Edition%29 "Enchantment tag (Java Edition)")[Enchantment](https://minecraft.wiki/w/Enchantment_tag_%28Java_Edition%29 "Enchantment tag (Java Edition)") * [![](/images/ItemSprite_paper.png?565a1)](https://minecraft.wiki/w/Dialog_tag_%28Java_Edition%29 "Dialog tag (Java Edition)")[Dialog](https://minecraft.wiki/w/Dialog_tag_%28Java_Edition%29 "Dialog tag (Java Edition)") * [![](/images/ItemSprite_clock.png?30324)](https://minecraft.wiki/w/Timeline_tag_%28Java_Edition%29 "Timeline tag (Java Edition)")[Timeline](https://minecraft.wiki/w/Timeline_tag_%28Java_Edition%29 "Timeline tag (Java Edition)") * [![](/images/ItemSprite_water-bottle.png?fe7c2)](https://minecraft.wiki/w/Potion_tag_%28Java_Edition%29 "Potion tag (Java Edition)")[Potion](https://minecraft.wiki/w/Potion_tag_%28Java_Edition%29 "Potion tag (Java Edition)") * [![](/images/EntitySprite_villager.png?05433)](https://minecraft.wiki/w/Villager_trade_tag_%28Java_Edition%29 "Villager trade tag (Java Edition)")[Villager trade](https://minecraft.wiki/w/Villager_trade_tag_%28Java_Edition%29 "Villager trade tag (Java Edition)") * [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Configured_feature_tag_%28Java_Edition%29 "Configured feature tag (Java Edition)")[Configured feature](https://minecraft.wiki/w/Configured_feature_tag_%28Java_Edition%29 "Configured feature tag (Java Edition)") | | [GameTest](https://minecraft.wiki/w/GameTest "GameTest") | * [![](/images/BlockSprite_test-block-start.png?35191)](https://minecraft.wiki/w/Test_environment_definition "Test environment definition")[Test environment](https://minecraft.wiki/w/Test_environment_definition "Test environment definition") * [![](/images/BlockSprite_test-instance-block.png?27a39)](https://minecraft.wiki/w/Test_instance_definition "Test instance definition")[Test instance](https://minecraft.wiki/w/Test_instance_definition "Test instance definition") | | [World generation](https://minecraft.wiki/w/Custom_world_generation "Custom world generation") | * [Dimension](https://minecraft.wiki/w/Dimension_definition "Dimension definition") * [![](/images/EnvSprite_nether-portal.png?47646)](https://minecraft.wiki/w/Dimension_type "Dimension type")[Dimension type](https://minecraft.wiki/w/Dimension_type "Dimension type") * [![](/images/EnvSprite_mountain.png?2e0ae)](https://minecraft.wiki/w/World_preset_definition "World preset definition")[World preset](https://minecraft.wiki/w/World_preset_definition "World preset definition") * [![](/images/EnvSprite_biomes.png?0a976)](https://minecraft.wiki/w/Biome_definition "Biome definition")[Biomes](https://minecraft.wiki/w/Biome_definition "Biome definition") * [![](/images/EnvSprite_cave.png?47a17)](https://minecraft.wiki/w/Carver_definition "Carver definition")[Carver](https://minecraft.wiki/w/Carver_definition "Carver definition") * [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Configured_feature "Configured feature")[Configured feature](https://minecraft.wiki/w/Configured_feature "Configured feature")   + [![](/images/EnvSprite_oak.png?742a4)](https://minecraft.wiki/w/Tree_definition "Tree definition")[Tree](https://minecraft.wiki/w/Tree_definition "Tree definition") * [![](/images/EnvSprite_map.png?b863e)](https://minecraft.wiki/w/Placed_feature "Placed feature")[Placed feature](https://minecraft.wiki/w/Placed_feature "Placed feature") * [Environment attribute](https://minecraft.wiki/w/Environment_attribute "Environment attribute")  |  |  | | --- | --- | | [Noise settings](https://minecraft.wiki/w/Noise_settings "Noise settings") | * [![](/images/EnvSprite_mountain.png?2e0ae)](https://minecraft.wiki/w/Noise_router "Noise router")[Noise router](https://minecraft.wiki/w/Noise_router "Noise router") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Density_function "Density function")[Density function](https://minecraft.wiki/w/Density_function "Density function") * [Noises](https://minecraft.wiki/w/Noise "Noise") * [![](/images/EnvSprite_surface.png?75bf7)](https://minecraft.wiki/w/Surface_rule "Surface rule")[Surface rule](https://minecraft.wiki/w/Surface_rule "Surface rule") | | [Structures](https://minecraft.wiki/w/Structure_definition "Structure definition") | * [![](/images/EnvSprite_abandoned-mineshaft.png?fab65)](https://minecraft.wiki/w/Structure_set "Structure set")[Structure set](https://minecraft.wiki/w/Structure_set "Structure set") * [![](/images/BlockSprite_jigsaw.png?ec5e3)](https://minecraft.wiki/w/Template_pool "Template pool")[Template pool](https://minecraft.wiki/w/Template_pool "Template pool") * [![](/images/BlockSprite_cracked-stone-bricks.png?f3f1d)](https://minecraft.wiki/w/Processor_list "Processor list")[Processor list](https://minecraft.wiki/w/Processor_list "Processor list") * [![](/images/EnvSprite_nether-fossil.png?93621)](https://minecraft.wiki/w/Structure_file "Structure file")[Structure templates](https://minecraft.wiki/w/Structure_file "Structure file") | | Removed | * [![](/images/ItemSprite_iron-pickaxe.png?77536)](https://minecraft.wiki/w/Configured_surface_builder "Configured surface builder")[Configured surface builder](https://minecraft.wiki/w/Configured_surface_builder "Configured surface builder") | | | | Data packs | * [![](/images/BlockSprite_deepslate.png?d7361)](https://minecraft.wiki/w/Caves_%26_Cliffs_Prototype_Data_Pack "Caves & Cliffs Prototype Data Pack")[Caves & Cliffs Prototype Data Pack](https://minecraft.wiki/w/Caves_%26_Cliffs_Prototype_Data_Pack "Caves & Cliffs Prototype Data Pack") * [![](/images/ItemSprite_magical-painting.png?b0bf0)](https://minecraft.wiki/w/Phantom_Frames "Phantom Frames")[Phantom Frames](https://minecraft.wiki/w/Phantom_Frames "Phantom Frames") | | Tutorials | * [![](/images/thumb/EnvSprite_autosave.png/16px-EnvSprite_autosave.png?a55e7)](https://minecraft.wiki/w/Tutorial%3AImporting_a_data_pack "Tutorial:Importing a data pack")[Importing](https://minecraft.wiki/w/Tutorial%3AImporting_a_data_pack "Tutorial:Importing a data pack") * [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Tutorial%3ACreating_a_data_pack "Tutorial:Creating a data pack")[Creating](https://minecraft.wiki/w/Tutorial%3ACreating_a_data_pack "Tutorial:Creating a data pack") * [Optimizing](https://minecraft.wiki/w/Tutorial%3AOptimizing_a_data_pack "Tutorial:Optimizing a data pack") * [![](/images/BlockSprite_command-block.png?e7078)](https://minecraft.wiki/w/Tutorial%3ACommand_blocks_and_functions "Tutorial:Command blocks and functions")[Command blocks and functions](https://minecraft.wiki/w/Tutorial%3ACommand_blocks_and_functions "Tutorial:Command blocks and functions") * [Repairing a world corrupted by a data pack](https://minecraft.wiki/w/Tutorial%3ARepairing_a_world_corrupted_by_a_data_pack "Tutorial:Repairing a world corrupted by a data pack")  |  |  | | --- | --- | | Content | * [![](/images/ItemSprite_enchanted-book.png?b7877)](https://minecraft.wiki/w/Tutorial%3AAdding_custom_enchantments "Tutorial:Adding custom enchantments")[Custom enchantments](https://minecraft.wiki/w/Tutorial%3AAdding_custom_enchantments "Tutorial:Adding custom enchantments") * [![](/images/ItemSprite_painting.png?55d20)](https://minecraft.wiki/w/Tutorial%3AAdding_custom_paintings "Tutorial:Adding custom paintings")[Custom paintings](https://minecraft.wiki/w/Tutorial%3AAdding_custom_paintings "Tutorial:Adding custom paintings") * [![](/images/ItemSprite_armor-trim.png?1d672)](https://minecraft.wiki/w/Tutorial%3AAdding_custom_trims "Tutorial:Adding custom trims")[Custom trims](https://minecraft.wiki/w/Tutorial%3AAdding_custom_trims "Tutorial:Adding custom trims") | | World generation | * [![](/images/EnvSprite_other-portal.png?ca57b)](https://minecraft.wiki/w/Tutorial%3AAdding_a_new_dimension "Tutorial:Adding a new dimension")[New dimension](https://minecraft.wiki/w/Tutorial%3AAdding_a_new_dimension "Tutorial:Adding a new dimension") * [![](/images/EnvSprite_lunar-base.png?648e4)](https://minecraft.wiki/w/Tutorial%3ACustom_structures "Tutorial:Custom structures")[Custom structures](https://minecraft.wiki/w/Tutorial%3ACustom_structures "Tutorial:Custom structures") | | | |
| | [Resource pack](https://minecraft.wiki/w/Resource_pack "Resource pack") | | | --- | --- | | Components | * [pack.mcmeta](https://minecraft.wiki/w/Pack.mcmeta "Pack.mcmeta") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Pack_format "Pack format")[Pack format](https://minecraft.wiki/w/Pack_format "Pack format") * [![](/images/EnvSprite_language.png?39da2)](https://minecraft.wiki/w/Resource_pack#Language "Resource pack")[Language](https://minecraft.wiki/w/Resource_pack#Language "Resource pack") * [![](/images/EntitySprite_creeper.png?703e9)](https://minecraft.wiki/w/Model "Model")[Models](https://minecraft.wiki/w/Model "Model") * [![](/images/BlockSprite_double-stone-slab.png?62750)](https://minecraft.wiki/w/Blockstates_definition "Blockstates definition")[Blockstates](https://minecraft.wiki/w/Blockstates_definition "Blockstates definition") * [![](/images/EnvSprite_item.png?89d23)](https://minecraft.wiki/w/Items_model_definition "Items model definition")[Items](https://minecraft.wiki/w/Items_model_definition "Items model definition") * [![](/images/EnvSprite_ambience.png?d7c92)](https://minecraft.wiki/w/Sound "Sound")[Sounds](https://minecraft.wiki/w/Sound "Sound") ([sounds.json](https://minecraft.wiki/w/Sounds.json "Sounds.json")) * [Shaders](https://minecraft.wiki/w/Shader "Shader") * [![](/images/EnvSprite_texture-pack.png?a4213)](https://minecraft.wiki/w/Resource_pack#Textures "Resource pack")[Textures](https://minecraft.wiki/w/Resource_pack#Textures "Resource pack") * [![](/images/ItemSprite_compass.png?2364d)](https://minecraft.wiki/w/Atlas "Atlas")[Atlases](https://minecraft.wiki/w/Atlas "Atlas") * [Aa](https://minecraft.wiki/w/Font "Font") [Fonts](https://minecraft.wiki/w/Font "Font") * [![](/images/BlockSprite_oak-leaves.png?81553)](https://minecraft.wiki/w/Resource_pack#Colormaps "Resource pack")[Colormaps](https://minecraft.wiki/w/Resource_pack#Colormaps "Resource pack") * ![File file.png: Sprite image for file in Minecraft](/images/thumb/File_file.png/16px-File_file.png?e19ce) [Texts](https://minecraft.wiki/w/Resource_pack#Texts "Resource pack") * [![](/images/Locator_Bar_icon_bowtie.png?a8cd8)](https://minecraft.wiki/w/Waypoint_style "Waypoint style")[Waypoint styles](https://minecraft.wiki/w/Waypoint_style "Waypoint style") * [regional\_compliancies.json](https://minecraft.wiki/w/Resource_pack#Regional_compliancies_warnings "Resource pack") * [![](/images/ItemSprite_all-iron-armor.png?87e31)](https://minecraft.wiki/w/Equipment "Equipment")[Equipment](https://minecraft.wiki/w/Equipment "Equipment") | | Debug | * [Missing font character](https://minecraft.wiki/w/Missing_font_character "Missing font character") * [![](/images/BlockSprite_missingno.png?031f4)](https://minecraft.wiki/w/Missing_model "Missing model")[Missing model](https://minecraft.wiki/w/Missing_model "Missing model") * [![](/images/BlockSprite_missingno.png?031f4)](https://minecraft.wiki/w/Missing_texture "Missing texture")[Missing texture](https://minecraft.wiki/w/Missing_texture "Missing texture") | | Tools | * [Slicer](https://minecraft.wiki/w/Slicer "Slicer")  |  |  | | --- | --- | | Legacy | * [Texture Ender](https://minecraft.wiki/w/Texture_Ender "Texture Ender") * [Unstitcher](https://minecraft.wiki/w/Unstitcher "Unstitcher") | | | Tutorials | * [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Tutorial%3ACreating_a_resource_pack "Tutorial:Creating a resource pack")[Creating](https://minecraft.wiki/w/Tutorial%3ACreating_a_resource_pack "Tutorial:Creating a resource pack") * [![](/images/Download.png?048e3)](https://minecraft.wiki/w/Tutorial%3ALoading_a_resource_pack "Tutorial:Loading a resource pack")[Loading](https://minecraft.wiki/w/Tutorial%3ALoading_a_resource_pack "Tutorial:Loading a resource pack") * [![](/images/EnvSprite_fluids.png?58a6a)](https://minecraft.wiki/w/Tutorial%3AModels "Tutorial:Models")[Models](https://minecraft.wiki/w/Tutorial%3AModels "Tutorial:Models") * [![](/images/EnvSprite_ambience.png?d7c92)](https://minecraft.wiki/w/Tutorial%3ASound_directory "Tutorial:Sound directory")[Sound directory](https://minecraft.wiki/w/Tutorial%3ASound_directory "Tutorial:Sound directory") | | |

Retrieved from "<https://minecraft.wiki/w/NBT_format?oldid=3597659>"

[Categories](https://minecraft.wiki/w/Special%3ACategories "Special:Categories"):

* [Articles missing technical information](https://minecraft.wiki/w/Category%3AArticles_missing_technical_information "Category:Articles missing technical information")
* [Java Edition technical](https://minecraft.wiki/w/Category%3AJava_Edition_technical "Category:Java Edition technical")

Hidden categories:

* [Verify](https://minecraft.wiki/w/Category%3AVerify "Category:Verify")
* [Minecraft Work in progress](https://minecraft.wiki/w/Category%3AMinecraft_Work_in_progress "Category:Minecraft Work in progress")
* [Minecraft Work in progress with a note](https://minecraft.wiki/w/Category%3AMinecraft_Work_in_progress_with_a_note "Category:Minecraft Work in progress with a note")
* [Java Edition specific information](https://minecraft.wiki/w/Category%3AJava_Edition_specific_information "Category:Java Edition specific information")
* [Information needed](https://minecraft.wiki/w/Category%3AInformation_needed "Category:Information needed")

## Navigation menu

### Personal tools

* [Create account](https://minecraft.wiki/w/Special%3ACreateAccount?returnto=NBT+format "You are encouraged to create an account and log in; however, it is not mandatory")
* [Log in](https://minecraft.wiki/w/Special%3AUserLogin?returnto=NBT+format "You are encouraged to log in; however, it is not mandatory [o]")

### associated-pages

* [Page](https://minecraft.wiki/w/NBT_format "View the content page [c]")
* [Talk](https://minecraft.wiki/w/Talk%3ANBT_format "Talk about the content page [t]")

[ ]

English

### Views

* [Read](https://minecraft.wiki/w/NBT_format)
* [Edit](https://minecraft.wiki/w/NBT_format?veaction=edit "Edit this page [v]")
* [Edit source](https://minecraft.wiki/w/NBT_format?action=edit "Edit the source code of this page [e]")
* [View history](https://minecraft.wiki/w/NBT_format?action=history "Past revisions of this page [h]")
