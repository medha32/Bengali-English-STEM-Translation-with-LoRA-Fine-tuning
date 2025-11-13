# Bengali-STEM-Translation-Challenge

**#🔎 Project Overview**

**#Overview**
Build a robust Bengali → English translation system for HSC-level STEM questions using LoRA fine-tuning of Meta's NLLB model. The dataset contains 5,000 Bengali–English paired STEM questions.


### **🧠 Model Architecture & Approach**

To tackle the Bengali → English STEM translation challenge, we built upon Meta’s NLLB (No Language Left Behind) model — specifically the facebook/nllb-200-distilled-600M checkpoint — known for supporting 200 languages and excelling in low-resource translation.
However, since NLLB is trained for general-purpose translation, it often struggles with domain-specific terminology (e.g., physics, chemistry, and math terms in HSC textbooks). To address this, we applied LoRA (Low-Rank Adaptation) fine-tuning to specialize the model on our dataset.

**#⚙️ Architecture Details**

Base Model: facebook/nllb-200-distilled-600M

Architecture Type: Transformer-based Encoder–Decoder (Seq2Seq)

Parameter Count: ~600M

Tokenizer: SentencePiece multilingual tokenizer trained on NLLB corpus

Fine-tuning Method: Parameter-efficient LoRA using PEFT

Training Framework: Hugging Face Transformers with PyTorch backend

Optimizer: AdamW

Scheduler: Cosine learning rate decay with warmup steps

Precision: Mixed precision (FP16 / bf16)

