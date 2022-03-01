---
title: Etkin olmayan posta kutusunun tutma süresini değiştirme
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: 8/29/2017
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: bdee24ed-b8cf-4dd0-92ae-b86ec4661e6b
ms.custom:
- seo-marvel-apr2020
description: Posta Office 365 etkin değil yapıldıktan sonra, bekletme süresini veya etkin Office 365 posta kutusuna atanmış bekletme ilkesi değişikliğini geri alın.
ms.openlocfilehash: bf1131aa0d14222bec7ab1c94983925cfe39e673
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010864"
---
# <a name="change-the-hold-duration-for-an-inactive-mailbox"></a>Etkin olmayan posta kutusunun tutma süresini değiştirme

Etkin [olmayan posta kutusu](inactive-mailboxes-in-office-365.md) , kuruluşdan ayrıldıktan sonra eski çalışanın e-postalarını tutmak için kullanılan posta kutusu durumudur. Posta kutusu, kullanıcı nesnesi silinmeden önce posta kutusuna uygun bir Microsoft 365 devre dışı kalır.  Aşağıdaki 10 tür 10 farklı 100 100 1000 1000 1000 1000 1000 000 0000 0000 hesap silme işlemi

- [Microsoft 365 bekletme ve silme ayarlarıyla,](retention.md) bekletme ilkelerini ve etiketlerini değiştirme

- eBulma durumuyla [ilişkilendirilmiş tutma](ediscovery.md)

- [Mahkeme Tutma](create-a-litigation-hold.md)

- Mevcut bir 1 In-Place tutma.

> [!IMPORTANT]
> Yukarıdaki bekletmelerden herhangi biri kullanıcı hesabı silinmesi üzerine posta kutusunun Microsoft 365 etkin olmaya zorlasa da, etkin olmayan posta kutularını önceden plan ederken Microsoft 365 bekletmeyi kullanmanız kesinlikle önerilir.
>
> - eBulma ayrımları, bir yasal sorunla ilgili belirli, zaman bağlantılı davalara yöneliktir. Bir noktada, büyük olasılıkla bir dava sona erer ve davayla ilişkilendirilmiş esnalar kaldırılır ve eBulma vakası kapatılır (veya silinir). Etkin olmayan bir posta kutusuna yerleştirilen tutma bir eBulma durumuyla ilişkilendirilmişse ve tutma serbest bırakılırsa veya eBulma vakası kapatılır veya silinirse, etkin olmayan posta kutusu kalıcı olarak silinir.
>
> - In-Place yönetim merkezinde Exchange 10 10 10 artık kaldırıldı. 1 Temmuz 2020'den In-Place 1 Temmuz 2020'den Exchange Online. 1 Ekim 2020'den sonra yerinde tutma süresi değiştirilemez. Tutma Tutma uygulanmış etkin olmayan In-Place posta kutuları yalnızca 1/6 /In-Place kaldırılarak silinebilir. Tutmada olan ve etkin olmayan In-Place, tutma kaldırılana kadar korunmaya devam eder. Eski eBulma araçlarının In-Place hakkında daha fazla bilgi için bkz. [Eski eBulma araçlarının emeklilik](legacy-ediscovery-retirement.md).
>
> - [Bir kullanıcı hesabı](create-a-litigation-hold.md) silindikten sonra posta kutusunda içeriği tutmak ve devre dışı kalmak için alternatif bir yöntem olarak mahkeme tutma destekleri devam ediyor. Bununla birlikte, daha eski bir teknoloji olarak bu Microsoft 365 öneririz.

Devre dışı bırakılırsa, posta kutusunun Kurtarılabilir Öğeler klasörü de [](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) içinde olmak üzere içeriği, devre dışı kalmadan önce posta kutusuna yerleştirilena kadar korunur.  

Geçerli saklama, yalnızca süresiz bekletme ilkesi veya etiketiyle ilişkilendirilmiş bekletme Microsoft 365 bekletme ilkesi veya etiket, eBulma vakası veya Mahkeme Tutma (```LitigationHoldDuration```yapılandırılmamış olmadan) gibi zamana bağlı olmaksızın olursa, saklama kaldırılana kadar posta kutusu içeriği süresiz olarak korunur.  

Öte yandan, tutma süresi zaman tabanlı olursa, posta kutusu içeriği tutma süresi dolana kadar korunur; bu noktada, Kurtarılabilir Öğeler klasöründeki tüm öğeler etkin olmayan posta kutusundan kalıcı olarak silinir (temiz olur).

> [!NOTE]
> Etkin olmayan posta kutuları için, bekletme ilkeniz veya etiketleriniz için bekletme Microsoft 365 ve silme ayarı kullanmanızı öneririz.  Yalnızca koruma ayarını seçerseniz, Kurtarılabilir Öğeler klasörü tutma süresinin sonunda temiz olur, ancak diğer silinmemiş öğeler etkin olmayan posta kutusunda süresiz olarak kalır.

Düzenlemeler ve ilkeler geliştikçe, etkin olmayan posta kutusuna atanan tutma süresini değiştirmenizi gereken bazı durumlar olabilir.  Aşağıdaki adımlarda bunun nasıl yapl şekli ana hatlarıyla açık şekilde ve açık adımlar ve ardından açık bir şekilde açık ve açık bir şekilde açık ve açık

## <a name="connect-to-powershell"></a>Bağlan PowerShell'e

Daha önce de belirttiğimiz gibi, birçok farklı türde 0'lar devre dışı posta kutusunun oluşturulmasını tetikler.  Bu nedenle, etkin olmayan posta kutusuna uygulanan tutma süresini değiştirmek için, önce bunu etkileyen 10 tür 10 122 0124'leri tanımlamanız gerekir.  Bunu yapmak için, bekletme türlerini tanımlamak üzere Exchange Online PowerShell kullanmalıdır ve etkin olmayan posta kutusu Microsoft 365 bekletme ilkelerinden veya etiketlerden etkileniyorsa, belirli ilkeleri tanımlamak için Güvenlik ve Uyumluluk Merkezi PowerShell'i de kullanmalıdır.

- PowerShell veya Exchange Online PowerShell & Uyumluluk Merkezi'ne bağlanmak için, aşağıdaki konulardan birini bakın:

  - [Bağlan'Exchange Online PowerShell'e](/powershell/exchange/connect-to-exchange-online-powershell)

  - [Bağlan ve Uyumluluk & PowerShell'e](/powershell/exchange/connect-to-scc-powershell)

## <a name="step-1-identify-the-holds-on-an-inactive-mailbox"></a>1. Adım: Etkin olmayan bir posta kutusunda 1. Adım: Etkin olmayan posta kutusunda 1.

Etkin olmayan bir posta kutusuna farklı türde bekletme Microsoft 365 veya birden çok bekletme ilkesi yerleştiril olabileceği için, ilk adım etkin olmayan bir posta kutusunda bekletmeyi tanımlamaktır.
  
PowerShell'de Exchange Online etkin olmayan belirli bir posta kutusunun tutma bilgilerini görüntülemek için bu komutu çalıştırın.
  
```powershell
Get-Mailbox -Identity <identity of inactive mailbox> -InactiveMailboxOnly | FL DisplayName,Name,DistinguishedName,ExchangeGuid,IsInactiveMailbox,LitigationHoldEnabled,LitigationHoldDuration,LitigationHoldDate,LitigationHoldOwner,InPlaceHolds,ComplianceTagHoldApplied
```

Birden çok etkin olmayan posta kutusunun ne tür olduğunu tanımlamanız gerekirse ve kurumda çok fazla sayıda posta kutusu varsa, PowerShell kullanılarak görüntülenemeyen bir durum olabilir. Bu durumda, aşağıdaki komutu kullanarak ve ortamınız için gerekenleri değiştirerek tüm geçerli bilgileri bir CSV ```Path``` dosyasına aktarabilirsiniz:

```powershell
Get-Mailbox -InactiveMailboxOnly -ResultSize Unlimited | Select DisplayName,Name,DistinguishedName,ExchangeGuid,IsInactiveMailbox,LitigationHoldEnabled,LitigationHoldDuration,LitigationHoldDate,LitigationHoldOwner,InPlaceHolds,ComplianceTagHoldApplied | Export-Csv -NoTypeInformation -Path "C:\Temp\InactiveMailboxHoldTypes.csv"
```

Bu örnekte, aşağıdaki örnekte, farklı olası tutma türlerine sahip devre dışı altı posta kutusu için sonuçlar ve almaktadır.

> [!NOTE]
> Birden çok türde 100 100 100 000 2013 ve 2013 arasında olmak üzere, birden çok 1000 0000 000
  
```text
DisplayName              : Ann Beebe
Name                     : annb
DistinguishedName        : CN=annb,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 664ef44e-c1a0-47b0-9553-2ecdfc6ef840
IsInactiveMailbox        : True
LitigationHoldEnabled    : True
LitigationHoldDuration   : 365.00:00:00
LitigationHoldDate       : 10/25/2021 6:54:57 PM
LitigationHoldOwner      : admin@contoso.com
InPlaceHolds             : {}
ComplianceTagHoldApplied : False
...
DisplayName              : Carol Olson
Name                     : carolo
DistinguishedName        : CN=carolo,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : e646a369-00bf-43d3-837a-8eae8b301d44
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {mbxcdbbb86ce60342489bff371876e7f224:3}
ComplianceTagHoldApplied : False
...
DisplayName              : Megan Bowen
Name                     : meganb
DistinguishedName        : CN=meganb,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 36ec77cb-c524-468a-a8e8-bfb75e01a176
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {mbx6fe063689d404a5bb9940eed0f0bf5d2:1}
ComplianceTagHoldApplied : True
...
DisplayName              : Mario Necaise
Name                     : marion
DistinguishedName        : CN=marion,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 0579e039-a695-40d5-8f0a-0dc04f4b4c8f
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {}
ComplianceTagHoldApplied : False
...
DisplayName              : Abraham McMahon
Name                     : abrahamm
DistinguishedName        : CN=abrahamm,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 55ad8905-4e68-4c8d-940d-e068ec6b51fc
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {UniH7d895d48-7e23-4a8d-8346-533c3beac15d}
ComplianceTagHoldApplied : False
...
DisplayName              : Pilar Pinilla
Name                     : pilarp
DistinguishedName        : CN=pilarp,OU=Soft Deleted
                           Objects,OU=contoso.onmicrosoft.com,OU=Microsoft Exchange
                           Hosted Organizations,DC=NAMPR06A007,DC=PROD,DC=OUTLOOK,DC=COM
ExchangeGuid             : 8d7867d6-bb6d-4cd8-a51f-09d208f97fcc
IsInactiveMailbox        : True
LitigationHoldEnabled    : False
LitigationHoldDuration   : Unlimited
LitigationHoldDate       :
LitigationHoldOwner      :
InPlaceHolds             : {c0ba3ce811b6432a8751430937152491}
ComplianceTagHoldApplied : False
```

Aşağıdaki tabloda, yukarıdaki örnekte yer alan her posta kutusunu devre dışı tutmak için kullanılan altı farklı tutma türü tanımkullanılmaktadır.
  
|**Etkin olmayan posta kutusu**|**Tutma türü**|**Etkin olmayan posta kutusunda 10.**|
|:-----|:-----|:-----|
|Ann Beebe  <br/> |Mahkeme Tutma  <br/> | Özellik  `LitigationHoldEnabled`  , posta kutusunun  `True` Mahkeme Tutmada olduğunu belirten şekilde ayarlanmıştır. <br/><br/> Buna ek olarak `LitigationHoldDuration` , posta `365.00:00:00` kutusu öğelerinin oluşturma tarihten (gönderilen/alınan) sonra 365 gün boyunca mahkemelere tabi olmayacaklarını belirten şekilde ayarlanır.  <br/><br/> Bu `LitigationHoldDate` , MahkemeHold'in etkinleştiril `LitigationHoldOwner` olduğu tarihi gösterir ve mahkeme tutmayı başlatan kişiyi tanımlar. <br/> |
|Carol Olson  <br/> |Microsoft 365 posta kutularına Microsoft 365 uyumluluk merkezi gelen kutusundan bekletme ilkesi yok  <br/> |Özellik`InPlaceHolds`, etkin olmayan posta kutusuna Microsoft 365 bekletme ilkesi GUID'lerini içerir. GUID ön ek ile başladığından `mbx` ve veya ile sona erdiğinde, bunun belirli posta kutularına uygulanan bir bekletme ilkesi olduğunu belirtebilirsiniz `:2` `:3`. <br/><br/> Daha fazla bilgi için bkz [. Bekletme ilkeleri için InPlaceHolds değerinin biçimini anlama](identify-a-hold-on-an-exchange-online-mailbox.md#understanding-the-format-of-the-inplaceholds-value-for-retention-policies).  <br/> |
|Oya Bowen <br/> | Microsoft 365 saklama veya saklama ve silme eylemine sahip olan bir bekletme etiketi, posta kutusunda en az bir öğeye uygulanır  <br/> |Özellik `ComplianceTagHoldApplied` , öğenin `True` koruma veya koruma etiketiyle etiketlenmiş olduğunu gösterir.  <br/><br/> Ayrıca özellik, `InPlaceHolds` etkin olmayan posta kutusuna Microsoft 365 bekletme etiketi ilkesi GUID'lerini de içerir.  <br/><br/> Daha fazla bilgi için bkz [. Klasöre veya öğeye bekletme etiketi uygulandığı için tanımlayıcı posta kutuları saklamayı belirleme](identify-a-hold-on-an-exchange-online-mailbox.md#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item) <br/>  |
|Ayrıca Necaise  <br/> |Kuruluş genelinde Microsoft 365 bekletme ilkesi ilk Microsoft 365 uyumluluk merkezi  <br/> |Özellik  `InPlaceHolds`  boştur ve `LitigationHoldEnabled` böyledir `False` `ComplianceTagHoldApplied` `False`. Bu, etkin olmayan posta kutusunun devralınan kuruluşa Microsoft 365 bekletme ilkelerinin bir veya birden çok (Exchange) konumunun tamamına uygulandığını gösterir. <br/><br/> Daha fazla bilgi için bkz [. Posta kutusuna kuruluş genelinde bir bekletme ilkesi uygulandığını onaylama](identify-a-hold-on-an-exchange-online-mailbox.md#how-to-confirm-that-an-organization-wide-retention-policy-is-applied-to-a-mailbox) <br/> |
|Abraham McMahon  <br/> |eBulma olay durumunda Microsoft 365 uyumluluk merkezi  <br/> |Özellik  `InPlaceHolds`  , etkin olmayan posta kutusuna yerleştirilen eBulma durumu GUID'sine sahip. Guid ön ek ile başladığından, bunun bir eBulma durumu olduğunu anlarız  `UniH` .  <br/><br/> Daha fazla bilgi için bkz. [eBulma 1](identify-a-hold-on-an-exchange-online-mailbox.md#ediscovery-holds). <br/> |
|Pilar Pinilla  <br/> |In-Place Tutun  <br/> |Özellik  `InPlaceHolds`  , etkin olmayan posta kutusuna In-Place Posta Kutusu'nun GUID'lerini içerir. Bunun bir Ön Ek In-Place olduğunu anlarız, çünkü GUID bir önekle başlamaz.  <br/><br/> **NOT**: 1 Ekim 2020'den sonra yerinde tutma süresi değiştirilemez. Yalnızca Etkin Olmayan Posta In-Place etkin olmayan posta kutusunun silinmesiyle sonuçlandıracak bir  Hold işlemini kaldırabilirsiniz. <br/><br/> Daha fazla bilgi için bkz. [Eski eKbulma araçlarının eski bir şekilde çalışma.](legacy-ediscovery-retirement.md) <br/> |

## <a name="step-2-change-the-hold-duration-for-an-inactive-mailbox"></a>2. Adım: Etkin olmayan bir posta kutusunun kullanım süresini değiştirme

Etkin olmayan posta kutusunda ne tür bir  hold (ve birden çok  hold) olduğunu tanımdikten sonra, bir sonraki adım, tutma süresini değiştirmektir.  İşlem, uygulanan tutma türüne bağlı olarak değişir.

- [Microsoft 365 bekletme Microsoft 365 değiştirme](#change-the-duration-for-a-microsoft-365-retention-policy)

- [Yeni bir bekletme etiketinin Microsoft 365 değiştirme](#change-the-duration-for-a-microsoft-365-retention-label)

- [eBulma  Tutma süresini değiştirme](#change-the-duration-for-an-ediscovery-hold)

- [Mahkeme Tutma süresini değiştirme](#change-the-duration-for-a-litigation-hold)

- [2010 12 Saat In-Place değiştirme](#change-the-duration-for-an-in-place-hold)

### <a name="change-the-duration-for-a-microsoft-365-retention-policy"></a>Microsoft 365 bekletme Microsoft 365 değiştirme

Microsoft 365 bekletme ilkesi için bekletme süresini değiştirmek için, `Get-RetentionCompliancePolicy` önce Güvenlik ve Uyumluluk Merkezi PowerShell'de posta kutusunda bulunan özellikten ilişkili GUID `InPlaceHolds` ile çalıştırarak etkin olmayan posta kutusunu etkileyen ilkeyi tanımlamanız gerekir.

Bu komutu çalıştırarak GUID'den öneki ve soneki kaldıryın.  Örneğin, yukarıdaki örnek bilgileri kullanarak, `InPlaceHolds` `:3` `mbxcdbbb86ce60342489bff371876e7f224:3` `mbx` değerini alıp GUID değerini kaldırabilir ve bunun sonucunda bir ilke GUID değeri elde etmiş olursunuz.`cdbbb86ce60342489bff371876e7f224`  Bu örnekte, çalıştırmak istediğiniz yer:

```powershell
Get-RetentionCompliancePolicy cdbbb86ce60342489bff371876e7f224 | FL Name
```

İlkenin adını biliyorktan sonra, Uyumluluk Merkezi'nde bekletme Microsoft 365 değiştirebilirsiniz.  Bekletme ilkelerinin genellikle birden çok konuma uygulandığını unutmayın, bu nedenle ilkenin değiştirilmesi, hem etkin olmayan hem de etkin olmayan tüm konumları etkiler ve bu da bekletme dışında konumları Exchange.  Daha fazla bilgi için bkz [. Bekletme ilkeleri oluşturma ve yapılandırma](create-retention-policies.md).  

> [!IMPORTANT]
> Saklama kilidi [etkinleştirilmiş bekletme](retention-preservation-lock.md) ilkeleri bekletme süresi uzatılabilir, ancak azaltılamaz veya kaldırılamaz.

Bekletme dönemini yalnızca etkin olmayan posta kutuları veya yalnızca belirli etkin olmayan posta kutuları için değiştirmekse, Azure AD ve Exchange özniteliklerini ve özelliklerini kullanarak belirli posta [](retention.md#adaptive-or-static-policy-scopes-for-retention)kutularını veya etkin olmayan posta kutuları gibi posta kutularını tek tek hedef alan uyarlanabilir ilke kapsamlarını dağıtmayı düşünebilirsiniz.

### <a name="change-the-duration-for-a-microsoft-365-retention-label"></a>Yeni bir bekletme etiketinin Microsoft 365 değiştirme

Bekletme ilkelerinde olduğu gibi, Microsoft 365 bekletme etiketinin bekletme süresini değiştirirken, `Get-RetentionCompliancePolicy` önce Güvenlik ve Uyumluluk Merkezi PowerShell'de posta kutusunda bulunan özellikten ilişkili GUID `InPlaceHolds` ile çalıştırarak etkin olmayan posta kutusunun içeriğini etkileyen etiketi yayımlayan ilkeyi tanımlamanız gerekir.

Bu komutu çalıştırarak GUID'den öneki ve soneki kaldıryın.  Örneğin, yukarıdaki örnek bilgileri kullanarak, `InPlaceHolds` `:1` `mbx6fe063689d404a5bb9940eed0f0bf5d2:1` `mbx` değerini alıp GUID değerini kaldırabilir ve bunun sonucunda bir ilke GUID değeri elde etmiş olursunuz.`6fe063689d404a5bb9940eed0f0bf5d2`  Bu örnekte, çalıştırmak istediğiniz yer:

```powershell
Get-RetentionCompliancePolicy 6fe063689d404a5bb9940eed0f0bf5d2 | FL Name
```

İlkeyi tanım verdiktan sonra, hangi etiketlerin yayımlanmış olduğunu ve bu etiketlerin ayarlarını bilirsiniz.  Etiketler tek tek öğeler için geçerli olduğundan, ilkeyle ve ayarlarıyla yayımlanan etiket sayısına bağlı olarak, içeriği etkileyen etiketi doğrudan tanımlamanız mümkün olabilir.  

Her etiketin uygulandığı içeriği tanımlamak için kullanabileceğiniz bir yöntem, İçerik [Arama'dır](content-search.md).  Örneğin, yukarıdaki örnek bilgileri kullanarak, ilkenin biri "İk-İçerik" adlı birkaç etiket yayımla olduğunu varsayalım.  Doğru [izinlerle](microsoft-365-compliance-center-permissions.md), İçerik Arama, etkin olmayan posta kutusunun birincil SMTP`.``-AllowNotFoundExchangeLocationsEnabled $true` adresini (noktayla () önceden kaleme alınarak ve doğrulamayı atlamak için parametre belirterek Yeni Uyumluluklu [Arama PowerShell](/powershell/module/exchange/new-compliancesearch) komutuyla çalıştırabilirsiniz:

```powershell
New-ComplianceSearch -Name "MeganB Inactive Mailbox HR-Content Label Search" -ExchangeLocation .meganb@contoso.onmicrosoft.com -AllowNotFoundExchangeLocationsEnabled $true -ContentMatchQuery "compliancetag=HR-Content"
```

Arama oluşturulduktan sonra, aşağıdaki komutu kullanarak aramaya başlarsiniz:

```powershell
Start-ComplianceSearch "MeganB Inactive Mailbox HR-Content Label Search"
```

Bu yöntemi kullanarak, artık tanımlanan etiket ilkesinden etkin olmayan posta kutusunun içeriğine hangi etiketlerin uygulanıyor olduğunu tanımlayabilir ve böylelikle bekletme dönemlerini değiştirebilirsiniz. Bekletme etiketlerinin genellikle birden çok konuma uygulandığını ve bu nedenle etiketin değiştirilmesi, etiketli ve konumlar dışında konumlar ile içeriğin de dahil olduğu tüm konumları ve etiketli içeriği Exchange. Daha fazla bilgi için bkz [. Bekletme etiketleri oluşturma ve bunları uygulamalarda uygulama](create-apply-retention-labels.md).

> [!NOTE]
> Tüm bekletme etiketi türleri değiştirilemez.  Bazı etiketlerde yalnızca bekletme süresi artabilirken, bazıları için bekletme dönemini hiç değiştireyemesiniz.

### <a name="change-the-duration-for-an-ediscovery-hold"></a>eBulma  Tutma süresini değiştirme

eBulma servis servisleriyle ilişkilendirilmiş askıyaların süresi belirsizdir ve bu da değiştirilebilir bir tutma süresi yoktur. Öğeler sonsuza kadar veya tutma [kaldırılana ya da](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold) vaka kapatılana kadar tutulacak.
  
### <a name="change-the-duration-for-a-litigation-hold"></a>Mahkeme Tutma süresini değiştirme

Etkin olmayan bir Exchange Online posta kutusuna yerleştirilen mahkeme tutma süresini değiştirmek için Exchange Online PowerShell kullanabilirsiniz. EAC'i kullanaasiniz. Tutma süresini değiştirmek için aşağıdaki komutu çalıştırın. Bu örnekte, tutma süresi sınırsız süreyle değiştirilir:
  
```powershell
Set-Mailbox -InactiveMailbox -Identity <identity of inactive mailbox> -LitigationHoldDuration unlimited
```

Sonuç olarak, etkin olmayan posta kutusu öğelerinin süresiz olarak veya tutma kaldırılana ya da tutma süresi farklı bir değere değiştirilene kadar korunur.
  
> [!TIP]
> Etkin olmayan bir posta kutusunu belirlemenin en iyi yolu, Ayırt Edici Adını **veya** GUID **değerini Exchange kullanmaktır**. Bu değerlerden birini kullanmak, yanlışlıkla yanlış posta kutusunu belirtmeyi önlemeye yardımcı olur.

### <a name="change-the-duration-for-an-in-place-hold"></a>2010 12 Saat In-Place değiştirme

In-Place 10 Adedi kaldırıldı ve artık değiştirilemez. Etkin olmayan posta kutusuna In-Place  Hold uygulanmışsa, tutma süresini değiştiremezsiniz. Yalnızca Etkin Olmayan Posta In-Place kaldırabilirsiniz, bu durumda etkin olmayan posta kutusunun silinmesine neden olur. Daha fazla bilgi için bkz [. Etkin olmayan posta kutusunu silme](delete-an-inactive-mailbox.md#remove-in-place-holds).
  
## <a name="more-information"></a>Daha fazla bilgi

- **Etkin olmayan bir posta kutusunda bir öğe için tutma süresi nasıl hesaplanır?** Süre, bir posta kutusu öğesinin ilk alındıktan veya oluşturulduktan sonra hesaplanır.
    
- **Tutma süresi sona erdiğinde ne olur?** Kurtarılabilir Öğeler klasöründeki bir posta kutusu öğesinin tutma süresi dolduğunda, öğe etkin olmayan posta kutusundan kalıcı olarak silinir (temiz olur). Etkin olmayan posta kutusuna yerleştirilen tutma için hiçbir süre belirtilmezse, Kurtarılabilir Öğeler klasöründeki öğeler hiçbir zaman temizilmez (etkin olmayan posta kutusunun tutma süresi değişmezse). 
    
- **Etkin Exchange olmayan posta kutularında MRM ilkesi hala işleniyor mu?**  Bir MRM bekletme ilkesi posta kutusuna devre dışı gitmeden önce uygulanmışsa, tüm silme ilkeleri ( **Delete** eylemiyle yapılandırılmış MRM bekletme etiketleri) etkin olmayan posta kutusunda işlemeye devam eder. Bu, bekletme süresi sona erdiğinde MRM silme ilkesiyle etiketlenen öğelerin Kurtarılabilir Öğeler klasörüne taşınacak olduğu anlamına gelir. Bu öğeler, tutma süresi sona erdiğinde etkin olmayan posta kutusundan temiz olur. Etkin olmayan posta kutusu için bir tutma süresi belirtilmezse, Öğeleri Kurtar klasöründeki öğeler süresiz olarak korunur.

    Buna karşılık, etkin olmayan bir posta kutusuna atanmış MRM bekletme ilkesinde yer alan tüm arşiv ilkeleri ( **MoveToArchive** eylemiyle yapılandırılmış MRM bekletme etiketleri) yoksayılır. Bu, etkin olmayan ve arşiv ilkesiyle etiketlenen öğelerin bekletme süresi dolduğunda birincil posta kutusunda kalacakları anlamına gelir. Bu öğeler arşiv posta kutusuna veya arşiv posta kutusunda Kurtarılabilir Öğeler klasörüne taşınmaz. Bunlar süresiz olarak korunurlar.
    > [!NOTE]
    > Kullanıcı hesabı Exchange bekletme ilkesi (Exchange Online'te İleti Kayıtları Yönetimi veya MRM özelliği) uygulamak etkin olmayan bir posta kutusu oluşturmaz.

- **Normal posta kutularında olduğu gibi, Yönetilen Klasör Yardımcısı (MFA) etkin olmayan posta kutularını da işler.** Başka Exchange Online, MFA yaklaşık olarak yedi günde bir posta kutularını işler. Etkin olmayan bir posta kutusunun tutma süresini değiştirdikten sonra, etkin olmayan posta kutusunun yeni tutma süresini hemen işlemeye başlamak için **Start-ManagedFolderAssistant** cmdlet'ini kullanabilirsiniz. Aşağıdaki komutu çalıştırın. 

    ```powershell
    Start-ManagedFolderAssistant -InactiveMailbox <identity of inactive mailbox>
    ```
   
- **Etkin olmayan `InPlaceHolds` bir posta kutusuna çok sayıda kullanıcı yerleştirilirse, TUTMA GUID'lerinin hepsi görüntülenmez.** Etkin olmayan bir posta kutusuna yerleştirilen her şey için `InPlaceHolds` GUID'leri görüntülemek için aşağıdaki komutu çalıştırabilirsiniz.
    
    ```powershell
    Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | Select-Object -ExpandProperty InPlaceHolds
    ```
