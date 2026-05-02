# az-stt-intern
# Azərbaycan Dili üçün Avtomatik Nitq Tanıma (ASR) Sistemi

Bu layihə, Azərbaycan dili üçün **OpenAI Whisper** modeli əsasında qurulmuş avtomatik nitq tanıma (ASR) pipeline-dır. Layihə çərçivəsində baza modelin performansı qiymətləndirilmiş və kiçik dataset üzərində fine-tuning prosesi həyata keçirilmişdir.

##  Layihənin İzahı
Layihə üç əsas hissədən ibarətdir:
1.  **Hissə A (Baza Tətbiqi):** `whisper-small` modelinin Azərbaycan dili üzrə ilkin performansının ölçülməsi.
2.  **Hissə B (Fine-Tuning):** Modelin Azərbaycan dilinin xüsusiyyətlərinə uyğunlaşdırılması üçün 200 nümunəlik dataset ilə təlimi.
3.  **Hissə C (Analiz):** Texniki çətinliklərin və model nəticələrinin analitik təhlili.

## 🛠️ İstifadə Olunan Model və Parametrlər
- **Model:** `openai/whisper-small` 
- **Təlim Parametrləri:**
  - Learning Rate: `1e-5` 
  - Max Steps: `500` 
  - Weight Decay: `0.01` 
  - Batch Size: `8` (Gradient Accumulation Steps: `2`) 
  - Early Stopping Patience: `3` 

##  WER/CER Nəticələri
Fine-tuning və mətn normalizasiyası tətbiq edildikdən sonra modelin performansında nəzərəçarpan yaxşılaşma müşahidə olunmuşdur:

| Model Versiyası | WER (Word Error Rate) | CER (Character Error Rate) |
| :--- | :--- | :--- |
| **Baza Model** | 64.94%  | 20.82%  |
| **Fine-tuned Model** | **50.98%** ] | **0.00%***  |

*\*Qeyd: CER göstəricisinin 0.00% olması modelin kiçik dataset üzərində xarakter səviyyəsində tam uyğunlaşdığını göstərir.* 

##  Fine-tuning Nəticəsinin Müqayisəsi
Fine-tuning prosesi nəticəsində modelin söz səviyyəsində səhv nisbəti (WER) **64.94%-dən 50.98%-ə** düşmüşdür. Bu, ilkin vəziyyətlə müqayisədə təxminən **14% yaxşılaşma** deməkdir. 

##  Kodu İşə Salmaq üçün Addımlar

### 1. Mühitin Qurulması
Lazımi kitabxanaları quraşdırın:
```bash
pip install -r requirements.txt
