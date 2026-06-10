> 来源链接：/uploads/ClaudeCode.mp4

<think>
The user wants me to create detailed, structured notes from a video transcript about Claude Code. The notes need to be in Chinese, well-organized, and comprehensive. Let me analyze the content and structure it properly.

The video covers:
1. Introduction to Claude Code
2. Environment setup and basic interaction
3. Complex task handling and terminal control
4. Multi-modal and context management
5. Advanced features and customization

Let me create comprehensive notes in Chinese with proper Markdown formatting, avoiding the numbered list rendering issue.
</think>
# Claude Code 实战指南

## 视频概述

最近 Claude Code 非常火，这期视频将从头到尾把 Claude Code 的实战流程彻底走一遍。光会敲几个简单的命令远远不够，本视频将带大家从入门到生产环境落地。

**视频分为以下四个部分：**
- 环境的搭建与基础交互
- 复杂任务处理与终端控制
- 多模态与上下文管理
- 高级功能的扩展与定制

> 市场上的同类产品（如 Codex、Open Code 等）跟 Claude Code 在功能和使用上没有太大区别，看完本视频可以一通百通。

---

## 第一部分：环境搭建与基础交互

### 安装流程

1. 访问 Claude Code 官方网站
2. 点击复制按钮获取安装命令
3. 回到终端粘贴执行，开始安装

### 初始配置

```bash
mkdir my-to-do       # 创建项目目录
cd my-to-do          # 进入项目目录
claude               # 打开 Claude Code
```

### 登录方式

Claude Code 官方提供两种标准接入方式：

| 方式 | 说明 |
|------|------|
| 订阅制 | 购买 Claude 的 Pro 或 Max 会员，直接选择此项 |
| API Key | 使用官方 API Key，按 token 用量计费，费用多少花多少 |

登录流程：
- Claude Code 会弹出网页进行授权
- 同意授权后回到终端按回车完成登录

### 使用其他模型驱动 Claude Code

Claude Code 是一个通用的编程 Agent，本身并不跟 Claude 模型绑定，可以完全使用其他模型来驱动：
- 支持国产模型如 GLM、minimax 等
- 只需要设置几个环境变量即可
- 具体方法网上搜索即可

### 三种工作模式

Claude Code 通过 `Shift + Tab` 在三种模式之间循环切换：

#### 1\. 默认模式（显示 `? for shortcuts`）

- 创建和修改文件前一定会询问用户
- 表现最为谨慎，最为稳妥
- 进入 Claude Code 时默认使用此模式

#### 2\. 自动模式（显示 `accept edits on`）

- Claude Code 会自动创建或修改文件
- 不会去询问用户
- 最为方便

#### 3\. 规划模式（Plan Mode）

- 只讨论不修改文件
- 适合构思复杂方案
- 专门用来讨论方案、确定细节

### 文件操作的权限选项

当 Claude Code 想要创建或修改文件时，会出现三个选项：

| 选项 | 说明 |
|------|------|
| Yes（单次授权） | 只同意当前这一个文件操作，后续操作还会再次询问 |
| Yes, allow all edits during this session | 本次对话期间后续所有文件操作自动通过，不再反复打扰 |
| No | 不同意，可以继续输入想法，Claude Code 根据输入重新生成代码并再次确认 |

### 多行输入与外部编辑器

**多行输入：**
- 换行需要按 `Shift + Enter`
- 直接敲回车会提交问题
- 如果 `Shift + Enter` 不起作用，大概率版本较旧，需要升级

**使用 VS Code 编辑输入：**
- 按 `Ctrl + G` 可以打开一个 VS Code 标签页
- 在 VS Code 中编辑更方便，回车随便按也不用担心误提交
- 要求事先装好 VS Code
- 保存并关掉标签页后，内容会自动放回输入框

### 在 Claude Code 中执行终端命令

使用 `!` 即可进入 wash 模式，可以运行任意终端命令：

```bash
! open index.html
```

---

## 第二部分：复杂任务处理与终端控制

### 实际项目：待办软件

**初始实现：**

提示 Claude Code 创建一个待办软件（使用 HTML 实现）：

```
给我做一个待办软件，使用 HTML 实现
```

Claude Code 会自动创建 `index.html` 文件。

**架构问题：**
- 初始版本所有代码都写在 `index.html` 里
- 小项目还可以，但项目做大了维护困难
- 建议换成 React + TypeScript + Vite 现代架构

### 使用规划模式（Plan Mode）

通过 `Shift + Tab` 进入 Plan Mode，然后提出重构需求：

```
将当前的待办应用重构为使用 React + TypeScript + Vite 的项目，
保留所有的现有功能，且 UI 风格保持一致。
```

**计划确认的三选项：**
- 执行计划，并进入自动模式（后续修改文件前不再询问）
- 执行计划，使用默认模式（后续每次写入文件前需要询问）
- 继续修改计划（如果对计划不满意可继续输入，Claude Code 会重新产出）

**迭代修改计划：**
如果对计划不满意，可以继续输入修改意见，例如：

```
给每个待办事项增加一个优先级，比如高、中、低，
并且用不同的颜色标记出来。
```

### 终端命令执行的权限

**关键区别：**
- `accept edits on` 模式只免除文件写入的询问
- 终端命令（如 `mkdir`、`npm install`）Claude Code 认为是比较危险的操作，仍需征得用户同意
- 即使选择第二项，也只是允许以后自由访问特定目录，其他命令仍要询问

### 跳过所有权限检测

```bash
claude --dangerously-skip-permissions
```

- 官方把 "dangerously"（危险的）写在参数名里，意图非常明确
- 一旦加上，Claude Code 会彻底放飞自我
- 进入后模式变成 `bypass permissions on`
- 执行任何终端命令都不会再征求意见

**风险提示：**
- 极大提升开发效率，全自动干活
- 理论上拥有和你一样的终端权限
- 实际破坏电脑的概率微乎其微
- 但仍存在理论上的风险，决定权在你手里

### 后台任务管理

**服务运行会阻塞 Claude Code：**
- 当 `npm run dev` 启动的开发服务器运行时
- Claude Code 没办法处理新的请求
- 因为服务还在运行，进程被占用

**后台运行服务：**
- 按 `Ctrl + B` 可以把服务放置在后台
- Cloud code 才开始处理请求

**查看后台任务：**
```
/tasks
```

可以查看所有后台运行的任务。按 `K` 可以关掉后台服务。按 `ESC` 回到原来界面。

### 回滚功能（Rewind）

每次输入请求时，Claude Code 都会创建一个回滚点。

**触发回滚：**
- 输入 `/rewind` 命令
- 或直接按两下 `ESC` 进入回滚页面
- 选择想要的回归点

**回滚选项：**

| 选项 | 说明 |
|------|------|
| 回滚代码和会话 | 还原代码修改并清除相关对话 |
| 只回滚会话 | 只清除对话历史，保留代码修改 |
| 只回滚代码 | 还原代码修改，保留对话历史 |
| 放弃回滚 | 不执行任何回滚操作 |

**回滚的局限性：**
- Claude Code 只能回滚它自己写入的那些文件
- 由终端命令生成的文件（如 mkdir、npm install 创建的文件）没有办法回滚
- 如果要精准回滚，建议使用 Git 会更好
- 解决办法：手动删掉不需要的文件，保留 `index.html` 等关键文件

### 实际项目演示流程

1. 让 Claude Code 添加切换语言功能（中文/英文）
2. 验证切换效果
3. 使用 rewind 功能回滚
4. 关闭后台 `npm run dev` 服务
5. 进一步回滚到最初只有 `index.html` 的版本
6. 手动清理多余文件

---

## 第三部分：多模态与上下文管理

### 传图片给 Claude Code

**方法一：拖拽**
- 直接把图片拖到 Claude Code 输入框
- 出现 `image 2` 提示代表已接收

**方法二：复制粘贴**
- 复制图片文件
- 来到 Claude Code 输入框按 `Ctrl + V` 粘贴
- **重要**：即使在 Mac OS 上也要用 `Ctrl + V`，`Cmd + V` 不起作用

### 图片还原的局限性

- Claude Code 通过图片还原往往不够精确
- 字体、间距等细节很难把握

### 使用 MCP 精确还原

MCP（Model Context Protocol）是模型与外界沟通的渠道。Figma 提供了好用的 MCP Server。

**安装 Figma MCP Server：**
```bash
# 根据 Figma 官方要求执行安装命令
npx figma-mcp-server
```

**安装后的步骤：**
1. 重新打开 Claude Code（之前的对话没了）
2. 使用 `/resume` 命令回到之前的对话
3. 或使用 `claude -c`（continue 缩写）启动并自动恢复上次对话

**配置 MCP 工具：**
- 执行 `/mcp` 查看已安装的 MCP 工具
- 选择 Figma 工具
- 选择 `authenticate` 进行认证授权
- 认证后状态变为可用
- 选择 `view tools` 查看工具列表（包含截图、创建设计规则等工具）

**使用 Figma MCP 还原设计稿：**

1. 在 Figma 中复制设计稿链接（copy link to selection）
2. 在 Claude Code 中输入需求：

```
修改当前的页面，使它与 Figma 稿件保持一致
[粘贴 Figma 链接]
```

3. Claude Code 调用的 MCP 工具：
   - `get design context` - 获取设计上下文
   - `get_screenshot` - 获取设计稿截图

4. 调完工具后，Claude Code 获取到的信息包括：
   - 设计稿的截图
   - 各种组件的间距、字体、样式等
   - 非常详细

5. Claude Code 根据这些信息修改 HTML 代码

> 还原程度高，但仍有细节需要打磨（如 `undefined` 等），整体效果不错。

### 上下文压缩

随着使用，Claude Code 上下文里会积累大量信息（有些有用，有些没太大用处）。

**压缩命令：**
```bash
/compact
```

可以选择性地在后面追加具体的压缩策略，例如：
```
/compact 重点保留用户提出的需求
```

**查看压缩结果：**
- 按 `Ctrl + O` 可以看到压缩后的上下文内容
- 压缩后 token 消耗量会少很多，性能更有保障

**完全清空上下文：**
```bash
/clear
```

- 比 compact 更为极端，直接清空所有上下文内容
- 适用于后续任务与之前上下文没有关联的情况

**压缩的局限性：**
- 压缩结果的可控性没有那么强
- 想手动改改压缩结果，Claude Code 并没有提供这个选项
- 无论压不压缩，上下文都跟某个会话绑定
- 下次进入 Claude Code 必须要来到这个会话，否则 Claude Code 不知道之前发生了什么

---

## 第四部分：高级功能的扩展与定制

### CLAUDE.md 文件

**作用：**
- 让 Claude Code 每次进入时都读取自己设定的信息
- 让 Claude Code 知道项目是什么、用户有什么需求
- 可以写各种注意事项，让 Claude Code 更好地工作

**生成 CLAUDE.md：**
```bash
/init
```

- Claude Code 自动创建一份 `CLAUDE.md` 文件
- 初始内容是英文的
- 可以让 Claude Code 转为中文
- 内容可以随便修改

**验证生效：**
- 在 `CLAUDE.md` 末尾加注意事项：每次回答的最后必须要追加 "happy coding"
- 重新进入 Claude Code
- 提问 "hi"，回答末尾出现 "happy coding" 说明生效

**打开 CLAUDE.md：**
- 在输入框输入 `/memory`
- 两种类型：
  - **项目级别**：放在当前目录里，对当前项目生效
  - **用户级别**：放在用户目录里，对当前用户生效
- 选择对应项后文件自动打开

### Hook 功能

**概念：**
- 允许用户在运行工具前后等时机执行一段自己指定的逻辑
- 例如：可以用它来做自动格式化
- Cloud code 写完代码后，自动执行设定的格式化函数

**配置流程：**
1. 执行 `/hooks` 进入 hook 配置页面
2. 选择执行时机：
   - 工具使用前（PreToolUse）
   - 工具使用后（PostToolUse）
   - 工具使用失败
   - 发送通知
3. 选择对应的工具（如 Write、Edit）
4. 填入具体的格式化命令

**示例：使用 prettier 格式化文件**

```bash
jq -r '.tool_input.file_path' | xargs prettier --write
```

**命令解析：**
- Cloud code 运行时传入 JSON 结构
- `file_path` 是 Cloud code 刚刚编辑好的文件路径
- `jq` 用来解析 JSON 取出 `file_path` 的值
- `xargs` 把文件路径传递给 `prettier` 命令
- 最后用 `prettier` 格式化文件

**保存级别（三选一）：**

| 级别 | 路径 | 范围 |
|------|------|------|
| 本地项目级别 | `settings.local.json` | 只在本机本项目生效，不会共享给别人 |
| 项目级别 | `settings.json` | 所有使用项目的用户都能用，会随 git 分发 |
| 用户级别 | 用户目录 | 对当前用户生效，每用户一份 |

**实际效果验证：**
- 创建新文件 `test.html`，让所有内容写在一行
- 执行后查看文件内容已被格式化好
- 说明 hook 生效，Cloud code 写入后 hook 启动格式化

### Agent Skill

**概念：**
- 给大模型看的说明书，一个动态加载的 prompt
- 适合需要重复执行、有固定格式要求的任务
- 例如：每天写一份遵循特定格式的开发总结

**创建 Agent Skill：**

1. 在用户目录下创建文件夹：
```bash
mkdir ~/.claude/skills/daily-reports
```

2. 用 VS Code 打开文件夹
3. 创建 `SKILL.md` 文件

**SKILL.md 文件结构：**

分为两部分：
- **前面前言（name 和 description）**：分别代表 agent skill 的名称和描述，Cloud code 根据这部分内容决定是否要使用
- **具体描述**：写明 skill 要遵循的格式要求

**使用 Agent Skill：**

1. 重启 Cloud code
2. 输入 `/skills` 可以看到已发现的 agent skill
3. 两种调用方式：

**方式一：自动调用**
- 输入请求："写一份每日总结"
- Cloud code 自动发现请求与 agent skill 相关
- 请求使用该 skill，用户同意后执行
- 输出符合格式要求的内容

**方式二：手动调用**
```
/daily-reports 写一份今日开发总结
```
- 省去大模型意图识别的过程
- 直接由用户调用，结果更可控

### Sub Agent

**概念：**
- 一个独立的 Agent
- 拥有独立的上下文、独立的工具、独立的 skill
- 可以独立完成某一件事情

**创建用于代码审核的 Sub Agent：**

1. 输入 `/agents`
2. 选择 `create new agents`
3. 选择 agent 类型（项目级别 / 用户级别）
4. 选择创建方法：
   - 用 Cloud code 初始化（推荐）
   - 完全手动创建
5. 描述 agent 要做的事情：

```
这是一个用于代码审核的 sub agents，
在用户要求代码审核的时候调用它
```

6. 选择可用的工具（如 read only tools，只使用只读工具）
7. 选择模型（如默认的 sonnet）
8. 选择显示颜色（如绿色）

**Sub Agent 描述文件结构：**
与 Agent skill 类似：
- **上面原数据**：名称、描述、模型、颜色等
- **下面具体任务**：详细描述要干的事情，如审查准则（JS 检查、CSS 检查）和输出格式要求

**使用 Sub Agent：**
- 重启 Cloud code
- 提交请求："给我做一下代码审核"
- Cloud code 调用创建的 sub agent
- sub agent 用配置的颜色（绿色）展示
- 输出的代码审核报告符合 sub agent 描述里的要求

### Agent Skill vs Sub Agent：核心区别

**对上下文的处理方式不同：**

**Agent Skill：**
- 完全继承并共享当前主对话的上下文
- 执行过程中的每一行日志、每一个思考过程都会进入当前上下文
- 适合处理几万行代码审核时，会逐步塞满上下文窗口
- Token 消耗飙升，Agent 也会因记忆过载变慢变傻
- **适合场景**：与上下文关联比较大且对上下文影响不大的任务
- **举例**：根据今天的开发过程写每日总结

**Sub Agent：**
- 拥有完全独立的上下文
- 启动时开辟全新对话窗口
- 看的所有代码、生成的中间分析过程都不会回传到主对话
- 只有活干完了，才拿最终执行结果来汇报
- 主对话永远干干净净，不会被琐碎中间过程撑爆
- **适合场景**：与上下文关联比较小且对上下文影响比较大的任务

### Plugin（插件）

**概念：**
- 全家桶的安装包
- 类似 Mac OS 的 DMG 或 Windows 下的 EXE 文件
- 把一系列的 skill、sub agents、hook 等能力全部打包在一起
- 一键安装 Cloud code 就能瞬间获得整套高级能力

**插件管理：**
- 输入 `/plugin` 进入插件管理器
- 三个选项：
  - `discover`：发现新插件
  - `installed`：已安装的插件
  - `market places`：插件市场

**安装插件：**
1. 在 `discover` 中找到 `frontend design` 按回车安装
2. 选择安装范围：
   - 对当前用户生效
   - 对当前项目生效
   - 对当前用户的当前项目生效
3. 安装完成

**插件示例：Frontend Design**
- 用来做前端设计的插件
- 据说能打破大模型前端设计的共性（如都用深紫色主题）
- 让界面看起来更加好看
- 排版更加高级，色彩更加协调，交互更符合现代审美

**验证安装：**
- 输入 `/plugin`，选择 `installed`
- 看到 `frontend design` 已安装
- 查看详情：包含一个 `frontend-design` 的 agent skill
- 输入 `/skills` 可以看到多了一个 `frontend design` 的 agent skill

**Plugin 本质：**
- 本质上就是安装了包含的 agent skill
- 一些 plugin 包含多个组成元素（agent skill、MCP、hook 等）
- 可以理解为整套解决能力一次性全部安装

**使用插件：**
- 输入请求："按照 frontend design 的要求做一个待办软件，使用 HTML 来实现"
- Cloud code 意识到用户要求使用 frontend design 的规范
- 请求使用这个 agent skill
- 同意后，Cloud code 拥有 ANTHROPIC 官方沉淀的一整套 UI 设计直觉
- 开始写代码，最终效果与默认风格完全不同

**插件生态：**
- 目前 Cloud code 的插件市场在迅速增长
- 除了 UI 设计外，还有一些针对特定编程语言的 LSP 插件
- 如果自己配置写得很好，可以参考官方文档
- 把 skill、sub agent、MCP 等打包成插件分享给团队或社区

---

## 实用命令速查表

| 命令 | 功能 |
|------|------|
| `claude` | 打开 Claude Code |
| `claude -c` | 继续上一次的对话 |
| `claude --dangerously-skip-permissions` | 跳过所有权限检测 |
| `/login` | 主动触发登录流程 |
| `Shift + Tab` | 循环切换三种模式 |
| `Shift + Enter` | 在输入框中换行 |
| `Ctrl + G` | 用 VS Code 编辑输入 |
| `Ctrl + B` | 把服务放置在后台 |
| `Ctrl + O` | 查看压缩后的上下文内容 |
| `Ctrl + V`（Mac 也是）| 在 Claude Code 中粘贴图片 |
| `!` | 进入 wash 模式执行终端命令 |
| `/tasks` | 查看后台任务 |
| `/rewind` 或双击 `ESC` | 进入回滚页面 |
| `/compact` | 压缩上下文 |
| `/clear` | 清空所有上下文 |
| `/init` | 生成 CLAUDE.md 文件 |
| `/memory` | 打开 CLAUDE.md 文件 |
| `/hooks` | 配置 hooks |
| `/skills` | 查看 agent skills |
| `/agents` | 管理 sub agents |
| `/plugin` | 插件管理器 |
| `/mcp` | 查看已安装的 MCP 工具 |
| `/resume` | 回到之前的对话 |

---

## 核心要点总结

1. **三种模式选择**：默认模式最稳妥，自动模式最方便，规划模式适合讨论方案
2. **终端命令权限**：即使在自动编辑模式下，终端命令仍需授权；可用 `--dangerously-skip-permissions` 跳过（需谨慎）
3. **多模态支持**：支持传图片，但更推荐使用 Figma MCP 精确还原设计稿
4. **上下文管理**：使用 `/compact` 压缩，`/clear` 清空；`CLAUDE.md` 实现项目级配置持久化
5. **Hook 自动化**：在工具使用前后自动执行自定义逻辑（如代码格式化）
6. **Agent Skill vs Sub Agent**：前者共享上下文适合轻量任务，后者独立上下文适合重型任务
7. **Plugin 生态**：一键安装整套高级能力，扩展 Claude Code 的功能边界