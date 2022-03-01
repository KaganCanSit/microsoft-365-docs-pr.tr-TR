---
title: Varsayılan bağlantı filtresi ilkesi yapılandırma
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
description: Yöneticiler, e-posta sunucularından e-postalara izin Exchange Online Protection engellemek için EOP'de bağlantı filtrelemeyi nasıl yapılandırabilirsiniz?
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2fbc481468fca8562c11e89b2e6c9dfa6361126a
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032523"
---
# <a name="configure-connection-filtering"></a>Bağlantı filtrelemeyi yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)


Exchange Online veya Microsoft 365 posta kutuları olmayan tek başına Exchange Online Protection (EOP) müşterisiysanız Exchange Online  posta kutuları için, ip adreslerine göre iyi veya kötü kaynak e-posta sunucularını tanımlamak için EOP'de bağlantı filtrelemeyi (özellikle, varsayılan bağlantı filtresi ilkesi) kullanırsınız. Varsayılan bağlantı filtresi ilkesi temel bileşenleri:

- **IP İzin Listesi**: IP adresi veya IP adresi aralığına göre belirttiğiniz kaynak e-posta sunucularından gelen tüm iletiler için istenmeyen posta filtrelemeyi atlayabilirsiniz. Bu kaynaklardan gelen iletilerde istenmeyen posta filtrelemenin yine oluştuğu senaryolar için, bu makalenin devam bölümündeki [IP](#scenarios-where-messages-from-sources-in-the-ip-allow-list-are-still-filtered) İzinLeri Listesi'ne gelen kaynaklardan gelen iletilerin yine filtrelenmiş olduğu senaryolar bölümüne bakın. İzin Verme IP'leri Listesinin genel güvenilir gönderenler stratejinize nasıl uyması gerektiği hakkında daha fazla bilgi için bkz. [EOP'de güvenilir gönderen listeleri oluşturma](create-safe-sender-lists-in-office-365.md).

- **IP Engelleme Listesi**: IP adresi veya IP adresi aralığıyla belirttiğiniz kaynak e-posta sunucularından gelen tüm iletileri engelin. Gelen iletiler reddedilir, istenmeyen posta olarak işaretlanmaz ve ek filtre oluşmaz. IP Engelleme Listesi'nin bir bütün olarak engellenen gönderenler stratejinize nasıl uyması gerektiği hakkında daha fazla bilgi için bkz. [EOP'de engellenen gönderen listeleri oluşturma](create-block-sender-lists-in-office-365.md).

- **Kasa:** Güvenli *liste*, Microsoft veri merkezinde müşteri yapılandırması gerektiren dinamik izinler listesidir. Microsoft, aboneliklerden çeşitli üçüncü taraf listelerine bu güvenilir e-posta kaynaklarını tanımlar. Güvenli listenin kullanımını etkinleştiriyor veya devre dışı bırakabilirsiniz; güvenilir listede kaynak e-posta sunucularını yapılandıramazsanız. İstenmeyen posta filtreleme, güvenilir listede e-posta sunucularından gelen iletilerden atlanır.

Bu makalede, Microsoft 365 Microsoft 365 Defender portalında veya PowerShell'de (Exchange Online posta kutuları olan Microsoft 365 kuruluşlar için PowerShell) varsayılan bağlantı filtresi Exchange Online ; posta kutusu olmayan kuruluşlar için tek Exchange Online EOP PowerShell). EOP'nin bağlantı filtrelemeyi nasıl kullandığı hakkında daha fazla bilgi için bkz. Genelde istenmeyen posta önleme ayarlarının [bir parçası](anti-spam-protection.md). İstenmeyen posta önleme koruması.

> [!NOTE]
> IP İzin Listesi, güvenilir liste ve IP Engelleme Listesi, genel stratejinizin, kurumda e-postaya izin verme veya engelleme stratejinizin bir bölümüdür. Daha fazla bilgi için bkz [. Güvenli gönderen listeleri oluşturma](create-safe-sender-lists-in-office-365.md) [ve Engellenen gönderen listeleri oluşturma](create-block-sender-lists-in-office-365.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açın<https://security.microsoft.com>. Doğrudan İstenmeyen posta **önleme ilkeleri sayfasına gitmek** için, kullanın <https://security.microsoft.com/antispam>.

- Exchange Online PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online e bağlama](/powershell/exchange/connect-to-exchange-online-powershell). Tek başına EOP PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online Protection e bağlama](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Bu makaledeki yordamları **yerine Exchange Online** önce Bu makalede izinlerin atanmamış olması gerekir:
  - Varsayılan bağlantı filtresi ilkesinde değişiklik yapmak için, Kuruluş Yönetimi veya Güvenlik **Yöneticisi rol gruplarının** **üyesi olun** .
  - Varsayılan bağlantı filtresi ilkesine salt okunur erişim için, Genel Okuyucu veya Güvenlik Okuyucusu **rol** **gruplarının üyesi** olun.

  Daha fazla bilgi için bkz. [Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Notlar**:

  - Görev sırasında ilgili kullanıcı Azure Active Directory eklemek Microsoft 365 yönetim merkezi kullanıcılara çalışma sayfalarındaki diğer özellikler için gerekli izinleri ve izinleri Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  - **Görünüm'de Yalnızca Görüntüleme** [kuruluş Exchange Online rol](/Exchange/permissions-exo/permissions-exo#role-groups) grubu, özel salt okunur erişim de sağlar.

- İzin vermek veya engellemek istediğiniz e-posta sunucularının (gönderenler) kaynak IP adreslerini bulmak için, ileti üst bilgisinde BAĞLANTı IP (**ZAMAN**) üst bilgi alanını kontrol edin. Çeşitli e-posta istemcilerinde ileti üst bilgilerini görüntülemek için bkz[. Çeşitli e-posta istemcilerinde İnternet ileti Outlook](https://support.microsoft.com/office/cd039382-dc6e-4264-ac74-c048563d212c).

- ip İzinLeri Listesi, IP Engelleme Listesi'ne göre önceliklidir (her iki listede de yer alan bir adres engellenmiş değildir).

- IP İzin Verilenler Listesi ve IP Engelleme Listesi'nin her biri en çok 1273 girdiyi destekler. Burada girdi tek bir IP adresi, IP adresi aralığı veya Sınıfsız Etki Alanı Yönlendirmesi (CIDR) IP'dir.

## <a name="use-the-microsoft-365-defender-portal-to-modify-the-default-connection-filter-policy"></a>Varsayılan Microsoft 365 Defender filtresi ilkesini değiştirmek için Kullanıcı Portalı'nın kullanımı

1. aşağıdaki Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler **bölümünde E-posta &** \> İşbirliği **İlkeleri'&** \>  \> Kurallar Tehdit ilkeleri **İstenmeyen** postayla **mücadele'ye** gidin. Doğrudan İstenmeyen posta **önleme ilkeleri sayfasına gitmek** için, kullanın <https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme ilkeleri** sayfasında, listeden **ilkenin** adına tıklayarak Bağlantı filtresi ilkesi (Varsayılan) öğesini seçin.

3. Görüntülenen ilke ayrıntıları açılır sayfasında, aşağıdaki ayarlardan herhangi birini yapılandırabilirsiniz:

   - **Açıklama** bölümü: Adı ve **açıklamayı düzenle'ye tıklayın**. Görüntülenen **Adı ve açıklamayı** düzenle açılır kutusuna Açıklama kutusuna isteğe bağlı açıklayıcı **metin** girin.

     Bitirdiğinizde, **Kaydet**'i tıklatın.

   - **Bağlantı filtreleme bölümü: Bağlantı** filtresi **İlkesini düzenle'ye tıklayın**. Görüntülenen açılır listede aşağıdaki ayarları yapılandırabilirsiniz:

     - **Her zaman aşağıdaki IP adreslerinden veya adres aralığından gelen iletilere izin ver**: Bu, IP İzinLeri listesidir. Kutuya tıklayın, bir değer girin ve Enter tuşuna basın veya kutunun altında gösterilen tam değeri seçin. Geçerli değerler:
       - Tek IP: Örneğin, 192.168.1.1.
       - IP aralığı: Örneğin, 192.168.0.1-192.168.0.254.
       - CIDR IP'si: Örneğin, 192.168.0.1/25. Geçerli alt ağ maskesi değerleri /24 ile /32 arasındadır. /1 olan /23 için istenmeyen posta filtrelemesini /23'e atlamak için, bu makalenin devam bölümündeki [CIDR IP'leri](#skip-spam-filtering-for-a-cidr-ip-outside-of-the-available-range) için istenmeyen posta filtresini kullanılabilir aralığın dışında atlama bölümüne bakın.

       Bu adımı gereken sayıda yinelayın. Var olan bir değeri kaldırmak için kaldır'a tıklayın. ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) seçin.

     IP adresi veya adres aralığını eklemek için, kutuya tıklayın ve Simge **Ekle'ye tıklayın**![.](../../media/ITPro-EAC-AddIcon.png) Bir girdiyi kaldırmak için İzin Verilen **IP Adresi'nin girdisini seçin ve** **Kaldır'a** ![tıklayın](../../media/scc-remove-icon.png). Bitirdiğinizde, **Kaydet**'i tıklatın.

   - **Her zaman şu IP adreslerinden veya adres aralığından gelen iletileri engelin**: Bu, IP Engelleme Listesi'dir. Daha önce Aşağıdaki IP adreslerinden veya adres aralığından gelen iletilere her zaman izin ver ayarında açıklandığı gibi tek bir IP, IP aralığı veya CIDR **IP'sini** girin.

   - **Güvenli listeyi açma**: İstenmeyen posta filtrelemesini atlayıp bilinen, iyi gönderenleri belirlemek için güvenli listenin kullanımını etkinleştirin veya devre dışı bırak. Güvenli listeyi kullanmak için onay kutusunu seçin.

   Bitirdiğinizde, **Kaydet**'i tıklatın.

4. İlke ayrıntıları ayrıntılarına dönüp Kapat'a **tıklayın**.

## <a name="use-the-microsoft-365-defender-portal-to-view-the-default-connection-filter-policy"></a>Varsayılan Microsoft 365 Defender filtresi Microsoft 365 Defender için varsayılan portalını kullanma

1. aşağıdaki Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler **bölümünde E-posta &** \> İşbirliği **İlkeleri'&** \>  \> Kurallar Tehdit ilkeleri **İstenmeyen** postayla **mücadele'ye** gidin. Doğrudan İstenmeyen posta **önleme ilkeleri sayfasına gitmek** için, kullanın <https://security.microsoft.com/antispam>.

2. **İstenmeyen posta önleme** ilkeleri sayfasında, ilkeler listesinde aşağıdaki özellikler görüntülenir:

   - **Ad**: Bu değer, **varsayılan bağlantı filtresi ilkesi için Bağlantı** filtresi ilkesidir (Varsayılan).
   - **Durum**: Varsayılan bağlantı filtresi **ilkesi için** bu değer Her Zaman açık durumdadır.
   - **Öncelik**: Varsayılan bağlantı filtresi **ilkesi için** bu değer En Düşük değeridir.
   - **Tür**: Varsayılan bağlantı filtresi ilkesi için bu değer boştur.

3. Varsayılan bağlantı filtresi ilkesi'ne tıklayınca, ilke ayarları bir çıkışta görüntülenir.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-modify-the-default-connection-filter-policy"></a>Varsayılan Exchange Online filtresi ilkesi değiştirmek için PowerShell veya tek başına EOP PowerShell kullanma

Aşağıdaki sözdizimini kullanın:

```powershell
Set-HostedConnectionFilterPolicy -Identity Default [-AdminDisplayName <"Optional Comment">] [-EnableSafeList <$true | $false>] [-IPAllowList <IPAddressOrRange1,IPAddressOrRange2...>] [-IPBlockList <IPAddressOrRange1,IPAddressOrRange2...>]
```

**Notlar**:

- Geçerli IP adresi veya adres aralığı değerleri:
  - Tek IP: Örneğin, 192.168.1.1.
  - IP aralığı: Örneğin, 192.168.0.1-192.168.0.254.
  - CIDR IP'si: Örneğin, 192.168.0.1/25. Geçerli ağ maskesi değerleri /24 ile /32 arasındadır.
- Belirttiğiniz *değerlerle* var olan tüm girdilerin üzerine yazmak için aşağıdaki söz dizimi kullanın: `IPAddressOrRange1,IPAddressOrRange2,...,IPAddressOrRangeN`.
- Varolan *diğer girdileri* etkilemeden IP adresleri veya adres aralıkları eklemek veya kaldırmak için, aşağıdaki söz dizimi kullanın: `@{Add="IPAddressOrRange1","IPAddressOrRange2",...,"IPAddressOrRangeN";Remove="IPAddressOrRange3","IPAddressOrRange4",...,"IPAddressOrRangeN"}`.
- IP İzin Listesine veya IP Engelleme Listesi'ne ne kadar boş değer yoksa, değerini kullanın `$null`.

Bu örnekte IP İzin Listesi ve IP Engelleme Listesi, belirtilen IP adresleri ve adres aralıkları ile yapılandırılır.

```powershell
Set-HostedConnectionFilterPolicy -Identity Default -IPAllowList 192.168.1.10,192.168.1.23 -IPBlockList 10.10.10.0/25,172.17.17.0/24
```

Bu örnekte, IP İzin Listesi'ne belirtilen IP adresleri ve adres aralıkları eklenir ve bunlar kaldırır.

```powershell
Set-HostedConnectionFilterPolicy -Identity Default -IPAllowList @{Add="192.168.2.10","192.169.3.0/24","192.168.4.1-192.168.4.5";Remove="192.168.1.10"}
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-HostedConnectionFilterPolicy](/powershell/module/exchange/set-hostedconnectionfilterpolicy).

## <a name="how-do-you-know-this-worked"></a>Bunun çalıştığını nasıl anlarsınız?

Varsayılan bağlantı filtresi ilkesi başarıyla değiştirildiğinden emin olmak için, aşağıdaki adımlardan herhangi birini yapın:

- Microsoft 365 Defender portalında  <https://security.microsoft.com/antispam>İstenmeyen posta önleme sayfasında, ilkenin adına tıklayarak listeden Bağlantı filtresi ilkesi **(Varsayılan)** öğesini seçin ve ayarları doğrulayın.

- PowerShell Exchange Online tek başına EOP PowerShell'de, aşağıdaki komutu çalıştırın ve ayarları doğrulayın:

  ```powershell
  Get-HostedConnectionFilterPolicy -Identity Default
  ```

- IP İzin Ver Listesi'ne gelen bir girdiden test iletisi gönderin.

## <a name="additional-considerations-for-the-ip-allow-list"></a>IP İzin Listesi ile ilgili dikkat edilmesi gereken diğer noktalar

Aşağıdaki bölümlerde, IP İzin Listesi'ne yapılandırıldığında hakkında bilgili olmak istediğiniz ek öğeler tanımlanmaktadır.

### <a name="skip-spam-filtering-for-a-cidr-ip-outside-of-the-available-range"></a>CIDR IP'leri için istenmeyen posta filtrelemesini kullanılabilir aralığın dışında atlama

Bu makalede daha önce açıklandığı gibi, ip İzin Listesi'nin altında yalnızca /24 - /32 ağ maskeli bir CIDR IP'yi kullanabilirsiniz. /1 ile /23 aralığındaki kaynak e-posta sunucularından gelen iletilerde istenmeyen posta filtrelemeyi atlamak için, bir posta Exchange kuralları (aktarım kuralları olarak da bilinir) kullanmalıdır. Ancak, mümkün olduğunca bunu yapmamanizi öneririz, çünkü /1 - /23 CIDR IP aralığındaki bir IP adresi Microsoft'un özel veya üçüncü taraf engelleme listelerinde görünürse iletiler engellenir.

Artık olası sorunların tam olarak farkında olduğunuza göre, bu IP adreslerinden gelen iletilerin istenmeyen posta filtresini atlamayacaklarından emin olmak için, aşağıdaki ayarlara (en azından) sahip bir posta akışı kuralı oluşturabilirsiniz:

- Kural koşulu: **Gönderen** \>  \> **IP** \> adresi bu aralıklardan herhangi birinde veya tam eşleşmesinde ise bu kuralı uygula (CIDR IP'nizi /1 - /23 ağ maskesiyle girin).
- Kural eylemi: **İleti özelliklerini değiştirme İstenmeyen** \> **posta güvenlik düzeyini ayarlama (SCL) İstenmeyen** \> **posta filtresini atla**.

Kuralı denetleme, denetleme, belirli bir zaman süresinde kuralı etkinleştirme ve diğer seçimler. Kuralı zorunlu olmadan önce belirli bir süre için test etmenizi öneririz. Daha fazla bilgi için bkz[. Kendi adres mektuplarında posta Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules).

### <a name="skip-spam-filtering-on-selective-email-domains-from-the-same-source"></a>Aynı kaynaktan seçmeli e-posta etki alanlarında istenmeyen posta filtrelemeyi atla

Normalde, IP adresi veya adres aralığını IP İzin Listesi'ne eklemek, o e-posta kaynağından gelen tüm iletilere güvenmeniz anlamına gelir. Peki bu kaynak birden çok etki alanından e-posta gönderirse ve bu etki alanlarından bazıları için istenmeyen posta filtrelemeyi atlayıp diğerlerini atlamak istemiyorsanız ne olacak? Bunu yapmak için IP İzin Listesi'ne tek başına sahip olmazsınız, ancak IP İzinLeri Listesini bir posta akışı kuralıyla birlikte kullanabilirsiniz.

Örneğin, 192.168.1.25 kaynak e-posta sunucusu contoso.com, fabrikam.com ve tailspintoys.com etki alanlarından e-posta gönderir, ancak yalnızca fabrikam.com'te gönderenlerden gelen iletiler için istenmeyen posta filtrelemeyi atlamak fabrikam.com. Bunu yapmak için aşağıdaki adımları kullanın:

1. IP İzin Listesi'ne 192.168.1.25 ekleyin.

2. Posta akış kuralını aşağıdaki ayarlarla yapılandırma (en azından):
   - Kural **koşulu:** \>  \> Gönderen **IP** \> adresi bu aralıklardan herhangi birsinde veya 192.168.1.25 ile (önceki adımda IP İzin Listesine ekleytilen IP adresi veya adres aralığı) tam olarak eşleniyorsa, bu kuralı uygula.
   - Kural eylemi: **İleti özelliklerini değiştirme İstenmeyen** \> **posta güven düzeyi (SCL)** \> **0'ı ayarlayın**.
   - Kural özel durumu: **Gönderen** \> **etki** \> alanı fabrikam.com etki alanıdır (yalnızca istenmeyen posta filtrelemesini atlamak istediğiniz etki alanı veya etki alanları).

### <a name="scenarios-where-messages-from-sources-in-the-ip-allow-list-are-still-filtered"></a>IP İzin Listesi'ne gelen kaynaklardan gelen iletilerin filtrelenmiş durumda olduğu senaryolar

IP İzin Listeniz'de yer alan bir e-posta sunucusundan gelen iletiler, aşağıdaki senaryolarda hala istenmeyen posta filtresine tabi olabilir:

- IP İzin Listeniz'in IP adresi aynı zamanda Microsoft 365'daki herhangi bir kiracıda bulunan şirket içi, IP tabanlı gelen bağlayıcısı  (bu Kiracı A'ya **diyelim) ve** iletiyle ilk kez karşılaşan EOP sunucusu da yapılandırıldığında, her ikisi de Microsoft veri merkezlerindeki *aynı Active* Directory ormanı içinde yer alır. Bu senaryoda **IPV:CAL**, iletinin istenmeyen posta önleme ileti üst bilgilerine [eklenir (](anti-spam-message-headers.md)iletinin istenmeyen posta filtrelemeyi atla olduğunu gösterir), ancak ileti yine de istenmeyen posta filtrelemeye tabi olur.

- IP İzin Listesi'nin ve iletiyle ilk kez karşılaşan EOP sunucusunu içeren kiracınız, Microsoft veri merkezlerinde yer alan *farklı Active Directory* ormanlarında olabilir. Bu senaryoda, **IPV:CAL** *ileti* üst bilgilerine eklenmez, dolayısıyla ileti yine istenmeyen posta filtrelemeye tabi olur.

Bu senaryolardan herhangi biri ile karşılaşırsanız, sorunlu IP adreslerinden gelen iletilerin istenmeyen posta filtresini atlamayacaklarından emin olmak için, aşağıdaki ayarlarla (en azından) bir posta akışı kuralı oluşturabilirsiniz:

- Kural koşulu: Gönderen **IP** \> **adresi bu** \> **aralıklardan** \> herhangi birsinde veya tam eşleşmesinde ise (IP adresiniz veya adresleriniz) bu kuralı uygula.
- Kural eylemi: **İleti özelliklerini değiştirme İstenmeyen** \> **posta güvenlik düzeyini ayarlama (SCL) İstenmeyen** \> **posta filtresini atla**.

## <a name="new-to-microsoft-365"></a>Yeni misiniz? Microsoft 365?

****

![LinkedIn Learning kısa simgesi.](../../media/eac8a413-9498-4220-8544-1e37d1aaea13.png) **Yeni misiniz? Microsoft 365?** LinkedIn tarafından size Microsoft 365 yönetici ve **IT** profesyonelleri için ücretsiz görüntülü kursları Learning.
