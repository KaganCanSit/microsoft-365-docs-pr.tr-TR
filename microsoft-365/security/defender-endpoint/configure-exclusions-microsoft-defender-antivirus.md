---
title: Taramalar için özel Microsoft Defender Virüsten Koruma ayarlama
description: Dosyaları (belirtilen süreçler tarafından değiştirilen dosyalar dahil) ve klasörlerin bu dosyalar tarafından taranmalarını Microsoft Defender Virüsten Koruma. PowerShell ile dışlamalarınızı doğrulama.
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
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 5a26951535b6e2197d8ada45b2108e62f15fda03
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010012"
---
# <a name="configure-and-validate-exclusions-for-microsoft-defender-antivirus-scans"></a>Taramalar için dışlamaları yapılandırma Microsoft Defender Virüsten Koruma doğrulama

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)


Belirli dosyaları, klasörleri, süreçleri ve süreç açılan dosyaları taramaların dışında Microsoft Defender Virüsten Koruma tutabilirsiniz. Bu tür dışlamalar [zamanlanmış taramalar](scheduled-catch-up-scans-microsoft-defender-antivirus.md), [isteğe](run-scan-microsoft-defender-antivirus.md) bağlı taramalar ve [her zaman gerçek zamanlı koruma ve izleme için geçerlidir](configure-real-time-protection-microsoft-defender-antivirus.md). süreç açılan dosyalar için dışlamalar yalnızca gerçek zamanlı koruma için geçerlidir.

## <a name="configure-and-validate-exclusions"></a>Dışlamaları yapılandırma ve doğrulama

Dışlamaları yapılandırmak ve doğrulamak için aşağıdakilere bakın:

- [Dosya adı, uzantı ve klasör konumu temel alarak dışlamaları yapılandırır ve doğrular](configure-extension-file-exclusions-microsoft-defender-antivirus.md). Dosyaları, dosya uzantısına, Microsoft Defender Virüsten Koruma veya konumlarına göre taramalar dışında tutabilirsiniz.

- [İşlemler tarafından açılan dosyalar için dışlamaları yapılandırma ve doğrulama](configure-process-opened-file-exclusions-microsoft-defender-antivirus.md). Belirli bir işlem tarafından açılmış olan dosyaları taramaların dışında tutabilirsiniz.

## <a name="recommendations-for-defining-exclusions"></a>Öneriler tanımlama hakkında daha fazla bilgi

> [!IMPORTANT]
> Microsoft Defender Virüsten Koruma, bilinen işletim sistemi davranışlarına ve kurumsal yönetim, veritabanı yönetimi ve diğer kurumsal senaryo ve durumlarda kullanılanlar gibi tipik yönetim dosyalarına dayalı birçok otomatik dışlama içerir.
>
> Dışlamaları tanımlamak, kullanıcı tarafından sunulan korumayı Microsoft Defender Virüsten Koruma. Dışlamaları uygulamayla ilişkili riskleri her zaman değerlendirmeli ve yalnızca kötü amaçlı olmadığınız dosyaları hariç tutabilirsiniz.

Dışlama tanımlarken aşağıdaki noktaları unutmayın:

- Dışlamalar teknik olarak bir koruma aralığıdır. Dışlama tanımlarken tüm seçeneklerinizi göz önünde bulundurabilirsiniz. Diğer seçenekler, dışarıda bırakılan konumun uygun erişim denetimi listelerine (ACL) sahip olduğundan emin olmak veya başta denetim moduna ilkeler ayarlamak kadar basit olabilir.

- Dışlamaları düzenli aralıklarla gözden geçirme. gözden geçirme işleminizin bir parçası olarak risk azaltmaları yeniden kontrol etmek ve yeniden zorunlu kılın.

- İdeal olan, proaktif olmak için dışlamaları tanımlamaktan kaçının. Örneğin, bir şeyi, gelecekte bir sorun olabileceğini düşünme nedeniyle hariç tutmakn. Dışlamaların azaltmakta olduğu performans veya uygulama uyumluluğuyla ilgili sorunlar gibi, yalnızca belirli sorunlar için dışlamaları kullanın.

- Dışlamalar listenizin değişikliklerini gözden geçirme ve denetleme. Güvenlik ekibinin sonradan karışıklıkları önlemek için belirli bir dışlamanın neden ekli olduğuyla ilgili bağlamı koruması gerekir. Güvenlik ekibinin, dışlamaların neden var olduğuyla ilgili sorulara belirli yanıtlar sağlaymabilecektir.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft Defender Virüsten Koruma dışlamaları Windows Server 2016](configure-server-exclusions-microsoft-defender-antivirus.md)
- [Dışlamaları tanımlarken kaçınılması gereken yaygın hatalar](common-exclusion-mistakes-microsoft-defender-antivirus.md)
