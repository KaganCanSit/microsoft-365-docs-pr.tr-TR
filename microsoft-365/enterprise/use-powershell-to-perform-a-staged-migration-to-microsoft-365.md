---
title: Geçişe aşamalı geçiş yapmak için PowerShell Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 07/17/2020
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
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: Zaman içinde kaynak e-posta sisteminden içerik taşımak için PowerShell kullanarak aşamalı geçiş ve kaynak e-posta Microsoft 365.
ms.openlocfilehash: 562dcb8f32a0cd2b8452f2145dcb608dac353e2f
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "63018828"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-microsoft-365"></a>Geçişe aşamalı geçiş yapmak için PowerShell Microsoft 365

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Kullanıcı posta kutularının içeriğini kaynak e-posta sisteminden zaman içinde aşamalı Microsoft 365 geçişe geçirebilirsiniz.

Bu makalede, Exchange Online PowerShell kullanarak aşamalı e-posta geçişiyle ilgili görevlerde size yol gösterir. Aşamalı [e-posta geçişi hakkında bilmek istediğiniz konu](/Exchange/mailbox-migration/what-to-know-about-a-staged-migration) başlığı, geçiş sürecine genel bir bakış sağlar. Bu makalenin içeriğini rahatça anladığınızda, posta kutularını bir e-posta sisteminden diğerine geçirmeye başlamak için bunu kullanın.

> [!NOTE]
> Ayrıca, aşamalı geçiş <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim</a> merkezini de kullanabilirsiniz. Bkz[. E-postanın aşamalı geçişini Microsoft 365](/Exchange/mailbox-migration/perform-a-staged-migration/perform-a-staged-migration).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

Bu görevi tamamlamak için tahmini süre: Geçiş toplu işlemini oluşturmak için 2-5 dakika. Geçiş toplu işlemi başlatıldıktan sonra, toplu işlemde yer alan posta kutularının sayısına, her posta kutusunun boyutuna ve kullanılabilir ağ kapasitenize bağlı olarak geçiş süresi değişir. Posta kutularını bu posta kutusuna geçirmenin ne kadar sürer olduğunu etkileyen diğer faktörler hakkında bilgi Microsoft 365 bkz. [Geçiş Performansı](/Exchange/mailbox-migration/office-365-migration-best-practices).

Bu yordamı veya yordamları gerçekleştirebilmeniz için, önce izinlerin atanması gerekir. Size hangi izinlerin gerekli olduğunu görmek için, Alıcı İzinleri konu başlığında yer alan " [Geçiş" girdisini](/exchange/recipients-permissions-exchange-2013-help) bakın.

Exchange Online PowerShell cmdlet'lerini kullanmak için oturum açmalı ve cmdlet'leri yerel Windows PowerShell gerekir. Yönergeler [Bağlan uzak PowerShell Exchange Online için bkz. Uzak PowerShell'i](/powershell/exchange/connect-to-exchange-online-powershell) kullanma hakkında daha fazla bilgi.

Geçiş komutlarının tam listesi için bkz. [Taşıma ve geçiş cmdlet'leri](/powershell/exchange/).

## <a name="migration-steps"></a>Geçiş adımları

### <a name="step-1-prepare-for-a-staged-migration"></a>1. Adım: Aşamalı geçişe hazırlanma

Aşamalı geçiş kullanarak posta Microsoft 365 geçirmeden önce, posta kutunuzda veya ortamınız için birkaç Exchange vardır.

 **Her Yerden Outlook'u şirket içi Exchange Server**'ınızda yapılandırma E-posta geçiş hizmeti şirket içi Exchange Server'ınıza bağlanmak için Her Yerden Outlook (HTTP üzerinden RPC olarak da bilinir) kullanır. Outlook 2007 ve Exchange 2003'te her Exchange Server'i ayarlama hakkında bilgi için aşağıdakilere bakın:

- [Exchange 2007: Her Yerden Outlook'u Etkinleştirme](/previous-versions/office/exchange-server-2007/bb123889(v=exchg.80))

- [Her Yerden Outlook'u Exchange 2003'le yapılandırma](/previous-versions/office/exchange-server-2007/aa996922(v=exchg.80))

> [!IMPORTANT]
> Her Yerden Outlook yapılandırmanızla, güvenilir bir sertifika yetkilisi (CA) tarafından verilmiş bir sertifika kullanmalısınız. Her Yerden Outlook, otomatik olarak imzalanan sertifikayla yapılandırılamaz. Daha fazla bilgi için bkz. [Her Yerden Outlook için SSL'yi yapılandırma](/previous-versions/office/exchange-server-2007/aa995982(v=exchg.80)).

 **İsteğe bağlı: Her Yerden Outlook kullanarak Exchange kuruluşunuza bağlanabildiğinizi doğrulama** Bağlantı ayarlarınızı test etmek için aşağıdaki yöntemlerden birini deneyin.

- Şirket içi Exchange posta kutunuza bağlanmak için şirket ağınızın dışından Outlook'u kullanın.

- Bağlantı ayarlarınızı [test etmek için Microsoft Uzak Bağlantı](https://https://testconnectivity.microsoft.com/) Çözümleyicisi'ne tıklayın. Her Yerden Outlook (HTTP üzerinden RPC) veya Outlook Otomatik Bulma testlerini kullanın.

- Exchange Online PowerShell'de aşağıdaki komutları çalıştırın:

  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **İzinleri ayarlama** Şirket içi Exchange hesabınıza bağlanmak için (geçiş yöneticisi olarak da adlandırılan) şirket içi kullanıcı hesabının, Microsoft 365'e geçirmek istediğiniz şirket içi posta kutularına erişmek için gerekli izinlere sahip olması gerekir. Bu kullanıcı hesabı, daha sonra bu yordamın 3. Adımı: Geçiş uç noktası oluşturma yordamında bir geçiş uç noktası oluşturarak e-posta [sisteminize bağlanarak kullanılır](#step-3-create-a-migration-endpoint).

Posta kutularını geçirmek için yöneticinin şu izin kümelerinden birine sahip olması gerekir:

- Şirket içi **kuruluşta Active** Directory'de Domain Admins grubuna üye olun.

    veya

- Şirket içi posta kutularının her biri için **fullAccess** izni ve şirket içi kullanıcı hesaplarda **TargetAddress** özelliğini değiştirmek için **WriteProperty** izni atanabilir.

    veya

- Kullanıcı posta **kutularının depolu** olduğu şirket içi posta kutusu veritabanında receive As izni ve şirket içi kullanıcı hesaplarında **TargetAddress** özelliğini değiştirmek için **WriteProperty** izni atanabilir.

Bu izinleri ayarlama yönergeleri için Posta kutularını başka bir klasöre [geçirmek için izin Microsoft 365](/Exchange/mailbox-migration/assign-permissions-for-migration).

 **Birleşik Mesajlaşma'yi (UM) devre dışı bırakma** Geçişini tamamlarken şirket içi posta kutuları için UM açıksa, geçiş öncesinde UM'i kapatın. Geçiş tamamlandıktan sonra posta kutuları için UM'i açabilirsiniz. Nasıl bilgi adımları için bkz. [Dağıtılabilir birleşik mesajlaşma](/previous-versions/office/exchange-server-2007/bb124691(v=exchg.80)).

 **Yeni bir hesapta yeni kullanıcılar oluşturmak için dizin Microsoft 365.** Dizin eşitlemesini, şirket içi kullanıcı sayısınıza göre tüm şirket içi kullanıcıları oluşturmak Microsoft 365 kullanır.

Oluşturulduktan sonra kullanıcılara lisans alınız. Kullanıcılar oluşturulduktan sonra lisans eklemek için 30 gün süreniz vardır. Lisans ekleme adımları için bkz. [8. Adım: Geçiş sonrası görevlerini tamamlama](#step-8-complete-post-migration-tasks).

 Şirket içi kullanıcılarınızı aynı Microsoft Azure Active Directory için Eşitleme Hizmetleri'ni veya Microsoft Azure AD Eşitleme Hizmetleri'ni Microsoft 365. Posta kutuları Microsoft 365'a geçirildikten sonra, şirket içi kuruluşta kullanıcı hesaplarını yönetirsiniz ve bu hesaplar Microsoft 365 eşitlenir. Daha fazla bilgi için [bkz.Directory Tümleştirmesi](/previous-versions/azure/azure-services/jj573653(v=azure.100)) .

### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>2. Adım: Aşamalı geçiş toplu işlemi için CSV dosyası oluşturma

Şirket içi posta kutularını Microsoft 365'a geçirmek istediğiniz kullanıcıları tanımdikten sonra, bir virgülle ayrılmış değer (CSV) dosyası kullanarak geçiş toplu işlemini oluşturabilirsiniz. MICROSOFT 365 tarafından geçişi çalıştırmak için kullanılan CSV dosyasının her satırı, bir şirket içi posta kutusuyla ilgili bilgileri içerir.

> [!NOTE]
> Aşamalı geçiş kullanarak posta kutusuna geçirebilirsiniz ve bu posta kutularının Microsoft 365 sınırı yoktur. Geçiş toplu işleminde kullanılan CSV dosyası en çok 2.000 satır içerebilir. 2.000'den çok posta kutusunu geçirmek için, ek CSV dosyaları oluşturun ve her dosyayı yeni bir geçiş toplu işlemi oluşturmak için kullanın.

 **Desteklenen öznitelikler**

Aşamalı geçiş için CSV dosyası aşağıdaki üç özniteliği destekler. CSV dosyasındaki her satır bir posta kutusuna karşılık gelir ve bu özniteliklerin her biri için bir değer içermelidir.

|**Öznitelik**|**Açıklama**|**Gerekli mi?**|
|:-----|:-----|:-----|
|EmailAddress  <br/> |Şirket içi posta kutuları için birincil SMTP e-posta adresini belirtir; örneğin, pilarp@contoso.com.  <br/> Şirket içi posta kutuları için birincil SMTP adresini kullanın ve posta kutusundan kullanıcı Microsoft 365. Örneğin, şirket içi etki alanının adı contoso.com ancak Microsoft 365 e-posta etki alanının adı service.contoso.com ise, CSV dosyasındaki e-posta adresleri için contoso.com etki alanı adını kullanabilirsiniz.  <br/> |Gerekli  <br/> |
|Password  <br/> |Yeni ve yeni posta kutusu için Microsoft 365 ayarlanır. E-postanıza uygulanan tüm Microsoft 365 uygulanan parola kısıtlamaları, CSV dosyasına dahil edilen parolalara da uygulanır.  <br/> |İsteğe bağlı  <br/> |
|ForceChangePassword  <br/> |Kullanıcının yeni posta kutusunda ilk kez oturum a açma parolasını değiştirmesi gerekip gerek Microsoft 365 belirtir. Bu parametrenin değeri olarak **True** veya **False** kullanın. <br/> > [!NOTE]> Şirket içi kuruluşta Active Directory Federasyon Hizmetleri'ni (AD FS) veya daha büyük bir bölümü dağıtarak çoklu oturum açma (SSO) çözümü uygulamadınız, **ForceChangePassword** özniteliğinin değeri olarak **False** kullansanız gerekir.          |İsteğe bağlı  <br/> |

 **CSV dosya biçimi**

Aşağıda, CSV dosyasının biçimi için bir örnek verilmiştir. Bu örnekte, üç şirket içi posta kutusu Posta Kutusu'Microsoft 365.

CSV dosyasının ilk satırında veya üst bilgi satırında, izleyen satırlarda belirtilen özniteliklerin veya alanların adları listelenir. Öznitelik adları birbirinden virgülle ayrılır.

```powershell
EmailAddress,Password,ForceChangePassword
pilarp@contoso.com,Pa$$w0rd,False
tobyn@contoso.com,Pa$$w0rd,False
briant@contoso.com,Pa$$w0rd,False
```

Üst bilgi satırın altındaki her satır bir kullanıcıyı temsil eder ve kullanıcının posta kutusu geçirilirken kullanılacak bilgileri sağlar. Her satırdaki öznitelik değerleri, üst bilgi satırındaki öznitelik adlarıyla aynı sırada olmalıdır.

CSV dosyasını oluşturmak için herhangi bir metin düzenleyicisini veya Excel gibi bir uygulamayı kullanın. Dosyayı .csv veya .txt dosyası olarak kaydedin.

> [!NOTE]
> CSV dosyası ASCII olmayan veya özel karakterler içeriyorsa, CSV dosyasını UTF-8 veya başka bir Unicode kodlamayla kaydedin. Uygulamaya bağlı olarak, bilgisayarın sistem yerel ayarları CSV dosyasında kullanılan dille eşlaşıyorsa CSV dosyasını UTF-8 veya başka bir Unicode kodlamayla kaydetme işlemi daha kolay olabilir.

### <a name="step-3-create-a-migration-endpoint"></a>3. Adım: Geçiş uç noktası oluşturma

E-postayı geçirmeyi Microsoft 365, e-postanın kaynak e-posta sistemine bağlanması ve bu sistemle iletişim kurması gerekir. Bunu yapmak için, Microsoft 365 uç noktasını kullanır. PowerShell kullanarak Outlook Her Yerden geçiş uç noktası oluşturmak için, aşamalı geçiş için, önce [Exchange Online.](/powershell/exchange/connect-to-exchange-online-powershell)

Geçiş komutlarının tam listesi için bkz. [Taşıma ve geçiş cmdlet'leri](/powershell/exchange/).

Exchange Online PowerShell'Outlook Her Yerden geçiş uç noktası oluşturmak için, aşağıdaki komutları çalıştırın:

```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

**New-MigrationEndpoint cmdlet'i** hakkında daha fazla bilgi için [bkz.New-MigrationEndpoint](/powershell/module/exchange/new-migrationendpoint).

> [!NOTE]
> **New-MigrationEndpoint** cmdlet'i, **-TargetDatabase seçeneği kullanılarak hizmetin kullanabileceği bir veritabanı belirtmek için** kullanılabilir. Aksi takdirde, yönetim posta kutusunun bulunduğu Active Directory Federasyon Hizmetleri (AD FS) 2.0 sitesinden bir veritabanı rastgele atanır.

#### <a name="verify-it-worked"></a>Çalıştığını doğrulayın

PowerShell Exchange Online te, "StagedEndpoint" geçiş uç noktası hakkında bilgi görüntülemek için aşağıdaki komutu çalıştırın:

```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>4. Adım: Aşama geçiş toplu işlemini oluşturma ve başlatma

PowerShell'de **New-MigrationBatch** cmdlet'ini kullanarak Exchange Online geçişi için bir geçiş toplu işlemi oluşturabilirsiniz. Otomatik Başlat parametresini de dahilerek geçiş toplu işlemini oluşturabilir ve _otomatik olarak başlatabilirsiniz_ . Alternatif olarak, geçiş toplu işlemini oluşturabilir ve daha sonra **Start-MigrationBatch** cmdlet'ini kullanarak el ile başlatabilirsiniz. Bu örnekte, "StagedBatch1" adlı bir geçiş toplu işlemi oluşturulur ve önceki adımda oluşturulmuş geçiş uç noktasını kullanır.

```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

Bu örnek, "StagedBatch1" adlı bir geçiş toplu işlemi oluşturur ve önceki adımda oluşturulan geçiş uç noktasını kullanır. Otomatik Başlat  _parametresi dahil_ etme nedeniyle, geçiş toplu işleminin geçiş panosunda veya **Start-MigrationBatch** cmdlet'i kullanılarak el ile başlatılabilir. Daha önce de belirtildiği gibi, bir defada yalnızca bir geçiş toplu işlemi olabilir.

```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a>Çalıştığını doğrulayın

"StagedBatch1" Exchange Online görüntülemek için PowerShell'de aşağıdaki komutu çalıştırın:

```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

Ayrıca, aşağıdaki komutu çalıştırarak toplu işleminin başlat doğrulayın:

```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

**Get-MigrationBatch cmdlet'i** hakkında daha fazla bilgi için [bkz.Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a>5. Adım: Şirket içi posta kutularını posta özelliği etkin kullanıcılara dönüştürme

Bir grup posta kutusunu başarıyla geçirdikten sonra, kullanıcıların e-postalarına ulaşmalarını sağlamak için bir yol bulmanız gerekir. Posta kutusu geçirilen bir kullanıcının, artık hem şirket içinde hem de posta kutularında bir posta Microsoft 365. Aynı adreste posta kutusu Microsoft 365 kullanıcılar artık şirket içi posta kutularında yeni posta almayacak.

Geçişlerinizi henüz bitiremediklerinden, henüz tüm kullanıcıları e-postalarını E-posta için Microsoft 365 hazır olmazsınız. Peki her iki posta kutusu da olan kişiler için ne yapacaksınız? Yapabileceğiniz, zaten geçirmiş olduğunuz şirket içi posta kutularını posta özelliği etkin kullanıcılara dönüştürmektir. Posta kutusundan posta hesabı etkin kullanıcıya değiştirildiğinde, kullanıcıyı e-postası için Microsoft 365 posta kutusuna değil de E-posta adresine yönlendirebilirsiniz.

Şirket içi posta kutularını posta özelliği etkin kullanıcılara dönüştürmenin bir diğer önemli nedeni de, ara sunucu adreslerini posta özelliği etkin kullanıcılara kopyalayıp Microsoft 365 posta kutularından ara sunucu adreslerini tutmaktır. Bu, Active Directory kullanarak şirket içi kuruluşunuzdaki bulut tabanlı kullanıcıları yönetebilmenizi sağlar. Ayrıca, tüm posta kutuları Microsoft 365'e geçirildikten sonra şirket içi Exchange Server organizasyon undan izin olmaya karar verirsiniz, posta özelliği etkin kullanıcılara kopyalanmış olan ara sunucu adresleri şirket içi Active Directory'niz içinde kalır.

### <a name="step-6-delete-a-staged-migration-batch"></a>6. Adım: Aşamalı geçiş toplu işlemini silme

 Geçiş toplu işlemi'nde yer alan tüm posta kutuları başarıyla geçirildikten ve toplu işlemde şirket içi posta kutularını posta özelliği etkin kullanıcılara dönüştürüldikten sonra, aşamalı geçiş toplu işlemini silebilirsiniz. Geçiş toplu işlemi içinde postanın postanın posta kutusuna Microsoft 365 emin olun. Aşamalı geçiş toplu işlemini silebilirsiniz, geçiş hizmeti geçiş toplu işlemiyle ilgili tüm kayıtları temizler ve geçiş toplu işlemini siler.

PowerShell'de "StagedBatch1" geçiş toplu Exchange Online silmek için aşağıdaki komutu çalıştırın.

```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

**Remove-MigrationBatch cmdlet'i** hakkında daha fazla bilgi için [bkz.Remove-MigrationBatch](/powershell/module/exchange/remove-migrationbatch).

#### <a name="verify-it-worked"></a>Çalıştığını doğrulayın

"IMAPBatch1 Exchange Online bilgi görüntülemek için PowerShell'de aşağıdaki komutu çalıştırın:

```powershell
Get-MigrationBatch StagedBatch1
```

Komut, geçiş toplu işlemini Kaldırma durumuyla döndürür veya geçiş toplu işleminin bulunamadısını ve toplu İşlemin silindikten sonra bulunamadısını belirten bir hata döndürür.

**Get-MigrationBatch cmdlet'i** hakkında daha fazla bilgi için [bkz.Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

### <a name="step7-assign-licenses-to-microsoft-365-users"></a>Adım7: Kullanıcılara lisans Microsoft 365 atama

Geçirilen Microsoft 365 için kullanıcı hesaplarını lisans ataarak etkinleştirin. Lisans ata atadığınız zaman, yetkisiz kullanım süresi (30 gün) sona erdiğinde posta kutusu devre dışı bırakılır. Lisans atama ve lisans Microsoft 365 yönetim merkezi için bkz. [Lisansları atama veya atamayı iptal et](../admin/manage/assign-licenses-to-users.md).

### <a name="step-8-complete-post-migration-tasks"></a>8. Adım: Geçiş sonrası görevlerini tamamlama

- **Kullanıcıların posta kutularına kolayca ulaşabilmeleri için bir Otomatik Bulma DNS kaydı oluşturun.** Tüm şirket içi posta kutuları Microsoft 365'e geçirildikten sonra, kullanıcıların Outlook ve mobil istemcilerle yeni Microsoft 365 posta kutularına kolayca bağlanmalarına olanak sağlamak üzere Microsoft 365 kuruluşu için bir Otomatik Bulma DNS kaydı yapılandırabilirsiniz. Bu yeni Otomatik Bulma DNS kaydında, bu kaydın tüm kuruluşlarında kullanmakta olduğu ad alanıyla Microsoft 365 gerekir. Örneğin, bulut tabanlı ad alanınız bulut.contoso.com ise, oluşturmanız gereken Otomatik Bulma DNS kaydı autodiscover.bulut.contoso.com'dur.

    Microsoft 365 müşterilere ve mobil istemcilere Otomatik Bulma hizmetini uygulamak için CNAME Outlook kullanır. Otomatik Bulma CNAME kaydı aşağıdaki bilgileri içermelidir:

  - **Alias:** autodiscover

  - **Target:** autodiscover.outlook.com

    Daha fazla bilgi için bkz [. Etki alanınıza bağlanmak için DNS kayıtları ekleme](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

- **Şirket içi Exchange sunucularının yetkisini alın.** Tüm e-postanın doğrudan Microsoft 365 posta kutularına yönlendirildikten ve artık şirket içi e-posta kuruluşlarınızı korumanız gerekmeyecektir veya SSO çözümü uygulamayı planlamayacaksanız, Exchange'i sunuculardan kaldırabilir ve şirket içi Exchange kuruluşu kaldırabilirsiniz.

    Daha fazla bilgi için aşağıdakilere bakın:

  - [Exchange 2010'u Değiştirme veya Kaldırma](/previous-versions/office/exchange-server-2010/ee332361(v=exchg.141))

  - [Exchange 2007 Kuruluşunu Kaldırma](/previous-versions/office/exchange-server-2007/aa998313(v=exchg.80))

  - [Exchange Server 2003'ü Kaldırma](/previous-versions/tn-archive/bb125110(v=exchg.65))
