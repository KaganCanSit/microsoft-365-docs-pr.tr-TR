---
title: Kiracı İzin Ver/Engelle Listesinde girdileri değiştirme ve kaldırma
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
description: Yöneticiler, Güvenlik portalında Kiracı İzin Ver/Engelle Listesi'ne girişlerin nasıl değiştir ve kaldırı hakkında bilgi edinebilirsiniz.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f1ab3f815cc64af6d1383df228ef7961c3afdcec
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330195"
---
# <a name="modify-and-remove-entries-in-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelle Listesinde girdileri değiştirme ve kaldırma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Kiracı İzin Ver/Microsoft 365 Defender Listesinde girdileri değiştirmek ve kaldırmak için Microsoft 365 Defender veya PowerShell kullanabilirsiniz.

## <a name="use-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalını kullanma

### <a name="modify-entries-in-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelle Listesinde girdileri değiştirme

1. Microsoft 365 Defender portalında, İlkeler ve kurallar **& Kuralları** \> **Tehdit** \> **İlkeleri** bölümü Kiracı İzin \> Verme **/Engelleme Listeleri'ne gidin**.

2. Değiştirmek istediğiniz girdi türünü içeren sekmeyi seçin:
   - **Gönderenler**
   - **Spoofing**
   - **URL'ler**
   - **Dosyalar**


3. Değiştirmek istediğiniz girdiyi seçin ve Düzenle simgesine ![tıklayın.](../../media/m365-cc-sc-edit-icon.png) **Düzenle'yi seçin**. Görüntülenen açılır sekmede değiştiryebilirsiniz değerler, önceki adımda seçtiğiniz sekmeye bağlıdır:
   - **Gönderenler**
     - **Hiçbir zaman ve** /veya son kullanma tarihi sona ermez.
     - **İsteğe bağlı not**
   - **Spoofing**
     - **Eylem**: Değeri İzin Ver veya Engelle **olarak** **değiştirebilirsiniz**.
   - **URL'ler**
     - **Hiçbir zaman ve** /veya son kullanma tarihi sona ermez.
     - **İsteğe bağlı not**
   - **Dosyalar**
     - **Hiçbir zaman ve** /veya son kullanma tarihi sona ermez.
     - **İsteğe bağlı not**

4. Bitirdiğinizde, **Kaydet**'i tıklatın.

> [!NOTE]
> Oluşturma tarihini takip yalnızca en fazla 30 gün boyunca izin ve ardından 30 gün uzatarak devam  olabilir. Bloklar 90 gün kadar uzatılabilir, ancak izinlerin aksine, süresi hiçbir zaman dolmaacak şekilde de ayarlanır.

### <a name="remove-entries-from-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelleme Listesinden girdileri kaldırma

1. Microsoft 365 Defender portalında, İlkeler ve kurallar **& Kuralları** \> **Tehdit** \> **İlkeleri** bölümü Kiracı İzin \> Verme **/Engelleme Listeleri'ne gidin**.

2. Kaldırmak istediğiniz girdi türünü içeren sekmeyi seçin:
   - **Gönderenler**
   - **Spoofing**
   - **URL'ler**
   - **Dosyalar**
 
3. Kaldırmak istediğiniz girdiyi seçin ve Sil simgesine ![tıklayın.](../../media/m365-cc-sc-delete-icon.png) **Sil'i seçin**.

4. Görüntülenen uyarı iletişim kutusunda Sil'e **tıklayın**.

## <a name="use-powershell"></a>PowerShell kullanma

### <a name="modify-allow-or-block-sender-file-and-url-entries-in-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelle Listesinde gönderene, dosyaya ve URL girdilerine izin verme veya engellemeyi değiştirme

Kiracı İzin Ver/Engelleme Listesi'ne gönderen, dosya ve URL girdilerine izin verme veya bu girdileri engellemek için aşağıdaki söz dizimlerini kullanın:

```powershell
Set-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Ids <"Id1","Id2",..."IdN"> [<-ExpirationDate Date | -NoExpiration>] [-Notes <String>]
```

Bu örnekte, belirtilen URL girişinin son kullanma tarihi değişir.

```powershell
Set-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -ExpirationDate "5/30/2020"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-TenantAllowBlockListItems](/powershell/module/exchange/set-tenantallowblocklistitems).

### <a name="remove-allow-or-block-sender-url-or-file-entries-from-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelle Listesinden gönderene, URL'ye veya dosya girdilerine izin verme veya engellemeyi kaldırma

Kiracı İzin Ver/Engelleme Listesi'ne gönderen, dosya ve URL girdilerine izin verme veya bunları engellemek için aşağıdaki söz dizimlerini kullanın:

```powershell
Remove-TenantAllowBlockListItems -ListType <Sender | FileHash | Url> -Ids <"Id1","Id2",..."IdN">
```

Bu örnek, belirtilen URL engelleme girdisini Kiracı İzin Verme/Engelleme Listesinden kaldırır.

```powershell
Remove-TenantAllowBlockListItems -ListType Url -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSPAAAA0"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Remove-TenantAllowBlockListItems](/powershell/module/exchange/remove-tenantallowblocklistitems).

### <a name="modify-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engellenenler Listesinden kimliği doğru engellenen gönderen girişlerini değiştirme

Kiracı İzin Ver/Engelleme Listesi'ne hatalı gönderen girdilerini değiştirmek veya engellemek için aşağıdaki söz dizimlerini kullanın:

```powershell
Set-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN"> -Action <Allow | Block>
```

Bu örnekte, kimliği doğruya doğru gönderen girdisi engellemeye izin vermiyor.

```powershell
Set-TenantAllowBlockListItems -Ids "RgAAAAAI8gSyI_NmQqzeh-HXJBywBwCqfQNJY8hBTbdlKFkv6BcUAAAl_QCZAACqfQNJY8hBTbdlKFkv6BcUAAAl_oSRAAAA" -Action Block
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-TenantAllowBlockListSpoofItems](/powershell/module/exchange/set-tenantallowblocklistspoofitems).

### <a name="remove-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list"></a>Kiracı İzin Ver/Engelle listesinden kimliği doğru engellenen gönderen girişlerini kaldırma
 
Kiracı İzin Ver/Engelle Listesinden kimliği doğru gönderen girişlerini kaldırmak veya engellemek için aşağıdaki söz dizimlerini kullanın:

```powershell
Remove-TenantAllowBlockListSpoofItems -Ids <"Id1","Id2",..."IdN">
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Remove-TenantAllowBlockListSpoofItems](/powershell/module/exchange/remove-tenantallowblocklistspoofitems).
