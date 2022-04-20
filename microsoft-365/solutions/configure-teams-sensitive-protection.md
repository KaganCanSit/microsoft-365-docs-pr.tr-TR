---
title: Hassas veriler için koruma ile ekipleri yapılandırma
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
description: Hassas veriler için koruma ile ekip dağıtmayı öğrenin.
ms.openlocfilehash: 2ea13fbf8a677ba4a04efbd0b2a6fdfed7d80644
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64941291"
---
# <a name="configure-teams-with-protection-for-sensitive-data"></a>Hassas veriler için koruma ile ekipleri yapılandırma

Bu makalede, hassas bir koruma düzeyi için bir ekip ayarlamayı inceleyeceğiz. Bu makaledeki adımları uygulamadan önce [Ekipleri temel korumayla dağıtma](configure-teams-baseline-protection.md) makalesindeki adımları tamamladığınızdan emin olun. Hassas katman, temel katman üzerinde aşağıdaki ek korumaları sunar:

- Ekip için konuk paylaşımını açmanıza veya kapatmanıza olanak tanıyan ve yönetilmeyen cihazlar için SharePoint içeriğe erişimi yalnızca web ile sınırlayan bir duyarlılık etiketi. Bu etiket, dosyaları sınıflandırmak için de kullanılabilir.
- Daha kısıtlayıcı bir varsayılan paylaşım bağlantı türü
- Yalnızca ekip sahipleri özel kanallar oluşturabilir.

## <a name="video-demonstration"></a>Video tanıtımı

Bu makalede açıklanan yordamların kılavuzu için bu videoyu izleyin.
<br>
<br>
> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4NMS6]

## <a name="guest-sharing"></a>Konuk paylaşımı

İşletmenizin yapısına bağlı olarak, hassas veriler içeren ekipler için konuk paylaşımını etkinleştirmek isteyebilir veya istemeyebilirsiniz. Ekipte kuruluşunuzun dışındaki kişilerle işbirliği yapmayı planlıyorsanız konuk paylaşımını etkinleştirmenizi öneririz. Microsoft 365, hassas içeriği güvenli bir şekilde paylaşmanıza yardımcı olacak çeşitli güvenlik ve uyumluluk özellikleri içerir. Bu genellikle içeriği doğrudan kuruluşunuzun dışındaki kişilere e-postayla göndermekten daha güvenli bir seçenektir.

Konuklarla güvenli bir şekilde paylaşma hakkında ayrıntılı bilgi için aşağıdaki kaynaklara bakın:

- [Kuruluşunuzun dışındaki kişilerle paylaşım yaparken dosyaların yanlışlıkla açığa çıkmalarını sınırlayın](./share-limit-accidental-exposure.md)
- [Güvenli bir konuk paylaşım ortamı oluşturma](./create-secure-guest-sharing-environment.md)

Konuk paylaşımına izin vermek veya bunları engellemek için ekip için duyarlılık etiketinin ve ilişkili SharePoint sitesi için site düzeyinde paylaşım denetimlerinin bir bileşimini kullanırız. Her ikisi de daha sonra ele alınmalıdır.

## <a name="sensitivity-labels"></a>Duyarlılık etiketleri

Hassas koruma düzeyi için, ekibi sınıflandırmak için bir duyarlılık etiketi kullanacağız. Bu etiket, bu veya diğer ekiplerdeki ya da SharePoint ya da OneDrive gibi diğer dosya konumlarında ayrı ayrı dosyaları sınıflandırmak için de kullanılabilir. 

İlk adım olarak, Teams için duyarlılık etiketlerini etkinleştirmeniz gerekir. Ayrıntılar için bkz. [Microsoft Teams, Office 365 Grupları ve SharePoint sitelerindeki içeriği korumak için duyarlılık etiketlerini kullanma](../compliance/sensitivity-labels-teams-groups-sites.md).

Kuruluşunuzda zaten dağıtılmış duyarlılık etiketleriniz varsa, bu etiketin genel etiket stratejinize nasıl uyduğunu göz önünde bulundurun. Kuruluşunuzun gereksinimlerini karşılamak için gerekirse adı veya ayarları değiştirebilirsiniz.

Teams için duyarlılık etiketlerini etkinleştirdikten sonra, sonraki adım etiketi oluşturmaktır.

Duyarlılık etiketi oluşturmak için
1. [Microsoft Purview uyumluluk portalını](https://compliance.microsoft.com) açın.
2. **Çözümler'in** altında **Bilgi koruma'ya** tıklayın.
3. **Etiket oluştur'a** tıklayın.
4. Etikete bir ad verin. **Hassas'ı** öneririz, ancak bu ad zaten kullanılıyorsa farklı bir ad seçebilirsiniz.
5. Bir görünen ad ve açıklama ekleyin ve **ardından İleri'ye** tıklayın.
6. **Bu etiket için kapsamı tanımla sayfasında****, E-postalar ve Gruplar &** **siteleri &** dosyalar'ı seçin ve **İleri'ye** tıklayın.
7. **Dosyalar ve e-postalar için koruma ayarlarını seçin** sayfasında **İleri'ye** tıklayın.
8. *Dosyalar ve e-postalar için otomatik etiketleme** sayfasında **İleri'ye** tıklayın.
9. **Gruplar ve siteler için koruma ayarlarını tanımla** sayfasında **Gizlilik ve dış kullanıcı erişim ayarları ile** **Cihaz erişimi ve dış paylaşım ayarları'nı seçin ve** **İleri'ye** tıklayın.
10. **Gizlilik ve dış kullanıcı erişimi ayarlarını tanımla** sayfasındaki **Gizlilik'in** altında **Özel** seçeneğini belirleyin.
11. Konuk erişimine izin vermek istiyorsanız **Dış kullanıcı erişimi'nin** altında **Grup sahiplerinin kuruluşunuz dışındaki kişileri gruba konuk olarak eklemesine izin Microsoft 365'ı** seçin.
12. **İleri**'ye tıklayın.
13. **Dış paylaşım ve cihaz erişim ayarlarını tanımla** sayfasında **Etiketli SharePoint sitelerden dış paylaşımı denetle'yi** seçin.
14. **İçerik paylaşılabilir** altında, konuk erişimine izin verirseniz **Yeni ve mevcut konuklar'ı** veya **Yalnızca kuruluşunuzdaki kişiler** (paylaşmıyorsanız) seçeneğini belirleyin.
15. **Yönetilmeyen cihazlardan erişim'in** altında **Sınırlı, yalnızca web erişimine izin ver'i** seçin.
16. **İleri**'ye tıklayın.
17. **Veritabanı sütunları için otomatik etiketleme** sayfasında **İleri'ye** tıklayın.
18. **Etiket oluştur'a** ve ardından **Bitti'ye** tıklayın.

Etiketi oluşturduktan sonra, etiketi kullanacak kullanıcılara yayımlamanız gerekir. Hassas koruma için etiketi tüm kullanıcıların kullanımına sunacağız. Etiketi Microsoft Purview uyumluluk portalında **, Bilgi koruma** sayfasının **Etiket ilkeleri** sekmesinde yayımlarsınız. Tüm kullanıcılar için geçerli olan bir ilkeniz varsa, bu etiketi bu ilkeye ekleyin. Yeni bir ilke oluşturmanız gerekiyorsa bkz. [Etiket ilkesi oluşturarak duyarlılık etiketlerini yayımlama](../compliance/create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy).

## <a name="create-a-team"></a>Ekip oluşturma

Hassas senaryonun daha fazla yapılandırması ekiple ilişkilendirilmiş SharePoint sitesinde yapılır, bu nedenle bir sonraki adım bir ekip oluşturmaktır.

Hassas bilgiler için ekip oluşturmak için
1. Teams'da, uygulamanın sol tarafındaki **Teams'e** tıklayın ve ardından ekip listesinin en altında **Katıl'a veya ekip oluştur'a** tıklayın.
2. **Ekip oluştur'a** tıklayın (ilk kart, sol üst köşe).
3. **Sıfırdan ekip oluştur'u** seçin.
4. **Duyarlılık** listesinde, yeni oluşturduğunuz **hassas** etiketi seçin.
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

[Paylaşılan kanalların](/MicrosoftTeams/shared-channels) ekip düzeyinde ayarları yoktur. Teams yönetim merkezinde ve Azure AD'de yapılandırdığınız paylaşılan kanal ayarları, duyarlılık ne olursa olsun tüm ekipler için geçerlidir.

## <a name="sharepoint-settings"></a>SharePoint ayarları

Hassas etikete sahip yeni bir ekip oluşturduğunuzda, SharePoint yapmanız gereken iki adım vardır:

- Varsayılan paylaşım bağlantısını *Belirli kişiler* olarak güncelleştirmek için SharePoint yönetim merkezinde sitenin konuk paylaşım ayarlarını güncelleştirin.
- Üyelerin siteyi paylaşmasını önlemek için sitedeki site paylaşım ayarlarını güncelleştirin.

### <a name="site-default-sharing-link-settings"></a>Site varsayılan paylaşım bağlantısı ayarları

Site varsayılan paylaşım bağlantı türünü güncelleştirmek için

1. SharePoint yönetim merkezini açın ve **Siteler'in** altında <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**Etkin siteler'i**</a> seçin.
1. Ekiple ilişkili siteyi seçin.
1. **İlkeler** sekmesinde, **Dış paylaşım'ın** altında **Düzenle'ye** tıklayın.
1. Varsayılan paylaşım bağlantı türü'nün altında **Kuruluş düzeyi ayarıyla aynı** onay kutusunu temizleyin ve **Belirli kişiler (yalnızca kullanıcının belirttiği kişiler)** seçeneğini belirleyin.
1. **Kaydet**'i seçin.

Bunu ekip oluşturma işleminizin bir parçası olarak betik oluşturmak istiyorsanız, varsayılan paylaşım bağlantısını *Belirli kişiler* olarak değiştirmek için [Set-SPOSite](/powershell/module/sharepoint-online/set-sposite) parametresini `-DefaultSharingLinkType Direct` kullanabilirsiniz.

Takıma özel veya paylaşılan kanallar eklerseniz, her biri varsayılan paylaşım ayarlarıyla yeni bir SharePoint sitesi oluşturur. Ekiple ilişkili siteleri seçerek bunları SharePoint yönetim merkezinde güncelleştirebilirsiniz.

### <a name="site-sharing-settings"></a>Site paylaşım ayarları

SharePoint sitesinin ekip üyesi olmayan kişilerle paylaşılmamasını sağlamaya yardımcı olmak için bu tür paylaşımları sahiplerle sınırlandırıyoruz. Bu yalnızca ekiple oluşturulan SharePoint sitesi için gereklidir. Özel veya paylaşılan kanalların bir parçası olarak oluşturulan ek siteler ekip veya kanal dışında paylaşılamaz.

Yalnızca sahipler için site paylaşımını yapılandırmak için
1. Teams'da güncelleştirmek istediğiniz ekibin **Genel** sekmesine gidin.
2. Ekibin araç çubuğunda **Dosyalar'a** tıklayın.
3. Üç noktaya tıklayın ve ardından **SharePoint aç'a** tıklayın.
4. Temel alınan SharePoint sitesinin araç çubuğunda ayarlar simgesine ve ardından **Site izinleri'ne** tıklayın.
5. **Site izinleri** bölmesinde, **Site paylaşımı'nın** altında Üyelerin **paylaşım şeklini değiştir'e** tıklayın.
6. **Paylaşım izinleri'nin** altında **Site sahipleri ve üyeleri'ni seçin ve Düzenleme izinleri olan kişiler dosya ve klasörleri paylaşabilir, ancak siteyi yalnızca site sahipleri paylaşabilir** ve kaydet'e tıklayın.


## <a name="related-topics"></a>İlgili konular

[Duyarlılık etiketleri ve ilkeleri oluşturma ve yapılandırma](../compliance/create-sensitivity-labels.md)
