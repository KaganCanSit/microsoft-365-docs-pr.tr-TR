---
title: Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlama
ms.reviewer: ''
description: Kuruluşlarda Linux'ta Uç Nokta için Microsoft Defender yapılandırmayı açıklar.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, linux, installation, deploy, uninstallation, puppet, ansible, linux, redhat, ubuntu, debian, sles, suse, centos
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
ms.openlocfilehash: 1a579944fa0f7578fa2afcf66472cebbb6f07037
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64663786"
---
# <a name="set-preferences-for-microsoft-defender-for-endpoint-on-linux"></a>Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlama

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimlemek mi istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

> [!IMPORTANT]
> Bu konu, kurumsal ortamlarda Linux üzerinde Uç Nokta için Defender tercihlerini ayarlama yönergelerini içerir. Ürünü bir cihazda komut satırından yapılandırmak istiyorsanız bkz [. Kaynaklar](linux-resources.md#configure-from-the-command-line).

Kurumsal ortamlarda, Linux üzerinde Uç Nokta için Defender bir yapılandırma profili aracılığıyla yönetilebilir. Bu profil, seçtiğiniz yönetim aracından dağıtılır. Kuruluş tarafından yönetilen tercihler, cihazda yerel olarak ayarlanan tercihlerden önceliklidir. Başka bir deyişle, kuruluşunuzdaki kullanıcılar bu yapılandırma profili aracılığıyla ayarlanan tercihleri değiştiremez.

Bu makalede, bu profilin yapısı (başlamak için kullanabileceğiniz önerilen bir profil dahil) ve profilin nasıl dağıtılacağına ilişkin yönergeler açıklanmaktadır.

## <a name="configuration-profile-structure"></a>Yapılandırma profili yapısı

Yapılandırma profili, bir anahtar tarafından tanımlanan girdilerden (tercihin adını belirtir) ve ardından tercihin yapısına bağlı olarak bir değerden oluşan bir .json dosyasıdır. Değerler, sayısal değer gibi basit veya iç içe yerleştirilmiş tercih listesi gibi karmaşık olabilir.

Genellikle, konumunda ```/etc/opt/microsoft/mdatp/managed/```adıyla ```mdatp_managed.json``` bir dosya göndermek için bir yapılandırma yönetim aracı kullanırsınız.

Yapılandırma profilinin en üst düzeyi, ürünün alt ürünleri için ürün genelindeki tercihleri ve girişleri içerir ve bunlar sonraki bölümlerde daha ayrıntılı olarak açıklanmıştır.

### <a name="antivirus-engine-preferences"></a>Virüsten koruma altyapısı tercihleri

Yapılandırma profilinin *antivirusEngine* bölümü, ürünün virüsten koruma bileşeninin tercihlerini yönetmek için kullanılır.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|antivirusEngine|
|**Veri türü**|Sözlük (iç içe tercih)|
|**Açıklamalar**|Sözlük içeriğinin açıklaması için aşağıdaki bölümlere bakın.|
|

#### <a name="enforcement-level-for-antivirus-engine"></a>Virüsten koruma altyapısı için zorlama düzeyi

Virüsten koruma altyapısının zorlama tercihini belirtir. Zorlama düzeyini ayarlamak için üç değer vardır:

- Gerçek zamanlı (`real_time`): Gerçek zamanlı koruma (erişilen dosyaları tara) etkinleştirilir.
- İsteğe bağlı (`on_demand`): Dosyalar yalnızca isteğe bağlı olarak taranır. Burada:
  - Gerçek zamanlı koruma kapalıdır.
- Pasif (`passive`): Virüsten koruma altyapısını pasif modda çalıştırır. Burada:
  - Gerçek zamanlı koruma kapalıdır.
  - İsteğe bağlı tarama açıktır.
  - Otomatik tehdit düzeltme kapalı.
  - Güvenlik bilgileri güncelleştirmeleri açıktır.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|enforcementLevel|
|**Veri türü**|Dize|
|**Olası değerler**|real_time (varsayılan) <p> on_demand <p> Pasif|
|**Açıklamalar**|Uç Nokta için Defender sürüm 101.10.72 veya sonraki sürümlerde kullanılabilir.|
|


#### <a name="enabledisable-behavior-monitoring"></a>Davranış izlemeyi etkinleştirme/devre dışı bırakma 

Cihazda davranış izleme ve engelleme özelliğinin etkinleştirilip etkinleştirilmediğini belirler. Güvenlik korumasının verimliliğini artırmak için bu özelliği açık tutmanızı öneririz.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|behaviorMonitoring|
|**Veri türü**|Dize|
|**Olası değerler**|devre dışı (varsayılan) <p> etkin (varsayılan)|
|**Açıklamalar**|Uç Nokta için Defender sürüm 101.45.00 veya üzeri sürümlerde kullanılabilir.|
  
#### <a name="run-a-scan-after-definitions-are-updated"></a>Tanımlar güncelleştirildikten sonra tarama çalıştırma

Cihaza yeni güvenlik bilgileri güncelleştirmeleri indirildikten sonra işlem taraması başlatılıp başlatılmayacağını belirtir. Bu ayarın etkinleştirilmesi, cihazın çalışan işlemlerinde virüsten koruma taraması tetikler.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|scanAfterDefinitionUpdate|
|**Veri türü**|Boole|
|**Olası değerler**|true (varsayılan) <p> False|
|**Açıklamalar**|Uç Nokta için Defender sürüm 101.45.00 veya üzeri sürümlerde kullanılabilir.|
|

#### <a name="scan-archives-on-demand-antivirus-scans-only"></a>Arşivleri tara (yalnızca isteğe bağlı virüsten koruma taramaları)

İsteğe bağlı virüsten koruma taramaları sırasında arşivlerin taranıp taranmayacağını belirtir.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|scanArchives|
|**Veri türü**|Boole|
|**Olası değerler**|true (varsayılan) <p> False|
|**Açıklamalar**|Uç Nokta için Microsoft Defender sürüm 101.45.00 veya üzeri sürümlerde kullanılabilir.|
|||

#### <a name="degree-of-parallelism-for-on-demand-scans"></a>İsteğe bağlı taramalar için paralellik derecesi

İsteğe bağlı taramalar için paralellik derecesini belirtir. Bu, taramayı gerçekleştirmek için kullanılan iş parçacığı sayısına karşılık gelir ve CPU kullanımını ve isteğe bağlı tarama süresini etkiler.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|maximumOnDemandScanThreads|
|**Veri türü**|Tamsayı|
|**Olası değerler**|2 (varsayılan). İzin verilen değerler 1 ile 64 arasındaki tamsayılardır.|
|**Açıklamalar**|Uç Nokta için Microsoft Defender sürüm 101.45.00 veya üzeri sürümlerde kullanılabilir.|
|||
  

#### <a name="exclusion-merge-policy"></a>Dışlama birleştirme ilkesi

Dışlamalar için birleştirme ilkesini belirtir. Yönetici tanımlı ve kullanıcı tanımlı dışlamaların (`merge`) veya yalnızca yönetici tanımlı dışlamaların (`admin_only`) birleşimi olabilir. Bu ayar, yerel kullanıcıların kendi dışlamalarını tanımlamasını kısıtlamak için kullanılabilir.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|exclusionsMergePolicy|
|**Veri türü**|Dize|
|**Olası değerler**|merge (varsayılan) <p> admin_only|
|**Açıklamalar**|Uç Nokta için Defender sürüm 100.83.73 veya sonraki sürümlerde kullanılabilir.|
|

#### <a name="scan-exclusions"></a>Tarama dışlamaları

Taramanın dışında tutulan varlıklar. Dışlamalar tam yollar, uzantılar veya dosya adlarıyla belirtilebilir.
(Dışlamalar bir öğe dizisi olarak belirtilir, yönetici gerektiği kadar öğeyi herhangi bir sırada belirtebilir.)

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|Dışlamalar|
|**Veri türü**|Sözlük (iç içe tercih)|
|**Açıklamalar**|Sözlük içeriğinin açıklaması için aşağıdaki bölümlere bakın.|
|

##### <a name="type-of-exclusion"></a>Dışlama türü

Taramanın dışında tutulan içerik türünü belirtir.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|$type|
|**Veri türü**|Dize|
|**Olası değerler**|excludedPath <p> excludedFileExtension <p> excludedFileName|
|

##### <a name="path-to-excluded-content"></a>Dışlanan içeriğin yolu

İçeriği taramadan tam dosya yolu ile dışlamak için kullanılır.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|Yolu|
|**Veri türü**|Dize|
|**Olası değerler**|geçerli yollar|
|**Açıklamalar**|Yalnızca *$type* *excludedPath* olduğunda uygulanabilir|
|

##### <a name="path-type-file--directory"></a>Yol türü (dosya / dizin)

*path* özelliğinin bir dosyaya veya dizine başvurup başvurmadığını gösterir.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|isDirectory|
|**Veri türü**|Boole|
|**Olası değerler**|false (varsayılan) <p> True|
|**Açıklamalar**|Yalnızca *$type* *excludedPath* olduğunda uygulanabilir|
|

##### <a name="file-extension-excluded-from-the-scan"></a>Dosya uzantısı taramanın dışında bırakıldı

İçeriği dosya uzantısına göre taramanın dışında tutmak için kullanılır.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|Uzantısı|
|**Veri türü**|Dize|
|**Olası değerler**|geçerli dosya uzantıları|
|**Açıklamalar**|Yalnızca *$type* *excludedFileExtension* olduğunda geçerlidir|
|

##### <a name="process-excluded-from-the-scan"></a>Taramanın dışında tutulan işlem*

Tüm dosya etkinliğinin taramanın dışında bırakıldığı bir işlemi belirtir. İşlem adıyla (örneğin, `cat`) veya tam yoluyla (örneğin, `/bin/cat`) belirtilebilir.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|Adı|
|**Veri türü**|Dize|
|**Olası değerler**|herhangi bir dize|
|**Açıklamalar**|Yalnızca *$type* *excludedFileName* olduğunda geçerlidir|
|

#### <a name="allowed-threats"></a>İzin verilen tehditler

Ürün tarafından engellenmeyen ve bunun yerine çalışmasına izin verilen tehditlerin (adıyla tanımlanır) listesi.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|allowedThreats|
|**Veri türü**|Dize dizisi|
|

#### <a name="disallowed-threat-actions"></a>İzin verilmeyen tehdit eylemleri

Bir cihazın yerel kullanıcısının tehdit algılandığında gerçekleştirebileceği eylemleri kısıtlar. Bu listede yer alan eylemler kullanıcı arabiriminde görüntülenmez.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|disallowedThreatActions|
|**Veri türü**|Dize dizisi|
|**Olası değerler**|allow (kullanıcıların tehditlere izin vermelerini kısıtlar) <p> geri yükleme (kullanıcıların karantinadan tehditleri geri yüklemesini kısıtlar)|
|**Açıklamalar**|Uç Nokta için Defender sürüm 100.83.73 veya sonraki sürümlerde kullanılabilir.|
|

#### <a name="threat-type-settings"></a>Tehdit türü ayarları

Virüsten koruma altyapısındaki *threatTypeSettings* tercihi, belirli tehdit türlerinin ürün tarafından nasıl işlenme şeklini denetlemek için kullanılır.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|threatTypeSettings|
|**Veri türü**|Sözlük (iç içe tercih)|
|**Açıklamalar**|Sözlük içeriğinin açıklaması için aşağıdaki bölümlere bakın.|
|

##### <a name="threat-type"></a>Tehdit türü

Davranışın yapılandırıldığı tehdit türü.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|Anahtar|
|**Veri türü**|Dize|
|**Olası değerler**|potentially_unwanted_application <p> archive_bomb|
|

##### <a name="action-to-take"></a>Gerçekleştirecek eylem

Önceki bölümde belirtilen türdeki bir tehditle karşılaşıldığında gerçekleştirilen eylem. Şu olabilir:

- **Denetim**: Cihaz bu tür tehditlere karşı korunmaz, ancak tehditle ilgili bir giriş günlüğe kaydedilir.
- **Engelle**: Cihaz bu tür tehditlere karşı korunur ve güvenlik konsolunda size bildirilir.
- **Kapalı**: Cihaz bu tür tehditlere karşı korunmaz ve hiçbir şey günlüğe kaydedilmez.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|Değer|
|**Veri türü**|Dize|
|**Olası değerler**|denetim (varsayılan) <p> Blok <p> kapalı|
|

#### <a name="threat-type-settings-merge-policy"></a>Tehdit türü ayarları birleştirme ilkesi

Tehdit türü ayarları için birleştirme ilkesini belirtir. Bu, yönetici tanımlı ve kullanıcı tanımlı ayarların () veya yalnızca yönetici tanımlı ayarların (`merge``admin_only`) birleşimi olabilir. Bu ayar, yerel kullanıcıların farklı tehdit türleri için kendi ayarlarını tanımlamasını kısıtlamak için kullanılabilir.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|threatTypeSettingsMergePolicy|
|**Veri türü**|Dize|
|**Olası değerler**|merge (varsayılan) <p> admin_only|
|**Açıklamalar**|Uç Nokta için Defender sürüm 100.83.73 veya sonraki sürümlerde kullanılabilir.|
|

#### <a name="antivirus-scan-history-retention-in-days"></a>Virüsten koruma tarama geçmişi saklama (gün olarak)

Sonuçların cihazdaki tarama geçmişinde tutulacağını gün sayısını belirtin. Eski tarama sonuçları geçmişten kaldırılır. Diskten de kaldırılan eski karantinaya alınan dosyalar.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|scanResultsRetentionDays|
|**Veri türü**|Dize|
|**Olası değerler**|90 (varsayılan). İzin verilen değerler 1 günden 180 güne kadardır.|
|**Açıklamalar**|Uç Nokta için Defender sürüm 101.04.76 veya sonraki sürümlerde kullanılabilir.|
|

#### <a name="maximum-number-of-items-in-the-antivirus-scan-history"></a>Virüsten koruma tarama geçmişindeki en fazla öğe sayısı

Tarama geçmişinde tutulacak en fazla girdi sayısını belirtin. Girişler, geçmişte gerçekleştirilen tüm isteğe bağlı taramaları ve tüm virüsten koruma algılamalarını içerir.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|scanHistoryMaximumItems|
|**Veri türü**|Dize|
|**Olası değerler**|10000 (varsayılan). İzin verilen değerler 5000 öğeden 15000 öğeye kadardır.|
|**Açıklamalar**|Uç Nokta için Defender sürüm 101.04.76 veya sonraki sürümlerde kullanılabilir.|
|

### <a name="cloud-delivered-protection-preferences"></a>Bulut tabanlı koruma tercihleri

Yapılandırma profilindeki *cloudService* girdisi, ürünün bulut tabanlı koruma özelliğini yapılandırmak için kullanılır.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|cloudService|
|**Veri türü**|Sözlük (iç içe tercih)|
|**Açıklamalar**|Sözlük içeriğinin açıklaması için aşağıdaki bölümlere bakın.|
|

#### <a name="enable--disable-cloud-delivered-protection"></a>Bulut teslimli korumayı etkinleştirme/devre dışı bırakma

Cihazda bulut tabanlı korumanın etkinleştirilip etkinleştirilmediğini belirler. Hizmetlerinizin güvenliğini artırmak için bu özelliği açık tutmanızı öneririz.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|Etkin|
|**Veri türü**|Boole|
|**Olası değerler**|true (varsayılan) <p> False|
|

#### <a name="diagnostic-collection-level"></a>Tanılama toplama düzeyi

Tanılama verileri Uç Nokta için Defender'ı güvenli ve güncel tutmak, sorunları algılamak, tanılamak ve düzeltmek ve ürün geliştirmeleri yapmak için kullanılır. Bu ayar, ürün tarafından Microsoft'a gönderilen tanılama düzeyini belirler.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|diagnosticLevel|
|**Veri türü**|Dize|
|**Olası değerler**|isteğe bağlı (varsayılan) <p> Gerekli|
|

#### <a name="enable--disable-automatic-sample-submissions"></a>Otomatik örnek gönderimlerini etkinleştirme/devre dışı bırakma

Şüpheli örneklerin (tehdit içerme olasılığı yüksek) Microsoft'a gönderilip gönderilmeyeceğini belirler. Örnek gönderimini denetlemek için üç düzey vardır:

- **Hiçbiri**: Microsoft'a şüpheli örnek gönderilmez.
- **Kasa**: Yalnızca kişisel bilgiler (PII) içermeyen şüpheli örnekler otomatik olarak gönderilir. Bu ayar için varsayılan değer budur.
- **Tümü**: Tüm şüpheli örnekler Microsoft'a gönderilir.

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|automaticSampleSubmissionConsent|
|**Veri türü**|Dize|
|**Olası değerler**|Hiçbiri <p> güvenli (varsayılan) <p> Tüm|
|

#### <a name="enable--disable-automatic-security-intelligence-updates"></a>Otomatik güvenlik bilgileri güncelleştirmelerini etkinleştirme/devre dışı bırakma

Güvenlik zekası güncelleştirmelerinin otomatik olarak yüklenip yüklenmediğini belirler:

<br>

****

|Açıklama|Değer|
|---|---|
|**Anahtar**|automaticDefinitionUpdateEnabled|
|**Veri türü**|Boole|
|**Olası değerler**|true (varsayılan) <p> False|
|

## <a name="recommended-configuration-profile"></a>Önerilen yapılandırma profili

Başlamak için, uç nokta için Defender'ın sağladığı tüm koruma özelliklerinden yararlanmak üzere kuruluşunuz için aşağıdaki yapılandırma profilini öneririz.

Aşağıdaki yapılandırma profili şunları yapacaktır:

- Gerçek zamanlı korumayı etkinleştirme (RTP)
- Aşağıdaki tehdit türlerinin nasıl işleneceğini belirtin:
  - **İstenmeyebilecek uygulamalar (PUA)** engellendi
  - **Arşiv bombaları** (yüksek sıkıştırma oranına sahip dosya) ürün günlükleri için denetleniyor
- Otomatik güvenlik bilgileri güncelleştirmelerini etkinleştirme
- Bulut tabanlı korumayı etkinleştirme
- Düzeyinde otomatik örnek göndermeyi `safe` etkinleştirme
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

Aşağıdaki yapılandırma profili, bu belgede açıklanan tüm ayarların girdilerini içerir ve ürün üzerinde daha fazla denetime sahip olmak istediğiniz daha gelişmiş senaryolar için kullanılabilir.

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

komutu ilk kez çalıştırdığınızda `mdatp health` , etiket ve grup kimliği değeri boş olur. Dosyaya etiket veya grup kimliği eklemek için `mdatp_managed.json` aşağıdaki adımları izleyin:
  
  1. yolundan `/etc/opt/microsoft/mdatp/managed/mdatp_managed.json`yapılandırma profilini açın.
  2. Bloğun bulunduğu `cloudService` dosyanın en altına gidin.
  3. gerekli etiketi veya grup kimliğini, için kapanış küme ayracı `cloudService`sonuna aşağıdaki örnek olarak ekleyin.

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
  > Bloğun sonundaki `cloudService` kapanış küme ayracından sonra virgül eklemeyi unutmayın. Ayrıca Etiket veya Grup Kimliği bloğu eklendikten sonra iki kapatma köşeli ayracı olduğundan emin olun (lütfen yukarıdaki örneğe bakın). Şu anda etiketler için desteklenen tek anahtar adıdır `GROUP`. 
  
## <a name="configuration-profile-validation"></a>Yapılandırma profili doğrulaması

Yapılandırma profili geçerli bir JSON biçimli dosya olmalıdır. Bunu doğrulamak için kullanılabilecek çeşitli araçlar vardır. Örneğin, cihazınıza yüklediyseniz `python` :

```bash
python -m json.tool mdatp_managed.json
```

JSON iyi biçimlendirilmişse, yukarıdaki komut onu Terminal'e geri gönderir ve çıkış kodunu `0`döndürür. Aksi takdirde, sorunu açıklayan bir hata görüntülenir ve komutu çıkış `1`kodunu döndürür.

## <a name="verifying-that-the-mdatp_managedjson-file-is-working-as-expected"></a>mdatp_managed.json dosyasının beklendiği gibi çalıştığını doğrulama

/etc/opt/microsoft/mdatp/managed/mdatp_managed.json dosyanızın düzgün çalıştığını doğrulamak için şu ayarların yanında "[managed]" ifadesini görmeniz gerekir:

- cloud_enabled
- cloud_automatic_sample_submission_consent
- passive_mode_enabled
- real_time_protection_enabled
- automatic_definition_update_enabled

> [!NOTE]
> mdatp_managed.json dosyasının etkili olması için deamon'un `mdatp` yeniden başlatılması gerekmez.

## <a name="configuration-profile-deployment"></a>Yapılandırma profili dağıtımı

Kuruluşunuz için yapılandırma profilini derledikten sonra, kuruluşunuzun kullandığı yönetim aracı aracılığıyla dağıtabilirsiniz. Linux'ta Uç Nokta için Defender yönetilen yapılandırmayı */etc/opt/microsoft/mdatp/managed/mdatp_managed.json dosyasından* okur.
