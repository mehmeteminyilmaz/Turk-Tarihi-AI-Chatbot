# ğŸ“š Dataset

## Overview

The training dataset consists of **Turkish history question-answer pairs** curated for this project.

## ğŸ“‹ Dataset Format

Each training sample follows this instruction-tuning format:

```json
{
  "instruction": "OsmanlÄ± Ä°mparatorluÄŸu ne zaman kuruldu?",
  "input": "",
  "output": "OsmanlÄ± Ä°mparatorluÄŸu, 1299 yÄ±lÄ±nda Osman Bey tarafÄ±ndan SÃ¶ÄŸÃ¼t'te kurulmuÅŸtur..."
}
```

## ğŸ—‚ï¸ Categories

| Category | # Samples (approx.) | Topics |
|---|---|---|
| OsmanlÄ± Tarihi | â€” | KuruluÅŸ, padiÅŸahlar, yÃ¶netim, Ã§Ã¶kÃ¼ÅŸ |
| TÃ¼rkiye Cumhuriyeti | â€” | KuruluÅŸ, AtatÃ¼rk dÃ¶nemi, reformlar |
| SavaÅŸlar & Muharebeler | â€” | KurtuluÅŸ SavaÅŸÄ±, Ã‡anakkale, Balkan SavaÅŸlarÄ± |
| Tarihi Åahsiyetler | â€” | Biyografiler, dÃ¶neme katkÄ±larÄ± |
| Reformlar & Yenilikler | â€” | Tanzimat, MeÅŸrutiyet, cumhuriyet reformlarÄ± |

## ğŸ“¥ Data Sources

The dataset was compiled from the following sources:

- Turkish history textbooks (public domain)
- Wikipedia Turkish history articles
- Historical documents and encyclopedias
- Manually curated Q&A pairs

## âš ï¸ Usage Notes

- Dataset is intended for **educational and research purposes**
- Content focuses on **factual historical information**
- All sources are either public domain or properly attributed

## ğŸ”— Related Datasets

If you'd like to build on or extend this work, here are similar public datasets:

- [Turkish NLP Datasets](https://github.com/boun-tabi/turkish-nlp-resources)
- [Wikipedia TR Dump](https://dumps.wikimedia.org/trwiki/)
- [OPUS Turkish Corpora](https://opus.nlpl.eu/)

## ğŸ“§ Contact

If you would like access to the training dataset, please open a [GitHub Issue](https://github.com/mehmeteminyilmaz/Turk-Tarihi-AI-Chatbot/issues/new).

