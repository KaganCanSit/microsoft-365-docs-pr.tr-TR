---
title: Contoso için mobil cihaz yönetimi
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: Contoso'un cihazlarını ve üzerinde çalışan uygulamaları yönetmek için Microsoft 365'de Microsoft Intune nasıl kullandığını anlayın.
ms.openlocfilehash: c321fc9bdaf27577e32d934aa771c92d1a0bdd79
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092701"
---
# <a name="mobile-device-management-for-contoso"></a>Contoso için mobil cihaz yönetimi

Kuruluş için Microsoft 365 Intune ve mobil cihaz ile uygulama yönetimi ve güvenliğini destekleyen bir dizi Azure hizmeti içerir.

Contoso'nun mobil etkinleştirilmiş birçok çalışanı vardır. Bazılarında Contoso konumlarında ofisler, bazılarının ise ofisi yoktur. Contoso çalışan üretkenliğini sağlamak için bir yönteme ihtiyaç duyar, ancak cihazları, bu cihazlarda depolanan Contoso verilerini ve uygulama davranışını güvenli tutar.

## <a name="plan"></a>Plan

Contoso, kuruluş için Microsoft 365 için mobil cihaz yönetiminin aşağıdaki Intune kullanım örneklerini tanımladı:

- Mobil cihazlar tarafından güvenli bir şekilde erişilebilmesi için Exchange Online e-postayı ve verileri koruyun.
- Contoso çalışanları için kendi cihazını getir (KCG) programı uygulayın.
- Contoso çalışanlarına kuruluşa ait telefonlar ve sınırlı kullanımlı paylaşılan tabletler oluşturun.

Contoso aşağıdakiler için Intune kullanmaz:

- Çalışanların yönetilmeyen bir genel bilgi noktası Microsoft 365 güvenli bir şekilde erişmesine izin verin.
- Şirket içi Microsoft Exchange sunucusu olmadığından, şirket içi e-postayı ve verileri mobil cihazlar tarafından güvenli bir şekilde erişilebilmeleri için koruyun.

## <a name="deploy"></a>Dağıtım

Contoso mobil cihaz yönetimi altyapısını böyle ayarlar:

- Intune Mobil Cihaz Yönetimi (MDM) yetkilisi olarak ayarlayın ve içeriği yönetmek ve cihazları yönetmek için Azure'da Intune kullanın
- Kayıt ve Intune ayarları ile cihaz tabanlı Koşullu Erişim ilkeleri için cihazlar için Azure Active Directory (Azure AD) grupları oluşturuldu

  Daha fazla bilgi için bkz. [Contoso Koşullu Erişim ilkeleri](contoso-identity.md#conditional-access-policies-for-zero-trust-identity-and-device-access).

- iPad' ler, iMac'ler, iPhone'lar ve şirkete ait iPhone'lar ile çalışanları desteklemek için Apple cihaz platformunu etkinleştirdi
- Contoso için Şirket Portalı mobil cihazlara yüklenmesi sırasında görülen Contoso'ya özgü hüküm ve koşullar ilkeleri oluşturuldu
- Kaydedilmemiş cihazlar için, Microsoft 365 hizmetlerine erişim için kimlik doğrulaması gerektiren bir dizi Mobil Uygulama Yönetimi (MAM) ilkesi uyguladınız
- Şunları zorunlu kılan Intune ilkeleri oluşturuldu:
  - İzin verilen uygulamalar.
  - Yetkisiz erişimi önlemeye yardımcı olmak için cihaz şifrelemesi.
  - Altı basamaklı PIN veya parola.
  - Etkinlik dışı-zaman aşımı süresi.
  - Virüsten koruma ve kötü amaçlı yazılım koruması ve Windows 10 cihazlarda Windows Defender ile imza güncelleştirmeleri.
  - En son güvenlik güncelleştirmelerini içeren Windows 10 cihazlarda otomatik güncelleştirmeler.
  - Sertifikaları yönetilen cihazlara gönderme.
  - İş ve kişisel verilerin net bir şekilde ayrılması. Kullanıcılar veya yöneticiler cihazdan şirket verilerini seçerek silebilir ve resimler, kişisel e-posta hesapları ve kişisel dosyalar gibi kişisel verileri el değmemiş olarak bırakabilir.

Contoso, dağıtılan bilgisayarları ve şirkete ait akıllı telefonları ve tabletleri uygun Intune cihaz gruplarına ekleyerek kaydetti. Ayrıca çalışanların kişisel cihazlarını kaydetmeleri için bir KCG programı oluşturdular. Kayıtlı cihazlar, yönetilen ve güvenli cihazlara ve uygulamalarına neden olan Intune ilkeleri alır. Kaydedilmemiş cihazların, izin verilen uygulamaları belirten Mobil Uygulama Yönetimi (MAM) ilkeleri vardır.

Contoso mobil cihaz yönetimi dağıtım mimarisi aşağıdadır.

![Contoso mobil cihaz yönetimi dağıtım altyapısı.](../media/contoso-mdm/contoso-mdm-fig1.png)

## <a name="next-step"></a>Sonraki adım

Contoso'nun kuruluş genelinde önemli dijital varlıkları sınıflandırmak, tanımlamak ve korumak için Microsoft 365 [bilgi koruma özelliklerini](contoso-info-protect.md) nasıl kullandığını öğrenin.

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 için cihaz yönetimi](device-management-roadmap-microsoft-365.md)

[Microsoft 365 Kurumsal’a genel bakış](microsoft-365-overview.md)

[Test laboratuvarı kılavuzları](m365-enterprise-test-lab-guides.md)

