---
title: Markanızı şifrelenmiş iletilere ekleme
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 5/12/2022
search.appverid:
- MET150
- MOE150
ms.assetid: 7a29260d-2959-42aa-8916-feceff6ee51d
ms.collection:
- Strat_O365_IP
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
description: Office 365 genel yöneticilerin şifreleme portalının içeriği & şifrelenmiş e-posta iletilerine kuruluşunuzun markasını nasıl uygulayabileceğini öğrenin.
ms.openlocfilehash: bf6f3b9de64185778be7eeb4da6cc8e537f0305a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66637031"
---
# <a name="add-your-organizations-brand-to-your-microsoft-365-for-business-message-encryption-encrypted-messages"></a>İş için Microsoft 365 İleti Şifrelemesi şifreli iletilerinize kuruluşunuzun markasını ekleme

Kuruluşunuzun e-posta iletilerinin ve şifreleme portalının görünümünü özelleştirmek için şirketinizin markasını uygulayabilirsiniz. Başlamadan önce iş veya okul hesabınıza genel yönetici izinleri uygulamanız gerekir. Bu izinlere sahip olduktan sonra, şifrelenmiş e-posta iletilerinin bu bölümlerini özelleştirmek için Exchange Online PowerShell'deki Get-OMEConfiguration ve Set-OMEConfiguration cmdlet'lerini kullanın:

- Giriş metni
- Yasal uyarı metni
- Kuruluşunuzun gizlilik bildiriminin URL'si
- OME portalındaki metin
- E-posta iletisinde ve OME portalında görünen logo veya logonun kullanılıp kullanılmaymayacağı
- E-posta iletisinde ve OME portalında arka plan rengi

Ayrıca istediğiniz zaman varsayılan görünüme geri dönebilirsiniz.

Daha fazla denetim istiyorsanız, kuruluşunuzdan kaynaklanan şifrelenmiş e-postalar için birden çok şablon oluşturmak üzere Microsoft Purview Gelişmiş İleti Şifrelemesi'ni kullanın. Son kullanıcı deneyiminin bölümlerini denetlemek için bu şablonları kullanın. Örneğin, alıcıların şifreleme portalında oturum açmak için Google, Yahoo ve Microsoft Hesaplarını kullanıp kullanamayacağını belirtin. Aşağıdakiler gibi çeşitli kullanım örneklerini yerine getirmek için şablonları kullanın:

- Finans, Satış gibi tek tek departmanlar.
- Farklı ürünler
- Farklı coğrafi bölgeler veya ülkeler
- E-postaların iptal edilmesine izin vermek isteyip istemediğiniz
- Dış alıcılara gönderilen e-postaların süresinin belirtilen sayıda gün sonra dolmasını isteyip istemediğiniz.

Şablonları oluşturduktan sonra, Exchange posta akışı kurallarını kullanarak bunları şifrelenmiş e-postalara uygulayabilirsiniz. Microsoft Purview Gelişmiş İleti Şifrelemesi'ne sahipseniz, bu şablonları kullanarak markaladığınız tüm e-postaları iptal edebilirsiniz.

## <a name="work-with-ome-branding-templates"></a>OME marka şablonlarıyla çalışma

Bir marka şablonundaki çeşitli özellikleri değiştirebilirsiniz. Varsayılan şablonu değiştirebilirsiniz ancak kaldıramayın. Gelişmiş İleti Şifrelemesi'ne sahipseniz özel şablonlar da oluşturabilir, değiştirebilir ve kaldırabilirsiniz. Exchange Online PowerShell kullanarak aynı anda tek bir marka şablonuyla çalışın.

- [Set-OMEConfiguration](/powershell/module/exchange/set-omeconfiguration) - Oluşturduğunuz varsayılan marka şablonunu veya özel bir marka şablonunu değiştirin.
- [New-OMEConfiguration](/powershell/module/exchange/new-omeconfiguration) - Yalnızca Gelişmiş İleti Şifrelemesi adlı yeni bir marka şablonu oluşturun.
- [Remove-OMEConfiguration](/powershell/module/exchange/remove-omeconfiguration) - Yalnızca Gelişmiş İleti Şifrelemesi olan özel bir marka şablonunu kaldırın. Varsayılan marka şablonunu silemezsiniz.

## <a name="modify-an-ome-branding-template"></a>OME marka şablonunu değiştirme

Exchange Online PowerShell kullanarak aynı anda bir marka şablonunu değiştirin. Gelişmiş İleti Şifrelemesi'ne sahipseniz özel şablonlar da oluşturabilir, değiştirebilir ve kaldırabilirsiniz.

1. Kuruluşunuzda genel yönetici izinlerine sahip bir iş veya okul hesabı kullanarak Exchange Online PowerShell'e bağlanın. Yönergeler için bkz. [Exchange Online PowerShell'e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

2. [Set-OMEConfiguration'da](/powershell/module/exchange/Set-OMEConfiguration) açıklandığı gibi Set-OMEConfiguration cmdlet'ini kullanın veya rehberlik için aşağıdaki grafiği ve tabloyu kullanın.

![Özelleştirilebilir e-posta bölümleri.](../media/ome-template-breakout.png)

|Şifreleme deneyiminin bu özelliğini özelleştirmek için|Bu komutları kullanın|
|---|---|
|Arka plan rengi|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -BackgroundColor "<#RRGGBB hexadecimal color code or name value>"` <p> **Örnek:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -BackgroundColor "#ffffff"` <p> Arka plan renkleri hakkında daha fazla bilgi için bu makalenin devamında [yer alan Arka plan renkleri](#background-color-reference) bölümüne bakın.|
|Logo|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -Image <Byte[]>` <p> **Örnek:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -Image ([System.IO.File]::ReadAllBytes('C:\Temp\contosologo.png'))` <p> Desteklenen dosya biçimleri: .png, .jpg, .bmp veya .tiff <p> En uygun logo dosyası boyutu: 40 KB'tan az <p> En uygun logo görüntüsü boyutu: 170x70 piksel. Resminiz bu boyutları aşarsa hizmet, portalda görüntülenmek üzere logonuzu yeniden boyutlandırıyor. Hizmet, grafik dosyasının kendisini değiştirmez. En iyi sonuçları elde için en uygun boyutu kullanın.|
|Gönderenin adının ve e-posta adresinin yanındaki metin|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -IntroductionText "<String up to 1024 characters>"` <p> **Örnek:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -IntroductionText "has sent you a secure message."`|
|"İletiyi Oku" düğmesinde görünen metin|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -ReadButtonText "<String up to 1024 characters>"` <p> **Örnek:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -ReadButtonText "Read Secure Message."`|
|"İletiyi Oku" düğmesinin altında görünen metin|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -EmailText "<String up to 1024 characters>"` <p> **Örnek:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -EmailText "Encrypted message from ContosoPharma secure messaging system."`|
|Gizlilik Bildirimi bağlantısının URL'si|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PrivacyStatementURL "<URL>"` <p> **Örnek:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -PrivacyStatementURL "https://contoso.com/privacystatement.html"`|
|Şifrelenmiş iletiyi içeren e-postadaki yasal uyarı deyimi|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -DisclaimerText "<Disclaimer statement. String of up to 1024 characters.>"` <p> **Örnek:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -DisclaimerText "This message is confidential for the use of the addressee only."`|
|Şifrelenmiş posta görüntüleme portalının en üstünde görünen metin|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PortalText "<Text for your portal. String of up to 128 characters.>"` <p> **Örnek:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -PortalText "ContosoPharma secure email portal."`|
|Bu özel şablon için tek seferlik geçiş koduyla kimlik doğrulamasını etkinleştirmek veya devre dışı bırakmak için|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -OTPEnabled <$true|$false>` <p> **Örnekler:** <br/>Bu özel şablon için tek seferlik geçiş kodlarını etkinleştirmek için <p> `Set-OMEConfiguration -Identity "Branding Template 1" -OTPEnabled $true` <p> Bu özel şablon için tek seferlik geçiş kodlarını devre dışı bırakmak için <p> `Set-OMEConfiguration -Identity "Branding Template 1" -OTPEnabled $false`|
|Bu özel şablonda Microsoft, Google veya Yahoo kimlikleriyle kimlik doğrulamasını etkinleştirmek veya devre dışı bırakmak için|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -SocialIdSignIn <$true|$false>` <p> **Örnekler:** <br/>Bu özel şablon için sosyal kimlikleri etkinleştirmek için <p> `Set-OMEConfiguration -Identity "Branding Template 1" -SocialIdSignIn $true` <p> Bu özel şablon için sosyal kimlikleri devre dışı bırakmak için <p> `Set-OMEConfiguration -Identity "Branding Template 1" -SocialIdSignIn $false`|

## <a name="create-an-ome-branding-template-advanced-message-encryption"></a>OME marka şablonu oluşturma (Gelişmiş İleti Şifrelemesi)

Microsoft Purview Gelişmiş İleti Şifrelemesi'ne sahipseniz [, New-OMEConfiguration](/powershell/module/exchange/new-omeconfiguration) cmdlet'ini kullanarak kuruluşunuz için özel marka şablonları oluşturabilirsiniz. Şablonu oluşturduktan sonra, [OME marka şablonunu değiştirme](#modify-an-ome-branding-template) bölümünde açıklandığı gibi Set-OMEConfiguration cmdlet'ini kullanarak şablonu değiştirirsiniz. Birden çok şablon oluşturabilirsiniz.

Yeni bir özel marka şablonu oluşturmak için:

1. Kuruluşunuzda genel yönetici izinlerine sahip bir iş veya okul hesabı kullanarak Exchange Online PowerShell'e bağlanın. Yönergeler için bkz. [Exchange Online PowerShell'e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

2. Yeni bir şablon oluşturmak için [New-OMEConfiguration](/powershell/module/exchange/new-omeconfiguration) cmdlet'ini kullanın.

   ```powershell
   New-OMEConfiguration -Identity "<OMEConfigurationName>"
   ```

   Örneğin,

   ```powershell
   New-OMEConfiguration -Identity "Custom branding template"
   ```

## <a name="return-the-default-branding-template-to-its-original-values"></a>Varsayılan marka şablonunu özgün değerlerine döndürme

Marka özelleştirmeleri gibi tüm değişiklikleri varsayılan şablondan kaldırmak için şu adımları tamamlayın:

1. Kuruluşunuzda genel yönetici izinlerine sahip bir iş veya okul hesabı kullanarak Exchange Online PowerShell'e bağlanın. Yönergeler için bkz. [Exchange Online PowerShell'e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

2. **Set-OMEConfiguration'da** açıklandığı gibi [Set-OMEConfiguration](/powershell/module/exchange/Set-OMEConfiguration) cmdlet'ini kullanın. Kuruluşunuzun markalı özelleştirmelerini DisclaimerText, EmailText ve PortalText değerlerinden kaldırmak için değeri boş bir dize olarak `""`ayarlayın. Logo gibi tüm görüntü değerleri için değerini olarak `"$null"`ayarlayın.

   Aşağıdaki tabloda şifreleme özelleştirme seçeneği varsayılanları açıklanmaktadır.

   |Şifreleme deneyiminin bu özelliğini varsayılan metin ve görüntüye geri döndürmek için|Bu komutları kullanın|
   |:-----|:-----|
   |Şifrelenmiş e-posta iletileriyle birlikte gelen varsayılan metin. Şifrelenmiş iletileri görüntüleme yönergelerinin üzerinde varsayılan metin görüntülenir|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -EmailText "<empty string>"` <p> **Örnek:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -EmailText ""`|
   |Şifrelenmiş iletiyi içeren e-postadaki yasal uyarı deyimi|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" DisclaimerText "<empty string>"` <p> **Örnek:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText ""`|
   |Şifrelenmiş posta görüntüleme portalının en üstünde görünen metin|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PortalText "<empty string>"` <p> **Varsayılana geri dönme örneği:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -PortalText ""`|
   |Logo|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -Image <"$null">` <p> **Varsayılana geri dönme örneği:** <p> `Set-OMEConfiguration -Identity "OME configuration" -Image $null`|
   |Arka plan rengi|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -BackgroundColor "$null">` <p> **Varsayılana geri dönme örneği:** <p> `Set-OMEConfiguration -Identity "OME configuration" -BackgroundColor $null`|

## <a name="remove-a-custom-branding-template-advanced-message-encryption"></a>Özel markalama şablonunu kaldırma (Gelişmiş İleti Şifrelemesi)

Yalnızca oluşturduğunuz marka şablonlarını kaldırabilir veya silebilirsiniz. Varsayılan marka şablonunu kaldıramazsınız.

Özel bir markalama şablonunu kaldırmak için:

1. Kuruluşunuzda genel yönetici izinlerine sahip bir iş veya okul hesabı kullanarak Exchange Online PowerShell'e bağlanın. Yönergeler için bkz. [Exchange Online PowerShell'e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

2. **Remove-OMEConfiguration** cmdlet'ini aşağıdaki gibi kullanın:

   ```powershell
   Remove-OMEConfiguration -Identity ""<OMEConfigurationName>"
   ```

   Örneğin,

   ```powershell
   Remove-OMEConfiguration -Identity "Branding template 1"
   ```

   Daha fazla bilgi için bkz [. Remove-OMEConfiguration](/powershell/module/exchange/remove-omeconfiguration).

## <a name="create-an-exchange-mail-flow-rule-that-applies-your-custom-branding-to-encrypted-emails"></a>Şifrelenmiş e-postalara özel markanızı uygulayan bir Exchange posta akışı kuralı oluşturma

> [!IMPORTANT]
> Postayı taratan ve değiştiren üçüncü taraf uygulamalar, OME markasının doğru uygulanmasını engelleyebilir.

Varsayılan şablonu değiştirdikten veya yeni marka şablonları oluşturduktan sonra, belirli koşullara göre özel markanızı uygulamak için Exchange posta akışı kuralları oluşturabilirsiniz. En önemlisi, e-posta şifrelenmelidir. Böyle bir kural aşağıdaki senaryolarda özel markalama uygular:

- E-posta Outlook veya Web üzerinde Outlook kullanılarak son kullanıcı tarafından el ile şifrelendiyse, eski adıyla Outlook Web App
- E-posta bir Exchange posta akışı kuralı veya Microsoft Purview Veri Kaybı Önleme ilkesi tarafından otomatik olarak şifrelendiyse

Microsoft Purview İleti Şifrelemesi özel markanızı uyguladığınızdan emin olmak için e-posta iletilerinizi şifrelemek için bir posta akışı kuralı ayarlayın. Şifreleme kuralının önce işlenmesi için şifreleme kuralının önceliği markalama kuralından daha yüksek olmalıdır. Varsayılan olarak, şifreleme kuralını marka kuralından önce oluşturursanız şifreleme kuralı daha yüksek önceliğe sahip olur. Şifreleme uygulayan bir Exchange posta akışı kuralı oluşturma hakkında bilgi için bkz. [Office 365 e-posta iletilerini şifrelemek için posta akışı kuralları tanımlama](define-mail-flow-rules-to-encrypt-email.md). Posta akışı kuralının önceliğini ayarlama hakkında bilgi için bkz. [Posta akışı kurallarını yönetme](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#set-the-priority-of-a-mail-flow-rule).

1. Web tarayıcısında, genel yönetici izinleri verilmiş bir iş veya okul hesabı kullanarak [Office 365 oturum açın](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. **Yönetici** kutucuğunu seçin.

3. <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> Yönetici **merkezleri** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">**Exchange'i**</a> seçin.

4. EAC'de **Posta akışı** \> **Kuralları'na** gidin ve **Yeni Yeni simgesi'ni** ![seçin.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Yeni bir kural oluşturun**. EAC'yi kullanma hakkında daha fazla bilgi için bkz. [Exchange Online'de Exchange yönetim merkezi](/exchange/exchange-admin-center).

5. **Ad** alanına kural için satış departmanı için markalama gibi bir ad yazın.

6. **Bu kuralı uygula alanında**, Gönderen **kuruluş içinde yer alıyor koşulunu** ve kullanılabilir koşullar listesinden istediğiniz diğer koşulları seçin. Örneğin, belirli bir markalama şablonunu aşağıdakilere uygulamak isteyebilirsiniz:

   - Finans departmanı üyelerinden gönderilen tüm şifrelenmiş e-postalar
   - "Dış" veya "İş Ortağı" gibi belirli bir anahtar sözcükle gönderilen şifrelenmiş e-postalar
   - Belirli bir etki alanına gönderilen şifrelenmiş e-postalar

7. Şifreleme uygulamak için zaten bir posta akışı kuralı tanımladıysanız bu adımı atlayın. Aksi takdirde, posta akışı kuralını şifreleme uygulayacak şekilde yapılandırmak için **Aşağıdakileri yapın** bölümünde **İleti güvenliğini değiştir'i** ve ardından **İleti Şifrelemesi ve hak koruması Office 365 Uygula'yı** seçin. Listeden bir RMS şablonu seçin ve eylem **ekle'yi** seçin.

   Şablon listesi varsayılan şablonları ve seçenekleri ve oluşturduğunuz tüm özel şablonları içerir. Liste boşsa, Microsoft Purview İleti Şifrelemesi ayarladığınızdan emin olun. Yönergeler için bkz[. Microsoft Purview İleti Şifrelemesi ayarlama](set-up-new-message-encryption-capabilities.md). Varsayılan şablonlar hakkında bilgi için bkz. [Azure Information Protection için şablonları yapılandırma ve yönetme](/information-protection/deploy-use/configure-policy-templates). **İletme** seçeneği hakkında bilgi için bkz. [E-postalar için İletme seçeneği](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). **Yalnızca şifrele** seçeneği hakkında bilgi için bkz. [E-postalar için Yalnızca Şifrele seçeneği](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

8. **Aşağıdakileri yapın bölümünde** **İleti güvenliğini** \> değiştir **OME iletilerine özel marka uygulama'yı** seçin. Ardından açılan listeden bir marka şablonu seçin.

   Başka bir eylem belirtmek istiyorsanız **Eylem ekle'yi** seçin veya **Kaydet'i** ve ardından **Tamam'ı** seçin.

## <a name="background-color-reference"></a>Arka plan rengi başvurusu

Arka plan rengi için kullanabileceğiniz renk adları sınırlıdır. Renk adı yerine onaltılık kod değeri (`#RRGGBB`) kullanabilirsiniz. Renk adına karşılık gelen bir onaltılık kod değeri veya özel bir onaltılık kod değeri kullanabilirsiniz. Onaltılık kod değerini tırnak içine aldığınızdan emin olun (örneğin, `"#f0f8ff"`).

Kullanılabilir arka plan renk adları ve karşılık gelen onaltılık kod değerleri aşağıdaki tabloda açıklanmıştır.

|Renk adı|Renk kodu|
|---|---|
|`aliceblue`|#f0f8ff|
|`antiquewhite`|#faebd7|
|`aqua`|#00ffff|
|`aquamarine`|#7fffd4|
|`azure`|#f0ffff|
|`beige`|#f5f5dc|
|`bisque`|#ffe4c4|
|`black`|#000000|
|`blanchedalmond`|#ffebcd|
|`blue`|#0000ff|
|`blueviolet`|#8a2be2|
|`brown`|#a52a2a|
|`burlywood`|#deb887|
|`cadetblue`|#5f9ea0|
|`chartreuse`|#7fff00|
|`chocolate`|#d2691e|
|`coral`|#ff7f50|
|`cornflowerblue`|#6495ed|
|`cornsilk`|#fff8dc|
|`crimson`|#dc143c|
|`cyan`|#00ffff|
|`darkblue`|#00008b|
|`darkcyan`|#008b8b|
|`darkgoldenrod`|#b8860b|
|`darkgray`|#a9a9a9|
|`darkgreen`|#006400|
|`darkkhaki`|#bdb76b|
|`darkmagenta`|#8b008b|
|`darkolivegreen`|#556b2f|
|`darkorange`|#ff8c00|
|`darkorchid`|#9932cc|
|`darkred`|#8b0000|
|`darksalmon`|#e9967a|
|`darkseagreen`|#8fbc8f|
|`darkslateblue`|#483d8b|
|`darkslategray`|#2f4f4f|
|`darkturquoise`|#00ced1|
|`darkviolet`|#9400d3|
|`deeppink`|#ff1493|
|`deepskyblue`|#00bfff|
|`dimgray`|#696969|
|`dodgerblue`|#1e90ff|
|`firebrick`|#b22222|
|`floralwhite`|#fffaf0|
|`forestgreen`|#228b22|
|`fuchsia`|#ff00ff|
|`gainsboro`|#dcdcdc|
|`ghostwhite`|#f8f8ff|
|`gold`|#ffd700|
|`goldenrod`|#daa520|
|`gray`|#808080|
|`green`|#008000|
|`greenyellow`|#adff2f|
|`honeydew`|#f0fff0|
|`hotpink`|#ff69b4|
|`indianred`|#cd5c5c|
|`indigo`|#4b0082|
|`ivory`|#fffff0|
|`khaki`|#f0e68c|
|`lavender`|#e6e6fa|
|`lavenderblush`|#fff0f5|
|`lawngreen`|#7cfc00|
|`lemonchiffon`|#fffacd|
|`lightblue`|#add8e6|
|`lightcoral`|#f08080|
|`lightcyan`|#e0ffff|
|`lightgoldenrodyellow`|#fafad2|
|`lightgray`|#d3d3d3|
|`lightgrey`|#d3d3d3|
|`lightgreen`|#90ee90|
|`lightpink`|#ffb6c1|
|`lightsalmon`|#ffa07a|
|`lightseagreen`|#20b2aa|
|`lightskyblue`|#87cefa|
|`lightslategray`|#778899|
|`lightsteelblue`|#b0c4de|
|`lightyellow`|#ffffe0|
|`lime`|#00ff00|
|`limegreen`|#32cd32|
|`linen`|#faf0e6|
|`magenta`|#ff00ff|
|`maroon`|#800000|
|`mediumaquamarine`|#66cdaa|
|`mediumblue`|#0000cd|
|`mediumorchid`|#ba55d3|
|`mediumpurple`|#9370db|
|`mediumseagreen`|#3cb371|
|`mediumslateblue`|#7b68ee|
|`mediumspringgreen`|#00fa9a|
|`mediumturquoise`|#48d1cc|
|`mediumvioletred`|#c71585|
|`midnightblue`|#191970|
|`mintcream`|#f5fffa|
|`mistyrose`|#ffe4e1|
|`moccasin`|#ffe4b5|
|`navajowhite`|#ffdead|
|`navy`|#000080|
|`oldlace`|#fdf5e6|
|`olive`|#808000|
|`olivedrab`|#6b8e23|
|`orange`|#ffa500|
|`orangered`|#ff4500|
|`orchid`|#da70d6|
|`palegoldenrod`|#eee8aa|
|`palegreen`|#98fb98|
|`paleturquoise`|#afeeee|
|`palevioletred`|#db7093|
|`papayawhip`|#ffefd5|
|`peachpuff`|#ffdab9|
|`peru`|#cd853f|
|`pink`|#ffc0cb|
|`plum`|#dda0dd|
|`powderblue`|#b0e0e6|
|`purple`|#800080|
|`red`|#ff0000|
|`rosybrown`|#bc8f8f|
|`royalblue`|#4169e1|
|`saddlebrown`|#8b4513|
|`salmon`|#fa8072|
|`sandybrown`|#f4a460|
|`seagreen`|#00ff00|
|`seashell`|#fff5ee|
|`sienna`|#a0522d|
|`silver`|#c0c0c0|
|`skyblue`|#87ceeb|
|`slateblue`|#6a5acd|
|`slategray`|#708090|
|`snow`|#fffafa|
|`springgreen`|#00ff7f|
|`steelblue`|#4682b4|
|`tan`|#d2b48c|
|`teal`|#008080|
|`thistle`|#d8bfd8|
|`tomato`|#ff6347|
|`turquoise`|#40e0d0|
|`violet`|#ee82ee|
|`wheat`|#f5deb3|
|`white`|#ffffff|
|`whitesmoke`|#f5f5f5|
|`yellow`|#ffff00|
|`yellowgreen`|#9acd32|
