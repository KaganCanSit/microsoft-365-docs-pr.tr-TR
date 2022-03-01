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
description: Etkin olmayan posta kutusunun içeriğini artık korumanız Microsoft 365, etkin olmayan posta kutusunu kalıcı olarak silebilirsiniz.
ms.openlocfilehash: 71223c0b5f53e03d51797e32f249f24146e96dee
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63009984"
---
# <a name="delete-an-inactive-mailbox"></a>Etkin olmayan posta kutusunu silme

Etkin olmayan posta kutusu, kuruluşdan ayrıldıktan sonra eski çalışanın e-postasını korumak için kullanılır. Artık etkin olmayan bir posta kutusunun içeriğini korumanız gerekmeyecektir, tutmayı kaldırarak etkin olmayan posta kutusunu kalıcı olarak silebilirsiniz. Aynı zamanda, etkin olmayan bir posta kutusuna birden çok 100 000 000 100 2013 yerleştirilebilirsiniz. Örneğin, etkin olmayan bir posta kutusu Mahkeme Tutma'ya ve bir veya birden çok Mahkeme 1 Veya Daha Fazla In-Place olabilir. Buna ek olarak, etkin olmayan posta kutusuna bir bekletme ilkesi (Office 365 veya Microsoft 365' güvenlik ve uyumluluk merkezinde oluşturulmuş olabilir). Etkin olmayan bir posta kutusunu silmek için, tüm bekletme ve bekletme ilkelerini kaldırmanız gerekir. Bekletme ve bekletme ilkelerini kaldırdikten sonra, etkin olmayan posta kutusu silinmek üzere işaretlenir ve işlendikten sonra kalıcı olarak silinir.
  
> [!IMPORTANT]
> Posta kutusu içeriğinin korunması için farklı yollar çalışmaya devam ettiyseniz In-Place, Exchange yönetim merkezinde Esnas'ın Esnad'ın da Exchange bulunmaktadır. Bu, etkin olmayan bir posta kutusu oluşturmak için Mahkeme Bekletmeleri ve bekletme ilkelerini kullanabileceğiniz anlamına gelir. 1 Temmuz 2020'den başlayarak, aynı In-Place 12 Exchange Online. Ancak etkin olmayan bir posta kutusuna yerleştirilen bir posta kutusunun In-Place tutma süresini değiştirebilirsiniz. Ancak, 1 Ekim 2020'den başlayarak, uzma süresini değiştiremezsiniz. Etkin olmayan posta kutusunu silmek için Yalnızca Etkin Değil olarak Tutma'ya In-Place gerekir. Tutmada olan ve etkin olmayan In-Place, tutma kaldırılana kadar korunur. Eski eBulma araçlarının eski In-Place [hakkında daha fazla bilgi için bkz. Eski eKbulma araçlarının emeklilik](legacy-ediscovery-retirement.md).
  
Etkin olmayan [bir posta](#more-information) kutusundan 1.000.000 ABD posta kutusu kaldırıldıktan sonra neler olduğunu açıklama için Daha fazla bilgi bölümüne bakın.
  
## <a name="before-you-delete-an-inactive-mailbox"></a>Etkin olmayan posta kutusunu smeden önce

- Etkin olmayan bir posta Exchange Online Mahkeme Tutma'ya kaldırmak için PowerShell'i kullanabilirsiniz. Exchange yönetim merkezini (EAC) kullanasınız. Adım adım yönergeler için bkz. [PowerShell'Bağlan Exchange Online kullanma](/powershell/exchange/connect-to-exchange-online-powershell).

- Etkin olmayan posta kutusunun içeriğini, tutmayı kaldırmadan ve etkin olmayan posta kutusunu smeden önce başka bir posta kutusuna kopyaabilirsiniz. Ayrıntılar için bkz. [Etkin olmayan posta kutusunu Şu posta kutusunda Office 365](restore-an-inactive-mailbox.md).

- Etkin olmayan bir posta kutusundan bekletme veya bekletme ilkesi kaldırırsanız ve posta kutusunun geçici olarak silinen posta kutusu bekletme süresi dolsa bile, 183 günlük geçici silinmiş posta kutusu bekletme süresi sona erdikten sonra posta kutusu kalıcı olarak silinir. Yumuşak silinmiş posta kutusu bekletme süresi hakkında daha fazla bilgi için, bu [makalenin Daha fazla](#more-information) bilgi bölümüne bakın. Etkin olmayan posta kutusu kalıcı olarak silindikten sonra, kurtarılamaz. Tutmayı kaldırmadan önce, posta kutusunun içeriğine artık ihtiyacınız kalmay olduğundan emin olun. Etkin olmayan bir posta kutusunu yeniden etkinleştirmek için, posta kutusunu kurtarabilirsiniz. Ayrıntılar için bkz. [Etkin olmayan posta kutusunu posta kutusunda Office 365](recover-an-inactive-mailbox.md).

- Etkin olmayan posta kutuları hakkında daha fazla bilgi için bkz[. Etkin olmayan posta kutuları hakkında bilgi.](inactive-mailboxes-in-office-365.md)

## <a name="step-1-identify-the-holds-on-an-inactive-mailbox"></a>1. Adım: Etkin olmayan bir posta kutusunda 1. Adım: Etkin olmayan posta kutusunda 1.

Daha önce de belirtildiği gibi, etkin olmayan bir In-Place posta kutusuna Mahkeme Tutma, Bekletme veya bekletme ilkesi yer alan bir ilke olabilir. İlk adım, etkin olmayan bir posta kutusunda 1.
  
Aşağıdaki komutu çalıştırarak, kurumda etkin olmayan tüm posta kutularının hold bilgilerini görüntülemeniz gerekir.
  
```powershell
Get-Mailbox -InactiveMailboxOnly | FL DisplayName,Name,IsInactiveMailbox,LitigationHoldEnabled,InPlaceHolds
```

**LitigationHoldEnabled** özelliği için **True** değeri, etkin olmayan posta kutusunun Mahkeme Tutmada olduğunu gösterir. Etkin In-Place olmayan bir posta kutusuna Yer Tutucu yerleştirilse, tutma GUID değeri **InPlaceHolds özelliğinin değeri olarak** görüntülenir. Örneğin, etkin olmayan iki posta kutusu için aşağıdaki sonuçlar, Ann Beebe'de Mahkeme Tutma ve Pilar Pinilla'ya In-Place bekletme ilkesi olduğunu gösterir.
  
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
> Çok fazla In-Place Bekletme veya bekletme ilkeleri etkin olmayan bir posta kutusuna yerleştirilirse, GUID Bekletme In-Place tutma ilkelerinin hepsi görüntülenmez. InPlaceHolds özelliğinde tüm GUID'leri görüntülemek için aşağıdaki komutu çalıştırabilirsiniz:  `Get-Mailbox -InactiveMailboxOnly -Identity <identity of inactive mailbox> | Select-Object -ExpandProperty InPlaceHolds`
  
Tutmaları tanımlama hakkında daha fazla bilgi için bkz [. Posta kutusuna yerleştirilen tutma türünü belirleme](identify-a-hold-on-an-exchange-online-mailbox.md).

## <a name="step-2-remove-a-hold-from-an-inactive-mailbox"></a>2. Adım: Etkin olmayan posta kutusundan  tutmayı kaldırma

Etkin olmayan posta kutusuna ne tür bir hold (ve birden çok 10 0 veya birden çok 100 01/16/ varsa) yerleştirildikten sonra, bir sonraki adım posta kutusunda 1. Daha önce de belirtildiği gibi, etkin olmayan bir posta kutusunu kalıcı olarak silmek için tüm 10.
  
### <a name="remove-a-litigation-hold"></a>Mahkeme Tutma kaldırma

Daha önce de belirtildiği gibi, etkin Windows PowerShell posta kutusundan Mahkeme Windows PowerShell'ı kaldırmanız gerekir. EAC'i kullanaasiniz. Mahkeme Tutma'ı kaldırmak için aşağıdaki komutu çalıştırın.
  
```powershell
Set-Mailbox -InactiveMailbox -Identity <identity of inactive mailbox> -LitigationHoldEnabled $false
```

> [!TIP]
> Etkin olmayan posta kutusunu belirlemenin en iyi yolu, Ayırt Edici Adını veya GUID değerini Exchange kullanmaktır. Bu değerlerden birini kullanmak, yanlışlıkla yanlış posta kutusunu belirtmeyi önlemeye yardımcı olur. 
  
### <a name="remove-an-inactive-mailbox-from-a-retention-policy"></a>Etkin olmayan posta kutusunu bekletme ilkesinden kaldırma

Etkin olmayan posta kutusunu bekletme ilkesinden kaldırma yordamı Microsoft 365 posta kutusuna atanan bekletme ilkesi kuruluş genelinde mi yoksa açık mı olduğuna bağlıdır. etkin olmayan posta kutusuna atanan bekletme ilkesi türünü seçin.

- Kuruluş genelinde, kuruluş genelinde tüm posta kutularına atanmış bekletme ilkeleri. Kuruluş **genelindeki bekletme ilkeleri hakkında** bilgi almak için Exchange Online PowerShell'de Get-OrganizationConfig cmdlet'ini kullanın.

- Belirli posta kutularına atanmış belirli konum bekletme ilkeleri. Bunlar, belirli kullanıcıların içerik konumlara atanan ilkelerdir. Belirli etkin olmayan posta kutularına atanmış bekletme ilkeleri hakkında bilgi almak için, Exchange Online PowerShell'de **Get-Mailbox -IncludeInactiveMailbox** cmdlet'ini kullanın.

#### <a name="remove-an-inactive-mailbox-from-an-organization-wide-retention-policy"></a>Kuruluş genelindeki bir bekletme ilkesinden etkin olmayan posta kutusunu kaldırma

Kuruluş genelindeki bir bekletme Exchange Online dışında tutmak için PowerShell'de aşağıdaki komutu çalıştırın.

```powershell
Set-Mailbox <identity of inactive mailbox> -ExcludeFromOrgHolds <retention policy GUID without prefix or suffix>
```

Etkin olmayan bir posta kutusuna uygulanan kuruluş genelinde bekletme ilkelerini tanımlama ve bekletme ilkesi IÇIN GUID alma hakkında daha fazla bilgi için Posta kutusuna yerleştirilen saklama türünü belirleme bölümündeki "Get-OrganizationConfig" bölümüne [bakın](identify-a-hold-on-an-exchange-online-mailbox.md#get-organizationconfig).

Alternatif olarak, etkin olmayan posta kutusunu kuruluş genelindeki tüm ilkelerden kaldırmak için aşağıdaki komutu çalıştırabilirsiniz:

```powershell
Set-Mailbox <identity of inactive mailbox> -ExcludeFromAllOrgHolds
```

#### <a name="remove-an-inactive-mailbox-from-a-specific-location-retention-policy"></a>Etkin olmayan posta kutusunu belirli bir konum bekletme ilkesinden kaldırma

Etkin olmayan posta kutusunu [açık bir bekletme & kaldırmak](/powershell/exchange/connect-to-scc-powershell) için Güvenlik ve Uyumluluk Merkezi PowerShell'de aşağıdaki komutu çalıştırın.

```powershell
Set-RetentionCompliancePolicy -Identity <retention policy GUID without prefix or suffix> -AddExchangeLocationException <identity of inactive mailbox>
```

Etkin olmayan bir posta kutusuna uygulanan belirli konum bekletme ilkelerini tanımlama ve bekletme ilkesi IÇIN GUID alma hakkında daha fazla bilgi için, Posta kutusuna yerleştirilen saklama türünü belirleme bölümündeki "Posta Kutusunu Al" bölümüne [bakın](identify-a-hold-on-an-exchange-online-mailbox.md#get-mailbox).

### <a name="remove-in-place-holds"></a>Geçerli In-Place kaldırma

 Etkin olmayan posta kutusundan bir In-Place kaldırmanın iki yolu vardır:
  
- **Seçili In-Place silme**. Kalıcı olarak silmek istediğiniz etkin olmayan posta kutusu, Geçici Tutma için tek kaynak posta In-Place ise, Yalnızca Tutma In-Place silebilirsiniz. 

    > [!NOTE]
    > Önceden basılı tutma nesnesini silemezsiniz ve In-Place devre dışı bırakabilirsiniz. Tutmanın etkin olduğu In-Place Bir Tutma nesnesini silmeyi denersanız, bir hata iletisi alırsınız. 
  
- **Etkin olmayan posta kutusunu, Etkin Tutma'nın kaynak posta In-Place kaldırın**. Bir ay süreyle diğer kaynak posta kutularını In-Place, etkin olmayan posta kutusunu kaynak posta kutuları listesinden kaldırabilir ve Etkin Değil In-Place tutabilirsiniz.

#### <a name="delete-an-in-place-hold"></a>Silme veya In-Place silme

1. Silmek istediğiniz  Tutma In-Place özelliklerini içeren bir değişken oluşturun. 1. In-Place: Etkin olmayan bir posta kutusunda 1. Adım: 1. Adım [:](#step-1-identify-the-holds-on-an-inactive-mailbox) Etkin olmayan posta kutusunda 1.

   ```powershell
   $InPlaceHold = Get-MailboxSearch -InPlaceHoldIdentity <In-Place Hold GUID>
   ```

2. Aynı Tutma sırasında tutma özelliğini In-Place.

   ```powershell
   Set-MailboxSearch $InPlaceHold.Name -InPlaceHoldEnabled $false
   ```

3. Onay In-Place silin.

   ```powershell
   Remove-MailboxSearch $InPlaceHold.Name
   ```

#### <a name="remove-an-inactive-mailbox-from-an-in-place-hold"></a>Etkin olmayan posta kutusunu 12 gün In-Place kaldırma

Bekleme In-Place çok fazla sayıda kaynak posta kutusu içeriyorsa, etkin olmayan posta kutusunun EAC'nin Kaynaklar sayfasında listelenmiyor olması mümkündür. Kaynaklar sayfasında bir 3.000'e kadar posta kutusu, bir  3.000 posta kutusunu In-Place görüntülenir. Kaynaklar sayfasında etkin olmayan bir posta kutusu listelenmiyorsa,  Exchange Online PowerShell kullanarak posta kutusunu Tutma In-Place kaldırabilirsiniz. 
  
1. Etkin olmayan posta kutusuna yerleştirilen  Hold In-Place özelliklerini içeren bir değişken oluşturun. 1. In-Place: Etkin olmayan bir posta kutusunda 1. Adım: 1. Adım [:](#step-1-identify-the-holds-on-an-inactive-mailbox) Etkin olmayan posta kutusunda 1.

    ```powershell
    $InPlaceHold = Get-MailboxSearch -InPlaceHoldIdentity <In-Place Hold GUID>
    ```

2. Etkin olmayan posta kutusunun, Etkin Olmayan Posta Kutusu için kaynak posta kutusu olarak liste In-Place doğrulayın. 

   ```powershell
   $InPlaceHold.Sources
   ```

   > [!NOTE]
   > Posta *Kutusu* 'In-Place Sources özelliği, kaynak posta kutularını *LegacyExchangeDN özellikleriyle* tanımlar. Bu özellik etkin olmayan posta kutularını benzersiz olarak tanım olduğundan, Hold özelliğinin *Kaynaklar* özelliğini kullanmak yanlış posta In-Place posta kutusunun kaldırılmasını engellemeye yardımcı olur. Bu, iki posta kutusunun aynı diğer adı veya SMTP adresine sahip olduğu sorunları önlemeye de yardımcı olur. 

3. Etkin olmayan posta kutusunu değişkende kaynak posta kutuları listesinden kaldırın. Önceki adımda komut tarafından döndürülen etkin olmayan posta kutusunun **LegacyExchangeDN'ini** kullanmaya dikkat edin. 

    ```powershell
    $InPlaceHold.Sources.Remove("<LegacyExchangeDN of the inactive mailbox>")
    ```

    Örneğin, aşağıdaki komut Pilar Pinilla için etkin olmayan posta kutusunu kaldırır.

    ```powershell
    $InPlaceHold.Sources.Remove("/o=contoso/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/ cn=9c8dfff651ec4908950f5df60cbbda06-pilarp")
    ```

4. Etkin olmayan posta kutusunun değişkende kaynak posta kutuları listesinden kaldırılmış olduğunu doğrulayın.

   ```powershell
   $InPlaceHold.Sources
   ```

5. Etkin In-Place olmayan kaynak posta kutularının güncelleştirilmiş listesiyle, Yer Tutma'da değişiklik.

   ```powershell
   Set-MailboxSearch $InPlaceHold.Name -SourceMailboxes $InPlaceHold.Sources
   ```

6. Etkin olmayan posta kutusunun, Etkin Olmayan Posta Kutusu için kaynak posta kutuları listesinden kaldır In-Place doğrulayın.

   ```powershell
   Get-MailboxSearch $InPlaceHold.Name | FL Sources
   ```

## <a name="more-information"></a>Daha fazla bilgi

- **Etkin olmayan posta kutusu, bir tür yumuşak silinmiş posta kutusudur.** Otomatik Exchange Online kutusu, silinmiş olan bir posta kutusudur ve bu posta kutusu silinmiştir, ancak belirli bir bekletme süresi içinde kurtarılabilir. Posta kutusu 30 gün içinde kurtarılabilir ve kalıcı olarak silinmiş olan posta kutuları için kullanılabilir. Etkin olmayan bir posta kutusu (posta kutusu silinmeden önce basılı durumda kalır), tutma kaldırılana kadar yumuşak silinmiş durumda kalır. Etkin olmayan bir posta kutusundan tutma kaldırıldıktan sonra, posta kutusu artık devre dışı durumda olmaz. Bunun yerine yazılım yazılıma göre silinir ve Exchange Online kaldırıldığı günden itibaren 183 gün boyunca orada kalır ve bu süre içinde kurtarılabilir. 183 gün sonra, geçici silinmiş bir posta kutusu kalıcı olarak silinmek üzere işaretlenir ve kurtarılamaz.

- **Etkin olmayan bir posta kutusunda  hold'i kaldırdikten sonra ne olur?** Posta kutusu diğer geçici silinmiş posta kutuları gibi kabul edilir ve 183 günlük geçici silinmiş posta kutusu bekletme süresinin sona erdikten sonra kalıcı olarak silinmek üzere işaretlenir. Bu bekletme süresi, etkin olmayan posta kutusundan saklamanın kaldırıldığı tarihte başlar. *InactiveMailboxRetireTime* özelliği, posta kutusu etkin değil durumdan (geçici silinmiş durumdayken) artık etkin olmadığı zaman (tutmadan geçici olarak silindiğinde) ayarlanır. Bu noktada, *InactiveMailboxRetireTime* özelliği geçişin meydana geldiği geçerli tarihe ayarlanır. *InactiveMailboxRetireTime* özellik kümesi olan posta kutularını arayabilecek bir yardımcı çalışır (*MailboxLifeCycle* assistant olarak adlandırılan). "InactiveMailboxRetireTime + 183 gün" geçerli tarihten küçükse, posta kutusunu temizler.

- **Etkin olmayan posta kutusu, tutma kaldırıldıktan hemen sonra kalıcı olarak silinir mi?** Önceden etkin olmayan bir posta kutusu 183 gün süreyle yumuşak silinmiş durumda kullanılabilir durumda olur. 183 gün sonra, posta kutusu kalıcı olarak silinmek üzere işaretlenir.

- **Tutma kaldırıldıktan sonra etkin olmayan posta kutusu hakkında bilgileri nasıl görüntülersiniz?** Tutma kaldırıldıktan ve etkin olmayan posta kutusu artık silinmiş bir posta kutusuna geri döndürüldikten sonra, **Get-Mailbox** cmdlet'iyle *InactiveMailboxOnly* parametresi kullanılarak döndürülemez. Ancak, **Get-Mailbox -SoftDeletedMailbox komutunu kullanarak posta kutusuyla ilgili bilgileri görüntüebilirsiniz** . Örneğin:

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

  Yukarıdaki örnekte, *WhenSoftDeleted* özelliği otomatik olarak silinen tarihi tanımlar ve bu örnekte bu tarih 16 Haziran 2020'dir. *WasInactiveMailbox özelliği* daha önce etkin olmayan `True` bir posta kutusu olduğu için listelenir. Posta kutusu, 30 Eylül 2020'den 183 gün sonra kalıcı olarak silinecek.
