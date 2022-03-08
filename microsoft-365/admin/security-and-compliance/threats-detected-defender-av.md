---
title: Güvenlik tarafından algılanan Microsoft Defender Virüsten Koruma
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
description: Virüslerin Microsoft Defender Virüsten Koruma, kötü amaçlı yazılımlar Windows yazılımlara ve casus yazılımlar gibi yazılım tehditlerine karşı nasıl korumaları olduğunu öğrenin.
ms.openlocfilehash: c11ce9a2f38f1ecb7f47cd5b74e710d92c8ffbe0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63325663"
---
# <a name="threats-detected-by-microsoft-defender-antivirus"></a>Güvenlik tarafından algılanan Microsoft Defender Virüsten Koruma

Microsoft Defender Virüsten Koruma, cihazlarınızı Windows, kötü amaçlı yazılım ve casus yazılımlar gibi yazılım tehditlerine karşı korur.

- Virüsler normalde kendi kodlarını cihaz veya ağ bilgisayarınızdan diğer dosyalara iliştirerek yayılır ve virüs bulan programların yanlış çalışmasına neden olabilir.
- Kötü amaçlı yazılım, cihazlara zarar verebilecek ve normal kullanımı kesintiye neden olan kötü amaçlı dosyalar, uygulamalar ve kod içerir. Ayrıca, kötü amaçlı yazılımlar yetkisiz erişime izin verir, sistem kaynaklarını kullanabilir, parolaları ve hesap bilgilerini çaldırarak sizi bilgisayarınızdan dışarı kilitleyip güvenliklerini talep ve daha fazlasını sorabilir.
- Casus yazılım, web'e gözatma etkinliği gibi verileri toplar ve uzak sunuculara gönderir.
 
Tehdit koruması sağlamak için Microsoft Defender Virüsten Koruma yöntemleri kullanır. Bu yöntemler buluta teslim edilen koruma, gerçek zamanlı koruma ve özel koruma güncelleştirmelerini içerir.

- Bulut teslimi koruması, yeni ve ortaya çıkan tehditlerin neredeyse anında algılanmasına ve engellenmesine yardımcı olur.
- Her zaman açık taramada dosya ve işlem davranışı izleme ve diğer teknikler (gerçek zamanlı koruma *olarak da bilinir) kullanır*.
- Özel koruma güncelleştirmeleri makine öğrenimi, insan ve otomatik büyük veri çözümlemelerine ve derinlemesine tehdit direnci araştırmalarına dayalıdır. 

Kötü amaçlı yazılım ve kötü amaçlı yazılım Microsoft Defender Virüsten Koruma için aşağıdaki makalelere bakın: 

- [Kötü amaçlı yazılımları & tehditlere karşı anlama](/windows/security/threat-protection/intelligence/understanding-malware)
- [Microsoft kötü amaçlı yazılımları ve istenmeyen olabilecek uygulamaları nasıl tanımlar?](/windows/security/threat-protection/intelligence/criteria)
- [Yeni nesil koruma altında Windows 10](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-in-windows-10)

## <a name="what-happens-when-a-non-microsoft-antivirus-solution-is-used"></a>Microsoft dışı bir virüsten koruma çözümü kullanılırsa ne olur? 

Microsoft Defender Virüsten Koruma, işletim sisteminin bir parçasıdır ve işletim sisteminin bir parçası olan cihazlarda Windows 10. Bununla birlikte, Microsoft dışı bir virüsten koruma çözümü kullanıyorsanız ve Uç Nokta için [Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) kullansanız bile, otomatik olarak Microsoft Defender Virüsten Koruma devre dışı moduna girer.  

Kullanıcılar ve müşteriler devre dışı modundayken, zamanlanmış veya isteğe bağlı taramalarda Microsoft Defender Virüsten Koruma'ı kullanarak tehditleri belirlemeye devam edebilir; Microsoft Defender Virüsten Koruma artık kullanmayacak:

- varsayılan virüsten koruma uygulaması olarak kullanılabilir.
- tehditlere karşı etkin bir şekilde dosya tarayın.
- tehditleri düzeltmek veya çözmek.

Microsoft olmayan bir virüsten koruma çözümünü kaldırırsanız, Microsoft Defender Virüsten Koruma cihazlarınızı tehditlerden korumak için otomatik olarak Windows moduna geçer.

> [!TIP]
> - Microsoft 365 kullanıyorsanız, birincil virüsten koruma Microsoft Defender Virüsten Koruma olarak Microsoft Defender Virüsten Koruma'i kullanmayı deneyin. Tümleştirme daha iyi koruma sağlar. Birlikte [daha iyi: Microsoft Defender Virüsten Koruma ve Office 365](/windows/security/threat-protection/microsoft-defender-antivirus/office-365-microsoft-defender-antivirus).
> - Microsoft dışı bir Microsoft Defender Virüsten Koruma virüsten koruma çözümü kullanıyor bile olun, bu güncelleştirmeleri güncel tutmanızı sağlar.

## <a name="what-to-expect-when-threats-are-detected"></a>Tehdit algılandığında neler olabilir?

Güvenlik tarafından tehdit Microsoft Defender Virüsten Koruma, aşağıdakiler olur:

- Kullanıcılar diğer [kullanıcılar tarafından Windows](https://support.microsoft.com/windows/8942c744-6198-fe56-4639-34320cf9444e). 
- Algılamalar, Koruma [Windows Güvenliği sayfasındaki](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center) **Algılamalar listesinde** listelenir.  
- [Windows 10](../setup/secure-win-10-pcs.md) cihazlarınızı güvenlik altına aldıysanız ve [bunları Intune'a](/mem/intune/enrollment/windows-enrollment-methods) kaydettiyebilirsiniz ve kuruluşta 800 veya daha az cihaz kayıtlı ise Tehditler ve virüsten koruma sayfasındaki <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi'de</a>  **tehdit algılamalarını ve öngörüleri görebilirsiniz. Bu sayfaya Microsoft Defender Virüsten Koruma** sayfasında (**veya gezinti bölmesinde** **HealthThreats** veya **antivirus** >  öğesini seçerek) & seçin.

    Kuruluşta Intune'a kayıtlı 800'den fazla cihaz varsa, Tehditler ve virüsten koruma sayfasından değil de, Microsoft Endpoint Manager'den tehdit [](/mem/endpoint-manager-overview) algılamalarını ve öngörüleri **görüntülemeniz** istenir.
 
    > [!NOTE]
    > Yeni **Microsoft Defender Virüsten Koruma** ve **Tehditlerle** virüsten koruma sayfası aşamalar olarak yuvarlanıyor, dolayısıyla bu karta hemen erişiminiz yok olabilir.

Çoğu durumda, kullanıcıların başka bir işlemde yer almaları gerekmektedir. Cihazda kötü amaçlı bir dosya veya program algılandığında, Microsoft Defender Virüsten Koruma bunu engeller ve çalıştırmasını engeller. Ayrıca, virüsten koruma ve kötü amaçlı yazılımdan koruma altyapısına yeni algılanan tehditlerin yanı sıra, diğer cihaz ve kullanıcıların da korunmasını sağlar.  

Kötü amaçlı bir dosyanın kaldırılmasını onaylama gibi bir kullanıcının bir işlemde çalışması gerekirse, bu eylemi alacak olan bildirimde bunu görebilirler. Bir kullanıcının adına gerçekleştirilen Microsoft Defender Virüsten Koruma veya kullanıcıların eylemleri hakkında daha fazla bilgi edinmek için Koruma [Geçmişi'ne bakın](https://support.microsoft.com/office/f1e5fd95-09b4-46d1-b8c7-1059a1e09708). Bir IT uzmanı/yöneticisi olarak tehdit algılamalarını yönetmeyi öğrenmek için bkz. Algılanan [tehditleri gözden geçirme ve önlem alma](review-threats-take-action.md).

Farklı tehditlerle ilgili daha fazla bilgi edinmek Microsoft Güvenlik Zekası <a href="https://www.microsoft.com/wdsi/threats" target="_blank">tehditlere</a> karşı aşağıdaki eylemleri gerçekleştirebilirsiniz: 

- En önemli tehditlerle ilgili güncel bilgileri görüntüleme.
- Belirli bir bölge için en son tehditleri görüntüleme.
- Belirli bir tehditle ilgili ayrıntılar için tehdit anlarını arama.

## <a name="related-content"></a>İlgili içerik

[Mobil cihazların Windows güvenlidir](/misc/m365bp-secure-windows-devices) (makale)\
[Microsoft Defender Virüsten Koruma](/windows/security/threat-protection/microsoft-defender-antivirus/evaluate-microsoft-defender-antivirus) (makale)\
[Gerçek zamanlı ve buluta teslim edilen virüsten korumayı](/mem/intune/user-help/turn-on-defender-windows#turn-on-real-time-and-cloud-delivered-protection) açma (makale)\
[Microsoft Defender Virüsten Koruma uygulamasından Windows Güvenliği ve kullanma](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-security-center-antivirus) (makale)\
[Grup İlkesi (Microsoft Defender Virüsten Koruma) kullanarak e-postayı](/mem/intune/user-help/turn-on-defender-windows#turn-on-windows-defender) açma
[Virüsten koruma tanımlarınızı güncelleştirme](/mem/intune/user-help/turn-on-defender-windows#update-your-antivirus-definitions) (makale)\
[Çözümleme için Microsoft'a kötü amaçlı yazılım ve kötü amaçlı yazılım olmayan yazılımlar gönderme](/microsoft-365/security/office-365-security/submitting-malware-and-non-malware-to-microsoft-for-analysis) (makale)