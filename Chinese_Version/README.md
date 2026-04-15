# RAG 聊天机器人 - 模板版本（中文版）

一个空白模板 RAG 聊天机器人，教师可以复制并自定义自己的主题、文档和角色设定。

## 这是什么？

这是 RAG（检索增强生成）聊天机器人的**空白模板**版本。它包含所有代码基础设施，但没有预加载的文档或特定主题内容。请用您自己的内容填充占位符：

- **文档**（PDF、DOCX 或 Google 文档）
- **角色设定**（聊天机器人的性格和指令）
- **示例问题**（学生使用的示例提示）

## 快速开始

**Colab 直接链接：**
```
https://colab.research.google.com/github/enricoconductive/letstalk/blob/main/Chinese_Version/RAG_Chatbot_Chinese.ipynb
```

**设置时间：** 约5分钟（添加文档后）

**您需要配置：**
1. 您的 HuggingFace API 令牌
2. 您的文档链接（第3步）
3. 您的角色描述（第4步）
4. 您的示例问题（第4步）

## 步骤

| 步骤 | 说明 | 时间 |
|------|------|------|
| 1 | 安装依赖库 | 约30秒 |
| 2 | 加载依赖库 | 约5秒 |
| 3 | **下载文档**（添加您的链接） | 约10秒 |
| 4 | **配置**（令牌 + 角色 + 问题） | - |
| 5 | 测试 API 连接 | 约5秒 |
| 6 | 读取文档 | 约30秒 |
| 7 | 创建搜索数据库 | 约1分钟 |
| 8 | 设置问答系统 | 约5秒 |
| 9 | 启动聊天界面 | 约10秒 |

## 如何添加文档

在第3步中，将您的文档添加到 `DOCUMENTS` 列表：

```python
DOCUMENTS = [
    # PDF/DOCX: ("文件名", "GOOGLE_DRIVE_文件ID", "pdf" 或 "docx")
    ("Your_Document.pdf", "YOUR_GOOGLE_DRIVE_FILE_ID", "pdf"),

    # Google 文档: ("文件名.txt", "GOOGLE_DOC_ID", "gdoc")
    ("Your_Doc.txt", "YOUR_GOOGLE_DOC_ID", "gdoc"),
]
```

**如何获取 ID：**
- **PDF/DOCX：** 分享链接 `https://drive.google.com/file/d/文件ID/view` -> 提取文件ID
- **Google 文档：** 文档网址 `https://docs.google.com/document/d/文档ID/edit` -> 提取文档ID

**重要：** 文件必须设置为"知道链接的任何人都可查看"。

## HuggingFace 令牌设置

1. 访问 https://huggingface.co/settings/tokens
2. 点击 "Create new token"（创建新令牌）
3. 选择 **"Fine-grained"**
4. 启用 **"Make calls to Inference Providers"**
5. 复制令牌（以 `hf_` 开头）

## 功能特点

- **可自定义角色** - 定义聊天机器人的性格、场景和任务
- **多格式文档** - PDF、DOCX 和 Google 文档
- **文档锚定** - 机器人仅使用您文档中的信息
- **来源引用** - 查看使用了哪些文档及相关原文摘录
- **对话记忆** - 支持追问
- **30秒超时** - 防止卡死
- **简洁回答** - 最多约200字
- **中文优化** - 默认使用 Qwen 模型，中文能力强

## 故障排除

| 问题 | 解决方案 |
|------|----------|
| API 503 错误 | 模型正在加载 - 等待30秒 |
| API 401/403 错误 | 检查令牌是否有 "Inference Providers" 权限 |
| 下载失败 | 确保 Google Drive 文件已公开分享 |
| 超时错误 | 尝试更短或更简单的问题 |
| 未找到文档 | 在第3步中添加您的文档链接 |

## 许可证

与主项目相同 - 参见根目录 LICENSE 文件。
