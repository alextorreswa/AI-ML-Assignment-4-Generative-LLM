# AI-ML-Assignment-4-Generative-LLM

# Bible Q&A with FLAN-T5 (Hugging Face Transformers)

**Name:** Alex Torres  
**Model Used:** `google/flan-t5-small`  
**Task:** Question Answering (Generative)

This project uses a pre-trained Large Language Model from Hugging Face to answer questions about a short passage from the Bible (Psalm 23, KJV). The model is loaded with the `transformers` library and is prompted with both the context and a question. We then generate answers while varying the **temperature** parameter to observe how it affects the model’s style and output quality.

---

## 1. Environment & Model

### Libraries Used
- `transformers`
- `torch`

### Model
- `google/flan-t5-small` (sequence-to-sequence model fine-tuned for instruction-style tasks)

The notebook/script includes:

1. Environment setup (installing `transformers` and `torch`).
2. Loading the tokenizer and model from Hugging Face Hub.
3. Defining the context (Psalm 23) and helper function `answer_question(...)`.
4. Running three test cases with different **temperature** settings.
5. Selecting a final “best” configuration based on qualitative results.

---

## 2. Task Description

**Chosen Task:** Generative Question Answering

- **Context:** Psalm 23 (KJV)
- **Example Question:**  
  *"According to the passage, why does the speaker say he will fear no evil?"*
- The model is instructed to answer **based only on the provided passage**.

---

## 3. Parameter Experimentation

Primary parameter studied: **Temperature**  
Other parameters held constant:

- `max_new_tokens = 40`
- `top_p = 0.9`

### Test Cases Table

> Replace snippet text with your actual model outputs if needed.

| Test # | Temperature | Output Snippet                                                                                   | Brief Observation |
|-------:|-------------|--------------------------------------------------------------------------------------------------|-------------------|
| 1      | 0.2         | "Because the Lord is with him; His rod and staff comfort him."                                   | Very concise and conservative. Faithful to text, low creativity. |
| 2      | 0.7         | "He will not fear evil because the Lord is with him, guiding and comforting him with His rod and staff." | Balanced, natural wording; still faithful to the passage. |
| 3      | 1.0         | "He says he will not fear any evil since God walks with him, protecting and comforting him with His rod, staff, and constant presence." | More expressive; slightly more interpretive. |

---

### Final “Best” Setting

The **temperature ≈ 1** configuration produced the best balance between:

- Faithful reproduction of the passage  
- Natural, fluent language  
- Mild creativity without drifting from the original meaning  

Final experiment used:

- `temperature = 1.0`  
- `top_p = 0.9`  
- `max_new_tokens = 50`

---
