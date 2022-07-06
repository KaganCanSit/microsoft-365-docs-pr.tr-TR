---
title: Grup Politikası aracılığıyla Windows 10 ve Windows 11 cihazlarının katılımı
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
description: yapılandırma paketini Windows 10 ve Windows 11 cihazlara dağıtmak için grup ilkesi kullanın; böylece hizmete eklenirler.
ms.openlocfilehash: 6c8c70d1bfdf3de0bc3848069a22b8610d445e42
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623263"
---
# <a name="onboard-windows-10-devices-and-windows-11-using-group-policy"></a>grup ilkesi kullanarak Windows 10 cihazları ve Windows 11 ekleme 

**Şunlar için geçerlidir:**

- [Uç nokta veri kaybı önleme (DLP)](./endpoint-dlp-learn-about.md)
- [İçeriden risk yönetimi](insider-risk-management.md)
- Grup İlkesi

> [!NOTE]
> Paketi dağıtmak için grup ilkesi (GP) güncelleştirmelerini kullanmak için Windows Server 2008 R2 veya sonraki bir sürümde olmanız gerekir.

> Windows Server 2019 için, grup ilkesi tercihinin oluşturduğu XML dosyasının NT AUTHORITY\Well-Known-System-Account yerine NT AUTHORITY\SYSTEM kullanmanız gerekebilir.

## <a name="onboard-devices-using-group-policy"></a>grup ilkesi kullanarak cihazları ekleme

1. [Uyumluluk merkezini](https://compliance.microsoft.com) açın.

2. Gezinti bölmesinde **Ayarlar** > **Cihaz Ekleme'yi** seçin.

3. **Dağıtım yöntemi** alanında **Grup ilkesi'ni** seçin.

4. **Paketi indir'e** tıklayın ve .zip dosyasını kaydedin.

5. .zip dosyasının içeriğini, cihaz tarafından erişilebilen paylaşılan, salt okunur bir konuma ayıklayın. *OptionalParamsPolicy* adlı bir klasörünüz ve *DeviceComplianceLocalOnboardingScript.cmd* dosyası olmalıdır.

6. [grup ilkesi Yönetim Konsolu'nu](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine (GPO) sağ tıklayın ve **Düzenle'ye** tıklayın.

7. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na**, **Tercihler'e** ve ardından **Denetim masası ayarları'na** gidin.

8. **Zamanlanmış görevler'e** sağ tıklayın, **Yeni'nin** üzerine gelin ve **ardından Anında Görev 'e (En az Windows 7)** tıklayın.

9. Açılan **Görev** penceresinde **Genel** sekmesine gidin. **Güvenlik seçenekleri'nin** altında **Kullanıcıyı veya Grubu Değiştir'e** tıklayın ve SİSTEM yazın ve ardından **Adları Denetle'ye** ve ardından **Tamam'a** tıklayın. NT AUTHORITY\SYSTEM, görevin çalıştırılacağı kullanıcı hesabı olarak görünür.

10. **Kullanıcının oturum açıp açmadığını çalıştır'ı** seçin ve **En yüksek ayrıcalıklarla çalıştır** onay kutusunu işaretleyin.

11. **Eylemler** sekmesine gidin ve **Yeni...** öğesine tıklayın. **Eylem** alanında **Program başlat'ın** seçili olduğundan emin olun. Paylaşılan *WindowsDefenderATPOnboardingScript.cmd* dosyasının dosya adını ve konumunu girin.

12. **Tamam'a** tıklayın ve açık GPMC pencerelerini kapatın.

## <a name="offboard-devices-using-group-policy"></a>grup ilkesi kullanarak cihazları çıkarma
Güvenlik nedeniyle, cihazları kullanıma almak için kullanılan paketin süresi, indirildiği tarihten 30 gün sonra dolar. Bir cihaza gönderilen süresi dolan çıkarma paketleri reddedilir. Bir çıkarma paketini indirirken paketlerin son kullanma tarihi size bildirilir ve paket adına da eklenir.

> [!NOTE]
> Ekleme ve çıkarma ilkeleri aynı cihazda aynı anda dağıtılmamalıdır, aksi takdirde bu öngörülemeyen çakışmalara neden olur.

1. [Microsoft Purview uyumluluk portalı'dan](https://compliance.microsoft.com/compliancesettings/deviceonboarding) çıkarma paketini alın.

2. Gezinti bölmesinde **Ayarlar** > **//Cihaz ekleme** >  Çıkarma'yı **seçin.**

3. **Dağıtım yöntemi** alanında **Grup ilkesi'ni** seçin.

4. **Paketi indir'e** tıklayın ve .zip dosyasını kaydedin.

5. .zip dosyasının içeriğini, cihaz tarafından erişilebilen paylaşılan, salt okunur bir konuma ayıklayın. *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd* adlı bir dosyanız olmalıdır.

6. [grup ilkesi Yönetim Konsolu'nu](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine (GPO) sağ tıklayın ve **Düzenle'ye** tıklayın.

7. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na,** **Tercihler'e** ve ardından **Denetim masası ayarları'na** gidin.

8. **Zamanlanmış görevler'e** sağ tıklayın, **Yeni'nin** üzerine gelin ve **hemen görev'e** tıklayın.

9. Açılan **Görev** penceresinde **Genel** sekmesine gidin. **Güvenlik seçenekleri'nin** altında yerel SYSTEM kullanıcı hesabını (BUILTIN\SYSTEM) seçin.

10. **Kullanıcının oturum açıp açmadığını çalıştır'ı** seçin ve **En yüksek ayrıcalıklarla çalıştır** onay kutusunu işaretleyin.

11. **Eylemler** sekmesine gidin ve **Yeni...** öğesine tıklayın. **Eylem** alanında **Program başlat'ın** seçili olduğundan emin olun. Paylaşılan  *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd* dosyasının dosya adını ve konumunu girin.

12. **Tamam'a** tıklayın ve açık GPMC pencerelerini kapatın.

> [!IMPORTANT]
> Çıkarma, cihazın portala algılayıcı verileri göndermeyi durdurmasına, ancak cihazdan veri göndermesine neden olur.


## <a name="monitor-device-configuration"></a>Cihaz yapılandırmasını izleme
grup ilkesi ile cihazlarda ilkelerin dağıtımını izleme seçeneği yoktur. İzleme doğrudan portalda veya farklı dağıtım araçları kullanılarak yapılabilir.

## <a name="monitor-devices-using-the-portal"></a>Portalı kullanarak cihazları izleme
1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalı</a> gidin.
2. **Cihazlar** listesi'ne tıklayın.
3. Cihazların görüntülendiğini doğrulayın.

> [!NOTE]
> Cihazların **Cihazlar listesinde** gösterilmeye başlaması birkaç gün sürebilir. Bu, ilkelerin cihaza dağıtılması için gereken süreyi, kullanıcının oturum açacağı süreyi ve uç noktanın raporlamaya başlaması için geçen süreyi içerir.


## <a name="related-topics"></a>İlgili konular
- [Microsoft Endpoint Configuration Manager kullanarak Windows 10 ve Windows 11 cihazları ekleme](device-onboarding-sccm.md)
- [Mobil Cihaz Yönetimi araçlarını kullanan Windows 10 ve Windows 11 cihazlarının katılımı](device-onboarding-mdm.md)
- [Yerel bir komut dosyası kullanan Windows 10 ve Windows 11 cihazlarının katılımı](device-onboarding-script.md)
- [Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarının katılımı](device-onboarding-vdi.md)
- [Yeni eklenen Uç Nokta için Microsoft Defender cihazlarda algılama testi çalıştırma](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Microsoft Defender Gelişmiş Tehdit Koruması ekleme sorunlarını giderme](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
