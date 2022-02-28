---
title: Verilerde şifrelemeyi Office 365 Kurumsal
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/2/2018
audience: Admin
ms.topic: hub-page
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: e86fc991-0161-4f01-9c1c-d25e87733d06
description: Daha Office 365, bazı şifreleme özellikleri varsayılan olarak açıktır; bazı uyumluluk veya yasal gereksinimleri karşılamak üzere diğer özellikler ya da kullanılabilir.
ms.openlocfilehash: 00035af0049abedff8a794710649f162576dc46c
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983227"
---
# <a name="set-up-encryption-in-office-365-enterprise"></a>Verilerde şifrelemeyi Office 365 Kurumsal

Şifreleme, içeriğinizi yetkisiz kullanıcıların okumasını koruyabilir. Şifreleme [Office 365](encryption.md) çeşitli teknolojiler ve yöntemler kullanılarak yapalır, çünkü şifrelemeyi tek bir yerde açmaz veya ayarlamaz. Bu makalede, bilgi koruma stratejiniz kapsamında şifrelemeyi ayarlamanın veya yapılandırmanın çeşitli yolları hakkında bilgi sağlar.

> [!TIP]
> Şifreleme hakkında daha teknik ayrıntılar arıyorsanız, bkz. Şifreleme [hakkında teknik başvuru Office 365](technical-reference-details-about-encryption.md).

Şifreleme Office 365, varsayılan olarak çeşitli şifreleme özellikleri kullanılabilir. Ek şifreleme özellikleri, belirli uyumluluk veya yasal gereksinimleri karşılamak üzere ya da geliştirebilirsiniz. Aşağıdaki tabloda, farklı senaryolar için çeşitli şifreleme yöntemleri açık almaktadır.

<br>

****

|Senaryo|Şifreleme Yöntemleri|
|---|---|
|Dosyalar başka bilgisayarlarda Windows kaydedilir|Bilgisayar düzeyinde şifreleme, farklı cihazlarda BitLocker Windows yapılabilir. Kuruluş yöneticisi veya PRO olarak, Microsoft Dağıtım Araç Seti'nı (MDT) kullanarak bunu kurabilirsiniz. Bkz [. BitLocker için MDT ayarlama](/windows/deployment/deploy-windows-mdt/set-up-mdt-for-bitlocker).|
|Dosyalar mobil cihazlara kaydedilir|Bazı mobil cihazlar, bu cihazlara varsayılan olarak kaydedilen dosyaları şifreler. Yerleşik [Mobil Cihaz Özellikleri Office 365 için Mobil Cihaz Yönetimi](https://support.microsoft.com/office/capabilities-of-built-in-mobile-device-management-for-microsoft-365-a1da44e5-7475-4992-be91-9ccec25905b0), mobil cihazların mobil cihazlardaki verilere erişim izni verisine izin verip vermeyeceklerini belirleyen Office 365. Örneğin, yalnızca içeriği şifrelenen cihazların belirli bir veriye erişmesini sağlayan bir ilke Office 365 kurabilirsiniz. Bkz [. Cihaz güvenliği ilkelerini oluşturma ve dağıtma](https://support.microsoft.com/office/create-and-deploy-device-security-policies-d310f556-8bfb-497b-9bd7-fe3c36ea2fd6). <p> Mobil cihazların mobil cihazlarla etkileşim kurması üzerinde ek Office 365 daha fazla denetim [Microsoft Intune.](/mem/intune/fundamentals/setup-steps)|
|Microsoft'un veri merkezlerinde verilerinizi şifrelemek için kullanılan şifreleme anahtarları üzerinde denetime ihtiyacınız vardır|Genel Office 365 yöneticisi olarak, microsoft veri merkezlerinde beklemede verilerinizi şifrelemek üzere Office 365 şifrelemek üzere Office 365'i yapılandırabilirsiniz. <p> [Müşteri Hizmetleri'ne Müşteri Anahtarı ile Office 365](customer-key-overview.md)|
|Kişiler e-posta yoluyla iletişim kurar (Exchange Online)|Genel Exchange Online olarak, e-posta şifrelemeyi yapılandırmak için çeşitli seçenekleriniz vardır. Şunlar dahildir: <ul><li>Kişilerin Office 365 kuruluş içinde veya dışında şifrelenmiş iletiler göndermesini sağlamak için Azure Rights Management (Azure RMS) ile ileti şifreleme [(OME)](set-up-new-message-encryption-capabilities.md) kullanma</li><li>[E-posta iletilerini şifrelemek ve](/exchange/security-and-compliance/smime-exo/smime-exo) dijital olarak imzalamak için S/MIME kullanma</li><li>Başka bir kuruluşla [güvenli posta akışı için bağlayıcıları ayarlamak için](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner) TLS kullanma</li></ul> <p> Bkz[. E-posta şifreleme Office 365](./email-encryption.md).|
|Dosyalara ekip sitelerinden veya belge kitaplıklarından erişilebilir (OneDrive İş veya SharePoint Online)|Kişiler OneDrive İş Online'a OneDrive İş dosyalar ile SharePoint, TLS bağlantıları kullanılır. Bu, otomatik olarak bu Office 365 oluşturulur. Bkz[. OneDrive İş ve SharePoint Online'da Veri Şifreleme](./data-encryption-in-odb-and-spo.md).|
|Dosyalar çevrimiçi toplantılarda ve IM görüşmelerde paylaşılır (Skype Kurumsal Online)|Kişiler Skype Kurumsal Online kullanarak dosyalarla çalışırken, bağlantı için TLS kullanılır. Bu, otomatik olarak bu Office 365 oluşturulur. Bkz[. Güvenlik ve Arşivleme (Skype Kurumsal Çevrimiçi)](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).|
|Dosyalar çevrimiçi toplantılarda ve IM görüşmelerde paylaşılır (Microsoft Teams)|Kişiler dosyalarla çalışırken bağlantı Microsoft Teams, TLS kullanılır. Bu, otomatik olarak bu Office 365 oluşturulur. Microsoft Teams, şu anda şifreli e-postanın satır içi olarak işlenmesini desteklemez. Şifreli e-postanın bu adrese şifrelenmiş olarak Microsoft Teams için bkz. İleti Şifreleme [hakkında SSS](./ome-faq.yml#can-i-automatically-remove-encryption-on-incoming-and-outgoing-mail-).|
|

## <a name="additional-information"></a>Ek bilgiler

Şifreleme seçeneklerini içeren dosya koruma çözümleri hakkında daha fazla bilgi edinmek için bkz. Dosya [Koruma Office 365](https://www.microsoft.com/download/details.aspx?id=55523).
