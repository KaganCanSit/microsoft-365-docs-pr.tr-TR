---
title: İçerik Arama'ya kopyalama
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Bu makaledeki PowerShell betiğini kullanarak, Uyumluluk Merkezi'nde veya Farklı Bir Uyumluluk Merkezi'nde var olan İçerik Office 365 Microsoft 365.
ms.openlocfilehash: 763bd6ac49841e5b55bbbc187631ef74426d9d0a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983237"
---
# <a name="clone-a-content-search"></a>İçerik Arama'ya kopyalama

Birçok posta kutusu veya posta kutusu Office 365 Microsoft 365 sitelerde arama SharePoint ve sitelerde OneDrive İş İçerik Arama'nın oluşturulması zaman alabilirsiniz. Bir URL'yi yanlış yazmışsanız, arama için sitelerin belirt açık olması hatalara da neden olabilir. Bu sorunlardan kaçınmak için, bu makaledeki Windows PowerShell betiği kullanarak var olan İçerik Arama'larını hızla kopyaabilirsiniz. Bir aramanızı kopyalarken, özgün aramayla aynı özellikleri (içerik konumları ve arama sorgusu gibi) içeren yeni bir arama (farklı bir adla) oluşturulur. Daha sonra anahtar sözcük sorgusunu veya tarih aralığını değiştirerek yeni aramanızı düzenleyebilir ve çalıştırabilirsiniz.
  
İçerik Aramalarını neden klonlayasınız?
  
- Farklı anahtar sözcük arama sorgularının sonuçlarını karşılaştırmak için, aynı içerik konumlarında çalıştırın.
    
- Yeni arama  oluşturmak zorunda kalmanızı, çok fazla sayıda içerik konumu girmenizi kaydetmek için.
    
- Arama sonuçlarının boyutunu azaltmak için. Örneğin, dışarı aktarılamanız için çok fazla sonuç döndüren bir aramanız varsa, arama sonuçlarının sayısını azaltmak için aramanızı klonlar ve sonra tarih aralığını temel alan bir arama koşulu  eklersiniz.
  
## <a name="script-information"></a>Komut dosyası bilgileri

- Bu konu başlığı altında açıklanan betiği çalıştırmak için, Microsoft 365 uyumluluk merkezi Yöneticisi rol grubunun bir üyesi olmak gerekir.
    
- Betik en az hata işlemeyi içerir. Betiğin birincil amacı hızla içerik aramalarını klonlamaktır.
    
- Betik yeni bir İçerik Arama oluşturur, ancak başlatmaz.
    
- Bu betik, tıkanıklıkta olduğunuz İçerik Arama'nın bir eKbulma durumuyla ilişkilendirilip ilişkilendirililil ilişkilendiril noktadaki olmadığını dikkate alır. Arama bir vakayla ilişkilendirilmişse, yeni arama da aynı vakayla ilişkilendirilecek. Var olan arama bir vakayla ilişkili değilse, yeni arama uyumluluk merkezinde **İçerik arama** sayfasında listelenir. 
    
- Bu konu başlığı altında verilen örnek betik, herhangi bir Microsoft standart destek programı veya hizmeti kapsamında desteklenmiyor. Örnek betik, hiçbir garanti olmaksızın OLDUĞU GIBI verilmektedir. Microsoft, ticarete uygunluk veya belirli bir amaca uygunluk ile ilgili zımni garantiler dahil ancak bununla sınırlı olmaksızın her türlü zımni garantiyi bundan sonra feragat ediyor. Örnek betiğin ve belgelerin kullanımından veya performansından doğan tüm riskler size aittir. Hiçbir durumda Microsoft, yazarları veya betiklerin oluşturulması, üretimi veya dağıtımında yer alan diğer herhangi bir kişi, örnek betiklerin veya belgelerin kullanımından ya da kullanılamazlığından kaynaklanan hiçbir zarardan (ticari kar kaybı, iş kesintisi, iş bilgisi kaybı veya diğer maddi kayıplar dahil ancak ancak bu zararlar dahil ancak ancak hiçbir zarardan sorumlu olmayacaktır),  Microsoft bu tür zarar olasılığı hakkında bilgilansa bile.
  
## <a name="step-1-run-the-script-to-clone-a-search"></a>1. Adım: Betiği çalıştırarak bir aramanın kopyasını kopyalama

Bu adımda betik, var olan bir İçerik Arama'ya tıkanarak yeni bir İçerik Arama oluşturacak. Bu betiği çalıştırarak aşağıdaki bilgileri girmeniz istenir:
  
- **Kullanıcı kimlik bilgileriniz** - Betik, Güvenlik ve Uyumluluk Merkezi PowerShell'e bağlanmak & kimlik bilgilerinizi kullanır. Daha önce de belirtildiği gibi, betiği çalıştırmak için Security & compCompliance Center'nda eBulma Yöneticisi rol grubunun üyesi olmak gerekir. 
    
- **Var olan aramanın adı** - Bu, klonlamak istediğiniz İçerik Arama'dır. 
    
- Oluşturulacak **yeni** aramanın adı - Bu değeri boş bırakırsanız betik, tıkanık olarak oluşturduğunuz aramanın adını temel alan yeni arama için bir ad oluşturulur. 
    
Bir aramanızı klonlamak için:
  
1. Aşağıdaki metni, Windows PowerShell dosya adı son eklerini kullanarak bir .ps1 betik dosyasına kaydedin; örneğin, `CloneSearch.ps1`.
    
  ```powershell
  # This PowerShell script clones an existing content search in the Security &amp; Compliance Center.
  # Get login credentials from the user
  if(!$UserCredential)
  {
      $UserCredential = Get-Credential
      $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid -Credential $UserCredential -Authentication Basic -AllowRedirection
      if (!$Session)
      {
          Write-Error "Couldn't create a remote PowerShell session."
          return
      }
      Import-PSSession $Session -AllowClobber -DisableNameChecking
      $Host.UI.RawUI.WindowTitle = $UserCredential.UserName + " (Security & Compliance Center)"
  }
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

2. Windows PowerShell'i açın ve betiği kaydeden klasöre gidin.
    
3. Betiği çalıştırın; örneğin:
    
    ```powershell
    .\CloneSearch.ps1
    ```

4. Kimlik bilgileriniz istendiğinde e-posta adresinizi ve parolanızı girin, ardından Tamam'a **tıklayın**.
    
5. Betik tarafından istendiğinde aşağıdaki bilgileri girin. Her bilgi parçasını yazın ve Enter tuşuna **basın**.
    
    - Var olan aramanın adı.
    
    - Yeni aramanın adı.
    
    Betik yeni İçerik Arama'yı oluşturur, ancak başlatmaz. Bu size, sonraki adımda aramanızı düzenleme ve çalıştırma fırsatı verir. **Get-ComplianceSearch** cmdlet'ini çalıştırarak veya yeni aramanın bir davayla ilişkilendirilmiş olup olmadığını bağlı  olarak uyumluluk merkezinde İçerik arama veya **eBulma** sayfasına gidip yeni aramanın özelliklerini görüntüleyebilirsiniz. 
  
## <a name="step-2-edit-and-run-the-cloned-search-in-the-compliance-center"></a>2. Adım: Uyumluluk merkezinde kopyalanan arama düzenleme ve çalıştırma

Var olan İçerik Arama'larını klonlamak için betiği çalıştırdikten sonra, bir sonraki adım uyumluluk merkezine gidip yeni aramanızı düzenlemek ve çalıştırmaktır. Daha önce de belirtildiği gibi, anahtar sözcük arama sorgusunu değiştirerek ve arama koşullarını ekleyerek veya kaldırarak bir arama düzenleyebilirsiniz. Daha fazla bilgi için bkz.:
  
- [arama sonuçlarında Office 365](content-search.md)
    
- [İçerik Arama için Anahtar Sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md)
    
- [eBulma servis örnekleri](./get-started-core-ediscovery.md)