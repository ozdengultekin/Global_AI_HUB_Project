# Health and Fitness Project
# Giriş

Bu repo, Global AI Hub  Makine Öğrenmesine Giriş Bootcamp ı  sürecinde bitirme projesini sunmak amacıyla  oluşturulmuştur.

## Veri Seti Hakkında Genel Bilgi

Veri Seti https://www.kaggle.com/datasets/evan65549/health-and-fitness-dataset linkten alınmıştır. Değişkenlerle ilgili açıklamaları belirttiğim linkten inceleyebilirsiniz. Health_fitness_dataset, 3.000 katılımcının 2024 yılına ait gerçek sağlık ve fitness izleme verilerini içermektedir. Veri seti 687701 satırdan oluşmaktadır.  

Bu veri kümesi günlük aktiviteleri, önemli sağlık göstergelerini ve yaşam tarzı faktörlerini içermektedir.  

Projenin amacı, 

Makine Öğrenmesinin bir türü olan gözetimli öğrenme ile  yeni gelen kullanıcının girmiş olduğu bilgilere göre; 1 gün içerisinde yaptığı spor ve mevcut sağlık durumuna göre sağlık seviyesini matematiksel olarak  hesaplamaktır. 

Makine Öğrenmesinin bir türü olan gözetimli öğrenme  ile mevcut veri setindeki kişilerin günlük sağlık ve spor alışkanlıklarını belirten değişkenlerin ortalama değerleriyle yeni veri seti oluşturulmuştur. Sisteme yeni dahil olmuş kişinin belirlediğimiz değişkenlerin ortalama değerlerini girmesini bekliyoruz.  Bu yeni verilere göre, yeni kişinin hangi spor ve sağlık grubuna dahil olduğunu bulmak temel hedefimizi oluşturmaktadır.


# Metrikler

## 1. Gözetimli Öğrenmede Kullanılan Metrikler  

   Model: Random Forest Regressor ile GPU destekli XGBoost Regressor  
   
   Model Optimizasyonu: RandomizedSearchCV(Veri seti büyükdere olduğundan eğitilmesi uzun süreceğinden seçilmiştir. Ancak MSE değerlerini iyileştirmede etkisi olmamıştır.) 3-fold cross-validation modelin genelleme kabiliyetini yükseltmek için uygulanmıştır.  
   
   Model Değerlendirme Metrikleri: MSE,MAE,RMSE, R2 skorları hesaplanmıştır.Tüm sonuçlar ile ilgili genel bir değerlendirme yapılmıştır.  
   
## 2. Gözetimsiz Öğrenmede Kullanılan Metrikler  

   Aykırı Değer Analizi: IQR yöntemi kullanılmıştır. K-means kümeleme de uzaklık temelli bir algoritma(öklidiyen) kullandığından mutlaka aykırı değerler elimine edilmelidir. 
   
   Standartlaştırma: MinMaxScaler Veri setimizin her değişkeninin aralıkları birbirinden çok farklı aralıklardadır.  MinMaxScaler bu değişken aralıklarını 0-1 aralığında  sınırlandırarak kümeleme performansını arttırmıştır. 
   
   Model: K-Means
   
   Model Optimizasyonu: Kümeleme optimizasyonu için elbow(dirsek) yöntemi kullanılmıştır. Bu yöntemle elde ettiğimiz küme sayısı veriyi iyi gruplandırmamıştır.
   
   PCA: Kümelediğimiz veri setini daha düzgün bir şekilde görüntülemek adına kullanıldı. Çünkü Temel bileşenler analizi(PCA) bilgiyi en fazla taşıyan değişkenlerle grafiği temsil eder.    
   silhouette_score: Elbow yöntemiyle  optimize edilmiş kümeleme sayısı ile kümeleme başarısı değerlendirilmiştir.  

# Sonuç ve Gelecek Çalışmalar  

## 1. Gözetimli Öğrenme için Sonuçlar:  
3000 kişinin günlük sağlık verileri baz alınarak, yeni bir kullanıcının mevcut sağlık durumu ve spor aktiviteleri sonucu girdiği veriler ile  sağlık seviyesinin (fitness_level:sürekli değişken) matematiksel olarak hesaplanması amaçlanmaktadır. Bunun için streamlit üzerinde bir arayüz tasarımı yapılacaktır.
İlerleyen aşamada, veri setinde var olan kullanıcılar için geleceğe yönelik sağlık seviye tahmini yapacak ve dahil olduğu sağlık grubuna göre geçmiş verileri elimizde olan kişilere tavsiyelerin verileceği bir sistem geliştirmek amaçlanmaktadır. Bunun için zaman serisi üzerine çalışma yapılacaktır.

## 2. Gözetimsiz Öğrenme için Sonuçlar:  
İlerleyen aşamalar projenin başında da belirttiğim gibi proje ile ilgili bir arayüz hazırlanacaktır.Projenin bu kısmında sisteme dahil olacak yeni bir kişiden endurance_heart_ratio, avg_heart_rate ve heart_rate_reserve değişkenleriyle ilgili ortalama değerlerini girmesini bekliyoruz. Buna ek olarak age bilgisini de sisteme girmesini bekliyoruz. Böylece yeni gelen kişinin mevcut veri setinde hangi gruba dahil olacağını belirliyor olacağız.Ancak veri gruplama konusunda yetersiz gibi görünüyor. Bu nedenle veriyi arttırmak daha verimli olacaktır.  

### Segment İsimlendirmesi ve Öneriler

### 🧘‍♂️💓 Cluster 1 – Kondisyonlu Yetişkinler (40+ yaş, düşük HR, yüksek kondisyon)

#### ✅ Öneriler:

* Kardiyo aktiviteleri (yürüyüş, yüzme, bisiklet) haftada en az 3–4 gün devam ettirilmeli.
  
* Esneklik ve denge egzersizleri (yoga, pilates, tai chi) eklenmeli. Yaşla birlikte denge kaybı riskine karşı önlem alınmalı.

* Düzenli kalp kontrolleri yaptırılmalı (özellikle hipertansiyon veya genetik kalp hastalığı öyküsü varsa).

* Düşük tempolu direnç antrenmanları → kas kütlesini korumak ve yaşa bağlı kayıpları önlemek için.
* Uyku kalitesi ve stres yönetimi göz ardı edilmemeli. Kalp sağlığına doğrudan etki eder.
Beslenme: Akdeniz tipi diyet (zeytinyağı, balık, sebze ağırlıklı) tercih edilmeli.


### 🏃‍♀️🔥 Cluster 2 – Genç ve Aktif Bireyler (20–40 yaş, yüksek HR, kondisyon değişken)

#### ✅ Öneriler:

* Düzenli egzersiz alışkanlığı kazandırılmalı (özellikle kardiyo + kuvvet çalışmaları kombinasyonu).
* VO2 Max artırıcı antrenmanlar (HIIT, interval koşular) kondisyonu iyileştirmede etkili olur.
* Kalp atış hızı takip edilmeli. Yüklenme seviyeleri buna göre ayarlanmalı.
* Recovery (toparlanma) günleri ihmal edilmemeli. Yüksek efor sonrası dinlenme kas gelişimi ve kalp sağlığı için kritiktir.
* Beslenme: Protein, kompleks karbonhidrat ve sağlıklı yağ dengesi iyi kurulmalı.
* Uyku takibi yapılmalı. 7–9 saat kaliteli uyku, genç yaşta bile kalp ritmini ve performansı olumlu etkiler.
* Alkol, sigara gibi alışkanlıklardan uzak durulmalı.

### Hangi Problemle Karşılaştık?


# Linkler  

Projemle ilgili detaylı anlatımlara aşağıdaki linklerden ulaşabilirsiniz.  
https://www.kaggle.com/code/zdengltekin/health-and-fitness-unsupervised-3/  
https://www.kaggle.com/code/zdengltekin/health-and-fitness-supervised/  

