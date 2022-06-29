---
title: Microsoft 365 Multi-Geo
ms.reviewer: anfra
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
description: Bu makalede, Microsoft 365 Multi-Geo ile Microsoft 365 iletişim durumunuzu birden çok coğrafi bölgeye genişletmeyi öğrenin.
ms.openlocfilehash: 154082785b71be8fbba55e00e2df8a1a3eacb500
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66490220"
---
# <a name="microsoft-365-multi-geo"></a>Microsoft 365 Multi-Geo

Microsoft 365 Multi-Geo ile kuruluşunuz Microsoft 365 iletişim durumunu mevcut kiracınızdaki birden çok coğrafi bölgeye ve/veya ülkeye genişletebilir. Microsoft 365 Multi-Geo için Multi-National Şirketinize kaydolmak için Microsoft Hesap Ekibinize ulaşın.
  
Microsoft 365 Multi-Geo ile bekleyen verileri veri yerleşimi gereksinimlerini karşılamak için seçtiğiniz coğrafi konumlarda sağlayabilir ve depolayabilir ve aynı zamanda iş gücünüz için modern üretkenlik deneyimlerinden küresel olarak faydalanmanızı sağlayabilirsiniz.

Microsoft 365 Multi-Geo'ya giriş videosu için bkz. [SharePoint Online ve verilerinizin nerede olduğunu denetlemek için OneDrive Multi-Geo](https://www.youtube.com/watch?v=Do9U3JuROhk).

## <a name="multi-geo-architecture"></a>Multi-Geo mimarisi

Multi-Geo ortamında, Microsoft 365 kiracınız merkezi bir konumdan (Microsoft 365 aboneliğinizin ilk sağlandığı yer) ve bir veya daha fazla uydu konumundan oluşur. Çok coğrafi kiracılı bir kiracıda coğrafi konumlar, gruplar ve kullanıcı bilgileriyle ilgili bilgiler Azure Active Directory'de (Azure AD) ana veridir. Kiracı bilgileriniz merkezi olarak yönetildiğinden ve her coğrafi konuma eşitlendiğinden, şirketinizden herhangi bir kişiyi içeren paylaşım ve deneyimler küresel farkındalık içerir.

![SharePoint yönetim merkezinden çok coğrafi haritanın ekran görüntüsü.](../media/multi-geo-world-map.png)

Microsoft 365 Multi-Geo'nın performans iyileştirme için tasarlanmadığını, veri yerleşimi gereksinimlerini karşılayacak şekilde tasarlandığını unutmayın. Microsoft 365 için performans iyileştirme hakkında bilgi için bkz. [Microsoft 365 için ağ planlaması ve performans ayarlama](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) veya destek grubunuzla iletişime geçin.

## <a name="terminology"></a>Terminoloji

Microsoft 365 Multi-Geo'da kullanılan temel terimler şunlardır:

- **Merkezi konum** - kiracınızın ilk olarak sağlandığı coğrafi konum.
- **Coğrafi yönetici** - Belirtilen bir veya daha fazla uydu konumunu yönetebilen bir yönetici.
- **Coğrafi kod** - belirli bir coğrafi konum için üç harfli kod.
- **Coğrafi konum** : Exchange posta kutuları, OneDrive ve SharePoint siteleri de dahil olmak üzere verileri barındırmak için çok coğrafi bir kiracıda kullanılabilecek coğrafi konum.
- **Tercih Edilen Veri Konumu (PDL)** – Yönetici tarafından ayarlanan ve kullanıcıların Exchange posta kutusu ve OneDrive'ın sağlanması gereken coğrafi konumu gösteren bir kullanıcı özelliği. PDL, kullanıcı tarafından oluşturulan SharePoint sitelerinin nerede sağlandığını da belirler.
- **Uydu konumu** – Coğrafi olarak algılayan Microsoft 365 iş yüklerinin (SharePoint, OneDrive ve Exchange) çok coğrafi kiracıda etkinleştirildiği coğrafi konumlar.
- **Kiracı** – Bir kuruluşun Microsoft 365'te temsilidir ve genellikle kendisiyle ilişkilendirilmiş bir veya daha fazla etki alanı vardır (örneğin, contoso.com).

## <a name="licensing"></a>Lisanslama

Microsoft 365 Multi-Geo, kiracılarında en az 250 Microsoft 365 lisansına ve bu koltukların en az %5'ine sahip Kurumsal Anlaşma müşteriler için aşağıdaki Microsoft 365 abonelik planlarına bir eklenti olarak sunulur. Kullanıcı aboneliği lisansları, Multi-Geo Services lisanslarıyla aynı Kurumsal Anlaşma olmalıdır. Ayrıntılar için lütfen Microsoft hesabı ekibinize başvurun.

- Microsoft 365 F1, F3, E3 veya E5
- F3, E1, E3 veya E5 Office 365
- Exchange Online Plan 1 veya Plan 2
- OneDrive İş Plan 1 veya Plan 2
- SharePoint Online Plan 1 veya Plan 2

Kullanıcıya lisans atanırsa ve daha sonra kaldırılırsa, Teams kullanıcı sohbet verileri merkezi konuma geri taşınmak üzere kuyruğa alınır. SharePoint ve Exchange verileri taşınmaz.

## <a name="microsoft-365-multi-geo-availability"></a>Microsoft 365 Multi-Geo kullanılabilirliği

Microsoft 365 Multi-Geo şu anda şu bölgelerde ve ülkelerde sunulmaktadır:

[!INCLUDE [Microsoft 365 Multi-Geo locations](../includes/microsoft-365-multi-geo-locations.md)]

## <a name="getting-started"></a>Başlarken

Multi-geo kullanmaya başlamak için şu adımları izleyin:

1. _Microsoft 365 hizmet planında Multi-Geo Özelliklerini_ eklemek için hesap ekibinizle birlikte çalışın. Gerekli lisans sayısını eklemeniz için size yol gösterir. Multi-Geo özelliği, en az 250 Microsoft 365 aboneliğine sahip EA müşterileri tarafından kullanılabilir.

   Microsoft 365 Multi-Geo kullanmaya başlamadan önce Microsoft'un çok coğrafi destek için Exchange Online kiracınızı yapılandırması gerekir. Bu tek seferlik yapılandırma işlemi *, Microsoft 365 hizmet planında Multi-Geo Özelliklerini* sipariş ettikten ve lisanslar kiracınızda gösterildikten sonra tetiklenir. Kiracınız her iş yükü için yapılandırma işlemini tamamladıktan sonra [Microsoft 365 ileti merkezinde](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) iş yüküne özgü bildirimler alırsınız ve ardından Microsoft 365 Multi-Geo özelliklerinizi yapılandırmaya ve kullanmaya başlayabilirsiniz. Multi-Geo desteği için kiracıyı yapılandırmak için gereken süre kiracıdan kiracıya değişir, ancak çoğu kiracı özellik lisansları alındıktan sonraki bir ay içinde biter. Daha büyük veya daha karmaşık kiracılar, yapılandırma işlemini tamamlamak için daha fazla zaman gerektirebilir. Gerekli olması halinde ilgili kiracınızla ilgili ayrıntılar için lütfen hesap ekibinize başvurun.

2. [Çoklu coğrafi ortamınızı planlama'ya](plan-for-multi-geo.md) bakın.

3. [Çok coğrafi ortamı yönetme](administering-a-multi-geo-environment.md) ve [kullanıcılarınızın ortamı nasıl deneyimleyecekleri](multi-geo-user-experience.md) hakkında bilgi edinin.

4. Microsoft 365 Multi-Geo'yı ayarlamaya hazır olduğunuzda [kiracınızı çok coğrafi bölge için yapılandırın](multi-geo-tenant-configuration.md).

5. [Aramayı ayarlayın](configure-search-for-multi-geo.md).

## <a name="see-also"></a>Ayrıca bkz.

[Exchange Online ve OneDrive'da Multi-Geo](https://Aka.ms/GoMultiGeo)

[OneDrive ve SharePoint Online’da Multi-Geo Özellikleri](multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md)

[Exchange Online'da Multi-Geo Özellikleri](multi-geo-capabilities-in-exchange-online.md)

[Çok coğrafi bir ortamda Teams deneyimi](/microsoftteams/teams-experience-o365odb-spo-multi-geo)
