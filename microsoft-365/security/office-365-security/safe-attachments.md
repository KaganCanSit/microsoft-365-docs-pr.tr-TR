---
title: Kasa Ekleri Kaydetme
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 6e13311e-92ae-495e-a619-56d770199170
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
- seo-marvel-apr2020
description: Yöneticiler, e-posta Kasa Microsoft Defender'daki Ekler özelliği hakkında bilgi Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b65813dedcf421e8335dc2433b5befee69cc60e6
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996495"
---
# <a name="safe-attachments-in-microsoft-defender-for-office-365"></a>Kasa için Microsoft Defender'daki Ekleri Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Kasa için [Microsoft Defender'daki](defender-for-office-365.md) Office 365 Ekleri, [Exchange Online Protection(EOP)](anti-malware-protection.md) üzerinde kötü amaçlı yazılımdan koruma ile taranmış e-posta ekleri için ek bir koruma katmanı sağlar. Özellikle de Kasa, Ekler e-posta iletileri alıcılarına teslim edilmediklerine (detonation olarak bilinen bir işlem) önce ekleri kontrol etmek için sanal bir _ortam kullanır_.

Kasa-posta iletileri için Eklere Karşı Koruma, E-posta Kasa tarafından denetleniyor. Varsayılan Kasa Ekler ilkesi her ne kadar da olsa, yerleşik koruma önceden ayarlanmış güvenlik  ilkesi tüm alıcılara Kasa Ekler koruması sağlar (özel Kasa Ek ilkeleri içinde tanımlanmamış kullanıcılar). Daha fazla bilgi için bkz[. İlke için EOP'de ve Microsoft Defender'da önceden Office 365](preset-security-policies.md). Belirli kullanıcılar, Kasa etki alanları için geçerli olan ek ilkeleri de oluşturabilirsiniz. Yönergeler için bkz[. Kasa için Microsoft Defender'da Ekleri ayarlama Office 365](set-up-safe-attachments-policies.md).

Aşağıdaki tabloda Microsoft 365'ta Kasa Ekleri için senaryolar ve Office 365 için Microsoft Defender içeren Office 365 (başka bir deyişle, örneklerde hiçbir zaman lisans olmaması sorunu değildir).

<br>

****

|Senaryo|Sonuç|
|---|---|
|Pat'in Microsoft 365 E5 yapılandırılmış ek Kasa yok.|Pat, Kasa Ekler tarafından, Ekler ilkesinde başka türlü tanımlanmamış tüm alıcılara uygulanan yerleşik koruma önceden ayarlanmış güvenlik ilkesi nedeniyle Kasa korunur.|
|Lee'nin kuruluşunda, yalnızca finans Kasa çalışanlara uygulanan Bir Ekler ilkesi vardır. Lee, satış departmanının bir üyesidir.|Lee ve satış departmanının kalan bölümü Kasa Ekleri tarafından, Kasa Ekleri ilkesinde başka türlü  tanımlanmamış tüm alıcılar için geçerli olan yerleşik koruma önceden ayarlanmış güvenlik ilkesi nedeniyle Kasa korunur.|
|Dün, Zaman'ın kuruluşunda bir yönetici tüm Kasa için geçerli olan bir Ekler ilkesi oluşturdu. Bugün daha önce, İleti ek içeren bir e-posta iletisi aldı.|Her zaman, Kasa ek ilkesi nedeniyle Ekler Kasa korunur. <p> Genellikle, yeni bir ilkenin yürürlüğe girecekleri yaklaşık 30 dakika sürer.|
|Chris'in kuruluşunda uzun süredir Kasa Ekler ilkeleri var. Chris, eki olan bir e-posta alır ve iletiyi dış alıcılara iletir.|Chis, E-Kasa tarafından korunur. <p> Bir kuruluşta dış alıcılar Microsoft 365, iletili iletiler de E-posta Ekleri Kasa korunur.|
|

Kasa tarama işlemi, dosya verilerinizin bulunduğu bölgede Microsoft 365 yer alır. Veri merkezi coğrafyası hakkında daha fazla bilgi için bkz [. Verileriniz nerede bulunur?](https://products.office.com/where-is-your-data-located?geo=All)

> [!NOTE]
> Aşağıdaki özellikler, Kasa portalında Ekleri ilkelerinin genel Microsoft 365 Defender bulunur. Ancak, bu ayarlar genel olarak etkinleştirilir veya devre dışı bırakılır ve eklerin Kasa gerektirmez:
>
> - [Kasa, Posta SharePoint, OneDrive için Ekleri Microsoft Teams](mdo-for-spo-odb-and-teams.md).
> - [Microsoft 365 E5 aboneliğinde Güvenli Belgeler](safe-docs.md)

## <a name="safe-attachments-policy-settings"></a>Kasa ler ilke ayarlarını değiştirme

Bu bölümde, Eklerin İlkeleri Kasa ayarları açık almaktadır:

- **Kasa bilinmeyen kötü amaçlı yazılım yanıtı**: Bu ayar, e-posta iletisinde kötü amaçlı yazılım Kasa amaçlı yazılım taramasına karşı eylemi kontrol eder. Kullanılabilir seçenekler aşağıdaki tabloda açıklanmıştır:

  <br>

  ****

  |Seçenek|Efekt|Şunları yapmak istediğiniz zaman kullanın:|
  |---|---|---|
  |**Kapalı**|Ekler, Ekleri Kullanarak Kötü Amaçlı Yazılım Kasa taranamaz. EOP'de, kötü amaçlı yazılımdan koruma [tarafından iletiler hâlâ kötü amaçlı yazılım için taranır](anti-malware-protection.md).|Seçili alıcılar için taramayı kapatın. <p> İç postayı yönlendirmede gereksiz gecikmeleri önle. <p> **Bu seçenek çoğu kullanıcı için önerilmez. Yalnızca güvenilen gönderenlerden ileti alan alıcıları Kasa Ekler taramayı kapatmak için bu seçeneği kullanabilirsiniz. EKLER kapalı ise ve kötü amaçlı yazılım sinyali Kasa ZAP iletileri karantinaya alanmaz. Ayrıntılar için bkz [. Sıfır saatlik otomatik temizleme](zero-hour-auto-purge.md)**|
  |**Monitör**|Ekleri olan iletileri teslim edin ve ardından algılanan kötü amaçlı yazılımla ne olduğunu izler. <p> Ekler tarama özelliği nedeniyle güvenli iletilerin teslimi Kasa ertelenebilir.|Kötü amaçlı yazılım algılandığından kuruluşta nereye gittiğini bakın.|
  |**Engelle**|Kötü amaçlı yazılım ekleri algılandığında iletilerin teslim edile engel olur. <p> İletiler karantinaya alınır. Varsayılan olarak iletileri yalnızca yöneticiler (kullanıcılar değil) gözden geçirebilirsiniz, yayımlar veya silebilir.<sup>\*</sup> <p> İletilerin ve eklerin gelecekteki örneklerini otomatik olarak engeller. <p> Ekler tarama özelliği nedeniyle güvenli iletilerin teslimi Kasa ertelenebilir.|Aynı kötü amaçlı yazılım eklerini kullanarak organizasyonlarınızı tekrarlanan saldırılardan korur. <p> Bu, varsayılan değerdir ve Standart ve Katı önceden tanımlı güvenlik ilkelerde [önerilen değerdir](preset-security-policies.md).|
  |**Değiştir**|Algılanan kötü amaçlı yazılım eklerini kaldırır. <p> Alıcılara eklerin kaldırıldığıyla ilgili bilgi gönderilir. <p>  Kötü amaçlı ek içeren iletiler karantinaya alınır. Varsayılan olarak iletileri yalnızca yöneticiler (kullanıcılar değil) gözden geçirebilirsiniz, yayımlar veya silebilir.<sup>\*</sup> <p> Ekler tarama özelliği nedeniyle güvenli iletilerin teslimi Kasa ertelenebilir.|Algılandı kötü amaçlı yazılım nedeniyle eklerin kaldırıldığı alıcılara görünürlüğü yükseltin.|
  |**Dinamik Teslim**|İletileri anında teslim edin, ancak ekler tarama işlemi tamamlandıktan sonra Kasa yer tutucularla değiştirir. <p> Kötü amaçlı ek içeren iletiler karantinaya alınır. Varsayılan olarak iletileri yalnızca yöneticiler (kullanıcılar değil) gözden geçirebilirsiniz, yayımlar veya silebilir.<sup>\*</sup> <p> Ayrıntılar için, bu [makalenin devam Kasa Ek İlkeleri'nin](#dynamic-delivery-in-safe-attachments-policies) Dinamik Teslimi bölümüne bakın.|Alıcıları kötü amaçlı dosyalardan korurken ileti gecikmelerinden kaçının.|
  |

  <sup>\*</sup>Yöneticiler, karantinaya alınan iletiler _için ne_ yapmalarına izin Kasa Ek ilkeleri içinde karantina ilkeleri oluşturabilir ve atayabilirsiniz. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md).

- Eki **algılamada** yeniden yönlendirme: Yeniden yönlendirmeyi etkinleştir ve Eki şu e-posta adresine **gönder: Engelleme****, İzleme** veya Değiştir eylemleri için, kötü amaçlı yazılım ekleri içeren iletileri çözümleme ve soruşturma için belirtilen iç veya dış e-posta adresine gönderin. 

  Standart ve Katı ilke ayarları için öneri, yeniden yönlendirmeyi etkinleştirmektir. Daha fazla bilgi için Bkz[. Kasa ayarlarına bakın](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

- Kötü amaçlı yazılım ekleri tarayın zaman dışında veya hata oluşursa yukarıdaki seçimi **uygula:** **Kasa** Ekler bilinmeyen kötü amaçlı yazılım yanıtı tarafından belirtilen eylem, Kasa Ekler tarama tamamlanamasa bile iletilere alınır. Yönlendirmeyi etkinleştir'i her zaman seçerek **bu seçeneği belirtin**. Aksi takdirde, iletiler kaybolabilir.

- **Alıcı filtreleri**: İlkenin kimlere geçerli olduğunu belirleyen alıcı koşullarını ve özel durumlarını belirtmeniz gerekir. Bu özellikleri koşullar ve özel durumlar için kullanabilirsiniz:
  - **Alıcı**
  - **Alıcı etki alanı:**
  - **Alıcı,**

  Bir koşul veya özel durumu tek bir kez kullanabilirsiniz, ancak koşul veya özel durum birden çok değer içerebilir. Aynı koşul veya özel durum kullanımı VEYA mantığının birden çok değeri (örneğin, _\<recipient1\>_ veya _\<recipient2\>_). Farklı koşullar veya özel durumlar, AND mantığı kullanır (örneğin, _\<recipient1\>_ ve _\<member of group 1\>_).

- **Öncelik**: Birden çok ilke sanız, uygulanma sıralarını belirtsiniz. İki ilke aynı önceliğe sahip olabilir ve ilk ilke uygulandıktan sonra ilke işleme durur.

  Öncelik sırası, birden çok ilkenin nasıl değerlendirilip uygulandığı hakkında daha fazla bilgi için bkz. [E-posta korumasının sırası ve önceliği](how-policies-and-protections-are-combined.md).

### <a name="dynamic-delivery-in-safe-attachments-policies"></a>Eklerde Dinamik Kasa ilkeleri

> [!NOTE]
> Dinamik Teslim yalnızca bu posta Exchange Online çalışır.

Ekler'de Dinamik Teslim Kasa ilkeleri, Ekler tarama özelliği tarafından neden olabileceği e-posta teslim gecikmelerini Kasa arıyor. E-posta iletisi gövdesi, her ek için bir yer tutucu içeren alıcıya teslim edilir. Yer tutucu, ek güvenli bulunana kadar kalır ve sonra ek aç/indirilebilir duruma gelir.

Bir ek kötü amaçlı olarak bulunursa, ileti karantinaya alınır.

Ekleri tarama Office devam ederken çoğu PDF ve Kasa belgeleri güvenli modda öniz olabilir. Bir ek Dinamik Teslim önizicisi ile uyumlu değilse, Ekler tarama tamamlandıktan sonra alıcılar ek için Kasa yer tutucusu görebilirler.

Mobil cihaz kullanıyorsanız ve PDF'ler mobil cihazınızın Dinamik Teslim önizizicisinde işleniğine sahip değilse, mobil tarayıcınızı kullanarak iletiyi Web üzerinde Outlook'de (eski adı Outlook Web App) kullanmayı deneyin.

Dinamik Teslim ve iletili iletilerde dikkat edilmesi gereken bazı noktalar:

- Forwarded recipient is protected by a Kasa Attachments policy that uses the Dynamic Delivery option, then alıcı sees the placeholder, with the ability to preview compatible files.
- İletilen alıcı bir Kasa Ekleri ilkesi tarafından korunmazsa, ileti ve ekler herhangi bir ek Kasa tarama veya ek yer tutucuları olmadan teslim edilir.

Dinamik Teslim'in iletilerde ekleri değiştiramadığı senaryolar vardır. Bu senaryolar şunlardır:

- Ortak klasörlerdeki iletiler.
- Özel kurallar kullanılarak kullanıcının posta kutusundan dışarı yönlendiren ve sonra geri yönlendiren iletiler.
- Bulut posta kutularının dışından arşiv klasörleri de dahil olmak üzere başka konumlara taşınan iletiler (otomatik olarak veya el ile).
- Gelen kutusu kuralları iletiyi Gelen Kutusu'dan farklı bir klasöre taşınır.
- Silinmiş iletiler.
- Kullanıcının posta kutusu arama klasörü hata durumda.
- Exchange Online Alıntı özelliği etkin durumda olan kuruluşlarda çalışır. Bu sorunu çözmek için bkz [. KB4014438](https://support.microsoft.com/help/4014438).
- [S/MIME)](/exchange/security-and-compliance/smime-exo/smime-exo) şifreli iletiler.
- Dinamik Teslim eylemi Kasa Ekleri ilkesinde yapılandırdınız, ancak alıcı Dinamik Teslimi desteklemez (örneğin, alıcı şirket içi bir Exchange posta kutusudur). Ancak [Kasa için Microsoft Defender'daki](set-up-safe-links-policies.md) Bağlantılar Office 365 URL içeren Office ekleri tarayabilirsiniz (bağlantıların genel ayarlarına bağlı olarak [Kasa](configure-global-settings-for-safe-links.md) yapılandırıldığında).

## <a name="submitting-files-for-malware-analysis"></a>Kötü amaçlı yazılım çözümlemesi için dosya gönderme

- Çözümleme için Microsoft'a göndermek istediğiniz bir dosya alırsanız, çözümleme için Kötü amaçlı yazılım ve kötü amaçlı yazılım olmayan dosyaları [Microsoft'a gönderme makalesi'ne bakın](submitting-malware-and-non-malware-to-microsoft-for-analysis.md).
- Çözümleme için Microsoft'a göndermek istediğiniz bir e-posta iletisi (ekli veya eksiz) alırsanız bkz. İletileri ve [dosyaları Microsoft'a bildirme](report-junk-email-messages-to-microsoft.md).
