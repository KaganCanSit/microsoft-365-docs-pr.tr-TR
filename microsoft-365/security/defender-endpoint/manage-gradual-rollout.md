---
title: Microsoft Defender güncelleştirmeleri için aşamalı dağıtım işlemini yönetme
description: Aşamalı güncelleştirme işlemi ve denetimleri hakkında bilgi edinin
keywords: güncelleştirme, güncelleştirme işlemi, denetimler, yayın
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 8f1f2add8196afef6e8bd738586957d7fea15c84
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65416342"
---
# <a name="manage-the-gradual-rollout-process-for-microsoft-defender-updates"></a>Microsoft Defender güncelleştirmeleri için aşamalı dağıtım işlemini yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Kritik koruma özellikleri sunmak ve saldırıları önlemek için istemci bileşenlerinin güncel olduğundan emin olmak önemlidir.

Özellikler çeşitli bileşenler aracılığıyla sağlanır:

- [Uç Nokta Algılama & Yanıtı](overview-endpoint-detection-response.md)
- Bulut [tabanlı koruma ile yeni nesil](microsoft-defender-antivirus-windows.md) [koruma](cloud-protection-microsoft-defender-antivirus.md)
- [Saldırı Yüzeyi Azaltma](overview-attack-surface-reduction.md)

Güncelleştirmeler, aşamalı bir sürüm işlemi kullanılarak aylık olarak yayımlanıyor. Bu işlem, ortaya çıkan etkiyi yakalamak ve daha büyük bir dağıtımdan önce hızlı bir şekilde ele almak için erken hata algılamayı etkinleştirmeye yardımcı olur.

> [!NOTE]
> Günlük güvenlik bilgileri güncelleştirmelerini denetleme hakkında daha fazla bilgi için bkz[. Microsoft Defender Virüsten Koruma koruma güncelleştirmelerini zamanlama](manage-protection-update-schedule-microsoft-defender-antivirus.md). Güncelleştirmeler, uç nokta için bulut tabanlı koruma sağlanmıyor olsa bile yeni nesil korumanın yeni tehditlere karşı koruma sağlayabilmesini sağlar.

## <a name="microsoft-gradual-rollout-model"></a>Microsoft aşamalı dağıtım modeli

Aylık Defender güncelleştirmeleri için aşağıdaki aşamalı dağıtım modeli takip edilir:

1. İlk sürüm Beta kanalı abonelerine gönderilir.
2. Doğrulama, geri bildirim ve düzeltmelerden sonra aşamalı dağıtım sürecini kısıtlanmış bir şekilde başlatıp önce kanal abonelerini önizlemeye alıyoruz.
3. Ardından güncelleştirmeyi genel popülasyonun geri kalanına yayınlamaya devam ediyoruz ve ölçeği %10-100 oranında artırıyoruz.

Mühendislerimiz, gerektiğinde bir düzeltme oluşturmak için etkileri sürekli olarak izler ve sorunları yükseltir.

## <a name="how-to-customize-your-internal-deployment-process"></a>İç dağıtım işleminizi özelleştirme

Makineleriniz Windows Update Defender güncelleştirmelerini alıyorsa aşamalı dağıtım işlemi bazı makinelerinizin Defender güncelleştirmelerini diğerlerinden daha erken almasına neden olabilir. Aşağıdaki bölümde, güncelleştirme kanalı yapılandırmasından yararlanarak otomatik güncelleştirmelerin belirli cihaz gruplarına farklı şekilde akmasını sağlayacak bir stratejinin nasıl tanımlanacağı açıklanmaktadır.

> [!NOTE]
> Kendi aşamalı sürümünüzü planlarken, lütfen her zaman önizlemeye ve hazırlanmış kanallara abone olan cihazların bir seçimine sahip olduğunuzdan emin olun. Bu, hem kuruluşunuza hem de Microsoft'a ortamınıza özgü sorunları engelleme veya bulma ve düzeltme fırsatı sağlar.

Windows Sunucu Güncelleştirme Hizmetleri (WSUS) veya Microsoft Endpoint Configuration Manager (MECM) gibi güncelleştirmeleri alan makineler için, tüm Windows güncelleştirmeleri için seçenekler de dahil olmak üzere daha fazla seçenek sağlanır Uç Nokta için Microsoft Defender.

- Güncelleştirmelerin dağıtımını ve uygulamasını yönetmek için WSUS, MECM gibi bir çözümün nasıl kullanılacağı hakkında daha fazla bilgi için [bkz. Microsoft Defender Virüsten Koruma güncelleştirmeleri yönetme ve temelleri uygulama - Windows güvenlik](manage-updates-baselines-microsoft-defender-antivirus.md#product-updates).

## <a name="update-channels-for-monthly-updates"></a>Aylık güncelleştirmeler için kanalları güncelleştirme

Bir makinenin aylık altyapı ve platform güncelleştirmelerini aldığı tempoyu tanımlamak için bir makineyi güncelleştirme kanalına atayabilirsiniz.

Güncelleştirmeleri yapılandırma hakkında daha fazla bilgi için bkz. [Microsoft Defender güncelleştirmeleri için özel bir aşamalı dağıtım işlemi oluşturma](configure-updates.md).

Aşağıdaki güncelleştirme kanalları kullanılabilir:

<br>

****

|Kanal adı|Açıklama|Uygulama|
|---|---|---|
|Beta Kanalı - Yayın Öncesi|Güncelleştirmeleri diğerlerinden önce test etme|Yeni aylık güncelleştirmeleri ilk alan cihazlar bu kanala ayarlanır. Sorunları tanımlama ve Microsoft'a raporlamaya katılmak için Beta Kanalı'na tıklayın. Windows Insider Programı cihazlar varsayılan olarak bu kanala abonedir. Yalnızca test ortamlarında kullanım için.|
|Geçerli Kanal (Önizleme)|Geçerli Kanal güncelleştirmelerini aşamalı sürüm sırasında **daha önce** alın|Bu kanala ayarlanan cihazlara, aşamalı sürüm döngüsü boyunca en erken güncelleştirmeler sunulacaktır. Ön üretim/doğrulama ortamları için önerilir.|
|Geçerli Kanal (Aşamalı)|Aşamalı sürüm sırasında Güncel Kanal güncelleştirmelerini daha sonra alın|Cihazlara daha sonra aşamalı sürüm döngüsü sırasında güncelleştirmeler sunulacaktır. Cihaz popülasyonunuzun küçük, temsili bir bölümüne (%10) başvurmanız önerilir.|
|Geçerli Kanal (Geniş)|Aşamalı sürümün sonunda güncelleştirmeleri alma|Cihazlara yalnızca aşamalı sürüm döngüsü tamamlandıktan sonra güncelleştirmeler sunulacaktır. Üretim popülasyonunuzda (~%10-100) geniş bir cihaz kümesine uygulanması önerilir.|
|Kritik: Gecikme Süresi|Defender güncelleştirmelerini geciktirme|Cihazlara 48 saat gecikmeli güncelleştirmeler sunulacaktır. Yalnızca sınırlı güncelleştirmeler alan veri merkezi makineleri için en iyi yöntemdir. Yalnızca kritik ortamlar için önerilir.|
|(varsayılan)||Bu ilkeyi devre dışı bırakır veya yapılandırmazsanız cihaz Geçerli Kanal'da kalır (Varsayılan): Aşamalı yayın döngüsü sırasında otomatik olarak güncel kalın. Çoğu cihaz için uygundur.|
|

### <a name="update-channels-for-daily-updates"></a>Günlük güncelleştirmeler için kanalları güncelleştirme

Ayrıca, bir makineyi günlük güncelleştirmeleri aldığı tempoyu tanımlamak için kanala atayabilirsiniz. Aylık işlemden farklı olarak Beta kanalı olmadığını ve bu aşamalı yayın döngüsünün günde birden çok kez gerçekleştiğini unutmayın.

<br>

****

|Kanal adı|Açıklama|Uygulama|
|---|---|---|
|Geçerli Kanal (Aşamalı)|Aşamalı sürüm sırasında Güncel Kanal güncelleştirmelerini daha sonra alın|Cihazlara daha sonra aşamalı sürüm döngüsü sırasında güncelleştirmeler sunulacaktır. Cihaz popülasyonunuzun küçük, temsili bir bölümüne (%10) başvurmanız önerilir.|
|Geçerli Kanal (Geniş)|Aşamalı sürümün sonunda güncelleştirmeleri alma|Cihazlara aşamalı sürüm döngüsünden sonra güncelleştirmeler sunulacaktır. Yalnızca sınırlı güncelleştirmeler alan veri merkezi makineleri için en iyi yöntemdir. Not: Bu ayar tüm Defender güncelleştirmeleri için geçerlidir.|
|(varsayılan)||Bu ilkeyi devre dışı bırakır veya yapılandırmazsanız cihaz Geçerli Kanal'da kalır (Varsayılan): Aşamalı yayın döngüsü sırasında otomatik olarak güncel kalın. Çoğu cihaz için uygundur|
|

> [!NOTE]
> Gecikme süresinden yararlanarak yerine en yeni imzaya bir güncelleştirme uygulamak isterseniz, önce bu ilkeyi kaldırmanız gerekir.

## <a name="update-guidance"></a>Güncelleştirme kılavuzu

Çoğu durumda, Windows Update kullanılırken önerilen yapılandırma uç noktaların geldikçe aylık Defender güncelleştirmelerini almasına ve uygulamasına izin vermektir. Bu, koruma ile ortaya çıkarabilecekleri değişikliklerle ilişkili olası etki arasında en iyi dengeyi sağlar.

Otomatik Defender güncelleştirmelerinin daha denetimli aşamalı dağıtımına ihtiyaç duyulan ortamlar için dağıtım gruplarıyla ilgili bir yaklaşımı göz önünde bulundurun:

1. Windows Insider programına katılın veya beta kanalına bir cihaz grubu atayın.
2. Yeni güncelleştirmeleri erken almak için önizleme kanalını (genellikle doğrulama ortamları) kabul eden bir pilot grup belirleyin.
3. Aşamalı kanaldan aşamalı dağıtım sırasında daha sonra güncelleştirmeleri alan bir makine grubu belirleyin. Genellikle bu, popülasyonun yaklaşık %10'unu temsil eder.
4. Aşamalı sürüm döngüsü tamamlandıktan sonra güncelleştirmeleri alan bir makine grubu belirleyin. Bunlar genellikle önemli üretim sistemleridir.

Cihazların geri kalanı için varsayılan ayar, Microsoft aşamalı dağıtım işlemi sırasında gelen yeni güncelleştirmeleri almaktır ve başka yapılandırma gerekmez.

Bu modeli benimseme:

- Üretim ortamına ulaşmadan önce erken sürümleri test etmenizi sağlar
- Üretim ortamının hala düzenli güncelleştirmeler aldığından ve kritik tehditlere karşı koruma sağladığından emin olun.

## <a name="management-tools"></a>Yönetim araçları

Aylık güncelleştirmeler için kendi özel aşamalı dağıtım işleminizi oluşturmak için aşağıdaki araçları kullanabilirsiniz:

- Grup ilkesi
- Microsoft Endpoint Manager
- PowerShell

Bu araçların nasıl kullanılacağı hakkında ayrıntılı bilgi için bkz. [Microsoft Defender güncelleştirmeleri için özel bir aşamalı dağıtım işlemi oluşturma](configure-updates.md).

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)