---
title: Denetim günlüğü bekletme ilkelerini yönetme
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
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
description: Denetim günlüğü bekletme ilkeleri, denetim ilkesi yönetimi kapsamındaki yeni Gelişmiş Denetim Microsoft 365. Denetim günlüğü bekletme ilkesi, denetim günlüklerinin kurumda ne kadar süreyle tutula tutula tutula açık olduğunu belirtmenize olanak sağlar.
ms.openlocfilehash: f8c269aa4541c438942c69831857ed531681b742
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986488"
---
# <a name="manage-audit-log-retention-policies"></a>Denetim günlüğü bekletme ilkelerini yönetme

Aşağıdaki çalışma sayfalarında denetim günlüğü bekletme ilkelerini oluşturabilir ve Microsoft 365 uyumluluk merkezi. Denetim günlüğü bekletme ilkeleri, denetim ilkesi yönetimi kapsamındaki yeni Gelişmiş Denetim Microsoft 365. Denetim günlüğü bekletme ilkesi, denetim günlüklerinin kurumda ne kadar süreyle tutula tutula tutula açık olduğunu belirtmenize olanak sağlar. Denetim günlüklerini en çok 10 yıl koruyebilirsiniz. İlkeleri aşağıdaki ölçütlere göre oluşturabilirsiniz:

- Bir veya birden çok hizmette Microsoft 365 etkinlikleri
- Tüm kullanıcılar veya belirli Microsoft 365 tarafından gerçekleştirilen belirli etkinlikler (bir hizmette)
- Birden çok ilkeniz varsa, hangi ilkenin öncelikli olduğunu belirten bir öncelik düzeyi

## <a name="default-audit-log-retention-policy"></a>Varsayılan denetim günlüğü bekletme ilkesi

Gelişmiş Denetim Microsoft 365 tüm kuruluşlar için varsayılan denetim günlüğü bekletme ilkesi sağlar. Bu ilke bir yıl Exchange Online, SharePoint Online, OneDrive İş ve Azure Active Directory tüm denetim kayıtlarını korur. Bu varsayılan ilke **, workload** özelliği (**etkinliğin** olduğu hizmet) için Exchange, **SharePoint**, **OneDrive**, **AzureActiveDirectory** değerini içeren denetim kayıtlarını korur. Varsayılan ilke değiştirilemez. Varsayılan [ilkede](#more-information) yer alan her iş yükünün kayıt türlerinin listesi için, bu makalenin Daha fazla bilgi bölümüne bakın.

> [!NOTE]
> Varsayılan denetim günlüğü bekletme ilkesi yalnızca Office 365 veya Microsoft 365 E5 lisansına sahip olan ya da Microsoft 365 E5 Uyumluluk veya E5 eKbulma ve Denetim eklenti lisansına sahip kullanıcılar tarafından gerçekleştirilen etkinliklere ilişkin denetim kayıtları için geçerlidir. Kuruluşta E5 kullanıcısı olmayan kullanıcılarınız veya konuk kullanıcılarınız varsa, buna karşılık gelen denetim kayıtları 90 gün boyunca korunur.

## <a name="before-you-create-an-audit-log-retention-policy"></a>Denetim günlüğü bekletme ilkesi oluşturmadan önce

- Denetim bekletme ilkesi oluşturmak veya değiştirmek için, Microsoft 365 uyumluluk merkezi Kuruluş Yapılandırması rolüne atanmış olmak gerekir.

- Kuruluşta en çok 50 denetim günlüğü bekletme ilkesi olabilir.

- Denetim günlüğünü 90 gün (ve 1 yıla kadar) süreyle tutmak için, denetim günlüğünü oluşturan kullanıcıya (denetim etkinliği gerçekleştirerek) bir Office 365 E5 veya Microsoft 365 E5 lisansı atanabilir ya da Microsoft 365 E5 Uyumluluk veya E5 eBulma ve Denetim eklenti lisansına sahip olması gerekir. 10 yıllık denetim günlüklerini tutmak için, denetim günlüğünü oluşturan kullanıcıya E5 lisansının yanı sıra 10 yıllık denetim günlüğü bekletme eklenti lisansı da atanabilir.

- Tüm özel denetim günlüğü bekletme ilkeleri (sizin oluşturduğunuz) varsayılan bekletme ilkesine göre önceliğe sahiptir. Örneğin, bir yıldan kısa bir bekletme süresi olan Exchange posta kutusu etkinliği için bir denetim günlüğü bekletme ilkesi oluşturmanız, Exchange posta kutusu etkinliklerinin denetim kayıtları özel ilke tarafından belirtilen süre boyunca korunur.

## <a name="create-an-audit-log-retention-policy"></a>Denetim günlüğü bekletme ilkesi oluşturma

1. Oturum açma <https://compliance.microsoft.com> sayfasının İzinler sayfasında Kuruluş Yapılandırması rolüne atanmış bir kullanıcı hesabıyla Microsoft 365 uyumluluk merkezi.

2. Denetim bölmesinin sol Microsoft 365 uyumluluk merkezi'a **tıklayın**.

3. Denetim bekletme **ilkeleri sekmesine** tıklayın.

4. Denetim **bekletme ilkesi oluştur'a** tıklayın ve sonra çıkış sayfasında aşağıdaki alanları doldurun:

   ![Yeni denetim bekletme ilkesi uç sayfası.](../media/CreateAuditLogRetentionPolicy.png)

   1. **İlke adı:** Denetim günlüğü bekletme ilkesi adı. Bu ad, kurum içinde benzersiz olmalıdır ve ilke oluşturulduktan sonra değiştirilmeyecektir.

   2. **Açıklama:** İsteğe bağlı, ancak ilke hakkında kayıt türü veya iş yükü, ilkede belirtilen kullanıcılar ve süre gibi bilgiler sağlamak yararlı olabilir.

   3. **Kullanıcılar:** İlkeyi uygulamak için bir veya birden çok kullanıcı seçin. Bu kutuyu boş bırakırsanız, ilke tüm kullanıcılara uygulanır. Kayıt türünü boş **bırakırsanız** , bir kullanıcı seçmeniz gerekir.

   4. **Kayıt türü:** İlkenin geçerli olduğu denetim kayıt türü. Bu özelliği boş bırakırsanız, Kullanıcılar kutusundan **bir kullanıcı seçmeniz** gerekir. Tek bir kayıt türü veya birden çok kayıt türü seçin:
      - Tek bir kayıt türü belirtirsiniz, **Etkinlikler alanı** dinamik olarak görüntülenir. Açılan listeyi kullanarak, seçilen kayıt türünden ilkeyi uygulamak üzere etkinlikleri seçebilirsiniz. Belirli etkinlikleri seçmezseniz, ilke seçilen kayıt türünün tüm etkinliklerine uygulanır.
      - Birden çok kayıt türü seçerek etkinlikleri seçesiniz. İlke, seçilen kayıt türlerinin tüm etkinliklerine uygulanır.

   5. **Süre:** İlke ölçütlerine uyan denetim günlüklerinin tutulması için gereken süre.

   6. **Öncelik:** Bu değer, kurumda denetim günlüğü bekletme ilkelerinin hangi sırayla işlenme sıralarını belirler. Daha düşük bir değer, daha yüksek öncelikli olduğunu gösterir. Geçerli öncelikler **1 ile** **10000 arasındaki sayısal değerlerdir**. **1 değeri en yüksek** önceliğe, **10000 değeri de en düşük** önceliktir. Örneğin, değeri 5 olan bir ilke **, değeri** 10 olan bir ilkeye göre **önceliğe sahiptir**. Daha önce de açıklanmıştır; tüm özel denetim günlüğü bekletme ilkesi, kurum için varsayılan ilkeden önceliğe sahiptir.

5. Yeni **denetim günlüğü** bekletme ilkesi oluşturmak için Kaydet'e tıklayın.

Yeni ilke, Denetim bekletme ilkeleri **sekmesindeki listede** görüntülenir.

## <a name="manage-audit-log-retention-policies-in-the-microsoft-365-compliance-center"></a>Denetim günlüğü bekletme ilkelerini aşağıdaki Microsoft 365 uyumluluk merkezi

Denetim günlüğü bekletme ilkeleri, Denetim bekletme ilkeleri **sekmesinde (pano** olarak da denir) *listelenir*. Denetim bekletme ilkelerini görüntülemek, düzenlemek ve silmek için panoyu kullanabilirsiniz.

### <a name="view-policies-in-the-dashboard"></a>Panoda ilkeleri görüntüleme

Denetim günlüğü bekletme ilkeleri panoda listelenir. İlkeleri panoda görüntülemenin bir avantajı, öncelik sütununa tıklar ve uygulanacak önceliğe göre ilkeleri listeleyebilirsiniz. Daha önce de açıklanmıştır, düşük bir değer daha yüksek öncelikli olduğunu gösterir.

![Denetim bekletme ilkeleri panosunda öncelik sütunu.](../media/AuditLogRetentionDashboardPriority.png)

Ayrıca, bir ilkeyi seçerek bu ilkenin ayarlarını uç uç sayfada görüntüleyebilirsiniz.

> [!NOTE]
> Panoda, kurum için varsayılan denetim günlüğü bekletme ilkesi görüntülenmez.

### <a name="edit-policies-in-the-dashboard"></a>Panoda ilkeleri düzenleme

Bir ilkeyi düzenlemek için, ilkeyi seçerek çıkış sayfasını görüntüleyebilirsiniz. Bir veya birden çok ayarı değiştirebilir ve sonra değişikliklerinizi kaydedebilirsiniz.

> [!IMPORTANT]
>
> **New-UnifiedAuditLogRetentionPolicy** cmdlet'ini kullanıyorsanız, panoda Denetim bekletme ilkesi oluştur aracında yer alan kayıt türleri veya etkinlikler için bir denetim günlüğü bekletme ilkesi oluşturabilirsiniz. Bu durumda, Denetimin bekletme ilkeleri panosundan ilkeyi düzenleyemez (örneğin, bekletme süresini değiştiremez veya etkinlikleri ekleyemez ve **kaldırabilirsiniz** ). Uyumluluk merkezinde yalnızca ilkeyi  görüntüp silebilirsiniz. İlkeyi düzenlemek için, Güvenlik ve Uyumluluk Merkezi PowerShell.&'de [Set-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/set-unifiedauditlogretentionpolicy) cmdlet'ini kullan >
>
> **İpucu:** PowerShell kullanılarak düzenleniyor olması gereken ilkelere yönelik olarak, çıkış sayfasının en üstünde bir ileti görüntülenir.

### <a name="delete-policies-in-the-dashboard"></a>Panoda ilkeleri silme

Bir ilkeyi silmek için Sil **simgesine** ![tıklayın.](../media/92a9f8e0-d469-48da-addb-69365e7ffb6f.jpg) simgesini seçin ve ardından ilkeyi silmek istediğinize onaylayın. İlke panodan kaldırılır, ancak ilkenin kuruluştan kaldırılması 30 dakika kadar sürebilir.

## <a name="create-and-manage-audit-log-retention-policies-in-powershell"></a>PowerShell'de denetim günlüğü bekletme ilkelerini oluşturma ve yönetme

Denetim günlüğü bekletme ilkelerini oluşturmak & için Güvenlik ve Uyumluluk Merkezi PowerShell'i de kullanabilirsiniz. PowerShell'i kullanmanın bir nedeni, kullanıcı arabiriminde olmayan bir kayıt türü veya etkinliği için ilke oluşturmaktır.

### <a name="create-an-audit-log-retention-policy-in-powershell"></a>PowerShell'de denetim günlüğü bekletme ilkesi oluşturma

PowerShell'de denetim günlüğü bekletme ilkesi oluşturmak için şu adımları izleyin:

1. [Bağlan ve Uyumluluk & PowerShell'e.](/powershell/exchange/connect-to-scc-powershell)

2. Denetim günlüğü bekletme ilkesi oluşturmak için aşağıdaki komutu çalıştırın:

   ```powershell
   New-UnifiedAuditLogRetentionPolicy -Name "Microsoft Teams Audit Policy" -Description "One year retention policy for all Microsoft Teams activities" -RecordTypes MicrosoftTeams -RetentionDuration TenYears -Priority 100
   ```

   Bu örnekte, bu ayarlarla birlikte "Denetim İlkesini Microsoft Teams denetim günlüğü bekletme ilkesi" adı ve oluşturur:

   - İlkenin açıklaması.
   - Tüm Microsoft Teams korur (*RecordType parametresi tarafından tanımlandığı gibi*).
   - Denetim Microsoft Teams 10 yıl süreyle korur.
   - 100 öncelik.

Denetim günlüğü bekletme ilkesi oluşturmanın başka bir örneği. Bu ilke, kullanıcı oturum açtığında altı ay boyunca "Oturum açan kullanıcı" etkinliğinin denetim günlüklerini admin@contoso.onmicrosoft.com.

```powershell
New-UnifiedAuditLogRetentionPolicy -Name "SixMonth retention for admin logons" -RecordTypes AzureActiveDirectoryStsLogon -Operations UserLoggedIn -UserIds admin@contoso.onmicrosoft.com -RetentionDuration SixMonths -Priority 25
```

Daha fazla bilgi için bkz [. New-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/new-unifiedauditlogretentionpolicy).

### <a name="view-policies-in-powershell"></a>PowerShell'de ilkeleri görüntüleme

Denetim günlüğü bekletme ilkelerini görüntülemek için Güvenlik ve Uyumluluk Merkezi PowerShell'de [Get-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/get-unifiedauditlogretentionpolicy) cmdlet'ini & kullanın.

İşte, kurumuzda tüm denetim günlüğü bekletme ilkelerinin ayarlarını görüntülemeye yönelik örnek bir komut. Bu komut, ilkeleri en yüksekten en düşük önceliğe doğru sıralar.

```powershell
Get-UnifiedAuditLogRetentionPolicy | Sort-Object -Property Priority -Descending | FL Priority,Name,Description,RecordTypes,Operations,UserIds,RetentionDuration
```

> [!NOTE]
> **Get-UnifiedAuditLogRetentionPolicy** cmdlet'i, sizin için varsayılan denetim günlüğü bekletme ilkesi geri dönmez.

### <a name="edit-policies-in-powershell"></a>PowerShell'de ilkeleri düzenleme

Var olan bir denetim günlüğü bekletme ilkesi düzenlemek için Güvenlik ve Uyumluluk Merkezi PowerShell'& de [Set-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/set-unifiedauditlogretentionpolicy) cmdlet'ini kullanın.

### <a name="delete-policies-in-powershell"></a>PowerShell'de ilkeleri silme

Denetim günlüğü bekletme ilkesi silmek için Güvenlik ve Uyumluluk Merkezi PowerShell'de [Remove-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/remove-unifiedauditlogretentionpolicy) cmdlet'ini & kullanın. İlkenin kuruluştan kaldırılması 30 dakika kadar sürebilir.

## <a name="more-information"></a>Daha fazla bilgi

Daha önce de belirtildiği gibi, Azure Active Directory, Exchange Online, SharePoint Online ve OneDrive İş'daki işlemlerin denetim kayıtları varsayılan olarak bir yıl süreyle korunur. Aşağıdaki tabloda, varsayılan denetim günlüğü bekletme ilkesine dahil edilen tüm kayıt türleri (bu hizmetlerin her biri için) listelemektedir. Bu, belirli bir kayıt türü, işlem veya kullanıcı için özel bir denetim günlüğü bekletme ilkesi öncelikli olmadığı sürece, bu kayıt türüyle yapılan tüm işlemlerde denetim günlüklerinin bir yıl süreyle tutuldiği anlamına gelir. Her kayıt türünün Enum değeri (denetim kaydında RecordType özelliği için değer olarak görüntülenir) parantez içinde gösterilir.

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
||ExchangeItemAregated (50)|SharePointFileOperation (6)|
||ExchangeItemGroup (3)|SharePointListOperation (36)|
||InformationBarrierPolicyApplication (53)|SharePointSharingOperation (14)|
||||
