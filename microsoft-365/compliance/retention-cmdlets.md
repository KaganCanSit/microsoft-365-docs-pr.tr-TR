---
title: Bekletme için kullanılabilir PowerShell cmdlet'lerini belirleme
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: normal
ms.collection:
- M365-security-compliance
- SPO_Content
- m365initiative-compliance
description: Ölçeklendirme, otomasyon veya gelişmiş yapılandırma senaryoları için gerekli olabilecek yapılandırmayı destekleyen saklama için PowerShell cmdlet'lerini belirleyin.
ms.openlocfilehash: 23dda0c7e5cdc2ce52c2dfca8e5ab575d5653b99
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66625995"
---
# <a name="powershell-cmdlets-for-retention-policies-and-retention-labels"></a>Bekletme ilkeleri ve bekletme etiketleri için PowerShell cmdlet'leri

>*[Güvenlik & uyumluluğu için Microsoft 365 lisanslama kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Ölçeklendirme, otomatik betikler veya gelişmiş yapılandırma senaryoları için ihtiyaç duyabileceğiniz bekletme ilkeleri ve bekletme etiketleri için kullanılabilen ana PowerShell cmdlet'lerini tanımlamak için aşağıdaki bölümleri kullanın. Cmdlet'lerin tam listesi için PowerShell belgelerindeki [ilke ve uyumluluk saklama listesine](/powershell/module/exchange#policy-and-compliance-retention) bakın.

Bu cmdlet'leri kullanmadan önce [Güvenlik & Uyumluluk Merkezi PowerShell'e bağlanmanız](/powershell/exchange/connect-to-scc-powershell) gerekir.

İzleyen açıklamalarda, bekletme ilkesi bir bekletme ilkesine (etiket yok) veya bekletme etiketi ilkesine başvurabilir. Her ilke, statik mi yoksa uyarlamalı mı olduğunu ve ilkenin uygulanacağı konumları tanımlar. İlke daha sonra yapılandırmayı tamamlamak için bir kural gerektirir.

Örneğin:
- Bekletme ilkesi, bekletme ayarlarını tanımlayan bir kurala (örneğin, beş yıl boyunca saklama ve silme) ihtiyaç duyar.

Bekletme etiketlerini kullandığınızda, bunlar bekletme ayarlarını içerir ve ilkeleri farklı kurallara ihtiyaç duyar:
- Yayımladığınız bir bekletme etiketi ilkesi, uygulamalarda hangi etiketlerin görüntüleneceğini tanımlayan bir kurala ihtiyaç duyar.
- Otomatik uygulama bekletme etiketi ilkesi, uygulanacak etiketi ve etiketi uygulama koşullarını tanımlayan bir kurala ihtiyaç duyar.

## <a name="retention-cmdlets-for-most-locations"></a>Çoğu konum için bekletme cmdlet'leri

Konumlar **Exchange e-postası**, **SharePoint siteleri**, **OneDrive hesapları**, **Microsoft 365 Grupları**, **Skype Kurumsal**, **Exchange ortak klasörleri**, **Teams sohbet iletileri** veya **Teams kanal iletileri** olduğunda aşağıdaki tabloda yer alan cmdlet'leri kullanın.

Konumlar Teams özel kanal iletileri, Yammer kullanıcı iletileri veya Yammer topluluk iletileri içinse bu cmdlet'leri kullanmayın. Bu konumlar [, sonraki bölümde](#retention-cmdlets-specific-to-teams-private-channels-and-yammer) tanımlanan alternatif cmdlet'lere sahiptir.

|Cmdlet|Açıklama|Geçerli konumlar|
|:-----|:-----|:-----|:-----|
|[Enable-complianceTagStorage](/powershell/module/exchange/enable-compliancetagstorage) <br /><br /> [Get-ComplianceTagStorage](/powershell/module/exchange/enable-compliancetagstorage) |Depolama alanı oluşturmak veya saklama etiketleri için bu depolama alanını görüntülemek için tek seferlik bir işlem |Exchange e-postası <br /><br />SharePoint siteleri <br /><br /> OneDrive hesapları <br /><br /> Microsoft 365 Grupları|
|[Get-ComplianceTag](/powershell/module/exchange/get-compliancetag)<br /><br> [New-ComplianceTag](/powershell/module/exchange/new-compliancetag) <br /><br> [Remove-ComplianceTag](/powershell/module/exchange/remove-compliancetag) <br /><br> [Set-ComplianceTag](/powershell/module/exchange/set-compliancetag) |Bekletme etiketlerini görüntüleme, oluşturma, silme, yapılandırma |Exchange e-postası <br /><br /> SharePoint siteleri <br /><br /> OneDrive hesapları<br /><br /> Microsoft 365 Grupları|
|[Get-RecordReviewNotificationTemplateConfig](/powershell/module/exchange/get-recordreviewnotificationtemplateconfig) <br /><br /> [Set-RecordReviewNotificationTemplateConfig](/powershell/module/exchange/remove-retentioncompliancepolicy)  |Değerlendirme gözden geçirme bildirimi ve anımsatıcı ayarları için yapılandırmayı görüntüleme veya yapılandırma |Exchange e-postası <br /><br /> SharePoint siteleri <br /><br /> OneDrive hesapları <br /><br /> Microsoft 365 Grupları|
|[Get-RetentionCompliancePolicy](/powershell/module/exchange/get-retentioncompliancepolicy) <br /><br /> [New-RetentionCompliancePolicy](/powershell/module/exchange/new-retentioncompliancepolicy) <br /><br /> [Remove-RetentionCompliancePolicy](/powershell/module/exchange/remove-retentioncompliancepolicy) <br /><br /> [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) |Bekletme için ilkeleri görüntüleme, oluşturma, silme, yapılandırma |Exchange e-postası <br /><br /> SharePoint siteleri <br /><br /> OneDrive hesapları<br /><br /> Microsoft 365 Grupları <br /><br /> Skype Kurumsal <br /><br /> Exchange ortak klasörleri <br /><br /> Teams sohbet iletileri <br /><br /> Teams kanal iletileri |
|[Get-RetentionComplianceRule](/powershell/module/exchange/get-retentioncompliancepolicy) <br /><br /> [New-RetentionComplianceRule](/powershell/module/exchange/get-retentioncompliancepolicy) <br /><br /> [Set-RetentionComplianceRule](/powershell/module/exchange/set-retentioncompliancerule) <br /><br /> [Remove-RetentionComplianceRule](/powershell/module/exchange/remove-retentioncompliancerule)  | Bekletme veya bekletme etiketleri için ilkelerin ayarlarını görüntüleme, oluşturma, yapılandırma, silme |Exchange e-postası <br /><br /> SharePoint siteleri <br /><br /> OneDrive hesapları <br /><br /> Microsoft 365 Grupları <br /><br /> Skype Kurumsal <br /><br /> Exchange ortak klasörleri <br /><br /> Teams sohbet iletileri <br /><br /> Teams kanal iletileri |

## <a name="retention-cmdlets-specific-to-teams-private-channels-and-yammer"></a>Teams özel kanallarına ve Yammer'a özgü bekletme cmdlet'leri

Konumlar **Teams özel kanal iletileri**, **Yammer kullanıcı** iletileri veya **Yammer topluluk** iletileri için olduğunda aşağıdaki cmdlet'leri kullanın.

Konumlar Teams sohbet iletileri, Teams kanal iletileri, Exchange e-postası, SharePoint siteleri, OneDrive hesapları, Microsoft 365 Grupları, Skype Kurumsal veya Exchange ortak klasörleri için olduğunda, [önceki bölümde](#retention-cmdlets-for-most-locations) listelenen cmdlet'leri kullanın.

|Cmdlet|Açıklama|Geçerli konumlar|
|:-----|:-----|:-----|:-----|
|[Get-AppRetentionCompliancePolicy](/powershell/module/exchange/get-appretentioncompliancepolicy) <br /><br> [New-AppRetentionCompliancePolicy](/powershell/module/exchange/new-appretentioncompliancepolicy) <br /><br> [Remove-AppRetentionCompliancePolicy](/powershell/module/exchange/remove-appretentioncompliancepolicy) <br /><br> [Set-AppRetentionCompliancePolicy](/powershell/module/exchange/remove-appretentioncompliancepolicy) | Bekletme ilkelerini görüntüleme, oluşturma, silme, yapılandırma |Teams özel kanal iletileri <br /><br /> Yammer kullanıcı iletileri <br /><br /> Yammer topluluk iletileri|
|[Get-AppRetentionComplianceRule](/powershell/module/exchange/get-appretentioncompliancerule) <br /><br /> [New-AppRetentionComplianceRule](/powershell/module/exchange/new-appretentioncompliancerule) <br /><br /> [Remove-AppRetentionComplianceRule](/powershell/module/exchange/remove-appretentioncompliancerule) <br /><br /> [Set-AppRetentionComplianceRule](/powershell/module/exchange/remove-appretentioncompliancerule) | Bekletme ilkeleri için bekletme ayarlarını görüntüleme, oluşturma, silme, yapılandırma |Teams özel kanal iletileri <br /><br /> Yammer kullanıcı iletileri <br /><br /> Yammer topluluk iletileri|

## <a name="configuration-guidance"></a>Yapılandırma kılavuzu

Ayrıntılı bilgi ve örnekler için her cmdlet ile ilişkili yardım sayfalarını kullanın.

Bekletme etiketleri oluşturma ve yayımlama konusunda destekli yardım için bkz. [PowerShell kullanarak bekletme etiketleri oluşturma ve yayımlama](bulk-create-publish-labels-using-powershell.md).