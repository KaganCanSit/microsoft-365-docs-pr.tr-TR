---
title: Eski eBulma aramalarını ve tutmalarını Microsoft Purview uyumluluk portalı geçirme
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
ms.openlocfilehash: 607b66d863c0584ce1bb06c069de7870245cb167
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622601"
---
# <a name="migrate-legacy-ediscovery-searches-and-holds-to-the-compliance-portal"></a>Eski eBulma aramalarını ve tutmalarını uyumluluk portalına geçirme

Microsoft Purview uyumluluk portalı, eBulma kullanımı için gelişmiş bir deneyim sunar: daha yüksek güvenilirlik, daha iyi performans ve içeriğinizi maddeye göre düzenleme örnekleri dahil olmak üzere eBulma iş akışlarına uyarlanmış birçok özellik, içeriği gözden geçirmek için inceleme kümeleri ve analizler de dahil olmak üzere yinelenene yakın gruplandırma, e-posta iş parçacığı oluşturma, tema analizi ve tahmine dayalı kodlama gibi verileri gözden geçirmeye yardımcı olur.

Müşterilerin yeni ve geliştirilmiş işlevsellikten yararlanmasına yardımcı olmak için bu makalede, <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">exchange yönetim merkezinden</a> uyumluluk portalına In-Place eBulma aramalarını ve tutmalarını geçirme konusunda temel yönergeler sağlanır.

> [!NOTE]
> Birçok farklı senaryo olduğundan bu makale, uyumluluk portalında arama ve ayrı tutma işlemlerini eBulma (Standart) durumuna geçirme konusunda genel rehberlik sağlar. eBulma servis taleplerinin kullanılması her zaman gerekli değildir, ancak kuruluşunuzdaki eBulma servis taleplerine kimlerin erişimi olduğunu denetlemek için izinler atamanıza izin vererek ek bir güvenlik katmanı ekler.

## <a name="before-you-begin"></a>Başlamadan önce

- Exchange Online V2 modülünü yüklemeniz gerekir. Yönergeler için bkz. [EXO V2 modülünü yükleme ve koruma](/powershell/exchange/exchange-online-powershell-v2#install-and-maintain-the-exo-v2-module).

- Bu makalede açıklanan PowerShell komutlarını çalıştırmak için uyumluluk portalında eBulma Yöneticisi rol grubunun üyesi olmanız gerekir. Ayrıca <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">, Exchange yönetim merkezindeki</a> Bulma Yönetimi rol grubunun da üyesi olmanız gerekir.

- Bu makalede, eBulma ayrı tutma oluşturma hakkında yönergeler sağlanır. Saklama ilkesi, zaman uyumsuz bir işlem aracılığıyla posta kutularına uygulanır. eBulma ayrı tutması oluştururken hem CaseHoldPolicy hem de CaseHoldRule oluşturmanız gerekir, aksi takdirde ayrı tutma oluşturulmaz ve içerik konumları ayrı tutmaya alınmaz.

## <a name="step-1-connect-to-exchange-online-powershell-and-security--compliance-powershell"></a>1. Adım: Exchange Online PowerShell ve Güvenlik & Uyumluluk PowerShell'e bağlanma

İlk adım, aynı PowerShell penceresinde Exchange Online PowerShell ve Güvenlik & Uyumluluğu PowerShell'e bağlanmaktır. Aşağıdaki komutları kopyalayabilir, bir PowerShell penceresine yapıştırabilir ve ardından çalıştırabilirsiniz. Sizden kimlik bilgileri istenir.

```powershell
Connect-IPPSSession
Connect-ExchangeOnline -UseRPSSession
```

Ayrıntılı yönergeler için bkz[. Güvenlik & Uyumluluğu PowerShell'e](/powershell/exchange/connect-to-scc-powershell) [bağlanma ve Exchange Online PowerShell'e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

## <a name="step-2-get-a-list-of-in-place-ediscovery-searches-by-using-get-mailboxsearch"></a>2. Adım: Get-MailboxSearch kullanarak In-Place eBulma aramalarının listesini alma

Bağlandıktan sonra **Get-MailboxSearch** cmdlet'ini çalıştırarak In-Place eBulma aramalarının listesini alabilirsiniz. Aşağıdaki komutu kopyalayıp PowerShell penceresine yapıştırın ve ardından çalıştırın.

```powershell
Get-MailboxSearch
```

Aramaların listesi, adları ve In-Place Tutma durumlarıyla birlikte listelenir.

Cmdlet çıkışı aşağıdakine benzer olacaktır:

![PowerShell örneği Get-MailboxSearch.](../media/MigrateLegacyeDiscovery1.png)

## <a name="step-3-get-information-about-the-in-place-ediscovery-searches-and-in-place-holds-you-want-to-migrate"></a>3. Adım: Geçirmek istediğiniz In-Place eBulma aramaları ve In-Place Tutmaları hakkında bilgi edinin

Yine **Get-MailboxSearch** cmdlet'ini kullanacaksınız, ancak bu kez aramanın özelliklerini almak için. Bu özellikleri daha sonra kullanmak üzere bir değişkende depolayabilirsiniz. Aşağıdaki örnek **Get-MailboxSearch** cmdlet'inin sonuçlarını bir değişkende depolar ve ardından aramanın özelliklerini görüntüler.

```powershell
$search = Get-MailboxSearch -Identity "Search 1"
```

```powershell
$search | Format-List
```

Bu iki komutun çıkışı aşağıdakine benzer olacaktır:

![Tek bir arama için Get-MailboxSearch kullanmanın PowerShell çıktısı örneği.](../media/MigrateLegacyeDiscovery2.png)

> [!NOTE]
> Bu örnekteki In-Place Tutma süresi belirsizdir (*ItemHoldPeriod: Sınırsız*). Bu, eBulma ve yasal araştırma senaryoları için tipiktir. Saklama süresi belirsiz değerden farklıysa, bunun nedeni büyük olasılıkla bekletme senaryosundaki içeriği korumak için kullanılmakta olmasıdır. Bekletme senaryoları için Güvenlik & Uyumluluğu PowerShell'deki eBulma cmdlet'lerini kullanmak yerine, içeriği korumak için [New-RetentionCompliancePolicy](/powershell/module/exchange/new-retentioncompliancepolicy) ve [New-RetentionComplianceRule](/powershell/module/exchange/new-retentioncompliancerule) kullanmanızı öneririz. Bu cmdlet'leri kullanmanın sonucu **New-CaseHoldPolicy** ve **New-CaseHoldRule** kullanımına benzer, ancak saklama süresi sona erdikten sonra içeriği silme gibi bir saklama süresi ve bekletme eylemi belirtebilirsiniz. Ayrıca, bekletme cmdlet'lerini kullanmak için bekletme saklamayı bir eBulma olayıyla ilişkilendirmeniz gerekmez.

## <a name="step-4-create-a-case-in-the-microsoft-purview-compliance-portal"></a>4. Adım: Microsoft Purview uyumluluk portalı servis talebi oluşturma

eBulma ayrı tutması oluşturmak için ayrı tutma ile ilişkilendirilecek bir eBulma servis talebi oluşturmanız gerekir. Aşağıdaki örnek, seçtiğiniz bir adı kullanarak bir eBulma olayı oluşturur. Yeni servis talebinin özelliklerini daha sonra kullanmak üzere bir değişkende depolayacağız. Olayı oluşturduktan sonra komutunu çalıştırarak `$case | FL` bu özellikleri görüntüleyebilirsiniz.

```powershell
$case = New-ComplianceCase -Name "[Case name of your choice]"
```

![New-ComplianceCase komutunu çalıştırma örneği.](../media/MigrateLegacyeDiscovery3.png)

## <a name="step-5-create-the-ediscovery-hold"></a>5. Adım: eBulma ayrı tutmasını oluşturma

Servis talebi oluşturulduktan sonra ayrı tutmayı oluşturabilir ve önceki adımda oluşturduğunuz servis talebiyle ilişkilendirebilirsiniz. Hem servis talebi tutma ilkesi hem de servis talebi saklama kuralı oluşturmanız gerektiğini unutmayın. Servis talebi saklama ilkesi oluşturulduktan sonra servis talebi saklama kuralı oluşturulmazsa, eBulma ayrı tutması oluşturulmaz ve hiçbir içerik beklemeye alınmaz.

Geçirmek istediğiniz eBulma ayrı tutmasını yeniden oluşturmak için aşağıdaki komutları çalıştırın. Bu örneklerde, 3. Adımdaki In-Place Ayrı Tutma özelliğinin geçirmek istediğiniz özellikleri kullanılır. İlk komut yeni bir büyük/küçük harf saklama ilkesi oluşturur ve özellikleri bir değişkene kaydeder. İkinci komut, karşılık gelen büyük/küçük harf tutma kuralını oluşturur.

```powershell
$policy = New-CaseHoldPolicy -Name $search.Name -Case $case.Identity -ExchangeLocation $search.SourceMailboxes
```

```powershell
New-CaseHoldRule -Name $search.Name -Policy $policy.Identity
```

![NewCaseHoldPolicy ve NewCaseHoldRule cmdlet'lerini kullanma örneği.](../media/MigrateLegacyeDiscovery4.png)

## <a name="step-6-verify-the-ediscovery-hold"></a>6. Adım: eBulma ayrı tutmasını doğrulama

Ayrı tutma oluşturmada sorun olmadığından emin olmak için ayrı tutma dağıtım durumunun başarılı olup olmadığını denetlemek iyi olur. Dağıtım, ayrı tutmanın önceki adımda *ExchangeLocation* parametresinde belirtilen tüm içerik konumlarına uygulandığı anlamına gelir. Bunu yapmak için **Get-CaseHoldPolicy** cmdlet'ini çalıştırabilirsiniz. Önceki adımda oluşturduğunuz *$policy* değişkenine kaydedilen özellikler değişkende otomatik olarak güncelleştirilemediğinden, dağıtımın başarılı olduğunu doğrulamak için cmdlet'i yeniden çalıştırmanız gerekir. Servis talebi saklama ilkelerinin başarıyla dağıtılması 5 dakika ile 24 saat arasında sürebilir.

eBulma ayrı tutma işleminin başarıyla dağıtıldığını doğrulamak için aşağıdaki komutu çalıştırın.

```powershell
Get-CaseHoldPolicy -Identity $policy.Identity | Select name, DistributionStatus
```

*DistributionStatus* özelliğinin **Success** değeri, ayrı tutmanın içerik konumlarına başarıyla yerleştirildiğini gösterir. Dağıtım henüz tamamlanmadıysa **Bekleyen** değeri görüntülenir.

![PowerShell Get-CaseHoldPolicy örneği.](../media/MigrateLegacyeDiscovery5.png)

## <a name="step-7-create-the-search"></a>7. Adım: Aramayı oluşturma

Son adım, 3. Adımda tanımladığınız aramayı yeniden oluşturmak ve servis talebiyle ilişkilendirmektir. Aramayı oluşturduktan sonra **Start-ComplianceSearch** cmdlet'ini kullanarak çalıştırabilir veya daha sonra çalıştırabilirsiniz.

```powershell
New-ComplianceSearch -Name $search.Name -ExchangeLocation $search.SourceMailboxes -ContentMatchQuery $search.SearchQuery -Case $case.name
```

![PowerShell New-ComplianceSearch örneği.](../media/MigrateLegacyeDiscovery6.png)

## <a name="step-8-verify-the-case-hold-and-search-in-the-compliance-portal"></a>8. Adım: Uyumluluk portalında olayı doğrulama, saklama ve arama

Her şeyin doğru ayarlandığından emin olmak için adresinden uyumluluk portalına [https://compliance.microsoft.com](https://compliance.microsoft.com)gidin ve **eBulma > Core'a** tıklayın.

![eBulma'Microsoft Purview uyumluluk portalı.](../media/MigrateLegacyeDiscovery7.png)

3. Adımda oluşturduğunuz servis talebi **, eBulma (Standart)** sayfasında listelenir. Servis talebini açın ve 4. Adımda oluşturduğunuz ayrı tutmanın **Ayrı Tut** sekmesinde listelendiğine dikkat edin. Ayrı tutmanın uygulandığı posta kutularının sayısı ve dağıtım durumu da dahil olmak üzere açılır sayfada ayrıntıları görmek için ayrı tutmayı seçebilirsiniz.

![eBulma, uyumluluk portalında tutar.](../media/MigrateLegacyeDiscovery8.png)

7. Adımda oluşturduğunuz arama, servis talebinin **Aramalar** sekmesinde listelenir.

![Uyumluluk portalında eBulma servis talebi araması.](../media/MigrateLegacyeDiscovery9.png)

bir In-Place eBulma aramasını geçirirseniz ancak bir eBulma olayıyla ilişkilendirmezseniz, uyumluluk portalındaki İçerik arama sayfasında listelenir.

## <a name="more-information"></a>Daha fazla bilgi

- <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezinde</a> In-Place eBulma & Tutmaları hakkında daha fazla bilgi için bkz:

  - [Yerinde eKeşif](/exchange/security-and-compliance/in-place-ediscovery/in-place-ediscovery)

  - [Yerinde Saklama ve Dava Tutma](/exchange/security-and-compliance/in-place-and-litigation-holds)

- Makalede kullanılan PowerShell cmdlet'leri hakkında daha fazla bilgi için bkz:

  - [Get-MailboxSearch](/powershell/module/exchange/get-mailboxsearch)

  - [New-ComplianceCase](/powershell/module/exchange/new-compliancecase)

  - [New-CaseHoldPolicy](/powershell/module/exchange/new-caseholdpolicy)

  - [New-CaseHoldRule](/powershell/module/exchange/new-caseholdrule)

  - [Get-CaseHoldPolicy](/powershell/module/exchange/get-caseholdpolicy)

  - [New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch)

  - [Start-ComplianceSearch](/powershell/module/exchange/start-compliancesearch)

- Uyumluluk portalı hakkında daha fazla bilgi için bkz. [Microsoft Purview uyumluluk portalı genel bakış](microsoft-365-compliance-center.md).