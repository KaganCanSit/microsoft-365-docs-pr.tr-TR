---
title: Liste veya kitaplı listeye Bilgi Hakları Yönetimi (IRM) uygulama
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
description: Listelerden veya kitaplıklardan indirilen dosyaları denetlemeye ve korumaya yardımcı olmak için Bilgi Hakları Yönetimi'ne (IRM) sahipebilirsiniz.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 4dfa7360dd178e5943402fcb834236d7d0bf9a08
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988172"
---
# <a name="apply-information-rights-management-irm-to-a-list-or-library"></a>Liste veya kitaplı listeye Bilgi Hakları Yönetimi (IRM) uygulama

Listelerden veya kitaplıklardan indirilen dosyaları denetlemeye ve korumaya yardımcı olmak için Bilgi Hakları Yönetimi'ne (IRM) sahipebilirsiniz. Bu özellik yalnızca Microsoft genel bulutlarında kullanılabilir. IRM, ulusal bulut SharePoint listeleri ve kitaplıkları desteklemez.
  
## <a name="administrator-preparations-before-applying-irm"></a>IRM uygulamadan önce yönetici hazırlıkları

- Azure Information Protection'dan Azure Rights Management hizmeti (Azure RMS) ve şirket içi eşdeğeri olan Active Directory Rights Management Services (AD RMS) siteler için Bilgi Hakları Yönetimi'ne destek olur. Ayrı veya ek yükleme gerekmez.

- IRM'yi bir liste veya kitaplara eklemeden önce, siteniz için IRM'yi etkinleştirmeniz gerekir. IRM'yi etkinleştirmek için yönetici izinlerine ihtiyacınız vardır.

- Bir liste veya kitapma IRM uygulamak için, o liste veya kitaplık üzerinde yönetici izinlerine sahip olmak gerekir.

- SharePoint Online kullanıyorsanız, kullanıcılarınız daha büyük IRM korumalı dosyaları indirirken zaman aşımıyla karşıdan yüklenebilirsiniz. Zaman aşımından kaçınmak için, Office programlarınızı kullanarak IRM koruması uygulayabilir ve büyük dosyaları IRM kullanmayan bir SharePoint kitaplığında depolar.

> [!NOTE]
> SharePoint Server 2013 kullanıyorsanız, bir sunucu yöneticisinin, kurumda IRM kullanarak korumak istediğiniz her dosya türü için tüm ön uç Web sunucularına lisans yüklemesi gerekir.
  
## <a name="apply-irm-to-a-list-or-library"></a>Liste veya kitaplı kitaplara IRM uygulama
<a name="__toc256598179"> </a>

![Bilgi Hakları Yönetimi Ayarlar.](../media/1b708102-9c90-42b0-b255-ef0e72d0be88.png)
  
1. IRM'yi yapılandırmak istediğiniz listeye veya kitaplıma gidin.

2. Şeritte Kitaplık sekmesini seçin **ve** ardından Kitaplık **Kitaplığı'Ayarlar**. (Bir liste üzerinde çalışıyorsanız, Liste sekmesini seçin **ve ardından** Liste **Sekmesi'Ayarlar**).
    
    ![SharePoint Kitaplık Ayarlar düğmeleri.](../media/cdf718fa-d792-40fc-8026-00c3b80b9e05.png)
  
3. **İzinler ve Yönetim'in** altında Bilgi **Hakları Yönetimi'ne tıklayın**. Bilgi Hakları Yönetimi bağlantısı görünmüyorsa, IRM siteniz için etkinleştirilmemiş olabilir. IRM'yi siteniz için etkinleştirebilirsiniz. Resim **kitaplıkları** için Bilgi Hakları Yönetimi bağlantısı görünmüyor.

4. Bilgi **Hakları Yönetimi Ayarlar**, kullanıcıların bu liste veya kitaplıktan indir olduğu  belgelere kısıtlanmış izin uygulamak için, bu kitaplıkta indirme iznini kısıtla onay kutusunu seçin.

5. İzin **ilkesi başlığı oluştur kutusuna** ilke için açıklayıcı bir ad girin. Diğer ilkelerden bu ilkeyi tanımlamanıza yardımcı olacak bir ad kullanın. Örneğin, gizli şirket **belgeleri içeren** bir liste veya kitaplara kısıtlı izinler uygulamak için Şirkete Özel'i kullanın.

6. İzin ilkesi **açıklaması ekle kutusunda** , bu listeyi veya kitaplığı kullanan kişilerin bu liste veya kitaplıkta yer alan belgeleri nasıl işlemeleri gerektiğini açıklayan bir açıklama yazın. Örneğin, bu belgelerde **yer alan bilgilere erişimi** iç çalışanlarla kısıtlamak için Yalnızca diğer çalışanlarla bu belgenin içeriğini tartış yazın. 

7. Bu liste veya kitaplıkta yer alan belgelere ek kısıtlamalar uygulamak için, **Seçenekleri Göster'i** seçin ve şunlardan birini yapın:

|**Bunu yapmak için:**|**Bunu yapmak için:**|
|:-----|:-----|
|Kişilerin bu liste veya kitaplıktan belgeleri yazdırmasına izin ver|Görüntüleyicilerin **yazdırmasına izin ver onay** kutusunu seçin.|
|En azından Öğeleri Görüntüleme izni olan kişilerin belgede eklenmiş kodu veya makroları çalıştırmasına izin verme.|Görüntüleyicilerin **indirilen belgeler üzerinde betik ve ekran okuyucu çalıştırmasına izin ver onay** kutusunu seçin. Bu seçeneği tercih ettiyseniz, kullanıcılar belgenin içeriğini ayıklamak için kod çalıştırabilir.           |
|İçeriğin erişimini belirli bir süreyle kısıtlamak istediğiniz zaman bu seçeneği belirtin. Bu seçeneği belirtirseniz, kişilerin içerik için verme lisanslarının süresi belirtilen sayıda gün dolmaz ve kişilerin kimlik bilgilerini doğrulamak ve yeni bir kopya indirmek için sunucuya geri dönmeleri gerekir.|İndirdikten sonra, belge erişim haklarının süresi bu kadar gün **(1-365)** dolacak onay kutusunu seçin ve ardından belgenin görüntülensin istediğiniz gün sayısını belirtin.|
| Kişilerin IRM desteği olan belgeleri bu listeye veya kitaplı kitaplıya yüklemesini engelin. Bu seçeneği belirtirseniz, kişiler aşağıdaki dosya türlerinden herhangi birini yükleyemz: Ön uç web sunucularının tümsinde karşılık gelen IRM dosya türleri yüklü olmayan dosya türleri. Server 2010'SharePoint çözemedi dosya türleri. Başka bir programda IRM korumalı olan dosya türleri.|Kullanıcıların **IRM desteği olan belgeleri karşıya yüklemesine izin verme onay** kutusunu seçin.|
|Belirli bir tarihte bu liste veya kitaplıktan kısıtlanmış izinleri kaldırın.|Kitaplık **için erişimi kısıtlamayı durdur onay kutusunu** seçin ve sonra da istediğiniz tarihi seçin.|
|Belgeyi açmak için lisans alınmış olan program için kimlik bilgilerinin önbelleğe alınma aralığını denetleme.|Kullanıcıların kimlik **bilgilerini bu süre (gün) kullanarak** doğrulamaları gerekir onay kutusunu seçin, ardından kimlik bilgilerini önbelleğe alma aralığını gün sayısı içinde girin.|
|Kullanıcıların aynı grubun üyeleriyle paylaş olması için grup korumasına izin ver.|Grup **korumasına izin** ver'i seçin ve paylaşım için grubun adını girin.|

8. İstediğiniz seçenekleri seçmeyi bitirdikten sonra Tamam'ı **seçin**.
  
## <a name="what-is-information-rights-management"></a>Bilgi Hakları Yönetimi nedir?
<a name="__toc256598175"> </a>

Bilgi Hakları Yönetimi (IRM), kullanıcıların listelerden veya kitaplıklardan indirilen dosyalar üzerinde gerçekleştir eylemleri sınırlamaya olanak sağlar. IRM indirilen dosyaları şifreler ve bu dosyaların şifresini çözme izni olan kullanıcı ve program kümelerini sınırlar. Ayrıca IRM, dosyaları okuma izni olan kullanıcıların haklarını da sınırlandırarak dosyaların kopyalarını yazdırma veya metin kopyalama gibi eylemleri gerçekleştirememelerini sağlar.
  
Hassas içeriğin yayınlarını sınırlamak için IRM'yi listelerde veya kitaplıklarda kullanabilirsiniz. Örneğin, yaklaşan ürünler hakkında seçili pazarlama temsilcileriyle bilgi paylaşmak için bir belge kitaplığı oluşturuyorsanız, bu kişilerin bu içeriği şirket çalışanıyla diğer çalışanlarla paylaşmasını önlemek için IRM kullanabilirsiniz.
  
Bir sitede, IRM'i tek tek dosyalara değil, listenin veya kitaplığın tamamına uygulayabilirsiniz. Bu, tüm belge veya dosyalar kümesi için tutarlı bir koruma düzeyi olmasını kolaylaştırır. IRM, gizli veya özel bilgilerin kullanımını ve gizliliğini yöneten şirket ilkelerini zorunlu kullanmalarına yardımcı olabilir.
  
> [!NOTE]
> Bilgi Hakları Yönetimi ile ilgili bu sayfada yer alan bilgiler, herhangi bir Microsoft SharePoint Server 2013 ve SharePoint Server 2016 lisans süresi sözleşmesinde 'Bilgi Hakları Yönetimi'ne' başvurulan tüm koşulların yönetimini almaktadır. 
  
### <a name="how-irm-can-help-protect-content"></a>IRM, içeriği korumaya nasıl yardımcı olabilir?
<a name="__toc256598176"> </a>

IRM, kısıtlanmış içeriği aşağıdaki yollarla korumaya yardımcı olur:
  
- Yetkili bir görüntüleyicinin içeriği yetkisiz kullanım için kopyalamasını, değiştirmesini, yazdırmasını, fakslamasını veya kopyalayıp yapıştırarak engellemeye yardımcı olur
    
- Microsoft Web Sitesinde Yazdırma Ekranı özelliğini kullanarak yetkili bir görüntüleyicinin içeriği kopyalamasını önlemeye yardımcı Windows
    
- Sunucudan indirildikten sonra e-postayla gönderilen içeriği yetkisiz bir görüntüleyicinin görüntülemesini önlemeye yardımcı olur
    
- İçeriklere erişimi belirtilen bir süreyle kısıtlar; bundan sonra kullanıcıların kimlik bilgilerini onaylaması ve içeriği yeniden indirmesi gerekir
    
- kuruluş içinde içeriğin kullanımını ve yayınını yöneten şirket ilkelerinin zorunlu kılınmalarına yardımcı olur
    
### <a name="how-irm-cannot-help-protect-content"></a>IRM, içeriğin korunmasına nasıl yardımcı olamaz?
<a name="__toc256598177"> </a>

IRM, kısıtlanmış içeriği aşağıdakilerden koruyamaz:
  
- Truva atları, tuş vuruşu kaydediciler ve belirli türde casus yazılımlar gibi kötü amaçlı programlar tarafından silme, hırsızlık, yakalama veya iletim
    
- Bilgisayar virüslerinin eylemleri nedeniyle kayıp veya bozulma
    
- Ekrandan içeriği el ile kopyalama veya yeniden ekran görüntüsünden yeniden kullanma
    
- Ekranda görüntülenen içeriğin dijital veya film fotoğrafları
    
- Üçüncü taraf ekran yakalama programlarının kullanımı yoluyla kopyalama
    
- Üçüncü taraf ekran yakalama programları veya kopyalayıp yapıştırma eylemi aracılığıyla içerik meta verilerini (sütun değerleri) kopyalama
  
## <a name="how-irm-works-for-lists-and-libraries"></a>IRM listeler ve kitaplıklar için nasıl çalışır?
<a name="__toc256598178"> </a>

IRM koruması dosyalara liste veya kitaplık düzeyinde uygulanır. IRM bir kitaplık için etkinleştirildiğinde, hak yönetimi o kitaplıkta yer alan tüm dosyalara uygulanır. IRM bir liste için etkinleştirildiğinde, hak yönetimi gerçek liste öğelerine değil, yalnızca liste öğelerine eklenmiş dosyalara uygulanır.
  
Kişiler bir IRM etkinleştirilmiş liste veya kitaplıkta dosya indirdikten sonra, bu dosyalar şifrelenir ve böylelikle yalnızca yetkili kişiler bunları ilebilir. Hak yönetimi olan her dosya aynı zamanda dosyayı gören kişiler üzerinde kısıtlamalar dayatan bir verme lisansı içerir. Genel kısıtlamalar arasında dosyayı salt okunur yapma, metin kopyalamayı devre dışı bırakma, kişilerin yerel bir kopya kaydetmesini ve dosyayı yazdırmasını önleme gibi kısıtlamalar yer almaktadır. IRM desteği olan dosya türlerini okuyabilen istemci programları, bu kısıtlamaları uygulamak için hakları yönetilen dosyanın içindeki verme lisansını kullanır. Hak yönetimi olan bir dosya sunucudan indirildikten sonra bile korumasını böyle korur.
  
Bir dosya liste veya kitaplıktan indirilirken dosyaya uygulanan kısıtlama türleri, kullanıcının dosyayı içeren siteyle ilgili izinlerine göre uygulanır. Aşağıdaki tabloda, sitelerde izinlerin IRM izinlerine nasıl karşılık gelenler açık bulunmaktadır.
  
|**İzinler**|**IRM İzinleri**|
|:-----|:-----|
|İzinleri Yönetme, Web Sitesini Yönetme|**Tam denetim** (istemci programı tarafından tanımlandığı gibi): Bu izin genellikle kullanıcının hak yönetimi kapsamındaki içeriğin izinlerini okuması, düzenlemesi, kopyalaması, kaydetmesi ve değiştirmesi için olanak sağlar.|
|Öğeleri Düzenleme, Listeleri Yönetme, Sayfa Ekleme ve Özelleştirme|**Düzenleme****, Kopyalama** ve **Kaydetme**: Bir kullanıcı ancak liste veya kitaplığın Bilgi Hakları Yönetimi  sayfasında Kullanıcıların belgeleri yazdırmasına izin ver onay kutusu seçili Ayarlar dosyayı yazdırabilirsiniz.|
|Öğeleri Görüntüleme|**Okuma**: Kullanıcı belgeyi okuyabilir ancak içeriğini kopyalayıp değiştiremez. Bir kullanıcı ancak liste **veya kitaplığın** Bilgi Hakları Yönetimi iletişim kutusunun Belge Hakları Yönetimi'Ayarlar izin ver onay kutusu seçildiğinde yazdırılabilir.|
|Diğer|Diğer izinler doğrudan IRM izinlerine karşılık gelen izinler yoktur.|
   
SharePoint Server 2013'te bir liste veya kitaplık için IRM'yi etkinleştirirken, yalnızca bu liste veya kitaplıkta bulunan ve tüm ön uç web sunucularına yüklenmiş olan dosya türlerini koruyabilirsiniz. Bir program, belirli bir dosya biçiminde hak yönetimi olan dosyaların şifrelerini ve şifrelerini çözmeyi kontrol eden bir programdır. SharePoint, aşağıdaki dosya türleri için özel çeşitler içerir:
  
- Microsoft Office Path formlarını doldurma
    
- Aşağıdaki programlara uygun 97-2003 dosya Microsoft Office: Word, Excel ve PowerPoint
    
- Aşağıdaki Office için Open XML Biçimleri'nin Microsoft Office: Word, Excel ve PowerPoint
    
- XML Kağıt Belirtimi (XPS) biçimi
    
Kuruluş, yukarıda listelenenlere ek olarak başka dosya türlerini de korumak üzere IRM kullanmayı planlıyorsa, sunucu yöneticiniz bu ek dosya biçimleri için lisans yüklemesi gerekir.
  

