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
description: Lync Server 2013'ten yükseltecek bilgileri ve kaynakları bulun. Destek 11 Nisan 2023'de sona eriyor.
ms.openlocfilehash: 925b53d751cd559ce3ccdf28d823531021611551
ms.sourcegitcommit: 997eb64f80da99b1099daba62994c722bbb25d72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/16/2022
ms.locfileid: "66129151"
---
# <a name="upgrading-from-lync-server-2013"></a>Lync Server 2013'ten yükseltme

Microsoft Lync Server 2013 **, 11 Nisan 2023'te** destek sonuna ulaşacaktır. Bu makalede, mevcut Lync Server dağıtımınızı şirket içi Microsoft Teams veya Skype Kurumsal yükseltmenize yardımcı olacak kaynaklar sağlanır.

## <a name="what-is-end-of-support"></a>*Destek sonu* nedir?

Microsoft ürünlerinin çoğu, yeni özellikler, hata düzeltmeleri, güvenlik düzeltmeleri vb. alan bir destek yaşam döngüsüne sahiptir. Destek sonu tarihinden sonra ürün çalışmayı durdurmaz, ancak Microsoft artık şunları sağlamaz:

- Oluşabilecek sorunlar için teknik destek.

- Sunucunun kararlılığını ve kullanılabilirliğini etkileyebilecek sorunlar için hata düzeltmeleri.

- Sunucuyu güvenlik ihlallerine açık hale getirebilecek güvenlik açıklarına yönelik güvenlik düzeltmeleri.

- Saat dilimi güncelleştirmeleri.

Bu, ürün için başka güncelleştirme, düzeltme eki veya düzeltme olmayacağı anlamına gelir (güvenlik düzeltme ekleri/düzeltmeler dahil). Microsoft Desteği destek çalışmalarını daha yeni sürümlere tamamen kaydırmış olacak.

## <a name="plan-ahead"></a>Önceden planlayın

[Ürün Yaşam Döngüsü sitesinde](/lifecycle/products/microsoft-lync-server-2013) desteğin sona erdiğini gösteren tarihleri denetleyin. Bu tarihleri göz önünde bulundurarak yükseltmelerinizi veya geçişlerinizi planlayın. Ürününüzün listelenen tarihte *çalışmayı durdurmayacağını* unutmayın. Ancak bu tarihten sonra yüklemenize artık düzeltme eki uygulanmayacağından ürünün sonraki sürümüne sorunsuz bir geçiş planlamak istersiniz. Aşağıdaki tabloda kullanabileceğiniz seçenekler listelenmiştir.

|Destek sonu ürünü|Destekleniyor|Önerilen|
|---|---|---|
|Lync Server 2013|Skype Kurumsal Sunucu 2015 veya 2019'a yükseltme|Microsoft Teams yükseltme

## <a name="whats-next"></a>Sırada ne var?

Microsoft Teams yükseltmenizi öneririz. Microsoft Teams Lync Server'ın özelliklerini genişleterek sohbet, toplantılar, arama, işbirliği, uygulama tümleştirmesi ve dosya depolama özelliklerini tek bir arabirimde bir araya getirir. Teams, kullanıcıların işleri yapma şeklini kolaylaştırarak kullanıcı memnuniyetini artırmaya ve iş sonuçlarını hızlandırmaya yardımcı olur. Yeni yollarla iletişim kurmanızı ve işbirliği yapmanızı, kurumsal ve coğrafi engelleri yıkmanızı ve süreç ve karar alma sürecinde verimliliği artırmanızı sağlamak için Teams özelliklerini sürekli olarak genişletiyoruz.

Microsoft Teams yükseltemiyorsanız, Skype Kurumsal Sunucu 2015 veya 2019'a yükseltebilirsiniz. Bu ürünlerin her ikisinin de 14 Ekim 2025'te destek sonuna ulaşacağını bilmeniz gereken önemli bir planlama konusudur. Daha fazla bilgi için aşağıdaki destek yaşam döngüsü sayfalarına bakın:

- [Skype Kurumsal Sunucu 2015 destek yaşam döngüsü bilgileri](/lifecycle/products/skype-for-business-server-2015)
- [Skype Kurumsal Sunucu 2019 destek yaşam döngüsü bilgileri](/lifecycle/products/skype-for-business-server-2019)

### <a name="upgrade-to-microsoft-teams"></a>Microsoft Teams yükseltme

Şirket içi dağıtımınızdan Microsoft Teams yükseltme konusunda ayrıntılı yönergelere sahibiz. İlk olarak, bazı önemli teknik gereksinimleri ele alalım. Kullanıcılarınızı Teams taşımanızı sağlayacak karma bağlantı kurmanız gerekir. [Karma bağlantıyı planlama, karma](/SkypeForBusiness/hybrid/plan-hybrid-connectivity) ortam ayarlamaya genel bir bakış sağlar. Makale Skype Kurumsal odaklanmış olsa da, tüm kavramlar Lync Server 2013 için de geçerlidir. Lync Server 2013'e özgü ayrıntılar için [sunucu sürümü gereksinimleri](/SkypeForBusiness/hybrid/plan-hybrid-connectivity#server-version-requirements) bölümüne bakın.

Ayrıca Lync Server 2013 dağıtımınızın tamamen güncel olduğundan da emin olmanız gerekir. [Lync Server 2013 için en son güncelleştirmelerin listesini](https://support.microsoft.com/topic/updates-for-lync-server-2013-a2a042ac-79f0-2665-7453-0a541fb25164) yayımlıyoruz ancak aşağıdaki güncelleştirme, Microsoft Teams yükseltme için bir önkoşuldur:

- [Lync Server 2013, Temel Bileşenler için Eylül 2021 toplu güncelleştirmesi 5.0.8308.1149](https://support.microsoft.com/topic/september-2021-cumulative-update-5-0-8308-1149-for-lync-server-2013-core-components-6755903a-fc9a-44d2-b835-2a6d01f14043): Bu güncelleştirme, şirket içi kullanıcıları Microsoft Teams taşımak için kullanılan cmdlet için `Move-CSUser` Live ID kimlik doğrulamasını OAuth kimlik doğrulama protokolüyle değiştirir.

Microsoft Teams'daki kullanıcı deneyimi Lync'e göre çok daha zengin ve üstün olsa da, aynı zamanda önemli ölçüde farklıdır. Bu nedenle, Microsoft Teams hızlı bir şekilde benimsenmesini sağlamak için kuruluşunuzu ve kullanıcılarınızı da hazırlamanız gerekir. Kuruluşunuzu hazırlama, Teams yükseltmenizi planlama ve başarılı bir dağıtım sağlama hakkında çok sayıda bilgiye sahibiz.

Teknik bilgileri, eğitim kaynaklarını, Ignite oturumlarının bağlantılarını, kullanılabilir yardım kaynaklarını, örnek olay incelemelerini ve daha fazlasını bulabileceğiniz **[Teams yükseltme portalımızdan](/MicrosoftTeams/upgrade-skype-teams) başlamanızı öneririz**.

:::image type="content" source="../media/teams-upgrade-portal.png" alt-text="Teams yükseltme portalının ekran görüntüsü":::

### <a name="upgrade-to-skype-for-business-server"></a>Skype Kurumsal Sunucu yükseltme

Skype Kurumsal Sunucu yolu, yükseltmeyi seçtiğiniz sürüme bağlı olarak farklı olacaktır. Skype Kurumsal Sunucu 2015, Lync Server 2013'ten yerinde yükseltmeyi destekler. Öte yandan, Skype Kurumsal Sunucu 2019'a yükseltmek için öncelikle bir veya daha fazla yeni sunucu ekleyerek Lync Server 2013 yüklemenize Skype Kurumsal Sunucu 2019'un tanıtılması ve ardından işlemleri eklediğiniz yeni 2019 sunucularına aktarmanız gerekir.

Dikkate alınması gereken önemli noktalardan biri, her ürün için geçerli destek aşamasıdır: Skype Kurumsal 2019 temel destektedir ve Skype Kurumsal 2015 şu anda genişletilmiş destektedir.  Bu nedenle, Skype Kurumsal Sunucu 2019'a yükseltmenizi öneririz. Temel ve genişletilmiş destek arasındaki fark hakkında daha fazla bilgi edinmek için bkz. [Sabit Yaşam Döngüsü İlkesi](/lifecycle/policies/fixed).

Her yükseltme senaryosu hakkında ayrıntılı bilgi için aşağıdaki kaynaklara bakın.

- [Skype Kurumsal Sunucu 2019'a yükseltme](/skypeforbusiness/migration/migration-to-skype-for-business-server-2019)
- [Skype Kurumsal Sunucu 2015'e yükseltme](/skypeforbusiness/deploy/upgrade-to-skype-for-business-server)
