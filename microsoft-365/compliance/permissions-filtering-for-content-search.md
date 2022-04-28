---
title: eBulma için izin filtrelemeyi yapılandırma
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
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
ms.assetid: 1adffc35-38e5-4f7d-8495-8e0e8721f377
description: eBulma yöneticilerinin kuruluşunuzdaki posta kutularının ve sitelerin yalnızca bir alt kümesini aramasına izin vermek için arama izinleri filtrelemesini kullanın.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: ba8cfaaec45ceefff89b17b561a5e80bebbdade6
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098812"
---
# <a name="configure-permissions-filtering-for-ediscovery"></a>eBulma için izin filtrelemeyi yapılandırma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

EBulma yöneticisinin kuruluşunuzdaki posta kutularının ve sitelerin yalnızca bir alt kümesini aramasına izin vermek için arama izinleri filtrelemesini kullanabilirsiniz. Ayrıca, aynı eBulma yöneticisinin yalnızca belirli bir arama ölçütünü karşılayan posta kutusu veya site içeriği için arama yapmasına izin vermek için izin filtrelemeyi de kullanabilirsiniz. Örneğin, eBulma yöneticisinin yalnızca belirli bir konum veya departmandaki kullanıcıların posta kutularını aramasına izin vekleyebilirsiniz. Bunu, belirli bir kullanıcının veya kullanıcı grubunun hangi posta kutularını arayabileceğini sınırlamak için desteklenen bir alıcı filtresi kullanan bir filtre oluşturarak yaparsınız. Ayrıca, kullanıcının hangi posta kutusu içeriğini arayabileceğini belirten bir filtre de oluşturabilirsiniz. Bu işlem, aranabilir bir ileti özelliği kullanan bir filtre oluşturularak yapılır. Benzer şekilde, bir eBulma yöneticisinin kuruluşunuzdaki yalnızca belirli SharePoint siteleri aramasına izin vekleyebilirsiniz. Bunu, aranabilecek siteyi sınırlayan bir filtre oluşturarak yaparsınız. Ayrıca, hangi site içeriğinin aranabileceğini belirten bir filtre de oluşturabilirsiniz. Bu işlem, aranabilir bir site özelliği kullanan bir filtre oluşturularak yapılır.

Microsoft Purview uyumluluk portalında İçerik arama, Microsoft Purview eKeşif (Standart) ve Microsoft Purview eKeşif (Premium) kullanarak içerik aradığınızda arama izinleri filtreleri uygulanır. Belirli bir kullanıcıya arama izinleri filtresi uygulandığında, bu kullanıcı aramayla ilgili aşağıdaki eylemleri gerçekleştirebilir:

- İçerik için arama yapma

- Arama sonuçlarını önizleme

- Arama sonuçlarını dışarı aktarma

- Arama tarafından döndürülen öğeleri temizleme

Ayrıca, belirli eBulma yöneticilerinin arayabileceği kullanıcı içerik konumlarını (posta kutuları, SharePoint siteler ve OneDrive hesapları gibi) denetleyan bir kuruluş içinde mantıksal *sınırlar (uyumluluk sınırları* olarak adlandırılır) oluşturmak için arama izinleri filtrelemesini de kullanabilirsiniz. Daha fazla bilgi için bkz. [eBulma araştırmaları için uyumluluk sınırlarını ayarlama](set-up-compliance-boundaries.md).
  
Güvenlik & Uyumluluğu PowerShell'deki aşağıdaki dört cmdlet, arama izinleri filtrelerini yapılandırmanıza ve yönetmenize olanak sağlar:
  
[New-ComplianceSecurityFilter](#new-compliancesecurityfilter)

[Get-ComplianceSecurityFilter](#get-compliancesecurityfilter)

[Set-ComplianceSecurityFilter](#set-compliancesecurityfilter)

[Remove-ComplianceSecurityFilter](#remove-compliancesecurityfilter)

## <a name="requirements-to-configure-permissions-filtering"></a>İzin filtrelemeyi yapılandırma gereksinimleri

- Uyumluluk güvenlik filtresi cmdlet'lerini çalıştırmak için, uyumluluk portalında Kuruluş Yönetimi rol grubunun üyesi olmanız gerekir. Daha fazla bilgi için bkz [. Güvenlik & Uyumluluk Merkezi'ndeki İzinler](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

- Uyumluluk güvenlik filtresi cmdlet'lerini kullanmak için hem Exchange Online hem de Güvenlik & Uyumluluk Merkezi PowerShell'e bağlanmanız gerekir. Bu cmdlet'ler posta kutusu özelliklerine erişim gerektirdiği için bu gereklidir; bu nedenle Exchange Online PowerShell'e bağlanmanız gerekir. Sonraki bölümdeki adımlara bakın.

- Arama izinleri filtreleri hakkında ek [bilgi için Daha fazla bilgi](#more-information) bölümüne bakın.

- Arama izinleri filtreleme etkin olmayan posta kutuları için geçerlidir. Bu, etkin olmayan posta kutusunda kimlerin arama yapabileceklerini sınırlamak için posta kutusu ve posta kutusu içeriği filtrelemesini kullanabileceğiniz anlamına gelir. İzin filtreleme ve etkin olmayan posta kutuları hakkında ek bilgi için [Daha fazla bilgi](#more-information) bölümüne bakın.

- Arama izinleri filtrelemesi, Exchange ortak klasörlerde kimlerin arama yapabileceklerini sınırlamak için kullanılamaz.

- Bir kuruluşta oluşturulabilecek arama izni filtrelerinin sayısıyla ilgili bir sınır yoktur. Ancak, arama sorgusu en fazla 100 koşula sahip olabilir. Bu durumda, bir koşul Boole işleci ( **AND**, **OR** ve **NEAR** gibi) tarafından sorguya bağlı bir şey olarak tanımlanır. Koşul sayısı sınırı, arama sorgusunun kendisini ve aramayı çalıştıran kullanıcıya uygulanan tüm arama izinleri filtrelerini içerir. Bu nedenle, ne kadar çok arama izni filtreniz varsa (özellikle bu filtreler aynı kullanıcı veya kullanıcı grubuna uygulanırsa), arama için en fazla koşul sayısını aşma olasılığı o kadar yüksek olur. Kuruluşunuzun koşullar sınırına ulaşmasını önlemek için, iş gereksinimlerinizi karşılamak için kuruluşunuzdaki arama izni filtrelerinin sayısını mümkün olduğunca az tutun. Daha fazla bilgi için bkz. [eBulma araştırmaları için uyumluluk sınırlarını ayarlama](set-up-compliance-boundaries.md#frequently-asked-questions).

## <a name="connect-to-exchange-online-and-security--compliance-center-powershell-in-a-single-session"></a>Exchange Online ve Güvenlik & Uyumluluk Merkezi PowerShell'e tek bir oturumda Bağlan

Bu bölümdeki betiği başarıyla çalıştırabilmeniz için önce Exchange Online PowerShell V2 modülünü indirip yüklemeniz gerekir. Bilgi için bkz. [Exchange Online PowerShell V2 modülü hakkında](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

1. .ps1dosya adı soneki kullanarak aşağıdaki metni bir **Windows PowerShell** betik dosyasına kaydedin. Örneğin, **ConnectEXO-SCC.ps1** adlı bir dosyaya kaydedebilirsiniz.

    ```powershell
    Import-Module ExchangeOnlineManagement
    $UserCredential = Get-Credential
    Connect-ExchangeOnline -Credential $UserCredential -ShowBanner:$false
    Connect-IPPSSession -Credential $UserCredential
    $Host.UI.RawUI.WindowTitle = $UserCredential.UserName + " (Exchange Online + Compliance Center)"
    ```

2. Yerel bilgisayarınızda Windows PowerShell açın, önceki adımda oluşturduğunuz betiğin bulunduğu klasöre gidin ve ardından betiği çalıştırın; örneğin:

    ```powershell
    .\ConnectEXO-SCC.ps1
    ```

Bunun işe yarayip yaramadığını nasıl anlarsınız? Betiği çalıştırdıktan sonra, Exchange Online ve Güvenlik & Uyumluluğu PowerShell cmdlet'leri yerel Windows PowerShell oturumunuza aktarılır. Herhangi bir hata almazsanız başarıyla bağlandınız. Hızlı test, Exchange Online ve Güvenlik & Uyumluluk Merkezi PowerShell cmdlet'lerini çalıştırmaktır. Örneğin, **Get-Mailbox** ve **Get-ComplianceSearch** komutunu çalıştırabilirsiniz.

PowerShell bağlantı hatalarını gidermek için bkz:

- [PowerShell'i Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell#how-do-you-know-this-worked)

- [Güvenlik & Uyumluluk Merkezi PowerShell'e Bağlan](/powershell/exchange/connect-to-scc-powershell#how-do-you-know-this-worked)

## <a name="new-compliancesecurityfilter"></a>New-ComplianceSecurityFilter

**New-ComplianceSecurityFilter**, arama izinleri filtresi oluşturmak için kullanılır. Bu cmdlet'in temel söz dizimi aşağıdadır:

```powershell
New-ComplianceSecurityFilter -FilterName <name of filter> -Users <user or role group> -Filters <filter>
```

Aşağıdaki bölümlerde bu cmdlet'in parametreleri açıklanmaktadır. Arama izinleri filtresi oluşturmak için tüm parametreler gereklidir.

### <a name="filtername"></a>*Filtername*

_FilterName_ parametresi, izin filtresinin adını belirtir. Bu ad **Get-ComplianceSecurityFilter, Set-ComplianceSecurityFilter** ve **Remove-ComplianceSecurityFilter** cmdlet'leri kullanılırken bir filtreyi tanımlamak için kullanılır.

### <a name="filters"></a>*Filtre*

_Filters_ parametresi, uyumluluk güvenlik filtresi için arama ölçütlerini belirtir. Üç farklı filtre türü oluşturabilirsiniz:  

- **Posta kutusu veya OneDrive filtreleme:** Bu filtre türü, atanan kullanıcıların (_Kullanıcılar_ parametresi tarafından belirtilen) arayabileceği posta kutularını ve OneDrive hesaplarını belirtir. Bu tür bir filtre, kullanıcının arayabileceği içerik konumlarını tanımladığından içerik *konumu* filtresi olarak adlandırılır. Bu filtre türünün söz dizimi **,** _MailboxPropertyName_ Mailbox_, burada _MailboxPropertyName_, aranabilecek posta kutularının ve OneDrive hesaplarının kapsamını oluşturmak için kullanılan bir posta kutusu özelliğini belirtir. Örneğin, posta kutusu filtresi`"Mailbox_CustomAttribute10 -eq 'OttawaUsers'"`, kullanıcının bu filtreyi atadığı kullanıcının yalnızca CustomAttribute10 özelliğinde "OttawaUsers" değerine sahip posta kutularını ve OneDrive hesaplarını aramasına olanak tanır.

  Posta kutusunda veya OneDrive filtrede _MailboxPropertyName_ özelliği için desteklenen filtrelenebilir alıcı özellikleri kullanılabilir. Aşağıdaki tabloda, posta kutusu veya OneDrive filtresi oluşturmak için kullanılan yaygın olarak kullanılan dört alıcı özelliği listelemektedir. Tabloda ayrıca özelliğin filtrede kullanılmasına ilişkin bir örnek de yer alır.

  |Özellik adı  |Örnek  |
  |---------|---------|
  |Diğer ad    |`"Mailbox_Alias -like 'v-'"`         |
  |Şirket  |`"Mailbox_Company -eq 'Contoso'"`        |
  |Countryorregion |`"Mailbox_CountryOrRegion -eq 'United States'"`         |
  |Bölüm |`"Mailbox_Department -eq 'Finance'"`        |
  |||

- **Posta kutusu içeriği filtreleme:** Bu filtre türü, aranabilecek içeriğe uygulanır. Bu tür bir filtre, atanan kullanıcıların arayabileceği posta kutusu içeriğini veya aranabilir e-posta özelliklerini belirttiğinden *içerik filtresi* olarak adlandırılır. Bu tür bir filtrenin söz dizimi **MailboxContent_** _SearchablePropertyName, burada _SearchablePropertyName_ bir aramada belirtilebilen anahtar sözcük sorgu dili (KQL) özelliğini belirtir. Örneğin, posta kutusu içerik filtresi `"MailboxContent_Recipients  -like 'contoso.com'"` bu filtreyi ataan kullanıcının yalnızca contoso.com etki alanındaki alıcılara gönderilen iletileri aramasına olanak tanır. Aranabilir e-posta özelliklerinin listesi için bkz [. eBulma için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md#searchable-email-properties).

  > [!IMPORTANT]
  > Tek bir arama filtresi, posta kutusu filtresi ve posta kutusu içerik filtresi içeremez. Bunları tek bir filtrede birleştirmek için [bir filtre listesi](#using-a-filters-list-to-combine-filter-types) kullanmanız gerekir.  Ancak bir filtre aynı türde daha karmaşık bir sorgu içerebilir. Örneğin, `"Mailbox_CustomAttribute10 -eq 'FTE' -and Mailbox_MemberOfGroup -eq '$($DG.DistinguishedName)'"`

- **Site ve site içeriği filtreleme:** Atanan kullanıcıların hangi site veya site içeriğini arayabileceğini belirtmek için kullanabileceğiniz iki SharePoint ve OneDrive ilgili filtre vardır.

  - **Site_**_SearchableSiteProperty_
  
  - **SiteContent_**_SearchableSiteProperty_
  
   Bu iki filtre birbirinin yerine kullanılabilir. Örneğin, `"Site_Path -like 'https://contoso.sharepoint.com/sites/doctors'"` aynı  `"SiteContent_Path -like 'https://contoso.sharepoint.com/sites/doctors'"` sonuçları döndürür. Aranabilir site özelliklerinin listesi için bkz[. eBulma için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md#searchable-site-properties) Daha eksiksiz bir liste için bkz. [SharePoint'da gezinilen ve yönetilen özelliklere genel bakış](/SharePoint/technical-reference/crawled-and-managed-properties-overview). **Sorgulanabilir** sütununda **Evet** ile işaretlenmiş özellikler, site veya site içerik filtresi oluşturmak için kullanılabilir.  

  > [!IMPORTANT]
  > Site filtresinin desteklenen özelliklerden biriyle ayarlanması, filtredeki site özelliğinin bu sitedeki tüm belgelere yayılacağı anlamına gelmez. Başka bir deyişle, site filtresinin çalışması ve doğru içeriği yakalaması için bu sitedeki belgelerle ilişkili belirli özellik alanlarının doldurulmasından kullanıcının sorumlu olduğu anlamına gelir. Örneğin, kullanıcının "Site_RefineableString00 -eq 'abc' Site_RefineableString00" güvenlik filtresi uygulanmışsa ve kullanıcı "xyz" anahtar sözcüğünü kullanarak bir arama çalıştırırsa. Güvenlik filtresi sorguya eklenir ve çalıştırılan gerçek sorgu "xyz **AND RefineableString0:'abc'**" olur. Kullanıcının sitedeki belgelerin RefineableString00 alanında "abc" olarak değerlere sahip olduğundan emin olması gerekir. Aksi takdirde, arama sorgusu hiçbir sonuç döndürmez.

Arama izinleri filtreleri için *Filtreler* parametresini yapılandırırken aşağıdaki noktaları göz önünde bulundurun:

- *Site* filtresi bir konum filtresi gibi görünse de, posta kutularının aksine siteler için içerik konumu filtresi yoktur. SharePoint ve OneDrive tüm filtreleri içerik filtreleridir (bu nedenle *Site_* ve *SiteContent_* filtreleri de değiştirilebilir). Çünkü *Path* gibi siteyle ilgili özellikler doğrudan belgelere damgalanır. Bu neden? bu, SharePoint tasarımının bir sonucudur. SharePoint'da, Exchange posta kutuları gibi özellikleri olan bir "site nesnesi" yoktur. Bu nedenle, *Path* özelliği belgeye damgalanır ve belgenin bulunduğu sitenin URL'sini içerir. Bu nedenle *Site* filtresi içerik konumu filtresi olarak değil içerik filtresi olarak kabul edilir.

- Kullanıcıların belirli bir hizmetteki içerik konumlarında arama yapmasını (örneğin, kullanıcının herhangi bir Exchange posta kutusunda veya herhangi bir SharePoint sitesinde arama yapmasını engellemek) için bir arama izinleri filtresi oluşturmanız gerekir. Başka bir deyişle, kullanıcının kuruluştaki tüm SharePoint sitelerinde arama yapmasına olanak tanıyan bir arama izinleri filtresi oluşturmak, kullanıcının posta kutularını aramasını engellemez. Örneğin, SharePoint yöneticilerin yalnızca SharePoint sitelerde arama yapmasını sağlamak için, posta kutularını aramalarını engelleyen bir filtre oluşturmanız gerekir. Benzer şekilde, Exchange yöneticilerin yalnızca posta kutularını aramasına izin vermek için, sitelerde arama yapmasını engelleyen bir filtre oluşturmanız gerekir.

### <a name="users"></a>*Kullanıcılar*

_Users_ parametresi, aramalarına bu filtreyi uygulayan kullanıcıları belirtir. Kullanıcıları diğer adlarına veya birincil SMTP adreslerine göre tanımlayın. Virgülle ayrılmış birden çok değer belirtebilir veya **Tümü** değerini kullanarak filtreyi tüm kullanıcılara atayabilirsiniz.

Uyumluluk portalı rol grubunu belirtmek için  _Users_ parametresini de kullanabilirsiniz. Bu, özel bir rol grubu oluşturmanıza ve ardından bu rol grubuna bir arama izinleri filtresi atamanıza olanak tanır. Örneğin, çok uluslu bir şirketin ABD yan kuruluşu için eKeşif yöneticileri için özel bir rol grubunuz olduğunu varsayalım. Bu rol grubunu belirtmek için  _Users_ parametresini kullanabilirsiniz (rol grubunun Name özelliğini kullanarak) ve ardından  _Filter_ parametresini kullanarak yalnızca ABD'deki posta kutularının aranmasına izin vekleyebilirsiniz. Bu parametreyle dağıtım grupları belirtemezsiniz.|

### <a name="using-a-filters-list-to-combine-filter-types"></a>Filtre türlerini birleştirmek için filtre listesi kullanma

*Filtreler listesi*, posta kutusu filtresi ve virgülle ayrılmış site filtresi içeren bir filtredir. Bu virgül aynı zamanda **OR** işleci olarak da çalışır. Filtre listesi kullanmak, farklı filtre türlerini birleştirmek için desteklenen tek yöntemdir. Aşağıdaki örnekte, posta **kutusu** ve **site** filtrelerini virgülle ayırdığını fark edin:

```powershell
-Filters "Mailbox_CustomAttribute10 -eq 'OttawaUsers'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/doctors'"
```

Arama çalıştırılırken filtre listesi içeren bir filtre işlendiğinde, filtreler listesinden iki arama izni filtresi oluşturulur: Virgülle ayrılmış her filtre için bir filtre. Bu nedenle, önceki örnekte bir posta kutusu arama izinleri filtresi ve bir site arama izinleri filtresi oluşturulacaktı. Bu filtreler **OR** işleci tarafından bağlanır.

Filtreler listesi kullanmanın alternatifi, iki ayrı arama izni filtresi oluşturmaktır. Bu nedenle, önceki örnekte posta kutusu özniteliği için bir filtre ve site özniteliği için bir filtre oluşturacaksınız. Her iki durumda da sonuçlar aynıdır. Filtreler listesi kullanmak veya ayrı arama izinleri filtreleri oluşturmak tercih konusudur.

Filtre listesi kullanma hakkında aşağıdaki şeyleri aklınızda bulundurun:

- **Posta Kutusu** filtresi ve **MailboxContent** filtresi içeren bir filtre oluşturmak için filtreler listesi kullanmanız gerekir.

- Filtreler listesinin her bileşeni karmaşık bir filtre söz dizimi içerebilir. Örneğin, posta kutusu ve site filtreleri bir **-veya** işleciyle ayrılmış birden çok filtre içerebilir:

   ```powershell
   -Filters "Mailbox_Department -eq 'CohoWinery' -or Mailbox_CustomAttribute10 -eq 'CohoUsers'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery*'"
   ```

## <a name="examples-of-creating-search-permissions-filters"></a>Arama izinleri filtreleri oluşturma örnekleri

Burada, arama izinleri filtresi oluşturmak için **New-ComplianceSecurityFilter** cmdlet'ini kullanma örnekleri verilmiştir.

Bu örnek, "US Discovery Managers" rol grubunun üyelerinin yalnızca Birleşik Devletler posta kutularını ve OneDrive hesaplarını aramasına olanak tanır.
  
```powershell
New-ComplianceSecurityFilter -FilterName USDiscoveryManagers  -Users "US Discovery Managers" -Filters "Mailbox_CountryOrRegion  -eq 'United States'"
```
  
Bu örnek, kullanıcının annb@contoso.com yalnızca Kanada'daki posta kutuları ve OneDrive hesapları için arama eylemleri gerçekleştirmesine olanak tanır. Bu filtre, ISO 3166-1'den Kanada için üç basamaklı sayısal ülke kodunu içerir.

```powershell
New-ComplianceSecurityFilter -FilterName CountryFilter  -Users annb@contoso.com -Filters "Mailbox_CountryCode  -eq '124'"
```

Bu örnek, kullanıcıların yalnızca CustomAttribute1 posta kutusu özelliği için 'Marketing' değerine sahip posta kutularını ve OneDrive hesaplarını aramasına olanak tanır.

```powershell
New-ComplianceSecurityFilter -FilterName MarketingFilter  -Users donh,suzanf -Filters "Mailbox_CustomAttribute1  -eq 'Marketing'"
```

Bu örnek, "Fourth Coffee eBulma Yöneticileri" rol grubunun üyelerinin yalnızca Departman posta kutusu özelliği için 'FourthCoffee' değerine sahip posta kutularını ve OneDrive hesaplarını aramasına olanak tanır. Filtre ayrıca rol grubu üyelerinin Fourth Coffee SharePoint sitesindeki belgeleri aramasına da olanak tanır.

```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```

> [!NOTE]
> Önceki örnekte, rol grubu üyelerinin OneDrive hesaplarındaki belgeleri arayabilmesi için ek bir site içerik filtresinin (`SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'`) eklenmesi gerekir. Bu filtre dahil değilse, filtre yalnızca rol grubu üyelerinin içinde `https://contoso.sharepoint.com/sites/FourthCoffee`bulunan belgeleri aramasına izin verir.

Bu örnek, eBulma Yöneticisi rol grubu üyelerinin yalnızca Ottawa Kullanıcıları dağıtım grubu üyelerinin posta kutularını ve OneDrive hesaplarını aramasına olanak tanır. Exchange Online PowerShell'deki Get-DistributionGroup cmdlet'i, Ottawa Kullanıcıları grubunun üyelerini bulmak için kullanılır.
  
```powershell
$DG = Get-DistributionGroup "Ottawa Users"
```

```powershell
New-ComplianceSecurityFilter -FilterName DGFilter  -Users eDiscoveryManager -Filters "Mailbox_MemberOfGroup -eq '$($DG.DistinguishedName)'"
```

Bu örnek, herhangi bir kullanıcının Yönetim Ekibi dağıtım grubu üyelerinin posta kutularında ve OneDrive hesaplarında arama eylemleri gerçekleştirmesini engeller. Bu, kullanıcıların bu posta kutularından içerik silebileceği anlamına gelir. Exchange Online PowerShell'deki Get-DistributionGroup cmdlet'i, Yönetim Ekibi grubunun üyelerini bulmak için kullanılır.

```powershell
$DG = Get-DistributionGroup "Executive Team"
```

```powershell
New-ComplianceSecurityFilter -FilterName NoExecutivesPreview  -Users All -Filters "Mailbox_MemberOfGroup -ne '$($DG.DistinguishedName)'" 
```

Bu örnek, OneDrive eBulma Yöneticileri özel rol grubu üyelerinin yalnızca kuruluştaki OneDrive hesaplarındaki içeriği aramasına olanak tanır.

```powershell
New-ComplianceSecurityFilter -FilterName OneDriveOnly  -Users "OneDrive eDiscovery Managers" -Filters "SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```
  
Bu örnek, kullanıcıyı yalnızca 2015 takvim yılı boyunca gönderilen e-posta iletilerinde arama eylemleri gerçekleştirmeye kısıtlar.

```powershell
New-ComplianceSecurityFilter -FilterName EmailDateRestrictionFilter -Users donh@contoso.com -Filters "MailboxContent_Received -ge '01-01-2015' -and MailboxContent_Received -le '12-31-2015'"
```

Bu örnek, önceki örneğe benzer şekilde, kullanıcıyı yalnızca 2015 takvim yılında en son değiştirilen belgelerde arama eylemleri gerçekleştirmeye kısıtlar.

```powershell
New-ComplianceSecurityFilter -FilterName DocumentDateRestrictionFilter -Users donh@contoso.com -Filters "SiteContent_LastModifiedTime -ge '01-01-2015' -and SiteContent_LastModifiedTime -le '12-31-2015'" 
```

Bu örnek, "OneDrive Bulma Yöneticileri" rol grubunun üyelerinin kuruluştaki herhangi bir posta kutusunda arama eylemleri gerçekleştirmesini engeller.

```powershell
New-ComplianceSecurityFilter -FilterName NoEXO -Users "OneDrive Discovery Managers" -Filters "Mailbox_Alias -notlike '*'"
```

Bu örnek, kuruluştaki herkesin Janets veya Sarad tarafından gönderilen veya alınan e-posta iletilerinde arama eylemleri gerçekleştirmesini engeller.

```powershell
New-ComplianceSecurityFilter -FilterName NoSaraJanet -Users All -Filters "MailboxContent_Participants -notlike 'janets@contoso.onmicrosoft.com' -and MailboxContent_Participants -notlike 'sarad@contoso.onmicrosoft.com'"
```

Bu örnekte, posta kutusu ve site filtrelerini birleştirmek için filtreler listesi kullanılır. Bu örnekte, posta kutusu filtresi bir içerik konumu filtresi, site filtresi ise bir içerik filtresidir.

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery'"
```

## <a name="get-compliancesecurityfilter"></a>Get-ComplianceSecurityFilter

**Get-ComplianceSecurityFilter**, arama izinleri filtrelerinin listesini döndürmek için kullanılır. Belirli bir arama filtresine ilişkin bilgileri döndürmek için  _FilterName_ parametresini kullanın.
  
## <a name="set-compliancesecurityfilter"></a>Set-ComplianceSecurityFilter

**Set-ComplianceSecurityFilter**, mevcut arama izinleri filtresini değiştirmek için kullanılır. Aşağıdaki bölümlerde bu cmdlet'in parametreleri açıklanmaktadır. Gereken tek parametre  _FilterName'dir_.
  
### <a name="filtername"></a>*Filtername*

_FilterName_ parametresi, izin filtresinin adını belirtir.

### <a name="users"></a>*Kullanıcılar*

_Users_ parametresi, aramalarına bu filtreyi uygulayan kullanıcıları belirtir. Bu çok değerli bir özellik olduğundan, bu parametreye sahip bir kullanıcı veya kullanıcı grubu belirterek mevcut kullanıcı listesinin üzerine yazın. Seçili kullanıcıları ekleme ve kaldırma söz dizimi için aşağıdaki örneklere bakın.

Uyumluluk portalı rol grubunu belirtmek için  _Users_ parametresini de kullanabilirsiniz. Bu, özel bir rol grubu oluşturmanıza ve ardından bu rol grubuna bir arama izinleri filtresi atamanıza olanak tanır. Örneğin, çok uluslu bir şirketin ABD yan kuruluşu için eKeşif yöneticileri için özel bir rol grubunuz olduğunu varsayalım. Bu rol grubunu belirtmek için  _Users_ parametresini kullanabilirsiniz (rol grubunun Name özelliğini kullanarak) ve ardından  _Filter_ parametresini kullanarak yalnızca ABD'deki posta kutularının aranmasına izin vekleyebilirsiniz. Bu parametreyle dağıtım grupları belirtemezsiniz.

### <a name="filters"></a>*Filtre*

_Filters_ parametresi, uyumluluk güvenlik filtresi için arama ölçütlerini belirtir. Üç farklı filtre türü oluşturabilirsiniz:

- **Posta kutusu ve OneDrive filtreleme:** Bu filtre türü, atanan kullanıcıların (_Kullanıcılar_ parametresi tarafından belirtilen) arayabileceği posta kutularını ve OneDrive hesaplarını belirtir. Bu filtre türünün söz dizimi _MailboxPropertyName_ **Mailbox_**, burada _MailboxPropertyName_, aranabilecek posta kutularının kapsamını daraltmak için kullanılan bir posta kutusu özelliğini belirtir. Örneğin, posta kutusu filtresi  `"Mailbox_CustomAttribute10 -eq 'OttawaUsers'"` , kullanıcının bu filtreyi atadığı posta kutularının yalnızca CustomAttribute10 özelliğinde "OttawaUsers" değerine sahip posta kutularını aramasına izin verir.  _MailboxPropertyName_ özelliği için desteklenen filtrelenebilir alıcı özellikleri kullanılabilir. Desteklenen özelliklerin listesi için bkz. [-RecipientFilter parametresi için filtrelenebilir özellikler](/powershell/exchange/recipientfilter-properties).

- **Posta kutusu içeriği filtreleme:** Bu filtre türü, aranabilecek içeriğe uygulanır. Atanan kullanıcıların arayabileceği posta kutusu içeriğini belirtir. Bu filtre türünün söz dizimi **MailboxContent_**_SearchablePropertyName_ şeklindedir; burada _SearchablePropertyName_, aramada belirtilebilen bir Anahtar Sözcük Sorgu Dili (KQL) özelliğini belirtir. Örneğin, posta kutusu içerik filtresi `"MailboxContent_Recipients  -like 'contoso.com'"` bu filtreyi ataan kullanıcının yalnızca contoso.com etki alanındaki alıcılara gönderilen iletileri aramasına olanak tanır.  Aranabilir e-posta özelliklerinin listesi için bkz [. eBulma için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md).

- **Site ve site içeriği filtreleme:** Atanan kullanıcıların hangi site veya site içeriğini arayabileceğini belirtmek için kullanabileceğiniz iki SharePoint ve OneDrive İş siteyle ilgili filtre vardır:

  - **Site_** *SearchableSiteProperty* 
  - **SiteContent** _ *SearchableSiteProperty*
  
  Bu iki filtre birbirinin yerine kullanılabilir. Örneğin,  `"Site_Path -like 'https://contoso.spoppe.com/sites/doctors*'"` aynı  `"SiteContent_Path -like 'https://contoso.spoppe.com/sites/doctors*'"` sonuçları döndürür. Aranabilir site özelliklerinin listesi için bkz. [SharePoint'de gezinilen ve yönetilen özelliklere genel bakış](/SharePoint/technical-reference/crawled-and-managed-properties-overview). **Sorgulanabilir** sütununda **Evet** ile işaretlenmiş özellikler, site veya site içerik filtresi oluşturmak için kullanılabilir.

### <a name="examples-of-changing-search-permissions-filters"></a>Arama izinleri filtrelerini değiştirme örnekleri

Bu örneklerde **Get-ComplianceSecurityFilter** ve **Set-ComplianceSecurityFilter** cmdlet'lerini kullanarak filtrenin atandığı mevcut kullanıcı listesine kullanıcı ekleme veya kaldırma işlemleri gösterilir. Bir filtreye kullanıcı eklediğinizde veya filtreden kullanıcı kaldırdığınızda, SMTP adresini kullanarak kullanıcıyı belirtin.
  
Bu örnek, filtreye bir kullanıcı ekler.

```powershell
$filterusers = Get-ComplianceSecurityFilter -FilterName OttawaUsersFilter
```

```powershell
$filterusers.users.add("pilarp@contoso.com")
```

```powershell
Set-ComplianceSecurityFilter -FilterName OttawaUsersFilter -Users $filterusers.users
```

Bu örnek bir kullanıcıyı filtreden kaldırır.

```powershell
$filterusers = Get-ComplianceSecurityFilter -FilterName OttawaUsersFilter
```

```powershell
$filterusers.users.remove("annb@contoso.com")
```

```powershell
Set-ComplianceSecurityFilter -FilterName OttawaUsersFilter -Users $filterusers.users
```

## <a name="remove-compliancesecurityfilter"></a>Remove-ComplianceSecurityFilter

**Remove-ComplianceSecurityFilter**, arama filtresini silmek için kullanılır. Silmek istediğiniz filtreyi belirtmek için  _FilterName_ parametresini kullanın.
  
## <a name="more-information"></a>Daha fazla bilgi

- **Arama izinleri filtreleme nasıl çalışır?** Bir arama çalıştırıldığında arama sorgusuna izin filtresi eklenir. İzin filtresi **, AND** Boole işleci tarafından arama sorgusuna katılır. Arama sorgusu ve izinler filtresi için sorgu mantığı şöyle görünür:

  ```text
  <SearchQuery> AND <PermissionsFilter>
  ```

  Örneğin, Bob'un Çalışanlar dağıtım grubunun üyelerinin posta kutularındaki tüm arama eylemlerini gerçekleştirmesine izin veren bir izin filtreniz vardır. Ardından Bob, arama sorgusuyla  `sender:jerry@adatum.com`kuruluştaki tüm posta kutularında bir arama çalıştırır. İzin filtresi ve arama sorgusu bir **AND** işleci tarafından mantıksal olarak birleştirildiğinden, arama jerry@adatum.com tarafından Çalışanlar dağıtım grubunun herhangi bir üyesine gönderilen tüm iletileri döndürür. 

- **Birden çok arama izni filtreniz varsa ne olur?** Bir arama sorgusunda, birden çok izin filtresi **OR** Boole işleçleri tarafından birleştirilir. Bu nedenle, filtrelerden herhangi biri doğruysa sonuçlar döndürülür. Bir aramada, tüm filtreler ( **OR** işleçleri tarafından birleştirilir) **ve** işleci tarafından arama sorgusuyla birleştirilir.

  ```text
  <SearchQuery> AND  (<PermissionsFilter1> OR <PermissionsFilter2> OR <PermissionsFilter3>)
  ```

  Bir arama filtresinin Bob'un yalnızca Çalışanlar dağıtım grubunun üyelerinin posta kutularını aramasına izin verdiği önceki örneği ele alalım. Ardından Bob'un Phil'in posta kutusunu ("Mailbox_Alias -ne 'Phil'") aramasını engelleyen başka bir filtre oluştururuz. Ayrıca Phil'in İşçiler grubunun bir üyesi olduğunu da varsayalım. Bob, kuruluştaki tüm posta kutularında bir arama (önceki örnekten) çalıştırdığında, Bob'un Phil'in posta kutusunda arama yapmasını önlemek için filtre uygulamış olsanız bile Arama sonuçları Phil'in posta kutusu için döndürülür. Bunun nedeni Bob'un Çalışanlar grubunda arama yapmasına izin veren ilk filtrenin doğru olmasıdır. Phil çalışanlar grubunun bir üyesi olduğu için Bob, Phil'in posta kutusunda arama yapabilir.

- **Etkin olmayan posta kutuları için arama izinleri filtrelemesi çalışıyor mu?** Evet, kuruluşunuzda etkin olmayan posta kutularında kimlerin arama yapabileceklerini sınırlamak için posta kutusu ve posta kutusu içerik filtrelerini kullanabilirsiniz. Normal posta kutusu gibi, etkin olmayan bir posta kutusunun da izin filtresi oluşturmak için kullanılan alıcı özelliğiyle yapılandırılması gerekir. Gerekirse, **etkin olmayan posta kutularının özelliklerini görüntülemek için Get-Mailbox -InactiveMailboxOnly** komutunu kullanabilirsiniz. Daha fazla bilgi için bkz [. Etkin olmayan posta kutularını oluşturma ve yönetme](create-and-manage-inactive-mailboxes.md).
  
- **Arama izinleri filtreleme ortak klasörler için çalışıyor mu?** Hayır. Daha önce açıklandığı gibi, arama izinleri filtrelemesi, Exchange ortak klasörlerde kimlerin arama yapabileceklerini sınırlamak için kullanılamaz. Örneğin, ortak klasör konumlarındaki öğeler bir izin filtresi tarafından arama sonuçlarından dışlanamaz.

- **Kullanıcının belirli bir hizmetteki tüm içerik konumlarını aramasına izin vermek, farklı bir hizmetteki içerik konumlarında arama yapmasını da engelliyor mu?** Hayır. Daha önce açıklandığı gibi, kullanıcıların belirli bir hizmetteki içerik konumlarında arama yapmasını (örneğin, kullanıcının herhangi bir Exchange posta kutusunda veya herhangi bir SharePoint sitesinde arama yapmasını engellemek) için bir arama izinleri filtresi oluşturmanız gerekir. Başka bir deyişle, kullanıcının kuruluştaki tüm SharePoint sitelerinde arama yapmasına olanak tanıyan bir arama izinleri filtresi oluşturmak, kullanıcının posta kutularını aramasını engellemez. Örneğin, SharePoint yöneticilerin yalnızca SharePoint sitelerde arama yapmasını sağlamak için, posta kutularını aramalarını engelleyen bir filtre oluşturmanız gerekir. Benzer şekilde, Exchange yöneticilerin yalnızca posta kutularını aramasına izin vermek için, sitelerde arama yapmasını engelleyen bir filtre oluşturmanız gerekir.

- **Arama izinleri filtreleri, arama sorgusu karakter sınırlarına göre sayılır mı?** Evet. Arama izinleri filtreleri, arama sorguları için karakter sınırına göre sayılır. Daha fazla bilgi için bkz. [eBulma sınırları (Premium)](limits-ediscovery20.md).

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