---
title: Exchange Multi-Geo
ms.reviewer: adwood
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
ms.localizationpriority: medium
description: Özellik sınırlamaları ve posta kutusu yerleşimi Exchange Online, birden çok coğrafi özellik hakkında bilgi alın.
ms.openlocfilehash: c45c5c8e8856206fc2afc3e08005821f24dcd028
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010803"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Multi-Geo Capabilities in Exchange Online

Çok coğrafi bir ortamda, posta kutusu içeriğinin (Exchange Online verilerin) konumunu kullanıcı başına seçebilirsiniz.

Posta kutularını uydu coğrafi konumlara şu şekilde yerebilirsiniz:

- Uydu coğrafi Exchange Online yeni bir posta kutusu oluşturma.

- Kullanıcının tercih Exchange Online değiştirerek var olan bir posta kutusunu uydu coğrafi bir konuma taşıma.

- Şirket içi bir kuruluştan bir posta kutusunu Exchange uydu coğrafi bir konuma ekleme.

## <a name="mailbox-placement-and-moves"></a>Posta kutusu yerleşimi ve hareketleri

Microsoft önkoşul olan multi-geo yapılandırma adımlarını tamamlandıktan Exchange Online, Azure AD'daki kullanıcı nesnelerinde **PreferredDataLocation** özniteliğine uyar.

Exchange Online Azure **AD'den PreferredDataLocation** özelliğini dizin hizmetinin **MailboxRegion** özelliğiyle Exchange Online eşitler. **MailboxRegion değeri, kullanıcı** posta kutularının ve ilişkili arşiv posta kutularının nereye yerleştiril olacağını coğrafi olarak belirler. Kullanıcının birincil posta kutusu ve arşiv posta kutularını farklı coğrafi konumlarda olacak şekilde yapılandırmanız mümkün değildir. Kullanıcı nesnesi başına tek bir coğrafi konum yalıtabilirsiniz.

- **Var olan posta kutusu olan bir kullanıcıda PreferredDataLocation** yapılandırıldığında, posta kutusu yeniden yükleme sırasına konacak ve otomatik olarak belirtilen coğrafi konuma taşınır.

- Var olan posta kutusu olmayan bir kullanıcıda **PreferredDataLocation** yapılandırıldığında, posta kutusunu sağlanana kadar, belirtilen coğrafi konuma sağlandı.

- Bir **kullanıcıda PreferredDataLocation** belirtilmemişse, posta kutusunu sağlarken, bu posta kutusu merkezi coğrafi konumda sağlanmaz.

- **PreferredDataLocation** kodu yanlışsa (örneğin, NAM yerine NAN'ın yazım hatası), posta kutusu merkezi coğrafi konumda sağlanmış olur.

**Not**: Birden çok coğrafi özellik ve Skype Kurumsal Çevrimiçi olarak barındırılan toplantılarda, hizmetleri bulmak için kullanıcı nesnelerinde **PreferredDataLocation** özelliği kullanılır. Bölgesel olarak barındırılan toplantılar için kullanıcı nesnelerinde **PreferredDataLocation** değerlerini yapılandırıyorsanız, kiracıda multi-geo etkinleştirildikten sonra söz Microsoft 365 kullanıcıların posta kutusu belirtilen coğrafi konuma taşınır.

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Birden çok coğrafi alan için özellik Exchange Online

- EXCHANGE yönetim merkezinde (EAC) bulunan güvenlik ve uyumluluk özellikleri (örneğin, denetim ve eKbul) çok coğrafi kuruluşlarda kullanılamaz. Bunun yerine, güvenlik ve uyumluluk [Microsoft 365 için & Uyumluluk Merkezi'ne](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) ihtiyacınız vardır.

- Mac için Outlook posta kutularını yeni bir coğrafi konuma taşımanız sırasında kullanıcılar Çevrimiçi Arşiv klasörlerine geçici bir erişim kaybıyla açabilirler. Bu koşul, kullanıcının birincil ve arşiv posta kutuları farklı coğrafi konumlarda olduğunda ortaya çıkar, çünkü coğrafi posta kutusu hareketleri farklı zamanlarda tamamlanır.

- Kullanıcılar posta *kutusu klasörlerini* Web üzerinde Outlook'daki (eski adı Outlook Web App OWA) coğrafi konumlarda paylaş değildir. Örneğin, Avrupa Birliği'nde bir kullanıcı Web üzerinde Outlook'da bulunan bir posta kutusunda paylaşılan bir klasörü açmak için Avrupa Birliği'nde oturum açılamaz. Bununla Outlook, [Web'de](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362) kullanıcılar Başka bir kişinin posta  kutusunu farklı bir tarayıcı penceresinde açma konusunda açıklandığı gibi ayrı bir tarayıcı penceresi kullanarak farklı coğrafi konumlarda diğer posta kutularını Outlook Web App.

  **Not**: Çapraz coğrafi posta kutusu klasör paylaşımı, e-Outlook üzerinde Windows.

- Ortak klasörler, çok coğrafi kuruluşlarda destekler. Bununla birlikte, ortak klasörlerin merkezi coğrafi konumda kalması gerekir. Ortak klasörleri uydu coğrafi konumlara taşıyasınız.

- Çok coğrafi bir ortamda, coğrafi olarak posta kutusu denetimi desteklanmaz. Örneğin, kullanıcıya farklı bir coğrafi konumdaki paylaşılan posta kutusuna erişim izinleri atanmışsa, o kullanıcı tarafından gerçekleştirilen posta kutusu eylemleri paylaşılan posta kutusunun posta kutusu denetim günlüğüne kaydedilmez. Exchange denetim olayları yalnızca varsayılan konum için de kullanılabilir. Daha fazla bilgi için bkz. [Posta kutusu denetimini yönetme](../compliance/enable-mailbox-auditing.md).
