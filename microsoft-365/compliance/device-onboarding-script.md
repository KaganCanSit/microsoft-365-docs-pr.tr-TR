---
title: Yerel bir Windows 10 kullanarak Windows 10 ve 11 Windows cihaz kullanın
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
description: Yapılandırma paketini hizmete dahil etmek üzere cihazlara dağıtmak için yerel bir betik kullanın.
ms.openlocfilehash: 14412e782cffd597786a4d2c322fe2b8fc20e5ca
ms.sourcegitcommit: 8eca41cd21280ffcb1f50cafce7a934e5544f302
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2021
ms.locfileid: "62999581"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-a-local-script"></a>Yerel bir Windows 10 kullanarak Windows 10 ve 11 Windows cihaz kullanın

**Aşağıdakiler için geçerlidir:**

- [Microsoft 365 Uç nokta veri kaybı önleme (DLP)](./endpoint-dlp-learn-about.md)
- [Insider risk yönetimi](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

Ayrıca cihaz eklemeye tek tek cihazları el ile Microsoft 365. Bunu, ağ üzerindeki tüm cihazları eklemeye karardan önce hizmeti test etmek için yapmak iyi bir durum olabilir.

> [!IMPORTANT]
> Bu betik, 10 cihaza kadar kullanım için en iyi duruma getirilmiş.
>
> Ölçekte dağıtmak için diğer dağıtım [seçeneklerini kullanın](device-onboarding-overview.md). Örneğin, üretimde 10'dan fazla cihaza bir ekleme betiği dağıtabilirsiniz ve bu betiği Grup İlkesi kullanarak [Windows 10](device-onboarding-gp.md) cihazlarında kullanılabilir.

## <a name="onboard-devices"></a>Cihazları ekleme
 
1. Microsoft Uyumluluk Merkezi'.zip yapılandırma *paketiDeviceComplianceOnboardingPackage.zip*) paketini [al](https://compliance.microsoft.com)

2. Gezinti bölmesinde,Device <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**ekleme Ayarlar**</a> >  **seçin**.

3. Dağıtım yöntemi **alanında Yerel** **Betik'i seçin**.

4. Paketi **indir'e** tıklayın ve .zip kaydedin.
  
5. Yapılandırma paketinin içeriğini, eklemek istediğiniz cihazda (örneğin Masaüstü) bir konuma ayıklar. *DeviceOnboardingScript.cmd adlı bir dosyanız olmalıdır*.

6. Cihazda yükseltilmiş bir komut satırı istemi açın ve betiği çalıştırın:

7. **Başlat'a gidin** ve **cmd yazın**.

8. Komut istemi'ne **sağ tıklayın ve** Yönetici olarak **çalıştır'ı seçin**.

    ![Window Başlat menüsü Yönetici olarak çalıştır'a işaret ediyor olabilir.](../media/dlp-run-as-admin.png)

9. Betik dosyasının konumunu yazın. Dosyayı masaüstüne kopyaladıysanız, şöyle yazın: *%userprofile%\Desktop\WindowsDefenderATPOnboardingScript.cmd*

10. **Enter tuşuna basın** veya Tamam'a **tıklayın**.

Cihazın uyumlu olduğunu el ile nasıl doğru şekilde doğrulayabilirsiniz hakkında bilgi için bkz. [Microsoft Defender Gelişmiş Tehdit Koruması ekleme sorunlarını giderme](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding).

## <a name="offboard-devices-using-a-local-script"></a>Yerel betik kullanan offboard cihazları

Güvenlik nedeniyle, Offboard cihazları için kullanılan paketin süresi, indirildikten 30 gün sonra sona erer. Bir cihaza gönderilen süresi dolmuş offboard paketleri reddedilir. Bir çıkartan kullanım paketi indirirken paketlerin son kullanma tarihi size bildirilecek ve paket adına da bu paket dahil edilecektir.

> [!NOTE]
> Ekleme ve çıkarma ilkeleri aynı cihazda aynı anda dağıtıldığından, öngörülemeyen zararlara neden olur.

1. Bir panodan çıkar <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">paketine Microsoft 365 uyumluluk merkezi</a>.

2. Gezinti bölmesinde, <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Panodan**</a> **Ayarlar'ı** >  seçin.

3. Dağıtım yöntemi **alanında Yerel** **Betik'i seçin**.

4. Paketi **indir'e** tıklayın ve .zip kaydedin.

5. Bu dosyanın içeriğini .zip cihazlar tarafından erişilebilen, paylaşılan, salt okunur bir konuma ayıklar. *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd adlı bir dosyanız olmalıdır*.

6. Cihazda yükseltilmiş bir komut satırı istemi açın ve betiği çalıştırın:

7. **Başlat'a gidin** ve **cmd yazın**.

8. Komut istemi'ne **sağ tıklayın ve** Yönetici olarak **çalıştır'ı seçin**.

    ![Window Başlat menüsü Yönetici olarak çalıştır'a işaret ediyor olabilir.](../media/dlp-run-as-admin.png)

9. Betik dosyasının konumunu yazın. Dosyayı masaüstüne kopyalediysanız, şöyle yazın: *%userprofile%\Desktop\WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd*

10. **Enter tuşuna basın** veya Tamam'a **tıklayın**.

> [!IMPORTANT]
> Offboard, cihazın algılayıcı verilerinin portala gönderilmesini durdurmaya neden olur.

## <a name="monitor-device-configuration"></a>Cihaz yapılandırmasını izleme

Betiğin başarıyla tamamlandıktan ve aracının çalıştığını doğrulamak için [Ekleme sorunlarını giderme]((/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding) altında farklı doğrulama adımlarını izleyin.

İzleme doğrudan portalda veya farklı dağıtım araçları kullanılarak da yapılabilir.

### <a name="monitor-devices-using-the-portal"></a>Portalı kullanarak cihazları izleme

1. Uyumluluk [Microsoft 365 gidin](https://compliance.microsoft.com).

2. Diğer **Ayarlar** >  **Device** **eklemeCicileri** >  seçin.

1. Ekran'Microsoft 365 uyumluluk merkezi gidin ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2174201" target="_blank">**Ayarlar**</a> >  **Device onboardingDevices** >  **öğesini seçin**.

1. Cihazların görüntüde olduğunu doğrulayın.

## <a name="related-topics"></a>İlgili konular
- [Grup Windows 10 kullanarak Windows 11 cihazı ekleme ve kullanma](device-onboarding-gp.md)
- [Microsoft Endpoint Configuration Manager kullanarak Windows 10 cihaz ve 11 Windows cihaz Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Mobil Windows 10 araçları Windows 11 cihaza ekleme ve kullanma](device-onboarding-mdm.md)
- [Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarını ekleme](device-onboarding-vdi.md)
- [Yeni eklenen Uç nokta cihazı için Microsoft Defender'da bir algılama testi çalıştırma](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Microsoft Defender Gelişmiş Tehdit Koruması'nın ekleme sorunlarını giderme](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)