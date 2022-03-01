---
title: Müşteri Anahtarı ile Hizmet şifrelemesi
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
description: Bu makalede, Hizmet Şifrelemesi'nin Müşteri Anahtarı ile birlikte nasıl çalıştığını Microsoft 365.
ms.openlocfilehash: 14760bfcb26fa1bf45c54661cbb6fc189bad7d93
ms.sourcegitcommit: f563b4229760fa099703296d1ad2c1f0264f1647
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2022
ms.locfileid: "63016263"
---
# <a name="service-encryption-with-customer-key"></a>Müşteri Anahtarı ile Hizmet şifrelemesi

Microsoft 365, BitLocker ve Dağıtılmış Anahtar Yöneticisi (DKM) aracılığıyla etkinleştiren temel, toplu düzey şifreleme sağlar. Microsoft 365, içeriğiniz için ek bir şifreleme katmanı sunar. Bu içerik; Exchange Online, Skype Kurumsal, SharePoint Online, OneDrive İş ve Microsoft Teams.

## <a name="how-service-encryption-bitlocker-and-customer-key-work-together"></a>Hizmet şifreleme, BitLocker ve Müşteri Anahtarı birlikte nasıl çalışır?

BitLocker ve DKM ile aynı hizmette Microsoft 365 verileriniz sabitlenir. Daha fazla bilgi için bkz[. Exchange Online e-posta sırlarınızı nasıl güvence altına alır](exchange-online-secures-email-secrets.md)? Müşteri Anahtarı, verileri yetkisiz sistemlere veya personele göre görüntülemeye karşı ek koruma sağlar ve Microsoft veri merkezlerinde BitLocker disk şifrelemesini tamamlar. Hizmet şifreleme, Microsoft personelinin verilerinize erişmesini engellemek için değildir. Müşteri Anahtarı bunun yerine, kök anahtarların denetlenmeyle ilgili mevzuat veya uyumluluk yükümlülüklerini karşılamanıza yardımcı olur. eBulma, Microsoft 365 dan koruma, istenmeyen posta önleme, arama dizini oluşturma gibi değer ekli bulut hizmetleri sağlamak üzere şifreleme anahtarlarınızı kullanmak için bu hizmetlere açıkça yetki verirsiniz.

Müşteri Anahtarı hizmet şifrelemesi üzerine yerleşiktir ve şifreleme anahtarlarını sağlama ve denetlemenizi sağlar. Microsoft 365 bu anahtarları, Online Services Koşulları'nda (OST) açıklandığı gibi geri kalanını [şifrelemek için kullanır](https://www.microsoft.com/licensing/product-licensing/products.aspx). Müşteri Anahtarı, verilerin şifresini çözmek ve şifrelerini çözmek için kullandığı şifreleme anahtarlarını Microsoft 365 uyumluluk yükümlülüklerini karşılamanıza yardımcı olur.
  
Müşteri Anahtarı, bulut hizmeti sağlayıcısıyla önemli düzenlemeleri belirten uyumluluk gereksinimleri taleplerini karşılama olanağını geliştirmektedir. Müşteri Anahtarı ile, verileriniz için kök şifreleme anahtarlarını uygulama Microsoft 365 düzeyinde sağlar ve kontrol edersiniz. Sonuç olarak, kuruluş anahtarlarının üzerinde denetim alıştırması yapın.

## <a name="customer-key-with-hybrid-deployments"></a>Karma dağıtımlı Müşteri Anahtarı

Müşteri Anahtarı yalnızca buluttaki verileri şifreler. Şirket içi posta kutularınızı ve dosyalarınızı korumak için Müşteri Anahtarı çalışmıyor. BitLocker gibi başka bir yöntem kullanarak şirket içi verilerinizi şifreebilirsiniz.

## <a name="about-data-encryption-policies"></a>Veri şifreleme ilkeleri hakkında

Veri şifreleme ilkesi (DEP), şifreleme hiyerarşisini tanımlar. Bu hiyerarşi, hizmet tarafından, yönetmekte olduğu her anahtarı ve Microsoft tarafından korunan kullanılabilirlik anahtarını kullanarak verileri şifrelemek için kullanılır. PowerShell cmdlet'lerini kullanarak DEP'ler oluşturabilir ve sonra bu DEP'leri uygulama verilerini şifrelemek için atarsanız. Müşteri Anahtarı tarafından desteklenen üç DEP türü Microsoft 365, her ilke türü farklı cmdlet'ler kullanır ve farklı türde veriler için kapsam sağlar. Tanımladığınız DEP'ler şunlardır:

**Birden çok iş Microsoft 365 DEP'ler**, birden çok M365 iş yükü genelinde verileri kiracıdaki tüm kullanıcılar için şifreler. Bu iş yükleri şunlardır:

- Teams mesajları gönderme (bire bir sohbetler, grup sohbetleri, toplantı sohbetleri ve kanal konuşmaları)
- Teams mesajları (resimler, kod parçacıkları, görüntülü mesajlar, sesli mesajlar, wiki görüntüleri)
- Teams depolamada depolanan arama ve Teams kaydetmeyi sağlar
- Teams bildirimlerini geri bildirim olarak kabul edin
- Teams önerilerini, web Cortana
- Teams iletilerini gönderme
- Kullanıcı ve sinyal bilgileri Exchange Online
- Exchange Online kutusu DEP'leri tarafından şifrelenmeen posta kutularını geri alın
- Microsoft Bilgi Koruması:

  - Veri dosyası şemaları, kural paketleri ve hassas verileri karma olarak birleştirmek için kullanılan saltlar da dahil olmak üzere tam veri eşleşmesi (EDM) verileri. EDM ve Microsoft Teams için, çok iş yüküne sahip DEP, DEP'yi kiracıya atadığınız zamanla yeni verileri şifreler. Daha Exchange Online için, Customer Key mevcut ve yeni tüm verileri şifreler.

  - Duyarlılık etiketleri için etiket yapılandırması

Çok iş yüküne sahip DEP'ler aşağıdaki veri türlerini şifrelemez. Bunun Microsoft 365, bu verileri korumak için başka şifreleme türleri kullanır.

- SharePoint ve OneDrive İş.
- Microsoft Teams ve OneDrive İş Online'Teams kaydedilen bazı arama ve toplantı kayıtları, SharePoint Online DEP SharePoint şifrelenir.
- Şu Microsoft 365 Müşteri Anahtarı Yammer Planner gibi diğer iş yükleri.
- Teams Etkinlik verilerini içerir.

Kiracı başına birden çok DEP oluşturabilirsiniz, ancak bir defada yalnızca bir DEP atabilirsiniz. DEP'yi atadığınız zaman, şifreleme otomatik olarak başlar ancak kiracının boyutuna bağlı olarak tamamlanması biraz zaman alır.

**Posta kutularının Exchange Online DEP'leri**, posta kutusu içinde tek tek posta kutuları üzerinde daha hassas Exchange Online. UserMailbox, MailUser, Group, PublicFolder ve Paylaşılan posta kutuları gibi farklı türlerde OLAN EXO posta kutularında depolanan verileri şifrelemek için posta kutusu DEP'lerini kullanın. Kiracı başına en çok 50 etkin DEP'ye sahip olabilir ve bu DEP'leri tek tek posta kutularına atabilirsiniz. Birden çok posta kutusuna bir DEP atabilirsiniz.

Varsayılan olarak, Microsoft tarafından yönetilen anahtarlar kullanılarak posta kutularınız şifrelenir. Posta kutusuna Müşteri Anahtarı DEP'si atadığınız zaman:

- Posta kutusu çok iş yüküne sahip bir DEP kullanılarak şifrelenirse, kullanıcı veya sistem işlemi posta kutusu verilerine eriş olduğu sürece hizmet yeni posta kutusu DEP'i kullanarak posta kutusunu yeniden sarmalar.

- Posta kutusu Zaten Microsoft tarafından yönetilen anahtarlar kullanılarak şifrelenirse, kullanıcı veya sistem işlemi posta kutusu verilerine eriş olduğu sürece hizmet yeni posta kutusu DEP'i kullanarak posta kutusunu yeniden sarmalar.

- Posta kutusu henüz varsayılan şifreleme kullanılarak şifrelenmezse, hizmet posta kutusunu taşıma için işaretler. Taşıma tamamlandıktan sonra şifreleme  sürer. Posta kutusu hareketleri, tüm posta kutuları için ayarlanmış önceliklere Microsoft 365. Daha fazla bilgi için bkz[. Müşteri hizmetleri Microsoft 365 taşıma](/exchange/mailbox-migration/office-365-migration-best-practices#move-requests-in-the-microsoft-365-or-office-365-service). Posta kutuları belirtilen süre içinde şifrelenmezse, Microsoft'a ulaşın.

Daha sonra DEP'yi yenileyin veya Posta Kutusu için Müşteri Anahtarını Yönetme konusunda açıklandığı gibi farklı bir DEP [Office 365](customer-key-manage.md). Her posta kutusuna deP atanacak uygun lisanslar olması gerekir. Lisanslama hakkında daha fazla bilgi için bkz [. Müşteri Anahtarını ayarlamadan önce](customer-key-set-up.md#before-you-set-up-customer-key).

DEP'ler paylaşılan posta kutusuna, ortak klasör posta kutusuna Microsoft 365 kullanıcı posta kutuları için lisans gereksinimini karşılayacak kiracılar için grup posta kutularına atanabilir. Customer Key DEP'i atamak için kullanıcıya özgü olmayan posta kutuları için ayrı lisanslara ihtiyacınız yoktur.

Tek tek posta kutularına atadığınız Müşteri Anahtarı DEP'leri için, hizmetten ayrılarak Microsoft'un belirli DEP'leri temizlemesi için istekte bulundurabilirsiniz. Veri temizleme işlemi ve anahtar iptali hakkında bilgi için bkz. [Anahtarlarınızı iptal etme ve veri temizleme yol işlemini başlatma](customer-key-manage.md#revoke-your-keys-and-start-the-data-purge-path-process).

Hizmetten ayrılma işleminin bir parçası olarak anahtarlarına erişimi iptal edersiniz, kullanılabilirlik anahtarı silinir ve sonuçta verilerinizin şifreleme silinmesine neden olur. Şifreleme silme, hem güvenlik hem de uyumluluk yükümlülüklerini yerine getirme açısından önemli olan veri yeniden yönetimi riskini azalttı.

SharePoint Online ve OneDrive İş için **DEP Bu DEP**, SPO'da depolanan ve SPO'da depolanan OneDrive İş dosyalar dahil Microsoft Teams içeriği şifrelemek için kullanılır. Multi-geo özelliğini kullanıyorsanız, organizasyonunız için coğrafi olarak tek bir DEP oluşturabilirsiniz. Çok coğrafi özellik kullansanız bile, kiracı başına yalnızca bir DEP oluşturabilirsiniz. Müşteri Anahtarını [Ayarlama'daki ayrıntılara bakın](customer-key-set-up.md).

### <a name="encryption-ciphers-used-by-customer-key"></a>Customer Key tarafından kullanılan şifreleme şifrelemeleri

Müşteri Anahtarı, aşağıdaki şekillere gösterildiği gibi anahtarları şifrelemek için çeşitli şifreleme şifrelemeleri kullanır.

Birden çok iş yükünün verilerini şifrelenen DEP'ler için kullanılan anahtar hiyerarşisi Microsoft 365 posta kutuları için ayrı ayrı DEP'ler için kullanılan Exchange Online benzer. Tek fark, Posta Kutusu Anahtarı'nın ilgili Posta Kutusu Anahtarı ile değiştirilmesi Microsoft 365 olur.

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-exchange-online-and-skype-for-business"></a>Şifreleme şifrelemesi, şifreleme ve şifreleme için Exchange Online için Skype Kurumsal

![Müşteri Anahtarı şifrelemesi için Exchange Online şifreleme.](../media/customerkeyencryptionhierarchiesexchangeskype.png)

#### <a name="encryption-ciphers-used-to-encrypt-keys-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>SharePoint Online, OneDrive İş ve Teams dosyalarını şifrelemek için kullanılan şifreleme şifrelemeleri

![Çevrimiçi Müşteri Anahtarı şifrelemesi SharePoint Şifreleme.](../media/customerkeyencryptionhierarchiessharepointonedriveteamsfiles.png)

## <a name="related-articles"></a>İlgili makaleler

- [Müşteri Anahtarını Ayarlama](customer-key-set-up.md)

- [Müşteri Anahtarını Yönet](customer-key-manage.md)

- [Müşteri Anahtarını veya uygunluk anahtarını döndürme veya döndürme](customer-key-availability-key-roll.md)

- [Kullanılabilirlik anahtarı hakkında bilgi](customer-key-availability-key-understand.md)

- [Müşteri Kasası](customer-lockbox-requests.md)

- [Hizmet Şifrelemesi](office-365-service-encryption.md)
