---
title: ABD Kamu müşterileri için Uç Nokta için Microsoft Defender
description: ABD Kamu müşterileri için Uç Nokta için Microsoft Defender gereksinimleri ve özellikleri hakkında bilgi
keywords: kamu, gcc, yüksek, gereksinimler, özellikler, defender, Uç Nokta için Microsoft Defender, uç nokta, dod
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 03d4d22bdce9f18b4883437215ea5cba50b3868e
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681358"
---
# <a name="microsoft-defender-for-endpoint-for-us-government-customers"></a>ABD Kamu müşterileri için Uç Nokta için Microsoft Defender

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Azure US Government ortamında yerleşik olarak yer alan US Government müşterileri için Uç Nokta için Microsoft Defender, Azure Ticari Uç Nokta için Defender ile aynı temel alınan teknolojileri kullanır.

Bu teklif GCC, GCC High ve DoD müşterilerine sunulmaktadır ve ticari sürümle aynı engelleme, algılama, soruşturma ve düzeltmelerden temel alındı. Bununla birlikte, bu teklifin özelliklerinde bazı farklılıklar vardır.

> [!NOTE]
> Ticari Amaçlı Uç nokta GCC Defender kullanan bir müşteriysiniz, lütfen genel belge sayfalarına bakın.

## <a name="licensing-requirements"></a>Lisans gereksinimleri

US Government müşterileri için Uç Nokta için Microsoft Defender için aşağıdaki Microsoft toplu lisans tekliflerinden birini gerektirir:

### <a name="desktop-licensing"></a>Masaüstü lisansı

<br />

****

|GCC|GCC Yüksek|DoD|
|---|---|---|
|Microsoft 365 GCC G5|Microsoft 365 E5 High için GCC.|MICROSOFT 365 için G5|
|Microsoft 365 G5 Güvenlik GCC|Microsoft 365 G5 Security for GCC High|Microsoft 365 DOD için G5 Güvenliği|
|Uç Nokta için Microsoft Defender - GCC|GCC High uç noktası için Microsoft Defender|DOD için Uç Nokta için Microsoft Defender|
|Windows 10 Enterprise E5 GCC|Windows 10 Enterprise yüksek için E5 GCC|dod Windows 10 Enterprise E5|
|

### <a name="server-licensing"></a>Sunucu lisansı

<br />

****

|GCC|GCC Yüksek|DoD|
|---|---|---|
|Endpoint Server 2010 için Microsoft Defender GCC|GCC High için Endpoint Server için Microsoft Defender|DOD için Uç Nokta Sunucusu için Microsoft Defender|
|Sunucular için Microsoft Defender|Sunucular için Microsoft Defender - Kamu|Sunucular için Microsoft Defender - Kamu|
|

## <a name="portal-urls"></a>Portal URL'leri

ABD Kamu müşterileri için Uç Nokta portalı URL'leri için Microsoft Defender'ı aşağıda bulabilirsiniz:

<br />

****

|Müşteri türü|Portal URL'si|
|---|---|
|GCC|<https://security.microsoft.com>|
|GCC Yüksek|<https://security.microsoft.us>|
|DoD|<https://security.microsoft.us>|
|
> [!NOTE]
> GCC müşterisiysiniz ve Uç nokta ticari sürümü için Microsoft Defender'dan GCC'e taşıma sürecindeysanız, https://transition.security.microsoft.com Uç nokta ticari verileri için Microsoft Defender'ınıza erişmek için kullanın.

## <a name="endpoint-versions"></a>Uç nokta sürümleri

### <a name="standalone-os-versions"></a>Tek başına işletim sistemi sürümleri

Aşağıdaki işletim sistemi sürümleri destekle devam ediyor:

<br />

****

işletim sistemi sürümü|GCC|GCC Yüksek|DoD
:---|:---:|:---:|:---:
Windows 11|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows 10, sürüm 21H1 ve üzeri|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows 10 sürüm 20H2 ([KB4586853](https://support.microsoft.com/help/4586853) <sup>1 ile</sup>)|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows 10 Sürüm 2004 ([KB4586853](https://support.microsoft.com/help/4586853) <sup>1 ile</sup>)|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows 10 Sürüm 1909 ([KB4586819](https://support.microsoft.com/help/4586819) <sup>1 ile</sup>)|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows 10 Sürüm 1903 ([KB4586819](https://support.microsoft.com/help/4586819) <sup>1 ile</sup>)|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows 10, sürüm 1809 ([KB4586839](https://support.microsoft.com/help/4586839) <sup>1 ile</sup>)|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows 10 Sürüm 1803 ([KB4598245](https://support.microsoft.com/help/4598245) <sup>1 ile</sup>)|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows 10, sürüm 1709|![Hayır.](images/svg/check-no.svg) <br /> Not: Destek olmayacak|![[KB4499147](https://support.microsoft.com/help/4499147)](images/svg/check-yes.svg) <sup>1 ile Evet</sup> <br /> Not: [Kullanımdan silindi](/lifecycle/announcements/revised-end-of-service-windows-10-1709), lütfen yükseltin|![Hayır](images/svg/check-no.svg) <br /> Not: Destek olmayacak
Windows 10 1703 ve önceki sürümler|![Hayır.](images/svg/check-no.svg) <br /> Not: Destek olmayacak|![Hayır](images/svg/check-no.svg) <br /> Not: Destek olmayacak|![Hayır](images/svg/check-no.svg) <br /> Not: Destek olmayacak
Windows Server 2022|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows Server 2019 ([KB4586839](https://support.microsoft.com/help/4586839) <sup>1 ile</sup>)|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows Server 2016 (Modern) <sup>2</sup>|![Evet.](images/svg/check-yes.svg) <br /> Genel önizleme|![Evet](images/svg/check-yes.svg) <br /> Genel önizleme|![Evet](images/svg/check-yes.svg) <br /> Genel önizleme
Windows Server 2012 R2 (Modern) <sup>2</sup>|![Evet.](images/svg/check-yes.svg) <br /> Genel önizleme|![Evet](images/svg/check-yes.svg) <br /> Genel önizleme|![Evet](images/svg/check-yes.svg) <br /> Genel önizleme
Windows Server 2016 (Eski) <sup>3</sup>|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows Server 2012 R2 (Eski) <sup>3</sup>|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows Server 2008 R2 SP1 (Eski) <sup>3</sup>|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows 8.1 Enterprise (Eski) <sup>3</sup>|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows 8 Pro (Eski) <sup>3</sup>|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows 7 SP1 Enterprise (Eski) <sup>3</sup>|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows 7 SP1 Pro (Eski) <sup>3</sup>|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Linux|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
macOS|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Android|![Evet.](images/svg/check-yes.svg) <br /> Genel önizleme|![Evet](images/svg/check-yes.svg) <br /> Genel önizleme|![Evet](images/svg/check-yes.svg) <br /> Genel önizleme
iOS|![Evet.](images/svg/check-yes.svg) <br /> Genel önizleme|![Evet](images/svg/check-yes.svg) <br /> Genel önizleme|![Evet](images/svg/check-yes.svg) <br /> Genel önizleme
|

> [!NOTE]
> <sup>1</sup> Uç nokta için Defender'ı doğru ortama yapılandırmak üzere cihaz eklemeden önce düzeltme ekini dağıtılmış olmalıdır.
>
> <sup>2</sup> Windows [2012 R2 için birleşik modern çözüm hakkında bilgi edinmek için](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview): Sunucularınızı daha önce MMA kullanarak ekleme yaptıysanız, yeni çözüme geçiş için [Sunucu](server-migration.md) geçişi'de sağlanan yönergeleri izleyin.
>
> <sup>3</sup> [Microsoft Monitoring Agent](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) kurulum sihirbazını kullanıyorsanız veya komut satırı ya da betik kullanıyorsanız "Azure US Government" altında "Azure US Government"ı seçmeniz gerekir- "OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE" [](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line) parametresini 1 olarak [](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation) ayarlayın.[](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard) <br /> Desteklenen en düşük MMA sürümü 10.20.18029'dür (Mart 2020).

### <a name="os-versions-when-using-microsoft-defender-for-servers"></a>Sunucular için Microsoft Defender kullanırken işletim sistemi sürümleri

Sunucularda Microsoft Defender kullanılırken aşağıdaki [işletim sistemi sürümleri destek almaktadır](/azure/security-center/security-center-wdatp):

<br />

****

işletim sistemi sürümü|GCC|GCC Yüksek|DoD
:---|:---:|:---:|:---:
Windows Server 2022|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows Server 2019|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows Server 2016|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows Server 2012 R2|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows Server 2008 R2 SP1|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
|

## <a name="required-connectivity-settings"></a>Gerekli bağlantı ayarları

Bir ara sunucu veya güvenlik duvarı varsayılan olarak tüm trafiği engelliyorsa ve yalnızca belirli etki alanları üzerinden izin veriliyorsa, indirilebilir sayfada listelenen etki alanlarını izin verilen etki alanları listesine ekleyin.

Aşağıdaki indirilebilir elektronik tablo, ağ bağlantı kurabilirsiniz ve bu hizmetlerle ilişkilendirilmiş URL'leri listeler. Bu URL'lere erişimi reddedecek güvenlik duvarı veya ağ filtreleme kuralı olmadığını doğrulayın veya özel olarak onlar için *bir izin kuralı* oluşturun.

|Etki alanı listesinin elektronik tablosu| Açıklama|
|---|---|
| Gov/GCC/DoD müşterileri için Uç nokta URL listesi için Microsoft Defender | Gov/GCC/DoD müşterileri için hizmet konumları, coğrafi konumlar ve işletim sistemi için belirli DNS kayıtlarının elektronik tablosu. <p> [Elektronik tabloyu buradan indirin.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

Daha fazla bilgi için bkz [. Cihaz ara sunucusunu ve İnternet bağlantı ayarlarını yapılandırma](configure-proxy-internet.md).

> [!NOTE]
> Elektronik tablo ticari URL'ler de içeriyor. "US Gov" sekmelerini kontrol edin.
>
> Filtreyi görüntülerken, "ABD Gov" olarak etiketlenmiş kayıtları ve coğrafi sütun altında size özel bulutun kayıtlarına bakın.

## <a name="api"></a>API

[API](apis-intro.md) belgelerinde listelenen genel URL yerine, aşağıdaki URL'leri kullanasınız:

<br />

****

|Uç nokta türü|GCC|GCC High & DoD|
|---|---|---|
|Oturum açma|`https://login.microsoftonline.com`|`https://login.microsoftonline.us`|
|Uç Nokta API için Defender|`https://api-gcc.securitycenter.microsoft.us`|`https://api-gov.securitycenter.microsoft.us`|
|SIEM|`https://wdatp-alertexporter-us.gcc.securitycenter.windows.us`|`https://wdatp-alertexporter-us.securitycenter.windows.us`|
|

## <a name="feature-parity-with-commercial"></a>Ticari özellik eşlik

ABD Kamu müşterileri için Uç Nokta için Defender ticari teklifle tam olarak uygun değildir. TÜM ticari özellikleri ve işlevleri ABD Kamu müşterilerine sunmakla birlikte, henüz mevcut olmayan bazı özellikleri vurgulamak için çalışıyoruz.

Bunlar bilinen boşluklardır:

<br />

****

|Özellik adı|GCC|GCC Yüksek|DoD|
|---|:---:|:---:|:---:|
|Ağ değerlendirmeleri|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|
|Ağ bulma|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|
|Raporlar: Cihaz Denetimi, Cihaz durumu, Güvenlik Duvarı|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|
|Web içeriği filtreleme|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|
  

Mobil Tehdit Savunması [(Android ve iOS'ta Uç Nokta için Microsoft Defender) özellikleri ve bilinen & vardır](mtd.md):

<br />

****

|Özellik adı|GCC|GCC Yüksek|DoD|
|---|:---:|:---:|:---:|
|Web Koruması (Kimlik Avı Önleme ve özel göstergeler)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|
|Kötü Amaçlı Yazılımdan Koruma (Yalnızca Android)|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|
|Jailbreak Algılama (iOS-Only)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|
|Koşullu Erişim/Koşullu Başlatma|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|
|MAM desteği|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|
|Gizlilik Denetimleri|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|
|Tehdit ve Güvenlik Açığı Yönetimi (TVM)|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|
|Web içeriği filtreleme|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|
  

