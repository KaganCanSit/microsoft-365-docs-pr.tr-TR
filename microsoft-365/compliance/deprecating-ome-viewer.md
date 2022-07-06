---
title: OME Görüntüleyicisi uygulamasını kullanımdan kaldırma
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 6336cabb-b06e-402f-9e85-8bb9eb4ce68f
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Office 365 İleti Şifrelemesi (OME) Görüntüleyici uygulaması 2018'de Android ve Apple mağazalarından kaldırılmıştır.
ms.openlocfilehash: 2e1e0ead7d34761a3159b4b51368ea4460acb596
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630091"
---
# <a name="deprecating-message-encryption-viewer-app"></a>İleti Şifreleme Görüntüleyicisi Uygulamasını KullanımDan Kaldırma

15 Ağustos 2018'de android ve Apple mağazalarından Office 365 İleti Şifrelemesi (OME) Görüntüleyicisi mobil uygulamasını kaldırdık. Office 365 İleti Şifreleme Görüntüleyicisi mobil uygulamasının, Apple ve Android telefonlarda OME'nin önceki sürümüyle şifrelenmiş e-posta iletilerini ve eklerini okuması gerekiyordu. OME Görüntüleyicisi uygulamasını kaldırmanın dışında, OME'nin önceki sürümünde başka bir değişiklik yapmayız.
  
## <a name="changes-from-august-2018"></a>Ağustos 2018'den itibaren değişiklikler

Eylül 2017'de duyurulduğu gibi, kullanıcıların mobil uygulamanın gereksinimi olmadan kuruluş içindeki veya dışındaki herkese şifrelenmiş ve korumalı iletiler gönderebilmesi için Office 365 [İleti Şifrelemesi'nin](https://aka.ms/ome2017) yeni bir sürümünü yayımladık. O zamandan beri ek özellikler ekledik:
  
- [Yalnızca şifrele şablonu](https://aka.ms/encryptonly)

- [Eklerin şifresini çözme denetimi](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Admin-control-for-attachments-now-available-in-Office-365/ba-p/204007)

Bu değişiklikle, kullanıcılar 1 Ağustos'tan itibaren Office 365 İleti Şifreleme Görüntüleyicisi mobil uygulamasını indiremeyecek. Sonuç olarak, posta alıcıları bazı Android ve Apple mobil cihazlarında OME'nin önceki sürümüyle şifrelenmiş iletileri okuyamayabilir. Ancak, bu iletileri kişisel bilgisayarlarda (masaüstü tarayıcıları aracılığıyla) okumaya devam edebilirler. Uygulamayı zaten indirmiş olan kullanıcılar uygulamayı kullanmaya devam eder.
  
## <a name="why-this-change-was-made"></a>Bu değişikliğin nedeni

OME'nin yeni sürümü artık korumalı e-posta iletilerini ve eklerini okumak için bir mobil uygulama gerektirmez. Microsoft Purview İleti Şifrelemesi kullanan müşteriler, korumalı iletiyi Outlook Mobile'da, müşteri olmayanlar ise korumalı iletileri tarayıcıda görüntüleyebilir.
  
Kullanıcıların mobil uygulama indirmesini gerektirmek, müşterilerin korumalı iletileri görüntülemesi için bir diğer engeldir. Microsoft Purview İleti Şifrelemesi daha iyi bir mobil deneyim sağlar.
  
## <a name="can-i-still-use-the-previous-version-of-office-365-message-encryption"></a>Office 365 İleti Şifrelemesi'nin önceki sürümünü kullanmaya devam edebilir miyim?

Office 365 İleti Şifrelemesi'nin önceki sürümü şu anda kullanımdan kaldırılmayacaktır, ancak Microsoft Purview İleti Şifrelemesi kullanıcıların korumalı iletileri doğrudan Outlook'ta (masaüstü, mobil ve  web).
  
## <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Bu değişikliğe hazırlanmak için ne yapmam gerekiyor?

Kuruluşunuz şu anda OME Görüntüleyicisi uygulamasını gerektiren alıcılara şifreli ekler gönderiyorsa, belgelerinizi ve eğitim kaynaklarınızı güncelleştirmeniz gerekir.
  
Kuruluşunuzun yeni ve geliştirilmiş özelliklerden yararlanabilmesi için mevcut Exchange posta akışı kurallarını Microsoft Purview İleti Şifrelemesi kullanacak şekilde güncelleştirmenizi öneririz. Microsoft Purview İleti Şifrelemesi ayarladıktan sonra, alıcıların mobil cihazlarda şifrelenmiş iletileri okumak için OME Görüntüleyicisi uygulamasına ihtiyacı olmaz.
  
Microsoft, kuruluşunuz için makul olduğu anda Microsoft Purview İleti Şifrelemesi'e geçmek için bir plan yapmanızı önerir. Yönergeler için bkz[. Microsoft Purview İleti Şifrelemesi ayarlama](set-up-new-message-encryption-capabilities.md). önce ileti şifrelemenin nasıl çalıştığı hakkında daha fazla bilgi edinmek istiyorsanız bkz. [İleti Şifrelemesi](ome.md).
