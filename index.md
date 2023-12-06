![img](./index.assets/logo-long-chatchat-trans-v2.png)


## 项目简介

📃 **LangChain-Chatchat** (原 Langchain-ChatGLM):  基于 Langchain 与 ChatGLM 等大语言模型的本地知识库问答应用实现。

🤖️ 一种利用 [langchain](https://github.com/hwchase17/langchain) 思想实现的基于本地知识库的问答应用，目标期望建立一套对中文场景与开源模型支持友好、可离线运行的知识库问答解决方案。

💡 受 [GanymedeNil](https://github.com/GanymedeNil) 的项目 [document.ai](https://github.com/GanymedeNil/document.ai) 和 [AlexZhangji](https://github.com/AlexZhangji) 创建的 [ChatGLM-6B Pull Request](https://github.com/THUDM/ChatGLM-6B/pull/216) 启发，建立了全流程可使用开源模型实现的本地知识库问答应用。本项目的最新版本中通过使用 [FastChat](https://github.com/lm-sys/FastChat) 接入 Vicuna, Alpaca, LLaMA, Koala, RWKV 等模型，依托于 [langchain](https://github.com/langchain-ai/langchain) 框架支持通过基于 [FastAPI](https://github.com/tiangolo/fastapi) 提供的 API 调用服务，或使用基于 [Streamlit](https://github.com/streamlit/streamlit) 的 WebUI 进行操作。

✅ 依托于本项目支持的开源 LLM 与 Embedding 模型，本项目可实现全部使用**开源**模型**离线私有部署**。与此同时，本项目也支持 OpenAI GPT API 的调用，并将在后续持续扩充对各类模型及模型 API 的接入。

⛓️ 本项目实现原理如下图所示，过程包括加载文件 -> 读取文本 -> 文本分割 -> 文本向量化 -> 问句向量化 -> 在文本向量中匹配出与问句向量最相似的 `top k`个 -> 匹配出的文本作为上下文和问题一起添加到 `prompt`中 -> 提交给 `LLM`生成回答。


## 算法流程

📺 [原理介绍视频](https://www.bilibili.com/video/BV13M4y1e7cN/?share_source=copy_web&vd_source=e6c5aafe684f30fbe41925d61ca6d514)

实现原理图：

![实现原理图](./index.assets/langchain+chatglm.png) 

从文档处理角度来看，实现流程如下：

![实现原理图2](./index.assets/langchain+chatglm2.png)


## 技术路线图

- [X] Langchain 应用
  - [X] 本地数据接入
    - [X] 接入非结构化文档
      - [X] .txt, .rtf, .epub, .srt
      - [X] .eml, .msg
      - [X] .html, .xml, .toml
      - [X] .json, .jsonl
      - [X] .md, .rst
      - [X] .docx, .doc, .pptx, .ppt, .odt
      - [X] .pdf
      - [X] .jpg, .jpeg, .png, .bmp
      - [X] .py, .ipynb
    - [X] 结构化数据接入
      - [X] .csv, .tsv
      - [X] .xlsx, .xlsd
    - [ ] 分词及召回
      - [X] 接入不同类型 TextSplitter
      - [X] 优化依据中文标点符号设计的 ChineseTextSplitter
      - [ ] 重新实现上下文拼接召回
    - [ ] 本地网页接入
    - [ ] SQL 接入
    - [ ] 知识图谱/图数据库接入
  - [X] 搜索引擎接入
    - [X] Bing 搜索
    - [X] DuckDuckGo 搜索
    - [X] Metaphor 搜索
  - [X] Agent 实现
    - [X] 基础React形式的Agent实现，包括调用计算器等
    - [X] Langchain 自带的Agent实现和调用
    - [X] 智能调用不同的数据库和联网知识
    - [ ] 更多工具
- [X] LLM 模型接入
  - [X] 支持通过调用 [FastChat](https://github.com/lm-sys/fastchat) api 调用 llm
  - [X] 支持 ChatGLM API 等 LLM API 的接入
  - [X] 支持 Langchain 框架支持的LLM API 接入
- [X] Embedding 模型接入
  - [X] 支持调用 HuggingFace 中各开源 Emebdding 模型
  - [X] 支持 OpenAI Embedding API 等 Embedding API 的接入
  - [X] 支持 智谱AI、百度千帆、千问、MiniMax 等在 Embedding API 的接入
- [X] 基于 FastAPI 的 API 方式调用
- [X] Web UI
  - [X] 基于 Streamlit 的 Web UI