---
title: Dosyalar için göstergeler oluşturma
ms.reviewer: ''
description: Varlıkları algılama, önleme ve dışlamaları tanımlayan bir dosya karması için göstergeler oluşturun.
keywords: dosya, karma, yönet, izin verilen, engellendi, engelle, temizle, kötü amaçlı, dosya karma, ip adresi, url'ler, etki alanı
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
ms.openlocfilehash: 2ee262e2a42bcf4bd03a6d1204b60412d60740d5
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2022
ms.locfileid: "63016332"
---
# <a name="create-indicators-for-files"></a>Dosyalar için göstergeler oluşturma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

Olası kötü amaçlı dosyaları veya kötü amaçlı yazılımdan şüpheleniyorlar tarafından engellenebilir ve saldırının organizasyona daha fazla yayılmasını önle. Kötü amaçlı olabilecek bir taşınabilir yürütülebilir (PE) dosyası biliyorsanız, dosyayı engelleyebilirsiniz. Bu işlem, okunmalarını, yazıldıklarını veya organizasyonlar üzerinde yürütüleceklerini önler.

Dosyalar için göstergeler oluşturmanın üç yolu vardır:

- Ayarlar sayfasından bir gösterge oluşturarak
- Dosya ayrıntıları sayfasındaki gösterge ekle düğmesini kullanarak bir bağlam göstergesi oluşturarak
- Gösterge API'si aracılığıyla bir [gösterge oluşturarak](ti-indicator.md)

## <a name="before-you-begin"></a>Başlamadan önce

Dosyalar için gösterge oluşturmadan önce aşağıdaki önkoşulları anlamak önemlidir:

- Bu özellik, organizasyonunız etkin **modda Microsoft Defender Virüsten Koruma kullanıyorsa ve** **Bulut tabanlı koruma etkinleştirildiyse kullanılabilir**. Daha fazla bilgi için bkz [. Bulut tabanlı korumayı yönetme](/windows/security/threat-protection/microsoft-defender-antivirus/deploy-manage-report-microsoft-defender-antivirus).

- Kötü amaçlı yazılımdan koruma istemci sürümü 4.18.1901.x veya sonraki bir sürümde olabilir. Aylık [platform ve altyapı sürümlerine bakın](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions)

- Windows 10, sürüm 1703 veya sonraki bir sürümü, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 ve Windows Server 2022 yüklü cihazlarda Windows.
    
   >[!NOTE]
    >Windows Server 2016 ve Windows Server 2012 R2 için, bu özelliğin çalışması için [onboard Windows sunucularında](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016) verilen yönergeler kullanılarak ekleme gerekiyor. 

- Dosyaları engellemeye başlamak için öncelikle dosyanın içinde ["engelle veya izin ver" özelliğini Ayarlar](advanced-features.md).

Bu özellik kötü amaçlı yazılımdan (veya kötü amaçlı olabilecek dosyalardan) şüphelenilen dosyaların Web'den indirilmalarını önlemek için tasarlanmıştır. Şu anda dosya dosyaları ve yürütülebilir dosyalar da dahil olmak üzere taşınabilir yürütülebilir (PE) .exe .dll destekler. Kapsam zaman içinde uzatılacaktır.

## <a name="create-an-indicator-for-files-from-the-settings-page"></a>Ayarlar sayfasından dosyalar için bir gösterge oluşturma

1. Gezinti bölmesinde, Uç Noktaları **Ayarlar** \> **Seçin** \> (**Kurallar'ın** **altında**).

2. Dosya **karmaları sekmesini** seçin.

3. Gösterge **ekle'yi seçin**.

4. Aşağıdaki ayrıntıları belirtin:
    - Gösterge - Varlık ayrıntılarını belirtin ve göstergenin sona erme tarihini tanımlayın.
    - Eylem - Alınacak eylemi belirtin ve bir açıklama girin.
    - Kapsam - Cihaz grubunun kapsamını tanımlayın.

5. Özet sekmesinde ayrıntıları gözden geçirerek Kaydet'i **seçin**.

## <a name="create-a-contextual-indicator-from-the-file-details-page"></a>Dosya ayrıntıları sayfasından bağlam göstergesi oluşturma

Bir dosya üzerinde yanıt eylemleri [gerçekleştirerek seçeneklerden biri](respond-file-alerts.md) de dosya için bir gösterge eklemek. Dosya için bir gösterge karması eklerken, bir uyarı bırakmayı ve kuruluşta bir cihaz bu karmayı çalıştırmayı her çalıştırsa dosyayı engellemeyi seçebilirsiniz.

Otomatik olarak bir gösterge tarafından engellenen dosyalar dosyanın İşlem merkezinde görünmez, ancak uyarılar Uyarılar sırasında görünmeye devam eder.

## <a name="public-preview-alerting-on-file-blocking-actions"></a>Genel Önizleme: Dosya engelleme eylemleriyle ilgili uyarı

> [!IMPORTANT]
> Bu bölümdeki **bilgiler (** Otomatik araştırma ve düzeltme altyapısı için Genel Önizleme), ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilecek, ön sürüm ürünüyle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

IOC dosyası için desteklenen geçerli eylemler izin verme, denetleme ve engelleme ile düzeltmektir. Dosyayı engellemeyi seçtikten sonra, uyarının tetiklenirken gerekli olup olmadığını seçebilirsiniz. Bu şekilde, güvenlik işlemleri ekiplerinize gelen uyarı sayısını kontrolabilecek ve yalnızca gerekli uyarıların yükselt bunlardan emin olacağınız olur.

Daha Microsoft 365 Defender, Ayarlar  > **EndpointsIndicatorsAdd** >  >  **Yeni Dosya Karma'ya gidin**.

Engelle'yi seçin ve dosyayı düzeltmek için.

Dosya bloğu olayında uyarı oluştur'a tıklayın ve uyarı ayarlarını tanımlayın:

- Uyarı başlığı
- Uyarı önem derecesi
- Kategori
- Açıklama
- Önerilen eylemler

![Dosya göstergeleri için uyarı ayarları.](images/indicators-generate-alert.png)

> [!IMPORTANT]
>
> - Normalde, dosya blokları zorunlu kılınır ve birkaç dakika içinde kaldırılır, ancak yukarı doğru 30 dakika sürebilir.
> - Aynı zorlama türü ve hedefine sahip çakışan dosya IoC ilkeleri varsa, daha güvenli karma ilkesi uygulanır. SHA-256 dosya karma IoC ilkesi, SHA-1 dosya karma IoC ilkesine göre kazanır ve karma türleri aynı dosyayı tanımlarsa MD5 dosya karma IoC ilkesine sahip olur. Cihaz grubundan bağımsız olarak bu her zaman doğrudur.
> - Diğer tüm durumlarda, aynı zorlama hedefiyle çakışan dosya IoC ilkeleri tüm cihazlara ve cihazın grubuna uygulanırsa, cihaz grubunda ilkeler uygulanır.
> - EnableFileHashComputation grup ilkesi devre dışı bırakılırsa, dosya IoC'nin engelleme doğruluğu azalır. Bununla birlikte, etkinleştirme `EnableFileHashComputation` cihaz performansını etkileyebilir. Örneğin, ağ paylaşımından büyük dosyaları yerel cihazınıza özellikle de bir VPN bağlantısı üzerinden kopyalamak cihaz performansını etkileyebilir.
>
> EnableFileHashComputation grup ilkesi hakkında daha fazla bilgi için bkz. [Defender CSP](/windows/client-management/mdm/defender-csp).

## <a name="public-preview-advanced-hunting-capabilities"></a>Genel Önizleme: Gelişmiş av özellikleri

> [!IMPORTANT]
> Bu bölümdeki **bilgiler (** Otomatik araştırma ve düzeltme altyapısı için Genel Önizleme), ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilabilecek yayın öncesi sürüm ürünüyle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Önceden avda yanıt eylemi etkinliğini sorguabilirsiniz. Aşağıda bir örnek gelişmiş arama sorgusu verilmiştir:

```console
search in (DeviceFileEvents, DeviceProcessEvents, DeviceEvents, DeviceRegistryEvents, DeviceNetworkEvents, DeviceImageLoadEvents, DeviceLogonEvents)
Timestamp > ago(30d)
| where AdditionalFields contains "EUS:Win32/CustomEnterpriseBlock!cl"
```

Gelişmiş arama hakkında daha fazla bilgi için bkz. Gelişmiş [avla tehditlere karşı önceden arama.](advanced-hunting-overview.md)

Aşağıda, yukarıdan örnek sorguda  kullanılan diğer iş parçacığı adları verilmiştir:

Dosyalar:

- EUS:Win32/CustomEnterpriseBlock!cl
- EUS:Win32/CustomEnterpriseNoAlertBlock!cl

Sertifikalar:

- EUS:Win32/CustomCertEnterpriseBlock!cl

Yanıt eylemi etkinliği cihaz zaman çizelgesinde de değiştirilebilir.

## <a name="policy-conflict-handling"></a>İlke çakışması işleme

Sertifika ve Dosya IoC ilke işleme çakışması aşağıdaki sırayı izlemektedir:

- Uygulama Denetimi ve AppLocker zorunlu mod ilkesi/ilkeleri Windows Defender tarafından dosyaya izin verilmiyorsa Engelle 
- Dosyaya dışlama tarafından izin veriliyorsa Microsoft Defender Virüsten Koruma izin **ver**
- Dosya bir blok veya uyarı tarafından engellenmişse veya uyarılmışsa, IoC dosyası için uyarırsanız, Engelle **/Uyar**
- Dosyaya izin verme dosyası IoC ilkesi tarafından izin veriliyorsa, İzin **Ver**
- Else if the file is blocked by ASR rules, CFA, AV, SmartScreen, then **Block**
- Else **Allow** (uygulama denetimi Windows Defender AppLocker & geçer, IoC kuralı geçerli değildir)

Aynı zorlama türü ve hedefine sahip çakışan dosya IoC ilkeleri varsa, daha güvenli (yani daha uzun) karma ilkesi uygulanır. Örneğin, her iki karma türü de aynı dosyayı tanımlarsa, SHA-256 dosya karma IoC ilkesi MD5 dosya karma IoC ilkesine göre kazanır.

> [!WARNING]
> Dosyalar ve sertifikalar için ilke çakışması işleme, etki alanları/URL'ler/IP adresleri için ilke çakışması işlemeden farklıdır.

Threat and güvenlik açığı yönetimi's block vulnerable application features uses the file Iocs for enforcement and will follow the above conflict handling order.

### <a name="examples"></a>Örnekler

<br>

****

|Bileşen|Bileşen zorlama|Dosya göstergesi Eylemi|Sonuç|
|---|---|---|---|
|Saldırı yüzeyini azaltma dosya yolu dışlama|İzin ver|Engelle|Engelle|
|Saldırı yüzeyini azaltma kuralı|Engelle|İzin ver|İzin ver|
|Windows Defender Uygulaması Denetimi|İzin ver|Engelle|İzin ver|
|Windows Defender Uygulaması Denetimi|Engelle|İzin ver|Engelle|
|Microsoft Defender Virüsten Koruma dışlama|İzin ver|Engelle|İzin ver|
|

## <a name="see-also"></a>Ayrıca bkz.

- [Gösterge oluşturma](manage-indicators.md)
- [URL'ler ve URL'ler/etki alanları için göstergeler oluşturma](indicator-ip-domain.md)
- [Sertifikalara dayalı göstergeler oluşturma](indicator-certificates.md)
- [Göstergeleri yönetme](indicator-manage.md)
