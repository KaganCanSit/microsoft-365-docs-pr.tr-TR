---
title: Microsoft 365 Bağlantı Optikleri
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: Bu makale Microsoft 365 Bağlantı Optikleri hakkında bilgi içerir.
ms.openlocfilehash: cda5fa074aa04be5fbbaff9b98360a3a2f927fc2
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090329"
---
# <a name="microsoft-365-connectivity-optics"></a>Microsoft 365 Bağlantı Optikleri

Bu belgede, Microsoft'un genellikle müşteri cihazlarından topladığı bağlantı optiklerinden bazıları açıklanmaktadır ve Microsoft'un bu tür verileri hizmet teslimini analiz etmek ve iyileştirmek ve mümkün olan en iyi son kullanıcı deneyimini değerlendirmek ve sağlamak için kullandığı yollardan bazıları açıklanmaktadır.

Bağlantı optikleri genellikle son kullanıcı cihazlarına yüklenebilen veya tarayıcılardan erişilebilen Microsoft uygulamalarından toplanır. Microsoft 365 hizmetlerindeki isteğe bağlı veri toplamanın aksine, burada açıklanan bağlantı optiklerinin çoğu Microsoft'un müşterilere yönelik kullanılabilirlik ve performans taahhüdümüzü karşıladığından emin olmak için ayrılmaz bir seçenektir. Bu optikler, Microsoft'un son kullanıcılarla Microsoft hizmet uç noktaları arasındaki bağlantı yolundaki sorunları hızla algılamasını ve yanıtlamasını sağlar. Bu optiklerden bazıları[, Microsoft 365 Yönetici Merkezi'nde Ağ bağlantısı](office-365-network-mac-perf-overview.md) gibi özellikleri etkinleştirmek için de kullanılır.

## <a name="optics-collected-from-microsoft-365-applications"></a>Microsoft 365 uygulamalarından toplanan optikler

Optikler şu anda tüm cihazlarda seyrek örnekleme kullanılarak toplanıyor. Genel olarak, belirli bir yinelemede ölçülecek belirli optik ve hedef (hizmet uç noktaları) kümesi Microsoft tarafından hizmet gereksinimlerine göre yapılandırılır ve örnekleme amacıyla rastgele oluşturulur.
Her optik toplama aralığında, ölçüm kaynağı olarak son kullanıcı cihazı ve ölçüm hedefi olarak Microsoft 365 hizmet uç noktası kullanılarak aşağıdaki ölçümlerden biri veya daha fazlası toplanabilir:

| Ölçüm | Açıklama |
| --- | --- |
| Gecikme | HTTP aracılığıyla küçük bir dosyayı almak için geçen süre |
| Verim | Http aracılığıyla daha büyük bir dosyayı almak için geçen süre, aşırı bant genişliği tüketimini önlemek için nadiren ölçülür |
| Gidiş Dönüş Süresi (RTT) | ICMP ping |
| Traceroute | ICMP izleme yolu |

Her ölçüm genellikle aşağıdaki öğeleri içerebilecek ek bilgilerle ilişkilendirilir:

| Öğe | Açıklama |
| --- | --- |
| Kiracı Kimliği | Müşterinin son kullanıcı cihazıyla ilişkili Azure Active Directory kiracısının benzersiz tanımlayıcısı. |
| İzleyici Kimliği | Ölçümü gerçekleştiren istemci uygulama tarafından sağlanan isteği oluşturan uygulamanın tanımlayıcısı (Outlook, OneDrive vb.). |
| İstek Kimliği | Microsoft tarafından sağlanan ölçüm yapılandırmasında belirtilen ölçüm isteğinin tanımlayıcısı. |
| Uzak IP | ölçü isteğini alan ve Microsoft tarafından görülebilen istemci kaynak IP adresine göre hesaplanan sunucu tarafından sağlanan, istemciden hizmet uç noktasına istekle ilişkilendirilmiş maskelenmiş kaynak IP'si. IP adresleri, Microsoft'un tek tek cihazları veya kullanıcıları tanımlayamaması için IPv4 adresleri için /24 alt ağından veya IPv6 adresleri için bir /48 alt ağından maskelenir. |
| Ön uç | ölçüm isteğini alan sunucu tarafından sağlanan hizmet ön uç tanımlayıcısını Microsoft 365. |
| Uç nokta | ölçüm isteğini alan sunucu tarafından sağlanan hizmet uç noktası konumunu Microsoft 365. |
| Sertifika Veren | Hizmet uç noktasına bağlanırken sunulan SSL sertifikasının "sertifika tarafından verilen sertifika" özelliği, sertifikayı hizmet uç noktasına veren sertifika yetkilisini gösterir. |
| Sertifika Parmak İzi | Sertifikanın genel olarak erişilebilen benzersiz tanımlayıcısı olan hizmet uç noktasına bağlanırken sunulan SSL sertifikasının "sertifika parmak izi" özelliği. |
| Enlem/Boylam | Son kullanıcı cihazının soyutlanmış enlemi ve boylamı. Bu yalnızca son kullanıcı cihazlarında konum hizmeti Windows etkinleştirmiş ve bu [bilgilerin Microsoft 365 yönetici portalında toplanmasını etkinleştirmiş olan kiracılar](office-365-network-mac-perf-overview.md#1-enable-windows-location-services) için toplanır. |

## <a name="measurement-process"></a>Ölçüm işlemi

Her son kullanıcı cihazı genellikle zamanlanmış olarak (yüklü uygulamalar için) veya tarayıcı sayfalarını yükleme eylemine (web tabanlı uygulamalar için) göre bir ölçüm gerçekleştirir. Ölçüm etkinlikleri arka plan işlemleri olarak gerçekleştirilir ve kullanıcılar için uygulama deneyimini etkilemez. Bu işlemin belirli bir yinelemesi için kullanılacak ölçüm türleri ve hedefleri rastgele olduğundan müşteriler, bölgelerindeki Microsoft hizmet uç noktalarına yapılan ve normal uygulama bağlantısı için son kullanıcı cihazları tarafından yapılan tipik isteklere benzer istekler olduğunu fark edebilir. Ayrıca müşteriler, yerel bölgelerinin dışında olan Microsoft hizmet uç noktalarına yönelik istekler fark edebilir. Bu ölçümler genellikle müşteri isteklerinin en iyi hizmet uç noktasına en iyi şekilde yönlendirilmesini sağlamak için kullanılır. Müşteri ve ISS altyapısında yapılan değişiklikler Microsoft'un istek yönlendirme ilkelerimizi sürekli olarak değiştirmesini gerektirebilir. Microsoft'un trafiği en iyi hizmet uç noktasına yönlendirmesi ve Microsoft 365 ağ bağlantısına [genel bakış](microsoft-365-networking-overview.md) bölümünde Microsoft 365 hizmetlerine bağlantıyı iyileştirme hakkında daha fazla bilgi edinin.

## <a name="service-endpoints"></a>Hizmet uç noktaları

Bu ölçümler için hedef olarak kullanılan Microsoft hizmet uç noktaları, yayımlanan [Office 365 URL'leri ve IP adresi aralıkları](urls-and-ip-address-ranges.md) içinde yer alır. Bu bağlantı optiklerinin toplanması için ek hizmet uç noktalarına erişim gerekli değildir.
