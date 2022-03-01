---
title: Eski eBulma aramalarını ve 1 Microsoft 365 uyumluluk merkezi 0.
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: admindeeplinkEXCHANGE
ROBOTS: NOINDEX, NOFOLLOW
description: ''
ms.openlocfilehash: fe3f65e2545b71f8cfbaea76dfd34fd2720a790f
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "63018799"
---
# <a name="migrate-legacy-ediscovery-searches-and-holds-to-the-microsoft-365-compliance-center"></a>Eski eBulma aramalarını ve 1 Microsoft 365 uyumluluk merkezi 0.

Microsoft 365 uyumluluk merkezi, eBulma kullanımına yönelik gelişmiş bir deneyim sunar. Örneğin, daha yüksek güvenilirlik, daha iyi performans ve içeriğinizi önemli bir şekilde düzenlemeniz için uyarlanmış özellikler( eBulma iş akışlarına uyarlanan birçok özellik, yakın yinelemeli gruplama, e-posta dizileri, tema çözümlemesi ve tahmine dayalı kodlama gibi verilerin gözden geçirilmesinde yardımcı olmak üzere içeriği ve çözümlemeyi gözden geçirmeye yardımcı olacak kümeleri gözden geçirebilirsiniz.

Müşterilerin yeni ve geliştirilmiş işlevsellikten yararlanmalarına yardımcı olmak için, bu makalede In-Place eBulma aramalarını ve 1024'e Exchange yönetim merkezinden diğer yönetim merkezine geçirme konusunda <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank"></a> temel Microsoft 365 uyumluluk merkezi.

> [!NOTE]
> Birçok farklı senaryo olduğundan, bu makale genel olarak, çalışma sayfalarındaki temel bir eKbulma durumuna arama ve 30 Microsoft 365 uyumluluk merkezi. eBulma servis durumlarını kullanmak her zaman gerekli değildir, ancak bu servis taleplerine kimlerin kuruluş içinde eBulma örneklerine erişimi olduğunu denetlemeniz için izinler atamanıza izin vererek fazladan bir güvenlik katmanı eklerler.

## <a name="before-you-begin"></a>Başlamadan önce

- Bu makalede açıklanan PowerShell komutlarını çalıştırmak için, Microsoft 365 uyumluluk merkezi Yöneticisi'nde eBulma Yöneticisi rol grubunun üyesi olmak gerekir. Ayrıca, genel yönetim merkezinde Keşif Yönetimi rol grubunun üyesi <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange gerekir</a>.

- Bu makalede, eBulma tutma oluşturma konusunda yol gösterici bilgi sağlar. Tutma ilkesi, zaman uyumsuz bir işlem aracılığıyla posta kutularına uygulanır. eBulma ayrımı oluştururken hem CaseHoldPolicy hem de CaseHoldRule oluşturmanız gerekir; aksi takdirde, tutma oluşturulmaz ve içerik konumları ayrı tutma durumuna yerleştirilmemiş olur.

## <a name="step-1-connect-to-exchange-online-powershell-and-security--compliance-center-powershell"></a>1. Adım: Bağlan PowerShell Exchange Online Güvenlik ve Güvenlik & Merkezi PowerShell'i nasıl edinecek?

İlk adım, PowerShell ve Güvenlik Exchange Online Merkezi PowerShell'& bağlanmaktır. Aşağıdaki betiği kopyalayıp bir PowerShell penceresine yapıştırarak çalıştırabilirsiniz. Bağlanmak istediğiniz kuruluşun kimlik bilgileri istenir. 

```powershell
$UserCredential = Get-Credential
$sccSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid -Credential $UserCredential -Authentication Basic -AllowRedirection
Import-PSSession $sccSession -DisableNameChecking
$exoSession = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
Import-PSSession $exoSession -AllowClobber -DisableNameChecking
```

Bu PowerShell oturumunda aşağıdaki adımlarda komutları çalıştırmamız gerekir.

## <a name="step-2-get-a-list-of-in-place-ediscovery-searches-by-using-get-mailboxsearch"></a>2. Adım: In-Place kullanarak eBulma aramalarının listesini Get-MailboxSearch

Kimliği doğrulandıktan sonra, **Get-MailboxSearch** cmdlet'ini çalıştırarak eBulma aramalarının In-Place listesini elde edersiniz. Aşağıdaki komutu kopyalayıp PowerShell'e yapıştırın ve çalıştırın. Arama listesi, adlarıyla ve Uzla ve 122 12/2013 In-Place listelenir.

```powershell
Get-MailboxSearch
```

Cmdlet çıkışı aşağıdakine benzer olur:

![PowerShell örnek Get-MailboxSearch.](../media/MigrateLegacyeDiscovery1.png)

## <a name="step-3-get-information-about-the-in-place-ediscovery-searches-and-in-place-holds-you-want-to-migrate"></a>3. Adım: eBulma arama In-Place ve geçirmek istediğiniz In-Place 1 10 Aya'ya ilişkin bilgi

Yine **Get-MailboxSearch cmdlet'ini** kullanasınız, ama bu kez aramanın özelliklerini elde edin. Bu özellikleri daha sonra kullanmak üzere bir değişkende depoabilirsiniz. Aşağıdaki örnekte, **Get-MailboxSearch** cmdlet'in sonuçları değişkende depolar ve aramanın özellikleri görüntülenir.

```powershell
$search = Get-MailboxSearch -Identity "Search 1"
```

```powershell
$search | FL
```

Bu iki komutun çıkışı aşağıdakine benzer olur:

![Tek bir arama için Get-MailboxSearch kullanılarak Get-MailboxSearch çıktısı örneği.](../media/MigrateLegacyeDiscovery2.png)

> [!NOTE]
> Bu örnekteki In-Place Tutma süresi belirsizdir (*ItemHoldPeriod: Unlimited*). eBulma ve yasal soruşturma senaryolarında tipik bir durumdur. Bekletme süresi süresi süresi belirsizden farklı bir değere sahipse, bunun nedeni büyük olasılıkla saklamanın bir bekletme senaryosunda içeriği tutmak için kullanılıyor olmasıdır. Bekletme senaryoları için Güvenlik & Uyumluluk Merkezi PowerShell'de eBulma cmdlet'lerini kullanmak yerine, içeriği korumak için [New-RetentionCompliancePolicy](/powershell/module/exchange/new-retentioncompliancepolicy) ve [New-RetentionComplianceRule'yi](/powershell/module/exchange/new-retentioncompliancerule) kullanmalarını öneririz. Bu cmdlet'leri kullanmanın sonucu **New-CaseHoldPolicy** ve **New-CaseHoldRule** kullanmaya benzer, ancak bekletme süresi sona erdikten sonra içeriği silme gibi bir bekletme süresi ve bekletme eylemi belirtebilirsiniz. Ayrıca, bekletme cmdlet'lerini kullanmak, bekletme bekletmeyi bir eBulma durumuyla ilişkilendirmeyi gerektirmez.

## <a name="step-4-create-a-case-in-the-microsoft-365-compliance-center"></a>4. Adım: Uyumluluk Merkezinde Microsoft 365 oluşturma

eBulma ayrımı oluşturmak için, tutma ile ilişkilendirmek için bir eBulma vakası oluşturmanız gerektir. Aşağıdaki örnek, istediğiniz adı kullanarak bir eBulma durumu oluşturur. Daha sonra kullanmak üzere bir değişkende yeni vakanın özelliklerini depolarız. Bu özellikleri, durumu oluşturduk sonra `$case | FL` komutu çalıştırarak görüntüebilirsiniz.

```powershell
$case = New-ComplianceCase -Name "[Case name of your choice]"
```
![New-ComplianceCase komutunu çalıştırma örneği.](../media/MigrateLegacyeDiscovery3.png)

## <a name="step-5-create-the-ediscovery-hold"></a>5. Adım: eBulma ayrımını oluşturma

Vaka oluşturulduktan sonra, tutma oluşturarak önceki adımda oluşturduğunuz vakayla ilişkilendirmek için bu belgeyi oluşturabilirsiniz. Hem dava tutma ilkesi hem de dava tutma kuralı oluşturmanız gerektiğini unutmamanız önemlidir. Eğer dava tutma ilkesi oluşturulduktan sonra tutma kuralı oluşturulmazsa, eBulma ayrımı oluşturulmaz ve hiçbir içerik tutmaz.

Geçirmek istediğiniz eBulma ayrımlarını yeniden oluşturmak için aşağıdaki komutları çalıştırın. Bu örneklerde, geçiş yapmak In-Place Adım 3'te bulunan 3. Adıma kadar olan özellikler kullanılır. İlk komut yeni bir büyük/küçük harf tutma ilkesi oluşturur ve özellikleri değişkene kaydeder. İkinci komut, ilgili büyük/harf tutma kuralını oluşturur.

```powershell
$policy = New-CaseHoldPolicy -Name $search.Name -Case $case.Identity -ExchangeLocation $search.SourceMailboxes
```

```powershell
New-CaseHoldRule -Name $search.Name -Policy $policy.Identity
```

![NewCaseHoldPolicy ve NewCaseHoldRule cmdlet'lerini kullanma örneği.](../media/MigrateLegacyeDiscovery4.png)

## <a name="step-6-verify-the-ediscovery-hold"></a>6. Adım: eBulma ayrımını doğrulama

Tutma oluşturmada sorun olup olmadığını kontrol etmek için, tutma dağılımı durumunun başarılı olup olmadığını denetlemek iyi olur. Dağıtım, bir önceki adımda ExchangeLocation parametresinde belirtilen tüm içerik *konumlarını tutmanın* uygulandığı anlamına gelir. Bunu yapmak için **, Get-CaseHoldPolicy cmdlet'ini** çalıştırarak. Önceki adımda oluşturduğunuz *$policy* değişkene kaydedilen özellikler değişkende otomatik olarak güncelleştirilmez, çünkü bu dağılımın başarılı olduğunu doğrulamak için cmdlet'i yeniden çalıştırmanız gerekir. Olay tutma ilkelerinin başarıyla dağıtılması 5 dakika ile 24 saat arasında sürebilir.

eBulma ayrımlarının başarıyla dağıtıldığından emin olmak için aşağıdaki komutu çalıştırın.

```powershell
Get-CaseHoldPolicy -Identity $policy.Identity | Select name, DistributionStatus
```

*DistributionStatus özelliği için Success değeri*, tutmanın içerik konumlarına başarıyla yerleştiril olduğunu gösterir. Dağıtım henüz tamamlanmadı ise, Beklemede **değeri** görüntülenir.

![PowerShell Get-CaseHoldPolicy örnek.](../media/MigrateLegacyeDiscovery5.png)

## <a name="step-7-create-the-search"></a>7. Adım: Arama oluşturma

Son adım, 3. Adımda tanım istediğiniz aramanın yeniden oluşturularak olayla ilişkilendirmektir. Arama oluşturdukktan sonra, Başlangıç Uyumluluğu Arama **cmdlet'ini** kullanarak çalıştırabilirsiniz veya daha sonra çalıştırabilirsiniz.

```powershell
New-ComplianceSearch -Name $search.Name -ExchangeLocation $search.SourceMailboxes -ContentMatchQuery $search.SearchQuery -Case $case.name
```

![PowerShell New-ComplianceSearch örnek.](../media/MigrateLegacyeDiscovery6.png)

## <a name="step-8-verify-the-case-hold-and-search-in-the-microsoft-365-compliance-center"></a>8. Adım: Vakayı doğrulayın, basılı tutun ve Microsoft 365 uyumluluk merkezi

Her şeyin doğru ayarlanmış olduğundan emin olmak için, [https://compliance.microsoft.com](https://compliance.microsoft.com)'ta Microsoft 365 uyumluluk merkezi **gidin ve Çekirdek için eBulma'> tıklayın**.

![Microsoft 365 Merkezi eKbulma'ya bakın.](../media/MigrateLegacyeDiscovery7.png)

3. Adımda oluşturduğunuz durum, **Çekirdek eKbulma sayfasında** listelenir. Vakayı açın ve 4. Adımda oluşturduğunuz ve Hold sekmesinde listelenmiş olduğunu **fark** edin. Uç uç sayfada, tutmanın uygulandığı posta kutusu sayısı ve dağıtım durumu gibi ayrıntıları görmek için, tutma seçeneğini kullanabilirsiniz.

![eKbulma 1. Microsoft 365 uyumluluk merkezi.](../media/MigrateLegacyeDiscovery8.png)

7. Adımda oluşturduğunuz arama, vakanın **Aramalar** sekmesinde listelenir.

![eBulma olay araması Microsoft 365 uyumluluk merkezi.](../media/MigrateLegacyeDiscovery9.png)

Bir eBulma In-Place geçirir, ancak bunu bir eBulma durumuyla ilişkilendirmezse, arama sonuçları çalışma sayfasında İçerik arama Microsoft 365 uyumluluk merkezi.

## <a name="more-information"></a>Daha fazla bilgi

- Bir yönetim merkezinde eK In-Place bulma & hakkında daha fazla <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">bilgi Exchange bkz</a>.
  
  - [Yerinde eKbulma](/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery)

  - [Yerinde Tutma ve Mahkeme Tutma](/exchange/security-and-compliance/in-place-and-litigation-holds)

- Makalede kullanılan PowerShell cmdlet'leri hakkında daha fazla bilgi için bkz:

  - [Get-MailboxSearch](/powershell/module/exchange/get-mailboxsearch)
  
  - [New-ComplianceCase](/powershell/module/exchange/new-compliancecase)

  - [New-CaseHoldPolicy](/powershell/module/exchange/new-caseholdpolicy)
  
  - [New-CaseHoldRule](/powershell/module/exchange/new-caseholdrule)

  - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)
  
  - [New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch)

  - [Start-ComplianceSearch](/powershell/module/exchange/start-compliancesearch)

- Bu bilgiler hakkında daha fazla Microsoft 365 uyumluluk merkezi için bkz. [İlkelere genel Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center.md).