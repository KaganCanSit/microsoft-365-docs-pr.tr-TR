---
title: DAP iş ortakları için etki alanı, Windows PowerShell kiraya ekleme
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
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
ms.assetid: f49b4d24-9aa0-48a6-95dd-6bae9cf53d2c
description: "Özet: Mevcut bir müşteri kiracısına Microsoft 365 etki alanı adı eklemek için PowerShell for Microsoft 365'i kullanın."
ms.openlocfilehash: 1a121407ebe242747a693084289e972e56e1cbee
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973848"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>Temsilci Erişim İzni (DAP) iş ortakları için Windows PowerShell hesabı olan bir istemci kiraya etki alanı ekleme

*Bu makale hem Yeni hem de Microsoft 365 Kurumsal için Office 365 Kurumsal.*

Yeni etki alanlarını daha hızlı bir şekilde kullanmak yerine, yeni etki alanlarını daha hızlı bir şekilde Microsoft 365 için PowerShell'in kirala Microsoft 365 yönetim merkezi.

Temsilcili Erişim İzni (DAP) iş ortakları Dağıtım ve Bulut Çözümü Sağlayıcıları (CSP) İş Ortaklarıdır. Bunlar çoğunlukla diğer şirketlere yönelik ağ veya telekom sağlayıcılarıdır. Aboneliklerini Microsoft 365 kendi hizmet tekliflerinde paketler. Microsoft 365 aboneliği satarken, müşteri eğilimlerini yönetip raporlaymalarını sağlamak için müşteri eğilimlerini yönetme (AOBO) izinleri otomatik olarak yapılır.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

Bu konudaki yordamlar için[, Bağlan'a Microsoft 365 PowerShell'e bağlanmanız gerekir](connect-to-microsoft-365-powershell.md).

Ayrıca, iş ortağı kiracı yöneticisi kimlik bilgileriniz de gerekir.

Ayrıca aşağıdaki bilgilere de ihtiyacınız var:

- Müşterinizin istediği tam etki alanı adı (FQDN) gerekir.

- Müşterinin **TenantId'sına ihtiyacınız var**.

- FQDN'nin GoDaddy gibi bir İnternet etki alanı adı hizmeti (DNS) kayıt şirketine kaydedilmiş olması gerekir. Etki alanı adını genel olarak kaydetme hakkında daha fazla bilgi için bkz [. Etki alanı adı satın alma](../admin/get-help-with-domains/buy-a-domain-name.md).

- DNS kayıt şirketiniz için kayıtlı DNS bölgesine txt kaydının nasıl ekileceğini bilmek gerekir. TXT kaydını ekleme hakkında daha fazla bilgi için bkz. [Etki alanınıza bağlanmak için DNS kayıtları ekleme](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md). Bu yordamlar işe yaramadı mı? DNS kayıt şirketinizin yordamlarını bulmanız gerekir.

## <a name="create-domains"></a>Etki alanı oluşturma

 Müşterileriniz, varsayılan \<domain>.onmicrosoft.com etki alanının dünya için kurumsal kimliklerini temsil eden birincil etki alanı olduğundan, kirala ilişkilendirmek için başka etki alanları oluşturmanızı ister. Bu yordam, müşterinizin kira alanıyla ilişkilendirilmiş yeni bir etki alanı oluştururken size yol sağlar.

> [!NOTE]
> Bu işlemlerden bazıları gerçekleştirmek için, destek istediğiniz şirketlere yönetici erişimi ata ayarının Yönetici hesabının ayrıntılarda yer alan Yönetici  erişimi atama ayarı için oturum ataydığınız iş ortağı yönetici hesabının Tam yönetim <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a>. İş ortağı yöneticisi rollerini yönetme hakkında daha fazla bilgi için bkz. [İş Ortakları: Temsili yönetim teklif edin](https://go.microsoft.com/fwlink/p/?LinkId=532435).

### <a name="create-the-domain-in-azure-active-directory"></a>Etki alanını Azure Active Directory

Bu komut, etki alanını Azure Active Directory genel olarak kaydedilmiş etki alanıyla ilişkilendirmez. Bu, kuruluşlar için Microsoft Microsoft 365'de genel olarak kayıtlı bir etki alanının sahibi Microsoft 365 gelir.

```powershell
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

> [!NOTE]
> PowerShell Core, adı **Msol** Microsoft Azure Active Directory modül Windows PowerShell cmdlet'ler için Modül Desteklemez. Bu cmdlet'leri kullanmaya devam etmek için, tüm cmdlet'leri Windows PowerShell.

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>DNS TXT doğrulama kaydıyla ilgili verileri alma

 Microsoft 365 DNS TXT doğrulama kaydına eklemek için ihtiyacınız olan belirli verileri üretir. Verileri almak için bu komutu çalıştırın.

```powershell
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

Bu size şu şekilde çıkış sağlar:

 `Label: domainname.com`

 `Text: MS=ms########`

 `Ttl: 3600`

> [!NOTE]
> Genel olarak kaydedilmiş DNS bölgesinde TXT kaydını oluşturmak için bu metne ihtiyacınız vardır. Dosyayı kopyalayıp kaydetmeye emin olun.

### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>Genel olarak kaydedilmiş DNS bölgesine TXT kaydı ekleme

Bu Microsoft 365 genel olarak kaydedilmiş etki alanı adına yönlendirilen trafiği kabul etmeye başlamadan önce, etki alanına sahip ve yönetici izinlerine sahip olamanız gerekir. Etki alanında bir TXT kaydı oluşturarak etki alanının sahibi olduğunu kanıtlarsiniz. TXT kaydı etki alanınız içinde hiçbir şey yapmaz ve etki alanı sahipliğiniz belirlendikten sonra silinebilir. TXT kayıtlarını oluşturmak için, Etki alanınıza bağlanmak [için DNS kayıtları ekleme yordamlarını izleyin](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md). Bu yordamlar size uygunsa, DNS kayıt şirketi yordamlarını bulmanız gerekir.

nslookup yoluyla TXT kaydının başarıyla oluşturulmasını onaylayın. Aşağıdaki söz dizimlerini izleyin.

```console
nslookup -type=TXT <FQDN of registered domain>
```

Bu size şu şekilde çıkış sağlar:

 `Non-authoritative answer:`

 `FQDN of the registered domain`

 `text=MS=ms########`

### <a name="validate-domain-ownership-in-microsoft-365"></a>E-postada etki alanı sahipliğini Microsoft 365

Bu son adımda, genel olarak kayıtlı Microsoft 365 etki alanının sahibi olduğunu doğrulamanız gerekir. Bu adımdan Microsoft 365, yeni etki alanı adına yönlendirilen trafiği kabul etmeye başlar. Etki alanı oluşturma ve kayıt işlemini tamamlamak için bu komutu çalıştırın.

```powershell
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Bu komut hiçbir çıktı geri dönmez, bu nedenle bu komutu çalıştırarak çalıştığını onaylayın.

```powershell
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Bu, buna benzer bir şey

```console
Name                   Status      Authentication
--------------------   ---------   --------------
FQDN of new domain     Verified    Managed
```

## <a name="see-also"></a>Ayrıca bkz.

[İş ortakları için yardım](https://go.microsoft.com/fwlink/p/?LinkID=533477)
