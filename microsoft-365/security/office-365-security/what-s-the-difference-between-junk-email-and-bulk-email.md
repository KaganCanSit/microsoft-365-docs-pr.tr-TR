---
title: Önemsiz e-posta ile toplu e-posta arasındaki fark nedir?
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 8079f193-1b40-4081-9e5d-d0e50dfbcc59
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler, Exchange Online Protection'da (EOP) gereksiz e-posta (istenmeyen posta) ile toplu e-posta (gri posta) arasındaki farklar hakkında bilgi edinebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: dd876b522a0d565b84e8bb9043e277cd3bc34495
ms.sourcegitcommit: 61bdfa84f2d6ce0b61ba5df39dcde58df6b3b59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2022
ms.locfileid: "65940458"
---
# <a name="whats-the-difference-between-junk-email-and-bulk-email-in-eop"></a>EOP'de gereksiz e-posta ile toplu e-posta arasındaki fark nedir?

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online'da posta kutuları olan Microsoft 365 kuruluşlarında veya Exchange Online posta kutuları olmayan tek başına Exchange Online Protection (EOP) kuruluşlarında müşteriler bazen şunu sorar: "Gereksiz e-posta ile toplu e-posta arasındaki fark nedir?" Bu konu, farkı açıklar ve EOP'de kullanılabilen denetimleri açıklar.

- **Gereksiz e-posta** istenmeyen ve evrensel olarak istenmeyen iletiler olan istenmeyen postadır (doğru tanımlandığında). Varsayılan olarak, EOP kaynak e-posta sunucusunun itibarına bağlı olarak istenmeyen postaları reddeder. Bir ileti kaynak IP incelemesini geçerse istenmeyen posta filtrelemeye gönderilir. İleti istenmeyen posta filtresiyle istenmeyen posta olarak sınıflandırılırsa, ileti (varsayılan olarak) hedeflenen alıcılara teslim edilir ve Gereksiz E-posta klasörüne taşınır.

  - İstenmeyen posta filtreleme kararlarında gerçekleştirebileceğiniz eylemleri yapılandırabilirsiniz. Yönergeler için bkz. [EOP'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

  - İstenmeyen posta filtreleme kararına katılmıyorsanız, iletileri ve dosyaları Microsoft'a bildirme bölümünde açıklandığı gibi, istenmeyen posta veya istenmeyen posta olmadığını düşündüğünüz [iletileri çeşitli yollarla Microsoft'a](report-junk-email-messages-to-microsoft.md) bildirebilirsiniz.

- **Toplu e-postayı** ( _gri posta_ olarak da bilinir) sınıflandırmak daha zordur. İstenmeyen postalar sürekli bir tehdit olsa da toplu e-posta genellikle tek seferlik reklamlar veya pazarlama iletileridir. Bazı kullanıcılar toplu e-posta iletilerini (ve aslında bunları almak için kasıtlı olarak kaydolmuşlardır) isterken, diğer kullanıcılar toplu e-postayı istenmeyen posta olarak kabul eder. Örneğin, bazı kullanıcılar Contoso Corporation'dan reklam iletileri veya siber güvenlikle ilgili yaklaşan bir konferansa davetler almak isterken, diğer kullanıcılar aynı iletileri istenmeyen posta olarak kabul eder.

  Toplu e-postanın nasıl tanımıldığı hakkında daha fazla bilgi için bkz. [EOP'de toplu şikayet düzeyi (BCL).](bulk-complaint-level-values.md)

## <a name="how-to-manage-bulk-email"></a>Toplu e-postayı yönetme

Toplu e-postaya yönelik karışık tepki nedeniyle, her kuruluş için geçerli olan evrensel rehberlik yoktur.

İstenmeyen posta önleme ilkeleri, toplu e-postayı istenmeyen posta olarak tanımlamak için kullanılan varsayılan bir BCL eşiğine sahiptir. Yöneticiler eşiği artırabilir veya azaltabilir. Daha fazla bilgi için, aşağıdaki konulara bakın:

- [EOP'de istenmeyen posta önleme ilkelerini yapılandırın](configure-your-spam-filter-policies.md).

- [EOP istenmeyen posta önleme ilkesi ayarları](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings)

Gözden kaçırması kolay başka bir seçenek: Bir kullanıcı toplu e-posta almaktan şikayetçiyse ancak iletiler EOP'de istenmeyen posta filtrelemesi geçiren saygın gönderenlerden geliyorsa, kullanıcının toplu e-posta iletisinde abonelikten çıkma seçeneğini denetlemesini sağlayın.
