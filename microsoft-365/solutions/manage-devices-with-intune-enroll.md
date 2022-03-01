---
title: Adım 2. Intune ile cihazları yönetime kaydetme
ms.author: bcarter
author: brendacarter
f1.keywords:
- enroll devices into management
- enroll devices with Intune
- Intune mobile device platforms
manager: dougeby
audience: ITPro
description: Cihazları yönetime kaydetmek ve üzerinde çalışan uygulamaların uyumlu olduğundan emin olmak ve şirket veri sızıntılarını önlemek için Intune ve AutoPilot'u kullanın.
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-managedevices
- m365solution-scenario
ms.custom: ''
keywords: ''
ms.openlocfilehash: 5810513cd3aa4fccd8ce0100f22c708c53527c42
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2022
ms.locfileid: "63010194"
---
# <a name="step-2-enroll-devices-into-management-with-intune"></a>Adım 2. Intune ile cihazları yönetime kaydetme

Uç noktanın güvenliğini sağlamanın çeşitli yolları vardır; bu terim çoğunlukla cihazlar, uygulamalar ve kullanıcı kimliği gibi birleştirilmiş varlığa başvuru yapmak için kullanılır. Güvenlik ilkeleri tutarlı ve güvenilir bir şekilde yalnızca uygulamalarda değil, cihazın kendi cihazında da zorunlu kılınmalıdır. Cihazı yönetime kaydetmek ve bulut kimlik sağlayıcısına (örneğin, Azure Active Directory) kaydetmek harika bir başlangıçtır.

Bir cihaz İster kişisel olarak sahip olun ister kurumsal olsun, tamamen yönetilen bir cihaz olsun, yalnızca sağlıklı ve uyumlu cihazlara izin vermenizi sağlamak için, kuruluş kaynaklarına erişen uç noktaların görünür olması iyi bir fikirdir. Buna, uç noktalarda çalıştıran mobil ve masaüstü uygulamalarının durumu ve güvenilirliği dahildir. Bu uygulamaların sağlıklı ve uyumlu olduğundan ve şirket verilerinizin kötü amaçlı veya yanlışlıkla başka bir amaçla tüketici uygulamalarına veya hizmetlere sızdır olmasını önlemek istiyor olun.

Cihaz kayıt işlemi, kullanıcı, cihaz ve cihaz arasında bir ilişki Microsoft Intune sağlar. Microsoft Intune'i tek başına bir hizmet olarak kullanmak, tek bir web tabanlı yönetim konsolu kullanarak bilgisayarlarınızı, macOS'u Windows en popüler mobil cihaz platformlarını yönetmenize olanak sağlar.

Bu makalede, Intune kullanarak cihazları yönetime kaydetme yöntemleri önerilir. Bu yöntemler ve her birinin nasıl dağıtıla ilgili daha fazla bilgi için bkz. [Dağıtım kılavuzu: Cihazları](/mem/intune/fundamentals/deployment-guide-enrollment) başka bir Microsoft Intune.

![Cihazları yönetme adımları](../media/devices/intune-mdm-steps-1.png#lightbox)

## <a name="windows-enrollment"></a>Windows kaydı
11 cihaza ve Windows 10 için Windows birkaç seçenek vardır. En yaygın yöntemlerden ikisi şunlardır:

- Azure Active Directory (Azure AD) Katılma - Azure Active Directory ile cihaza katılır ve kullanıcıların Azure AD kimlik bilgileriyle Windows'te oturum açmalarına olanak sağlar. Otomatik Kayıt etkinleştirilirse, cihaz otomatik olarak Intune'a kaydedilir. Otomatik kayıt, kullanıcı için tek adımlı bir işlemdir. Aksi takdirde, yalnızca MDM kaydı aracılığıyla ayrı olarak kaydolmaları ve kimlik bilgilerini yeniden girmeniz gerekir. Kullanıcılar bu şekilde, ilk oturum Windows veya OOBE'den Ayarlar. Cihaz, Intune'da kurumsal bir cihaz olarak işaretlenir.
- Autopilot - Azure AD Katılma özelliğini otomatik hale alır ve kurumsal olarak sahip olunan yeni cihazları Intune'a kaydettirr. Bu yöntem, ilk çalıştırma deneyimini basitleştirerek cihazlara özel işletim sistemi görüntüleri uygulama ihtiyacını ortadan kaldırır. Yöneticiler Intune'u kullanarak AutoPilot cihazlarını yönetmek için ilkeler, profiller, uygulamalar ve daha fazlasını kaydettikten sonra yönetebilirler. Dört tür AutoPilot dağıtımı vardır: Self-Deploying Modu (bilgi bilgileri, dijital imza veya paylaşılan bir cihaz için), Kullanıcı Tarafından Kullanım Modu (geleneksel kullanıcılar için), Windows Önceden sağlanan dağıtım için AutoPilot, iş ortaklarının veya IT personelinin Windows 10 veya Windows  11 ile tam olarak yapılandırılmış ve iş kullanıma hazır hale geldi. Mevcut cihazlar için AutoPilot, Windows en son sürümünü mevcut cihazlarınıza kolayca dağıtmanıza olanak tanır.

TEKMİ veya başka cihazlara Windows ek seçenekler için bkz. Windows [cihaz kaydetme Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-windows).

## <a name="ios-and-ipados-enrollment"></a>iOS ve iPadOS kaydı

Kullanıcıya ait (BYOD) cihazlar için, aşağıdaki yöntemlerden birini kullanarak kullanıcıların kişisel cihazlarını Intune yönetimi için kaydetmelerine izin veebilirsiniz.
- Cihaz kaydı, genel BYOD kaydı olarak düşünebilirsiniz. Yöneticilere çok çeşitli yönetim seçenekleri sunar.
- Kullanıcı kaydı, yöneticilere bir cihaz yönetim seçenekleri alt kümesi sağlayan daha kolaylaştırılmış bir kayıt işlemidir. Bu özellik şu anda önizlemede.

Intune, kullanıcıları için cihaz satın alan kuruluşlarda aşağıdaki iOS/iPadOS şirkete ait cihaz kayıt yöntemlerini destekler:
- Apple Otomatik Cihaz Kaydı (ADE)
- Apple Okul Yöneticisi
- Apple Configurator Kurulum Yardımcısı kaydı
- Apple Configurator doğrudan kaydı

Daha fazla bilgi için bkz[. iOS ve iPadOS cihazlarını başka bir Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-ios-ipados).

## <a name="android-enrollment"></a>Android kaydı 

Cihazın türüne, desteklemek istediğiniz kayıt türüne ve ayrıca kullandığınız Android sürümü, hatta üretici (özellikle Samsung) gibi şeylere bağlı olarak Android Kaydı için çeşitli seçenekler vardır. Çoğu kuruluş, ANDROID İş profillerini son kullanıcıları için (özellikle BYOD senaryolarında) kullanır. 

Android iş profiliyle, son kullanıcının bilgileri iş ve kişisel kullanım için ayrı uygulamaların yanı sıra veri kapsayıcıları ile ayrı ayrı ayrılmıştır. Bu, kullanıcıların kendi verilerini ve kurumsal verilerin güvenliğini koruyarak kendi cihazlarını kaydetmeleri için ideal bir yol sağlar. 

Ancak, organizasyonunız Android cihazları sağlıyorsa, tam olarak yönetilen (Kullanıcı Benıştır) veya özel (Kullanıcı Yakınlığı yok) adı verilen cihazı kullanmayı tercih edebilirsiniz.

Android kaydı hakkında daha fazla bilgi edinmek için bkz[. Android cihazlarını Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-android).

## <a name="macos-enrollment"></a>macOS kaydı

macOS'a kayıt, pek çok IT kuruluşu için karmaşık bir konu olabilir. Kullanıcılarının çoğunluğu Mac kullanıcısı olmadığı sürece bu tür cihazları büyük ölçüde yönetemebilirsiniz. Az sayıda macOS kullanıcınız varsa, Yalnızca Intune Kaydı'nın kullanılması önerilir. Çok fazla sayıda macOS kullanıcınız varsa Intune + Jamf kaydı öneririz.  
- Yalnızca Intune kaydı — Bu, macOS cihazlarının temel yönetimine göredir. Bu işlem, diğer kullanıcı tabanlı kayıt seçeneklerinin çoğuna benzer şekilde elle bir işlem gerektirir. Ancak, az sayıda Mac cihazı varsa, bu sadece birkaç kullanıcı için otomatik bir altyapının tamamını ayarlamadan daha kolay olabilir. Intune yalnızca kaydıyla sertifikalar, parola yapılandırmaları ve uygulamalar gibi şeyleri dağıtabilirsiniz. Ayrıca uyumluluk ilkelerini ve koşullu Erişimi yapılandırabilmenin yanı sıra şifreleme ve cihaz temizlemeyi zorunlu kılınabilme olanağını da yapılandırabilirsiniz. 
- Intune ve Jamf kaydı : Mac yönetimi için en kapsamlı desteği arayanlar için, Koşullu Erişim için Jamf + Intune ile Koşullu Erişim'i etkinleştirmek için Jamf'in kapsamlı Mac yönetim özelliklerini Intune uyumluluğu ile birleştiren mükemmel bir çözümüz var. Bu senaryoda, güvenliğin artması için Jamf'den bu sinyalleri alırken, cihazı Jamf ile tam olarak yönetiyorsanız.

macOS kaydı hakkında daha fazla bilgi edinmek için bkz[. MacOS cihazlarını farklı Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-macos).

## <a name="next-steps"></a>Sonraki adımlar

[3. Adım'a gidin. Intune'la cihazlar için uyumluluk ilkeleri ayarlayın](manage-devices-with-intune-compliance-policies.md).

