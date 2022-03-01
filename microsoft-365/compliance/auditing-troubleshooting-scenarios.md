---
title: Sık karşılaşılan senaryoları gidermek için denetim günlüğünde arama yapın
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: E-posta hesaplarıyla ilgili Microsoft 365 sorunları gidermeye yardımcı olmak için denetim günlüğü arama aracını nasıl kullanabileceğinizi öğrenin.
ms.openlocfilehash: 496729c7955448519d6cb1447e08b5a4b15aa655
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "63014272"
---
# <a name="search-the-audit-log-to-investigate-common-support-issues"></a>Sık karşılaşılan destek sorunlarını araştırmak için denetim günlüğünde arama yapın

Bu makalede, sık karşılaşılan destek sorunlarını araştırmanıza yardımcı olmak için denetim günlüğü arama aracının nasıl kullanıldığı açıklanmıştır. Bu, denetim günlüğünü kullanarak şunları yapmak için içerir:

- Güvenliği ihlal edilmiş bir hesaba erişmek için kullanılan bilgisayarın IP adresini bulma
- Posta kutusu için e-posta iletmeyi kimin ayarlay hazır olduğunu belirleme
- Kullanıcının posta kutusudaki e-posta öğelerini s olup olmadığını belirleme
- Kullanıcının gelen kutusu kuralı oluşturduğuna karar verin
- Kuruluş dışından bir kullanıcı tarafından başarılı bir oturum açmanın neden olduğunu araştırma
- E5 lisansı olmayan kullanıcılar tarafından gerçekleştirilen posta kutusu etkinliklerini arama
- Temsilci kullanıcılar tarafından gerçekleştirilen posta kutusu etkinliklerini arama

## <a name="using-the-audit-log-search-tool"></a>Denetim günlüğü arama aracını kullanma

Bu makalede açıklanan sorun giderme senaryolarının her biri, aşağıdaki makaledeki denetim günlüğü arama aracını Microsoft 365 uyumluluk merkezi. Bu bölümde, denetim günlüğünde arama yapmak için gereken izinler liste olmakta ve denetim günlüğü aramalarına erişme ve bu aramaları çalıştırma adımları açık almaktadır. Her senaryo bölümünde, denetim günlüğü arama sorgusunu yapılandırma ve denetim kayıtlarında arama ölçütleriyle eşleşmeye uygun ayrıntılı bilgilerde nelerin aranacakları açıklandı.

### <a name="permissions-required-to-use-the-audit-log-search-tool"></a>Denetim günlüğü arama aracını kullanmak için gereken izinler

Denetim günlüğünde arama View-Only için Exchange Online Günlükleri veya Denetim Günlükleri rolüne atanmanız gerekir. Varsayılan olarak, bu roller yönetim merkezinin İzinler sayfasında yer alan Uyumluluk Yönetimi <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">ve Kuruluş Exchange atanır</a>. Office 365 ve Microsoft 365 genel yöneticiler otomatik olarak Kuruluş Yönetimi rol grubuna üye olarak Exchange Online. Daha fazla bilgi için bkz[. Gruptaki rol gruplarını Exchange Online](/Exchange/permissions-exo/role-groups).

### <a name="running-audit-log-searches"></a>Denetim günlüğü aramalarını çalıştırma

Bu bölümde, denetim günlüğü aramaları oluşturma ve çalıştırmayla ilgili temel bilgiler açık bir şekilde açık almaktadır. Bu makaledeki her sorun giderme senaryosu için başlangıç noktası olarak bu yönergeleri kullanın. Daha ayrıntılı adım adım yönergeler için bkz. [Denetim günlüğünde arama.](search-the-audit-log-in-security-and-compliance.md#step-1-run-an-audit-log-search)

1. İş veya <https://compliance.microsoft.com/auditlogsearch> okul hesabınızla oturum açın ve gidin.
  
    **Denetim sayfası** görüntülenir.
  
    ![Ölçütleri yapılandırabilirsiniz ve sonra da Arama'ya seçerek aramanızı çalıştırın.](../media/AuditLogSearchPage1.png)
  
2. Aşağıdaki arama ölçütlerini yapılandırabilirsiniz. Bu makaledeki her sorun giderme senaryosu, bu alanları yapılandırmak için özel kılavuzlar önermektedir.
  
   a. **Başlangıç tarihi** **ve Bitiş tarihi:** Bir tarih ve saat aralığı seçerek, o dönem içinde 4. Son yedi gün varsayılan olarak seçilidir. Tarih ve saat, Eşgüdümli Evrensel Saat (UTC) biçiminde görüntülenir. Belirtmezseniz, en uzun tarih aralığı 90 gündür.

   b. **Etkinlikler:** Arayabilirsiniz etkinlikleri görüntülemek için açılan listeyi seçin. Siz arama çalıştırdikten sonra, yalnızca seçili etkinliklere yönelik denetim kayıtları görüntülenir. Tüm etkinlikler **için sonuçları göster'i seçerek** , diğer arama ölçütlerine uyan tüm etkinliklere yönelik sonuçlar görüntülenir. Sorun giderme senaryolarının bazılarında da bu alanı boş bırakmanız gerekir.
  
    c. **Kullanıcılar:** Bu kutuya tıklayın ve arama sonuçlarını görüntülemek için bir veya birden çok kullanıcı seçin. Bu kutuda seçtiğiniz kullanıcılar tarafından gerçekleştirilen seçili etkinliğin denetim kayıtları, sonuç listesinde görüntülenir. Tüm kullanıcılara (ve hizmet hesaplarına) ait girdilerin kuruma geri dönmesi için bu kutuyu boş bırakın.
  
    d. **Dosya, klasör veya site:** Belirtilen anahtar sözcüğü içeren klasör dosyasıyla ilgili etkinliği aramak için, dosya veya klasör adının bir veya hepsini yazın. Dosya veya klasörün URL'sini de belirtebilirsiniz. URL kullanıyorsanız, tam URL yolunu yazın veya URL'nin yalnızca bir bölümünü yazarak özel karakter ya da boşluk içermein. Kuruma ait tüm dosya ve klasörlere ait girdilerin geri dönmesi için bu kutuyu boş bırakın. Bu alan, bu makaledeki tüm sorun giderme senaryolarında boş bırakılır.
  
3. Arama **ölçütlerinizi** kullanarak arama çalıştırmak için Ara'ya seçin.
  
    Arama sonuçları yüklenir ve birkaç dakika sonra denetim günlüğü arama aracının bir sayfasında görüntülenir. Bu makaledeki bölümlerden her biri, belirli bir sorun giderme senaryosu bağlamında bakmanız gerekenler konusunda yol gösterici bilgi sağlar.

    Denetim günlüğü arama sonuçlarını görüntüleme ve dışarı aktarma hakkında daha fazla bilgi için bkz:

    - [Arama sonuçlarını görüntüleme](search-the-audit-log-in-security-and-compliance.md#step-2-view-the-search-results)
  
    - [Arama sonuçlarını dışarı aktarma](search-the-audit-log-in-security-and-compliance.md#step-3-export-the-search-results-to-a-file)

## <a name="find-the-ip-address-of-the-computer-used-to-access-a-compromised-account"></a>Güvenliği ihlal edilmiş bir hesaba erişmek için kullanılan bilgisayarın IP adresini bulma

Denetim kayıtlarının çoğuna, herhangi bir kullanıcı tarafından gerçekleştirilen bir etkinlikle ilgili IP adresi dahildir. Kullanılan istemciyle ilgili bilgiler denetim kaydına da dahil edilir.

Bu senaryo için denetim günlüğü arama sorgusunu şu şekilde yapılandırabilirsiniz:

**Etkinlikler:** Davanızla ilgili ise aramak istediğiniz belirli bir etkinliği seçin. Güvenliği ihlal edilmiş hesaplarda sorun giderme için, Kullanıcı posta kutusu etkinlikleri altında **Posta kutusu** **etkinliğinde oturum Exchange seçin**. Bu, posta kutusunda oturum a oturum aken kullanmakta olan IP adresini gösteren denetim kayıtlarını döndürür. Aksi takdirde, tüm etkinliklere yönelik denetim kayıtlarının iade etmek için bu alanı boş bırakın. 

> [!TIP]
> Bu alan boş bırakılırsa, bir kullanıcı hesabında oturum Azure Active Directory bir kullanıcı etkinliği olan **UserLoggedIn** etkinlikleri döner. **UserLoggedIn denetim kayıtlarını görüntülemek için arama sonuçlarında filtrelemeyi** kullanın.

**Başlangıç tarihi** **ve Bitiş tarihi:** Araştırmanız için geçerli olan bir tarih aralığı seçin.

**Kullanıcılar:** Güvenliği ihlal edilmiş bir hesabı araştırıyorsanız, hesabı güvenliği ihlal edilmiş olan kullanıcıyı seçin. Bu işlem, o kullanıcı hesabı tarafından gerçekleştirilen etkinliklerin denetim kayıtlarını döndürür.

**Dosya, klasör veya site:** Bu alanı boş bırakın.

Siz aramayı çalıştırdıktan sonra, arama sonuçlarının **IP adresi sütununda her etkinliğin IP** adresi görüntülenir. Uçarak giriş sayfasında daha ayrıntılı bilgi görüntülemek için arama sonuçlarında kaydı seçin.

## <a name="determine-who-set-up-email-forwarding-for-a-mailbox"></a>Posta kutusu için e-posta iletmeyi kimin ayarlay hazır olduğunu belirleme

Posta kutusu için e-posta iletme yapılandırıldığında, posta kutusuna gönderilen e-posta iletileri başka bir posta kutusuna ilet olur. İletiler, kuruluş içindeki veya dışındaki kullanıcılara iletebilirsiniz. Bir posta kutusunda e-posta iletme ayar olduğunda, Exchange Online için temel alınan ileti **Set-Mailbox cmdlet'tir**.

Bu senaryo için denetim günlüğü arama sorgusunu şu şekilde yapılandırabilirsiniz:

**Etkinlikler:** Aramanın tüm etkinlikler için denetim kayıtlarını döndürt etmek için bu alanı boş bırakın. Bu, Set-Mailbox cmdlet'iyle **ilgili tüm denetim kayıtlarının geri** dönmesi için gereklidir.

**Başlangıç tarihi** **ve Bitiş tarihi:** Araştırmanız için geçerli olan bir tarih aralığı seçin.

**Kullanıcılar:** Belirli bir kullanıcı için e-posta iletme sorunu araştırıyorsanız, bu alanı boş bırakın. Bu, e-posta iletmenin herhangi bir kullanıcı için ayarlanmış olup olduğunu tanımlamanıza yardımcı olur.

**Dosya, klasör veya site:** Bu alanı boş bırakın.

Aramanızı çalıştırdikten sonra, arama **sonuçları sayfasında Sonuçları** filtrele'yi seçin. Etkinlik sütun başlığı altındaki **kutuya** , **Set-Mailbox** yazın; böylelikle yalnızca **Set-Mailbox** cmdlet'iyle ilgili denetim kayıtları görüntülenir.

![Denetim günlüğü arama sonuçlarına filtre uygulama.](../media/emailforwarding1.png)

Bu noktada, etkinliğin e-posta iletmeyle ilgili olup olmadığını belirlemek için her denetim kaydının ayrıntılarına bakabilirsiniz. Denetim kaydını seçerek **Ayrıntılar çıkış sayfasını** görüntüleyebilirsiniz ve sonra da Daha fazla **bilgi'yi seçin**. Aşağıdaki ekran görüntüsü ve açıklamalar, posta kutusunda e-posta iletmenin ayarlanmış olduğunu gösteren bilgileri vurgular.

![Denetim kaydından ayrıntılı bilgiler.](../media/emailforwarding2.png)

a. **ObjectId alanında**, e-posta iletmenin ayar olduğu posta kutusunun diğer adı görüntülenir. Bu posta kutusu, arama sonuçları **sayfasının** Öğe sütununda da görüntülenir.

b. Parametreler **alanında** *ForwardingSmtpAddress* değeri, posta kutusunda e-posta iletmenin ayar olduğunu gösterir. Bu örnekte, posta diğer kuruluşun dışında bulunan mike@contoso.com e-posta adresine alpinehouse.onmicrosoft.com iletildi.

c. *DeliverToMailboxAndForward* parametresinin *True* değeri, iletinin bir kopyasının sarad@alpinehouse.onmicrosoft.com'a teslim edilir ve *ForwardingSmtpAddress* parametresi tarafından belirtilen e-posta adresine iletilebilir; bu örnekte bu değer mike@contoso.com. *DeliverToMailboxAndForward* parametresinin değeri *False* olarak ayarlanırsa, e-posta yalnızca *ForwardingSmtpAddress* parametresi tarafından belirtilen adrese iletilebilir. NesneKimlik alanında belirtilen posta kutusuna **teslim edilir** .

d. **UserId alanı**, ObjectId alanında belirtilen posta kutusunda e-posta iletmeyi ayar eden **kullanıcıyı** gösterir. Bu kullanıcı, arama sonuçları **sayfasının** Kullanıcı sütununda da görüntülenir. Bu durumda, posta kutusunun sahibi posta kutusunda e-posta iletmeyi ayarlamış gibi görünüyor.

Posta kutusunda e-posta iletmenin ayar olmaması gerektiğini belirlersanız, Exchange Online PowerShell'de aşağıdaki komutu çalıştırarak bunu kaldırabilirsiniz:

```powershell
Set-Mailbox <mailbox alias> -ForwardingSmtpAddress $null 
```

E-posta iletmeyle ilgili parametreler hakkında daha fazla bilgi için, [Set-Mailbox makalesine](/powershell/module/exchange/set-mailbox) bakın.

## <a name="determine-if-a-user-deleted-email-items"></a>Kullanıcının e-posta öğelerini s olup olmadığını belirleme

Ocak 2019'dan başlayarak, Microsoft tüm microsoft kuruluşları ve Office 365 kutusu denetim günlüğünü varsayılan olarak etkinleştirdi. Bu, posta kutusu sahipleri tarafından gerçekleştirilen bazı eylemlerin otomatik olarak günlüğe kaydedileceğini ve posta kutusu denetim günlüğünde arama gerçekleştirerek ilgili posta kutusu denetim kayıtlarının kullanılabilir olduğu anlamına gelir. Posta kutusu denetimi varsayılan olarak açıkken, önce bunu organizasyonu tüm kullanıcı posta kutuları için el ile etkinleştirmeniz gerekmektedir. 

Varsayılan olarak günlüğe kaydedilen posta kutusu eylemleri, posta kutusu sahipleri tarafından gerçekleştirilen SoftDelete ve HardDelete posta kutusu eylemlerini içerir. Bu da, denetim günlüğünde silinmiş e-posta öğeleriyle ilgili olayları aramak için aşağıdaki adımları kullanabileceğiniz anlamına gelir. Posta kutusu denetimi hakkında varsayılan olarak daha fazla bilgi için bkz. [Posta kutusu denetimini yönetme](enable-mailbox-auditing.md).

Bu senaryo için denetim günlüğü arama sorgusunu şu şekilde yapılandırabilirsiniz:

**Etkinlikler:** Posta **Exchange etkinliklerine erişin** altında, aşağıdaki etkinliklerden birini veya her ikisini de seçin:

- **Silinmiş Öğeler klasöründen silinen iletiler:** Bu etkinlik, **SoftDelete posta kutusu** denetim eylemine karşılık gelen bir eylemdir. Bu etkinlik, kullanıcı öğeyi seçerek ve **Shift+Delete** tuşlarına basarak kalıcı olarak silebilir. Öğe kalıcı olarak silindikten sonra, kullanıcı silinmiş öğe bekletme süresi dolana kadar öğeyi kurtarabilirsiniz.

- **İletiler posta kutusundan temizildi:** Bu etkinlik, **HardDelete posta kutusu denetim** eylemine karşılık gelen bir eylemdir. Kullanıcı Kurtarılabilir Öğeler klasöründen bir öğeyi temizleye olduğunda bu günlüğe kaydedilir. Yöneticiler, güvenlik ve uyumluluk merkezinde bulunan İçerik Arama aracını kullanarak, silinen öğe bekletme süresi dolana kadar veya kullanıcının posta kutusu saklamaya devam ediyorsa daha uzun süre depolayana kadar, temizli öğeleri arayabilir ve kurtarabilirsiniz.

**Başlangıç tarihi** **ve Bitiş tarihi:** Araştırmanız için geçerli olan bir tarih aralığı seçin.

**Kullanıcılar:** Bu alandan bir kullanıcı seçiyorsanız, denetim günlüğü arama aracı belirttiğiniz kullanıcı tarafından silinen (SoftDeleted veya HardDeleted) e-posta öğelerinin denetim kayıtlarını döndürür. Bazen e-postayı senen kullanıcı posta kutusunun sahibi o zaman değildir.

**Dosya, klasör veya site:** Bu alanı boş bırakın.

Arama çalıştırtıktan sonra, otomatik silinmiş veya sabit silinmiş öğeler için denetim kayıtlarını görüntülemek için arama sonuçlarına filtre ebilirsiniz. Denetim kaydını seçerek **Ayrıntılar çıkış sayfasını** görüntüleyebilirsiniz ve sonra da Daha fazla **bilgi'yi seçin**. Silinen öğe hakkında ek bilgiler, örneğin konu satırı ve silindiğinde öğenin konumu **AffectedItems alanında** görüntülenir. Aşağıdaki ekran görüntüleri, yumuşak **silinmiş bir** öğeden ve sabit silinmiş bir öğeden etkilenen Öğe alanına bir örnek gösterir.

**Yumuşak silinmiş öğe için affecteditems alanı örneği**

![Yumuşak silinmiş öğe için denetim kaydı.](../media/softdeleteditem.png)

**Sabit silinmiş öğe için affecteditems alanı örneği**

![Sabit silinmiş e-posta öğesi için denetim kaydı.](../media/harddeleteditem.png)

### <a name="recover-deleted-email-items"></a>Silinmiş e-posta öğelerini kurtarma

Silinmiş öğelerin bekletme süresi dolmamışsa, kullanıcılar yumuşak silinmiş öğeleri kurtarabilirsiniz. Son Exchange Online, varsayılan silinmiş öğelerin bekletme süresi 14 gündür, ancak yöneticiler bu ayarı en çok 30 gün olacak şekilde artırabilir. Kullanıcıları, Silinmiş öğeleri [kurtarma yönergeleri için Web üzerinde Outlook](https://support.office.com/article/Recover-deleted-items-or-email-in-Outlook-Web-App-C3D8FC15-EEEF-4F1C-81DF-E27964B7EDD4) kurtar makalesinde Silinmiş öğeleri veya e-postaları kurtar'a işaret edin.

Daha önce de belirtildiği gibi, yöneticiler silinmiş öğe bekletme süresinin dolmamış olması veya posta kutusunun saklama durumunda olması durumunda kalıcı olarak silinmiş öğeleri kurtarabilecektir. Bu durumda, tutma süresi dolana kadar öğeler tutulur. İçerik aramasında çalıştırsanız, Kurtarılabilir Öğeler klasöründeki yumuşak silinmiş ve sabit silinmiş öğeler, arama sorgusuyla eşleşirse arama sonuçlarında döndürülür. İçerik aramalarını çalıştırma hakkında daha fazla bilgi için bkz. İçerik [Arama ve Office 365](content-search.md).

> [!TIP]
> Silinmiş e-posta öğelerini aramak için, denetim kaydının **AffectedItems** alanında görüntülenen konu satırın bir bölümünü veya bir bölümünü arama.

## <a name="determine-if-a-user-created-an-inbox-rule"></a>Kullanıcının gelen kutusu kuralı oluşturduğuna karar verin

Kullanıcılar kendi posta kutuları için bir gelen Exchange Online, buna karşılık gelen bir denetim kaydı denetim günlüğüne kaydedilir. Gelen kutusu kuralları hakkında daha fazla bilgi için bkz:

- [E-postada gelen kutusu kurallarını Web üzerinde Outlook](https://support.office.com/article/use-inbox-rules-in-outlook-on-the-web-8400435c-f14e-4272-9004-1548bb1848f2)
- [E-posta iletilerini Outlook kullanarak e-posta iletilerini yönetme](https://support.office.com/article/Manage-email-messages-by-using-rules-C24F5DEA-9465-4DF4-AD17-A50704D66C59)

Bu senaryo için denetim günlüğü arama sorgusunu şu şekilde yapılandırabilirsiniz:

**Etkinlikler:** Posta **Exchange etkinliklerine erişin** altında, aşağıdaki etkinliklerden birini veya her ikisini de seçin:

- **Yeni Gelen KutusuSağdan gelen kutusu kuralı Outlook Web App**. Outlook Web App veya PowerShell kullanarak gelen kutusu kuralları Exchange Online bu etkinlik denetim kayıtlarını döndürür.

- **İstemci tarafından güncelleştirilmiş gelen Outlook kuralları**. Masaüstü istemcisinde gelen kutusu kuralları oluşturulduğunda, değiştirildiğinde veya kaldırildiğinde, bu Outlook döndürür.

**Başlangıç tarihi** **ve Bitiş tarihi:** Araştırmanız için geçerli olan bir tarih aralığı seçin.

**Kullanıcılar:** Belirli bir kullanıcıyla ilgili araştırma yoksa bu alanı boş bırakın. Bu, herhangi bir kullanıcı tarafından ayarlanmış yeni gelen kutusu kurallarını tanımlamanıza yardımcı olur.

**Dosya, klasör veya site:** Bu alanı boş bırakın.

Siz aramayı çalıştırdikten sonra, arama sonuçlarında bu etkinliğin tüm denetim kayıtları görüntülenir. Ayrıntılar çıkış sayfasını görüntülemek için bir **denetim kaydı** seçin ve sonra da Daha fazla **bilgi'yi seçin**. Gelen kutusu kuralı ayarları hakkında bilgiler Parametreler **alanında** görüntülenir. Aşağıdaki ekran görüntüsü ve açıklamalar, gelen kutusu kurallarıyla ilgili bilgileri vurgular.

![Yeni gelen kutusu kuralı için denetim kaydı.](../media/NewInboxRuleRecord.png)

a. **ObjectId alanında**, gelen kutusu kuralının tam adı görüntülenir. Bu ad, kullanıcının posta kutusunun diğer adını (örneğin, SaraD) ve gelen kutusu kuralının adını içerir (örneğin, "İletileri yöneticiden taşı").

b. Parametreler **alanında** , gelen kutusu kuralının koşulu görüntülenir. Bu örnekte, koşul From parametresi tarafından *belirtilir* . From parametresi için tanımlanan *değer, gelen* kutusu kuralının posta kutusu tarafından gönderilen e-posta üzerinde eylem admin@alpinehouse.onmicrosoft.com. Gelen kutusu kurallarının koşullarını tanımlamakta kullanılan parametrelerin tam listesi için, [New-InboxRule makalesine](/powershell/module/exchange/new-inboxrule) bakın.

c. *MoveToFolder* parametresi gelen kutusu kuralı için eylemi belirtir. Bu örnekte, kullanıcı tarafından admin@alpinehouse.onmicrosoft.com *AdminSearch adlı klasöre taşınır*. Ayrıca, [gelen kutusu kuralının eylemlerini](/powershell/module/exchange/new-inboxrule) tanımlamak için kullanılan parametrelerin tam listesi için New-InboxRule makalesine de bakın.

d. **UserId alanı**, ObjectId alanında belirtilen gelen kutusu kuralını oluşturan **kullanıcıyı** gösterir. Bu kullanıcı, arama sonuçları **sayfasının** Kullanıcı sütununda da görüntülenir.

## <a name="investigate-why-there-was-a-successful-login-by-a-user-outside-your-organization"></a>Kuruluş dışından bir kullanıcı tarafından başarılı bir oturum açmanın neden olduğunu araştırma

Denetim günlüğünde denetim kayıtlarını gözden geçirerek, dış kullanıcının Azure Active Directory başarılı bir şekilde oturum açtığını belirten kayıtları görebilirsiniz. Örneğin, contoso.onmicrosoft.com'daki bir yönetici, farklı bir kuruluştan (örneğin, kullanıcı) bir kullanıcının fabrikam.onmicrosoft.com başarılı bir şekilde oturum açtığını gösteren bir contoso.onmicrosoft.com. Benzer şekilde, microsoft hesabı (MSA) olan ve Outlook.com veya Live.com hesabı olan kullanıcıların, Live.com başarıyla oturum açtığını belirten denetim kayıtlarını bulabilirsiniz. Böyle durumlarda, denetlenen etkinlik Kullanıcı Oturum **Aç'tır**. 

Bu davranış tasarımdan kaynaklanır. Azure Active Directory (Azure AD) dizin hizmeti, dış kullanıcı SharePoint sitesine veya OneDrive konumlarına erişmeye çalıştığında doğrudan kimlik doğrulama olarak adlandırılan bir şeye izin verir. Dış kullanıcı bunu yapmaya çalıştığında, kimlik bilgilerini girmeleri istenir. Azure AD kullanıcının kimliğini doğrulamak için kimlik bilgilerini kullanır; başka bir ifadeyle, yalnızca Azure AD kullanıcının kim olduğunu doğrular. Denetim kaydında başarılı oturum açmanın göstergesi, Azure AD'nin kullanıcı için kimlik doğrulamayı belirlemesi sonucu elde edilir. Başarılı oturum açma, kullanıcının herhangi bir kaynaklara erişeni veya kuruluş içinde başka eylemler gerçekleştir diğer eylemleri gerçekleştir olduğu anlamına değildir. Bu yalnızca kullanıcının Azure AD tarafından kimliği doğrulanmış olduğunu gösterir. Doğrudan kullanıcıdan SharePoint veya OneDrive kaynaklarına erişmesi için, kurumuz kullanıcıya paylaşım daveti veya anonim paylaşım bağlantısı göndererek kaynağı dış kullanıcıyla açıkça paylaşması gerekir. 

> [!NOTE]
> Azure AD, yalnızca SharePoint Online ve OneDrive İş gibi birinci taraf uygulamalar için geçişli kimlik OneDrive İş. Diğer üçüncü taraf uygulamalarda buna izin verilmez.

Burada, geçişli kimlik doğrulamasının sonucu olarak Günlüğe Kaydedilen Kullanıcı için bir denetim kaydında  ilgili özelliklere örnek ve açıklamalar ve bir örnek ve açıklamalar ve şekilde yer almaktadır. Denetim kaydını seçerek **Ayrıntılar çıkış sayfasını** görüntüleyebilirsiniz ve sonra da Daha fazla **bilgi'yi seçin**.

![Başarılı geçiş doğrulaması için denetim kaydı örneği.](../media/PassThroughAuth1.png)

   a. Bu alan, kuruluşta bir kaynağa erişmeye çalışan kullanıcının, kuruluşun Azure AD'sinde buluna olmadığını gösterir.

   b. Bu alanda, kurumda bir kaynağa erişmeyi denen dış kullanıcının UPN'si görüntülenir. Bu kullanıcı kimliği, denetim kaydında **User** **ve UserId** özelliklerinde de tanımlanır.

   c. **ApplicationId özelliği**, oturum açma isteğini tetikleyen uygulamayı tanımlar. Bu denetim kaydında ApplicationId özelliğinde görüntülenen 00000003-0000-0ff1-ce00-0000000000 değerinin değeri SharePoint Online olduğunu gösterir. OneDrive İş Aynı ApplicationId'ye de sahip.

   d. Bu, geçişli kimlik doğrulamanın başarılı olduğunu gösterir. Başka bir deyişle, kullanıcının kimliği Azure AD tarafından başarıyla doğrulandı. 

   e. **15** **RecordType** değeri, denetlenen etkinliğin (UserLoggedIn) Azure AD'de bir Güvenli Belirteç Hizmeti (STS) oturum açma olayı olduğunu gösterir.

UserLoggedIn denetim kaydında görüntülenen diğer özellikler hakkında daha fazla bilgi için, bir Kullanıcı Yönetimi Etkinliği API'si şemasında Azure AD ile [Office 365 bilgilerine bakın](/office/office-365-management-api/office-365-management-activity-api-schema#azure-active-directory-base-schema).

Aşağıda, geçiş kimlik doğrulaması nedeniyle başarılı bir Kullanıcı denetim etkinliğinde  oturum açan başarılı bir kullanıcı deneyimine neden olacak iki örnek senaryo verilmiştir: 

  - Microsoft Hesabı (örneğin SaraD@outlook.com) olan bir kullanıcı fourthcoffee.onmicrosoft.com'te bir OneDrive İş hesabındaki bir belgeye erişmeyi denedi ve fourthcoffee.onmicrosoft.com'te SaraD@outlook.com için buna karşılık gelen bir konuk kullanıcı hesabı yok.

  - Kuruluşta İş veya Okul hesabı olan bir kullanıcı (örneğin, pilarp@fabrikam.onmicrosoft.com) contoso.onmicrosoft.com'te bir SharePoint sitesine erişmeye çalışıyor ve pilarp@fabrikam.com'te pilarp@fabrikam.com için buna karşılık gelen bir konuk kullanıcı hesabı contoso.onmicrosoft.com.

### <a name="tips-for-investigating-successful-logins-resulting-from-pass-through-authentication"></a>İpuçları kimlik doğrulamasından elde edilen başarılı oturum açmaları araştırmanın sonuçları

- Denetim günlüğünde, Kullanıcı denetim kaydında oturum açan dış **kullanıcı tarafından gerçekleştirilen etkinlikleri** arama. Kullanıcılar kutusuna dış kullanıcının **UPN'nizi yazın** ve senaryoyla ilgili bir tarih aralığı kullanın. Örneğin, aşağıdaki arama ölçütlerini kullanarak bir arama oluşturabilirsiniz:

   ![Dış kullanıcı tarafından gerçekleştirilen tüm etkinlikleri arama.](../media/PassThroughAuth2.png)

    Kullanıcıyla oturum açma  etkinliklerine ek olarak, kuruluşta yer alan bir kullanıcının kaynakları dış kullanıcıyla paylaştığını ve dış kullanıcının kendileriyle paylaşılan bir belgeye erişip erişemediklerini, değiştirip indiremediklerini belirten diğer denetim kayıtları döndürülebilir.

- Bir SharePoint oturum açan kullanıcı tarafından tanımlanan dış kullanıcıyla paylaşılıyor olduğunu gösteren paylaşım etkinliklerini **aratır.** Daha fazla bilgi için [bkz. Denetim günlüğünde paylaşım denetimini kullanma](use-sharing-auditing.md).

- Dış kullanıcıyla ilgili diğer etkinlikleri aramak için Excel'i kullanmak üzere Excel kayıtları içeren denetim günlüğü arama sonuçlarını dışarı aktarın. Daha fazla bilgi için bkz  [. Denetim günlüğü kayıtlarını dışarı aktarma, yapılandırma ve görüntüleme](export-view-audit-log-records.md).

## <a name="search-for-mailbox-activities-performed-by-users-with-non-e5-licenses"></a>E5 lisansı olmayan kullanıcılar tarafından gerçekleştirilen posta kutusu etkinliklerini arama

Sizin için [](enable-mailbox-auditing.md) posta kutusu denetimi varsayılan olarak açık olduğunda bile, bazı kullanıcılar için posta kutusu denetim olaylarının uyumluluk merkezi, **Search-UnifiedAuditLog** cmdlet'i veya Office 365 Yönetim Etkinliği API'si kullanılarak denetim günlüğü aramalarında bulunamadiğini farkabilirsiniz. Bunun nedeni, birleşik denetim günlüğünde arama yapmak için önceki yöntemlerden biri olduğunda, yalnızca E5 lisansı olan kullanıcılar için posta kutusu denetim olaylarının döndürülecek olmasıdır.

E5 olmayan kullanıcıların posta kutusu denetim günlüğü kayıtlarını almak için, aşağıdaki geçici çözümlerden birini gerçekleştirebilirsiniz:

- Tek tek posta kutularında posta kutusu denetimini el ile etkinleştirme (`Set-Mailbox -Identity <MailboxIdentity> -AuditEnabled $true`PowerShell'de Exchange Online çalıştırın). Bunu gerçekleştirdikten sonra, uyumluluk merkezini, **Search-UnifiedAuditLog** cmdlet'ini veya Office 365 Management Activity API'sini kullanarak arama yapar.
  
  > [!NOTE]
  > Posta kutusunda posta kutusu denetimi zaten etkinleştirilmiş gibi görünüyorsa, ancak aramanız hiçbir sonuç sonuç getirmiyorsa, _AuditEnabled_ `$false` parametresinin değerini 'a ve sonra yeniden seçin `$true`.
  
- Exchange Online PowerShell'de aşağıdaki cmdlet'leri kullanın:

  - [Belirli kullanıcılar için posta kutusu denetim günlüğünde arama yapmak için Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog) .

  - [New-MailboxAuditLogSearch, belirli](/powershell/module/exchange/new-mailboxauditlogsearch) kullanıcılar için posta kutusu denetim günlüğünde arama yapmak ve sonuçların belirtilen alıcılara e-postayla gönderilmelerini sağlar.

## <a name="search-for-mailbox-activities-performed-in-a-specific-mailbox-including-shared-mailboxes"></a>Belirli bir posta kutusunda gerçekleştirilen posta kutusu etkinliklerini arama (paylaşılan posta kutuları dahil)

Denetim günlüğü arama aracında Denetim günlüğü arama aracında Kullanıcılar açılan listesini veya Exchange Online PowerShell'de **Search-UnifiedAuditLog -UserIds** komutunu kullanırken, belirli bir kullanıcı tarafından gerçekleştirilen etkinlikleri arayabilirsiniz. Posta kutusu denetim etkinlikleri için, bu tür bir arama, belirtilen kullanıcı tarafından gerçekleştirilen etkinlikleri aratır. Aynı posta kutusunda gerçekleştirilen tüm etkinliklerin arama sonuçlarında döndürülecek olması garanti değildir. Örneğin, denetim günlüğü araması temsilci kullanıcı tarafından gerçekleştirilen etkinlikler için denetim kayıtlarını geri dönmez, çünkü belirli bir kullanıcı tarafından gerçekleştirilen posta kutusu etkinlikleri için arama yapmak, başka bir kullanıcının posta kutusuna erişme izinleri atanmış olan temsilci kullanıcı tarafından gerçekleştirilen etkinlikleri geri dönmez. (Temsilci kullanıcı, başka bir kullanıcının posta kutusuna SendAs, SendOnBehalf veya FullAccess posta kutusu izni atanan kişidir.)

Ayrıca, denetim günlüğü  arama aracında veya **Search-UnifiedAuditLog -UserIds** içinde Kullanıcı açılan listesinin kullanımı, paylaşılan posta kutusunda gerçekleştirilen etkinliklere yönelik sonuçları sonuç olarak geri dönmez.

Belirli bir posta kutusunda gerçekleştirilen etkinlikleri aramak veya paylaşılan bir posta kutusunda gerçekleştirilen etkinlikleri aramak için **, Search-UnifiedAuditLog** cmdlet'ini çalıştırmada aşağıdaki söz dizimini kullanın:

```powershell
Search-UnifiedAuditLog  -StartDate <date> -EndDate <date> -FreeText (Get-Mailbox <mailbox identity).ExchangeGuid
```

Örneğin, aşağıdaki komut, Ağustos 2020 ile Ekim 2020 arasında Contoso Uyumluluk Ekibi paylaşılan posta kutusunda gerçekleştirilen etkinliklerin denetim kayıtlarını döndürür:

```powershell
Search-UnifiedAuditLog  -StartDate 08/01/2020 -EndDate 10/31/2020 -FreeText (Get-Mailbox complianceteam@contoso.onmicrosoft.com).ExchangeGuid
```

Alternatif olarak, belirli bir posta kutusunda gerçekleştirilen etkinliğin denetim kayıtlarını aramak için **Search-MailboxAuditLog** cmdlet'ini kullanabilirsiniz. Bu, paylaşılan posta kutusunda gerçekleştirilen etkinlikleri aramayı içerir.

Aşağıdaki örnek, Contoso Uyumluluk Ekibi paylaşılan posta kutusunda gerçekleştirilen etkinlikler için posta kutusu denetim günlüğü kayıtlarını döndürür:

```powershell
Search-MailboxAuditLog -Identity complianceteam@contoso.onmicrosoft.com -StartDate 08/01/2020 -EndDate 10/31/2020 -ShowDetails
```

Aşağıdaki örnek, temsilci kullanıcılar tarafından belirtilen posta kutusunda gerçekleştirilen etkinlikler için posta kutusu denetim günlüğü kayıtlarını döndürür:

```powershell
Search-MailboxAuditLog -Identity <mailbox identity> -StartDate <date> -EndDate <date> -LogonTypes Delegate -ShowDetails
```

Ayrıca, denetim günlüğünde belirli bir posta kutusu için arama yapmak ve sonuçların belirli alıcılara e-postayla gönderilmelerini için **New-MailboxAuditLogSearch** cmdlet'ini de kullanabilirsiniz.