
# 🚗 Vehicle Sales Price Analysis & Prediction

Bu proje, araç satış verilerinin analiz edilmesi, çeşitli özniteliklerin fiyat üzerindeki etkisinin incelenmesi ve nihayetinde araç fiyatlarını tahmin eden bir makine öğrenimi modelinin geliştirilmesini amaçlamaktadır.

## 📁 Proje İçeriği

### 1. Veri Seti
Veri, Kaggle üzerinden indirilen bir araç satış verisidir:

- Kaynak: [`syedanwarafridi/vehicle-sales-data`](https://www.kaggle.com/datasets/syedanwarafridi/vehicle-sales-data)
- Yerel olarak `"car_prices.csv"` dosyası kullanılmıştır.

### 2. Veri Temizleme

- Eksik veriler tespit edildi ve silindi.
- Tarih, kilometre (odometer), araç yılı, araç kondisyonu ve MMR gibi değişkenler analiz için temizlendi.

### 3. Görselleştirmeler

- Yıl-Satış Fiyatı
- KM-Satış Fiyatı
- Marka-Satış Fiyatı (Top 10 Marka)
- Şanzıman Tipi-Satış Fiyatı
- Kondisyon-Satış Fiyatı
- MMR (bazaar değeri)-Satış Fiyatı
- Zaman serisi üzerinde satış fiyatlarının değişimi

Görselleştirmeler için `matplotlib` ve `seaborn` kütüphaneleri kullanıldı.

### 4. Özellik Mühendisliği

- Sayısal değişkenler (`year`, `condition`, `odometer`, `mmr`, `sellingprice`) `StandardScaler` ile normalize edildi.
- Kategorik değişkenler (`make`, `model`, `body`, `transmission`) one-hot encoding ile dönüştürüldü.
- Az önemli olan `trim`, `color`, `seller` gibi sütunlar çıkarıldı.

### 5. Modelleme

Modelleme kısmı kodun ilerleyen bölümlerinde yer alıyor (yüklemenin devamında olabilir). Şu ana kadarki hazırlıklar, regresyon tabanlı bir tahmin modeli için temel oluşturuyor.

## 🛠 Kullanılan Kütüphaneler

- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `sklearn`
- `kagglehub`

## 🚀 Başlatmak için

1. Gerekli kütüphaneleri yükleyin:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn kagglehub
```

2. Veriyi çekmek için:

```python
import kagglehub
path = kagglehub.dataset_download("syedanwarafridi/vehicle-sales-data")
```

3. `main.ipynb` dosyasını Jupyter Notebook veya VS Code üzerinde çalıştırarak analiz sürecini adım adım takip edebilirsiniz.

## 📌 Notlar

- Categorical encoding sırasında yüksek boyutluluk (curse of dimensionality) problemi göz önünde bulundurulmuştur.
- Hafıza hatalarını önlemek için bazı sütunlar dışarıda bırakılmıştır.
- Proje ilerletilerek regresyon modelleriyle fiyat tahmini yapılabilir (Random Forest, XGBoost, vs.).

## 🧠 Geliştirici Notları

- Bu proje bir veri bilimi bootcamp projesi kapsamında gerçekleştirilmiştir.
- Gerçek dünyada uygulanabilir bir araç fiyatlandırma modeli geliştirmeyi hedeflemektedir.
