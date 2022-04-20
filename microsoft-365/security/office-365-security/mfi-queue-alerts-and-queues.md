---
title: Posta akışı panosundaki kuyruklar içgörüleri
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.custom: ''
ms.localizationpriority: medium
ms.assetid: 37640c80-ce6f-47e2-afd1-bc1d3c50e637
description: Yöneticiler, şirket içi veya iş ortağı kuruluşlarına giden bağlayıcılar üzerinden yapılan başarısız posta akışını izlemek için Güvenlik & Uyumluluk Merkezi'ndeki Posta akışı panosundaki Kuyruklar pencere öğesini kullanmayı öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 146ce26c32f1ff80a451b85fd343990db547a131
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64972661"
---
# <a name="queues-insight-in-the-security--compliance-center"></a>Güvenlik & Uyumluluk Merkezi'ndeki kuyruklar içgörüleri

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Bağlayıcılar kullanılarak kuruluşunuzdan şirket içi veya iş ortağı e-posta sunucularınıza ileti gönderilemediyse, iletiler Microsoft 365 kuyruğa alınır. Bu koşula neden olan yaygın örnekler şunlardır:

- Bağlayıcı yanlış yapılandırılmış.
- Şirket içi ortamınızda ağ veya güvenlik duvarı değişiklikleri yapıldı.

Microsoft 365 24 saat boyunca teslime yeniden denemeye devam edecektir. 24 saat sonra iletilerin süresi dolar ve teslim edilemeyen raporlarda (NDR veya geri dönen iletiler olarak da bilinir) gönderenlere döndürülür.

Kuyruğa alınan e-posta birimi önceden tanımlanmış eşiği aşarsa (varsayılan değer 200 iletidir), bilgiler aşağıdaki konumlarda kullanılabilir:

- [Güvenlik & Uyumluluk Merkezi'ndeki](https://protection.office.com) [Posta akışı panosundaki](mail-flow-insights-v2.md) **Kuyruklar** içgörüleri. Daha fazla bilgi için bu makalenin [Posta akışı panosu bölümündeki Kuyruklar içgörülerine](#queues-insight-in-the-mail-flow-dashboard) bakın.

- [Güvenlik & Uyumluluk Merkezi'ndeki](https://protection.office.com) Uyarılar panosunda (Uyarılar **Panosu** veya <https://protection.office.com/alertsdashboard>) **bir** **uyarı** \> görüntülenir.

  :::image type="content" source="../../media/mfi-queued-messages-alert.png" alt-text="Güvenlik & Uyumluluk Merkezi'ndeki Uyarılar panosundaki Son uyarılar" lightbox="../../media/mfi-queued-messages-alert.png":::

- Yöneticiler, **İletiler geciktirildi** adlı varsayılan uyarı ilkesinin yapılandırmasını temel alan bir e-posta bildirimi alır. Bu uyarının bildirim ayarlarını yapılandırmak için sonraki bölüme bakın.

  Uyarı ilkeleri hakkında daha fazla bilgi için [bkz. Güvenlik & Uyumluluk Merkezi'ndeki Uyarı ilkeleri](../../compliance/alert-policies.md).

## <a name="customize-queue-alerts"></a>Kuyruk uyarılarını özelleştirme

1. [Güvenlik & Uyumluluk Merkezi'nde](https://protection.office.com) **Uyarılar** \> **Uyarı ilkeleri'ne** gidin veya öğesini açın<https://protection.office.com/alertpolicies>.

2. **Uyarı ilkeleri** sayfasında **İletiler geciktirildi** adlı ilkeyi bulun ve seçin.

3. Açılan **İleti gecikmeli** açılır öğesinde uyarıyı açabilir veya kapatabilir ve bildirim ayarlarını yapılandırabilirsiniz.

   :::image type="content" source="../../media/mfi-queued-messages-alert-policy.png" alt-text="İletiler gecikmeli uyarının ayrıntıları" lightbox="../../media/mfi-queued-messages-alert-policy.png":::

   - **Durum**: Uyarıyı açıp kapatabilirsiniz.

   - **E-posta alıcıları** ve **Günlük bildirim sınırı**: **Düzenle'ye** tıklayarak aşağıdaki ayarları yapılandırın:

4. Bildirim ayarlarını yapılandırmak için **Düzenle'ye** tıklayın. Görüntülenen **İlkeyi düzenle** açılır penceresinde aşağıdaki ayarları yapılandırın:

   - **E-posta bildirimleri gönder**: Varsayılan değer açıktır.
   - **E-posta alıcıları**: Varsayılan değer **TenantAdmins'tir**.
   - **Günlük bildirim sınırı**: Varsayılan değer **Sınır yok'dur**.
   - **Eşik**: Varsayılan değer 200'dür.

     :::image type="content" source="../../media/mfi-queued-messages-alert-policy-notification-settings.png" alt-text="İletiler'deki Bildirim ayarları gecikmeli uyarı" lightbox="../../media/mfi-queued-messages-alert-policy-notification-settings.png":::

5. İşiniz bittiğinde **Kaydet** ve **Kapat'a** tıklayın.

## <a name="queues-insight-in-the-mail-flow-dashboard"></a>Posta akışı panosundaki kuyruklar içgörüleri

Kuyruğa alınan ileti birimi eşiği aşmamış ve bir uyarı oluşturmamış olsa bile, posta [akışı panosundaki](mail-flow-insights-v2.md) **Kuyruklar içgörülerini** kullanarak bir saatten uzun süredir kuyruğa alınmış iletileri görebilir ve kuyruğa alınan ileti sayısı fazla artmadan önce eylem gerçekleştirebilirsiniz.

:::image type="content" source="../../media/mfi-queues-widget.png" alt-text="Güvenlik & Uyumluluk Merkezi'ndeki Posta akışı panosundaki Kuyruklar pencere öğesi" lightbox="../../media/mfi-queues-widget.png":::

Pencere öğesindeki ileti sayısına tıklarsanız, aşağıdaki bilgilerle **birlikte kuyruğa alınan iletiler** açılır öğesi görüntülenir:

- **Kuyruğa alınan ileti sayısı**
- **Bağlayıcı adı**: konumundaki Exchange yönetim merkezinde (EAC) <https://admin.exchange.microsoft.com/#/connectors>bağlayıcıyı yönetmek için bağlayıcı adını seçin.
- **Kuyruk başlama zamanı**
- **En eski iletilerin süresi doldu**
- **Hedef sunucu**
- **Son IP adresi**
- **Son hata**
- **Nasıl düzeltilir**: Yaygın sorunlar ve çözümler sağlanır. **Şimdi düzelt** bağlantısı varsa, sorunu çözmek için bu bağlantıya tıklayın. Aksi takdirde, hata ve olası çözümler hakkında daha fazla bilgi için kullanılabilir bağlantılara tıklayın.

:::image type="content" source="../../media/mfi-queues-details.png" alt-text="Posta akışı panosundaki Kuyruklar içgörüsüne tıkladıktan sonra ayrıntılar" lightbox="../../media/mfi-queues-details.png":::

İletiler **gecikmiş** uyarısının ayrıntılarında **Kuyruğu görüntüle'ye** tıkladıktan sonra aynı açılır öğe görüntülenir.

:::image type="content" source="../../media/mfi-queued-messages-alert-details.png" alt-text="Güvenlik & Uyumluluk Merkezi'nde İletilerin ayrıntıları geciktirildi uyarısı" lightbox="../../media/mfi-queued-messages-alert-details.png":::

## <a name="see-also"></a>Ayrıca bkz.

Posta akışı panosundaki diğer içgörüler hakkında bilgi için [Bkz. Güvenlik & Uyumluluk Merkezi'ndeki Posta akışı içgörüleri](mail-flow-insights-v2.md).
