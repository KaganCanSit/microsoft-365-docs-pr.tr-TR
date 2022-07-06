---
title: Office 365 İleti Şifrelemesi için eski bilgiler
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 05/22/2020
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.assetid: 5986b9e1-c824-4f8f-9b7d-a2b0ae2a7fe9
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
description: Kuruluşunuz için eski dosyaların Office 365 İleti Şifrelemesi'ne (OME) nasıl geçirilmesini anlayın.
ms.openlocfilehash: b34ccbcf077238ba3caee9da3b337cd0d32cf458
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66642535"
---
# <a name="legacy-information-for-office-365-message-encryption"></a>Office 365 İleti Şifrelemesi için eski bilgiler

Kuruluşunuzu henüz Microsoft Purview İleti Şifrelemesi taşımadıysanız ancak OME'yi zaten dağıttıysanız, bu makaledeki bilgiler kuruluşunuz için geçerlidir. Microsoft, kuruluşunuz için makul olduğu anda Microsoft Purview İleti Şifrelemesi'e geçmek için bir plan yapmanızı önerir. Yönergeler için bkz[. Microsoft Purview İleti Şifrelemesi ayarlama](set-up-new-message-encryption-capabilities.md). Yeni ileti şifrelemesi hakkında daha fazla bilgi edinmek istiyorsanız bkz. [İleti şifreleme](ome.md). Bu makalenin geri kalanı, Microsoft Purview İleti Şifrelemesi yayımlanmadan önceki OME davranışını ifade eder.

Office 365 İleti Şifrelemesi ile kuruluşunuz, kuruluşunuzun içindeki ve dışındaki kişiler arasında şifreli e-posta iletileri gönderebilir ve alabilir. Office 365 İleti Şifrelemesi Outlook.com, Yahoo, Gmail ve diğer e-posta hizmetleriyle çalışır. E-posta iletisi şifrelemesi, yalnızca hedeflenen alıcıların ileti içeriğini görüntüleyebilmesine yardımcı olur.

İşte birkaç örnek:

- Banka çalışanı müşterilere kredi kartı ekstreleri gönderiyor
- Sigorta şirketi temsilcisi müşterilere ilke ayrıntıları sağlar
- Bir ipotek komisyoncusu, kredi başvurusu için müşteriden finansal bilgiler talep eder
- Bir sağlık hizmeti sağlayıcısı hastalara sağlık hizmeti bilgileri gönderir
- Avukat bir müşteriye veya başka bir avukata gizli bilgiler gönderir

## <a name="how-office-365-message-encryption-works-without-the-new-capabilities"></a>Office 365 İleti Şifrelemesi yeni özellikler olmadan nasıl çalışır?

Office 365 İleti Şifrelemesi, Microsoft Azure Rights Management (Azure RMS) üzerinde oluşturulmuş bir çevrimiçi hizmettir. Azure RMS ile yöneticiler, şifreleme koşullarını belirlemek için posta akışı kuralları tanımlayabilir. Örneğin, bir kural belirli bir alıcıya gönderilen tüm iletilerin şifrelenmesini gerektirebilir.

Birisi Exchange Online şifreleme kuralıyla eşleşen bir e-posta iletisi gönderdiğinde, ileti bir HTML eki ile gönderilir. Alıcı HTML ekini açar ve şifrelenmiş iletiyi Office 365 İleti Şifrelemesi portalında görüntülemek için yönergeleri izler. Alıcı, bir Microsoft hesabıyla veya Office 365 ilişkili bir iş veya okulla oturum açarak ya da tek seferlik bir geçiş kodu kullanarak iletiyi görüntülemeyi seçebilir. Her iki seçenek de şifrelenmiş iletiyi yalnızca hedeflenen alıcının görüntüleyebilmesini sağlamaya yardımcı olur. Bu işlem Microsoft Purview İleti Şifrelemesi için çok farklıdır.

Aşağıdaki diyagramda, şifreleme ve şifre çözme işlemi aracılığıyla bir e-posta iletisinin geçişi özetlenmiştir.

![Şifrelenmiş e-postanın yolunu gösteren diyagram.](../media/O365-Office365MessageEncryption-Concept.png)

Daha fazla bilgi için bkz. [Microsoft Purview İleti Şifrelemesi yayımlanmadan önce eski Office 365 İleti Şifrelemesi için hizmet bilgileri](legacy-information-for-message-encryption.md#LegacyServiceInfo).

## <a name="defining-mail-flow-rules-for-office-365-message-encryption-that-dont-use-microsoft-purview-message-encryption"></a>Microsoft Purview İleti Şifrelemesi kullanmayan Office 365 İleti Şifrelemesi için posta akışı kuralları tanımlama

yeni özellikler olmadan Office 365 İleti Şifrelemesini etkinleştirmek için, Exchange Online ve Exchange Online Protection yöneticileri Exchange posta akışı kurallarını tanımlar. Bu kurallar, e-posta iletilerinin şifrelenmesi gereken koşulların yanı sıra ileti şifrelemesini kaldırma koşullarını belirler. Bir kural için bir şifreleme eylemi ayarlandığında, hizmet, iletileri göndermeden önce kural koşullarıyla eşleşen tüm iletilerde eylemi gerçekleştirir.

Posta akışı kuralları esnektir ve koşulları birleştirerek belirli güvenlik gereksinimlerini tek bir kuralda karşılamanızı sağlar. Örneğin, belirtilen anahtar sözcükleri içeren ve dış alıcılara gönderilen tüm iletileri şifrelemek için bir kural oluşturabilirsiniz. Office 365 İleti Şifrelemesi, şifrelenmiş e-posta alıcılarından gelen yanıtları da şifreler ve e-posta kullanıcılarınıza kolaylık sağlamak için bu yanıtların şifresini çözen bir kural oluşturabilirsiniz. Bu şekilde, kuruluşunuzdaki kullanıcıların yanıtları görüntülemek için şifreleme portalında oturum açması gerekmez.

Exchange posta akışı kuralları oluşturma hakkında daha fazla bilgi için bkz. [Office 365 İleti Şifrelemesi için Kuralları Tanımlama](define-mail-flow-rules-to-encrypt-email.md).

### <a name="use-the-eac-to-create-a-mail-flow-rule-for-encrypting-email-messages-without-microsoft-purview-message-encryption"></a>EAC kullanarak e-posta iletilerini Microsoft Purview İleti Şifrelemesi olmadan şifrelemek için bir posta akışı kuralı oluşturma

1. Web tarayıcısında, genel yönetici izinleri verilmiş bir iş veya okul hesabı kullanarak [Office 365 oturum açın](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. **Yönetici** kutucuğunu seçin.

3. Microsoft 365 yönetim merkezi Yönetici **merkezleri** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">**Exchange'i**</a> seçin.

4. EAC'de **Posta akışı** \> **Kuralları'na** gidin ve **Yeni Yeni simgesi'ni** ![seçin.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Yeni bir kural oluşturun**. EAC'yi kullanma hakkında daha fazla bilgi için bkz. [Exchange Online'de Exchange yönetim merkezi](/exchange/exchange-admin-center).

5. **Ad** alanına kural için DrToniRamos@hotmail.com için posta şifreleme gibi bir ad yazın.

6. **Bir koşul seçerseniz bu kuralı uygula** alanına bir değer girin ve gerekirse bir değer girin. Örneğin, DrToniRamos@hotmail.com giden iletileri şifrelemek için:

   1. **Bu kuralı uygula** alanında **alıcıyı** seçin.

   2. Kişi listesinden var olan bir adı seçin veya **onay adları** kutusuna yeni bir e-posta adresi yazın.

      - Var olan bir adı seçmek için listeden seçin ve **ardından Tamam'a** tıklayın.

      - Yeni bir ad girmek için, **onay adları** kutusuna bir e-posta adresi yazın ve ardından **adları** \> **denetle Tamam'ı** seçin.

7. Daha fazla koşul eklemek için **Diğer seçenekler'i** ve ardından **Koşul ekle'yi** seçin ve listeden seçin.

   Örneğin, kuralı yalnızca alıcı kuruluşunuzun dışındaysa uygulamak için **Koşul ekle'yi** ve ardından Alıcı **kuruluş** \> **dışından/kuruluş** \> dışında **Tamam'ı** seçin.

8. Yeni OME özelliklerini kullanmadan şifrelemeyi etkinleştirmek için **Aşağıdakileri yapın** bölümünde **İleti güvenliğini** \> değiştir **OME'nin önceki sürümünü uygula'yı** ve ardından **Kaydet'i** seçin.

   IRM lisanslamanın etkinleştirilmediğini belirten bir hata alırsanız eski OME kullanmıyorsunuz demektir.

9. (İsteğe bağlı) Başka bir eylem belirtmek için **Eylem ekle'yi** seçin.

### <a name="use-exchange-online-powershell-to-create-a-mail-flow-rule-for-encrypting-email-messages-without-the-new-ome-capabilities"></a>Exchange Online PowerShell kullanarak yeni OME özellikleri olmadan e-posta iletilerini şifrelemek için bir posta akışı kuralı oluşturun

1. Exchange Online PowerShell’e bağlanın. Daha fazla bilgi için bkz[. Exchange Online PowerShell'e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

2. **New-TransportRule** cmdlet'ini kullanarak bir kural oluşturun ve _ApplyOME_ parametresini olarak `$true`ayarlayın.

   Bu örnek, DrToniRamos@hotmail.com gönderilen tüm e-posta iletilerinin şifrelenmesini gerektirir.

   ```powershell
   New-TransportRule -Name "Encrypt rule for Dr Toni Ramos" -SentTo "DrToniRamos@hotmail.com" -SentToScope "NotinOrganization" -ApplyOME $true
   ```

   Nerede

   - Yeni kuralın benzersiz adı "Dr Toni Ramos için kuralı şifrele" şeklindedir.
   - _SentTo_ parametresi ileti alıcılarını belirtir (ad, e-posta adresi, ayırt edici ad vb. ile tanımlanır). Bu örnekte, alıcı "DrToniRamos@hotmail.com" e-posta adresiyle tanımlanır.
   - _SentToScope_ parametresi, ileti alıcılarının konumunu belirtir. Bu örnekte, alıcının posta kutusu hotmail'dedir ve kuruluşun bir parçası olmadığından değer `NotInOrganization` kullanılır.

   Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-TransportRule](/powershell/module/exchange/New-TransportRule).

### <a name="remove-encryption-from-email-replies-encrypted-without-microsoft-purview-message-encryption"></a>Microsoft Purview İleti Şifrelemesi olmadan şifrelenen e-posta yanıtlarından şifrelemeyi kaldırma

E-posta kullanıcılarınız şifreli iletiler gönderdiğinde, bu iletilerin alıcıları şifrelenmiş yanıtlarla yanıt verebilir. Kuruluşunuzdaki e-posta kullanıcılarının bunları görüntülemek için şifreleme portalında oturum açmasını gerektirmeyecek şekilde yanıtlardan şifrelemeyi otomatik olarak kaldırmak için posta akışı kuralları oluşturabilirsiniz. Bu kuralları tanımlamak için EAC veya Exchange Online PowerShell cmdlet'lerini kullanabilirsiniz. Kuruluşunuzun içinden gönderilen iletilerin veya kuruluşunuzun içinden gönderilen iletilere yanıt olan iletilerin şifresini çözebilirsiniz. Kuruluşunuzun dışından gelen şifrelenmiş iletilerin şifresini çözemezsiniz.

#### <a name="use-the-eac-to-create-a-rule-for-removing-encryption-from-email-replies-encrypted-without-microsoft-purview-message-encryption"></a>EAC kullanarak Microsoft Purview İleti Şifrelemesi olmadan şifrelenmiş e-posta yanıtlarından şifrelemeyi kaldırmaya yönelik bir kural oluşturma

1. Bir web tarayıcısında, yönetici izinleri verilmiş bir iş veya okul hesabı kullanarak [Office 365 oturum açın](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. **Yönetici** kutucuğunu seçin.

3. Microsoft 365 yönetim merkezi Yönetici **merkezleri** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">**Exchange'i**</a> seçin.

4. EAC'de **Posta akışı** \> **Kuralları'na** gidin ve **Yeni Yeni simgesi'ni** ![seçin.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Yeni bir kural oluşturun**. EAC'yi kullanma hakkında daha fazla bilgi için bkz. [Exchange Online'de Exchange yönetim merkezi](/exchange/exchange-admin-center).

5. **Ad** alanına kural için gelen postadan şifrelemeyi kaldır gibi bir ad yazın.

6. İletilerden şifrelemenin kaldırılması gereken koşulları (örneğin Alıcı kuruluş içinde **bulunur**\>) seçerseniz **, Bu kuralı uygula** **bölümünde.**

7. **Aşağıdakileri yapın bölümünde** **İleti güvenliğini** \> değiştir **OME'nin önceki sürümünü kaldır'ı** seçin.

8. **Kaydet**'i seçin.

#### <a name="use-exchange-online-powershell-to-create-a-rule-to-remove-encryption-from-email-replies-encrypted-without-the-new-ome-capabilities"></a>Exchange Online PowerShell kullanarak yeni OME özellikleri olmadan şifrelenmiş e-posta yanıtlarından şifrelemeyi kaldırma kuralı oluşturma

1. Exchange Online PowerShell’e bağlanın. Daha fazla bilgi için bkz[. Exchange Online PowerShell'e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

2. **New-TransportRule** cmdlet'ini kullanarak bir kural oluşturun ve _RemoveOME_ parametresini olarak `$true`ayarlayın.

   Bu örnek, kuruluştaki alıcılara gönderilen tüm postalardan şifrelemeyi kaldırır.

   ```powershell
   New-TransportRule -Name "Remove encryption from incoming mail" -SentToScope "InOrganization" -RemoveOME $true
   ```

   Nerede

   - Yeni kuralın benzersiz adı "Gelen postadan şifrelemeyi kaldır" şeklindedir.
   - _SentToScope_ parametresi, ileti alıcılarının konumunu belirtir. Bu örnekte, aşağıdakilerden birini gösteren değer `InOrganization` değeri kullanılır:
     - Alıcı, kuruluşunuzda posta kutusu, posta kullanıcısı, grup veya posta özellikli bir ortak klasördür.
     - Alıcının e-posta adresi, kuruluşunuzda yetkili bir etki alanı veya iç geçiş etki alanı olarak yapılandırılmış kabul edilen bir etki alanındadır _ve_ ileti kimliği doğrulanmış bir bağlantı üzerinden gönderilmiş veya alınmış.

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-TransportRule](/powershell/module/exchange/New-TransportRule).

## <a name="sending-viewing-and-replying-to-messages-encrypted-without-the-new-capabilities"></a>Yeni özellikler olmadan şifrelenmiş iletileri gönderme, görüntüleme ve yanıtlama

Office 365 İleti Şifrelemesi ile, e-posta iletileri yönetici tanımlı kurallara göre otomatik olarak şifrelenir. Şifrelenmiş ileti taşıyan bir e-posta, alıcının Gelen Kutusu'na ekli bir HTML dosyasıyla gelir.

Alıcılar eki açmak için iletideki yönergeleri izler ve bir Microsoft hesabı veya Office 365 ile ilişkilendirilmiş bir iş veya okul kullanarak kimlik doğrulaması yapar. Alıcıların iki hesabı da yoksa, şifrelenmiş iletiyi görüntülemek için oturum açmalarını sağlayacak bir Microsoft hesabı oluşturmaya yönlendirilirler. Alternatif olarak, alıcılar iletiyi görüntülemek için tek seferlik bir geçiş kodu almayı seçebilir. Oturum açtıktan veya tek seferlik bir geçiş kodu kullandıktan sonra, alıcılar şifresi çözülen iletiyi görüntüleyebilir ve şifreli bir yanıt gönderebilir.

## <a name="customize-encrypted-messages-with-office-365-message-encryption"></a>şifrelenmiş iletileri Office 365 İleti Şifrelemesi ile özelleştirme

Exchange Online ve Exchange Online Protection yöneticisi olarak şifrelenmiş iletilerinizi özelleştirebilirsiniz. Örneğin, şirketinizin markasını ve logosunu ekleyebilir, bir giriş belirtebilir, şifrelenmiş iletilere ve alıcıların şifrelenmiş iletilerinizi görüntülediği portalda sorumluluk reddi metni ekleyebilirsiniz. Exchange Online PowerShell cmdlet'lerini kullanarak, şifrelenmiş e-posta iletilerinin alıcıları için görüntüleme deneyiminin aşağıdaki yönlerini özelleştirebilirsiniz:

- Şifrelenmiş iletiyi içeren e-postanın giriş metni
- Şifrelenmiş iletiyi içeren e-postanın yasal uyarı metni
- İleti görüntüleme portalında görünecek portal metni
- E-posta iletisinde ve görüntüleme portalında görünecek logo

Ayrıca istediğiniz zaman varsayılan görünüme geri dönebilirsiniz.

Aşağıdaki örnekte, e-posta ekinde ContosoPharma için özel bir logo gösterilmektedir:

> [!div class="mx-imgBorder"]
> ![Görünüm şifreli ileti sayfasının örneği.](../media/TA-OME-3attachment2.jpg)

### <a name="to-customize-encryption-email-messages-and-the-encryption-portal-with-your-organizations-brand"></a>Şifreleme e-posta iletilerini ve şifreleme portalını kuruluşunuzun markasıyla özelleştirmek için

1. [Exchange Online PowerShell’e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

2. Burada açıklandığı gibi Set-OMEConfiguration cmdlet'ini kullanın: [Set-OMEConfiguration](/powershell/module/exchange/set-omeconfiguration) veya rehberlik için aşağıdaki tabloyu kullanın.

   **Şifreleme özelleştirme seçenekleri**

   |Şifreleme deneyiminin bu özelliğini özelleştirmek için|Bu Exchange Online PowerShell komutlarını kullanın|
   |---|---|
   |Şifrelenmiş e-posta iletilerine eşlik eden varsayılan metin <p> Şifrelenmiş iletileri görüntüleme yönergelerinin üzerinde varsayılan metin görüntülenir|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -EmailText "<string of up to 1024 characters>"` <p> **Örnek:** `Set-OMEConfiguration -Identity "OME Configuration" -EmailText "Encrypted message from ContosoPharma secure messaging system"`|
   |Şifrelenmiş iletiyi içeren e-postadaki yasal uyarı deyimi|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> DisclaimerText "<your disclaimer statement, string of up to 1024 characters>"` <p> **Örnek:** `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText "This message is confidential for the use of the addressee only"`|
   |Şifrelenmiş posta görüntüleme portalının en üstünde görünen metin|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -PortalText "<text for your portal, string of up to 128 characters>"` <p> **Örnek:** `Set-OMEConfiguration -Identity "OME Configuration" -PortalText "ContosoPharma secure email portal"`|
   |Logo|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -Image <Byte[]>` <p> **Örnek:** `Set-OMEConfiguration -Identity "OME configuration" -Image ([System.IO.File]::ReadAllBytes('C:\Temp\contosologo.png'))` <p> Desteklenen dosya biçimleri: .png, .jpg, .bmp veya .tiff <p> En uygun logo dosyası boyutu: 40 KB'tan az <p> En uygun logo görüntüsü boyutu: 170x70 piksel|

### <a name="to-remove-brand-customizations-from-encryption-email-messages-and-the-encryption-portal"></a>Şifreleme e-posta iletilerinden ve şifreleme portalından marka özelleştirmelerini kaldırmak için

1. [Exchange Online PowerShell’e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

2. Burada açıklandığı gibi Set-OMEConfiguration cmdlet'ini kullanın: [Set-OMEConfiguration](/powershell/module/exchange/set-omeconfiguration). Kuruluşunuzun markalı özelleştirmelerini DisclaimerText, EmailText ve PortalText değerlerinden kaldırmak için değeri boş bir dize olarak `""`ayarlayın. Logo gibi tüm görüntü değerleri için değerini olarak `"$null"`ayarlayın.

   **Şifreleme özelleştirme seçenekleri**

   |Şifreleme deneyiminin bu özelliğini varsayılan metin ve görüntüye geri döndürmek için|Bu Exchange Online PowerShell komutlarını kullanın|
   |---|---|
   |Şifrelenmiş e-posta iletilerine eşlik eden varsayılan metin <p> Şifrelenmiş iletileri görüntüleme yönergelerinin üzerinde varsayılan metin görüntülenir|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -EmailText "<empty string>"` <p> **Örnek:** `Set-OMEConfiguration -Identity "OME Configuration" -EmailText ""`|
   |Şifrelenmiş iletiyi içeren e-postadaki yasal uyarı deyimi <p> |`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> DisclaimerText "<empty string>"` <p> **Örnek:** `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText ""`|
   |Şifrelenmiş posta görüntüleme portalının en üstünde görünen metin|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -PortalText "<empty string>"` <p> **Varsayılana geri dönme örneği:** `Set-OMEConfiguration -Identity "OME Configuration" -PortalText ""`|
   |Logo|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -Image <"$null">` <p> **Varsayılana geri dönme örneği:** `Set-OMEConfiguration -Identity "OME configuration" -Image $null`|

## <a name="service-information-for-legacy-office-365-message-encryption-prior-to-the-release-of-the-new-ome-capabilities"></a>Yeni OME özellikleri yayımlanmadan önce eski Office 365 İleti Şifrelemesi için hizmet bilgileri
<a name="LegacyServiceInfo"> </a>

Aşağıdaki tabloda, Microsoft Purview İleti Şifrelemesi yayımlanmadan önce Office 365 İleti Şifrelemesi hizmeti için teknik ayrıntılar sağlanır.

|Hizmet ayrıntıları|Açıklama|
|---|---|
|İstemci cihaz gereksinimleri|Html eki Form Post'u destekleyen modern bir tarayıcıda açıldığı sürece şifrelenmiş iletiler herhangi bir istemci cihazında görüntülenebilir.|
|Şifreleme algoritması ve Federal Bilgi İşleme Standartları (FIPS) uyumluluğu|Office 365 İleti Şifrelemesi, Windows Azure Bilgi Hakları Yönetimi (IRM) ile aynı şifreleme anahtarlarını kullanır ve Şifreleme Modu 2'yi (RSA için 2K anahtar ve SHA-1 sistemleri için 256 bit anahtar) destekler. Temel alınan IRM şifreleme modları hakkında daha fazla bilgi için bkz. [AD RMS Şifreleme Modları](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh867439(v=ws.10)).|
|Desteklenen ileti türleri|Office 365 İleti Şifrelemesi yalnızca IPM ileti sınıfı kimliğine sahip öğeler için desteklenir **. Not.** Daha fazla bilgi için bkz [. Öğe türleri ve ileti sınıfları](/office/vba/outlook/Concepts/Forms/item-types-and-message-classes).|
|İleti boyutu sınırları|Office 365 İleti Şifrelemesi en fazla 25 megabaytlık iletileri şifreleyebilir. İleti boyutu sınırları hakkında daha fazla bilgi için bkz. [Exchange Online Sınırları](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits).|
|E-posta bekletme ilkelerini Exchange Online|Exchange Online şifrelenmiş iletileri depolamaz.|
|Office 365 İleti Şifrelemesi için dil desteği|Office 365 İleti şifrelemesi aşağıdaki gibi Microsoft 365 dillerini destekler: <p> Gelen e-posta iletileri ve ekli HTML dosyaları, gönderenin dil ayarlarına göre yerelleştirilir. <p> Görüntüleme portalı, alıcının tarayıcı ayarlarına göre yerelleştirilir. <p> Şifrelenmiş iletinin gövdesi (içeriği) yerelleştirilmemiş.|
|OME Portalı ve OME Görüntüleyici Uygulaması için gizlilik bilgileri|[Office 365 Microsoft Mesajlaşma Şifreleme Portalı gizlilik bildirimi](https://privacy.microsoft.com/privacystatement), Microsoft'un özel bilgilerinizle ne yaptığı ve neleri yapmadığı hakkında ayrıntılı bilgi sağlar.|

## <a name="frequently-asked-questions-about-legacy-ome"></a>Eski OME hakkında Sık Sorulan Sorular
<a name="LegacyServiceInfo"> </a>

Office 365 İleti Şifrelemesi hakkında sorularınız mı var? İşte bazı yanıtlar. İhtiyacınız olanı bulamıyorsanız [Office 365 için Microsoft Tech Community forumlarına](https://techcommunity.microsoft.com/t5/Office-365/ct-p/Office365) bakın.

 **S. Kullanıcılarım kuruluş dışındaki alıcılara şifreli e-posta iletileri gönderiyor. Office 365 İleti Şifrelemesi ile şifrelenmiş e-posta iletilerini okumak ve yanıtlamak için dış alıcıların yapması gereken bir şey var mı?**

Microsoft 365 şifreli iletileri alan kuruluşunuzun dışındaki alıcılar bunları iki yoldan biriyle görüntüleyebilir:

- Microsoft hesabıyla veya Office 365 ile ilişkilendirilmiş bir iş veya okul hesabıyla oturum açarak.

- Tek seferlik geçiş kodu kullanarak.

 **S. Microsoft 365 şifreli iletileri bulutta mı yoksa Microsoft sunucularında mı depolanıyor?**

Hayır, şifrelenmiş iletiler alıcının e-posta sisteminde tutulur ve alıcı iletiyi açtığında, microsoft sunucularında görüntülenmek üzere geçici olarak gönderilir. İletiler orada depolanmaz.

 **S. Şifrelenmiş e-posta iletilerini markamla özelleştirebilir miyim?**

Evet. Exchange Online PowerShell cmdlet'lerini kullanarak şifrelenmiş e-posta iletilerinin en üstünde görünen varsayılan metni, yasal uyarı metnini ve e-posta iletisi ile şifreleme portalında kullanmak istediğiniz logoyu özelleştirebilirsiniz. Bu özellik artık OMEv2'de kullanılabilir. Ayrıntılar için bkz. [Şifrelenmiş iletilere marka ekleme](add-your-organization-brand-to-encrypted-messages.md).

 **S. Hizmet, kuruluşumdaki her kullanıcı için bir lisans gerektiriyor mu?**

Kuruluştaki şifrelenmiş e-posta gönderen her kullanıcı için bir lisans gereklidir.

 **S. Dış alıcılar için abonelik gerekiyor mu?**

Hayır, dış alıcıların şifrelenmiş iletileri okuması veya yanıtlaması için abonelik gerekmez.

 **S. Office 365 İleti Şifrelemesi'nin Rights Management Services'ten (RMS) farkı nedir?**

RMS, aşağıdakiler gibi yerleşik şablonlar sağlayarak kuruluşun iç e-postaları için Bilgi Hakları Koruması özellikleri sağlar: İletme ve Şirkete Özel. Office 365 İleti Şifrelemesi, hem dış alıcılara hem de iç alıcılara gönderilen iletiler için e-posta iletisi şifrelemesini destekler.

 **S. Office 365 İleti Şifrelemesi'nin S/MIME'den farkı nedir?**

S/MIME temelde bir istemci tarafı şifreleme teknolojisidir ve karmaşık sertifika yönetimi ve yayımlama altyapısı gerektirir. Office 365 İleti Şifrelemesi posta akışı kurallarını (aktarım kuralları olarak da bilinir) kullanır ve sertifika yayımlamaya bağımlı değildir.

 **S. Şifrelenmiş iletileri mobil cihazlar üzerinden okuyabilir miyim?**

Evet, Google Play mağazasından ve Apple App Store'dan OME Görüntüleyicisi uygulamalarını indirerek mesajları Android ve iOS'ta görüntüleyebilirsiniz. OME Görüntüleyicisi uygulamasında HTML ekini açın ve ardından şifrelenmiş iletinizi açmak için yönergeleri izleyin. Posta istemciniz Form Post'u desteklediği sürece diğer mobil cihazlar için HTML ekini açabilirsiniz.

 **S. Yanıtlar ve iletilen iletiler şifrelenir mi?**

Evet. Yanıtlar iş parçacığı süresi boyunca şifrelenmeye devam eder.

 **S. Office 365 İleti Şifrelemesi yerelleştirme sağlar mı?**

Gelen e-posta ve HTML içeriği, gönderen e-posta ayarlarına göre yerelleştirilir. Görüntüleme portalı, alıcının tarayıcı ayarlarına göre yerelleştirilir. Ancak, şifrelenmiş iletinin gerçek gövdesi (içeriği) yerelleştirilmemiştir.

 **S. Office 365 İleti Şifrelemesi için hangi şifreleme yöntemi kullanılır?**

Office 365 İleti Şifrelemesi, şifreleme altyapısı olarak Rights Management Services 'ı (RMS) kullanır. Kullanılan şifreleme yöntemi, iletileri şifrelemek ve şifresini çözmek için kullanılan RMS anahtarlarını nereden aldığınıza bağlıdır.

- Anahtarları almak için Microsoft Azure RMS kullanırsanız Şifreleme Modu 2 kullanılır. Şifreleme Modu 2, güncelleştirilmiş ve geliştirilmiş bir AD RMS şifreleme uygulamasıdır. İmza ve şifreleme için RSA 2048'i ve imza için SHA-256'yı destekler.

- Anahtarları almak için Active Directory (AD) RMS kullanıyorsanız Şifreleme Modu 1 veya Şifreleme Modu 2 kullanılır. Kullanılan yöntem, şirket içi AD RMS dağıtımınıza bağlıdır. Şifreleme Modu 1, özgün AD RMS şifreleme uygulamasıdır. İmza ve şifreleme için RSA 1024'i ve imza için SHA-1'i destekler. Bu mod, RMS'nin tüm geçerli sürümleri tarafından desteklenmeye devam eder.

Daha fazla bilgi için bkz. [AD RMS Şifreleme Modları](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh867439(v=ws.10)).

**S. Neden bazı şifreli iletiler Office365@messaging.microsoft.com geldiğini söylüyor** ?

Şifreleme portalından veya OME Görüntüleyicisi uygulamasından şifrelenmiş bir yanıt gönderildiğinde, şifrelenmiş ileti bir Microsoft uç noktası üzerinden gönderildiğinden, gönderen e-posta adresi Office365@messaging.microsoft.com olarak ayarlanır. Bu, şifrelenmiş iletilerin istenmeyen posta olarak işaretlenmesini önlemeye yardımcı olur. E-postada görüntülenen ad ve şifreleme portalındaki adres bu etiketleme nedeniyle değiştirilmez. Ayrıca, bu etiketleme yalnızca portaldan gönderilen iletiler için geçerlidir, diğer e-posta istemcilerinden değil.

 **S. Exchange Barındırılan Şifreleme (EHE) abonesiyim. Office 365 İleti Şifrelemesi'ne yükseltme hakkında nereden daha fazla bilgi edinebilirim?**

Tüm EHE müşterileri Office 365 İleti Şifrelemesi'ne yükseltildi. Daha fazla bilgi için [Exchange Barındırılan Şifreleme Yükseltme Merkezi'ni ziyaret edin](../security/office-365-security/exchange-online-protection-overview.md).

 **S. Office 365 İleti Şifrelemesini desteklemek için kuruluşumun güvenlik duvarındaki URL'leri, IP adreslerini veya bağlantı noktalarını açmam gerekiyor mu?**

Evet. Office 365 İleti Şifrelemesi ile şifrelenen iletiler için kimlik doğrulamasını etkinleştirmek için kuruluşunuzun izin verme listesine Exchange Online URL'leri eklemeniz gerekir. Exchange Online URL'lerin listesi için bkz. [Microsoft 365 URL'leri ve IP adresi aralıkları](../enterprise/urls-and-ip-address-ranges.md).

 **S. Microsoft 365 şifreli iletisini kaç alıcıya gönderebilirim?**

Alıcı sınırı, ileti başına 500 alıcıdır veya dağıtım listesi genişletildikten sonra birleştirildiğinde iletinin **Kime** alanında 11.980 karakter (hangisi önce gerçekleşirse) olur.

 **S. Belirli bir alıcıya gönderilen iletiyi iptal etmek mümkün mü?**

Hayır. İleti gönderildikten sonra belirli bir kişiye ileti gönderemezsiniz.

 **S. Alınan ve okunan şifrelenmiş iletilerin raporunu görüntüleyebilir miyim?**

Şifrelenmiş bir iletinin görüntülenip görüntülenmediğini gösteren bir rapor yoktur, ancak örneğin belirli bir posta akışı kuralıyla (aktarım kuralı olarak da bilinir) eşleşen ileti sayısını belirlemek için kullanabileceğiniz Microsoft 365 raporları vardır.

 **S. Microsoft, OME Portalı ve OME Görüntüleyici Uygulaması aracılığıyla sağladığım bilgilerle ne yapar?**

[Office 365 Microsoft Mesajlaşma Şifreleme Portalı gizlilik bildirimi](https://privacy.microsoft.com/privacystatement), Microsoft'un özel bilgilerinizle ne yaptığı ve neleri yapmadığı hakkında ayrıntılı bilgi sağlar.

**S. İstedikten sonra tek seferlik geçiş kodunu alamazsam ne yapmalıyım?**

İlk olarak, e-posta istemcinizdeki gereksiz veya istenmeyen posta klasörünü denetleyin. Kuruluşunuzun DKIM ve DMARC ayarları bu e-postaların istenmeyen posta olarak filtrelenmesine neden olabilir.

Ardından, Güvenlik & Uyumluluk Merkezi'nde karantinayı denetleyin. Genellikle, tek seferlik bir geçiş kodu içeren iletiler, özellikle kuruluşunuzun ilk aldığı iletiler karantinaya alınıyor.
