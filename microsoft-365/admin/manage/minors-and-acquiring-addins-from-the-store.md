---
title: Reşit olmayanlar ve Store'dan eklenti edinme
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 737e8c86-be63-44d7-bf02-492fa7cd9c3f
description: Reşit olmayanların kişisel verilerini yöneten Genel Veri Koruma Yönetmeliği (GDPR) düzenlemelerini öğrenin.
ms.openlocfilehash: 84a1ecc9eb5d29ae1c2e4597b8299430cc3de038
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985573"
---
# <a name="minors-and-acquiring-add-ins-from-the-store"></a>Reşit olmayanlar ve Store'dan eklenti edinme

Genel Veri Koruma Yönetmeliği (GDPR) 25 Mayıs 2018 tarihinde yürürlüğe girecek olan bir Avrupa Birliği yönetmeliğidir. Kullanıcılara verilerini koruma hakkı verir. GDPR'nin bir başka boyutu da, reşit olmayanların kişisel bilgilerinin, ebeveynleri veya vasilerinin onayı olmadan üçüncü şahıslara gönderilemeyeceğidir. Reşit olma yaşı, kişilerin yaşadığı bölgeye bağlı olarak belirlenir.
  
Ebeveyn onayı hakkında kanuni yönetmeliklere sahip olan bölgeler arasında Amerika Birleşik Devletleri, Güney Kore, Birleşik Krallık ve Avrupa Birliği yer alır. Bu bölgelerde, reşit olmayanların Store'dan yeni Office eklentileri edinmeleri ve daha önce edinilen eklentileri çalıştırmaları engellenecektir (Azure Active Directory üzerinden). Yasal düzenlemelere tabii olmayan bölgeler için indirme kısıtlaması olmayacaktır.
  
Bir kullanıcının reşit olup olmadığı Azure Active Directory'de belirtilen verilere göre belirlenir. Bu kullanıcı için yasal yaş grubu ve ebeveyn rızası bildirim almak kuruluş yöneticisinin sorumluluğundadır.
  
Ebeveyn/veli belirli bir eklentiyi kullanmak için reşit olmayan bir kullanıcıya izin verdi ise kuruluş yöneticisi bu eklentiyi rıza alan tüm reşit olmayan kullanıcılara dağıtmak için merkezi dağıtım kullanabilir.
  
Reşit olmayanlarla GDPR uyumlu olmak için öncelikle belirtilen Office uygulamalarından birinin okul veya kuruluşunuzda dağıtıldığından emin olun.
 
 **Word, Excel, PowerPoint ve Project için** 

|**Ortam** <br/> |**Derleme numarası** <br/> |
|:-----|:-----|
|Kurumlar için Microsoft 365 Uygulamaları (Güncel Kanal)  <br/> |9001.2138   <br/> |
|Kurumlar için Microsoft 365 Uygulamaları (Yarı Yıllık Enterprise Kanalı)  <br/> |8431.2159  <br/> |
|Windows için Office 2016  <br/> |16.0.4672.1000  <br/> |
|Windows için Office 2013  <br/> |15.0.5023.1000  <br/> |
|Office Mac 2016  <br/> |16.11.18020200  <br/> |
|Web için Office  <br/> |Yok  <br/> |
   
 **Outlook için**: 
  
|**Ortam** <br/> |**Derleme numarası** <br/> |
|:-----|:-----|
|Windows için Outlook 2016 (MSI)  <br/> |Derleme numarası TBD  <br/> |
|Windows için Outlook 2016 (C2R)  <br/> |16.0.9323.1000  <br/> |
|Office Mac 2016  <br/> |16.0.9318.1000  <br/> |
|iOS için Outlook Mobile  <br/> |2.75.0  <br/> |
|Android için Office Mobile  <br/> |2.2.145  <br/> |
|Outlook.com  <br/> |Yok  <br/> |

 **Office 2013 gereksinimleri**
  
Active Directory Excel (ADAL) etkin olup Windows için Word, PowerPoint ve PowerPoint 2013 aynı reşit olmayanları destekleyecektir. Uyumluluk için sıradaki açıklamadaki gibi iki seçenek vardır.
  
- **ADAL'ı etkinleştirin**. Bu makalede Office 2013 için ADAL'Office etkinleştirme açıklanmıştır: Microsoft 365 istemcileriyle [modern kimlik Office kullanma](../../enterprise/modern-auth-for-office-2013-and-2016.md).<br/>[Windows cihazlarda Office 2013 için Modern Kimlik Doğrulamayı Etkinleştirme](../security-and-compliance/enable-modern-authentication.md) kısmında belirtildiği gibi ADAL'ı etkinleştirmek için kayıt defteri anahtarlarını da ayarlamanız gerekir.<br/>Ek olarak, Office 2013 için şu Nisan güncelleştirmelerini kurmanız gereklidir:
    
  - [Outlook 2013 güvenlik güncelleştirmesinin açıklaması: 10 Nisan 2018](https://support.microsoft.com/help/4018330/description-of-the-security-update-for-office-2013-april-10-2018)
    
  - [3 Nisan 2018 Office 2013 (KB4018333) güncelleştirmesi](https://support.microsoft.com/help/4018333/april-3-2018-update-for-office-2013-kb4018333)
    
- **ADAL'ı etkinleştirme.** Office 2013'te ADAL'ı etkinleştiremiyorsanız, o zaman önerimiz Grup İlkesi kullanarak Store'un müşteri adayları için Office. Office ayarları uygulamasını kapatma konusunda bilgi [burada](/previous-versions/office/office-2013-resource-kit/cc178992(v=office.15)) bulunur.

## <a name="related-articles"></a>İlgili makaleler

[Yönetim merkezinde eklentileri dağıtma](./manage-deployment-of-add-ins.md)

[Yönetim merkezinde eklentileri yönetme](./manage-addins-in-the-admin-center.md)
