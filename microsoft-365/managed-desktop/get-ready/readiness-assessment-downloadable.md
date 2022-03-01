---
title: İndirilebilir hazırlık değerlendirme denetleyicisi
description: Gerekli uç noktalar da dahil olmak üzere cihaz ve ağ ayarlarını denetler
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 9e3ad0953cdbd6561f9a0145ccff5aefe24b8dfb
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011833"
---
# <a name="downloadable-readiness-assessment-checker"></a>İndirilebilir hazırlık değerlendirme denetleyicisi

Microsoft Yönetilen Masaüstü ile iyi çalışması için cihazların donanım ve ayarlarla ilgili belirli gereksinimleri karşılaması gerekir. Her cihazın önemli uç noktalara ulaşıyor olması gerekir.

HTML raporu almak, sonuçları görüntülemek ve önlem almak için hazırlık değerlendirme denetleyicisi aracını indirin ve çalıştırın. Aracı ve destek dosyalarını indirmeniz gerekir. Ardından, Microsoft Yönetilen Masaüstü'ne kaydetmek istediğiniz her cihazda el ile çalıştırın.

Her denetimde, araç şu üç olası sonuçdan birini bildirecek:

| Sonuç | Anlamı |
| ----- | ----- |
| Hazır | Kaydı tamamlamadan önce herhangi bir işlem gerekmez. |
| Danışma | Kayıt ve kullanıcılar için en iyi deneyimi yaşamak için araçta yer alan adımları izleyin. <br><br> Kaydı *tamamabilirsiniz* , ancak ilk cihazınızı dağıtmadan önce bu sorunları çözmeniz gerekir. |
| Hazır değil | **Bu sorunları** çözesiniz kayıt başarısız olur. <br><br> Bunları çözmek için araçta olan adımları izleyin. |

## <a name="obtain-the-checker"></a>Denetleyiciyi alın

.zip indirin https://aka.ms/mmddratoolv0.

> [!NOTE]
> Aracı çalıştıran kullanıcı, aracı çalıştıran cihazda yerel Yönetici haklarına sahip olması gerekir.

**Aracı çalıştırmak için:**

1. İndirilen .zip istediğiniz her cihaza kopyalayın.
2. Sıkıştırılmış indirmedeki tüm dosyaları ayıkla.
3. **Microsoft.MMD.DeviceReadinessAssessmentTool.exe.**
4. Kullanıcı Erişimi Denetimi istemi görüntülendiğinde Evet'i **seçin**. Araç çalışır ve varsayılan tarayıcınızda bir rapor açar.

Ayrıca posta arşivini paylaşılan bir .zip indirip ayıklar, arşive her **Microsoft.MMD.DeviceReadinessAssessmentTool.exe** erişebilirsiniz. Ardından yerel olarak çalıştırın.

## <a name="checks"></a>Denetimler

İndirilebilir araç, cihaz ve ağ ile ilgili öğeleri denetler:

| Çek | Açıklama |
| ----- | ----- |
| Donanım | Cihazların Microsoft Yönetilen Masaüstü ile çalışmak için belirli donanım gereksinimlerini karşılaması gerekir. Daha fazla bilgi için bkz. [Cihaz gereksinimleri](../service-description/device-list.md). <br><br> Cihazınız denetimlerden herhangi biri başarısız olursa, Microsoft Yönetilen Masaüstü ile uyumlu değildir. |
| Ağ uç noktaları | Microsoft Yönetilen Masaüstü ile çalışmak için [çok sayıda önemli](network.md) uç noktaya ulaşabilirsiniz. <br><br> Araç hazır değil **sonucu bildirıyorsa** , hangi uç noktaların erişilemez olduğunu bulmak için ayrıntılı rapora bakın. Ardından, bu uç noktalara ulaşılana kadar güvenlik duvarınızı veya diğer ağ ayarlarınızı ayarlayın. |

### <a name="other-settings"></a>Diğer ayarlar

| Ayar | Açıklama |
| ----- | ----- |
| Enterprise Wi-Fi profillerini oluşturma | Danışma **sonucu** , düzgün çalışması için sertifika ve Wi-Fi çok kullanıcı profili kullanıyorsanız anlamına gelir. Daha fazla bilgi için bkz [. Sertifikaları ve #A0/VPN profilini dağıtma](certs-wifi-lan.md#deploy-certificates-and-wi-fivpn-profile). |
| LAN profilleri | Danışma **sonucu** , düzgün çalışması için sertifika ve profiller gereken LAN'lere sahip olduğunuz anlamına gelir. Daha fazla bilgi için bkz [. Microsoft Yönetilen Masaüstü için sertifikaları ve ağ profillerini hazırlama](certs-wifi-lan.md). |
| VPN profilleri | Danışma **sonucu** , sanal özel ağ (VPN) kullanmakta olduğunuz anlamına gelir. Kullanıcılarla tümleşik sertifikaların dağıtın bir VPN profili Microsoft Intune. Daha fazla bilgi için bkz [. Microsoft Yönetilen Masaüstü için sertifikaları ve ağ profillerini hazırlama](certs-wifi-lan.md). |
| Eşlenmiş sürücüler | Öneri **sonucu** , bazı eşlenmiş sürücülerin olduğu anlamına gelir ve bu önerilmez. Daha fazla bilgi için bkz [. Eşlenmiş sürücüleri Microsoft Yönetilen Masaüstü için hazırlama](mapped-drives.md). |
| Kuyrukları yazdırma | Öneri **sonucu** , önerilmez, bekleyen bazı yazdırma sıranız olduğu anlamına gelir. Bulut yazdırmayı kullanmak bir çözüm olabilir. Daha fazla bilgi için bkz [. Microsoft Yönetilen Masaüstü için yazdırma kaynaklarını hazırlama](printing.md). |
| Proxies | Danışma **sonucu** , kullanımda bir proxy sunucunuz olduğu anlamına gelir. Daha fazla bilgi için bkz [. Microsoft Yönetilen Masaüstü için ağ yapılandırması](network.md). |
