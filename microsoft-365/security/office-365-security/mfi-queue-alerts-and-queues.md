---
title: Posta akışı panosunda Kuyruklar içgörü
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
description: Yöneticiler, şirket içi veya iş ortağı kuruluşlarının giden bağlantı bağlayıcıları üzerinden başarısız posta akışını izlemek için Güvenlik & Uyumluluk Merkezi'nin Posta akışı panosunda Kuyruklar widget'ini kullanmayı öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.collection: M365-security-compliance
ms.openlocfilehash: 54bff65b29555fe0c94c86141cd7a10a77c36219
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680016"
---
# <a name="queues-insight-in-the-security--compliance-center"></a>Güvenlik ve Uyumluluk Merkezi'nde Kuyruklar & bilgileri

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

İletiler, bağlayıcılar kullanılarak şirket içi veya iş ortağı e-posta sunucularınıza gönderilmey olduğunda, iletiler şirket içinde Microsoft 365. Bu koşula neden olan yaygın örnekler:

- Bağlayıcı yanlış yapılandırıldı.
- Şirket içi ortamınıza yönelik ağ veya güvenlik duvarı değişiklikleri var.

Microsoft 365 24 saat boyunca teslimi yeniden denemeye devam edecektir. 24 saat sonra, iletilerin süresi dolar ve teslim edil iletileri (NDR'ler veya geri dönen iletiler olarak da bilinir) içinde gönderenlere döndürülür.

Sıraya alınan e-posta hacmi önceden tanımlanmış eşiği aşarsa (varsayılan değer 200 iletidir), bilgiler aşağıdaki konumlarda mevcuttur:

- Güvenlik **ve Uyumluluk** Merkezi'nin [Posta akışı panosunda](mail-flow-insights-v2.md) [Kuyruklar &.](https://protection.office.com) Daha fazla bilgi için, [bu makalenin Posta akışı panosu bölümündeki Kuyruklar](#queues-insight-in-the-mail-flow-dashboard) içgörüsine bakın.

- Güvenlik ve Uyumluluk **Merkezi'nde (Uyarılar** Panosu veya ) Uyarılar [panosunda &](https://protection.office.com) **uyarı** \> **görüntülenir**<https://protection.office.com/alertsdashboard>.

  ![Güvenlik ve Uyumluluk Merkezi'nin Uyarılar panosunda son &.](../../media/mfi-queued-messages-alert.png)

- Yöneticiler, İletiler adlı varsayılan uyarı ilkesi gecikmiş yapılandırmasına dayalı bir **e-posta bildirimi alır**. Bu uyarının bildirim ayarlarını yapılandırmak için sonraki bölüme bakın.

  Uyarı ilkeleri hakkında daha fazla bilgi için Güvenlik [ve Uyumluluk Merkezi'nde & bakın](../../compliance/alert-policies.md).

## <a name="customize-queue-alerts"></a>Kuyruk uyarılarını özelleştirme

1. Güvenlik [ve Uyumluluk &'nde](https://protection.office.com) Uyarılar Uyarı **ilkeleri'ne gidin** \> **veya** 'i açın <https://protection.office.com/alertpolicies>.

2. Uyarı **ilkeleri sayfasında** İletiler gecikmeli adlı **ilkeyi bulup seçin**.

3. Açılan **İleti gecikmiş açılır** iletisinde, uyarıyı açar veya kapatabilir ve bildirim ayarlarını yapılandırabilirsiniz.

   ![İletiler gecikmeli uyarı ilkesi ayrıntıları Güvenlik ve Uyumluluk & bulunmaktadır.](../../media/mfi-queued-messages-alert-policy.png)

   - **Durum**: Uyarıyı açıp kapatarak kapatarak,

   - **E-posta alıcıları** ve **Günlük bildirim sınırı**: Aşağıdaki **ayarları yapılandırmak için** Düzenle'ye tıklayın:

4. Bildirim ayarlarını yapılandırmak için Düzenle'ye **tıklayın**. Görüntülenen **İlkeyi** düzenle açılır sayfasında, aşağıdaki ayarları yapılandırabilirsiniz:

   - **E-posta bildirimleri gönderme**: Varsayılan değer açıktır.
   - **E-posta** alıcıları: Varsayılan değer **TenantAdmins'tir**.
   - **Günlük bildirim sınırı**: Varsayılan değer Sınır **yok'tır**.
   - **Eşik**: Varsayılan değer 200'tir.

   ![İletiler'in bildirim ayarları, Güvenlik ve Uyumluluk Merkezi'nde gecikmiş uyarı & ayrıntılarıdır.](../../media/mfi-queued-messages-alert-policy-notification-settings.png)

5. Bitirdikten sonra Kaydet'e ve **Kapat'a** **tıklayın**.

## <a name="queues-insight-in-the-mail-flow-dashboard"></a>Posta akışı panosunda Kuyruklar içgörü

Sıraya alınan ileti hacmi eşiği aşmamış ve uyarı oluşturmamış olsa bile, posta akışı panosunda Kuyruklar içgörülerini kullanarak  bir saatten uzun süre sıraya [](mail-flow-insights-v2.md) alınan iletileri görebilir ve sıraya alınan iletilerin sayısı çok fazla olmadan önce bir işlem yapabilirsiniz.

![Güvenlik ve Uyumluluk Merkezi'nde Posta akışı panosunda kuyruklar widget& görüntülenir.](../../media/mfi-queues-widget.png)

Widget'ta ileti sayısına tıklarsanız, sıraya alınan **iletiler** açılır öğesi aşağıdaki bilgileri içerir:

- **Sıraya alınan iletilerin sayısı**
- **Bağlayıcı adı**: Bağlayıcı adını seçerek bağlayıcıyı yönetim merkezinden (EAC) <https://admin.exchange.microsoft.com/#/connectors>Exchange seçin.
- **Sırada başlama süresi**
- **İletilerin en eski süresi doldu**
- **Hedef sunucu**
- **Son IP adresi**
- **Son hata**
- **Nasıl düzeltebilirim**: Yaygın sorunlar ve çözümler kullanılabilir. Şimdi **düzelt bağlantısı varsa** , sorunu düzeltmek için bu bağlantıya tıklayın. Aksi takdirde, hata ve olası çözümler hakkında daha fazla bilgi için kullanılabilir bağlantılardan birini tıklatın.

![Posta akışı panosunda Kuyruklar içgörüne tık olduktan sonra ayrıntılar.](../../media/mfi-queues-details.png)

İletiler gecikmiş uyarısının **ayrıntılarında** Kuyruğu görüntüle'ye tıklarsanız **aynı uç uçarak** çıkış görüntülenir.

![İletiler, Güvenlik ve Uyumluluk Merkezi'nde gecikmeli & yapıldı.](../../media/mfi-queued-messages-alert-details.png)

## <a name="see-also"></a>Ayrıca bkz.

Posta akışı panosunda yer alan diğer içgörüler hakkında bilgi için, Güvenlik ve Uyumluluk Merkezi'nde [Posta & bakın](mail-flow-insights-v2.md).
