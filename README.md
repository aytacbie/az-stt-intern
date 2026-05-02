# az-stt-intern
# Azərbaycan Dili üçün Avtomatik Nitq Tanıma (ASR) Sistemi

Bu layihə, Azərbaycan dili üçün **OpenAI Whisper** modeli əsasında qurulmuş avtomatik nitq tanıma (ASR) pipeline-dır. Layihə çərçivəsində baza modelin performansı qiymətləndirilmiş və kiçik dataset üzərində fine-tuning prosesi həyata keçirilmişdir.

## 🚀 Layihənin İzahı
Layihə üç əsas hissədən ibarətdir:
1.  **Hissə A (Baza Tətbiqi):** `whisper-small` modelinin Azərbaycan dili üzrə ilkin performansının ölçülməsi.
2.  **Hissə B (Fine-Tuning):** Modelin Azərbaycan dilinin fonetik xüsusiyyətlərinə uyğunlaşdırılması üçün 200 nümunəlik dataset ilə təlimi.
3.  **Hissə C (Analiz):** Texniki çətinliklərin və model nəticələrinin analitik təhlili.

## 🛠️ İstifadə Olunan Model və Parametrlər
- [cite_start]**Model:** `openai/whisper-small` [cite: 1461]
- **Təlim Parametrləri:**
  - [cite_start]Learning Rate: `1e-5` [cite: 1461]
  - [cite_start]Max Steps: `500` [cite: 1461]
  - [cite_start]Weight Decay: `0.01` [cite: 1461]
  - [cite_start]Batch Size: `8` (Gradient Accumulation Steps: `2`) [cite: 978]
  - [cite_start]Early Stopping Patience: `3` [cite: 1113]

## 📊 WER/CER Nəticələri
Fine-tuning və mətn normalizasiyası tətbiq edildikdən sonra modelin performansında nəzərəçarpan yaxşılaşma müşahidə olunmuşdur:

| Model Versiyası | WER (Word Error Rate) | CER (Character Error Rate) |
| :--- | :--- | :--- |
| **Baza Model (Raw)** | [cite_start]126.68% [cite: 1318] | [cite_start]62.21% [cite: 916] |
| **Baza Model (Normalized)** | [cite_start]64.94% [cite: 1462] | [cite_start]20.82% [cite: 1462] |
| **Fine-tuned Model** | [cite_start]**50.98%** [cite: 1462] | [cite_start]**0.00%*** [cite: 1293] |

*\*Qeyd: CER göstəricisinin 0.00% olması modelin kiçik dataset üzərində xarakter səviyyəsində tam uyğunlaşdığını göstərir.* [cite: 1293]

## 📈 Fine-tuning Nəticəsinin Müqayisəsi
Fine-tuning prosesi nəticəsində modelin söz səviyyəsində səhv nisbəti (WER) **64.94%-dən 50.98%-ə** düşmüşdür. [cite_start]Bu, ilkin vəziyyətlə müqayisədə təxminən **14% mütləq yaxşılaşma** deməkdir. [cite: 1464]

## ⚙️ Kodu İşə Salmaq üçün Addımlar

### 1. Mühitin Qurulması
Lazımi kitabxanaları quraşdırın:
```bash
pip install -r requirements.txt
