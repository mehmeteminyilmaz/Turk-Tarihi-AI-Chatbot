# 🏛️ Türk Tarihi Yapay Zeka Sohbet Botu (Turkish History AI Chatbot)

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue?style=for-the-badge&logo=python)](https://python.org)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0%2B-EE4C2C?style=for-the-badge&logo=pytorch)](https://pytorch.org)
[![HuggingFace](https://img.shields.io/badge/%F0%9F%A4%97-Transformers-yellow?style=for-the-badge)](https://huggingface.co)
[![License: MIT](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](LICENSE)
[![Open In Colab](https://img.shields.io/badge/Open%20in-Colab-F9AB00?style=for-the-badge&logo=googlecolab)](https://colab.research.google.com/github/mehmeteminyilmaz/Turk-Tarihi-AI-Chatbot/blob/main/chatbot.ipynb)

![Turkish History AI Chatbot Demo](images/chatbot_demo.png)

---

## 📖 Proje Hakkında (About the Project)

**Türk Tarihi Yapay Zeka Sohbet Botu**, LoRA (Low-Rank Adaptation) ve Unsloth kullanılarak Türk tarihi verileriyle fine-tune edilmiş (ince ayar yapılmış) bir dil modelidir. Osmanlı İmparatorluğu, Türkiye Cumhuriyeti, önemli tarihsel olaylar ve kişiler hakkında doğal dilde sorulara Türkçe cevap verebilmektedir.

### ✨ Öne Çıkan Özellikler (Key Features)

- 🧠 **Fine-Tuned LLaMA 2 7B**: Türk tarihi alanında özel olarak eğitildi.
- ⚡ **LoRA & Unsloth**: Düşük donanım kaynağıyla hızlı ve verimli fine-tuning.
- 💬 **Doğal Dil Anlama**: Türkçe sorulara akıcı ve mantıklı cevaplar.
- 🎨 **Gradio Web Arayüzü**: Kullanıcı dostu ve şık arayüz.
- 🔄 **Google Drive Entegrasyonu**: Model ağırlıkları doğrudan Drive'dan yüklenir.

---

## 🎯 Kapsanan Konular (Topics Covered)

| Kategori | Örnek Konular |
|---|---|
| **Osmanlı İmparatorluğu** | Kuruluş, yükselme, padişahlar, devlet yapısı |
| **Türkiye Cumhuriyeti** | Kuruluş dönemi, Atatürk reformları, ilk meclis |
| **Savaşlar & Muharebeler** | Kurtuluş Savaşı, Çanakkale, Malazgirt, Balkan Savaşları |
| **Tarihi Şahsiyetler** | Mustafa Kemal Atatürk, Fatih Sultan Mehmet, Kanuni Sultan Süleyman |
| **Reformlar & Fermanlar** | Tanzimat, Meşrutiyet, Harf Devrimi, Laiklik |

---

## 🏗️ Model Mimarisi (Architecture)

```text
Base Model: meta-llama/Llama-2-7b-chat-hf (4-bit quantized)
     |
     +--> LoRA Adapter (rank=16, alpha=32, target_modules=["q_proj", "v_proj"])
           |
           +--> Training: Unsloth + HuggingFace Trainer
                 |
                 +--> Saved Weights (Google Drive)
                       |
                       +--> Gradio Chatbot Web UI
```

### ⚙️ Konfigürasyon (Model Configuration)

| Parametre | Değer |
|---|---|
| **Base Model** | LLaMA 2 7B Chat |
| **LoRA Rank (r)** | 16 |
| **LoRA Alpha** | 32 |
| **LoRA Dropout** | 0.05 |
| **Max Sequence Length** | 2048 |
| **Eğitim Framework'ü** | Unsloth + PEFT + HuggingFace |
| **Quantization** | 4-bit (NF4) |

---

## 🚀 Başlangıç & Kurulum (Getting Started)

### Gereksinimler (Prerequisites)

- Google Colab hesabı (ücretsiz T4 GPU)
- Google Drive (model ağırlıkları için)
- Python 3.10+

### Adım Adım Çalıştırma

1. **Repository'yi klonlayın:**
   ```bash
   git clone https://github.com/mehmeteminyilmaz/Turk-Tarihi-AI-Chatbot.git
   cd Turk-Tarihi-AI-Chatbot
   ```

2. **Gerekli kütüphaneleri yükleyin:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Google Colab'da `chatbot.ipynb` notebook'unu açın:**

   [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mehmeteminyilmaz/Turk-Tarihi-AI-Chatbot/blob/main/chatbot.ipynb)

4. Colab üzerinde **Runtime -> Change Runtime Type -> T4 GPU** seçin.
5. Hücreleri sırasıyla çalıştırarak Gradio arayüzünü başlatın.

---

## 💬 Örnek Kullanım (Example Usage)

```text
Kullanıcı: Osmanlı'nın kuruluşundaki 'Gaza' ruhunun önemi nedir?

Bot: Osmanlı'nın kuruluşunda 'Gaza' ruhu, devletleşme döneminden sonra
     ülkenin genişlemesine yardımcı olmuştur. Bu durum, Osmanlı'nın
     genişlemesinin ve güçlenmesinin ana nedenlerinden biri olarak kabul edilir.

Kullanıcı: Malazgirt Savaşı'nın Türk tarihi açısından önemi nedir?

Bot: Malazgirt Savaşı, Türk tarihinde önemli bir dönüm noktası olarak kabul edilir.
     Bu savaştan sonra Anadolu'nun kapıları Türklere açılmıştır...
```

---

## 📁 Proje Yapısı (Project Structure)

```text
Turk-Tarihi-AI-Chatbot/
|-- chatbot.ipynb          # Ana Colab Notebook (Model Yükleme + Gradio UI)
|-- requirements.txt       # Gerekli Python paketleri
|-- README.md              # Proje dokümantasyonu
|-- LICENSE               # MIT Lisansı
|-- .gitignore             # Git tarafından yoksayılacak dosyalar
|-- images/
|   |-- chatbot_demo.png   # Gradio arayüz ekran görüntüsü
|   `-- architecture.png   # Model mimarisi diyagramı
|-- dataset/
|   `-- README.md          # Veri seti açıklaması
`-- model/
    `-- README.md          # Model ağırlıkları bilgisi
```

---

## 🤖 Model Ağırlıkları (Model Weights)

Model ağırlıkları boyutları nedeniyle (~3.5 GB) GitHub repository'sine doğrudan yüklenmemiştir.

- **Kendi Eğitiminizi Yapmak İçin:** `chatbot.ipynb` içerisindeki eğitim adımlarını çalıştırabilirsiniz (T4 GPU ile ~1-2 saat).
- **Eğitilmiş Ağırlıklara Erişim İçin:** [GitHub Issues](https://github.com/mehmeteminyilmaz/Turk-Tarihi-AI-Chatbot/issues) bölümünden talepte bulunabilirsiniz.

---

## 🛠️ Kullanılan Teknolojiler (Technologies Used)

- **Dil:** Python 3.10+
- **Derin Öğrenme:** PyTorch, Hugging Face Transformers, PEFT, Unsloth
- **Arayüz:** Gradio
- **Ortam:** Google Colab (T4 GPU), Google Drive

---

## 📄 Lisans (License)

Bu proje [MIT Lisansı](LICENSE) ile lisanslanmıştır.
