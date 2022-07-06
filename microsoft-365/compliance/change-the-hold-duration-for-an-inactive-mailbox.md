---
title: Etkin olmayan posta kutusunun bekletme süresini değiştirme
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
description: bir Office 365 posta kutusu devre dışı bırakıldıktan sonra, etkin olmayan posta kutusuna atanan saklama veya Office 365 bekletme ilkesinin süresini değiştirin.
ms.openlocfilehash: 6fdb3993fd6b6503ab672a0c6465a394f3824c4b
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66628891"
---
# <a name="change-the-hold-duration-for-an-inactive-mailbox"></a>Etkin olmayan posta kutusunun bekletme süresini değiştirme

[Etkin olmayan posta kutusu](inactive-mailboxes-in-office-365.md), eski bir çalışanın e-postasını kuruluşunuzdan ayrıldıktan sonra tutmak için kullanılan posta kutusu durumudur. Microsoft 365 kullanıcı nesnesi silinmeden önce geçerli bir ayrı tutma uygulandığında bir posta kutusu devre dışı olur.  Aşağıdaki tür ayrı tutmalar, kullanıcı hesabı silinerek etkin olmayan bir posta kutusunun oluşturulmasını başlatır:

- Saklama veya saklama ve silme ayarlarıyla [Microsoft 365 bekletme ilkeleri ve etiketleri](retention.md)

- [eBulma](ediscovery.md) servis talebiyle ilişkili ayrı tutma

- [Dava Tutma](create-a-litigation-hold.md)

- Mevcut bir In-Place Ayrı Tutma.

> [!IMPORTANT]
> Yukarıdaki ayrı tutmalardan herhangi biri, Microsoft 365 kullanıcı hesabı silindiğinde posta kutusunun devre dışı kalması için zorlansa da, etkin olmayan posta kutularını proaktif olarak kullanmayı planlarken Microsoft 365 saklamayı kullanmanız kesinlikle önerilir.
>
> - eBulma tutmaları, yasal bir sorunla ilgili belirli, zamana bağlı servis talepleri için tasarlanmıştır. Bir noktada, büyük olasılıkla bir yasal dava sona erer ve servis talebiyle ilişkili tutmalar kaldırılır ve eBulma olayı kapatılır (veya silinir). Etkin olmayan posta kutusuna yerleştirilen bir ayrı tutma bir eBulma olayıyla ilişkilendirilirse ve ayrı tutma serbest bırakılırsa veya eBulma olayı kapatılır veya silinirse, etkin olmayan posta kutusu kalıcı olarak silinir.
>
> - Exchange yönetim merkezindeki In-Place Tutmalar artık kullanımdan kaldırılmıştır. 1 Temmuz 2020 itibarıyla yeni In-Place Tutmalar Exchange Online'da oluşturulamadı. 1 Ekim 2020 itibarıyla yerinde tutma süresi artık değiştirilemedi. In-Place Ayrı Tutma uygulanmış etkin olmayan posta kutuları yalnızca In-Place Ayrı Tutma kaldırılarak silinebilir. In-Place Ayrı Tutma'da bulunan etkin olmayan posta kutuları, ayrı tutma kaldırılana kadar korunmaya devam eder. In-Place Tutmaları kullanımdan kaldırma hakkında daha fazla bilgi için bkz. [Eski eKeşif araçlarının kullanımdan kaldırılması](legacy-ediscovery-retirement.md).
>
> - [Bir](create-a-litigation-hold.md) posta kutusunda içeriği tutmak ve kullanıcı hesabı silindikten sonra etkin olmayan hale getirmek için alternatif bir yöntem olarak dava tutma desteği devam eder. Ancak, eski bir teknoloji olarak bunun yerine Microsoft 365 saklama kullanmanızı öneririz.

Devre dışı bırakıldıktan sonra, [Kurtarılabilir Öğeler klasörü](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder) de dahil olmak üzere posta kutusunun içeriği, posta kutusu devre dışı bırakılmadan önce posta kutusuna yerleştirilen saklamaya kadar korunur.  

Geçerli ayrı tutma süresine bağlı değilse (örneğin, süresiz saklama yalnızca Microsoft 365 saklama ilkesi veya etiketiyle ilişkili ayrı tutma), bir eBulma olayı veya Dava Bekletmesi (yapılandırılmadan ```LitigationHoldDuration``` ), saklama kaldırılana kadar posta kutusu içeriği süresiz olarak korunur.  

Ancak, bekletme zamana bağlıysa, posta kutusu içeriği saklama süresi dolana kadar korunur ve bu noktada Kurtarılabilir Öğeler klasöründeki tüm öğeler etkin olmayan posta kutusundan kalıcı olarak silinir (temizlenir).

> [!NOTE]
> Etkin olmayan posta kutuları için Microsoft 365 bekletme ilkeniz veya etiketleriniz için bir saklama ve silme ayarı kullanmanızı öneririz.  Yalnızca saklama ayarını seçerseniz, Kurtarılabilir Öğeler klasörü saklama süresinin sonunda temizlenir, ancak diğer silinmeyen öğeler süresiz olarak etkin olmayan posta kutusunda kalır.

Düzenlemeler ve ilkeler geliştikçe, etkin olmayan posta kutusuna atanan saklama süresini değiştirmeniz gereken bazı durumlar olabilir.  Aşağıdaki adımlarda bunun nasıl yapılacağının ana hatlarıyla anlatılacaktır.

## <a name="connect-to-powershell"></a>PowerShell'e bağlanma

Daha önce de belirttiğimiz gibi, birçok farklı ayrı tutma türü etkin olmayan posta kutusunun oluşturulmasını tetikleyebilir.  Bu nedenle, etkin olmayan posta kutusuna uygulanan saklama süresini değiştirmek için önce hangi tür ayrı tutmaların onu etkilediğini belirlemeniz gerekir.  Bunu yapmak için Exchange Online PowerShell kullanarak ayrı tutma türlerini belirlemeniz ve etkin olmayan posta kutusunun Microsoft 365 bekletme ilkelerinden veya etiketlerinden etkilenmesi durumunda belirli ilkeleri tanımlamak için Güvenlik & Uyumluluk PowerShell'i de kullanmanız gerekir.

- Exchange Online PowerShell'e veya Güvenlik & Uyumluluğu PowerShell'e bağlanmak için aşağıdaki konulardan birine bakın:

  - [Exchange Online PowerShell’e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell)

  - [Güvenlik & Uyumluluğu PowerShell'e bağlanma](/powershell/exchange/connect-to-scc-powershell)

## <a name="step-1-identify-the-holds-on-an-inactive-mailbox"></a>1. Adım: Etkin olmayan posta kutusunda ayrı tutmaları belirleme

Etkin olmayan bir posta kutusuna farklı saklama türleri veya bir veya daha fazla Microsoft 365 bekletme ilkesi yerleştirilebileceği için, ilk adım etkin olmayan bir posta kutusunda ayrı tutmaları belirlemektir.
  
Kuruluşunuzdaki belirli bir etkin olmayan posta kutusunun saklama bilgilerini görüntülemek için Exchange Online PowerShell'de aşağıdaki komutu çalıştırın.
  
```powershell
Get-Mailbox -Identity <identity of inactive mailbox> -InactiveMailboxOnly | FL DisplayName,Name,DistinguishedName,ExchangeGuid,IsInactiveMailbox,LitigationHoldEnabled,LitigationHoldDuration,LitigationHoldDate,LitigationHoldOwner,InPlaceHolds,ComplianceTagHoldApplied
```

Birden çok etkin olmayan posta kutusu için ayrı tutma türünü belirlemeniz gerekiyorsa ve kuruluşunuzda çok sayıda ayrı tutma varsa, PowerShell kullanarak görüntülemek yönetilemez hale gelebilir. Bu durumda, aşağıdaki komutu kullanarak ve ortamınız için gereken şekilde değiştirerek ```Path``` tüm geçerli bilgileri bir CSV dosyasına aktarabilirsiniz:

```powershell
Get-Mailbox -InactiveMailboxOnly -ResultSize Unlimited | Select DisplayName,Name,DistinguishedName,ExchangeGuid,IsInactiveMailbox,LitigationHoldEnabled,LitigationHoldDuration,LitigationHoldDate,LitigationHoldOwner,InPlaceHolds,ComplianceTagHoldApplied | Export-Csv -NoTypeInformation -Path "C:\Temp\InactiveMailboxHoldTypes.csv"
```

Bu örneğin amaçları doğrultusunda, aşağıda farklı olası ayrı tutma türlerine sahip altı etkin olmayan posta kutusunun sonuçları gösterilmektedir.

> [!NOTE]
> Birden çok ayrı tutma türü de dahil olmak üzere birden çok ayrı tutma, tek bir etkin olmayan posta kutusuna uygulanabilir.
  
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

Aşağıdaki tabloda, her posta kutusunu yukarıdaki örnekten etkin olmayan hale getirmek için kullanılan altı farklı ayrı tutma türü tanımlanmıştır.
  
|**Etkin olmayan posta kutusu**|**Ayrı tutma türü**|**Etkin olmayan posta kutusunda bekletmeyi tanımlama**|
|:-----|:-----|:-----|
|Ann Beebe  <br/> |Dava Tutma  <br/> | `LitigationHoldEnabled` özelliği, posta kutusunun Dava Tutma'da olduğunu belirten olarak ayarlanır`True`. <br/><br/> Ayrıca, `LitigationHoldDuration` posta kutusu öğelerinin oluşturulma tarihinden (gönderildi/alındı) 365 gün sonra artık davaya tabi tutulmayacaklarını belirten olarak ayarlanır `365.00:00:00` .  <br/><br/> , `LitigationHoldDate` Dava Sahibi'nin etkinleştirildiği tarihi gösterir ve `LitigationHoldOwner` dava tutma işlemini başlatan kişiyi tanımlar. <br/> |
|Carol Olson  <br/> |Belirli posta kutularına uygulanan Microsoft Purview uyumluluk portalı Microsoft 365 bekletme ilkesi  <br/> |özelliği,  `InPlaceHolds`  etkin olmayan posta kutusuna uygulanan Microsoft 365 bekletme ilkesinin GUID'sini içerir. GUID ön ekiyle başlayıp veya `:3`ile sona erdiğinden, bunun belirli posta kutularına `mbx` uygulanan bir `:2` bekletme ilkesi olduğunu anlayabilirsiniz. <br/><br/> Daha fazla bilgi için bkz [. Bekletme ilkeleri için InPlaceHolds değerinin biçimini anlama](identify-a-hold-on-an-exchange-online-mailbox.md#understanding-the-format-of-the-inplaceholds-value-for-retention-policies).  <br/> |
|Megan Bowen <br/> | Posta kutusunda en az bir öğeye saklama veya saklama ve silme eylemi içeren Microsoft 365 bekletme etiketi uygulanır  <br/> |`ComplianceTagHoldApplied` özelliği, `True` bir öğenin bir saklama veya saklama ve silme etiketiyle etiketlendiğini belirtir.  <br/><br/> Ayrıca özelliği, `InPlaceHolds` etkin olmayan posta kutusuna uygulanan Microsoft 365 bekletme etiketi ilkesinin GUID'sini içerir.  <br/><br/> Daha fazla bilgi için bkz. Bir [klasöre veya öğeye bekletme etiketi uygulandığından, beklemedeki posta kutularını tanımlama](identify-a-hold-on-an-exchange-online-mailbox.md#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item) <br/>  |
|Mario Necaise  <br/> |Microsoft Purview uyumluluk portalı kuruluş genelinde Microsoft 365 saklama ilkesi <br/> |`InPlaceHolds` özelliği boş, `LitigationHoldEnabled` ve `False` `ComplianceTagHoldApplied` şeklindedir`False`. Bu durum, etkin olmayan posta kutusunun devraldığı kuruluşa bir veya daha fazla (Exchange) konum Microsoft 365 saklama ilkesi uygulandığını gösterir. <br/><br/> Daha fazla bilgi için bkz. [Kuruluş genelinde saklama ilkesinin posta kutusuna uygulandığını onaylama](identify-a-hold-on-an-exchange-online-mailbox.md#how-to-confirm-that-an-organization-wide-retention-policy-is-applied-to-a-mailbox) <br/> |
|Abraham McMahon  <br/> |Microsoft Purview uyumluluk portalı eBulma servis talebi saklama  <br/> |özelliği,  `InPlaceHolds`  etkin olmayan posta kutusuna yerleştirilen eBulma servis talebi saklamanın GUID'sini içerir. GUID ön ekiyle  `UniH` başladığından bunun bir eBulma servis talebi saklama işlemi olduğunu anlayabilirsiniz.  <br/><br/> Daha fazla bilgi için bkz. [eBulma tutmaları](identify-a-hold-on-an-exchange-online-mailbox.md#ediscovery-holds). <br/> |
|Pilar Pinilla  <br/> |In-Place Tutma  <br/> |özelliği,  `InPlaceHolds`  etkin olmayan posta kutusuna yerleştirilen In-Place Tutma guid'sini içerir. GUID bir ön ek ile başlamadığından bunun bir In-Place Ayrı Tutma olduğunu anlayabilirsiniz.  <br/><br/> **NOT**: 1 Ekim 2020 itibarıyla yerinde tutma süresi artık değiştirilemez. Yalnızca etkin olmayan posta kutusunun silinmesine neden olacak bir In-Place Ayrı Tutma'sını kaldırabilirsiniz. <br/><br/> Daha fazla bilgi için bkz [. Eski eBulma araçlarının kullanımdan kaldırılması](legacy-ediscovery-retirement.md). <br/> |

## <a name="step-2-change-the-hold-duration-for-an-inactive-mailbox"></a>2. Adım: Etkin olmayan posta kutusunun saklama süresini değiştirme

Etkin olmayan posta kutusuna ne tür bir ayrı tutma yerleştirildiğini (ve birden çok ayrı tutma olup olmadığını) belirledikten sonra, sonraki adım ayrı tutma süresini değiştirmektir.  İşlem, uygulanan ayrı tutma türüne bağlı olarak değişir.

- [Microsoft 365 bekletme ilkesinin süresini değiştirme](#change-the-duration-for-a-microsoft-365-retention-policy)

- [Microsoft 365 bekletme etiketinin süresini değiştirme](#change-the-duration-for-a-microsoft-365-retention-label)

- [eBulma Ayrı Tutma süresini değiştirme](#change-the-duration-for-an-ediscovery-hold)

- [Dava Tutma süresini değiştirme](#change-the-duration-for-a-litigation-hold)

- [In-Place Ayrı Tutma süresini değiştirme](#change-the-duration-for-an-in-place-hold)

### <a name="change-the-duration-for-a-microsoft-365-retention-policy"></a>Microsoft 365 bekletme ilkesinin süresini değiştirme

Microsoft 365 bekletme ilkesinin saklama süresini değiştirmek için, önce Güvenlik & Uyumluluk PowerShell'indeki posta kutusunda bulunan özelliğinden `InPlaceHolds` ilişkili GUID ile çalıştırarak `Get-RetentionCompliancePolicy` etkin olmayan posta kutusunu etkileyen ilkeyi tanımlamanız gerekir.

Bu komutu çalıştırırken GUID'den ön eki ve son eki kaldırdığınızdan emin olun.  Örneğin, yukarıdaki örnek bilgileri kullanarak öğesinin `InPlaceHolds` değerini `:3` `mbxcdbbb86ce60342489bff371876e7f224:3` `mbx` alır ve öğesinin ilke GUID'sine `cdbbb86ce60342489bff371876e7f224`neden olursunuz.  Bu örnekte şunları çalıştırmak istersiniz:

```powershell
Get-RetentionCompliancePolicy cdbbb86ce60342489bff371876e7f224 | FL Name
```

İlkenin adını bildiğinizde, Microsoft Purview uyumluluk portalı bekletme ilkesini değiştirebilirsiniz.  Bekletme ilkelerinin genellikle birden fazla konuma uygulandığını unutmayın, bu nedenle ilkenin değiştirilmesi hem etkin olmayan hem de etkin olan ve Exchange dışındaki konumları da içerebilen tüm uygulanan konumları etkiler.  Daha fazla bilgi için bkz. [Bekletme ilkeleri oluşturma ve yapılandırma](create-retention-policies.md).  

> [!IMPORTANT]
> [Koruma kilidi etkinleştirilmiş bekletme](retention-preservation-lock.md) ilkeleri saklama süresini uzatabilir, ancak azaltılmayabilir veya kaldırılmayabilir.

Amaç yalnızca etkin olmayan posta kutuları veya yalnızca belirli etkin olmayan posta kutuları için bekletme süresini değiştirmekse, Azure AD ve Exchange özniteliklerini ve özelliklerini kullanarak belirli posta kutularını veya etkin olmayan posta kutuları gibi posta kutusu türlerini tek tek hedeflemek için kullanılabilecek [uyarlamalı ilke kapsamları](retention.md#adaptive-or-static-policy-scopes-for-retention) dağıtmayı düşünebilirsiniz.

### <a name="change-the-duration-for-a-microsoft-365-retention-label"></a>Microsoft 365 bekletme etiketinin süresini değiştirme

Bekletme ilkelerinde olduğu gibi, bir Microsoft 365 bekletme etiketinin saklama süresini değiştirirken, önce Güvenlik & Uyumluluk PowerShell'de posta kutusunun özelliğinden `InPlaceHolds` ilişkili GUID ile çalıştırarak `Get-RetentionCompliancePolicy` etkin olmayan posta kutusu içindeki içeriği etkileyen etiketi yayımlayan ilkeyi tanımlamanız gerekir.

Bu komutu çalıştırırken GUID'den ön eki ve son eki kaldırdığınızdan emin olun.  Örneğin, yukarıdaki örnek bilgileri kullanarak öğesinin `InPlaceHolds` değerini `:1` `mbx6fe063689d404a5bb9940eed0f0bf5d2:1` `mbx` alır ve öğesinin ilke GUID'sine `6fe063689d404a5bb9940eed0f0bf5d2`neden olursunuz.  Bu örnekte şunları çalıştırmak istersiniz:

```powershell
Get-RetentionCompliancePolicy 6fe063689d404a5bb9940eed0f0bf5d2 | FL Name
```

İlkeyi belirledikten sonra, hangi etiketlerin yayımlandığını ve ayarlarını bilirsiniz.  Etiketler tek tek öğeler için geçerli olduğundan, ilkeyle yayımlanan etiketlerin sayısına ve ayarlarına bağlı olarak, içeriği etkileyen etiketi doğrudan belirleyemeyebilirsiniz.  

Her etiketin geçerli olduğu içeriği tanımlamak için kullanabileceğiniz yöntemlerden biri [İçerik Arama'yı](content-search.md) kullanmaktır.  Örneğin, yukarıdaki örnek bilgileri kullanarak ilkenin biri "HR-Content" olarak adlandırılan birkaç etiket yayımladığı varsayılır.  [Doğru izinlerle](microsoft-365-compliance-center-permissions.md), etkin olmayan posta kutusunun birincil SMTP adresi, önceden nokta ()`.``-AllowNotFoundExchangeLocationsEnabled $true` ile belirlenmiş ve doğrulamayı atlayan parametre belirterek [New-ComplianceSearch PowerShell komutuyla](/powershell/module/exchange/new-compliancesearch) bir İçerik Araması çalıştırılabilir:

```powershell
New-ComplianceSearch -Name "MeganB Inactive Mailbox HR-Content Label Search" -ExchangeLocation .meganb@contoso.onmicrosoft.com -AllowNotFoundExchangeLocationsEnabled $true -ContentMatchQuery "compliancetag=HR-Content"
```

Arama oluşturulduktan sonra, aşağıdaki komutu kullanarak aramayı başlatacaksınız:

```powershell
Start-ComplianceSearch "MeganB Inactive Mailbox HR-Content Label Search"
```

Bu yöntemi kullanarak, tanımlanan etiket ilkesinden hangi etiketlerin etkin olmayan posta kutusu içindeki içeriğe uygulanacağını belirleyebilir ve böylece bekletme sürelerini değiştirebilirsiniz. Bekletme etiketlerinin genellikle birden fazla konuma uygulandığını unutmayın, bu nedenle bir etiketin değiştirilmesi tüm uygulanan konumları ve etiketlenmiş içeriği etkiler ve bu da Exchange dışındaki konumları ve içeriği de içerebilir. Daha fazla bilgi için bkz. [Bekletme etiketlerini yayımlama ve bunları uygulamalarda uygulama](create-apply-retention-labels.md).

> [!NOTE]
> Tüm bekletme etiketi türleri değiştirilemez.  Bazı etiketler için yalnızca saklama süresini artırabilirsiniz ve diğerleri için bekletme süresini hiç değiştiremeyebilirsiniz.

### <a name="change-the-duration-for-an-ediscovery-hold"></a>eBulma Ayrı Tutma süresini değiştirme

eBulma servis talepleri ile ilişkili ayrı tutmalar süresiz tutmalardır; başka bir deyişle değiştirilebilen ayrı tutma süresi yoktur. Öğeler sonsuza kadar veya [ayrı tutma kaldırılana](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold) veya servis talebi kapatılana kadar tutulur.
  
### <a name="change-the-duration-for-a-litigation-hold"></a>Dava Tutma süresini değiştirme

Etkin olmayan bir posta kutusuna yerleştirilen Dava Tutma süresini değiştirmek için powershell Exchange Online kullanmanız gerekir. EAC'yi kullanamazsınız. Bekletme süresini değiştirmek için aşağıdaki komutu çalıştırın. Bu örnekte saklama süresi sınırsız bir süre olarak değiştirilmiştir:
  
```powershell
Set-Mailbox -InactiveMailbox -Identity <identity of inactive mailbox> -LitigationHoldDuration unlimited
```

Sonuç olarak, etkin olmayan posta kutusunda bulunan öğeler süresiz olarak veya ayrı tutma kaldırılana veya ayrı tutma süresi farklı bir değere değiştirilene kadar korunur.
  
> [!TIP]
> Etkin olmayan posta kutusunu tanımlamanın en iyi yolu **, Ayırt Edici Adı** veya **Exchange GUID** değerini kullanmaktır. Bu değerlerden birinin kullanılması yanlışlıkla yanlış posta kutusunun belirtilmesini önlemeye yardımcı olur.

### <a name="change-the-duration-for-an-in-place-hold"></a>In-Place Ayrı Tutma süresini değiştirme

In-Place Tutmalar kullanımdan kaldırıldı ve artık değiştirilemez. Etkin olmayan bir posta kutusuna In-Place Ayrı Tutma uygulanmışsa saklama süresini değiştiremezsiniz. Yalnızca In-Place Ayrı Tutma'yı kaldırabilirsiniz, bu da etkin olmayan posta kutusunun silinmesine neden olur. Daha fazla bilgi için bkz [. Etkin olmayan posta kutusunu silme](delete-an-inactive-mailbox.md#remove-in-place-holds).
  
## <a name="more-information"></a>Daha fazla bilgi

- **Etkin olmayan posta kutusunda bir öğe için ayrı tutma süresi nasıl hesaplanır?** Süre, bir posta kutusu öğesinin alındığı veya oluşturulduğu özgün tarihten hesaplanır.
    
- **Saklama süresi dolduğunda ne olur?** Kurtarılabilir Öğeler klasöründeki bir posta kutusu öğesi için saklama süresi dolduğunda, öğe etkin olmayan posta kutusundan kalıcı olarak silinir (temizlenir). Etkin olmayan posta kutusuna yerleştirilen saklama için belirtilen süre yoksa, Kurtarılabilir Öğeler klasöründeki öğeler hiçbir zaman temizlenmez (etkin olmayan posta kutusunun saklama süresi değiştirilmediği sürece). 
    
- **Exchange MRM ilkesi hala etkin olmayan posta kutularında işleniyor mu?**  Bir MRM bekletme ilkesi, devre dışı bırakılmadan önce posta kutusuna uygulandıysa, tüm silme ilkeleri ( **Silme** eylemiyle yapılandırılmış MRM bekletme etiketleri) etkin olmayan posta kutusunda işlenmeye devam eder. Bu, MRM silme ilkesiyle etiketlenmiş öğelerin saklama süresi dolduğunda Kurtarılabilir Öğeler klasörüne taşınacağı anlamına gelir. Saklama süresi dolduğunda bu öğeler etkin olmayan posta kutusundan temizlenir. Etkin olmayan posta kutusu için ayrı tutma süresi belirtilmezse, Öğeleri Kurtar klasöründeki öğeler süresiz olarak korunur.

    Buna karşılık, etkin olmayan bir posta kutusuna atanan MRM saklama ilkesine dahil edilen tüm arşiv ilkeleri ( **MoveToArchive** eylemiyle yapılandırılmış MRM bekletme etiketleri) yoksayılır. Bu, arşiv ilkesiyle etiketlenmiş etkin olmayan posta kutusunda bulunan öğelerin saklama süresi dolduğunda birincil posta kutusunda kaldığı anlamına gelir. Bunlar arşiv posta kutusuna veya arşiv posta kutusunda Kurtarılabilir Öğeler klasörüne taşınmaz. Süresiz olarak tutulacaklardır.
    > [!NOTE]
    > Kullanıcı hesabı silindiğinde Exchange bekletme ilkesi (Exchange Online'daki Microsoft Mesajlaşma Kayıt Yönetimi veya MRM özelliği) etkin olmayan bir posta kutusu oluşturmaz.

- **Normal posta kutularında olduğu gibi, Yönetilen Klasör Yardımcısı (MFA) etkin olmayan posta kutularını da işler.** Exchange Online'de MFA, posta kutularını yaklaşık olarak yedi günde bir işler. Etkin olmayan posta kutusunun saklama süresini değiştirdikten sonra, etkin olmayan posta kutusunun yeni saklama süresini hemen işlemeye başlamak için **Start-ManagedFolderAssistant** cmdlet'ini kullanabilirsiniz. Aşağıdaki komutu çalıştırın. 

    ```powershell
    Start-ManagedFolderAssistant -InactiveMailbox <identity of inactive mailbox>
    ```
   
- **Çok sayıda `InPlaceHolds` etkin olmayan posta kutusuna yerleştirilirse, tutma GUID'lerinin tümü görüntülenmez.** Etkin olmayan bir posta kutusuna yerleştirilen tüm `InPlaceHolds` GUID'leri görüntülemek için aşağıdaki komutu çalıştırabilirsiniz.
    
    ```powershell
    Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | Select-Object -ExpandProperty InPlaceHolds
    ```
