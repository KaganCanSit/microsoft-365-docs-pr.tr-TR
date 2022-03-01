---
title: Grup Windows 10 ile Windows 11 cihazı ekleme
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
description: Yapılandırma paketini hizmete dahil etmek üzere Windows 10 ve Windows 11 cihaz üzerinde dağıtmak için Grup İlkesi kullanın.
ms.openlocfilehash: fbba73fcf15ee9f71c4caacc57155a64e6cb9e9c
ms.sourcegitcommit: 8eca41cd21280ffcb1f50cafce7a934e5544f302
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2021
ms.locfileid: "62999577"
---
# <a name="onboard-windows-10-devices-and-windows-11-using-group-policy"></a>Grup Windows 10 kullanarak cihaz Windows 11'i ekleme 

**Aşağıdakiler için geçerlidir:**

- [Microsoft 365 Uç nokta veri kaybı önleme (DLP)](./endpoint-dlp-learn-about.md)
- [Insider risk yönetimi](insider-risk-management.md#learn-about-insider-risk-management-in-microsoft-365)
- Grup İlkesi

> [!NOTE]
> Paketin dağıtımında Grup İlkesi (GP) güncelleştirmelerini kullanmak için, Windows Server 2008 R2 veya sonraki bir işletim sistemi kullanıyor olun.

> Windows Server 2019'da, Grup İlkesi tercihlerinin oluşturduğu XML dosyasının NT AUTHORITY\SYSTEM ile NT AUTHORITY\Well-Known-System-Account değiştirmeniz gerekir.

## <a name="onboard-devices-using-group-policy"></a>Grup İlkesi kullanarak cihazları ekleme

1. Uyumluluk [merkezini açın](https://compliance.microsoft.com).

2. Gezinti bölmesinde, **Diğer'Ayarlar** >  **Ekleme'yi seçin**.

3. Dağıtım yöntemi **alanında** Grup **ilkesi'ne seçin**.

4. Paketi **indir'e** tıklayın ve .zip kaydedin.

5. .zip dosyasının içeriğini cihaz tarafından erişilebilen, salt okunur bir konuma ayıklar. *optionalParamsPolicy* adlı bir klasörünüz ve *DeviceComplianceLocalOnboardingScript.cmd dosyasının olması gerekir*.

6. Grup İlkesi [Yönetim Konsolu'nu](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine (GPO) sağ tıklayın ve Düzenle'ye **tıklayın**.

7. Grup İlkesi **Yönetim Düzenleyicisi'nde** Bilgisayar **yapılandırması'nı, Tercihler'i** ve denetim masası **ayarları'nı seçin**.

8. Zamanlanmış **görevler'e sağ tıklayın**, **Yeni'nin** üzerine gelin ve Anlık Görev **(En az 7 Windows) tıklayın**.

9. Açılan **Görev** penceresinde Genel **sekmesine** gidin. Güvenlik **seçenekleri'nin** altında **Kullanıcı veya Grubu Değiştir'e** tıklayın, SİSS SISTEMI yazın ve Adları **Denetleme'ye ve Tamam'a** **tıklayın**. NT AUTHORITY\SYSTEM, görevin çalıştıracak olduğu kullanıcı hesabı olarak görünür.

10. Kullanıcının **oturum açmış olup olmadığını çalıştır'ı seçin ve** En yüksek **ayrıcalıklarla çalıştır onay** kutusunu işaretleyin.

11. Eylemler sekmesine **gidin** ve Yeni **... öğesini tıklatın.** Eylem alanında **Program başlat'ın** seçili olduğundan **emin** olun. Paylaşılan *WindowsDefenderATPOnboardingScript.cmd dosyasının dosya adını ve konumunu* girin.

12. **Tamam'a** tıklayın ve tüm açık GPMC pencerelerini kapatın.

## <a name="offboard-devices-using-group-policy"></a>Grup İlkesi kullanan offboard cihazları
Güvenlik nedeniyle, cihazlara kullanılan paket, indirildikten 30 gün sonra sona erer. Bir cihaza gönderilen süresi dolmuş offboard paketleri reddedilir. Bir çıkartan kullanım paketi indirirken paketlerin son kullanma tarihi size bildirilecek ve paket adına da bu paket dahil edilecektir.

> [!NOTE]
> Ekleme ve çıkarma ilkeleri aynı cihazda aynı anda dağıtıldığından, öngörülemeyen zararlara neden olur.

1. Microsoft Uyumluluk Merkezi'nden çıkartan [pakete bakın](https://compliance.microsoft.com/compliancesettings/deviceonboarding).

2. Gezinti bölmesinde Seçenekler **/Ayarlar** > **/Cihaz** **eklemeOffboarding** >  öğesini seçin.

3. Dağıtım yöntemi **alanında** Grup **ilkesi'ne seçin**.

4. Paketi **indir'e** tıklayın ve .zip kaydedin.

5. .zip dosyasının içeriğini cihaz tarafından erişilebilen, salt okunur bir konuma ayıklar. *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd adlı bir dosyanız olmalıdır*.

6. Grup İlkesi [Yönetim Konsolu'nu](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC) açın, yapılandırmak istediğiniz Grup İlkesi Nesnesine (GPO) sağ tıklayın ve Düzenle'ye **tıklayın**.

7. Grup İlkesi **Yönetim Düzenleyicisi'nde** Bilgisayar **yapılandırması'nı, Tercihler'i** ve denetim masası **ayarları'nı seçin**.

8. Zamanlanmış **görevler'e sağ tıklayın**, **Yeni'nin üzerine gelin** ve Anlık **görev'e tıklayın**.

9. Açılan **Görev** penceresinde Genel **sekmesine** gidin. Güvenlik seçenekleri'nin altında yerel SYSTEM kullanıcı hesabını (BUILTIN\SYSTEM) **seçin**.

10. Kullanıcının **oturum açmış olup olmadığını çalıştır'ı seçin ve** En yüksek **ayrıcalıklarla çalıştır onay** kutusunu işaretleyin.

11. Eylemler sekmesine **gidin** ve Yeni... **öğesini tıklatın**. Eylem alanında **Program başlat'ın** seçili olduğundan **emin** olun. Paylaşılan dosyanın adını ve konumunu  *DeviceComplianceOffboardingScript_valid_until_YYYY-MM-DD.cmd dosyasını* girin.

12. **Tamam'a** tıklayın ve tüm açık GPMC pencerelerini kapatın.

> [!IMPORTANT]
> Offboard, cihazın algılayıcı verilerini portala ancak cihazdan verilerin gönderilmesini durdurmaya neden olur.


## <a name="monitor-device-configuration"></a>Cihaz yapılandırmasını izleme
Grup İlkesiyle, ilkelerin cihazlara dağıtımını izleme seçeneği yok. İzleme doğrudan portalda veya farklı dağıtım araçları kullanılarak yapılabilir.

## <a name="monitor-devices-using-the-portal"></a>Portalı kullanarak cihazları izleme
1. Diğer <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi.</a>
2. Cihazlar **listesi'ne** tıklayın.
3. Cihazların görüntüde olduğunu doğrulayın.

> [!NOTE]
> Cihazların Cihazlar listesinde göstermeye başlaması birkaç gün **kadar zaman alıyor**. İlkelerin cihaza dağıtılması için gereken süre, kullanıcı oturum amadan önce geçen süre ve uç noktanın raporlamaya başlaması için geçen süre de buna dahildir.


## <a name="related-topics"></a>İlgili konular
- [Microsoft Endpoint Configuration Manager kullanarak Windows 10 cihaz ve 11 Windows cihaz Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Mobil Windows 10 araçları Windows 11 cihaza ekleme ve kullanma](device-onboarding-mdm.md)
- [Yerel bir Windows 10 kullanarak Windows 10 ve 11 Windows cihaz kullanın](device-onboarding-script.md)
- [Kalıcı olmayan sanal masaüstü altyapısı (VDI) cihazlarını ekleme](device-onboarding-vdi.md)
- [Yeni eklenen Uç nokta cihazları için Microsoft Defender'da bir algılama testi çalıştırın](/windows/security/threat-protection/microsoft-defender-atp/run-detection-test)
- [Microsoft Defender Gelişmiş Tehdit Koruması'nın ekleme sorunlarını giderme](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)