---
title: URL'ler ve URL'ler/etki alanları için göstergeler oluşturma
ms.reviewer: ''
description: Varlıkları algılama, önleme ve dışlamaları tanımlayan IP'ler ve URL'ler/etki alanları için göstergeler oluşturun.
keywords: ip, url, etki alanı, yönet, izin verilen, engellendi, engelle, temizle, kötü amaçlı, dosya karma, ip adresi, url'ler, etki alanı
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
ms.openlocfilehash: 8865bf2138947238980b533b8b47ee9663fd5448
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2022
ms.locfileid: "63014044"
---
# <a name="create-indicators-for-ips-and-urlsdomains"></a>URL'ler ve URL'ler/etki alanları için göstergeler oluşturma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Uç Nokta için Defender, Microsoft tarayıcıları için Windows Defender SmartScreen aracılığıyla ve Microsoft dışı tarayıcılar veya tarayıcı dışında yapılan aramalar için Ağ Koruması aracılığıyla kötü amaçlı IP'ler/URL'ler olarak değerlendirmesini engelleyebilir.

Bunun için tehdit zekası veri kümesi Microsoft tarafından yönetiliyor.

Artık IP'ler ve URL'ler veya etki alanları için göstergeler oluşturarak, kendi tehdit zekanız temel alarak URL'lere, URL'lere veya etki alanlarına izin ve ardından bu göstergeleri engelleyebilirsiniz. Ayrıca, riskli bir uygulama açtıklarını kullanıcılara bir istem ile uyarabilirsiniz. Komut istemi, uygulamayı kullanmalarını durdurmaz, ancak özel bir ileti ve uygulamanın uygun kullanımını açıklayan bir şirket sayfasına bağlantı sabilirsiniz. Kullanıcılar yine de uyarıyı atlayarak gerekirse uygulamayı kullanmaya devam eder.

Bazı grupların diğerlerine göre daha fazla veya daha az riskli olduğunu varsaya kadar ayarlar sayfasından veya makine gruplarına göre bunu yapabilirsiniz.

> [!NOTE]
> IP Inter-Domain sınıfsız Yönlendirme (CIDR) yönlendirmesi desteklenmiyor.

## <a name="before-you-begin"></a>Başlamadan önce

IPS, URL veya etki alanları için gösterge oluşturmadan önce aşağıdaki önkoşulların anlamak önemlidir:

- URL/IP izin verme ve engelleme, Uç nokta bileşeni Ağ Koruması için Defender'ın engelleme modunda etkinleştirilmesine dayandır. Ağ Koruması ve yapılandırma yönergeleri hakkında daha fazla bilgi için bkz. [Ağ korumasını etkinleştirme](enable-network-protection.md).
- Kötü amaçlı yazılımdan koruma istemci sürümü 4.18.1906.x veya sonraki bir sürümde olabilir. 
- Windows 10 sürüm 1709 veya sonraki sürümler, Windows 11, Windows Server 2016, Windows Server 2012 R2, Windows Server 2019 ve Windows Server 2022 makinelerde desteklenen makinelerde.

    > [!NOTE]
    > Windows Server 2016 ve Windows Server 2012 R2 için, bu özelliğin çalışması için [onboard Windows sunucularında](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016) verilen yönergeler kullanılarak ekleme gerekiyor.

- Gelişmiş **özellikler'i kullanarak Özel** ağ göstergelerinin Microsoft 365 Defender **Ayarlar** \>  \> **emin olun**. Daha fazla bilgi için bkz. [Gelişmiş özellikler](advanced-features.md).
- iOS'ta göstergelerin desteği için bkz [. Özel göstergeleri yapılandırma](/microsoft-365/security/defender-endpoint/ios-configure-features#configure-custom-indicators).

> [!IMPORTANT]
> Gösterge listesine yalnızca dış IP'ler eklenebilir. İç IP'ler için göstergeler oluşturulamaz.
> Web koruma senaryoları için, web koruma senaryolarında yerleşik özellikleri Microsoft Edge. Microsoft Edge, ağ [trafiğini incelemek için](network-protection.md) Ağ Koruması'nın kullanır ve TCP, HTTP ve HTTPS (TLS) bloklarına izin verir.
> Çakışan URL göstergesi ilkeleri varsa, uzun yol uygulanır. Örneğin, URL göstergesi ilkesi, `https://support.microsoft.com/office` URL gösterge ilkesine göre önceliklidir `https://support.microsoft.com`.

> [!NOTE]
> Diğer tüm işlemler için, web koruma senaryoları inceleme ve zorlama için Ağ Koruması'nın avantajlarını sağlar:
>
> - IP, bu üç protokolün üçü için de destekler
> - Yalnızca tek tek IP adresleri destek kalır (CIDR blokları veya IP aralıkları yoktur)
> - Şifreli URL'ler (tam yol) yalnızca birinci taraf tarayıcılarda (Internet Explorer, Edge) engellenmiş olabilir
> - Şifrelenmiş URL'ler (yalnızca FQDN) birinci taraf tarayıcılar (Internet Explorer, Edge) dışında engellenmiş olabilir
> - Tam URL yol blokları etki alanı düzeyine ve tüm şifrelenmemiş URL'lere uygulanabilir
>
> Eylemin 4 saat içinde (genellikle daha kısa) ve URL ile IP'nin engellenmiş olması arasında en çok 2 saatlik gecikme süresi olabilir.

Uyarı modunu kullanırken, aşağıdaki denetimleri yapılandırabilirsiniz:

**Atlama özelliği**:

- Edge'de İzin Ver düğmesi
- Konuşmada İzin Ver düğmesi (Microsoft dışı tarayıcılar)
- Göstergede süre parametresini atlama
- Microsoft ve Microsoft dışı tarayıcılarda zorlamayı atlama

**Yeniden yönlendirme URL'si**:

- Göstergede URL parametresini yeniden yönlendir
- Edge'de Yeniden Yönlendirme URL'si
- Konuşmada URL'yi yeniden yönlendirme (Microsoft dışı tarayıcılar)

Daha fazla bilgi için bkz [. Uç Nokta için Microsoft Defender tarafından bulunan uygulamaları yönetme](/cloud-app-security/mde-govern).

## <a name="create-an-indicator-for-ips-urls-or-domains-from-the-settings-page"></a>Ayarlar sayfasından IP'ler, URL'ler veya etki alanları için bir gösterge oluşturma

1. Gezinti bölmesinde, Uç Noktaları **Ayarlar** \> **Seçin** \> (**Kurallar'ın** **altında**).

2. IP adreslerini **veya URL'leri/Etki Alanları sekmesini** seçin.

3. Öğe **ekle'yi seçin**.

4. Aşağıdaki ayrıntıları belirtin:
   - Gösterge - Varlık ayrıntılarını belirtin ve göstergenin sona erme tarihini tanımlayın.
   - Eylem - Alınacak eylemi belirtin ve bir açıklama girin.
   - Kapsam - Makine grubunun kapsamını tanımlayın.

5. Özet sekmesinde ayrıntıları gözden geçirin ve Kaydet'e **tıklayın**.

## <a name="related-topics"></a>İlgili konular

- [Gösterge oluşturma](manage-indicators.md)
- [Dosyalar için göstergeler oluşturma](indicator-file.md)
- [Sertifikalara dayalı göstergeler oluşturma](indicator-certificates.md)
- [Göstergeleri yönetme](indicator-manage.md)
