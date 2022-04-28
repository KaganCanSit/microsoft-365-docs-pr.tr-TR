---
title: Microsoft 365'e IMAP geçişi gerçekleştirmek için PowerShell'i kullanma
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
ms.assetid: c28de4a5-1e8e-4491-9421-af066cde7cdd
description: PowerShell kullanarak Microsoft 365 İnternet Posta Erişim Protokolü (IMAP) geçişi gerçekleştirmeyi öğrenin.
ms.openlocfilehash: f93d56379dfa82ec3a369c89b35fc40d49fa1537
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65078661"
---
# <a name="use-powershell-to-perform-an-imap-migration-to-microsoft-365"></a>Microsoft 365'e IMAP geçişi gerçekleştirmek için PowerShell'i kullanma

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Microsoft 365 dağıtma işleminin bir parçası olarak, kullanıcı posta kutularının içeriğini bir İnternet Posta Erişim Protokolü (IMAP) e-posta hizmetinden Microsoft 365'a geçirmeyi seçebilirsiniz. Bu makalede, Exchange Online PowerShell kullanarak e-posta IMAP geçişiyle ilgili görevlerde size yol gösterilir.

> [!NOTE]
> IMAP geçişi gerçekleştirmek için <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezini</a> de kullanabilirsiniz. Bkz [. IMAP posta kutularınızı geçirme](/Exchange/mailbox-migration/migrating-imap-mailboxes/migrating-imap-mailboxes).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

Bu görevi tamamlamak için tahmini süre: Geçiş toplu işlemini oluşturmak için 2-5 dakika. Geçiş toplu işlemi başlatıldıktan sonra, geçiş süresi toplu işlemdeki posta kutularının sayısına, her posta kutusunun boyutuna ve kullanılabilir ağ kapasitenize göre değişir. Posta kutularının Microsoft 365 geçirilmesinin ne kadar sürdüğünü etkileyen diğer faktörler hakkında bilgi için bkz[. Geçiş Performansı](/Exchange/mailbox-migration/office-365-migration-best-practices).

Bu yordamı veya yordamları gerçekleştirebilmeniz için, önce izinlerin atanması gerekir. Hangi izinlere ihtiyacınız olduğunu görmek için [, Alıcılar İzinleri](/exchange/recipients-permissions-exchange-2013-help) konusunun bir tablosundaki "Geçiş" girdisine bakın.

Exchange Online PowerShell cmdlet'lerini kullanmak için oturum açmanız ve cmdlet'leri yerel Windows PowerShell oturumunuza aktarmanız gerekir. Yönergeler için bkz. [Uzak PowerShell kullanarak Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell).

Geçiş komutlarının tam listesi için bkz [. Taşıma ve geçiş cmdlet'leri](/powershell/exchange/).

IMAP geçişleri için aşağıdaki kısıtlamalar geçerlidir:

- Yalnızca kullanıcının gelen kutusundaki veya diğer posta klasörlerindeki öğeler geçirilebilir. Kişileri, takvim öğelerini veya görevleri geçiremezsiniz.

- Kullanıcının posta kutusundan en fazla 500.000 öğe geçirilebilir.

- Geçirilebilen ileti boyutu üst sınırı 35 MB'tır.

## <a name="migration-steps"></a>Geçiş adımları

### <a name="step-1-prepare-for-an-imap-migration"></a>1. Adım: IMAP geçişi için hazırlanma
<a name="BK_Step1"> </a>

- **IMAP kuruluşunuz için bir etki alanınız varsa, bunu Microsoft 365 kuruluşunuzun kabul edilen etki alanı olarak ekleyin.** Microsoft 365 posta kutularınız için zaten sahip olduğunuz etki alanını kullanmak istiyorsanız, önce Microsoft 365 kabul edilen etki alanı olarak eklemeniz gerekir. Ekledikten sonra kullanıcılarınızı Microsoft 365'de oluşturabilirsiniz. Daha fazla bilgi için bkz. [Etki alanınızı onaylama](../admin/setup/add-domain.md).

- **Posta kutusuna sahip olması için her kullanıcıyı Microsoft 365 ekleyin.** Yönergeler için bkz[. Kullanıcıları iş için Microsoft 365 ekleme](../admin/add-users/add-users.md).

- **IMAP sunucusunun FQDN'sini alın**. Bir IMAP geçiş uç noktası oluşturduğunuzda posta kutusu verilerini geçireceğiniz IMAP sunucusunun tam etki alanı adını (FQDN) (tam bilgisayar adı olarak da adlandırılır) sağlamanız gerekir. Internet üzerinden IMAP sunucusuyla iletişim kurmak için FQDN'yi kullanıp kullanamadığınızı doğrulamak için bir IMAP istemcisi veya PING komutu kullanın.

- **Güvenlik duvarını IMAP bağlantılarına izin verecek şekilde yapılandırın**. Geçiş sırasında Microsoft veri merkezinden kaynaklanan ağ trafiğinin IMAP sunucusunu barındıran kuruluşa girmesine izin verebilmek için IMAP sunucusunu barındıran kuruluşun güvenlik duvarında bağlantı noktalarını açmanız gerekebilir. Microsoft veri merkezleri tarafından kullanılan IP adreslerinin listesi için bkz. [EXCHANGE ONLINE URL'ler ve IP Adresi Aralıkları](./urls-and-ip-address-ranges.md).

- **IMAP kuruluşunuzdaki posta kutularına erişmek için yönetici hesabı izinlerini atayın**. CSV dosyasında yönetici kimlik bilgileri kullanırsanız, kullandığınız hesabın kurum içi posta kutularına erişmek için gerekli izinlere sahip olması gerekir. Kullanıcı posta kutularına erişmek için gereken izinler, belirli bir IMAP sunucusu tarafından belirlenir.

- **Exchange Online PowerShell cmdlet'lerini kullanmak için** oturum açmanız ve cmdlet'leri yerel Windows PowerShell oturumunuza aktarmanız gerekir. Yönergeler için bkz. [Uzak PowerShell kullanarak Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell).

    Geçiş komutlarının tam listesi için bkz [. Taşıma ve geçiş cmdlet'leri](/powershell/exchange/).

- **IMAP sunucunuza bağlanabildiğinizi doğrulayın**. IMAP sunucunuza bağlantı ayarlarını test etmek için Exchange Online PowerShell'de aşağıdaki komutu çalıştırın.

  ```powershell
  Test-MigrationServerAvailability -IMAP -RemoteServer <FQDN of IMAP server> -Port <143 or 993> -Security <None, Ssl, or Tls>
  ```

    **Port** parametresinin değeri için, şifrelenmemiş veya Aktarım Katmanı Güvenliği (TLS) bağlantıları için 143 kullanmak ve SSL bağlantıları için 993 kullanmak normaldir.

### <a name="step-2-create-a-csv-file-for-an-imap-migration-batch"></a>2. Adım: IMAP geçiş toplu işlemi için CSV dosyası oluşturma

Posta kutularını bir IMAP geçiş toplu işlemiyle geçirmek istediğiniz kullanıcı grubunu belirleyin. CSV dosyasındaki her satır, IMAP mesajlaşma sistemindeki bir posta kutusuna bağlanmak için gereken bilgileri içerir.

Her kullanıcı için gerekli öznitelikler şunlardır:

- **EmailAddress**, kullanıcının Microsoft 365 posta kutusunun kullanıcı kimliğini belirtir.

- **UserName** , IMAP sunucusundaki posta kutusuna erişmek için kullanılacak hesabın oturum açma adını belirtir.

- **Password** , **UserName** sütununda hesabın parolasını belirtir.

Aşağıda, CSV dosyasının biçimi için bir örnek verilmiştir. Bu örnekte üç posta kutusu geçirilir:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams,1091990
annb@contoso.edu,ann.beebe,2111991
paulc@contoso.edu,paul.cannon,3281986
```

**UserName** özniteliği için, kullanıcı adına ek olarak, IMAP sunucusundaki posta kutularına erişmek için gerekli izinlere atanmış bir hesabın kimlik bilgilerini kullanabilirsiniz. IMAP sunucularından bazıları için kullanılan belirli biçimlerden bazıları şunlardır:

 **Microsoft Exchange:**

E-postayı Microsoft Exchange için IMAP uygulamasından geçiriyorsanız, CSV dosyasındaki **UserName** özniteliğinde **Domain/Admin_UserName/User_UserName** biçimini kullanın. Terry Adams, Ann Beebe ve Paul Cannon için Exchange'den e-posta geçişi yaptığınızı varsayalım. Kullanıcı adı **mailadmin**, parola ise **Pssw0rd\@** olan bir posta yöneticisi hesabınız var. CSV dosyanız şöyle görünebilir:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,contoso-students/mailadmin/terry.adams,P@ssw0rd
annb@contoso.edu,contoso-students/mailadmin/ann.beebe,P@ssw0rd
paulc@contoso.edu,contoso-students/mailadmin/paul.cannon,P@ssw0rd
```

 **Dovecot:**

Dovecot IMAP sunucusu gibi Basit Kimlik Doğrulama ve Güvenlik Katmanı'nı (SASL) destekleyen IMAP sunucuları için, **User_UserName*Admin_UserName** biçimini kullanın; burada yıldız işareti ( * ) yapılandırılabilir bir ayırıcı karakterdir. Aynı kullanıcıların e-postalarını **mailadmin** ve **Pssw0rd\@** yönetici kimlik bilgilerini kullanarak bir Dovecot IMAP sunucusundan geçiriyorsunuz diyelim. CSV dosyanız şöyle görünebilir:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams*mailadmin,P@ssw0rd
annb@contoso.edu,ann.beebe*mailadmin,P@ssw0rd
paulc@contoso.edu,paul.cannon*mailadmin,P@ssw0rd
```

 **Mirapoint:**

E-postayı Mirapoint İleti Sunucusu'ndan geçiriyorsanız yönetici kimlik bilgileri için **#user\@ domain#Admin_UserName#** biçimini kullanın. **e-postayı mailadmin** ve **Pssw0rd\@** yönetici kimlik bilgilerini kullanarak Mirapoint'ten geçirmek için CSV dosyanız şöyle görünür:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,#terry.adams@contoso-students.edu#mailadmin#,P@ssw0rd
annb@contoso.edu,#ann.beebe@contoso-students.edu#mailadmin#,P@ssw0rd
paulc@contoso.edu,#paul.cannon@contoso-students.edu#mailadmin#,P@ssw0rd
```

 **Courier IMAP:**

Courier IMAP gibi bazı kaynak e-posta sistemleri, posta kutularını Microsoft 365 geçirmek için posta kutusu yöneticisi kimlik bilgilerinin kullanılmasını desteklemez. Bunun yerine, kaynak e-posta sisteminizi sanal paylaşılan klasörleri kullanacak şekilde ayarlayabilirsiniz. Sanal paylaşılan klasörleri kullanarak, kaynak e-posta sistemindeki kullanıcı posta kutularına erişmek için posta kutusu yöneticisi kimlik bilgilerini kullanabilirsiniz. Courier IMAP için sanal paylaşılan klasörleri yapılandırma hakkında daha fazla bilgi için bkz. [Paylaşılan Klasörler](https://go.microsoft.com/fwlink/p/?LinkId=398870).

Kaynak e-posta sisteminizde sanal paylaşılan klasörleri ayarladıktan sonra posta kutularını geçirmek için, geçiş dosyasına isteğe bağlı **UserRoot** özniteliğini eklemeniz gerekir. Bu öznitelik, kaynak e-posta sisteminde her kullanıcının posta kutusunun sanal paylaşılan klasör yapısındaki konumunu belirtir. Örneğin, Terry'nin posta kutusunun yolu /users/terry.adams şeklindedir.

Aşağıda, **UserRoot** özniteliğini içeren bir CSV dosyası örneği verilmiştir:

```powershell
EmailAddress,UserName,Password,UserRoot
terrya@contoso.edu,mailadmin,P@ssw0rd,/users/terry.adams
annb@contoso.edu,mailadmin,P@ssw0rd,/users/ann.beebe
paulc@contoso.edu,mailadmin,P@ssw0rd,/users/paul.cannon
```

### <a name="step-3-create-an-imap-migration-endpoint"></a>3. Adım: IMAP geçiş uç noktası oluşturma

E-postayı başarıyla geçirmek için Microsoft 365 kaynak e-posta sistemine bağlanması ve bu sistemle iletişim kurması gerekir. Bunu yapmak için Microsoft 365 bir geçiş uç noktası kullanır. Geçiş uç noktası, artımlı eşitleme sırasında eşzamanlı olarak eşitlenecek posta kutularının sayısını ve her 24 saatte bir gerçekleşen posta kutularının sayısını da tanımlar. IMAP geçişi için bir geçiş bitiş noktası oluşturmak için önce [Exchange Online bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

Geçiş komutlarının tam listesi için bkz [. Taşıma ve geçiş cmdlet'leri](/powershell/exchange/).

Exchange Online PowerShell'de "IMAPEndpoint" adlı IMAP geçiş uç noktasını oluşturmak için aşağıdaki komutu çalıştırın:

```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 993 -Security Ssl

```

Eşzamanlı geçişleri, eşzamanlı artımlı geçişleri ve kullanılacak bağlantı noktasını belirtmek için parametreler de ekleyebilirsiniz. Aşağıdaki Exchange Online PowerShell komutu, 50 eşzamanlı geçişi ve 25'e kadar eşzamanlı artımlı eşitlemeyi destekleyen "IMAPEndpoint" adlı bir IMAP geçiş uç noktası oluşturur. Ayrıca uç noktayı TLS şifrelemesi için 143 numaralı bağlantı noktasını kullanacak şekilde yapılandırıyor.

```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 143 -Security Tls -MaxConcurrentMigrations
50 -MaxConcurrentIncrementalSyncs 25
```

**New-MigrationEndpoint** cmdlet'i hakkında daha fazla bilgi için [bkz.Yeni-MigrationEndpoint](/powershell/module/exchange/new-migrationendpoint).

#### <a name="verify-it-worked"></a>Çalıştığını doğrulayın

"IMAPEndpoint" hakkındaki bilgileri görüntülemek için Exchange Online PowerShell'de aşağıdaki komutu çalıştırın:

```powershell
Get-MigrationEndpoint IMAPEndpoint | Format-List EndpointType,RemoteServer,Port,Security,Max*
```

### <a name="step-4-create-and-start-an-imap-migration-batch"></a>4. Adım: IMAP geçiş toplu işlemini oluşturma ve başlatma

IMAP geçişi için bir geçiş toplu işlemi oluşturmak için [New-MigrationBatch](/powershell/module/exchange/new-migrationbatch) cmdlet'ini kullanabilirsiniz. _Otomatik Başlangıç_ parametresini ekleyerek bir geçiş toplu işlemi oluşturabilir ve bunu otomatik olarak başlatabilirsiniz. Alternatif olarak, geçiş toplu işlemini oluşturabilir ve daha [sonraStart-MigrationBatch](/powershell/module/exchange/start-migrationbatch) cmdlet'ini kullanarak başlatabilirsiniz.

Aşağıdaki Exchange Online PowerShell komutu, "IMAPEndpoint" adlı IMAP uç noktasını kullanarak "IMAPBatch1" adlı geçiş toplu işlemini otomatik olarak başlatır:

```powershell
New-MigrationBatch -Name IMAPBatch1 -SourceEndpoint IMAPEndpoint -CSVData ([System.IO.File]::ReadAllBytes("C:\Users\Administrator\Desktop\IMAPmigration_1.csv")) -AutoStart
```

#### <a name="verify-it-worked"></a>Çalıştığını doğrulayın

"IMAPBatch1" hakkındaki bilgileri görüntülemek için [Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch) cmdlet'ini çalıştırın:

```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List
```

Aşağıdaki komutu çalıştırarak toplu işleminin başlatıldığını da doğrulayabilirsiniz:

```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a>5. Adım: E-postanızı Microsoft 365 yönlendirme

E-posta sistemleri, e-postaların teslim edileceği yeri belirlemek için MX kaydı olarak adlandırılan bir DNS kaydını kullanır. E-posta geçiş işlemi sırasında, MX kaydınız kaynak e-posta sisteminize işaret ediyor olur. Microsoft 365'a e-posta geçişi tamamlandıktan sonra MX kaydınızı Microsoft 365 işaret etme zamanı geldi. Bu, e-postanın Microsoft 365 posta kutularınıza teslim edilmiş olmasına yardımcı olur. MX kaydını taşıyarak, hazır olduğunuzda eski e-posta sisteminizi de kapatabilirsiniz.

Birçok DNS sağlayıcısı için, MX kaydınızı değiştirmeye yönelik belirli yönergeler sağlanmıştır. DNS sağlayıcınız bunların arasında değilse veya genel yönergeler hakkında fikir edinmek istiyorsanız, [genel MX kaydı yönergeleri](https://go.microsoft.com/fwlink/?LinkId=397449) de sağlanmıştır.

Müşterilerinizin ve iş ortaklarınızın e-posta sistemlerinin değişen MX kaydını fark etmesi 72 saat kadar sürebilir. Sonraki göreve geçmeden önce en az 72 saat bekleyin: 6. Adım: IMAP geçiş toplu işlemini silme.

### <a name="step-6-delete-imap-migration-batch"></a>6. Adım: IMAP geçiş toplu işlemini silme

MX kaydını değiştirdikten ve tüm e-postaların Microsoft 365 posta kutularına yönlendirildiğini doğruladıktan sonra, kullanıcılara postalarının Microsoft 365 bildirin. Bundan sonra, IMAP geçiş toplu işlemini silebilirsiniz. Geçiş toplu işlemini silmeden önce aşağıdakileri doğrulayın.

- Tüm kullanıcılar Microsoft 365 posta kutularını kullanıyor. Toplu iş silindikten sonra, şirket içi Exchange Server posta kutularına gönderilen postalar ilgili Microsoft 365 posta kutularına kopyalanır.

- Microsoft 365 posta kutuları, posta doğrudan gönderilmeye başladıktan sonra en az bir kez eşitlendi. Bunu yapmak için, geçiş toplu işleminin Son Eşitlenen Saat kutusundaki değerin, postanın doğrudan Microsoft 365 posta kutularına yönlendirilmeye başlamasından daha yeni olduğundan emin olun.

Exchange Online PowerShell'den "IMAPBatch1" geçiş toplu işlemini silmek için aşağıdaki komutu çalıştırın:

```powershell
Remove-MigrationBatch -Identity IMAPBatch1
```

**Remove-MigrationBatch** cmdlet'i hakkında daha fazla bilgi için [bkz.Remove-MigrationBatch](/powershell/module/exchange/remove-migrationbatch).

#### <a name="verify-it-worked"></a>Çalıştığını doğrulayın

"IMAPBatch1" hakkındaki bilgileri görüntülemek için Exchange Online PowerShell'de aşağıdaki komutu çalıştırın:

```powershell
Get-MigrationBatch IMAPBatch1"
```

Komut, **Kaldırılıyor** durumuna sahip geçiş toplu işlemini döndürür veya toplu işleminin silindiğini doğrulayarak geçiş toplu işleminin bulunamadığını belirten bir hata döndürür.

**Get-MigrationBatch** cmdlet'i hakkında daha fazla bilgi için [bkz.Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

## <a name="see-also"></a>Ayrıca bkz.

[IMAP Geçiş Sorun Gidericisi](/exchange/troubleshoot/move-or-migrate-mailboxes/troubleshoot-issues-with-imap-mailbox-migration)