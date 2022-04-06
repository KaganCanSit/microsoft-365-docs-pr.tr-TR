---
title: Microsoft 365 Defender dilimi ayarlarını değiştirme
description: Saat dilimi ayarlarını yapılandırmak ve lisans bilgilerini Microsoft 365 Defender buradaki bilgileri kullanın.
keywords: settings, Microsoft Defender, siber güvenlik tehdit İstihbaratı, Uç Nokta için Microsoft Defender, saat dilimi, utc, yerel saat, lisans
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: adf693bded45dcb44abd8d1e7892e5edc7b65585
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467169"
---
# <a name="microsoft-365-defender-time-zone-settings"></a>Microsoft 365 Defender dilimi ayarlarını değiştirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)


> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-settings-abovefoldlink)

Saat **dilimini yapılandırmak** ve lisans bilgilerini görüntülemek için Saat dilimi menüsünü kullanın.
:::image type="content" source="images/atp-time-zone.png" alt-text="Saat dilimi ayarları-1" lightbox="images/atp-time-zone.png":::

## <a name="time-zone-settings"></a>Saat dilimi ayarları

Zaman, algılanması ve gerçek siber saldırıların değerlendirmesi ve çözümlemesi açısından önemlidir.

Siberforensik soruşturmalar genellikle olay dizisini bir araya parça parça etmek için zaman damgalarını güvenmektedir. Sisteminizin doğru saat dilimi ayarlarını yansıtması önemlidir.

Uç Nokta için Microsoft Defender Saat (UTC) veya yerel saat Eşgüdümli Evrensel Saat'i  görüntülemeyi sağlar.

Geçerli saat dilimi ayarınız Saat dilimi Uç Nokta için Microsoft Defender görüntülenir. Saat dilimi menüsünde görüntülenen saat dilimini **değiştirebilirsiniz** .

:::image type="content" source="images/atp-time-zone-menu.png" alt-text="Saat dilimi ayarları-2" lightbox="images/atp-time-zone-menu.png":::

### <a name="utc-time-zone"></a>UTC saat dilimi

Uç Nokta için Microsoft Defender varsayılan olarak UTC saati kullanır.

Saat Uç Nokta için Microsoft Defender UTC olarak ayarsanız tüm kullanıcılar için UTC'de tüm sistem zaman damgası (uyarılar, olaylar ve diğerleri) görüntülenir. Bu, güvenlik analistlerin dünyanın her yerinde farklı konumlarda çalışarak olayları araştırırken aynı zaman damgalarını kullanmalarına yardımcı olabilir.

### <a name="local-time-zone"></a>Yerel saat dilimi

Yerel saat dilimi ayarlarını Uç Nokta için Microsoft Defender saat dilimi ayarlarını kullanmayı tercih edebilirsiniz. Tüm uyarılar ve olaylar yerel saat diliminiz kullanılarak görüntülenir.

Yerel saat dilimi cihazınızın bölgesel ayarlarından alınır. Bölgesel ayarlarınızı değiştirirsiniz, saat Uç Nokta için Microsoft Defender saat dilimi de değişir. Bu ayarın seçimi, aynı anda görüntülenen zaman damgasının Uç Nokta için Microsoft Defender tüm kullanıcılar için yerel saatle Uç Nokta için Microsoft Defender anlamına gelir. Farklı küresel konumlarda yer alan analistler, artık Uç Nokta için Microsoft Defender ayarlarına göre önemli uyarıları görebilirler.

Analistler tek konumda yer alıyorsa, yerel saati seçme yararlı olabilir. Bu durumda, örneğin yerel kullanıcı şüpheli bir e-posta bağlantısına tıklamışsa, etkinlikleri yerel saatle daha kolay bir şekilde ilişkili yapmak daha kolay olabilir.

### <a name="set-the-time-zone"></a>Saat dilimini ayarlama

Saat Uç Nokta için Microsoft Defender saat dilimi varsayılan olarak UTC'ye ayarlanır. Saat dilimini ayar her görünüm için saat Uç Nokta için Microsoft Defender değiştirir.

Saat dilimini ayarlamak için:

1. Saat dilimi **menüsüne** tıklayın.
   :::image type="content" source="images/atp-time-zone.png" alt-text="Saat dilimi ayarları-3" lightbox="images/atp-time-zone.png":::
1. Saat Dilimi **UTC göstergesini** seçin.
1. Saat **Dilimi UTC'yi** veya yerel saat diliminizi (örneğin-7:00) seçin.

### <a name="regional-settings"></a>Bölgesel ayarlar

İnternet'e farklı tarih biçimleri Uç Nokta için Microsoft Defender Internet Explorer (IE) ve Diğer (Edge) için bölgesel Microsoft Edge kullanın. Google Chrome gibi başka bir tarayıcı kullanıyorsanız, bu tarayıcının tarih ve saat ayarlarını değiştirmek için gerekli adımları izleyin. 

#### <a name="internet-explorer-ie-and-microsoft-edge"></a>Internet Explorer (IE) ve Microsoft Edge

IE ve Microsoft Edge Denetim Masası'nda Saat, Dil ve Bölge seçeneğinde **yapılandırılan** Bölge ayarlarını kullanır. 

#### <a name="known-issues-with-regional-formats"></a>Bölgesel biçimlerle ilgili bilinen sorunlar

##### <a name="date-and-time-formats"></a>Tarih ve saat biçimleri

Saat ve tarih biçimleriyle ilgili bilinen bazı sorunlar vardır. Bölgesel ayarlarınızı desteklenen biçimler dışında bir şekilde yapılandırdısanız, portal ayarlarınızı doğru şekilde yansıtmamış olabilir.

Aşağıdaki tarih ve saat biçimleri desteklemektedir:

- Tarih biçimi AA/uz/yyyy
- Tarih biçimi d/AA/yyyy
- Saat biçimi ss:dd:ss (12 saat biçimi)

Aşağıdaki tarih ve saat biçimleri şu anda desteklenmiyor:

- Tarih biçimi yyyy-AA-2
- Tarih biçimi d-AAA-yy
- Tarih biçimi d/AA/yy
- Tarih biçimi AA/d/yy
- yy ile tarih biçimi. Yalnızca yyyy gösterir.
- Saat biçimi SS:dd:ss (24 saat biçimi)

##### <a name="decimal-symbol-used-in-numbers"></a>Sayılarda kullanılan ondalık simgesi

Bölge ayarları'nın Sayı biçimi ayarlarında virgül seçili olsa bile, kullanılan **ondalık** simgesi her zaman **nokta olarak gösterilir** . Örneğin, 15,5K 15,5K olarak görüntülenir.
