---
title: Liste veya kitaplığa IRM uygulama
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 7/2/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- OSU150
- OSU160
- MET150
ms.assetid: 3bdb5c4e-94fc-4741-b02f-4e7cc3c54aa1
ms.collection:
- M365-security-compliance
- SPO_Content
description: Listelerden veya kitaplıklardan indirilen dosyaları denetlemeye ve korumaya yardımcı olmak için Bilgi Hakları Yönetimi'ni (IRM) kullanabilirsiniz.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: cf677fc81a20b7e86d9b66505dd8968c0a31272b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633135"
---
# <a name="apply-information-rights-management-irm-to-a-list-or-library"></a>Bir liste veya kitaplığa Bilgi Hakları Yönetimi (IRM) uygulama

Listelerden veya kitaplıklardan indirilen dosyaları denetlemeye ve korumaya yardımcı olmak için Bilgi Hakları Yönetimi'ni (IRM) kullanabilirsiniz. Bu özellik yalnızca Microsoft genel bulutunda desteklenir. IRM, ulusal bulut dağıtımlarındaki SharePoint listeleri ve kitaplıkları için desteklenmez.
  
## <a name="administrator-preparations-before-applying-irm"></a>IRM'yi uygulamadan önce yönetici hazırlıkları

- Azure Information Protection'den Azure Rights Management hizmeti (Azure RMS) ve şirket içi eşdeğeri Active Directory Rights Management Services (AD RMS), siteler için Bilgi Hakları Yönetimi'ni destekler. Ayrı veya ek yükleme gerekmez.

- IRM'yi bir liste veya kitaplığa uygulamadan önce, siteniz için IRM'yi etkinleştirmeniz gerekir. IRM'yi etkinleştirmek için yönetici izinlerine sahip olmanız gerekir.

- IRM'yi bir liste veya kitaplığa uygulamak için, bu liste veya kitaplık için yönetici izinlerine sahip olmanız gerekir.

- SharePoint Online kullanıyorsanız, kullanıcılarınız daha büyük IRM korumalı dosyaları indirirken zaman aşımlarıyla karşılaşabilir. Zaman aşımlarını önlemek için Office programlarınızı kullanarak IRM koruması uygulayın ve daha büyük dosyaları IRM kullanmayan bir SharePoint kitaplığında depolayın.

> [!NOTE]
> SharePoint Server 2013 kullanıyorsanız, bir sunucu yöneticisinin kuruluşunuzdaki kişilerin IRM kullanarak korumak istediği her dosya türü için tüm ön uç Web sunucularına koruyucular yüklemesi gerekir.
  
## <a name="apply-irm-to-a-list-or-library"></a>Liste veya kitaplığa IRM uygulama
<a name="__toc256598179"> </a>

![Bilgi Hakları Yönetimi Ayarları.](../media/1b708102-9c90-42b0-b255-ef0e72d0be88.png)
  
1. IRM'yi yapılandırmak istediğiniz listeye veya kitaplığa gidin.

2. Şeritte **Kitaplık** sekmesini ve ardından **Kitaplık Ayarları'nı** seçin. (Listede çalışıyorsanız Liste sekmesini ve ardından **Liste Ayarları'nı** seçin).
    
    ![Şeritteki SharePoint Kitaplığı Ayarları düğmeleri.](../media/cdf718fa-d792-40fc-8026-00c3b80b9e05.png)
  
3. **İzinler ve Yönetim'in** altında **Bilgi Hakları Yönetimi'ne** tıklayın. Bilgi Hakları Yönetimi bağlantısı görünmüyorsa, siteniz için IRM etkinleştirilmemiş olabilir. Siteniz için IRM'yi etkinleştirip etkinleştiremediğini görmek için sunucu yöneticinize başvurun. Resim kitaplıkları için **Bilgi Hakları Yönetimi** bağlantısı görünmez.

4. **Bilgi Hakları Yönetimi Ayarları** sayfasında, kullanıcıların bu listeden veya **kitaplıktan indiren belgelere kısıtlı izin uygulamak için İndirmede bu kitaplıktaki** belgelere izni kısıtla onay kutusunu seçin.

5. **İzin ilkesi başlığı oluştur** kutusuna ilke için açıklayıcı bir ad girin. Bu ilkeyi diğer ilkelerden tanımlamanıza yardımcı olan bir ad kullanın. Örneğin, gizli şirket belgeleri içeren bir liste veya kitaplığa kısıtlı izinler uygulamak için **Gizli** Şirket'i kullanın.

6. **İzin ilkesi açıklaması ekle** kutusuna, bu liste veya kitaplığı kullanan kişilerin bu liste veya kitaplıktaki belgeleri nasıl işlemeleri gerektiğini açıklayan bir açıklama yazın. Örneğin, bu belgedeki bilgilere erişimi şirket içi çalışanlarla kısıtlamak istiyorsanız Bu **belgenin içeriğini yalnızca diğer çalışanlarla** tartışın yazabilirsiniz. 

7. Bu liste veya kitaplıktaki belgelere ek kısıtlamalar uygulamak için **Seçenekleri Göster'i** seçin ve aşağıdakilerden birini yapın:

|**Bunu yapmak için:**|**Bunu yapın:**|
|:-----|:-----|
|Kişilerin bu liste veya kitaplıktan belge yazdırmasına izin ver|**Görüntüleyicilerin yazdırmasına izin ver** onay kutusunu seçin.|
|En azından Öğeleri Görüntüleme izni olan kişilerin belge üzerinde ekli kod veya makro çalıştırmasına izin verin.|**İzleyicilerin indirilen belgelerde betik ve ekran okuyucu çalıştırmasına izin ver** onay kutusunu seçin. Bu seçeneği seçerseniz, kullanıcılar belgenin içeriğini ayıklamak için kod çalıştırabilir.           |
|İçeriğe erişimi belirli bir süreyle kısıtlamak istiyorsanız bu seçeneği belirleyin. Bu seçeneği belirtirseniz, kişilerin içeriğe erişim izni verme lisansları belirtilen gün sayısından sonra sona erer ve kişilerin kimlik bilgilerini doğrulamak ve yeni bir kopya indirmek için sunucuya geri dönmeleri gerekir.|**İndirmeden sonra, belge erişim haklarının süresi bu kadar gün (1-365) sonra dolacak** onay kutusunu seçin ve belgenin görüntülenebilen gün sayısını belirtin.|
| Kişilerin IRM'yi desteklemeyen belgeleri bu listeye veya kitaplığa yüklemesini engelleyin. Bu seçeneği seçerseniz, kişiler aşağıdaki dosya türlerinden hiçbirini karşıya yükleyemez: Ön uç web sunucularının tümüne karşılık gelen IRM koruyucuları yüklü olmayan dosya türleri. SharePoint Server 2010'un şifresini çözemediği dosya türleri. IRM korumalı dosya türleri başka bir programda.|**Kullanıcıların IRM'yi desteklemeyen belgeleri karşıya yüklemesine izin verme** onay kutusunu seçin.|
|Belirli bir tarihte bu listeden veya kitaplıktan kısıtlanmış izinleri kaldırın.|**Kitaplık erişimini kısıtlamayı durdur** onay kutusunu ve ardından istediğiniz tarihi seçin.|
|Belgeyi açmak üzere lisanslanan program için kimlik bilgilerinin önbelleğe alınma aralığını denetleyin.|**Kullanıcılar bu aralığı (gün) kullanarak kimlik bilgilerini doğrulamalıdır** onay kutusunu seçin, ardından kimlik bilgilerini gün sayısı olarak önbelleğe alma aralığını girin.|
|Kullanıcıların aynı grubun üyeleriyle paylaşabilmesi için grup korumasına izin verin.|**Grup korumasına izin ver'i** seçin ve paylaşım için grubun adını girin.|

8. İstediğiniz seçenekleri belirlemeyi tamamladıktan sonra **Tamam'ı** seçin.
  
## <a name="what-is-information-rights-management"></a>Bilgi Hakları Yönetimi nedir?
<a name="__toc256598175"> </a>

Bilgi Hakları Yönetimi (IRM), kullanıcıların listelerden veya kitaplıklardan indirilmiş dosyalarda gerçekleştirebileceği eylemleri sınırlamanıza olanak tanır. IRM indirilen dosyaları şifreler ve bu dosyaların şifresini çözmesine izin verilen kullanıcı ve program kümesini sınırlar. IRM ayrıca dosyaları okumasına izin verilen kullanıcıların haklarını sınırlayabilir, böylece dosyaların kopyalarını yazdırma veya onlardan metin kopyalama gibi eylemler gerçekleştiremezler.
  
IRM'yi listelerde veya kitaplıklarda kullanarak hassas içeriğin dağıtımını sınırlayabilirsiniz. Örneğin, yaklaşan ürünlerle ilgili bilgileri seçili pazarlama temsilcileriyle paylaşmak için bir belge kitaplığı oluşturuyorsanız, bu kişilerin bu içeriği şirketteki diğer çalışanlarla paylaşmasını önlemek için IRM'yi kullanabilirsiniz.
  
Bir sitede, IRM'yi tek tek dosyalar yerine listenin veya kitaplığın tamamına uygularsınız. Bu, belge veya dosya kümesinin tamamı için tutarlı bir koruma düzeyi sağlamayı kolaylaştırır. Böylece IRM, kuruluşunuzun gizli veya özel bilgilerin kullanımını ve dağıtılmalarını yöneten kurumsal ilkeleri zorunlu kılmasında yardımcı olabilir.
  
> [!NOTE]
> Bilgi Hakları Yönetimi ile ilgili bu sayfadaki bilgiler, herhangi bir Microsoft SharePoint Server 2013 ve SharePoint Server 2016 lisans dönemi sözleşmelerinde 'Bilgi Hakları Yönetimi'ne başvuran tüm terimlerin yerini alır. 
  
### <a name="how-irm-can-help-protect-content"></a>IRM içeriğin korunmasına nasıl yardımcı olabilir?
<a name="__toc256598176"> </a>

IRM, kısıtlanmış içeriğin aşağıdaki yollarla korunmasına yardımcı olur:
  
- Yetkili görüntüleyicinin yetkisiz kullanım için içeriği kopyalamasını, değiştirmesini, yazdırmasını, fakslamasını veya kopyalayıp yapıştırmasını önlemeye yardımcı olur
    
- Microsoft Windows'ta Ekran Yazdır özelliğini kullanarak yetkili görüntüleyicinin içeriği kopyalamasını önlemeye yardımcı olur
    
- Yetkisiz görüntüleyicinin, sunucudan indirildikten sonra e-postayla gönderildiğinde içeriği görüntülemesini önlemeye yardımcı olur
    
- İçeriğe erişimi belirli bir süreyle kısıtlar, bundan sonra kullanıcıların kimlik bilgilerini onaylaması ve içeriği yeniden indirmesi gerekir
    
- Kuruluşunuzdaki içeriğin kullanımını ve dağıtımını yöneten şirket ilkelerinin uygulanmasına yardımcı olur
    
### <a name="how-irm-cannot-help-protect-content"></a>IRM içeriği korumaya nasıl yardımcı olamaz?
<a name="__toc256598177"> </a>

IRM kısıtlanmış içeriği aşağıdakilerden koruyamaz:
  
- Truva atları, tuş vuruşu kaydedicileri ve belirli casus yazılım türleri gibi kötü amaçlı programlar tarafından silinme, hırsızlık, yakalama veya iletim
    
- Bilgisayar virüslerinin eylemleri nedeniyle kayıp veya bozulma
    
- Ekrandaki içeriği el ile kopyalama veya yeniden yazma
    
- Ekranda görüntülenen içeriğin dijital veya film fotoğrafı
    
- Üçüncü taraf ekran yakalama programlarının kullanımı aracılığıyla kopyalama
    
- Üçüncü taraf ekran yakalama programları veya kopyalama ve yapıştırma eylemi aracılığıyla içerik meta verilerinin (sütun değerleri) kopyalanması
  
## <a name="how-irm-works-for-lists-and-libraries"></a>IRM listeler ve kitaplıklar için nasıl çalışır?
<a name="__toc256598178"> </a>

IRM koruması, liste veya kitaplık düzeyindeki dosyalara uygulanır. IRM bir kitaplık için etkinleştirildiğinde, hak yönetimi bu kitaplıktaki tüm dosyalara uygulanır. IRM bir liste için etkinleştirildiğinde, hak yönetimi gerçek liste öğelerine değil, yalnızca liste öğelerine eklenmiş dosyalara uygulanır.
  
IRM özellikli bir liste veya kitaplıktaki dosyalar indirildiğinde, dosyalar yalnızca yetkili kişilerin görüntüleyebilmesi için şifrelenir. Haklarla yönetilen her dosya, dosyayı görüntüleyen kişilere kısıtlamalar getiren bir verme lisansı da içerir. Tipik kısıtlamalar arasında bir dosyanın salt okunur hale getirilmesi, metnin kopyalanmasının devre dışı bırakılması, kişilerin yerel kopyayı kaydetmesini engelleme ve kişilerin dosyayı yazdırmasını engelleme sayılabilir. IRM tarafından desteklenen dosya türlerini okuyabilen istemci programları, bu kısıtlamaları zorlamak için haklarla yönetilen dosya içindeki verme lisansını kullanır. Haklarla yönetilen bir dosya, sunucudan indirildikten sonra bile korumasını böyle korur.
  
Bir listeden veya kitaplıktan indirildiğinde dosyaya uygulanan kısıtlama türleri, tek tek kullanıcının dosyayı içeren sitedeki izinlerini temel alır. Aşağıdaki tabloda sitelerdeki izinlerin IRM izinlerine nasıl karşılık olduğu açıklanmaktadır.
  
|**İzinler**|**IRM İzinleri**|
|:-----|:-----|
|İzinleri Yönetme, Web Sitesini Yönetme|**Tam denetim** (istemci programı tarafından tanımlandığı gibi): Bu izin genellikle kullanıcının haklarla yönetilen içeriğin izinlerini okumasına, düzenlemesine, kopyalamasına, kaydetmesine ve değiştirmesine olanak tanır.|
|Öğeleri Düzenleme, Listeleri Yönetme, Sayfa Ekleme ve Özelleştirme|**Düzenleme**, **Kopyalama** ve **Kaydetme**: Kullanıcı bir dosyayı yalnızca **kullanıcıların belge yazdırmasına izin ver** onay kutusu liste veya kitaplığın Bilgi Hakları Yönetimi Ayarları sayfasında seçiliyse yazdırabilir.|
|Öğeleri Görüntüle|**Okuma**: Kullanıcı belgeyi okuyabilir, ancak içeriğini kopyalayamaz veya değiştiremez. Kullanıcı yalnızca, liste veya kitaplığın Bilgi Hakları Yönetimi Ayarları sayfasında **Kullanıcıların belge yazdırmasına izin ver** onay kutusu seçiliyse yazdırabilir.|
|Diğer|Başka hiçbir izin doğrudan IRM izinlerine karşılık gelir.|
   
SharePoint Server 2013'te bir liste veya kitaplık için IRM'yi etkinleştirdiğinizde, söz konusu liste veya kitaplıktaki dosya türlerini yalnızca tüm ön uç web sunucularına koruyucusu yüklenmiş olarak koruyabilirsiniz. Koruyucu, belirli bir dosya biçimindeki haklarla yönetilen dosyaların şifrelenmesini ve şifresinin çözülmesini denetleyan bir programdır. SharePoint aşağıdaki dosya türleri için koruyucular içerir:
  
- Microsoft Office InfoPath formları
    
- Aşağıdaki Microsoft Office programları için 97-2003 dosya biçimleri: Word, Excel ve PowerPoint
    
- Aşağıdaki Microsoft Office programları için Office Open XML Biçimleri: Word, Excel ve PowerPoint
    
- XML Kağıt Belirtimi (XPS) biçimi
    
Kuruluşunuz yukarıda listelenenlere ek olarak diğer dosya türlerini korumak için IRM kullanmayı planlıyorsa, sunucu yöneticinizin bu ek dosya biçimleri için koruyucular yüklemesi gerekir.
  

