---
title: Göstergeleri yönetme
ms.reviewer: ''
description: Bir dosya karma, IP adresi, URL'ler veya varlıkları algılama, önleme ve dışlama alanlarını tanımlayan etki alanları için göstergeleri yönetin.
keywords: import, indicator, list, ioc, csv, manage, allowed, block, block, clean, malicious, file hash, ip address, urls, domain
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
ms.openlocfilehash: 2f66106dd39b9cd1f590148addfdd2cae89748c6
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032468"
---
# <a name="manage-indicators"></a>Göstergeleri yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://www.microsoft.com/WindowsForBusiness/windows-atp?ocid=docs-wdatp-automationexclusionlist-abovefoldlink)

1. Gezinti bölmesinde, Uç Noktaları **Ayarlar** \> **Seçin** \> (**Kurallar'ın** **altında**).

2. Yönetmek istediğiniz varlık türünün sekmesini seçin.

3. Göstergenin ayrıntılarını güncelleştirin ve **ardından varlığı** **listeden kaldırmak için** Kaydet'e veya Sil düğmesine tıklayın.

## <a name="import-a-list-of-iocs"></a>IoCs listesini içeri aktarma

Gösterge özniteliklerini, alınacak eylemi ve diğer ayrıntıları tanımlayan bir CSV dosyası da karşıya yükleyebilirsiniz.

Desteklenen sütun özniteliklerini bilmek için örnek CSV'i indirin.

1. Gezinti bölmesinde, Uç Noktaları **Ayarlar** \> **Seçin** \> (**Kurallar'ın** **altında**).

2. Göstergelerini içeri aktarmayı istediğiniz varlık türünün sekmesini seçin.

3. İçeri Aktar **Dosya** **seç'i**\> seçin.

4. İçeri **Aktar'ı seçin**. İçeri aktarma işlemi yapmak tüm dosyalar için bunu kullanın.

5. **Bitti'yi seçin**.

> [!NOTE]
> Her toplu işlem için yalnızca 500 gösterge karşıya yükleyebilir.

Aşağıdaki tabloda desteklenen parametreler gösterir.

Parametre|Tür|Açıklama
:---|:---|:---
indicatorType|Enum|Göstergenin türü. Olası değerler şöyledir: "FileSha1", "FileSha256", "IpAddress", "DomainName" ve "Url". **Gerekli**
indicatorValue|Dize|Gösterge varlık [kimliği](ti-indicator.md) . **Gerekli**
eylem|Enum|Gösterge kuruluşta keşfedilecekse, alınacak eylem. Olası değerler: "Uyarı", "AlertAndBlock" ve "İzin Verildi". **Gerekli**
başlık|Dize|Gösterge uyarısı başlığı. **Gerekli**
açıklama|Dize| Göstergenin açıklaması. **Gerekli**
expirationTime|DateTimeOffset|Aşağıdaki biçimdeki göstergenin sona erme zamanı YYYY-AA-THH:DD:SS.0Z. Sona erme zamanı geçtikten sonra gösterge silinir ve sona erme zamanında olan her şey saniye (SS) değerinde gerçekleşir. **İsteğe bağlı**
önem derecesi|Enum|Göstergenin önem derecesidir. Olası değerler şöyledir: "Bilgilendirme", "Düşük", "Orta" ve "Yüksek". **İsteğe bağlı**
recommendedActions|Dize|TI göstergesi uyarısı önerilen eylemler. **İsteğe bağlı**
rbacGroupNames|Dize|Göstergenin uygulanabilecek RBAC grup adlarının virgülle ayrılmış listesi. **İsteğe bağlı**
kategori|Dize|Uyarının kategorisi. Örnekler: Yürütme ve kimlik bilgileri erişimi. **İsteğe bağlı**
mitretechniques|Dize|MİTRE tekniklerini kod/kimlik (virgülle ayrılmış). Daha fazla bilgi için bkz[. Enterprise bilgi.](https://attack.mitre.org/tactics/enterprise/) **İsteğe bağlı** MITRE tekniğini kullanarak kategoriye bir değer eklemeniz önerilir.
GenerateAlert|Dize|Uyarının oluşturulıp oluşturulmay(ya da oluşturulmay) olup olmadığı. Olası Değerler şöyledir: Doğru veya Yanlış. **İsteğe bağlı**



> [!NOTE]
> IP Inter-Domain sınıfsız Yönlendirme (CIDR) yönlendirmesi desteklenmiyor.
Daha fazla bilgi için bkz. [Uç nokta uyarı kategorileri için Microsoft Defender artık MITRE ATT&CK! ile hizalandı](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/microsoft-defender-atp-alert-categories-are-now-aligned-with/ba-p/732748).

## <a name="see-also"></a>Ayrıca bkz.

- [Gösterge oluşturma](manage-indicators.md)
- [Dosyalar için göstergeler oluşturma](indicator-file.md)
- [URL'ler ve URL'ler/etki alanları için göstergeler oluşturma](indicator-ip-domain.md)
- [Sertifikalara dayalı göstergeler oluşturma](indicator-certificates.md)
