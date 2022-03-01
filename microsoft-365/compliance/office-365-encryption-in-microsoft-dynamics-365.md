---
title: Microsoft Dynamics 365'te şifreleme
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
ms.collection: Strat_O365_Enterprise
description: Microsoft'un, Microsoft veritabanında beklemede ve geçiş sırasında Microsoft Dynamics 365'te müşteri verilerini korumak için şifreleme teknolojisini nasıl kullandığını öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: ba3dbef73b7674364f19e83befdbb8cdfe417ad6
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2021
ms.locfileid: "62999040"
---
# <a name="encryption-in-microsoft-dynamics-365"></a>Microsoft Dynamics 365'te şifreleme

Microsoft, Dynamics 365'te müşteri verilerini Microsoft veri merkezinde beklemede ve kullanıcı cihazlarımız ile veri merkezlerimiz arasında geçiş yaparken korumak için şifreleme teknolojisi kullanır. Müşterilerle Microsoft veri merkezleri arasında kurulan bağlantılar şifrelenir ve tüm genel uç noktalar endüstri standardı TLS kullanılarak güvenlik altına alınır. TLS, masaüstü ve veri merkezleri arasında verilerin gizliliğini ve bütünlüğünü sağlamaya yardımcı olmak için, güvenliği iyileştirilmiş bir tarayıcıdan sunucuya bağlantı kurmaktadır. Veri şifreleme etkinleştirildikten sonra kapatamaz. Daha fazla bilgi için bkz [. Alan düzeyinde veri şifreleme](/previous-versions/dynamicscrm-2016/developers-guide/dn481562(v=crm.8)).

Dynamics 365, kullanıcı Microsoft SQL Server ve e-posta parolaları gibi hassas bilgiler içeren bir dizi varsayılan varlık özniteliği için standart kimlik düzeyi şifrelemesi kullanır. Bu özellik kuruluşların FIPS 140-2 ile ilişkili uyumluluk gereksinimlerini karşılamalarına yardımcı olabilir. Alan düzeyi veri şifrelemesi, Dynamics 365 örneği ile e-posta hizmeti arasındaki tümleştirmeyi etkinleştirmek için kullanıcı adlarını ve parolaları depolaması gereken [Microsoft Dynamics CRM](/previous-versions/dynamicscrm-2016/administering-dynamics-365/hh699800(v=crm.8)) E-posta Yönlendiricisi'den yararlanan senaryolarda özellikle önemlidir.

Dynamics 365'in tüm örnekleri, [diske](/sql/relational-databases/security/encryption/transparent-data-encryption) (beklemede) yazıldığı zaman verilerin gerçek zamanlı şifrelemesini gerçekleştirmek için Microsoft SQL Server Saydam Veri Şifrelemesi (TDE) kullanır. TDE, SQL Server, Azure SQL Veritabanı ve Azure Veritabanı SQL dosyalarını şifreler. Varsayılan olarak, Microsoft Dynamics 365 örnekleriniz için veritabanı şifreleme anahtarlarını depolar ve yönetir. (Finansallar için Dynamics 365 tarafından kullanılan anahtarlar Veri Koruma API'si .NET Framework tarafından oluşturulur.)

Dynamics 365 Yönetim Merkezi'nin anahtarları yönetme özelliği yöneticilere Dynamics 365 örnekleriyle ilişkilendirilmiş veritabanı şifreleme anahtarlarını kendi kendine yönetme olanağı verir. (Kendi kendine veritabanı şifreleme anahtarları, yalnızca Microsoft Dynamics 365'in Ocak 2017 güncelleştirmesinde kullanılabilir ve sonraki sürümlerde kullanılamaz. Daha fazla bilgi için bkz [. Dynamics 365 (çevrimiçi) örneğiniz için şifreleme anahtarlarını yönetme.)](/dynamics365/customer-engagement/admin/manage-encryption-keys-instance) Anahtar yönetimi özelliği, HSM'de depolanan dosyalar gibi hem PFX hem de BYOK şifreleme anahtar dosyalarını destekler. (İnternet üzerinden HSM korumalı bir anahtar oluşturma ve aktarma hakkında daha fazla bilgi için bkz. Azure Anahtar Kasası için [HSM](/azure/key-vault/key-vault-hsm-protected-keys) korumalı anahtarlar oluşturma ve aktarma.)

Karşıya yükleme şifreleme anahtarı seçeneğini kullanmak için, hem genel hem de özel şifreleme anahtarı gerekir.

Anahtar yönetimi özelliği, şifreleme anahtarlarını güvenli bir şekilde depolamak için Azure Anahtar Kasasını kullanarak şifreleme anahtarı yönetimini karmaşık hale getirir. Azure Anahtar Kasası, bulut uygulamaları ve hizmetleri tarafından kullanılan şifreleme anahtarlarını ve sırlarını korumaya yardımcı olur. Anahtar yönetimi özelliği Azure Anahtar Kasa aboneliğiniz olması gerektirmez ve çoğu durumda kasa içinde Dynamics 365 için kullanılan şifreleme anahtarlarına erişmeniz gerek yoktur.
