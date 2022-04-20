---
title: Son derece hassas veriler için koruma ile ekipleri yapılandırma
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- m365solution-3tiersprotection
- m365solution-securecollab
ms.custom:
- Ent_Solutions
- admindeeplinkSPO
recommendations: false
description: Son derece hassas veriler için koruma ile ekipleri dağıtmayı öğrenin.
ms.openlocfilehash: b104828f5437b9389e83379984a40edf33340f33
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64947571"
---
# <a name="configure-teams-with-protection-for-highly-sensitive-data"></a>Son derece hassas veriler için koruma ile ekipleri yapılandırma

Bu makalede, son derece hassas bir koruma düzeyi için bir ekip ayarlamayı inceleyeceğiz. Bu makaledeki adımları uygulamadan önce [Ekipleri temel korumayla dağıtma](configure-teams-baseline-protection.md) makalesindeki adımları tamamladığınızdan emin olun.

Bu koruma katmanı için, kuruluşunuz genelinde son derece hassas ekipler ve dosyalar için kullanılabilecek bir duyarlılık etiketi oluştururuz. Yalnızca kuruluşunuzun üyeleri ve belirttiğiniz konuklar bu etiketi kullanan dosyaların şifresini çözebilir. Yalnızca belirli bir ekibin üyelerinin dosyaların şifresini çözebilmesi için izinleri daha fazla yalıtmanız gerekiyorsa bkz.  [Güvenlik yalıtımıyla ekip dağıtma](secure-teams-security-isolation.md).

Son derece hassas katman, temel katman üzerinde aşağıdaki ek korumaları sunar:

- Ekip için konuk paylaşımını açmanızı veya kapatmanızı sağlayan ve yönetilmeyen cihazlar için SharePoint içeriğe erişimi engelleyen bir duyarlılık etiketi. Bu etiket, dosyaları sınıflandırmak ve şifrelemek için de kullanılabilir.
- Daha kısıtlayıcı bir varsayılan paylaşım bağlantı türü
- Yalnızca ekip sahipleri özel kanallar oluşturabilir.
- İlişkili SharePoint sitesi için erişim istekleri kapatılır.

## <a name="video-demonstration"></a>Video tanıtımı

Bu makalede açıklanan yordamların kılavuzu için bu videoyu izleyin.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4NzI7]

## <a name="guest-sharing"></a>Konuk paylaşımı

İşletmenizin yapısına bağlı olarak, son derece hassas veriler içeren ekipler için konuk paylaşımını etkinleştirmek isteyebilir veya istemeyebilirsiniz. Ekipte kuruluşunuzun dışındaki kişilerle işbirliği yapmayı planlıyorsanız konuk paylaşımını etkinleştirmenizi öneririz. Microsoft 365, hassas içeriği güvenli bir şekilde paylaşmanıza yardımcı olacak çeşitli güvenlik ve uyumluluk özellikleri içerir. Bu genellikle içeriği doğrudan kuruluşunuzun dışındaki kişilere e-postayla göndermekten daha güvenli bir seçenektir.

Konuklarla güvenli bir şekilde paylaşma hakkında ayrıntılı bilgi için aşağıdaki kaynaklara bakın:

- [Kuruluşunuzun dışındaki kişilerle paylaşım yaparken dosyaların yanlışlıkla açığa çıkmalarını sınırlayın](./share-limit-accidental-exposure.md)
- [Güvenli bir konuk paylaşım ortamı oluşturma](./create-secure-guest-sharing-environment.md)

Konuk paylaşımına izin vermek veya bunları engellemek için ekip için duyarlılık etiketinin ve ilişkili SharePoint sitesi için site düzeyinde paylaşım denetimlerinin bir bileşimini kullanırız. Her ikisi de daha sonra ele alınmalıdır.

## <a name="sensitivity-labels"></a>Duyarlılık etiketleri

Son derece hassas koruma düzeyi için ekibi sınıflandırmak için bir duyarlılık etiketi kullanacağız. Bu etiket, bu veya diğer ekiplerdeki ya da SharePoint ya da OneDrive gibi diğer dosya konumlarındaki tek tek dosyaları sınıflandırmak ve şifrelemek için de kullanılabilir. 

İlk adım olarak, Teams için duyarlılık etiketlerini etkinleştirmeniz gerekir. Ayrıntılar için bkz. [Microsoft Teams, Office 365 Grupları ve SharePoint sitelerindeki içeriği korumak için duyarlılık etiketlerini kullanma](../compliance/sensitivity-labels-teams-groups-sites.md).

Kuruluşunuzda zaten dağıtılmış duyarlılık etiketleriniz varsa, bu etiketin genel etiket stratejinize nasıl uyduğunu göz önünde bulundurun. Kuruluşunuzun gereksinimlerini karşılamak için gerekirse adı veya ayarları değiştirebilirsiniz.

Teams için duyarlılık etiketlerini etkinleştirdikten sonra, sonraki adım etiketi oluşturmaktır.

Duyarlılık etiketi oluşturmak için
1. [Microsoft Purview uyumluluk portalını](https://compliance.microsoft.com) açın.
2. **Çözümler'in** altında **Bilgi koruma'ya** tıklayın.
3. **Etiket oluştur'a** tıklayın.
4. Etikete bir ad verin. **Son derece hassas** kullanmanızı öneririz, ancak bu ad zaten kullanılıyorsa farklı bir ad seçebilirsiniz.
5. Bir görünen ad ve açıklama ekleyin ve **ardından İleri'ye** tıklayın.
6. **Bu etiket için kapsamı tanımla sayfasında****, E-postalar ve Gruplar &** **siteleri &** dosyalar'ı seçin ve **İleri'ye** tıklayın.
7. **Dosyalar ve e-postalar için koruma ayarlarını seçin** sayfasında **Dosyaları ve e-postaları şifrele'yi** seçin ve **ardından İleri'ye** tıklayın.
8. **Şifreleme** sayfasında **Şifreleme ayarlarını yapılandır'ı** seçin.
9. **Belirli kullanıcılara ve gruplara izin ata'nın** altında **İzin ata'ya** tıklayın.
10. **Kuruluşunuzdaki tüm kullanıcıları ve grupları ekle'ye** tıklayın.
11. Dosyaların şifresini çözme izinleri olması gereken konuklar varsa **, Kullanıcı veya grup ekle'ye** tıklayın ve bunları ekleyin.
12.  **Kaydet'e** ve ardından **İleri'ye** tıklayın.
13. *Dosyalar ve e-postalar için otomatik etiketleme** sayfasında **İleri'ye** tıklayın.
14. **Gruplar ve siteler için koruma ayarlarını tanımla** sayfasında **Gizlilik ve dış kullanıcı erişim ayarları ile** **Cihaz erişimi ve dış paylaşım ayarları'nı seçin ve** **İleri'ye** tıklayın.
15. **Gizlilik ve dış kullanıcı erişimi ayarlarını tanımla** sayfasındaki **Gizlilik'in** altında **Özel** seçeneğini belirleyin.
16. Konuk erişimine izin vermek istiyorsanız **Dış kullanıcı erişimi'nin** altında **Grup sahiplerinin kuruluşunuz dışındaki kişileri gruba konuk olarak eklemesine izin Microsoft 365'ı** seçin.
17. **İleri**'ye tıklayın.
18. **Dış paylaşım ve cihaz erişim ayarlarını tanımla** sayfasında **Etiketli SharePoint sitelerden dış paylaşımı denetle'yi** seçin.
19. **İçerik paylaşılabilir** altında, konuk erişimine izin verirseniz **Yeni ve mevcut konuklar'ı** veya **Yalnızca kuruluşunuzdaki kişiler** (paylaşmıyorsanız) seçeneğini belirleyin.
20. **Yönetilmeyen cihazlardan erişim'in** altında **Erişimi engelle'yi** seçin. (Konuklara izin verirseniz ve bunların yönetilen cihazları yoksa Sınırlı **, yalnızca web erişimine izin ver'i** seçebilirsiniz.)
21. **İleri**'ye tıklayın.
22. **Veritabanı sütunları için otomatik etiketleme** sayfasında **İleri'ye** tıklayın.
23. **Etiket oluştur'a** ve ardından **Bitti'ye** tıklayın.

Etiketi oluşturduktan sonra, etiketi kullanacak kullanıcılara yayımlamanız gerekir. Hassas koruma için etiketi tüm kullanıcıların kullanımına sunacağız. Etiketi Microsoft Purview uyumluluk portalında **, Bilgi koruma** sayfasının **Etiket ilkeleri** sekmesinde yayımlarsınız. Tüm kullanıcılar için geçerli olan bir ilkeniz varsa, bu etiketi bu ilkeye ekleyin. Yeni bir ilke oluşturmanız gerekiyorsa bkz. [Etiket ilkesi oluşturarak duyarlılık etiketlerini yayımlama](../compliance/create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy).

## <a name="create-a-team"></a>Ekip oluşturma

Son derece hassas senaryonun daha fazla yapılandırması ekiple ilişkilendirilmiş SharePoint sitesinde yapılır, bu nedenle bir sonraki adım bir ekip oluşturmaktır.

Son derece hassas bilgiler için bir ekip oluşturmak için
1. Teams'da, uygulamanın sol tarafındaki **Teams'e** tıklayın ve ardından ekip listesinin en altında **Katıl'a veya ekip oluştur'a** tıklayın.
2. **Ekip oluştur'a** tıklayın (ilk kart, sol üst köşe).
3. **Sıfırdan ekip oluştur'u** seçin.
4. **Duyarlılık** listesinde, yeni oluşturduğunuz **Yüksek duyarlılığa sahip** etiketi seçin.
5. **Gizlilik'in** altında **Özel'e** tıklayın.
6. Ekip için bir ad yazın ve **Oluştur'a** tıklayın.
7. Takıma kullanıcı ekleyin ve **kapat'a** tıklayın.

## <a name="private-channel-settings"></a>Özel kanal ayarları

Bu katmanda özel kanal oluşturmayı ekip sahipleriyle kısıtlarız.

Özel kanal oluşturmayı kısıtlamak için
1. Ekipte **Diğer seçenekler'e** ve ardından **Ekibi yönet'e** tıklayın.
2. **Ayarlar** sekmesinde **Üye izinleri'ni** genişletin.
3. **Üyelerin özel kanal oluşturmasına izin ver** onay kutusunu temizleyin.

Özel kanal oluşturabilecekleri denetlemek için [teams ilkelerini](/MicrosoftTeams/teams-policies) de kullanabilirsiniz.

## <a name="shared-channel-settings"></a>Paylaşılan kanal ayarları

[Paylaşılan kanalların](/MicrosoftTeams/shared-channels) ekip düzeyinde ayarları yoktur. Teams yönetim merkezinde ve Azure AD'de yapılandırdığınız paylaşılan kanal ayarları, duyarlılık ne olursa olsun tüm ekipler için kullanılabilir.

## <a name="sharepoint-settings"></a>SharePoint ayarları

Son derece hassas etikete sahip yeni bir ekip oluşturduğunuzda, SharePoint'da yapmanız gereken iki adım vardır:

- Varsayılan paylaşım bağlantısını *mevcut erişimi olan kişilere* güncelleştirmek için SharePoint yönetim merkezinde sitenin konuk paylaşım ayarlarını güncelleştirin.
- Üyelerin dosya, klasör veya site paylaşmasını önlemek ve erişim isteklerini kapatmak için sitedeki site paylaşım ayarlarını güncelleştirin.

### <a name="site-default-sharing-link-settings"></a>Site varsayılan paylaşım bağlantısı ayarları

Site varsayılan paylaşım bağlantı türünü güncelleştirmek için

1. SharePoint yönetim merkezini açın ve **Siteler'in** altında <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Etkin siteler'i**</a> seçin.
1. Ekiple ilişkili siteyi seçin.
1. **İlkeler** sekmesinde, **Dış paylaşım'ın** altında **Düzenle'yi** seçin.
1. Varsayılan paylaşım bağlantı türü'nün altında **Kuruluş düzeyi ayarıyla aynı** onay kutusunu temizleyin ve **Mevcut erişimi olan kişiler'i** seçin.
1. **Kaydet**'i seçin.

Takıma özel veya paylaşılan kanallar eklerseniz, her biri varsayılan paylaşım ayarlarıyla yeni bir SharePoint sitesi oluşturur. Ekiple ilişkili siteleri seçerek bunları SharePoint yönetim merkezinde güncelleştirebilirsiniz.

### <a name="site-sharing-settings"></a>Site paylaşım ayarları

SharePoint sitesinin ekip üyesi olmayan kişilerle paylaşılmamasını sağlamaya yardımcı olmak için bu tür paylaşımları sahiplerle sınırlandırıyoruz. Ayrıca dosya ve klasörlerin paylaşımını ekip sahiplerine de sınırlandırıyoruz. Bu, ekip dışındaki biriyle her dosya paylaşıldığında sahiplerin farkında olmasını sağlamaya yardımcı olur.

Yalnızca sahipler için site paylaşımını yapılandırmak için
1. Teams'da güncelleştirmek istediğiniz ekibin **Genel** sekmesine gidin.
2. Ekibin araç çubuğunda **Dosyalar'a** tıklayın.
3. Üç noktaya tıklayın ve ardından **SharePoint aç'a** tıklayın.
4. Temel alınan SharePoint sitesinin araç çubuğunda ayarlar simgesine ve ardından **Site izinleri'ne** tıklayın.
5. **Site izinleri** bölmesinde, **Site paylaşımı'nın** altında Üyelerin **paylaşım şeklini değiştir'e** tıklayın.
6. **Paylaşım izinleri'nin** altında **Yalnızca site sahipleri dosyaları, klasörleri ve siteyi paylaşabilir'i** seçin.
7. **Erişim isteklerine izin ver** seçeneğini **Kapalı** olarak ayarlayın ve Kaydet'e tıklayın.

## <a name="see-also"></a>Ayrıca Bkz

[Duyarlılık etiketleri ve ilkeleri oluşturma ve yapılandırma](../compliance/create-sensitivity-labels.md)
