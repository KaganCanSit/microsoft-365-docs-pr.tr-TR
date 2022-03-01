---
title: Exchange Online posta kutusuna yerleştirilen tutma Exchange Online tanımlama
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 6057daa8-6372-4e77-a636-7ea599a76128
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: E-posta kutunuzda, bir posta kutusuna yerleştirilen farklı Exchange Online belirlemeyi Microsoft 365.
ms.openlocfilehash: 0ad2a1a4479c2de667b23ee29ee321912e7d18e9
ms.sourcegitcommit: e3bff611439354e6339bb666a88682078f32ec13
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2022
ms.locfileid: "63014358"
---
# <a name="how-to-identify-the-type-of-hold-placed-on-an-exchange-online-mailbox"></a>Exchange Online posta kutusuna yerleştirilen tutma Exchange Online tanımlama

Bu makalede, posta kutularına yerleştirilen ve Exchange Online belirleme Microsoft 365.

Microsoft 365, kurumuz için posta kutusu içeriğinin kalıcı olarak silinmesini önleyen çeşitli yollar sunar. Bu sayede, kuruluş uyumluluk düzenlemelerine uygun olarak veya yasal ve diğer soruşturma türlerinde içerik bulundurabilirsiniz. İşte, 2013'te bekletme olarak da *adlandırılan* bekletme özelliklerinin Office 365:

- **[Mahkeme Tutma](create-a-litigation-hold.md):** Posta kutusunda kullanıcı posta kutularına uygulanan 10 Exchange Online.

- **[eBulma tutma](create-ediscovery-holds.md):** Güvenlik ve uyumluluk merkezinde Core eKbulma durumuyla ilişkilendirilmiş esnalar. eK bulma bulma, kullanıcı posta kutularına ve Microsoft 365 Grupları ve Posta Kutuları için ilgili posta Microsoft Teams.

- **[Yerinde Tutma](/Exchange/security-and-compliance/create-or-remove-in-place-holds):** In-Place yönetim merkezinin Exchange Yönetim Merkezi'nde bulunan In-Place e & Kbulma veya Yerinde Tutma aracı kullanılarak kullanıcı <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">posta</a> kutularına Exchange Online. 

   > [!NOTE]
   > In-Place 1 12,5 ay içinde kaldırıldı ve artık 10 12 In-Place Oluşturamaz veya posta kutularına uygulayamazsiniz. Öte In-Place, bu makalede yer alan posta kutularına yine De 10.000 12.000'de uygulanabilir. Daha fazla bilgi için bkz. [Eski eKbulma araçlarının eski bir şekilde çalışma.](legacy-ediscovery-retirement.md#in-place-ediscovery-and-in-place-holds-in-the-exchange-admin-center)

- **[Microsoft 365 bekletme](retention.md) ilkeleri:** Exchange Online'ta ve Microsoft 365 Grupları ve Grupları grupları için ilgili posta kutusunda bulunan kullanıcı posta kutularındaki içeriği korumak (veya alıkoyarak ve silmek) için Microsoft Teams. Ayrıca, kullanıcı posta kutularında depolanan konuşmaları Skype Kurumsal tutmak için bir bekletme ilkesi oluşturabilirsiniz.

  Posta kutularına Microsoft 365 iki tür bekletme ilkesi vardır.

    - **Belirli konum bekletme ilkeleri:** Bunlar, belirli kullanıcıların içerik konumlara atanan ilkelerdir. **PowerShell'de Get-Mailbox** cmdlet'ini Exchange Online posta kutularına atanan bekletme ilkeleri hakkında bilgi almak için kullanırsiniz. Bu tür bekletme ilkesi hakkında daha fazla bilgi için bekletme ilkesi belgelerinde [](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions) yer alan belirli eklemeleri veya dışlamaları olan bir ilke bölümüne bakın.

    - **Kuruluş genelinde bekletme ilkeleri:** Bunlar, kurum içinde tüm içerik konumlara atanan ilkelerdir. Kuruluş genelindeki bekletme ilkeleri hakkında bilgi almak için, Exchange Online PowerShell'de **Get-OrganizationConfig** cmdlet'ini kullanın. Bu tür bir bekletme ilkesi hakkında daha fazla bilgi için bekletme ilkesi belgelerinden tüm konumlara [uygulanan](retention-settings.md#a-policy-that-applies-to-entire-locations) ilkeler bölümüne bakın.

- **[Microsoft 365 bekletme etiketlerini değiştirme](retention.md):** Kullanıcı posta kutusunda herhangi bir klasöre veya öğeye bir Microsoft 365 bekletme etiketi (içeriği alıkoyacak veya içeriği alıkoyacak ve sonra da silen) için  yapılandırılan bir bekletme etiketi uygularsa, posta kutusu Mahkeme Tutma'ya yerleştirilmiş veya Microsoft 365 bekletme ilkesine atanmış gibi posta kutusu üzerinde bekletme yerleştirilir. Daha fazla bilgi için, bu [makalenin Klasör veya](#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item) öğeye bir bekletme etiketi uygulandığı için tanımlayıcı posta kutuları saklamaya devam ediyor bölümüne bakın.

Bekletmede posta kutularını yönetmek için, posta kutusuna yerleştirilen saklama türünü tanımlamanız gerekir; böylelikle bekletme süresini değiştirme, saklamayı geçici veya kalıcı olarak kaldırma ya da Microsoft 365 bekletme ilkesinden posta kutusunu dışlama gibi görevleri gerçekleştirebilirsiniz. Bu gibi durumlarda, ilk adım posta kutusuna yerleştirilen tutma türünü belirlemektir. Ayrıca, tek bir posta kutusuna birden çok 10 ayrı tutma (ve farklı türde tutma) yerleştirile bile, bir posta kutusuna yerleştirilen tüm  tutmaları tanımlamak için, bir posta kutusunda yer alan tüm tutmaları tanımlamanız gerekir.

## <a name="step-1-obtain-the-guid-for-holds-placed-on-a-mailbox"></a>1. Adım: Posta kutusuna yerleştirilen 1.

PowerShell'de, posta kutusuna yerleştirilen 00 Exchange Online GUID'sine sahip olmak için, PowerShell'de aşağıdaki iki cmdlet'i çalıştırabilirsiniz. GUID elde edindikten sonra, 2. Adım'daki belirli bir tutmayı tanımlamak için kullanırlar. Mahkeme Tutma, GUID tarafından tanım değil. Posta kutusunda Mahkeme Etkinleştirilmiş veya devre dışı bırakıldı.

- **Get-Mailbox:** Bu cmdlet'i kullanarak posta kutusu için Mahkeme Bekletme'nin etkinleştirildiğini ve özel olarak bir posta kutusuna atanmış eBulma bekletmeleri, In-Place Bekletmeleri ve Microsoft 365 bekletme ilkelerini almak için kullanın. Bu cmdlet'in çıkışı, posta kutusunun kuruluş genelindeki bir bekletme ilkesinden açıkça dışlanmış olup olduğunu da belirtir.

- **Get-OrganizationConfig:** Kuruluş genelindeki bekletme ilkeleri için GUID'leri almak üzere bu cmdlet'i kullanın.

Exchange Online PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online e bağlama](/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="get-mailbox"></a>Get-Mailbox

Bekletme hakkında bilgi almak ve posta kutusuna uygulanan bekletme Microsoft 365 için aşağıdaki komutu çalıştırın.

```powershell
Get-Mailbox <username> | FL LitigationHoldEnabled,InPlaceHolds
```

> [!TIP]
> InPlaceHolds özelliğinde çok fazla değer varsa ve bunların hepsi görüntülense de, `Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds` her GUID'nin ayrı bir satırda görüntülenebilir.

Aşağıdaki tabloda, Get-Mailbox cmdlet'ini çalıştırarak *InPlaceHolds* özelliğinde yer alan değerlere dayalı olarak farklı türde 00/ **000 000 00/000** -000 -000 -0a00 -0a00 -0001 -0a01-37555551178d açık almaktadır.

| Tutma türü                                                          | Örnek değer                                                                                  | Sılamı belirleme                                                                                                                                                                                                                                                                                                                     |
| ------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Mahkeme Tutma                                                    | `True`                                                                                         | *LitigationHoldEnabled* özelliği olarak ayarlanmış bir posta kutusu için Mahkeme Tutma etkinleştirilir`True`.                                                                                                                                                                                                                                         |
| eKbulma tutma                                                    | `UniH7d895d48-7e23-4a8d-8346-533c3beac15d`                                                     | *InPlaceHolds özelliği*, güvenlik ve uyumluluk merkezinde eKbulma durumuyla ilişkilendirilmiş herhangi bir tutma GUID'sini içerir. Bunun bir eBulma ayrımı olduğunu anlarısınız, çünkü GUID `UniH` ön ekle başlar (Bu, Birleşik Tutma'ya değerdir).                                                                                   |
| In-Place Tutun                                                      | `c0ba3ce811b6432a8751430937152491` <br/> veya <br/> `cld9c0a984ca74b457fbe4504bf7d3e00de`        | *InPlaceHolds* özelliği, posta kutusuna In-Place Yer Tutucu'nun GUID'sini içerir. Bunun bir Ön Ek In-Place, GUID bir önekle başlamay olduğundan veya ön ekle `cld` başladığından, bunu anlarız.                                                                                                               |
| Microsoft 365 posta kutusuna özel olarak uygulanmış bekletme ilkesi | `mbxcdbbb86ce60342489bff371876e7f224:1` <br/> veya <br/> `skp127d7cf1076947929bf136b7a2a8c36f:3` | InPlaceHolds özelliği, posta kutusuna uygulanan belirli konum bekletme ilkesi GUID'lerini içerir. GUID ön ek veya ön ek ile başladığından bekletme `mbx` ilkelerini tanımlayabilirsiniz `skp` . Ön `skp` ek, bekletme ilkesine kullanıcının posta Skype Kurumsal konuşmalara uygulandığını gösterir. |
| Kuruluş genelindeki bir veya daha fazla bekletme Microsoft 365 dışında bırakıldı  | `-mbxe9b52bf7ab3b46a286308ecb29624696`                                                         | Posta kutusu, kuruluş genelindeki bir Microsoft 365 bekletme ilkesi dışında tutulacaksa, posta kutusunun dışlanan bekletme ilkesine ait GUID InPlaceHolds özelliğinde görüntülenir ve önek tarafından `-mbx` tanımlanır.                                                                                                     |

### <a name="get-organizationconfig"></a>Get-OrganizationConfig
**Get-Mailbox** cmdlet'ini çalıştırsanız bile *InPlaceHolds* özelliği boşsa, posta kutusuna uygulanmış kuruluş genelinde Microsoft 365 ilkeler olabilir. Tüm kuruluş çapında [GUID'ler Exchange Online bekletme ilkeleri için PowerShell'de](/powershell/exchange/connect-to-exchange-online-powershell) aşağıdaki Microsoft 365 çalıştırın.

```powershell
Get-OrganizationConfig | FL InPlaceHolds
```

> [!TIP]
> InPlaceHolds özelliğinde çok fazla değer varsa ve bunların hepsi görüntülense de, `Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds` her GUID'nin ayrı bir satırda görüntülenebilir.

Aşağıdaki tabloda, kuruluş genelinde farklı türde 000 000 000 000 000 000 000 000 000 000 000 000 0000 (**Get-OrganizationConfig** cmdlet'ini çalıştırarak *InPlaceHolds* özelliğinde yer alan GUID bilgilerine dayalı olarak) nasıl tanımlan?

| Tutma türü                                                                                                | Örnek değer                           | Açıklama                                                                                                                                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------- | --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Microsoft 365 kutularına, ortak klasörlere Exchange sohbetlere Exchange bekletme Teams ilkeler uygulama | `mbx7cfb30345d454ac0a989ab3041051209:2` | Exchange posta kutularına, Exchange ortak klasörlere ve Microsoft Teams'da 1xN sohbetlere uygulanan kuruluş genelinde bekletme ilkeleri, ön ekle başlamakta olan GUID'ler tarafından `mbx` tanımlanır. Tek tek sohbet katılımcılarının posta kutusunda 1xN sohbetler depolanır.  |
| Microsoft 365 gruplarına ve kanal iletilerine Microsoft 365 bekletme Teams ilke uygulama                | `grp1a0a132ee8944501a4bb6a452ec31171:3` | E-posta gruplarına ve kanal Microsoft 365 uygulanan kuruluş genelinde bekletme Microsoft Teams, ön ekle Microsoft Teams GUID'ler tarafından `grp` tanımlanır. Not kanalı iletileri, bir Microsoft Ekibi ile ilişkilendirilmiş grup posta kutusunda saklanır. |

İlkelere uygulanan bekletme ilkeleri hakkında daha fazla bilgi Microsoft Teams bkz[.](retention-policies-teams.md) Microsoft Teams.

### <a name="understanding-the-format-of-the-inplaceholds-value-for-retention-policies"></a>Bekletme ilkeleri için InPlaceHolds değerinin biçimini anlama

InPlaceHolds özelliğinde bir öğeyi Microsoft 365 bekletme ilkesi olarak tanımlayan önek (mbx, skp veya grp) ek olarak, değer ilke için yapılandırılmış bekletme eylemi türünü tanımlayan bir sonek de içerir. Örneğin, aşağıdaki örneklerde eylem son eki kalın yazıyla vurgulanır:

   `skp127d7cf1076947929bf136b7a2a8c36f`**:1**

   `mbx7cfb30345d454ac0a989ab3041051209`**:2**

   `grp1a0a132ee8944501a4bb6a452ec31171`**:3**

Aşağıdaki tabloda üç olası bekletme eylemi tanımlar:

| Değer | Açıklama                                                                                                                          |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **1** | Bekletme ilkesinin öğeleri silmek üzere yapılandırıldığından emin olduğunu gösterir. İlke öğeleri korumaz.                                  |
| **2** | Bekletme ilkesinin öğeleri tutmak üzere yapılandırılanı gösterir. Bekletme süresi sona erdikten sonra ilke öğeleri silemez. |
| **3** | Bekletme ilkesi, bekletme süresi dolduktan sonra öğeleri tutmak ve sonra da silmek üzere yapılandırıldı.             |

Bekletme eylemleri hakkında daha fazla bilgi için İçeriği [belirli bir süre boyunca tutma bölümüne](retention-settings.md#retaining-content-for-a-specific-period-of-time) bakın.
   
## <a name="step-2-use-the-guid-to-identify-the-hold"></a>2. Adım: Guid'i kullanarak sılamı tanımlama

Posta kutusuna uygulanan bir tutma IÇIN GUID elde edindikten sonra, bir sonraki adım, guid'i kullanarak tutmayı tanımlamaktır. Aşağıdaki bölümlerde, GUID ayrımı GUID'lerini kullanarak tutma adını (ve diğer bilgileri) nasıl tanımlay adınız gösterebilirsiniz.

### <a name="ediscovery-holds"></a>eKbulma 1

Posta kutusuna uygulanan bir eBulma & tanımlamak için Güvenlik ve Uyumluluk Merkezi PowerShell'de aşağıdaki komutları çalıştırın. 1. Adımda tanımlanmamış eBulma ayrımı için GUID (UniH ön eki dahil değil) kullanın. 

Güvenlik ve Uyumluluk Merkezi PowerShell& e bağlanmak için bkz[. Bağlan ve Uyumluluk & PowerShell'e bağlanma](/powershell/exchange/connect-to-scc-powershell).

İlk komut, tutma hakkında bilgi içeren bir değişken oluşturur. Bu değişken diğer komutlarda kullanılır. İkinci komutta, tutmanın ilişkilendirilen eBulma büyük/harf adı görüntülenir. Üçüncü komut, tutma adını ve tutmanın geçerli olduğu posta kutularının listesini görüntüler.

```powershell
$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>
```

```powershell
Get-ComplianceCase $CaseHold.CaseId | FL Name
```

```powershell
$CaseHold | FL Name,ExchangeLocation
```

### <a name="in-place-holds"></a>In-Place 1.

PowerShell'de Exchange Online posta kutusuna In-Place  Hold komutunu tanımlamak için aşağıdaki komutu çalıştırın. 1. Adımda tanım In-Place Için GUID kullanın. Komutta, tutma adı ve tutma için geçerli olan posta kutularının listesi görüntülenir.

```powershell
Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL Name,SourceMailboxes
```

Bir önceki komutu In-Place GUID ön `cld` ekiyle başlıyorsa, önceki komutu çalıştırarak öneki de dahil etmek gerekir.

> [!IMPORTANT]
> Posta kutusu içeriğinin korunması için farklı yollar çalışmaya devam ettiyseniz, In-Place yönetim merkezinde (EAC) 19211'Exchange çalışmalarının geri Exchange bulunmaktadır. 1 Temmuz 2020'den başlayarak, aynı In-Place 12 Exchange Online. Ancak EAC'de veya In-Place PowerShell'de **Set-MailboxSearch** cmdlet'ini kullanarak Exchange Online yönetebilirsiniz. Ancak, 1 Ekim 2020'den başlayarak 1 Ekim 12013'te In-Place yönete In-Place yönete olmayacak. Bunları yalnızca EAC'de veya **Remove-MailboxSearch cmdlet'ini kullanarak** kaldırabilirsiniz. Eski eBulma araçlarının eski In-Place [hakkında daha fazla bilgi için bkz. Eski eKbulma araçlarının emeklilik](legacy-ediscovery-retirement.md).

### <a name="microsoft-365-retention-policies"></a>Microsoft 365 bekletme ilkeleri

[Bağlan için & Uyumluluk Merkezi PowerShell'e](/powershell/exchange/connect-to-scc-powershell) sürükleyin ve posta kutusuna uygulanan Microsoft 365 bekletme ilkesine (kuruluş genelinde veya belirli bir konuma) kimlik bilgileri sağlamak için aşağıdaki komutu çalıştırın. 1. Adım'da tanımtıklarını( mbx, skp, grp ön eki veya eylem soneki dahil değil) kullanın.

```powershell
Get-RetentionCompliancePolicy <hold GUID without prefix or suffix> -DistributionDetail  | FL Name,*Location
```

## <a name="identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item"></a>Klasöre veya öğeye bekletme etiketi uygulandığı için tanımlayıcı posta kutuları saklamaya devam ediyor

Kullanıcı, posta kutusunda içeriği tutmak veya tutmak ve silmek üzere yapılandırılan  bir bekletme  etiketi her ayarlamışsa, *ComplianceTagHoldApplied* posta kutusu özelliği **True olarak ayarlanır**. Bu durumda, posta kutusu bir Microsoft 365 bekletme ilkesine atanma ya da Mahkeme Tutma'ya yerleştirilma gibi saklama durumlarında olduğu gibi ele alınsa da benzer şekilde işlem gören bazı uyarılar içerir. *ComplianceTagHoldApplied özelliği* **True olarak ayarlanmamışsa**, aşağıdaki şeyler gerçekleşir:

- Posta kutusu veya kullanıcının posta kutusu Microsoft 365 hesabı silinirse, posta kutusu etkin olmayan bir [posta kutusuna olur](inactive-mailboxes-in-office-365.md).
- Posta kutusunu (birincil posta kutusu veya etkinse arşiv posta kutusu) devre dışı bırakasınız.
- Posta kutusundan silinmiş olan öğeler, etiketli olup olmadığını bağlı olarak iki yoldan birini izlemez:
    - **Etiketsiz öğeler,** posta kutusu için geçerli bir edat olmayan zaman, silinmiş öğelerin de geçerli olduğu yolu takip eder.  Bu öğelerin kalıcı olarak silinmesi için gereken süre, silinmiş öğe bekletme yapılandırmasına ve posta kutusu [](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#deleted-item-retention) için tek öğe kurtarmanın etkinleştirilme veya etkinleştirilmesine göre belirlenir.[](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#single-item-recovery)
    - **Etiketli öğeler**, ayrı ayrı öğe düzeyinde bir [](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#recoverable-items-folder) bekletme ilkesi uygulandığında olduğu gibi Microsoft 365 kurtarılabilir öğeler klasöründe korunur.  İçeriği farklı aralıklarla korumak veya tutmak ve silmek üzere yapılandırılmış  birden çok  öğenin farklı etiketleri varsa, her öğe uygulanan etiketin yapılandırmasına bağlı olarak korunur.
- eBulma bekletme Microsoft 365 bekletmeleri veya mahkeme tutma gibi diğer bekletmeler, etiketli öğelerin bekletme ilkelerine göre ne kadar süreyle [tutulacaklarını da uzatabilirsiniz](retention.md#the-principles-of-retention-or-what-takes-precedence).

Tek bir posta kutusunun *ComplianceTagHoldApplied* özelliğinin değerini görüntülemek için, [Exchange Online PowerShell'de çalıştırın](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Get-Mailbox <username> | FL ComplianceTagHoldApplied
```

Bekletme etiketleri hakkında daha fazla bilgi için bkz. [bekletme etiketleri](retention.md#retention-labels).

## <a name="managing-mailboxes-on-delay-hold"></a>Posta kutularını gecikmeli olarak yönetme

Posta kutusundan herhangi bir türde tutma kaldırıldıktan sonra, *gecikme süresi* uygulanır. Bu, verilerin posta kutusundan kalıcı olarak silinmesini (temizlemesini) önlemek için, gerçek tutma kaldırmanın 30 gün ertelenmiş olduğu anlamına gelir. Bu, yöneticilere, tutma kaldırıldıktan sonra temiz olacak posta kutusu öğelerini arama veya kurtarma fırsatı verir. Yönetilen Klasör Yardımcısı bu posta kutusunu bir sonraki kez işlemesi ve bir tutmanın kaldırılmış olduğunu algılaması için, posta kutusuna bir gecikme gecikmesi yerleştirilir. Özel olarak, Yönetilen Klasör Yardımcısı aşağıdaki posta kutusu özelliklerden birini True olarak ayarlarsa, posta kutusuna gecikme ayrımı **uygulanır**:

- **DelayHoldApplied:** Bu özellik, kullanıcının posta kutusunda depolanan e-postayla ilgili (Outlook ve Web üzerinde Outlook kullanan kişiler tarafından oluşturulan içerik) için geçerlidir.

- **DelayReleaseHoldApplied:** Bu özellik kullanıcının posta kutusunda depolanan bulut tabanlı içerik (Microsoft Teams, Microsoft Forms ve Microsoft Yammer gibi Outlook olmayan uygulamalar tarafından oluşturulmuş) için geçerlidir. Microsoft uygulaması tarafından oluşturulan bulut verileri normalde kullanıcının posta kutusunda gizli bir klasörde depolanır.

Posta kutusuna gecikme süresi yerleştirilse (önceki özelliklerden biri **True** olarak ayarlanmışsa), posta kutusunun mahkeme nedeniyle tutma süresi boyunca olduğu kabul edilir. 30 gün sonra, gecikme nedeniyle tutma süresi dolar ve Microsoft 365, tutmanın kaldırılması için gecikme süresini (DelayHoldApplied veya DelayReleaseHoldApplied özelliğini **False** olarak ayararak) otomatik olarak kaldırmayı denecektir. Bu özelliklerden herhangi biri **False** olarak ayar kullandıktan sonra, posta kutusu Yönetilen Klasör Yardımcısı tarafından bir sonraki işlemde, kaldırma için işaretlenmiş ilgili öğeler temizlenir.

Posta kutusunun DelayHoldApplied ve DelayReleaseHoldApplied özelliklerinin değerlerini görüntülemek için, [Exchange Online PowerShell'de çalıştırın](/powershell/exchange/connect-to-exchange-online-powershell).

```powershell
Get-Mailbox <username> | FL *HoldApplied*
```

Süresi dolmadan önce gecikme süresini kaldırmak için, hangi özelliği değiştirmek istediğinize bağlı olarak Exchange Online PowerShell'de aşağıdaki komutlardan birini (veya her ikisini) çalıştırabilirsiniz:

```powershell
Set-Mailbox <username> -RemoveDelayHoldApplied
```

Veya

```powershell
Set-Mailbox <username> -RemoveDelayReleaseHoldApplied
```

*RemoveDelayHoldApplied* veya *RemoveDelayReleaseHoldApplied* parametrelerini kullanmak için Exchange Online'de Yasal Tutma rolüne atanmış olması gerekir. 

Etkin olmayan bir posta kutusunda gecikmeyi ertelemeyi kaldırmak için, PowerShell'de aşağıdaki Exchange Online çalıştırın:

```powershell
Set-Mailbox <DN or Exchange GUID> -InactiveMailbox -RemoveDelayHoldApplied
```

Veya

```powershell
Set-Mailbox <DN or Exchange GUID> -InactiveMailbox -RemoveDelayReleaseHoldApplied
```

> [!TIP]
> Önceki komutta etkin olmayan bir posta kutusunu belirtmenin en iyi yolu, Ayırt Edici Adı veya GUID değerini Exchange kullanmaktır. Bu değerlerden birini kullanmak, yanlışlıkla yanlış posta kutusunu belirtmeyi önlemeye yardımcı olur. 

Bu parametreleri gecikme tutulmalarını yönetmek için kullanma hakkında daha fazla bilgi için bkz. [Set-Mailbox](/powershell/module/exchange/set-mailbox).

Posta kutusunu gecikmeli tutarken yönetmeye devam etmek için aşağıdaki şeyleri unutmayın:

- DelayHoldApplied veya DelayReleaseHoldApplied özelliği **True** olarak ayarlanırsa ve bir posta kutusu (veya buna karşılık gelen kullanıcı hesabı) silinirse, posta kutusu etkin olmayan bir posta kutusuna olur. Bunun nedeni, her iki özellik de **True** olarak ayarlanırsa posta kutusunun orada olduğu kabul edilir ve bir posta kutusunun tutmadan silinmesi de etkin olmayan posta kutusuna neden olur. Posta kutusunu silmek ve etkin olmayan posta kutusu yapmak için, her iki özelliği de **Yanlış olarak ayarlamış olun**.

- Daha önce de belirtildiği gibi, GecikmeHoldApplied veya DelayReleaseHoldApplied özelliği True olarak ayarlanırsa posta kutusunun sınırsız bir süre boyunca basılı tutul olduğu kabul **edilir**. Bununla birlikte, bu posta kutusunun *tüm içeriğinin* korun korul olduğu anlamına da değildir. Bu, her özellik için ayarlanmış olan değere bağlıdır. Örneğin, posta kutusundan 10 dakika kaldırıldığı için her iki özelliğin de **True** olarak ayar olduğunu varsayalın. Ardından, yalnızca bulut verilerine uygulanan gecikme Outlook kaldırırsınız (*RemoveDelayReleaseHoldApplied parametresini kullanarak*). Yönetilen Klasör Yardımcısı posta kutusunu bir sonraki işlemde, kaldırma Outlook olmayan öğeler temizlenir. Kaldırma Outlook için işaretlenmiş hiçbir öğe temizlanmaz, çünkü DelayHoldApplied özelliği True olarak ayarlanmış **durumda olur**. Bunun tersi de doğru olabilir: DelayHoldApplied **False** olarak ve DelayReleaseHoldApplied true olarak ayarlanırsa **, kaldırma** için Outlook yalnızca kaldırma için işaretlenmiş öğeler temizlenir.

## <a name="how-to-confirm-that-an-organization-wide-retention-policy-is-applied-to-a-mailbox"></a>Posta kutusuna kuruluş genelinde bir bekletme ilkesi uygulandığını doğrulama

Kuruluş genelinde bir bekletme ilkesi bir posta kutusuna uygulandığında veya kaldırıldığı zaman, posta kutusu tanılama günlüklerinin dışarı aktarılmış olması, Exchange Online bekletme ilkesi'nin posta kutusuna gerçekten uygulandığında veya kaldırıldığına emin olamanıza yardımcı olabilir. Bu bilgileri görüntülemek için, önce [Exchange Online Powershell kullanarak Exchange Online gerekir](/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="obtain-the-guids-for-any-retention-policies-explicitly-applied-to-a-mailbox"></a>Posta kutusuna açıkça uygulanmış bekletme ilkelerinin GUID'lerini alma

```powershell
Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds
```

### <a name="obtain-the-guids-for-any-organization-wide-retention-policies-applied-to-mailboxes"></a>Posta kutularına uygulanan kuruluş genelindeki tüm bekletme ilkeleri için GUID'leri alma

```powershell
Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds
```

### <a name="get-the-mailbox-diagnostics-for-holdtracking"></a>HoldTracking için Posta Kutusu Tanılama'yı alın

İzleme Posta Kutusu Tanılama günlükleri, kullanıcı posta kutusuna uygulanan tutma geçmişini içerir.

```powershell
$ht = Export-MailboxDiagnosticLogs <username> -ComponentName HoldTracking
$ht.MailboxLog | Convertfrom-Json
```

### <a name="review-the-results-of-the-mailbox-diagnostics-logs"></a>Posta Kutusu Tanılama günlüklerinin sonuçlarını gözden geçirme

Önceki adımdan veri toplarsanız, sonuçta elde edilen veriler aşağıdakine benzer olabilir:

> **ed**`  : 0001-01-01T00:00:00.0000000`
>  **hid**` : mbx7cfb30345d454ac0a989ab3041051209:1`
>  **ht**`  : 4`
>  **lsd**` : 2020-03-23T18:24:37.1884606Z`
>  **işletim sistemi**` : 2020-03-23T18:24:37.1884606Z`

Tanılama günlüğünde listelenen önceki değerlerden her birini anlamanıza yardımcı olacak aşağıdaki tabloyu kullanın.

| Değer   | Açıklama |
|:------- |:----------- |
| **ed**  | Bekletme ilkesine devre dışı bırakılacak olan Bitiş tarihini gösterir. MinValue, ilkenin hala posta kutusuna atandığı anlamına gelir. |
| **hid** | Bekletme ilkesi GUID'lerini gösterir. Bu değer, posta kutusuna atanan açık veya kuruluş genelindeki bekletme ilkeleri için topladığı GUID değerleriyle ilişkili olacaktır.|
| **lsd** | Bekletme politikasının posta kutusuna atandığı tarih olan Son başlangıç tarihini gösterir.|
| **işletim sistemi** | Bekletme ilkesiyle ilgili ilk kayıtlı bilgilerin Exchange Başlangıç başlangıç tarihini gösterir. |
|||

Bir bekletme ilkesi artık posta kutusuna uygulanmazsa, içeriği temizlemeyi önlemek için kullanıcıya geçici bir gecikme süresi uygulanır. Gecikme nedeniyle tutma komutu çalıştırarak devre dışı bırakılabilir `Set-Mailbox -RemoveDelayHoldApplied` .

## <a name="next-steps"></a>Sonraki adımlar

Posta kutusuna uygulanan bekletmeyi tanımdikten sonra, bekletme süresini değiştirme, saklamayı geçici veya kalıcı olarak kaldırma ya da etkin olmayan posta kutusunu bekletme ilkesinden çıkarmak gibi Microsoft 365 gerçekleştirebilirsiniz. 1. Görevler ile ilgili görevleri gerçekleştirme hakkında daha fazla bilgi için, aşağıdaki konulardan birini bakın:

- Kuruluş genelindeki bir posta kutusunu bekletme ilkesinden dışlamak için Güvenlik [& Uyumluluk Merkezi PowerShell'de](/powershell/exchange/connect-to-scc-powershell) [Set-RetentionCompliancePolicy -Identity \<Policy Name> -AddExchangeLocationException \<user mailbox>](/powershell/module/exchange/set-retentioncompliancepolicy) Microsoft 365 çalıştırın. Bu komut yalnızca ExchangeLocation özelliğinin değeri eşit olduğu *bekletme ilkeleri* için kullanılabilir `All`.

- [Etkin olmayan posta kutusunun tutma süresini değiştirme](change-the-hold-duration-for-an-inactive-mailbox.md)

- [Etkin olmayan posta kutusunu silme](delete-an-inactive-mailbox.md)

- [Bulut tabanlı posta kutularının Kurtarılabilir Öğeler klasöründeki öğeleri silme](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md)
