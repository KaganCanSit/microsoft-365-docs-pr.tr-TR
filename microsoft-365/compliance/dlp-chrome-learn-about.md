---
title: Microsoft Purview Uzantısı hakkında bilgi edinme
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: Microsoft Purview Uzantısı, dosya etkinliklerinin ve koruyucu eylemlerin izlenmesini ve denetimini Google Chrome tarayıcısına genişletir
ms.openlocfilehash: 08078871765a75577475c93ba35cabda9ee3fd6a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622909"
---
# <a name="learn-about-the-microsoft-purview-extension"></a>Microsoft Purview Uzantısı hakkında bilgi edinme

[Uç nokta veri kaybı önleme (uç nokta DLP),](endpoint-dlp-learn-about.md) [Microsoft Purview veri kaybı önlemenin (DLP)](dlp-learn-about-dlp.md) etkinlik izleme ve koruma özelliklerini Windows 10 cihazlardaki hassas öğelere genişletir. Cihazlar Microsoft Purview çözümlerine eklendikten sonra, kullanıcıların hassas öğelerle yaptıklarıyla ilgili bilgiler [etkinlik gezgininde](data-classification-activity-explorer.md) görünür hale getirilir ve [DLP ilkeleri](create-test-tune-dlp-policy.md) aracılığıyla bu öğeler üzerinde koruyucu eylemler uygulayabilirsiniz.

Uzantı bir Windows 10 cihazına yüklendikten sonra, kuruluşlar bir kullanıcının Google Chrome kullanarak hassas bir öğeye erişmeye veya bir bulut hizmetine yüklemeye çalıştığında izleyebilir ve DLP aracılığıyla koruyucu eylemler uygulayabilir.  

## <a name="activities-you-can-monitor-and-take-action-on"></a>İzleyebileceğiniz ve üzerinde işlem yapabileceğiniz etkinlikler

Uzantı, kullanıcıların Windows 10 çalıştıran cihazlarda hassas öğeler üzerinde gerçekleştirecekleri aşağıdaki etkinlik türlerini denetlemenize ve yönetmenize olanak tanır.

Etkinlik |Açıklama  | desteklenen ilke eylemleri|
|---------|---------|---------|
|dosya buluta kopyalandı  | Bir kullanıcının Chrome tarayıcısı aracılığıyla kısıtlanmış bir hizmet etki alanına hassas bir öğe yüklemeyi denediğinde algılar |denetim, geçersiz kılma ile engelleme, engelleme|
|dosya yazdırıldı  |Kullanıcının Chrome tarayıcısında açık olan hassas bir öğeyi yerel veya ağ yazıcısına yazdırmaya çalıştığında algılar |denetim, geçersiz kılma ile engelleme, engelleme|
|dosya panoya kopyalandı |Bir kullanıcının Chrome tarayıcısında görüntülenen hassas bir öğeden bilgileri kopyalamaya çalıştığında bunu algılar ve ardından başka bir uygulama, işlem veya öğeye yapıştırır. |denetim, geçersiz kılma ile engelleme, engelleme|
|dosya çıkarılabilir depolama birimine kopyalandı    | Bir kullanıcının Chrome tarayıcısında açık olan hassas bir öğeden çıkarılabilir medyaya veya USB cihazına hassas bir öğeyi veya bilgileri kopyalamaya çalıştığında algılar |denetim, geçersiz kılma ile engelleme, engelleme|
|dosya ağ paylaşımına kopyalandı  |Bir kullanıcının Chrome tarayıcısında açık olan hassas bir öğeden bir ağ paylaşımına veya eşlenmiş ağ sürücüsüne hassas bir öğeyi veya bilgileri kopyalamayı denediğini algılar.|denetim, geçersiz kılma ile engelleme, engelleme |

## <a name="deployment-process"></a>Dağıtım işlemi
1. [Uç nokta veri kaybı önlemeyi kullanmaya başlama](endpoint-dlp-getting-started.md)
2. [Windows 10 cihazlar için ekleme araçları ve yöntemleri](device-onboarding-overview.md)
3. [Uzantıyı Windows 10 cihazlarınıza yükleme](dlp-chrome-get-started.md)
4. Bulut hizmetine yüklemeyi veya izin verilmeyen tarayıcı eylemleriyle erişimi kısıtlayan ve bunları Windows 10 cihazlarınıza uygulayan [DLP ilkeleri oluşturma veya düzenleme](create-test-tune-dlp-policy.md)

## <a name="next-steps"></a>Sonraki adımlar

Eksiksiz dağıtım yordamları ve senaryoları için bkz. [Microsoft Purview Uzantısı ile çalışmaya başlama](dlp-chrome-get-started.md) .

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Purview Uzantısı'nı kullanmaya başlama](dlp-chrome-get-started.md)
- [Uç nokta veri kaybı önleme hakkında daha fazla bilgi edinme](endpoint-dlp-learn-about.md)
- [Uç nokta veri kaybı önlemeyi kullanmaya başlama](endpoint-dlp-getting-started.md)
- [Uç noktada veri kaybı önlemeyi kullanma](endpoint-dlp-using.md)
- [Veri kaybı önleme hakkında daha fazla bilgi edinme](dlp-learn-about-dlp.md)
- [Bir DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md)
- [Etkinlik gezginini kullanmaya başlama](data-classification-activity-explorer.md)
- [Uç Nokta için Microsoft Defender](/windows/security/threat-protection/)
- [İçeriden risk yönetimi](insider-risk-management.md)
