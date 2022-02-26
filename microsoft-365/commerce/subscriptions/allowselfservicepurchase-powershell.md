---
title: MSCommerce PowerShell modülü için AllowSelfServicePurchase kullanma
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
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
- AdminSurgePortfolio
- commerce_ssp
search.appverid:
- MET150
description: Self servis satın alma hizmetini açmak veya kapatmak için AllowSelfServicePurchase PowerShell cmdlet'ini nasıl kullanabileceğinizi öğrenin.
ROBOTS: NOINDEX, NOFOLLOW
ms.date: 12/15/2021
ms.openlocfilehash: ebe01b9ed55b13d1d61ae1a59dca3bdb6373f285
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "62974169"
---
# <a name="use-allowselfservicepurchase-for-the-mscommerce-powershell-module"></a>MSCommerce PowerShell modülü için AllowSelfServicePurchase kullanma

**MSCommerce** PowerShell modülü artık [PowerShell Galerisi'nde kullanılabilir](https://aka.ms/allowselfservicepurchase-powershell-gallery). Modül, **allowSelfServicePurchase** için bir **PolicyID** parametre değeri içerir ve bu değer, organizasyonlu kullanıcıların self servis satın almalar yapma olanaklarını denetlemenize olanak sağlar.

**MSCommerce PowerShell modülünü** kullanarak şunları yapmak için kullanabilirsiniz:

- Etkin veya devre dışı olsa da **AllowSelfServicePurchase** parametre değerinin varsayılan durumunu görüntüleme
- Geçerli ürünlerin listesini ve self servis alışverişin etkinleştirildiğinde veya devre dışı bırakılmıştır
- Belirli bir ürünü etkinleştirmek veya devre dışı bırakmak için geçerli ayarı görüntüleme veya değiştirme

## <a name="requirements"></a>Gereksinimler

**MSCommerce** PowerShell modülünü kullanmak için gerekenler:

- Windows 10 cihazı
- PowerShell 5 veya daha altında. Şu anda, bu modülde PowerShell 6.x/7.x desteklenmiyor.
- Cihaz için yönetici izni
- Kiracınız için Genel veya Fatura Yöneticisi rolü

## <a name="install-the-mscommerce-powershell-module"></a>MSCommerce PowerShell modülünü yükleme

**MSCommerce** PowerShell modülünü Windows 10 cihazınıza yükleyebilir ve ardından bu modülü başlatan her PowerShell oturumuna aktarabilirsiniz. **PowerShell Galerisi'den MSCommerce** [PowerShell modülünü indirin](https://aka.ms/allowselfservicepurchase-powershell-gallery).

**PowerShellGet ile MSCommerce** PowerShell modülünü **yüklemek** için aşağıdaki komutu çalıştırın:

```powershell
Install-Module -Name MSCommerce
```

## <a name="import-mscommerce-into-the-powershell-session"></a>MSCommerce'ı PowerShell oturumuna aktarma

Modülü Windows 10 cihazınıza yükledikten sonra, bu modülü başlatan her PowerShell oturumuna içeri aktarın. PowerShell oturumuna içeri aktarma işlemi için aşağıdaki komutu çalıştırın:

```powershell
Import-Module -Name MSCommerce
```

## <a name="connect-to-mscommerce-with-your-credentials"></a>Bağlan bilgilerinizle MSCommerce'a oturum açma

PowerShell modülüne kimlik bilgilerinizle bağlanmak için aşağıdaki komutu çalıştırın.

```powershell
Connect-MSCommerce
```

Bu komut, geçerli PowerShell oturumunu bir Azure Active Directory bağlar. Komut, bağlanmak istediğiniz kiracı için bir kullanıcı adı ve parola ister. Kimlik bilgileriniz için çok faktörlü kimlik doğrulaması etkinleştirildiyse, oturum açmak için etkileşimli seçeneği kullanırsanız.

## <a name="view-details-for-allowselfservicepurchase"></a>AllowSelfServicePurchase için ayrıntıları görüntüleme

Kuruluşa bağlı olarak **AllowSelfServicePurchase** parametre değerinin ve varsayılan durumunun açıklamasını görüntülemek için aşağıdaki komutu çalıştırın:

```powershell
Get-MSCommercePolicy -PolicyId AllowSelfServicePurchase
```

## <a name="view-a-list-of-self-service-purchase-products-and-their-status"></a>Self servis satın alınan ürünlerin listesini ve durumlarını görüntüleme

Kullanılabilir tüm self servis satın alma ürünlerinin listesini ve her bir ürünle ilgili durumu görüntülemek için aşağıdaki komutu çalıştırın:

```powershell
Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase
```

Aşağıdaki tabloda, kullanılabilir ürünler ve bunların **ProductId'leri listelemektedir**.

| Ürün | ÜrünKimlik |
|-----------------------------|--------------|
| Power Apps başına bir değer | CFQ7TTC0KP0P |
| Power Automate başına bir değer | CFQ7TTC0KP0N |
| Power Automate RPA | CFQ7TTC0KXG6  |
| Power BI Premium (tek başına) | CFQ7TTC0KXG7  |
| Power BI Pro | CFQ7TTC0L3PB |
| Project Plan 1* | CFQ7TTC0HDB1 |
| Project Plan 3* | CFQ7TTC0HDB0 |
| Visio Plan 1* | CFQ7TTC0HD33 |
| Visio Plan 2* | CFQ7TTC0HD32 |
| Windows 365 Enterprise | CFQ7TTC0HHS9 |
| Windows 365 Business | CFQ7TTC0J203 |
| Windows Karma Avantajı olan Windows 365 İş | CFQ7TTC0HX99 |

*Bu kimlikler değişti. Eski kimlikleri kullanan ürünleri daha önce engelle ettiysanız, yeni kimlikler kullanılarak bunlar otomatik olarak engellenir. Ek çalışma gerekmez.

## <a name="view-or-set-the-status-for-allowselfservicepurchase"></a>AllowSelfServicePurchase durumunu görüntüleme veya ayarlama

Self servis satın alma için kullanılabilen ürünlerin listesini görüntüledikten sonra, belirli bir ürünün ayarını ekleyebilirsiniz veya değiştirebilirsiniz.

Belirli bir ürünün ilke ayarını almak için aşağıdaki komutu çalıştırın:

```powershell
Get-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N
```

Belirli bir ürünün ilke ayarını etkinleştirmek için aşağıdaki komutu çalıştırın:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N -Enabled $True
```

Belirli bir ürünün ilke ayarını devre dışı bırakmak için aşağıdaki komutu çalıştırın:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId CFQ7TTC0KP0N -Enabled $False
```

## <a name="example-script-to-disable-allowselfservicepurchase"></a>AllowSelfServicePurchase'i devre dışı bırakmak için örnek betik

Aşağıdaki örnek, **MSCommerce** modülünü içeri aktarma, hesabınızla oturum açma, Power Automate için **ProductId'yi** alma ve sonra bu ürün için **AllowSelfServicePurchase'i** devre dışı bırakma adımları boyunca size yol sağlar.

```powershell
Import-Module -Name MSCommerce
Connect-MSCommerce #sign-in with your global or billing administrator account when prompted
$product = Get-MSCommerceProductPolicies -PolicyId AllowSelfServicePurchase | where {$_.ProductName -match 'Power Automate'}
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product.ProductID -Enabled $false
```

Ürün için birden çok değer varsa, aşağıdaki örnekte gösterildiği gibi her değer için komutu tek tek çalıştırabilirsiniz:

```powershell
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product[0].ProductID -Enabled $false
Update-MSCommerceProductPolicy -PolicyId AllowSelfServicePurchase -ProductId $product[1].ProductID -Enabled $false
```


## <a name="troubleshooting"></a>Sorun giderme

### <a name="problem"></a>Sorun

Aşağıdaki hata iletisini görüyorsunuz:

> HandleError: PolicyId 'AllowSelfServicePurchase', ErrorMessage ile ilke alınamadı - Temel bağlantı kapatıldı: Gönderme sırasında beklenmeyen bir hata oluştu.

Bunun nedeni Aktarım Katmanı Güvenliği'nin (TLS) eski bir sürümü olabilir. Bu hizmeti bağlamak için TLS 1.2 veya daha büyük bir değer kullan

### <a name="solution"></a>Çözüm

TLS 1.2'ye yükseltin. Aşağıdaki söz dizimi ServicePointManager Güvenlik Protokolü'ünü TLS1.2 olarak ler:

```powershell
 [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.SecurityProtocolType]::Tls12
```

Daha fazla bilgi için bkz [. TLS 1.2'yi etkinleştirme](/mem/configmgr/core/plan-design/security/enable-tls-1-2).

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
