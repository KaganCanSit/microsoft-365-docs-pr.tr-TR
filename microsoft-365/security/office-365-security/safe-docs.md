---
title: Kasa Belgeler'i Office 365 için Microsoft Defender
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: kshi
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Kasa Microsoft 365 E5/A5 veya Microsoft 365 E5/A5 Güvenlik belgelerini nasıl Microsoft 365 E5 öğrenin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: ab5e35954cac20a18e34f418b5b9fcdc7f2fd007
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466355"
---
# <a name="safe-documents-in-microsoft-365-e5a5"></a>Kasa/A5'Microsoft 365 E5 Belgeleri Belgele

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Kasa Belgeler, belgelerinizi Uç Nokta için Microsoft Defender için [Korumalı](https://support.microsoft.com/office/d6f09ac7-e6b9-4495-8e43-2bbcdbcb6653) Görünüm'de veya [Application Guard'da](https://support.microsoft.com/topic/9e0fb9c2-ffad-43bf-8ba3-78f785fdba46) Office taramak için Office.[](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)

Kullanıcıların Yerel cihazlarında uç nokta için Defender'ın yüklü olması veya Belge korumasının Kasa olması gerekli değildir. Aşağıdaki gereksinimlerin Kasa kullanıcılar Belge korumasına sahip olur:

- Kasa makalede açıklandığı gibi, kuruluşta belgeler etkinleştirilmiştir.
- Gerekli lisans planından lisanslar kullanıcılara atanır. Kasa Belgeler **, Office 365 SafeDocs** (veya **SAFEDOCS** veya **bf6f5520-59e3-4f82-974b-7dbbc4fd27c7**) hizmet planı (hizmet olarak da bilinir) tarafından denetlenmektedir. Bu hizmet planı aşağıdaki lisans planlarında (lisans planları, ürün planları veya Microsoft 365 olarak da bilinir) kullanılabilir:
  - Microsoft 365 A5 için yeni bilgiler
  - Microsoft 365 A5 için Karne
  - Microsoft 365 E5
  - Microsoft 365 E5 Güvenlik

  Kasa Belgeler, lisans planlarına Office 365 için Microsoft Defender değildir.

  Daha fazla bilgi için bkz [. Lisanslama için ürün adları ve hizmet planı tanımlayıcıları](/azure/active-directory/enterprise-users/licensing-service-plan-reference).

- Bunlar Kurumlar için Microsoft 365 Uygulamaları (eski adı Office 365 ProPlus) 2004 veya sonraki bir sürümünü kullanıyor.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açın<https://security.microsoft.com>. Doğrudan Ekler sayfasına **Kasa için**, kullanın<https://security.microsoft.com/safeattachmentv2>.

- Exchange Online PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online e bağlama](/powershell/exchange/connect-to-exchange-online-powershell).

- Bu makaledeki **yordamları Exchange Online** önce bu makalede izinlere ihtiyacınız vardır:
  - Belge ayarlarını Kasa için, Kuruluş Yönetimi veya Güvenlik Yöneticisi **rol gruplarının** **üyesi olun**.
  - Belgeler ayarlarına salt Kasa için, Genel Okuyucu veya Güvenlik Okuyucusu rol **gruplarının üyesi** olun.

  Daha fazla bilgi için bkz. [Exchange Online](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Görev sırasında ilgili kullanıcı Azure Active Directory eklemek Microsoft 365 yönetim merkezi kullanıcılara çalışma sayfalarındaki diğer özellikler için gerekli izinleri ve izinleri Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  >
  > - **Görünüm'de Yalnızca Görüntüleme** [kuruluş Exchange Online rol](/Exchange/permissions-exo/permissions-exo#role-groups) grubu, özel salt okunur erişim de sağlar.

### <a name="how-does-microsoft-handle-your-data"></a>Microsoft verilerinizi nasıl işler?

Korunmak için Belgeler Kasa çözümleme için dosyaları [Uç Nokta için Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) buluta gönderir. Verilerinizin nasıl Uç Nokta için Microsoft Defender ilgili ayrıntıları burada bulunabilir: [Uç Nokta için Microsoft Defender ve gizlilik](/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy).

Postayle gönderilen Kasa Belgeler çözümleme için gereken süre kadar (normalde 24 saatten az) Uç Nokta için Defender'da tutulmz.

## <a name="use-the-microsoft-365-defender-portal-to-configure-safe-documents"></a>Belgeler Microsoft 365 Defender i yapılandırmak için Kasa kullanma

1. aşağıdaki Microsoft 365 Defender portalında, <https://security.microsoft.com>İlkeler bölümünde **E-posta &** \> İşbirliği **İlkeleri &** \>  \> Kuralları Tehdit **Kasa'e** gidin. Doğrudan Ekler sayfasına **Kasa için**, kullanın<https://security.microsoft.com/safeattachmentv2>.

2. Ekler **sayfasında Kasa ayarlar'a** **tıklayın**.

3. Görüntülenen **Genel ayarlar** açılır sayfasında aşağıdaki ayarları yapılandırabilirsiniz:
   - **Belgeler Kasa açma Office açma**: Özelliği açmak için iki durumlu düğmeyi sağa taşıma: ![Açık.](../../media/scc-toggle-on.png)
   - **Kişiler Bu Belgeler dosyayı** kötü amaçlı olarak tanımlasa Kasa Korumalı Görünüm'e tıklamalarına izin ver: Bu seçeneği kapalı bırakmanız önerilir (iki durumlu düğmeyi sola bırakın: ![Kapalı.](../../media/scc-toggle-off.png)

   Bitirdiğinizde, **Kaydet**'i tıklatın.

   :::image type="content" source="../../media/safe-docs-global-settings.png" alt-text="Ekler Kasa Genel ayarlar'ı seçdikten sonra Belgeler Kasa ayarlarına tıklayın" lightbox="../../media/safe-docs-global-settings.png":::

### <a name="use-exchange-online-powershell-to-configure-safe-documents"></a>belgeleri Exchange Online yapılandırmak için powershell Kasa kullanma

PowerShell kullanıcı arabirimini Belgeler'de Kasa tercih ediyorsanız, PowerShell'de aşağıdaki Exchange Online kullanın:

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs <$true | $false> -AllowSafeDocsOpen <$true | $false>
```

- _EnableSafeDocs parametresi_, Belgelerin tüm kuruluş Kasa etkinleştirmesini veya devre dışı bırakmasını sağlar.
- _AllowSafeDocsOpen_ parametresi, belgenin kötü amaçlı olarak tanımlandığ sürece kullanıcıların Korumalı Görünüm'den (yani belgeyi açmasına) izin verir veya bu parametreden ayrılır.

Bu örnek Kasa tüm kuruluş için Tüm Belgeler'in açılmasını sağlar ve kullanıcıların Korumalı Görünüm'den kötü amaçlı olarak tanımlanan belgeleri açmasını sağlar.

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs $true -AllowSafeDocsOpen $false
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

### <a name="configure-individual-access-to-safe-documents"></a>Belgelere tek tek Kasa yapılandırma

Belgeler özelliğine erişimi seçmeli olarak izin vermek veya engellemek Kasa, şu adımları izleyin:

1. Daha önce Kasa makalede açıklandığı gibi Microsoft 365 Defender portalında veya PowerShell Exchange Online de Belgeler'i açın.
2. Azure AD PowerShell'i kullanarak belirli Kasa belgelerini devre dışı bırakma konusunda açıklandığı gibi Belirli kullanıcılar için belirli Microsoft 365 hizmetlerini belirli bir lisans planı için devre [dışı bırakma konusunda açıklanmıştır](/microsoft-365/enterprise/disable-access-to-services-with-microsoft-365-powershell#disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan).

  PowerShell'de devre dışı bırakmak istediğiniz hizmet planının adı **SAFEDOCS'tır**.

Daha fazla bilgi için, aşağıdaki konulara bakın:

- [PowerShell Microsoft 365 ve hizmetleri görüntüleme](/microsoft-365/enterprise/view-licenses-and-services-with-microsoft-365-powershell)
- [PowerShell Microsoft 365 lisansı ve hizmet ayrıntılarını görüntüleme](/microsoft-365/enterprise/view-account-license-and-service-details-with-microsoft-365-powershell)
- [Lisanslama için ürün adları ve hizmet planı tanımlayıcıları](/azure/active-directory/enterprise-users/licensing-service-plan-reference)

### <a name="onboard-to-the-microsoft-defender-for-endpoint-service-to-enable-auditing-capabilities"></a>Denetim özelliklerini etkinleştirmek Uç Nokta için Microsoft Defender hizmetine ekleme

Denetim olanaklarını etkinleştirmek için, yerel cihazın yüklü Uç Nokta için Microsoft Defender olması gerekir. Dağıtım Uç Nokta için Microsoft Defender, dağıtımın çeşitli aşamalarını tamamlamalısınız. Eklemeden sonra, denetim özelliklerini özellikler portalında Microsoft 365 Defender yapılandırabilirsiniz.

Daha fazla bilgi edinmek için [bkz. Uç Nokta için Microsoft Defender ekleme](/microsoft-365/security/defender-endpoint/onboarding). Ek yardıma ihtiyacınız varsa Ekleme sorunlarını [giderme Uç Nokta için Microsoft Defender bakın](/microsoft-365/security/defender-endpoint/troubleshoot-onboarding).

### <a name="how-do-i-know-this-worked"></a>Nasıl yaparım? çalıştığını biliyor musunuz?

Belgeler'i etkinleştirdikten ve yapılandırmış Kasa için, aşağıdaki adımlardan herhangi birini yapın:

- Microsoft 365 Defender portalında, Genel ayarlar bölümünde  **E-posta &** \> İşbirliği **İlkeleri &** \> \> Kuralları Tehdit ilkeleri **Kasa**  \> Ekler'e **gidin ve** Office istemcileri için **Kasa** **Belgelerini aç ve Belgeler'in dosyayı kötü amaçlı ayarlar olarak tanımlasa Kasa Korumalı Görünüm'e tıklamasına izin** ver.

- PowerShell'de Exchange Online komutu çalıştırın ve özellik değerlerini doğrulayın:

  ```powershell
  Get-AtpPolicyForO365 | Format-List *SafeDocs*
  ```

- Belgeleri koruma hakkında test etmek için Kasa kullanılabilir. Bu dosyalar, kötü amaçlı yazılımdan EICAR.TXT ve virüsten koruma çözümlerini test etmek için bu dosyalara benzer. Dosyalar zararlı değildir, ancak Belgeler korumasını Kasa tetikler.

  - [SafeDocsDemo.docx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.docx)
  - [SafeDocsDemo.pptx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.pptx)
  - [SafeDocsDemo.xlsx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.xlsx)
