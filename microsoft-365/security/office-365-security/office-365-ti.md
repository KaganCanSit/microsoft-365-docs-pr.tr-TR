---
title: Tehdit & yanıt özellikleri - Office 365 için Microsoft Defender Plan 2
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 12/09/2019
audience: Admin
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 32405da5-bee1-4a4b-82e5-8399df94c512
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Plan'da tehdit soruşturması ve yanıt Office 365 için Microsoft Defender öğrenin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 53f1077d4ef32c6dc5698aae74de51dd5a421510
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474915"
---
# <a name="threat-investigation-and-response"></a>Tehdit soruşturması ve yanıt

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli Olduğu Yer**
- [Office 365 için Microsoft Defender plan 2](defender-for-office-365.md)


Güvenlik analistleri ve yöneticilerinin [Office 365 için Microsoft Defender](defender-for-office-365.md) yönelik tehdit soruşturması ve yanıt özellikleri, güvenlik analistlerinin ve yöneticilerin Microsoft 365 tarafından kurumsal kullanıcılara yönelik güvenliğini korumalarına yardımcı olur:

- Siber saldırıları kolayca tanıyın, takip edebilir ve anlıyoruz.
- Exchange Online, SharePoint Online, OneDrive İş ve Microsoft Teams'te tehditlere hızlı bir OneDrive İş yardımcı Microsoft Teams.
- Güvenlik işlemlerinin, kuruluşlarına yönelik siber saldırıları önlemesine yardımcı olmak için içgörüler ve bilgi sağlama.
- [E-posta tabanlı kritik tehditlere karşı Office 365](automated-investigation-response-office.md) araştırmayı ve yanıtları otomatik olarak kullanarak.

Tehdit soruşturması ve yanıt özellikleri, portalda bulunan tehditlere ve ilgili yanıt eylemlerine yönelik Microsoft 365 Defender sağlar. Bu içgörüler, kuruluş güvenlik ekibinin kullanıcıları e-posta veya dosya tabanlı saldırılardan korumalarına yardımcı olabilir. Bu özellikler kullanıcı etkinliği, kimlik doğrulama, e-posta, güvenliği tehlikeye atılmış bilgisayarlar ve güvenlik olayları gibi birden çok kaynakta sinyallerin izlenmesine ve bu kaynaklardan veri toplamaya yardımcı olur. İşle ilgili karar vericiler ve güvenlik işlemleri ekibinin bu bilgileri kullanarak, organizasyona yönelik tehditleri anlıyoruz ve buna yanıt vermenizi, fikri mülkiyet haklarınızı korumanızı sağlar.

## <a name="get-acquainted-with-threat-investigation-and-response-tools"></a>Tehdit soruşturması ve yanıt araçlarını yakından tanıyın

Microsoft 365 Defender portalında tehdit soruşturması ve yanıt <https://security.microsoft.com> özellikleri, aşağıdakileri içeren bir dizi araç ve yanıt iş akışıdır:

- [Explorer](#explorer)
- [Olaylar](#incidents)
- [Saldırı benzetimi eğitimi](attack-simulation-training.md)
- [Otomatik araştırma ve yanıt](automated-investigation-response-office.md)

### <a name="explorer"></a>Explorer

Tehditleri çözümlemek, zaman içinde saldırı hacmini görmek ve tehdit aileleri, altyapı gibi daha fazlasını analiz etmek için [Explorer'ı (ve gerçek zamanlı algılamaları)](threat-explorer.md) kullanın. Gezgin (Tehdit Gezgini olarak da adlandırılır), her güvenlik analistinin araştırma iş akışının başlangıç noktasıdır.

:::image type="content" source="../../media/7a7cecee-17f0-4134-bcb8-7cee3f3c3890.png" alt-text="Threat explorer page" lightbox="../../media/7a7cecee-17f0-4134-bcb8-7cee3f3c3890.png":::

Bu raporu şu adreste görüntülemek ve Microsoft 365 Defender portalında görüntülemek için, <https://security.microsoft.com>E-posta ve **işbirliği &** \> **gidin**. Doğrudan Gezgin sayfasına gitmek **için de** bunu kullanın <https://security.microsoft.com/threatexplorer>.

## <a name="office-365-threat-intelligence-connection"></a>Office 365 Tehdit İstihbaratı bağlantısı

Bu özelliğin kullanılabilir olması için, etkin bir Office 365 E5 veya Tehdit İstihbaratı eklentiniz olması gerekir. Daha fazla bilgi için, Office 365 Kurumsal E5 ürün sayfasına bakın.

Bu özelliği kapatarak, posta kutuları ve diğer cihazlarınız arasında kapsamlı bir güvenlik Office 365 için Microsoft Defender yapmak için Microsoft 365 Defender'den Office 365 verileri Windows.

> [!NOTE]
> Bu özelliği etkinleştirmek için uygun lisansa sahip olmak gerekir.

Threat Intelligence içinde bağlamsal cihaz tümleştirmesi Office 365 için Güvenlik ve Uyumluluk panosunda Uç Nokta için Defender ayarlarını etkinleştirmeniz & gerekir.

### <a name="incidents"></a>Olaylar

Uçuş güvenliği olaylarının listesini görmek için Olaylar listesini (Bu liste Araştırma olarak da denir) kullanın. Olaylar, şüpheli e-posta iletileri gibi tehditleri izlemek, daha fazla araştırma ve düzeltme yapmak için kullanılır.

:::image type="content" source="../../media/acadd4c7-d2de-4146-aeb8-90cfad805a9c.png" alt-text="2013'te geçerli Tehdit Olaylarının listesi Office 365" lightbox="../../media/acadd4c7-d2de-4146-aeb8-90cfad805a9c.png":::

daha fazla portalda, 'da yer <https://security.microsoft.com>alan Microsoft 365 Defender geçerli olayları listesini görüntülemek için Olaylar ve uyarılar **&** \> **gidin**. Olaylar sayfasına doğrudan gitmek **için de** bunu kullanın <https://security.microsoft.com/incidents>.

:::image type="content" source="../../media/e0f46454-fa38-40f0-a120-b595614d1d22.png" alt-text="Güvenlik ve Uyumluluk Merkezi'nde & sayfası" lightbox="../../media/e0f46454-fa38-40f0-a120-b595614d1d22.png":::

### <a name="attack-simulation-training"></a>Saldırı benzetimi eğitimi

Organizasyon içinde gerçekçi siber saldırıları ayarlamak ve çalıştırmak ve gerçek bir siber saldırıların işlerinizi etkilemeden önce savunmasız kişilerini tanımlamak için Saldırı benzetimi eğitimini kullanın. Daha fazla bilgi edinmek için bkz [. Kimlik avı saldırısının benzetimini yapmak](attack-simulation-training.md).

Bu özelliği web sitesi portalında (Microsoft 365 Defender) <https://security.microsoft.com> >  görüntülemek ve kullanmak için, E-posta ve işbirliği & **benzetim eğitimi'ne gidin**. Veya doğrudan Saldırı benzetimi **eğitim sayfasına gitmek** için ' i kullanın <https://security.microsoft.com/attacksimulator?viewid=overview>.

### <a name="automated-investigation-and-response"></a>Otomatik araştırma ve yanıt

zaman kazanmak ve içerikle, cihazlarla ve insanların kuruluşta tehditlere karşı tehditlere karşı işbirliğinden tasarruf etmek için otomatik araştırma ve yanıt (AIR) özelliklerini kullanın. Hava durumu işlemleri, belirli uyarıların tetiklendiğinde veya güvenlik işlemleri ekibinin başlatmış olduğu durumlarda başlayabilir. Daha fazla bilgi edinmek için bkz. [Otomatik araştırma ve Office 365](automated-investigation-response-office.md).

## <a name="threat-intelligence-widgets"></a>Tehdit zekası pencere öğeleri

Plan 2'Office 365 için Microsoft Defender bir parçası olarak, güvenlik analistleri bilinen tehditle ilgili ayrıntıları gözden geçirebilirsiniz. Bu, kullanıcıların güvenli olması için atılacak ek önlem/adımlar olup olmadığını belirlemek için kullanışlıdır.

:::image type="content" source="../../media/11e7d40d-139b-4c56-8d52-c091c8654151.png" alt-text="Son tehditlerle ilgili bilgileri gösteren Güvenlik eğilimleri bölmesi" lightbox="../../media/11e7d40d-139b-4c56-8d52-c091c8654151.png":::

## <a name="how-do-we-get-these-capabilities"></a>Bu özellikleri nasıl elde  yapabiliriz?

Microsoft 365 tehdit soruşturması ve yanıt özellikleri, Enterprise E5'te bulunan veya belirli aboneliklere eklenti olarak bulunan Office 365 için Microsoft Defender Plan 2'ye dahil edilir. Daha fazla bilgi edinmek için bkz[. Office 365 için Defender 1 ve Plan 2](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2).

## <a name="required-roles-and-permissions"></a>Gerekli roller ve izinler

Office 365 için Microsoft Defender tabanlı erişim denetimi kullanır. Azure Active Directory, Microsoft 365 yönetim merkezi portalında belirli roller üzerinden Microsoft 365 Defender atanır.

> [!TIP]
> Güvenlik Yöneticisi gibi bazı roller portalda atanabilir Microsoft 365 Defender, ancak bunun yerine Microsoft 365 yönetim merkezi veya Azure Active Directory kullanabilirsiniz. Roller, rol grupları ve izinler hakkında bilgi için aşağıdaki kaynaklara bakın:
>
> - [Microsoft 365 Defender portalında izinler](permissions-microsoft-365-security-center.md)
> - [Azure AD yerleşik rolleri](/azure/active-directory/roles/permissions-reference)

|Etkinlik|Roller ve izinler|
|---|---|
|Threat & Vulnerability Management panosunun (veya yeni Güvenlik [panosunun) kullanımı](security-dashboard.md) <p> Son veya mevcut tehditlerle ilgili bilgileri görüntüleme|Aşağıdakilerden biri: <ul><li>**Genel Yönetici**</li><li>**Güvenlik Yöneticisi**</li><li>**Güvenlik Okuyucu**</li></ul> <p> Bu roller Azure Active Directory () veya Microsoft 365 yönetim merkezi<https://portal.azure.com>.<https://admin.microsoft.com>|
|Tehditleri [çözümlemek için Gezgin'i (ve gerçek zamanlı algılamaları)](threat-explorer.md) kullanın|Aşağıdakilerden biri: <ul><li>**Genel Yönetici**</li><li>**Güvenlik Yöneticisi**</li><li>**Güvenlik Okuyucu**</li></ul> <p> Bu roller Azure Active Directory () veya Microsoft 365 yönetim merkezi<https://portal.azure.com>.<https://admin.microsoft.com>|
|Olayları Görüntüleme (Araştırma olarak da adlandırılır) <p> Olay e-posta iletileri ekleme|Aşağıdakilerden biri: <ul><li>**Genel Yönetici**</li><li>**Güvenlik Yöneticisi**</li><li>**Güvenlik Okuyucu**</li></ul> <p> Bu roller Azure Active Directory () veya Microsoft 365 yönetim merkezi<https://portal.azure.com>.<https://admin.microsoft.com>|
|Olayda e-posta eylemlerini tetikleme <p> Şüpheli e-posta iletilerini bulma ve silme|Aşağıdakilerden biri: <ul><li>**Genel Yönetici**</li><li>**Güvenlik Yöneticisi** ile **birlikte Arama ve Temizleme** rolü</li></ul> <p> Genel **Yönetici** ve **Güvenlik Yöneticisi** rolleri Azure Active Directory (<https://portal.azure.com>) veya üst bilgi Microsoft 365 yönetim merkezi.<https://admin.microsoft.com> <p> Arama **ve Temizleme rolü** , Microsoft 36 Defender **portalında ( &** işbirliği rollerinin E-posta Adresi'nden atanabilir<https://security.microsoft.com>.|
|Plan 2 Office 365 için Microsoft Defender i başka bir Uç Nokta için Microsoft Defender <p> Plan 2 Office 365 için Microsoft Defender i SIEM sunucusuyla tümleştirin|Genel **Yönetici veya** herhangi **bir kullanıcıya**<https://portal.azure.com> () veya Azure Active Directory Güvenlik Yöneticisi rolü Microsoft 365 yönetim merkezi<https://admin.microsoft.com>. <p> --- **artı** --- <p> Ek uygulamalarda (Microsoft Defender Güvenlik Merkezi veya SIEM sunucunuzda[) atanan](/windows/security/threat-protection/microsoft-defender-atp/user-roles) uygun bir rol.|

## <a name="next-steps"></a>Sonraki adımlar

- [Tehdit İzleyicisi - Yeni ve Dikkat çekici hakkında bilgi](threat-trackers.md)
- [Teslim edilen kötü amaçlı e-postaları bulma ve araştırma (Tehdit Office 365 Yanıtı)](investigate-malicious-email-that-was-delivered.md)
- [Tehdit Office 365 Araştırmayı ve Yanıtı Güvenlikle Tümleştirin Uç Nokta için Microsoft Defender](integrate-office-365-ti-with-mde.md)
- [Kimlik avı saldırılarını benzetimini](attack-simulation-training.md)
