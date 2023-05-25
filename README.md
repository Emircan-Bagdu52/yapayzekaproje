<h1>Beton Çatlakları</h1>
Görüntü işleme tekniklerini kullanarak beton yüzeylerdeki çatlakları otomatik olarak tespit etmektir. Bu projenin temel amacı, manuel olarak yapılan beton çatlak tespit işlemlerinin otomatikleştirilmesi ile zaman ve emek tasarrufu sağlamak, hata payını azaltmak ve sonuçları daha tutarlı hale getirmektir. Bu sayede, beton yüzeylerin daha hızlı ve etkili bir şekilde değerlendirilmesi sağlanabilir. Ayrıca, beton yapılarda erken çatlak tespiti yaparak, hasarların daha küçük boyutlarda kalmasını sağlayarak onarım maliyetlerinin azaltılmasına da yardımcı olunabilir.
<h2>Veri Seti</h2>
Veriler çeşitli ODTÜ Kampüs Binalarından toplanmıştır. Veri seti, görüntü sınıflandırması için negatif ve pozitif crack görüntüleri olarak ikiye ayrılmıştır. Her sınıf, RGB kanallı 227 x 227 piksel ile toplam 40000 resim olmak üzere 20000 resme sahiptir

![00001](https://github.com/Emircan-Bagdu52/yapayzekaproje/assets/95845060/45f3c744-085f-46fc-a12b-118581802abb)
![00002](https://github.com/Emircan-Bagdu52/yapayzekaproje/assets/95845060/ae5d5fa3-2e4e-4667-ae11-9e1892f0b5c0)<br>
Pozitif &nbsp;&nbsp;&nbsp;&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;  &nbsp; Negatif
<h2>Veri Ön İşleme</h2>
Projemizin ilk aşamasında modele girdik olarak vermeden ön işleme adımları uygulayacağız bu adımlar:
<ol> 
    <li>Gri Kanala Çevirme,</li> 
    <li>Filtreleme,</li> 
    <li>Thresoldh</li>
    <li>Motfolojik İşlemler</li>
</ol>
olmak üzere adımdan oluşacaktır. 

Görüntü veri ön işlemede ilk olarak resimleri gri  kanala çeviririz bunun nedeni resimler rgb renk kanalları üzerinde işlenir 3 kanal daha fazla işlem yükü getirir gray kanala çevirerek bize resimleri işleme kolaylığı sağlar. Filtreleme adımı uygulayarak görüntüdeki gürültüleri azaltmak, kenarları vurgulamak veya belirli özellikleri çıkarmak için kullanılır. Threshold(eşikleme) adımıyla görüntü üzerindeki bölgeleri ayırmak için eşikleme değeri belirlenir ve bu değer üzerinden resimler siyah veya beyaz piksel olarak belirlenir son olarak morfolojik işlem, aşındırma ve genişleme. Aşındırma işlemi, nesneleri küçültür ve gürültüyü azaltırken, genişleme işlemi nesneleri büyütür ve boşlukları doldurur. Bu işlemler, görüntüdeki gürültüyü azaltmak ve nesneler arasındaki boşlukları kapatmak için kullandık.

<h2>Model Oluşturma</h2>

Model yapımız, girdi olarak aldığımız görüntüleri Convolutional katmanı aracılığıyla filtreler kullanarak Convolutional işlemine tabi tutar. Bu işlem, görüntünün üzerinden öznitelikleri çıkarmak amacıyla gerçekleştirilir ve elde edilen öznitelikler aktivasyon fonksiyonlarına aktarılır. Maxpooling katmanı, öznitelik haritasının boyutunu küçültmek ve öznitelikleri özetlemek için kullanılır. Aşırı uyum sorununu önlemek için Dropout kullanırız. Dropout, belirli bir olasılıkla rastgele nöronları devre dışı bırakarak ağırlıkların güncellenmesini sağlar. Flatten katmanına geldiğimizde, önceki katmandan gelen öznitelik haritasını 1D vektörlere dönüştürür ve çıkış katmanına iletilir. Çıkış katmanı, sınıf sayısı kadar nörona sahiptir. Softmax aktivasyon fonksiyonunu kullanarak olasılık dağılımını hesaplar
![image](https://github.com/Emircan-Bagdu52/yapayzekaproje/assets/95845060/d604cb50-e4b3-4137-89ea-3f311aef5089)

<h2>Model Değerlendirilmesi</h2>
Karmaşıklık matrisi veri setindeki var olan durum ile sınıflandırma modelimizin doğru ve yanlış tahminlerinin sayısını tablo olarak göstermektedir. Accuracy (Doğruluk): Sistemde doğru olarak yapılan tahminlerin tüm tahminlere oranıdır.
![image](https://github.com/Emircan-Bagdu52/yapayzekaproje/assets/95845060/6883a3f5-cb5c-42fe-b3ef-3d7279388548)

<h2>Sonuç</h2>




