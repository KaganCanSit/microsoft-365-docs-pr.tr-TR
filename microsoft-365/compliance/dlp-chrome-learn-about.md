---
title: Microsoft Uyumluluk Uzantısı hakkında bilgi
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
description: Microsoft Uyumluluk Uzantısı, Google Chrome tarayıcısında dosya etkinliklerinin ve koruyucu eylemlerin izlenmesi ve kontrollerini genişlettir
ms.openlocfilehash: 15c62369bb8b4fc02926fa0e2b0bfc4834c371ac
ms.sourcegitcommit: 966344e1aa442a4d10a0fb05f56badd38c833bb2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2022
ms.locfileid: "63015564"
---
# <a name="learn-about-the-microsoft-compliance-extension"></a>Microsoft Uyumluluk Uzantısı hakkında bilgi

[Uç nokta veri](endpoint-dlp-learn-about.md) kaybı önleme (uç nokta DLP Windows 10), veri kaybını önlemenin [(DLP)](dlp-learn-about-dlp.md) etkinlik izleme ve koruma özelliklerini farklı cihazlardaki hassas öğelere Microsoft 365 genişletmektedir. Cihazlar uyumluluk çözümlerine Microsoft 365, kullanıcıların hassas öğelerle yaptıklarına ilişkin bilgiler etkinlik gezgininde görünür hale gelir ve DLP ilkeleri aracılığıyla bu öğeler [](data-classification-activity-explorer.md) üzerinde koruyucu işlemler [gerçekleştirebilirsiniz](create-test-tune-dlp-policy.md).

Microsoft Uyumluluk Uzantısı bir Windows 10 cihazına yüklendikten sonra, kuruluşlar kullanıcının Google Chrome kullanarak bir bulut hizmetine hassas bir öğeye erişmeyi veya bu bir bulut hizmetine karşıya yüklemeyi denemelerini ve DLP aracılığıyla koruyucu eylemleri uygulamaya çalışmalarını izleyebilir.  

## <a name="activities-you-can-monitor-and-take-action-on"></a>İzlemek ve üzerinde işlem gerçekleştirin

Microsoft Uyumluluk Uzantısı, kullanıcıların farklı cihazlarda çalışan hassas öğeler üzerinde gerçekleştirecekleri aşağıdaki etkinlik türlerini denetlemenizi ve Windows 10.

etkinlik |açıklama  | desteklenen ilke eylemleri|
|---------|---------|---------|
|buluta kopyalanan dosya  | Kullanıcının Chrome tarayıcısı aracılığıyla kısıtlanmış bir hizmet etki alanına hassas bir öğe karşıya yükleme girişiminde olduğunu algılar |denetim, geçersiz kılma ile engelle, engelle|
|dosya yazdırıldı  |Kullanıcının Chrome tarayıcıda açık olan hassas bir öğeyi yerel bir yazıcıya veya ağ yazıcısında yazdırmayı denemesi gerekir |denetim, geçersiz kılma ile engelle, engelle|
|panoya kopyalanan dosya |Kullanıcı Chrome tarayıcısında görüntülenen hassas bir öğeden bilgi kopyalamaya ve sonra bunu başka bir uygulamaya, işlemeye veya öğeye yapıştırmaya çalışır. |denetim, geçersiz kılma ile engelle, engelle|
|çıkarılabilir depolama alanına kopyalanan dosya    | Kullanıcının Chrome tarayıcıda açık olan hassas bir öğeden çıkarılabilir medyaya veya USB cihazına hassas bir öğe veya bilgi kopyalamayı denemesi gerekir |denetim, geçersiz kılma ile engelle, engelle|
|ağ paylaşımına kopyalanan dosya  |Kullanıcının Chrome tarayıcıda açık olan hassas bir öğeden ağ paylaşımına veya eşlenmiş bir ağ sürücüsüne hassas bir öğe veya bilgi kopyalamayı denemesi gerekir.|denetim, geçersiz kılma ile engelle, engelle |

## <a name="deployment-process"></a>Dağıtım işlemi
1. [Uç nokta veri kaybını önlemeye başlama](endpoint-dlp-getting-started.md)
2. [Windows 10 cihazları için Windows 10 yöntemleri](device-onboarding-overview.md)
3. [Uzantıyı cihazlarınıza Windows 10 yükleyin](dlp-chrome-get-started.md)
4. [Bulut hizmetine yüklemeyi kısıtlayan veya](create-test-tune-dlp-policy.md) izin verilmeyen tarayıcılar eylemleriyle erişimi kısıtlayan DLP ilkeleri oluşturun veya bu Windows 10 cihazlarınıza uygulama

## <a name="next-steps"></a>Sonraki adımlar

Tam [dağıtım yordamları ve senaryoları için bkz. Microsoft](dlp-chrome-get-started.md) Uyumluluk Uzantısını çalışmaya başlama.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Uyumluluk Uzantısı ile çalışmaya başlama](dlp-chrome-get-started.md)
- [Uç nokta Microsoft 365 kaybı önleme hakkında bilgi](endpoint-dlp-learn-about.md)
- [Microsoft Endpoint veri kaybı önleme ile çalışmaya başlama](endpoint-dlp-getting-started.md)
- [Microsoft Uç Noktası veri kaybını önlemeyi kullanma](endpoint-dlp-using.md)
- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)
- [DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md)
- [Etkinlik gezgini ile çalışmaya başlama](data-classification-activity-explorer.md)
- [Uç Nokta için Microsoft Defender](/windows/security/threat-protection/)
- [Insider Risk yönetimi](insider-risk-management.md)
