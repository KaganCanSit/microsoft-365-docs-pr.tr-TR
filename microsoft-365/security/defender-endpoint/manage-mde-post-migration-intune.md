---
title: Intune kullanarak Uç Nokta için Microsoft Defender'ı yönetme
description: Intune ile Uç Nokta için Microsoft Defender'ı yönetmeyi öğrenin
keywords: geçiş sonrası, yönetme, işlemler, bakım, kullanım, intune, Uç Nokta için Microsoft Defender, edr
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
ms.topic: article
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: 290d98f3f4136cfd07b5ea5abc21988ac8d9867a
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027490"
---
# <a name="manage-microsoft-defender-for-endpoint-with-intune"></a>Intune ile Uç Nokta için Microsoft Defender'ı yönetme

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Bazı cihazlarda [(uç Microsoft Endpoint Manager](/mem) olarak da adlandırılır) Microsoft Intune (Intune) içeren Microsoft Endpoint Manager'i kullanarak, bu özellikleri kullanmanızı öneririz. [Daha fazla bilgi Endpoint Manager](/mem/endpoint-manager-overview).

Bu makalede, Intune'da Uç nokta ayarları için Microsoft Defender'ı nasıl bulasınız ve gerçekleştirebilirsiniz çeşitli görevler liste almaktadır.

## <a name="find-your-microsoft-defender-for-endpoint-settings-in-intune"></a>Intune'da Uç Nokta ayarları için Microsoft Defender'nızı bulma

> [!IMPORTANT]
> Bu makalede açıklanan ayarları yapılandırmak için Intune'a atanmış genel yönetici veya hizmet yöneticisi rolünüz olması gerekir. Daha fazla bilgi edinmek için **[bkz. Yönetici türleri (Intune)](/mem/intune/fundamentals/users-add#types-of-administrators)**.

1. Azure portalına () gidin[https://portal.azure.com](https://portal.azure.com) ve oturum açın.

2. **Azure Hizmetleri'nin** altında **Intune'ı seçin**.

3. Sol gezinti bölmesinde Cihaz yapılandırması'ni **seçin ve sonra** Yönet'in altında **Profiller'i seçin**.

4. Mevcut bir profili seçin veya yeni bir profil oluşturun.

> [!TIP]
> Yardıma mı ihtiyacınız var? Bkz **[. Intune ile Uç Nokta için Microsoft Defender Kullanma](/mem/intune/protect/advanced-threat-protection#example-of-using-microsoft-defender-atp-with-intune)**.

## <a name="configure-microsoft-defender-for-endpoint-with-intune"></a>Intune ile Uç Nokta için Microsoft Defender'ı yapılandırma

Aşağıdaki tabloda, Intune ile Uç Nokta için Microsoft Defender'ı yapılandırmak üzere gerçekleştirebilirsiniz çeşitli görevler listeledir. Her şeyi bir kerede yapılandırmaya gerek yok; bir görev seçin, ilgili kaynakları okuyun ve sonra devam edin.

<br/><br/>

|Görev|Daha fazla bilgi edinmek için kaynaklar|
|---|---|
|**Intune kullanarak, bu cihazları ve bu** cihazlarda depolanan verileri korumak için, kuruluşun cihazlarını yönetme|[Cihazlara mobil cihaz Microsoft Intune](/mem/intune/protect/device-protect)|
|**Mobil Tehdit Savunma çözümü olarak Intune ile** Uç Nokta için Microsoft Defender'ı tümleştirin <br/>*(Windows 10 veya Windows 11 çalıştıran Android cihazlar için)*|[Intune'da Koşullu Erişim ile Uç Nokta için Microsoft Defender'da uyumluluğu zorunludur](/mem/intune/protect/advanced-threat-protection)|
|**E-postanıza** ve şirket kaynaklarınıza bağlanan cihazları ve uygulamaları kontrol etmek için Koşullu Erişim'i kullanma|[Uç Nokta için Microsoft Defender'da Koşullu Erişimi Yapılandırma](/microsoft-365/security/defender-endpoint/configure-conditional-access)|
|**İlke Microsoft Defender Virüsten Koruma hizmet sağlayıcısını** (İlke [CSP](/windows/client-management/mdm/policy-configuration-service-provider)) kullanarak güvenlik ayarlarını yapılandırma|[Cihaz kısıtlamaları: Microsoft Defender Virüsten Koruma](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus) <br/><br/> [İlke CSP - Uç Nokta için Microsoft Defender](/windows/client-management/mdm/policy-csp-defender)|
|**Gerekirse, dışlamaları özel Microsoft Defender Virüsten Koruma** <br/><br/> *Genel olarak, dışlamaları uygulama gerekmedilir. Microsoft Defender Virüsten Koruma, bilinen işletim sistemi davranışları ve kurumsal yönetim, veritabanı yönetimi ve diğer kurumsal senaryolarda kullanılanlar gibi tipik yönetim dosyalarına dayalı bir dizi otomatik dışlama içerir.*|[Şu anda desteklenen Enterprise bilgisayarlarla ilgili virüs tarama Windows](https://support.microsoft.com/help/822158/virus-scanning-recommendations-for-enterprise-computers) <br/><br/> [Cihaz kısıtlamaları: Microsoft Defender Virüsten Koruma 11 cihaz için Windows 10 Windows Özel Kullanımları](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus-exclusions) <br/><br/> [Windows Server 2016 2019 Microsoft Defender Virüsten Koruma 2022'de dışlamaları yapılandırma](/windows/security/threat-protection/microsoft-defender-antivirus/configure-server-exclusions-microsoft-defender-antivirus)|
|**Saldırı yüzeyini azaltma kurallarınızı, genellikle** saldırganlar tarafından kötüye ilen yazılım davranışlarına yönelik olarak yapılandırma <br/><br/> *Saldırı yüzeyini azaltma kurallarınızı ilk [başta denetim modunda](/microsoft-365/security/defender-endpoint/audit-windows-defender) yapılandırın (en az bir hafta ve en çok iki ay için). Hazırken E-posta Power BI [(şablonmizi](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Attack%20Surface%20Reduction%20rules) al) kullanarak durumu izleyebilir ve bu kuralları etkin moda ayarlayabilirsiniz.*|[Uç Nokta için Microsoft Defender'da Denetim modu](/microsoft-365/security/defender-endpoint/audit-windows-defender) <br/><br/> [Uç nokta koruması: Saldırı Yüzeyini Azaltma](/mem/intune/protect/endpoint-protection-windows-10?toc=/intune/configuration/toc.json&bc=/intune/configuration/breadcrumb/toc.json#attack-surface-reduction) <br/><br/> [Saldırı yüzeyini azaltma kuralları hakkında daha fazla bilgi](/microsoft-365/security/defender-endpoint/attack-surface-reduction) <br/><br/> [Teknik Community blog gönderisi: Saldırı yüzeyini azaltma kurallarının yeniden ortaya çıkarımı - Bölüm 1](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420)|
|**Ağ filtrelemenizi herhangi bir uygulamadan** IP adreslerine veya etki alanlarına düşük saygınlığı olan giden bağlantıları engellemek üzere yapılandırma  <br/><br/> *Ağ filtreleme, ağ koruması olarak [da adlandırılır](/microsoft-365/security/defender-endpoint/network-protection).* <br/><br/> *Yazılım ve Windows 10 11 Windows en son kötü amaçlı yazılımdan koruma platform güncelleştirmelerinin [yüklü olduğundan emin](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform) olun.*|[Uç nokta koruması: Ağ filtreleme](/mem/intune/protect/endpoint-protection-windows-10#network-filtering) <br/><br/> [Olay Görüntüleyicisi'nde ağ Windows olaylarını gözden geçirme](/microsoft-365/security/defender-endpoint/evaluate-network-protection#review-network-protection-events-in-windows-event-viewer)|
|**Fidye yazılımlarına karşı korunmak için** denetimli klasör erişimini yapılandırma <br/><br/> *[Denetimli klasör](/microsoft-365/security/defender-endpoint/controlled-folders) erişimi, yazılım önleme yazılımı koruması olarak da adlandırılır.*|[Uç nokta koruması: Denetimli klasör erişimi](/mem/intune/protect/endpoint-protection-windows-10#controlled-folder-access) <br/><br/> [Intune'da denetimli klasör erişimini etkinleştirme](/microsoft-365/security/defender-endpoint/enable-controlled-folders#intune)|
|**Diğer cihazları yaymak** ve bulaştırmak için açıklardan yararlanan kötü amaçlı yazılımdan korumak için exploit protection'i yapılandırma <br/><br/> *[Exploit Protection](/microsoft-365/security/defender-endpoint/exploit-protection) , Exploit Guard olarak da adlandırılır.*|[Uç nokta koruması: Microsoft Defender Exploit Guard](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-exploit-guard) <br/><br/> [Intune'da açıkları korumayı etkinleştirme](/microsoft-365/security/defender-endpoint/enable-exploit-protection#intune)|
|**Web Microsoft Defender SmartScreen** ve internet'e yönelik kötü amaçlı sitelere ve dosyalara karşı korumak üzere yapılandırma. <br/><br/> *Microsoft Edge cihazlarında yüklü olması gerekir. Google Chrome ve FireFox tarayıcılarını koruma için, exploit protection'ı yapılandırabilirsiniz.*|[Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) <br/><br/> [Cihaz kısıtlamaları: Microsoft Defender SmartScreen](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-smartscreen) <br/><br/> [Intune'da SmartScreen'i yönetmek için ilke ayarları](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings#mdm-settings)|
|**Microsoft Defender Güvenlik Duvarı'nı** , kuruluş cihazlarına yetkisiz ağ trafiğinin akışını engellemek üzere yapılandırma|[Uç nokta koruması: Microsoft Defender Güvenlik Duvarı](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-firewall) <br/><br/> [Gelişmiş Güvenlik Duvarı ile Microsoft Defender Güvenlik Duvarı](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)|
|**Şifrelemeyi ve BitLocker'ı** yapılandırarak kuruluş kuruluşlarının çalışan cihazlarında yer alan bilgileri Windows|[Uç nokta koruması: Windows Şifreleme](/mem/intune/protect/endpoint-protection-windows-10#windows-encryption) <br/><br/> [Windows 10 11 cihaz için BitLocker Windows Locker](/windows/security/information-protection/bitlocker/bitlocker-overview)|
|**Kimlik bilgileri hırsızlığı saldırılarına karşı korumak için Microsoft Defender Credential Guard'ı** yapılandırma|Windows 10, Windows 11, Windows Server 2016, Windows Server 2019 ve Windows Server 2022 için bkz. Uç nokta koruması[: Microsoft Defender Credential Guard](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-credential-guard) <br/><br/> Windows 7 SP1, Windows Server 2008 R2 SP1, Windows 8.1 ve Windows Server 2012 R2 için bkz. Karma Geçiş (PtH) Saldırılarını Azaltma ve Diğer Kimlik Bilgileri Hırsızlığı[, Sürüm 1 ve 2](https://www.microsoft.com/download/details.aspx?id=36036)|
|**Microsoft Defender Uygulama Denetimi'yi** yapılandırarak, kuruluş cihazlarında uygulamaları denetlemeyi veya uygulamaları güvenmeyi seçme <br/><br/> *Microsoft Defender Uygulama Denetimi [uygulamasına AppLocker da adlandırılır](/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview).*|[Microsoft Intune kullanarak Microsoft Defender Uygulama Denetimi ilkelerini Microsoft Intune](/windows/security/threat-protection/windows-defender-application-control/deploy-windows-defender-application-control-policies-using-intune) <br/><br/> [Uç nokta koruması: Microsoft Defender Uygulama Denetimi](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-application-control) <br/><br/> [AppLocker CSP](/windows/client-management/mdm/applocker-csp)|
|**Yetkisiz çevre birimlerinin cihazlarınıza** ödün vermesini önlemeye yardımcı olmak için cihaz denetimi ve USB çevre birimleri erişimini yapılandırma|[Uç Nokta ve Intune için Microsoft Defender'ı kullanarak USB cihazlarını ve diğer çıkarılabilir medyayı denetleme](/windows/security/threat-protection/device-control/control-usb-devices-using-intune)|

## <a name="configure-your-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalınızı yapılandırma

Daha önce bunu yapmadısanız, Microsoft 365 Defender portalınızı uyarıları görüntülemek, tehdit koruması özelliklerini yapılandırmak ve genel güvenlik sonrası hakkında ayrıntılı bilgileri görüntülemek üzere yapılandırabilirsiniz. Bkz[. Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). Ayrıca, son kullanıcıların portalda hangi özellikleri göreceğini Microsoft 365 Defender.

- [Genel bakış Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/use)
- [Uç nokta koruması: Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Sonraki adımlar

- [Nasıl olduğunu genel Tehdit ve Güvenlik Açığı Yönetimi](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Microsoft 365 Defender portal güvenlik işlemleri panosuna ziyaret edin](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
