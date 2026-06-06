---
name: "usual-knowledges"
description: "Minecraft Wiki knowledge base for datapack/mod development. Invoke when user asks about Minecraft mechanics, NBT, entities, scoreboard, data components, or needs info not in local files."
license: MIT
compatibility: opencode
metadata:
  version: "1.0"
  game-version: "26.1.2"
  category: minecraft-datapack
---

# Minecraft Wiki Knowledge Base

## 本地知识库文件

```
knowledges/
├── NBT_format.md              # NBT/SNBT 格式
├── Entity_format.md           # 实体 NBT 数据格式
├── Data_component_format.md   # 数据组件 (1.20.5+)
├── Text_component_format.md   # 文本组件 (raw JSON text)
├── Scoreboard.md              # 计分板系统
└── Java_Edition_data_values.md# Java 版数据值
```

## 快速参考

### NBT 格式 (`NBT_format.md`)

| 类型 | TAG ID | SNBT 示例 |
|------|--------|-----------|
| Byte | 1 | `b` 后缀: `1b` |
| Short | 2 | `s` 后缀: `3s` |
| Int | 3 | 无后缀: `42` |
| Long | 4 | `L` 后缀: `7L` |
| Float | 5 | `f` 后缀: `2.5f` |
| Double | 6 | `d` 后缀: `3.14d` 或不带后缀小数 |
| String | 8 | 引号: `"hello"` |
| Byte Array | 7 | `[B;1b,2b,3b]` |
| Int Array | 11 | `[I;1,2,3]` |
| Long Array | 12 | `[L;1L,2L,3L]` |
| List | 9 | `[1,2,3]` 或 `[{...},{...}]` |
| Compound | 10 | `{key: value, ...}` |

NBT 路径语法: `foo.bar[0].baz`、`foo.bar[0..2]`、`foo.bar[-1]`
UUID 简写: `{UUID:[I;1,1,1,1]}` 或 `{UUID:uuid("00000000-0000-0000-0000-000000000001")}`

### 文本组件格式 (`Text_component_format.md`)

**基本结构:**
```json
{"text": "Hello", "color": "red", "bold": true}
```
字符串简写 `"Hello"` 等同于 `{"text": "Hello"}`，列表 `["A", "B"]` 等同于 `{"text": "A", "extra": ["B"]}`。

**内容类型 (type):**
| type | 用途 | 示例 |
|------|------|------|
| `text` | 纯文本 | `{"text": "hello"}` |
| `translatable` | 翻译文本 | `{"translate": "item.minecraft.diamond"}` |
| `score` | 计分板分数 | `{"score": {"name": "@p", "objective": "obj"}}` |
| `selector` | 实体选择器名称 | `{"selector": "@p"}` |
| `keybind` | 按键绑定 | `{"keybind": "key.jump"}` |
| `nbt` | NBT 值 | `{"nbt": "Health", "entity": "@s"}` |

**Click 事件:**
| action | 说明 |
|--------|------|
| `open_url` | 打开 URL |
| `run_command` | 执行命令 |
| `suggest_command` | 填入命令输入框 |
| `copy_to_clipboard` | 复制到剪贴板 |
| `change_page` | 翻页（成书） |

**Hover 事件:**
| action | 说明 |
|--------|------|
| `show_text` | 显示文本 |
| `show_item` | 显示物品 |
| `show_entity` | 显示实体 |

**格式化代码:**
`bold`, `italic`, `underlined`, `strikethrough`, `obfuscated`, `color`（支持命名颜色: black, dark_blue, dark_green, dark_aqua, dark_red, dark_purple, gold, gray, dark_gray, blue, green, aqua, red, light_purple, yellow, white，以及 hex `#RRGGBB`）

**字体设置:**
```json
{"text": "A", "font": "minecraft:default"}
```
内置字体: `minecraft:default`、`minecraft:uniform`、`minecraft:alt`、`minecraft:illageralt`

### 数据组件 (`Data_component_format.md`)

常用组件:

| 组件 ID | 用途 | 命令示例 |
|---------|------|---------|
| `custom_name` | 自定义名称 | `{custom_name: '"Diamond"'}` |
| `lore` | 物品描述 | `{lore: ['"Line 1"', '"Line 2"']}` |
| `custom_data` | 自定义 NBT | `{custom_data: {my_key: "val"}}` |
| `enchantments` | 附魔 | `{enchantments: {levels: {"sharpness": 5}}}` |
| `damage` | 耐久度 | `{damage: 100}` |
| `unbreakable` | 不可破坏 | `{unbreakable: {}}` |
| `food` | 食物属性 | `{food: {nutrition: 6, saturation: 7.2}}` |
| `consumable` | 可消耗 | `{consumable: {consume_seconds: 1.6}}` |
| `attribute_modifiers` | 属性修饰 | `{attribute_modifiers: {modifiers: [{type: "movement_speed", amount: 0.1, operation: "add_value"}]}}` |
| `can_break` / `can_place_on` | 可破坏/放置 | `{can_break: {blocks: ["minecraft:stone"]}}` |
| `item_model` | 物品模型 | `{item_model: "minecraft:diamond"}` |
| `item_name` | 物品名称（不可修改） | `{item_name: '"Special Sword"'}` |
| `block_state` | 方块状态 | `{block_state: {properties: {"facing": "north"}}}` |
| `container` | 容器内容 | `{container: {items: [{slot: 0, item: {id: "diamond", count: 1}}]}}` |
| `fireworks` | 烟花 | `{fireworks: {explosions: [{type: "large_ball", colors: [I;16711680]}]}}` |
| `charged_projectiles` | 弩装载 | `{charged_projectiles: [{id: "arrow", count: 1}]}` |
| `bundle_contents` | 收纳袋内容 | `{bundle_contents: [{id: "diamond", count: 1}]}` |
| `lock` | 容器锁定 | `{lock: {key: {id: "trial_key", count: 1}}}` |
| `custom_model_data` | 自定义模型数据 | `{custom_model_data: 42}` |

### 计分板 (`Scoreboard.md`)

**常用命令:**
```
/scoreboard objectives add <name> <criterion> [<display>]
/scoreboard objectives remove <name>
/scoreboard players set <target> <objective> <score>
/scoreboard players add <target> <objective> <score>
/scoreboard players remove <target> <objective> <score>
/scoreboard players operation <target> <objective> <op> <source> <objective>
/scoreboard players get <target> <objective>
/scoreboard players reset <target> [<objective>]
/scoreboard objectives modify <name> display name <json>
/scoreboard objectives modify <name> rendertype hearts
```

**运算操作符 (operation):**
| 操作 | 效果 |
|------|------|
| `=` | 赋值: target = source |
| `+=` | 加法: target += source |
| `-=` | 减法: target -= source |
| `*=` | 乘法: target *= source |
| `/=` | 整数除法: target /= source |
| `%=` | 取模: target %= source |
| `<` | 取最小值 |
| `>` | 取最大值 |
| `><` | 交换: target <-> source |

**显示槽:**
| 槽位 | 说明 |
|------|------|
| `sidebar` | 右侧边栏 |
| `list` | Tab 列表 |
| `below_name` | 头顶下方 |
| `sidebar.team.<color>` | 队伍专用 |

**实体标签:**
```
/scoreboard players tag <target> add <tag> [<predicate>]
/scoreboard players tag <target> remove <tag> [<predicate>]
```

### 实体数据格式 (`Entity_format.md`)

实体通用字段:

| 字段 | 类型 | 说明 |
|------|------|------|
| `id` | string | 实体 ID (如 `minecraft:zombie`) |
| `Pos` | [double,double,double] | 坐标 |
| `Rotation` | [float,float] | 旋转 (yaw, pitch) |
| `Motion` | [double,double,double] | 速度向量 |
| `FallDistance` | float | 掉落距离 |
| `Fire` | short | 着火时间（tick） |
| `Air` | short | 空气值 |
| `OnGround` | byte | 是否在地面 |
| `Invulnerable` | byte | 是否无敌 |
| `NoGravity` | byte | 是否不受重力 |
| `Tags` | list of string | 标签列表 |
| `CustomName` | JSON text | 自定义名称 |
| `CustomNameVisible` | byte | 始终显示名称 |
| `Silent` | byte | 是否静音 |
| `Passengers` | list | 乘客实体列表 |
| `UUID` | int array | UUID `[I;1,1,1,1]` |

### Java 版数据值 (`Java_Edition_data_values.md`)

包含方块、物品、实体、生物群系、粒子、声音事件、自定义统计等 ID 的完整参考。用于需要查找特定 ID 的场景，如 `setblock minecraft:stone`、`particle minecraft:heart` 等。

## 使用原则

### 1. 优先查阅本地知识库

用户问题涉及 NBT、实体、数据组件、文本组件、计分板等 → **先读本地文件**，直接引用内容回答。

### 2. 本地不足时到 Wiki 搜索

- 基础搜索: `https://minecraft.wiki/w/{PageName}`
- 命令/方块/物品: `https://minecraft.wiki/w/{PascalCase名称}`
- 搜索: `https://minecraft.wiki/w/Special:Search?search={关键词}`

### 3. 快速关联嗅探

`https://minecraft.wiki/w/Special:WhatLinksHere/{PageName}` 反向查找关联页面。

### 4. 引用规范

引用时注明来源: `[Minecraft Wiki - 页面名](https://minecraft.wiki/w/页面名)`
