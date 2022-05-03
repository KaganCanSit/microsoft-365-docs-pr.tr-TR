---
title: İş için Microsoft Defender gereksinimleri
description: lisans, donanım ve yazılım gereksinimlerini İş için Microsoft Defender
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 01abbfe2a6190da21836c9493868c5d1b136f104
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65173211"
---
# <a name="microsoft-defender-for-business-requirements"></a>İş için Microsoft Defender gereksinimleri

Bu makalede İş için Microsoft Defender gereksinimleri açıklanmaktadır.

## <a name="what-to-do"></a>Yapılması gerekenler

1. [Gereksinimleri gözden geçirin ve karşıladığınızdan emin olun](#review-the-requirements).
2. [Sonraki adımlarınıza geçin](#next-steps).

>
> **Bir dakikan var mı?**
> Lütfen <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">güvenlikle ilgili kısa anketimize</a> katılın. Sizden haber almak isteriz!
>

## <a name="review-the-requirements"></a>Gereksinimleri gözden geçirin

Aşağıdaki tabloda, İş için Microsoft Defender yapılandırmak ve kullanmak için temel gereksinimler listelemektedir.

| Gereksinim | Açıklama |
|:---|:---|
| Abonelik | Microsoft 365 İş Ekstra veya İş için Microsoft Defender (tek başına). Bkz[. İş için Microsoft Defender alma](get-defender-business.md).<br/><br/>Birden çok aboneliğiniz varsa en yüksek aboneliğin öncelikli olduğunu unutmayın. Örneğin, Uç Nokta için Microsoft Defender Plan 2 'niz (satın alınmış veya deneme aboneliği) varsa ve İş için Microsoft Defender alırsanız, Uç Nokta Için Defender Plan 2 önceliklidir. Bu durumda, İş için Defender deneyimini görmezsiniz.  |
| Datacenter | Aşağıdaki veri merkezi konumlarından biri: <br/>- Avrupa Birliği <br/>- Birleşik Krallık <br/>- Birleşik Devletler |
| Kullanıcı hesapları | - Kullanıcı hesapları Microsoft 365 yönetim merkezi oluşturulur ([https://admin.microsoft.com](https://admin.microsoft.com))<br/>- İş için Microsoft Defender lisansları Microsoft 365 yönetim merkezi<br/><br/>Bu görevle ilgili yardım almak için bkz. [Kullanıcı ekleme ve lisans atama](mdb-add-users.md). |
| İzinler  | İş için Microsoft Defender kaydolmak için Genel Yönetici olmanız gerekir.<br/><br/>Microsoft 365 Defender portalına erişmek için kullanıcıların [Azure AD'da aşağıdaki rollerden](mdb-roles-permissions.md) birine atanmış olması gerekir: <br/>- Güvenlik Okuyucusu<br/>- Güvenlik Yöneticisi<br/>- Genel Yönetici<br/><br/>Daha fazla bilgi için bkz. [İş için Microsoft Defender'de roller ve izinler](mdb-roles-permissions.md). |
| Tarayıcı gereksinimleri | Microsoft Edge veya Google Chrome |
| İşletim sistemi | Microsoft 365 Defender portalındaki cihazları yönetmek için cihazlarınız aşağıdaki işletim sistemlerinden birini çalıştırıyor olmalıdır: <br/>- Windows 10 Business veya üzeri <br/>- Windows 10 Professional veya üzeri <br/>- Windows 10 Enterprise veya üzeri <br/>- macOS (en güncel üç sürüm desteklenir)<br/><br/>[Windows cihazlarda KB5006738'in](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) yüklü olduğundan emin olun. <br/><br/>Cihazları zaten Microsoft Intune yönetiyorsanız, Microsoft Endpoint Manager yönetim merkezini kullanmaya devam edebilirsiniz. |

> [!NOTE]
> [Azure Active Directory (Azure AD)](/azure/active-directory/fundamentals/active-directory-whatis) kullanıcı izinlerini ve cihaz gruplarını yönetmek için kullanılır. Azure AD, İş için Defender aboneliğinize dahildir. 
> - Deneme sürümüne başlamadan önce Microsoft 365 aboneliğiniz yoksa etkinleştirme işlemi sırasında sizin için Azure AD sağlanır. 
> - İş için Defender deneme sürümünüzü başlattığınızda başka bir Microsoft 365 aboneliğiniz varsa, mevcut Azure AD hizmetinizi kullanabilirsiniz. 
> - İş için Defender deneme sürümünüzü başlattığınızda [Microsoft 365 İş Ekstra](../../business/index.yml) kullanıyorsanız cihazlarınızı Intune kullanarak yönetme seçeneğiniz olur. 

## <a name="next-steps"></a>Sonraki adımlar

2. [Adım: İş için Microsoft Defender rol ve izin atama](mdb-roles-permissions.md) bölümüne geçin.
 
