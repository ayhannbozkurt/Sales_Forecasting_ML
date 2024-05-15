# Rossmann Mağazaları Satış Tahmin Projesi

Bu proje, Rossmann mağazaları için günlük satış tahminleri yapmayı amaçlamaktadır. Veri ön işleme, model eğitimi ve değerlendirme adımlarını içeren bu projede, farklı makine öğrenimi algoritmaları kullanılarak en iyi tahmin sonuçları elde edilmeye çalışılmıştır.

## İçindekiler

- [Giriş](#giriş)
- [Veri Seti](#veri-seti)
- [Ön İşleme Adımları](#ön-işleme-adımları)
- [Model Eğitimi ve Değerlendirme](#model-eğitimi-ve-değerlendirme)
- [Özellik Önem Düzeyleri](#özellik-önem-düzeyleri)
- [Sonuçlar](#sonuçlar)
- [Gelecek Çalışmalar](#gelecek-çalışmalar)
- [Kurulum](#kurulum)
- [Kullanım](#kullanım)
- [İndirme](#indirme)

## Giriş

Rossmann, Avrupa'nın yedi ülkesinde 3.000'den fazla mağazası olan büyük bir ilaç zinciridir. Bu proje, Rossmann mağazaları için günlük satış tahminleri yapmayı ve mağaza yöneticilerine daha iyi iş gücü planlaması yapmalarına yardımcı olmayı amaçlamaktadır.

## Veri Seti

Veri seti, Rossmann mağazalarının geçmiş satış verilerini içermektedir. Bu veriler, promosyonlar, tatiller, mağaza türleri ve daha birçok değişkeni kapsar.

## Ön İşleme Adımları

1. **Eksik Verilerin Tamamlanması**:
    - Simple Imputer kullanılarak eksik veriler ortalama, medyan veya en sık görülen değerlerle dolduruldu.
2. **Veri Ölçeklendirme**:
    - MinMaxScaler kullanılarak veriler 0 ile 1 arasında ölçeklendirildi.
3. **Kategorik Verilerin Kodlanması**:
    - OneHotEncoder kullanılarak kategorik değişkenler sayısal değerlere dönüştürüldü.

## Model Eğitimi ve Değerlendirme

Farklı makine öğrenimi algoritmaları kullanılarak modeller eğitildi ve değerlendirildi. Aşağıdaki fonksiyon, verilen modelin eğitim ve doğrulama hatalarını hesaplamak için kullanıldı:

```python
def try_model(model):
    # Fit the model
    model.fit(X_train, train_targets)
    
    # Generate predictions
    train_preds = model.predict(X_train)
    val_preds = model.predict(X_val)
    
    # Compute RMSE
    train_rmse = mean_squared_error(train_targets, train_preds, squared=False)
    val_rmse = mean_squared_error(val_targets, val_preds, squared=False)
    return train_rmse, val_rmse
```
Özellik Önem Düzeyleri
Özellik önem düzeyleri, modelin hangi özelliklere daha fazla dikkat ettiğini gösterir. Aşağıda en önemli 10 özelliği gösteren bir çubuk grafik yer almaktadır:

python
```python
sns.barplot(data=importance_df.head(10), x='importance', y='feature')
```

Sonuçlar
Günler ve Aylar: Pazar ve pazartesi günleri yüksek satışlar görülürken, Aralık ayında yılın en yüksek satışları gerçekleşmiştir.
Yıllık İstikrar: Satışlar yıllık bazda istikrarlı bir şekilde seyretmiştir.
Promosyon Etkisi: Promosyonların satışları önemli ölçüde artırdığı gözlemlenmiştir.
Gelecek Çalışmalar
Ek Özelliklerin Eklenmesi:
Hava durumu verileri, sosyal medya etkileşimleri ve ekonomik göstergeler gibi ek veriler kullanılabilir.
Gelişmiş Modelleme Teknikleri:
Hiperparametre optimizasyonu ve ansambl yöntemleri uygulanabilir.
Zaman Serisi Analizi:
Mevsimsellik ve trend analizleri için ARIMA ve Prophet modelleri kullanılabilir.
Modelin Gerçek Zamanlı Kullanımı:
Gerçek zamanlı tahminler ve otomatik raporlama sistemleri geliştirilebilir.
Kurulum
Proje ortamını kurmak için aşağıdaki adımları izleyin:

Gerekli kütüphaneleri yükleyin:

bash
Kodu kopyala
pip install -r requirements.txt
Veri setlerini indirin ve uygun dizine yerleştirin.

Kullanım
Projeyi çalıştırmak için Jupyter Notebook veya benzeri bir ortamda aşağıdaki adımları izleyin:

Veri setlerini yükleyin ve ön işleme adımlarını gerçekleştirin.
Modelleri eğitip değerlendirin.
Özellik önem düzeylerini analiz edin.
Sonuçları ve gelecekte yapılacak çalışmaları raporlayın.
İndirme
Proje dosyalarını ve veri setlerini indirmek için bu bağlantıyı kullanabilirsiniz.
