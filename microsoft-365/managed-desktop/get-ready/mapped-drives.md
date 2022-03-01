---
title: Microsoft Yönetilen Masaüstü için eşlenmiş sürücüleri hazırlama
description: Kullanıcıların eşlenmiş sürücülerde verilere erişe olduğundan emin olmak için önemli adımlar
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: d8100323350b11cb2329d752892cd64b1bc764a0
ms.sourcegitcommit: d4797cfc15c732f1a7ef21e4f944e672a7170f9a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2022
ms.locfileid: "63016648"
---
# <a name="prepare-mapped-drives-for-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü için eşlenmiş sürücüleri hazırlama

Birçok kurumsal ortamda, kullanıcılarının veya ekiplerinin dosyaları paylaşmasına ve depolamasına ya da şirket içi uygulamalara izin vermesine olanak sağlayan eşlenmiş sürücülere yönelik eski gereksinimler vardır.

Microsoft, Microsoft Yönetilen Masaüstü ile eşlenmiş sürücülerin kullanımını önerilmez. Bunun yerine, dosya erişimi çözümlerinizi aşağıdaki gibi modernleştirmenizi öneririz:
  
- Tek tek kullanıcıların kullandığı eşlenmiş sürücüleri başka kullanıcılara OneDrive İş.
- Ekipler tarafından dosyaları SharePoint Online'a paylaşmak için kullanılan eşlenmiş SharePoint geçirebilirsiniz.
- Bu gereksinimi kaldırmak için şirket içi dosya paylaşımlarını kullanan tüm uygulamaları modernleştirin veya değiştirin.
  
Bu hizmetleri modernleştirerek Microsoft Yönetilen Masaüstü ile en iyi kullanıcı deneyimini sağlayacaktır. Microsoft FastTrack Hizmetleri, Microsoft Bulut Hizmetleri'i kullanarak ortamınızı modernleştirmenize yardımcı olabilir. Uygun Hizmetler ve Planlar'da hizmetler için uygun FastTrack [olup olmadığını kontrol edin](/fasttrack/m365-eligible-services-and-plans). Ardından, Microsoft Yönetilen Masaüstü'ne hazırlanmak için doğrudan bu kişi ile iletişime geçin. Çevrimiçi Geçiş hakkında daha fazla FastTrack OneDrive İş veya çevrimiçi SharePoint için bkz. [Veri Geçişi](/fasttrack/o365-data-migration).

## <a name="mapped-drives-on-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü'nden eşlenmiş sürücüler

Bazı kullanım durumlarında eşlenmiş sürücüleri kaldıramaz veya değiştireyseniz, bu sürücülerin Microsoft Yönetilen Masaüstü kullanıcılarına dağıtılması için Microsoft Yönetilen Masaüstü Yönetim Portalı'nda bir destek isteği göndermeniz gerekir.

Böyle bir istek için, destek isteğinde aşağıdaki ayrıntıları sağlay gerekir:

- Microsoft Yönetilen Masaüstü cihazlarıyla eşlenmiş olması gereken dosya paylaşım konumlarına giden tüm UNC yolları.
- Bu dosya paylaşım konumlarına erişim gerektiren kullanıcı grupları.
- Atanacak belirli bir sürücü harfi (gerekirse).

Örneğin:

| Sürücü harfi | UNC yolu | Kullanıcı grubu |
|--------------|----------|------------|
| X:  | \\\server\share\Marketing | ContosoMarketing |

Şunları yapmak tamamen sizin sorumluluğumdadır:

- Kullanıcıların ve grupların dosya paylaşım konumlarına erişmek için doğru izinlere sahip olduğundan ve bu konumlara sahip olduğundan emin olun
- Şirket içi dosya hizmetlerinin erişilebilir olmasını sağlar.

Bu tür dosya paylaşımları için gereksinimlerinizi en kısa zamanda kaldırmanız gerekir.

**Microsoft Yönetilen Masaüstü'ne eşlenmiş sürücülerin dağıtılması için:**

Eşlenmiş sürücülerden kaçınılamay olduğundan ve herhangi bir destek isteği göndermeden önce gereksinimleri dikkatle gözden geçirmelisiniz.

1. [Destek'e Microsoft Endpoint Manager](https://endpoint.microsoft.com/) Sorun Giderme **+ destek'i seçin**.
1. Microsoft Yönetilen **Masaüstü bölümünde** Hizmet **istekleri'ne tıklayın**.
1. "Eşlenmiş sürücüler dağıtımı" başlıklı bir destek isteği gönderin ve tüm gerekli dosya paylaşımı ayrıntılarını sağlama.  
1. Microsoft Yönetilen Masaüstü IT İşlemleri, isteğin ne zaman tamamlandıktan sonra destek isteği güncelleştirmelerini kullanarak bilgi edinebilirsiniz. Başlangıçta bu yapılandırma yalnızca Test dağıtım grubunda cihazlara dağıtılacaktır.  
1. Microsoft Yönetilen Masaüstü IT İşlemleri tarafından dağıtılan yapılandırmanın beklediğiniz gibi çalıştığını test edip onaylamanız gerekir.
1. Aynı destek isteğinde, sınamanızı tamamlandıktan **sonra** Microsoft Yönetilen Masaüstü IT İşlemlerini bildirmek için Tartışma sekmesini kullanarak yanıtlayın.  
1. Microsoft Yönetilen Masaüstü IT İşlemleri ekibi yapılandırmayı diğer dağıtım gruplarına dağıtır.

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü için hazır adımlar

1. [Microsoft Yönetilen Masaüstü için önkoşulları gözden geçirebilirsiniz](prerequisites.md).
1. Hazırlık [değerlendirme araçlarını çalıştırın](readiness-assessment-tool.md).
1. Satın [Şirket Portalı](../get-started/company-portal.md).
1. Konuk [hesapları için önkoşulları gözden geçirebilirsiniz](guest-accounts.md).
1. Ağ [yapılandırmasını denetleme](network.md).
1. [Sertifikaları ve ağ profillerini hazırlayın](certs-wifi-lan.md).
1. [Verileri kullanıcı erişimini hazırlama](authentication.md).
1. [Uygulamaları hazırlama](apps.md).
1. Eşlenmiş sürücüleri hazırlama (bu makale).
1. [Yazdırma kaynaklarını hazırlama](printing.md).
1. Cihaz [adlarını adresle](address-device-names.md).
