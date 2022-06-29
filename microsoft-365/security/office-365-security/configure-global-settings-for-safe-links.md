---
title: Office 365 için Defender'de Güvenli Bağlantılar ayarları için genel ayarları yapılandırma
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Yöneticiler, Office 365 için Microsoft Defender'da Güvenli Bağlantılar için genel ayarları ('Aşağıdaki URL'leri engelle' listesi ve Office 365 uygulamaları için koruma) görüntülemeyi ve yapılandırmayı öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6c8b40109f20215b86a2264ed1a9f69c8db43bda
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66487575"
---
# <a name="configure-global-settings-for-safe-links-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'da Güvenli Bağlantılar için genel ayarları yapılandırma

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Bu makale, [Office 365 için Microsoft Defender](defender-for-office-365.md) sahip iş müşterilerine yöneliktir. Outlook'ta Güvenli Bağlantılar hakkında bilgi arayan bir ev kullanıcısıysanız bkz. [Gelişmiş Outlook.com güvenliği](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Güvenli Bağlantılar[, Office 365 için Microsoft Defender'de](defender-for-office-365.md) gelen e-posta iletilerinin posta akışında URL taraması ve e-posta iletilerinde ve diğer konumlardaki URL'lerin ve bağlantıların tıklamayla doğrulanmasını sağlayan bir özelliktir. Daha fazla bilgi için bkz. [Office 365 için Microsoft Defender'de Güvenli Bağlantılar](safe-links.md).

Güvenli Bağlantılar ayarlarının çoğunu Güvenli Bağlantılar ilkelerinde yapılandırabilirsiniz. Yönergeler için bkz. [Office 365 için Microsoft Defender'de Güvenli Bağlantılar ilkelerini ayarlama](set-up-safe-links-policies.md).

Ancak Güvenli Bağlantılar, Güvenli Bağlantılar ilkelerinin dışında yapılandırdığınız aşağıdaki genel ayarları da kullanır:

- **Aşağıdaki URL'leri engelle** listesi. Bu ayar, etkin Güvenli Bağlantılar ilkelerine dahil olan tüm kullanıcılar için geçerlidir. Daha fazla bilgi için Güvenli [Bağlantılar için "Aşağıdaki URL'leri engelle" listesine](safe-links.md#block-the-following-urls-list-for-safe-links) bakın

- Office 365 uygulamaları için Güvenli Bağlantılar koruması. Bu ayarlar, kullanıcıların etkin Güvenli Bağlantılar ilkelerine dahil edilip edilmediğine bakılmaksızın kuruluştaki Office 365 için Defender lisansına sahip olan tüm kullanıcılar için geçerlidir. Daha fazla bilgi için bkz. [Office 365 uygulamaları için Güvenli Bağlantılar ayarları](safe-links.md#safe-links-settings-for-office-365-apps).

Genel Güvenli Bağlantılar ayarlarını Microsoft 365 Defender portalında veya PowerShell'de (Exchange Online PowerShell'de Exchange Online posta kutuları olan uygun Microsoft 365 kuruluşları için PowerShell'de yapılandırabilirsiniz; Exchange Online olmayan kuruluşlar için tek başına EOP PowerShell posta kutuları, ancak Office 365 için Microsoft Defender eklenti abonelikleri ile).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Varsayılan Güvenli Bağlantılar ilkesi olmasa **da, yerleşik koruma** önceden ayarlanmış güvenlik ilkesi tüm alıcılara (özel Güvenli Bağlantılar ilkelerinde tanımlanmayan kullanıcılar) Güvenli Bağlantılar koruması sağlar. Daha fazla bilgi için bkz. [EOP'de önceden ayarlanmış güvenlik ilkeleri ve Office 365 için Microsoft Defender](preset-security-policies.md). Belirli kullanıcılara, gruplara veya etki alanlarına uygulamak için Güvenli Bağlantılar ilkeleri de oluşturabilirsiniz. Yönergeler için bkz. [Office 365 için Microsoft Defender'de Güvenli Bağlantılar ilkelerini ayarlama](set-up-safe-links-policies.md).

- Microsoft 365 Defender portalını adresinde <https://security.microsoft.com>açarsınız. Doğrudan **Güvenli Bağlantılar** sayfasına gitmek için kullanın <https://security.microsoft.com/safelinksv2>.

- Exchange Online PowerShell'e bağlanmak için bkz[. Exchange Online PowerShell'e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell). Tek başına EOP PowerShell'e bağlanmak için bkz. [Exchange Online Protection PowerShell'e bağlanma](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Bu makaledeki yordamları gerçekleştirebilmeniz için **önce Exchange Online'de** izinlerin atanmış olması gerekir:
  - Güvenli Bağlantılar için genel ayarları yapılandırmak için **Kuruluş Yönetimi** veya **Güvenlik Yöneticisi** rol gruplarının üyesi olmanız gerekir.
  - Güvenli Bağlantılar'ın genel ayarlarına salt okunur erişim için Genel Okuyucu veya **Güvenlik Okuyucusu** rol gruplarının üyesi  olmanız gerekir.

  Daha fazla bilgi için bkz. [Exchange Online'de İzinler](/exchange/permissions-exo/permissions-exo).

  **Notlar**:

  - kullanıcıları Microsoft 365 yönetim merkezi ilgili Azure Active Directory rolüne eklemek, kullanıcılara Microsoft 365'teki diğer özellikler için gerekli izinleri _ve_ izinleri verir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  - [Exchange Online'daki](/Exchange/permissions-exo/permissions-exo#role-groups) **Yalnızca Görüntüleme Kuruluş Yönetimi** rol grubu da özelliğe salt okunur erişim sağlar.

- Güvenli Bağlantılar için genel ayarlar için önerilen değerlerimiz için bkz. [Güvenli Bağlantılar ayarları](recommended-settings-for-eop-and-office365.md#safe-links-settings).

- Yeni veya güncelleştirilmiş bir ilkenin uygulanması için 30 dakikaya kadar bekleyin.

- [Office 365 için Microsoft Defender sürekli olarak yeni özellikler ekleniyor](defender-for-office-365.md#new-features-in-microsoft-defender-for-office-365). Yeni özellikler eklendikçe, mevcut Güvenli Bağlantılar ilkelerinizde ayarlamalar yapmanız gerekebilir.

## <a name="configure-the-block-the-following-urls-list-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında "Aşağıdaki URL'leri engelle" listesini yapılandırın

> [!NOTE]
> Artık [Kiracı İzin Ver/Engelle Listesi'nde](allow-block-urls.md#create-block-url-entries-in-the-tenant-allowblock-list) blok URL'si girdilerini yönetebilirsiniz. "Aşağıdaki URL'leri engelle" listesi kullanım dışı bırakılıyor. Kiracı İzin Ver/Engelle Listesindeki URL girdilerini engellemek için "Aşağıdaki URL'leri engelle" listesinden mevcut girdileri geçirmeyi deneyeceğiz. Engellenen URL'yi içeren iletiler karantinaya alınır.

**Aşağıdaki URL'leri engelle** listesi, desteklenen uygulamalarda Güvenli Bağlantılar taraması tarafından her zaman engellenmesi gereken bağlantıları tanımlar. Daha fazla bilgi [için Güvenli Bağlantılar için "Aşağıdaki URL'leri engelle" listesine](safe-links.md#block-the-following-urls-list-for-safe-links) bakın.

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümündeki **E-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Güvenli Bağlantılar'a** gidin. Doğrudan **Güvenli Bağlantılar** sayfasına gitmek için kullanın <https://security.microsoft.com/safelinksv2>.

2. **Güvenli Bağlantılar** sayfasında **Genel ayarlar'a** tıklayın. **Kuruluşunuzun Güvenli Bağlantılar ilkesinde** görüntülenen açılır öğede **Aşağıdaki URL'leri engelle** kutusuna gidin.

3. ["Aşağıdaki URL'leri engelle" listesi için Giriş söz diziminde](safe-links.md#entry-syntax-for-the-block-the-following-urls-list) açıklandığı gibi bir veya daha fazla girdi yapılandırın.

   Bitirdiğinizde, **Kaydet**'i tıklatın.

### <a name="configure-the-block-the-following-urls-list-in-powershell"></a>PowerShell'de "Aşağıdaki URL'leri engelle" listesini yapılandırma

Giriş söz dizimi hakkında ayrıntılı bilgi için, ["Aşağıdaki URL'leri engelle" listesi için giriş söz dizimine](safe-links.md#entry-syntax-for-the-block-the-following-urls-list) bakın.

_BlockURLs_ özelliğindeki mevcut girişleri görüntülemek için **Get-AtpPolicyForO365** cmdlet'ini kullanabilirsiniz.

- Var olan girdilerin yerini alacak değerler eklemek için PowerShell'Exchange Online veya PowerShell'i Exchange Online Protection aşağıdaki söz dizimini kullanın:

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "Entry1","Entry2",..."EntryN"
  ```

  Bu örnek listeye aşağıdaki girdileri ekler:

  - fabrikam.com için etki alanı, alt etki alanları ve yolları engelleyin.
  - Alt etki alanı araştırmasını engelle, ancak tailspintoys.com'deki üst etki alanını veya diğer alt etki alanını engelleme

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "fabrikam.com","https://research.tailspintoys.com*"
  ```

- Diğer mevcut girişleri etkilemeden değer eklemek veya kaldırmak için aşağıdaki söz dizimini kullanın:

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="Entry1","Entry2"...; Remove="Entry3","Entry4"...}
  ```

  Bu örnek, adatum.com için yeni bir giriş ekler ve fabrikam.com girdisini kaldırır.

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="adatum.com"; Remove="fabrikam"}
  ```

## <a name="configure-safe-links-protection-for-office-365-apps-in-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında Office 365 uygulamalar için Güvenli Bağlantılar korumasını yapılandırma

Office 365 uygulamaları için Güvenli Bağlantılar koruması, desteklenen Office masaüstü, mobil ve web uygulamalarındaki belgeler için geçerlidir. Daha fazla bilgi için bkz. [Office 365 uygulamaları için Güvenli Bağlantılar ayarları](safe-links.md#safe-links-settings-for-office-365-apps).

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümündeki **E-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Güvenli Bağlantılar'a** gidin. Doğrudan **Güvenli Bağlantılar** sayfasına gitmek için kullanın <https://security.microsoft.com/safelinksv2>.

2. **Güvenli Bağlantılar** sayfasında **Genel ayarlar'a** tıklayın. **Kuruluşunuz için Güvenli Bağlantılar ilkesi** açılır penceresinde, **desteklenen Office 365 uygulamalarındaki içeriğe uygulanan ayarlar** bölümünde aşağıdaki ayarları yapılandırın:

   - **Office 365 uygulamalarında Güvenli Bağlantılar'ı kullanma**: Desteklenen Office 365 uygulamaları için Güvenli Bağlantılar'ı etkinleştirmek için iki durumlu düğmenin sağ tarafta olduğunu doğrulayın: ![Açık..](../../media/scc-toggle-on.png).

   - **Kullanıcıların Office 365 uygulamalarda korumalı bağlantılara ne zaman tıkladığını izlemeyin**: Desteklenen Office 365 uygulamalarında engellenen URL'lerle ilgili kullanıcı tıklamalarını izlemek için iki durumlu düğmeyi sola taşıyın: ![Geçiş kapat.](../../media/scc-toggle-off.png).

   - **Kullanıcıların Office 365 uygulamalarda özgün URL'ye tıklamasına izin verme**: Kullanıcıların desteklenen Office 365 uygulamalarında engellenen özgün URL'ye tıklamasını önlemek için iki durumlu düğmenin sağ tarafta olduğunu doğrulayın: ![Açık..](../../media/scc-toggle-on.png).

   Bitirdiğinizde, **Kaydet**'i tıklatın.

### <a name="configure-safe-links-protection-for-office-365-apps-in-powershell"></a>PowerShell'de Office 365 uygulamaları için Güvenli Bağlantılar korumasını yapılandırma

Office 365 uygulamalar için Güvenli Bağlantılar korumasını yapılandırmak için PowerShell'i kullanmayı tercih ediyorsanız, PowerShell'Exchange Online veya PowerShell'i Exchange Online Protection aşağıdaki söz dizimini kullanın:

```powershell
Set-AtpPolicyForO365 [-EnableSafeLinksForO365Clients <$true | $false> [-AllowClickThrough <$true | $false>] [-TrackClicks <$true | $false>]
```

Bu örnekte, Office 365 uygulamalarında Güvenli Bağlantılar koruması için aşağıdaki ayarlar yapılandırılır:

- Office 365 uygulamaları için Güvenli Bağlantılar açık (_EnableSafeLinksForO365Clients_ parametresini kullanmıyoruz ve varsayılan değer $true).
- Desteklenen Office 365 uygulamalarda engellenen URL'lerle ilgili kullanıcı tıklamaları izlenir.
- Desteklenen Office 365 uygulamalarında kullanıcıların özgün engellenen URL'ye tıklamasına izin verilmez (_AllowClickThrough_ parametresini kullanmıyoruz ve varsayılan değer $false).

```powershell
Set-AtpPolicyForO365 -TrackClicks $true
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

## <a name="how-do-you-know-these-procedures-worked"></a>Bu yordamların işe yaramış olduğunu nasıl anlarsınız?

Güvenli Bağlantılar için genel ayarları başarıyla yapılandırdığınızdan emin olmak için (**Aşağıdaki URL'leri engelle** listesi ve Office 365 uygulama koruma ayarları), aşağıdaki adımlardan herhangi birini yapın:

- konumundaki Microsoft 365 Defender portalındaki <https://security.microsoft.com/safelinksv2>**Güvenli Bağlantılar** sayfasında **Genel ayarlar'a** tıklayın ve görüntülenen açılır listede ayarları doğrulayın.

- PowerShell Exchange Online veya PowerShell Exchange Online Protection aşağıdaki komutu çalıştırın ve ayarları doğrulayın:

  ```powershell
  Get-AtpPolicyForO365 | Format-List BlockUrls,EnableSafeLinksForO365Clients,AllowClickThrough,TrackClicks
  ```

  Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-AtpPolicyForO365](/powershell/module/exchange/get-atppolicyforo365).
