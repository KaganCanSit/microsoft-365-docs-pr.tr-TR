---
title: Office 365 İleti Şifrelemesi
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
description: Kuruluşunuzun içindeki ve dışındaki kişiler arasında şifreli e-posta iletileri göndermeyi ve almayı öğrenin.
ms.openlocfilehash: 746a1cbb1d4fa5e98fb3fc3cbba529232178987c
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66640576"
---
# <a name="message-encryption"></a>İleti Şifrelemesi

İnsanlar genellikle finansal veriler, yasal sözleşmeler, gizli ürün bilgileri, satış raporları ve projeksiyonlar, hasta sağlığı bilgileri veya müşteri ve çalışan bilgileri gibi hassas bilgileri değiştirmek için e-posta kullanır. Sonuç olarak, posta kutuları büyük miktarlarda hassas olabilecek bilgiler için depolara dönüşebilir ve bilgi sızıntısı kuruluşunuz için ciddi bir tehdit haline gelebilir.

Office 365 İleti Şifrelemesi ile kuruluşunuz, kuruluşunuzun içindeki ve dışındaki kişiler arasında şifreli e-posta iletileri gönderebilir ve alabilir. Office 365 İleti Şifrelemesi Outlook.com, Yahoo!, Gmail ve diğer e-posta hizmetleriyle çalışır. E-posta iletisi şifrelemesi, yalnızca hedeflenen alıcıların ileti içeriğini görüntüleyebilmesine yardımcı olur.

## <a name="how-message-encryption-works"></a>İleti Şifrelemesi nasıl çalışır?

Bu makalenin geri kalanı Microsoft Purview İleti Şifrelemesi için geçerlidir.

Microsoft Purview İleti Şifrelemesi, Azure Information Protection'nin bir parçası olan Microsoft Azure Rights Management (Azure RMS) üzerinde oluşturulmuş bir çevrimiçi hizmettir. Bu hizmet e-postanızın güvenliğini sağlamaya yardımcı olmak için şifreleme, kimlik ve yetkilendirme ilkelerini içerir. İletileri, hak yönetimi şablonlarını, [İletme seçeneğini](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails) ve [yalnızca şifrele seçeneğini kullanarak şifreleyebilirsiniz](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

Kullanıcılar daha sonra bu seçenekleri kullanarak e-posta iletilerini ve çeşitli ekleri şifreleyebilir. Desteklenen ek türlerinin tam listesi için, [E-posta iletileri için IRM'ye giriş bölümündeki "İletilere eklendiklerinde IRM ilkelerinin kapsadığı dosya türleri"](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM) bölümüne bakın.

Yönetici olarak, bu korumayı uygulamak için posta akışı kuralları da tanımlayabilirsiniz. Örneğin, belirli bir alıcıya gönderilen tüm iletilerin şifrelenmesini gerektiren veya konu satırında belirli sözcükler içeren bir kural oluşturabilir ve ayrıca alıcıların iletinin içeriğini kopyalayamaz veya yazdıramazsınız.

OME'nin önceki sürümünden farklı olarak yeni özellikler, kuruluşunuzun içinden veya Microsoft 365 dışındaki alıcılara posta gönderirken birleşik bir gönderen deneyimi sağlar. Ayrıca, Outlook 2016 veya Web üzerinde Outlook microsoft 365 hesabına gönderilen korumalı bir e-posta iletisi alan alıcıların iletiyi görüntülemek için başka bir eylemde bulunmaları gerekmez. Sorunsuz çalışır. Diğer e-posta istemcilerini ve e-posta hizmeti sağlayıcılarını kullanan alıcılar da gelişmiş bir deneyime sahiptir. Bilgi için bkz. [Office 365 korumalı iletiler hakkında bilgi edinme](https://support.office.com/article/Learn-about-protected-messages-in-Office-365-2baf3ac7-12db-40a4-8af7-1852204b4b67) ve [korumalı ileti açma Nasıl yaparım?](https://support.office.com/article/How-do-I-open-a-protected-message-1157a286-8ecc-4b1e-ac43-2a608fbf3098).

OME'nin önceki sürümüyle Microsoft Purview İleti Şifrelemesi arasındaki farkların ayrıntılı listesi için bkz. [İleti şifrelemesinin sürümlerini karşılaştırma](ome-version-comparison.md).

Birisi şifreleme posta akışı kuralıyla eşleşen bir e-posta iletisi gönderdiğinde, ileti gönderilmeden önce şifrelenir. Posta okumak için Outlook istemcilerini kullanan tüm Microsoft 365 son kullanıcıları, gönderenle aynı kuruluşta olmasalar bile şifrelenmiş ve hak korumalı postalar için yerel, birinci sınıf okuma deneyimleri alır. Desteklenen Outlook istemcileri Outlook masaüstü, Outlook Mac, iOS ve Android üzerinde Outlook mobile ve Web üzerinde Outlook (eski adıyla Outlook Web App) içerir.

Outlook.com, Gmail ve Yahoo hesaplarına gönderilen şifrelenmiş veya hak korumalı posta alan şifrelenmiş iletilerin alıcıları, microsoft hesabı, Gmail veya Yahoo kimlik bilgilerini kullanarak kolayca kimlik doğrulaması yapabilecekleri OME Portalı'na yönlendiren bir sarmalayıcı posta alır.

Outlook dışındaki istemcilerde şifrelenmiş veya hak korumalı posta okuyan son kullanıcılar, aldıkları şifrelenmiş ve hak korumalı iletileri görüntülemek için OME portalını da kullanır.

Korumalı postayı gönderen GCC High'daysa ve alıcı ticari kullanıcılar, Outlook.com kullanıcılar ve Gmail gibi diğer e-posta sağlayıcılarının kullanıcıları da dahil olmak üzere GCC High'ın dışındaysa, alıcı bir sarmalayıcı posta alır. Sarmalayıcı posta, alıcıyı, alıcının iletiyi okuyup yanıtlayabildiği OME Portalı'na yönlendirir. Aksi takdirde, gönderen ve alıcı aynı kuruluşta olmasalar bile GCC High ortamındaysa, posta okumak için Outlook istemcilerini kullanan alıcılar şifrelenmiş ve hak korumalı postalar için yerel, birinci sınıf okuma deneyimleri alır. GCC High'daki farklı deneyim hakkında daha fazla bilgi için bkz. [OME sürümlerini karşılaştırma](ome-version-comparison.md).

OME kullanarak şifreleyebileceğiniz iletilerin ve eklerin boyut sınırları hakkında daha fazla bilgi için bkz. [Exchange Online Sınırları](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits).

## <a name="how-microsoft-purview-advanced-message-encryption-works-on-top-of-microsoft-purview-message-encryption"></a>Microsoft Purview Gelişmiş İleti Şifrelemesi Microsoft Purview İleti Şifrelemesi üzerinde nasıl çalışır?

Microsoft Purview Gelişmiş İleti Şifrelemesi, birden çok markalama şablonu oluşturmanıza olanak tanır, böylece alıcı postası üzerinde ince ayar yapabilir ve farklı bir kurumsal yapıyı desteklemek için özel markalama deneyimleri oluşturabilirsiniz.

Microsoft 365'teki Gelişmiş İleti Şifrelemesi, dış alıcının şifrelenmiş e-postalara erişimi üzerinde daha esnek denetim gerektiren uyumluluk yükümlülüklerini karşılamanıza yardımcı olur. Yönetici olarak Gelişmiş İleti Şifrelemesi ile, güvenli bir web portalı üzerinden şifrelenmiş e-postalara erişimin süresi dolarak korumayı geliştirmek için hassas bilgi türlerini (örneğin, PII, Finansal veya Sistem Durumu Kimlikleri) veya anahtar sözcükleri algılayan otomatik ilkelerle kuruluş dışında paylaşılan hassas e-postaları denetleyebilirsiniz. Yönetici olarak, istediğiniz zaman bir e-postaya erişimi iptal ederek web portalı üzerinden erişilen şifrelenmiş e-postaları daha fazla denetleyebilirsiniz.

İleti iptali ve süre sonu yalnızca kullanıcılarınızın kuruluşunuzun dışındaki alıcılara gönderdiği e-postalarda çalışır. Ayrıca, alıcıların web portalı üzerinden e-postaya erişmesi gerekir. Alıcının e-posta almak için portalı kullandığından emin olmak için sarmalayıcıyı uygulayan özel bir markalama şablonu ayarlarsınız. Ardından, marka şablonunu bir posta akışı kuralına uygularsınız. Gelişmiş İleti Şifrelemesi hakkında daha fazla bilgi için bkz. [Gelişmiş İleti Şifrelemesi](ome-advanced-message-encryption.md).

## <a name="defining-rules-for-microsoft-purview-message-encryption"></a>Microsoft Purview İleti Şifrelemesi için kurallar tanımlama

Microsoft Purview İleti Şifrelemesi etkinleştirmenin bir yolu, Exchange Online ve Exchange Online Protection yöneticilerinin posta akışı kurallarını tanımlamasıdır. Bu kurallar, e-posta iletilerinin hangi koşullarda şifreleneceğini belirler. Bir kural için şifreleme eylemi ayarlandığında, kural koşullarıyla eşleşen tüm iletiler gönderilmeden önce şifrelenir.

Posta akışı kuralları esnektir ve koşulları birleştirerek belirli güvenlik gereksinimlerini tek bir kuralda karşılamanızı sağlar. Örneğin, belirtilen anahtar sözcükleri içeren ve dış alıcılara gönderilen tüm iletileri şifrelemek için bir kural oluşturabilirsiniz. Microsoft Purview İleti Şifrelemesi şifrelenmiş e-posta alıcılarından gelen yanıtları da şifreleyin.

Microsoft Purview İleti Şifrelemesi yararlanmak için posta akışı kuralları oluşturma hakkında daha fazla bilgi için bkz. [E-posta iletilerini şifrelemek için posta akışı kuralları tanımlama](define-mail-flow-rules-to-encrypt-email.md).

## <a name="get-started-with-the-microsoft-purview-message-encryption"></a>Microsoft Purview İleti Şifrelemesi kullanmaya başlama

Kuruluşunuzdaki Microsoft Purview İleti Şifrelemesi kullanmaya başlamaya hazırsanız bkz. [Microsoft Purview İleti Şifrelemesi ayarlama](set-up-new-message-encryption-capabilities.md).

## <a name="sending-viewing-and-replying-to-encrypted-email-messages"></a>Şifrelenmiş e-posta iletilerini gönderme, görüntüleme ve yanıtlama

Microsoft Purview İleti Şifrelemesi ile kullanıcılar Outlook'tan ve Web üzerinde Outlook şifrelenmiş e-posta gönderebilir. Ayrıca yöneticiler, anahtar sözcük eşleştirme veya diğer koşullara göre e-postaları otomatik olarak şifrelemek için Microsoft 365'te posta akışı kuralları ayarlayabilir.

Kuruluşlardaki şifrelenmiş iletilerin alıcıları pc için Outlook, Mac için Outlook, Web üzerinde Outlook, iOS için Outlook ve Android için Outlook dahil olmak üzere tüm Outlook sürümlerinde bu iletileri sorunsuz bir şekilde okuyabilir. Diğer e-posta istemcilerinde şifrelenmiş iletiler alan kullanıcılar, iletileri OME portalında görüntüleyebilir.

Şifrelenmiş iletileri gönderme ve görüntüleme hakkında ayrıntılı yönergeler için bu makalelere göz atın.

|Bu makaleyi okuyun...|Eğer...|
|:-----|:-----|
|[Office 365'de korumalı iletiler hakkında bilgi edinin](https://support.office.com/article/2baf3ac7-12db-40a4-8af7-1852204b4b67.aspx)|Şifrelenmiş iletilerin nasıl çalıştığı ve kullanabileceğiniz seçenekler hakkında daha fazla bilgi edinmek isteyen bir son kullanıcı.|
|[Korumalı bir iletiyi Nasıl yaparım? aç?](https://support.office.com/article/1157a286-8ecc-4b1e-ac43-2a608fbf3098.aspx)|Size gönderilen korumalı bir iletiyi okumak isteyen son kullanıcı. Bu makale, Outlook'un çeşitli sürümlerinde ve Gmail ve Yahoo! gibi Microsoft 365 dışındaki hesaplar da dahil olmak üzere farklı e-posta hesaplarından gelen iletileri okuma hakkında bilgi içerir Hesap.|
|[Outlook'ta şifrelenmiş iletileri gönderme, görüntüleme ve yanıtlama](https://support.microsoft.com/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980)|Outlook'tan şifrelenmiş bir iletiyi göndermek, görüntülemek veya yanıtlamak isteyen bir son kullanıcı. Bir kuruluşun üyesi olmasanız bile, Outlook'ta size gönderilen şifrelenmiş iletilerin bildirimini almaya devam edebilirsiniz. Office 365 gönderilen şifrelenmiş iletileri görüntüleme ve yanıtlama yönergeleri için bu makaleyi kullanın.|
|[Dijital olarak imzalanmış veya şifrelenmiş ileti gönderme](https://support.microsoft.com/office/send-a-digitally-signed-or-encrypted-message-a18ecf7f-a7ac-4edd-b02e-687b05eff547)|Mac için Outlook kullanarak şifrelenmiş iletileri göndermek, görüntülemek veya yanıtlamak isteyen bir son kullanıcı. Bu makale, S/MIME gibi OME dışındaki şifreleme yöntemlerini kullanmayı da kapsar.|
|[Android cihazınızda şifrelenmiş iletileri görüntüleme](https://support.office.com/article/83d60f17-2305-407a-a762-7d518401fdeb)|Android cihazınızda Office 365 İleti Şifrelemesi ile şifrelenmiş bir ileti alan son kullanıcı, iletiyi görüntülemek ve şifreli bir yanıt göndermek için ücretsiz OME Görüntüleyicisi uygulamasını kullanabilirsiniz. Bu makalede nasıl yapılır açıklanmaktadır.|
|[iPhone veya iPad'inizde şifrelenmiş iletileri görüntüleme](https://support.microsoft.com/office/view-protected-messages-on-your-iphone-or-ipad-4d631321-0d26-4bcc-a483-d294dd0b1caf)|iPhone veya iPad'inizde Office 365 İleti Şifrelemesi ile şifrelenmiş bir ileti alan son kullanıcı, iletiyi görüntülemek ve şifreli bir yanıt göndermek için ücretsiz OME Görüntüleyicisi uygulamasını kullanabilirsiniz. Bu makalede nasıl yapılır açıklanmaktadır.|
||
