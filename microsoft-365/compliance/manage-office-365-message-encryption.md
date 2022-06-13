---
title: Office 365 İleti Şifrelemesini yönetme
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 03/04/2022
search.appverid:
- MET150
ms.assetid: 09f6737e-f03f-4bc8-8281-e46d24ee2a74
ms.collection:
- Strat_O365_IP
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Office 365 İleti Şifrelemesi'ni (OME) ayarlamayı tamamladıktan sonra dağıtımınızı çeşitli yollarla özelleştirmeyi öğrenin.
ms.openlocfilehash: 2e39f811ec23b2f3b068ef5684fca479850a8744
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014838"
---
# <a name="manage-office-365-message-encryption"></a>Office 365 İleti Şifrelemesini yönetme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Office 365 İleti Şifrelemesi'ni (OME) ayarlamayı tamamladıktan sonra, dağıtımınızın yapılandırmasını çeşitli yollarla özelleştirebilirsiniz. Örneğin, tek seferlik geçiş kodlarının etkinleştirilip etkinleştirilmeyebileceğini yapılandırabilir, **şifrele** düğmesini Web üzerinde Outlook ve daha fazlasını görüntüleyebilirsiniz. Bu makaledeki görevler nasıl yapılacağını açıklar.

## <a name="manage-whether-google-yahoo-and-microsoft-account-recipients-can-use-these-accounts-to-sign-in-to-the-office-365-message-encryption-portal"></a>Google, Yahoo ve Microsoft Hesabı alıcılarının Office 365 İleti Şifreleme portalında oturum açmak için bu hesapları kullanıp kullanamayacağını yönetin

Yeni Office 365 İleti Şifrelemesi özelliklerini ayarladığınızda, kuruluşunuzdaki kullanıcılar kuruluşunuzun dışındaki alıcılara ileti gönderebilir. Alıcı Google hesabı, Yahoo hesabı veya Microsoft hesabı gibi bir *sosyal kimlik* kullanıyorsa, alıcı OME portalında sosyal kimlikle oturum açabilir. İsterseniz, alıcıların OME portalında oturum açmak için sosyal kimlik kullanmasına izin vermemeyi seçebilirsiniz.

### <a name="to-manage-whether-recipients-can-use-social-ids-to-sign-in-to-the-ome-portal"></a>Alıcıların OME portalında oturum açmak için sosyal kimlikleri kullanıp kullanamayacağını yönetmek için

1. [PowerShell'i Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell).

2. SocialIdSignIn parametresiyle Set-OMEConfiguration cmdlet'ini aşağıdaki gibi çalıştırın:

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

## <a name="manage-the-use-of-one-time-pass-codes-for-the-office-365-message-encryption-portal"></a>Office 365 İleti Şifreleme portalı için tek seferlik geçiş kodlarının kullanımını yönetme

OME tarafından şifrelenen bir iletinin alıcısı, alıcı tarafından kullanılan hesaba bakılmaksızın Outlook kullanmıyorsa, alıcı iletiyi okumasına olanak tanıyan sınırlı süreli bir web görünümü bağlantısı alır. Bu bağlantı tek seferlik bir geçiş kodu içerir. Yönetici olarak, alıcıların OME portalında oturum açmak için tek seferlik geçiş kodlarını kullanıp kullanamadığını seçebilirsiniz.

### <a name="to-manage-whether-ome-generates-one-time-pass-codes"></a>OME'nin tek seferlik geçiş kodları oluşturup oluşturmadığını yönetmek için

1. Kuruluşunuzda genel yönetici izinlerine sahip bir iş veya okul hesabı kullanın ve Exchange Online PowerShell'e bağlanın. Yönergeler için bkz. [Exchange Online PowerShell'e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

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

## <a name="manage-the-display-of-the-encrypt-button-in-outlook-on-the-web"></a>Web üzerinde Outlook'de Şifrele düğmesinin görünümünü yönetme

Yönetici olarak, bu düğmenin son kullanıcılara görüntülenip görüntülenmeyeceğini yönetebilirsiniz.

### <a name="to-manage-whether-the-encrypt-button-appears-in-outlook-on-the-web"></a>Şifrele düğmesinin Web üzerinde Outlook

1. Kuruluşunuzda genel yönetici izinlerine sahip bir iş veya okul hesabı kullanın ve Exchange Online PowerShell'e bağlanın. Yönergeler için bkz. [Exchange Online PowerShell'e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

2. Set-IRMConfiguration cmdlet'ini -SimplifiedClientAccessEnabled parametresiyle çalıştırın:

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled <$true|$false>
   ```

   Örneğin, **Şifrele** düğmesini devre dışı bırakmak için:

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $false
   ```

   **Şifrele** düğmesini etkinleştirmek için:

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $true
   ```

## <a name="enable-service-side-decryption-of-email-messages-for-ios-mail-app-users"></a>iOS posta uygulaması kullanıcıları için e-posta iletilerinin hizmet tarafı şifre çözmesini etkinleştirme

iOS posta uygulaması, Office 365 İleti Şifrelemesi ile korunan iletilerin şifresini çözemez. Microsoft 365 yöneticisi olarak, iOS posta uygulamasına teslim edilen iletiler için hizmet tarafı şifre çözme uygulayabilirsiniz. Hizmet tarafı şifre çözmeyi kullanmayı seçtiğinizde, hizmet iletinin şifresi çözülmüş bir kopyasını iOS cihaza gönderir. İstemci cihazı, iletinin şifresi çözülmüş bir kopyasını depolar. ayrıca iOS posta uygulaması kullanıcıya istemci tarafı kullanım hakları uygulamasa bile ileti kullanım hakları hakkındaki bilgileri korur. Kullanıcı, başlangıçta bu haklara sahip olmasa bile iletiyi kopyalayabilir veya yazdırabilir. Ancak, kullanıcı Microsoft 365 posta sunucusu gerektiren bir eylemi (örneğin, iletiyi iletmeyi) tamamlamaya çalışırsa, kullanıcının başlangıçta kullanım hakkı yoksa sunucu eyleme izin vermez. Ancak son kullanıcılar, iletiyi iOS posta uygulamasındaki farklı bir hesaptan ileterek "İletme" kullanım kısıtlamasını geçici olarak düzeltebilir. Postanın hizmet tarafı şifre çözmesini ayarlayıp ayarlamadığınıza bakılmaksızın, şifrelenmiş ve hak korumalı posta ekleri iOS posta uygulamasında görüntülenemez.

Şifresi çözülmüş iletilerin iOS posta uygulaması kullanıcılarına gönderilmesine izin vermemeyi seçerseniz, kullanıcılar iletiyi görüntüleme hakları olmadığını belirten bir ileti alır. Varsayılan olarak, e-posta iletilerinin hizmet tarafı şifre çözmesi etkinleştirilmez.

Daha fazla bilgi ve istemci deneyiminin görünümü için bkz. [iPhone veya iPad şifrelenmiş iletileri görüntüleme](https://support.microsoft.com/en-us/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf).

### <a name="to-manage-whether-ios-mail-app-users-can-view-messages-protected-by-office-365-message-encryption"></a>iOS posta uygulaması kullanıcılarının Office 365 İleti Şifrelemesi ile korunan iletileri görüntüleyip görüntüleyemeyeceğini yönetmek için

1. Kuruluşunuzda genel yönetici izinlerine sahip bir iş veya okul hesabı kullanın ve Exchange Online PowerShell'e bağlanın. Yönergeler için bkz. [Exchange Online PowerShell'e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

2. allowRMSSupportForUnenlightenedApps parametresiyle Set-ActiveSyncOrganizations cmdlet'ini çalıştırın:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps <$true|$false>
   ```

   Örneğin, hizmeti iOS posta uygulaması gibi ışıksız uygulamalara gönderilmeden önce iletilerin şifresini çözecek şekilde yapılandırmak için:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps $true
   ```

   Veya hizmeti, şifresi çözülmüş iletilerin ışıksız uygulamalara gönderilmemesi için yapılandırmak için:

   ```powershell
   Set-ActiveSyncOrganizationSettings -AllowRMSSupportForUnenlightenedApps $false
   ```

> [!NOTE]
> Tek tek posta kutusu ilkeleri (OWA/ActiveSync) bu ayarları geçersiz kılar (örneğin, ilgili OWA Posta Kutusu ilkesi veya ActiveSync Posta Kutusu ilkesi içinde -IRMEnabled False olarak ayarlanırsa, bu yapılandırmalar geçerli olmaz).

## <a name="enable-service-side-decryption-of-email-attachments-for-web-browser-mail-clients"></a>Web tarayıcısı posta istemcileri için e-posta eklerinin hizmet tarafı şifre çözmesini etkinleştirme

Normalde, Office 365 ileti şifrelemesi kullandığınızda ekler otomatik olarak şifrelenir. Yönetici olarak, kullanıcıların bir web tarayıcısından indirdiği e-posta ekleri için hizmet tarafı şifre çözme uygulayabilirsiniz.

Hizmet tarafı şifre çözmeyi kullandığınızda, hizmet dosyanın şifresi çözülmüş bir kopyasını cihaza gönderir. İleti hala şifrelenmiştir. Tarayıcı kullanıcıya istemci tarafı kullanım hakları uygulamasa bile e-posta eki kullanım hakları hakkında bilgi de tutar. Kullanıcı, başlangıçta bu haklara sahip olmasa bile e-posta ekini kopyalayabilir veya yazdırabilir. Ancak, kullanıcı ekin iletilmesi gibi Microsoft 365 posta sunucusunu gerektiren bir eylemi tamamlamaya çalışırsa, kullanıcının başlangıçta kullanım hakkı yoksa sunucu eyleme izin vermez.

Eklerin hizmet tarafı şifre çözmesini ayarlayıp ayarlamadığınıza bakılmaksızın, kullanıcılar iOS posta uygulamasında şifrelenmiş ve hak korumalı posta eklerini görüntüleyemez.

Şifresi çözülmüş e-posta eklerine izin vermemeyi seçerseniz (varsayılan değer budur), kullanıcılar eki görüntüleme hakları olmadığını belirten bir ileti alır.

Microsoft 365 Encrypt-Only seçeneğiyle e-postalar ve e-posta ekleri için şifrelemeyi nasıl uyguladığı hakkında daha fazla bilgi için bkz[. E-postalar için Yalnızca şifreleme seçeneği.](/azure/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails)

### <a name="to-manage-whether-email-attachments-are-decrypted-on-download-from-a-web-browser"></a>Web tarayıcısından indirildiğinde e-posta eklerinin şifresinin çözülmüş olup olmadığını yönetmek için

1. Kuruluşunuzda genel yönetici izinlerine sahip bir iş veya okul hesabı kullanın ve Exchange Online PowerShell'e bağlanın. Yönergeler için bkz. [Exchange Online PowerShell'e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

2. DecryptAttachmentForEncryptOnly parametresiyle Set-IRMConfiguration cmdlet'ini çalıştırın:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly <$true|$false>
   ```

   Örneğin, bir kullanıcı bunları bir web tarayıcısından indirdiğinde hizmeti e-posta eklerinin şifresini çözecek şekilde yapılandırmak için:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true
   ```

   Hizmeti, şifrelenmiş e-posta eklerini indirildiğinde olduğu gibi bırakacak şekilde yapılandırmak için:

   ```powershell
   Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $false
   ```

## <a name="ensure-all-external-recipients-use-the-ome-portal-to-read-encrypted-mail"></a>Tüm dış alıcıların şifrelenmiş postaları okumak için OME Portalını kullandığından emin olun

Alıcıları Outlook veya Web üzerinde Outlook kullanmak yerine OME Portalı'nda şifrelenmiş e-postaları okumaya yönlendiren bir sarmalayıcı posta almaya zorlamak için özel markalama şablonları kullanabilirsiniz. Kullanıyorsanız, alıcıların aldıkları postayı nasıl kullandığı üzerinde daha fazla denetim sahibi olmak istiyorsanız bunu yapmak isteyebilirsiniz. Örneğin, dış alıcılar e-postayı web portalında görüntülediyse, e-posta için bir sona erme tarihi ayarlayabilir ve e-postayı iptal edebilirsiniz. Bu özellikler yalnızca OME Portalı aracılığıyla desteklenir. Posta akışı kurallarını oluştururken Şifrele seçeneğini ve İletme seçeneğini kullanabilirsiniz.

### <a name="use-a-custom-template-to-force-all-external-recipients-to-use-the-ome-portal-and-for-encrypted-email"></a>Tüm dış alıcıları OME Portalı'nı ve şifrelenmiş e-postaları kullanmaya zorlamak için özel bir şablon kullanın

1. Kuruluşunuzda genel yönetici izinlerine sahip bir iş veya okul hesabı kullanın ve Exchange Online PowerShell'e bağlanın. Yönergeler için bkz. [Exchange Online PowerShell'e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

2. New-TransportRule cmdlet'ini çalıştırın:

   ```powershell
   New-TransportRule -name "<mail flow rule name>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "<option name>" -ApplyRightsProtectionCustomizationTemplate "<template name>"
   ```

    Nerede:

   - `mail flow rule name` , yeni posta akışı kuralı için kullanmak istediğiniz addır.

   - `option name` veya `Encrypt` `Do Not Forward`şeklindedir.

   - `template name` , örneğin özel markalama şablonuna `OME Configuration`verdiğiniz addır.

   Tüm dış e-postaları "OME Yapılandırması" şablonuyla şifrelemek ve Encrypt-Only seçeneğini uygulamak için:

   ```powershell
   New-TransportRule -name "<All outgoing mail>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "Encrypt" -ApplyRightsProtectionCustomizationTemplate "OME Configuration"
   ```

   Tüm dış e-postaları "OME Yapılandırması" şablonuyla şifrelemek ve İletme seçeneğini uygulamak için:

   ```powershell
   New-TransportRule -name "<All outgoing mail>" -FromScope "InOrganization" -ApplyRightsProtectionTemplate "Do Not Forward" -ApplyRightsProtectionCustomizationTemplate "OME Configuration"
   ```

## <a name="customize-the-appearance-of-email-messages-and-the-ome-portal"></a>E-posta iletilerinin ve OME portalının görünümünü özelleştirme

Kuruluşunuz için Microsoft Purview İleti Şifrelemesini nasıl özelleştirebileceğiniz hakkında ayrıntılı bilgi için bkz. [Şifrelenmiş iletilerinize kuruluşunuzun markasını ekleme](add-your-organization-brand-to-encrypted-messages.md). Şifrelenmiş iletileri izleme ve iptal etme özelliğini etkinleştirmek için özel markanızı OME portalına eklemeniz gerekir.

## <a name="disable-microsoft-purview-message-encryption"></a>Microsoft Purview İleti Şifrelemesini Devre Dışı Bırakma

Bunun işe yaramaz olduğunu umuyoruz, ancak gerekirse Microsoft Purview İleti Şifrelemesi'nin devre dışı bırakılması çok basittir. İlk olarak, Oluşturduğunuz ve Microsoft Purview İleti Şifrelemesi kullanan tüm posta akışı kurallarını kaldırmanız gerekir. Posta akışı kurallarını kaldırma hakkında bilgi için bkz. [Posta akışı kurallarını yönetme](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules). Ardından powershell Exchange Online bu adımları tamamlayın.

### <a name="to-disable-microsoft-purview-message-encryption"></a>Microsoft Purview İleti Şifrelemesini devre dışı bırakmak için

1. Kuruluşunuzda genel yönetici izinlerine sahip bir iş veya okul hesabı kullanarak Exchange Online PowerShell'e bağlanın. Yönergeler için bkz. [Exchange Online PowerShell'e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

2. Web üzerinde Outlook'de **Şifrele** düğmesini etkinleştirdiyseniz, BasitleştirilmişClientAccessEnabled parametresiyle Set-IRMConfiguration cmdlet'ini çalıştırarak devre dışı bırakın. Aksi takdirde bu adımı atlayın.

   ```powershell
   Set-IRMConfiguration -SimplifiedClientAccessEnabled $false
   ```

3. AzureRMSLicensingEnabled parametresi false olarak ayarlanmış Set-IRMConfiguration cmdlet'ini çalıştırarak Microsoft Purview İleti Şifrelemesi'ni devre dışı bırakın:

   ```powershell
   Set-IRMConfiguration -AzureRMSLicensingEnabled $false
   ```
