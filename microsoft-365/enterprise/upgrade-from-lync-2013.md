---
title: Lync Server 2013'ten yükseltme
ms.author: serdars
author: serdarsoysal
manager: serdars
ms.date: 11/10/2021
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
ms.collection:
- Ent_O365
search.appverid:
- MET150
f1.keywords:
- NOCSH
description: Lync Server 2013'ten yükseltme yapmak için bilgi ve kaynaklar bulun. Destek 11 Nisan 2023'te sona erer.
ms.openlocfilehash: 6d6d3baed383e85a1e97d37726ff7f1eb355e98c
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2022
ms.locfileid: "63010036"
---
# <a name="upgrading-from-lync-server-2013"></a>Lync Server 2013'ten yükseltme

Microsoft Lync Server 2013, **11 Nisan 2023'te destek sonuna ulaşacak**. Bu makalede, var olan Lync Server dağıtımınızı şirket içinde başka bir Microsoft Teams veya Skype Kurumsal için kaynaklar sağlar.

## <a name="what-is-end-of-support"></a>Destek *sonu nedir*?

Çoğu Microsoft ürünlerinin bir destek yaşam döngüsü vardır ve bu süre boyunca yeni özellikler, hata düzeltmeleri ve güvenlik düzeltmeleri gibi başka özellikler elde eder. Destek sonu tarihini tamamlanın, ürün çalışmayı durdurmaz, ancak Microsoft artık şunları sağlar:

- Ortaya çıkabilir sorunlar için teknik destek.

- Sunucunun kararlılığını ve kullanılabilirliğini etkilebilir sorunlar için hata düzeltmeleri.

- Sunucuda güvenlik ihlallerine neden olan güvenlik açıklarına yönelik güvenlik düzeltmeleri.

- Saat dilimi güncelleştirmeleri.

Bu, ürün için başka güncelleştirme, yama veya düzeltme (güvenlik yamaları/düzeltmeleri de dahil) olmayacaktır. Microsoft Desteği, destek çalışmalarını tümüyle daha yeni sürümlere kaydıracak.

## <a name="plan-ahead"></a>Devam et'i planla

Desteğin Ürün Yaşam Döngüsü sitesinde sona [erer tarihlerini kontrol edin](/lifecycle/products/lync-server-2013). Yükseltmelerinizi veya geçişlerinizi bu tarihleri unutmayın. Ürününüz listelenen *tarihte çalışmayı durdurmayacak* . Ancak, yükleme işleminize bu tarihten sonra yama olmayacak olması nedeniyle ürünün sonraki sürümüne sorunsuz bir geçiş planlamak istemeniz gerekir. Aşağıdaki tabloda sizin için kullanılabilir seçenekler listelenmiştir.

|Destek ürünü sonu|Destekleniyor|Önerilen|
|---|---|---|
|Lync Server 2013|Skype Kurumsal Sunucu 2015 veya 2019'a yükseltme|Yükseltme Microsoft Teams

## <a name="whats-next"></a>Sırada ne var?

Microsoft Teams'e yükseltmenizi öneririz. Microsoft Teams, Lync Server'ın özelliklerini genişleterek sohbeti, toplantıları, aramayı, işbirliğini, uygulama tümleştirmeyi ve dosya depolamayı tek bir arabirimde bir araya getirebilirsiniz. Teams, kullanıcıların işleri yapma yolunu kolaylaştırarak kullanıcı memnuniyetini iyileştirmeye ve iş sonuçlarını hızlandırmaya yardımcı olur. yeni yollarla iletişim kurmanız ve işbirliği Teams, kurumsal ve coğrafi engelleri ortadan kaldırabilmek, süreç ve karar verme sürecinde verimliliği artırmak için Teams'ın özelliklerini sürekli genişletiyoruz.

Microsoft Teams'a yükselte Microsoft Teams, 2015 veya 2019'Skype Kurumsal Sunucu yükseltebilirsiniz. İki ürün de 14 Ekim 2025'te destek sonuna ulaşacak. Daha fazla bilgi için aşağıdaki destek yaşam döngüsü sayfalarına bakın:

- [Skype Kurumsal Sunucu 2015 destek yaşam döngüsü bilgileri](/lifecycle/products/skype-for-business-server-2015)
- [Skype Kurumsal Sunucu 2019 destek yaşam döngüsü bilgileri](/lifecycle/products/skype-for-business-server-2019)

### <a name="upgrade-to-microsoft-teams"></a>Yükseltme Microsoft Teams

Şirket içi dağıtımdan Microsoft Teams yükseltme konusunda ayrıntılı yol gösterici bilgilerimiz var. İlk olarak, bazı önemli teknik gereksinimleri karşılarız. Karma bağlantı kurarak kullanıcılarınızı başka kullanıcılarla birlikte Teams. [Karma bağlantı planla](/SkypeForBusiness/hybrid/plan-hybrid-connectivity) , karma ortamı ayarlama hakkında genel bir bakış sağlar. Makale her ne kadar temel Skype Kurumsal kavramlar Lync Server 2013 için de geçerlidir. Lync Server [](/SkypeForBusiness/hybrid/plan-hybrid-connectivity#server-version-requirements) 2013'e özgü ayrıntılar için sunucu sürüm gereksinimleri bölümüne bakın.

Ayrıca Lync Server 2013 dağıtımınızı tamamen güncel olmasını da sağlamalısınız. Lync [Server 2013](https://support.microsoft.com/topic/updates-for-lync-server-2013-a2a042ac-79f0-2665-7453-0a541fb25164) için en son güncelleştirmelerin listesini yayımlarız. Bununla birlikte, aşağıdaki güncelleştirme, yükseltme işleminin önceden Microsoft Teams:

- [Lync Server 2013 için Eylül 2021 toplu güncelleştirmesi 5.0.8308.1149,](https://support.microsoft.com/topic/september-2021-cumulative-update-5-0-8308-1149-for-lync-server-2013-core-components-6755903a-fc9a-44d2-b835-2a6d01f14043) Çekirdek Bileşenler: Bu güncelleştirme, cmdlet'in Canlı Kimlik doğrulamasını OAuth `Move-CSUser` kimlik doğrulama protokolüyle değiştirir ve bu protokol şirket içi kullanıcıları posta Microsoft Teams.

lync'te kullanıcı deneyimi Microsoft Teams Lync'ten çok daha zengin ve üstün olsa da, çok ciddi derecede farklıdır. Bu nedenle, kullanıcıların kısa sürede benimsenmesi için organizasyon ve kullanıcılarınızı hazırlamanız Microsoft Teams. Kurumlarınızı hazırlama, organizasyon yükseltmenizi planlama ve başarılı bir şekilde Teams hakkında zengin bilgiler elde edildi.

**Teknik bilgileri, eğitim kaynaklarını [](/MicrosoftTeams/upgrade-skype-teams)**, Ignite oturumlarının bağlantılarını, kullanılabilir yardım kaynaklarını, örnek olay incelemelerini ve daha fazlasını içeren Teams yükseltme portalımızda başlamanızı öneririz.

:::image type="content" source="../media/teams-upgrade-portal.png" alt-text="Yükseltme portalının Teams ekran görüntüsü":::

### <a name="upgrade-to-skype-for-business-server"></a>Yükseltme Skype Kurumsal Sunucu

Bu Skype Kurumsal Sunucu, yükseltmeyi seçtiğiniz sürüme bağlı olarak farklı olur. Skype Kurumsal Sunucu 2015, Lync Server 2013'ten yerinde yükseltmeyi destekler. Öte yandan, bir veya birden çok yeni sunucu ekleyerek önce Skype Kurumsal Sunucu 2019'a yükseltmek için, bir veya birden çok yeni sunucu ekleme yoluyla Lync Server 2013 yüklemenize Skype Kurumsal Sunucu 2019'ü tanıtmanız ve ardından eklenen yeni 2019 sunucularına aktarmanız gerekir.

Her ürün için geçerli destek aşamasının şu anda geçerli destek aşaması olduğunu dikkate alın: Skype Kurumsal 2019 ana destektedir ve Skype Kurumsal 2015 şu anda genişletilmiş destektedir.  Bu nedenle, Skype Kurumsal Sunucu 2019'a yükseltmenizi öneririz. Temel ve genişletilmiş destek arasındaki fark hakkında daha fazla bilgi edinmek için Sabit Yaşam Döngüsü [İlkesi'ne bakın](/lifecycle/policies/fixed).

Her yükseltme senaryosu hakkında ayrıntılı bilgi için aşağıdaki kaynaklara bakın.

- [Skype Kurumsal Sunucu 2019'a yükseltme](/skypeforbusiness/migration/migration-to-skype-for-business-server-2019)
- [Skype Kurumsal Sunucu 2015'e yükseltme](/skypeforbusiness/deploy/upgrade-to-skype-for-business-server)
