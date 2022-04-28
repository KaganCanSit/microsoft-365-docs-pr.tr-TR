---
title: Denetim günlüğü saklama ilkelerini yönetme
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Denetim günlüğü saklama ilkeleri, yeni Microsoft Purview Denetimi (Premium) özelliklerinin bir parçasıdır. Denetim günlüğü saklama ilkesi, kuruluşunuzda denetim günlüklerinin ne kadar süre tutulacağını belirtmenize olanak tanır.
ms.openlocfilehash: 0a35177c160e80cef2263382e4a1bc04057963b5
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099685"
---
# <a name="manage-audit-log-retention-policies"></a>Denetim günlüğü saklama ilkelerini yönetme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview uyumluluk portalında denetim günlüğü saklama ilkeleri oluşturabilir ve yönetebilirsiniz. Denetim günlüğü saklama ilkeleri, yeni Microsoft Purview Denetimi (Premium) özelliklerinin bir parçasıdır. Denetim günlüğü saklama ilkesi, kuruluşunuzda denetim günlüklerinin ne kadar süre tutulacağını belirtmenize olanak tanır. Denetim günlüklerini 10 yıla kadar saklayabilirsiniz. İlkeleri aşağıdaki ölçütlere göre oluşturabilirsiniz:

- Bir veya daha fazla Microsoft 365 hizmetindeki tüm etkinlikler
- Tüm kullanıcılar veya belirli kullanıcılar tarafından gerçekleştirilen belirli etkinlikler (Microsoft 365 hizmetinde)
- Kuruluşunuzda birden çok ilkeye sahip olduğunuzda hangi ilkenin öncelikli olduğunu belirten bir öncelik düzeyi

## <a name="default-audit-log-retention-policy"></a>Varsayılan denetim günlüğü saklama ilkesi

Microsoft 365'daki denetim (Premium), tüm kuruluşlar için varsayılan denetim günlüğü saklama ilkesi sağlar. Bu ilke tüm Exchange Online, SharePoint Online, OneDrive İş ve Azure Active Directory denetim kayıtlarını bir yıl boyunca korur. Bu varsayılan ilke **, workload** özelliği (etkinliğin gerçekleştiği hizmettir) için **Exchange**, **SharePoint**, **OneDrive**, **AzureActiveDirectory** değerini içeren denetim kayıtlarını korur. Varsayılan ilke değiştirilemez. Varsayılan ilkeye dahil edilen her iş yükü için kayıt türlerinin listesi için bu makaledeki [Daha fazla bilgi](#more-information) bölümüne bakın.

> [!NOTE]
> Varsayılan denetim günlüğü saklama ilkesi yalnızca Office 365 veya Microsoft 365 E5 lisansı atanmış ya da Microsoft 365 E5 Uyumluluk ya da E5 eBulma ve Denetim eklentisi lisansına sahip kullanıcılar tarafından gerçekleştirilen etkinlik denetim kayıtları için geçerlidir. Kuruluşunuzda E5 dışı kullanıcılarınız veya konuk kullanıcılarınız varsa, ilgili denetim kayıtları 90 gün boyunca saklanır.

## <a name="before-you-create-an-audit-log-retention-policy"></a>Denetim günlüğü saklama ilkesi oluşturmadan önce

- Bir denetim bekletme ilkesi oluşturmak veya değiştirmek için uyumluluk portalında Kuruluş Yapılandırması rolüne atanmış olmanız gerekir.

- Kuruluşunuzda en fazla 50 denetim günlüğü saklama ilkesine sahip olabilirsiniz.

- Denetim günlüğünü 90 günden (ve 1 yıla kadar) uzun süre saklamak için, denetim günlüğünü oluşturan kullanıcıya (denetim etkinliği gerçekleştirerek) bir Office 365 E5 veya Microsoft 365 E5 lisansı atanması ya da Microsoft 365 E5 Uyumluluk ya da E5 eBulma ve Denetim eklentisi lisansına sahip olması gerekir. Denetim günlüklerini 10 yıl boyunca tutmak için, denetim günlüğünü oluşturan kullanıcıya E5 lisansına ek olarak 10 yıllık denetim günlüğü saklama eklentisi lisansı da atanmalıdır.

- Tüm özel denetim günlüğü saklama ilkeleri (kuruluşunuz tarafından oluşturulan) varsayılan bekletme ilkesine göre önceliklidir. Örneğin, bir yıldan kısa bir saklama süresine sahip Exchange posta kutusu etkinliği için bir denetim günlüğü saklama ilkesi oluşturursanız, Exchange posta kutusu etkinliklerinin denetim kayıtları özel ilke tarafından belirtilen daha kısa süre boyunca korunur.

## <a name="create-an-audit-log-retention-policy"></a>Denetim günlüğü saklama ilkesi oluşturma

1. <https://compliance.microsoft.com> Uyumluluk portalındaki İzinler sayfasında Kuruluş Yapılandırması rolü atanmış bir kullanıcı hesabına gidin ve bu hesapla oturum açın.

2. Uyumluluk portalının sol bölmesinde **Denetim'e** tıklayın.

3. **Saklama ilkelerini denetle** sekmesine tıklayın.

4. **Denetim bekletme ilkesi oluştur'a** tıklayın ve açılır sayfada aşağıdaki alanları tamamlayın:

   ![Yeni denetim bekletme ilkesi açılır sayfası.](../media/CreateAuditLogRetentionPolicy.png)

   1. **İlke adı:** Denetim günlüğü saklama ilkesinin adı. Bu ad kuruluşunuzda benzersiz olmalıdır ve ilke oluşturulduktan sonra değiştirilemez.

   2. **Açıklama:** İsteğe bağlı, ancak kayıt türü veya iş yükü, ilkede belirtilen kullanıcılar ve süre gibi ilke hakkında bilgi sağlamak yararlı olur.

   3. **Kullanıcı:** İlkenin uygulanacağı bir veya daha fazla kullanıcıyı seçin. Bu kutuyu boş bırakırsanız, ilke tüm kullanıcılara uygulanır. **Kayıt türünü** boş bırakırsanız bir kullanıcı seçmelisiniz.

   4. **Kayıt türü:** İlkenin uygulandığı denetim kaydı türü. Bu özelliği boş bırakırsanız **, Kullanıcılar** kutusunda bir kullanıcı seçmelisiniz. Tek bir kayıt türü veya birden çok kayıt türü seçebilirsiniz:
      - Tek bir kayıt türü seçerseniz **, Etkinlikler** alanı dinamik olarak görüntülenir. İlkenin uygulanacağı seçili kayıt türünden etkinlikleri seçmek için açılan listeyi kullanabilirsiniz. Belirli etkinlikleri seçmezseniz, ilke seçilen kayıt türünün tüm etkinliklerine uygulanır.
      - Birden çok kayıt türü seçerseniz etkinlikleri seçemezsiniz. İlke, seçilen kayıt türlerinin tüm etkinliklerine uygulanır.

   5. **Süre:** İlkenin ölçütlerini karşılayan denetim günlüklerini tutma süresi.

   6. **Öncelik:** Bu değer, kuruluşunuzdaki denetim günlüğü saklama ilkelerinin işlenme sırasını belirler. Daha düşük bir değer daha yüksek bir önceliğe işaret eder. Geçerli öncelikler **1 ile** **10000** arasında sayısal değerlerdir. **1** değeri en yüksek öncelik, **10000** değeri ise en düşük önceliktir. Örneğin, değeri 5 olan bir ilke **, değeri** **10** olan bir ilkeye göre önceliklidir. Daha önce açıklandığı gibi, herhangi bir özel denetim günlüğü saklama ilkesi, kuruluşunuz için varsayılan ilkeden önceliklidir.

5. Yeni denetim günlüğü saklama ilkesini oluşturmak için **Kaydet'e** tıklayın.

Yeni ilke, **Saklama ilkelerini denetle** sekmesindeki listede görüntülenir.

## <a name="manage-audit-log-retention-policies-in-the-compliance-portal"></a>Uyumluluk portalında denetim günlüğü saklama ilkelerini yönetme

Denetim günlüğü saklama ilkeleri **, Denetim bekletme ilkeleri** sekmesinde ( *pano* olarak da adlandırılır) listelenir. Denetim bekletme ilkelerini görüntülemek, düzenlemek ve silmek için panoyu kullanabilirsiniz.

### <a name="view-policies-in-the-dashboard"></a>Panoda ilkeleri görüntüleme

Denetim günlüğü saklama ilkeleri panoda listelenir. İlkeleri panoda görüntülemenin avantajlarından biri, ilkeleri uygulandıkları öncelik içinde listelemek için **Öncelik** sütununa tıklayabilmenizdir. Daha önce açıklandığı gibi, daha düşük bir değer daha yüksek bir önceliğe işaret eder.

![Saklama ilkeleri panosundaki Öncelik sütunu.](../media/AuditLogRetentionDashboardPriority.png)

Ayrıca, açılır sayfada ayarlarını görüntülemek için bir ilke seçebilirsiniz.

> [!NOTE]
> Kuruluşunuz için varsayılan denetim günlüğü saklama ilkesi panoda görüntülenmez.

### <a name="edit-policies-in-the-dashboard"></a>Panoda ilkeleri düzenleme

İlkeyi düzenlemek için açılır sayfayı görüntülemek için seçin. Bir veya daha fazla ayarı değiştirebilir ve değişikliklerinizi kaydedebilirsiniz.

> [!IMPORTANT]
>
> **New-UnifiedAuditLogRetentionPolicy** cmdlet'ini kullanıyorsanız, panodaki **Denetim bekletme ilkesi oluşturma** aracında bulunmayan kayıt türleri veya etkinlikler için bir denetim günlüğü bekletme ilkesi oluşturabilirsiniz. Bu durumda, ilkeyi **Denetim bekletme ilkeleri** panosundan düzenleyemezsiniz (örneğin, bekletme süresini değiştiremez veya etkinlik ekleyip kaldıramazsınız). İlkeyi yalnızca uyumluluk merkezinde görüntüleyebilir ve silebilirsiniz. İlkeyi düzenlemek için Güvenlik & Uyumluluk Merkezi PowerShell.>'da [Set-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/set-unifiedauditlogretentionpolicy) cmdlet'ini kullanmanız gerekir
>
> **Ipucu:** PowerShell kullanılarak düzenlenmesi gereken ilkeler için açılır sayfa üst kısmında bir ileti görüntülenir.

### <a name="delete-policies-in-the-dashboard"></a>Panodaki ilkeleri silme

İlkeyi silmek için **Sil** ![simgesine tıklayın.](../media/92a9f8e0-d469-48da-addb-69365e7ffb6f.jpg) simgesini seçin ve ardından ilkeyi silmek istediğinizi onaylayın. İlke panodan kaldırılır, ancak ilkenin kuruluşunuzdan kaldırılması 30 dakika kadar sürebilir.

## <a name="create-and-manage-audit-log-retention-policies-in-powershell"></a>PowerShell'de denetim günlüğü saklama ilkeleri oluşturma ve yönetme

Denetim günlüğü saklama ilkeleri oluşturmak ve yönetmek için Güvenlik & Uyumluluk Merkezi PowerShell'i de kullanabilirsiniz. PowerShell'i kullanmanın bir nedeni, kullanıcı arabiriminde bulunmayan bir kayıt türü veya etkinliği için ilke oluşturmaktır.

### <a name="create-an-audit-log-retention-policy-in-powershell"></a>PowerShell'de denetim günlüğü saklama ilkesi oluşturma

PowerShell'de denetim günlüğü saklama ilkesi oluşturmak için şu adımları izleyin:

1. [Güvenlik & Uyumluluk Merkezi PowerShell'e Bağlan](/powershell/exchange/connect-to-scc-powershell).

2. Denetim günlüğü saklama ilkesi oluşturmak için aşağıdaki komutu çalıştırın:

   ```powershell
   New-UnifiedAuditLogRetentionPolicy -Name "Microsoft Teams Audit Policy" -Description "One year retention policy for all Microsoft Teams activities" -RecordTypes MicrosoftTeams -RetentionDuration TenYears -Priority 100
   ```

   Bu örnek, şu ayarlarla "Microsoft Teams Denetim İlkesi" adlı bir denetim günlüğü saklama ilkesi oluşturur:

   - İlkenin açıklaması.
   - Tüm Microsoft Teams etkinliklerini korur (*RecordType* parametresi tarafından tanımlandığı şekilde).
   - Microsoft Teams denetim günlüklerini 10 yıl boyunca korur.
   - 100'ün önceliği.

Aşağıda bir denetim günlüğü saklama ilkesi oluşturmaya yönelik başka bir örnek verilmiştir. Bu ilke, "Oturum açan kullanıcı" etkinliğinin denetim günlüklerini kullanıcı admin@contoso.onmicrosoft.com için altı ay boyunca saklar.

```powershell
New-UnifiedAuditLogRetentionPolicy -Name "SixMonth retention for admin logons" -RecordTypes AzureActiveDirectoryStsLogon -Operations UserLoggedIn -UserIds admin@contoso.onmicrosoft.com -RetentionDuration SixMonths -Priority 25
```

Daha fazla bilgi için bkz. [New-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/new-unifiedauditlogretentionpolicy).

### <a name="view-policies-in-powershell"></a>PowerShell'de ilkeleri görüntüleme

Denetim günlüğü saklama ilkelerini görüntülemek için Güvenlik & Uyumluluk Merkezi PowerShell'de [Get-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/get-unifiedauditlogretentionpolicy) cmdlet'ini kullanın.

Burada, kuruluşunuzdaki tüm denetim günlüğü saklama ilkelerinin ayarlarını görüntülemek için örnek bir komut verilmiştir. Bu komut ilkeleri en yüksekten en düşük önceliğe sıralar.

```powershell
Get-UnifiedAuditLogRetentionPolicy | Sort-Object -Property Priority -Descending | FL Priority,Name,Description,RecordTypes,Operations,UserIds,RetentionDuration
```

> [!NOTE]
> **Get-UnifiedAuditLogRetentionPolicy** cmdlet'i kuruluşunuz için varsayılan denetim günlüğü saklama ilkesini döndürmez.

### <a name="edit-policies-in-powershell"></a>PowerShell'de ilkeleri düzenleme

Mevcut denetim günlüğü saklama ilkesini düzenlemek için Güvenlik & Uyumluluk Merkezi PowerShell'de [Set-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/set-unifiedauditlogretentionpolicy) cmdlet'ini kullanın.

### <a name="delete-policies-in-powershell"></a>PowerShell'de ilkeleri silme

Denetim günlüğü saklama ilkesini silmek için Güvenlik & Uyumluluk Merkezi PowerShell'de [Remove-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/remove-unifiedauditlogretentionpolicy) cmdlet'ini kullanın. İlkenin kuruluşunuzdan kaldırılması 30 dakika kadar sürebilir.

## <a name="more-information"></a>Daha fazla bilgi

Daha önce belirtildiği gibi, Azure Active Directory, Exchange Online, SharePoint Online ve OneDrive İş'daki işlemlerin denetim kayıtları varsayılan olarak bir yıl boyunca saklanır. Aşağıdaki tabloda, varsayılan denetim günlüğü saklama ilkesine dahil edilen tüm kayıt türleri (bu hizmetlerin her biri için) listelenmektedir. Bu, özel denetim günlüğü saklama ilkesinin belirli bir kayıt türü, işlem veya kullanıcı için öncelikli olmadığı sürece, bu kayıt türüne sahip herhangi bir işlemin denetim günlüklerinin bir yıl boyunca tutulduğunu gösterir. Her kayıt türü için Enum değeri (bir denetim kaydındaki RecordType özelliğinin değeri olarak görüntülenir) parantez içinde gösterilir.

<br>

****

|AzureActiveDirectory|Exchange |SharePoint veya OneDrive|
|---|---|---|
|AzureActiveDirectory (8)|ExchangeAdmin (1)|ComplianceDLPSharePoint (11)|
|AzureActiveDirectoryAccountLogon (9)|ExchangeItem (2)|ComplianceDLPSharePointClassification (33)|
|AzureActiveDirectoryStsLogon (15)|Kampanya (62)|Project (35)|
||ComplianceDLPExchange (13)|SharePoint (4)|
||ComplianceSupervisionExchange (68)|SharePointCommentOperation (37)|
||CustomerKeyServiceEncryption (69)|SharePointContentTypeOperation (55)|
||ExchangeAggregatedOperation (19)|SharePointFieldOperation (56)|
||ExchangeItemAggregated (50)|SharePointFileOperation (6)|
||ExchangeItemGroup (3)|SharePointListOperation (36)|
||InformationBarrierPolicyApplication (53)|SharePointSharingOperation (14)|
||||
