---
title: Giden teslim havuzları
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ac11edd9-2da3-462d-8ea3-bbf9dbc6f948
ms.collection:
- M365-security-compliance
description: Teslim havuzlarının, veri merkezlerindeki e-posta sunucularının itibarını Microsoft 365 öğrenin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 273d105ca600face4d79d70fc1622dfce8bf9f5e
ms.sourcegitcommit: 601ab9ad2b624e3b5e04eed927a08884c885c72a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2022
ms.locfileid: "64403855"
---
# <a name="outbound-delivery-pools"></a>Giden teslim havuzları

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

E-posta sunucuları Microsoft 365 istenmeyen posta göndermeye geçici olarak neden olabilir. Örneğin, şirket içi e-posta kuruluşunda kötü amaçlı veya kötü amaçlı bir istenmeyen posta saldırısı, şirket içi postayı Microsoft 365 veya hesaplarda Microsoft 365 güvenliği ihlal ediyor. Ayrıca, saldırganlar iletileri yayın ve iletme yoluyla göndererek algılamayı Microsoft 365 dener.

Bu senaryolar, etkilenen veri merkezi sunucularının Microsoft 365 üçüncü taraf engellenen listelerde görünmesine neden olabilir. Bu engellenenler listesi kullanan hedef e-posta kuruluşları, bu hedef e-posta Microsoft 365 reddeder.

## <a name="high-risk-delivery-pool"></a>Yüksek riskli teslim havuzu

IP adreslerimizin engellenmiş olması için, Microsoft 365 veri merkezi sunucularından gelen ve istenmeyen posta olduğu belirlenen tüm iletiler yüksek riskli teslim havuzu _üzerinden gönderilir_.

Yüksek riskli teslim havuzu, yalnızca "düşük kaliteli" iletiler (örneğin, istenmeyen posta ve geri çıktı) göndermek için kullanılan, giden e-posta için ayrı bir IP [adres havuzudur](backscatter-messages-and-eop.md). Yüksek riskli teslim havuzunun kullanımı, giden e-postanın istenmeyen posta göndermesi için normal IP adres havuzunun önlenmesine yardımcı olur. Giden e-posta için normal IP adres havuzu "yüksek kaliteli" ileti gönderme itibarını koruyarak bu IP adresinin IP engellenen listelerde görünme olasılığını azaltır.

Yüksek riskli teslim havuzunda IP adreslerinin IP engelleme listelerine yerleştiril olasılığı hala aynı kalır, ancak bu tasarım sayesindedir. Hedeflenen alıcılara teslim garanti edilmeyecektir, çünkü birçok e-posta kuruluşu yüksek riskli teslim havuzundan ileti kabul etmez.

Daha fazla bilgi için bkz. [Giden istenmeyen postaları denetleme](outbound-spam-controls.md).

> [!NOTE]
> Kaynak e-posta etki alanının A kaydı veya genel DNS'de tanımlanmış MX kaydı olmayan iletiler, istenmeyen posta veya gönderme sınırı yok durumuna bakılmaksızın her zaman yüksek riskli teslim havuzu yoluyla yönlendirilmez.
>
> Aşağıdaki sınırları aşan iletiler engellenir, böylece yüksek riskli teslim havuzu üzerinden gönderilmezler:
>
> - [Hizmetin gönderme sınırları](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options).
> - [Gönderenlerin posta göndermesi](configure-the-outbound-spam-policy.md) kısıtlanmış durumda olan giden istenmeyen posta ilkeleri.

### <a name="bounce-messages"></a>Geri dönen iletiler

Giden yüksek riskli teslim havuzu tüm teslim edililmeyen raporların (NDR'ler, geri dönen iletiler, teslim durumu bildirimleri veya DSN'ler olarak da bilinir) teslimi yönetir.

NDR'lerdeki bir dalgalanmanın olası nedenleri şunlardır:

- Hizmeti kullanan müşterilerden birini etkileyen,pozma kampanyası.
- Dizin toplama saldırısı.
- İstenmeyen posta saldırısı.
- Bir sss e-posta sunucusu.

Tüm bu sorunlar, hizmet tarafından işlenen NDR sayısının aniden artmasına neden olabilir. Çoğu zaman, bu NDR'ler diğer e-posta sunucuları ve hizmetlere (geri çıktı çıktısı olarak da bilinir _[) istenmeyen posta olarak görünür](backscatter-messages-and-eop.md)_.

### <a name="relay-pool"></a>Geçiş havuzu

Bazı senaryolarda Microsoft 365 aracılığıyla iletilen veya iletilene iletiler özel bir geçiş havuzu kullanılarak gönderilir, çünkü hedef iletileri Microsoft 365 olarak değerlendirmez. Otomatik iletme veya e-postayı dışarı aktarmanın yasal ve geçersiz senaryoları olduğundan bu e-posta trafiğini yalıtmak çok Microsoft 365. Yüksek riskli teslim havuzuna benzer şekilde, geçişli posta için ayrı bir IP adresi havuzu kullanılır. Bu adres havuzu yayımlanmaz çünkü sık değişebilir ve bu havuz, yayımlanacak SPF kaydının bir parçası Microsoft 365.

Microsoft 365 iletilen iletiyi güvenli bir şekilde sunmiz için özgün gönderenin yasal olduğunu doğrulamamız gerekir.

İletilen veya geçiş yapılan ileti, geçiş havuzunun kullanımından kaçınmak için aşağıdaki ölçütlerden birini karşılamalı:

- Giden gönderen kabul edilen bir [etki alanındadır](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- İleti geldiğinde SPF Microsoft 365.
- Mesaj gönderici etki alanında DKIM, geldiğinde Microsoft 365.

Giden sunucu IP'sinde (geçiş havuzu 40.95.0.0/16 aralığında yer alır) bakarak veya giden sunucu adına bakarak (adı "rly" olan) bir iletinin geçiş havuzu aracılığıyla gönderildiğini öğrenebilirsiniz.

Gönderenin kimliğini doğrulaymiz durumlarda, alıcı e-posta sisteminin iletilene iletinin güvenilir bir kaynaktan olduğunu an önce ansına yardımcı olmak için Gönderen Yeniden Yazma Düzeni'ne (SRS) kullanıyoruz. Bunun nasıl çalıştığını ve gönderen etki alanının, başka bir programda Gönderen Yeniden Yazma [Düzeni'ne (SRS)](/office365/troubleshoot/antispam/sender-rewriting-scheme) kimlik doğrulamayı geçeci olduğundan emin olmak için neler Office 365.

DKIM'nin çalışması için, etki alanı gönderirken DKIM'yi etkinleştirmeye emin olun. Örneğin, fabrikam.com E-contoso.com parçasıdır ve kuruluşun kabul edilen etki alanlarında tanımlanır. İletiyi gönderen kişi sender@fabrikam.com, DKIM'nin devre dışı olması fabrikam.com. buradan DKIM kullanarak özel etki alanınıza [gönderilen giden e-postayı doğrulama hakkında bilgi edinebilirsiniz](use-dkim-to-validate-outbound-email.md).

Özel etki alanları eklemek için, Etki alanına [etki alanı ekleme sayfasındaki Microsoft 365](../../admin/setup/add-domain.md).

Etki alanınıza yönelik MX kaydı üçüncü taraf bir hizmeti veya şirket içi bir e-posta sunucusunu kullanıyorsa, Bağlayıcılar için Gelişmiş [Filtreleme'ye gerek vardır](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors). İyileştirilmiş Filtreleme, SPF doğrulamanın gelen posta için doğru olduğunu ve geçiş havuzu üzerinden e-posta gönderilmesini önlemeyi sağlar.
