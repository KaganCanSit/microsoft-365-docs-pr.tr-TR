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
description: Azure'da kullanılabilen Azure Disk Şifrelemesi gibi şifreleme hakkında bilgi edinin
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f3672800b6f90277195a63b640911ea1ed24cac9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983229"
---
# <a name="encryption-in-azure"></a>Azure'da şifreleme

Şifreli iletişimler ve işlem süreçleri gibi Azure'daki gizli korumalar, verilerinizin güvenliğini korumaya yardımcı olur. Ayrıca, ek şifreleme özellikleri uygulama ve kendi şifreleme anahtarlarınızı yönetme esnekliğine de sahipsiniz. Müşteri yapılandırması ne olursa olsun, Microsoft Azure'da müşteri verilerini korumak için şifreleme uygular. Microsoft ayrıca şifreleme anahtarlarını şifrelemek, yönetmek ve yönetmek ve verilere erişimi denetlemek için bir dizi gelişmiş teknoloji aracılığıyla Azure'da barındırılan verilerinizi denetlemenize olanak sağlar. Buna ek olarak, Azure Depolama birlikte geliştiricilerin güvenli uygulamalar oluşturmasını sağlayan kapsamlı bir güvenlik özellikleri kümesi sağlar.

Azure, verileri bir konumdan diğerine taşırken korumak için birçok mekanizma sunar. Microsoft, bulut hizmetleriyle müşteriler arasında seyahat ederken verileri korumak için TLS kullanır. Microsoft'un veri merkezleri, Azure hizmetleriyle bağlantılı istemci sistemleriyle TLS bağlantısında görüşmede bulunmaktadır. Mükemmel İletme Gizliliği (PFS) müşterilerin istemci sistemleriyle Microsoft bulut hizmetleri arasındaki bağlantıları benzersiz anahtarlar ile korur. Bağlantılar RSA tabanlı 2.048 bit şifreleme anahtarı uzunluklarını da kullanır. Bu birleşim, geçişte olan verilerin önünü kesmesini ve bu verilere erişmesini zorlaştır.

İstemci tarafı şifreleme, HTTPS veya SMB 3.0 kullanılarak uygulama [](/azure/storage/storage-client-side-encryption)ile Azure arasında aktarım sırasında veriler güvenli hale alınabilir. Kendi sanal makineleriniz (SANAL MAKINELERI) ile kullanıcılarınız arasındaki trafik için şifrelemeyi etkinleştirebilirsiniz. [Azure Sanal Ağlar ile](https://azure.microsoft.com/services/virtual-network/) kurumsal VPN ağ geçidiniz ve Azure arasındaki trafiği ve Sanal Ağ'nızda yer alan sanal sanal makineler arasındaki trafiği şifrelemek için endüstri standardı III Protokolünü kullanabilirsiniz.

Azure, geriye kalan veriler için AES-256 desteği gibi birçok şifreleme seçeneği sunar ve size ihtiyaçları en iyi şekilde karşılayacak veri depolama senaryosunu seçme esnekliği sağlar. Azure Veritabanına yazıldığı zaman veriler Depolama Şifreleme kullanılarak Azure Depolama Depolama şifrelenir [](/azure/storage/storage-service-encryption)ve SANAL'lar tarafından kullanılan işletim sistemi ve veri diskleri şifrelenir. Daha fazla bilgi için bkz[. Azure'daki sanal Windows için güvenlik önerileri](/azure/security/azure-security-disk-encryption). Ayrıca, Paylaşılan Erişim İmzaları kullanılarak Azure Depolama veri nesnelerine [temsilciyle erişim de verebilirsiniz](/azure/storage/storage-dotnet-shared-access-signature-part-1). Azure ayrıca, depolama ve Veri Ambarı için Saydam Veri Şifrelemesi [kullanarak Azure SQL Veritabanı şifreleme sağlar](/sql/relational-databases/security/encryption/transparent-data-encryption-azure-sql).

Azure'da şifreleme hakkında daha fazla bilgi için bkz. Azure şifrelemeye [genel bakış](/azure/security/security-azure-encryption-overview) [ve Azure Veri Şifrelemesi-beklemede](/azure/security/azure-security-encryption-atrest).

## <a name="azure-disk-encryption"></a>Azure Disk Şifrelemesi

Azure Disk Şifrelemesi, Windows Linux Altyapınızı Hizmet (IaaS) VM diskleri olarak şifrelemenize olanak sağlar. Azure Disk Şifrelemesi, işletim sistemi ve veri diskleri için toplu Windows düzeyinde şifreleme sağlamak üzere Linux'un BitLocker özelliği ve Linux'un DM-Crypt özelliği kullanır. Ayrıca VM disklerdeki tüm verilerin Azure depolama alanınıza sabitlenirken şifrelenir. Azure Disk Şifrelemesi, şifreleme anahtarları ve sırlarının kullanımını denetlemeye, yönetmeye ve denetlemeye yardımcı olmak için Azure Anahtar Kasası ile tümleşiktir.

Daha fazla bilgi için bkz[. Azure'daki sanal Windows için güvenlik önerileri](/azure/virtual-machines/windows/security-recommendations).

## <a name="azure-storage-service-encryption"></a>Azure Depolama Hizmet Şifrelemesi

[Azure Depolama Hizmet](/azure/storage/storage-service-encryption) Şifrelemesi ile, Azure Depolama alma öncesinde verileri otomatik olarak şifreler ve alma öncesinde verilerin şifresini çözebilir. Şifreleme, şifre çözme ve anahtar yönetim süreçleri tamamen kullanıcılar için saydamdır. Azure Blob Depolama ve Azure Dosyaları için [Azure](https://azure.microsoft.com/services/storage/blobs/) Depolama [Şifrelemesi kullanılabilir](https://azure.microsoft.com/services/storage/files/). Ayrıca, Microsoft tarafından yönetilen şifreleme anahtarlarını Azure Depolama Şifreleme'de veya kendi şifreleme anahtarlarınızı da kullanabilirsiniz. (Kendi anahtarlarınızı kullanma hakkında bilgi için bkz. [azure Depolama Kasasında müşteri tarafından yönetilen anahtarların kullanılarak Hizmet Şifrelemesi.](/azure/storage/common/storage-service-encryption-customer-managed-keys) Microsoft tarafından yönetilen anahtarları kullanma hakkında bilgi için bkz. [Depolama Yerinde Veri Için Hizmet Şifrelemesi'ne bakın](/azure/storage/storage-service-encryption).) Buna ek olarak, şifreleme kullanımını otomatik hale de kullanabilirsiniz. Örneğin, [Azure Depolama Kaynak Sağlayıcısı REST API'si](/rest/api/storagerp/), [.NET](/dotnet/api/overview/azure/storage), [Azure PowerShell](/powershell/azureps-cmdlets-docs) veya [Azure CLI](/azure/storage/storage-azure-cli) için Depolama Kaynak Sağlayıcısı İstemci Kitaplığı'nın kullanımıyla bir depolama hesabında Depolama Hizmet Şifrelemesi'nin programlı olarak etkinleştirilebilir veya devre dışı bırakabilirsiniz.

Bazı Microsoft 365 hizmetleri verileri depolamak için Azure kullanır. Örneğin, SharePoint Online'a OneDrive İş Azure Blob depolama alanında veri depolar ve Microsoft Teams sohbet hizmetinin verilerini tablolar, bloblar ve kuyruklarda depolar. Buna ek olarak, Microsoft 365 uyumluluk merkezi'daki Uyumluluk Yöneticisi özelliği, müşteri tarafından girilen ve Hizmet Olarak Platform (PaaS), küresel olarak dağıtılmış, çok modelli veritabanı [Azure Cosmos DB'de](/azure/cosmos-db/database-encryption-at-rest) şifrelenmiş biçimde depolanan verileri depolar. Azure Depolama Hizmet Şifrelemesi, Azure Blob depolama alanında ve tablolarda depolanan verileri şifreler ve Azure Disk Şifrelemesi, işletim sistemi ve veri diskine toplu şifreleme sağlamak için kuyruklar arasındaki verilerin yanı sıra Windows ve IaaS sanal makine disklerini de şifreler. Çözüm, sanal makine diskleri üzerinde yer alan tüm verilerin Azure depolama alanınıza çözüm olarak şifrelenir. [Azure Cosmos DB'de](/azure/cosmos-db/database-encryption-at-rest) beklemede şifreleme, güvenli anahtar depolama sistemleri, şifrelenmiş ağlar ve şifreleme API'leri gibi çeşitli güvenlik teknolojileri kullanılarak uygulanır.

## <a name="azure-key-vault"></a>Azure Anahtar Kasası

Güvenli anahtar yönetimi yalnızca şifreleme en iyi yöntemleri için temel değildir; ayrıca buluttaki verileri korumak için de çok önemlidir. [Azure Anahtar Kasası](/azure/key-vault/key-vault-whatis) , donanım güvenlik modüllerinde (HSM) depolanan anahtarları kullanan anahtarları ve parolalar gibi küçük özellikleri şifrelemenıza olanak sağlar. Azure Anahtar Kasası, bulut hizmetleri tarafından kullanılan şifreleme anahtarlarına erişimi yönetmek ve denetlemek için Microsoft'un önerilen çözümüdür. Erişim tuşlarına yönelik izinler, hizmetlere veya aynı hesabı olan Azure Active Directory atanabilir. Azure Anahtar Kasası, kuruluşlara HSM'leri ve anahtar yönetim yazılımlarını yapılandırma, yama ve koruma ihtiyacı ile ilgili yardım sağlar. Azure Anahtar Kasası ile Microsoft hiçbir zaman anahtarlarınızı ve uygulamalarınızı doğrudan erişime sahip olmadığını görmez; denetimin size sağ tarafından korunmasını sağlar. Ayrıca, HSM'lerde anahtarları içeri aktarın veya üretin. Azure Information Protection'ı içeren bir aboneliği olan kuruluşlar, Azure Information Protection kiracılarını müşteri tarafından yönetilen bir anahtarı Bring [Your Own Key](/information-protection/plan-design/byok-price-restrictions) (BYOK) kullanarak) yapılandırarak kullanımını [günlüğe kilitler](/information-protection/deploy-use/log-analyze-usage).