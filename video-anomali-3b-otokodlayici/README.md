# Güvenlik Kamerası Videolarında 3B Evrişimli Otokodlayıcı ile Denetimsiz Anomali Tespiti ve Çapraz Veri Seti Genellenebilirliğinin Analizi

Bu depo, aynı adlı makalenin kodlarını içerir. Model yalnızca CUHK Avenue'nun normal videolarıyla eğitilmiş, UCSD Ped2, UCF-Crime ve UR Fall üzerinde test edilmiştir. Kontrol deneyleri (öğrenmesiz skorlar, aynı video içi testler) ve ablasyonlar, modelin farklı ortamlarda olaydan çok sahne görünümündeki farka duyarlı olduğunu göstermektedir.

*English summary:* Code for the paper "Unsupervised Anomaly Detection in Surveillance Videos with a 3D Convolutional Autoencoder and an Analysis of Cross-Dataset Generalization". A ~3.2M-parameter 3D convolutional autoencoder is trained only on normal CUHK Avenue videos and evaluated on Avenue, UCSD Ped2, UCF-Crime and UR Fall, with learning-free control scores, same-video tests and ablations.

## Yazarlar
Zehra Gündüz, Ayşe Sıla İnci — Yapay Zekâ ve Veri Mühendisliği Bölümü, Mühendislik Fakültesi, Fırat Üniversitesi

## Depo yapısı

```
notebooks/
  01_egitim.ipynb            Model eğitimi (tohum 7 / 2024, Ped2 ve ablasyon varyantları; RUN satırıyla seçilir)
  02_tum_deneyler.ipynb      Avenue, Ped2, UCF-Crime, UR Fall testleri, öğrenmesiz kontrol skorları,
                             eşikler, tohum özeti, bootstrap güven aralıkları, makaledeki şekil ve tablolar
  03_ablasyon.ipynb          Ablasyon tablosu ve çıkarım hızı ölçümü
  04_ek_analizler.ipynb      UCF-Crime kare aralıkları; Avenue'da model ile öğrenmesiz skorlar arasındaki
                             AUC farkı için video düzeyinde eşleştirilmiş bootstrap
  05_ucf_resmi_etiket.ipynb  UCF-Crime karelerinin resmi olay aralıklarıyla karşılaştırılması
sonuclar/                    Notebook'ların ürettiği tablolar ve sayılar (makaledeki değerler)
veri/README.md               Veri setlerinin nereden indirileceği ve klasör yapısı
requirements.txt
```

## Çalıştırma
Notebook'lar Google Colab için yazılmıştır (T4 GPU). Tüm yollar Google Drive'daki `MyDrive/AnomalyProject` klasörüne göredir; farklı bir konum kullanacaksanız her notebook'un başındaki `PROJ` değişkenini değiştirin.

1. Veri setlerini `veri/README.md`'deki yapıya göre Drive'a yerleştirin.
2. Ana model ağırlığını (`model_90plus.pth`, tohum 42) bu deponun **Releases** bölümünden indirip `AnomalyProject/` klasörüne koyun. Ya da `01_egitim.ipynb` içinde `RUN = 'avenue_seed42'` seçerek yeniden eğitin.
3. Diğer tohumlar ve ablasyonlar için `01_egitim.ipynb`'i her seferinde `RUN` satırını değiştirerek çalıştırın.
4. `02_tum_deneyler.ipynb` → `03_ablasyon.ipynb` → `04_ek_analizler.ipynb` → `05_ucf_resmi_etiket.ipynb` sırasıyla çalıştırın. Sonuçlar `AnomalyProject/revizyon_sonuclari_v2/` altına yazılır.

## Model ve eğitim ayarları
| Ayar | Değer |
|---|---|
| Giriş | 8 karelik pencere, 64×64 gri ton, [0, 1] |
| Mimari | 3B evrişimli kodlayıcı-çözücü, 3 seviyede atlama bağlantısı, 3.210.305 parametre |
| Kayıp | 0,8·MSE + 0,2·L1 |
| Optimizasyon | Adam (öğrenme oranı 5×10⁻⁴), CosineAnnealingWarmRestarts, 60 epoch, erken durdurma (sabır 15), parti boyutu 32 |
| Anomali skoru | Pencerenin ortalama yeniden yapılandırma hatası (MSE) |
| Eşik | Yalnızca normal doğrulama verisinden (P95, P99, ort.+2σ, ort.+3σ) |

## Atıf
Makale yayımlandığında künye buraya eklenecektir. Bu depoyu kullanırsanız lütfen `CITATION.cff` dosyasındaki bilgilerle atıf yapın.

## Lisans
Kodlar MIT lisansı ile paylaşılmıştır (`LICENSE`). Veri setleri bu depoya dahil değildir; her biri kendi sağlayıcısının kullanım koşullarına tabidir.
