---
title: Exchange Online posta kutusunda bekletmeyi tanımlama
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Microsoft 365'te bir Exchange Online posta kutusuna yerleştirilebilen farklı saklama türlerini tanımlamayı öğrenin.
ms.openlocfilehash: d7a174d267897f37fa113a51e138ec68def65b8a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638311"
---
# <a name="how-to-identify-the-type-of-hold-placed-on-an-exchange-online-mailbox"></a>Exchange Online posta kutusuna yerleştirilmiş saklama türünü tanımlama

Bu makalede, Microsoft 365'te Exchange Online posta kutularına yerleştirilmiş ayrı tutmaların nasıl belirlendiği açıklanır.

Microsoft 365, kuruluşunuzun posta kutusu içeriğinin kalıcı olarak silinmesini önleyebileceği çeşitli yollar sunar. Bu, kuruluşunuzun uyumluluk düzenlemelerini karşılamak için veya yasal ve diğer araştırma türleri sırasında içeriği saklamasına olanak tanır. Office 365 bekletme özelliklerinin (*ayrı tutma* olarak da adlandırılır) listesi aşağıda verilmiştir:

- **[Dava Tutma](create-a-litigation-hold.md):** Exchange Online kullanıcı posta kutularına uygulanan ayrı tutmalar.

- **[eBulma ayrı tutma](create-ediscovery-holds.md):** Güvenlik ve uyumluluk merkezindeki bir Microsoft Purview eKeşif (Standart) servis talebiyle ilişkili tutmalar. eBulma tutmaları, kullanıcı posta kutularına ve Microsoft 365 Grupları ve Microsoft Teams için ilgili posta kutusuna uygulanabilir.

- **[Yerinde Saklama](/Exchange/security-and-compliance/create-or-remove-in-place-holds):** Exchange Online'deki <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezindeki</a> In-Place eBulma & Ayrı Tutma aracı kullanılarak kullanıcı posta kutularına uygulanan ayrı tutmalar. 

   > [!NOTE]
   > In-Place Ayrı Tutmalar kullanımdan kaldırıldı ve artık In-Place Ayrı Tutmalar oluşturamıyor veya bunları posta kutularına uygulayamıyabilirsiniz. Ancak, In-Place Tutmalar kuruluşunuzdaki posta kutularına uygulanmaya devam edebilir. Bu nedenle bu makalede yer alır. Daha fazla bilgi için bkz [. Eski eBulma araçlarının kullanımdan kaldırılması](legacy-ediscovery-retirement.md#in-place-ediscovery-and-in-place-holds-in-the-exchange-admin-center).

- **[Microsoft 365 bekletme ilkeleri](retention.md):** Exchange Online ve Microsoft 365 Grupları ve Microsoft Teams için ilgili posta kutusunda bulunan kullanıcı posta kutularındaki içeriği saklayacak (veya saklayacak ve silecek) şekilde yapılandırılabilir. Kullanıcı posta kutularında depolanan Skype Kurumsal Konuşmalarını korumak için bir bekletme ilkesi de oluşturabilirsiniz.

  Posta kutularına atanabilecek iki tür Microsoft 365 bekletme ilkesi vardır.

    - **Belirli konum saklama ilkeleri:** Bunlar, belirli kullanıcıların içerik konumlarına atanan ilkelerdir. Belirli posta kutularına atanan bekletme ilkeleri hakkında bilgi almak için Exchange Online PowerShell'de **Get-Mailbox** cmdlet'ini kullanırsınız. Bu saklama ilkesi türü hakkında daha fazla bilgi için bekletme ilkesi belgelerindeki [belirli eklemeler veya dışlamalar içeren bir](retention-settings.md#a-policy-with-specific-inclusions-or-exclusions) ilke bölümüne bakın.

    - **Kuruluş genelinde saklama ilkeleri:** Bunlar, kuruluşunuzdaki tüm içerik konumlarına atanan ilkelerdir. Kuruluş genelinde saklama ilkeleri hakkında bilgi almak için PowerShell Exchange Online de **Get-OrganizationConfig** cmdlet'ini kullanırsınız. Bu saklama ilkesi türü hakkında daha fazla bilgi için bekletme ilkesi belgelerindeki [Konumların tamamı için geçerli olan](retention-settings.md#a-policy-that-applies-to-entire-locations) ilke bölümüne bakın.

- **[Microsoft 365 bekletme etiketleri](retention.md):** Kullanıcı, posta kutusundaki *herhangi* bir klasöre veya öğeye Microsoft 365 bekletme etiketi (içeriği saklamak veya saklamak ve silmek için yapılandırılmış bir etiket) uygularsa, posta kutusuna, posta kutusu Dava Tutma'ya yerleştirilmiş veya microsoft 365 saklama ilkesine atanmış gibi bir saklama yerleştirilir. Daha fazla bilgi için, bu makaledeki Bir [klasöre veya öğeye bekletme etiketi uygulandığından, beklemedeki posta kutularını tanımlama](#identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item) bölümüne bakın.

Ayrı tutmadaki posta kutularını yönetmek için, saklama süresini değiştirme, saklamayı geçici veya kalıcı olarak kaldırma ya da bir posta kutusunu Microsoft 365 bekletme ilkesinden dışlama gibi görevleri gerçekleştirebilmeniz için posta kutusuna yerleştirilen ayrı tutma türünü tanımlamanız gerekebilir. Bu gibi durumlarda ilk adım, posta kutusuna yerleştirilen saklama türünü belirlemektir. Tek bir posta kutusuna birden çok ayrı tutma (ve farklı ayrı tutma türleri) yerleştirilebildiği için, ayrı tutmayı kaldırmak veya değiştirmek istiyorsanız posta kutusuna yerleştirilen tüm ayrı tutmaları tanımlamanız gerekir.

## <a name="step-1-obtain-the-guid-for-holds-placed-on-a-mailbox"></a>1. Adım: Posta kutusuna yerleştirilen tutmalar için GUID alma

Exchange Online PowerShell'de aşağıdaki iki cmdlet'i çalıştırarak posta kutusuna yerleştirilen tutmaların GUID değerini alabilirsiniz. BIR GUID aldıktan sonra, 2. Adım'da belirli bir ayrı tutmayı tanımlamak için bunu kullanırsınız. Bir Dava Tutma guid tarafından tanımlanmaz. Dava Tutmaları bir posta kutusu için etkin veya devre dışıdır.

- **Get-Mailbox:** Bu cmdlet'i, bir posta kutusu için Dava Tutma'nın etkinleştirilip etkinleştirilmediğini belirlemek ve özellikle bir posta kutusuna atanmış eBulma tutmaları, In-Place Tutmalar ve Microsoft 365 bekletme ilkeleri için GUID'leri almak için kullanın. Bu cmdlet'in çıkışı, bir posta kutusunun kuruluş genelinde saklama ilkesinden açıkça dışlanmış olup olmadığını da gösterir.

- **Get-OrganizationConfig:** Kuruluş genelinde saklama ilkelerine yönelik GUID'leri almak için bu cmdlet'i kullanın.

Exchange Online PowerShell'e bağlanmak için bkz[. Exchange Online PowerShell'e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="get-mailbox"></a>Get-Mailbox

Bir posta kutusuna uygulanan saklamalar ve Microsoft 365 bekletme ilkeleri hakkında bilgi almak için aşağıdaki komutu çalıştırın.

```powershell
Get-Mailbox <username> | FL LitigationHoldEnabled,InPlaceHolds
```

> [!TIP]
> InPlaceHolds özelliğinde çok fazla değer varsa ve bunların tümü görüntülenmiyorsa, her GUID'yi `Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds` ayrı bir satırda görüntülemek için komutunu çalıştırabilirsiniz.

Aşağıdaki tabloda **, Get-Mailbox** *cmdlet'ini çalıştırdığınızda InPlaceHolds* özelliğindeki değerlere göre farklı türlerde ayrı tutmaların nasıl tanımlandığı açıklanmaktadır.

| Ayrı tutma türü                                                          | Örnek değer                                                                                  | Ayrı tutma nasıl tanımlanır?                                                                                                                                                                                                                                                                                                                     |
| ------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Dava Tutma                                                    | `True`                                                                                         | *LitigationHoldEnabled* özelliği olarak ayarlandığında`True`, bir posta kutusu için Dava Tutma etkinleştirilir.                                                                                                                                                                                                                                         |
| eBulma ayrı tutma                                                    | `UniH7d895d48-7e23-4a8d-8346-533c3beac15d`                                                     | *InPlaceHolds özelliği*, güvenlik ve uyumluluk merkezindeki bir eBulma olayıyla ilişkili tüm ayrı tutmaların GUID'sini içerir. BUNUN bir eBulma ayrılığı olduğunu anlayabilirsiniz çünkü GUID ön ekiyle `UniH` başlar (Birleştirilmiş Ayrı Tutmayı belirtir).                                                                                   |
| In-Place Tutma                                                      | `c0ba3ce811b6432a8751430937152491` <br/> veya <br/> `cld9c0a984ca74b457fbe4504bf7d3e00de`        | *InPlaceHolds* özelliği, posta kutusuna yerleştirilen In-Place Tutmanın GUID'sini içerir. GUID bir ön ek ile başlamadığından veya ön ek ile `cld` başladığından bunun bir In-Place Ayrı Tutma olduğunu anlayabilirsiniz.                                                                                                               |
| Posta kutusuna özel olarak uygulanan Microsoft 365 bekletme ilkesi | `mbxcdbbb86ce60342489bff371876e7f224:1` <br/> veya <br/> `skp127d7cf1076947929bf136b7a2a8c36f:3` | InPlaceHolds özelliği, posta kutusuna uygulanan belirli bir konum saklama ilkesinin GUID'lerini içerir. GUID veya `skp` ön eki ile `mbx` başladığından bekletme ilkelerini tanımlayabilirsiniz. Ön ek, `skp` bekletme ilkesinin kullanıcının posta kutusunda Skype Kurumsal konuşmalara uygulandığını gösterir. |
| Kuruluş genelinde microsoft 365 saklama ilkesinin dışında bırakıldı  | `-mbxe9b52bf7ab3b46a286308ecb29624696`                                                         | Bir posta kutusu kuruluş genelinde microsoft 365 bekletme ilkesi dışında bırakılırsa, posta kutusunun dışlandığı bekletme ilkesinin GUID'i InPlaceHolds özelliğinde görüntülenir ve ön ek ile `-mbx` tanımlanır.                                                                                                     |

### <a name="get-organizationconfig"></a>Get-OrganizationConfig
**Get-Mailbox** cmdlet'ini çalıştırdığınızda *InPlaceHolds* özelliği boşsa, posta kutusuna kuruluş genelinde bir veya daha fazla Microsoft 365 bekletme ilkesi uygulanmış olabilir. Exchange Online [PowerShell'de](/powershell/exchange/connect-to-exchange-online-powershell) aşağıdaki komutu çalıştırarak kuruluş genelindeki Microsoft 365 saklama ilkelerine yönelik GUID'lerin listesini alın.

```powershell
Get-OrganizationConfig | FL InPlaceHolds
```

> [!TIP]
> InPlaceHolds özelliğinde çok fazla değer varsa ve bunların tümü görüntülenmiyorsa, her GUID'yi `Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds` ayrı bir satırda görüntülemek için komutunu çalıştırabilirsiniz.

Aşağıdaki tabloda, **Get-OrganizationConfig** cmdlet'ini çalıştırdığınızda, kuruluş genelindeki farklı saklama türleri ve *Her türün InPlaceHolds* özelliğinde yer alan GUID'lere göre nasıl tanımlandığı açıklanmaktadır.

| Ayrı tutma türü                                                                                                | Örnek değer                           | Açıklama                                                                                                                                                                                                                                                            |
| -------------------------------------------------------------------------------------------------------- | --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Exchange posta kutularına, Exchange ortak klasörlerine ve Teams sohbetlerine uygulanan Microsoft 365 bekletme ilkeleri | `mbx7cfb30345d454ac0a989ab3041051209:2` | Microsoft Teams'de Exchange posta kutularına, Exchange ortak klasörlerine ve 1xN sohbetlerine uygulanan kuruluş genelinde bekletme ilkeleri, ön ekle `mbx` başlayan GUID'ler tarafından tanımlanır. Not 1xN sohbetleri, tek tek sohbet katılımcılarının posta kutusunda depolanır.  |
| Microsoft 365 Grupları ve Teams kanal iletilerine uygulanan Microsoft 365 bekletme ilkesi                | `grp1a0a132ee8944501a4bb6a452ec31171:3` | Microsoft Teams'de Microsoft 365 gruplarına ve kanal iletilerine uygulanan kuruluş genelinde saklama ilkeleri, ön ekle `grp` başlayan GUID'ler tarafından tanımlanır. Not kanalı iletileri, Bir Microsoft Ekibi ile ilişkili grup posta kutusunda depolanır. |

Microsoft Teams'e uygulanan bekletme ilkeleri hakkında daha fazla bilgi için bkz. [Microsoft Teams için bekletme ilkeleri hakkında bilgi edinin](retention-policies-teams.md).

### <a name="understanding-the-format-of-the-inplaceholds-value-for-retention-policies"></a>Bekletme ilkeleri için InPlaceHolds değerinin biçimini anlama

InPlaceHolds özelliğindeki bir öğeyi Microsoft 365 bekletme ilkesi olarak tanımlayan ön eke (mbx, skp veya grp) ek olarak, değer ilke için yapılandırılan bekletme eyleminin türünü tanımlayan bir sonek de içerir. Örneğin, eylem soneki aşağıdaki örneklerde kalın yazıyla vurgulanır:

   `skp127d7cf1076947929bf136b7a2a8c36f`**:1**

   `mbx7cfb30345d454ac0a989ab3041051209`**:2**

   `grp1a0a132ee8944501a4bb6a452ec31171`**:3**

Aşağıdaki tabloda üç olası bekletme eylemi tanımları yer alır:

| Değer | Açıklama                                                                                                                          |
| ----- | ------------------------------------------------------------------------------------------------------------------------------------ |
| **1** | Bekletme ilkesinin öğeleri silmek için yapılandırıldığını gösterir. İlke öğeleri saklamaz.                                  |
| **2** | Bekletme ilkesinin öğeleri barındıracak şekilde yapılandırıldığını gösterir. bekletme süresi dolduktan sonra ilke öğeleri silmez. |
| **3** | Bekletme ilkesinin öğeleri tutacak ve bekletme süresi dolduktan sonra bunları silecek şekilde yapılandırıldığını gösterir.             |

Bekletme eylemleri hakkında daha fazla bilgi [için İçeriği belirli bir süre boyunca saklama](retention-settings.md#retaining-content-for-a-specific-period-of-time) bölümüne bakın.
   
## <a name="step-2-use-the-guid-to-identify-the-hold"></a>2. Adım: Ayrı tutmayı tanımlamak için GUID kullanın

Bir posta kutusuna uygulanan ayrı tutmanın GUID'sini aldıktan sonra, sonraki adım bekletmeyi tanımlamak için bu GUID'yi kullanmaktır. Aşağıdaki bölümlerde, ayrı tutma GUID'sini kullanarak ayrı tutmanın adını (ve diğer bilgileri) nasıl tanımlayacakları gösterilir.

### <a name="ediscovery-holds"></a>eBulma tutmaları

Posta kutusuna uygulanan bir eBulma ayrı tutmasını belirlemek için Güvenlik & Uyumluluk PowerShell'de aşağıdaki komutları çalıştırın. 1. Adımda tanımladığınız eBulma ayrılığı için GUID'yi (UniH ön eki dahil değil) kullanın. 

Güvenlik & Uyumluluğu PowerShell'e bağlanmak için bkz. [Güvenlik & Uyumluluk PowerShell'e bağlanma](/powershell/exchange/connect-to-scc-powershell).

İlk komut, ayrı tutma hakkında bilgi içeren bir değişken oluşturur. Bu değişken diğer komutlarda kullanılır. İkinci komut, ayrı tutmanın ilişkili olduğu eBulma olayının adını görüntüler. Üçüncü komut, ayrı tutmanın adını ve ayrı tutmanın geçerli olduğu posta kutularının listesini görüntüler.

```powershell
$CaseHold = Get-CaseHoldPolicy <hold GUID without prefix>
```

```powershell
Get-ComplianceCase $CaseHold.CaseId | FL Name
```

```powershell
$CaseHold | FL Name,ExchangeLocation
```

### <a name="in-place-holds"></a>In-Place Ayrı Tutma

Exchange Online PowerShell'de aşağıdaki komutu çalıştırarak posta kutusuna uygulanan In-Place Bekletme'yi belirleyin. 1. Adımda tanımladığınız In-Place Ayrı Tutma için GUID kullanın. komut, ayrı tutmanın adını ve ayrı tutmanın geçerli olduğu posta kutularının listesini görüntüler.

```powershell
Get-MailboxSearch -InPlaceHoldIdentity <hold GUID> | FL Name,SourceMailboxes
```

In-Place Tutma guid'i ön ek ile `cld` başlıyorsa, önceki komutu çalıştırırken ön eki eklediğinizden emin olun.

> [!IMPORTANT]
> Posta kutusu içeriğini korumak için farklı yöntemlerle yatırım yapmaya devam ettikçe, Exchange yönetim merkezinde (EAC) In-Place Tutmaların kullanımdan kaldırılıp kaldırılamını duyuruyoruz. 1 Temmuz 2020'den itibaren Exchange Online'da yeni In-Place Tutmaları oluşturamayacaksınız. Ancak EAC'deki In-Place Tutmalarını yönetmeye veya powershell'Exchange Online **Set-MailboxSearch** cmdlet'ini kullanmaya devam edebilirsiniz. Ancak, 1 Ekim 2020'den itibaren In-Place Tutmaları yönetemezsiniz. Bunları yalnızca EAC'de veya **Remove-MailboxSearch** cmdlet'ini kullanarak kaldırabilirsiniz. In-Place Tutmaların kullanımdan kaldırılması hakkında daha fazla bilgi için bkz. [Eski eKeşif araçlarının kullanımdan kaldırılması](legacy-ediscovery-retirement.md).

### <a name="microsoft-365-retention-policies"></a>Microsoft 365 bekletme ilkeleri

[Güvenlik & Uyumluluğu PowerShell'e bağlanın](/powershell/exchange/connect-to-scc-powershell) ve posta kutusuna uygulanan Microsoft 365 bekletme ilkesini (kuruluş genelinde veya belirli bir konum) tanımlamak için aşağıdaki komutu çalıştırın. 1. Adımda tanımladığınız GUID'yi (mbx, skp, grp ön eki veya eylem soneki dahil değil) kullanın.

```powershell
Get-RetentionCompliancePolicy <hold GUID without prefix or suffix> -DistributionDetail  | FL Name,*Location
```

## <a name="identifying-mailboxes-on-hold-because-a-retention-label-has-been-applied-to-a-folder-or-item"></a>Bir klasöre veya öğeye bekletme etiketi uygulandığından, beklemedeki posta kutularını tanımlama

Kullanıcı, posta kutularındaki herhangi bir klasöre veya öğeye içerik *saklamak* veya *saklamak ve silmek* için yapılandırılmış bir bekletme etiketi uyguladığında *ComplianceTagHoldApplied* posta kutusu özelliği **True** olarak ayarlanır. Böyle bir durumda, posta kutusu bir Microsoft 365 saklama ilkesine atandığında veya Bazı uyarılar ile Dava Tutma'ya yerleştirildiğinde olduğu gibi beklemeye alındığında olduğu gibi değerlendirilir. *ComplianceTagHoldApplied* özelliği **True** olarak ayarlandığında aşağıdaki işlemler gerçekleşir:

- Posta kutusu veya kullanıcının Microsoft 365 hesabı silinirse, posta kutusu [etkin olmayan bir posta kutusuna](inactive-mailboxes-in-office-365.md) dönüşür.
- Posta kutusunu devre dışı bırakamazsınız (birincil posta kutusu veya etkinse arşiv posta kutusu).
- Posta kutusundan silinmiş öğeler etiketlenip etiketlenmediklerine bağlı olarak iki yoldan birini izler:
    - **Etiketsiz öğeler** , posta kutusuna hiçbir ayrı tutma uygulanmadığında silinmiş öğelerin izlediği yolu izler.  Bu öğelerin kalıcı olarak silinmesi için gereken süre, [silinen öğe saklama](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#deleted-item-retention) yapılandırmasına ve posta kutusu için [tek öğe kurtarmanın](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#single-item-recovery) etkinleştirilip etkinleştirilmediğine göre belirlenir.
    - **Etiketlenen öğeler** [kurtarılabilir öğeler klasöründe](/exchange/security-and-compliance/recoverable-items-folder/recoverable-items-folder#recoverable-items-folder) , Microsoft 365 bekletme ilkesi uygulandığında olduğu gibi, ancak tek tek öğe düzeyinde korunur.  Birden çok öğenin içeriği farklı aralıklarla *saklayacak* veya *saklayacak ve silecek* şekilde yapılandırılmış farklı etiketleri varsa, her öğe uygulanan etiketin yapılandırmasına göre korunur.
- Microsoft 365 saklama ilkeleri, eBulma saklama veya dava tutma gibi diğer tutmalar, etiketlenmiş öğelerin [saklama ilkelerine](retention.md#the-principles-of-retention-or-what-takes-precedence) göre ne kadar süreyle tutulabileceğini uzatabilir.

Tek bir posta kutusunun *ComplianceTagHoldApplied* özelliğinin değerini görüntülemek için [PowerShell Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell) de aşağıdaki komutu çalıştırın:

```powershell
Get-Mailbox <username> | FL ComplianceTagHoldApplied
```

Bekletme etiketleri hakkında daha fazla bilgi için bkz. [bekletme etiketleri](retention.md#retention-labels).

## <a name="managing-mailboxes-on-delay-hold"></a>Gecikmeli saklamada posta kutularını yönetme

Bir posta kutusundan herhangi bir tür ayrı tutma kaldırıldıktan sonra *bir gecikmeli saklama* uygulanır. Bu, verilerin posta kutusundan kalıcı olarak silinmesini (temizlenmesini) önlemek için saklama işleminin gerçek kaldırılmasının 30 gün ertelendiği anlamına gelir. Bu, yöneticilere ayrı tutma kaldırıldıktan sonra temizlenecek posta kutusu öğelerini arama veya kurtarma fırsatı verir. Yönetilen Klasör Yardımcısı posta kutusunu bir sonraki işlediğinde ve bir ayrı tutmanın kaldırıldığını algılayışında bir posta kutusuna gecikmeli saklama yerleştirilir. Özellikle, Yönetilen Klasör Yardımcısı aşağıdaki posta kutusu özelliklerinden birini **True** olarak belirlediğinde bir posta kutusuna gecikmeli saklama uygulanır:

- **DelayHoldApplied:** Bu özellik, kullanıcının posta kutusunda depolanan e-postayla ilgili içerik (Outlook ve Web üzerinde Outlook kullanan kişiler tarafından oluşturulur) için geçerlidir.

- **DelayReleaseHoldApplied:** Bu özellik, kullanıcının posta kutusunda depolanan bulut tabanlı içerik (Microsoft Teams, Microsoft Forms ve Microsoft Yammer gibi Outlook dışı uygulamalar tarafından oluşturulur) için geçerlidir. Microsoft uygulaması tarafından oluşturulan bulut verileri genellikle kullanıcının posta kutusunda gizli bir klasörde depolanır.

Posta kutusuna bir gecikmeli saklama yerleştirildiğinde (önceki özelliklerden biri **True** olarak ayarlandığında), posta kutusu, dava ayrı tutmadaymış gibi, sınırsız bir saklama süresi boyunca beklemede olarak kabul edilir. 30 gün sonra gecikme saklama süresi dolar ve Microsoft 365, bekletmenin kaldırılması için gecikme saklamayı (DelayHoldApplied veya DelayReleaseHoldApplied özelliğini **False** olarak ayarlayarak) otomatik olarak kaldırmaya çalışır. Bu özelliklerden biri **False** olarak ayarlandıktan sonra, posta kutusu Yönetilen Klasör Yardımcısı tarafından bir sonraki işlendiğinde, kaldırılmak üzere işaretlenmiş ilgili öğeler temizlenir.

Posta kutusunun DelayHoldApplied ve DelayReleaseHoldApplied özelliklerinin değerlerini görüntülemek için [PowerShell'Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell) aşağıdaki komutu çalıştırın.

```powershell
Get-Mailbox <username> | FL *HoldApplied*
```

Süresi dolmadan önce gecikmeli saklamayı kaldırmak için, değiştirmek istediğiniz özelliğe bağlı olarak PowerShell Exchange Online de aşağıdaki komutlardan birini (veya her ikisini) çalıştırabilirsiniz:

```powershell
Set-Mailbox <username> -RemoveDelayHoldApplied
```

Veya

```powershell
Set-Mailbox <username> -RemoveDelayReleaseHoldApplied
```

*RemoveDelayHoldApplied veya RemoveDelayReleaseHoldApplied* parametrelerini kullanmak için Exchange Online'da Yasal Tutma  rolüne atanmış olmanız gerekir. 

Etkin olmayan bir posta kutusunda gecikmeli saklamayı kaldırmak için PowerShell'Exchange Online aşağıdaki komutlardan birini çalıştırın:

```powershell
Set-Mailbox <DN or Exchange GUID> -InactiveMailbox -RemoveDelayHoldApplied
```

Veya

```powershell
Set-Mailbox <DN or Exchange GUID> -InactiveMailbox -RemoveDelayReleaseHoldApplied
```

> [!TIP]
> Önceki komutta etkin olmayan bir posta kutusu belirtmenin en iyi yolu, Ayırt Edici Ad veya Exchange GUID değerini kullanmaktır. Bu değerlerden birinin kullanılması yanlışlıkla yanlış posta kutusunun belirtilmesini önlemeye yardımcı olur. 

Gecikmeli tutmaları yönetmek için bu parametreleri kullanma hakkında daha fazla bilgi için bkz. [Set-Mailbox](/powershell/module/exchange/set-mailbox).

Gecikmeli beklemede bir posta kutusunu yönetirken aşağıdaki şeyleri göz önünde bulundurun:

- DelayHoldApplied veya DelayReleaseHoldApplied özelliği **True** olarak ayarlanırsa ve bir posta kutusu (veya ilgili kullanıcı hesabı) silinirse, posta kutusu etkin olmayan bir posta kutusuna dönüşür. Bunun nedeni, bir özelliğin **True** olarak ayarlanması durumunda posta kutusunun beklemede olarak kabul edilmesi ve beklemedeki bir posta kutusunun silinmesinin etkin olmayan bir posta kutusuna neden olmasıdır. Posta kutusunu silmek ve devre dışı posta kutusu yapmak için her iki özelliği de **False** olarak ayarlamanız gerekir.

- Daha önce belirtildiği gibi, DelayHoldApplied veya DelayReleaseHoldApplied özelliği **True** olarak ayarlandıysa, posta kutusu sınırsız ayrı tutma süresi boyunca ayrı tutulmuş olarak kabul edilir. Ancak bu, posta kutusundaki *tüm* içeriğin korunduğu anlamına gelmez. Her özelliğe ayarlanan değere bağlıdır. Örneğin, her iki özelliğin de posta kutusundan ayrı tutmalar kaldırıldığı için **True** olarak ayarlandığını düşünelim. Ardından yalnızca Outlook dışı bulut verilerine uygulanan gecikme bekletmesini kaldırırsınız ( *RemoveDelayReleaseHoldApplied* parametresini kullanarak). Yönetilen Klasör Yardımcısı posta kutusunu bir sonraki işlediğinde, kaldırılmak üzere işaretlenen Outlook dışı öğeler temizlenir. DelayHoldApplied özelliği hala **True** olarak ayarlandığından, kaldırılmak üzere işaretlenmiş tüm Outlook öğeleri temizlenmez. Tam tersi de doğru olacaktır: DelayHoldApplied **değeri False** ve DelayReleaseHoldApplied değeri **True** olarak ayarlanırsa, yalnızca kaldırılmak üzere işaretlenmiş Outlook öğeleri temizlenir.

## <a name="how-to-confirm-that-an-organization-wide-retention-policy-is-applied-to-a-mailbox"></a>Kuruluş genelinde saklama ilkesinin posta kutusuna uygulandığını onaylama

Bir posta kutusuna kuruluş genelinde bekletme ilkesi uygulandığında veya kaldırıldığında, posta kutusu tanılama günlüklerinin dışarı aktarılması, Exchange Online saklama ilkesini posta kutusuna gerçekten uyguladığından veya kaldırdığınızdan emin olmanıza yardımcı olabilir. Bu bilgileri görüntülemek için öncelikle [powershell Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell) kullanarak birkaç şeyi doğrulamanız gerekir.

### <a name="obtain-the-guids-for-any-retention-policies-explicitly-applied-to-a-mailbox"></a>Bir posta kutusuna açıkça uygulanan bekletme ilkeleri için GUID'leri alma

```powershell
Get-Mailbox <username> | Select-Object -ExpandProperty InPlaceHolds
```

### <a name="obtain-the-guids-for-any-organization-wide-retention-policies-applied-to-mailboxes"></a>Posta kutularına uygulanan kuruluş genelinde saklama ilkeleri için GUID'leri alma

```powershell
Get-OrganizationConfig | Select-Object -ExpandProperty InPlaceHolds
```

### <a name="get-the-mailbox-diagnostics-for-holdtracking"></a>HoldTracking için Posta Kutusu Tanılamasını Alma

Saklama İzleme Posta Kutusu Tanılama günlükleri, bir kullanıcı posta kutusuna uygulanan saklamaların geçmişini tutar.

```powershell
$ht = Export-MailboxDiagnosticLogs <username> -ComponentName HoldTracking
$ht.MailboxLog | Convertfrom-Json
```

### <a name="review-the-results-of-the-mailbox-diagnostics-logs"></a>Posta Kutusu Tanılama günlüklerinin sonuçlarını gözden geçirin

Önceki adımdan veri toplarsanız, sonuçta elde edilen veriler şuna benzer olabilir:

> **Ed**`  : 0001-01-01T00:00:00.0000000`
>  **Sakladı**` : mbx7cfb30345d454ac0a989ab3041051209:1`
>  **Ht**`  : 4`
>  **Lsd**` : 2020-03-23T18:24:37.1884606Z`
>  **Osd**` : 2020-03-23T18:24:37.1884606Z`

Tanılama günlüğünde listelenen önceki değerlerin her birini anlamanıza yardımcı olması için aşağıdaki tabloyu kullanın.

| Değer   | Açıklama |
|:------- |:----------- |
| **Ed**  | Saklama ilkesinin devre dışı bırakıldığı tarih olan Bitiş tarihini gösterir. MinValue, ilkenin posta kutusuna hala atandığı anlamına gelir. |
| **Sakladı** | Bekletme ilkesinin GUID'sini gösterir. Bu değer, posta kutusuna atanan açık veya kuruluş genelinde saklama ilkeleri için topladığınız GUID'lerle ilişkilendirilecektir.|
| **Lsd** | Saklama ilkesinin posta kutusuna atandığı tarih olan Son başlangıç tarihini gösterir.|
| **Osd** | Exchange'in bekletme ilkesiyle ilgili bilgileri ilk kaydettiği tarih olan Özgün başlangıç tarihini gösterir. |
|||

Bir saklama ilkesi artık bir posta kutusuna uygulanmadığında, içeriğin temizlenmesini önlemek için kullanıcıya geçici bir gecikmeli saklama uygularız. Komutu çalıştırarak `Set-Mailbox -RemoveDelayHoldApplied` gecikmeli saklama devre dışı bırakılabilir.

## <a name="next-steps"></a>Sonraki adımlar

Bir posta kutusuna uygulanan ayrı tutmaları belirledikten sonra, saklama süresini değiştirme, saklamayı geçici veya kalıcı olarak kaldırma ya da etkin olmayan bir posta kutusunu Microsoft 365 bekletme ilkesinden dışlama gibi görevleri gerçekleştirebilirsiniz. Ayrı tutmalarla ilgili görevleri gerçekleştirme hakkında daha fazla bilgi için aşağıdaki konulardan birine bakın:

- Güvenlik [& Uyumluluk PowerShell'de](/powershell/exchange/connect-to-scc-powershell) [Set-RetentionCompliancePolicy -Identity \<Policy Name> -AddExchangeLocationException \<user mailbox>](/powershell/module/exchange/set-retentioncompliancepolicy) komutunu çalıştırarak bir posta kutusunu kuruluş genelinde microsoft 365 bekletme ilkesinin dışında tutun. Bu komut yalnızca *ExchangeLocation* özelliğinin değerinin eşit `All`olduğu bekletme ilkeleri için kullanılabilir.

- [Etkin olmayan posta kutusunun bekletme süresini değiştirme](change-the-hold-duration-for-an-inactive-mailbox.md)

- [Etkin olmayan posta kutusunu silme](delete-an-inactive-mailbox.md)

- [Beklemedeki bulut tabanlı posta kutularının Kurtarılabilir Öğeler klasöründeki öğeleri silme](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md)
