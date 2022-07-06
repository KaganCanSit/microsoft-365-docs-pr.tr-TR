---
title: Mobil Cihaz Yönetimi araçlarını kullanan Windows 10 ve Windows 11 cihazlarının katılımı
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
description: Yapılandırma paketini hizmete eklenmeleri için cihazlara dağıtmak için Mobile Cihaz Yönetimi araçlarını kullanın.
ms.openlocfilehash: d5c03c80c9a38d34ab27f888084604372874a64a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624211"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-mobile-device-management-tools"></a>Mobil Cihaz Yönetimi araçlarını kullanan Windows 10 ve Windows 11 cihazlarının katılımı

**Şunlar için geçerlidir:**

- [Uç nokta veri kaybı önleme (DLP)](./endpoint-dlp-learn-about.md)
- [İçeriden risk yönetimi](insider-risk-management.md)

Cihazları yapılandırmak için mobil cihaz yönetimi (MDM) çözümlerini kullanabilirsiniz. Microsoft 365 bilgi koruması, cihazları yönetmek için ilkeler oluşturmak için OMA-URIs sağlayarak MDM'leri destekler.


## <a name="before-you-begin"></a>Başlamadan önce
Microsoft Intune kullanıyorsanız cihaz MDM'sini kaydetmiş olmanız gerekir. Aksi takdirde, ayarlar başarıyla uygulanmaz. 

MDM'yi Microsoft Intune ile etkinleştirme hakkında daha fazla bilgi için bkz[. Cihaz kaydı (Microsoft Intune)](/mem/intune/enrollment/device-enrollment).

## <a name="onboard-devices-using-microsoft-intune"></a>Microsoft Intune kullanarak cihazları ekleme

[Intune](/mem/intune/protect/advanced-threat-protection-configure) yönergelerini izleyin.
 
> [!NOTE]
> - **Eklenen cihazlar için Sistem Durumu** ilkesi salt okunur özellikleri kullanır ve düzeltilemiyor.

## <a name="offboard-and-monitor-devices-using-mobile-device-management-tools"></a>Mobil Cihaz Yönetimi araçlarını kullanarak cihazları çıkarma ve izleme

Güvenlik nedeniyle, cihazları kullanıma almak için kullanılan paketin süresi, indirildiği tarihten 30 gün sonra dolar. Bir cihaza gönderilen süresi dolan çıkarma paketleri reddedilir. Bir çıkarma paketini indirirken paketlerin son kullanma tarihi size bildirilir ve paket adına da eklenir.

> [!NOTE]
> Ekleme ve çıkarma ilkeleri aynı cihazda aynı anda dağıtılmamalıdır, aksi takdirde bu öngörülemeyen çakışmalara neden olur.

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalı'dan</a> çıkarma paketini alın.

2. Gezinti bölmesinde **Ayarlar** > **Cihaz ekleme** > **Çıkarma'yı** seçin.

3. **Dağıtım yöntemi** alanında **Mobil Cihaz Yönetimi / Microsoft Intune'ı** seçin.

4. **Paketi indir'e** tıklayın ve .zip dosyasını kaydedin.

5. .zip dosyasının içeriğini, paketi dağıtacak ağ yöneticileri tarafından erişilebilen paylaşılan, salt okunur bir konuma ayıklayın. *DeviceCompliance_valid_until_YYYY-MM-DD.offboarding* adlı bir dosyanız olmalıdır.

6. Aşağıdaki desteklenen OMA-URI ayarlarını dağıtmak için Microsoft Intune özel yapılandırma ilkesini kullanın.

    ```text
    OMA-URI: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
    Date type: String
    Value: [Copy and paste the value from the content of the DeviceCompliance_valid_until_YYYY-MM-DD.offboarding file]
    ```
> [!NOTE]
> Uç Nokta için Microsoft Defender zaten yapılandırılmışsa **cihaz eklemeyi açabilirsiniz** ve 6. Adım artık gerekli değildir.

> [!NOTE]
> **Kullanıma alınan cihazlar için Sistem Durumu** ilkesi salt okunur özellikleri kullanır ve düzeltilemiyor.

> [!IMPORTANT]
> Kullanıma alma, cihazın portala algılayıcı verileri göndermeyi durdurmasına neden olur, ancak sahip olduğu uyarılara başvuru da dahil olmak üzere cihazdaki veriler 6 aya kadar saklanır.

## <a name="related-topics"></a>İlgili konular
- [grup ilkesi kullanarak Windows 10 cihazları ekleme](device-onboarding-gp.md)
- [Microsoft Endpoint Configuration Manager kullanarak Windows 10 cihazları ekleme](device-onboarding-sccm.md)
- [Yerel betik kullanarak Windows 10 cihazları ekleme](device-onboarding-script.md)
- [Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarının katılımı](device-onboarding-vdi.md)
- [Microsoft Defender Gelişmiş Tehdit Koruması ekleme sorunlarını giderme](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
