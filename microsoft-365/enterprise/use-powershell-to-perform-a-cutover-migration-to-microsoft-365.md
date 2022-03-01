---
title: Microsoft 365'a geçiş yapmak için PowerShell Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: PowerShell kullanarak kaynak e-posta sisteminden içeriği tek bir kerede taşımayı öğrenmek için PowerShell'i nasıl Microsoft 365.
ms.openlocfilehash: 65f48d95a73742a0ba4e5225361ecfb0fbf66c40
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "63018801"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-microsoft-365"></a>Microsoft 365'a geçiş yapmak için PowerShell Microsoft 365

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Kullanıcı posta kutularının içeriğini kaynak e-posta sisteminden bir kerede tamamla Microsoft 365 geçiş kullanarak geçirebilirsiniz. Bu makale, Exchange Online PowerShell kullanarak e-posta geçişinin görev Exchange Online gösterir.

Microsoft 365'da tam e-posta geçişi hakkında Microsoft 365 ler konusunu gözden geçirerek[, geçiş](/Exchange/mailbox-migration/what-to-know-about-a-cutover-migration) sürecine genel bir bakış elde edin. Bu makalenin içeriğini rahatça anladığınızda, posta kutularını bir e-posta sisteminden diğerine geçirmeye başlamak için bunu kullanın.

> [!NOTE]
> Ayrıca, Exchange <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">merkezini kullanarak</a> da geçiş işlemini gerçekleştirin. Bkz[. E-postanın diğer adreslere geçişini Microsoft 365](/Exchange/mailbox-migration/cutover-migration-to-office-365).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

Bu görevi tamamlamak için tahmini süre: Geçiş toplu işlemini oluşturmak için 2-5 dakika. Geçiş toplu işlemi başlatıldıktan sonra, toplu işlemde yer alan posta kutularının sayısına, her posta kutusunun boyutuna ve kullanılabilir ağ kapasitenize bağlı olarak geçiş süresi değişir. Posta kutularını bu posta kutusuna geçirmenin ne kadar sürer olduğunu etkileyen diğer faktörler hakkında bilgi Microsoft 365 bkz. [Geçiş Performansı](/Exchange/mailbox-migration/office-365-migration-best-practices).

Bu yordamı veya yordamları gerçekleştirebilmeniz için, önce izinlerin atanması gerekir. Size hangi izinlerin gerekli olduğunu görmek için, Alıcı İzinleri konu başlığında yer alan bir tabloda yer alan " [Geçiş" girdisini](/exchange/recipients-permissions-exchange-2013-help) bakın.

Exchange Online PowerShell cmdlet'lerini kullanmak için oturum açmalı ve cmdlet'leri yerel Windows PowerShell gerekir. Yönergeler [Bağlan uzak PowerShell Exchange Online için bkz. Uzak PowerShell'i](/powershell/exchange/connect-to-exchange-online-powershell) kullanma hakkında daha fazla bilgi.

Geçiş komutlarının tam listesi için bkz. [Taşıma ve geçiş cmdlet'leri](/powershell/exchange/).

## <a name="migration-steps"></a>Geçiş adımları

### <a name="step-1-prepare-for-a-cutover-migration"></a>1. Adım: Kesin geçişe hazırlanma
<a name="BK_Step1"> </a>

- **Şirket içi veya kuruluş Exchange, bu kuruluşta kabul edilen bir etki alanı Microsoft 365 ekleyin.** Geçiş hizmeti, yeni posta kutuları için Microsoft Online Services kullanıcı kimliğini ve e-posta adresini oluşturmak için şirket içi posta kutularınızı SMTP Microsoft 365 kullanır. Etki alanınız kabul edilen bir Exchange veya Microsoft 365 birincil etki alanı değilse, geçiş başarısız olur. Daha fazla bilgi için bkz. [Etki alanlarınızı doğrulama](../admin/setup/add-domain.md).

- **Her Outlook şirket içi sunucu sunucunuzda her Exchange yapılandırabilirsiniz.** E-posta geçiş hizmeti, şirket içi Outlook sunucunuza bağlanmak için HTTP üzerinden RPC veya Her Yerden RPC Exchange kullanır. Exchange 2010, Exchange 2007 ve Exchange 2003 için Her Yerden Outlook'u ayarlama hakkında bilgi için aşağıdakilere bakın:

  - [Exchange 2010: Her Yerden Outlook'u Etkinleştirme](/previous-versions/office/exchange-server-2010/bb123542(v=exchg.141))

  - [Exchange 2007: Her Yerden Outlook'u Etkinleştirme](/previous-versions/office/exchange-server-2007/bb123889(v=exchg.80))

  - [Exchange 2003: HTTP üzerinden RPC için Dağıtım Senaryoları](/previous-versions/tn-archive/bb124876(v=exchg.65))

  - [Outlook 2003'te Her Exchange Yapılandırma](/previous-versions/office/exchange-server-2007/aa996922(v=exchg.80))

    > [!IMPORTANT]
    > Her Outlook Yapılandırmanız, güvenilir bir sertifika yetkilisi (CA) tarafından verilen bir sertifikayla yapılandırıldığından emin olmak gerekir. Otomatik olarak imzalanan sertifikayla yapılandırılmaz. Daha fazla bilgi için bkz. [Her Yerden Her Yerden SSL Outlook.](/previous-versions/office/exchange-server-2007/aa995982(v=exchg.80))

- **Her Yerden Kullan'ı kullanarak Exchange bilgisayarınıza bağlan Outlook doğrulayın.** Bağlantı ayarlarınızı test etmek için aşağıdaki yöntemlerden birini deneyin:

  - Şirket Outlook posta kutunuza bağlanmak için şirket ağınız dışından Microsoft Exchange kullanın.

  - Bağlantı ayarlarınızı test [etmek Exchange için Microsoft Masaüstü](https://www.testexchangeconnectivity.com/) Uzaktan Bağlantı Çözümleyicisi'ne tıklayın. Her Yerden Outlook (HTTP üzerinden RPC) veya Outlook Otomatik Bulma testlerini kullanın.

  - Exchange Online PowerShell'de aşağıdaki komutları çalıştırın.

  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- **Şirket içi kullanıcı hesabına, şirket içi kutunuzda posta kutularına erişim için gerekli izinleri Exchange attayın.** Şirket içi Exchange hesabınıza bağlanmak için (geçiş yöneticisi olarak da adlandırılan) şirket içi kullanıcı hesabının, Microsoft 365'e geçirmek istediğiniz şirket içi posta kutularına erişmek için gerekli izinlere sahip olması gerekir. Bu kullanıcı hesabı, şirket içi kuruluşa bir geçiş uç noktası oluşturmak için kullanılır.

    Aşağıdaki listede, tam geçiş kullanarak posta kutularını geçirmek için gereken yönetim ayrıcalıkları görüntülenir. Üç olası seçenek vardır.

  - Geçiş yöneticisi, şirket içi kuruluşta **Active Directory'de Domain Admins** grubunun bir üyesi olmalıdır.

    Veya

  - Geçiş yöneticisine şirket içi her posta kutusu için **FullAccess** izni atanmalıdır.

    Veya

  - Geçiş yöneticisine kullanıcı posta **kutularının depoldığı** şirket içi posta kutusu veritabanında Receive As izni atanabilir.

- **Birleşik Mesajlaşma'yi devre dışı bırakma.** Geçişte olduğu şirket içi posta kutuları Birleşik Mesajlaşma (UM) için etkinleştirilmişse, posta kutularını geçirmeden önce UM'yi devre dışı bırakmanız gerekir. Geçiş tamamlandıktan sonra posta kutularda UM'yi etkinleştirebilirsiniz.

- **Güvenlik Grupları ve Temsilciler** E-posta geçiş hizmeti, şirket içi Active Directory gruplarının güvenlik grubu olup olmadığını algılayamaz ve bu nedenle geçirilen hiçbir grubu Active Directory'de güvenlik Microsoft 365. Microsoft 365 kiracınıza güvenlik grupları almak için, geçiş işlemini başlatmadan önce Microsoft 365 kiracınıza posta özelliği etkin boş bir güvenlik grubu hazırlamanız gerekir. Buna ek olarak, bu geçiş yöntemi yalnızca posta kutularını, posta kullanıcılarını, posta kişilerini ve posta özelliği etkin grupları taşır. Başka herhangi bir Active Directory nesnesi, örneğin Microsoft 365'e geçirilmez kullanıcı, geçirilen bir nesnenin yöneticisi veya temsilcisi olarak atanırsa, bu nesnenin geçiş öncesinde nesneden kaldırılması gerekir.

### <a name="step-2-create-a-migration-endpoint"></a>2. Adım: Geçiş uç noktası oluşturma
<a name="BK_Step2"> </a>

E-postayı geçirmeyi Microsoft 365, e-postanın kaynak e-posta sistemine bağlanması ve bu sistemle iletişim kurması gerekir. Bunu yapmak için, Microsoft 365 uç noktasını kullanır. Geçiş için her Outlook geçiş uç noktasını oluşturmak için, önce [Tamamla'ya Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

Geçiş komutlarının tam listesi için bkz. [Taşıma ve geçiş cmdlet'leri](/powershell/exchange/).

Exchange Online PowerShell'de aşağıdaki komutları çalıştırın:

```powershell
$Credentials = Get-Credential
```

Örnekte, şirket içi Exchange sunucusuyla bağlantı ayarlarını almak ve test etmek için [Test-MigrationServerAvailability](/powershell/module/exchange/test-migrationserveravailability) cmdlet'i kullanılır ve ardından "CutoverEndpoint" adlı geçiş uç noktasını oluşturmak için bu bağlantı ayarları kullanılır.

```powershell
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> **New-MigrationEndpoint** cmdlet'i, **-TargetDatabase seçeneği kullanılarak hizmetin kullanabileceği bir veritabanı belirtmek için** kullanılabilir. Aksi takdirde, yönetim posta kutusunun bulunduğu Active Directory Federasyon Hizmetleri (AD FS) 2.0 sitesinden bir veritabanı rastgele atanır.

#### <a name="verify-it-worked"></a>Çalıştığını doğrulayın

Diğer Exchange Online PowerShell'de, "CutoverEndpoint" geçiş uç noktası hakkında bilgi görüntülemek için aşağıdaki komutu çalıştırın:

```powershell
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a>3. Adım: Tam geçiş toplu işlemini oluşturma
<a name="BK_Step3"> </a>

PowerShell'de **New-MigrationBatch** cmdlet'ini kullanarak Exchange Online geçişi için bir geçiş toplu işlemi oluşturabilirsiniz. Otomatik Başlat parametresini de dahilerek geçiş toplu işlemini oluşturabilir ve _otomatik olarak başlatabilirsiniz_ . Alternatif olarak, geçiş toplu işlemini oluşturabilir ve daha sonra **Start-MigrationBatch** cmdlet'ini kullanarak el ile başlatabilirsiniz. Bu örnekte, "CutoverBatch" adlı bir geçiş toplu işlemi oluşturulur ve önceki adımda oluşturulmuş geçiş uç noktasını kullanır.

```powershell
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

Bu örnekte ayrıca "CutoverBatch" adlı bir geçiş toplu işlemi oluşturulur ve önceki adımda oluşturulmuş geçiş uç noktasını kullanır. Otomatik Başlat  _parametresi dahil_ etme nedeniyle, geçiş toplu işleminin geçiş panosunda veya **Start-MigrationBatch** cmdlet'i kullanılarak el ile başlatılabilir. Daha önce de belirtildiği gibi, bir defada yalnızca bir geçiş toplu işlemi olabilir.

```powershell
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a>Çalıştığını doğrulayın

Geçiş için bir geçiş toplu işlemini başarıyla oluşturduğunuzdan emin olmak için, yeni geçiş toplu işlemiyle ilgili bilgileri görüntülemek için Exchange Online PowerShell'de aşağıdaki komutu çalıştırın:

```powershell
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a>4. Adım: Tam geçiş toplu işlemini başlatma

PowerShell'de geçiş toplu Exchange Online başlatmak için aşağıdaki komutu çalıştırın. Bu, "CutoverBatch" adlı bir geçiş toplu işlemi oluşturacak.

```powershell
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a>Çalıştığını doğrulayın

Geçiş toplu işlemi başarıyla başlatıldı olursa, geçiş panosunda durumu Eşitleniyor olarak belirtilir. Exchange Online PowerShell kullanarak geçiş toplu işlemini başarıyla çalıştırdığınızı doğrulamak için, aşağıdaki komutu çalıştırın:

```powershell
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a>5. Adım: E-postanızı başka bir Microsoft 365

E-posta sistemleri, e-postaların teslim edileceği yeri belirlemek için MX kaydı olarak adlandırılan bir DNS kaydını kullanır. E-posta geçiş işlemi sırasında, MX kaydınız kaynak e-posta sisteminize işaret ediyor olur. Artık MX kaydınıza işaret Microsoft 365 işlemi tamamlandığından, MX kaydınızı başka bir adrese Microsoft 365. Bu, e-postanın posta kutunuza teslim Microsoft 365 yardımcı olur. MX kaydını hareket ettirerek, hazır olurken eski e-posta sisteminizi de kapatabilirsiniz.

Birçok DNS sağlayıcısı için, MX kaydınızı değiştirmeye yönelik belirli yönergeler sağlanmıştır. DNS sağlayıcınız bunların arasında değilse veya genel yönergeler hakkında fikir edinmek istiyorsanız, [genel MX kaydı yönergeleri](https://support.office.microsoft.com/article/7b7b075d-79f9-4e37-8a9e-fb60c1d95166#bkmk_add_mx) de sağlanmıştır.

Müşterilerinizin ve iş ortaklarınızın e-posta sistemlerinin değişen MX kaydını fark etmesi 72 saat kadar sürebilir. Sonraki görev olan 6. Adım: Geçiş toplu işlemini silme göreviyle devam etmek için en az 72 [saat bekleyin](#step-6-delete-the-cutover-migration-batch).

### <a name="step-6-delete-the-cutover-migration-batch"></a>6. Adım: Tam geçiş toplu işlemini silme

MX kaydını değiştirdikten ve tüm e-postanın bu posta kutularına yönlendirildikten Microsoft 365, kullanıcılara postalarının gönder gerekmeyeceklerini Microsoft 365. Bundan sonra, geçiş toplu işlemini silebilirsiniz. Geçiş toplu işlemini silmeden önce aşağıdakileri doğrulayın.

- Tüm kullanıcılar posta kutuları Microsoft 365 kullanıyor. Toplu işlem silindikten sonra, şirket içi posta kutularına Exchange Server posta ilgili posta kutularına Microsoft 365 kopyalanmaz.

- Microsoft 365 posta kutuları, posta doğrudan onlara gönderilmeye başladıktan sonra en az bir kez eşitlenmiş olabilir. Bunu yapmak için, geçiş toplu işleminin Son Eşitleme Zamanı kutusunda yer alan değerin, postanın doğrudan posta posta kutularına yönlendir yapmaya başladığı zamanla daha yakın Microsoft 365 olun.

PowerShell'de "CutoverBatch" geçiş toplu Exchange Online silmek için aşağıdaki komutu çalıştırın:

```powershell
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a>Bölüm 7: Kullanıcı lisansları atama

 **Geçirilen Microsoft 365 için kullanıcı hesaplarını lisans ataarak etkinleştirin.** Lisans ata atasanız, yetkisiz kullanım süresi sona erdiğinde (30 gün) posta kutusu devre dışı bırakılır. Lisans atama ve lisans Microsoft 365 yönetim merkezi için bkz. [Lisansları atama veya atamayı iptal et](../admin/manage/assign-licenses-to-users.md).

### <a name="step-8-complete-post-migration-tasks"></a>8. Adım: Geçiş sonrası görevlerini tamamlama

- **Kullanıcıların posta kutularına kolayca ulaşabilmeleri için bir Otomatik Bulma DNS kaydı oluşturun.** Tüm şirket içi posta kutuları Microsoft 365'e geçirildikten sonra, kullanıcıların Outlook ve mobil istemcilerle yeni Microsoft 365 posta kutularına kolayca bağlanmalarına olanak sağlamak üzere Microsoft 365 kuruluşu için bir Otomatik Bulma DNS kaydı yapılandırabilirsiniz. Bu yeni Otomatik Bulma DNS kaydında, bu kaydın tüm kuruluşlarında kullanmakta olduğu ad alanıyla Microsoft 365 gerekir. Örneğin, bulut tabanlı ad alanınız bulut.contoso.com ise, oluşturmanız gereken Otomatik Bulma DNS kaydı autodiscover.bulut.contoso.com'dur.

    Exchange Server etki alanınıza bağlı kalmanızı sağlarsanız, otomatik bulma DNS CNAME kaydının geçiş sonrasında hem iç hem de dış DNS'te Microsoft 365'e işaret etmek zorunda olduğundan emin olun; böylelikle Outlook istemcisi doğru posta kutusuna bağlanacak.

    > [!NOTE]
    >  Exchange 2007, Exchange 2010 ve Exchange 2013'te de 'a ayarlaym `Set-ClientAccessServer AutodiscoverInternalConnectionURI` gerekir`Null`.

    Microsoft 365 müşterilere ve mobil istemcilere Otomatik Bulma hizmetini uygulamak için CNAME Outlook kullanır. Otomatik Bulma CNAME kaydı aşağıdaki bilgileri içermelidir:

  - **Alias:** autodiscover

  - **Target:** autodiscover.outlook.com

    Daha fazla bilgi için bkz [. Etki alanınıza bağlanmak için DNS kayıtları ekleme](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

- **Şirket içi Exchange sunucularının yetkisini alın.** Tüm e-postanın doğrudan Microsoft 365 posta kutularına yönlendirildikten ve artık şirket içi e-posta kuruluşlarınızı korumanız gerekmeyecektir veya çoklu oturum açma (SSO) çözümü uygulamayı planlaydıktan sonra, Exchange'i sunuculardan kaldırabilir ve şirket içi Exchange kuruluşu kaldırabilirsiniz.

    Daha fazla bilgi için aşağıdakilere bakın:

  - [Exchange 2010'u Değiştirme veya Kaldırma](/previous-versions/office/exchange-server-2010/ee332361(v=exchg.141))

  - [Exchange 2007 Kuruluşunu Kaldırma](/previous-versions/office/exchange-server-2007/aa998313(v=exchg.80))

  - [Exchange Server 2003'ü Kaldırma](/previous-versions/tn-archive/bb125110(v=exchg.65))