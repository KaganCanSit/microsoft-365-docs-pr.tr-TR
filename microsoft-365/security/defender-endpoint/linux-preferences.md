---
title: Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlama
ms.reviewer: ''
description: Kuruluşlarda Linux'ta Uç Nokta için Microsoft Defender'ın nasıl yapılandırıldığından emin olun.
keywords: microsoft, defender, Endpoint için Microsoft Defender, linux, yükleme, dağıtma, kaldırma, ssible, linux, redhat, ubuntu, debian, sles, suse, centos
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 8f33208fd605193ec553ffb7901d75148e985fea
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63016447"
---
# <a name="set-preferences-for-microsoft-defender-for-endpoint-on-linux"></a>Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlama

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

> [!IMPORTANT]
> Bu konu başlığı altında, kurumsal ortamlarda Linux'ta Uç Nokta için Defender tercihlerini ayarlama ile ilgili yönergeler yer almaktadır. Ürünü komut satırına göre bir cihaz üzerinde yapılandırmak ilginizi çekiyorsa, Kaynaklar'a [bakın](linux-resources.md#configure-from-the-command-line).

Kurumsal ortamlarda Linux'ta Uç Nokta için Defender bir yapılandırma profili aracılığıyla yönetilebilir. Bu profil, tercih edilen yönetim aracından dağıtılır. Kuruluş tarafından yönetilen tercihler, cihazda yerel olarak ayarlanmış tercihlerden önceliklidir. Başka bir deyişle, işletmeniz kullanıcıları bu yapılandırma profiliyle ayarlanmış olan tercihleri değiştiremezler.

Bu makalede, bu profilin yapısı (kullanmaya başlamak için kullanabileceğiniz önerilen bir profil de dahil) ve profilin dağıtımıyla ilgili yönergeler açıklanmıştır.

## <a name="configuration-profile-structure"></a>Yapılandırma profili yapısı

Yapılandırma profili, bir anahtarla tanımlanan (tercihin adını belirtir) girdilerden ve ardından tercihin yapısına bağlı olarak bir değerden oluşan bir .json dosyasıdır. Değerler sayısal değer gibi basit veya iç içe tercih listesi gibi karmaşık olabilir.

Normalde, bir yapılandırma yönetim aracı kullanarak, konumda adı olan bir dosyayı ```mdatp_managed.json``` itersiniz ```/etc/opt/microsoft/mdatp/managed/```.

Yapılandırma profilinin en üst düzeyinde ürün genelinde tercihler ve ürünün alt bölümlerine girişler yer almaktadır. Bu bilgiler sonraki bölümlerde daha ayrıntılı olarak açıklanmaktadır.

### <a name="antivirus-engine-preferences"></a>Virüsten koruma altyapısı tercihleri

Ürünün *virüsten* koruma bileşeninin tercihlerini yönetmek için yapılandırma profilinin virüsten koruma bölümü kullanılır.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|antivirusEngine|
|**Veri türü**|Sözlük (iç içe tercih)|
|**Açıklamalar**|Sözlük içeriğinin açıklaması için aşağıdaki bölümlere bakın.|
|

#### <a name="enforcement-level-for-antivirus-engine"></a>Virüsten koruma altyapısı için zorlama düzeyi

Virüsten koruma altyapısının zorlama tercihini belirtir. Zorlama düzeyini ayarlama için üç değer vardır:

- Gerçek zamanlı (`real_time`): Gerçek zamanlı koruma (dosyalara erişildikten sonra tarama) etkinleştirilir.
- İsteğe bağlı (`on_demand`): Dosyalar yalnızca isteğe bağlı olarak taranır. Burada:
  - Gerçek zamanlı koruma kapalıdır.
- Edilgen (`passive`): Virüsten koruma altyapısını pasif modunda çalıştırır. Burada:
  - Gerçek zamanlı koruma kapalıdır.
  - Üzerine tarama özelliği açık.
  - Otomatik tehdit düzeltmesi kapalı.
  - Güvenlik zekası güncelleştirmeleri açık.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|enforcementLevel|
|**Veri türü**|Dize|
|**Olası değerler**|real_time (varsayılan) <p> on_demand <p> edilgen|
|**Açıklamalar**|Uç nokta sürüm 101.10.72 veya üzerinde Defender'da kullanılabilir.|
|


#### <a name="enabledisable-behavior-monitoring"></a>Davranış izlemeyi etkinleştirme/devre dışı bırakma 

Cihazda davranış izleme ve engelleme özelliğinin etkin olup olmadığını belirler. Güvenlik korumasının daha etkili olması için bu özelliği açık tutmasını öneririz.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|behaviorMonitoring|
|**Veri türü**|Dize|
|**Olası değerler**|devre dışı <p> etkin (varsayılan)|
|**Açıklamalar**|Uç nokta sürüm 101.45.00 veya üzerinde Defender'da kullanılabilir.|
  
#### <a name="run-a-scan-after-definitions-are-updated"></a>Tanımlar güncelleştirildikten sonra taramayı çalıştırma

Cihaza yeni güvenlik zekası güncelleştirmeleri indirildikten sonra bir işlem taraması başlatıp başlatmayacağız belirtir. Bu ayarın etkinleştirilmesi, cihazın çalışan işlemlerinin virüsten koruma taramasını tetikler.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|scanAfterDefinitionUpdate|
|**Veri türü**|Boole|
|**Olası değerler**|true (varsayılan) <p> false|
|**Açıklamalar**|Uç nokta sürüm 101.45.00 veya üzerinde Defender'da kullanılabilir.|
|

#### <a name="scan-archives-on-demand-antivirus-scans-only"></a>Arşivleri tarama (yalnızca isteğe bağlı virüsten koruma taramaları)

isteğe bağlı virüsten koruma taramaları sırasında arşivlerin taranıp taranmasının gerekip gerek olmadığını belirtir.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|scanArchives|
|**Veri türü**|Boole|
|**Olası değerler**|true (varsayılan) <p> false|
|**Açıklamalar**|Uç nokta sürüm 101.45.00 veya üzerinde Microsoft Defender'da kullanılabilir.|
|||

#### <a name="degree-of-parallelism-for-on-demand-scans"></a>Isteğe bağlı taramalar için paralellik derecesi

Isteğe bağlı taramalar için paralellik derecesini belirtir. Bu, taramayı gerçekleştirmek için kullanılan iş parçacığı sayısına karşılık gelen CPU kullanımını ve isteğe bağlı tarama süresini etkiler.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|maximumOnDemandScanThreads|
|**Veri türü**|Tamsayı|
|**Olası değerler**|2 (varsayılan). İzin verilen değerler 1 ile 64 arasındaki tamsayılardır.|
|**Açıklamalar**|Uç nokta sürüm 101.45.00 veya üzerinde Microsoft Defender'da kullanılabilir.|
|||
  

#### <a name="exclusion-merge-policy"></a>Dışlama birleştirme ilkesi

Dışlamalar için birleştirme ilkesi belirtir. Bu, yönetici tanımlı ve kullanıcı tanımlı dışlamaların (`merge`) veya yalnızca yönetici tanımlı dışlamaların (`admin_only`) bir birleşimi olabilir. Bu ayar, yerel kullanıcıların kendi dışlamalarını tanımlamalarını kısıtlamak için kullanılabilir.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|exclusionsMergePolicy|
|**Veri türü**|Dize|
|**Olası değerler**|birleştirme (varsayılan) <p> admin_only|
|**Açıklamalar**|Uç nokta sürüm 100.83.73 veya üzerinde Defender'da kullanılabilir.|
|

#### <a name="scan-exclusions"></a>Tarama dışlamaları

Tarama dışında bırakılan varlıklar. Dışlamalar tam yollar, uzantılar veya dosya adlarla belirtilebilir.
(Dışlamalar bir öğe dizisi olarak belirtilir, yönetici herhangi bir sırada, gereken sayıda öğe belirtilebilir.)

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|dışlamalar|
|**Veri türü**|Sözlük (iç içe tercih)|
|**Açıklamalar**|Sözlük içeriğinin açıklaması için aşağıdaki bölümlere bakın.|
|

##### <a name="type-of-exclusion"></a>Dışlama türü

Tarama dışında bırakılan içerik türünü belirtir.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|$type|
|**Veri türü**|Dize|
|**Olası değerler**|excludedPath <p> excludedFileExtension <p> excludedFileName|
|

##### <a name="path-to-excluded-content"></a>Dışarıda bırakılan içeriğin yolu

İçeriği tam dosya yolu ile taramanın dışında tutmak için kullanılır.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|yol|
|**Veri türü**|Dize|
|**Olası değerler**|geçerli yollar|
|**Açıklamalar**|Yalnızca *dışlanan* *$type Path olduğunda uygulanabilir*|
|

##### <a name="path-type-file--directory"></a>Yol türü (dosya / dizin)

Yol özelliğinin *bir* dosyaya veya dizine başvurup başvurduğuna işaret eder.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|isDirectory|
|**Veri türü**|Boole|
|**Olası değerler**|false (varsayılan) <p> true|
|**Açıklamalar**|Yalnızca *dışlanan* *$type Path olduğunda uygulanabilir*|
|

##### <a name="file-extension-excluded-from-the-scan"></a>Tarama dışında bırakılan dosya uzantısı

İçeriği dosya uzantısına göre taramanın dışında tutmak için kullanılır.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|uzantı|
|**Veri türü**|Dize|
|**Olası değerler**|geçerli dosya uzantıları|
|**Açıklamalar**|Yalnızca $type *excludedFileExtension olduğunda uygulanabilir* |
|

##### <a name="process-excluded-from-the-scan"></a>Tarama dışında bırakılan işlem*

Tüm dosya etkinliğinin tarama dışında tutulacak bir işlemi belirtir. İşlem, adına (örneğin, ) veya tam yola (örneğin, `cat`) göre belirtilebilir `/bin/cat`.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|ad|
|**Veri türü**|Dize|
|**Olası değerler**|herhangi bir dize|
|**Açıklamalar**|Yalnızca $type *DosyaAdı dışlanmışsa uygulanabilir* |
|

#### <a name="allowed-threats"></a>İzin verilen tehdit

Ürün tarafından engel edilemeyen ve bunun yerine çalışmasına izin verilen tehditlerin listesi (adlarıyla tanımlanır).

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|allowedThreats|
|**Veri türü**|Dize dizisi|
|

#### <a name="disallowed-threat-actions"></a>Tehdit eylemlerine izin verilmedi

Bir cihazın yerel kullanıcılarının tehdit algılandığında gerçekleştire eylemleri kısıtlar. Bu listede yer alan eylemler kullanıcı arabiriminde görüntülenmez.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|disallowedThreatActions|
|**Veri türü**|Dize dizisi|
|**Olası değerler**|izin ver (kullanıcıların tehditlere izin vermelerini kısıtlar) <p> geri yükleme (kullanıcıların karantinadan tehditleri geri yüklemesini kısıtlar)|
|**Açıklamalar**|Uç nokta sürüm 100.83.73 veya üzerinde Defender'da kullanılabilir.|
|

#### <a name="threat-type-settings"></a>Tehdit türü ayarları

*Virüsten koruma altyapısında threatTypeSettings* tercihi, belirli tehdit türlerinin ürün tarafından nasıl ele alıl olduğunu kontrol etmek için kullanılır.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|threatTypeSettings|
|**Veri türü**|Sözlük (iç içe tercih)|
|**Açıklamalar**|Sözlük içeriğinin açıklaması için aşağıdaki bölümlere bakın.|
|

##### <a name="threat-type"></a>Tehdit türü

Davranışın yapılandırıldığında tehdit türü.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|anahtar|
|**Veri türü**|Dize|
|**Olası değerler**|potentially_unwanted_application <p> archive_bomb|
|

##### <a name="action-to-take"></a>Alacak eylem

Önceki bölümde belirtilen türe yönelik bir tehditle karşı karşıyayken at gereken eylem. Şu olabilir:

- **Denetim**: Cihaz bu tür tehditlere karşı korunmaz, ancak tehditle ilgili bir giriş günlüğe kaydedilir.
- **Engelle**: Cihaz bu tür tehditlere karşı korunmaktadır ve güvenlik konsolunda bu durum size bildirilecek.
- **Kapalı**: Cihaz bu tür tehditlere karşı korunmaz ve hiçbir şey günlüğe kaydedilmez.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|değer|
|**Veri türü**|Dize|
|**Olası değerler**|denetim (varsayılan) <p> engelle <p> Kapalı|
|

#### <a name="threat-type-settings-merge-policy"></a>Tehdit türü ayarları birleştirme ilkesi

Tehdit türü ayarları için birleştirme ilkesi belirtir. Bu, yönetici tanımlı ve kullanıcı tanımlı ayarların (`merge`) veya yalnızca yönetici tanımlı ayarların () bir bileşimi olabilir`admin_only`. Bu ayar, yerel kullanıcıların farklı tehdit türleri için kendi ayarlarını tanımlamalarını kısıtlamak için kullanılabilir.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|threatTypeSettingsMergePolicy|
|**Veri türü**|Dize|
|**Olası değerler**|birleştirme (varsayılan) <p> admin_only|
|**Açıklamalar**|Uç nokta sürüm 100.83.73 veya üzerinde Defender'da kullanılabilir.|
|

#### <a name="antivirus-scan-history-retention-in-days"></a>Virüsten koruma tarama geçmişi bekletme (gün içinde)

Sonuçların cihaz tarama geçmişinde kaç gün korunacaklarını belirtin. Eski tarama sonuçları geçmişten kaldırılır. Diskten de kaldırılan eski karantinaya alınmış dosyalar.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|scanResultsRetentionDays|
|**Veri türü**|Dize|
|**Olası değerler**|90 (varsayılan). İzin verilen değerler 1 günden 180 güne kadardır.|
|**Açıklamalar**|Uç nokta sürüm 101.04.76 veya üzerinde Defender'da kullanılabilir.|
|

#### <a name="maximum-number-of-items-in-the-antivirus-scan-history"></a>Virüsten koruma tarama geçmişinde en fazla öğe sayısı

Tarama geçmişinde tutmak istediğiniz girdi sayısı üst sayısını belirtin. Girdiler, geçmişte gerçekleştirilen tüm isteğe bağlı taramaları ve tüm virüsten koruma algılamalarını içerir.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|scanHistoryMaximumItems|
|**Veri türü**|Dize|
|**Olası değerler**|10000 (varsayılan). İzin verilen değerler 5000 öğeden 15000 öğeye kadardır.|
|**Açıklamalar**|Uç nokta sürüm 101.04.76 veya üzerinde Defender'da kullanılabilir.|
|

### <a name="cloud-delivered-protection-preferences"></a>Bulut teslimi koruma tercihleri

Ürünün bulut tabanlı koruma özelliğini yapılandırmak için yapılandırma profilinde *cloudService* girdisi kullanılır.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|cloudService|
|**Veri türü**|Sözlük (iç içe tercih)|
|**Açıklamalar**|Sözlük içeriğinin açıklaması için aşağıdaki bölümlere bakın.|
|

#### <a name="enable--disable-cloud-delivered-protection"></a>Bulut teslimi korumasını etkinleştirme / devre dışı bırakma

Bulutta teslim edilen korumanın cihazda etkinleştirilip etkinleştirilme olmadığını belirler. Hizmetlerinizin güvenliğini geliştirmek için bu özelliği açık tutmanızı öneririz.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|etkin|
|**Veri türü**|Boole|
|**Olası değerler**|true (varsayılan) <p> false|
|

#### <a name="diagnostic-collection-level"></a>Tanılama koleksiyonu düzeyi

Tanılama verileri, Uç Nokta için Defender'ı güvenli ve güncel tutmak, sorunları algılamak, tanılamak ve düzeltmek ve ürün geliştirmeleri yapmak için kullanılır. Bu ayar, ürün tarafından Microsoft'a gönderilen tanılama düzeyini belirler.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|diagnosticLevel|
|**Veri türü**|Dize|
|**Olası değerler**|isteğe bağlı (varsayılan) <p> Gerekli|
|

#### <a name="enable--disable-automatic-sample-submissions"></a>Otomatik örnek gönderimleri etkinleştirme / devre dışı bırakma

Şüpheli örneklerin (tehdit içerme olasılığı olan) Microsoft'a gönder olup olmadığını belirler. Örnek gönderimi denetlemek için üç düzey vardır:

- **Yok**: Microsoft'a hiçbir şüpheli örnek gönderilmez.
- **Kasa**: Yalnızca kişisel kimliği belirlenebilir bilgi (PII) içeren şüpheli örnekler otomatik olarak yüklenir. Bu, bu ayarın varsayılan değeridir.
- **Hepsi**: Tüm şüpheli örnekler Microsoft'a gönderilir.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|automaticSampleSubmissionConsent|
|**Veri türü**|Dize|
|**Olası değerler**|yok <p> güvenli (varsayılan) <p> hepsi|
|

#### <a name="enable--disable-automatic-security-intelligence-updates"></a>Otomatik güvenlik zekası güncelleştirmelerini etkinleştirme / devre dışı bırakma

Güvenlik zekası güncelleştirmelerinin otomatik olarak yük olup olmadığını belirler:

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|automaticDefinitionUpdateEnabled|
|**Veri türü**|Boole|
|**Olası değerler**|true (varsayılan) <p> false|
|

## <a name="recommended-configuration-profile"></a>Önerilen yapılandırma profili

Çalışmaya başlamanız için, aşağıdaki yapılandırma profilinin kurum için Uç Nokta için Defender'ın sağladığı tüm koruma özelliklerinden yararlanmasını öneririz.

Aşağıdaki yapılandırma profili şu şekilde olur:

- Gerçek zamanlı korumayı (RTP) etkinleştirme
- Aşağıdaki tehdit türlerinin nasıl iş idaresi olduğunu belirtin:
  - **İstenmeyen olabilecek uygulamalar (PUA)** engellenmiş
  - **Arşiv arşiv** (yüksek sıkıştırma hızı olan dosya) ürün günlüklerinde denetlenır
- Otomatik güvenlik zekası güncelleştirmelerini etkinleştirme
- Bulut teslimi korumasını etkinleştirme
- Otomatik örnek gönderimi belirli bir düzeyde `safe` etkinleştirme
- Davranış izlemeyi etkinleştirme

### <a name="sample-profile"></a>Örnek profil

```JSON
{
   "antivirusEngine":{
      "behaviorMonitoring":"enabled",
      "enforcementLevel":"real_time",
      "threatTypeSettings":[
         {
            "key":"potentially_unwanted_application",
            "value":"block"
         },
         {
            "key":"archive_bomb",
            "value":"audit"
         }
      ]
   },
   "cloudService":{
      "automaticDefinitionUpdateEnabled":true,
      "automaticSampleSubmissionConsent":"safe",
      "enabled":true,
      "proxy": "<EXAMPLE DO NOT USE> http://proxy.server:port/"
   }
}
```

## <a name="full-configuration-profile-example"></a>Tam yapılandırma profili örneği

Aşağıdaki yapılandırma profili, bu belgede açıklanan tüm ayarlara ait girdileri içerir ve ürün üzerinde daha fazla denetime sahip olmak istediğiniz daha gelişmiş senaryolarda kullanılabilir.

### <a name="full-profile"></a>Tam profil

```JSON
{
   "antivirusEngine":{
      "behaviorMonitoring":"enabled",
      "enforcementLevel":"real_time",
      "scanAfterDefinitionUpdate":true,
      "scanArchives":true,
      "maximumOnDemandScanThreads":2,
      "exclusionsMergePolicy":"merge",
      "exclusions":[
         {
            "$type":"excludedPath",
            "isDirectory":false,
            "path":"/var/log/system.log"
         },
         {
            "$type":"excludedPath",
            "isDirectory":true,
            "path":"/run"
         },
         {
            "$type":"excludedPath",
            "isDirectory":true,
            "path":"/home/*/git"
         },
         {
            "$type":"excludedFileExtension",
            "extension":".pdf"
         },
         {
            "$type":"excludedFileName",
            "name":"cat"
         }
      ],
      "allowedThreats":[
         "<EXAMPLE DO NOT USE>EICAR-Test-File (not a virus)"
      ],
      "disallowedThreatActions":[
         "allow",
         "restore"
      ],
      "threatTypeSettingsMergePolicy":"merge",
      "threatTypeSettings":[
         {
            "key":"potentially_unwanted_application",
            "value":"block"
         },
         {
            "key":"archive_bomb",
            "value":"audit"
         }
      ]
   },
   "cloudService":{
      "enabled":true,
      "diagnosticLevel":"optional",
      "automaticSampleSubmissionConsent":"safe",
      "automaticDefinitionUpdateEnabled":true,
      "proxy": "<EXAMPLE DO NOT USE> http://proxy.server:port/"
   }
}
```

## <a name="add-tag-or-group-id-to-the-configuration-profile"></a>Yapılandırma profiline etiket veya grup kimliği ekleme

Komutu ilk `mdatp health` kez çalıştırsanız, etiket ve grup kimliğinin değeri boş olur. Dosyaya etiket veya grup kimliği eklemek `mdatp_managed.json` için aşağıdaki adımları izleyin:
  
  1. Yoldan yapılandırma profilini açın `/etc/opt/microsoft/mdatp/managed/mdatp_managed.json`.
  2. Dosyanın en altına, bloğun bulunduğu `cloudService` yere gidin.
  3. için kapanış kıvrımlı ayracı sonuna aşağıdaki örnekte olduğu gibi gerekli etiketi veya grup kimliğini ekleyin `cloudService`.

  ```JSON
    },
    "cloudService": {
      "enabled": true,
      "diagnosticLevel": "optional",
      "automaticSampleSubmissionConsent": "safe",
      "automaticDefinitionUpdateEnabled": true,
      "proxy": "http://proxy.server:port/"
  },
  "edr": {
    "groupIds":"GroupIdExample",
    "tags": [
              {
              "key": "GROUP",
              "value": "Tag"
              }
            ]
        }
  }
  ```

  > [!NOTE]
  > Bloğun sonuna sağ kıvrımlı ayracı kapattıktan sonra virgül eklemeyi `cloudService` unutmayın. Ayrıca, Etiket veya Grup Kimliği bloğu ekledikten sonra iki sağ kıvrımlı ayraç olduğundan emin olun (lütfen yukarıdaki örneğine bakın). Şu anda, etiketler için desteklenen tek anahtar adı `GROUP`. 
  
## <a name="configuration-profile-validation"></a>Yapılandırma profili doğrulaması

Yapılandırma profili geçerli bir JSON biçimlendirilmiş dosya olmalıdır. Bunu doğrulamak için kullanılmaktadır. Örneğin, cihazınıza `python` yüklemişsanız:

```bash
python -m json.tool mdatp_managed.json
```

JSON iyi düz ise, yukarıdaki komut terminale döndürür ve çıkış kodunu verir `0`. Aksi takdirde, sorunu açıklayan bir hata görüntülenir ve komut bir çıkış kodu verir `1`.

## <a name="verifying-that-the-mdatp_managedjson-file-is-working-as-expected"></a>mdatp_managed.json dosyasının beklendiği gibi çalıştığını doğrulama

/etc/opt/microsoft/mdatp/managed/mdatp_managed.json dosyanın düzgün çalıştığını doğrulamak için, bu ayarların yanında "[yönetilen]" ifadesini görüyor olun:

- cloud_enabled
- cloud_automatic_sample_submission_consent
- passive_mode_enabled
- real_time_protection_enabled
- automatic_definition_update_enabled

> [!NOTE]
> mdatp_managed.json'un etkin olması için, deamon'u `mdatp` yeniden başlatmanız gerekmez.

## <a name="configuration-profile-deployment"></a>Yapılandırma profili dağıtımı

Kuruluş için yapılandırma profilini hazır bulunduktan sonra, bu profili, kurumda kullanmakta olan yönetim aracı aracılığıyla dağıtabilirsiniz. Linux'ta Uç Nokta için Defender, *yönetilen yapılandırmayı /etc/opt/microsoft/mdatp/managed/mdatp_managed.json dosyasından* okur.
