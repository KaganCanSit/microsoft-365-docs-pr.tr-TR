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
ms.openlocfilehash: 4353bbfc0ce11c4a767ca599ecb23a1ab4f77a56
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010793"
---
# <a name="microsoft-365-defender-time-zone-settings"></a>Microsoft 365 Defender dilimi ayarlarını değiştirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)


> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-settings-abovefoldlink)

Saat dilimi **menüsü Saat** dilimi ![ayarları simgesini kullanın1.](images/atp-time-zone.png) saat dilimini yapılandırarak lisans bilgilerini görüntülemeyi sağlar.

## <a name="time-zone-settings"></a>Saat dilimi ayarları

Zaman, algılanması ve gerçek siber saldırıların değerlendirmesi ve çözümlemesi açısından önemlidir.

Siberforensik soruşturmalar genellikle olay dizisini bir araya parça parça etmek için zaman damgalarını güvenmektedir. Sisteminizin doğru saat dilimi ayarlarını yansıtması önemlidir.

Uç Nokta için Microsoft Defender Eşgüdümli Evrensel Saat (UTC) veya yerel saati  görüntüleniyor olabilir.

Geçerli saat dilimi ayarınız Microsoft Defender ayarlarında gösterilir. Görüntülenen saat dilimini, Saat dilimi menüsündeki Saat **Dilimi'nin** altında **Ayarlar > değiştirebilirsiniz**.

### <a name="utc-time-zone"></a>UTC saat dilimi

Uç Nokta için Microsoft Defender varsayılan olarak UTC saati kullanır.

Uç nokta saat dilimi için Microsoft Defender'ı UTC olarak ayar her kullanıcı için tüm sistem zaman damgasını (uyarılar, olaylar ve diğerleri) UTC'de görüntüler. Bu, güvenlik analistlerin dünyanın her yerinde farklı konumlarda çalışarak olayları araştırırken aynı zaman damgalarını kullanmalarına yardımcı olabilir.

### <a name="local-time-zone"></a>Yerel saat dilimi

Uç nokta için Microsoft Defender'ın yerel saat dilimi ayarlarını kullanmalarını seçebilirsiniz. Tüm uyarılar ve olaylar yerel saat diliminiz kullanılarak görüntülenir.

Yerel saat dilimi cihazınızın bölgesel ayarlarından alınır. Bölgesel ayarlarınızı değiştirirsiniz, Uç nokta saat dilimi için Microsoft Defender da değişir. Bu ayarın seçimi, Uç Nokta için Microsoft Defender'da görüntülenen zaman damgasının tüm Uç Nokta kullanıcıları için Microsoft Defender'ın yerel saatle hizalanması anlamına gelir. Farklı genel konumlarda yer alan analistler artık bölgesel ayarlarına göre Uç Nokta uyarıları için Microsoft Defender'ı görebilirler.

Analistler tek konumda yer alıyorsa, yerel saati seçme yararlı olabilir. Bu durumda, örneğin yerel kullanıcı şüpheli bir e-posta bağlantısına tıklamışsa, etkinlikleri yerel saatle daha kolay bir şekilde ilişkili yapmak daha kolay olabilir.

### <a name="set-the-time-zone"></a>Saat dilimini ayarlama

Uç nokta saat dilimi için Microsoft Defender varsayılan olarak UTC'ye ayarlanır. Saat dilimini ayarlama, uç nokta görünümleri için tüm Microsoft Defender'ın saatlerini de değiştirir.

Saat dilimini ayarlamak için:

1. Portal **Saat Ayarlar** simgesinde [Microsoft 365 Defender menüsüne](https://security.microsoft.com/) ![tıklayın.](images/atp-time-zone.png)
2. Güvenlik **merkezi'ne seçin**.
3. Saat **Dilimi'ne** seçin ve saat dilimini UTC veya yerel saat diliminiz olarak ayarlayın.

### <a name="regional-settings"></a>Bölgesel ayarlar

Uç nokta için Microsoft Defender'a farklı tarih biçimleri uygulamak için Internet Explorer (IE) ve Uç Nokta (Edge) için bölgesel Microsoft Edge kullanın. Google Chrome gibi başka bir tarayıcı kullanıyorsanız, bu tarayıcının tarih ve saat ayarlarını değiştirmek için gerekli adımları izleyin. 

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
