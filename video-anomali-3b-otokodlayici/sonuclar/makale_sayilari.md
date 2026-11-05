# Makaleye girecek sayılar (otomatik üretildi — elle değiştirmeyin, notebook'u yeniden çalıştırın)

## Protokol
- Eşik: yalnızca Avenue doğrulama kümesindeki 382 normal sekanstan; ana eşik P95 = 5.16e-05 (P99 = 1.24e-04).
- Avenue test pencereleri: 8 kare, pencere içi kare aralığı 2 (eşleştirme: medyan adım 2, eşleşme hatası medyanı 2.2e-06, adımların %100'ı 2); kare skoru = onu içeren pencerelerin ortalaması.
- Avenue→UCF-Crime: 172 normal + 516 anomali sekansı (tamamı, alt örnekleme yok).
- Önceki sürümdeki fall_test klasörü çıkarıldı (600 ADL karesi anomali etiketliydi). Düşme testi kare etiketli UR Fall ile yapıldı.
- Kategori adları düzeltildi: ucf_robbery = Stealing (hırsızlık), ucf_accident = Burglary (soygun), kaza değil.

## K2 — Avenue resmi test kümesi (21 video, kare düzeyi)
- Mikro AUC: %86,75 (%95 GA, video bootstrap: 81,01–91,31)
- Makro AUC: %83,53; video bazında min-max ile mikro AUC: %79,42
- Ped2 mikro AUC: %70,70 (makro %89,96)

## Avenue → UCF-Crime
- ROC-AUC %95,30 (%95 GA, video düzeyi: 77,21–100,00); PR-AUC %96,97 (anomali oranı %75 olduğu için yüksek)
- Dengeli alt küme (10 çekiliş): %95,25 ± 0,11
- Kavga (Fighting): AUC %95,46, tespit P95 %100,00, P99 %88,95
- Hırsızlık (Stealing): AUC %96,22, tespit P95 %100,00, P99 %100,00
- Soygun (Burglary): AUC %94,21, tespit P95 %100,00, P99 %99,42
- Normal yanlış alarm: P95 %30,81, P99 %8,14
- Karışıklık matrisi (P95): gerçek normal → 119 doğru / 53 yanlış alarm; gerçek anomali → 516 tespit / 0 kaçırılan

## Avenue → UR Fall (kare etiketli, 40 ADL + 30 düşme videosu)
- ADL–düşme anı AUC (K1-a): %87,13 (%95 GA, video bootstrap: 80,07–93,27)
- Aynı düşme videosu içinde düşme öncesi–düşme anı AUC (K1-b): %57,06
- P95: ADL yanlış alarm %77,93, düşme recall %99,44 | P99: yanlış alarm %28,28, recall %95,32

## K1 — Kontrol deneyleri (AUC %)
| Yöntem                         |   Avenue (alan içi, kare) AUC % |   Avenue→UCF-Crime AUC % |   Avenue→UR Fall ADL–düşme AUC % (K1-a) |   UR Fall aynı video içi AUC % (K1-b) |
|:-------------------------------|--------------------------------:|-------------------------:|----------------------------------------:|--------------------------------------:|
| 3B otokodlayıcı (seed42)       |                           86.75 |                    95.3  |                                   87.13 |                                 57.06 |
| Kare farkı enerjisi            |                           81.27 |                    81.53 |                                   70    |                                 73.66 |
| Optik akış büyüklüğü           |                           80.43 |                    78.74 |                                   71.18 |                                 73.17 |
| Parlaklık sapması              |                           53.22 |                    10.66 |                                   52.3  |                                 66.39 |
| Kontrast sapması               |                           55.33 |                    18.54 |                                   15.05 |                                 52.51 |
| Avenue ortalama kareye uzaklık |                           82.61 |                    17.54 |                                   87.34 |                                 71.5  |

## K5 — Seed özeti
                             Metrik  seed42  seed7  seed2024 Ortalama ± std
                 Avenue mikro AUC %   86.75  87.10     86.85   86.90 ± 0.15
                 Avenue makro AUC %   83.53  83.80     83.21   83.51 ± 0.24
                UCF-Crime ROC-AUC %   95.30  98.60     96.62   96.84 ± 1.36
                 UCF-Crime PR-AUC %   96.97  99.50     98.13   98.20 ± 1.03
       UCF-Crime yanlış alarm P95 %   30.81  76.16     71.51  59.50 ± 20.37
             UCF-Crime recall P95 %  100.00 100.00    100.00  100.00 ± 0.00
       UCF-Crime yanlış alarm P99 %    8.14  10.47      9.88    9.50 ± 0.99
             UCF-Crime recall P99 %   96.12  99.22     97.48   97.61 ± 1.27
     UR Fall ADL–düşme AUC % (K1-a)   87.13  83.11     88.09   86.11 ± 2.16
UR Fall aynı video içi AUC % (K1-b)   57.06  53.08     59.18   56.44 ± 2.53
         UR Fall yanlış alarm P95 %   77.93  64.34     46.55  62.94 ± 12.85
               UR Fall recall P95 %   99.44 100.00    100.00   99.81 ± 0.26
         UR Fall yanlış alarm P99 %   28.28  43.81     39.23   37.11 ± 6.52
               UR Fall recall P99 %   95.32 100.00     97.55   97.62 ± 1.91

## Şekil E alt yazı değerleri
Avenue video 4 — normal kare: sekans MSE = 2.25e-05, eşiğin 0.44 katı
Avenue video 4 — anomali karesi: sekans MSE = 9.51e-05, eşiğin 1.84 katı
Normal (medyan skorlu sekans): sekans MSE = 4.69e-05, eşiğin 0.91 katı
Kavga (Fighting) (medyan skorlu sekans): sekans MSE = 2.38e-04, eşiğin 4.61 katı
Hırsızlık (Stealing) (medyan skorlu sekans): sekans MSE = 2.22e-04, eşiğin 4.30 katı
Soygun (Burglary) (medyan skorlu sekans): sekans MSE = 1.77e-04, eşiğin 3.44 katı