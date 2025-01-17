---
title: Yönetime ve API'lere genel bakış
ms.reviewer: ''
description: Aşağıdaki yönetim araçları ve API kategorileri hakkında bilgi Uç Nokta için Microsoft Defender
keywords: ekleme, api, siem, rbac, access, portal, tümleştirme, araştırma, yanıt, varlıklar, varlık, kullanıcı bağlamı, uygulama bağlamı, akış
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
MS.technology: mde
ms.custom: api
ms.openlocfilehash: cc73531540222791eb39eeca74570f34ff78a1b7
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469789"
---
# <a name="overview-of-management-and-apis"></a>Yönetime ve API'lere genel bakış

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mgt-apis-abovefoldlink)


Uç nokta için Defender, müşterilerin platforma kolayca benimseyesini sağlamak için çok çeşitli seçenekleri destekler.

Müşteri ortamlarının ve yapılarının farklılık gösterebiliyor olması, çeşitli müşteri gereksinimlerine uyacak şekilde esneklik ve ayrıntılı denetimle Uç Nokta için Defender oluşturuldu.

## <a name="endpoint-onboarding-and-portal-access"></a>Uç nokta ekleme ve portal erişimi

Cihaz ekleme, istemci cihazları için Microsoft Endpoint Manager Microsoft Intune ve sunucu cihazları için Microsoft Defender ile tam olarak tümleştirilmiştir; bu uygulama yapılandırma, dağıtım ve izlemenin tam 24 bit deneyimi sunar. Buna ek Uç Nokta için Microsoft Defender, cihaz grup ilkesi için kullanılan diğer üçüncü taraf araçlarını da desteklemektedir.

Uç Nokta için Defender, portala erişimi olan kullanıcıların rol tabanlı erişim denetimi (RBAC) esnekliği aracılığıyla neler göreceği ve neler göreceği üzerinde daha fazla denetim sağlar. RBAC modeli, güvenlik ekipleri yapısının tüm çeşitlerini destekler:

- Küresel olarak dağıtılmış kuruluşlar ve güvenlik ekipleri
- Katmanlı model güvenlik işlemleri ekipleri
- Tek merkezi global güvenlik işlemleri ekipleriyle tam olarak ayrık bölümler

## <a name="available-apis"></a>Kullanılabilir API'ler

En Uç Nokta için Microsoft Defender çözümü, tümleştirmeye hazır bir platformun üzerine üzerine yerleşiktir.

Uç Nokta için Defender, veri ve eylemlerinin büyük bir fazlasını bir dizi programlı API aracılığıyla ortaya çıkarır. Bu API'ler, iş akışlarını otomatikleştirmenize ve Uç nokta özellikleri için Defender'a dayalı yenilikler yapmaya olanak sağlar.

:::image type="content" source="images/mdatp-apis.png" alt-text="Uç Nokta için Microsoft Defender'de kullanılabilen API ve tümleştirme" lightbox="images/mdatp-apis.png":::

Uç Nokta API'leri için Defender üç olarak gruplandı:

- Uç Nokta için Microsoft Defender API'leri
- Ham veri akışı API'si
- SIEM tümleştirmesi

## <a name="microsoft-defender-for-endpoint-apis"></a>Uç Nokta için Microsoft Defender API'leri

Uç Nokta için Defender, kullanıcılar veya SaaS uygulamaları bağlamında erişime olanak sağlayan, standart Bir Azure AD tabanlı kimlik doğrulama ve yetkilendirme modeli aracılığıyla ortaya çıkar, yapılandırılmış, açık ve kullanımı kolay bir modelde verilerin ve becerilerin ortaya çıkar olduğu katmanlı bir API modeli sunar. API modeli varlıkları ve özellikleri tutarlı bir şekilde göstermek için tasarlanmıştır.

Uç nokta API'leri için Defender'a hızlı bir genel bakış için bu videoyu izleyin.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4d73M]

**Araştırma API'si** Uç Nokta için Defender'ın zenginliğini ortaya çıkarır; hesaplanan veya "profilli" varlıkları (örneğin, cihaz, kullanıcı ve dosya) ortaya çıkarır ve genellikle bir varlığa ilişkin bir davranışı açıklayan ayrık olaylar (örneğin, süreç oluşturma ve dosya oluşturma) ortaya çıkar ve araştırma arabirimleri aracılığıyla verilere sorgu tabanlı erişime olanak sağlar. Daha fazla bilgi için bkz [. Desteklenen API'ler](exposed-apis-list.md).

Yanıt **API'si** hizmette ve cihazlarda işlem yapma olanağı sunar; müşterilerin göstergeleri en iyi şekilde yönetmesine, ayarları yönetmesine, uyarı durumunu yönetmesine ve ayrıca cihazları ağdan ayırmak, dosyaları karantinaya almak gibi programlı olarak cihazlar üzerinde yanıt eylemleri yapmalarına olanak tanır.

## <a name="raw-data-streaming-api"></a>Ham veri akışı API'si

Uç nokta ham veri akışı API'si için Defender, müşterilerin tek bir veri akışı içinde gerçek zamanlı etkinlikleri ve uyarıları tek bir veri akışı içinde teslim etmelerine olanak sağlayarak düşük gecikme süresi ve yüksek aktarım hızı teslim mekanizması sağlar.

Uç Nokta için Defender olay bilgileri, uzun vadeli veri bekletme için doğrudan Azure depolama alanına gönderilir veya görselleştirme hizmetleri Azure Event Hubs ek veri işleme altyapılarının kullanımına yönelik olarak kullanılır.

Daha fazla bilgi için bkz. [Ham veri akışı API'si](raw-data-export.md).

Yeni Akış MICROSOFT 365 DEFENDER API'si, cihaz etkinliklerine ek olarak e-posta ve uyarı olaylarını da içerir.
Daha fazla bilgi için bkz[. Microsoft 365 Defender API'si](../defender/streaming-api.md).

## <a name="siem-api"></a>SIEM API

Güvenlik bilgileri ve olay yönetimi (SIEM) tümleştirmesini etkinleştirerek, SIEM çözümlerinizi kullanarak veya doğrudan REST API'sini algılamalara bağlanarak algılamaları Microsoft 365 Defender algılamaları çekmenize olanak sağlar. Bu, önceden doldurulmuş değerlere sahip SIEM bağlayıcı erişim ayrıntıları bölümünü etkinleştirir ve Azure Active Directory (Azure AD) kiracınız altında bir uygulama oluşturulur. 

## <a name="related-topics"></a>İlgili konular

- [Api'lere Uç Nokta için Microsoft Defender erişme](apis-intro.md)
- [Desteklenen API'ler](exposed-apis-list.md)
- [Teknik iş ortağı fırsatları](partner-integration.md)
