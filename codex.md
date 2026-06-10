> 来源链接：https://www.youtube.com/watch?v=HQGUed-e2wM

<think>The user wants me to create detailed, structured notes from a video transcript about Codex (OpenAI's coding assistant). The notes should be in Chinese, comprehensive, well-organized, and follow the Markdown formatting guidelines provided. Let me analyze the transcript carefully and organize it into clear sections.

The video covers:
1. Introduction to Codex
2. Installation and setup
3. Basic features (Annotate, basic operations)
4. Permission modes (default, autoreview, full access)
5. Model settings (thinking depth, fast mode)
6. Git integration
7. Fork functionality
8. Archive functionality
9. AGENTS.md configuration
10. Plan mode
11. Side chat
12. Steer functionality
13. Plugin (Chrome, Computer use, etc.)
14. Skill (imagegen, custom skills)
15. Automation (scheduled tasks)
16. Mobile functionality

Let me structure this comprehensively in Markdown format, ensuring I use the format correctly to avoid numbered list issues.</think>

# Codex 从 0 到 1 全攻略 - 学习笔记

## 视频概览

本期视频系统性地讲解了 **Codex**（OpenAI 的核心产品，对标 Anthropic 的 Claude Code）的核心功能，帮助建立完整的使用思路。Codex 不仅能编写代码、排查 bug、执行测试，还能管理 Git、操作浏览器、甚至直接控制电脑完成各种任务。

视频分为三个部分：
- **基础篇**：快速上手 Codex、核心配置、容易踩坑的地方
- **进阶篇**：版本控制、会话管理、高效组织和推进开发任务
- **扩展篇**：通过 plugin、skill、automation、mobile 等功能扩展能力边界

---

## 一、安装与登录

### 1.1 下载安装
- 访问 Codex 官网，点击下载按钮
- macOS 用户：直接将 Codex 拖入 applications 文件夹即可完成安装

### 1.2 登录方式
登录提供两种选项：

**方式一：使用 ChatGPT 账号登录**
- 需要订阅 ChatGPT 套餐
- 套餐选择（从左到右价格递增，Codex 额度递增）：
  - **免费版**：额度少得可怜，只能勉强试水
  - **Go 套餐**：与免费版额度差不多
  - **Plus 套餐**：额度明显上升（**推荐**）
  - **Pro 套餐**：额度更多
- **建议**：先订阅 **Plus Plan**（20 美元/月），可用量比较适中

**方式二：使用 API Key 登录（Sign in another way）**
- 需要输入 OpenAI 的 API Key
- 需要海外信用卡，门槛较高
- **不推荐**：API 没有订阅套餐划算

### 1.3 初始化设置
首次启动时会询问：
1. 工作类型选择（按实际情况选择）
2. 是否导入 Claude Code 和 Cursor 相关配置（建议先跳过）
3. 是否试用 Codex 手机版（点击 Setup Later）

---

## 二、基础功能实战演示

### 2.1 项目创建与需求提交
- **新建项目目录**：在访达创建文件夹（例如"马克笔记"）
- **关联项目**：点击 `Work in the Project` → `Use an existing folder` → 选择文件夹
- **提交需求**：在输入框输入具体需求，例如：
  - 使用 HTML 写一个笔记软件
  - 软件界面分为左右两部分：左边笔记列表，右边笔记内容
  - 注意做好测试

### 2.2 权限请求机制
当 Codex 需要执行操作时，会弹出选项：
- **Yes**：本次同意执行
- **Yes, and don't ask again**：本次同意，且以后类似操作不再询问
- **输入框**：可告诉 Codex 希望的处理方式（例如只检查代码，不启动本地服务器）
- **Skip 按钮**：不同意且不说明原因（弱化的第四选项）

### 2.3 Annotate（标注功能）
- 点击 **annotate 图标**
- 直接在预览界面选中需要修改的区域
- 输入修改意见（例如"去掉"）
- 提交请求：包含对应的截图 + 具体要求
- **优势**：比文字描述更准确、方便

### 2.4 界面控制技巧
- **收起左侧栏**：点击特定按钮，左侧区域被收起，预览空间更大
- **隐藏下方 Composer**：点击三个点 → 选择 `Hide Composer`
- **重新展开**：再次点击对应按钮

### 2.5 预览区的限制（重要踩坑点）
- 点击"加号"添加笔记时无反应——**不是 bug**，是预览区安全限制
- Codex 右侧预览区禁止了 local storage（本地存储）等功能
- 在独立浏览器中打开则完全正常
- **建议**：做外部应用时，务必在独立浏览器中测试，不要被预览区骗了

---

## 三、权限配置（输入框下方）

三种权限选项：

### 3.1 Default Permissions（默认权限）
- 修改项目目录外文件或执行有风险命令时弹出提醒
- 必须用户点头同意才能继续
- **优点**：绝对安全，一切尽在掌握
- **缺点**：根本离不开人，必须随时授权

### 3.2 Auto Review（自动审查，推荐）
- 引入专门负责安全审查的 agent
- 安全的直接放行，危险的直接拒绝
- 只有少数 agent 拿不定主意的情况才弹窗让用户决定
- **优势**：效率与安全之间平衡最好

### 3.3 Full Access（完全访问）
- 放飞自我模式，全部自动同意
- Codex 想干嘛就干嘛，完全不需要用户插手
- **风险**：无任何安全校验，误删数据拦也拦不住
- **警告**：开启前一定要三思

---

## 四、模型与参数配置

### 4.1 思考深度
- 输入框旁边显示 `5.5 medium` 表示使用 GPT 5.5 模型，思考深度为 medium
- **四个级别**：low、medium、high、extra high
- 思考深度越高：耗时越长、token 消耗越多、代码质量通常越好

### 4.2 模型切换
- 下拉列表中可选择 GPT 5.5、GPT 5.4 等多个模型
- 根据具体任务难度灵活选择

### 4.3 输出速度
- **Standard**（标准）：默认模式
- **Fast**（快速）：生成速度提升至原来的 **1.5 倍**
  - 代价：token 消耗量增加
  - GPT 5.5 模型下，fast 模式的 token 消耗是标准模式的 **2 倍**
- 适合 token 充足、追求效率的场景

---

## 五、Git 版本控制

### 5.1 终端快捷键
- 按下 `Command + J` 弹出/隐藏右侧终端面板
- 双手不离键盘，操作丝滑

### 5.2 Git 基本工作流
防止新加功能时把代码搞乱，先用 Git 保存当前版本：
```bash
git init      # 初始化仓库
git add .     # 添加到暂存区
git commit    # 提交第一次修改
```

### 5.3 Codex 内置的 Git 操作
- 点击 **environment 区域** → **changes 按钮** → 选择 **unstaged**
- 显示所有未提交的代码改动（Codex 刚才的修改）
- **评论功能**：点击行旁的加号 → 输入要求 → 点击 `comment` 让 Codex 修改
- **直接提交**：点击 `commit` 按钮 → 输入 commit message → 点击 `continue`

### 5.4 撤销上次消息（重要技巧）
- 场景：上一个消息无意义或不需要（例如排查了一个不是问题的问题）
- 点击消息旁的 **编辑按钮** → 直接修改消息 → 提交
- **限制**：只能编辑**最后一条消息**，更靠前的消息不支持编辑
- 原来排查问题的消息消失后：不再占用模型上下文，也不会影响后续执行

---

## 六、对话管理（Fork / Archive）

### 6.1 Fork 功能
**Fork 的含义**：基于当前会话复制一个新会话，新会话只到所选消息为止，后面的消息全不保留。

#### 6.1.1 Fork into Local
- 继续使用当前目录作为新会话代码存放地址
- **特性**：只会处理会话内容，**不会回滚代码**
- 配合 Git 使用：先 Fork 会话，再用 `git checkout <commit-hash>` 回滚代码
- 实现"会话和代码同时回滚"

#### 6.1.2 Fork into New Worktree
- 创建一个新的目录存放新会话代码
- 基于 **Git Worktree** 实现
- **特性**：新老会话所处理的代码**不是一份**，彼此互不影响
- 适合两个会话分别处理不同功能点，最后合并

#### 6.1.3 Fork 总结
| 特性 | Fork into Local | Fork into New Worktree |
|------|----------------|----------------------|
| 复制会话到所选消息 | ✓ | ✓ |
| 回滚代码 | ✗ | ✗（只复制代码到新目录） |
| 代码存放位置 | 原目录 | 新建隔离目录 |

### 6.2 Archive（归档）
- 点击会话旁的图标 → 点击 `confirm` 归档
- **归档 vs 删除的区别**：
  - **归档**：暂时隐藏，可恢复
  - **删除**：彻底消失
- **恢复归档**：按 `Command + ,` 打开设置面板 → 点击 `Archive chats` → 解除归档状态或彻底删除

---

## 七、AGENTS.md 配置

### 7.1 作用
- 放在项目根目录的**配置文件**
- Codex 开始新会话时自动读取，把内容当成对自己的指令执行
- 实现**跨会话的规则配置**

### 7.2 使用示例
让 Codex 每次写完代码自动提交 Git commit：
1. 使用 VSCode 打开项目目录
2. 在根目录创建 `agents.md`
3. 写入："每次完成代码修改后，都需要提交一次 Git commit"

### 7.3 可配置内容
- 代码风格
- 命名规范
- 技术栈要求
- 项目背景介绍
- 任何希望 Codex 遵守的规则

### 7.4 注意事项
- Codex 只提交**当前需求所对应的代码改动**
- 初始创建的 `agents.md` 不属于当前需求，需要手动提交

---

## 八、Plan Mode（计划模式）

### 8.1 适用场景
处理大工程时，先让 Codex 做规划，确认规划无误后再动工。

### 8.2 使用方法
- 点击输入框旁的 **加号** → 选择 **Plan Mode**
- Codex 进入计划模式，先做计划再写代码
- 计划完成后给出两个选项：
  - **直接同意**：按计划开始实现
  - **提出修改要求**：输入修改意见，Codex 根据修改出新的计划

### 8.3 实战演示
将 HTML 网页改造为桌面客户端（Electron + React + TypeScript）：
- Codex 会先询问关键问题（如数据存放位置、交付标准）
- 给出详细的计划（包含测试方案、架构设计）
- 用户确认后开始实现

---

## 九、Side Chat（侧边对话）

### 9.1 功能
- 在 Codex 执行任务的过程中，使用 `-side` 打开 side chat
- 在里面随便问 Codex 别的问题

### 9.2 重要特点
- 不会影响左侧主任务的执行
- 允许用户在 Codex 工作时问一些轻量级问题
- 两个任务互不干扰

---

## 十、Steer 功能

### 10.1 问题场景
默认情况下，只有上一个请求完成后 Codex 才会处理下一个请求。但如果新需求需要在原任务中途介入（例如：发现 logo 需要在深浅模式下都清晰可见，但 logo 已经在生成中）：

### 10.2 解决方法
- 点击输入框旁的 **Steer 按钮**
- 请求会**立即发送**给 Codex
- 让 Codex 在生成前就注意到新增要求

---

## 十一、Plugin（插件）

### 11.1 插件概念
- Plugin 是 Codex 的"外挂"，扩展 Codex 的能力
- 可在侧边栏 `Plugins` 中查看所有可用插件

### 11.2 Plugin 的组成部分
Plugin 通常由两类组件构成：
- **App（应用）**：提供多个工具（在 Codex 中称为 **Action**），本质与 MCP 工具类似
- **Skill（技能）**：给大模型看的说明文档，规定如何使用工具

### 11.3 实战示例 - Gmail Plugin
包含：
- **1 个 App**：提供 24 个工具（如 apply labels to emails、archive emails）
- **2 个 Skill**：
  - gmail skill：总结邮件内容、撰写回复、何时使用哪些工具
  - inbox triage skill：邮件归类、判断紧急程度

### 11.4 实用插件推荐

#### Chrome 插件
- 安装步骤：点击 chrome 旁边的加号 → `Install Chrome` → 同时在 Chrome 上安装对应扩展
- 使用方式：
  - 点击插件旁的按钮直接开启会话
  - 修改提示词为具体需求（例如：打开 product hunt 首页，找出今天最热门的三个新发布的产品，总结特点并附上访问链接）
- **特点**：Codex 会创建标签组专门解决问题，独立操作浏览器

#### Computer Use 插件
- 用来控制电脑，操作各种桌面应用
- 安装步骤：点击加号安装
- 使用方式：点击 `Computer Use` 旁的小图标开启会话
- **重要特性**：使用**独立的虚拟鼠标**，与用户的鼠标互不干扰
  - 用户完全可以让 Codex 在后台默默干活，自己继续上网、看视频
- 实战示例：让 Codex 打开日历应用，创建 5月28日 10:00 的日程

### 11.5 指定使用某个插件
在任务最前面输入 `@` 符号，然后敲入插件名称回车：
```
@presentations 给这个笔记软件做一个 PPT...
```
不过不加也没关系，Codex 会自动找到合适的插件。

---

## 十二、Skill（技能）

### 12.1 Skill 概念
- 给大模型看的**说明文档**
- 详细说明如何完成某类任务、何时使用哪些工具

### 12.2 浏览 Skill
- 打开 `Plugins` → 点击 `Skills` 查看可用 skill 列表
- 安装 plugin 时相关的 skill 会被一并安装

### 12.3 特色 Skill - ImageGen
- 用于生成图片的"王牌级"skill
- 利用 GPT 的生图能力（美观且真实）

#### 使用示例：生成宣传海报
1. 新建会话，输入需求："给笔记软件生成一个宣传海报图片，注意要使用真实的软件截图"
2. **附加截图的方法**：
   - **方法一**：点击加号 → `Attach Electron`（Codex 中将笔记软件识别为 Electron）
   - **方法二（更方便）**：按**左右 Command 键同时按下**，自动把当前窗口截图传给 Codex
3. Codex 会使用 imagegen skill 来制作海报

### 12.4 创建自定义 Skill
让 Codex 自己创建项目专属 skill：
- 新建会话 → 输入任务："写一个代码审核 skill，专门给当前的项目使用"
- 生成的 skill 命名为 `marknotes code review`
- 新建会话时 `@` 引用该 skill 即可使用

---

## 十三、Automation（自动化任务）

### 13.1 适用场景
定期执行重复性任务（例如每天定时检查项目代码是否有问题）。

### 13.2 创建步骤
1. 点击界面中的三个点 → `Add Automation`
2. 配置以下参数：
   - **标题**：codex 自动填好
   - **任务描述**：定时任务启动时发给 Codex 的要求
   - **执行环境**：
     - **Local**：在某个项目目录里运行
     - **Worktree**：基于项目目录创建新 worktree 后运行
     - **Chats**：不绑定任何项目目录（之前用 Chrome plugin 搜索时使用的就是这种）
   - **项目目录**：选择 local 时需绑定（如马克笔记）
   - **运行频率**：Daily / 其他
   - **运行时间**：例如每天 9:00
   - **模型与推理强度**：例如 GPT 5.5 + medium

### 13.3 查看与管理
- 在左侧栏的 `Automations` 中查看已创建的定时任务
- 点击试运行按钮可立即执行
- 每次运行都会创建一个新会话用于执行任务

---

## 十四、Codex Mobile（手机端）

### 14.1 功能
通过手机远程操控电脑端的 Codex，让电脑完成任务。

### 14.2 配对步骤
1. 电脑端点击 `Codex Mobile` → `Get Started` → `Allow`（允许手机操纵电脑）→ `Done`
2. 显示二维码（如果未显示，点击手机图标）
3. 用手机摄像头扫描二维码，跳转到 ChatGPT 的 Codex 页面
4. 即可在手机端向电脑端 Codex 发送指令

### 14.3 使用示例
从手机端发送指令让 Codex 删除日历中的某条日程：
- 手机端点击聊天 → 选择 `Computer Use`
- 输入具体请求
- **注意**：如果请求与当前项目无关，需点设置按钮选择"不使用项目"
- 电脑端弹窗确认后，Codex 开始操作电脑完成任务

### 14.4 优势
- 在外面也能使用 Codex 完成各种任务
- 灵活方便

---

## 十五、关键总结

### 15.1 推荐配置组合
- **权限模式**：Auto Review（效率与安全的平衡）
- **订阅方案**：ChatGPT Plus（20 美元/月）
- **代码管理**：配合 Git + `agents.md` 配置文件

### 15.2 重要操作清单
- 提交需求前先 `Command + J` 打开终端初始化 Git
- 使用 **Annotate** 精准定位界面修改区域
- 无意义的消息使用**编辑按钮**删除
- 大工程先用 **Plan Mode** 规划
- 工作中途介入新需求用 **Steer** 按钮
- 跨会话规则写在 `agents.md`
- 多个独立任务用 **Fork into New Worktree** 隔离

### 15.3 注意事项
- 预览区有安全限制，正式测试要在独立浏览器中进行
- Full Access 模式风险极高，慎用
- Fork 功能不回滚代码，需配合 Git 使用
- Archive 和删除有区别，归档可恢复