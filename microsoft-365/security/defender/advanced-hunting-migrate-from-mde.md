---
title: Uç nokta için Microsoft Defender'dan gelişmiş arama sorgularını geçirme
description: Microsoft Defender for Endpoint sorgularınızı farklı bir uygulamayla kullanmak üzere nasıl ayarlay öğrenin Microsoft 365 Defender
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, Uç Nokta için Microsoft Defender, arama, sorgu, telemetri, özel algılamalar, şema, kusto, eşleme
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
ms.openlocfilehash: e64d1a56468d6e87d23c5720bb231e17ecd5679a
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2022
ms.locfileid: "63014172"
---
# <a name="migrate-advanced-hunting-queries-from-microsoft-defender-for-endpoint"></a>Uç nokta için Microsoft Defender'dan gelişmiş arama sorgularını geçirme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Daha geniş bir veri kümesi kullanarak tehditlere karşı önceden arama yapmak için gelişmiş av iş akışlarınızı Uç Nokta için Microsoft Defender'dan taşıma. Microsoft 365 Defender'da, diğer güvenlik çözümlerinden Microsoft 365 erişebilirsiniz:

- Uç Nokta için Microsoft Defender
- Office 365 için Microsoft Defender
- Bulut Uygulamaları için Microsoft Defender
- Kimlik için Microsoft Defender

>[!NOTE]
>Uç nokta müşterileri için Microsoft Defender müşterilerinin çoğu [Microsoft 365 Defender lisansı olmadan bu hizmeti kullanabilir](prerequisites.md#licensing-requirements). Gelişmiş av iş akışlarınızı Uç Nokta için Defender'dan geçişi başlatmak için[, Gelişmiş Microsoft 365 Defender](m365d-enable.md).

Uç nokta iş akışları için var olan Defender'ı etkilemeden geçişebilirsiniz. Kaydedilen sorgular olduğu gibi kalır ve özel algılama kuralları çalışmaya ve uyarılar oluşturmaya devam eder. Bununla birlikte, diğer tüm Microsoft 365 Defender. 

## <a name="schema-tables-in-microsoft-365-defender-only"></a>Yalnızca iş Microsoft 365 Defender şema tabloları
Gelişmiş [Microsoft 365 Defender şema, çeşitli](advanced-hunting-schema-tables.md) arama ve güvenlik çözümlerinden veri içeren Microsoft 365 sağlar. Aşağıdaki tablolar yalnızca aşağıdaki Microsoft 365 Defender:

| Tablo adı | Açıklama |
|------------|-------------|
| [AlertEvidence](advanced-hunting-alertevidence-table.md) | Uyarılarla ilişkilendirilmiş dosyalar, IP adresleri, URL'ler, kullanıcılar veya cihazlar |
| [UyarıBilgileri](advanced-hunting-alertinfo-table.md) | Önem derecesi bilgileri ve tehdit kategorileri de dahil olmak üzere Uç Nokta için Microsoft Defender, Office 365 için Microsoft Defender, Bulut Uygulamaları için Microsoft Defender ve Kimlik için Microsoft Defender uyarıları  |
| [EmailAttachmentInfo](advanced-hunting-emailattachmentinfo-table.md) | E-postalara eklenen dosyalar hakkında bilgi |
| [EmailEvents](advanced-hunting-emailevents-table.md) | Microsoft 365 teslimi ve engelleme etkinlikleri de dahil olmak üzere e-posta etkinliklerini engelleme |
| [EmailPostDeliveryEvents](advanced-hunting-emailpostdeliveryevents-table.md) | E-postalar alıcı posta kutusuna teslim Microsoft 365 sonra, teslim sonrası oluşan güvenlik olayları |
| [EmailUrlInfo](advanced-hunting-emailurlinfo-table.md) | E-postalarda yer alan URL'ler hakkında bilgiler |
| [IdentityDirectoryEvents](advanced-hunting-identitydirectoryevents-table.md) | Active Directory (AD) çalıştıran bir şirket içi etki alanı denetleyicisini içeren olaylar. Bu tablo, etki alanı denetleyicisinde kimlikle ilgili çeşitli olayları ve sistem olaylarını kapsar. |
| [IdentityInfo](advanced-hunting-identityinfo-table.md) | Hesap bilgileri de dahil olmak üzere çeşitli kaynaklardan Azure Active Directory |
| [IdentityLogonEvents](advanced-hunting-identitylogonevents-table.md) | Active Directory ve Microsoft çevrimiçi hizmetlerinde kimlik doğrulama olayları |
| [IdentityQueryEvents](advanced-hunting-identityqueryevents-table.md) | Kullanıcılar, gruplar, cihazlar ve etki alanları gibi Active Directory nesneleri için sorgular |

>[!IMPORTANT]
> Yalnızca başka bir tabloda kullanılabilen şema tablolarını kullanan sorgular ve Microsoft 365 Defender algılamalar yalnızca Microsoft 365 Defender.

## <a name="map-devicealertevents-table"></a>DeviceAlertEvents tablosuna eşleme
Uç `AlertInfo` nokta `AlertEvidence` için `DeviceAlertEvents` Microsoft Defender şemasında tabloyu ve tablolar değiştirir. Cihaz uyarıları ile ilgili verilere ek olarak, bu iki tablo kimlikler, uygulamalar ve e-postalar için uyarılarla ilgili veriler de içerir.

Sütunların ve tablodaki sütunların `DeviceAlertEvents` nasıl eşlenitasını kontrol etmek için aşağıdaki `AlertInfo` tabloyu `AlertEvidence` kullanın.

>[!TIP]
>Aşağıdaki tabloda yer alan sütunlara ek olarak, `AlertEvidence` tablo çeşitli kaynaklardan gelen uyarıların daha holist bir resmini sağlayan başka birçok sütun içerir. [Tüm AlertEvidence sütunlarını görme](advanced-hunting-alertevidence-table.md) 

| DeviceAlertEvents sütunu | Aynı verileri aynı yerde bulma Microsoft 365 Defender |
|-------------|-----------|-------------|-------------|
| `AlertId` | `AlertInfo` ve  `AlertEvidence` tablolar |
| `Timestamp` | `AlertInfo` ve  `AlertEvidence` tablolar |
| `DeviceId` | `AlertEvidence` tablo |
| `DeviceName` | `AlertEvidence` tablo |
| `Severity` | `AlertInfo` tablo |
| `Category` | `AlertInfo` tablo |
| `Title` | `AlertInfo` tablo |
| `FileName` | `AlertEvidence` tablo |
| `SHA1` | `AlertEvidence` tablo |
| `RemoteUrl` | `AlertEvidence` tablo |
| `RemoteIP` | `AlertEvidence` tablo |
| `AttackTechniques` | `AlertInfo` tablo |
| `ReportId` | Bu sütun normalde diğer tablolarda ilişkili kayıtları bulmak için Uç Nokta için Microsoft Defender'da kullanılır. Diğer Microsoft 365 Defender, ilişkili verileri doğrudan tablodan alırsınız`AlertEvidence`. |
| `Table` | Bu sütun normalde diğer tablolarda ek olay bilgileri için Uç Nokta için Microsoft Defender'da kullanılır. Diğer Microsoft 365 Defender, ilişkili verileri doğrudan tablodan alırsınız`AlertEvidence`. |

## <a name="adjust-existing-microsoft-defender-for-endpoint-queries"></a>Uç nokta sorguları için mevcut Microsoft Defender'ı ayarlama
Uç Nokta sorguları için Microsoft Defender, tabloya başvurmayacaksa olduğu gibi `DeviceAlertEvents` çalışır. Bu sorguları aynı sorgularda Microsoft 365 Defender, şu değişiklikleri yapın:

- ile `DeviceAlertEvents` değiştirin `AlertInfo`.
- Eşdeğer veriler `AlertInfo` elde etmek `AlertEvidence` için tabloları `AlertId` ve tabloları birleştirme.

### <a name="original-query"></a>Özgün sorgu
Aşağıdaki sorgu, uç noktayla `DeviceAlertEvents` ilgili uyarıları almak için Uç Nokta için Microsoft _Defender'dapowershell.exe_:

```kusto
DeviceAlertEvents
| where Timestamp > ago(7d) 
| where AttackTechniques has "PowerShell (T1086)" and FileName == "powershell.exe"
```
### <a name="modified-query"></a>Sorgu değiştirildi
Aşağıdaki sorgu, başka bir sorguda kullanım Microsoft 365 Defender. Dosya adını doğrudan üzerinden kontrol etmek yerine `DeviceAlertEvents`, o `AlertEvidence` tablodaki dosya adını bir alır ve denetler.

```kusto
AlertInfo 
| where Timestamp > ago(7d) 
| where AttackTechniques has "PowerShell (T1086)" 
| join AlertEvidence on AlertId
| where FileName == "powershell.exe"
```

## <a name="migrate-custom-detection-rules"></a>Özel algılama kurallarını geçirme

Uç nokta kuralları için Microsoft Defender Microsoft 365 Defender, sonuçta elde edilen sorgu yalnızca cihaz tablolarına görünüyor gibi çalışmaya devam eder. 

Örneğin, yalnızca cihaz tablolarını sorgu eden özel algılama kuralları tarafından oluşturulan uyarılar, bunları Uç Nokta için Microsoft Defender'da nasıl yapılandırdınıza bağlı olarak SIEM'nize teslim olmaya ve e-posta bildirimleri oluşturmaya devam eder. Uç Nokta için Defender'da var olan tüm gizleme kuralları da uygulanabilecektir.

Uç nokta için Defender kuralını düzenlenin, yalnızca Microsoft 365 Defender'de kullanılabilen kimlik ve e-posta tablolarını sorgular, kural otomatik olarak Başka bir Microsoft 365 Defender. 

Geçirilen kural tarafından oluşturulan uyarılar:

- Uç nokta portalı için Defender'da (Microsoft Defender Güvenlik Merkezi)
- SIEM'nize teslim etmeyi durdurun veya e-posta bildirimleri üretin. Bu değişiklikle ilgili olarak, uyarıları almak Microsoft 365 Defender aracılığıyla bildirimleri yapılandırarak yapılandırma. Bu [API'yi Microsoft 365 Defender algılama](api-incident.md) uyarıları veya ilgili olaylarla ilgili bildirimler almak için kullanabilirsiniz.
- Uç nokta gizleme kuralları için Microsoft Defender bunu gizlemez. Belirli kullanıcılar, cihazlar veya posta kutuları için uyarı oluşturmasını önlemek için, ilgili sorguları söz konusu varlıkları açıkça dışarıda bırakacak şekilde değiştirebilirsiniz.

Kuralı bu şekilde düzenlersanız, bu değişiklikler uygulanmadan önce onay istenir.

E-postada özel algılama kuralları tarafından Microsoft 365 Defender yeni uyarılar, aşağıdaki bilgileri sağlayan bir uyarı sayfasında görüntülenir:

- Uyarı başlığı ve açıklaması 
- Etkide olan varlıklar
- Uyarıya yanıt olarak alınan eylemler
- Uyarıyı tetikleyen sorgu sonuçları 
- Özel algılama kuralı hakkında bilgi 
 
> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/new-alert-page.png" alt-text="Portalda özel algılama kuralları tarafından oluşturulan yeni uyarıları görüntüleyen bir uyarı Microsoft 365 Defender örneği" lightbox="../../media/new-alert-page.png":::

## <a name="write-queries-without-devicealertevents"></a>DeviceAlertEvents olmadan sorgu yazma

Tablo Microsoft 365 Defender, `AlertInfo` `AlertEvidence` çeşitli kaynaklardan gelen uyarılara eşlik eden farklı bilgi kümelerine uyum sağlanacak şekilde ve tablolar sağlanır. 

Uç nokta `DeviceAlertEvents` için Microsoft Defender şemasında yer alan tablodan almak için kullandığı uyarı bilgilerini almak için, `AlertInfo` `ServiceSource` `AlertEvidence` tabloya filtre uygulama ve ardından ayrıntılı olay ve varlık bilgilerini sağlayan her benzersiz kimliği tabloyla birleştirme. 

Aşağıdaki örnek sorguya bakın:

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
| join AlertEvidence on AlertId
```

Bu sorgu Uç nokta için Microsoft Defender şemasına `DeviceAlertEvents` göre çok daha fazla sütun sağlar. Sonuçların yönetilebilir durumda tutmak için `project` , yalnızca ilgilendiğiniz sütunları elde etmek için kullanın. Aşağıdaki örnekte, araştırma PowerShell etkinliği algılandığında ilginizi çekebilirsiniz:

```kusto
AlertInfo
| where Timestamp > ago(7d)
| where ServiceSource == "Microsoft Defender for Endpoint"
    and AttackTechniques has "powershell"
| join AlertEvidence on AlertId
| project Timestamp, Title, AlertId, DeviceName, FileName, ProcessCommandLine 
```

Uyarılara katılan belirli varlıklar için filtrelemek istediğiniz varlıklar varsa, `EntityType` filtrelemek istediğiniz varlık türünü ve değerini belirterek bunu da kullanabilirsiniz. Aşağıdaki örnek belirli bir IP adresini aramaz:

```kusto
AlertInfo
| where Title == "Insert_your_alert_title"
| join AlertEvidence on AlertId 
| where EntityType == "Ip" and RemoteIP == "192.88.99.01" 
```

## <a name="see-also"></a>Ayrıca bkz.
- [E-Microsoft 365 Defender](advanced-hunting-query-language.md)
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Uç Nokta için Microsoft Defender'da gelişmiş av](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)
