# SMOTE-Algorithms-for-Imblance-Data
Dengesiz veri setleri hakkında daha önce kısa bir bilgi vererek yapabileceklerimizden buradaki yazıda bahsetmiştik. Bu yazıda ise yeniden örnekleme yöntemlerinden birisi olan SMOTE algoritmaları üzerine konuşacağız.

Örnek kodlara ulaşmak için buraya bakabilirsiniz.

Synthetic Minorty Over-sampling Tecnique (SMOTE) yöntemleri azınlık sınıfında yer alan örnekleri ele alarak yeni bir gözlem birimi oluşturmayı amaçlar. SMOTE yöntemlerinin temeli genel olarak en yakın komşu uzaklığına dayanır. Sentetik veri oluşturmak için kullanılabilecek farklı SMOTE algoritmaları aşağıdaki gibidir:

SMOTE
ADASYN
SMOTENC
SMOTEN
BORDELINE SMOTE
KMEANS SMOTE
SVM SMOTE
SMOTEEN
SMOTE TOMEK
SMOTE ve ADASYN
SMOTE ve ADASYN algoritmalarının her ikisinde de en yakın komşu algoritması ve öklid uzaklığı kullanılır. SMOTE ve ADASAYN algoritması formülü aşağıdaki gibidir.

Xyeni= Xi + λ(Xi-Xij)

Bu formülde Xi sentetik veri üretmek için seçilen gözlem birimini ifade eder. Xi-Xij ise gözlem biriminin en yakın komşuları arasındaki uzaklıktır. λ ise 0 ve 1 arasında rasgele üretilen sayıya anlamına gelir.

ADASYN ve SMOTE algoritmasının arasındaki en temel fark ADASYN algoritmasında üretilecek sentetik örnek sayısına karar vermek için yoğunluk dağılımı kullanılmasıdır. ADASYN algoritmasında yoğunluk dağılımı kullanılarak öğrenilmesi zor olan gözlem birimlerine yoğunlaşılır. Burada amaçlanan, sınıf dağılımını eşitlemenin yanında öğrenilmesi zor olan gözlemlerin sayısını artırarak modelin öğrenmesini güçlendirmektir.

Sonuç olarak SMOTE ve ADASYN algoritmaları aynı formüle sahiptirler. SMOTE algoritması ile veri üretilirken gözlem birimleri arasından herhangi bir filtre yapılmazken ADASYN algoritması ile veri üretilirken öğrenilmesi zor olan gözlem birimlerine odaklanılır.

SMOTENC
SMOTE algoritmalarının geneli sürekli değişkenler üzerinde çalışabilecek şekilde tasarlanmıştır. Yani bu algoritmaları kullanırken veri setinde nominal değişken olması istenmez. SMOTENC algoritması ise bu soruna çözüm getirerek sürekli ve nominal değişkenlerin her ikisi ile çalışma imkanı verir.

Nominal değişkenlerin sentetik üretimi için; öncelikle azınlık sınıfında bulunan tüm sürekli değişkenlerin standart sapmalarının medyanı bulunur. Daha sonra nominal özellikte olan gözlem birimiyle en yakın komşuları arasında farklılık varsa hesaplanan medyan değeri öklid uzaklığına dahil edilir.

NOT: Tamamı nominal değişkenden oluşan veri seti ile çalışmaz. Algoritmanın çalışması için veri seti içerisinde en az bir tane sürekli değişken bulunması gerekir.

SMOTEN
SMOTEN algoritması yalnızca kategorik değişkenlere sahip veri setleri ile çalışırlar. Yeni bir sentetik veri üretilirken gözlem birimlerinin en yakın komşuları dikkate alınarak en sık gözlenen kategori yeni veri olarak belirlenir.

BORDERLINE SMOTE
Borderline SMOTE algoritmasının temelinde gözlem birimlerinin bir sınır çizgisi ile ayrılması vardır. Sentetik veri üretilirken kullanılabilecek iki algoritma türü bulunur bunlar: Borderline smote1 ve Borderline smote2 olarak geçer.

Her iki algoritma içinde ilk olarak azınlık sınıfında yer alan her gözlem (Xi) biriminin en yakın komşu uzaklığı bulunur. Burada önemli olan gözlem birimlerinin en yakın komşularının bulunmasında çoğunluk sınıfınında kullanılıyor olmasıdır. (Yani azınlık sınıfına dahil gözlem birimlerinin her birinin en yakın komşunun bulunmasında tüm sınıflar dikkate alınır.)

Bu aşamadan sonra algoritma şöyle işler;

Eğer Xi gözlem biriminin tüm en yakın komşuları çoğunluk sınıfına ait gözlemlerden oluşuyorsa azınlık sınıfına ait bu Xi “GÜRÜLTÜ” olarak adlandırılır ve sonraki adımlarda kullanılmaz.
Eğer Xi gözlem biriminin çoğunluk sınıfında bulunan en yakın komşuları, azınlık sınıfında bulunan en yakın komşularından fazlaysa azınlık sınıfına ait bu Xi “yanlış sınıflandırılabilir” olarak tanımlanır ve “TEHLİKELİ” olarak ifade edilerek bu gruba atanır.
Eğer Xi gözlem biriminin en yakın komşularının çoğu azınlık sınıfına ait gözlemlerden oluşuyorsa bu Xi “GÜVENLİ” olarak ifade edilerek bu gruba atanır.
NOT: En yakın komşular bulunurken çoğunluk sınıfının da kullanılmasının nedeni azınlık sınıfı gözlem birimlerinin Gürültü, Tehlikeli ve Güvenli olarak farklı gruplara atanmasını sağlamaktır.

Bu aşamalardan sonra “TEHLİKELİ” olarak atanan her bir gözlem birimi için artık yalnızca azınlık sınıfındaki gözlem birimleri dikkate alınarak en yakın komşular hesaplanır. (Bu işlem tehlikeli grubunda bulunan tüm gözlem birimleri bitene kadar devam eder.)

Borderline smote 1 algoritması ve Borderline smote 2 algoritması aynı aşamalara sahiptir. Aralarındaki fark son aşama olan sentetik veri üretiminde başlar. Borderline smote 1 algoritmasında son aşamada sentetik veri üretilirken yalnızca azınlık sınıfındaki gözlem birimleri kullanılır. Borderline smote 2 algoritmasının son aşamasında ise sentetik veri üretilirken çoğunluk sınıfında yer almasına rağmen azınlık sınıfı gözlem birimine daha yakın olan gözlem birimleri de dikkate alınarak sentetik veri üretilir.

KMEANS SMOTE
K Means SMOTE algoritmasında amaç doğal olarak kümelenen örnekler oluşturarak sınıfların bölgelerini belirleyebilmektir.

Bu yöntemde öncelikle gözlem birimleri belirlenen sayı kadar kümeye ayrılır. Daha sonra azınlık sınıfına ait gözlemlerin çoğunlukta bulunduğu kümelere yeni sentetik örnekler eklenir.

NOT: Bir kümenin en az %50'si azınlık sınıfı verilerinden oluşuyorsa o küme yeniden örnekleme için uygun kabul edilir.

SVM SMOTE
SVM algoritmasının mantığı kullanılarak yeni sentetik verilerin üretilmesini sağlar. algoritmada öncelikle SVM eğitilerek azınlık ve çoğunluk sınıfı arasındaki farklı maksimize edecek şekilde hiper düzlem oluşturulur. Daha sonra sınıra yakın olan gözlem birimleri kullanılarak sentetik veriler üretilir.

SMOTE TOMEK
Tomek bağlantıları potansiyel yanlış sınıflama veya belirsiz karara sebep olabilecek gözlem birimlerini tespit etmek için kullanılır.

İkili bir sınıflandırmada (0 ve 1) birbirine en yakın iki komşu (a ve b olsun) farklı sınıflara aitse bunlar Tomek Bağlantısı olarak adlandırılır.

Örneğin: a 0 sınıfına ait bir gözlem birimi, b 1 sınıfına ait bir gözlem birimi olsun. Aynı zamanda A ve B birimleri birbirlerinin en yakın komşusu olsun. Bu durumda a ve b birimleri tomek bağlantısı içerir.

SMOTE Tomek yönteminde bu bağlantıya sahip gözlem birimleri tespit edilerek veri setinden kaldırılması amaçlanır. Böylelikle üretilecek yeni sentetik verilerin kararsızlığa sebep olabilecek gözlem birimlerinden etkilenmemesi amaçlanır.

SMOTEENN
SMOTEENN yöntemi en yakın komşu algoritmasının düzenlenmesiyle elde edilmiştir. Gözlem biriminin sınıfı ve K en yakın komşularının çoğunluk sınıfı farklı sınıfa sahip olduğunda her iki sınıftan da bazı gözlemlerin silinmesine odaklanır.

Tüm yöntemlerin örnek kodlarına ulaşmak için buraya tıklayabilirsiniz.

Herkese iyi çalışmalar dilerim :)

KAYNAKLAR

ADASYN
SMOTENC
BORDERLINE SMOTE ve BORDERLINE SMOTE
