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
description: Yöneticiler, Güvenlik portalındaki Kiracı İzin Ver/Engelle Listesi'nde blokları yapılandırmayı öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 03c56e5e7e540766bb4a6048fba15b494c46d815
ms.sourcegitcommit: 4d6a8e9d69a421d6c293b2485a8aa5e806b71616
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65182727"
---
# <a name="add-blocks-in-the-tenant-allowblock-list"></a>Kiracı İzin Verilenler/Engellenenler Listesine engellemeler ekleme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

## <a name="use-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalını kullanma

### <a name="create-block-sender-entries-in-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelle Listesinde blok gönderen girdileri oluşturma

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**İlkeler & kuralları** \> **Tehdit İlkeleri** \> **Kuralları** bölümüne **Kiracı İzin Ver/Listeleri Engelle** bölümüne \> gidin. Ya da doğrudan **Kiracı İzin Ver/Engelle Listesi** sayfasına gitmek için kullanın <https://security.microsoft.com/tenantAllowBlockList>.

2. **Kiracı İzin Ver/Engelle Listesi** sayfasında **, Gönderenler** sekmesinin seçili olduğunu doğrulayın ve ardından Engelle simgesine tıklayın![.](../../media/m365-cc-sc-create-icon.png) **Engelle'ye bakın**.

3. Görüntülenen **Gönderenleri engelle** açılır penceresinde aşağıdaki ayarları yapılandırın:
   - **Gönderen e-posta adresleri veya etki alanları**: Satır başına en fazla 20 gönderen (e-posta adresi veya etki alanı) girin.
   - **Hiçbir zaman sona ermez**: Aşağıdaki adımlardan birini yapın:
     - Ayarın kapalı olduğunu doğrulayın (![Kapat.](../../media/scc-toggle-off.png)) ve **Girişlerin** sona erme tarihini belirtmek için Kaldır açık kutusunu kullanın.

       veya

     - Girişleri hiçbir zaman sona ermeyecek şekilde yapılandırmak için iki durumlu düğmeyi sağa taşıyın: ![İki durumlu düğmeyi açın.](../../media/scc-toggle-on.png).
   - **İsteğe bağlı not**: Girişler için açıklayıcı metin girin.

4. İşiniz bittiğinde **Ekle'ye** tıklayın.

> [!NOTE]
> Bu gönderenlerden gelen e-postalar _yüksek güvenilirlikli istenmeyen posta_ olarak engellenir (SCL = 9).

### <a name="create-block-url-entries-in-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelle Listesinde blok URL'si girdileri oluşturma

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**İlkeler & kuralları** \> **Tehdit İlkeleri** \> **Kuralları** bölümüne **Kiracı İzin Ver/Listeleri Engelle** bölümüne \> gidin. Ya da doğrudan **Kiracı İzin Ver/Engelle Listesi** sayfasına gitmek için kullanın <https://security.microsoft.com/tenantAllowBlockList>.

2. **Kiracı İzin Ver/Engelle Listesi** sayfasında **URL'ler** sekmesinin seçili olduğunu doğrulayın ve ardından Engelle simgesine tıklayın![.](../../media/m365-cc-sc-create-icon.png) **Engelle'ye bakın**.

3. Görüntülenen **URL'leri engelle** açılır penceresinde aşağıdaki ayarları yapılandırın:
   - **Joker karakterli URL'ler ekleme**: Satır başına en fazla 20 URL girin. URL girişlerinin söz dizimi hakkında ayrıntılı bilgi için [Kiracı İzin Verme/Engelleme Listesini Yönetme](tenant-allow-block-list.md) bölümündeki URL söz dizimi bölümüne bakın.
   - **Hiçbir zaman sona ermez**: Aşağıdaki adımlardan birini yapın:
     - Ayarın kapalı olduğunu doğrulayın (![Kapat.](../../media/scc-toggle-off.png)) ve **Girişlerin** sona erme tarihini belirtmek için Kaldır açık kutusunu kullanın.

       veya

     - Girişleri hiçbir zaman sona ermeyecek şekilde yapılandırmak için iki durumlu düğmeyi sağa taşıyın: ![İki durumlu düğmeyi açın.](../../media/scc-toggle-on.png).
   - **İsteğe bağlı not**: Girişler için açıklayıcı metin girin.

4. İşiniz bittiğinde **Ekle'ye** tıklayın.

> [!NOTE]
> Bu URL'leri içeren e-postalar _kimlik avı_ olarak engellenir.

### <a name="create-block-file-entries-in-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelle Listesinde blok dosyası girdileri oluşturma

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**İlkeler & kuralları** \> **Tehdit İlkeleri** \> **Kuralları** bölümüne **Kiracı İzin Ver/Listeleri Engelle** bölümüne \> gidin. Ya da doğrudan **Kiracı İzin Ver/Engelle Listesi** sayfasına gitmek için kullanın <https://security.microsoft.com/tenantAllowBlockList>.

2. **Kiracı İzin Ver/Engelle Listesi** sayfasında **Dosyalar** sekmesini seçin ve ardından Engelle simgesine tıklayın![.](../../media/m365-cc-sc-create-icon.png) **Engelle'ye bakın**.

3. Görüntülenen **Dosyaları engelle** açılır öğesinde aşağıdaki ayarları yapılandırın:
   - **Dosya karmaları ekleme**: Satır başına en fazla 20 SHA256 karma değeri girin.
   - **Hiçbir zaman sona ermez**: Aşağıdaki adımlardan birini yapın:
     - Ayarın kapalı olduğunu doğrulayın (![Kapat.](../../media/scc-toggle-off.png)) ve **Girişlerin** sona erme tarihini belirtmek için Kaldır açık kutusunu kullanın.

     veya

     - Girişleri hiçbir zaman sona ermeyecek şekilde yapılandırmak için iki durumlu düğmeyi sağa taşıyın: ![İki durumlu düğmeyi açın.](../../media/scc-toggle-on.png).
   - **İsteğe bağlı not**: Girişler için açıklayıcı metin girin.

4. İşiniz bittiğinde **Ekle'ye** tıklayın.

> [!NOTE]
> Bu dosyaları içeren e-postalar _kötü amaçlı yazılım_ olarak engellenir.

### <a name="create-spoofed-sender-block-entries"></a>Sahte gönderen bloğu girdileri oluşturma

**Notlar**:

- Yalnızca kimlik sahtekarlığına neden olan kullanıcı _ile_ etki alanı çiftinde tanımlanan gönderme _altyapısının birleşimine_ özellikle izin verilir veya kimlik sahtekarlığına engellenir.
- Bir etki alanı çifti için izin ver veya engelle girdisi yapılandırdığınızda, bu etki alanı çiftinden gelen iletiler artık kimlik sahtekarı zeka içgörülerinde görünmez.
- Sahte gönderenlerin girdilerinin süresi hiçbir zaman dolmaz.
- Kimlik sahtekarı hem izin verme hem de engellemeyi destekler.

1. Microsoft 365 Defender portalında **İlkeler & kuralları** \> **Tehdit İlkeleri** \> **Kuralları** bölümüne **Kiracı İzin Ver/Listeleri Engelle** bölümüne \> gidin.

2. **Kiracı İzin Ver/Engelle Listesi** sayfasında Kimlik **Sahtekarlık** sekmesini seçin ve ardından Engelle simgesine tıklayın![.](../../media/m365-cc-sc-create-icon.png) **Ekle'yi seçin**.

3. Görüntülenen **Yeni etki alanı çiftleri ekle** açılır penceresinde aşağıdaki ayarları yapılandırın:
   - **Joker karakterlerle yeni etki alanı çiftleri ekleyin**: Satır başına en fazla 20 etki alanı çifti girin. Kimlik sahtekarlığına neden olan gönderen girdilerinin söz dizimi hakkında ayrıntılı bilgi için bkz. [Kiracı İzin Verme/Engelleme Listesini Yönetme](tenant-allow-block-list.md).
   - **Kimlik sahtekarı türü**: Aşağıdaki değerlerden birini seçin:
     - **İç**: Sahte gönderen, kuruluşunuza ait bir etki alanındadır ( [kabul edilen bir etki alanı](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)).
     - **Dış**: Sahte gönderen bir dış etki alanında.
   - **Eylem**: **Engelle'yi** seçin.

4. İşiniz bittiğinde **Ekle'ye** tıklayın.

> [!NOTE]
> Bu gönderenlerden gelen e-postalar _kimlik avı_ olarak engellenir.

## <a name="use-powershell"></a>PowerShell kullanma

### <a name="add-block-sender-file-or-url-entries-to-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelle Listesi'ne blok göndereni, dosyayı veya URL girdilerini ekleme

Kiracı İzin Ver/Engelle Listesi'ne blok gönderen, dosya veya URL girdileri eklemek için aşağıdaki söz dizimini kullanın:

```powershell
New-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Block -Entries "Value1","Value2",..."ValueN" <-ExpirationDate Date | -NoExpiration> [-Notes <String>]
```

Bu örnek, belirtilen gönderen için belirli bir tarihte süresi dolan bir engel gönderen girdisi ekler.

```powershell
New-TenantAllowBlockListItems -ListType Sender -Block -Entries "test@badattackerdomain.com", "test2@anotherattackerdomain.com" -ExpirationDate 8/20/2021
```

Bu örnek, belirtilen dosyalar için hiçbir zaman süresi dolmamış bir blok dosyası girdisi ekler.

```powershell
New-TenantAllowBlockListItems -ListType FileHash -Block -Entries "768a813668695ef2483b2bde7cf5d1b2db0423a0d3e63e498f3ab6f2eb13ea3","2c0a35409ff0873cfa28b70b8224e9aca2362241c1f0ed6f622fef8d4722fd9a" -NoExpiration
```

Bu örnek, contoso.com ve tüm alt etki alanları (örneğin, contoso.com, www.contoso.com ve xyz.abc.contoso.com) için bir blok URL girişi ekler. ExpirationDate veya NoExpiration parametrelerini kullanmadığımız için girdinin süresi 30 gün sonra dolar.

```powershell
New-TenantAllowBlockListItems -ListType Url -Block -Entries ~contoso.com
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-TenantAllowBlockListItems](/powershell/module/exchange/new-tenantallowblocklistitems).

### <a name="add-spoofed-sender-block-entries"></a>Sahte gönderen bloğu girdileri ekleme

Kiracı İzin Ver/Engelle Listesi'ne sahte gönderen girdileri eklemek için aşağıdaki söz dizimini kullanın:

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).
