---
title: İş planlarının Microsoft 365 el ile değiştirme
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: nalinkla, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_subscriptions
- AdminSurgePortfolio
search.appverid: MET150
description: Yeni bir abonelik satın alarak ve her iki aboneliğin de listelenmiş ve etkin olduğundan emin olarak abonelikleri el ile değiştirin.
ROBOTS: NOINDEX
ms.date: 03/17/2021
ms.openlocfilehash: d7969821cceb0864ac2ee20674e7aa67d8a12e39
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66101608"
---
# <a name="change-plans-manually"></a>Planları el ile değiştirme

## <a name="step-1-decide-how-to-change-plans"></a>1. Adım: Planları nasıl değiştireceğini belirleme

Tüm kullanıcılarınızı bir plandan diğerine değiştirmenin en iyi yolu [Yükselt sekmesini kullanmaktır](upgrade-to-different-plan.md). Bazen bu mümkün değildir. Bunun yerine planları el ile değiştirin:

- **Yükselt** sekmesi geçerli planı yükseltemediğini gösterirse.

- **Yükselt** sekmesini seçtiğinizde istediğiniz plan listelenmiyorsa.

- Tüm kullanıcılarınızı aynı şekilde yükseltmek istemiyorsanız. Bazı işletmelerin farklı planlara abone olan farklı kullanıcılara ihtiyacı vardır. Bunun için el ile değişiklik kullanın.

El ile yapılan bir değişikliğe devam etmek için bu [konudaki 2. Adım: Yeni abonelik satın alma](#step-2-buy-a-new-subscription) konusunu okuyun.

> [!IMPORTANT]
> Geçerli planınızdan daha az veriyle ilgili hizmet içeren bir plana (düşürme) geçiş yaparsanız, saklamak istediğiniz tüm verileri el ile yedeklemeniz gerekir. Daha fazla bilgi için bkz. [Planları değiştirmeden önce verileri yedekleme](back-up-data-before-switching-plans.md).

## <a name="step-2-buy-a-new-subscription"></a>2. Adım: Yeni abonelik satın alma

**Zaten satın mı alınmış?** Kullanıcıları taşımak istediğiniz bir aboneliğiniz zaten varsa, bu adımı atlayın ve 3. Adım: Bu konudaki [yeni aboneliğinizi ve lisanslarınızı denetleyin](#step-3-check-your-new-subscription-and-licenses) bölümüne gidin.

VEYA

**Yeni bir abonelik ve lisans satın alın:** Yeni [abonelik satın almak için İş aboneliği için başka bir Microsoft 365 satın alma](../try-or-buy-microsoft-365.md) bölümündeki adımları izleyin.

Kullanıcıların şu anda içinde olduğu kuruluş için bir abonelik satın aldığınızdan emin olun. Örneğin, taşımak istediğiniz kullanıcıların e-posta adreslerini denetleyin. E-posta adresleri contoso.com içeriyorsa \@, contoso.com için yeni bir abonelik satın almalısınız.
Taşımak istediğiniz her kullanıcı için bir lisans ekleyin.

## <a name="step-3-check-your-new-subscription-and-licenses"></a>3. Adım: Yeni aboneliğinizi ve lisanslarınızı denetleme

1. Yönetim merkezinde **Faturalama** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Ürünleriniz</a> sayfasına gidin.

2. **Her iki aboneliğin de listelendiğini ve etkin olduğunu doğrulayın** Kullanıcıları taşıdığınız abonelik ve kullanıcıları taşıdığınız abonelik birlikte listelenmelidir. İlk kontrol ettiğinizde yeni abonelik yoksa daha sonra yeniden deneyin. Her iki aboneliğin de etkin olup olmadığını denetleyin. [Yeni abonelik listede yok veya etkin değil](#the-new-subscription-isnt-listed-or-isnt-active).

3. **Her kullanıcı için yeterli lisansa sahip olup olmadığınızı denetleyin** Her kullanıcının aboneliğiyle eşleşen bir lisansa ihtiyacı vardır. Bu nedenle, on kullanıcıyı Microsoft 365 İş Ekstra taşımak istiyorsanız, on lisansın kullanılabilir olduğundan emin olmanız gerekir.

4. **Yeni abonelik için daha fazla lisansa mı ihtiyacınız var?**
   **Ürünleriniz** sayfasına gidin ve [daha fazla lisans satın alın](../licenses/buy-licenses.md).

> [Eski lisanslar ne olacak?](#what-about-the-old-licenses)

### <a name="the-new-subscription-isnt-listed-or-isnt-active"></a>Yeni abonelik listelenmiyor veya etkin değil

- **İki abonelik satın aldıysanız ve ikisi de burada listelenmiyorsa**, farklı kuruluşlar (farklı etki alanları için) için satın alınmış olabilir. Abonelikler kuruluş sınırlarını aşamaz.

- **Ek aboneliğiniz olduğunu biliyorsanız** ve bu abonelik burada listelenmiyorsa veya etkin değilse [Microsoft desteğini arayın](../../admin/get-help-support.md).

### <a name="what-about-the-old-licenses"></a>Eski lisanslar ne olacak?

Geçerli aboneliğin lisansları daha sonra kaldırılacaktır; o tarihten itibaren yalnızca yeni kullanıcı lisansları için ödeme yaparsınız.

## <a name="step-4-reassign-licenses"></a>4. Adım: Lisansları yeniden atama

bir Office 365 planından Microsoft 365 planına yükseltirken, tüm kullanıcıların lisans atamalarını değiştirmeniz gerekir. Planları el ile değiştirdiğinizde lisanslar otomatik olarak atanamaz.

### <a name="reassign-a-license-for-one-user"></a>Bir kullanıcı için lisansı yeniden atama

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

2. **Etkin kullanıcılar** sayfasında, lisans atamak istediğiniz kullanıcıyı seçin.

3. **Lisanslar ve Uygulamalar** sekmesinde **Lisanslar'ı** genişletin, atamak istediğiniz lisansların kutularını seçin ve ardından **Değişiklikleri kaydet'i** seçin.

### <a name="reassign-licenses-for-multiple-users-at-once"></a>Aynı anda birden çok kullanıcı için lisansları yeniden atama

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.

2. Var olan lisansları değiştirmek istediğiniz kullanıcıların adlarının yanındaki daireleri seçin.

3. Üst kısımda üç noktayı (diğer eylemler) ve ardından **Ürün lisanslarını yönet'i** seçin.

4. **Mevcut ürün lisansı atamalarını değiştir** \> **İleri**'yi seçin.

5. Bu kullanıcılara atamak istediğiniz ürünlerin iki durumlu düğmesini **Açık** konumuna getirin.

    > [!TIP]
    > - Kullanıcının kullanabileceği hizmetleri sınırlamak için, bu kullanıcı için kaldırmak istediğiniz hizmetlerin **Kapalı** konumuna geçiş yapın. Örneğin, kullanıcının Skype Kurumsal Online dışındaki tüm kullanılabilir hizmetlere erişmesini istiyorsanız, Skype Kurumsal Online hizmetinin iki durumlu düğmesini **Kapalı** konumuna geçirebilirsiniz.
    > - Seçili kullanıcıların önceki tüm lisans atamaları kaldırılacaktır.

6. **Var olan ürünleri değiştir** bölmesinin en altında **Kapat'ı Değiştir'i** \> seçin.

## <a name="step-5-cancel-subscriptions-or-remove-licenses-that-you-no-longer-need-optional"></a>5. Adım: Abonelikleri iptal etme veya artık ihtiyacınız olmayan lisansları kaldırma (İsteğe bağlı)

Tüm kullanıcıları bir abonelikten diğerine taşıdıysanız ve başlangıçtaki aboneliğe artık ihtiyacınız yoksa, [aboneliği iptal edebilirsiniz](cancel-your-subscription.md).

Yalnızca bazı kullanıcıları farklı bir aboneliğe taşıdıysanız, artık ihtiyacınız olmayan [lisansları kaldırın](../licenses/buy-licenses.md) .

## <a name="call-support-to-help-you-change-plans"></a>Planları değiştirmenize yardımcı olması için desteği arayın

[Microsoft desteğini arayın](../../admin/get-help-support.md).
