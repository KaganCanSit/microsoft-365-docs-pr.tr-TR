---
title: İleti Şifreleme Görüntüleyicisi Uygulamasını kullanımdandandan kullanımdandan kullanımdan
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
description: Uygulama Office 365 İleti Şifrelemesi Görüntüleyicisi uygulaması, Android ve Apple mağazalarından 2018'de kaldırılmıştır.
ms.openlocfilehash: 0eded17f4da5347e1f1a88031a780cee5f8b1dee
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983230"
---
# <a name="deprecating-message-encryption-viewer-app"></a>İleti Şifreleme Görüntüleyicisi Uygulamasını kullanımdandandan kullanımdandan kullanımdan

15 Ağustos 2018 tarihinde Android ve Apple Office 365 İleti Şifrelemesi OME) Görüntüleyicisi mobil uygulamasını kaldırdık. Bu Office 365 İleti Şifrelemesi Görüntüleyicisi uygulaması, Apple ve Android telefonlarda OME'nin önceki sürümüyle şifrelenmiş e-posta iletilerini ve ekleri okumak için gereklidir. OME Görüntüleyicisi uygulamasını kaldırmanın dışında, OME'nin önceki sürümünde başka bir değişiklik yapıyoruz.
  
## <a name="changes-from-august-2018"></a>Ağustos 2018'den itibaren yapılan değişiklikler

Eylül 2017'de duyurularak, kullanıcıların mobil uygulamaya gerek kalmadan kuruluş içinden veya dışından herkese şifreli ve korumalı iletiler göndereyyler için yeni bir [Office 365 İleti Şifrelemesi](https://aka.ms/ome2017) sürümü yayınlandı. O zamandan beri ek özellikler ekledik:
  
- [Yalnızca şifrele şablonu](https://aka.ms/encryptonly)

- [Eklerin şifresini çözmek için denetim](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Admin-control-for-attachments-now-available-in-Office-365/ba-p/204007)

Bu değişiklikle, kullanıcılar 1 Ağustos'Office 365 İleti Şifrelemesi Görüntüleyicisi mobil uygulamayı indirmeyecek. Sonuç olarak, posta alıcıları bazı Android ve Apple mobil cihazlarında OME'nin önceki sürümüyle şifrelenmiş iletileri okuy ediyor olabilir. Bununla birlikte, bu iletileri kişisel bilgisayarlarda (masaüstü tarayıcıları üzerinden) okuyabilirler. Uygulamayı indiren kullanıcılar uygulamayı kullanmaya devam edecektir.
  
## <a name="why-this-change-was-made"></a>Bu değişiklik neden yapıldı?

OME'nin yeni sürümü, artık korumalı e-posta iletilerini ve ekleri okumak için mobil uygulama gerektirmeyecek. Yeni OME özelliklerini kullanan müşteriler korumalı iletiyi mobil Outlook olmayan müşteriler de korumalı iletileri tarayıcıda iletiyi mobilde 2.
  
Kullanıcıların mobil uygulamayı indirmelerini gerektiren uygulamalar, müşterilerin korunan iletileri görüntülemesi için engelli bir engeldir. Yeni Office 365 İleti Şifrelemesi özellikleri, daha iyi bir mobil deneyim sunar.
  
## <a name="can-i-still-use-the-previous-version-of-office-365-message-encryption"></a>Office 365 İleti Şifrelemesi'in önceki sürümünü kullanmaya devam Office 365 İleti Şifrelemesi

Office 365 İleti Şifrelemesi'in önceki sürümü şu anda kullanımdan kullanımdan kullanım dışı olmayacaktır; bununla birlikte, kullanıcıların korumalı iletileri doğrudan okuma olanağı da dahil olmak üzere hassas verileri herkes ve herhangi bir cihazda şifrelemeyi ve korumayı kolaylaştıran yeni Office 365 İleti Şifrelemesi sürümünde önemli geliştirmeler yaptık.  (Outlook, mobil ve web). 
  
## <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>Bu değişiklike hazırlanmak için ne yapabilirim?

Organizasyonunız şu anda OME Görüntüleyicisi uygulaması gerektiren alıcılara şifreli ekler gönderiyorsa, belgelerinizi ve eğitim kaynaklarınızı güncelleştirmeniz gerekir.
  
Kurum gerek yeni Exchange gelişmiş özelliklerden yararlanabilmek için, posta akışı kurallarını ve geçerli sürümünü kullanmak üzere var olan E-posta akış kurallarını güncelleştirmenizi öneririz. Yeni OME özelliklerini bir kez ayardan sonra, alıcıların mobil cihazlarda şifrelenmiş iletileri okumak için OME Görüntüleyicisi uygulamasına ihtiyacı olmayacaktır.
  
Microsoft, yeni OME özelliklerine, kurum için uygun olduğu anda bir plan yapmanızı önerir. Yönergeler için bkz[. Yeni özellik Office 365 İleti Şifrelemesi ayarlama](set-up-new-message-encryption-capabilities.md). Yeni becerilerin nasıl ilk kez çalışması hakkında daha fazla bilgi almak için [bkz. Office 365 İleti Şifrelemesi](ome.md).
  

