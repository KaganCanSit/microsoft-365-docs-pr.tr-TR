---
title: Test Temel API & SDK
description: Test Temel API & SDK
search.appverid: MET150
author: mansipatel-usl
ms.author: mapatel
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: f7e5edeeac79b417bcb41f8607c46fc8894ea4fc
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "63005487"
---
# <a name="manage-your-resource-with-sdk--apis"></a>SDK ve API'lerle & yönetme
Otomasyon, otomasyon ve çevik DevOps önemli bir yönüdür. Test Bankası'nın kaynak Microsoft 365 yönetmek, test sonuçlarını programatik olarak almak ve bunları CI araçlarımız ile tümleştirecek misiniz? Test Temel API'leri/SDK tüm bunları ve daha fazlasını başarmanıza yardımcı olabilir! 

Bu API'ler/SDK, BT uzmanlarının ve uygulama geliştiricilerinin şunları şunları uygulamasını sağlar: 
- Test Tabanı hesaplarını oluşturun, güncelleştirin ve çıkararak yönetin. 
- Paket oluşturma, güncelleştirme, silme ve indirme de içinde olmak üzere uygulama paketlerini yönetin. 
- Test özetini, ayrıntılı test sonuçlarını ve çözümleme sonuçlarını elde etmek. Çözümleme sonucu; CPU regresyon çözümlemesi, CPU kullanımı çözümlemesi, bellek regresyon çözümlemesi ve bellek kullanımı çözümlemesini içerir. 
- Test sonuçlarını indirin ve video yürütme video kaydını test edin.  

Bir hizmet için Test Temel'de bu yeni beceriye nasıl erişebilirsiniz, aşağıda adım adım ana Microsoft 365 bulabilirsiniz.

## <a name="a-step-by-step-example-of-test-base-account-creation-by-using-python-sdk"></a>Python SDK kullanarak Test Temel hesabı oluşturma işlemi için adım adım bir örnek

1. Önkoşullar: 

- Aşağıdaki gerekli bileşenleri yükleyin: 

    [Aboneliğiniz yoksa etkin](https://azure.microsoft.com/free/?utm_source=campaign&utm_campaign=python-dev-center&mktingSource=environment-setup) bir aboneliğe sahip Azure hesabı<br>
    [Python 2.7+ veya 3.6+](https://www.python.org/downloads)<br>
    [Azure Command-Line Arabirimi (CLI)](/cli/azure/install-azure-cli) <br>

- Konsoldan pip yükleme kullanarak kitaplık paketlerini yükleme 

```
pip install azure-identity 
pip install azure-mgmt-testbase
```

- Geliştirme ortamında kimlik doğrulama 

Kod yerel olarak hata ayıklama ve yürütme sırasında geliştiricilerin Azure hizmetlerinde yapılan aramaları kimlik doğrularken kendi hesaplarını kullanmaları normaldir. Azure kimlik paketi, yerel geliştirmeyi basitleştirmek için Azure CLI aracılığıyla kimlik doğrulamayı destekler. Azure CLI'da oturum açma için, çalıştırın ```az login ```. Varsayılan web tarayıcısı olan bir sistemde, Azure CLI kullanıcının kimliğini doğrulamak için tarayıcıyı başlatacak. 

[Azure hizmetleriyle Python uygulamalarının kimliğini doğrulamayı öğrenin| Microsoft Docs ve](/azure/developer/python/azure-sdk-authenticate) [https://pypi.org/project/azure-identity/](https://pypi.org/project/azure-identity/) desteklenen diğer kimlik doğrulama yöntemleri için. 

 - İstediğiniz adla, aşağıdaki adımlarda kullanılacak bir Kaynak Grubu oluşturun. 

2. Aşağıdaki kod parçacığının altında, aşağıdakiler de dahil olmak üzere bir Test Temel Hesabı oluşturmak için akışı bulabilirsiniz. 

- Azure ile etkileşim için Azure CLI aracılığıyla kimlik bilgisi isteği 
- Daha sonraki işlemler için kimlik bilgileri ve abonelik kimliğiyle Test Temel SDK istemcisini başlatma 
- Test begin_create test_base_accounts için test_base_accounts modelinden invoke e-postası 

Kodu Python geliştirme ortamınıza kopyalayın ve "subscription-id" yerine Azure abonelik kimliğinizi ve "resource-group-name" ifadesini yukarıda oluşturduğunuz Kaynak Grubunuzla değiştirin. 

 
```python

from azure.identity import AzureCliCredential
from azure.mgmt.testbase import TestBase
from azure.mgmt.testbase.models import TestBaseAccountResource
from azure.mgmt.testbase.models import TestBaseAccountSKU

# requesting token from Azure CLI for request
# For other authentication approaches, please see: https://pypi.org/project/azure-identity/
credential = AzureCliCredential()
subscription_id = "<subscription-id>"
resource_group = "<resource-group-name>"
testBaseAccount_name = "contoso-testbaseAccount"
testBaseAccount_location = "global"
sku_name = "S0"
sku_tier = "Standard"
sku_locations = {"global"}

# Create client
testBase_client = TestBase(credential, subscription_id)

# Create sku for test base account
sku = TestBaseAccountSKU(name=sku_name, tier=sku_tier, locations=sku_locations)

# Create test base account
parameters = TestBaseAccountResource(location=testBaseAccount_location, sku=sku)
testBaseAccount = testBase_client.test_base_accounts.begin_create(resource_group, testBaseAccount_name, parameters).result()
print("Create test base account:\n{}".format(testBaseAccount))

```


## <a name="learn-more"></a>Daha fazla bilgi 

SDK özellikleri ve API'si hakkında daha fazla bilgi edinmek & bakın. 

**Azure Aboneliği** 

- [Etkin bir aboneliğe sahip Azure hesabı](https://azure.microsoft.com/free/?utm_source=campaign&utm_campaign=python-dev-center&mktingSource=environment-setup)

**Python SDK** 

- [Temel Python SDK Belgelerini test edin](/python/api/overview/azure/mgmt-testbase-readme)
- [Temel Python SDK Örneği](https://aka.ms/testbase-sample-py)
- [Python SDK'nin Azure Genel Kullanım Deseni](/azure/developer/python/azure-sdk-overview#provision-and-manage-azure-resources-with-management-libraries)

**REST API**  

- [REST API Belgeleri](https://aka.ms/testbase-api)  
