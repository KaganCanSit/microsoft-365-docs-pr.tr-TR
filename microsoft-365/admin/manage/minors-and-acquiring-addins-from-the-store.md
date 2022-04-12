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
description: Reşit olmayanların kişisel verilerini yöneten Genel Veri Koruma Yönetmeliği (GDPR) düzenlemeleri hakkında bilgi edinin.
ms.openlocfilehash: 15b35798ba03132b35285dc16ce57b139e4d7222
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782379"
---
# <a name="minors-and-acquiring-add-ins-from-the-store"></a>Reşit olmayanlar ve Store'dan eklenti edinme

Genel Veri Koruma Yönetmeliği (GDPR) 25 Mayıs 2018 tarihinde yürürlüğe girecek olan bir Avrupa Birliği yönetmeliğidir. Kullanıcılara verilerini koruma hakkı verir. GDPR'nin bir başka boyutu da, reşit olmayanların kişisel bilgilerinin, ebeveynleri veya vasilerinin onayı olmadan üçüncü şahıslara gönderilemeyeceğidir. Reşit olma yaşı, kişilerin yaşadığı bölgeye bağlı olarak belirlenir.

Ebeveyn onayı hakkında kanuni yönetmeliklere sahip olan bölgeler arasında Amerika Birleşik Devletleri, Güney Kore, Birleşik Krallık ve Avrupa Birliği yer alır. Bu bölgelerde, reşit olmayanların Store'dan yeni Office eklentileri edinmeleri ve daha önce edinilen eklentileri çalıştırmaları engellenecektir (Azure Active Directory üzerinden). Yasal düzenlemelere tabii olmayan bölgeler için indirme kısıtlaması olmayacaktır.

Bir kullanıcının reşit olup olmadığı Azure Active Directory'de belirtilen verilere göre belirlenir. Kuruluş yöneticisi, yasal yaş grubunu ve bu kullanıcı için ebeveyn iznini bildirmekle sorumludur.

Ebeveyn/veli belirli bir eklentiyi kullanarak reşit olmayan bir kişiyi onaylarsa, kuruluş yöneticisi bu eklentiyi onayı olan tüm reşit olmayanlara dağıtmak için merkezi dağıtımı kullanabilir.

Reşit olmayanlarla GDPR uyumlu olmak için öncelikle belirtilen Office uygulamalarından birinin okul veya kuruluşunuzda dağıtıldığından emin olun.

 **Word, Excel, PowerPoint ve Project için**

|Ortam|Derleme numarası|
|---|---|
|Kurumlar için Microsoft 365 Uygulamaları (Geçerli Kanal)|9001.2138|
|Kurumlar için Microsoft 365 Uygulamaları (Altı Aylık Enterprise Kanalı)|8431.2159|
|Windows için Office 2016|16.0.4672.1000|
|Windows için Office 2013|15.0.5023.1000|
|Office Mac 2016|16.11.18020200|
|Web için Office|Yok|

 **Outlook için**:

|Ortam|Derleme numarası|
|---|---|
|Windows için Outlook 2016 (MSI)|Derleme numarası TBD|
|Windows için Outlook 2016 (C2R)|16.0.9323.1000|
|Office Mac 2016|16.0.9318.1000|
|iOS için Outlook Mobile|2.75.0|
|Android için Office Mobile|2.2.145|
|Outlook.com|Yok|

 **Office 2013 gereksinimleri**

Windows için Word, Excel ve PowerPoint 2013, Active Directory Kimlik Doğrulama Kitaplığı'nın (ADAL) etkinleştirilip etkinleştirilmediğinin aynı ikincil denetimlerini destekler. Uyumluluk için sıradaki açıklamadaki gibi iki seçenek vardır.

- **ADAL'yi etkinleştirin**. Bu makalede, Office 2013 için ADAL'ın nasıl etkinleştirileceği açıklanmaktadır: [Office istemcilerle modern Microsoft 365 kimlik doğrulaması kullanma](../../enterprise/modern-auth-for-office-2013-and-2016.md).<br/>[Windows cihazlarda Office 2013 için Modern Kimlik Doğrulamayı Etkinleştirme](../security-and-compliance/enable-modern-authentication.md) kısmında belirtildiği gibi ADAL'ı etkinleştirmek için kayıt defteri anahtarlarını da ayarlamanız gerekir.<br/>Ek olarak, Office 2013 için şu Nisan güncelleştirmelerini kurmanız gereklidir:

  - [Outlook 2013 güvenlik güncelleştirmesinin açıklaması: 10 Nisan 2018](https://support.microsoft.com/help/4018330/description-of-the-security-update-for-office-2013-april-10-2018)

  - [3 Nisan 2018 Office 2013 (KB4018333) güncelleştirmesi](https://support.microsoft.com/help/4018333/april-3-2018-update-for-office-2013-kb4018333)

- **ADAL'yi etkinleştirmeyin**. Office 2013'te ADAL'ı etkinleştiremiyorsanız, Office istemciler için Mağaza'yı kapatmak için grup ilkesi kullanmanız gerekir. Office ayarları uygulamasını kapatma konusunda bilgi [burada](/previous-versions/office/office-2013-resource-kit/cc178992(v=office.15)) bulunur.

## <a name="related-articles"></a>İlgili makaleler

[Yönetim merkezinde eklentileri dağıtma](./manage-deployment-of-add-ins.md)

[Yönetim merkezinde eklentileri yönetme](./manage-addins-in-the-admin-center.md)
