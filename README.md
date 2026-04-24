# 🏥 Medical Claims Root Cause Analyzer  
### Fine-Tuned Qwen 2.5-1.5B using QLoRA

A domain-specific Large Language Model (LLM) fine-tuned to automatically identify the **root cause of medical claim denials** from structured claim data.

---

## 🎯 Project Overview

In medical billing, insurance claims are often denied due to issues related to CPT codes, diagnosis codes, or payer-specific rules. Simply reading denial codes is not enough — identifying the **true root cause** requires contextual reasoning.

This project fine-tunes a lightweight LLM (**Qwen 2.5-1.5B-Instruct**) to:

- Take structured medical claim data (JSON format) as input  
- Analyze denial-related information (CPT, ICD, denial codes, etc.)  
- Generate a **clear and concise root cause explanation**  
- Provide results via local inference or a **Gradio-based web interface**

---

## ⚙️ Fine-Tuning Approach

### Why QLoRA (Quantized Low-Rank Adaptation)?

Training or fully fine-tuning large language models is computationally expensive. This project uses **QLoRA**, which combines:

#### 🔹 1. 4-bit Quantization
- Compresses model weights from 32-bit → 4-bit  
- Significantly reduces GPU memory usage (~6GB → ~1.5GB for 1.5B model)  
- Enables training on consumer-grade GPUs  

#### 🔹 2. LoRA (Low-Rank Adaptation)
- Adds small trainable adapter layers to attention modules  
- Only ~1–3% of parameters are trained  
- Retains most of the base model’s knowledge  

---

## 💡 Key Highlights

- Instruction tuning for **controlled reasoning**
- Domain-specific adaptation (medical claims analysis)
- Efficient fine-tuning using:
  - LoRA
  - 4-bit Quantization
- Converts **structured JSON → natural language reasoning**
- End-to-end pipeline:
  > Data → Training → Inference → Deployment

---

## 🔄 Workflow

1. Load JSONL dataset (medical claims data)  
2. Convert data into instruction-based prompts  
3. Apply LoRA + 4-bit quantization  
4. Fine-tune Qwen 2.5 model  
5. Merge LoRA weights into base model  
6. Save the trained model  
7. Perform inference using prompt templates  
8. Deploy using Gradio interface  

---

## 📂 Project Structure
qwen-root-cause-llm/
│
├── README.md
├── requirements.txt
├── train.py
├── inference.py
├── app.py
├── utils.py
├── sample_data.jsonl
└── screenshots/
