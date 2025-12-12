# RoBERTa Kullanarak Twitter Verileri Üzerinde Çok Sınıflı Duygu Sınıflandırması
## FIFA Dünya Kupası 2022 Üzerine Bir Örnek Çalışma

## Proje Özeti
Bu proje, 2022 FIFA Dünya Kupası ile ilgili Twitter verileri üzerinde çok sınıflı duygu analizi gerçekleştirmeyi amaçlamaktadır. Tweet’ler pozitif, nötr ve negatif olmak üzere üç farklı duygu sınıfına ayrılmıştır.

Çalışmada, klasik makine öğrenimi yaklaşımlarının ötesine geçilerek transformer tabanlı derin öğrenme mimarisi olan RoBERTa kullanılmıştır. Amaç, bağlamsal anlamı daha iyi yakalayarak duygu sınıflandırma performansını artırmaktır.

---

## Motivasyon
Twitter gibi sosyal medya platformları, kamuoyunun duygu ve düşüncelerini yansıtan büyük ölçekli metin verileri üretmektedir. Ancak bu veriler genellikle gürültülü, kısaltmalar ve emojiler içeren ve anlamsal olarak belirsiz bir yapıya sahiptir.

Aynı veri seti üzerinde yapılan önceki çalışmalarda, geleneksel makine öğrenimi ve LSTM tabanlı modeller ile en fazla %73 doğruluk elde edilmiştir. Bu proje, transformer tabanlı derin öğrenme yöntemleri kullanarak bu başarımı aşmayı hedeflemektedir.

---

## Veri Seti
- Dosya adı: fifa_world_cup_2022_tweets.csv  
- Boyut: 22.000+ İngilizce tweet  
- Duygu Etiketleri: Pozitif, Nötr, Negatif  

Veri seti sütunları:
- Tweet: Ham tweet metni  
- Sentiment: Duygu etiketi (pozitif, nötr, negatif)

---

## Veri Ön İşleme
Veri seti üzerinde aşağıdaki ön işleme adımları uygulanmıştır:
- URL temizleme  
- Kullanıcı etiketlerinin (@username) kaldırılması  
- Hashtag ve özel karakter temizleme  
- Emoji → metin dönüştürme  
- Metin normalizasyonu (kısaltmaların düzeltilmesi)  
- Durak kelime (stopword) kaldırma  
- Lemmatizasyon  

Ön işleme sonrası veriler processed_tweets.csv dosyasına kaydedilmiştir.

---

## Model Mimarisi
- Temel Model: RoBERTa-base (önceden eğitilmiş)
- Altyapı: PyTorch ve HuggingFace Transformers
- Çıkış Katmanı: 3 sınıflı sınıflandırma başlığı
- Kayıp Fonksiyonu: Sınıf ağırlıklı CrossEntropyLoss
- Optimizasyon Algoritması: AdamW (öğrenme oranı = 3e-5)
- Epoch Sayısı: 6
- Batch Size: 16
- Cihaz: GPU (CUDA) mevcutsa, aksi takdirde CPU

---

## Değerlendirme Metrikleri
Model performansı aşağıdaki metrikler ile değerlendirilmiştir:
- Doğruluk (Accuracy)
- Precision
- Recall
- F1-skoru
- Karmaşıklık Matrisi (Confusion Matrix)

Nihai performans sonuçları:
- Doğruluk: %81.11
- F1 (Pozitif): 0.82
- F1 (Nötr): 0.75
- F1 (Negatif): 0.81

Model, literatürde raporlanan temel çalışmalara kıyasla yaklaşık %8 daha yüksek doğruluk elde etmiştir.

---

## Sonuçlar
- Pozitif ve negatif duygu sınıflarında güçlü sınıflandırma başarımı elde edilmiştir.
- Nötr duygu sınıfı, anlamsal belirsizlik nedeniyle en zor sınıf olarak gözlemlenmiştir.
- Karmaşıklık matrisi, sınıflar arası karışıklığın azaldığını göstermektedir.

---

## Karşılaştırmalı Analiz
- Random Forest (Temel Çalışma): %73.1
- Bi-LSTM: %73.0
- RoBERTa (Bu Çalışma): %81.11

---

## Çalıştırma Talimatları
1. Repoyu klonlayın.
2. Gerekli kütüphaneleri kurun:
pip install -r requirements.txt

3. Jupyter Notebook dosyasını çalıştırın:
deep_learning_sentiment_analysis.ipynb

---

## Gereksinimler
- Python 3.8+
- PyTorch
- Transformers
- Scikit-learn
- NLTK
- Emoji
- Matplotlib

---

## Yazar
Buğrahan Ata  
Bilgisayar Mühendisliği  
İstanbul Medeniyet Üniversitesi

---

## Not
Bu proje, Derin Öğrenme dersi kapsamında hazırlanmış akademik bir çalışmadır.
