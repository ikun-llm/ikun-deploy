<p align="center"><img src="https://raw.githubusercontent.com/ikun-llm/.github/main/profile/logo.png" width="120" /></p>
<h2 align="center">ikun-deploy</h2>
<p align="center"><b>把练习生送上舞台</b><br/><sub>Level 4 | 工程篇</sub></p>

---

> 从练习室到舞台，ikun 出道指南。

## 你将学到

- 模型格式转换：PyTorch → HuggingFace → GGUF
- 搭建 OpenAI 兼容 API 服务
- Streamlit 聊天界面
- llama.cpp / ollama / vllm 部署
- 模型量化（int8/int4）减小体积

## 部署方式一览

| 方式 | 适用场景 | 命令 |
|------|---------|------|
| `eval_llm.py` | 本地终端测试 | `python eval_llm.py --weight full_sft` |
| `serve_openai_api.py` | API 服务 | `python serve_openai_api.py` |
| `web_demo.py` | Web 聊天界面 | `streamlit run web_demo.py` |
| ollama | 一键本地部署 | `ollama run ikun-2.5B` |
| llama.cpp | C++ 高性能推理 | 转 GGUF 后运行 |
| vllm | 高吞吐服务 | `vllm serve ikun-2.5B` |

## 格式转换流程

```
PyTorch (.pth)
    ↓ convert_model.py
HuggingFace (pytorch_model.bin + config.json)
    ↓ llama.cpp/convert
GGUF (.gguf)
    ↓
ollama / llama.cpp / vllm
```

## 核心代码

基于 [MiniMind](https://github.com/jingyaogong/minimind) 的:
- `scripts/serve_openai_api.py` — FastAPI OpenAI 兼容服务端
- `scripts/web_demo.py` — Streamlit 聊天前端
- `scripts/convert_model.py` — 格式转换工具

## 量化对比

| 精度 | 模型大小 | 速度 | 质量 |
|------|---------|------|------|
| float16 | 49MB | 基准 | 最佳 |
| int8 | ~25MB | ×1.5 | 几乎无损 |
| int4 | ~13MB | ×2 | 略有下降 |

## 系列导航

| Level | Repo | 学什么 |
|-------|------|--------|
| 1 | [ikun-tokenizer](https://github.com/ikun-llm/ikun-tokenizer) | 分词器原理 |
| 1 | [ikun-pretrain](https://github.com/ikun-llm/ikun-pretrain) | 从零预训练 |
| 1 | [ikun-2.5B](https://github.com/ikun-llm/ikun-2.5B) | SFT + LoRA 微调 |
| 2 | [ikun-DPO](https://github.com/ikun-llm/ikun-DPO) | 偏好对齐 |
| 2 | [ikun-GRPO](https://github.com/ikun-llm/ikun-GRPO) | 强化学习 |
| 2 | [ikun-Reason](https://github.com/ikun-llm/ikun-Reason) | 推理模型 |
| 3 | [ikun-MoE](https://github.com/ikun-llm/ikun-MoE) | 混合专家 |
| 3 | [ikun-Distill](https://github.com/ikun-llm/ikun-Distill) | 知识蒸馏 |
| 3 | [ikun-V](https://github.com/ikun-llm/ikun-V) | 多模态 |
| **4** | **ikun-deploy** ← 你在这里 | **部署** |
