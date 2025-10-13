# Claude 4.5 Sonnet System Prompt 分析报告

## 文件概览

- **文件名**: `claude-4.5-sonnet.md`
- **总行数**: 2,743 行
- **文件类型**: System Prompt（系统提示词）
- **用途**: Claude 4.5 Sonnet 模型的核心行为指令集
- **版本**: Claude Sonnet 4 (claude-sonnet-4-20250514)

## 主要结构分段统计

| 序号 | 部分名称 | 起始行 | 结束行 | 行数 | 占比 | 主要功能 |
|------|---------|--------|--------|------|------|----------|
| 1 | Citation Instructions | 2 | 22 | 21 | 0.8% | 定义引用规则和版权合规要求 |
| 2 | Past Chats Tools | 25 | 219 | 195 | 7.1% | 历史对话搜索和检索功能 |
| 3 | Computer Use | 222 | 493 | 272 | 9.9% | Linux环境操作和文件管理功能 |
| 4 | Available Skills | 496 | 607 | 112 | 4.1% | 文档处理技能定义（docx, pdf, pptx, xlsx） |
| 5 | Claude Completions in Artifacts | 611 | 1021 | 411 | 15.0% | 在Artifacts中调用Claude API的详细指南 |
| 6 | Gmail & Calendar Tools | 1023 | 1031 | 9 | 0.3% | Gmail和Google Calendar工具说明 |
| 7 | Search Instructions | 1032 | 1451 | 420 | 15.3% | 网络搜索策略和版权规则 |
| 8 | Preferences Info | 1454 | 1542 | 89 | 3.2% | 用户偏好设置处理规则 |
| 9 | Tool Function Definitions | 1544 | 2614 | 1,071 | 39.0% | API工具函数的JSON Schema定义 |
| 10 | Claude Identity & Behavior | 2617 | 2695 | 79 | 2.9% | Claude的基本信息和产品介绍 |
| 11 | Core Behavioral Guidelines | 2697 | 2722 | 26 | 0.9% | 核心行为准则和对话原则 |
| 12 | Long Conversation Reminder | 2727 | 2742 | 16 | 0.6% | 长对话中的提醒事项 |

**总计**: 2,743 行

## 详细内容分析

### 1. Citation Instructions（引用指令）
**行数**: 21 行 | **占比**: 0.8%

- 定义如何正确引用搜索结果
- 强调必须用自己的话改写，不能直接引用原文
- 提供cite标签的使用规范
- 版权保护的核心要求

### 2. Past Chats Tools（历史对话工具）
**行数**: 195 行 | **占比**: 7.1%

包含子部分：
- `trigger_patterns`: 识别用户何时需要访问历史对话
- `tool_selection`: conversation_search vs recent_chats的选择逻辑
- `conversation_search_tool_parameters`: 关键词提取规则
- `recent_chats_tool_parameters`: 时间范围检索参数
- `decision_framework`: 工具选择决策树
- `response_guidelines`: 响应格式要求
- `examples`: 16个使用场景示例

### 3. Computer Use（计算机使用功能）
**行数**: 272 行 | **占比**: 9.9%

包含子部分：
- `skills`: 技能文档读取策略
- `file_creation_advice`: 文件创建触发条件
- `unnecessary_computer_use_avoidance`: 避免不必要的工具使用
- `file_handling_rules`: 文件位置和访问规则
  - `/mnt/user-data/uploads`: 用户上传文件
  - `/home/claude`: 临时工作目录
  - `/mnt/user-data/outputs`: 最终输出目录
- `producing_outputs`: 输出策略（短内容vs长内容）
- `sharing_files`: 文件分享最佳实践
- `artifacts`: Artifact创建规则
- `package_management`: npm和pip包管理

### 4. Available Skills（可用技能）
**行数**: 112 行 | **占比**: 4.1%

定义了4个核心文档处理技能：
- **docx**: Word文档创建、编辑、追踪更改
- **pdf**: PDF处理、表单填写、文本提取
- **pptx**: PowerPoint演示文稿创建和编辑
- **xlsx**: Excel电子表格、公式、数据分析

### 5. Claude Completions in Artifacts（Artifact中的Claude调用）
**行数**: 411 行 | **占比**: 15.0%

最详细的技术指南部分，包含：
- **overview**: 功能概述
- **api_details_and_prompting**: API调用详解
  - 图像和PDF处理
  - 结构化JSON响应指南
- **context_window_management**: 上下文管理策略
  - 对话管理（conversation_management）
  - 有状态应用（stateful_applications）
  - 错误处理
- **artifact_tips**: React表单限制等关键提示

### 6. Gmail & Calendar Tools（Gmail和日历工具）
**行数**: 9 行 | **占比**: 0.3%

- Gmail邮件搜索注意事项
- Google Calendar事件分析规则
- 避免使用截断的结果

### 7. Search Instructions（搜索指令）
**行数**: 420 行 | **占比**: 15.3%

第二大模块，包含：
- **core_search_behaviors**: 核心搜索行为
- **query_complexity_categories**: 查询复杂度分类
  - never_search_category: 永不搜索
  - do_not_search_but_offer_category: 先回答再提供搜索
  - single_search_category: 单次搜索
  - research_category: 深度研究（2-20次工具调用）
- **web_search_usage_guidelines**: 搜索使用指南
- **mandatory_copyright_requirements**: 版权要求
- **harmful_content_safety**: 有害内容安全规则
- **search_examples**: 6个详细示例

### 8. Preferences Info（偏好信息）
**行数**: 89 行 | **占比**: 3.2%

- 行为偏好（Behavioral Preferences）
- 上下文偏好（Contextual Preferences）
- 何时应用偏好的详细规则
- 8个偏好应用示例

### 9. Tool Function Definitions（工具函数定义）
**行数**: 1,071 行 | **占比**: 39.0%

**最大的单一部分**，包含所有可用工具的JSON Schema定义：
- `web_search`: 网络搜索
- `web_fetch`: 网页内容获取
- `google_drive_search`: Google Drive搜索（最复杂的工具定义）
- `google_drive_fetch`: Google文档获取
- `conversation_search`: 对话搜索
- `recent_chats`: 最近聊天记录
- `list_gcal_calendars`: 日历列表
- `fetch_gcal_event`: 获取日历事件
- `list_gcal_events`: 列出日历事件
- `find_free_time`: 查找空闲时间
- `read_gmail_profile`: 读取Gmail配置
- `search_gmail_messages`: 搜索Gmail邮件（包含详细的搜索操作符）
- `read_gmail_message`: 读取单条邮件（标记为不使用）
- `read_gmail_thread`: 读取邮件线程

### 10. Claude Identity & Behavior（Claude身份与行为）
**行数**: 79 行 | **占比**: 2.9%

- Claude的基本信息（Anthropic创建）
- 模型家族信息（Claude 4: Opus 4 和 Sonnet 4）
- 产品访问方式
- 知识截止日期（2025年1月底）
- 2024年美国大选信息

### 11. Core Behavioral Guidelines（核心行为准则）
**行数**: 26 行 | **占比**: 0.9%

定义Claude的核心个性和行为：
- 不使用奉承语言
- 谨慎使用表情符号
- 批判性评估理论和观点
- 心理健康警觉性
- 提供诚实反馈
- 明确AI身份
- 角色扮演边界
- 哲学论证的应对
- AI意识问题的处理方式

### 12. Long Conversation Reminder（长对话提醒）
**行数**: 16 行 | **占比**: 0.6%

长对话中的关键提醒事项，重复核心行为准则的精华部分。

## 关键发现

### 1. 内容分布特征
- **技术定义占主导**: 工具函数定义（39.0%）是最大部分
- **功能指南丰富**: Claude in Artifacts（15.0%）和搜索指令（15.3%）占约30%
- **核心行为简洁**: 身份和行为准则仅占3.8%，但非常关键

### 2. 设计理念
- **工具优先**: 强调通过工具扩展能力
- **版权合规**: 在多个部分重复强调版权保护
- **用户安全**: 有害内容、儿童安全多次提及
- **灵活适配**: 根据查询复杂度动态调整策略

### 3. 技术架构
- **模块化设计**: 每个功能独立封装
- **详细示例**: 关键功能都配有实例说明
- **决策树逻辑**: 使用明确的if-then规则
- **错误预防**: 明确的"不要做"指令

### 4. 交互原则
- **直接响应**: 避免奉承，直接给答案
- **批判思维**: 不盲目认同用户观点
- **情境感知**: 根据对话类型调整风格
- **透明度**: 明确AI身份，不混淆

## 各类指令统计

### 按指令类型分类

| 类型 | 行数 | 占比 | 说明 |
|------|------|------|------|
| 工具API定义 | 1,071 | 39.0% | JSON Schema格式的函数定义 |
| 功能使用指南 | 1,103 | 40.2% | Computer Use + Artifacts + Search |
| 行为准则 | 210 | 7.7% | Identity + Core Guidelines + Reminders |
| 工具选择逻辑 | 284 | 10.4% | Past Chats + Preferences |
| 技能定义 | 112 | 4.1% | Document processing skills |
| 其他 | 21 | 0.8% | Citations等 |

### 按XML标签层级统计

**一级标签** (12个主要部分):
- citation_instructions
- past_chats_tools
- computer_use
- available_skills
- claude_completions_in_artifacts
- search_instructions
- preferences_info
- functions (隐含在Tool Function Definitions中)
- election_info
- long_conversation_reminder

**二级标签** (约60+子部分):
- 如 `trigger_patterns`, `tool_selection`, `conversation_management` 等

## 设计洞察

### 1. 渐进式能力扩展
System prompt采用"核心+工具"架构：
- 核心行为准则简洁明确（约200行）
- 通过工具API扩展功能范围（1000+行）
- 每个工具都有详细的使用指南

### 2. 安全与合规优先
多层次的安全保障：
- 版权保护（Citation + Search）
- 有害内容过滤（Harmful Content Safety）
- 儿童保护（Child Safety）
- 隐私保护（Gmail工具中的注意事项）

### 3. 用户体验优化
- 动态搜索策略（0-20次工具调用）
- 上下文感知的响应风格
- 用户偏好的细粒度控制
- 长对话中的提醒机制

### 4. 开发者友好
- 完整的API Schema定义
- 丰富的使用示例
- 清晰的错误处理指南
- Computer Use功能支持快速开发

## 复杂度分析

### 最复杂的部分（按详细程度）

1. **Google Drive Search** (~200行): 最复杂的工具定义，包含完整的查询语法
2. **Search Instructions** (420行): 包含复杂的决策树和多个场景
3. **Claude in Artifacts** (411行): 技术实现的详细指南
4. **Computer Use** (272行): 文件系统和环境管理

### 最简洁的部分

1. **Gmail & Calendar Tools** (9行): 仅关键注意事项
2. **Citation Instructions** (21行): 清晰的规则定义
3. **Long Conversation Reminder** (16行): 精华提炼

## 总结

Claude 4.5 Sonnet 的 system prompt 是一个精心设计的多层次指令系统：

1. **规模适中**: 2,743行，在详细和简洁之间取得平衡
2. **结构清晰**: 12个主要模块，职责明确
3. **工具驱动**: 39%的内容是工具定义，体现能力扩展策略
4. **安全为先**: 多处强调版权、安全和伦理规范
5. **实例丰富**: 关键功能都配有详细示例
6. **持续优化**: 包含长对话提醒等实用机制

这份 system prompt 不仅定义了 Claude 的能力边界，更体现了 Anthropic 在AI助手设计上的深度思考和工程实践。

---

*分析日期: 2025年10月*  
*文件版本: Claude Sonnet 4 (claude-sonnet-4-20250514)*

