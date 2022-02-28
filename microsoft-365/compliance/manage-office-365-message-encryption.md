---
title: Office 365 İleti Şifrelemesi
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 5/8/2019
search.appverid:
- MET150
ms.assetid: 09f6737e-f03f-4bc8-8281-e46d24ee2a74
ms.collection:
- Strat_O365_IP
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Web Hizmetleri (OME) Office 365 İleti Şifrelemesi sonra dağıtımınızı çeşitli yollarla özelleştirmeyi öğrenin.
ms.openlocfilehash: c402b5f414e81fbb7403d56a7314c9255c8cf1b4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985031"
---
# <a name="manage-office-365-message-encryption"></a>Office 365 İleti Şifrelemesi

Office 365 İleti Şifrelemesi (OME) ayarlarını bitirdikten sonra, dağıtımın yapılandırmasını çeşitli yollarla özelleştirebilirsiniz. Örneğin, tek seferlik geçiş kodlarının etkinleştirip etkinleştirmeyeceği, Kodlar ve  Daha fazlası için Şifrele Web üzerinde Outlook yapılandırabilirsiniz. Bu makaledeki görevlerde bunun nasıl olduğu açıklanmıştır.

## <a name="manage-whether-google-yahoo-and-microsoft-account-recipients-can-use-these-accounts-to-sign-in-to-the-office-365-message-encryption-portal"></a>Google, Yahoo ve Microsoft Hesabı alıcılarından bu hesapları kullanarak portalda oturum açma Office 365 İleti Şifrelemesi yönetme

Yeni özellik özelliklerini Office 365 İleti Şifrelemesi, kuruluş dışındaki alıcılara ileti gönderebilir. Alıcı Google hesabı, Yahoo  hesabı veya Microsoft hesabı gibi bir sosyal kimlik kullanıyorsa, alıcı sosyal kimlikle OME portalında oturum açın. Alıcının, sosyal kimlikleri kullanarak OME portalında oturum açmasına izin vermeyebilirsiniz.
  
### <a name="to-manage-whether-recipients-can-use-social-ids-to-sign-in-to-the-ome-portal"></a>Alıcıların sosyal kimlikleri kullanarak OME portalında oturum açmasını yönetme
  
1. [Bağlan PowerShell Exchange Online'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

2. Set-OMEConfiguration cmdlet'ini SocialIdSignIn parametresiyle aşağıdaki gibi çalıştırın:

   ```powershell
   Set-OMEConfiguration -Identity <"OMEConfigurationIdParameter"> -SocialIdSignIn <$true|$false>
   ```

   Örneğin, sosyal kimlikleri devre dışı bırakmak için:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -SocialIdSignIn $false
   ```

   Sosyal kimlikleri etkinleştirmek için:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -SocialIdSignIn $true
   ```

## <a name="manage-the-use-of-one-time-pass-codes-for-the-office-365-message-encryption-portal"></a>Geçiş portalı için tek kullanımlık geçiş kodlarının Office 365 İleti Şifrelemesi yönetme

OME tarafından şifrelenmiş bir iletinin alıcısı Outlook kullanmazsa, alıcı tarafından kullanılan hesap ne olursa olsun, iletiyi okumalarına olanak sağlayan sınırlı bir web görünümü bağlantısı alır. Bu bağlantı tek seferlik bir geçiş kodu içerir. Yönetici olarak, alıcıların OME portalında oturum aya tek kullanımlık geçiş kodlarını kullanarak oturum açmasına karar veabilirsiniz.
  
### <a name="to-manage-whether-ome-generates-one-time-pass-codes"></a>OME'nin tek seferlik geçiş kodları oluşturması ile ilgili yönetimi
  
1. Kuruluşta genel yönetici izinleri olan bir iş veya okul hesabı kullanın ve yeni bir oturum Windows PowerShell oturum açın ve Exchange Online. Yönergeler için bkz. [Bağlan PowerShell'Exchange Online yükleme](/powershell/exchange/connect-to-exchange-online-powershell).

2. Set-OMEConfiguration cmdlet'ini OTPEnabled parametresiyle çalıştırın:

   ```powershell
   Set-OMEConfiguration -Identity <"OMEConfigurationIdParameter"> -OTPEnabled <$true|$false>
   ```

   Örneğin, tek seferlik geçiş kodlarını devre dışı bırakmak için:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -OTPEnabled $false
   ```

   Tek seferlik geçiş kodlarını etkinleştirmek için:

   ```powershell
   Set-OMEConfiguration -Identity "OME Configuration" -OTPEnabled $true
   ```

## <a name="manage-the-display-of-the-encrypt-button-in-outlook-on-the-web"></a>E-postada Şifrele düğmesinin görüntülenme Web üzerinde Outlook

Yönetici olarak, bu düğmenin son kullanıcılara görüntüleniyor olup olmadığını yönetebilirsiniz.
  
### <a name="to-manage-whether-the-encrypt-button-appears-in-outlook-on-the-web"></a>Şifrele düğmesinin dosyada görüntülendiğinden Web üzerinde Outlook
  
1. Kuruluşta genel yönetici izinleri olan bir iş veya okul hesabı kullanın ve yeni bir oturum Windows PowerShell oturum açın ve Exchange Online. Yönergeler için bkz. [Bağlan PowerShell'Exchange Online yükleme](/powershell/exchange/connect-to-exchange-online-powershell).

2. Set-IRMConfiguration cmdlet'ini -SimplifiedClientAccessEnabled parametresiyle çalıştırın:

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled <$true|$false>
   ```

   Örneğin, Şifrele düğmesini devre **dışı bırakmak** için:

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $false
   ```

   Şifrele düğmesini **etkinleştirmek** için:

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $true
   ```

## <a name="enable-service-side-decryption-of-email-messages-for-ios-mail-app-users"></a>iOS posta uygulaması kullanıcıları için e-posta iletilerinin hizmet tarafındaki şifre çözmeyi etkinleştirme

iOS posta uygulaması, parola korumalı iletilerin şifresini çöz Office 365 İleti Şifrelemesi. Yönetici Microsoft 365 olarak, iOS posta uygulamasına teslim edilen iletiler için hizmet tarafındaki şifre çözmeyi uygulayabilirsiniz. Hizmet tarafında şifre çözmeyi kullanmayı tercih ettiyken, hizmet iOS cihazına iletinin bir şifresi çözülmüş kopyasını gönderir. İstemci cihaz iletinin şifresini çözmüş bir kopyasını depolar. Ayrıca iOS posta uygulaması kullanıcıya istemci tarafı kullanım hakları uygulamasa da, iletide kullanım haklarıyla ilgili bilgiler korunur. Başlangıçta iletiyi kopyalama hakları yoksa bile kullanıcı iletiyi kopyalayıp yazdırabilirsiniz. Bununla birlikte, kullanıcı Microsoft 365 posta sunucusunu gerektiren bir eylemi (iletiyi iletme gibi) tamamlamaya çalışırsa, kullanıcı aslında bunu yapmak için gerekli kullanım iznine sahip yoksa, sunucu eyleme izin vermez. Bununla birlikte, son kullanıcılar iletiyi iOS posta uygulaması içinde farklı bir hesaptan ileterek "İtelama" kullanım kısıtlaması üzerinde çalışabilirsiniz. Postanın hizmet tarafında şifre çözmeyi ayar isteyip ayarlamamış olursanız olun, şifrelenmiş posta ekleri ve hakları korunan posta ekleri iOS posta uygulamasında görüntüilemez.
  
Şifre çözülmüş iletilerin iOS posta uygulaması kullanıcılarına gönderilmesine izin vermeyebilirsiniz; kullanıcılara iletiyi görüntüleme hakları olmadığının bir ileti gönderilir. Varsayılan olarak, e-posta iletilerinin hizmet tarafında şifre çözme etkin değildir.
  
Daha fazla bilgi ve istemci deneyiminin görünümü için bkz. E-posta [iletilerinizin iPhone iPad](https://support.microsoft.com/en-us/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf).
  
### <a name="to-manage-whether-ios-mail-app-users-can-view-messages-protected-by-office-365-message-encryption"></a>iOS posta uygulaması kullanıcılarının korumalı iletileri iOS posta uygulaması tarafından görüntü edip Office 365 İleti Şifrelemesi
  
1. Kuruluşta genel yönetici izinleri olan bir iş veya okul hesabı kullanın ve yeni bir oturum Windows PowerShell oturum açın ve Exchange Online. Yönergeler için bkz. [Bağlan PowerShell'Exchange Online yükleme](/powershell/exchange/connect-to-exchange-online-powershell).

2. Set-ActiveSyncOrganizations cmdlet'ini AllowRMSSupportForUnenlightenedApps parametresiyle çalıştırın:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps <$true|$false>
   ```

   Örneğin, iOS posta uygulaması gibi planlanmamış uygulamalara gönderilmeden önce iletilerin şifresini çözecek şekilde hizmeti yapılandırmak için:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps $true
   ```

   Ya da hizmeti, şifre çözülmüş iletilerin,lightedilen uygulamalara gönderilene kadar göndermeyecek şekilde yapılandırmak için:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps $false
   ```

> [!NOTE]
> Tek tek posta kutusu ilkeleri (OWA/ActiveSync) bu ayarları geçersiz kılar (örneğin, ilgili OWA Posta Kutusu ilkesi veya ActiveSync Posta Kutusu ilkesi içinde -IRMEnabled False olarak ayarlanırsa, bu yapılandırmalar geçerli olmaz).

## <a name="enable-service-side-decryption-of-email-attachments-for-web-browser-mail-clients"></a>Web tarayıcısı posta istemcileri için e-posta eklerinin hizmet tarafındaki şifre çözmeyi etkinleştirme

Normalde, ileti şifrelemesi Office 365 ekler otomatik olarak şifrelenir. Yönetici olarak, kullanıcıların web tarayıcısında indirebilecekleri e-posta ekleri için hizmet tarafında şifre çözme uygulayabilirsiniz.
  
Hizmet tarafında şifre çözmeyi kullanırsanız, hizmet dosyanın bir şifre çözülmüş kopyasını cihaza gönderir. İleti hala şifrelenmiş olarak devam ediyor. Tarayıcı kullanıcıya istemci tarafı kullanım hakları uygulamasa da, e-posta eki kullanım haklarıyla ilgili bilgileri tutar. Başlangıçta bu haklara sahip değil olsalar bile kullanıcı e-posta eklerini kopyalayıp yazdırabilirsiniz. Bununla birlikte, kullanıcı Microsoft 365 posta sunucusunu gerektiren eki iletme gibi bir eylemi tamamlamaya çalışırsa, kullanıcı aslında bunu yapmak için gerekli kullanım iznine sahip yoksa sunucu eyleme izin vermez.
  
Eklerin hizmet tarafında şifre çözmeyi ayarip ayarlamamasanız da, kullanıcılar iOS posta uygulamasında şifrelenmiş e-postalara ve hak korunan postalara hiçbir ek görüntüleyemz.
  
Şifresini çözülmüş e-posta eklerine izin vermeyebilirsiniz (bu varsayılan ayardır). Kullanıcılara, eki görüntüleme hakları olmadığının bir ileti gönderilir.
  
E-postalar ve e-Microsoft 365 şifrelemeyi en iyi şekilde uygulama hakkında daha fazla bilgi Encrypt-Only için bkz. [E-postalar için Yalnızca Şifrele seçeneği.](/azure/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails)
  
### <a name="to-manage-whether-email-attachments-are-decrypted-on-download-from-a-web-browser"></a>Web tarayıcısında indirilen e-posta eklerin şifresinin çözülmüş olup olmadığını yönetmek için
  
1. Kuruluşta genel yönetici izinleri olan bir iş veya okul hesabı kullanın ve yeni bir oturum Windows PowerShell oturum açın ve Exchange Online. Yönergeler için bkz. [Bağlan PowerShell'Exchange Online yükleme](/powershell/exchange/connect-to-exchange-online-powershell).

2. Şu cmdletSet-IRMConfiguration IncryptAttachmentForEncryptOnly parametresiyle çalıştırın:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly <$true|$false>
   ```

   Örneğin, kullanıcı web tarayıcısında e-posta eklerini indirirken e-posta eklerin şifresini çözecek şekilde hizmeti yapılandırmak için:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true
   ```

   Hizmeti, şifrelenmiş e-posta eklerini indirildikleri gibi bırakılacak şekilde yapılandırmak için:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $false
   ```

## <a name="ensure-all-external-recipients-use-the-ome-portal-to-read-encrypted-mail"></a>Tüm dış alıcıların şifreli postayı okumak için OME Portalı'nın kullanmaya özen gösterme

Alıcıları oME Portalı'nın şifreli e-postalarını okumaya yönlendiren bir paket postası almaya zorlamak için, özel markalama Outlook veya Web üzerinde Outlook. Alıcıların alacakları postaları nasıl kullanmaları üzerinde daha fazla denetime sahip olmak istemeniz gerekir. Örneğin, dış alıcılar web portalında e-postayı görüntüıyorsa, e-posta için son kullanma tarihi ayarlayabilecek ve e-postayı iptal edebilirsiniz. Bu özellikler yalnızca OME Portalı aracılığıyla destekler. Posta akışı kurallarını oluştururken Şifrele seçeneğini ve İleri gönderme seçeneğini kullanabilirsiniz.

### <a name="use-a-custom-template-to-force-all-external-recipients-to-use-the-ome-portal-and-for-encrypted-email"></a>Tüm dış alıcıları OME Portalını kullanmaya ve şifreli e-posta kullanmaya zorlamak için özel bir şablon kullanma

1. Kuruluşta genel yönetici izinleri olan bir iş veya okul hesabı kullanın ve yeni bir oturum Windows PowerShell oturum açın ve Exchange Online. Yönergeler için bkz. [Bağlan PowerShell'Exchange Online yükleme](/powershell/exchange/connect-to-exchange-online-powershell).

2. New-TransportRule cmdlet'ini çalıştırın:

   ```powershell
   New-TransportRule -name "<mail flow rule name>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "<option name>" -ApplyRightsProtectionCustomizationTemplate "<template name>"
   ```

    burada:

   - `mail flow rule name` yeni posta akışı kuralı için kullanmak istediğiniz addır.

   - `option name` ya da `Encrypt` `Do Not Forward`.

   - `template name` , özel markalama şablonuna vermek istediğiniz addır `OME Configuration`.

   Tüm dış e-postaları "OME Yapılandırması" şablonuyla şifrelemek ve Encrypt-Only uygulamak için:

   ```powershell
   New-TransportRule -name "<All outgoing mail>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "Encrypt" -ApplyRightsProtectionCustomizationTemplate "OME Configuration"
   ```

   Tüm dış e-postaları "OME Yapılandırması" şablonuyla şifrelemek ve İtememe seçeneğini uygulamak için:

   ```powershell
   New-TransportRule -name "<All outgoing mail>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "Do Not Forward" -ApplyRightsProtectionCustomizationTemplate "OME Configuration"
   ```

## <a name="customize-the-appearance-of-email-messages-and-the-ome-portal"></a>E-posta iletilerinin ve OME portalının görünümünü özelleştirme

OME'yi organizasyonunız için nasıl özelleştirebileceğiniz hakkında ayrıntılı bilgi için bkz. Şifreli [iletilerinize kuruluş markasını ekleme](add-your-organization-brand-to-encrypted-messages.md).
  
## <a name="disable-the-new-capabilities-for-ome"></a>OME için yeni özellikleri devre dışı bırakma

Umarız buna gelmedir, ancak gerekirse OME'nin yeni özelliklerini devre dışı bırakmak çok basittir. İlk olarak, yeni OME özelliklerini kullanan oluşturduğunuz tüm posta akış kurallarını kaldırmanız gerekir. Posta akış kurallarını kaldırma hakkında bilgi için bkz. [Posta akışı kurallarını yönetme](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules). Ardından, bu adımları Exchange Online PowerShell'de tamamlayın.
  
### <a name="to-disable-the-new-capabilities-for-ome"></a>OME'nin yeni özelliklerini devre dışı bırakmak için
  
1. Kuruluşta genel yönetici izinleri olan bir iş veya okul hesabı kullanarak yeni bir oturum Windows PowerShell bu hesaba bağlanarak Exchange Online. Yönergeler için bkz. [Bağlan PowerShell'Exchange Online yükleme](/powershell/exchange/connect-to-exchange-online-powershell).

2. Şifreleme düğmesi etkinleştirilmişse, Web üzerinde Outlook ClientAccessEnabled parametresiyle Set-IRMConfiguration cmdlet'ini çalıştırarak düğmeyi devre dışı bırakın. Aksi takdirde bu adımı atlayabilirsiniz.

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $false
   ```

3. AzureRMSLicensingEnabled parametresi false olarak ayarlanmış Set-IRMConfiguration cmdlet'ini çalıştırarak OME'nin yeni özelliklerini devre dışı bırakma:

   ```powershell
   Set-IRMConfiguration -AzureRMSLicensingEnabled $false
   ```
