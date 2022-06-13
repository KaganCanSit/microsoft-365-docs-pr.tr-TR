---
title: SharePoint, OneDrive ve Microsoft Teams için Güvenli Ekleri açma
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
description: Yöneticiler, algılanan dosyalar için uyarı ayarlama da dahil olmak üzere SharePoint, OneDrive ve Microsoft Teams için Kasa Eklerini açmayı öğrenebilir.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 55923b13cf47e0309a7246ba43dcb9adaf3c58ff
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016020"
---
# <a name="turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>SharePoint, OneDrive ve Microsoft Teams için Güvenli Ekleri açma

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

SharePoint, OneDrive ve Microsoft Teams için Office 365 için Microsoft Defender, kuruluşunuzu yanlışlıkla kötü amaçlı dosyaları paylaşmaya karşı korur. Daha fazla bilgi için bkz[. SharePoint, OneDrive ve Microsoft Teams için ekleri Kasa](mdo-for-spo-odb-and-teams.md).

Bu makale SharePoint, OneDrive ve Microsoft Teams için Kasa Eklerini etkinleştirme ve yapılandırma adımlarını içerir.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını adresinde <https://security.microsoft.com>açarsınız. **Doğrudan Kasa Ekler** sayfasına gitmek için kullanın<https://security.microsoft.com/safeattachmentv2>.

- SharePoint, OneDrive ve Microsoft Teams için Kasa Eklerini açmak için, Microsoft 365 Defender portalında **Kuruluş Yönetimi** veya **Güvenlik Yöneticisi** rol gruplarının üyesi olmanız gerekir. Daha fazla bilgi için bkz. [Microsoft 365 Defender portalında İzinler](permissions-microsoft-365-security-center.md).

- kişilerin kötü amaçlı dosyaları indirmesini önlemek için SharePoint Online PowerShell kullanmak için, Azure AD'da [Genel Yönetici](/azure/active-directory/roles/permissions-reference#global-administrator) veya [SharePoint Yöneticisi](/azure/active-directory/roles/permissions-reference#sharepoint-administrator) rollerinin üyesi olmanız gerekir.

- Kuruluşunuz için denetim günlüğünün etkinleştirildiğini doğrulayın. Daha fazla bilgi için bkz [. Denetim günlüğü aramasını açma veya kapatma](../../compliance/turn-audit-log-search-on-or-off.md).

- Ayarların geçerlilik kazanması için 30 dakikaya kadar bekleyin.

## <a name="step-1-use-the-microsoft-365-defender-portal-to-turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>1. Adım: SharePoint, OneDrive ve Microsoft Teams için Kasa Eklerini açmak için Microsoft 365 Defender portalını kullanın

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**İlkeler & kuralları** \> **Tehdit ilkeleri** \> **Kasa İlkeler** **bölümündeki** Ekler'e gidin. **Doğrudan Kasa Ekler** sayfasına gitmek için kullanın<https://security.microsoft.com/safeattachmentv2>.

2. **Kasa Ekler** sayfasında **Genel ayarlar'a** tıklayın.

3. Görüntülenen **Genel ayarlar** açılır penceresinde SharePoint **, OneDrive ve Microsoft Teams dosyaları koruma** bölümüne gidin.

   **SharePoint, OneDrive ve Microsoft Teams için Office 365 için Defender aç** iki durumlu düğmesini sağ ![Geçiş açık konuma getirin.](../../media/scc-toggle-on.png) SharePoint, OneDrive ve Microsoft Teams için Kasa Eklerini açmak için.

   Bitirdiğinizde, **Kaydet**'i tıklatın.

### <a name="use-exchange-online-powershell-to-turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>SharePoint, OneDrive ve Microsoft Teams için Kasa Eklerini açmak için Exchange Online PowerShell'i kullanın

SharePoint, OneDrive ve Microsoft Teams için Kasa Eklerini açmak için PowerShell'i kullanmayı tercih ederseniz, [powershell'Exchange Online bağlanın](/powershell/exchange/connect-to-exchange-online-powershell) ve aşağıdaki komutu çalıştırın:

```powershell
Set-AtpPolicyForO365 -EnableATPForSPOTeamsODB $true
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

## <a name="step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files"></a>2. Adım: (Önerilen) Kullanıcıların kötü amaçlı dosyaları indirmesini önlemek için çevrimiçi SharePoint PowerShell kullanın

Varsayılan olarak, kullanıcılar SharePoint, OneDrive ve Microsoft Teams için Kasa Ekleri tarafından algılanan kötü amaçlı dosyaları açamaz, taşıyamaz, kopyalayamaz veya paylaşamaz<sup>\*</sup>. Ancak, kötü amaçlı dosyaları silebilir ve indirebilirler.

<sup>\*</sup> Kullanıcılar **Erişimi yönet'e** giderse **Paylaş** seçeneği hala kullanılabilir durumdadır.

Kullanıcıların kötü amaçlı dosyaları indirmesini önlemek [için SharePoint Online PowerShell'e bağlanın](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) ve aşağıdaki komutu çalıştırın:

```powershell
Set-SPOTenant -DisallowInfectedFileDownload $true
```

**Notlar**:

- Bu ayar hem kullanıcıları hem de yöneticileri etkiler.
- Kişiler kötü amaçlı dosyaları silmeye devam edebilir.

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant).

## <a name="step-3-recommended-use-the-microsoft-365-defender-portal-to-create-an-alert-policy-for-detected-files"></a>3. Adım (Önerilen) Algılanan dosyalar için uyarı ilkesi oluşturmak üzere Microsoft 365 Defender portalını kullanma

SharePoint, OneDrive ve Microsoft Teams için Ekleri Kasa kötü amaçlı bir dosya algıladığında sizi ve diğer yöneticileri bilgilendiren bir uyarı ilkesi oluşturabilirsiniz. Uyarılar hakkında daha fazla bilgi edinmek için bkz. [Uyarı ilkeleri](../../compliance/alert-policies.md).

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**İlkeler & kuralları** \> **Uyarı ilkesi'ne** gidin. **Doğrudan Uyarı ilkesi** sayfasına gitmek için kullanın<https://security.microsoft.com/alertpolicies>.

2. **Uyarı ilkesi** sayfasında **Yeni uyarı ilkesi'ne** tıklayın.

3. **Yeni uyarı ilkesi** sihirbazı açılır. **Uyarınızı adlandırın** sayfasında aşağıdaki ayarları yapılandırın:
   - **Ad**: Benzersiz ve açıklayıcı bir ad yazın. Örneğin, Kitaplıklardaki Kötü Amaçlı Dosyalar.
   - **Açıklama**: İsteğe bağlı bir açıklama yazın. Örneğin, SharePoint Online, OneDrive veya Microsoft Teams'da kötü amaçlı dosyalar algılandığında yöneticileri bilgilendirin.
   - **Önem Derecesi**: Açılan listeden **Düşük**, **Orta** veya **Yüksek'i** seçin.
   - **Kategori**: Açılan listeden **Tehdit yönetimi'ni** seçin.

   İşiniz bittiğinde **İleri'ye** tıklayın.

4. **Uyarı ayarları oluştur** sayfasında aşağıdaki ayarları yapılandırın:
   - **Ne hakkında uyarı vermek istiyorsunuz?** bölümünde \> **Etkinlik,** \> açılan listeden **Dosyada kötü amaçlı yazılım algılandı'yı** seçin.
   - **Uyarının nasıl tetiklanmasını istiyorsunuz?** section: Bir **etkinlik seçili kuralla her eşleştiğinde** varsayılan değeri bırakın.

   İşiniz bittiğinde **İleri'ye** tıklayın.

5. **Alıcılarınızı ayarlayın** sayfasında aşağıdaki ayarları yapılandırın:
   - **E-posta bildirimleri gönder'in** seçili olduğunu doğrulayın. **E-posta alıcıları** kutusunda, kötü amaçlı bir dosya algılandığında bildirim alması gereken bir veya daha fazla genel yöneticiyi, güvenlik yöneticisini veya güvenlik okuyucuyu seçin.
   - **Günlük bildirim sınırı**: Varsayılan değeri **Sınır yok** seçeneğini belirleyin.

   İşiniz bittiğinde **İleri'ye** tıklayın.

6. **Ayarlarınızı gözden geçirin** sayfasında ayarlarınızı gözden geçirin. Bölümün içindeki ayarları değiştirmek için her bölümde **Düzenle'yi** seçebilirsiniz. Ya da **Geri'ye** tıklayabilir veya sihirbazdaki belirli bir sayfayı seçebilirsiniz.

   **İlkeyi hemen açmak istiyor musunuz?** bölümünde, varsayılan **Evet, hemen aç** ayarını seçili bırakın.

   İşiniz bittiğinde **Son'a** tıklayın.

### <a name="use-security--compliance-powershell-to-create-an-alert-policy-for-detected-files"></a>Algılanan dosyalar için uyarı ilkesi oluşturmak için Güvenlik & Uyumluluğu PowerShell'i kullanma

Önceki bölümde açıklandığı gibi aynı uyarı ilkesini oluşturmak için PowerShell'i kullanmak isterseniz [Güvenlik & Uyumluluğu PowerShell'e bağlanın](/powershell/exchange/connect-to-scc-powershell) ve aşağıdaki komutu çalıştırın:

```powershell
New-ActivityAlert -Name "Malicious Files in Libraries" -Description "Notifies admins when malicious files are detected in SharePoint Online, OneDrive, or Microsoft Teams" -Category ThreatManagement -Operation FileMalwareDetected -NotifyUser "admin1@contoso.com","admin2@contoso.com"
```

**Not**: Varsayılan _Önem Derecesi_ değeri Düşük'dür. Orta veya Yüksek belirtmek için, komuta _Önem Derecesi_ parametresini ve değerini ekleyin.

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-ActivityAlert](/powershell/module/exchange/new-activityalert).

### <a name="how-do-you-know-these-procedures-worked"></a>Bu yordamların işe yaramış olduğunu nasıl anlarsınız?

- SharePoint, OneDrive ve Microsoft Teams için Kasa Eklerini başarıyla açtığınızı doğrulamak için aşağıdaki adımlardan birini kullanın:

  - Microsoft 365 Defender portalında **, ekler Kasa İlkeler & kurallar** \> **Tehdit İlkeleri** \> bölümüne  \> gidin, **Genel ayarlar'ı** seçin ve **SharePoint için Office 365 için Defender aç'ın değerini doğrulayın. OneDrive ve Microsoft Teams** ayarı.

  - Exchange Online PowerShell'de, özellik ayarını doğrulamak için aşağıdaki komutu çalıştırın:

    ```powershell
    Get-AtpPolicyForO365 | Format-List EnableATPForSPOTeamsODB
    ```

    Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-AtpPolicyForO365](/powershell/module/exchange/get-atppolicyforo365).

- Kişilerin kötü amaçlı dosyaları indirmesini başarıyla engellediğinizden emin olmak için, SharePoint Online PowerShell'i açın ve özellik değerini doğrulamak için aşağıdaki komutu çalıştırın:

  ```powershell
  Get-SPOTenant | Format-List DisallowInfectedFileDownload
  ```

  Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant).

- Algılanan dosyalar için bir uyarı ilkesini başarıyla yapılandırdığınızdan emin olmak için aşağıdaki adımlardan birini kullanın:
  - Microsoft 365 Defender portalında **İlkeler & kuralları** \> **Uyarı ilkesi'ne** \> gidin, uyarı ilkesini seçin ve ayarları doğrulayın.
  - Microsoft 365 Defender portal PowerShell'de değerini uyarı ilkesinin adıyla değiştirin\<AlertPolicyName\>, aşağıdaki komutu çalıştırın ve özellik değerlerini doğrulayın:

    ```powershell
    Get-ActivityAlert -Identity "<AlertPolicyName>"
    ```

    Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-ActivityAlert](/powershell/module/exchange/get-activityalert).

- algılanan dosyalar hakkındaki bilgileri SharePoint, OneDrive ve Microsoft Teams görüntülemek için [Tehdit koruması durum raporunu](view-email-security-reports.md#threat-protection-status-report) kullanın. Özellikle, **Verileri görüntüleme ölçütü: İçerik \> Kötü Amaçlı Yazılım** görünümünü kullanabilirsiniz.
