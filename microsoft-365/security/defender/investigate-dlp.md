---
title: Microsoft 365 Defender ile veri kaybı olaylarını araştırma
description: Microsoft 365 Defender veri kaybını araştırma.
keywords: Veri Kaybı Önleme, olaylar, uyarılar, araştırma, analiz etme, yanıt, bağıntı, saldırı, makineler, cihazlar, kullanıcılar, kimlikler, kimlik, posta kutusu, e-posta, 365, microsoft, m365
f1.keywords:
- NOCSH
ms.prod: m365-security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
ms.technology: m365d
ms.openlocfilehash: 6111bf9e2a44d079bfae19d9aa0c34f7b125ff08
ms.sourcegitcommit: f181e110cdb983788a86f30d5bb018e53c83e64d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66057897"
---
# <a name="investigate-data-loss-incidents-with-microsoft-365-defender"></a>Microsoft 365 Defender ile veri kaybı olaylarını araştırma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- Microsoft 365 Defender

Microsoft Purview Veri Kaybı Önleme (DLP) olayları artık Microsoft 365 Defender portalında yönetilebilir. DLP olaylarını ve güvenlik olaylarını, <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalın</a> hızlı başlatılmasıyla ilgili **Olaylar & uyarılar** \> **Güvenlik olaylarıyla** birlikte yönetebilirsiniz. Bu sayfadan şunları yapabilirsiniz:

- Microsoft 365 Defender olay kuyruğundaki olaylar altında gruplandırılmış tüm DLP uyarılarınızı görüntüleyin.
- Tek bir olay altında akıllı çözümler arası (DLP-MDE, DLP-MDO) ve çözüm içi (DLP-DLP) bağıntılı uyarıları görüntüleyin.
- Gelişmiş Avcılık kapsamında güvenlikle birlikte uyumluluk günlüklerini arayın.
- Kullanıcı, dosya ve cihazda yerinde yönetici düzeltme eylemleri. 
- Özel etiketleri DLP olaylarıyla ilişkilendirin ve bunlara göre filtreleyin.
- Birleştirilmiş olay kuyruğundaki DLP ilkesi adına, etiketine, Tarihe, hizmet kaynağına, olay durumuna ve kullanıcıya göre filtreleyin. 

DLP olaylarının yanı sıra olayları ve kanıtları araştırma ve düzeltme amacıyla Microsoft Sentinel'e çekmek için Microsoft Sentinel'deki Microsoft 365 Defender bağlayıcısını da kullanabilirsiniz.

## <a name="licensing-requirements"></a>Lisans gereksinimleri

Microsoft 365 Defender portalında Microsoft Purview Veri Kaybı Önleme olaylarını araştırmak için aşağıdaki aboneliklerden birinin lisansına sahip olmanız gerekir: 

- Microsoft Office 365 E5/A5
- Microsoft 365 E5/A5
- Microsoft 365 E5/A5 Uyumluluğu
- Microsoft 365 E5/A5 Güvenliği
- Microsoft 365 E5/A5 Information Protection ve İdare

## <a name="dlp-investigation-experience-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında DLP araştırma deneyimi

Başlamadan önce<a href="https://purview.microsoft.com" target="_blank">, Microsoft Purview uyumluluk portalında</a> [tüm DLP ilkeleriniz için uyarıları açın](/microsoft-365/compliance/dlp-configure-view-alerts-policies#alert-configuration-experience).

1. Microsoft 365 Defender portalına gidin ve sol taraftaki gezinti **menüsünden Olaylar'ı** seçerek olaylar sayfasını açın.

2. Sağ üst kısımdaki **Filtreler'i** seçin ve DLP uyarılarıyla tüm olayları görüntülemek için **Hizmet Kaynağı : Veri Kaybı Önleme'yi** seçin.

3. İlgilendiğiniz uyarıların ve olayların DLP ilkesi adını arayın.

4. Olay özeti sayfasını görüntülemek için kuyruktan olayı seçin. Benzer şekilde, DLP uyarı sayfasını görüntülemek için uyarıyı seçin.

5. **İlke ve uyarıda** algılanan hassas bilgi türleri hakkındaki ayrıntılar için Uyarı hikayesini görüntüleyin. Kullanıcı etkinliği ayrıntılarını görmek için **İlgili Olaylar** bölümünde olayı seçin.

6. Gerekli izne sahipseniz **, Hassas bilgi türleri** sekmesinde eşleşen hassas içeriği ve **Kaynak** sekmesindeki dosya içeriğini görüntüleyin ( <a href="/microsoft-365/compliance/dlp-alerts-dashboard-get-started#roles" target="_blank">Ayrıntılara buradan</a> bakın).

7. Araştırmanız için kullanıcı, dosya ve site konumlarının denetim günlüklerinde arama yapmak için Gelişmiş Avcılık'ı da kullanabilirsiniz. **CloudAppEvents** tablosu Sharepoint, OneDrive, Exchange ve Cihazlar gibi tüm konumlardaki tüm denetim günlüklerini içerir.

8. Ayrıca **Eylemler** \> E-postayı indir'i seçerek **de e-postayı** indirebilirsiniz. 

9. SPO veya ODB sitelerdeki dosyalarda düzeltme eylemleri için şunlar gibi eylemleri görebilirsiniz:

    - Bekletme etiketi uygulama
    - Duyarlılık etiketi uygulama
    - Dosyanın paylaşımını kaldırma
    - Silme

   Düzeltme eylemleri için uyarı sayfasının üst kısmındaki **Kullanıcı kartını** seçerek kullanıcı ayrıntılarını açın.

   Cihazlar DLP uyarıları için uyarı sayfasının üst kısmındaki cihaz kartını seçerek cihaz ayrıntılarını görüntüleyin ve cihazda düzeltme eylemleri gerçekleştirin.

10. Olay etiketleri eklemek, olayı atamak veya çözmek için olay özeti sayfasına gidin ve **Olayı Yönet'i** seçin.

## <a name="dlp-investigation-experience-in-microsoft-sentinel"></a>Microsoft Sentinel'de DLP araştırma deneyimi

Bağıntınızı, algılamanızı ve araştırmanızı diğer veri kaynakları arasında genişletmek ve Sentinel'in yerel SOAR özelliklerini kullanarak otomatik düzenleme akışlarınızı genişletmek için tüm DLP olaylarını Sentinel'e aktarmak için Microsoft Sentinel'deki Microsoft 365 Defender bağlayıcısını kullanabilirsiniz. 

1. DLP olayları ve uyarıları da dahil olmak üzere tüm olayları Sentinel'e aktarmak için Microsoft 365 Defender'dan Microsoft Sentinel'e Bağlan verileri hakkındaki yönergeleri izleyin. Olay bağlayıcısını etkinleştirerek `CloudAppEvents` tüm O365 denetim günlüklerini Sentinel'e çekin.

   Yukarıdaki bağlayıcı ayarlandıktan sonra DLP olaylarınızı Sentinel'de görebilmeniz gerekir.

2. Uyarı sayfasını görüntülemek için **Uyarılar'ı** seçin.

3. Uyarıya katkıda bulunan tüm kullanıcı etkinliklerini almak üzere **CloudAppEvents** tablosunu sorgulamak için **AlertType**, **startTime** ve **endTime** kullanabilirsiniz. Temel alınan etkinlikleri tanımlamak için bu sorguyu kullanın:

```kusto
let Alert = SecurityAlert 
| where TimeGenerated  > ago(30d) 
| where SystemAlertId == "" // insert the systemAlertID here 
CloudAppEvents 
| extend correlationId = parse_json(tostring(RawEventData.Data)).cid
| join kind=inner Alert on $left.correlationId == $right.AlertType 
| where RawEventData.CreationTime > StartTime and RawEventData.CreationTime < EndTime
```

## <a name="related-articles"></a>İlgili makaleler

- [Olaylara genel bakış](incidents-overview.md)
- [Olaylara öncelik belirleyin](incident-queue.md)
- [Olayları yönetin](manage-incidents.md)
