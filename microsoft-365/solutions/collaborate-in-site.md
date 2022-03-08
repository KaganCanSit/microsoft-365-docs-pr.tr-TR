---
title: Bir sitede konuklarla işbirliği yapma
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-3tiersprotection
- m365solution-securecollab
- m365initiative-externalcollab
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.localizationpriority: medium
f1.keywords: NOCSH
recommendations: false
description: Konuklarla işbirliği Microsoft 365 bir siteyi ayarlamak için SharePoint yapılandırma adımları hakkında bilgi alın.
ms.openlocfilehash: 7187149324f88c64570549429f86291320431566
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63318547"
---
# <a name="collaborate-with-guests-in-a-site"></a>Bir sitede konuklarla işbirliği yapma

Konuklarla belgeler, veriler ve listeler arasında işbirliği yapma gerekirse, bir konuk SharePoint kullanabilirsiniz. Modern SharePoint siteleri Microsoft 365 Gruplarla bağlantılıdır ve site üyeliğini yönetebilir ve paylaşılan posta kutusu ve takvim gibi ek işbirliği araçları sağlar.

Bu makalede, konuklarla işbirliğine Microsoft 365 yönelik bir SharePoint yapılandırma adımlarını takip edeceğiz.

## <a name="video-demonstration"></a>Video tanıtımı

Bu videoda, bu belgede açıklanan yapılandırma adımları gösterir.</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44Llg?autoplay=false]

## <a name="azure-external-collaboration-settings"></a>Azure dış işbirliği ayarları

Dış Microsoft 365, çalışma sayfasındaki [B2B dış işbirliği ayarları tarafından en yüksek Azure Active Directory](/azure/active-directory/external-identities/delegate-invitations). Azure AD'de konuk paylaşımı devre dışı bırakılmış veya kısıtlanmışsa, bu ayar Microsoft 365.

Konuklarla paylaşımın engellenmiş olduğundan emin olmak için B2B dış işbirliği ayarlarını kontrol edin.

![Dış işbirliği Azure Active Directory sayfası Ayarlar ekran görüntüsü.](../media/azure-ad-organizational-relationships-settings.png)

Dış işbirliği ayarlarını ayarlamak için

1. Azure Active Directory'ta oturum açma[https://aad.portal.azure.com](https://aad.portal.azure.com).
2. Sol gezinti bölmesinde Ekle'ye **Azure Active Directory**.
3. Dış **kimlikler'e tıklayın**.
4. Çalışmaya başlama **ekranında,** sol gezinti bölmesinde Dış işbirliği **ayarları'ne tıklayın**.
5. Belirli yönetici **rollerine atanan** Üye kullanıcıların ve kullanıcıların, konuk kullanıcılar (üye izinleri olan konuklar dahil) davet etme veya Kuruluşta herkes konuk kullanıcılar (konuklar ve yönetici olmayanlar) seçili olarak davet olabilir.
6. Değişiklikler yaptıysanız Kaydet'e **tıklayın**.

İşbirliği kısıtlamaları bölümündeki **ayarlara dikkat** edin. Konukların işbirliği yapmak istediğiniz etki alanlarının engellenmiş olduğundan emin olun.

Birden çok kuruluştan konuklarla çalışıyorsanız, dizin verilerine erişim izinlerini kısıtlamak istemeyebilirsiniz. Bu, dizinde başka kimlerin konuk olduğunu görmelerini önler. Bunu yapmak için Konuk kullanıcı erişimi kısıtlamaları'nın **altında Konuk kullanıcıların** özelliklere erişimi ve dizin nesneleri ayarları üyeliği sınırlı seçeneğini veya Konuk kullanıcı erişimi kendi dizin nesnelerinin özellik ve üyelikleriyle **sınırlıdır**.

## <a name="microsoft-365-groups-guest-settings"></a>Microsoft 365 Grupları konuk ayarlarını değiştirme

Modern SharePoint sitelerde, site Microsoft 365 denetimi için Grup Gruplarında kullanılır. Microsoft 365 sitelerinde konuk erişiminin çalışması için Grup Gruplarında konuk SharePoint açık olması gerekir.

![Grup Grup Microsoft 365 ayarlarının ekran Microsoft 365 yönetim merkezi.](../media/office-365-groups-guest-settings.png)

Grup konuk Microsoft 365 ayarlarını ayarlamak için

1. Gezinti Microsoft 365 yönetim merkezi gezinti bölmesinde Gezinti **Bölmesi'ni Ayarlar**.
2. Kuruluş **ayarları'ne tıklayın**.
3. Listede Grup **Ekle'Microsoft 365 tıklayın**.
4. Grup sahiplerinin kuruluş **dışından kişi eklemesine izin ver Microsoft 365 Grupları** konuk olarak ekle ve Konuk grup üyelerinin grup içeriğine erişmesine izin **ver onay** kutularının her ikisi de işaretlidir.
5. Değişiklik yaptıysanız, Değişiklikleri **kaydet'e tıklayın**.

## <a name="sharepoint-organization-level-sharing-settings"></a>SharePoint düzeyinde paylaşım ayarlarını değiştirme

Konukların sitelere erişimleri için SharePoint, kuruluş SharePoint düzeyinde paylaşım ayarlarının konuklarla paylaşıma izin vermesi gerekir.

Tek tek siteler için  hangi ayarların kullanılabilir olacağını kuruluş düzeyinde ayarlar belirler. Site ayarları, kuruluş düzeyindeki ayarlardan daha izinli olamaz.

Kimliği doğrulanmamış dosya ve klasör paylaşımına izin vermek için Herkes'i **seçin**. Kuruluş dışındaki tüm kişilerin kimlik doğrulaması yapmak zorunda olduğundan emin olmak için Yeni ve mevcut **konuklar'ı seçin**. Kuruluş herhangi bir site tarafından gerekli olacak en izinli ayarı seçin.

![Kuruluş düzeyi SharePoint ayarlarının ekran görüntüsü.](../media/sharepoint-organization-external-sharing-controls.png)


Kuruluş SharePoint paylaşım ayarlarını ayarlamak için

1. Gezinti Microsoft 365 yönetim merkezi, Yönetim merkezleri altında, Sol gezinti **bölmesindeKimlik'i SharePoint**.
2. SharePoint yönetim merkezinde, sol gezinti bölmesinde, İlkeler'in **altında Paylaşım'ı** <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**seçin**</a>.
3. Dış paylaşım için dış SharePoint Herkes veya Yeni **ve var olan** **konuklar olarak ayarlayın**.
4. Değişiklik yaptıysanız Kaydet'i **seçin**.

## <a name="create-a-site"></a>Site oluşturma

Sonraki adım, konuklarla işbirliği yapmak için kullanmayı planlayın siteyi oluşturmaktır.

Site oluşturmak için
1. Yönetim merkezinde SharePoint altında Etkin <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**siteler'i seçin**</a>.
2. **Oluştur**’u seçin.
3. Ekip **sitesi'ne seçin**.
4. Bir site adı yazın ve Grup sahibi (site sahibi) için bir ad girin.
5. Gelişmiş **ayarlar'ın** altında, bu sitenin genel mi yoksa özel site mi olacağını seçin.
6. **İleri**'yi seçin.
7. **Bitir'i** seçin.

Kullanıcıları daha sonra davetacağız. Daha sonra, bu site için site düzeyinde paylaşım ayarlarını denetlemeniz önemlidir.

## <a name="sharepoint-site-level-sharing-settings"></a>SharePoint düzeyinde paylaşım ayarlarını değiştirme

Bu site için istediğiniz erişim türüne izin vermelerini sağlayan site düzeyinde paylaşım ayarlarını kontrol edin. Örneğin, kuruluş düzeyi ayarlarını Herkes olarak ayarlarsanız **ancak tüm** konukların bu site için kimlik doğrulaması yapmalarını istiyorsanız, site düzeyinde paylaşım ayarlarının Yeni ve var olan konuklar olarak ayarlanmış olduğundan **emin olun**.

Sitenin kimliği doğrulanmamış kullanıcılarla paylaşılanamay (Herkes ayarı), ancak tek tek dosyalar ve klasörler paylaşabilirsiniz.

Duyarlılık etiketlerini, [site site sitelerinin dış paylaşım ayarlarını kontrol etmek SharePoint kullanabilirsiniz](../compliance/sensitivity-labels-teams-groups-sites.md).

![Site dış SharePoint ayarlarının ekran görüntüsü.](../media/sharepoint-site-external-sharing-settings.png)

Site düzeyinde paylaşım ayarlarını ayarlamak için
1. Genel SharePoint, sol gezinti bölmesinde Siteler'i genişletin **ve Etkin** <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**siteler'i seçin**</a>.
2. Paylaşmak istediğiniz siteyi seçin.
3. ... öğesini ve ardından Paylaşım'ı **seçin**.
4. Paylaşımın Herkes veya Yeni ve mevcut **konuklar** **olarak ayarlanmış olduğundan emin olmak**.
5. Değişiklik yaptıysanız Kaydet'i **seçin**.

## <a name="invite-users"></a>Kullanıcıları davet et

Konuk paylaşım ayarları artık yapılandırılmıştır, böylece sitenize iç kullanıcıları ve konukları eklemeye başlayabilirsiniz. Site erişimi ilişkili Microsoft 365 Grubu aracılığıyla denetlenmektedir, dolayısıyla biz de kullanıcıları bu gruba ekliyoruz.

Bir gruba iç kullanıcıları davet etmek için

1. Kullanıcı eklemek istediğiniz siteye gidin.
2. Sağ **üst** köşede üye sayısını ifadeen Üyeler bağlantısı'ı seçin.
3. Üye **ekle'yi seçin**.
4. Siteye davet etmek istediğiniz kullanıcıların adlarını veya e-posta adreslerini yazın ve ardından Kaydet'i **seçin**.

Konuklar bu siteden eklenmiştir. Bunları, Bir Veri Ekle'yi kullanarak Web üzerinde Outlook. Bu nedenle, konukları gruba eklemek ve davet etmek için önkoşul olarak **URL sütununda sitenin URL'sini**  tıklatın ve siteye özgü sayfaya gidin. Bu sayfada Uygulama başlatıcı **simgesine tıklayın ve** Başlatıcı'yı **Outlook**. Bu, aşağıda açıklanan yordamın açıklandığı bir gruba konuk davet edebilirsiniz.

Konukları gruba davet etmek için
1. **Gruplar'ın** altında, konukları davet etmek istediğiniz gruba tıklayın.
2. Grup kişi kartını açın, sağ **üstteki** Üyeler bağlantısına tıklayın (üye sayısını ifade edecek bağlantı).
3. Üye **ekle'ye tıklayın**.
4. Davet etmek istediğiniz konukların e-posta adreslerini yazın ve Ekle'ye **tıklayın**.
5. **Kapat**'a tıklayın.
Yalnızca grubun **sahibi değilseniz** Kapat'a tıklamanız gerekmektedir ve bunun sonucunda konuğu gruba eklemenize izin verilmiyor. Böyle durumlarda, konuğu gruba ekleme isteği onay için grup sahibine aktarılır.

## <a name="see-also"></a>Ayrıca bkz.

[Kimliği doğrulanmamış kullanıcılarla dosya ve klasör paylaşmak için en iyi yöntemler](best-practices-anonymous-sharing.md)

[Konuklarla paylaşım sırasında dosyalarda yanlışlıkla açık kalma sürelerini sınırlama](share-limit-accidental-exposure.md)

[Güvenli bir konuk paylaşım ortamı oluşturma](create-secure-guest-sharing-environment.md)

[Yönetilen konuklarla B2B extranet oluşturma](b2b-extranet.md)

[Azure Active Directory B2B ile SharePoint ve OneDrive tümleştirmesi](/sharepoint/sharepoint-azureb2b-integration-preview)
