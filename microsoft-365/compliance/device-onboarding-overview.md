---
title: 11 Windows 10 cihaz Windows cihaz ekleme ve cihaz ekleme Microsoft 365 genel bakış
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
description: 11 Windows 10 cihaz Windows cihaz ekleme ve Microsoft 365
ms.openlocfilehash: dc2324f9ab8105d51730071f84397c8648c9a9de
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63525065"
---
# <a name="onboard-windows-10-and-windows-11-devices-into-microsoft-365-overview"></a>11 Windows 10 cihaz Windows cihaz ekleme ve cihaz ekleme Microsoft 365 genel bakış

**Aşağıdakiler için geçerlidir:**

- [Microsoft 365 Uç nokta veri kaybı önleme (DLP)](./endpoint-dlp-learn-about.md)
- [Insider risk yönetimi](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

Microsoft 365 Uç nokta veri kaybı önleme (Uç nokta DLP) ve insider risk yönetimi için Windows 10 Windows ve Windows 11 cihazlarının hizmetlere izleme verileri gönder göndersin diye hizmete ekli olması gerekir.
 
Microsoft 365 Uç Noktası DLP, hassas öğelerin Windows 10 veya Windows 11 cihazı izlemenizi ve hassas öğelerin ne zaman kullanıl olduğunu ve paylaşılıyor olduğunu saptamanizi sağlar. Bu size, bunların düzgün kullanıldıklarını ve korunacaklarını garanti etmek ve onları tehlikeye atacak riskli davranışı önlemeye yardımcı olmak için gereken görünürlük ve denetimi sağlar. Microsoft'un tüm DLP teklifleri hakkında daha fazla bilgi için bkz. [Veri kaybını önleme hakkında bilgi.](dlp-learn-about-dlp.md) Uç nokta DLP hakkında daha fazla bilgi edinmek için bkz[. Uç nokta veri kaybını önleme hakkında bilgi.](endpoint-dlp-learn-about.md)

Insider risk yönetimi, riskli kullanıcı etkinliğini hızla tanımlamanıza, önceliği belirlemeye ve bu etkinlik üzerinde eyleme son olarak yardımcı olmak için hizmetin ve 3. taraf göstergelerinin eksiksiz bir deneyiminden yararlanır. Insider risk yönetimi Microsoft 365 Microsoft Graph'den gelen günlükleri kullanarak, risk göstergelerini tanımlamak ve bu riskleri azaltmak için önlem almak üzere belirli ilkeler tanımlamanıza olanak sağlar. Daha fazla bilgi için bkz[. Microsoft iş yerizsinde insider risk yönetimi Microsoft 365](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365).

Cihaz ekleme, mobil cihaz genelinde Microsoft 365 Uç Nokta (MDE) için Microsoft Defender ile paylaşılır. Cihazları MDE'ye zaten eklediysiniz, bu cihazlar yönetilen cihazlar listesinde görünür ve bu belirli cihazları eklemeye yönelik başka adım gerekmez. Uyumluluk merkezi'nde cihaz ekleme cihazları da MDE'ye onboarding olarak verir.

## <a name="before-you-begin"></a>Başlamadan önce

### <a name="skusubscriptions-licensing"></a>SKU/abonelik lisansı

Lisans gereksinimlerini buradan [kontrol edin](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

### <a name="permissions"></a>İzinler

Cihaz yönetimini etkinleştirmek için, kullanmakta olunan hesap şu rollerden herhangi birinin üyesi olması gerekir:

- Genel yönetici
- Güvenlik yöneticisi
- Uyumluluk yöneticisi

Cihaz yönetimi ayarlarını görüntülemek için özel bir hesap kullanmak istediğiniz şu rollerden biri olabilir:

- Genel yönetici
- Uyumluluk yöneticisi
- Uyumluluk verileri yöneticisi
- Genel okuyucu

Ekleme/çıkarma sayfasına erişmek için özel bir hesap kullanmak için bu hesabın şu rollerden birisinde olması gerekir:

- Genel yönetici
- Uyumluluk yöneticisi

Cihaz izlemenin aç/kapat için özel bir hesap kullanmak istemeniz, şu rollerden birisinde yer alalır:

- Genel yönetici
- Uyumluluk yöneticisi

### <a name="prepare-your-windows-devices"></a>Cihazlarınızı Windows hazırlama

Ekleme için gereken Windows ilgili cihazların bu gereksinimleri karşılaya olduğundan emin olun.

1. x64 derleme Windows 10 1809 veya sonraki bir derlemeyi veya 11 Windows çalışıyor olması gerekir.

2. Kötü amaçlı yazılımdan koruma İstemci Sürümü 4.18.2110 veya daha yenidir. Windows Güvenliği uygulamasını açarak Ayarlar sürümünizi kontrol edin, Ayarlar Hakkında'ya tıklayın. Sürüm numarası Kötü Amaçlı Yazılımdan Koruma İstemci Sürümü altında listelenir. Kb4052623 Güncelleştirmesini yükleyerek kötü amaçlı yazılımlardan koruma Windows sürümüne güncelleştirin.

   > [!NOTE]
   > Bu Windows Güvenliği etkin olması gerekmektedir, ancak [Gerçek zamanlı koruma ve Davranış monitörü](/windows/security/threat-protection/microsoft-defender-antivirus/configure-real-time-protection-microsoft-defender-antivirus)) etkinleştirilmelidir.

3. Aşağıdaki Windows Güncelleştirmeleri Windows 10 izlenir cihazlar için yüklenir.

   > [!NOTE]
   > Bu güncelleştirmeler bir cihazı eklemenin önkulları değildir, önemli sorunlar için düzeltmeler içerir, bu nedenle ürünü kullanamadan önce yüklenmeleri gerekir.
   >
    > - Kb4559003 Windows 10 1809 - KB4559003, KB4577069, KB4580390
    > - Kb4559004 Windows 10 1903 veya 1909 için - KB4559004, KB4577062, KB4580386
    > - DAHA Windows 10 2004 - KB4568831, KB4577063

4. Tüm cihazlar şu cihazlardan biri olabilir:

   - [Azure Active Directory (Azure AD) ile katılan](/azure/active-directory/devices/concept-azure-ad-join)
   - [Hibrit Azure AD ile katılan](/azure/active-directory/devices/concept-azure-ad-join-hybrid)
   - [AAD kayıtlı](/azure/active-directory/user-help/user-help-register-device-on-network)

5. Desteklenen bir Microsoft Office yüklü ve günceldir. En güçlü koruma ve kullanıcı deneyimi için 16.0.14701.0 Microsoft 365 Uygulamaları veya daha yeni bir sürümün yüklü olduğundan emin olun.
> [!NOTE]
   > - Çalışma boyutu - Office 365 KB 4577063 gereklidir.
   > - 2004-2008 Enterprise aylık Microsoft 365 Uygulamaları Kanalı'dır, 2009 veya sonraki sürümlere güncelleştirmeniz gerekir. Geçerli [sürümler için Microsoft 365 Uygulamaları (tarihe göre listelenmiş) güncelleştirme](/officeupdates/update-history-microsoft365-apps-by-date) geçmişi'ne bakın. Bilinen sorun hakkında daha fazla bilgi edinmek için [2020'de](/officeupdates/current-channel#version-2010-october-27) geçerli Kanal yayınlarına Office Paketi bölümüne bakın.

6. İnternet'e bağlanmak için cihaz ara sunucusunu kullanan uç noktalarınız varsa, Cihaz ara sunucusunu ve Bilgi Koruması için İnternet bağlantısı ayarlarını yapılandırma'daki [yordamları izleyin](device-onboarding-configure-proxy.md#configure-device-proxy-and-internet-connection-settings-for-information-protection).

## <a name="onboarding-windows-10-or-windows-11-devices"></a>11 Windows 10 veya Windows cihaz ekleme

Cihazda hassas öğeleri izleymeden ve koruyamadan önce cihaz izlemeyi etkinleştirmeniz ve uç noktalarınızı eklemeniz gerekir. Bu eylemlerin ikisi de Uyumluluk Portalı'Microsoft 365 yapılır.

Henüz eklememiş cihazları almak istediğinizde, uygun betiği indirmiş ve bu cihazlara dağıtmış oluruz. Aşağıdaki cihaz ekleme yordamlarını izleyin.

Uç Nokta için [Microsoft Defender'a önceden cihazlarınız](/windows/security/threat-protection/) varsa, bunlar yönetilen cihazlar listesinde zaten görünür.

Bu dağıtım senaryosunda, henüz Windows 10 11 Windows cihaza veya başka bir cihaza sahip oluruz.

1. Microsoft uyumluluk [merkezini açın](https://compliance.microsoft.com).  >  Ayarlar **Enable cihaz izleme'yi seçin**.

   > [!NOTE]
   > Cihaz eklemenin etkinleştirilmesi genellikle yaklaşık 60 saniye sürerken, Microsoft desteğiyle iletişime başlamadan önce lütfen 30 dakika kadar bekleyin.

2. Uyumluluk Merkezi ayarlar sayfasını açın ve Cihazları **ekleyin'i seçin**.

   > [!div class="mx-imgBorder"]
   > ![cihaz yönetimini etkinleştirin.](../media/endpoint-dlp-learn-about-1-enable-device-management.png)

3. Cihazlar **listesini açmak** için Cihaz **yönetimi'ne** tıklayın. 

> [!NOTE]
> Uç nokta için Microsoft Defender'ı daha önce dağıttıysanız, bu işlem sırasında ekli olan tüm cihazlar Cihazlar **listesinde** listelenir. Yeniden eklemeye gerek yok.

4. Ekleme **işlemini başlamak** için Ekleme'yi seçin.

5. Dağıtım yöntemi listesinden bu ek cihazlara dağıtmak istediğiniz **yöntemi seçin** ve ardından paketi **indirin**.

6. Aşağıdaki tablodan takip etmek için uygun yordamı seçin:

Konu | Açıklama
:---|:---
[Grup Windows 10 kullanarak 11 veya 11 cihazı ekleme](device-onboarding-gp.md) | Yapılandırma paketini cihazlara dağıtmak için Grup İlkesi'ne kullanın.
[Windows 10 kullanarak 11 veya 11 cihaz Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md) | Yapılandırma paketini cihazlara dağıtmak için Microsoft Endpoint Configuration Manager (geçerli dalı) sürüm 1606 veya Microsoft Endpoint Configuration Manager (geçerli dalı) sürüm 1602 veya daha önceki bir sürümünü kullanabilirsiniz.
[Mobil Windows 10 yönetim araçlarını kullanarak cihaz kullanın veya 11 cihazı kullanın](device-onboarding-mdm.md) | Mobil Cihaz Yönetimi araçlarını veya Microsoft Intune paketin dağıtımı için Mobil Cihaz Yönetimi araçlarını kullanın.
[Yerel Windows 10 kullanarak 11 veya 11 cihaza ekleme](device-onboarding-script.md) | Uç noktalara yapılandırma paketini dağıtmak için yerel betiği kullanmayı öğrenin.
[Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarını ekleme](device-onboarding-vdi.md) | VDI cihazlarını yapılandırmak için yapılandırma paketini kullanmayı öğrenin.

Bir cihaz alındıktan sonra, cihaz listesinde görünür olmalı ve denetim etkinliği günlüklerini Etkinlik gezginine bildirmeye başla olmalıdır.

### <a name="viewing-endpoint-dlp-alerts-in-dlp-alerts-management-dashboard"></a>DLP Uyarıları Yönetimi panosunda Uç Nokta DLP uyarılarını görüntüleme

1. Çalışma sayfasında Veri kaybı önleme sayfasını <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">açın ve Microsoft 365 uyumluluk merkezi'ı</a> seçin.

2. Uç Nokta DLP [ilkelerinize yönelik uyarıları görüntülemek üzere DLP](dlp-configure-view-alerts-policies.md) ilkelerinizin uyarılarını yapılandırma ve görüntüleme makalesinde yer alan yordamlara bakın.

### <a name="viewing-endpoint-dlp-data-in-activity-explorer"></a>Etkinlik gezgininde Uç Nokta DLP verilerini görüntüleme

1. Uyumluluk merkezinde [etki alanınız](https://compliance.microsoft.com/dataclassification?viewid=overview) için Veri sınıflandırma sayfasını Microsoft 365 Gezgini'ni seçin.

2. Uç nokta cihazlarınız için [tüm verilere erişmek ve](data-classification-activity-explorer.md) bu verilere filtre uygulama için Etkinlik gezginiyle çalışmaya başlama'daki yordamlara bakın.

   > [!div class="mx-imgBorder"]
   > ![uç nokta cihazları için etkinlik gezgini filtresi.](../media/endpoint-dlp-4-getting-started-activity-explorer.png)


## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft 365'da Insider risk yönetimi hakkında bilgi Microsoft 365](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)
- [Uç nokta veri kaybını önleme hakkında bilgi](endpoint-dlp-learn-about.md)
- [Uç nokta veri kaybını önlemeyi kullanma](endpoint-dlp-using.md)
- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)
- [DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md)
- [Etkinlik gezgini ile çalışmaya başlama](data-classification-activity-explorer.md)
- [Uç Nokta için Microsoft Defender](/windows/security/threat-protection/)
- [Makine makineniz için ekleme araçları Windows 10 yöntemleri](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)
- [Microsoft 365 aboneliği](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Azure AD'ye katılan cihazlar](/azure/active-directory/devices/concept-azure-ad-join)
- [Temel Microsoft Edge yeni Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
