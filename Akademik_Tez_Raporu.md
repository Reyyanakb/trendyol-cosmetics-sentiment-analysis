# E-Ticaret Kozmetik Sektöründe Müşteri Yorumlarının Doğal Dil İşleme (NLP) ile Duygu ve Kök Neden Analizi

## 1. Giriş
E-ticaret platformlarındaki tüketici yorumları, müşteri memnuniyetini ölçmek ve ürün gelişimine yön vermek açısından kritik bir veri kaynağıdır. Bu çalışmada, Türkiye'nin önde gelen e-ticaret platformlarından Trendyol üzerinde satılan kozmetik ürünlerine ait müşteri yorumları Doğal Dil İşleme (NLP) yöntemleriyle incelenmiştir. Araştırmanın temel amacı; farklı kozmetik kategorilerindeki müşteri memnuniyet oranlarını belirlemek ve en çok şikayet alan ürün grubunda yaşanan problemlerin kök nedenlerini (root causes) tespit etmektir.

## 2. Metodoloji

### 2.1. Veri Toplama (Data Collection)
Araştırma kapsamında Trendyol platformunda yer alan dört ana kozmetik kategorisine (Maskara, Fondöten, Güneş Kremi, Ruj) ait popüler ürün sayfalarından veri kazıma (web scraping) yöntemleriyle müşteri yorumları toplanmıştır. Çalışma kapsamında toplamda 60.873 adet yorumdan oluşan kapsamlı bir veri seti oluşturulmuştur.

### 2.2. Veri Ön İşleme (Data Preprocessing)
Makine öğrenmesi modellerinin metinleri doğru analiz edebilmesi amacıyla, elde edilen ham veri seti üzerinde detaylı bir temizleme süreci yürütülmüştür:
* **Gürültü Optimizasyonu:** Yorum içerisindeki web adresleri (URL), HTML etiketleri ve anlamsız özel karakterler temizlenmiştir.
* **Karakter Standardizasyonu:** Türkçe karakter yapısından kaynaklanan (örn. "I" ve "İ") büyük-küçük harf dönüştürme problemleri, kelimelerin anlamsal bütünlüğünü korumak adına manuel fonksiyonlarla standartlaştırılmıştır.
* **Düzenli İfadeler (Regex) ile Filtreleme:** Sadece harfler, rakamlar ve temel noktalama işaretleri (. , ! ?) veri setinde bırakılmış; emojiler ve semboller analiz dışı bırakılmıştır.

### 2.3. Duygu Analizi Sınıflandırması (Sentiment Analysis)
Veri setindeki yorumların "Olumlu", "Olumsuz" ve "Nötr" olarak etiketlenmesinde hibrit (iki aşamalı) bir sınıflandırma algoritması tercih edilmiştir:
1. **Derin Öğrenme Tabanlı Sınıflandırma:** İlk aşamada, Türkçe dil yapısı üzerinde eğitilmiş olan BERT (Bidirectional Encoder Representations from Transformers) tabanlı `savasy/bert-base-turkish-sentiment-v2` modeli kullanılmıştır. Model, metnin bağlamını analiz ederek ön bir duygu tahmini gerçekleştirmiştir.
2. **Kural Tabanlı (Lexicon) Yaklaşım:** Kozmetik sektörüne özgü terimlerin model tarafından yanlış sınıflandırılmasını önlemek adına kural tabanlı bir güvenlik ağı (fallback) kurulmuştur. Örneğin; "akıyor", "kırık", "dökülme" gibi kelimeler yüksek şikayet içermesine rağmen modelin "güzel akıyor" ifadesini olumlu algılama riskine karşı, bu kelimeleri barındıran ve düşük yıldız puanına (1-2) sahip yorumlar zorunlu olarak "Olumsuz" sınıfına atanmıştır.

### 2.4. Kök Neden Analizi (Root Cause Analysis)
Duygu analizi sonucunda en yüksek olumsuz yorum oranına sahip olduğu tespit edilen kategori üzerinde bir kök neden analizi uygulanmıştır.
* **Etkisiz Kelime (Stopwords) Eliminasyonu:** Türkçe bağlaçlar ve analiz değeri taşımayan dolgu kelimeleri (ve, ama, için, krem vb.) veri setinden çıkarılmıştır.
* **N-Gram Çıkarımı:** Kalan anlamlı kelimeler, Tekli (Unigram) ve İkili (Bigram) kelime öbekleri halinde gruplandırılarak frekans (sıklık) analizine tabi tutulmuştur.

## 3. Bulgular (Results)

### 3.1. Kategorik Duygu Analizi Dağılımı
Gerçekleştirilen duygu analizi sonucunda, incelenen dört farklı kategorinin müşteri memnuniyet ve şikayet oranları Tablo 1'de sunulmuştur.

| Kategori | Toplam Yorum | Olumlu Yorum (%) | Olumsuz Yorum (%) | Nötr Yorum (%) |
| :--- | :--- | :--- | :--- | :--- |
| **Ruj** | 20.200 | 20.037 (%99.19) | 73 (%0.36) | 90 (%0.45) |
| **Maskara** | 14.931 | 14.376 (%96.28) | 462 (%3.09) | 93 (%0.62) |
| **Fondöten** | 11.128 | 10.501 (%94.37) | 493 (%4.43) | 134 (%1.20) |
| **Güneş Kremi** | 14.614 | 13.332 (%91.23) | **997 (%6.82)** | 285 (%1.95) |
*Tablo 1: Kozmetik Kategorilerine Göre Duygu Dağılımı*

Tablo 1 incelendiğinde, müşteri memnuniyetinin en yüksek olduğu kategorinin **Ruj** (%99.19) olduğu, en fazla şikayet alan ürün grubunun ise **%6.82**'lik olumsuz yorum oranıyla **Güneş Kremi** kategorisi olduğu tespit edilmiştir.

### 3.2. Güneş Kremi Kategorisi Kök Neden Analizi Bulguları
%6.82'lik olumsuz oran ile en problemli kategori olan Güneş Kremleri için sadece negatif etiketli yorumlar üzerinden (n=997) frekans analizi (Unigram ve Bigram) yapılmıştır. Analiz sonucunda müşteri şikayetlerinin rastgele olmadığı, 6 spesifik kök nedene dayandığı kanıtlanmıştır:

1. **Beyazlık Bırakması (White Cast):** Formülasyonun cilt tarafından absorbe edilememesi ve yüzde beyaz bir kalıntı bırakmasıdır. En sık tekrar eden kelime grupları: *beyazlık bırakıyor* (f=48), *beyaz beyaz* (f=14).
2. **Komedojenik Etki (Sivilce/Akne Kusması):** Ürünlerin hassas veya akneye meyilli ciltlerde sivilcelenmeye (breakout) sebep olmasıdır. En sık tekrar eden kelimeler: *sivilce yaptı* (f=10), *sivilce* (f=52).
3. **Tekstür ve Emikilim Sorunu (Yağlı His):** Ürünlerin ciltte ağırlık ve parlama yapması, yağlı/yapışkan bir his (greasy feel) bırakmasıdır. Frekanslar: *yağlı his* (f=36), *aşırı yağlı* (f=29).
4. **Tekstil Boyanması (Sarı Leke):** Güneş filtrelerinin kıyafet yakalarında geri döndürülemez sarı lekeler oluşturmasıdır. Frekanslar: *sarı leke* (f=14), *leke bırakıyor* (f=17).
5. **Göz İritasyonu:** Yüz bölgesine uygulanan kremin göz bölgesinde yanma oluşturmasıdır. Frekanslar: *göz yakıyor* (f=14).
6. **Operasyonel Kusurlar (SKT Problemi):** Satıcılar tarafından Son Kullanma Tarihi (SKT) geçmiş ürünlerin sevk edilmesidir. Frekanslar: *kullanma tarihi* (f=29), *iade ettim* (f=18).

## 4. Sonuç ve Öneriler
Bu çalışma, e-ticaret müşteri yorumlarının Doğal Dil İşleme yöntemleriyle analiz edilmesinin ürün geliştirme (Ar-Ge) ve operasyonel iyileştirmeler için ne kadar hayati olduğunu ortaya koymaktadır. 
Duygu analizleri kozmetik ürünleri içinde renkli kozmetiğin (Ruj, Maskara) yüksek tatmin sağladığını gösterirken; cilt bakım bariyer ürünlerinde (Güneş Kremi) memnuniyetsizliğin arttığını göstermiştir. 

Güneş kremlerindeki olumsuz deneyimler büyük ölçüde kimyasal/fiziksel filtrelerin kimyasından (beyazlık, yağlanma, tekstil lekesi ve sivilce) kaynaklanmaktadır. Bu doğrultuda kozmetik üreticilerinin su bazlı (water-based), ciltte hızlı emilen ve göz yakmayan (tear-free) yeni nesil formülasyonlara yönelmesi gerekmektedir. Ayrıca, operasyonel boyutta tespit edilen "Tarihi geçmiş ürün" sorununun çözümü için satıcıların depo ve raf ömrü yönetimlerini sıkılaştırması önem arz etmektedir.
