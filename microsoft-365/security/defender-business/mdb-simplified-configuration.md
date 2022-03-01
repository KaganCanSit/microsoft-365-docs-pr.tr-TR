---
title: İş için Microsoft Defender'da (önizleme) basitleştirilmiş yapılandırma işlemi
description: İş için Microsoft Defender'da (önizleme) basitleştirilmiş yapılandırma işlemi hakkında bilgi
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 1bd11102636696f7aafe781af6d16ae078212d8a
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63016670"
---
# <a name="the-simplified-configuration-process-in-microsoft-defender-for-business-preview"></a>İş için Microsoft Defender'da (önizleme) basitleştirilmiş yapılandırma işlemi

> [!IMPORTANT]
> İş için Microsoft Defender şu anda önizlemede ve istekte etmek için buraya kaydolan müşterilere ve IT [İş Ortaklarına aşamalı](https://aka.ms/mdb-preview) olarak aşamalı olarak aşamalı olarak sunulmaktadır. Önümüzdeki haftalarda bir ilk müşteri ve iş ortağı kümesi sunuyoruz ve genel kullanılabilirlik durumuna kadar önizlemeyi genişleteceğiz. Önizlemenin bir dizi ilk [senaryoyla başlat olacağını](mdb-tutorials.md#try-these-preview-scenarios) ve düzenli olarak özellikler ekley olacacaz.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

İş için Microsoft Defender (önizleme), özellikle küçük ve orta ölçekli işletmeler için tasarlanmış basitleştirilmiş bir yapılandırma işlemi içerir. Bu deneyim, ilk günden kuruluş cihazlarınızı korumak üzere tasarlanmış sihirbaza benzer bir deneyim ve varsayılan ilkelerle cihazları ekleme ve yönetme çalışmalarından çıkar. **Basitleştirilmiş yapılandırma işlemini öneririz; bununla birlikte, bu seçenekle sınırlı değildirsiniz**.

Kuruluş cihazlarına ekleme ve güvenlik ayarlarını yapılandırma söz konusu olduğunda, çeşitli deneyimler arasında seçim yapabilirsiniz: 

- İş için Microsoft Defender'da (önizleme) basitleştirilmiş *yapılandırma işlemi (önerilen*) 
- Microsoft Endpoint Manager içeren Microsoft Intune
- Cihazları yönetmek için Microsoft olmayan çözümünüz 

## <a name="what-to-do"></a>Ne yapmalı?

1. [Kurulum ve yapılandırma seçeneklerinizi gözden geçirme](#review-your-setup-and-configuration-options)
2. [Basitleştirilmiş yapılandırma işlemi hakkında daha fazla bilgi edinmek için Defender for Business (önizleme)](#why-we-recommend-using-the-simplified-configuration-process)
3. [Sonraki adımlarınıza devam edin](#next-steps)

## <a name="review-your-setup-and-configuration-options"></a>Kurulum ve yapılandırma seçeneklerinizi gözden geçirme

Aşağıdaki tabloda her deneyim açık almaktadır:
<br/><br/>

| Portal deneyimi  | Açıklama  |
|---------|---------|
| Yeni portalda basitleştirilmiş Microsoft 365 Defender deneyimi ([https://security.microsoft.com](https://security.microsoft.com)) <br/>(*Bu çoğu müşteri için önerilen seçenektir*)  | Basitleştirilmiş yapılandırma deneyimi, kuruluş cihazlarınızı ilk günden korumanıza yardımcı olacak varsayılan güvenlik ayarlarını ve ilkelerini içerir. Bu deneyimde, güvenlik ekipleriniz şu Microsoft 365 Defender kullanır: <br/>- İş için Defender'ı ayarlama ve yapılandırma (önizleme) <br/>- Olayları görüntüleme ve yönetme<br/>- Tehditleri yanıtlama ve azaltmak<br/>- Raporları görüntüleme<br/>- Bekleyen veya tamamlanmış eylemleri gözden geçirme <br/><br/> Bu portal, kuruluşun güvenlik ayarları ve tehdit koruması özellikleri için tek alışverişte bulundurabilirsiniz. Hızlı ve verimli bir şekilde başlamanıza yardımcı olacak basitleştirilmiş bir deneyim elde edersiniz.  Ayrıca, ayarlarınızı düzenleyebilir veya yeni ilkeler tanımlayarak kuruluş  ihtiyaçlarını karşılar.<br/><br/>Daha fazla bilgi edinmek için bkz [. Microsoft Defender İş'te (önizleme) cihaz ilkelerini görüntüleme veya düzenleme](mdb-view-edit-policies.md). |
| Microsoft Endpoint Manager yönetim merkezi ([https://endpoint.microsoft.com](https://endpoint.microsoft.com))  | Microsoft Endpoint Manager uygulamaları Microsoft Intune için bulut tabanlı bir mobil cihaz yönetimi (MDM) ve mobil uygulama yönetimi (MAM) sağlayıcısı olan Uygulamaları içerir. <br/><br/>Birçok kuruluş Intune'i cep telefonları, tabletler ve dizüstü bilgisayarlar gibi cihazlarını yönetmek için kullanır. Daha fazla bilgi edinmek için [bkz Microsoft Intune cihazlarınız için bir MDM ve MAM sağlayıcısıdır](/mem/intune/fundamentals/what-is-intune). <br/><br/>Zaten Microsoft Intune veya Microsoft Endpoint Manager kullanıyorsanız, o çözümü kullanmaya devam edersiniz. |
| Microsoft olmayan cihaz yönetimi çözümünüz  | MacOS için Jamf veya Linux için Ansible gibi Microsoft dışı bir üretkenlik ve cihaz yönetim çözümü kullanıyorsanız, bu çözümü İş için Defender (önizleme) ile kullanmaya devam edebilirsiniz. <br/><br/>Cihazlar defender for Business (önizleme) sürümüne geldiğinde, cihaz durumunu ve uyarılarını Microsoft 365 Defender. Daha fazla bilgi edinmek için bkz. [Uç Nokta için Defender için Ekleme ve yapılandırma aracı seçenekleri](../defender-endpoint/onboard-configure.md).<br/><br/>Microsoft dışı bir cihaz yönetim çözümü kullanıyorsanız, o çözümü kullanmaya devam edebilirsiniz. |


## <a name="why-we-recommend-using-the-simplified-configuration-process"></a>Neden basitleştirilmiş yapılandırma işleminin kullanılması önerilir?

**Çoğu müşteri için İş için Microsoft Defender'da (önizleme) basitleştirilmiş yapılandırma** işleminin kullanılması önerilir. Basitleştirilmiş yapılandırma işlemi, özellikle küçük ve orta ölçekli işletmeler için kolaylaştırılmıştır. İş için Defender (önizleme), daha fazla teknik uzmanlık veya özel bir bilgiye gerek kalmadan, ilk günden kuruluş cihazlarınızı korumanıza yardımcı olmak için tasarlanmıştır. Varsayılan güvenlik ayarları ve ilkeleriyle, cihazlarınız işe alındıklarında korunur.


İş için Defender (önizleme), güvenlik ayarlarınızı yapılandırmada size zaman ve çabadan tasarruf ederken güçlü bir koruma sağlamak üzere tasarlanmıştır. Yeni portalda yer alan düzenli Microsoft 365 Defender, cihazları ekleme ve yönetmeyi basit hale geliyor. Buna ek olarak, varsayılan ilkeler de dahil edilir; böylelikle, kuruluş cihazları ekli olduğu anda korunur. Varsayılan ayarlarınızı olduğu gibi saklayabilirsiniz veya iş ihtiyaçlarınıza uygun değişiklikler yapabilirsiniz. Ayrıca, gerektiğinde cihazları yönetmek için yeni ilkeler de ebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

>
> **Bir dakika mı kaldı?**
> Lütfen İş için <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">Microsoft Defender ile ilgili kısa ankete göz atyın</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

- [İş için Microsoft Defender'ı (önizleme) ayarlama ve yapılandırma](mdb-setup-configuration.md)

- [İş için Microsoft Defender'ı (önizleme) kullanmaya başlama](mdb-get-started.md)