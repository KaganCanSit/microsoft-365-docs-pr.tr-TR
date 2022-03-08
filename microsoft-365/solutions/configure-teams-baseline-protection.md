---
title: Taban çizgisi korumasıyla ekipleri yapılandırma
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
- admindeeplinkTEAMS
- admindeeplinkSPO
recommendations: false
description: Temel koruma düzeyiyle ekipleri dağıtmayı öğrenin.
ms.openlocfilehash: 21fe46a9df9b67c41ff2c0a21fbbe175295e1fdf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63312747"
---
# <a name="configure-teams-with-baseline-protection"></a>Taban çizgisi korumasıyla ekipleri yapılandırma

Bu makalede, temel koruma düzeyine sahip ekiplerin nasıl dağıtıldıklarının bakıldı. Bu düzey kullanıcılara işbirliği için geniş bir seçenek sunarken izin yönetimini geliştirerek ve aşırı paylaşıma karşı temel koruma sağlar. Bu düzey için önerilen korumalar kimlik ve cihaz erişim ilkelerini ve kötü amaçlı yazılıma karşı korumayı içerir. Buna ek olarak, gerektiğinde koşullu erişim ilkeleri ve veri kaybı korumaları uygulayabilirsiniz.

## <a name="initial-protections"></a>İlk korumalar

İlk adım olarak, temel kimlik ve cihaz erişimi ilkelerini yapılandırmanız önerilir. Ayrıntılar [için bkz. Sohbetlerin, grupların Teams güvenliğini sağlamak için ilke](../security/office-365-security/teams-access-policies.md) önerileri.

Belgeler, ekler ve bağlantılarda kötü amaçlı yazılımlara Office 365 için temel Defender'ı da açmalarını öneririz. Aşağıdaki tabloda yer alan seçeneklerin her birini açmamız önerilir.

|Seçenek|Bilgi|
|:------|:-----------|
|Kasa, Posta ve Posta OneDrive için Teams|[Kasa Ekleri Kaydetme](../security/office-365-security/safe-attachments.md) <p> [Office 365 , SharePoint, OneDrive ve Microsoft Teams için Defender](../security/office-365-security/mdo-for-spo-odb-and-teams.md)|
|Güvenli Belgeler|[Kasa için Microsoft Defender'da Belgeleri Office 365](../security/office-365-security/safe-docs.md)|
|Kasa için Bağlantılar'Teams|[Office 365 Kasa'te Bağlantıları Teams](../security/office-365-security/safe-links.md) <p> [Güvenli Bağlantılar](../security/office-365-security/safe-links.md)|

## <a name="teams-guest-sharing"></a>Teams paylaşımı

Katmanların her biri, kuruluş dışındakilerle paylaşma seçeneğine sahipiz. Hassas ve çok hassas katmanlarda, duyarlılık etiketlerini kullanarak konuk paylaşımını ekip düzeyinde kapatma seçeneğine sahip oluruz. Ancak, konuk paylaşımının tüm ortamda çalışması için kuruluş düzeyinde konuk paylaşımı ayarının Teams.

![Konuk erişimi Teams iki durumlu düğmenin ekran görüntüsü.](../media/teams-guest-access-toggle-on.png)

Konuk erişimi Teams ayarlarını yapmak için

1. hesabıyla oturum Microsoft 365 yönetim merkezi.[https://admin.microsoft.com](https://admin.microsoft.com)
2. Sol gezintide, Hepsini **göster'e tıklayın**.
3. Yönetim **merkezleri altında,** Yönetim **Merkezi'nin Teams**.
4. Genel Teams yönetim merkezinde, sol gezinti bölmesinde Kuruluş çapında **ayarlarGuest** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2173122" target="_blank">**erişimi'ni genişletin**</a>.
5. **E-postada konuk erişimine izin ver Teams'in** On olarak ayar olduğundan emin **olun**.
6. Ek konuk ayarlarında istediğiniz değişiklikleri yapın ve ardından Kaydet'e **tıklayın**.

> [!NOTE]
> Konuk ayarının siz bu ayarı Teams etkin olması yirmi dört saat kadar sürebilir.

Office 365 gruplarında ve SharePoint'te konuk paylaşımı varsayılan olarak açıktır, ancak daha önce kuruma yönelik konuk paylaşım ayarlarından herhangi birini değiştirdiysanız, Teams'de konuk paylaşımının kullanılabilir olduğundan emin olmak için [](./collaborate-as-team.md) Bir ekipte konuklarla işbirliği yap'i gözden geçirmenizi Teams.

## <a name="site-and-file-sharing"></a>Site ve dosya paylaşımı

Dosyalarınızı veya klasörlerinizi yanlışlıkla kuruluş dışındaki kişiler ile paylaşma riskini azaltmak için, SharePoint için varsayılan paylaşım bağlantısını Yalnızca SharePoint *olarak değiştirmenizi öneririz*. (Kullanıcıların dışarıdan paylaşması gerekirse ve konuk paylaşımını etkinleştirdiysek, paylaştığınızda bağlantı türünü değiştirmeye devam etmek için bu özelliği kullanabilirler.)

Varsayılan paylaşım bağlantısını değiştirmek için

1. Yönetim merkezini açın SharePoint altında **Paylaşım'ı** <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**seçin**</a>.
1. Dosya **ve klasör bağlantıları'nın altında** Yalnızca **kuruluşta olan kişiler'i seçin**.
1. **Kaydet**'i seçin.

En iyi konuk paylaşımı deneyimi için, [Azure AD B2B ile SharePoint ve OneDrive tümleştirmeyi etkinleştirmenizi de öneririz](/sharepoint/sharepoint-azureb2b-integration-preview).

## <a name="create-a-team"></a>Ekip oluşturma

Temel koruma düzeyi için ek yapılandırma, ekiple SharePoint ilgili ekip sitesinde yapılır. [Sonraki bölüme devam etmeden önce,](https://support.office.com/article/174adf5f-846b-4780-b765-de1a0a737e2b) genel veya özel bir ekip oluşturun.

## <a name="site-sharing-settings"></a>Site paylaşım ayarları

Varsayılan olarak, sitenin SharePoint başkalarını siteye davet edebilirsiniz. Site bir ekibin parçası olduğunda, ekip üyeleri site üyesi olarak dahil edilir. Bununla birlikte, doğrudan siteye eklenen kişilerin ekibin geri kalanına erişimi yok. Bu nedenle, izinlerin ekip aracılığıyla özel olarak yönetilmesini öneririz.

İzin yönetimine yardımcı olmak için, ilişkili siteyi yalnızca sahiplerin siteyi kendi başına paylaşmasına izin verecek şekilde yapılandırmayı öneririz. Bu, izin yönetimini basitleştirerek ekip sahibinin bilgisi olmayan kişilerin erişimini engellemeye yardımcı olur. Taban çizgisi koruması gerektiren her ekip için bunu yapma.

Site paylaşımı ayarlarını güncelleştirmek için
1. Ekibin araç çubuğunda Dosyalar'a **tıklayın**.
2. Aynı **Dosyada Aç'a SharePoint**.
3. Sitenin araç çubuğunda SharePoint simgesine tıklayın ve sonra da Site **izinleri'ne tıklayın**.
4. Site izinleri **bölmesinde,** Site **paylaşımı'nın altında** Üyelerin **paylaşımlarını değiştir'e tıklayın**.
5. Paylaşım **izinleri'nin** altında **Site sahipleri** ve üyeleri'ne tıklayın; Düzenleme izinleri olan kişiler dosyaları ve klasörleri paylaşabilir; ancak yalnızca site sahipleri siteyi paylaşabilir ve Kaydet'e **tıklayın**.

## <a name="additional-protections"></a>Ek korumalar

Microsoft 365, içeriğinizin güvenliğini sağlamak için ek yöntemler sunar. Aşağıdaki seçeneklerin, organizasyon güvenliğinizi iyileştirmeye yardımcı olup olacağını düşünün.

- Konukların kullanım koşullarını [kabul etmiş göstermelerini s anlayabilirler](/azure/active-directory/conditional-access/terms-of-use).
- Konuklar için [oturum zaman aşımı ilkesi](/azure/active-directory/conditional-access/howto-conditional-access-session-lifetime) yapılandırma.
- Hassas [bilgi türleri oluşturun ve](../compliance/sensitive-information-type-learn-about.md) hassas bilgilere [erişimle ilgili](../compliance/dlp-learn-about-dlp.md) ilkeler ayarlamak için veri kaybına karşı koruma kullanın.

## <a name="see-also"></a>Ayrıca Bkz

[Toplantıda toplantı ilkelerini Teams](/microsoftteams/meeting-policies-in-teams)

[Insider risk yönetimiyle çalışmaya başlama](../compliance/insider-risk-management-configure.md)