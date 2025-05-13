# YMT5270 Ara Sınav Projesi: Orange ile Veri Analizi ve Makine Öğrenmesi

## Öğrenci Bilgileri
- **Ad Soyad: Serenay Çelik** 
- **Öğrenci Numarası: 242138201** 
- **E-posta: serenaycelik23@gmail.com**

## Proje Özeti
> *Bu projede, buğday tohumlarının türünü tahmin etmeye yönelik bir makine öğrenmesi sınıflandırma uygulaması gerçekleştirilmiştir. Kullanılan veri seti, UCI Machine Learning Repository'den alınan ve farklı buğday türlerine ait morfolojik özellikleri içeren Seeds veri setidir. Veri seti; alan (area), çevre (perimeter), kompaktlık (compactness), çekirdek uzunluğu ve genişliği gibi 7 adet öznitelik ile buğday türünü (1:Kama, 2:Rosa, 3:Canadian) temsil eden 1 adet hedef değişkene sahip 210 örnekten oluşturulmuştur. Veri setinin uyguluğundan analiz yöntemi olarak sınıflandırma tercih edilmiştir. Bu çalışmada, K-En Yakın Komşu (KNN), Random Forest ve Destek Vektör Makineleri (SVM) algoritmaları kullanılmış ve tüm modelleme süreci Orange Data Mining aracı aracılığıyla gerçekleştirilmiştir. Elde edilen sonuçlar, KNN ve Random Forest algoritmalarının oldukça başarılı performans sergilediğini, SVM modelinin genel sınıflandırma performansı açısından en yüksek başarıyı gösterdiğini ortaya koymuştur.Değerlendirme metrikleri olarak AUC (Area Under the Curve), F1 Score, Doğruluk (Accuracy), Precision ve Recall kullanılmıştır. Sonuçlar, SVM algoritmasının, KNN ve Random Forest algoritmalarına göre daha yüksek AUC ve F1 Score değerleri ile en iyi performansı sergilediğini göstermektedir. Özellikle F1 Score, modelin hem doğruluğunu hem de sınıfların dengesiz dağılımını dikkate alarak daha anlamlı sonuçlar vermiştir. Ayrıca, AUC değeri, modelin genel sınıflandırma performansını göstererek SVM'in daha iyi genel sınıflandırıcı olduğunu doğrulamaktadır. Sonuçlar, buğday tohumlarının fiziksel-morfolojik özelliklerinin doğru sınıflandırma için yeterli bilgi sağladığını ve uygun algoritmalarla yüksek doğruluk oranlarına ulaşılabileceğini göstermektedir.*

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
> Veri setine ait temel istatistikler (ortalama, medyan, standart sapma, vb.) Feature Statistics widgeti kullanılarak görselleştirilmiştir. Eksik veri kotrolü sağlanmıştır.
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
> *Orange ile yaptığınız veri görselleştirmelerini buraya ekleyiniz. Her görselleştirme için kısa bir açıklama yazınız. Görselleri bu repoya yükleyip, markdown içinde referans verebilirsiniz.*

#### Görselleştirme 1: Özniteliklerin sınıflandırmaya etkisi (Tree Viewer)
![5](https://github.com/user-attachments/assets/752f4067-1cc8-4c4e-a9be-6d3b60dd55af)

> *Bu görselleştirme ile ilgili yorumunuz ve çıkarımlarınız.*

#### Görselleştirme 2: [Görselleştirme Adı]
![Görselleştirme 2 Açıklaması](goruntuler/gorselleştirme2.png)
> *Bu görselleştirme ile ilgili yorumunuz ve çıkarımlarınız.*

### Öznitelik İlişkileri
> *Öznitelikler arasındaki ilişkileri analiz ediniz. Korelasyon matrisi, scatter plot matrisi gibi görsellerle destekleyiniz.*

## Makine Öğrenmesi Uygulaması
### Kullanılan Yöntem
> *Veri setinize uyguladığınız makine öğrenmesi yöntemini (sınıflandırma, regresyon veya kümeleme) belirtiniz ve neden bu yöntemi seçtiğinizi açıklayınız.*

### Modeller ve Parametreler
> *Denediğiniz modelleri ve kullandığınız parametreleri açıklayınız. Orange'da yapılandırdığınız widget ayarlarını ekran görüntüleri ile destekleyebilirsiniz.*

### Model Değerlendirmesi
> *Uyguladığınız modelin performansını değerlendiriniz. Kullandığınız değerlendirme metriklerini açıklayınız.*

#### Metrikler
| Metrik | Değer |
|--------|-------|
| Örnek Metrik 1 | 0.85 |
| Örnek Metrik 2 | 0.78 |
| ... | ... |

### Sonuçların Yorumlanması
> *Elde ettiğiniz sonuçları detaylı bir şekilde yorumlayınız. Modelin güçlü ve zayıf yönleri nelerdir? Başka hangi modeller denenebilirdi?*

## Orange İş Akışı
> *Orange ile oluşturduğunuz iş akışı görselini buraya ekleyiniz. İş akışınızın adımlarını kısaca açıklayınız.*

![Orange İş Akışı](goruntuler/is_akisi.png)

## Sonuç ve Öneriler
> *Projenizin genel bir değerlendirmesini yapınız. Elde ettiğiniz sonuçlar hakkında çıkarımlarınızı ve gelecek çalışmalar için önerilerinizi yazınız.*

## Kaynaklar
> *Proje boyunca yararlandığınız kaynakları (makaleler, web siteleri, videolar, vb.) buraya ekleyiniz.*

1. Kaynak 1
2. Kaynak 2
3. ...

## Ekler
### Orange Proje Dosyası
> *Orange proje dosyanızı (.ows) bu repoya yükleyiniz ve buradan referans veriniz.*
> 
> [Proje_Dosyasi.ows](proje_dosyasi.ows)

### Veri Seti Dosyası veya Bağlantısı
> *Kullandığınız veri setini bu repoya yükleyebilir veya bağlantısını burada paylaşabilirsiniz.*
>
> [Veri_Seti.csv](veri_seti.csv) veya [Veri Seti Bağlantısı](https://ornek-veri-seti-baglantisi.com)
