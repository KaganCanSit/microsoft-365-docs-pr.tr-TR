---
title: Hizmet planı özel durumları
description: Standart hizmet planında özel durumlar nasıl talep edilebilir?
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 8069a899b9992a0e8b941b6ac53cd2f230a6174a
ms.sourcegitcommit: 559df2c86a7822463ce0597140537bab260c746a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2022
ms.locfileid: "63015271"
---
# <a name="exceptions-to-the-service-plan"></a>Hizmet planı özel durumları

Microsoft Yönetilen Masaüstü, hepsi kullanıcılara [güvenli, üretken](device-policies.md) ve keyifli bir deneyim sağlamak için tasarlanmış bir genel [](../working-with-managed-desktop/config-setting-overview.md)cihaz listesi, standart cihaz ayarları, uygulama gereksinimleri ve bazı yapılandırılabilir ayarlar sağlar.

Hizmet her zaman, olduğu gibi hizmette kalmak en iyisidir. Bununla birlikte, hizmetin bazı ayrıntılarının tam olarak kurumnizin ihtiyaçlarına uymayy olabileceğinin farkındaız. Hizmeti bir şekilde değiştirmeniz gerekirse, bu değişiklikleri talep etmek için aşağıdaki işlemleri takip etmek önemlidir.

## <a name="types-of-exceptions"></a>Özel durum türleri

Bunun tek istisnası Microsoft Yönetilen Masaüstü yapılandırmasını ekleme veya bu yapılandırmada değişiklik yapmaktır. Örnekler, USB bağlantı noktaları yapılandırmasından yeni cihaz sürücüsünün dağıtımına kadar değişebilir. Çeşitli özel durumları aşağıdaki gibi grupladık:

| Özel durum türleri | Açıklama |
| ----- | ----- |
| Üretkenlik yazılımı | Kullanıcıların ihtiyacı olan ön plan yazılımı, uygulama gereksinimlerine [göre kısıtlanmıştır](mmd-app-requirements.md). |
| VPN'ler & aracıları | Cihazın veya ağın güvenliğini sağlamak, izlemek veya davranışını değiştirmek için kullanılan yazılım. |
| Dijital deneyim izleme | Bir kullanıcının cihazına rapor etmek için kullanılan verileri izlemek için kullanılan yazılım. |
| Donanım ve yazılım sürücüleri | Cihaz sürücüleri, uygulama gereksinimleriyle [kısıtlanmıştır](mmd-app-requirements.md). |
| İlkeler | Windows 10 cihazda Kurumlar için Microsoft 365 Uygulamaları ayarları değiştirin veya değiştirin. |
| Cihazlar | Microsoft Yönetilen Masaüstü cihaz listesinde olmayan [cihazlar](device-list.md). |
| Diğer | Diğer alanlarda ele alınan bir şey yok. |

## <a name="request-an-exception"></a>Bir özel durum talep

Bir değişiklik isteği oluşturarak istekleri Microsoft Yönetilen Masaüstü Yöneticisi portalı üzerinden gönderin. Bu ayrıntıların dahil olduğundan emin olun:

| Değişiklik isteği ayrıntısı | Açıklama |
| ----- | ----- |
| Muaflama türü | Ne tür bir özel durumdur? (önceki [tabloya bakın](#types-of-exceptions)) |
| Gereksinim | Özel durum için belirli iş gereksinimi nedir? |
| Teklif | İş isteğiniz hangi çözümü talep ediyor? |
| Zaman çizelgesi | Bu özel durumun ne kadar süreyle devam istemeniz gerekir? |

## <a name="how-we-assess-an-exception-request"></a>Bir özel durum isteğini nasıl değerlendiriz?

Özel durum isteklerini gözden geçir sunduğumuzda, bu etmenleri şu sırayla değerlendiririz:

1. Microsoft Yönetilen Masaüstü'ne yönelik olarak tüm cihazlara dağıtan bazı uygulama ve ilkeler olumsuz değildir. İsteğiniz bu uygulamaları ve ilkeleri etkilemez. Daha fazla bilgi için bkz. [Cihaz yapılandırması](device-policies.md).
2. Bir kullanıcının işini yapmaları için gereken kısıtlı üretkenlik yazılımı büyük olasılıkla onaylanır.
3. Microsoft teknolojisini kullanarak gereksiniminizi karşılıyor olabiliriz, büyük olasılıkla üç ile 12 ay arasında bir özel durum geçiş süresi için isteğinizi onaylarız. Geçiş süresi projenin kapsamına bağlıdır.
4. Microsoft teknolojisini kullanarak gereksiniminizi karşılamıyorsanız, büyük olasılıkla isteğinizi Temel koşullardan birini ihlal etmediği sürece [onaylarız](#key-conditions).  

Bu ilkeler, Standart şablonumuzdan sapmaları takip ederken Microsoft Yönetilen Masaüstü'nin her zaman sizin ihtiyaçlarınıza uygun olmasını sağlar.

## <a name="key-conditions"></a>Temel koşullar

Bu koşullardan herhangi birini ihlal etmeyerken özel durumları gözden geçir ederiz:

- Bunun dışında, sistem güvenliğini olumsuz etkilemesi gerekir.
- Bunun dışında tutularak Microsoft Yönetilen Masaüstü işlemleri veya desteği için önemli bir ücrete neden olmaz.
- Bunun bir özel durumu, örneğin çekirdek modunun kilitlenmesi veya kilitlenmesi nedeniyle sistem kararlılığını etkilemez.
- Bu değişiklik, hizmeti çalıştırmamızı veya temel Microsoft Yönetilen Masaüstü teknolojisiyle çakışmamızı kısıtlamaz.
- Bunun dışında, kullanıcı deneyimini kişiselleştirmek (görev çubuğunda veya Görev çubuğunda değişiklik Başlat menüsü söz konusu değildir.

Bu koşullar gelecekte değişebilir. Bu tür değişiklikler olursa, bu koşulların yürürlüğe girecekleri önceden 30 gün önceden uyarıda bulunan bir bildirim sağlaruz.  Microsoft Yönetilen Masaüstü onaylanan bir özel durumu karşılamak için alternatif bir yol sağlarsa, Microsoft Yönetilen Masaüstü bunun özel durumu desteklediği şekilde değiştirerek müşteriye bunu bildirecektir.

## <a name="revoking-approval-for-an-exception"></a>Bir özel durum için onayı iptal

İstenen bir özel durum onaylandıktan ve dağıtıldıktan sonra, ilk başta değişikliği onaylamız ile ortaya çıkar olmayan temel koşulları ihlal eden sorunlar keşfederiz. Bu durumda, özel durum için onayı iptal etmek zorunda olabiliriz.

Özel durum için onayı iptal etmemiz gerekirse, bunu Microsoft Yönetilen Masaüstü yönetim portalını kullanarak size bildiracağız. İlk bildirimden itibaren, özel durumu kaldırmak için 90 gün süre vardır; bu özel durum, cihazlar artık Microsoft Yönetilen Masaüstü hizmet düzeyi sözleşmelere bağlı değildir.

Size kesin bir zaman çizelgesine göre birkaç bildirim göndeririz. Ancak, ciddi bir olay veya tehdit, özel durumla ilgili kararlarımızın zaman çizelgesini değiştirmemizi gerekli görüyor olabilir. Sizin izniniz olmadan *bir* özel durumu kaldırmayız. Öte yandan, iptal edilmiş bir özel durum söz konusu cihaz artık hizmet düzeyi sözleşmemize bağlı olmayacaktır. Aşağıdaki tablo, size göndeririz bildirimlerin zaman çizelgesidir:

| Bildirim türü | Açıklama |
| ----- | ----- |
| İlk bildirim | İlk bildirimde aşağıdaki bilgileri sağlaruz: <ul><li>Neden iptal burada olduğuyla ilgili bilgi.</li><li>Size atmanızı önerimiz işlemler.</li><li>Bu eylemlerin son tarihi.</li><Li>Kararın caziplik içinde yer aldığına karar için takip etmek istediğiniz adımlar.</li></ul> <br>Bu bildirim, özel durumun tüm cihazlardan kaldırılması için 90 gün önceden gerçekleşir. |
| İkinci bildirim (30 gün sonra) | İlk bildirimde sağlanan bilgilerin aynısını içeren ikinci bir bildirim sağlaruz. |
| Üçüncü bildirim (ilk bildirimden 60 gün sonra) | İlk bildirimde sağlanan bilgilerle birlikte üçüncü bir bildirim sağlaruz. |
| Son uyarı (90 günlük son günden bir hafta önce) | İlk bildirimde sağlanan bilgilerle birlikte dördüncü bir bildirim sağlaruz. |
| İlk bildirimden 90 gün sonra| Microsoft Yönetilen Masaüstü hizmet düzeyi anlaşmaları, iptal edilen özel durumlara sahip cihazlar için artık geçerli değildir. Herhangi bir anda, kararı zorlar ve yükseltme, yapılandırma değişiklikleri veya yazılım değişikliği gibi dikkate alınması gereken ek bilgiler silebilir. |
