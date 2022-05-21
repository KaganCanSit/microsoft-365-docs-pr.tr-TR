---
title: Microsoft Defender Virüsten Koruma tarafından algılanan tehditler
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid: MET150
description: Microsoft Defender Virüsten Koruma'nın Windows cihazlarınızı virüs, kötü amaçlı yazılım ve casus yazılım gibi yazılım tehditlerine karşı nasıl koruyup korumayacağınızı öğrenin.
ms.openlocfilehash: 796edb343745e19267f901b736ca19217b0e4f01
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65620917"
---
# <a name="overview-of-threat-protection-by-microsoft-defender-antivirus"></a>Microsoft Defender Virüsten Koruma'nın tehdit korumasına genel bakış

Microsoft Defender Virüsten Koruma, Windows cihazlarınızı virüs, kötü amaçlı yazılım ve casus yazılım gibi yazılım tehditlerinden korur.

- Virüsler genellikle kodunu cihazınızdaki veya ağınızdaki diğer dosyalara ekleyerek yayılır ve virüslü programların yanlış çalışmasına neden olabilir.
- Kötü amaçlı yazılım, zarara neden olabilecek ve cihazların normal kullanımını kesintiye uğratabilecek kötü amaçlı dosyalar, uygulamalar ve kod içerir. Ayrıca, kötü amaçlı yazılım yetkisiz erişime izin verebilir, sistem kaynaklarını kullanabilir, parolaları ve hesap bilgilerini çalabilir, sizi bilgisayarınızdan kilitleyebilir ve fidye isteyebilir ve daha fazlasını yapabilir.
- Casus yazılımlar web'e gözatma etkinliği gibi verileri toplar ve uzak sunuculara gönderir.
 
Microsoft Defender Virüsten Koruma, tehdit koruması sağlamak için çeşitli yöntemler kullanır. Bu yöntemler bulut tabanlı koruma, gerçek zamanlı koruma ve ayrılmış koruma güncelleştirmelerini içerir.

- Bulut tabanlı koruma, yeni ve yeni tehditlerin neredeyse anında algılanması ve engellenmesine yardımcı olur.
- Her zaman açık tarama dosya ve işlem davranışı izleme ve diğer teknikleri ( *gerçek zamanlı koruma* olarak da bilinir) kullanır.
- Özel koruma güncelleştirmeleri makine öğrenmesi, insan ve otomatik büyük veri analizi ve ayrıntılı tehdit direnci araştırmalarını temel alır. 

Kötü amaçlı yazılım ve Microsoft Defender Virüsten Koruma hakkında daha fazla bilgi edinmek için aşağıdaki makalelere bakın: 

- [Kötü amaçlı yazılımları & diğer tehditleri anlama](/windows/security/threat-protection/intelligence/understanding-malware)
- [Microsoft kötü amaçlı yazılımları ve istenmeyebilecek uygulamaları nasıl tanımlar?](/windows/security/threat-protection/intelligence/criteria)
- [Windows 10'da yeni nesil koruma](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10)

## <a name="what-happens-when-a-non-microsoft-antivirus-solution-is-used"></a>Microsoft dışı bir virüsten koruma çözümü kullanıldığında ne olur? 

Microsoft Defender Virüsten Koruma, işletim sisteminin bir parçasıdır ve Windows 10 çalıştıran cihazlarda etkinleştirilir. Ancak, Microsoft dışı bir virüsten koruma çözümü kullanıyorsanız ve [Uç Nokta için Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) kullanmıyorsanız, Microsoft Defender Virüsten Koruma otomatik olarak devre dışı moduna geçer.  

Devre dışı modundayken, kullanıcılar ve müşteriler tehditleri tanımlamak için zamanlanmış veya isteğe bağlı taramalar için Microsoft Defender Virüsten Koruma'yı kullanmaya devam edebilir; ancak Microsoft Defender Virüsten Koruma artık şunları yapacaktır:

- varsayılan virüsten koruma uygulaması olarak kullanılır.
- dosyaları etkin bir şekilde tehditlere karşı tarayın.
- tehditleri düzeltme veya çözme.

Microsoft dışı virüsten koruma çözümünü kaldırırsanız Microsoft Defender Virüsten Koruma, Windows cihazlarınızı tehditlere karşı korumak için otomatik olarak etkin moda geçer.

> [!TIP]
> - Microsoft 365 kullanıyorsanız birincil virüsten koruma çözümünüz olarak Microsoft Defender Virüsten Koruma'yı kullanmayı göz önünde bulundurun. Tümleştirme daha iyi koruma sağlayabilir. [Bkz. Birlikte daha iyi: Microsoft Defender Virüsten Koruma ve Office 365](/windows/security/threat-protection/microsoft-defender-antivirus/office-365-microsoft-defender-antivirus).
> - Microsoft dışı bir virüsten koruma çözümü kullanıyor olsanız bile Microsoft Defender Virüsten Koruma'yı güncel tuttuğunuzdan emin olun.

## <a name="what-to-expect-when-threats-are-detected"></a>Tehditler algılandığında neler beklenir?

Microsoft Defender Virüsten Koruma tarafından tehditler algılandığında aşağıdaki işlemler gerçekleşir:

- Kullanıcılar [Windows'da bildirim](https://support.microsoft.com/windows/8942c744-6198-fe56-4639-34320cf9444e) alır. 
- Algılamalar **, Koruma geçmişi** sayfasındaki [Windows Güvenliği uygulamasında](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center) listelenir.  
- [Windows 10 cihazlarınızın güvenliğini sağladıysanız](../setup/secure-win-10-pcs.md) ve [bunları Intune'a kaydettiyseniz ve kuruluşunuzda](/mem/intune/enrollment/windows-enrollment-methods) kayıtlı 800 veya daha az cihaz varsa, **Tehditler ve virüsten koruma** sayfasındaki <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezinde</a> tehdit algılamaları ve içgörüleri görürsünüz. Bu bilgilere **Giriş** sayfasındaki **Microsoft Defender Virüsten Koruma** kartından (veya **HealthThreats** >  **& virüsten koruma'yı** seçerek gezinti bölmesinden erişebilirsiniz).

    Kuruluşunuzda Intune'a kayıtlı 800'den fazla cihaz varsa Tehditler ve virüsten koruma sayfası yerine [Microsoft Endpoint Manager'dan](/mem/endpoint-manager-overview) tehdit **algılamalarını ve içgörülerini** görüntülemeniz istenir.
 
    > [!NOTE]
    > **Microsoft Defender Virüsten Koruma** kartı ve **Tehditler ve virüsten koruma** sayfası aşamalı olarak dağıtılıyor, bu nedenle bunlara hemen erişiminiz olmayabilir.

Çoğu durumda kullanıcıların başka bir işlem gerçekleştirmesi gerekmez. Bir cihazda kötü amaçlı bir dosya veya program algılandığında, Microsoft Defender Virüsten Koruma bunu engeller ve çalışmasını engeller. Ayrıca, diğer cihazların ve kullanıcıların da korunması için virüsten koruma ve kötü amaçlı yazılımdan koruma altyapısına yeni algılanan tehditler eklenir.  

Kötü amaçlı bir dosyanın kaldırılmasını onaylama gibi bir kullanıcının gerçekleştirmesi gereken bir eylem varsa, bunu aldığı bildirimde görür. Microsoft Defender Virüsten Koruma'nın bir kullanıcı adına yaptığı eylemler veya kullanıcıların gerçekleştirmesi gerekebilecek eylemler hakkında daha fazla bilgi edinmek için bkz. [Koruma Geçmişi](https://support.microsoft.com/office/f1e5fd95-09b4-46d1-b8c7-1059a1e09708). BT uzmanı/yöneticisi olarak tehdit algılamalarını yönetmeyi öğrenmek için bkz. [Algılanan tehditleri gözden geçirme ve eylem gerçekleştirme](../../business-premium/m365bp-review-threats-take-action.md).

Farklı tehditler hakkında daha fazla bilgi edinmek için, aşağıdaki eylemleri gerçekleştirebileceğiniz <a href="https://www.microsoft.com/wdsi/threats" target="_blank">Microsoft Güvenlik Zekası Tehditleri sitesini</a> ziyaret edin: 

- En önemli tehditler hakkındaki güncel bilgileri görüntüleyin.
- Belirli bir bölge için en son tehditleri görüntüleyin.
- Belirli bir tehditle ilgili ayrıntılar için tehdit ansiklopedisi'ni arayın.

## <a name="related-content"></a>İlgili içerik

[Güvenli Windows cihazları](/misc/m365bp-secure-windows-devices) (makale)\
[Microsoft Defender Virüsten Koruma'yi](/windows/security/threat-protection/microsoft-defender-antivirus/evaluate-microsoft-defender-antivirus) değerlendirme (makale)\
[Gerçek zamanlı ve bulut tabanlı virüsten korumayı açma](/mem/intune/user-help/turn-on-defender-windows#turn-on-real-time-and-cloud-delivered-protection) (makale)\
[Windows Güvenliği uygulamasından Microsoft Defender Virüsten Koruma'yi açma ve kullanma](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-security-center-antivirus) (makale)\
[Grup İlkesi'ni kullanarak Microsoft Defender Virüsten Koruma'nın nasıl açılıyor](/mem/intune/user-help/turn-on-defender-windows#turn-on-windows-defender) (makale)\
[Virüsten koruma tanımlarınızı güncelleştirme](/mem/intune/user-help/turn-on-defender-windows#update-your-antivirus-definitions) (makale)\
[Kötü amaçlı yazılım ve kötü amaçlı olmayan yazılımları analiz için Microsoft'a gönderme](/microsoft-365/security/office-365-security/submitting-malware-and-non-malware-to-microsoft-for-analysis) (makale)