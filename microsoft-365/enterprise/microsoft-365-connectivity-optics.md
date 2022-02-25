---
title: Microsoft 365 Bağlantı Optikleri
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: Bu makale, Bağlantı Optikleri Microsoft 365 bilgi içerir.
ms.openlocfilehash: c1ee14966f13ff50ff809ebbdf4c578bf949e956
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62959930"
---
# <a name="microsoft-365-connectivity-optics"></a>Microsoft 365 Bağlantı Optikleri

Bu belgede, Microsoft'un normalde müşteri cihazlarından top kullandığı bağlantılarından bazıları ve Microsoft'un bu tür verileri kullanarak hizmet teslimi analiz edip en iyi duruma getirmek, mümkün olan en iyi son kullanıcı deneyimini değerlendirebilir ve sağlamak için kullandığı yöntemlerden bazıları açık almaktadır.

Bağlantı optikleri genellikle son kullanıcı cihazlarına yüklenilebilen veya tarayıcılardan erişilebilen Microsoft uygulamalarından toplanır. Microsoft hizmetleri içinde isteğe bağlı Microsoft 365, burada açıklanan bağlantılarının birçoğu, Microsoft'un müşteriler için kullanılabilirlik ve performans taahhüdmızı karşılaması konusunda ayrılmazdır. Bu optikler, Microsoft'un son kullanıcılarla Microsoft hizmet uç noktaları arasındaki bağlantı yolu sorunlarını hemen algılamasına ve yanıtlamasına olanak sağlar. Bu optik işaretlerden bazıları, Merkezi'nde Ağ bağlantısı [gibi özellikleri etkinleştirmek Microsoft 365 Yönetici kullanılır](office-365-network-mac-perf-overview.md).

## <a name="optics-collected-from-microsoft-365-applications"></a>Microsoft 365 uygulamalarından toplanan optikler

Optikler şu anda tüm cihazlarda seyrek örnekleme kullanılarak toplanır. Genel olarak, belirli bir yinelemeyle ölçülmeyecek olan optik ve hedef (hizmet uç noktaları) kümesi, Microsoft tarafından hizmet gereksinimlerine göre yapılandırılır ve örnekleme amacıyla rastgele gerçekleştirilen.
Her optik koleksiyon aralığında, ölçü kaynağı olarak son kullanıcı cihazı ve ölçü hedefi olarak bir Microsoft 365 hizmet uç noktası kullanılarak aşağıdaki ölçümlerden biri veya birden fazlası toplanabilir:

| Ölçü | Açıklama |
| --- | --- |
| Gecikme süresi | HTTP aracılığıyla küçük bir dosyayı almak için alınan süre |
| Aktarım hızı | HTTP yoluyla daha büyük bir dosyayı alma süresi, aşırı bant genişliği tüketimini önlemek için nadiren ölçülür |
| Gidiş Dönüş Süresi (RTT) | ICMP ping |
| İzlemeroute | ICMP izleme yönlendirmesi |

Her ölçü normal olarak aşağıdaki öğeleri de içeren ek bilgilerle ilişkilendirildi:

| Öğe | Açıklama |
| --- | --- |
| Kiracı Kimliği | Müşterinin son kullanıcı cihazıyla ilişkilendirilmiş Azure Active Directory kiracısına yönelik benzersiz tanımlayıcı. |
| Monitör Kimliği | Ölçümü gerçekleştiren istemci uygulaması tarafından sağlanan isteği (Outlook, OneDrive, vb.) gerçekleştiren uygulamanın tanımlayıcısı. |
| İstek Kimliği | Microsoft tarafından sağlanan ölçü yapılandırmasında belirtilen ölçü isteğinin tanımlayıcısı. |
| Uzak IP | İstemciden hizmet uç noktasına yönelik istekle ilişkilendirilmiş maskelenmiş kaynak IP'ler, ölçü isteğini alan ve Microsoft'un görünür olduğu istemci kaynağı IP adresine bağlı olarak hesaplanan sunucu tarafından sağlanır. Microsoft'un tek tek cihazları veya kullanıcıları tanımlayamay olduğundan emin olmak için IP adresleri, IPv4 adresleri için /24 alt ağın veya IPv6 adresleri için /48 alt ağın maskesini kullanır. |
| Ön uç | Microsoft 365 isteği alan sunucu tarafından sağlanan bir hizmet ön uç tanımlayıcısıdır. |
| Uç nokta | Microsoft 365 isteği alan sunucu tarafından sağlanan bir hizmet uç noktası konumudur. |
| Sertifika Verilen | Hizmet uç noktasına bağlanırken sunulan SSL sertifikasının "sertifika veren" özelliği. Bu, sertifikayı hizmet uç noktasına veren sertifika yetkilisini gösterir. |
| Sertifika Başparmak Yazdır | Sertifikanın genel olarak erişilebilir benzersiz bir tanımlayıcısı olan hizmet uç noktasına bağlanırken sunulan SSL sertifikasının "sertifika thumbprint" özelliği. |
| Enlem/Boylam | Son kullanıcı cihazıyla ilgili özet enlem ve boylam. Bu yalnızca son kullanıcı cihazlarında Windows Konum Hizmeti'ni etkinleştirmiş olan ve aynı zamanda bu bilgilerin Microsoft 365 [portalında toplanır](office-365-network-mac-perf-overview.md#1-enable-windows-location-services). |

## <a name="measurement-process"></a>Ölçü işlemi

Her son kullanıcı cihazı normal olarak belirli bir ölçü (yüklü uygulamalar için) veya tarayıcı sayfalarını yükleme eylemlerini temel alarak (web tabanlı uygulamalar için) gerçekleştirecek. Ölçü etkinlikleri arka plan işlemleri olarak gerçekleştirilir ve kullanıcılar için uygulama deneyimini etkilemez. Bu sürecin belirli bir yinelemesi için kullanılacak ölçü türleri ve hedefler rastgele sıralandırıldıklarından, müşteriler kendi bölgelerinde yer alan Microsoft hizmeti uç noktalarına yapılan istekler ile normal uygulama bağlantısı için son kullanıcı cihazları tarafından yapılan isteklere benzer. Buna ek olarak, müşteriler kendi yerel bölgelerinin dışında olan Microsoft hizmeti uç noktalarına yapılan istekler de fark edeyleyler. Müşteri ve ISS altyapısında yapılan değişiklikler Microsoft'un istek yönlendirme ilkelerimizi sürekli olarak değiştirmesini gerektirey olduğundan, bu ölçümler çoğunlukla müşteri isteklerinin en iyi hizmet uç noktasına en iyi yönlendirmesini sağlamak için kullanılır. Microsoft'un trafiği en iyi hizmet uç noktasına nasıl yönlendir olduğu ve ağ bağlantısına genel bakış Microsoft 365 hizmetleriyle Microsoft 365 [hakkında daha fazla bilgi edinebilirsiniz](microsoft-365-networking-overview.md).

## <a name="service-endpoints"></a>Hizmet uç noktaları

Bu ölçülerin hedefleri olarak kullanılan Microsoft hizmeti uç noktaları, yayımlanan URL'ler [Office 365 IP adresi aralıkları içinde yer almaktadır](urls-and-ip-address-ranges.md). Bu bağlantı bağlantılarının koleksiyonu için ek hizmet uç noktalarına erişim gerekmez.
