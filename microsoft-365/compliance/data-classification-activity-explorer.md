---
title: Etkinlik gezginiyle çalışmaya başlama
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Etkinlik gezgini, kullanıcıların etiketli içeriğinize gerçekleştir yaptıkları eylemleri görmenizi ve filtrelemenizi sağlar.
ms.openlocfilehash: 93cd3910a79b136d95ba46fa79940d379340cf75
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019512"
---
# <a name="get-started-with-activity-explorer"></a>Etkinlik gezginiyle çalışmaya başlama

Veri [sınıflandırması genel bakış](data-classification-overview.md) [ve içerik gezgini](data-classification-content-explorer.md) sekmeleri, nelerin keşfedilen, etiketlenmiş ve bu içeriğin nerede bulunduğuyla ilgili görünürlük sağlar. Etkinlik gezgini, etiketli içeriğinize neler olduğunu izlemenizi sağlayarak bu işlev paketini yuvarlar. Etkinlik gezgini, etiketli içeriğinize etkinliklerin geçmiş bir görünümünü sağlar. Etkinlik bilgileri en son Microsoft 365 denetim günlüklerinden toplanır, dönüştürüler ve Etkinlik gezgini kullanıcı arabiriminde kullanılabilir olarak yapılır. Etkinlik gezgini 30 günlük verilere kadar raporlar.

![yer tutucu ekran görüntüsü genel bakış etkinlik gezgini.](../media/data-classification-activity-explorer-1.png)

30'dan fazla farklı filtre kullanılabilir, bazıları:

- Tarih aralığı
- Etkinlik türü
- Konum
- Kullanıcı
- Duyarlılık etiketi
- Bekletme etiketi
- Dosya yolu
- DLP ilkesi



## <a name="prerequisites"></a>Önkoşullar

Veri sınıflandırmaya erişen ve kullanan her hesaba, şu aboneliklerden birinin lisansı atanmış olması gerekir:

- Microsoft 365 (E5)
- Office 365 (E5)
- Gelişmiş Uyumluluk (E5) eklenti
- Gelişmiş Tehdit zekası (E5) eklentisi
- Microsoft 365 E5/A5 Bilgi Koruması & Yönetimi
- Microsoft 365 E5/A5 Uyumluluğu

### <a name="permissions"></a>İzinler

Bu rol gruplarından herhangi bir hesaba açıkça üye atanması veya role açıkça atanması gerekir.

### <a name="roles-and-role-groups-in-preview"></a>Önizlemede Roller ve Rol Grupları

Önizlemede, erişim denetimlerinize ince ayar yapmak için test etmek için sınayabilirsiniz roller ve rol grupları vardır.

İşte önizlemede olan Microsoft Bilgi Koruması (MIP) rollerinin listesi. Bu roller hakkında daha fazla bilgi edinmek [için Güvenlik ve Uyumluluk Merkezi'& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Bilgi Koruması Yöneticisi
- Bilgi Koruma Analisti
- Bilgi Koruma Koruma Koruma Koruması
- Bilgi Koruma Okuyucusu

Önizlemede olan MIP rol gruplarının listesi burada ve ve şekildedir. Bu gruplar hakkında daha fazla bilgi [edinmek için Güvenlik ve Uyumluluk Merkezi'nde & bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center).

- Bilgi Koruması
- Bilgi Koruması Yöneticileri
- Bilgi Koruma Analistleri
- Bilgi Koruma Koruma KorumaLarı
- Bilgi Koruma Okuyucuları

<!--
> [!IMPORTANT]
> Access to Activity explorer via the Security reader or Device Management role groups or other has been removed-->

**Microsoft 365 grupları**

- Genel yönetici
- Uyumluluk yöneticisi
- Güvenlik yöneticisi
- Uyumluluk veri yöneticisi

**Microsoft 365 rollerini atama**

- Uyumluluk yöneticisi
- Güvenlik yöneticisi
- Güvenlik Okuyucu

## <a name="activity-types"></a>Etkinlik türleri

Etkinlik gezgini, birden çok etkinlik kaynağında denetim günlüklerinden etkinlik bilgilerini toplar. Etkinliğin etkinlik gezgininde hangi etikete ekli olduğu hakkında daha ayrıntılı bilgi için bkz. [Etkinlik gezgininde kullanılabilir etiketleme olayları](data-classification-activity-explorer-available-events.md).

 Office yerel uygulamaları, Azure Information  Protection eklenti, SharePoint Online, Exchange Online (yalnızca duyarlılık etiketleri) ve diğer uygulamalardan Duyarlılık etiketi etkinlikleri ve OneDrive. Bazı örnekler:

- Etiket uygulandı
- Etiket değişti (yükseltildi, indirildi veya kaldırıldı)
- Otomatik etiket benzetim
- Dosya okuma

**Azure Information Protection (AIP) tarayıcı ve AIP istemcileri**

- Koruma uygulandı
- Koruma değiştirildi
- Koruma kaldırıldı
- Bulunan dosyalar

Etkinlik gezgini ayrıca **, DLP** ilkesi Exchange Online, SharePoint Online, OneDrive, Teams Sohbet ve Kanal (önizleme), şirket içi SharePoint klasörleri ve kitaplıkları ile şirket içi dosya paylaşımlarından ve Windows 10 **cihazlarından Uç nokta veri kaybı önleme (DLP)**. Bu cihazlardan bazı Windows 10 olay dosya olarak verilmiştir:

- Silmeler
- Oluşturmalar
- Panoya kopyalandı
- Değiştirme Tarihi
- Oku
- Yazdırıldı
- Yeniden adlandırıldı
- Ağ paylaşımına kopyalandı
- Izin verilmeyen uygulama tarafından erişilir 

Hassas etiketli içeriğiniz ile hangi eylemlerin gerçekleştiriliyor olduğunu anlamak, veri kaybı önleme ilkeleri gibi geçerli denetimlerin etkin olup olmadığını görmenizi sağlar.[](dlp-learn-about-dlp.md) Böyle bir `highly confidential` `general`durumla karşılaşamazsanız veya etiketlenmiş ve indirilen çok sayıda öğe gibi beklenmeyen bir şey keşfedersanız, çeşitli ilkelerinizi yönetebilir ve beklenmedik davranışı kısıtlamak için yeni işlemler gerçekleştirebilirsiniz.

> [!NOTE]
> Etkinlik gezgini şu anda herhangi bir etkinlik için bekletme Exchange Online.

## <a name="see-also"></a>Ayrıca bkz.

- [Duyarlılık etiketleri hakkında bilgi edinin](sensitivity-labels.md)
- [Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi](retention.md)
- [Hassas bilgi türleri hakkında bilgi](sensitive-information-type-learn-about.md)
- [Veri sınıflandırması hakkında bilgi](data-classification-overview.md)
