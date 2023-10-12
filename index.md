
- [1. Denetimsiz Öğrenme Nedir?](#1-denetimsiz-öğrenme-nedir)
- [2. Optimum Küme Sayısının
  Seçilmesi](#2-optimum-küme-sayısının-seçilmesi)
  - [2.1. Dirsek Yöntemi](#21-dirsek-yöntemi)
  - [2.2. Ortalama Silhouette Yöntemi](#22-ortalama-silhouette-yöntemi)
  - [2.3. Gap İstatistiği](#23-gap-i̇statistiği)
  - [2.4. Calinski-Harabasz Yöntemi](#24-calinski-harabasz-yöntemi)
  - [2.5. Davies-Bouldin Yöntemi](#25-davies-bouldin-yöntemi)
  - [2.6. Dunn Endeksi](#26-dunn-endeksi)
  - [k determination cheat sheet](#k-determination-cheat-sheet)

# 1. Denetimsiz Öğrenme Nedir?

Metinlerin, görüntülerin, sayıların ve daha fazlasının çılgınca bir
araya geldiği sonsuz veri akışlarından oluşan bir denizde gezindiğinizi
hayal edin. Dijital çağın bu zengin kaynağı derinlerde saklı gerçek bir
değer taşır. Bunu yüzdeyden fark etmek çok mümkün değildir. Denetimli
makine öğrenimi yaklaşımları makinenin eğitimi için etiketli verileri
kullanır ve bu, hiç bilmediğiniz sonsuz veri akışına sahip o denizde bir
harita ile gezinmeye benzer. Gideceğiniz yeri bilirsiniz ve rotanız
açıkça işaretlenmiştir. Bu şekilde yol almak oldukça basittir, değil mi?
Peki ya size herhangi bir açıklama verilmeden, işaret veya ipucu olmadan
bu seyehati yapsaydınız? İşte bu noktada denetimsiz öğrenme devreye
giriyor.

Denetimsiz öğrenme, veri dünyasında saklı olan sırları keşfetme
sanatıdır. Makinelerin ne arayacaklarını bilmeden verilerin
derinliklerine dalmalarını sağlayan bir dizi teknik içerir. Etiketli
örnekler tarafından yönlendirilmek yerine, denetimsiz öğrenme
algoritmaları altta yatan yapıları, ilişkileri ve desenleri ortaya
çıkarmak için veri okyanusunun derinliklerine dalar. Bu, bir makineye
bir büyüteç vermek ve kendi kalıplarını ve bağlantılarını keşfetmesine
izin vermek gibidir.

Denetimsiz öğrenmenin merkezinde iki ana konu bulunmaktadır: kümeleme ve
boyut indirgeme. Kümeleme, bir veri setinde bulunan gözlemleri
benzerliklerine göre gruplara ayırma işlemidir. Eve yeni bir kitaplık
aldığınızı hayal edin. Önceden çalışma masanızın üzerine, evdeki
sehpalara yığmanız gereken kitapları, şimdi, yeni aldığınız kitaplığa
yerleştirebilirsiniz. Fakat kitapların her birinin hangi rafta olacağını
ve hatta raftaki sıralamasını nasıl belirlerdiniz? Örneğim Asimov,
Philip Dick ve Frank Herbert’in kitaplarına ek olarak James Joyce,
Tolstoy ve Albert Camus gibi yazarlara ait kitaplarınız da var. Bu
kitaplar arasındaki benzerlik nedir? Asimov ve Herbert gibi yazarlar
bilim-kurgu temalı kitaplar kaleme aldıkları için bir benzerlikleri
olduğunu söyleyebiliriz. Fakat diğer taraftan Joyce ve Camus gibi
yazarları ise dünya klasikleri çatısı altında birleştirebiliriz. Yani
temelde iki küme oluşturmuş oluruz; dünya klasikleri ve bilim-kurgu
kitapları. Yani kitaplığımızda bulunan kitapları kümelemiş oluruz.
Örneğini vermiş olduğum bu teknik, yani kümemele, pazarlamada müşteri
segmentasyonundan sağlık hizmetlerinde hastalık alt tiplerinin
belirlenmesine kadar çeşitli alanlarda son derece kullanışlıdır.

Boyut indirgeme, özelliklerin veya boyutların sayısını azaltarak
karmaşık verileri basitleştirmekle ilgilidir. Ayrıntılı bir resim
düşünün; boyut indirgeme orijinalin özünü koruyan daha basit, soyut bir
temsil oluşturmaya yardımcı olur. Unutulmamalıdır ki makinelerle
yaptığımız her işlemin arka planda makineye bir maliyeti vardır. Tıpkı
iş yerinde size verilen bir görev, ya da okulda yapmanız gereken bir
ödev gibi. Bu tarz görevlerin yerine getirilmesi için vakit, emek ve
belki çok daha fazlasını harcamanız gerekir. Ancak size verilen görev ne
kadar basitse, yapacağınız harcamalar da aynı nicelikte azalacaktır.
Boyut indirgeme de tam olarak bunu yapmaktadır. Boyutunu indirgediğimiz
bir veri seti, makinenin daha az yorulmasına ve maliyetinin szalmasına
olanak sağlayacaktır. Üstelik tek artısının bu olduğunu da söyleyemeyiz.
Bu kitaba ulaşabilen bir çoğunuzun da bilebileceği gibi veri setlerinin
görselleştirilmesi üç boyutla sınırlıdır. Üçüncü boyut, yani bir başka
deyişle üç değişkenli, veri setleri dışında, daha fazla değişkene sahip
veri setlerini görselleştirmek mümkün değildir. Fakat örneğin on beş
değişkenli bir setinin boyutunu iki değişkene düşürürsek, sizin de
tahmin edebileceğimiz gibi veri seti görselleştirilebilir bir hale
gelecektir. Tüm bunlar hesaba katıldığında ise boyut indirgemenin bizi
boyutu büyük bir lanetten kurtaran, tonton algoritma büyücüsü olduğunu
söyleyebiliriz.

Bu kitabın kalan kısmında çeşitli kümeleme algoritmalarıyla birlikte
boyut indirgeme tekniklerinden Temel Bileşen Analizinin nasıl
çalıştığını, adım adım nasıl hesaplandığını ve R’da nasıl uygulanacağını
göreceğiz. Ayrıca kitabın en sonunda yer alan Alıştırma bölümüyle
öğrendiklerinizi sınayabilir, hatta pekiştirebilirsiniz. Unutmayın ki
makine öğrenmesi bir buz dağı ise öğretmek görünen, öğrenmek ise buz
dağının görünmeyen kısmıdır. Eğer birçok veri seti ile öğrendiğiniz
şeyleri tekrar tekrar denemezseniz aslında hiçbir şey öğrenmemiş
olacaksınız. Tüm bunlar düşünüldüğünde umarım bu kitap sizin için
faydalı olacaktır.

# 2. Optimum Küme Sayısının Seçilmesi

Böyle bir başlıkla karşılaştığınızda küme sayısının belirlenmesinin
neden önemli olduğunu merak edebilirsiniz. Bir önceki bölümdeki kitaplık
örneğini hatırlayalım. Kitaplıkta yer alan kitapları iki kümeye(dünya
klasikleri ve bilim-kurgu kitapları) ayırmıştık. Fakat iki küme olduğuna
nasıl karar verdik? Gerçekten iki kümenin doğru küme sayısı olduğundan
emin olabilir miyiz? Hatta çrnekte elimizde yalnızca altı kitap olduğu
için bunu bir şekilde yapabildik. Ya elimizdeki kitap sayısı bir milyon
olsaydı? Küme sayısını belirlemek bazı durumlarda mümkün olabilirken,
bazen de bir o kadar mümkün olmayabilir. Bunu bir veri seti ile
gözününzde canlandırmak faydalı olabilir. Örneğin aşağıdaki dağılım
grafiğine baktığımızda küme sayısının üç olduğunu, gözlemlerin üç farklı
nokta özelinde yoğunlaşması sebebiyle söyleyebiliriz.

![](https://cdn-images-1.medium.com/max/800/1*b218oEdOwrx8g24HC13B5w.png)

Ancak, yaygın olarak karşılaşılan veri setlerinde küme sayısını
belirlemek, sadece bir dağılım grafiği ile veri setinin genel yapısını
gözlemleyerek elde edilemeyecek kadar karmaşıktır. Örneğin aşağıdaki
dağılım grafiği incelendiğinde veri setinin kaç kümeye ayrıldığını
söylemek oldukça zor olacaktır.

![](https://cdn-images-1.medium.com/max/800/1*ekHDzQi6HseK6uGd6yv0Zg.png)

Bu gibi sorunlarla sürekli karşılaşıldığı için, küme sayısını belirleme
göreviyle bazı yöntemler geliştirilmiştir. Bu bölümün kalanında bu
yöntemlerden en çok kullanılan altı tanesinin ne olduğunu, adım adım
nasıl hesaplandıklarını ve R’da nasıl uygulandıklarını göreceğiz. Tüm
örneklerde aynı veri seti ([Breast Cancer
Wisconsin](https://archive.ics.uci.edu/ml/datasets/breast+cancer+wisconsin+%28diagnostic%29))
kullanılmıştır..

## 2.1. Dirsek Yöntemi

Dirsek yöntemi, bir kümeleme analizinde en uygun küme sayısını
belirlemek için kullanılan bir tekniktir. Arkasındaki fikir, bir dizi
küme sayısı (k) için veri kümesi üzerinde k-ortalamalar kümelemesini
çalıştırmak ve her k değeri için her noktanın en yakın merkeze olan
karesel uzaklıklarının toplamını (KUT) hesaplamaktır. Dirsek noktası,
KUT’nin k’ya karşı grafiğinde KUT’daki değişimin düzleşmeye başladığı
noktadır, bu da daha fazla küme eklemenin modeli çok fazla
iyileştirmediğini gösterir. \[1\], \[2\]

Dirsek yöntemini aşağıdaki adımlarla hesaplanabilir:

1.  Genellikle 1 ila 10 arasında seçilen ama analize göre değişebilecek
    aralıkta küme sayıları belirlenir.

2.  Her k değeri için istediğinilen kümeleme algoritmasını çalıştırılır
    ve her bir k değeri için KUT hesaplanır.

3.  Her k değeri x ekseninde, KUT değerleri ise y ekseninde olacak
    şekilde çizgi grafiği çizilir.

4.  KUT’un daha yavaş bir oranda azalmaya başladığı nokta dirsek
    noktasıdır ve buna karşılık gelen küme sayısı k için en uygun
    değerdir.

Kuşkusuz, Dirsek yöntemi en yaygın kullanılan yöntemlerden biridir.
Ancak, tecrübeyle sabit, her koşulda iyi sonuçlar verdiğini söylemek
yanlış olacaktır. Hatta bazen yanıltıcı olduğu bile söylenebilir. Bu
nedenle her kümeleme analizinde küme sayısını belirlemek için Dirsek
Yönteminin kullanılması gerektiği; ancak tek başına bu yönteme
güvenilmemesi gerektiğinin altı mutlaka çizilmelidir.

R’da `factoextra` paketi optimum küme sayısını belirleme yöntemleri için
güzel grafik imkanları sunan güzel bir paket. Biz de bu pakette yer alan
`fviz_nbclust` fonksiyonu ile Dirsek Grafiğini çizeceğiz.

``` r
fviz_nbclust(df, # veri seti  
             kmeans, # kümeleme algoritması 
             nstart = 25, # kümeleme algoritması ile ilgili seçenek 1
             iter.max = 200, #  kümeleme algoritması ile ilgili seçenek 2 - bu iki seçenek k-means bölümünde açıklanacaktır.
             method = "wss") # dirsek yöntemi için wss yazılmalıdır.
```

![](index_files/figure-gfm/unnamed-chunk-2-1.png)<!-- -->

Örneğin yukarıdaki çıktıda keskin bir dirsek olmadığı görülmektedir. Bu
nedenle yoruma açık bir sonuç olarak dikkat çekmektedir. Bu dirseğe
dayalı bir yorum bu nedenle yanlış sonuçlara yol açabilir.

## 2.2. Ortalama Silhouette Yöntemi

Ortalama silhouette yöntemi, belirli bir gözlemin dahil olduğu kümeyi ne
kadar iyi tanımlandığını ve diğer kümelerden ne kadar iyi ayrıldığını
ölçen bir geçerlilik metriğidir \[3\] , \[4\]. Üç adımda
hesaplanmaktadır.

1.  Küme sıkılığı hesaplanır: silhouette katsayısı hesaplanan
    gözlemin(aşağıdaki çizimde mor renkle vurgulanan gözlem) dahil
    olduğu kümenin diğer elemanlarına(mavi renkle vurgulanan diğer bütün
    gözlemler) uzaklıklarının toplamının toplam gözlem sayısına
    bölünmesi. Bu metriği a(i) olarak isimlendirebiliriz. (Uzaklık
    hesaplanırken genellikle Öklit uzaklık metriği tercih edilir.)

    ![](https://cdn-images-1.medium.com/max/800/1*oPJ8x71lbkMomHRx4qm2Ug.png)

2.  Küme ayrımı hesaplanır: silhouette katsayısı hesaplanan gözlemin
    dahil olmadığı kümelerde yer alan gözlemler içerisinden uzaklığı en
    az olan gözlemle olan uzaklığı. Bu metriği b(i) olarak
    isimlendirebiliriz.

    ![](https://cdn-images-1.medium.com/max/800/1*h0Ues0gLRs2FD5TrOpmFGA.png)

3.  Silhouette katsayısı hesaplanır: b(i) değerinin a(i) değerinden
    farkının alınıp; b(i) ve a(i) değerlerinden hangisi daha yüksek bir
    değere sahipse o değere bölünmesi ile silhouette katsayısı bulunur.

![](https://miro.medium.com/v2/resize:fit:640/format:webp/1*L2nNHjwqpS7ZOdXZEvTC2g.png)

Yukarıdaki adımlarla veri setinde yer alan her bir gözlem için
Silhouette değeri hesaplanır. Eğer her bir gözlemin Silhouette
katsayısına bakarsak her bir gözlem için kümelemenin ne kadar başarılı
olduğunu görebiliriz. -1 ile 1 arasında değer alan Silhouette
katsayısında, bir değer 1’e ne kadar yakında kümeleme sonucunun o kadar
başarılı olduğunu söyleyebiliriz. Fakat bizim buradaki önceliğimizin
küme sayısı belirlemek olduğunu hatırlayalım. Tüm gözlemlerin silhouette
değerlerini toplayıp veri setindeki gözlem sayısına bölersek kümeleme
sonucunun Silhouette değerine ulaşmış oluruz. Fakat yine, bu bölümdeki
önceliğimizle çelişen bir sonuç elde etmiş olduk. Küme sayısını
belirlemek için belirli aralıkta(örneğin 2 ile 10 arasında) her bir
sayıda küme için kümeleme yapılıp, her bir kümelemenin silhouette
değerini hesaplayıp en yüksek değeri ararsak bu sefer Silhouette
yöntemini küme sayısı belirlemek için kullanmış oluruz.

Yine `fviz_nbclust` fonksiyonu optimum küme sayısına karar vermek için
ortalama silhoutte grafiğini görmenin bir yoludur:

``` r
fviz_nbclust(df, # veri
             kmeans, # kümeleme algoritması
             method = "silhouette") # silhouette grafiği için 
```

![](index_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

Grafikten kolayca görülebileceği gibi, en yüksek silhouette değerine
sahip kümeleme modeli 2 küme için kümelemedir. Dolayısıyla optimum küme
sayısının iki olduğu sonucuna varılabilir. Ancak, y eksenindeki
silhouette değerleri incelendiğinde, 2 küme sayısı en yüksek olmasına
rağmen 3 küme sayısının silhouette değeri de oldukça yakındır. Bu
nedenle kümeleme algoritmasının hem 2 hem de 3 küme için çalıştırılması
ve sonuçların yorumlanması daha faydalı olacaktır. Tıpkı Dirsek
Yönteminde olduğu gibi, Ortalama Silhouette yöntemine de tek başına
güvenilmemelidir. Veri setini 2 ve 3 küme sayısı için kümeleyip;
kümelerin genel yapısını analiz etmek her yöntemden daha güvenilir
olacaktır.

## 2.3. Gap İstatistiği

farklı k değerleri için gözlemlenen küme içi varyansı, verilerin boş bir
referans dağılımı altında beklenen varyansla karşılaştırarak küme
geçerliliğini ölçen bir metriktir ve altı farklı adımla hesaplanır.
\[5\]

1.  Genellikle 2 ila 10 arasında bir k değeri aralığı seçilir.

2.  Her k değeri için arzu edilen kümeleme algoritmasıyla veri seti
    kümelenir ve küme içi varyans hesaplanır.

3.  Orijinal veriler rassal örneklenerek referans kümeler oluşturulur ve
    oluşturulan her kümenin küme içi varyansı hesaplanır.

4.  Gerçek kümelerin küme içi varyansı ile ve referans kümelerin küme
    içi varyansları birbirinin farkı alınarak Gap İstatistik değeri elde
    edilir.

5.  Her k değeri için ayrı ayrı Gap İstatistik değeri hesaplanır.

6.  Maksimum Gap İstatistiğine karşılık gelen k değeri optimum küme
    sayısıdır.

Tıpkı diğer yöntemlerde olduğu gibi `fviz_nbclust` fonksiyonu kullanarak
Gap İstatistik methodunun çizgi grafiğini çizdirebiliriz:

``` r
fviz_nbclust(df, 
             kmeans ,
             nstart = 25, 
             method = "gap_stat")
```

![](index_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

Ortalama Siluet Yöntemi gibi Gap İstatistiği Yöntemi de optimum küme
sayısı olarak 2’yi önermektedir.

## 2.4. Calinski-Harabasz Yöntemi

Varyans Oranı Kriteri olarak da bilinen Calinski-Harabasz, tıpkı diğer
yöntemler gibi, küme geçerliliği ve küme sayı belirlemede kullanılır.
Kümeler arası varyans ile küme içi varyansın bir oranı olarak da
açıklanabilecek yöntem üç farklı adımda hesaplanır\[6\].

1.  Her bir küme için, o kümede bulunan bütün gözlemlerin küme merkezine
    olan uzaklıklarının ortalaması hesaplanır. WCSS olarak da
    adlandırılabilir

    ![](https://cdn-images-1.medium.com/max/800/1*4WNGuodDuuGJE_rCGrQwLw.png)

2.  Her bir küme için o kümenin merkezinin veri setinin merkezine olan
    uzaklığı hesaplanır. BCSS olarak adlandırabiliriz.

    ![](https://cdn-images-1.medium.com/max/800/1*aeLLLdSZe-juNaQIm2irbQ.png)

3.  Aşağıdaki formül kullanılarak her bir küme için Calinski-Harabasz
    katsayısı hesaplanır.

(BCSS / WCSS) — (n-k) / (k-1)

\*burada k toplam küme sayısını, n ise veri setindeki toplam gözlem
sayısını ifade eder.

Calinski-Harabasz indeksi 0 ile sonsuz arasında değerler alır ve daha
yüksek bir değer daha iyi bir kümelemeye işaret eder. Calinski -
Harabasz yöntemi için R’da daha önce bahsettiğim yöntemlerde olduğu gibi
bir görselleştirme fonksiyonu bulunmamaktadır. Bu nedenle, `fpc`
paketindeki `calinhara` fonksiyonunu kullanarak 2 ila 10 arasındaki
kümeler için Calinski - Harabasz değerlerini hesaplayan ve
görselleştiren bir fonksiyon yazalım.

``` r
library(fpc) # calinhara fonksiyonu için kütüphanenin çağırılması

fviz_ch <- function(data) { # fonksiyonun oluşturulması: tek girdisi veri seti
  ch <- c()
  for (i in 2:10) { # 2 ile 10 küme sayısı için bir döngü
    km <- kmeans(data, i) # kümelemenin uygulanması
    ch[i] <- calinhara(data, # veri seti
                       km$cluster, # kümeleme atamaları
                       cn=max(km$cluster) # toplam küme sayısı
                       ) # döngüdeki küme sayısı için calinski-harabasz değerinin hesaplanması
  }
  ch <-ch[2:10] # hesaplanan ch değerlerinin bir nesnede toplanması
  k <- 2:10 
  plot(k, ch,xlab =  "Cluster number k",
       ylab = "Caliński - Harabasz Score",
       main = "Caliński - Harabasz Plot", cex.main=1,
       col = "dodgerblue1", cex = 0.9 ,
       lty=1 , type="o" , lwd=1, pch=4,
       bty = "l",
       las = 1, cex.axis = 0.8, tcl  = -0.2) # çizgi grafiği
  abline(v=which(ch==max(ch)) + 1, lwd=1, col="red", lty="dashed") # maksimum değeri işaret edecek dikey kesikli çizgi
}

fviz_ch(df) # grafiğin çizdirilmesi
```

![](index_files/figure-gfm/unnamed-chunk-5-1.png)<!-- -->

Tıpkı diğer yöntemler gibi Calinski - Harabasz da 2 küme önermektedir.

## 2.5. Davies-Bouldin Yöntemi

Davies-Bouldin kümeler arasındaki benzerliği ölçen bir küme geçerliliği
ve küme sayısı belirleme metriğidir\[7\]. Üç ana adımda aşağıdaki gibi
hesaplanır:

1.  Her bir küme için, o kümede bulunan bütün gözlemlerin küme merkezine
    olan uzaklıklarının ortalaması hesaplanır.

    ![](https://cdn-images-1.medium.com/max/800/1*aeLLLdSZe-juNaQIm2irbQ.png)

2.  Her bir kümenin merkezinin diğer kümelerin merkezine olan uzaklığı
    hesaplanır.

    ![](https://cdn-images-1.medium.com/max/800/1*HtFg6se9Yzdt8jE5zRnLmw.png)

3.  Her bir kümenin kendisine en benzer olan, yani merkezler arasındaki
    mesafesi minimum olan değer bulunur. Bu iki kümenin birinci adımda
    hesaplanan değerlerinin toplamı bu iki kümenin merkezi arasındaki
    mesafeye bölünür. Böylelikle her bir küme için en benzer küme
    bulunmuş olur. Ardından bütün kümelerin bu değerleri toplanıp küme
    sayısına bölünerek o kümelemenin Davies-Bouldin katsayısı
    hesaplanmış olur.

Davies-Bouldin indeksi 0 ile sonsuz arasında değerler alır ve daha düşük
bir değer daha iyi bir kümelemeye işaret eder. Bu değerin 0 olması
herhangi iki küme arasında benzerlik olmadığını gösterirken; yüksek
olması bazı kümeler arasında yüksek düzeyde benzerlik olduğunu gösterir.

Tıpkı Calinski-Harabasz yönteminde olduğu gibi Davies-Bouldin yöntemi
için de R’da bir görselleştirme fonksiyonu bulunmamaktadır. Bu nedenle,
`NbClust` paketindeki `NbClust` fonksiyonunu kullanarak 2 ila 10
arasındaki kümeler için Davies Bouldin değerini hesaplayan ve
görselleştiren bir fonksiyon yazalım.

``` r
library(NbClust)

fviz_db <- function(data) {
  k <- c(2:10)
  nb <- NbClust(data, min.nc = 2, max.nc = 10, index = "db", method = "kmeans")
  db <- as.vector(nb$All.index)
  plot(k, db,xlab =  "Cluster number k",
       ylab = "Davies-Bouldin Score",
       main = "Davies-Bouldin Plot", cex.main=1,
       col = "dodgerblue1", cex = 0.9 ,
       lty=1 , type="o" , lwd=1, pch=4,
       bty = "l",
       las = 1, cex.axis = 0.8, tcl  = -0.2)
  abline(v=which(db==min(db)) + 1, lwd=1, col="red", lty="dashed")
}

fviz_db(df)
```

![](index_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->

Diğer yöntemlerden farklı olarak Davies-Bouldin’in küme sayısı için
önerisinin 7 olduğunu görüyoruz. Bu veri setinde farklı sonuçlar verse
de diğer veri setlerinde daha güvenilir sonuçlar verebilir. Bu nedenle
her kümeleme analizinde Davies-Bouldin yöntemine yer verilmesi faydalı
olacaktır.

## 2.6. Dunn Endeksi

Dunn indeksi, bir kümeleme analizindekikümelerin kompaktlığının ve
ayrımının bir ölçüsüdür \[8\] ve aşağıdaki üç adımla hesaplanır:

1.  İki farklı kümeye ait olan gözlemlerin birbiri arasındaki farklar
    hesaplanarak farklı kümelerde olup birbirine en yakın olan gözlem
    hesaplanır. Buna minimum ayrışma adı verilir.

    ![](https://cdn-images-1.medium.com/max/800/1*EHsIVbk6_82UuuxrKn602Q.png)

2.  Aynı kümede yer alan gözlemler arasındaki mesafe hesaplanarak
    birbirine en uzak iki gözlemin arasındaki mesafe hesaplanır ve buna
    maksimum dağılım adı verilir.

    ![](https://cdn-images-1.medium.com/max/800/1*Fl9-NiLKg17SXiz71CMHDw.png)

3.  Minimum ayrışma maksimum dağılıma bölünerek Dunn Endeksi hesaplanır.

Dunn indeksi 0 ile sonsuz arasında değerler alır ve daha yüksek bir
değer daha iyi bir kümelemeye işaret eder. 1 değeri, kümelerin mükemmel
bir şekilde ayrıldığını ve mükemmel bir şekilde kompakt olduğunu
gösterirken, düşük bir değer kümelerin ayrılmadığını veya kompakt
olmadığını gösterir.

Tıpkı Calinski-Harabasz ve Davies- Bouldin yöntemlerinde olduğu gibi
Dunn Index için de R’da görselleştirme fonksiyonu bulunmamaktadır. Bu
nedenle, `clValid` paketindeki `dunn` fonksiyonunu kullanarak 2’den 10’a
kadar olan kümeler için Dunn Index değerlerini hesaplayan ve
görselleştiren bir fonksiyon yazalım.

``` r
library(clValid)
```

    ## Zorunlu paket yükleniyor: cluster

``` r
fviz_dunn <- function(data) {
  k <- c(2:10)
  dunnin <- c()
  for (i in 2:10) {
    dunnin[i] <- dunn(distance = dist(data), clusters = kmeans(data, i)$cluster)
  }
  dunnin <- dunnin[2:10]
  plot(k, dunnin, xlab =  "Cluster number k",
       ylab = "Dunn Index",
       main = "Dunn Plot", cex.main=1,
       col = "dodgerblue1", cex = 0.9 ,
       lty=1 , type="o" , lwd=1, pch=4,
       bty = "l",
       las = 1, cex.axis = 0.8, tcl  = -0.2)
  abline(v=which(dunnin==max(dunnin)) + 1, lwd=1, col="red", lty="dashed")
}

fviz_dunn(df)
```

![](index_files/figure-gfm/unnamed-chunk-7-1.png)<!-- -->

Davies-Bouldin yöntemleri gibi Dunn da farklı küme sayıları önermiştir.
Daha önce de söylediğim gibi, her yöntem her veri seti için farklı
sonuçlar verebilir. Bu nedenle her kümeleme analizinde tüm yöntemlerin
karşılaştırılmasında fayda vardır.

***References for Chapter***

\[1\] Steinley, D., & Brusco, M. J. (2011). Choosing number of clusters
in Κ-means clustering. Psychological methods, 16(3), 285.

\[2\] Halkidi, Maria, Yannis Batistakis, and Michalis Vazirgiannis. “On
clustering validation techniques.” Journal of intelligent information
systems 17 (2001): 107–145.

\[3\] RouKUTeuw, Peter J. Silhouettes: a graphical aid to interpretation
and validation of cluster analysis.Journal of computational and applied
mathematics, 1987, 20: 53–65.

\[4\] Halkidi, M., Batistakis, Y., & Vazirgiannis, M. (2001). On
clustering validation techniques. Journal of intelligent information
systems, 17, 107–145.

\[5\] Tibshirani, R., Walther, G., & Hastie, T. (2001). Estimating
number of clusters in a data set via gap statistic. Journal of Royal
Statistical Society: Series B (Statistical Methodology), 63(2), 411–423.

\[6\] Caliński, T., & Harabasz, J. (1974). A dendrite method for cluster
analysis. Communications in Statistics-theory and Methods, 3(1), 1–27.

\[7\] Davies, D. L., & Bouldin, D. W. (1979). A cluster separation
measure. IEEE transactions on pattern analysis and machine intelligence,
(2), 224–227.

\[8\] Dunn, J. C. (1973). A fuzzy relative of ISODATA process and its
use in detecting compact well-separated clusters.

## k determination cheat sheet

<figure>
<img src="images/machinelearningwithfeo_kdetermination.png"
alt="k-determination-cheat-sheat" />
<figcaption aria-hidden="true">k-determination-cheat-sheat</figcaption>
</figure>

---