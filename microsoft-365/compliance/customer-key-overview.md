---
title: Microsoft Purview Müşteri Anahtarı ile hizmet şifreleme
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
ms.custom: seo-marvel-apr2020
description: Bu makalede, hizmet şifrelemenin Microsoft Purview Müşteri Anahtarı ile nasıl çalıştığını öğreneceksiniz.
ms.openlocfilehash: 98f298e88a53fee40e5f254e18695bca42aad52a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66632475"
---
# <a name="service-encryption-with-microsoft-purview-customer-key"></a>Microsoft Purview Müşteri Anahtarı ile hizmet şifreleme

Microsoft 365, BitLocker ve Dağıtılmış Anahtar Yöneticisi (DKM) aracılığıyla etkinleştirilen temel, birim düzeyinde şifreleme sağlar. Microsoft 365, içeriğiniz için ek bir şifreleme katmanı sunar. Bu içerik Exchange Online, Skype Kurumsal, SharePoint Online, OneDrive İş ve Microsoft Teams verilerini içerir.

## <a name="how-service-encryption-bitlocker-and-customer-key-work-together"></a>Hizmet şifrelemesi, BitLocker ve Müşteri Anahtarı birlikte nasıl çalışır?

Verileriniz BitLocker ve DKM ile Microsoft 365 hizmetinde bekleme sırasında her zaman şifrelenir. Daha fazla bilgi için bkz. [Exchange Online e-posta gizli dizilerinizin güvenliğini nasıl sağlar](exchange-online-secures-email-secrets.md)? Müşteri Anahtarı, yetkisiz sistemler veya personel tarafından verilerin görüntülenmesine karşı ek koruma sağlar ve Microsoft veri merkezlerinde BitLocker disk şifrelemesini tamamlar. Hizmet şifrelemesi, Microsoft personelinin verilerinize erişmesini engellemeye yönelik değildir. Bunun yerine Müşteri Anahtarı, kök anahtarları denetlemeye yönelik mevzuat veya uyumluluk yükümlülüklerini yerine getirmenize yardımcı olur. Microsoft 365 hizmetlerini eBulma, kötü amaçlı yazılımdan koruma, istenmeyen posta önleme, arama dizini oluşturma gibi katma değerli bulut hizmetleri sağlamak için şifreleme anahtarlarınızı kullanmaları için açıkça yetkilendirebilirsiniz.

Müşteri Anahtarı, hizmet şifrelemesi üzerine kurulmuştur ve şifreleme anahtarlarını sağlamanıza ve denetlemenize olanak tanır. Daha sonra Microsoft 365, [Bekleyen verilerinizi Çevrimiçi Hizmet Koşulları'nda (OST)](https://www.microsoft.com/licensing/product-licensing/products.aspx) açıklandığı gibi şifrelemek için bu anahtarları kullanır. Müşteri Anahtarı, Microsoft 365'in verileri şifrelemek ve şifresini çözmek için kullandığı şifreleme anahtarlarını denetlediğinizden uyumluluk yükümlülüklerini karşılamanıza yardımcı olur.
  
Müşteri Anahtarı, kuruluşunuzun bulut hizmeti sağlayıcısıyla önemli düzenlemeleri belirten uyumluluk gereksinimleri taleplerini karşılama becerisini geliştirir. Müşteri Anahtarı ile Microsoft 365 verilerinizin kök şifreleme anahtarlarını uygulama düzeyinde sağlar ve denetlersiniz. Sonuç olarak, kuruluşunuzun anahtarları üzerinde denetime sahip olursunuz.

## <a name="customer-key-with-hybrid-deployments"></a>Karma dağıtımlarla Müşteri Anahtarı

Müşteri Anahtarı yalnızca bulutta bekleyen verileri şifreler. Müşteri Anahtarı, şirket içi posta kutularınızı ve dosyalarınızı korumak için çalışmaz. BitLocker gibi başka bir yöntem kullanarak şirket içi verilerinizi şifreleyebilirsiniz.

## <a name="about-data-encryption-policies"></a>Veri şifreleme ilkeleri hakkında

Veri şifreleme ilkesi (DEP), şifreleme hiyerarşisini tanımlar. Bu hiyerarşi, yönettiğiniz anahtarların her birini ve Microsoft tarafından korunan kullanılabilirlik anahtarını kullanarak verileri şifrelemek için hizmet tarafından kullanılır. PowerShell cmdlet'lerini kullanarak DEP'ler oluşturur ve ardından uygulama verilerini şifrelemek için bu DEP'leri atarsınız. Müşteri Anahtarı tarafından desteklenen üç tür DEP vardır ve her ilke türü farklı cmdlet'ler kullanır ve farklı bir veri türü için kapsam sağlar. Tanımlayabileceğiniz DEP'ler şunlardır:

**Birden çok Microsoft 365 iş yükü için DEP** Bu DEP'ler, kiracıdaki tüm kullanıcılar için birden çok M365 iş yükünde verileri şifreler. Bu iş yükleri şunlardır:

- Teams sohbet iletileri (1:1 sohbetler, grup sohbetleri, toplantı sohbetleri ve kanal konuşmaları)
- Teams medya iletileri (görüntüler, kod parçacıkları, video iletileri, sesli iletiler, wiki görüntüleri)
- Teams depolama alanında depolanan Teams arama ve toplantı kayıtları
- Teams sohbet bildirimleri
- Cortana tarafından teams sohbet önerileri
- Teams durum iletileri
- Exchange Online için kullanıcı ve sinyal bilgileri
- Posta kutusu DEP'leri tarafından henüz şifrelenmemiş posta kutularını Exchange Online
- Microsoft Purview Bilgi Koruması:

  - Veri dosyası şemaları, kural paketleri ve hassas verilerin karması için kullanılan tuzlar da dahil olmak üzere tam veri eşleşmesi (EDM) verileri. EDM ve Microsoft Teams için çok iş yükülü DEP, DEP'yi kiracıya atadığınız zamandan itibaren yeni verileri şifreler. Exchange Online için Müşteri Anahtarı tüm mevcut ve yeni verileri şifreler.

  - Duyarlılık etiketleri için etiket yapılandırması

Çok iş yüküLÜ DEP'ler aşağıdaki veri türlerini şifrelemez. Bunun yerine, Microsoft 365 bu verileri korumak için diğer şifreleme türlerini kullanır.

- SharePoint ve OneDrive İş verileri.
- Microsoft Teams dosyaları ve OneDrive İş ve SharePoint Online'a kaydedilen bazı Teams arama ve toplantı kayıtları SharePoint Online DEP kullanılarak şifrelenir.
- Şu anda Müşteri Anahtarı tarafından desteklenmeyen Yammer ve Planner gibi diğer Microsoft 365 iş yükleri.
- Teams Canlı Etkinlik verileri.

Kiracı başına birden çok DEP oluşturabilir, ancak aynı anda yalnızca bir DEP atayabilirsiniz. DEP'yi atadığınızda şifreleme otomatik olarak başlar ancak kiracınızın boyutuna bağlı olarak tamamlanması biraz zaman alır.

**Exchange Online posta kutuları için DEP'ler** Posta kutusu DEP'leri, Exchange Online içindeki tek tek posta kutuları üzerinde daha hassas denetim sağlar. UserMailbox, MailUser, Group, PublicFolder ve Paylaşılan posta kutuları gibi farklı türlerdeki EXO posta kutularında depolanan verileri şifrelemek için posta kutusu DEP'lerini kullanın. Kiracı başına en fazla 50 etkin DEP'niz olabilir ve bu DEP'leri tek tek posta kutularına atayabilirsiniz. Birden çok posta kutusuna bir DEP atayabilirsiniz.

Posta kutularınız varsayılan olarak Microsoft tarafından yönetilen anahtarlar kullanılarak şifrelenir. Bir posta kutusuna Müşteri Anahtarı DEP'i atadığınızda:

- Posta kutusu çok iş yükülü bir DEP kullanılarak şifrelenirse, kullanıcı veya sistem işlemi posta kutusu verilerine eriştiği sürece hizmet yeni posta kutusu DEP'sini kullanarak posta kutusunu yeniden oluşturur.

- Posta kutusu Microsoft tarafından yönetilen anahtarlar kullanılarak zaten şifrelenmişse, kullanıcı veya sistem işlemi posta kutusu verilerine eriştiği sürece hizmet yeni posta kutusu DEP'sini kullanarak posta kutusunu yeniden oluşturur.

- Posta kutusu henüz varsayılan şifreleme kullanılarak şifrelenmemişse, hizmet posta kutusunu taşıma için işaretler. Taşıma tamamlandıktan sonra şifreleme gerçekleştirilir. Posta kutusu taşıma işlemleri, tüm Microsoft 365 için ayarlanan öncelikler temelinde yönetilir. Daha fazla bilgi için bkz. [Microsoft 365 hizmetinde istekleri taşıma](/exchange/mailbox-migration/office-365-migration-best-practices#move-requests-in-the-microsoft-365-or-office-365-service). Posta kutuları belirtilen süre içinde şifrelenmemişse Microsoft'a başvurun.

Daha sonra DEP'yi yenileyebilir veya [Office 365 için Müşteri Anahtarını Yönetme](customer-key-manage.md) bölümünde açıklandığı gibi posta kutusuna farklı bir DEP atayabilirsiniz. Her posta kutusunun bir DEP'ye atanması için uygun lisanslara sahip olması gerekir. Lisanslama hakkında daha fazla bilgi için bkz. [Müşteri Anahtarını ayarlamadan önce](customer-key-set-up.md#before-you-set-up-customer-key).

DEP'ler, kullanıcı posta kutuları için lisans gereksinimini karşılayan kiracılar için paylaşılan posta kutusuna, ortak klasör posta kutusuna ve Microsoft 365 grup posta kutusuna atanabilir. Müşteri Anahtarı DEP'sini atamak için kullanıcıya özgü olmayan posta kutuları için ayrı lisanslara ihtiyacınız yoktur.

Tek tek posta kutularına atadığınız Müşteri Anahtarı DEP'leri için, hizmetten ayrıldığınızda Microsoft'un belirli DEP'leri temizlemesini isteyebilirsiniz. Veri temizleme işlemi ve anahtar iptali hakkında bilgi için bkz. [Anahtarlarınızı iptal etme ve veri temizleme yolu işlemini başlatma](customer-key-manage.md#revoke-your-keys-and-start-the-data-purge-path-process).

Hizmetten ayrılmanın bir parçası olarak anahtarlarınıza erişimi iptal ettiğinizde kullanılabilirlik anahtarı silinir ve bu da verilerinizin şifrelemeyle silinmesine neden oluyor. Şifreleme silme işlemi, hem güvenlik hem de uyumluluk yükümlülüklerini yerine getirme açısından önemli olan veri yeniden yönetimi riskini azaltır.

**SharePoint Online ve OneDrive İş için DEP** Bu DEP, SPO'da depolanan Microsoft Teams dosyaları dahil olmak üzere SPO ve OneDrive İş depolanan içeriği şifrelemek için kullanılır. Çok coğrafi bölge özelliğini kullanıyorsanız, kuruluşunuz için her coğrafi bölge için bir DEP oluşturabilirsiniz. Multi-geo özelliğini kullanmıyorsanız kiracı başına yalnızca bir DEP oluşturabilirsiniz. [Müşteri Anahtarını Ayarlama](customer-key-set-up.md) makalesindeki ayrıntılara bakın.

### <a name="encryption-ciphers-used-by-customer-key"></a>Müşteri Anahtarı tarafından kullanılan şifreleme şifreleri

Müşteri Anahtarı, aşağıdaki şekilde gösterildiği gibi anahtarları şifrelemek için çeşitli şifreleme şifreleri kullanır.

Birden çok Microsoft 365 iş yükü için verileri şifreleyen DEP'ler için kullanılan anahtar hiyerarşisi, tek tek Exchange Online posta kutuları için DEP'ler için kullanılan hiyerarşiye benzer. Tek fark, Posta Kutusu Anahtarı'nın karşılık gelen Microsoft 365 İş Yükü Anahtarı ile değiştirilmesidir.

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-exchange-online-and-skype-for-business"></a>Exchange Online ve Skype Kurumsal anahtarlarını şifrelemek için kullanılan şifreleme şifreleri

![Exchange Online Müşteri Anahtarı için şifreleme şifreleri.](../media/customerkeyencryptionhierarchiesexchangeskype.png)

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>SharePoint Online, OneDrive İş ve Teams dosyalarının anahtarlarını şifrelemek için kullanılan şifreleme şifreleri

![SharePoint Online Müşteri Anahtarı için şifreleme şifreleri.](../media/customerkeyencryptionhierarchiessharepointonedriveteamsfiles.png)

## <a name="related-articles"></a>İlgili makaleler

- [Müşteri Anahtarını Ayarlama](customer-key-set-up.md)

- [Müşteri Anahtarını Yönet](customer-key-manage.md)

- [Bir Müşteri Anahtarını veya uygunluk anahtarını toplama veya döndürme](customer-key-availability-key-roll.md)

- [Kullanılabilirlik anahtarı hakkında bilgi edinin](customer-key-availability-key-understand.md)

- [Müşteri Kasası](customer-lockbox-requests.md)

- [Hizmet Şifrelemesi](office-365-service-encryption.md)
