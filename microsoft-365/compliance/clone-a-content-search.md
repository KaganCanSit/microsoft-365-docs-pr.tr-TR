---
title: İçerik Araması Kopyalama
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 4/26/2017
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 7b40eeaa-544c-4534-b89b-9f79998e374c
ms.custom:
- seo-marvel-apr2020
description: Bu makaledeki PowerShell betiğini kullanarak Microsoft 365'deki Microsoft Purview uyumluluk portalında mevcut bir İçerik Aramasını hızla kopyalayabilirsiniz.
ms.openlocfilehash: f5ec0433e445256865033b71082c92889972f827
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66017454"
---
# <a name="clone-a-content-search"></a>İçerik Araması Kopyalama

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview uyumluluk portalında, birçok posta kutusunda veya SharePoint ve OneDrive İş sitelerde arama yapılan Microsoft 365 İçerik Araması oluşturmak biraz zaman alabilir. Url'yi yanlış yazdığınızda, aranacak sitelerin belirtilmesi hatalara da açık olabilir. Bu sorunlardan kaçınmak için bu makaledeki Windows PowerShell betiğini kullanarak mevcut İçerik Aramasını hızla kopyalayabilirsiniz. Bir aramayı kopyaladığınızda, özgün aramayla aynı özellikleri (içerik konumları ve arama sorgusu gibi) içeren yeni bir arama (farklı bir ada sahip) oluşturulur. Ardından anahtar sözcük sorgusunu veya tarih aralığını değiştirerek yeni aramayı düzenleyebilir ve çalıştırabilirsiniz.

İçerik Aramalarını neden kopyalamalı?

- Farklı anahtar sözcük arama sorgularının sonuçlarını karşılaştırmak için aynı içerik konumlarında çalıştırılır.

- Yeni bir arama oluştururken çok sayıda içerik konumunu yeniden girdiğinizden sizi kurtarmak için.

- Arama sonuçlarının boyutunu küçültmek için. Örneğin, dışarı aktarılmayacak kadar çok sonuç döndüren bir aramanız varsa, aramayı kopyalayabilir ve ardından arama sonuçlarının sayısını azaltmak için tarih aralığına göre bir arama koşulu ekleyebilirsiniz.

## <a name="script-information"></a>Betik bilgileri

- Exchange Online V2 modülünü yüklemeniz gerekir. Yönergeler için bkz. [EXO V2 modülünü yükleme ve koruma](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

- Bu konuda açıklanan betiği çalıştırmak için Microsoft Purview uyumluluk portalında eBulma Yöneticisi rol grubunun üyesi olmanız gerekir.

- Betik en az hata işleme içerir. Betiğin birincil amacı, bir içerik aramasını hızla kopyalamaktır.

- Betik yeni bir İçerik Araması oluşturur ancak başlatmaz.

- Bu betik, kopyaladığınız İçerik Aramasının bir eBulma olayıyla ilişkilendirilip ilişkilendirilmediğini dikkate alır. Arama bir servis talebiyle ilişkilendirilmişse, yeni arama aynı servis talebiyle de ilişkilendirilir. Mevcut arama bir servis talebiyle ilişkilendirilmiyorsa, yeni arama Microsoft Purview uyumluluk portalındaki **İçerik arama** sayfasında listelenir.

- Bu konuda sağlanan örnek betik, herhangi bir Microsoft standart destek programı veya hizmeti altında desteklenmez. Örnek betik, herhangi bir garanti olmadan OLDUĞU GIBI sağlanır. Microsoft, satılabilirlik veya belirli bir amaca uygunlukla ilgili zımni garantiler dahil ancak bunlarla sınırlı olmaksızın tüm zımni garantileri de reddeder. Örnek betiğin ve belgelerin kullanımından veya performansından kaynaklanan tüm risk sizinle kalır. Hiçbir durumda Microsoft, yazarları veya betiklerin oluşturulması, üretimi veya teslimi ile ilgili herhangi bir kişi, örnek betiklerin veya belgelerin kullanımından veya kullanılamama durumundan kaynaklanan herhangi bir zarardan (bunlarla sınırlı olmaksızın, iş kârı kaybı, iş kesintisi, iş bilgisi kaybı veya diğer maddi kayıplar dahil) sorumlu tutulamaz,  Microsoft'a bu tür hasarlar olabileceği bildirilmiş olsa bile.

## <a name="step-1-run-the-script-to-clone-a-search"></a>1. Adım: Aramayı kopyalamak için betiği çalıştırma

Bu adımdaki betik, var olan bir betiği kopyalayarak yeni bir İçerik Araması oluşturur. Bu betiği çalıştırdığınızda aşağıdaki bilgiler istenir:

- **Kullanıcı kimlik bilgileriniz** - Betik, Güvenlik & Uyumluluk PowerShell'e bağlanmak için kimlik bilgilerinizi kullanır. Daha önce belirtildiği gibi, betiği çalıştırmak için Microsoft Purview uyumluluk portalında eKeşif Yöneticisi rol grubunun üyesi olmanız gerekir.

- **Var olan aramanın adı** - Bu, kopyalamak istediğiniz İçerik Araması'dır.

- **Oluşturulacak yeni aramanın adı** - Bu değeri boş bırakırsanız, betik yeni arama için kopyaladığınız aramanın adını temel alan bir ad oluşturur.

Aramayı kopyalamak için:

1. Aşağıdaki metni .ps1 dosya adı soneki kullanarak bir Windows PowerShell betik dosyasına kaydedin; örneğin, `CloneSearch.ps1`.

   ```powershell
   # This PowerShell script clones an existing content search in Microsoft Purview compliance.

   # Ask for the name of the search you want to clone
   $searchName = Read-Host 'Enter the name of the search that you want to clone'
   # Ask for the name of the new search
   $newSearchName = Read-Host 'Enter a name for the new search [leave blank to automatically generate a name]'
   $originalSearch = Get-ComplianceSearch $searchName -EA SilentlyContinue
   # Make sure we have a valid search before continuing
   if(!$originalSearch)
   {
       Write-Error "Couldn't find search: $searchName"
       return
   }
   $searchNameCounter = 1
   # Find a suitable name for the new search
   while(!$newSearchName)
   {
       $newSearchName = $originalSearch.Name + "_" + $searchNameCounter
       $tempSearch = Get-ComplianceSearch $newSearchName -EA SilentlyContinue
       if ($tempSearch)
       {
           $newSearchName = $null
           $searchNameCounter++
       }
   }
   $caseName
   # Determine if the search is part of a case; if so get the case name
   if ($originalSearch.CaseId)
   {
       $searchCase = Get-ComplianceCase $originalSearch.CaseId
       $caseName = $searchCase.Name
   }
   # Need to cast this value as a Boolean the old fashion way
   $allowNotFoundExchangeLocationsEnabled = $false
   if ($originalSearch.AllowNotFoundExchangeLocationsEnabled)
   {
       $allowNotFoundExchangeLocationsEnabled = $true
   }
   $newSearch = New-ComplianceSearch -Name $newSearchName -AllowNotFoundExchangeLocationsEnabled $allowNotFoundExchangeLocationsEnabled -Case $caseName -ContentMatchQuery $originalSearch.ContentMatchQuery -Description $originalSearch.Description -ExchangeLocation $originalSearch.ExchangeLocation -ExchangeLocationExclusion $originalSearch.ExchangeLocationExclusion -Language $originalSearch.Language -SharePointLocation $originalSearch.SharePointLocation -SharePointLocationExclusion $originalSearch.SharePointLocationExclusion -PublicFolderLocation $originalSearch.PublicFolderLocation
   if ($newSearch)
   {
       Write-Host $newSearch.Name "was successfully created" -ForegroundColor Yellow
   }
   ```

2. [Güvenlik & Uyumluluğu PowerShell'e Bağlan](/powershell/exchange/connect-to-scc-powershell). Aynı PowerShell penceresinde betiği kaydettiğiniz klasöre gidin.

3. Betiği çalıştırın; örneğin:

     ```powershell
     .\CloneSearch.ps1
     ```

4. Betik tarafından istendiğinde aşağıdaki bilgileri girin. Her bilgi parçasını yazın ve **Enter tuşuna** basın.

     - Mevcut aramanın adı.
     - Yeni aramanın adı.

     Betik yeni İçerik Aramasını oluşturur ancak başlatmaz. Bu size sonraki adımda aramayı düzenleme ve çalıştırma fırsatı verir. Yeni aramanın bir servis talebiyle ilişkilendirilip ilişkilendirilmediğine bağlı olarak **, Get-ComplianceSearch** cmdlet'ini çalıştırarak veya Microsoft Purview uyumluluk portalındaki **İçerik araması** veya **eBulma** sayfasına giderek yeni aramanın özelliklerini görüntüleyebilirsiniz.

## <a name="step-2-edit-and-run-the-cloned-search-in-the-microsoft-purview-compliance-portal"></a>2. Adım: Kopyalanan aramayı Microsoft Purview uyumluluk portalında düzenleme ve çalıştırma

Mevcut bir İçerik Aramasını kopyalamak için betiği çalıştırdıktan sonra, sonraki adım yeni aramayı düzenlemek ve çalıştırmak için Microsoft Purview uyumluluk portalına gitmektir. Daha önce belirtildiği gibi, anahtar sözcük arama sorgusunu değiştirerek ve arama koşullarını ekleyerek veya kaldırarak bir aramayı düzenleyebilirsiniz. Daha fazla bilgi için bkz.:

- [Office 365 İçerik Arama](content-search.md)

- [İçerik Arama için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md)

- [eBulma durumları](./get-started-core-ediscovery.md)
