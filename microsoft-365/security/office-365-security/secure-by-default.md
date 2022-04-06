---
title: Office 365'de varsayılan olarak güvenlidir
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
description: Exchange Online Protection'da (EOP) varsayılan olarak güvenli ayarı hakkında daha fazla bilgi edinin
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 09395775cc5ecbd420dc7197664401c01c24d6c3
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664226"
---
# <a name="secure-by-default-in-office-365"></a>Office 365'de varsayılan olarak güvenlidir

[!INCLUDE [Prerelease information](../includes/prerelease.md)]
[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

"Varsayılan olarak güvenli", mümkün olan en güvenli varsayılan ayarları tanımlamak için kullanılan bir terimdir.

Ancak güvenliğin üretkenlikle dengelenmesi gerekir. Bu, aşağıdakiler arasında dengelemeyi içerebilir:

- **Kullanılabilirlik**: Ayarlar kullanıcı üretkenliğinin önünü almamalıdır.
- **Risk**: Güvenlik önemli etkinlikleri engelleyebilir.
- **Eski ayarlar**: Yeni, modern ayarlar iyileştirilse bile eski ürünler ve özellikler için bazı yapılandırmaların iş nedeniyle korunması gerekebilir.

posta kutuları Exchange Online olan Microsoft 365 kuruluşlar Exchange Online Protection (EOP) tarafından korunur. Bu koruma şunları içerir:

- Kötü amaçlı yazılım olduğundan şüphelenilen e-postalar otomatik olarak karantinaya alınır. Karantinaya alınan kötü amaçlı yazılım iletileri alıcılara bildirilip bildirilmediği, karantina ilkesi ve kötü amaçlı yazılımdan koruma ilkesindeki ayarlar tarafından denetlenmektedir. Daha fazla bilgi için bkz. [EOP'de kötü amaçlı yazılımdan koruma ilkelerini yapılandırma](configure-anti-malware-policies.md).
- Yüksek güvenilirlikli kimlik avı olarak tanımlanan e-postalar istenmeyen posta önleme ilkesi eylemine göre işlenir. Bkz [. EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

EOP hakkında daha fazla bilgi için bkz. [Exchange Online Protection genel bakış](exchange-online-protection-overview.md).

Microsoft varsayılan olarak müşterilerimizin güvenliğini sağlamak istediğinden, bazı kiracı geçersiz kılmaları kötü amaçlı yazılım veya yüksek güvenilirlikli kimlik avı için uygulanmaz. Bu geçersiz kılmalar şunlardır:

- İzin verilen gönderen listeleri veya izin verilen etki alanı listeleri (istenmeyen posta önleme ilkeleri)
- Outlook Kasa Gönderenler
- IP İzin Ver Listesi (bağlantı filtreleme)
- Exchange posta akışı kuralları (taşıma kuralları olarak da bilinir)

Bu geçersiz kılmalar hakkında daha fazla bilgi [Güvenli gönderen oluşturma listelerinde](create-safe-sender-lists-in-office-365.md) bulunabilir.

> [!NOTE]
> EOP istenmeyen posta önleme ilkelerinde **Yüksek güvenilirlikli kimlik avı e-postası** kararı için **İletiyi Gereksiz E-posta klasörüne taşı** eylemini kullanım dışı bırakılmıştır. Yüksek güvenilirlikli kimlik avı iletileri için bu eylemi kullanan istenmeyen posta önleme ilkeleri **Karantina iletisine** dönüştürülür. Yüksek güvenilirlikli kimlik avı iletileri için **e-posta adresine yeniden yönlendirme** eylemi bundan etkilenmez.

Varsayılan olarak güvenli, açılabilir veya kapatılabilir bir ayar değildir, ancak potansiyel olarak tehlikeli veya istenmeyen iletileri posta kutularınızdan uzak tutmak için filtrelememizin kullanıma hazır şekilde çalışmasıdır. Kötü amaçlı yazılım ve yüksek güvenilirlikli kimlik avı iletileri karantinaya alınmalıdır. Varsayılan olarak, yalnızca yöneticiler kötü amaçlı yazılım veya yüksek güvenilirlikli kimlik avı olarak karantinaya alınan iletileri yönetebilir ve buradan Microsoft'a hatalı pozitif sonuçları da bildirebilir. Daha fazla bilgi için bkz. [Karantinaya alınan iletileri ve dosyaları EOP'de yönetici olarak yönetme](manage-quarantined-messages-and-files.md).

## <a name="more-on-why-were-doing-this"></a>Bunu neden yaptığımız hakkında daha fazla bilgi

Varsayılan olarak güvenli olmanın ruhu şudur: Yapılandırılmış bir özel durum iletinin teslim edilmesine izin verse bile, iletiyi kötü amaçlı olarak biliyorsanız iletide gerçekleştirdiğiniz eylemin aynısını yapıyoruz. Bu, her zaman kötü amaçlı yazılımlarda kullandığımız yaklaşımla aynıdır ve şimdi de aynı davranışı yüksek güvenilirlikli kimlik avı iletilerine genişletiyoruz.

Verilerimiz, kullanıcının Gereksiz E-posta klasöründeki iletilerde kötü amaçlı bir bağlantıya tıklama olasılığının 30 kat daha yüksek olduğunu ve Karantinaya Alma'nın karşı karşıya olduğunu gösteriyor. Verilerimiz ayrıca yüksek güvenilirlikli kimlik avı iletileri için hatalı pozitif oranın (iyi iletiler kötü olarak işaretlenir) çok düşük olduğunu ve yöneticilerin hatalı pozitif sonuçları yönetici gönderimleriyle çözümleyebileceğini gösterir.

Ayrıca, istenmeyen posta önleme ilkelerinde izin verilen gönderen ve izin verilen etki alanı listelerinin ve Outlook'daki Kasa Gönderenlerin çok geniş olduğunu ve iyiden daha fazla zarara neden olduğunu belirledik.

Başka bir şekilde ifade etmek gerekirse, bir güvenlik hizmeti olarak kullanıcılarınızın gizliliğinin tehlikeye girmesini önlemek için sizin adına hareket ediyoruz.

## <a name="exceptions"></a>Özel durum

Yalnızca aşağıdaki senaryolarda geçersiz kılmaları kullanmayı düşünmelisiniz:

- Kimlik avı simülasyonları: Sanal saldırılar, kuruluşunuzu gerçek bir saldırı etkilemeden önce savunmasız kullanıcıları belirlemenize yardımcı olabilir. Kimlik avı benzetimi iletilerinin filtrelenmesini önlemek için [gelişmiş teslim ilkesinde üçüncü taraf kimlik avı simülasyonlarını yapılandırma](/microsoft-365/security/office-365-security/configure-advanced-delivery#use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy) bölümüne bakın.
- Güvenlik/SecOps posta kutuları: Güvenlik ekipleri tarafından filtrelenmemiş iletiler (hem iyi hem de kötü) almak için kullanılan ayrılmış posta kutuları. Teams daha sonra kötü amaçlı içerik içerip içermediklerini gözden geçirebilir. Daha fazla bilgi için bkz. [Gelişmiş teslim ilkesinde SecOps posta kutularını yapılandırma](/microsoft-365/security/office-365-security/configure-advanced-delivery#use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy).
- Üçüncü taraf filtreleri: Varsayılan olarak güvenli, yalnızca etki alanınızın MX kaydı Exchange Online Protection (contoso.mail.protection.outlook.com) olarak ayarlandığında geçerlidir. Başka bir hizmete veya cihaza ayarlandıysa, tüm istenmeyen posta filtrelemesini atlamak için Varsayılan olarak Güvenli'yi bir [Aktarım Kuralı](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl) ile geçersiz kılmak mümkündür. Microsoft, bu kuralla iletileri Yüksek Güvenilirlikli Kimlik Avı olarak algıladığında, yine de Gelen Kutusu'na teslim eder. 
- Hatalı pozitifler: [Yönetici gönderimleri aracılığıyla](admin-submission.md) Microsoft tarafından analiz edilmeye devam eden belirli iletilere geçici olarak izin vermek isteyebilirsiniz. Tüm geçersiz kılmalarda olduğu gibi, bunların da geçici olması önerilir.
