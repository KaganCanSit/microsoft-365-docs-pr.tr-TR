---
title: E Exchange Online, e-posta sırlarınızı nasıl güvence altına alır?
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 07/01/2019
audience: ITPro
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 989ba10c-f73f-4efb-ad1b-af3322e5f376
ms.collection:
- M365-security-compliance
description: Microsoft'Office 365 Güvenlik, Gizlilik ve Uyumluluk Bilgileri sağlayan Microsoft 365 Güven Merkezi'ne ek olarak, Microsoft'un veri merkezlerinde depola verilerinizin korunmasına nasıl yardımcı olduğunu da bilmek istiyor olabilirsiniz. Dağıtılmış Anahtar Yöneticisi (DKM) adlı bir teknoloji kullanıyoruz.
ms.openlocfilehash: a1d939ebfc1ecba1e7cb8b97111f677f754894b1
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019490"
---
# <a name="how-exchange-online-secures-your-email-secrets"></a>E Exchange Online, e-posta sırlarınızı nasıl güvence altına alır?

Bu makalede, Microsoft'un e-posta sırlarınızı veri merkezlerinde nasıl güvenli hale geldiği açıklanır.
  
## <a name="how-do-we-secure-secret-information-provided-by-you"></a>Sizin sağladığımız gizli bilgileri nasıl güvence altına alarız?

Microsoft'un Office 365 [Office 365](./get-started-with-service-trust-portal.md), Gizlilik ve Uyumluluk Bilgilerini sağlayan Office 365 Güven Merkezi'ne ek olarak, Microsoft'un veri merkezlerinde sağladığınız sırları korumaya nasıl yardımcı olduğunu da bilmek istiyor olabilirsiniz. Dağıtılmış Anahtar Yöneticisi (DKM) adlı bir teknoloji kullanıyoruz.
  
[Dağıtılmış Anahtar Yöneticisi](office-365-bitlocker-and-distributed-key-manager-for-encryption.md) (DKM), bilgileri şifrelemek ve şifrelerini çözmek için bir dizi gizli anahtar kullanan istemci tarafı işlevleridir. DKM ile şifrelenen verilerin şifresini çözmek için yalnızca Active Directory Etki Alanı Hizmetleri'nin belirli bir güvenlik grubunun üyeleri bu anahtarlara erişim sağlar. Başka Exchange Online, bu güvenlik grubunun yalnızca Exchange işlemlerinin çalıştır olduğu belirli hizmet hesapları vardır. Veri merkezinde standart işletim yordamı kapsamında, bu güvenlik grubunun bir parçası olan hiçbir insana kimlik bilgisi verilmiştir ve dolayısıyla hiçbir insan bu sırların şifresini çözebilecek anahtarlara erişemmektedir.
  
Hata ayıklama, sorun giderme veya denetim amaçlarına yönelik olarak, veri merkezi yöneticisinin güvenlik grubunun parçası olan geçici kimlik bilgileri elde etmek için yükseltilmiş erişim isteğinde  olması gerekir. Bu işlem için birden çok yasal onay düzeyi gerekir. Erişim verildiyse, tüm etkinlikler günlüğe kaydedilir ve denetlener. Buna ek olarak, yalnızca süresi otomatik olarak dolacak olan, daha sonra süresi dolana kadar erişim de verilir.
  
Ek koruma için DKM teknolojisi otomatik anahtar dağıtım ve arşivleme içerir. Bu ayrıca, aynı anahtarı süresiz olarak güvenmek zorunda kalmadan eski içeriğinize erişmeye devamnızı sağlar.
  
## <a name="where-does-exchange-online-make-use-of-dkm"></a>DKM'Exchange Online nereden kullanabilirim?

Microsoft, [dağıtılmış Anahtar Yöneticisi'ni](office-365-bitlocker-and-distributed-key-manager-for-encryption.md) kullanarak gizli Exchange Online kullanır. Örneğin:
  
- Bağlı hesaplar için e-posta hesabı kimlik bilgileri. Bağlı hesaplar Hotmail, Gmail ve Yahoo! e-posta hesaplarıyla oturum açın.

- Müşteri anahtarı. Müşteri Anahtarı ile [Hizmet şifrelemesi kullanıyorsanız](customer-key-overview.md), sırlarınızı korumak için [Azure Anahtar Kasasını](/azure/key-vault/key-vault-whatis) kullanırsanız.

## <a name="related-topics"></a>İlgili konular

[Şifreleme Office 365](encryption.md)
  
[Şifreleme hakkında teknik başvuru ayrıntıları](technical-reference-details-about-encryption.md)
  
[Güvenlik Uyumluluk Merkezi'nde &amp; Hizmet güvencesi](./service-assurance.md)
