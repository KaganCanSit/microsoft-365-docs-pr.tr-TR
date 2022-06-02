---
title: URL/etki alanı ve IP’ler için göstergeler oluşturun
ms.reviewer: ''
description: VARLıKLARın algılanmasını, önlenmesini ve dışlanmasını tanımlayan IP'ler ve URL'ler/etki alanları için göstergeler oluşturun.
keywords: ip, url, etki alanı, yönetme, izin verildi, engellendi, engelle, temiz, kötü amaçlı, dosya karması, IP adresi, URL'ler, etki alanı
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
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 955f11aa44bd0defb867c25124da7c5a3769c98d
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65840131"
---
# <a name="create-indicators-for-ips-and-urlsdomains"></a>URL/etki alanı ve IP’ler için göstergeler oluşturun

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Uç Nokta için Defender, Microsoft tarayıcıları için SmartScreen Windows Defender ve Microsoft dışı tarayıcılar veya tarayıcı dışında yapılan çağrılar için Ağ Koruması aracılığıyla Microsoft'un kötü amaçlı IP'ler/URL'ler olarak gördüğü şeyleri engelleyebilir.

Bunun için tehdit bilgileri veri kümesi Microsoft tarafından yönetilmiştir.

IP'ler ve URL'ler veya etki alanları için göstergeler oluşturarak artık kendi tehdit zekanıza göre IP'lere, URL'lere veya etki alanlarına izin verebilir veya bunları engelleyebilirsiniz. Riskli bir uygulama açtıklarında kullanıcıları bir istemle de uyarabilirsiniz. İstem, uygulamayı kullanmalarını engellemez, ancak özel bir ileti ve uygulamanın uygun kullanımını açıklayan bir şirket sayfasına bağlantılar sağlayabilirsiniz. Kullanıcılar yine de uyarıyı atlayabilir ve gerekirse uygulamayı kullanmaya devam edebilir.

Bazı grupların diğerlerinden daha fazla veya daha az risk altında olduğunu düşünüyorsanız, bunu ayarlar sayfasından veya makine gruplarına göre yapabilirsiniz.

> [!NOTE]
> IP adresleri için sınıfsız Inter-Domain Yönlendirme (CIDR) gösterimi desteklenmez.

## <a name="before-you-begin"></a>Başlamadan önce

IPS, URL'ler veya etki alanları için göstergeler oluşturmadan önce aşağıdaki önkoşulları anlamak önemlidir:

- URL/IP izin verir ve engeller, Uç Nokta için Defender bileşeni Ağ Koruması'nın blok modunda etkinleştirilmesine bağlıdır. Ağ Koruması ve yapılandırma yönergeleri hakkında daha fazla bilgi için bkz. [Ağ korumasını etkinleştirme](enable-network-protection.md).
- Kötü amaçlı yazılımdan koruma istemcisi sürümü 4.18.1906.x veya üzeri olmalıdır. 
- Windows 10, sürüm 1709 veya üzeri, Windows 11, Windows Server 2016, Windows Server 2012 R2, Windows Server 2019, Windows Server 2022 ve Android ve cihazları iOS.

    > [!NOTE]
    > Windows Server 2016 ve Windows Server 2012 R2'nin bu özelliğin çalışması için [Windows sunucularında ekleme](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016) yönergeleri kullanılarak eklenmelidir.

- Microsoft 365 Defender **Ayarlar** \> **Gelişmiş özelliklerde** **Özel ağ göstergelerinin** **etkinleştirildiğinden** \> emin olun. Daha fazla bilgi için bkz [. Gelişmiş özellikler](advanced-features.md).
- iOS gösterge desteği için bkz. [iOS'da Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/ios-configure-features#configure-custom-indicators).
- Android gösterge desteği için bkz. [Android Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/android-configure#configure-custom-indicators).

> [!IMPORTANT]
> Gösterge listesine yalnızca dış IP'ler eklenebilir. İç IP'ler için göstergeler oluşturulamaz.
> Web koruma senaryoları için Microsoft Edge'daki yerleşik özellikleri kullanmanızı öneririz. Microsoft Edge ağ trafiğini incelemek için [Ağ Koruması'na](network-protection.md) olanak tanır ve TCP, HTTP ve HTTPS (TLS) bloklarına izin verir.
> Çakışan URL göstergesi ilkeleri varsa, daha uzun yol uygulanır. Örneğin, URL göstergesi ilkesi `https://support.microsoft.com/office` URL göstergesi ilkesinden `https://support.microsoft.com`önceliklidir.

> [!NOTE]
> Diğer tüm işlemler için web koruma senaryoları, inceleme ve zorlama için Ağ Koruması'ndan yararlanıyor:
>
> - IP, üç protokol için de desteklenir
> - Yalnızca tek IP adresleri desteklenir (CIDR blokları veya IP aralıkları yoktur)
> - Şifrelenmiş URL'ler (tam yol) yalnızca birinci taraf tarayıcılarda engellenebilir (Internet Explorer, Edge)
> - Şifrelenmiş URL'ler (yalnızca FQDN) birinci taraf tarayıcıların dışında engellenebilir (Internet Explorer, Edge)
> - Tam URL yol blokları etki alanı düzeyinde ve tüm şifrelenmemiş URL'lere uygulanabilir
>
> Eylemin gerçekleştirilişi ile URL ve IP'nin engellenmesi arasında 2 saate kadar gecikme süresi (genellikle daha az) olabilir.

Uyarı modunu kullanırken aşağıdaki denetimleri yapılandırabilirsiniz:

**Atlama özelliği**:

- Edge'de İzin Ver düğmesi
- Bildirimdeki İzin Ver düğmesi (Microsoft dışı tarayıcılar)
- Göstergedeki atlama süresi parametresi
- Microsoft ve Microsoft dışı tarayıcılarda zorlamayı atlama

**Yeniden yönlendirme URL'si**:

- Göstergedeki yeniden yönlendirme URL'si parametresi
- Edge'de URL'yi yeniden yönlendirme
- Bildirimde yeniden yönlendirme URL'si (Microsoft dışı tarayıcılar)

Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender tarafından bulunan uygulamaları yönetme](/cloud-app-security/mde-govern).

## <a name="create-an-indicator-for-ips-urls-or-domains-from-the-settings-page"></a>Ayarlar sayfasından IP'ler, URL'ler veya etki alanları için bir gösterge oluşturma

1. Gezinti bölmesinde uç **nokta göstergelerini** \> **Ayarlar** \> seçin (**Kurallar'ın** altında).

2. **IP adresleri veya URL'ler/Etki Alanları** sekmesini seçin.

3. **Öğe ekle'yi** seçin.

4. Aşağıdaki ayrıntıları belirtin:
   - Gösterge - Varlık ayrıntılarını belirtin ve göstergenin süre sonunu tanımlayın.
   - Eylem - Gerçekleştirilecek eylemi belirtin ve bir açıklama sağlayın.
   - Kapsam - Makine grubunun kapsamını tanımlayın.

5. Özet sekmesinde ayrıntıları gözden geçirin ve **Kaydet'e** tıklayın.

## <a name="related-topics"></a>İlgili konular

- [Göstergeleri oluşturun](manage-indicators.md)
- [Dosyalar için göstergeler oluşturun](indicator-file.md)
- [Sertifikaları temel alan göstergeler oluşturma](indicator-certificates.md)
- [Göstergeleri yönetin](indicator-manage.md)
