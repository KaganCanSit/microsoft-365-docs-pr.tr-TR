---
title: İçeriği otomatik olarak saklamak veya silmek için bekletme ayarlarını yapılandırma
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
description: İstediğinizi korumak ve istemediğinizden kurtulmak için bekletme ilkesinde veya bekletme etiketi ilkesinde yapılandırabileceğiniz ayarları anlayın.
ms.openlocfilehash: ddfa921c8dae22bbe091e2c0f66fc9ae42aeea41
ms.sourcegitcommit: b16520d8bfe04b29274f7a129d90ef116bb77f69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2022
ms.locfileid: "65231813"
---
# <a name="common-settings-for-retention-policies-and-retention-label-policies"></a>Bekletme ilkeleri ve bekletme etiketi ilkeleri için yaygın ayarlar

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](https://aka.ms/ComplianceSD).*

Bekletme için birçok ayar hem bekletme ilkeleri hem de bekletme etiketi ilkeleri için ortaktır. Bu ayarları içeriği proaktif olarak korumak, içeriği silmek veya her ikisini birden korumak ve sonra silmek üzere yapılandırmanıza yardımcı olması için aşağıdaki bilgileri kullanın.

Bekletme için bu ilkeleri destekleyen senaryolar için bkz:

- [Bekletme ilkeleri oluşturun ve yapılandırın](create-retention-policies.md).
- [Bekletme etiketlerini yayımlama ve uygulamalarda uygulama](create-apply-retention-labels.md)
- [İçeriğe otomatik olarak bekletme etiketi uygulama](apply-retention-labels-automatically.md)

Her senaryoya özgü Ayarlar ilgili belgelerinde açıklanmıştır.

Bekletme ilkeleri ve bekletmenin Microsoft 365 nasıl çalıştığı hakkında genel bakış bilgileri için bkz. [Bekletme ilkeleri ve bekletme etiketleri hakkında bilgi edinin](retention.md).

## <a name="scopes---adaptive-and-static"></a>Kapsamlar - uyarlamalı ve statik

Uyarlamalı ve statik kapsamları bilmiyorsanız ve bekletme için bir ilke yapılandırırken hangisini kullanacağınızı seçmenize yardımcı olmak için bkz. [Bekletme için uyarlamalı veya statik ilke kapsamları](retention.md#adaptive-or-static-policy-scopes-for-retention). 

Uyarlamalı veya statik bir kapsam kullanmaya karar verdiyseniz, yapılandırmanıza yardımcı olması için aşağıdaki bilgileri kullanın:
- [Uyarlamalı kapsamlar için yapılandırma bilgileri](#configuration-information-for-adaptive-scopes)
- [Statik kapsamlar için yapılandırma bilgileri](#configuration-information-for-static-scopes)

> [!TIP]
> Statik kapsamlar kullanan ilkeleriniz varsa ve bunları uyarlamalı kapsamlara dönüştürmek istiyorsanız, aynı bekletme ayarlarına sahip uyarlamalı kapsamlar kullanan yeni ilkeler oluştururken mevcut ilkelerinizi yerinde bırakın. Statik kapsamlara sahip eski ilkeleri devre dışı bırakmadan veya silmeden önce bu yeni ilkelerin doğru kullanıcıları, siteleri ve grupları hedeflediklerini doğrulayın.

### <a name="configuration-information-for-adaptive-scopes"></a>Uyarlamalı kapsamlar için yapılandırma bilgileri

Uyarlamalı kapsamları kullanmayı seçtiğinizde, istediğiniz uyarlamalı kapsam türünü seçmeniz istenir. Uyarlamalı kapsamların üç farklı türü vardır ve her biri farklı öznitelikleri veya özellikleri destekler:

| Uyarlamalı kapsam türü | Desteklenen öznitelikler veya özellikler şunlardır: |
|:-----|:-----|
|**Kullanıcılar** - şunlar için geçerlidir:  <br/> - Exchange e-posta <br/> - OneDrive hesapları <br/> - Teams sohbetleri <br/> - Özel kanal iletilerini Teams <br/> - kullanıcı iletilerini Yammer| Ad <br/> Soyadı    <br/>Görünen ad <br/> İş unvanı <br/> Bölüm <br/> Office <br/>Sokak adresi    <br/> Şehir <br/>Eyalet veya bölge <br/>Posta kodu <br/> Ülke veya bölge <br/> E-posta adresleri <br/> Diğer ad <br/> özel öznitelikleri Exchange: CustomAttribute1 - CustomAttribute15|
|**SharePoint siteler** - şunlar için geçerlidir:  <br/> - SharePoint siteleri <br/> - OneDrive hesapları |Site URL'si <br/>Site adı <br/> SharePoint özel özellikleri: RefinableString00 - RefinableString99 |
|**Microsoft 365 Grupları** - şunlar için geçerlidir:  <br/> - Microsoft 365 Grupları <br/> - Teams kanal iletileri (standart ve paylaşılan) <br/> - topluluk iletilerini Yammer |Name <br/> Görünen ad <br/> Açıklama <br/> E-posta adresleri <br/> Diğer ad <br/> özel öznitelikleri Exchange: CustomAttribute1 - CustomAttribute15 |

Sitelerin özellik adları, site tarafından yönetilen SharePoint özellikleri temel alır. Özel öznitelikler hakkında bilgi için bkz. [Uyarlamalı İlke Kapsamlarıyla Microsoft 365 Elde Tutma Uygulamak için Özel SharePoint Site Özelliklerini Kullanma](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/using-custom-sharepoint-site-properties-to-apply-microsoft-365/ba-p/3133970).

Kullanıcıların ve grupların öznitelik adları, Azure AD öznitelikleriyle [eşlenebilen filtrelenebilir alıcı özelliklerini](/powershell/exchange/recipientfilter-properties#filterable-recipient-properties) temel alır. Örneğin:

- **Diğer ad**, Azure AD yönetim merkezinde **E-posta** olarak görüntülenen **mailNickname** LDAP adıyla eşler.
- **E-posta adresleri**, Azure AD yönetim merkezinde **Proxy adresi** olarak görüntülenen LDAP adı **proxyAddresses ile eşlenir**.

Basit sorgu oluşturucusu kullanılarak uyarlamalı bir kapsam yapılandırdığınızda tabloda listelenen öznitelikler ve özellikler kolayca belirtilebilir. Aşağıdaki bölümde açıklandığı gibi gelişmiş sorgu oluşturucusu ile ek öznitelikler ve özellikler desteklenir.

> [!TIP]
> Gelişmiş sorgu oluşturucusunu kullanma hakkında daha fazla bilgi için aşağıdaki web seminerlerine bakın: 
> - [Uyarlamalı İlke Kapsamları ile Kullanıcılar ve Gruplar için Gelişmiş Sorgular Oluşturma](https://mipc.eventbuilder.com/event/52683/occurrence/49452/recording?rauth=853.3181650.1f2b6e8b4a05b4441f19b890dfeadcec24c4325e90ac492b7a58eb3045c546ea)
> - [Uyarlamalı İlke Kapsamlarıyla SharePoint Siteleri için Gelişmiş Sorgular Oluşturma](https://aka.ms/AdaptivePolicyScopes-AdvancedSharePoint)

Bekletme için tek bir ilkenin bir veya birden çok uyarlamalı kapsamı olabilir.

#### <a name="to-configure-an-adaptive-scope"></a>Uyarlamalı kapsam yapılandırmak için

Uyarlamalı kapsamınızı yapılandırmadan önce, oluşturulacak kapsam türünü ve hangi öznitelikleri ve değerleri kullanacağınızı belirlemek için önceki bölümü kullanın. Bu bilgileri onaylamak için diğer yöneticilerle birlikte çalışmanız gerekebilir. 

Özellikle SharePoint siteler için[, özel site özelliklerini](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/using-custom-sharepoint-site-properties-to-apply-microsoft-365/ba-p/3133970) kullanmayı planlıyorsanız ek SharePoint yapılandırması gerekebilir.

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com/) aşağıdaki konumlardan birine gidin:
    
    - Kayıt yönetimi çözümünü kullanıyorsanız:
        - **Çözümleri** >  **Kayıt yönetimi** >  **Uyarlamalı kapsamlar** sekmesi > + **Kapsam oluştur**
        
    - Veri yaşam döngüsü yönetim çözümünü kullanıyorsanız:
       - **Çözümleri** >  **Veri yaşam döngüsü yönetimi** >  **Uyarlamalı kapsamlar** sekmesi > + **Kapsam oluştur**
    
    Gezinti bölmesinde çözümünüzü hemen görmüyor musunuz? İlk olarak **Tümünü göster'i** seçin. 

2. Önce kapsam türünü seçmek için yapılandırmadaki istemleri izleyin ve ardından dinamik üyeliği oluşturmak için kullanmak istediğiniz öznitelikleri veya özellikleri seçin ve öznitelik veya özellik değerlerini yazın.
    
    Örneğin, Avrupa'daki kullanıcıları tanımlamak için kullanılacak uyarlamalı bir kapsam yapılandırmak için önce kapsam türü olarak **Kullanıcılar'ı** seçin ve ardından **Ülke veya bölge** özniteliğini seçin ve **Avrupa'ya** yazın:
    
    ![Örnek uyarlamalı kapsam yapılandırması.](../media/example-adaptive-scope.png)
    
    Günde bir kez, bu sorgu Azure AD karşı çalıştırılır ve **Ülke veya bölge** özniteliği için hesaplarında **Avrupa** için belirtilen değere sahip tüm kullanıcıları tanımlar.
    
    > [!IMPORTANT]
    > Sorgu hemen çalışmadığından, değere doğru yazdığınız bir doğrulama yoktur.
    
    Sorgu oluşturmak üzere mantıksal işleçlerle birlikte kapsam türleri için desteklenen özniteliklerin veya özelliklerin herhangi bir bileşimini kullanmak için **Öznitelik ekle** (kullanıcılar ve gruplar için) veya **Özellik ekle** (siteler için) seçeneğini belirleyin. Desteklenen işleçler **eşittir**, **eşit değildir**, **ile başlar** ve **ile başlamaz** ve seçili öznitelikleri veya özellikleri gruplandırabilirsiniz. Örneğin:
    
    ![Öznitelik gruplandırmalarıyla örnek uyarlamalı kapsam yapılandırması.](../media/example-adaptive-scope-grouping.png)
    
    Alternatif olarak, gelişmiş **sorgu oluşturucusu'nu** seçerek kendi sorgularınızı belirtebilirsiniz:
    
    - **Kullanıcı** ve **Microsoft 365 Grubu** kapsamları için [OPATH filtreleme söz dizimlerini](/powershell/exchange/recipient-filters) kullanın. Örneğin, üyeliğini departmana, ülkeye ve eyalete göre tanımlayan bir kullanıcı kapsamı oluşturmak için:
    
        ![Gelişmiş sorgu ile örnek uyarlamalı kapsam.](../media/example-adaptive-scope-advanced-query.png)
        
        Bu kapsamlar için gelişmiş sorgu oluşturucu kullanmanın avantajlarından biri, daha geniş bir sorgu işleçleri seçimidir:
        - **ve**
        - **Veya**
        - **Değil**
        - **eq** (eşittir)
        - **ne** (eşit değildir)
        - **lt** (küçüktür)
        - **gt** (büyüktür)
        - **like** (dize karşılaştırması)
        - **notlike** (dize karşılaştırması)
    
    - **SharePoint site** kapsamları için Anahtar Sözcük Sorgu Dili (KQL) kullanın. Dizine alınmış site özelliklerini kullanarak SharePoint aramak için KQL kullanmayı zaten biliyor olabilirsiniz. Bu KQL sorgularını belirtmenize yardımcı olmak için bkz[. Anahtar Sözcük Sorgu Dili (KQL) söz dizimi başvurusu](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference).
        
        Örneğin, SharePoint site kapsamları, grup bağlantılı ve OneDrive siteleri içeren tüm Microsoft 365 SharePoint site türlerini otomatik olarak içerdiğinden, belirli site türlerini dahil etmek veya hariç tutmak için **SiteTemplate** dizinli site özelliğini kullanabilirsiniz. Belirtebileceğiniz şablonlar:
        - `SITEPAGEPUBLISHING` modern iletişim siteleri için
        - `GROUP`gruba bağlı Microsoft 365 siteler için
        - `TEAMCHANNEL`Microsoft Teams özel kanal siteleri için
        - `STS`klasik bir SharePoint ekip sitesi için
        - `SPSPERS`OneDrive siteler için
        
        Bu nedenle, yalnızca modern iletişim sitelerini içeren ve Microsoft 365 bağlı ve OneDrive siteleri dışlayan uyarlamalı bir kapsam oluşturmak için aşağıdaki KQL sorguyu belirtin:
        ````console
        SiteTemplate=SITEPAGEPUBLISHING
        ````
    
    [Bu gelişmiş sorguları](#validating-advanced-queries) kapsam yapılandırmasından bağımsız olarak doğrulayabilirsiniz.
    
    > [!TIP]
    > Etkin olmayan posta kutularını dışlamak istiyorsanız gelişmiş sorgu oluşturucusunu kullanmanız gerekir. Alternatif olarak, yalnızca etkin olmayan posta kutularını hedefle. Bu yapılandırma için *IsInactiveMailbox* OPATH özelliğini kullanın:
    > 
    > - Etkin olmayan posta kutularını dışlamak için sorgunun şunları içerdiğinden emin olun: `(IsInactiveMailbox -eq "False")`
    > - Yalnızca etkin olmayan posta kutularını hedeflemek için şunları belirtin: `(IsInactiveMailbox -eq "True")`

3. İhtiyacınız olan sayıda uyarlamalı kapsam oluşturun. Bekletme için ilkenizi oluştururken bir veya daha fazla uyarlamalı kapsam seçebilirsiniz.

> [!NOTE]
> Sorguların tam olarak doldurulması beş güne kadar sürebilir ve değişiklikler hemen yapılmaz. Bekletme için ilkeye yeni oluşturulan kapsamı eklemeden önce birkaç gün bekleyerek bu gecikmeyi dikkate alırsınız.

Uyarlamalı kapsam için geçerli üyelik ve üyelik değişikliklerini onaylamak için:

1. **Uyarlamalı kapsamlar** sayfasında kapsama çift tıklayın (veya seçin ve Enter tuşuna basın)

2. Açılır öğe **Ayrıntıları** bölmesinde **Kapsam ayrıntıları'nı** seçin. 
    
    Otomatik olarak eklenip eklenmediğini veya kaldırıldığını ve bu üyeliğin tarih ve saatinin değiştirildiği kapsamdaki tüm kullanıcıları, siteleri veya grupları tanımlayan bilgileri gözden geçirin.

> [!TIP]
> Belirli kullanıcılara, sitelere ve Microsoft 365 gruplarına atanmış olan ilkeleri belirlemenize yardımcı olması için ilke [arama](retention.md#policy-lookup) seçeneğini kullanın.

#### <a name="validating-advanced-queries"></a>Gelişmiş sorguları doğrulama

PowerShell'i kullanarak gelişmiş sorguları el ile doğrulayabilir ve arama SharePoint:
- **Kullanıcılar** ve **Microsoft 365 Grupları** kapsam türleri için PowerShell kullanma
- Kapsam türü SharePoint **siteleri için arama SharePoint** kullanın

PowerShell kullanarak sorgu çalıştırmak için:

1. Uygun [Exchange Online Yönetici izinlerine](/powershell/exchange/connect-to-exchange-online-powershell) sahip bir hesap kullanarak [PowerShell'i Exchange Online Bağlan](/powershell/exchange/find-exchange-cmdlet-permissions#use-powershell-to-find-the-permissions-required-to-run-a-cmdlet).

2. Küme ayraçları (`{`,`}`) içine alınmış uyarlamalı kapsam için *-Filter* parametresi ve [OPATH sorgunuzla](/powershell/exchange/filter-properties) [Get-Recipient](/powershell/module/exchange/get-recipient), [Get-Mailbox](/powershell/module/exchange/get-mailbox) veya [Get-User](/powershell/module/exchange/get-user) kullanın. Öznitelik değerleriniz dizeyse, bu değerleri çift veya tek tırnak içine alın.

    Sorgunuz için seçtiğiniz [OPATH özelliği](/powershell/exchange/filter-properties) tarafından hangi cmdlet'in desteklendiğini belirleyerek doğrulama için Get-Mailbox, Get-Recipient veya Get-User kullanılıp kullanılmayacağını belirleyebilirsiniz.

    > [!IMPORTANT]
    > Get-Mailbox *MailUser* alıcı türünü desteklemez, bu nedenle karma bir ortamda şirket içi posta kutuları içeren sorguları doğrulamak için Get-Recipient veya Get-User kullanılmalıdır.

    **Kullanıcı** kapsamını doğrulamak için uygun komutu kullanın:
    - `Get-Mailbox`*with -RecipientTypeDetails UserMailbox,SharedMailbox,RoomMailbox,EquipmentMailbox*
    - `Get-Recipient` with *-RecipientTypeDetails UserMailbox,MailUser,SharedMailbox,RoomMailbox,EquipmentMailbox*
    
    **Microsoft 365 Grubu** kapsamını doğrulamak için şunu kullanın:
    - `Get-Mailbox`*-GroupMailbox* veya `Get-Recipient` *-RecipientTypeDetails GroupMailbox* ile

    Örneğin, **bir Kullanıcı** kapsamını doğrulamak için şunları kullanabilirsiniz:
    
    ````PowerShell
    Get-Recipient -RecipientTypeDetails UserMailbox,MailUser -Filter {Department -eq "Marketing"} -ResultSize Unlimited
    ````
    
    **Microsoft 365 Grubu** kapsamını doğrulamak için şunları kullanabilirsiniz:
    
    ```PowerShell
    Get-Mailbox -RecipientTypeDetails GroupMailbox -Filter {CustomAttribute15 -eq "Marketing"} -ResultSize Unlimited
    ```
    
    > [!TIP]
    > Kullanıcı kapsamını doğrulamak için bu komutları kullandığınızda, döndürülen alıcı sayısı beklenenden yüksekse, bunun nedeni uyarlamalı kapsamlar için geçerli lisansı olmayan kullanıcıları içermesi olabilir. Bu kullanıcılara bekletme ayarları uygulanmaz.
    > 
    > Örneğin, karma bir ortamda, şirket içinde veya Exchange Online Exchange posta kutusu olmayan lisanssız eşitlenmiş kullanıcı hesaplarınız olabilir. Aşağıdaki komutu çalıştırarak bu kullanıcıları tanımlayabilirsiniz: `Get-User -RecipientTypeDetails User`

3. Çıkışın uyarlamalı kapsamınız için beklenen kullanıcı veya gruplara eşleştiğinden emin olun. Aksi takdirde sorgunuzu ve değerleri Azure AD veya Exchange için ilgili yöneticiye danışın.
 
SharePoint arama kullanarak sorgu çalıştırmak için:

1. Genel yönetici hesabı veya SharePoint yönetici rolüne sahip bir hesap kullanarak adresine `https://<your_tenant>.sharepoint.com/search`gidin.

2. KQL sorgunuzu belirtmek için arama çubuğunu kullanın.

3. Arama sonuçlarının uyarlamalı kapsamınız için beklenen site URL'leri ile eşleştiğinden emin olun. Aksi takdirde sorgunuzu ve URL'leri SharePoint için ilgili yöneticiye danışın.

### <a name="configuration-information-for-static-scopes"></a>Statik kapsamlar için yapılandırma bilgileri

Statik kapsamları kullanmayı seçtiğinizde, ilkenin seçili konum (konumun tamamı) için tüm örneklere uygulanıp uygulanmayacağına veya belirli örneklerin (belirli eklemeler veya dışlamalar) dahil edilip edilmeyeceğine karar vermeniz gerekir.

#### <a name="a-policy-that-applies-to-entire-locations"></a>Konumların tamamı için geçerli olan ilke

Skype Kurumsal dışında, varsayılan ayar seçili konumların tüm örneklerinin ilkeye otomatik olarak dahil edilmeleridir ve bunları dahil olarak belirtmeniz gerekmez.

Örneğin, **Exchange e-posta** konumu için **tüm alıcılar**. Bu varsayılan ayarda, ilkeye tüm mevcut kullanıcı posta kutuları eklenir ve ilke uygulandıktan sonra oluşturulan tüm yeni posta kutuları ilkeyi otomatik olarak devralır.

#### <a name="a-policy-with-specific-inclusions-or-exclusions"></a>Belirli eklemeler veya dışlamalar içeren bir ilke

Bekletme ayarlarınızı belirli kullanıcılara, belirli Microsoft 365 gruplarına veya belirli sitelere kapsamak için isteğe bağlı yapılandırmayı kullanırsanız, ilke başına dikkat etmeniz gereken bazı sınırlar olduğunu unutmayın. Daha fazla bilgi için bkz. [Bekletme ilkeleri ve bekletme etiketi ilkeleri için sınırlar](retention-limits.md). 

Bekletme ayarlarınızı kapsamak için isteğe bağlı yapılandırmayı kullanmak için, o konumun **Durumunun** **Açık** olduğundan emin olun ve ardından bağlantıları kullanarak belirli kullanıcıları, Microsoft 365 grupları veya siteleri dahil edin veya hariç tutun.

> [!WARNING]
> Örnekleri son örneği içerecek ve kaldıracak şekilde yapılandırıyorsanız, yapılandırma konum için **Tümü'ne** geri döner.  İlkeyi kaydetmeden önce amaçladığınız yapılandırmanın bu olduğundan emin olun.
>
> Örneğin, verileri silmek üzere yapılandırılmış bekletme ilkenize eklenecek bir SharePoint site belirtir ve ardından tek siteyi kaldırırsanız, varsayılan olarak tüm SharePoint siteler verileri kalıcı olarak silen bekletme ilkesine tabi olur. Aynı durum, Exchange alıcılar, OneDrive hesapları, Teams sohbet kullanıcıları vb. için de geçerlidir.
>
> Bu senaryoda, konumun **Tümü** ayarının bekletme ilkesine tabi olmasını istemiyorsanız konumu kapatın. Alternatif olarak, ilkeden muaf tutulacak dışlama örneklerini belirtin.

## <a name="locations"></a>Konum

Bekletme ilkelerindeki konumlar, Exchange e-posta ve SharePoint siteleri gibi bekletme ayarlarını destekleyen belirli Microsoft 365 hizmetlerini tanımlar. İlkeniz için seçerken bilmeniz gereken yapılandırma ayrıntıları ve olası özel durumlara sahip konumlar için aşağıdaki bölümü kullanın.

### <a name="configuration-information-for-exchange-email-and-exchange-public-folders"></a>Exchange e-posta ve Exchange ortak klasörler için yapılandırma bilgileri

**Hem Exchange e-posta** konumu hem de **Exchange ortak klasörler** konumu, bekletme ayarları uygulanmadan önce posta kutularının en az 10 MB veriye sahip olmasını gerektirir.

**Exchange e-posta** konumu, bir posta kutusu düzeyinde bekletme ayarları uygulayarak kullanıcıların e-posta, takvim ve diğer posta kutusu öğeleri için bekletmeyi destekler. Donanım ve odalar için paylaşılan posta kutuları ve kaynak posta kutuları da desteklenir.

E-posta kişileri ve Microsoft 365 grup posta kutuları Exchange e-posta için desteklenmez. Microsoft 365 grup posta kutuları için bunun yerine **Microsoft 365 Grupları** konumu seçin. Exchange konumu başlangıçta statik kapsam için bir grup posta kutusunun seçilmesine izin veriyor olsa da, bekletme ilkesini kaydetmeye çalıştığınızda "RemoteGroupMailbox" bu konum için geçerli bir seçim değil hatasını alıyorsunuz.

İlke yapılandırmanıza bağlı olarak [, etkin olmayan posta kutuları](inactive-mailboxes-in-office-365.md) dahil edilebilir veya eklenmeyebilir:

- Statik ilke kapsamları, varsayılan **Tüm alıcılar** yapılandırmasını kullandığınızda etkin olmayan posta kutularını içerir, ancak [belirli eklemeler veya dışlamalar](#a-policy-with-specific-inclusions-or-exclusions) için desteklenmez. Ancak, ilke uygulandığı sırada etkin posta kutusu olan bir alıcıyı dahil ederseniz veya dışlarsanız ve posta kutusu daha sonra devre dışı kalırsa, bekletme ayarları uygulanmaya veya dışlamaya devam eder.

- Uyarlamalı ilke kapsamları varsayılan olarak, kapsamın sorgusunu karşıladığında etkin olmayan posta kutularını içerir. Gelişmiş sorgu oluşturucusunu ve *IsInactiveMailbox* OPATH özelliğini kullanarak bunları dışlayabilirsiniz:
    
    ```console
    (IsInactiveMailbox -eq "False")
    ```

Statik bir ilke kapsamı kullanır ve dahil etmek veya dışlamak için alıcıları seçerseniz, dağıtım gruplarını ve e-posta etkin güvenlik gruplarını tek tek seçmek yerine birden çok alıcıyı seçmenin verimli bir yolu olarak seçebilirsiniz. Bu seçeneği kullandığınızda, arka planda bu gruplar, gruptaki kullanıcıların posta kutularını seçmek için yapılandırma sırasında otomatik olarak genişletilir. Bu grupların üyeliği daha sonra değişirse, uyarlamalı ilke kapsamlarından farklı olarak mevcut bekletme ilkeniz otomatik olarak güncelleştirilmez.

Exchange için bekletme ayarlarını yapılandırırken dahil edilen ve dışlanan posta kutusu öğeleri hakkında ayrıntılı bilgi için bkz. [Bekletme ve silme için eklenenler](retention-policies-exchange.md#whats-included-for-retention-and-deletion).

**ortak klasörlerin Exchange** konumu tüm ortak klasörlere bekletme ayarları uygular ve klasör veya posta kutusu düzeyinde uygulanamaz.

#### <a name="exceptions-for-auto-apply-policies-configured-for-sensitive-information-types"></a>Hassas bilgi türleri için yapılandırılmış otomatik uygulama ilkeleri için özel durumlar

Hassas bilgi türlerini kullanan bir otomatik uygulama ilkesi yapılandırdığınızda ve **Exchange e-posta** konumunu seçtiğinizde:

- Microsoft 365 grup posta kutuları dahil edilir.

- Belirli posta kutularını tanımlamak için uyarlamalı bir kapsam yapılandırsanız bile tüm posta kutuları otomatik olarak eklenir. Statik bir ilke kapsamı seçtiyseniz, dahil edilecek veya dışlanacak alıcıları belirtemezsiniz.

### <a name="configuration-information-for-sharepoint-sites-and-onedrive-accounts"></a>SharePoint siteleri ve OneDrive hesapları için yapılandırma bilgileri

**SharePoint sitelerin** konumunu seçtiğinizde, bekletme ilkesi SharePoint iletişim sitelerindeki, Microsoft 365 grupları tarafından bağlı olmayan ekip sitelerindeki ve klasik sitelerdeki belgeleri koruyabilir ve silebilir. [Uyarlamalı ilke kapsamları](#exceptions-for-adaptive-policy-scopes) kullanmıyorsanız, Microsoft 365 grupları tarafından bağlanan ekip siteleri bu seçenekte desteklenmez ve bunun yerine grubun posta kutusu, sitesi ve dosyalarındaki içerik için geçerli **olan Microsoft 365 Grupları** konumunu kullanın.

SharePoint ve OneDrive için bekletme ayarlarını yapılandırırken dahil edilen ve dışlananlar hakkında ayrıntılı bilgi için bkz. [Bekletme ve silme için eklenenler](retention-policies-sharepoint.md#whats-included-for-retention-and-deletion).

SharePoint siteler veya OneDrive hesapları için konumlarınızı belirttiğinizde, sitelere erişmek için izinlere ihtiyacınız yoktur. Statik kapsamlar için, **KONUMları düzenle** sayfasında URL'yi belirttiğiniz sırada doğrulama yapılmaz. Ancak, belirttiğiniz SharePoint sitelerin yapılandırmanın son sayfasında mevcut olup olmadığını kontrol eder. Bu denetim başarısız olursa, girdiğiniz URL için doğrulamanın başarısız olduğunu ve doğrulama denetimi geçene kadar bekletme ilkesinin oluşturulamadığını belirten bir ileti görürsünüz. Bu iletiyi görürseniz URL'yi değiştirmek veya siteyi bekletme ilkesinden kaldırmak için yapılandırma işlemine geri dönün.

Tek tek OneDrive hesapları belirtmek için bkz. [Kuruluşunuzdaki tüm kullanıcı OneDrive URL'lerinin listesini alma](/onedrive/list-onedrive-urls).

> [!NOTE]
> Tek tek OneDrive hesapları belirttiğinizde, OneDrive hesapları [önceden sağlanmadığı](/onedrive/pre-provision-accounts) sürece, kullanıcı OneDrive ilk kez erişene kadar URL'nin oluşturulmadığını unutmayın.
>
> Ayrıca, kullanıcının UPN'sinde bir değişiklik olduğunda OneDrive [URL'si otomatik olarak değişir](/onedrive/upn-changes). Örneğin, evlilik gibi bir ad değiştirme olayı veya bir kuruluşun yeniden adlandırmasını veya iş yeniden yapılandırılmasını desteklemek için etki alanı adı değişikliği. UPN değişirse, bekletme ayarları için belirttiğiniz OneDrive URL'lerini güncelleştirmeniz gerekir.
>
> Tek tek kullanıcıların statik kapsamları dahil etmek veya dışlamak için URL'leri güvenilir bir şekilde belirtme zorlukları nedeniyle, **Kullanıcı** kapsam türüne sahip [uyarlamalı kapsamlar](retention.md#adaptive-or-static-policy-scopes-for-retention) bu amaç için daha uygundur.

#### <a name="exceptions-for-adaptive-policy-scopes"></a>Uyarlamalı ilke kapsamları için özel durumlar

Uyarlamalı ilke kapsamları kullanan bir ilkeyi bekletme için yapılandırdığınızda ve **sitelerin SharePoint** konumunu seçtiğinizde:

- OneDrive siteler ve Microsoft 365 grup bağlantılı siteler, SharePoint iletişim sitelerine, Microsoft 365 grupları tarafından bağlı olmayan ekip sitelerine ve klasik sitelere ek olarak eklenir.

### <a name="configuration-information-for-microsoft-365-groups"></a>Microsoft 365 Grupları için yapılandırma bilgileri

bir Microsoft 365 grubunun (eski adıyla Office 365 grubu) içeriğini korumak veya silmek için **Microsoft 365 Grupları** konumunu kullanın. Bekletme ilkeleri için bu konum grup posta kutusunu ve SharePoint ekip sitesini içerir. Bekletme etiketleri için bu konum yalnızca SharePoint ekip sitesini içerir.

Bu ilke konumuyla hedeflediğiniz posta kutularına bekletme ayarları uygulanmadan önce en az 10 MB veri gerekir.

> [!NOTE]
> bir Microsoft 365 grubunun Exchange posta kutusu olsa da, **Exchange e-posta** konumu için bekletme ilkesi Microsoft 365 grup posta kutularına içerik içermez.

Statik kapsamlar kullanıyorsanız: Statik kapsamın **Exchange e-posta** konumu başlangıçta dahil edilecek veya hariç tutulacak bir grup posta kutusu belirtmenize olanak tanısa da, bekletme ilkesini kaydetmeye çalıştığınızda "RemoteGroupMailbox" öğesinin Exchange konumu için geçerli bir seçim olmadığını belirten bir hata görürsünüz.

Varsayılan olarak, bir Microsoft 365 grubuna uygulanan bekletme ilkesi grup posta kutusunu ve SharePoint ekip sitesini içerir. SharePoint ekipler sitesinde depolanan dosyalar bu konumla kapsanmaktadır ancak kendi bekletme ilkesi konumlarına sahip Teams sohbetleri veya Teams kanal iletilerini kapsamaz.

Bekletme ilkesinin yalnızca Microsoft 365 posta kutularına veya yalnızca bağlı SharePoint ekip sitelerine uygulanmasını istediğiniz için varsayılanı değiştirmek için [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) PowerShell cmdlet'ini ve *Uygulamalar* parametresini aşağıdaki değerlerden biriyle kullanın:

- `Group:Exchange`yalnızca gruba bağlı Microsoft 365 posta kutuları için.
- `Group:SharePoint`yalnızca gruba bağlı SharePoint siteler için.

Seçili Microsoft 365 grupları için hem posta kutusunun hem de SharePoint sitesinin varsayılan değerine dönmek için belirtin`Group:Exchange,SharePoint`.

#### <a name="exceptions-for-auto-apply-policies-configured-for-sensitive-information-types"></a>Hassas bilgi türleri için yapılandırılmış otomatik uygulama ilkeleri için özel durumlar

Hassas bilgi türlerini kullanan bir otomatik uygulama ilkesi yapılandırdığınızda ve **Microsoft 365 Grupları** konumunu seçtiğinizde:

- Microsoft 365 grup posta kutuları dahil değildir. Bu posta kutularını ilkenize eklemek için bunun yerine **Exchange e-posta** konumunu seçin.

#### <a name="what-happens-if-a-microsoft-365-group-is-deleted-after-a-policy-is-applied"></a>İlke uygulandıktan sonra bir Microsoft 365 grubu silinirse ne olur?

Bekletme ilkesi (statik ilke kapsamı veya uyarlamalı) bir Microsoft 365 grubuna uygulandığında ve bu grup Azure Active Directory silindiğinde:

- Grup bağlantılı SharePoint sitesi korunur ve **Microsoft 365 Grupları** konumuyla bekletme ilkesi tarafından yönetilmeye devam eder. Site, grup silinmeden önce siteye erişimi olan kişiler tarafından hala erişilebilir durumdadır ve yeni izinler artık SharePoint aracılığıyla yönetilmelidir.
    
    Bu noktada, silinen grubu belirtemediğinizden siteyi Microsoft 365 Grupları konumundan dışlayamazsınız. Bekletme ilkesini bu siteden serbest bırakmanız gerekiyorsa Microsoft Desteği başvurun. Örneğin, [Microsoft 365 Yönetici Merkezi'nde bir destek isteği açın](/microsoft-365/admin/get-help-support#online-support).

- Silinen grubun posta kutusu etkin değil olur ve SharePoint site gibi saklama ayarlarına tabidir. Daha fazla bilgi için bkz. [Exchange Online'da etkin olmayan posta kutuları](inactive-mailboxes-in-office-365.md).

### <a name="configuration-information-for-skype-for-business"></a>Skype Kurumsal için yapılandırma bilgileri

> [!NOTE]
> Skype Kurumsal [31 Temmuz 2021'de kullanımdan kaldırıldı](https://techcommunity.microsoft.com/t5/microsoft-teams-blog/skype-for-business-online-to-be-retired-in-2021/ba-p/777833) ve müşterilerin Microsoft Teams geçişlerini öneririz. Ancak, Skype Kurumsal için bekletme ilkeleri mevcut müşteriler için desteklenmeye devam eder.

Exchange e-postadan farklı olarak, tüm kullanıcıları otomatik olarak dahil etmek için Skype konumunun durumunu değiştiremezsiniz, ancak bu konumu açtığınızda konuşmalarını tutmak istediğiniz kullanıcıları el ile seçmeniz gerekir:

![Bekletme ilkeleri için Skype konumu seçin.](../media/skype-location-retention-policies.png)

Bu **Düzenle** seçeneğini seçtikten sonra **, Skype Kurumsal** bölmesinde **, Ad** sütunundan önceki gizli kutuyu seçerek tüm kullanıcıları hızla ekleyebilirsiniz. Ancak, her kullanıcının ilkeye belirli bir ekleme olarak sayıldığını anlamak önemlidir. Bu nedenle, bu kutuyu seçerek 1.000 kullanıcı eklerseniz, dahil etmek üzere 1.000 kullanıcıyı el ile seçmiş olmanızla aynıdır. Bu, Skype Kurumsal için desteklenen en yüksek değerdir.

Outlook'daki bir klasör olan **Konuşma Geçmişi'nin** Skype arşivlemeyle ilgisi olmayan bir özellik olduğunu unutmayın. **Konuşma Geçmişi** son kullanıcı tarafından kapatılabilir, ancak Skype için arşivleme, Skype konuşmalarının bir kopyasını kullanıcının erişemeyeceği ancak eBulma'nın kullanabileceği gizli bir klasörde depolayarak yapılır.

## <a name="settings-for-retaining-and-deleting-content"></a>İçeriği saklamak ve silmek için Ayarlar

İçeriği saklama ve silme ayarlarını seçerek bekletme ilkeniz belirli bir süre için aşağıdaki yapılandırmalardan birine sahip olur:

- Yalnızca saklama
    
    Bu yapılandırma için aşağıdaki seçenekleri belirleyin:
    
    - Bekletme ilkeleri için: **İçeriği korumak mı, silmek mi yoksa her ikisini birden mi yapmak istediğinize karar verin** sayfasında **Öğeleri belirli bir süre için tut'u** seçin, bekletme süresini belirtin ve **bekletme süresinin sonunda bekletme ayarlarının** kaldırılması için **Hiçbir şey yapma'yı** seçin.  Veya bitiş tarihi olmadan saklamak için Bu sayfada **öğeleri sonsuza kadar koru'ya** da tıklayabilirsiniz.
    
    - Bekletme etiketleri için: **Etiket ayarlarını tanımla sayfasında** **Öğeleri süresiz olarak veya belirli bir süre boyunca tut'u** seçin ve sonra:
        - Bekletme ayarlarının belirli bir süre sonra etiketlenmiş içerikte artık geçerli olmaması için: **Bekletme süresini tanımla** sayfasında, **Öğeleri saklama için** zaman aralığını belirtin. Ardından **Bekletme süresinden sonra ne olacağını seçin** sayfasında **Bekletme ayarlarını devre dışı bırak'ı** seçin. Etiket içerikte kalır ancak herhangi bir kısıtlama olmadan yalnızca [sınıflandırır](retention.md#classifying-content-without-applying-any-actions).
        - Bitiş tarihi olmadan saklamak için: **Bekletme dönemini tanımla** sayfasında **, Öğeleri saklama için** **Süresiz bir dönem'i** seçin. Etiket [, mevcut kısıtlamalarla](records-management.md#compare-restrictions-for-what-actions-are-allowed-or-blocked ) birlikte içerikte kalır.

- Saklama ve silme

    Bu yapılandırma için aşağıdaki seçenekleri belirleyin:
    
    - Bekletme ilkeleri için: **İçeriği korumak mı, silmek mi yoksa her ikisini birden mi yapmak istediğinize karar verin** sayfasında **Öğeleri belirli bir süre için tut'u** seçin, bekletme süresini belirtin ve **bekletme süresinin sonunda** **Öğeleri otomatik olarak sil'i** seçin.
    
    - Bekletme etiketleri için: **Etiket ayarlarını tanımla** sayfasında **Öğeleri süresiz olarak veya belirli bir süre boyunca tut'u** seçin, bekletme süresini belirtin ve ardından **Bekletme döneminden sonra ne olacağını seçin** için **Öğeleri otomatik olarak sil'i** veya **Değerlendirmeyi başlat'ı** seçin. Değerlendirme gözden geçirmeleri hakkında daha fazla bilgi için bkz [. Disposition gözden geçirmesi](disposition.md#disposition-reviews).

- Yalnızca sil

    Bu yapılandırma için aşağıdaki seçenekleri belirleyin:
    
    - Bekletme ilkeleri için: **İçeriği korumak mı, silmek mi yoksa her ikisini birden mi yapmak istediğinize karar verin** sayfasında **Yalnızca belirli bir yaşa ulaşan öğeleri sil'i** seçin ve zaman aralığını belirtin.
    
    - Bekletme etiketleri için: **Etiket ayarlarını tanımla** sayfasında **Belirli bir dönemden sonra eylemleri zorla'yı** seçin ve saklama süresi olarak da adlandırılan süreyi belirtin. Dönem otomatik olarak Öğeleri otomatik olarak **sil** olarak **ayarlandıktan sonra ne olacağını seçin** seçeneği.

### <a name="retaining-content-for-a-specific-period-of-time"></a>İçeriği belirli bir süre boyunca saklama

İçeriği korumak için bir bekletme etiketi veya ilkesi yapılandırdığınızda, öğeleri belirli sayıda gün, ay (bir ay için 30 gün varsayılır) veya yıllar için saklamayı seçersiniz. Alternatif olarak, öğeleri sonsuza kadar tutun. Bekletme süresi, ilkenin atandığı zamandan değil, belirtilen saklama süresinin başlangıcına göre hesaplanır.

Saklama süresinin başlangıcı için içeriğin ne zaman oluşturulduğunu veya yalnızca dosyalar ve SharePoint, OneDrive ve Microsoft 365 Grupları için desteklenip desteklenmediğini ve içeriğin en son ne zaman değiştirildiğini seçebilirsiniz. Bekletme etiketleri için, içerik etiketlendiğinden ve bir olay gerçekleştiğinde bekletme süresini başlatabilirsiniz.

Örnekler:

- SharePoint: Bu içerik son değiştirildikten sonra bir site koleksiyonundaki öğeleri yedi yıl boyunca saklamak istiyorsanız ve bu site koleksiyonundaki bir belge altı yıl içinde değiştirilmediyse, belge değiştirilmezse yalnızca bir yıl daha saklanır. Belge yeniden düzenlenirse, belgenin yaşı yeni son değiştirme tarihinden hesaplanır ve yedi yıl daha saklanır.

- Exchange: Öğeleri yedi yıl boyunca posta kutusunda tutmak istiyorsanız ve altı yıl önce bir ileti gönderildiyse, ileti yalnızca bir yıl boyunca saklanır. Exchange öğeler için yaş, gelen e-posta için alınan tarihi veya giden e-posta için gönderilen tarihi temel alır. Öğeleri en son ne zaman değiştirildiğine göre saklamak yalnızca OneDrive ve SharePoint site içeriğine uygulanır.

Saklama süresinin sonunda, içeriğin kalıcı olarak silinmesini isteyip istemediğinizi seçersiniz. Örneğin, bekletme ilkeleri için:

![Bekletme ayarları sayfası.](../media/b05f84e5-fc71-4717-8f7b-d06a29dc4f29.png)

Bekletmeyi yapılandırmadan önce, önce ilgili iş yükleri için kapasite ve depolama sınırları hakkında bilgi edinin:

- SharePoint ve OneDrive için, korunan öğeler sitenin depolama kotasında yer alan Koruma Saklama kitaplığında depolanır. Daha fazla bilgi için SharePoint belgelerinde [site depolama sınırlarını yönetme](/sharepoint/manage-site-collection-storage-limits) bölümüne bakın.

- Tutulan iletilerin posta kutularında depolandığı Exchange, Teams ve Yammer için bkz. [Exchange Online sınırları](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits) ve [otomatik genişletme arşivlemeyi](autoexpanding-archiving.md) etkinleştirme.
    
    Kullanıcılar tarafından veya ilke ayarlarından otomatik olarak kısa bir süre içinde yüksek miktarda e-postanın silindiği aşırı durumlarda, Exchange kullanıcının birincil posta kutusunda bulunan Kurtarılabilir Öğeler klasöründeki öğeleri arşiv posta kutusunda kurtarılabilir öğeler klasörüne daha sık taşımak için de yapılandırmanız gerekebilir. Adım adım yönergeler için bkz. [Bekleyen posta kutuları için Kurtarılabilir Öğeler kotasını artırma](increase-the-recoverable-quota-for-mailboxes-on-hold.md).

### <a name="deleting-content-thats-older-than-a-specific-age"></a>Belirli bir yaştan eski içeriği silme

Bekletme ayarları öğeleri koruyup silebilir veya eski öğeleri saklamadan silebilir.

Her iki durumda da bekletme ayarlarınız öğeleri silerse, belirttiğiniz zaman aralığının ilkenin atandığı zamandan değil, belirtilen saklama süresinin başlangıcına göre hesaplanmadığını anlamanız önemlidir. Örneğin, öğenin oluşturulduğu, değiştirildiği veya etiketlendiği zamandan itibaren.

Bu nedenle, önce mevcut içeriğin yaşını ve ayarların bu içeriği nasıl etkileyebileceklerini göz önünde bulundurun. Ayarlar içeriğe uygulanmadan önce, seçtiğiniz ayarları kullanıcılarınıza ve yardım masasına iletmeyi göz önünde bulundurun ve bu da onlara olası etkiyi değerlendirmek için zaman verir.

### <a name="a-policy-that-applies-to-entire-locations"></a>Konumların tamamı için geçerli olan ilke

Konumları seçtiğinizde( Skype Kurumsal hariç), konumun durumu **Açık** olduğunda varsayılan ayar **Tümü'dür**.

Bekletme ilkesi tüm konumların herhangi bir birleşimine uygulandığında, ilkenin içerebileceği alıcı, site, hesap, grup vb. sayısıyla ilgili bir sınır yoktur.

Örneğin, bir ilke tüm Exchange e-postayı ve tüm SharePoint sitelerini içeriyorsa, kaç tane olursa olsun tüm siteler ve alıcılar dahil olur. Exchange için, ilke uygulandıktan sonra oluşturulan tüm yeni posta kutuları ilkeyi otomatik olarak devralır.

### <a name="a-policy-with-specific-inclusions-or-exclusions"></a>Belirli eklemeler veya dışlamalar içeren bir ilke

Bekletme ayarlarınızı belirli kullanıcılara, belirli Microsoft 365 gruplarına veya belirli sitelere kapsamak için isteğe bağlı yapılandırmayı kullanırsanız, ilke başına dikkat etmeniz gereken bazı sınırlar olduğunu unutmayın. Daha fazla bilgi için bkz. [Bekletme ilkeleri ve bekletme etiketi ilkeleri için sınırlar](retention-limits.md). 

Bekletme ayarlarınızı kapsamak için isteğe bağlı yapılandırmayı kullanmak için, o konumun **Durumunun** **Açık** olduğundan emin olun ve ardından bağlantıları kullanarak belirli kullanıcıları, Microsoft 365 grupları veya siteleri dahil edin veya hariç tutun.

> [!WARNING]
> Eklemeleri yapılandırıp sonuncuyu kaldırırsanız, yapılandırma konum için **Tümü'ne** geri döner.  İlkeyi kaydetmeden önce amaçladığınız yapılandırmanın bu olduğundan emin olun.
>
> Örneğin, verileri silmek üzere yapılandırılmış bekletme ilkenize eklenecek bir SharePoint site belirtir ve ardından tek siteyi kaldırırsanız, varsayılan olarak tüm SharePoint siteler verileri kalıcı olarak silen bekletme ilkesine tabi olur. Aynı durum, Exchange alıcılar, OneDrive hesapları, Teams sohbet kullanıcıları vb. için de geçerlidir.
>
> Bu senaryoda, konumun **Tümü** ayarının bekletme ilkesine tabi olmasını istemiyorsanız konumu kapatın. Alternatif olarak, ilkeden muaf tutulacak dışlamaları belirtin.

## <a name="updating-policies-for-retention"></a>Bekletme için ilkeleri güncelleştirme

Bekletme ilkesi oluşturulduktan ve kaydedildikten sonra bazı ayarlar değiştirilemez ve bunlar şunlardır:
- İlke adı ve bekletme süresi ve saklama süresinin ne zaman başlatılıp başlatılmayacakları hariç tutma ayarları.

Bir bekletme ilkesini düzenlerseniz ve öğeler zaten bekletme ilkenizdeki özgün ayarlara tabiyse, güncelleştirilmiş ayarlarınız yeni tanımlanan öğelere ek olarak bu öğelere otomatik olarak uygulanır.

Genellikle bu güncelleştirme oldukça hızlıdır ancak birkaç gün sürebilir. Microsoft 365 konumlarınız arasında ilke çoğaltması tamamlandığında, Microsoft Purview uyumluluk portalında bekletme ilkesinin durumunu Açık **(Beklemede)** yerine **Açık (Başarılı)** olarak değiştirirsiniz.

## <a name="locking-the-policy-to-prevent-changes"></a>Değişiklikleri önlemek için ilkeyi kilitleme

Kimsenin ilkeyi kapatamadığını, ilkeyi silemediğini veya daha az kısıtlayıcı hale getiremediğini güvence altına almanız gerekiyorsa bkz [. Bekletme ilkeleri ve bekletme etiketi ilkelerindeki değişiklikleri kısıtlamak için Koruma Kilidi'ni kullanma](retention-preservation-lock.md).
