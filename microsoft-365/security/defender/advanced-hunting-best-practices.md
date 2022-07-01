---
title: Microsoft 365 Defender'de gelişmiş tehdit avcılığı sorgusu en iyi yöntemleri
description: Gelişmiş avcılık ile hızlı, verimli ve hatasız tehdit avcılığı sorguları oluşturma hakkında bilgi edinin
keywords: gelişmiş tehdit avcılığı, tehdit avcılığı, siber tehdit avcılığı, Microsoft 365 Defender, microsoft 365, m365, arama, sorgu, telemetri, şema, kusto, zaman aşımından kaçınma, komut satırları, işlem kimliği, iyileştirme, en iyi yöntem, ayrıştırma, katılma, özetleme
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: c4236edcb2b5ec15b7c66be8f4b74ad0a2bc44c7
ms.sourcegitcommit: e9692a40dfe1f8c2047699ae3301c114a01b0d3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66603483"
---
# <a name="advanced-hunting-query-best-practices"></a>Gelişmiş tehdit avcılığı sorgusu en iyi yöntemleri

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- Microsoft 365 Defender

Karmaşık sorgular çalıştırırken sonuçları daha hızlı almak ve zaman aşımlarından kaçınmak için bu önerileri uygulayın. Sorgu performansını iyileştirme hakkında daha fazla kılavuz için [Kusto sorgu en iyi yöntemleri](/azure/kusto/query/best-practices) makalesini okuyun.

## <a name="understand-cpu-resource-quotas"></a>CPU kaynak kotalarını anlama
Boyutuna bağlı olarak, her kiracının gelişmiş tehdit avcılığı sorguları çalıştırmak için ayrılmış belirli miktarda CPU kaynağına erişimi vardır. Çeşitli kullanım parametreleri hakkında ayrıntılı bilgi için [gelişmiş tehdit avcılığı kotaları ve kullanım parametreleri hakkında bilgi edinin](advanced-hunting-limits.md).

Sorgunuzu çalıştırdıktan sonra yürütme süresini ve kaynak kullanımını (Düşük, Orta, Yüksek) görebilirsiniz. Yüksek, sorgunun çalıştırılması için daha fazla kaynak aldığını ve sonuçları daha verimli döndürmek için iyileştirilebileceğini gösterir.

:::image type="content" source="../../media/resource-usage.png" alt-text="Microsoft 365 Defender portalındaki **Sonuçlar** sekmesinin altındaki sorgu ayrıntıları" lightbox="../../media/resource-usage.png":::

Düzenli olarak birden çok sorgu çalıştıran müşterilerin tüketimi izlemesi ve kotaların veya kullanım parametrelerinin aşılmasından kaynaklanan kesintiyi en aza indirmek için bu makaledeki iyileştirme kılavuzunu uygulaması gerekir.

[Sorgularınızı iyileştirmenin](https://www.youtube.com/watch?v=ceYvRuPp5D8) en yaygın yollarından bazılarını görmek için KQL sorgularını iyileştirme bölümünü izleyin.  

## <a name="general-optimization-tips"></a>Genel iyileştirme ipuçları

- **Yeni sorguları boyutlandırma**—Bir sorgunun büyük bir sonuç kümesi döndüreceğinden şüpheleniyorsanız, önce [count işlecini](/azure/data-explorer/kusto/query/countoperator) kullanarak sorguyu değerlendirin. Büyük sonuç kümelerini önlemek için [limit](/azure/data-explorer/kusto/query/limitoperator) veya eş anlamlısını `take` kullanın.
- **Filtreleri erken uygulama**—Özellikle [alt dize()](/azure/data-explorer/kusto/query/substringfunction), [replace](/azure/data-explorer/kusto/query/replacefunction)(), [trim()](/azure/data-explorer/kusto/query/trimfunction), [toupper](/azure/data-explorer/kusto/query/toupperfunction)()veya [parse_json](/azure/data-explorer/kusto/query/parsejsonfunction)() gibi dönüştürme ve ayrıştırma işlevlerini kullanmadan önce veri kümesini azaltmak için zaman filtrelerini ve diğer filtreleri uygulayın. Aşağıdaki örnekte, filtreleme işleçleri kayıt sayısını azalttığı için [extractjson()](/azure/data-explorer/kusto/query/extractjsonfunction) ayrıştırma işlevi kullanılmıştır.

    ```kusto
    DeviceEvents
    | where Timestamp > ago(1d)
    | where ActionType == "UsbDriveMount"
    | where DeviceName == "user-desktop.domain.com"
    | extend DriveLetter = extractjson("$.DriveLetter", AdditionalFields)
     ```

- **Has beats contains**—Sözcüklerin içindeki alt dizelerin gereksiz yere aranmasını önlemek için yerine işlecini `has` `contains`kullanın. [Dize işleçleri hakkında bilgi edinin](/azure/data-explorer/kusto/query/datatypes-string-operators)
- **Belirli sütunlara bakın— Tüm sütunlarda** tam metin aramaları çalıştırmak yerine belirli bir sütuna bakın. Tüm sütunları denetlemek için kullanmayın `*` .
- **Hız için büyük/küçük harfe duyarlı**— Büyük/küçük harfe duyarlı aramalar daha belirgindir ve genellikle daha yüksek performanslıdır. ve `contains_cs`gibi `has_cs` büyük/küçük harfe duyarlı [dize işleçlerinin](/azure/data-explorer/kusto/query/datatypes-string-operators) adları genellikle ile `_cs`biter. Yerine büyük/küçük harfe duyarlı eşittir işlecini `==` `=~`de kullanabilirsiniz.
- **Ayrıştırma, ayıklama—** Mümkün olduğunda [ayrıştırma işlecini](/azure/data-explorer/kusto/query/parseoperator) veya [parse_json()](/azure/data-explorer/kusto/query/parsejsonfunction) gibi bir ayrıştırma işlevini kullanın. `matches regex` Her ikisi de normal ifade kullanan dize işlecinden veya [extract() işlevinden](/azure/data-explorer/kusto/query/extractfunction) kaçının. Daha karmaşık senaryolar için normal ifade kullanımını ayırın. [İşlevleri ayrıştırma hakkında daha fazla bilgi edinin](#parse-strings)
- **Tabloları ifadelere değil filtrele**—Tablo sütununa göre filtre uygulanabiliyorsa hesaplanan sütuna filtre uygulamayın.
- **Üç karakterli terim yok**— Üç veya daha az karakterle terimleri karşılaştırmaktan veya filtrelemekten kaçının. Bu terimler dizine alınmaz ve bunlar eşleştirildiğinde daha fazla kaynak gerekir.
- **Seçmeli olarak proje** oluşturma—Yalnızca ihtiyacınız olan sütunları yansıtarak sonuçlarınızın daha kolay anlaşılmasını sağlayın. [Birleştirme](/azure/data-explorer/kusto/query/joinoperator) veya benzer işlemleri çalıştırmadan önce belirli sütunları yansıtmak da performansı artırmaya yardımcı olur.



## <a name="optimize-the-join-operator"></a>İşleci iyileştirme `join`
[Birleştirme işleci](/azure/data-explorer/kusto/query/joinoperator), belirtilen sütunlardaki değerleri eşleştirerek iki tablodaki satırları birleştirir. Bu işleci kullanan sorguları iyileştirmek için bu ipuçlarını uygulayın.

- **Sol tarafınızda daha küçük bir tablo**— `join` İşleç, birleştirme deyiminizin sol tarafındaki tablodaki kayıtları sağdaki kayıtlara eşler. Sol tarafta daha küçük bir tablonun olması nedeniyle daha az kaydın eşleşmesi gerekir ve böylece sorgu hızlandırılır.

    Aşağıdaki tabloda, hesap SID'leri ile `IdentityLogonEvents` birleştirmeden önce sol tabloyu `DeviceLogonEvents` yalnızca üç belirli cihazı kapsayacak şekilde azaltıyoruz.

    ```kusto
    DeviceLogonEvents
    | where DeviceName in ("device-1.domain.com", "device-2.domain.com", "device-3.domain.com")
    | where ActionType == "LogonFailed"
    | join
        (IdentityLogonEvents
        | where ActionType == "LogonFailed"
        | where Protocol == "Kerberos")
    on AccountSid
    ```

- **İç birleşim aromasını kullanın**— Varsayılan [birleşim aroması](/azure/data-explorer/kusto/query/joinoperator#join-flavors) veya [innerunique-join](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#innerunique-join-flavor) , her eşleşme için bir satırı sağ tabloya döndürmeden önce sol tablodaki satırları birleştirme tuşuyla yinelenenleri kaldırıyor. Sol tabloda anahtar için `join` aynı değere sahip birden çok satır varsa, bu satırlar her benzersiz değer için tek bir rastgele satır bırakmak üzere yinelenenleri kaldırılacaktır.

    Bu varsayılan davranış, sol tablodan yararlı içgörüler sağlayabilecek önemli bilgiler bırakabilir. Örneğin, aynı ek birden çok e-posta iletisi kullanılarak gönderilmiş olsa bile aşağıdaki sorguda belirli bir eki içeren yalnızca bir e-posta gösterilir:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```

    Bu sınırlamayı gidermek için, sol tablodaki tüm satırların sağda eşleşen değerlerle gösterilmesini belirterek `kind=inner` [iç birleşim](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#inner-join-flavor) aromasını uygularız:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join kind=inner (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```
- Bir **zaman penceresinden kayıtları birleştirme**—Analistler güvenlik olaylarını araştırırken, aynı zaman aralığında gerçekleşen ilgili olayları arar. Kullanırken `join` aynı yaklaşımın uygulanması, denetlenecek kayıt sayısını azaltarak performansa da avantaj sağlar.

    Aşağıdaki sorgu, kötü amaçlı bir dosya aldıktan sonra 30 dakika içinde oturum açma olaylarını denetler:

    ```kusto
    EmailEvents
    | where Timestamp > ago(7d)
    | where ThreatTypes has "Malware"
    | project EmailReceivedTime = Timestamp, Subject, SenderFromAddress, AccountName = tostring(split(RecipientEmailAddress, "@")[0])
    | join (
    DeviceLogonEvents
    | where Timestamp > ago(7d)
    | project LogonTime = Timestamp, AccountName, DeviceName
    ) on AccountName
    | where (LogonTime - EmailReceivedTime) between (0min .. 30min)
    ```
- **Zaman filtrelerini her iki tarafa da uygulayın**: Belirli bir zaman penceresini araştırmasanız bile, hem sol hem de sağ tablolara zaman filtreleri uygulamak, performansı denetlemek ve iyileştirmek `join` için kayıt sayısını azaltabilir. Aşağıdaki sorgu her iki tablo için de geçerlidir `Timestamp > ago(1h)` , böylece yalnızca son bir saat içindeki kayıtları birleştirir:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join kind=inner (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```

- **Performans için ipuçları kullanın**— Arka uca yoğun kaynak kullanan işlemleri çalıştırırken yükü dağıtmasını bildirmek için işleçle ipuçlarını `join` kullanın. [Birleştirme ipuçları hakkında daha fazla bilgi edinin](/azure/data-explorer/kusto/query/joinoperator#join-hints)

    Örneğin karıştırma **[ipucu](/azure/data-explorer/kusto/query/shufflequery)** , aşağıdaki sorguda olduğu gibi, çok sayıda benzersiz değere sahip bir anahtar olan yüksek kardinaliteye sahip bir anahtar kullanarak tabloları birleştirirken sorgu performansını artırmaya `AccountObjectId` yardımcı olur:

    ```kusto
    IdentityInfo
    | where JobTitle == "CONSULTANT"
    | join hint.shufflekey = AccountObjectId
    (IdentityDirectoryEvents
        | where Application == "Active Directory"
        | where ActionType == "Private data retrieval")
    on AccountObjectId
    ```

    **[Yayın ipucu](/azure/data-explorer/kusto/query/broadcastjoin)**, sol tablonun küçük olması (en fazla 100.000 kayıt) ve sağ tablonun son derece büyük olması için yardımcı olur. Örneğin, aşağıdaki sorgu, tablodaki bağlantıları içeren _tüm_ iletilere belirli konuları olan birkaç e-postayı birleştirmeye `EmailUrlInfo` çalışıyor:

    ```kusto
    EmailEvents
    | where Subject in ("Warning: Update your credentials now", "Action required: Update your credentials now")
    | join hint.strategy = broadcast EmailUrlInfo on NetworkMessageId
    ```

## <a name="optimize-the-summarize-operator"></a>İşleci iyileştirme `summarize`
[Summarize işleci](/azure/data-explorer/kusto/query/summarizeoperator) bir tablonun içeriğini toplar. Bu işleci kullanan sorguları iyileştirmek için bu ipuçlarını uygulayın.

- **Ayrı değerleri bulma**—Genel olarak, tekrarlanabilir ayrı değerleri bulmak için kullanın `summarize` . Yinelenen değerleri olmayan sütunları toplamak için kullanmak gereksiz olabilir.

    Tek bir e-posta birden çok olayın parçası olabilir ancak tek bir e-postanın ağ iletisi kimliği her zaman benzersiz bir gönderen adresiyle birlikte geldiğinden `summarize` aşağıdaki örnek verimli bir kullanım _değildir_.

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize by NetworkMessageId, SenderFromAddress
    ```
    işleci `summarize` kolayca ile `project`değiştirilebilir ve bu da daha az kaynak tüketirken aynı sonuçları verebilir:

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | project NetworkMessageId, SenderFromAddress
    ```
    Aşağıdaki örnek, aynı alıcı adresine e-posta gönderen bir gönderen adresinin birden çok farklı örneği olabileceğinden daha verimli bir kullanımıdır `summarize` . Bu tür birleşimler daha az farklıdır ve yinelemeleri olabilir.

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize by SenderFromAddress, RecipientEmailAddress
    ```

- **Sorguyu karıştırma**— Yinelenen değerlere sahip sütunlarda en iyi şekilde kullanılırken `summarize` , aynı sütunlar _da yüksek kardinaliteye_ veya çok sayıda benzersiz değere sahip olabilir. `join` işleci gibi, işleme yükünü dağıtmak ve yüksek kardinaliteye sahip sütunlarda çalışırken performansı artırmak için karıştırma [ipucunu](/azure/data-explorer/kusto/query/shufflequery) ile `summarize` de uygulayabilirsiniz.

    Aşağıdaki sorgu, büyük kuruluşlarda yüz binlerde çalıştırabilen ayrı alıcı e-posta adresini saymak için kullanır `summarize` . Performansı geliştirmek için şunları içerir `hint.shufflekey`:

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize hint.shufflekey = RecipientEmailAddress count() by Subject, RecipientEmailAddress
    ```



## <a name="query-scenarios"></a>Sorgu senaryoları

### <a name="identify-unique-processes-with-process-ids"></a>İşlem kimlikleriyle benzersiz işlemleri tanımlama

İşlem kimlikleri (PID) Windows'ta geri dönüştürülür ve yeni işlemler için yeniden kullanılır. Kendi başlarına, belirli işlemler için benzersiz tanımlayıcılar olarak görev yapamazlar.

Belirli bir makinedeki bir işlemin benzersiz tanımlayıcısını almak için işlem oluşturma zamanıyla birlikte işlem kimliğini kullanın. İşlemler etrafında verileri birleştirdiğinizde veya özetlerken, makine tanımlayıcısı (veya veya `DeviceId` `DeviceName`), işlem kimliği ( veya ) ve işlem oluşturma zamanı (`ProcessId``ProcessCreationTime` veya `InitiatingProcessId``InitiatingProcessCreationTime`) için sütunlar ekleyin

Aşağıdaki örnek sorgu, 445 numaralı bağlantı noktası (SMB) üzerinden 10'dan fazla IP adresine erişen işlemleri bulur ve muhtemelen dosya paylaşımlarını tarar.

Örnek sorgu:

```kusto
DeviceNetworkEvents
| where RemotePort == 445 and Timestamp > ago(12h) and InitiatingProcessId !in (0, 4)
| summarize RemoteIPCount=dcount(RemoteIP) by DeviceName, InitiatingProcessId, InitiatingProcessCreationTime, InitiatingProcessFileName
| where RemoteIPCount > 10
```

Sorgu, birden çok işlemi aynı işlem kimliğiyle karıştırmadan tek bir işleme bakması için hem hem de her ikisine `InitiatingProcessId` `InitiatingProcessCreationTime` göre özetler.

### <a name="query-command-lines"></a>Sorgu komut satırları
Bir görevi gerçekleştirmek için komut satırı oluşturmanın birçok yolu vardır. Örneğin, bir saldırgan yol olmadan, dosya uzantısı olmadan, ortam değişkenlerini kullanarak veya tırnak işaretleri kullanarak bir görüntü dosyasına başvurabilir. Saldırgan ayrıca parametrelerin sırasını değiştirebilir veya birden çok tırnak işareti ve boşluk ekleyebilir.

Komut satırları çevresinde daha dayanıklı sorgular oluşturmak için aşağıdaki uygulamaları uygulayın:

- Komut satırının kendisini filtrelemek yerine dosya ** adı alanlarıyla eşleşerek bilinen işlemleri ( *net.exeveyapsexec.exe* gibi) tanımlayın.
- [parse_command_line() işlevini](/azure/data-explorer/kusto/query/parse-command-line) kullanarak komut satırı bölümlerini ayrıştırma
- Komut satırı bağımsız değişkenlerini sorgularken, belirli bir sırada birden çok ilişkisiz bağımsız değişkende tam eşleşme arayın. Bunun yerine normal ifadeler kullanın veya birden çok ayrı içeren işleç kullanın.
- Büyük/küçük harfe duyarsız eşleşmeler kullanın. Örneğin, , `in~`ve `contains` yerine `==`, `in`ve `contains_cs`kullanın`=~`.
- Komut satırı gizleme tekniklerini azaltmak için tırnak işaretleri kaldırmayı, virgülleri boşluklarla değiştirmeyi ve ardışık birden çok boşluğu tek bir boşlukla değiştirmeyi göz önünde bulundurun. Başka yaklaşımlar gerektiren daha karmaşık karartma teknikleri vardır, ancak bu ince ayarlar yaygın olanları gidermeye yardımcı olabilir.

Aşağıdaki örneklerde, "MpsSvc" güvenlik duvarı hizmetini durdurmak için dosya *net.exe* arayabilen bir sorgu oluşturmanın çeşitli yolları gösterilir:

```kusto
// Non-durable query - do not use
DeviceProcessEvents
| where ProcessCommandLine == "net stop MpsSvc"
| limit 10

// Better query - filters on file name, does case-insensitive matches
DeviceProcessEvents
| where Timestamp > ago(7d) and FileName in~ ("net.exe", "net1.exe") and ProcessCommandLine contains "stop" and ProcessCommandLine contains "MpsSvc"

// Best query also ignores quotes
DeviceProcessEvents
| where Timestamp > ago(7d) and FileName in~ ("net.exe", "net1.exe")
| extend CanonicalCommandLine=replace("\"", "", ProcessCommandLine)
| where CanonicalCommandLine contains "stop" and CanonicalCommandLine contains "MpsSvc"
```

### <a name="ingest-data-from-external-sources"></a>Dış kaynaklardan veri alma
Uzun listeleri veya büyük tabloları sorgunuza eklemek için [externaldata işlecini](/azure/data-explorer/kusto/query/externaldata-operator) kullanarak belirtilen URI'den veri alın. TXT, CSV, JSON veya [diğer biçimlerdeki](/azure/data-explorer/ingestion-supported-formats) dosyalardan veri alabilirsiniz. Aşağıdaki örnekte, e-postalardaki ekleri denetlemek için MalwareBazaar (abuse.ch) tarafından sağlanan kapsamlı kötü amaçlı yazılım SHA-256 karmalarını nasıl kullanabileceğiniz gösterilmektedir:

```kusto
let abuse_sha256 = (externaldata(sha256_hash: string)
[@"https://bazaar.abuse.ch/export/txt/sha256/recent/"]
with (format="txt"))
| where sha256_hash !startswith "#"
| project sha256_hash;
abuse_sha256
| join (EmailAttachmentInfo
| where Timestamp > ago(1d)
) on $left.sha256_hash == $right.SHA256
| project Timestamp,SenderFromAddress,RecipientEmailAddress,FileName,FileType,
SHA256,ThreatTypes,DetectionMethods
```

### <a name="parse-strings"></a>Dizeleri ayrıştırma
Ayrıştırma veya dönüştürme gerektiren dizeleri verimli bir şekilde işlemek için kullanabileceğiniz çeşitli işlevler vardır.

| Dize | İşlev | Kullanım örneği |
|--|--|--|
| Komut satırları | [parse_command_line()](/azure/data-explorer/kusto/query/parse-command-line) | Komutu ve tüm bağımsız değişkenleri ayıklayın. |
| Yol | [parse_path()](/azure/data-explorer/kusto/query/parsepathfunction) | Dosya veya klasör yolunun bölümlerini ayıklayın. |
| Sürüm numaraları | [parse_version()](/azure/data-explorer/kusto/query/parse-versionfunction) | En fazla dört bölüm ve bölüm başına en fazla sekiz karakter içeren bir sürüm numarasının yapısı kaldırılır. Sürüm yaşını karşılaştırmak için ayrıştırılmış verileri kullanın. |
| IPv4 adresleri | [parse_ipv4()](/azure/data-explorer/kusto/query/parse-ipv4function) | IPv4 adresini uzun bir tamsayıya dönüştürün. IPv4 adreslerini dönüştürmeden karşılaştırmak için [ipv4_compare()](/azure/data-explorer/kusto/query/ipv4-comparefunction) kullanın. |
| IPv6 adresleri | [parse_ipv6()](/azure/data-explorer/kusto/query/parse-ipv6function)  | IPv4 veya IPv6 adresini kurallı IPv6 gösterimine dönüştürün. IPv6 adreslerini karşılaştırmak için [ipv6_compare()](/azure/data-explorer/kusto/query/ipv6-comparefunction) kullanın. |

Desteklenen tüm ayrıştırma işlevleri hakkında bilgi edinmek için [Kusto dize işlevleri hakkında bilgi edinin](/azure/data-explorer/kusto/query/scalarfunctions#string-functions).

>[!NOTE]
>Bu makaledeki bazı tablolar Uç Nokta için Microsoft Defender'de kullanılamayabilir. Daha fazla veri kaynağı kullanarak tehditleri avlamak için [Microsoft 365 Defender açın](m365d-enable.md). Gelişmiş avcılık sorgularını Uç Nokta için Microsoft Defender'den geçirme bölümünde yer alan adımları izleyerek [gelişmiş avcılık iş akışlarınızı Uç Nokta için Microsoft Defender'den Microsoft 365 Defender](advanced-hunting-migrate-from-mde.md) taşıyabilirsiniz.

## <a name="related-topics"></a>İlgili konular
- [Kusto sorgu dili belgeleri](/azure/data-explorer/kusto/query/)
- [Kotalar ve kullanım parametreleri](advanced-hunting-limits.md)
- [Gelişmiş tehdit avcılığı hatalarını işleme](advanced-hunting-errors.md)
- [Gelişmiş avcılığa genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenin](advanced-hunting-query-language.md)