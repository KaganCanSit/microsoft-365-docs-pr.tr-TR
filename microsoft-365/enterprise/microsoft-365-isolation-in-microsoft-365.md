---
title: Microsoft 365'de Yalıtım ve Erişim Denetimi
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
f1.keywords:
- NOCSH
description: 'Özet: Bir denetimin çeşitli uygulamaları içindeki yalıtlama ve erişim denetimi Microsoft 365.'
ms.openlocfilehash: 65845a8d6c8e6be578e997fa1455aa280c787897
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019505"
---
# <a name="isolation-and-access-control-in-microsoft-365"></a>Microsoft 365'de Yalıtım ve Erişim Denetimi

Azure Active Directory (Azure AD) ve Microsoft 365, onlarca hizmet, yüzlerce varlık, binlerce ilişki ve on binlerce öznitelik içeren son derece karmaşık bir veri modeli kullanır. Üst düzeyde, Azure AD ve hizmet dizinleri durum tabanlı çoğaltma protokolleri kullanılarak eşitlenen kiracı ve alıcılar kapsayıcılarıdır. Azure AD'de alınan dizin bilgilerine ek olarak, hizmet iş yüklerinin her biri kendi dizin hizmetleri altyapısına da sahip olur.
 
![Microsoft 365 veri eşitlemeyi seçin.](../media/office-365-isolation-tenant-data-sync.png)

Bu modelin içinde tek bir dizin veri kaynağı yoktur. Belirli sistemlerin ayrı ayrı veri parçaları vardır, ancak tek sistem tüm verileri bulundur olmaz. Microsoft 365 hizmetleri, bu veri modelinde Azure AD ile işbirliği yapar. Azure AD, paylaşılan veriler için genellikle her hizmet tarafından kullanılan küçük ve statik veriler olan "tek doğru sistem" sistemidir. Verilerin paylaşılan görünümünü, Microsoft 365 ve Azure AD'de kullanılan federasyon modeli sağlar.

Microsoft 365 hem fiziksel depolama alanı hem de Azure bulut depolaması kullanır. Exchange Online verileri için (Exchange Online Protection dahil) ve Skype Kurumsal kendi depolama alanını kullanabilirsiniz. SharePoint Online hem depolama SQL Server Azure Depolama'i kullanır; dolayısıyla müşteri verilerini depolama düzeyinde fazladan ayırma ihtiyacı olur.

## <a name="exchange-online"></a>Exchange Online

Exchange Online verilerini posta kutuları içinde depolar. Posta kutuları, posta kutusu veritabanları olarak adlandırılan Genişletilebilir Depolama Altyapısı (ESE) veritabanlarında barındırılabilir. Bu, kullanıcı posta kutularını, bağlantılı posta kutularını, paylaşılan posta kutularını ve ortak klasör posta kutularını içerir. Kullanıcı posta kutuları, konuşma Skype Kurumsal gibi kaydedilmiş içerikler içerir.

Kullanıcı posta kutusu içeriği şunları içerir:

- E-postalar ve e-posta ekleri
- Takvim ve serbest/meşgul bilgileri
- Kişiler
- Görevler
- Notlar
- Gruplar
- Verileri çıkartır

E-posta Exchange Online posta kutusu veritabanı, birden çok kiracının posta kutularını içerir. Yetkilendirme kodu, bir kira da içinde olmak üzere her posta kutusunun güvenliğini sağlar. Varsayılan olarak, posta kutusuna yalnızca atanan kullanıcının erişimi olur. Posta kutusunun güvenliğini altına alan erişim denetim listesi (ACL), kiracı düzeyinde Azure AD tarafından kimliği doğrulanmış bir kimlik içerir. Her kiracının posta kutuları, kiracının kimlik doğrulaması sağlayıcısında kimliği doğrulanmış kimliklerle sınırlıdır ve bu kimlikler yalnızca o kiracıdan gelen kullanıcıları içerir. A kiracısı içeriği, A kiracısı tarafından açıkça onaylanmadı sürece, B kiracısı kullanıcıları tarafından hiçbir şekilde alınamaz.

## <a name="skype-for-business"></a>Skype Kurumsal

Skype Kurumsal çeşitli yerlerde depolar:

- Bağlantı uç noktaları, kiracı kimlikleri, arama planları, dolaşım ayarları, iletişim durumu, kişi listeleri vb. içeren kullanıcı ve hesap bilgileri, Skype Kurumsal Active Directory sunucularında ve çeşitli Skype Kurumsal veritabanı sunucularında depolanır. Kişi listeleri, kullanıcı hem ürün Exchange Online, hem de kullanıcı etkin değilse Skype Kurumsal sunucularında kullanıcının posta kutusunda depolanır. Skype Kurumsal veritabanı sunucuları kiracı başına bölümlenmiş değildir, ancak rol tabanlı erişim denetimi (RBAC) aracılığıyla verilerin çok kiracılı yalıtımsı zorunludur.
- Toplantı içeriği ve karşıya yüklenen veriler Dağıtılmış Dosya Sistemi (AİS) paylaşımlarda depolanır. Bu içerik, etkinleştirildiyse aynı zamanda Exchange Online arşivlenir. TABLO paylaşımları kiracı başına bölümlemez. içeriği ACL'lerle güvence altına alınır ve çok kiralanan alan RBAC aracılığıyla uygulanır.
- Arama geçmişi, IM oturumları, uygulama paylaşımı, IM geçmişi gibi etkinlik geçmişi olan arama ayrıntı kayıtları da Exchange Online'te depolansa da, arama ayrıntı kayıtlarının çoğu arama ayrıntı kaydı (CDR) sunucularında geçici olarak depolanır. İçerik kiracı başına bölümlemez, ancak RBAC aracılığıyla çok kiracılı kiracı uygulanır.

## <a name="sharepoint-online"></a>SharePoint Online

SharePoint Online'da veri yalıtım sağlayan çeşitli bağımsız mekanizmalar vardır. Nesneleri uygulama veritabanları içinde özet kod olarak depolar. Örneğin, bir kullanıcı dosyayı SharePoint Online'a yükledikten sonra dosya parçalarına çevrilir, uygulama koduna çevrilir ve birden çok veritabanında birden çok tabloda depolanır.

Kullanıcı verileri içeren depolama alanına doğrudan erişim elde ettiyse, içerik insanlar veya SharePoint Online dışında herhangi bir sistem için yorumlanmaz. Bu mekanizmalar, güvenlik erişimi denetimi ve özelliklerini içerir. Tüm SharePoint Çevrimiçi kaynakları, bir kiraya dahil olmak üzere yetkilendirme kodu ve RBAC ilkesi ile güvence altına alınır. Kaynağın kiracı düzeyinde kimliği doğrulanmış bir kimlik içerdiğini güvence altına alan erişim denetim listesi (ACL). SharePoint çevrimiçi verileri, kiracının kimlik doğrulama sağlayıcısı tarafından kimlik doğrulaması yapılan kimliklerle sınırlıdır.

ACL'lere ek olarak, kimlik doğrulama sağlayıcısını (kiracıya özgü Azure AD'ye) belirten kiracı düzeyi özelliği bir kez yazılır ve bir kez ayarlanamıyor. Kimlik doğrulama sağlayıcısı kiracı özelliği bir kiracı için ayarlanamıyorsa, kiracıya açık olan hiçbir API kullanılarak değiştirilemez.

Her kiracı *için benzersiz bir SubscriptionId* kullanılır. Tüm müşteri siteleri bir kiracıya aittir ve kiracıya benzersiz bir *SubscriptionId* atanır. *Sitenin SubscriptionId* özelliği bir kez yazılır ve kalıcıdır. Bir kiracıya atandıktan sonra, site farklı bir kiracıya taşınabilir. *SubscriptionId,* kimlik doğrulama sağlayıcısının güvenlik kapsamını oluşturmak için kullanılan anahtardır ve kiracıya bağlıdır.

SharePoint Online, içerik meta SQL Server depolaması Depolama Azure Depolama'i kullanır. İçerik deposu için bölüm anahtarı, site sitesinde *SiteId* SQL. SQL Online, bir SharePoint SQL düzeyindeki *SubscriptionId* denetimi kapsamında doğrulanmış bir *SiteId kullanır*.

SharePoint Online şifrelenmiş dosya içeriğini blob'lara Microsoft Azure depolar. Her SharePoint Online sunucu grubu kendi Microsoft Azure hesabına sahiptir ve Azure'da kaydedilen tüm blob'lar, SQL içerik mağazasında depolanan bir anahtarla tek tek şifrelenir. Yetkilendirme katmanı tarafından kodda korunan ve doğrudan son kullanıcıya açıkta yer alan şifreleme anahtarı. SharePoint Online'da HTTP isteğinin birden çok kiracı için verileri okuduğunda veya yazdığında algılayan gerçek zamanlı izleme vardır. İstek kimliği *SubscriptionId* , erişilen kaynağın *SubscriptionId'sinde* izilir. Birden çok kiracının kaynaklarına erişim istekleri, son kullanıcılar tarafından asla yaşanmaz. Çok kiracılı bir ortamdaki hizmet istekleri tek istisnadır. Örneğin, arama gezinicisi tüm veritabanının içerik değişikliklerini bir kerede alır. Bu genellikle, verimlilik nedenleriyle yapılan tek bir hizmet isteğinde birden çok kiracının sitelerini sorgulamayı içerir.

## <a name="teams"></a>Teams

Veri Teams, içerik türüne bağlı olarak farklı bir şekilde depolanır. 

Ayrıntılı bir tartışma [için Ignite ara oturumunu Microsoft Teams](https://channel9.msdn.com/Events/Ignite/Microsoft-Ignite-Orlando-2017/BRK3071) mimariye göz atabilirsiniz.

### <a name="core-teams-customer-data"></a>Temel Teams müşteri verileri

Kiracınız Avustralya, Kanada, Avrupa Birliği, Fransa, Almanya, Hindistan, Japonya, Güney Afrika, Güney Kore, İsviçre'de (Liechtenstein'ı içerir), Birleşik Arap Emirlikleri'nde, Birleşik Krallık'ta veya ABD'de sağlanıyorsa, Microsoft yalnızca bu konumda bulunan aşağıdaki müşteri verilerini depolar:

- Teams, ekip ve kanal görüşmelerini, resimleri, sesli mesajları ve kişileri görüntü olarak görüntüler.
- SharePoint Online site içeriğini ve bu site içinde depolanan dosyaları içerir.
- İş veya okul OneDrive dosyaları OneDrive dosyaları.

#### <a name="chat-channel-messages-team-structure"></a>Sohbet, kanal iletileri, ekip yapısı

E-posta Teams her ekip bir Microsoft 365 Grubu ve SharePoint posta kutusuyla Exchange vardır. Özel sohbetler (grup sohbetleri dahil), kanalda bir konuşmanın parçası olarak gönderilen iletiler ve ekiplerin ve kanalların yapısı, Azure'da çalışan bir sohbet hizmette depolanır. Ayrıca, Bilgi Koruması özelliklerini etkinleştirmek için veriler kullanıcı ve grup posta kutularında gizli bir klasörde depolanır.

#### <a name="voicemail-and-contacts"></a>Sesli mesaj ve kişiler

Sesli mesajları tek bir Exchange. Kişiler, Exchange bulut veri depolarında depolanır. Exchange ve Exchange tabanlı bulut deposu, dünya çapında veri merkezi coğrafilerinin her birsinde zaten veri ikameti sağlar. Tüm ekipler için sesli mesaj ve kişiler, Avustralya, Kanada, Fransa, Almanya, Hindistan, Japonya, Birleşik Arap Emirlikleri, Birleşik Krallık, Güney Afrika, Güney Kore, İsviçre (Liechtenstein'ı da içerir) ve ABD'de ülke içinde depolanır. Diğer tüm ülkelerde, dosyalar kiracıya yakınlığı temel Asia-Pacific ABD, Avrupa veya Asia-Pacific bir konumda depolanır.

#### <a name="images-and-media"></a>Resimler ve medya

Sohbetlerde kullanılan medyalar (depolanmış olmayan ama özgün Giphy hizmeti URL'sinin başvuru bağlantısı olan Giphy GIF'ler dışında, Giphy Microsoft dışı bir hizmettir) sohbet hizmetiyle aynı konumlara dağıtılan Azure tabanlı bir medya hizmetinde depolanır.

#### <a name="files"></a>Dosyalar

Kanalda birinin OneNote biri tarafından paylaşıldı olan dosyalar (Wiki ve Wiki dahil) ekibin SharePoint depolanır. Özel sohbette veya toplantı ya da arama sırasında paylaşılan dosyalar karşıya OneDrive paylaşan kullanıcının iş veya okul hesabı için hesapta depolanır. Exchange, SharePoint ve OneDrive zaten dünya çapında veri merkezi coğrafilerinin her birsinde veri ikameti sağlar. Dolayısıyla, mevcut müşteriler için tüm dosyalar, OneNote defterleri, Teams wiki içeriği ve Teams deneyiminin parçası olan posta kutuları, kiracıya yakınlığınıza bağlı olarak zaten bu konumda depolanır. Dosyalar Avustralya, Kanada, Fransa, Almanya, Hindistan, Japonya, Birleşik Arap Emirlikleri, Birleşik Krallık, Güney Afrika, Güney Kore ve İsviçre'de (Liechtenstein'ı da içerir) ülke içinde depolanır. Diğer tüm ülkelerde, dosyalar kiracıya yakınlığı temel alarak ABD, Avrupa veya Asya Pasifik konumunda depolanır.
