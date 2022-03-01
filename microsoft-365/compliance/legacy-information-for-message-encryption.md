---
title: Yeni e-Office 365 İleti Şifrelemesi
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
description: Eski dosyaları kuruluş için OME Office 365 İleti Şifrelemesi geçişini anlıyoruz.
ms.openlocfilehash: 6213aec3edd8d55c21ba4137a2052b08147aedc3
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2022
ms.locfileid: "63010053"
---
# <a name="legacy-information-for-office-365-message-encryption"></a>Yeni e-Office 365 İleti Şifrelemesi

Henüz organizasyonlarınızı yeni OME özelliklerine taşıdıysanız, ancak OME'nin zaten dağıtmış olduğu bilgiler, bu makaledeki bilgiler organizasyonunız için geçerlidir. Microsoft, yeni OME özelliklerine, kurum için uygun olduğu anda bir plan yapmanızı önerir. Yönergeler için bkz[. Azure Information Protection Office 365 İleti Şifrelemesi üzerine yerleşik yeni güvenlik özellikleri ayarlama](set-up-new-message-encryption-capabilities.md). Yeni becerilerin nasıl ilk kez çalışması hakkında daha fazla bilgi almak için [bkz. Office 365 İleti Şifrelemesi](ome.md). Bu makalenin kalan bölümü, yeni OME özelliklerini piyasaya çıkarmadan önce OME davranışını ifade eder.

Bu Office 365 İleti Şifrelemesi, kuruluş içindeki ve dışındaki kişiler arasında şifrelenmiş e-posta iletileri gönderebilir ve alabilirsiniz. Office 365 İleti Şifrelemesi. Outlook.com, Yahoo, Gmail ve diğer e-posta hizmetleriyle çalışır. E-posta iletisi şifrelemesi, yalnızca hedeflenen alıcıların ileti içeriğini görüntüleyemelerini sağlamaya yardımcı olur.

İşte birkaç örnek:

- Bir banka çalışanı müşterilere kredi kartı deyimleri gönderiyor
- Sigorta şirketi temsilcisi müşterilere ilke ayrıntıları sağlar
- Kredi aracısı, kredi uygulaması için müşteriden finansal bilgi istiyor
- Sağlık sağlayıcısı hastalar için sağlık hizmetleri bilgilerini gönderiyor
- Bir avukat müşteri veya başka bir avukata gizli bilgiler gönderiyor

## <a name="how-office-365-message-encryption-works-without-the-new-capabilities"></a>Yeni Office 365 İleti Şifrelemesi olmadan nasıl çalışır?

Office 365 İleti Şifrelemesi, Hak Yönetimi (Azure RMS) Microsoft Azure bir çevrimiçi hizmettir. Azure RMS ile yöneticiler şifreleme koşullarını belirlemek için posta akışı kurallarını tanımlayabilir. Örneğin, kural, belirli bir alıcıya gönderilen tüm iletilerin şifrelenirken şifrelenir.

Birisi bir şifreleme kuralıyla eşleşen bir Exchange Online e-posta iletisi gönderdiğinde, ileti bir HTML ekiyle gönderilir. Alıcı HTML ekını açar ve posta portalında şifrelenmiş iletiyi görüntüleme Office 365 İleti Şifrelemesi izler. Alıcı, Microsoft hesabıyla ya da Office 365 ile ilişkilendirilmiş bir iş veya okulla oturum açın ya da tek seferlik geçiş kodu kullanarak iletiyi görüntülemeyi seçebilir. Her iki seçenek de, şifrelenmiş iletiyi yalnızca hedeflenen alıcının görüntüleye olduğundan emin olmak için yardımcı olur. Bu işlem, yeni OME özellikleri için çok farklıdır.

Aşağıdaki diyagramda, şifreleme ve şifre çözme işlemi aracılığıyla bir e-posta iletisinin pasajı özetlenir.

![Şifreli bir e-postanın yolunu gösteren diyagram.](../media/O365-Office365MessageEncryption-Concept.png)

Daha fazla bilgi için [bkz. Yeni OME Office 365 İleti Şifrelemesi öncesi eski işletim sistemi özellikleriyle ilgili hizmet bilgileri](legacy-information-for-message-encryption.md#LegacyServiceInfo).

## <a name="defining-mail-flow-rules-for-office-365-message-encryption-that-dont-use-the-new-ome-capabilities"></a>Yeni OME Office 365 İleti Şifrelemesi kullanmayan e-postalar için posta akış kurallarını tanımlama

Kullanıcıların yeni Office 365 İleti Şifrelemesi olmadan e-postayı etkinleştirmek için, Exchange Online ve Exchange Online Protection yöneticileri posta Exchange kurallarını tanımlar. Bu kurallar, hem e-posta iletilerinin şifrelenmeleri gereken koşullar hem de ileti şifrelemesini kaldırma koşullarını belirler. Bir şifreleme eylemi kural için ayar olduğunda, hizmet iletileri göndermeden önce kural koşullarına uygun tüm iletiler üzerinde eylemi gerçekleştirir.

Posta akış kuralları esnektir ve koşulları bir araya getirir ve böylelikle tek bir kuralda belirli güvenlik gereksinimlerini karşılar. Örneğin, belirtilen anahtar sözcükleri içeren ve dış alıcılara gönderilen tüm iletileri şifrelemek için bir kural oluşturabilirsiniz. Office 365 İleti Şifrelemesi e-posta alıcılarından gelen yanıtları da şifreler ve e-posta kullanıcılarınıza kolaylık sağlamak için bu yanıtların şifresini çözen bir kural oluşturabilirsiniz. Bu şekilde, kurumuz kullanıcılar yanıtları görüntülemek için şifreleme portalında oturum açmaz.

Posta akış kuralları oluşturma hakkında daha Exchange için bkz. Posta akış [kuralları için Office 365 İleti Şifrelemesi](define-mail-flow-rules-to-encrypt-email.md).

### <a name="use-the-eac-to-create-a-mail-flow-rule-for-encrypting-email-messages-without-the-new-ome-capabilities"></a>Yeni OME özellikleri olmadan e-posta iletilerini şifrelemek için e-posta akış kuralı oluşturmak üzere EAC kullanma

1. Web tarayıcısında, genel yönetici izinlerine sahip bir iş veya okul hesabı kullanarak [Office 365.](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser)

2. Yönetici **kutucuğunu** seçin.

3. Genel Microsoft 365 yönetim merkezi Yönetim **merkezleri'ni Exchange**\>.<a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank"></a>

4. EAC'de, Posta akışı **Kuralları'ne gidin** \> **ve** Yeni Yeni **simgesi'yi** ![seçin.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Yeni kural oluşturma**. EAC'nin kullanımı hakkında daha fazla bilgi için bkz[. Exchange Yönetim Merkezi'Exchange Online](/exchange/exchange-admin-center).

5. Ad **kutusuna** kural için Bir ad yazın; örneğin Posta şifreleme DrToniRamos@hotmail.com.

6. Bu **kuralı uygula altında bir** koşul seçin ve gerekirse bir değer girin. Örneğin, iletileri şifrelemek için şunları DrToniRamos@hotmail.com:

   1. Şu **durumda bu kuralı uygula'da** **alıcıyı seçin**.

   2. Kişi listesinden mevcut bir adı seçin veya onay adları kutusuna yeni bir **e-posta adresi** yazın.

      - Var olan bir adı seçmek için, listeden adı seçin ve ardından Tamam'a **tıklayın**.

      - Yeni bir ad girmek için, onay adları kutusuna bir **e-posta adresi yazın** ve adları onayla **Tamam'ı** \> **seçin**.

7. Daha fazla koşul eklemek için Diğer **seçenekler'i** , sonra koşul **ekle'yi seçin** ve listeden seçim yapabilirsiniz.

   Örneğin, kuralı yalnızca alıcı kuruluş dışında olursa uygulamak için koşul ekle'yi seçin ve sonra  Alıcı, Kuruluş dışında **/** \> şirket dışında **Tamam'ı** \> **seçin**.

8. Yeni OME özelliklerini kullanmadan şifrelemeyi etkinleştirmek için,  \> Aşağıdakini yapın'da İleti güvenliğini değiştir'i seçin. **OME'nin** önceki sürümünü uygula'ya ve sonra da Kaydet'e **tıklayın**.

   IRM lisansının etkinleştirilmemiş olduğu hatasını alırsanız eski OME'yi kullanasınız.

9. (İsteğe bağlı) Başka **bir eylem belirtmek** için Eylem ekle'yi seçin.

### <a name="use-exchange-online-powershell-to-create-a-mail-flow-rule-for-encrypting-email-messages-without-the-new-ome-capabilities"></a>Yeni Exchange Online OME özellikleri olmadan e-posta iletilerini şifrelemek için bir posta akış kuralı oluşturmak üzere PowerShell'i kullanma

1. Exchange Online PowerShell’e bağlanın. Daha fazla bilgi için bkz[. Bağlan PowerShell Exchange Online e geri Exchange Online.](/powershell/exchange/connect-to-exchange-online-powershell)

2. **New-TransportRule cmdlet'ini** kullanarak bir kural oluşturun ve _ApplyOME_ parametresini 'a ayarlayın`$true`.

   Bu örnekte, bu e-posta iletilerine gönderilen DrToniRamos@hotmail.com şifrelenmeleri gerekir.

   ```powershell
   New-TransportRule -Name "Encrypt rule for Dr Toni Ramos" -SentTo "DrToniRamos@hotmail.com" -SentToScope "NotinOrganization" -ApplyOME $true
   ```

   Burada,

   - Yeni kuralın benzersiz adı "Dr Toni Ramos için kuralı şifrele" şeklindedir.
   - _SentTo parametresi_ ileti alıcılarını (ad, e-posta adresi, ayırt edici ad vb. ile tanımlanır) belirtir. Bu örnekte alıcı, "Adres" e-posta adresiyle DrToniRamos@hotmail.com.
   - _SentToScope_ parametresi ileti alıcılarının konumunu belirtir. Bu örnekte, alıcının posta kutusu Hotmail'dedir ve kuruluşun bir parçası değildir; dolayısıyla değer `NotInOrganization` kullanılır.

   Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-TransportRule](/powershell/module/exchange/New-TransportRule).

### <a name="remove-encryption-from-email-replies-encrypted-without-the-new-ome-capabilities"></a>Yeni OME özellikleri olmadan şifrelenen e-posta yanıtlarından şifrelemeyi kaldırma

E-posta kullanıcılarınız şifrelenmiş iletiler gönderirken, bu iletilerin alıcıları şifrelenmiş yanıtlarla yanıt gönderebilir. E-posta kullanıcılarının iletileri görüntülemek için şifreleme portalında oturum açmaları gerektirsin diye yanıtlardan şifrelemeyi otomatik olarak kaldırmak için posta akışı kuralları oluşturabilirsiniz. Bu kuralları tanımlamak için EAC veya Windows PowerShell cmdlet'lerini kullanabilirsiniz. Şifresini çözebilirsiniz ve bu iletilerin şifresini çözebilirsiniz ve bu iletiler kuruluş içinden gönderilen iletilere yanıt olarak gönderilir. Kuruluş dışından kaynaklanan şifreli iletilerin şifresini çözesiniz.

#### <a name="use-the-eac-to-create-a-rule-for-removing-encryption-from-email-replies-encrypted-without-the-new-ome-capabilities"></a>Yeni OME özellikleri olmadan şifrelenmiş e-posta yanıtlarından şifrelemeyi kaldırmak için EAC'i kullanma

1. Bir web tarayıcısında, yönetici izinleri verilmiş olan bir iş veya okul hesabı [kullanarak Office 365.](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser)

2. Yönetici **kutucuğunu** seçin.

3. Daha fazla bilgi >Microsoft 365 yönetim merkezi Yönetim **merkezleri'ni** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">**Exchange**</a>.

4. EAC'de, Posta akışı **Kuralları'ne gidin** \> **ve** Yeni Yeni **simgesi'yi** ![seçin.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Yeni kural oluşturma**. EAC'nin kullanımı hakkında daha fazla bilgi için bkz[. Exchange Yönetim Merkezi'Exchange Online](/exchange/exchange-admin-center).

5. Ad **kutusuna** kural için bir ad yazın; örneğin Gelen postadan şifrelemeyi kaldır.

6. Alıcı **Kuruluş içinde yer alıyor** gibi iletilerden şifrelemenin kaldırılması gereken koşulları seçerse Bu **kuralı** \> **uygula'da.**

7. Bunu **yapın'da** İleti **güvenliğini değiştir OME'nin** \> **önceki sürümünü kaldır'ı seçin**.

8. **Kaydet**'i seçin.

#### <a name="use-exchange-online-powershell-to-create-a-rule-to-remove-encryption-from-email-replies-encrypted-without-the-new-ome-capabilities"></a>Yeni OME Exchange Online olmadan şifrelenmiş e-posta yanıtlarından şifrelemeyi kaldırmak üzere bir kural oluşturmak için PowerShell'i kullanma

1. Exchange Online PowerShell’e bağlanın. Daha fazla bilgi için bkz[. Bağlan PowerShell Exchange Online e geri Exchange Online.](/powershell/exchange/connect-to-exchange-online-powershell)

2. **New-TransportRule cmdlet'ini** kullanarak bir kural oluşturun ve _RemoveOME parametresini 'a_ ayarlayın`$true`.

   Bu örnek, kuruluşta alıcılara gönderilen tüm postalardan şifrelemeyi kaldırır.

   ```powershell
   New-TransportRule -Name "Remove encryption from incoming mail" -SentToScope "InOrganization" -RemoveOME $true
   ```

   Burada,

   - Yeni kuralın benzersiz adı "Gelen postadan şifrelemeyi kaldır" adıdır.
   - _SentToScope_ parametresi ileti alıcılarının konumunu belirtir. Bu örnekte, değer `InOrganization` değeri kullanılır ve bu da aşağıdakilerden birini gösterir:
     - Alıcı, kurum içinde posta kutusu, posta kullanıcısı, grup veya posta özelliği etkin bir ortak klasördür.
     - Alıcının e-posta adresi yetkili etki alanı veya kuruluşta iç geçiş etki alanı olarak yapılandırılmış kabul edilen bir etki alanındadır ve ileti kimliği doğrulanmış bir bağlantı üzerinden gönderilmiş veya alınmıştır. 

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-TransportRule](/powershell/module/exchange/New-TransportRule).

## <a name="sending-viewing-and-replying-to-messages-encrypted-without-the-new-capabilities"></a>Yeni özellikler olmadan şifrelenmiş iletileri gönderme, görüntüleme ve yanıtlama

Otomatik Office 365 İleti Şifrelemesi, e-posta iletileri yönetici tanımlı kurallara göre otomatik olarak şifrelenir. Şifreli bir iletiyi alıcının Gelen Kutusu'na ekli bir HTML dosyasıyla birlikte gönderen bir e-posta gelir.

Alıcılar iletide verilen yönergeleri izleyerek eki açar ve Microsoft hesabı ya da Microsoft hesabı ya da microsoft hesabıyla ilişkilendirilmiş bir iş veya Office 365. Alıcıların iki hesabı da yoksa, şifreli iletiyi görüntülemek için oturum açmalarına izin vermeleri için bir Microsoft hesabı oluşturmaları gönderilir. Alternatif olarak, alıcılar iletiyi görüntülemek için tek seferlik geçiş kodu alır. Oturum açtıktan veya tek seferlik geçiş kodunu kullandıktan sonra, alıcılar şifresi çözülen iletiyi görüntüler ve şifrelenmiş bir yanıt gönderebilir.

## <a name="customize-encrypted-messages-with-office-365-message-encryption"></a>Şifreli iletileri iletilerle Office 365 İleti Şifrelemesi

Bir Exchange Online yöneticisi Exchange Online Protection olarak, şifrelenmiş iletilerinizi özelleştirebilirsiniz. Örneğin, şirketinizin markasını ve logosunu ekleyebilir, bir giriş belirtebilirsiniz ve şifreli iletilerde ve alıcıların şifreli iletilerinizi görüntüley haberleri olduğu portalda tekz yazı  eklersiniz. Bu Windows PowerShell cmdlet'lerini kullanarak, şifreli e-posta iletilerini alıcıları için görüntüleme deneyiminin aşağıdaki yönlerini özelleştirebilirsiniz:

- Şifreli iletiyi içeren e-postanın giriş metni
- Şifreli iletiyi içeren e-postanın yasal uyarı metni
- Portal metni, portalı görüntüleme iletisinde görünür
- E-posta iletisinde ve portal görüntülemede görünen logo

Ayrıca, herhangi bir anda varsayılan görünüme ve görünüme geri dönabilirsiniz.

Aşağıdaki örnekte, e-posta ekine ContosoPharma için özel bir logo gösterir:

> [!div class="mx-imgBorder"]
> ![Görünüm şifreli ileti sayfasının örneği.](../media/TA-OME-3attachment2.jpg)

### <a name="to-customize-encryption-email-messages-and-the-encryption-portal-with-your-organizations-brand"></a>Şifreleme e-posta iletilerini ve şifreleme portalını kuruluş markasıyla özelleştirmek için

1. Bağlan PowerShell Exchange Online'i kullanma konusunda açıklandığı [gibi Uzak PowerShell Bağlan Exchange Online kadar kullanabilirsiniz](/powershell/exchange/connect-to-exchange-online-powershell).

2. Aşağıda Set-OMEConfiguration cmdlet'ini kullanın: [Set-OMEConfiguration veya](/powershell/module/exchange/set-omeconfiguration) kılavuz için aşağıdaki tabloyu kullanın.

   **Şifreleme özelleştirme seçenekleri**

   |Şifreleme deneyiminin bu özelliğini özelleştirmek için|Bu Windows PowerShell kullanın|
   |---|---|
   |Şifreli e-posta iletilerine eşlikan varsayılan metin <p> Şifreli iletileri görüntüleme yönergelerinin üzerinde varsayılan metin görüntülenir|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -EmailText "<string of up to 1024 characters>"` <p> **Örnek:** `Set-OMEConfiguration -Identity "OME Configuration" -EmailText "Encrypted message from ContosoPharma secure messaging system"`|
   |Şifreli iletiyi içeren e-postada Yasal Uyarı bildirimi|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> DisclaimerText "<your disclaimer statement, string of up to 1024 characters>"` <p> **Örnek:** `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText "This message is confidential for the use of the addressee only"`|
   |Şifreli posta görüntüleme portalının en üstünde görünen metin|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -PortalText "<text for your portal, string of up to 128 characters>"` <p> **Örnek:** `Set-OMEConfiguration -Identity "OME Configuration" -PortalText "ContosoPharma secure email portal"`|
   |Logo|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -Image <Byte[]>` <p> **Örnek:** `Set-OMEConfiguration -Identity "OME configuration" -Image ([System.IO.File]::ReadAllBytes('C:\Temp\contosologo.png'))` <p> Desteklenen dosya biçimleri: .png, .jpg, .bmp veya .tiff <p> Logo dosyasının en iyi boyutu: 40 KB'den küçük <p> Logo resminin en uygun boyutu: 170x70 piksel|

### <a name="to-remove-brand-customizations-from-encryption-email-messages-and-the-encryption-portal"></a>Şifreleme e-posta iletilerinden ve şifreleme portalında marka özelleştirmelerini kaldırmak için

1. Bağlan PowerShell Exchange Online'i kullanma konusunda açıklandığı [gibi Uzak PowerShell Bağlan Exchange Online kadar kullanabilirsiniz](/powershell/exchange/connect-to-exchange-online-powershell).

2. Aşağıda açıklandığı Set-OMEConfiguration kullanın: [Set-OMEConfiguration](/powershell/module/exchange/set-omeconfiguration). DisclaimerText, EmailText ve PortalText değerlerinden, organizasyon markalı özelleştirmelerini kaldırmak için, değeri boş bir dizeye, ayarlayın. `""` Logo gibi tüm resim değerleri için değeri olarak ayarlayın `"$null"`.

   **Şifreleme özelleştirme seçenekleri**

   |Şifreleme deneyiminin bu özelliğini varsayılan metin ve görüntüye geri döndürme|Bu Windows PowerShell kullanın|
   |---|---|
   |Şifreli e-posta iletilerine eşlikan varsayılan metin <p> Şifreli iletileri görüntüleme yönergelerinin üzerinde varsayılan metin görüntülenir|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -EmailText "<empty string>"` <p> **Örnek:** `Set-OMEConfiguration -Identity "OME Configuration" -EmailText ""`|
   |Şifreli iletiyi içeren e-postada Yasal Uyarı bildirimi <p> |`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> DisclaimerText "<empty string>"` <p> **Örnek:** `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText ""`|
   |Şifreli posta görüntüleme portalının en üstünde görünen metin|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -PortalText "<empty string>"` <p> **Varsayılan değere geri döndürülen örnek:** `Set-OMEConfiguration -Identity "OME Configuration" -PortalText ""`|
   |Logo|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -Image <"$null">` <p> **Varsayılan değere geri döndürülen örnek:** `Set-OMEConfiguration -Identity "OME configuration" -Image $null`|

## <a name="service-information-for-legacy-office-365-message-encryption-prior-to-the-release-of-the-new-ome-capabilities"></a>Yeni OME Office 365 İleti Şifrelemesi öncesi eski sürümler için hizmet bilgileri
<a name="LegacyServiceInfo"> </a>

Aşağıdaki tablo, yeni OME Office 365 İleti Şifrelemesi öncesi hizmet için teknik ayrıntılar sağlar.

|Hizmet ayrıntıları|Açıklama|
|---|---|
|İstemci cihazı gereksinimleri|HTML eki Form Gönderisini destekleyen modern bir tarayıcıda açılabilir olduğu sürece, şifrelenmiş iletiler tüm istemci cihazlarında ılabilir.|
|Şifreleme algoritması ve Federal Bilgi İşleme Standartları (FIPS) uyumluluğu|Office 365 İleti Şifrelemesi Azure Bilgi Hakları Yönetimi (IRM) ile aynı şifreleme anahtarlarını kullanır ve Şifreleme Modu 2'Windows (RSA için 2K anahtar ve SHA-1 sistemleri için 256 bit tuşu) destekler. Temel IRM şifreleme modları hakkında daha fazla bilgi için bkz. [AD RMS Şifreleme Modları](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh867439(v=ws.10)).|
|Desteklenen ileti türleri|Office 365 İleti Şifrelemesi IPM ileti sınıfı kimliğine sahip öğeler için **destekler. Not**. Daha fazla bilgi için bkz [. Öğe türleri ve ileti sınıfları](/office/vba/outlook/Concepts/Forms/item-types-and-message-classes).|
|İleti boyutu sınırları|Office 365 İleti Şifrelemesi 25 megabayta kadar olan iletileri şifreler. İleti boyutu sınırları hakkında daha fazla ayrıntı için bkz. [Exchange Online tıklayın](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits).|
|Exchange Online-posta bekletme ilkelerini gönderme|Exchange Online iletileri depolamaz.|
|Destek için dil Office 365 İleti Şifrelemesi|Office 365 şifreleme, aşağıdaki Microsoft 365 dilleri destekler: <p> Gelen e-posta iletileri ve ekli HTML dosyaları, gönderenin dil ayarlarına göre yerelleştirilmiştir. <p> Görüntüleme portalı, alıcının tarayıcı ayarlarına göre yerelleştirilmiştir. <p> Şifreli iletinin gövdesi (içeriği) yerelleştirilmiş değildir.|
|OME Portalı ve OME Görüntüleyicisi Uygulaması için gizlilik bilgileri|Microsoft [Office 365 Şifreleme Portalı](https://privacy.microsoft.com/privacystatement) gizlilik bildirimi, Microsoft'un özel bilgilerinizi kullanarak ne yaptığını ve bu konuda bir şey yapmama hakkında ayrıntılı bilgi sağlar.|

## <a name="frequently-asked-questions-about-legacy-ome"></a>Eski OME hakkında Sık Sorulan Sorular
<a name="LegacyServiceInfo"> </a>

Bu konuda sorularınız Office 365 İleti Şifrelemesi? İşte bazı yanıtlar. Size gerekenleri bulamıyorsanız, daha fazla bilgi için [Microsoft Tech Community forumlarına Office 365](https://techcommunity.microsoft.com/t5/Office-365/ct-p/Office365).

 **Q. Kullanıcılarım, kuruluşlarımızın dışındaki alıcılara şifreli e-posta iletileri gönderiyor. Dış alıcıların e-posta iletileriyle şifrelenmiş e-posta iletilerini okumak ve yanıtlamak için bir şey yapmaları Office 365 İleti Şifrelemesi?**

Şifreli ileti alan ve Microsoft 365 olan alıcılar, bunları iki şekilden birini görüntüleyebilirsiniz:

- Microsoft hesabıyla ya da microsoft hesabıyla ilişkilendirilmiş bir iş veya okul hesabıyla oturum Office 365.

- Tek seferlik geçiş kodu kullanarak.

 **Q. Şifrelenmiş Microsoft 365 bulutta mı yoksa Microsoft sunucularında mı depolanıyor?**

Hayır, şifreli iletiler alıcının e-posta sisteminde tutulur ve alıcı iletiyi açtığında, geçici olarak Microsoft sunucularında görüntülemek için gönderilir. İletiler burada depolanmaz.

 **Q. Şifreli e-posta iletilerini markam ile özelleştirilebilir miyim?**

Evet. Windows PowerShell cmdlet'lerini kullanarak, şifrelenmiş e-posta iletilerinin üstünde görünen varsayılan metni, e-posta iletisi ve şifreleme portalı için kullanmak istediğiniz logoyu özelleştirebilirsiniz. Bu özellik artık OMEv2'de kullanılabilir. Ayrıntılar için bkz [. Şifreli iletilere markalama ekleme](add-your-organization-brand-to-encrypted-messages.md).

 **Q. Bu hizmet kuruluşumda her kullanıcı için bir lisans gerektirir mi?**

Kuruluşta şifreli e-posta gönderen her kullanıcı için bir lisans gereklidir.

 **Q. Dış alıcılar abonelik gerektirir mi?**

Hayır, dış alıcıların şifreli iletileri okuması veya yanıtlaması için abonelik gerektirmez.

 **Q. Hak Yönetimi Office 365 İleti Şifrelemesi (RMS) arasında ne fark vardır?**

RMS, şu tür yerleşik şablonlar sağlayarak kuruluşun dahili e-postaları için Bilgi Hakları Koruma özellikleri sağlar: Iletme ve Şirket için Gizli değil. Office 365 İleti Şifrelemesi hem dış alıcılara hem de iç alıcılara gönderilen iletiler için e-posta iletisi şifrelemesi destekler.

 **Q. S/MIME Office 365 İleti Şifrelemesi den farklı olan nedir?**

S/MIME temelde istemci tarafı bir şifreleme teknolojisidir ve karmaşık sertifika yönetimi ve yayımlama altyapısı gerektirir. Office 365 İleti Şifrelemesi akış kurallarını (aktarım kuralları olarak da bilinir) kullanır ve sertifika yayımlamaya bağlı değildir.

 **Q. Mobil cihazlar üzerinden şifreli iletileri okuyabilir miyim?**

Evet, Google Play mağazasından ve Apple App Store'dan OME Görüntüleyicisi uygulamalarını indirerek Android ve iOS'ta iletileri görüntüleyebilirsiniz. OME Görüntüleyicisi uygulamasında HTML ekini açın ve sonra şifreli iletinizi açmak için yönergeleri izleyin. Diğer mobil cihazlarda, posta istemciniz Form Gönderisi'yi desteklediği sürece HTML ekini açabilirsiniz.

 **Q. Yanıtlar ve iletili iletiler şifrelenir mi?**

Evet. Yanıtlar, ileti dizi süresi boyunca şifrelenmeye devam eder.

 **Q. Yerel Office 365 İleti Şifrelemesi sağlar mı?**

Gelen e-posta ve HTML içeriği, gönderen e-posta ayarlarına göre yerelleştirilmiştir. Görüntüleme portalı, alıcının tarayıcı ayarlarına göre yerelleştirilmiştir. Ancak, şifrelenmiş iletinin gerçek gövdesi (içeriği) yerelleştirilmiş değildir.

 **Q. E-doğrulama için hangi şifreleme Office 365 İleti Şifrelemesi?**

Office 365 İleti Şifrelemesi şifreleme altyapısı olarak Rights Management Services'i (RMS) kullanır. Kullanılan şifreleme yöntemi, iletileri şifrelemek ve şifrelerini çözmek için kullanılan RMS anahtarlarını nereden edin sayfanız olduğuna bağlıdır.

- Anahtarları almak Microsoft Azure RMS kullanıyorsanız Şifreleme Modu 2 kullanılır. Şifreleme Modu 2, güncelleştirilmiş ve geliştirilmiş bir AD RMS şifreleme uygulamasıdır. İmza ve şifreleme için RSA 2048'i destekler ve imza için SHA-256'yı destekler.

- Anahtarları almak için Active Directory (AD) RMS kullanıyorsanız, Şifreleme Modu 1 veya Şifreleme Modu 2 kullanılır. Kullanılan yöntem, şirket içi AD RMS dağıtımınıza bağlıdır. Şifreleme Modu 1, özgün AD RMS şifreleme uygulamasıdır. İmza ve şifreleme için RSA 1024'ü destekler ve imza için SHA-1'i destekler. Bu mod, tüm geçerli RMS sürümleri tarafından destek büyümeye devam eder.

Daha fazla bilgi için bkz [. AD RMS Şifreleme Modları](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh867439(v=ws.10)).

**S. Neden bazı şifreli iletilerde iletilerin e-postadan Office365@messaging.microsoft.com** ?

Şifreleme portalında veya OME Görüntüleyicisi uygulaması aracılığıyla şifrelenmiş bir yanıt gönderiliyorsa, şifrelenmiş ileti bir Microsoft uç noktası üzerinden gönderildiği için Office365@messaging.microsoft.com e-posta adresi Office365@messaging.microsoft.com olarak ayarlanır. Bu, şifreli iletilerin istenmeyen posta olarak işaretlenmelerini önlemeye yardımcı olur. E-postada görüntülenen ad ve şifreleme portalında yer alan adres bu etiket nedeniyle değişmez. Ayrıca, bu etiket diğer e-posta istemcileri üzerinden değil, yalnızca portal aracılığıyla gönderilen iletiler için geçerlidir.

 **Q. Exchange Barındırılan Şifreleme (EHE) abonesiyim. Yeni bir sürüme yükseltme hakkında nereden daha fazla Office 365 İleti Şifrelemesi?**

Tüm EHE müşterileri e-Office 365 İleti Şifrelemesi. Daha fazla bilgi için Barındırılan [Şifreleme Exchange Merkezi'ne bakın](../security/office-365-security/exchange-online-protection-overview.md).

 **Q. Kuruluşumda destek olmak için güvenlik duvarında URL'leri, IP adreslerini veya bağlantı noktalarını açmam Office 365 İleti Şifrelemesi?**

Evet. E-posta tarafından şifrelenen iletilerde Exchange Online kimlik doğrulamasını etkinleştirmek için, bu iletilerin URL'lerini Office 365 İleti Şifrelemesi. URL'leri Exchange Online için bkz. [MICROSOFT 365 VE IP adresi aralıkları](../enterprise/urls-and-ip-address-ranges.md).

 **Q. Şifreli bir iletiyi kaç Microsoft 365 gönderebilirim?**

Alıcı sınırı ileti başına 500 alıcıdır veya dağıtım listesi genişletildikten sonra bir araya geldiğinde, iletinin Son alanında (hangisi önce gelirse) 11.980 karakterdir.

 **Q. Belirli bir alıcıya gönderilen bir iletiyi iptal etmek mümkün mü?**

Hayır. Gönderildikten sonra belirli bir kişiye gönderilen iletiyi iptal etmeyebilirsiniz.

 **Q. Alınan ve okunan şifreli iletilerin raporunu  görüntülemem gerekir mi?**

Şifreli bir iletinin görüntülenen sayısını gösteren bir rapor yok, ancak örneğin belirli bir posta akışı kuralıyla (aktarım kuralı olarak da bilinir) eşlenen ileti sayısını belirlemek için yararlanabilirsiniz Microsoft 365 raporları da vardır.

 **Q. Microsoft, OME Portalı ve OME Görüntüleyicisi Uygulaması aracılığıyla bilgilerim ile ne yapar?**

Microsoft [Office 365 Şifreleme Portalı](https://privacy.microsoft.com/privacystatement) gizlilik bildirimi, Microsoft'un özel bilgilerinizi kullanarak ne yaptığını ve bu konuda bir şey yapmama hakkında ayrıntılı bilgi sağlar.

**Q. İsteğim sonrasında tek seferlik geçiş kodunu alam olursa ne yapabilirim?**

İlk olarak, e-posta istemcinizin gereksiz veya istenmeyen posta klasörünü kontrol edin. DkIM ve DMARC ayarları, bu e-postaların istenmeyen posta olarak filtrelenmiş olarak bitimini neden olabilir.

Ardından, Güvenlik ve Uyumluluk Merkezi'nde karantinayı & alın. Çoğu zaman, tek seferlik geçiş kodunu içeren iletiler, özellikle de kuruma ilk alınanlar karantinaya alınır.
