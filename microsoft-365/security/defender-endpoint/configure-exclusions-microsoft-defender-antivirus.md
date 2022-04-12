---
title: Microsoft Defender Virüsten Koruma taramaları için dışlamaları ayarlama
description: Dosyaları (belirtilen işlemler tarafından değiştirilen dosyalar dahil) ve klasörlerin Microsoft Defender Virüsten Koruma tarafından taranmasını dışlayabilirsiniz. Dışlamalarınızı PowerShell ile doğrulayın.
keywords: ''
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ksarens
manager: dansimp
ms.technology: mde
ms.audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: c9796f4e5154fd46d1479f0cbfa25f2afaf4e9bb
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64787522"
---
# <a name="configure-and-validate-exclusions-for-microsoft-defender-antivirus-scans"></a>Microsoft Defender Virüsten Koruma taramaları için dışlamaları yapılandırma ve doğrulama

**Şunlar için geçerlidir:**
- [Pertahanan Microsoft untuk Titik Akhir Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Bazı dosyaları, klasörleri, işlemleri ve işlem tarafından açılan dosyaları Microsoft Defender Virüsten Koruma taramaların dışında tutabilirsiniz. Bu tür dışlamalar [zamanlanmış taramalar](scheduled-catch-up-scans-microsoft-defender-antivirus.md), [isteğe bağlı taramalar](run-scan-microsoft-defender-antivirus.md) ve [her zaman açık gerçek zamanlı koruma ve izleme](configure-real-time-protection-microsoft-defender-antivirus.md) için geçerlidir. İşlemle açılan dosyalar için dışlamalar yalnızca gerçek zamanlı koruma için geçerlidir.

## <a name="configure-and-validate-exclusions"></a>Dışlamaları yapılandırın ve doğrulayın

Dışlamaları yapılandırmak ve doğrulamak için aşağıdakilere bakın:

- [Dosya adı, uzantı ve klasör konumu temelinde dışlamaları yapılandırın ve doğrulayın](configure-extension-file-exclusions-microsoft-defender-antivirus.md). Dosyaları, dosya uzantılarına, dosya adlarına veya konumlarına göre Microsoft Defender Virüsten Koruma taramalarının dışında tutabilirsiniz.

- [İşlemler tarafından açılan dosyalar için dışlamaları yapılandırın ve doğrulayın](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md). Dosyaları belirli bir işlem tarafından açılmış taramaların dışında tutabilirsiniz.

## <a name="recommendations-for-defining-exclusions"></a>Dışlamaları tanımlamak için Öneriler

> [!IMPORTANT]
> Microsoft Defender Virüsten Koruma, kuruluş yönetiminde, veritabanı yönetiminde ve diğer kurumsal senaryolarda ve durumlarda kullanılanlar gibi bilinen işletim sistemi davranışlarına ve tipik yönetim dosyalarına dayalı birçok otomatik dışlama içerir.
>
> Dışlamaların tanımlanması, Microsoft Defender Virüsten Koruma tarafından sunulan korumayı düşürür. Dışlamaları uygulamayla ilişkili riskleri her zaman değerlendirmeli ve yalnızca kötü amaçlı olmadığından emin olduğunuz dosyaları hariç tutmalısınız.

Dışlamaları tanımlarken aşağıdaki noktaları göz önünde bulundurun:

- Dışlamalar teknik olarak bir koruma açığıdır. Dışlamaları tanımlarken tüm seçeneklerinizi göz önünde bulundurun. Diğer seçenekler, dışlanan konumun uygun erişim denetimi listelerine (ACL' ler) sahip olduğundan emin olmak veya ilkeleri önce denetim moduna ayarlamak kadar basit olabilir.

- Dışlamaları düzenli aralıklarla gözden geçirin. Gözden geçirme işleminizin bir parçası olarak azaltmaları yeniden denetleyin ve yeniden uygulayın.

- İdeal olarak, proaktif olmak için dışlamaları tanımlamaktan kaçının. Örneğin, gelecekte bir sorun olabileceğini düşündüğünüz için bir şeyi dışlamayın. Dışlamaları yalnızca performansla ilgili sorunlar veya dışlamaların azaltabileceği uygulama uyumluluğu gibi belirli sorunlar için kullanın.

- Dışlama listenizdeki değişiklikleri gözden geçirin ve denetleyin. Güvenlik ekibiniz daha sonra karışıklığı önlemek için belirli bir dışlamanın neden eklendiğine ilişkin bağlamı korumalıdır. Güvenlik ekibiniz dışlamaların neden mevcut olduğuyla ilgili sorulara özel yanıtlar sağlayabilmelidir.

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [macOS'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender Virüsten Koruma macOS Virüsten Koruma ilkesi ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android'de Uç Nokta için Defender özelliklerini yapılandırma](android-configure.md)
> - [iOS özelliklerinde Pertahanan Microsoft untuk Titik Akhir yapılandırma](ios-configure-features.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Windows Server 2016 Microsoft Defender Virüsten Koruma dışlamaları](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Dışlamaları tanımlarken kaçınılması gereken yaygın hatalar](common-exclusion-mistakes-microsoft-defender-antivirus.md)
