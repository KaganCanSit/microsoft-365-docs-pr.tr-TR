---
title: DNS kayıtlarını güncelleştirerek web sitenizi geçerli barındırma sağlayıcınızla koruma
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 2c4cf347-b897-45c1-a71f-210bdc8f1061
description: Microsoft'u özel etki alanınız için DNS kayıtlarını yönetecek şekilde ayarladıysanız, trafiği Microsoft dışında barındırılan mevcut bir genel web sitesine nasıl yönlendirileceğini öğrenin.
ms.openlocfilehash: 9bb12d4f73e8d95717ddd90492fb9cb97c73eec9
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314828"
---
# <a name="update-dns-records-to-keep-your-website-with-your-current-hosting-provider"></a>DNS kayıtlarını güncelleştirerek web sitenizi geçerli barındırma sağlayıcınızla koruma

 **Etki alanınıza göre Microsoft kayıtlarını DNS barındırma** sağlayıcınızda yönetirsiniz, bu konudaki adımları düşünmenize gerek yok. Web siteniz olduğu yerde kalır ve herkes sitenize erişmeye devam edebilir. 
  
 **DNS kayıtlarınızı Microsoft yönetecekse**, trafiği Microsoft dışında barındırılan mevcut bir genel web sitesine yönlendirecek şekilde etki alanınızı Microsoft'a ekledikten sonra şunları yapın: 
  
## <a name="update-dns-records-in-the-microsoft-365-admin-center"></a>Kayıtlarda DNS kayıtlarını Microsoft 365 yönetim merkezi
1. Yönetim merkezinde Etki Alanları'Ayarlar  \> gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank"></a>

1. Etki Alanları **sayfasında** etki alanını seçin ve sonra da **DNS Kayıtları'ı seçin**.

1. **+ Kayıt ekle'yi** seçin ve şunları girin: 
    
   - Tür **olarak** şunları girin: **A (Adres)**
    
   - **Ana bilgisayar adı veya Diğer ad** olarak şunu yazın: **@**
    
   - **IP Adresi** olarak web sitenizin şu anda barındırıldığı statik IP adresini yazın (örneğin, 172.16.140.1). 
    
   Bu adres web sitesinin  *statik*  IP adresi olmalıdır,  *dinamik*  IP adresi olamaz. Genel web siteniz için bir statik IP adresi alıp alamayacağınızdan emin olmak için web sitenizin barındırıldığı siteyi kontrol edin. 
    
1. **Kaydet** 'i seçin. 
    
Buna ek olarak, müşterilerin web sitenizi bulmalarına yardım etmek için bir CNAME kaydı da oluşturabilirsiniz.
  
1. **+ Kayıt ekle'yi** seçin ve şunları girin: 
    
   - Tür **olarak** şunları girin: **CNAME (Diğer ad)**
    
   - **Ana bilgisayar adı veya Diğer ad** olarak şunu yazın: **www**
    
   - **İşaret edilen adres** olarak, web sitenizin tam etki alanı adını (FQDN) yazın (örneğin, contoso.com). 
    
2. **Kaydet** 'i seçin. 
    
Son olarak da aşağıdakileri yapın:
  
[Etki alanınıza göre NS kayıtlarını Microsoft'a](../setup/add-domain.md) işaret ediyor şekilde güncelleştirin. 
  
NS kayıtları Microsoft'u işaret etmek için güncelleştirildiğinde, etki alanınız ayarlanır. E-posta Microsoft'a yönlendirilen ve web sitenizin adresine giden trafik geçerli web sitesi barındırma hizmetinize yönlendirilene kadar devam edecektir.
