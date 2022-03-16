---
title: İş için Microsoft Defender gereksinimleri
description: İş için Microsoft Defender lisans, donanım ve yazılım gereksinimleri
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: d7336e06aa970ac9fc08cafcb50f8bbed040c8a8
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/16/2022
ms.locfileid: "63512314"
---
# <a name="microsoft-defender-for-business-requirements"></a>İş için Microsoft Defender gereksinimleri

> [!IMPORTANT]
> İş için Microsoft Defender 1 Mart 2022 [Microsoft 365 İş Ekstra'den](../../business-premium/index.md) itibaren tüm müşterilere sunulmaktadır. Tek başına bir abonelik olarak İş için Defender önizlemededir ve istekte etmek için buraya kaydolan müşterilere ve IT İş Ortaklarına [aşamalı](https://aka.ms/mdb-preview) olarak tüm müşterilere aşamalı olarak tüm müşterilere aşamalı olarak ve tek başına bir abonelik sunar. Önizleme bir [dizi senaryo içerir ve](mdb-tutorials.md#try-these-preview-scenarios) düzenli olarak özellikler ekleycek.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

Bu makalede, İş için Microsoft Defender gereksinimleri açıklanmıştır.

## <a name="what-to-do"></a>Ne yapmalı?

1. [Gereksinimleri gözden geçirme ve bunları karşıla](#review-the-requirements)

2. [Sonraki adımlarınıza devam edin](#next-steps).

>
> **Bir dakika mı kaldı?**
> Lütfen İş için <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">Microsoft Defender ile ilgili kısa ankete göz atyın</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

## <a name="review-the-requirements"></a>Gereksinimleri gözden geçirme

Aşağıdaki tabloda, İş için Microsoft Defender'ı yapılandırmak ve kullanmak için temel gereksinimler listelemektedir. <br/><br/>

| Gereksinim | Açıklama |
|:---|:---|
| Abonelik | Microsoft 365 Business Premium <br/>--- veya ---<br/>İş için Microsoft Defender (tek başına; şu anda önizlemede). <br/><br/> Bkz [. İş için Microsoft Defender'ı almak](get-defender-business.md).<br/><br/>Birden çok aboneliğiniz varsa, en yüksek aboneliğin öncelikli olduğunu unutmayın. Örneğin, Uç Nokta Planı 2 için Microsoft Defender'ı (satın alınan veya deneme aboneliği) alıyorsanız ve İş için Microsoft Defender alıyorsanız, Uç Nokta Planı 2 için Defender öncelikli olur. Bu durumda, İş için Defender deneyimini görmeyersiniz.  |
| Datacenter | Aşağıdaki veri merkezi konumlarından biri: <br/>- Avrupa Birliği <br/>- Birleşik Krallık <br/>- Amerika Birleşik Devletleri |
| Kullanıcı hesapları | Kullanıcı hesapları yeni hesapta Microsoft 365 yönetim merkezi ([https://admin.microsoft.com](https://admin.microsoft.com))<br/><br/>Microsoft Defender for Business lisansları aşağıdaki Microsoft 365 yönetim merkezi<br/><br/>Bu görevle ilgili yardım almak için bkz [. Kullanıcı ekleme ve lisans atama](../../admin/add-users/add-users.md). |
| İzinler  | İş için Microsoft Defender'a kaydolmak için Genel Yönetici olmak gerekir.<br/><br/>Kullanıcı portalına Microsoft 365 Defender, kullanıcıların Azure [AD'de şu rollerden birinin atanmış olması](mdb-roles-permissions.md) gerekir: <br/>- Güvenlik Okuyucu<br/>- Güvenlik Yöneticisi<br/>- Genel Yönetici<br/><br/>Daha fazla bilgi edinmek için bkz [. İş için Microsoft Defender'da roller ve izinler](mdb-roles-permissions.md). |
| Tarayıcı gereksinimleri | Microsoft Edge Veya Google Chrome |
| İşletim sistemi | Cihazları İş için Microsoft Defender'da yönetmek için, cihazlarınız aşağıdaki işletim sistemlerinden birini çalıştırmaktadır: <br/>- Windows 10 Business veya sonrası <br/>- Windows 10 Professional veya sonrası <br/>- Windows 10 Enterprise veya sonrası <br/><br/>[KB5006738'in yüklü](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) olduğundan emin olun. <br/><br/>Cihazları zaten Microsoft Intune 'da (veya Microsoft Endpoint Manager) yönetiyorsanız, bu cihazları İş için Defender'a  edinebilirsiniz. |
| Microsoft Endpoint Manager ile tümleştirme  | Cihazları İş için [Microsoft Defender güvenlik yapılandırmasını kullanarak eklemeyi planlıyorsanız](mdb-onboard-devices.md#microsoft-defender-for-business-security-configuration), aşağıdaki gereksinimlerin karşı olması gerekir:<br/><br/>Uç Nokta için [Microsoft Defender Güvenlik Yönetimi'nin önkoşulları karşı olmalıdır](/mem/intune/protect/mde-security-integration).<br/>- Azure AD, şirketinizin cihazları arasında güveni ve Azure AD'nin oluşturulacak şekilde yapılandırılması gerekir. <br/>- İş için Defender,'da güvenlik yönetiminin etkinleştirilmiş Microsoft Endpoint Manager.<br/><br/>Cihazların aşağıdaki URL'lere bağlanamaları gerekir:<br/>- `enterpriseregistration.windows.net` (Azure AD'de kayıt için)<br/>- `login.microsoftonline.com` (Azure AD'de kayıt için)<br/>- `*.dm.microsoft.com` (Joker karakter (*), kayıt, iade ve raporlama için kullanılan bulut hizmeti uç noktalarını destekler ve hizmet ölçeği olarak değişebilir.) |

> [!NOTE]
> [Azure Active Directory izinlerini ve cihaz gruplarını yönetmek için otomatik ad (Azure AD)](/azure/active-directory/fundamentals/active-directory-whatis) kullanılır. Azure AD, İş için Defender aboneliğinize dahildir. 
> - Denemenizi başlatmadan Microsoft 365 aboneliğiniz yoksa, etkinleştirme işlemi sırasında Azure AD sizin için hazır olur. 
> - Defender For Business denemenizi Microsoft 365 başka bir Microsoft 365 aboneliğiniz varsa, var olan Azure AD hizmetinizi kullanabilirsiniz. 
> - İşletmeler için [Defender Microsoft 365 İş Ekstra'i](../../business/index.yml) kullanırken Microsoft Intune. 

## <a name="next-steps"></a>Sonraki adımlar

Şu şekilde devam edin:

- [2. Adım: İş için Microsoft Defender'da roller ve izinler atama](mdb-roles-permissions.md) 
 