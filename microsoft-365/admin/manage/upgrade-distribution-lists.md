---
title: Dağıtım listelerini Outlook'Microsoft 365 Gruplarına yükseltme
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
description: Outlook'ta grup gruplarına bir veya Microsoft 365 dağıtım listelerini yükseltmeyi ve aynı anda birkaç dağıtım listelerini yükseltmek için PowerShell'i kullanmayı öğrenin.
ms.openlocfilehash: 7a6e0eff49958b99df9ca59702b814b364aefb46
ms.sourcegitcommit: 27eb93a7d46bcbb9c948a50b0a8481ffd3832ca0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/28/2021
ms.locfileid: "63028356"
---
# <a name="upgrade-distribution-lists-to-microsoft-365-groups-in-outlook"></a>Dağıtım listelerini Outlook'Microsoft 365 Gruplarına yükseltme

Dağıtım listelerini, aynı Microsoft 365 Gruplarına Outlook. Bu, tüm kuruluş gruplarında yer alan dağıtım listelerinin tüm özelliklerini ve işlevlerini sağlamak için Microsoft 365 birdir. [Neden Outlook'ta dağıtım listelerinizi gruplara yükseltmelisiniz?](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188)

DL'leri tek tek veya aynı anda birkaç DL'ye yükseltebilirsiniz.

## <a name="upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Bir veya birçok dağıtım listesi listesini farklı bir Microsoft 365 Gruplarına Outlook

Dağıtım listesi grubunu yükseltmek için genel yönetici Exchange yönetici veya yönetici olasınız. Dağıtım Grupları'Microsoft 365 yükseltmek için, dağıtım listesi grubunun posta kutusu olan bir sahibi olması gerekir.

### <a name="use-the-new-eac-to-upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Yeni EAC'i kullanarak bir veya birçok dağıtım listesi listesini aynı Microsoft 365 grupları Outlook

1. Alıcılar Grupları'Exchange yönetim > **gidin** \> <a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank">.</a>

2. Gruplar sayfasından grup grubuna yükseltmek istediğiniz dağıtım listesi grubunu (dağıtım grubu olarak Microsoft 365 **) seçin.**

3. Araç **çubuğundan Dağıtım grubunu** yükselt'i seçin.

4. Yükseltmeye hazır mısınız **? iletişim kutusunda Yükselt'e** **tıklayın**. İşlem hemen başlar. Yükseltmeyi kullandığınız dağıtım listesi gruplarının boyutuna ve sayısına bağlı olarak, işlem dakika veya saat sürebilir.

> [!NOTE]
> Üst başlıkta yer alan başlık, örneğin Dağıtım grubunun *yükseltil olduğunu gösterir. Değişiklikleri yansıtmak 5 dakika sürer. Yükseltilen dağıtım Microsoft 365 görmek için gruplara göre filtre uygulama*.

### <a name="use-the-classic-eac-to-upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Klasik EAC'i kullanarak bir veya birçok dağıtım listesi gruplarını aynı gruptaki Microsoft 365 için Outlook

1. Alıcı Grupları'Exchange yönetim > **gidin**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a><br/>Grup Gruplarında yükseltmeye uygun dağıtım listelerine (dağıtım grupları olarak da **denir) sahip** olduğunu belirten bir Microsoft 365 bakın.<br/> ![Çalışmaya başla düğmesini seçin.](../../media/8cf838b4-2644-401f-a366-08c1eea183eb.png)

1. Gruplar sayfasından bir veya birden çok dağıtım listesi ( **dağıtım grubu** olarak da **adlandırılan)** seçin.<br/>![Bir dağıtım grubu seçin.](../../media/2c303433-d60b-4100-a6ae-5809b03a8cdb.png)

1. Yükseltme simgesini seçin.<br/>![Gruplara Microsoft 365 yükseltin.](../../media/1e28cb3d-bff3-4be3-8329-1902d2d54720.png)

1. Bilgi iletişim kutusunda, yükseltmeyi onaylamak **için Evet'i** seçin. İşlem hemen başlar. Yükseltmekte bulunduğunuz DL'nin boyutuna ve sayısına bağlı olarak, işlem dakika veya saat sürebilir.<br/>Dağıtım listesi yükseltilemiyorsa, bunu söyleyen bir iletişim kutusu görüntülenir. Bkz[. Hangi dağıtım listeleri yükseltilemiyor?](#which-distribution-lists-cant-be-upgraded)

1. Birden çok dağıtım listesini yükseltirken, yükseltilen dağıtım listelerini filtrelemek için açılan listeyi kullanın. Liste tamamlanmadısa, biraz daha bekleyin ve ardından başarıyla yükseltilenleri  görmek için Yenile'yi seçin.<br/>Seçtiğiniz tüm URL'ler için yükseltme işleminin ne zaman tamamlandıktan sonra bunu size söyleyen bir bildirim yoktur. Bunu, Yükseltme için kullanılabilir veya Yükseltilmiş DL'ler altında **nelerin listelenmiş olduğunu** **görerek anabilirsiniz**.

1. Yükseltme için bir DL seçtiysanız, ancak yükseltme için kullanılabilir olarak sayfada hala karşı çıktı ve yükseltme başarısız oldu. Bkz [. Yükseltme işe yaramadı mı](#what-to-do-if-the-upgrade-doesnt-work)?

> [!NOTE]
> Grupların özet e-postalarını alıyorsanız, en altta bu e-postanın bazen sahibi olduğunuz uygun dağıtım listelerini yükseltmenizi teklif e-posta olarak farkedebilirsiniz. Özet [e-postaları hakkında daha fazla bilgi Outlook](https://support.microsoft.com/office/a0482e24-a769-4e39-a5ba-a7c56e828b22) için bkz. E-postalarda grup görüşmesi yapmak.

## <a name="what-to-do-if-the-upgrade-doesnt-work"></a>Yükseltme işe yaramadı mı?

Yükseltmesi başarısız olan dağıtım listeleri değişmeden kalır.

Bir veya birden **çok uygun** dağıtım listesi yükseltilenene kadar, 

1. Dağıtım [listesinin](https://aka.ms/DLToM365Group) Microsoft 365 grubuna yükseltilmesine engel olacak olası sorunları taramak, betik tarafından bildirilen sorunları düzeltmek ve dağıtım listesini bir kez daha yükseltmeyi denemek için bu betiği kullanın. 

2. Yukarıdaki betiğin bir yardımı yoksa veya sorun devam ederse bir Destek [bileti açın](../../business-video/get-help-support.md). Onların sorunu an önce çözmeleri için bu sorunun Gruplar Mühendislik ekibine ednleri gerekir.

## <a name="how-to-use-powershell-to-upgrade-several-distribution-lists-at-the-same-time"></a>Aynı anda birkaç dağıtım listelerini yükseltmek için PowerShell kullanma

PowerShell kullanırken deneyimliysiniz, kullanıcı arabirimi yerine bu yönlendirmeye gitmek istiyor olabilirsiniz. Dağıtım listelerini yükseltmeniz için size yardımcı olacak bir dizi cmdlet'imiz var. Aşağıya bakın.

### <a name="upgrade-a-single-dl"></a>Tek bir DL'ye yükseltme

Tek bir DL'ye yükseltmek için aşağıdaki komutu çalıştırın:

```PowerShell
Upgrade-DistributionGroup -DlIdentities <Dl SMTP address>
```

Örneğin, SMTP adres defterine sahip bir DL'ye yükseltmek dl1@contoso.com aşağıdaki komutu çalıştırın:

```PowerShell
Upgrade-DistributionGroup -DlIdentities dl1@contoso.com
```

> [!NOTE]
> Ayrıca, [New-UnifiedGroup](/powershell/module/exchange/new-unifiedgroup) PowerShell cmdlet'ini Microsoft 365 dağıtım listesine yükseltebilirsiniz

### <a name="upgrade-multiple-dls-in-a-batch"></a>Bir toplu işlemde birden çok DL'ye yükseltme

Ayrıca toplu işlem olarak birden çok DL'ye geçiş ve bunları birlikte yükseltebilirsiniz:

```PowerShell
Upgrade-DistributionGroup -DlIdentities <DL SMTP address1>, <DL SMTP address2>,
<DL SMTP address3>, <DL SMTP address4>
```

Örneğin, SMTP `dl1@contoso.com` `dl4@contoso.com` `dl2@contoso.com``dl3@contoso.com`adresi ve , ile birlikte beş DL'ye yükseltmek için `dl5@contoso.com`aşağıdaki komutu çalıştırın:

`Upgrade-DistributionGroup -DlIdentities dl1@contoso.com, dl2@contoso.com, dl3@contoso.com, dl4@contoso.com, dl5@contoso.com`

### <a name="upgrade-all-eligible-dls"></a>Tüm uygun DL'leri yükseltme

Tüm uygun DL'leri iki şekilde yükseltebilirsiniz.

> [!NOTE]
> Upgrade-DistributionGroup cmdlet'i ardışık düzenden veri almaz, bu nedenle başarılı bir şekilde çalıştırmak için "foreach-object{}" işlecinin zorunludur.

1. Kiracıya uygun DL'leri almak ve yükseltme komutunu kullanarak yükseltmek için:

```PowerShell
Get-EligibleDistributionGroupForMigration | Foreach-Object{
    Upgrade-DistributionGroup -DlIdentities $_.PrimarySMTPAddress
}
```

2. Tüm DL'lerin listesini al ve yalnızca uygun DL'leri yükselt:

```PowerShell
Get-DistributionGroup| Foreach-Object{
    Upgrade-DistributionGroup -DlIdentities $_.PrimarySMTPAddress
}
```

## <a name="faq-about-upgrading-distribution-lists-to-microsoft-365-groups-in-outlook"></a>Outlook'de Dağıtım listelerini Microsoft 365 Gruplarına yükseltme hakkında SSS

### <a name="which-distribution-lists-cant-be-upgraded"></a>Hangi dağıtım listeleri yükseltilemiyor?

Yalnızca bulut tarafından yönetilen, basit, iç içe olmayan dağıtım listelerini yükseltebilirsiniz. Aşağıdaki tabloda yükseltililemez dağıtım **listeleri** listelenmiştir.

|**Özellik**|**Uygun musunuz?**|
|:-----|:-----|
|Şirket içi yönetilen dağıtım listesi.  <br/> |Hayır  <br/> |
|İç içe dağıtım listeleri. Dağıtım listesinin alt grupları vardır veya başka bir grubun üyesidir.  <br/> |Hayır  <br/> |
|**UserMailbox, SharedMailbox**, **TeamMailbox**, **MailUser** dışında üye **RecipientTypeDetails** **ile** dağıtım listeleri  <br/> |Hayır  <br/> |
|100'den fazla sahibi olan dağıtım listesi  <br/> |Hayır  <br/> |
|Yalnızca üyeleri olan ancak sahibi olmadığınız dağıtım listesi  <br/> |Hayır  <br/> |
|Özel karakterler içeren diğer ad içeren dağıtım listesi  <br/> |Hayır  <br/> |
|Dağıtım listesi Paylaşılan Posta Kutusu için bir iletme adresi olacak şekilde yapılandırılmışsa  <br/> |Hayır  <br/> |
|DL, başka bir **DL'de Gönderen Kısıtlaması'nın** parçası ise.  <br/> |Hayır  <br/> |
|Güvenlik grupları  <br/> |Hayır  <br/> |
|Dinamik Dağıtım listeleri  <br/> |Hayır  <br/> |
|OdaListeleri'ne **dönüştürülmüş dağıtım listeleri**  <br/> |Hayır  <br/> |

### <a name="check-which-dls-are-eligible-for-upgrade"></a>Hangi DL'lerin yükseltme için uygun olduğunu denetleme

DL'nin uygun olup olmadığını kontrol etmek için aşağıdaki komutu çalıştırabilirsiniz:

`Get-DistributionGroup <DL SMTP address> | Get-EligibleDistributionGroupForMigration`

Hangi DL'lerin yükseltmeye uygun olduğunu kontrol etmek için aşağıdaki komutu çalıştırın:

`Get-EligibleDistributionGroupForMigration`

### <a name="who-can-run-the-upgrade-scripts"></a>Who betiklerini nasıl çalıştırabilirsiniz?

Genel yönetici veya yönetici Exchange kişiler.

### <a name="why-is-the-contact-card-still-showing-a-distribution-list-what-should-i-do-to-prevent-an-upgraded-distribution-list-from-showing-up-in-my-auto-suggest-list"></a>Kişi kartı neden hala bir dağıtım listesi gösteriyor? Yükseltilen bir dağıtım listesinin otomatik öneri listemde  gösterilemesini engellemek için ne yapabilirim?

- Örneğin Outlook: Birisi geçiş sonrasında Outlook adını yazarak Microsoft 365 e-posta göndermeye çalıştığında, alıcı grup yerine dağıtım listesi olarak çözümlenir. Alıcının kişi kartı, dağıtım listeleri kişi kartı olur. Bunun nedeni, dosyada alıcı önbelleği veya takma ad önbelleğinin Outlook. E-posta gruba başarıyla gönderilir, ancak gönderende karışıklığa neden olabilir.<br/>Bu makaledeki adımları, önbelleği sıfırlamak [için Outlook](/outlook/troubleshoot/contacts/information-about-the-outlook-autocomplete-list) Otomatik Tamamlama listesi hakkında bilgiler bulabilirsiniz. Bu, sorunu çözecektir.

- Örneğin Web üzerinde Outlook: Dağıtım listesi Web üzerinde Outlook, dağıtım listesi alıcısı yine de önbellekte kalır. Grup kişi kartını görmek üzere [önbelleği yenilemek için](https://support.microsoft.com/office/9E1419D9-E88F-445B-B07F-F558B8A37C58) , Önerilen adı veya e-posta adresini Otomatik Tamamlama Listesi'den kaldırma'daki adımları izleyin.

### <a name="do-new-group-members-get-a-welcome-email-in-their-inbox"></a>Yeni grup üyeleri gelen kutularında bir karşılama e-postası mı alır?

Hayır. Hoş geldiniz iletilerini etkinleştirme ayarı varsayılan olarak yanlış değerine ayarlanmıştır. Bu ayar, geçiş tamamlandıktan sonra katıl isteyen mevcut ve yeni grup üyelerini etkiler. Grup sahibi daha sonra konuk kullanıcılara izin verirse, konuk kullanıcılar gelen kutularında bir hoş geldiniz e-postası almaz. Konuk üyeler grupla çalışmaya devam eder.

### <a name="what-if-one-or-some-of-the-dls-are-not-upgraded"></a>Bir veya bazı DL'ler yükseltilmezse ne olacak?

Bazı durumlarda DL uygundur ancak yükseltilemez. DL yükseltilmez ve DL olarak kalır.

- Yöneticinin bir kuruluşta **yer** alan gruplara Grup E-posta Adresi İlkesi'ni uygulaması ve ölçütleri karşılamayan DL'leri yükseltmeyi denemesi halinde, DL yükseltilmez

- **MemberJoinRestriction** veya **MemberDepartRestriction** kapalı olarak ayarlanmış DLS'ler yükseltilemdi 

- Grup Microsoft 365, bu makaledeki adımlar kullanılarak yalnızca birkaç kullanıcıya [izin verilir](/microsoft-365/solutions/manage-creation-of-groups). Bu senaryoda, dağıtım listesinin sahibinin Dağıtım Grubu oluşturmasına izin Microsoft 365, dağıtım listesi Microsoft 365 yükseltmez. Geçici çözüm: Yukarıdaki senaryo için aşağıdaki geçici çözümden birini kullanın:
1)  DL sahibi olarak sözü geçen tüm kullanıcıların M365 Grubu oluşturmasına izin verili, örneğin, M365 Grubuna izin verilen güvenlik grubunun üyesi olduğundan emin olur.
VEYA
2)  Geçici olarak, M365 Grubu oluşturmasına izin verilmiyor DL'nin sahibini M365 Grubu oluşturma izni olan kullanıcıyla değiştirin

### <a name="what-happens-to-the-dl-if-the-upgrade-from-eac-fails"></a>EAC'den yükseltme başarısız olursa DL'ye ne olur?

Yükseltme, ancak arama sunucuya gönderilebilir. Yükseltme başarısız olursa, URL'leri korunur. Her zaman olduğu gibi çalışırlar.

## <a name="related-content"></a>İlgili içerik

[Grupları karşılaştırma](../create-groups/compare-groups.md) (makale)\
[Kullanıcılarınıza Microsoft 365 Grupları Açıklama](../create-groups/explain-groups-knowledge-worker.md) (makale)\
[Yönetim merkezini kullanarak gruplarda Microsoft 365 ekleme veya kaldırma](../create-groups/add-or-remove-members-from-groups.md)
