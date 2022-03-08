---
title: DNS kayıtlarını oluşturmak için ihtiyacınız olan bilgileri toplama
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
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 77f90d4a-dc7f-4f09-8972-c1b03ea85a67
description: Etki alanınızı Microsoft 365 aboneliğinize bağlamak için DNS kayıtları oluşturmak için ihtiyacınız olan değerleri/Microsoft 365 toplayın.
ms.openlocfilehash: 672d57babb1b26e42b3fd24da8c9dc841223e41f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316807"
---
# <a name="gather-the-information-you-need-to-create-dns-records"></a>DNS kayıtlarını oluşturmak için ihtiyacınız olan bilgileri toplama

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**. 
  
### <a name="step-1-find-the-txt-record-value-and-verify"></a>1. Adım: TXT kaydı değerini bulma ve doğrulama

::: moniker range="o365-worldwide"

1. Etki Microsoft 365 yönetim merkezi, Etki Alanları **Ayarlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">gidin.</a>

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetim merkezinde Etki Alanları'Ayarlar  > gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank"></a>

::: moniker-end
    
2. Etki Alanları **sayfasında** etki alanınızı seçin ve sonra da Kurulumu **başlat'ı seçin**. Eklemeniz gereken değeri görmek için etki alanları kurulum sihirbazına dönersiniz.
    
3. Etki Alanı **Doğrulama sayfasında** , etki **alanının DNS kayıtlarına TXT kaydı ekle'yi seçin ve sonra da** Devam'ı **seçin**.
    
4. Gösterilen **TXT değerini** kopyalayın. Şöyle görünüyor: **MS=msXXXXXXXX**. 
    
5. Etki [alanınıza bağlanmak için DNS kayıtları ekleme'ye](create-dns-records-at-any-dns-hosting-provider.md) gidin ve DNS barındırma sitenizin web sitesinde kayıtları ekleme adımlarını izleyin.
    
6. DNS ana ekleyebilirsiniz ve sonra etki alanını yeniden DOĞRULA'da TXT kaydı (veya MX kaydı) oluşturma adımlarını Microsoft 365.

7. Etki alanı doğrulandıktan sonra DNS ana ekleyebilirsiniz TXT kaydını (veya MX kaydını) Microsoft 365.
    
### <a name="step-2-find-the-mx-record-value-for-email-and-more"></a>2. Adım: E-posta ve daha fazlası için MX kaydı değerini bulma

::: moniker range="o365-worldwide"

1. Etki Microsoft 365 yönetim merkezi, Etki Alanları **Ayarlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">gidin.</a>

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetim merkezinde Etki Alanları'Ayarlar  > gidin.<a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank"></a>

::: moniker-end
    
2. **Etki Alanları** sayfasında etki alanınızı seçin.
    
3.  **DNS'yi Yönet'i** seçin, **Diğer SeçeneklerKendi** >  **DNS'nizi** ekleyin ve eklemek istediğiniz DNS kayıtlarını görmek için Devam'ı seçin.
    
    DNS barındırma sağlayıcınızda değişiklikleri yaparken bu bilgilerin kullanılabilir durumda olmasını istersiniz, çünkü böylelikle değerleri kopyalayıp yapıştırabilirsiniz.
    
    Sayfada listelenen DNS kayıtları grubu **Etki alanı amacı**'nın altında listelenen seçimlerinize bağlıdır.
    
4. Etki [alanınıza bağlanmak için DNS kayıtları ekleme'ye](create-dns-records-at-any-dns-hosting-provider.md) gidin ve DNS barındırma sitenizin web sitesinde kayıtları ekleme adımlarını izleyin.

5. DNS ana bilgisayarınızda kayıtları oluşturma adımlarını izleyin.

## <a name="related-content"></a>İlgili içerik

[Etki Alanları SSS](../setup/domains-faq.yml) (makale)\
[Etki alanınızı veya DNS kayıtlarınızı ekledikten sonra sorunları bulma](find-and-fix-issues.md) ve düzeltme (makale)\
[Etki alanlarını yönetme](/admin) (bağlantı sayfası)