---
title: Azure'da şifreleme
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.collection:
- Strat_O365_Enterprise
- M365-security-compliance
- Strat_O365_Enterprise
description: Azure Disk Şifrelemesi gibi Azure'da kullanılabilen şifreleme hakkında bilgi edinin
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 66fb4e54c0837534d6943372d84cf3a4864e4739
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632189"
---
# <a name="encryption-in-azure"></a>Azure'da şifreleme

Şifrelenmiş iletişimler ve operasyonel süreçler gibi Azure'daki teknolojik güvenlik önlemleri verilerinizin güvenliğini sağlamaya yardımcı olur. Ayrıca ek şifreleme özellikleri uygulama ve kendi şifreleme anahtarlarınızı yönetme esnekliğine de sahipsiniz. Müşteri yapılandırmasından bağımsız olarak Microsoft, Azure'daki müşteri verilerini korumak için şifreleme uygular. Microsoft ayrıca şifreleme anahtarlarını şifrelemek, denetlemek ve yönetmek, verilere erişimi denetlemek ve denetlemek için çeşitli gelişmiş teknolojiler aracılığıyla Azure'da barındırılan verilerinizi denetlemenizi sağlar. Ayrıca Azure Depolama, geliştiricilerin güvenli uygulamalar oluşturmasına olanak tanıyan kapsamlı bir güvenlik özellikleri kümesi sağlar.

Azure, verileri bir konumdan diğerine taşırken korumaya yönelik birçok mekanizma sunar. Microsoft, bulut hizmetleriyle müşteriler arasında seyahat ederken verileri korumak için TLS kullanır. Microsoft'un veri merkezleri, Azure hizmetlerine bağlanan istemci sistemleriyle BIR TLS bağlantısı kurar. Perfect Forward Secrecy (PFS), müşterilerin istemci sistemleriyle Microsoft'un bulut hizmetleri arasındaki bağlantıları benzersiz anahtarlarla korur. Bağlantılar ayrıca RSA tabanlı 2.048 bit şifreleme anahtarı uzunluklarını da kullanır. Bu birleşim, birinin aktarımdaki verileri kesmesini ve verilere erişmesini zorlaştırır.

Veriler [istemci tarafı şifreleme](/azure/storage/storage-client-side-encryption), HTTPS veya SMB 3.0 kullanılarak uygulama ile Azure arasında aktarım sırasında güvenli hale getirilebilir. Kendi sanal makineleriniz (VM) ile kullanıcılarınız arasındaki trafik için şifrelemeyi etkinleştirebilirsiniz. [Azure Sanal Ağları](https://azure.microsoft.com/services/virtual-network/) ile kurumsal VPN ağ geçidinizle Azure arasındaki trafiği şifrelemek ve Sanal Ağ bulunan VM'ler arasındaki trafiği şifrelemek için endüstri standardı IPsec protokollerini kullanabilirsiniz.

Bekleyen veriler için Azure, AES-256 desteği gibi birçok şifreleme seçeneği sunarak ihtiyaçlarınıza en uygun veri depolama senaryolarını seçme esnekliği sunar. Veriler [Depolama Hizmeti Şifrelemesi](/azure/storage/storage-service-encryption) kullanılarak Azure Depolama'ya yazıldığında otomatik olarak şifrelenebilir ve VM'ler tarafından kullanılan işletim sistemi ve veri diskleri şifrelenebilir. Daha fazla bilgi için bkz. [Azure'da Windows sanal makineleri için güvenlik önerileri](/azure/security/azure-security-disk-encryption). Ayrıca, Azure Depolama'daki veri nesnelerine temsilci erişimi [, Paylaşılan Erişim İmzaları](/azure/storage/storage-dotnet-shared-access-signature-part-1) kullanılarak verilebilir. Azure ayrıca [Azure SQL Veritabanı ve Data Warehouse için Saydam Veri Şifrelemesi](/sql/relational-databases/security/encryption/transparent-data-encryption-azure-sql) kullanarak bekleyen veriler için şifreleme sağlar.

Azure'da şifreleme hakkında daha fazla bilgi için bkz. [Azure şifrelemeye genel bakış](/azure/security/security-azure-encryption-overview) ve [Bekleyen Azure Veri Şifrelemesi](/azure/security/azure-security-encryption-atrest).

## <a name="azure-disk-encryption"></a>Azure Disk Şifrelemesi

Azure Disk Şifrelemesi, Windows ve Linux Hizmet Olarak Altyapı (IaaS) VM disklerinizi şifrelemenize olanak tanır. Azure Disk Şifrelemesi, işletim sistemi ve veri diskleri için birim düzeyinde şifreleme sağlamak üzere Windows'un BitLocker özelliğinden ve Linux'un DM-Crypt özelliğinden yararlanıyor. Ayrıca VM disklerindeki tüm verilerin Azure depolama alanınızda bekleyen konumda şifrelenmesini sağlar. Azure Disk Şifrelemesi, şifreleme anahtarlarının ve gizli dizilerinin kullanımını denetlemenize, yönetmenize ve denetlemenize yardımcı olmak için Azure Key Vault ile tümleşiktir.

Daha fazla bilgi için bkz. [Azure'da Windows sanal makineleri için güvenlik önerileri](/azure/virtual-machines/windows/security-recommendations).

## <a name="azure-storage-service-encryption"></a>Azure Depolama Hizmeti Şifrelemesi

[Azure Depolama Hizmeti Şifrelemesi](/azure/storage/storage-service-encryption) ile Azure Depolama, verileri depolamada kalıcı hale getirmeden önce otomatik olarak şifreler ve veri alınmadan önce verilerin şifresini çözer. Şifreleme, şifre çözme ve anahtar yönetimi işlemleri kullanıcılar için tamamen saydamdır. Azure Depolama Hizmeti Şifrelemesi [Azure Blob Depolama](https://azure.microsoft.com/services/storage/blobs/) ve [Azure Dosyalar](https://azure.microsoft.com/services/storage/files/) için kullanılabilir. Azure Depolama Hizmeti Şifrelemesi ile Microsoft tarafından yönetilen şifreleme anahtarlarını veya kendi şifreleme anahtarlarınızı da kullanabilirsiniz. (Kendi anahtarlarınızı kullanma hakkında bilgi için bkz. [Azure Key Vault'de müşteri tarafından yönetilen anahtarları kullanarak Depolama Hizmeti Şifrelemesi](/azure/storage/common/storage-service-encryption-customer-managed-keys). Microsoft tarafından yönetilen anahtarları kullanma hakkında bilgi için bkz. [Bekleyen Veriler için Depolama Hizmeti Şifrelemesi](/azure/storage/storage-service-encryption).) Ayrıca, şifreleme kullanımını otomatikleştirebilirsiniz. Örneğin, [Azure Depolama Kaynak Sağlayıcısı REST API'sini](/rest/api/storagerp/), .NET, [Azure PowerShell](/powershell/azureps-cmdlets-docs) veya [Azure CLI](/azure/storage/storage-azure-cli) [için Depolama Kaynak Sağlayıcısı İstemci Kitaplığı'nı](/dotnet/api/overview/azure/storage) kullanarak depolama hesabında Depolama Hizmeti Şifrelemesi'ni program aracılığıyla etkinleştirebilir veya devre dışı bırakabilirsiniz.

Bazı Microsoft 365 hizmetleri verileri depolamak için Azure kullanır. Örneğin, SharePoint Online ve OneDrive İş verileri Azure Blob depolama alanında depolar ve Microsoft Teams sohbet hizmeti verilerini tablolarda, bloblarda ve kuyruklarda depolar. Ayrıca, Microsoft Purview uyumluluk portalı Uyumluluk Yöneticisi özelliği, müşteri tarafından girilen verileri depolar ve bu veriler Hizmet Olarak Platform (PaaS), genel olarak dağıtılmış, çok modelli veritabanı olan [Azure Cosmos DB'de](/azure/cosmos-db/database-encryption-at-rest) şifrelenmiş biçimde depolanır. Azure Depolama Hizmeti Şifrelemesi, Azure Blob depolamada ve tablolarda depolanan verileri şifreler ve Azure Disk Şifrelemesi kuyruklardaki verilerin yanı sıra Windows ve IaaS sanal makine disklerini de şifreleyerek işletim sistemi ve veri diski için birim şifrelemesi sağlar. Çözüm, sanal makine disklerindeki tüm verilerin Azure depolama alanınızda bekleyen konumda şifrelenmesini sağlar. [Azure Cosmos DB'de bekleyen şifreleme](/azure/cosmos-db/database-encryption-at-rest) , güvenli anahtar depolama sistemleri, şifrelenmiş ağlar ve şifreleme API'leri gibi çeşitli güvenlik teknolojileri kullanılarak uygulanır.

## <a name="azure-key-vault"></a>Azure Key Vault

Güvenli anahtar yönetimi yalnızca şifreleme için en iyi yöntemlerin temeli değildir; ayrıca buluttaki verileri korumak için de gereklidir. [Azure Key Vault](/azure/key-vault/key-vault-whatis), anahtarları ve donanım güvenlik modüllerinde (HSM) depolanan anahtarları kullanan parolalar gibi küçük gizli dizileri şifrelemenize olanak tanır. Azure Key Vault, Microsoft'un bulut hizmetleri tarafından kullanılan şifreleme anahtarlarına erişimi yönetmek ve denetlemek için önerdiği çözümdür. Anahtarlara erişim izinleri hizmetlere veya Azure Active Directory hesaplarına sahip kullanıcılara atanabilir. Azure Key Vault, kuruluşların HSM'leri ve anahtar yönetim yazılımını yapılandırma, düzeltme eki uygulama ve bakımını yapma gereksinimini giderir. Azure Key Vault ile Microsoft anahtarlarınızı hiçbir zaman görmez ve uygulamaların bunlara doğrudan erişimi yoktur; denetimi siz korursunuz. Ayrıca HSM'lerde anahtarları içeri aktarabilir veya oluşturabilirsiniz. Azure Information Protection içeren bir aboneliği olan kuruluşlar, Azure Information Protection kiracılarını müşteri tarafından yönetilen bir Anahtarı [Kendi Anahtarını Getir](/information-protection/plan-design/byok-price-restrictions) (BYOK) kullanacak şekilde yapılandırabilir ve [kullanımını günlüğe kaydedebilir](/information-protection/deploy-use/log-analyze-usage).
