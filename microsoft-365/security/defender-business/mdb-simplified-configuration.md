---
title: İş için Microsoft Defender'da basitleştirilmiş yapılandırma işlemi
description: İş için Microsoft Defender'da basitleştirilmiş yapılandırma işlemi hakkında bilgi
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/01/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: f7f6b7d7f4c6af004e019c8f45aab4ae3d9b9554
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63323689"
---
# <a name="the-simplified-configuration-process-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'da basitleştirilmiş yapılandırma işlemi

> [!IMPORTANT]
> İş için Microsoft Defender 1 Mart 2022 Microsoft 365 İş Ekstra müşterilere sunulmaktadır. Tek başına bir abonelik olarak İş için Defender önizlemededir ve istekte etmek için buraya kaydolan müşterilere ve IT İş Ortaklarına [aşamalı](https://aka.ms/mdb-preview) olarak tüm müşterilere aşamalı olarak tüm müşterilere aşamalı olarak ve tek başına bir abonelik sunar. Önizleme bir [dizi senaryo içerir ve](mdb-tutorials.md#try-these-preview-scenarios) düzenli olarak özellikler ekleycek.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

İş için Microsoft Defender, özellikle küçük ve orta ölçekli işletmeler için tasarlanmış basitleştirilmiş bir yapılandırma işlemi içerir. Bu deneyim, ilk günden kuruluş cihazlarınızı korumak üzere tasarlanmış sihirbaza benzer bir deneyim ve varsayılan ilkelerle cihazları ekleme ve yönetme çalışmalarından çıkar. **Basitleştirilmiş yapılandırma işlemini öneririz; bununla birlikte, bu seçenekle sınırlı değildirsiniz**.

Kuruluş cihazlarına ekleme ve güvenlik ayarlarını yapılandırma söz konusu olduğunda, çeşitli deneyimler arasında seçim yapabilirsiniz: 

- İş için Microsoft Defender'da basitleştirilmiş yapılandırma işlemi (*önerilir*) 
- Microsoft Endpoint Manager içeren Microsoft Intune
- Cihazları yönetmek için Microsoft olmayan çözümünüz 

## <a name="what-to-do"></a>Ne yapmalı?

1. [Kurulum ve yapılandırma seçeneklerinizi gözden geçirme](#review-your-setup-and-configuration-options)

2. [İş için Defender'da basitleştirilmiş yapılandırma işlemi hakkında daha fazla bilgi](#why-we-recommend-using-the-simplified-configuration-process)

3. [Sonraki adımlarınıza devam edin](#next-steps)

>
> **Bir dakika mı kaldı?**
> Lütfen İş için <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">Microsoft Defender ile ilgili kısa ankete göz atyın</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

## <a name="review-your-setup-and-configuration-options"></a>Kurulum ve yapılandırma seçeneklerinizi gözden geçirme

Aşağıdaki tabloda her deneyim açık almaktadır:
<br/><br/>

| Portal deneyimi  | Açıklama  |
|---------|---------|
| Yeni portalda basitleştirilmiş Microsoft 365 Defender deneyimi ([https://security.microsoft.com](https://security.microsoft.com)) <br/>(*Bu çoğu müşteri için önerilen seçenektir*)  | Basitleştirilmiş yapılandırma deneyimi, İş için Defender'ı ayarlamanıza ve yapılandırmanıza yardımcı olan sihirbaza benzer bir deneyim içerir. Basitleştirilmiş yapılandırma, aynı zamanda kuruluş cihazlarınızı ilk günden korumanıza yardımcı olacak varsayılan güvenlik ayarlarını ve ilkeleri de içerir. <br/><br/>Bu deneyimde, güvenlik ekipleriniz şu Microsoft 365 Defender kullanır: <br/>- İş için Defender'ı ayarlama ve yapılandırma <br/>- Olayları görüntüleme ve yönetme<br/>- Tehditleri yanıtlama ve azaltmak<br/>- Raporları görüntüleme<br/>- Bekleyen veya tamamlanmış eylemleri gözden geçirme <br/><br/> Bu portal, kuruluşun güvenlik ayarları ve tehdit koruması özellikleri için tek alışverişte bulundurabilirsiniz. Hızlı ve verimli bir şekilde başlamanıza yardımcı olacak basitleştirilmiş bir deneyim elde edersiniz. Daha fazla bilgi edinmek için bkz [. İş için Microsoft Defender'ı ayarlamak için sihirbazı kullanma](mdb-use-wizard.md).<br/><br/>Ayrıca, ayarlarınızı düzenleyebilir veya yeni ilkeler tanımlayarak kuruluş  ihtiyaçlarını karşılar.<br/><br/>Daha fazla bilgi edinmek için bkz [. İş için Microsoft Defender'da cihaz ilkelerini görüntüleme veya düzenleme](mdb-view-edit-policies.md). |
| Microsoft Endpoint Manager yönetim merkezi ([https://endpoint.microsoft.com](https://endpoint.microsoft.com))  | Microsoft Endpoint Manager uygulamaları Microsoft Intune için bulut tabanlı bir mobil cihaz yönetimi (MDM) ve mobil uygulama yönetimi (MAM) sağlayıcısı olan Uygulamaları içerir. <br/><br/>Birçok kuruluş Intune'i cep telefonları, tabletler ve dizüstü bilgisayarlar gibi cihazlarını yönetmek için kullanır. Daha fazla bilgi edinmek için [bkz Microsoft Intune cihazlarınız için bir MDM ve MAM sağlayıcısıdır](/mem/intune/fundamentals/what-is-intune). <br/><br/>Zaten Microsoft Intune veya Microsoft Endpoint Manager kullanıyorsanız, o çözümü kullanmaya devam edersiniz. |
| Microsoft olmayan cihaz yönetimi çözümünüz  | Microsoft dışı bir üretkenlik ve cihaz yönetim çözümü kullanıyorsanız, bu çözümü İş için Defender ile kullanmaya devam edebilirsiniz. <br/><br/>Cihazlar İş için Defender'a geldiğinde, cihaz portalında durumları ve Microsoft 365 Defender. Daha fazla bilgi edinmek için bkz. [Uç Nokta için Defender için Ekleme ve yapılandırma aracı seçenekleri](../defender-endpoint/onboard-configure.md).<br/><br/>Microsoft dışı bir cihaz yönetim çözümü kullanıyorsanız, o çözümü kullanmaya devam edebilirsiniz. |


## <a name="why-we-recommend-using-the-simplified-configuration-process"></a>Neden basitleştirilmiş yapılandırma işleminin kullanılması önerilir?

**İş için Microsoft Defender'da çoğu müşteri için basitleştirilmiş yapılandırma işleminin** kullanılması önerilir. Basitleştirilmiş yapılandırma işlemi, özellikle küçük ve orta ölçekli işletmeler için kolaylaştırılmıştır. İş için Defender, daha derin teknik uzmanlık veya özel bir bilgiye gerek kalmadan, ilk günden kuruluş cihazlarınızı korumanıza yardımcı olmak üzere tasarlanmıştır. Varsayılan güvenlik ayarları ve ilkeleriyle, cihazlarınız işe alındıklarında korunur.

İş için Defender, güvenlik ayarlarınızı yapılandırmada size zaman ve emek tasarrufu sağlarken güçlü bir koruma sağlamak üzere tasarlanmıştır. Yeni portalda yer alan düzenli Microsoft 365 Defender, cihazları ekleme ve yönetmeyi basit hale geliyor. Buna ek olarak, varsayılan ilkeler de dahil edilir; böylelikle, kuruluş cihazları ekli olduğu anda korunur. Varsayılan ayarlarınızı olduğu gibi saklayabilirsiniz veya iş ihtiyaçlarınıza uygun değişiklikler yapabilirsiniz. Ayrıca, gerektiğinde cihazları yönetmek için yeni ilkeler de ebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

- [İş için Microsoft Defender'ı ayarlama ve yapılandırma](mdb-setup-configuration.md)

- [İş için Microsoft Defender'ı kullanmaya başlama](mdb-get-started.md)