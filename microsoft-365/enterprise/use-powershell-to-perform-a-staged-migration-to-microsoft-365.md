---
title: Microsoft 365'e aşamalı geçiş gerçekleştirmek için PowerShell'i kullanma
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 06/07/2022
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
description: Microsoft 365'e aşamalı geçiş kullanarak zaman içinde kaynak e-posta sisteminden içerik taşımak için PowerShell'i kullanmayı öğrenin.
ms.openlocfilehash: 361bf6e2bdfc58ea79f73c3596622ae96b420648
ms.sourcegitcommit: a5e75d7f7651313818bd2de292d5c38b290d8975
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2022
ms.locfileid: "65930757"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-microsoft-365"></a>Microsoft 365'e aşamalı geçiş gerçekleştirmek için PowerShell'i kullanma

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Aşamalı geçiş kullanarak kullanıcı posta kutularının içeriğini bir kaynak e-posta sisteminden Microsoft 365'e zaman içinde geçirebilirsiniz.

Bu makalede, Exchange Online PowerShell kullanarak aşamalı e-posta geçişi için ilgili görevler açıklanmıştır. [Aşamalı e-posta geçişi hakkında bilmeniz gerekenler](/Exchange/mailbox-migration/what-to-know-about-a-staged-migration) konusu, geçiş işlemine genel bir bakış sağlar. Bu makalenin içeriğini rahatça anladığınızda, posta kutularını bir e-posta sisteminden diğerine geçirmeye başlamak için bunu kullanın.

> [!NOTE]
> Aşamalı geçiş gerçekleştirmek için <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezini</a> de kullanabilirsiniz. Bkz. [E-postanın Microsoft 365'e aşamalı geçişini gerçekleştirme](/Exchange/mailbox-migration/perform-a-staged-migration/perform-a-staged-migration).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

Bu görevi tamamlamak için tahmini süre: Geçiş toplu işlemini oluşturmak için 2-5 dakika. Geçiş toplu işlemi başlatıldıktan sonra, geçiş süresi toplu işlemdeki posta kutularının sayısına, her posta kutusunun boyutuna ve kullanılabilir ağ kapasitenize göre değişir. Posta kutularının Microsoft 365'e geçirilmesinin ne kadar sürdüğünü etkileyen diğer faktörler hakkında bilgi için bkz [. Geçiş Performansı](/Exchange/mailbox-migration/office-365-migration-best-practices).

Bu yordamı veya yordamları gerçekleştirebilmeniz için, önce izinlerin atanması gerekir. Hangi izinlere ihtiyacınız olduğunu görmek için [Alıcılar İzinleri](/exchange/recipients-permissions-exchange-2013-help) konusunda "Geçiş" girdisine bakın.

Exchange Online PowerShell cmdlet'lerini kullanmak için oturum açmanız ve cmdlet'leri yerel Windows PowerShell oturumunuza aktarmanız gerekir. Yönergeler için bkz. [Uzak PowerShell kullanarak Exchange Online'a bağlanma](/powershell/exchange/connect-to-exchange-online-powershell) .

Geçiş komutlarının tam listesi için bkz [. Taşıma ve geçiş cmdlet'leri](/powershell/exchange/).

## <a name="migration-steps"></a>Geçiş adımları

### <a name="step-1-prepare-for-a-staged-migration"></a>1. Adım: Aşamalı geçişe hazırlanma

Aşamalı geçiş kullanarak posta kutularını Microsoft 365'e geçirmeden önce Exchange ortamınızda yapmanız gereken birkaç değişiklik vardır.

 **Her Yerden Outlook'u şirket içi Exchange Server**'ınızda yapılandırma E-posta geçiş hizmeti şirket içi Exchange Server'ınıza bağlanmak için Her Yerden Outlook (HTTP üzerinden RPC olarak da bilinir) kullanır. Exchange Server 2007 ve Exchange 2003 için Outlook Anywhere'yi ayarlama hakkında bilgi için aşağıdakilere bakın:

- [Exchange 2007: Her Yerden Outlook'u Etkinleştirme](/previous-versions/office/exchange-server-2007/bb123889(v=exchg.80))

- [Her Yerden Outlook'u Exchange 2003'le yapılandırma](/previous-versions/office/exchange-server-2007/aa996922(v=exchg.80))

> [!IMPORTANT]
> Her Yerden Outlook yapılandırmanızla, güvenilir bir sertifika yetkilisi (CA) tarafından verilmiş bir sertifika kullanmalısınız. Her Yerden Outlook, otomatik olarak imzalanan sertifikayla yapılandırılamaz. Daha fazla bilgi için bkz. [Her Yerden Outlook için SSL'yi yapılandırma](/previous-versions/office/exchange-server-2007/aa995982(v=exchg.80)).

 **İsteğe bağlı: Her Yerden Outlook kullanarak Exchange kuruluşunuza bağlanabildiğinizi doğrulama** Bağlantı ayarlarınızı test etmek için aşağıdaki yöntemlerden birini deneyin.

- Şirket içi Exchange posta kutunuza bağlanmak için şirket ağınızın dışından Outlook'u kullanın.

- Bağlantı ayarlarınızı test etmek için [Microsoft Uzak Bağlantı Çözümleyicisi'ni](https://https://testconnectivity.microsoft.com/) kullanın. Her Yerden Outlook (HTTP üzerinden RPC) veya Outlook Otomatik Bulma testlerini kullanın.

- Exchange Online PowerShell'de aşağıdaki komutları çalıştırın:

  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **İzinleri ayarlama** Şirket içi Exchange kuruluşunuza bağlanmak için kullandığınız şirket içi kullanıcı hesabının (geçiş yöneticisi olarak da adlandırılır) Microsoft 365'e geçirmek istediğiniz şirket içi posta kutularına erişmek için gerekli izinlere sahip olması gerekir. Bu kullanıcı hesabı, [3. Adım:](#step-3-create-a-migration-endpoint) Geçiş uç noktası oluşturma yordamının ilerleyen bölümlerinde bir geçiş uç noktası oluşturarak e-posta sisteminize bağlandığınızda kullanılır.

Posta kutularını geçirmek için yöneticinin şu izin kümelerinden birine sahip olması gerekir:

- Şirket içi kuruluşta Active Directory'de **Domain Admins** grubunun üyesi olun.

    veya

- Şirket içi kullanıcı hesaplarında **TargetAddress** özelliğini değiştirmek için her şirket içi posta kutusu için **FullAccess** izni ve **WriteProperty** izni atanmalıdır.

    veya

- Kullanıcı posta kutularını depolayan şirket içi posta kutusu veritabanında **Farklı Al** iznine ve şirket içi kullanıcı hesaplarında **TargetAddress** özelliğini değiştirmek için **WriteProperty** iznine atanmalıdır.

Bu izinleri ayarlama hakkında yönergeler için bkz. [Posta kutularını Microsoft 365'e geçirmek için izin atama](/Exchange/mailbox-migration/assign-permissions-for-migration).

 **Birleşik Mesajlaşmayı Devre Dışı Bırakma (UM)** Geçirmekte olduğunuz şirket içi posta kutuları için UM açıksa geçişten önce UM'yi kapatın. Geçiş tamamlandıktan sonra posta kutuları için UM'yi açın. Nasıl yapılır adımları için bkz.[Birleşik mesajlaşmayı devre dışı bırakma](/previous-versions/office/exchange-server-2007/bb124691(v=exchg.80)).

 **Microsoft 365'te yeni kullanıcılar oluşturmak için dizin eşitlemesini kullanın.** Dizin eşitlemesini, Microsoft 365 kuruluşunuzdaki tüm şirket içi kullanıcıları oluşturmak için kullanırsınız.

Oluşturulduktan sonra kullanıcıları lisanslamalısınız. Kullanıcılar oluşturulduktan sonra lisans eklemek için 30 gününüz vardır. Lisans ekleme adımları için bkz [. 8. Adım: Geçiş sonrası görevleri tamamlama](#step-8-complete-post-migration-tasks).

 Microsoft 365'te şirket içi kullanıcılarınızı eşitlemek ve oluşturmak için Microsoft Azure Active Directory (Azure AD) Eşitleme Aracı'nı veya Microsoft Azure AD Eşitleme Hizmetleri'ni kullanabilirsiniz. Posta kutuları Microsoft 365'e geçirildikten sonra, şirket içi kuruluşunuzdaki kullanıcı hesaplarını yönetirsiniz ve bunlar Microsoft 365 kuruluşunuzla eşitlenir. Daha fazla bilgi için bkz[. Dizin Tümleştirmesi](/previous-versions/azure/azure-services/jj573653(v=azure.100)) .

### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>2. Adım: Aşamalı geçiş toplu işlemi için CSV dosyası oluşturma

Şirket içi posta kutularını Microsoft 365'e geçirmek istediğiniz kullanıcıları belirledikten sonra, geçiş toplu işlemi oluşturmak için virgülle ayrılmış değer (CSV) dosyası kullanırsınız. Geçişi çalıştırmak için Microsoft 365 tarafından kullanılan CSV dosyasındaki her satır, şirket içi posta kutusu hakkında bilgi içerir.

> [!NOTE]
> Aşamalı geçiş kullanarak Microsoft 365'e geçirebileceğiniz posta kutusu sayısı için bir sınır yoktur. Geçiş toplu işleminde kullanılan CSV dosyası en çok 2.000 satır içerebilir. 2.000'den çok posta kutusunu geçirmek için, ek CSV dosyaları oluşturun ve her dosyayı yeni bir geçiş toplu işlemi oluşturmak için kullanın.

 **Desteklenen öznitelikler**

Aşamalı geçiş için CSV dosyası aşağıdaki üç özniteliği destekler. CSV dosyasındaki her satır bir posta kutusuna karşılık gelir ve bu özniteliklerin her biri için bir değer içermelidir.

|**Öznitelik**|**Açıklama**|**Gerekli mi?**|
|:-----|:-----|:-----|
|Emailaddress  <br/> |Şirket içi posta kutuları için birincil SMTP e-posta adresini belirtir; örneğin, pilarp@contoso.com.  <br/> Microsoft 365'ten kullanıcı kimlikleri değil, şirket içi posta kutuları için birincil SMTP adresini kullanın. Örneğin, şirket içi etki alanının adı contoso.com ancak Microsoft 365 e-posta etki alanı service.contoso.com olarak adlandırılmışsa, CSV dosyasındaki e-posta adresleri için contoso.com etki alanı adını kullanırsınız.  <br/> |Gerekli  <br/> |
|Password  <br/> |Yeni Microsoft 365 posta kutusu için ayarlanacak parola. Microsoft 365 kuruluşunuza uygulanan tüm parola kısıtlamaları CSV dosyasındaki parolalar için de geçerlidir.  <br/> |İsteğe bağlı  <br/> |
|Forcechangepassword  <br/> |Kullanıcının yeni Microsoft 365 posta kutusunda ilk kez oturum açışında parolayı değiştirmesi gerekip gerekmediğini belirtir. Bu parametrenin değeri olarak **True** veya **False** kullanın. <br/> > [!NOTE]> Şirket içi kuruluşunuzda Active Directory Federasyon Hizmetleri (AD FS) veya üzerini dağıtarak bir çoklu oturum açma (SSO) çözümü uyguladıysanız **ForceChangePassword** özniteliğinin değeri için **False** kullanmanız gerekir.          |İsteğe bağlı  <br/> |

 **CSV dosya biçimi**

Aşağıda, CSV dosyasının biçimi için bir örnek verilmiştir. Bu örnekte, üç şirket içi posta kutusu Microsoft 365'e geçirilir.

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
> CSV dosyası ASCII olmayan veya özel karakterler içeriyorsa, CSV dosyasını UTF-8 veya başka bir Unicode kodlamayla kaydedin. Uygulamaya bağlı olarak, bilgisayarın sistem yerel ayarı CSV dosyasında kullanılan dille eşleştiğinde CSV dosyasını UTF-8 veya diğer Unicode kodlamasıyla kaydetmek daha kolay olabilir.

### <a name="step-3-create-a-migration-endpoint"></a>3. Adım: Geçiş uç noktası oluşturma

E-postayı başarıyla geçirmek için Microsoft 365'in kaynak e-posta sistemine bağlanması ve bu sistemle iletişim kurması gerekir. Bunu yapmak için Microsoft 365 bir geçiş uç noktası kullanır. PowerShell kullanarak bir Outlook Anywhere geçiş uç noktası oluşturmak için, aşamalı geçiş için önce [Exchange Online'a bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

Geçiş komutlarının tam listesi için bkz [. Taşıma ve geçiş cmdlet'leri](/powershell/exchange/).

Exchange Online PowerShell'de "StagedEndpoint" adlı bir Outlook Anywhere geçiş uç noktası oluşturmak için aşağıdaki komutları çalıştırın:

```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

**New-MigrationEndpoint** cmdlet'i hakkında daha fazla bilgi için bkz.[New-MigrationEndpoint](/powershell/module/exchange/new-migrationendpoint).

> [!NOTE]
> **New-MigrationEndpoint** cmdlet'i **, -TargetDatabase** seçeneği kullanılarak hizmetin kullanacağı bir veritabanı belirtmek için kullanılabilir. Aksi takdirde bir veritabanı, yönetim posta kutusunun bulunduğu Active Directory Federasyon Hizmetleri (AD FS) 2.0 sitesinden rastgele atanır.

#### <a name="verify-it-worked"></a>Çalıştığını doğrulayın

Exchange Online PowerShell'de, "StagedEndpoint" geçiş uç noktası hakkındaki bilgileri görüntülemek için aşağıdaki komutu çalıştırın:

```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>4. Adım: Aşama geçişi toplu işlemini oluşturma ve başlatma

Tam geçiş için bir geçiş toplu işlemi oluşturmak için Exchange Online PowerShell'de **New-MigrationBatch** cmdlet'ini kullanabilirsiniz. _Otomatik Başlangıç_ parametresini ekleyerek bir geçiş toplu işlemi oluşturabilir ve bunu otomatik olarak başlatabilirsiniz. Alternatif olarak, geçiş toplu işlemini oluşturabilir ve daha sonra **Start-MigrationBatch** cmdlet'ini kullanarak el ile başlatabilirsiniz. Bu örnek, "StagedBatch1" adlı bir geçiş toplu işlemi oluşturur ve önceki adımda oluşturulan geçiş uç noktasını kullanır.

```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

Bu örnek ayrıca "StagedBatch1" adlı bir geçiş toplu işlemi oluşturur ve önceki adımda oluşturulan geçiş uç noktasını kullanır. _AutoStart_ parametresi dahil edilmediğinden, geçiş toplu işleminin geçiş panosunda veya **Start-MigrationBatch** cmdlet'i kullanılarak el ile başlatılması gerekir. Daha önce belirtildiği gibi, aynı anda yalnızca bir tam geçiş toplu işlemi bulunabilir.

```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a>Çalıştığını doğrulayın

"StagedBatch1" hakkındaki bilgileri görüntülemek için Exchange Online PowerShell'de aşağıdaki komutu çalıştırın:

```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

Aşağıdaki komutu çalıştırarak toplu işleminin başlatıldığını da doğrulayabilirsiniz:

```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

**Get-MigrationBatch** cmdlet'i hakkında daha fazla bilgi için bkz.[Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a>5. Adım: Şirket içi posta kutularını posta özellikli kullanıcılara dönüştürme

Bir grup posta kutusunu başarıyla geçirdikten sonra, kullanıcıların e-postalarına ulaşmalarını sağlamak için bir yol bulmanız gerekir. Posta kutusu geçirilen bir kullanıcının hem şirket içinde hem de Microsoft 365'te bir posta kutusu vardır. Microsoft 365'te posta kutusu olan kullanıcılar şirket içi posta kutularına yeni posta almayı durdurur.

Geçiş işlemleriniz tamamlanmamış olduğundan, tüm kullanıcıları e-postaları için Microsoft 365'e yönlendirmeye henüz hazır değilsiniz. Peki her iki posta kutusu da olan kişiler için ne yapacaksınız? Yapabileceğiniz, zaten geçirmiş olduğunuz şirket içi posta kutularını posta özelliği etkin kullanıcılara dönüştürmektir. Posta kutusundan posta özellikli bir kullanıcıya geçiş yaptığınızda, kullanıcıyı şirket içi posta kutusuna gitmek yerine e-postası için Microsoft 365'e yönlendirebilirsiniz.

Şirket içi posta kutularını posta özellikli kullanıcılara dönüştürmenin bir diğer önemli nedeni de, proxy adreslerini posta özellikli kullanıcılara kopyalayarak Microsoft 365 posta kutularından ara sunucu adreslerini korumaktır. Bu, Active Directory kullanarak şirket içi kuruluşunuzdaki bulut tabanlı kullanıcıları yönetebilmenizi sağlar. Ayrıca, tüm posta kutuları Microsoft 365'e geçirildikten sonra şirket içi Exchange Server kuruluşunuzun yetkisini kaldırmaya karar verirseniz, posta özellikli kullanıcılara kopyaladığınız proxy adresleri şirket içi Active Directory'nizde kalır.

### <a name="step-6-delete-a-staged-migration-batch"></a>6. Adım: Aşamalı geçiş toplu işlemini silme

 Geçiş toplu işlemindeki tüm posta kutuları başarıyla geçirildikten ve toplu işteki şirket içi posta kutularını posta özellikli kullanıcılara dönüştürdükten sonra, aşamalı geçiş toplu işlemini silmeye hazır olursunuz. Postanın geçiş toplu işlemindeki Microsoft 365 posta kutularına iletildiğini doğrulamayı unutmayın. Aşamalı bir geçiş toplu işlemini sildiğinizde, geçiş hizmeti geçiş toplu işlemiyle ilgili tüm kayıtları temizler ve geçiş toplu işlemini siler.

Exchange Online PowerShell'de "StagedBatch1" geçiş toplu işlemini silmek için aşağıdaki komutu çalıştırın.

```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

**Remove-MigrationBatch** cmdlet'i hakkında daha fazla bilgi için bkz.[Remove-MigrationBatch](/powershell/module/exchange/remove-migrationbatch).

#### <a name="verify-it-worked"></a>Çalıştığını doğrulayın

"IMAPBatch1" hakkındaki bilgileri görüntülemek için Exchange Online PowerShell'de aşağıdaki komutu çalıştırın:

```powershell
Get-MigrationBatch StagedBatch1
```

Komut, **Kaldırılıyor** durumuna sahip geçiş toplu işlemini döndürür veya toplu işleminin silindiğini doğrulayarak geçiş toplu işleminin bulunamadığını belirten bir hata döndürür.

**Get-MigrationBatch** cmdlet'i hakkında daha fazla bilgi için bkz.[Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

### <a name="step7-assign-licenses-to-microsoft-365-users"></a>7. Adım: Microsoft 365 kullanıcılarına lisans atama

Lisans atayarak geçirilen hesaplar için Microsoft 365 kullanıcı hesaplarını etkinleştirin. Lisans atamazsanız, yetkisiz kullanım süresi (30 gün) sona erdiğinde posta kutusu devre dışı bırakılır. Microsoft 365 yönetim merkezinde lisans atamak için bkz. [Lisans atama veya atamasını kaldırma](../admin/manage/assign-licenses-to-users.md).

### <a name="step-8-complete-post-migration-tasks"></a>8. Adım: Geçiş sonrası görevleri tamamlama

- **Kullanıcıların posta kutularına kolayca ulaşabilmeleri için bir Otomatik Bulma DNS kaydı oluşturun.** Tüm şirket içi posta kutuları Microsoft 365'e geçirildikten sonra, kullanıcıların Outlook ve mobil istemcilerle yeni Microsoft 365 posta kutularına kolayca bağlanmasını sağlamak üzere Microsoft 365 kuruluşunuz için bir Otomatik Bulma DNS kaydı yapılandırabilirsiniz. Bu yeni Otomatik Bulma DNS kaydının, Microsoft 365 kuruluşunuz için kullandığınız ad alanını kullanması gerekir. Örneğin, bulut tabanlı ad alanınız bulut.contoso.com ise, oluşturmanız gereken Otomatik Bulma DNS kaydı autodiscover.bulut.contoso.com'dur.

    Microsoft 365, Outlook ve mobil istemciler için Otomatik Bulma hizmetini uygulamak için bir CNAME kaydı kullanır. Otomatik Bulma CNAME kaydı aşağıdaki bilgileri içermelidir:

  - **Alias:** autodiscover

  - **Target:** autodiscover.outlook.com

    Daha fazla bilgi için bkz. [Etki alanınıza bağlanmak için DNS kayıtları ekleme](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

- **Şirket içi Exchange sunucularının yetkisini alın.** Tüm e-postaların doğrudan Microsoft 365 posta kutularına yönlendirildiğini doğruladıktan ve şirket içi e-posta kuruluşunuzun bakımını yapmanıza gerek kalmadıktan veya bir SSO çözümü uygulamayı planlamadığınızda Exchange'i sunucularınızdan kaldırabilir ve şirket içi Exchange kuruluşunuzu kaldırabilirsiniz.

> [!NOTE]
> Exchange'in yetkisinin alınması istenmeyen sonuçlara neden olabilir. Şirket içi Exchange kuruluşunuzun yetkisini almadan önce, Microsoft Desteği'ne başvurmanızı öneririz.

Daha fazla bilgi için aşağıdakilere bakın:

- [Exchange 2010'u Değiştirme veya Kaldırma](/previous-versions/office/exchange-server-2010/ee332361(v=exchg.141))

- [Exchange 2007 Kuruluşunu Kaldırma](/previous-versions/office/exchange-server-2007/aa998313(v=exchg.80))

- [Exchange Server 2003'ü Kaldırma](/previous-versions/tn-archive/bb125110(v=exchg.65))
