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
description: Aynı görünümde özel kullanıcı görünümü oluşturmak, düzenlemek veya silmek için filtreleri Microsoft 365.
ms.openlocfilehash: cf3e286a7d8f0e9b5f9741541974b2125df505ad
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499605"
---
# <a name="create-edit-or-delete-a-custom-user-view"></a>Özel kullanıcı görünümü oluşturma, düzenleme veya silme

Microsoft 365 İş aboneliğinde genel yönetici veya kullanıcı yönetimi yöneticisiyseniz, belirli bir kullanıcı alt kümesini görüntülemek için özel kullanıcı görünümleri oluşturabilirsiniz. Bu görünümler, standart görünüm kümesine ek olarak bulunmaktadır. Özel kullanıcı görünümlerini oluşturabilir, düzenleyebilir veya silebilirsiniz ve kendi özel görünümlerini tüm yöneticiler kullanabilir.
  
## <a name="custom-user-views-in-the-admin-center"></a>Yönetim merkezinde özel kullanıcı görünümleri

Özel bir kullanıcı görünümü ekleyebilirsiniz, bu görünümü düzenleyebilir veya silebilirsiniz; değişiklikler Filtre listesinde gösterilir. Bu değişiklikler, şirketinizin tüm yöneticilerinin Kullanıcılar sayfasına **gidecekleri zaman göreceği şekilde** görüntülenir. En çok 50 özel görünüm oluşturabilirsiniz. 

> [!TIP]
>  Standart kullanıcı görünümleri, Filtreler açılan **listesinde varsayılan** olarak görüntülenir. Standart **filtreler şunlardır**: Tüm **kullanıcılar, Lisanslı** **kullanıcılar, Konuk**  **kullanıcılar, Oturum** açma izni **verildi, Oturum** açma **engellendi,** Lisanssız **kullanıcılar, Hatalı** **kullanıcılar, Faturalama** **yöneticileri, Genel** **yöneticiler, Yardım** masası **yöneticileri, Hizmet** yöneticileri ve Kullanıcı yönetimi **yöneticileri**. Standart görünümleri düzenleyemez veya silemezsiniz. 

Standart görünümler hakkında dikkat gereken birkaç şey: 

- Listede 2.000'den fazla kullanıcı varsa, bazı standart görünümlerde sıralanmamış bir liste görüntülenir. Bu listede belirli kullanıcıları bulmak için arama kutusunu kullanın. 
- Microsoft'tan fatura Microsoft 365, **Fatura** yöneticileri standart görünümler listesinde görünmez. Daha fazla bilgi için bkz [. Yönetici rolleri atama](assign-admin-roles.md). 
  
## <a name="choose-the-filters-for-your-custom-user-view"></a>Özel kullanıcı görünümünüz için filtreleri seçme

Özel görünümlerinizi Özel filtre bölmesinde oluşturabilir ve **düzenleyebilirsiniz** . Birden çok filtre seçeneğiniz varsa, tüm seçili ölçütlere uyan kullanıcıları içeren sonuçlar elde olur. Aşağıdaki örnekte, Kanada'da olan belirli bir etki alanındaki tüm kullanıcıları gösteren"Kanada kullanıcıları" adında özel bir görünümün nasıl oluşturul adımlarıyla oluşturlları gerekir. 

  
 **A - Etki Alanı** Kurum için birden çok etki alanınız varsa, kullanılabilir etki alanları açılır listesinden seçim kullanabilirsiniz. 
  
 **B - Oturum açma durumu** İzin verilen veya engellenen kullanıcıları seçin. 
  
 **C - Konum** Ülke açılan listesinden bir konum seçin. 
  
 **D - Atanan ürün lisansı** Açılan lisans listesinden, kurumda kullanılabilen lisanslar seçin. Seçtiğiniz lisansa sahip kullanıcıları göstermek için bu filtreyi kullanın. Kullanıcıların da ek lisansları olabilir. 
  
Ayrıca bölüm, şehir, il, ülke veya bölge veya iş unvanı gibi organizasyonda kullanılan ek kullanıcı profili ayrıntılarına göre de filtreyi kaldırabilirsiniz.
  
 **Diğer koşullar:**
  
- **Yalnızca eşitlenmiş kullanıcılar** Kullanıcıların etkinleştirilmiş olup olmadığı önemli değildir; yerel Active Directory ile eşitlenen tüm kullanıcıları göstermek için bu kutuyu seçin. 
    
- **Hatalı kullanıcılar** Sağlama hatası olan kullanıcılara göstermek için bu kutuyu seçin. 
    
- **Lisanssız kullanıcılar** Lisans atanmamış tüm kullanıcıları bulmak için bu kutuyu seçin. Bu görünümün sonuçları, posta kutusu kullanıcısı olan ancak Exchange lisansına sahip olan kullanıcıları da içerebilir. Bu kullanıcıları özellikle izlemek için, Lisanssız kullanıcılar **filtresini kullanarak posta kutuları Exchange arşivleri kullanın**. Bu görünümün sonuçları, arşivinde lisans Exchange olan kullanıcıları da içerebilir.
    
- **Exchange** posta kutuları veya arşivleri olan lisanssız kullanıcılar Exchange Online'de oluşturulmuş, Exchange posta kutusu olan ancak Microsoft 365 lisansı atanmamış kullanıcı hesaplarını göstermek için bu kutuyu seçin. Bu filtrenin sonuçları, arşive bir arşive atanmış veya bu filtreye Exchange içerir. 

> [!NOTE]
> Şu **olduğunda posta kutuları filtresini Exchange Lisanssız** kullanıcılar çalışır:
1. Posta kutusu yakın zamanda paylaşılan **kullanıcıya dönüştürülen** **ve** lisansı yok.
2. Posta kutusu yakın zamanda Başka bir Microsoft 365 ancak bir lisans atanmamış.
3. Posta kutusu PowerShell kullanılarak oluşturulmuş ve bir lisans atanmamış.
4. Şirket içinde oluşturulmuş yeni bir posta kutusu ve kullanıcıya New-RemoteMailbox cmdlet'i sağlandı.
    
> [!TIP]
> 2.000'den fazla kullanıcı döndüren özel bir görünüm ekleyebilirsiniz, sonuçta elde edilen kullanıcı listesi sıralanmayacaktır. Bu durumda, arama kutusunu kullanarak kullanıcıları bulun veya aramanızı iyileştirmek üzere özel görünümlerinizi düzenleyin. 
  
## <a name="create-a-custom-user-view"></a>Özel kullanıcı görünümü oluşturma

::: moniker range="o365-worldwide"

1. Yönetim merkezinde Kullanıcılar Etkin **kullanıcılar'a** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">gidin</a>.
  
::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetim merkezinde Kullanıcılar Etkin **kullanıcılar'a** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">gidin</a>.  

::: moniker-end
    
2. Etkin kullanıcılar **sayfasında Filtreler'i** ve **ardından Yeni** **filtre'yi seçin**.
  
3. Özel **filtre sayfasında** , filtrenizin adını girin, özel filtrenizin koşullarını seçin ve sonra da Ekle'yi **seçin**. Özel görünümünüz artık filtre açılan listesine eklidir.

## <a name="edit-or-delete-a-custom-user-view"></a>Özel kullanıcı görünümünü düzenleme veya silme

::: moniker range="o365-worldwide"

1. Yönetim merkezinde Kullanıcılar Etkin **kullanıcılar'a** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">gidin</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Yönetim merkezinde Kullanıcılar Etkin **kullanıcılar'a** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">gidin</a>. 

::: moniker-end 
    
2. Etkin **kullanıcılar sayfasında Filtre'yi** **seçin**, değiştirmek istediğiniz filtreyi seçin ve sonra da Filtreyi **düzenle'yi seçin**. 
    
    > [!TIP]
    > Yalnızca özel görünümleri düzenleyebilirsiniz. 
  
3. Özel **filtre sayfasında** , bilgileri gereken şekilde düzenleyin ve ardından Kaydet'i **seçin**. Filtreyi silmek için sayfanın alt kısmında Sil'i **de seçin**. 

## <a name="related-content"></a>İlgili içerik

[Videoya genel Microsoft 365 yönetim merkezi](../admin-overview/admin-center-overview.md) (video)\
[Yönetici rolleri hakkında](../add-users/about-admin-roles.md) (video)\
[Kuruluş için Microsoft 365 temasını özelleştirme](../setup/customize-your-organization-theme.md) (makale)


     
