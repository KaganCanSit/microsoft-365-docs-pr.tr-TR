---
title: Microsoft 365'a IMAP geçişi gerçekleştirmek için PowerShell Microsoft 365
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
ms.assetid: c28de4a5-1e8e-4491-9421-af066cde7cdd
description: İnternet Posta Erişim Protokolü (IMAP) geçişini gerçekleştirmek için PowerShell'i kullanmayı Microsoft 365.
ms.openlocfilehash: 0c546782e81a399f092c8c7878b52c419adee799
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "63018800"
---
# <a name="use-powershell-to-perform-an-imap-migration-to-microsoft-365"></a>Microsoft 365'a IMAP geçişi gerçekleştirmek için PowerShell Microsoft 365

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Microsoft 365'i dağıtma işleminin bir parçası olarak, kullanıcı posta kutularının içeriğini İnternet Posta Erişim Protokolü (IMAP) e-posta hizmetlerinden posta kutusuna geçirmeyi Microsoft 365. Bu makalede, Exchange Online PowerShell kullanarak e-posta IMAP geçişiyle Exchange Online yol gösterir.

> [!NOTE]
> Ayrıca, IMAP <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">geçişini Exchange yönetim</a> merkezini de kullanabilirsiniz. Bkz [. IMAP posta kutularınızı geçirme](/Exchange/mailbox-migration/migrating-imap-mailboxes/migrating-imap-mailboxes).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

Bu görevi tamamlamak için tahmini süre: Geçiş toplu işlemini oluşturmak için 2-5 dakika. Geçiş toplu işlemi başlatıldıktan sonra, toplu işlemde yer alan posta kutularının sayısına, her posta kutusunun boyutuna ve kullanılabilir ağ kapasitenize bağlı olarak geçiş süresi değişir. Posta kutularını bu posta kutusuna geçirmenin ne kadar sürer olduğunu etkileyen diğer faktörler hakkında bilgi Microsoft 365 bkz. [Geçiş Performansı](/Exchange/mailbox-migration/office-365-migration-best-practices).

Bu yordamı veya yordamları gerçekleştirebilmeniz için, önce izinlerin atanması gerekir. Size hangi izinlerin gerekli olduğunu görmek için, Alıcı İzinleri konu başlığında yer alan bir tabloda yer alan " [Geçiş" girdisini](/exchange/recipients-permissions-exchange-2013-help) bakın.

Exchange Online PowerShell cmdlet'lerini kullanmak için oturum açmalı ve cmdlet'leri yerel Windows PowerShell gerekir. Yönergeler [Bağlan uzak PowerShell Exchange Online için bkz. Uzak PowerShell'i](/powershell/exchange/connect-to-exchange-online-powershell) kullanma hakkında daha fazla bilgi.

Geçiş komutlarının tam listesi için bkz. [Taşıma ve geçiş cmdlet'leri](/powershell/exchange/).

IMAP geçişleri için aşağıdaki kısıtlamalar geçerlidir:

- Yalnızca kullanıcının gelen kutusunda veya diğer posta klasörlarında yer alan öğeler geçirilir. Kişileri, takvim öğelerini veya görevleri geçirebilirsiniz.

- Kullanıcının posta kutusundan en çok 500.000 öğe geçirebilirsiniz.

- En fazla ileti boyutu 35 MB'dir.

## <a name="migration-steps"></a>Geçiş adımları

### <a name="step-1-prepare-for-an-imap-migration"></a>1. Adım: IMAP geçişi için hazırlanma
<a name="BK_Step1"> </a>

- **IMAP kuruluşu için bir etki alanınız varsa, bunu kendi etki alanınız olan ve Microsoft 365 ekleyin.** Posta kutularınız için sahip olduğu etki alanını Microsoft 365 kullanmak için, önce bu etki alanını posta kutusuna kabul edilen bir etki alanı olarak Microsoft 365. Bunu ekledikten sonra, diğer kullanıcılar için yeni bir Microsoft 365. Daha fazla bilgi için bkz[. Etki alanlarınızı ortalama](../admin/setup/add-domain.md).

- **Posta kutusu olacak Microsoft 365 kullanıcı ekleme.** Yönergeler için bkz[. İşletmeler için Microsoft 365'e kullanıcı yükleme](../admin/add-users/add-users.md).

- **IMAP sunucusunun FQDN'lerini alın**. IMAP geçiş uç noktası bilgisayarınızda posta kutusu verilerini geçirtecek IMAP sunucusunun tam etki alanı adını (FQDN) (tam bilgisayar adı olarak da denir) sağlanız gerekir. Internet üzerinden IMAP sunucusuyla iletişim kurmak için FQDN'yi kullanıp kullanamadığınızı doğrulamak için bir IMAP istemcisi veya PING komutu kullanın.

- **Güvenlik duvarını IMAP bağlantılarına izin verecek şekilde yapılandırabilirsiniz**. Geçiş sırasında Microsoft veri merkezinden kaynaklanan ağ trafiğinin IMAP sunucusunu barındıran kuruluşa girmesine izin verilmiyor için, IMAP sunucusunu barındıran kuruluşun güvenlik duvarında bağlantı noktalarını açmanız gerekebilir. Microsoft veri merkezleri tarafından kullanılan IP adreslerinin listesi için bkz. EXCHANGE ONLINE [VE IP Adresi Aralıkları](./urls-and-ip-address-ranges.md).

- **IMAP kurumuzda posta kutularına erişim için yönetici hesabı izinlerini attayabilirsiniz**. CSV dosyasında yönetici kimlik bilgileri kullanırsanız, kullandığınız hesabın kurum içi posta kutularına erişmek için gerekli izinlere sahip olması gerekir. Kullanıcı posta kutularına erişim için gereken izinler, belirli IMAP sunucusu tarafından belirlenir.

- **Exchange Online PowerShell cmdlet'lerini** kullanmak için oturum açmalı ve cmdlet'leri yerel Windows PowerShell gerekir. Yönergeler [Bağlan uzak PowerShell Exchange Online için bkz. Uzak PowerShell'i](/powershell/exchange/connect-to-exchange-online-powershell) kullanma hakkında daha fazla bilgi.

    Geçiş komutlarının tam listesi için bkz. [Taşıma ve geçiş cmdlet'leri](/powershell/exchange/).

- **IMAP sunucunuza bağlananızı doğrulayın**. IMAP sunucunuzla bağlantı Exchange Online sınamak için PowerShell'de aşağıdaki komutu çalıştırın.

  ```powershell
  Test-MigrationServerAvailability -IMAP -RemoteServer <FQDN of IMAP server> -Port <143 or 993> -Security <None, Ssl, or Tls>
  ```

    Bağlantı Noktası parametresinin değeri  için, şifrelenmemiş veya Aktarım Katmanı Güvenliği (TLS) bağlantılarında 143 ve SSL bağlantıları için 993 kullanmak gerekir.

### <a name="step-2-create-a-csv-file-for-an-imap-migration-batch"></a>2. Adım: IMAP geçiş toplu işlemi için CSV dosyası oluşturma

Bir IMAP geçiş toplu işleminde posta kutularını geçirmek istediğiniz kullanıcı grubunu seçin. CSV dosyasındaki her satır, IMAP ileti sisteminde bir posta kutusuna bağlanmak için gereken bilgileri içerir.

Her kullanıcı için gerekli öznitelikler şunlardır:

- **EmailAddress**, kullanıcının posta kutusunun kullanıcı Microsoft 365 belirtir.

- **UserName** , IMAP sunucusundaki posta kutusuna erişmek için kullanmak üzere hesabın oturum açma adını belirtir.

- **Password** , **UserName** sütununda hesabın parolasını belirtir.

Aşağıda, CSV dosyasının biçimi için bir örnek verilmiştir. Bu örnekte, üç posta kutusu geçirilir:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams,1091990
annb@contoso.edu,ann.beebe,2111991
paulc@contoso.edu,paul.cannon,3281986
```

**UserName** özniteliğinde, kullanıcı adına ek olarak, IMAP sunucusundaki posta kutularına erişmek için gerekli izinlerin atandığı bir hesabın kimlik bilgilerini de kullanabilirsiniz; aşağıda, IMAP sunucularından bazıları için kullanılan belirli biçimlerden bazıları yer almaktadır:

 **Microsoft Exchange:**

E-postayı Microsoft Exchange için IMAP uygulamasından geçiriyorsanız, CSV dosyasındaki **UserName** özniteliğinde **Domain/Admin_UserName/User_UserName** biçimini kullanın. Terry Adams, Ann Beebe ve Paul Cannon için Exchange'den e-posta geçişi yaptığınızı varsayalım. Kullanıcı adı **mailadmin** ve parolası **Pssw0rd\@ olan bir posta yöneticisi hesabınız var**. CSV dosyanız şöyle görünebilir:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,contoso-students/mailadmin/terry.adams,P@ssw0rd
annb@contoso.edu,contoso-students/mailadmin/ann.beebe,P@ssw0rd
paulc@contoso.edu,contoso-students/mailadmin/paul.cannon,P@ssw0rd
```

 **Dovecot:**

Dovecot IMAP sunucusu gibi Basit Kimlik Doğrulama ve Güvenlik Katmanı'nın (SASL) destekleniyor olduğu IMAP sunucularında, yıldız ( * ) yapılandırılabilir bir ayırıcı karakter olduğu **User_UserName*Admin_UserName** biçimini kullanın. Aynı kullanıcıların e-postasını **, mailadmin** ve **Pssw0rd\@** yönetici kimlik bilgilerini kullanarak Dovecot IMAP sunucusundan geçirilmesinitesiniz. CSV dosyanız şöyle görünebilir:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams*mailadmin,P@ssw0rd
annb@contoso.edu,ann.beebe*mailadmin,P@ssw0rd
paulc@contoso.edu,paul.cannon*mailadmin,P@ssw0rd
```

 **Mirapoint:**

E-postayı Mirapoint Message Server'dan kullanıyorsanız, yönetici kimlik **bilgileri için #user\@ domain#Admin_UserName#** biçimini kullanın. **Mailadmin** ve **Pssw0rd\@** yönetici kimlik bilgilerini kullanarak e-postayı Mirapoint'den geçirmek için, CSV dosyanız aşağıdaki gibi olabilir:

```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,#terry.adams@contoso-students.edu#mailadmin#,P@ssw0rd
annb@contoso.edu,#ann.beebe@contoso-students.edu#mailadmin#,P@ssw0rd
paulc@contoso.edu,#paul.cannon@contoso-students.edu#mailadmin#,P@ssw0rd
```

 **Courier IMAP:**

Courier IMAP gibi bazı kaynak e-posta sistemleri, posta kutularını başka bir adrese geçirmek için posta kutusu yöneticisi kimlik bilgilerini Microsoft 365. Bunun yerine, kaynak e-posta sistemini sanal paylaşılan klasörleri kullanmak üzere kurabilirsiniz. Sanal paylaşılan klasörleri kullanarak, kaynak e-posta sisteminde kullanıcı posta kutularına erişmek için posta kutusu yöneticisi kimlik bilgilerini kullanabilirsiniz. Courier IMAP için sanal paylaşılan klasörleri yapılandırma hakkında daha fazla bilgi için bkz. [Paylaşılan Klasörler](https://go.microsoft.com/fwlink/p/?LinkId=398870).

Kaynak e-posta sisteminizde sanal paylaşılan klasörleri ayarladıktan sonra posta kutularını geçirmek için, geçiş dosyasına isteğe bağlı **UserRoot** özniteliğini eklemeniz gerekir. Bu öznitelik, kaynak e-posta sisteminde her kullanıcının posta kutusunun sanal paylaşılan klasör yapısındaki konumunu belirtir. Örneğin, Terry'nin posta kutusunun yolu /users/terry.adams'tır.

Aşağıda, **UserRoot** özniteliğini içeren bir CSV dosyası örneği verilmiştir:

```powershell
EmailAddress,UserName,Password,UserRoot
terrya@contoso.edu,mailadmin,P@ssw0rd,/users/terry.adams
annb@contoso.edu,mailadmin,P@ssw0rd,/users/ann.beebe
paulc@contoso.edu,mailadmin,P@ssw0rd,/users/paul.cannon
```

### <a name="step-3-create-an-imap-migration-endpoint"></a>3. Adım: IMAP geçiş uç noktası oluşturma

E-postayı geçirmeyi Microsoft 365, e-postanın kaynak e-posta sistemine bağlanması ve bu sistemle iletişim kurması gerekir. Bunu yapmak için, Microsoft 365 uç noktasını kullanır. Geçiş uç noktası, eşzamanlı olarak geçirilen posta kutularının sayısını ve artımlı eşitleme sırasında eşzamanlı olarak eşitlenecek posta kutularının sayısını da tanımlar. Bu, her 24 saatte bir gerçekleşir. IMAP geçişinin geçiş uç noktasını oluşturmak için, önce [IMAP'e Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

Geçiş komutlarının tam listesi için bkz. [Taşıma ve geçiş cmdlet'leri](/powershell/exchange/).

PowerShell'de "IMAPEndpoint" adlı IMAP geçiş Exchange Online oluşturmak için aşağıdaki komutu çalıştırın:

```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 993 -Security Ssl

```

Ayrıca, eş zamanlı geçişleri, eş zamanlı artımlı geçişleri ve kullanmak üzere bağlantı noktasını belirtmek için de parametreler abilirsiniz. Aşağıdaki PowerShell Exchange Online, 50 eşzamanlı geçişi ve en çok 25 eşzamanlı eş zamanlı eşitlemeyi destekleyen "IMAPEndpoint" adlı bir IMAP geçiş uç noktası oluşturur. Ayrıca, uç noktayı TLS şifrelemesi için bağlantı noktası 143'ü kullanmak üzere yapılandırıyor.

```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 143 -Security Tls -MaxConcurrentMigrations
50 -MaxConcurrentIncrementalSyncs 25
```

**New-MigrationEndpoint cmdlet'i** hakkında daha fazla bilgi için [bkz.New-MigrationEndpoint](/powershell/module/exchange/new-migrationendpoint).

#### <a name="verify-it-worked"></a>Çalıştığını doğrulayın

"IMAPEndpoint" Exchange Online görüntülemek için PowerShell'de aşağıdaki komutu çalıştırın:

```powershell
Get-MigrationEndpoint IMAPEndpoint | Format-List EndpointType,RemoteServer,Port,Security,Max*
```

### <a name="step-4-create-and-start-an-imap-migration-batch"></a>4. Adım: IMAP geçiş toplu işlemini oluşturma ve başlatma

IMAP geçişi için [geçiş toplu işlemini oluşturmak üzere New-MigrationBatch](/powershell/module/exchange/new-migrationbatch) cmdlet'ini kullanabilirsiniz. Otomatik Başlat parametresini de dahilerek geçiş toplu işlemini oluşturabilir ve _otomatik olarak başlatabilirsiniz_ . Alternatif olarak, geçiş toplu işlemini oluşturabilir ve daha [sonraStart-MigrationBatch cmdlet'ini](/powershell/module/exchange/start-migrationbatch) kullanarak başlatebilirsiniz.

Aşağıdaki PowerShell Exchange Online " IMAPBatch1" adlı geçiş toplu işlemini "IMAPEndpoint" adlı IMAP uç noktasını kullanarak otomatik olarak başlatacaktır:

```powershell
New-MigrationBatch -Name IMAPBatch1 -SourceEndpoint IMAPEndpoint -CSVData ([System.IO.File]::ReadAllBytes("C:\Users\Administrator\Desktop\IMAPmigration_1.csv")) -AutoStart
```

#### <a name="verify-it-worked"></a>Çalıştığını doğrulayın

"IMAPBatch1" hakkında bilgi görüntülemek için [Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch) cmdlet'ini çalıştırın:

```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List
```

Ayrıca, aşağıdaki komutu çalıştırarak toplu işleminin başlat doğrulayın:

```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a>5. Adım: E-postanızı başka bir Microsoft 365

E-posta sistemleri, e-postaların teslim edileceği yeri belirlemek için MX kaydı olarak adlandırılan bir DNS kaydını kullanır. E-posta geçiş işlemi sırasında, MX kaydınız kaynak e-posta sisteminize işaret ediyor olur. Artık MX kaydınıza işaret Microsoft 365 işlemi tamamlandığından, MX kaydınızı başka bir adrese Microsoft 365. Bu, e-postanın posta kutunuza teslim Microsoft 365 yardımcı olur. MX kaydını taşımanız, hazır olduğunda eski e-posta sisteminizi de kapatabilirsiniz.

Birçok DNS sağlayıcısı için, MX kaydınızı değiştirmeye yönelik belirli yönergeler sağlanmıştır. DNS sağlayıcınız bunların arasında değilse veya genel yönergeler hakkında fikir edinmek istiyorsanız, [genel MX kaydı yönergeleri](https://go.microsoft.com/fwlink/?LinkId=397449) de sağlanmıştır.

Müşterilerinizin ve iş ortaklarınızın e-posta sistemlerinin değişen MX kaydını fark etmesi 72 saat kadar sürebilir. Sonraki görev olan 6. Adım: IMAP geçiş toplu işlemini silme göreviyle devam etmek için en az 72 saat bekleyin.

### <a name="step-6-delete-imap-migration-batch"></a>6. Adım: IMAP geçiş toplu işlemini silme

MX kaydını değiştirdikten ve tüm e-postanın bu posta kutularına yönlendirildikten Microsoft 365, kullanıcılara postalarının gönder gerekmeyeceklerini Microsoft 365. Bundan sonra, IMAP geçiş toplu işlemini silebilirsiniz. Geçiş toplu işlemini silmeden önce aşağıdakileri doğrulayın.

- Tüm kullanıcılar posta kutuları Microsoft 365 kullanıyor. Toplu işlem silindikten sonra, şirket içi posta kutularına Exchange Server posta ilgili posta kutularına Microsoft 365 kopyalanmaz.

- Microsoft 365 posta kutuları, posta doğrudan onlara gönderilmeye başladıktan sonra en az bir kez eşitlenmiş olabilir. Bunu yapmak için, geçiş toplu işleminin Son Eşitleme Zamanı kutusunda yer alan değerin, postanın doğrudan posta posta kutularına yönlendir yapmaya başladığı zamanla daha yakın Microsoft 365 olun.

"IMAPBatch1" geçiş toplu işlemini PowerShell Exchange Online den silmek için aşağıdaki komutu çalıştırın:

```powershell
Remove-MigrationBatch -Identity IMAPBatch1
```

**Remove-MigrationBatch cmdlet'i** hakkında daha fazla bilgi için [bkz.Remove-MigrationBatch](/powershell/module/exchange/remove-migrationbatch).

#### <a name="verify-it-worked"></a>Çalıştığını doğrulayın

"IMAPBatch1 Exchange Online bilgi görüntülemek için PowerShell'de aşağıdaki komutu çalıştırın:

```powershell
Get-MigrationBatch IMAPBatch1"
```

Komut, geçiş toplu işlemini Kaldırma durumuyla döndürür veya geçiş toplu işleminin bulunamadısını ve toplu İşlemin silindikten sonra bulunamadısını belirten bir hata döndürür.

**Get-MigrationBatch cmdlet'i** hakkında daha fazla bilgi için [bkz.Get-MigrationBatch](/powershell/module/exchange/get-migrationbatch).

## <a name="see-also"></a>Ayrıca bkz.

[IMAP Geçiş Sorun Gidericisi](/exchange/troubleshoot/move-or-migrate-mailboxes/troubleshoot-issues-with-imap-mailbox-migration)