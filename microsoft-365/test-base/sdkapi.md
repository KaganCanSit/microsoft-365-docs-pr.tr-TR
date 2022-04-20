---
title: Temel API & SDK'sını test edin
description: Temel API & SDK'sını test edin
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
ms.openlocfilehash: 14bfa8711d5cff46b8cce02950c087844384b9f9
ms.sourcegitcommit: e911dd506ea066795e418daf7b84c1e11381a21c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64953792"
---
# <a name="manage-your-resource-with-sdk--apis"></a>SDK & API'leri ile kaynağınızı yönetme

Otomasyon, DevOps ve çevik geliştirmenin önemli bir yönüdür. Microsoft 365 kaynakları için Test Tabanı'nı yönetmek, test sonuçlarını program aracılığıyla almak ve ci araçlarımızla tümleştirmek mi istiyorsunuz? Test Temel API'leri/SDK'ları tüm bunları ve daha fazlasını başarmanıza yardımcı olabilir!

Bu API'ler/SDK, BT uzmanlarının ve uygulama geliştiricilerinin şunları yapmasını sağlar:

- Oluşturma, güncelleştirme ve çıkarma dahil olmak üzere Test Temeli hesaplarını yönetin.
- Paket oluşturma, güncelleştirme, silme ve indirme dahil olmak üzere uygulama paketlerini yönetin.
- Test özetini, ayrıntılı test sonuçlarını ve analiz sonuçlarını alın. Analiz sonucu CPU regresyon analizini, CPU kullanım analizini, bellek regresyon analizini ve bellek kullanım analizini içerir.
- Test sonuçlarını ve test yürütme video kaydını indirin.

Microsoft 365 hizmeti için Test Temeli'nde bu yeni özelliğe nasıl erişeceklerini öğrenmek için aşağıdaki adım adım ana hattı gözden geçirin.

## <a name="a-step-by-step-example-of-test-base-account-creation-by-using-python-sdk"></a>Python SDK'sını kullanarak Test Temeli hesabı oluşturmaya adım adım bir örnek

1. Önkoşullar:

   - Aşağıdaki gerekli bileşenleri yükleyin:

     - Aboneliğiniz yoksa [etkin aboneliği olan Azure hesabı](https://azure.microsoft.com/free/?utm_source=campaign&utm_campaign=python-dev-center&mktingSource=environment-setup)
     - [Python 2.7+ veya 3.6+](https://www.python.org/downloads)
     - [Azure Command-Line Arabirimi (CLI)](/cli/azure/install-azure-cli)

   - Konsoldan pip yüklemesini kullanarak kitaplık paketlerini yükleme

     ```console
     pip install azure-identity
     pip install azure-mgmt-testbase
     ```

   - Geliştirme ortamında kimlik doğrulaması

     Yerel olarak kod hatalarını ayıklarken ve yürütürken, geliştiricilerin Azure hizmetlerine yönelik çağrıların kimliğini doğrulamak için kendi hesaplarını kullanması normaldir. azure-identity paketi, yerel geliştirmeyi basitleştirmek için Azure CLI aracılığıyla kimlik doğrulamayı destekler. Azure CLI'da oturum açmak için komutunu çalıştırın `az login`. Varsayılan web tarayıcısına sahip bir sistemde Azure CLI, kullanıcının kimliğini doğrulamak için tarayıcıyı başlatır.

     [Azure hizmetleriyle Python uygulamalarının kimliğini doğrulama'ya bakın| Microsoft Docs](/azure/developer/python/azure-sdk-authenticate) ve <https://pypi.org/project/azure-identity/> diğer desteklenen kimlik doğrulama yöntemleri için.

   - Aşağıdaki adımlarda kullanılacak istediğiniz ada sahip bir Kaynak Grubu oluşturun.

2. Aşağıdaki kod parçacığı, dahil olmak üzere bir Test Temel Hesabı oluşturmak için akışı kapsar

   - Azure ILE etkileşim için Azure CLI aracılığıyla kimlik bilgisi isteme
   - Test Temel SDK istemcisini daha sonraki işlemler için kimlik bilgileri ve abonelik kimliğiyle başlatın
   - Test Temel Hesabı oluşturmak için test_base_accounts modelden begin_create çağırma

   Kodu Python geliştirme ortamınıza kopyalayın ve "subscription-id" yerine Azure abonelik kimliğinizi ve "resource-group-name" yerine yukarıda oluşturduğunuz Kaynak Grubunuz yazın.

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

SDK & API hakkında daha fazla bilgi edinmek için aşağıdaki bağlantılara bakın.

**Azure Aboneliği**:

- [Etkin aboneliği olan Azure hesabı](https://azure.microsoft.com/free/?utm_source=campaign&utm_campaign=python-dev-center&mktingSource=environment-setup)

**Python SDK'sı**:

- [Test Temeli Python SDK'sı Belgeleri](/python/api/overview/azure/mgmt-testbase-readme)
- [Test Temeli Python SDK Örneği](https://aka.ms/testbase-sample-py)
- [Python SDK'sının Azure Genel Kullanım Düzeni](/azure/developer/python/azure-sdk-overview#provision-and-manage-azure-resources-with-management-libraries)

**REST API**:

- [REST API Belgeleri](https://aka.ms/testbase-api)
