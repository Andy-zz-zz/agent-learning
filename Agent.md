> 来源链接：/uploads/Agent.mp4

<think>
The user wants me to create structured notes from the video transcript about "Agent". The notes should be in Chinese, use Markdown formatting, and be concise while retaining key information. I need to avoid numbering that could be parsed as ordered lists, and handle mathematical formulas in LaTeX.

Let me organize the content:

1. Introduction - why agents are important (Jensen Huang says 2025 is the year of agents, Andrew Ng says agents is the most important research direction)
2. What is an agent - comparison with non-agent LLM
3. Four types of agents (from Andrew Ng's keynote):
   - Reflection
   - Tool Use
   - Planning
   - Multi-agent Collaboration
4. Industry actions:
   - Google Astra Project
   - OpenAI (Operator, Sam Altman's tweet)
   - Anthropic
   - Microsoft
   - ByteDance (Coze)

Let me write this in a clean, structured Markdown format.
</think>
# Agent 知识笔记

## 一、Agent 的重要性

- **黄仁勋（Jensen Huang）**：2025 年是 Agent 元年，未来将是 AI Agent 的集群（swarms of AI agents）和网络（networks of AI agents）
- **吴恩达（Andrew Ng）**：Agent 是当下最重要的 AI 研究方向

---

## 二、Agent vs 普通 LLM

以"写文章"为例对比：

| 普通 LLM | Agent |
|---------|-------|
| 一次性输出结果 | 先列大纲 → 查资料 → 写初稿 → 反复自审修改 → 输出终稿 |
| 中途无法修改 | 可自主迭代优化 |
| 满意度较低 | 满意度大幅提升 |

**本质**：Agent 模拟了人类的工作流程，像"牛马"一样反复执行"写—改—改—改"的循环。

---

## 三、Agent 的四大设计模式（吴恩达 Keynote）

### 1\. Reflection（反思）

- **定义**：模型通过自我反思不断改进输出质量
- **示例**：设置"程序员"和"审查员"两个角色，审查员指出代码错误，程序员修改
- **适用场景**：复杂代码编写、复杂文档撰写、法律文件分析等高质量任务

### 2\. Tool Use（工具调用）

- **定义**：大模型调用外部工具完成自身无法处理的任务
- **工具类型**：计算器、知识库、数据库、搜索引擎、其他模型
- **核心优势**：
  - 突破模型能力限制
  - 减少 AI 幻觉，提升准确率
  - 将单一大脑扩展为多功能助手
- **典型应用**：ChatGPT Plus 插件商店（如 Speeh 文本转语音、找优惠码、查询课程、检查域名可用性等插件）

### 3\. Planning（规划）

- **定义**：面对复杂任务时，模型能像人一样拆解问题、制定步骤、逐步执行
- **示例**：从图片提取动作 → 生成新图片 → 转为文字 → 朗读出来
  - OpenPose（提取动作）→ Google（生成图片）→ Vito GPT-2（图片转文字）→ FastSpeech（文字转语音）

### 4\. Multi-Agent Collaboration（多智能体协作）

- **定义**：多个智能体在共同目标下分工协作完成任务
- **典型案例**：清华团队开发的 **ChatDev**（虚拟软件公司）
  - 角色：CEO、CTO、程序员、测试员等
  - 流程：设计 → 写代码 → 测试 → 文档协作
- **三大机制**：
  - 角色专业化：明确定义每个 Agent 的职责
  - 记忆流：保存所有对话记录，避免遗忘上下文
  - 自我反思：未达成共识前重新思考并调整

---

## 四、各大厂在 Agent 领域的布局

### Google

- **Project Astra**（2024.12.11 发布）：通用 AI 助手研究模型
  - 识别门锁密码、洗护标签、纸面文字
  - 充当旅行导游（识别历史建筑/雕塑）
  - 图书推荐、多语言交互
  - 已移植到智能眼镜
- **Agents 白皮书**（2025.1 发布）：探讨 Agent 概念、架构与应用

### OpenAI

- 2025.1.1 Sam Altman 公布年度计划，**Agent 排名第二位**
- 网友爆料将推出代号 **"Operator"** 的产品，让 Agent 直接操控电脑

### Anthropic

- 2024.10.23 公布**可操作计算机的模型**（Computer Use）
- 2024.12 发布博文《Building Effective Agents》

### 微软 & 字节跳动

- 微软积极布局 Agent 相关应用
- 字节跳动推出 **Coze** 平台布局 Agent

---

## 五、核心洞察

> Agent 让 AI 颠覆世界的轮廓逐渐清晰，科幻片中的未来场景正在成为现实。未来的方向是：**每个人都可能成为"老板"，手下拥有大量 AI 员工协同完成任务**。