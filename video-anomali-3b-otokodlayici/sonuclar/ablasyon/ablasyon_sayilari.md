# Ablasyon ve hız sonuçları (otomatik üretildi)

Tüm varyantlar seed 42 ile eğitildi; eşik, Avenue kare skoru ve test kurulumları 02 notebook'u ile aynı.

## Ablasyon (Ö1, Ö5)
| Varyant                |   Parametre |   Normal doğrulama MSE (×1e-5) |   Avenue mikro AUC % |   Avenue makro AUC % |   Avenue anomali/normal MSE oranı |   Avenue FPR P95 % |   Avenue→UCF-Crime AUC % |   Avenue→UR Fall ADL–düşme AUC % |   UR Fall aynı video içi AUC % |
|:-----------------------|------------:|-------------------------------:|---------------------:|---------------------:|----------------------------------:|-------------------:|-------------------------:|---------------------------------:|-------------------------------:|
| Tam (makaledeki model) |     3210305 |                           2.7  |                86.75 |                83.53 |                              2.66 |              10.39 |                    95.3  |                            87.13 |                          57.06 |
| Atlama bağlantısı yok  |     2629697 |                         122.99 |                87.27 |                83.83 |                              1.94 |               8.55 |                    76.27 |                            77.49 |                          65.83 |
| Yalnızca derin seviye  |     3072065 |                         124.93 |                87.14 |                85.02 |                              1.58 |               6.06 |                    91.73 |                            78.84 |                          62.37 |
| Veri artırma yok       |     3210305 |                           0.92 |                88.46 |                84.71 |                              3.26 |              10.85 |                    38.56 |                            43.77 |                          65.02 |
| Pencere 16 kare        |     3210305 |                           2.21 |                86.5  |                83.64 |                              2.43 |              10.05 |                    97.15 |                            93.02 |                          53.95 |

Not: "Normal doğrulama MSE" düşük ve "anomali/normal MSE oranı" 1'e yakınsa model girişi kopyalıyor demektir (özdeşlik kısayolu, Ö1).

## Hız (Ö9)
| Cihaz                |   Parti |   Gecikme (ms / parti) |   Pencere / sn |
|:---------------------|--------:|-----------------------:|---------------:|
| Tesla T4             |       1 |                  13.68 |           73.1 |
| Tesla T4             |      32 |                 363.19 |           88.1 |
| CPU (1 iş parçacığı) |       1 |                 676.15 |            1.5 |
| CPU (1 iş parçacığı) |      32 |                8329.97 |            3.8 |

Not: Kare okuma ve 64×64 küçültme süresi dahil değildir.