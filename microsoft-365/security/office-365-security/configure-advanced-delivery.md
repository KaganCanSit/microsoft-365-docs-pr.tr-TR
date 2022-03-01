---
title: Kullanıcılara üçüncü taraf kimlik avı benzetimleri teslimi ve filtrelenmemiş iletileri SecOps posta kutularına yapılandırma
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Yöneticiler, belirli desteklenen senaryolarda (üçüncü taraf kimlik avı benzetimleri ve güvenlik işlemlerine (SecOps) teslim edilen iletilere filtre uygulamaması gereken iletileri tanımlamak için Exchange Online Protection'de (EOP) gelişmiş teslim politikasını kullanmayı öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bf564765b9bb896fcfcdac01961d414139199603
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021756"
---
# <a name="configure-the-delivery-of-third-party-phishing-simulations-to-users-and-unfiltered-messages-to-secops-mailboxes"></a>Kullanıcılara üçüncü taraf kimlik avı benzetimleri teslimi ve filtrelenmemiş iletileri SecOps posta kutularına yapılandırma

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

EOP[, varsayılan olarak](secure-by-default.md) organizasyon güvenliğinizi sağlamak için, Exchange Online Protection (EOP) kötü amaçlı yazılım veya yüksek güvenli kimlik avı olarak tanımlanan iletilerde güvenli listelere veya filtreleme atlamalarına izin vermez. Ancak, filtrelenmemiş iletilerin teslimi gereken belirli senaryolar vardır. Örneğin:

- **Üçüncü taraf kimlik avı benzetimleri**: Sanal saldırılar, gerçek bir saldırının organizasyonunu etkilemeden önce zayıf kullanıcıları tanımlamanıza yardımcı olur.
- **Güvenlik işlemleri (SecOps) posta kutuları**: Güvenlik ekipleri tarafından filtrelenmemiş iletileri (hem iyi hem de kötü) toplamak ve çözümlemek için kullanılan özel posta kutuları.

Bu belirli _senaryolarda gelen_ iletilerin filtre Microsoft 365 için gelişmiş _teslim_ Microsoft 365 kullanırsınız.<sup>\*</sup> Gelişmiş teslim ilkesi, bu senaryolarda iletilerin aşağıdaki sonuçları elde edene kadar elde  gerçekleştir:

- EOP ve Aşağıdakiler için Microsoft Defender Office 365 filtreler bu iletilerde hiçbir işlem uygulamaz.<sup>\*</sup>
- [İstenmeyen posta ve kimlik avı için sıfır saatlik temizleme (ZAP)](zero-hour-auto-purge.md) bu iletilerde hiçbir işlem olmaz.<sup>\*</sup>
- [Bu senaryolar](/microsoft-365/compliance/alert-policies#default-alert-policies) için varsayılan sistem uyarıları tetikli değildir.
- [Air and clustering in Defender for Office 365](office-365-air.md), bu iletileri yoksayar.
- Özel olarak üçüncü taraf kimlik avı benzetimleri için:
  - [Yönetici gönderileri](admin-submission.md) , iletinin bir kimlik avı benzetim kampanyasına parçası olduğunu ve gerçek bir tehdit olmadığını söyleyen otomatik bir yanıt oluşturuyor. Uyarılar ve AIR tetiklanmaz. Yönetici gönderimleri deneyimi, bu iletileri sanal bir tehdit olarak gösterir.
  - Bir kullanıcı Rapor İletisi veya Kimlik Avı Bildir eklentilerini kullanarak bir kimlik avı benzetimi iletisi bildirse [, sistem](enable-the-report-message-add-in.md) bir uyarı, araştırma veya olay oluşturmaz. Bağlantılar veya dosyalar deni bulunmayacak, ancak ileti Gönderimler sayfasının Kullanıcı tarafından bildirilen iletiler **sekmesinde de** görüntülenir.
  - [Kasa için Defender'daki Office 365](safe-links.md) Bağlantıları, bu iletilerde tıklama zamanında özel olarak tanımlanan URL'leri engellemez veya bu URL'leri engellemez. URL'ler yine kaydırılmış ancak engellenmiş değil.
  - [Kasa için Defender'daki Office 365](safe-attachments.md) ekleri bu iletilerde yer alan ekleri değil.

<sup>\*</sup> Kötü amaçlı yazılım filtrelemesini veya kötü amaçlı yazılım için ZAP'i atlayamabilirsiniz.

Gelişmiş teslim ilkesi tarafından tanımlanan iletiler güvenlik tehditlerine neden değildir; dolayısıyla iletiler sistem geçersiz kılmaları ile işaretlenir. Yönetici deneyimleri, kimlik avı benzetim sistemi geçersiz kılma veya  **SecOps** posta kutusu sistemi geçersiz kılma nedeniyle bu iletileri gösterir. Yöneticiler aşağıdaki deneyimlerde bu sistem geçersiz kılmalarını filtreleyen ve çözümleyen kullanıcılar olabilir:

- [Office 365 2. plan için Defender'da Tehdit Gezgini/](threat-explorer.md)Gerçek zamanlı algılamalar: Yönetici, Sistem geçersiz kılma kaynağına göre filtre uygulama ve Kimlik  avı benzetimi veya **SecOps Posta Kutusu'na filtre uygulama**.
- [Threat Explorer/Gerçek zamanlı algılamalarda E-posta](mdo-email-entity-page.md) varlığı Sayfası: Yönetici, Geçersiz **Kılmalar** bölümünde Kiracı geçersiz kılma'nın altında **SecOps** posta kutusu veya Kimlik  avı benzetimi yoluyla  kuruluş ilkesi tarafından izin verilen bir iletiyi görebilirsiniz.
- Tehdit [koruması durum raporu](view-email-security-reports.md#threat-protection-status-report): Yönetici, açılan menüde Sistem  geçersiz kılma'ya göre verileri görüntüye göre filtre uygulamalı ve kimlik avı benzetimi sistemi geçersiz kılma nedeniyle izin verilen iletileri görmek için öğesini seçebilirsiniz. SecOps posta kutusu geçersiz kılma tarafından izin verilen iletileri görmek için, grafik  çözümlemesinde neden açılan menüsünde teslim konumuna göre grafik **çözümlemesi** seçebilirsiniz.
- [Uç Nokta için Microsoft Defender'da](../defender-endpoint/advanced-hunting-overview.md) gelişmiş av: Kimlik avı benzetimi ve SecOps posta kutusu sistemi geçersiz kılmaları, EmailEvents'te OrgLevelPolicy'nin içinde seçenek olarak gösterir.
- [Kampanya Görünümleri](campaigns.md): Yönetici, Sistem geçersiz kılma kaynağına göre filtre kullanabilir **ve** Kimlik avı **benzetimi'ni** veya **SecOps Posta Kutusu'ni seçin**.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açın<https://security.microsoft.com>. Doğrudan Gelişmiş teslim **sayfasına gitmek için** , 'i açın <https://security.microsoft.com/advanceddelivery>.

- Güvenlik ve Uyumluluk Merkezi PowerShell& e bağlanmak için bkz[. Bağlan ve Uyumluluk & PowerShell'e bağlanma](/powershell/exchange/connect-to-scc-powershell).

- Bu makaledeki yordamları gerçekleştirmek için önce izinlerin atanmamış olması gerekir:
  - Gelişmiş teslim ilkesinde yapılandırılmış ayarları oluşturmak, değiştirmek veya kaldırmak için, **Microsoft 365 Defender portalında** Güvenlik Yöneticisi rol grubuna üye ve Exchange Online'te Kuruluş Yönetimi rol grubuna üye **Exchange Online**. 
  - Gelişmiş teslim ilkesine salt okunur erişim için, Genel Okuyucu veya Güvenlik Okuyucusu rol **gruplarının üyesi** olmak gerekir.

  Daha fazla bilgi için bkz. [Site portalında Microsoft 365 Defender ve](permissions-microsoft-365-security-center.md) [Site'deki Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  > İlgili kullanıcı rolüne kullanıcı Azure Active Directory, kullanıcılara portalda gerekli izinleri Microsoft 365 Defender bu portalda yer alan diğer özellikler  için Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).

## <a name="use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy"></a>Gelişmiş Microsoft 365 Defender ilkesinde SecOps posta kutularını yapılandırmak için Posta Kutusu portalını kullanın

1. aşağıdaki Microsoft 365 Defender portalında, <https://security.microsoft.com>Kurallar bölümünde, **E-posta &** \> İşbirliği **İlkeleri'& Kurallar** \>  \> tehdit **ilkeleri Gelişmiş** **teslim'e** gidin. Doğrudan Gelişmiş teslim **sayfasına gitmek için** , 'i kullanın <https://security.microsoft.com/advanceddelivery>.

2. Gelişmiş **teslim sayfasında** , **SecOps posta kutusu sekmesinin** seçili olduğunu doğrulayın ve aşağıdaki adımlardan birini uygulayın:
   - Düzenle simgesine ![tıklayın.](../../media/m365-cc-sc-edit-icon.png) **Düzenle'yi seçin**.
   - Yapılandırılmış kimlik avı benzetimi yoksa Ekle'ye **tıklayın**.

3. Açılan **Edit SecOps posta kutuları** açılır kutusunda, aşağıdaki adımlardan birini Exchange Online secOps posta kutusu olarak atamasını istediğiniz mevcut bir posta kutusunu girin:
   - Kutuya tıklayın, posta kutularının listesinin çözülmesine izin ver ve sonra posta kutusunu seçin.
   - Kutuya tıklayın, posta kutusu için bir tanımlayıcı (ad, görünen ad, diğer ad, e-posta adresi, hesap adı, vb.) yazmaya başlayın ve sonuçlardan posta kutusunu (görünen ad) seçin.

     Bu adımı gereken sayıda yinelayın. Dağıtım gruplarına izin verilmez.

     Var olan bir değeri kaldırmak için kaldır'a tıklayın. ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) seçin.

4. Bitirdiğinizde, **Kaydet**'i tıklatın.

Yapılandırılan SecOps posta kutusu girdileri **, SecOps** posta kutusu sekmesinde görüntülenir. Değişiklik yapmak için Düzenle simgesine ![tıklayın.](../../media/m365-cc-sc-edit-icon.png) **Sekmede** düzenleyin.

## <a name="use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a>Gelişmiş Microsoft 365 Defender ilkesinde üçüncü taraf kimlik avı benzetimlerini yapılandırmak için Kimlik avı portalını kullanın

1. aşağıdaki Microsoft 365 Defender portalında, <https://security.microsoft.com>Kurallar bölümünde, **E-posta &** \> İşbirliği **İlkeleri'& Kurallar** \>  \> tehdit **ilkeleri Gelişmiş** **teslim'e** gidin. Doğrudan Gelişmiş teslim **sayfasına gitmek için** , 'i kullanın <https://security.microsoft.com/advanceddelivery>.

2. Gelişmiş **teslim sayfasında** Kimlik avı **benzetimi sekmesini** seçin ve aşağıdaki adımlardan birini uygulayın:
   - Düzenle simgesine ![tıklayın.](../../media/m365-cc-sc-edit-icon.png) **Düzenle'yi seçin**.
   - Yapılandırılmış kimlik avı benzetimi yoksa Ekle'ye **tıklayın**.

3. Açılan **Üçüncü taraf kimlik avı benzetimini** düzenle açılır sayfasında, aşağıdaki ayarları yapılandırın:

   - **Etki** alanı: Bu ayarı genişletin ve kutuya tıklayarak, bir değer girerek ve sonra da Enter tuşuna basarak veya kutunun altında görüntülenen değeri seçerek en az bir e-posta adresi etki alanı (örneğin, contoso.com) girin. Bu adımı gereken sayıda yinelayın. En çok 20 girdi  ekleyin.

     > [!NOTE]
     > İletinin SMTP iletiminde kullanılan adresten (**MAIL FROM** adresi, P1 gönderen veya zarf gönderen olarak da bilinir) gelen etki alanını veya kimlik avı benzetimi satıcınız tarafından  belirtilen DomainKeys Identified Mail (DKIM) etki alanını kullanın.`5321.MailFrom` 

   - **IP gönderme**: Bu ayarı genişletin ve kutuya tıklar, bir değer girin ve sonra da Enter tuşuna basarak veya kutunun altında görüntülenen değeri seçerek en az bir geçerli IPv4 adresi girin. Bu adımı gereken sayıda yinelayın. En çok 10 girdi  ekleyin. Geçerli değerler:
     - Tek IP: Örneğin, 192.168.1.1.
     - IP aralığı: Örneğin, 192.168.0.1-192.168.0.254.
     - CIDR IP'si: Örneğin, 192.168.0.1/25.
   - **Benzetim URL'leri** izin vermek için: Bu ayarı genişletin ve isteğe bağlı olarak, kutuya tıklarsanız, bir değer girerek ve sonra Enter tuşuna basarak veya kutunun altında görüntülenen değeri seçerek kimlik avı benzetim kampanyanıza bağlı olan belirli URL'leri girin. En çok 10 girdi  ekleyin. URL söz dizimi biçimi için bkz. [Kiracı İzin Ver/Engelleme Listesi için URL söz dizimi](tenant-allow-block-list.md#url-syntax-for-the-tenant-allowblock-list). Bu URL'ler tıklama zamanında kaydırılmış ancak engellenmiş değil.

   Var olan bir değeri kaldırmak için kaldır'a tıklayın. ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) seçin.

   > [!NOTE]
   > Gelişmiş Teslim'de üçüncü taraf kimlik avı benzetimlerini yapılandırmak için, aşağıdaki bilgileri profesyonel bir şekilde koruması gerekir:
   > 
   > - Aşağıdaki kaynaklardan **herhangi birinin** en az bir Etki Alanı:
   >   - Adres `5321.MailFrom` (MAIL FROM adresi, P1 gönderen veya zarf gönderen olarak da bilinir).
   >   - DKIM etki alanı.
   > - En az bir **Gönderen IP**.
   > 
   > Benzetim iletilerine gönderilen **URL'lerin engellenmiş** olmasını sağlamak için, isteğe bağlı olarak Benzetim URL'leri dahilebilirsiniz.
   > Her alan için en çok 10 girdi belirtebilirsiniz.
   > En az bir Etki Alanı **ve bir Gönderme** **IP'si için** eşleşme olmalıdır, ancak değerler arasında ilişki yoktur.

4. Bitirdikten sonra, aşağıdaki adımlardan birini uygulayın:
   - **İlk kez:** **Ekle'ye tıklayın** ve sonra da Kapat'a **tıklayın**.
   - **Varolanı düzenle**: **Kaydet'e ve** ardından Kapat'a **tıklayın**.

Yapılandırılan üçüncü taraf kimlik avı benzetim girdileri Kimlik avı benzetimi **sekmesinde** görüntülenir. Değişiklik yapmak için Düzenle simgesine ![tıklayın.](../../media/m365-cc-sc-edit-icon.png) **Sekmede** düzenleyin.

## <a name="additional-scenarios-that-require-filtering-bypass"></a>Filtreleme atlama gerektiren ek senaryolar

Gelişmiş teslim ilkesi size yardımcı olabileceği iki senaryoya ek olarak, filtrelemeyi atlamanıza gerek de olan başka senaryolar da vardır:

- **Üçüncü taraf filtreler**: Etki alanınız MX kaydı iletilerinizi (iletiler önce başka bir yere Office 365 yönlendirildi [) olarak](secure-by-default.md) işaret e-posta olarak işaret etmezse, *varsayılan ayar olarak güvenli kullanılamaz*. Koruma eklemek istediğiniz bağlayıcılar için Geliştirilmiş Filtreleme'yi (liste atlama olarak da bilinir) *etkinleştirmeniz gerekir*. Daha fazla bilgi için bkz[. Üçüncü taraf bulut hizmetini kullanarak posta akışını yönetme ve Exchange Online](/exchange/mail-flow-best-practices/manage-mail-flow-using-third-party-cloud). Bağlayıcılar için Gelişmiş Filtreleme'nin istemiyorsanız, üçüncü taraf filtreleme tarafından zaten değerlendirilen iletiler için Microsoft filtrelemesini atlamak için posta akış kurallarını (aktarım kuralları olarak da bilinir) kullanın. Daha fazla bilgi için bkz [. İletilerde SCL'i ayarlamak için posta akışı kurallarını kullanma](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

- **Gözden geçirilen hatalı** pozitif sonuçlar: Yönetici gönderimleri aracılığıyla Microsoft tarafından çözümlenen bazı iletilere geçici olarak izin vermek ve microsoft'a yanlış olarak kötü işaretlenen bilinen iyi iletileri (hatalı pozitif sonuçlar) bildirebilirsiniz.[](admin-submission.md) Tüm geçersiz kılmalarda olduğu gibi, **_bu izinlerin_** geçici olarak kullanılması kesinlikle önerilir.

## <a name="security--compliance-center-powershell-procedures-for-secops-mailboxes-in-the-advanced-delivery-policy"></a>Gelişmiş & ilkede SecOps posta kutuları için Güvenlik ve Uyumluluk Merkezi PowerShell yordamları

Güvenlik ve & Merkezi PowerShell'de, gelişmiş teslim ilkesinde SecOps posta kutularının temel öğeleri:

- **SecOps geçersiz kılma ilkesi**: **\*-SecOpsOverridePolicy** cmdlet'leri tarafından denetlenmektedir.
- **SecOps geçersiz kılma kuralı**: **\*-SecOpsOverrideRule** cmdlet'leri tarafından denetlendi.

Bu davranış aşağıdaki sonuçlara neden olur:

- önce ilkeyi, sonra da kuralın geçerli olduğu ilkeyi tanımlayan kuralı siz oluşturun.
- PowerShell'den bir ilkeyi kaldırabilirsiniz, buna karşılık gelen kural da kaldırılır.
- Bir kuralı PowerShell'den kaldırabilirsiniz, buna karşılık gelen ilke kaldırılamaz. İlgili ilkeyi el ile kaldırmanız gerekir.

### <a name="use-powershell-to-configure-secops-mailboxes"></a>SecOps posta kutularını yapılandırmak için PowerShell kullanma

PowerShell'de gelişmiş teslim ilkesinde SecOps posta kutusu yapılandırmak iki adımlık bir işlemdir:

1. SecOps geçersiz kılma ilkesi oluşturun.
2. Kuralın geçerli olduğu ilkeyi belirten SecOps geçersiz kılma kuralını oluşturun.

#### <a name="step-1-use-powershell-to-create-the-secops-override-policy"></a>1. Adım: SecOps geçersiz kılma ilkesi oluşturmak için PowerShell kullanma

SecOps geçersiz kılma ilkesi oluşturmak için aşağıdaki söz dizimi kullanın:

```powershell
New-SecOpsOverridePolicy -Name SecOpsOverridePolicy -SentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>
```

> [!NOTE]
> Belirttiğiniz Ad değerinden bağımsız olarak, ilke adı _SecOpsOverridePolicy_ olur; dolayısıyla bu değeri de kullanabilirsiniz.

Bu örnekte, SecOps posta kutusu ilkesi oluşturur.

```powershell
New-SecOpsOverridePolicy -Name SecOpsOverridePolicy -SentTo secops@contoso.com
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-SecOpsOverridePolicy](/powershell/module/exchange/new-secopsoverridepolicy).

#### <a name="step-2-use-powershell-to-create-the-secops-override-rule"></a>2. Adım: SecOps geçersiz kılma kuralını oluşturmak için PowerShell kullanma

Bu örnekte, belirtilen ayarlarla SecOps posta kutusu kuralı oluşturur.

```powershell
New-SecOpsOverrideRule -Name SecOpsOverrideRule -Policy SecOpsOverridePolicy
```

> [!NOTE]
> Belirttiğiniz Ad değerinden bağımsız olarak, kural adı benzersiz bir GUID değeri olan _SecOpsOverrideRule_\<GUID\> \<GUID\> olur (örneğin, 6fed4b63-3563-495d-a481-b24a311f8329).

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-SecOpsOverrideRule](/powershell/module/exchange/new-secopsoverriderule).

### <a name="use-powershell-to-view-the-secops-override-policy"></a>SecOps geçersiz kılma ilkesi görüntülemek için PowerShell kullanma

Bu örnekte, bir ve yalnızca SecOps posta kutusu ilkesi hakkında ayrıntılı bilgi döndürür.

```powershell
Get-SecOpsOverridePolicy
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-SecOpsOverridePolicy](/powershell/module/exchange/get-secopsoverridepolicy).

### <a name="use-powershell-to-view-secops-override-rules"></a>SecOps geçersiz kılma kurallarını görüntülemek için PowerShell kullanma

Bu örnek, SecOps geçersiz kılma kuralları hakkında ayrıntılı bilgi döndürür.

```powershell
Get-SecOpsOverrideRule
```

Bir önceki komutun tek bir kural İadesi gerektirse de, silinmeyi bekleyen tüm kurallar sonuçlara da dahil olabilir.

Bu örnekte geçerli kural (bir) ve varsa geçersiz kurallar geçerlidir.

```powershell
Get-SecOpsOverrideRule | Format-Table Name,Mode
```

Geçersiz kuralları belirledikten sonra, bu makalenin devamlarında açıklandığı gibi **Remove-SecOpsOverrideRule** cmdlet'ini kullanarak bunları [kaldırabilirsiniz](#use-powershell-to-remove-secops-override-rules).

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-SecOpsOverrideRule](/powershell/module/exchange/get-secopsoverriderule).

### <a name="use-powershell-to-modify-the-secops-override-policy"></a>SecOps geçersiz kılma ilkesi değiştirmek için PowerShell kullanma

SecOps geçersiz kılma ilkesinde değişiklik yapmak için aşağıdaki söz dizimi kullanın:

```powershell
Set-SecOpsOverridePolicy -Identity SecOpsOverridePolicy [-AddSentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>] [-RemoveSentTo <EmailAddress1>,<EmailAddress2>,...<EmailAddressN>]
```

Bu örnek SecOps `secops2@contoso.com` geçersiz kılma ilkesine ekler.

```powershell
Set-SecOpsOverridePolicy -Identity SecOpsOverridePolicy -AddSentTo secops2@contoso.com
```

> [!NOTE]
> İlişkili, geçerli bir SecOps geçersiz kılma kuralı varsa, kuralda yer alan e-posta adresleri de güncelleştirilir.

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-SecOpsOverridePolicy](/powershell/module/exchange/set-secopsoverridepolicy).

### <a name="use-powershell-to-modify-a-secops-override-rule"></a>SecOps geçersiz kılma kuralını değiştirmek için PowerShell kullanma

**Set-SecOpsOverrideRule** cmdlet'i, SecOps geçersiz kılma kuralında e-posta adreslerini değiştirmez. SecOps geçersiz kılma kuralında **e-posta adreslerini değiştirmek için Set-SecOpsOverridePolicy** cmdlet'ini kullanın.

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-SecOpsOverrideRule](/powershell/module/exchange/set-secopsoverriderule).

### <a name="use-powershell-to-remove-the-secops-override-policy"></a>SecOps geçersiz kılma ilkesi kaldırmak için PowerShell kullanma

Bu örnekte, SecOps Posta Kutusu ilkesi ve buna karşılık gelen kural kaldırıldı.

```powershell
Remove-SecOpsOverridePolicy -Identity SecOpsOverridePolicy
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Remove-SecOpsOverridePolicy](/powershell/module/exchange/remove-secopsoverridepolicy).

### <a name="use-powershell-to-remove-secops-override-rules"></a>SecOps geçersiz kılma kurallarını kaldırmak için PowerShell kullanma

SecOps geçersiz kılma kuralını kaldırmak için aşağıdaki söz dizimi kullanın:

```powershell
Remove-SecOpsOverrideRule -Identity <RuleIdentity>
```

Bu örnekte, belirtilen SecOps geçersiz kılma kuralı kaldırıldı.

```powershell
Remove-SecOpsOverrideRule -Identity SecOpsOverrideRule6fed4b63-3563-495d-a481-b24a311f8329
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Remove-SecOpsOverrideRule](/powershell/module/exchange/remove-secopsoverriderule).

## <a name="security--compliance-center-powershell-procedures-for-third-party-phishing-simulations-in-the-advanced-delivery-policy"></a>Gelişmiş & ilkesinde üçüncü taraf kimlik avı benzetimleri için Güvenlik ve Uyumluluk Merkezi PowerShell yordamları

Güvenlik ve & Merkezi PowerShell'de, gelişmiş teslim ilkesinde üçüncü taraf kimlik avı benzetimlerinin temel öğeleri:

- **Kimlik avı benzetimi geçersiz kılma ilkesi**: **\*-PhishSimOverridePolicy** cmdlet'leri tarafından denetlenmektedir.
- **Kimlik avı benzetimi geçersiz kılma kuralı**: **\*-PhishSimOverrideRule** cmdlet'leri tarafından denetlenmektedir.
- **İzin verilen (engelsiz) kimlik** avı benzetimi URL'leri: **\*-TenantAllowBlockListItems** cmdlet'leri tarafından denetlenmektedir.

Bu davranış aşağıdaki sonuçlara neden olur:

- önce ilkeyi, sonra da kuralın geçerli olduğu ilkeyi tanımlayan kuralı siz oluşturun.
- İlke ve kuralda ayarları ayrı olarak değiştirirsiniz.
- PowerShell'den bir ilkeyi kaldırabilirsiniz, buna karşılık gelen kural da kaldırılır.
- Bir kuralı PowerShell'den kaldırabilirsiniz, buna karşılık gelen ilke kaldırılamaz. İlgili ilkeyi el ile kaldırmanız gerekir.

### <a name="use-powershell-to-configure-third-party-phishing-simulations"></a>Üçüncü taraf kimlik avı benzetimlerini yapılandırmak için PowerShell kullanma

PowerShell'de üçüncü taraf kimlik avı benzetimlerini yapılandırma, çok adımlı bir işlemdir:

1. Kimlik avı benzetimi geçersiz kılma ilkesi oluşturun.
2. Kimlik avı benzetimi geçersiz kılma kuralını şu şekilde oluşturun:
   - Kuralın geçerli olduğu ilke.
   - Kimlik avı benzetimi iletilerinin kaynak IP adresi.
3. İsteğe bağlı olarak, izin ver gereken kimlik avı benzetimi URL'lerini kimlik avı benzetimi URL'lerini (engellenmiş veya taranmış değil) kimlik avı URL'lerini kimlik avı url'lerinde kimlik doğrulama.

#### <a name="step-1-use-powershell-to-create-the-phishing-simulation-override-policy"></a>1. Adım: Kimlik avı benzetimi geçersiz kılma ilkesi oluşturmak için PowerShell kullanma

Bu örnek, kimlik avı benzetimi geçersiz kılma ilkesi oluşturur.

```powershell
New-PhishSimOverridePolicy -Name PhishSimOverridePolicy
```

**Not**: Belirttiğiniz Ad değerinden bağımsız olarak, ilke adı _PhishSimOverridePolicy_ olur; dolayısıyla bu değeri de kullanabilirsiniz.

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-PhishSimOverridePolicy](/powershell/module/exchange/new-phishsimoverridepolicy).

#### <a name="step-2-use-powershell-to-create-the-phishing-simulation-override-rule"></a>2. Adım: Kimlik avı benzetimi geçersiz kılma kuralını oluşturmak için PowerShell kullanma

Aşağıdaki sözdizimini kullanın:

```powershell
New-PhishSimOverrideRule -Name PhishSimOverrideRule -Policy PhishSimOverridePolicy -Domains <Domain1>,<Domain2>,...<Domain10> -SenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntry10>
```

Belirttiğiniz Ad değerinden bağımsız olarak, kural adı _PhishSimOverrideRule_\<GUID\> \<GUID\> olur ve bu benzersiz bir GUID değeridir (örneğin, a0eae53e-d755-4a42-9320-b9c6b55c5011).

Geçerli bir IP adresi girdisi aşağıdaki değerlerden biridir:

- Tek IP: Örneğin, 192.168.1.1.
- IP aralığı: Örneğin, 192.168.0.1-192.168.0.254.
- CIDR IP'si: Örneğin, 192.168.0.1/25.

Bu örnek, belirtilen ayarlarla kimlik avı benzetimi geçersiz kılma kuralını oluşturur.

```powershell
New-PhishSimOverrideRule -Name PhishSimOverrideRule -Policy PhishSimOverridePolicy -Domains fabrikam.com,wingtiptoys.com -SenderIpRanges 192.168.1.55
```

Ayrıntılı söz dizimi ve parametre bilgileri için [bkz. New-PhishSimOverrideRule](/powershell/module/exchange/new-phishsimoverriderule).

#### <a name="step-3-optional-use-powershell-to-identify-the-phishing-simulation-urls-to-allow"></a>3. Adım: (İsteğe bağlı) İzin vermek üzere kimlik avı benzetimi URL'lerini tanımlamak için PowerShell kullanın

Aşağıdaki sözdizimini kullanın:

```powershell
New-TenantAllowBlockListItems -Allow -ListType Url -ListSubType AdvancedDelivery -Entries "<URL1>","<URL2>",..."<URL10>" <[-NoExpiration] | [-ExpirationDate <DateTime>]>
```

URL söz dizimi hakkında ayrıntılı bilgi için bkz. [Kiracı İzin Ver/Engelle Listesi için URL söz dizimi](tenant-allow-block-list.md#url-syntax-for-the-tenant-allowblock-list).

Bu örnek, süresi dolmadan belirtilen üçüncü taraf kimlik avı benzetimi URL'si için bir URL izin girdisi ekler.

```powershell
New-TenantAllowBlockListItems -Allow -ListType Url -ListSubType AdvancedDelivery -Entries *.fabrikam.com -NoExpiration
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

### <a name="use-powershell-to-view-the-phishing-simulation-override-policy"></a>Kimlik avı benzetimi geçersiz kılma ilkesi görüntülemek için PowerShell kullanma

Bu örnek, bir ve yalnızca kimlik avı benzetimi geçersiz kılma ilkesi hakkında ayrıntılı bilgi döndürür.

```powershell
Get-PhishSimOverridePolicy
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-PhishSimOverridePolicy](/powershell/module/exchange/get-phishsimoverridepolicy).

### <a name="use-powershell-to-view-phishing-simulation-override-rules"></a>Kimlik avı benzetimi geçersiz kılma kurallarını görüntülemek için PowerShell kullanma

Bu örnek, kimlik avı benzetimi geçersiz kılma kuralları hakkında ayrıntılı bilgi döndürür.

```powershell
Get-PhishSimOverrideRule
```

Bir önceki komutun tek bir kural İadesi gerektirse de, silinmeyi bekleyen tüm kurallar sonuçlara da dahil olabilir.

Bu örnekte geçerli kural (bir) ve varsa geçersiz kurallar geçerlidir.

```powershell
Get-PhishSimOverrideRule | Format-Table Name,Mode
```

Geçersiz kuralları belirledikten sonra, bu makalenin devamlarında açıklandığı gibi **Remove-PhishSimOverrideRule** cmdlet'ini kullanarak bunları [kaldırabilirsiniz](#use-powershell-to-remove-phishing-simulation-override-rules).

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-PhishSimOverrideRule](/powershell/module/exchange/get-phishsimoverriderule).

### <a name="use-powershell-to-view-the-allowed-phishing-simulation-url-entries"></a>İzin verilen kimlik avı benzetimi URL girdilerini görüntülemek için PowerShell kullanma

İzin verilen kimlik avı benzetimi URL'lerini görüntülemek için aşağıdaki komutu çalıştırın:

```powershell
Get-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

### <a name="use-powershell-to-modify-the-phishing-simulation-override-policy"></a>Kimlik avı benzetimi geçersiz kılma ilkesi değiştirmek için PowerShell kullanma

Kimlik avı benzetimi geçersiz kılma ilkesinde değişiklik yapmak için aşağıdaki söz dizimi kullanın:

```powershell
Set-PhishSimOverridePolicy -Identity PhishSimOverridePolicy [-Comment "<DescriptiveText>"] [-Enabled <$true | $false>]
```

Bu örnekte, kimlik avı benzetimi geçersiz kılma ilkesi devre dışıdır.

```powershell
Set-PhishSimOverridePolicy -Identity PhishSimOverridePolicy -Enabled $false
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-PhishSimOverridePolicy](/powershell/module/exchange/set-phishsimoverridepolicy).

### <a name="use-powershell-to-modify-phishing-simulation-override-rules"></a>Kimlik avı benzetimi geçersiz kılma kurallarını değiştirmek için PowerShell kullanma

Kimlik avı benzetimi geçersiz kılma kuralını değiştirmek için aşağıdaki söz dizimi kullanın:

```powershell
Set-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011 [-Comment "<DescriptiveText>"] [-AddSenderDomainIs <DomainEntry1>,<DomainEntry2>,...<DomainEntryN>] [-RemoveSenderDomainIs <DomainEntry1>,<DomainEntry2>,...<DomainEntryN>] [-AddSenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>] [-RemoveSenderIpRanges <IPAddressEntry1>,<IPAddressEntry2>,...<IPAddressEntryN>]
```

Bu örnekte, belirtilen kimlik avı benzetimi geçersiz kılma kuralı aşağıdaki ayarlarla değiştiriliyor:

- Etki alanı girdisini ekle blueyonderairlines.com.
- 192.168.1.55 IP adresi girdisini kaldırın.

Bu değişikliklerin mevcut girdileri etkilemeyeceğini unutmayın.

```powershell
Set-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011 -AddSenderDomainIs blueyonderairlines.com -RemoveSenderIpRanges 192.168.1.55
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-PhishSimOverrideRule](/powershell/module/exchange/set-phishsimoverriderule).

### <a name="use-powershell-to-modify-the-allowed-phishing-simulation-url-entries"></a>İzin verilen kimlik avı benzetimi URL girdilerini değiştirmek için PowerShell kullanma

URL değerlerini doğrudan değiştiremezsiniz. Var olan [URL girdilerini kaldırabilir ve](#use-powershell-to-remove-the-allowed-phishing-simulation-url-entries) [bu makalede açıklandığı gibi yeni URL](#step-3-optional-use-powershell-to-identify-the-phishing-simulation-urls-to-allow) girdileri eklersiniz.

İzin verilen kimlik avı benzetimi URL girdisinin diğer özelliklerini değiştirmek için (örneğin, son kullanma tarihi veya açıklamalar), aşağıdaki söz dizimi kullanın:

```powershell
Set-TenantAllowBlockListItems <-Entries "<URL1>","<URL2>",..."<URLN>" | -Ids <Identity>> -ListType URL -ListSubType AdvancedDelivery <[-NoExpiration] | [-ExpirationDate <DateTime>]> [-Notes <String>]
```

Değiştireceğiz girişi, URL değerlerine ( _Entries_ parametresi) veya **Get-TenantAllowBlockListItems** cmdlet'inin ( _Ids_ parametresi) çıkışından gelen Identity değerine göre tanımlayabilirsiniz.

Bu örnekte, belirtilen girdinin son kullanma tarihi değiştirilmiştir.

```powershell
Set-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery –Entries "*.fabrikam.com" -ExpirationDate 9/11/2021
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

### <a name="use-powershell-to-remove-a-phishing-simulation-override-policy"></a>Kimlik avı benzetimi geçersiz kılma ilkesi kaldırmak için PowerShell kullanma

Bu örnek, kimlik avı benzetimi ilkeyi ve ilgili kuralı geçersiz kılar.

```powershell
Remove-PhishSimOverridePolicy -Identity PhishSimOverridePolicy
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Remove-PhishSimOverridePolicy](/powershell/module/exchange/remove-phishsimoverridepolicy).

### <a name="use-powershell-to-remove-phishing-simulation-override-rules"></a>Kimlik avı benzetimi geçersiz kılma kurallarını kaldırmak için PowerShell kullanma

Kimlik avı benzetimi geçersiz kılma kuralını kaldırmak için aşağıdaki söz dizimi kullanın:

```powershell
Remove-PhishSimOverrideRule -Identity <RuleIdentity>
```

Bu örnek, belirtilen kimlik avı benzetimi geçersiz kılma kuralını kaldırır.

```powershell
Remove-PhishSimOverrideRule -Identity PhishSimOverrideRulea0eae53e-d755-4a42-9320-b9c6b55c5011
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Remove-PhishSimOverrideRule](/powershell/module/exchange/remove-phishsimoverriderule).

### <a name="use-powershell-to-remove-the-allowed-phishing-simulation-url-entries"></a>İzin verilen kimlik avı benzetimi URL girdilerini kaldırmak için PowerShell kullanma

Var olan bir kimlik avı benzetimi URL girdisini kaldırmak için aşağıdaki söz dizimi kullanın:

```powershell
Remove-TenantAllowBlockListItems <-Entries "<URL1>","<URL2>",..."<URLN>" | -Ids <Identity>> -ListType URL -ListSubType AdvancedDelivery
```

Değiştireceğiz girişi, URL değerlerine ( _Entries_ parametresi) veya **Get-TenantAllowBlockListItems** cmdlet'inin ( _Ids_ parametresi) çıkışından gelen Identity değerine göre tanımlayabilirsiniz.

Bu örnekte, belirtilen girdinin son kullanma tarihi değiştirilmiştir.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -ListSubType AdvancedDelivery –Entries "*.fabrikam.com" -ExpirationDate 9/11/2021
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).
