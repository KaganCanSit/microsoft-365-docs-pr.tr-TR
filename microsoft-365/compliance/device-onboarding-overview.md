---
title: Windows 10 veya Windows 11 cihazlarını Microsoft 365'e eklemeye genel bakış
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: Windows 10 ve Windows 11 cihazlarını Microsoft 365'e ekleme
ms.openlocfilehash: 630a159327dc5ce177caf819b21e77ec40929866
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635589"
---
# <a name="onboard-windows-10-and-windows-11-devices-into-microsoft-365-overview"></a>Windows 10 ve Windows 11 cihazlarının Microsoft 365'e katılımına genel bakış

**Şunlar için geçerlidir:**

- [Uç nokta veri kaybı önleme (DLP)](./endpoint-dlp-learn-about.md)
- [İçeriden risk yönetimi](insider-risk-management.md)

Uç nokta veri kaybı önleme (Uç nokta DLP) ve iç risk yönetimi, hizmetlere izleme verileri gönderebilmeleri için Windows 10 Windows ve Windows 11 cihazlarının hizmete eklenmesini gerektirir.
 
Uç nokta DLP, Windows 10 veya Windows 11 cihazları izlemenize ve hassas öğelerin ne zaman kullanıldığını ve paylaşılmasını algılamanıza olanak tanır. Bu, bunların düzgün kullanıldığından ve korunduğundan emin olmak ve onları tehlikeye atabilecek riskli davranışları önlemeye yardımcı olmak için ihtiyacınız olan görünürlüğü ve denetimi sağlar. Microsoft'un tüm DLP teklifleri hakkında daha fazla bilgi için bkz. [Veri kaybını önleme hakkında bilgi edinin](dlp-learn-about-dlp.md). Uç Nokta DLP hakkında daha fazla bilgi edinmek için bkz. [Uç nokta veri kaybını önleme hakkında bilgi edinin](endpoint-dlp-learn-about.md).

Insider risk yönetimi, riskli kullanıcı etkinliklerini hızla tanımlamanıza, önceliklendirmenize ve harekete geçirmenize yardımcı olmak için hizmetin ve üçüncü taraf göstergelerin tamamını kullanır. Insider risk yönetimi, Microsoft 365 ve Microsoft Graph günlüklerini kullanarak risk göstergelerini tanımlamak ve bu riskleri azaltmak için eyleme geçmek için belirli ilkeler tanımlamanızı sağlar. Daha fazla bilgi için bkz. [Insider risk yönetimi hakkında bilgi edinin](insider-risk-management.md).

Cihaz ekleme, Microsoft 365 ve Uç Nokta için Microsoft Defender (MDE) arasında paylaşılır. Cihazları zaten MDE'ye eklediyseniz, bunlar yönetilen cihazlar listesinde görünür ve bu belirli cihazları eklemek için başka adım gerekmez. Uyumluluk merkezi'ne cihaz ekleme, cihazları MDE'ye de ekler.

## <a name="before-you-begin"></a>Başlamadan önce

### <a name="skusubscriptions-licensing"></a>SKU/abonelik lisanslama

[Lisanslama gereksinimlerini buradan](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business) kontrol edin.

### <a name="permissions"></a>İzinler

Cihaz yönetimini etkinleştirmek için kullandığınız hesabın şu rollerden herhangi birinin üyesi olması gerekir:

- Genel yönetici
- Güvenlik yöneticisi
- Uyumluluk yöneticisi

Cihaz yönetimi ayarlarını görüntülemek için özel bir hesap kullanmak istiyorsanız, bu hesabın şu rollerden birinde olması gerekir:

- Genel yönetici
- Uyumluluk yöneticisi
- Uyumluluk verileri yöneticisi
- Genel gözetmen

Ekleme/çıkarma sayfasına erişmek için özel bir hesap kullanmak istiyorsanız, bu hesap şu rollerden birinde olmalıdır:

- Genel yönetici
- Uyumluluk yöneticisi

Cihaz izlemeyi açmak/kapatmak için özel bir hesap kullanmak istiyorsanız, bu hesabın şu rollerden birinde olması gerekir:

- Genel yönetici
- Uyumluluk yöneticisi

### <a name="prepare-your-windows-devices"></a>Windows cihazlarınızı hazırlama

Eklemeniz gereken Windows cihazlarının bu gereksinimleri karşıladığından emin olun.

1. Windows 10 x64 derleme 1809 veya üzeri ya da Windows 11 çalıştırıyor olmalıdır.

2. Kötü Amaçlı Yazılımdan Koruma İstemci sürümü 4.18.2110 veya daha yenidir. Windows Güvenliği uygulamasını açarak geçerli sürümünüzü denetleyin, Ayarlar simgesini ve ardından Hakkında'yı seçin. Sürüm numarası Kötü Amaçlı Yazılımdan Koruma İstemci Sürümü altında listelenir. Windows Update KB4052623 yükleyerek en son Kötü Amaçlı Yazılımdan Koruma İstemci sürümüne güncelleştirin.

   > [!NOTE]
   > Windows Güvenliği bileşenlerin hiçbirinin etkin olması gerekmez, ancak [Gerçek zamanlı koruma ve Davranış izleyicisi](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus)) etkinleştirilmelidir.

3. İzlenecek cihazlar için Windows 10 için aşağıdaki Windows Güncelleştirmeler yüklenir.

   > [!NOTE]
   > Bu güncelleştirmeler bir cihazı eklemek için bir önkoşul değildir, ancak önemli sorunlara yönelik düzeltmeler içerir, bu nedenle ürünü kullanmadan önce yüklenmesi gerekir.
   >
    > - Windows 10 1809 - KB4559003, KB4577069, KB4580390 için
    > - Windows 10 1903 veya 1909 için - KB4559004, KB4577062, KB4580386
    > - Windows 10 2004 - KB4568831, KB4577063 için

4. Tüm cihazlar şunlardan biri olmalıdır:

   - [Azure Active Directory (Azure AD) ile katılan](/azure/active-directory/devices/concept-azure-ad-join)
   - [Hibrit Azure AD ile katılan](/azure/active-directory/devices/concept-azure-ad-join-hybrid)
   - [AAD kayıtlı](/azure/active-directory/user-help/user-help-register-device-on-network)

5. Microsoft Office'in desteklenen bir sürümü yüklü ve güncel. En güçlü koruma ve kullanıcı deneyimi için Microsoft 365 Uygulamaları sürüm 16.0.14701.0 veya üzerinin yüklü olduğundan emin olun.
> [!NOTE]
   > - Office 365 çalıştırıyorsanız KB 4577063 gereklidir.
   > - Microsoft 365 Uygulamaları sürüm 2004-2008'in Aylık Kurumsal Kanalı'ndaysanız, 2009 veya sonraki bir sürüme güncelleştirmeniz gerekir. Geçerli [sürümler için Microsoft 365 Uygulamaları güncelleştirme geçmişi (tarihe göre listelenmiştir)](/officeupdates/update-history-microsoft365-apps-by-date) bölümüne bakın. Bilinen sorun hakkında daha fazla bilgi edinmek [için 2020'deki Geçerli Kanal sürümleri için sürüm notları'nın](/officeupdates/current-channel#version-2010-october-27) Office Paketi bölümüne bakın.

6. İnternet'e bağlanmak için cihaz ara sunucusu kullanan uç noktalarınız varsa, [Information Protection için cihaz ara sunucusu ve İnternet bağlantısı ayarlarını yapılandırma'daki](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection) yordamları izleyin.

## <a name="onboarding-windows-10-or-windows-11-devices"></a>Windows 10 veya Windows 11 cihazları ekleme

Cihazdaki hassas öğeleri izleyebilmeniz ve koruyabilmeniz için önce cihaz izlemeyi etkinleştirmeniz ve uç noktalarınızı eklemeniz gerekir. Bu eylemlerin ikisi de Microsoft Purview uyumluluk portalı yapılır.

Henüz eklenmemiş cihazları eklemek istediğinizde, uygun betiği indirir ve bu cihazlara dağıtırsınız. Aşağıdaki cihaz ekleme yordamlarını izleyin.

[Uç Nokta için Microsoft Defender'a](/windows/security/threat-protection/) eklenen cihazlarınız zaten yönetilen cihazlar listesinde görünür.

Bu dağıtım senaryosunda, henüz eklenmemiş Windows 10 veya Windows 11 cihazları eklersiniz.

1. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com) açın. **Ayarlar** > **Cihaz izlemeyi etkinleştir'i** seçin.

   > [!NOTE]
   > Cihaz eklemenin etkinleştirilmesi genellikle yaklaşık 60 saniye sürer ancak lütfen Microsoft desteğiyle etkileşime geçmeden önce 30 dakikaya kadar bekleyin.

2. Uyumluluk Merkezi ayarları sayfasını açın ve **Windows cihaz izlemeyi aç'ı** seçin.

3. **Cihazlar** listesini açmak için **Cihaz yönetimi'ni** seçin. 

> [!NOTE]
> Daha önce Uç Nokta için Microsoft Defender dağıttıysanız, bu işlem sırasında eklenen tüm cihazlar **Cihazlar** listesinde listelenir. Bunları yeniden eklemeye gerek yoktur.

4. **Ekleme** işlemini başlatmak için Ekleme'yi seçin.

5. **Dağıtım yöntemi** listesinden bu ek cihazlara dağıtmak istediğiniz yöntemi seçin ve ardından **paketi indirin**.

6. Aşağıdaki tablodan izleyebileceğiniz uygun yordamı seçin:

Konu | Açıklama
:---|:---
[grup ilkesi kullanarak Windows 10 veya 11 cihazı ekleme](device-onboarding-gp.md) | Yapılandırma paketini cihazlara dağıtmak için grup ilkesi kullanın.
[Microsoft Endpoint Configuration Manager kullanarak Windows 10 veya 11 cihazı ekleme](device-onboarding-sccm.md) | Yapılandırma paketini cihazlara dağıtmak için Microsoft Endpoint Configuration Manager (geçerli dal) sürüm 1606 veya Microsoft Endpoint Configuration Manager (geçerli dal) sürüm 1602 veya önceki bir sürümü kullanabilirsiniz.
[Mobil Cihaz Yönetimi araçlarını kullanarak Windows 10 veya 11 cihazı ekleme](device-onboarding-mdm.md) | Yapılandırma paketini cihaza dağıtmak için Mobil Cihaz Yönetimi araçlarını veya Microsoft Intune kullanın.
[Yerel betik kullanarak Windows 10 veya 11 cihaz ekleme](device-onboarding-script.md) | Yapılandırma paketini uç noktalara dağıtmak için yerel betiği kullanmayı öğrenin.
[Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarının katılımı](device-onboarding-vdi.md) | VDI cihazlarını yapılandırmak için yapılandırma paketini kullanmayı öğrenin.

## <a name="see-also"></a>Ayrıca bkz.

- [İçeriden risk yönetimi hakkında daha fazla bilgi edinme](insider-risk-management.md)
- [Uç nokta veri kaybı önleme hakkında daha fazla bilgi edinme](endpoint-dlp-learn-about.md)
- [Uç noktada veri kaybı önlemeyi kullanma](endpoint-dlp-using.md)
- [Veri kaybı önleme hakkında daha fazla bilgi edinme](dlp-learn-about-dlp.md)
- [Bir DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md)
- [Etkinlik gezginini kullanmaya başlama](data-classification-activity-explorer.md)
- [Uç Nokta için Microsoft Defender](/windows/security/threat-protection/)
- [Windows 10 makineleri için ekleme araçları ve yöntemleri](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)
- [Microsoft 365 aboneliği](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Birleştirilmiş cihazları Azure AD](/azure/active-directory/devices/concept-azure-ad-join)
- [Chromium tabanlı yeni Microsoft Edge'i indirin](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
