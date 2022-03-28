---
title: E-postada varsayılan olarak Office 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: 06/28/2021
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
description: Exchange Online Protection (EOP) güvenlik ayarı hakkında daha fazla bilgi
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 59f29b0e923bdeb7481a64fb9ba1c3890e2b1369
ms.sourcegitcommit: 9c8eca862a2f0fdca7a66c641e382e37fcaefa10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2022
ms.locfileid: "63775510"
---
# <a name="secure-by-default-in-office-365"></a>E-postada varsayılan olarak Office 365

[!INCLUDE [Prerelease information](../includes/prerelease.md)]
[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

"Varsayılan olarak güvenli", mümkün olduğunca güvenli olan varsayılan ayarları tanımlamak için kullanılan bir terimdir.

Ancak güvenlik, üretkenlikle dengelenmeli. Bu, aşağıdakiler arasında dengeyi içerebilir:

- **Kullanılabilirlik**: Ayarlar üretkenliğini artırmamalarını sağlar.
- **Risk**: Güvenlik önemli etkinlikleri engelleyebilir.
- **Eski ayarlar**: Yeni, modern ayarlar geliştirnse bile, iş nedenleriyle eski ürün ve özelliklerle ilgili bazı yapılandırmaların korunması gerekebilir.

Microsoft 365 posta kutuları olan tüm kuruluşlar Exchange Online EOP (Exchange Online Protection) tarafından korunur. Bu koruma şunları içerir:

- Kötü amaçlı yazılımdan şüpheleniyorsanız e-posta otomatik olarak karantinaya alınır. Alıcılara karantinaya alınmış kötü amaçlı yazılım iletileri hakkında bildirilecek iletiler karantina ilkesi ve kötü amaçlı yazılımdan koruma ilkesindeki ayarlar tarafından denetleniyor. Daha fazla bilgi için bkz. [EOP'de kötü amaçlı yazılımdan koruma ilkelerini yapılandırma](configure-anti-malware-policies.md).
- Kimlik avının yüksek güven olduğu tanımlanan e-postalar, istenmeyen posta önleme ilkesi eylemine göre ele alınacaktır. Bkz [. EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

EOP hakkında daha fazla bilgi için bkz. [Exchange Online Protection genel bakış](exchange-online-protection-overview.md).

Microsoft müşterilerimizin varsayılan olarak güvenliğini sağlamak istediği için, bazı kiracılar geçersiz kılmalar kötü amaçlı yazılım veya yüksek güvenli kimlik avı için uygulanmaz. Bu geçersiz kılmalar şunlardır:

- İzin verilen gönderenler listeleri veya izin verilen etki alanı listeleri (istenmeyen posta önleme ilkeleri)
- Outlook Kasa Gönderenler
- IP İzin Ver Listesi (bağlantı filtreleme)
- Exchange akış kurallarını (aktarım kuralları olarak da bilinir) taşıma

Bu geçersiz kılmalar hakkında daha fazla bilgiyi Güvenilir gönderen [listeleri oluşturma altında bulunabilir](create-safe-sender-lists-in-office-365.md).

> [!NOTE]
> EOP istenmeyen posta önleme ilkelarında, Yüksek güvene sahip kimlik avı e-posta kararlığı için İletiyi Gereksiz E-posta klasörüne taşı eylemlerini kullanım dışı bıraktık. Kimlik avı iletilerinin yüksek güvene sahip olması için bu eylemi kullanan istenmeyen posta önleme ilkeleri Karantina **iletisine dönüştürülür**. Yüksek **güven kimlik avı iletileri için** iletiyi e-posta adresine yeniden yönlendir eylemi etkilenmez.

Varsayılan olarak güvenli, açık veya kapalı olabilecek bir ayar değildir, ancak filtre uygulamamızın, tehlikeli veya istenmeyen iletileri posta kutularınıza kapatmanın kolay yoludur. Kötü amaçlı yazılım ve yüksek güvene sahip kimlik avı iletileri karantinaya alınacaktır. Varsayılan olarak, yalnızca yöneticiler kötü amaçlı yazılım olarak karantinaya alınmış veya yüksek güveni olan kimlik avı iletileri yönetebilir ve Microsoft'a buradan da hatalı pozitif sonuçlar bildirebilirsiniz. Daha fazla bilgi için bkz [. EOP'de yönetici olarak karantinaya alınmış iletileri ve dosyaları yönetme](manage-quarantined-messages-and-files.md).

## <a name="more-on-why-were-doing-this"></a>Bunu neden yapıyoruz hakkında daha fazla bilgi

Varsayılan olarak güvende olmanın ruhunu şudur: Yapılandırılan bir özel durum iletinin teslim  olmasına izin verse bile, kötü amaçlı iletiyi biliyorsanız iletide de aynı eylemi benimseriz. Bu, her zaman kötü amaçlı yazılım üzerinde kullandığımız yaklaşımla aynıdır ve şimdi de aynı davranışı yüksek güven amaçlı kimlik avı iletilerine genişletiyoruz.

Verilerimiz bir kullanıcının Gereksiz E-posta klasöründeki Karantina yerine iletilerde yer alan kötü amaçlı bağlantıya tıklama olasılığı 30 kat daha yüksek olduğunu gösterir. Ayrıca verilerimiz, kimlik avı iletilerine yönelik hatalı pozitif oranın (iyi iletiler kötü olarak işaretlenen iletiler) çok düşük olduğunu ve yöneticilerin yönetici gönderimleriyle tüm hatalı pozitif pozitifleri çöze bir durumu olduğunu da gösterir.

Ayrıca, izin verilen gönderenin ve izin verilen etki alanı listelerinin istenmeyen posta önleme ilkelerinde ve Kasa Web'Outlook fazla geniş olduğunu ve iyiden çok daha fazla hasara neden olduğunu belirledik.

Başka bir şekilde ifade etmek gerekir: Güvenlik hizmeti olarak kullanıcılarının güvenliğinin ihlalini önlemek için sizin adına hareket ediyoruz.

## <a name="exceptions"></a>Özel Durumlar

Geçersiz kılmaları yalnızca aşağıdaki senaryolarda kullanabilirsiniz:

- Kimlik avı benzetimleri: Benzetimi yapılan saldırılar, gerçek bir saldırının organizasyonunu etkilemeden önce zayıf kullanıcıları tanımlamanıza yardımcı olabilir. Kimlik avı benzetimi iletilerinin filtresini önlemek için bkz. Gelişmiş teslim ilkesinde üçüncü taraf kimlik [avı benzetimlerini yapılandırma](/microsoft-365/security/office-365-security/configure-advanced-delivery#use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy).
- Güvenlik/SecOps posta kutuları: Güvenlik ekipleri tarafından filtrelenmemiş iletileri almak için kullanılan özel posta kutuları (hem iyi hem de kötü). Teams içeriği olup olduklarını görmek için gözden geçirebilirsiniz. Daha fazla bilgi için bkz [. Gelişmiş teslim ilkesinde SecOps posta kutularını yapılandırma](/microsoft-365/security/office-365-security/configure-advanced-delivery#use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy).
- Üçüncü taraf filtreler: Varsayılan olarak güvenli yalnızca etki alanınıza uygulanan MX kaydı Exchange Online Protection (contoso.mail.protection.outlook.com). Başka bir hizmet veya cihaza ayarlanmışsa, tüm istenmeyen posta filtrelemesini atlayan bir Aktarım Kuralı ile varsayılan [](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl) olarak Güvenli'i geçersiz kılmak mümkündür. Microsoft, bu kuralın yerine geldiğinde iletileri Yüksek Güven Kimlik Avı olarak algılasa da Gelen Kutusu'na teslim eder. 
- Hatalı pozitif sonuçlar: Yönetici gönderimleri aracılığıyla Microsoft tarafından çözüm halen incelene bazı iletilere geçici [olarak izin vermek istiyor olabilir](admin-submission.md). Tüm geçersiz kılmalarda olduğu gibi, bunların geçici olarak kullanılması önerilir.
