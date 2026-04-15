# 中文版 - RAG 聊天机器人

## 概述

RAG（检索增强生成）聊天机器人的中文模板版本，教师可以复制并自定义自己的主题、文档和角色设定。所有界面文字和提示均已翻译为简体中文。

## 用途

这是一个**模板版本** - 没有预配置的文档、角色设定或示例问题。教师需要填写：
- 文档链接（第3步）
- 角色名称和描述（第4步）
- 示例问题（第4步）

## 功能特点

- **空白模板** - 无预加载内容；添加您自己的文档和角色设定
- **中文界面** - 所有提示、说明和输出均为简体中文
- **中文优化模型** - 默认使用 Qwen/Qwen3-8B（中文能力强）
- **多格式支持** - PDF、DOCX 和 Google 文档
- **文档锚定** - 机器人仅使用所提供文档中的信息
- **来源引用** - 显示文档名称、章节编号和查询匹配的相关片段
- **对话记忆** - 记住最近3轮对话用于追问
- **简洁回答** - 最多约200字（MAX_OUTPUT_TOKENS=300）
- **30秒超时** - 防止卡死

## 技术栈

| 组件 | 技术 |
|------|------|
| 大语言模型 | Qwen/Qwen3-8B（HuggingFace API） |
| 嵌入模型 | all-MiniLM-L6-v2（Sentence Transformers） |
| 向量数据库 | ChromaDB |
| 界面 | Gradio |
| 平台 | Google Colab（免费版） |

## 配置

所有设置在第4步（单元格8）中：

```python
# API
HUGGINGFACE_TOKEN = "hf_..."

# 模型
MODEL_NAME = "Qwen/Qwen3-8B"
MAX_OUTPUT_TOKENS = 300  # 最多约200字

# 角色设定（自定义这些内容）
PERSONA_NAME = "您的角色名称"
PERSONA_DESCRIPTION = "..."  # [角色]、[场景]、[任务] 结构

# 检索
NUM_RETRIEVED_DOCS = 7
CHUNK_SIZE = 1000
OVERLAP = 200

# 记忆
CONVERSATION_MEMORY = 3
SHOW_SOURCES = True
```

## 角色设定模板

角色设定使用结构化格式：

- **[角色]** - 聊天机器人的性格和语气
- **[场景]** - 工作坊场景和关键文档
- **[任务]** - 聊天机器人的具体任务和指令

## 结构

| 步骤 | 说明 |
|------|------|
| 1 | 安装依赖库 |
| 2 | 加载依赖库 |
| 3 | 下载文档（添加您的链接） |
| 4 | 配置（令牌 + 角色 + 问题） |
| 5 | 测试 API 连接 |
| 6 | 读取文档 |
| 7 | 创建搜索数据库 |
| 8 | 设置问答系统 |
| 9 | 启动聊天界面 |

## 费用

**100% 免费**
- HuggingFace API：约300次请求/小时
- Google Colab：免费版
- 无需 VPN（香港可用）

## 快速开始

1. 打开：`https://colab.research.google.com/github/enricoconductive/letstalk/blob/main/Chinese_Version/RAG_Chatbot_Chinese.ipynb`
2. 在第3步中添加您的文档
3. 获取 HuggingFace 令牌（免费）：https://huggingface.co/settings/tokens
4. 在第4步中配置角色设定和示例问题
5. 运行所有单元格
6. 在新标签页中打开 Gradio 链接

---

**最后更新：** 2026年4月
