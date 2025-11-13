# Bengali-STEM-Translation-Challenge

# **🔎 Project Overview**

Build a robust Bengali → English translation system for HSC-level STEM questions using LoRA fine-tuning of Meta's NLLB model. The dataset contains 5,000 Bengali–English paired STEM questions.


# **🧠 Model Architecture & Approach**

To tackle the Bengali → English STEM translation challenge, we built upon Meta’s NLLB (No Language Left Behind) model — specifically the facebook/nllb-200-distilled-600M checkpoint — known for supporting 200 languages and excelling in low-resource translation.
However, since NLLB is trained for general-purpose translation, it often struggles with domain-specific terminology (e.g., physics, chemistry, and math terms in HSC textbooks). To address this, we applied LoRA (Low-Rank Adaptation) fine-tuning to specialize the model on our dataset.
| Component              | Description                           |
| ---------------------- | ------------------------------------- |
| **Base model**         | `facebook/nllb-200-1.3B`              |
| **Architecture**       | Transformer Encoder-Decoder (Seq2Seq) |
| **Fine-tuning method** | LoRA via Hugging Face PEFT            |
| **Target modules**     | `q_proj`, `v_proj` (attention layers) |
| **LoRA parameters**    | `r = 16`, `α = 32`, dropout = 0.05    |
| **Optimizer**          | AdamW                                 |
| **Precision**          | FP16                                  |
| **Epochs**             | 30                                    |
| **Batch size**         | 8                                     |
| **Learning rate**      | 2 × 10⁻⁴                              |
| **Languages**          | `ben_Latn → eng_Latn`                 |


# **📊 Evaluation**

Metrics used:

BLEU

chrF

Term accuracy (STEM glossary match)

| Model       | chrF | BLEU | Term Accuracy |
| ----------- | ---- | ---- | ------------- |
| NLLB-base   | 45.2 | 18.1 | 64.5 %        |
| NLLB + LoRA | 52.7 | 26.9 | 78.2 %        |


# Sample Prediction
| id | english_question                                                                                     | bangla_question                                                                     |
| -- | ---------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| 1  | If blood pressure is 115/80 mmHg; what is the pulse pressure?                                        | রক্তচাপ 115/80 mmHg হলে পালস প্রেসার কত?                                            |
| 2  | What is the required force in newtons to move an object to a distance of 20 m with a force of 150 J? | 150 J কাজ করে একটি বস্তুকে 20 m দূরত্বে স্থানান্তরিত করতে প্রয়োজনীয় বল কত নিউটন?  |
| 3  | If a rectangle has a length of 21 cm and a width of 30 cm; what is its area in square centimeters?   | একটি আয়তক্ষেত্রের দৈর্ঘ্য 21 cm এবং প্রস্থ 30 cm হলে ক্ষেত্রফল কত বর্গসেন্টিমিটার? |
| 4  | If a DNA molecule contains 36% adenine; what is the percentage amount of thymine?                    | DNA অণুতে যদি অ্যাডেনিন 36% থাকে, তাহলে থাইমিনের শতকরা পরিমাণ কত?                   |
| 5  | How many moles are there in 45 g CH3COOH? (molecular mass = 60.0)                                    | 45 g CH₃COOH এ কতগুলি মোল পদার্থ আছে? (আণবিক ভর = 60.0)                             |




# 💡 Key Insights

LoRA fine-tuning enabled efficient specialization with <1 % parameter updates.

Strong improvement on STEM terminology translation (“বিকিরণ” → Radiation, “সমচাপ প্রক্রিয়া” → Isobaric process).

Demonstrated how domain adaptation can enhance multilingual models for low-resource educational data.

# 🧩 Tech Stack

Python 3.12

PyTorch + Hugging Face Transformers

PEFT (LoRA)

Datasets

Google Colab / Kaggle Notebook environment


# 👥 Team NeuralSight

🧑‍💻 Nuzhat Tabassum

👨‍💻 Utpal Barua
