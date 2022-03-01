---
title: Şifrelenmiş iletilerinize kuruluş markanızı ekleme
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 4/1/2020
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
description: Bu Office 365 yöneticilerin, şifreleme portalında yer alan şifrelenmiş e-posta iletilerine ve & markalamalarını nasıl uygulayabileceklerini öğrenin.
ms.openlocfilehash: b96f87886b6f1dc5ca78de068b86dbbcfb9e460d
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2022
ms.locfileid: "63010040"
---
# <a name="add-your-organizations-brand-to-your-microsoft-365-for-business-message-encryption-encrypted-messages"></a>İşletmeler için İleti Şifrelemesi şifreli iletilerinize Microsoft 365 markasını ekleme

Şirketinizi markalama özelliğiyle kuruluş e-posta iletilerinin ve şifreleme portalının görünümünü özelleştirebilirsiniz. Başlamadan önce iş veya okul hesabınıza genel yönetici izinlerini uygulayabilirsiniz. Bu izinlere sahip olduktan sonra, Get-OMEConfiguration ve Set-OMEConfiguration Windows PowerShell ileti cmdlet'lerini kullanarak şifreli e-posta iletilerinin şu bölümlerini özelleştirin:

- Giriş metni
- Yasal Uyarı metni
- Organizasyon gizlilik bildiriminin URL'si
- OME portalında metin
- E-posta iletisinde ve OME portalında görünen logo veya logonun hiç kullanılamama
- E-posta iletisinde ve OME portalında arka plan rengi

Ayrıca, herhangi bir anda varsayılan görünüme ve görünüme geri dönabilirsiniz.

Daha fazla denetim için, Office 365 Gelişmiş İleti Şifrelemesi e-postalar için birden çok şablon oluşturmak üzere bu şablonu kullanın. Son kullanıcı deneyiminin bölümlerini kontrol etmek için bu şablonları kullanın. Örneğin, alıcıların Google, Yahoo ve Microsoft Hesaplarını kullanarak şifreleme portalında oturum açmasını isteyip göremezseniz belirtin. Çeşitli kullanım durumlarını karşılamak için şablonları kullanın; örneğin:

- Finans, Satış gibi ayrı departmanlar.
- Farklı ürünler
- Farklı coğrafi bölgeler veya ülkeler
- E-postaların iptal  olmasına izin vermek isteyip istemeyebilirsiniz
- Dış alıcılara gönderilen e-postaların süresinin belirtilen sayıda gün sonra sona erip sona erer mi?

Şablonları oluşturduktan sonra, e-posta akış kurallarını kullanarak bunları şifrelenmiş Exchange uygulayabilirsiniz. E-posta Office 365 Gelişmiş İleti Şifrelemesi, bu şablonları kullanarak markanız olan tüm e-postaları iptal edin.

## <a name="work-with-ome-branding-templates"></a>OME markalama şablonlarıyla çalışma

Bir markalama şablonu içinde çeşitli özellikleri değiştirebilirsiniz. Varsayılan şablonu değiştirebilir, ancak kaldırabilirsiniz. Gelişmiş İleti Şifreleme'niz varsa, özel şablonları da oluşturabilir, değiştirebilir ve kaldırabilirsiniz. Bir Windows PowerShell markalama şablonuyla çalışmak için bu şablonları kullanın.

- [Set-OMEConfiguration](/powershell/module/exchange/set-omeconfiguration) - Varsayılan markalama şablonunu veya oluşturduğunuz özel bir markalama şablonunu değiştirme.
- [New-OMEConfiguration](/powershell/module/exchange/new-omeconfiguration) - Yeni bir markalama şablonu, yalnızca Gelişmiş İleti Şifrelemesi oluşturun.
- [Remove-OMEConfiguration](/powershell/module/exchange/remove-omeconfiguration) - Yalnızca Gelişmiş İleti Şifrelemesi olan özel bir markalama şablonunu kaldırın. Varsayılan markalama şablonunu silemezsiniz.

## <a name="modify-an-ome-branding-template"></a>OME markalama şablonunu değiştirme

Bir Windows PowerShell markalama şablonunu değiştirmek için markalama şablonunu kullanın. Gelişmiş İleti Şifreleme'niz varsa, özel şablonları da oluşturabilir, değiştirebilir ve kaldırabilirsiniz.

1. Kuruluşta genel yönetici izinleri olan bir iş veya okul hesabı kullanarak yeni bir oturum Windows PowerShell bu hesaba bağlanarak Exchange Online. Yönergeler için bkz. [Bağlan PowerShell'Exchange Online yükleme](/powershell/exchange/connect-to-exchange-online-powershell).

2. [Set-OMEConfiguration Set-OMEConfiguration cmdlet'ini kullanın](/powershell/module/exchange/Set-OMEConfiguration) veya kılavuz olarak aşağıdaki grafiği ve tabloyu kullanın.

![E-posta bölümleri özelleştirilebilir.](../media/ome-template-breakout.png)

<br>

****

|**Şifreleme deneyiminin bu özelliğini özelleştirmek için**|**Şu komutları kullanın**|
|---|---|
|Arka plan rengi|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -BackgroundColor "<#RRGGBB hexadecimal color code or name value>"` <p> **Örnek:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -BackgroundColor "#ffffff"` <p> Arka plan renkleri hakkında daha fazla bilgi için, bu [makalenin sonraki](#background-color-reference) kısımlarında yer alan Arka plan renkleri bölümüne bakın.|
|Logo|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -Image <Byte[]>` <p> **Örnek:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -Image ([System.IO.File]::ReadAllBytes('C:\Temp\contosologo.png'))` <p> Desteklenen dosya biçimleri: .png, .jpg, .bmp veya .tiff <p> Logo dosyasının en iyi boyutu: 40 KB'den küçük <p> Logo resminin en uygun boyutu: 170x70 piksel. Resminiz bu boyutları aşarsa, hizmet portalda görüntülenmek için logonuzu yeniden boyutlandırr. Hizmet, grafik dosyasının kendisini değiştirmez. En iyi sonuçları elde etmek için en uygun boyutu kullanın.|
|Gönderenin adının ve e-posta adresinin yanındaki metin|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -IntroductionText "<String up to 1024 characters>"` <p> **Örnek:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -IntroductionText "has sent you a secure message."`|
|"İletiyi Oku" düğmesi üzerinde görünen metin|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -ReadButtonText "<String up to 1024 characters>"` <p> **Örnek:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -ReadButtonText "Read Secure Message."`|
|"İletiyi Oku" düğmesinin altında görünen metin|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -EmailText "<String up to 1024 characters>"` <p> **Örnek:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -EmailText "Encrypted message from ContosoPharma secure messaging system."`|
|Gizlilik Bildirimi bağlantısının URL'si|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PrivacyStatementURL "<URL>"` <p> **Örnek:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -PrivacyStatementURL "https://contoso.com/privacystatement.html"`|
|Şifreli iletiyi içeren e-postada Yasal Uyarı bildirimi|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -DisclaimerText "<Disclaimer statement. String of up to 1024 characters.>"` <p> **Örnek:** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -DisclaimerText "This message is confidential for the use of the addressee only."`|
|Şifreli posta görüntüleme portalının en üstünde görünen metin|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PortalText "<Text for your portal. String of up to 128 characters.>"` <p> **Örnek:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -PortalText "ContosoPharma secure email portal."`|
|Bu özel şablon için tek seferlik geçiş koduyla kimlik doğrulamayı etkinleştirmek veya devre dışı bırakmak için|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -OTPEnabled <$true|$false>` <p> **Örnekler:** <br/>Bu özel şablon için tek seferlik geçiş kodlarını etkinleştirmek için <p> `Set-OMEConfiguration -Identity "Branding Template 1" -OTPEnabled $true` <p> Bu özel şablonda tek seferlik geçiş kodlarını devre dışı bırakmak için <p> `Set-OMEConfiguration -Identity "Branding Template 1" -OTPEnabled $false`|
|Bu özel şablonda Microsoft, Google veya Yahoo kimlikleriyle kimlik doğrulamasını etkinleştirmek veya devre dışı bırakmak için|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -SocialIdSignIn <$true|$false>` <p> **Örnekler:** <br/>Bu özel şablonda sosyal kimlikleri etkinleştirmek için <p> `Set-OMEConfiguration -Identity "Branding Template 1" -SocialIdSignIn $true` <p> Bu özel şablonda sosyal kimlikleri devre dışı bırakmak için <p> `Set-OMEConfiguration -Identity "Branding Template 1" -SocialIdSignIn $false`|
|

## <a name="create-an-ome-branding-template-advanced-message-encryption"></a>OME markalama şablonu oluşturma (Gelişmiş İleti Şifrelemesi)

Birden çok Office 365 Gelişmiş İleti Şifrelemesi varsa, [New-OMEConfiguration](/powershell/module/exchange/new-omeconfiguration) cmdlet'ini kullanarak organizasyonunız için özel markalama şablonları oluşturabilirsiniz. Şablonu oluşturduktan sonra, OME markalama şablonunu değiştirme konusunda açıklandığı Set-OMEConfiguration bir cmdlet'i [kullanarak şablonu değiştirirsiniz](#modify-an-ome-branding-template). Birden çok şablon oluşturabilirsiniz.

Yeni bir özel markalama şablonu oluşturmak için:

1. Kuruluşta genel yönetici izinleri olan bir iş veya okul hesabı kullanarak yeni bir oturum Windows PowerShell bu hesaba bağlanarak Exchange Online. Yönergeler için bkz. [Bağlan PowerShell'Exchange Online yükleme](/powershell/exchange/connect-to-exchange-online-powershell).

2. Yeni şablon [oluşturmak için New-OMEConfiguration](/powershell/module/exchange/new-omeconfiguration) cmdlet'ini kullanın.

   ```powershell
   New-OMEConfiguration -Identity "<OMEConfigurationName>"
   ```

   Örneğin,

   ```powershell
   New-OMEConfiguration -Identity "Custom branding template"
   ```

## <a name="return-the-default-branding-template-to-its-original-values"></a>Varsayılan markalama şablonunu özgün değerlerine geri dönme

Marka özelleştirmeleri gibi tüm değişiklikleri varsayılan şablondan kaldırmak için şu adımları tamamlayın:

1. Kuruluşta genel yönetici izinleri olan bir iş veya okul hesabı kullanarak yeni bir oturum Windows PowerShell bu hesaba bağlanarak Exchange Online. Yönergeler için bkz. [Bağlan PowerShell'Exchange Online yükleme](/powershell/exchange/connect-to-exchange-online-powershell).

2. **Set-OMEConfiguration** cmdlet'ini [Set-OMEConfiguration'ta açıklandığı gibi kullanın](/powershell/module/exchange/Set-OMEConfiguration). DisclaimerText, EmailText ve PortalText değerlerinden, organizasyon markalı özelleştirmelerini kaldırmak için, değeri boş bir dizeye, ayarlayın. `""` Logo gibi tüm resim değerleri için değeri olarak ayarlayın `"$null"`.

   Aşağıdaki tabloda, şifreleme özelleştirme seçeneği varsayılanları açık almaktadır.

   <br>

   ****

   |Şifreleme deneyiminin bu özelliğini varsayılan metin ve görüntüye geri döndürme|Şu komutları kullanın|
   |:-----|:-----|
   |Şifreli e-posta iletileriyle birlikte gelen varsayılan metin. Şifreli iletileri görüntüleme yönergelerinin üzerinde varsayılan metin görüntülenir|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -EmailText "<empty string>"` <p> **Örnek:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -EmailText ""`|
   |Şifreli iletiyi içeren e-postada Yasal Uyarı bildirimi|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" DisclaimerText "<empty string>"` <p> **Örnek:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText ""`|
   |Şifreli posta görüntüleme portalının en üstünde görünen metin|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PortalText "<empty string>"` <p> **Varsayılan değere geri döndürülen örnek:** <p> `Set-OMEConfiguration -Identity "OME Configuration" -PortalText ""`|
   |Logo|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -Image <"$null">` <p> **Varsayılan değere geri döndürülen örnek:** <p> `Set-OMEConfiguration -Identity "OME configuration" -Image $null`|
   |Arka plan rengi|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -BackgroundColor "$null">` <p> **Varsayılan değere geri döndürülen örnek:** <p> `Set-OMEConfiguration -Identity "OME configuration" -BackgroundColor $null`|
   |

## <a name="remove-a-custom-branding-template-advanced-message-encryption"></a>Özel markalama şablonunu kaldırma (Gelişmiş İleti Şifrelemesi)

Yalnızca kendi markalama şablonlarını kaldırabilir veya silebilirsiniz. Varsayılan markalama şablonunu kaldırabilirsiniz.

Özel markalama şablonunu kaldırmak için:

1. Kuruluşta genel yönetici izinleri olan bir iş veya okul hesabı kullanarak yeni bir oturum Windows PowerShell bu hesaba bağlanarak Exchange Online. Yönergeler için bkz. [Bağlan PowerShell'Exchange Online yükleme](/powershell/exchange/connect-to-exchange-online-powershell).

2. **Remove-OMEConfiguration** cmdlet'ini aşağıdaki gibi kullanın:

   ```powershell
   Remove-OMEConfiguration -Identity ""<OMEConfigurationName>"
   ```

   Örneğin,

   ```powershell
   Remove-OMEConfiguration -Identity "Branding template 1"
   ```

   Daha fazla bilgi için bkz [. Remove-OMEConfiguration](/powershell/module/exchange/remove-omeconfiguration).

## <a name="create-an-exchange-mail-flow-rule-that-applies-your-custom-branding-to-encrypted-emails"></a>Özel markalamanızı Exchange e-postalara uygulanan bir hızlı posta akışı kuralı oluşturma

> [!IMPORTANT]
> Postayı taratan ve değiştiren üçüncü taraf uygulamalar, OME markalamanın doğru şekilde uygulanmasına engel olabilir.

Varsayılan şablonu değiştirdikten veya yeni markalama şablonları oluşturduktan sonra, özel markalamanızı belirli Exchange uygulamak için posta akış kuralları oluşturabilirsiniz. Böyle bir kural, aşağıdaki senaryolarda özel markalama uygulayacak:

- E-posta son kullanıcı tarafından e-posta Outlook veya Web üzerinde Outlook kullanılarak el ile şifrelenirse, eski adı Outlook Web App
- E-posta bir posta akışı kuralı veya Exchange Önleme ilkesi tarafından otomatik olarak şifrelenirse

Şifreleme içeren bir posta akışı kuralı Exchange hakkında bilgi için bkz. E-posta iletilerini şifrelemek için posta akış kurallarını tanımlama [Office 365](define-mail-flow-rules-to-encrypt-email.md).

1. Web tarayıcısında, genel yönetici izinlerine sahip bir iş veya okul hesabı kullanarak [Office 365.](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser)

2. Yönetici **kutucuğunu** seçin.

3. Genel <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi Yönetim</a> **merkezleri'ni Exchange**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank"></a>

4. EAC'de, Posta akışı **Kuralları'ne gidin** \> **ve** Yeni Yeni **simgesi'yi** ![seçin.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Yeni kural oluşturma**. EAC'nin kullanımı hakkında daha fazla bilgi için bkz[. Exchange Yönetim Merkezi'Exchange Online](/exchange/exchange-admin-center).

5. Ad **kutusuna**, kural için bir ad (satış bölümü için Markalama gibi) yazın.

6. Bu **kuralı uygula altında**, Gönderen kuruluş içinde **yer alıyor** koşullarını ve kullanılabilir koşullar listesinden istediğiniz diğer koşulları seçin. Örneğin, belirli bir markalama şablonunu aşağıdakilere uygulamak istediğiniz olabilir:

   - Finans departmanı üyelerinden gönderilen tüm şifreli e-postalar
   - "Dış" veya "İş Ortağı" gibi belirli bir anahtar sözcükle gönderilen şifreli e-postalar
   - Belirli bir etki alanına gönderilen şifreli e-postalar

7. Bunu **yapın'da**, İleti **güvenliğini değiştir: Özel markalama** \> **uygula öğesini OME iletilerine uygula'ya tıklayın**. Ardından, açılan listeden bir markalama şablonu seçin.

8. (İsteğe bağlı) Posta akışı kuralını şifreleme ve özel markalama uygulamak üzere yapılandırabilirsiniz. Bunu **yapın'da** İleti güvenliğini **değiştir'i seçin ve sonra** da Güvenlik ve **hak Office 365 İleti Şifrelemesi uygula'ya seçin**. Listeden bir RMS şablonu seçin, Kaydet'i **ve** ardından Tamam'ı **seçin**.

   Şablon listesi, varsayılan şablonları ve seçenekleri ve sizin oluştur oluşturursanız özel şablonları içerir. Liste boşsa, yeni özelliklerle listenizin Office 365 İleti Şifrelemesi emin olur. Yönergeler için bkz[. Yeni özellik Office 365 İleti Şifrelemesi ayarlama](set-up-new-message-encryption-capabilities.md). Varsayılan şablonlar hakkında bilgi için bkz. [Azure Information Protection için şablonları yapılandırma ve yönetme](/information-protection/deploy-use/configure-policy-templates). E-postalarda **İleri seçeneğini iletme** [seçeneği hakkında bilgi için bkz. E-postalar için iletme seçeneği](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). Yalnızca şifrele seçeneği hakkında **bilgi için** bkz. [E-postalar için Yalnızca Şifrele seçeneği](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

   Başka **bir eylem** belirtmek için Eylem ekle'yi seçin.

## <a name="background-color-reference"></a>Arka plan rengi başvurusu

Arka plan rengi olarak kullanabileceğiniz renk adları sınırlıdır. Renk adı yerine, bir hex kodu değeri () kullanabilirsiniz`#RRGGBB`. Bir renk adına karşılık gelen hex kodu değerini veya özel bir hex kodu değeri kullanabilirsiniz. Hex kodu değerini tırnak işareti (örneğin, ) içine almanız gerekir `"#f0f8ff"`.

Kullanılabilir arka plan rengi adları ve bunların ilgili hex kod değerleri aşağıdaki tabloda açıklanmıştır.

|**Renk adı**|**Renk kodu**|
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
