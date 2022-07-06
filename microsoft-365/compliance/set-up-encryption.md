---
title: Office 365 Kurumsal'de şifrelemeyi ayarlama
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/2/2018
audience: Admin
ms.topic: landing-page
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: e86fc991-0161-4f01-9c1c-d25e87733d06
description: Office 365 ile bazı şifreleme özellikleri varsayılan olarak açıktır; diğer özellikler belirli uyumluluk veya yasal gereksinimleri karşılayacak şekilde yapılandırılabilir.
ms.openlocfilehash: 86e39603025c29d47a2e1b2b5b946bfe2549245d
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622117"
---
# <a name="set-up-encryption-in-office-365-enterprise"></a>Office 365 Kurumsal'de şifrelemeyi ayarlama

Şifreleme, içeriğinizin yetkisiz kullanıcılar tarafından okunmasını engelleyebilir. [Office 365'de şifreleme](encryption.md) çeşitli teknolojiler ve yöntemler kullanılarak yapılabileceğinden, şifrelemeyi açmak veya ayarlamak için tek bir yer yoktur. Bu makalede, bilgi koruma stratejinizin bir parçası olarak şifrelemeyi ayarlamanın veya yapılandırmanın çeşitli yolları hakkında bilgi sağlanır.

> [!TIP]
> Şifreleme hakkında daha fazla teknik ayrıntı arıyorsanız bkz. [Office 365 şifreleme hakkında teknik başvuru ayrıntıları](technical-reference-details-about-encryption.md).

Office 365 ile, varsayılan olarak çeşitli şifreleme özellikleri sağlanır. Belirli uyumluluk veya yasal gereksinimleri karşılamak için ek şifreleme özellikleri yapılandırılabilir. Aşağıdaki tabloda farklı senaryolar için çeşitli şifreleme yöntemleri açıklanmaktadır.

<br>

****

|Senaryo|Şifreleme Yöntemleri|
|---|---|
|Dosyalar Windows bilgisayarlara kaydedilir|Bilgisayar düzeyinde şifreleme, Windows cihazlarında BitLocker kullanılarak yapılabilir. Kuruluş yöneticisi veya BT Uzmanı olarak bunu Microsoft Dağıtım Araç Seti'ni (MDT) kullanarak ayarlayabilirsiniz. Bkz. [BitLocker için MDT'i ayarlama](/windows/deployment/deploy-windows-mdt/set-up-mdt-for-bitlocker).|
|Dosyalar mobil cihazlara kaydedilir|Bazı mobil cihazlar, bu cihazlara kaydedilen dosyaları varsayılan olarak şifreler. [Yerleşik Office 365 için Mobil Cihaz Yönetimi Özellikleri](https://support.microsoft.com/office/capabilities-of-built-in-mobile-device-management-for-microsoft-365-a1da44e5-7475-4992-be91-9ccec25905b0) ile mobil cihazların Office 365'daki verilere erişmesine izin verilip verilmeyeceğini belirleyen ilkeler ayarlayabilirsiniz. Örneğin, yalnızca içeriği şifreleyen cihazların Office 365 verilere erişmesine izin veren bir ilke ayarlayabilirsiniz. Bkz. [Cihaz güvenlik ilkeleri oluşturma ve dağıtma](https://support.microsoft.com/office/create-and-deploy-device-security-policies-d310f556-8bfb-497b-9bd7-fe3c36ea2fd6). <p> Mobil cihazların Office 365 ile etkileşim kurması üzerinde ek denetim için [Microsoft Intune](/mem/intune/fundamentals/setup-steps) eklemeyi düşünebilirsiniz.|
|Microsoft'un veri merkezlerinde verilerinizi şifrelemek için kullanılan şifreleme anahtarları üzerinde denetim sahibi olmanız gerekir|Office 365 yöneticisi olarak kuruluşunuzun şifreleme anahtarlarını denetleyebilir ve ardından Office 365 Microsoft'un veri merkezlerinde bekleyen verilerinizi şifrelemek için bunları kullanacak şekilde yapılandırabilirsiniz. <p> [Microsoft Purview Müşteri Anahtarı ile hizmet şifreleme](customer-key-overview.md)|
|Kişiler e-posta yoluyla iletişim kuruyor (Exchange Online)|Exchange Online yöneticisi olarak, e-posta şifrelemesini yapılandırmak için çeşitli seçenekleriniz vardır. Şunlar dahildir: <ul><li>Kişilerin kuruluşunuzun içinde veya dışında şifrelenmiş iletiler göndermesini sağlamak için Azure Rights Management (Azure RMS) ile [Office 365 ileti şifrelemesi (OME)](set-up-new-message-encryption-capabilities.md) kullanma</li><li>E-posta iletilerini şifrelemek ve dijital olarak imzalamak için [S/MIME](/exchange/security-and-compliance/smime-exo/smime-exo) kullanma</li><li>[Başka bir kuruluşla güvenli posta akışı için bağlayıcıları ayarlamak için](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-for-secure-mail-flow-with-a-partner) TLS kullanma</li></ul> <p> Bkz. [Office 365'de e-posta şifrelemesi](./email-encryption.md).|
|Dosyalara ekip sitelerinden veya belge kitaplıklarından (OneDrive İş veya SharePoint Online) erişilir|kişiler OneDrive İş veya SharePoint Online'a kaydedilmiş dosyalarla çalışırken TLS bağlantıları kullanılır. Bu, otomatik olarak Office 365 yerleşik olarak bulunur. Bkz. [OneDrive İş ve SharePoint Online'da Veri Şifreleme](./data-encryption-in-odb-and-spo.md).|
|Dosyalar çevrimiçi toplantılarda ve anlık ileti konuşmalarında paylaşılır (çevrimiçi Skype Kurumsal)|kişiler Skype Kurumsal Online kullanarak dosyalarla çalışırken, bağlantı için TLS kullanılır. Bu, otomatik olarak Office 365 yerleşik olarak bulunur. Bkz[. Güvenlik ve Arşivleme (çevrimiçi Skype Kurumsal)](/office365/servicedescriptions/skype-for-business-online-service-description/skype-for-business-online-features).|
|Dosyalar çevrimiçi toplantılarda ve anlık ileti konuşmalarında paylaşılır (Microsoft Teams)|Kişiler Microsoft Teams'i kullanarak dosyalarla çalışırken, bağlantı için TLS kullanılır. Bu, otomatik olarak Office 365 yerleşik olarak bulunur. Microsoft Teams şu anda şifrelenmiş e-postaların satır içi işlenmesini desteklememektedir. Şifrelenmiş e-postaların Microsoft Teams'e şifrelenmiş olarak gelmesini önlemek için bkz. [İleti Şifrelemesi SSS](./ome-faq.yml#can-i-automatically-remove-encryption-on-incoming-and-outgoing-mail-).|
|

## <a name="additional-information"></a>Ek bilgiler

Şifreleme seçeneklerini içeren dosya koruma çözümleri hakkında daha fazla bilgi edinmek için bkz. [Office 365'de Dosya Koruma Çözümleri](https://www.microsoft.com/download/details.aspx?id=55523).
