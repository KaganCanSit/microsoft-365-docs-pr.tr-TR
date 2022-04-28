---
title: Microsoft 365 için neden PowerShell kullanmanız gerekiyor?
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 07/17/2020
audience: ITPro
ms.topic: overview
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: admindeeplinkEXCHANGE
ms.assetid: b3209b1a-40c7-4ede-8e78-8a88bb2adc8a
description: 'Özet: Microsoft 365 yönetmek için neden PowerShell kullanmanız gerektiğini, bazı durumlarda daha verimli ve diğer durumlarda gerekliliği anlayın.'
ms.openlocfilehash: 114b97ff27ae1b79e58589eb746a261f83dc422f
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097942"
---
# <a name="why-you-need-to-use-powershell-for-microsoft-365"></a>Microsoft 365 için neden PowerShell kullanmanız gerekiyor?

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Microsoft 365 yönetim merkezi ile Microsoft 365 kullanıcı hesaplarınızı ve lisanslarınızı yönetebilirsiniz. Exchange Online, Teams ve SharePoint Online gibi Microsoft 365 hizmetlerinizi de yönetebilirsiniz. Bunun yerine bu hizmetleri yönetmek için PowerShell kullanıyorsanız hız, otomasyon ve ek özellikler için komut satırı ve betik dili ortamından yararlanabilir ve bu ortamdan yararlanabilirsiniz.

Bu makalede, powershell kullanarak Microsoft 365 nasıl yönetileceğini gösterir:

- Microsoft 365 yönetim merkezi göremediğiniz ek bilgileri gösterme

- Özellikleri ve ayarları yalnızca PowerShell ile yapılandırma

- Toplu işlemler yapma

- Verileri filtreleme

- Verileri yazdırma veya kaydetme

- Hizmetler arasında yönetme

Microsoft 365 için PowerShell'in Windows tabanlı hizmetler ve platformlar için bir komut satırı ortamı olan Windows PowerShell için bir dizi modül olduğunu unutmayın. Bu ortam, ek modüllerle genişletilebilen bir komut kabuğu dili oluşturur. Basit veya karmaşık komutlar veya betikler yürütmek için bir yol sağlar. Örneğin, Microsoft 365 modülleri için PowerShell'i yükledikten ve Microsoft 365 aboneliğinize bağlandıktan sonra, Microsoft Exchange Online tüm kullanıcı posta kutularını listelemek için aşağıdaki komutu çalıştırabilirsiniz:

```powershell
Get-Mailbox
```

Posta kutularının listesini Microsoft 365 yönetim merkezi kullanarak da alabilirsiniz, ancak tüm web uygulamalarınız için tüm siteler için tüm listelerdeki öğeleri saymak kolay değildir.

Microsoft 365 için PowerShell, Microsoft 365 yönetim merkezi değiştirmek yerine Microsoft 365 yönetmenize yardımcı olmak için tasarlanmıştır. Yalnızca Microsoft 365 komutlar için PowerShell aracılığıyla gerçekleştirilebilecek bazı yapılandırma yordamları olduğundan yöneticilerin Microsoft 365 için PowerShell'i kullanabilmesi gerekir. Bu durumlarda şunların nasıl yapılacağını bilmeniz gerekir:

- Microsoft 365 modülleri için PowerShell'i yükleyin (her yönetici bilgisayar için yalnızca bir kez yapılır).

- Microsoft 365 aboneliğinize (her PowerShell oturumu için bir kez) Bağlan.

- Microsoft 365 komutları için gerekli PowerShell'i çalıştırmak için gereken bilgileri toplayın.

- Microsoft 365 komutları için PowerShell'i çalıştırın.

Bu temel becerileri öğrendikte, **Posta Kutusu Al** komutunu kullanarak posta kutusu kullanıcılarınızı listelemeniz gerekmez. Ayrıca, tüm web uygulamalarınız için tüm sitelerin tüm listelerindeki tüm öğeleri saymak için daha önce alıntı yapılan komut gibi yeni bir komutun nasıl oluşturulacağını da anlamanız gerekmez. Microsoft ve yöneticiler topluluğu, gerektiğinde bu tür görevlerde size yardımcı olabilir.

## <a name="powershell-for-microsoft-365-can-reveal-information-that-you-cant-see-with-the-microsoft-365-admin-center"></a>Microsoft 365 için PowerShell, Microsoft 365 yönetim merkezi ile göremediğiniz bilgileri açabilir

Microsoft 365 yönetim merkezi birçok yararlı bilgi görüntüler. Ancak kullanıcılar, lisanslar, posta kutuları ve siteler hakkında Microsoft 365 tüm olası bilgileri görüntülemez. Microsoft 365 yönetim merkezi *kullanıcılar ve gruplar* için bir örnek aşağıda verilmiştır:

![Microsoft 365 yönetim merkezi kullanıcıların ve grupların görüntülenmesi örneği.](../media/o365-powershell-users-and-groups.png)

Bu görünüm, birçok durumda ihtiyacınız olan bilgileri sağlar. Ancak, daha fazlasına ihtiyaç duyduğunuz zamanlar vardır. Örneğin, Microsoft 365 lisanslama (ve kullanıcının kullanabileceği Microsoft 365 özellikleri) kısmen kullanıcının coğrafi konumuna bağlıdır. Birleşik Devletler yaşayan bir kullanıcıya genişletebileceğiniz ilkeler ve özellikler, Hindistan veya Belçika'daki bir kullanıcıya genişletebileceğiniz ilkeler ve özelliklerle aynı olmayabilir. Kullanıcının coğrafi konumunu belirlemek için Microsoft 365 yönetim merkezi şu adımları izleyin:

1. Kullanıcının **Görünen Adı'na** çift tıklayın.

2. Kullanıcı özellikleri görüntüleme bölmesinde **ayrıntılar'ı** seçin.

3. Ayrıntılar ekranında **ek ayrıntılar'ı** seçin.

4. **Ülke veya bölge** başlığını bulana kadar kaydırın:

     ![Microsoft 365 yönetim merkezi bir kullanıcının bölge bilgileri örneği.](../media/o365-powershell-usage-location.png)

5. Kullanıcının görünen adını ve konumunu bir kağıda yazın veya kopyalayıp Not Defteri yapıştırın.

Bu yordamı her kullanıcı için yinelemeniz gerekir. Çok sayıda kullanıcınız varsa, bu işlem yorucu olabilir. Microsoft 365 için PowerShell ile aşağıdaki komutu kullanarak tüm kullanıcılarınız için bu bilgileri görüntüleyebilirsiniz:

```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```


>[!Note]
>PowerShell Core, Windows PowerShell modülü için Microsoft Azure Active Directory Modülünü ve adında *Msol* bulunan cmdlet'leri desteklemez. Bu cmdlet'leri Windows PowerShell çalıştırmanız gerekir.
>

İşte sonuçlara bir örnek:

```powershell
DisplayName                               UsageLocation
-----------                               -------------
Bonnie Kearney                            GB
Fabrice Canel                             BR
Brian Johnson (TAILSPIN)                  US
Anne Wallace                              US
Alex Darrow                               US
David Longmuir                            BR
```

Bu PowerShell komutunun yorumu şöyledir: Geçerli Microsoft 365 aboneliğindeki tüm kullanıcıları alın (**Get-AzureADUser**), ancak yalnızca her kullanıcının adını ve konumunu görüntüleyin (**DisplayName, UsageLocation'ı seçin**).

Microsoft 365 için PowerShell komut kabuğu dilini desteklediğinden, **Get-AzureADUser** komutuyla elde edilen bilgileri daha fazla işleyebilirsiniz. Örneğin, bu kullanıcıları konumlarına göre sıralamak, tüm Brezilyalı kullanıcıları birlikte gruplandırmak, tüm Birleşik Devletler kullanıcıları birlikte gruplandırmak vb. Komut şu şekildedir:

```powershell
Get-AzureADUser | Select DisplayName, UsageLocation | Sort UsageLocation, DisplayName
```

İşte sonuçlara bir örnek:

```powershell
DisplayName                                 UsageLocation
-----------                                 -------------
David Longmuir                              BR
Fabrice Canel                               BR
Bonnie Kearney                              GB
Alex Darrow                                 US
Anne Wallace                                US
Brian Johnson (TAILSPIN)                    US
```

Bu PowerShell komutunun yorumu şöyledir: Geçerli Microsoft 365 aboneliğindeki tüm kullanıcıları alın, ancak yalnızca her kullanıcının adını ve konumunu görüntüleyin ve önce konumlarına ve sonra adlarına göre sıralayın (**Sort UsageLocation, DisplayName**).

Ek filtreleme de kullanabilirsiniz. Örneğin, yalnızca Brezilya'da bulunan kullanıcılar hakkında bilgi görmek istiyorsanız şu komutu kullanın:

```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq "BR"} | Select DisplayName, UsageLocation
```

İşte sonuçlara bir örnek:

```powershell
DisplayName                                           UsageLocation
-----------                                           -------------
David Longmuir                                        BR
Fabrice Canel                                         BR
```

Bu PowerShell komutunun yorumu şöyledir: Geçerli Microsoft 365 aboneliğindeki konumu Brezilya olan tüm kullanıcıları alın (**Burada {$\_). UsageLocation -eq "BR"}**) ve ardından her kullanıcının adını ve konumunu görüntüleyin.

 **Büyük etki alanları hakkında bir not**

On binlerce kullanıcı içeren büyük bir etki alanınız varsa, bu makalede gösterdiğimiz örneklerden bazılarını denemek azaltmaya neden olabilir. İşlem gücü ve kullanılabilir ağ bant genişliği gibi faktörlere bağlı olarak, aynı anda çok fazla şey yapmaya çalışıyor olabilirsiniz. Büyük kuruluşlar bu PowerShell işlemlerinden bazılarını iki komut olarak bölmek isteyebilir.

Örneğin, aşağıdaki komut tüm kullanıcı hesaplarını döndürür ve her birine ilişkin adı ve konumu gösterir:

```powershell
Get-AzureADUser | Select DisplayName, UsageLocation
```

Bu, daha küçük etki alanları için harika çalışır. Ancak büyük bir kuruluşta bu işlemi iki komuta bölmek isteyebilirsiniz: kullanıcı hesabı bilgilerini bir değişkende depolamak için bir komut ve gerekli bilgileri görüntülemek için başka bir komut. İşte bir örnek:

```powershell
$x = Get-AzureADUser
$x | Select DisplayName, UsageLocation
```

Bu PowerShell komut kümesinin yorumu şöyledir:
1. Geçerli Microsoft 365 aboneliğindeki tüm kullanıcıları alın ve bilgileri $x (**$x = Get-AzureADUser**) adlı bir değişkende depolayın.
1.  *$x* değişkeninin içeriğini görüntüleyin, ancak yalnızca her kullanıcının adını ve konumunu ekleyin (**$x | DisplayName, UsageLocation'ı seçin**).

## <a name="microsoft-365-has-features-that-you-can-only-configure-with-powershell-for-microsoft-365"></a>Microsoft 365 yalnızca Microsoft 365 için PowerShell ile yapılandırabileceğiniz özelliklere sahiptir

Microsoft 365 yönetim merkezi, çoğu ortam için geçerli olan yaygın, yararlı yönetim görevlerine erişim sağlamak için tasarlanmıştır. Başka bir deyişle, Microsoft 365 yönetim merkezi tipik yöneticinin en yaygın yönetim görevlerini gerçekleştirebilmesi için tasarlanmıştır. Ancak yönetim merkezinde yapılamaz bazı görevler vardır.

Örneğin, Skype Kurumsal Online yönetim merkezi özel toplantı davetleri oluşturmak için birkaç seçenek sağlar:

![Skype Kurumsal Online Yönetim merkezinde özel toplantı davetlerinin görüntülenmesi örneği.](../media/o365-powershell-meeting-invitation.png)

Bu ayarlarla toplantı davetlerine kişiselleştirme ve profesyonellik dokunuşu ekleyebilirsiniz. Ancak, yalnızca özel toplantı davetleri oluşturmak yerine toplantı yapılandırma ayarlarından daha fazlası vardır. Örneğin, varsayılan olarak toplantılar şunları sağlar:

- Her toplantıya otomatik giriş elde etmek için anonim kullanıcılar.

- Toplantıyı kaydedecek katılımcılar.

- Kuruluşunuzdaki tüm kullanıcılar toplantıya katıldıklarında sunucu olarak belirlenecek.

Bu ayarlar Skype Kurumsal Çevrimiçi yönetim merkezinde kullanılamaz. Bunları Microsoft 365 için PowerShell'den denetleyebilirsiniz. Bu üç ayarı devre dışı bırakmaya yönelik bir komut aşağıdadır:

```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $False -AllowConferenceRecording $False -DesignateAsPresenter "None"
```

> [!NOTE]
> Bu komutu çalıştırmak için [Skype Kurumsal Online PowerShell Modülünü](https://www.microsoft.com/download/details.aspx?id=39366) yüklemeniz gerekir.

Bu PowerShell komutunun yorumu şöyledir:

1. Yeni Skype Kurumsal Çevrimiçi toplantıların ayarlarında (**Set-CsMeetingConfiguration**), anonim kullanıcıların toplantılara otomatik giriş yapmalarına izin verme özelliğini devre dışı bırakın (**-AdmitAnonymousUsersByDefault $False**).
2.  Katılımcıların toplantıları kaydetme özelliğini devre dışı bırakın (**-AllowConferenceRecording $False**).
3. Kuruluşunuzdan tüm kullanıcıları sunucu olarak belirlemeyin (**-DesignateAsPresenter "Yok"**).

Bu varsayılan ayarları geri yüklemek (seçenekleri etkinleştirmek) için şu komutu çalıştırın:

```powershell
Set-CsMeetingConfiguration -AdmitAnonymousUsersByDefault $True -AllowConferenceRecording $True -DesignateAsPresenter "Company"
```

Benzer başka senaryolar da vardır. Bu nedenle yöneticiler, Microsoft 365 komutlar için PowerShell'i nasıl çalıştıracaklarını bilmelidir.

## <a name="powershell-for-microsoft-365-is-great-for-bulk-operations"></a>Microsoft 365 için PowerShell, toplu işlemler için harikadır

Microsoft 365 yönetim merkezi gibi görsel arabirimler, yapmanız gereken tek bir işlem olduğunda en değerlidir. Örneğin, bir kullanıcı hesabını devre dışı bırakmanız gerekiyorsa, bir onay kutusunu hızla bulup temizlemek için yönetim merkezini kullanabilirsiniz. Bu, PowerShell'de benzer bir işlem gerçekleştirmekten daha kolay olabilir.

Ancak, büyük bir dizi başka şey içinde birçok şeyi veya bazı seçili öğeleri değiştirmeniz gerekiyorsa, Microsoft 365 yönetim merkezi en iyi araç olmayabilir. Örneğin, binlerce telefon numarasındaki ön eki değiştirmeniz veya belirli bir kullanıcı *olan Ken Myer'ı* tüm SharePoint Çevrimiçi sitelerinden kaldırmanız gerekeceğini varsayalım. bunu Microsoft 365 yönetim merkezi nasıl yaparsın?

Son örnekte, birkaç yüz SharePoint Çevrimiçi siteniz olduğunu ve Ken Meyer'in hangilerinin üyesi olduğunu bilmediğinizi varsayalım. Microsoft 365 yönetim merkezi başlayıp her site için şu yordamı uygulamanız gerekir:

1. Sitenin **URL'sini** seçin.

2. **Site koleksiyonu özellikleri** kutusunda **Web Sitesi Adresi** bağlantısını seçerek siteyi açın.

3. Sitede **Paylaş'ı** seçin.

4. **Paylaş** iletişim kutusunda, site üzerinde izinleri olan tüm kullanıcıları gösteren bağlantıyı seçin:

     ![SharePoint Online Yönetim merkezinde bir SharePoint Online sitesinin üyelerini görüntüleme örneği.](../media/o365-powershell-view-permissions.png)

5. **Paylaşılan** iletişim kutusunda **Gelişmiş'i** seçin.

6. Kullanıcı listesini aşağı kaydırın, Ken Myer'ı bulun ve seçin (site izinleri olduğu varsayılarak) ve ardından **Kullanıcı İzinlerini Kaldır'ı** seçin.

Bu, birkaç yüz site için *uzun* sürebilir.

Alternatif olarak, Ken Myer'ı tüm sitelerinden kaldırmak üzere Microsoft 365 için PowerShell'de aşağıdaki komutu çalıştırmaktır:

```powershell
Get-SPOSite | ForEach {Remove-SPOUser -Site $_.Url -LoginName "kenmyer@litwareinc.com"}
```

> [!NOTE]
> Bu komut[, SharePoint Online PowerShell modülünü](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) yüklemenizi gerektirir.

Bu PowerShell komutunun yorumu şöyledir: Geçerli Microsoft 365 aboneliğindeki (**Get-SPOSite**) tüm SharePoint sitelerini alın ve her site için Ken Meyer'i buna erişebilen kullanıcılar listesinden kaldırın (**ForEach {Remove-SPOUser -Site $\_). Url -LoginName "kenmyer\@ litwareinc.com"}**).

Microsoft 365 Ken Meyer'i erişimi olmayanlar da dahil olmak üzere her siteden kaldırmasını söyleriz. Bu nedenle sonuçlar, erişimi olmayan sitelerle ilgili hatalar gösterir. Ken Meyer'i yalnızca oturum açma listelerinde bulunan sitelerden kaldırmak için bu komutta ek bir koşul kullanabiliriz. Ancak döndürülen hatalar sitelerin kendilerine zarar vermez. Bu komutun yüzlerce site üzerinde çalışması birkaç dakika sürebilir, Microsoft 365 yönetim merkezi üzerinden çalışma saatleri yerine.

İşte başka bir toplu işlem örneği. Yeni bir SharePoint yöneticisi *olan Bonnie Kearney'i* kuruluştaki tüm sitelere eklemek için bu komutu kullanın:

```powershell
Get-SPOSite | ForEach {Add-SPOUser -Site $_.Url -LoginName "bkearney@litwareinc.com" -Group "Members"}
```

Bu PowerShell komutunun yorumu şöyledir: Geçerli Microsoft 365 aboneliğindeki tüm SharePoint siteleri alın ve her site için bonnie Kearney'e sitenin Üyeler grubuna oturum açma adını ekleyerek erişim izni verin (**ForEach {Add-SPOUser -Site $\_). Url -LoginName "bkearney\@ litwareinc.com" -Group "Members"}**).

## <a name="powershell-for-microsoft-365-is-great-at-filtering-data"></a>Microsoft 365 için PowerShell, verileri filtreleme konusunda harikadır

Microsoft 365 yönetim merkezi, hedeflenen bir bilgi alt kümesini kolayca bulmak için verilerinizi filtrelemek için çeşitli yollar sağlar. Örneğin Exchange, kullanıcı posta kutusunun hemen her özelliğine göre filtrelemeyi kolaylaştırır. Örneğin, Bloomington şehrinde yaşayan tüm kullanıcıların posta kutularının listesi aşağıdadır:

![Bloomington şehrinde yaşayan tüm kullanıcıların posta kutuları listesi için Microsoft 365 yönetim merkezi gelişmiş arama yapma örneği.](../media/o365-powershell-advanced-search.png)

<a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezi</a>, filtre ölçütlerini birleştirmenizi de sağlar. Örneğin, Bloomington'da yaşayan ve Finans departmanında çalışan tüm kişilerin posta kutularını bulabilirsiniz.

Ancak, Exchange Yönetim merkezinde yapabileceklerinin sınırlamaları vardır. Örneğin, Bloomington veya San Diego'da yaşayan kişilerin posta kutularını *veya* Bloomington'da yaşamayan tüm kişilerin posta kutularını kolayca bulamazsınız.

Bloomington veya San Diego'da yaşayan tüm kişilerin posta kutularının listesini almak için aşağıdaki Microsoft 365 için PowerShell komutunu kullanabilirsiniz:

```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and ($_.City -eq "San Diego" -or $_.City -eq "Bloomington")} | Select DisplayName, City
```

İşte sonuçlara bir örnek:

```powershell
DisplayName                              City
-----------                              ----
Alex Darrow                              San Diego
Bonnie Kearney                           San Diego
Julian Isla                              Bloomington
Rob Young                                Bloomington
```

Bu PowerShell komutunun yorumu şöyledir: Geçerli Microsoft 365 aboneliğindeki, San Diego veya Bloomington şehrinde posta kutusu olan tüm kullanıcıları alın (**{$\_. RecipientTypeDetails -eq "UserMailbox" -and ($\_. Şehir -eq "San Diego" -veya $\_. City -eq "Bloomington")}**) ve ardından her birine ilişkin adı ve şehri görüntüleyin (**DisplayName, City'yi seçin**).

Bloomington dışında herhangi bir yerde yaşayan kişilerin tüm posta kutularını listeleme komutu aşağıdadır:

```powershell
Get-User | Where {$_.RecipientTypeDetails -eq "UserMailbox" -and $_.City -ne "Bloomington"} | Select DisplayName, City
```

İşte sonuçlara bir örnek:

```powershell
DisplayName                               City
-----------                               ----
MOD Administrator                         Redmond
Alex Darrow                               San Diego
Allie Bellew                              Bellevue
Anne Wallace                              Louisville
Aziz Hassouneh                            Cairo
Belinda Newman                            Charlotte
Bonnie Kearney                            San Diego
David Longmuir                            Waukesha
Denis Dehenne                             Birmingham
Garret Vargas                             Seattle
Garth Fort                                Tulsa
Janet Schorr                              Bellevue
```

Bu PowerShell komutunun yorumu şöyledir: Geçerli Microsoft 365 aboneliğindeki, Bloomington şehrinde bulunmayan posta kutusu olan tüm kullanıcıları alın (**{$\_. RecipientTypeDetails -eq "UserMailbox" -ve $\_. City -ne "Bloomington"}**) ve ardından her birine ilişkin adı ve şehri görüntüleyin.

### <a name="use-wildcards"></a>Joker karakter kullanma

Bir adın bir bölümüyle eşleştirmek için PowerShell filtrelerinizde joker karakterler de kullanabilirsiniz. Örneğin, bir kullanıcı hesabı aradığınızı varsayalım. Hatırlayabildiğiniz tek şey, kullanıcının soyadının *Anderson* ya da *Henderson* ya da *Jorgenson* olduğu.

Arama aracını kullanarak ve üç farklı arama yaparak Microsoft 365 yönetim merkezi bu kullanıcıyı izleyebilirsiniz:

- *Anderson* için bir tane

- Bir tane  *de Henderson için.*

- *Jorgenson* için bir tane

Bu adların üçü de "son" ile sona erdiğinden, PowerShell'e adı "son" ile biten tüm kullanıcıları görüntülemesini söyleyebilirsiniz. Komut şu şekildedir:

```powershell
Get-User -Filter '{LastName -like "*son"}'
```

Bu PowerShell komutunun yorumu şöyledir: Geçerli Microsoft 365 aboneliğindeki tüm kullanıcıları alın, ancak yalnızca soyadları "son" ile biten kullanıcıları listeleyen bir filtre kullanın (**-Filter '{LastName -like "\*son"}'**). , \* kullanıcının soyadındaki harfler olan herhangi bir karakter kümesinin kısaltmasıdır.

## <a name="powershell-for-microsoft-365-makes-it-easy-to-print-or-save-data"></a>Microsoft 365 için PowerShell, verileri yazdırmayı veya kaydetmeyi kolaylaştırır

Microsoft 365 yönetim merkezi, veri listelerini görüntülemenizi sağlar. Skype Kurumsal Online için etkinleştirilen kullanıcıların listesini görüntüleyen Skype Kurumsal Online yönetim merkezi örneği aşağıda verilmişti:

![Skype Kurumsal Online için etkinleştirilen kullanıcıların listesini görüntüleyen Skype Kurumsal Çevrimiçi Yönetim merkezi örneği.](../media/o365-powershell-lync-users.png)

Bu bilgileri bir dosyaya kaydetmek için bir belgeye veya Microsoft Excel çalışma sayfasına yapıştırmanız gerekir. Her iki durumda da ek biçimlendirme gerekebilir. Ayrıca, Microsoft 365 yönetim merkezi görüntülenen listeyi doğrudan yazdırmak için bir yol sağlamaz.

Neyse ki, PowerShell'i yalnızca listeyi görüntülemek için değil, Excel kolayca içeri aktarılabilir bir dosyaya kaydetmek için de kullanabilirsiniz. Aşağıda, Skype Kurumsal Çevrimiçi kullanıcı verilerini virgülle ayrılmış değerler (CSV) dosyasına kaydetmeye yönelik örnek bir komut verilmiştir ve bu komut daha sonra Excel çalışma sayfasında kolayca tablo olarak içeri aktarılabilir:

```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Export-Csv -Path "C:\Logs\SfBUsers.csv" -NoTypeInformation
```

İşte sonuçlara bir örnek:

![Virgülle ayrılmış değerler dosyasına kaydedilmiş Skype Kurumsal Çevrimiçi kullanıcı verileri için Excel çalışma sayfasına aktarılan tablo örneği.](../media/o365-powershell-data-in-excel.png)

Bu PowerShell komutunun yorumu şöyledir: Geçerli Microsoft 365 aboneliğindeki tüm Skype Kurumsal Online kullanıcılarını alın (**Get-CsOnlineUser**); yalnızca kullanıcı adını, UPN'yi ve konumu (**DisplayName, UserPrincipalName, UsageLocation'ı seçin**) alın ve bu bilgileri C:Logs\\SfBUsers.csv adlı bir CSV dosyasına kaydedin (Export-Csv -Path "C:\\**\\Logs\\SfBUsers.csv" -NoTypeInformation**).

Bu listeyi XML dosyası veya HTML sayfası olarak kaydetmek için seçenekleri de kullanabilirsiniz. Aslında, ek PowerShell komutlarıyla, istediğiniz özel biçimlendirmeyle doğrudan Excel dosyası olarak kaydedebilirsiniz.

Ayrıca, listeyi görüntüleyen bir PowerShell komutunun çıkışını doğrudan Windows'deki varsayılan yazıcıya gönderebilirsiniz. Aşağıda örnek bir komut verilmişti:

```powershell
Get-CsOnlineUser | Select DisplayName, UserPrincipalName, UsageLocation | Out-Printer
```

Yazdırılan belgeniz şöyle görünür:

![Windows'da doğrudan varsayılan yazıcıya gönderilen bir PowerShell komutunun çıktısı olan yazdırılan belge örneği.](../media/o365-powershell-printed-data.png)

Bu PowerShell komutunun yorumu şöyledir: Geçerli Microsoft 365 aboneliğindeki tüm Skype Kurumsal Çevrimiçi kullanıcıları alın; yalnızca kullanıcı adını, UPN'yi ve konumu alın ve bu bilgileri varsayılan Windows yazıcıya (**Yazıcı Dışında**) gönderin.

Yazdırılan belge, PowerShell komut penceresindeki görüntüyle aynı basit biçimlendirmeye sahiptir. Basılı kopya almak için **| Komutun sonuna kadar Yazıcı Dışı** ...

## <a name="powershell-for-microsoft-365-lets-you-manage-across-server-products"></a>Microsoft 365 için PowerShell, sunucu ürünleri arasında yönetmenizi sağlar

Microsoft 365 oluşturan bileşenler birlikte çalışacak şekilde tasarlanmıştır. Örneğin, Microsoft 365 yeni bir kullanıcı eklediğinizi ve kullanıcının departmanı ve telefon numarası gibi bilgileri belirttiğinizi varsayalım. Bu bilgiler daha sonra kullanıcının bilgilerine Microsoft 365 hizmetlerden herhangi birinde erişerek kullanılabilir: Skype Kurumsal Çevrimiçi, Exchange veya SharePoint.

Ancak bu, ürün paketini kapsayan yaygın bilgiler içindir. Kullanıcının Exchange posta kutusuyla ilgili bilgiler gibi ürüne özgü bilgiler genellikle pakette kullanılamaz. Örneğin, kullanıcının posta kutusunun etkinleştirilip etkinleştirilmediğiyle ilgili bilgiler yalnızca Exchange yönetim merkezinde kullanılabilir.

Tüm kullanıcılarınız için aşağıdaki bilgileri gösteren bir rapor oluşturmak istediğinizi varsayalım:

- Kullanıcının görünen adı

- Kullanıcının Microsoft 365 için lisanslanıp lisanslanmayacağı

- Kullanıcının Exchange posta kutusunun etkinleştirilip etkinleştirilmediği

- Kullanıcının Skype Kurumsal Online için etkinleştirilip etkinleştirilmediği

Microsoft 365 yönetim merkezi kolayca böyle bir rapor oluşturamazsınız. Bunun yerine, bilgileri depolamak için Excel çalışma sayfası gibi ayrı bir belge oluşturmanız gerekir. Ardından, Microsoft 365 yönetim merkezi tüm kullanıcı adlarını ve lisans bilgilerini alın, <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezinden</a> posta kutusu bilgilerini alın, Skype Kurumsal Çevrimiçi Yönetim merkezinden çevrimiçi Skype Kurumsal bilgileri alın ve bu bilgileri birleştirin.

Alternatif olarak, raporu sizin için derlemek için bir PowerShell betiği kullanabilirsiniz.

Aşağıdaki örnek betik, bu makalede şimdiye kadar gördüğünüz komutlardan daha karmaşıktır. Ancak, aksi takdirde elde etmek zor olan bilgi görünümleri oluşturmak için PowerShell kullanma olasılığını gösterir. İşte ihtiyacınız olan listeyi derlemek ve görüntülemek için betik:

```powershell
$x = Get-AzureADUser

foreach ($i in $x)
    {
      $y = Get-Mailbox -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled

      $y = Get-CsOnlineUser -Identity $i.UserPrincipalName
      $i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled
    }

$x | Select DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB
```

İşte sonuçlara bir örnek:

```powershell
DisplayName             IsLicensed   IsMailboxEnabled   EnabledForSfB
-----------             ----------   ----------------   --------------
Bonnie Kearney          True         True               True
Fabrice Canel           True         True               True
Brian Johnson           False        True               False
Anne Wallace            True         True               True
Alex Darrow             True         True               True
David Longmuir          True         True               True
Katy Jordan             False        True               False
Molly Dempsey           False        True               False
```

Bu PowerShell betiğinin yorumu şöyledir:

1. Geçerli Microsoft 365 aboneliğindeki tüm kullanıcıları alın ve bilgileri *$x* (**$x = Get-AzureADUser**) adlı bir değişkende depolayın.
1. $x değişkenindeki tüm kullanıcıların üzerinde çalışan bir döngü başlatın **(foreach ($x'de $i)**).
1. *$y* adlı bir değişken tanımlayın ve kullanıcının posta kutusu bilgilerini içinde depolayın (**$y = Get-Mailbox -Identity $i.UserPrincipalName**).
1. *IsMailBoxEnabled* adlı kullanıcı bilgilerine yeni bir özellik ekleyin. Kullanıcı posta kutusunun IsMailBoxEnabled özelliğinin değerine ayarlayın (**$i | Add-Member -MemberType NoteProperty -Name IsMailboxEnabled -Value $y.IsMailboxEnabled**).
1. *$y* adlı bir değişken tanımlayın ve kullanıcının Skype Kurumsal Çevrimiçi bilgilerini içinde depolayın (**$y = Get-CsOnlineUser -Identity $i.UserPrincipalName**).
1. *EnabledForSfB* adlı kullanıcı bilgilerine yeni bir özellik ekleyin. Kullanıcının Skype Kurumsal Çevrimiçi bilgilerinin Enabled özelliğinin değerine ayarlayın (**$i | Add-Member -MemberType NoteProperty -Name EnabledForSfB -Value $y.Enabled**).
1. Kullanıcı listesini görüntüleyin, ancak yalnızca adlarını, lisanslı olup olmadıklarını ve posta kutularının etkinleştirilip etkinleştirilmediğini ve Skype Kurumsal Online için etkinleştirilip etkinleştirilmediklerini belirten iki yeni özelliği ekleyin (**$x | DisplayName, IsLicensed, IsMailboxEnabled, EnabledforSfB'yi seçin**.

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 için PowerShell ile Kullanmaya başlayın](getting-started-with-microsoft-365-powershell.md)

[PowerShell ile Microsoft 365 kullanıcı hesaplarını, lisanslarını ve gruplarını yönetme](manage-user-accounts-and-licenses-with-microsoft-365-powershell.md)

[Microsoft 365'de rapor oluşturmak için Windows PowerShell kullanma](use-windows-powershell-to-create-reports-in-microsoft-365.md)