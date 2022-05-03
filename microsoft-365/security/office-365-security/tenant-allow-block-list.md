---
title: Kiracı İzin Ver/Engelle Listesinde izinlerinizi ve bloklarınızı yönetin
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
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Yöneticiler, Güvenlik portalındaki Kiracı İzin Ver/Engelle Listesi'nde izin ve blokları yönetmeyi öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 64b9c044a463e940b0d9862221ca854fe0eebfdc
ms.sourcegitcommit: 4d6a8e9d69a421d6c293b2485a8aa5e806b71616
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65182660"
---
# <a name="manage-the-tenant-allowblock-list"></a>Kiracı İzin Verilenler/Engellenenler Listesini Yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online posta kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarında posta kutuları olan Microsoft 365 kuruluşlarda, EOP filtreleme kararına katılamayabilirsiniz. Örneğin, iyi bir ileti kötü (hatalı pozitif) olarak işaretlenebilir veya hatalı bir iletiye (hatalı negatif) izin verilir.

Microsoft 365 Defender portalındaki Kiracı İzin Ver/Engelle Listesi, Microsoft 365 filtreleme kararlarını el ile geçersiz kılmanın bir yolunu sunar. Kiracı İzin Ver/Engelle Listesi, gelen iletiler için posta akışı sırasında (kuruluş içi iletiler için geçerli değildir) ve kullanıcı tıklamaları sırasında kullanılır. Aşağıdaki geçersiz kılma türlerini belirtebilirsiniz:

- Engelleyecek URL'ler.
- Engellenmesi gereken dosyalar.
- Engellenmesi gereken gönderen e-postaları veya etki alanları.
- İzin vermek veya engellemek için sahte gönderenler. Sahte [zeka içgörülerinde](learn-about-spoof-intelligence.md) izin verme veya engelleme kararını geçersiz kılarsanız, sahtekar gönderen yalnızca Kiracı İzin Ver/Engelle Listesi'ndeki **Kimlik Sahtekarı** sekmesinde görünen el ile izin verme veya engelleme girdisine dönüşür. Sahte gönderenler için kimlik sahtekarlık zekası tarafından algılanana kadar el ile izin verme veya engelleme girdileri de oluşturabilirsiniz.
- İzin verecek URL'ler.
- İzin verecek dosyalar.
- İzin vermek için gönderen e-postaları veya etki alanları.

Bu makalede, Microsoft 365 Defender portalında veya PowerShell'de (Exchange Online posta kutuları olan Microsoft 365 kuruluşlar için PowerShell Exchange Online olmayan kuruluşlar için tek başına EOP PowerShell'de Kiracı İzin Ver/Engelle Listesi'nde girdilerin nasıl yapılandırıldığı açıklanır Exchange Online posta kutuları).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını adresinde <https://security.microsoft.com>açarsınız. **Doğrudan Kiracı İzin Ver/Listeleri Engelle** sayfasına gitmek için kullanın<https://security.microsoft.com/tenantAllowBlockList>.

- Dosyanın SHA256 karma değerini kullanarak dosyaları belirtirsiniz. Windows'da bir dosyanın SHA256 karma değerini bulmak için komut isteminde aşağıdaki komutu çalıştırın:

  ```console
  certutil.exe -hashfile "<Path>\<Filename>" SHA256
  ```

  Örnek değer: `768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3a`. Algısal karma (pHash) değerleri desteklenmez.

- Kullanılabilir URL değerleri, bu makalenin devamında yer alan [Kiracı İzin Ver/Engelle Listesi bölümünün URL söz diziminde](#url-syntax-for-the-tenant-allowblock-list) açıklanmaktadır.

- Kiracı İzin Ver/Engelle Listesi gönderenler için en fazla 500 girdi, URL'ler için 500 girdi, dosya karmaları için 500 girdi ve kimlik sahtekarlığına yönelik 1024 girdiye (sahtekar gönderenler) izin verir.

- Her girdi için en fazla karakter sayısı:
  - Dosya karmaları = 64
  - URL = 250

- Bir girdi 30 dakika içinde etkin olmalıdır.

- Varsayılan olarak, Kiracı İzin Ver/Engelle Listesindeki girdilerin süresi 30 gün sonra dolar. Bir tarih belirtebilir veya bunların süresi hiç dolmak üzere ayarlayabilirsiniz.

- Exchange Online PowerShell'e bağlanmak için bkz. [PowerShell'Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell). Tek başına EOP PowerShell'e bağlanmak için bkz. [PowerShell'i Exchange Online Protection için Bağlan](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Bu makaledeki yordamları gerçekleştirmeden önce Exchange Online'de izinlerin atanmış olması gerekir:
  - **Gönderenler, URL'ler ve dosyalar**:
    - Kiracı İzin Ver/Engelle Listesinden değer eklemek ve kaldırmak için
      - **Kuruluş Yönetimi** veya **Güvenlik Yöneticisi** rol grubu (**Güvenlik yöneticisi rolü**)
      - **Güvenlik İşleci** rol grubu (**Kiracı AllowBlockList Manager**).
    - Kiracı İzin Ver/Engelle Listesi'ne salt okunur erişim için
      - **Genel Okuyucu**  rol grubu
      - **Güvenlik Okuyucusu** rol grubu
  - **Kimlik sahtekarlığına:** Aşağıdaki birleşimlerden biri:
    - **Kuruluş Yönetimi**
    - **Güvenlik Yöneticisi** <u>ve</u> **Yalnızca Görüntüleme Yapılandırması** veya **Yalnızca Görüntüleme Kuruluş Yönetimi**.

  Daha fazla bilgi için bkz. [Exchange Online'de İzinler](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - kullanıcıları Microsoft 365 yönetim merkezi karşılık gelen Azure Active Directory rolüne eklemek, kullanıcılara Microsoft 365'deki diğer özellikler için gerekli izinleri *ve* izinleri verir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  > - [Exchange Online'daki](/Exchange/permissions-exo/permissions-exo#role-groups) **Yalnızca Görüntüleme Kuruluş Yönetimi** rol grubu da özelliğe salt okunur erişim sağlar.

## <a name="configure-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelle Listesini Yapılandırma

### <a name="use-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalını kullanma

konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **Kurallar** bölümünde **İlkeler & kurallar** \> **Tehdit İlkeleri** \> **Kiracı İzin Ver/Engelle Listeleri'ne** gidin. **Doğrudan Kiracı İzin Ver/Listeleri Engelle** sayfasına gitmek için kullanın<https://security.microsoft.com/tenantAllowBlockList>.

Tüm blokları eklemek için bkz. [Kiracı İzin Ver/Engelle Listesinde blok ekleme](manage-tenant-blocks.md).

Tüm izinler eklemek için bkz. [Kiracı İzin Ver/Engelle Listesi'nde Ekleme izin verir](manage-tenant-allows.md).

Tüm blokları değiştirmek ve kaldırmak ve izin vermek için bkz. [Kiracı İzin Ver/Engelle Listesindeki girdileri değiştirme ve kaldırma](modify-remove-entries-tenant-allow-block.md).

### <a name="use-exchange-online-powershell-or-standalone-eop-powershell"></a>Exchange Online PowerShell veya tek başına EOP PowerShell kullanma

Tüm izin verme ve blokları yönetmek için bkz. [Kiracı İzin Ver/Engelle Listesinde blok ekleme](manage-tenant-blocks.md), [Kiracı İzin Ver/Engelle Listesinde İzin Ver/Engelle Listesinde Ekle ve Kiracı İzin Ver/Engelle Listesindeki](manage-tenant-allows.md) [girdileri değiştirme ve kaldırma](modify-remove-entries-tenant-allow-block.md).

## <a name="view-entries-in-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelle Listesindeki girdileri görüntüleme

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **Kurallar** bölümünde **İlkeler & kurallar** \> **Tehdit İlkeleri** \> **Kiracı İzin Ver/Engelle Listeleri'ne** gidin. İsterseniz, doğrudan **Kiracı İzin Ver/Listeleri Engelle** sayfasına gitmek için kullanın <https://security.microsoft.com/tenantAllowBlockList>.

2. İstediğiniz sekmeyi seçin. Kullanılabilir sütunlar seçtiğiniz sekmeye bağlıdır:

   - **Gönderenler**:
     - **Değer**: Gönderen etki alanı veya e-posta adresi.
     - **Eylem**: **İzin Ver** veya **Engelle** değeri.
     - **Değiştiren**
     - **Son güncelleştirme**
     - **Kaldırılacak yer**
     - **Notlar**
   - **Sızdırma**
     - **Sahte kullanıcı**
     - **Altyapı gönderme**
     - **Kimlik sahtekarı türü**: **İç** veya **Dış** değeri.
     - **Eylem**: **Engelle** veya **İzin Ver** değeri.
   - **URL'ler**:
     - **Değer**: URL.
     - **Eylem**: **İzin Ver** veya **Engelle** değeri.
     - **Değiştiren**
     - **Son güncelleştirme**
     - **Kaldırılacak yer**
     - **Notlar**
   - **Dosyaları**
     - **Değer**: Dosya karması.
     - **Eylem**: **İzin Ver** veya **Engelle** değeri.
     - **Değiştiren**
     - **Son güncelleştirme**
     - **Kaldırılacak yer**
     - **Notlar**

   Artan veya azalan düzende sıralamak için sütun başlığına tıklayabilirsiniz.

   Sonuçları gruplandırmak için **Gruplandır'a** tıklayabilirsiniz. Kullanılabilir değerler seçtiğiniz sekmeye bağlıdır:

   - **Gönderenler**: Sonuçları **Eyleme** göre gruplandırabilirsiniz.
   - **Kimlik sahtekarlığına:** Sonuçları **Eylem** veya **Kimlik Sahtekarı türüne** göre gruplandırabilirsiniz.
   - **URL'ler**: Sonuçları **Eyleme** göre gruplandırabilirsiniz.
   - **Dosyalar**: Sonuçları **Eyleme** göre gruplandırabilirsiniz.

   **Ara'ya** tıklayın, bir değerin tamamını veya bir bölümünü girin ve belirli bir değeri bulmak için ENTER tuşuna basın. İşiniz bittiğinde Aramayı temizle simgesine tıklayın ![.](../../media/m365-cc-sc-close-icon.png) **Aramayı temizle'yi seçin**.

   Sonuçları filtrelemek için **Filtre'ye** tıklayın. **Görüntülenen Filtre** açılır öğesinde bulunan değerler, seçtiğiniz sekmeye bağlıdır:

   - **Gönderenler**
     - **Eylem**
     - **Hiçbir zaman süresi dolmaz**
     - **Son güncelleştirme tarihi**
     - **Kaldırılacak yer**
   - **Sızdırma**
     - **Eylem**
     - **Kimlik sahtekarı türü**
   - **Url 'leri**
     - **Eylem**
     - **Hiçbir zaman süresi dolmaz**
     - **Son güncelleştirme tarihi**
     - **Kaldırılacak yer**
   - **Dosyaları**
     - **Eylem**
     - **Hiçbir zaman süresi dolmaz**
     - **Son güncelleştirme**
     - **Kaldırılacak yer**

   İşiniz bittiğinde **Uygula'ya** tıklayın. Mevcut filtreleri temizlemek için **Filtre'ye** tıklayın ve görüntülenen **Filtre** açılır öğesinde **Filtreleri temizle'ye** tıklayın.

3. İşiniz bittiğinde **Ekle'ye** tıklayın.

## <a name="view-sender-file-or-url-entries-in-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelle Listesinde gönderen, dosya veya URL girdilerini görüntüleme

Kiracı İzin Ver/Engelle Listesi'nde blok gönderen, dosya veya URL girdilerini görüntülemek için aşağıdaki söz dizimini kullanın:

```powershell
Get-TenantAllowBlockListItems -ListType <Sender | FileHash | URL> [-Entry <SenderValue | FileHashValue | URLValue>] [<-ExpirationDate Date | -NoExpiration>]
```

Bu örnek, belirtilen dosya karması değeri için bilgi döndürür.

```powershell
Get-TenantAllowBlockListItems -ListType FileHash -Entry "9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08"
```

Bu örnek tüm engellenen URL'leri döndürür.

```powershell
Get-TenantAllowBlockListItems -ListType Url -Block
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

## <a name="view-spoofed-sender-entries"></a>Sahte gönderen girdilerini görüntüleme

Kiracı İzin Ver/Engelle Listesi'nde sahte gönderen girdilerini görüntülemek için aşağıdaki söz dizimini kullanın:

```powershell
Get-TenantAllowBlockListSpoofItems [-Action <Allow | Block>] [-SpoofType <External | Internal>
```

Bu örnek, Kiracı İzin Ver/Engelle Listesindeki tüm sahte gönderen girdilerini döndürür.

```powershell
Get-TenantAllowBlockListSpoofItems
```

Bu örnek, iç olan tüm sahte gönderen girişlerini döndürür.

```powershell
Get-TenantAllowBlockListSpoofItems -Action Allow -SpoofType Internal
```

Bu örnek, dış olan tüm engellenen sahte gönderen girdilerini döndürür.

```powershell
Get-TenantAllowBlockListSpoofItems -Action Block -SpoofType External
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-TenantAllowBlockListSpoofItems](/powershell/module/exchange/get-tenantallowblocklistspoofitems).

## <a name="url-syntax-for-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelle Listesi için URL söz dizimi

- IPv4 ve IPv6 adreslerine izin verilir, ancak TCP/UDP bağlantı noktalarına izin verilmez.

- Dosya adı uzantılarına izin verilmez (örneğin, test.pdf).

- Unicode desteklenmez, ancak Punycode desteklenir.

- Aşağıdaki deyimlerin tümü doğruysa konak adlarına izin verilir:
  - Konak adı bir nokta içerir.
  - Noktanın solunda en az bir karakter vardır.
  - Noktanın sağında en az iki karakter vardır.

  Örneğin, `t.co` izin verilir veya `.com` `contoso.` izin verilmez.

- Alt yollar izinler için ima edilmemektedir.

  Örneğin, `contoso.com` içermez `contoso.com/a`.

- Aşağıdaki senaryolarda joker karakterlere (*) izin verilir:

  - Alt etki alanı belirtmek için sol joker karakterden sonra nokta gelmelidir.

    Örneğin, `*.contoso.com` izin verilir; `*contoso.com` izin verilmez.

  - Bir yol belirtmek için sağ joker karakter eğik çizgi (/) izlemelidir.

    Örneğin, `contoso.com/*` izin verilir veya `contoso.com*` `contoso.com/ab*` izin verilmez.

  - `*.com*` geçersiz (çözümlenebilir bir etki alanı değil ve sağ joker karakter eğik çizgi izlemez).

  - IP adreslerinde joker karakterlere izin verilmez.

- Tilde (~) karakteri aşağıdaki senaryolarda kullanılabilir:

  - Sol tilde bir etki alanı ve tüm alt etki alanları anlamına gelir.

    Örneğin `~contoso.com` ve `*.contoso.com`içerir`contoso.com`.

- URL girişleri tüm protokoller için geçerli olduğundan, protokoller içeren URL girişleri (örneğin, `http://`, `https://`veya `ftp://`) başarısız olur.

- Kullanıcı adı veya parola desteklenmez veya gerekli değildir.

- Tırnak işaretleri (' veya ") geçersiz karakterlerdir.

- Url mümkün olduğunda tüm yeniden yönlendirmeleri içermelidir.

### <a name="url-entry-scenarios"></a>URL giriş senaryoları

Geçerli URL girişleri ve sonuçları aşağıdaki bölümlerde açıklanmıştır.

#### <a name="scenario-no-wildcards"></a>Senaryo: Joker karakter yok

**Giriş**: `contoso.com`

- **Eşleşmeye izin ver**: contoso.com

- **Eşleşmemiş izin ver**:

  - abc-contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

- **Blok eşleşmesi**:

  - contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

- **Blok eşleşmiyor**: abc-contoso.com

#### <a name="scenario-left-wildcard-subdomain"></a>Senaryo: Sol joker karakter (alt etki alanı)

**Giriş**: `*.contoso.com`

- **Eşleşmeye izin ver** ve **Eşleşmeyi engelle**:

  - www.contoso.com
  - xyz.abc.contoso.com

- **Eşleşmedi** ve **Engelle eşleşmedi**:

  - 123contoso.com
  - contoso.com
  - test.com/contoso.com
  - www.contoso.com/abc

#### <a name="scenario-right-wildcard-at-top-of-path"></a>Senaryo: Yolun en üstünde sağ joker karakter

**Giriş**: `contoso.com/a/*`

- **Eşleşmeye izin ver** ve **Eşleşmeyi engelle**:

  - contoso.com/a/b
  - contoso.com/a/b/c
  - contoso.com/a/?q=joe@t.com

- **Eşleşmedi** ve **Engelle eşleşmedi**:

  - contoso.com
  - contoso.com/a
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

#### <a name="scenario-left-tilde"></a>Senaryo: Sol tilde

**Giriş**: `~contoso.com`

- **Eşleşmeye izin ver** ve **Eşleşmeyi engelle**:

  - contoso.com
  - www.contoso.com
  - xyz.abc.contoso.com

- **Eşleşmedi** ve **Engelle eşleşmedi**:

  - 123contoso.com
  - contoso.com/abc
  - www.contoso.com/abc

#### <a name="scenario-right-wildcard-suffix"></a>Senaryo: Sağ joker karakter soneki

**Giriş**: `contoso.com/*`

- **Eşleşmeye izin ver** ve **Eşleşmeyi engelle**:

  - contoso.com/?q=whatever@fabrikam.com
  - contoso.com/a
  - contoso.com/a/b/c
  - contoso.com/ab
  - contoso.com/b
  - contoso.com/b/a/c
  - contoso.com/ba

- **eşleşmedi** ve **Engelle eşleşmedi**: contoso.com

#### <a name="scenario-left-wildcard-subdomain-and-right-wildcard-suffix"></a>Senaryo: Sol joker karakter alt etki alanı ve sağ joker karakter soneki

**Giriş**: `*.contoso.com/*`

- **Eşleşmeye izin ver** ve **Eşleşmeyi engelle**:

  - abc.contoso.com/ab
  - abc.xyz.contoso.com/a/b/c
  - www.contoso.com/a
  - www.contoso.com/b/a/c
  - xyz.contoso.com/ba

- **Eşleşmedi** ve **Engelle eşleşmedi**: contoso.com/b

#### <a name="scenario-left-and-right-tilde"></a>Senaryo: Sol ve sağ tilde

**Giriş**: `~contoso.com~`

- **Eşleşmeye izin ver** ve **Eşleşmeyi engelle**:

  - contoso.com
  - contoso.com/a
  - www.contoso.com
  - www.contoso.com/b
  - xyz.abc.contoso.com

- **Eşleşmedi** ve **Engelle eşleşmedi**:

  - 123contoso.com
  - contoso.org

#### <a name="scenario-ip-address"></a>Senaryo: IP adresi

**Giriş**: `1.2.3.4`

- **Eşleşmeye izin ver** ve **Eşleşmeyi engelle**: 1.2.3.4

- **Eşleşmedi** ve **Engelle eşleşmedi**:

  - 1.2.3.4/a
  - 11.2.3.4/a

#### <a name="ip-address-with-right-wildcard"></a>Sağ joker karakterli IP adresi

**Giriş**: `1.2.3.4/*`

- **Eşleşmeye izin ver** ve **Eşleşmeyi engelle**:

  - 1.2.3.4/b
  - 1.2.3.4/baaaa

### <a name="examples-of-invalid-entries"></a>Geçersiz girdi örnekleri

Aşağıdaki girdiler geçersiz:

- **Eksik veya geçersiz etki alanı değerleri**:

  - Contoso
  - \*.contoso.\*
  - \*.com
  - \*.pdf

- **Metinde veya aralık karakterleri olmadan joker karakter**:

  - \*contoso.com
  - contoso.com\*
  - \*1.2.3.4
  - 1.2.3.4\*
  - contoso.com/a\*
  - contoso.com/ab\*

- **Bağlantı noktaları olan IP adresleri**:

  - contoso.com:443
  - abc.contoso.com:25

- **Açıklayıcı olmayan joker karakterler**:

  - \*
  - \*.\*

- **Orta joker karakterler**:

  - conto\* so.com
  - conto~so.com

- **Çift joker karakter**

  - contoso.com/\*\*
  - contoso.com/\*/\*

## <a name="domain-pair-syntax-for-spoofed-sender-entries-in-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelle Listesindeki sahte gönderen girişleri için etki alanı çifti söz dizimi

Kiracı İzin Ver/Engelle Listesindeki kimlik sahtekarı bir gönderen için etki alanı çifti aşağıdaki söz dizimini kullanır: `<Spoofed user>, <Sending infrastructure>`.

- **Kimlik sahtekarı kullanıcı**: Bu değer, e-posta istemcilerindeki **Kimden** kutusunda görüntülenen sahte kullanıcının e-posta adresini içerir. Bu adres, adres olarak `5322.From` da bilinir. Geçerli değerler şunlardır:
  - Tek bir e-posta adresi (örneğin, chris@contoso.com).
  - E-posta etki alanı (örneğin, contoso.com).
  - Joker karakter (örneğin, \*).

- **Altyapı gönderiliyor**: Bu değer, sahte kullanıcıdan gelen iletilerin kaynağını gösterir. Geçerli değerler şunlardır:
  - Kaynak e-posta sunucusunun IP adresinin (örneğin, fabrikam.com) ters DNS aramasında (PTR kaydı) bulunan etki alanı.
  - Kaynak IP adresinin PTR kaydı yoksa, gönderen altyapı /24 olarak \<source IP\>tanımlanır (örneğin, 192.168.100.100/24).

Sahte gönderenleri tanımlamak için geçerli etki alanı çiftlerinin bazı örnekleri aşağıda verilmiştir:

- `contoso.com, 192.168.100.100/24`
- `chris@contoso.com, fabrikam.com`
- `*, contoso.net`

Sahte gönderen girdisi sayısı üst sınırı 1000'dir.

Etki alanı çifti eklemek yalnızca kimlik sahtekarlığına sahip kullanıcının *ve* gönderen altyapının *birleşimine* izin verir veya engeller. Kimlik sahtekarı olan kullanıcının herhangi bir kaynaktan gelen e-postasına izin vermez veya sahte kullanıcı için gönderen altyapı kaynağından gelen e-postaya izin vermez.

Örneğin, aşağıdaki etki alanı çifti için bir izin ver girdisi eklersiniz:

- **Etki alanı**: gmail.com
- **Altyapı**: tms.mx.com

Yalnızca bu etki alanından gelen *ve* altyapı çifti gönderen iletilerin kimlik sahtekarlığına izin verilir. gmail.com sahtekarlık yapmaya çalışan diğer gönderenlere izin verilmez. diğer etki alanlarındaki tms.mx.com gelen gönderenlerden gelen iletiler kimlik sahtekarlığına göre denetleniyor.
