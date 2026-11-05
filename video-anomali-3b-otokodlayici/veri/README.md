# Veri setleri

Veri setleri lisans koşulları ve boyutları nedeniyle bu depoya konmamıştır. Notebook'lar aşağıdaki klasör yapısını bekler (Google Drive, `MyDrive/AnomalyProject/`):

```
AnomalyProject/
  model_90plus.pth                 ana model (tohum 42) — Releases bölümünden
  frames/
    avenue_train/                  Avenue eğitim videolarından alınan 7.658 kare (her 2. kare)
    ucf_normal/                    UCF-Crime: Normal_Videos_003, 006, 010
    ucf_fighting/                  UCF-Crime: Fighting003, Fighting018
    ucf_robbery/                   UCF-Crime: Stealing019   (klasör adı eskidir, içerik hırsızlıktır)
    ucf_accident/                  UCF-Crime: Burglary005   (klasör adı eskidir, içerik soygundur)
  data/
    Avenue_Dataset/
      training_videos/*.avi
      testing_videos/*.avi
  avenue_gt/testing_label_mask/    Avenue resmi kare etiketleri (yoksa 02 notebook'u indirir)
```

| Veri seti | Kaynak | Not |
|---|---|---|
| CUHK Avenue | Lu ve ark. (2013), CUHK resmi proje sayfası | Eğitim ve test videoları `data/Avenue_Dataset/` altına konur. |
| UCSD Ped2 | Mahadevan ve ark. (2010), UCSD SVCL sayfası | `02_tum_deneyler` otomatik indirir. |
| UCF-Crime | Sultani ve ark. (2018), UCF CRCV sayfası | Resmi test listesindeki 7 videodan, 10 karede bir alınmış kareler; kategori başına 350 kare. Dosya adı biçimi: `<önek>_<VideoAdı>_x264_<kare no>.jpg`. Kullanılan kare aralıkları makalenin Tablo 2'sindedir. |
| UR Fall | Kwolek ve Kepski (2014), resmi proje sayfası | Kamera 0, 40 ADL + 30 düşme videosu; `02_tum_deneyler` otomatik indirir. |
