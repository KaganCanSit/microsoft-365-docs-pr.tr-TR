---
title: Dağıtım listelerini Outlook'da Microsoft 365 组 yükseltme
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
description: Outlook'da bir veya birden çok dağıtım listesini Microsoft 365 组 yükseltmeyi ve aynı anda çeşitli dağıtım listelerini yükseltmek için PowerShell'i kullanmayı öğrenin.
ms.openlocfilehash: 832d65854a6a18ad28e3d9fca6d1d11c17146c80
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782269"
---
# <a name="upgrade-distribution-lists-to-microsoft-365-groups-in-outlook"></a>Dağıtım listelerini Outlook'da Microsoft 365 组 yükseltme

Dağıtım listelerini Outlook'da Microsoft 365 组 yükseltebilirsiniz. Bu, kuruluşunuzun dağıtım listelerine Microsoft 365 组 tüm özelliklerini ve işlevlerini vermenin harika bir yoludur. [Neden Outlook'ta dağıtım listelerinizi gruplara yükseltmelisiniz?](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188)

DLL'leri birer birer veya aynı anda birkaç tane yükseltebilirsiniz.

## <a name="upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Bir veya birden çok dağıtım listesi grubunu Outlook'da Microsoft 365 组 yükseltme

Dağıtım listesi grubunu yükseltmek için genel yönetici veya Exchange yöneticisi olmanız gerekir. Microsoft 365 组 yükseltmek için dağıtım listesi grubunun posta kutusu olan bir sahibi olmalıdır.

### <a name="use-the-new-eac-to-upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Outlook'de bir veya birden çok dağıtım listesi grubunu Microsoft 365 组 yükseltmek için yeni EAC'yi kullanın

1. **Alıcı** \> <a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank">Grupları</a> > yeni Exchange yönetim merkezine gidin.

2. **Gruplar** sayfasından Microsoft 365 grubuna yükseltmek istediğiniz dağıtım listesi grubunu (**dağıtım grubu** olarak da adlandırılır) seçin.

3. Araç çubuğundan **Dağıtım grubunu yükselt'i** seçin.

4. **Yükseltmeye hazır mısınız?** iletişim kutusunda **Yükselt'e** tıklayın. İşlem hemen başlar. Yükseltmekte olduğunuz dağıtım listesi gruplarının boyutuna ve sayısına bağlı olarak işlem dakika veya saat sürebilir.

> [!NOTE]
> En üstteki başlık yükseltmeyi gösterir; örneğin *Dağıtım grupları yükseltilmiştir. Değişiklikleri yansıtmak 5 dakika sürer. Yükseltilen dağıtım gruplarını görmek için Microsoft 365 gruplarına göre filtreleyin*.

### <a name="use-the-classic-eac-to-upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Outlook'da Microsoft 365 组 için bir veya birden çok dağıtım listesi grubunu yükseltmek için Klasik EAC'yi kullanın

1. Exchange yönetim merkezine > **Alıcı Grupları'na** \> gidin.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a><br/>Microsoft 365 组 yükseltilmeye uygun dağıtım listeleriniz (**dağıtım grupları** olarak da adlandırılır) olduğunu belirten bir bildirim görürsünüz.<br/> ![Kullanmaya başlayın düğmesini seçin.](../../media/8cf838b4-2644-401f-a366-08c1eea183eb.png)

1. **Gruplar** sayfasından bir veya daha fazla dağıtım listesi (**dağıtım grubu** olarak da adlandırılır) seçin.<br/>![Bir dağıtım grubu seçin.](../../media/2c303433-d60b-4100-a6ae-5809b03a8cdb.png)

1. Yükseltme simgesini seçin.<br/>![Microsoft 365 组 simgesine yükseltin.](../../media/1e28cb3d-bff3-4be3-8329-1902d2d54720.png)

1. Yükseltmeyi onaylamak için bilgi iletişim kutusunda **Evet'i** seçin. İşlem hemen başlar. Yükseltmekte olduğunuz DLL'lerin boyutuna ve sayısına bağlı olarak işlem dakika veya saat sürebilir.<br/>Dağıtım listesi yükseltilemiyorsa, bunu söyleyen bir iletişim kutusu görüntülenir. [Bkz. Hangi dağıtım listeleri yükseltilemiyor?](#which-distribution-lists-cant-be-upgraded).

1. Birden çok dağıtım listesini yükseltiyorsanız, hangi dağıtım listelerinin yükseltildiğini filtrelemek için açılan listeyi kullanın. Liste tamamlanmamışsa, bir süre daha bekleyin ve ardından başarıyla yükseltilenleri görmek için **Yenile'yi** seçin.<br/>Seçtiğiniz tüm DLL'ler için yükseltme işleminin ne zaman tamamlandığını bildiren bir bildirim yoktur. **Yükseltme için kullanılabilir** veya **Yükseltilen DLL'ler** altında listelenenleri görmek için bunu anlayabilirsiniz.

1. Yükseltme için bir DL seçtiyseniz ancak yükseltme için kullanılabilir olarak sayfada görünmeye devam ediyorsa yükseltme başarısız oldu. Bkz. [Yükseltme işe yaramazsa yapılması gerekenler](#what-to-do-if-the-upgrade-doesnt-work).

> [!NOTE]
> Grupların özet e-postalarını alıyorsanız, bazen sahibi olduğunuz uygun dağıtım listelerini yükseltmenizi sağlamanın en altta olduğunu fark edebilirsiniz. Özet e-postalar hakkında daha fazla bilgi için bkz. [Outlook'da grup konuşması yapma](https://support.microsoft.com/office/a0482e24-a769-4e39-a5ba-a7c56e828b22).

## <a name="what-to-do-if-the-upgrade-doesnt-work"></a>Yükseltme işe yaramazsa yapılması gerekenler

Yükseltilemeyen dağıtım listeleri değişmeden kalır.

Bir veya daha fazla **uygun** dağıtım listesi yükseltilemiyorsa, 

1. Dağıtım listesinin Microsoft 365 grubuna yükseltilmesini engelleyebilecek olası sorunları taramak, betik tarafından bildirilen sorunları düzeltmek ve dağıtım listesini bir kez daha yükseltmeyi denemek için [bu](https://aka.ms/DLToM365Group) betiği kullanın. 

2. Yukarıdaki betik işe yaramazsa veya sorun devam ederse bir [Destek bileti](../../business-video/get-help-support.md) açın. Sorunu anlamaları için sorunun Gruplar Mühendisliği ekibine yükseltilmesi gerekir.

## <a name="how-to-use-powershell-to-upgrade-several-distribution-lists-at-the-same-time"></a>Aynı anda çeşitli dağıtım listelerini yükseltmek için PowerShell'i kullanma

PowerShell kullanma konusunda deneyimliyseniz, kullanıcı arabirimini kullanmak yerine bu yola gitmek isteyebilirsiniz. Dağıtım listelerini yükseltmenize yardımcı olacak bir dizi cmdlet'imiz var. Aşağıya bakın.

### <a name="upgrade-a-single-dl"></a>Tek bir DL'i yükseltme

Tek bir DL'yi yükseltmek için aşağıdaki komutu çalıştırın:

```PowerShell
Upgrade-DistributionGroup -DlIdentities <Dl SMTP address>
```

Örneğin, SMTP adresi dl1@contoso.com bir DL'yi yükseltmek istiyorsanız aşağıdaki komutu çalıştırın:

```PowerShell
Upgrade-DistributionGroup -DlIdentities dl1@contoso.com
```

> [!NOTE]
> [New-UnifiedGroup](/powershell/module/exchange/new-unifiedgroup) PowerShell cmdlet'ini kullanarak tek bir dağıtım listesini Microsoft 365 grubuna da yükseltebilirsiniz

### <a name="upgrade-multiple-dls-in-a-batch"></a>Toplu işlemde birden çok DLL'i yükseltme

Ayrıca birden çok DLL'i toplu iş olarak geçirip birlikte yükseltebilirsiniz:

```PowerShell
Upgrade-DistributionGroup -DlIdentities <DL SMTP address1>, <DL SMTP address2>,
<DL SMTP address3>, <DL SMTP address4>
```

Örneğin, SMTP adresi `dl1@contoso.com` ve , `dl3@contoso.com``dl4@contoso.com` `dl5@contoso.com`ve `dl2@contoso.com`ile beş DLL'yi yükseltmek istiyorsanız aşağıdaki komutu çalıştırın:

```powershell
Upgrade-DistributionGroup -DlIdentities dl1@contoso.com, dl2@contoso.com, dl3@contoso.com, dl4@contoso.com, dl5@contoso.com
```

### <a name="upgrade-all-eligible-dls"></a>Tüm uygun DLL'leri yükseltme

Tüm uygun DLL'leri yükseltmenin iki yolu vardır.

> [!NOTE]
> Upgrade-DistributionGroup cmdlet'i işlem hattından veri almaz, bu nedenle başarıyla çalıştırmak için "foreach-object{}" işlecinin kullanılması gerekir.

1. Kiracıdaki uygun DLL'leri alın ve upgrade komutunu kullanarak yükseltin:

   ```PowerShell
   Get-EligibleDistributionGroupForMigration | Foreach-Object{
       Upgrade-DistributionGroup -DlIdentities $_.PrimarySMTPAddress
   }
   ```

2. Tüm DLL'lerin listesini alın ve yalnızca uygun DLL'leri yükseltin:

   ```PowerShell
   Get-DistributionGroup| Foreach-Object{
       Upgrade-DistributionGroup -DlIdentities $_.PrimarySMTPAddress
   }
   ```

## <a name="faq-about-upgrading-distribution-lists-to-microsoft-365-groups-in-outlook"></a>Outlook'da dağıtım listelerini Microsoft 365 组 yükseltme hakkında SSS

### <a name="which-distribution-lists-cant-be-upgraded"></a>Hangi dağıtım listeleri yükseltilemiyor?

Yalnızca bulut tarafından yönetilen, basit, iç içe olmayan dağıtım listelerini yükseltebilirsiniz. Aşağıdaki tabloda **yükseltilemeyen** dağıtım listeleri listelenmiştir.

|Özellik|Uygun?|
|---|---|
|Şirket içi yönetilen dağıtım listesi.|Hayır|
|İç içe dağıtım listeleri. Dağıtım listesi alt gruplara sahiptir veya başka bir grubun üyesidir.|Hayır|
|**UserMailbox, SharedMailbox**, **TeamMailbox**, **MailUser** dışında **recipientTypeDetails** üyesi olan dağıtım listeleri|Hayır|
|100'den fazla sahibi olan dağıtım listesi|Hayır|
|Yalnızca üyeleri olan ancak sahibi olmayan dağıtım listesi|Hayır|
|Özel karakterler içeren diğer adı olan dağıtım listesi|Hayır|
|Dağıtım listesi Paylaşılan Posta Kutusu için iletme adresi olarak yapılandırılmışsa|Hayır|
|DL, başka bir DL'deki **Gönderen Kısıtlaması'nın** bir parçasıysa.|Hayır|
|Güvenlik grupları|Hayır|
|Dinamik Dağıtım listeleri|Hayır|
|**RoomLists'e** dönüştürülen dağıtım listeleri|Hayır|

### <a name="check-which-dls-are-eligible-for-upgrade"></a>Yükseltme için hangi DLL'lerin uygun olduğunu denetleyin

DL'nin uygun olup olmadığını denetlemek istiyorsanız aşağıdaki komutu çalıştırabilirsiniz:

```PowerShell
Get-DistributionGroup <DL SMTP address> | Get-EligibleDistributionGroupForMigration
```

Yükseltme için hangi DLL'lerin uygun olduğunu denetlemek istiyorsanız aşağıdaki komutu çalıştırmanız yeterlidir:

```PowerShell
Get-EligibleDistributionGroupForMigration
```

### <a name="who-can-run-the-upgrade-scripts"></a>Yükseltme betiklerini Who çalıştırabilirsiniz?

Genel yönetici veya Exchange yönetici haklarına sahip kişiler.

### <a name="why-is-the-contact-card-still-showing-a-distribution-list-what-should-i-do-to-prevent-an-upgraded-distribution-list-from-showing-up-in-my-auto-suggest-list"></a>Kişi kartı neden hala bir dağıtım listesi gösteriyor? Yükseltilmiş bir dağıtım listesinin otomatik öneri listemde gösterilmesini önlemek için ne yapmalıyım?

- Outlook için: Birisi geçiş sonrasında Microsoft 365 grup adını yazarak Outlook'de e-posta göndermeye çalıştığında, alıcı grup yerine dağıtım listesi olarak çözümlenir. Alıcının kişi kartı, dağıtım listeleri kişi kartı olacaktır. Bunun nedeni, Outlook'deki alıcı önbelleği veya nick adı önbelleğidir. E-posta gruba başarıyla gönderilir, ancak gönderenin kafa karışıklığına neden olabilir.<br/>Önbelleği sıfırlamak için [Outlook Otomatik Tamamlama listesi hakkındaki bilgiler adlı](/outlook/troubleshoot/contacts/information-about-the-outlook-autocomplete-list) bu makaledeki adımları gerçekleştirebilirsiniz ve bu da bu sorunu düzeltir.

- Outlook na Web için: Outlook na Web durumunda dağıtım listesi alıcısı önbellekte kalmaya devam eder. Grup kişi kartını görmek için önbelleği yenilemek için [Önerilen adı veya e-posta adresini Otomatik Tamamlama Listesinden kaldırma](https://support.microsoft.com/office/9E1419D9-E88F-445B-B07F-F558B8A37C58) başlığındaki adımları izleyebilirsiniz.

### <a name="do-new-group-members-get-a-welcome-email-in-their-inbox"></a>Yeni grup üyeleri gelen kutularına hoş geldiniz e-postası mı alıyor?

Hayır. Karşılama iletilerini etkinleştirme ayarı varsayılan olarak false olarak ayarlanır. Bu ayar, geçiş tamamlandıktan sonra katılabilecek mevcut ve yeni grup üyelerini etkiler. Grup sahibi daha sonra konuk kullanıcılara izin verirse, konuk kullanıcılar gelen kutularına hoş geldiniz e-postası almaz. Konuk üyeler grupla çalışmaya devam edebilir.

### <a name="what-if-one-or-some-of-the-dls-are-not-upgraded"></a>DLL'lerden biri veya bir kısmı yükseltilmediyse ne olur?

DL'nin uygun olmasına rağmen yükseltilemediği bazı durumlar vardır. DL yükseltilmez ve DL olarak kalır.

- Yöneticinin bir kuruluştaki gruplar için **Grup E-posta Adresi İlkesi** uyguladığı ve ölçütleri karşılamayan DLL'leri yükseltmeye çalıştığı durumlarda, DL yükseltilmez

- **MemberJoinRestriction** veya **MemberDepartRestriction** kapalı olarak ayarlanmış DLL'ler yükseltilemedi 

- Microsoft 365 Grubu oluşturmaya, [bu makaledeki](/microsoft-365/solutions/manage-creation-of-groups) adımlar kullanılarak yalnızca birkaç kullanıcı tarafından izin verilir. Bu senaryoda, dağıtım listesinin sahibinin Microsoft 365 Grubu oluşturmasına izin verilmiyorsa, dağıtım listesi Microsoft 365 Grubuna yükseltilmeyecektir.
Geçici çözüm: Yukarıdaki senaryo için aşağıdaki geçici çözümlerden birini kullanın:

1. DL'nin sahibi olarak bahsedilen tüm kullanıcıların M365 Grubu oluşturmasına izin verildiğinden, yani M365 Grubu'na izin verilen güvenlik grubunun üyesi olduğundan emin olun.

   VEYA

2. Geçici olarak, M365 Grubu oluşturmasına izin verilmeyen DL'nin sahibini M365 Grubu oluşturmasına izin verilen kullanıcıyla değiştirin.

### <a name="what-happens-to-the-dl-if-the-upgrade-from-eac-fails"></a>EAC'den yükseltme başarısız olursa DL'ye ne olur?

Yükseltme yalnızca çağrı sunucuya gönderildiğinde gerçekleşir. Yükseltme başarısız olursa, DLL'leriniz bozulmaz. Eskiden olduğu gibi çalışacaklar.

### <a name="what-happens-to-message-approval-moderation-settings-on-distribution-groups-after-upgrading"></a>Yükseltmeden sonra dağıtım gruplarında ileti onayı (denetim) ayarlarına ne olur?

İleti onayı (denetim) ayarları korunur ve dağıtım grubu bir Microsoft 365 Grubuna yükseltildikten sonra düzgün çalışmaya devam eder.

## <a name="related-content"></a>İlgili içerik

[Grupları karşılaştırma](../create-groups/compare-groups.md) (makale)\
[Kullanıcılarınıza Microsoft 365 组 açıklama](../create-groups/explain-groups-knowledge-worker.md) (makale)\
[Yönetim merkezini kullanarak Microsoft 365 gruplarına üye ekleme veya gruptan üye kaldırma](../create-groups/add-or-remove-members-from-groups.md)
