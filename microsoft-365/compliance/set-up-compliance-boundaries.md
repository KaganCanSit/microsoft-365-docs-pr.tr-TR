---
title: eBulma araştırmaları için uyumluluk sınırlarını ayarlama
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: 1b45c82f-26c8-44fb-9f3b-b45436fe2271
description: eBulma yöneticisinin Microsoft 365'te arayabileceği kullanıcı içerik konumlarını denetleyebilen mantıksal sınırlar oluşturmak için uyumluluk sınırlarını kullanmayı öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 903992df71b82a7dc1081bb286871e0b7af72d37
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625071"
---
# <a name="set-up-compliance-boundaries-for-ediscovery-investigations"></a>eBulma araştırmaları için uyumluluk sınırlarını ayarlama

Araştırma yönetmek için Microsoft Purview eKeşif (Standart) veya Microsoft Purview eKeşif (Premium) kullanılırken bu makaledeki yönergeler uygulanabilir.

Uyumluluk sınırları, eBulma yöneticilerinin arayabileceği kullanıcı içerik konumlarını (posta kutuları, OneDrive hesapları ve SharePoint siteleri gibi) denetleyebilen bir kuruluş içinde mantıksal sınırlar oluşturur. Ayrıca, uyumluluk sınırları kuruluşunuzdaki yasal, insan kaynaklarını veya diğer soruşturmaları yönetmek için kullanılan eBulma olaylarına kimlerin erişebileceğini denetler. Uyumluluk sınırlarına duyulan ihtiyaç genellikle coğrafi kurullara ve düzenlemelere uymak zorunda olan çok uluslu şirketler ve genellikle farklı kurumlara ayrılan hükümetler için gereklidir. Microsoft 365'te uyumluluk sınırları, içerik aramaları yaparken ve eBulma olaylarıyla araştırma yönetirken bu gereksinimleri karşılamanıza yardımcı olur.
  
Uyumluluk sınırlarının nasıl çalıştığını açıklamak için aşağıdaki çizimdeki örneği kullanırız.
  
![Uyumluluk sınırları, eBulma olaylarına erişimi denetleen ajanslara ve yönetici rol gruplarına erişimi denetleen arama izinleri filtrelerinden oluşur.](../media/M365_ComplianceBoundary_OrgChart_v2.png)
  
Bu örnekte Contoso LTD, Fourth Coffee ve Coho Winery gibi iki yan kuruluşa sahip bir kuruluşdur. İşletme, eBulma yöneticilerinin ve araştırmacılarının yalnızca exchange posta kutularını, OneDrive hesaplarını ve SharePoint sitelerini kendi kuruluşlarında aramalarını gerektirir. Ayrıca, eBulma yöneticileri ve araştırmacıları yalnızca kendi kuruluşlarında eBulma vakalarını görebilir ve yalnızca üyesi oldukları davalara erişebilirler. Bu senaryoya ek olarak, araştırmacılar içerik konumlarını ayrı tutamaz veya bir servis talebinin içeriğini dışarı aktaramaz. Uyumluluk sınırları bu gereksinimleri şu şekilde karşılar.
  
- eBulma için arama izinleri filtreleme işlevi, eBulma yöneticilerinin ve araştırmacıların arayabileceği içerik konumlarını denetler. Bu, Fourth Coffee ajansındaki eKeşif yöneticileri ve araştırmacılarının yalnızca Fourth Coffee yan kuruluşundaki içerik konumlarında arama yapabilecekleri anlamına gelir. Aynı kısıtlama Coho Winery yan kuruluşu için de geçerlidir.

- [Rol grupları](assign-ediscovery-permissions.md#rbac-roles-related-to-ediscovery) uyumluluk sınırları için aşağıdaki işlevleri sağlar:

  - Microsoft Purview uyumluluk portalı eBulma servis taleplerini kimlerin görebileceğini denetleme. Bu, eBulma yöneticilerinin ve araştırmacılarının yalnızca kendi kuruluşlarında eBulma davalarını görebileceği anlamına gelir.

  - eBulma servis talebine kimlerin üye atayabileceğini denetleyin. Bu, eBulma yöneticilerinin ve araştırmacılarının üyeleri yalnızca kendi üye oldukları davalara atayabileceği anlamına gelir.

  - Belirli izinleri atayan roller ekleyerek veya kaldırarak üyelerin gerçekleştirebileceği eBulma ile ilgili görevleri denetleyin.

- Bir rol grubuna arama izinleri filtresi uygulandığında, rol grubuna eylem gerçekleştirme izinleri atandığı sürece rol grubunun üyeleri aramayla ilgili aşağıdaki eylemleri gerçekleştirebilir:

  - İçerik için arama yapma

  - Arama sonuçlarını önizleme

  - Arama sonuçlarını dışarı aktarma

  - Arama tarafından döndürülen öğeleri temizleme

Uyumluluk sınırlarını ayarlama işlemi aşağıdadır:
  
[1. Adım: Ajanslarınızı tanımlamak için bir kullanıcı özniteliği tanımlama](#step-1-identify-a-user-attribute-to-define-your-agencies)

[2. Adım: Her ajans için bir rol grubu oluşturma](#step-2-create-a-role-group-for-each-agency)

[3. Adım: Uyumluluk sınırını zorlamak için arama izinleri filtresi oluşturma](#step-3-create-a-search-permissions-filter-to-enforce-the-compliance-boundary)

[4. Adım: Kurum içi araştırmalarda eBulma olayı oluşturma](#step-4-create-an-ediscovery-case-for-intra-agency-investigations)

## <a name="before-you-set-up-compliance-boundaries"></a>Uyumluluk sınırlarını ayarlamadan önce

- Kullanıcılara bir Exchange Online lisansı atanmalıdır. Bunu doğrulamak için Exchange Online PowerShell'de [Get-User](/powershell/module/exchange/get-user) cmdlet'ini kullanın.

## <a name="step-1-identify-a-user-attribute-to-define-your-agencies"></a>1. Adım: Ajanslarınızı tanımlamak için bir kullanıcı özniteliği tanımlama

İlk adım, ajanslarınızı tanımlayacak bir öznitelik seçmektir. Bu öznitelik, eBulma yöneticisini yalnızca bu öznitelik için belirli bir değer atanmış kullanıcıların içerik konumlarını aramayla sınırlayan arama izinleri filtresi oluşturmak için kullanılır. Örneğin Contoso'nun **Department** özniteliğini kullanmaya karar vereceğini düşünelim. Fourth Coffee yan kuruluşundaki kullanıcılar için bu özniteliğin değeri ve  `FourthCoffee`  Coho Winery yan kuruluşundaki kullanıcıların değeri olacaktır `CohoWinery`. 3. Adımda, eBulma yöneticilerinin arayabileceği kullanıcı içerik konumlarını sınırlamak için bu  `attribute:value`  çifti (örneğin *, Department:FourthCoffee*) kullanırsınız. 
  
Uyumluluk sınırları için kullanabileceğiniz kullanıcı özniteliklerine bazı örnekler aşağıda verilmiştir:
  
- Şirket

- CustomAttribute1 - CustomAttribute15

- Bölüm

- Office

- CountryOrRegion (İki harfli ülke kodu)

Tam liste için desteklenen [posta kutusu filtrelerinin](/powershell/exchange/recipientfilter-properties#filterable-recipient-properties) tam listesine bakın.

## <a name="step-2-create-a-role-group-for-each-agency"></a>2. Adım: Her ajans için bir rol grubu oluşturma

Sonraki adım, uyumluluk portalında ajanslarınızla uyumlu olacak rol gruplarını oluşturmaktır. Yerleşik eBulma Yöneticileri grubunu kopyalayarak, uygun üyeleri ekleyerek ve gereksinimlerinize uygun olmayan rolleri kaldırarak bir rol grubu oluşturmanızı öneririz. eBulma ile ilgili roller hakkında daha fazla bilgi için bkz. [eBulma izinleri atama](assign-ediscovery-permissions.md).
  
Rol gruplarını oluşturmak için uyumluluk portalındaki **İzinler** sayfasına gidin ve her bir kuruluştaki her ekip için araştırma yönetmek için uyumluluk sınırlarını ve eBulma servis taleplerini kullanacak bir rol grubu oluşturun.
  
Contoso uyumluluk sınırları senaryosu kullanılarak dört rol grubunun oluşturulması ve her birine uygun üyelerin eklenmesi gerekir.
  
- Dördüncü Kahve eKeşif Yöneticileri

- Dördüncü Kahve Araştırmacıları

- Coho Winery eKeşif Yöneticileri

- Coho Winery Araştırmacıları
  
Contoso uyumluluk sınırları senaryosunun gereksinimlerini karşılamak için araştırmacıların içerik konumlarına **ayrı tutmalarını** ve bir servis talebindeki içeriği dışarı aktarmalarını önlemek için Araştırmacı rol gruplarından Ayrı Tutma ve **Dışarı Aktarma** rollerini de kaldırabilirsiniz.

> [!IMPORTANT]
> Bir rolün, servis talebine üye olarak eklediğiniz bir rol grubuna eklenmesi veya kaldırılması durumunda rol grubu, servis talebinin bir üyesi olarak (veya rol grubunun üyesi olduğu herhangi bir durumda) otomatik olarak kaldırılır. Bunun nedeni, kuruluşunuzun bir olayın üyelerine yanlışlıkla ek izinler sağlamasını korumaktır. Benzer şekilde, bir rol grubu silinirse, üyesi olduğu tüm durumlardan kaldırılır.

## <a name="step-3-create-a-search-permissions-filter-to-enforce-the-compliance-boundary"></a>3. Adım: Uyumluluk sınırını zorlamak için arama izinleri filtresi oluşturma

Her bir ajans için rol grupları oluşturduktan sonra, bir sonraki adım, her rol grubunu belirli bir kuruluşla ilişkilendiren ve uyumluluk sınırını tanımlayan arama izinleri filtreleri oluşturmaktır. Her bir ajans için bir arama izinleri filtresi oluşturmanız gerekir. Güvenlik izinleri filtreleri oluşturma hakkında daha fazla bilgi için bkz. [İçerik Arama için izin filtrelemeyi yapılandırma](permissions-filtering-for-content-search.md).
  
Bu makaledeki senaryo için uyumluluk sınırları için kullanılan bir arama izinleri filtresi oluşturmak için kullanılan söz dizimi aşağıda verilmiştir.

```powershell
New-ComplianceSecurityFilter -FilterName <name of filter> -Users <role groups> -Filters "Mailbox_<MailboxPropertyName>  -eq '<Value> '", "SiteContent_Path -like '<SharePointURL>' -or SiteContent_Path -like '<OneDriveURL>'"
```

Komuttaki her parametrenin açıklaması aşağıdadır:
  
- `FilterName`: Filtrenin adını belirtir. Filtrenin kullanıldığı ajansı tanımlayan veya tanımlayan bir ad kullanın.

- `Users`: Bu filtreyi gerçekleştirdikleri arama eylemlerine uygulayan kullanıcıları veya grupları belirtir. Uyumluluk sınırları için bu parametre, filtresini oluşturduğunuz kuruluştaki rol gruplarını (3. Adımda oluşturduğunuz) belirtir. Bu çok değerli bir parametredir, bu nedenle virgülle ayrılmış bir veya daha fazla rol grubu ekleyebilirsiniz.

- `Filters`: Filtrenin arama ölçütlerini belirtir. Uyumluluk sınırları için aşağıdaki filtreleri tanımlarsınız. Her biri farklı içerik konumları için geçerlidir.

  - `Mailbox`: Parametresinde tanımlanan `Users` rol gruplarının arayabileceği posta kutularını veya OneDrive hesaplarını belirtir. Bu filtre, rol grubu üyelerinin yalnızca belirli bir ajanstaki posta kutularında veya OneDrive hesaplarında arama yapmasına olanak tanır; örneğin, `"Mailbox_Department -eq 'FourthCoffee'"`.

  - `SiteContent`: Bu filtre iki ayrı filtre içerir. İlki `SiteContent_Path` , parametrede tanımlanan `Users` rol gruplarının arayabileceği sharepoint sitelerini belirtir. Örneğin, `SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee'`. İkinci `SiteContent_Path` filtre (operatör tarafından `or` ilk `SiteContent_Path` filtreye bağlı), ajansın OneDrive etki alanını (*Sitem* etki alanı olarak da adlandırılır) belirtir. Örneğin, `SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'`. Filtre yerine filtreyi `Site_Path` `SiteContent` de kullanabilirsiniz. `Site` ve `SiteContent` filtreleri birbirinin yerine kullanılabilir ve bu makalede açıklanan arama izinleri filtrelerini etkilemez.

    > [!IMPORTANT]
    > `SiteContent` OneDrive filtresi neden önceki arama izinleri filtresine dahil edilir? Filtre hem posta kutuları *hem de* OneDrive hesapları için geçerli olsa `Mailbox` da, OneDrive filtresini de eklemediyseniz SharePoint filtresinin eklenmesi OneDrive `Site` hesaplarını dışlar. Arama izinleri filtresi bir SharePoint filtresi içermiyorsa, Posta Kutusu filtresi uyumluluk sınırının kapsamına OneDrive hesaplarını dahil edeceğinden ayrı bir OneDrive filtresi eklemeniz gerekmez. Başka bir deyişle, yalnızca filtreye `Mailbox` sahip bir arama izinleri filtresi hem posta kutularını hem de OneDrive hesaplarını içerebilir.

Contoso uyumluluk sınırları senaryosını desteklemek için oluşturulacak iki arama izni filtresinin örnekleri aşağıda verilmiştir. Bu örneklerin her ikisi de, posta kutusu ve site filtrelerinin aynı arama izinleri filtresine dahil olduğu ve virgülle ayrıldığı virgülle ayrılmış filtreler listesini içerir.
  
### <a name="fourth-coffee"></a>Dördüncü Kahve

```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```

### <a name="coho-winery"></a>Coho Şaraphanesi

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```

> [!NOTE]
> Önceki örneklerde yer alan parametrelerin `Filters` söz dizimi *bir filtre listesi* içerir. Filtreler listesi, posta kutusu filtresi ve virgülle ayrılmış bir site yolu filtresi içeren bir filtredir. Önceki örnekte virgülün ayrıldığına `Mailbox` ve `SiteContent` filtrelendiğini fark edeceksiniz: `-Filters "Mailbox_<MailboxPropertyName>  -eq '<Value> '", "SiteContent_Path -like '<SharePointURL>' -or SiteContent_Path -like '<OneDriveURL>'"`. Bir eBulma araması çalıştırılırken bu filtre işlendiğinde, filtreler listesinden iki arama izni filtresi oluşturulur: bir posta kutusu filtresi ve bir SharePoint/OneDrive filtresi. Filtreler listesi kullanmanın alternatifi, her bir kuruluş için iki ayrı arama izni filtresi oluşturmaktır: posta kutusu özniteliği için bir arama izinleri filtresi ve SharePoint ve OneDrive site öznitelikleri için bir filtre. Her iki durumda da sonuçlar aynı olacaktır. Filtreler listesi kullanmak veya ayrı arama izinleri filtreleri oluşturmak tercih konusudur.

### <a name="how-do-the-search-permissions-filters-work-in-this-scenario"></a>Arama izinleri filtreleri bu senaryoda nasıl çalışır?

Bu senaryoda, arama izni filtrelerinin her bir kuruluş için nasıl uygulandığı aşağıda anlatılır.

1. Filtre `Mailbox` ilk olarak eBulma yöneticilerinin arayabileceği içerik konumlarını tanımlamak için uygulanır. Bu durumda, Coho Winery eKeşif yöneticileri yalnızca *Departman* posta kutusu özelliği **FourthCoffee** değerine sahip kullanıcıların posta kutularında ve OneDrive hesaplarında arama yapabilir; Coho Winery eKeşif yöneticileri yalnızca *Departman* posta kutusu özelliği **CohoWinery** değerine sahip kullanıcıların posta kutularında ve OneDrive hesaplarında arama yapabilir. Filtre `Mailbox` , eBulma yöneticilerinin arayabileceği içerik konumlarını belirttiğinden bir içerik *konumu filtresidir*. Her iki filtrede de eBulma yöneticileri yalnızca belirli bir posta kutusu özellik değerine sahip içerik konumlarında arama yapabilir.

2. Aranabilecek içerik konumları tanımlandıktan sonra, filtrenin bir sonraki bölümü eBulma yöneticilerinin arayabileceği içeriği tanımlar. İlk `SiteContent` filtre Fourth Coffee eKeşif yöneticilerinin yalnızca içeren (veya ile başlayan) `https://contoso.sharepoint.com/sites/FourthCoffee`site yolu özelliğine sahip belgeleri aramasına olanak tanır; Coho Winery eKeşif yöneticileri yalnızca içeren (veya ile başlayan) `https://contoso.sharepoint.com/sites/CohoWinery`site yolu özelliğine sahip belgelerde arama yapabilir. Bu nedenle, aranabilecek içeriği tanımladıkları için iki `SiteContent` *filtre içerik filtreleridir* . Her iki filtrede de eBulma yöneticileri yalnızca belirli bir belge özelliği değerine sahip belgeleri arayabilir. Arama yapılabilir site özellikleri tüm belgelere damgalandığından, SharePoint ile ilgili tüm filtreler içerik filtreleridir. Daha fazla bilgi için bkz. [eBulma için izin filtrelemeyi yapılandırma](permissions-filtering-for-content-search.md#new-compliancesecurityfilter).

   > [!NOTE]
   > Bu makaledeki senaryo bunları kullanmasa da, eBulma yöneticilerinin arayabileceği içeriği belirtmek için posta kutusu içerik filtrelerini de kullanabilirsiniz. Posta kutusu içerik filtrelerinin söz dizimi şeklindedir `"MailboxContent_<property> -<comparison operator> '<value>'"`. Tarih aralıklarına, alıcılara ve etki alanlarına veya aranabilir herhangi bir e-posta özelliğine göre içerik filtreleri oluşturabilirsiniz. Örneğin, bu filtre eBulma yöneticilerinin yalnızca contoso.com etki alanındaki kullanıcılar tarafından gönderilen veya alınan posta öğelerini aramasına izin verir: `"MailboxContent_Participants -like 'contoso.com'"`. Posta kutusu içerik filtreleri hakkında daha fazla bilgi için bkz. [Arama izinleri filtrelemeyi yapılandırma](permissions-filtering-for-content-search.md#new-compliancesecurityfilter).

3. Arama izinleri filtresi **, AND** Boole işleci tarafından arama sorgusuna katılır. Başka bir deyişle, kurumlardan birinde bir eBulma yöneticisi bir eBulma araması çalıştırdığında, arama tarafından döndürülen öğeler arama sorgusuyla ve arama izinleri filtresinde tanımlanan koşullarla eşleşmelidir.

## <a name="step-4-create-an-ediscovery-case-for-intra-agency-investigations"></a>4. Adım: Kurum içi araştırmalarda eBulma olayı oluşturma

Son adım, uyumluluk portalında bir eBulma (Standart) servis talebi veya eBulma (Premium) olayı oluşturmak ve ardından 2. Adımda oluşturduğunuz rol grubunu olayın bir üyesi olarak eklemektir. Bu, uyumluluk sınırlarını kullanmanın iki önemli özelliğine neden olur:
  
- Yalnızca servis talebine eklenen rol grubunun üyeleri, servis talebini uyumluluk portalında görebilir ve erişebilir. Örneğin, bir olayın tek üyesi Dördüncü Kahve Araştırmacıları rol grubuysa, Fourth Coffee eBulma Yöneticileri rol grubunun üyeleri (veya başka bir rol grubunun üyeleri) olayı göremez veya bu gruba erişemez.

- Bir servis talebine atanan rol grubunun bir üyesi servis talebiyle ilişkili bir arama çalıştırdığında, yalnızca kendi ajansındaki içerik konumlarında arama yapabilir (bu, 3. Adımda oluşturduğunuz arama izinleri filtresi tarafından tanımlanır).)

Bir servis talebi oluşturmak ve üyeleri atamak için:

1. Uyumluluk portalında **eBulma (Standart)** veya **eBulma (Premium)** sayfasına gidin ve bir servis talebi oluşturun.

2. Servis talebi listesinde, oluşturduğunuz servis talebinin adına tıklayın.

3. Role groups'ı servis talebine üye olarak ekleyin. Yönergeler için aşağıdaki makalelerden birine bakın:

   - [eBulma (Standart) servis talebine üye ekleme](get-started-core-ediscovery.md#step-4-optional-add-members-to-a-ediscovery-standard-case)

   - [eBulma (Premium) olayına üye ekleme](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

> [!NOTE]
> Bir servis talebine rol grubu eklerken, yalnızca üyesi olduğunuz rol gruplarını ekleyebilirsiniz.

## <a name="searching-and-exporting-content-in-multi-geo-environments"></a>Multi-Geo ortamlarında içerik arama ve dışarı aktarma

Arama izinleri filtreleri, dışarı aktarma için içeriğin nereye yönlendirilebileceğini ve [SharePoint Multi-Geo bir ortamda](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md) içerik konumlarında arama yaparken hangi veri merkezinin aranabileceğini denetlemenize de olanak tanır.
  
- **Arama sonuçlarını dışarı aktarma:** Arama sonuçlarını Exchange posta kutularından, SharePoint sitelerinden ve OneDrive hesaplarından belirli bir veri merkezinden dışarı aktarabilirsiniz. Bu, arama sonuçlarının dışarı aktarılacağı veri merkezi konumunu belirtebileceğiniz anlamına gelir.

    Dışarı aktarmanın hangi veri merkezinden yönlendirileceğini oluşturmak veya değiştirmek için **New-ComplianceSecurityFilter** veya **Set-ComplianceSecurityFilter** cmdlet'leri için *Region* parametresini kullanın.
  
    |**Parametre değeri**|**Veri merkezi konumu**|
    |:-----|:-----|
    |NAM  <br/> |Kuzey Amerika (veri merkezleri ABD'dedir)  <br/> |
    |EUR  <br/> |Avrupa  <br/> |
    |APC  <br/> |Asya Pasifik  <br/> |
    |-BİLİRSİNİZ <br/> |Kanada|
    |||

- **Yönlendirme içeriği aramaları:** SharePoint sitelerinin ve OneDrive hesaplarının içerik aramalarını bir uydu veri merkezine yönlendirebilirsiniz. Bu, aramaların çalıştırılacağı veri merkezi konumunu belirtebileceğiniz anlamına gelir.

    SharePoint sitelerinde ve OneDrive hesaplarında arama yaparken aramaların çalıştırılacağı veri merkezi konumunu denetlemek için *Region* parametresi için aşağıdaki değerlerden birini kullanın.
  
    |**Parametre değeri**|**SharePoint için veri merkezi yönlendirme konumları**|
    |:-----|:-----|
    |NAM  <br/> |US  <br/> |
    |EUR  <br/> |Avrupa  <br/> |
    |APC  <br/> |Asya Pasifik  <br/> |
    |-BİLİRSİNİZ  <br/> |US  <br/> |
    |AUS  <br/> |Asya Pasifik  <br/> |
    |KOR  <br/> |Kuruluşun varsayılan veri merkezi  <br/> |
    |GBR  <br/> |Avrupa  <br/> |
    |JPN  <br/> |Asya Pasifik  <br/> |
    |SANAYİ  <br/> |Asya Pasifik  <br/> |
    |LAM  <br/> |US  <br/> |
    |NOR  <br/> |Avrupa |
    |SUTYEN  <br/> |Kuzey Amerika veri merkezleri |
    |||

   Arama izinleri filtresi için *Region* parametresini belirtmezseniz, kuruluşun birincil SharePoint bölgesi aranacaktır. Arama sonuçları en yakın veri merkezine aktarılır.

   Kavramı basitleştirmek için *Region* parametresi, SharePoint ve OneDrive'da içerik aramak için kullanılan veri merkezini denetler. Exchange içerik aramaları veri merkezlerinin coğrafi konumuna bağlı olmadığından Bu, Exchange'de içerik arama için geçerli değildir. Ayrıca, aynı *Region* parametresi değeri dışarı aktaran veri merkezinin yönlendirildiğini de dikte edebilir. Bu genellikle verilerin coğrafi panolar arasında hareketini denetlemek için gereklidir.

> [!NOTE]
> eBulma (Premium) kullanıyorsanız *, Region* parametresi verilerin dışarı aktardığı bölgeyi denetlemez. Veriler kuruluşun merkezi konumundan dışarı aktarılır. Ayrıca, SharePoint ve OneDrive'da içerik aramak veri merkezlerinin coğrafi konumuna bağlı değildir. Tüm veri merkezleri aranıyor. eBulma (Premium) hakkında daha fazla bilgi için bkz. [Microsoft 365'te eKeşif (Premium) çözümüne genel bakış](overview-ediscovery-20.md).

Uyumluluk sınırları için arama izni filtreleri oluştururken *Region* parametresini kullanma örnekleri aşağıda verilmiştir. Bu, Fourth Coffee yan kuruluşunun Kuzey Amerika'da yer aldığını ve Coho Winery'nin Avrupa'da olduğunu varsayar.
  
```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'" -Region NAM
```

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'" -Region EUR
```

Çok coğrafi ortamlarda içerik ararken ve dışarı aktarırken aşağıdakileri göz önünde bulundurun.
  
- *Region* parametresi Exchange posta kutularının aramalarını denetlemez. Posta kutularında arama yaptığınızda tüm veri merkezleri aranacaktır. Exchange posta kutularının aranma kapsamını sınırlamak için, arama izinleri filtresi oluştururken veya değiştirirken *Filters* parametresini kullanın.

- Bir eBulma Yöneticisinin birden çok SharePoint bölgesinde arama gerçekleştirmesi gerekiyorsa, SharePoint sitelerinin veya OneDrive hesaplarının bulunduğu bölgeyi belirtmek üzere arama izinleri filtresinde kullanmak üzere bu eBulma yöneticisi için farklı bir kullanıcı hesabı oluşturmanız gerekir. Bunu ayarlama hakkında daha fazla bilgi için İçerik [Arama'nın](content-search-reference.md#searching-for-content-in-a-sharepoint-multi-geo-environment) "SharePoint Multi-Geo ortamında içerik arama" bölümüne bakın.

- SharePoint ve OneDrive'da içerik ararken *, Region* parametresi aramaları eBulma yöneticisinin eBulma araştırmalarını gerçekleştireceği birincil veya uydu konumuna yönlendirir. Bir eBulma yöneticisi, arama izinleri filtresinde belirtilen bölgenin dışındaki SharePoint ve OneDrive sitelerinde arama yaparsanız, hiçbir arama sonucu döndürülür.

- Arama sonuçlarını eBulma'dan (Standart) dışarı aktarırken, tüm içerik konumlarından (Exchange, Skype Kurumsal, SharePoint, OneDrive ve İçerik Arama aracını kullanarak arama yapabileceğiniz diğer hizmetler dahil) içerik *, Bölge* parametresi tarafından belirtilen veri merkezinde Azure Depolama konumuna yüklenir. Bu, kuruluşların içeriğin denetimli kenarlıklar arasında dışarı aktarılmasına izin vermeyerek uyumluluk içinde kalmasına yardımcı olur. Arama izinleri filtresinde hiçbir bölge belirtilmezse, içerik kuruluşun birincil veri merkezine yüklenir.

  eBulma'dan (Premium) içerik dışarı aktarırken *Region* parametresini kullanarak içeriğin karşıya yüklendiği yeri denetleyemezsiniz. İçerik, kuruluşunuzun merkezi konumundaki bir veri merkezinde azure depolama konumuna yüklenir. Merkezi konumunuza göre coğrafi konumların listesi için bkz. [Microsoft 365 Multi-Geo eKeşif yapılandırması](../enterprise/multi-geo-ediscovery-configuration.md).

- Aşağıdaki komutu çalıştırarak bölgeyi eklemek veya değiştirmek için var olan bir arama izinleri filtresini düzenleyebilirsiniz:

    ```powershell
    Set-ComplianceSecurityFilter -FilterName <Filter name>  -Region <Region>
    ```

## <a name="using-compliance-boundaries-for-sharepoint-hub-sites"></a>SharePoint hub siteleri için uyumluluk sınırlarını kullanma

[SharePoint hub siteleri](/sharepoint/dev/features/hub-site/hub-site-overview) genellikle eKeşif uyumluluk sınırlarının izlediği coğrafi veya ajans sınırlarıyla aynı hizalanır. Bu, uyumluluk sınırı oluşturmak için hub sitesinin site kimliği özelliğini kullanabileceğiniz anlamına gelir. Bunu yapmak için SharePoint Online PowerShell'de [Get-SPOHubSite](/powershell/module/sharepoint-online/get-spohubsite#examples) cmdlet'ini kullanarak hub sitesinin SiteId değerini alın ve ardından bölüm kimliği özelliği için bu değeri kullanarak arama izinleri filtresi oluşturun.

SharePoint hub sitesi için arama izinleri filtresi oluşturmak için aşağıdaki söz dizimini kullanın:

```powershell
New-ComplianceSecurityFilter -FilterName <Filter Name> -Users <User or Group> -Filters "Site_Departmentid -eq '{SiteId of hub site}'"
```

Coho Winery ajansı için merkez sitesi için arama izinleri filtresi oluşturma örneği aşağıda verilmiştir:

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Hub Site Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Site_Departmentid -eq '44252d09-62c4-4913-9eb0-a2a8b8d7f863'"
```

## <a name="compliance-boundary-limitations"></a>Uyumluluk sınırı sınırlamaları

Uyumluluk sınırlarını kullanan eBulma olaylarını ve araştırmalarını yönetirken aşağıdaki sınırlamaları göz önünde bulundurun.
  
- Arama oluştururken ve çalıştırırken, kuruluşunuzun dışındaki içerik konumlarını seçebilirsiniz. Ancak, arama izinleri filtresi nedeniyle bu konumlardaki içerik arama sonuçlarına dahil değildir.

- Uyumluluk sınırları eBulma durumlarında tutmalar için geçerli değildir. Başka bir deyişle, bir ajanstaki eBulma yöneticisi bir kullanıcıyı farklı bir ajansa beklemeye alabilir. Ancak, eBulma yöneticisi beklemeye alınan kullanıcının içerik konumlarını ararsa uyumluluk sınırı zorlanır. Bu, eBulma yöneticisinin kullanıcıyı beklemeye alabilse bile kullanıcının içerik konumlarında arama yapamayacağı anlamına gelir.

- Size bir arama izinleri filtresi (posta kutusu veya site filtresi) atanırsa ve kuruluşunuzdaki tüm SharePoint sitelerini içeren bir arama için dizine alınmamış öğeleri dışarı aktarmaya çalışırsanız, şu hata iletisini alırsınız: `Unable to execute the task. Reason: The scope options UnindexedItemsOnly or BothIndexedandUnindexedItems are not allowed when the executing user has a compliance security filter applied`. Size bir arama izinleri filtresi atanmışsa ve dizine alınmamış öğeleri SharePoint'ten dışarı aktarmak istiyorsanız, aramayı yeniden çalıştırmanız ve arama için belirli SharePoint sitelerini eklemeniz gerekir. Aksi takdirde, yalnızca tüm SharePoint sitelerini içeren bir aramadan dizine alınan öğeleri dışarı aktarabilirsiniz. Arama sonuçlarını dışarı aktardığınız seçenekler hakkında daha fazla bilgi için bkz. [İçerik arama sonuçlarını dışarı aktarma](export-search-results.md#step-1-prepare-search-results-for-export).

- Arama izinleri filtreleri Exchange ortak klasörlerine uygulanmaz.

## <a name="more-information"></a>Daha fazla bilgi

- Posta kutusunun lisansı kaldırılırsa veya geçici olarak silinirse, kullanıcı artık uyumluluk sınırı içinde dikkate alınmaz. Silinen posta kutusuna ayrı tutma işlemi yapıldıysa, posta kutusunda korunan içerik yine de uyumluluk sınırına veya arama izinleri filtresine tabidir.

- Bir kullanıcı için uyumluluk sınırları ve arama izinleri filtreleri uygulanıyorsa, onedrive hesabını değil kullanıcının posta kutusunu silmemenizi öneririz. Başka bir deyişle, kullanıcının posta kutusunu silerseniz, OneDrive için arama izni filtresini zorlamak için mailbox_RecipientFilter kullanıldığından kullanıcının OneDrive hesabını da kaldırmanız gerekir.

- Uyumluluk sınırları ve arama izinleri filtreleri Exchange, OneDrive ve SharePoint'teki içeriğe damgalanan özniteliklere ve bu damgalanmış içeriğin sonraki dizinlenmesine bağlıdır.

- İçerik tabanlı uyumluluk sınırı için dışlama filtreleri (arama izinleri filtresinde kullanma `-not()` gibi) kullanmanızı önermeyiz. Son güncelleştirilen özniteliklere sahip içerik dizine eklenmezse, dışlama filtresinin kullanılması beklenmeyen sonuçlara neden olabilir.

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

**Kim arama izinleri filtreleri oluşturabilir ve yönetebilir (New-ComplianceSecurityFilter ve Set-ComplianceSecurityFilter cmdlet'lerini kullanarak)?**
  
Arama izinleri filtrelerini oluşturmak, görüntülemek ve değiştirmek için uyumluluk portalında Kuruluş Yönetimi rol grubunun üyesi olmanız gerekir.
  
**Bir eBulma yöneticisi birden çok ajansa yayılan birden çok rol grubuna atanmışsa, bir ajanstaki veya diğerindeki içeriği nasıl arar?**
  
eBulma yöneticisi, arama sorgusuna, aramayı belirli bir ajansla kısıtlayan parametreler ekleyebilir. Örneğin, bir kuruluş ajansları ayırt etmek için **CustomAttribute10** özelliğini belirttiyse, belirli bir kuruluştaki posta kutularını ve OneDrive hesaplarını aramak için arama sorgusuna aşağıdakileri ekleyebilir:  `CustomAttribute10:<value>`.
  
**Arama izinleri filtresinde uyumluluk özniteliği olarak kullanılan özniteliğin değeri değiştirilirse ne olur?**
  
Filtrede kullanılan özniteliğin değeri değiştirilirse, bir arama izinleri filtresinin uyumluluk sınırını zorlaması üç güne kadar sürer. Örneğin Contoso senaryosunda Fourth Coffee ajansındaki bir kullanıcının Coho Winery ajansına aktarıldığını düşünelim. Sonuç olarak, kullanıcı nesnesinde **Department** özniteliğinin değeri *FourthCoffee* olan *CohoWinery* olarak değiştirilir. Bu durumda, Fourth Coffee eKescovery ve yatırımcılar, özniteliği değiştirildikten sonra üç gün boyunca bu kullanıcının arama sonuçlarını alır. Benzer şekilde, Coho Winery eKeşif yöneticilerinin ve araştırmacılarının kullanıcı için arama sonuçları alması üç güne kadar sürer.
  
**Bir eBulma yöneticisi iki ayrı uyumluluk sınırındaki içeriği görebilir mi?**
  
Evet, bu, eKeşif yöneticisini her iki ajans için görünürlüğü olan rol gruplarına ekleyerek Exchange posta kutuları aranırken yapılabilir. Ancak, SharePoint sitelerinde ve OneDrive hesaplarında arama yaparken, bir eBulma yöneticisi farklı uyumluluk sınırları içindeki içeriği yalnızca kurumlar aynı bölgede veya coğrafi konumda olduğunda arayabilir. **Not:** SharePoint ve OneDrive'da içerik aramak coğrafi konuma bağlı olmadığından, siteler için bu sınırlama eBulma (Premium) içinde geçerli değildir.
  
**Arama izinleri filtreleri eBulma servis talebi saklamaları, Microsoft 365 bekletme ilkeleri veya DLP için çalışıyor mu?**
  
Şu anda yok.
  
**İçeriğin dışarı aktarıldığı yeri denetlemek için bir bölge belirtirsem ancak bu bölgede bir SharePoint kuruluşum yoksa SharePoint'te arama yapabilir miyim?**
  
Arama izinleri filtresinde belirtilen bölge kuruluşunuzda yoksa, varsayılan bölge aranacaktır.
  
**Bir kuruluşta oluşturulabilecek en fazla arama izni filtresi sayısı nedir?**
  
Bir kuruluşta oluşturulabilecek arama izni filtrelerinin sayısıyla ilgili bir sınır yoktur. Ancak, arama sorgusu en fazla 100 koşula sahip olabilir. Bu durumda, bir koşul Boole işleci ( **AND**, **OR** ve **NEAR** gibi) tarafından sorguya bağlı bir şey olarak tanımlanır. Koşul sayısı sınırı, arama sorgusunun kendisini ve aramayı çalıştıran kullanıcıya uygulanan tüm arama izinleri filtrelerini içerir. Bu nedenle, ne kadar çok arama izni filtreniz varsa (özellikle bu filtreler aynı kullanıcı veya kullanıcı grubuna uygulanırsa), arama için en fazla koşul sayısını aşma olasılığı o kadar yüksek olur.

Bu sınırın nasıl çalıştığını anlamak için, arama çalıştırıldığında arama sorgusuna bir arama izinleri filtresi eklendiğini anlamanız gerekir. **VE** Boole işleci tarafından arama sorgusuna bir arama izinleri filtresi eklenir. Arama sorgusu ve tek bir arama izinleri filtresi için sorgu mantığı şöyle görünür:

```text
<SearchQuery> AND <PermissionsFilter>
```

**OR** Boole işleci tarafından birden çok arama izni filtresi birleştirilir ve ardından bu koşullar **VE** işleci tarafından arama sorgusuna bağlanır.

Arama sorgusu ve birden çok arama izni filtresi için sorgu mantığı şöyle görünür:

```text
<SearchQuery> AND (<PermissionsFilter1> OR <PermissionsFilter2> OR <PermissionsFilter3>...)
```

Arama sorgusunun kendisi Boole işleçleri tarafından bağlanan birden çok koşuldan oluşabilir. Arama sorgusundaki her koşul da 100 koşul sınırına göre sayılır.

Ayrıca, sorguya eklenen arama izinleri filtrelerinin sayısı aramayı çalıştıran kullanıcıya bağlıdır. Belirli bir kullanıcı bir arama çalıştırdığında, kullanıcıya uygulanan arama izinleri filtreleri (filtredeki *Users* parametresi tarafından tanımlanır) sorguya eklenir. Kuruluşunuzda yüzlerce arama izni filtresi olabilir, ancak aynı kullanıcılara 100'den fazla filtre uygulanırsa, bu kullanıcılar arama çalıştırdığında 100 koşul sınırının aşılması olasıdır.

Koşul sınırıyla ilgili akılda tutulması gereken bir şey daha var. Arama sorgusuna veya arama izinleri filtrelerine dahil edilen belirli SharePoint sitelerinin sayısı da bu sınıra göre sayılır. 

Kuruluşunuzun koşullar sınırına ulaşmasını önlemek için, iş gereksinimlerinizi karşılamak için kuruluşunuzdaki arama izni filtrelerinin sayısını mümkün olduğunca az tutun.
