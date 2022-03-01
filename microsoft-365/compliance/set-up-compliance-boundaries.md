---
title: eBulma soruşturmaları için uyumluluk sınırlarını ayarlama
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: eBulma yöneticisinin eBulma yöneticisinin aynı adreste aray kontrolünde kullanabileceği mantıksal sınırlar oluşturmak için uyumluluk sınırlarının nasıl Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 5fe023391823abbde2cb289926863bbcbb98dfb2
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021774"
---
# <a name="set-up-compliance-boundaries-for-ediscovery-investigations"></a>eBulma soruşturmaları için uyumluluk sınırlarını ayarlama

Bu makaledeki kılavuz, soruşturmaları yönetmek için Core eKovery veya Advanced eDiscovery kullanırken uygulanabilir.

Uyumluluk sınırları, eBulma yöneticilerinin aray kontrolü yaptığı kullanıcı içerik konumlarını (posta kutuları, OneDrive hesapları ve SharePoint siteleri gibi) kontrol altına alan bir kuruluş içinde mantıksal sınırlar oluşturabilir. Ayrıca uyumluluk sınırları, kuruluş içinde yasal, insan kaynakları veya diğer soruşturmaları yönetmek için kullanılan eBulma olaylarına kimlerin eriş erişeni kontrol etmek için kullanılır. Çoğunlukla farklı kuruluşlara ayrılmış coğrafi yönetimlere ve hükümetlere uyması gereken çok uluslu şirketler için uyumluluk sınırları gereklidir. Uyumluluk Microsoft 365, içerik aramaları yaparken ve eBulma olaylarında araştırma yaparken bu gereksinimleri karşılamanıza yardımcı olur.
  
Aşağıdaki çizimde yer alan örneği, uyumluluk sınırlarının nasıl işle ilgili olduğunu açıklamak için kullanıyoruz.
  
![Uyumluluk sınırları, eBulma durumlarına erişimi denetim altına alan kuruluşlara ve yönetici rolü gruplarına erişimi denetim altına alan arama izinleri filtrelerinden oluşur.](../media/M365_ComplianceBoundary_OrgChart_v2.png)
  
Bu örnekte, Contoso LTD iki yan kuruluştan (Fourth Coffee ve Coho Winery) oluşan bir kuruluştır. İşletme, eBulma yöneticilerinin ve güvenlik yöneticilerinin yalnızca Exchange posta kutularında, OneDrive hesaplarında ve SharePoint sitelerinde arama işletmesini gerektirir. Ayrıca, eBulma yöneticileri ve güvenlik yöneticileri yalnızca acentelerinde eBulma servis durumlarını görebilir ve yalnızca üyesi olduğu vakalara erişim sağlar. Bu senaryoda, güvenlik nedenleri içerik konumlarını yerinde tutamaz veya bir vakadan içerik dışarı aktaramaz. Uyumluluk sınırları bu gereksinimleri şu şekilde karşılar.
  
- eBulma için arama izinleri filtreleme işlevselliği, eBulma yöneticilerinin ve özel olarak aranacak içerik konumlarını kontrol eder. Bu, Fourth Coffee acentesi'nin eBulma yöneticileri ve şirket yöneticilerinin yalnızca Fourth Coffee yan kuruluşlarının içerik konumlarında arama yapacı olduğu anlamına gelir. Aynı kısıtlama Coho Winery yan kuruluşu için de geçerlidir.

- [Rol grupları](assign-ediscovery-permissions.md#rbac-roles-related-to-ediscovery) uyumluluk sınırları için aşağıdaki işlevleri sağlar:

  - eBulma olaylarını dosyada kimlerin göreceğini Microsoft 365 uyumluluk merkezi. Bu, eBulma yöneticilerinin ve ekip yöneticilerinin yalnızca acentelerinde eBulma servis durumlarını göreceği anlamına gelir.

  - eBulma durumuna kimlerin üye ataytayayıp, denetleme. Bu, eBulma yöneticilerinin ve güvenlik yöneticilerinin yalnızca üyesi olduğu durumlar için üye atay diğer bir anlama gelir.

  - Üyelerin belirli izinler atadığınız rolleri ekleyerek veya kaldırarak gerçekleştirebilirleri eBulma ile ilgili görevleri denetleyin.

- Rol grubuna bir arama izinleri filtresi uygulandığında, rol grubuna eylem gerçekleştirme izinleri atanmış olan rol grubunun üyeleri aramayla ilgili aşağıdaki eylemleri gerçekleştirebilirsiniz:

  - İçerik arama

  - Arama sonuçlarını önizleme

  - Arama sonuçlarını dışarı aktarma

  - Arama tarafından döndürülen öğeleri temizleme

Uyumluluk sınırlarını ayarlama işlemi şöyledir:
  
[1. Adım: Kuruluşlarınız için bir kullanıcı özniteliği belirleme](#step-1-identify-a-user-attribute-to-define-your-agencies)

[2. Adım: Her bir acente için bir rol grubu oluşturma](#step-2-create-a-role-group-for-each-agency)

[3. Adım: Uyumluluk sınırını zorunlu oluşturmak için arama izinleri filtresi oluşturma](#step-3-create-a-search-permissions-filter-to-enforce-the-compliance-boundary)

[4. Adım: Bir şirket içi acente soruşturmaları için eBulma vakası oluşturma](#step-4-create-an-ediscovery-case-for-intra-agency-investigations)

## <a name="before-you-set-up-compliance-boundaries"></a>Uyumluluk sınırlarını ayarlamadan önce

- Kullanıcılara yeni bir lisans Exchange Online gerekir. Bunu doğrulamak için, Exchange Online PowerShell'de [Get-User](/powershell/module/exchange/get-user) cmdlet'ini kullanın.

## <a name="step-1-identify-a-user-attribute-to-define-your-agencies"></a>1. Adım: Kuruluşlarınız için bir kullanıcı özniteliği belirleme

İlk adım, kuruluşlarınızı tanımlayan ve kullanmak üzere bir öznitelik seçmektir. Bu öznitelik, eBulma yöneticisini yalnızca bu öznitelik için belirli bir değer atanmış kullanıcıların içerik konumlarını aramakla sınırlayan arama izinleri filtresi oluşturmak için kullanılır. Örneğin, Contoso'nun Department özniteliğini kullanmaya karar verdi **diyelim** . Fourth Coffee  `FourthCoffee`  yan kuruluşu içindeki kullanıcılar için bu özniteliğin değeri ve Coho Winery yan kuruluşta yer alan kullanıcıların değeri `CohoWinery`. 3. Adımda,  `attribute:value`  bu çifti (örneğin, *Department:FourthCoffee) kullanarak eBulma* yöneticilerinin arayabilirsiniz kullanıcı içerik konumlarını sınırlandırabilirsiniz. 
  
Aşağıda, uyumluluk sınırları için kullanabileceğiniz kullanıcı özniteliklerine bazı örnekler verilmiştir:
  
- Şirket

- CustomAttribute1 - CustomAttribute15

- Bölüm

- Office

- ÜlkeOrRegion (İki harfli ülke kodu)

Tam liste için, desteklenen posta kutusu filtrelerinin tam [listesine bakın](/powershell/exchange/recipientfilter-properties#filterable-recipient-properties).

## <a name="step-2-create-a-role-group-for-each-agency"></a>2. Adım: Her bir acente için bir rol grubu oluşturma

Sonraki adım, kuruluşlarla uyumlu olacak Microsoft 365 uyumluluk merkezi grupları oluşturmaktır. Yerleşik eBulma Yöneticileri grubunu kopyalayıp uygun üyeleri ekleyerek ve sizin ihtiyaçlarınıza uygun olmayan rolleri kaldırarak bir rol grubu oluşturmanızı öneririz. eBulma ile ilgili roller hakkında daha fazla bilgi için bkz [. eBulma izinleri atama](assign-ediscovery-permissions.md).
  
Rol gruplarını oluşturmak için, Microsoft 365 uyumluluk merkezi'de İzinler sayfasına gidin ve araştırmayı yönetmek için her bir ajansta uyumluluk sınırlarını ve eKbulma olaylarını kullanan her ekip için bir rol grubu oluşturun.
  
Contoso uyumluluk sınırları senaryosu kullanılırken, dört rol grubu oluşturularak her biri için uygun üyelerin ekli olması gerekir.
  
- Fourth Coffee eBulma Yöneticileri

- Fourth Coffee Coffee CoffeeS

- Coho Winery eBulma Yöneticileri

- Coho Winery Tirnak
  
Contoso uyumluluk sınırları senaryosunun gereksinimlerini karşılamak için, güvenlik lisanslarının içerik konumlarında tutma  ve bir  vakadan içerik dışarı aktarmasını önlemek üzere güvenlik gruplarının Yerinde Tutma ve Dışarı Aktarma rollerini de kaldırabilirsiniz.

> [!IMPORTANT]
> Bir rol, davanın üyesi olarak ekleyseniz veya bu gruptan çıkarılırsa, rol grubu otomatik olarak davanın üyesi olarak kaldırılır (veya rol grubunun üyesi olduğu herhangi bir durum). Bunun nedeni, kurumlarınızı bir davanın üyelerine yanlışlıkla ek izinler sağlamaktan korumaktır. Benzer şekilde, bir rol grubu silinirse, üyesi olduğu tüm durumlarda gruptan kaldırılır.

## <a name="step-3-create-a-search-permissions-filter-to-enforce-the-compliance-boundary"></a>3. Adım: Uyumluluk sınırını zorunlu oluşturmak için arama izinleri filtresi oluşturma

Her bir acente için rol grupları oluşturduktan sonraki adım, her rol grubunu belirli bir acenteyle ilişkilendirmek ve uyumluluk sınırının kendisini tanımlayan arama izinleri filtrelerini oluşturmaktır. Her bir acente için bir arama izinleri filtresi oluşturmanız gerekir. Güvenlik izinleri filtreleri oluşturma hakkında daha fazla bilgi için bkz. [İçerik Arama için izin filtrelemeyi yapılandırma](permissions-filtering-for-content-search.md).
  
İşte bu makalede, senaryo için uyumluluk sınırları için kullanılan arama izinleri filtresi oluşturmak için kullanılan söz dizimi.

```powershell
New-ComplianceSecurityFilter -FilterName <name of filter> -Users <role groups> -Filters "Mailbox_<MailboxPropertyName>  -eq '<Value> '", "SiteContent_Path -like '<SharePointURL>' -or SiteContent_Path -like '<OneDriveURL>'"
```

Komutta her parametrenin açıklaması şöyledir:
  
- `FilterName`: Filtrenin adını belirtir. Filtrenin kullandığı daireyi açıklayan veya tanımlayan bir ad kullanın.

- `Users`: Bu filtrenin gerçekleştir olduğu arama eylemlerine uygulanan kullanıcıları veya grupları belirtir. Uyumluluk sınırları için, bu parametre filtreyi oluşturduğunuz dairenin rol gruplarını (3. Adımda oluşturduğunuz) belirtir. Bu çok değerli bir parametredir ve virgülle ayırarak bir veya birden çok rol grubu  dahil edebilirsiniz.

- `Filters`: Filtre için arama ölçütlerini belirtir. Uyumluluk sınırları için aşağıdaki filtreleri tanımlarsiniz. Her biri farklı içerik konumları için geçerlidir.

  - `Mailbox`: Parametrede tanımlanan rol OneDrive posta kutularını veya posta kutularını `Users` belirtir. Bu filtre, rol grubu üyelerinin yalnızca posta kutularında veya özel bir OneDrive hesaplarında arama (örneğin, ) aramalarına olanak sağlar`"Mailbox_Department -eq 'FourthCoffee'"`.

  - `SiteContent`: Bu filtre iki ayrı filtre içerir. İlk olarak`SiteContent_Path`, SharePoint de tanımlanan rol gruplarının aray tanımlay role sahip olduğu `Users` siteler belirtmektedir. Örneğin, `SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee'`. İkinci filtre `SiteContent_Path` (ilk `SiteContent_Path` `or` filtreye operatör tarafından bağlanır) acentenin etki alanını (Sitem etki alanı olarak da OneDrive *) belirtir.* Örneğin, `SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'`. Filtrenin yerine `Site_Path` filtreyi de kullanabilirsiniz `SiteContent` . Ve `Site` filtreler `SiteContent` birbirinin yerine kullanılabilir ve bu makalede açıklanan arama izinleri filtrelerini etkilemez.

    > [!IMPORTANT]
    > Önceki arama `SiteContent` izinleri filtresine OneDrive filtreye neden filtre ekli? Filtre hem posta kutuları hem  de OneDrive hesapları için geçerli olsa da, SharePoint filtresinin dahil edilmesi, filtreyi OneDrive filtresinin içermesi OneDrive `Site` içerebilir.`Mailbox` Arama izinleri filtresinde SharePoint filtresi yoksa, Posta Kutusu filtresi uyumluluk sınırı kapsamında OneDrive hesaplarını da içermesi nedeniyle ayrı bir OneDrive filtresi eklemek zorunda olmazsınız. Başka bir deyişle, yalnızca filtreyi içeren bir arama `Mailbox` izinleri filtresi hem posta kutularını hem de OneDrive içerebilir.

Burada, Contoso uyumluluk sınırları senaryosunu desteklemek için oluşturulacak iki arama izni filtresine örnek olarak verilmiştir. Bu örneklerin her ikisi de, posta kutusu ve site filtrelerinin aynı arama izinleri filtresine dahil edilen ve virgülle ayrıldığı virgülle ayrılmış filtreler listesini içerir.
  
### <a name="fourth-coffee"></a>Fourth Coffee

```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```

### <a name="coho-winery"></a>Coho Winery

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'"
```

> [!NOTE]
> Önceki örneklerde yer `Filters` alan parametrelerin söz dizimi filtre *listesi içerir*. Filtreler listesi, posta kutusu filtresi ve virgülle ayrılmış site yol filtresini içeren bir filtredir. Önceki örnekte, virgülün şu şekilde ilerler: `Mailbox` `SiteContent` `-Filters "Mailbox_<MailboxPropertyName>  -eq '<Value> '", "SiteContent_Path -like '<SharePointURL>' -or SiteContent_Path -like '<OneDriveURL>'"`. eBulma araması çalıştırılan bu filtre işlendiğinde, filtreler listesinden iki arama izni filtresi oluşturulur: bir posta kutusu filtresi ve bir tane de Filtre/SharePoint/OneDrive. Filtre listesi kullanmaya alternatif olarak, her bir daire için iki ayrı arama izinleri filtresi oluşturabilirsiniz: posta kutusu özniteliği için bir arama izinleri filtresi ve SharePoint ve site OneDrive filtresi. Her iki durumda da sonuçlar aynı olur. Filtre listesi kullanmak veya ayrı arama izinleri filtreleri oluşturmak tercihe bağlıdır.

### <a name="how-do-the-search-permissions-filters-work-in-this-scenario"></a>Arama izinleri filtreleri bu senaryoda nasıl çalışır?

Bu senaryoda, arama izin filtreleri her bir acenteye şu şekilde uygulanır.

1. Filtre `Mailbox` ilk olarak, eBulma yöneticilerinin arayabilirsiniz içerik konumlarını tanımlamak için uygulanır. Bu durumda, Coho Winery eBulma yöneticileri yalnızca Departman posta kutusu özelliği **FourthCoffee** değerine sahip kullanıcıların posta kutularında OneDrive hesaplarını  arayabilir; Coho Winery eBulma yöneticileri yalnızca Departman posta kutusu özelliği **CohoWinery** değerine sahip kullanıcıların posta kutularını OneDrive hesaplarını  arayabilir. Filtre `Mailbox` bir içerik *konumu filtresidir*, çünkü eBulma yöneticilerinin arayabilirsiniz içerik konumlarını belirtir. Her iki filtrede de, eBulma yöneticileri yalnızca belirli bir posta kutusu özellik değerine sahip içerik konumlarında arama kullanabilir.

2. Filtrenin aranacak içerik konumları tanımlanmamışsa, filtrenin bir sonraki bölümü eBulma yöneticilerinin arayladığı içeriği tanımlar. İlk filtre `SiteContent` , Fourth Coffee eBulma yöneticilerinin yalnızca site yolu özelliği bulunan (veya ile başlayan) `https://contoso.sharepoint.com/sites/FourthCoffee`belgeleri aramalarını sağlar; Coho Winery eBulma yöneticileri yalnızca , içinde (veya başlar) bulunan bir site yolu özelliği olan belgeleri arayabilir `https://contoso.sharepoint.com/sites/CohoWinery`. Dolayısıyla, iki `SiteContent` filtre *içerik filtreleridir* çünkü aranacak içeriği tanımlarlar. Her iki filtrede de, eBulma yöneticileri yalnızca belirli bir belge özelliği değerine sahip belgeleri arayabilir. Aranabilir SharePoint tüm belgelere damgalı olduğundan, ilgili tüm filtreler içerik filtreleridir. Daha fazla bilgi için bkz [. eBulma için izin filtrelemeyi yapılandırma](permissions-filtering-for-content-search.md#new-compliancesecurityfilter).

   > [!NOTE]
   > Bu makaledeki senaryo bunları kullanmasa da, eBulma yöneticilerinin arayabilirsiniz içeriği belirtmek için posta kutusu içerik filtrelerini de kullanabilirsiniz. Posta kutusu içerik filtreleri söz dizimi şudur `"MailboxContent_<property> -<comparison operator> '<value>'"`: . Tarih aralıkları, alıcılar ve etki alanları ya da aranabilir herhangi bir e-posta özelliğine dayalı olarak içerik filtreleri oluşturabilirsiniz. Örneğin, bu filtre eBulma yöneticilerinin yalnızca şu etki alanındaki kullanıcılar tarafından gönderilen veya alınan posta öğelerini contoso.com sağlar: `"MailboxContent_Participants -like 'contoso.com'"`. Posta kutusu içerik filtreleri hakkında daha fazla bilgi için bkz [. Arama izinleri filtrelemeyi yapılandırma](permissions-filtering-for-content-search.md#new-compliancesecurityfilter).

3. Arama izinleri filtresi, AND Boole işleci tarafından arama **sorgusuna** bir araya geldi. Başka bir ifadeyle, kuruluşlardan birdeki eBulma yöneticisi eBulma araması çalıştırsa, arama tarafından döndürülen öğeler arama sorgusuyla ve arama izinleri filtresinde tanımlanan koşullarla eşleşmeli.

## <a name="step-4-create-an-ediscovery-case-for-intra-agency-investigations"></a>4. Adım: Şirket içi soruşturmalar için eBulma vakası oluşturma

Son adım, Microsoft 365 uyumluluk merkezi'de Çekirdek eBulma durumu veya Advanced eDiscovery büyük/küçük harf ayrımını oluşturmak ve 2. Adımda oluşturduğunuz rol grubunu davanın bir üyesi olarak eklemektir. Bu, uyumluluk sınırlarının kullanımıyla ilgili iki önemli özel buna neden olur:
  
- Olayda yalnızca rol grubuna eklenen rol grubunun üyeleri vakayı görebilir ve bu Microsoft 365 uyumluluk merkezi. Örneğin, Fourth Coffee'ler rol grubu bir davanın tek üyesi ise, Fourth Coffee eBulma Yöneticileri rol grubunun üyeleri (veya başka herhangi bir rol grubunun üyeleri) vakayı görem veya erişim slanı yoktur.

- Bir vakaya atanan rol grubunun bir üyesi olayla ilişkilendirilmiş bir arama çalıştırdığı zaman, yalnızca acentesi içindeki içerik konumlarında aramaabilir (3. Adımda oluşturduğunuz arama izinleri filtresiyle tanımlanır.)

Vaka oluşturmak ve üyeler atamak için:

1. Çalışma sayfasının **Core eDiscovery** **veya Advanced eDiscovery** sayfasına gidin Microsoft 365 uyumluluk merkezi bir vaka oluşturun.

2. Vaka listesinde, oluşturduğunuz vakanın adına tıklayın.

3. Vakaya üye olarak rol grupları ekleyin. Yönergeler için aşağıdaki makalelerden birini okuyun:

   - [Çekirdek eKbulma durumuna üye ekleme](get-started-core-ediscovery.md#step-4-optional-add-members-to-a-core-ediscovery-case)

   - [Olayda üye Advanced eDiscovery ekleme](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

> [!NOTE]
> Bir vakaya rol grubu eklerken, yalnızca üyesi olduğunuz rol gruplarını  eklemeniz gerekir.

## <a name="searching-and-exporting-content-in-multi-geo-environments"></a>Multi-Geo ortamlarında içerik arama ve dışarı aktarma

Arama izinleri filtreleri, bir çalışma ortamında içerik konumlarını ararken içeriğin dışarı aktarıldığı yeri ve hangi [veri merkezinde arama SharePoint Multi-Geo sağlar](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md).
  
- **Arama sonuçlarını dışarı aktarma:** Arama sonuçlarını belirli bir veri Exchange posta kutularından, SharePoint sitelerinden ve OneDrive hesaplarından dışarı aktarabilirsiniz. Bu, arama sonuçlarının dışarı aktarılamayacak veri merkezi konumunu belirtebilirsiniz.

    Dışarı *aktarmanın hangi* veri merkezi boyunca yönlendir iş olacağını oluşturmak veya değiştirmek için **New-ComplianceSecurityFilter** veya **Set-ComplianceSecurityFilter** cmdlet'leri için Region parametresini kullanın.
  
    |**Parametre değeri**|**Veri merkezi konumu**|
    |:-----|:-----|
    |NAM  <br/> |Kuzey Amerika (veri merkezleri ABD'dedir)  <br/> |
    |EUR  <br/> |Avrupa  <br/> |
    |APC  <br/> |Asya Pasifik  <br/> |
    |CAN <br/> |Kanada|
    |||

- **İçerik aramalarını yönlendirme:** Tüm sitelerin ve SharePoint ağ hesaplarının içerik OneDrive bir uydu veri merkezine yönlendirebilirsiniz. Bu, aramaları çalıştıracak veri merkezi konumunu belirtebilirsiniz.

    Bölge parametresi için aşağıdaki değerlerden birini kullanarak, tüm sitelerde ve hesaplarda arama SharePoint çalıştıracakları veri merkezi OneDrive kullanın.
  
    |**Parametre değeri**|**Veriler için veri merkezi yönlendirme SharePoint**|
    |:-----|:-----|
    |NAM  <br/> |US  <br/> |
    |EUR  <br/> |Avrupa  <br/> |
    |APC  <br/> |Asya Pasifik  <br/> |
    |CAN  <br/> |US  <br/> |
    |AUS  <br/> |Asya Pasifik  <br/> |
    |KOR  <br/> |Kuruluşun varsayılan veri merkezi  <br/> |
    |GBR  <br/> |Avrupa  <br/> |
    |JPN  <br/> |Asya Pasifik  <br/> |
    |IND  <br/> |Asya Pasifik  <br/> |
    |LAM  <br/> |US  <br/> |
    |NOR  <br/> |Avrupa |
    |BRA  <br/> |Kuzey Amerika veri merkezleri |
    |||

   Arama izinleri filtresi için *Bölge parametresini* belirtmezseniz, kuruluşun birincil parametre SharePoint aranır. Arama sonuçları en yakın veri merkezine dışarı aktarıldı.

   Bu kavramı basitleştirmek için *Bölge parametresi,* SharePoint ve başka veri kaynaklarında içerik aramak için kullanılan veri OneDrive. Bu durum, Exchange'de içerik Exchange için geçerli değildir, çünkü Exchange aramaları veri merkezlerinin coğrafi konumuyla ilişkili değildir. Ayrıca, aynı *Bölge parametre* değeri dışarı aktaran veri merkeziyle yönlendirmeyi de dikte ediyor olabilir. Çoğu durumda coğrafi panosunda verilerin hareketini denetlemeniz gerekir.

> [!NOTE]
> Veri kaynağı olarak Advanced eDiscovery, *Bölge* parametresi verilerin dışarı aktarıldı olduğu bölgeyi denetlemez. Veriler kuruluşun merkezi konumdan dışarı aktarıldı. Ayrıca, SharePoint ve OneDrive'da içerik arama, veri merkezlerinin coğrafi konumuyla ilişkili değildir. Tüm veri merkezlerine arama yapıldı. Bu sorun hakkında daha fazla Advanced eDiscovery için bkz. Advanced eDiscovery [çözüme genel Microsoft 365](overview-ediscovery-20.md).

Aşağıda, uyumluluk sınırları için *arama izin* filtreleri oluştururken Bölge parametresini kullanma örnekleri verilmiştir. Bu, Fourth Coffee yan kuruluş bunun Kuzey Amerika'da bulunduğu ve Coho Winery'nin Avrupa'da bulunduğu varsaymaktadır.
  
```powershell
New-ComplianceSecurityFilter -FilterName "Fourth Coffee Security Filter" -Users "Fourth Coffee eDiscovery Managers", "Fourth Coffee Investigators" -Filters "Mailbox_Department -eq 'FourthCoffee'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/FourthCoffee' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'" -Region NAM
```

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Mailbox_Department -eq 'CohoWinery'", "SiteContent_Path -like 'https://contoso.sharepoint.com/sites/CohoWinery' -or SiteContent_Path -like 'https://contoso-my.sharepoint.com/personal'" -Region EUR
```

Çok coğrafi ortamlardaki içeriği ararken ve dışarı sunarken aşağıdaki şeyleri gözlerde tutabilirsiniz.
  
- Bölge *parametresi*, bu posta kutularının Exchange denetlemez. Posta kutularına arama geldiğinde tüm veri merkezlerinde arama olur. Hangi posta kutulerinde arama Exchange sınırlamak için, arama izinleri *filtresini* oluştururken veya değiştirirken Filters parametresini kullanın.

- eBulma Yöneticisi'nin birden çok SharePoint bölgesinde araması gerekiyorsa, o eBulma yöneticisinin arama izinleri filtresinde kullanarak SharePoint siteleri veya OneDrive hesaplarının bulunduğu bölgeyi belirtmek için farklı bir kullanıcı hesabı oluşturmanız gerekir. Bunu ayarlama hakkında daha fazla bilgi için, İçerik Arama'daki "SharePoint Multi-Geo ortamda içerik [arama" bölümüne bakın](content-search-reference.md#searching-for-content-in-a-sharepoint-multi-geo-environment).

- SharePoint ve OneDrive'de içerik ararken, *Region* parametresi aramaları eBulma yöneticisinin eKököden araştırmalarını yönet yönetecek olduğu birincil veya uydu konumunu yönlendirmektedir. eBulma yöneticisi, SharePoint OneDrive filtresinde belirtilen bölge dışındaki sitelerde arama ve site ararsa, hiçbir arama sonucu döndürülilmez.

- Core eKover'dan *arama sonuçlarını dışarı aktarıyorsanız, tüm içerik konumlarından (Exchange, Skype Kurumsal, SharePoint, OneDrive ve İçerik Arama aracını kullanarak arayabilirsiniz Depolama diğer hizmetler dahil) veri merkezinde Bölge* parametresi. Bu, kuruluşların denetimli kenarlıklar arasında içerik dışarı aktarılamalarına izin vermelerine yardımcı olur. Arama izinleri filtresinde hiçbir bölge belirtilmezse, içerik kuruluşun birincil veri merkezine karşıya yükler.

  Bir siteden içerik Advanced eDiscovery, Bölge parametresini kullanarak içeriğin nereden karşıya *yükll olduğunu kontrol altında bulundurabilirsiniz*. İçerik, azure Depolama merkezi konumdaki veri merkezinde bulunan bir konuma yüklendi. Merkezi konumunuz temel alarak coğrafi konumların listesi için bkz. [Microsoft 365 Multi-Geo eKovery yapılandırması.](../enterprise/multi-geo-ediscovery-configuration.md)

- Var olan arama izinleri filtresini düzenerek, aşağıdaki komutu çalıştırarak bölgeyi ekleyebilir veya değiştirebilirsiniz:

    ```powershell
    Set-ComplianceSecurityFilter -FilterName <Filter name>  -Region <Region>
    ```

## <a name="using-compliance-boundaries-for-sharepoint-hub-sites"></a>Merkezi sitelerde uyumluluk SharePoint kullanma

[SharePoint merkezi siteler,](/sharepoint/dev/features/hub-site/hub-site-overview) çoğunlukla eBulma uyumluluk sınırlarının takip edecekleri aynı coğrafi veya acente sınırlarına göre hizalanır. Bu, uyumluluk sınırı oluşturmak için merkez sitenin site kimliği özelliğini kullanabileceğiniz anlamına gelir. Bunu yapmak için, SharePoint Online PowerShell'deki [Get-SPOHubSite](/powershell/module/sharepoint-online/get-spohubsite#examples) cmdlet'ini kullanarak merkez sitenin SiteId'sini alın ve ardından arama izinleri filtresi oluşturmak üzere bölüm kimliği özelliği için bu değeri kullanın.

Hub sitesinde arama izinleri filtresi oluşturmak için aşağıdaki söz SharePoint kullanın:

```powershell
New-ComplianceSecurityFilter -FilterName <Filter Name> -Users <User or Group> -Filters "Site_Departmentid -eq '{SiteId of hub site}'"
```

Coho Winery acentesi için merkez sitesi için bir arama izinleri filtresi oluşturma örneği:

```powershell
New-ComplianceSecurityFilter -FilterName "Coho Winery Hub Site Security Filter" -Users "Coho Winery eDiscovery Managers", "Coho Winery Investigators" -Filters "Site_Departmentid -eq '44252d09-62c4-4913-9eb0-a2a8b8d7f863'"
```

## <a name="compliance-boundary-limitations"></a>Uyumluluk sınırı sınırlamaları

Uyumluluk sınırları kullanan eBulma olaylarını ve soruşturmalarını yönetmeye ilişkin aşağıdaki sınırlamaları göz zamanlayın.
  
- Bir arama oluştururken ve oluştururken, acentenizin dışındaki içerik konumlarını seçin. Bununla birlikte, arama izinleri filtresi nedeniyle, bu konumlardan gelen içerik arama sonuçlarına dahil değildir.

- eBulma durumlarında uyumluluk sınırları geçerli değildir. Bu, bir dairenin eBulma yöneticisinin bir kullanıcıyı farklı bir acentede yerinde tut olduğu anlamına gelir. Bununla birlikte, eBulma yöneticisi basılı tutunan kullanıcının içerik konumlarında arama yaptığı zaman uyumluluk sınırının uygulanması uygulanır. Bu, eBulma yöneticisi, kullanıcıyı yerinde tutsa bile kullanıcının içerik konumlarını arayabilecektir.

    Ayrıca, tutma istatistikleri yalnızca acentenin içerik konumlarında geçerli olacaktır.

- Size bir arama izinleri filtresi (posta kutusu veya site filtresi) atanmışsa ve SharePoint sitelerinin hepsini içeren bir arama için tekinde olmayan öğeleri dışarı aktarmayı denersanız, şu hata iletisini alırsınız: `Unable to execute the task. Reason: The scope options UnindexedItemsOnly or BothIndexedandUnindexedItems are not allowed when the executing user has a compliance security filter applied`. Size bir arama izinleri filtresi atanmışsa ve SharePoint'den bağımsız olarak dışarı aktarmayı istiyorsanız, aramaya yeniden çalışmalı ve aranacak belirli SharePoint siteleri dahil SharePoint gerekir. Aksi takdirde, dizine alınan öğeleri yalnızca tüm siteyi içeren bir aramadan SharePoint aktarabilirsiniz. Arama sonuçlarını dışarı aktarma seçenekleri hakkında daha fazla bilgi için bkz. [İçerik Arama sonuçlarını Dışarı Aktarma](export-search-results.md#step-1-prepare-search-results-for-export).

- Arama izinleri filtreleri ortak klasörlerdeki Exchange uygulanmaz.

## <a name="more-information"></a>Daha fazla bilgi

- Posta kutusunun lisansı iptal edilirse veya posta kutusu otomatik olarak silinirse, kullanıcı artık uyumluluk sınırı içinde kabul edilir. Posta kutusu silindiğinde posta kutusunda tutma yerleştirilmişse, posta kutusunda korunan içerik yine uyumluluk sınırları veya arama izinleri filtresine tabi olur.

- Kullanıcı için uyumluluk sınırları ve arama izinleri filtreleri uygulanmışsa, kullanıcı hesaplarını değil, posta kutusunu OneDrive öneririz. Başka bir deyişle, bir kullanıcının posta kutusunu silerse, bu kullanıcının OneDrive için arama izin filtresini zorunlu mailbox_RecipientFilter için de OneDrive.

- Uyumluluk sınırları ve arama izinleri filtreleri, Exchange, OneDrive ve SharePoint'daki içeriğe damgalı özniteliklere ve bu damgalı içeriğin sonraki dizinine eklemeye bağlıdır.

- İçerik tabanlı bir uyumluluk sınırı için dışlama filtreleri ( `-not()` arama izinleri filtresinde kullanma gibi) kullanmamanızı öneririz. Son güncelleştirilmiş öznitelikleri olan içerik dizinelenmemişse, dışlama filtresinin kullanımı beklenmeyen sonuçlara neden olabilir.

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

**Who izinleri filtrelerini (New-ComplianceSecurityFilter cmdlet'leri kullanarak) Set-ComplianceSecurityFilter yönetebilirsiniz?**
  
Arama izinleri filtrelerini oluşturmak, görüntülemek ve değiştirmek için, ilgili kuruluşta Kuruluş Yönetimi rol grubunun bir üyesi Microsoft 365 uyumluluk merkezi.
  
**eBulma yöneticisi birden çok ajansa yayılan birden fazla rol grubuna atanırsa, bir kuruluşta veya diğer kuruluşta içerik için nasıl arama yapar?**
  
eBulma yöneticisi, arama sorgularına, aramayı belirli bir acenteyle kısıtlayan parametreler ekleyebilir. Örneğin, bir kuruluş farklı kuruluşlar için **CustomAttribute10** özelliğini belirttiyse, posta kutularını ve özel bir acentenin hesaplarını aramak için aşağıdaki OneDrive sorgularına ekler: `CustomAttribute10:<value>`.
  
**Arama izinleri filtresinde uyumluluk özniteliği olarak kullanılan özniteliğin değeri değiştirilirse ne olur?**
  
Filtrede kullanılan özniteliğin değeri değiştirilirse, arama izinleri filtresinin uyumluluk sınırının uygulanması üç gün kadar sürer. Örneğin Contoso senaryosunda, Fourth Coffee acentesi çalışan bir kullanıcının Coho Winery acentesine aktarıldı diyelim. Sonuç olarak, kullanıcı nesnesinde **Department** özniteliğinin değeri *FourthCoffee'den* *CohoWinery'e değiştirilir*. Bu durumda, Fourth Coffee eDiscovery ve yatırımcılar öznitelik değiştirildikten sonra bu kullanıcı için üç gün boyunca arama sonuçları amayacak. Benzer şekilde, Coho Winery eK bulma yöneticileri ve kullanıcı için arama sonuçları almaları da üç gün kadar sürer.
  
**eBulma yöneticisi iki ayrı uyumluluk sınırlarının içeriğini görebilir mi?**
  
Evet, eBulma yöneticisi her Exchange görünürlüğü olan rol gruplarına ek olarak posta kutularında arama yapılırken bu yapılabilir. Bununla birlikte, SharePoint ve OneDrive hesapları için arama yapan eBulma yöneticisi, yalnızca kuruluşlar aynı bölgede veya coğrafi konumda olduğunda farklı uyumluluk sınırlarında içerik arayabilir. **Not:** site ve sitelerde içerik arama Advanced eDiscovery coğrafi konuma bağlı SharePoint OneDrive, bu sitelerde bu sınırlama geçerli değildir.
  
**Arama izinleri eBulma olay bekletmeleri, bekletme ilkeleri Microsoft 365 DLP için filtre uygulamalı mı?**
  
Şu anda yok.
  
**İçeriğin dışarı aktarıl olduğu bölgeyi kontrol etmek için bir bölge belirtir, ancak SharePoint kuruluşum yoksa, yine de bu bölgede SharePoint?**
  
Arama izinleri filtresinde belirtilen bölge, kuruluşta yoksa, varsayılan bölgede arama ilmez.
  
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
