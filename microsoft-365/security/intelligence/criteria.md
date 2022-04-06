---
title: Microsoft kötü amaçlı yazılımları ve istenmeyebilecek uygulamaları nasıl tanımlar?
ms.reviewer: ''
description: Microsoft'un kötü amaçlı yazılım mı yoksa istenmeyebilecek bir uygulama mı olduğunu belirlemek için yazılımı gizlilik ihlalleri ve diğer olumsuz davranışlara karşı nasıl gözden geçireceğini öğrenin.
keywords: güvenlik, kötü amaçlı yazılım, virüs araştırma tehditleri, araştırma kötü amaçlı yazılımları, cihaz koruması, bilgisayar bulaşması, virüs bulaşması, açıklamalar, düzeltme, en son tehditler, MMdevice, Microsoft Kötü Amaçlı Yazılımdan Koruma Merkezi, PUA, istenmeyebilecek uygulamalar
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
ms.openlocfilehash: 1f210ee98c8fc51cfa6900b19bb3cb5d5465dbb3
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663558"
---
# <a name="how-microsoft-identifies-malware-and-potentially-unwanted-applications"></a>Microsoft kötü amaçlı yazılımları ve istenmeyebilecek uygulamaları nasıl tanımlar?

Microsoft, cihazlarınızı güvende ve denetimde olduğunuzdan emin olmak için çalışarak keyifli ve üretken bir Windows deneyimi sağlamayı amaçlar. Microsoft, yazılımları ve çevrimiçi içeriği tanımlayıp analiz ederek olası tehditlerden korunmanıza yardımcı olur. Yazılımı indirdiğinizde, yüklediğinizde ve çalıştırdığınızda, indirilen programların itibarını denetler ve bilinen tehditlere karşı korunmanızı sağlarız. Ayrıca, bizim bilmediğimiz yazılımlar hakkında da uyarılırsınız.  

[Analiz için bilinmeyen veya şüpheli yazılımlar göndererek Microsoft'a](https://www.microsoft.com/wdsi/filesubmission/) yardımcı olabilirsiniz. Bu, bilinmeyen veya şüpheli yazılımların itibarını artırmaya başlamak için sistemimiz tarafından taranmasını sağlamaya yardımcı olur. [Analiz için dosya gönderme hakkında daha fazla bilgi edinin](submission-guide.md)

Sonraki bölümlerde, uygulamalar için kullandığımız sınıflandırmalara ve bu sınıflandırmaya yol açan davranış türlerine genel bir bakış sağlanır.

>[!NOTE]
> Yeni kötü amaçlı yazılım biçimleri ve istenmeyebilecek uygulamalar hızla geliştiriliyor ve dağıtılıyor. Aşağıdaki liste kapsamlı olmayabilir ve Microsoft, önceden bildirimde bulunmadan veya duyurulmadan bunları ayarlama, genişletme ve güncelleştirme hakkını saklıdır.

## <a name="unknown--unrecognized-software"></a>Bilinmiyor – Tanınmayan yazılım  

Hiçbir virüsten koruma veya koruma teknolojisi mükemmel değildir. Kötü amaçlı siteleri ve uygulamaları tanımlamak ve engellemek ya da yeni yayımlanan programlara ve sertifikalara güvenmek zaman alır. İnternet'te neredeyse 2 milyar web sitesi ve yazılım sürekli olarak güncelleştirilip yayınlandığında, her site ve program hakkında bilgi sahibi olmak imkansızdır.

Bilinmeyen/Yaygın olarak indirilmeyen uyarıları, algılanmamış olabilecek kötü amaçlı yazılımlar için erken uyarı sistemi olarak düşünün. Yeni kötü amaçlı yazılımların kullanıma sunulma süresi, tanımlanana kadar genellikle bir gecikme yaşanıyor. Yaygın olmayan programların tümü kötü amaçlı değildir, ancak bilinmeyen kategorideki risk tipik kullanıcı için çok daha yüksektir. Bilinmeyen yazılım uyarıları blok değildir. Kullanıcılar isterlerse uygulamayı normal bir şekilde indirip çalıştırmayı seçebilir.

Yeterli veri toplandıktan sonra Microsoft'un güvenlik çözümleri bir belirleme yapabilir. Tehdit bulunamadı ya da bir uygulama veya yazılım kötü amaçlı yazılım veya istenmeyebilecek yazılım olarak kategorilere ayrılmıştır.

## <a name="malware"></a>Malware

Kötü amaçlı yazılım, Microsoft'un *kötü amaçlı* yazılım veya *istenmeyen* yazılım olarak daha ayrıntılı olarak sınıflandıran uygulamalar ve yazılım gibi diğer kodlar için ayrıntılı bir addır.

### <a name="malicious-software"></a>Kötü amaçlı yazılım

Kötü amaçlı yazılım, kullanıcı güvenliğini tehlikeye atan bir uygulama veya koddur. Kötü amaçlı yazılımlar kişisel bilgilerinizi çalabilir, fidye ödeyene kadar cihazınızı kilitler, istenmeyen posta göndermek için cihazınızı kullanabilir veya diğer kötü amaçlı yazılımları indirebilir. Genel olarak, kötü amaçlı yazılımlar kullanıcıları kandırmak, kandırmak veya dolandırmak, savunmasız durumlara yerleştirmek ister.

Microsoft, kötü amaçlı yazılımların çoğunu aşağıdaki kategorilerden birinde sınıflandırır:

* **Backdoor:** Kötü amaçlı korsanlara cihazınıza uzaktan erişim ve cihazınızın denetimini sağlayan bir kötü amaçlı yazılım türü.

* **Komut ve Denetim:** Cihazınıza bulaşan ve yönergeleri almak için bilgisayar korsanlarının komut ve denetim sunucusuyla iletişim kuran bir kötü amaçlı yazılım türü. İletişim kurulduktan sonra bilgisayar korsanları verileri çalabilen, cihazı kapatıp yeniden başlatabilen ve web hizmetlerini kesintiye uğratabilecek komutlar gönderebilir.

* **Downloader:** Cihazınıza diğer kötü amaçlı yazılımları indiren bir kötü amaçlı yazılım türü. Dosyaları indirmek için İnternet'e bağlanması gerekir.

* **Damlalık:** Cihazınıza başka kötü amaçlı yazılım dosyaları yükleyen bir kötü amaçlı yazılım türü. İndiricinin aksine, bir damlalık kötü amaçlı dosyaları bırakmak için İnternet'e bağlanmak zorunda değildir. Bırakılan dosyalar genellikle damlalık içine eklenir.

* **Istismar:** Cihazınıza erişim kazanmak ve kötü amaçlı yazılım yükleme gibi diğer görevleri gerçekleştirmek için yazılım güvenlik açıklarını kullanan bir kod parçası. [Açıklardan yararlanmalar hakkında daha fazla bilgi edinin](exploits-malware.md).

* **Hacktool:** Cihazınıza yetkisiz erişim elde etmek için kullanılabilecek bir araç türü.

* **Makro virüsü:** Microsoft Word veya Excel belgeleri gibi virüslü belgeler arasında yayılan bir kötü amaçlı yazılım türü. Virüs bulaşmış bir belgeyi açtığınızda virüs çalıştırılır.

* **Obfuscator:** Kodunu ve amacını gizleyen ve güvenlik yazılımlarının algılamasını veya kaldırmasını zorlaştıran bir kötü amaçlı yazılım türü.

* **Parola çalan:** Kullanıcı adları ve parolalar gibi kişisel bilgilerinizi toplayan bir kötü amaçlı yazılım türü. Genellikle bastığınız tuşlar ve ziyaret ettiğiniz web siteleri hakkında bilgi toplayan ve gönderen bir keylogger ile birlikte çalışır.

* **Fidye yazılımı:** Dosyalarınızı şifreleyen veya cihazınızı kullanmanızı engelleyebilecek başka değişiklikler yapan bir kötü amaçlı yazılım türü. Ardından cihazınızı yeniden kullanabilmeniz için önce para ödemeniz veya başka eylemler gerçekleştirmeniz gerektiğini belirten bir fidye notu görüntüler. [Fidye yazılımı hakkında daha fazla bilgi edinin](/security/compass/human-operated-ransomware).

* **Sahte güvenlik yazılımı:** Güvenlik yazılımıymış gibi davranan ancak herhangi bir koruma sağlamayan kötü amaçlı yazılım. Bu tür kötü amaçlı yazılımlar genellikle cihazınızda var olmayan tehditlerle ilgili uyarılar görüntüler. Ayrıca hizmetlerini ödemeniz için sizi ikna etmeye çalışır.

* **Trojan:** Zararsız görünmeye çalışan bir kötü amaçlı yazılım türü. Virüs veya solucandan farklı olarak truva atı tek başına yayılmaz. Bunun yerine, kullanıcıları indirme ve yükleme konusunda hileler yapmaya çalışır. Truva atları yüklendikten sonra kişisel bilgileri çalmak, diğer kötü amaçlı yazılımları indirmek veya saldırganlara cihazınıza erişim vermek gibi çeşitli kötü amaçlı etkinlikler gerçekleştirir.

* **Truva atıcısı:** Web siteleri veya uygulamalardaki düğmelere veya benzer denetimlere otomatik olarak tıklayan bir truva atı türü. Saldırganlar bu truva atını kullanarak çevrimiçi reklamlara tıklayabilir. Bu tıklamalar çevrimiçi anketleri veya diğer izleme sistemlerini çarpıtabilir ve hatta cihazınıza uygulama yükleyebilir.

* **Solucan:** Diğer cihazlara yayılan bir kötü amaçlı yazılım türü. Solucanlar e-posta, anlık ileti, dosya paylaşım platformları, sosyal ağlar, ağ paylaşımları ve çıkarılabilir sürücüler aracılığıyla yayılabilir. Gelişmiş solucanlar, yazılım güvenlik açıklarından yararlanarak yayılmayı sağlar.

### <a name="unwanted-software"></a>İstenmeyen yazılım

Microsoft, Windows deneyiminiz üzerinde denetim sahibi olmanız gerektiğine inanıyor. Windows üzerinde çalışan yazılımlar, bilinçli seçimler ve erişilebilir denetimler aracılığıyla cihazınızın denetimini size vermelidir. Microsoft, denetiminizi korumanızı sağlayan yazılım davranışlarını tanımlar. Bu davranışları tam olarak göstermeyen yazılımları "istenmeyen yazılım" olarak sınıflandırırız.

#### <a name="lack-of-choice"></a>Seçim eksikliği

Yazılımın ne yaptığı ve etkin olup olmadığı da dahil olmak üzere cihazınızda neler olduğu hakkında size bildirimde bulunmalısınız.

Seçim eksikliği gösteren yazılımlar:

* Yazılımın davranışı ve amacı ve amacı hakkında belirgin bir bildirim sağlanamaması.

* Yazılımın ne zaman etkin olduğunu net bir şekilde belirtemez. Ayrıca varlığını gizlemeye veya gizlemeye çalışabilir.

* İzin, etkileşim veya onayınız olmadan yazılım yükleyin, yeniden yükleyin veya kaldırın.

* Birincil yazılımla ilişkisini net bir şekilde belirtmeden diğer yazılımları yükleyin.

* Tarayıcıdan veya işletim sisteminden kullanıcı onayı iletişim kutularını atlatın.

* Microsoft'un yazılımı olduğunu iddia etme.

Yazılım, cihazınızla ilgili kararlar alma konusunda sizi yanıltmamalı veya zorlamamalıdır. Seçimlerinizi sınırlayan davranış olarak kabul edilir. Önceki listeye ek olarak, seçim eksikliği gösteren yazılımlar şunları da gösterebilir:

* Cihazınızın durumu hakkında abartılı beyanlar görüntüleyin.

* Cihazınızdaki dosyalar, kayıt defteri girdileri veya diğer öğeler hakkında yanıltıcı veya yanlış talepler oluşturun.

* Taleplerinizi cihazınızın durumu hakkında endişe verici bir şekilde görüntüleyin ve tasdikli sorunları düzeltmek için ödeme veya belirli eylemleri zorunlu kılın.

Etkinliklerinizi veya verilerinizi depolayan veya ileten yazılımlar:

* Size bildirimde bulunur ve bunu yapmak için onay alırsınız. Yazılım, verilerinizi depolama veya iletme ile ilişkili etkinlikleri gizlemek için bunu yapılandıran bir seçenek içermemelidir.

#### <a name="lack-of-control"></a>Denetim eksikliği

Cihazınızdaki yazılımları denetleyebilmeniz gerekir. Yazılım yetkilendirmesini başlatabilmeniz, durdurabilmeniz veya iptal edebilmeniz gerekir.

Denetim eksikliği gösteren yazılımlar:

* Tarayıcı özelliklerini veya ayarlarını görüntülemenizi veya değiştirmenizi engelleyin veya sınırlayın.

* Tarayıcı pencerelerini yetkilendirme olmadan açın.

* Bildirimde bulunmadan ve onay almadan web trafiğini yeniden yönlendirin.

* Onayınız olmadan web sayfası içeriğini değiştirin veya değiştirin.

Gözatma deneyiminizi değiştiren yazılımlar yalnızca yükleme, yürütme, devre dışı bırakma veya kaldırma için tarayıcının desteklenen genişletilebilirlik modelini kullanmalıdır. Desteklenen genişletilebilirlik modelleri sağlamayan tarayıcılar genişletilebilir değildir ve değiştirilmemelidir.

#### <a name="installation-and-removal"></a>Yükleme ve kaldırma

Yazılıma verilen yetkilendirmeyi başlatabilmeniz, durdurabilmeniz veya başka bir şekilde iptal edebilmeniz gerekir. Yazılım yüklemeden önce onayınızı almalıdır ve yüklemeniz, kaldırmanız veya devre dışı bırakmanız için açık ve anlaşılır bir yol sağlamalıdır.

*Kötü yükleme deneyimi* sunan yazılımlar, Microsoft tarafından sınıflandırılan diğer "istenmeyen yazılımları" paketleyip indirebilir.

*Kötü kaldırma deneyimi* sunan yazılımlar şunları gerçekleştirebilir:

* Kaldırmayı denediğinizde kafa karıştırıcı veya yanıltıcı istemler veya açılır pencereler sunun.

* Program Ekle/Kaldır gibi standart yükleme/kaldırma özellikleri kullanılamaz.

#### <a name="advertising-and-advertisements"></a>Reklam ve reklamlar

Bir ürünü veya hizmeti yazılımın kendisi dışında yükselten yazılım, bilgi işlem deneyiminizi engelleyebilir. Reklam sunan yazılımları yüklerken net bir seçim ve denetime sahip olmanız gerekir.

Yazılım tarafından sunulan reklamlar:

* Kullanıcıların reklamı kapatması için açık bir yol ekleyin. Reklamı kapatma eylemi başka bir reklam açmamalıdır.

* Reklamı sunan yazılımın adını ekleyin.

Bu reklamları sunan yazılım şunları yapmalıdır:

* Sunduğu reklamda gösterildiği gibi aynı adı kullanarak yazılım için standart bir kaldırma yöntemi sağlayın.

Size gösterilen reklamlar:

* Web sitesi içeriğinden ayırt edilebilir olun.

* Yanıltma, aldatma veya karıştırma.

* Kötü amaçlı kod içermez.

* Dosya indirme çağırmaz.

#### <a name="consumer-opinion"></a>Tüketici görüşü

Microsoft, [analiz için yazılım gönderebileceğiniz](https://www.microsoft.com/wdsi/filesubmission) dünya çapında bir analistler ve zeka sistemleri ağı sunar. Katılımınız, Microsoft'un yeni kötü amaçlı yazılımları hızla tanımlamalarına yardımcı olur. Analizden sonra Microsoft, açıklanan ölçütleri karşılayan yazılımlar için Güvenlik zekası oluşturur. Bu Güvenlik bilgileri yazılımı kötü amaçlı yazılım olarak tanımlar ve Microsoft Defender Virüsten Koruma ve diğer Microsoft kötü amaçlı yazılımdan koruma çözümleri aracılığıyla tüm kullanıcılar tarafından kullanılabilir.

## <a name="potentially-unwanted-application-pua"></a>İstenmeyebilecek uygulama (PUA)

PUA korumamız, kullanıcı üretkenliğini korumayı ve keyifli Windows deneyimler sağlamayı amaçlar. Bu koruma daha üretken, performanslı ve keyifli Windows deneyimler sunmaya yardımcı olur. Chromium tabanlı Microsoft Edge ve Microsoft Defender Virüsten Koruma PUA korumasını etkinleştirme hakkında yönergeler için bkz. [İstenmeyebilecek uygulamaları algılama ve engelleme](/microsoft-365/security/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus).

*PUA'lar kötü amaçlı yazılım olarak kabul edilmez.*

Microsoft, yazılımları PUA olarak sınıflandırmak için belirli kategorileri ve kategori tanımlarını kullanır.

* **Reklam yazılımı:** Reklamlar veya promosyonlar görüntüleyen ya da kendi dışındaki yazılımlardaki diğer ürünler veya hizmetler için anketleri tamamlamanızı isteyen yazılım. Bu, web sayfalarına reklam ekleyen yazılımları içerir.

* **Torrent yazılımı (yalnızca Enterprise):** Özel olarak eşler arası dosya paylaşım teknolojileriyle kullanılan torrentleri veya diğer dosyaları oluşturmak veya indirmek için kullanılan yazılım.

* **Şifreleme yazılımı (yalnızca Enterprise):** Kripto para madencileri için cihaz kaynaklarınızı kullanan yazılım.

* **Paketleme yazılımı:** Aynı varlık tarafından geliştirilmeyen veya yazılımın çalışması için gerekli olmayan diğer yazılımları yüklemeyi teklif eden yazılım. Ayrıca, bu belgede belirtilen ölçütlere göre PUA olarak nitelendirilen diğer yazılımları yüklemeyi teklif eden yazılımlar.

* **Pazarlama yazılımı:** Kullanıcıların etkinliklerini izleyen ve pazarlama araştırması için kendi dışındaki uygulamalara veya hizmetlere ileten yazılım.

* **Kaçış yazılımı:** Güvenlik ürünlerinin varlığında farklı davranan yazılımlar da dahil olmak üzere güvenlik ürünleri tarafından algılamayı aktif olarak atlatmaya çalışan yazılım.

* **Düşük sektör itibarı:** Güvenilen güvenlik sağlayıcılarının güvenlik ürünleriyle algıladıkları yazılım. Güvenlik sektörü, müşterileri korumaya ve deneyimlerini geliştirmeye kendini adamıştır. Microsoft ve güvenlik sektöründeki diğer kuruluşlar, kullanıcılara mümkün olan en iyi korumayı sağlamak için analiz ettiğimiz dosyalar hakkında sürekli bilgi alışverişinde bulunur.

