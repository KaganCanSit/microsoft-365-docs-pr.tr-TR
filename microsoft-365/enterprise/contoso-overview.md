---
title: Contoso Corporation'a Genel Bakış
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: Contoso Corporation'ın dünya çapındaki ofislerinin iş ve katman yapısını anlıyoruz.
ms.openlocfilehash: 9c14849d09dc4adb75630dffd86d00d7bc766545
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985150"
---
# <a name="overview-of-contoso-corporation"></a>Contoso Corporation'a Genel Bakış

Contoso Corporation, merkezi Paris'te olan çok uluslu bir işletmedir. Şirket 100.000'den fazla ürüne sahip bir üretim, satış ve destek kuruluşudur.

## <a name="contoso-around-the-world"></a>Dünyanın her yeri için Contoso

Şekil 1, Paris merkez ofisini ve çeşitli kıtalarda bölgesel merkez ve uydu ofislerini gösterir.

![Dünya geneli contoso ofisleridir.](../media/contoso-overview/contoso-overview-fig1.png)

**Şekil 1: Dünya geneli contoso ofisleri**
 
Contoso'da üç ofis katmanı vardır:

- Genel Müdürlük

  Contoso yönetim merkezi, Paris'in dışında bulunan ve yönetim, mühendislik ve üretim tesislerinin onlarca binasının olduğu bir kurumsal kampüstur. Tüm Contoso veri merkezleri ve İnternet iletişim durumu, Paris merkezinde yer alır.

  Merkezde 25.000 çalışan var.

- Bölgesel hub'lar

  Merkez ofisleri, yüzde 60 satış ve destek personeliyle dünyanın belirli bir bölgesinde hizmet ediyor. Her bölgesel merkez, yüksek bant genişliğine sahip bir WAN bağlantısı üzerinden Paris merkezine bağlanır.

  Bölgesel merkezlerde ortalama 2.000 çalışan vardır.

- Uydu ofisleri

  Uydu ofisleri yüzde 80 satış ve destek personeli içerir. Önemli şehirlerden veya altbölgelerden Contoso müşterileri için yerinde iletişim durumu sağlarlar. Her uydu ofisi, yüksek bant genişliğine sahip bir WAN bağlantısı üzerinden bölgesel bir merkez ile bağlantılıdır.

  Uydu ofislerinin ortalama 250 çalışan var.

Contoso iş gücünün yaklaşık %25'i mobilde çalışır. Bölgesel merkezler ve uydu ofislerinin bu çalışanlardan büyük bir oranı vardır. Yalnızca mobil çalışanlarına daha iyi destek sağlamak Contoso için önemli bir iş hedefidir.

## <a name="design-considerations-for-microsoft-365-for-enterprise"></a>Kurumsal tasarımda Microsoft 365 noktalar

Contoso IT mimarları, şirket için postanın dağıtımında aşağıdaki tasarım gereksinimi Microsoft 365 gerektirmektedir:

- Yerel düzenlemeler ve uyumluluk gereksinimlerine sahip birden çok coğrafi konum
- Yönetim merkezinde ofis ve bölgesel uygulama sunucularında iç iş hattı uygulamaları barındıran bir merkezi intranet veri merkezi
- Mevcut bir Microsoft Endpoint Configuration Manager altyapısı
- Linux, Mac ve Windows istemci bilgisayar cihazlarının karışımı
- iOS (iPhone iPad ve tabletler) ile Android akıllı telefonlar ve tabletler dahil olmak üzere kişisel ve şirkete ait mobil cihazlar karışımı
- Birçok uzak çalışan ve mobil çalışan
- Birçok iş ortağı
- Yönetmek ve güvenliğini sağlamak için çok fazla miktarda müşteri ve diğer gizli kişisel bilgi
- Ürün ve üretim ticari sırlarının tasarım belirtimleri formunda büyük miktarda yüksek değerli fikri mülkiyet

## <a name="next-step"></a>Sonraki adım

Contoso Corporation şirket içi IT [altyapısı hakkında bilgi edinmek](contoso-infra-needs.md) ve kurumsal iş ihtiyaçlarıyla ilgili olarak contoso Microsoft 365 öğrenin.

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Test laboratuvarı kılavuzları](m365-enterprise-test-lab-guides.md)
