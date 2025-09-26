# Akbank-Derin-Orenme-Bootcamp

Ömer Can ESKİCİOĞLU

Proje dosyasında istenilen tüm şartlar sağlanmıştır.
Kaggle ve Google Colab yetersiz kaldığından dolayı eğitimde birkaç defa yarıda kesilmiştir.
Tensorboard ve Gradcam ayrı olarak çalıştırıldı. Sonuçlar kaggle sayfasında başarıyla kaydedilmişti. 
Eğitim hala devam etmektedir. Ancak haftalık kotamızda dolmak üzere. Bilginize Sunarız

# 📂 Proje Akışı
## Veri Keşfi
Klasör ve dosya boyutlarının incelenmesi
.jpg/.jpeg dosyalarının toplanıp:
Görsel yolu
Etiket (damage / no_damage)
Train / Validation / Test ayrımı
Dosya adından türetilen enlem–boylam bilgisi
Split (train/validation) ve etiket (damage/no_damage) dağılımlarının saçılım grafikleri
Örnek görsellerin grid halinde gösterilmesi
RGB histogramları ile renk kanal dağılımlarının incelenmesi
## Ön İşleme
Luma kanalına HE / AHE / CLAHE uygulanması
Görsellerin RMS kontrast ve Shannon entropi metrikleriyle değerlendirilmesi
Orijinal ve işlenmiş görsellerin yan yana karşılaştırılması
## Veri Artırma (Augmentation)
ImageDataGenerator ile özel preprocessing (he_preprocess)
Eğitim seti: dönüş, kaydırma, yakınlaştırma, yatay/dikey ayna, parlaklık ayarları
Validation & Test: yalnızca preprocessing
## Modelleme
EfficientNetB4 (ImageNet ön eğitimli) omurga
Katmanların bir kısmı donduruldu, son blok fine-tune edildi
Eklenen katmanlar:
Global Average Pooling
Batch Normalization
Dropout
L2 düzenlemeli Dense(256, ReLU)
Sigmoid çıkış (binary classification)
## Optimizasyon
Kayıp fonksiyonu: Binary Crossentropy
Optimizasyon: Adam / AdamW / SGD seçenekleri
Metrikler: Accuracy, AUC, Precision, Recall
## Hiperparametre Araması
Parametre uzayı tanımlanarak Random Search ile denemeler
Callback’ler:
TensorBoard (eğitimi izleme)
ModelCheckpoint (val AUC’e göre en iyi modeli best.keras olarak kaydetme)
EarlyStopping & ReduceLROnPlateau
Deneme sonuçları random_search_results.json dosyasına kaydedildi
En iyi konfigürasyon seçilip ek 10 epoch eğitim yapıldı
## Açıklanabilirlik (Explainability)
Son konvolüsyon katmanını bulan yardımcı fonksiyon ile Grad-CAM
Görsellerin üzerine ısı haritaları bindirilerek /kaggle/working/gradcam* klasörlerine kaydedildi
## Değerlendirme
Test seti üzerinde classification report (precision, recall, f1-score)
Confusion Matrix (ham ve normalize edilmiş halleri)
Hata profilleri sınıf bazında analiz edildi

# 📊 Sonuçlar
Eğitim ve doğrulama metrikleri TensorBoard ile izlendi
En iyi model AUC skoruna göre seçildi
Test setinde ayrıntılı classification report ve confusion matrix üretildi
Grad-CAM görselleri ile model kararları görselleştirildi
