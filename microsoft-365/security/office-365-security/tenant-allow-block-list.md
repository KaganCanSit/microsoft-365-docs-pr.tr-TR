---
title: Kiracı İzin Ver/Engelle Listesinde izin ve bloklarınızı yönetme
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
description: Yöneticiler, güvenlik portalında yer alan Kiracı İzin Ver/Engelleme Listesi'nin izinlerini ve bloklarını yönetmeyi öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e27da44a38162955df252e29c1754c93a2dc8967
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63318571"
---
# <a name="manage-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelleme Listesini Yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
>
> Bu makalede açıklanan özelliklerden bazıları Önizleme'dedir, değişebilir ve tüm kuruluşlarda kullanılamaz.
>
> Bu makalede açıklandığı gibi kuruluşta kimliği doğrulanıyorsa, [EOP'de](walkthrough-spoof-intelligence-insight.md) akıllı ifade ilkesi ve bilgimli ifadeyi kullanarak kimliği doğru gönderenleri yönetme makalesinde eski kullanıcı kimliğine sahip yönetim deneyimine bakın.

EOP Microsoft 365 kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarına posta kutusu Exchange Online kuruluşlarda, EOP filtreleme kararını kabul edeyleyemsiniz. Örneğin, iyi bir ileti kötü (hatalı pozitif) olarak işaretlenir veya hatalı bir iletiye izin (yanlış negatif) olabilir.

Yeni Portalında Yer Alan Kiracı İzinleri/Microsoft 365 Defender Listesi, size verilen kararların filtresini geçersiz Microsoft 365 bir yol sağlar. Kiracı İzin Ver/Engelleme Listesi, gelen iletiler için posta akışı sırasında (kuruluş içi iletiler için geçerli değildir) ve kullanıcı tıklamaları sırasında kullanılır. Aşağıdaki geçersiz kılma türlerini belirterek:

- Engellenmiş olacak URL'ler.
- Engellenmiş dosyalar.
- Engellen gönderilecek gönderen e-postaları veya etki alanları.
- İzin vermek veya engellemek için kimliği doğru engellenen gönderenler. Bilgi bloğu içgörüsinde izin verme veya engelleme kararını geçersiz kılarsanız[, kimliği](learn-about-spoof-intelligence.md) doğruya sahip olan gönderen, yalnızca Kiracı İzin Ver/Engelle Listesi'nin Gizli Bilgi sekmesinde  görüntülenen bir el ile izin verme veya engelleme girişi haline gelir. Ayrıca, burada kimliği doğru hesabıyla alınan gönderenler için, kimliği doğrulandığından önce bu gönderenlere el ile izin verme veya engelleme girdileri oluşturabilirsiniz.
- İzin verecek URL'ler.
- İzin verecek dosyalar.
- İzin vermek için gönderen e-postaları veya etki alanları.

Bu makalede, Microsoft 365 Defender portalında veya PowerShell'de (Microsoft 365 posta kutusu olan Microsoft 365 kuruluşları için Exchange Online PowerShell; Exchange Online'te posta kutusu olmayan kuruluşlar için tek başına EOP PowerShell'de girişlerin nasıl yapılandırıldığından emin olun Exchange Online kutularını da) kullanın.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açın<https://security.microsoft.com>. Doğrudan Kiracı İzin Ver **/Listeleri Engelleme sayfasına gitmek** için kullanın <https://security.microsoft.com/tenantAllowBlockList>.

- Dosyaları, dosyanın SHA256 karma değerini kullanarak belirtirsiniz. Dosyanın SHA256 karma değerini Windows Komut İstemi'ne aşağıdaki komutu çalıştırın:

  ```console
  certutil.exe -hashfile "<Path>\<Filename>" SHA256
  ```

  Örnek bir değerdir `768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3a`. Algısal karma (pHash) değerleri desteklenmiyor.

- Kullanılabilir URL değerleri, bu makalenin devam [bölümündeki Kiracı İzin Ver/](#url-syntax-for-the-tenant-allowblock-list) Engelleme Listesi bölümünün URL söz dizim bölümünde açıklanmıştır.

- Kiracı İzin Ver/Engelle Listesi gönderenler için en çok 500 girdi, URL'ler için 500 girdi, dosya karmaları için 500 girdi ve kimliği doğrunlama için 1024 girdiye izin verir.

- Her girdi için en fazla karakter sayısı:
  - Dosya karmaları = 64
  - URL = 250

- Girdinin 30 dakika içinde etkin olması gerekir.

- Varsayılan olarak, Kiracı İzin Ver/Engelleme Listesi'ne gelen girdilerin süresi 30 gün sonra dolar. Bir tarih belirterek veya asla süresi dolmay bunları olarak ayarlayın.

- Exchange Online PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online e bağlama](/powershell/exchange/connect-to-exchange-online-powershell). Tek başına EOP PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online Protection e bağlama](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Bu makaledeki yordamları yerine Microsoft 365 Defender portalında izinlerin atanmamış olması gerekir:
  - **Gönderenler, URL'ler ve dosyalar**:
    - Kiracı İzin Ver/Engelleme Listesi'nde değerleri eklemek ve kaldırmak için, Kuruluş **Yönetimi, Güvenlik** Yöneticisi veya Güvenlik İşleci rol gruplarına üye  olmalı veya **Kiracı AllowBlockList Manager** rolüne atanmışsınızdır.
    - Kiracı İzin Ver/Engelleme Listesine salt okunur erişim için, Genel Okuyucu veya Güvenlik **Okuyucusu rol** **gruplarının üyesi** olmak gerekir.
  - **Poofing**: Aşağıdaki kombinasyonlardan biri:
    - **Kuruluş Yönetimi**
    - **Güvenlik Yöneticisi** <u>ve</u> **Yalnızca Görüntüleme Yapılandırması veya** **Yalnızca Görüntüleme Kuruluş Yönetimi**.

  Daha fazla bilgi için bkz. [Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Görev sırasında ilgili kullanıcı Azure Active Directory eklemek Microsoft 365 yönetim merkezi kullanıcılara çalışma sayfalarındaki diğer özellikler için gerekli izinleri ve izinleri Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  >
  > - **Görünüm'de Yalnızca Görüntüleme** [kuruluş Exchange Online rol](/Exchange/permissions-exo/permissions-exo#role-groups) grubu, özel salt okunur erişim de sağlar.

## <a name="configure-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelleme Listesini Yapılandırma

### <a name="use-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalını kullanma

Aşağıdaki Microsoft 365 Defender portalında İlkeler ve <https://security.microsoft.com>kurallar **& Kurallar** \> bölümündeki **Tehdit** \> İlkeleri **Kiracı İzin Verme/** Engelleme **Listeleri bölümüne** gidin. Doğrudan Kiracı İzin Ver **/Listeleri Engelleme sayfasına gitmek** için kullanın <https://security.microsoft.com/tenantAllowBlockList>.

Tüm blokları eklemek için bkz [. Kiracı İzin Verme/Engelleme Listesi'ne blok ekleme](manage-tenant-blocks.md).

Tüm izinleri eklemek için bkz [. Kiracı İzin Ver/Engelleme Listesi'ne izin ekleme](manage-tenant-allows.md).

Tüm blokları ve izinlerini değiştirmek ve kaldırmak için bkz [. Kiracı İzin Verme/Engelleme Listesi'ni kullanarak girdileri değiştirme ve kaldırma](modify-remove-entries-tenant-allow-block.md).

### <a name="use-exchange-online-powershell-or-standalone-eop-powershell"></a>Exchange Online PowerShell veya tek başına EOP PowerShell kullanma

Tüm izin ve blokları yönetmek için bkz. Kiracı İzin Verme [/](manage-tenant-blocks.md)Engelleme Listesi'ne blok ekleme, Kiracı İzin Verme [/](manage-tenant-allows.md)Engelleme Listesi'ne izin ekleme ve Kiracı İzin Ver/Engelleme Listesi'ne girişleri değiştirme [ve kaldırma](modify-remove-entries-tenant-allow-block.md).

## <a name="view-entries-in-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelle Listesinde girdileri görüntüleme

1. Aşağıdaki Microsoft 365 Defender portalında İlkeler ve <https://security.microsoft.com>kurallar **& Kurallar** \> bölümündeki **Tehdit** \> İlkeleri **Kiracı İzin Verme/** Engelleme **Listeleri bölümüne** gidin. Doğrudan Kiracı İzin Ver **/Listeleri Engelleme sayfasına gitmek** için kullanın <https://security.microsoft.com/tenantAllowBlockList>.

2. İstediğiniz sekmeyi seçin. Kullanılabilir sütunlar, seçtiğiniz sekmeye bağlıdır:

   - **Gönderenler**:
     - **Değer**: Gönderenin etki alanı veya e-posta adresi.
     - **Eylem**: İzin Ver **veya Engelle** **değeri.**
     - **Değiştiren**
     - **Son güncelleştirme**
     - **Kaldırma günü**
     - **Notlar**
   - **URL'ler**:
     - **Değer**: URL.
     - **Eylem**: İzin Ver **veya Engelle** **değeri.**
     - **Değiştiren**
     - **Son güncelleştirme**
     - **Kaldırma günü**
     - **Notlar**
   - **Dosyalar**
     - **Değer**: Dosya karması.
     - **Eylem**: İzin Ver **veya Engelle** **değeri.**
     - **Değiştiren**
     - **Son güncelleştirme**
     - **Kaldırma günü**
     - **Notlar**
   - **Spoofing**
     - **Kullanıcı kimliklerini doğrulandı**
     - **Altyapı gönderme**
     - **Poof türü**: İç veya **Dış** **değerdir**.
     - **Eylem**: Engelle veya **İzin Ver** **değeridir**.

   Artan veya azalan düzende sıralamak için sütun başlığına tıkebilirsiniz.

   Sonuçları **grupla'yı** tıklatmak için Grup'u tıklatın. Kullanılabilir değerler, seçtiğiniz sekmeye bağlıdır:

   - **Gönderenler**: Sonuçları Eyleme göre **gruplandı**.
   - **URL'ler**: Sonuçları Eylem'e göre **gruplandı.**
   - **Dosyalar**: Sonuçları Eyleme göre **grupabilirsiniz**.
   - **Poylama**: Sonuçları Eylem veyaPoof **türüne** **göre gruplandı.**

   **Ara'ya** tıklayın, değerin bir bölümünü veya bölümünü girin ve belirli bir değeri bulmak için ENTER tuşuna basın. Bitirdikten sonra, Arama simgesini temizle'ye ![tıklayın.](../../media/m365-cc-sc-close-icon.png) **Arama temizleme**.

   Sonuçları **filtrelemek** için Filtrele'ye tıklayın. Görüntülenen Filtre açılır sekmesinde **bulunan** değerler, seçtiğiniz sekmeye bağlıdır:

   - **Gönderenler**
     - **Eylem**
     - **Hiçbir zaman süresi dolmaz**
     - **Son güncelleştirme tarihi**
     - **Kaldırma günü**
   - **URL'ler**
     - **Eylem**
     - **Hiçbir zaman süresi dolmaz**
     - **Son güncelleştirme tarihi**
     - **Kaldırma günü**
   - **Dosyalar**
     - **Eylem**
     - **Hiçbir zaman süresi dolmaz**
     - **Son güncelleştirme**
     - **Kaldırma günü**
   - **Spoofing**
     - **Eylem**
     - **Poof türü**

   Bitirdikten sonra Uygula'ya **tıklayın**. Varolan filtreleri temizlemek için, **Filtre'ye** tıklayın ve görüntülenen **Filtre** açılır alanında Filtreleri temizle'ye **tıklayın**.

4. Bitirdikten sonra Ekle'ye **tıklayın**.

## <a name="view-sender-file-or-url-entries-in-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelleme Listesi'ne gönderen, dosya veya URL girdilerini görüntüleme

Kiracı İzin Ver/Engelleme Listesi'ne gelen gönderen, dosya veya URL girdilerini engellemek için aşağıdaki söz dizimlerini kullanın:

```powershell
Get-TenantAllowBlockListItems -ListType <Sender | FileHash | URL> [-Entry <SenderValue | FileHashValue | URLValue>] [<-ExpirationDate Date | -NoExpiration>]
```

Bu örnekte, belirtilen dosya karma değeri için bilgiler döndürür.

```powershell
Get-TenantAllowBlockListItems -ListType FileHash -Entry "9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08"
```

Bu örnek, tüm engellenen URL'leri döndürür.

```powershell
Get-TenantAllowBlockListItems -ListType Url -Block
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-TenantAllowBlockListItems](/powershell/module/exchange/get-tenantallowblocklistitems).

## <a name="view-spoofed-sender-entries"></a>Gizli gönderen girdilerini görüntüleme

Kiracı İzin Ver/Engelleme Listesi'ne hatalı gönderen girdilerini görüntülemek için aşağıdaki söz dizimlerini kullanın:

```powershell
Get-TenantAllowBlockListSpoofItems [-Action <Allow | Block>] [-SpoofType <External | Internal>
```

Bu örnekte, Kiracı İzin Ver/Engelleme Listesi'ne ait tüm kimliği doğruya sahip gönderen girdileri döndürür.

```powershell
Get-TenantAllowBlockListSpoofItems
```

Bu örnekte, iç kullanıcılara ait tüm izin verilen gönderen girdileri iade edildi.

```powershell
Get-TenantAllowBlockListSpoofItems -Action Allow -SpoofType Internal
```

Bu örnekte, dış olan tüm engellenen kimliği doğruya sahip gönderen girdileri döndürür.

```powershell
Get-TenantAllowBlockListSpoofItems -Action Block -SpoofType External
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-TenantAllowBlockListSpoofItems](/powershell/module/exchange/get-tenantallowblocklistspoofitems).

## <a name="url-syntax-for-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelle Listesi için URL söz dizimi

- IPv4 ve IPv6 adreslerine izin verilir, ancak TCP/UDP bağlantı noktaları izin verilmez.

- Dosya adı uzantılarına izin verilmez (örneğin, test.pdf).

- Unicode desteklenmiyor, ancak Noktalama Kodu'dur.

- Aşağıdaki ifadelerin hepsi doğruysa, ana bilgisayar adlarına izin verilir:
  - Ana bilgisayar adı bir nokta içerir.
  - Dönemin en az bir karakteri vardır.
  - Dönemin sağ en az iki karakteri vardır.

  Örneğin, izin `t.co` verilir veya `.com` `contoso.` izin verilmez.

- Izinler için altpathler zımni değildir.

  Örneğin, `contoso.com` dahil değildir `contoso.com/a`.

- Aşağıdaki senaryolarda joker karakterlere (*) izin verilir:

  - Alt etki alanı belirtmek için, sol joker karakterin arkasından bir noktanın atlı bir dönemi olması gerekir.

    Örneğin, izin `*.contoso.com` verilir; `*contoso.com` izin verilmez.

  - Bir yol belirtmek için, sağ joker karakterin eğik çizgi (/) izlemesi gerekir.

    Örneğin, izin `contoso.com/*` verilir veya `contoso.com*` `contoso.com/ab*` izin verilmez.

  - `*.com*` geçersiz (çözümlenebilir bir etki alanı değildir ve doğru joker karakter eğik çizgiyle takip edilemez).

  - IP adreslerinde joker karakterlere izin verilmez.

- Tilde (~) karakteri aşağıdaki senaryolarda kullanılabilir:

  - Sol tilde bir etki alanını ve tüm alt etki alanları belirtir.

    Örneğin, `~contoso.com` ve içerir`*.contoso.com``contoso.com`.

- URL girdileri tüm protokollere geçerli olduğundan, protokol içeren URL girdileri (örneğin, `http://`, `https://``ftp://`veya ) başarısız olur.

- Kullanıcı adı veya parola desteklenmiyor veya gerekli değildir.

- Tırnak (' veya ") geçersiz karakterlerdir.

- Bir URL, mümkün olduğunca tüm yönlendirmeleri içermeli.

### <a name="url-entry-scenarios"></a>URL giriş senaryoları

Geçerli URL girdileri ve sonuçları aşağıdaki bölümlerde açıklanmıştır.

#### <a name="scenario-no-wildcards"></a>Senaryo: Joker karakter yok

**Girdi**: `contoso.com`

- **Eşleşmeye izin** ver: contoso.com

- **Eşleşmeye izin ver**:

  - abc-contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

- **Eşleşmeyi engelle**:

  - contoso.com
  - contoso.com/a
  - payroll.contoso.com
  - test.com/contoso.com
  - test.com/q=contoso.com
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

- **Blok eşleşmedi**: abc-contoso.com

#### <a name="scenario-left-wildcard-subdomain"></a>Senaryo: Sol joker karakter (alt etki alanı)

**Girdi**: `*.contoso.com`

- **Eşleşmeye izin ver** ve **Eşleşmeyi engelle**:

  - www.contoso.com
  - xyz.abc.contoso.com

- **Eşleşmeye izin ver ve** **Engelle eşleşmedi**:

  - 123contoso.com
  - contoso.com
  - test.com/contoso.com
  - www.contoso.com/abc

#### <a name="scenario-right-wildcard-at-top-of-path"></a>Senaryo: Yolun en üstünde sağ joker karakter

**Girdi**: `contoso.com/a/*`

- **Eşleşmeye izin ver** ve **Eşleşmeyi engelle**:

  - contoso.com/a/b
  - contoso.com/a/b/c
  - contoso.com/a/?q=joe@t.com

- **Eşleşmeye izin ver ve** **Engelle eşleşmedi**:

  - contoso.com
  - contoso.com/a
  - www.contoso.com
  - www.contoso.com/q=a@contoso.com

#### <a name="scenario-left-tilde"></a>Senaryo: Sol tilde

**Girdi**: `~contoso.com`

- **Eşleşmeye izin ver** ve **Eşleşmeyi engelle**:

  - contoso.com
  - www.contoso.com
  - xyz.abc.contoso.com

- **Eşleşmeye izin ver ve** **Engelle eşleşmedi**:

  - 123contoso.com
  - contoso.com/abc
  - www.contoso.com/abc

#### <a name="scenario-right-wildcard-suffix"></a>Senaryo: Sağ joker karakter son eki

**Girdi**: `contoso.com/*`

- **Eşleşmeye izin ver** ve **Eşleşmeyi engelle**:

  - contoso.com/?q=whatever@fabrikam.com
  - contoso.com/a
  - contoso.com/a/b/c
  - contoso.com/ab
  - contoso.com/b
  - contoso.com/b/a/c
  - contoso.com/ba

- **Eşleşmeye izin ver ve** **Engelle eşleşmedi**: contoso.com

#### <a name="scenario-left-wildcard-subdomain-and-right-wildcard-suffix"></a>Senaryo: Sol joker karakterli alt etki alanı ve sağ joker karakter son eki

**Girdi**: `*.contoso.com/*`

- **Eşleşmeye izin ver** ve **Eşleşmeyi engelle**:

  - abc.contoso.com/ab
  - abc.xyz.contoso.com/a/b/c
  - www.contoso.com/a
  - www.contoso.com/b/a/c
  - xyz.contoso.com/ba

- **Eşleşmeye izin ver ve** **Engelle eşleşmedi**: contoso.com/b

#### <a name="scenario-left-and-right-tilde"></a>Senaryo: Sol ve sağ tilde

**Girdi**: `~contoso.com~`

- **Eşleşmeye izin ver** ve **Eşleşmeyi engelle**:

  - contoso.com
  - contoso.com/a
  - www.contoso.com
  - www.contoso.com/b
  - xyz.abc.contoso.com

- **Eşleşmeye izin ver ve** **Engelle eşleşmedi**:

  - 123contoso.com
  - contoso.org

#### <a name="scenario-ip-address"></a>Senaryo: IP adresi

**Girdi**: `1.2.3.4`

- **Eşleşmeye izin** **ver ve Engelleme eşleşmesi**: 1.2.3.4

- **Eşleşmeye izin ver ve** **Engelle eşleşmedi**:

  - 1.2.3.4/a
  - 11.2.3.4/a

#### <a name="ip-address-with-right-wildcard"></a>Sağ joker karakterli IP adresi

**Girdi**: `1.2.3.4/*`

- **Eşleşmeye izin ver** ve **Eşleşmeyi engelle**:

  - 1.2.3.4/b
  - 1.2.3.4/baaaa

### <a name="examples-of-invalid-entries"></a>Geçersiz giriş örnekleri

Aşağıdaki girişler geçersiz:

- **Eksik veya geçersiz etki alanı değerleri**:

  - contoso
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

- **Bağlantı noktası olan IP adresleri**:

  - contoso.com:443
  - abc.contoso.com:25

- **Açıklayıcı olmayan joker karakterler**:

  - \*
  - \*.\*

- **Orta joker karakterler**:

  - conto\* so.com
  - conto~so.com

- **Çift joker karakterler**

  - contoso.com/\*\*
  - contoso.com/\*/\*

## <a name="domain-pair-syntax-for-spoofed-sender-entries-in-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelle Listesinde hatalı gönderen girdileri için etki alanı çifti söz dizimi

Kiracı İzin Ver/Engelleme Listesi'ne hatalı gönderen için etki alanı çifti şu söz dizimi kullanılır: `<Spoofed user>, <Sending infrastructure>`.

- **Kimlikfli kullanıcı**: Bu değer, e-posta istemcilerinin İlk kutusunda görüntülenen kimlik doğrulu **kullanıcının e-posta** adresini içerir. Bu adres, adres olarak da `5322.From` bilinir. Geçerli değerler şunlardır:
  - Tek bir e-posta adresi (örneğin, chris@contoso.com).
  - Bir e-posta etki alanı (örneğin, contoso.com).
  - Joker karakter (örneğin, \*).

- **Altyapı gönderme**: Bu değer, kimlik doğrulu kullanıcıdan gelen iletilerin kaynağını gösterir. Geçerli değerler şunlardır:
  - Kaynak e-posta sunucusunun IP adresinin ters DNS araması (PTR kaydı) içinde bulunan etki alanı (örneğin, PtR fabrikam.com).
  - Kaynak IP adresinin PTR kaydı yoksa, \<source IP\>gönderme altyapısı /24 olarak tanımlanır (örneğin, 192.168.100.100/24).

Aşağıda, kimlik doğru hesabı olan gönderenleri tanımlamak için geçerli etki alanı çiftlerinden bazı örnekler verilmiştir:

- `contoso.com, 192.168.100.100/24`
- `chris@contoso.com, fabrikam.com`
- `*, contoso.net`

En fazla kimliği doğru gönderen girdisi sayısı 1000'tir.

Etki alanı çifti ekleme yalnızca kimlik *doğrulu* kullanıcıyla gönderme altyapısının birleşimine *izin verir veya* bu birleşimi engeller. Kimlik doğrulu kullanıcının herhangi bir kaynaktan e-postasına izin vermez ya da kimlik doğrulu herhangi bir kullanıcının gönderen altyapı kaynağından gelen e-postaya izin vermez. 

Örneğin, aşağıdaki etki alanı çifti için bir izin girdisi eklersiniz:

- **Etki** alanı: gmail.com
- **Altyapı**: tms.mx.com

Yalnızca bu etki alanındaki *ve gönderen* altyapı çiftlerinden gelen iletilerin hesabı doğru olarak kullanılabilir. Bu e-postayı kullanarak bilgi gmail.com diğer gönderenlere izin verilmez. Diğer etki alanlarındaki gönderenlerden gelen ve e-tms.mx.com, akıllı e-posta adresi tarafından denetlenir.
