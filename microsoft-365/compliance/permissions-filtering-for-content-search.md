---
title: eBulma için izin filtrelemeyi yapılandırma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: eBulma yöneticilerinin, yalnızca kuruluşta yer alan posta kutularının ve sitelerin bir alt kümesini aramasına izin için arama izinleri filtrelemeyi kullanın.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 6310334bdbfd1a94456d5e826daebb9f2945af14
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63028426"
---
# <a name="configure-permissions-filtering-for-ediscovery"></a>eBulma için izin filtrelemeyi yapılandırma

eBulma yöneticisinin, yalnızca kuruluşta yer alan posta kutularının ve sitelerin bir alt kümesini aramasına izin olmak için arama izinleri filtrelemeyi kullanabilirsiniz. ayrıca, aynı eBulma Yöneticisi'nin yalnızca belirli bir arama ölçütlerine uyan posta kutusu veya site içeriği için aramasına izin filtrelemeyi de kullanabilirsiniz. Örneğin, eBulma Yöneticisi'nin yalnızca belirli bir konum veya departmanda yer alan kullanıcıların posta kutularında aramasına izin veebilirsiniz. Bunu yapmak için, belirli bir kullanıcı veya kullanıcı grubunun hangi posta kutulerinde arama yapanı sınırlamak için desteklenen bir alıcı filtresi kullanan bir filtre oluşturabilirsiniz. Ayrıca kullanıcının hangi posta kutusu içeriğini aray erişeni belirten bir filtre de oluşturabilirsiniz. Bu, aranabilir ileti özelliğini kullanan bir filtre oluşturarak yapılır. Benzer şekilde, eBulma Yöneticisinin yalnızca belirli sitelerde veya SharePoint aramasına izin veebilirsiniz. Bunun için, aramanın yapl olduğu siteyi sınırlayan bir filtre oluşturabilirsiniz. Ayrıca, hangi site içeriğine aramanın olacağını belirten bir filtre de oluşturabilirsiniz. Bu, aranabilir bir site özelliği kullanan bir filtre oluşturarak yapılır.

arama izinleri filtreleri, İçerik arama, Çekirdek eKbulma ve kaynak arama Advanced eDiscovery içerik için arama Microsoft 365 uyumluluk merkezi. Belirli bir kullanıcıya arama izinleri filtresi uygulandığında, o kullanıcı aramayla ilgili aşağıdaki eylemleri gerçekleştirebilirsiniz:

- İçerik arama

- Arama sonuçlarını önizleme

- Arama sonuçlarını dışarı aktarma

- Arama tarafından döndürülen öğeleri temizleme

Arama izinleri filtrelemeyi, belirli eBulma yöneticilerinin aray kendi kullanıcı içerik konumlarını (posta kutuları, SharePoint siteleri ve OneDrive hesapları *gibi) denetimi* altına alan bir kuruluş içinde mantıksal sınırlar (uyumluluk sınırları olarak adlandırılan) oluşturmak için de kullanabilirsiniz. Daha fazla bilgi için bkz [. eBulma soruşturmaları için uyumluluk sınırlarını ayarlama](set-up-compliance-boundaries.md).
  
Güvenlik ve Uyumluluk & PowerShell'deki aşağıdaki dört cmdlet, arama izinleri filtrelerini yapılandırmanızı ve yönetmenizi sağlar:
  
[New-ComplianceSecurityFilter](#new-compliancesecurityfilter)

[Get-ComplianceSecurityFilter](#get-compliancesecurityfilter)

[Set-ComplianceSecurityFilter](#set-compliancesecurityfilter)

[Remove-ComplianceSecurityFilter](#remove-compliancesecurityfilter)

## <a name="requirements-to-configure-permissions-filtering"></a>İzin filtrelemeyi yapılandırma gereksinimleri

- Uyumluluk güvenlik filtresi cmdlet'lerini çalıştırmak için, uyumluluk filtresinde Kuruluş Yönetimi rol grubunun üyesi Microsoft 365 uyumluluk merkezi. Daha fazla bilgi için Güvenlik [ve Uyumluluk Merkezi'& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

- Uyumluluk güvenlik filtresi cmdlet'lerini kullanmak Exchange Online Güvenlik & Uyumluluk Merkezi PowerShell'e bağlanın. Bu gerekli bir durumdur çünkü bu cmdlet'ler posta kutusu özelliklerine erişim gerektirir ve bu nedenle Exchange Online PowerShell'e bağlanabilirsiniz. Sonraki bölümde yer alan adımlara bakın.

- Arama izinleri [filtreleri hakkında](#more-information) ek bilgi için Daha fazla bilgi bölümüne bakın.

- Etkin olmayan posta kutularına arama izinleri filtreleme uygulanabilir; bu da, etkin olmayan posta kutularında kimlerin aramalandır bilgileriyle sınırlı olarak posta kutusu ve posta kutusu içerik filtrelemesi kullanabileceğiniz anlamına gelir. İzin filtreleme [ve etkin olmayan](#more-information) posta kutuları hakkında ek bilgi için Daha fazla bilgi bölümüne bakın.

- Arama izinleri filtreleme, aynı klasörde ortak klasörlerde kimlerin arama olacağını sınırlamak Exchange.

- Kuruluşta oluşturulacak arama izinleri filtresi sayısında bir sınırlama yoktur. Bununla birlikte, arama sorgusunun en çok 100 durumu olabilir. Bu durumda koşul, bir Boole işleci ( **VE**, VEYA ve NEAR gibi) tarafından sorguya bağlı bir **şey** olarak **tanımlanır**. Koşulların sayısıyla ilgili sınır, arama sorgusunun kendisini ve aramayı çalıştıran kullanıcıya uygulanan tüm arama izin filtrelerini içerir. Bu nedenle, sahip olduğunuz arama izinleri filtreleri ne kadar fazla olursa (özellikle de bu filtreler aynı kullanıcı veya kullanıcı grubuna uygulandığında), arama için en fazla sayıda koşulları aşma şansı o kadar iyi olur. Kuruluşun koşullar sınırına ulaşmasını önlemek için, kuruluşta arama izinleri filtresi sayısını iş gereksinimlerinizi karşılamak üzere mümkün olan en az bir süreyle sınırlı tutabilirsiniz. Daha fazla bilgi için bkz [. eBulma soruşturmaları için uyumluluk sınırlarını ayarlama](set-up-compliance-boundaries.md#frequently-asked-questions).

## <a name="connect-to-exchange-online-and-security--compliance-center-powershell-in-a-single-session"></a>Bağlan oturumda Exchange Online ve Güvenlik & Uyumluluk Merkezi PowerShell'i kullanabilirsiniz

Bu bölümdeki betiği başarıyla çalıştıramadan önce, Exchange Online PowerShell V2 modülünü indirmeniz ve yüklemeniz gerekir. Bilgi için bkz[. Exchange Online PowerShell V2 modülü hakkında](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

1. Dosya adı son eklerini kullanarak Windows PowerShell betik dosyasına aşağıdaki metni **.ps1**. Örneğin, bu dosyayı **ConnectEXO-SCC.ps1.**

    ```powershell
    Import-Module ExchangeOnlineManagement
    $UserCredential = Get-Credential
    Connect-ExchangeOnline -Credential $UserCredential -ShowBanner:$false
    Connect-IPPSSession -Credential $UserCredential
    $Host.UI.RawUI.WindowTitle = $UserCredential.UserName + " (Exchange Online + Compliance Center)"
    ```

2. Yerel bilgisayarınızda Dosya Windows PowerShell açın, önceki adımda oluşturduğunuz betiğin bulunduğu klasöre gidin ve sonra betiği çalıştırın; örneğin:

    ```powershell
    .\ConnectEXO-SCC.ps1
    ```

Bunun işe yarap çalışmadı olduğunu nasıl bilsiniz? Betiği çalıştırdikten sonra, Exchange Online ve Güvenlik & PowerShell'den cmdlet'ler yerel Windows PowerShell aktarılır. Hiçbir hata alasanız, başarılı bir şekilde bağlandınız. Hızlı bir test, PowerShell cmdlet'leri Exchange Online Güvenlik &'i çalıştırmaktır. Örneğin, **Get-Mailbox** ve **Get-ComplianceSearch çalıştırabilirsiniz**.

PowerShell bağlantı hatalarını gidermek için bkz:

- [Bağlan'Exchange Online PowerShell'e](/powershell/exchange/connect-to-exchange-online-powershell#how-do-you-know-this-worked)

- [Bağlan ve Uyumluluk & PowerShell'e](/powershell/exchange/connect-to-scc-powershell#how-do-you-know-this-worked)

## <a name="new-compliancesecurityfilter"></a>New-ComplianceSecurityFilter

Arama **izinleri filtresi oluşturmak için New-ComplianceSecurityFilter** kullanılır. Bu cmdlet'in temel söz dizimi şöyledir:

```powershell
New-ComplianceSecurityFilter -FilterName <name of filter> -Users <user or role group> -Filters <filter>
```

Aşağıdaki bölümlerde bu cmdlet'in parametreleri açıklanmaktadır. Arama izinleri filtresi oluşturmak için tüm parametreler gereklidir.

### <a name="filtername"></a>*FilterName*

_FilterName_ parametresi, izin filtresinin adını belirtir. Bu ad, **Get-ComplianceSecurityFilter, Set-ComplianceSecurityFilter** ve **Remove-ComplianceSecurityFilter** cmdlet'lerini kullanırken bir filtreyi kimlikle ayarlamak için kullanılır. 

### <a name="filters"></a>*Filtreler*

_Filters parametresi_, uyumluluk güvenlik filtresi için arama ölçütlerini belirtir. Üç farklı filtre türü oluşturabilirsiniz:  

- **Posta OneDrive kutusu veya filtre uygulama:** Bu filtre türü posta kutularını belirtir ve OneDrive kullanıcıların (_Users_ parametresi tarafından belirtilen) aranabilir olduğu hesapları belirtir. Bu filtre türüne içerik konumu *filtresi denir* , çünkü kullanıcının arayladığı içerik konumlarını tanımlar. Bu filtre türünün söz dizimi **Mailbox_** _MailboxPropertyName'tir_; burada _MailboxPropertyName_ posta kutularının kapsamını ve aranacak posta kutusu hesaplarının kapsamını OneDrive için kullanılan posta kutusu özelliğini belirtir. Örneğin, `"Mailbox_CustomAttribute10 -eq 'OttawaUsers'"` posta kutusu filtresi kullanıcının bu filtreyi yalnızca CustomAttribute10 özelliğinde "OttawaUsers" değeri bulunan posta kutularında ve OneDrive hesaplarında aramasına izin verir.

  Desteklenen herhangi bir filtrelenebilir alıcı özelliği, posta kutusunda _MailboxPropertyName_ özelliği için veya alıcı OneDrive kullanılabilir. Aşağıdaki tabloda, posta kutusu veya posta kutusu filtresi oluşturmak için yaygın olarak kullanılan dört OneDrive listele. Tabloda, özelliğin filtrede kullanımına da bir örnek yer almaktadır.

  |Özellik adı  |Örnek  |
  |---------|---------|
  |Diğer Ad    |`"Mailbox_Alias -like 'v-'"`         |
  |Şirket  |`"Mailbox_Company -eq 'Contoso'"`        |
  |CountryOrRegion |`"Mailbox_CountryOrRegion -eq 'United States'"`         |
  |Bölüm |`"Mailbox_Department -eq 'Finance'"`        |
  |||

- **Posta kutusu içeriği filtreleme:** Aramanın uygulandığı içeriğe bu filtre türü uygulanır. Bu filtre türü içerik *filtresi olarak adlandırılan* filtrenin adı, atanan kullanıcıların posta kutusunun içeriğini veya aranabilir e-posta özelliklerini belirtir. Bu filtre türünün söz dizimi **MailboxContent_** _SearchablePropertyName dir; burada  _SearchablePropertyName_ aramada belirtilebilir Anahtar Sözcük Sorgu Dili (KQL) özelliğini belirtir. Örneğin, posta kutusu içerik filtresi `"MailboxContent_Recipients  -like 'contoso.com'"` kullanıcının bu filtreyi yalnızca etki alanındaki alıcılara gönderilen iletileri aramasına contoso.com olanak sağlar. Aranabilir e-posta özelliklerinin listesi için bkz. [eBulma için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md#searchable-email-properties).

  > [!IMPORTANT]
  > Tek bir arama filtresi, bir posta kutusu filtresi ve bir posta kutusu içerik filtresi içer yoktur. Bunları tek bir filtrede birleştirmek için, filtre listesi [kullanabilirsiniz](#using-a-filters-list-to-combine-filter-types).  Ancak bir filtre, aynı türde daha karmaşık bir sorgu içerebilir. Örneğin, `"Mailbox_CustomAttribute10 -eq 'FTE' -and Mailbox_MemberOfGroup -eq '$($DG.DistinguishedName)'"`

- **Site ve site içeriği filtreleme:** Atanmış kullanıcıların SharePoint site OneDrive site içeriğini belirtmek için kullanabileceğiniz iki filtre ve bu filtrelerle ilgili iki filtre vardır.

  - **Site_**_SearchableSiteProperty_
  
  - **SiteContent_**_SearchableSiteProperty_
  
   Bu iki filtre birbirinin yerine kullanılabilir. Örneğin, aynı `"Site_Path -like 'https://contoso.sharepoint.com/sites/doctors'"`  `"SiteContent_Path -like 'https://contoso.sharepoint.com/sites/doctors'"` sonuçları verirsiniz. Aranabilir site özelliklerinin listesi için bkz. [eBulma](keyword-queries-and-search-conditions.md#searchable-site-properties) için anahtar sözcük sorguları ve arama koşulları Daha eksiksiz bir liste için bkz. EBulma'da gezinilen ve yönetilen [özelliklere genel SharePoint](/SharePoint/technical-reference/crawled-and-managed-properties-overview). Sorgulanabilir sütununda **Evet olarak** **işaretlenen** özellikler, site veya site içerik filtresi oluşturmak için kullanılabilir.  

  > [!IMPORTANT]
  > Desteklenen özelliklerden birini kullanarak site filtresinin ayarlaması, filtrede site özelliğinin bu sitenin tüm belgelerine yay anlamı değildir. Bu, site filtresinin çalışması ve doğru içeriği yakalaması için, kullanıcının yine de bu siteden belgelerle ilişkilendirilmiş belirli özellik alanlarını doldurmakla sorumlu olduğu anlamına gelir. Örneğin, kullanıcının "Site_RefineableString00 -eq 'abc'" uygulanmış bir güvenlik filtresi varsa ve kullanıcı "xyz" anahtar sözcük sorgusunu kullanarak bir arama çalıştırır. Güvenlik filtresi sorguya eklenir ve gerçek sorgu "xyz **AND RefineableString0:'abc'"** olur. Kullanıcının site'de gerçekten de RefineableString00 alanında "abc" olarak değere sahip olduğundan emin olması gerekir. Yoksa, arama sorgusu hiçbir sonuç aramaz.

Arama izinleri filtreleri için Filters parametresini *yapılandırirken* aşağıdaki noktalar göz önünde bulundurul:

- Posta kutulerinden farklı olarak, Site filtresi konum filtresi gibi olsa bile *siteler* için içerik konum filtresi yoktur. SharePoint OneDrive ve OneDrive için tüm filtreler içerik filtreleridir (*Site_ ve SiteContent_* filtreleri birbirinin yerine kullanılabilirdir), çünkü Yol gibi  siteyle ilgili özellikler doğrudan belgelere damgalır. Neden bu? Bu, yeni bir tasarımın SharePoint sonucu elde olur. Diğer SharePoint, bazı posta kutularında olduğu gibi özellikleri olan bir "site Exchange" yoktur. Bu nedenle, *Yol* özelliği belgeye damgalı ve belgenin bulunduğu sitenin URL'sini içerir. Bu nedenle *Site filtresi,* içerik konumu filtresi olarak değil, içerik filtresi olarak kabul edilir.

- Kullanıcıların belirli bir hizmette (kullanıcının herhangi bir posta kutusunda veya herhangi bir paylaşılan sitede aramasını engelleme gibi) içerik konumlarında arama Exchange için arama izinleri filtresi SharePoint gerekir. Başka bir deyişle, kullanıcının kuruluşta tüm sitelerde veya tüm sitelerde arama SharePoint izin filtresi oluşturmak, o kullanıcının posta kutularını aramasını engellemez. Örneğin, yöneticilerin SharePoint sitelerde arama SharePoint izin vermek için, posta kutularını aramalarını engelleyen bir filtre oluşturmanız gerekir. Benzer şekilde, yöneticilerin Exchange posta kutularını aramasına izin vermek için, site aramalarını engelleyen bir filtre oluşturmanız gerekir.

### <a name="users"></a>*Kullanıcılar*

_Users parametresi_, bu filtrenin aramalarına uygulandığını belirten kullanıcılar. Kullanıcıları diğer adlarına veya birincil SMTP adreslerine göre tanımlama. Virgülle ayrılmış birden çok değer belirtebilirsiniz veya Tüm değerini kullanarak filtreyi tüm kullanıcılara **atabilirsiniz**.

Ayrıca, bir kullanıcı rolü grubu belirtmek için _Users_ Microsoft 365 uyumluluk merkezi da kullanabilirsiniz. Bu, özel bir rol grubu oluşturmanıza ve sonra bu rol grubuna arama izinleri filtresi atamanızı sağlar. Örneğin, çok uluslu bir şirketin ABD yan kuruluşu için eBulma yöneticilerine özel bir rol grubunuz olduğunu kabul etmek için kullanabilirsiniz. Bu rol grubunu belirtmek için  _Users_ parametresini kullanabilir (rol grubunun Name özelliğini kullanarak) ve sonra  _da Filter_ parametresini kullanarak yalnızca ABD'de posta kutularında arama olmasına izin veebilirsiniz. Bu parametreyle dağıtım gruplarını belirtemezseniz.|

### <a name="using-a-filters-list-to-combine-filter-types"></a>Filtre türlerini birleştirmek için filtre listesini kullanma

Filtreler *listesi,* posta kutusu filtresi ve virgülle ayrılmış site filtresini içeren bir filtredir. Bu virgül OR işleci olarak **da** işlev gösterir. Filtre listesi kullanmak, farklı filtre türlerini bir araya getiren tek desteklenen yöntemdir. Aşağıdaki örnekte, Posta Kutusu ve Site filtreleri virgülle **birbirinden bağımsız** olarak **bulunmaktadır** :

```powershell
-Filters "Mailbox_CustomAttribute10 -eq 'OttawaUsers'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/doctors'"
```

Bir arama çalıştırıldıktan sonra, filtre listesi içeren bir filtre işlendiğinde, filtreler listesinden iki arama izni filtresi oluşturulur: Virgülle ayrılmış her filtre için bir filtre. Bu nedenle önceki örnekte, bir posta kutusu arama izinleri filtresi ve bir site arama izinleri filtresi oluşturulmuş olur. Bu filtreler OR **işleciyle** bağlantılıdır.

Filtre listesi kullanmanın alternatifi, iki ayrı arama izinleri filtresi oluşturmak olabilir. Bu nedenle önceki örnekte, posta kutusu özniteliği için bir filtre ve site özniteliği için bir filtre oluşturabilirsiniz. Her iki durumda da sonuçlar aynıdır. Filtre listesi kullanmak veya ayrı arama izinleri filtreleri oluşturmak tercihe bağlıdır.

Filtre listesi kullanma konusunda aşağıdaki şeyleri unutmayın:

- Posta kutusu filtresi ve **MailboxContent** filtresi içeren **bir filtre oluşturmak** için filtre listesini kullan gerekir.

- Filtre listesinin her bileşeni karmaşık bir filtre söz dizimi içerebilir. Örneğin, posta kutusu ve site filtreleri -veya işleciyle ayrılmış birden çok **filtre** içerebilir:

   ```powershell
   -Filters "Mailbox_Department -eq 'CohoWinery' -or Mailbox_CustomAttribute10 -eq 'CohoUsers'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery*'"
   ```

## <a name="examples-of-creating-search-permissions-filters"></a>Arama izinleri filtresi oluşturma örnekleri

Aşağıda, arama izinleri filtresi **oluşturmak için New-ComplianceSecurityFilter** cmdlet'ini kullanma örnekleri verilmiştir.

Bu örnek, "ABD Keşif Yöneticileri" rol grubunun üyelerinin yalnızca posta kutularında arama OneDrive Amerika Birleşik Devletleri'nde kendi hesaplarını aramalarına olanak sağlar.
  
```powershell
New-ComplianceSecurityFilter -FilterName USDiscoveryManagers  -Users "US Discovery Managers" -Filters "Mailbox_CountryOrRegion  -eq 'United States'"
```
  
Bu örnek, kullanıcının annb@contoso.com posta kutuları ve Kanada'daki posta kutuları için OneDrive eylemleri gerçekleştirmelerini sağlar. Bu filtre, Kanada için ISO 3166-1'den gelen üç basamaklı sayısal ülke kodunu içerir.

```powershell
New-ComplianceSecurityFilter -FilterName CountryFilter  -Users annb@contoso.com -Filters "Mailbox_CountryCode  -eq '124'"
```

Bu örnek, kullanıcıların özelAttribute1 posta kutusu özelliği için 'Pazarlama' değerine sahip olan posta kutularını OneDrive hesaplarını aramalarına izin verir.

```powershell
New-ComplianceSecurityFilter -FilterName MarketingFilter  -Users donh,suzanf -Filters "Mailbox_CustomAttribute1  -eq 'Marketing'"
```

Bu örnek, "Fourth Coffee eBulma Yöneticileri" rol grubunun üyelerinin, Department mailbox özelliği için yalnızca 'FourthCoffee' değerine sahip posta kutularını ve OneDrive hesaplarını aramalarına olanak sağlar. Filtre, rol grubu üyelerinin Fourth Coffee Site'de belge aramalarına da SharePoint sağlar.

```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```

> [!NOTE]
> Önceki örnekte, rol grubu üyelerinin hesaplarda belge araması için ek bir site içerik filtresinin (`SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'`) dahil OneDrive gerekir. Bu filtre dahil değilse, filtre yalnızca rol grubu üyelerinin içinde yer alan belgeleri aramasına olanak sağlar `https://contoso.sharepoint.com/sites/FourthCoffee`.

Bu örnek, eBulma Yöneticisi rol grubu üyelerinin yalnızca posta kutularını ve Ottawa Kullanıcıları dağıtım grubunun OneDrive hesaplarını aramalarına olanak sağlar. powershellGet-DistributionGroup daki Exchange Online cmdlet'i Ottawa Kullanıcıları grubunun üyelerini bulmak için kullanılır.
  
```powershell
$DG = Get-DistributionGroup "Ottawa Users"
```

```powershell
New-ComplianceSecurityFilter -FilterName DGFilter  -Users eDiscoveryManager -Filters "Mailbox_MemberOfGroup -eq '$($DG.DistinguishedName)'"
```

Bu örnek, tüm kullanıcıların posta kutularda arama eylemleri gerçekleştirmesini ve OneDrive Yönetim Ekibi dağıtım grubunun üyelerinin hesaplarını engellemesine neden olur. Bu, kullanıcıların bu posta kutularına içerik silebilirleri anlamına gelir. Get-DistributionGroup'daki Exchange Online Cmdlet'i, Yönetim Ekibi grubunun üyelerini bulmak için kullanılır.

```powershell
$DG = Get-DistributionGroup "Executive Team"
```

```powershell
New-ComplianceSecurityFilter -FilterName NoExecutivesPreview  -Users All -Filters "Mailbox_MemberOfGroup -ne '$($DG.DistinguishedName)'" 
```

Bu örnek, eBulma Yöneticileri OneDrive rol grubu üyelerinin yalnızca kuruluşta yer alan OneDrive içerik aramalarına olanak sağlar.

```powershell
New-ComplianceSecurityFilter -FilterName OneDriveOnly  -Users "OneDrive eDiscovery Managers" -Filters "SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```
  
Bu örnek, kullanıcının yalnızca 2015 takvim yılında gönderilen e-posta iletilerde arama eylemleri gerçekleştirmesi kısıtlar.

```powershell
New-ComplianceSecurityFilter -FilterName EmailDateRestrictionFilter -Users donh@contoso.com -Filters "MailboxContent_Received -ge '01-01-2015' -and MailboxContent_Received -le '12-31-2015'"
```

Önceki örnektekine benzer şekilde, bu örnekte de kullanıcı yalnızca 2015 takvim yılında en son değiştirilen belgelerde arama eylemleri gerçekleştirecek şekilde kısıtlandı.

```powershell
New-ComplianceSecurityFilter -FilterName DocumentDateRestrictionFilter -Users donh@contoso.com -Filters "SiteContent_LastModifiedTime -ge '01-01-2015' -and SiteContent_LastModifiedTime -le '12-31-2015'" 
```

Bu örnek, "Keşif Yöneticileri OneDrive olan üyelerin kuruluşta herhangi bir posta kutusunda arama eylemleri gerçekleştirmelerini engellemaktadır.

```powershell
New-ComplianceSecurityFilter -FilterName NoEXO -Users "OneDrive Discovery Managers" -Filters "Mailbox_Alias -notlike '*'"
```

Bu örnek, kuruluşta herkes tarafından gönderilmiş veya gönderilmiş ya da sarad tarafından gönderilmiş veya alınan e-posta iletisinde arama eylemleri gerçekleştirmesini engelleyebilirsiniz.

```powershell
New-ComplianceSecurityFilter -FilterName NoSaraJanet -Users All -Filters "MailboxContent_Participants -notlike 'janets@contoso.onmicrosoft.com' -and MailboxContent_Participants -notlike 'sarad@contoso.onmicrosoft.com'"
```

Bu örnekte, posta kutusu ve site filtrelerini birleştirmek için filtreler listesi kullanılır. Bu örnekte, posta kutusu filtresi bir içerik konumu filtresi ve site filtresi de içerik filtresidir.

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery'"
```

## <a name="get-compliancesecurityfilter"></a>Get-ComplianceSecurityFilter

**Get-ComplianceSecurityFilter**, arama izinleri filtrelerinin listesini bulmak için kullanılır. Belirli bir  _arama filtresinin_ bilgilerini almak için FilterName parametresini kullanın.
  
## <a name="set-compliancesecurityfilter"></a>Set-ComplianceSecurityFilter

**Set-ComplianceSecurityFilter,** var olan arama izinleri filtresini değiştirmek için kullanılır. Aşağıdaki bölümlerde bu cmdlet'in parametreleri açıklanmaktadır. Yalnızca  _FilterName parametresi gereklidir_.
  
### <a name="filtername"></a>*FilterName*

_FilterName_ parametresi, izin filtresinin adını belirtir.

### <a name="users"></a>*Kullanıcılar*

_Users parametresi_, bu filtrenin aramalarına uygulandığını belirten kullanıcılar. Bu çok değerli bir özellik olduğundan, bu parametreyle bir kullanıcı veya kullanıcı grubu belirterek var olan kullanıcı listesinin üzerine yazabilirsiniz. Seçili kullanıcıları ekleme ve kaldırma söz dizimi için aşağıdaki örneklere bakın.

Ayrıca, bir kullanıcı rolü grubu belirtmek için _Users_ Microsoft 365 uyumluluk merkezi da kullanabilirsiniz. Bu, özel bir rol grubu oluşturmanıza ve sonra bu rol grubuna arama izinleri filtresi atamanızı sağlar. Örneğin, çok uluslu bir şirketin ABD yan kuruluşu için eBulma yöneticilerine özel bir rol grubunuz olduğunu kabul etmek için kullanabilirsiniz. Bu rol grubunu belirtmek için  _Users_ parametresini kullanabilir (rol grubunun Name özelliğini kullanarak) ve sonra  _da Filter_ parametresini kullanarak yalnızca ABD'de posta kutularında arama olmasına izin veebilirsiniz. Bu parametreyle dağıtım gruplarını belirtemezseniz.

### <a name="filters"></a>*Filtreler*

_Filters parametresi_, uyumluluk güvenlik filtresi için arama ölçütlerini belirtir. Üç farklı filtre türü oluşturabilirsiniz:

- **Posta OneDrive kutusu ve posta kutusu filtrelemesi:** Bu filtre türü posta kutularını belirtir ve OneDrive kullanıcıların (_Users_ parametresi tarafından belirtilen) aranabilir olduğu hesapları belirtir. Bu filtre türünün söz dizimi  _MailboxPropertyName Mailbox_i içerir; burada MailboxPropertyName_, aramanın geçerli olduğu posta kutularının kapsamını filtrelemek için kullanılan bir posta kutusu özelliği belirtir. Örneğin,  `"Mailbox_CustomAttribute10 -eq 'OttawaUsers'"` posta kutusu filtresi kullanıcının bu filtreyi yalnızca CustomAttribute10 özelliğinde "OttawaUsers" değeri bulunan posta kutularında aramasına izin verir.  _MailboxPropertyName_ özelliği için, desteklenen herhangi bir filtrelenebilir alıcı özelliği kullanılabilir. Desteklenen özelliklerin listesi için bkz. [-RecipientFilter parametresi için filtrelenebilir özellikler](/powershell/exchange/recipientfilter-properties).

- **Posta kutusu içeriği filtreleme:** Aramanın uygulandığı içeriğe bu filtre türü uygulanır. Bu, atanan kullanıcıların arayabilirsiniz olduğu posta kutusu içeriğini belirtir. Bu filtre türünün söz dizimi **MailboxContent_**_SearchablePropertyName'tir_; burada  _SearchablePropertyName_ aramada belirtilebilir Anahtar Sözcük Sorgu Dili (KQL) özelliğini belirtir. Örneğin, posta kutusu içerik filtresi `"MailboxContent_Recipients  -like 'contoso.com'"` kullanıcının bu filtreyi yalnızca etki alanındaki alıcılara gönderilen iletileri aramasına contoso.com olanak sağlar.  Aranabilir e-posta özelliklerinin listesi için bkz. [eBulma için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md).

- **Site ve site içeriği filtreleme:** Atanan kullanıcıların SharePoint veya site OneDrive İş site içeriğini belirtmek için kullanabileceğiniz, siteyle ilgili iki filtre ve daha fazla filtre vardır:

  - **Site_** *SearchableSiteProperty* 
  - **SiteContent** _ *SearchableSiteProperty*
  
  Bu iki filtre birbirinin yerine kullanılabilir. Örneğin, aynı  `"Site_Path -like 'https://contoso.spoppe.com/sites/doctors*'"`  `"SiteContent_Path -like 'https://contoso.spoppe.com/sites/doctors*'"` sonuçları verirsiniz. Aranabilir site özelliklerinin listesi için bkz. Arama sonuçlarında [gezinilen ve yönetilen özelliklere SharePoint](/SharePoint/technical-reference/crawled-and-managed-properties-overview). Sorgulanabilir sütununda **Evet olarak** **işaretlenen** özellikler, site veya site içerik filtresi oluşturmak için kullanılabilir.

### <a name="examples-of-changing-search-permissions-filters"></a>Arama izinleri filtrelerini değiştirme örnekleri

Bu örneklerde, filtrenin atandığı mevcut kullanıcı listesine kullanıcı eklemek veya kaldırmak için **Get-ComplianceSecurityFilter** ve **Set-ComplianceSecurityFilter** cmdlet'lerinin nasıl kullanımı gösterilmektedir. Filtreye kullanıcı ekler veya filtreden kullanıcı kaldırırken, SMTP adresini kullanarak kullanıcıları belirtin.
  
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

Bu örnek, filtreden bir kullanıcı kaldırır.

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

Bir **arama filtresini silmek için Remove-ComplianceSecurityFilter** kullanılır. Silmek  _istediğiniz filtreyi belirtmek için FilterName_ parametresini kullanın.
  
## <a name="more-information"></a>Daha fazla bilgi

- **Arama izinleri filtreleme nasıl çalışır?** Bir arama çalıştırıldında, izin filtresi arama sorgusuna eklenir. İzin filtresi, AND Boole işleci tarafından arama **sorgusuna** bir araya geldi. Arama sorgusunun ve izin filtresinin sorgu mantığı şöyle olur:

  ```text
  <SearchQuery> AND <PermissionsFilter>
  ```

  Örneğin, Ahmet'in, Çalışanlar dağıtım grubunun üyelerinin posta kutuları üzerinde tüm arama eylemlerini gerçekleştirmesine izin veren bir izin filtreniz vardır. Sonra Ahmet, arama sorgusuyla kuruluşteki tüm posta kutularında bir arama çalıştırır  `sender:jerry@adatum.com`. İzin filtresi ve arama sorgusu **AND** işleciyle mantıksal olarak bir araya getiri olduğundan, arama jerry@adatum.com herhangi bir Çalışan dağıtım grubunun üyesine gönderilen tüm iletiyi döndürür. 

- **Birden çok arama izni filtreniz varsa ne olur?** Arama sorgusunda, birden çok izin filtresi OR Boole **işleçleri** tarafından bir araya kullanılır. Dolayısıyla, filtrelerden herhangi biri doğruysa sonuçlar döndürülür. Aramada, tüm filtreler ( **OR** işleçleri tarafından birleştirilmiştir) ve işleci tarafından arama sorgusuyla **bir** araya kullanılır.

  ```text
  <SearchQuery> AND  (<PermissionsFilter1> OR <PermissionsFilter2> OR <PermissionsFilter3>)
  ```

  Önceki örneği örnekle alalım; burada, bir arama filtresi Ahmet'in yalnızca Çalışanlar dağıtım grubunun üyelerinin posta kutularını aramasına izin verir. Sonra, Ahmet'in Fild5'in posta kutusunu ("ne -ne 'Mailbox_Alias'lar' ") aramasını engelleyen başka bir filtre oluşturduk. Ayrıca, Phil'in Çalışanlar grubunun bir üyesi olduğunu da varsayalım. Ahmet kuruluşta yer alan tüm posta kutularında bir arama çalıştırsa (önceki örnekten) Ahmet'in posta kutusunu aramasını engellemek için filtre uygulamanız rağmen, Ahmet'in posta kutusu için arama sonuçları döndürülür. Bunun nedeni, Ahmet'in Çalışanlar grubunda aramalarına izin veren ilk filtrenin doğru çalışmasıdır. Ayrıca, Kemal Çalışanlar grubunun bir üyesi olduğu için Ahmet, Phil'nin posta kutusunda arama kullanabilir.

- **Etkin olmayan posta kutuları için arama izinleri filtreleme çalışır mı?** Evet, posta kutusu ve posta kutusu içerik filtrelerini kullanarak, kurumda etkin olmayan posta kutularında kimlerin arama kullanabileceğini sınırlandırabilirsiniz. Normal bir posta kutusu gibi, etkin olmayan posta kutusunun da izin filtresi oluşturmak için kullanılan alıcı özelliğiyle yapılandırılması gerekir. Gerekirse, etkin olmayan posta **kutularının özelliklerini görüntülemek için Get-Mailbox -InactiveMailboxOnly** komutunu kullanabilirsiniz. Daha fazla bilgi için bkz [. Etkin olmayan posta kutularını oluşturma ve yönetme](create-and-manage-inactive-mailboxes.md).
  
- **Ortak klasörler için arama izinleri filtreleme çalışır mı?** Hayır. Daha önce de belirtildiği gibi, arama izinleri filtreleme özelliği bu dosyalarda ortak klasörlerde kimlerin arama Exchange. Örneğin, ortak klasör konumlarında yer alan öğeler, izin filtresiyle arama sonuçlarından dışlanmaz.

- **Kullanıcının belirli bir hizmette tüm içerik konumlarında aramasına izin verme, o kullanıcının farklı bir hizmette içerik konumlarında aramasını da engelle mi?** Hayır. Daha önce de belirtildiği gibi, kullanıcıların belirli bir hizmette içerik konumlarında (kullanıcının herhangi bir posta kutusunda veya herhangi bir SharePoint sitesinde aramasını engelleme gibi) arama izinlerini açıkça engellemek için bir Exchange arama izinleri filtresi oluşturmanız gerekir. Başka bir deyişle, kullanıcının kuruluşta tüm sitelerde veya tüm sitelerde arama SharePoint izin filtresi oluşturmak, o kullanıcının posta kutularını aramasını engellemez. Örneğin, yöneticilerin SharePoint sitelerde arama SharePoint izin vermek için, posta kutularını aramalarını engelleyen bir filtre oluşturmanız gerekir. Benzer şekilde, yöneticilerin Exchange posta kutularını aramasına izin vermek için, site aramalarını engelleyen bir filtre oluşturmanız gerekir.

- **Arama izinleri, arama sorgusu karakter sınırları içinde sayılır mı?** Evet. Arama izinleri filtreleri, arama sorgularında karakter sınırını karşılar. Daha fazla bilgi için bkz. [Alan Advanced eDiscovery](limits-ediscovery20.md).

**Kuruluşta oluşturulacak arama izinleri filtresi sayısı en fazla kaçtır?**
  
Kuruluşta oluşturulacak arama izinleri filtresi sayısında bir sınırlama yoktur. Bununla birlikte, arama sorgusunun en çok 100 durumu olabilir. Bu durumda koşul, bir Boole işleci ( **VE**, VEYA ve NEAR gibi) tarafından sorguya bağlı bir **şey** olarak **tanımlanır**. Koşulların sayısı sınırı, arama sorgusunun kendisini ve aramayı çalıştıran kullanıcıya uygulanan tüm arama izin filtrelerini içerir. Bu nedenle, sahip olduğunuz arama izinleri filtreleri ne kadar fazla olursa (özellikle de bu filtreler aynı kullanıcı veya kullanıcı grubuna uygulandığında), arama için en fazla sayıda koşulları aşma şansı o kadar iyi olur.

Bu sınırın nasıl çalıştığını anlamak için, arama çalıştırıldında arama sorgusuna bir arama izin filtresinin ek olduğunu anlamış olun. Arama izinleri filtresi, **AND Boole** işleci tarafından arama sorgusuna bir araya geldi. Arama sorgusunun sorgu mantığı ve tek bir arama izinleri filtresi şöyle olur:

```text
<SearchQuery> AND <PermissionsFilter>
```

OR **Boole** işleciyle birden çok arama izinleri filtresi bir araya kullanılır ve bu koşullar ARAMA sorgusuna **AND işleciyle** bağlanır.

Arama sorgusunun sorgu mantığı ve birden çok arama izinleri filtresi şöyle olur:

```text
<SearchQuery> AND (<PermissionsFilter1> OR <PermissionsFilter2> OR <PermissionsFilter3>...)
```

Arama sorgusunun kendisi, Boole işleçleri tarafından birbirine bağlı birden çok koşullardan oluşan bir sorgu olabilir. Arama sorgusunda yer alan her koşul 100 koşul sınırını da aşar.

Ayrıca, bir sorguya eklenen arama izinleri filtresinin sayısı, aramayı çalıştıran kullanıcıya bağlıdır. Belirli bir kullanıcı arama çalıştırsa, kullanıcıya uygulanan arama izinleri filtreleri (filtrede *Users* parametresi tarafından tanımlanır) sorgunun sonuna eklenir. Kuruluşta yüzlerce arama izni filtresi olabilir, ancak aynı kullanıcılara 100'den fazla filtre uygulanmışsa, bu kullanıcılar aramaları çalıştıracaksa 100 koşula sahip sınır aşılır.

Koşul sınırıyla ilgili bir şey daha unutmayın. Arama sorgusuna veya SharePoint izin filtrelerine dahil edilen belirli site sayısı da bu sınıra göre sayılır. 

Kuruluşun koşullar sınırına ulaşmasını önlemek için, kuruluşta arama izinleri filtresi sayısını iş gereksinimlerinizi karşılamak üzere mümkün olan en az bir süreyle sınırlı tutabilirsiniz.