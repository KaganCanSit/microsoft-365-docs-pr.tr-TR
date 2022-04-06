---
title: Sistem gereksinimleri İş için Microsoft Defender
description: İş için Microsoft Defender lisans, donanım ve yazılım gereksinimleri
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/01/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 9fd082160640c239424ec75ff58c695a0175d630
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634943"
---
# <a name="microsoft-defender-for-business-requirements"></a>İş için Microsoft Defender gereksinimleri

> [!IMPORTANT]
> İş için Microsoft Defender 1 Mart 2022 [Microsoft 365 İş Ekstra'den](../../business-premium/index.md) itibaren tüm müşterilere sunulmaktadır. Tek başına bir abonelik olarak İş için Defender önizlemededir ve istekte etmek için buraya kaydolan müşterilere ve IT İş Ortaklarına [aşamalı](https://aka.ms/mdb-preview) olarak tüm müşterilere aşamalı olarak tüm müşterilere aşamalı olarak ve tek başına bir abonelik sunar. Önizleme bir [dizi senaryo içerir ve](mdb-tutorials.md#try-these-preview-scenarios) düzenli olarak özellikler ekleycek.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

Bu makalede, iş gereksinimleri İş için Microsoft Defender.

## <a name="what-to-do"></a>Ne yapmalı?

1. [Gereksinimleri gözden geçirme ve bunları karşıla](#review-the-requirements)

2. [Sonraki adımlarınıza devam edin](#next-steps).

>
> **Bir dakika mı kaldı?**
> Lütfen bu konuda <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">kısa anket İş için Microsoft Defender</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

## <a name="review-the-requirements"></a>Gereksinimleri gözden geçirme

Aşağıdaki tabloda, bu gereksinimleri yapılandırmak ve kullanmak için temel İş için Microsoft Defender. <br/><br/>

| Gereksinim | Açıklama |
|:---|:---|
| Abonelik | Microsoft 365 Business Premium <br/>--- veya ---<br/>İş için Microsoft Defender (tek başına; şu anda önizlemede). <br/><br/> Bkz[. İş için Microsoft Defender](get-defender-business.md).<br/><br/>Birden çok aboneliğiniz varsa, en yüksek aboneliğin öncelikli olduğunu unutmayın. Örneğin, 2. Plan 2 Uç Nokta için Microsoft Defender i (satın alınan veya deneme aboneliği) satın alıyorsanız ve İş için Microsoft Defender Defender ile Uç Nokta Planı 2 için Defender'ı alırsınız. Bu durumda, İş için Defender deneyimini görmeyersiniz.  |
| Datacenter | Aşağıdaki veri merkezi konumlarından biri: <br/>- Avrupa Birliği <br/>- Birleşik Krallık <br/>- Birleşik Devletler |
| Kullanıcı hesapları | Kullanıcı hesapları yeni hesapta Microsoft 365 yönetim merkezi ([https://admin.microsoft.com](https://admin.microsoft.com))<br/><br/>İş için Microsoft Defender lisansların atandığı Microsoft 365 yönetim merkezi<br/><br/>Bu görevle ilgili yardım almak için bkz [. Kullanıcı ekleme ve lisans atama](../../admin/add-users/add-users.md). |
| İzinler  | Genel Yönetici İş için Microsoft Defender olmak gerekir.<br/><br/>Kullanıcı portalına Microsoft 365 Defender, kullanıcıların Azure [AD'de şu rollerden birinin atanmış olması](mdb-roles-permissions.md) gerekir: <br/>- Güvenlik Okuyucu<br/>- Güvenlik Yöneticisi<br/>- Genel Yönetici<br/><br/>Daha fazla bilgi edinmek için bkz[. Daha fazla bilgi edinmek için İş için Microsoft Defender](mdb-roles-permissions.md). |
| Tarayıcı gereksinimleri | Microsoft Edge Veya Google Chrome |
| İşletim sistemi | Cihazları aynı İş için Microsoft Defender yönetmek için, cihazlarınız aşağıdaki işletim sistemlerinden birini çalıştırmaktadır: <br/>- Windows 10 Business veya sonrası <br/>- Windows 10 Professional veya sonrası <br/>- Windows 10 Enterprise veya sonrası <br/><br/>[KB5006738'in yüklü](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) olduğundan emin olun. <br/><br/>Cihazları zaten Microsoft Intune 'da (veya Microsoft Endpoint Manager) yönetiyorsanız, bu cihazları İş için Defender'a  edinebilirsiniz. |

> [!NOTE]
> [Azure Active Directory izinlerini ve cihaz gruplarını yönetmek için otomatik ad (Azure AD)](/azure/active-directory/fundamentals/active-directory-whatis) kullanılır. Azure AD, İş için Defender aboneliğinize dahildir. 
> - Denemenizi başlatmadan Microsoft 365 aboneliğiniz yoksa, etkinleştirme işlemi sırasında Azure AD sizin için hazır olur. 
> - Defender For Business denemenizi Microsoft 365 başka bir Microsoft 365 aboneliğiniz varsa, var olan Azure AD hizmetinizi kullanabilirsiniz. 
> - İşletmeler için [Defender Microsoft 365 İş Ekstra'i](../../business/index.yml) kullanırken Microsoft Intune. 

## <a name="next-steps"></a>Sonraki adımlar

Şu şekilde devam edin:

- [2. Adım: İş için Microsoft Defender'de roller ve izinler atama](mdb-roles-permissions.md) 
 