---
title: Kiracı İzin Verilenler/Engellenenler Listesinde girdileri değiştirme ve kaldırma
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
description: Yöneticiler, Güvenlik portalındaki Kiracı İzin Ver/Engelle Listesi'ndeki girdileri değiştirmeyi ve kaldırmayı öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7da986c42421c797f2d01b1e61d50c06933e373f
ms.sourcegitcommit: 45bc65972d4007b2aa7760d4457a0d2699f81926
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64970950"
---
# <a name="modify-and-remove-entries-in-the-tenant-allowblock-list"></a>Kiracı İzin Verilenler/Engellenenler Listesinde girdileri değiştirme ve kaldırma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Kiracı İzin Ver/Engelle Listesi'ndeki girdileri değiştirmek ve kaldırmak için Microsoft 365 Defender portalını veya PowerShell'i kullanabilirsiniz.

## <a name="use-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalını kullanma

### <a name="modify-entries-in-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelle Listesindeki girdileri değiştirme

1. Microsoft 365 Defender portalında **İlkeler & kuralları** \> **Tehdit İlkeleri** \> **Kuralları** bölümüne **Kiracı İzin Ver/Listeleri Engelle** bölümüne \> gidin.

2. Değiştirmek istediğiniz girdi türünü içeren sekmeyi seçin:
   - **Gönderenler**
   - **Sızdırma**
   - **Url 'leri**
   - **Dosyaları**

3. Değiştirmek istediğiniz girdiyi seçin ve düzenle simgesine tıklayın ![.](../../media/m365-cc-sc-edit-icon.png) **Düzenle'yi seçin**. Görüntülenen açılır öğede değiştirebileceğiniz değerler, önceki adımda seçtiğiniz sekmeye bağlıdır:
   - **Gönderenler**
     - **Hiçbir zaman süresi dolmaz** ve/veya son kullanma tarihi.
     - **İsteğe bağlı not**
   - **Sızdırma**
     - **Eylem**: Değeri **İzin Ver** veya **Engelle** olarak değiştirebilirsiniz.
   - **Url 'leri**
     - **Hiçbir zaman süresi dolmaz** ve/veya son kullanma tarihi.
     - **İsteğe bağlı not**
   - **Dosyaları**
     - **Hiçbir zaman süresi dolmaz** ve/veya son kullanma tarihi.
     - **İsteğe bağlı not**

4. Bitirdiğinizde, **Kaydet**'i tıklatın.

> [!NOTE]
> İzin verilen süreyi yalnızca oluşturma tarihinden sonra en fazla 30 gün uzatabilirsiniz. Bloklar 90 güne kadar uzatılabilir, ancak izin vermedikleri gibi Süresi hiç dolmaz olarak da ayarlanabilir.

### <a name="remove-entries-from-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelle Listesinden girdileri kaldırma

1. Microsoft 365 Defender portalında **İlkeler & kuralları** \> **Tehdit İlkeleri** \> **Kuralları** bölümüne **Kiracı İzin Ver/Listeleri Engelle** bölümüne \> gidin.

2. Kaldırmak istediğiniz girdi türünü içeren sekmeyi seçin:
   - **Gönderenler**
   - **Sızdırma**
   - **Url 'leri**
   - **Dosyaları**

3. Kaldırmak istediğiniz girdiyi seçin ve sil simgesine tıklayın ![.](../../media/m365-cc-sc-delete-icon.png) **Sil'i seçin**.

4. Görüntülenen uyarı iletişim kutusunda **Sil'e** tıklayın.

## <a name="use-powershell"></a>PowerShell kullanma

### <a name="modify-allow-or-block-sender-file-and-url-entries-in-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelle Listesinde gönderen, dosya ve URL girişlerine izin verme veya engelleme

Kiracı İzin Ver/Engelle Listesindeki gönderen, dosya ve URL girişlerine izin vermek veya bunları engellemek için aşağıdaki söz dizimini kullanın:

```powershell
Set-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Ids <"Id1","Id2",..."IdN"> [<-ExpirationDate Date | -NoExpiration>] [-Notes <String>]
```

Bu örnek, belirtilen blok URL'si girişinin sona erme tarihini değiştirir.

```powershell
Set-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -ExpirationDate "5/30/2020"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

### <a name="remove-allow-or-block-sender-url-or-file-entries-from-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelle Listesinden gönderen, URL veya dosya girdilerine izin verme veya bunları engelleme

Kiracı İzin Ver/Engelle Listesinden gönderen, dosya ve URL girdilerine izin vermek veya bunları engellemek için aşağıdaki söz dizimini kullanın:

```powershell
Remove-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Ids <"Id1","Id2",..."IdN">
```

Bu örnek, belirtilen blok URL'si girişini Kiracı İzin Ver/Engelle Listesinden kaldırır.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSPAAAA0"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).

### <a name="modify-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelle Listesinden sahte gönderen girişlerine izin verme veya engelleme

Kiracı İzin Ver/Engelle Listesi'nde sahte gönderen girişlerine izin vermek veya bunları engellemek için aşağıdaki söz dizimini kullanın:

```powershell
Set-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN"> -Action <Allow | Block>
```

Bu örnek sahte gönderen girdisini izin ver'den engellemeye değiştirir.

```powershell
Set-TenantAllowBlockListItems -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -Action Block
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-TenantAllowBlockListSpoofItems](/powershell/module/exchange/set-tenantallowblocklistspoofitems).

### <a name="remove-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list"></a>Kimlik sahtekarlığına izin veren veya engellenen gönderen girdilerini Kiracı İzin Ver/Engelle Listesinden kaldırma

Kiracı İzin Ver/Engelle Listesinden kimlik sahtekarlığına izin verme veya engelleme girdilerini kaldırmak için aşağıdaki söz dizimini kullanın:

```powershell
Remove-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN">
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-TenantAllowBlockListSpoofItems](/powershell/module/exchange/remove-tenantallowblocklistspoofitems).
