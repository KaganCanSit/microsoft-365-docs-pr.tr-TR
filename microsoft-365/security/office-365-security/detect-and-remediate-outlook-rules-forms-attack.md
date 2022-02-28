---
title: Geçerli kuralları ve özel form ekleme Outlook saldırılarını algıla ve düzeltmek.
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyp
manager: dansimp
ms.date: 04/23/2018
audience: ITPro
ms.topic: article
ms.collection:
- o365_security_incident_response
- M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MET150
description: Yeni kural ve özel form ekleme saldırılarını Outlook ve düzeltmeyi Office 365
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6c715552fedeefeb87206d889aa448609e8d7f60
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983497"
---
# <a name="detect-and-remediate-outlook-rules-and-custom-forms-injections-attacks"></a>Kuralları ve Özel Form Eklemeleri Outlook Algılama ve Düzeltme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


**Özet** Yeni kural ve özel Forms ekleme saldırılarını Outlook ve düzeltmeyi Office 365.

## <a name="what-is-the-outlook-rules-and-custom-forms-injection-attack"></a>En son Outlook ve Özel Formlar ekleme saldırısı nedir?

Bir saldırgan organizasyona erişim elde ettikten sonra, kalmak veya bulunduktan sonra geri dönmek için bir dipnot yapmaya dener. Bu etkinlik, *kalıcılık mekanizması kurma olarak adlandırılan bir etkinliktir*. Bir saldırganın kalıcılık mekanizması Outlook iki şekilde kullanabilir:

- Kuralları kullanarak Outlook.
- Şekillerin içine özel formlar Outlook.

Etki Outlook yeniden yüklemek veya etkilenen kişiye yeni bilgisayar vermek bile size yardımcı olmaz. Yeni dosya yüklemesi Outlook posta kutusuna bağlandığında, tüm kurallar ve formlar buluttan eşitlenir. Kurallar veya formlar normalde uzak kodu çalıştırmak ve yerel makinede kötü amaçlı yazılım yüklemek için tasarlanmıştır. Kötü amaçlı yazılım kimlik bilgilerini çalar veya başka bir zararlı etkinlik gerçekleştirir.

Ancak, istemcilerinizi en son Outlook yaması olarak bırakırsanız, mevcut Outlook istemci varsayılanları her iki mekanizmayı da engellesin diye tehditlere karşı açık değildirsiniz.

Saldırılar genellikle şu desenleri takip eder:

**Kurallardan Yararlanma**:

1. Saldırgan bir kullanıcının kimlik bilgilerini çalar.

2. Saldırgan, o kullanıcının posta kutusunda (Exchange şirket içi Exchange Online posta kutusunda oturum Exchange.

3. Saldırgan posta kutusunda bir iletme Gelen Kutusu kuralı oluşturur. Posta kutusu saldırgandan kuralın koşullarına uygun belirli bir ileti aldığında iletme kuralı tetiklenir. Kural koşulları ve ileti biçimi birbirinin için ayrı ayrı yapılır.

4. Saldırgan tetik e-postayı güvenliği tehlikeye atılmış posta kutusuna gönderir ve bu durumdan bağımsız kullanıcı normalde olduğu gibi kullanılır.

5. Posta kutusu kuralın koşullarına uygun bir ileti aldığında, kural eylemi uygulanır. Normalde, kural eylemi bir uygulamayı uzak (WebDAV) sunucusunda başlatmaktır.

6. Normalde, uygulama kullanıcının makinesine kötü amaçlı yazılım yükleyebilir (örneğin, [PowerShell İmparatorluğu](https://www.powershellempire.com/)).

7. Kötü amaçlı yazılım, saldırganin yerel makineden kullanıcı adını ve parolasını veya diğer kimlik bilgilerini çalmasına (veya yeniden çalmasına) ve diğer kötü amaçlı etkinlikleri gerçekleştirmesına olanak sağlar.

**Forms Exploit**:

1. Saldırgan bir kullanıcının kimlik bilgilerini çalar.

2. Saldırgan, o kullanıcının posta kutusunda (Exchange şirket içi Exchange Online posta kutusunda oturum Exchange.

3. Saldırgan kullanıcının posta kutusuna özel bir posta formu şablonu eklemektedir. Posta kutusu saldırgandan, posta kutusunun özel formu yüklemesi için gereken belirli bir ileti aldığında özel form tetiklenir. Özel form ve ileti biçimi birbirinin için uyarlanmış biçimdedir.

4. Saldırgan tetik e-postayı güvenliği tehlikeye atılmış posta kutusuna gönderir ve bu durumdan bağımsız kullanıcı normalde olduğu gibi kullanılır.

5. Posta kutusu iletiyi aldığında, posta kutusu gerekli formu yükler. Form, uzak (WebDAV) sunucusunda bir uygulama başlatıyor.

6. Normalde, uygulama kullanıcının makinesine kötü amaçlı yazılım yükleyebilir (örneğin, [PowerShell İmparatorluğu](https://www.powershellempire.com/)).

7. Kötü amaçlı yazılım, saldırganin yerel makineden kullanıcı adını ve parolasını veya diğer kimlik bilgilerini çalmasına (veya yeniden çalmasına) ve diğer kötü amaçlı etkinlikleri gerçekleştirmesına olanak sağlar.

## <a name="what-a-rules-and-custom-forms-injection-attack-might-look-like-office-365"></a>Kurallar ve Özel Form Ekleme saldırısı nasıl Office 365?

Bu kalıcılık mekanizmaları büyük bir soruna neden olmaz ve bazı durumlarda onlar için görünmez bile olabilir. Bu makalede, aşağıda listelenen yedi işaretten (Güvenlik Göstergeleri) nasıl bakabilirsiniz? Bu düzeltmelerden herhangi birini bulursanız, düzeltme adımları atılması gerekir.

- **Kuralların tehlikeye at olduğu göstergeler**:
  - Kural Eylemi, bir uygulama başlatmaktır.
  - Kural EXE, ZIP veya URL'ye başvurur.
  - Yerel makinede, PID'den gelen yeni Outlook bakın.

- **Özel formların güvenliği tehlikeye atacak göstergeler**:
  - Kendi ileti sınıfı olarak kaydedilmiş özel formlar vardır.
  - İleti sınıfı yürütülebilir kod içerir.
  - Kötü amaçlı formlar genellikle Kişisel Formlar Kitaplığı veya Gelen Kutusu klasörlarında depolanır.
  - Form IPM olarak adlandırılmıştır. Not. [özel ad].

## <a name="steps-for-finding-signs-of-this-attack-and-confirming-it"></a>Bu saldırının işaretlerini bulma ve onaylama adımları

Saldırıyı onaylamak için aşağıdaki yöntemlerden birini kullanabilirsiniz:

- Outlook istemcisini kullanarak, her posta kutusu için kuralları ve formları Outlook inceleyebilirsiniz. Bu yöntem kapsamlıdır, ancak bir defada yalnızca bir posta kutusunu kontrol edin. Denetlemeniz gereken çok sayıda kullanıcınız varsa bu yöntem çok zaman alabilir ve bu da kullanmakta olduğunu bilgisayara bulaşacak olabilir.

- Get-AllTenantRulesAndForms.ps1[ tüm posta ](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) iletme kurallarını ve özel formlarını kira alanınıza otomatik olarak dökümü içinGet-AllTenantRulesAndForms.ps1PowerShell betiği kullanın. Bu, en düşük yük miktarına sahip en hızlı ve en güvenli yöntemdir.

### <a name="confirm-the-rules-attack-using-the-outlook-client"></a>Outlook istemcisini Kullanarak Kural Saldırılarını Onaylayın

1. Kullanıcı olarak Outlook istemcisini açın. Kullanıcı posta kutusuyla ilgili kuralları incelemeniz için sizin yardıma ihtiyacı olabilir.

2. Aynı [dosyada kural arabirimini açma yordamları](https://support.microsoft.com/office/c24f5dea-9465-4df4-ad17-a50704d66c59) için kurallar makalesine kullanarak e-posta iletilerini yönetme Outlook.

3. Kullanıcının oluşturmadiği kuralları veya şüpheli adlarla ilgili beklenmedik kuralları veya kuralları bakın.

4. Başlangıç ve uygulama kural eylemleri için kural açıklamasına bakın veya .EXE, .ZIP veya BIR URL başlatmaya bakın.

5. Kullanıcı adı ve işlem kimliğini kullanmaya başlamak için Outlook bakın. süreç [kimliğini bulma'ya bakın](/windows-hardware/drivers/debugger/finding-the-process-id).

### <a name="steps-to-confirm-the-forms-attack-using-the-outlook-client"></a>Outlook istemcisini kullanarak Forms saldırılarını onaylama adımları

1. Kullanıcı olarak Outlook istemcisini açın.

2. Kullanıcının kullanıcı [sürümünün Geliştirici sekmesini](https://support.microsoft.com/office/e1192344-5e56-4d45-931b-e5fd9bea2d45) gösterme altında yer alan adımları Outlook.

3. Yeni Görünüm'de artık görünür olan geliştirici Outlook ve form **tasarla'ya tıklayın**.

4. Bak **listesinden** Gelen **Kutusu'na** tıklayın. Özel formlara bakın. Özel formlar nadiren de olsa, özel formlar varsa daha derine bakmanız yeterlidir.

5. Özel formları (özellikle de gizli olarak işaretli formları) araştıryın.

6. Herhangi bir özel formu açın ve **Form** **grubunda Kodu** Görüntüle'ye tıklar ve form yüklendiğinde nelerin çalıştır yaptığını bakın.

### <a name="steps-to-confirm-the-rules-and-forms-attack-using-powershell"></a>PowerShell kullanarak Kurallar ve Formlar saldırılarını onaylama adımları

Kurallara veya özel formlara yönelik saldırıyı doğrulamanın en basit yolu, [Get-AllTenantRulesAndForms.ps1PowerShell ](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) betiği çalıştırmaktır. Bu betik kiracınız içinde yer alan tüm posta kutularına bağlanır ve tüm kuralları ve formları iki ayrı .csv oluşturur.

#### <a name="pre-requisites"></a>Önkoşullar

Betiği çalıştırmak için genel yönetici haklarınız olması gerekir, çünkü betik kira dosyasındaki tüm posta kutularına kuralları ve formları okumak için bağlanır.

1. Betiği çalıştıracak makinede yerel yönetici haklarıyla oturum açın.

2. Bu betiği Get-AllTenantRulesAndForms.ps1 betiği GitHub çalıştıracak bir klasöre indirin veya kopyalayın. Betik, bu klasöre iki tarih damgasılı dosya oluşturur; MailboxFormsExport-yyyy-mm-dd.csv dosya MailboxRulesExport-yyyy-mm-dd.csv.

3. Bir PowerShell örneğini yönetici olarak açın ve betiği kayıtlı klasörü açın.

4. Bu PowerShell komut satırı `.\Get-AllTenantRulesAndForms.ps1`.\Get-AllTenantRulesAndForms.ps1

#### <a name="interpreting-the-output"></a>Çıkışı yorumlama

- ***MailboxRulesExport-yyyy-mm-dd*.csv**: Uygulamaları veya yürütülebilir dosyaları içeren eylem koşulları için kuralları (satır başına bir) incele:

  - **ActionType (A sütunu)**: "Özel" değerini ID_ACTION_CUSTOM, kural büyük olasılıkla kötü amaçlıdır.

  - **IsPotentiallyMalicious (D sütunu)**: Bu değer "DOĞRU" ise, kural büyük olasılıkla kötü amaçlıdır.

  - **ActionCommand (G sütunu)**: Bu sütunda .exe veya .zip uzantılara sahip bir uygulama ya da dosya ya da URL'ye başvuran bilinmeyen bir giriş listeıyorsa, kural büyük olasılıkla kötü amaçlıdır.

- ***MailboxFormsExport-yyyy-aa-.csv***: Genelde özel formların kullanımı enderdir. Bu çalışma kitabında herhangi bir şey bulursanız, o kullanıcının posta kutusunu açar ve formun kendisini incelersiniz. If your organization did not put it in intentionally, it is likely malicious.

## <a name="how-to-stop-and-remediate-the-outlook-rules-and-forms-attack"></a>Kurallar ve Formlar saldırılarını durdurma Outlook düzeltme

Bu saldırılardan herhangi biri için kanıt bulursanız, düzeltme basit bir işlemdir, yalnızca posta kutusundan kuralı veya formu silin. Bunu Outlook istemcide veya uzak PowerShell kullanarak kuralları kaldırabilirsiniz.

### <a name="using-outlook"></a>Outlook'i kullanma

1. Kullanıcının diğer kullanıcılarla birlikte kullandığı tüm cihazları Outlook. Tüm olası kötü amaçlı yazılımların temizlenmesi gerekir. Tüm cihazlar temizleninceye kadar kullanıcının oturum açmasına ve e-posta kullanmasına izin verme.

2. Her cihaz için [kural silme'de](https://support.microsoft.com/office/2f0e7139-f696-4422-8498-44846db9067f) adımları izleyin.

3. Başka bir kötü amaçlı yazılıma sahip olup olmadığınız konusunda emin değilseniz, tüm yazılımı cihaza biçimlendirin ve yeniden yükleyin. Mobil cihazlarda, cihazı fabrika görüntüsüne sıfırlamak için üreticilerin adımlarını izleyin.

4. Office 365'in en güncel sürümlerini Outlook. Outlook'in geçerli sürümünün her iki tür saldırıyı da varsayılan olarak engeller.

5. Posta kutusunun çevrimdışı kopyalarının hepsi kaldırıldıktan sonra, kullanıcının parolasını sıfırlayın (yüksek kaliteli bir parola kullanın) ve MFA daha önce etkinleştirilmemişse kullanıcılar [](../../admin/security-and-compliance/set-up-multi-factor-authentication.md) için çok faktörlü kimlik doğrulamasını ayarlama'daki adımları izleyin. Bu, kullanıcının kimlik bilgilerinin başka bir araçla (kimlik avı veya parola yeniden kullanımı gibi) açık kalmalarını sağlar.

### <a name="using-powershell"></a>PowerShell'i kullanma

Tehlikeli kuralları kaldırmak veya devre dışı bırakmak için kullanabileceğiniz iki uzak PowerShell cmdlet'i vardır. Adımları takip edin.

#### <a name="steps-for-mailboxes-that-are-on-an-exchange-server"></a>Exchange sunucusundaki posta kutuları için adımlar

1. Bağlan PowerShell Exchange sunucuya bağlanın. Uzak [PowerShell kullanarak Bağlan'Exchange aşağıdaki adımları izleyin](/powershell/exchange/connect-to-exchange-servers-using-remote-powershell).

2. Bir posta kutusundan tek bir kuralı, birden çok kuralı veya tüm kuralları tamamen kaldırmak için [Gelen KutusuRule](/powershell/module/exchange/Remove-InboxRule) cmdlet'ini kullanın.

3. Kuralı ve içeriğini daha fazla araştırma yapmak için korumak için Gelen Kutusu Kuralını [Devre Dışı Bırak cmdlet'ini](/powershell/module/exchange/disable-inboxrule) kullanın.

#### <a name="steps-for-mailboxes-in-exchange-online"></a>Posta kutuları için Exchange Online

1. [PowerShell kullanarak Bağlan Exchange Online adımları izleyin](/powershell/exchange/connect-to-exchange-online-powershell).

2. Bir posta kutusundan tek bir kuralı, birden çok kuralı veya tüm kuralları tamamen kaldırmak için Gelen Kutusu Kuralını [Kaldır](/powershell/module/exchange/Remove-InboxRule) cmdlet'ini kullanın.

3. Kuralı ve içeriğini daha fazla araştırma yapmak için korumak için Gelen Kutusu Kuralını [Devre Dışı Bırak cmdlet'ini](/powershell/module/exchange/disable-inboxrule) kullanın.

## <a name="how-to-minimize-future-attacks"></a>Gelecekteki saldırılar nasıl en aza indirger

### <a name="first-protect-your-accounts"></a>İlk olarak, hesaplarınızı koruyun

Kurallar ve Formlar istismarları ancak kullanıcı hesaplarından birini çalınırsa veya ihlal edildikten sonra bir saldırgan tarafından kullanılır. Bu nedenle, bu istismarların organizasyona karşı kullanımını önlemenin ilk adımı, kullanıcı hesaplarınızı saldırgan bir şekilde korumaktır. Hesapların ihlal etmenin en yaygın yollarından bazıları kimlik avı veya parola parola [saldırılarındandır](https://www.microsoft.com/security/blog/2020/04/23/protecting-organization-password-spray-attacks/).

Kullanıcı hesaplarınızı ve özellikle de yönetici hesaplarınızı korumanın en iyi yolu, kullanıcılar için [çok faktörlü kimlik doğrulamasını ayarlamaktır](../../admin/security-and-compliance/set-up-multi-factor-authentication.md). Ayrıca şunları da gerekir:

- Kullanıcı hesaplarınıza nasıl erişil olduğunu [ve nasıl kullanıldıklarını takip etmek](/azure/active-directory/active-directory-view-access-usage-reports). İlk ihlali önlemeyin, ancak daha önce tespit edersiniz ve ihlalin süresini ve etkisini kısaltmış oluruz. Hesaplarınız ve olağan [Office 365 Bulut Uygulamaları Güvenliği izlemek](/cloud-app-security/what-is-cloud-app-security) için bu yardım ilkelerini kullanabilirsiniz:

  - **Birden çok başarısız** oturum açma girişimi: Bu ilke ortamınızı profiller ve kullanıcılar tek oturumda birden fazla başarısız oturum açma işlemi gerçekleştirildiğinde, öğrenilen temele göre uyarılar tetikler; bu da bir ihlal girişimlerine neden olabilir.

  - **Imkansız seyahat**: Bu ilke ortamınızı profiller ve iki konum arasındaki beklenen seyahat süresinden daha kısa bir süre içinde aynı kullanıcıdan farklı konumlarda etkinlikler algılandığında uyarıları tetikler. Bu, farklı bir kullanıcının aynı kimlik bilgilerini kullanıyor olduğunu gösteriyor olabilir. Bu anormal davranışı algılamak, yeni bir kullanıcının etkinlik desenini öğrenmesi için yedi günlük bir başlangıç öğrenme dönemi gerekir.

  - **Olağan dışı kimliğe** bürünülen etkinlik (kullanıcıya göre): Bu ilke ortamınızı profiller ve kullanıcılar öğrenilen taban çizgisine göre tek oturumda birden çok kimliğe bürünülen etkinlik gerçekleştirildiğinde uyarılar tetikler; bu da ihlale neden olabilir.

- Hesap güvenliği yapılandırmalarını [ve Office 365 yönetmek için](https://securescore.office.com/) Güvenli Puan'a sahip olmak gibi bir araç kullanın.

### <a name="second-keep-your-outlook-clients-current"></a>İkinci: Outlook istemcilerinizi güncel tutma

Outlook 2013 ve 2016'nın tümüyle güncelleştirilmiş ve yamalı sürümleri, "Uygulamayı Başlat" kuralı/formu eylemini varsayılan olarak devre dışı bırak. Bu şekilde, bir saldırgan hesap ihlal edese bile kural ve form eylemleri engellenir. En son güncelleştirmeleri ve güvenlik yamalarını yüklemek için Bu Güncelleştirmeleri Yükleme Office [edinebilirsiniz](https://support.microsoft.com/office/2ab296f3-7f03-43a2-8e50-46de917611c5).

Outlook 2013 ve 2016 istemcileriniz için düzeltme eki sürümleri:

- **Outlook 2016**: 16.0.4534.1001 veya üzerinde.

- **Outlook 2013**: 15.0.4937.1000 veya daha büyük.

Tek tek güvenlik yamaları hakkında daha fazla bilgi için bkz:

- [Outlook 2016 Düzeltme Eki](https://support.microsoft.com/help/3191883)

- [Outlook 2013 Güvenlik Düzeltme Eki](https://support.microsoft.com/help/3191938)

### <a name="third-monitor-your-outlook-clients"></a>Üçüncü: Outlook istemcilerinizi izleme

Düzeltme ekleri ve güncelleştirmeler yüklü olsa bile, bir saldırganın yerel makine yapılandırmasında "Başlangıç Uygulaması" davranışını yeniden etkinleştirmesi mümkündür. İstemcilerinize [yerel makine ilkelerini izlemek](/microsoft-desktop-optimization-pack/agpm/) ve uygulamak için Gelişmiş Grup İlkesi Yönetimi'ne kullanabilirsiniz.

Uygulamanın 64 bit sürümlerini kullanarak sistem kayıt defterini görüntüleme makalesinde yer alan bilgileri kullanarak, "Başlangıç Uygulaması" değerinin kayıt defterinde geçersiz kılınarak yeniden [etkinleştiril olup Windows](https://support.microsoft.com/help/305097). Şu alt anahtarları kontrol edin:

- **Outlook 2016**:`HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Outlook\Security\`

- **Outlook 2013**:`HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Outlook\Security\`

EnableUnsafeClientMailRules anahtarına bakın. Varsa ve 1 olarak ayarlanırsa, Outlook düzeltme eki geçersiz kılınır ve bilgisayar Form/Kurallar saldırılarına açık kalır. Değer 0 ise, "Uygulamayı Başlat" eylemi devre dışı bırakılır. Bu güvenlik defteri anahtarının güncelleştirilmiş ve yama Outlook yüklüyse ve bu kayıt defteri anahtarı yoksa, sistem bu saldırılara açık değildir.

Şirket içi yüklemeleri olan Exchange, kullanılabilir yamaları olmayan Outlook sürümlerini engellemeyi göz önünde bulundurmalı. Bu işlemle ilgili ayrıntıları İstemci engellemeyi [yapılandırma makalesinde Outlook bulunabilir](/exchange/configure-outlook-client-blocking-exchange-2013-help).

## <a name="secure-microsoft-365-like-a-cybersecurity-pro"></a>Siber Microsoft 365 gibi güvenliği sağlama

Microsoft 365 aboneliğiniz, verilerinizi ve kullanıcılarınızı korumak için kullanabileceğiniz güçlü bir güvenlik özellikleri kümesiyle gelir. Güvenlik [Microsoft 365 kullanın - İlk 30 gün, 90](security-roadmap.md) gün ve bundan sonra Microsoft'un kiracı kiracının güvenliğini sağlamak için önerilen en iyi yöntemleri uygulamak için Microsoft 365 vardır.

- İlk 30 gün içinde yerine gelen görevler. Bunlar hemen etkili olur ve kullanıcılarınız için düşük etki sağlar.

- 90 gün içinde yapılacak görevler. Bunlar planlamak ve uygulamak için biraz daha zaman alır ama güvenlik performansını büyük ölçüde geliştirin.

- 90 gün dışında. Bu iyileştirmeler ilk 90 gün çalışmanıza dahil.

## <a name="see-also"></a>Ayrıca bkz:

- [Kurallar Outlook SilentBreak](https://silentbreaksecurity.com/malicious-outlook-rules/) Güvenlik Gönderisi'nin Kötü Amaçlı Kullanıcı Kuralları, Kullanıcı Kuralları'nın nasıl ayrıntılı Outlook sağlar.

- MAILrule Pwnage hakkında Sensepost blog'gönderisi üzerinden [MAPI ve Mailrule Pwnage](https://sensepost.com/blog/2016/mapi-over-http-and-mailrule-pwnage/), Cetvel adlı aracı tartışarak posta kutularını Outlook tartışır.

- [Outlook Posta blog'sinde](https://sensepost.com/blog/2017/outlook-forms-and-shells/) Forms Threat Vector hakkında form ve kabukları kontrol edin.

- [Cetvel Kod Tabanı](https://github.com/sensepost/ruler)

- [CetvelIn Güvenliği Ile Ilgili Göstergeler](https://github.com/sensepost/notruler/blob/master/iocs.md)