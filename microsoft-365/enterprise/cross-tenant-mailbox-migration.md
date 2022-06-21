---
title: Kiracılar arası posta kutusu geçişi
description: Posta kutularını Microsoft 365 veya Office 365 kiracılar arasında taşıma.
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.prod: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.date: 06/20/2022
ms.reviewer: georgiah
ms.custom:
- it-pro
- admindeeplinkMAC
- admindeeplinkEXCHANGE
ms.collection:
- M365-subscription-management
ms.openlocfilehash: fc0c9186f506cdead968668959c401517551a4d3
ms.sourcegitcommit: af2b570e76e074bbef98b665b5f9a731350eda58
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2022
ms.locfileid: "66185401"
---
# <a name="cross-tenant-mailbox-migration-preview"></a>Kiracılar arası posta kutusu geçişi (önizleme)

Genellikle, birleştirmeler veya bakışlar sırasında, kullanıcınızın Exchange Online posta kutusunu yeni bir kiracıya taşıyabilmeniz gerekir. Kiracılar arası posta kutusu geçişi, kiracı yöneticilerinin kullanıcıları yeni kuruluşlarına geçiş yapmak için Exchange Online PowerShell ve MRS gibi iyi bilinen arabirimleri kullanmasına olanak tanır.

Yöneticiler, kiracılar arası taşımaları yürütmek için _Posta Kutularını Taşı_ yönetim rolü aracılığıyla sağlanan **New-MigrationBatch** cmdlet'ini kullanabilir.

Geçiş yapılan kullanıcılar hedef kiracı Exchange Online sisteminde PostaKullanıçları olarak bulunmalıdır ve kiracılar arası taşımaları etkinleştirmek için belirli özniteliklerle işaretlenmelidir. Sistem, hedef kiracıda düzgün ayarlanmayan kullanıcılar için taşımalarda başarısız olur.

Taşımalar tamamlandığında, kaynak kullanıcı posta kutusu MailUser'a dönüştürülür ve targetAddress (Exchange'de ExternalEmailAddress olarak gösterilir) hedef kiracıya yönlendirme adresiyle damgalanır. Bu işlem, eski MailUser'ı kaynak kiracıda bırakır ve birlikte bulunmaya ve posta yönlendirmeye olanak tanır. İş süreçleri izin verildiğinde, kaynak kiracı kaynak MailUser'ı kaldırabilir veya bir posta kişisine dönüştürebilir.

Kiracılar arası Exchange posta kutusu geçişleri yalnızca karma veya buluttaki kiracılar için ya da ikisinin herhangi bir birleşimi için desteklenir.

Bu makalede, kiracılar arası posta kutusu taşıma işlemi açıklanır ve Exchange Online posta kutusu içeriği taşımaları için kaynak ve hedef kiracıların nasıl hazırlandığına ilişkin yönergeler sağlanır.

   > [!NOTE]
   > Kısa süre önce, kiracılar arası posta kutusu geçişine artık Azure Key Vault gerektiremeyecek şekilde kurulum adımlarımızı güncelleştirdik! Bu önizlemeye ilk kez ekleniyorsanız herhangi bir işlem yapmanız gerekmez ve devam edip bu belgede ayrıntılarıyla gösterilen adımları izleyebilirsiniz. Kiracılarınızı önceki AKV yöntemini kullanarak yapılandırmaya başladıysanız, bu yeni yöntemi kullanmaya başlamak için bu yapılandırmayı durdurmanızı veya kaldırmanızı kesinlikle öneririz. Önceki AKV yöntemiyle devam eden posta kutusu geçişleriniz varsa, mevcut geçişlerinizin tamamlanmasını bekleyin ve yeni basitleştirilmiş yöntemi etkinleştirmek için aşağıdaki adımları izleyin. Azure Key Vault gerekli kurulum adımları arşivlenir ancak başvuru için **[burada](https://github.com/microsoft/cross-tenant/wiki/V1-Content#cross-tenant-mailbox-migration-preview)** bulunabilir.

## <a name="preparing-source-and-target-tenants"></a>Kaynak ve hedef kiracıları hazırlama

### <a name="prerequisites-for-source-and-target-tenants"></a>Kaynak ve hedef kiracılar için önkoşullar

Başlamadan önce, Azure'da Posta Kutusunu Taşı uygulamasını, EXO Geçiş Uç Noktasını ve EXO Kuruluş İlişkisini yapılandırmak için gerekli izinlere sahip olduğunuzdan emin olun.

Ayrıca, kaynak kiracıda en az bir posta etkin güvenlik grubu gereklidir. Bu gruplar, kaynak kiracıdan (veya bazen kaynak olarak da adlandırılır) hedef kiracıya taşınabilen posta kutularının listesinin kapsamını bulmak için kullanılır. Bu, kaynak kiracı yöneticisinin taşınması gereken belirli posta kutusu kümesini kısıtlamasına veya kapsamını belirlemesine olanak tanır ve istenmeyen kullanıcıların geçirilmesini önler. İç içe gruplar desteklenmez.

Ayrıca, Microsoft 365 kiracı kimliğini almak için güvenilir iş ortağı şirketinizle (posta kutularını taşıyacağınız şirketle) iletişim kurmanız gerekir. Bu kiracı kimliği, Kuruluş İlişkisi Etki AlanıAdı alanında kullanılır.

Aboneliğin kiracı kimliğini almak için [Microsoft 365 yönetim merkezi](https://go.microsoft.com/fwlink/p/?linkid=2024339) oturum açın ve adresine [https://aad.portal.azure.com/\#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties](https://aad.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Properties)gidin. Kiracı Kimliği özelliğini panoya kopyalamak için kopyala simgesine tıklayın.

### <a name="configuration-steps-to-enable-your-tenants-for-cross-tenant-mailbox-migrations"></a>Kiracılarınızın kiracılar arası posta kutusu geçişlerini etkinleştirmeye yönelik yapılandırma adımları

   > [!NOTE]
   > Önce hedefi (hedefi) yapılandırmanız gerekir. Bu adımları tamamlamak için hem kaynak hem de hedef kiracı için kiracı yöneticisi kimlik bilgilerine sahip olmanız veya bunları bilmeniz gerekmez. Adımlar, farklı yöneticiler tarafından her kiracı için ayrı ayrı gerçekleştirilebilir.

### <a name="prepare-the-target-destination-tenant-by-creating-the-migration-application-and-secret"></a>Geçiş uygulamasını ve gizli diziyi oluşturarak hedef (hedef) kiracıyı hazırlama

1. Hedef kiracı yöneticisi kimlik bilgilerinizle Azure AD portalınızda (<https://portal.azure.com>) oturum açın

   ![Azure Oturum Açma](../media/tenant-to-tenant-mailbox-move/74f26681e12df3308c7823ee7d527587.png)

2. Yönet Azure Active Directory altında görünüm'e tıklayın.

   ![Azure Active Directory Düğmesi](../media/tenant-to-tenant-mailbox-move/109ac3dfbac2403fb288f085767f393b.png)

3. Sol gezinti çubuğunda Uygulama kayıtları'ı seçin.

4. Yeni kayıt'ı seçin

   ![Yeni Uygulama](../media/tenant-to-tenant-mailbox-move/b36698df128e705eacff4bff7231056a.png)

5. Uygulama kaydetme sayfasında, Desteklenen hesap türleri'nin altında Herhangi bir kuruluş dizinindeki hesaplar 'ı seçin (Herhangi bir Azure AD dizini - Çok Kiracılı). Ardından, Yeniden Yönlendirme URI'si (isteğe bağlı) altında Web'i seçin ve girin <https://office.com>. Son olarak Kaydet'i seçin.

   ![Uygulama Kaydı](../media/tenant-to-tenant-mailbox-move/edcdf18b9f504c47284fe4afb982c433.png)

6. Sayfanın sağ üst köşesinde uygulamanın başarıyla oluşturulduğunu belirten bir bildirim açılır penceresi görürsünüz.

7. Giriş'e Geri dön Azure Active Directory ve Uygulama kayıtları tıklayın.

8. Sahip olunan uygulamalar altında, oluşturduğunuz uygulamayı bulun ve üzerine tıklayın.

9. ^Essentials altında, hedef kiracı için bir URL oluşturmak için daha sonra gerek duyacağınız için Uygulama (istemci) kimliğini kopyalamanız gerekir.

10. Şimdi sol gezinti çubuğunda API izinleri'ne tıklayarak uygulamanıza atanan izinleri görüntüleyin.

11. Varsayılan olarak, Kullanıcı. Oluşturduğunuz uygulamaya okuma izinleri atanır, ancak posta kutusu geçişleri için gerekli değildir, bu izni kaldırabilirsiniz.

    ![Uygulama İzinleri](../media/tenant-to-tenant-mailbox-move/6a8c13a36cb3e10964a6920b8138e12b.png)

12. Şimdi posta kutusu geçişi için izin eklememiz gerekiyor, İzin ekle'yi seçin

13. API izinleri iste pencerelerinde kuruluşumun kullandığı API'leri seçin, Office 365 Exchange Online arayın ve seçin.

    ![API'yi seçin](../media/tenant-to-tenant-mailbox-move/0b4dc1eea3910e9c475724d9473aca58.png)

14. Ardından Uygulama izinleri'ne tıklayın

15. Ardından İzinleri seçin'in altında Posta Kutusu'nı genişletin ve Mailbox.Migration'ı işaretleyin ve ekranın alt kısmındaki İzin ekle'yi seçin.

    ![API'leri ayarlama](../media/tenant-to-tenant-mailbox-move/0038a4cf74bb13de0feb51800e078803.png)

16. Şimdi uygulamanızın sol gezinti çubuğunda Sertifikalar & gizli diziler'i seçin.

17. İstemci gizli dizileri'nin altında yeni istemci gizli dizisi'ni seçin.

    ![İstemci Gizli Dizileri](../media/tenant-to-tenant-mailbox-move/273dafd5e6c6455695f9baf35ef9977a.png)

18. İstemci gizli dizisi ekle penceresinde bir açıklama girin ve istediğiniz süre sonu ayarlarını yapılandırın.

      > [!NOTE]
      > Bu, geçiş uç noktanızı oluştururken kullanılacak paroladır. Bu parolayı panonuza kopyalamanız veya bu parolayı güvenli/gizli parola güvenli konumuna kopyalamanız son derece önemlidir. Bu parolayı yalnızca bu kez görebilirsiniz! Bir şekilde kaybederseniz veya sıfırlamanız gerekiyorsa Azure portal yeniden oturum açabilir, Uygulama kayıtları gidebilir, geçiş uygulamanızı bulabilir, Gizli diziler & sertifikalar'ı seçebilir ve uygulamanız için yeni bir gizli dizi oluşturabilirsiniz.

19. Geçiş uygulamasını ve gizli diziyi başarıyla oluşturduğunuza göre, uygulamaya onay vermeniz gerekir. Uygulamaya onay vermek için Azure Active Directory giriş sayfasına dönün, sol gezinti bölmesinde Enterprise uygulamalara tıklayın, oluşturduğunuz geçiş uygulamanızı bulun, uygulamayı seçin ve sol gezinti bölmesinde İzinler'i seçin.

20. [Kiracınız] için yönetici onayı ver düğmesine tıklayın.

21. Yeni bir tarayıcı penceresi açılır ve Kabul Et'i seçin.

22. Kabulünüzü onaylamak için portal pencerenize geri dönüp Yenile'yi seçebilirsiniz.

23. Posta kutusu geçişini etkinleştirmek için uygulamayı kabul edebilmeleri için güvenilen iş ortağınıza (kaynak kiracı yöneticisi) gönderilecek URL'yi formüle edin. Oluşturduğunuz uygulamanın uygulama kimliğine ihtiyacınız olacak url'nin bir örneği aşağıda verilmiştir:

    ```powershell
    https://login.microsoftonline.com/sourcetenant.onmicrosoft.com/adminconsent?client_id=[application_id_of_the_app_you_just_created]&redirect_uri=https://office.com
    ```

    > [!NOTE]
    > Yeni oluşturduğunuz posta kutusu geçiş uygulamasının uygulama kimliğine ihtiyacınız olacaktır.
    >
    > Yukarıdaki örnekteki sourcetenant.onmicrosoft.com kaynak kiracılarınızın doğru onmicrosoft.com adıyla değiştirmeniz gerekir.
    >
    > [application_id_of_the_app_you_just_created] öğesini yeni oluşturduğunuz posta kutusu geçiş uygulamasının uygulama kimliğiyle de değiştirmeniz gerekir.

### <a name="prepare-the-target-tenant-by-creating-the-exchange-online-migration-endpoint-and-organization-relationship"></a>Exchange Online geçiş uç noktası ve kuruluş ilişkisi oluşturarak hedef kiracıyı hazırlama

1. Hedef Exchange Online kiracısında [PowerShell'i](/powershell/exchange/connect-to-exchange-online-powershell) Exchange Online Bağlan.

2. Kiracılar arası posta kutusu taşımaları için yeni bir geçiş uç noktası oluşturma

   > [!NOTE]
   > Yeni oluşturduğunuz posta kutusu geçiş uygulamasının uygulama kimliğine ve bu işlem sırasında yapılandırdığınız parolaya (gizli dizi) ihtiyacınız olacaktır. Ayrıca uç noktanızı kullandığınız Microsoft 365 Bulut Örneğine bağlı olarak farklı olabilir. Lütfen [Microsoft 365 uç noktaları](/microsoft-365/enterprise/microsoft-365-endpoints) sayfasına bakın ve kiracınız için doğru örneği seçin ve gerekli adresi en iyi duruma getirme ve uygun şekilde değiştirme Exchange Online gözden geçirin.

   ```powershell

   # Enable customization if tenant is dehydrated
   $dehydrated=Get-OrganizationConfig | select isdehydrated
   if ($dehydrated.isdehydrated -eq $true) {Enable-OrganizationCustomization}
   $AppId = "[guid copied from the migrations app]"
   $Credential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList $AppId, (ConvertTo-SecureString -String "[this is your secret password you saved in the previous steps]" -AsPlainText -Force)
   New-MigrationEndpoint -RemoteServer outlook.office.com -RemoteTenant "sourcetenant.onmicrosoft.com" -Credentials $Credential -ExchangeRemoteMove:$true -Name "[the name of your migration endpoint]" -ApplicationId $AppId
   ```

3. Yeni oluşturun veya mevcut kuruluş ilişkisi nesnenizi kaynak kiracınızla düzenleyin.

   ```powershell
   $sourceTenantId="[tenant id of your trusted partner, where the source mailboxes are]"
   $orgrels=Get-OrganizationRelationship
   $existingOrgRel = $orgrels | ?{$_.DomainNames -like $sourceTenantId}
   If ($null -ne $existingOrgRel)
   {
       Set-OrganizationRelationship $existingOrgRel.Name -Enabled:$true -MailboxMoveEnabled:$true -MailboxMoveCapability Inbound
   }
   If ($null -eq $existingOrgRel)
   {
       New-OrganizationRelationship "[name of the new organization relationship]" -Enabled:$true -MailboxMoveEnabled:$true -MailboxMoveCapability Inbound -DomainNames $sourceTenantId
   }
   ```

### <a name="prepare-the-source-current-mailbox-location-tenant-by-accepting-the-migration-application-and-configuring-the-organization-relationship"></a>Geçiş uygulamasını kabul ederek ve kuruluş ilişkisini yapılandırarak kaynak (geçerli posta kutusu konumu) kiracısını hazırlama

1. Bir tarayıcıdan, posta kutusu geçiş uygulamasına onay vermek için güvenilen iş ortağınız tarafından sağlanan URL bağlantısına gidin. URL şöyle görünür:

   ```powershell
   https://login.microsoftonline.com/sourcetenant.onmicrosoft.com/adminconsent?client_id=[application_id_of_the_app_you_just_created]&redirect_uri=https://office.com
   ```

   > [!NOTE]
   > Yeni oluşturduğunuz posta kutusu geçiş uygulamasının uygulama kimliğine ihtiyacınız olacaktır.
   > Yukarıdaki örnekteki sourcetenant.onmicrosoft.com kaynak kiracılarınızın doğru onmicrosoft.com adıyla değiştirmeniz gerekir.
   > [application_id_of_the_app_you_just_created] öğesini yeni oluşturduğunuz posta kutusu geçiş uygulamasının uygulama kimliğiyle de değiştirmeniz gerekir.

2. Açılır pencere göründüğünde uygulamayı kabul edin. Ayrıca Azure Active Directory portalınızda oturum açabilir ve uygulamayı Enterprise uygulamalar altında bulabilirsiniz.

3. Exchange Online PowerShell'de yeni bir kuruluş ilişkisi oluşturun veya mevcut kuruluş ilişkisi nesnenizi hedef (hedef) kiracınızla düzenleyin:

   ```powershell
   $targetTenantId="[tenant id of your trusted partner, where the mailboxes are being moved to]"
   $appId="[application id of the mailbox migration app you consented to]"
   $scope="[name of the mail enabled security group that contains the list of users who are allowed to migrate]"
   $orgrels=Get-OrganizationRelationship
   $existingOrgRel = $orgrels | ?{$_.DomainNames -like $targetTenantId}
   If ($null -ne $existingOrgRel)
   {
       Set-OrganizationRelationship $existingOrgRel.Name -Enabled:$true -MailboxMoveEnabled:$true -MailboxMoveCapability RemoteOutbound -OAuthApplicationId $appId -MailboxMovePublishedScopes $scope
   }
   If ($null -eq $existingOrgRel)
   {
       New-OrganizationRelationship "[name of your organization relationship]" -Enabled:$true -MailboxMoveEnabled:$true -MailboxMoveCapability RemoteOutbound -DomainNames $targetTenantId -OAuthApplicationId $appId -MailboxMovePublishedScopes $scope
   }
   ```

> [!NOTE]
> $sourceTenantId ve $targetTenantId olarak girdiğiniz kiracı kimliği, kiracı etki alanı adı değil GUID'dir. Kiracı kimliği örneği ve kiracı kimliğinizi bulma hakkında bilgi için bkz. [Microsoft 365 kiracı kimliğinizi bulma](/onedrive/find-your-office-365-tenant-id).

### <a name="how-do-i-know-this-worked"></a>Nasıl yaparım? çalıştığını biliyor musun?

[Test-MigrationServerAvailability](/powershell/module/exchange/Test-MigrationServerAvailability) cmdlet'ini hedef kiracınızda oluşturduğunuz kiracılar arası geçiş uç noktasında çalıştırarak kiracılar arası posta kutusu geçiş yapılandırmasını doğrulayabilirsiniz.

```powershell
Test-MigrationServerAvailability -EndPoint "Migration endpoint for cross-tenant mailbox moves" - TestMailbox "Primary SMTP of MailUser object in target tenant"
```

### <a name="move-mailboxes-back-to-the-original-source"></a>Posta kutularını özgün kaynağa geri taşıma

Bir posta kutusunun özgün kaynak kiracıya geri taşınması gerekiyorsa, aynı adım ve betik kümesinin hem yeni kaynak hem de yeni hedef kiracılarda çalıştırılması gerekir. Mevcut Kuruluş İlişkisi nesnesi güncelleştirilecek veya eklenecek, yeniden oluşturulmayacak

## <a name="prepare-target-user-objects-for-migration"></a>Hedef kullanıcı nesnelerini geçiş için hazırlama

Geçiş yapılan kullanıcılar, kiracılar arası taşımaları etkinleştirmek için hedef kiracıda ve Exchange Online sisteminde (MailUsers olarak) belirli özniteliklerle işaretlenmiş olmalıdır. Sistem, hedef kiracıda düzgün ayarlanmayan kullanıcılar için taşımalarda başarısız olur. Aşağıdaki bölümde, hedef kiracı için MailUser nesne gereksinimleri ayrıntılı olarak yer almaktadır.

### <a name="prerequisites-for-target-user-objects"></a>Hedef kullanıcı nesneleri için önkoşullar

Hedef kuruluşta aşağıdaki nesnelerin ve özniteliklerin ayarlandığından emin olun.

1. Kaynak kuruluştan taşınan herhangi bir posta kutusu için, Hedef kuruluşta bir MailUser nesnesi sağlamalısınız:

   - Hedef PostaKullanıcısı kaynak posta kutusundan bu özniteliklere sahip olmalı veya yeni User nesnesiyle atanmış olmalıdır:
      - ExchangeGUID (kaynaktan hedefe doğrudan akış): Posta kutusu GUID'sinin eşleşmesi gerekir. Bu hedef nesnede yoksa taşıma işlemi devam etmez.
      - ArchiveGUID (kaynaktan hedefe doğrudan akış): Arşiv GUID'sinin eşleşmesi gerekir. Bu hedef nesnede yoksa taşıma işlemi devam etmez. (Bu yalnızca kaynak posta kutusu Arşiv etkinse gereklidir).
      - LegacyExchangeDN (proxyAddress, "x500:\<LegacyExchangeDN>" olarak akış): LegacyExchangeDN hedef MailUser üzerinde x500: proxyAddress olarak bulunmalıdır. Ayrıca, kaynak posta kutusundan hedef posta kullanıcısına tüm x500 adreslerini kopyalamanız gerekir. Bunlar hedef nesnede yoksa taşıma işlemleri devam etmez.
      - UserPrincipalName: UPN, kullanıcının NEW kimliğine veya hedef şirketine hizalanır (örneğin, user@northwindtraders.onmicrosoft.com).
      - Birincil SMTPAddress: Birincil SMTP adresi kullanıcının YENİ şirketiyle (örneğin, user@northwind.com) hizalanır.
      - TargetAddress/ExternalEmailAddress: MailUser, kullanıcının kaynak kiracıda barındırılan geçerli posta kutusuna (örneğin user@contoso.onmicrosoft.com) başvurur. Bu değeri atarken, PrimarySMTPAddress'i atadığınızdan/atadığınızdan emin olun; aksi takdirde bu değer PrimarySMTPAddress değerini ayarlar ve bu da taşıma hatalarına neden olur.
      - Hedef MailUser'a kaynak posta kutusundan eski smtp proxy adresleri ekleyemezsiniz. Örneğin, fabrikam.onmicrosoft.com kiracı nesnelerinde MEU'da contoso.com koruyamazsınız). Etki alanları yalnızca bir Azure AD veya Exchange Online kiracıyla ilişkilendirilir.

     Örnek **hedef** MailUser nesnesi:

     | Öznitelik            | Değer                                                                                                                   |
     | -------------------- | ----------------------------------------------------------------------------------------------------------------------- |
     | Diğer ad                | LaraN                                                                                                                   |
     | Alıcı Türü        | Mailuser                                                                                                                |
     | RecipientTypeDetails | Mailuser                                                                                                                |
     | Userprincipalname    | LaraN@northwintraders.onmicrosoft.com                                                                                   |
     | PrimarySmtpAddress   | Lara.Newton@northwind.com                                                                                               |
     | ExternalEmailAddress | SMTP:LaraN@contoso.onmicrosoft.com                                                                                      |
     | ExchangeGuid         | 1ec059c7-8396-4d0b-af4e-d6bd4c12a8d8                                                                                    |
     | LegacyExchangeDN     | /o=İlk Kuruluş/ou=Exchange Yönetim Grubu                                                                  |
     |                      | (FYDIBOHF23SPDLT)/cn=Recipients/cn=74e5385fce4b46d19006876949855035Lara                                                 |
     | EmailAddresses       | x500:/o=First Organization/ou=Exchange Yönetim Grubu (FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c8190 |
     |                      | 7273f1f9-Lara                                                                                                           |
     |                      | smtp:LaraN@northwindtraders.onmicrosoft.com                                                                             |
     |                      | SMTP:Lara.Newton@northwind.com                                                                                          |

     Örnek **kaynak** Posta Kutusu nesnesi:

     | Öznitelik            | Değer                                                                   |
     | -------------------- | ----------------------------------------------------------------------- |
     | Diğer ad                | LaraN                                                                   |
     | Alıcı Türü        | UserMailbox                                                             |
     | RecipientTypeDetails | UserMailbox                                                             |
     | Userprincipalname    | LaraN@contoso.onmicrosoft.com                                           |
     | PrimarySmtpAddress   | Lara.Newton@contoso.com                                                 |
     | ExchangeGuid         | 1ec059c7-8396-4d0b-af4e-d6bd4c12a8d8                                    |
     | LegacyExchangeDN     | /o=İlk Kuruluş/ou=Exchange Yönetim Grubu                  |
     |                      | (FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c81907273f1f9Lara |
     | EmailAddresses       | smtp:LaraN@contoso.onmicrosoft.com                                      |
     |                      | SMTP:Lara.Newton@contoso.com                                            |

   - Karma geri yazma Exchange ek öznitelikler eklenmiş olabilir. Aksi takdirde, bunlar dahil edilmelidir.
   - msExchBlockedSendersHash – İstemcilerden gelen güvenli ve engellenen gönderen verilerini şirket içi Active Directory geri yazar.
   - msExchSafeRecipientsHash – İstemcilerden gelen güvenli ve engellenen gönderen verilerini şirket içi Active Directory'a geri yazar.
   - msExchSafeSendersHash – İstemcilerden gelen çevrimiçi güvenli ve engellenen gönderen verilerini şirket içi Active Directory yazar.

2. Kaynak posta kutusu LitigationHold üzerindeyse ve kaynak posta kutusu Kurtarılabilir Öğeler boyutu veritabanı varsayılanımızdan (30 GB) büyükse, hedef kota kaynak posta kutusu boyutundan küçük olduğundan taşıma işlemi devam etmeyecektir. Hedef MailUser nesnesini, ELC posta kutusu bayraklarını kaynak ortamdan hedefe geçirerek hedef sistemi tetikleyerek MailUser kotasını 100 GB'a genişleterek hedefe taşınmasını sağlayabilirsiniz. ELC bayraklarını damgalama komutları kiracı yöneticilerine gösterilmediğinden, bu yönergeler yalnızca Azure AD Bağlan çalıştıran karma kimlik için çalışır.

    > [!NOTE]
    > ÖRNEK – OLDUĞU GIBI, GARANTİ YOK
    >
    > Bu betik, hem kaynak posta kutusuna (kaynak değerleri almak için) hem de hedef şirket içi Active Directory (ADUser nesnesini damgalamak için) bir bağlantı olduğunu varsayar. Kaynakta dava açma veya tek öğe kurtarma etkinleştirildiyse, bunu hedef hesapta ayarlayın.  Bu, hedef hesabın dökümü boyutunu 100 GB'a yükseltecektir.

    ```powershell
    $ELCValue = 0
    if ($source.LitigationHoldEnabled) {$ELCValue = $ELCValue + 8} if ($source.SingleItemRecoveryEnabled) {$ELCValue = $ELCValue + 16} if ($ELCValue -gt 0) {Set-ADUser -Server $domainController -Identity $destination.SamAccountName -Replace @{msExchELCMailboxFlags=$ELCValue}}
    ```

3. Karma olmayan hedef kiracılar, MailUser nesnesinde Litigation Hold özelliğini etkinleştirmek ve kotayı 100 GB'a yükseltmek için aşağıdaki komutu çalıştırarak geçiş öncesinde MailUsers için Kurtarılabilir Öğeler klasöründeki kotayı değiştirebilir:

   ```powershell
   Set-MailUser -Identity <MailUserIdentity> -EnableLitigationHoldForMigration
   ```

   Bunun karma kiracılar için çalışmayacağını unutmayın.

4. Hedef kuruluştaki kullanıcıların, kuruluş için uygun Exchange Online abonelikleri ile lisanslanması gerekir. Posta kutusu taşımadan önce lisans uygulayabilirsiniz, ancak HEDEF MailUser ExchangeGUID ve proxy adresleriyle düzgün bir şekilde ayarlandıktan sonra. ExchangeGUID uygulanmadan önce lisans uygulanması, hedef kuruluşta yeni bir posta kutusunun sağlanmasına neden olur.

    > [!NOTE]
    > Posta Kutusu veya MailUser nesnesine lisans uyguladığınızda, Exchange EmailAddresses dizisine yalnızca doğrulanmış etki alanlarının dahil edildiğinden emin olmak için tüm SMTP türü proxyAddresses temizlenir.

5. Hedef MailUser'da Kaynak ExchangeGuid ile eşleşmeyen önceki ExchangeGuid olmadığından emin olmanız gerekir. Hedef MEU daha önce Exchange Online lisansına sahipse ve bir posta kutusu sağlandıysa bu durum oluşabilir. Hedef MailUser daha önce Source ExchangeGuid ile eşleşmeyen bir ExchangeGuid lisansına sahipse veya bir ExchangeGuid'e sahipse, bulut MEU'sunu temizlemeniz gerekir. Bu bulut MEU'ları için komutunu çalıştırabilirsiniz `Set-User <identity> -PermanentlyClearPreviousMailboxInfo`.

    > [!CAUTION]
    > Bu işlem geri alınamaz. Nesnenin softDeleted posta kutusu varsa, bu noktadan sonra geri yüklenemez. Ancak temizlendikten sonra, doğru ExchangeGuid'i hedef nesneyle eşitleyebilirsiniz ve MRS kaynak posta kutusunu yeni oluşturulan hedef posta kutusuna bağlar. (Yeni parametrede EHLO blogu başvurusu.)

    Bu komutu kullanarak daha önce posta kutusu olan nesneleri bulun.

    ```powershell
    Get-User <identity> | select Name, *recipient* | Format-Table -AutoSize
    ```

    Burada bir örnek verilmiştir.

    ```powershell
    Get-User John@northwindtraders.com |select name, *recipient*| Format-Table -AutoSize

    Name       PreviousRecipientTypeDetails     RecipientType RecipientTypeDetails
    ----       ---------------------------- ------------- --------------------
    John       UserMailbox                  MailUser      MailUser
    ```

    Bu komutu kullanarak geçici olarak silinen posta kutusunu temizleyin.

    ```powershell
    Set-User <identity> -PermanentlyClearPreviousMailboxInfo
    ```

    Burada bir örnek verilmiştir.

    ```powershell
    Set-User John@northwindtraders.com -PermanentlyClearPreviousMailboxInfo -Confirm

    Are you sure you want to perform this action?
    Delete all existing information about user "John@northwindtraders.com"?. This operation will clear existing values from Previous home MDB and Previous Mailbox GUID of the user. After deletion, reconnecting to the previous mailbox that existed in the cloud will not be possible and any content it had will be unrecoverable PERMANENTLY.
    Do you want to continue?
    [Y] Yes  [A] Yes to All  [N] No  [L] No to All  [?] Help (default is "Y"): Y
    ```

### <a name="perform-mailbox-migrations"></a>Posta kutusu geçişlerini gerçekleştirme

Kiracılar arası Exchange posta kutusu geçişleri, geçiş toplu işlemleri olarak hedef kiracıdan başlatılır. Bu, şirket içi Exchange Microsoft 365 geçiş yaparken şirket içi geçiş toplu işlemlerinin çalışması gibidir.

### <a name="create-migration-batches"></a>Geçiş toplu işleri oluşturma

Taşımaları başlatmaya yönelik örnek bir geçiş toplu iş cmdlet'i aşağıda verilmiştir.

```powershell
New-MigrationBatch -Name T2Tbatch -SourceEndpoint target_source_7977 -CSVData ([System.IO.File]::ReadAllBytes('users.csv')) -Autostart -TargetDeliveryDomain target.onmicrosoft.com

Identity                   Status  Type               TotalCount
--------                   ------  ----               ----------
T2Tbatch                   Syncing ExchangeRemoteMove 1
```

> [!NOTE]
> CSV dosyasındaki e-posta adresi, kaynak kiracıda değil hedef kiracıda belirtilen adres olmalıdır.
>
> [Cmdlet hakkında daha fazla bilgi için buraya tıklayın](/powershell/module/exchange/new-migrationbatch)
>
> [Örnek bir CSV dosyası için buraya tıklayın](/exchange/csv-files-for-mailbox-migration-exchange-2013-help)

Geçiş toplu işlemi gönderimi, kiracılar arası seçenek belirlenirken yeni <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezinden</a> de desteklenir.

### <a name="update-on-premises-mailusers"></a>Şirket içi MailUsers'i güncelleştirme

Posta kutusu kaynaktan hedefe geçtikten sonra, hem kaynak hem de hedefteki şirket içi posta kullanıcılarının yeni targetAddress ile güncelleştirildiğinden emin olmanız gerekir. Örneklerde, taşımada kullanılan targetDeliveryDomain **contoso.onmicrosoft.com**. Posta kullanıcılarını bu targetAddress ile güncelleştirin.

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

### <a name="do-we-need-to-update-remotemailboxes-in-source-on-premises-after-the-move"></a>Taşıma sonrasında şirket içi kaynaktaki RemoteMailbox'ları güncelleştirmemiz gerekiyor mu?

Evet, kaynak kiracı posta kutusu hedef kiracıya geçtiğinde kaynak şirket içi kullanıcıların targetAddress (RemoteRoutingAddress/ExternalEmailAddress) güncelleştirmeniz gerekir.  Posta yönlendirme, farklı targetAddresses'e sahip birden çok posta kullanıcısı arasındaki başvuruları izleyebilirken, posta kullanıcıları için Serbest/Meşgul aramaları posta kutusu kullanıcısının konumunu hedeflemeLIDIR. Serbest/Meşgul aramaları birden çok yeniden yönlendirmeyi kovalamaz.

### <a name="do-teams-meetings-migrate-cross-tenant"></a>Teams toplantılar kiracılar arası geçiş yapar mı?

Toplantılar taşınır, ancak öğeler kiracılar arası geçiş yaparken Teams toplantı URL'si güncelleştirilmez. HEDEF kiracıda URL geçersiz olacağından, Teams toplantılarını kaldırmanız ve yeniden oluşturmanız gerekir.

### <a name="does-the-teams-chat-folder-content-migrate-cross-tenant"></a>Teams sohbet klasörü içeriği kiracılar arası geçiş yapar mı?

Hayır, Teams sohbet klasörü içeriği kiracılar arası geçiş yapmaz.

### <a name="how-can-i-see-just-moves-that-are-cross-tenant-moves-not-my-onboarding-and-off-boarding-moves"></a>Ekleme ve biniş dışı hareketlerimi değil, yalnızca kiracılar arası taşımalar olan taşımaları nasıl görebilirim?

_Flags_ parametresini kullanın. Burada bir örnek verilmiştir.

```powershell
Get-MoveRequest -Flags "CrossTenant"
```

### <a name="can-you-provide-example-scripts-for-copying-attributes-used-in-testing"></a>Testte kullanılan öznitelikleri kopyalamak için örnek betikler sağlayabilir misiniz?

> [!NOTE]
> ÖRNEK – OLDUĞU GIBI GARANTİ YOK Bu betik, hem kaynak posta kutusuna (kaynak değerleri almak için) hem de etki alanı hizmetleri şirket içi Active Directory hedefine (ADUser nesnesini damgalama amacıyla) bir bağlantı olduğunu varsayar. Kaynakta dava açma veya tek öğe kurtarma etkinleştirildiyse, bunu hedef hesapta ayarlayın.  Bu, hedef hesabın dökümü boyutunu 100 GB'a yükseltecektir.

   ```powershell
   # This will export users from the source tenant with the CustomAttribute1 = "Cross-Tenant-Project"
   # These are the 'target' users to be moved to the Northwind org tenant
   $outFileUsers = "$home\desktop\UsersToMigrate.txt"
   $outFileUsersXML = "$home\desktop\UsersToMigrate.xml"
   Get-Mailbox -Filter "CustomAttribute1 -like 'Cross-Tenant-Project'" -ResultSize Unlimited | Select-Object -ExpandProperty  Alias | Out-File $outFileUsers
   $mailboxes = Get-Content $outFileUsers
   $mailboxes | ForEach-Object {Get-Mailbox $_} | Select-Object PrimarySMTPAddress,Alias,SamAccountName,FirstName,LastName,DisplayName,Name,ExchangeGuid,ArchiveGuid,LegacyExchangeDn,EmailAddresses | Export-Clixml $outFileUsersXML
   ```

   ```powershell
   # Copy the file $outfile to the desktop of the target on-premises then run the below to create MEU in Target
   $mailboxes = Import-Clixml $home\desktop\UsersToMigrate.xml
   add-type -AssemblyName System.Web
   foreach ($m in $mailboxes) {
       $organization = "@contoso.onmicrosoft.com"
       $mosi = $m.Alias+$organization
       $Password = [System.Web.Security.Membership]::GeneratePassword(16,4) | ConvertTo-SecureString -AsPlainText -Force
       $x500 = "x500:" +$m.LegacyExchangeDn
       $tmpUser = New-MailUser -MicrosoftOnlineServicesID $mosi -PrimarySmtpAddress $mosi -ExternalEmailAddress $m.PrimarySmtpAddress -FirstName $m.FirstName -LastName $m.LastName -Name $m.Name -DisplayName $m.DisplayName -Alias $m.Alias -Password $Password
       $tmpUser | Set-MailUser -EmailAddresses @{add=$x500} -ExchangeGuid $m.ExchangeGuid -ArchiveGuid $m.ArchiveGuid -CustomAttribute1 "Cross-Tenant-Project"
       $tmpx500 = $m.EmailAddresses | ?{$_ -match "x500"}
       $tmpx500 | %{Set-MailUser $m.Alias -EmailAddresses @{add="$_"}}
       }
   ```

   ```powershell
   # Now sync the changes from On-Premises to Azure and Exchange Online in the Target tenant
   # This action should create the target mail enabled users (MEUs) in the Target tenant
   Start-ADSyncSyncCycle
   ```

### <a name="how-do-we-access-outlook-on-day-1-after-the-use-mailbox-is-moved"></a>Kullanım posta kutusu taşındıktan sonra 1. Günde Outlook nasıl erişebiliriz?

Bir etki alanına yalnızca bir kiracı sahip olabileceğinden, posta kutusu taşıma işlemi tamamlandığında eski birincil SMTPAddress hedef kiracıdaki kullanıcıyla ilişkilendirilmez; yalnızca yeni kiracıyla ilişkili etki alanları. Outlook, hizmette kimlik doğrulaması yapmak için yeni UPN kullanıcılarını kullanır ve Outlook profili, hedef sistemdeki posta kutusuyla eşleşecek eski birincil SMTPAddress'i bulmayı bekler. Eski adres hedef Sistemde olmadığından, outlook profili yeni taşınan posta kutusunu bulmak için bağlanmayacak.

Bu ilk dağıtım için kullanıcıların profillerini yeni UPN, birincil SMTP adresleri ve yeniden eşitleme OST içeriğiyle yeniden oluşturmaları gerekir.

> [!NOTE]
> Tamamlama için kullanıcılarınızı toplu iş olarak planlayın. Outlook istemci profilleri oluşturulduğunda ve izleyen OST ve OAB dosyaları istemcilere indirildiğinde ağ kullanımını ve kapasitesini dikkate almanız gerekir.

### <a name="what-exchange-rbac-roles-do-i-need-to-be-member-of-to-set-up-or-complete-a-cross-tenant-move"></a>Kiracılar arası taşımayı ayarlamak veya tamamlamak için hangi Exchange RBAC rollerine üye olmak istiyorum?

Posta kutusu taşıma işlemi yürütülürken temsilci görevleri varsayımını temel alan bir rol matrisi vardır. Şu anda iki rol gereklidir:

- İlk rol, içeriği kiracı/kuruluş sınırınıza veya dışına taşıma yetkilendirmesini oluşturan tek seferlik bir kurulum görevidir. Verileri kuruluş denetiminizden çıkarmak tüm şirketler için kritik bir konu olduğundan, Kuruluş Yöneticisi 'nin (OrgAdmin) en yüksek atanan rolünü seçtik. Bu rol, uzak kuruluşla -MailboxMoveCapability öğesini tanımlayan yeni bir OrganizationRelationship'i değiştirmelidir veya ayarlamalıdır. Yalnızca OrgAdmin MailboxMoveCapability ayarını değiştirebilirken, OrganizationRelationship üzerindeki diğer öznitelikler Federasyon Paylaşımı yöneticisi tarafından yönetilebilir.

- Gerçek taşıma komutlarını yürütme rolü alt düzey bir işleve devredilebilir. Posta Kutularını Taşı rolü, posta kutularını kuruluşa veya kuruluş dışına taşıma özelliğine atanır.

### <a name="how-do-we-target-which-smtp-address-is-selected-for-targetaddress-targetdeliverydomain-on-the-converted-mailbox-to-mailuser-conversion"></a>Dönüştürülen posta kutusunda (MailUser dönüştürmesine) targetAddress (TargetDeliveryDomain) için hangi SMTP adresinin seçildiğini nasıl hedefleyeceğiz?

Exchange posta kutusu, hedef nesnedeki bir e-posta adresiyle (proxyAddress) eşleşerek bir MailUser'a dönüştürülürken özgün kaynak posta kutusunda TARGETAddress'i MRS oluşturarak taşınır. İşlem, taşıma komutuna geçirilen -TargetDeliveryDomain değerini alır ve ardından hedef taraftaki etki alanı için eşleşen bir ara sunucuyu denetler. Bir eşleşme bulduğumuzda, dönüştürülen posta kutusu (şimdi MailUser) nesnesinde ExternalEmailAddress (targetAddress) ayarlamak için eşleşen proxyAddress kullanılır.

### <a name="how-do-mailbox-permissions-transition"></a>Posta kutusu izinleri nasıl geçiş yapar?

Posta kutusu izinleri, Adına Gönder ve Posta Kutusu Erişimi'ni içerir:

- Adına Gönder (AD:publicDelegates), kullanıcının posta kutusuna temsilci olarak erişimi olan alıcıların DN'sini depolar. Bu değer Active Directory'de depolanır ve şu anda posta kutusu geçişinin bir parçası olarak taşınmaz. Kaynak posta kutusunda publicDelegates ayarlandıysa, MEU'nun posta kutusuna dönüştürme işlemi çalıştırılarak `Set-Mailbox <principle> -GrantSendOnBehalfTo <delegate>`hedef ortamda tamamlandıktan sonra hedef Posta Kutusu'nda publicDelegates'i yeniden örneklemeniz gerekir.

- Posta kutusunda depolanan Posta Kutusu İzinleri, hem sorumlu hem de temsilci hedef sisteme taşındığında posta kutusuyla birlikte taşınır. Örneğin, kullanıcıya TestUser_7 kiracı SourceCompany.onmicrosoft.com posta kutusu TestUser_8 FullAccess verilir. Posta kutusu TargetCompany.onmicrosoft.com taşındıktan sonra hedef dizinde aynı izinler ayarlanır. Hem kaynak hem de hedef kiracılarda TestUser_7 için _Get-MailboxPermission_ kullanan örnekler aşağıda gösterilmiştir. Exchange cmdlet'lere kaynak ve hedef eklenmiştir.

Taşımadan önce posta kutusu izni çıkışının bir örneği aşağıda verilmiştir.

```powershell
Get-SourceMailboxPermission TestUser_7 | Format-Table -AutoSize User, AccessRights, IsInherited, Deny

User                                             AccessRights                         IsInherited Deny
----                                             ------------                         ----------- ----
NT AUTHORITY\SELF                                {FullAccess, ReadPermission}         False       False
TestUser_8@SourceCompany.onmicrosoft.com         {FullAccess}                         False       False
```

Taşıma sonrasında posta kutusu izni çıkışının bir örneği aşağıda verilmiştır.

```powershell
Get-TargetMailboxPermission TestUser_7 | Format-Table -AutoSize User, AccessRights, IsInherited, Deny

User                                             AccessRights                         IsInherited Deny
----                                             ------------                         ----------- ----
NT AUTHORITY\SELF                                {FullAccess, ReadPermission}         False       False
TestUser_8@TargetCompany.onmicrosoft.com         {FullAccess}                         False       False
```

> [!NOTE]
> Kiracılar arası posta kutusu ve takvim izinleri DESTEKLENMEZ. Bu bağlı posta kutularının kaynak kiracıdan aynı anda geçiş yapması için sorumluları ve temsilcileri birleştirilmiş taşıma toplu işlerinde düzenlemeniz gerekir.

### <a name="what-x500-proxy-should-be-added-to-the-target-mailuser-proxy-addresses-to-enable-migration"></a>Geçişi etkinleştirmek için hedef MailUser proxy adreslerine hangi X500 proxy eklenmelidir?

Kiracılar arası posta kutusu geçişi, kaynak posta kutusu nesnesinin LegacyExchangeDN değerinin hedef MailUser nesnesine x500 e-posta adresi olarak damgalanması gerekir.

Örneğin:

```powershell
LegacyExchangeDN value on source mailbox is:
/o=First Organization/ou=Exchange Administrative Group(FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c81907273f1f9Lara

so, the x500 email address to be added to target MailUser object would be:
x500:/o=First Organization/ou=Exchange Administrative Group (FYDIBOHF23SPDLT)/cn=Recipients/cn=d11ec1a2cacd4f81858c81907273f1f9-Lara
```

> [!NOTE]
> Bu X500 proxy'sine ek olarak, kaynaktaki posta kutusundan hedefteki posta kutusuna tüm X500 proxy'lerini kopyalamanız gerekir.

### <a name="can-the-source-and-target-tenant-utilize-the-same-domain-name"></a>Kaynak ve hedef kiracı aynı etki alanı adını kullanabilir mi?

Hayır. Kaynak ve hedef kiracı etki alanı adları benzersiz olmalıdır. Örneğin, contoso.com kaynak etki alanı ve fourthcoffee.com hedef etki alanı.

### <a name="will-shared-mailboxes-move-and-still-work"></a>Paylaşılan posta kutuları taşınacak ve çalışmaya devam edecek mi?

Evet, ancak mağaza izinlerini yalnızca şu makalelerde açıklandığı gibi saklarız:

- [Microsoft Docs | Exchange Online'de alıcılar için izinleri yönetme](/exchange/recipients-in-exchange-online/manage-permissions-for-recipients)

- [Microsoft Desteği | ayrılmış Office 365 Exchange ve Outlook posta kutusu izinleri verme](https://support.microsoft.com/topic/how-to-grant-exchange-and-outlook-mailbox-permissions-in-office-365-dedicated-bac01b2c-08ff-2eac-e1c8-6dd01cf77287)

### <a name="do-you-have-any-recommendations-for-batches"></a>Toplu iş önerileriniz var mı?

Toplu iş başına 2000 posta kutusunu aşmayın. Eşitleme sırasında son kullanıcılar üzerinde herhangi bir etki olmadığından, toplu iş göndermeyi kesme tarihinden iki hafta önce kesinlikle öneririz. 50.000'den fazla posta kutusu miktarı için rehberliğe ihtiyacınız varsa, crosstenantmigrationpreview@service.microsoft.com Mühendislik Geri Bildirim Dağıtım Listesi'ne ulaşabilirsiniz.

### <a name="what-if-i-use-service-encryption-with-customer-key"></a>Müşteri Anahtarı ile Hizmet şifrelemesi kullanırsam ne olur?

Posta kutusunun şifresi taşınmadan önce çözülür. Müşteri Anahtarının hala gerekliyse hedef kiracıda yapılandırıldığından emin olun. Daha fazla bilgi için [buraya](/microsoft-365/compliance/customer-key-overview) bakın.

### <a name="what-is-the-estimated-migration-time"></a>Tahmini geçiş süresi nedir?

Geçişinizi planlamanıza yardımcı olmak için [buradaki](/exchange/mailbox-migration/office-365-migration-best-practices#estimated-migration-times) tabloda toplu posta kutusu geçişlerinin veya tek tek geçişlerin ne zaman tamamlanmasını bekleyebileceğinize ilişkin yönergeler gösterilir. Bu tahminler, önceki müşteri geçişlerinin veri analizini temel alır. Her ortam benzersiz olduğundan, tam geçiş hızınız farklılık gösterebilir.

Bu özelliğin şu anda önizlemede ve SLA'da olduğunu ve ilgili Hizmet Düzeylerinin bu özelliğin önizleme durumu sırasındaki performans veya kullanılabilirlik sorunları için geçerli olmadığını unutmayın.

### <a name="protecting-documents-in-the-source-tenant-consumable-by-users-in-the-destination-tenant"></a>Hedef kiracıdaki kullanıcılar tarafından kullanılabilir kaynak kiracıdaki belgeleri koruma.**

Kiracılar arası geçiş yalnızca posta kutusu verilerini geçirir ve başka bir şey geçirmez. Aşağıdaki blog gönderisinde belgelenen ve yardımcı olabilecek birden çok seçenek daha vardır: <https://techcommunity.microsoft.com/t5/security-compliance-and-identity/mergers-and-spinoffs/ba-p/910455>

### <a name="can-i-have-the-same-labels-in-the-destination-tenant-as-you-had-in-the-source-tenant-either-as-the-only-set-of-labels-or-an-additional-set-of-labels-for-the-migrated-users-depending-on-alignment-between-the-organizations"></a>Hedef kiracıda, kuruluşlar arasındaki hizalamaya bağlı olarak, geçirilen kullanıcılar için tek etiket kümesi veya ek bir etiket kümesi olarak kaynak kiracıda sahip olduğunuz etiketlerin aynısını alabilir miyim.**

Kiracılar arası geçişler etiketleri dışarı aktarmadığından ve kiracılar arasında etiketleri paylaşmanın bir yolu olmadığından, bunu yalnızca hedef kiracıdaki etiketleri yeniden oluşturarak gerçekleştirebilirsiniz.

### <a name="do-you-support-moving-microsoft-365-groups"></a>Microsoft 365 Grupları taşımayı destekliyor musunuz?

Şu anda Kiracılar Arası posta kutusu geçişleri özelliği Microsoft 365 Grupları geçişini desteklemiyor.

### <a name="can-a-source-tenant-admin-perform-an-ediscovery-search-against-a-mailbox-after-the-mailbox-has-been-migrated-to-the-newtarget-tenant"></a>Kaynak kiracı yöneticisi, posta kutusu yeni/hedef kiracıya geçirildikten sonra posta kutusunda eBulma araması yapabilir mi?

Hayır, kiracılar arası posta kutusu geçişinin ardından, geçirilen kullanıcının kaynaktaki posta kutusuna karşı eBulma çalışmaz. Bunun nedeni, posta kutusu hedef kiracıya geçirildiğinden ve artık hedef kiracıya ait olduğundan kaynakta artık aranacak bir posta kutusu olmamasıdır. eBulma, posta kutusu sonrası geçişi yalnızca hedef kiracıda (posta kutusunun bulunduğu yerde) yapılabilir. Geçiş sonrasında kaynak posta kutusunun bir kopyasının kaynak kiracıda kalıcı olması gerekiyorsa, kaynaktaki yönetici verilerine karşı gelecekteki eBulma işlemleri için içeriği alternatif bir posta kutusu geçiş öncesi geçişe kopyalayabilir.

### <a name="at-which-point-will-the-destination-mailuser-be-converted-to-a-destination-mailbox-and-the-source-mailbox-converted-to-a-source-mailuser"></a>Hedef MailUser hangi noktada hedef posta kutusuna, kaynak posta kutusu ise bir kaynak MailUser'a dönüştürülecek?

Bu dönüştürmeler geçiş işlemi sırasında otomatik olarak gerçekleşir. El ile adım atılması gerekmez.

### <a name="at-which-step-should-i-assign-the-exchange-online-license-to-destination-mailusers"></a>Hedef MailUsers'a Exchange Online lisansını hangi adımda atamalıyım?

Geçiş tamamlanmadan önce bu yapılabilir, ancak _ExchangeGuid_ özniteliğini damgalamadan önce lisans atamamalısınız veya MailUser nesnesinin posta kutusuna dönüştürülmesi başarısız olur ve bunun yerine yeni bir posta kutusu oluşturulur. Bu riski azaltmak için geçiş tamamlanana kadar beklemek ve 30 günlük yetkisiz kullanım süresi boyunca lisans atamak en iyisidir.

## <a name="known-issues"></a>Bilinen sorunlar

- **Sorun: Geçiş sonrası Teams kaynak kiracıdaki işlevsellik sınırlı olacaktır.** Posta kutusu hedef kiracıya geçirildikten sonra, kaynak kiracıdaki Teams artık kullanıcının posta kutusuna erişimi olmaz. Bu nedenle, bir kullanıcı kaynak kiracı kimlik bilgileriyle Teams oturum açarsa, profil resminizi güncelleştirememe, takvim uygulaması olmaması ve genel ekiplerde arama ve katılma gibi işlevler kaybı olur.

- **Sorun: Otomatik Genişletilmiş arşivler geçirilemiyor.** Kiracılar arası geçiş özelliği, belirli bir kullanıcı için birincil posta kutusunun ve arşiv posta kutusunun geçişlerini destekler. Ancak kaynaktaki kullanıcının otomatik olarak genişletilmiş bir arşivi varsa (yani birden fazla arşiv posta kutusu varsa, özellik ek arşivleri geçiremez ve başarısız olmalıdır).

- **Sorun: Sahip olunmayan smtp proxy'si olan Cloud MailUsersAddress block MRS arka planı taşır.** Hedef kiracı MailUser nesneleri oluştururken, tüm SMTP proxy adreslerinin hedef kiracı kuruluşuna ait olduğundan emin olmanız gerekir. Hedef posta kullanıcısı üzerinde yerel kiracıya ait olmayan bir SMTP proxyAddress varsa, MailUser'ın Posta Kutusu'na dönüştürülmesi engellenir. Bunun nedeni, posta kutusu nesnelerinin yalnızca kiracının yetkili olduğu etki alanlarından (kiracı tarafından talep edilen etki alanları) posta gönderebileceği güvencemizden kaynaklanır:

  - Azure AD Bağlan kullanarak şirket içindeki kullanıcıları eşitlerken, şirket içi MailUser nesnelerini ExternalEmailAddress ile posta kutusunun bulunduğu kaynak kiracıya işaret eden (LaraN@contoso.onmicrosoft.com) sağlar ve PrimarySMTPAddress'i hedef kiracıda (Lara.Newton@northwind.com) bulunan bir etki alanı olarak damgalarsınız. Bu değerler kiracıyla eşitlenir ve uygun bir posta kullanıcısı sağlanır ve geçiş için hazır olur. Burada örnek bir nesne gösterilmiştir.

    ```powershell
    Get-MailUser LaraN | select ExternalEmailAddress, EmailAddresses

    ExternalEmailAddress               EmailAddresses
    --------------------               --------------
    SMTP:LaraN@contoso.onmicrosoft.com {SMTP:lara.newton@northwind.com}
    ```

   > [!NOTE]
   > _contoso.onmicrosoft.com_ adresi EmailAddresses / proxyAddresses dizisinde _yok_.

- **Sorun: "Dış" birincil SMTP adreslerine sahip MailUser nesneleri değiştiriliyor / "şirket tarafından talep edilen" etki alanlarına sıfırlanıyor**

  MailUser nesneleri, yerel olmayan posta kutularının işaretçileridir. Kiracılar arası posta kutusu geçişleri söz konusu olduğunda, kaynak posta kutusunu (hedef kuruluşun perspektifinden) veya hedef posta kutusunu (kaynak kuruluşun perspektifinden) temsil etmek için MailUser nesnelerini kullanırız. MailUsers, gerçek posta kutusunun smtp adresine (ProxyTest@fabrikam.onmicrosoft.com) ve dizinde posta kutusu kullanıcısının görüntülenen SMTP adresini temsil eden primarySMTP adresine işaret eden bir ExternalEmailAddress (targetAddress) içerir. Bazı kuruluşlar, birincil SMTP adresini yerel kiracının sahip olduğu/doğruladığı bir adres olarak değil dış SMTP adresi olarak (contoso.com yerine fabrikam.com gibi) görüntülemeyi tercih eder.  Ancak, lisanslama işlemleri aracılığıyla MailUser'a bir Exchange hizmet planı nesnesi uygulandıktan sonra, birincil SMTP adresi yerel kuruluş (contoso.com) tarafından doğrulanmış bir etki alanı olarak gösterilecek şekilde değiştirilir. İki olası neden vardır:

  - MailUser'a herhangi bir Exchange hizmet planı uygulandığında, Azure AD işlemi yerel kuruluşun başka bir kiracıdan posta gönderemediğinden, kimlik sahtekarlığına veya posta gönderemediğinden emin olmak için ara sunucu temizlemeyi zorlamaya başlar. Bu hizmet planlarına sahip bir alıcı nesnesi üzerindeki tüm SMTP adresleri, adres yerel kuruluş tarafından doğrulanmazsa kaldırılır. Örnekte olduğu gibi, Fabikam.com etki alanı contoso.onmicrosoft.com kiracı tarafından doğrulanmaz, bu nedenle temizleme işlemi bu fabrikam.com etki alanını kaldırır. Geçiş öncesinde veya geçiş sonrasında bu dış etki alanlarını MailUser'da kalıcı hale getirmek istiyorsanız, geçiş işlemlerinizi taşıma tamamlandıktan sonra veya taşımadan önce kullanıcıların beklenen dış markanın uygulandığından emin olmak için lisansları kaldıracak şekilde değiştirmeniz gerekir. Posta kutusu nesnesinin posta hizmetini etkilemeyecek şekilde düzgün lisanslandığından emin olmanız gerekir.
  - contoso.onmicrosoft.com kiracısında MailUser'daki hizmet planlarını kaldırmaya yönelik örnek betik burada gösterilmiştir.

    ```powershell
    $LO = New-MsolLicenseOptions -AccountSkuId "contoso:ENTERPRISEPREMIUM" DisabledPlans "LOCKBOX_ENTERPRISE","EXCHANGE_S_ENTERPRISE","INFORMATION_BARRIERS","MIP_S_CLP2","MIP_S_CLP1","MYANALYTICS_P2","EXCHANGE_ANALYTICS","EQUIVIO_ANALYTICS","THREAT_INTELLIGENCE","PAM_ENTERPRISE","PREMIUM_ENCRYPTION"
    Set-MsolUserLicense -UserPrincipalName ProxyTest@contoso.com LicenseOptions $lo
    ```

       Atanan ServicePlans kümesindeki sonuçlar burada gösterilir.

    ```powershell
    (Get-MsolUser -UserPrincipalName ProxyTest@contoso.com).licenses | Select-Object -ExpandProperty ServiceStatus |sort ProvisioningStatus -Descending

    ServicePlan           ProvisioningStatus
    -----------           ------------------
    ATP_ENTERPRISE        PendingProvisioning
    MICROSOFT_SEARCH      PendingProvisioning
    INTUNE_O365           PendingActivation
    PAM_ENTERPRISE        Disabled
    EXCHANGE_ANALYTICS    Disabled
    EQUIVIO_ANALYTICS     Disabled
    THREAT_INTELLIGENCE   Disabled
    LOCKBOX_ENTERPRISE    Disabled
    PREMIUM_ENCRYPTION    Disabled
    EXCHANGE_S_ENTERPRISE Disabled
    INFORMATION_BARRIERS  Disabled
    MYANALYTICS_P2        Disabled
    MIP_S_CLP1            Disabled
    MIP_S_CLP2            Disabled
    ADALLOM_S_O365        PendingInput
    RMS_S_ENTERPRISE      Success
    YAMMER_ENTERPRISE     Success
    PROJECTWORKMANAGEMENT Success
    BI_AZURE_P2           Success
    WHITEBOARD_PLAN3      Success
    SHAREPOINTENTERPRISE  Success
    SHAREPOINTWAC         Success
    KAIZALA_STANDALONE    Success
    OFFICESUBSCRIPTION    Success
    MCOSTANDARD           Success
    Deskless              Success
    STREAM_O365_E5        Success
    FLOW_O365_P3          Success
    POWERAPPS_O365_P3     Success
    TEAMS1                Success
    MCOEV                 Success
    MCOMEETADV            Success
    BPOS_S_TODO_3         Success
    FORMS_PLAN_E5         Success
    SWAY                  Success
    ```

    Kullanıcının PrimarySMTPAddress'i artık temizlenmez. fabrikam.com etki alanı contoso.onmicrosoft.com kiracıya ait değildir ve dizinde gösterilen birincil SMTP adresi olarak kalır.

    Burada bir örnek verilmiştir.

    ```powershell
    Get-Recipient ProxyTest | Format-Table -AutoSize UserPrincipalName, PrimarySmtpAddress, ExternalEmailAddress, ExternalDirectoryObjectId
    UserPrincipalName               PrimarySmtpAddress              ExternalEmailAddress                 ExternalDirectoryObjectId
    -----------------               ------------------              --------------------                 -------------------------
    ProxyTest@fabrikam.com          ProxyTest@fabrikam.com          SMTP:ProxyTest@fabrikam.com          e2513482-1d5b-4066-936a-cbc7f8f6f817
    ```

    - Hedef kiracıya geçirilen şirket içi MailUser'lar için msExchRemoteRecipientType 8 (DeprovisionMailbox) olarak ayarlandığında, Azure'daki proxy temizleme mantığı sahip olunmayan etki alanlarını kaldırır ve primarySMTP'yi sahip olunan bir etki alanına sıfırlar. Şirket içi MailUser'da msExchRemoteRecipientType temizlenerek ara sunucu temizleme mantığı artık uygulanmaz.

      Aşağıda, Exchange Online içeren geçerli hizmet planlarının tamamı yer alır.

      | Name                                             |
      | ------------------------------------------------ |
      | eBulma (Premium) Depolama (500 GB)             |
      | Müşteri Kasası                                 |
      | Veri Kaybı Önleme                             |
      | Exchange Enterprise CAL Hizmetleri (EOP, DLP)      |
      | Exchange Temel Parçalar                              |
      | Exchange Vakfı                              |
      | Exchange Online (P1)                             |
      | Exchange Online (Plan 1)                         |
      | Exchange Online (Plan 2)                         |
      | Exchange Online için Exchange Online Arşivleme    |
      | Exchange Server için Exchange Online Arşivleme    |
      | Etkin Olmayan Kullanıcı Eklentisini Exchange Online             |
      | Exchange Online Kiosk                            |
      | Exchange Online Multi-Geo                        |
      | Exchange Online Plan 1                           |
      | Exchange Online POP                              |
      | Exchange Online Protection                       |
      | Bilgi Engelleri                             |
      | Office 365 için Information Protection - Premium  |
      | Office 365 için Information Protection - Standart |
      | MyAnalytics tarafından Analizler                          |
      | gelişmiş denetim Microsoft 365                  |
      | Microsoft Kayıtları                               |
      | Microsoft İş Merkezi                        |
      | Microsoft MyAnalytics (Tam)                     |
      | Office 365 eBulma (Premium)                   |
      | Office 365 için Microsoft Defender (Plan 1)       |
      | Office 365 için Microsoft Defender (Plan 2)       |
      | Ayrıcalıklı Erişim Yönetimi'ni Office 365          |
      | Office 365'da şifrelemeyi Premium                 |
