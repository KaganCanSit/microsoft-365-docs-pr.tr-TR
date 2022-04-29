---
title: Posta akışı panosunda giden ve gelen posta akışı içgörüleri
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
description: Yöneticiler, Güvenlik & Uyumluluk Merkezi'ndeki Posta akışı panosunda Giden ve gelen posta akışı içgörüleri hakkında bilgi edinebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f856e2b9a4829531966802f2594f26c19e6ab7e5
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65131206"
---
# <a name="outbound-and-inbound-mail-flow-insight-in-the-security--compliance-center"></a>Güvenlik & Uyumluluk Merkezi'nde giden ve gelen posta akışı içgörüleri

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[Güvenlik & Uyumluluk Merkezi'ndeki](https://protection.office.com) [Posta akışı panosundaki](mail-flow-insights-v2.md) **Giden ve gelen posta akışı** içgörüleri [, Bağlayıcı raporuyla](view-mail-flow-reports.md#connector-report) eski **TLS genel bakış raporundaki** bilgileri tek bir yerde birleştirir.

Pencere öğesi, kuruluşunuza ve kuruluşunuzdan iletiler teslim edildiğinde bağlantı için kullanılan TLS şifrelemesini görüntüler. Diğer e-posta hizmetleriyle kurulan bağlantılar, TLS her iki taraf tarafından sunulduğunda TLS tarafından şifrelenir. Pencere öğesi, posta akışının son haftasının anlık görüntüsünü sunar.

:::image type="content" source="../../media/mfi-outbound-and-inbound-mail-flow-report-widget.png" alt-text="Güvenlik & Uyumluluk Merkezi'ndeki Posta akışı panosundaki Giden ve gelen posta akışı pencere öğesi" lightbox="../../media/mfi-outbound-and-inbound-mail-flow-report-widget.png":::

Pencere öğesindeki bilgiler, Microsoft 365'deki bağlayıcılar ve TLS ileti korumasıyla ilgilidir. Daha fazla bilgi için şu konulara bakın:

- [Bağlayıcıları kullanarak posta akışını yapılandırma](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)
- [Exchange Online, e-posta bağlantılarının güvenliğini sağlamak için TLS'yi nasıl kullanır?](../../compliance/exchange-online-uses-tls-to-secure-email-connections.md)
- [Microsoft 365'de şifreleme hakkında teknik başvuru ayrıntıları](../../compliance/technical-reference-details-about-encryption.md)

## <a name="message-protected-in-transit-by-tls"></a>İleti aktarımda korunuyor (TLS tarafından)

Pencere öğesinde **Ayrıntıları Görüntüle'ye** tıkladığınızda **aktarımda korunan ileti (TLS tarafından)** açılır öğesi, kuruluşunuza giren ve ayrılan iletiler için TLS korumasını gösterir.

:::image type="content" source="../../media/mfi-outbound-and-inbound-mail-flow-report-details.png" alt-text="Giden ve gelen e-posta pencere öğesinde Ayrıntıları görüntüle'ye tıkladıktan sonra görüntülenen aktarımda korunan iletiler (TLS tarafından) açılır öğesi" lightbox="../../media/mfi-outbound-and-inbound-mail-flow-report-details.png":::

Şu anda TLS 1.2, Microsoft 365 tarafından sunulan en güvenli TLS sürümüdür. Genellikle uyumluluk denetimleri için kullanılan TLS şifrelemesini bilmeniz gerekir. Büyük olasılıkla kaynak ve hedef e-posta sunucularının çoğuyla doğrudan bir ilişkiniz yoktur (bunların sahibi siz değilsiniz ve Microsoft'un da yoktur), bu nedenle bu sunucular tarafından kullanılan TLS şifrelemesini geliştirmek için çok fazla seçeneğiniz yoktur.

Ancak, e-posta sunucularınız ile Microsoft 365 arasında gönderilen iletiler için kullanılabilir en iyi TLS korumasını sağlamak için [bağlayıcıları](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow) kullanabilirsiniz. Microsoft 365 ile kendi e-posta sunucularınız veya iş ortaklarınıza ait sunucular arasındaki posta akışı genellikle normal iletilerden daha önemli ve hassastır, bu nedenle bu iletilere ek güvenlik ve ihtiyat uygulamak istersiniz.

Kullanılan TLS şifrelemesini geliştirmek için kendi e-posta sunucularınızı yükseltebilir veya düzeltebilir ya da aynı işlemi yapmak için iş ortaklarınıza ulaşabilirsiniz. **Bağlayıcı Raporu**, Microsoft 365 bağlayıcılarınızı kullanan iletiler için hem posta akışı hacmini hem de TLS şifrelemesini görüntüler.

**Bağlayıcı raporu** bağlantısına tıklayarak [Bağlayıcı raporuna](view-mail-flow-reports.md#connector-report) gidebilirsiniz. İlişkili koşul algılandıysa **Bağlayıcı rapor** sayfasında aşağıdaki içgörüler bulunabilir:

- **Gelen İş Ortağı bağlayıcısı önemli TLS1.0 posta akışı görüyor**
- **Gelen OnPremises bağlayıcısı önemli TLS1.0 posta akışı görüyor**

TLS 1.0 bağlantılarında, TLS 1.0 desteği sonunda Microsoft 365 kullanım dışı bırakıldığında herhangi bir sorun yaşanmaması için e-posta sunucunuzu veya iş ortağınızın sunucusunu yükseltmeniz veya düzeltmeniz gerekir.

## <a name="see-also"></a>Ayrıca bkz.

Posta akışı panosundaki diğer içgörüler hakkında bilgi için [Bkz. Güvenlik & Uyumluluk Merkezi'ndeki Posta akışı içgörüleri](mail-flow-insights-v2.md).
