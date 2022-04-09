---
title: İş için Microsoft Defender gereksinimleri
description: lisans, donanım ve yazılım gereksinimlerini İş için Microsoft Defender
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
ms.openlocfilehash: dd30af8003e6c5bc6a4348efe16626d2d45317f1
ms.sourcegitcommit: dd5fc139affb4cba4089cbdb2c478968b680699a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2022
ms.locfileid: "64747083"
---
# <a name="microsoft-defender-for-business-requirements"></a>İş için Microsoft Defender gereksinimleri

> [!IMPORTANT]
> İş için Microsoft Defender, 1 Mart 2022'de başlayarak [Microsoft 365 İş Ekstra](../../business-premium/index.md) müşterilerine dağıtılıyor. Tek başına abonelik olarak İş için Defender önizleme aşamasındadır ve istekte bulunmak için [buraya kaydolan](https://aka.ms/mdb-preview) müşterilere ve BT İş Ortaklarına aşamalı olarak dağıtılacaktır. Önizleme, [bir dizi ilk senaryo](mdb-tutorials.md#try-these-preview-scenarios) içerir ve düzenli olarak özellikler ekleyeceğiz.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilebilen önceden yayımlanmış ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

Bu makalede İş için Microsoft Defender gereksinimleri açıklanmaktadır.

## <a name="what-to-do"></a>Yapılması gerekenler

1. [Gereksinimleri gözden geçirin ve karşıladığınızdan emin olun](#review-the-requirements).

2. [Sonraki adımlarınıza geçin](#next-steps).

>
> **Bir dakikan var mı?**
> Lütfen <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">İş için Microsoft Defender hakkındaki kısa anketimize</a> katılın. Sizden haber almak isteriz!
>

## <a name="review-the-requirements"></a>Gereksinimleri gözden geçirin

Aşağıdaki tabloda, İş için Microsoft Defender yapılandırmak ve kullanmak için temel gereksinimler listelemektedir. <br/><br/>

| Gereksinim | Açıklama |
|:---|:---|
| Abonelik | Microsoft 365 Business Premium <br/>--- veya ---<br/>İş için Microsoft Defender (tek başına; şu anda önizleme aşamasında). <br/><br/> Bkz[. İş için Microsoft Defender alma](get-defender-business.md).<br/><br/>Birden çok aboneliğiniz varsa en yüksek aboneliğin öncelikli olduğunu unutmayın. Örneğin, Uç Nokta için Microsoft Defender Plan 2 'niz (satın alınmış veya deneme aboneliği) varsa ve İş için Microsoft Defender alırsanız, Uç Nokta Için Defender Plan 2 önceliklidir. Bu durumda, İş için Defender deneyimini görmezsiniz.  |
| Datacenter | Aşağıdaki veri merkezi konumlarından biri: <br/>- Avrupa Birliği <br/>- Birleşik Krallık <br/>- Birleşik Devletler |
| Kullanıcı hesapları | Kullanıcı hesapları Microsoft 365 yönetim merkezi oluşturulur ([https://admin.microsoft.com](https://admin.microsoft.com))<br/><br/>İş için Microsoft Defender lisansları Microsoft 365 yönetim merkezi<br/><br/>Bu görevle ilgili yardım almak için bkz. [Kullanıcı ekleme ve lisans atama](../../admin/add-users/add-users.md). |
| İzinler  | İş için Microsoft Defender kaydolmak için Genel Yönetici olmanız gerekir.<br/><br/>Microsoft 365 Defender portalına erişmek için kullanıcıların [Azure AD'de aşağıdaki rollerden](mdb-roles-permissions.md) birine atanmış olması gerekir: <br/>- Güvenlik Okuyucusu<br/>- Güvenlik Yöneticisi<br/>- Genel Yönetici<br/><br/>Daha fazla bilgi için bkz. [İş için Microsoft Defender'de roller ve izinler](mdb-roles-permissions.md). |
| Tarayıcı gereksinimleri | Microsoft Edge veya Google Chrome |
| İşletim sistemi | İş için Microsoft Defender cihazları yönetmek için, cihazlarınız aşağıdaki işletim sistemlerinden birini çalıştırıyor olmalıdır: <br/>- Windows 10 Business veya üzeri <br/>- Windows 10 Professional veya üzeri <br/>- Windows 10 Enterprise veya üzeri <br/><br/>[KB5006738'in](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) yüklü olduğundan emin olun. <br/><br/>Cihazları zaten Microsoft Intune 'de (veya Microsoft Endpoint Manager) yönetiyorsanız, bu cihazları İş için Defender'a ekleyebilirsiniz. |

> [!NOTE]
> [Azure Active Directory (Azure AD),](/azure/active-directory/fundamentals/active-directory-whatis) kullanıcı izinlerini ve cihaz gruplarını yönetmek için kullanılır. Azure AD, İş için Defender aboneliğinize dahildir. 
> - Denemenize başlamadan önce Microsoft 365 aboneliğiniz yoksa, etkinleştirme işlemi sırasında Azure AD sizin için sağlanır. 
> - İş için Defender deneme sürümünüzü başlattığınızda başka bir Microsoft 365 aboneliğiniz varsa mevcut Azure AD hizmetinizi kullanabilirsiniz. 
> - İş için Defender denemenizi başlattığınızda [Microsoft 365 İş Ekstra](../../business/index.yml) kullanıyorsanız, cihazları Microsoft Intune'de yönetme seçeneğiniz olur. 

## <a name="next-steps"></a>Sonraki adımlar

2. [Adım: İş için Microsoft Defender rol ve izin atama](mdb-roles-permissions.md) bölümüne geçin.
 