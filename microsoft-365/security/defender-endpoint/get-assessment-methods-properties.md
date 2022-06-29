---
title: Cihaz başına değerlendirme yöntemlerini ve özelliklerini dışarı aktarma
description: "\"Tehdit ve Güvenlik Açığı Yönetimi\" verileri çeken API'ler hakkında bilgi sağlar. Farklı veri türlerini almak için farklı API çağrıları vardır. Genel olarak, her API çağrısı kuruluşunuzdaki cihazlar için gerekli verileri içerir."
keywords: api, API'ler, dışarı aktarma değerlendirmesi, cihaz değerlendirmesi başına, makine değerlendirmesi başına, güvenlik açığı değerlendirmesi raporu, cihaz güvenlik açığı değerlendirmesi, cihaz güvenlik açığı raporu, güvenli yapılandırma değerlendirmesi, güvenli yapılandırma raporu, yazılım güvenlik açıkları değerlendirmesi, yazılım güvenlik açığı raporu, makineye göre güvenlik açığı raporu,
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
ms.openlocfilehash: 022c5854c955ed9b0faef16455be1af3a81b0997
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66487299"
---
# <a name="export-assessment-methods-and-properties-per-device"></a>Cihaz başına değerlendirme yöntemlerini ve özelliklerini dışarı aktarma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft Defender Güvenlik Açığı Yönetimi](../defender-vulnerability-management/index.yml)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="api-description"></a>API açıklaması

Cihaz başına Tehdit ve Güvenlik Açığı Yönetimi verileri çeken API'ler hakkında yöntemler ve özellik ayrıntıları sağlar. Farklı veri türlerini almak için farklı API çağrıları vardır. Genel olarak, her API çağrısı kuruluşunuzdaki cihazlar için gerekli verileri içerir.

> [!NOTE]
> Aksi belirtilmedikçe, listelenen tüm dışarı aktarma değerlendirme yöntemleri **_tam dışarı aktarma_** ve **_cihaza göredir_** ( **_cihaz başına_** olarak da adlandırılır).

Farklı bilgi türlerini almak (dışarı aktarmak) için dışarı aktarma değerlendirme API'lerini kullanabilirsiniz:

- [1. Güvenli yapılandırma değerlendirmeyi dışarı aktarma](#1-export-secure-configurations-assessment)
- [2. Yazılım envanteri değerlendirmeyi dışarı aktarma](#2-export-software-inventory-assessment)
- [3. Yazılım güvenlik açıklarını dışarı aktarma değerlendirmesi](#3-export-software-vulnerabilities-assessment)

Dışarı aktarma bilgileri türlerine karşılık gelen API'ler 1, 2 ve 3. bölümlerde açıklanmıştır.

Her yöntemin farklı veri türlerini almak için farklı API çağrıları vardır. Veri miktarı büyük olabileceğinden, alınabilmesinin iki yolu vardır:

- **JSON yanıtı**  API, kuruluşunuzdaki tüm verileri JSON yanıtları olarak çeker. Bu yöntem, _100 K'den az cihazı olan küçük kuruluşlar_ için en iyisidir. Yanıt sayfalandırılır, böylece yanıttan \@odata.nextLink alanını kullanarak sonraki sonuçları getirebilirsiniz.

- **dosyalar aracılığıyla** Bu API çözümü, daha fazla miktarda veriyi daha hızlı ve daha güvenilir bir şekilde çekmenizi sağlar. Bu nedenle, 100 K'den fazla cihazı olan büyük kuruluşlar için önerilir. Bu API, kuruluşunuzdaki tüm verileri indirme dosyaları olarak çeker. Yanıt, Azure Depolama'dan tüm verileri indirmek için URL'ler içerir. Bu API, Azure Depolama'dan tüm verilerinizi aşağıdaki gibi indirmenizi sağlar:
  - Tüm kuruluş verilerinizi içeren indirme URL'lerinin listesini almak için API'yi çağırın.
  - İndirme URL'lerini kullanarak tüm dosyaları indirin ve verileri istediğiniz gibi işleyin.

'_JSON yanıtı_ veya _dosyalar aracılığıyla_' kullanılarak toplanan veriler, geçerli durumu gösteren geçerli anlık görüntüdür. Geçmiş verileri içermez. Geçmiş verileri toplamak için müşterilerin verileri kendi veri depolamalarına kaydetmesi gerekir.

## <a name="1-export-secure-configurations-assessment"></a>1. Güvenli yapılandırma değerlendirmeyi dışarı aktarma

Tüm yapılandırmaları ve bunların durumunu cihaz başına temel alarak döndürür.

### <a name="11-methods"></a>1.1 Yöntemleri

Yöntem|Veri türü|Açıklama
:---|:---|:---
Güvenli yapılandırma değerlendirmeyi **dışarı aktarma (JSON yanıtı)**|Cihaz koleksiyonuna göre güvenli yapılandırma. Bkz. [1.2 Özellikleri (JSON yanıtı)](#12-properties-json-response)|DeviceId, ConfigurationId'nin her benzersiz bileşimi için bir giriş içeren bir tablo döndürür. API, kuruluşunuzdaki tüm verileri JSON yanıtları olarak çeker. Bu yöntem, 100 K'den az cihazı olan küçük kuruluşlar için en iyisidir. Yanıt sayfalandırılır, böylece yanıttan @odata.nextLink alanını kullanarak sonraki sonuçları getirebilirsiniz.
Güvenli yapılandırma değerlendirmeyi **dışarı aktarma (dosyalar aracılığıyla)**|Cihaz koleksiyonuna göre güvenli yapılandırma. Bkz. [1.3 Özellikler (dosyalar aracılığıyla)](#13-properties-via-files)|DeviceId, ConfigurationId'nin her benzersiz bileşimi için bir giriş içeren bir tablo döndürür. Bu API çözümü, daha fazla miktarda veriyi daha hızlı ve daha güvenilir bir şekilde çekmenizi sağlar. Bu nedenle, 100 K'den fazla cihazı olan büyük kuruluşlar için önerilir. Bu API, kuruluşunuzdaki tüm verileri indirme dosyaları olarak çeker. Yanıt, Azure Depolama'dan tüm verileri indirmek için URL'ler içerir. Bu API, Azure Depolama'dan tüm verilerinizi aşağıdaki gibi indirmenizi sağlar: <ol><li>Tüm kuruluş verilerinizi içeren indirme URL'lerinin listesini almak için API'yi çağırın.</li><li>İndirme URL'lerini kullanarak tüm dosyaları indirin ve verileri istediğiniz gibi işleyin.</li></ol>

### <a name="12-properties-json-response"></a>1.2 Özellikleri (JSON yanıtı)

Özellik (Kimlik)|Veri türü|Açıklama
:---|:---|:---
configurationCategory|Dize|Yapılandırmanın ait olduğu kategori veya gruplandırma: Uygulama, İşletim Sistemi, Ağ, Hesaplar, Güvenlik denetimleri.
configurationId|Dize|Belirli bir yapılandırma için benzersiz tanımlayıcı.
configurationImpact|Dize|Yapılandırmanın genel yapılandırma puanına (1-10) göre derecelendirilmiş etkisi.
Configurationname|Dize|Yapılandırmanın görünen adı.
configurationSubcategory|Dize|Yapılandırmanın ait olduğu alt kategori veya alt gruplama. Çoğu durumda, belirli özellikler veya özellikler.
Deviceıd|Dize|Hizmetteki cihaz için benzersiz tanımlayıcı.
deviceName|Dize|Cihazın tam etki alanı adı (FQDN).
isApplicable|Bool|Yapılandırmanın veya ilkenin geçerli olup olmadığını gösterir.
isCompliant|Bool|Yapılandırmanın veya ilkenin düzgün yapılandırılıp yapılandırılmadığını gösterir.
isExpectedUserImpact|Bool|Yapılandırmanın uygulanıp uygulanmayacağını kullanıcının etkilenip etkilenmediğini gösterir.
osPlatform|Dize|Cihazda çalışan işletim sisteminin platformu. Windows 10 ve Windows 11 gibi aynı aile içinde varyasyonları olan belirli işletim sistemleri. Ayrıntılar için bkz. TVM tarafından desteklenen işletim sistemleri ve platformlar.
osVersion|Dize|Cihazda çalışan işletim sisteminin belirli bir sürümü.
rbacGroupName|Dize|Rol tabanlı erişim denetimi (RBAC) grubu. Cihaz herhangi bir RBAC grubuna atanmamışsa, değer "Atanmamış" olur. Kuruluş herhangi bir RBAC grubu içermiyorsa, değer "Yok" olur.
rbacGroupId|Dize|Rol tabanlı erişim denetimi (RBAC) grup kimliği.
recommendationReference|Dize|Yazılımla ilgili öneri kimliğine başvuru.
Zaman damgası|Dize|Yapılandırmanın cihazda son görüldüğü zaman.

### <a name="13-properties-via-files"></a>1.3 Özellikler (dosyalar aracılığıyla)

Özellik (Kimlik)|Veri türü|Açıklama
:---|:---|:---
Dosyaları dışarı aktarma|dizi\[dizesi\]|Kuruluşun geçerli anlık görüntüsünü içeren dosyalar için indirme URL'lerinin listesi.
GeneratedTime|Dize|Dışarı aktarmanın oluşturulduğu zaman.

## <a name="2-export-software-inventory-assessment"></a>2. Yazılım envanteri değerlendirmeyi dışarı aktarma

Her cihazdaki tüm yüklü yazılımları ve bunların ayrıntılarını döndürür.

### <a name="21-methods"></a>2.1 Yöntemleri

|Yöntem|Veri türü|Açıklama|
|:---|:---|:---|
|Yazılım envanteri değerlendirmeyi **dışarı aktarma (JSON yanıtı)**|Cihaz koleksiyonuna göre yazılım envanteri. Bkz. [2.2 Özellikleri (JSON yanıtı)](#22-properties-json-response)|DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion'ın her benzersiz bileşimi için bir giriş içeren bir tablo döndürür. API, kuruluşunuzdaki tüm verileri JSON yanıtları olarak çeker. Bu yöntem, 100 K'den az cihazı olan küçük kuruluşlar için en iyisidir. Yanıt sayfalandırılır, böylece yanıttan @odata.nextLink alanını kullanarak sonraki sonuçları getirebilirsiniz. |
| Yazılım envanteri değerlendirmeyi **dışarı aktarma (dosyalar aracılığıyla)**|Cihaz dosyalarına göre yazılım envanteri. Bkz. [2.3 Özellikler (dosyalar aracılığıyla)](#23-properties-via-files)|DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion'ın her benzersiz bileşimi için bir giriş içeren bir tablo döndürür. Bu API çözümü, daha fazla miktarda veriyi daha hızlı ve daha güvenilir bir şekilde çekmenizi sağlar. Bu nedenle, 100 K'den fazla cihazı olan büyük kuruluşlar için önerilir. Bu API, kuruluşunuzdaki tüm verileri indirme dosyaları olarak çeker. Yanıt, Azure Depolama'dan tüm verileri indirmek için URL'ler içerir. Bu API, Azure Depolama'dan aşağıdaki gibi veri indirmenize olanak tanır: <ol><li>Kuruluş verilerinizle birlikte indirme URL'lerinin listesini almak için API'yi çağırın</li><li>İndirme URL'lerini kullanarak dosyaları indirin ve verileri istediğiniz gibi işleyin.</li></ol> |

### <a name="22-properties-json-response"></a>2.2 Özellikler (JSON yanıtı)

Özellik (Kimlik)|Veri türü|Açıklama
:---|:---|:---
Deviceıd|Dize|Hizmetteki cihaz için benzersiz tanımlayıcı.
DeviceName|Dize|Cihazın tam etki alanı adı (FQDN).
DiskPath'ler|Dizi[dize]|Ürünün cihaza yüklendiğini gösteren disk kanıtı.
EndOfSupportDate|Dize|Bu yazılım için desteğin sona ereceği veya sona ereceği tarih.
EndOfSupportStatus|Dize|Destek sonu durumu. Şu olası değerleri içerebilir: Yok, EOS Sürümü, Yaklaşan EOS Sürümü, EOS Yazılımı, Yaklaşan EOS Yazılımı.
NumberOfWeaknesses|Int|Bu cihazdaki bu yazılımdaki zayıflıkların sayısı.
OSPlatform|Dize|Cihazda çalışan işletim sisteminin platformu; Windows 10 ve Windows 11 gibi aynı aile içindeki varyasyonlara sahip belirli işletim sistemleri. Ayrıntılar için bkz. tvm tarafından desteklenen işletim sistemleri ve platformlar.
RbacGroupName|Dize|Rol tabanlı erişim denetimi (RBAC) grubu. Bu cihaz herhangi bir RBAC grubuna atanmazsa, değer "Atanmamış" olur. Kuruluş herhangi bir RBAC grubu içermiyorsa, değer "Yok" olur.
rbacGroupId|Dize|Rol tabanlı erişim denetimi (RBAC) grup kimliği.
RegistryPaths|Dizi[dize]|Ürünün cihaza yüklendiğine dair kayıt defteri kanıtı.
SoftwareFirstSeenTimestamp|Dize|Bu yazılım cihazda ilk kez görüldü.
SoftwareName|Dize|Yazılım ürününün adı.
SoftwareVendor|Dize|Yazılım satıcısının adı.
SoftwareVersion|Dize|Yazılım ürününün sürüm numarası.

### <a name="23-properties-via-files"></a>2.3 Özellikler (dosyalar aracılığıyla)

Özellik (Kimlik)|Veri türü|Açıklama
:---|:---|:---
Dosyaları dışarı aktarma|dizi\[dizesi\]|Kuruluşun geçerli anlık görüntüsünü içeren dosyalar için indirme URL'lerinin listesi.
GeneratedTime|Dize|Dışarı aktarmanın oluşturulduğu zaman.

## <a name="3-export-software-vulnerabilities-assessment"></a>3. Yazılım güvenlik açıklarını dışarı aktarma değerlendirmesi

Bir cihazdaki bilinen tüm güvenlik açıklarını ve bunların ayrıntılarını tüm cihazlar için döndürür.

### <a name="31-methods"></a>3.1 Yöntemleri

Yöntem|Veri türü|Açıklama
:---|:---|:---
Yazılım güvenlik açıklarını dışarı aktarma değerlendirmesi **(JSON yanıtı)**|Araştırma koleksiyonu Bkz: [3.2 Özellikleri (JSON yanıtı)](#32-properties-json-response)|DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId'nin her benzersiz bileşimi için bir giriş içeren bir tablo döndürür. API, kuruluşunuzdaki tüm verileri JSON yanıtları olarak çeker. Bu yöntem, 100 K'den az cihazı olan küçük kuruluşlar için en iyisidir. Yanıt sayfalandırılır, böylece yanıttan @odata.nextLink alanını kullanarak sonraki sonuçları getirebilirsiniz.
Yazılım güvenlik açıklarını dışarı aktarma değerlendirmesi **(dosyalar aracılığıyla)**|Araştırma varlığı Bkz: [3.3 Özellikler (dosyalar aracılığıyla)](#33-properties-via-files)|DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId'nin her benzersiz bileşimi için bir giriş içeren bir tablo döndürür. Bu API çözümü, daha fazla miktarda veriyi daha hızlı ve daha güvenilir bir şekilde çekmenizi sağlar. Bu nedenle, 100 K'den fazla cihazı olan büyük kuruluşlar için önerilir. Bu API, kuruluşunuzdaki tüm verileri indirme dosyaları olarak çeker. Yanıt, Azure Depolama'dan tüm verileri indirmek için URL'ler içerir. Bu API, Azure Depolama'dan tüm verilerinizi aşağıdaki gibi indirmenizi sağlar: <ol><li>Tüm kuruluş verilerinizi içeren indirme URL'lerinin listesini almak için API'yi çağırın.</li><li>İndirme URL'lerini kullanarak tüm dosyaları indirin ve verileri istediğiniz gibi işleyin.</li></ol>
**Delta dışarı aktarma** yazılımı güvenlik açıkları değerlendirmesi **(JSON yanıtı)**|Araştırma koleksiyonu Bkz: [3.4 Özellikler Delta dışarı aktarma (JSON yanıtı)](#34-properties-delta-export-json-response)|DeviceId, SoftwareVendor, SoftwareName, SoftwareVersion, CveId ve EventTimestamp'ın her benzersiz bileşimi için bir giriş içeren bir tablo döndürür. <p> API, kuruluşunuzdaki verileri JSON yanıtları olarak çeker. Yanıt sayfalandırılır, böylece yanıttan @odata.nextLink alanını kullanarak sonraki sonuçları getirebilirsiniz. Tam yazılım güvenlik açıkları değerlendirmesi (JSON yanıtı), cihazınıza göre kuruluşunuzun yazılım güvenlik açıkları değerlendirmesinin tüm anlık görüntüsünü almak için kullanılır. Ancak, delta dışarı aktarma API çağrısı yalnızca seçili tarih ile geçerli tarih ("delta" API çağrısı) arasında gerçekleşen değişiklikleri getirmek için kullanılır. Her seferinde büyük miktarda veriyle tam dışarı aktarma işlemi almak yerine yalnızca yeni, sabit ve güncelleştirilmiş güvenlik açıklarıyla ilgili belirli bilgileri alırsınız. Delta dışarı aktarma API'si çağrısı, "kaç güvenlik açığı düzeltildi?" gibi farklı KPI'leri hesaplamak için de kullanılabilir. veya "Kuruluşuma kaç yeni güvenlik açığı eklendi?" <p> Yazılım güvenlik açıkları için Delta dışarı aktarma API çağrısı yalnızca hedeflenen bir tarih aralığına ilişkin verileri döndürdüğünden, _tam dışarı aktarma_ olarak kabul edilmez.

### <a name="32-properties-json-response"></a>3.2 Özellikleri (JSON yanıtı)

Özellik (Kimlik)|Veri türü|Açıklama
:---|:---|:---
CveId|Dize|Ortak Güvenlik Açıkları ve Etkilenmeler (CVE) sistemi altında güvenlik açığına atanan benzersiz tanımlayıcı.
CvssScore|Dize|CVE'nin CVSS puanı.
Deviceıd|Dize|Hizmetteki cihaz için benzersiz tanımlayıcı.
DeviceName|Dize|Cihazın tam etki alanı adı (FQDN).
DiskPath'ler|Dizi\[dizesi\]|Ürünün cihaza yüklendiğini gösteren disk kanıtı.
ExploitabilityLevel|Dize|Bu güvenlik açığının kötüye kullanılabilirlik düzeyi (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)
FirstSeenTimestamp|Dize|Bu ürünün CVE'i cihazda ilk kez görüldü.
Kimlik|Dize|Kayıt için benzersiz tanımlayıcı.
LastSeenTimestamp|Dize|CVE'nin cihazda son görüldüğü zaman.
OSPlatform|Dize|Cihazda çalışan işletim sisteminin platformu; Windows 10 ve Windows 11 gibi aynı aile içindeki varyasyonlara sahip belirli işletim sistemleri. Ayrıntılar için bkz. tvm tarafından desteklenen işletim sistemleri ve platformlar.
RbacGroupName|Dize|Rol tabanlı erişim denetimi (RBAC) grubu. Bu cihaz herhangi bir RBAC grubuna atanmazsa, değer "Atanmamış" olur. Kuruluş herhangi bir RBAC grubu içermiyorsa, değer "Yok" olur.
rbacGroupId|Dize|Rol tabanlı erişim denetimi (RBAC) grup kimliği.
RecommendationReference|Dize|Bu yazılımla ilgili öneri kimliğine başvuru.
RecommendedSecurityUpdate|Dize|Güvenlik açığını gidermek için yazılım satıcısı tarafından sağlanan güvenlik güncelleştirmesinin adı veya açıklaması.
RecommendedSecurityUpdateId|Dize|İlgili kılavuz veya bilgi bankası (KB) makaleleri için geçerli güvenlik güncelleştirmelerinin veya tanımlayıcının tanımlayıcısı.
Kayıt Defteri Yolları|Dizi[dize]|Ürünün cihaza yüklendiğine dair kayıt defteri kanıtı.
SecurityUpdateAvailable|Boole|Yazılım için bir güvenlik güncelleştirmesi olup olmadığını gösterir.
SoftwareName|Dize|Yazılım ürününün adı.
SoftwareVendor|Dize|Yazılım satıcısının adı.
SoftwareVersion|Dize|Yazılım ürününün sürüm numarası.
VulnerabilitySeverityLevel|Dize|CVSS puanına ve tehdit ortamının etkilediği dinamik faktörlere göre güvenlik açığına atanan önem düzeyi.

### <a name="33-properties-via-files"></a>3.3 Özellikler (dosyalar aracılığıyla)

Özellik (Kimlik)|Veri türü|Açıklama
:---|:---|:---
Dosyaları dışarı aktarma|dizi\[dizesi\]|Kuruluşun geçerli anlık görüntüsünü içeren dosyalar için indirme URL'lerinin listesi.
GeneratedTime|Dize|Dışarı aktarmanın oluşturulduğu zaman.

### <a name="34-properties-delta-export-json-response"></a>3.4 Özellikler (değişiklik dışarı aktarma JSON yanıtı)

Özellik (Kimlik)|Veri türü|Açıklama
:---|:---|:---
CveId |Dize|Ortak Güvenlik Açıkları ve Etkilenmeler (CVE) sistemi altında güvenlik açığına atanan benzersiz tanımlayıcı.
CvssScore|Dize|CVE'nin CVSS puanı.
Deviceıd|Dize|Hizmetteki cihaz için benzersiz tanımlayıcı.
DeviceName|Dize|Cihazın tam etki alanı adı (FQDN).
DiskPath'ler|Dizi[dize]|Ürünün cihaza yüklendiğini gösteren disk kanıtı.
EventTimestamp|Dize|Delta olayının bulunduğu saat.
ExploitabilityLevel|Dize|Güvenlik açığının kötüye kullanılabilirlik düzeyi (NoExploit, ExploitIsPublic, ExploitIsVerified, ExploitIsInKit)
FirstSeenTimestamp|Dize|Ürünün CVE'i cihazda ilk kez görüldü.
Kimlik|Dize|Kayıt için benzersiz tanımlayıcı.  
LastSeenTimestamp|Dize|CVE'nin cihazda son görüldüğü zaman.
OSPlatform|Dize|Cihazda çalışan işletim sisteminin platformu; Windows 10 ve Windows 11 gibi aynı aile içindeki varyasyonlara sahip belirli işletim sistemleri. Ayrıntılar için bkz. tvm tarafından desteklenen işletim sistemleri ve platformlar.
RbacGroupName|Dize|Rol tabanlı erişim denetimi (RBAC) grubu. Bu cihaz herhangi bir RBAC grubuna atanmazsa, değer "Atanmamış" olur. Kuruluş herhangi bir RBAC grubu içermiyorsa, değer "Yok" olur.
RecommendationReference|Dize|Bu yazılımla ilgili öneri kimliğine başvuru.
RecommendedSecurityUpdate |Dize|Güvenlik açığını gidermek için yazılım satıcısı tarafından sağlanan güvenlik güncelleştirmesinin adı veya açıklaması.
RecommendedSecurityUpdateId |Dize|İlgili kılavuz veya bilgi bankası (KB) makaleleri için geçerli güvenlik güncelleştirmelerinin veya tanımlayıcısının tanımlayıcısı
RegistryPaths |Dizi[dize]|Ürünün cihaza yüklendiğine dair kayıt defteri kanıtı.
SoftwareName|Dize|Yazılım ürününün adı.
SoftwareVendor|Dize|Yazılım satıcısının adı.
SoftwareVersion|Dize|Yazılım ürününün sürüm numarası.
Durum|Dize|**Yeni** (cihazda kullanıma sunulan yeni bir güvenlik açığı için). **Düzeltildi** (cihazda artık mevcut olmayan ve düzeltildiği anlamına gelen bir güvenlik açığı için). **Güncelleştirildi** (değiştirilen bir cihazdaki güvenlik açığı için. Olası değişiklikler şunlardır: CVSS puanı, kötüye kullanılabilirlik düzeyi, önem düzeyi, DiskPaths, RegistryPaths, RecommendedSecurityUpdate).
VulnerabilitySeverityLevel|Dize|CVSS puanına ve tehdit ortamının etkilediği dinamik faktörlere bağlı olarak güvenlik açığına atanan önem düzeyi.

## <a name="see-also"></a>Ayrıca bkz.

- [Cihaz başına güvenli yapılandırma değerlendirmelerini dışarı aktarma](get-assessment-secure-config.md)
- [Cihaz başına yazılım envanteri değerlendirmeyi dışarı aktarma](get-assessment-software-inventory.md)
- [Cihaz başına yazılım güvenlik açıkları değerlendirmesi dışarı aktarma](get-assessment-software-vulnerabilities.md)

Diğer ilgililer

- [Risk tabanlı tehdit & güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Kuruluşunuzdaki güvenlik açıkları](tvm-weaknesses.md)
