Bayes Teoremı

BAYES Teoremini hesaplamak için bir örnek inceleyelim

Önce bir senaryo tanımlayacağız, ardından manuel bir hesaplama, Ardından Python'da bir hesaplama yapacağız

	Teşhis Testi Senaryosu

	Manuel Hesaplama

	Python Kodu Hesaplama

Teşhis Testi Senaryosu

Bayes Teoreminin faydasının mükemmel ve yaygın olarak kullanılan bir örneği, tıbbi bir teşhis testinin analizidir.

	Senaryo : Covid olabilecek veya olmayabilecek bir insan popülasyonunu (Covid Doğru veya Yanlış) ve Covid saptamak için pozitif veya negatif dönen bir tıbbi test. (Test Pozitif veya Negatif), örneğin Covid hastalığını tespit etmek için bir X testi gibi düşünelim.

	Sorun : Rastgele seçilen bir insanın testi var ve pozitif ise, hastanın covid yakalanma olasılığı nedir?

Manuel Hesaplama

Tıbbi teşhis testleri mükemmel değildir; hatalar olabilir
   Bir hasta Covid olur, ama test onu tespit edemeyebilir. Testin Covid hastalığını tespit etme yeteneği, duyarlılık veya gerçek pozitif oran olarak adlandırılır.

	Bu durumda, test için bir duyarlılık değeri oluşturacağız. Test ancak% 85'lik gerçek bir pozitif oran veya duyarlılıkla mükemmel değildir. Yani Covid olan ve test edilen tüm insanların% 85'i testten pozitif sonuç alacaktır.

	P (Test = Pozitif | Covid = Doğru) = 0.85

	Bilgiler göz önüne alındığında, sezgimiz, hastanın Covid e yakalanma olasılığının% 85 olduğunu öne sürebilir. Fakat sezgilerimiz yanlış.

	Olasılıkları yorumlarken hata o kadar yaygındır ki, kendi adına sahiptir;  taban oran yanılgısı  olarak adlandırılır .

	Bir olayın olasılığının tahmin edilmesindeki hata, taban oranının göz ardı edilmesinden kaynaklanır. Yani, bir teşhis testinin sonuçlarına bakılmaksızın, rastgele seçilen bir kişinin Covid e yakalanma olasılığını göz ardı eder.

	Bu durumda, Covid olasılığının düşük olduğunu varsayabiliriz ve 5.000'de bir kişi veya (0.0002)% 0.02'lik bir uydurma taban oran değeri kullanabiliriz.
     P (Covid= Doğru) =% 0,02.

Senaryomuzu denklemle eşleyelim:

	P (A | B) = P (B | A) * P (A) / P (B)

	P (Covid= Doğru | Test = Pozitif) = P (Test = Pozitif | Covid= Doğru) * P (Covid= Doğru) / P (Test = Pozitif)

	Hastanın Covid e sahip olduğu göz önüne alındığında testin pozitif olma olasılığının% 85 olduğunu biliyoruz ve belirli bir hastanın Covid e yakalanma oranının veya önceki olasılığının% 0,02 olduğunu biliyoruz; bu değerleri yerine koyabiliriz:

P(Covid= Doğru|Test = Pozitif)=0,85 * 0,0002 / P (Test = Pozitif)

P(Test = Pozitif) 'yi bilmiyoruz, doğrudan verilmiyor.

	Bunun yerine aşağıdaki şekilde tahmin edebiliriz:
     P (B) = P (B | A) * P (A) + P (B | A değil) * P (A değil)
     

P (Test = Pozitif) = P (Test = Pozitif | covid= Doğru) * P (covid= Doğru) + P (Test = Pozitif | covid= Yanlış) * P (covid= Yanlış)

	İlk olarak, zaten bildiğimiz P (covid= Doğru) 'nun tamamlayıcısı olarak P (covid= Yanlış) hesaplayabiliriz.

	P (covid= Yanlış) = 1 - P (covid= Doğru)

	= 1 - 0.0002 = 0.9998

	Elimizde ne varsa eklenti yapalım, bilinen değerlerimizi aşağıdaki gibi ekleyebiliriz:

	P(Test=Pozitif)=0.85 * 0.0002+P(Test = Pozitif|covid= Yanlış) * 0.9998

	Hala Covid olmadığı halde pozitif bir test sonucunun olasılığını bilmiyoruz.

	Spesifik olarak, testin covid olmayan kişileri doğru bir şekilde tanımlamada ne kadar iyi olduğunu bilmemiz gerekir. Yani, hastada covid olmadığında (covid= Yanlış) negatif sonucun (Test = Negatif) test edilmesi, gerçek negatif oran veya özgüllük olarak adlandırılır .

	% 95'lik yapmacık bir özgüllük değeri kullanacağız.

	P (Test = Negatif | covid= Yanlış) = 0,95

	Bu son bilgi parçasıyla, yanlış pozitif veya yanlış alarm oranını, gerçek negatif oranın tamamlayıcısı olarak hesaplayabiliriz.

	P (Test = Pozitif | covid= Yanlış) = 1 - P (Test = Negatif | covid= Yanlış)

	= 1 - 0,95

	= 0.05

	Bu yanlış alarm oranını P (Test = Pozitif) hesaplamamıza aşağıdaki şekilde ekleyebiliriz:

	P (Test = Pozitif) = 0.85 * 0.0002 + 0.05 * 0.9998

	P (Test = Pozitif) = 0.00017 + 0.04999

	P (Test = Pozitif) = 0.05016

	Kişinin Covid olup olmadığına bakılmaksızın testin pozitif sonuç verme olasılığı yaklaşık% 5'tir.

	Artık Bayes Teoremini hesaplamak ve pozitif bir test sonucu alırsa rastgele seçilen bir kişinin Covid yakalanma olasılığını tahmin etmek için yeterli bilgiye sahibiz.

	P (Covid= Doğru | Test = Pozitif) = P (Test = Pozitif | Covid= Doğru) * P (Covid= Doğru) / P (Test = Pozitif)

	P (Covid = Doğru | Test = Pozitif) = 0,85 * 0,0002 / 0,05016

	P (Covid= Doğru | Test = Pozitif) = 0.00017 / 0.05016

	P (Covid= Doğru | Test = Pozitif) = 0,003389154704944

	Hesaplama, hastaya bu testle Covid olduğu bildirilirse, Covid olma olasılığının sadece % 0,33 olduğunu göstermektedir.
