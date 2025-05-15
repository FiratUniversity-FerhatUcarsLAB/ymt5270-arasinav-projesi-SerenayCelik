# YMT5270 Ara Sınav Projesi: Orange ile Veri Analizi ve Makine Öğrenmesi

## Öğrenci Bilgileri
- **Ad Soyad: Serenay Çelik** 
- **Öğrenci Numarası: 242138201** 
- **E-posta: serenaycelik23@gmail.com**

## Proje Özeti
> *Bu projede, buğday tohumlarının türünü tahmin etmeye yönelik bir makine öğrenmesi sınıflandırma uygulaması gerçekleştirilmiştir. Kullanılan veri seti, UCI Machine Learning Repository'den alınan ve farklı buğday türlerine ait morfolojik özellikleri içeren Seeds veri setidir. Veri seti; Area, Perimeter, Compactness, Length of kernel, Width of kernel, Asymmetry coefficient ve Length of kernel groove gibi 7 adet öznitelik ile buğday türünü (1:Kama, 2:Rosa, 3:Canadian) temsil eden 1 adet hedef değişkene sahip 210 örnekten oluşturulmuştur. Veri setinin uyguluğundan analiz yöntemi olarak sınıflandırma tercih edilmiştir. Bu çalışmada, K-En Yakın Komşu (KNN), Random Forest ve Destek Vektör Makineleri (SVM) algoritmaları kullanılmış ve tüm modelleme süreci Orange Data Mining aracı aracılığıyla gerçekleştirilmiştir. Elde edilen sonuçlar, KNN ve Random Forest algoritmalarının oldukça başarılı performans sergilediğini, SVM modelinin genel sınıflandırma performansı açısından en yüksek başarıyı gösterdiğini ortaya koymuştur. Değerlendirme metrikleri olarak AUC (Area Under the Curve), F1 Score, Doğruluk (Accuracy), Precision ve Recall kullanılmıştır. Sonuçlar, SVM algoritmasının, KNN ve Random Forest algoritmalarına göre daha yüksek AUC ve F1 Score değerleri ile en iyi performansı sergilediğini göstermektedir. Özellikle F1 Score, modelin hem doğruluğunu hem de sınıfların dengesiz dağılımını dikkate alarak daha anlamlı sonuçlar vermiştir. Ayrıca, AUC değeri, modelin genel sınıflandırma performansını göstererek SVM'in daha iyi genel sınıflandırıcı olduğunu doğrulamaktadır. Sonuçlar, buğday tohumlarının fiziksel-morfolojik özelliklerinin doğru sınıflandırma için yeterli bilgi sağladığını ve uygun algoritmalarla yüksek doğruluk oranlarına ulaşılabileceğini göstermektedir.*

## Veri Seti
### Veri Seti Bilgileri
- **Veri Seti Adı**: *Seeds*
- **Kaynak**: *https://archive.ics.uci.edu/dataset/236/seeds*
- **Lisans**: *M. Charytanowicz, J. Niewczas, P. Kulczycki, P. Kowalski, and S. Lukasik. "Seeds," UCI Machine Learning Repository, 2010. [Online]. Available: https://doi.org/10.24432/C5H30K.*
- **Veri Seti Boyutu**: *210 satır, 8 sütun*

### Veri Seti Tanımı
> Buğday çeşitlerini tanımak için kullanılan Seeds veri seti, her türün çeşitli özelliklerine dayalı sınıflandırma yapmaya olanak tanır. Veri setinde, farklı buğday türlerinin fiziksel özellikleri hakkında bilgi bulunur. Araştırmalar, Polonya’nın Lublin şehrinde bulunan Bilimler Akademisi Tarım Fiziği Enstitüsü’ndeki deney alanlarından toplanan, kombine hasat edilmiş buğday taneleriyle gerçekleştirilmiştir. İncelenen grup, her biri 70 örnekten oluşan üç farklı buğday çeşidini içermektedir: Kama, Rosa ve Canadian. Buğday tanelerinin iç çekirdek yapıları, yumuşak bir X-ışını tekniği kullanılarak yüksek kalitede görüntülenmiş ve elde edilen görüntüler 13x18 cm boyutlarında X-ışını KODAK plakalarına kaydedilmiştir.

*Olası Sınırlılıklar*
> 1. Küçük Veri Seti: Seeds veri seti, sadece 210 örnek içeriyor, bu da sınıflandırma modellerinin genellenebilirliğini sınırlayabilir.
> 2. Fiziksel Özelliklere Dayanma: Veri seti, sadece buğday tanelerinin fiziksel özelliklerine odaklanmaktadır. Ancak bazı durumlarda, buğdayın kalite ve verimliliğini etkileyen diğer faktörler, örneğin genetik faktörler, çevre koşulları, toprak türü ve ekim stratejileri gibi faktörler de sınıflandırmada önemli rol oynayabilir.

### Öznitelik Açıklamaları
| Öznitelik Adı | Veri Tipi | Açıklama | Örnek Değer |
|---------------|-----------|----------|-------------|
| Area | Sayısal | Buğday tanesinin alanı | 15.26 |
| Perimeter | Sayısal | Buğday tanesinin çevresinin uzunluğu | 14.84 |
| Compactness | Sayısal | Alanın çevre uzunluğuna oranı | 0.8710 |
| Length of kernel | Sayısal | Buğday tanesinin uzunluğu | 5.763 |
| Width of kernel | Sayısal | Buğday tanesinin genişliği | 3.312 |
| Asymmetry coefficient | Sayısal | Tane şeklinin simetrik olup olmadığına dair bir ölçüt | 2.2210 |
| Length of kernel groove | Sayısal | Tane üzerindeki oluk uzunluğu | 5.220 |
| Class | Kategorik | Sınıf etiketi | "Kama" |

## Keşifsel Veri Analizi (Explanatory Data Analysis - EDA)
### Temel İstatistikler
> Veri setine ait temel istatistikler (ortalama, medyan, standart sapma, vb.) Feature Statistics widget'ı kullanılarak görselleştirilmiştir. Eksik veri kotrolü sağlanmıştır.

![image](https://github.com/user-attachments/assets/72a1c3af-39cb-488f-b1d7-9fa5b5976372)

### Veri Ön İşleme
> - *Eksik verilerin tespiti*
![1](https://github.com/user-attachments/assets/eeff511f-2b1c-4463-aecd-c6505e21786f)

![2](https://github.com/user-attachments/assets/5b094da9-95e6-4dba-b2dd-f38849f40cd2)

> Feature Statistics'te missing değerlerin 0 olması ve Data Table'de tüm değerlerin dolu olması eksik değerlerin olmadığını göstermektedir.

> - *Aykırı değerlerin tespiti*
![3](https://github.com/user-attachments/assets/fc4675f6-e732-4a9c-bf93-efc150335158)

![4](https://github.com/user-attachments/assets/3ce9827d-038a-4ad3-b56d-c5e6ca77f57b)

> Box Plot kullanılarak yapılan analizde özniteliklerde aykırı değerler tespiti yapılmıştır. Ortalama değerler göz önünde bulundurulduğunda ve özniteliklere ait Box Plot, Distributions widgetleri görselleştirildiğinde modellerin performanslarını etkilecek aykırı değerler gözlemlenmemiştir.

### Görselleştirmeler
#### Görselleştirme 1: Özniteliklerin sınıflandırmaya etkisi (Tree Viewer)

![5](https://github.com/user-attachments/assets/752f4067-1cc8-4c4e-a9be-6d3b60dd55af)

> *Sınıflandırma ve regresyon ağaçlarını 2D olarak görselleştirerek, modelin nasıl çalıştığını ve verilerin nasıl sınıflandırıldığını anlamayı kolaylaştırmaktadır. Böylece özniteliklerin sınıflandırmadaki etkisi gözlemlenmiştir.*

#### Görselleştirme 2: Alanın çevre uzunluğuna oranının buğday türlerine göre dağılımı (Distributions)

![6](https://github.com/user-attachments/assets/c22000b8-eff2-4602-9eb3-a25aba7d2193)

> *Alanın çevre uzunluğuna oranının buğday türlerine göre dağılımına bakıldığında, her bir buğday türü için bu oranın farklı yoğunluklarda dağıldığı görülmektedir.*

### Öznitelik İlişkileri
![7](https://github.com/user-attachments/assets/189b9e9e-9623-4687-a7f6-36d99df05f7a)

> *Scatter Plot grafiğinde, "Area" ve "Perimeter" özniteliklerinin buğday türlerine göre dağılımı incelendiğinde, bu iki özniteliğin birlikte kullanıldığında türler arasında kısmen ayırt edici bir yapı oluşturduğu görülmektedir. Bazı buğday türleri belirli bölgelerde kümelenirken, diğer türlerle örtüşen alanlar da mevcuttur.*

![image](https://github.com/user-attachments/assets/602fb2af-b8ac-4006-abbb-3f737a7ffc2a)

> *Correlation widget’ı ile veri kümesindeki tüm sayısal özniteliklerin birbiriyle olan ilişkisi görülebilmektedir. Veri setindeki öznitelikler arasında yapılan korelasyon analizi sonucunda, özellikle "Area" ile "Perimeter" (r ≈ 0.994) ve "Length of kernel" ile "Perimeter" (r ≈ 0.972) arasında yüksek pozitif korelasyon olduğu görülmüştür. Bu değerler, bu özniteliklerin birbirine çok benzer bilgi taşıdığını göstermektedir.*

## Makine Öğrenmesi Uygulaması
### Kullanılan Yöntem
> *Seeds veri setinde yer alan 7  öznitelik kullanılarak, buğdayların üç buğday türüne göre sınıflandırılması amaçlanmıştır; bu sebeple , SVM ve Random Forest algoritmaları kullanılmıştır.*

### Modeller ve Parametreler
> 1. KNN: En yakın komşulara bakarak sınıflandırma yapmaktadır.
> 2. Random Forest: Birden fazla karar ağacının oyuyla tahmin etmektedir.
> 3. SVM: Sınıflar arasındaki en iyi ayırıcı sınırı bulmaktadır.

![9](https://github.com/user-attachments/assets/c37dbb84-f6bc-4c8e-900e-95046d9a2ec8)

> *Select Columns widget'ı kullanılarak özellikler ve hedef değişken belirlenmiştir.*

 ![10](https://github.com/user-attachments/assets/cf7a6d5a-779a-4cbe-af65-6a197655270e)
 
> *Data Sampler widget'ı kullanılarak veri setinin %70'i eğitim verisi, %30'u test verisi olarak bölünmüştür.*

![image](https://github.com/user-attachments/assets/afcd2093-f42d-4fad-b034-411b73506348)

> *KNN modelinde k parametresi (komşu sayısı) 5 olarak seçilmiştir.*


### Model Değerlendirmesi
> *Seeds veri seti üzerinde yapılan sınıflandırma deneylerinde, KNN, SVM ve Random Forest modelleri karşılaştırılmıştır. Sonuçlar, SVM algoritmasının hem doğruluk (CA) hem de AUC, F1, precision, recall ve MCC gibi performans metriklerinde diğer modellere kıyasla daha üstün olduğunu göstermektedir. Random Forest modeli, yüksek performansıyla SVM’yi takip ederken, KNN daha düşük ancak hala kabul edilebilir bir başarı düzeyi sergilemiştir. Genel olarak, üç model de Seeds veri setindeki sınıflandırma problemi için uygun olmakla birlikte, SVM’nin en başarılı model olduğu söylenebilir.*

#### Metrikler
> *AUC (Area Under Curve): Modelin sınıfları ayırmadaki genel başarısını gösterir, 1’e yakınsa iyidir.*
 
> *CA (Classification Accuracy): Doğru sınıflandırılan örneklerin oranıdır.*

> *F1 Score: Precision ve Recall’un dengeli ortalamasıdır, özellikle dengesiz veri için önemlidir.*

> *Precision (Kesinlik): Modelin pozitif tahminlerinin ne kadarının doğru olduğunu gösterir.*

> *Recall (Duyarlılık): Gerçek pozitiflerin model tarafından ne kadarının bulunduğunu ifade eder.*

> *MCC (Matthews Correlation Coefficient): Tüm sınıflar için dengeli başarı ölçüsü, -1 ile +1 arasında değer alır.*

| Metrik | KNN | SVM | Random Forest |
|---------------|-----------|----------|-------------|
| AUC | 0.979 | 0.987 | 0.980 |
| CA | 0.871 | 0.925 | 0.898 |
| F1 Score | 0.869 | 0.925 | 0.898 |
| Precision | 0.870 | 0.925 | 0.899 |
| Recall | 0.871 | 0.925 | 0.898 |
| MCC | 0.807 | 0.888 |  0.847 |

### Sonuçların Yorumlanması
### Modellerin Güçlü ve Zayıf Yönleri
> *SVM modeli, karmaşık veri setlerinde sınıflar arasındaki sınırları etkili bir şekilde belirleyebilmesi ve yüksek doğruluk sağlamasıyla güçlüdür. Ancak, doğru parametrelerin seçilmesi zor olabilmekte ve büyük veri setlerinde eğitim süresi uzayabilmektedir. Random Forest, çok sayıda karar ağacından oluşan yapısıyla aşırı öğrenmeye karşı dayanıklı ve genelleme kabiliyeti yüksek bir modeldir; bununla birlikte, çok sayıda ağaç kullanıldığında eğitim süresi artabilmektedir. KNN ise basit ve uygulanması kolay bir yöntem olmasına rağmen, büyük veri setlerinde yavaş çalışabilmekte ve özellikle yüksek boyutlu verilerde performansı düşmektedir. Ayrıca, doğru k değerinin belirlenmesi kritik olup modelin başarısını doğrudan etkilemektedir.*

### Modellerin Performansları
![12](https://github.com/user-attachments/assets/d92b2371-b360-4fca-acbb-cda7eee0eb9a)

> *SVM modeli, tüm metriklerde en yüksek başarıyı göstererek en iyi performansı sağlamıştır. Random Forest iyi bir alternatif olup dengeli ve güvenilir sonuçlar verirken, KNN diğerlerine göre daha düşük doğruluk ve hassasiyet sunmuştur. Genel olarak, SVM sınıflandırma için en etkili model olarak öne çıkmaktadır.*

![13](https://github.com/user-attachments/assets/50e70b62-f797-4f40-b99f-a345f89dbfaf)

![14](https://github.com/user-attachments/assets/234f6232-870e-470d-8738-50f139e8b8ac)

![15](https://github.com/user-attachments/assets/faaf6ee2-d94a-42de-84c0-d03ef42c3f21)

> *Confusion matrisi sonuçları, modellerin sınıfları doğru şekilde ayırt etme başarısını gösteriyor ve SVM’nin diğer modellere göre daha dengeli ve yüksek doğru sınıflandırma oranına sahip olduğunu doğrulamaktadır.*

## Orange İş Akışı
> *Orange ile oluşturduğunuz iş akışı görselini buraya ekleyiniz. İş akışınızın adımlarını kısaca açıklayınız.*
![16](https://github.com/user-attachments/assets/f24590a0-8806-4356-8fab-840ae7b696e9)

> *File widget’ı ile Seeds veri setini yüklenmiştir.*

> *Data Table ile veri seti incelenmiş ve öznitelikler gözden geçirilmiştir.*

> *Distributions, Scatter Plot, Box plot, Feature Statistics Correlations gibi widgetleri ile veri analiz edilmiştir.*

> *Select Columns ile hedef değişken (buğday türü) ve öznitelikler belirlenmiştir.*

> *Data Sampler ile veri eğitim ve test verileri olarak ayrılmıştır.*

> *Test & Score widget’ı ile sınıflandırma algoritmaları (KNN, SVM, Random Forest) değerlendirilmiştir.*

> *Confusion Matrix ile performans sonuçlarını görselleştirilmiştir.*

## Sonuç ve Öneriler
> *Bu projede, Seeds veri seti kullanılarak buğday türlerinin sınıflandırılması hedeflenmiştir. KNN, SVM ve Random Forest algoritmaları karşılaştırılmış ve SVM modeli en yüksek doğruluk ve genel performansla en başarılı sonuçları vermiştir. Hiperparametre optimizasyonu (grid search, random search) ile modellerin performansı artırılabilir. Farklı ensemble yöntemleri (XGBoost, LightGBM)  denenebilir. Veri ön işleme ve özellik mühendisliği çalışmalarıyla model başarısı desteklenebilir.*

## Kaynaklar

1. Orange Data Mining Video Tutorials - https://www.youtube.com/c/OrangeDataMining
2. Orange Data Mining Documentation – https://orangedatamining.com
3. Machine Learning for beginners with Orange Data Mining - https://medium.com/eni-digitalks/machine-learning-for-beginners-with-orange-data-mining-0690372533b9
4. ChatGPT

## Ekler
### Orange Proje Dosyası
[serenaycelikymt5270arasınav.ows](https://github.com/FiratUniversity-FerhatUcarsLAB/ymt5270-arasinav-projesi-SerenayCelik/blob/main/project/serenaycelikymt5270aras%C4%B1nav.ows)

### Veri Seti Dosyası veya Bağlantısı
[UCI Seeds Dataset](https://archive.ics.uci.edu/dataset/236/seeds)

