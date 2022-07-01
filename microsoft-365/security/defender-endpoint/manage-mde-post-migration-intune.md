---
title: Intune kullanarak Uç Nokta için Microsoft Defender yönetme
description: Intune ile Uç Nokta için Microsoft Defender yönetmeyi öğrenin
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
ms.topic: article
ms.date: 11/29/2021
ms.reviewer: chventou
ms.openlocfilehash: 05fb01b411b1b32eeac763f3c364b29e29f5d8f5
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603714"
---
# <a name="manage-microsoft-defender-for-endpoint-with-intune"></a>Intune ile Uç Nokta için Microsoft Defender yönetme

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Kuruluşunuzun cihazlar için tehdit koruması özelliklerini (uç noktalar olarak da adlandırılır) yönetmek için Microsoft Intune (Intune) içeren [Microsoft](/mem) Endpoint Manager kullanmanızı öneririz. [Endpoint Manager hakkında daha fazla bilgi edinin](/mem/endpoint-manager-overview).

Bu makalede, Intune'da Uç Nokta için Microsoft Defender ayarlarınızın nasıl bulunabileceği açıklanır ve gerçekleştirebileceğiniz çeşitli görevler listelenir.

## <a name="find-your-microsoft-defender-for-endpoint-settings-in-intune"></a>Intune'da Uç Nokta için Microsoft Defender ayarlarınızı bulma

> [!IMPORTANT]
> Bu makalede açıklanan ayarları yapılandırmak için Intune'de genel yönetici veya hizmet yöneticisi rolü atanmış olmalıdır. Daha fazla bilgi için bkz. **[Yönetici türleri (Intune)](/mem/intune/fundamentals/users-add#types-of-administrators)**.

1. Azure portal ([https://portal.azure.com](https://portal.azure.com)) gidin ve oturum açın.

2. **Azure Hizmetleri'nin** altında **Intune'ı** seçin.

3. Sol taraftaki gezinti bölmesinde **Cihaz yapılandırması'nı** ve ardından **Yönet'in** altında **Profiller'i** seçin.

4. Mevcut bir profili seçin veya yeni bir profil oluşturun.

> [!TIP]
> Yardıma mı ihtiyacınız var? Bkz **[. Intune ile Uç Nokta için Microsoft Defender kullanma](/mem/intune/protect/advanced-threat-protection#example-of-using-microsoft-defender-atp-with-intune)**.

## <a name="configure-microsoft-defender-for-endpoint-with-intune"></a>Intune ile Uç Nokta için Microsoft Defender yapılandırma

Aşağıdaki tabloda, Intune ile Uç Nokta için Microsoft Defender yapılandırmak için gerçekleştirebileceğiniz çeşitli görevler listelenir. Her şeyi aynı anda yapılandırmanız gerekmez; bir görev seçin, ilgili kaynakları okuyun ve devam edin.

<br/><br/>

|Görev|Daha fazla bilgi edinmek için kaynaklar|
|---|---|
|Kuruluşunuzda depolanan cihazları ve verileri korumak için **Intune kullanarak kuruluşunuzun cihazlarını yönetme**|[Cihazları Microsoft Intune ile koruma](/mem/intune/protect/device-protect)|
|mobil tehdit savunması çözümü olarak **Intune ile Uç Nokta için Microsoft Defender tümleştirme** <br/>*(Windows 10 veya Windows 11 çalıştıran Android cihazlar ve cihazlar için)*|[Intune'da Koşullu Erişim ile Uç Nokta için Microsoft Defender uyumluluğu zorunlu kılma](/mem/intune/protect/advanced-threat-protection)|
|E-postanıza ve şirket kaynaklarınıza bağlanabilen cihazları ve uygulamaları denetlemek için **Koşullu Erişim'i kullanma**|[Uç Nokta için Microsoft Defender'de Koşullu Erişimi Yapılandırma](/microsoft-365/security/defender-endpoint/configure-conditional-access)|
|İlke yapılandırma hizmet sağlayıcısını ([İlke CSP](/windows/client-management/mdm/policy-configuration-service-provider)) kullanarak **Microsoft Defender Virüsten Koruma ayarlarını yapılandırma**|[Cihaz kısıtlamaları: Microsoft Defender Virüsten Koruma](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus) <br/><br/> [İlke CSP - Uç Nokta için Microsoft Defender](/windows/client-management/mdm/policy-csp-defender)|
|**Gerekirse Microsoft Defender Virüsten Koruma için dışlamalar belirtin** <br/><br/> *Genel olarak, dışlamaları uygulamanız gerekmez. Microsoft Defender Virüsten Koruma, bilinen işletim sistemi davranışlarına ve kurumsal yönetim, veritabanı yönetimi ve diğer kurumsal senaryolarda kullanılanlar gibi tipik yönetim dosyalarına dayalı bir dizi otomatik dışlama içerir.*|[Şu anda desteklenen Windows sürümlerini çalıştıran Kurumsal bilgisayarlar için virüs tarama önerileri](https://support.microsoft.com/help/822158/virus-scanning-recommendations-for-enterprise-computers) <br/><br/> [Cihaz kısıtlamaları: Windows 10 ve Windows 11 cihazlar için Microsoft Defender Virüsten Koruma Dışlamaları](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-antivirus-exclusions) <br/><br/> [Windows Server 2016, 2019 veya 2022'de Microsoft Defender Virüsten Koruma dışlamalarını yapılandırma](/windows/security/threat-protection/microsoft-defender-antivirus/configure-server-exclusions-microsoft-defender-antivirus)|
|**Saldırı yüzeyi azaltma kurallarınızı** , saldırganlar tarafından sıklıkla kötüye kullanılabilecek yazılım davranışlarını hedeflemek için yapılandırma <br/><br/> *Saldırı yüzeyi azaltma kurallarınızı önce [denetim modunda](/microsoft-365/security/defender-endpoint/audit-windows-defender) yapılandırın (en az bir hafta ve iki aya kadar). Power BI kullanarak durumu izleyebilir ([şablonumuzu alın](https://github.com/microsoft/MDATP-PowerBI-Templates/tree/master/Attack%20Surface%20Reduction%20rules)) ve hazır olduğunuzda bu kuralları etkin moda ayarlayabilirsiniz.*|[Uç Nokta için Microsoft Defender'de denetim modu](/microsoft-365/security/defender-endpoint/audit-windows-defender) <br/><br/> [Uç nokta koruması: Saldırı Yüzeyi Azaltma](/mem/intune/protect/endpoint-protection-windows-10?toc=/intune/configuration/toc.json&bc=/intune/configuration/breadcrumb/toc.json#attack-surface-reduction) <br/><br/> [Saldırı yüzeyi azaltma kuralları hakkında daha fazla bilgi edinin](/microsoft-365/security/defender-endpoint/attack-surface-reduction) <br/><br/> [Teknoloji Topluluğu blog gönderisi: Saldırı yüzeyi azaltma kurallarının demystifying - Bölüm 1](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420)|
|**Ağ filtrelemenizi** , herhangi bir uygulamadan IP adreslerine veya düşük saygınlığı olan etki alanlarına giden bağlantıları engelleyecek şekilde yapılandırın  <br/><br/> *Ağ filtreleme ağ [koruması](/microsoft-365/security/defender-endpoint/network-protection) olarak da adlandırılır.* <br/><br/> *Windows 10 ve Windows 11 cihazlarda en son [kötü amaçlı yazılımdan koruma platformu güncelleştirmelerinin](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform) yüklü olduğundan emin olun.*|[Uç nokta koruması: Ağ filtreleme](/mem/intune/protect/endpoint-protection-windows-10#network-filtering) <br/><br/> [Windows Olay Görüntüleyicisi'de ağ koruma olaylarını gözden geçirme](/microsoft-365/security/defender-endpoint/evaluate-network-protection#review-network-protection-events-in-windows-event-viewer)|
|Fidye yazılımlarına karşı korunmak için **denetimli klasör erişimini yapılandırma** <br/><br/> *[Denetimli klasör erişimi](/microsoft-365/security/defender-endpoint/controlled-folders) , antiransomware koruması olarak da adlandırılır.*|[Uç nokta koruması: Denetimli klasör erişimi](/mem/intune/protect/endpoint-protection-windows-10#controlled-folder-access) <br/><br/> [Intune'de denetimli klasör erişimini etkinleştirme](/microsoft-365/security/defender-endpoint/enable-controlled-folders#intune)|
|Kuruluşunuzun cihazlarını diğer cihazlara yaymak ve bulaştırmak için kötüye kullanım kullanan kötü amaçlı yazılımlardan korumak için yararlanma **korumasını yapılandırma** <br/><br/> *[Exploit Protection, Exploit](/microsoft-365/security/defender-endpoint/exploit-protection) Guard olarak da adlandırılır.*|[Uç nokta koruması: Microsoft Defender Exploit Guard](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-exploit-guard) <br/><br/> [Intune'de açıklara karşı korumayı etkinleştirme](/microsoft-365/security/defender-endpoint/enable-exploit-protection#intune)|
|**Microsoft Defender SmartScreen'i** , internet üzerindeki kötü amaçlı sitelere ve dosyalara karşı korumak için yapılandırın. <br/><br/> *Microsoft Edge, kuruluşunuzun cihazlarına yüklenmelidir. Google Chrome ve FireFox tarayıcılarında koruma için açıklardan yararlanma korumasını yapılandırın.*|[Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) <br/><br/> [Cihaz kısıtlamaları: Microsoft Defender SmartScreen](/mem/intune/configuration/device-restrictions-windows-10#microsoft-defender-smartscreen) <br/><br/> [Intune'de SmartScreen'i yönetmek için ilke ayarları](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-available-settings#mdm-settings)|
|Kuruluşunuzun cihazlarına veya cihazlarına gelen veya giden yetkisiz ağ trafiğini engellemek için **Microsoft Defender Güvenlik Duvarı yapılandırma**|[Uç nokta koruması: Microsoft Defender Güvenlik Duvarı](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-firewall) <br/><br/> [Gelişmiş Güvenlik ile Microsoft Defender Güvenlik Duvarı](/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security)|
|Kuruluşunuzun Windows çalıştıran cihazlarındaki bilgileri korumak için **şifrelemeyi ve BitLocker'ı yapılandırma**|[Uç nokta koruması: Windows Şifrelemesi](/mem/intune/protect/endpoint-protection-windows-10#windows-encryption) <br/><br/> [Windows 10 ve Windows 11 cihazlar için BitLocker](/windows/security/information-protection/bitlocker/bitlocker-overview)|
|Kimlik bilgisi hırsızlığı saldırılarına karşı korunmak için **Microsoft Defender Credential Guard'ı yapılandırma**|Windows 10, Windows 11, Windows Server 2016, Windows Server 2019 ve Windows Server 2022 için bkz[. Endpoint protection: Microsoft Defender Credential Guard](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-credential-guard) <br/><br/> Windows 7 SP1, Windows Server 2008 R2 SP1, Windows 8.1 ve Windows Server 2012 R2 için bkz. [Karma Geçiş (PtH) Saldırılarını ve Diğer Kimlik Bilgileri Hırsızlığını Azaltma, Sürüm 1 ve 2](https://www.microsoft.com/download/details.aspx?id=36036)|
|**Microsoft Defender Uygulama Denetimi'ni** kuruluşunuzun cihazlarında uygulamaların denetlenip denetlenmeyeceğini veya güvenileceğini seçecek şekilde yapılandırın <br/><br/> *Microsoft Defender Uygulama Denetimi, [AppLocker](/windows/security/threat-protection/windows-defender-application-control/applocker/applocker-overview) olarak da adlandırılır.*|[Microsoft Intune kullanarak Microsoft Defender Uygulama Denetimi ilkelerini dağıtma](/windows/security/threat-protection/windows-defender-application-control/deploy-windows-defender-application-control-policies-using-intune) <br/><br/> [Uç nokta koruması: Microsoft Defender Uygulama Denetimi](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-application-control) <br/><br/> [AppLocker CSP](/windows/client-management/mdm/applocker-csp)|
|Yetkisiz **çevre birimlerindeki tehditlerin** cihazlarınızı tehlikeye atmasını önlemeye yardımcı olmak için cihaz denetimi ve USB çevre birimleri erişimini yapılandırma|[Uç Nokta için Microsoft Defender ve Intune kullanarak USB cihazlarını ve diğer çıkarılabilir medyayı denetleme](/windows/security/threat-protection/device-control/control-usb-devices-using-intune)|

## <a name="configure-your-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalınızı yapılandırma

Henüz yapmadıysanız, Microsoft 365 Defender portalınızı uyarıları görüntülemek, tehdit koruması özelliklerini yapılandırmak ve kuruluşunuzun genel güvenlik duruşu hakkında ayrıntılı bilgileri görüntülemek için yapılandırın. [bkz. Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender). Ayrıca son kullanıcıların Microsoft 365 Defender portalında görüp göremeyeceğini ve hangi özellikleri görebileceğini de yapılandırabilirsiniz.

- [Microsoft 365 Defender genel bakış](/microsoft-365/security/defender-endpoint/use)
- [Uç nokta koruması: Microsoft 365 Defender](/mem/intune/protect/endpoint-protection-windows-10#microsoft-defender-security-center)

## <a name="next-steps"></a>Sonraki adımlar

- [Tehdit ve Güvenlik Açığı Yönetimi genel bakışını edinin](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)
- [Microsoft 365 Defender portalı güvenlik işlemleri panosunu ziyaret edin](/microsoft-365/security/defender-endpoint/security-operations-dashboard)
