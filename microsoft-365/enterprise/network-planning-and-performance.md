---
title: Ağ planlaması ve performans ayarı Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 2/18/2022
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Strat_O365_Enterprise
f1.keywords:
- CSH
search.appverid:
- MET150
ms.assetid: e5f1228c-da3c-4654-bf16-d163daee8848
ms.custom:
- seo-marvel-apr2020
- Adm_O365
description: Bu makale, ağ bant genişliği gereksinimlerinizi planlamanıza ve performans Microsoft 365 ince ayar ve sorun gidermenize yardımcı olur.
ms.openlocfilehash: 628d532a106ce9776443b252c863fa8bdc221b4b
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015475"
---
# <a name="network-planning-and-performance-tuning-for-microsoft-365"></a>Ağ planlaması ve performans ayarı Microsoft 365
Microsoft 365'i ilk kez dağıtmadan veya geçişe başlamadan önce, bu konu başlıkları altında yer alan bilgileri kullanarak ihtiyacınız olan bant genişliğini tahmin edecek ve Microsoft 365'i dağıtmak veya geçiş yapmak için yeterli bant genişliğiniz olup olmadığını test Microsoft 365. Genel bir bakış için bkz: [Ağ ve geçiş planlama için Microsoft 365](network-and-migration-planning.md).
  
|Kategori |Açıklama |Kategori |Açıklama |
|:-----|:-----|:-----|:-----|
|**Ağ planlaması** <br/> ![Ağ.](../media/5e9dcd06-601b-4b28-88dc-f524e7548794.png)           <br/> |Hızlı bağlantılar ve çabuk gelen sayfalar mı istiyorsunuz?  <br/> [E-Microsoft 365'de en iyi bağlantı ve performansı elde Microsoft 365](https://aka.ms/o365perfprinciples).<br/>Kavramları [Microsoft 365 için Ağ Bağlantısına Genel Bakış](microsoft-365-networking-overview.md) makalelerini okuyun.<br/> |**Ağ ölçülerini ölçerek** <br/> ![Hesap Makinesi](../media/d690a132-4884-40eb-a918-526bb3dff3cc.png)           <br/> |[Temelleri Microsoft 365 performans geçmişini kullanarak performans ayarlama ve Proje için performans](performance-tuning-using-baselines-and-history.md) [sorunlarını giderme planını Microsoft 365](performance-troubleshooting-plan.md).  <br/> Mevcut anızı değerlendirmek [için bu araçları kullanın](network-and-migration-planning.md#calculators).  <br/> |
|**En iyi yöntemler** <br/> ![En iyi yöntemler.](../media/2a659a5c-1007-47d3-a6c6-a19e018ab29b.png)           <br/> |[Ağ planlaması ve geçiş performansını iyileştirmek için en iyi Microsoft 365](network-and-migration-planning.md#BestPractices). Kullanıcılarınıza hemen yardımcı olmak mı istiyor musunuz? Yavaş [bir ağ üzerinde Office 365 en iyi yöntemler'e bakın](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166).  <br/> [Microsoft 365 Bağlantısı İlkeleri](./microsoft-365-network-connectivity-principles.md), ağ bağlantısını güvenli bir şekilde en iyi duruma getirme konusunda en yeni Microsoft 365 yardımcı olacaktır.  <br/> |**Başvuru** <br/> ![Kitap veya Günlük](../media/56dff3c1-f605-48d8-811f-7d13ce639ecd.png)           <br/> |IP adreslerinin ve bağlantı noktalarının listesi gibi ayrıntıları mı görmek istiyor musunuz? Daha fazla [bilgi için Ağ planlama Microsoft 365](network-and-migration-planning.md#NetReference).  <br/> |
|![Enterprise Architects için Microsoft Bulut Ağı posterlerine bakın.](../media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)           <br/> |Hem microsoft hem de diğer Microsoft bulut Microsoft 365 hizmetleri için ağına en iyi duruma getirme adımları için, [Enterprise Architects için Microsoft Bulut Ağı posteri'ne](../solutions/cloud-architecture-models.md) bakın.  <br/> |
   
## <a name="performance-tuning-and-troubleshooting-resources-for-microsoft-365"></a>E-Microsoft 365 için performans ayarlama ve sorun giderme kaynakları
<a name="apptuning"> </a>

Uygulama dağıttıktan Microsoft 365, bu bölümdeki konuları kullanarak performansınızı en iyi duruma getirmeniz gerekir. Performans düşüşü yaşanıyorsa, sorunları gidermek için de bu konuları kullanabilirsiniz.
  
 **[Performans Office 365 ayarlama](tune-microsoft-365-performance.md)**: Destek hizmetleriyle ağ adresi çevirisi Office 365 [bilgi için bkz. AĞ Office 365](nat-support-with-microsoft-365.md). Ayrıca, ağ bağlantınızı [iyileştirmeniz ve sorunları gidermeniz için en iyi 10 Office 365 göz atabilirsiniz](/archive/blogs/onthewire/top-10-tips-for-optimising-troubleshooting-your-office-365-network-connectivity).
  
 **[Performans Exchange Online ayarlama](tune-exchange-online-performance.md)**: Performansı en iyi şekilde ayarlamak için Exchange Online kullanın.

 **[Destek için kuruluş ağına hazırlanma: Microsoft Teams](/microsoftteams/prepare-network)** için iyileştirmek üzere şu makaleleri Teams.
  
 **[Çevrimiçi Skype Kurumsal ayarlama](tune-skype-for-business-online-performance.md)**: Çevrimiçi performansın ince ayarını yapmak için Skype Kurumsal makalelerden yardım alın.
  
 **[Çevrimiçi SharePoint ayarlama](tune-sharepoint-online-performance.md)**: Çevrimiçi performansın ince ayarını yapmak için SharePoint makalelerini kullanın.
  
 **[Performans Project Online ayarlama](https://support.office.com/article/12ba0ebd-c616-42e5-b9b6-cad570e8409c)**: Performansta ince ayarlar yapmak Project Online kullanın
