---
title: DAP iş ortakları için Windows PowerShell ile istemci kiracısına etki alanı ekleme
ms.author: kvice
author: kelleyvice-msft
manager: scotv
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
description: 'Özet: Mevcut bir müşteri kiracısına alternatif bir etki alanı adı eklemek için Microsoft 365 için PowerShell kullanın.'
ms.openlocfilehash: c4dcdb34f9065009ccaa77d23222601506b537b5
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099048"
---
# <a name="add-a-domain-to-a-client-tenancy-with-windows-powershell-for-delegated-access-permission-dap-partners"></a>TemsilciLi Erişim İzni (DAP) iş ortakları için Windows PowerShell ile istemci kiracısına etki alanı ekleme

*Bu makale hem Microsoft 365 Kurumsal hem de Office 365 Kurumsal için geçerlidir.*

Microsoft 365 yönetim merkezi kullanmaktan daha hızlı Microsoft 365 için yeni etki alanları oluşturabilir ve müşterinizin kiracısıyla PowerShell ile ilişkilendirebilirsiniz.

Temsilci Erişim İzni (DAP) iş ortakları, Dağıtım ve Bulut Çözümü Sağlayıcıları (CSP) İş Ortaklarıdır. Bunlar genellikle diğer şirketlerin ağ veya telekom sağlayıcılarıdır. Microsoft 365 aboneliklerini müşterilerine sunulan hizmet tekliflerine paketlemektedir. bir Microsoft 365 aboneliği sattıklarında, müşteri kiracılarını yönetebilmeleri ve raporlamaları için otomatik olarak müşteri kiracılarına Adına Yönetme (AOBO) izinleri verilir.
## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

Bu konudaki yordamlar[, PowerShell ile Microsoft 365 için Bağlan](connect-to-microsoft-365-powershell.md) bağlanmanızı gerektirir.

Ayrıca iş ortağı kiracı yöneticisi kimlik bilgilerinize de ihtiyacınız vardır.

Ayrıca aşağıdaki bilgilere de ihtiyacınız vardır:

- Müşterinizin istediği tam etki alanı adına (FQDN) ihtiyacınız vardır.

- Müşterinin **TenantId** değeri gerekir.

- FQDN, GoDaddy gibi bir İnternet etki alanı adı hizmeti (DNS) kayıt şirketine kayıtlı olmalıdır. Bir etki alanı adını genel olarak kaydetme hakkında daha fazla bilgi için bkz. [Etki alanı adı satın alma](../admin/get-help-with-domains/buy-a-domain-name.md).

- DNS kayıt şirketiniz için kayıtlı DNS bölgesine txt kaydının nasıl ekleneceğini bilmeniz gerekir. TXT kaydı ekleme hakkında daha fazla bilgi için bkz. [Etki alanınıza bağlanmak için DNS kayıtları ekleme](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md). Bu yordamlar sizin için işe yaramazsa, DNS kayıt şirketiniz için yordamları bulmanız gerekir.

## <a name="create-domains"></a>Etki alanı oluşturma

 Müşterileriniz, varsayılan \<domain>.onmicrosoft.com etki alanının şirket kimliklerini dünyaya temsil eden birincil etki alanı olmasını istemediklerinden, kiracılarıyla ilişkilendirmek için büyük olasılıkla ek etki alanları oluşturmanızı isteyecektir. Bu yordam, müşterinizin kiracısıyla ilişkili yeni bir etki alanı oluşturma konusunda size yol gösterir.

> [!NOTE]
> Bu işlemlerden bazılarını gerçekleştirmek için, Microsoft 365 yönetim merkezi yönetici hesabının ayrıntılarında bulunan **Desteklediğiniz şirketlere yönetim erişimi ata** ayarı için oturum açabileceğiniz iş ortağı yönetici hesabının **Tam yönetim** olarak ayarlanması <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">gerekir.</a> İş ortağı yöneticisi rollerini yönetme hakkında daha fazla bilgi için bkz [. İş ortakları: Temsilcili yönetim teklifi](https://go.microsoft.com/fwlink/p/?LinkId=532435).

### <a name="create-the-domain-in-azure-active-directory"></a>etki alanını Azure Active Directory'de oluşturma

Bu komut etki alanını Azure Active Directory oluşturur ancak genel olarak kayıtlı etki alanıyla ilişkilendirmez. Bu, kuruluşlar için Microsoft Microsoft 365 genel olarak kayıtlı etki alanının sahibi olduğunuzu kanıtladığınızda ortaya çıkar.

```powershell
New-MsolDomain -TenantId <customer TenantId> -Name <FQDN of new domain>
```

> [!NOTE]
> PowerShell Core, Windows PowerShell modülü için Microsoft Azure Active Directory Modülünü ve adında **Msol** bulunan cmdlet'leri desteklemez. Bu cmdlet'leri kullanmaya devam etmek için bunları Windows PowerShell çalıştırmanız gerekir.

### <a name="get-the-data-for-the-dns-txt-verification-record"></a>DNS TXT doğrulama kaydı için verileri alma

 Microsoft 365, DNS TXT doğrulama kaydına yerleştirmeniz gereken belirli verileri oluşturur. Verileri almak için bu komutu çalıştırın.

```powershell
Get-MsolDomainVerificationDNS -TenantId <customer TenantId> -DomainName <FQDN of new domain> -Mode DnsTxtRecord
```

Bu size aşağıdaki gibi bir çıkış verir:

 `Label: domainname.com`

 `Text: MS=ms########`

 `Ttl: 3600`

> [!NOTE]
> Genel olarak kayıtlı DNS bölgesinde TXT kaydını oluşturmak için bu metne ihtiyacınız olacaktır. Kopyalayıp kaydettiğinizden emin olun.

### <a name="add-a-txt-record-to-the-publically-registered-dns-zone"></a>Genel olarak kayıtlı DNS bölgesine TXT kaydı ekleme

Microsoft 365 genel olarak kayıtlı etki alanı adına yönlendirilen trafiği kabul etmeye başlamadan önce, etki alanına sahip olduğunuzu ve etki alanı üzerinde yönetici izinlerine sahip olduğunuzu kanıtlamanız gerekir. Etki alanında bir TXT kaydı oluşturarak etki alanının sahibi olduğunuzu kanıtlarsınız. TXT kaydı etki alanınızda hiçbir şey yapmaz ve etki alanı sahipliğiniz oluşturulduktan sonra silinebilir. TXT kayıtlarını oluşturmak için ETKI [alanınıza bağlanmak için DNS kayıtları ekleme](../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) başlığı altında yer alan yordamları izleyin. Bu yordamlar sizin için işe yaramazsa, DNS kayıt şirketiniz için yordamları bulmanız gerekir.

nslookup aracılığıyla TXT kaydının başarıyla oluşturulduğundan emin olun. Bu söz dizimlerini izleyin.

```console
nslookup -type=TXT <FQDN of registered domain>
```

Bu size aşağıdaki gibi bir çıkış verir:

 `Non-authoritative answer:`

 `FQDN of the registered domain`

 `text=MS=ms########`

### <a name="validate-domain-ownership-in-microsoft-365"></a>Microsoft 365'de etki alanı sahipliğini doğrulama

Bu son adımda, genel olarak kayıtlı etki alanının sahibi olduğunuzu Microsoft 365 doğrularsınız. Bu adımdan sonra, Microsoft 365 yeni etki alanı adına yönlendirilen trafiği kabul etmeye başlar. Etki alanı oluşturma ve kayıt işlemini tamamlamak için bu komutu çalıştırın.

```powershell
Confirm-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Bu komut herhangi bir çıkış döndürmez, bu nedenle bunun çalıştığını onaylamak için bu komutu çalıştırın.

```powershell
Get-MsolDomain -TenantId <customer TenantId> -DomainName <FQDN of new domain>
```

Bu, şuna benzer bir şey döndürür

```console
Name                   Status      Authentication
--------------------   ---------   --------------
FQDN of new domain     Verified    Managed
```

## <a name="see-also"></a>Ayrıca bkz.

[İş ortakları için yardım](https://go.microsoft.com/fwlink/p/?LinkID=533477)
