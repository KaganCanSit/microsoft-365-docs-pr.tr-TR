---
title: Intune kullanarak Windows cihazlarını Uç Nokta için Defender'a ekleme
description: Uç Nokta için Defender hizmetine eklenmeleri için yapılandırma paketini cihazlara dağıtmak için Microsoft Intune kullanın.
keywords: mdm kullanarak cihazları ekleme, cihaz yönetimi, Uç Nokta için Microsoft Defender cihazları ekleme, mdm
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 90c6ec688b19f328f89e2bcabe70b7955086e8da
ms.sourcegitcommit: c6f1486617b39565bfd8f662ee6ad65a9cefd3e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66531066"
---
# <a name="onboard-windows-devices-to-defender-for-endpoint-using-intune"></a>Intune kullanarak Windows cihazlarını Uç Nokta için Defender'a ekleme 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configureendpointsmdm-abovefoldlink)

Windows 10 cihazları yapılandırmak için mobil cihaz yönetimi (MDM) çözümlerini kullanabilirsiniz. Uç Nokta için Defender, cihazları yönetmeye yönelik ilkeler oluşturmak için OMA-URIs sağlayarak MDM'leri destekler.

Uç Nokta için Defender CSP'yi kullanma hakkında daha fazla bilgi için bkz. [WindowsAdvancedThreatProtection CSP](https://msdn.microsoft.com/library/windows/hardware/mt723296(v=vs.85).aspx) ve [WindowsAdvancedThreatProtection DDF dosyası](https://msdn.microsoft.com/library/windows/hardware/mt723297(v=vs.85).aspx).

## <a name="before-you-begin"></a>Başlamadan önce

Cihazların Mobil Cihaz Yönetimi (MDM) çözümünüz olarak Intune ile kaydedilmesi gerekir.

MDM'yi Microsoft Intune ile etkinleştirme hakkında daha fazla bilgi için bkz[. Cihaz kaydı (Microsoft Intune)](/mem/intune/enrollment/device-enrollment).

## <a name="onboard-devices-using-microsoft-intune"></a>Microsoft Intune kullanarak cihazları ekleme

Uç Nokta için Defender'ı dağıtma ile ilgili çeşitli yolları görmek için [PDF](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.pdf) veya [Visio'ya](https://download.microsoft.com/download/5/6/0/5609001f-b8ae-412f-89eb-643976f6b79c/mde-deployment-strategy.vsdx) göz atın.

[Intune](/mem/intune/protect/advanced-threat-protection-configure#enable-microsoft-defender-for-endpoint-in-intune) yönergelerini izleyin.


Uç Nokta için Defender CSP'yi kullanma hakkında daha fazla bilgi için bkz. [WindowsAdvancedThreatProtection CSP](https://msdn.microsoft.com/library/windows/hardware/mt723296(v=vs.85).aspx) ve [WindowsAdvancedThreatProtection DDF dosyası](https://msdn.microsoft.com/library/windows/hardware/mt723297(v=vs.85).aspx).

> [!NOTE]
>
> - **Eklenen cihazlar için Sistem Durumu** ilkesi salt okunur özellikleri kullanır ve düzeltilemiyor.
> - Tanılama veri raporlama sıklığı yapılandırması yalnızca Windows 10 sürüm 1703'te bulunan cihazlar için kullanılabilir.
> - Uç Nokta için Defender'a eklendiğinde cihaz, Microsoft 365 uyumluluğunun da bir parçası olan [Veri Kaybı Önleme'ye (DLP)](../../compliance/endpoint-dlp-learn-about.md) eklenir.


## <a name="run-a-detection-test-to-verify-onboarding"></a>Ekleme işlemini doğrulamak için algılama testi çalıştırma
Cihazı ekledikten sonra, bir cihazın hizmete düzgün şekilde eklendiğini doğrulamak için bir algılama testi çalıştırmayı seçebilirsiniz. Daha fazla bilgi için bkz. [Yeni eklenen Uç Nokta için Microsoft Defender cihazında algılama testi çalıştırma](run-detection-test.md).


## <a name="offboard-devices-using-mobile-device-management-tools"></a>Mobil Cihaz Yönetimi araçlarını kullanarak cihazları çıkarma

Güvenlik nedeniyle, cihazları kullanıma almak için kullanılan paketin süresi, indirildiği tarihten 30 gün sonra dolar. Bir cihaza gönderilen süresi dolan çıkarma paketleri reddedilir. Bir çıkarma paketini indirirken paketlerin son kullanma tarihi size bildirilir ve paket adına da eklenir.

> [!NOTE]
> Ekleme ve çıkarma ilkeleri aynı cihazda aynı anda dağıtılmamalıdır, aksi takdirde bu öngörülemeyen çakışmalara neden olur.

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalından</a> çıkarma paketini alın:

   1. Gezinti bölmesinde **Ayarlar** \> **Uç Noktaları** \> **Cihaz yönetimi** \> **Çıkarma'yı** seçin.

   1. İşletim sistemi olarak Windows 10 veya Windows 11 seçin.

   1. **Dağıtım yöntemi** alanında **Mobil Cihaz Yönetimi / Microsoft Intune'ı** seçin.

   1. **Paketi indir'e** tıklayın ve .zip dosyasını kaydedin.

2. .zip dosyasının içeriğini, paketi dağıtacak ağ yöneticileri tarafından erişilebilen paylaşılan, salt okunur bir konuma ayıklayın. *WindowsDefenderATP_valid_until_YYYY-MM-DD.offboarding* adlı bir dosyanız olmalıdır.

3. Aşağıdaki desteklenen OMA-URI ayarlarını dağıtmak için Microsoft Intune özel yapılandırma ilkesini kullanın.
   - OMA-URI: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
   - Tarih türü: Dize
   - Değer: [WindowsDefenderATP_valid_until_YYYY-MM-DD.offboarding dosyasının içeriğindeki değeri kopyalayıp yapıştırın]

Microsoft Intune ilke ayarları hakkında daha fazla bilgi için bkz. [Microsoft Intune'da ilke ayarlarını Windows 10](/mem/intune/configuration/custom-settings-windows-10).

> [!NOTE]
> **Kullanıma alınan cihazlar için Sistem Durumu** ilkesi salt okunur özellikleri kullanır ve düzeltilemiyor.

> [!IMPORTANT]
> Kullanıma alma, cihazın portala algılayıcı verileri göndermeyi durdurmasına neden olur, ancak sahip olduğu uyarılara başvuru da dahil olmak üzere cihazdaki veriler 6 aya kadar saklanır.

## <a name="related-topics"></a>İlgili konular
- [Windows araçlarını Grup İlkesi kullanarak ekleyin](configure-endpoints-gp.md)
- [Microsoft Endpoint Configuration Manager kullanarak Windows cihazlarını ekleyin](configure-endpoints-sccm.md)
- [Windows araçlarını yerel betik kullanarak ekleyin](configure-endpoints-script.md)
- [Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarının katılımı](configure-endpoints-vdi.md)
- [Yeni eklenen bir Uç Nokta için Microsoft Defender cihazında algılama testi çalıştırma](run-detection-test.md)
- [Uç Nokta için Microsoft Defender ekleme sorunlarını giderme](troubleshoot-onboarding.md)
