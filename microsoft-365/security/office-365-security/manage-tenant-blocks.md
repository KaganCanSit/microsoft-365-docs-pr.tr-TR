---
title: Kiracı İzin Ver/Engelle Listesinde bloklarınızı yönetme
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Yöneticiler, güvenlik portalında Kiracı İzin Ver/Engelleme Listesi'ni nasıl yapılandıracaklarını öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4cca466ce4862cc93ec7521bf6bd00fe960f06a9
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317437"
---
# <a name="add-blocks-in-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelle Listesine blok ekleme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

## <a name="use-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalını kullanma 

### <a name="create-block-sender-entries-in-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelleme Listesi'ne gönderenleri engelleme girdileri oluşturma

1. Microsoft 365 Defender portalında, İlkeler ve kurallar **& Kuralları** \> **Tehdit** \> **İlkeleri** bölümü Kiracı İzin \> Verme **/Engelleme Listeleri'ne gidin**.

2. Kiracı İzin **Ver/Engelleme Listesi sayfasında** Gönderenler **sekmesinin seçili olduğunu** doğrulayın ve Engelle simgesine ![tıklayın.](../../media/m365-cc-sc-create-icon.png) **Engelle.**

3. Görüntülenen **Gönderenleri engelle** açılır sayfasında aşağıdaki ayarları yapılandırabilirsiniz:
   - **Gönderenin e-posta adresleri** veya etki alanları: Satır başına en çok 20 gönderen (e-posta adresi veya etki alanı) girin.
   - **Asla süresi** dolmaz: Aşağıdaki adımlardan birini uygulayın:
     - Ayarın kapalı olduğunu doğrulayın (![Kapalı olarak değiştir).](../../media/scc-toggle-off.png)) ve girişlerin son kullanma tarihini belirtmek için Kaldır kutusunu kullanın.

       veya

     - Girdilerin süresini hiçbir zaman dolmamak üzere yapılandırmak için iki durumlu düğmeyi sağa taşıma: ![Geçiş'i açık olarak geçişin.](../../media/scc-toggle-on.png).
   - **İsteğe** bağlı not: Girdiler için açıklayıcı metin girin.

4. Bitirdikten sonra Ekle'ye **tıklayın**.

> [!NOTE]
> Bu gönderenlerden gelen e-postalar istenmeyen posta olarak *engellenir*. 

### <a name="create-block-url-entries-in-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelleme Listesinde engellenen URL girdileri oluşturma

1. Microsoft 365 Defender portalında, İlkeler ve kurallar **& Kuralları** \> **Tehdit** \> **İlkeleri** bölümü Kiracı İzin \> Verme **/Engelleme Listeleri'ne gidin**.

2. Kiracı İzin **Ver/Engelleme Listesi sayfasında** URL'ler **sekmesinin seçili** olduğunu doğrulayın ve Engelle simgesine ![tıklayın.](../../media/m365-cc-sc-create-icon.png) **Engelle.**

3. Görüntülenen **URL'leri** engelle açılır sayfasında aşağıdaki ayarları yapılandırabilirsiniz:
   - **Joker karakterli URL ekleme**: Satır başına en çok 20 URL girin. URL girdilerinin söz dizimi hakkında ayrıntılı bilgi için, Kiracı İzin Ver/Engelleme Listesini Yönetme [bölümündeki URL söz dizimi bölümüne bakın](tenant-allow-block-list.md).
   - **Asla süresi** dolmaz: Aşağıdaki adımlardan birini uygulayın:
     - Ayarın kapalı olduğunu doğrulayın (![Kapalı olarak değiştir).](../../media/scc-toggle-off.png)) ve girişlerin son kullanma tarihini belirtmek için Kaldır kutusunu kullanın.

       veya

     - Girdilerin süresini hiçbir zaman dolmamak üzere yapılandırmak için iki durumlu düğmeyi sağa taşıma: ![Geçiş'i açık olarak geçişin.](../../media/scc-toggle-on.png).
   - **İsteğe** bağlı not: Girdiler için açıklayıcı metin girin.

4. Bitirdikten sonra Ekle'ye **tıklayın**.

> [!NOTE]
> Bu URL'leri içeren e-postalar kimlik avı olarak *engellenir*. 

### <a name="create-block-file-entries-in-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelleme Listesi'ne dosya engelleme girdileri oluşturma

1. Microsoft 365 Defender portalında, İlkeler ve kurallar **& Kuralları** \> **Tehdit** \> **İlkeleri** bölümü Kiracı İzin \> Verme **/Engelleme Listeleri'ne gidin**.

2. Kiracı İzin **Ver/Engelleme Listesi sayfasında** Dosyalar sekmesini **seçin ve** engelle simgesine ![tıklayın.](../../media/m365-cc-sc-create-icon.png) **Engelle.**

3. Görüntülenen **Dosyaları engelle** açılır sayfasında, aşağıdaki ayarları yapılandırabilirsiniz:
   - **Dosya karmaları ekleme**: Satır başına bir SHA256 karma değeri (en çok 20 tane) girin.
   - **Asla süresi** dolmaz: Aşağıdaki adımlardan birini uygulayın:
     - Ayarın kapalı olduğunu doğrulayın (![Kapalı olarak değiştir).](../../media/scc-toggle-off.png)) ve girişlerin son kullanma tarihini belirtmek için Kaldır kutusunu kullanın.

     veya

     - Girdilerin süresini hiçbir zaman dolmamak üzere yapılandırmak için iki durumlu düğmeyi sağa taşıma: ![Geçiş'i açık olarak geçişin.](../../media/scc-toggle-on.png).
   - **İsteğe** bağlı not: Girdiler için açıklayıcı metin girin.

4. Bitirdikten sonra Ekle'ye **tıklayın**.

> [!NOTE]
> Bu dosyaları içeren e-postalar kötü amaçlı yazılım olarak *engellenir*. 

### <a name="create-spoofed-sender-block-entries"></a>Gizli gönderen engelleme girdileri oluşturma

**Notlar**:

- Yalnızca _kimlik_ doğrulanmamış kullanıcının ve etki alanı çifti  içinde tanımlandığı üzere gönderme altyapısının birleşimine özel olarak kimlik doğrulama izni verilir veya bu altyapı engellenir.
- Bir etki alanı çifti için bir izin verme veya engelleme girdisi yapılandırıldığında, bu etki alanı çiftinin iletileri artık kimlik bilgileri bilgisinde görünmez.
- Kimliği doğru gönderenlerin girdilerinin süresi hiçbir zaman dolmaz.
- Poof, hem izin verme hem de engellemeyi destekler.

1. Microsoft 365 Defender portalında, İlkeler ve kurallar **& Kuralları** \> **Tehdit** \> **İlkeleri** bölümü Kiracı İzin \> Verme **/Engelleme Listeleri'ne gidin**.

2. Kiracı İzin **Ver/Engelleme Listesi sayfasında** , Bilgi Verme **sekmesini seçin ve** ardından Engelle simgesine ![tıklayın.](../../media/m365-cc-sc-create-icon.png) **ekle'yi seçin**.

3. Görüntülenen **Yeni etki alanı çiftleri** ekle açılır sayfasında, aşağıdaki ayarları yapılandırabilirsiniz:
   - **Joker karakterlerle yeni etki alanı çiftleri ekleme**: Satır başına bir etki alanı çifti (en çok 20) girin. Hatalı gönderen girişlerinin söz dizimi hakkında ayrıntılı bilgi için bkz. [Kiracı İzin Ver/Engelleme Listesini Yönetme](tenant-allow-block-list.md).
   - **Poof türü**: Aşağıdaki değerlerden birini seçin:
     - **İç**: Kimliği doğru olmayan gönderen, organizasyona ait bir etki alanında (kabul edilen etki [alanı) yer alır](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
     - **Dış**: Gönderenin kimliği doğru değil dış etki alanında.
   - **Eylem**: İzin **Ver'i veya** **Engelle'yi seçin**.

4. Bitirdikten sonra Ekle'ye **tıklayın**.

## <a name="use-powershell"></a>PowerShell kullanma

### <a name="add-block-sender-file-or-url-entries-to-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelleme Listesi'ne gönderen, dosya veya URL girdileri ekleme

Kiracı İzin Ver/Engelleme Listesi'ne gönderen, dosya veya URL girdileri eklemek için aşağıdaki söz dizimlerini kullanın:

```powershell
New-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Block -Entries "Value1","Value2",..."ValueN" <-ExpirationDate Date | -NoExpiration> [-Notes <String>]
```

Bu örnek, belirtilen tarihte süresi dolan gönderen için bir engellenen gönderen girdisi ekler.

```powershell
New-TenantAllowBlockListItems -ListType Sender -Block -Entries "test@badattackerdomain.com", "test2@anotherattackerdomain.com" -ExpirationDate 8/20/2021
```

Bu örnek, belirtilen dosyaların süresi hiç dolmadan engellenen dosya girdilerini ekler.

```powershell
New-TenantAllowBlockListItems -ListType FileHash -Block -Entries "768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3","2c0a35409ff0873cfa28b70b8224e9aca2362241c1f0ed6f622fef8d4722fd9a" -NoExpiration
```

Bu örnekte, contoso.com ve tüm alt etki alanları (örneğin, contoso.com, Ekle ve Tamam www.contoso.com) için bir engellenen URL xyz.abc.contoso.com. ExpirationDate veya NoExpiration parametrelerini kullanmamız nedeniyle, girişin süresi 30 gün sonra dolmaz.

```powershell
New-TenantAllowBlockListItems -ListType Url -Block -Entries ~contoso.com
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

### <a name="add-spoofed-sender-block-entries"></a>Kimliği doğru olan gönderen engelleme girdilerini ekleme 

Kiracı İzin Ver/Engelleme Listesi'ne hatalı gönderen girdileri eklemek için aşağıdaki söz dizimlerini kullanın:

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).
