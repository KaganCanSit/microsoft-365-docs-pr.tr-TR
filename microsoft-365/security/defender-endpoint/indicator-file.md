---
title: Dosyalar için göstergeler oluşturun
ms.reviewer: ''
description: Varlıkların algılanmasını, önlenmesini ve dışlanmasını tanımlayan bir dosya karması için göstergeler oluşturun.
keywords: dosya, karma, yönetme, izin verilen, engellenen, engelleme, temizleme, kötü amaçlı, dosya karması, IP adresi, URL'ler, etki alanı
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
ms.openlocfilehash: f1d32c546fc270e044d391dd35f325afc98fe5a9
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101457"
---
# <a name="create-indicators-for-files"></a>Dosyalar için göstergeler oluşturun

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 1](/microsoft-365/security/defender-endpoint/defender-endpoint-plan-1)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Uç Nokta için Defender'ı deneyimlemek mi istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Kötü amaçlı olabilecek dosyaları veya şüpheli kötü amaçlı yazılımları yasaklayarak kuruluşunuzda bir saldırının daha fazla yayılmasını önleyin. Kötü amaçlı olabilecek bir taşınabilir yürütülebilir dosya (PE) biliyorsanız, dosyayı engelleyebilirsiniz. Bu işlem, kuruluşunuzdaki cihazlarda okunmasını, yazılmasını veya yürütülmesini engeller.

Dosyalar için gösterge oluşturmanın üç yolu vardır:

- Ayarlar sayfasından bir gösterge oluşturarak
- Dosya ayrıntıları sayfasındaki gösterge ekle düğmesini kullanarak bağlamsal bir gösterge oluşturarak
- [Gösterge API'sini](ti-indicator.md) kullanarak bir gösterge oluşturarak

## <a name="before-you-begin"></a>Başlamadan önce

Dosyalar için göstergeler oluşturmadan önce aşağıdaki önkoşulları anlamak önemlidir:

- Kuruluşunuz **Microsoft Defender Virüsten Koruma kullanıyorsa (etkin modda)** ve **Bulut tabanlı koruma etkinse bu** özellik kullanılabilir. Daha fazla bilgi için bkz. [Bulut tabanlı korumayı yönetme](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus).

- Kötü amaçlı yazılımdan koruma istemcisi sürümü 4.18.1901.x veya üzeri olmalıdır. [Bkz. Aylık platform ve altyapı sürümleri](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions)

- Windows 10, sürüm 1703 veya üzeri, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 ve Windows Server 2022'ye sahip cihazlarda desteklenir.
    
   > [!NOTE]
   > Windows Server 2016 ve Windows Server 2012 R2'nin bu özelliğin çalışması için [Windows sunucularında ekleme](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016) yönergeleri kullanılarak eklenmelidir. İzin Ver, Engelle ve Düzelt eylemlerine sahip özel dosya göstergeleri artık [macOS ve Linux için geliştirilmiş kötü amaçlı yazılımdan koruma altyapısı özellikleri için genel önizlemede](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/enhanced-antimalware-engine-capabilities-for-linux-and-macos/ba-p/3292003) de kullanılabilir.

- Dosyaları engellemeye başlamak için önce [Ayarlar'da "engelle veya izin ver" özelliğini açmanız](advanced-features.md) gerekir.

Bu özellik, şüpheli kötü amaçlı yazılımların (veya kötü amaçlı olabilecek dosyaların) web'den indirilmesini önlemek için tasarlanmıştır. Şu anda .exe ve .dll dosyaları da dahil olmak üzere taşınabilir yürütülebilir (PE) dosyaları destekler. Kapsam zaman içinde uzatılır.

## <a name="create-an-indicator-for-files-from-the-settings-page"></a>Ayarlar sayfasından dosyalar için gösterge oluşturma

1. Gezinti bölmesinde uç **nokta göstergelerini** \> **Ayarlar** \> seçin (**Kurallar'ın** altında).

2. **Dosya karmaları** sekmesini seçin.

3. **Öğe ekle'yi** seçin.

4. Aşağıdaki ayrıntıları belirtin:
    - Gösterge - Varlık ayrıntılarını belirtin ve göstergenin süre sonunu tanımlayın.
    - Eylem - Gerçekleştirilecek eylemi belirtin ve bir açıklama sağlayın.
    - Kapsam - Cihaz grubunun kapsamını tanımlayın.

5. Özet sekmesinde ayrıntıları gözden geçirin ve **Kaydet'i** seçin.

## <a name="create-a-contextual-indicator-from-the-file-details-page"></a>Dosya ayrıntıları sayfasından bağlamsal gösterge oluşturma

[Bir dosyada yanıt eylemleri](respond-file-alerts.md) gerçekleştirirken seçeneklerden biri, dosya için bir gösterge eklemektir. Bir dosya için gösterge karması eklediğinizde, kuruluşunuzdaki bir cihaz çalıştırmayı denediğinde uyarı oluşturmayı ve dosyayı engellemeyi seçebilirsiniz.

Bir gösterge tarafından otomatik olarak engellenen dosyalar dosyanın İşlem merkezinde gösterilmez, ancak uyarılar Uyarılar kuyruğunda görünmeye devam eder.

## <a name="public-preview-alerting-on-file-blocking-actions"></a>Genel Önizleme: Dosya engelleme eylemleriyle ilgili uyarı

> [!IMPORTANT]
> Bu bölümdeki bilgiler (**Otomatik araştırma ve düzeltme altyapısı için Genel Önizleme**), ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilebilen yayın öncesi ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Dosya IOC için desteklenen geçerli eylemler izin verme, denetleme ve engelleme ve düzeltme işlemleridir. Bir dosyayı engellemeyi seçtikten sonra uyarı tetiklemenin gerekip gerekmediğini seçebilirsiniz. Bu şekilde, güvenlik operasyonları ekiplerinize gelen uyarı sayısını denetleyebilecek ve yalnızca gerekli uyarıların tetiklenmiş olduğundan emin olabilirsiniz.

Microsoft 365 Defender'da **Ayarlar** >  **EndpointsIndicatorsYeni** >  >  **Dosya Karması Ekle'ye** gidin.

Engelle'yi seçin ve dosyayı düzeltin.

Dosya bloğu olayında uyarı oluştur seçeneğini belirleyin ve uyarı ayarlarını tanımlayın:

- Uyarı başlığı
- Uyarı önem derecesi
- Kategori
- Açıklama
- Önerilen eylemler

:::image type="content" source="images/indicators-generate-alert.png" alt-text="Dosya göstergeleri için Uyarı ayarları" lightbox="images/indicators-generate-alert.png":::

> [!IMPORTANT]
>
> - Genellikle, dosya blokları birkaç dakika içinde zorlanır ve kaldırılır, ancak 30 dakika kadar sürebilir.
> - Aynı zorlama türüne ve hedefe sahip çakışan dosya IoC ilkeleri varsa, daha güvenli karma ilkesi uygulanır. SHA-256 dosya karması IoC ilkesi SHA-1 dosya karması IoC ilkesine sahip olur ve karma türleri aynı dosyayı tanımlarsa MD5 dosya karması IoC ilkesini kazanır. Cihaz grubundan bağımsız olarak bu her zaman geçerlidir.
> - Diğer tüm durumlarda, aynı zorlama hedefine sahip çakışan dosya IoC ilkeleri tüm cihazlara ve cihazın grubuna uygulanırsa, cihaz için cihaz grubundaki ilke kazanır.
> - EnableFileHashComputation grup ilkesi devre dışı bırakılırsa, IoC dosyasının engelleme doğruluğu azalır. Ancak etkinleştirme `EnableFileHashComputation` işlemi cihaz performansını etkileyebilir. Örneğin, büyük dosyaları bir ağ paylaşımından yerel cihazınıza, özellikle de bir VPN bağlantısı üzerinden kopyalamanın cihaz performansı üzerinde bir etkisi olabilir.
>
> EnableFileHashComputation grup ilkesi hakkında daha fazla bilgi için bkz. [Defender CSP](/windows/client-management/mdm/defender-csp).

## <a name="public-preview-advanced-hunting-capabilities"></a>Genel Önizleme: Gelişmiş tehdit avcılığı özellikleri

> [!IMPORTANT]
> Bu bölümdeki bilgiler (**Otomatik araştırma ve düzeltme altyapısı için Genel Önizleme**), ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilebilen yayın öncesi ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Yanıt eylemi etkinliğini önceden avlanmak için sorgulayabilirsiniz. Aşağıda örnek bir gelişmiş avcılık sorgusu verilmiştir:

```console
search in (DeviceFileEvents, DeviceProcessEvents, DeviceEvents, DeviceRegistryEvents, DeviceNetworkEvents, DeviceImageLoadEvents, DeviceLogonEvents)
Timestamp > ago(30d)
| where AdditionalFields contains "EUS:Win32/CustomEnterpriseBlock!cl"
```

Gelişmiş avcılık hakkında daha fazla bilgi için bkz. [Gelişmiş avcılık ile tehditleri proaktif olarak avlama](advanced-hunting-overview.md).

Aşağıda, yukarıdan örnek sorguda kullanılabilecek ek iş parçacığı adları verilmişti:

Dosyaları:

- EUS:Win32/CustomEnterpriseBlock!cl
- EUS:Win32/CustomEnterpriseNoAlertBlock!cl

Sertifika:

- EUS:Win32/CustomCertEnterpriseBlock!cl

Yanıt eylemi etkinliği cihaz zaman çizelgesinde de görüntülenebilir.

## <a name="policy-conflict-handling"></a>İlke çakışması işleme

Sertifika ve Dosya IoC ilke işleme çakışması aşağıdaki sırayı izler:

- Windows Defender Uygulama Denetimi ve AppLocker zorlama modu ilkesi/ilkeleri tarafından dosyaya izin verilmiyorsa **Engelle**
- Dosyaya Microsoft Defender Virüsten Koruma dışlama izin veriliyorsa **İzin Ver**
- Aksi takdirde dosya bir blok tarafından engellenirse veya uyarılırsa ya da ioC'yi uyarırsa **Engelle/Uyar**
- Dosyaya izin verilen bir dosya IoC ilkesi tarafından izin veriliyorsa, **İzin Ver**
- Aksi takdirde dosya ASR kuralları, CFA, AV, SmartScreen ve **ardından Engelle** tarafından engellenirse
- Else **Allow** (Uygulama Denetimi & AppLocker ilkesini Windows Defender geçirir, buna ioC kuralı uygulanmaz)

>[!NOTE]
> Microsoft Defender Virüsten Koruma **Engelle** olarak ayarlandığı ancak Uç Nokta için Defender'ın **İzin Ver** olarak ayarlandığı durumlarda, ilke varsayılan olarak **İzin Ver** olarak ayarlanır.

Aynı zorlama türüne ve hedefe sahip çakışan dosya IoC ilkeleri varsa, daha güvenli (daha uzun anlamına gelir) karması ilkesi uygulanır. Örneğin, bir SHA-256 dosya karması IoC ilkesi, her iki karma türü de aynı dosyayı tanımlarsa bir MD5 dosya karması IoC ilkesini kazanır.

> [!WARNING]
> Dosyalar ve sertifikalar için ilke çakışması işleme, etki alanları/URL'ler/IP adresleri için ilke çakışması işlemesinden farklıdır.

Tehdit ve güvenlik açığı yönetimi engelleyici uygulama özellikleri zorlama için dosya ICS'lerini kullanır ve yukarıdaki çakışma işleme sırasını izler.

### <a name="examples"></a>Örnekler

<br>

****

|Bileşen|Bileşen zorlama|Dosya göstergesi Eylemi|Sonuç|
|---|---|---|---|
|Saldırı yüzeyi azaltma dosyası yolu dışlaması|İzin ver|Engelle|Engelle|
|Saldırı yüzeyi azaltma kuralı|Engelle|İzin ver|İzin ver|
|Uygulama Denetimini Windows Defender|İzin ver|Engelle|İzin ver|
|Uygulama Denetimini Windows Defender|Engelle|İzin ver|Engelle|
|Microsoft Defender Virüsten Koruma dışlama|İzin ver|Engelle|İzin ver|
|

## <a name="see-also"></a>Ayrıca bkz.

- [Göstergeleri oluşturun](manage-indicators.md)
- [URL/etki alanı ve IP’ler için göstergeler oluşturun](indicator-ip-domain.md)
- [Sertifikaları temel alan göstergeler oluşturma](indicator-certificates.md)
- [Göstergeleri yönetin](indicator-manage.md)
