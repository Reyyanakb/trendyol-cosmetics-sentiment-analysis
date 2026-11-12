# Trendyol Kozmetik Ürünleri Müşteri Yorumları Duygu Analizi ve Kök Neden Raporu

Bu rapor, dört farklı kozmetik kategorisindeki (Maskara, Fondöten, Güneş Kremi, Ruj) müşteri yorumlarının duygu analizi sonuçlarını ve en yüksek memnuniyetsizlik oranına sahip kategori olan "Güneş Kremi" için yapılan kök neden analizini içermektedir.

## 1. Kategorilere Göre Duygu Analizi Dağılımı

Toplam 60.873 müşteri yorumu üzerinde yapılan duygu durumu (sentiment) analizi sonuçlarına göre kategorilerin memnuniyet oranları aşağıda listelenmiştir:

| Kategori | Toplam Yorum | Olumlu Yorum (%) | Olumsuz Yorum (%) | Nötr Yorum (%) |
| :--- | :--- | :--- | :--- | :--- |
| **Ruj** | 20.200 | 20.037 (%99.19) | 73 (%0.36) | 90 (%0.45) |
| **Maskara** | 14.931 | 14.376 (%96.28) | 462 (%3.09) | 93 (%0.62) |
| **Fondöten** | 11.128 | 10.501 (%94.37) | 493 (%4.43) | 134 (%1.20) |
| **Güneş Kremi** | 14.614 | 13.332 (%91.23) | **997 (%6.82)** | 285 (%1.95) |

> [!NOTE]
> Sonuçlara göre en yüksek müşteri memnuniyetine sahip kategori **Ruj** iken, en fazla şikayet alan ve olumsuz yorum oranına sahip kategori **Güneş Kremi** olarak tespit edilmiştir.

---

## 2. Güneş Kremi Kategorisi Kök Neden Analizi (Root Cause Analysis)

Güneş Kremi kategorisindeki %6.82'lik olumsuz yorum oranı mercek altına alınarak, sadece "Olumsuz" olarak etiketlenmiş 997 adet yorum üzerinde Doğal Dil İşleme (NLP) teknikleriyle kelime frekansı (Unigram) ve ikili kelime grubu (Bigram) analizi gerçekleştirilmiştir.

Müşterilerin şikayetçi olduğu temel problemler 6 ana başlıkta toplanmıştır:

### A. Beyazlık Bırakması (White Cast)
Güneş kremlerinin ciltte tam olarak emilmemesi ve yüzde beyaz bir tabaka bırakması en sık karşılaşılan formülasyon sorunudur.
* **Sık Geçen Kelime Grupları:** `beyazlık bırakıyor` (48 kez), `beyaz beyaz` (14 kez)
* **Örnek Müşteri İfadesi:** *"Beyazlık bırakıyor ve göz yakmıyor diye almıştım ama göz yakıyor"*

### B. Aşırı Yağlı ve Yapışkan His
Ürünlerin ciltte ağırlık yapması, parlama yapması ve yağlı/yapışkan bir doku bırakması kullanıcıların günlük kullanımını zorlaştıran ikinci temel etkendir.
* **Sık Geçen Kelime Grupları:** `yağlı his` (36 kez), `his bırakıyor` (35 kez), `aşırı yağlı` (29 kez), `yapış yapış` (17 kez)

### C. Kıyafetlerde Çıkmayan Sarı Lekeler
Güneş kremlerinin temas ettiği tişört veya yakalarda çıkması çok zor olan sarı lekeler bırakması, ciddi bir ürün iade sebebidir.
* **Sık Geçen Kelime Grupları:** `sarı leke` (14 kez), `leke bırakıyor` (17 kez)
* **Örnek Müşteri İfadesi:** *"Koruyuculuğu çok iyi fakat sürüldükten sonra giyilen kıyafetin rengini sarartıyor ve çıkmıyor maalesef."*

### D. Akne ve Sivilce Oluşumu
Özellikle hassas veya akneye meyilli cilt tipine sahip kullanıcıların (ürün komedojenik değil vaadiyle satılsa dahi) sivilcelenme problemi yaşamasıdır.
* **Sık Geçen Kelime Grupları:** `sivilce yaptı` (10 kez), `sivilce` (52 kez)
* **Örnek Müşteri İfadesi:** *"...Bir de yüzümde çok fazla sivilceye neden oldu"*

### E. Son Kullanma Tarihi ve Operasyonel Sorunlar
Satıcılar tarafından son kullanma tarihi (SKT) geçmiş, tarihi silinmiş veya bitmesine çok az kalmış ürünlerin gönderilmesidir.
* **Sık Geçen Kelime Grupları:** `kullanma tarihi` (29 kez), `tarihi geçmiş` (10 kez), `iade ettim` (18 kez)

### F. Göz Yanması
Özellikle yüze sürülen güneş kremlerinin göz çevresine yaklaştığında veya terlemeyle göze akması durumunda yoğun bir yanma hissi oluşturmasıdır.
* **Sık Geçen Kelime Grupları:** `göz yakıyor` (14 kez)

---

## 3. Sonuç ve Değerlendirme

* **Formülasyon İyileştirmeleri:** Güneş kremlerindeki olumsuz müşteri deneyimi ağırlıklı olarak kimyasal/fiziksel filtrelerin yapısından kaynaklanmaktadır. Tüketiciler, beyazlık bırakmayan (no white-cast), hızlı emilen (yağsız/su bazlı his), kıyafet lekelemeyen ve göz yakmayan yeni nesil formüllere yönelmektedir.
* **Satıcı Performansı:** SKT kontrolünün depo süreçlerinde daha iyi yönetilmesi, "Tarihi geçmiş ürün" şikayetlerini ve operasyonel iade maliyetlerini sıfıra indirecektir.
