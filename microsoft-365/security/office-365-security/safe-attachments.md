---
title: Güvenli Ekleri Kaydetme
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
description: Yöneticiler, Office 365 için Microsoft Defender Kasa Ekleri özelliği hakkında bilgi edinebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9d069d92eb012211af8dd4e12109ebcae7eb221e
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65128728"
---
# <a name="safe-attachments-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'da Ekleri Kasa

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Kasa [Office 365 için Microsoft Defender'deki Ekler,](defender-for-office-365.md) [Exchange Online Protection'da (EOP) kötü amaçlı yazılımdan koruma](anti-malware-protection.md) tarafından zaten taranmış e-posta ekleri için ek bir koruma katmanı sağlar. Özellikle, Kasa Ekler, e-posta iletilerindeki ekleri alıcılara teslim etmeden önce denetlemek için bir sanal ortam kullanır (_patlama_ olarak bilinen bir işlem).

Kasa E-posta iletileri için Ekler koruması Kasa Ekler ilkeleri tarafından denetlenmektedir. Varsayılan Kasa Ekler ilkesi olmasa **da, Yerleşik koruma** önceden ayarlanmış güvenlik ilkesi tüm alıcılara Kasa Ekler koruması sağlar (özel Kasa Ekler ilkelerinde tanımlanmayan kullanıcılar). Daha fazla bilgi için bkz. [EOP'de önceden ayarlanmış güvenlik ilkeleri ve Office 365 için Microsoft Defender](preset-security-policies.md). Ayrıca, belirli kullanıcılar, gruplar veya etki alanları için geçerli Kasa Ekler ilkeleri de oluşturabilirsiniz. Yönergeler için bkz. [Office 365 için Microsoft Defender Kasa Ekler ilkelerini ayarlama](set-up-safe-attachments-policies.md).

Aşağıdaki tabloda, Microsoft 365 ve Office 365 kuruluşlarda Office 365 için Microsoft Defender içeren Kasa Ekleri senaryoları açıklanmaktadır (başka bir deyişle, lisans eksikliği örneklerde hiçbir zaman sorun değildir).

|Senaryo|Sonuç|
|---|---|
|Pat'in Microsoft 365 E5 kuruluşunda yapılandırılmış Kasa Ek ilkeleri yoktur.|Pat, Kasa Ekler ilkelerinde başka şekilde tanımlanmayan tüm alıcılar için geçerli olan **Yerleşik koruma** önayarlı güvenlik ilkesi nedeniyle Kasa Ekler tarafından korunur.|
|Lee'nin kuruluşu, yalnızca finans çalışanları için geçerli olan bir Kasa Ekleri ilkesine sahiptir. Lee satış departmanının bir üyesi.|Lee ve satış departmanının geri kalanı, Kasa Ekler ilkelerinde başka şekilde tanımlanmayan tüm alıcılar için geçerli olan **Yerleşik koruma** ön ayarı güvenlik ilkesi nedeniyle Kasa Ekler tarafından korunur.|
|Dün Jean'in kuruluşundaki bir yönetici, tüm çalışanlar için geçerli olan bir Kasa Eki ilkesi oluşturdu. Bugün erken saatlerde Jean ek içeren bir e-posta iletisi aldı.|Jean, özel Kasa Ekler ilkesi nedeniyle Kasa Ekler tarafından korunur. <br/><br/> Genellikle yeni bir ilkenin geçerlilik kazanması yaklaşık 30 dakika sürer.|
|Chris'in kuruluşu, kuruluştaki herkes için uzun süredir Kasa Ekler ilkelerine sahiptir. Chris eki olan bir e-posta alır ve ardından iletiyi dış alıcılara iletir.|Chis, Kasa Ekleri tarafından korunur. <br/><br/> Microsoft 365 bir kuruluştaki dış alıcılar da Kasa Ekler tarafından korunur.|

Kasa Ekler taraması, Microsoft 365 verilerinizin bulunduğu bölgede gerçekleşir. Veri merkezi coğrafyası hakkında daha fazla bilgi için bkz. [Verileriniz nerede bulunur?](https://products.office.com/where-is-your-data-located?geo=All)

> [!NOTE]
> Aşağıdaki özellikler, Microsoft 365 Defender portalındaki Kasa Ekler ilkelerinin genel ayarlarında bulunur. Ancak bu ayarlar genel olarak etkinleştirilir veya devre dışı bırakılır ve Kasa Ekler ilkeleri gerekmez:
>
> - [SharePoint, OneDrive ve Microsoft Teams için ekleri Kasa](mdo-for-spo-odb-and-teams.md).
> - [Microsoft 365 E5 aboneliğinde Güvenli Belgeler](safe-docs.md)

## <a name="safe-attachments-policy-settings"></a>Kasa Ekler ilke ayarları

Bu bölümde, Kasa Ekler ilkelerindeki ayarlar açıklanmaktadır:

- **Kasa Ekler bilinmeyen kötü amaçlı yazılım yanıtı**: Bu ayar, e-posta iletilerinde Kasa Ekler kötü amaçlı yazılım taraması eylemini denetler. Kullanılabilir seçenekler aşağıdaki tabloda açıklanmıştır:

  |Seçeneği|Etkisi|Şunu yapmak istediğinizde kullanın:|
  |---|---|---|
  |**Kapalı**|Ekler, Kasa Ekler tarafından kötü amaçlı yazılım taramasına neden olmaz. EOP'de kötü amaçlı yazılımdan [koruma tarafından iletiler yine de kötü amaçlı yazılımlara](anti-malware-protection.md) karşı taranır.|Seçili alıcılar için taramayı kapatın. <br/><br/> İç posta yönlendirmede gereksiz gecikmeleri önleyin. <br/><br/> **Bu seçenek çoğu kullanıcı için önerilmez. Bu seçeneği yalnızca güvenilen gönderenlerden yalnızca ileti alan alıcılar için Kasa Ekler taramasını kapatmak için kullanmalısınız. KASA Ekler kapalıysa ve kötü amaçlı yazılım sinyali alınmazsa ZAP iletileri karantinaya almayacaktır. Ayrıntılar için bkz. [Sıfır saatlik otomatik temizleme](zero-hour-auto-purge.md)**|
  |**Monitör**|Ekleri olan iletileri teslim eder ve ardından algılanan kötü amaçlı yazılımla ne olduğunu izler. <br/><br/> güvenli iletilerin teslimi Kasa Ekler tarama nedeniyle gecikebilir.|Algılanan kötü amaçlı yazılımların kuruluşunuzda nereye gittiğini görün.|
  |**Engelle**|Algılanan kötü amaçlı yazılım eklerine sahip iletilerin teslim edilmesini engeller. <br/><br/> İletiler karantinaya alınır. Varsayılan olarak, iletileri yalnızca yöneticiler (kullanıcılar değil) gözden geçirebilir, yayımlayabilir veya silebilir.<sup>\*</sup> <br/><br/> İletilerin ve eklerin gelecekteki örneklerini otomatik olarak engeller. <br/><br/> güvenli iletilerin teslimi Kasa Ekler tarama nedeniyle gecikebilir.|Aynı kötü amaçlı yazılım eklerini kullanarak kuruluşunuzu tekrarlanan saldırılara karşı korur. <br/><br/> Bu varsayılan değerdir ve Standart ve Katı [önceden belirlenmiş güvenlik ilkeleri](preset-security-policies.md) için önerilen değerdir.|
  |**Değiştirmek**|Algılanan kötü amaçlı yazılım eklerini kaldırır. <br/><br/> Alıcılara eklerin kaldırıldığını bildirir. <br/><br/>  Kötü amaçlı ekler içeren iletiler karantinaya alınır. Varsayılan olarak, iletileri yalnızca yöneticiler (kullanıcılar değil) gözden geçirebilir, yayımlayabilir veya silebilir.<sup>\*</sup> <br/><br/> güvenli iletilerin teslimi Kasa Ekler tarama nedeniyle gecikebilir.|Algılanan kötü amaçlı yazılım nedeniyle eklerin kaldırıldığı alıcılara görünürlük sağlayın.|
  |**Dinamik Teslim**|İletileri hemen teslim eder, ancak Kasa Ekler taraması tamamlanana kadar ekleri yer tutucularla değiştirir. <br/><br/> Kötü amaçlı ekler içeren iletiler karantinaya alınır. Varsayılan olarak, iletileri yalnızca yöneticiler (kullanıcılar değil) gözden geçirebilir, yayımlayabilir veya silebilir.<sup>\*</sup> <br/><br/> Ayrıntılar için, bu makalenin [devamında yer alan Kasa Ekler ilkelerinde Dinamik Teslim](#dynamic-delivery-in-safe-attachments-policies) bölümüne bakın.|Alıcıları kötü amaçlı dosyalardan korurken ileti gecikmelerinden kaçının.|

  <sup>\*</sup>Yöneticiler, kullanıcıların _karantinaya alınan iletilere_ ne yapmalarına izin verildiğini tanımlayan Kasa Ekler ilkelerinde karantina ilkeleri oluşturabilir ve atayabilir. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md).

- **Algılama sırasında eki yeniden yönlendirme: Yeniden yönlendirmeyi etkinleştirin** ve **Eki şu e-posta adresine gönderin**: **Engelle**, **İzle** veya **Değiştir** eylemleri için, analiz ve araştırma için belirtilen iç veya dış e-posta adresine kötü amaçlı yazılım ekleri içeren iletiler gönderin.

  Standart ve Katı ilke ayarları için öneri, yeniden yönlendirmeyi etkinleştirmektir. Daha fazla bilgi için bkz. [Kasa Ekler ayarları](recommended-settings-for-eop-and-office365.md#safe-attachments-settings).

- **Ekler için kötü amaçlı yazılım taraması zaman aşımına uğradıysa veya hata oluşursa yukarıdaki seçimi uygulayın**: **Kasa Ekler bilinmeyen kötü amaçlı yazılım yanıtı** tarafından belirtilen eylem, Kasa Ekler taraması tamamlanamadıklarında bile iletilerde gerçekleştirilir. **Yeniden yönlendirmeyi etkinleştir'i** seçerseniz her zaman bu seçeneği belirleyin. Aksi takdirde iletiler kaybolabilir.

- **Alıcı filtreleri**: İlkenin kime uygulanacağını belirleyen alıcı koşullarını ve özel durumlarını belirtmeniz gerekir. Koşullar ve özel durumlar için şu özellikleri kullanabilirsiniz:
  - **Alıcı**
  - **Alıcı etki alanı**
  - **Alıcı,**

  Bir koşulu veya özel durumu yalnızca bir kez kullanabilirsiniz, ancak koşul veya özel durum birden çok değer içerebilir. Aynı koşula veya özel duruma ait birden çok değer OR mantığını kullanır (örneğin, _\<recipient1\>_ veya _\<recipient2\>_). Farklı koşullar veya özel durumlar AND mantığını kullanır (örneğin, _\<recipient1\>_ ve _\<member of group 1\>_).

- **Öncelik**: Birden çok ilke oluşturursanız, bunların uygulanacağı sırayı belirtebilirsiniz. hiçbir iki ilke aynı önceliğe sahip olamaz ve ilke işleme ilk ilke uygulandıktan sonra durur.

  Öncelik sırası ve birden çok ilkenin nasıl değerlendirilip uygulandığı hakkında daha fazla bilgi için bkz [. E-posta korumasının sırası ve önceliği](how-policies-and-protections-are-combined.md).

### <a name="dynamic-delivery-in-safe-attachments-policies"></a>Kasa Eklerinde Dinamik Teslim ilkeleri

> [!NOTE]
> Dinamik Teslim yalnızca Exchange Online posta kutuları için çalışır.

Kasa Ekler ilkelerindeki Dinamik Teslim eylemi, Kasa Ekler taramasının neden olabileceği e-posta teslim gecikmelerini ortadan kaldırmaya çalışır. E-posta iletisinin gövdesi, her ek için bir yer tutucu ile alıcıya teslim edilir. Yer tutucu, ek güvenli bulunana kadar kalır ve ek açılabilir veya indirilebilir hale gelir.

Bir ekin kötü amaçlı olduğu tespit edilirse, ileti karantinaya alınır.

Kasa Ekler taraması devam ederken çoğu PDF ve Office belge güvenli modda önizlenebilir. Bir ek Dinamik Teslim önİzleyicisi ile uyumlu değilse, Kasa Ekler taraması tamamlanana kadar alıcılar ek için bir yer tutucu görür.

Mobil cihaz kullanıyorsanız ve PDF'ler mobil cihazınızda dinamik teslim önizleyicisinde işlenmiyorsa, mobil tarayıcınızı kullanarak iletiyi Web üzerinde Outlook (eski adıyla Outlook Web App) açmayı deneyin.

Dinamik Teslim ve iletilen iletiler için dikkat edilmesi gereken bazı noktalar şunlardır:

- İletilen alıcı, Dinamik Teslim seçeneğini kullanan Kasa Ekler ilkesiyle korunuyorsa, alıcı uyumlu dosyaların önizlemesini görüntüleme özelliğiyle yer tutucuyu görür.
- İletilen alıcı Kasa Ekleri ilkesiyle korunmuyorsa, ileti ve ekler Kasa Ek tarama veya ek yer tutucuları olmadan teslim edilir.

Dinamik Teslim'in iletilerdeki ekleri değiştiremediği senaryolar vardır. Bu senaryolar şunlardır:

- Ortak klasörlerdeki iletiler.
- Özel kurallar kullanılarak kullanıcının posta kutusundan dışarı ve sonra geri yönlendirilen iletiler.
- Bulut posta kutularından arşiv klasörleri de dahil olmak üzere diğer konumlara taşınan (otomatik veya el ile) iletiler.
- Gelen kutusu kuralları, iletiyi Gelen Kutusu'nun dışına farklı bir klasöre taşır.
- İletiler silindi.
- Kullanıcının posta kutusu arama klasörü hata durumunda.
- Exclaimer'ın etkinleştirildiği kuruluşları Exchange Online. Bu sorunu çözmek için bkz [. KB4014438](https://support.microsoft.com/help/4014438).
- [S/MIME)](/exchange/security-and-compliance/smime-exo/smime-exo) şifrelenmiş iletiler.
- Dinamik Teslim eylemini Kasa Ekler ilkesinde yapılandırdıysanız, ancak alıcı Dinamik Teslim'i desteklemez (örneğin, alıcı şirket içi Exchange kuruluşundaki bir posta kutusudur). Ancak[, Office 365 için Microsoft Defender Kasa Bağlantıları](set-up-safe-links-policies.md) URL'ler içeren Office dosya eklerini tarar ([Kasa Bağlantıları için genel ayarların](configure-global-settings-for-safe-links.md) nasıl yapılandırıldığına bağlı olarak).

## <a name="submitting-files-for-malware-analysis"></a>Kötü amaçlı yazılım analizi için dosya gönderme

- Analiz için Microsoft'a göndermek istediğiniz bir dosya alırsanız, bkz. [Analiz için Microsoft'a kötü amaçlı yazılım ve kötü amaçlı olmayan yazılım gönderme](submitting-malware-and-non-malware-to-microsoft-for-analysis.md).
- Analiz için Microsoft'a göndermek istediğiniz bir e-posta iletisi (ekli veya eksiz) alırsanız bkz. [İletileri ve dosyaları Microsoft'a bildirme](report-junk-email-messages-to-microsoft.md).
