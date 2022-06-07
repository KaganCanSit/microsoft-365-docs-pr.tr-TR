---
title: Exchange Online'da dağıtım listelerini Microsoft 365 Gruplarına yükseltme
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 787d7a75-e201-46f3-a242-f698162ff09f
description: Exchange Online'da bir veya birden çok dağıtım listesini Microsoft 365 Gruplarına yükseltmeyi ve aynı anda çeşitli dağıtım listelerini yükseltmek için PowerShell'i kullanmayı öğrenin.
ms.openlocfilehash: 6f27c4a7df345a25f4b5ca7d2a9f2979a97e7c6a
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2022
ms.locfileid: "65922185"
---
# <a name="upgrade-distribution-lists-to-microsoft-365-groups-in-exchange-online"></a>Exchange Online'da dağıtım listelerini Microsoft 365 Gruplarına yükseltme

Dağıtım listesini Microsoft 365 Grubuna yükseltmek, kuruluşunuzdaki grupların özelliklerini ve özelliklerini geliştirmenin harika bir yoludur. Daha fazla bilgi için bkz. [Dağıtım listelerinizi neden Outlook'ta gruplara yükseltmeniz gerekir](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188)?

Dağıtım listelerini birer birer veya aynı anda birkaç tane yükseltebilirsiniz. Exchange yönetim merkezini (EAC) veya Exchange Online PowerShell'i kullanabilirsiniz.

## <a name="upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups"></a>Bir veya birden çok dağıtım listesi grubunu Microsoft 365 Gruplarına yükseltme

Dağıtım listesini yükseltmek için genel yönetici veya Exchange yöneticisi olmanız gerekir. Microsoft 365 Grupları'na yükseltmek için dağıtım listesinin atanmış bir sahibi ve bu sahibin bir posta kutusu olması gerekir.

### <a name="use-the-classic-eac-to-upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Outlook'ta bir veya birden çok dağıtım listesi grubunu Microsoft 365 Gruplarına yükseltmek için Klasik EAC'yi kullanma

> [!NOTE]
> Bu bölümdeki yordamlar yeni EAC'de kullanılamaz.

1. Exchange yönetim merkezine > **Alıcı Grupları'na** \> gidin.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a>

   Microsoft 365 Gruplarına yükseltilmeye uygun dağıtım listeleriniz ( **dağıtım grupları** olarak da adlandırılır) olduğunu belirten bir bildirim görürsünüz.
   
   ![Başlarken düğmesini seçin.](../../media/8cf838b4-2644-401f-a366-08c1eea183eb.png)

1. **Gruplar** sayfasından bir veya daha fazla dağıtım listesi (**dağıtım grupları** olarak da adlandırılır) seçin.

   ![Bir dağıtım grubu seçin.](../../media/2c303433-d60b-4100-a6ae-5809b03a8cdb.png)

1. Yükseltme simgesini seçin.

   ![Microsoft 365 Grupları simgesine yükseltin.](../../media/1e28cb3d-bff3-4be3-8329-1902d2d54720.png)

1. Yükseltmeyi onaylamak için bilgi iletişim kutusunda **Evet'i** seçin. İşlem hemen başlar. Yükseltmekte olduğunuz dağıtım ışıklarının boyutuna ve sayısına bağlı olarak işlem dakika veya saat sürebilir.

   Dağıtım listesi yükseltilemiyorsa, bunu söyleyen bir iletişim kutusu görüntülenir. [Bkz. Hangi dağıtım listeleri yükseltilemiyor?](#which-distribution-lists-cant-be-upgraded).

1. Birden çok dağıtım listesini yükseltiyorsanız, hangi dağıtım listelerinin yükseltildiğini filtrelemek için açılan listeyi kullanın. Liste tamamlanmamışsa, bir süre daha bekleyin ve ardından başarıyla yükseltilenleri görmek için **Yenile'yi** seçin.

**Notlar**:

- Yükseltmeler tamamlandığında bildirim almazsınız. Bunun yerine, **Yükseltme için kullanılabilir** veya **Yükseltilen DLL'ler altında listelenenlere** bakın.

- Yükseltme için bir dağıtım listesi seçtiyseniz ancak yine de sayfada **Yükseltme için kullanılabilir** olarak görüntüleniyorsa yükseltme başarısız oldu. Bkz. [Yükseltme işe yaramazsa yapılması gerekenler](#what-to-do-if-the-upgrade-doesnt-work).

- Grubun özet e-postası, sahibi olduğunuz tüm uygun dağıtım listelerini yükseltmenizi önerebilir. Özet e-posta hakkında daha fazla bilgi için bkz. [Outlook'ta grup konuşması yapma](https://support.microsoft.com/office/a0482e24-a769-4e39-a5ba-a7c56e828b22).

## <a name="what-to-do-if-the-upgrade-doesnt-work"></a>Yükseltme işe yaramazsa yapılması gerekenler

Yükseltilemeyen dağıtım listeleri değişmeden kalır.

Bir veya daha fazla **uygun** dağıtım listesi yükseltilemiyorsa aşağıdaki adımları uygulayın:

1. Olası sorunları taramak için [bu betiği](https://aka.ms/DLToM365Group) kullanın. Betik tarafından bildirilen sorunları düzeltin ve dağıtım listesini bir kez daha yükseltmeyi deneyin. 

2. Betik işe yaramazsa bir [Destek bileti](../../business-video/get-help-support.md) açın. Sorunun Gruplar Mühendisliği ekibine yükseltilmesi gerekir.

## <a name="how-to-use-exchange-online-powershell-to-upgrade-several-distribution-lists-at-the-same-time"></a>Aynı anda çeşitli dağıtım listelerini yükseltmek için Exchange Online PowerShell'i kullanma

Exchange Online PowerShell'e bağlanmak için bkz. [Exchange Online PowerShell'e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

### <a name="upgrade-a-single-distribution-list"></a>Tek bir dağıtım listesini yükseltme

Tek bir dağıtım listesini yükseltmek için aşağıdaki söz dizimini kullanın:

```PowerShell
Upgrade-DistributionGroup -DLIdentities <EmailAddress>
```

Bu örnek, dağıtım listesini marketing@contoso.com yükseltin:

```PowerShell
Upgrade-DistributionGroup -DLIdentities marketing@contoso.com
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Upgrade-DistributionGroup](/powershell/module/exchange/upgrade-distributiongroup).

> [!NOTE]
> [New-UnifiedGroup](/powershell/module/exchange/new-unifiedgroup) cmdlet'ini kullanarak tek bir dağıtım listesini Microsoft 365 grubuna da yükseltebilirsiniz.

### <a name="upgrade-multiple-distribution-lists-at-the-same-time"></a>Aynı anda birden çok dağıtım listesini yükseltme

Aynı anda birden çok dağıtım listesini yükseltmek için aşağıdaki söz dizimini kullanın:

```PowerShell
Upgrade-DistributionGroup -DLIdentities <EmailAddress1>,<EmailAddress2>,...
```

Bu örnek, belirtilen dağıtım listelerini Microsoft 365 Gruplarına yükseltmektedir.

```powershell
Upgrade-DistributionGroup -DLIdentities marketing@contoso.com,finanace@contoso.com,hr@contoso.com
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Upgrade-DistributionGroup](/powershell/module/exchange/upgrade-distributiongroup).

### <a name="upgrade-all-eligible-distribution-lists"></a>Tüm uygun dağıtım listelerini yükseltme

Tüm uygun dağıtım listelerini Microsoft 365 Gruplarına yükseltmek için aşağıdaki yöntemlerden birini kullanın:

- Tüm uygun dağıtım listelerini yükseltin:

   ```PowerShell
   $All = Get-EligibleDistributionGroupForMigration -ResultSize unlimited
   $All | Foreach-Object {Upgrade-DistributionGroup -DLIdentities $_.PrimarySMTPAddress}
   ```

- Uygun olup olmadıklarına bakılmaksızın tüm dağıtım listelerini yükseltmeyi deneyin:

   ```PowerShell
   $All Get-DistributionGroup -RecipientTypeDetails MailUniversalDistributionGroup -ResultSize unlimited
   $All | Foreach-Object {Upgrade-DistributionGroup -DLIdentities $_.PrimarySMTPAddress}
   ```

## <a name="faq-about-upgrading-distribution-lists-to-microsoft-365-groups-in-outlook"></a>Outlook'ta dağıtım listelerini Microsoft 365 Gruplarına yükseltme hakkında SSS

### <a name="which-distribution-lists-cant-be-upgraded"></a>Hangi dağıtım listeleri yükseltilemiyor?

Yalnızca bulut tarafından yönetilen, basit, iç içe olmayan dağıtım listelerini yükseltebilirsiniz. Aşağıdaki tabloda **yükseltilemeyen** dağıtım listeleri listelenmiştir.

|Özellik|Uygun?|
|---|:---:|
|Şirket içi yönetilen dağıtım listesi.|Hayır|
|İç içe dağıtım listeleri. Dağıtım listesi alt gruplara sahiptir veya başka bir grubun üyesidir.|Hayır|
|Bir veya daha fazla üyenin kullanıcı posta kutusu, paylaşılan posta kutusu, ekip posta kutusu veya posta kullanıcısı dışında bir şey olduğu dağıtım listeleri. Başka bir deyişle, dağıtım listesinin herhangi bir üyesinin **RecipientTypeDetails** değeri **UserMailbox**, **SharedMailbox**, **TeamMailbox** veya **MailUser** değildir.|Hayır|
|100'den fazla sahibi olan dağıtım listesi.|Hayır|
|Yalnızca üyeleri olan ancak sahibi olmayan dağıtım listesi.|Hayır|
|Özel karakterler içeren diğer adı olan dağıtım listesi.|Hayır|
|Dağıtım listesi, Paylaşılan posta kutusunun iletme adresi olacak şekilde yapılandırılmıştır.|Hayır|
|Dağıtım listesi, başka bir dağıtım listesindeki **Gönderen Kısıtlaması'nın** bir parçasıdır.|Hayır|
|Posta etkin güvenlik grupları.|Hayır|
|Dinamik dağıtım grupları.|Hayır|
|**RoomLists'e** dönüştürülen dağıtım listeleri.|Hayır|

### <a name="check-which-distribution-lists-are-eligible-for-upgrade"></a>Hangi dağıtım listelerinin yükseltme için uygun olduğunu denetleyin

Belirli bir dağıtım listesinin yükseltme için uygun olup olmadığını denetlemek için aşağıdaki komutu çalıştırın:

```PowerShell
Get-DistributionGroup <EmailAddress> | Get-EligibleDistributionGroupForMigration
```

Yükseltme için uygun tüm dağıtım gruplarını görmek için aşağıdaki komutu çalıştırın:

```PowerShell
Get-EligibleDistributionGroupForMigration
```

### <a name="who-can-run-the-upgrade-scripts"></a>Yükseltme betiklerini kimler çalıştırabilir?

Genel yönetici veya Exchange yönetici haklarına sahip kişiler.

### <a name="why-is-the-contact-card-still-showing-a-distribution-list-what-should-i-do-to-prevent-an-upgraded-distribution-list-from-showing-up-in-my-auto-suggest-list"></a>Kişi kartı neden hala bir dağıtım listesi gösteriyor? Yükseltilmiş bir dağıtım listesinin otomatik öneri listemde gösterilmesini önlemek için ne yapmalıyım?

- **Outlook**: Bir ilişkilendirme listesini Bir Microsoft 365 grubuna yükselttikten sonra, kullanıcının yerel alıcı önbelleği (nick adı önbelleği olarak da bilinir) değişikliğin farkında olmaz. Kullanıcının yerel alıcı önbelleğini sıfırlamak için aşağıdaki makaledeki adımları uygulayın: [Outlook Otomatik Tamamlama listesi hakkındaki bilgiler](/outlook/troubleshoot/contacts/information-about-the-outlook-autocomplete-list). 

  Alıcı önbelleğini güncelleştirmezseniz, Microsoft 365 Grubuna gönderilen tüm e-postalar başarıyla teslim edilir, ancak aşağıdaki sorunlar devam eder:
  
  - Grup alıcısı, Microsoft 365 Grubu yerine dağıtım listesi olarak çözümlenir.
  - Kişi kartı, Microsoft 365 Grubu yerine dağıtım listesinin kişisi olacaktır.

- **Web üzerinde Outlook**: Outlook gibi dağıtım listesi de alıcı önbelleğinde kalır. Grubun kişi kartını görmek için önbelleği yenilemek için bu makaledeki adımları izleyin: [Önerilen adı veya e-posta adresini Otomatik Tamamlama Listesinden kaldırın](https://support.microsoft.com/office/9E1419D9-E88F-445B-B07F-F558B8A37C58).

### <a name="do-new-group-members-get-a-welcome-email-in-their-inbox"></a>Yeni grup üyeleri gelen kutularına hoş geldiniz e-postası mı alıyor?

Hayır. Karşılama iletilerini etkinleştirme ayarı varsayılan olarak false olarak ayarlanır. Bu ayar, geçiş tamamlandıktan sonra katılabilecek mevcut ve yeni grup üyelerini etkiler. Grup sahibi daha sonra konuk kullanıcılara izin verirse, konuk kullanıcılar Gelen Kutularına hoş geldiniz e-postası almaz. Konuk üyeler grupla çalışmaya devam edebilir.

### <a name="what-if-one-or-some-of-the-dls-are-not-upgraded"></a>DLL'lerden biri veya bir kısmı yükseltilmediyse ne olur?

Uygun dağıtım listelerinin yükseltilememe durumları vardır. Örneğin:

- Yönetici bir **Grup E-posta Adresi İlkesi** uyguladı ve dağıtım listesi ilkenin gereksinimlerini karşılamıyor.

- Dağıtım listesinde **MemberJoinRestriction** veya **MemberDepartRestriction** **değeri Kapalı** olarak ayarlanmıştır.

- Microsoft 365 Grubu oluşturma işlemi, bu makalede açıklandığı gibi sınırlıdır: [bu makale](/microsoft-365/solutions/manage-creation-of-groups).

  Bu özel sorun için aşağıdaki geçici çözümlerden birini kullanın:

  - Dağıtım listesinin tüm sahiplerinin Microsoft 365 Grupları oluşturmasına izin verildiğinden emin olun (örneğin, sahipler Microsoft 365 Grupları oluşturmasına izin verilen güvenlik grubunun üyesidir).

  - Dağıtım listesinin sahibini geçici olarak Microsoft 365 Grupları oluşturmasına izin verilen bir kullanıcıyla değiştirin.

### <a name="what-happens-to-the-dl-if-the-upgrade-from-eac-fails"></a>EAC'den yükseltme başarısız olursa DL'ye ne olur?

Yükseltme yalnızca çağrı sunucuya gönderildiğinde gerçekleşir. Yükseltme başarısız olursa dağıtım listeleriniz kalır ve eskisi gibi çalışır.

### <a name="what-happens-to-message-approval-moderation-settings-on-distribution-groups-after-upgrading"></a>Yükseltmeden sonra dağıtım gruplarında ileti onayı (denetim) ayarlarına ne olur?

İleti onayı (denetim) ayarları korunur ve dağıtım grubu bir Microsoft 365 Grubuna yükseltildikten sonra düzgün çalışmaya devam eder.

## <a name="related-content"></a>İlgili içerik

[Grupları karşılaştırma](../create-groups/compare-groups.md) (makale)\
[Microsoft 365 Gruplarını kullanıcılarınıza açıklama](../create-groups/explain-groups-knowledge-worker.md) (makale)\
[Yönetim merkezini kullanarak Microsoft 365 gruplarına üye ekleme veya gruptan üye kaldırma](../create-groups/add-or-remove-members-from-groups.md)
