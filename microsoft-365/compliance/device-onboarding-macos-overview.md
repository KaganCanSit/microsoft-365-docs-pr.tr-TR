---
title: MacOS cihazlarını mobil cihazlara Microsoft 365 genel bakış (önizleme)
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: MacOS cihazlarını Uyumluluk çözümlerine ekleme hakkında bilgi edinin
ms.openlocfilehash: 93a930f13a17c19c3ff7209295ddada648b9575a
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63526576"
---
# <a name="onboard-macos-devices-into-microsoft-365-overview-preview"></a>MacOS cihazlarını mobil cihazlara Microsoft 365 genel bakış (önizleme)

MacOS cihazları, Intune veya JAM Pro F Microsoft 365 uyumluluk çözümleri kullanılarak kullanılabilir. Ekleme yordamları, kullandığınız yönetim çözümüne bağlı olarak farklılık gösterir. macOS cihazlarınız Uç Nokta için Microsoft Defender'a (MDE) önceden ekli olarak alındısa, daha az adım vardır. Size [uygun yordamların](#next-steps) bağlantıları için sonraki adımlara bakın.

**Aşağıdakiler için geçerlidir:**

- [Microsoft 365 Uç nokta veri kaybı önleme (DLP)](./endpoint-dlp-learn-about.md)
- [Insider risk yönetimi](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

## <a name="before-you-begin"></a>Başlamadan önce

MacOS cihazlarında Uç Nokta DLP(Catalina 10.15 veya sonrası) ile çalışmaya başlamadan önce şu makaleleri tanımanız gerekir:

- [Uç nokta Microsoft 365 kaybı önleme hakkında bilgi](endpoint-dlp-learn-about.md#learn-about-microsoft-365-endpoint-data-loss-prevention)
- [Uç nokta veri kaybını önlemeye başlama](endpoint-dlp-getting-started.md#get-started-with-endpoint-data-loss-prevention)

DLP'ye hiç aşina değilsanız, şu makaleleri de tanımanız gerekir:

- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md#learn-about-data-loss-prevention)
- [Veri kaybı önleme (DLP) planı](dlp-overview-plan-for-dlp.md#plan-for-data-loss-prevention-dlp)
- [Veri Kaybı Önleme ilke başvurusu](dlp-policy-reference.md#data-loss-prevention-policy-reference)

Insider Riski'ne aşina değilsanız, şu makaleleri tanımanız gerekir:

 - [Insider risk yönetimi](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)
 - [Insider risk yönetimini planlama](insider-risk-management-plan.md#plan-for-insider-risk-management)

macOS cihazlarınız intune veya JAMF mobil cihazlarında zaten Pro.
 
- Intune'a başlangıç yapmak için bkz. [Dağıtım kılavuzu: Microsoft Intune'de macOS](/mem/intune/fundamentals/deployment-guide-platform-macos) cihazlarını yönetme ve [Mac'inizi Başka bir Intune Şirket Portalı](/mem/intune/user-help/enroll-your-device-in-intune-macos-cp). 
- JAMF yönetim Pro için [bkz. JAMF Pro](https://www.jamf.com/resources/product-documentation/jamf-pro-administrators-guide/) yöneticisi kılavuzu ve [JAMF mac Pro Yapılandırma Kılavuzu](https://www.jamf.com/resources/product-documentation/jamf-pro-installation-guide-for-mac/)
- v95+ Edge tarayıcısını macOS cihazlarınıza yükleme 

## <a name="licensing-guidance"></a>Lisanslama kılavuzu

Bilgi Microsoft 365 [lisanslama kılavuzuna bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

## <a name="activities-that-can-be-restricted-on-macos"></a>macOS'ta kısıtlanabilir etkinlikler 

Uyumluluk çözümlerine bir macOS cihazı Microsoft 365, veri kaybı önleme (DLP) ilkeleriyle bu eylemleri izleyebilir ve kısıt edebilirsiniz.

**USB çıkarılabilir** medyaya kopyalama – bu eylem zorunlu olduğunda korumalı dosyaların uç nokta cihazından USB çıkarılabilir medyaya kopyalayıp taşıması konusunda uyarma ya da denetimler sağlar 

**Ağ paylaşımlara kopyalama** – zorunlu tutulsa bu eylem, korumalı dosyaların uç nokta cihazından herhangi bir ağ paylaşımına kopyalayıp taşıması için bloklar, uyarılar veya denetimler sağlar 

**Yazdırma** – zorunlu olduğunda, korumalı dosyalar uç nokta cihazından yazdırılırken bu eylem blokları, uyarılarını veya denetimleri engeller 

**Panoya kopyala** – zorunlu olduğunda bu eylem, uç nokta cihazında panoya kopyalanan korumalı dosyadaki verileri engeller, uyarır veya denetimler sağlar 

**Upload buluta** yükseltme – Genel ayarlarda yer alan izin verilen/izin verilmeyen etki alanları listesi temel alarak korumalı dosyaların bulut hizmetlerine karşıya yüklemesi engellenebilir veya bu dosyalar için izin verilmeyen bu eylem blokları, uyarılarını veya denetimleri engeller. Bu eylem uyarmaya veya engellemeye ayarlandığı zaman, diğer tarayıcıların (Genel ayarlar altındaki izin verilmeyen tarayıcılar listesinde tanımlanmış olan tarayıcılar) dosyaya erişimi engellenir. 

**Izin verilmeyen** uygulamalar tarafından erişilir – zorunlu olduğunda, bu eylem izin verilmeyen uygulamalar listesinde yer alan uygulamaların (Genel ayarlarda tanımlandığı gibi) uç nokta cihazında korumalı dosyalara erişmesini engelleme. Örnek senaryolar 

## <a name="onboarding-devices-into-device-management"></a>Cihazları cihaz yönetimine ekleme

Cihazda hassas öğeleri izleymeden ve koruyamadan önce cihaz izlemeyi etkinleştirmeniz ve uç noktalarınızı eklemeniz gerekir. Bu eylemlerin ikisi de Uyumluluk Portalı'Microsoft 365 yapılır.

Henüz eklememiş cihazları almak istediğinizde, uygun betiği indirmiş ve bu cihazlara dağıtmış oluruz. <!--Follow the [Onboarding devices procedure](endpoint-dlp-getting-started.md#onboarding-devices).-->

<!--If you already have devices onboarded into [Microsoft Defender for Endpoint](/windows/security/threat-protection/), they will already appear in the managed devices list.-->

1. Cihaz [izlemeyi etkinleştir'Ayarlar](https://compliance.microsoft.com)  Microsoft uyumluluk merkezi **sayfasını açın**.

   > [!NOTE]
   > Cihaz eklemenin etkinleştirilmesi genellikle yaklaşık 60 saniye sürerken, Microsoft desteğiyle iletişime başlamadan önce lütfen 30 dakika kadar bekleyin.

2. Uyumluluk Merkezi ayarlar sayfasını açın ve Cihazları **ekleyin'i seçin**.

   > [!div class="mx-imgBorder"]
   > ![cihaz yönetimini etkinleştirin.](../media/endpoint-dlp-learn-about-1-enable-device-management.png)

## <a name="next-steps"></a>Sonraki adımlar

DLP algılayıcı telemetrisi al Microsoft 365 veri kaybı önleme ilkelerinin uygulanması için cihazların uyumluluk çözümleriyle birlikte kullanılabilir olması gerekir. 

Konu | Açıklama
:---|:---
|[Intune (önizleme) kullanarak MacOS cihazlarını Microsoft 365 Uyumluluk çözümlerine ekleme ve çıkarma](device-onboarding-offboarding-macos-intune.md#onboard-and-offboard-macos-devices-into-microsoft-365-compliance-solutions-using-intune-preview)|Intune aracılığıyla yönetilen macOS cihazlar için
|[Uç nokta müşterileri için Microsoft Defender'ı kullanarak MacOS cihazlarını Uyumluluk çözümlerine ekleme ve çıkararak kullanma (önizleme)](device-onboarding-offboarding-macos-intune-mde.md#onboard-and-offboard-macos-devices-into-compliance-solutions-using-intune-for-microsoft-defender-for-endpoint-customers-preview) |Intune üzerinden yönetilen ve Uç Nokta (MDE) için Microsoft Defender'ın dağıtıldı olduğu macOS cihazlar için
|[JAMF uyumluluk çözümleri kullanarak macOS cihazlarını Microsoft 365 kullanma ve çıkararak uyumluluk çözümlerine (Pro)](device-onboarding-offboarding-macos-jamfpro.md#onboard-and-offboard-macos-devices-into-microsoft-365-compliance-solutions-using-jamf-pro-preview) | JAMF tarafından yönetilen macOS cihazlar Pro
|[Uç nokta müşterileri için Microsoft Defender 'da JAMF Pro kullanarak MacOS cihazlarını ekleme ve çıkararak Uyumluluk çözümlerine ekleme (önizleme)](device-onboarding-offboarding-macos-jamfpro-mde.md#onboard-and-offboard-macos-devices-into-compliance-solutions-using-jamf-pro-for-microsoft-defender-for-endpoint-customers-preview)|JAMF hizmeti aracılığıyla yönetilen ve Uç Nokta için Microsoft Defender (MDE) Pro bu cihazlara dağıtılan macOS cihazlar için


## <a name="related-topics"></a>İlgili konular

- [Uç nokta veri kaybını önlemeyi kullanma](endpoint-dlp-using.md#using-endpoint-data-loss-prevention)
- [Microsoft uygulamaları genelinde DLP ilkesi ipuçları için Destek Matrisi](dlp-policy-tips-reference.md#support-matrix-for-dlp-policy-tips-across-microsoft-apps)
