---
title: Mac'te Uç Nokta için Microsoft Defender için farklı bir Mobil Cihaz Yönetimi (MDM) sistemiyle dağıtım
description: Mac'e diğer yönetim çözümlerine Uç Nokta için Microsoft Defender yükleyin.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mac, installation, deploy, macos, catalina, mojave, high sierra
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: mavel
author: maximvelichko
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 2fa64ee9822fe1f784788e2d1ead79e66eb200ef
ms.sourcegitcommit: 2d870e06e87b10d9e8ec7a7a8381353bc3bc59c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65349748"
---
# <a name="deployment-with-a-different-mobile-device-management-mdm-system-for-microsoft-defender-for-endpoint-on-macos"></a>macOS'da Uç Nokta için Microsoft Defender için farklı bir Mobil Cihaz Yönetimi (MDM) sistemiyle dağıtım

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimlemek mi istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)
 
## <a name="prerequisites-and-system-requirements"></a>Önkoşullar ve sistem gereksinimleri

Başlamadan önce, geçerli yazılım sürümü için önkoşulların ve sistem gereksinimlerinin açıklaması için [macOS sayfasındaki ana Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md) bakın.


## <a name="approach"></a>Yaklaşım

> [!CAUTION]

> Şu anda Microsoft, macOS üzerinde Uç Nokta için Microsoft Defender dağıtımı ve yönetimi için yalnızca Intune ve JAMF'yi resmi olarak desteklemektedir. Microsoft, aşağıda verilen bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Kuruluşunuz resmi olarak desteklenmeyen bir Mobil Cihaz Yönetimi (MDM) çözümü kullanıyorsa bu, macOS Uç Nokta için Microsoft Defender dağıtamadığınız veya çalıştıramadığınız anlamına gelmez.

macOS Uç Nokta için Microsoft Defender satıcıya özgü özelliklere bağlı değildir. Aşağıdaki özellikleri destekleyen herhangi bir MDM çözümüyle kullanılabilir:

- Yönetilen cihazlara bir macOS .pkg dağıtın.
- Yönetilen cihazlara macOS sistem yapılandırma profilleri dağıtın.
- Yönetilen cihazlarda rastgele yönetici tarafından yapılandırılmış bir araç/betik çalıştırın.

Modern MDM çözümlerinin çoğu bu özellikleri içerir, ancak bunları farklı şekilde adlandırabilirler.

Ancak, uç nokta için Defender'ı önceki listeden son gereksinim olmadan dağıtabilirsiniz:

- Durumu merkezi bir şekilde toplayamazsınız.
- Uç Nokta için Defender'ı kaldırmaya karar verirseniz istemci cihazında yönetici olarak yerel olarak oturum açmanız gerekir.

## <a name="deployment"></a>Dağıtım

Çoğu MDM çözümü, benzer terminolojiye sahip macOS cihazları yönetmek için aynı modeli kullanır. [ŞABLON olarak JAMF tabanlı dağıtımı](mac-install-with-jamf.md) kullanın.

### <a name="package"></a>Paket

Yükleme paketi (wdav.pkg) [Microsoft 365 Defender portalından](mac-install-with-jamf.md) indirilmiş [olarak gerekli bir uygulama](mac-install-with-jamf.md) paketinin dağıtımını yapılandırın.

Paketi kuruluşunuza dağıtmak için MDM çözümünüzle ilişkili yönergeleri kullanın.

### <a name="license-settings"></a>Lisans ayarları

[Bir sistem yapılandırma profili](mac-install-with-jamf.md) ayarlayın. 

MDM çözümünüz buna "Özel Ayarlar Profili" gibi bir ad verebilir; macOS Uç Nokta için Microsoft Defender macOS parçası değildir.

[Microsoft 365 Defender portalından](mac-install-with-jamf.md) indirilen bir ekleme paketinden ayıklanabilen jamf/WindowsDefenderATPOnboarding.plist özellik listesini kullanın.
Sisteminiz XML biçiminde rastgele bir özellik listesini destekleyemeyebilir. Bu durumda jamf/WindowsDefenderATPOnboarding.plist dosyasını olduğu gibi karşıya yükleyebilirsiniz.
Alternatif olarak, önce özellik listesini farklı bir biçime dönüştürmeniz gerekebilir.

Genellikle özel profilinizin kimliği, adı veya etki alanı özniteliği vardır. Bu değer için tam olarak "com.microsoft.wdav.atp" kullanmanız gerekir.
MDM, ayarlar dosyasını bir istemci cihazında **/Library/Managed Preferences/com.microsoft.wdav.atp.plist** dosyasına dağıtmak için kullanır ve Uç Nokta için Defender da ekleme bilgilerini yüklemek için bu dosyayı kullanır.

### <a name="kernel-extension-policy"></a>Çekirdek uzantısı ilkesi

KEXT veya çekirdek uzantısı ilkesi ayarlayın. Microsoft tarafından sağlanan çekirdek uzantılarına izin vermek için **UBF8T346G9** ekip tanımlayıcısını kullanın.

> [!CAUTION]
> Ortamınız Apple Silicon (M1) cihazlarından oluşuyorsa, bu makineler KEXT ilkelerine sahip yapılandırma profillerini almamalıdır.
> Apple bu makinelerde KEXT'yi desteklemez, bu tür bir profilin dağıtımı M1 makinelerinde başarısız olur.

### <a name="system-extension-policy"></a>Sistem uzantısı ilkesi

Bir sistem uzantısı ilkesi ayarlayın. **UBF8T346G9** takım tanımlayıcısını kullanın ve aşağıdaki paket tanımlayıcılarını onaylayın:

- com.microsoft.wdav.epsext
- com.microsoft.wdav.netext

### <a name="full-disk-access-policy"></a>Tam disk erişim ilkesi

Aşağıdaki bileşenlere Tam Disk Erişimi verin:

- Uç Nokta için Microsoft Defender
    - Tanımlayıcı: `com.microsoft.wdav`
    - Tanımlayıcı Türü: Paket Kimliği
    - Kod Gereksinimi: `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

- Uç Nokta için Microsoft Defender Güvenlik Uzantısı
    - Tanımlayıcı: `com.microsoft.wdav.epsext`
    - Tanımlayıcı Türü: Paket Kimliği
    - Kod Gereksinimi: `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

### <a name="network-extension-policy"></a>Ağ uzantısı ilkesi

Uç Nokta Algılama ve Yanıt özelliklerinin bir parçası olarak macOS'da Uç Nokta için Microsoft Defender yuva trafiğini inceler ve bu bilgileri Microsoft 365 Defender portalına bildirir. Aşağıdaki ilke, ağ uzantısının bu işlevi gerçekleştirmesine izin verir.

- Filtre türü: Eklenti
- Eklenti paketi tanımlayıcısı: `com.microsoft.wdav`
- Filtre veri sağlayıcısı paket tanımlayıcısı: `com.microsoft.wdav.netext`
- Filtre veri sağlayıcısı belirlenmiş gereksinimi: `identifier "com.microsoft.wdav.netext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
- Filtre yuvaları: `true`

## <a name="check-installation-status"></a>Yükleme durumunu denetleme

Ekleme durumunu denetlemek için bir istemci cihazında [Uç Nokta için Microsoft Defender](mac-install-with-jamf.md) çalıştırın.
