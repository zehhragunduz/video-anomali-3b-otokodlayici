# UCF-Crime · resmi olay aralıklarıyla karşılaştırma

| Kategori             | Video                  |   Videonun toplam karesi | Resmi olay aralığı   | Kullanılan kare aralığı   |   Kullanılan kare | Olay içinde   | Olay dışında   |
|:---------------------|:-----------------------|-------------------------:|:---------------------|:--------------------------|------------------:|:--------------|:---------------|
| Normal               | Normal_Videos_003_x264 |                     2822 | — (normal)           | 0–2820                    |               283 | —             | —              |
| Normal               | Normal_Videos_006_x264 |                      450 | — (normal)           | 0–440                     |                45 | —             | —              |
| Normal               | Normal_Videos_010_x264 |                     1053 | — (normal)           | 0–1050                    |                22 | —             | —              |
| Kavga (Fighting)     | Fighting003_x264       |                     3102 | 1820–3103            | 0–3100                    |               311 | 129           | 182            |
| Kavga (Fighting)     | Fighting018_x264       |                     1389 | 80–420               | 0–1320                    |                39 | 4             | 35             |
| Hırsızlık (Stealing) | Stealing019_x264       |                     4911 | 2730–2790, 4170–4350 | 0–4120                    |               350 | 7             | 343            |
| Soygun (Burglary)    | Burglary005_x264       |                     7729 | 4710–5040            | 0–4120                    |               350 | 0             | 350            |

Anomali etiketli 1050 karenin 140 tanesi resmi olay aralığında.

| Kategori             |   iki video karışık |   karışık |   normal |   olay |   olay dışı |
|:---------------------|--------------------:|----------:|---------:|-------:|------------:|
| Hırsızlık (Stealing) |                   0 |         7 |        0 |      0 |         165 |
| Kavga (Fighting)     |                   4 |        69 |        0 |     18 |          81 |
| Normal               |                   7 |         0 |      165 |      0 |           0 |
| Soygun (Burglary)    |                   0 |         0 |        0 |      0 |         172 |

Zaman sırası bozuk sekans oranı: %72.1

| Karşılaştırma                                                              |   AUC (%) |   Negatif sekans |   Pozitif sekans |
|:---------------------------------------------------------------------------|----------:|-----------------:|-----------------:|
| Makaledeki kurulum: normal videolar vs anomali videolarının tüm sekansları |     98.7  |              165 |              516 |
| Resmi etiket: normal videolar vs yalnızca olay sekansları                  |     98.75 |              165 |               18 |
| Normal videolar vs anomali videolarının olay DIŞI sekansları               |     98.48 |              165 |              418 |
| Aynı video içi: olay dışı vs olay sekansları                               |     55.74 |              418 |               18 |
| Aynı video içi, yalnızca Fighting003_x264                                  |     64.47 |               76 |               18 |