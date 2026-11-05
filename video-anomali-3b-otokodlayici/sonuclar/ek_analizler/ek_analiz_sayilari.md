# Ek analizler (hocanın istedikleri)

## Madde 2 · UCF-Crime kare aralıkları

| Kategori             | Klasör       | Video                                 |   Kare sayısı |   İlk sayı |   Son sayı |   Adım (medyan) | Boşluk var mı   |
|:---------------------|:-------------|:--------------------------------------|--------------:|-----------:|-----------:|----------------:|:----------------|
| Normal               | ucf_normal   | ucf_ucf_normal_Normal_Videos_003_x264 |           283 |          0 |       2820 |              10 | hayır           |
| Normal               | ucf_normal   | ucf_ucf_normal_Normal_Videos_006_x264 |            45 |          0 |        440 |              10 | hayır           |
| Normal               | ucf_normal   | ucf_ucf_normal_Normal_Videos_010_x264 |            22 |          0 |       1050 |              10 | evet            |
| Kavga (Fighting)     | ucf_fighting | ucf_ucf_fighting_Fighting003_x264     |           311 |          0 |       3100 |              10 | hayır           |
| Kavga (Fighting)     | ucf_fighting | ucf_ucf_fighting_Fighting018_x264     |            39 |          0 |       1320 |              10 | evet            |
| Hırsızlık (Stealing) | ucf_robbery  | ucf_ucf_robbery_Stealing019_x264      |           350 |          0 |       4120 |              10 | evet            |
| Soygun (Burglary)    | ucf_accident | ucf_ucf_accident_Burglary005_x264     |           350 |          0 |       4120 |              10 | evet            |

Toplam 1400 kare, 7 video.

## Madde 3 · Avenue AUC farkı, video düzeyi eşleştirilmiş bootstrap

10000 tekrar, 21 test videosu iadeli örneklendi, model ve öğrenmesiz skor aynı videolar üzerinden karşılaştırıldı.

| Karşılaştırma                          |   Model AUC (%) |   Öğrenmesiz AUC (%) |   Fark (puan) |   %95 GA alt |   %95 GA üst |   Farkın ≤ 0 olduğu tekrar oranı |
|:---------------------------------------|----------------:|---------------------:|--------------:|-------------:|-------------:|---------------------------------:|
| Model − Avenue ortalama kareye uzaklık |           86.75 |                82.61 |          4.14 |        -2.4  |        11.24 |                           0.1146 |
| Model − Kare farkı enerjisi            |           86.75 |                81.27 |          5.48 |        -0.11 |        12.66 |                           0.0292 |
| Model − Optik akış büyüklüğü           |           86.75 |                80.43 |          6.32 |        -1.16 |        15.48 |                           0.0752 |
| Model − Kontrast sapması               |           86.75 |                55.33 |         31.42 |        18.66 |        44.08 |                           0      |
| Model − Parlaklık sapması              |           86.75 |                53.22 |         33.53 |        21.44 |        46.46 |                           0      |

### Makale için önerilen cümle (değerleri kontrol edin)

Model ile en iyi öğrenmesiz skor (Avenue ortalama kareye uzaklık) arasındaki AUC farkı 4,14 puandır (video düzeyinde eşleştirilmiş bootstrap, 10000 tekrar, %95 GA: -2,40 – 11,24).