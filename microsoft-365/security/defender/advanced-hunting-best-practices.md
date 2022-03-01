---
title: Microsoft 365 Defender'da gelişmiş arama sorgusu en Microsoft 365 Defender
description: Gelişmiş avıyla hızlı, verimli ve hatasız tehdit arama sorgularını nasıl kuraya devam etmeyi öğrenin
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, şema, kusto, zaman aşımından kaçınma, komut satırları, süreç kimliği, en iyi duruma getirme, en iyi yöntem, ayrıştırma, birleştirme, özetleme
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
ms.openlocfilehash: d797fb8843bdf5d29e9af43cac152461eb379e5f
ms.sourcegitcommit: 4af23696ff8b44872330202fe5dbfd2a69d9ddbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/30/2021
ms.locfileid: "62997088"
---
# <a name="advanced-hunting-query-best-practices"></a>Gelişmiş arama sorgusu en iyi yöntemleri

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Sonuçları daha hızlı elde etmek ve karmaşık sorguları çalışırken zaman aşımından kaçınmak için bu önerileri uygulayabilirsiniz. Sorgu performansını geliştirme konusunda daha fazla yol gösterici bilgi için [, Kusto sorgusu en iyi yöntemleri makalelerini okuyun](/azure/kusto/query/best-practices).

## <a name="understand-cpu-resource-quotas"></a>CPU kaynak kotalarını anlama
Boyutuna bağlı olarak, her kiracı gelişmiş arama sorguları yapmak için ayrılmış belirli bir CPU kaynağı miktarına erişimi vardır. Çeşitli kullanım parametreleri hakkında ayrıntılı bilgi için gelişmiş av [kotaları ve kullanım parametreleri hakkında bilgi edinebilirsiniz](advanced-hunting-limits.md).

Sorguyu çalıştırdikten sonra, yürütme süresini ve kaynak kullanımını (Düşük, Orta, Yüksek) görebilirler. Yüksek, sorgunun çalıştıracak daha fazla kaynak aldıklarını ve sonuçları daha verimli bir şekilde geri almak için geliştirilene olduğunu belirtir.

:::image type="content" source="../../media/resource-usage.png" alt-text="Portalda **Sonuçlar** sekmesinin altındaki Microsoft 365 Defender." lightbox="../../media/resource-usage.png":::

Düzenli olarak birden çok sorgu çalıştıran müşterilerin, kullanım kullanımını izlemesi ve kotaların veya kullanım parametrelerinin aşilmesiyle sonuçlanabilecek aksaklıkları en aza indirmek için bu makaledeki iyileştirme kılavuzlarını uygulaması gerekir.

## <a name="general-optimization-tips"></a>Genel iyileştirme ipuçları

- **Yeni sorguları boyut—** Bir sorgunun büyük bir sonuç kümesi geri döneceğine şüpheleniyorsanız, önce sayı işlecini kullanarak [bunu değerlendirin](/azure/data-explorer/kusto/query/countoperator). Büyük [sonuç](/azure/data-explorer/kusto/query/limitoperator) kümelerini önlemek için `take` sınırı veya eş anlamlıyı kullanın.
- Filtreleri **erken** uygulama—Veri kümesini azaltmak için, özellikle [de substring()](/azure/data-explorer/kusto/query/substringfunction), [replace()](/azure/data-explorer/kusto/query/replacefunction), [trim()](/azure/data-explorer/kusto/query/trimfunction), [toupper()](/azure/data-explorer/kusto/query/toupperfunction) veya [parse_json()](/azure/data-explorer/kusto/query/parsejsonfunction) gibi işlevleri kullanmadan önce, zaman filtrelerini ve diğer filtreleri uygulama. Aşağıdaki örnekte, filtreleme işleçlerinin kayıt sayısını azalttırma sonrası ayrıştırma işlevi [extractjson()](/azure/data-explorer/kusto/query/extractjsonfunction) kullanılır.

    ```kusto
    DeviceEvents
    | where Timestamp > ago(1d)
    | where ActionType == "UsbDriveMount"
    | where DeviceName == "user-desktop.domain.com"
    | extend DriveLetter = extractjson("$.DriveLetter", AdditionalFields)
     ```

- **Has contains contains**—To avoid searching substrings within words unnecessarily, use the `has` operator of .`contains` [Dize işleçleri hakkında bilgi](/azure/data-explorer/kusto/query/datatypes-string-operators)
- **Belirli sütunlara bakın**: Tüm sütunlarda tam metin aramaları çalıştır yerine belirli bir sütuna bakın. Tüm sütunları kontrol `*` etmek için kullanmayın.
- **Hız için büyük/düşük harfe** duyarlı: Büyük/düşük harfe duyarlı aramalar daha özeldir ve genel olarak daha iyi performansa sahip olur. ve gibi büyük/ [harfe duyarlı](/azure/data-explorer/kusto/query/datatypes-string-operators) dize işleçlerinin `has_cs` adları `contains_cs`genellikle ile biter `_cs`. Ayrıca, . yerine büyük/harfe duyarlı eşittir işlecini `==` de kullanabilirsiniz `=~`.
- **Ayrıştırma, ayıklamayın—** Mümkün olduğunda, [ayrıştırma](/azure/data-explorer/kusto/query/parseoperator) işlecini veya parse_json() gibi bir [ayrıştırma işlevini kullanın](/azure/data-explorer/kusto/query/parsejsonfunction). Her ikisi `matches regex` de normal ifade [kullanan dize işleci](/azure/data-explorer/kusto/query/extractfunction) veya extract() işlevini kullanmaktan kaçının. Normal ifade kullanımını daha karmaşık senaryolar için rezerve. [İşlevleri ayrıştırma hakkında daha fazla makale okuyun](#parse-strings)
- **Tablolara ifade filtre uygulama**— Bir tablo sütununa filtre uygulama, hesaplanmış sütuna filtre uygulama.
- **Üç karakterli terim yok**: Üç karakterli veya daha az karakter içeren terimleri kullanarak karşılaştırma veya filtreleme yapmaktan kaçının. Bu şartlar dizine alındı değildir ve bu şartlarla eşleştirmek için daha fazla kaynak gerekir.
- **Project seçime bağlı**:Yalnızca ihtiyacınız olan sütunları projesiyle sonuçlarınızı daha kolay anlaşılır hale getirirsiniz. Birleştirme veya benzer işlemleri çalıştırmadan önce belirli [sütunların](/azure/data-explorer/kusto/query/joinoperator) projecting de performansı artırmaya yardımcı olur.

## <a name="optimize-the-join-operator"></a>İşleci en iyi duruma `join` getirme
Birleştirme [işleci](/azure/data-explorer/kusto/query/joinoperator) , belirtilen sütunlardaki eşleşen değerlere göre iki tin satırları birleştirerek. Bu işleci kullanan sorguları en iyi duruma getirmek için bu ipuçlarını uygulayabilirsiniz.

- **Sola doğru daha küçük bir** tablo— `join` İşleç, birleştirme deyiminizin sol tarafındaki tablodaki kayıtlarla sağ tarafta yer alan kayıtlarla eşler. Sol tarafta daha küçük bir tablo olmasıyla, daha az kaydın eşleşmesi gerekir ve böylece sorgu hızlandırabilirsiniz.

    Aşağıdaki tabloda, sol tabloyu hesap `DeviceLogonEvents` SID'leriyle birleştirmeden önce yalnızca üç cihazı kapsayacak `IdentityLogonEvents` şekilde azalttırız.

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

- **İç birleşim** çeşnisini kullanın: Varsayılan [](/azure/data-explorer/kusto/query/joinoperator#join-flavors) birleşim çeşnisi veya [innerunique-join](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#innerunique-join-flavor), doğru tabloyla her eşleşme için bir satır dönmeden önce, sol tablodaki satırları birleştirme tuşuyla eşler. Sol tablo anahtar için aynı `join` değere sahip birden çok satırı varsa, bu satırlar her benzersiz değer için tek bir rastgele satır bırakılacak şekilde lisansları atılacaktır.

    Bu varsayılan davranış, sol tablodan yararlı bilgiler sağ sağlayacak önemli bilgiler bırakabilirsiniz. Örneğin, aşağıdaki sorgu birden çok e-posta iletisi kullanarak gönderilmiş olsa bile, yalnızca belirli bir eki içeren bir e-posta gösterir:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```

    Bu sınırlamaya çözüm olarak, sol [](/azure/data-explorer/kusto/query/joinoperator?pivots=azuredataexplorer#inner-join-flavor) `kind=inner` tablodaki eşleşen değerlerin sağ tarafta tüm satırlarını göstermeyi belirterek iç birleşim çeşitleni uygulanır:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join kind=inner (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```
- **Zaman penceresinden kayıtlara katılın**: Güvenlik olaylarını incelerken, analistler aynı zaman süresinde oluşan ilgili olayları araştırabilir. Aynı yaklaşımın uygulanması, `join` aynı zamanda kontrol etmek istediğiniz kayıt sayısını azaltarak performansın da avantajlarını sağlar.

    Aşağıdaki sorgu kötü amaçlı dosyayı aldıktan sonra 30 dakika içinde oturum açma olaylarını denetler:

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
- **Belirli bir zaman**`join` penceresini araştırmasanız bile, sol ve sağ tabloların her iki tarafına da zaman filtreleri uygulayarak performans denetimi ve iyileştirme için kayıt sayısını azaltabilirsiniz. Aşağıdaki sorgu, yalnızca `Timestamp > ago(1h)` son saatten itibaren kayıtları birleştirmesi için her iki tablo için de geçerlidir:

    ```kusto
    EmailAttachmentInfo
    | where Timestamp > ago(1h)
    | where Subject == "Document Attachment" and FileName == "Document.pdf"
    | join kind=inner (DeviceFileEvents | where Timestamp > ago(1h)) on SHA256
    ```

- **Performans için ipuçları kullanın**—İşleçle `join` birlikte, kaynak kullanımı yoğun olan işlemler çalıştırarak arka uçta yükü dağıtması için ipuçları kullanın. [Katılma ipuçları hakkında daha fazla bilgi](/azure/data-explorer/kusto/query/joinoperator#join-hints)

    Örneğin karışık çalmayı ipucu **[](/azure/data-explorer/kusto/query/shufflequery)**, `AccountObjectId` çok sayıda benzersiz değere sahip bir anahtar (aşağıdaki sorgu gibi) yüksek kardinaliteye sahip bir anahtar kullanarak tabloları birleştirmede sorgu performansını iyileştirmeye yardımcı olur:

    ```kusto
    IdentityInfo
    | where JobTitle == "CONSULTANT"
    | join hint.shufflekey = AccountObjectId
    (IdentityDirectoryEvents
        | where Application == "Active Directory"
        | where ActionType == "Private data retrieval")
    on AccountObjectId
    ```

    Yayın **[ipucu,](/azure/data-explorer/kusto/query/broadcastjoin)** sol tablonun küçük (en çok 100.000 kayıt) olduğu ve doğru tablonun aşırı büyük olduğu durumlarda yararlı olur. Örneğin, aşağıdaki sorgu, tabloda bağlantı içeren tüm iletilerin belirli konuları olan birkaç e-postayı  birleştirmeye `EmailUrlInfo` çalışıyor:

    ```kusto
    EmailEvents
    | where Subject in ("Warning: Update your credentials now", "Action required: Update your credentials now")
    | join hint.strategy = broadcast EmailUrlInfo on NetworkMessageId
    ```

## <a name="optimize-the-summarize-operator"></a>İşleci en iyi duruma `summarize` getirme
[Özetleme işleci](/azure/data-explorer/kusto/query/summarizeoperator), tablonun içeriğini bir araya toplar. Bu işleci kullanan sorguları en iyi duruma getirmek için bu ipuçlarını uygulayabilirsiniz.

- **Ayrı değerleri bulma**— Genelde, `summarize` tekrar tekrar eden farklı değerleri bulmak için kullanın. Yinelenen değerlere sahip olmayan sütunları toplamak için kullanmak gereksiz olabilir.

    Tek bir e-posta birden çok etkinlik kapsamında yer alasa da,  `summarize` aşağıdaki örnek verimli bir kullanım değildir çünkü tek bir e-posta için ağ ileti kimliği her zaman benzersiz bir gönderen adresiyle birlikte gelir.

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize by NetworkMessageId, SenderFromAddress
    ```
    İşleç `summarize` kolayca ' ile değiştirilebilir `project`ve daha az kaynak tüketmek için aynı sonuçları elde edebilirsiniz:

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | project NetworkMessageId, SenderFromAddress
    ```
    Aşağıdaki örnek, aynı alıcı adresine e-posta `summarize` gönderen bir gönderen adresinin birden çok farklı örneği olması nedeniyle kullanımını daha verimli bir şekilde yapmaktır. Bu tür bileşimler daha az belirgindir ve yinelemeleri olabilir.

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize by SenderFromAddress, RecipientEmailAddress
    ```

- **Sorguyu karıştırma**—Yinelenen `summarize` değerlere sahip sütunlarda en iyi şekilde kullanılır ama aynı sütunların da yüksek _kardinalitesi_ veya çok sayıda benzersiz değeri olabilir. Aynı işleç `join` gibi işleme [](/azure/data-explorer/kusto/query/shufflequery) `summarize` yükünü dağıtmak ve yüksek kardinaliteye sahip sütunlarda işletim performansını artırmak için karıştırma ipucunu da uygulayabilirsiniz.

    Aşağıdaki sorgu, büyük `summarize` kuruluşlarda yüzlerce binlercesinde çalıştırlan ayrı alıcı e-posta adreslerini saymak için kullanır. Performansı geliştirmek için şunları da dahil ediyor `hint.shufflekey`:

    ```kusto
    EmailEvents
    | where Timestamp > ago(1h)
    | summarize hint.shufflekey = RecipientEmailAddress count() by Subject, RecipientEmailAddress
    ```

## <a name="query-scenarios"></a>Sorgu senaryoları

### <a name="identify-unique-processes-with-process-ids"></a>Süreç kimlikleriyle benzersiz işlemleri tanımlama

süreç kimlikleri (PID) yeniden kullanılabilir ve Windows işlemler için yeniden kullanılır. Kendi başına, belirli süreçler için benzersiz tanımlayıcılar olarak hizmet edecekleri bir işlem değil.

Belirli bir makinede bir işleme yönelik benzersiz tanımlayıcı almak için, süreç kimliğiyle birlikte işlem oluşturma süresi kullanın. İşlemleri temel alan verileri birlerken veya özetlerken, makine tanımlayıcısı (`DeviceId`ya da ), süreç kimliği ( `InitiatingProcessId``ProcessId` veya ) için sütunlar ve işlem oluşturma süresi (`ProcessCreationTime` veya `InitiatingProcessCreationTime`)`DeviceName`

Aşağıdaki örnek sorgu, büyük olasılıkla dosya paylaşımlarını tarar ve bağlantı noktası 445 (SMB) üzerinden 10'dan fazla IP adresine erişen işlemleri bulur.

Örnek sorgu:

```kusto
DeviceNetworkEvents
| where RemotePort == 445 and Timestamp > ago(12h) and InitiatingProcessId !in (0, 4)
| summarize RemoteIPCount=dcount(RemoteIP) by DeviceName, InitiatingProcessId, InitiatingProcessCreationTime, InitiatingProcessFileName
| where RemoteIPCount > 10
```

Sorgu hem iki hem de son `InitiatingProcessId` `InitiatingProcessCreationTime` olarak özetler; böylece, aynı işlem kimliğiyle birden çok işlemi karma kullanmadan tek bir işleme bakabilirsiniz.

### <a name="query-command-lines"></a>Sorgu komut satırları
Bir görevi gerçekleştirmek için bir komut satırı oluşturmanın çeşitli yolları vardır. Örneğin, bir saldırgan dosya uzantısı olmadan, ortam değişkenlerini kullanarak veya tırnak içine almadan bir resim dosyasına referans olabilir. Ayrıca saldırgan parametrelerin sıralamalarını değiştirebilir veya birden çok tırnak ve boşluk ekleyebilir.

Komut satırları çevresinde daha dayanıklı sorgular oluşturmak için aşağıdaki uygulamaları kullanın:

- Komut satırına filtrenet.exe *psexec.exe* *, bilinen* işlemleri (örneğin,net.exeveyapsexec.exe) bulun.
- [parse_command_line() işlevini kullanarak komut satırı bölümlerini ayrıştırma](/azure/data-explorer/kusto/query/parse-command-line)
- Komut satırı bağımsız değişkenlerini sorgularken, belirli bir sırada birden çok ilgili olmayan bağımsız değişkende tam eşleşme aramaz. Bunun yerine, normal ifadeleri kullanın veya birden çok ayrı içeren işleç kullanın.
- Büyük/harfe duyarlısız eşleşmeleri kullanın. Örneğin, , `=~`ve `in~`yerine `contains` `==`, ve `in`kullanın `contains_cs`.
- Komut satırı obfuscation tekniklerini azaltmak için, tırnakları kaldırmayı, virgülleri boşluklarla değiştirmeyi ve birbirini takip eden birden çok boşluğu tek boşlukla değiştirmeyi göz önünde bulundurabilirsiniz. Başka yaklaşımlar gerektiren daha karmaşık obfuscation teknikleri vardır, ancak bu ince düzeltmeler yaygın yaklaşımları düzeltmeye yardımcı olabilir.

Aşağıdaki örneklerde, "MpsSvc" güvenlik duvarı hizmetini durdurmak *üzerenet.exe* dosyasınınet.exesorgu oluşturmak için çeşitli yollar göstermektedir:

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

### <a name="ingest-data-from-external-sources"></a>Dış kaynaklardan veri toplama
Uzun listeleri veya büyük tabloları sorgunuza birleştirmek için, [dış veri](/azure/data-explorer/kusto/query/externaldata-operator) işlecini kullanarak belirtilen URI'den veri alın. TXT, CSV, JSON veya diğer biçimlerde yer alan dosyalardan [veri alabilirsiniz](/azure/data-explorer/ingestion-supported-formats). Aşağıdaki örnekte, e-posta eklerini kontrol etmek için MalwareBazaar (abuse.ch) tarafından sağlanan kapsamlı kötü amaçlı yazılım SHA-256 karmaları listesinden nasıl yararlanabilirsiniz:

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
Ayrıştırma veya dönüştürme gereken dizeleri verimli bir şekilde işlemek için kullanabileceğiniz çeşitli işlevler vardır.

| Dize | İşlev | Kullanım örneği |
|--|--|--|
| Komut satırları | [parse_command_line()](/azure/data-explorer/kusto/query/parse-command-line) | Komutu ve tüm bağımsız değişkenleri ayıklama. |
| Yollar | [parse_path()](/azure/data-explorer/kusto/query/parsepathfunction) | Dosya veya klasör yolunun bölümlerini ayıkla. |
| Sürüm numaraları | [parse_version()](/azure/data-explorer/kusto/query/parse-versionfunction) | Sürüm numarasının en çok dört bölüme ve bölüm başına en çok sekiz karaktere kadar olan bölümlerinden farklı olarak yapılandırabilirsiniz. Sürüm yaşını karşılaştırmak için ayrıştırıcı verileri kullanın. |
| IPv4 adresleri | [parse_ipv4()](/azure/data-explorer/kusto/query/parse-ipv4function) | IPv4 adresini uzun bir tamsayıya dönüştürme. IPv4 adreslerini dönüştürmeden karşılaştırmak için, ipv4_compare [() kullanın](/azure/data-explorer/kusto/query/ipv4-comparefunction). |
| IPv6 adresleri | [parse_ipv6()](/azure/data-explorer/kusto/query/parse-ipv6function)  | IPv4 veya IPv6 adresini kurallı IPv6 notasyonuna dönüştürme. IPv6 adreslerini karşılaştırmak için, ipv6_compare [() kullanın](/azure/data-explorer/kusto/query/ipv6-comparefunction). |

Desteklenen tüm ayrıştırma işlevleri hakkında bilgi edinmek için, [Kusto dize işlevleri hakkında bilgi okuyun](/azure/data-explorer/kusto/query/scalarfunctions#string-functions).

>[!NOTE]
>Bu makaledeki bazı tablolar Uç Nokta için Microsoft Defender'da kullanılamıyor olabilir. [Daha fazla Microsoft 365 Defender](m365d-enable.md) kullanarak tehdit yakalamak için çok daha fazla kaynağı açabilirsiniz. Gelişmiş av iş akışlarınızı Uç Nokta için Microsoft Defender'dan Microsoft 365 Defender için [Microsoft Defender'dan gelişmiş arama sorgularını geçirme makalesinde](advanced-hunting-migrate-from-mde.md) yer alan adımları takip edebilirsiniz.

## <a name="related-topics"></a>İlgili konular
- [Kusto sorgu dili belgeleri](/azure/data-explorer/kusto/query/)
- [Kotalar ve kullanım parametreleri](advanced-hunting-limits.md)
- [Gelişmiş av hatalarını işleme](advanced-hunting-errors.md)
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)