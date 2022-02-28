---
title: Exchange Online RMS ile posta şifrelemesi
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
description: IRM'yi, Exchange Online gereksinimlerini karşılamak üzere şirket içi Active Directory Rights Management Service (AD RMS) kullanmak üzere yapılandırmayı öğrenin.
ms.openlocfilehash: 867293d5afa29242409cc92702ff8b505ed21196
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984692"
---
# <a name="exchange-online-mail-encryption-with-ad-rms"></a>Exchange Online RMS ile posta şifrelemesi

E-posta iletilerinin ve eklerin Exchange Online çevrimiçi ve çevrimdışı korunmasını sağlayan Bilgi Hakları Yönetimi (IRM) işlevselliği, bilgi sızıntısını önlemeye yardımcı olur. Gerekirse, Exchange Online gereksinimlerinizi karşılamak için IRM'yi şirket içi Active Directory Rights Management Service'i (AD RMS) kullanmak üzere yapılandırabilirsiniz. Bu sık karşılaşılan bir durum değildir. AD RMS'yi kullanmak için gereksiniminiz yoksa, [bunun yerine OFFICE 365 İLETI ŞIFRELEMESI](ome.md) kullanın. 

IRM koruması, Microsoft Outlook veya Web üzerinde Outlook'daki kullanıcılar tarafından uygulanabilir ve aktarım koruma kurallarını veya toplu koruma kurallarını Outlook tarafından uygulanabilir. IRM, sizin ve kullanıcılarının e-posta içinde hassas verilere kimlerin eriş erişeb, ilet, yazdırılabilir veya kopyalayıp kopyalay kullanıcılar tarafından kontrol musunuz? denetlemenize yardımcı olur.
  
## <a name="changes-to-how-irm-works-with-office-365-message-encryption-ome-and-azure-active-directory"></a>IRM'nin IRM'de (OME) Office 365 İleti Şifrelemesi çalışma ve çalışma Azure Active Directory

Eylül 2017'den itibaren, Office 365 İleti Şifrelemesi özellikleri ayar tarihine kadar IRM'yi Azure Rights Management (Azure RMS) ile kullanmak üzere de ayarlamıştınız. Artık IRM'yi Azure RMS ile ayrı olarak ayarlamazsınız. Bunun yerine, OME ve hak yönetimi sorunsuz bir şekilde birlikte çalışır. Yeni özellikler hakkında daha fazla ayrıntı için bkz. [SSS Office 365 İleti Şifrelemesi bakın](./ome-faq.yml). Kurum içindeki yeni OME özelliklerini kullanmaya başlamaya hazırsanız, bkz. [Azure Information Protection'ın Office 365 İleti Şifrelemesi](./set-up-new-message-encryption-capabilities.md) yeni özellikler ayarlama.
  
## <a name="how-irm-works-with-exchange-online-and-active-directory-rights-management-services"></a>IRM diğer çalışanlarla Exchange Online ve Active Directory Rights Management Services

Exchange Online IRM, Windows Server 2008 ve sonraki bir Active Directory Rights Management Services bilgi koruma teknolojisi olan şirket içi E-posta (AD RMS) kullanır. IRM koruması, e-posta iletisine bir AD RMS hak ilkesi şablonu uygulanarak e-postaya uygulanır. Haklar iletinin kendisine iliştirilir ve böylelikle koruma, hem çevrimiçi, hem çevrimdışı hem de kurum güvenlik duvarı içinde ve dışında gerçekleşir.
  
Kullanıcılar, alıcıların bir ileti üzerinde sahip olduğu izinleri denetim altına almak için e-posta iletisine şablon uygulayabilir. İletiden bilgi iletme, iletiden bilgi ayıklama, ileti kaydetme veya iletiyi yazdırma gibi eylemler, iletiye AD RMS hakları ilkesi uygulanarak denetlenebilirsiniz.
  
IRM'yi, Windows Server 2008 veya sonraki bir Windows AD RMS sunucusunu kullanmak üzere yapılandırabilirsiniz. Bulut tabanlı kuruluş için AD RMS hak ilkesi şablonlarını yönetmek için bu AD RMS sunucusunu kullanabilirsiniz. Outlook, kullanıcıların göndermekte olduğu iletilere IRM koruması uygulamalarına olanak sağlamak için AD RMS sunucusuna da güven verir. Ayrıntılar için bkz. [IRM'yi şirket içi AD RMS sunucusunu kullanmak üzere yapılandırma](configure-irm-to-use-an-on-premises-ad-rms-server.md). 
  
Etkinleştirildikten sonra, IRM koruması iletilere aşağıdaki gibi uygulanabilir:
  
- **Kullanıcılar şablonlar ve şablonlar kullanarak el ile Outlook ve Web üzerinde Outlook.** Kullanıcılar, İzinleri ayarla listesinden şablonu seçerek e-posta iletisine AD RMS hak **ilkesi şablonu uygulayabilirler** . Kullanıcılar IRM korumalı bir ileti gönderirken, desteklenen bir biçim kullanan ekli dosyalar da iletiyle aynı IRM korumasını alır. IRM koruması Word, Excel ve PowerPoint dosyalarının yanı sıra .xps dosyaları ve ekli e-posta iletileriyle ilişkilendirilmiş dosyalara uygulanır. 
    
- **Yöneticiler, IRM korumasını otomatik olarak hem aktarım hem de diğer kullanıcılara uygulamak Outlook aktarım Web üzerinde Outlook.** IRM ile koruma iletileri için aktarım koruma kuralları oluşturabilirsiniz. Aktarım koruma kuralı eylemsini yapılandırarak, kural koşuluna uygun iletilere AD RMS hak ilkesi şablonu uygulayabilirsiniz. IRM'yi etkinleştirdikten sonra, kuruluşun AD RMS hak ilkesi şablonları iletiye hak koruması uygulama adlı aktarım koruma kuralı **eylemiyle kullanılabilir**.
    
- **Yöneticiler özel koruma Outlook oluşturabilir.** Outlook koruma kuralları, gönderenin departmanını, iletinin kime gönderildiğini ve alıcıların kuruluş içinde mi yoksa dışında mı olduğunu içeren ileti koşullarına bağlı olarak, Outlook 2010'da iletilere otomatik olarak IRM koruması uygulamaz (Web üzerinde Outlook değil). Ayrıntılar için bkz[. Özel koruma Outlook oluşturma](/exchange/create-an-outlook-protection-rule-exchange-2013-help).
