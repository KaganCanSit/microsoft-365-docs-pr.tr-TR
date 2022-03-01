---
title: Contoso için mobil cihaz yönetimi
author: kelleyvice-msft
f1.keywords:
- NOCSH
ms.author: kvice
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom: ''
description: Contoso'ya Microsoft Intune Microsoft 365 cihazları ve bu cihazlarda çalışan uygulamaları yönetmek için Kurumsal'da Nasıl Contoso'ya sahip olduğunu öğrenin.
ms.openlocfilehash: dedda98083dd5a27c4c7721b5ae8e5dc1fed4bad
ms.sourcegitcommit: 07405a81513d1c63071a128b9d5070d3a3bfe1cd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "63006806"
---
# <a name="mobile-device-management-for-contoso"></a>Contoso için mobil cihaz yönetimi

Microsoft 365 uygulamaları, Intune'ı ve mobil cihaz ile uygulama yönetimini ve güvenliğini destekleyen bir dizi Azure hizmeti içerir.

Contoso'da mobil etkinleştirilmiş birçok çalışan var. Bazılarında Contoso konumlarında ofisleri, bazıları ise ofisleri yoktur. Contoso'ya çalışanların üretkenliğini etkinleştirmenin ama cihazları, bu cihazlarda depolanan Contoso verilerini ve uygulama davranışını güvenli tutmak için bir yol gerekiyordu.

## <a name="plan"></a>Plan

Contoso, Kurumsal cihazlar için mobil cihaz yönetimiyle ilgili aşağıdaki Intune Microsoft 365 belirledi:

- Mobil Exchange Online güvenli bir şekilde erişilebilen e-posta ve verileri koruyun.
- Contoso çalışanları için kendi cihazınızı getirin (BYOD) programı kullanın.
- Contoso çalışanlarına kuruluşa ait telefon ve sınırlı kullanımlı paylaşılan tabletleri sorun.

Contoso, Intune'i kullanarak şunları yapmak için kullanmaz:

- Çalışanların, erişilen bir genel Microsoft 365 bilgi noktası üzerinden güvenli bir şekilde erişmesine izin verme.
- Şirket içi e-postayı ve verileri koruyun; bu şekilde mobil cihazlar tarafından güvenle erişilebilir, çünkü şirket içi Microsoft Exchange yoktur.

## <a name="deploy"></a>Dağıtma

Contoso mobil cihaz yönetim altyapısını şu şekilde kuracak:

- Intune'i Mobil Cihaz Yönetimi (MDM) yetkilisi olarak ayarlayın ve Azure'da Intune'i kullanarak içeriği yönetin ve cihazları yönetin
- Kayıt Azure Active Directory Intune ayarları ve cihaz tabanlı Koşullu Erişim ilkeleri için cihazlar için kullanıcı grupları (Azure AD) grupları oluşturuldu

  Daha fazla bilgi için bkz. [Contoso Koşullu Erişim ilkeleri](contoso-identity.md#conditional-access-policies-for-zero-trust-identity-and-device-access).

- iPad, iMac, iPhone ve kurumsal iPhone'lara sahip çalışanları desteklemek için Apple cihaz platformu etkinleştirildi
- Contoso'ya özgü hüküm ve koşullar ilkeleri oluşturulmuştur ve bu ilkeler Contoso'Şirket Portalı mobil cihazlara yüklemesi sırasında görülür
- Kaydolmamış cihazlar için, Microsoft 365 hizmetleri için kimlik doğrulaması gerektiren bir dizi Mobil Uygulama Yönetimi (MAM) ilkeleri uygulanmıştır
- Zorunlu olan Intune ilkeleri oluşturuldu:
  - İzin verilen uygulamalar.
  - Yetkisiz erişimi önlemeye yardımcı olmak için cihaz şifrelemesi.
  - Altı basamaklı bir PIN veya parola.
  - Etkileşim dışı zaman aşımı süresi.
  - Virüsten koruma ve kötü amaçlı yazılıma karşı koruma ve Windows Defender ve Windows 10 güncelleştirmeleri.
  - En son Windows 10 güncelleştirmeleri içeren mobil cihazlarda otomatik güncelleştirmeler.
  - Yönetilen cihazlara sertifikalar iletir.
  - İş ve kişisel verilerin net bir ayrımı. Kullanıcılar veya yöneticiler cihazdan şirket verilerini seçmeli olarak temizlerken, resimler, kişisel e-posta hesapları ve kişisel dosyalar gibi kişisel verileri olduğu gibi kişisel dosyaları olduğu gibi bırakabilirsiniz.

Contoso, uygun Intune cihaz gruplarına ekleyerek dağıtılmış bilgisayarları ve şirkete ait akıllı telefon ve tabletleri kaydetti. Ayrıca, çalışanların kişisel cihazlarını kaydetmeleri için bir BYOD programı da kurtılar. Kayıtlı cihazlar Intune ilkeleri alır ve sonuçta yönetilen ve güvenli cihazlar ve uygulamaları elde olur. Kaydolmamış olan cihazlar, izin verilen uygulamaları belirten Mobil Uygulama Yönetimi (MAM) ilkelerine sahiptir.

Burada, Contoso mobil cihaz yönetimi dağıtım mimarisi ve bilgileri bulunmaktadır.

![Contoso mobil cihaz yönetimi dağıtım altyapısı.](../media/contoso-mdm/contoso-mdm-fig1.png)

## <a name="next-step"></a>Sonraki adım

Contoso'nın [kuruluş genelinde çok](contoso-info-protect.md) önemli dijital varlıkları sınıflandırmak, Microsoft 365 ve korumak için kurumsal şirketlere yardımcı olan bilgi koruma özelliklerini nasıl kullandığını öğrenin.

## <a name="see-also"></a>Ayrıca bkz.

[Mobil cihaz için cihaz Microsoft 365](device-management-roadmap-microsoft-365.md)

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Test laboratuvarı kılavuzları](m365-enterprise-test-lab-guides.md)

