---
title: Özel kullanıcı görünümü oluşturma, düzenleme veya silme
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 4fe7f6ac-be8e-4b57-9e13-24ff889a4b28
description: İş için Microsoft 365 aboneliğinin genel veya kullanıcı yönetimi yöneticisiyseniz, özel kullanıcı görünümü oluşturmak, düzenlemek veya silmek için filtreleri kullanabilirsiniz.
ms.openlocfilehash: d90d324690d153fa708dbe7c36a9f41d349f8588
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436745"
---
# <a name="create-edit-or-delete-a-custom-user-view"></a>Özel kullanıcı görünümü oluşturma, düzenleme veya silme

İş için Microsoft 365 aboneliğinin genel veya kullanıcı yönetimi yöneticisiyseniz, belirli bir kullanıcı alt kümesini görüntülemek için özel kullanıcı görünümleri oluşturabilirsiniz. Bu görünümler, standart görünüm kümesine ek olarak sağlanır. Özel kullanıcı görünümleri oluşturabilir, düzenleyebilir veya silebilirsiniz ve oluşturduğunuz özel görünümler tüm yöneticiler tarafından kullanılabilir.
  
## <a name="custom-user-views-in-the-admin-center"></a>Yönetim merkezinde özel kullanıcı görünümleri

Özel bir kullanıcı görünümü oluşturduğunuzda, düzenlediğinizde veya sildiğinizde, değişiklikler Şirketinizdeki tüm yöneticilerin **Kullanıcılar** sayfasına gittiği zaman göreceği **Filtre** listesinde gösterilir. En fazla 50 özel görünüm oluşturabilirsiniz. 

> [!TIP]
>  Standart kullanıcı görünümleri **varsayılan olarak Filtreler** açılan listesinde görüntülenir. Standart filtreler **Tüm kullanıcılar**, **Lisanslı kullanıcılar**, **Konuk kullanıcılar**,  **Oturum açmaya izin verilenler**, **Oturum açma engellenenler**, **Lisanssız kullanıcılar**, **Hatalı** kullanıcılar, **Faturalama yöneticileri**, **Genel yöneticiler**, **Yardım masası yöneticileri**, **Hizmet yöneticileri** ve **Kullanıcı yönetimi yöneticileridir**. Standart görünümleri düzenleyemez veya silemezsiniz. 

Standart görünümler hakkında dikkate almak gereken birkaç nokta: 

- Listede 2.000'den fazla kullanıcı varsa bazı standart görünümler sıralanmamış bir liste görüntüler. Bu listedeki belirli kullanıcıları bulmak için arama kutusunu kullanın. 
- Microsoft'tan Microsoft 365 satın almadıysanız **Faturalama yöneticileri standart görünümler** listesinde görünmez. Daha fazla bilgi için bkz. [Yönetici rolleri atama](assign-admin-roles.md). 
  
## <a name="choose-the-filters-for-your-custom-user-view"></a>Özel kullanıcı görünümünüz için filtreleri seçme

**Özel görünümlerinizi Özel filtre** bölmesinde oluşturabilir ve düzenleyebilirsiniz. Birden çok filtre seçeneği seçerseniz, seçilen tüm ölçütlere uyan kullanıcıları içeren sonuçlar elde edersiniz. Aşağıdaki örnekte, Kanada'da bulunan belirli bir etki alanındaki tüm kullanıcıları gösteren "Kanada kullanıcıları" adlı özel bir görünümün nasıl oluşturulacağı gösterilmektedir. 

  
 **A - Etki Alanı** Kuruluşunuz için birden çok etki alanınız varsa, kullanılabilir etki alanlarının açılan listesinden seçim yapabilirsiniz. 
  
 **B - Oturum açma durumu** İzin verilen veya engellenen kullanıcıları seçin. 
  
 **C - Konum** Ülkelerin açılan listesinden bir konum seçin. 
  
 **D - Atanan ürün lisansı** Kuruluşunuzda kullanılabilen lisansların açılan listesinden seçim yapın. Seçtiğiniz lisansın atandığı kullanıcıları göstermek için bu filtreyi kullanın. Kullanıcıların ek lisansları da olabilir. 
  
Ayrıca kuruluşunuzda kullanılan departman, şehir, eyalet veya il, ülke veya bölge ya da iş unvanı gibi ek kullanıcı profili ayrıntılarına göre filtreleyebilirsiniz.
  
 **Diğer koşullar:**
  
- **Yalnızca eşitlenen kullanıcılar** Kullanıcıların etkinleştirilip etkinleştirilmediğine bakılmaksızın, yerel Active Directory ile eşitlenmiş olan tüm kullanıcıları göstermek için bu kutuyu seçin. 
    
- **Hataları olan kullanıcılar** Sağlama hataları olabilecek kullanıcıları göstermek için bu kutuyu seçin. 
    
- **Lisanssız kullanıcılar** Lisans atanmamış tüm kullanıcıları bulmak için bu kutuyu seçin. Bu görünümün sonuçları, Exchange posta kutusu olan ancak lisansı olmayan kullanıcıları da içerebilir. Bu kullanıcıları özellikle izlemek için, **Exchange posta kutuları veya arşivleri olan Lisanssız kullanıcılar** filtresini kullanın. Bu görünümün sonuçları, Exchange arşivi olan ancak lisansı olmayan kullanıcıları da içerebilir.
    
- **posta kutuları veya arşivleri Exchange lisanssız kullanıcılar Exchange Online** oluşturulan ve Exchange posta kutusuna sahip olan ancak Microsoft 365 lisansı atanmamış kullanıcı hesaplarını göstermek için bu kutuyu seçin. Bu filtrenin sonuçları, Exchange arşivi olan veya atanmış olan kullanıcıları içerir. 

> [!NOTE]
> **Exchange posta kutularına sahip Lisanssız kullanıcılar** filtresi şu durumlarda çalışır:
1. Posta kutusu yakın zamanda **paylaşılan** posta kutusundan **kullanıcıya** dönüştürüldü ve lisansı yok.
2. Posta kutusu yakın zamanda Microsoft 365 geçirildi ancak lisans atanmadı.
3. Posta kutusu PowerShell kullanılarak oluşturulmuş ve lisans atanmamış.
4. Kullanıcı için bir New-RemoteMailbox cmdlet'i ile şirket içinde oluşturulan yeni bir posta kutusu sağlanır.
    
> [!TIP]
> 2.000'den fazla kullanıcı döndüren özel bir görünüm oluşturursanız, sonuçta elde edilen kullanıcı listesi sıralanmaz. Bu durumda, kullanıcıları bulmak için arama kutusunu kullanın veya aramanızı daraltmak için özel görünümünüzü düzenleyin. 
  
## <a name="create-a-custom-user-view"></a>Özel kullanıcı görünümü oluşturma

::: moniker range="o365-worldwide"

1. Yönetim merkezinde **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar'a</a> gidin.
  
::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetim merkezinde **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Etkin kullanıcılar'a</a> gidin.  

::: moniker-end
    
2. **Etkin kullanıcılar** sayfasında **Filtreler'i** ve **ardından Yeni filtre'yi** seçin.
  
3. **Özel filtre** sayfasında, filtrenizin adını girin, özel filtrenizin koşullarını seçin ve ardından **Ekle'yi** seçin. Özel görünümünüz artık filtrelerin açılan listesinde yer alır.

## <a name="edit-or-delete-a-custom-user-view"></a>Özel kullanıcı görünümünü düzenleme veya silme

::: moniker range="o365-worldwide"

1. Yönetim merkezinde **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar'a</a> gidin.

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetim merkezinde **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Etkin kullanıcılar'a</a> gidin. 

::: moniker-end 
    
2. **Etkin kullanıcılar** sayfasında **Filtre'yi** seçin, değiştirmek istediğiniz filtreyi seçin ve ardından **Filtreyi düzenle'yi** seçin. 
    
    > [!TIP]
    > Yalnızca özel görünümleri düzenleyebilirsiniz. 
  
3. **Özel filtre** sayfasında, bilgileri gerektiği gibi düzenleyin ve **kaydet'i** seçin. Ya da filtreyi silmek için sayfanın alt kısmında **Sil'i** seçin. 

## <a name="related-content"></a>İlgili içerik

[Microsoft 365 yönetim merkezi genel bakış](../admin-overview/admin-center-overview.md) (video)\
[Yönetici rolleri hakkında](../add-users/about-admin-roles.md) (video)\
[Kuruluşunuz için Microsoft 365 temasını özelleştirme](../setup/customize-your-organization-theme.md) (makale)


     
