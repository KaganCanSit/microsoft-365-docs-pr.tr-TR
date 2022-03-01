---
title: Şirket Teams için sohbet verilerini arama
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: high
search.appverid:
- MOE150
- MST160
- MET150
ms.assetid: 3f7dde1a-a8ea-4366-86da-8ee6777f357c
description: Yöneticiler, Microsoft 365'te eBulma araçlarını kullanarak, Teams bir karma dağıtımda şirket içi kullanıcıların sohbet verilerini Exchange dışarı aktarabilirsiniz.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: fdd142783313418c8c65c04f9b5e344ff325ec2c
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021607"
---
# <a name="search-for-teams-chat-data-for-on-premises-users"></a>Şirket Teams için sohbet verilerini arama

Kuruluşta Exchange karma dağıtımı varsa (veya organizasyonunız şirket içi Exchange kuruluşunu Office 365 ile eşitler) ve Microsoft Teams'i etkinleştirdiyse, şirket içi kullanıcılar anlık ileti için Teams sohbet uygulamasını kullanabilir. Bulut tabanlı bir kullanıcı için Teams sohbet verileri (*1x1 veya 1xN* sohbet olarak da adlandırılan) birincil bulut tabanlı posta kutusuna kaydedilir. Şirket içi bir kullanıcı Teams sohbet uygulamasını kullandığında, bu kullanıcının sohbet iletileri şirket içinde bulunan birincil posta kutusunda depolanmayacaktır. Bu sınırlamayı temel almak için, Microsoft bulut tabanlı bir depolama alanı oluşturulmuş yeni bir özellik yayınladı. Bu nedenle, şirket içi kullanıcılar için eBulma araçlarını kullanarak Teams verilerini arayabilir ve dışarı aktarabilirsiniz.
  
Şirket içi kullanıcılar için bulut tabanlı depolamayı etkinleştirmeyle ilgili gereksinimler ve sınırlamalar:
  
- Şirket içi dizin hizmetinizin (örneğin, Active Directory) kullanıcı hesaplarının, Azure Active Directory'te dizin hizmeti olan Microsoft 365. Bu, Posta Kutusu'nda bir posta kullanıcı hesabının Microsoft 365, birincil posta kutusu şirket içi kuruluşta yer alan bir kullanıcıyla ilişkilendiril olduğu anlamına gelir.

- Birincil posta kutusu şirket içi kuruluşta yer alan kullanıcıya Microsoft Teams lisansı ve Plan 1 lisansının en Exchange Online atanmamış olması gerekir.

- Kuruluşun karma dağıtımı yoksa, Exchange dağıtım şemanızı eşitlemek için şirket içi Exchange eşitlemeniz Azure Active Directory. Bunu yapsanız bile, şirket içi posta kutusu Exchange Online veya kuruluş içinde posta kutusu olan kullanıcılar için Exchange Online bulut tabanlı yinelenen posta kutuları oluşturma Exchange olabilir.

- Yalnızca Teams kullanıcıyla ilişkilendirilmiş sohbet verileri bulut tabanlı depolama alanında depolanır. Şirket içi kullanıcılar bu depolama alanına herhangi bir şekilde erişe sahiptir.

> [!NOTE]
> Teams görüşmeleri her zaman Ekiple ilişkilendirilmiş bulut tabanlı posta kutusunda depolanır ve bu da kanal konuşmalarını arayabilirsiniz anlamına gelir. Kanal konuşmalarında arama Teams daha fazla bilgi için bkz. [Gruplarda Microsoft Teams ve Microsoft 365.](content-search-reference.md#searching-microsoft-teams-and-microsoft-365-groups)
  
## <a name="how-it-works"></a>Nasıl çalışır?

Microsoft Teams etkinleştirilmiş bir kullanıcının şirket içi posta kutusu varsa ve kullanıcının hesabı/kimliği bulutla eşitlenense, Microsoft şirket içi kullanıcının 1xN ve sohbet verilerini ilişkilendirmek için bulut tabanlı Teams oluşturur. Teams kullanıcıların sohbet verileri, arama için dizine alındı. Bu özellik, şirket içi kullanıcıların sohbet verilerini aramak Teams, önizlemek ve dışarı Advanced eDiscovery için İçerik aramalarını (ve Core eK bulma ve Advanced eDiscovery aramaları) kullanmanızı sağlar. Ayrıca, Güvenlik ve **Uyumluluk\*** Merkezi PowerShell'de ComplianceSearch cmd & let'lerini kullanarak Teams kullanıcıların sohbet verilerini arayabilirsiniz.
  
Aşağıdaki grafikte, şirket içi kullanıcıların Teams verileri için arama, önizleme ve dışarı aktarmada nasıl kullanılabilir olduğuyla ilgili iş akışı görüntülenir.
  
![şirket içi kullanıcıların bulut tabanlı depolama alanı Microsoft Teams.](../media/EHAMShard1.png)
  
Bu özelliğin yanı sıra, bulut tabanlı SharePoint sitesinde ve her Microsoft Team ile ilişkilendirilmiş Exchange posta kutusunda Teams içeriğini aramak, önizlemek ve dışarı aktarmak için eBulma araçlarını ve bulut tabanlı kullanıcılar için Exchange Online posta kutusunda 1xN Teams sohbet verilerini de kullanabilirsiniz.

## <a name="searching-for-teams-chat-content-for-on-premises-users"></a>Şirket Teams kullanıcılarının sohbet içeriğini arama

Şirket içi kullanıcıların sohbet verilerini aramak Microsoft 365 uyumluluk merkezi için Teams arama özelliğinde İçerik arama'nın nasıl kullanılır? Ayrıca, Core eKover'daki arama aracını kullanarak şirket içi kullanıcılar için sohbet verilerini de arayabilirsiniz.
  
1. İçerik Microsoft 365 uyumluluk merkezi **arama'ya gidin**.

2. Aramalar **sekmesinde Yeni** **arama'ya tıklayın** ve yeni aramaya bir ad girin.

3. Konumlar **sayfasında**, posta kutuları için iki **durumlu** düğmeyi Exchange ayarlayın.

4. Belirli kullanıcılar (Teams şirket içi kullanıcılar dahil) için Arama yapmak için Kullanıcı **,** grup veya ekip seç'i seçin ve aramaya dahil etmek üzere belirli kullanıcıları seçin. Belirli kullanıcıları listele listeniz yoksa, aramada şirket içi kullanıcılar da dahil olmak üzere tüm kullanıcılar yer a olur.

5. Şirket içi **kullanıcılar için uygulama içeriği ekle onay kutusunun seçili** olduğundan emin olun. Bu, şirket içi kullanıcılar için bulut tabanlı depolamada arama yapılmasını sağlar.

    ![Konumlar sihirbazı Office uygulaması "Şirket içi kullanıcılar için posta kutusu içeriği ekle" onay kutusunu seçin.](../media/EHAMShardCheckBox.png)

6. Arama **koşullarınızı tanımlayın sayfasında** bir anahtar sözcük sorgusu oluşturun ve gerekirse arama sorgusuna koşullar ekleyin. Yalnızca Ekip sohbetleri verilerini aramak için Anahtar sözcükler kutusuna aşağıdaki **sorguyu** ekleyebilirsiniz:

    ```text
    kind:im AND kind:microsoftteams
    ```

6. Gönderin ve arama çalıştırın. Şirket içi kullanıcıların tüm arama sonuçları, diğer tüm arama sonuçları gibi önizlemede 2222 olarak görüntülenir. Ayrıca arama sonuçlarını (tüm sohbet verileri dahil) Teams bir PST dosyasına aktarabilirsiniz. Daha fazla bilgi için bkz.:

    - [Arama oluşturma](content-search.md)

    - [Arama sonuçlarını önizleme](preview-ediscovery-search-results.md)

    - [Arama sonuçlarını dışarı aktarma](export-search-results.md)

## <a name="using-powershell-to-search-for-teams-chat-data-for-on-premises-users"></a>PowerShell kullanarak şirket Teams sohbet verilerini arama

Güvenlik ve **Uyumluluk Merkezi** PowerShell'de Yeni Uyumluluk Arama cmdlet'& lerini kullanarak şirket içi kullanıcıları Teams sohbet verilerini arayabilirsiniz. Daha önce de belirtildiği gibi, PowerShell kullanarak şirket içi kullanıcıların sohbet Teams için destek isteği göndermeniz gerekmektedir.
  
1. [Bağlan ve Uyumluluk & PowerShell'e.](/powershell/exchange/connect-to-scc-powershell)

2. Aşağıdaki PowerShell komutunu çalıştırarak, şirket içi kullanıcılar için Teams verilerinde arama yapılan içerik araması oluşturun.

    ```powershell
    New-ComplianceSearch <name of new search> -ContentMatchQuery <search query> -ExchangeLocation <on-premises user> -IncludeUserAppContent $true -AllowNotFoundExchangeLocationsEnabled $true  
    ```

    *IncludeUserAppContent* parametresi, *ExchangeLocation* parametresiyle belirtilen kullanıcı veya kullanıcıların bulut tabanlı depolama alanını belirtmek için kullanılır. *AllowNotFoundExchangeLocationsEnabled*, bulut tabanlı depolamada şirket içi kullanıcıları aramanızı sağlar. Bu parametrenin `$true` değerini kullanırken, arama çalışmadan önce posta kutusunun varlığını doğrulamaya çalışmaz. Bu, şirket içi kullanıcıları bulut tabanlı depolamada aramak için gereklidir, çünkü bu bulut tabanlı depolama normal bir bulut tabanlı posta kutusu olarak çözümleyici değildir.

    Aşağıdaki örnekte, Contoso Teams şirket içi kullanıcısı Olan Sara Davis için bulut tabanlı depolamada "redstone" anahtar sözcüğü içeren sarı metin sohbetleri için arama yapabilirsiniz.
  
    ```powershell
    New-ComplianceSearch "Redstone_Search" -ContentMatchQuery "redstone AND (kind:im AND kind:microsoftteams)" -ExchangeLocation sarad@contoso.com -IncludeUserAppContent $true -AllowNotFoundExchangeLocationsEnabled $true  
    ```

   Arama oluşturdukktan sonra, aramanızı çalıştırmak için **Start-ComplianceSearch** cmdlet'ini kullanmaya devam edin.
  
Bu cmdlet'leri kullanma hakkında daha fazla bilgi için bkz:
  
- [New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch)

- [Start-ComplianceSearch](/powershell/module/exchange/start-compliancesearch)

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda, şirket içi kullanıcıların sohbet verisinde arama Teams önizleme ve dışarı aktarma özelliği bulunmaktadır. Ayrıca Core veya Advanced eDiscovery durumuyla ilişkilendirilmiş bir şirket içi kullanıcının Teams sohbet verilerini yerinde saklamaya ve şirket içi kullanıcılar için Teams sohbetleri veya kanal iletileri için bekletme ilkesi uygulayabilirsiniz. Ancak şu anda, şirket içi kullanıcılara diğer içerik konumlarını (örneğin, Exchange posta kutularını ve SharePoint sitelerini) bekletme ilkesi uygulayaabilirsiniz.

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

**Şirket içi kullanıcıların sohbet iletilerini aramak için bir destek isteği göndermem gerekir mi?**

Hayır. Bu özellik tüm kuruluşlar için varsayılan olarak etkindir. Bir noktada Microsoft Desteği'ne başvurarak bağlantı kurmanız gerekirdi, ancak artık böyle değildir.
  
 **eBulma araçları, bu Teams tüm kuruluşlarda varsayılan olarak etkinleştirilmeden önce şirket içi kullanıcıların eski sohbet verilerini bulabilir mi?**
  
Microsoft, şirket Teams sohbet verilerini 31 Ocak 2018'de depolamaya başladı. Dolayısıyla, şirket içi Teams kullanıcılarının kimliği, bu tarihten itibaren şirket içi Active Directory ile Microsoft 365'te Azure Active Directory arasında eşitlanmışsa, Teams sohbet verileri bulutta depolanır ve eBulma araçları kullanılarak aranabilir.

 **Şirket içi kullanıcıların, kullanıcılarının sohbet verilerini bulutta Teams için lisansa ihtiyacı var mı?**
  
Evet. Şirket içi Teams bulut tabanlı bir depolamada şirket içi bir kullanıcının sohbet verilerini depolamak için, kullanıcıya Microsoft Teams lisansı ve Office 365'de Exchange Online Planı lisansı (veya Microsoft 365) atanabilir.

**Şirket içi kullanıcıların bulut tabanlı depolaması nerede?**
  
Teams sohbet verileri, şirket içi kullanıcı için Tercih Edilen Veri Konumu'nda (PDL) depolanır. PDL hem coğrafi ortamlarda Single-Geo Multi-Geo ortamlarında bulunmaktadır. Daha fazla bilgi için bkz[. Microsoft 365 Multi-Geo](../enterprise/microsoft-365-multi-geo.md).

**Kullanıcının şirket içi posta kutusu buluta Teams bu kullanıcının sohbet verilerini kaybetme riski var mı?**
  
Hayır. Şirket içi kullanıcının birincil posta kutusunu buluta geçirerek, bu kullanıcının Teams sohbet verileri yeni bulut tabanlı birincil posta kutusuna geçirilir.
  
 **Şirket içi kullanıcılara eBulma saklama veya bekletme ilkeleri uygulayabilir miyim?**
  
Evet. Şirket içi kullanıcıların sohbetlerini ve kanal iletilerini Teams için eKbulma bekletmeleri veya bekletme ilkeleri uygulayabilirsiniz. Ancak şirket içi kullanıcıların Teams korumak veya korumak için, şirket içi kullanıcıya Exchange Online Plan 2 lisansı atanabilir.
