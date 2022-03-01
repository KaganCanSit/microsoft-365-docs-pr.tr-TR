---
title: İş için Microsoft Defender gereksinimleri (önizleme)
description: İş için Microsoft Defender (önizleme) lisansı, donanım ve yazılım gereksinimleri
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/14/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 59de83ae127a20fd7d7c529a626544cc0a9d2434
ms.sourcegitcommit: 007822d16e332522546e948f5c216327254a4d49
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2022
ms.locfileid: "63015327"
---
# <a name="microsoft-defender-for-business-preview-requirements"></a>İş için Microsoft Defender (önizleme) gereksinimleri

> [!IMPORTANT]
> İş için Microsoft Defender şu anda önizlemede ve istekte etmek için buraya kaydolan müşterilere ve IT [İş Ortaklarına aşamalı](https://aka.ms/mdb-preview) olarak aşamalı olarak aşamalı olarak sunulmaktadır. Önümüzdeki haftalarda bir ilk müşteri ve iş ortağı kümesi sunuyoruz ve genel kullanılabilirlik durumuna kadar önizlemeyi genişleteceğiz. Önizlemenin bir dizi ilk [senaryoyla başlat olacağını](mdb-tutorials.md#try-these-preview-scenarios) ve düzenli olarak özellikler ekley olacacaz.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

Bu makalede, İş için Microsoft Defender (önizleme) gereksinimleri açıklanmıştır.

## <a name="what-to-do"></a>Ne yapmalı?

1. [Gereksinimleri gözden geçirme ve bunları karşıla](#review-the-requirements)

2. [Sonraki adımlarınıza devam edin](#next-steps).

## <a name="review-the-requirements"></a>Gereksinimleri gözden geçirme

Aşağıdaki tabloda, İş için Microsoft Defender (önizleme) yapılandıracak ve kullanabileceğiniz temel gereksinimler listelemektedir. <br/><br/>

| Gereksinim | Açıklama |
|:---|:---|
| Abonelik | İş için Microsoft Defender (şu anda önizlemede!). Bkz[. İş için Microsoft Defender (önizleme)'yi nasıl almak için?](get-defender-business.md)<br/><br/>**Microsoft Defender for Business (önizleme) Microsoft 365 başka bir çevrimiçi aboneliğiniz olması** gerekmez.<br/><br/>Birden çok aboneliğiniz varsa, en yüksek abonelik öncelikli olur. Örneğin, Uç Nokta Planı 2 için Microsoft Defender'ı (satın alınan veya deneme aboneliği) alıyorsanız ve İş için Microsoft Defender (önizleme) alıyorsanız, Uç Nokta Planı 2 için Defender öncelikli olur. Bu durumda, İş için Defender (önizleme) deneyimini görmüyoruz.  |
| Datacenter | Aşağıdaki veri merkezi konumlarından biri: <br/>- Avrupa Birliği <br/>- Birleşik Krallık <br/>- Amerika Birleşik Devletleri |
| Kullanıcı hesapları | Kullanıcı hesapları yeni hesapta Microsoft 365 yönetim merkezi ([https://admin.microsoft.com](https://admin.microsoft.com))<br/><br/>Microsoft Defender İş (önizleme) lisansları aşağıdaki iletişim Microsoft 365 yönetim merkezi<br/><br/>Bu görevle ilgili yardım almak için bkz [. Kullanıcı ekleme ve lisans atama](../../admin/add-users/add-users.md). |
| İzinler  | İş için Microsoft Defender'a (önizleme) kaydolmak için Genel Yönetici olmak gerekir.<br/><br/>Kullanıcı portalına Microsoft 365 Defender, kullanıcıların Azure [AD'de şu rollerden birinin atanmış olması](mdb-roles-permissions.md) gerekir: <br/>- Güvenlik Okuyucu<br/>- Güvenlik Yöneticisi<br/>- Genel Yönetici<br/><br/>Daha fazla bilgi edinmek için bkz [. İş için Microsoft Defender'da (önizleme) roller ve izinler](mdb-roles-permissions.md). |
| Tarayıcı gereksinimleri | Microsoft Edge Veya Google Chrome |
| İşletim sistemi | Cihazları İş için Microsoft Defender(önizleme) ile yönetmek için cihazlarınızı aşağıdaki işletim sistemlerinden birini çalıştırabilirsiniz: <br/>- Windows 10 Business veya sonrası <br/>- Windows 10 Professional veya sonrası <br/>- Windows 10 Enterprise veya sonrası <br/><br/>[KB5006738'in yüklü](https://support.microsoft.com/topic/october-26-2021-kb5006738-os-builds-19041-1320-19042-1320-and-19043-1320-preview-ccbce6bf-ae00-4e66-9789-ce8e7ea35541) olduğundan emin olun. <br/><br/>Cihazları zaten Microsoft Intune'te (veya Microsoft Endpoint Manager) yönetiyorsanız veya Microsoft olmayan bir cihaz yönetim çözümü kullanıyorsanız, cihazlarınız Uç Nokta için Microsoft Defender'da desteklenen işletim sistemlerinden birini [çalıştırıyor olmalıdır](../defender-endpoint/minimum-requirements.md). |
| Microsoft Endpoint Manager ile tümleştirme  |  **Önizleme sırasında, cihaz tümleştirmesi gerektirmeyen yerel bir betik kullanarak cihazları Microsoft Endpoint Manager**. Ancak Microsoft Endpoint Manager, Grup İlkesi, System Center Configuration Manager veya Mobil Cihaz Yönetimi için indirilebilir paketleri kullanarak cihazları Defender for Business (önizleme) uygulamasına el ile eklemeyi planlıyorsanız aşağıdaki gereksinimler karşılanabilir:<br/><br/>Uç Nokta için [Microsoft Defender Güvenlik Yönetimi'nin önkoşulları karşı olmalıdır](/mem/intune/protect/mde-security-integration).<br/>- Azure AD, kuruluş cihazlarıyla Azure AD arasında güven oluşturulacak şekilde yapılandırıldığından emin olun. <br/>- İş için Defender (önizleme) ikisinde de güvenlik yönetiminin etkinleştirilmiş Microsoft Endpoint Manager.<br/><br/>Cihazların aşağıdaki URL'lere bağlanamaları gerekir:<br/>- `enterpriseregistration.windows.net` (Azure AD'de kayıt için)<br/>- `login.microsoftonline.com` (Azure AD'de kayıt için)<br/>- `*.dm.microsoft.com` (Joker karakter (*), kayıt, iade ve raporlama için kullanılan bulut hizmeti uç noktalarını destekler ve hizmet ölçeği olarak değişebilir.) |

> [!NOTE]
> [Azure Active Directory izinlerini ve cihaz gruplarını yönetmek için otomatik ad (Azure AD)](/azure/active-directory/fundamentals/active-directory-whatis) kullanılır. Azure AD, İş için Defender (önizleme) aboneliğinize dahildir. 
> - Denemenizi başlatmadan Microsoft 365 aboneliğiniz yoksa, etkinleştirme işlemi sırasında Azure AD sizin için hazır olur. 
> - Defender for Business (önizleme) Microsoft 365 başka bir Microsoft 365 aboneliğiniz varsa, var olan Azure AD hizmetinizi kullanabilirsiniz. 
> - İşletmeler için [Defender Microsoft 365 İş Ekstra](../../business/index.yml) (önizleme) denemenizi başlarken Microsoft Intune. 

## <a name="next-steps"></a>Sonraki adımlar

Şu şekilde devam edin:

- [2. Adım: İş için Microsoft Defender'da (önizleme) roller ve izinler atama](mdb-roles-permissions.md) 
 
