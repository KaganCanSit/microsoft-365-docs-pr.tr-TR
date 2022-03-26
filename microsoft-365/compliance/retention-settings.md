---
title: Bekletme ayarlarını içeriği otomatik olarak korumak veya silmek üzere yapılandırma
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Bir bekletme ilkesinde veya bekletme etiketi ilkesinde, istediğiniz şeyi saklayarak ve istemediklerden kurtulmak için yapılandırabilirsiniz ayarları anlıyoruz.
ms.openlocfilehash: 3b2833b2b6293845379f9f5aeffd3bd46610e2a8
ms.sourcegitcommit: 46456ca009c9d50622e57e24269be74986184654
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2022
ms.locfileid: "63713085"
---
# <a name="common-settings-for-retention-policies-and-retention-label-policies"></a>Bekletme ilkeleri ve bekletme etiketi ilkeleri için ortak ayarlar

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](https://aka.ms/ComplianceSD)*

Bekletmeye yönelik birçok ayar, hem bekletme ilkeleri hem de bekletme etiketi ilkeleri için yaygındır. İçeriği önceden korumak, içeriği veya her ikisini birden silmek üzere bu ayarları yapılandırmanıza yardımcı olmak için aşağıdaki bilgileri kullanın; bunları korur ve sonra da silersiniz.

Bekletme için bu ilkeleri destekleyen senaryolar için bkz:

- [Bekletme ilkeleri oluşturun ve yapılandıryın](create-retention-policies.md).
- [Bekletme etiketleri oluşturma ve bunları uygulamalarda uygulama](create-apply-retention-labels.md)
- [İçeriği otomatik olarak bekletme etiketi uygulama](apply-retention-labels-automatically.md)

Ayarlar senaryoya özgü olan senaryolar ilgili belgelerinde açıklanmıştır.

Bekletme ilkeleri ve bekletmenin çalışma yöntemleri hakkında genel bilgiler Microsoft 365 bkz. Bekletme ilkeleri [ve bekletme etiketleri hakkında bilgi edinebilirsiniz](retention.md).

## <a name="scopes---adaptive-and-static"></a>Kapsamlar - uyarlanabilir ve statik

Uyarlanabilir ve statik kapsamları kullanmaya yabancı değilseniz ve bekletme için bir ilke yapılandırken hangisinin kullanıca yardımcı olması için bkz. Bekletme için uyarlanabilir veya statik ilke [kapsamları](retention.md#adaptive-or-static-policy-scopes-for-retention). 

Uyarlanabilir veya statik bir kapsam kullanmaya karar verdiyken, yapılandırmanıza yardımcı olması için aşağıdaki bilgileri kullanın:
- [Uyarlanabilir kapsamlar için yapılandırma bilgileri](#configuration-information-for-adaptive-scopes)
- [Statik kapsamlar için yapılandırma bilgileri](#configuration-information-for-static-scopes)

> [!TIP]
> Statik kapsamlar kullanan ilkeleriniz varsa ve bunları uyarlanabilir kapsamlara dönüştürmek istiyorsanız, aynı bekletme ayarlarına sahip uyarlanabilir kapsamlar kullanan yeni ilkeler hazırken var olan ilkelerinizi olduğu gibi bırakın. Statik kapsamları olan eski ilkeleri devre dışı bırakmadan veya smeden önce, bu yeni ilkelerin doğru kullanıcıları, siteleri ve grupları hedeflemektedir.

### <a name="configuration-information-for-adaptive-scopes"></a>Uyarlanabilir kapsamlar için yapılandırma bilgileri

Uyarlanabilir kapsamları kullanmayı tercih ettiyken, hangi tür uyarlanabilir kapsam kullanmak istediğiniz sorarak seçmeniz istenir. Üç farklı tür uyarlanabilir kapsam vardır ve bunlardan her biri farklı öznitelikleri veya özellikleri destekler:

| Uyarlanabilir kapsam türü | Desteklenen öznitelikler veya özellikler şunları içerir: |
|:-----|:-----|
|**Kullanıcılar** - aşağıdakiler için geçerlidir:  <br/> - Exchange-postayı gönderme <br/> - OneDrive hesapları <br/> - Teams sohbetler <br/> - Teams kanal iletilerini gönderme <br/> - Yammer iletilerini gönderme| Ad <br/> Soyadı    <br/>Görünen ad <br/> İş unvanı <br/> Bölüm <br/> Office <br/>Sokak adresi    <br/> Şehir <br/>Eyalet veya il <br/>Posta kodu <br/> Ülke veya bölge <br/> E-posta adresleri <br/> Diğer Ad <br/> Exchange öznitelikleriyle birlikte: CustomAttribute1 - CustomAttribute15|
|**SharePoint siteleri** - aşağıdakiler için geçerlidir:  <br/> - SharePoint siteleri <br/> - OneDrive hesapları |Site URL'si <br/>Site adı <br/> SharePoint özellikleri görüntüleme: RefinableString00 - RefinableString99 |
|**Microsoft 365 Grupları** - aşağıdakiler için geçerlidir:  <br/> - Microsoft 365 Grupları <br/> - Teams iletilerini (standart ve paylaşılan) içerir <br/> - Yammer iletilerini gönderme |Name <br/> Görünen ad <br/> Açıklama <br/> E-posta adresleri <br/> Diğer Ad <br/> Exchange öznitelikleriyle birlikte: CustomAttribute1 - CustomAttribute15 |

Sitelerin özellik adları, site tarafından yönetilen SharePoint temel almaktadır. Özel öznitelikler hakkında bilgi için bkz. Uyarlanabilir İlke Kapsamları ile SharePoint Bekletmeyi Uygulamak için [Microsoft 365 Site Özelliklerini Kullanma](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/using-custom-sharepoint-site-properties-to-apply-microsoft-365/ba-p/3133970).

Kullanıcıların ve grupların öznitelik adları, Azure AD [öznitelikleriyle](/powershell/exchange/recipientfilter-properties#filterable-recipient-properties) eşen filtrelenebilir alıcı özelliklerine dayalıdır. Örneğin:

- **Diğer** ad, Azure AD yönetim **merkezinde E-posta olarak gösterilen mailNickname** LDAP adıyla eşler.
- **E-posta** adresleri, Azure AD yönetim merkezinde Proxy adresi olarak gösterilen **LDAP adı proxyAddresses** ile eşler.

Tabloda listelenen öznitelikler ve özellikler, basit sorgu oluşturucusunu kullanarak uyarlanabilir bir kapsam yapılandırıldığında kolayca belirtilebilir. Ek öznitelikler ve özellikler, aşağıdaki bölümde açıklandığı gibi, gelişmiş sorgu oluşturucusu tarafından de destekler.

> [!TIP]
> Gelişmiş sorgu oluşturucusunu kullanma hakkında ek bilgi için aşağıdaki web seminerine bakın: 
> - [Uyarlanabilir İlke Kapsamlarına Sahip Kullanıcılar ve Gruplar için Gelişmiş Sorgular Oluşturmak](https://mipc.eventbuilder.com/event/52683/occurrence/49452/recording?rauth=853.3181650.1f2b6e8b4a05b4441f19b890dfeadcec24c4325e90ac492b7a58eb3045c546ea)
> - [Uyarlanabilir İlke Kapsamları olan SharePoint Siteleri için Gelişmiş Sorgular Oluşturmak](https://aka.ms/AdaptivePolicyScopes-AdvancedSharePoint)

Tek bir bekletme ilkesi bir veya birden çok uyarlanabilir kapsamına sahip olabilir.

#### <a name="to-configure-an-adaptive-scope"></a>Uyarlanabilir bir kapsamı yapılandırmak için

Uyarlanabilir kapsamınızı yapılandırmadan önce, hangi kapsam türünü oluşturacağız ve hangi öznitelikleri ve değerleri kullanacağız belirlemek için önceki bölümü kullanın. Bu bilgileri onaylamak için diğer yöneticilerle birlikte çalışmanız gerekiyor olabilir. 

Özel olarak SharePoint site özelliklerini kullanmayı planlıyorsanız SharePoint ek yapılandırma [gerekmektedir](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/using-custom-sharepoint-site-properties-to-apply-microsoft-365/ba-p/3133970).

1. Gezinti [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com/) konumlardan birini seçin:
    
    - Kayıt yönetimi çözümünü kullanıyorsanız:
        - **Çözümler** >  **Kayıt yönetimi** >  **Uyarlanabilir kapsamlar** sekmesi > + **Kapsam oluştur**
        
    - Bilgi yönetimi çözümünü kullanıyorsanız:
       - **Çözümler** >  **Bilgi yönetimi** >  **Uyarlanabilir kapsamlar** sekmesi > + **Kapsam oluştur**
    
    Çözümlerinizi gezinti bölmesinde hemen görmüyor musunuz? Önce, Hepsini **göster'i seçin**. 

2. Önce kapsamın türünü seçmek için yapılandırmada istemleri izleyin, sonra dinamik üyeliği oluşturmak için kullanmak istediğiniz öznitelikleri veya özellikleri seçin, sonra öznitelik veya özellik değerlerini yazın.
    
    Örneğin, Avrupa'daki kullanıcıları tanımlamak için kullanılacak uyarlanabilir bir kapsam yapılandırmak için, önce kapsam türü olarak  Kullanıcılar'ı seçin, ardından Ülke veya bölge özniteliğini seçin ve Avrupa'da **yazın**:
    
    ![Örnek uyarlanabilir kapsam yapılandırması.](../media/example-adaptive-scope.png)
    
    Bu sorgu, günde bir kez Azure AD'de çalıştırarak, Ülke veya bölge özniteliğine yönelik  hesaplarında Avrupa değeri belirtilen tüm **kullanıcıları** tanımlayabilir.
    
    > [!IMPORTANT]
    > Sorgu hemen çalışmay olduğundan, değere doğru şekilde yazarak doğrulamanız olmaz.
    
    Sorgu **oluşturmak üzere mantıksal** işleçlerle birlikte, kapsam türlerinde desteklenen öznitelik veya özelliklerin herhangi bir bileşimini kullanmak için Öznitelik ekle (kullanıcılar ve gruplar için) veya **Add** özelliği (siteler için) seçeneğini seçin. Desteklenen işleçler **eşittir****, eşit** **değildir, başlangıç** ile başlar, başlamaz ve seçilen öznitelikleri veya özellikleri grupabilirsiniz. Örneğin:
    
    ![Öznitelik gruplamaları ile örnek uyarlanabilir kapsam yapılandırması.](../media/example-adaptive-scope-grouping.png)
    
    Alternatif olarak, kendi sorgularınızı **belirtmek için** Gelişmiş sorgu oluşturucusu'nu da kullanabilirsiniz:
    
    - Kullanıcı **ve** Kullanıcı **Microsoft 365 kapsamları** için, [OPATH filtreleme söz dizimi kullanın](/powershell/exchange/recipient-filters). Örneğin, üyeliğini departmana, ülkeye ve eyalete göre tanımlayan bir kullanıcı kapsamı oluşturmak için:
    
        ![Gelişmiş sorguyla örnek uyarlanabilir kapsam.](../media/example-adaptive-scope-advanced-query.png)
        
        Bu kapsamlar için gelişmiş sorgu oluşturucusunu kullanmanın avantajlarından biri, daha geniş bir sorgu işleci seçeneğidir:
        - **ve**
        - **veya**
        - **not**
        - **eq** (eşittir)
        - **ne** (eşit değildir)
        - **lt** (küçükten küçük)
        - **gt** (büyüktür)
        - **like** (dize karşılaştırması)
        - **notlike** (dize karşılaştırması)
    
    - Site **SharePoint için** Anahtar Sözcük Sorgu Dili'yi (KQL) kullanın. Dizinli site özelliklerini kullanarak arama yapmak için KQL SharePoint zaten biliyor olabileceğiniz gibi görünüyor. Bu KQL sorgularını belirtmenize yardımcı olmak için bkz. [Anahtar Sözcük Sorgu Dili (KQL) söz dizimi başvurusu](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference).
        
        Örneğin, SharePoint sitelerin kapsamları Microsoft 365 bağlantılı ve OneDrive sitelerini içeren tüm SharePoint site türlerini otomatik olarak dahil olduğundan, belirli site türlerini eklemek veya dışarıda tutmak için **SiteTemplate** dizinli site özelliğini kullanabilirsiniz. Belirtebilirsiniz şablonlar:
        - Modern iletişim siteleri için SITEPAGEPUBLISHING
        - Grup bağlantılı Microsoft 365 için GROUP
        - Özel kanal siteleri için MICROSOFT TEAMS TEAMCHANNEL
        - Klasik bir ekip sitesi SharePoint STS
        - Web siteleri için SPSPERS OneDrive siteleri
        
        Dolayısıyla, yalnızca modern iletişim sitelerini içeren ve goup bağlantılı ve Microsoft 365 sitelerini hariç OneDrive uyarlanabilir kapsam oluşturmak için, aşağıdaki KQL sorgusunu belirtin:
        ````console
        SiteTemplate=SITEPAGEPUBLISHING
        ````
    
    Bu gelişmiş [sorguları, kapsam yapılandırmasından](#validating-advanced-queries) bağımsız olarak doğruabilirsiniz.
    
    > [!TIP]
    > Etkin olmayan posta kutularını dışarıda tutmak için gelişmiş sorgu oluşturucusunu kullanabilirsiniz. Veya tersine, yalnızca etkin olmayan posta kutularını hedef alın. Bu yapılandırmada, *IsInactiveMailbox OPATH özelliğini kullanın*:
    > 
    > - Etkin olmayan posta kutularını dışarıda tutmak için, sorgunun şunları içerir: `(IsInactiveMailbox -eq "False")`
    > - Yalnızca etkin olmayan posta kutularını hedeflemek için şunları belirtin: `(IsInactiveMailbox -eq "True")`

3. Size gereken sayıda uyarlanabilir kapsam oluşturun. Bekletme ilkenizi  hazırlarken bir veya birden çok uyarlanabilir kapsam da kullanabilirsiniz.

> [!NOTE]
> Sorguların tümüyle dolu olması beş gün kadar sürer ve değişiklikler anında olmaz. Bekletme ilkesine yeni oluşturulmuş bir kapsam eklemeden birkaç gün önce bekleerek, bu gecikmede faktör.

Uyarlanabilir bir kapsamda geçerli üyelik ve üyelik değişikliklerini onaylamak için:

1. Uyarlanabilir kapsamlar sayfasında kapsamı çift tıklatın (veya seçin ve Enter **tuşuna basın** )

2. Uçarak **Çıkış Ayrıntıları bölmesinde** Kapsam ayrıntıları'nın **seçin**. 
    
    Otomatik olarak eklenmiş veya kaldırılmışsa, o kapsamda bulunan tüm kullanıcıları, siteleri veya grupları tanımlayan bilgileri ve bu üyelik değişikliğinin tarihi ve saatiyle ilgili bilgileri gözden geçirebilirsiniz.

> [!TIP]
> Şu anda [belirli kullanıcılara](retention.md#policy-lookup), sitelere ve site gruplarına atanmış olan ilkeleri tanımlamanıza yardımcı olacak ilke arama Microsoft 365 kullanın.

#### <a name="validating-advanced-queries"></a>Gelişmiş sorguları doğrulama

Gelişmiş sorguları PowerShell kullanarak el ile doğrulayan ve arama SharePoint yapabilirsiniz:
- PowerShell'i Kullanıcılar **ve Kullanıcı Grupları** Microsoft 365 **kullanma**
- Sitelerin SharePoint türünü aramak için **SharePoint kullanma**

PowerShell kullanarak sorgu çalıştırmak için:

1. [Bağlan izinlerine Exchange Online bir hesap kullanarak PowerShell'i](/powershell/exchange/connect-to-exchange-online-powershell) [Exchange Online seçin](/powershell/exchange/find-exchange-cmdlet-permissions#use-powershell-to-find-the-permissions-required-to-run-a-cmdlet).

2. -Filter [parametresiyle Get-Recipient](/powershell/module/exchange/get-recipient) veya [Get-Mailbox'ı](/powershell/module/exchange/get-mailbox) ve kıvrımlı ayraç (`{`,) içine alınmış uyarlanabilir kapsam için [OPATH](/powershell/exchange/filter-properties) sorgunuz kullanın.`}` Öznitelik değerleriniz dize ise, bu değerleri çift veya tek tırnak içine alın.  

    Sorgunuz için seçtiğiniz `Get-Mailbox` `Get-Recipient` [OPATH](/powershell/exchange/filter-properties) özelliği tarafından desteklenen cmdlet'in hangi cmdlet'i kullanıp desteklemediğini belirleyerek, doğrulama için mi kullan belirleyebilirsiniz.

    > [!IMPORTANT]
    > `Get-Mailbox`*MailUser* alıcı türünü desteklemez, bu `Get-Recipient` nedenle karma bir ortamda şirket içi posta kutuları içeren sorguları doğrulamak için kullanılmalıdır.

    Kullanıcı kapsamını **doğrulamak için** , aşağıdaki iki işlemden birini kullanın:
    - `Get-Mailbox`veya `-RecipientTypeDetails UserMailbox`
    - `Get-Recipient` ile `-RecipientTypeDetails UserMailbox,MailUser`
    
    Bir Grup Microsoft 365 **doğrulamak** için şunları kullanın:
    - `Get-Mailbox`veya `Get-Recipient``-RecipientTypeDetails GroupMailbox`

    Örneğin, bir Kullanıcı kapsamını **doğrulamak** için şunları kullanabilirsiniz:
    
    ````PowerShell
    Get-Recipient -RecipientTypeDetails UserMailbox,MailUser -Filter {Department -eq "Marketing"} -ResultSize Unlimited
    ````
    
    Bir Grup **Microsoft 365 doğrulamak** için şunları kullanabilirsiniz:
    
    ```PowerShell
    Get-Mailbox -RecipientTypeDetails GroupMailbox -Filter {CustomAttribute15 -eq "Marketing"} -ResultSize Unlimited
    ```

3. Çıkışın uyarlanabilir kapsamınız için beklenen kullanıcılarla veya gruplarla eşleni olduğunu doğrulayın. Yoksa, sorgunuza ve Değerleri Azure AD veya Azure AD için ilgili yöneticiye Exchange.
 
Aramanızı kullanarak sorgu SharePoint için:

1. Genel yönetici hesabı veya yönetici rolüne sahip SharePoint hesabı kullanarak, 'a gidin`https://<your_tenant>.sharepoint.com/search`.

2. KQL sorgunuz belirtmek için arama çubuğunu kullanın.

3. Arama sonuçlarının uyarlanabilir kapsamınız için beklenen site URL'leri ile eş olduğunu doğrulayın. Böyle bir şey yoksa, sorgunuza ve URL'leri ilgili yöneticiye danışın ve SharePoint.

### <a name="configuration-information-for-static-scopes"></a>Statik kapsamlar için yapılandırma bilgileri

Statik kapsamları kullanmayı tercih ettiyseniz, bundan sonra ilkenin seçili konumun tüm örneklerine mi (tüm konum) uygulanıp uygulanmayacakna yoksa belirli örnekleri (belirli eklemeler veya dışlamalar) dahil edip etme mi yoksa hariç tutmaya karar vermeniz gerekir.

#### <a name="a-policy-that-applies-to-entire-locations"></a>Konumların tamamına uygulanan ilke

Varsayılan ayar, Skype Kurumsal konumlar için olan tüm örneklerin, siz bunları dahil olarak belirtmek zorunda kalmadan ilkeye otomatik olarak dahil olmasıdır.

Örneğin, **E-posta** konumu için **Exchange alıcılar**. Bu varsayılan ayarla, var olan tüm kullanıcı posta kutuları ilkeye eklenir ve ilke uygulandıktan sonra oluşturulan tüm yeni posta kutuları ilkeyi otomatik olarak devralacaktır.

#### <a name="a-policy-with-specific-inclusions-or-exclusions"></a>Belirli eklemelerin veya dışlamaların olduğu bir ilke

İsteğe bağlı yapılandırmayı kullanarak bekletme ayarlarınızın kapsamını belirli kullanıcılara, belirli Microsoft 365 gruplarına veya belirli sitelere doğru kullanırsanız, ilke başına dikkat etmek gereken bazı sınırlamalar olduğunu unutmayın. Daha fazla bilgi için bkz. [Bekletme ilkeleri ve bekletme etiketi ilkeleri için sınırlar](retention-limits.md). 

Bekletme ayarlarınızın kapsamını isteğe bağlı yapılandırmada kullanmak için, Bu konumun durumu Açık olduğundan emin olun ve sonra belirli kullanıcıları, kullanıcı gruplarını veya siteleri dahil etmek veya dışarıda Microsoft 365 için bağlantıları kullanın.

> [!WARNING]
> Örnekleri son birini içerecek ve sonra kaldır olacak şekilde yapılandırıyorsanız, yapılandırma konum için **All** olarak geri döner.  İlkeyi kaydetmeden önce bunun sizin için tam olarak doğru yapılandırma olduğundan emin olun.
>
> Örneğin, verileri silmek üzere yapılandırılmış bekletme ilkenize dahil etmek üzere bir SharePoint sitesi belirtirseniz ve sonra da tek siteyi kaldırırsanız, varsayılan olarak tüm SharePoint siteleri verileri kalıcı olarak silen bekletme ilkesine tabi olur. Aynı durum yalnızca e-Exchange alıcılar, OneDrive hesapları, sohbet Teams gibi diğer kullanıcılar için de geçerlidir.
>
> Bu senaryoda, konum için Tüm ayarının bekletme ilkesine tabi tutulmasını istemiyorsanız  konumu kapatın. Alternatif olarak, ilkeden muaf tutulacak örnekleri belirtin.

## <a name="locations"></a>Konumlar

Bekletme ilkelerinde yer alan konumlar, Microsoft 365-posta ve site saklamayı destekleyen Exchange hizmet SharePoint kullanır. İlkeniz için seçimlerinizi yapmak üzere yapılandırma ayrıntılarına ve olası özel durumlara sahip konumlar için aşağıdaki bölümü kullanın.

### <a name="configuration-information-for-exchange-email-and-exchange-public-folders"></a>E-postayı Exchange ortak klasörleri Exchange yapılandırma bilgileri

Varsayılan **Exchange posta konumu**, bekletme ayarlarını bir posta kutusu düzeyinde uygulayarak kullanıcıların e-posta, takvim ve diğer posta kutusu öğeleri için bekletmeyi destekler. Paylaşılan posta kutuları da de kullanılabilir.

Kaynak posta kutuları, Microsoft 365 ve grup posta kutuları bu e-posta Exchange desteklemez. Grup Microsoft 365 kutularını değiştirmek için, bunun **Microsoft 365 Grupları konumunu** seçin. Farklı Exchange, statik bir kapsam için grup posta kutusunun seçili olmasına izin verir ama bekletme ilkesi kaydetmeye denemişseniz, "RemoteGroupMailbox" bu konum için geçerli bir seçim olmadığının hatasını alırsınız.

İlke yapılandırmanıza bağlı olarak, [etkin olmayan posta kutuları](inactive-mailboxes-in-office-365.md) dahil olabilir veya hiç yer almayan posta kutuları:

- Statik ilke kapsamları, varsayılan Tüm alıcılar yapılandırmasını kullanıyor ancak belirli eklemeler  veya dışlamalar için desteklenmiyor olduğunda etkin olmayan [posta kutularını içerir](#a-policy-with-specific-inclusions-or-exclusions). Bununla birlikte, ilke uygulandığı sırada etkin posta kutusu olan bir alıcıyı dahil eder veya hariç ayarlarsanız ve posta kutusu daha sonra devre dışı bırakılırsa, bekletme ayarları uygulanmaya veya dışarıda bırakılır.

- Varsayılan olarak, uyarlanabilir ilke kapsamları, kapsamın sorgusuna geldiğinde etkin olmayan posta kutularını içerir. Gelişmiş sorgu oluşturucusunu ve *IsInactiveMailbox* OPATH özelliğini kullanarak bunları hariç tutabilirsiniz:
    
    ```console
    (IsInactiveMailbox -eq "False")
    ```

Statik bir ilke kapsamı kullanıyorsanız ve eklemek veya dışlamak için alıcıları seçerseniz, dağıtım gruplarını ve e-posta etkin güvenlik gruplarını, tek tek seçmek yerine birden çok alıcı seçmek için verimli bir yol olarak seçebilirsiniz. Bu seçeneği kullanırsanız, sahne gerisinde bu gruplar yapılandırma sırasında gruptaki kullanıcıların posta kutularını seçerek otomatik olarak genişletilir. Daha sonra bu grupların üyeliği değişirse, uyarlanabilir ilke kapsamlarından farklı olarak var olan bekletme ilkeniz otomatik olarak güncelleştirilmez.

Bekletme ayarlarını bekletme ayarları yapılandırıldığında hangi posta kutusu öğelerinin dahil olduğu ve dışarıda bırakıldığında Exchange ayrıntılı bilgi için bkz. Bekletme ve silme işlemiyle [ilgili öğeler.](retention-policies-exchange.md#whats-included-for-retention-and-deletion)

Ortak **Exchange konumu**, bekletme ayarlarını tüm ortak klasörlere uygular ve klasör veya posta kutusu düzeyinde uygulanamaz.

#### <a name="exceptions-for-auto-apply-policies-configured-for-sensitive-information-types"></a>Hassas bilgi türleri için yapılandırılmış otomatik uygulama ilkeleri için özel durumlar

Hassas bilgi türleri kullanan bir otomatik uygulama ilkesi yapılandırsanız ve e-posta **Exchange seçin**:

- Microsoft 365 posta kutuları da dahil edilir.

- Belirli posta kutularını tanımlamak üzere uyarlanabilir bir kapsam yapılandırsanız bile, tüm posta kutuları otomatik olarak eklenir. Statik bir ilke kapsamı seçtiyseniz, dahil etmek veya dışarıda tutmak için alıcıları belirtemezseniz.

### <a name="configuration-information-for-sharepoint-sites-and-onedrive-accounts"></a>Site ve hesap SharePoint yapılandırma OneDrive bilgileri

SharePoint sitelerin konumunu  seçtiğiniz zaman, bekletme ilkesi SharePoint iletişim sitelerinde, Microsoft 365 gruplarıyla bağlantılı olmayan ekip sitelerinde ve klasik sitelerde belgeleri alıkoyarak silebilir. Uyarlanabilir ilke kapsamlarını kullanmadıysanız [, Microsoft 365](#exceptions-for-adaptive-policy-scopes) grupları tarafından bağlanan ekip siteleri bu seçenekte destek desteklemez ve bunun yerine, grubun posta kutusu, site ve dosyalarına uygulanan **Microsoft 365** Grupları konumunu kullanın.

yeni ve otomatik bekletme ayarları yapılandırıldığında nelerin dahil olduğu ve dışarıda bırakıldıkları hakkında ayrıntılı bilgi SharePoint OneDrive bkz. Bekletme ve silme işlemi için [neler dahil edilir](retention-policies-sharepoint.md#whats-included-for-retention-and-deletion)?

Belirli sitelerin veya SharePoint hesaplarının OneDrive belirttiğinizde, sitelere erişim için izinlere ihtiyacınız yok. Statik kapsamlar için, Konumları düzenle sayfasında URL'yi belirttiğiniz sırada **doğrulama yapılmaz** . Bununla birlikte SharePoint tüm sitelerde, yapılandırmanın son sayfasında var olduğu denetlenir. Bu denetim başarısız olursa, girdiğiniz URL için doğrulamanın başarısız olduğunu ve doğrulama denetimi geçinceye kadar bekletme ilkesi oluşturulamaz. Bu iletiyi görüyorsanız, URL'yi değiştirmek veya siteyi bekletme ilkesinden kaldırmak için yapılandırma sürecine geri gidin.

Tek tek hesap OneDrive için bkz[. Tüm kullanıcı kimlik OneDrive listesi elde görme](/onedrive/list-onedrive-urls).

> [!NOTE]
> Tek tek OneDrive hesapları belirtirken, OneDrive hesapları önceden sağlamadıkça[, kullanıcı](/onedrive/pre-provision-accounts) OneDrive hesaplarına ilk kez erişene kadar URL'nin oluşturulmay olacağını unutmayın.
>
> Ayrıca, OneDrive [UPN'sinde](/onedrive/upn-changes) değişiklik varsa URL otomatik olarak değişir. Örneğin, bir kuruluşun yeniden adlandırın veya yeniden yapılandırınması için etki alanı adı değişikliği gibi ad değiştirme olayı. UPN değişirse, bekletme ayarları için OneDrive URL'leri güncelleştirmeniz gerekir.
>
> Tek tek kullanıcıların statik kapsamları dahil etmesini veya dışında tutacaklarını güvenilir bir şekilde belirtmenin güçlükleri [nedeniyle, Kullanıcı](retention.md#adaptive-or-static-policy-scopes-for-retention) kapsamı türüne göre uyarlanabilir kapsamlar bu amaç için daha uygun olur.

#### <a name="exceptions-for-adaptive-policy-scopes"></a>Uyarlanabilir ilke kapsamları için özel durumlar

Uyarlanabilir ilke kapsamlarını kullanan bir bekletme ilkesi yapılandırıyor ve SharePoint **konumu** seçin:

- OneDrive ve Microsoft 365 bağlantılı sitelere ek olarak, SharePoint siteleri, Microsoft 365 grupları ile bağlantılı olmayan ekip siteleri ve klasik siteler dahil edilir.

### <a name="configuration-information-for-microsoft-365-groups"></a>Grup yapılandırma Microsoft 365 bilgileri

Bir grup (eski adı Microsoft 365 grup) için içeriği korumak veya Office 365 için Grup grubunun **Microsoft 365** kullanın. Bekletme ilkeleri için, bu konum grup posta kutusunu ve ekipler SharePoint içerir. Bekletme etiketleri için, bu konum yalnızca SharePoint siteyi içerir.

> [!NOTE]
> Microsoft 365 grubunda Exchange posta kutusu olsa da, **Exchange e-posta** konumu için bekletme ilkesi grup posta kutularına Microsoft 365 içermez.

Statik kapsamlar kullanıyorsanız: Statik kapsam için **Exchange** e-posta konumu başlangıçta dahil edilecek veya hariç tutulacak bir grup posta kutusu belirtmenize izinse de, bekletme ilkesi kaydetmeyi deneerek, "RemoteGroupMailbox" değerinin posta kutusunun konumu için geçerli bir seçim olmadığını belirten bir hata Exchange alırsınız.

Varsayılan olarak, bir Microsoft 365 grubuna Microsoft 365 bekletme ilkesi grup posta kutusunu ve SharePoint sitesini içerir. ekipler sitesinde depolanan SharePoint bu konum kapsamındadır, ancak kendi bekletme ilkesi konumları olan Teams sohbetler veya Teams iletileri göndermez.

Bekletme ilkesi yalnızca Microsoft 365 posta kutularına veya yalnızca bağlantılı SharePoint ekipleri sitelerine uygulanacak olduğundan varsayılanı değiştirmek için [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) PowerShell cmdlet'ini aşağıdaki değerlerden birini kullanarak *Applications* parametresini kullanın:

- `Group:Exchange`yalnızca Microsoft 365 bağlı posta kutuları için.
- `Group:SharePoint`yalnızca SharePoint bağlı siteler için.

Seçili posta kutusu gruplarının hem posta kutusunun hem de SharePoint sitenin varsayılan Microsoft 365 için, belirtin`Group:Exchange,SharePoint`.

#### <a name="exceptions-for-auto-apply-policies-configured-for-sensitive-information-types"></a>Hassas bilgi türleri için yapılandırılmış otomatik uygulama ilkeleri için özel durumlar

Hassas bilgi türleri kullanan bir otomatik uygulama ilkesi yapılandırıldığında ve Gruplarda geçerli **Microsoft 365 seçin**:

- Microsoft 365 posta kutuları dahil değildir. Bu posta kutularını ilkenize eklemek için, bunun yerine **Exchange posta** kutusunu seçin.

#### <a name="what-happens-if-a-microsoft-365-group-is-deleted-after-a-policy-is-applied"></a>İlke uygulandıktan Microsoft 365 grup silinirse ne olur?

Bekletme ilkesi (statik ilke kapsamı veya uyarlanabilir) bir Microsoft 365 grubuna uygulandığında ve bu grup bir başka Azure Active Directory:

- Grup bağlantılı SharePoint sitesi korunur ve bekletme ilkesi tarafından Grup konumunun Microsoft 365 **devam** eder. Siteye, grup silinmeden önce erişmiş olan kişiler için hala erişilebilir ve yeni izinlerin şimdi Tüm Kullanıcılar tarafından SharePoint.
    
    Bu noktada, silinmiş grubu belirtemezseniz, Microsoft 365 Grupları konumunun dışında tutabilirsiniz. Bekletme İlkesini bu siteden bırakmanız gerekirse, Microsoft Desteği'ne başvurun. Örneğin, [Merkezi'nde bir hizmet Microsoft 365 Yönetici açın](https://admin.microsoft.com/Adminportal/Home#/support).

- Silinmiş grubun posta kutusu devre dışı olur ve aynı site SharePoint, bekletme ayarlarına tabi kalır. Daha fazla bilgi için bkz[. Etkin olmayan posta kutuları Exchange Online](inactive-mailboxes-in-office-365.md).

### <a name="configuration-information-for-skype-for-business"></a>İletişim için yapılandırma Skype Kurumsal

> [!NOTE]
> Skype Kurumsal [31 Temmuz 2021'de](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/skype-for-business-online-to-be-retired-in-2021/ba-p/777833) de kaldırıldı ve müşterilerin Microsoft Teams. Bununla birlikte, var olan Skype Kurumsal için bekletme ilkeleri destekmaya devam eder.

Exchange e-postanın aksine, Skype konumunun durumunu tüm kullanıcıları otomatik olarak içerecek şekilde açabilirsiniz, ancak bu konumu açık durumdayken konuşmalarını korumak istediğiniz kullanıcıları kendiniz seçmeniz gerekir:

![Bekletme Skype için konum seçin.](../media/skype-location-retention-policies.png)

Bu Düzenle seçeneğini **kullandıktan** sonra, **Skype Kurumsal** bölmesinde Ad sütunundan önce gizli kutuyu seçerek tüm **kullanıcıları hızla ekleyebilirsiniz**. Bununla birlikte, her kullanıcının ilkeye dahil olan belirli bir kullanıcı sayısı olarak saymak önemlidir. Dolayısıyla, bu kutuyu seçerek 1.000 kullanıcı dahil etmek, dahil etmek üzere 1.000 kullanıcıyla el ile seçilmiş olmasıyla aynıdır. Bu, kullanıcı sayısı için desteklenen en Skype Kurumsal.

konuşma geçmişini **arşivlemeyle hiçbir** ilgisi Outlook Konuşma Geçmişi klasörüdür ve Skype vardır. **Konuşma Geçmişi** son kullanıcı tarafından kapatılabilir, ancak Skype için arşivleme, Skype konuşmalarının bir kopyasını kullanıcının erişilemeyen ancak eBulma tarafından kullanılabilen gizli bir klasörde depolanmasıyla yapılır.

## <a name="settings-for-retaining-and-deleting-content"></a>Ayarlar tutma ve silme hakkında daha fazla bilgi

İçeriği koruma ve silme ayarlarını seçerek, bekletme ilkeniz belirli bir süre için aşağıdaki yapılandırmalardan biri olur:

- Yalnızca koruma

    Bu yapılandırma için Öğeleri belirli **bir süre boyunca alıkoy'a ve** **Bekletme döneminin sonunda: Hiçbir şey yapma'ya seçin**. Ya da Öğeleri sonsuza **kadar koruy'ı seçin**.

- Koruma ve silme

    Bu yapılandırma için Öğeleri belirli **bir süre boyunca alıkoy'a ve** Bekletme döneminin **sonunda: Öğeleri otomatik olarak sil'e tıklayın**.

- Yalnızca silme

    Bu yapılandırma için, Yalnızca **belirli bir yaşa ulaştıklarda öğeleri sil'i seçin**.

### <a name="retaining-content-for-a-specific-period-of-time"></a>İçeriği belirli bir süre tutma

İçeriği korumak üzere bir bekletme etiketi veya ilkesi yapılandırıldığında, öğeleri belirli sayıda gün, ay veya yıl boyunca saklamayı seçersiniz. Alternatif olarak, öğeleri sonsuza kadar koruyabilirsiniz. Bekletme süresi, ilkenin atandığı süreden itibaren hesaplanmaz, ancak belirtilen bekletme döneminin başlangıcına göre hesaplanır.

Bekletme döneminin başlangıcı için, içeriğin ne zaman oluşturulacaklarını veya yalnızca dosyalar ve içeriğin en son ne zaman değiştirildiğinde SharePoint, OneDrive ve Microsoft 365 Grupları için destek olaylarını seçebilirsiniz. Bekletme etiketleri için, bekletme dönemini içeriğin etiketli olduğu ve bir olayın oluştuğu zaman başlatabilirsiniz.

Örnekler:

- SharePoint: Bu içerik en son değiştirildikten sonra site koleksiyonunda bulunan öğeleri yedi yıl süreyle tutmak ve bu site koleksiyonunda bulunan bir belge altı yıl içinde değiştirilmemişse, belge değiştirilmezse yalnızca bir yıl daha korunur. Belge yeniden düzenlenmişse, belgenin yaşı yeni değiştirme tarihine göre hesaplanır ve yedi yıl daha korunur.

- Exchange: Posta kutusunda öğeleri yedi yıl süreyle tutmak ister ve altı yıl önce bir ileti gönderilmişse, ileti yalnızca bir yıl süreyle korunur. Daha Exchange için yaş, gelen e-posta için alınan tarihe veya giden e-posta için gönderme tarihine dayalıdır. Öğelerin en son ne zaman değiştirildiğinden bağlı olarak tutma, yalnızca Site ve OneDrive Site SharePoint.

Bekletme döneminin sonunda, içeriğin kalıcı olarak silinmesini isteyip istemeyebilirsiniz:

![Bekletme ayarları sayfasına gidin.](../media/b05f84e5-fc71-4717-8f7b-d06a29dc4f29.png)

Bekletmeyi yapılandırmadan önce, ilgili iş yükleri için kapasite ve depolama sınırlarını tanımanız gerekir:

- Site SharePoint OneDrive için, saklanan öğeler sitenin depolama kotasına dahil olan Saklama Kitaplığı'nın saklama kitaplığında saklanır. Daha fazla bilgi için bkz[. Site depolama alanı sınırlarını](/sharepoint/manage-site-collection-storage-limits) belgeler SharePoint yönetme.

- Daha Exchange, Teams ve Yammer depolanmış iletilerin posta kutularında depolandığı alan hakkında bilgi için bkz. Exchange Online sınırlarına bakın ve otomatik [](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits) genişleyen [arşivlemeyi etkinleştirin](autoexpanding-archiving.md).
    
    Çok büyük hacimli e-postanın kısa bir süre içinde kullanıcılar tarafından veya ilke ayarlarından otomatik olarak silindiğinde, öğeleri kullanıcının birincil posta kutusunun Kurtarılabilir Öğeler klasöründen arşiv posta kutusunun Kurtarılabilir Öğeler klasörüne daha sık taşımak için Exchange'yi yapılandırmanız da gerekebilir. Adım adım yönergeler için bkz. [Posta kutuları için Kurtarılabilir Öğe kotasını artırma](increase-the-recoverable-quota-for-mailboxes-on-hold.md).

### <a name="deleting-content-thats-older-than-a-specific-age"></a>Belirli bir yaştan daha eski içeriği silme

Bekletme ilkesi öğeleri alıkoydurarak silebilir veya eski öğeleri bekletmeden silebilir.

Her iki durumda da, ilkeniz öğeleri silerse, belirttiğiniz sürenin ilkenin atandığı süreden değil, belirtilen bekletme döneminin başlangıcına göre hesaplanmadığı anlamanız önemlidir. Örneğin, öğenin oluşturulma veya değiştirilme ya da etiketli olduğu zaman.

Bu nedenle, öncelikle mevcut içeriğin yaşını ve ilkenin bu içeriği nasıl etkiley kullanılabilir olduğunu düşünün. Ayrıca, yeni ilkeyi atamadan önce kullanıcılarınıza bu ilkeyi haber vermek ve olası etkiyi değerlendirmek için onlara zaman vermek de istiyor olabilirsiniz.

### <a name="a-policy-that-applies-to-entire-locations"></a>Konumların tamamına uygulanan ilke

Konumları seçerseniz, konumun durumu Skype Kurumsal dışında, varsayılan ayar  **Tüm'tir**.

Bekletme ilkesi konumların tamamının herhangi bir bileşimine uygulandığında, ilkenin dahil olduğu alıcı, site, hesap, grup, vb. sayısında bir sınırlama yoktur.

Örneğin, bir ilke tüm e-Exchange e-postayı ve tüm SharePoint sitelerini içerirse, kaç tane olursa olsun tüm siteler ve alıcılar dahil edilir. Diğer Exchange, ilke uygulandıktan sonra oluşturulan tüm yeni posta kutuları ilkeyi otomatik olarak devralacaktır.

### <a name="a-policy-with-specific-inclusions-or-exclusions"></a>Belirli eklemelerin veya dışlamaların olduğu bir ilke

İsteğe bağlı yapılandırmayı kullanarak bekletme ayarlarınızın kapsamını belirli kullanıcılara, belirli Microsoft 365 gruplarına veya belirli sitelere doğru kullanırsanız, ilke başına dikkat etmek gereken bazı sınırlamalar olduğunu unutmayın. Daha fazla bilgi için bkz. [Bekletme ilkeleri ve bekletme etiketi ilkeleri için sınırlar](retention-limits.md). 

Bekletme ayarlarınızın kapsamını isteğe bağlı yapılandırmada kullanmak için, Bu konumun durumu Açık olduğundan emin olun ve sonra belirli kullanıcıları, kullanıcı gruplarını veya siteleri dahil etmek veya dışarıda Microsoft 365 için bağlantıları kullanın.

> [!WARNING]
> Yapılandırsanız, son yapılandırmayı içerir ve sonra kaldırırsanız, yapılandırma konum için **All** olarak geri döner.  İlkeyi kaydetmeden önce bunun sizin için tam olarak doğru yapılandırma olduğundan emin olun.
>
> Örneğin, verileri silmek üzere yapılandırılmış bekletme ilkenize dahil etmek üzere bir SharePoint sitesi belirtirseniz ve sonra da tek siteyi kaldırırsanız, varsayılan olarak tüm SharePoint siteleri verileri kalıcı olarak silen bekletme ilkesine tabi olur. Aynı durum yalnızca e-posta Exchange, OneDrive sohbet kullanıcıları vb. Teams için de geçerlidir.
>
> Bu senaryoda, konum için Tüm ayarının bekletme ilkesine tabi tutulmasını istemiyorsanız  konumu kapatın. Alternatif olarak, ilkeden muaf olmak için hariç tutulacakları belirtme.

## <a name="updating-policies-for-retention"></a>Bekletme ilkelerini güncelleştirme

Bazı ayarlar, bekletme ilkesi oluşturulduktan ve kaydedildikten sonra değiştirilemez. Bu ayarlar şunlardır:
- Bekletme süresi ve bekletme döneminin ne zaman başlayacağı dışında ilke adı ve bekletme ayarları.

Bir bekletme ilkesi düzenlerseniz ve öğeler zaten bekletme ilkenizin özgün ayarlarına tabi olursa, güncelleştirilmiş ayarlarınız yeni tanımlanan öğelere ek olarak bu öğelere otomatik olarak uygulanır.

Bu güncelleştirme genellikle oldukça hızlıdır, ancak birkaç gün de sürer. Veritabanı konumlar arasında ilke çoğaltması Microsoft 365 tamamlandığında, bekletme ilkesi durumunun On (Beklemede **)** Microsoft 365 uyumluluk merkezi **(Başarılı) olarak değiştir olduğunu görmenizi sağlar**.

## <a name="locking-the-policy-to-prevent-changes"></a>Değişiklikleri önlemek için ilkeyi kilitleme

Hiç kimsenin ilkeyi kapatamaya, ilkeyi silene veya ilkeyi daha az kısıtlayıcı hale döndürene emin olmak için bkz. Bekletme ilkeleri ve bekletme etiketi ilkelerine yönelik değişiklikleri kısıtlamak için Koruma [Kilidi'ne bakın](retention-preservation-lock.md).
