---
title: DAP Microsoft 365 iş ortaklarının Windows PowerShell kiracılarını yönetme
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: Bu makalede, müşteri eğilimlerini yönetmek üzere Microsoft 365 için PowerShell'in nasıl kullanıldığı hakkında bilgi bulabilirsiniz.
ms.openlocfilehash: ff74cc0ec710996c66a659034f4fb4a49ee57ab1
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977669"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Temsilci Microsoft 365 İzinleri (DAP) Windows PowerShell iş ortaklarıyla kiracıları yönetme

*Bu makale hem son hem de Microsoft 365 Kurumsal hem de Office 365 Kurumsal.*

Windows PowerShell, Dağıtım ve Bulut Çözümü Sağlayıcısı (CSP) iş ortaklarının, aşağıdaki siparişte yer alan müşteri kiralığı ayarlarını kolayca yönetmesine ve rapor etmesine Microsoft 365 yönetim merkezi. İş ortağı yönetici hesabının müşteri eğilimlerine bağlanması için Adına Yönetme (AOBO) izinlerinin gerekli olduğunu unutmayın.

Temsilcili Erişim İzni (DAP) iş ortakları Dağıtım ve Bulut Çözümü Sağlayıcıları (CSP) İş Ortaklarıdır. Bunlar çoğunlukla diğer şirketlere yönelik ağ veya telekom sağlayıcılarıdır. Bu abonelikler Microsoft 365 kendi müşterilerine yaptıkları hizmet tekliflerinde paketli olarak yer almaktadır. Microsoft 365 aboneliği satarken, müşteri eğilimlerini yönetip raporlaymalarını sağlamak için müşteri eğilimlerini yönetme (AOBO) izinlerine otomatik olarak sahip olur.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

Bu konudaki yordamlar için [PowerShell'i Bağlan Microsoft 365 bağlantınız gerekir](connect-to-microsoft-365-powershell.md).

Ayrıca, iş ortağı kiracı yöneticisi kimlik bilgileriniz de gerekir.

## <a name="what-do-you-want-to-do"></a>Ne yapmak istiyorsunuz?

### <a name="list-all-tenant-ids"></a>Tüm kiracı kimliklerini listele

> [!NOTE]
> 500'den fazla kiracınız varsa, cmdlet sözdizimini  _-All_ veya _-MaxResultsParameter ile kapsamına bakın_. Bu, **Get-MsolUser** gibi büyük bir çıktı veremeyen diğer cmdlet'ler için geçerlidir.

Erişiminiz olan tüm müşteri kiracı kimliklerini listeliyorsa bu komutu çalıştırın.

```powershell
Get-MsolPartnerContract -All | Select-Object TenantId
```

Bu, **TenantId** ile tüm müşteri kiracılarınızı listeler.

>[!Note]
>PowerShell Core, **Msol'Microsoft Azure Active Directory Msol** Windows PowerShell cmdlet'leri için Modül Adını Desteklemez. Bu cmdlet'leri kullanmaya devam etmek için, tüm cmdlet'leri Windows PowerShell.
>

### <a name="get-a-tenant-id-by-using-the-domain-name"></a>Etki alanı adını kullanarak bir kiracı kimliği al

Belirli bir müşteri **kiracısı için** etki alanı adına göre TenantId'i almak için bu komutu çalıştırın. Bu _<domainname.onmicrosoft.com>_ istediğiniz müşteri kiracısı gerçek etki alanı adıyla değiştirin.

```powershell
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a>Kiracının tüm etki alanlarını listele

Herhangi bir müşteri kiracısına tüm etki alanlarını almak için bu komutu çalıştırın. Gerçek  _\<customer TenantId value>_ değerle değiştirin.

```powershell
Get-MsolDomain -TenantId <customer TenantId value>
```

Kayıtlı başka etki alanlarınız varsa, bu, müşteri TenantId ile ilişkilendirilmiş tüm etki **alanlarını geri verir**.

### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a>Tüm kiracıların ve kayıtlı etki alanlarının eşlemesini al

Önceki Microsoft 365 için PowerShell komutları, kiracı kimliklerini veya etki alanlarını aynı anda alamama ve bunların arasında net bir eşlemeyi alma gibi bir yolu yoktu. Bu komut, tüm müşteri kiracı kimliklerinizi ve onların etki alanlarının listesini üretir.

```powershell
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a>Kiracı için tüm kullanıcıları al

Bu, belirli bir **kiracının tüm kullanıcıları için UserPrincipalName**, **DisplayName** ve **isLicensed** durumunu görüntüler. Gerçek _\<customer TenantId value>_ değerle değiştirin.

```powershell
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a>Kullanıcı hakkında tüm ayrıntıları al

Belirli bir kullanıcının tüm özelliklerini görmek için bu komutu çalıştırın. Gerçek  _\<customer TenantId value>_ değerlerin _\<user principal name value>_ yerine kullanın.

```powershell
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a>Kullanıcı ekleme, seçenekleri ayarlama ve lisans atama

Kullanıcıların toplu oluşturma, yapılandırma ve lisanslama Microsoft 365, özellikle Microsoft 365 için PowerShell kullanarak verimli bir Microsoft 365. Bu iki adımlı işlemde, önce virgülle ayrılmış değer (CSV) dosyasına eklemek istediğiniz tüm kullanıcılar için girişler oluşturun ve ardından Microsoft 365 için PowerShell kullanarak bu dosyayı içeri aktarın.

#### <a name="create-a-csv-file"></a>CSV dosyası oluşturma

Bu biçimi kullanarak CSV dosyası oluşturun:

`UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`

burada:

- **UsageLocation**: Bunun değeri, kullanıcının iki harfli ISO ülke/bölge kodudur. Ülke/bölge [kodları,ISO Çevrimiçi Gözatma Platformu'nda aramanızı sağlar](https://go.microsoft.com/fwlink/p/?LinkId=532703). Örneğin, AMERIKA Birleşik Devletleri'nin kodu ABD ve Brezilya'nın kodu ise BR kodudur.

- **LicenseAssignment**: Bunun değeri şu biçimi kullanır: `syndication-account:<PROVISIONING_ID>`. Örneğin, müşteri kiracı kullanıcılarına lisanslar O365_Business_Premium, **LisansAssignment** değeri şöyle olur: **dağıtım-hesabı:O365_Business_Premium**. Dağıtım ortağı PROVISIONING_IDs CSP iş ortağı olarak erişiminiz olan Dağıtım İş Ortağı Portalı'nın iletişim konularını bulabilirsiniz.

#### <a name="import-the-csv-file-and-create-the-users"></a>CSV dosyasını içeri aktarma ve kullanıcıları oluşturma

CSV dosyanız oluşturulduktan sonra, kullanıcının ilk oturum açmada değiştirmesi gereken ve sizin belirttiğiniz lisansı atayan süresi dolmayan parolaları olan kullanıcı hesapları oluşturmak için bu komutu çalıştırın. Doğru CSV dosya adının yerine başka bir ad kullanın.

```powershell
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a>Ayrıca bkz.

[İş ortakları için yardım](https://go.microsoft.com/fwlink/p/?LinkId=533477)
