# az-stt-intern
Azərbaycan Dili üçün Nitq Tanıma Sistemi
Bu layihə Azərbaycan dili üçün Whisper modeli əsasında qurulmuş ASR pipeline-dır.

## Layihənin İzahı
Tapşırıq çərçivəsində OpenAI Whisper-small modeli Azərbaycan dili üçün Fine-tune edilmişdir.

## WER/CER Nəticələri
| Model | WER (%) | CER (%) |
|-------|---------|---------|
| Baza Model (Baseline) | 64.94% | 20.82% |
| Fine-tuned Model | 50.98% | 0.00% |

## İdarəetmə və Qurulum
1. Kitabxanaları quraşdırın: "pip install -r requirements.txt"
2. Baza tətbiqi üçün: "part_a/" qovluğundakı kodları işə salın.
3. Fine-tuning üçün: "part_b/" qovluğundakı təlim skriptini işə salın.

## Təlim Gedişatı
Training Loss və WER inkişaf qrafikləri "results/" qovluğunda yerləşdirilmişdir.
