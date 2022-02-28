---
title: İleti Şifrelemesi
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 02/07/2020
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
ms.assetid: f87cb016-7876-4317-ae3c-9169b311ff8a
ms.custom:
- seo-marvel-apr2020
description: Kurum içindeki ve dışındaki kişiler arasında şifreli e-posta iletileri göndermeyi ve almayı öğrenin.
ms.openlocfilehash: 04c2ddd3bfb77199f924a10e29f23dc3d27cc38b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62986486"
---
# <a name="message-encryption"></a>İleti Şifrelemesi

İnsanlar genellikle mali veriler, yasal sözleşmeler, gizli ürün bilgileri, satış raporları ve projeksiyonlar, hasta durumu bilgileri veya müşteri ve çalışan bilgileri gibi hassas bilgileri almak için e-posta kullanır. Sonuç olarak, posta kutuları büyük miktarlarda potansiyel hassas bilgiler için depolar haline gelir ve bilgi sızıntıları da organizasyonunız için önemli bir tehdit haline gelir.

Bu Office 365 İleti Şifrelemesi, kuruluş içindeki ve dışındaki kişiler arasında şifrelenmiş e-posta iletileri gönderebilir ve alabilirsiniz. Office 365 İleti Şifrelemesi e-posta Outlook.com, Yahoo!, Gmail ve diğer e-posta hizmetleriyle çalışır. E-posta iletisi şifrelemesi, yalnızca hedeflenen alıcıların ileti içeriğini görüntüleyemelerini sağlamaya yardımcı olur.

## <a name="how-office-365-message-encryption-works"></a>Office 365 İleti Şifrelemesi nasıl çalışır?

Bu makalenin kalan bölümü yeni OME özellikleri için geçerlidir.

Office 365 İleti Şifrelemesi, Azure Information Protection'ın bir parçası olan Microsoft Azure Hak Yönetimi'ne (Azure RMS) bağlı bir çevrimiçi hizmettir. Bu hizmet, e-postanızı güvenlik altına almak için şifreleme, kimlik ve yetkilendirme ilkelerini içerir. Hak yönetimi şablonlarını, İletileri Iletme [seçeneğini](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails) ve yalnızca şifrele [seçeneğini kullanarak iletileri şifreebilirsiniz](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

Kullanıcılar bu seçenekleri kullanarak e-posta iletilerini ve çeşitli ekleri şifreler. Desteklenen ek türlerinin tam listesi için, E-posta iletileri için IRM'ye giriş altında yer alan "İletilere ekli olduğunda IRM ilkeleri kapsamındaki dosya türleri [" bölüme bakın](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM).

Yönetici olarak, bu korumayı uygulamak için posta akış kuralları da tanımlayabilirsiniz. Örneğin, belirli bir alıcıya gönderilen tüm iletilerin şifrelenirken şifrelenirken gerekli olduğu veya konu satırına belirli sözcükler ek içeren bir kural oluşturabilir ve alıcıların iletinin içeriğini kopyalayıp yazdıramayacaklarını belirtebilirsiniz.

OME'nin önceki sürümünden farklı olarak, yeni özellikler hem kuruluşun içinden hem de postanın dışındaki alıcılara posta gönderirken birleşik bir gönderen deneyimi Microsoft 365. Buna ek olarak, Outlook 2016 veya Web üzerinde Outlook'te bir Microsoft 365 hesabına gönderilmiş korumalı bir e-posta iletisi alan alıcıların, iletiyi görüntülemek için başka bir işlem yapmak zorunda değil. Sorunsuz çalışır. Diğer e-posta istemcilerini ve e-posta servis sağlayıcılarını kullanan alıcıların da deneyimi iyileştirildi. Bilgi için bkz[. E-posta iletileri Office 365](https://support.office.com/article/Learn-about-protected-messages-in-Office-365-2baf3ac7-12db-40a4-8af7-1852204b4b67) [hakkında bilgi ve Korumalı bir iletiyi nasıl açarim](https://support.office.com/article/How-do-I-open-a-protected-message-1157a286-8ecc-4b1e-ac43-2a608fbf3098)?

Önceki OME sürümüyle yeni OME özellikleri arasındaki farkların ayrıntılı bir listesi için bkz. [OME sürümlerini karşılaştırma](ome-version-comparison.md).

Birisi bir şifreleme posta akışı kuralıyla eşleşen bir e-posta iletisi gönderdiğinda, ileti gönderilmeden önce şifrelenir. E Microsoft 365 okumak için Outlook istemcilerini kullanan tüm son kullanıcılar, gönderenle aynı kuruluşta yer almasalar bile, şifrelenmiş ve hak korunan postalar için yerel ve birinci sınıf okuma deneyimleri alır. Desteklenen Outlook istemciler Outlook masaüstü, Outlook Mac, iOS Outlook Android'de mobil ve Web üzerinde Outlook (eski adı Outlook Web App) içerir.

Outlook.com, Gmail ve Yahoo hesaplarına gönderilen şifrelenmiş veya hak korumalı posta alan şifreli iletilerin alıcıları, onları Microsoft hesabı, Gmail veya Yahoo kimlik bilgileri kullanarak kolayca kimlik doğrulaması yapmaları için OME Portalına yönlendiren bir paket posta alırlar.

E-posta adresleri dışında istemcilerde şifrelenmiş veya hak korumalı posta Outlook son kullanıcılar, bu iletilerin şifrelenmiş ve hak korumalı iletileri görüntülemek için de OME portalını kullanır.

Korumalı postanın göndereni GCC Yüksek düzeyde ise ve alıcı ticari kullanıcılar, Outlook.com kullanıcıları ve Gmail gibi diğer e-posta sağlayıcılarının kullanıcıları da dahil olmak üzere GCC High dışında olursa, alıcıya paketli posta gönderilir. Paketlayıcı posta, alıcıyı iletiyi okuyabilecek ve yanıtlayabilecek olduğu OME Portalı'na gönderir. Aksi takdirde, gönderen ve alıcı aynı kuruluşta yer almasa bile, gönderen ve alıcı GCC Yüksek ortamında yer alsa bile, posta okumak için Outlook istemcilerini kullanan alıcılar, şifrelenmiş ve hak korumalı posta için yerel, birinci sınıf okuma deneyimleri alırlar. GCC High'daki farklı deneyim hakkında daha fazla bilgi için bkz. [OME sürümlerini karşılaştırma](ome-version-comparison.md).

OME kullanarak şifreleyebilirsiniz ileti ve eklerin boyut sınırları hakkında daha fazla bilgi için bkz. Exchange Online [tıklayın](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits).

## <a name="how-office-365-advanced-message-encryption-works-on-top-of-ome"></a>Office 365 Gelişmiş İleti Şifrelemesi OME'de nasıl çalışır?

Office 365 Gelişmiş İleti Şifrelemesi, birden çok markalama şablonu oluşturmanıza olanak sağlar, böylece alıcı postası üzerinde hassas denetime sahip olabilir ve farklı bir kuruluş yapısını destekleyecek özel markalama deneyimleri oluşturabilirsiniz.

Gelişmiş İleti Şifrelemesi Microsoft 365 dış alıcının şifreli e-postalara erişimi üzerinde daha esnek bir denetim gerektiren uyumluluk yükümlülüklerini karşılamanıza yardımcı olur. Office 365'ta Gelişmiş İleti Şifreleme ile, yönetici olarak kuruluş dışında paylaşılan hassas e-postaları, hassas bilgi türlerini (örneğin, PII, Finansal veya Sistem Durumu Kimlikleri) veya anahtar sözcükleri algılayan otomatik ilkelerle ve şifreli e-postalara güvenli bir web portalı aracılığıyla erişimin süresi dolarak korumayı geliştiren anahtar sözcükleri kontrol edebilirsiniz. Yönetici olarak, bir web portalı aracılığıyla erişilen şifrelenmiş e-Microsoft 365 istediğiniz zaman e-posta erişimini iptal edebilirsiniz.

İleti iptali ve süre sonu yalnızca kullanıcılarının kuruluş dışındaki alıcılara göndermesi gereken e-postalar için kullanılabilir. Buna ek olarak, alıcıların e-postaya web portalı üzerinden erişmeleri gerekir. Alıcının e-postayı almak için portalı kullandığıdan emin olmak için, kaydırmayı kullanan özel bir markalama şablonu oluşturursanız. Ardından, markalama şablonunu bir posta akışı kuralına uygulayabilirsiniz. Gelişmiş İleti Şifrelemesi hakkında daha fazla bilgi için bkz. [Office 365 Gelişmiş İleti Şifrelemesi](ome-advanced-message-encryption.md).

## <a name="defining-rules-for-office-365-message-encryption"></a>Kurallar tanımlama Office 365 İleti Şifrelemesi

E-postayla ilgili yeni özellikleri Office 365 İleti Şifrelemesi bir yolu, posta Exchange Online yöneticilerinin Exchange Online Protection kurallarını tanımlamalarını sağlamaktır. Bu kurallar, e-posta iletilerinin hangi koşullarda şifrelenmeleri gerektiğini belirler. Bir şifreleme eylemi kural için ayar olduğunda, kural koşullarına uygun tüm iletiler gönderilmeden önce şifrelenir.

Posta akış kuralları esnektir ve koşulları bir araya getirir ve böylelikle tek bir kuralda belirli güvenlik gereksinimlerini karşılar. Örneğin, belirtilen anahtar sözcükleri içeren ve dış alıcılara gönderilen tüm iletileri şifrelemek için bir kural oluşturabilirsiniz. E-posta Office 365 İleti Şifrelemesi yeni özellikleri, şifrelenmiş e-posta alıcılarından gelen yanıtları da şifreler.

Yeni OME yeteneklerine sahip olmak için posta akış kuralları oluşturma hakkında daha fazla bilgi için bkz. Posta akış [kuralları Office 365 İleti Şifrelemesi](define-mail-flow-rules-to-encrypt-email.md).

## <a name="get-started-with-the-new-ome-capabilities"></a>Yeni OME özelliklerini çalışmaya başlama

Kurum içindeki yeni OME özelliklerini kullanmaya başlamaya hazırsanız bkz. Yeni kullanıcı [Office 365 İleti Şifrelemesi ayarlama](set-up-new-message-encryption-capabilities.md).

## <a name="sending-viewing-and-replying-to-encrypted-email-messages"></a>Şifreli e-posta iletilerini gönderme, görüntüleme ve yanıtlama

Daha Office 365 İleti Şifrelemesi, kullanıcılar e-posta adreslerine posta Outlook e-Web üzerinde Outlook. Ayrıca yöneticiler, e-postaları anahtar sözcük eşleştirme veya diğer Microsoft 365 göre otomatik olarak şifrelemek için E-posta'da posta akış kuralları da hazırlar.

Kuruluşlarda yer alan şifrelenmiş iletilerin alıcıları, bu iletileri PC için Outlook, Mac için Outlook, Web üzerinde Outlook, iOS için Outlook ve Android için Outlook gibi herhangi bir Outlook sürümünde sorunsuz okuyabilir. Diğer e-posta istemcilerine şifrelenmiş iletiler alan kullanıcılar, OME portalında iletileri tikler.

Şifreli iletileri gönderme ve görüntüleme hakkında ayrıntılı kılavuz için, şu makalelere göz atabilirsiniz.

|Bu makaleyi okuyun...|Şu isanız...|
|:-----|:-----|
|[E-posta iletileriyle ilgili bilgi Office 365](https://support.office.com/article/2baf3ac7-12db-40a4-8af7-1852204b4b67.aspx)|Şifreli iletilerin nasıl olduğu ve sizin için hangi seçeneklerin kullanılabilir olduğu hakkında daha fazla bilgi edinmek isteyen son kullanıcı.|
|[Korumalı bir iletiyi nasıl açarim?](https://support.office.com/article/1157a286-8ecc-4b1e-ac43-2a608fbf3098.aspx)|Size gönderilen korumalı iletiyi okumak isteyen son kullanıcı. Bu makalede, Outlook Microsoft 365'un çeşitli sürümlerindeki ve gmail ve Yahoo! hesapları için bir hesap açın.|
|[E-posta iletisinde şifreli iletileri gönderme, görüntüleme ve Outlook](https://support.microsoft.com/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980)|Posta iletilerinden şifreli bir iletiyi göndermek, görüntülemek veya yanıtlamak isteyen son Outlook. Bir kuruluşun üyesi olmadığınız bile, size gönderilen şifrelenmiş iletilerin bildirimini e-posta iletisinde almaya devam Outlook. E-postadan gönderilen şifrelenmiş iletileri görüntüleme ve yanıtlama yönergeleri için bu Office 365.|
|[Dijital olarak imzalanmış veya şifrelenmiş ileti gönderme](https://support.microsoft.com/office/send-a-digitally-signed-or-encrypted-message-a18ecf7f-a7ac-4edd-b02e-687b05eff547)|Şifreli iletileri e-posta iletileri göndermek, görüntülemek veya yanıtlamak isteyen son Mac için Outlook. Bu makale, S/MIME gibi OME dışında şifreleme yöntemlerini kullanmayı da kapsar.|
|[Şifrelenmiş iletileri Android aygıtınızda görüntüleme](https://support.office.com/article/83d60f17-2305-407a-a762-7d518401fdeb)|Android aygıtınızda Office 365 İleti Şifrelemesi ile şifrelenmiş bir ileti alan son kullanıcı, iletiyi görüntülemek ve şifrelenmiş bir yanıt göndermek için ücretsiz OME Görüntüleyicisi uygulamasını kullanabilirsiniz. Bu makalede nasıl olduğu açıklanmıştır.|
|[E-posta iletilerinizin veya iletilerinizin iPhone iPad](https://support.microsoft.com/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf)|iPhone veya iPad üzerinde Office 365 İleti Şifrelemesi ile şifrelenmiş bir ileti alan son kullanıcı, iletiyi görüntülemek ve şifrelenmiş bir yanıt göndermek için ücretsiz OME Görüntüleyicisi uygulamasını kullanabilirsiniz. Bu makalede nasıl olduğu açıklanmıştır.|
||