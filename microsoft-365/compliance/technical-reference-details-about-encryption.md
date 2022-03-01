---
title: Şifreleme hakkında teknik başvuru ayrıntıları
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
- Strat_O365_IP
search.appverid:
- MET150
- MOE150
ms.assetid: 862cbe93-4268-4ef9-ba79-277545ecf221
description: Şifreleme için kullanılan çeşitli sertifikalar, teknolojiler ve Aktarım Katmanı Güvenliği (TLS) şifreleme paketleri hakkında bilgi Office 365 şifreleme Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6b5df1f9e983ab2e8add09b50c2dfbd30dc1243e
ms.sourcegitcommit: 2a4dddf7c655b44b17d4fd7f5e1e5d8a6e2b7aef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/06/2021
ms.locfileid: "62996607"
---
# <a name="technical-reference-details-about-encryption"></a>Şifreleme hakkında teknik başvuru ayrıntıları

Şifrelemede kullanılan sertifikalar, teknolojiler ve TLS şifreleme paketleri hakkında bilgi edinmek için bu [makaleye Office 365](encryption.md). Bu makalede planlanan kullanımdan kullanım ayrıntıları da velanmaktadır.
  
- Genel bakış bilgilerini arıyorsanız, bkz. Daha [fazla bilgi için Office 365](encryption.md).
- Kurulum bilgilerini arıyorsanız, bkz. Kurulum bilgileri [için bkz. Office 365 Kurumsal](set-up-encryption.md).
- TTS'nin belirli sürümlerinde desteklenen şifreleme paketleri hakkında bilgi Windows bkz. [TLS/SSL'de Cipher Suite (Schannel SSP)](/windows/desktop/SecAuthN/cipher-suites-in-schannel).

## <a name="microsoft-office-365-certificate-ownership-and-management"></a>Microsoft Office 365 sahiplik ve yönetimi ile ilgili daha fazla bilgi

Sertifika satın alma veya sertifikayı korumanız Office 365. Bunun Office 365, kendi sertifikalarını kullanır.
  
## <a name="current-encryption-standards-and-planned-deprecations"></a>Geçerli şifreleme standartları ve planlanan kullanımdan kullanımdan kullanımdandan

En iyi sınıf şifrelemeyi sağlamak için, Office 365 şifreleme standartlarını düzenli olarak gözden almaktadır. Bazen, eski standartlar güncel değilken ve daha az güvenli olmalarına neden olarak kullanımdandan çıkar çıkar. Bu makalede şu anda desteklenen şifreleme paketleri ve diğer standartlar ve planlanan kullanımdan kullanımdan kullanım ayrıntıları açıklanmaktadır.

## <a name="fips-compliance-for-office-365"></a>FiPS uyumluluğu Office 365

FIPS 140-2 Office 365 kabul edilebilir algoritmaları kullanarak desteklenen tüm şifreleme paketleri. Office 365 FIPS doğrulamalarını Windows (Schannel aracılığıyla). Schannel hakkında bilgi için bkz. [Cipher Suites in TLS/SSL (Schannel SSP)](/windows/desktop/SecAuthN/cipher-suites-in-schannel).
  
## <a name="versions-of-tls-supported-by-office-365"></a>TLS'nin desteklenen sürümleri Office 365

TLS'den önce gelen TLS ve SSL, bilgisayarlar arasındaki bağlantıyı şifrelemek için güvenlik sertifikaları kullanarak ağ üzerinden iletişimi güvenli hale gelen şifreleme protokolleridir. Office 365, TLS sürüm 1.2'yi (TLS 1.2) destekler.

TLS sürüm 1.3 (TLS 1.3) bazı hizmetler tarafından destekler.

> [!IMPORTANT]
> TLS sürümlerinin kullanımdan silindi olduğunu ve daha yeni sürümlerin kullanılabilir olduğu yerde,  kullanımdan kullanım dışı sürümlerinin kullanılması gerektiğini de varsayın. Eski hizmetleriniz TLS 1.0 veya 1.1 gerektirmezse bunları devre dışı bırakabilirsiniz.
  
## <a name="support-for-tls-10-and-11-deprecation"></a>TLS 1.0 ve 1.1'in kullanımdan kullanımdan desteği

Office 365 31 Ekim 2018'de TLS 1.0 ve 1.1'i desteklemeyi durdurdu. Yüksek ve DoD ortamlarında TLS 1.0 ve 1.1 GCC devre dışı bırakmayı tamamladık. 15 Ekim 2020'den itibaren Dünya Çapında ve GCC ortamları için TLS 1.0 ve 1.1'i devre dışı bırakmaya başladık ve önümüzdeki haftalarda ve aylarda devre dışı bırakılmasına devam edeceğiz.

Office 365 ve Microsoft 365 hizmetleriyle güvenli bir bağlantı sağlamak için, tüm istemci sunucu ve tarayıcı sunucu bileşimleri TLS 1.2 ve modern şifreleme paketlerini kullanır. Belirli istemci-sunucu ve tarayıcı-sunucu kombinasyonlarını güncelleştirmeniz gerekebilir. Bu değişikliğin sizi nasıl etkile ilgili olduğu hakkında bilgi için bkz. Yeni Aralık'ta [TLS 1.2'nin zorunlu kullanımına hazırlanma Office 365](https://support.microsoft.com/help/4057306/preparing-for-tls-1-2-in-office-365).
  
## <a name="deprecating-support-for-3des"></a>3DES için desteği kullanımdandan kullanım

31 Ekim 2018'den Office 365, iletişim için 3DES şifreleme paketlerinin kullanımını artık Office 365. Daha açık olarak Office 365, şifreleme paketini TLS_RSA_WITH_3DES_EDE_CBC_SHA desteklemez. Bu şifreleme paketi 28 Şubat 2019'dan itibaren aynı Office 365. Bu ağ ile iletişim Office 365 istemcilerin ve sunucuların desteklenen şifrelemelerden birini veya birden fazlasını desteklemesi gerekir. Desteklenen şifrelemelerin listesi için bkz. Şifreleme tarafından desteklenen [TLS şifreleme Office 365](#tls-cipher-suites-supported-by-office-365).
  
## <a name="deprecating-sha-1-certificate-support-in-office-365"></a>Office 365'de SHA-1 sertifika desteğini Office 365

Haziran 2016'dan Office 365, giden veya gelen bağlantılar için ARTıK SHA-1 sertifikası kabul etmiyor. Sertifika zincirinde SHA-2 (Güvenli Karma Algoritması 2) veya daha güçlü bir karma algoritması kullanın.
  
## <a name="tls-cipher-suites-supported-by-office-365"></a>TT şifreleme paketleri tarafından desteklenen TLS Office 365

TLS, *güvenli bağlantılar kurmak* için şifreleme algoritması koleksiyonları olan şifreleme paketlerini kullanır. Office 365 tabloda listelenen şifreleme paketlerini destekler. Tabloda şifreleme paketleri, en güçlü şifreleme paketi ilk sırada listelenmiş olarak, güçlü güvenlik sırasına göre listelenmiştir.

Office 365 en güvenli şifreleme paketini kullanarak bağlanmayı denerek bağlantı isteğini yanıtlar. Bağlantı çalışmıyorsa, Office 365 en güvenli şifreleme paketini ve bu şekilde devam etmeye çalışır. Bağlantı kabul edilene kadar hizmet listede devam eder. Benzer şekilde, Office 365 istekte olduğunda, alıcı hizmet TLS'nin kullanılamayacak ve hangi şifreleme paketinin kullanılamayacaklarını seçer.

| Şifreleme paketinin adı | Anahtar değişim algoritması/gücü | İletme gizliliği | Şifreleme/güç | Kimlik doğrulama algoritması/gücü |
|:-----|:-----|:-----|:-----|:-----|
| TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384  <br/> | ECDH/192  <br/> | Evet  <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256  <br/> | ECDH/128  <br/> | Evet  <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384  <br/> | ECDH/192  <br/> | Evet  <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256  <br/> | ECDH/128  <br/> | Evet  <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA     <br/> | ECDH/192  <br/> | Evet  <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA     <br/> | ECDH/128  <br/> | Evet  <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS_RSA_WITH_AES_256_GCM_SHA384        <br/> | RSA/112   <br/> | Hayır   <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS_RSA_WITH_AES_128_GCM_SHA256        <br/> | RSA/112   <br/> | Hayır   <br/> | AES/256  <br/> | RSA/112  <br/> |

Aşağıdaki şifreleme paketleri, kullanımdan kullanımdan kullanım tarihine kadar TLS 1.0 ve 1.1 protokollerini destekliyor. Son GCC kullanımdan alan yüksek ve DoD ortamları için 15 Ocak 2020'dir. Dünya çapında ve GCC ortamlar için ve 15 Ekim 2020'dir.

| Protokoller | Şifreleme paketinin adı | Anahtar değişim algoritması/gücü | İletme gizliliği | Şifreleme/güç | Kimlik doğrulama algoritması/gücü | 
|:-----|:-----|:-----|:-----|:-----|:-----|
| TLS 1.0, 1.1, 1.2  <br/> | TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA  <br/> | ECDH/192  <br/> | Evet  <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS 1.0, 1.1, 1.2  <br/> | TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA  <br/> | ECDH/128  <br/> | Evet  <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS 1.0, 1.1, 1.2  <br/> | TLS_RSA_WITH_AES_256_CBC_SHA        <br/> | RSA/112   <br/> | Hayır   <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS 1.0, 1.1, 1.2  <br/> | TLS_RSA_WITH_AES_128_CBC_SHA        <br/> | RSA/112   <br/> | Hayır   <br/> | AES/128  <br/> | RSA/112  <br/> |
| TLS 1.0, 1.1, 1.2  <br/> | TLS_RSA_WITH_AES_256_CBC_SHA256     <br/> | RSA/112   <br/> | Hayır   <br/> | AES/256  <br/> | RSA/112  <br/> |
| TLS 1.0, 1.1, 1.2  <br/> | TLS_RSA_WITH_AES_128_CBC_SHA256     <br/> | RSA/112   <br/> | Hayır   <br/> | AES/256  <br/> | RSA/112  <br/> |

Bazı Office 365 ürünleri (diğer Microsoft Teams) TLS bağlantılarını sonlandırmak ve ağ trafiğini verimli bir şekilde yönlendirecek [Azure Front Door'yi](/azure/frontdoor/front-door-overview) kullanır. Bu ürünlere başarılı bir şekilde [bağlanmak için TLS 1.2 üzerinden Azure Front Door](/azure/frontdoor/front-door-faq#what-are-the-current-cipher-suites-supported-by-azure-front-door-) tarafından desteklenen şifreleme paketlerinin en az biri etkinleştirilmelidir. Daha Windows 10 için, daha iyi güvenlik için ECDHE şifreleme paketlerinin birini veya her ikisini de etkinleştirmenizi öneririz. Windows 7, 8 ve 8.1 ile Azure Front Door'nın ECDHE şifreleme paketleri uyumlu değildir ve DHE şifreleme paketleri bu işletim sistemleriyle uyumluluk için sağlanmıştır.

## <a name="related-articles"></a>İlgili makaleler

[Windows 10 v1903'te TLS Şifreleme Paketleri](/windows/win32/secauthn/tls-cipher-suites-in-windows-10-v1903)

[Şifreleme Office 365](encryption.md)
  
[Verilerde şifrelemeyi Office 365 Kurumsal](set-up-encryption.md)
  
[Bu güncelleştirmede TLS 1.0'ın Schannel Windows: 24 Kasım 2015](https://support.microsoft.com/kb/3117336)
  
[TLS/SSL Şifreleme Geliştirmeleri (WINDOWS)](/previous-versions/windows/it-pro/windows-vista/cc766285(v=ws.10))
  
[Office 365 ve Office 365 GCC'de TLS 1.2'ye hazırlanma](/office365/troubleshoot/security/prepare-tls-1.2-in-office-365)

[Azure Front Door tarafından desteklenen geçerli şifreleme paketleri nedir?](/azure/frontdoor/front-door-faq#what-are-the-current-cipher-suites-supported-by-azure-front-door-)
