---
title: Yerel bir komut dosyası kullanan Windows 10 ve Windows 11 cihazlarının katılımı
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
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: Yapılandırma paketini hizmete eklenmeleri için cihazlara dağıtmak için yerel bir betik kullanın.
ms.openlocfilehash: 840573794b447162f917fed162bb1f869585286e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634433"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-a-local-script"></a>Yerel bir komut dosyası kullanan Windows 10 ve Windows 11 cihazlarının katılımı

**Şunlar için geçerlidir:**

- [Uç nokta veri kaybı önleme (DLP)](./endpoint-dlp-learn-about.md)
- [İçeriden risk yönetimi](insider-risk-management.md)

Ayrıca tek tek cihazları Microsoft 365'e el ile de ekleyebilirsiniz. Ağınızdaki tüm cihazları eklemeyi taahhüt etmeden önce hizmeti test ederken bunu yapmak isteyebilirsiniz.

> [!IMPORTANT]
> Bu betik en fazla 10 cihazda kullanılmak üzere iyileştirilmiştir.
>
> Büyük ölçekte dağıtmak için [diğer dağıtım seçeneklerini](device-onboarding-overview.md) kullanın. Örneğin, grup ilkesi [kullanarak ekleme Windows 10 cihazlarda](device-onboarding-gp.md) kullanılabilen betikle üretimdeki 10'dan fazla cihaza ekleme betiği dağıtabilirsiniz.

## <a name="onboard-devices"></a>Cihazları ekleme
 
1. Microsoft Purview uyumluluk portalı yapılandırma paketi .zip dosyası (*DeviceComplianceOnboardingPackage.zip*) paketini alma [](https://compliance.microsoft.com)

2. Gezinti bölmesinde <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ayarlar**</a> > **Cihaz ekleme'yi** seçin.

3. **Dağıtım yöntemi** alanında **Yerel Betik'i** seçin.

4. **Paketi indir'e** tıklayın ve .zip dosyasını kaydedin.
  
5. Yapılandırma paketinin içeriğini eklemek istediğiniz cihazdaki bir konuma (örneğin, Masaüstü) ayıklayın. *DeviceOnboardingScript.cmd* adlı bir dosyanız olmalıdır.

6. Cihazda yükseltilmiş bir komut satırı istemi açın ve betiği çalıştırın:

7. **Başlangıç'a** gidin ve **cmd** yazın.

8. **Komut istemi'ne** sağ tıklayın ve **Yönetici olarak çalıştır'ı** seçin.

    ![Yönetici olarak çalıştır'a işaret eden Pencere Başlat menüsü.](../media/dlp-run-as-admin.png)

9. Betik dosyasının konumunu yazın. Dosyayı masaüstüne kopyaladıysanız şunu yazın: *%userprofile%\Desktop\WindowsDefenderATPOnboardingScript.cmd*

10. **Enter** tuşuna basın veya **Tamam'a** tıklayın.

Cihazın uyumlu olduğunu el ile nasıl doğrulayabileceğiniz ve algılayıcı verilerini doğru şekilde bildirebileceğiniz hakkında bilgi için bkz. [Microsoft Defender Gelişmiş Tehdit Koruması ekleme sorunlarını giderme](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding).

## <a name="offboard-devices-using-a-local-script"></a>Yerel betik kullanarak cihazları çıkarma

Güvenlik nedeniyle, cihazları kullanıma almak için kullanılan paketin süresi, indirildiği tarihten 30 gün sonra dolar. Bir cihaza gönderilen süresi dolan çıkarma paketleri reddedilir. Bir çıkarma paketini indirirken paketlerin son kullanma tarihi size bildirilir ve paket adına da eklenir.

> [!NOTE]
> Ekleme ve çıkarma ilkeleri aynı cihazda aynı anda dağıtılmamalıdır, aksi takdirde bu öngörülemeyen çakışmalara neden olur.

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalı'dan</a> çıkarma paketini alın.

2. Gezinti bölmesinde <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ayarlar**</a> > **Cihaz çıkarma'yı** seçin.

3. **Dağıtım yöntemi** alanında **Yerel Betik'i** seçin.

4. **Paketi indir'e** tıklayın ve .zip dosyasını kaydedin.

5. .zip dosyasının içeriğini cihazlar tarafından erişilebilen paylaşılan, salt okunur bir konuma ayıklayın. *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd* adlı bir dosyanız olmalıdır.

6. Cihazda yükseltilmiş bir komut satırı istemi açın ve betiği çalıştırın:

7. **Başlangıç'a** gidin ve **cmd** yazın.

8. **Komut istemi'ne** sağ tıklayın ve **Yönetici olarak çalıştır'ı** seçin.

    ![Yönetici olarak çalıştır'a işaret eden Pencere Başlat menüsü.](../media/dlp-run-as-admin.png)

9. Betik dosyasının konumunu yazın. Dosyayı masaüstüne kopyaladıysanız şunu yazın: *%userprofile%\Desktop\WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*

10. **Enter** tuşuna basın veya **Tamam'a** tıklayın.

> [!IMPORTANT]
> Çıkarma, cihazın portala algılayıcı verileri göndermeyi durdurmasına neden olur.

## <a name="monitor-device-configuration"></a>Cihaz yapılandırmasını izleme

Betiğin başarıyla tamamlandığını ve aracının çalıştığını doğrulamak için [Ekleme sorunlarını giderme]((/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding) içindeki farklı doğrulama adımlarını izleyebilirsiniz.

İzleme doğrudan portalda veya farklı dağıtım araçları kullanılarak da yapılabilir.

### <a name="monitor-devices-using-the-portal"></a>Portalı kullanarak cihazları izleme

1. [Microsoft Purview uyumluluk portalı'a](https://compliance.microsoft.com) gidin.

2. **Ayarlar** > **Cihaz ekleme Cihazları'nı** >  seçin.

1. Microsoft Purview uyumluluk portalı gidin ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ayarlar**</a> > **Cihaz ekleme Cihazları'nı** >  seçin.

1. Cihazların görüntülendiğini doğrulayın.

## <a name="related-topics"></a>İlgili konular
- [grup ilkesi kullanarak Windows 10 ve Windows 11 cihazları ekleme](device-onboarding-gp.md)
- [Microsoft Endpoint Configuration Manager kullanarak Windows 10 ve Windows 11 cihazları ekleme](device-onboarding-sccm.md)
- [Mobil Cihaz Yönetimi araçlarını kullanan Windows 10 ve Windows 11 cihazlarının katılımı](device-onboarding-mdm.md)
- [Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarının katılımı](device-onboarding-vdi.md)
- [Yeni eklenen bir Uç Nokta için Microsoft Defender cihazında algılama testi çalıştırma](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Microsoft Defender Gelişmiş Tehdit Koruması ekleme sorunlarını giderme](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
