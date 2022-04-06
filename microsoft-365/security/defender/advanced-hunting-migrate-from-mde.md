---
title: gelişmiş tehdit avcılığı sorgularını Uç Nokta için Microsoft Defender geçirme
description: Uç Nokta için Microsoft Defender sorgularınızı Microsoft 365 Defender'de kullanabilmek için nasıl ayarlayacağınızı öğrenin
keywords: gelişmiş tehdit avcılığı, tehdit avcılığı, siber tehdit avcılığı, Microsoft 365 Defender, microsoft 365, m365, Uç Nokta için Microsoft Defender, arama, sorgu, telemetri, özel algılamalar, şema, Kusto, eşleme
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
ms.collection:
- M365-security-compliance
ms.topic: article
ms.custom: seo-marvel-apr2020
ms.technology: m365d
ms.openlocfilehash: 9fd00df5e61d37e5133f23e5f06973ceb99c4636
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64666184"
---
# <a name="migrate-advanced-hunting-queries-from-microsoft-defender-for-endpoint"></a>gelişmiş tehdit avcılığı sorgularını Uç Nokta için Microsoft Defender geçirme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- Microsoft 365 Defender

Daha geniş bir veri kümesi kullanarak tehditleri proaktif olarak avlamak için gelişmiş tehdit avcılığı iş akışlarınızı Uç Nokta için Microsoft Defender taşıyın. Microsoft 365 Defender, aşağıdakiler dahil olmak üzere diğer Microsoft 365 güvenlik çözümlerinden verilere erişebilirsiniz:

- Uç Nokta için Microsoft Defender
- Office 365 için Microsoft Defender
- Bulut Uygulamaları için Microsoft Defender
- Kimlik için Microsoft Defender

>[!NOTE]
>çoğu Uç Nokta için Microsoft Defender müşteri [Microsoft 365 Defender ek lisans olmadan kullanabilir](prerequisites.md#licensing-requirements). Gelişmiş avcılık iş akışlarınızı Uç Nokta için Defender'dan geçiş yapmaya başlamak için [Microsoft 365 Defender açın](m365d-enable.md).

Mevcut Uç Nokta için Defender iş akışlarınızı etkilemeden geçiş yapabilirsiniz. Kaydedilen sorgular olduğu gibi kalır ve özel algılama kuralları çalışmaya ve uyarı oluşturmaya devam eder. Ancak bunlar Microsoft 365 Defender görünür olacaktır.

## <a name="schema-tables-in-microsoft-365-defender-only"></a>Yalnızca Microsoft 365 Defender şema tabloları

[Microsoft 365 Defender gelişmiş tehdit avcılığı şeması](advanced-hunting-schema-tables.md), çeşitli Microsoft 365 güvenlik çözümlerinden veri içeren ek tablolar sağlar. Aşağıdaki tablolar yalnızca Microsoft 365 Defender kullanılabilir:

| Tablo adı | Açıklama |
|------------|-------------|
| [AlertEvidence](advanced-hunting-alertevidence-table.md) | Uyarılarla ilişkili dosyalar, IP adresleri, URL'ler, kullanıcılar veya cihazlar |
| [AlertInfo](advanced-hunting-alertinfo-table.md) | Uç Nokta için Microsoft Defender, Office 365 için Microsoft Defender, Microsoft Defender for Cloud Apps ve Kimlik için Microsoft Defender uyarıları , önem derecesi bilgileri ve tehdit kategorileri dahil  |
| [EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md) | E-postalara eklenen dosyalar hakkında bilgi |
| [EmailEvents](advanced-hunting-emailevents-table.md) | E-posta teslimi ve engelleme olayları dahil olmak üzere e-posta olaylarını Microsoft 365 |
| [EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md) | Microsoft 365 e-postaları alıcı posta kutusuna teslim ettikten sonra teslim sonrası gerçekleşen güvenlik olayları |
| [EmailUrlInfo](advanced-hunting-emailurlinfo-table.md) | E-postalardaki URL'ler hakkında bilgi |
| [IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md) | Active Directory (AD) çalıştıran bir şirket içi etki alanı denetleyicisini içeren olaylar. Bu tablo, etki alanı denetleyicisindeki kimlikle ilgili olayları ve sistem olaylarını kapsar. |
| [IdentityInfo](advanced-hunting-identityinfo-table.md) | Azure Active Directory dahil olmak üzere çeşitli kaynaklardan gelen hesap bilgileri |
| [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md) | Active Directory ve Microsoft çevrimiçi hizmetler kimlik doğrulama olayları |
| [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md) | Kullanıcılar, gruplar, cihazlar ve etki alanları gibi Active Directory nesneleri için sorgular |

>[!IMPORTANT]
> Yalnızca Microsoft 365 Defender'de kullanılabilen şema tablolarını kullanan sorgular ve özel algılamalar yalnızca Microsoft 365 Defender'de görüntülenebilir.

## <a name="map-devicealertevents-table"></a>DeviceAlertEvents tablosunu eşleme

ve tabloları, `AlertInfo` Uç Nokta için Microsoft Defender şemasındaki tablonun yerini alır`DeviceAlertEvents`.`AlertEvidence` Bu iki tablo, cihaz uyarıları hakkındaki verilere ek olarak kimlikler, uygulamalar ve e-postalar için uyarılarla ilgili verileri içerir.

Ve tablolarında sütunların sütunlara nasıl `DeviceAlertEvents` eşlenip eşlen `AlertInfo` `AlertEvidence` olmadığını denetlemek için aşağıdaki tabloyu kullanın.

> [!TIP]
> Aşağıdaki tablodaki sütunlara ek olarak, `AlertEvidence` tablo çeşitli kaynaklardan gelen uyarıların daha bütünsel bir resmini sağlayan birçok başka sütun içerir. [Tüm AlertEvidence sütunlarına bakın](advanced-hunting-alertevidence-table.md)

| DeviceAlertEvents sütunu | Microsoft 365 Defender'da aynı verilerin nerede bulunacağı |
|-------------|-----------|-------------|-------------|
| `AlertId` | `AlertInfo` ve  `AlertEvidence` tablolar |
| `Timestamp` | `AlertInfo` ve  `AlertEvidence` tablolar |
| `DeviceId` | `AlertEvidence` Tablo |
| `DeviceName` | `AlertEvidence` Tablo |
| `Severity` | `AlertInfo` Tablo |
| `Category` | `AlertInfo` Tablo |
| `Title` | `AlertInfo` Tablo |
| `FileName` | `AlertEvidence` Tablo |
| `SHA1` | `AlertEvidence` Tablo |
| `RemoteUrl` | `AlertEvidence` Tablo |
| `RemoteIP` | `AlertEvidence` Tablo |
| `AttackTechniques` | `AlertInfo` Tablo |
| `ReportId` | Bu sütun genellikle diğer tablolardaki ilgili kayıtları bulmak için Uç Nokta için Microsoft Defender kullanılır. Microsoft 365 Defender'da, ilgili verileri doğrudan tablodan `AlertEvidence` alabilirsiniz. |
| `Table` | Bu sütun genellikle diğer tablolardaki ek olay bilgileri için Uç Nokta için Microsoft Defender kullanılır. Microsoft 365 Defender'da, ilgili verileri doğrudan tablodan `AlertEvidence` alabilirsiniz. |

## <a name="adjust-existing-microsoft-defender-for-endpoint-queries"></a>Mevcut Uç Nokta için Microsoft Defender sorgularını ayarlama

Uç Nokta için Microsoft Defender sorgular tabloya `DeviceAlertEvents` başvurmadıkları sürece olduğu gibi çalışır. Bu sorguları Microsoft 365 Defender kullanmak için şu değişiklikleri uygulayın:

- değerini ile `AlertInfo`değiştirin`DeviceAlertEvents`.
- `AlertInfo` Eşdeğer verileri almak için ve `AlertEvidence` tablolarını `AlertId` birleştirin.

### <a name="original-query"></a>Özgün sorgu

Aşağıdaki sorgu,powershell.exeiçeren uyarıları almak için _Uç Nokta için Microsoft Defender_ kullanır`DeviceAlertEvents`:

```kusto
DeviceAlertEvents
| where Timestamp > ago(7d)
| where AttackTechniques has "PowerShell (T1086)" and FileName == "powershell.exe"
```

### <a name="modified-query"></a>Değiştirilen sorgu

Aşağıdaki sorgu Microsoft 365 Defender kullanılacak şekilde ayarlandı. Dosya adını doğrudan içinden `DeviceAlertEvents`denetlemek yerine, bu tablodaki dosya adını birleştirir `AlertEvidence` ve denetler.

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where AttackTechniques has "PowerShell (T1086)"
| join AlertEvidence on AlertId
| where FileName == "powershell.exe"
```

## <a name="migrate-custom-detection-rules"></a>Özel algılama kurallarını geçirme

Uç Nokta için Microsoft Defender kuralları Microsoft 365 Defender düzenlendiğinde, sonuçta elde edilen sorgu yalnızca cihaz tablolarına bakıyorsa önceki gibi çalışmaya devam ederler.

Örneğin, yalnızca cihaz tablolarını sorgulayan özel algılama kuralları tarafından oluşturulan uyarılar, bunları Uç Nokta için Microsoft Defender'de nasıl yapılandırdığınıza bağlı olarak SIEM'inize teslim edilmeye ve e-posta bildirimleri oluşturmaya devam eder. Uç Nokta için Defender'daki mevcut engelleme kuralları da uygulanmaya devam eder.

Yalnızca Microsoft 365 Defender'de kullanılabilen kimlik ve e-posta tablolarını sorgulayan bir Uç Nokta için Defender kuralını düzenledikten sonra, kural otomatik olarak Microsoft 365 Defender taşınır.

Geçirilen kural tarafından oluşturulan uyarılar:

- Uç Nokta için Defender portalında (Microsoft Defender Güvenlik Merkezi) artık görünmüyor
- SIEM'inize teslim edilmeyi durdurun veya e-posta bildirimleri oluşturun. Bu değişikliği geçici olarak çözmek için, uyarıları almak için Microsoft 365 Defender aracılığıyla bildirimleri yapılandırın. [Microsoft 365 Defender API'sini](api-incident.md) kullanarak müşteri algılama uyarılarına veya ilgili olaylara yönelik bildirimler alabilirsiniz.
- Uç Nokta için Microsoft Defender gizleme kuralları tarafından gizlenmeyecek. Belirli kullanıcılar, cihazlar veya posta kutuları için uyarıların oluşturulmasını önlemek için ilgili sorguları bu varlıkları açıkça dışlamak üzere değiştirin.

Bir kuralı bu şekilde düzenlerseniz, bu tür değişiklikler uygulanmadan önce sizden onay istenir.

Microsoft 365 Defender özel algılama kuralları tarafından oluşturulan yeni uyarılar, aşağıdaki bilgileri sağlayan bir uyarı sayfasında görüntülenir:

- Uyarı başlığı ve açıklaması
- Etkilenen varlıklar
- Uyarıya yanıt olarak gerçekleştirilen eylemler
- Uyarıyı tetikleyen sorgu sonuçları
- Özel algılama kuralıyla ilgili bilgiler

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/new-alert-page.png" alt-text="Microsoft 365 Defender portalında özel algılama kuralları tarafından oluşturulan yeni uyarıları görüntüleyen bir uyarı sayfası örneği" lightbox="../../media/new-alert-page.png":::

## <a name="write-queries-without-devicealertevents"></a>DeviceAlertEvents olmadan sorgu yazma

Microsoft 365 Defender şemasında `AlertInfo` ve `AlertEvidence` tabloları, çeşitli kaynaklardan gelen uyarılara eşlik eden çeşitli bilgi kümelerini barındırmak için sağlanır.

Uç Nokta için Microsoft Defender şemasındaki tablodan `DeviceAlertEvents` almak için kullandığınız uyarı bilgilerini almak için, tabloyu ölçütüne göre `ServiceSource` filtreleyin `AlertInfo` ve ardından her benzersiz kimliği ayrıntılı olay ve varlık bilgilerini sağlayan tabloyla birleştirin`AlertEvidence`.

Aşağıdaki örnek sorguya bakın:

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
| join AlertEvidence on AlertId
```

Bu sorgu, Uç Nokta için Microsoft Defender şemasından çok daha fazla sütun `DeviceAlertEvents` döndürür. Sonuçları yönetilebilir tutmak için yalnızca ilgilendiğiniz sütunları almak için kullanın `project` . Aşağıdaki örnek, araştırma PowerShell etkinliğini algıladığında ilginizi çekebilecek proje sütunlarıdır:

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
    and AttackTechniques has "powershell"
| join AlertEvidence on AlertId
| project Timestamp, Title, AlertId, DeviceName, FileName, ProcessCommandLine
```

Uyarılarda yer alan belirli varlıkları filtrelemek isterseniz, içindeki varlık türünü `EntityType` ve filtrelemek istediğiniz değeri belirterek bunu yapabilirsiniz. Aşağıdaki örnek belirli bir IP adresini arar:

```kusto
AlertInfo
| where Title == "Insert_your_alert_title"
| join AlertEvidence on AlertId
| where EntityType == "Ip" and RemoteIP == "192.88.99.01"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft 365 Defender’ı açın](advanced-hunting-query-language.md)
- [Gelişmiş avcılığa genel bakış](advanced-hunting-overview.md)
- [Şemayı anlayın](advanced-hunting-schema-tables.md)
- [Uç Nokta için Microsoft Defender'da gelişmiş avcılık](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
