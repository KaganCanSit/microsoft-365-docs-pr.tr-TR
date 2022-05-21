---
title: Göstergeleri yönetin
ms.reviewer: ''
description: Varlıkların algılanmasını, önlenmesini ve dışlanmasını tanımlayan dosya karması, IP adresi, URL'ler veya etki alanları için göstergeleri yönetin.
keywords: import, indicator, list, ioc, csv, manage, allowed, blocked, block, clean, malicious, file hash, ip address, urls, domain
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
ms.openlocfilehash: 72509f7480d54819fc29f40bab0e2bf65dcd8660
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65622023"
---
# <a name="manage-indicators"></a>Göstergeleri yönetin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

1. Gezinti bölmesinde uç **nokta göstergelerini** \> **Ayarlar** \> seçin (**Kurallar'ın** altında).

2. Yönetmek istediğiniz varlık türünün sekmesini seçin.

3. Göstergenin ayrıntılarını güncelleştirin ve varlığı listeden kaldırmak istiyorsanız **Kaydet'e** tıklayın veya **Sil** düğmesine tıklayın.

## <a name="import-a-list-of-iocs"></a>IoCs listesini içeri aktarma

Ayrıca göstergelerin özniteliklerini, gerçekleştirilecek eylemi ve diğer ayrıntıları tanımlayan bir CSV dosyasını karşıya yüklemeyi de seçebilirsiniz.

Desteklenen sütun özniteliklerini öğrenmek için örnek CSV dosyasını indirin.

1. Gezinti bölmesinde uç **nokta göstergelerini** \> **Ayarlar** \> seçin (**Kurallar'ın** altında).

2. Göstergelerini içeri aktarmak istediğiniz varlık türünün sekmesini seçin.

3. **Dosya** **seç'i içeri aktar'ı** \> seçin.

4. **İçeri Aktar'ı** seçin. İçeri aktarmak istediğiniz tüm dosyalar için bunu yapın.

5. **Bitti'yi** seçin.

> [!NOTE]
> Her toplu iş için yalnızca 500 gösterge karşıya yüklenebilir.

Aşağıdaki tabloda desteklenen parametreler gösterilmektedir.

Parametre|Tür|Açıklama
:---|:---|:---
indicatorType|Enum|Göstergenin türü. Olası değerler şunlardır: "FileSha1", "FileSha256", "IpAddress", "DomainName" ve "Url". **Gerekli**
indicatorValue|Dize|[Gösterge](ti-indicator.md) varlığının kimliği. **Gerekli**
Eylem|Enum|Gösterge kuruluşta bulunursa gerçekleştirilecek eylem. Olası değerler şunlardır: "Alert", "AlertAndBlock" ve "Allowed". **Gerekli**
Başlık|Dize|Gösterge uyarı başlığı. **Gerekli**
Açıklama|Dize| Göstergenin açıklaması. **Gerekli**
expirationTime|Datetimeoffset|Göstergenin YYYY-AA-GGTHH:AA:SS.0Z biçiminde sona erme zamanı. Süre sonu süresi geçtiğinde ve süre sonu sırasında ne olursa olsun saniye (SS) değerinde gerçekleşirse gösterge silinir. **İsteğe bağlı**
Önem|Enum|Göstergenin önem derecesi. Olası değerler şunlardır: "Bilgilendirici", "Düşük", "Orta" ve "Yüksek". **İsteğe bağlı**
recommendedActions|Dize|TI göstergesi uyarısı önerilen eylemler. **İsteğe bağlı**
rbacGroupNames|Dize|Göstergenin uygulanacağı RBAC grup adlarının virgülle ayrılmış listesi. **İsteğe bağlı**
Kategori|Dize|Uyarı kategorisi. Örnekler şunlardır: Yürütme ve kimlik bilgileri erişimi. **İsteğe bağlı**
mitretechniques|Dize|MITRE teknikleri kod/kimlik (virgülle ayrılmış). Daha fazla bilgi için bkz. [Enterprise taktikleri](https://attack.mitre.org/tactics/enterprise/). **Isteğe bağlı** MITRE tekniğinde kategoriye değer eklemeniz önerilir.
GenerateAlert|Dize|Uyarının oluşturulup oluşturulmayacağı. Olası Değerler şunlardır: True veya False. **İsteğe bağlı**

> [!NOTE]
> IP adresleri için sınıfsız Inter-Domain Yönlendirme (CIDR) gösterimi desteklenmez.
Daha fazla bilgi için bkz. [Uç Nokta için Microsoft Defender uyarı kategorileri artık MITRE ATT&CK!](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/microsoft-defender-atp-alert-categories-are-now-aligned-with/ba-p/732748).

Uç Nokta için Microsoft Defender'nin güvenlik ihlal göstergeleri (ICS) eklemek ve yönetmek için nasıl birden çok yol sağladığını öğrenmek için bu videoyu izleyin. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4qLVw]

## <a name="see-also"></a>Ayrıca bkz.

- [Göstergeleri oluşturun](manage-indicators.md)
- [Dosyalar için göstergeler oluşturun](indicator-file.md)
- [URL/etki alanı ve IP’ler için göstergeler oluşturun](indicator-ip-domain.md)
- [Sertifikaları temel alan göstergeler oluşturma](indicator-certificates.md)
