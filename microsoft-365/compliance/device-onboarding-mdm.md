---
title: Mobil Windows 10 araçları Windows 11 cihaza ekleme ve kullanma
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
description: Yapılandırma paketini hizmete dahil etmek üzere cihazlara dağıtmak için Mobil Cihaz Yönetimi araçlarını kullanın.
ms.openlocfilehash: 578a1e06bf5f83f700c5db69ddc32a480d68b729
ms.sourcegitcommit: 726a72f135358603c2fde3f4067d834536e6deb2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2022
ms.locfileid: "63014310"
---
# <a name="onboard-windows-10-and-windows-11-devices-using-mobile-device-management-tools"></a>Mobil Windows 10 araçları Windows 11 cihaza ekleme ve kullanma

**Aşağıdakiler için geçerlidir:**

- [Microsoft 365 Uç nokta veri kaybı önleme (DLP)](./endpoint-dlp-learn-about.md)
- [Insider risk yönetimi](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)

Cihazları yapılandırmak için mobil cihaz yönetimi (MDM) çözümlerini kullanabilirsiniz. Microsoft 365 koruması, cihazları yönetmek için ilkeler oluşturmak için OMA-URIs bilgi sağlayarak MDM'leri destekler.


## <a name="before-you-begin"></a>Başlamadan önce
MDM Kaydını Microsoft Intune cihazında olması gerekir. Aksi takdirde, ayarlar başarıyla uygulanmaz. 

MDM'nin birden çok cihazda etkinleştirilmesi hakkında daha fazla Microsoft Intune için bkz[. Cihaz kaydı (Microsoft Intune).](/mem/intune/enrollment/device-enrollment).

## <a name="onboard-devices-using-microsoft-intune"></a>Microsoft Intune kullanarak cihazları Microsoft Intune

[Intune'daki yönergeleri izleyin](/intune/advanced-threat-protection).

> [!NOTE]
> - **Onboarded cihazlar için Durum** ilkesi salt okunur özellikleri kullanır ve düzelti değildir.

## <a name="offboard-and-monitor-devices-using-mobile-device-management-tools"></a>Mobil Cihaz Yönetimi araçlarını kullanarak offboard ve monitör cihazları

Güvenlik nedeniyle, Offboard cihazları için kullanılan paketin süresi, indirildikten 30 gün sonra sona erer. Bir cihaza gönderilen süresi dolmuş offboard paketleri reddedilir. Bir çıkartan kullanım paketi indirirken paketlerin son kullanma tarihi size bildirilecek ve paket adına da bu paket dahil edilecektir.

> [!NOTE]
> Ekleme ve çıkarma ilkeleri aynı cihazda aynı anda dağıtıldığından, öngörülemeyen zararlara neden olur.

1. Hazır gelen offboard paketini <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a>.

2. Gezinti **bölmesinde,Device onboardingOffboarding** >  **Ayarlar'ı** >  seçin.

3. Dağıtım yöntemi **alanında**, Mobil Cihaz Yönetimi **/ Mobil Cihaz Yönetimi'ne Microsoft Intune**.

4. Paketi **indir'e** tıklayın ve dosyayı .zip kaydedin.

5. .zip dosyasının içeriğini, paketi dağıtacak olan ağ yöneticileri tarafından erişilebilen, paylaşılan, salt okunur bir konuma ayıklar. *DeviceCompliance_valid_until_YYYY-MM-DD.offboarding adlı bir dosyanız olmalıdır*.

6. Desteklenen Microsoft Intune OMA-URI ayarlarını dağıtmak için aşağıdaki özel yapılandırma ilkesine tıklayın.

    ```text
    OMA-URI: ./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding
    Date type: String
    Value: [Copy and paste the value from the content of the DeviceCompliance_valid_until_YYYY-MM-DD.offboarding file]
    ```
> [!NOTE]
> Uç Nokta için Microsoft Defender zaten yapılandırılmışsa cihaz eklemeyi açabilirsiniz **ve** 6. Adım artık gerekli değildir.

> [!NOTE]
> Kapalı **durumdaki cihazlar için Durum** ilkesi salt okunur özellikleri kullanır ve düzelti değildir.

> [!IMPORTANT]
> Offboard, cihazın algılayıcı verilerini portala göndermeyi durdurmaya neden olur, ancak sahip olduğu uyarılara başvuru da dahil olmak üzere cihazdan alınan veriler 6 ay süreyle korunur.

## <a name="related-topics"></a>İlgili konular
- [Grup Windows 10 kullanarak cihaz ekleme](device-onboarding-gp.md)
- [Microsoft Endpoint Configuration Manager kullanarak Windows 10 cihazları Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Yerel Windows 10 kullanarak cihazları ekleme](device-onboarding-script.md)
- [Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarını ekleme](device-onboarding-vdi.md)
- [Microsoft Defender Gelişmiş Tehdit Koruması'nın ekleme sorunlarını giderme](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
