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

# OFBiz Agent Skills：覆盖范围总览

本文档对 OFBiz Agent Toolkit 中开发的专项技能进行高层级概述。这些技能为 AI Agent 提供了必要的操作规范、设计模式和执行流程，使其能够高效地与 Apache OFBiz 框架进行交互。

## 🏗️ 核心抽象

| 技能 | 说明 |
| :--- | :--- |
| **[manage-entities](manage-entities/SKILL.md)** | 处理数据模型变更，包括实体定义、关联关系和主键。 |
| **[manage-services](manage-services/SKILL.md)** | 定义并实现 OFBiz 服务（Java、Groovy、Script），确保正确的属性和参数配置。 |
| **[manage-data](manage-data/SKILL.md)** | 使用 Entity Engine XML 工件管理 Seed、Demo 和 Setup 数据。 |
| **[manage-dynamic-view-entities](manage-dynamic-view-entities/SKILL.md)** | 动态创建高级 View Entity，以优化数据检索，避免使用原生 SQL。 |

## 🎨 UI 与交互

| 技能 | 说明 |
| :--- | :--- |
| **[manage-screens](manage-screens/SKILL.md)** | 使用 XML Screen 定义和装饰器构建复杂、可复用的 UI 布局。 |
| **[manage-forms](manage-forms/SKILL.md)** | 使用 OFBiz Form Widget 实现声明式的数据录入和展示表单。 |
| **[manage-menus](manage-menus/SKILL.md)** | 管理应用程序导航和菜单层级结构。 |
| **[manage-templates](manage-templates/SKILL.md)** | 使用 Apache FreeMarker (FTL) 和宏开发动态 UI 组件。 |
| **[manage-ajax](manage-ajax/SKILL.md)** | 使用 OFBiz 标准 AJAX 模式和事件处理实现无缝的 UI 刷新。 |
| **[manage-themes](manage-themes/SKILL.md)** | 处理视觉样式、CSS 集成以及主题特定属性。 |
| **[manage-labels](manage-labels/SKILL.md)** | 管理跨语言的国际化（i18n）和 UI 文本标签。 |
| **[manage-content](manage-content/SKILL.md)** | 操作 OFBiz 内容管理系统（DataResource、Content、ElectronicText）。 |
| **[manage-pdf-export](manage-pdf-export/SKILL.md)** | 使用 Apache FOP (PDF) 设计并实现专业文档（发票、标签等）。 |

## ⚙️ 逻辑与流程

| 技能 | 说明 |
| :--- | :--- |
| **[manage-groovy](manage-groovy/SKILL.md)** | 使用 Groovy 脚本编写业务逻辑，利用 `run-groovy` 引擎和 DSL。 |
| **[manage-java](manage-java/SKILL.md)** | 在 Java 源码层实现类型安全的业务逻辑和 Worker 类。 |
| **[manage-java-patterns](manage-java-patterns/SKILL.md)** | 遵循 OFBiz 特定的 Java 设计模式（如 Worker 类、内部服务调用）。 |
| **[manage-java-events](manage-java-events/SKILL.md)** | 实现 OFBiz Event（Web 边界层）并在 Java 中路由 HTTP 请求。 |
| **[manage-minilang](manage-minilang/SKILL.md)** | 维护传统 MiniLang（XML）逻辑，用于标准服务工作流。 |
| **[manage-eca](manage-eca/SKILL.md)** | 编排 Event Condition Action（Service ECA 和 Entity ECA）以实现自动化流程。 |
| **[manage-service-groups](manage-service-groups/SKILL.md)** | 定义并管理聚合服务执行和引擎级分组。 |
| **[manage-controller](manage-controller/SKILL.md)** | 在 `controller.xml` 中配置 Web 请求映射、安全约束和视图处理器。 |
| **[manage-async](manage-async/SKILL.md)** | 管理异步执行、定时任务以及 OFBiz 中的 JobSandbox。 |
| **[manage-quartz-jobs](manage-quartz-jobs/SKILL.md)** | 调度和管理后台任务、任务轮询及时间表达式。 |

## 🔌 集成与通信

| 技能 | 说明 |
| :--- | :--- |
| **[manage-api-integration](manage-api-integration/SKILL.md)** | 通过 REST 或 SOAP 暴露服务，并处理 JSON/XML 数据映射。 |
| **[manage-rest-api](manage-rest-api/SKILL.md)** | 使用原生服务和契约安全的包装器设计、重构和验证 OFBiz REST API。 |
| **[manage-email-services](manage-email-services/SKILL.md)** | 配置 SMTP、管理邮件模板并自动化外发邮件通信。 |

## 🔐 高级管理

| 技能 | 说明 |
| :--- | :--- |
| **[manage-security-advanced](manage-security-advanced/SKILL.md)** | 实现复杂的安全权限、ACL 和服务级数据过滤。 |
| **[manage-security-deployment](manage-security-deployment/SKILL.md)** | 在基础设施层面对 OFBiz 部署进行加固和安全防护。 |
| **[manage-localization-advanced](manage-localization-advanced/SKILL.md)** | 处理高级国际化、时区和区域特定的格式化需求。 |
| **[manage-webapps](manage-webapps/SKILL.md)** | 配置 Web 应用边界、会话管理和过滤器链。 |
| **[manage-cache-and-performance](manage-cache-and-performance/SKILL.md)** | 通过实体缓存、服务缓存和 SQL 查询调优来优化性能。 |
| **[manage-properties](manage-properties/SKILL.md)** | 在 `.properties` 文件中集中管理配置设置，支持环境切换。 |

## 🚀 项目生命周期

| 技能 | 说明 |
| :--- | :--- |
| **[create-component](create-component/SKILL.md)** | 使用标准化的目录结构搭建新的 OFBiz 插件。 |
| **[manage-component](manage-component/SKILL.md)** | 管理组件级依赖和 `ofbiz-component.xml` 注册。 |
| **[coding-standards](coding-standards/SKILL.md)** | 关于整洁代码、注释和 OFBiz 贡献标准的通用指南。 |
| **[manage-tests](manage-tests/SKILL.md)** | 在 `testdef/` 中定义自动化测试套件，实现实体测试、服务测试和 JUnit 测试，并通过 Gradle 运行。 |
| **[prepush-readiness](prepush-readiness/SKILL.md)** | 以适配 pre-push 钩子（Checkstyle、CodeNarc）的规范编写变更，加上推送前的编译、XML 校验和针对性测试。 |
| **[manage-contribution-workflow](manage-contribution-workflow/SKILL.md)** | 将变更从分支推进到可合并 PR 的完整流程：worktree 设置、framework/plugins 仓库配对、预测试数据加载、反向移植以及社区 PR 模板。 |

## 🧠 策略思考

| 技能 | 说明 |
| :--- | :--- |
| **[manage-strategies](manage-strategies/SKILL.md)** | 高层决策指南：XML vs Java、Service vs Event、以及性能权衡。 |
