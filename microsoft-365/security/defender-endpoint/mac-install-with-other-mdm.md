---
title: Mac'te Uç Nokta için Microsoft Defender için farklı bir Mobil Cihaz Yönetimi (MDM) sistemiyle dağıtım
description: Diğer yönetim çözümlerine Mac'te Uç Nokta için Microsoft Defender'ı yükleyin.
keywords: microsoft, defender, Endpoint için Microsoft Defender, mac, yükleme, deploy, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: c8ffab850302967b9e36e841bf035cef07ad2775
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63012013"
---
# <a name="deployment-with-a-different-mobile-device-management-mdm-system-for-microsoft-defender-for-endpoint-on-macos"></a>macOS'ta Uç Nokta için Microsoft Defender için farklı bir Mobil Cihaz Yönetimi (MDM) sistemiyle dağıtım

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)
 
## <a name="prerequisites-and-system-requirements"></a>Önkoşullar ve sistem gereksinimleri

Başlamadan önce, geçerli yazılım sürümünün önkoşullarının ve sistem gereksinimlerinin açıklaması için [macOS'ta](microsoft-defender-endpoint-mac.md) uç nokta için ana Microsoft Defender sayfasına bakın.


## <a name="approach"></a>Yaklaşım

> [!CAUTION]

> Microsoft şu anda macOS üzerinde Uç Nokta için Microsoft Defender dağıtımı ve yönetimi için yalnızca Intune ve JAMF'yi resmi olarak destekliyor. Microsoft, aşağıda verilen bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Kuruluş resmi olarak desteklemeyen bir Mobil Cihaz Yönetimi (MDM) çözümü kullanıyorsa, bu macOS üzerinde Uç Nokta için Microsoft Defender'ı dağıtamadığınız veya çalıştıramadığınız anlamına değildir.

macOS üzerinde Uç Nokta için Microsoft Defender satıcıya özgü özelliklere bağımlı değildir. Aşağıdaki özellikleri destekleyen tüm MDM çözümleriyle kullanılabilir:

- Yönetilen cihazlara macOS .pkg dağıtın.
- MacOS sistem yapılandırma profillerini yönetilen cihazlara dağıtın.
- Yönetilen cihazlarda rastgele yönetici tarafından yapılandırılan bir araç/betik çalıştırın.

Modern MDM çözümlerinin çoğu bu özellikleri içerir, ancak bunlar farklı çağrılar da içerebilir.

Öte yandan, yukarıdaki listede son gereksinim olmadan Uç Nokta için Defender'ı dağıtabilirsiniz:

- Durumu merkezi bir şekilde toplayabilirsiniz.
- Uç nokta için Defender'ı kaldırmaya karar verdiyseniz, istemci cihazında yönetici olarak yerel olarak oturum açabilirsiniz.

## <a name="deployment"></a>Dağıtım

MDM çözümlerinin çoğu, macOS cihazlarını yönetmek için aynı modeli, benzer terminolojiyle kullanır. [JAMF tabanlı dağıtımı şablon](mac-install-with-jamf.md) olarak kullanın.

### <a name="package"></a>Paket

Gerekli uygulama [paketinin dağıtımını, portaldan](mac-install-with-jamf.md) indirilen yükleme paketiyle (wdav.pkg) [Microsoft 365 Defender yapılandırabilirsiniz](mac-install-with-jamf.md).

Paketi kuruma dağıtmak için MDM çözümünüzle ilişkili yönergeleri kullanın.

### <a name="license-settings"></a>Lisans ayarları

Bir [sistem yapılandırma profili ayarlayın](mac-install-with-jamf.md). 

mdm çözümünüz, macOS'ta Uç Nokta için Microsoft Defender'ın macOS'un bir parçası Ayarlar Profili" gibi bir adı olabilir.

Microsoft 365 Defender portaldan indirilen ekleme paketinden ayıklandırilebilen özellik listesini (jamf/WindowsDefenderATPOnboarding.plist[) kullanın](mac-install-with-jamf.md).
Sisteminiz XML biçiminde rastgele özellik listesini desteklemektedir. Bu durumda, jamf/WindowsDefenderATPOnboarding.plist dosyasını olduğu gibi karşıya yükleyebilirsiniz.
Alternatif olarak, öncelikle özellik listesini farklı bir biçime dönüştürmeyi gerektirebilirsiniz.

Normalde, özel profilinizde kimlik, ad veya etki alanı özniteliği olur. Bu değer için tam olarak "com.microsoft.wdav.atp" kullanabilirsiniz.
MDM, ayarlar dosyasını istemci cihazda **/Library/Managed Preferences/com.microsoft.wdav.atp.plist'e** dağıtmak için bu dosyayı kullanır ve Uç Nokta için Defender ekleme bilgilerini yüklerken bu dosyayı kullanır.

### <a name="kernel-extension-policy"></a>Kernel extension policy

KEXT veya çekirdek uzantı ilkesi ayarlama. Microsoft tarafından sağlanan çekirdek **uzantılarına izin vermek için ekip tanımlayıcısını UBF8T346G9** kullanın.

> [!CAUTION]
> Ortamınız Apple Silicon (M1) cihazlardan oluşursa, bu makinelerde KEXT ilkeleriyle yapılandırma profilleri almamalıdır.
> Apple bu makinelerde KEXT'i desteklemez, bu profilin dağıtımı M1 makinesinde başarısız olur.

### <a name="system-extension-policy"></a>Sistem uzantısı ilkesi

Sistem uzantısı ilkesi ayarlama. Ekip tanımlayıcı **UBF8T346G9** kullanın ve aşağıdaki paket tanımlayıcılarını onaylar:

- com.microsoft.wdav.epsext
- com.microsoft.wdav.netext

### <a name="full-disk-access-policy"></a>Tam disk erişimi ilkesi

Aşağıdaki bileşenlere Tam Disk Erişimi ver:

- Uç Nokta için Microsoft Defender
    - Tanımlayıcı: `com.microsoft.wdav`
    - Tanımlayıcı Türü: Paket Kimliği
    - Kod Gereksinimi: `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

- Uç Nokta Güvenlik Uzantısı için Microsoft Defender
    - Tanımlayıcı: `com.microsoft.wdav.epsext`
    - Tanımlayıcı Türü: Paket Kimliği
    - Kod Gereksinimi: `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

### <a name="network-extension-policy"></a>Ağ uzantısı ilkesi

Uç Nokta Algılama ve Yanıt özellikleri kapsamında, macOS'ta Uç Nokta için Microsoft Defender yuva trafiğini inceler ve bu bilgileri Microsoft 365 Defender raporlar. Aşağıdaki ilke, ağ uzantısının bu işlevi gerçekleştirmesi için izin verir.

- Filtre türü: Eklenti
- Eklenti paketi tanımlayıcısı: `com.microsoft.wdav`
- Veri sağlayıcısı paket tanımlayıcısını filtreleme: `com.microsoft.wdav.netext`
- Veri sağlayıcısına filtre uygulama gereksinimi belirlenmiştir: `identifier "com.microsoft.wdav.tunnelext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
- Filtre yuvaları: `true`

## <a name="check-installation-status"></a>Yükleme durumunu denetleme

Ekleme [durumunu kontrol etmek için](mac-install-with-jamf.md) istemci cihazda Uç Nokta için Microsoft Defender'ı çalıştırın.
