---
title: Mac'te Uç Nokta için Microsoft Defender tercihlerini ayarlama
description: Büyük kuruluşlarda Mac'te Uç Nokta için Microsoft Defender'ı yapılandırma.
keywords: microsoft, defender, Endpoint için Microsoft Defender, mac, yönetim, tercihler, kurumsal, intune, jamf, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: 07e91e5b2cb93a6ba876510b558761f95489f496
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011857"
---
# <a name="set-preferences-for-microsoft-defender-for-endpoint-on-macos"></a>macOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlama

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [macOS'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!IMPORTANT]
> Bu makalede, kurumsal kuruluşlarda macOS üzerinde Uç Nokta için Microsoft Defender tercihlerini ayarlama ile ilgili yönergeler yer almaktadır. Komut satırı arabirimini kullanarak macOS'ta Uç Nokta için Microsoft Defender'ı yapılandırmak için bkz. [Kaynaklar](mac-resources.md#configuring-from-the-command-line).

## <a name="summary"></a>Özet

Kurumsal kuruluşlarda, macOS üzerinde Uç Nokta için Microsoft Defender çeşitli yönetim araçlarından biri kullanılarak dağıtılan bir yapılandırma profili aracılığıyla yönetilebilir. Güvenlik işlemleri ekipleri tarafından yönetilen tercihler, cihazda yerel olarak ayarlanmış tercihlere göre önceliklidir. Yapılandırma profili aracılığıyla ayarlanmış tercihlerin değiştirilmesi için, yükseltme ayrıcalıkları gerekir ve yönetici izinleri olmayan kullanıcılar için kullanılamaz.

Bu makalede yapılandırma profilinin yapısı açıklanmıştır, kullanmaya başlamanız için kullanabileceğiniz önerilen bir profil ve profilin dağıtımıyla ilgili yönergeler yer almaktadır.

## <a name="configuration-profile-structure"></a>Yapılandırma profili yapısı

Yapılandırma profili, bir anahtarla tanımlanan (tercihin adını belirtir) girdilerden ve ardından tercihin yapısına bağlı olarak bir değerden oluşan *bir .plist* dosyasıdır. Değerler basit (sayısal değer gibi) veya iç içe geçmiş tercih listesi gibi karmaşık olabilir.

> [!CAUTION]
>Yapılandırma profilinin düzeni, kullandığınız yönetim konsoluna bağlıdır. Aşağıdaki bölümlerde JAMF ve Intune için yapılandırma profili örnekleri verilmiştir.

Yapılandırma profilinin en üst düzeyi, sonraki bölümlerde daha ayrıntılı olarak açıklanan Uç Nokta için Microsoft Defender'ın alt bölümlerine yapılan ürün genelinde tercihler ve girdileri içerir.

### <a name="antivirus-engine-preferences"></a>Virüsten koruma altyapısı tercihleri

Yapılandırma *profilinin virüsten* koruma bölümü, Uç Nokta için Microsoft Defender'ın virüsten koruma bileşeninin tercihlerini yönetmek için kullanılır.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|antivirusEngine|
|**Veri türü**|Sözlük (iç içe tercih)|
|**Açıklamalar**|Sözlük içeriğinin açıklaması için aşağıdaki bölümlere bakın.|
|||

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
  - Durum menüsü simgesi gizlenmiş.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|enforcementLevel|
|**Veri türü**|Dize|
|**Olası değerler**|real_time (varsayılan) <p> on_demand <p> edilgen|
|**Açıklamalar**|Uç nokta sürüm 101.10.72 veya üzerinde Microsoft Defender'da kullanılabilir.|
|||

#### <a name="run-a-scan-after-definitions-are-updated"></a>Tanımlar güncelleştirildikten sonra taramayı çalıştırma

Cihaza yeni güvenlik zekası güncelleştirmeleri indirildikten sonra bir işlem taraması başlatıp başlatmayacağız belirtir. Bu ayarın etkinleştirilmesi, cihazın çalışan işlemlerinin virüsten koruma taramasını tetikler.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|scanAfterDefinitionUpdate|
|**Veri türü**|Boole|
|**Olası değerler**|true (varsayılan) <p> false|
|**Açıklamalar**|Uç nokta sürüm 101.41.10 veya üzerinde Microsoft Defender'da kullanılabilir.|
|||

#### <a name="scan-archives-on-demand-antivirus-scans-only"></a>Arşivleri tarama (yalnızca isteğe bağlı virüsten koruma taramaları)

isteğe bağlı virüsten koruma taramaları sırasında arşivlerin taranıp taranmasının gerekip gerek olmadığını belirtir.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|scanArchives|
|**Veri türü**|Boole|
|**Olası değerler**|true (varsayılan) <p> false|
|**Açıklamalar**|Uç nokta sürüm 101.41.10 veya üzerinde Microsoft Defender'da kullanılabilir.|
|||

#### <a name="degree-of-parallelism-for-on-demand-scans"></a>Isteğe bağlı taramalar için paralellik derecesi

Isteğe bağlı taramalar için paralellik derecesini belirtir. Bu, taramayı gerçekleştirmek için kullanılan iş parçacığı sayısına karşılık gelen CPU kullanımını ve isteğe bağlı tarama süresini etkiler.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|maximumOnDemandScanThreads|
|**Veri türü**|Tamsayı|
|**Olası değerler**|2 (varsayılan). İzin verilen değerler 1 ile 64 arasındaki tamsayılardır.|
|**Açıklamalar**|Uç nokta sürüm 101.41.10 veya üzerinde Microsoft Defender'da kullanılabilir.|
|||

#### <a name="exclusion-merge-policy"></a>Dışlama birleştirme ilkesi

Dışlamalar için birleştirme ilkesi belirtin. Bu, yönetici tanımlı ve kullanıcı tanımlı dışlamaların ()`merge` veya yalnızca yönetici tanımlı dışlamaların ()`admin_only` bir bileşimi olabilir. Bu ayar, yerel kullanıcıların kendi dışlamalarını tanımlamalarını kısıtlamak için kullanılabilir.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|exclusionsMergePolicy|
|**Veri türü**|Dize|
|**Olası değerler**|birleştirme (varsayılan) <p> admin_only|
|**Açıklamalar**|Uç nokta sürüm 100.83.73 veya üzerinde Microsoft Defender'da kullanılabilir.|
|||

#### <a name="scan-exclusions"></a>Tarama dışlamaları

Taranma dışında bırakılan varlıkları belirtin. Dışlamalar tam yollar, uzantılar veya dosya adlarla belirtilebilir.
(Dışlamalar bir öğe dizisi olarak belirtilir, yönetici herhangi bir sırada, gereken sayıda öğe belirtilebilir.)

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|dışlamalar|
|**Veri türü**|Sözlük (iç içe tercih)|
|**Açıklamalar**|Sözlük içeriğinin açıklaması için aşağıdaki bölümlere bakın.|
|||

##### <a name="type-of-exclusion"></a>Dışlama türü

Türe göre taranma dışında bırakılan içeriği belirtin.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|$type|
|**Veri türü**|Dize|
|**Olası değerler**|excludedPath <p> excludedFileExtension <p> excludedFileName|
|||

##### <a name="path-to-excluded-content"></a>Dışarıda bırakılan içeriğin yolu

Tam dosya yolu ile taranma dışında bırakılan içeriği belirtin.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|yol|
|**Veri türü**|Dize|
|**Olası değerler**|geçerli yollar|
|**Açıklamalar**|Yalnızca *dışlanan* *$type Path olduğunda uygulanabilir*|
|||

## <a name="supported-exclusion-types"></a>Desteklenen dışlama türleri

Aşağıdaki tablo Mac'te Uç Nokta için Defender tarafından desteklenen dışlama türlerini gösterir.

<br>

****

|Dışlama|Tanım|Örnekler|
|---|---|---|
|Dosya uzantısı|Uzantılı tüm dosyalar, cihazın herhangi bir yerinde|`.test`|
|Dosya|Tam yoldan tanımlanan belirli bir dosya|`/var/log/test.log` <p> `/var/log/*.log` <p> `/var/log/install.?.log`|
|Klasör|Belirtilen klasörün altındaki tüm dosyalar (tekrarlı bir şekilde)|`/var/log/` <p> `/var/*/`|
|İşlem|Belirli bir işlem (tam yol veya dosya adı ile belirtilen işlem) ve bu dosya tarafından açılan tüm dosyalar|`/bin/cat` <p> `cat` <p> `c?t`|
||||

> [!IMPORTANT]
> Başarıyla dışlamak için yukarıdaki yollar sembolik bağlantı değil, sabit bağlantılar olmalı. 'i çalıştırarak yolun sembolik bir bağlantı olup olduğunu kontrol edin `file <path-name>`.

Dosya, klasör ve süreç dışlamaları aşağıdaki joker karakterleri destekler:

<br>

****

|Joker karakter|Açıklama|Örnek|Eşleşmeler|Eşmser değil|
|---|---|---|---|---|
|\*|Hiçbiri dahil herhangi bir sayıda karakterle eşler (bu joker karakterin yol içinde kullanılırken tek bir klasörün yerini alamayacaktır)|`/var/\*/\*.log`|`/var/log/system.log`|`/var/log/nested/system.log`|
|?|Herhangi bir tek karakterle eşler|`file?.log`|`file1.log` <p> `file2.log`|`file123.log`|
||||||

### <a name="path-type-file--directory"></a>Yol türü (dosya / dizin)

Yol özelliğinin *bir* dosyaya veya dizine başvurup başvurduğuna işaret eder.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|isDirectory|
|**Veri türü**|Boole|
|**Olası değerler**|false (varsayılan) <p> true|
|**Açıklamalar**|Yalnızca *dışlanan* *$type Path olduğunda uygulanabilir*|
|||

### <a name="file-extension-excluded-from-the-scan"></a>Tarama dışında bırakılan dosya uzantısı

Dosya uzantısıyla taranma dışında bırakılan içeriği belirtin.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|uzantı|
|**Veri türü**|Dize|
|**Olası değerler**|geçerli dosya uzantıları|
|**Açıklamalar**|Yalnızca $type *excludedFileExtension olduğunda uygulanabilir* |
|||

### <a name="process-excluded-from-the-scan"></a>Tarama dışında bırakılan işlem

Tüm dosya etkinliğinin tarama dışında tutulacak bir işlem belirtme. İşlem, adına (örneğin, ) veya tam yola (örneğin, `cat`) göre belirtilebilir `/bin/cat`.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|ad|
|**Veri türü**|Dize|
|**Olası değerler**|herhangi bir dize|
|**Açıklamalar**|Yalnızca $type *DosyaAdı dışlanmışsa uygulanabilir* |
|||

#### <a name="allowed-threats"></a>İzin verilen tehdit

Mac'te Uç Nokta için Defender tarafından engel tehdit olarak belirtebilirsiniz. Bu tehditlerin çalışmasına izin verilir.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|allowedThreats|
|**Veri türü**|Dize dizisi|
|||

#### <a name="disallowed-threat-actions"></a>Tehdit eylemlerine izin verilmedi

Bir cihazın yerel kullanıcılarının tehdit algılandığında gerçekleştire eylemleri kısıtlar. Bu listede yer alan eylemler kullanıcı arabiriminde görüntülenmez.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|disallowedThreatActions|
|**Veri türü**|Dize dizisi|
|**Olası değerler**|izin ver (kullanıcıların tehditlere izin vermelerini kısıtlar) <p> geri yükleme (kullanıcıların karantinadan tehditleri geri yüklemesini kısıtlar)|
|**Açıklamalar**|Uç nokta sürüm 100.83.73 veya üzerinde Microsoft Defender'da kullanılabilir.|
|||

#### <a name="threat-type-settings"></a>Tehdit türü ayarları

MacOS'ta Uç Nokta için Microsoft Defender tarafından bazı tehdit türlerinin nasıl ele alıl olduğunu belirtin.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|threatTypeSettings|
|**Veri türü**|Sözlük (iç içe tercih)|
|**Açıklamalar**|Sözlük içeriğinin açıklaması için aşağıdaki bölümlere bakın.|
|||

##### <a name="threat-type"></a>Tehdit türü

Tehdit türlerini belirtin.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|anahtar|
|**Veri türü**|Dize|
|**Olası değerler**|potentially_unwanted_application <p> archive_bomb|
|||

##### <a name="action-to-take"></a>Alacak eylem

Önceki bölümde belirtilen türde bir tehdit algılandığında hangi eylemin geçerli olduğunu belirtin. Aşağıdaki seçeneklerden birini belirleyin:

- **Denetim**: Cihazınız bu tür tehditlere karşı korunmaz, ancak tehditle ilgili bir giriş günlüğe kaydedilir.
- **Engelle**: Cihazınız bu tür tehditlere karşı korunmaktadır ve kullanıcı arabirimi ve güvenlik konsolunda bu durum size bildirilecek.
- **Kapalı**: Cihazınız bu tür tehditlere karşı korunmaz ve hiçbir şey günlüğe kaydedilmez.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|değer|
|**Veri türü**|Dize|
|**Olası değerler**|denetim (varsayılan) <p> engelle <p> Kapalı|
|||

#### <a name="threat-type-settings-merge-policy"></a>Tehdit türü ayarları birleştirme ilkesi

Tehdit türü ayarları için birleştirme ilkesi belirtin. Bu, yönetici tanımlı ve kullanıcı tanımlı ayarların (`merge`) veya yalnızca yönetici tanımlı ayarların () bir bileşimi olabilir`admin_only`. Bu ayar, yerel kullanıcıların farklı tehdit türleri için kendi ayarlarını tanımlamalarını kısıtlamak için kullanılabilir.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|threatTypeSettingsMergePolicy|
|**Veri türü**|Dize|
|**Olası değerler**|birleştirme (varsayılan) <p> admin_only|
|**Açıklamalar**|Uç nokta sürüm 100.83.73 veya üzerinde Microsoft Defender'da kullanılabilir.|
|||

#### <a name="antivirus-scan-history-retention-in-days"></a>Virüsten koruma tarama geçmişi bekletme (gün içinde)

Sonuçların cihaz tarama geçmişinde kaç gün korunacaklarını belirtin. Eski tarama sonuçları geçmişten kaldırılır. Diskten de kaldırılan eski karantinaya alınmış dosyalar.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|scanResultsRetentionDays|
|**Veri türü**|Dize|
|**Olası değerler**|90 (varsayılan). İzin verilen değerler 1 günden 180 güne kadardır.|
|**Açıklamalar**|Uç nokta sürüm 101.07.23 veya üzerinde Microsoft Defender'da kullanılabilir.|
|||

#### <a name="maximum-number-of-items-in-the-antivirus-scan-history"></a>Virüsten koruma tarama geçmişinde en fazla öğe sayısı

Tarama geçmişinde tutmak istediğiniz girdi sayısı üst sayısını belirtin. Girdiler, geçmişte gerçekleştirilen tüm isteğe bağlı taramaları ve tüm virüsten koruma algılamalarını içerir.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|scanHistoryMaximumItems|
|**Veri türü**|Dize|
|**Olası değerler**|10000 (varsayılan). İzin verilen değerler 5000 öğeden 15000 öğeye kadardır.|
|**Açıklamalar**|Uç nokta sürüm 101.07.23 veya üzerinde Microsoft Defender'da kullanılabilir.|
|||

### <a name="cloud-delivered-protection-preferences"></a>Bulut teslimi koruma tercihleri

macOS'ta Uç Nokta için Microsoft Defender'ın bulut tabanlı koruma özelliklerini yapılandırın.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|cloudService|
|**Veri türü**|Sözlük (iç içe tercih)|
|**Açıklamalar**|Sözlük içeriğinin açıklaması için aşağıdaki bölümlere bakın.|
|||

#### <a name="enable--disable-cloud-delivered-protection"></a>Bulut teslimi korumasını etkinleştirme / devre dışı bırakma

Cihazda bulut teslimi korumasını etkinleştirip etkinleştirmeymezseniz belirtin. Hizmetlerinizin güvenliğini geliştirmek için bu özelliği açık tutmanızı öneririz.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|etkin|
|**Veri türü**|Boole|
|**Olası değerler**|true (varsayılan) <p> false|
|||

#### <a name="diagnostic-collection-level"></a>Tanılama koleksiyonu düzeyi

Tanılama verileri, Uç nokta için Microsoft Defender'ı güvenli ve güncel tutmak, sorunları algılamak, tanılamak ve düzeltmek ve ürün geliştirmeleri yapmak için kullanılır. Bu ayar, Uç Nokta için Microsoft Defender tarafından Microsoft'a gönderilen tanılama düzeyini belirler.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|diagnosticLevel|
|**Veri türü**|Dize|
|**Olası değerler**|isteğe bağlı (varsayılan) <p> Gerekli|
|||

#### <a name="enable--disable-automatic-sample-submissions"></a>Otomatik örnek gönderimleri etkinleştirme / devre dışı bırakma

Şüpheli örneklerin (tehdit içerme olasılığı olan) Microsoft'a gönder olup olmadığını belirler. Gönderilen dosyanın büyük olasılıkla kişisel bilgi içermesi istenir.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|automaticSampleSubmission|
|**Veri türü**|Boole|
|**Olası değerler**|true (varsayılan) <p> false|
|||

#### <a name="enable--disable-automatic-security-intelligence-updates"></a>Otomatik güvenlik zekası güncelleştirmelerini etkinleştirme / devre dışı bırakma

Güvenlik zekası güncelleştirmelerinin otomatik olarak yük olup olmadığını belirler:

<br>

****

|Bölüm|Değer|
|---|---|
|**Anahtar**|automaticDefinitionUpdateEnabled|
|**Veri türü**|Boole|
|**Olası değerler**|true (varsayılan) <p> false|
|||

### <a name="user-interface-preferences"></a>Kullanıcı arabirimi tercihleri

macOS'ta Uç Nokta için Microsoft Defender kullanıcı arabirimi tercihlerini yönetin.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|userInterface|
|**Veri türü**|Sözlük (iç içe tercih)|
|**Açıklamalar**|Sözlük içeriğinin açıklaması için aşağıdaki bölümlere bakın.|
|||

#### <a name="show--hide-status-menu-icon"></a>Durum menüsünü göster / gizle simgesi

Ekranın sağ üst köşesindeki durum menüsü simgesinin göster mi yoksa gizleyip gizlenmezseniz belirtin.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|hideStatusMenuIcon|
|**Veri türü**|Boole|
|**Olası değerler**|false (varsayılan) <p> true|
|||

#### <a name="show--hide-option-to-send-feedback"></a>Geri bildirim göndermek için göster / gizle seçeneği

Kullanıcıların Microsoft'a geri bildirim gönderip gönderemezseniz, 'a gidip bunu belirtme `Help` > `Send Feedback`.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|userInitiatedFeedback|
|**Veri türü**|Dize|
|**Olası değerler**|etkin (varsayılan) <p> devre dışı|
|**Açıklamalar**|Uç nokta sürüm 101.19.61 veya üzerinde Microsoft Defender'da kullanılabilir.|
|||

### <a name="endpoint-detection-and-response-preferences"></a>Uç nokta algılama ve yanıt tercihleri

macOS'ta Uç uç noktada algılama ve yanıtlama için Microsoft Defender'EDR Uç Nokta(EDR) bileşeninin tercihlerini yönetin.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|edr|
|**Veri türü**|Sözlük (iç içe tercih)|
|**Açıklamalar**|Sözlük içeriğinin açıklaması için aşağıdaki bölümlere bakın.|
|||

#### <a name="device-tags"></a>Cihaz etiketleri

Etiket adını ve değerini belirtin.

- GROUP etiketi, cihazı belirtilen değerle etiketler. Etiket, cihaz sayfasının altındaki portala yansıtılmaktadır ve filtreleme ve gruplama cihazları için kullanılabilir.

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|etiketler|
|**Veri türü**|Sözlük (iç içe tercih)|
|**Açıklamalar**|Sözlük içeriğinin açıklaması için aşağıdaki bölümlere bakın.|
|||

##### <a name="type-of-tag"></a>Etiket türü

Etiketin türünü belirtir

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|anahtar|
|**Veri türü**|Dize|
|**Olası değerler**|`GROUP`|
|||

##### <a name="value-of-tag"></a>Etiket değeri

Etiketin değerini belirtir

<br>

****

|Bölüm|Değer|
|---|---|
|**Etki alanı**|`com.microsoft.wdav`|
|**Anahtar**|değer|
|**Veri türü**|Dize|
|**Olası değerler**|herhangi bir dize|
|||

> [!IMPORTANT]
>
> - Etiket türü başına yalnızca bir değer ayarlanabilirsiniz.
> - Etiketlerin türü benzersizdir ve aynı yapılandırma profilinde yinelenene kadar yinelenir.

## <a name="recommended-configuration-profile"></a>Önerilen yapılandırma profili

Çalışmaya başlamanız için, aşağıdaki yapılandırmanın kurum için Microsoft Defender for Endpoint'ın sağladığı tüm koruma özelliklerinden yararlanmasını öneririz.

Aşağıdaki yapılandırma profili (veya JAMF durumunda, özel ayarlar yapılandırma profiline yüklen listeden bir özellik listesi) şu şekilde olur:

- Gerçek zamanlı korumayı (RTP) etkinleştirme
- Aşağıdaki tehdit türlerinin nasıl iş idaresi olduğunu belirtin:
  - **İstenmeyen olabilecek uygulamalar (PUA)** engellenmiş
  - **Arşiv arşiv** (yüksek sıkıştırma hızı olan dosya) Uç nokta günlükleri için Microsoft Defender'da denetlendi
- Otomatik güvenlik zekası güncelleştirmelerini etkinleştirme
- Bulut teslimi korumasını etkinleştirme
- Otomatik örnek gönderimi etkinleştirme

### <a name="property-list-for-jamf-recommended-configuration-profile"></a>JAMF önerilen yapılandırma profili için özellik listesi

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>antivirusEngine</key>
    <dict>
        <key>enforcementLevel</key>
        <string>real_time</string>
        <key>threatTypeSettings</key>
        <array>
            <dict>
                <key>key</key>
                <string>potentially_unwanted_application</string>
                <key>value</key>
                <string>block</string>
            </dict>
            <dict>
                <key>key</key>
                <string>archive_bomb</string>
                <key>value</key>
                <string>audit</string>
            </dict>
        </array>
    </dict>
    <key>cloudService</key>
    <dict>
        <key>enabled</key>
        <true/>
        <key>automaticSampleSubmission</key>
        <true/>
        <key>automaticDefinitionUpdateEnabled</key>
        <true/>
    </dict>
</dict>
</plist>
```

### <a name="intune-recommended-profile"></a>Intune önerilen profil

```XML
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>com.microsoft.wdav</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender for Endpoint settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft Defender for Endpoint configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
                <key>PayloadUUID</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadType</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadOrganization</key>
                <string>Microsoft</string>
                <key>PayloadIdentifier</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadDisplayName</key>
                <string>Microsoft Defender for Endpoint configuration settings</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>antivirusEngine</key>
                <dict>
                    <key>enforcementLevel</key>
                    <string>real_time</string>
                    <key>threatTypeSettings</key>
                    <array>
                        <dict>
                            <key>key</key>
                            <string>potentially_unwanted_application</string>
                            <key>value</key>
                            <string>block</string>
                        </dict>
                        <dict>
                            <key>key</key>
                            <string>archive_bomb</string>
                            <key>value</key>
                            <string>audit</string>
                        </dict>
                    </array>
                </dict>
                <key>cloudService</key>
                <dict>
                    <key>enabled</key>
                    <true/>
                    <key>automaticSampleSubmission</key>
                    <true/>
                    <key>automaticDefinitionUpdateEnabled</key>
                    <true/>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

## <a name="full-configuration-profile-example"></a>Tam yapılandırma profili örneği

Aşağıdaki şablonlar, bu belgede açıklanan tüm ayarlar için girdiler içerir ve macOS'ta Uç Nokta için Microsoft Defender üzerinde daha fazla denetime sahip olmak istediğiniz daha gelişmiş senaryolarda kullanılabilir.

### <a name="property-list-for-jamf-full-configuration-profile"></a>JAMF tam yapılandırma profili için özellik listesi

```XML
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
    <key>antivirusEngine</key>
    <dict>
        <key>enforcementLevel</key>
        <string>real_time</string>
        <key>scanAfterDefinitionUpdate</key>
        <true/>
        <key>scanArchives</key>
        <true/>
        <key>maximumOnDemandScanThreads</key>
        <integer>2</integer>
        <key>exclusions</key>
        <array>
            <dict>
                <key>$type</key>
                <string>excludedPath</string>
                <key>isDirectory</key>
                <false/>
                <key>path</key>
                <string>/var/log/system.log</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedPath</string>
                <key>isDirectory</key>
                <true/>
                <key>path</key>
                <string>/home</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedPath</string>
                <key>isDirectory</key>
                <true/>
                <key>path</key>
                <string>/Users/*/git</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedFileExtension</string>
                <key>extension</key>
                <string>pdf</string>
            </dict>
            <dict>
                <key>$type</key>
                <string>excludedFileName</string>
                <key>name</key>
                <string>cat</string>
            </dict>
        </array>
        <key>exclusionsMergePolicy</key>
        <string>merge</string>
        <key>allowedThreats</key>
        <array>
            <string>EICAR-Test-File (not a virus)</string>
        </array>
        <key>disallowedThreatActions</key>
        <array>
            <string>allow</string>
            <string>restore</string>
        </array>
        <key>threatTypeSettings</key>
        <array>
            <dict>
                <key>key</key>
                <string>potentially_unwanted_application</string>
                <key>value</key>
                <string>block</string>
            </dict>
            <dict>
                <key>key</key>
                <string>archive_bomb</string>
                <key>value</key>
                <string>audit</string>
            </dict>
        </array>
        <key>threatTypeSettingsMergePolicy</key>
        <string>merge</string>
    </dict>
    <key>cloudService</key>
    <dict>
        <key>enabled</key>
        <true/>
        <key>diagnosticLevel</key>
        <string>optional</string>
        <key>automaticSampleSubmission</key>
        <true/>
        <key>automaticDefinitionUpdateEnabled</key>
        <true/>
    </dict>
    <key>edr</key>
    <dict>
        <key>tags</key>
        <array>
            <dict>
                <key>key</key>
                <string>GROUP</string>
                <key>value</key>
                <string>ExampleTag</string>
            </dict>
        </array>
    </dict>
    <key>userInterface</key>
    <dict>
        <key>hideStatusMenuIcon</key>
        <false/>
        <key>userInitiatedFeedback</key>
        <string>enabled</string>
    </dict>
</dict>
</plist>
```

### <a name="intune-full-profile"></a>Intune tam profili

```XML
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1">
    <dict>
        <key>PayloadUUID</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadType</key>
        <string>Configuration</string>
        <key>PayloadOrganization</key>
        <string>Microsoft</string>
        <key>PayloadIdentifier</key>
        <string>C4E6A782-0C8D-44AB-A025-EB893987A295</string>
        <key>PayloadDisplayName</key>
        <string>Microsoft Defender for Endpoint settings</string>
        <key>PayloadDescription</key>
        <string>Microsoft Defender for Endpoint configuration settings</string>
        <key>PayloadVersion</key>
        <integer>1</integer>
        <key>PayloadEnabled</key>
        <true/>
        <key>PayloadRemovalDisallowed</key>
        <true/>
        <key>PayloadScope</key>
        <string>System</string>
        <key>PayloadContent</key>
        <array>
            <dict>
                <key>PayloadUUID</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadType</key>
                <string>com.microsoft.wdav</string>
                <key>PayloadOrganization</key>
                <string>Microsoft</string>
                <key>PayloadIdentifier</key>
                <string>99DBC2BC-3B3A-46A2-A413-C8F9BB9A7295</string>
                <key>PayloadDisplayName</key>
                <string>Microsoft Defender for Endpoint configuration settings</string>
                <key>PayloadDescription</key>
                <string/>
                <key>PayloadVersion</key>
                <integer>1</integer>
                <key>PayloadEnabled</key>
                <true/>
                <key>antivirusEngine</key>
                <dict>
                    <key>enforcementLevel</key>
                    <string>real_time</string>
                    <key>scanAfterDefinitionUpdate</key>
                    <true/>
                    <key>scanArchives</key>
                    <true/>
                    <key>maximumOnDemandScanThreads</key>
                    <integer>1</integer>
                    <key>exclusions</key>
                    <array>
                        <dict>
                            <key>$type</key>
                            <string>excludedPath</string>
                            <key>isDirectory</key>
                            <false/>
                            <key>path</key>
                            <string>/var/log/system.log</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedPath</string>
                            <key>isDirectory</key>
                            <true/>
                            <key>path</key>
                            <string>/home</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedPath</string>
                            <key>isDirectory</key>
                            <true/>
                            <key>path</key>
                            <string>/Users/*/git</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedFileExtension</string>
                            <key>extension</key>
                            <string>pdf</string>
                        </dict>
                        <dict>
                            <key>$type</key>
                            <string>excludedFileName</string>
                            <key>name</key>
                            <string>cat</string>
                        </dict>
                    </array>
                    <key>exclusionsMergePolicy</key>
                    <string>merge</string>
                    <key>allowedThreats</key>
                    <array>
                        <string>EICAR-Test-File (not a virus)</string>
                    </array>
                    <key>disallowedThreatActions</key>
                    <array>
                        <string>allow</string>
                        <string>restore</string>
                    </array>
                    <key>threatTypeSettings</key>
                    <array>
                        <dict>
                            <key>key</key>
                            <string>potentially_unwanted_application</string>
                            <key>value</key>
                            <string>block</string>
                        </dict>
                        <dict>
                            <key>key</key>
                            <string>archive_bomb</string>
                            <key>value</key>
                            <string>audit</string>
                        </dict>
                    </array>
                    <key>threatTypeSettingsMergePolicy</key>
                    <string>merge</string>
                </dict>
                <key>cloudService</key>
                <dict>
                    <key>enabled</key>
                    <true/>
                    <key>diagnosticLevel</key>
                    <string>optional</string>
                    <key>automaticSampleSubmission</key>
                    <true/>
                    <key>automaticDefinitionUpdateEnabled</key>
                    <true/>
                </dict>
                <key>edr</key>
                <dict>
                    <key>tags</key>
                    <array>
                        <dict>
                            <key>key</key>
                            <string>GROUP</string>
                            <key>value</key>
                            <string>ExampleTag</string>
                        </dict>
                    </array>
                </dict>
                <key>userInterface</key>
                <dict>
                    <key>hideStatusMenuIcon</key>
                    <false/>
                    <key>userInitiatedFeedback</key>
                    <string>enabled</string>
                </dict>
            </dict>
        </array>
    </dict>
</plist>
```

## <a name="property-list-validation"></a>Özellik listesi doğrulaması

Özellik listesi geçerli bir *.plist dosyası* olmalıdır. Bunu yürütmekle denetlenir:

```bash
plutil -lint com.microsoft.wdav.plist
```

```Output
com.microsoft.wdav.plist: OK
```

Dosya iyi düz ise, yukarıdaki komut çıktısını verir `OK` ve 'ın çıkış kodunu verir `0`. Aksi takdirde, sorunu açıklayan bir hata görüntülenir ve komut bir çıkış kodu verir `1`.

## <a name="configuration-profile-deployment"></a>Yapılandırma profili dağıtımı

Kurumunuzun yapılandırma profilini hazır bulunduktan sonra, bu profili kurumunuzun kullanmakta olduğu yönetim konsolu aracılığıyla dağıtabilirsiniz. Aşağıdaki bölümlerde, JAMF ve Intune kullanarak bu profilin dağıtımıyla ilgili yönergeler sağlanmıştır.

### <a name="jamf-deployment"></a>JAMF dağıtımı

JAMF konsolundan Bilgisayarlar  \> Yapılandırma Profilleri'ne **gidin, kullanmak** istediğiniz yapılandırma profiline gidin ve Özel Yapılandırma **Profilleri'Ayarlar**. Tercih etki alanı olarak `com.microsoft.wdav` bir girdi oluşturun ve daha önce üretilen *.plisti* karşıya yükleyin.

> [!CAUTION]
> Doğru tercih etki alanını girmeniz gerekir (`com.microsoft.wdav`); aksi takdirde, tercihler Uç Nokta için Microsoft Defender tarafından tanınmayacaktır.

### <a name="intune-deployment"></a>Intune dağıtımı

1. Cihaz **yapılandırmasını** \> **yönet'i açın**. Profilleri **Yönet** \> **Profil** **Oluştur'a**\> tıklayın.

2. Profil için bir ad seçin. **Platform=macOS'u Profil** türü **=Özel olarak değiştirme**. Yapılandır'ı seçin.

3. Daha önce 'olarak üretilen .plist'i kaydedin `com.microsoft.wdav.xml`.

4. Özel `com.microsoft.wdav` yapılandırma **profili adı olarak girin**.

5. Yapılandırma profilini açın ve dosyayı karşıya `com.microsoft.wdav.xml` yükleyin. (Bu dosya 3. adımda oluşturulmuş.

6. **Tamam**'ı seçin.

7. Ödevleri **Yönet'i** \> seçin. Ekle sekmesinde **Tüm** Cihazlarda Tüm **Kullanıcılara Ata'& seçin**.

> [!CAUTION]
> Doğru özel yapılandırma profili adını girmeniz gerekir; aksi takdirde, bu tercihler Uç Nokta için Microsoft Defender tarafından tanınamaz.

## <a name="resources"></a>Kaynaklar

- [Yapılandırma Profili Başvurusu (Apple geliştirici belgeleri)](https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf)
