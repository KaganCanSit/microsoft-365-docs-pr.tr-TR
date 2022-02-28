---
title: Microsoft 365 Multi-Geo
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: seo-marvel-apr2020
ms.collection: Strat_SP_gtc
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: Bu makalede, kaynak iletişim durumu bilginizi Multi-Geo Microsoft 365 birden çok coğrafi bölgeye Microsoft 365 öğrenin.
ms.openlocfilehash: 5122979fc79ce9aebe542a80ed614e7dcad70d03
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986476"
---
# <a name="microsoft-365-multi-geo"></a>Microsoft 365 Multi-Geo

Birden Microsoft 365 Multi-Geo'ya sahip olan organizasyonu, Microsoft 365 kiracı içinde birden çok coğrafi bölgeye ve/veya ülkeye genişletip kullanılabilir. Multi-Geo üzerinde Çok Uluslu Şirket'e kaydolmak için Microsoft Microsoft 365 olun.
  
Microsoft 365 Multi-Geo ile, veri yerleşim gereksinimlerini karşılamayı seçtiğiniz coğrafi konumlarda verilerin geri kalanını hazırlar ve depolar ve aynı zamanda iş gücünize küresel olarak modern üretkenlik deneyimlerinizi sunar.

Multi-Geo'ya Microsoft 365 video için [SharePoint Online'a OneDrive Multi-Geo verilerinizin yerini denetleme hakkında daha fazla bilgi için bkz](https://www.youtube.com/watch?v=Do9U3JuROhk).

## <a name="multi-geo-architecture"></a>Multi-Geo architecture

Multi-Geo ortamında, Microsoft 365 kiracınız merkezi bir konumdan (Microsoft 365 aboneliğinizin sağladığı konum) ve bir veya birden çok uydu konumdan oluşur. Çok coğrafi bir kiracıda, coğrafi konumlar, gruplar ve kullanıcı bilgileriyle ilgili bilgiler Azure Active Directory (Azure AD) içindedir. Kiracı bilgileri merkezi olarak ustalıklı ve her coğrafi konumda eşitlenmiş olduğundan, şirketiniz dışından herhangi birini içeren paylaşım ve deneyimler küresel farkındalık içerir.

![SharePoint yönetim merkezinden multi-geo haritanın ekran görüntüsü.](../media/multi-geo-world-map.png)

Multi-Geo Microsoft 365 performans iyileştirme için tasarlanmasa da, verilerin ikamet gereksinimlerini karşılamak için tasarlanmamaktadır. E-posta için performans iyileştirme Microsoft 365 için bkz. E-posta için ağ [Microsoft 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) performans ayarı veya destek grubunuzla iletişime geçin.

## <a name="terminology"></a>Terminoloji

Multi-Geo'da Microsoft 365 kullanılan anahtar terimler:

- **Merkezi konum** - Kiracınız başlangıçta sağlandı olan coğrafi konum.
- **Coğrafi yönetici** - Belirtilen bir veya daha fazla uydu konumunu yöneten bir yönetici.
- **Coğrafi kod** - Verilen coğrafi konum için üç harfli bir koddur.
- **Coğrafi konum** – Posta kutuları, posta kutuları, posta kutuları ve posta kutuları ve diğer siteler dahil olmak Exchange üzere verileri barındırmak OneDrive coğrafi bir SharePoint konum.
- **Tercih Edilen Veri Konumu (PDL)** – Yönetici tarafından, kullanıcıların posta kutusu veya posta kutusu veya posta kutusu için nereye Exchange sağlanarak OneDrive ayarlanmış bir kullanıcı özelliği. PDL, kullanıcı tarafından SharePoint hangi sitelerin sağlandıklarını da belirler.
- **Uydu konumu** – Coğrafi olarak farkında olan Microsoft 365 iş yüklerinin (SharePoint, OneDrive ve Exchange) çok coğrafi kiracıda etkinleştirildiğinde coğrafi konumlar.
- **Kiracı** – Normalde bir veya daha fazla etki Microsoft 365 etki alanı (örneğin, birden çok etki alanı) olan Kullanıcı Bilgileri sayfasında contoso.com.

## <a name="licensing"></a>Lisanslama

Microsoft 365 Multi-Geo, kiracılarında en az 250 Microsoft 365 kullanıcısı olan Kurumsal Anlaşma müşterileri için ve multi-geo kullanan bu bilgisayar kullanıcılarının en az %5'i için aşağıdaki Microsoft 365 abonelik planlarına eklenti olarak kullanılabilir. Kullanıcı aboneliği lisansları Multi-Geo Services Kurumsal Anlaşma lisansları ile aynı lisans üzerinde yer almalı. Ayrıntılar için lütfen Microsoft hesabı ekibiyle iletişime geçin.

- Microsoft 365 F1, F3, E3 veya E5
- Office 365 F3, E1, E3 veya E5'i
- Exchange Online Plan 1 veya Plan 2
- OneDrive İş Plan 1 veya Plan 2
- SharePoint Online Plan 1 veya Plan 2

Bir kullanıcıya lisans atanmışsa ve daha sonra Teams merkezi konuma taşınmak için kullanıcı sohbeti verileri sıraya alındı. SharePoint ve Exchange verileri taşınmaz.

## <a name="microsoft-365-multi-geo-availability"></a>Microsoft 365 Multi-Geo kullanılabilirliğini sağlar

Microsoft 365 Multi-Geo şu anda şu bölgelerde ve ülkelerde sunulmaktadır:

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

## <a name="getting-started"></a>Başlarken

Multi-geo ile çalışmaya başlama için şu adımları izleyin:

1. Multi-Geo Özelliklerini bu hizmet _planına eklemek için hesap Microsoft 365_ üzerinde çalışabilirsiniz. Gereken lisans sayısını eklemeniz için size yol sağlarlar. Multi-Geo özelliği en az 250 farklı aylık abonelikle EA Microsoft 365 kullanılabilir.

   Multi-Geo'da Microsoft 365 başlamadan önce Microsoft'un multi-geo desteği Exchange Online kiracınızı yapılandırması gerekir. Bu tek seferlik yapılandırma işlemi, Microsoft 365 planında *Multi-Geo Capabilities'i* sipariş ettikten ve kiracıda lisanslar gösterdikten sonra tetiklenir. Kiracınız her iş yükünün yapılandırma sürecini tamamlandıktan [](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) sonra Microsoft 365 ileti merkezinde iş yüküne özgü bildirimler alırsınız ve sonra da Çok Coğrafi Özellikli Özellik özelliklerinizi yapılandırmaya Microsoft 365 kullanmaya başlayabilirsiniz. Multi-Geo desteği için kiracıyı yapılandırmak için gereken süre kiracıdan kiracıya değişir, ancak çoğu kiracı özellik lisanslarının alındıktan sonra bir ay içinde biter. Daha büyük veya daha karmaşık kiracılar, yapılandırma işlemini tamamlamak için daha fazla zaman gerektirmektedir. Özel kiracınız için gereken ayrıntıları almak için lütfen hesap ekibine ulaşın.

2. Çok [coğrafi ortamınızı planlama makalelerini okuyun](plan-for-multi-geo.md).

3. Çok coğrafi [ortamı yönetme ve kullanıcılarının](administering-a-multi-geo-environment.md) bu [ortamı nasıl deneyimleyeceklerini öğrenin](multi-geo-user-experience.md).

4. Multi-Geo'da Microsoft 365 hazır olduğunda, [kiracınızı multi-geo için yapılandırın](multi-geo-tenant-configuration.md).

5. [Arama ayarlama](configure-search-for-multi-geo.md).

## <a name="see-also"></a>Ayrıca bkz.

[Multi-Geo in Exchange Online and OneDrive](https://Aka.ms/GoMultiGeo)

[OneDrive ve SharePoint Online’da Multi-Geo Özellikleri](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md)

[Multi-Geo Capabilities in Exchange Online](multi-geo-capabilities-in-exchange-online.md)

[Teams ortamda en iyi deneyimi sağlar](/microsoftteams/teams-experience-o365odb-spo-multi-geo)