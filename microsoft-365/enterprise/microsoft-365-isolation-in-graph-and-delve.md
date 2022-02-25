---
title: Microsoft 365 Kiracı Yalıtım'nın Microsoft Graph Kiracı Delve
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Bu makalede, kiracı yalıtımnın kiracılığı Microsoft 365 iki Office Graph nasıl Delve.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 966f02726a2cce18e30e4d5bc7ab0beb5db51a29
ms.sourcegitcommit: 27addd4dac07926528b788215d2dcd0e46301eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2021
ms.locfileid: "62959691"
---
# <a name="microsoft-365-tenant-isolation-in-the-microsoft-graph-and-delve"></a>Microsoft 365 Kiracı Yalıtım'nın Microsoft Graph Kiracı Delve

## <a name="tenant-isolation-in-the-microsoft-graph"></a>Microsoft Graph'te Kiracı Yalıtım

Microsoft [Graph](https://developer.microsoft.com/graph), Microsoft 365 Online, Exchange Online Online, Yammer, SharePoint Skype Kurumsal, Azure Active Directory dahil olmak üzere Microsoft 365 hizmetlerinde Azure Active Directory gibi diğer hizmetlerde ve diğer hizmetlerde Microsoft hizmetleri üçüncü taraf hizmetlerde. Microsoft Graph bileşenleri tüm sistem Microsoft 365. Microsoft Graph, içerik ve etkinlik koleksiyonunu ve bu içerikler arasındaki ilişkileri de Office temsil eder. İlgili içeriğe, konuşmalara ve çevrelerine insanların bağlanması için gelişmiş makine öğrenme tekniklerini kullanır. Örneğin, SharePoint Online'daki kiracı dizininde Delve sorgularına hizmet vermek için kullanılan bir Microsoft Graph dizini vardır; SharePoint Online'daki Çözümleme İşleme Altyapısı sinyaller depolamak ve içgörüleri hesaplamak için kullanılır ve Exchange Online her kullanıcının alıcı önbelleğini kiracı çözümlemelerine giriş olarak hesaplar.

Microsoft Graph, kişiler ve belgeler gibi kurumsal nesnelerle ilgili bilgilerin yanı sıra bu nesneler arasındaki ilişkiler ve etkileşimleri de içerir. İlişkiler ve etkileşimler kenarlar olarak *temsil edildi*. Microsoft Graph kiracıya göre bölüm oluşturur; böyle kenarlar yalnızca aynı kiracıda düğümler arasında olabilir. Düğüm *;* Tekdüdüz Kaynak Tanımlayıcısı (URI), düğüm türü, erişim denetim listesi ve meta veri ve kenarlar içeren bir özellik kümesidir. Her düğümün, Ortak Bilgi Modelinde olduğu gibi modellere göre düzenlenmiş *ilişkili* meta verileri ve kenarları vardır. *Meta* veriler, düğümde depolanan ve Microsoft Veri Kaynağı'nın içinde arama, filtreleme veya çözümleme için Graph. Uç *, düğümdeki* meta verilerin ve kenarların mantıksal bir koleksiyonudur. Her facet, düğümün bir yönünü açıklar. 

Microsoft Graph verileri tek bir depoya getirmez; bunun yerine, başka bir yerde yaşayan veriler hakkında meta verileri ve ilişkileri depolar. Microsoft Graph, çeşitli veri depoları ve işleme bileşenlerinden oluşur:

- Kiracı Depolama Graph, verimli çözümleme için en iyi duruma getirilmiş toplu depolama alanı sağlar.
- Etkin İçerik Önbelleği, kullanıcı deneyimlerinin devamını sağlayan etkin düğüme ve kenarlara hızlı rastgele erişim sağlar.
- Giriş yönlendiricisi, kiracı grafiğinin iç ve dış bileşenlerinin değişikliklerini belirtir.

Her iş yükü içindeki çözümlemeler, kiracı genelindeki hesaplamalar ile ilgili öngörüler elde edin ve bunları kiracı grafiğine itin. Kiracı çözümlemesi, kiracı bir kiracıdan davranış düzenleri hakkında içgörüler üretmeye yardımcı olmak için kiracı kiracılarının tüm etkinliklerine neden olur. Örneğin, Exchange Online posta kutusu üzerinde etkili bir neden olan çözümlemelere sahip her kullanıcının alıcı önbelleğini hesaplar. Kullanıcı başına bu çözümlemeler, her bir kişi için bir *dizi RecipientCache Edge* hazırlar ve bu da kiracı grafiğine gönderilir. Bu işlem, çözümleme işlemlerinin mümkün olduğunca fazla kaynak veriye yakın olduğunu sağlar.

## <a name="tenant-isolation-in-delve"></a>Delve'de Kiracı Delve

Daha önce de belirtildiği gibi Microsoft Graph, insanların kuruluşlarında geçerli etkinlikleri keşfetmelerine ve bu etkinlikler üzerinde işbirliği yapmalarına yardımcı olan, ayrıca iş yükleri genelinde içerik ve etkinlikler üzerinden nedenler hakkında çözümlemeler yapmak için varlık odaklı bir platform Microsoft 365. Delve, Microsoft Destek Hizmetleri tarafından desteklenen ilk Graph.
Delve, Microsoft 365 ve Microsoft 365 Yammer Enterprise'tan Microsoft Microsoft 365 kullanıcılarına içerik Microsoft 365 bir web deneyimi Graph. Web deneyimi, verileri farklı panolar olarak görüntüler. Her biri Çevreme göre popüler veya  Benim tarafından değiştirildi gibi belirli *bir konu içerir*. Her alan, özet metni ve belgeden bir resim görüntülemek için birkaç belge kartından oluşur. Kart, kullanıcıların belgeyi açması veya belge için bir sayfa Yammer şeyler yapmalarını sağlar. bir Microsoft 365 kiracısı içinde her kişi için, bu kişi için en uygun belgeleri gösteren bir sayfa ve bu kişi ile etkileşim kurmak için Exchange Online veya Skype Kurumsal çağıran simgeler vardır. İş Delve Microsoft İş API'sini temel Graph, bu API'nin kiracı tabanlı yalıtlığı ile ilişkili olur.