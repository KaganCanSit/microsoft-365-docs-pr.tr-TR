---
title: Cihaz başına değerlendirme yöntemlerini ve özelliklerini dışarı aktarma
description: "\"Veri\" verisi alan API'ler hakkında Tehdit ve Güvenlik Açığı Yönetimi sağlar. Farklı türde veriler almak için farklı API çağrıları vardır. Genel olarak her API çağrısı, organizasyonlar için gerekli verileri içerir."
keywords: api, api'ler, dışarı aktarma değerlendirmesi, cihaz değerlendirme başına değerlendirme, makine değerlendirme başına güvenlik açığı değerlendirmesi raporu, cihaz açığı değerlendirmesi, cihaz güvenlik açığı raporu, güvenli yapılandırma değerlendirmesi, güvenli yapılandırma raporu, yazılım açıkları değerlendirmesi, yazılım güvenlik açığı raporu, makine tarafından güvenlik açığı raporu,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-jweston
author: jweston-1
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.custom: api
ms.openlocfilehash: c10f454919afc725b37537aa354fed05b95cb571
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2022
ms.locfileid: "63014039"
---
# <a name="export-assessment-methods-and-properties-per-device"></a>Cihaz başına değerlendirme yöntemlerini ve özelliklerini dışarı aktarma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="api-description"></a>API açıklaması

Cihaz başına veri alan API'ler hakkında Tehdit ve Güvenlik Açığı Yönetimi ve özellik ayrıntıları sağlar. Farklı türde veriler almak için farklı API çağrıları vardır. Genel olarak her API çağrısı, organizasyonlar için gerekli verileri içerir.

> [!NOTE]
> Aksi belirtilmedikçe, listelenen tüm dışarı aktarma değerlendirme yöntemleri tam dışarı **** aktarma ve **_cihaza göre_** (cihaz başına da **_adlandırılır) gösterilir_**.

Farklı tür bilgileri almak (dışarı aktarma) için dışarı aktarma değerlendirme API'lerini kullanabilirsiniz:

- [1. Güvenli yapılandırma değerlendirmesini dışarı aktarma](#1-export-secure-configurations-assessment)
- [2. Yazılım envanteri değerlendirmesini dışarı aktarma](#2-export-software-inventory-assessment)
- [3. Yazılım açıkları değerlendirmesini dışarı aktarma](#3-export-software-vulnerabilities-assessment)

Dışarı aktarma bilgi türlerine karşılık gelen API'ler 1, 2 ve 3. bölümde açıklanmıştır.

Her yöntemin farklı veri türlerini almak için farklı API çağrıları vardır. Veri miktarı büyük olduğundan, alınanın iki yolu vardır:

- **JSON yanıtı**  API, JSON yanıtları olarak tüm verileri kuruluş içinde çeker. Bu yöntem, _100 K'den az cihaza sahip küçük kuruluşlar için en iyisidir_. Yanıt sayfalandı, dolayısıyla sonraki sonuçları getirmek için \@yanıttan odata.nextLink alanını kullanabilirsiniz.

- **dosyalar aracılığıyla** Bu API çözümü, daha büyük miktarlarda verinin daha hızlı ve daha güvenilir bir şekilde çekmesini sağlar. Bu nedenle, 100 K'den fazla cihazı olan büyük kuruluşlar için önerilir. Bu API, kuruluşta yer alan tüm verileri dosya indir olarak çeker. Yanıt, Azure Veri Hizmetleri'nden tüm verileri indirmek için URL'leri Depolama. Bu API, Azure'dan tüm verilerinizi aşağıdaki gibi Depolama sağlar:
  - Tüm kuruluş verilerinizle birlikte indirme URL'lerinin listesini almak için API'yi arayın.
  - İndirme URL'lerini kullanarak tüm dosyaları indirin ve verileri like gibi işin.

'JSON yanıtı kullanılarak veya _dosyalar aracılığıyla_ ' _toplanan_ veriler geçerli durumun geçerli anlık görüntüsü olur. Tarihi veriler içermez. Tarihi verileri toplamak için, müşterilerin verileri kendi veri depolamalarına kaydetmeleri gerekir.

## <a name="1-export-secure-configurations-assessment"></a>1. Güvenli yapılandırma değerlendirmesini dışarı aktarma

Cihaz başına tüm yapılandırmaları ve bunların durumunu verir.

### <a name="11-methods"></a>1.1 Yöntemler

Yöntem|Veri türü|Açıklama
:---|:---|:---
Güvenli yapılandırma değerlendirmesini **dışarı aktarma (JSON yanıtı)**|Cihaz koleksiyonuna göre yapılandırmanın güvenliğini sağlama. Bkz. [1.2 Özellikler (JSON yanıtı)](#12-properties-json-response)|Her benzersiz DeviceId, ConfigurationId bileşimi için bir giriş olan bir tablo döndürür. API, JSON yanıtları olarak tüm verileri kuruluş içinde çeker. Bu yöntem, 100 K'den az cihaza sahip küçük kuruluşlar için en iyisidir. Yanıt sayfalandı, dolayısıyla sonraki sonuçları getirmek için yanıttan @odata.nextLink alanını kullanabilirsiniz.
Güvenli yapılandırma değerlendirmesini **dışarı aktarma (dosyalar yoluyla)**|Cihaz koleksiyonuna göre yapılandırmanın güvenliğini sağlama. Bkz. [1.3 Özellikler (dosyalar aracılığıyla)](#13-properties-via-files)|Her benzersiz DeviceId, ConfigurationId bileşimi için bir giriş olan bir tablo döndürür. Bu API çözümü, daha büyük miktarlarda verinin daha hızlı ve daha güvenilir bir şekilde çekmesini sağlar. Bu nedenle, 100 K'den fazla cihazı olan büyük kuruluşlar için önerilir. Bu API, kuruluşta yer alan tüm verileri dosya indir olarak çeker. Yanıt, Azure Veri Hizmetleri'nden tüm verileri indirmek için URL'leri Depolama. Bu API, Azure'dan tüm verilerinizi aşağıdaki gibi Depolama sağlar: <ol><li>Tüm kuruluş verilerinizle birlikte indirme URL'lerinin listesini almak için API'yi arayın.</li><li>İndirme URL'lerini kullanarak tüm dosyaları indirin ve verileri like gibi işin.</li></ol>

### <a name="12-properties-json-response"></a>1.2 Özellikler (JSON yanıtı)

Özellik (Kimlik)|Veri türü|Açıklama
:---|:---|:---
configurationCategory|Dize|Yapılandırmanın ait olduğu kategori veya gruplama: Uygulama, işletim sistemi, Ağ, Hesaplar, Güvenlik denetimleri.
configurationId|Dize|Belirli bir yapılandırma için benzersiz tanımlayıcı.
configurationImpact|Dize|Yapılandırmanın etkisini genel yapılandırma puanına (1-10) derecelendirilmiştir.
configurationName|Dize|Yapılandırmanın görünen adı.
configurationSubcategory|Dize|Yapılandırmanın ait olduğu alt kategori veya alt grup. Birçok durumda, belirli özellikler veya özellikler.
deviceId|Dize|Hizmette cihaz için benzersiz tanımlayıcı.
deviceName|Dize|Cihazın tam etki alanı adı (FQDN).
isApplicable|Boole|Yapılandırmanın mı yoksa ilkenin uygun olup olmadığını gösterir.
isCompliant|Boole|Yapılandırmanın veya ilkenin düzgün yapılandırıldığından emin olun.
isExpectedUserImpact|Boole|Yapılandırma uygulanırsa kullanıcının etkilendiğini gösterir.
osPlatform|Dize|Cihazda çalışan işletim sisteminin platformu. Windows 10 11 gibi, aynı aile içindeki çeşitlemelere sahip Windows 10 Windows. Ayrıntılar için TVM'de desteklenen işletim sistemleri ve platformlar'a bakın.
osVersion|Dize|cihazda çalışan işletim sisteminin belirli bir sürümü.
rbacGroupName|Dize|Rol tabanlı erişim denetimi (RBAC) grubu. Cihaz herhangi bir RBAC grubuna atanmamışsa, değer "Atanmamış" olur. Kuruluş hiçbir RBAC grubu içermese bile, değer "Yok" olur.
rbacGroupId|Dize|Rol tabanlı erişim denetimi (RBAC) grup kimliği.
recommendationReference|Dize|Yazılımla ilgili öneri kimliğine başvuru.
timestamp|Dize|Yapılandırmanın cihazda en son ne zaman görüldü?

### <a name="13-properties-via-files"></a>1.3 Özellikler (dosyalar yoluyla)

Özellik (Kimlik)|Veri türü|Açıklama
:---|:---|:---
Dosyaları dışarı aktarma|arraystring\[\]|Kuruluşun geçerli anlık görüntüsünü tutan dosyalar için indirme URL'lerinin listesi.
GeneratedTime|Dize|Dışarı aktarmanın oluşturulma zamanı.

## <a name="2-export-software-inventory-assessment"></a>2. Yazılım envanteri değerlendirmesini dışarı aktarma

Her bir cihaza tüm yüklü yazılımları ve ayrıntılarını verir.

### <a name="21-methods"></a>2.1 Yöntemler

|Yöntem|Veri türü|Açıklama|
|:---|:---|:---|
|Yazılım envanteri değerlendirmesini **dışarı aktarma (JSON yanıtı)**|Cihaz koleksiyonuna göre yazılım envanteri. Bkz. [2.2 Özellikler (JSON yanıtı)](#22-properties-json-response)|Her benzersiz DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion bileşimi için bir giriş olan bir tablo döndürür. API, JSON yanıtları olarak tüm verileri kuruluş içinde çeker. Bu yöntem, 100 K'den az cihaza sahip küçük kuruluşlar için en iyisidir. Yanıt sayfalandı, dolayısıyla sonraki sonuçları getirmek için yanıttan @odata.nextLink alanını kullanabilirsiniz. |
| Yazılım envanteri değerlendirmesini **dışarı aktarma (dosyalar yoluyla)**|Cihaz dosyalarına göre yazılım envanteri. Bkz. [2.3 Özellikler (dosyalar aracılığıyla)](#23-properties-via-files)|Her benzersiz DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion bileşimi için bir giriş olan bir tablo döndürür. Bu API çözümü, daha büyük miktarlarda verinin daha hızlı ve daha güvenilir bir şekilde çekmesini sağlar. Bu nedenle, 100 K'den fazla cihazı olan büyük kuruluşlar için önerilir. Bu API, kuruluşta yer alan tüm verileri dosya indir olarak çeker. Yanıt, Azure Veri Hizmetleri'nden tüm verileri indirmek için URL'leri Depolama. Bu API, Azure verilerini aşağıdaki gibi Depolama olanak sağlar: <ol><li>Kuruluş verilerinizle birlikte indirme URL'lerinin listesini almak için API'yi arayın</li><li>İndirme URL'lerini kullanarak dosyaları indirin ve verileri like gibi işin.</li></ol> |

### <a name="22-properties-json-response"></a>2.2 Özellikler (JSON yanıtı)

Özellik (Kimlik)|Veri türü|Açıklama
:---|:---|:---
DeviceId|Dize|Hizmette cihaz için benzersiz tanımlayıcı.
DeviceName|Dize|Cihazın tam etki alanı adı (FQDN).
DiskPath'ler|Dizi[dize]|Ürünün cihaza yük olduğuna dair disk kanıtı.
EndOfSupportDate|Dize|Bu yazılım için desteğin destek tarihi vardır veya sona erer.
EndOfSupportStatus|Dize|Destek durumu sonu. Şu olası değerleri içerebilir: Yok, EOS Sürümü, Yaklaşan EOS Sürümü, EOS Yazılımı, Yaklaşan EOS Yazılımı.
NumberOfWeaknesses|Int|Bu cihazla ilgili zayıf sayı.
OSPlatform|Dize|Cihazda çalışan işletim sisteminin platformu; Windows 10 ve Windows 11 gibi, aynı aile içindeki çeşitlemelere sahip belirli Windows. Ayrıntılar için TVm'de desteklenen işletim sistemleri ve platformlar'a bakın.
RbacGroupName|Dize|Rol tabanlı erişim denetimi (RBAC) grubu. Bu cihaz hiçbir RBAC grubuna atanmamışsa, değer "Atanmamış" olur. Kuruluş hiçbir RBAC grubu içermese bile, değer "Yok" olur.
rbacGroupId|Dize|Rol tabanlı erişim denetimi (RBAC) grup kimliği.
RegistryPaths|Dizi[dize]|Ürünün cihaza yük olduğuna dair kayıt defteri kanıtı.
SoftwareFirstSeenTimestamp|Dize|Bu yazılım ilk kez cihazda görüldü.
SoftwareName|Dize|Yazılım ürününün adı.
SoftwareVendor|Dize|Yazılım satıcısının adı.
SoftwareVersion|Dize|Yazılım ürününün sürüm numarası.

### <a name="23-properties-via-files"></a>2.3 Özellikler (dosyalar aracılığıyla)

Özellik (Kimlik)|Veri türü|Açıklama
:---|:---|:---
Dosyaları dışarı aktarma|arraystring\[\]|Kuruluşun geçerli anlık görüntüsünü tutan dosyalar için indirme URL'lerinin listesi.
GeneratedTime|Dize|Dışarı aktarmanın oluşturulma zamanı.

## <a name="3-export-software-vulnerabilities-assessment"></a>3. Yazılım açıkları değerlendirmesini dışarı aktarma

Bir cihazla ilgili bilinen tüm güvenlik açıklarını ve bu güvenlik açıklarını tüm cihazlara yönelik olarak verir.

### <a name="31-methods"></a>3.1 Yöntemler

Yöntem|Veri türü|Açıklama
:---|:---|:---
Yazılım açıkları değerlendirmesini **dışarı aktarma (JSON yanıtı)**|Araştırma koleksiyonu Bkz: [3.2 Özellikler (JSON yanıtı)](#32-properties-json-response)|DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion,ArdId gibi her benzersiz bileşimi için bir giriş olan bir tablo döndürür. API, JSON yanıtları olarak tüm verileri kuruluş içinde çeker. Bu yöntem, 100 K'den az cihaza sahip küçük kuruluşlar için en iyisidir. Yanıt sayfalandı, dolayısıyla sonraki sonuçları getirmek için yanıttan @odata.nextLink alanını kullanabilirsiniz.
Yazılım açıkları **değerlendirmesini dışarı aktarma (dosyalar yoluyla)**|Araştırma varlığı Bkz. [3.3 Özellikleri (dosyalar yoluyla)](#33-properties-via-files)|DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion,ArdId gibi her benzersiz bileşimi için bir giriş olan bir tablo döndürür. Bu API çözümü, daha büyük miktarlarda verinin daha hızlı ve daha güvenilir bir şekilde çekmesini sağlar. Bu nedenle, 100 K'den fazla cihazı olan büyük kuruluşlar için önerilir. Bu API, kuruluşta yer alan tüm verileri dosya indir olarak çeker. Yanıt, Azure Veri Hizmetleri'nden tüm verileri indirmek için URL'leri Depolama. Bu API, Azure'dan tüm verilerinizi aşağıdaki gibi Depolama sağlar: <ol><li>Tüm kuruluş verilerinizle birlikte indirme URL'lerinin listesini almak için API'yi arayın.</li><li>İndirme URL'lerini kullanarak tüm dosyaları indirin ve verileri like gibi işin.</li></ol>
**Delta dışarı aktarma** yazılım açıkları değerlendirmesi **(JSON yanıtı)**|Araştırma koleksiyonu Bkz: [3.4 Özellikler Aralığı dışarı aktarma (JSON yanıtı)](#34-properties-delta-export-json-response)|Her benzersiz bileşimi için bir girdiyle birlikte bir tablo döndürür: DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion,DorId ve EventTimestamp. <p> API, JSON yanıtları olarak organizasyon verilerinize veri çeker. Yanıt sayfalandı, dolayısıyla sonraki sonuçları getirmek için yanıttan @odata.nextLink alanını kullanabilirsiniz. Tüm yazılım açıkları değerlendirmesi (JSON yanıtı), cihaza göre kuruma göre yazılım açıkları değerlendirmesinin tüm anlık görüntüsünü almak için kullanılır. Bununla birlikte, değişiklik dışarı aktarma API'si çağrısı yalnızca seçili tarih ile geçerli tarih (değişiklik"API çağrısı) arasında olan değişiklikleri getirmek için kullanılır. Her zaman büyük miktarda veriyle tam dışarı aktarma yapmak yerine, yalnızca yeni, sabit ve güncelleştirilmiş güvenlik açıkları hakkında belirli bilgiler edinebilirsiniz. Delta dışarı aktarma API çağrısı, "kaç güvenlik açıkı düzeltildi?" gibi farklı K ÖNEMLI'leri hesaplamak için de kullanılabilir. veya "Kuruluşuma kaç yeni güvenlik açık eklendi?" gibi yeni güvenlik açıkları eklendi <p> Yazılım güvenlik açıkları için Delta dışarı aktarma API çağrısı yalnızca hedefli bir tarih aralığı için veri döndür olduğundan, tam dışarı aktarma olarak _kabul edilir_.

### <a name="32-properties-json-response"></a>3.2 Özellikler (JSON yanıtı)

Özellik (Kimlik)|Veri türü|Açıklama
:---|:---|:---
YerkarakDiyaKimlik|Dize|Ortak Güvenlik Açıkları ve SALDıRıLAR (ALI) sistemi kapsamındaki güvenlik açığına atanan benzersiz tanımlayıcı.
CvssScore|Dize|DEMİ'nin CVSS puanı.
DeviceId|Dize|Hizmette cihaz için benzersiz tanımlayıcı.
DeviceName|Dize|Cihazın tam etki alanı adı (FQDN).
DiskPath'ler|Arraystring\[\]|Ürünün cihaza yük olduğuna dair disk kanıtı.
ExploitabilityLevel|Dize|Bu güvenlik açığının açıkları açıklığı düzeyi (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)
FirstSeenTimestamp|Dize|Bu ürünün 1. TIR'ı cihazda ilk kez görüldü.
Kimlik|Dize|Kayıt için benzersiz tanımlayıcı.
LastSeenTimestamp|Dize|EN son YALNıZ BIRAYI cihaz üzerinde görüldü.
OSPlatform|Dize|Cihazda çalışan işletim sisteminin platformu; Windows 10 ve Windows 11 gibi, aynı aile içindeki çeşitlemelere sahip belirli Windows. Ayrıntılar için TVm'de desteklenen işletim sistemleri ve platformlar'a bakın.
RbacGroupName|Dize|Rol tabanlı erişim denetimi (RBAC) grubu. Bu cihaz hiçbir RBAC grubuna atanmamışsa, değer "Atanmamış" olur. Kuruluş hiçbir RBAC grubu içermese bile, değer "Yok" olur.
rbacGroupId|Dize|Rol tabanlı erişim denetimi (RBAC) grup kimliği.
RecommendationReference|Dize|Bu yazılımla ilgili öneri kimliğine başvuru.
RecommendedSecurityUpdate|Dize|Yazılım satıcısı tarafından güvenlik açığı için sağlanan güvenlik güncelleştirmelerinin adı veya açıklaması.
RecommendedSecurityUpdateId|Dize|İlgili kılavuz veya bilgi bankası (KB) makalelerine yönelik geçerli güvenlik güncelleştirmelerinin veya tanımlayıcının tanımlayıcısı.
Kayıt Defteri Yolları Arraystring\[\]|Ürünün cihaza yük olduğuna dair kayıt defteri kanıtı.
SoftwareName|Dize|Yazılım ürününün adı.
SoftwareVendor|Dize|Yazılım satıcısının adı.
SoftwareVersion|Dize|Yazılım ürününün sürüm numarası.
VulnerabilitySeverityLevel|Dize|CVSS puanı ve tehdit ortamını etkileyen dinamik etmenlere dayalı olarak güvenlik açığına atanan önem düzeyi.

### <a name="33-properties-via-files"></a>3.3 Özellikler (dosyalar yoluyla)

Özellik (Kimlik)|Veri türü|Açıklama
:---|:---|:---
Dosyaları dışarı aktarma|arraystring\[\]|Kuruluşun geçerli anlık görüntüsünü tutan dosyalar için indirme URL'lerinin listesi.
GeneratedTime|Dize|Dışarı aktarmanın oluşturulma zamanı.

### <a name="34-properties-delta-export-json-response"></a>3.4 Özellikler (delta dışarı aktarma JSON yanıtı)

Özellik (Kimlik)|Veri türü|Açıklama
:---|:---|:---
YerkarakDiyaKimlik |Dize|Ortak Güvenlik Açıkları ve SALDıRıLAR (ALI) sistemi kapsamındaki güvenlik açığına atanan benzersiz tanımlayıcı.
CvssScore|Dize|DEMİ'nin CVSS puanı.
DeviceId|Dize|Hizmette cihaz için benzersiz tanımlayıcı.
DeviceName|Dize|Cihazın tam etki alanı adı (FQDN).
DiskPath'ler|Dizi[dize]|Ürünün cihaza yük olduğuna dair disk kanıtı.
EventTimestamp|Dize|Delta olayı bulunduğu zaman.
ExploitabilityLevel|Dize|Güvenlik açığının açıkları açıkları düzeyi (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)
FirstSeenTimestamp|Dize|Ürünün 1. TIRA'sı cihazda ilk kez görüldü.
Kimlik|Dize|Kayıt için benzersiz tanımlayıcı.  
LastSeenTimestamp|Dize|EN son YALNıZ BIRAYI cihaz üzerinde görüldü.
OSPlatform|Dize|Cihazda çalışan işletim sisteminin platformu; Windows 10 ve Windows 11 gibi, aynı aile içindeki çeşitlemelere sahip belirli Windows. Ayrıntılar için TVm'de desteklenen işletim sistemleri ve platformlar'a bakın.
RbacGroupName|Dize|Rol tabanlı erişim denetimi (RBAC) grubu. Bu cihaz hiçbir RBAC grubuna atanmamışsa, değer "Atanmamış" olur. Kuruluş hiçbir RBAC grubu içermese bile, değer "Yok" olur.
RecommendationReference|Dize|Bu yazılımla ilgili öneri kimliğine başvuru.
RecommendedSecurityUpdate |Dize|Yazılım satıcısı tarafından güvenlik açığı için sağlanan güvenlik güncelleştirmelerinin adı veya açıklaması.
RecommendedSecurityUpdateId |Dize|İlgili kılavuz veya bilgi bankası (KB) makalelerine yönelik geçerli güvenlik güncelleştirmelerinin veya tanımlayıcının tanımlayıcısı
RegistryPaths |Dizi[dize]|Ürünün cihaza yük olduğuna dair kayıt defteri kanıtı.
SoftwareName|Dize|Yazılım ürününün adı.
SoftwareVendor|Dize|Yazılım satıcısının adı.
SoftwareVersion|Dize|Yazılım ürününün sürüm numarası.
Durum|Dize|**Yeni** (bir cihazda yeni bir güvenlik açığı için) açık. **Düzeltildi** (cihazda artık var olmayan bir güvenlik açığı için, düzeltilmiştir). **Güncelleştirildi** (değiştirilen bir cihazla ilgili bir güvenlik açığı için). Olası değişiklikler şunları içerir: CVSS puanı, exploitability level, önem düzeyi, DiskPaths, RegistryPaths, RecommendedSecurityUpdate).
VulnerabilitySeverityLevel|Dize|CVSS puanı ve tehdit ortamını etkileyen dinamik etmenlere dayalı olarak güvenlik açığına atanan önem düzeyi.

## <a name="see-also"></a>Ayrıca bkz.

- [Cihaz başına güvenli yapılandırma değerlendirmesini dışarı aktarma](get-assessment-secure-config.md)
- [Cihaz başına yazılım envanteri değerlendirmesini dışarı aktarma](get-assessment-software-inventory.md)
- [Cihaz başına yazılım açıkları değerlendirmesini dışarı aktarma](get-assessment-software-vulnerabilities.md)

Diğer ilgili

- [Risk tabanlı tehdit & güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Organizasyon güvenlik açıkları](tvm-weaknesses.md)
