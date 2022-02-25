---
title: Cihaz başına değerlendirme yöntemlerini ve özelliklerini dışarı aktarma
description: "\"Veri\" verisi alan API'ler hakkında Tehdit ve Güvenlik Açığı Yönetimi sağlar. Farklı türde veriler almak için farklı API çağrıları vardır. Genel olarak her API çağrısı, organizasyonlar için gerekli verileri içerir. Veri miktarı büyük olabilir, bu nedenle alınanın iki yolu vardır"
keywords: api, api'ler, dışarı aktarma değerlendirmesi, cihaz değerlendirme başına değerlendirme, makine değerlendirme başına güvenlik açığı değerlendirmesi raporu, cihaz açığı değerlendirmesi, cihaz güvenlik açığı raporu, güvenli yapılandırma değerlendirmesi, güvenli yapılandırma raporu, yazılım açıkları değerlendirmesi, yazılım güvenlik açığı raporu, makine tarafından güvenlik açığı raporu,
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: e820875a3350761824c3e4e67311e55507a9cb6f
ms.sourcegitcommit: 83df0be7144c9c5d606f70b4efa65369e86693d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2021
ms.locfileid: "62959661"
---
# <a name="export-assessment-methods-and-properties-per-device"></a>Cihaz başına değerlendirme yöntemlerini ve özelliklerini dışarı aktarma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

## <a name="api-description"></a>API açıklaması

Her cihaz temelinde veri alan API'ler Tehdit ve Güvenlik Açığı Yönetimi yöntemleri ve özellik ayrıntıları sağlar. Farklı türde veriler almak için farklı API çağrıları vardır. Genel olarak her API çağrısı, organizasyonlar için gerekli verileri içerir.

> [!Note]
>
> Aksi belirtilmedikçe, listelenen tüm dışarı aktarma değerlendirme yöntemleri tam dışarı **** aktarma ve **_cihaza göre_** (cihaz başına da **_adlandırılır) gösterilir_**.

Farklı tür bilgileri almak (dışarı aktarma) için kullanabileceğiniz üç API yöntemi vardır:

1. Güvenli yapılandırma değerlendirmesini dışarı aktarma

2. Yazılım envanteri değerlendirmesini dışarı aktarma

3. Yazılım açıkları değerlendirmesini dışarı aktarma

Her yöntem için, farklı türde veriler edinen farklı API çağrıları vardır. Veri miktarı büyük olduğundan, alınanın iki yolu vardır:

- **OData**  API, OData protokolüne göre organizasyon verilerinize Json yanıtları olarak tüm verileri çeker. Bu yöntem, _100 K'den az cihaza sahip küçük kuruluşlar için en iyisidir_. Yanıt sayfalandı, dolayısıyla sonraki sonuçları getirmek için \@yanıttan odata.nextLink alanını kullanabilirsiniz.

- **dosyalar aracılığıyla** Bu API çözümü, daha büyük miktarlarda verinin daha hızlı ve daha güvenilir bir şekilde çekmesini sağlar. Bu nedenle, 100 K'den fazla cihazı olan büyük kuruluşlar için önerilir. Bu API, kuruluşta yer alan tüm verileri dosya indir olarak çeker. Yanıt, Azure Veri Hizmetleri'nden tüm verileri indirmek için URL'leri Depolama. Bu API, azure verilerinden tüm verilerinizi aşağıdaki gibi Depolama sağlar:

  - Tüm kuruluş verilerinizle birlikte indirme URL'lerinin listesini almak için API'yi arayın.

  - İndirme URL'lerini kullanarak tüm dosyaları indirin ve verileri like gibi işin.

Toplanan veriler ( _OData_ kullanılarak veya dosyalar _yoluyla) geçerli_ durumunun geçerli anlık görüntüsü olur ve tarihi verileri içermez. Tarihi verileri toplamak için, müşterilerin verileri kendi veri depolamalarına kaydetmeleri gerekir.

## <a name="1-export-secure-configurations-assessment"></a>1. Güvenli yapılandırma değerlendirmesini dışarı aktarma

Cihaz başına tüm yapılandırmaları ve bunların durumunu verir.

### <a name="11-methods"></a>1.1 Yöntemler

Yöntem | Veri türü | Açıklama
:---|:---|:---
Güvenli yapılandırma değerlendirmesini **(OData) dışarı aktarma** | Cihaz koleksiyonuna göre yapılandırmanın güvenliğini sağlama. Bkz. [1.2 Özellikleri (OData)](#12-properties-odata) | Her benzersiz DeviceId, ConfigurationId bileşimi için bir giriş olan bir tablo döndürür. API, OData protokolüne göre organizasyon verilerinize Json yanıtları olarak tüm verileri çeker. Bu yöntem, 100 K'den az cihaza sahip küçük kuruluşlar için en iyisidir. Yanıt sayfalandı, dolayısıyla sonraki sonuçları getirmek için yanıttan @odata.nextLink alanını kullanabilirsiniz.
Güvenli yapılandırma değerlendirmesini **dışarı aktarma (dosyalar yoluyla)** | Cihaz koleksiyonuna göre yapılandırmanın güvenliğini sağlama. Bkz. [1.2 Özellikleri (OData)](#12-properties-odata) | Her benzersiz DeviceId, ConfigurationId bileşimi için bir giriş olan bir tablo döndürür. Bu API çözümü, daha büyük miktarlarda verinin daha hızlı ve daha güvenilir bir şekilde çekmesini sağlar. Bu nedenle, 100 K'den fazla cihazı olan büyük kuruluşlar için önerilir. Bu API, kuruluşta yer alan tüm verileri dosya indir olarak çeker. Yanıt, Azure Veri Hizmetleri'nden tüm verileri indirmek için URL'leri Depolama. Bu API, Azure verilerini şu şekilde Depolama indirmenize olanak sağlar: 1.  Tüm kuruluş verilerinizle birlikte indirme URL'lerinin listesini almak için API'yi arayın. 2.  İndirme URL'lerini kullanarak tüm dosyaları indirin ve verileri like gibi işin.

### <a name="12-properties-odata"></a>1.2 Özellikler (OData)

Özellik (Kimlik) | Veri türü | Açıklama
:---|:---|:---
ConfigurationCategory | dize | Yapılandırmanın ait olduğu kategori veya gruplama: Uygulama, işletim sistemi, Ağ, Hesaplar, Güvenlik denetimleri
ConfigurationId | dize | Belirli bir yapılandırma için benzersiz tanımlayıcı
ConfigurationImpact | dize | Yapılandırmanın etkisini genel yapılandırma puanına göre derecelendirildi (1-10)
ConfigurationName | dize | Yapılandırmanın görünen adı
ConfigurationSubcategory | dize | Yapılandırmanın ait olduğu alt kategori veya alt grup. Bu özellik, birçok durumda belirli özellikleri veya özellikleri açıklar.
DeviceId | dize | Hizmette cihaz için benzersiz tanımlayıcı.
DeviceName | dize | Cihazın tam etki alanı adı (FQDN).
IsApplicable | bool | Yapılandırmanın veya ilkenin uygun olup olmadığını gösterir
IsCompliant | bool | Yapılandırmanın veya ilkenin düzgün yapılandırıldığından emin olun
IsExpectedUserImpact | bool | Yapılandırmanın uygulanması kullanıcı üzerinde etki olup olmadığını gösterir
OSPlatform | dize | Cihazda çalışan işletim sisteminin platformu. Bu, Windows 10 ve Windows 7 gibi, aynı aile içindeki çeşitlemeler de dahil olmak üzere belirli işletim Windows gösterir. Ayrıntılar için TVm'de desteklenen işletim sistemleri ve platformlar'a bakın.
RbacGroupName | dize | Rol tabanlı erişim denetimi (RBAC) grubu. Bu cihaz hiçbir RBAC grubuna atanmamışsa, değer "Atanmamış" olur. Kuruluş hiçbir RBAC grubu içermese bile, değer "Yok" olur.
RecommendationReference | dize | Bu yazılımla ilgili öneri kimliğine başvuru.
Zaman damgası | dize | Yapılandırmanın cihazda en son ne zaman görüldü?

### <a name="13-properties-via-files"></a>1.3 Özellikler (dosyalar yoluyla)

Özellik (Kimlik) | Veri türü | Açıklama
:---|:---|:---
Dosyaları dışarı aktarma | arraystring\[\] | Kuruluşun geçerli anlık görüntüsünü tutan dosyalar için indirme URL'lerinin listesi.
GeneratedTime | dize | Dışarı aktarmanın oluşturulma zamanı.

## <a name="2-export-software-inventory-assessment"></a>2. Yazılım envanteri değerlendirmesini dışarı aktarma

Her bir cihaza tüm yüklü yazılımları ve ayrıntılarını verir.

### <a name="21-methods"></a>2.1 Yöntemler

Yöntem | Veri türü | Açıklama
:---|:---|:---
Yazılım envanteri değerlendirmesini **(OData) dışarı aktarma** | Cihaz koleksiyonuna göre yazılım envanteri. Bkz. [2.2 Özellikleri (OData)](#22-properties-odata) | Her benzersiz DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion bileşimi için bir giriş olan bir tablo döndürür. API, OData protokolüne göre organizasyon verilerinize Json yanıtları olarak tüm verileri çeker. Bu yöntem, 100 K'den az cihaza sahip küçük kuruluşlar için en iyisidir. Yanıt sayfalandı, dolayısıyla sonraki sonuçları getirmek için yanıttan @odata.nextLink alanını kullanabilirsiniz.
Yazılım envanteri değerlendirmesini **dışarı aktarma (dosyalar yoluyla)** | Cihaz dosyalarına göre yazılım envanteri. Bkz. [2.3 Özellikler (dosyalar aracılığıyla)](#23-properties-via-files) | Her benzersiz DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion bileşimi için bir giriş olan bir tablo döndürür. Bu API çözümü, daha büyük miktarlarda verinin daha hızlı ve daha güvenilir bir şekilde çekmesini sağlar. Bu nedenle, 100 K'den fazla cihazı olan büyük kuruluşlar için önerilir. Bu API, kuruluşta yer alan tüm verileri dosya indir olarak çeker. Yanıt, Azure Veri Kaynağı'Depolama'den tüm verileri indirmek için URL'leri Depolama. Bu API, Azure verilerini şu şekilde Depolama indirmenize olanak sağlar: 1.  Tüm kuruluş verilerinizle birlikte indirme URL'lerinin listesini almak için API'yi arayın. 2.  İndirme URL'lerini kullanarak tüm dosyaları indirin ve verileri like gibi işin.

### <a name="22-properties-odata"></a>2.2 Özellikler (OData)

Özellik (Kimlik) | Veri türü | Açıklama
:---|:---|:---
DeviceId | dize | Hizmette cihaz için benzersiz tanımlayıcı.
DeviceName | dize | Cihazın tam etki alanı adı (FQDN).
DiskPath'ler | Dizi[dize]  | Ürünün cihaza yük olduğuna dair disk kanıtı.
EndOfSupportDate | dize | Bu yazılım için desteğin destek tarihi vardır veya sona erer.
EndOfSupportStatus | dize | Destek durumu sonu. Şu olası değerleri içerebilir: Yok, EOS Sürümü, Yaklaşan EOS Sürümü, EOS Yazılımı, Yaklaşan EOS Yazılımı.
Kimlik | dize | Kayıt için benzersiz tanımlayıcı.
NumberOfWeaknesses | int|Bu cihaz üzerinde bu yazılıma olan zayıf sayı
OSPlatform | dize | Cihazda çalışan işletim sisteminin platformu. Bu, Windows 10 ve Windows 7 gibi, aynı aile içindeki çeşitlemeler de dahil olmak üzere belirli işletim Windows gösterir. Ayrıntılar için TVm'de desteklenen işletim sistemleri ve platformlar'a bakın.
RbacGroupName | dize | Rol tabanlı erişim denetimi (RBAC) grubu. Bu cihaz hiçbir RBAC grubuna atanmamışsa, değer "Atanmamış" olur. Kuruluş hiçbir RBAC grubu içermese bile, değer "Yok" olur.
RegistryPaths | Dizi[dize] | Ürünün cihaza yük olduğuna dair kayıt defteri kanıtı.
SoftwareFirstSeenTimestamp | dize | Bu yazılım ilk kez cihazda görüldü.
SoftwareName | dize | Yazılım ürününün adı.
SoftwareVendor | dize | Yazılım satıcısının adı.
SoftwareVersion | dize | Yazılım ürününün sürüm numarası.

### <a name="23-properties-via-files"></a>2.3 Özellikler (dosyalar aracılığıyla)

Özellik (Kimlik) | Veri türü | Açıklama
:---|:---|:---
Dosyaları dışarı aktarma | arraystring\[\] | Kuruluşun geçerli anlık görüntüsünü tutan dosyalar için indirme URL'lerinin listesi.
GeneratedTime | dize | Dışarı aktarmanın oluşturulma zamanı.

## <a name="3-export-software-vulnerabilities-assessment"></a>3. Yazılım açıkları değerlendirmesini dışarı aktarma

Bir cihazla ilgili bilinen tüm güvenlik açıklarını ve bu güvenlik açıklarını tüm cihazlara yönelik olarak verir.

### <a name="31-methods"></a>3.1 Yöntemler

Yöntem | Veri türü | Açıklama
:---|:---|:---
Yazılım açıkları **değerlendirmesini (OData) dışarı aktarma** | Araştırma koleksiyonu Bkz: [3.2 Özellikleri (OData)](#32-properties-odata) | DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion,ArdId gibi her benzersiz bileşimi için bir giriş olan bir tablo döndürür. API, OData protokolüne göre organizasyon verilerinize Json yanıtları olarak tüm verileri çeker. Bu yöntem, 100 K'den az cihaza sahip küçük kuruluşlar için en iyisidir. Yanıt sayfalandı, dolayısıyla sonraki sonuçları getirmek için yanıttan @odata.nextLink alanını kullanabilirsiniz.
Yazılım açıkları **değerlendirmesini dışarı aktarma (dosyalar yoluyla)** | Araştırma varlığı Bkz. [3.3 Özellikleri (dosyalar yoluyla)](#33-properties-via-files) | DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion,ArdId gibi her benzersiz bileşimi için bir giriş olan bir tablo döndürür. Bu API çözümü, daha büyük miktarlarda verinin daha hızlı ve daha güvenilir bir şekilde çekmesini sağlar. Bu nedenle, 100 K'den fazla cihazı olan büyük kuruluşlar için önerilir. Bu API, kuruluşta yer alan tüm verileri dosya indir olarak çeker. Yanıt, Azure Veri Hizmetleri'nden tüm verileri indirmek için URL'leri Depolama. Bu API, Azure verilerini şu şekilde Depolama indirmenize olanak sağlar: 1.  Tüm kuruluş verilerinizle birlikte indirme URL'lerinin listesini almak için API'yi arayın. 2.  İndirme URL'lerini kullanarak tüm dosyaları indirin ve verileri like gibi işin.

### <a name="32-properties-odata"></a>3.2 Özellikler (OData)

Özellik (Kimlik) | Veri türü | Açıklama
:---|:---|:---
YerkarakDiyaKimlik | dize | Ortak Güvenlik Açıkları ve SALDıRıLAR (ALI) sistemi kapsamındaki güvenlik açığına atanan benzersiz tanımlayıcı.
CvssScore | dize | DEMİ'nin CVSS puanı.
DeviceId | dize | Hizmette cihaz için benzersiz tanımlayıcı.
DeviceName | dize | Cihazın tam etki alanı adı (FQDN).
DiskPath'ler | Arraystring\[\] | Ürünün cihaza yük olduğuna dair disk kanıtı.
ExploitabilityLevel | dize | Bu güvenlik açığının açıkları açıklığı düzeyi (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)
FirstSeenTimestamp | dize | Bu ürünün 1. TIR'ı cihazda ilk kez görüldü.
Kimlik | dize | Kayıt için benzersiz tanımlayıcı.
LastSeenTimestamp | dize | EN son YALNıZ BIRAYI cihaz üzerinde görüldü.
OSPlatform | dize | Cihazda çalışan işletim sisteminin platformu. Bu, Windows 10 ve Windows 7 gibi, aynı aile içindeki çeşitlemeler de dahil olmak üzere belirli işletim Windows gösterir. Ayrıntılar için TVm'de desteklenen işletim sistemleri ve platformlar'a bakın.
RbacGroupName | dize | Rol tabanlı erişim denetimi (RBAC) grubu. Bu cihaz hiçbir RBAC grubuna atanmamışsa, değer "Atanmamış" olur. Kuruluş hiçbir RBAC grubu içermese bile, değer "Yok" olur.
RecommendationReference | dize | Bu yazılımla ilgili öneri kimliğine başvuru.
RecommendedSecurityUpdate | dize | Yazılım satıcısı tarafından güvenlik açığı için sağlanan güvenlik güncelleştirmelerinin adı veya açıklaması.
RecommendedSecurityUpdateId | dize | İlgili kılavuz veya bilgi bankası (KB) makalelerine yönelik geçerli güvenlik güncelleştirmelerinin veya tanımlayıcının tanımlayıcısı
Kayıt Defteri Yolları Arraystring\[\] | Ürünün cihaza yük olduğuna dair kayıt defteri kanıtı.
SoftwareName | dize | Yazılım ürününün adı.
SoftwareVendor | dize | Yazılım satıcısının adı.
SoftwareVersion | dize | Yazılım ürününün sürüm numarası.
VulnerabilitySeverityLevel | dize | CVSS puanı ve tehdit ortamını etkileyen dinamik etmenlere dayalı olarak güvenlik açığına atanan önem düzeyi.

### <a name="33-properties-via-files"></a>3.3 Özellikler (dosyalar yoluyla)

Özellik (Kimlik) | Veri türü | Açıklama
:---|:---|:---
Dosyaları dışarı aktarma | arraystring\[\]  | Kuruluşun geçerli anlık görüntüsünü tutan dosyalar için indirme URL'lerinin listesi.
GeneratedTime | dize | Dışarı aktarmanın oluşturulma zamanı.

## <a name="see-also"></a>Ayrıca bkz.

- [Cihaz başına güvenli yapılandırma değerlendirmesini dışarı aktarma](get-assessmnt-secure-cfg.md)

- [Cihaz başına yazılım envanteri değerlendirmesini dışarı aktarma](get-assessmnt-software-inventory.md)

- [Cihaz başına yazılım açıkları değerlendirmesini dışarı aktarma](get-assessmnt-software-vulnerabilities.md)

Diğer ilgili

- [Risk tabanlı tehdit & güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)

- [Organizasyon güvenlik açıkları](tvm-weaknesses.md)
