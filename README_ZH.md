<!--
Licensed to the Apache Software Foundation (ASF) under one
or more contributor license agreements.  See the NOTICE file
distributed with this work for additional information
regarding copyright ownership.  The ASF licenses this file
to you under the Apache License, Version 2.0 (the
"License"); you may not use this file except in compliance
with the License.  You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing,
software distributed under the License is distributed on an
"AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
KIND, either express or implied.  See the License for the
specific language governing permissions and limitations
under the License.
-->

# OFBiz Agent Skills 插件

## 总体目标

`ai-agent-skills` 插件是一个标准化知识库，汇集了 Apache OFBiz 的最佳实践与实现模式。其核心目的是赋能 AI Agent（如 Antigravity）高精度地执行复杂的 OFBiz 开发任务——例如创建实体、定义服务、构建界面以及管理业务逻辑——同时严格遵循框架特定的操作规范。

通过以结构化格式提供这些"技能"，我们确保 Agent 能够自动遵循正确的设计模式（例如，优先使用 View Entity 而非手动遍历、正确使用 Worker 类、遵循安全标准），而无需在每一步都进行人工干预。

## 版本兼容性

这些技能在 Apache OFBiz `trunk` 版本上效果最佳，相关指南会首先在该分支中维护和更新。

如果在旧版本发布分支或经过定制的代码库中使用，请在直接应用指南之前，先验证辅助类的可用性、服务契约以及框架行为是否一致。

## Agent 配置与激活

为了让 AI Agent（如 Antigravity、Cursor 或 GitHub Copilot）能够高效使用这些技能，需要将它们链接或汇总到 Agent 在工作区根目录下所期望的特定目录中。

### 1. 框架位置（插件）

将技能源码存放在 OFBiz 插件目录中，以便随项目一同进行版本控制：
`~/ofbiz-framework/plugins/ai-agent-skills/`

### 2. 通过 Gradle 进行同步

要让这些技能对特定的 AI Agent 可用并完成格式配置，请从 OFBiz 根目录运行自动化 Gradle 同步任务。

```bash
# 进入 OFBiz 框架根目录
cd ~/ofbiz-framework

# 方案一：同步到默认的通用 Agent 目录（.agents/skills）
./gradlew syncAgentSkills
```

### 更新技能

如果修改或新增了 `plugins/ai-agent-skills` 目录下的任何内容，需要重新运行同步命令才能使变更在 AI Agent 中生效：

```bash
./gradlew syncAgentSkills
```

该命令会将结构化文件重新复制到 `.agents/` 文件夹中（默认行为）。

```bash
# 方案二：使用 -Pagent 参数单独指定同步目标
./gradlew syncAgentSkills -Pagent=agents    # 复制到 .agents/skills/
./gradlew syncAgentSkills -Pagent=gemini    # 复制到 .gemini/skills/
./gradlew syncAgentSkills -Pagent=claude    # 复制到 .claude/skills/
./gradlew syncAgentSkills -Pagent=github    # 复制到 .github/skills/
./gradlew syncAgentSkills -Pagent=cursor    # 复制到 .cursor/skills/

# 也可以使用 "all" 将技能同时复制到所有支持的 Agent 目录：
./gradlew syncAgentSkills -Pagent=all

# 或者显式指定多个 Agent 进行选择性同步：
./gradlew syncAgentSkills -Pagent=claude,github
```

通过使用这些任务，当插件中的技能更新后，您的 Agent 会自动在本地继承这些更新，无需手动干预。

## 与 Agent 的配合方式

一旦完成同步，Agent 在 OFBiz 项目目录下工作时会自动发现这些技能。

### 集成模式

- **通用 Agent**：将其指向 `.agents/skills` 目录。
- **Gemini (Antigravity)**：自动从 `.gemini/skills/` 读取。
- **Claude**：自动从 `.claude/skills/` 读取上下文。
- **Cursor**：自动从 `.cursor/skills/` 读取上下文。
- **GitHub Copilot**：自动从 `.github/skills/` 载入能力。

## 目录结构

这些技能的主源文件应放置在 OFBiz 框架的 `plugins` 目录下：
`/path/to/ofbiz/plugins/ai-agent-skills/`

每个子目录包含：

- `SKILL.md`：核心知识文件，涵盖该技能的目标、流程和操作规范。

## 可用技能列表

关于所有技能的详细列表及简要说明，请参阅 [SKILLS\_SUMMARY\_ZH.md](SKILLS_SUMMARY_ZH.md)。

当前工具集覆盖：

- **核心抽象**：`manage-entities`、`manage-services`、`manage-data`。
- **UI 与交互**：`manage-screens`、`manage-forms`、`manage-menus`、`manage-templates`、`manage-ajax`。
- **逻辑与流程**：`manage-groovy`、`manage-java`、`manage-java-patterns`、`manage-eca`、`manage-service-groups`。
- **集成**：`manage-api-integration`、`manage-email-services`。
- **高级管理**：`manage-security-advanced`、`manage-localization-advanced`、`manage-webapps`、`manage-cache-and-performance`。
- **策略**：`manage-strategies`（Xml vs Java/Groovy、注意事项）。
- **质量门禁**：`prepush-readiness`（Pre-push 钩子——Checkstyle、CodeNarc——以及编译、XML 校验和针对性测试）。
- **贡献工作流**：`manage-contribution-workflow`（worktree 设置、framework/plugins 仓库配对、预测试数据加载、反向移植以及 PR 模板）。

## 部署与更新

本插件已关联 GitHub 仓库。要更新 Agent 可用的技能，请拉取仓库的最新变更。
