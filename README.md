<div align="center">

# ğŸ›ï¸ Turkish History AI Chatbot

### An intelligent chatbot fine-tuned on Turkish historical data using LoRA & Unsloth

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python)](https://python.org)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0%2B-EE4C2C?style=for-the-badge&logo=pytorch)](https://pytorch.org)
[![Hugging Face](https://img.shields.io/badge/ğŸ¤—-Transformers-yellow?style=for-the-badge)](https://huggingface.co)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)
[![Open In Colab](https://img.shields.io/badge/Open%20in-Colab-F9AB00?style=for-the-badge&logo=googlecolab)](https://colab.research.google.com)

<img src="images/chatbot_demo.png" alt="Turkish History AI Chatbot Demo" width="800"/>

</div>

---

## ğŸ“– About the Project

**Turkish History AI Chatbot** is a domain-specific conversational AI model fine-tuned on Turkish historical texts using **LoRA (Low-Rank Adaptation)** and **Unsloth** for efficient training. The chatbot can answer natural language questions about Ottoman Empire, Turkish Republic, key historical figures, battles, reforms, and more â€” in both Turkish and English.

### âœ¨ Key Features

- ğŸ§  **Fine-tuned LLaMA 2 7B** â€” Optimized for Turkish historical knowledge
- âš¡ **LoRA Fine-Tuning** â€” Efficient training with minimal compute via Unsloth
- ğŸ’¬ **Natural Language Understanding** â€” Conversational Q&A in Turkish
- ğŸ¨ **Gradio Interface** â€” Clean, interactive web UI
- ğŸ”„ **Google Drive Integration** â€” Model weights loaded directly from Drive
- ğŸ“š **Domain-Specific Knowledge** â€” Ottoman history, Turkish Republic, key figures & events

### ğŸ¯ Topics Covered

| Category | Examples |
|---|---|
| Ottoman Empire | Rise & fall, sultans, administrative structure |
| Turkish Republic | Founding, AtatÃ¼rk's reforms, early republic period |
| Wars & Battles | War of Independence, Gallipoli, Balkan Wars |
| Historical Figures | Mustafa Kemal AtatÃ¼rk, Fatih Sultan Mehmet, Suleiman the Magnificent |
| Reforms | Tanzimat, MeÅŸrutiyet, alphabet reform, secularism |

---

## ğŸ—ï¸ Architecture

```
Base Model: meta-llama/Llama-2-7b-chat-hf
    â”‚
    â–¼
LoRA Adapter (rank=16, alpha=32)
    â”‚
    â”œâ”€â”€ Target Modules: q_proj, v_proj
    â”‚
    â””â”€â”€ Training: Unsloth + HuggingFace Trainer
         â”‚
         â–¼
    Saved Adapter â†’ Google Drive
         â”‚
         â–¼
    Gradio Chatbot Interface
```

### Model Configuration

| Parameter | Value |
|---|---|
| Base Model | LLaMA 2 7B Chat |
| LoRA Rank (r) | 16 |
| LoRA Alpha | 32 |
| LoRA Dropout | 0.05 |
| Max Sequence Length | 2048 |
| Training Framework | Unsloth + PEFT |
| Quantization | 4-bit (NF4) |

---

## ğŸš€ Getting Started

### Prerequisites

- Google Colab account (free tier works with T4 GPU)
- Google Drive (for model weights)
- Python 3.10+

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/mehmeteminyilmaz/Turk-Tarihi-AI-Chatbot.git
cd Turk-Tarihi-AI-Chatbot
```

2. **Install dependencies**
```bash
pip install -r requirements.txt
```

3. **Open the notebook in Google Colab**

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mehmeteminyilmaz/Turk-Tarihi-AI-Chatbot/blob/main/chatbot.ipynb)

### Running the Chatbot

1. Open `chatbot.ipynb` in Google Colab
2. Enable GPU: `Runtime â†’ Change Runtime Type â†’ T4 GPU`
3. Mount your Google Drive (model weights will be loaded automatically)
4. Run all cells
5. Click the Gradio link to open the chatbot interface

---

## ğŸ¤– Model Weights

The model weights are **not included** in this repository due to their large size (~3.5 GB).

### How to obtain the model:

**Option 1: Re-train the model (Recommended)**
```bash
# Open chatbot.ipynb and run the training cells
# Training takes approximately 1-2 hours on a T4 GPU
```

**Option 2: Download from Google Drive**

> Contact me via [GitHub Issues](https://github.com/mehmeteminyilmaz/Turk-Tarihi-AI-Chatbot/issues) to request access to the pre-trained weights.

**Option 3: Use the base model without fine-tuning**
```python
from transformers import AutoModelForCausalLM, AutoTokenizer

model = AutoModelForCausalLM.from_pretrained("meta-llama/Llama-2-7b-chat-hf")
```

---

## ğŸ“Š Training Details

| Detail | Value |
|---|---|
| Training Framework | Google Colab (T4 GPU) |
| Training Duration | ~1-2 hours |
| Dataset Size | Custom Turkish history Q&A pairs |
| Epochs | 3 |
| Batch Size | 2 (with gradient accumulation 4) |
| Learning Rate | 2e-4 |
| Optimizer | AdamW (8-bit) |

---

## ğŸ“ Project Structure

```
Turk-Tarihi-AI-Chatbot/
â”‚
â”œâ”€â”€ ğŸ““ chatbot.ipynb          # Main notebook: training + inference + Gradio UI
â”œâ”€â”€ ğŸ“‹ requirements.txt       # Python dependencies
â”œâ”€â”€ ğŸ“„ README.md              # Project documentation
â”œâ”€â”€ âš–ï¸  LICENSE               # MIT License
â”œâ”€â”€ ğŸš« .gitignore             # Files excluded from Git
â”‚
â”œâ”€â”€ ğŸ“‚ images/
â”‚   â”œâ”€â”€ chatbot_demo.png      # Gradio interface screenshot
â”‚   â””â”€â”€ architecture.png     # Model architecture diagram
â”‚
â”œâ”€â”€ ğŸ“‚ dataset/
â”‚   â””â”€â”€ README.md            # Dataset description and source
â”‚
â””â”€â”€ ğŸ“‚ model/
    â””â”€â”€ README.md            # How to download/train the model
```

---

## ğŸ’¡ Example Usage

```
You: OsmanlÄ± Ä°mparatorluÄŸu ne zaman kuruldu?

Bot: OsmanlÄ± Ä°mparatorluÄŸu, 1299 yÄ±lÄ±nda Osman Bey tarafÄ±ndan kurulmuÅŸtur.
     Anadolu'nun kuzeybatÄ±sÄ±nda kÃ¼Ã§Ã¼k bir beylik olarak baÅŸlayan bu devlet,
     zamanla Asya, Avrupa ve Afrika'yÄ± kapsayan bÃ¼yÃ¼k bir imparatorluÄŸa
     dÃ¶nÃ¼ÅŸmÃ¼ÅŸtÃ¼r...

You: AtatÃ¼rk hangi reformlarÄ± yaptÄ±?

Bot: Mustafa Kemal AtatÃ¼rk, TÃ¼rkiye Cumhuriyeti'nin kurucusu olarak pek Ã§ok
     kÃ¶klÃ¼ reform gerÃ§ekleÅŸtirmiÅŸtir. Bu reformlar arasÄ±nda harf devrimi (1928),
     takvim deÄŸiÅŸikliÄŸi, medeni kanunun kabulÃ¼, laiklik ilkesinin benimsenmesi
     ve eÄŸitim sisteminin yeniden yapÄ±landÄ±rÄ±lmasÄ± yer almaktadÄ±r...
```

---

## ğŸ”® Future Improvements

- [ ] Expand dataset with more historical sources
- [ ] Add English language support
- [ ] Deploy to Hugging Face Spaces for public access
- [ ] Implement RAG (Retrieval-Augmented Generation) for more accurate responses
- [ ] Add source citations for historical claims
- [ ] Fine-tune on larger model (LLaMA 2 13B)
- [ ] Create a standalone web application

---

## ğŸ› ï¸ Technologies Used

<div align="center">

| Technology | Purpose |
|---|---|
| ğŸ Python | Core programming language |
| ğŸ”¥ PyTorch | Deep learning framework |
| ğŸ¤— Transformers | Model architecture & tokenization |
| âš¡ Unsloth | 2x faster LoRA fine-tuning |
| ğŸ¯ PEFT | Parameter-efficient fine-tuning |
| ğŸ¨ Gradio | Interactive web interface |
| ğŸ““ Google Colab | Training environment (T4 GPU) |
| ğŸ’¾ Google Drive | Model weight storage |

</div>

---

## ğŸ¤ Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## ğŸ“ License

This project is licensed under the MIT License â€” see the [LICENSE](LICENSE) file for details.

---

## ğŸ“§ Contact

**mehmeteminyilmaz** â€” [GitHub Profile](https://github.com/mehmeteminyilmaz)

Project Link: [https://github.com/mehmeteminyilmaz/Turk-Tarihi-AI-Chatbot](https://github.com/mehmeteminyilmaz/Turk-Tarihi-AI-Chatbot)

---

<hr/>
<br/>

<div align="center">

# ğŸ›ï¸ TÃ¼rk Tarihi Yapay Zeka Sohbet Botu

### LoRA Fine-Tuning ile EÄŸitilmiÅŸ TÃ¼rk Tarihi UzmanÄ± Chatbot

</div>

---

## ğŸ“– Proje HakkÄ±nda

**TÃ¼rk Tarihi Yapay Zeka Sohbet Botu**, LoRA (Low-Rank Adaptation) ve Unsloth kullanÄ±larak TÃ¼rk tarihi verileriyle ince ayar yapÄ±lmÄ±ÅŸ bir dil modelidir. OsmanlÄ± Ä°mparatorluÄŸu, TÃ¼rkiye Cumhuriyeti, Ã¶nemli tarihsel olaylar ve kiÅŸiler hakkÄ±nda doÄŸal dilde sorulara TÃ¼rkÃ§e cevap verebilmektedir.

### ğŸ¯ Kapsanan Konular

- OsmanlÄ± Ä°mparatorluÄŸu kuruluÅŸu, yÃ¼kseliÅŸi ve Ã§Ã¶kÃ¼ÅŸÃ¼
- TÃ¼rkiye Cumhuriyeti'nin kuruluÅŸu ve AtatÃ¼rk dÃ¶nemine ait reformlar
- KurtuluÅŸ SavaÅŸÄ± ve Ã¶nemli muharebeler
- Fatih Sultan Mehmet, Kanuni Sultan SÃ¼leyman, Mustafa Kemal AtatÃ¼rk gibi tarihi ÅŸahsiyetler
- Tanzimat ve MeÅŸrutiyet dÃ¶nemleri

---

## ğŸš€ BaÅŸlangÄ±Ã§

### Gereksinimler

- Google Colab hesabÄ± (Ã¼cretsiz T4 GPU ile Ã§alÄ±ÅŸÄ±r)
- Google Drive (model aÄŸÄ±rlÄ±klarÄ± iÃ§in)

### Kurulum

1. **Repository'yi klonla**
```bash
git clone https://github.com/mehmeteminyilmaz/Turk-Tarihi-AI-Chatbot.git
```

2. **Google Colab'da aÃ§**
   - `chatbot.ipynb` dosyasÄ±nÄ± Colab'da aÃ§
   - Runtime â†’ T4 GPU seÃ§
   - TÃ¼m hÃ¼creleri Ã§alÄ±ÅŸtÄ±r
   - Gradio linkine tÄ±kla

### Chatbot'u Ã‡alÄ±ÅŸtÄ±r

```python
# Ã–rnek kullanÄ±m
soru = "OsmanlÄ± Ä°mparatorluÄŸu kaÃ§ yÄ±l hÃ¼kÃ¼m sÃ¼rdÃ¼?"
cevap = chatbot(soru)
print(cevap)
```

---

## ğŸ¤– Model AÄŸÄ±rlÄ±klarÄ±

Model aÄŸÄ±rlÄ±klarÄ± boyutlarÄ± nedeniyle bu repository'ye dahil edilmemiÅŸtir (~3.5 GB).

**Modeli yeniden eÄŸitmek iÃ§in:**
- `chatbot.ipynb` dosyasÄ±ndaki eÄŸitim hÃ¼crelerini Ã§alÄ±ÅŸtÄ±r
- T4 GPU ile yaklaÅŸÄ±k 1-2 saat sÃ¼rer

**Ã–nceden eÄŸitilmiÅŸ aÄŸÄ±rlÄ±klar iÃ§in:**
- [GitHub Issues](https://github.com/mehmeteminyilmaz/Turk-Tarihi-AI-Chatbot/issues) Ã¼zerinden benimle iletiÅŸime geÃ§ebilirsin

---

## ğŸ“ Lisans

Bu proje MIT LisansÄ± altÄ±nda lisanslanmÄ±ÅŸtÄ±r. Detaylar iÃ§in [LICENSE](LICENSE) dosyasÄ±na bakÄ±nÄ±z.

