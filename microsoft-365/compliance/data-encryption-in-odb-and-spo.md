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
description: OneDrive İş ve SharePoint Online'da veri güvenliği için temel şifreleme öğelerini anlama.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 25bebc8fd5ab9b820667f5220785b021230ca6e1
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985705"
---
# <a name="data-encryption-in-onedrive-for-business-and-sharepoint-online"></a>Data Encryption in OneDrive for Business and SharePoint Online

OneDrive İş ve SharePoint Online'da veri güvenliği için temel şifreleme öğelerini anlama.
  
## <a name="security-and-data-encryption-in-office-365"></a>e-Office 365'de güvenlik ve veri Office 365

Microsoft 365 kapsamlı bir koruma sunan yüksek güvenli bir ortamdır: fiziksel veri merkezi güvenliği, ağ güvenliği, erişim güvenliği, uygulama güvenliği ve veri güvenliği. Bu makale özellikle OneDrive İş SharePoint Online için veri güvenliğinin in-transit ve yerinde şifreleme SharePoint üzerinde odaklanmektedir.
  
Veri şifrelemenin nasıl çalıştığını aşağıdaki videoda izleyin.
  
> [!VIDEO https://www.microsoft.com/videoplayer/embed/dea0dec4-4077-4095-9a32-19b94ea2da4b?autoplay=false]
  
## <a name="encryption-of-data-in-transit"></a>Geçişte veri şifrelemesi

OneDrive İş SharePoint Online'da, verilerin veri merkezlerine giriş ve çıkışları iki senaryodan çıkar.
  
- **Sunucuyla istemci iletişimi** İnternet üzerinden OneDrive İş,SSL/TLS bağlantıları kullanır. 2048 bit anahtarları kullanılarak tüm SSL bağlantıları kurulur.

- **Veri merkezleri arasında veri hareketi** Verileri veri merkezleri arasında taşımanın en önemli nedeni, olağanüstü durum kurtarmayı etkinleştirmek için coğrafi çoğaltmadır. Örneğin, işlem SQL Server blob depolama deltaları bu boru boyunca hareket ediyor. Bu veriler özel ağ kullanılarak zaten ilet açıksa da, bu veriler en iyi sınıf şifrelemeyle daha da korunur. 

## <a name="encryption-of-data-at-rest"></a>Beklemede verilerin şifreleniyor

Beklemede şifreleme iki bileşen içerir: BitLocker disk düzeyinde şifreleme ve müşteri içeriğinin dosya başına şifrelemesi.
  
BitLocker, servis genelinde OneDrive İş ve SharePoint Online için dağıtıldı. Dosya başına şifreleme aynı zamanda OneDrive İş ve SharePoint Online'da Microsoft 365 çok kiracılı teknoloji üzerine yerleşik yeni ayrılmış ortamlarda da kullanılabilir.
  
BitLocker diskte yer alan tüm verileri şifrelerken, her dosya için benzersiz bir şifreleme anahtarı daha da ileriye doğru ilerler. Ayrıca, her dosyanın her güncelleştirmesi kendi şifreleme anahtarı kullanılarak şifrelenir. Şifrelenmiş içeriğin anahtarları, fiziksel olarak içerikten ayrı bir konumda depolanır. Bu şifrelemenin her adımı, 256 bit anahtarları olan Gelişmiş Şifreleme Standardı (AES) kullanır ve Federal Bilgi İşleme Standardı (FIPS) 140-2 ile uyumludur. Şifrelenmiş içerik, veri merkezi genelinde bir dizi kapsayıcıya dağıtılır ve her kapsayıcıda benzersiz kimlik bilgileri vardır. Bu kimlik bilgileri, içerik veya içerik anahtarlarından ayrı bir fiziksel konumda depolanır.
  
FIPS 140-2 uyumluluğu hakkında ek bilgi için [bkz. FIPS 140-2 Uyumluluk](/previous-versions/sql/sql-server-2008-r2/bb326611(v=sql.105)).
  
Beklemede dosya düzeyinde şifreleme, hemen sınırsız depolama alanı büyümesine olanak sağlamak ve koruma korumasını etkinleştirmek için blob depolamadan faydalanır. OneDrive İş SharePoint Online'daki tüm müşteri içeriği blob depolama alanına geçirilir. Bu verilerin güvenliği şöyle sağlandı:
  
1. Tüm içerik şifrelenmiştir, potansiyel olarak birden çok anahtarla ve veri merkezi genelinde dağıtılmıştır. Depolanmış olan her dosya, boyutuna bağlı olarak bir veya birden çok öbek halinde kaydedilir. Ardından, her öbek kendi benzersiz anahtarı kullanılarak şifrelenir. Güncelleştirmeler benzer şekilde ele alınarak işlenir: kullanıcı tarafından gönderilen değişiklik kümesi veya değişiklik değişiklikleri öbeklere göre şifrelenir ve her biri kendi anahtarıyla şifrelenir.

2. Bu öbeklerin (dosyalar, dosya parçaları ve güncelleştirme parçaları) hepsi blob mağazamızda bloblar olarak depolanır. Ayrıca, birden çok blob kapsayıcısı arasında rastgele dağıtılmıştır.

3. Dosyanın bileşenlerinden yeniden bir araya gelen dosyayı yeniden derlerken kullanılan "eşleme", İçerik Veritabanında depolanır.

4. Her blob kapsayıcısını erişim türü (okuma, yazma, numarala ve sil) başına kendi benzersiz kimlik bilgileri vardır. Her kimlik bilgileri kümesi güvenli Anahtar Deposu'nda tutularak düzenli aralıklarla yenilenir.

Başka bir deyişle, ayrı bir işleve sahip olan, geri alınan dosya başına şifrelemeye katılan üç farklı depo türü vardır:
  
- İçerik, blob deposunda şifrelenmiş bloblar olarak depolanır. İçerik öbeklerinin anahtarı şifrelenir ve içerik veritabanında ayrı olarak depolanır. İçeriğin şifresinin nasıl çözülebilecek olduğuna dair hiçbir ipucu yoktur.

- İçerik Veritabanı, en son SQL Server veritabanıdır. Blob mağazasından yapılan tüm içerik bloblarını ve bu blobların şifresini çözmek için gereken anahtarların yanı sıra bu blobların şifresini çözmek için gereken tüm içerik bloblarını bulmak ve yeniden bire bir yapmak için gereken eşlemeyi tutar.

Bu üç depolama bileşeni (blob deposu, İçerik Veritabanı ve Anahtar Deposu) fiziksel olarak birbirinden ayrıdır. Bileşenlerden herhangi birsinde bulunan bilgiler kendi başına kullanılamaz. Bu, güvenlik düzeyi sağlar. Bu üç öbeklere erişmeniz, kullanılabilir olması için anahtarların şifresini çözmeniz, anahtarları karşılık gelen öbeklerle ilişkilendirmeniz, öbeklerin şifresini çözmeniz veya bir belgeyi ilişkili öbeklerden yeniden oluşturmanız imkansızdır.