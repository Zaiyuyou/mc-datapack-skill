---
name: "minecraft-datapack"
description: "Minecraft Java Edition datapack development suite (v26.1.2). Entry point for all datapack-related skills. Invoke when user asks about Minecraft datapacks, data pack creation, or any Minecraft Java Edition content authoring."
---

# Minecraft Datapack Development Suite

本项目包含完整的 Minecraft Java Edition 数据包开发工具集（版本 **26.1.2**），覆盖从数据包结构到具体 JSON 文件的全部技能。

## 目录结构

```
minecraft_datapack/
├── datapack/        # 数据包骨架 (pack.mcmeta, 目录结构, 加载顺序)
├── function/        # 函数 (mcfunction files, macros, function tags)
├── commands/        # 命令参考 (所有 JE 命令完整参考)
├── advancement/     # 进度系统 (57+ 触发器类型)
├── loot-table/      # 战利品表 (掉落、箱子、钓鱼、交易等)
├── predicate/       # 谓词/条件 (20+ 谓词类型)
├── recipe/          # 配方 (crafting, smelting, smithing, dye 等)
├── item-modifier/   # 物品修饰器 (40+ 修饰函数)
├── enchantment/     # 附魔数据驱动系统
├── tags/            # 标签系统 (blocks, items, entities, functions 等)
├── worldgen/        # 世界生成 (维度、生物群系、地物、结构等)
└── knowledges/      # Minecraft Wiki 知识库 (NBT, 实体, 数据组件等)
```

## 技能索引

### 基础框架

| 技能 | 目录 | SKILL 名称 | 用途 |
|------|------|-----------|------|
| 数据包结构 | `datapack/` | `mcf-datapack` | 创建 pack.mcmeta、设置目录结构、配置加载顺序和叠加层 |
| 函数 | `function/` | `mcf-function` | 编写 .mcfunction 文件、宏、函数标签 (#load, #tick)、调度 |
| 命令 | `commands/` | `mcf-commands` | 所有 JE 命令完整参考(/execute, /scoreboard, /data 等) |

### 内容定义

| 技能 | 目录 | SKILL 名称 | 用途 |
|------|------|-----------|------|
| 进度 | `advancement/` | `mcf-advancement` | 自定义进度树、触发器、奖励、配方解锁 |
| 战利品表 | `loot-table/` | `mcf-loot-table` | 物品掉落、箱子战利品、实体掉落、钓鱼、考古 |
| 配方 | `recipe/` | `mcf-recipe` | 自定义合成、烧炼、锻造、染色等配方 |
| 物品修饰器 | `item-modifier/` | `mcf-item-modifier` | 物品属性修改、通过 /item modify 或战利品表使用 |
| 附魔 | `enchantment/` | `mcf-enchantment` | 自定义附魔、效果值、实体效果、组件效果 |
| 标签 | `tags/` | `mcf-tags` | 分组方块/物品/实体/函数/生物群系等 |
| 谓词 | `predicate/` | `mcf-predicate` | 条件检查，用于战利品表、进度、execute 命令 |

### 世界生成

| 技能 | 目录 | SKILL 名称 | 用途 |
|------|------|-----------|------|
| 世界生成 | `worldgen/` | `mcf-worldgen` | 自定义维度、生物群系、地物、结构、噪声设置等 |

### 知识库

| 技能 | 目录 | SKILL 名称 | 用途 |
|------|------|-----------|------|
| Wiki 知识库 | `knowledges/` | `knowledges` | NBT、实体数据、数据组件、文本组件、计分板等参考 |

## 使用流程

### 1. 创建新数据包
1. 调用 `datapack/` 技能 → 生成 pack.mcmeta 和目录结构
2. 调用 `function/` 技能 → 编写核心函数逻辑
3. 根据需求调用对应内容定义技能（advancement, loot-table, recipe 等）

### 2. 编写具体内容
- 每个子目录的 SKILL.md 都包含完整的 JSON 结构参考
- 使用 `commands/` 技能查询命令语法
- 使用 `knowledges/` 技能查询 NBT、实体格式、数据组件等背景知识

### 3. 调试与测试
- 命令语法 → `commands/` 技能
- 条件检查（/execute if predicate）→ `predicate/` 技能
- 物品状态 → `item-modifier/` 技能 + `knowledges/` 的数据组件知识

## 注意事项

- 所有技能针对 **Minecraft Java Edition 26.1.2**
- 技能文件位于每个子目录的 `SKILL.md` 中
- 当本地知识不足时，`knowledges/` 技能会自动引导到 [Minecraft Wiki](https://minecraft.wiki/)


## 使用原则

### 1. 优先查阅本地知识库

当用户的问题涉及上述主题时，**先检查本地文件**，直接引用对应文件的内容。

### 2. 本地不足时到 Wiki 搜索

如果本地文件没有覆盖到用户需要的具体知识（例如某个特定方块/物品/实体的细节、不常见的特性、历史版本变更等），**自动到 Minecraft Wiki 搜索**：

- 基础搜索：`https://minecraft.wiki/w/{PageName}`
- 搜索特定命令/物品/方块：直接构造 URL `https://minecraft.wiki/w/{PascalCase名称}`
- 示例：`/w/Command_block`、`/w/Diamond_Sword`、`/w/Effect`

### 3. 快速关联嗅探

使用 `https://minecraft.wiki/w/Special:WhatLinksHere/` 反向查找哪些页面链接到当前页面，用于发现关联知识：

- **用途**：当需要了解某个主题的上下游关联时（如"哪些方块使用了这个 NBT 标签"），用此页面嗅探关联条目
- **格式**：`https://minecraft.wiki/w/Special:WhatLinksHere/{PageName}`
- **示例**：`/w/Special:WhatLinksHere/Scoreboard` 可以找到所有提到了计分板的页面（如命令、触发器、进度等）

### 4. 引用规范

引用 Wiki 内容时在回复中注明来源，例如 `[Minecraft Wiki - Scoreboard](https://minecraft.wiki/w/Scoreboard)`。

### 5. 搜索策略流程图

```
用户提问
  ├─ 主题在本地 knowledges/ 中？ → 直接读取本地文件回答
  └─ 主题不在本地？
       ├─ 明确页面名 → 直接构造 wiki URL 搜索
       └─ 不确定页面名
            ├─ 搜索 `https://minecraft.wiki/w/Special:Search?search={关键词}`
            └─ 用 WhatLinksHere 嗅探相关度最高的页面
```
