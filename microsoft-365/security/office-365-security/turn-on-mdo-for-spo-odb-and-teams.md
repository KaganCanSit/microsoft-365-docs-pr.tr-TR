---
title: E-Kasa, E-posta SharePoint, OneDrive için Ekleri Açma Microsoft Teams
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 07e76024-0c80-40dc-8c48-1dd0d0f863cb
ms.collection:
- M365-security-compliance
- SPO_Content
description: Yöneticiler, algılanan dosyalar için uyarılar ayarlama Kasa da içinde olmak üzere, SharePoint, OneDrive ve Microsoft Teams için Ekleri nasıl açabilirsiniz?
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 6501097251f4001c58a651db7ddb34bc623e9b0a
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021690"
---
# <a name="turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>E-Kasa, E-posta SharePoint, OneDrive için Ekleri Açma Microsoft Teams

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

SharePoint, Office 365 OneDrive ve Microsoft Teams için Microsoft Defender Microsoft Teams, kötü amaçlı dosyaları istemeden paylaşmaya karşı korur. Daha fazla bilgi için bkz[. Kasa, Dosya ve SharePoint OneDrive Ekleri'Microsoft Teams](mdo-for-spo-odb-and-teams.md).

Bu makalede, E-posta, Otomatik Bağlantı ve Diğer Kasa Ekleri SharePoint OneDrive ve yapılandırma Microsoft Teams.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açın<https://security.microsoft.com>. Doğrudan Ekler sayfasına **Kasa için**, kullanın<https://security.microsoft.com/safeattachmentv2>.

- SharePoint, OneDrive ve Microsoft Teams eklerini açmak için, Microsoft 365 Defender portalında Kuruluş Yönetimi veya Güvenlik Yöneticisi rol gruplarının üyesi Microsoft 365 Defender gerekir. Kasa   Daha fazla bilgi için bkz[. Microsoft 365 Defender portalına.](permissions-microsoft-365-security-center.md)

- Kişilerin kötü amaçlı dosyaları SharePoint için SharePoint Online PowerShell'i kullanmak için, Genel Yönetici'ye veya Azure AD'de [SharePoint](/azure/active-directory/roles/permissions-reference#sharepoint-administrator) Yönetici rollerine üye olun.[](/azure/active-directory/roles/permissions-reference#global-administrator)

- Kuruluşta denetim günlüğünün etkinleştirildiğinden emin olun. Daha fazla bilgi için bkz [. Denetim günlüğü aramalarını açma veya kapatma](../../compliance/turn-audit-log-search-on-or-off.md).

- Ayarların etkili olmasına 30 dakika kadar bekleyin.

## <a name="step-1-use-the-microsoft-365-defender-portal-to-turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>1. Adım: Microsoft 365 Defender, E-posta ve Kasa Ekleri'SharePoint için OneDrive portalını Microsoft Teams

1. aşağıdaki Microsoft 365 Defender portalında İlkeler ve <https://security.microsoft.com>kurallar **& Ahd** \>  \> Kasa **İlkeler** **bölümüne** gidin. Doğrudan Ekler sayfasına **Kasa için**, kullanın<https://security.microsoft.com/safeattachmentv2>.

2. Ekler **sayfasında Kasa ayarlar'a** **tıklayın**.

3. Görüntülenen **Genel ayarlar** açılır sayfasında Dosya, Dosya ve Dosya **SharePoint'de OneDrive bölümüne Microsoft Teams** gidin.

   Office 365 **, OneDrive için SharePoint Defender** Office 365 ve Microsoft Teams iki durumlu düğmeyi ![açık olarak hareket ettirin.](../../media/scc-toggle-on.png) SharePoint, OneDrive için Kasa'i açmak Microsoft Teams.

   Bitirdiğinizde, **Kaydet**'i tıklatın.

### <a name="use-exchange-online-powershell-to-turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Exchange Online, OneDrive ve diğer Kasa Ekleri açmak için SharePoint PowerShell'i Microsoft Teams

SharePoint, OneDrive ve Microsoft Teams için Kasa Eklerini açmak için PowerShell kullanmayı tercih ediyorsanız, [Exchange Online PowerShell'e](/powershell/exchange/connect-to-exchange-online-powershell) bağlanın ve aşağıdaki komutu çalıştırın:

```powershell
Set-AtpPolicyForO365 -EnableATPForSPOTeamsODB $true
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

## <a name="step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files"></a>2. Adım: (Önerilen) Kullanıcıların kötü amaçlı dosyaları SharePoint için SharePoint Online PowerShell'i kullanma

Varsayılan olarak,<sup>\*</sup> kullanıcılar SharePoint, OneDrive ve diğer dosya ekleri ile algılanan kötü amaçlı dosyaları Kasa dosya aç SharePoint, OneDrive veya Microsoft Teams. Ancak, kötü amaçlı dosyaları silebilir ve indirebilirler.

<sup>\*</sup>Kullanıcılar Erişimi **yönet'e giderse****, Paylaş** seçeneği yine kullanılabilir.

Kullanıcıların kötü amaçlı dosyaları indirmesini önlemek için SharePoint [Online PowerShell'e bağlanın](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) ve aşağıdaki komutu çalıştırın:

```powershell
Set-SPOTenant -DisallowInfectedFileDownload $true
```

**Notlar**:

- Bu ayar hem kullanıcıları hem de yöneticileri etkiler.
- Kişiler, kötü amaçlı dosyaları silebilir.

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. SPOTenant Ayarlama](/powershell/module/sharepoint-online/Set-SPOTenant).

## <a name="step-3-recommended-use-the-microsoft-365-defender-portal-to-create-an-alert-policy-for-detected-files"></a>3. Adım (Önerilen) Microsoft 365 Defender dosyalar için uyarı ilkesi oluşturmak üzere Bu Portal'a

SharePoint, OneDrive ve bir kötü amaçlı dosya algılayana kadar Kasa yöneticilere ve size SharePoint Microsoft Teams bir uyarı ilkesi oluşturabilirsiniz. Uyarılar hakkında daha fazla bilgi edinmek için bkz. [Uyarı ilkeleri](../../compliance/alert-policies.md).

1. Aşağıdaki Microsoft 365 Defender portalında İlkeler <https://security.microsoft.com>ve **Kurallar &** **ilkesi'ne**\> gidin. Doğrudan Uyarı ilkesi **sayfasına gitmek için** kullanın <https://security.microsoft.com/alertpolicies>.

2. Uyarı ilkesi **sayfasında Yeni** uyarı **ilkesi'ne tıklayın**.

3. Yeni **uyarı ilkesi** sihirbazı açılır. Uyarınızı **adla** sayfasında aşağıdaki ayarları yapılandırabilirsiniz:
   - **Ad**: Benzersiz ve açıklayıcı bir ad yazın. Örneğin, Kitaplıklarda Kötü Amaçlı Dosyalar.
   - **Açıklama**: İsteğe bağlı bir açıklama yazın. Örneğin, SharePoint Online, OneDrive veya başka dosyalarda kötü amaçlı dosyalar algılandığında yöneticilere Microsoft Teams.
   - **Önem Derecesi**: Açılan **listeden** **Düşük**, Orta **veya Yüksek'i** seçin.
   - **Kategori**: Açılan **listeden Tehdit** yönetimi'ne tıklayın.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

4. Uyarı **ayarları oluştur sayfasında** aşağıdaki ayarları yapılandırabilirsiniz:
   - **Ne hakkında uyarı almaksınız?** Bölüm \> **: Açılan** \> listeden **Dosyada kötü amaçlı yazılım algılandı** öğesini seçin.
   - **Uyarının nasıl tetiklenir?** bölüm: Bir etkinlik **kuralla her eş olduğunda varsayılan değeri seçili** olarak bırakın.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

5. Alıcılarınızı **ayarlayın sayfasında** aşağıdaki ayarları yapılandırabilirsiniz:
   - **E-posta bildirimlerini gönder'in seçili** olduğunu doğrulayın. **E-posta alıcıları kutusunda**, kötü amaçlı bir dosya algılandığında bildirim alacak bir veya birden çok genel yönetici, güvenlik yöneticisi veya güvenlik okuyucusu seçin.
   - **Günlük bildirim sınırı**: Varsayılan Sınır yok **değerini seçili** bırakın.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

6. Ayarlarınızı **gözden geçirme sayfasında** , ayarlarınızı gözden geçirebilirsiniz. Bölümün içindeki **ayarları değiştirmek** için her bölümde Düzenle'yi seçebilirsiniz. Geri'ye **tıklar** veya sihirbazda belirli bir sayfayı seçersiniz.

   **İlkeyi hemen açmak istiyor musunuz?** bölümünde, varsayılan Evet **değerini bırakın, hemen aç'a** tıklayın.

   Bitirdikten sonra Son'a **tıklayın**.

### <a name="use-security--compliance-powershell-to-create-an-alert-policy-for-detected-files"></a>Algılanan dosyalar & için uyarı ilkesi oluşturmak için Güvenlik ve Uyumluluk PowerShell kullanma

Önceki bölümde açıklanan uyarı ilkesiyle aynı uyarı ilkesi oluşturmak için PowerShell kullanmayı tercih ediyorsanız, Güvenlik ve Uyumluluk Merkezi [PowerShell'e &](/powershell/exchange/connect-to-scc-powershell) komutu çalıştırın:

```powershell
New-ActivityAlert -Name "Malicious Files in Libraries" -Description "Notifies admins when malicious files are detected in SharePoint Online, OneDrive, or Microsoft Teams" -Category ThreatManagement -Operation FileMalwareDetected -NotifyUser "admin1@contoso.com","admin2@contoso.com"
```

**Not**: Varsayılan _Önem Derecesi değeri_ Düşüktür. Orta veya Yüksek değerini belirtmek için, _komuta Önem Derecesi_ parametresini ve değerini yazın.

Ayrıntılı söz dizimi ve parametre bilgileri için [bkz. New-ActivityAlert](/powershell/module/exchange/new-activityalert).

### <a name="how-do-you-know-these-procedures-worked"></a>Bu yordamların çalıştığını nasıl biliyorsunuz?

- SharePoint, OneDrive ve Kasa Ekleri'Microsoft Teams başarıyla açık olduğunu doğrulamak için, aşağıdaki adımlardan birini kullanın:

  - Microsoft 365 Defender portalında   **İlkeler &** \> \> \> kuralları Tehdit İlkeleri **bölümüne Kasa** Ekleri'ne gidin, Genel ayarlar'ı seçin ve SharePoint için Office 365 için **Defender'ı Aç seçeneğinin OneDrive ve Microsoft Teams** seçin.

  - PowerShell Exchange Online, özellik ayarını doğrulamak için aşağıdaki komutu çalıştırın:

    ```powershell
    Get-AtpPolicyForO365 | Format-List EnableATPForSPOTeamsODB
    ```

    Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-AtpPolicyForO365](/powershell/module/exchange/get-atppolicyforo365).

- Kişilerin kötü amaçlı dosyaları indirmesi başarıyla engellenmiş olduğunu doğrulamak için, SharePoint Online PowerShell'i açın ve özellik değerini doğrulamak için aşağıdaki komutu çalıştırın:

  ```powershell
  Get-SPOTenant | Format-List DisallowInfectedFileDownload
  ```

  Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Get-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant).

- Algılanan dosyalar için bir uyarı ilkesi başarıyla yapılandırıldığından emin olmak için, aşağıdaki adımlardan herhangi birini kullanın:
  - Microsoft 365 Defender portalında İlkeler **ve kurallar & Uyarı** \> **ilkesi'ne** \> gidin ve ayarları doğrulayın.
  - Uygulama Microsoft 365 Defender PowerShell'de\<AlertPolicyName\>, uyarı ilkesi adıyla değiştirin, aşağıdaki komutu çalıştırın ve özellik değerlerini doğrulayın:

    ```powershell
    Get-ActivityAlert -Identity "<AlertPolicyName>"
    ```

    Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-ActivityAlert](/powershell/module/exchange/get-activityalert).

- Tehdit koruması [durum raporunu kullanarak dosyalarda](view-email-security-reports.md#threat-protection-status-report), dosyalarda veya dosyalarda SharePoint OneDrive bilgileri Microsoft Teams. Özel olarak, Verileri görüntüleme: **İçerik Kötü Amaçlı Yazılım görünümü'ne göre \> kullanabilirsiniz** .
