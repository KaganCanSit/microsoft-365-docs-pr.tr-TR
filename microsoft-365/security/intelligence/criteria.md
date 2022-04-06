---
title: Microsoft kötü amaçlı yazılımları ve istenmeyen olabilecek uygulamaları nasıl tanımlar?
ms.reviewer: ''
description: Microsoft'un kötü amaçlı yazılım veya istenmeyen olabilecek bir uygulama olup olmadığını belirlemek üzere gizlilik ihlalleri ve diğer negatif davranışlar için yazılımı nasıl gözden gözden uygulaması olduğunu öğrenin.
keywords: güvenlik, kötü amaçlı yazılım, virüs araştırması tehditleri, araştırma kötü amaçlı yazılım, cihaz koruması, bilgisayar bulaşması, virüs bulaşması, açıklamalar, düzeltme, en son tehdit, MMdevice, Microsoft Kötü Amaçlı Yazılımdan Koruma Merkezi, PUA, potansiyel olarak istenmeyen uygulamalar
ms.prod: m365-security
ms.mktglfcycl: secure
ms.sitesec: library
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.date: 12/13/2021
search.appverid: met150
ms.technology: m365d
ms.openlocfilehash: 3eb7eefb5309383b46189f784f811224dcfb2b28
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63705892"
---
# <a name="how-microsoft-identifies-malware-and-potentially-unwanted-applications"></a>Microsoft kötü amaçlı yazılımları ve istenmeyen olabilecek uygulamaları nasıl tanımlar?

Microsoft,güvenli ve cihazlarınızı kontrol altında Windows verimli bir deneyim sunmak için çalışıyor. Microsoft, yazılım ve çevrimiçi içeriği tanımlayarak ve çözümlayarak olası tehditlerden korunmanıza yardımcı olur. Yazılımı indirdiğiniz, yüklemeniz, çalıştırmanız, indirilen programların itibarını kontrol ediyor ve bilinen tehditlere karşı korunmanız gerekiyor. Ayrıca, bizim için bilinmeyen yazılım hakkında da uyarıldınız.  

Bilinmeyen veya şüpheli yazılımları analiz [için göndererek Microsoft'a yardımcı olabilirsiniz](https://www.microsoft.com/wdsi/filesubmission/). Bu, bilinmeyen veya şüpheli yazılımların saygınlığı sağlamaya başlamak için sistemimiz tarafından taranmasında yardımcı olur. [Çözümleme için dosya gönderme hakkında daha fazla bilgi](submission-guide.md)

Sonraki bölümlerde, uygulamalar için kullanılan sınıflandırmalara ve bu sınıflandırmaya yol açacak davranış türlerine genel bir bakış sağlanmıştır.

>[!NOTE]
> Yeni kötü amaçlı yazılım formları ve istenmeyen uygulamalar hızla geliştiriliyor ve dağıtılıyor. Aşağıdaki liste kapsamlı bir liste değildir ve Microsoft önceden bildirim veya duyurulmadan bunları ayarlama, genişletme ve güncelleştirme hakkını saklı tutar.

## <a name="unknown--unrecognized-software"></a>Bilinmiyor – Tanınmayan yazılım  

Virüsten koruma veya koruma teknolojisi mükemmel değildir. Kötü amaçlı site ve uygulamaları tanımlamak ve engellemek ya da yeni yayımlanan programlara ve sertifikalara güvenmek zaman alır.İnternet'te ve yazılımda sürekli güncelleştirilen ve yayımlanan neredeyse 2 milyar web sitesiyle, tek tek her site ve program hakkında bilgi almak imkansızdır.

Bilinmeyen/Seyrek İndirilen uyarılar, algılanmamış kötü amaçlı yazılımlar için erken uyarı sistemi olarak düşünmektedir. Genel olarak, yeni kötü amaçlı yazılım tanımlanana kadar yayımlanana kadar bir gecikme olur. Yaygın olmayan programların hepsi kötü amaçlı değildir, ancak bilinmeyen kategorideki risk normal kullanıcı için çok daha yüksektir. Bilinmeyen yazılımlar için uyarılar bloklar değildir. Kullanıcılar, dilese uygulamayı normal olarak indirmeyi ve çalıştırmayı seçebilir.

Yeterli veri toplanıp toplanıp, Microsoft'un güvenlik çözümleri bir karara varabilirsiniz. Tehdit bulunamıyor ya da bir uygulama veya yazılım kötü amaçlı yazılım veya potansiyel olarak istenmeyen yazılım olarak kategorilere ayrılmıştır.

## <a name="malware"></a>Kötü amaçlı yazılım

Kötü amaçlı yazılım, Microsoft'un kötü amaçlı yazılım veya istenmeyen yazılım olarak daha ayrıntılı bir şekilde sınıflara ekli hale gelen uygulamalar ve yazılım gibi diğer kodlara yönelik *aşırı arşiv* *adıdır*.

### <a name="malicious-software"></a>Kötü amaçlı yazılım

Kötü amaçlı yazılım, kullanıcı güvenliğini tehlikeye atan bir uygulama veya koddur. Kötü amaçlı yazılımlar kişisel bilgilerinizi çalmak, bir lisans ödemesi yapılana, istenmeyen posta göndermek için cihazınızı kullanana veya diğer kötü amaçlı yazılımları indirene kadar cihazınızı kilitler. Genel olarak, kötü amaçlı yazılımlar kullanıcıları kandırmak, hile yapmak veya hile yapmak ister ve onları zayıf devletlere yerleştirmek ister.

Microsoft, en kötü amaçlı yazılımları aşağıdaki kategorilerden birini sınıflandırabilir:

* **Backdoor:** Kötü amaçlı korsanlara cihazınıza uzaktan erişim ve kontrolü veren bir kötü amaçlı yazılım türü.

* **Komut ve Denetim:** Cihazınıza bulaşacak ve bilgisayar korsanlarının komut ve denetim sunucusuyla yönergeler almak için iletişim kuracak bir kötü amaçlı yazılım türü. İletişim kurulduktan sonra bilgisayar korsanları veri çaldıracak komutlar gönderebilir, cihazı kapatıp yeniden başlatıp web hizmetlerini kesintiye neden olabilir.

* **İndirici:** Cihazınıza başka bir kötü amaçlı yazılım indiren bir kötü amaçlı yazılım türü. Dosyaları indirmek için İnternet'e bağlanması gerekir.

* **Dropper:** Cihazınıza başka kötü amaçlı yazılım dosyaları yüken bir kötü amaçlı yazılım türü.İndiriciden farklı olarak, dropper kötü amaçlı dosyaları bırakmak için İnternet'e bağlanmak zorunda değildir. Bırakılan dosyalar genellikle dropper'ın kendisine ekli olarak gelir.

* **Exploit:** Cihazınıza erişim kazanmak ve kötü amaçlı yazılım yüklemek gibi diğer görevleri gerçekleştirmek için yazılım açıklarını kullanan bir kod parçası. [Açıkları hakkında daha fazla bilgi edinebilirsiniz](exploits-malware.md).

* **Hacktool:** Cihazınıza yetkisiz erişim kazanmak için kullanılmaktadır.

* **Makro virüsü:** Virüs bulaşmış belgelere yayılan kötü amaçlı yazılım Microsoft Word veya Excel olabilir. Virüs bulaşmış bir belgeyi a açınca 0 olur.

* **Obfuscator:** Kodunu ve amacını gizleyerek, güvenlik yazılımının algılamasını veya kaldırmasını zorlaştıracak bir kötü amaçlı yazılım t türü.

* **Parola çalmak:** Kullanıcı adları ve parolalar gibi kişisel bilgilerinizi topan bir kötü amaçlı yazılım t türü. Sık sık, basıldık tuşları ve ziyaret ettiğiniz web siteleri hakkında bilgi toplayan ve gönderen bir tuş günlüğüyle birlikte çalışır.

* **Fidye yazılımı:** Dosyalarınızı şifreleyen veya cihazınızı kullanmanızı engel olacak başka değişiklikler yapan bir kötü amaçlı yazılım türü. Ardından, cihazınızı yeniden kullanamadan önce para ödemeniz veya başka işlemler gerçekleştirmeniz gerektiğini gösteren bir not görüntülenir. [Fidye yazılımı hakkında daha fazla bilgi edinebilirsiniz](/security/compass/human-operated-ransomware).

* **Güvenlik yazılımı:** Güvenlik yazılımı gibi olmakla birlikte herhangi bir koruma sağlanmmakta olan kötü amaçlı yazılım. Bu tür bir kötü amaçlı yazılım genellikle aygıtınızda yok olan tehditlerle ilgili uyarılar görüntüler. Ayrıca hizmetleri için ödeme yapmaya ikna etmeye çalışır.

* **Truva:** Zararsız görünmeye çalışan bir kötü amaçlı yazılım türü. Virüs veya solucandan farklı olarak, Truva tek başına yayılmaz. Bunun yerine, kullanıcıların indirme ve yüklemeyle ilgili püf noktalarına karşı yasal bir görünüm yüklemeye çalışır. Yüklendikten sonra, Truvalar kişisel bilgileri çalmak, diğer kötü amaçlı yazılımları indirmek veya cihazınıza saldırganlara erişim vermek gibi çeşitli kötü amaçlı etkinlikler gerçekleştirler.

* **Truva tıkıcı:** Web siteleri veya uygulamalar üzerindeki düğmelere veya benzer denetimlere otomatik olarak tık eden bir truva türü. Saldırganlar çevrimiçi reklamlara tıklamak için bu Truva'yı kullanabilir. Bu tıklamalar çevrimiçi yoklamaları veya diğer izleme sistemlerini çarpıtarak cihazınıza uygulama bile yükleyebilir.

* **Solucan:** Başka cihazlara yayılan bir kötü amaçlı yazılım türü. Solucanlar e-postaya, anlık iletilere, dosya paylaşım platformlarına, sosyal ağlara, ağ paylaşımlarına ve çıkarılabilir sürücülere yayılabilir. Karmaşık solucanlar, yayılmak için yazılım güvenlik açıklarından faydalanıyor.

### <a name="unwanted-software"></a>İstenmeyen yazılım

Microsoft, en iyi deneyiminiz üzerinde denetim altında Windows inanıyor. Yazılım, Windows seçenekler ve erişilebilir denetimler aracılığıyla cihazınızın kontrolünüz altında tutmalı. Microsoft, denetim altında kalmanız için yazılım davranışlarını tanımlar. Bu davranışları tümüyle "istenmeyen yazılım" olarak göstermemeyen yazılımları sınıflandırıyoruz.

#### <a name="lack-of-choice"></a>Seçenek yok

Hangi yazılımın yaptığı ve etkin olup olmadığı dahil olmak üzere, aygıtınızda olup olmadığı konusunda bilgili olun.

Seçenek eksikliğini sergileyen yazılım:

* Yazılımın davranışı, amacı ve amacı hakkında belirgin bir bildirim sağlayamama.

* Yazılımın ne zaman etkin olduğunu açıkça belirtemesiniz. Ayrıca iletişim durumlarını gizlemeyi veya gizlemeyi de sınıyor olabilir.

* İzniniz, etkileşiminiz veya izniniz olmadan yazılımı yükleyin, yeniden yükleyin veya kaldırın.

* Birincil yazılımla ilişkisinin net bir göstergesi olmadan başka bir yazılım yükleyin.

* Tarayıcıdan veya işletim sisteminden kullanıcı izni iletişim kutularını kontrol edin.

* Yanlış şekilde Microsoft'tan yazılım olduğunu iddia eden bir yazılımdır.

Yazılım, cihazınız hakkında karar verme konusunda sizi yanıltmaması veya sizi zor güncelleştirmesine neden olmaz. Tercihlerinizi sınırlayan bir davranış olduğu kabul edilir. Önceki listeye ek olarak, seçenek eksikliğini sergileyen yazılım şunları da olabilir:

* Cihazınızın durumu hakkında abartılı iddialar gösterebilirsiniz.

* Aygıtınızdaki dosyalar, kayıt defteri girdileri veya diğer öğeler hakkında yanıltıcı veya yanlış iddialarda bulunabilirsiniz.

* Cihazınızın durumu hakkında alarm verici bir şekilde taleplerde bulunarak bu sorunların giderilmesi için ödeme ya da bazı eylemler gerektir.

Etkinliklerinizi veya verilerinizi depolar veya iletir yazılım:

* Size bildirim vermek ve bunu yapmak için izin almak. Yazılım, verilerinizi depolama veya iletilen etkinlikleri gizlemek için onu yapılandıran bir seçenek içermesi gerekir.

#### <a name="lack-of-control"></a>Denetim yok

Yazılımı aygıtınızda kontrol edebilirsiniz. Yazılım yetkilendirmeyi başlatabilecek, durdurabilecek veya başka bir şekilde iptal etmek zorunda olacağınız bir lisansa sahip olmak gerekir.

Denetim eksikliğini sergileyen yazılım:

* Tarayıcı özelliklerini veya ayarlarını görüntülemenizi veya değiştirmenizi engelleyin veya sınırlandırma.

* Yetkilendirme olmadan tarayıcı pencerelerini açın.

* Bildirim vermeden ve izin almadan web trafiğini yönlendirin.

* Onayınız olmadan web sayfası içeriğini değiştirebilir veya değiştirebilirsiniz.

Gözatma deneyiminizi destekleyen yazılımlar yalnızca, tarayıcının desteklenen genişletilebilirlik modelini yükleme, yürütme, devre dışı bırakma veya kaldırma için kullan mutlaka. Desteklenen genişletilebilirlik modelleri sağlamayan tarayıcılar genişletilebilir değildir ve değiştirilmemelidir.

#### <a name="installation-and-removal"></a>Yükleme ve kaldırma

Yazılıma verilen yetkiyi başlatabilecek, durdurabilecek veya başka bir şekilde iptal edile bir lisansa sahip olmak gerekir. Yazılım yüklemeden önce izninizi almalı ve yüklemeniz, kaldırmanız veya devre dışı bırakmanız için açık ve açık bir yol sağlamalı.

Kötü yükleme deneyimi *dağıtan yazılımlar Microsoft* tarafından sınıflandırılmış başka "istenmeyen yazılımları" paket olarak paket veya indirebilir.

Kötü kaldırma deneyimi *dağıtan yazılım* şunları olabilir:

* Kaldırmayı deneerek kafa karıştırıcı veya yanıltıcı istemler veya açılır görüntüler s ortaya çıkar.

* Program Ekle/Kaldır gibi standart yükleme/kaldırma özellikleri başarısız oldu.

#### <a name="advertising-and-advertisements"></a>Reklam ve reklamlar

Yazılımın kendi dışında bir ürünü veya hizmeti yükselten yazılım, bilgisayar deneyiminizi engellemeye neden olabilir. Reklamlar sunan yazılımları yüklerken net bir seçiminiz ve denetiminiz olması gerekir.

Yazılım tarafından sunulan reklamlar:

* Kullanıcıların reklamları kapatması için belirgin bir yol sağlar. Reklamları kapatma eylemi başka bir reklam açmaz.

* Tanıtımda sunulan yazılımın adını da yazın.

Bu reklamları sunan yazılım:

* Yazılım için, gösterilen reklamda gösterilen adla standart bir kaldırma yöntemi s s aracı sağla.

Size gösterilen reklamlar:

* Web sitesi içeriğinden ayırt edilebilir olabilir.

* Yanıltıcı, hileli veya kafanızı karıştırmayın.

* Kötü amaçlı kod içermez.

* Dosya indirme için çağırma.

#### <a name="consumer-opinion"></a>Tüketici görüşü

Microsoft, analiz için yazılım gönderebilirsiniz, dünya çapında bir analist ve zeka [sistemi ağı kullanır](https://www.microsoft.com/wdsi/filesubmission). Katılımınız, Microsoft'un yeni kötü amaçlı yazılımları hızla belirlemesi için yardımcı olur. Çözümlemeden sonra, Microsoft tanımlanan ölçütlere uyan yazılımlar için Güvenlik zekası oluşturur. Bu Güvenlik zekası, yazılımı kötü amaçlı yazılım olarak tanımlar ve yazılımdan koruma çözümleri ve diğer Microsoft Microsoft Defender Virüsten Koruma tüm kullanıcılar tarafından kullanılabilir.

## <a name="potentially-unwanted-application-pua"></a>İstenmeyen olabilecek uygulama (PUA)

Kullanıcı üretkenliğini korumak ve kullanıcı deneyimi deneyiminin keyfini çıkarmak için olan PUA Windows korumamız. Bu koruma daha üretken, performansa sahip ve harika deneyimler Windows yardımcı olur. Birden çok tabanlı uygulama veya posta Chromium PUA korumasını Microsoft Edge Microsoft Defender Virüsten Koruma için bkz. Olası istenmeyen uygulamaları [algılama ve engelleme](/microsoft-365/security/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus).

*PUA'lar kötü amaçlı yazılım olarak kabul edilir.*

Microsoft, yazılımı PUA olarak sınıflandırmak için belirli kategorileri ve kategori tanımlarını kullanır.

* **Reklam yazılımı:** Reklamlar veya promosyonlar görüntüleyen ya da kendi dışında bir yazılımda diğer ürünler veya hizmetler için anketler tamamlamanız istenen yazılım. Bu, web sayfalarına reklam eken yazılımlar içerir.

* **Yazılım (Enterprise:** Ağ taşkınları veya özel olarak eşler arası dosya paylaşım teknolojileriyle kullanılan diğer dosyaları oluşturmak veya indirmek için kullanılan yazılım.

* **Şifreleme yazılımı (yalnızca Enterprise yazılımı): Şifrelemeleri** meydana etmek için cihaz kaynaklarınızı kullanan yazılım.

* **Bundling yazılımı:** Aynı varlıkla geliştirnmiş veya yazılımın çalışması için gerekli dışında başka bir yazılım yüklemek için teklif sunan yazılım. Ayrıca, bu belgede belirtilen ölçütlere göre PUA olarak nitelendirilen başka bir yazılım yüklemesi de sunan yazılımlardır.

* **Pazarlama yazılımı:** Pazarlama araştırması için kullanıcıların etkinliklerini izleyen ve kendi dışında uygulamalara veya hizmetlere ileten yazılım.

* **İhale yazılımı:** Güvenlik ürünleri varlığında farklı davranan yazılımlar da dahil olmak üzere, güvenlik ürünleri tarafından algılamayı etkin bir şekilde geri etmeye çalışan yazılım.

* **Kötü endüstri itibarı:** Güvenlik sağlayıcılarının güvenlik ürünleriyle ilgili algılayan yazılım. Güvenlik sektörü, müşterileri korumaya ve deneyimlerini geliştirmeye adanmıştır. Microsoft ve güvenlik sektöründeki diğer kuruluşlar, kullanıcılara mümkün olan en iyi korumayı sağlamak için analiz ettiğimiz dosyalar hakkında sürekli bilgi alışverişinde kullanılmaktadır.

