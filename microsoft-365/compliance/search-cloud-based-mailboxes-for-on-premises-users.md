---
title: Şirket içi kullanıcılar için Teams sohbet verilerini arama
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Yöneticiler, Exchange karma dağıtımdaki şirket içi kullanıcılar için Teams sohbet verilerini aramak ve dışarı aktarmak için Microsoft 365'deki eBulma araçlarını kullanabilir.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 4af64bd77d820b67314bc37e574afdff3966d21b
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014354"
---
# <a name="search-for-teams-chat-data-for-on-premises-users"></a>Şirket içi kullanıcılar için Teams sohbet verilerini arama

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Kuruluşunuzun Exchange karma dağıtımı varsa (veya kuruluşunuz şirket içi Exchange kuruluşunu Office 365 ile eşitlediyse) ve Microsoft Teams etkinleştirdiyse, şirket içi kullanıcılar anlık ileti için Teams sohbet uygulamasını kullanabilir. Bulut tabanlı bir kullanıcı için, Teams sohbet verileri (*1x1 veya 1xN sohbetleri* olarak da adlandırılır) birincil bulut tabanlı posta kutusuna kaydedilir. Şirket içi kullanıcı Teams sohbet uygulamasını kullandığında, sohbet iletileri şirket içinde bulunan birincil posta kutusunda depolanamaz. Bu sınırlamayı geçici olarak çözmek için Microsoft, şirket içi kullanıcılar için Teams sohbet verilerini aramak ve dışarı aktarmak için eBulma araçlarını kullanmanız için bulut tabanlı bir depolama alanının oluşturulduğu yeni bir özellik yayımladı.
  
Şirket içi kullanıcılar için bulut tabanlı depolamayı etkinleştirmeye yönelik gereksinimler ve sınırlamalar şunlardır:
  
- Şirket içi dizin hizmetinizdeki kullanıcı hesapları (Active Directory gibi) Microsoft 365'daki dizin hizmeti olan Azure Active Directory ile eşitlenmelidir. Bu, posta kullanıcı hesabının Microsoft 365 oluşturulduğu ve birincil posta kutusu şirket içi kuruluşta bulunan bir kullanıcıyla ilişkili olduğu anlamına gelir.

- Birincil posta kutusu şirket içi kuruluşta bulunan kullanıcıya Microsoft Teams lisansı ve en az bir Exchange Online Plan 1 lisansı atanmalıdır.

- Kuruluşunuzun Exchange karma dağıtımı yoksa, şirket içi Exchange şemanızı Azure Active Directory ile eşitlemeniz gerekir. Bunu yapmazsanız, şirket içi Exchange kuruluşunuzda posta kutusu olan kullanıcılar için Exchange Online içinde yinelenen bulut tabanlı posta kutuları oluşturma riskiyle karşılayabilirsiniz.

- Yalnızca şirket içi kullanıcıyla ilişkili Teams sohbet verileri bulut tabanlı depolama alanında depolanır. Şirket içi kullanıcı bu depolama alanına hiçbir şekilde erişemez.

> [!NOTE]
> Teams kanal konuşmaları her zaman Ekiple ilişkili bulut tabanlı posta kutusunda depolanır ve bu da kanal konuşmalarını arayabileceğiniz anlamına gelir. Teams kanal konuşmalarını arama hakkında daha fazla bilgi için bkz[. arama Microsoft Teams ve Microsoft 365 Grupları](content-search-reference.md#searching-microsoft-teams-and-microsoft-365-groups).
  
## <a name="how-it-works"></a>Nasıl çalışır?

Microsoft Teams etkin bir kullanıcının şirket içi posta kutusu varsa ve kullanıcı hesabı/kimliği bulutla eşitlenmişse, Microsoft şirket içi kullanıcının 1xN Teams sohbet verilerini ilişkilendirmek için bulut tabanlı depolama alanı oluşturur. Şirket içi kullanıcılar için sohbet verileri Teams arama için dizine eklenir. Bu, şirket içi kullanıcılar için Teams sohbet verilerini aramak, önizlemek ve dışarı aktarmak için İçerik aramasını (ve Microsoft Purview eKeşif (Standart) ve Microsoft Purview eKeşif (Premium) servis talepleri ile ilişkili aramaları) kullanmanıza olanak tanır. Şirket içi kullanıcılar için Teams sohbet verilerini aramak için Güvenlik & Uyumluluk PowerShell'deki ComplianceSearch cmdlet'lerini de kullanabilirsiniz **\***.
  
Aşağıdaki grafikte, şirket içi kullanıcılar için Teams sohbet verilerinin arama, önizleme ve dışarı aktarma için nasıl kullanılabilir olduğu iş akışı gösterilmektedir.
  
![Microsoft Teams'deki şirket içi kullanıcılar için bulut tabanlı depolama.](../media/EHAMShard1.png)
  
Bu özelliğe ek olarak, bulut tabanlı SharePoint sitesinde Teams içeriği aramak, önizlemek ve dışarı aktarmak için eBulma araçlarını ve bulut tabanlı kullanıcılar için Exchange Online posta kutusunda her Microsoft Team ve 1xN Teams sohbet verileriyle ilişkilendirilmiş Exchange posta kutusunu da kullanabilirsiniz.

## <a name="searching-for-teams-chat-content-for-on-premises-users"></a>Şirket içi kullanıcılar için Teams sohbet içeriği arama

Şirket içi kullanıcılar için Teams sohbet verilerini aramak için Microsoft Purview uyumluluk portalında İçerik arama özelliğini şu şekilde kullanabilirsiniz. Şirket içi kullanıcıların sohbet verilerini aramak için eBulma (Standart) içindeki arama aracını da kullanabilirsiniz.
  
1. Uyumluluk portalında **İçerik arama'ya** gidin.

2. **Aramalar** sekmesinde **Yeni arama'ya** tıklayın ve yeni aramayı adlandırın.

3. **Konumlar** sayfasında, Exchange posta kutuları için iki durumlu düğmeyi **Açık** olarak ayarlayın.

4. Belirli kullanıcılar için (şirket içi kullanıcılar dahil) Teams içerik aramak için **Kullanıcı, grup veya ekip seç'i** seçin ve aramaya eklenecek belirli kullanıcıları seçin. Belirli kullanıcıları listelemezseniz, arama şirket içi kullanıcılar da dahil olmak üzere tüm kullanıcıları içerir.

5. **Şirket içi kullanıcılar için uygulama içeriği ekle** onay kutusunun seçili olduğundan emin olun. Bu, şirket içi kullanıcılar için bulut tabanlı depolamanın aranmasını sağlar.

    ![Konumlar sihirbazı sayfasında "Şirket içi kullanıcılar için Office uygulaması içerik ekle" onay kutusunu seçin.](../media/EHAMShardCheckBox.png)

6. **Arama koşullarınızı tanımlayın** sayfasında bir anahtar sözcük sorgusu oluşturun ve gerekirse arama sorgusuna koşullar ekleyin. Yalnızca Ekip sohbetleri verilerini aramak için **Anahtar Sözcükler** kutusuna aşağıdaki sorguyu ekleyebilirsiniz:

    ```text
    kind:im AND kind:microsoftteams
    ```

6. Aramayı gönderin ve çalıştırın. Şirket içi kullanıcılar için tüm arama sonuçları diğer arama sonuçları gibi önizlenebilir. Arama sonuçlarını (Teams sohbet verileri dahil) pst dosyasına da aktarabilirsiniz. Daha fazla bilgi için bkz.:

    - [Arama oluşturma](content-search.md)

    - [Arama sonuçlarını önizleme](preview-ediscovery-search-results.md)

    - [Arama sonuçlarını dışarı aktarma](export-search-results.md)

## <a name="using-powershell-to-search-for-teams-chat-data-for-on-premises-users"></a>Şirket içi kullanıcılar için Teams sohbet verilerini aramak için PowerShell kullanma

Şirket içi kullanıcılar için Teams sohbet verilerini aramak için Güvenlik & Uyumluluk PowerShell'deki **New-ComplianceSearch** cmdlet'lerini kullanabilirsiniz. Daha önce açıklandığı gibi, şirket içi kullanıcılar için Teams sohbet verilerini aramak için PowerShell'i kullanmak üzere bir destek isteği göndermeniz gerekmez.
  
1. [Güvenlik & Uyumluluğu PowerShell'e Bağlan](/powershell/exchange/connect-to-scc-powershell).

2. Şirket içi kullanıcılar için Teams sohbet verilerini arayan bir içerik araması oluşturmak için aşağıdaki PowerShell komutunu çalıştırın.

    ```powershell
    New-ComplianceSearch <name of new search> -ContentMatchQuery <search query> -ExchangeLocation <on-premises user> -IncludeUserAppContent $true -AllowNotFoundExchangeLocationsEnabled $true  
    ```

    *IncludeUserAppContent* parametresi, *ExchangeLocation* parametresi tarafından belirtilen kullanıcı veya kullanıcılar için bulut tabanlı depolamayı belirtmek için kullanılır. *AllowNotFoundExchangeLocationsEnabled*, şirket içi kullanıcılar için bulut tabanlı depolamada arama yapmanızı sağlar. Bu parametrenin `$true` değerini kullandığınızda, arama çalışmadan önce posta kutusunun varlığını doğrulamaya çalışmaz. Bu bulut tabanlı depolama normal bir bulut tabanlı posta kutusu olarak çözümlenemediğinden, şirket içi kullanıcılar için bulut tabanlı depolamada arama yapmak için bu gereklidir.

    Aşağıdaki örnek, Contoso kuruluşunda şirket içi kullanıcı olan Sara Davis için bulut tabanlı depolamada "redstone" anahtar sözcüğünü içeren Teams sohbetleri arar.
  
    ```powershell
    New-ComplianceSearch "Redstone_Search" -ContentMatchQuery "redstone AND (kind:im AND kind:microsoftteams)" -ExchangeLocation sarad@contoso.com -IncludeUserAppContent $true -AllowNotFoundExchangeLocationsEnabled $true  
    ```

   Arama oluşturduktan sonra, aramayı çalıştırmak için **Start-ComplianceSearch** cmdlet'ini kullandığınızdan emin olun.
  
Bu cmdlet'leri kullanarak daha fazla bilgi için bkz:
  
- [New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch)

- [Start-ComplianceSearch](/powershell/module/exchange/start-compliancesearch)

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda şirket içi kullanıcılar için Teams sohbet verilerini arayabilir, önizleyebilir ve dışarı aktarabilirsiniz. Ayrıca, şirket içi bir kullanıcının Teams sohbet verilerini Bir Çekirdek veya eBulma (Premium) olayıyla ilişkili ayrı tutmaya alabilir ve şirket içi kullanıcılar için Teams sohbetler veya kanal iletileri için bekletme ilkesi uygulayabilirsiniz. Ancak şu anda şirket içi kullanıcılar için diğer içerik konumları (Exchange posta kutuları ve SharePoint siteleri gibi) için bekletme ilkesi uygulayamazsınız.

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

**Şirket içi kullanıcıların sohbet iletilerini aramak için bir destek isteği göndermem gerekiyor mu?**

Hayır. Bu özellik tüm kuruluşlar için varsayılan olarak etkindir. Bir noktada, Microsoft Desteği ile iletişim kurmanız gerekirdi, ancak artık böyle bir durum söz konusu değildir.
  
 **eBulma araçları, bu özelliğin tüm kuruluşlar için varsayılan olarak etkinleştirildiği zamandan önce şirket içi kullanıcılar için eski Teams sohbet verilerini bulabilir mi?**
  
Microsoft, şirket içi kullanıcılar için Teams sohbet verilerini 31 Ocak 2018'de depolamaya başlamıştır. Bu nedenle, şirket içi Teams kullanıcının kimliği bu tarihten bu yana Microsoft 365 şirket içi Active Directory ve Azure Active Directory arasında eşitlendiyse, Teams sohbet verileri bulutta depolanır ve eBulma araçları kullanılarak aranabilir .

 **Şirket içi kullanıcıların Teams sohbet verilerini bulutta depolamak için lisansa ihtiyacı var mı?**
  
Evet. Şirket içi bir kullanıcının Teams sohbet verilerini bulut tabanlı depolama alanında depolamak için kullanıcıya Microsoft Teams lisansı ve Office 365 (veya Microsoft 365) Exchange Online Planı lisansı atanmalıdır.

**Şirket içi kullanıcılar için bulut tabanlı depolama nerede bulunur?**
  
Teams sohbet verileri, şirket içi bir kullanıcının Tercih Edilen Veri Konumu'nda (PDL) depolanır. PDL hem Single-Geo hem de Multi-Geo ortamlarında kabul edilir. Daha fazla bilgi için bkz[. Multi-Geo Microsoft 365](../enterprise/microsoft-365-multi-geo.md).

**Kullanıcının şirket içi posta kutusu buluta geçirilirse Teams sohbet verilerini kaybetme riski var mı?**
  
Hayır. Şirket içi kullanıcının birincil posta kutusunu buluta geçirdiğinizde, bu kullanıcının Teams sohbet verileri yeni bulut tabanlı birincil posta kutusuna geçirilecektir.
  
 **Şirket içi kullanıcılara eBulma saklama veya bekletme ilkeleri uygulayabilir miyim?**
  
Evet. Şirket içi kullanıcıların Teams sohbetleri ve kanal iletileri için eBulma tutmaları veya bekletme ilkeleri uygulayabilirsiniz. Ancak şirket içi kullanıcıların Teams içeriğini korumak veya korumak için şirket içi kullanıcıya Exchange Online Plan 2 lisansı atanmalıdır.
