---
title: Data Encryption in OneDrive for Business and SharePoint Online
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 9/20/2021
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- MET150
ms.assetid: 6501b5ef-6bf7-43df-b60d-f65781847d6c
ms.collection:
- M365-security-compliance
- SPO_Content
description: OneDrive İş ve SharePoint Online'da veri güvenliği için şifrelemenin temel öğelerini anlama.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 5b56caed2a93bf482509a4a90a8bbc3a828d76e7
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66630157"
---
# <a name="data-encryption-in-onedrive-for-business-and-sharepoint-online"></a>Data Encryption in OneDrive for Business and SharePoint Online

OneDrive İş ve SharePoint Online'da veri güvenliği için şifrelemenin temel öğelerini anlama.
  
## <a name="security-and-data-encryption-in-office-365"></a>Office 365'de güvenlik ve veri şifrelemesi

Microsoft 365, fiziksel veri merkezi güvenliği, ağ güvenliği, erişim güvenliği, uygulama güvenliği ve veri güvenliği olmak üzere birden çok katmanda kapsamlı koruma sunan son derece güvenli bir ortamdır. Bu makale özellikle OneDrive İş ve SharePoint Online için veri güvenliğinin aktarım ve bekleyen şifreleme tarafına odaklanır.
  
Aşağıdaki videoda veri şifrelemenin nasıl çalıştığını izleyin.
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/dea0dec4-4077-4095-9a32-19b94ea2da4b?autoplay=false]
  
## <a name="encryption-of-data-in-transit"></a>Aktarımdaki verilerin şifresi

OneDrive İş ve SharePoint Online'da, verilerin veri merkezlerine girip çıktığı iki senaryo vardır.
  
- **Sunucuyla istemci iletişimi** İnternet üzerinden OneDrive İş iletişiminde SSL/TLS bağlantıları kullanılır. Tüm SSL bağlantıları 2048 bit anahtarlar kullanılarak kurulur.

- **Veri merkezleri arasında veri taşıma** Verileri veri merkezleri arasında taşımanın birincil nedeni, olağanüstü durum kurtarmayı etkinleştirmek için coğrafi çoğaltmadır. Örneğin, SQL Server işlem günlükleri ve blob depolama deltaları bu kanal boyunca ilerler. Bu veriler zaten özel bir ağ kullanılarak iletilmiş olsa da, sınıfının en iyisi şifreleme ile daha da korunur. 

## <a name="encryption-of-data-at-rest"></a>Bekleyen verilerin şifrelenmesi

Bekleyen şifreleme iki bileşen içerir: BitLocker disk düzeyinde şifreleme ve müşteri içeriğinin dosya başına şifrelenmesi.
  
BitLocker, hizmet genelinde OneDrive İş ve SharePoint Online için dağıtılır. Dosya başına şifreleme, microsoft 365 çok kiracılı ve çok kiracılı teknoloji üzerine oluşturulmuş yeni ayrılmış ortamlarda OneDrive İş ve SharePoint Online'da da bulunur.
  
BitLocker disk üzerindeki tüm verileri şifrelese de, dosya başına şifreleme, her dosya için benzersiz bir şifreleme anahtarı ekleyerek daha da ileri gider. Ayrıca, her dosyaya yapılan her güncelleştirme kendi şifreleme anahtarı kullanılarak şifrelenir. Şifrelenmiş içeriğin anahtarları, içerikten fiziksel olarak ayrı bir konumda depolanır. Bu şifrelemenin her adımında 256 bit anahtarlarla Gelişmiş Şifreleme Standardı (AES) kullanılır ve Federal Bilgi İşleme Standardı (FIPS) 140-2 uyumludur. Şifrelenmiş içerik, veri merkezi genelinde bir dizi kapsayıcıya dağıtılır ve her kapsayıcının benzersiz kimlik bilgileri vardır. Bu kimlik bilgileri, içerikten veya içerik anahtarlarından ayrı bir fiziksel konumda depolanır.
  
FIPS 140-2 uyumluluğu hakkında ek bilgi için bkz. [FIPS 140-2 Uyumluluğu](/previous-versions/sql/sql-server-2008-r2/bb326611(v=sql.105)).
  
Bekleyen dosya düzeyinde şifreleme, neredeyse sınırsız depolama büyümesi sağlamak ve benzeri görülmemiş bir koruma sağlamak için blob depolamadan yararlanır. OneDrive İş ve SharePoint Online'daki tüm müşteri içeriği blob depolamaya geçirilecektir. Verilerin güvenliği şu şekilde sağlanır:
  
1. Tüm içerik şifrelenir, potansiyel olarak birden çok anahtarla şifrelenir ve veri merkezine dağıtılır. Depolanacak her dosya, boyutuna bağlı olarak bir veya daha fazla öbeklere ayrılır. Ardından her öbek kendi benzersiz anahtarı kullanılarak şifrelenir. Güncelleştirmeler benzer şekilde işlenir: Kullanıcı tarafından gönderilen değişiklik veya değişiklik kümesi öbeklere ayrılır ve her biri kendi anahtarıyla şifrelenir.

2. Bu öbeklerin tümü (dosyalar, dosya parçaları ve güncelleştirme deltaları) blob depomuzda blob olarak depolanır. Ayrıca birden çok blob kapsayıcısı arasında rastgele dağıtılır.

3. Dosyayı bileşenlerinden yeniden derlemek için kullanılan "harita" İçerik Veritabanında depolanır.

4. Her blob kapsayıcısı, erişim türü başına kendi benzersiz kimlik bilgilerine sahiptir (okuma, yazma, listeleme ve silme). Her kimlik bilgisi kümesi güvenli Anahtar Deposu'nda tutulur ve düzenli olarak yenilenir.

Başka bir deyişle, bekleyen dosya başına şifrelemeye dahil olan ve her biri ayrı bir işleve sahip üç farklı depo türü vardır:
  
- İçerik, blob deposunda şifrelenmiş bloblar olarak depolanır. Her içerik öbeklerinin anahtarı şifrelenir ve içerik veritabanında ayrı olarak depolanır. İçeriğin kendisi, şifresinin nasıl çözülebileceği hakkında hiçbir ipucu tutmaz.

- İçerik Veritabanı bir SQL Server veritabanıdır. Blob deposunda tutulan tüm içerik bloblarını ve bu blobların şifresini çözmek için gereken anahtarları bulmak ve yeniden bir araya getirmek için gereken haritayı tutar.

Bu üç depolama bileşeninin her biri (blob deposu, İçerik Veritabanı ve Anahtar Deposu) fiziksel olarak ayrıdır. Bileşenlerden herhangi birinde tutulan bilgiler tek başına kullanılamaz. Bu, daha önce görülmemiş bir güvenlik düzeyi sağlar. Üçüne de erişim olmadan öbeklerin anahtarlarını almak, kullanılabilir hale getirmek için anahtarların şifresini çözmek, anahtarları karşılık gelen öbekleriyle ilişkilendirmek, herhangi bir öbeklerin şifresini çözmek veya bir belgeyi kendi bağlı öbeklerinden yeniden yapılandırmak mümkün değildir.
