---
title: MSCommerce PowerShell modülü için AllowSelfServicePurchase kullanma
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: mijeffer, pablom
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: ''
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_ssp
- AdminSurgePortfolio
search.appverid:
- MET150
description: Self servis satın alma özelliğini açmak veya kapatmak için AllowSelfServicePurchase PowerShell cmdlet'ini kullanmayı öğrenin.
ROBOTS: NOINDEX, NOFOLLOW
ms.date: 4/7/2022
ms.openlocfilehash: e4423892f2dc045a9729e68519c85d471838d5ac
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66042198"
---
# <a name="use-allowselfservicepurchase-for-the-mscommerce-powershell-module"></a>MSCommerce PowerShell modülü için AllowSelfServicePurchase kullanma

**MSCommerce** PowerShell modülü artık [PowerShell Galerisi'de](https://aka.ms/allowselfservicepurchase-powershell-gallery) kullanılabilir. Modül, **allowSelfServicePurchase** için kuruluşunuzdaki kullanıcıların self servis satın alma işlemi yapıp yapamayacağını denetlemenize olanak tanıyan bir **PolicyID** parametre değeri içerir.

**MSCommerce** PowerShell modülünü kullanarak şunları yapabilirsiniz:

- **AllowSelfServicePurchase** parametre değerinin varsayılan durumunu (etkin veya devre dışı) görüntüleyin
- Geçerli ürünlerin listesini ve self servis satın alma özelliğinin etkinleştirilip etkinleştirilmediğini görüntüleme
- Belirli bir ürünü etkinleştirmek veya devre dışı bırakmak için geçerli ayarı görüntüleme veya değiştirme

## <a name="requirements"></a>Gereksinimler

**MSCommerce** PowerShell modülünü kullanmak için şunları yapmanız gerekir:

- Windows 10 cihazı
- PowerShell 5 veya üzeri. PowerShell 6.x/7.x şu anda bu modülde desteklenmiyor.
- Cihaz için yönetici izni
- Kiracınız için Genel veya Faturalama Yöneticisi rolü

## <a name="install-the-mscommerce-powershell-module"></a>MSCommerce PowerShell modülünü yükleme

**MSCommerce** PowerShell modülünü Windows 10 cihazınıza bir kez yükler ve ardından başlattığınız her PowerShell oturumuna aktarırsınız. **MSCommerce** PowerShell modülünü [PowerShell Galerisi](https://aka.ms/allowselfservicepurchase-powershell-gallery) indirin.

**MSCommerce** PowerShell modülünü **PowerShellGet** ile yüklemek için aşağıdaki komutu çalıştırın:

```powershell
Install-Module -Name MSCommerce
```

## <a name="import-mscommerce-into-the-powershell-session"></a>MSCommerce'i PowerShell oturumuna aktarma

Modülü Windows 10 cihazınıza yükledikten sonra, başlattığınız her PowerShell oturumuna aktarırsınız. Bir PowerShell oturumuna aktarmak için aşağıdaki komutu çalıştırın:

```powershell
Import-Module -Name MSCommerce
```

## <a name="connect-to-mscommerce-with-your-credentials"></a>Kimlik bilgilerinizle MSCommerce'e Bağlan

Kimlik bilgilerinizle PowerShell modülüne bağlanmak için aşağıdaki komutu çalıştırın.

```powershell
Connect-MSCommerce
```

Bu komut geçerli PowerShell oturumunu bir Azure Active Directory kiracısına bağlar. Komut, bağlanmak istediğiniz kiracı için bir kullanıcı adı ve parola ister. Kimlik bilgileriniz için çok faktörlü kimlik doğrulaması etkinleştirildiyse, oturum açmak için etkileşimli seçeneği kullanırsınız.

## <a name="view-details-for-allowselfservicepurchase"></a>AllowSelfServicePurchase için ayrıntıları görüntüleme

**AllowSelfServicePurchase** parametre değerinin açıklamasını ve kuruluşunuza bağlı olarak varsayılan durumu görüntülemek için aşağıdaki komutu çalıştırın:

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase
```

## <a name="view-a-list-of-self-service-purchase-products-and-their-status"></a>Self servis satın alma ürünlerinin listesini ve durumlarını görüntüleme

Kullanılabilir tüm self servis satın alma ürünlerinin listesini ve her birinin durumunu görüntülemek için aşağıdaki komutu çalıştırın:

```powershell
Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase
```

Aşağıdaki tabloda, kullanılabilir ürünler ve **bunların ProductId'leri** listelenir.

| Ürün | Productıd |
|-----------------------------|--------------|
| Kullanıcı başına Power Apps | CFQ7TTC0LH2H |
| Kullanıcı başına Power Automate | CFQ7TTC0KP0N |
| RPA Power Automate | CFQ7TTC0KXG6  |
| Power BI Premium (tek başına) | CFQ7TTC0KXG7  |
| Power BI Pro | CFQ7TTC0L3PB |
| Project Plan 1* | CFQ7TTC0HDB1 |
| Project Plan 3* | CFQ7TTC0HDB0 |
| Visio Plan 1* | CFQ7TTC0HD33 |
| Visio Plan 2* | CFQ7TTC0HD32 |
| Windows 365 Enterprise | CFQ7TTC0HHS9 |
| Windows 365 Business | CFQ7TTC0J203 |
| Windows Hibrit Avantajı ile Windows 365 Business | CFQ7TTC0HX99 |

*Bu kimlikler değişti. Eski kimlikleri kullanan ürünleri daha önce engellediyseniz, yeni kimlikler kullanılarak otomatik olarak engellenir. Ek çalışma gerekmez.

## <a name="view-or-set-the-status-for-allowselfservicepurchase"></a>AllowSelfServicePurchase durumunu görüntüleme veya ayarlama

Self servis satın alma için kullanılabilen ürünlerin listesini görüntüledikten sonra, belirli bir ürünün ayarını görüntüleyebilir veya değiştirebilirsiniz.

Belirli bir ürünün ilke ayarını almak için aşağıdaki komutu çalıştırın:

```powershell
Get-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N
```

Belirli bir ürün için ilke ayarını etkinleştirmek için aşağıdaki komutu çalıştırın:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N -Enabled $True
```

Belirli bir ürünün ilke ayarını devre dışı bırakmak için aşağıdaki komutu çalıştırın:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N -Enabled $False
```

## <a name="example-script-to-disable-allowselfservicepurchase"></a>AllowSelfServicePurchase'ı devre dışı bırakmak için örnek betik

Aşağıdaki örnek **, MSCommerce** modülünü içeri aktarma, hesabınızla oturum açma, kullanıcı başına Power Automate için **ProductId** alma ve ardından bu ürün için **AllowSelfServicePurchase'ı** devre dışı bırakma konusunda size yol gösterir.

```powershell
Import-Module -Name MSCommerce
Connect-MSCommerce #sign-in with your global or billing administrator account when prompted
$product = Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase | where {$_.ProductName -match 'Power Automate per user'}
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product.ProductID -Enabled $false
```

Ürün için birden çok değer varsa, aşağıdaki örnekte gösterildiği gibi komutu her değer için ayrı ayrı çalıştırabilirsiniz:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product[0].ProductID -Enabled $false
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product[1].ProductID -Enabled $false
```


## <a name="troubleshooting"></a>Sorun giderme

### <a name="problem"></a>Sorun

Aşağıdaki hata iletisini görürsünüz:

> HandleError: policyId 'AllowSelfServicePurchase' ile alınamadı, ErrorMessage - Temel alınan bağlantı kapatıldı: Gönderme sırasında beklenmeyen bir hata oluştu.

Bunun nedeni Aktarım Katmanı Güvenliği'nin (TLS) eski bir sürümü olabilir. Bu hizmeti bağlamak için TLS 1.2 veya üzerini kullanmanız gerekir

### <a name="solution"></a>Çözüm

TLS 1.2'ye yükseltin. Aşağıdaki söz dizimi ServicePointManager Güvenlik Protokolü'ni TLS1.2 olarak güncelleştirir:

```powershell
 [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.SecurityProtocolType]::Tls12
```

Daha fazla bilgi için bkz. [TLS 1.2'yi etkinleştirme](/mem/configmgr/core/plan-design/security/enable-tls-1-2).

<!--
## Uninstall the MSCommerce module

Before you uninstall the MSCommerce module, close your current PowerShell session, then open a new session with admin rights.

To remove the **MSCommerce** PowerShell module from your computer, run the following command:

```powershell
Uninstall-Module -Name MSCommerce
```-->

## <a name="related-content"></a>İlgili içerik

[Self servis satın almaları yönetme (Yönetici)](manage-self-service-purchases-admins.md) (makale)

[Self servis satın alma hakkında SSS](self-service-purchase-faq.yml) (makale)
