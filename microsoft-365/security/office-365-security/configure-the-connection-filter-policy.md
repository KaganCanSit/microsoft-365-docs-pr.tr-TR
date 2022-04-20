---
title: Varsayılan bağlantı filtresi ilkesini yapılandırma
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 6ae78c12-7bbe-44fa-ab13-c3768387d0e3
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler, e-posta sunucularından gelen e-postalara izin vermek veya bunları engellemek için Exchange Online Protection 'de (EOP) bağlantı filtrelemeyi yapılandırmayı öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0c09f445bf3d204f9e22d116dc9fda4c3fea9735
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64974135"
---
# <a name="configure-connection-filtering"></a>Bağlantı filtrelemeyi yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

posta kutuları Exchange Online olan Microsoft 365 bir müşteriyseniz veya Exchange Online olmayan tek başına Exchange Online Protection (EOP) müşterisiyseniz  posta kutuları, iyi veya hatalı kaynak e-posta sunucularını IP adreslerine göre tanımlamak için EOP'de (özellikle varsayılan bağlantı filtresi ilkesi) bağlantı filtrelemeyi kullanırsınız. Varsayılan bağlantı filtresi ilkesinin temel bileşenleri şunlardır:

- **IP İzin Listesi**: IP adresi veya IP adresi aralığına göre belirttiğiniz kaynak e-posta sunucularından gelen tüm iletiler için istenmeyen posta filtrelemesini atlayın. Bu kaynaklardan gelen iletilerde istenmeyen posta filtrelemesinin hala gerçekleşebileceği senaryolar için, bu makalenin [devamında IP İzin Ver Listesindeki kaynaklardan gelen iletilerin hala filtrelendiği senaryolar](#scenarios-where-messages-from-sources-in-the-ip-allow-list-are-still-filtered) bölümüne bakın. IP İzin Verme Listesinin genel güvenilir gönderenler stratejinize nasıl uyması gerektiği hakkında daha fazla bilgi için bkz. [EOP'de güvenilir gönderen listeleri oluşturma](create-safe-sender-lists-in-office-365.md).

- **IP Engelleme Listesi**: IP adresi veya IP adresi aralığına göre belirttiğiniz kaynak e-posta sunucularından gelen tüm iletileri engelleyin. Gelen iletiler reddedilir, istenmeyen posta olarak işaretlenmez ve ek filtreleme gerçekleşmez. IP Engelleme Listesi'nin genel engellenen gönderenler stratejinize nasıl uyması gerektiği hakkında daha fazla bilgi için bkz. [EOP'de engellenen gönderen listeleri oluşturma](create-block-sender-lists-in-office-365.md).

- **Kasa listesi**: *Güvenli liste*, Microsoft veri merkezinde müşteri yapılandırması gerektirmeyen dinamik bir izin verme listesidir. Microsoft bu güvenilir e-posta kaynaklarını aboneliklerden çeşitli üçüncü taraf listelerine tanımlar. Güvenli listenin kullanımını etkinleştirir veya devre dışı bırakırsınız; kaynak e-posta sunucularını güvenli listede yapılandıramazsınız. Güvenli listedeki e-posta sunucularından gelen iletilerde istenmeyen posta filtreleme atlanır.

Bu makalede, Microsoft 365 Microsoft 365 Defender portalında veya PowerShell'de (Exchange Online posta kutuları olan Microsoft 365 kuruluşlar için PowerShell'de Exchange Online) varsayılan bağlantı filtresi ilkesinin nasıl yapılandırıldığı açıklanır ; Exchange Online posta kutusu olmayan kuruluşlar için tek başına EOP PowerShell). EOP'nin bağlantı filtrelemeyi nasıl kullandığı hakkında daha fazla bilgi için bkz. [İstenmeyen posta önleme koruması](anti-spam-protection.md).

> [!NOTE]
> IP İzin Verme Listesi, güvenli liste ve IP Engelleme Listesi, kuruluşunuzda e-postaya izin verme veya e-postayı engelleme stratejinizin bir parçasıdır. Daha fazla bilgi için bkz. [Güvenli gönderen listeleri oluşturma](create-safe-sender-lists-in-office-365.md) ve [Engellenen gönderen listeleri oluşturma](create-block-sender-lists-in-office-365.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını adresinde <https://security.microsoft.com>açarsınız. **İstenmeyen posta önleme ilkeleri** sayfasına doğrudan gitmek için kullanın<https://security.microsoft.com/antispam>.

- Exchange Online PowerShell'e bağlanmak için bkz. [PowerShell'Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell). Tek başına EOP PowerShell'e bağlanmak için bkz. [PowerShell'i Exchange Online Protection için Bağlan](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Bu makaledeki yordamları gerçekleştirebilmeniz için **önce Exchange Online'de** izinlerin atanmış olması gerekir:
  - Varsayılan bağlantı filtresi ilkesini değiştirmek için **Kuruluş Yönetimi** veya **Güvenlik Yöneticisi** rol gruplarının üyesi olmanız gerekir.
  - Varsayılan bağlantı filtresi ilkesine salt okunur erişim için **Genel Okuyucu** veya **Güvenlik Okuyucusu** rol gruplarının üyesi olmanız gerekir.

  Daha fazla bilgi için bkz. [Exchange Online'de İzinler](/exchange/permissions-exo/permissions-exo).

  **Notlar**:

  - kullanıcıları Microsoft 365 yönetim merkezi karşılık gelen Azure Active Directory rolüne eklemek, kullanıcılara Microsoft 365'deki diğer özellikler için gerekli izinleri _ve_ izinleri verir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  - [Exchange Online'daki](/Exchange/permissions-exo/permissions-exo#role-groups) **Yalnızca Görüntüleme Kuruluş Yönetimi** rol grubu da özelliğe salt okunur erişim sağlar.

- İzin vermek veya engellemek istediğiniz e-posta sunucularının (gönderenler) kaynak IP adreslerini bulmak için, ileti üst bilgisindeki bağlanan IP (**CIP**) üst bilgi alanını de kontrol edebilirsiniz. Çeşitli e-posta istemcilerinde ileti üst bilgisini görüntülemek için bkz. [Outlook'de internet iletisi üst bilgilerini görüntüleme](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c).

- IP İzin Verilenler Listesi, IP Engelleme Listesi'ne göre önceliklidir (her iki listede de bir adres engellenmez).

- IP İzin Verilenler Listesi ve IP Blok Listesi en fazla 1273 girdiyi destekler; burada bir girdi tek bir IP adresi, IP adresi aralığı veya Sınıfsız Etki Alanı Arası Yönlendirme (CIDR) IP'dir.

## <a name="use-the-microsoft-365-defender-portal-to-modify-the-default-connection-filter-policy"></a>Varsayılan bağlantı filtresi ilkesini değiştirmek için Microsoft 365 Defender portalını kullanma

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **İstenmeyen posta önleme** bölümüne gidin. **İstenmeyen posta önleme ilkeleri** sayfasına doğrudan gitmek için kullanın<https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme ilkeleri** sayfasında, ilkenin adına tıklayarak listeden **Bağlantı filtresi ilkesi (Varsayılan)** seçeneğini belirleyin.

3. Görüntülenen ilke ayrıntıları açılır öğesinde aşağıdaki ayarlardan herhangi birini yapılandırın:

   - **Açıklama** bölümü: **Adı ve açıklamayı düzenle'ye** tıklayın. Görüntülenen **Adı ve açıklamayı düzenle** açılır menüsüne **Açıklama kutusuna** isteğe bağlı açıklayıcı metin girin.

     Bitirdiğinizde, **Kaydet**'i tıklatın.

   - **Bağlantı filtreleme bölümü**: **Bağlantı filtresi ilkesini düzenle'ye** tıklayın. Görüntülenen açılır öğede aşağıdaki ayarları yapılandırın:

     - **Her zaman aşağıdaki IP adreslerinden veya adres aralığından gelen iletilere izin ver**: Bu, IP İzin Ver listesidir. Kutuya tıklayın, bir değer girin ve enter tuşuna basın veya kutunun altında görüntülenen değerin tamamını seçin. Geçerli değerler şunlardır:
       - Tek IP: Örneğin, 192.168.1.1.
       - IP aralığı: Örneğin, 192.168.0.1-192.168.0.254.
       - CIDR IP: Örneğin, 192.168.0.1/25. Geçerli alt ağ maskesi değerleri /24 ile /32 arasındadır. /1 için istenmeyen posta filtrelemeyi /23'e atlamak için, bu makalenin [devamında sağlanan aralığın dışında bir CIDR IP'sine yönelik istenmeyen posta filtrelemeyi atlama](#skip-spam-filtering-for-a-cidr-ip-outside-of-the-available-range) bölümüne bakın.

       Bu adımı gerektiği kadar tekrarlayın. Mevcut bir değeri kaldırmak için Kaldır'a tıklayın ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) öğesini seçin.

     IP adresini veya adres aralığını eklemek için kutuya tıklayın ve Ekle Simgesi **Ekle'ye** ![tıklayın.](../../media/ITPro-EAC-AddIcon.png). Bir girdiyi kaldırmak için **İzin Verilen IP Adresi'nde** girdiyi seçin ve **kaldır'a tıklayın**![](../../media/scc-remove-icon.png). Bitirdiğinizde, **Kaydet**'i tıklatın.

   - **Her zaman aşağıdaki IP adreslerinden veya adres aralığından gelen iletileri engelleyin**: Bu, IP Engelleme Listesi'dir. **Aşağıdaki IP adreslerinden veya adres aralığından iletilere her zaman izin ver** ayarında daha önce açıklandığı gibi kutuya tek bir IP, IP aralığı veya CIDR IP girin.

   - **Güvenli listeyi aç**: İstenmeyen posta filtrelemeyi atlayacak bilinen, iyi gönderenleri tanımlamak için güvenli listenin kullanımını etkinleştirin veya devre dışı bırakın. Güvenli listeyi kullanmak için onay kutusunu seçin.

   Bitirdiğinizde, **Kaydet**'i tıklatın.

4. İlke ayrıntıları açılır menüsüne geri dönüp **Kapat'a** tıklayın.

## <a name="use-the-microsoft-365-defender-portal-to-view-the-default-connection-filter-policy"></a>Varsayılan bağlantı filtresi ilkesini görüntülemek için Microsoft 365 Defender portalını kullanma

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **İstenmeyen posta önleme** bölümüne gidin. **İstenmeyen posta önleme ilkeleri** sayfasına doğrudan gitmek için kullanın<https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme ilkeleri** sayfasında, ilke listesinde aşağıdaki özellikler görüntülenir:

   - **Ad**: Bu değer, varsayılan **bağlantı filtresi ilkesi için Bağlantı filtresi ilkesidir (Varsayılan** ).
   - **Durum**: Varsayılan bağlantı filtresi ilkesi için bu değer **Her zaman açıktır** .
   - **Öncelik**: Bu değer, varsayılan bağlantı filtresi ilkesi için **En Düşük** değerdir.
   - **Tür**: Bu değer, varsayılan bağlantı filtresi ilkesi için boş.

3. Varsayılan bağlantı filtresi ilkesini seçtiğinizde, ilke ayarları açılır öğede görüntülenir.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-modify-the-default-connection-filter-policy"></a>Varsayılan bağlantı filtresi ilkesini değiştirmek için Exchange Online PowerShell veya tek başına EOP PowerShell kullanma

Aşağıdaki sözdizimini kullanın:

```powershell
Set-HostedConnectionFilterPolicy -Identity Default [-AdminDisplayName <"Optional Comment">] [-EnableSafeList <$true | $false>] [-IPAllowList <IPAddressOrRange1,IPAddressOrRange2...>] [-IPBlockList <IPAddressOrRange1,IPAddressOrRange2...>]
```

**Notlar**:

- Geçerli IP adresi veya adres aralığı değerleri şunlardır:
  - Tek IP: Örneğin, 192.168.1.1.
  - IP aralığı: Örneğin, 192.168.0.1-192.168.0.254.
  - CIDR IP: Örneğin, 192.168.0.1/25. Geçerli ağ maskesi değerleri /24 ile /32 arasındadır.
- Belirttiğiniz değerlerle var olan girdilerin *üzerine yazmak* için aşağıdaki söz dizimini kullanın: `IPAddressOrRange1,IPAddressOrRange2,...,IPAddressOrRangeN`.
- Diğer mevcut girişleri etkilemeden IP adreslerini veya adres aralıklarını *eklemek veya kaldırmak* için aşağıdaki söz dizimini kullanın: `@{Add="IPAddressOrRange1","IPAddressOrRange2",...,"IPAddressOrRangeN";Remove="IPAddressOrRange3","IPAddressOrRange4",...,"IPAddressOrRangeN"}`.
- IP İzin Listesi veya IP Blok Listesi'ni boşaltmak için değerini `$null`kullanın.

Bu örnekte IP İzin Verme Listesi ve IP Blok Listesi belirtilen IP adresleri ve adres aralıklarıyla yapılandırılır.

```powershell
Set-HostedConnectionFilterPolicy -Identity Default -IPAllowList 192.168.1.10,192.168.1.23 -IPBlockList 10.10.10.0/25,172.17.17.0/24
```

Bu örnek, belirtilen IP adreslerini ve adres aralıklarını IP İzin Verme Listesi'ne ekler ve kaldırır.

```powershell
Set-HostedConnectionFilterPolicy -Identity Default -IPAllowList @{Add="192.168.2.10","192.169.3.0/24","192.168.4.1-192.168.4.5";Remove="192.168.1.10"}
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-HostedConnectionFilterPolicy](/powershell/module/exchange/set-hostedconnectionfilterpolicy).

## <a name="how-do-you-know-this-worked"></a>Bunun çalıştığını nasıl anlarsınız?

Varsayılan bağlantı filtresi ilkesini başarıyla değiştirdiğinizden emin olmak için aşağıdaki adımlardan birini yapın:

- konumundaki Microsoft 365 Defender portalındaki <https://security.microsoft.com/antispam>**İstenmeyen posta** önleme sayfasında, ilkenin adına tıklayarak listeden **Bağlantı filtresi ilkesi (Varsayılan)** seçeneğini belirleyin ve ayarları doğrulayın.

- Exchange Online PowerShell veya tek başına EOP PowerShell'de aşağıdaki komutu çalıştırın ve ayarları doğrulayın:

  ```powershell
  Get-HostedConnectionFilterPolicy -Identity Default
  ```

- IP İzin Ver Listesindeki bir girdiden test iletisi gönderin.

## <a name="additional-considerations-for-the-ip-allow-list"></a>IP İzin Verme Listesi için dikkat edilmesi gereken ek noktalar

Aşağıdaki bölümlerde, IP İzin Verilenler Listesi'ni yapılandırırken bilmeniz gereken ek öğeler tanımlanır.

### <a name="skip-spam-filtering-for-a-cidr-ip-outside-of-the-available-range"></a>Kullanılabilir aralığın dışında bir CIDR IP'sine yönelik istenmeyen posta filtrelemeyi atlama

Bu makalede daha önce açıklandığı gibi, IP İzin Verme Listesinde yalnızca /24 - /32 ağ maskesine sahip bir CIDR IP'si kullanabilirsiniz. /1 aralığındaki kaynak e-posta sunucularından /23 aralığına iletilerde istenmeyen posta filtrelemeyi atlamak için Exchange posta akışı kurallarını (aktarım kuralları olarak da bilinir) kullanmanız gerekir. Ancak, /1 - /23 CIDR IP aralığındaki bir IP adresi Microsoft'un özel veya üçüncü taraf blok listelerinden birinde göründüğünde iletiler engellendiğinden, mümkünse bunu yapmanızı öneririz.

Olası sorunları tam olarak fark ettiğinize göre, bu IP adreslerinden gelen iletilerin istenmeyen posta filtrelemeyi atladığından emin olmak için aşağıdaki ayarlarla (en azından) bir posta akışı kuralı oluşturabilirsiniz:

- Kural koşulu: **Gönderen** \> **IP adresi bu aralıklardan herhangi birindeyse** \> veya tam olarak eşleşiyorsa \> **bu kuralı uygulayın** (CIDR IP'nizi /1 ile /23 ağ maskesi arasında girin).
- Kural eylemi: **İleti özelliklerini** \> değiştirin **İstenmeyen posta güvenilirlik düzeyini (SCL)** \> **ayarlama İstenmeyen posta filtrelemesini atla**.

Kuralı denetleyebilir, kuralı test edebilir, belirli bir zaman aralığında kuralı etkinleştirebilir ve diğer seçimleri yapabilirsiniz. Kuralı zorlamadan önce bir süre boyunca test etmenizi öneririz. Daha fazla bilgi için bkz. [Exchange Online'de posta akışı kurallarını yönetme](/Exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules).

### <a name="skip-spam-filtering-on-selective-email-domains-from-the-same-source"></a>Aynı kaynaktan gelen seçmeli e-posta etki alanlarında istenmeyen posta filtrelemeyi atlama

Genellikle, IP İzin Ver Listesine bir IP adresi veya adres aralığı eklemek, bu e-posta kaynağından gelen tüm iletilere güvendiğiniz anlamına gelir. Peki ya bu kaynak birden çok etki alanından e-posta gönderirse ve bu etki alanlarından bazıları için istenmeyen posta filtrelemeyi atlamak istiyorsanız, diğerleri için değil? Bunu yapmak için yalnızca IP İzin Verme Listesi'ni kullanamazsınız, ancak IP İzin Verme Listesi'ni bir posta akışı kuralıyla birlikte kullanabilirsiniz.

Örneğin, kaynak e-posta sunucusu 192.168.1.25 etki alanlarından contoso.com, fabrikam.com ve tailspintoys.com e-posta gönderir, ancak yalnızca fabrikam.com gönderenlerden gelen iletiler için istenmeyen posta filtrelemesini atlamak istersiniz. Bunu yapmak için aşağıdaki adımları kullanın:

1. IP İzin Ver Listesine 192.168.1.25 ekleyin.

2. Posta akışı kuralını aşağıdaki ayarlarla yapılandırın (en azından):
   - Kural koşulu: **Gönderen** \> **IP adresi bu aralıklardan herhangi birindeyse** \> veya 192.168.1.25 ile tam olarak eşleşiyorsa \> (önceki adımda IP İzin Verme Listesine eklediğiniz IP adresi veya adres aralığı) **bu kuralı uygulayın**.
   - Kural eylemi: **İleti özelliklerini** \> değiştirin **İstenmeyen posta güvenilirlik düzeyini (SCL)** \> **0** ayarlayın.
   - Kural özel durumu: **Gönderen** \> **etki alanı** \> fabrikam.com (yalnızca istenmeyen posta filtrelemesini atlamak istediğiniz etki alanı veya etki alanları).

### <a name="scenarios-where-messages-from-sources-in-the-ip-allow-list-are-still-filtered"></a>IP İzin Ver Listesindeki kaynaklardan gelen iletilerin hala filtrelendiği senaryolar

IP İzin Ver Listenizdeki bir e-posta sunucusundan gelen iletiler hala aşağıdaki senaryolarda istenmeyen posta filtrelemesine tabidir:

- IP İzin Ver Listenizdeki bir IP adresi, Microsoft 365'daki *herhangi* bir kiracıdaki şirket içi, IP tabanlı bir gelen bağlayıcıda da yapılandırılır (bunu A Kiracısı olarak adlandıralım) ve A Kiracısı **ile** iletiyle ilk karşılaşan EOP sunucusu, Microsoft veri *merkezlerindeki aynı* Active Directory ormanında yer alır. Bu senaryoda **, IPV:CAL** iletinin [istenmeyen posta önleme ileti üst bilgilerine](anti-spam-message-headers.md) *eklenir (* iletinin istenmeyen posta filtrelemesini atlandığını gösterir), ancak ileti yine de istenmeyen posta filtrelemeye tabidir.

- IP İzin Verme Listesi'ni ve iletiyle ilk karşılaşan EOP sunucusunu içeren kiracınız, Microsoft veri *merkezlerindeki farklı* Active Directory ormanlarında yer alıyor. Bu senaryoda, ileti üst bilgilerine **IPV:CAL** *eklenmez* , bu nedenle ileti yine de istenmeyen posta filtrelemeye tabidir.

Bu senaryolardan biriyle karşılaşırsanız, sorunlu IP adreslerinden gelen iletilerin istenmeyen posta filtrelemesini atladığından emin olmak için aşağıdaki ayarlarla (en azından) bir posta akışı kuralı oluşturabilirsiniz:

- Kural koşulu: **Gönderen** \> **IP adresi bu aralıklardan herhangi birindeyse** \> veya tam olarak eşleşiyorsa \> (IP adresiniz veya adresleriniz) **bu kuralı uygulayın**.
- Kural eylemi: **İleti özelliklerini** \> değiştirin **İstenmeyen posta güvenilirlik düzeyini (SCL)** \> **ayarlama İstenmeyen posta filtrelemesini atla**.

## <a name="new-to-microsoft-365"></a>Microsoft 365'da yeni misiniz?

****

![LinkedIn Learning kısa simgesi.](../../media/eac8a413-9498-4220-8544-1e37d1aaea13.png) **Microsoft 365'da yeni misiniz?** LinkedIn Learning tarafından size getirilen **Microsoft 365 yöneticileri ve BT uzmanlarına** yönelik ücretsiz video kurslarını keşfedin.
