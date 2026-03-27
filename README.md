# 1. 简介

## 1.1 资源地址

OpenCode 是一个开源的 AI 编码工具。它提供终端界面、桌面应用和 IDE 扩展等多种使用方式。

- 文档地址：https://opencode.ai/docs/zh-cn
- 项目地址：https://github.com/anomalyco/opencode

## 1.2 OpenCode / ClaudeCode 对比

两者都是顶级的终端 AI 编程助手，但底层哲学和适用人群截然不同，核心对比如下：

| 特性维度       | OpenCode                                                     | Claude Code                                                  |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **开源模式**   | 100% 开源（MIT License），拥有超过 450 + 贡献者，社区驱动    | 闭源商业产品，代码由 Anthropic 内部团队掌握                  |
| **大语言模型** | 模型无关：可连接 75 + 家提供商，如 OpenAI、Google、DeepSeek、甚至本地模型 | 深度绑定 Anthropic 的 Claude 系列模型，是 Claude 能力在终端的最佳体现 |
| **核心理念**   | 灵活性与掌控，开发者拥有绝对的控制权，可自由选择、切换、组合模型，构建自己的工具链 | 集成与流畅，追求与 Claude 生态的完美结合，提供开箱即用、无缝衔接的可靠体验 |
| **定制化程度** | 极高，所有 Agent 行为、工具权限都可通过 Markdown 和 YAML 文件配置，甚至可创建全新 Agent | 有限，可通过 CLAUDE.md 添加指令，但核心系统提示词（近 3000 tokens）无法修改 |
| **交互与架构** | 交互性更强，支持 Tab 键快速切换 Agent，@提及子 Agent，提供 HTTP API 远程控制 | 子 Agent 系统成熟，内置原生、高可靠性的 Plan/Explore/Task Agent，以及独特的 “双 Esc 键回滚” 功能 |
| **工具生态**   | 声明式 MCP 加载，可基于每个 Agent 精细控制 MCP 工具的启用 / 禁用，避免上下文膨胀 | 工具集成度高，内置 20 多种工具，原生支持 Jupyter Notebook，MCP 工具启动时全部加载 |
| **成本与门槛** | 工具免费，仅需支付所选模型提供商的 API 费用，可选择高性价比或免费模型 | 需要订阅，必须拥有 Claude Pro/Max/Team 等订阅，成本相对固定且较高 |

## 1.3 为什么选 OpenCode

将 OpenCode 作为国内开发者的首选，并非单纯的技术对比，而是基于地缘政治风险和开发自主性的现实考量：

1. **首要原因：无法回避的 “断供” 风险**

   

   2025 年 9 月，Anthropic 发布强硬声明，禁止由中国资本控股的集团及其附属公司使用其所有 AI 服务（包括 Claude 模型和 Claude Code）。这意味着无论身处国内还是海外，只要公司背景沾边，都可能无法使用。大量国内开发者和创业公司因此账号被封，日常工作流被迫中断。这种随时可能被 “卡脖子” 的不确定性，是 Claude Code 在国内无法被稳定推荐的根本原因。

2. **OpenCode 的天然优势：自主可控，拥抱国产**

   - **无惧封锁**：OpenCode 本身是开源工具，不存在被单一公司远程封禁的可能。
   - **完美适配国产模型**：OpenCode 的 “模型无关” 特性，使其可以无缝对接智谱 GLM-4.7、阿里 Qwen-Coder、DeepSeek 等飞速进步的国产大模型。这些模型在编码能力上与 Claude 的差距正迅速缩小，且对中文理解更深、服务更稳定。
   - **数据隐私与合规**：对于企业和隐私敏感项目，OpenCode 可配合本地模型（如通过 Ollama）实现完全离线、私有化部署，所有代码数据不出本地，彻底满足合规要求。

   

3. **社区与生态的崛起**

   

   国内的开发者社区正在积极拥抱 OpenCode。例如，Oh-My-OpenCode 插件为其提供了强大的多智能体编排能力。围绕国产模型的工具链和服务也日益成熟，七牛云等厂商甚至提供预置 OpenCode 镜像的一键部署服务。一个多元化、开放化、本土化的 AI 编程生态系统正在形成，在这个新生态里，OpenCode 正扮演着连接者的关键角色。

# 2. 安装

官方安装文档：https://opencode.ai/zh/download

## 2.1 推荐安装

- **Windows**：

  请提前准备 node 环境：https://nodejs.org/zh-cn

  ```
  npm install -g opencode-ai
  ```

- **Linux**：

  ```
  curl -fsSL https://opencode.ai/install | bash
  ```

- **Mac**：

  请提前准备好 brew 环境

  ```
  brew install anomalyco/tap/opencode
  ```

- **Docker**：

  ```
  docker run -it --rm ghcr.io/anomalyco/opencode
  ```

 📌 **推荐：使用 WSL**
	为了在 Windows 上获得最佳体验，推荐使用 [WSL 相关方案](https://opencode.ai/docs/windows-wsl)。它提供更好的性能。

## 2.2 安装验证

在终端中执行以下命令来验证 OpenCode 是否安装成功：

```
opencode
```

<img width="1263" height="663" alt="image" src="https://github.com/user-attachments/assets/a86b88cb-e430-4b05-b647-cf4cc1bf2f64" />


## 2.3 IDE 插件

OpenCode 对 VS Code 系列的插件支持友好。

在 VS Code 扩展商店中搜索 `opencode`，找到并安装 **opencode for VS Code** 插件（由 SST 发布）。

<img width="1265" height="689" alt="image" src="https://github.com/user-attachments/assets/650e156c-efba-4115-9bd1-75700b275fe3" />


开启方式

```
# 开启
使用: ctrl + shift + p
输入: open opencode
```

## 2.4 配置文件

**配置加载顺序**

配置源按以下顺序加载（后面的源会覆盖前面的源）：

1. 远程配置（来自 .well-known/opencode） - 组织默认值
2. **全局配置（~/.config/opencode/opencode.json） - 用户偏好**
3. 自定义配置（OPENCODE_CONFIG 环境变量） - 自定义覆盖
4. **项目配置（项目中的 opencode.json） - 项目特定设置**
5. .opencode 目录 - 代理、命令、插件
6. 内联配置（OPENCODE_CONFIG_CONTENT 环境变量） - 运行时覆盖

**注意事项**

1. 配置文件是**合并**在一起的，而非直接替换
2. .opencode 和～/.config/opencode 目录的子目录使用复数名称：`agents/`、`commands/`、`modes/`、`plugins/`、`skills/`、`tools/` 和 `themes/`。为向后兼容，也支持单数名称（例如 `agent/`）。

# 3. 快速上手

## 3.1 命令概览

官方命令文档：https://opencode.ai/docs/tui#commands

界面说明：

<img width="1269" height="555" alt="image" src="https://github.com/user-attachments/assets/21609870-f57e-4fbe-bfd9-dc39cd1c1295" />


- **指令集**：以 `/` 开头的命令，如 `/agents`（切换智能体）、`/compact`（精简会话）、`/connect`（连接模型提供商）、`/copy`（复制会话记录）、`/editor`（打开编辑器）、`/exit`（退出应用）、`/export`（导出会话记录）、`/fork`（从消息分叉）、`/help`（查看帮助）、`/init`（创建 / 更新 AGENTS.md）等。
- **模式**：当前工作模式（如 Plan）。
- **使用的模型**：当前绑定的模型（如 MiniMax M2.5 Free OpenCode Zen）。

------

### 3.1.1 基本操作

|          操作           |   方式    |
| :---------------------: | :-------: |
|      **引用文件**       | `@文件名` |
|   **执行 Shell 命令**   |  `!命令`  |
| **切换计划 / 构建模式** | `Tab` 键  |
|       快捷键前缀        | `Ctrl+x`  |

### 3.1.2 OpenCode 内部命令清单

|    命令     |           描述            |                        备注                        |
| :---------: | :-----------------------: | :------------------------------------------------: |
|   `/help`   |      显示帮助对话框       |                         -                          |
| **`/init`** | 创建或更新 AGENTS.md 文件 | 默认有可能英文，可以要求它使用简体中文重新生成一下 |
| **`/undo`** | 撤销上一条消息及文件更改  |                         -                          |
| **`/redo`** |     重做已撤销的消息      |                         -                          |
|  `/share`   |       分享当前会话        |                         -                          |
| `/unshare`  |     取消分享当前会话      |                         -                          |
| `/connect`  |      添加 LLM 提供商      |                         -                          |
|  `/models`  |       列出可用模型        |                         -                          |
|   `/new`    |        开始新会话         |                      `/clear`                      |
| `/sessions` |      列出并切换会话       |               `/resume`, `/continue`               |
| `/compact`  |       压缩当前会话        |                    `/summarize`                    |
| `/details`  |   切换工具执行详情显示    |                         -                          |
|  `/editor`  |  打开外部编辑器编写消息   |                         -                          |
|  `/export`  |    导出会话为 Markdown    |                         -                          |
|  `/themes`  |       列出可用主题        |                         -                          |
| `/thinking` | 切换思考 / 推理块的可见性 |                         -                          |
|   `/exit`   |       退出 OpenCode       |                   `/quit`, `/q`                    |

## 3.2 打开项目

OpenCode 需要在某一个目录中作为根来执行后续操作，这个目录称之为：**工作目录**

有两种方式来确定工作目录：

1. 在项目目录下，直接执行 `opencode`
2. 执行 `opencode 项目目录`

------

⚠️ 注意事项：

一旦打开一个目录后，OpenCode 不支持在命令行里切换工作空间，没有 `cd` 之类的命令。

- 验证方式：用 `!ls` 查看目录，执行 `!cd` 切换后，再次执行 `!ls`，会发现目录切换无效。

## 3.3 基本操作

### 3.3.1 编辑模式

- **plan 模式（规划模式）**

  定位为 “思考者” 或 “架构师”，核心职责是分析代码、制定实施方案，**无任何文件修改或命令执行权限**，安全性极高。

  - 交互示例：会先列出待确认问题（如 “是否保留现有 MyBatis 配置”“是否保留 Entity 类中的验证注解”），并询问 “是否按此计划执行？”

- **build 模式（构建模式）**

  定位为 “执行者” 或 “工程师”，拥有完整的读写与执行权限，会根据 plan 模式确定的方案，**实际完成代码编写、文件修改和命令运行**。

  - 交互示例：会以 Todo 列表形式展示待办（如 “移除 pom.xml 中 spring-boot-starter-data-jpa 依赖”“修改 Entity 类，移除 JPA 注解”），并逐步执行编辑操作。

### 3.3.2 应用案例

- 分别在 `plan` 模式和 `build` 模式下，输入指令：**为我生成一个 readme.md 文件**
- 对比查看两种模式的不同反馈结果

------

### 3.3.3 其他操作

- **执行 shell 命令**：可以直接执行 shell 命令来完成高效的系统操作
- **引用文件**：可以引用指定文件并对其进行处理

## 3.4 供应商 / 模型 (connect/models)

### 3.4.1 直接使用提供的厂商

通过 `/connect` 命令可连接不同 LLM 提供商，可选的热门厂商包括：

- **OpenCode Zen (Recommended)**：推荐选项
- **OpenAI**：支持 ChatGPT Plus/Pro 或 API Key
- **GitHub Copilot**
- **OpenCode Go (Low cost)**：低成本选项
- **Anthropic**：支持 Claude Max 或 API Key
- **Google**
- 其他（Other）

### 3.4.2 列表中没有的供应商

查看apikey配置

```
echo %LONG_CAT_API_KEY%
```

可以通过 **OpenAI 通用适配器** 来接入列表外的供应商，配置示例如下：

```json
{
  "$schema": "https://opencode.ai/config.json",
  "provider": {
    "my-custom-provider": {
      // 自定义ID，可以任意取名
      "npm": "@ai-sdk/openai-compatible",
      // 使用OpenAI兼容适配器
      "name": "my-custom-provider",
      // 显示在UI中的名称
      "options": {
        "baseURL": "https://api.longcat.chat/openai",
        // 供应商的API地址
        "apiKey": "{env:LONG_CAT_API_KEY}",
        // 从环境变量读取，更安全
        "headers": {
          // 可选：自定义请求头
          "X-Custom-Header": "value"
        }
      },
      "models": {
        "LongCat-Flash-Chat": {"name": "LongCat-Flash-Chat"},
        // key是模型ID，name是显示名
        "LongCat-Flash-Thinking": {"name": "LongCat-Flash-Thinking"}
      }
    },
  }
}
```

**特殊厂商适配配置**

```json
{
  "provider": {
    "my-anthropic": {
      "npm": "@ai-sdk/anthropic", // Anthropic专用适配器
      "name": "我的Claude",
      "options": {
        "baseURL": "https://api.anthropic.com/v1", // 可自定义端点
        "apiKey": "{env:ANTHROPIC_API_KEY}"
      },
      "models": {
        "claude-3-sonnet": { "name": "Claude 3 Sonnet" }
      }
    },
    "my-gemini": {
      "npm": "@ai-sdk/google", // Google Gemini专用适配器
      "name": "我的Gemini",
      "options": {
        "baseURL": "https://generativelanguage.googleapis.com/v1beta",
        "apiKey": "{env:GEMINI_API_KEY}"
      },
      "models": {
        "gemini-pro": { "name": "Gemini Pro" }
      }
    }
  }
}
```

**方式二：命令行直接配置**

通过以下命令可直接在命令行配置 OpenCode（等价于自动修改配置文件）：

```
ollama launch opencode --model qwen3-coder:30b
```

## 3.5 开发规范 (init)

### 3.5.1 命令详解

在项目目录中初始化 OpenCode，这是启动新项目的标准步骤：

- 执行 `/init` 命令后，会自动生成 **AGENTS.md** 文件
- 该文件相当于项目的 “说明书”，可写入自定义指令，让 AI 理解项目的特殊规则、架构或约定
- 后续所有对话都会参考此文件内容

------

### 3.5.2 应用案例

场景：刚克隆新代码仓库，希望 AI 遵循仓库代码规范

1. 在项目根目录运行 `opencode`，进入 TUI 界面

2. 输入 `/init` 并回车

3. OpenCode 会在后台创建 **AGENTS.md** 文件

4. 用编辑器打开 AGENTS.md，写入规则：

   > 本项目生成的代码必须在方法上加注释，并定义作者为：潜心。

   

5. 后续让 AI 生成代码时，它会自动遵循该规则

6. 执行命令示例：`给OrderService生成注释`

# 3.6 基本编辑 (undo/redo)

## 3.6.1 命令详解

`/undo` 和 `/redo` 用于撤销或重做上一步操作：

- 在 OpenCode 中，AI 有时会批量修改多个文件
- 若对 AI 刚执行的修改不满意，可使用 `/undo` 一键回退到修改前状态
- 若反悔回退操作，可使用 `/redo` 恢复之前的修改

------

## 3.6.2 应用案例

操作步骤（配合 VS Code 观察文件变化）：

1. 执行命令：`给OrderService生成注释`
2. 执行 `/undo`，同时在 VS Code 中对比文件内容，会发现内容立刻回滚
3. 执行 `/redo`，观察 VS Code 中文件内容，之前的修改会被恢复

# 3.7 会话管理 (sessions/new)

## 3.7.1 命令详解

在 TUI 界面输入 `/sessions`，可以列出所有历史对话会话并快速切换。

- **会话**：OpenCode 中最核心的工作单元，代表一个完整的 AI 对话线程，包含所有交互历史、文件修改和成本统计。
- 别名：`/resume`、`/continue` 也可用于切换会话。
- 新建会话：使用 `/new`（别名 `/clear`）创建新的独立会话。

------

## 3.7.2 应用案例

场景：执行一个任务，需要切换另一个操作，且不希望互相干扰。

1. 输入 `/new` 创建新会话 B
2. 在新会话中添加另一个文件的注释
3. 完成后，输入 `/sessions`
4. 切换不同会话，执行 `/undo` 等操作，彼此互不干扰

# 3.8 skills 调用

## 3.8.1 skills 简介

- **起源**：Skills 最早诞生于 Anthropic 的 Claude Code 生态，后被作为独立开放标准发布，被主流 AI 编程工具（包括 OpenCode）广泛采用。

- **目录演进**：OpenCode 最初使用单数 `skill` 作为技能目录名称，后演进为 `skills`，同时兼容 `skill` 目录。

- **定义**：一个 Skill 是一份特殊的 Markdown 文件，**必须命名为 `SKILL.md`**，通过固定格式告诉 AI 如何完成特定任务，例如：

  - 执行项目代码检查
  - 生成符合标准的文档
  - 编写特定类型的测试用例

  

- **参考链接**：`https://www.bilibili.com/video/BV1ahFmzqE9z`

## 3.8.2 OpenCode 技能（Skill）搜索规则

OpenCode 会在以下路径自动搜索并加载 Skill：

- **项目专用**：

  ```
  .opencode/skills/<技能名称>/SKILL.md
  ```

  仅对当前项目生效，适合项目专属任务。

- **全局共享**：

  ```
  ~/.config/opencode/skills/<技能名称>/SKILL.md
  ```

  对所有项目生效，适合通用技能（如代码检查、文档生成）。

- **兼容 Claude**：

  同时支持 Claude 生态的路径，方便迁移已有技能：

  ```
  .claude/skills/
  .agents/skills/
  ```

------

### 路径说明

- `~` 代表用户主目录：
  - Windows：`C:\Users\你的用户名\`
  - Linux/macOS：`/home/你的用户名/` 或 `/Users/你的用户名/`
- 每个 Skill 必须放在以**技能名称命名**的子目录下，且文件名为 `SKILL.md`（大写）。

# 3.9 mcp

## 3.9.1 mcp 简介

**MCP (Model Context Protocol，模型上下文协议)** 是 Anthropic 公司在 2024 年底开源的一项开放标准协议，可理解为 **AI 世界的 “USB-C 接口”**，用于让模型连接外部工具与服务。

------

## 3.9.2 应用案例

- 操作：修改 OpenCode 配置文件，添加高德（amap）MCP 服务
- 备注：高德服务需要 API Key，申请入口：`https://console.amap.com/dev/key/app`

**配置示例（部分）：**

```json
{
  "$schema": "https://opencode.ai/config.json",
  "provider": {
    "ollama": {
      "name": "Ollama (local)",
      "npm": "@ai-sdk/openai-compatible",
      "options": {
        "baseURL": "http://127.0.0.1:11434/v1"
      },
      "models": {
        "qwen3-coder:30b": {
          "name": "qwen3-coder:30b",
          "_launch": true
        }
      }
    }
  },
  "mcp": {
    "amap": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-amap"
      ],
      "env": {
        "AMAP_API_KEY": "你的高德地图API Key"
      }
    }
  }
}
```
