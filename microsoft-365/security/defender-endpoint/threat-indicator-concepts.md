---
title: Uç Nokta için Microsoft Defender'da tehdit zekası kavramlarını anlama
description: Organizasyonunız için özel tehdit uyarıları oluşturun ve Uç Nokta için Microsoft Defender'da tehdit İstihbaratı ile ilgili kavramları öğrenin
keywords: tehdit zekası, uyarı tanımları, tehdit göstergeleri, güvenlik uyarıları, güvenlik göstergeleri,
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 440f788c4adb757013611bb05621b4eb4f4e9715
ms.sourcegitcommit: 348f3998a029a876a9dcc031f808e9e350804f22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "62996596"
---
# <a name="understand-threat-intelligence-concepts"></a>Tehdit zekası kavramlarını anlama

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)



> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-threatindicator-abovefoldlink)

Gelişmiş siber güvenlik saldırıları, birden çok karmaşık kötü amaçlı olaydan, özniteliklerden ve bağlamsal bilgilerden oluşur. Bu etkinliklerden hangilerinin şüpheli olarak nitelendirildiklerinin belirlenmesi ve bunlara karar vermek zor bir görev olabilir. Sektörünize özgü bilinen öznitelikler ve anormal etkinlikler hakkında bilginiz, gözlemlenen bir davranışı ne zaman şüpheli olarak çağıracağız konusunda bilgi sahibi olmak için temel bir özelliktir.

Microsoft 365 Defender ile, organizasyon uygulamanıza yönelik olası saldırı etkinliklerini takip etmeye yardımcı olacak özel tehdit uyarıları oluşturabilirsiniz. Şüpheli olayları bayrakla bayrakla kesip ipucunu bir araya durdurabilir ve muhtemelen bir saldırı zincirini durdurarak devam edeceğiz. Bu özel tehdit uyarıları yalnızca kuruluşta görünür ve izlemesi için ayarmış olduğunu olayları bayrakla bayraklar.

Özel tehdit uyarıları oluşturmadan önce, uyarı tanımlarının ve güvenlik göstergelerinin (IOC) ardındaki kavramları ve aralarındaki ilişkiyi bilmek önemlidir.

## <a name="alert-definitions"></a>Uyarı tanımları
Uyarı tanımları, olası siber güvenlik saldırılarının erken ipucunu belirlemek için toplu olarak kullanılmaktadır. Bu göstergeler tipik olarak bir saldırgan tarafından bir saldırının amacına başarıyla elde etmek için  alınan etkinliklerin, karakteristiklerin ve eylemlerin bir bileşimidir. Öznitelik bileşimlerinin izlenmesi, saldırılara karşı bir görüş noktası kazanmada ve bir saldırgan amacına ulaşmadan önce olay zincirini engellemede çok önemlidir.

## <a name="indicators-of-compromise-ioc"></a>Güvenlik göstergeleri (IOC)
IOC'ler tek tek bilinen ve bir ağ veya cihazın zaten ihlal edildi olduğunu belirten kötü amaçlı olaylardır. Uyarı tanımlarının aksine, bu göstergeler ihlal kanıtı olarak kabul edilir. Bu tür konuşmalar genellikle bir saldırı gerçekleştirildikten ve exfiltration gibi bir hedefe ulaştıktan sonra görülür. İTA'ları izlemek araştırma araştırmaları sırasında da önemlidir. Bir saldırı zinciriyle müdahale etmek mümkün olamsa da, gelecekteki olası saldırılar için daha iyi savunma oluşturmak için bu göstergeleri toplamak yararlı olabilir.

## <a name="relationship-between-alert-definitions-and-iocs"></a>Uyarı tanımları ile IOC'ler arasındaki ilişki
Microsoft 365 Defender Uç Nokta için Microsoft Defender bağlamında, uyarı tanımları IOS için kapsayıcılardır ve belirli bir IOC eşleşmesi için yükseltilmiş meta veriler de içinde olmak üzere uyarıyı tanımlar. Uyarı tanımlarının bir parçası olarak çeşitli meta veriler sağlanır. Saldırının uyarı tanımı adı, önem derecesi ve açıklama gibi meta veriler diğer seçeneklerle birlikte sağlanır.

Her IOC; türü, değeri ve eylemine dayalı olarak, hangi beton algılama mantığını tanımlar ve hangi yöntemin eşleşmesi olduğunu belirler. Algılamanın konsolda nasıl uyarı olarak görüntüleniyor olduğunu tanımlayan belirli bir uyarı tanımıyla Microsoft 365 Defender gerekir.

İşte bir IOC örneği:
- Tür: Sha1
- Değer: 92cfceb39d57d914ed8b14d0e37643de0797ae56
- Eylem: Eşittir

IOC'lerin uyarı tanımları ile bire bir ilişkisi vardır, örneğin uyarı tanımının buna karşılık gelen birçok IOC'si olabilir.


## <a name="related-topics"></a>İlgili konular
- [Göstergeleri yönetme](manage-indicators.md)
