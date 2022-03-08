---
title: Microsoft Yönetilen Masaüstü ve Windows 11
description: Windows 11'in hizmette nasıl ve ne zaman kullanılabilir olduğu
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: 494f147dad24b8c668fcb8adfc9b8a845a5fbe8f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317185"
---
# <a name="microsoft-managed-desktop-and-windows-11"></a>Microsoft Yönetilen Masaüstü ve Windows 11

Windows 11'in açıklanmasının ardından, Windows cihazları güncel tutma çabalarınız kapsamında 11 geçiş Windows 10 planlamaya başlamış olabilirsiniz.

Bu makalede önemli noktalar ve Microsoft Yönetilen Masaüstü'nin ortamlarınız için sorunsuz geçişleri nasıl destekleyecekleri açıklanmıştır. 11.Windows daha fazla bilgi için bkz. [Windows genel bakış](/windows/whats-new/windows-11).

Microsoft Yönetilen Masaüstü cihazlarınıza Windows 11'i yüklemek için izlemeniz gereken belirli adımlar için bkz. Microsoft Yönetilen Masaüstü ile [Windows 11'de önizleme ve test etme](../working-with-managed-desktop/test-win11-mmd.md).

## <a name="timeline-for-windows-10-and-windows-11"></a>Windows 10 ve Windows 11 için zaman çizelgesi

Windows 11 genel olarak 4 Ekim 2021'de kullanıma hazır hale geldi. Tüketici ve kurumsal dağıtım için hazır ve tam olarak desteklenen bir platformdur.

Ocak 2023'den itibaren tüm Microsoft Yönetilen Masaüstü cihazları için dağıtım zamanlamayı başlatmaya başlayacağız. Bununla birlikte, 11 gün içinde dağıtım yapmak isteyen Windows destek sağlarız. Yöneticilerin, teknik hazırlığı ve işletmeyle ilgili dikkate alınacak noktalara göre her bir kiracı için geçiş planları geliştirmelerini ve uygulamalarını istiyoruz.

Microsoft Yönetilen Masaüstü, kurumsal destek Windows 10 ulaşana kadar uygulamaları paralel olarak desteklemeye devam etmektedir. Yaşam [Windows 10 için bkz](/windows/release-health/release-information). Yayınla ilgili sürüm bilgileri.

## <a name="assessing-pre-release-versions-of-windows-11"></a>Windows 11'in yayın öncesi sürümlerini değerlendirme

Microsoft Yönetilen Masaüstü cihazlarının %95'inden fazlası 11 Windows uygundur. Yükseltmeyi üretim dağıtımı öncesinde test cihazlarda denemek istiyor olabilirsiniz. 11 sistem Windows hakkında daha fazla bilgi için bkz[. Windows gereksinimlerini karşılama](/windows/whats-new/windows-11-requirements).

Microsoft Yönetilen Masaüstü cihazları için cihazları [11 test Windows cihaz grubuna eklersiniz](/microsoft-365/managed-desktop/working-with-managed-desktop/test-win11-mmd?view=o365-worldwide#add-devices-to-the-windows-11-test-group). Bu grup, Microsoft Windows Masaüstü temel yapılandırmasıyla birlikte en son 11 genel kullanılabilirlik derlemesini alır. Cihaz grubuna eklendiktan sonra bir ile iki gün arasında bir cihazın yeni ayarları seçmesine izin verir ve 11 Windows sunulur.

Microsoft Yönetilen Masaüstü tarafından yönetil olmayan cihazlar için, 11. [Endpoint Manager](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/endpoint-manager-simplifies-upgrades-to-windows-11/ba-p/2771886) dağıtma hakkında bilgi edinmek için Windows okuyabilirsiniz. Windows 11 ve sonraki bir sürümü çalıştıran cihazlarınız varsa ve bunları Microsoft Yönetilen Masaüstü'ne kaydettiyseniz, geri Windows 10.

## <a name="support-for-pre-release-windows-11-devices"></a>11 cihaz için Windows desteği

Genel kullanılabilirlik öncesi Windows 11 testine katılmayı tercih eden cihazlar önizleme derlemelerini yüklemiş olabilir.

Bu durumdaki Microsoft Yönetilen Masaüstü cihazları için 11 genel Windows sürümü sunulacaktır. Bununla birlikte, karşılaşılan sorunları çözmek için cihazlar destek çözmeye devam ediyor. Microsoft Yönetilen Masaüstü, tüm yönetilen cihazları güvenlik tehditlerini izler ve cihazın Windows önizleme sürümü çalıştırsa da çalıştırılmaksızın tüm uyarıları yanıtlar.

Verimli çalışırken Windows 11'e geçişe yardımcı olmak için kararlıyız, çünkü platformda karşılaştığınız kusurları bildirmenizi teşvik ediyoruz. Öncelikleriz:

- 11'de geniş dağıtım üzerine kullanıcı üretkenliğini Windows kusurları.
- Bu cihazlarda kullanıcı üretkenliğini engel Windows 10 kusurları.

## <a name="testing-application-compatibility"></a>Uygulama uyumluluğunu test etme

Üretkenlik kesintileri olası olduğundan, uygulama uyumluluğu herhangi bir platform geçişi konusunda en yaygın kaygılardan birisidir. 11. adıma sorunsuz uygulama geçişleri konusunda güvenerek çalışmanıza yardımcı olmak için çeşitli proaktif ve yeniden Windows kullanıyoruz.

### <a name="proactive-measures"></a>Proaktif önlemler

Aşağıda bazı proaktif önlemler yer alıyor:

| Proaktif önlemler | Açıklama |
| ----- | ----- |
| Yaygın uygulamalar | Microsoft, en yaygın olarak 11 derleme üzerinde dağıtılan kurumsal uygulamaları ve paketleri Windows test ediyor. Test sırasında bulunan sorunları çözmek için dış yazılım yayıncıları ve iç ürün ekipleriyle birlikte çalışıyoruz. Proaktif uyumluluk testi çalışmamız hakkında daha fazla bilgi için, [Uygulama Uyumluluğu bloguna bakın](https://blogs.windows.com/windowsexperience/2019/01/15/application-compatibility-in-the-windows-ecosystem/).
| İş yeri uygulamaları | [Test Tabanı,](https://www.microsoft.com/en-us/testbase) uygulama yayımcılarının ve IT yöneticilerinin Microsoft'un güvenli bir Azure ortamında Windows 11 derlemelerini çalıştıran sanal bir makinede çalıştırması için uygulama ve test örnekleri göndermek için kullanabileceği bir kaynaktır.<br><br>Özel bir Azure portalında, her test yürütmesi için sonuçlar, test öngörüleri ve regresyon çözümlemesi kullanabilirsiniz. Microsoft Yönetilen Masaüstü, uygulama kullanımı ve güvenilirlik verilerine göre doğrulama için iş alanı uygulamalarınızı önceliklendirmenize yardımcı olur. Test Tabanı hakkında daha fazla bilgi için bkz. Test [Microsoft 365](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/test-base-for-microsoft-365-microsoft-ignite-2021-updates/ba-p/2185566). |

### <a name="reactive-measures"></a>Reactive measures

Test veya üretim ortamlarında uygulama uyumluluk sorunlarıyla karşılaşırsanız, bir destek isteği açarak ücret ödemeden [destek alabilirsiniz](/microsoft-365/managed-desktop/working-with-managed-desktop/test-win11-mmd?view=o365-worldwide#report-issues).

En Windows 11 sürümü için destek, en son işletim sistemi derlemeleri üzerinde çalışan aşağıdaki uygulamaları içeren tüm işlevleri içerir:

- Office
- Microsoft Edge
- Teams
- iş hattı uygulamaları

Microsoft App Assure, gerektiğinde uygulama uyumluluk sorunlarını önceliklerini belirlemek ve çözmek için uygulama yayıncılarını doğrudan etkileşime almaktadır.
