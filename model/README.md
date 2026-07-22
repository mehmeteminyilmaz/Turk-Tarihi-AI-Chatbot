# ğŸ“‚ Model Weights

The trained LoRA adapter weights are **not included** in this repository due to their large size.

## ğŸ“ Size

| Component | Size |
|---|---|
| LoRA Adapter (full) | ~1.5â€“3.5 GB |
| 4-bit quantized | ~500 MB |

## ğŸ”„ How to Get the Model

### Option 1: Re-train the Model (Recommended)

1. Open `chatbot.ipynb` in Google Colab
2. Enable T4 GPU: `Runtime â†’ Change Runtime Type â†’ GPU (T4)`
3. Run all cells in the **Training** section
4. Training takes approximately **1â€“2 hours** on a free T4 GPU
5. The trained adapter will be saved to your Google Drive automatically

### Option 2: Request Pre-trained Weights

If you'd like access to the pre-trained LoRA adapter:

1. Open a [GitHub Issue](https://github.com/mehmeteminyilmaz/Turk-Tarihi-AI-Chatbot/issues/new)
2. Title it: `[Model Request] Pre-trained weights access`
3. I'll respond within a few days with a Google Drive link

### Option 3: Use the Base Model (No Fine-tuning)

```python
from transformers import AutoModelForCausalLM, AutoTokenizer
import torch

model_name = "meta-llama/Llama-2-7b-chat-hf"

tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForCausalLM.from_pretrained(
    model_name,
    torch_dtype=torch.float16,
    device_map="auto"
)
```

> **Note**: The base model without fine-tuning will not have Turkish history domain knowledge.

## ğŸ“ Expected Directory Structure After Training

```
model/
â”œâ”€â”€ README.md           â† This file
â””â”€â”€ lora_adapter/       â† Created after training (gitignored)
    â”œâ”€â”€ adapter_config.json
    â”œâ”€â”€ adapter_model.bin
    â””â”€â”€ tokenizer files...
```

## âš™ï¸ LoRA Configuration Used

```python
lora_config = LoraConfig(
    r=16,
    lora_alpha=32,
    target_modules=["q_proj", "v_proj"],
    lora_dropout=0.05,
    bias="none",
    task_type="CAUSAL_LM"
)
```

