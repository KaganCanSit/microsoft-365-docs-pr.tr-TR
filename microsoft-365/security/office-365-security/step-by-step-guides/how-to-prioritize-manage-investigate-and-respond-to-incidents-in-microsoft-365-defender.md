---
title: Microsoft 365 Defender'de Olaylara Öncelik Verme, Yönetme, Araştırma & Yanıt Verme
description: Microsoft 365 Defender tetiklenen uyarıları yönetme adımları. Otomatik araştırma ve yanıt (AIR) abonelik genelinde avlanır ve bir tehdidin etkisini ve kapsamını belirler ve bilgileri tek bir Olayda birleştirir.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: 18127cd732c0e2e1392a9c62e221dadfbd123246
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043435"
---
# <a name="prioritize-manage-investigate--respond-to-incidents-in-microsoft-365-defender"></a>Microsoft 365 Defender'da Olaylara Öncelik Verme, Yönetme, Araştırma & Yanıt Verme

Uyarılar Microsoft 365 Defender tetiklendiğinde, otomatik araştırma ve yanıt (AIR), kuruluşun aboneliğinde avlanmak, tehdidin etkisini ve kapsamını belirlemek ve yöneticilerin birden çok olayı yönetmek zorunda bırakılmaması için bilgileri tek bir Olay olarak harmanlayarak tetiklenir.

## <a name="what-youll-need"></a>İhtiyacınız olan şey

- Plan 2 veya üzerini Office 365 için Microsoft Defender
- Yeterli izinler (Güvenlik okuyucusu, güvenlik işlemleri veya güvenlik yöneticisi, ayrıca [Arama ve temizleme](../permissions-microsoft-365-security-center.md) rolü)

## <a name="prioritize--manage-incidents"></a>Olaylara öncelik & yönetme

Güvenlik portalı Olaylar sayfasına https://security.microsoft.com/incidentsgidin.

Olay sayfası yüklendiğinde, eylemleri sıralamak için sütunlara tıklayarak filtreleyebilir ve önceliklerini ayarlayabilir veya filtreler'e basarak veri kaynağı, etiketler veya durum gibi bir filtre uygulayabilirsiniz.

Artık olayları yönet düğmesiyle yeniden adlandırmayı, atamayı, sınıflandırmayı, etiketlemeyi, durumu değiştirmeyi veya açıklama eklemeyi seçebileceğiniz önceliklendirilmiş bir olay listeniz var.

Office için Microsoft Defender öğelerinin dahil olduğundan emin olmak için filtreleri kullanın.

Belirli uyarılar arıyorsanız, olay arama özelliğini kullanın (*Ad veya kimlik arayın) veya* belirli bir uyarıda uyarı kuyruğu filtrelemesini kullanmayı göz önünde bulundurun.

## <a name="investigate--respond-to-incidents"></a>Olayları Araştırma & Yanıtlama

Olay kuyruğunuzun önceliğini oluşturduktan sonra, olaylara Genel Bakış sayfasını yüklemek için araştırmak istediğiniz Olaya tıklayın. *Gözlemlenen MITRE ATT&CK teknikleri* ve *saldırının zaman çizelgesi* gibi yararlı bilgiler olacaktır.

Olay sayfasının üst kısmındaki sekmeler, etkilenen kullanıcılar, posta kutuları, uç noktalar ve et cetera gibi daha fazla ayrıntıyı keşfetmenizi sağlar.

*Kanıt ve Yanıt* sekmesi, araştırma yoluyla özgün uyarıyla ilgili olarak tanımlanan öğeleri gösterir.

Kanıt ve Yanıt içinde *Bekleyen Eylem* olarak gösterilen tüm öğeler yöneticiden onay bekliyor.  *Tüm Kanıtlar* görünümünde düzeltme durumu sütununa göre sıralama yapılması önerilir ve ardından varlık veya kümeye tıklayarak açılır menüyü yükleyebilirsiniz; burada uygunsa eylemleri onaylayabilirsiniz.

İlgili öğeleri daha fazla anlamanız gerekiyorsa, olay grafiğini kullanarak ilgili kanıt ve varlıkların görsel bağlantısını görebilirsiniz. Alternatif olarak, güvenlik olayına dahil olan varlıkların ve öğelerin daha fazlasını gösteren temel araştırmaları gözden geçirebilirsiniz.

## <a name="next-steps"></a>Sonraki Adımlar

AIR'in onay alması gereken eylem öğelerine odaklanmak istiyorsanız kuruluşunuzdaki tüm olaylardan bekleyen eylem öğeleri üzerinde işlem yapmak için *İşlem Merkezi'ni* kullanmaya başlayabilirsiniz.  

## <a name="more-information"></a>Daha Fazla Bilgi

[Microsoft 365 Defender |'de olayları yönetme Microsoft Docs](../../defender/manage-incidents.md)

[Office 365 için Microsoft Defender'de otomatik araştırma ve yanıt nasıl çalışır?](../automated-investigation-response-office.md)

[Office 365 için Microsoft Defender'de düzeltme eylemleri](../air-remediation-actions.md)