---
title: Raporlama araçlarıyla ilgili sorunları giderme Microsoft Defender Virüsten Koruma
description: Güncelleştirme Uyumluluğu altında koruma durumunu bildirmeye çalışırken karşılaşılan yaygın Microsoft Defender Virüsten Koruma sorunları tanımlama ve çözme
keywords: sorun giderme, hata, düzeltme, uyumluluğu güncelleştirme, işletim sistemi, monitör, rapor, Microsoft Defender Virüsten Koruma
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: m365-security-compliance
ms.openlocfilehash: e17f50eb02fa6fbc3c34526ca064543b7afbdea2
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997487"
---
# <a name="troubleshoot-microsoft-defender-antivirus-reporting-in-update-compliance"></a>Güncelleştirme Microsoft Defender Virüsten Koruma raporlama sorunlarını giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!IMPORTANT]
> 31 Mart 2020'de, Güncelleştirme Microsoft Defender Virüsten Koruma raporlama özelliği kaldırılacaktır. Güvenlik özellikleri ve güncelleştirmeleri üzerinde daha iyi denetime olanak sağlayan [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager) kullanarak güvenlik uyumluluk ilkelerini tanımlamaya ve gözden geçirmeye devam edin.

Güncelleştirme Uyumluluğu Microsoft Defender Virüsten Koruma bilgileri kullanabilirsiniz. E3, B, F1, VL ve lisans Pro. Bununla birlikte, E5 lisansları için Uç nokta portalı için [Microsoft Defender'ı kullanasınız](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Lisans seçenekleri hakkında daha fazla bilgi edinmek için ürün [Windows 10 seçeneklerine bakın](https://www.microsoft.com/licensing/product-licensing/windows10.aspx).

[Windows Analytics Update Compliance'i](/windows/deployment/update/update-compliance-using#wdav-assessment) kullanarak ağınız için Microsoft Defender Virüsten Koruma kullanan cihazların veya uç noktaların koruma durumunu raporlamak için kullanırsanız, sorunlarla veya sorunlarla karşılaşabilirsiniz.

Normalde, bir sorunun en yaygın göstergeleri:

- Yalnızca görmeyi beklemede olduğunuz tüm cihazların küçük bir sayısını veya alt kümesini görüyorsunuz
- Hiçbir cihaz görmüyoruz
- Gördüğünüz raporlar ve bilgiler eskidir (birkaç gün önce)

Güncelleştirme Uyumluluğu ile ilgili Microsoft Defender Virüsten Koruma hizmetle ilgili yaygın hata kodları ve olay kimlikleri için bkz. [Microsoft Defender Virüsten Koruma.](troubleshoot-microsoft-defender-antivirus.md)

Bu sorunları gidermenin üç adımı vardır:

1. Tüm önkoşullara uyanı doğrulama
2. Bulut tabanlı Windows Defender bağlantınızı denetleme
3. Destek günlüklerini gönderme

> [!IMPORTANT]
> Cihazların Güncelleştirme Uyumluluğu'ta görünmeye başlaması normalde 3 gün sürer.

## <a name="confirm-prerequisites"></a>Önkoşulları onaylayın

Cihazların Güncelleştirme Uyumluluğu'ta düzgün bir şekilde gösternsin diye, hem Güncelleştirme Uyumluluğu hizmeti hem de Güncelleştirme Uyumluluğu hizmetinin bazı önkoşullarını karşılamanız Microsoft Defender Virüsten Koruma:

>[!div class="checklist"]
>
> - Uç noktalar, Microsoft Defender Virüsten Koruma virüsten koruma uygulaması olarak E-posta uygulamasını kullanıyor. [Başka herhangi bir virüsten koruma uygulamasının Microsoft Defender Virüsten Koruma devre dışı bırakmasını](microsoft-defender-antivirus-compatibility.md) neden olur ve uç nokta Güncelleştirme Uyumluluğu'ta bildirlanmaz.
> - [Bulut teslimi koruması etkinleştirilir](enable-cloud-protection-microsoft-defender-antivirus.md).
> - Uç noktalar [buluta Microsoft Defender Virüsten Koruma olabilir](configure-network-connections-microsoft-defender-antivirus.md#validate-connections-between-your-network-and-the-cloud)
> - Uç nokta 1607 veya Windows 10 daha önceki bir sürümde Windows 10 için tanılama verileri İyileştirilmiş [düzeye ayar olmalıdır](/windows/configuration/configure-windows-diagnostic-data-in-your-organization#enhanced-level).
> - Tüm gereksinimlerin karşı yaklaşık 3 gün içinde karşı bekleniyor

"Uyumluluk Güncelleştirmeleri ile Microsoft Defender Virüsten Koruma kullanabilirsiniz. E3, B, F1, VL ve lisans Pro. Bununla birlikte, E5 lisansları için Uç Nokta portalı için Microsoft Defender'ı kullansanız (/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Lisans seçenekleri hakkında daha fazla bilgi edinmek için ürün Windows 10 seçeneklerine bakın"

Yukarıdaki önkoşulların hepsi karşı kullandısa, tanılama bilgilerini toplamak ve bize göndermek için bir sonraki adıma geçin.

> [!div class="nextstepaction"]
> [Güncelleştirme Uyumluluğu sorunlarını gidermek için tanılama verilerini toplama](collect-diagnostic-data.md)


## <a name="related-topics"></a>İlgili konular

- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Dağıtım Microsoft Defender Virüsten Koruma](deploy-manage-report-microsoft-defender-antivirus.md)
