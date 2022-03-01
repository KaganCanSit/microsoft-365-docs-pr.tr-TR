---
title: Web için Defender'Kasa Bağlantılar ayarları için genel ayarları Office 365
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
description: Yöneticiler, Office 365 için Microsoft Defender'da Bağlantılara genel ayarları görüntülemeyi ve yapılandırmayı (Office 365 uygulamaları için 'Aşağıdaki URL'leri engelle' listesi ve Kasa koruma) hakkında bilgi Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 857519e93df9490ebeb178a23a44ddddbdfc83ef
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021696"
---
# <a name="configure-global-settings-for-safe-links-in-microsoft-defender-for-office-365"></a>Web için Microsoft Defender'Kasa Bağlantılar için genel ayarları Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> Bu makale, Microsoft [Defender'a sahip iş müşterileri için Office 365](defender-for-office-365.md). Bu bağlantılarda Safelink'ler hakkında bilgi arayan bir ev kullanıcısı Outlook[, bkz. Gelişmiş Outlook.com güvenliği](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

Kasa Bağlantıları[, Office 365 için Microsoft Defender'ın](defender-for-office-365.md) posta akışında gelen e-posta iletilerinin URL'sini tarama ve e-posta iletileriyle diğer konumlarda URL'leri ve bağlantıları tıklatma zamanlarını tarama özelliğini sağlayan bir özelliktir. Daha fazla bilgi için bkz. [Kasa için Microsoft Defender'daki Office 365](safe-links.md).

Bağlantılar ilkeleri'Kasa bağlantılar ayarlarının çoğunu Kasa yapılandırabilirsiniz. Yönergeler için bkz[. Kasa Office 365 için Microsoft Defender'da Bağlantılar Office 365](set-up-safe-links-policies.md).

Ancak, Kasa Bağlantılar, bağlantıların kendileri dışında yapılandırılan aşağıdaki genel Kasa kullanır:

- Aşağıdaki **URL'leri engelle** listesi. Bu ayar, tüm etkin kullanıcılara yöneliktir ve Bağlantılar Kasa uygulanır. Daha fazla bilgi için, [Bu Bağlantılar için "Aşağıdaki URL'leri engelleme" Kasa bakın](safe-links.md#block-the-following-urls-list-for-safe-links)
- Kasa için Bağlantılar Office 365 seçin. Bu ayarlar, kullanıcıların Etkin Bağlantılar ilkelerine dahil olup olmadığına bakılmaksızın, Office 365 için Defender lisansına sahip olan tüm Kasa uygulanır. Daha fazla bilgi için bkz[. Kasa uygulamaları için bağlantılar Office 365 bakın](safe-links.md#safe-links-settings-for-office-365-apps).

Microsoft 365 Defender portalında veya PowerShell'de (Exchange Online PowerShell Kasa posta kutuları olan uygun Microsoft 365 kuruluşları için Exchange Online; kuruluşlar için tek başına EOP PowerShell'de genel Kasa Bağlantıları ayarlarını yapılandırabilirsiniz Exchange Online kutuları olmadan, ancak Diğer eklentiler için Microsoft Defender Office 365 a sahip olun).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Varsayılan Bağlantı ilkesi Kasa, yerleşik koruma önceden ayarlanmış güvenlik ilkesi tüm alıcılara  Kasa Bağlantıları koruması sağlar (özel Bağlantılar ilkeleri içinde tanımlanmamış kullanıcılar Kasa). Daha fazla bilgi için bkz[. İlke için EOP'de ve Microsoft Defender'da önceden Office 365](preset-security-policies.md). Belirli kullanıcılara, Kasa etki alanlarına uygulanacak bağlantılar ilkeleri de oluşturabilirsiniz. Yönergeler için bkz[. Kasa Office 365 için Microsoft Defender'da Bağlantılar Office 365](set-up-safe-links-policies.md).

- Microsoft 365 Defender portalını açın<https://security.microsoft.com>. Doğrudan Bağlantılar sayfasına **Kasa için**, kullanın<https://security.microsoft.com/safelinksv2>.

- Exchange Online PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online e bağlama](/powershell/exchange/connect-to-exchange-online-powershell). Tek başına EOP PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online Protection e bağlama](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Bu makaledeki yordamları **yerine Exchange Online** önce Bu makalede izinlerin atanmamış olması gerekir:
  - Yardım Bağlantıları'nın genel Kasa yapılandırmak için, Kuruluş Yönetimi veya Güvenlik Yöneticisi rol **gruplarının üyesi olun**.
  - Genel Sayfa Bağlantıları'nın genel ayarlarına salt okunur Kasa için, Genel Okuyucu veya Güvenlik **Okuyucusu rol** **gruplarının üyesi** olun.

  Daha fazla bilgi için bkz. [Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Notlar**:

  - Görev sırasında ilgili kullanıcı Azure Active Directory eklemek Microsoft 365 yönetim merkezi kullanıcılara çalışma sayfalarındaki diğer özellikler için gerekli izinleri ve izinleri Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  - **Görünüm'de Yalnızca Görüntüleme** [kuruluş Exchange Online rol](/Exchange/permissions-exo/permissions-exo#role-groups) grubu, özel salt okunur erişim de sağlar.

- Bağlantılar'a genel ayarlar için önerilen değerlerimiz Kasa bağlantı [ayarları'Kasa bakın](recommended-settings-for-eop-and-office365.md#safe-links-settings).

- Yeni veya güncelleştirilmiş ilkenin uygulanması için 30 dakika kadar bekleyin.

- [İş için Microsoft Defender'a sürekli yeni özellikler Office 365](defender-for-office-365.md#new-features-in-microsoft-defender-for-office-365). Yeni özellikler eklendiklerine göre, mevcut Özellikler ve Bağlantılar ilkeleriniz için Kasa gerekir.

## <a name="configure-the-block-the-following-urls-list-in-the-microsoft-365-defender-portal"></a>Portalda "Aşağıdaki URL'leri engelle" listesini Microsoft 365 Defender yapılandırma

Aşağıdaki **URL'leri engelle** listesi, desteklenen uygulamalarda bağlantılar tarama her zaman Kasa bağlantıları tanımlar. Daha fazla bilgi için, [Bu Bağlantılar için "Aşağıdaki URL'leri engelleme" Kasa bakın](safe-links.md#block-the-following-urls-list-for-safe-links).

1. aşağıdaki Microsoft 365 Defender portalında, <https://security.microsoft.com>İlkeler bölümündeki **&** \> İşbirliği **İlkeleri** ve & kuralları \>  \> Tehdit **Kasa'ne** gidin. Doğrudan Bağlantılar sayfasına **Kasa için**, kullanın<https://security.microsoft.com/safelinksv2>.

2. Bağlantılar Kasa **Genel** **ayarlar'a tıklayın**. Görüntülenen **Kasa Bağlantılar ilkesi** açılır kutusunda Aşağıdaki URL'leri **engelle kutusuna** gidin.

3. "Aşağıdaki URL'leri engelle [" listesi için Giriş söz dizim altında açıklandığı gibi bir veya birden çok girdiyi yapılandırabilirsiniz](safe-links.md#entry-syntax-for-the-block-the-following-urls-list).

   Bitirdiğinizde, **Kaydet**'i tıklatın.

### <a name="configure-the-block-the-following-urls-list-in-powershell"></a>PowerShell'de "Aşağıdaki URL'leri engelle" listesini yapılandırma

Girdi söz dizimi hakkında ayrıntılı bilgi için bkz. ["Aşağıdaki URL'leri engelle" listesi için giriş söz dizimi](safe-links.md#entry-syntax-for-the-block-the-following-urls-list).

BlockURLs özelliğinde var olan **girdileri görüntülemek için Get-AtpPolicyForO365** cmdlet'ini _kullanabilirsiniz_ .

- Var olan tüm girdilerin yerini alacak değerleri eklemek için, PowerShell veya Exchange Online PowerShell'Exchange Online Protection kullanın:

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "Entry1","Entry2",..."EntryN"
  ```

  Bu örnekte, listeye aşağıdaki girdiler eklenir:

  - Etki alanı, alt etki alanları ve etki alanlarıyla ilgili yolları fabrikam.com.
  - Çalışma alanında alt etki alanı araştırmasını engelle ancak üst etki alanını veya diğer alt etki tailspintoys.com

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls "fabrikam.com","https://research.tailspintoys.com*"
  ```

- Var olan diğer girdileri etkilemeden değer eklemek veya kaldırmak için, aşağıdaki söz dizimi kullanın:

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="Entry1","Entry2"...; Remove="Entry3","Entry4"...}
  ```

  Bu örnekte, bu belge için yeni adatum.com ve bu girdinin fabrikam.com.

  ```powershell
  Set-AtpPolicyForO365 -BlockUrls @{Add="adatum.com"; Remove="fabrikam"}
  ```

## <a name="configure-safe-links-protection-for-office-365-apps-in-the-microsoft-365-defender-portal"></a>Web Kasa içinde yer alan Office 365 için Bağlantılar korumasını Microsoft 365 Defender yapılandırma

Kasa uygulamaları için bağlantılar Office 365 koruması desteklenen masaüstü, Office ve web uygulamaları uygulamaları için geçerlidir. Daha fazla bilgi için bkz[. Kasa uygulamaları için bağlantılar Office 365 bakın](safe-links.md#safe-links-settings-for-office-365-apps).

1. aşağıdaki Microsoft 365 Defender portalında, <https://security.microsoft.com>İlkeler bölümündeki **&** \> İşbirliği **İlkeleri** ve & kuralları \>  \> Tehdit **Kasa'ne** gidin. Doğrudan Bağlantılar sayfasına **Kasa için**, kullanın<https://security.microsoft.com/safelinksv2>.

2. Bağlantılar Kasa **Genel** **ayarlar'a tıklayın**. Görüntülenen **Kasa Bağlantılar** ilkesi açılır sayfasında, desteklenen Ayarlar uygulamaları bölümündeki içeriğe **uygulanacak aşağıdaki Office 365 yapılandırabilirsiniz**:

   - **Office 365 Kasa'de** Bağlantılar'ı kullanın: Desteklenen Kasa Office 365 uygulamaları için bağlantılar: Kasa etkinleştirmek için iki durumlu düğmenin sağ tarafta olduğunu doğrulayın: ![Açık.](../../media/scc-toggle-on.png)

   - **Kullanıcılar Office 365** uygulamaları içinde korumalı bağlantılara tıkladığında izleme: Desteklenen Office 365 uygulamaları altındaki engellenen URL'lerle ilgili kullanıcı tıklamalarını izlemek için iki durumlu düğmeyi sola Office 365: ![Kapat.](../../media/scc-toggle-off.png).

   - **Kullanıcıların Office 365** uygulamaları içinde özgün URL'ye tıklamalarına izin verme: Desteklenen Office 365 uygulamaları: Geçiş.'te, kullanıcıların engellenen özgün URL'ye ![](../../media/scc-toggle-on.png)tıklamalarını engellemek için iki durumlu düğmenin sağ tarafta olduğunu doğrulayın.

   Bitirdiğinizde, **Kaydet**'i tıklatın.

### <a name="configure-safe-links-protection-for-office-365-apps-in-powershell"></a>PowerShell Kasa uygulamalarınızı Office 365 Bağlantılar korumasını yapılandırma

Office 365 uygulamaları için Kasa Bağlantıları korumasını yapılandırmak için PowerShell kullanmayı tercih ediyorsanız, Exchange Online PowerShell veya Exchange Online Protection kullanın:

```powershell
Set-AtpPolicyForO365 [-EnableSafeLinksForO365Clients <$true | $false> [-AllowClickThrough <$true | $false>] [-TrackClicks <$true | $false>]
```

Bu örnekte, bir uygulamanın Bağlantılar Kasa için aşağıdaki Office 365 yapılandırılır:

- Kasa Office 365 için bağlantılar açık olmalıdır (_EnableSafeLinksForO365Clients_ parametresi kullanacağız ve varsayılan değer $true).
- Kullanıcı desteklenen sitelerde engellenen URL'lerle ilgili Office 365 tıkladığında.
- Kullanıcıların desteklenen Office 365 uygulamalarında engellenen özgün URL'ye tıklamalarına izin verilmez (_AllowClickThrough_ parametresi kullanacağız ve varsayılan değer $false).

```powershell
Set-AtpPolicyForO365 -TrackClicks $true
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

## <a name="how-do-you-know-these-procedures-worked"></a>Bu yordamların çalıştığını nasıl biliyorsunuz?

Kasa Bağlantıları'nın genel ayarlarını başarıyla yapılandırmış olduğunu doğrulamak için (Aşağıdaki URL'leri engelleme  listesi ve Office 365 koruma ayarları) aşağıdaki adımlardan herhangi birini yapın:

- Web **Kasa '** daki Microsoft 365 Defender <https://security.microsoft.com/safelinksv2>Bağlantılar **sayfasında Genel** ayarlar'a tıklayın ve beliren açılır sayfada ayarları doğrulayın.

- PowerShell Exchange Online powershell Exchange Online Protection'te, aşağıdaki komutu çalıştırın ve ayarları doğrulayın:

  ```powershell
  Get-AtpPolicyForO365 | Format-List BlockUrls,EnableSafeLinksForO365Clients,AllowClickThrough,TrackClicks
  ```

  Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-AtpPolicyForO365](/powershell/module/exchange/get-atppolicyforo365).
