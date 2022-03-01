---
title: Mac'te Uç Nokta için Microsoft Defender Gizliliği
description: Gizlilik denetimleri, Mac'te Uç Nokta için Microsoft Defender'da toplanan tanılama verileri hakkında gizliliği ve bilgileri etkileyen ilke ayarlarını yapılandırma.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mac, gizlilik, tanılama
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
ms.openlocfilehash: c49a6ff1440c7a3eee2e26eef90fb928e68458d1
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63014413"
---
# <a name="privacy-for-microsoft-defender-for-endpoint-on-macos"></a>macOS'ta Uç Nokta için Microsoft Defender Gizliliği

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Microsoft, macOS üzerinde Uç Nokta için Microsoft Defender kullanırken verilerinizin nasıl toplanacak ve kullanılacak konusunda seçim yapmak için ihtiyacınız olan bilgileri ve denetimleri sağlamayı taahhüt eder.

Bu konu başlığı altında, ürün içinde kullanılabilen gizlilik denetimleri, ilke ayarlarıyla bu denetimlerin nasıl yönetilebilecekleri ve toplanan veri olaylarla ilgili daha fazla ayrıntı açıklanmıştır.

## <a name="overview-of-privacy-controls-in-microsoft-defender-for-endpoint-on-macos"></a>macOS'ta Uç Nokta için Microsoft Defender'daki gizlilik denetimlerine genel bakış

Bu bölümde, macOS'ta Uç Nokta için Microsoft Defender tarafından toplanan farklı veri türleri için gizlilik denetimleri açıklanıyor.

### <a name="diagnostic-data"></a>Tanılama verileri

Tanılama verileri, Uç nokta için Microsoft Defender'ı güvenli ve güncel tutmak, sorunları algılamak, tanılamak ve düzeltmek ve ürün geliştirmeleri yapmak için kullanılır.

Bazı tanılama verileri isteğe bağlıyken bazı tanılama verileri gereklidir. Size, kuruluşlar için gizlilik ayarları gibi gizlilik denetimlerini kullanarak bize gerekli veya isteğe bağlı tanılama verilerini gönderip göndermeme olanağı sunarız.

Uç nokta istemci yazılımı için Microsoft Defender tanılama verilerini iki düzeyden birini seçebilirsiniz:

- **Gerekli**: Uç nokta için Microsoft Defender'ı güvenli, güncel ve yüklü olduğu cihazda beklendiği şekilde performans gösterirken tutmak için gereken en düşük veriler.

- **İsteğe** bağlı: Microsoft'un ürün geliştirmeleri yapmana yardımcı olan ve sorunları algılamaya, tanılamaya ve düzeltmeye yardımcı olacak gelişmiş bilgiler sağlayan ek veriler.

Varsayılan olarak, yalnızca gerekli tanılama verileri Microsoft'a gönderilir.

### <a name="cloud-delivered-protection-data"></a>Bulut teslimi koruma verileri

Bulut teslimi koruması, buluttaki en son koruma verilerine erişimle daha yüksek ve daha hızlı koruma sağlamak için kullanılır.

Bulut teslimi koruma hizmetinin etkinleştirilmesi isteğe bağlıdır, ancak uç noktalarınıza ve ağ genelinde kötü amaçlı yazılımlara karşı önemli bir koruma sağladığı için bu özelliğin kullanılması kesinlikle önerilir.

### <a name="sample-data"></a>Örnek veriler

Örnek veriler, çözümlenirken Microsoft'a şüpheli örnekler göndererek ürünün koruma özelliklerini geliştirmek için kullanılır. Otomatik örnek gönderimin etkinleştirilmesi isteğe bağlıdır.

Bu özellik etkinleştirildiğinde ve toplanan örneğin büyük olasılıkla kişisel bilgiler içerdiğinde, kullanıcıdan izin istenir.

## <a name="manage-privacy-controls-with-policy-settings"></a>Gizlilik denetimlerini ilke ayarlarıyla yönetme

Bir IT yöneticisiyseniz, bu denetimleri kuruluş düzeyinde yapılandırmak istediğiniz olabilir.

Önceki bölümde açıklanan çeşitli veri türleri için gizlilik denetimleri macOS üzerinde Uç nokta için Microsoft Defender tercihlerini ayarlama konusunda [ayrıntılı olarak açıklanmıştır](mac-preferences.md).

Yeni ilke ayarlarında olduğu gibi, ilke ayarlarını kurum içinde daha geniş bir alanla uygulamadan önce, yapılandırılan ayarların istediğiniz etkiyi elde etmek için bunları sınırlı, denetimli bir ortamda dikkatle test edin.

## <a name="diagnostic-data-events"></a>Tanılama veri olayları

Bu bölümde gerekli tanılama verileri olarak kabul edilenler, isteğe bağlı tanılama verileri olarak kabul edilenler ve toplanan olaylarla alanların açıklaması açıklanıyor.

### <a name="data-fields-that-are-common-for-all-events"></a>Tüm olaylar için ortak olan veri alanları

Kategorisi veya alt veri türü ne olursa olsun tüm olaylarda ortak olan olaylar hakkında bazı bilgiler bulunur.

Aşağıdaki alanlar tüm olaylar için ortak kabul edilir:

|Alan|Açıklama|
|---|---|
|platform|Uygulamanın çalıştır çalıştır olduğu platformun kapsamlı sınıflandırması. Microsoft'un sorunun hangi platformlarda ortaya çıkan bir sorun olduğunu belirlemesi ve doğru önceliklerin belirlenmesini sağlar.|
|machine_guid|Cihazla ilişkilendirilmiş benzersiz tanımlayıcı. Microsoft'un belirli bir yükleme dizisinde sorun olup olmadığını ve kaç kullanıcının etki etkisinin olduğunu belirlemesi için Microsoft'a olanak sağlar.|
|sense_guid|Cihazla ilişkilendirilmiş benzersiz tanımlayıcı. Microsoft'un belirli bir yükleme dizisinde sorun olup olmadığını ve kaç kullanıcının etki etkisinin olduğunu belirlemesi için Microsoft'a olanak sağlar.|
|org_id|Cihazın ait olduğu kuruluşla ilişkilendirilmiş benzersiz tanımlayıcı. Microsoft'un belirli bir kuruluş setlerini etkileyen sorunları ve kaç işletmeyi etkile ilgili olduğunu belirlemesi için Microsoft'a olanak sağlar.|
|ana bilgisayar adı|Yerel cihaz adı (DNS soneki olmadan). Microsoft'un belirli bir yükleme dizisinde sorun olup olmadığını ve kaç kullanıcının etki etkisinin olduğunu belirlemesi için Microsoft'a olanak sağlar.|
|product_guid|Ürünün benzersiz tanımlayıcısı. Microsoft'un ürünün farklı çeşitlerini etkileyen sorunları ayırt ingdir.|
|app_version|macOS uygulamasında Uç Nokta için Microsoft Defender sürümü. Microsoft'un, doğru önceliklendirmek için ürünün hangi sürümlerinin sorun gösterdiğini belirlemesi için izin verir.|
|sig_version|Güvenlik zekası veritabanı sürümü. Microsoft'un, güvenlik zekası sürümlerinin doğru önceliklendirmek için sorun gösterdiği sürümleri belirlemelerine olanak sağlar.|
|supported_compressions|Uygulama tarafından desteklenen sıkıştırma algoritmalarının listesi, örneğin `['gzip']`. Microsoft'un uygulamayla iletişim kurarken hangi tür sıkıştırmaların kullanıl olacağını anlamasına olanak sağlar.|
|release_ring|Cihazın ilişkilendirilen halkası (örneğin Insider Hızlı, Insider Yavaş, Üretim). Microsoft'un bir sorunun hangi sürüm halkası içinde olduğunu belirlemesi ve böylelikle doğru önceliklendirmeyi sağlar.|

### <a name="required-diagnostic-data"></a>Gerekli tanılama verileri

**Gerekli tanılama verileri** , uç nokta için Microsoft Defender'ı güvenli, güncel ve yüklü olduğu cihazda beklendiği şekilde gerçekleştirmeye yardımcı olmak için gereken minimum verilerdir.

Gerekli tanılama verileri, cihaz veya yazılım yapılandırmasıyla ilgili uç nokta için Microsoft Defender ile ilgili sorunları belirlemeye yardımcı olur. Örneğin, yeni eklenen özelliklerle birlikte belirli bir işletim sistemi sürümünde Uç Nokta için Microsoft Defender özelliğinin daha sık kilitleniyor mu yoksa uç nokta özellikleri için bazı Microsoft Defender devre dışı mı kilitleniyor? belirlemeye yardımcı olabilir. Gerekli tanılama verileri, Microsoft'un bu sorunları daha çabuk algılamasını, tanılamasını ve düzeltmesi için kullanıcıların veya kuruluşların etkisinin azalmasına yardımcı olur.

#### <a name="software-setup-and-inventory-data-events"></a>Yazılım kurulumu ve envanter veri olayları

**Uç nokta yüklemesi için Microsoft Defender / kaldırma**:

Aşağıdaki alanlar toplanır:

|Alan|Açıklama|
|---|---|
|correlation_id|Yüklemeyle ilişkili benzersiz tanımlayıcı.|
|Sürüm|Paketin sürümü.|
|önem derecesi|İletinin önem derecesi (örneğin Bilgilendirme).|
|kod|işlemi açıklayan kod.|
|metin|Ürün yüklemesi ile ilgili ek bilgiler.|

**Uç nokta yapılandırması için Microsoft Defender**:

Aşağıdaki alanlar toplanır:

|Alan|Açıklama|
|---|---|
|antivirus_engine.enable_real_time_protection|Gerçek zamanlı korumanın cihazda etkin olup olmadığı.|
|antivirus_engine.pasif_modu|Cihazda pasif modunun etkin olup olmadığı.|
|cloud_service.enabled|Cihazda bulut teslimi korumasının etkin olup olmadığı.|
|cloud_service.timeout|Uygulama Uç nokta bulutu için Microsoft Defender ile iletişim kurarken zaman out.|
|cloud_service.heartbeat_interval|Ürünün buluta gönderdiği ardışık sinyaller arasındaki aralık.|
|cloud_service.service_uri|Bulutla iletişim kurmak için kullanılan URI.|
|cloud_service.diagnostic_level|Cihazın tanılama düzeyi (gerekli, isteğe bağlı).|
|cloud_service.automatic_sample_submission|Otomatik örnek gönderimin açık olup olmadığı.|
|cloud_service.automatic_definition_update_enabled|Otomatik tanım güncelleştirmenin açık olup olmadığı.|
|edr.early_preview|Cihazın ilk önizleme özellikleri EDR çalıştırıp çalıştırması gerektiği.|
|edr.group_id|Algılama ve yanıt bileşeni tarafından kullanılan grup tanımlayıcısı.|
|edr.tags|Kullanıcı tanımlı etiketler.|
|özelliklerine sahiptir.\[ isteğe bağlı özellik adı\]|Önizleme özelliklerinin listesi ve bunların etkin olup olmadığı.|

#### <a name="product-and-service-usage-data-events"></a>Ürün ve hizmet kullanımı verisi olayları

**Güvenlik zekası güncelleştirme raporu**:

Aşağıdaki alanlar toplanır:

|Alan|Açıklama|
|---|---|
|from_version|İlk güvenlik zekası sürümü.|
|to_version|Yeni güvenlik zekası sürümü.|
|durum|Başarılı veya başarısız olduğunu gösteren güncelleştirmenin durumu.|
|using_proxy|Güncelleştirmenin proxy üzerinden yap isteyip olmadığı.|
|hatasını|Güncelleştirme başarısız olursa hata kodu.|
|Neden|Dosyalandı ise hata iletisi.|

#### <a name="product-and-service-performance-data-events-for-required-diagnostic-data"></a>Gerekli tanılama verileri için ürün ve hizmet performansı veri olayları

**Beklenmeyen uygulama çıkışı (kilitlenme)**:

Uygulama beklenmedik bir şekilde çıkışta olduğunda sistem bilgilerini ve uygulamanın durumunu toplar.

Aşağıdaki alanlar toplanır:

|Alan|Açıklama|
|---|---|
|v1_crash_count|İstemci makinesi üzerinde V1 altyapısı işleminin saatte bir kilitlenme sayısı|
|v2_crash_count|İstemci makinesi üzerinde V2 altyapısı işleminin saatte bir kilitlenme sayısı|
|EDR_crash_count|İstemci EDR her saatte bir kilitlenmeye neden olan kilitlenme sayısı|

**Çekirdek uzantısı istatistikleri**:

Aşağıdaki alanlar toplanır:

|Alan|Açıklama|
|---|---|
|Sürüm|macOS'ta Uç Nokta için Microsoft Defender Sürümü.|
|instance_id|Çekirdek uzantısı başlangıçta oluşturulan benzersiz tanımlayıcı.|
|trace_level|Çekirdek uzantısının izleme düzeyi.|
|alt sistem|Gerçek zamanlı koruma için temeldeki alt sistem kullanılır.|
|ipc.connects|Çekirdek uzantısıyla alınan bağlantı isteklerinin sayısı.|
|ipc.rejects|Çekirdek uzantısı tarafından reddedilen bağlantı isteklerinin sayısı.|
|ipc.connected|Çekirdek uzantısına etkin bağlantı olup olmadığı.|

#### <a name="support-data"></a>Destek verileri

**Tanılama günlükleri**:

Tanı günlükleri yalnızca geri bildirim gönderme özelliğinin bir parçası olarak kullanıcının onayıyla toplanır. Destek günlüklerinin bir parçası olarak aşağıdaki dosyalar toplanır:

- */Library/Logs/Microsoft/mdatp/ altındaki tüm dosyalar*
- macOS'ta Uç Nokta için Microsoft Defender tarafından oluşturulan ve kullanılan */Library/Application Support/Microsoft/Defender/* altındaki dosyaların alt kümesi
- macOS'ta Uç Nokta için Microsoft Defender tarafından kullanılan */Library/Managed Preferences* altındaki dosyaların alt kümesi
- /Library/Logs/Microsoft/autoupdate.log
- $HOME/Library/Preferences/com.microsoft.autoupdate2.plist

### <a name="optional-diagnostic-data"></a>İsteğe bağlı tanılama verileri

**İsteğe bağlı tanılama** verileri, Microsoft'un ürün geliştirmeleri yapmana yardımcı olan ve sorunları algılamaya, tanılamaya ve düzeltmeye yardımcı olacak gelişmiş bilgiler sağlayan ek verilerdir.

Bize isteğe bağlı tanılama verilerini göndermeyi seçerseniz, bu durum gerekli tanılama verilerini de içerir.

İsteğe bağlı tanılama verilerine örnek olarak, Microsoft'un ürün yapılandırması hakkında top aldığı veriler (örneğin, cihazda ayarlanmış dışlama sayısı) ve ürün performansı (ürünün bileşenlerinin performansıyla ilgili toplama ölçüleri) yer alır.

#### <a name="software-setup-and-inventory-data-events-for-optional-diagnostic-data"></a>İsteğe bağlı tanılama verileri için yazılım kurulumu ve stok verileri olayları

**Uç nokta yapılandırması için Microsoft Defender**:

Aşağıdaki alanlar toplanır:

|Alan|Açıklama|
|---|---|
|connection_retry_timeout|Bulutla iletişime geçken bağlantıda zaman outnı yeniden deneyin.|
|file_hash_cache_maximum|Ürün önbelleği boyutu.|
|crash_upload_daily_limit|Günlük olarak karşıya yüklenen kilitlenme günlükleri sınırı.|
|antivirus_engine.exclusions[].is_directory|Tarama dışında kalmanın bir dizin olup olmadığı.|
|antivirus_engine.exclusions[].path|Tarama dışında bırakılan yol.|
|antivirus_engine.exclusions[].extension|Tarama dışında bırakılan uzantı.|
|antivirus_engine.exclusions[].name|Tarama dışında bırakılan dosyanın adı.|
|antivirus_engine.scan_cache_maximum|Ürün önbelleği boyutu.|
|antivirus_engine.maximum_scan_threads|Tarama için kullanılan en fazla iş parçacığı sayısı.|
|antivirus_engine.threat_restore_exclusion_time|Dosya karantinadan geri yüklendi ancak yeniden algılanamaz.|
|antivirus_engine.threat_type_settings|Ürün tarafından farklı tehdit türlerinin nasıl ele handle handle?.|
|filesystem_scanner.full_scan_directory|Tam tarama dizini.|
|filesystem_scanner.quick_scan_directories|Hızlı taramada kullanılan dizinlerin listesi.|
|edr.latency_mode|Algılama ve yanıt bileşeni tarafından kullanılan gecikme süresi modu.|
|edr.proxy_address|Algılama ve yanıt bileşeni tarafından kullanılan ara sunucu adresi.|

**Microsoft Otomatik Güncelleştirme yapılandırması**:

Aşağıdaki alanlar toplanır:

|Alan|Açıklama|
|---|---|
|how_to_check|Ürün güncelleştirmelerinin nasıl denetlenir (örneğin otomatik veya el ile) belirler.|
|channel_name|Cihazla ilişkilendirilmiş kanalı güncelleştirin.|
|manifest_server|Güncelleştirmeleri indirmek için kullanılan sunucu.|
|update_cache|Güncelleştirmeleri depolamak için kullanılan önbelleğin konumu.|

### <a name="product-and-service-usage"></a>Ürün ve hizmet kullanımı

#### <a name="diagnostic-log-upload-started-report"></a>Tanılama günlüğü karşıya yükleme başlatıldı raporu

Aşağıdaki alanlar toplanır:

|Alan|Açıklama|
|---|---|
|sha256|Destek günlüğünün SHA256 tanımlayıcısı.|
|boyut|Destek günlüğünün boyutu.|
|original_path|Destek günlüğünün yolu (her zaman */Library/Application Support/Microsoft/Defender/wdavdiag/ altında).*|
|biçim|Destek günlüğünün biçimi.|
|meta veri|Destek günlüğünün içeriği hakkında bilgi.|

#### <a name="diagnostic-log-upload-completed-report"></a>Tanılama günlüğü karşıya yükleme tamamlandı raporu

Aşağıdaki alanlar toplanır:

|Alan|Açıklama|
|---|---|
|request_id|Destek günlüğü karşıya yükleme isteği için bağıntı kimliği.|
|sha256|Destek günlüğünün SHA256 tanımlayıcısı.|
|blob_sas_uri|Destek günlüğünü karşıya yüklemek için uygulama tarafından kullanılan URI.|

#### <a name="product-and-service-performance-data-events-for-product-and-service-usage"></a>Ürün ve hizmet kullanımına bağlı ürün ve hizmet performansı verileri olayları

**Beklenmeyen uygulama çıkışı (kilitlenme)**:

Uygulamadan beklenmeyen çıkışlar ve bu olduğunda uygulamanın durumu.

**Çekirdek uzantısı istatistikleri**:

Aşağıdaki alanlar toplanır:

|Alan|Açıklama|
|---|---|
|pkt_ack_timeout|Aşağıdaki özellikler, çekirdek uzantısının başlatılmasından bu yana oluşan olayların sayısını temsil eden toplam sayısal değerlerdir.|
|pkt_ack_conn_timeout||
|ipc.ack_pkts||
|ipc.nack_pkts||
|ipc.send.ack_no_conn||
|ipc.send.nack_no_conn||
|ipc.send.ack_no_qsq||
|ipc.send.nack_no_qsq||
|ipc.ack.no_space||
|ipc.ack.timeout||
|ipc.ack.ackd_fast||
|ipc.ack.ackd||
|ipc.recv.bad_pkt_len||
|ipc.recv.bad_reply_len||
|ipc.recv.no_waiter||
|ipc.recv.copy_failed||
|ipc.kauth.vnode.mask||
|ipc.kauth.vnode.read||
|ipc.kauth.vnode.write||
|ipc.kauth.vnode.exec||
|ipc.kauth.vnode.del||
|ipc.kauth.vnode.read_attr||
|ipc.kauth.vnode.write_attr||
|ipc.kauth.vnode.read_ex_attr||
|ipc.kauth.vnode.write_ex_attr||
|ipc.kauth.vnode.read_sec||
|ipc.kauth.vnode.write_sec||
|ipc.kauth.vnode.take_own||
|ipc.kauth.vnode.link||
|ipc.kauth.vnode.create||
|ipc.kauth.vnode.move||
|ipc.kauth.vnode.mount||
|ipc.kauth.vnode.denied||
|ipc.kauth.vnode.ackd_before_deadline||
|ipc.kauth.vnode.missed_deadline||
|ipc.kauth.file_op.mask||
|ipc.kauth_file_op.open||
|ipc.kauth.file_op.close||
|ipc.kauth.file_op.close_modified||
|ipc.kauth.file_op.move||
|ipc.kauth.file_op.link||
|ipc.kauth.file_op.exec||
|ipc.kauth.file_op.remove||
|ipc.kauth.file_op.unmount||
|ipc.kauth.file_op.fork||
|ipc.kauth.file_op.create||

## <a name="resources"></a>Kaynaklar

- [Microsoft'ta Gizlilik](https://privacy.microsoft.com/)
