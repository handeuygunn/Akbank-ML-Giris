# Araç Satış Fiyatı Tahmini – Decision Tree Regressor ile

Bu projede, araç satış verilerini analiz ederek satış fiyatlarını tahmin eden bir regresyon modeli geliştirdim. Karar ağacı (Decision Tree Regressor) algoritmasını kullanarak, farklı özelliklerin satış fiyatı üzerindeki etkisini inceledim ve en uygun hiperparametreleri `RandomizedSearchCV` ile belirledim.

## Projenin Amacı

Amaç, çeşitli araç özelliklerine (yıl, marka, km, kondisyon, MMR vs.) göre ikinci el araçların satış fiyatlarını olabildiğince doğru bir şekilde tahmin etmekti. Böylece hem pazar eğilimlerini daha iyi anlamak hem de gelecekteki satış fiyatlarını öngörebilen bir model oluşturmak istedim.

## Kullandığım Veri

Veri seti [Kaggle](https://www.kaggle.com/datasets/syedanwarafridi/vehicle-sales-data) üzerinden alındı. Bu veri setinde araçlara ait aşağıdaki gibi birçok değişken yer alıyor:

- year
- make
- model
- body
- transmission
- condition
- odometer
- mmr (Market Mean Retail)
- sellingprice
- saledate

## Adım Adım Yaptıklarım

### 1. Veri Yükleme ve Temizleme
- CSV dosyasını pandas ile içe aktardım.
- Eksik verileri kontrol edip, `dropna()` ile sildim.
- Satış tarihi gibi sütunları analiz için hazırladım.

### 2. Görselleştirme
Verilerin ilişkilerini daha iyi anlamak için aşağıdaki grafik türlerini kullandım:
- `year` vs. `sellingprice` scatter plot
- `odometer` vs. `sellingprice` scatter plot
- Marka bazlı satış fiyatı dağılımları (Top 10)
- `transmission` ve `condition` için boxplot
- Zaman serisi grafiği ile zamanla fiyat değişimi

### 3. Özellik Ölçekleme ve Kodlama
- Sayısal değişkenleri `StandardScaler` ile normalize ettim.
- `make`, `model`, `transmission`, `body` gibi kategorik sütunları one-hot encoding yöntemiyle dönüştürdüm.
- Ortaya çıkan yüksek boyutlu veri çerçevesi (`df_final`) yaklaşık 900 sütun içeriyordu.

### 4. Modelleme: Decision Tree Regressor
- Skor metriği olarak RMSE (Root Mean Squared Error) kullandım.
- `RandomizedSearchCV` ile hiperparametre optimizasyonu gerçekleştirdim:
  - `max_depth`
  - `min_samples_split`
  - `min_samples_leaf`
  - `criterion` (squared_error, absolute_error)
- `cv=5` ile çapraz doğrulama uyguladım.
- Eğitim sonrasında en iyi modeli test verisi üzerinde kullanarak RMSE değerini hesapladım.

### 5. Sonuç
Modelimin RMSE değeri oldukça düşüktü. Bu da modelin test verisinde düşük hata ile tahmin yaptığını gösteriyor. Ancak tüm özelliklerin one-hot encoded olması nedeniyle overfitting riskini de göz önünde bulundurdum. Gerekirse `SelectKBest` gibi yöntemlerle boyut indirgeme planlıyorum.

## Kullanılan Kütüphaneler

- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- scipy

## Çalıştırmak İçin

1. Gerekli kütüphaneleri yükle:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

2. `decisiontreeregression-price-predict.ipynb` dosyasını Jupyter Notebook veya Kaggle üzerinde aç.

3. Dosyayı satır satır çalıştırarak süreci takip et.

## Geliştirme Fikirleri

- Random Forest ve XGBoost ile model karşılaştırması yapılabilir.
- Özellik seçimi (feature selection) uygulanarak model daha hızlı ve daha az ezberleyen hale getirilebilir.
- Web arayüzü ile kullanıcıdan araç bilgileri alınıp fiyat tahmini yapılabilir.

## Lisans

Bu proje açık kaynak olup, kişisel ve akademik kullanıma uygundur.
