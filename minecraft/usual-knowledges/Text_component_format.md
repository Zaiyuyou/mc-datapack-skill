# Text component format

From Minecraft Wiki

[Jump to navigation](#mw-head)
[Jump to search](#searchInput)

![](/images/Disambig_color.svg?2db52) This article is about text component format. For the item components used in [*Bedrock Edition*](https://minecraft.wiki/w/Bedrock_Edition "Bedrock Edition"), see [Item components](https://minecraft.wiki/w/Item_components "Item components"). For the item components used in [*Java Edition*](https://minecraft.wiki/w/Java_Edition "Java Edition"), see [Data component format](https://minecraft.wiki/w/Data_component_format "Data component format").

The **text component format**, historically also known as **raw JSON text**, is used by *Minecraft* to send and display rich-text to players. It can also be sent by players themselves using commands (such as `/[tellraw](https://minecraft.wiki/w/Commands/tellraw "Commands/tellraw")` and `/[title](https://minecraft.wiki/w/Commands/title "Commands/title")`) and [data packs](https://minecraft.wiki/w/Data_pack "Data pack").

[ ]

## Contents

- [Text component format](#text-component-format)
  - [Contents](#contents)
  - [*Java Edition*](#java-edition)
    - [Content types](#content-types)
      - [Plain Text](#plain-text)
      - [Translated Text](#translated-text)
      - [Scoreboard Value](#scoreboard-value)
      - [Entity Names](#entity-names)
      - [Keybind](#keybind)
      - [NBT Values](#nbt-values)
      - [Object](#object)
        - [Atlas Object Type](#atlas-object-type)
        - [Player Object Type](#player-object-type)
    - [Component resolution](#component-resolution)
    - [Click events](#click-events)
      - [open\_url](#open_url)
      - [open\_file](#open_file)
      - [run\_command](#run_command)
      - [suggest\_command](#suggest_command)
      - [change\_page](#change_page)
      - [copy\_to\_clipboard](#copy_to_clipboard)
      - [show\_dialog](#show_dialog)
      - [custom](#custom)
    - [Hover events](#hover-events)
      - [show\_text](#show_text)
      - [show\_item](#show_item)
      - [show\_entity](#show_entity)
  - [*Bedrock Edition*](#bedrock-edition)
    - [Appending](#appending)
    - [Breaking lines](#breaking-lines)
    - [Translate](#translate)
    - [With](#with)
    - [%%s](#s)
    - [Multiple %s](#multiple-s)
    - [Ordering with %%#](#ordering-with)
    - [Formatting](#formatting)
  - [History](#history)
    - [*Java Edition*](#java-edition-1)
    - [*Bedrock Edition*](#bedrock-edition-1)
  - [See also](#see-also)
  - [Notes](#notes)
  - [References](#references)
  - [External links](#external-links)
  - [Navigation](#navigation)
  - [Navigation menu](#navigation-menu)
    - [Personal tools](#personal-tools)
    - [associated-pages](#associated-pages)
    - [Views](#views)

## *Java Edition*


![](/images/Disambig_color.svg?2db52) For text component format used in versions before [Java Edition 1.21.5](https://minecraft.wiki/w/Java_Edition_1.21.5 "Java Edition 1.21.5"), see [Text component format/Before Java Edition 1.21.5](https://minecraft.wiki/w/Text_component_format/Before_Java_Edition_1.21.5 "Text component format/Before Java Edition 1.21.5").

Text components are written in [SNBT](https://minecraft.wiki/w/NBT_format#SNBT_format "NBT format"), for example `{text: "Hello world"}`. They are used for rich-text formatting in [written books](https://minecraft.wiki/w/Written_book "Written book"), [signs](https://minecraft.wiki/w/Sign "Sign"), custom names and the `/[tellraw](https://minecraft.wiki/w/Commands/tellraw "Commands/tellraw")`, `/[title](https://minecraft.wiki/w/Commands/title "Commands/title")`, `/[bossbar](https://minecraft.wiki/w/Commands/bossbar "Commands/bossbar")`, `/[scoreboard](https://minecraft.wiki/w/Commands/scoreboard "Commands/scoreboard")` and `/[team](https://minecraft.wiki/w/Commands/team "Commands/team")` commands.

The format is made up of text components. There is a single root component, which can have child components, which can have their own children and so on. Components can also have formatting and interactivity added to them, which is inherited by their children.

A component can be a [String] string, [NBT List / JSON Array] list or a [NBT Compound / JSON Object] object. Strings and lists are both shorthand for longer object structures, as described below.

* [String] A string containing plain text to display directly. This is the same as an object that only has a [String] text tag. For example, `"A"` and `{text: "A"}` are equivalent.
* [NBT List / JSON Array] A list of components. Same as having all components after the first one appended to the first's [NBT List / JSON Array] extra list. For example, `["A", "B", "C"]` is equivalent to `{text: "A", extra: ["B", "C"]}`. Note that because the later components are actually children of the first one, any formatting applied to the first component is inherited by the later ones. For example, `[{text: "A", color: "red"}, "B", "C"]` will display all three letters with red text.
* [NBT Compound / JSON Object] A text component object. All non-content tags are optional.
  + ***Content***
    - [String] type: Optional. Specifies the content type. One of `["text"](#Plain_Text)`, `["translatable"](#Translated_Text)`, `["score"](#Scoreboard_Value)`, `["selector"](#Entity_Names)`, `["keybind"](#Keybind)`, or `["nbt"](#NBT_Values)`.
    - If [String] type is not present, has an invalid value, or if the required tags for the specified type are not present, the type is determined automatically by checking the object for the following tags: [[String] text](#Plain_Text), [[String] translate](#Translated_Text), [[NBT Compound / JSON Object] score](#Scoreboard_Value), [[String] selector](#Entity_Names), [[String] keybind](#Keybind), and finally [[String] nbt](#NBT_Values). If multiple are present, whichever one comes first in that list is used.
    - Values specific to each content type are described [below](#Content_types).
  + ***Children***
    - [NBT List / JSON Array] extra: A list of additional components to be displayed after this one.
      * A child text component. Child text components inherit all formatting and interactivity from the parent component, unless they explicitly override them.
  + ***Formatting***
    - [String] color: Optional. Changes the color to render the content in the text component object and its child objects. If not present, the parent color will be used instead. The color is specified as a color code or as a color name.
      * `"#<hex>"`, where `<hex>` is a [6-digit hexadecimal color](https://en.wikipedia.org/wiki/Web_colors#Hex_triplet "wikipedia:Web colors"), changes the color to #*<hex>*
      * `"black"` changes the color to
         #000000
      * `"dark_blue"` changes the color to
         #0000AA
      * `"dark_green"` changes the color to
         #00AA00
      * `"dark_aqua"` changes the color to
         #00AAAA
      * `"dark_red"` changes the color to
         #AA0000
      * `"dark_purple"` changes the color to
         #AA00AA
      * `"gold"` changes the color to
         #FFAA00
      * `"gray"` changes the color to
         #AAAAAA
      * `"dark_gray"` changes the color to
         #555555
      * `"blue"` changes the color to
         #5555FF
      * `"green"` changes the color to
         #55FF55
      * `"aqua"` changes the color to
         #55FFFF
      * `"red"` changes the color to
         #FF5555
      * `"light_purple"` changes the color to
         #FF55FF
      * `"yellow"` changes the color to
         #FFFF55
      * `"white"` changes the color to
         #FFFFFF
    - [String] font: Optional. The resource location of the [font](https://minecraft.wiki/w/Resource_pack#Fonts "Resource pack") for this component in the resource pack within `assets/<namespace>/font`. Defaults to `"minecraft:default"`.
    - [Boolean] bold: Optional. Whether to render the content in bold.
    - [Boolean] italic: Optional. Whether to render the content in italics. Note that text that is italicized by default, such as custom item names, can be unitalicized by setting this to `false`.
    - [Boolean] underlined: Optional. Whether to underline the content.
    - [Boolean] strikethrough: Optional. Whether to strikethrough the content.
    - [Boolean] obfuscated: Optional. Whether to render the content obfuscated.
    - [Int] shadow\_color: The color and opacity of the shadow. If omitted, the shadow is 25% the brightness of the text color and 100% the opacity[*[verify](https://minecraft.wiki/w/Special%3ATalkPage/Text_component_format "Special:TalkPage/Text component format")*]. Color codes are the ARGB hex code of the color converted to a decimal number, or can be calculated from the opacity, red, green and blue components using this formula:
      **Alpha[<<](https://en.wikipedia.org/wiki/Logical_shift "wikipedia:Logical shift")24 + Red<<16 + Green<<8 + Blue**
    - [NBT List / JSON Array] shadow\_color: Another format. A list containing 4 floats corresponding to red, green, blue, and opacity values as a fraction (ranged 0 to 1, inclusive) that is automatically converted to the int format.
  + ***Interactivity***
    - [String] insertion: Optional. When the text is shift-clicked by a player, this string is inserted in their chat input. It does not overwrite any existing text the player was writing. This only works in chat messages.
    - [NBT Compound / JSON Object] click\_event: Optional. Allows for events to occur when the player clicks on text. See [§ Click events](#Click_events).
    - [NBT Compound / JSON Object] hover\_event: Optional. Allows for a tooltip to be displayed when the player hovers their mouse over text. See [§ Hover events](#Hover_events).

Due to the [NBT List / JSON Array] extra tag, the above format may be recursively nested to produce complex and functional text strings. However, a text component doesn't have to be complicated at all: virtually all properties are optional and may be left out.

### Content types


Text components can display several types of content. These tags should be included directly into the text component object.

#### Plain Text


Displays plain text.

* [NBT Compound / JSON Object] The text component.
  + [String] type: Optional. Set to `"text"`.
  + [String] text: A string containing plain text to display directly.

#### Translated Text


Displays a translated piece of text from the currently selected [language](https://minecraft.wiki/w/Language "Language"). This uses the client's selected language, so if players with their games set to different languages are logged into the same server, each will see the component in their own language.

Translations are defined in [language files](https://minecraft.wiki/w/Resource_pack#Language "Resource pack") in [resource packs](https://minecraft.wiki/w/Resource_pack "Resource pack"), including the built-in resource pack.

Translations can contain slots for text that is not known ahead of time, such as player names. When displaying the translated text, slots will be filled from a provided list of text components. The slots are defined in the language file, the translate key, the fallback key and generally take the form `%s` (displays the next component in the list), or `%3$s` (displays the third component in the list; replace `3` with whichever index is desired).[[note 1]](#cite_note-1) For example, the built-in English language file contains the translation `"chat.type.advancement.task": "%s has made the advancement %s",`.

* [NBT Compound / JSON Object] The text component.
  + [String] type: Optional. Set to `"translatable"`.
  + [String] translate: A translation identifier, corresponding to the identifiers found in loaded language files. Displayed as the corresponding text in the player's selected language. If no corresponding translation can be found, the identifier itself is used as the translated text.
  + [String] fallback: Optional. If no corresponding translation can be found, this is used as the translated text. Ignored if [String] translate is not present.
  + [NBT List / JSON Array] with: Optional. A list of text components to be inserted into slots in the translation text. Ignored if [String] translate is not present.
    - A text component. If no component is provided for a slot, the slot is displayed as no text.

#### Scoreboard Value


Displays a score from the [scoreboard](https://minecraft.wiki/w/Scoreboard "Scoreboard").

| Requires [component resolution](#Component_resolution). |
| --- |
| This component is resolved into a [String] text component containing the scoreboard value. |

* [NBT Compound / JSON Object] The text component.
  + [String] type: Optional. Set to `"score"`.
  + [NBT Compound / JSON Object] score: Displays a score holder's current score in an objective. Displays nothing if the given score holder or the given objective do not exist, or if the score holder is not tracked in the objective.
    - [String] name: The name of the score holder whose score should be displayed. This can be a [selector](https://minecraft.wiki/w/Selector "Selector") like @p or an explicit name. If the text is a selector, the selector must be guaranteed to never select more than one entity, possibly by adding `limit=1`. If the text is `"*"`, it shows the reader's own score (for example, `/tellraw @a {score: {name: "*", objective: "obj"}}` shows every online player their own score in the "obj" objective).[[note 2]](#cite_note-2)
    - [String] objective: The internal name of the objective to display the player's score in.

#### Entity Names


Displays the name of one or more entities found by a [selector](https://minecraft.wiki/w/Selector "Selector").

If exactly one entity is found, the entity's name is displayed by itself. If more are found, their names are displayed in the form "Name1, Name2, Name3", with gray commas. If none are found, the component is displayed as no text.

Hovering over a name shows a tooltip with the name, type, and [UUID](https://minecraft.wiki/w/UUID "UUID") of the target. Clicking a player's name suggests a command to whisper to that player. Shift-clicking a player's name inserts that name into chat. Shift-clicking a non-player entity's name inserts its UUID into chat.

| Requires [component resolution](#Component_resolution). |
| --- |
| * If the selector finds a single entity,   + If the entity is a player, the component is resolved into a [String] text component containing their name.   + If it is an entity with a [custom name](https://minecraft.wiki/w/Name_Tag "Name Tag"), it is resolved into the text component of the custom name. In all vanilla survival scenarios ([name tag](https://minecraft.wiki/w/Name_tag "Name tag"), [anvil](https://minecraft.wiki/w/Anvil "Anvil")) this will be a [String] text component.   + If it is a non-player entity with no custom name, it is resolved into a [String] translate component containing the translation key for the entity type's name.   The resolved component also has an [String] insertion tag, a [NBT Compound / JSON Object] hover\_event tag with the `show_entity` action, and a [NBT Compound / JSON Object] click\_event tag with the `suggest_command` action (if the entity is a player) added to it to provide the functionality described above. If any of these tags are already present on the original component being resolved, the tag on the original component will be used.   * If more than one entity is found by the selector, the component is resolved into an empty [String] text component, with an [NBT List / JSON Array] extra list containing the individual entity name components (each resolved as in the single entity case) separated by copies of the [Undefined] separator component (or its default, if not present). * If no entities are found by the selector, the component is resolved into an empty [String] text component. |

* [NBT Compound / JSON Object] The text component.
  + [String] type: Optional. Set to `"selector"`.
  + [String] selector: A string containing a [selector](https://minecraft.wiki/w/Selector "Selector").
  + [NBT Compound / JSON Object] separator: Optional, defaults to `{color: "gray", text: ", "}`. A text component. Used as the separator between different names, if the component selects multiple entities.

#### Keybind


Displays the name of the button that is currently bound to a certain [configurable control](https://minecraft.wiki/w/Controls#Configurable_controls "Controls"). This uses the client's own control scheme, so if players with different control schemes are logged into the same server, each will see their own keybind.

* [NBT Compound / JSON Object] The text component.
  + [String] type: Optional. Set to `"keybind"`.
  + [String] keybind: A [keybind identifier](https://minecraft.wiki/w/Controls#Configurable_controls "Controls"), to be displayed as the name of the button that is currently bound to that action. For example, `{keybind: "key.inventory"}` displays "e" if the player is using the default control scheme. As a fallback it displays the translation if it exists.

#### NBT Values


Displays [NBT](https://minecraft.wiki/w/NBT_format "NBT format") values from [entities](https://minecraft.wiki/w/Entity "Entity"), [block entities](https://minecraft.wiki/w/Block_entity "Block entity"), or [command storage](https://minecraft.wiki/w/Commands/data#Storage "Commands/data").

By default, NBT values are displayed as SNBT, with special coloring added to the SNBT keys and values. If [Boolean] plain is set to true, no special coloring is added. If [Boolean] interpret is set to true, the game will attempt to interpret the NBT value as a text component instead of showing it as SNBT. If [Boolean] interpret is true and the NBT value is not a valid text component, it is displayed as no text. If more than one NBT value is found, either by selecting multiple entities or by using a multi-value path, they are displayed in order, with the [Undefined] separator value between them.

| Requires [component resolution](#Component_resolution). |
| --- |
| * If [Boolean] interpret is false, the component is resolved into an empty [String] text component whose [NBT List / JSON Array] extra list contains [String] text components for each part of the SNBT representation.   + Curly brackets, square brackets, commas, colons, semicolons, and spaces (`{}[],:;` ) that are part of the SNBT syntax each get their own single-character plain text components.   + Numbers appear as a single `"gold"` component for the entire numeric part (which includes the negative sign, decimal point, and exponent, if any), followed by an optional `"red"` component for the suffix.   + Non-key string values appear as a plain text component for the open quote, followed by a `"green"` component for the body of the string, followed by another plain text component for the close quote.   + Key-value pairs are preceded by an empty plain text component, and the last pair in a compound is also followed by an empty plain text component.   + Unquoted compound keys appear as an `"aqua"` component containing the body of the key. Quoted compound keys appear as a plain text component for the open quote, whose [NBT List / JSON Array] extra list contains an `"aqua"` component for the body of the key and a plain text component for the close quote. Quoted keys appear to be the only SNBT element whose text components are nested like this.   + The letter `B`, `I`, or `L` at the beginning of a byte, int, or long array appears as a `"red"` component.   + If multiple values are selected, all values after the first will be resolved into an empty [String] text component with an [NBT List / JSON Array] extra list as described above and added to the end of the first's [NBT List / JSON Array] extra list, separated by copies of the [Undefined] separator component.   + If [Boolean] plain is true, none of the SNBT text components get a color, but the component structure remains the same. * If [Boolean] interpret is true, the component is resolved into the text component represented by the NBT value. For any non-content tags that are present on both the resolved text component and the [String] nbt component itself, the tag on the [String] nbt component itself will be used.   + If multiple values are selected, all values after the first will be added to the first's [NBT List / JSON Array] extra list, separated by copies of the [Undefined] separator component. This means that all values after the first will inherit the first value's formatting tags, if any. |

* [NBT Compound / JSON Object] The text component.
  + [String] type: Optional. Set to `"nbt"`.
  + [String] source: Optional. Allowed values are `"block"`, `"entity"`, and `"storage"`, corresponding to the source of the NBT data.
  + [String] nbt: The [NBT path](https://minecraft.wiki/w/NBT_path_format "NBT path format") used for looking up NBT values from an entity, block entity, or storage. Requires one of [String] block, [String] entity, or [String] storage. Having more than one is allowed, but only one is used.[[note 3]](#cite_note-3)
  + [Boolean] interpret: Optional, defaults to false. If true, the game attempts to interpret each NBT value as a text component instead of displaying it as SNBT. Ignored if [String] nbt is not present. Can't be set to true at the same time as [Boolean] plain.
  + [Boolean] plain: Optional, defaults to false. If false, the game will style the SNBT with colors for the keys and values. If true, no coloring is added. Can't be set to true at the same time as [Boolean] interpret. Ignored if [String] nbt is not present.
  + [NBT Compound / JSON Object] separator: Optional, defaults to `{text: ", "}`. A text component. Used as the separator between different tags, if the component selects multiple tags.
  + [String] entity: A string specifying the [target selector](https://minecraft.wiki/w/Selector "Selector") for the entity or entities from which the NBT value is obtained. Ignored if [String] nbt is not present.
  + [String] block: A string specifying the coordinates of the block entity from which the NBT value is obtained. The coordinates can be absolute, [relative](https://minecraft.wiki/w/Commands#Tilde_and_caret_notation "Commands"), or local. Ignored if [String] nbt is not present.
  + [String] storage: A string specifying the [resource location](https://minecraft.wiki/w/Resource_location "Resource location") of the [command storage](https://minecraft.wiki/w/Command_storage "Command storage") from which the NBT value is obtained. Ignored if [String] nbt is not present.

#### Object


Displays objects as single sprites in component messages. Sprites are rendered as 8×8-pixel squares. This will ignore bold and italic styles!

##### Atlas Object Type


When specifying [String] object as `"atlas"`, it displays a single sprite from a [texture atlas](https://minecraft.wiki/w/Texture_atlas "Texture atlas") as a character.

* [NBT Compound / JSON Object] The text component.
  + [String] type: Optional. Defaults to `"object"` if object-specific keys are detected.
  + [String] object: `"atlas"` (Optional as it defaults to `"atlas"` if not specified)
  + [String] atlas: Optional. The name of texture atlas. Defaults to `"minecraft:blocks"`.
  + [String] sprite: The sprite name (for example: `"block/emerald_block"`).

##### Player Object Type


When specifying [String] object as `"player"` it displays the 2D face sprite of a player profile.

* [NBT Compound / JSON Object] The text component.
  + [String] type: Optional. Defaults to `"object"` if object-specific keys are detected.
  + [String] object: `"player"`
  + [String][NBT Compound / JSON Object] player: The textures and/or player profile used to render the face sprite. Provided with the same format as the [`profile`](https://minecraft.wiki/w/Data_component_format#profile "Data component format") data component. If specified as a string, it corresponds to [String] name.

    - A player profile and/or textures object see [Template:Nbt inherit/profile/template](https://minecraft.wiki/w/Template%3ANbt_inherit/profile/template "Template:Nbt inherit/profile/template")
  + [Boolean] hat: Whether to display the hat layer. (Defaults to `true`)

### Component resolution


Text component **resolution** is the process of converting "advanced" (server-side) text components into "simple" (client-side) text components so that they can be displayed to the user.

Certain text component types, such as `text`, `translate`, `keybind`, and `object`, can be directly displayed by a player client, as the client does not need any additional information to interpret them. Those are known as "client-side" or "simple" text components.

Other types, such as `score`, `selector`, and `nbt`, require additional work from the *server* before they can be displayed by the client. Those are known as "server-side" or "advanced" text components. As the client does not have access to the information that these text components are meant to display, they need to be **resolved** by the server, which involves retrieving appropriate data from the world and replacing the server-side text components with client-side ones which the client knows how to render.

If the client receives unresolved server-side text components, `score` and `nbt` text components display as empty text, but `selector` text components display the selector itself.

Additionally, text component resolution fixes a single value in place based on the appropriate data at the moment of resolution. Therefore, these content types are not dynamic, and don't update to reflect later changes. For example, `{score:{name:"@p",objective:"points"}}` may resolve to `"100"`, and will stay that way even if the player's "`points`" score increases or decreases.

Text component resolution can be done in many ways:

* Displaying text in chat or title slots with commands such as `/[tellraw](https://minecraft.wiki/w/Commands/tellraw "Commands/tellraw")` and `/[title](https://minecraft.wiki/w/Commands/title "Commands/title")`.
* Writing a text component to any line on a [sign](https://minecraft.wiki/w/Sign "Sign").
* Writing a text component to a [text display](https://minecraft.wiki/w/Text_display "Text display")'s `text` tag.
* Using the **set\_name** and **set\_lore** [item modifiers](https://minecraft.wiki/w/Item_modifier "Item modifier"), but only if their [String] entity field is set and that entity context exists.
* A text component in a [written book](https://minecraft.wiki/w/Written_book "Written book") will be resolved once first opened by an *operator* or, once placed into a lectern. However, if the resulting text component is too large then it will fail to resolve.
* Setting a [boss bar](https://minecraft.wiki/w/Boss_bar "Boss bar") name using `/[bossbar](https://minecraft.wiki/w/Commands/bossbar "Commands/bossbar") set <id> name` while the command is executing as an entity.
* Setting a [scoreboard objective](https://minecraft.wiki/w/Commands/scoreboard "Commands/scoreboard")'s display name using `/[scoreboard](https://minecraft.wiki/w/Commands/scoreboard "Commands/scoreboard") objectives modify <objective> displayname` while the command is executing as an entity.
* Setting a [score holder](https://minecraft.wiki/w/Commands/scoreboard "Commands/scoreboard")'s display name using `/[scoreboard](https://minecraft.wiki/w/Commands/scoreboard "Commands/scoreboard") players display name` while the command is executing as an entity.
* Setting a score holder or scoreboard objective's [number format](https://minecraft.wiki/w/Commands/scoreboard "Commands/scoreboard") to a `fixed` text component using `/[scoreboard](https://minecraft.wiki/w/Commands/scoreboard "Commands/scoreboard") players display numberformat` or `/[scoreboard](https://minecraft.wiki/w/Commands/scoreboard "Commands/scoreboard") objectives modify <objective> numberformat fixed` while the command is executing as an entity.

There are several places where text components are **not** automatically resolved, such as:

* Writing directly to data components such as [`custom_name`](https://minecraft.wiki/w/Data_component_format#custom_name "Data component format"), [`item_name`](https://minecraft.wiki/w/Data_component_format#item_name "Data component format"), [`lore`](https://minecraft.wiki/w/Data_component_format#lore "Data component format"), and [`written_book_content`](https://minecraft.wiki/w/Data_component_format#written_book_content "Data component format"). The previously mentioned item modifiers can be used to resolve text components when writing to these data components.
* Writing directly to entities' `CustomName` tag.
* All text in [dialogs](https://minecraft.wiki/w/Dialog "Dialog").[[1]](#cite_note-4)
* Most JSON files in data packs, such as [advancement](https://minecraft.wiki/w/Advancement "Advancement") names, chat types, painting variant authors/titles, etc.

### Click events


Click events control what happens when the player clicks on the text. Can be one of the following:

#### open\_url


Opens the specified URL in the user's default web browser.

* [NBT Compound / JSON Object] click\_event
  + [String] action: `open_url`
  + [String] url: The URL to open.

#### open\_file


Opens the specified file on the user's computer. This is used in messages automatically generated by the game (e.g., on taking a screenshot) and cannot be sent by servers for security reasons.

* [NBT Compound / JSON Object] click\_event
  + [String] action: `open_file`
  + [String] path: The file to open.

#### run\_command


Runs the specified command. This runs as if the player typed the specified command in chat and pressed enter. However, this can only be used to run commands that do not send chat messages directly (like `/[say](https://minecraft.wiki/w/Commands/say "Commands/say")`, `/[tell](https://minecraft.wiki/w/Commands/tell "Commands/tell")`, and `/[teammsg](https://minecraft.wiki/w/Commands/teammsg "Commands/teammsg")`). Since they are being run from chat, the player must have the required permissions.

On [signs](https://minecraft.wiki/w/Sign "Sign"), the command is run by the server at the sign's location, with the player who used the sign as the command executor (that is, the entity selected by `@s`). Since they are run by the server, sign commands have the same permission level as a [command block](https://minecraft.wiki/w/Command_block "Command block") instead of using the player's permission level, and are not restricted by chat length limits.

* [NBT Compound / JSON Object] click\_event
  + [String] action: `run_command`
  + [String] command: The command to run. Does not need to be prefixed with a `/` slash.

#### suggest\_command


Opens chat and fills in the specified text or command. If a chat message was already being composed, it is overwritten.This does not work in books.[[2]](#cite_note-5)

* [NBT Compound / JSON Object] click\_event
  + [String] action: `suggest_command`
  + [String] command: The command to fill in chat. Also works with normal texts.

#### change\_page


Can only be used in written books. Changes to the specified page if that page exists.

* [NBT Compound / JSON Object] click\_event
  + [String] action: `change_page`
  + [Int] page: The page to change to.

#### copy\_to\_clipboard


Copies the specified text to the clipboard.

* [NBT Compound / JSON Object] click\_event
  + [String] action: `copy_to_clipboard`
  + [String] value: The text to copy.

#### show\_dialog


Opens the specified [dialog](https://minecraft.wiki/w/Dialog "Dialog").

* [NBT Compound / JSON Object] click\_event
  + [String] action: `show_dialog`
  + [String][NBT Compound / JSON Object] dialog: One [dialog](https://minecraft.wiki/w/Dialog "Dialog") (an [String] [ID](https://minecraft.wiki/w/Resource_location "Resource location"), or a new [NBT Compound / JSON Object] dialog definition) to display.

#### custom


Sends a custom event to the server; has no effect on vanilla servers.

* [NBT Compound / JSON Object] click\_event
  + [String] action: `custom`
  + [String] id: Any [ID](https://minecraft.wiki/w/Resource_location "Resource location") to identify the event.
  + [String] payload: Optional payload of the event.

### Hover events


Hover events control what happens when the player hovers over the text. Can be one of the following:

#### show\_text


Shows a text component.

* [NBT Compound / JSON Object] hover\_event
  + [String] action: `show_text`
  + [String][NBT List / JSON Array][NBT Compound / JSON Object] value: Another text component. Can be any valid text component type: string, list, or object. Note that [NBT Compound / JSON Object] click\_event and [NBT Compound / JSON Object] hover\_event do not function within the tooltip.

#### show\_item


Shows the tooltip of an item as if it was being hovering over it in an inventory.

* [NBT Compound / JSON Object] hover\_event
  + [String] action: `show_item`
  + [String] id: The item's [resource location](https://minecraft.wiki/w/Resource_location "Resource location"). Defaults to `minecraft:air` if invalid.
  + [Int] count: Optional. Size of the item stack. This typically does not change the content tooltip.
  + [NBT Compound / JSON Object] components: Optional. Additional information about the item. See [Data component format](https://minecraft.wiki/w/Data_component_format "Data component format").

#### show\_entity


Shows an entity's name, type, and UUID. Used by [String] selector.

* [NBT Compound / JSON Object] hover\_event
  + [String] action: `show_entity`
  + [NBT Compound / JSON Object] name: Optional. Hidden if not present. A text that is displayed as the name of the entity.
  + [String] id: A string containing the type of the entity, as a [resource location](https://minecraft.wiki/w/Resource_location "Resource location").
  + [String][Int Array][NBT List / JSON Array] uuid: The [UUID](https://minecraft.wiki/w/UUID "UUID") of the entity. Either:
    - A string representing the UUID in the hyphenated hexadecimal format. Must be a valid UUID.
    - A list of four numbers representing the UUID in int-array or list format. e.g. `[I;1,1,1,1]` or `[1,1,1,1]`.

## *Bedrock Edition*


Unlike *Java Edition*, text components in *Bedrock Edition* are written in [JSON](https://minecraft.wiki/w/JSON "JSON").

* [NBT Compound / JSON Object] The root tag.
  + [NBT List / JSON Array] rawtext: A list contains all text object.
    - [NBT Compound / JSON Object] To be valid, an object must contain one ***content*** tag: [String] text, [String] translate, [NBT Compound / JSON Object] score, or [String] selector. Having more than one is allowed, but only one is used.[[note 4]](#cite_note-6)
      * ***Content:* Plain Text**
      * [String] text: A string containing plain text to display directly.
      * ***Content:* Translated Text**
      * [String] translate: A translation identifier, to be displayed as the corresponding text in the player's selected language. If no corresponding translation can be found, the identifier itself is used as the translation text. This identifier is the same as the identifiers found in [lang files](https://minecraft.wiki/w/Resource_pack#Language "Resource pack") from assets or resource packs.
      * [NBT List / JSON Array] with: Optional. A list of text component arguments to be inserted into slots in the translation text. Ignored if [String] translate is not present.
        + Translations can contain slots for text that is not known ahead of time, such as player names. These slots are defined in the translation text itself, not in the text component, and generally take the form `%%1` (displays the first argument; replace `1` with whichever index is desired). If no argument is provided for a slot, the slot is not displayed.
      * ***Content:* Scoreboard Value** *[(requires resolution)](#Component_resolution)*
      * [NBT Compound / JSON Object] score: Displays a score holder's current score in an objective. Displays nothing if the given score holder or the given objective do not exist, or if the score holder is not tracked in the objective.
        + [String] name: The name of the score holder whose score should be displayed. This can be a [selector](https://minecraft.wiki/w/Selector "Selector") like @p or an explicit name. If the text is `"*"`, it shows the reader's own score (for example, `/tellraw @a { "rawtext" : [ { "score" : { "name" : "*" , "objective" : "obj"} } ] }` shows every online player their own score in the "obj" objective).[[note 5]](#cite_note-7)
        + [String] objective: The internal name of the objective to display the player's score in.
      * ***Content:* Entity Names** *[(requires resolution)](#Component_resolution)*
      * [String] selector: A string containing a [selector](https://minecraft.wiki/w/Selector "Selector"). Displayed as the name of the player or entity found by the selector. If more than one player or entity is found by the selector, their names are displayed in either the form "Name1 and Name2" or the form "Name1, Name2, Name3, and Name4". Hovering over a name shows a tooltip with the name, type, and [UUID](https://minecraft.wiki/w/UUID "UUID") of the target. Clicking a player's name suggests a command to whisper to that player. Shift-clicking a player's name inserts that name into chat. Shift-clicking a non-player entity's name inserts its UUID into chat.

Basic raw text example
:   `/[tellraw](https://minecraft.wiki/w/Commands/tellraw "Commands/tellraw") @a { "rawtext" : [ { "text" : "Hello world" } ] }`

This sends a message to all players saying "Hello World" in English only. See the Translate action to see how to send localized texts.

### Appending


Raw text takes in an array of text objects. Each object in the list is added to the previous object. For example, `/[tellraw](https://minecraft.wiki/w/Commands/tellraw "Commands/tellraw") @a { "rawtext" : [ { "text":"Hello" }, { "text" : " World" } ] }`
outputs the same "Hello World" as the first example. Appending text can be useful to combine 2 different localized texts, or apply different colors to each word etc.

### Breaking lines


You can go down a line by using "\n". For example,

`/[tellraw](https://minecraft.wiki/w/Commands/tellraw "Commands/tellraw") @a { "rawtext" : [ { "text" : "Hello\nNext line" } ] }`

### Translate


The translate object allows creators to provide localized text to users. If translate is specified along with text, translate overrides the text object. The string to provide to translate is the name of the string in the language files. For example, in Vanilla Minecraft "commands.op.success" is the string that displays when /op is used on a player successfully.

`/[tellraw](https://minecraft.wiki/w/Commands/tellraw "Commands/tellraw") @a { "rawtext": [ { "translate" : "commands.op.success" } ] }`

This outputs "Opped %s" to all players. Note that because of text being ignored with translate specified, the following example outputs the same text:

`/[tellraw](https://minecraft.wiki/w/Commands/tellraw "Commands/tellraw") @a { "rawtext" : [ { "text":"Hello World", "translate":"commands.op.success" } ] }`

### With


In the translate example above, it outputs "Opped %s". To have a name or other text show up instead of %s, "with" needs to be specified as well. Note that "with" only works with "translate" and also requires an array `[]` instead of curly brackets `{}` .

`/[tellraw](https://minecraft.wiki/w/Commands/tellraw "Commands/tellraw") @a { "rawtext": [ { "translate" : "commands.op.success", "with": [ "Steve" ] } ] }`

If you want to use a translated text inside the "with" component, instead of an array it needs to be another rawtext component (which consists of an array of text components). The following example outputs "Opped Apple".

`/[tellraw](https://minecraft.wiki/w/Commands/tellraw "Commands/tellraw") @a { "rawtext": [ { "translate" : "commands.op.success", "with": { "rawtext": [ { "translate" : "item.apple.name" } ] } } ] }`

### %%s


"translate" and "%s" can be used without needing a corresponding string in the localization files. For example:

`/[tellraw](https://minecraft.wiki/w/Commands/tellraw "Commands/tellraw") @a { "rawtext": [ { "translate" : "Hello %%s", "with": [ "Steve" ] } ] }`

This outputs "Hello Steve" to all players.

### Multiple %s


%%s can be used multiple times. They are filled in, in the order specified

`/[tellraw](https://minecraft.wiki/w/Commands/tellraw "Commands/tellraw") @a { "rawtext": [ { "translate" : "Hello %%s and %%s", "with": [ "Steve", "Alex" ] } ] }`

Outputs: "Hello Steve and Alex"

You can again use a rawtext component to replace the plain string array, like so

`/[tellraw](https://minecraft.wiki/w/Commands/tellraw "Commands/tellraw") @a { "rawtext": [ { "translate" : "Hello %%s and %%s", "with": { "rawtext" : [ { "text" : "Steve" }, { "translate" : "item.apple.name" } ] } } ] }`

Outputs: "Hello Steve and Apple"

### Ordering with %%#


The order to fill in %%s can be changed by instead specifying it with %%#, replacing # with an actual number. For example, to swap the position of Steve and Alex in the above example, instead run the following:

`/[tellraw](https://minecraft.wiki/w/Commands/tellraw "Commands/tellraw") @a { "rawtext" : [ {"translate" : "Hello %%2 and %%1", "with": [ "Steve", "Alex"] } ] }`

Outputs: "Hello Alex and Steve"

### Formatting


String formatting is still possible, but not using the text component format used in Java Edition. Instead, [formatting codes](https://minecraft.wiki/w/Formatting_codes "Formatting codes") are used to change text color and style.

## History


### *Java Edition*


| [*Java Edition*](https://minecraft.wiki/w/Java_Edition_version_history "Java Edition version history") | | | | | | | |
| --- | --- | --- | --- | --- | --- | --- | --- |
| [1.7.2](https://minecraft.wiki/w/Java_Edition_1.7.2 "Java Edition 1.7.2") | | | [13w37a](https://minecraft.wiki/w/Java_Edition_13w37a "Java Edition 13w37a") | | | | Added `/[tellraw](https://minecraft.wiki/w/Commands/tellraw "Commands/tellraw")`, which supports raw JSON text. |
| [1.8](https://minecraft.wiki/w/Java_Edition_1.8 "Java Edition 1.8") | | | [14w02a](https://minecraft.wiki/w/Java_Edition_14w02a "Java Edition 14w02a") | | | | Added text component `insertion`. |
| [14w07a](https://minecraft.wiki/w/Java_Edition_14w07a "Java Edition 14w07a") | | | | Added text component `score`. |
| [14w20a](https://minecraft.wiki/w/Java_Edition_14w20a "Java Edition 14w20a") | | | | Added `/[title](https://minecraft.wiki/w/Commands/title "Commands/title")`, which supports raw JSON text. |
| Added text component `selector`. |
| [14w25a](https://minecraft.wiki/w/Java_Edition_14w25a "Java Edition 14w25a") | | | | Now supported by [signs](https://minecraft.wiki/w/Sign "Sign") and [written books](https://minecraft.wiki/w/Written_book "Written book"). |
| [1.12](https://minecraft.wiki/w/Java_Edition_1.12 "Java Edition 1.12") | | | [17w16a](https://minecraft.wiki/w/Java_Edition_17w16a "Java Edition 17w16a") | | | | Added text component `keybind`. |
| [1.13](https://minecraft.wiki/w/Java_Edition_1.13 "Java Edition 1.13") | | | [18w01a](https://minecraft.wiki/w/Java_Edition_18w01a "Java Edition 18w01a") | | | | Now supported by custom entity names. |
| [18w05a](https://minecraft.wiki/w/Java_Edition_18w05a "Java Edition 18w05a") | | | | Added `/[bossbar](https://minecraft.wiki/w/Commands/bossbar "Commands/bossbar")`. The argument `<name>` supports raw JSON text. |
| [pre8](https://minecraft.wiki/w/Java_Edition_1.13-pre8 "Java Edition 1.13-pre8") | | | | Now supported by [scoreboard](https://minecraft.wiki/w/Scoreboard "Scoreboard") objective names and team names. |
| [1.14](https://minecraft.wiki/w/Java_Edition_1.14 "Java Edition 1.14") | | | [18w43a](https://minecraft.wiki/w/Java_Edition_18w43a "Java Edition 18w43a") | | | | Added text component `nbt` with `block` and `entity`. |
| Now supported by the [item tag](https://minecraft.wiki/w/Player_format#Item_structure "Player format") `Lore`. |
| [18w44a](https://minecraft.wiki/w/Java_Edition_18w44a "Java Edition 18w44a") | | | | Added text component `interpret`. |
| [1.15](https://minecraft.wiki/w/Java_Edition_1.15 "Java Edition 1.15") | | | [19w39a](https://minecraft.wiki/w/Java_Edition_19w39a "Java Edition 19w39a") | | | | Added `storage` for the `nbt` text component. |
| [19w41a](https://minecraft.wiki/w/Java_Edition_19w41a "Java Edition 19w41a") | | | | Added the action `copy_to_clipboard` for the text component `clickEvent`. |
| [1.16](https://minecraft.wiki/w/Java_Edition_1.16 "Java Edition 1.16") | | | [20w17a](https://minecraft.wiki/w/Java_Edition_20w17a "Java Edition 20w17a") | | | | Added text component `font`. |
| Added argument `contents` for `hoverEvent`, replacing `value`, which is now deprecated but still supported. |
| The `color` component can now contain a hexadecimal RGB value prefixed by `#` (Example: `"color":"#ff0088"`). |
| [1.19.4](https://minecraft.wiki/w/Java_Edition_1.19.4 "Java Edition 1.19.4") | | | [23w03a](https://minecraft.wiki/w/Java_Edition_23w03a "Java Edition 23w03a") | | | | Added text component `fallback`. |
| [1.20.3](https://minecraft.wiki/w/Java_Edition_1.20.3 "Java Edition 1.20.3") | | | [23w40a](https://minecraft.wiki/w/Java_Edition_23w40a "Java Edition 23w40a") | | | | Added text component `type`. |
| `contents.id` field in `show_entity` can represent the UUID as an array of ints. |
| Numbers and booleans are no longer auto-converted to strings, and so are invalid for the `text` component. |
| Several errors that used to be ignored are now hard errors. |
| [23w42a](https://minecraft.wiki/w/Java_Edition_23w42a "Java Edition 23w42a") | | | | Changes to chat component serialization: components of type `nbt` now have `source` field with allowed values: `entity`, `block`, and `storage`. |
| [1.21.2](https://minecraft.wiki/w/Java_Edition_1.21.2 "Java Edition 1.21.2") | | | [24w33a](https://minecraft.wiki/w/Java_Edition_24w33a "Java Edition 24w33a") | | | | Invalid `selector` patterns in chat components will now cause commands to fail to parse, instead of resolving to an empty string. |
| [1.21.4](https://minecraft.wiki/w/Java_Edition_1.21.4 "Java Edition 1.21.4") | | | [24w44a](https://minecraft.wiki/w/Java_Edition_24w44a "Java Edition 24w44a") | | | | Added optional `shadow_color` style field to Text Components, which overrides the shadow properties of text. |
| [1.21.5](https://minecraft.wiki/w/Java_Edition_1.21.5 "Java Edition 1.21.5") | | | [25w02a](https://minecraft.wiki/w/Java_Edition_25w02a "Java Edition 25w02a") | | | | Text components are now stored as NBT and are passed into commands using SNBT. |
| The `hoverEvent` field has been renamed to `hover_event`.  * The legacy `value` field (which was parsed from a rendered text component) is no longer supported. * For the `show_text` action:   + `contents` field has been renamed to `text`. * For the `show_item` action:   + The `contents` field has been inlined.   + If contents was specified only as an item id, it is replaced with the full format and inlined. * For the `show_entity` action:   + The `contents` field has been inlined.   + The `id` field has been renamed to `uuid`.   + The `type` field has been renamed to `id`. |
| The `clickEvent` field has been renamed to `click_event`.  * For the `open_url` action:   + The `value` field has been renamed to `url`.   + The click event will no longer parse if not a valid URI with either `https://` or `http://` schemes, instead of simply not working. * For the `open_file` action:   + The `value` field has been renamed to `path`. * For the `run_command` action:   + The `value` field has been renamed to `command`.   + The click event will no longer parse if the command contains disallowed characters, instead of simply not working.   + It is no longer required that the specified command field has a `/` prefix. * For the `suggest_command` action:   + The `value` field has been renamed to `command`.   + The click event will no longer parse if the command contains disallowed characters, instead of simply not working. * For the `change_page` action:   + The `value` field has been renamed to `page`.   + The page value now requires a positive integer instead of a string. |
| [25w03a](https://minecraft.wiki/w/Java_Edition_25w03a "Java Edition 25w03a") | | | | The `text` field in `show_text` action has been renamed to `value`. |
| [1.21.6](https://minecraft.wiki/w/Java_Edition_1.21.6 "Java Edition 1.21.6") | | | [25w20a](https://minecraft.wiki/w/Java_Edition_25w20a "Java Edition 25w20a") | | | | Click Events: New click action `minecraft:custom` has been added. |
| Dialog Click Event: New action `show_dialog` has been added. |
| [1.21.9](https://minecraft.wiki/w/Java_Edition_1.21.9 "Java Edition 1.21.9") | | | [25w32a](https://minecraft.wiki/w/Java_Edition_25w32a "Java Edition 25w32a") | | | | Added new text component with type `object`. |
| [25w34a](https://minecraft.wiki/w/Java_Edition_25w34a "Java Edition 25w34a") | | | | Bold and italics styles are ignored when drawing sprites. |
| [25w35a](https://minecraft.wiki/w/Java_Edition_25w35a "Java Edition 25w35a") | | | | Object text component has been updated to support displaying other non-character objects as a part of text. |
| [26.1](https://minecraft.wiki/w/Java_Edition_26.1 "Java Edition 26.1") | | | [snap8](https://minecraft.wiki/w/Java_Edition_26.1_Snapshot_8 "Java Edition 26.1 Snapshot 8") | | | | `minecraft:nbt`: Tags resolved with the `minecraft:nbt` text component when the `interpret` field is set to `false` are now pretty-printed instead of being flattened into a single `text` component. Contents of the `nbt` and `block` fields are no longer silently rejected when parsing fails. The field `entity` no longer accepts trailing data after a selector. A new option called `plain` has been added to remove styling from pretty-printed text. |
| `minecraft:selector`: The field `selector` no longer accepts trailing data after a selector. |
| [pre1](https://minecraft.wiki/w/Java_Edition_26.1-pre1 "Java Edition 26.1-pre1") | | | | `minecraft:object`: Added a new optional field named `fallback`. |
| [pre2](https://minecraft.wiki/w/Java_Edition_26.1-pre2 "Java Edition 26.1-pre2") | | | | Components in server status messages (MotD) nested more than 16 times will now be discarded and replaced with an ellipsis. |

### *Bedrock Edition*


| [*Bedrock Edition*](https://minecraft.wiki/w/Bedrock_Edition_version_history "Bedrock Edition version history") | | | | | | | |
| --- | --- | --- | --- | --- | --- | --- | --- |
| [1.9.0](https://minecraft.wiki/w/Bedrock_Edition_1.9.0 "Bedrock Edition 1.9.0") | | | [beta 1.9.0.0](https://minecraft.wiki/w/Bedrock_Edition_beta_1.9.0.0 "Bedrock Edition beta 1.9.0.0") | | | | Added `/[tellraw](https://minecraft.wiki/w/Commands/tellraw "Commands/tellraw")`, the raw JSON text used to support this command. |
| [1.16.100](https://minecraft.wiki/w/Bedrock_Edition_1.16.100 "Bedrock Edition 1.16.100") | | | [beta 1.16.100.55](https://minecraft.wiki/w/Bedrock_Edition_beta_1.16.100.55 "Bedrock Edition beta 1.16.100.55") | | | | Added text component `score` and `selector`. |

## See also


* [Commands](https://minecraft.wiki/w/Commands "Commands")
* [Formatting code](https://minecraft.wiki/w/Formatting_code "Formatting code")

## Notes


1. [↑](#cite_ref-1) Selecting the "next" argument ignores slots that specify an index explicitly. So if the translation text "Hello %s, %2$s, and %s." was given the components "John" and "Becky", it would display "Hello John, Becky, and Becky."
2. [↑](#cite_ref-2) Showing the reader's own score only works in situations where a message has one singular reader. That is chat messages, [`/title`s](https://minecraft.wiki/w/Commands/title "Commands/title"), and [written books](https://minecraft.wiki/w/Written_book "Written book"). It does not work for [bossbar](https://minecraft.wiki/w/Bossbar "Bossbar") display names or blocks like signs.
3. [↑](#cite_ref-3) If [String] source is left unspecified, NBT sources are checked in the order [String] entity, [String] block, [String] storage. If multiple are present, whichever one comes first in that list is used.
4. [↑](#cite_ref-6) Content tags are checked in the order [String] translate, [String] text, [String] selector, [NBT Compound / JSON Object] score. If multiple are present, whichever one comes first in that list is used.
5. [↑](#cite_ref-7) Showing the reader's own score only works in situations where a message has one singular reader. That is chat messages, [`/titleraw`s](https://minecraft.wiki/w/Commands/titleraw "Commands/titleraw"), and [written books](https://minecraft.wiki/w/Written_book "Written book").[*[verify](https://minecraft.wiki/w/Special%3ATalkPage/Text_component_format "Special:TalkPage/Text component format")*] It doesn't work for things like signs that can have more than one "reader".[*[verify](https://minecraft.wiki/w/Special%3ATalkPage/Text_component_format "Special:TalkPage/Text component format")*]

## References


1. [↑](#cite_ref-4) [MC-297871](https://bugs.mojang.com/browse/MC-297871 "mojira:MC-297871") – resolved as "Invalid".
2. [↑](#cite_ref-5) [MC-70317](https://bugs.mojang.com/browse/MC-70317 "mojira:MC-70317") – resolved as "Works as Intended".

## External links


* [Visual text component generator on text.datapackhub.net](https://text.datapackhub.net/)
* [Node-based text component generator on misode.github.io](https://misode.github.io/text-component/)

## Navigation


| * [v](https://minecraft.wiki/w/Template%3ANavbox_Java_Edition_technical "Template:Navbox Java Edition technical") * [t](https://minecraft.wiki/w/Special%3ATalkPage/Template%3ANavbox_Java_Edition_technical "Special:TalkPage/Template:Navbox Java Edition technical") * [e](https://minecraft.wiki/w/Special%3AEditPage/Template%3ANavbox_Java_Edition_technical "Special:EditPage/Template:Navbox Java Edition technical") *[Java Edition](https://minecraft.wiki/w/Java_Edition "Java Edition")* technical | |
| --- | --- |
| | General | | | --- | --- | | Concepts | * [![](/images/BlockSprite_chest.png?15d81)](https://minecraft.wiki/w/Block_entity "Block entity")[Block entity](https://minecraft.wiki/w/Block_entity "Block entity") * [![](/images/EnvSprite_map.png?b863e)](https://minecraft.wiki/w/Coordinates "Coordinates")[Coordinates](https://minecraft.wiki/w/Coordinates "Coordinates") * [![](/images/EffectSprite_infested.png?4562a)](https://minecraft.wiki/w/Crash "Crash")[Crashes](https://minecraft.wiki/w/Crash "Crash") * [String] [Loot context](https://minecraft.wiki/w/Loot_context "Loot context") * [![](/images/EntitySprite_cow.png?893cf)](https://minecraft.wiki/w/Mob_AI "Mob AI")[Mob AI](https://minecraft.wiki/w/Mob_AI "Mob AI") * [![](/images/BlockSprite_lodestone.png?00f1a)](https://minecraft.wiki/w/Point_of_Interest "Point of Interest")[Point of Interest](https://minecraft.wiki/w/Point_of_Interest "Point of Interest") * ![File directory.png: Sprite image for directory in Minecraft](/images/thumb/File_directory.png/16px-File_directory.png?8a409) [Identifier](https://minecraft.wiki/w/Identifier "Identifier") * [![](/images/BlockSprite_camera.png?7ee99)](https://minecraft.wiki/w/Screenshot "Screenshot")[Screenshot](https://minecraft.wiki/w/Screenshot "Screenshot") * [![](/images/EnvSprite_scoreboard.png?38feb)](https://minecraft.wiki/w/Statistics "Statistics")[Statistics](https://minecraft.wiki/w/Statistics "Statistics") * [![](/images/ItemSprite_book.png?791a5)](https://minecraft.wiki/w/Telemetry "Telemetry")[Telemetry](https://minecraft.wiki/w/Telemetry "Telemetry") * [![](/images/ItemSprite_clock.png?30324)](https://minecraft.wiki/w/Tick "Tick")[Tick](https://minecraft.wiki/w/Tick "Tick") * [![](/images/ItemSprite_wheat-seeds.png?b83e5)](https://minecraft.wiki/w/Random_Tick "Random Tick")[Random Tick](https://minecraft.wiki/w/Random_Tick "Random Tick") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/UUID "UUID")[UUID](https://minecraft.wiki/w/UUID "UUID") * [![](/images/BlockSprite_computer.png?e0c37)](https://minecraft.wiki/w/JSON "JSON")[JSON](https://minecraft.wiki/w/JSON "JSON") | | [General format](https://minecraft.wiki/w/Development_resources "Development resources") | * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Java_Edition_data_values "Java Edition data values")[Data values](https://minecraft.wiki/w/Java_Edition_data_values "Java Edition data values")   + [![](/images/LegacyBlockSprite_bricks-je1.png?9a58b)](https://minecraft.wiki/w/Java_Edition_Classic_data_values "Java Edition Classic data values")[Classic](https://minecraft.wiki/w/Java_Edition_Classic_data_values "Java Edition Classic data values")     - [Remake](https://minecraft.wiki/w/Classic_remake_data_values "Classic remake data values")   + [![](/images/EntitySprite_rana.png?3f2f9)](https://minecraft.wiki/w/Java_Edition_Indev_data_values "Java Edition Indev data values")[Indev](https://minecraft.wiki/w/Java_Edition_Indev_data_values "Java Edition Indev data values")   + [![](/images/BlockSprite_stone.png?e9a91)](https://minecraft.wiki/w/Java_Edition_pre-flattening_data_values "Java Edition pre-flattening data values")[Pre-flattening](https://minecraft.wiki/w/Java_Edition_pre-flattening_data_values "Java Edition pre-flattening data values") * [![](/images/EnvSprite_item.png?89d23)](https://minecraft.wiki/w/Data_component_format "Data component format")[Data component format](https://minecraft.wiki/w/Data_component_format "Data component format")   + [![](/images/BlockSprite_test-block-start.png?35191)](https://minecraft.wiki/w/Data_component_predicate "Data component predicate")[Predicate](https://minecraft.wiki/w/Data_component_predicate "Data component predicate") * [![](/images/EnvSprite_entities.png?94711)](https://minecraft.wiki/w/Entity_format "Entity format")[Entity format](https://minecraft.wiki/w/Entity_format "Entity format") * [![](/images/BlockSprite_chest.png?15d81)](https://minecraft.wiki/w/Block_entity_format "Block entity format")[Block entity format](https://minecraft.wiki/w/Block_entity_format "Block entity format") * [![](/images/ItemSprite_map.png?05f8c)](https://minecraft.wiki/w/Map_item_format "Map item format")[Map item format](https://minecraft.wiki/w/Map_item_format "Map item format") * [NBT Compound / JSON Object] [NBT format](https://minecraft.wiki/w/NBT_format "NBT format") * [![](/images/EffectSprite_particle-healing.png?1357a)](https://minecraft.wiki/w/Particle_format "Particle format")[Particle format](https://minecraft.wiki/w/Particle_format "Particle format") * [![](/images/ItemSprite_book-and-quill.png?f190b)](https://minecraft.wiki/w/Text_component_format "Text component format")Text component format * [§](https://minecraft.wiki/w/Formatting_codes "Formatting codes") [Formatting codes](https://minecraft.wiki/w/Formatting_codes "Formatting codes") * [![](/images/thumb/Movement_hint.png/16px-Movement_hint.png?92667)](https://minecraft.wiki/w/Key_codes "Key codes")[Key codes](https://minecraft.wiki/w/Key_codes "Key codes") * [![](/images/thumb/Dice.png/14px-Dice.png?a4e84)](https://minecraft.wiki/w/Random_sequence_format "Random sequence format")[Random sequence](https://minecraft.wiki/w/Random_sequence_format "Random sequence format") * [![](/images/BlockSprite_structure-block.png?381fc)](https://minecraft.wiki/w/Structure_file "Structure file")[Structure file format](https://minecraft.wiki/w/Structure_file "Structure file")   + [![](/images/EnvSprite_chunk.png?b2cf1)](https://minecraft.wiki/w/Schematic_file_format "Schematic file format")[Schematic file format](https://minecraft.wiki/w/Schematic_file_format "Schematic file format") | | [World](https://minecraft.wiki/w/World "World") | * [![](/images/EnvSprite_altitude.png?9b274)](https://minecraft.wiki/w/Heightmap "Heightmap")[Heightmap](https://minecraft.wiki/w/Heightmap "Heightmap") * [![](/images/EnvSprite_mountain.png?2e0ae)](https://minecraft.wiki/w/World_seed "World seed")[Seed](https://minecraft.wiki/w/World_seed "World seed")   + [Anomalous](https://minecraft.wiki/w/Anomalous_world_seeds "Anomalous world seeds") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Data_version "Data version")[Data version](https://minecraft.wiki/w/Data_version "Data version")  |  |  | | --- | --- | | Legacy | * [![](/images/EnvSprite_chunk.png?b2cf1)](https://minecraft.wiki/w/Spawn_chunk "Spawn chunk")[Spawn chunk](https://minecraft.wiki/w/Spawn_chunk "Spawn chunk") | | [Level format](https://minecraft.wiki/w/Java_Edition_level_format "Java Edition level format") | * [![](/images/BlockSprite_anvil.png?a26c9)](https://minecraft.wiki/w/Anvil_file_format "Anvil file format")[Anvil file format](https://minecraft.wiki/w/Anvil_file_format "Anvil file format") * [![](/images/EnvSprite_chunk.png?b2cf1)](https://minecraft.wiki/w/Chunk_format "Chunk format")[Chunk format](https://minecraft.wiki/w/Chunk_format "Chunk format") * [![](/images/EntitySprite_steve.png?856f8)](https://minecraft.wiki/w/Player.dat_format "Player.dat format")[Player format](https://minecraft.wiki/w/Player.dat_format "Player.dat format") * [![](/images/BlockSprite_lodestone.png?00f1a)](https://minecraft.wiki/w/Point_of_Interest_format "Point of Interest format")[Point of Interest format](https://minecraft.wiki/w/Point_of_Interest_format "Point of Interest format") * [![](/images/EntitySprite_ravager.png?40196)](https://minecraft.wiki/w/Raids.dat_format "Raids.dat format")[raids.dat format](https://minecraft.wiki/w/Raids.dat_format "Raids.dat format") * [![](/images/BlockSprite_chain-command-block.png?0afa8)](https://minecraft.wiki/w/Command_storage_format "Command storage format")[Command storage format](https://minecraft.wiki/w/Command_storage_format "Command storage format") * [![](/images/EnvSprite_scoreboard.png?38feb)](https://minecraft.wiki/w/Scoreboard#NBT_format "Scoreboard")[Scoreboard format](https://minecraft.wiki/w/Scoreboard#NBT_format "Scoreboard")  |  |  | | --- | --- | | Legacy | * [![](/images/LegacyBlockSprite_bricks-je1.png?9a58b)](https://minecraft.wiki/w/Java_Edition_Classic_level_format "Java Edition Classic level format")[Classic level format](https://minecraft.wiki/w/Java_Edition_Classic_level_format "Java Edition Classic level format") * [Classic server protocol](https://minecraft.wiki/w/Classic_server_protocol "Classic server protocol") * [![](/images/EntitySprite_rana.png?3f2f9)](https://minecraft.wiki/w/Java_Edition_Indev_level_format "Java Edition Indev level format")[Indev level format](https://minecraft.wiki/w/Java_Edition_Indev_level_format "Java Edition Indev level format") * [![](/images/EnvSprite_nether-portal.png?47646)](https://minecraft.wiki/w/Java_Edition_Alpha_level_format "Java Edition Alpha level format")[Alpha level format](https://minecraft.wiki/w/Java_Edition_Alpha_level_format "Java Edition Alpha level format")   + [![](/images/LegacyItemSprite_oak-door-revision-1.png?b7426)](https://minecraft.wiki/w/Zone_file_format "Zone file format")[Zone file format](https://minecraft.wiki/w/Zone_file_format "Zone file format") * [![](/images/ItemSprite_locked-map.png?c4112)](https://minecraft.wiki/w/Region_file_format "Region file format")[Region file format](https://minecraft.wiki/w/Region_file_format "Region file format") * [![](/images/Servers.png?b1dc2)](https://minecraft.wiki/w/Server_level.dat "Server level.dat")[server\_level.dat format](https://minecraft.wiki/w/Server_level.dat "Server level.dat") * [![](/images/EnvSprite_new-village.png?3e8a5)](https://minecraft.wiki/w/Villages.dat_format "Villages.dat format")[villages.dat format](https://minecraft.wiki/w/Villages.dat_format "Villages.dat format") * [![](/images/EnvSprite_abandoned-mineshaft.png?fab65)](https://minecraft.wiki/w/Generated_structures_data_file_format "Generated structures data file format")[Generated structures format](https://minecraft.wiki/w/Generated_structures_data_file_format "Generated structures data file format") | | | | [.minecraft](https://minecraft.wiki/w/.minecraft ".minecraft") | * ![File archive.png: Sprite image for archive in Minecraft](/images/thumb/File_archive.png/16px-File_archive.png?5ba7d) [client.jar](https://minecraft.wiki/w/Client.jar "Client.jar")   + [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Version.json "Version.json")[version.json](https://minecraft.wiki/w/Version.json "Version.json") * [![](/images/ItemSprite_book-and-quill.png?f190b)](https://minecraft.wiki/w/Client.json "Client.json")[client.json](https://minecraft.wiki/w/Client.json "Client.json") * [![](/images/BlockSprite_command-block.png?e7078)](https://minecraft.wiki/w/Command_history.txt "Command history.txt")[command\_history.txt](https://minecraft.wiki/w/Command_history.txt "Command history.txt") * [![](/images/BlockSprite_chest.png?15d81)](https://minecraft.wiki/w/Launcher_profiles.json "Launcher profiles.json")[launcher\_profiles.json](https://minecraft.wiki/w/Launcher_profiles.json "Launcher profiles.json") * [![](/images/Chat_settings_gear.png?6a179)](https://minecraft.wiki/w/Options.txt "Options.txt")[options.txt](https://minecraft.wiki/w/Options.txt "Options.txt") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Version_manifest.json "Version manifest.json")[version\_manifest.json](https://minecraft.wiki/w/Version_manifest.json "Version manifest.json") * [![](/images/ItemSprite_paper.png?565a1)](https://minecraft.wiki/w/Hotbar.nbt_format "Hotbar.nbt format")[hotbar.nbt format](https://minecraft.wiki/w/Hotbar.nbt_format "Hotbar.nbt format") * [![](/images/Servers.png?b1dc2)](https://minecraft.wiki/w/Servers.dat_format "Servers.dat format")[Server list format](https://minecraft.wiki/w/Servers.dat_format "Servers.dat format") | | Tools | * `F3` [Debug screen](https://minecraft.wiki/w/Debug_screen "Debug screen")   + [hotkey](https://minecraft.wiki/w/Debug_hotkey "Debug hotkey")   + [renderer](https://minecraft.wiki/w/Debug_renderer "Debug renderer") * [![](/images/Mojang_logo.svg?0b294)](https://minecraft.wiki/w/Java_developer_tools "Java developer tools")[Developer Tools](https://minecraft.wiki/w/Java_developer_tools "Java developer tools")   + [![](/images/BlockSprite_test-instance-block.png?27a39)](https://minecraft.wiki/w/GameTest "GameTest")[GameTest](https://minecraft.wiki/w/GameTest "GameTest")   + [DataFixerUpper](https://minecraft.wiki/w/DataFixerUpper "DataFixerUpper")   + [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Debug_property "Debug property")[Debug properties](https://minecraft.wiki/w/Debug_property "Debug property")  |  |  | | --- | --- | | Legacy | * [![](/images/BlockSprite_computer.png?e0c37)](https://minecraft.wiki/w/Obfuscation_map "Obfuscation map")[Obfuscation map](https://minecraft.wiki/w/Obfuscation_map "Obfuscation map") | | | Sound | * [![](/images/BlockSprite_jukebox-side.png?8477e)](https://minecraft.wiki/w/Block_sound_type "Block sound type")[Block sound type](https://minecraft.wiki/w/Block_sound_type "Block sound type") * [![](/images/EnvSprite_chat.png?0dd92)](https://minecraft.wiki/w/Closed_captions "Closed captions")[Closed captions](https://minecraft.wiki/w/Closed_captions "Closed captions") * [![](/images/EnvSprite_ambience.png?d7c92)](https://minecraft.wiki/w/Sounds.json "Sounds.json")[sounds.json](https://minecraft.wiki/w/Sounds.json "Sounds.json") | | [Commands](https://minecraft.wiki/w/Commands "Commands") | * [Brigadier](https://minecraft.wiki/w/Brigadier "Brigadier") * [![](/images/BlockSprite_repeating-command-block.png?1dad0)](https://minecraft.wiki/w/Function_%28Java_Edition%29 "Function (Java Edition)")[Functions](https://minecraft.wiki/w/Function_%28Java_Edition%29 "Function (Java Edition)")   **[All commands](https://minecraft.wiki/w/Template%3ANavbox_commands "Template:Navbox commands")** | | [Launching](https://minecraft.wiki/w/Minecraft_Launcher "Minecraft Launcher") | * [Mojang API](https://minecraft.wiki/w/Mojang_API "Mojang API") * [![](/images/Microsoft_logo.svg?7e87a)](https://minecraft.wiki/w/Microsoft_authentication "Microsoft authentication")[Microsoft authentication](https://minecraft.wiki/w/Microsoft_authentication "Microsoft authentication") * [![](/images/thumb/Java_Edition_icon_3.png/16px-Java_Edition_icon_3.png?f7112)](https://minecraft.wiki/w/Quick_Play "Quick Play")[Quick Play](https://minecraft.wiki/w/Quick_Play "Quick Play")  |  |  | | --- | --- | | Legacy | * [Legacy Minecraft authentication](https://minecraft.wiki/w/Legacy_Minecraft_authentication "Legacy Minecraft authentication") * [Yggdrasil](https://minecraft.wiki/w/Yggdrasil "Yggdrasil") | | | [Protocol](https://minecraft.wiki/w/Java_Edition_protocol "Java Edition protocol") | * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Protocol_version "Protocol version")[Protocol version](https://minecraft.wiki/w/Protocol_version "Protocol version") * [![](/images/ItemSprite_bundle.png?9eb9f)](https://minecraft.wiki/w/Java_Edition_protocol/Packets "Java Edition protocol/Packets")[Packets](https://minecraft.wiki/w/Java_Edition_protocol/Packets "Java Edition protocol/Packets") * [Data types](https://minecraft.wiki/w/Java_Edition_protocol/Data_types "Java Edition protocol/Data types") * [![](/images/BlockSprite_computer.png?e0c37)](https://minecraft.wiki/w/Java_Edition_protocol/Encryption "Java Edition protocol/Encryption")[Encryption](https://minecraft.wiki/w/Java_Edition_protocol/Encryption "Java Edition protocol/Encryption") | | [Server](https://minecraft.wiki/w/Server "Server") | * ![File archive.png: Sprite image for archive in Minecraft](/images/thumb/File_archive.png/16px-File_archive.png?5ba7d) [server.jar](https://minecraft.wiki/w/Server.jar "Server.jar") * [![](/images/BlockSprite_test-instance-block.png?27a39)](https://minecraft.wiki/w/Server.properties "Server.properties")[server.properties](https://minecraft.wiki/w/Server.properties "Server.properties") * [![](/images/BlockSprite_test-instance-block.png?27a39)](https://minecraft.wiki/w/Server/Requirements "Server/Requirements")[Server requirements](https://minecraft.wiki/w/Server/Requirements "Server/Requirements") * [![](/images/BlockSprite_test-block-accept.png?08355)](https://minecraft.wiki/w/Whitelist "Whitelist")[Whitelist](https://minecraft.wiki/w/Whitelist "Whitelist") * [Operator list](https://minecraft.wiki/w/Server#Operator_list "Server")  |  |  | | --- | --- | | Protocols | * [Query](https://minecraft.wiki/w/Query "Query") * [RCON](https://minecraft.wiki/w/RCON "RCON") * [Server Management Protocol](https://minecraft.wiki/w/Minecraft_Server_Management_Protocol "Minecraft Server Management Protocol") | | | Legacy | * [al\_version](https://minecraft.wiki/w/Al_version "Al version") * [![](/images/EnvSprite_item.png?89d23)](https://minecraft.wiki/w/Item_format "Item format")[Item format](https://minecraft.wiki/w/Item_format "Item format") | | |
| | [Data pack](https://minecraft.wiki/w/Data_pack "Data pack") | | | --- | --- | | Components | * [pack.mcmeta](https://minecraft.wiki/w/Pack.mcmeta "Pack.mcmeta") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Pack_format "Pack format")[Pack format](https://minecraft.wiki/w/Pack_format "Pack format") * [![](/images/ItemSprite_map.png?05f8c)](https://minecraft.wiki/w/Advancement_definition "Advancement definition")[Advancements](https://minecraft.wiki/w/Advancement_definition "Advancement definition") * [![](/images/BlockSprite_repeating-command-block.png?1dad0)](https://minecraft.wiki/w/Function_%28Java_Edition%29 "Function (Java Edition)")[Functions](https://minecraft.wiki/w/Function_%28Java_Edition%29 "Function (Java Edition)") * [![](/images/BlockSprite_red-banner.png?8b4d0)](https://minecraft.wiki/w/Item_modifier "Item modifier")[Item modifier](https://minecraft.wiki/w/Item_modifier "Item modifier") * [![](/images/ItemSprite_diamond.png?8f019)](https://minecraft.wiki/w/Loot_table "Loot table")[Loot tables](https://minecraft.wiki/w/Loot_table "Loot table") * [![](/images/BlockSprite_test-block-start.png?35191)](https://minecraft.wiki/w/Predicate "Predicate")[Predicate](https://minecraft.wiki/w/Predicate "Predicate") * [![](/images/BlockSprite_crafting-table.png?6e126)](https://minecraft.wiki/w/Recipe_%28Java_Edition%29 "Recipe (Java Edition)")[Recipe](https://minecraft.wiki/w/Recipe_%28Java_Edition%29 "Recipe (Java Edition)") * [![](/images/EffectSprite_strength.png?05e79)](https://minecraft.wiki/w/Damage_type "Damage type")[Damage type](https://minecraft.wiki/w/Damage_type "Damage type") * [![](/images/EnvSprite_chat.png?0dd92)](https://minecraft.wiki/w/Chat_type "Chat type")[Chat type](https://minecraft.wiki/w/Chat_type "Chat type") * [![](/images/ItemSprite_enchanted-book.png?b7877)](https://minecraft.wiki/w/Enchantment_definition "Enchantment definition")[Enchantment](https://minecraft.wiki/w/Enchantment_definition "Enchantment definition") * [![](/images/BlockSprite_enchanting-table.png?45e2c)](https://minecraft.wiki/w/Enchantment_provider "Enchantment provider")[Enchantment provider](https://minecraft.wiki/w/Enchantment_provider "Enchantment provider") * [![](/images/ItemSprite_painting.png?55d20)](https://minecraft.wiki/w/Painting_variant_definition "Painting variant definition")[Painting variant](https://minecraft.wiki/w/Painting_variant_definition "Painting variant definition") * [![](/images/BlockSprite_white-banner.png?8b4d0)](https://minecraft.wiki/w/Banner_pattern_definition "Banner pattern definition")[Banner pattern](https://minecraft.wiki/w/Banner_pattern_definition "Banner pattern definition") * [![](/images/ItemSprite_goat-horn.png?e5a9f)](https://minecraft.wiki/w/Instrument_definition "Instrument definition")[Instrument](https://minecraft.wiki/w/Instrument_definition "Instrument definition") * [![](/images/BlockSprite_jukebox.png?86205)](https://minecraft.wiki/w/Jukebox_song_definition "Jukebox song definition")[Jukebox song](https://minecraft.wiki/w/Jukebox_song_definition "Jukebox song definition") * [![](/images/BlockSprite_trial-spawner.png?0a3dc)](https://minecraft.wiki/w/Trial_spawner_configuration "Trial spawner configuration")[Trial spawner configuration](https://minecraft.wiki/w/Trial_spawner_configuration "Trial spawner configuration") * [![](/images/EntitySprite_pig.png?5435e)](https://minecraft.wiki/w/Mob_variant_definitions "Mob variant definitions")[Mob variants](https://minecraft.wiki/w/Mob_variant_definitions "Mob variant definitions") * [![](/images/ItemSprite_paper.png?565a1)](https://minecraft.wiki/w/Dialog "Dialog")[Dialog](https://minecraft.wiki/w/Dialog "Dialog") * [![](/images/ItemSprite_wayfinder-armor-trim.png?ffaf0)](https://minecraft.wiki/w/Armor_trim_definition "Armor trim definition")[Armor trim](https://minecraft.wiki/w/Armor_trim_definition "Armor trim definition") * [![](/images/ItemSprite_footprint.png?1c844)](https://minecraft.wiki/w/Slot_sources "Slot sources")[Slot sources](https://minecraft.wiki/w/Slot_sources "Slot sources") * [![](/images/ItemSprite_clock.png?30324)](https://minecraft.wiki/w/Timeline "Timeline")[Timeline](https://minecraft.wiki/w/Timeline "Timeline") * [![](/images/EntitySprite_villager.png?05433)](https://minecraft.wiki/w/Villager_trade_definition "Villager trade definition")[Villager trade](https://minecraft.wiki/w/Villager_trade_definition "Villager trade definition") * [Trade set](https://minecraft.wiki/w/Trade_set "Trade set") * [World Clock](https://minecraft.wiki/w/World_Clock "World Clock") * [![](/images/EntitySprite_sulfur-cube.png?ad68d)](https://minecraft.wiki/w/Sulfur_cube_archetype_definition "Sulfur cube archetype definition")[Sulfur cube archetype](https://minecraft.wiki/w/Sulfur_cube_archetype_definition "Sulfur cube archetype definition")​[*upcoming: [JE 26.2](https://minecraft.wiki/w/Java_Edition_26.2 "Java Edition 26.2")*]  |  |  | | --- | --- | | [Tag](https://minecraft.wiki/w/Tag_%28Java_Edition%29 "Tag (Java Edition)") | * [![](/images/BlockSprite_grass-block.png?97c2e)](https://minecraft.wiki/w/Block_tag_%28Java_Edition%29 "Block tag (Java Edition)")[Block](https://minecraft.wiki/w/Block_tag_%28Java_Edition%29 "Block tag (Java Edition)") * [![](/images/EnvSprite_item.png?89d23)](https://minecraft.wiki/w/Item_tag_%28Java_Edition%29 "Item tag (Java Edition)")[Item](https://minecraft.wiki/w/Item_tag_%28Java_Edition%29 "Item tag (Java Edition)") * [![](/images/BlockSprite_repeating-command-block.png?1dad0)](https://minecraft.wiki/w/Function_tag_%28Java_Edition%29 "Function tag (Java Edition)")[Function](https://minecraft.wiki/w/Function_tag_%28Java_Edition%29 "Function tag (Java Edition)") * [![](/images/ItemSprite_water-bucket.png?6e72b)](https://minecraft.wiki/w/Fluid_tag_%28Java_Edition%29 "Fluid tag (Java Edition)")[Fluid](https://minecraft.wiki/w/Fluid_tag_%28Java_Edition%29 "Fluid tag (Java Edition)") * [![](/images/EnvSprite_entities.png?94711)](https://minecraft.wiki/w/Entity_type_tag_%28Java_Edition%29 "Entity type tag (Java Edition)")[Entity type](https://minecraft.wiki/w/Entity_type_tag_%28Java_Edition%29 "Entity type tag (Java Edition)") * [![](/images/BlockSprite_sculk-sensor.png?ccbdb)](https://minecraft.wiki/w/Game_event_tag_%28Java_Edition%29 "Game event tag (Java Edition)")[Game event](https://minecraft.wiki/w/Game_event_tag_%28Java_Edition%29 "Game event tag (Java Edition)") * [![](/images/BiomeSprite_forest.png?98e29)](https://minecraft.wiki/w/Biome_tag_%28Java_Edition%29 "Biome tag (Java Edition)")[Biome](https://minecraft.wiki/w/Biome_tag_%28Java_Edition%29 "Biome tag (Java Edition)") * [![](/images/EnvSprite_superflat.png?54c14)](https://minecraft.wiki/w/Flat_level_generator_preset_tag_%28Java_Edition%29 "Flat level generator preset tag (Java Edition)")[Flat level generator preset](https://minecraft.wiki/w/Flat_level_generator_preset_tag_%28Java_Edition%29 "Flat level generator preset tag (Java Edition)") * [![](/images/EnvSprite_mountain.png?2e0ae)](https://minecraft.wiki/w/World_preset_tag_%28Java_Edition%29 "World preset tag (Java Edition)")[World preset](https://minecraft.wiki/w/World_preset_tag_%28Java_Edition%29 "World preset tag (Java Edition)") * [![](/images/EnvSprite_jungle-pyramid.png?736e3)](https://minecraft.wiki/w/Structure_tag_%28Java_Edition%29 "Structure tag (Java Edition)")[Structure](https://minecraft.wiki/w/Structure_tag_%28Java_Edition%29 "Structure tag (Java Edition)") * [![](/images/BlockSprite_lodestone.png?00f1a)](https://minecraft.wiki/w/Point_of_interest_type_tag_%28Java_Edition%29 "Point of interest type tag (Java Edition)")[Point of interest type](https://minecraft.wiki/w/Point_of_interest_type_tag_%28Java_Edition%29 "Point of interest type tag (Java Edition)") * [![](/images/ItemSprite_painting.png?55d20)](https://minecraft.wiki/w/Painting_variant_tag_%28Java_Edition%29 "Painting variant tag (Java Edition)")[Painting variant](https://minecraft.wiki/w/Painting_variant_tag_%28Java_Edition%29 "Painting variant tag (Java Edition)") * [![](/images/BlockSprite_white-banner.png?8b4d0)](https://minecraft.wiki/w/Banner_pattern_tag_%28Java_Edition%29 "Banner pattern tag (Java Edition)")[Banner pattern](https://minecraft.wiki/w/Banner_pattern_tag_%28Java_Edition%29 "Banner pattern tag (Java Edition)") * [![](/images/ItemSprite_goat-horn.png?e5a9f)](https://minecraft.wiki/w/Instrument_tag_%28Java_Edition%29 "Instrument tag (Java Edition)")[Instrument](https://minecraft.wiki/w/Instrument_tag_%28Java_Edition%29 "Instrument tag (Java Edition)") * ![❤️](/images/Heart_%28icon%29.png?faf83) [Damage type](https://minecraft.wiki/w/Damage_type_tag_%28Java_Edition%29 "Damage type tag (Java Edition)") * [![](/images/ItemSprite_enchanted-book.png?b7877)](https://minecraft.wiki/w/Enchantment_tag_%28Java_Edition%29 "Enchantment tag (Java Edition)")[Enchantment](https://minecraft.wiki/w/Enchantment_tag_%28Java_Edition%29 "Enchantment tag (Java Edition)") * [![](/images/ItemSprite_paper.png?565a1)](https://minecraft.wiki/w/Dialog_tag_%28Java_Edition%29 "Dialog tag (Java Edition)")[Dialog](https://minecraft.wiki/w/Dialog_tag_%28Java_Edition%29 "Dialog tag (Java Edition)") * [![](/images/ItemSprite_clock.png?30324)](https://minecraft.wiki/w/Timeline_tag_%28Java_Edition%29 "Timeline tag (Java Edition)")[Timeline](https://minecraft.wiki/w/Timeline_tag_%28Java_Edition%29 "Timeline tag (Java Edition)") * [![](/images/ItemSprite_water-bottle.png?fe7c2)](https://minecraft.wiki/w/Potion_tag_%28Java_Edition%29 "Potion tag (Java Edition)")[Potion](https://minecraft.wiki/w/Potion_tag_%28Java_Edition%29 "Potion tag (Java Edition)") * [![](/images/EntitySprite_villager.png?05433)](https://minecraft.wiki/w/Villager_trade_tag_%28Java_Edition%29 "Villager trade tag (Java Edition)")[Villager trade](https://minecraft.wiki/w/Villager_trade_tag_%28Java_Edition%29 "Villager trade tag (Java Edition)") * [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Configured_feature_tag_%28Java_Edition%29 "Configured feature tag (Java Edition)")[Configured feature](https://minecraft.wiki/w/Configured_feature_tag_%28Java_Edition%29 "Configured feature tag (Java Edition)") | | [GameTest](https://minecraft.wiki/w/GameTest "GameTest") | * [![](/images/BlockSprite_test-block-start.png?35191)](https://minecraft.wiki/w/Test_environment_definition "Test environment definition")[Test environment](https://minecraft.wiki/w/Test_environment_definition "Test environment definition") * [![](/images/BlockSprite_test-instance-block.png?27a39)](https://minecraft.wiki/w/Test_instance_definition "Test instance definition")[Test instance](https://minecraft.wiki/w/Test_instance_definition "Test instance definition") | | [World generation](https://minecraft.wiki/w/Custom_world_generation "Custom world generation") | * [Dimension](https://minecraft.wiki/w/Dimension_definition "Dimension definition") * [![](/images/EnvSprite_nether-portal.png?47646)](https://minecraft.wiki/w/Dimension_type "Dimension type")[Dimension type](https://minecraft.wiki/w/Dimension_type "Dimension type") * [![](/images/EnvSprite_mountain.png?2e0ae)](https://minecraft.wiki/w/World_preset_definition "World preset definition")[World preset](https://minecraft.wiki/w/World_preset_definition "World preset definition") * [![](/images/EnvSprite_biomes.png?0a976)](https://minecraft.wiki/w/Biome_definition "Biome definition")[Biomes](https://minecraft.wiki/w/Biome_definition "Biome definition") * [![](/images/EnvSprite_cave.png?47a17)](https://minecraft.wiki/w/Carver_definition "Carver definition")[Carver](https://minecraft.wiki/w/Carver_definition "Carver definition") * [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Configured_feature "Configured feature")[Configured feature](https://minecraft.wiki/w/Configured_feature "Configured feature")   + [![](/images/EnvSprite_oak.png?742a4)](https://minecraft.wiki/w/Tree_definition "Tree definition")[Tree](https://minecraft.wiki/w/Tree_definition "Tree definition") * [![](/images/EnvSprite_map.png?b863e)](https://minecraft.wiki/w/Placed_feature "Placed feature")[Placed feature](https://minecraft.wiki/w/Placed_feature "Placed feature") * [Environment attribute](https://minecraft.wiki/w/Environment_attribute "Environment attribute")  |  |  | | --- | --- | | [Noise settings](https://minecraft.wiki/w/Noise_settings "Noise settings") | * [![](/images/EnvSprite_mountain.png?2e0ae)](https://minecraft.wiki/w/Noise_router "Noise router")[Noise router](https://minecraft.wiki/w/Noise_router "Noise router") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Density_function "Density function")[Density function](https://minecraft.wiki/w/Density_function "Density function") * [Noises](https://minecraft.wiki/w/Noise "Noise") * [![](/images/EnvSprite_surface.png?75bf7)](https://minecraft.wiki/w/Surface_rule "Surface rule")[Surface rule](https://minecraft.wiki/w/Surface_rule "Surface rule") | | [Structures](https://minecraft.wiki/w/Structure_definition "Structure definition") | * [![](/images/EnvSprite_abandoned-mineshaft.png?fab65)](https://minecraft.wiki/w/Structure_set "Structure set")[Structure set](https://minecraft.wiki/w/Structure_set "Structure set") * [![](/images/BlockSprite_jigsaw.png?ec5e3)](https://minecraft.wiki/w/Template_pool "Template pool")[Template pool](https://minecraft.wiki/w/Template_pool "Template pool") * [![](/images/BlockSprite_cracked-stone-bricks.png?f3f1d)](https://minecraft.wiki/w/Processor_list "Processor list")[Processor list](https://minecraft.wiki/w/Processor_list "Processor list") * [![](/images/EnvSprite_nether-fossil.png?93621)](https://minecraft.wiki/w/Structure_file "Structure file")[Structure templates](https://minecraft.wiki/w/Structure_file "Structure file") | | Removed | * [![](/images/ItemSprite_iron-pickaxe.png?77536)](https://minecraft.wiki/w/Configured_surface_builder "Configured surface builder")[Configured surface builder](https://minecraft.wiki/w/Configured_surface_builder "Configured surface builder") | | | | Data packs | * [![](/images/BlockSprite_deepslate.png?d7361)](https://minecraft.wiki/w/Caves_%26_Cliffs_Prototype_Data_Pack "Caves & Cliffs Prototype Data Pack")[Caves & Cliffs Prototype Data Pack](https://minecraft.wiki/w/Caves_%26_Cliffs_Prototype_Data_Pack "Caves & Cliffs Prototype Data Pack") * [![](/images/ItemSprite_magical-painting.png?b0bf0)](https://minecraft.wiki/w/Phantom_Frames "Phantom Frames")[Phantom Frames](https://minecraft.wiki/w/Phantom_Frames "Phantom Frames") | | Tutorials | * [![](/images/thumb/EnvSprite_autosave.png/16px-EnvSprite_autosave.png?a55e7)](https://minecraft.wiki/w/Tutorial%3AImporting_a_data_pack "Tutorial:Importing a data pack")[Importing](https://minecraft.wiki/w/Tutorial%3AImporting_a_data_pack "Tutorial:Importing a data pack") * [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Tutorial%3ACreating_a_data_pack "Tutorial:Creating a data pack")[Creating](https://minecraft.wiki/w/Tutorial%3ACreating_a_data_pack "Tutorial:Creating a data pack") * [Optimizing](https://minecraft.wiki/w/Tutorial%3AOptimizing_a_data_pack "Tutorial:Optimizing a data pack") * [![](/images/BlockSprite_command-block.png?e7078)](https://minecraft.wiki/w/Tutorial%3ACommand_blocks_and_functions "Tutorial:Command blocks and functions")[Command blocks and functions](https://minecraft.wiki/w/Tutorial%3ACommand_blocks_and_functions "Tutorial:Command blocks and functions") * [Repairing a world corrupted by a data pack](https://minecraft.wiki/w/Tutorial%3ARepairing_a_world_corrupted_by_a_data_pack "Tutorial:Repairing a world corrupted by a data pack")  |  |  | | --- | --- | | Content | * [![](/images/ItemSprite_enchanted-book.png?b7877)](https://minecraft.wiki/w/Tutorial%3AAdding_custom_enchantments "Tutorial:Adding custom enchantments")[Custom enchantments](https://minecraft.wiki/w/Tutorial%3AAdding_custom_enchantments "Tutorial:Adding custom enchantments") * [![](/images/ItemSprite_painting.png?55d20)](https://minecraft.wiki/w/Tutorial%3AAdding_custom_paintings "Tutorial:Adding custom paintings")[Custom paintings](https://minecraft.wiki/w/Tutorial%3AAdding_custom_paintings "Tutorial:Adding custom paintings") * [![](/images/ItemSprite_armor-trim.png?1d672)](https://minecraft.wiki/w/Tutorial%3AAdding_custom_trims "Tutorial:Adding custom trims")[Custom trims](https://minecraft.wiki/w/Tutorial%3AAdding_custom_trims "Tutorial:Adding custom trims") | | World generation | * [![](/images/EnvSprite_other-portal.png?ca57b)](https://minecraft.wiki/w/Tutorial%3AAdding_a_new_dimension "Tutorial:Adding a new dimension")[New dimension](https://minecraft.wiki/w/Tutorial%3AAdding_a_new_dimension "Tutorial:Adding a new dimension") * [![](/images/EnvSprite_lunar-base.png?648e4)](https://minecraft.wiki/w/Tutorial%3ACustom_structures "Tutorial:Custom structures")[Custom structures](https://minecraft.wiki/w/Tutorial%3ACustom_structures "Tutorial:Custom structures") | | | |
| | [Resource pack](https://minecraft.wiki/w/Resource_pack "Resource pack") | | | --- | --- | | Components | * [pack.mcmeta](https://minecraft.wiki/w/Pack.mcmeta "Pack.mcmeta") * [![](/images/EnvSprite_number.png?9ceb9)](https://minecraft.wiki/w/Pack_format "Pack format")[Pack format](https://minecraft.wiki/w/Pack_format "Pack format") * [![](/images/EnvSprite_language.png?39da2)](https://minecraft.wiki/w/Resource_pack#Language "Resource pack")[Language](https://minecraft.wiki/w/Resource_pack#Language "Resource pack") * [![](/images/EntitySprite_creeper.png?703e9)](https://minecraft.wiki/w/Model "Model")[Models](https://minecraft.wiki/w/Model "Model") * [![](/images/BlockSprite_double-stone-slab.png?62750)](https://minecraft.wiki/w/Blockstates_definition "Blockstates definition")[Blockstates](https://minecraft.wiki/w/Blockstates_definition "Blockstates definition") * [![](/images/EnvSprite_item.png?89d23)](https://minecraft.wiki/w/Items_model_definition "Items model definition")[Items](https://minecraft.wiki/w/Items_model_definition "Items model definition") * [![](/images/EnvSprite_ambience.png?d7c92)](https://minecraft.wiki/w/Sound "Sound")[Sounds](https://minecraft.wiki/w/Sound "Sound") ([sounds.json](https://minecraft.wiki/w/Sounds.json "Sounds.json")) * [Shaders](https://minecraft.wiki/w/Shader "Shader") * [![](/images/EnvSprite_texture-pack.png?a4213)](https://minecraft.wiki/w/Resource_pack#Textures "Resource pack")[Textures](https://minecraft.wiki/w/Resource_pack#Textures "Resource pack") * [![](/images/ItemSprite_compass.png?2364d)](https://minecraft.wiki/w/Atlas "Atlas")[Atlases](https://minecraft.wiki/w/Atlas "Atlas") * [Aa](https://minecraft.wiki/w/Font "Font") [Fonts](https://minecraft.wiki/w/Font "Font") * [![](/images/BlockSprite_oak-leaves.png?81553)](https://minecraft.wiki/w/Resource_pack#Colormaps "Resource pack")[Colormaps](https://minecraft.wiki/w/Resource_pack#Colormaps "Resource pack") * ![File file.png: Sprite image for file in Minecraft](/images/thumb/File_file.png/16px-File_file.png?e19ce) [Texts](https://minecraft.wiki/w/Resource_pack#Texts "Resource pack") * [![](/images/Locator_Bar_icon_bowtie.png?a8cd8)](https://minecraft.wiki/w/Waypoint_style "Waypoint style")[Waypoint styles](https://minecraft.wiki/w/Waypoint_style "Waypoint style") * [regional\_compliancies.json](https://minecraft.wiki/w/Resource_pack#Regional_compliancies_warnings "Resource pack") * [![](/images/ItemSprite_all-iron-armor.png?87e31)](https://minecraft.wiki/w/Equipment "Equipment")[Equipment](https://minecraft.wiki/w/Equipment "Equipment") | | Debug | * [Missing font character](https://minecraft.wiki/w/Missing_font_character "Missing font character") * [![](/images/BlockSprite_missingno.png?031f4)](https://minecraft.wiki/w/Missing_model "Missing model")[Missing model](https://minecraft.wiki/w/Missing_model "Missing model") * [![](/images/BlockSprite_missingno.png?031f4)](https://minecraft.wiki/w/Missing_texture "Missing texture")[Missing texture](https://minecraft.wiki/w/Missing_texture "Missing texture") | | Tools | * [Slicer](https://minecraft.wiki/w/Slicer "Slicer")  |  |  | | --- | --- | | Legacy | * [Texture Ender](https://minecraft.wiki/w/Texture_Ender "Texture Ender") * [Unstitcher](https://minecraft.wiki/w/Unstitcher "Unstitcher") | | | Tutorials | * [![](/images/thumb/Wrench.png/16px-Wrench.png?4711e)](https://minecraft.wiki/w/Tutorial%3ACreating_a_resource_pack "Tutorial:Creating a resource pack")[Creating](https://minecraft.wiki/w/Tutorial%3ACreating_a_resource_pack "Tutorial:Creating a resource pack") * [![](/images/Download.png?048e3)](https://minecraft.wiki/w/Tutorial%3ALoading_a_resource_pack "Tutorial:Loading a resource pack")[Loading](https://minecraft.wiki/w/Tutorial%3ALoading_a_resource_pack "Tutorial:Loading a resource pack") * [![](/images/EnvSprite_fluids.png?58a6a)](https://minecraft.wiki/w/Tutorial%3AModels "Tutorial:Models")[Models](https://minecraft.wiki/w/Tutorial%3AModels "Tutorial:Models") * [![](/images/EnvSprite_ambience.png?d7c92)](https://minecraft.wiki/w/Tutorial%3ASound_directory "Tutorial:Sound directory")[Sound directory](https://minecraft.wiki/w/Tutorial%3ASound_directory "Tutorial:Sound directory") | | |

Retrieved from "<https://minecraft.wiki/w/Text_component_format?oldid=3611471>"

[Categories](https://minecraft.wiki/w/Special%3ACategories "Special:Categories"):

* [Java Edition technical](https://minecraft.wiki/w/Category%3AJava_Edition_technical "Category:Java Edition technical")
* [Development](https://minecraft.wiki/w/Category%3ADevelopment "Category:Development")

Hidden category:

* [Verify](https://minecraft.wiki/w/Category%3AVerify "Category:Verify")

## Navigation menu

### Personal tools

* [Create account](https://minecraft.wiki/w/Special%3ACreateAccount?returnto=Text+component+format "You are encouraged to create an account and log in; however, it is not mandatory")
* [Log in](https://minecraft.wiki/w/Special%3AUserLogin?returnto=Text+component+format "You are encouraged to log in; however, it is not mandatory [o]")

### associated-pages

* [Page](https://minecraft.wiki/w/Text_component_format "View the content page [c]")
* [Talk](https://minecraft.wiki/w/Talk%3AText_component_format "Talk about the content page [t]")

[ ]

English

### Views

* [Read](https://minecraft.wiki/w/Text_component_format)
* [Edit](https://minecraft.wiki/w/Text_component_format?veaction=edit "Edit this page [v]")
* [Edit source](https://minecraft.wiki/w/Text_component_format?action=edit "Edit the source code of this page [e]")
* [View history](https://minecraft.wiki/w/Text_component_format?action=history "Past revisions of this page [h]")
