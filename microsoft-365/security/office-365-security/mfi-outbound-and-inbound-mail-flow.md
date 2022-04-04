---
title: Posta akışı panosunda Giden ve gelen posta akışı içgörü
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: f2738dec-41b0-43c4-b814-84c0a4e45c6d
description: Yöneticiler, Güvenlik ve Uyumluluk Merkezi'nin Posta akışı panosunda Giden ve gelen posta akışı hakkında bilgi & bilgi edinebilirsiniz.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5de9c699a12a7c3f282c4e1752eb23c5842a8c5d
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63679620"
---
# <a name="outbound-and-inbound-mail-flow-insight-in-the-security--compliance-center"></a>Güvenlik ve Uyumluluk Merkezi'nde Giden ve gelen posta & içgörü

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Güvenlik **ve Uyumluluk Merkezi &'nin** Posta akışı panosunda [](mail-flow-insights-v2.md) Giden ve gelen posta akışı [](https://protection.office.com) içgörüsi, [Bağlayıcı](view-mail-flow-reports.md#connector-report) raporuyla eski **TLS** genel bakış raporuna ilişkin bilgileri tek bir yerde birleştirir.

Pencere öğesi, iletiler kuruluşa teslim edilir ve buradan teslim edilirken bağlantı için kullanılan TLS şifrelemesi görüntüler. TLS her iki tarafın da sunduğunda, diğer e-posta hizmetleriyle kurulan bağlantılar TLS ile şifrelenir. Widget, posta akışının son haftası için bir anlık görüntü sunar.

![Güvenlik ve Uyumluluk Merkezi'nin Posta akışı panosunda Giden ve gelen posta & pencere öğesi.](../../media/mfi-outbound-and-inbound-mail-flow-report-widget.png)

Widget'daki bilgiler, çalışma sayfalarında bağlayıcılarla ve TLS ileti korumasıyla Microsoft 365. Daha fazla bilgi için bu konulara bakın:

- [Bağlayıcıları kullanarak posta akışını yapılandırma](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)
- [E Exchange Online bağlantılarının güvenliğini sağlamak için TLS'yi nasıl kullanır?](../../compliance/exchange-online-uses-tls-to-secure-email-connections.md)
- [E-Microsoft 365'de şifreleme hakkında teknik başvuru Microsoft 365](../../compliance/technical-reference-details-about-encryption.md)

## <a name="message-protected-in-transit-by-tls"></a>İletim sırasında korunan ileti (TLS ile)

**Widget'ta Ayrıntıları Görüntüle'ye** tıklarsanız, İletim halinde korunan **(TLS ile)** ileti geçici öğesi, kuruluşa giriş ve çıkışta iletiler için TLS korumasını gösterir.

![İletiler, Giden ve gelen e-posta widget'sinde Ayrıntıları görüntüle'yi tıklatmanız sonrasında görüntülenen , toplu (TLS ile) açılır öğesinde korunur.](../../media/mfi-outbound-and-inbound-mail-flow-report-details.png)

Şu anda TLS 1.2, TLS'nin sunduğu en güvenli TLS sürümü Microsoft 365. Çoğunlukla, uyumluluk denetimi için kullanılan TLS şifrelemesi hakkında bilgili olmak gerekir. Büyük olasılıkla, kaynak ve hedef e-posta sunucularının çoğuyla (bu sunuculara ve Microsoft'a sahip değil) doğrudan ilişkiniz yok, dolayısıyla bu sunucular tarafından kullanılan TLS şifrelemeyi geliştirmek için pek fazla seçeneğiniz yok.

Ancak, e-posta [sunucularınız](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) ve posta sunucularınız arasında gönderilen iletiler için en uygun TLS korumasının sağlanması için bağlayıcıları Microsoft 365. Microsoft 365 iş ortaklarına ait e-posta sunucularınız veya sunucularınız arasında posta akışı genellikle normal iletilerden daha önemli ve hassastır; dolayısıyla bu iletilere daha fazla güvenlik ve temlik uygulamak istemeniz gerekir.

Kullanılan TLS şifrelemesi geliştirmek için kendi e-posta sunucularınızı yükseltebilir veya düzeltebilir veya aynı işlemi yapmak için iş ortaklarına ulaşabilirsiniz. Bağlayıcı **Raporu,** kendi bağlayıcılarınızı kullanan iletiler için hem posta akışı hacmini hem de TLS Microsoft 365 görüntüler.

Bağlayıcı raporuna **gitmek için** Bağlayıcı raporu [bağlantısına tıkabilirsiniz](view-mail-flow-reports.md#connector-report). İlişkili koşul algılanırsa **, Bağlayıcı rapor** sayfasında aşağıdaki içgörüler kullanılabilir:

- **Önemli TLS1.0 posta akışını gören Gelen İş Ortağı bağlayıcısı**
- **Önemli TLS1.0 posta akışıyla ilgili gelen OnPremises bağlayıcısı**

TLS 1.0 bağlantılarında, TLS 1.0 desteği bir süre sonra TLS 1.0 desteğinin herhangi bir sorundan kaçınmak için e-posta sunucusunu veya iş ortağının sunucusunu yükseltmeniz veya Microsoft 365.

## <a name="see-also"></a>Ayrıca bkz.

Posta akışı panosunda yer alan diğer içgörüler hakkında bilgi için, Güvenlik ve Uyumluluk Merkezi'nde [Posta & bakın](mail-flow-insights-v2.md).