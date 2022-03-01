---
title: Resmi İzin Ver'i Algıla ve Düzeltmek
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.collection:
- o365_security_incident_response
- M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MET150
description: Bu izni tanımayı ve bu izni kabul etmeyi kabul etmeyi Microsoft 365.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: db401231a2db0bddf1115cbdf14ae14cc9897f57
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021805"
---
# <a name="detect-and-remediate-illicit-consent-grants"></a>Resmi İzin Ver'i Algıla ve Düzeltmek

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Özet**  Bu izni tanımayı ve bu izni kabul etmeyi kabul etmeyi Microsoft 365.

## <a name="what-is-the-illicit-consent-grant-attack-in-microsoft-365"></a>E-Microsoft 365'de resmi izin Microsoft 365?

Ücretsiz izin ver saldırılarında, saldırgan kişi bilgileri, e-posta veya belgeler gibi verilere erişim talep etmek için Azure tarafından kaydedilmiş bir uygulama oluşturur. Ardından saldırgan, son kullanıcıya kimlik avı saldırısı yoluyla ya da güvenilir bir web sitesine kötü amaçlı kod ekleme yoluyla bu uygulamaya izin vermek için püf noktaları sağlar. Bu illici uygulama izin verildikten sonra, kuruluş hesabına gerek kalmadan verilere hesap düzeyinde erişim sağlar. ihlal edildi hesaplarda parolaları sıfırlama veya hesaplarda Multi-Factor Authentication (MFA) gerektirme gibi normal düzeltme adımları, bu tür saldırılara karşı etkili değildir çünkü bunlar üçüncü taraf uygulamalardır ve kuruluşun dışındadır.

Bu saldırılar, bilgiyi çağıran varlığın bir insan değil otomasyon olduğunu kabul ediyor bir etkileşim modelinden yararlanmaktadır.

> [!IMPORTANT]
> Şu anda bir uygulamanın resmi olmayan onayları ile ilgili sorunlar yaşadığından şüpheleniyor musunuz? Bulut Uygulamaları için Microsoft Defender'da OAuth uygulamalarınızı algılamaya, araştırmaya ve düzeltmeye yardımcı olan araçlar vardır. Bulut Uygulamaları için Defender makalesinde, riskli OAuth uygulamalarını inceleme konusunda ana [hatlarıyla açıklanmıştır](/cloud-app-security/investigate-risky-oauth). Ayrıca, [OAuth uygulaması](/cloud-app-security/app-permission-policy) ilkelerini, bu uygulamaları kullanıcıların yetkilerini alan ve bu izin isteklerini yaygın olarak onaylayan veya yasaklayan uygulama izinlerini araştırmak üzere de ayarabilirsiniz.

## <a name="what-does-an-illicit-consent-grant-attack-look-like-in-microsoft-365"></a>Bu iznin kötü kullanımına izin vermek için verilen izin nasıl Microsoft 365?

Bu saldırının **Güvenlik Göstergeleri (** IOC) olarak da adlandırılan işaretleri bulmak için denetim günlüğünde aramanız gerekir. Azure'da kayıtlı birçok uygulama ve büyük bir kullanıcı tabanı olan kuruluşlar için en iyi uygulama, kuruluş izinlerini haftalık olarak gözden geçirmektir.

### <a name="steps-for-finding-signs-of-this-attack"></a>Bu saldırının işaretlerini bulma adımları

1. Microsoft 365 Defender portalını açın ve <https://security.microsoft.com> ardından Denetim'i **seçin**. Alternatif olarak, doğrudan **Denetim** sayfasına gitmek için <https://security.microsoft.com/auditlogsearch> seçeneğini kullanın.

2. Denetim **sayfasında** , Arama sekmesinin **seçili olduğunu** doğrulayın ve sonra aşağıdaki ayarları yapılandırabilirsiniz:
   - **Tarih ve saat aralığı**
   - **Etkinlikler**: Tüm **etkinlikler için sonuçları göster'in seçili** olduğunu doğrulayın.

   Bitirdiğinizde, **Ara**'yı tıklayın.

3. Sonuçları **sıralamak** ve Uygulama için İzin'i görmek için **Etkinlik sütununa tıklayın**.

4. Etkinlik ayrıntılarını görmek için listeden bir girdi seçin. IsAdminContent'in True olarak ayar olup olmadığını kontrol edin.

> [!NOTE]
>
> Bir olay sonrasında ilgili denetim günlüğü girdisini arama sonuçlarında 30 dakika ile 24 saat arasında sürebilir.
>
> Denetim kaydının denetim günlüğünde korunarak aranabilir olduğu süre Microsoft 365 aboneliğinize ve özel olarak belirli bir kullanıcıya atanan lisansın türüne bağlıdır. Daha fazla bilgi için bkz. [Denetim günlüğü](../../compliance/search-the-audit-log-in-security-and-compliance.md).
>
> Bu değer doğruysa, Genel Yönetici erişimi olan birinin verilere geniş erişim izni verilmiş olduğunu gösterir. Bu beklenmeyen bir durumsa saldırıyı onaylamak [için gerekli adımları izleyin](#how-to-confirm-an-attack).

## <a name="how-to-confirm-an-attack"></a>Saldırıyı onaylama

Yukarıda listelenen IOC'lerden bir veya daha fazla örneği varsa saldırının olduğunu olumlu olarak onaylamak için daha fazla araştırmanız gerekir. Saldırıyı onaylamak için şu üç yöntemden herhangi birini kullanabilirsiniz:

- Stok uygulamaları ve bu uygulamalara verilen izinler Azure Active Directory kullanın. Bu yöntem kapsamlıdır, ancak bir defada tek bir kullanıcıyı kontrol edin ve denetlemeniz gereken çok fazla kullanıcınız varsa bu yöntem çok fazla zaman alabilir.
- PowerShell kullanarak stok uygulamaları ve izinleri. Bu, en hızlı ve en kapsamlı yöntemdir ve en düşük yük miktarına sahiptir.
- Kullanıcılarınızı tek tek uygulamalarını ve izinlerini denetlemelerini ve düzeltme için sonuçları yöneticilere bildirmelerini sağlar.

## <a name="inventory-apps-with-access-in-your-organization"></a>Organizasyonda erişim olan stok uygulamaları

Bu, kullanıcılarınız için en iyi Azure Active Directory Portalı'Azure Active Directory PowerShell ile veya kullanıcılarının uygulama erişimlerini tek tek numaraya almalarını sebilirsiniz.

### <a name="steps-for-using-the-azure-active-directory-portal"></a>Kullanıcı Portalı'Azure Active Directory adımları

kullanıcı tarafından izin verilen uygulamaları, kullanıcı Portalı'nda Azure Active Directory bulabilirsiniz<https://portal.azure.com>.

1. Yönetim haklarıyla Azure portalında oturum açın.
2. Blade'Azure Active Directory seçin.
3. **Kullanıcılar**’ı seçin.
4. Gözden geçirmek istediğiniz kullanıcıya seçin.
5. **Uygulamalar**’ı seçin.

Bu size, kullanıcıya atanan uygulamaları ve uygulamaların sahip olduğu izinleri gösterir.

### <a name="steps-for-having-your-users-enumerate-their-application-access"></a>Kullanıcılarınızı uygulama erişimlerini numaraya aşağıdakilere göre numaraya alınma adımları

Kullanıcılarınızı oraya gidip kendi <https://myapps.microsoft.com> uygulama erişimlerini gözden geçirmelerini sağlar. Erişime sahip olan tüm uygulamaları görebilir, bunlar hakkında ayrıntıları (erişim kapsamı da içinde) görebilir ve şüpheli veya resmi olmayan uygulamalara olan ayrıcalıkları iptal edeebilirler.

### <a name="steps-for-doing-this-with-powershell"></a>PowerShell ile bunu yapma adımları

Illici [Get-AzureADPSPermissions.ps1](https://gist.github.com/psignoret/41793f8c6211d2df5051d77ca3728c09)t İzin Ver saldırısını doğrulamanın en basit yolu, kiralama süreniz içinde tüm OAuth izinlerini ve OAuth uygulamalarını tek bir .csv dosyasına yazar.

#### <a name="pre-requisites"></a>Önkoşullar

- Azure AD PowerShell kitaplığı yüklenir.
- Betiğin çalıştır çalıştırılamayacak kiracıda genel yönetici hakları.
- Betikleri çalıştıracak olan bilgisayarda Yerel Yönetici.

> [!IMPORTANT]
> Yönetim ***hesabınızla*** çok faktörlü kimlik doğrulaması gerektirmenizi kesinlikle öneririz. Bu betik, MFA kimlik doğrulamasını destekler.

1. Betiği çalıştıracakları bilgisayarda yerel yönetici haklarıyla oturum açın.

2. Bu betiği [Get-AzureADPSPermissions.ps1](https://gist.github.com/psignoret/41793f8c6211d2df5051d77ca3728c09) betiği GitHub betiği çalıştıracak olan klasöre indirin veya kopyalayın. Bu, "dosya çıktısı" dosyasının yazıldığı permissions.csv klasörü olur.

3. PowerShell oturumunu yönetici olarak açın ve betiği kaydedttiğinizi klasöre açın.

4. [Bağlan-AzureAD cmdlet'ini](/powershell/module/azuread/connect-azuread) Bağlan dizine seçin.

5. Bu PowerShell komutunu çalıştırın:

   ```powershell
   .\Get-AzureADPSPermissions.ps1 | Export-csv -Path "Permissions.csv" -NoTypeInformation
   ```

Betik, dosya adında bir Permissions.csv. Resmi olmayan uygulama izni verilenleri bakmak için şu adımları izleyin:

1. consentType sütununda (G sütunu), "AllPrinciples" değerini aratır. AllPrincipals izni, istemci uygulamasının kirada herkesin içeriğine erişmesini sağlar. Yerel Microsoft 365 uygulamaları doğru çalışması için bu izine ihtiyaç vardır. Bu izinle birlikte Microsoft olmayan her uygulama dikkatli bir şekilde gözden geçirilmelidir.

2. İzin sütununda (F sütunu), temsili olarak başvurulan her uygulamanın içerikle ilgili izinlerini gözden geçirebilirsiniz. "Okuma" ve "Yazma" iznini veya "*. Hepsi" iznini seçin ve uygun olmayacakları için bunları dikkatle gözden geçirin.

3. İzin verilmiş olan belirli kullanıcıları gözden geçirebilirsiniz. Yüksek profilli veya çok etkili kullanıcılar için uygunsuz izinler verilmişse, daha fazla araştırmanız gerekir.

4. ClientDisplayName sütununda (C sütunu), şüpheli görünen uygulamaları arama. Yanlış yazılmış adların, süper alan adlarının veya korsan adlarının olduğu uygulamalar dikkatle gözden geçirilmelidir.

## <a name="determine-the-scope-of-the-attack"></a>Saldırının kapsamını belirleme

Uygulama erişiminin envanterini tamamladikten sonra, ihlalin **tam** kapsamını belirlemek için denetim günlüğünü gözden geçirin. Etkilenen kullanıcıları, resmi uygulamanın kuruluşa erişimi olan zaman çerçevelerini ve uygulamanın sahip olduğu izinleri arama. Bu portalda **denetim günlüğünde** [Microsoft 365 Defender.](../../compliance/search-the-audit-log-in-security-and-compliance.md)

> [!IMPORTANT]
> [Yöneticiler ve kullanıcılar](../../compliance/enable-mailbox-auditing.md) [için posta kutusu denetimi](../../compliance/turn-audit-log-search-on-or-off.md) ve Etkinlik denetiminin, bu bilgileri alamanız için saldırıdan önce etkinleştirilmiş olması gerekir.

## <a name="how-to-stop-and-remediate-an-illicit-consent-grant-attack"></a>Resmi olmayan izin saldırısını durdurma ve düzeltme

Resmi olmayan izinleri olan bir uygulama belirledikten sonra, bu erişimi kaldırmak için çeşitli yollarınız vardır.

- Aşağıdakiler ile Başvuru Portalı'Azure Active Directory iptal edebilirsiniz:
  1. Son Kullanıcı Blade içinde etkilenen **Azure Active Directory** gidin.
  2. **Uygulamalar**’ı seçin.
  3. Resmi olmayan uygulamayı seçin.
  4. **Detaya gitmede** Kaldır'a tıklayın.

- [Remove-AzureADOAuth2PermissionGrant'daki](/powershell/module/azuread/Remove-AzureADOAuth2PermissionGrant) adımları takip edin ve PowerShell ile OAuth iznini iptal edin.

- [Remove-AzureADServiceAppRoleAssignment'daki](/powershell/module/azuread/Remove-AzureADServiceAppRoleAssignment) adımları takip ederek PowerShell ile Hizmet Uygulaması Rolü Atamasını iptal edin.

- Ayrıca, etkilenen hesapta oturum açma özelliğini de devre dışı abilirsiniz; böylece, hesapta verilere uygulama erişimi devre dışı olur. Bu kuşkusuz son kullanıcının üretkenliği için ideal değildir, ancak etkiyi hızla sınırlandıracak şekilde çalışıyorsanız, bu uygun bir kısa vadeli düzeltme olabilir.

- Kirayınız için tümleşik uygulamaları kapatabilirsiniz. Bu, son kullanıcıların kiracı genelinde izin verebilme yeteneğini devre dışı bırakmak için önemli bir adımdır. Bu, kullanıcılarınızı yanlışlıkla kötü amaçlı bir uygulamaya erişim izni verilmesini sağlar. Bu, kullanıcılarınızı üçüncü taraf uygulamalarda üretken hale getirirken ciddi bir engel olduğu için bu kesinlikle önerilmez. Bunu yapmak için Tümleşik Uygulamaları Açma veya [Kapatma'daki adımları izleyin](../../admin/misc/user-consent.md).

## <a name="secure-microsoft-365-like-a-cybersecurity-pro"></a>Siber Microsoft 365 gibi güvenliği sağlama

Microsoft 365 aboneliğiniz, verilerinizi ve kullanıcılarınızı korumak için kullanabileceğiniz güçlü bir güvenlik özellikleri kümesiyle gelir. Güvenlik [Microsoft 365 kullanın - İlk 30 gün, 90](security-roadmap.md) gün ve bundan sonra Microsoft'un kiracı kiracının güvenliğini sağlamak için önerilen en iyi yöntemleri uygulamak için Microsoft 365 vardır.

- İlk 30 gün içinde yerine gelen görevler. Bunlar hemen etkiler ve kullanıcılarınız için düşük etki sağlar.
- 90 gün içinde yapılacak görevler. Bunlar planlamak ve uygulamak için biraz daha zaman alır ama güvenlik performansını büyük ölçüde geliştirin.
- 90 gün dışında. Bu iyileştirmeler ilk 90 gün çalışmanıza dahil.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulamalarım listesinde beklenmeyen uygulama,](/azure/active-directory/application-access-unexpected-application) verilere erişimi olan beklenmeyen uygulamalar olduğunu fark eden yöneticilere, yapmak istemeleri gereken çeşitli işlemler konusunda yol sunar.
- [Uygulamaları izinlerle Azure Active Directory](/azure/active-directory/active-directory-apps-permissions-consent), izinlere ve izinlere üst düzey bir genel bakıştır.
- [Uygulamamı geliştirmekle ilgili](/azure/active-directory/active-directory-application-dev-development-content-map) sorunlar çeşitli izinlerle ilgili makalelerin bağlantılarını sağlar.
- [Azure Active Directory'daki (Azure AD)](/azure/active-directory/develop/active-directory-application-objects) uygulama ve hizmet sorumlusu nesneleri, uygulama modelini temel alan Uygulama ve Hizmet sorumlusu nesnelerine genel bir bakış sağlar.
- [Uygulamalara erişimi yönetme](/azure/active-directory/active-directory-managing-access-to-apps) , yöneticilerin uygulamalara kullanıcı erişimini yönetmesi gereken özelliklere genel bir bakışdır.
