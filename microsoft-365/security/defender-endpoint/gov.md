---
title: Kamu görevlisi müşterilere yönelik Uç Nokta için Microsoft Defender
description: US Government müşterilerinin gereksinimlerine ve özelliklerine yönelik Uç Nokta için Microsoft Defender hakkında bilgi edinin
keywords: government, gcc, high, requirements, capabilities, defender, Uç Nokta için Microsoft Defender, endpoint, dod
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
ms.openlocfilehash: 51f9c373a68e34ffafa5c3763b8efe77fa2c6146
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098746"
---
# <a name="microsoft-defender-for-endpoint-for-us-government-customers"></a>Kamu görevlisi müşterilere yönelik Uç Nokta için Microsoft Defender

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Azure US Government ortamında yerleşik olarak bulunan US Government müşterileri için Uç Nokta için Microsoft Defender, Azure Ticari'de Uç Nokta için Defender ile aynı temel teknolojileri kullanır.

Bu teklif GCC, GCC High ve DoD müşterileri tarafından kullanılabilir ve ticari sürümle aynı önleme, algılama, araştırma ve düzeltmeyi temel alır. Ancak, bu teklif için özelliklerin kullanılabilirliği ile ilgili bazı farklılıklar vardır.

> [!NOTE]
> Ticari uç nokta için Defender kullanan bir GCC müşterisiyseniz lütfen genel belge sayfalarına bakın.

## <a name="licensing-requirements"></a>Lisans gereksinimleri

US Government müşterileri için Uç Nokta için Microsoft Defender aşağıdaki Microsoft toplu lisanslama tekliflerinden birini gerektirir:

### <a name="desktop-licensing"></a>Masaüstü lisanslama

<br />

****

|GCC|yüksek GCC|Dod|
|---|---|---|
|Microsoft 365 GCC G5|GCC High için Microsoft 365 E5|DOD için Microsoft 365 G5|
|Microsoft 365 G5 Güvenlik GCC|GCC High için Microsoft 365 G5 Güvenliği|DOD için Microsoft 365 G5 Güvenliği|
|Uç Nokta için Microsoft Defender - GCC|GCC High için Uç Nokta için Microsoft Defender|DOD için Uç Nokta için Microsoft Defender|
|E5 GCC Windows 10 Enterprise|GCC High için Windows 10 Enterprise E5|DOD için E5 Windows 10 Enterprise|
|

### <a name="server-licensing"></a>Sunucu lisanslama

<br />

****

|GCC|yüksek GCC|Dod|
|---|---|---|
|Uç Nokta için Microsoft Defender Server GCC|GCC High için Uç Nokta için Microsoft Defender Sunucusu|DOD için Uç Nokta için Microsoft Defender Sunucusu|
|Sunucular için Microsoft Defender|Sunucular için Microsoft Defender - Kamu|Sunucular için Microsoft Defender - Kamu|
|

## <a name="portal-urls"></a>Portal URL'leri

US Government müşterileri için Uç Nokta için Microsoft Defender portalı URL'leri şunlardır:

<br />

****

|Müşteri türü|Portal URL'si|
|---|---|
|GCC|<https://security.microsoft.com>|
|yüksek GCC|<https://security.microsoft.us>|
|Dod|<https://security.apps.mil>|
|
> [!NOTE]
> GCC bir müşteriyseniz ve Uç Nokta için Microsoft Defender ticariden GCC geçiş sürecinde Uç Nokta için Microsoft Defender ticari verilerinize erişmek için kullanınhttps://transition.security.microsoft.com.

## <a name="endpoint-versions"></a>Uç nokta sürümleri

### <a name="standalone-os-versions"></a>Tek başına işletim sistemi sürümleri

Aşağıdaki işletim sistemi sürümleri desteklenir:

<br />

****

İşletim sistemi sürümü|GCC|yüksek GCC|Dod
:---|:---:|:---:|:---:
Windows 11|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows 10, sürüm 21H1 ve üzeri|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows 10, sürüm 20H2 ([KB4586853](https://support.microsoft.com/help/4586853) <sup>1</sup> ile)|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows 10, sürüm 2004 ([KB4586853](https://support.microsoft.com/help/4586853) <sup>1</sup> ile)|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows 10, sürüm 1909 ([KB4586819 1](https://support.microsoft.com/help/4586819) <sup></sup>ile)|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows 10, sürüm 1903 ([KB4586819 1](https://support.microsoft.com/help/4586819) <sup></sup>ile)|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows 10, sürüm 1809 ([KB4586839](https://support.microsoft.com/help/4586839) <sup>1</sup> ile)|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows 10, sürüm 1803 ([KB4598245](https://support.microsoft.com/help/4598245) <sup>1</sup> ile)|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows 10, sürüm 1709|![Hayır.](images/svg/check-no.svg) <br /> Not: Desteklenmez|![Evet](images/svg/check-yes.svg)[, KB4499147](https://support.microsoft.com/help/4499147) <sup>1</sup> ile <br /> Not: [Kullanım dışı,](/lifecycle/announcements/revised-end-of-service-windows-10-1709) lütfen yükseltin|![Hayır](images/svg/check-no.svg) <br /> Not: Desteklenmez
Windows 10, sürüm 1703 ve öncesi|![Hayır.](images/svg/check-no.svg) <br /> Not: Desteklenmez|![Hayır](images/svg/check-no.svg) <br /> Not: Desteklenmez|![Hayır](images/svg/check-no.svg) <br /> Not: Desteklenmez
Windows Server 2022|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows Server 2019 ([KB4586839](https://support.microsoft.com/help/4586839) <sup>1</sup> ile)|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
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
> <sup>1</sup> Uç Nokta için Defender'ı doğru ortama yapılandırmak için cihaz eklemeden önce düzeltme ekinin dağıtılması gerekir.
>
> <sup>2</sup> [Windows 2016 ve 2012 R2 için birleşik modern çözüm](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution) hakkında bilgi edinin. Sunucularınızı daha önce MMA kullanarak yüklediyseniz, yeni çözüme geçiş yapmak için [Sunucu geçişi](server-migration.md) bölümünde sağlanan yönergeleri izleyin.
>
> <sup>3</sup> [Microsoft Monitoring Agent](onboard-downlevel.md#install-and-configure-microsoft-monitoring-agent-mma) kullanırken [kurulum sihirbazını](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-setup-wizard) kullanıyorsanız veya [komut satırı](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-command-line) veya [betik](/azure/log-analytics/log-analytics-windows-agents#install-agent-using-dsc-in-azure-automation) kullanıyorsanız "Azure Bulutu" altında "Azure ABD Kamu" seçeneğini belirlemeniz gerekir. "OPINSIGHTS_WORKSPACE_AZURE_CLOUD_TYPE" parametresini 1 olarak ayarlayın. <br /> Desteklenen en düşük MMA sürümü 10.20.18029 'dir (Mart 2020).

### <a name="os-versions-when-using-microsoft-defender-for-servers"></a>Sunucular için Microsoft Defender kullanırken işletim sistemi sürümleri

[Sunucular için Microsoft Defender](/azure/security-center/security-center-wdatp) kullanılırken aşağıdaki işletim sistemi sürümleri desteklenir:

<br />

****

İşletim sistemi sürümü|GCC|yüksek GCC|Dod
:---|:---:|:---:|:---:
Windows Server 2022|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows Server 2019|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows Server 2016|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows Server 2012 R2|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
Windows Server 2008 R2 SP1|![Evet.](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)
|

## <a name="required-connectivity-settings"></a>Gerekli bağlantı ayarları

Ara sunucu veya güvenlik duvarı varsayılan olarak tüm trafiği engelliyorsa ve yalnızca belirli etki alanlarının geçmesine izin veriliyorsa, indirilebilir sayfada listelenen etki alanlarını izin verilen etki alanları listesine ekleyin.

Aşağıdaki indirilebilir elektronik tablo, ağınızın bağlanabilmesi gereken hizmetleri ve bunların ilişkili URL'lerini listeler. Bu URL'lere erişimi reddedecek güvenlik duvarı veya ağ filtreleme kuralı olmadığını doğrulayın veya bunlar için özel olarak bir *izin verme* kuralı oluşturun.

|Etki alanları listesinin elektronik tablosu| Açıklama|
|---|---|
|Ticari müşteriler için Uç Nokta için Microsoft Defender URL listesi| Ticari müşteriler için hizmet konumları, coğrafi konumlar ve işletim sistemi için belirli DNS kayıtlarının elektronik tablosu. <p> [Elektronik tabloyu buradan indirin.](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)
| Gov/GCC/DoD için Uç Nokta için Microsoft Defender URL listesi | Gov/GCC/DoD müşterileri için hizmet konumları, coğrafi konumlar ve işletim sistemi için belirli DNS kayıtlarının elektronik tablosu. <p> [Elektronik tabloyu buradan indirin.](https://download.microsoft.com/download/6/a/0/6a041da5-c43b-4f17-8167-79dfdc10507f/mde-urls-gov.xlsx)

Daha fazla bilgi için bkz. [Cihaz ara sunucusu ve İnternet bağlantı ayarlarını yapılandırma](configure-proxy-internet.md).

> [!NOTE]
> Elektronik tablo ticari URL'ler de içeriyor, "US Gov" sekmelerini denetlediğinizden emin olun.
>
> Filtreleme sırasında"US Gov" olarak etiketlenen kayıtları ve coğrafya sütununun altındaki belirli bulutunuzu arayın.

## <a name="api"></a>API

[API belgelerimizde](apis-intro.md) listelenen genel URI'ler yerine aşağıdaki URI'leri kullanmanız gerekir:

<br />

****

|Uç nokta türü|GCC|GCC Yüksek & DoD|
|---|---|---|
|Oturum açma|`https://login.microsoftonline.com`|`https://login.microsoftonline.us`|
|Uç Nokta için Defender API'si|`https://api-gcc.securitycenter.microsoft.us`|`https://api-gov.securitycenter.microsoft.us`|
|SİEM|`https://wdatp-alertexporter-us.gcc.securitycenter.windows.us`|`https://wdatp-alertexporter-us.securitycenter.windows.us`|
|

## <a name="feature-parity-with-commercial"></a>Ticari özellik eşlik

ABD Kamu müşterileri için Uç Nokta için Defender, ticari teklifle tam eşliğe sahip değildir. Hedefimiz tüm ticari özellikleri ve işlevleri ABD Kamu müşterilerimize sunmak olsa da, henüz vurgulamak istediğimiz bazı özellikler mevcut değildir.

Bilinen boşluklar şunlardır:

<br />

****

|Özellik adı|GCC|yüksek GCC|Dod|
|---|:---:|:---:|:---:|
|Ağ değerlendirmeleri|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|
|Ağ bulma|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|
|Raporlar: Cihaz Denetimi, Cihaz durumu, Güvenlik Duvarı|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|
|Web içeriği filtreleme|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|
  

[Mobile Threat Defense (Android & iOS'ta Uç Nokta için Microsoft Defender)](mtd.md) için özellikler ve bilinen boşluklar şunlardır:

<br />

****

|Özellik adı|GCC|yüksek GCC|Dod|
|---|:---:|:---:|:---:|
|Web Koruması (Kimlik Avı önleme ve özel göstergeler)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|
|Kötü Amaçlı YazılımDan Koruma (Yalnızca Android)|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|
|Jailbreak Algılama (iOS-Only)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|
|Koşullu Erişim/Koşullu Başlatma|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|
|MAM desteği|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|
|Gizlilik Denetimleri|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|![Evet](images/svg/check-yes.svg)|
|Tehdit ve Güvenlik Açığı Yönetimi (TVM)|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|![Hayır](images/svg/check-no.svg) Geliştirme aşamasında|
  

