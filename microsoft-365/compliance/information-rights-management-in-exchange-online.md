---
title: AD RMS ile Exchange Online posta şifrelemesi
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/13/2017
audience: End User
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 2c956776-0016-4be6-b4cd-133a237f4a9e
ms.custom:
- seo-marvel-apr2020
description: Exchange Online IRM'yi kuruluşunuzun gereksinimlerini karşılamak için şirket içi Active Directory Rights Management Service'i (AD RMS) kullanacak şekilde yapılandırmayı öğrenin.
ms.openlocfilehash: 926bea0b1f9379d2eaad2bc7c5bd672f98329b8a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66628803"
---
# <a name="exchange-online-mail-encryption-with-ad-rms"></a>AD RMS ile Exchange Online posta şifrelemesi

Bilgi sızıntısını önlemeye yardımcı olmak için Exchange Online, e-posta iletilerinin ve eklerinin çevrimiçi ve çevrimdışı korunmasını sağlayan Bilgi Hakları Yönetimi (IRM) işlevselliğini içerir. Exchange Online IRM'yi, kuruluşunuzun gereksinimlerini karşılamak için gerekirse şirket içi Active Directory Rights Management Service'i (AD RMS) kullanacak şekilde yapılandırabilirsiniz. Bu yaygın bir durum değildir. AD RMS kullanma gereksiniminiz yoksa bunun yerine [Microsoft Purview İleti Şifrelemesi](ome.md) kullanın.

IRM koruması Microsoft Outlook veya Web üzerinde Outlook kullanıcıları tarafından uygulanabilir ve yöneticiler tarafından aktarım koruma kuralları veya Outlook koruma kuralları kullanılarak uygulanabilir. IRM, sizin ve kullanıcılarınızın e-posta içindeki hassas verilere kimlerin erişebileceğini, iletebileceğini, yazdırabileceğini veya kopyalayabileceğini denetlemenize yardımcı olur.
  
## <a name="changes-to-how-irm-works-with-message-encryption-and-azure-active-directory"></a>İleti şifreleme ve Azure Active Directory ile IRM'nin çalışma şeklindeki değişiklikler

Eylül 2017 itibarıyla, kuruluşunuz için Microsoft Purview İleti Şifrelemesi ayarladığınızda, IRM'yi Azure Rights Management (Azure RMS) ile kullanılacak şekilde de ayarlarsınız. Artık Azure RMS ile IRM'i ayrı olarak ayarlamazsınız. Bunun yerine, ileti şifreleme ve hak yönetimi birlikte sorunsuz bir şekilde çalışır. Microsoft Purview İleti Şifrelemesi hakkında daha fazla ayrıntı için bkz. [İleti Şifrelemesi SSS](./ome-faq.yml). Kuruluşunuzdaki Microsoft Purview İleti Şifrelemesi kullanmaya başlamaya hazırsanız bkz. [Microsoft Purview İleti Şifrelemesi ayarlama](./set-up-new-message-encryption-capabilities.md).
  
## <a name="how-irm-works-with-exchange-online-and-active-directory-rights-management-services"></a>IRM Exchange Online ve Active Directory Rights Management Services ile nasıl çalışır?

Exchange Online IRM, Windows Server 2008 ve sonraki sürümlerde bir bilgi koruma teknolojisi olan şirket içi Active Directory Rights Management Services'ı (AD RMS) kullanır. E-posta iletisine AD RMS hak ilkesi şablonu uygulanarak e-postaya IRM koruması uygulanır. Korumanın çevrimiçi, çevrimdışı ve kuruluşunuzun güvenlik duvarının içinde ve dışında gerçekleşmesi için, haklar iletinin kendisine eklenir.
  
Kullanıcılar, alıcıların iletideki izinlerini denetlemek için bir e-posta iletisine şablon uygulayabilir. İletiye iletme, iletiden bilgi ayıklama, ileti kaydetme veya ileti yazdırma gibi eylemler, iletiye bir AD RMS hak ilkesi uygulanarak denetlenebilir.
  
IRM'yi Windows Server 2008 veya üzerini çalıştıran bir AD RMS sunucusu kullanacak şekilde yapılandırabilirsiniz. Bulut tabanlı kuruluşunuz için AD RMS hak ilkesi şablonlarını yönetmek için bu AD RMS sunucusunu kullanabilirsiniz. Outlook, kullanıcıların gönderdikleri iletilere IRM koruması uygulamasına olanak tanımak için AD RMS sunucusuna da dayanır. Ayrıntılar için bkz. [IRM'yi şirket içi AD RMS sunucusu kullanacak şekilde yapılandırma](configure-irm-to-use-an-on-premises-ad-rms-server.md).
  
Etkinleştirildikten sonra IRM koruması iletilere aşağıdaki gibi uygulanabilir:
  
- **Kullanıcılar Outlook ve Web üzerinde Outlook kullanarak el ile şablon uygulayabilir.** Kullanıcılar, **izinleri ayarla** listesinden şablonu seçerek bir e-posta iletisine AD RMS hak ilkesi şablonu uygulayabilir. Kullanıcılar IRM korumalı bir ileti gönderdiğinde, desteklenen biçimi kullanan ekli dosyalar da iletiyle aynı IRM korumasını alır. IRM koruması Word, Excel ve PowerPoint ile ilişkilendirilmiş dosyalara, ayrıca .xps dosyalarına ve ekli e-posta iletilerine uygulanır.

- **Yöneticiler, hem Outlook'a hem de Web üzerinde Outlook otomatik olarak IRM koruması uygulamak için aktarım koruma kurallarını kullanabilir.** IRM korumalı iletilere aktarım koruma kuralları oluşturabilirsiniz. Aktarım koruma kuralı eylemini, kural koşulunu karşılayan iletilere AD RMS hak ilkesi şablonu uygulayacak şekilde yapılandırın. IRM'yi etkinleştirdikten sonra, kuruluşunuzun AD RMS hak ilkesi şablonları, **ile iletiye hak korumasını uygula** adlı aktarım koruma kuralı eylemiyle kullanılabilir.

- **Yöneticiler Outlook koruma kuralları oluşturabilir.** Outlook koruma kuralları, gönderenin bölümünü, iletinin kime gönderildiğini ve alıcıların kuruluşunuzun içinde veya dışında olup olmadığını içeren ileti koşullarına göre Outlook 2010'daki iletilere (Web üzerinde Outlook değil) otomatik olarak IRM koruması uygular. Ayrıntılar için bkz. [Outlook Koruma Kuralı Oluşturma](/exchange/create-an-outlook-protection-rule-exchange-2013-help).
