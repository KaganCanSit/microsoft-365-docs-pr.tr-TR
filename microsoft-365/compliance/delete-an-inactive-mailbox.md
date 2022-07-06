---
title: Etkin olmayan posta kutusunu silme
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: f5caf497-5e8d-4b7a-bfff-d02942f38150
ms.custom:
- seo-marvel-apr2020
description: Artık Microsoft 365 etkin olmayan posta kutusunun içeriğini korumanız gerekmediğinde, etkin olmayan posta kutusunu kalıcı olarak silebilirsiniz.
ms.openlocfilehash: a8bdd0cb98d744b6c64f651b7b7bb1754ff4f12e
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66634499"
---
# <a name="delete-an-inactive-mailbox"></a>Etkin olmayan posta kutusunu silme

Etkin olmayan posta kutusu, kuruluşunuzdan ayrılan eski bir çalışanın e-postasını korumak için kullanılır. Artık etkin olmayan posta kutusunun içeriğini korumanız gerekmediğinde, saklamayı kaldırarak etkin olmayan posta kutusunu kalıcı olarak silebilirsiniz. Ayrıca, etkin olmayan bir posta kutusuna birden çok ayrı tutma yerleştirilebilir. Örneğin, etkin olmayan bir posta kutusu Dava Tutma'ya ve bir veya daha fazla In-Place Ayrı Tutma'ya yerleştirilebilir. Ayrıca, microsoft 365 saklama etkin olmayan posta kutusuna uygulanabilir. Silmek için etkin olmayan bir posta kutusundan tüm saklama ve saklama ilkelerini kaldırmanız gerekir. Saklama ve saklama ilkelerini kaldırdıktan sonra, etkin olmayan posta kutusu silinmek üzere işaretlenir ve işlendikten sonra kalıcı olarak silinir.
  
> [!IMPORTANT]
> Posta kutusu içeriğini korumak için farklı yöntemlerle yatırım yapmaya devam ettikçe, Exchange yönetim merkezinde In-Place Tutmaların kullanımdan kaldırılıp kaldırılamını duyuruyoruz. Bu, etkin olmayan bir posta kutusu oluşturmak için Dava Tutmaları ve bekletme ilkelerini kullanmanız gerektiği anlamına gelir. 1 Temmuz 2020'den itibaren Exchange Online'da yeni In-Place Tutmaları oluşturamayacaksınız. Ancak, etkin olmayan bir posta kutusuna yerleştirilen In-Place Ayrı Tutmanın bekleme süresini de değiştirebilirsiniz. Ancak 1 Ekim 2020'den itibaren saklama süresini değiştiremezsiniz. Etkin olmayan bir posta kutusunu yalnızca In-Place Ayrı Tut'unu kaldırarak silebilirsiniz. In-Place Ayrı Tutma'da bulunan etkin olmayan posta kutuları, ayrı tutma kaldırılana kadar korunur. In-Place Tutmaların kullanımdan kaldırılması hakkında daha fazla bilgi için bkz. [Eski eKeşif araçlarının kullanımdan kaldırılması](legacy-ediscovery-retirement.md).
  
Etkin olmayan posta kutusundan ayrı tutmalar kaldırıldıktan sonra ne olacağının açıklaması için [Daha fazla bilgi](#more-information) bölümüne bakın.
  
## <a name="before-you-delete-an-inactive-mailbox"></a>Etkin olmayan posta kutusunu silmeden önce

- Etkin olmayan posta kutusundan ayrı tutmaları kaldırmak için powershell Exchange Online kullanmanız gerekir. Bu yordamlar için Exchange yönetim merkezini (EAC) veya Microsoft Purview uyumluluk portalı kullanamazsınız. Exchange Online PowerShell'i kullanmaya yönelik adım adım yönergeler için bkz. [PowerShell'Exchange Online bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

- Etkin olmayan bir posta kutusunun içeriğini başka bir posta kutusuna kopyalayarak saklamayı kaldırabilir ve etkin olmayan bir posta kutusunu silebilirsiniz. Ayrıntılar için bkz. [Office 365'da etkin olmayan posta kutusunu geri yükleme](restore-an-inactive-mailbox.md).

- Etkin olmayan bir posta kutusundan saklama veya saklama ilkesini kaldırırsanız ve posta kutusunun geçici olarak silinen posta kutusu saklama süresi dolduysa, 183 günlük geçici olarak silinen posta kutusu saklama süresi dolduktan sonra posta kutusu kalıcı olarak silinir. Geçici olarak silinen posta kutusu saklama süresi hakkında daha fazla bilgi için bu makalenin [Daha fazla bilgi](#more-information) bölümüne bakın. Etkin olmayan posta kutusu kalıcı olarak silindikten sonra kurtarılamaz. Ayrı tutmayı kaldırmadan önce, posta kutusunda artık içeriğine ihtiyacınız olmadığından emin olun. Etkin olmayan bir posta kutusunu yeniden etkinleştirmek istiyorsanız, posta kutusunu kurtarabilirsiniz. Ayrıntılar için bkz. [Office 365'da etkin olmayan posta kutusunu kurtarma](recover-an-inactive-mailbox.md).

- Etkin olmayan posta kutuları hakkında daha fazla bilgi için bkz. [Etkin olmayan posta kutuları hakkında bilgi edinin](inactive-mailboxes-in-office-365.md).

## <a name="step-1-identify-the-holds-on-an-inactive-mailbox"></a>1. Adım: Etkin olmayan posta kutusunda ayrı tutmaları belirleme

Daha önce belirtildiği gibi, etkin olmayan bir posta kutusuna Bir Dava Tutma, In-Place Saklama veya saklama ilkesi yerleştirilebilir. İlk adım, etkin olmayan bir posta kutusunda tutmaları belirlemektir.
  
[Exchange Online PowerShell'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell)ve ardından kuruluşunuzdaki tüm etkin olmayan posta kutularının saklama bilgilerini görüntülemek için aşağıdaki komutu çalıştırın.
  
```powershell
Get-Mailbox -InactiveMailboxOnly | FL DisplayName,Name,IsInactiveMailbox,LitigationHoldEnabled,InPlaceHolds
```

**LitigationHoldEnabled** özelliği için **True** değeri, etkin olmayan posta kutusunun Dava Tutma'da olduğunu gösterir. Etkin olmayan bir posta kutusuna bir In-Place Ayrı Tutma yerleştirilirse, bekletmenin GUID değeri **InPlaceHolds** özelliğinin değeri olarak görüntülenir. Örneğin, etkin olmayan iki posta kutusu için aşağıdaki sonuçlar, Ann Beebe'ye bir Dava Tutma'nın yerleştirildiğini ve Pilar Pinilla'ya bir In-Place Saklama ve saklama ilkesi yerleştirildiğini gösterir.
  
```text
DisplayName           : Ann Beebe
Name                  : annb
IsInactiveMailbox     : True
LitigationHoldEnabled : True
InPlaceHolds          : {}
...
DisplayName           : Pilar Pinilla
Name                  : pilarp
IsInactiveMailbox     : True
LitigationHoldEnabled : False
InPlaceHolds          : {c0ba3ce811b6432a8751430937152491, mbxba6f4ba25b62490aaaa253eea27426ab}
```

> [!TIP]
> Çok fazla In-Place Tutma veya saklama ilkesi etkin olmayan bir posta kutusuna yerleştirilirse, In-Place Tutma GUID'lerinin tümü görüntülenmez. InPlaceHolds özelliğindeki tüm GUID'leri görüntülemek için aşağıdaki komutu çalıştırabilirsiniz:  `Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | Select-Object -ExpandProperty InPlaceHolds`
  
Ayrı tutmaları tanımlama hakkında daha fazla bilgi için bkz. [Posta kutusuna yerleştirilen saklama türünü tanımlama](identify-a-hold-on-an-exchange-online-mailbox.md).

## <a name="step-2-remove-a-hold-from-an-inactive-mailbox"></a>2. Adım: Etkin olmayan posta kutusundan ayrı tutmayı kaldırma

Etkin olmayan posta kutusuna hangi tür ayrı tutmanın yerleştirildiğini (ve birden çok ayrı tutma olup olmadığını) belirledikten sonra, bir sonraki adım posta kutusu üzerindeki ayrı tutmaları kaldırmaktır. Daha önce belirtildiği gibi, etkin olmayan posta kutusunu kalıcı olarak silmek için tüm ayrı tutmaları kaldırmanız gerekir.
  
### <a name="remove-a-litigation-hold"></a>Dava Ayrı Tutmasını Kaldırma

Bir Dava Bekletmesini kaldırmak için aşağıdaki PowerShell komutunu çalıştırın.
  
```powershell
Set-Mailbox -InactiveMailbox -Identity <identity of inactive mailbox> -LitigationHoldEnabled $false
```

> [!TIP]
> Etkin olmayan posta kutusunu tanımlamanın en iyi yolu, Ayırt Edici Adı veya Exchange GUID değerini kullanmaktır. Bu değerlerden birinin kullanılması yanlışlıkla yanlış posta kutusunun belirtilmesini önlemeye yardımcı olur. 
  
### <a name="remove-an-inactive-mailbox-from-a-retention-policy"></a>Bekletme ilkesinden etkin olmayan posta kutusunu kaldırma

Etkin olmayan posta kutusunu Microsoft 365 bekletme ilkesinden kaldırma yordamı, etkin olmayan posta kutusuna atanan bekletme ilkesinin kuruluş genelinde mi yoksa açık mı olduğuna bağlıdır:

- Kuruluştaki tüm posta kutularına atanan kuruluş genelinde saklama ilkeleri. Kuruluş genelinde saklama ilkeleri hakkında bilgi almak için Exchange Online PowerShell'de **Get-OrganizationConfig** cmdlet'ini kullanın.

- Belirli posta kutularına atanan belirli konum saklama ilkeleri. Bunlar, belirli kullanıcıların içerik konumlarına atanan ilkelerdir. Belirli etkin olmayan posta kutularına atanan bekletme ilkeleri hakkında bilgi almak için Exchange Online PowerShell'de **Get-Mailbox -IncludeInactiveMailbox** cmdlet'ini kullanın.

#### <a name="remove-an-inactive-mailbox-from-an-organization-wide-retention-policy"></a>Kuruluş genelinde saklama ilkesinden etkin olmayan posta kutusunu kaldırma

Etkin olmayan bir posta kutusunu kuruluş genelinde saklama ilkesinden dışlamak için aşağıdaki PowerShell komutunu çalıştırın.

```powershell
Set-Mailbox <identity of inactive mailbox> -ExcludeFromOrgHolds <retention policy GUID without prefix or suffix>
```

Etkin olmayan bir posta kutusuna uygulanan kuruluş genelinde bekletme ilkelerini tanımlama ve bekletme ilkesinin GUID değerini alma hakkında daha fazla bilgi için, Posta kutusuna [yerleştirilen saklama türünü belirleme](identify-a-hold-on-an-exchange-online-mailbox.md#get-organizationconfig) bölümündeki "Get-OrganizationConfig" bölümüne bakın.

Alternatif olarak, etkin olmayan posta kutusunu kuruluş genelindeki tüm ilkelerden kaldırmak için aşağıdaki PowerShell komutunu çalıştırabilirsiniz:

```powershell
Set-Mailbox <identity of inactive mailbox> -ExcludeFromAllOrgHolds
```

#### <a name="remove-an-inactive-mailbox-from-a-specific-location-retention-policy"></a>Etkin olmayan posta kutusunu belirli bir konum saklama ilkesinden kaldırma

Açık saklama ilkesinden etkin olmayan posta kutusunu kaldırmak için [Güvenlik & Uyumluluğu PowerShell'i](/powershell/exchange/connect-to-scc-powershell) kullanın:

```powershell
Set-RetentionCompliancePolicy -Identity <retention policy GUID without prefix or suffix> -RemoveExchangeLocation <identity of inactive mailbox>
```

Etkin olmayan bir posta kutusuna uygulanan belirli konum bekletme ilkelerini tanımlama ve bekletme ilkesi için GUID alma hakkında daha fazla bilgi için, Posta kutusuna [yerleştirilen saklama türünü belirleme](identify-a-hold-on-an-exchange-online-mailbox.md#get-mailbox) konusundaki "Get-Mailbox" bölümüne bakın.

### <a name="remove-in-place-holds"></a>In-Place Ayrı Tutmalarını Kaldır

 Etkin olmayan bir posta kutusundan In-Place Ayrı Tutmayı kaldırmanın iki yolu vardır:
  
- **In-Place Tutma nesnesini silin**. Kalıcı olarak silmek istediğiniz etkin olmayan posta kutusu bir In-Place Ayrı Tutma için tek kaynak posta kutusuysa, In-Place Ayrı Tutma nesnesini silebilirsiniz. 

    > [!NOTE]
    > bir In-Place Ayrı Tutma nesnesini silmeden önce ayrı tutmayı devre dışı bırakmanız gerekir. Ayrı tutma etkin olan bir In-Place Ayrı Tutma nesnesini silmeye çalışırsanız bir hata iletisi alırsınız. 
  
- **Etkin olmayan posta kutusunu bir In-Place Ayrı Tutma'nın kaynak posta kutusu olarak kaldırın**. In-Place Ayrı Tutma için diğer kaynak posta kutularını korumak istiyorsanız, etkin olmayan posta kutusunu kaynak posta kutuları listesinden kaldırabilir ve In-Place Ayrı Tutma nesnesini tutabilirsiniz.

#### <a name="delete-an-in-place-hold"></a>In-Place Ayrı Tutma'sını silme

1. Silmek istediğiniz In-Place Ayrı Tutma özelliklerini içeren bir değişken oluşturun. [1. Adım: Etkin olmayan posta kutusunda tutmaları tanımlama](#step-1-identify-the-holds-on-an-inactive-mailbox) bölümünde elde ettiğiniz In-Place Tutma GUID'sini kullanın.

   ```powershell
   $InPlaceHold = Get-MailboxSearch -InPlaceHoldIdentity <In-Place Hold GUID>
   ```

2. In-Place Ayrı Tutma'da bekletmeyi devre dışı bırakın.

   ```powershell
   Set-MailboxSearch $InPlaceHold.Name -InPlaceHoldEnabled $false
   ```

3. In-Place Ayrı Tutmayı silin.

   ```powershell
   Remove-MailboxSearch $InPlaceHold.Name
   ```

#### <a name="remove-an-inactive-mailbox-from-an-in-place-hold"></a>Etkin olmayan posta kutusunu In-Place Ayrı Tutma'dan kaldırma

In-Place Ayrı Tutma çok sayıda kaynak posta kutusu içeriyorsa, etkin olmayan posta kutusu EAC'nin **Kaynaklar** sayfasında listelenmez. Bir In-Place Ayrı Tutma'yı düzenlediğinizde **Kaynaklar** sayfasında en fazla 3.000 posta kutusu görüntülenir. Etkin olmayan bir posta kutusu **Kaynaklar** sayfasında listelenmiyorsa, Exchange Online PowerShell'i kullanarak In-Place Ayrı Tutma'dan kaldırabilirsiniz. 
  
1. Etkin olmayan posta kutusuna yerleştirilen In-Place Ayrı Tutma özelliğini içeren bir değişken oluşturun. [1. Adım: Etkin olmayan posta kutusunda tutmaları tanımlama](#step-1-identify-the-holds-on-an-inactive-mailbox) bölümünde elde ettiğiniz In-Place Tutma GUID'sini kullanın.

    ```powershell
    $InPlaceHold = Get-MailboxSearch -InPlaceHoldIdentity <In-Place Hold GUID>
    ```

2. Etkin olmayan posta kutusunun In-Place Ayrı Tutma için kaynak posta kutusu olarak listelendiğini doğrulayın. 

   ```powershell
   $InPlaceHold.Sources
   ```

   > [!NOTE]
   > In-Place Ayrı Tutma özelliğinin *Sources* özelliği, kaynak posta kutularını *LegacyExchangeDN* özelliklerine göre tanımlar. Bu özellik etkin olmayan posta kutularını benzersiz olarak tanımladığından, In-Place Ayrı Tutma'dan *Sources* özelliğinin kullanılması yanlış posta kutusunun kaldırılmasını önlemeye yardımcı olur. Bu, iki posta kutusunun diğer adı veya SMTP adresi aynıysa sorunlardan kaçınmaya da yardımcı olur. 

3. Etkin olmayan posta kutusunu değişkendeki kaynak posta kutuları listesinden kaldırın. Önceki adımda komutu tarafından döndürülen etkin olmayan posta kutusunun **LegacyExchangeDN** değerini kullandığınızdan emin olun. 

    ```powershell
    $InPlaceHold.Sources.Remove("<LegacyExchangeDN of the inactive mailbox>")
    ```

    Örneğin, aşağıdaki komut Pilar Pinilla için etkin olmayan posta kutusunu kaldırır.

    ```powershell
    $InPlaceHold.Sources.Remove("/o=contoso/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/ cn=9c8dfff651ec4908950f5df60cbbda06-pilarp")
    ```

4. Etkin olmayan posta kutusunun değişkendeki kaynak posta kutuları listesinden kaldırıldığını doğrulayın.

   ```powershell
   $InPlaceHold.Sources
   ```

5. Etkin olmayan posta kutusunu içermeyen kaynak posta kutularının güncelleştirilmiş listesiyle In-Place Ayrı Tutma'yı değiştirin.

   ```powershell
   Set-MailboxSearch $InPlaceHold.Name -SourceMailboxes $InPlaceHold.Sources
   ```

6. Etkin olmayan posta kutusunun In-Place Ayrı Tutma için kaynak posta kutuları listesinden kaldırıldığını doğrulayın.

   ```powershell
   Get-MailboxSearch $InPlaceHold.Name | FL Sources
   ```

## <a name="more-information"></a>Daha fazla bilgi

- **Etkin olmayan posta kutusu, geçici olarak silinen bir posta kutusu türüdür.** Exchange Online'de, geçici olarak silinen posta kutusu silinmiş ancak belirli bir saklama süresi içinde kurtarılabilen bir posta kutusudur. Beklemede olmayan geçici olarak silinen posta kutuları için, posta kutusu 30 gün içinde kurtarılabilir. Etkin olmayan bir posta kutusu (silinmeden önce beklemede olan bir posta kutusu), bekletme kaldırılana kadar geçici olarak silinmiş durumda kalır. Etkin olmayan bir posta kutusundan ayrı tutma kaldırıldıktan sonra, posta kutusu artık etkin değil durumda olmaz. Bunun yerine geçici olarak silinir ve saklamanın kaldırıldığı günden itibaren 183 gün boyunca Exchange Online kalır ve bu süre boyunca kurtarılabilir. 183 gün sonra geçici olarak silinen bir posta kutusu kalıcı silme için işaretlenir ve kurtarılamaz.

- **Etkin olmayan bir posta kutusunda bekletmeyi kaldırdıktan sonra ne olur?** Posta kutusu, geçici olarak silinen diğer posta kutuları gibi değerlendirilir ve 183 günlük geçici olarak silinen posta kutusu saklama süresi dolduktan sonra kalıcı silme için işaretlenir. Bu saklama süresi, saklamanın etkin olmayan posta kutusundan kaldırıldığı tarihte başlar. *InactiveMailboxRetireTime* özelliği, posta kutusu etkin olmayan (beklemede geçici olarak silinmiş) olmaktan çıkarak artık etkin olmayan (ayrı tutma olmadan geçici olarak silinen) durumuna geçtiğinde ayarlanır. Bu noktada *, InactiveMailboxRetireTime* özelliği geçişin gerçekleştiği geçerli tarihe ayarlanır. *InactiveMailboxRetireTime* özelliği ayarlanmış posta kutularını arayan çalışan (*MailboxLifeCycle* yardımcısı olarak adlandırılır) bir yardımcı vardır. "InactiveMailboxRetireTime + 183 gün" geçerli tarihten küçükse, posta kutusunu temizler.

- **Etkin olmayan bir posta kutusu saklama kaldırıldıktan hemen sonra kalıcı olarak silinir mi?** Önceden etkin olmayan bir posta kutusu 183 gün boyunca geçici olarak silinmiş durumda kullanılabilir. 183 gün sonra posta kutusu kalıcı silme için işaretlenir.

- **Ayrı tutma kaldırıldıktan sonra etkin olmayan posta kutusu hakkındaki bilgileri nasıl görüntülersiniz?** Bekletme kaldırıldıktan ve etkin olmayan posta kutusu geçici olarak silinen bir posta kutusuna geri döndürüldükten sonra, **Get-Mailbox** *cmdlet'i ile InactiveMailboxOnly* parametresi kullanılarak döndürülemez. Ancak **, Get-Mailbox -SoftDeletedMailbox** komutunu kullanarak posta kutusu hakkındaki bilgileri görüntüleyebilirsiniz. Örneğin:

  ```text
  Get-Mailbox -SoftDeletedMailbox -Identity pilarp | FL Name,Identity,LitigationHoldEnabled,In
  Placeholds,WhenSoftDeleted,IsInactiveMailbox,WasInactiveMailbox,InactiveMailboxRetireTime
  Name                   : pilarp
  Identity               : Soft Deleted Objects\pilarp
  LitigationHoldEnabled  : False
  InPlaceHolds           : {}
  WhenSoftDeleted        : 6/16/2020 1:19:04 AM
  IsInactiveMailbox      : False
  WasInactiveMailbox     : True
  InactiveMailboxRetireTime : 9/30/2020 11:16:23 PM
  ```

  Yukarıdaki örnekte *WhenSoftDeleted* özelliği geçici silme tarihini tanımlar ve bu örnekte 16 Haziran 2020'dir. *WasInactiveMailbox* özelliği, daha önce etkin olmayan bir posta kutusu olduğundan olarak `True` listelenir. Posta kutusu 30 Eylül 2020 tarihinden 183 gün sonra kalıcı olarak silinir.
