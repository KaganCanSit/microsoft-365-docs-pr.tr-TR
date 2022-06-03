---
title: Outlook kurallarını ve özel form ekleme saldırılarını algılayın ve düzeltin.
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
description: Office 365'de Outlook kurallarını ve özel form ekleme saldırılarını tanımayı ve düzeltmeyi öğrenin
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 268e50059ad1b128e583a5be383788b545fa6190
ms.sourcegitcommit: 35f167725bec5fd4fe131781a53d96b060cf232d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65874106"
---
# <a name="detect-and-remediate-outlook-rules-and-custom-forms-injections-attacks"></a>Outlook Kurallarını ve Özel Form Ekleme Saldırılarını Algılama ve Düzeltme

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Özet** Office 365'da Outlook kurallarını ve özel Forms ekleme saldırılarını tanıyıp düzeltmeyi öğrenin.

## <a name="what-is-the-outlook-rules-and-custom-forms-injection-attack"></a>Outlook Kuralları ve Özel Form ekleme saldırısı nedir?

Bir saldırgan kuruluşunuza erişim elde ettikten sonra, bulunduğu yerde kalmak veya bulunduktan sonra geri dönmek için bir koruma alanı oluşturmaya çalışır. Bu etkinliğe *kalıcılık mekanizması oluşturma* adı verilir. Bir saldırganın kalıcılık mekanizması oluşturmak için Outlook kullanabileceği iki yol vardır:

- Outlook kuralları kullanarak.
- Outlook özel formlar ekleyerek.

Outlook yeniden yüklemek ve hatta etkilenen kişiye yeni bir bilgisayar vermek yardımcı olmaz. yeni Outlook yüklemesi posta kutusuna bağlandığında, tüm kurallar ve formlar buluttan eşitlenir. Kurallar veya formlar genellikle uzak kod çalıştırmak ve yerel makineye kötü amaçlı yazılım yüklemek için tasarlanmıştır. Kötü amaçlı yazılım kimlik bilgilerini çalar veya diğer yasadışı etkinlikleri gerçekleştirir.

İyi haber şudur: Outlook istemcilerinize en son sürüme düzeltme eki uygulamazsanız, geçerli Outlook istemci varsayılanları her iki mekanizmayı da engellediğinden tehditlere karşı savunmasız olmazsınız.

Saldırılar genellikle şu desenleri izler:

**Kurallardan Yararlanma**:

1. Saldırgan bir kullanıcının kimlik bilgilerini çalar.

2. Saldırgan, kullanıcının Exchange posta kutusunda (Exchange Online veya şirket içi Exchange) oturum açar.

3. Saldırgan, posta kutusunda bir iletme Gelen Kutusu kuralı oluşturur. posta kutusu saldırgandan kuralın koşullarıyla eşleşen belirli bir ileti aldığında iletme kuralı tetikler. Kural koşulları ve ileti biçimi, birbirlerine göre uyarlanmıştır.

4. Saldırgan, güvenliği aşılmış olan posta kutusuna tetikleyici e-postasını gönderir ve bu e-posta, hala istenmeyen kullanıcı tarafından normal olarak kullanılmaktadır.

5. Posta kutusu kural koşullarıyla eşleşen bir ileti aldığında, kuralın eylemi uygulanır. Kural eylemi genellikle bir uygulamayı uzak (WebDAV) sunucusunda başlatmaktır.

6. Genellikle uygulama kullanıcının makinesine kötü amaçlı yazılım yükler (örneğin, [PowerShell Empire](https://www.powershellempire.com/)).

7. Kötü amaçlı yazılım, saldırganın kullanıcının kullanıcı adını ve parolasını veya diğer kimlik bilgilerini yerel makineden çalmasına (veya tekrar çalmasına) ve diğer kötü amaçlı etkinlikleri gerçekleştirmesine olanak tanır.

**Formların Açıkları**:

1. Saldırgan bir kullanıcının kimlik bilgilerini çalar.

2. Saldırgan, kullanıcının Exchange posta kutusunda (Exchange Online veya şirket içi Exchange) oturum açar.

3. Saldırgan, kullanıcının posta kutusuna özel bir posta formu şablonu ekler. Özel form, posta kutusu saldırgandan özel formun yüklenmesini gerektiren belirli bir ileti aldığında tetikler. Özel form ve ileti biçimi, birbirlerine göre uyarlanmıştır.

4. Saldırgan, güvenliği aşılmış olan posta kutusuna tetikleyici e-postasını gönderir ve bu e-posta, hala istenmeyen kullanıcı tarafından normal olarak kullanılmaktadır.

5. Posta kutusu iletiyi aldığında, posta kutusu gerekli formu yükler. Form, uzak (WebDAV) sunucusunda bir uygulama başlatır.

6. Genellikle uygulama kullanıcının makinesine kötü amaçlı yazılım yükler (örneğin, [PowerShell Empire](https://www.powershellempire.com/)).

7. Kötü amaçlı yazılım, saldırganın kullanıcının kullanıcı adını ve parolasını veya diğer kimlik bilgilerini yerel makineden çalmasına (veya tekrar çalmasına) ve diğer kötü amaçlı etkinlikleri gerçekleştirmesine olanak tanır.

## <a name="what-a-rules-and-custom-forms-injection-attack-might-look-like-office-365"></a>Kurallar ve Özel Form Ekleme saldırısı Office 365 nasıl görünebilir?

Bu kalıcılık mekanizmalarının kullanıcılarınız tarafından fark edilme olasılığı düşüktür ve bazı durumlarda bunlar için görünmez bile olabilir. Bu makalede, aşağıda listelenen yedi işaretin (Uzlaşma Göstergeleri) nasıl aranacakları açıklanır. Bunlardan herhangi birini bulursanız, düzeltme adımlarını uygulamanız gerekir.

- **Kuralların tehlikeye atılmasına ilişkin göstergeler**:
  - Kural Eylemi, bir uygulamayı başlatmaktır.
  - Kural Exe, ZIP veya URL'ye başvurur.
  - Yerel makinede, Outlook PID'den kaynaklanan yeni işlem başlangıçlarını arayın.

- **Özel formların güvenliğinin aşılmasına ilişkin göstergeler**:
  - Kendi ileti sınıfı olarak kaydedilen özel formlar var.
  - İleti sınıfı yürütülebilir kod içerir.
  - Genellikle, kötü amaçlı formlar Kişisel Formlar Kitaplığı'nda veya Gelen Kutusu klasörlerinde depolanır.
  - Form IPM olarak adlandırılır. Not. [özel ad].

## <a name="steps-for-finding-signs-of-this-attack-and-confirming-it"></a>Bu saldırının işaretlerini bulma ve onaylama adımları

Saldırıyı onaylamak için aşağıdaki yöntemlerden birini kullanabilirsiniz:

- Outlook istemcisini kullanarak her posta kutusu için kuralları ve formları el ile inceleyin. Bu yöntem kapsamlıdır, ancak aynı anda yalnızca bir posta kutusunu deleyebilirsiniz. Denetlemeniz gereken çok sayıda kullanıcı varsa bu yöntem çok zaman alabilir ve kullandığınız bilgisayara da bulaşabilir.

- [ kiracınızdaki ](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) tüm kullanıcılar için posta iletme kurallarını ve özel formları otomatik olarak dökümünü almak içinGet-AllTenantRulesAndForms.ps1PowerShell betiğini kullanın. Bu, en az ek yüke sahip en hızlı ve en güvenli yöntemdir.

### <a name="confirm-the-rules-attack-using-the-outlook-client"></a>Outlook istemcisini kullanarak Kural Saldırısını Onaylama

1. kullanıcı Outlook istemcisini kullanıcı olarak açın. Kullanıcının posta kutularındaki kuralları inceleme konusunda yardımınıza ihtiyacı olabilir.

2. Outlook'da kural arabirimini açma yordamları için Kural [kullanarak e-posta iletilerini yönetme](https://support.microsoft.com/office/c24f5dea-9465-4df4-ad17-a50704d66c59) makalesine bakın.

3. Kullanıcının oluşturmadığı kuralları veya şüpheli adlara sahip beklenmeyen kuralları veya kuralları arayın.

4. Başlatan ve uygulamaya yönelik kural eylemleri için kural açıklamasına bakın veya bir .EXE, .ZIP dosyasına veya url başlatmaya bakın.

5. Outlook işlem kimliğini kullanmaya başlayan tüm yeni işlemleri arayın. [İşlem Kimliğini Bulma bölümüne](/windows-hardware/drivers/debugger/finding-the-process-id) bakın.

### <a name="steps-to-confirm-the-forms-attack-using-the-outlook-client"></a>Outlook istemcisini kullanarak Forms saldırısını onaylama adımları

1. kullanıcı Outlook istemcisini kullanıcı olarak açın.

2. Kullanıcının Outlook [sürümünün Geliştirici sekmesini gösterme](https://support.microsoft.com/office/e1192344-5e56-4d45-931b-e5fd9bea2d45) bölümünde yer alan adımları izleyin.

3. Outlook'da görünür durumdaki geliştirici sekmesini açın ve **form tasarla'ya** tıklayın.

4. Bak listesinden **Gelen** **Kutusu'nu** seçin. Herhangi bir özel form arayın. Özel formlar, özel formlarınız varsa daha derin bir görünüme değer olacak kadar nadirdir.

5. Özel formları, özellikle de gizli olarak işaretlenmiş formları araştırın.

6. Herhangi bir özel formu açın ve **Form** grubunda **Kodu Görüntüle'ye** tıklayarak form yüklendiğinde nelerin çalıştığını görün.

### <a name="steps-to-confirm-the-rules-and-forms-attack-using-powershell"></a>PowerShell kullanarak Kurallar ve Formlar saldırısını onaylama adımları

Kuralları veya özel form saldırılarını doğrulamanın en basit yolu [ ,Get-AllTenantRulesAndForms.ps1](https://github.com/OfficeDev/O365-InvestigationTooling/blob/master/Get-AllTenantRulesAndForms.ps1) PowerShell betiğini çalıştırmaktır. Bu betik, kiracınızdaki her posta kutusuna bağlanır ve tüm kuralları ve formları iki .csv dosyasına döker.

#### <a name="pre-requisites"></a>Önkoşullar

Betik, kuralları ve formları okumak için kiracıdaki her posta kutusuna bağlandığından, betiği çalıştırmak için genel yönetici haklarına sahip olmanız gerekir.

1. Betiği çalıştıracağınız makinede yerel yönetici haklarıyla oturum açın.

2. Get-AllTenantRulesAndForms.ps1 betiğini GitHub'dan çalıştıracağınız klasöre indirin veya kopyalayın. Betik, bu klasöre MailboxFormsExport-yyyy-mm-dd.csv ve MailboxRulesExport-yyyy-mm-dd.csv olmak üzere iki tarih damgalı dosya oluşturur.

3. Bir PowerShell örneğini yönetici olarak açın ve betiği kaydettiğiniz klasörü açın.

4. Bu PowerShell komut satırını aşağıdaki `.\Get-AllTenantRulesAndForms.ps1`gibi çalıştırın.\Get-AllTenantRulesAndForms.ps1

#### <a name="interpreting-the-output"></a>Çıkışı yorumlama

- ***MailboxRulesExport-yyyy-mm-dd*.csv**: Uygulamaları veya yürütülebilir dosyaları içeren eylem koşulları için kuralları (satır başına bir tane) inceleyin:

  - **ActionType (A sütunu):**"ID_ACTION_CUSTOM" değerini görüyorsanız, kural büyük olasılıkla kötü amaçlıdır.

  - **IsPotentiallyMalicious (D sütunu):** Bu değer "DOĞRU" ise, kural büyük olasılıkla kötü amaçlıdır.

  - **ActionCommand (G sütunu):** Bu sütunda bir uygulama veya .exe ya da .zip uzantıları olan herhangi bir dosya ya da URL'ye başvuran bilinmeyen bir giriş listeleniyorsa, kural büyük olasılıkla kötü amaçlıdır.

- ***MailboxFormsExport-yyyy-mm-dd*.csv**: Genel olarak, özel formların kullanımı nadirdir. Bu çalışma kitabında herhangi bir posta kutusu bulursanız, kullanıcının posta kutusunu açar ve formun kendisini incelersiniz. Kuruluşunuz bunu kasıtlı olarak koymadıysa, büyük olasılıkla kötü amaçlıdır.

## <a name="how-to-stop-and-remediate-the-outlook-rules-and-forms-attack"></a>Outlook Kuralları ve Formları saldırısını durdurma ve düzeltme

Bu saldırılardan herhangi biriyle ilgili herhangi bir kanıt bulursanız, düzeltme basittir, kuralı veya formu posta kutusundan silmeniz gerekir. Bunu Outlook istemcisiyle veya kuralları kaldırmak için uzak PowerShell kullanarak yapabilirsiniz.

### <a name="using-outlook"></a>Outlook kullanma

1. Kullanıcının Outlook ile kullandığı tüm cihazları tanımlayın. Bunların tümünün olası kötü amaçlı yazılımlardan temizlenmesi gerekir. Tüm cihazlar temizlenene kadar kullanıcının oturum açmasına ve e-posta kullanmasına izin verme.

2. Her cihaz için [kural silme'deki](https://support.microsoft.com/office/2f0e7139-f696-4422-8498-44846db9067f) adımları izleyin.

3. Diğer kötü amaçlı yazılımların varlığından emin değilseniz, tüm yazılımı cihaza biçimlendirebilir ve yeniden yükleyebilirsiniz. Mobil cihazlar için üretici adımlarını izleyerek cihazı fabrika görüntüsüne sıfırlayabilirsiniz.

4. Outlook en güncel sürümlerini yükleyin. Outlook geçerli sürümünün bu saldırının her iki türünü de varsayılan olarak engellediğini unutmayın.

5. Posta kutusunun tüm çevrimdışı kopyaları kaldırıldıktan sonra, kullanıcının parolasını sıfırlayın (yüksek kaliteli bir parola kullanın) ve MFA henüz etkinleştirilmemişse [kullanıcılar için çok faktörlü kimlik doğrulamasını ayarlama](../../admin/security-and-compliance/set-up-multi-factor-authentication.md) başlığı altında yer alan adımları izleyin. Bu, kullanıcının kimlik bilgilerinin başka yollarla (kimlik avı veya parola yeniden kullanımı gibi) gösterilmemesini sağlar.

### <a name="using-powershell"></a>PowerShell kullanma

Tehlikeli kuralları kaldırmak veya devre dışı bırakmak için kullanabileceğiniz iki uzak PowerShell cmdlet'i vardır. Adımları izlemen yeter.

#### <a name="steps-for-mailboxes-that-are-on-an-exchange-server"></a>Exchange sunucusundaki posta kutuları için adımlar

1. uzak PowerShell kullanarak Exchange sunucusuna Bağlan. [Uzak PowerShell kullanarak sunucuları Exchange için Bağlan'deki](/powershell/exchange/connect-to-exchange-servers-using-remote-powershell) adımları izleyin.

2. Bir posta kutusundan tek bir kuralı, birden çok kuralı veya tüm kuralları tamamen kaldırmak istiyorsanız [Remove-InboxRule cmdlet'ini](/powershell/module/exchange/Remove-InboxRule) kullanın.

3. Kuralı ve içeriğini daha fazla araştırma için korumak istiyorsanız [Disable-InboxRule cmdlet'ini](/powershell/module/exchange/disable-inboxrule) kullanın.

#### <a name="steps-for-mailboxes-in-exchange-online"></a>Exchange Online'da posta kutuları için adımlar

1. [PowerShell kullanarak Exchange Online için Bağlan'deki](/powershell/exchange/connect-to-exchange-online-powershell) adımları izleyin.

2. Bir posta kutusundan tek bir kuralı, birden çok kuralı veya tüm kuralları tamamen kaldırmak istiyorsanız [Gelen Kutusu Kuralını Kaldır cmdlet'ini](/powershell/module/exchange/Remove-InboxRule) kullanın.

3. Kuralı ve içeriğini daha fazla araştırma için korumak istiyorsanız [Disable-InboxRule cmdlet'ini](/powershell/module/exchange/disable-inboxrule) kullanın.

## <a name="how-to-minimize-future-attacks"></a>Gelecekteki saldırıları en aza indirme

### <a name="first-protect-your-accounts"></a>İlk olarak: Hesaplarınızı koruma

Kurallar ve Formlar açıklarından yararlanma işlemleri, bir saldırgan tarafından yalnızca kullanıcı hesaplarınızdan birini çaldıktan veya ihlal ettikten sonra kullanılır. Bu nedenle, bu açıkların kuruluşunuza karşı kullanılmasını önlemenin ilk adımı, kullanıcı hesaplarınızı agresif bir şekilde korumaktır. Hesapların ihlal edilmesi için en yaygın yollardan bazıları kimlik avı veya [parola spreyi saldırılarıdır](https://www.microsoft.com/security/blog/2020/04/23/protecting-organization-password-spray-attacks/).

Kullanıcı hesaplarınızı ve özellikle de yönetici hesaplarınızı korumanın en iyi yolu [, kullanıcılar için çok faktörlü kimlik doğrulamasını ayarlamaktır](../../admin/security-and-compliance/set-up-multi-factor-authentication.md). Ayrıca şunları da yapmalısınız:

- Kullanıcı hesaplarınıza nasıl [erişilip kullanıldığını](/azure/active-directory/active-directory-view-access-usage-reports) izleyin. İlk ihlali önleyemeyebilirsiniz, ancak daha erken algılayarak ihlalin süresini ve etkisini kısaltırsınız. Hesaplarınızı izlemek ve olağan dışı etkinliklerle ilgili uyarı vermek için bu [Office 365 Bulut Uygulamaları Güvenliği ilkelerini](/cloud-app-security/what-is-cloud-app-security) kullanabilirsiniz:

  - **Birden çok başarısız oturum açma girişimi**: Bu ilke ortamınızın profilini oluşturur ve kullanıcılar öğrenilen temele göre tek bir oturumda birden çok başarısız oturum açma etkinliği gerçekleştirdiğinde uyarı tetikler ve bu da ihlal girişimine işaret edebilir.

  - **İmkansız seyahat**: Bu ilke ortamınızın profilini oluşturur ve iki konum arasındaki beklenen seyahat süresinden daha kısa bir süre içinde farklı konumlarda aynı kullanıcıdan etkinlikler algılandığında uyarıları tetikler. Bu, farklı bir kullanıcının aynı kimlik bilgilerini kullandığını gösterebilir. Bu anormal davranışın algılanması, yeni bir kullanıcının etkinlik desenini öğrendiği yedi günlük ilk öğrenme süresini gerektirmektedir.

  - **Olağan dışı kimliğe bürünülen etkinlik (kullanıcı tarafından)**: Bu ilke ortamınızın profilini oluşturur ve kullanıcılar öğrenilen temele göre tek bir oturumda birden çok kimliğine bürünülen etkinlik gerçekleştirdiğinde uyarı tetikler ve bu da ihlal girişimine işaret edebilir.

- Hesap güvenlik yapılandırmalarını ve davranışlarını yönetmek için [Office 365 Güvenli Puan](/microsoft-365/security/defender/microsoft-secure-score) gibi bir araç kullanın.

### <a name="second-keep-your-outlook-clients-current"></a>İkinci: Outlook istemcilerinizi güncel tutun

Outlook 2013 ve 2016'nın tam olarak güncelleştirilmiş ve düzeltme eki eklenmiş sürümleri varsayılan olarak "Uygulamayı Başlat" kuralı/form eylemini devre dışı bırakır. Bu, bir saldırgan hesabı ihlal ederse bile kural ve form eylemlerinin engellenmesini sağlar. Güncelleştirmeleri yükleme Office adımlarını izleyerek en son güncelleştirmeleri ve güvenlik düzeltme [eklerini](https://support.microsoft.com/office/2ab296f3-7f03-43a2-8e50-46de917611c5) yükleyebilirsiniz.

Outlook 2013 ve 2016 istemcileriniz için düzeltme eki sürümleri şunlardır:

- **Outlook 2016**: 16.0.4534.1001 veya üzeri.

- **Outlook 2013**: 15.0.4937.1000 veya üzeri.

Tek tek güvenlik düzeltme ekleri hakkında daha fazla bilgi için bkz:

- [Outlook 2016 Güvenlik Düzeltme Eki](https://support.microsoft.com/help/3191883)

- [Outlook 2013 Güvenlik Düzeltme Eki](https://support.microsoft.com/help/3191938)

### <a name="third-monitor-your-outlook-clients"></a>Üçüncü: Outlook istemcilerinizi izleme

Düzeltme ekleri ve güncelleştirmeler yüklü olsa bile, bir saldırganın "Uygulamayı Başlat" davranışını yeniden etkinleştirmek için yerel makine yapılandırmasını değiştirmesinin mümkün olduğunu unutmayın. İstemcilerinizde yerel makine ilkelerini izlemek ve zorunlu kılmak için [Gelişmiş grup ilkesi Yönetimi'ni](/microsoft-desktop-optimization-pack/agpm/) kullanabilirsiniz.

Windows'nin [64 bit sürümlerini kullanarak sistem kayıt defterini görüntüleme'deki](https://support.microsoft.com/help/305097) bilgileri kullanarak kayıt defterindeki bir geçersiz kılma aracılığıyla "Uygulamayı Başlat" özelliğinin yeniden etkinleştirilip etkinleştirilmediğini görebilirsiniz. Şu alt anahtarları denetleyin:

- **Outlook 2016**:`HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Outlook\Security\`

- **Outlook 2013**:`HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Outlook\Security\`

EnableUnsafeClientMailRules anahtarını arayın. Oradaysa ve 1 olarak ayarlandıysa, Outlook güvenlik düzeltme eki geçersiz kılınmıştır ve bilgisayar Form/Kurallar saldırısına karşı savunmasızdır. Değer 0 ise, "Uygulamayı Başlat" eylemi devre dışı bırakılır. Outlook güncelleştirilmiş ve düzeltme eki uygulanmış sürümü yüklüyse ve bu kayıt defteri anahtarı yoksa, sistem bu saldırılara karşı savunmasız değildir.

Şirket içi Exchange yüklemeleri olan müşteriler, düzeltme ekleri bulunmayan eski Outlook sürümlerini engellemeyi düşünmelidir. Bu işlemle ilgili ayrıntılara [Outlook istemci engellemeyi yapılandırma](/exchange/configure-outlook-client-blocking-exchange-2013-help) makalesinde bulunabilir.

## <a name="secure-microsoft-365-like-a-cybersecurity-pro"></a>Siber güvenlik uzmanı gibi güvenli Microsoft 365

Microsoft 365 aboneliğiniz, verilerinizi ve kullanıcılarınızı korumak için kullanabileceğiniz güçlü bir güvenlik özellikleri kümesiyle birlikte gelir. microsoft'un Microsoft 365 kiracınızın güvenliğini sağlamaya yönelik önerilen en iyi yöntemleri uygulamak [için Microsoft 365 güvenlik yol haritası - İlk 30 gün, 90 gün ve sonrasındaki en önemli öncelikleri](security-roadmap.md) kullanın.

- İlk 30 günde gerçekleştirecek görevler. Bunlar hemen etkili olur ve kullanıcılarınız için düşük etkiye sahiptir.

- 90 gün içinde gerçekleştirecek görevler. Bunların planlanıp uygulanması biraz daha zaman alır ancak güvenlik duruşunuzu büyük ölçüde geliştirir.

- 90 günden fazla. Bu geliştirmeler ilk 90 günlük çalışmanızda derlemektedir.

## <a name="see-also"></a>Ayrıca bkz:

- Kurallar Vektör hakkında SilentBreak Güvenlik Gönderisi'nin [Kötü Amaçlı Outlook Kuralları](https://silentbreaksecurity.com/malicious-outlook-rules/), Outlook Kurallarının nasıl yapıldığını ayrıntılı bir şekilde gözden geçirmenizi sağlar.

- Mailrule Pwnage hakkındaki Sensepost blogundaki [HTTP ve Mailrule Pwnage üzerinden MAPI](https://sensepost.com/blog/2016/mapi-over-http-and-mailrule-pwnage/), Outlook kuralları aracılığıyla posta kutularında yararlanmanıza olanak tanıyan Cetvel adlı bir aracı ele alır.

- Formlar Tehdit Vektörüne ilişkin Sensepost bloguna [formlar ve kabuklar Outlook](https://sensepost.com/blog/2017/outlook-forms-and-shells/).

- [Cetvel Kod Tabanı](https://github.com/sensepost/ruler)

- [Ele Geçirilenin Cetvel Göstergeleri](https://github.com/sensepost/notruler/blob/master/iocs.md)
