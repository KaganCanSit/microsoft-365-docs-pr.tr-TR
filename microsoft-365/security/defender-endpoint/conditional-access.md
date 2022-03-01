---
title: Kullanıcıları, cihazları ve verileri daha iyi korumak için Koşullu Erişimi etkinleştirme
description: Bir cihaz risk altında kabul edilirse ve bir uygulamanın uyumlu olmayan olarak belirlensi durumlarının uygulamanın çalışmasını engellemek için Koşullu Erişimi etkinleştir.
keywords: koşullu erişim, uygulamaları engelleme, güvenlik düzeyi, intune,
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 8ee1b1542eb2e737da509ce12ad9c2a605a4ffa5
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2021
ms.locfileid: "62996998"
---
# <a name="enable-conditional-access-to-better-protect-users-devices-and-data"></a>Kullanıcıları, cihazları ve verileri daha iyi korumak için Koşullu Erişimi etkinleştirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-conditionalaccess-abovefoldlink)

Koşullu Erişim, yalnızca güvenli cihazların uygulamalara erişimi olduğundan emin olarak kullanıcılarınızı ve kuruluş bilgilerini daha iyi korumanıza yardımcı olan bir özelliktir.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4byD1]

Koşullu Erişim ile, cihazın risk düzeyine bağlı olarak kuruluş bilgilerine erişimi kontrol edebilirsiniz. Bu, güvenilen uygulamaları kullanarak güvenilen cihazlardaki güvenilen kullanıcıları tutmanıza yardımcı olur.

Cihazlar ve uygulamaların, bir cihaz uyumlu durumuna dönene kadar uygulamaların çalışır durumdan durmalarını durdurmak üzere ilkeleri zorlayarak, hangi cihaz ve uygulamaların ağdan bilgilere çalıştır bilgileri ağın içinde çalıştır bağlanağına ilişkin güvenlik koşulları tanımlayabilirsiniz.

Uç nokta için Defender'da Koşullu Erişim'in uygulanması, Microsoft Intune (Intune) cihaz uyumluluk ilkelerini ve Azure Active Directory (Azure AD) koşullu erişim ilkelerini temel alır.

Uyumluluk ilkesi, uygulamalara erişim için yalnızca bir veya daha fazla cihaz uyumluluk ilkesi kuralı sağlayan cihazlara izin vermek üzere Koşullu Erişim ile kullanılır.

## <a name="understand-the-conditional-access-flow"></a>Koşullu Erişim akışını anlama

Koşullu Erişim, tehdit bir cihazda görülene kadar hassas içeriğe erişimin tehdit düzeltilene kadar engellenir.

Akış, cihazların düşük, orta veya yüksek risklere sahip olduğu görülür şekilde başlar. Daha sonra bu risk belirlemeleri Intune'a gönderilir.

Intune'da ilkeleri nasıl yapılandırdınıza bağlı olarak, Koşullu Erişim belirli koşulların karşı uygulanması için ilkenin uygulanması için ayarlanır.

Örneğin, Intune'i yüksek riskli cihazlara Koşullu Erişim uygulayacak şekilde yapılandırabilirsiniz.

Intune'da, uygulamalara erişimi engellemek için Azure AD Koşullu Erişimi ile birlikte bir cihaz uyumluluk ilkesi kullanılır. Paralel olarak, otomatik bir araştırma ve düzeltme işlemi başlatıldı.

 Otomatik araştırma ve düzeltme devam ederken kullanıcı cihazı kullanmaya devam ediyor ancak tehdit tümüyle düzeltilene kadar kurumsal verilere erişim engellenmiş olur.

Bir cihazda bulunan riski çözmek için, cihazı uyumlu bir hale geri iadeniz gerekir. Üzerinde hiçbir risk görülen bir cihaz uyumlu durumuna döner.

Riskle ilgili üç yol vardır:

1. El ile veya otomatik düzeltmeyi kullanın.
2. Cihaz üzerinde etkin uyarıları giderin. Bu, riski cihazdan kaldırır.
3. Cihazı etkin ilkelerden kaldırabilirsiniz ve sonuç olarak, cihaza Koşullu Erişim uygulanmaz.

El ile düzeltme için bir secops yöneticisinin bir uyarıyı araştırması ve cihazda görülen riski düzeltmesi gerekir. Otomatik düzeltme, aşağıdaki Koşullu Erişimi Yapılandırma bölümünde sağlanan yapılandırma ayarları [aracılığıyla yapılandırılır](configure-conditional-access.md).

Risk el ile veya otomatik düzeltme yoluyla kaldırıldığı zaman, cihaz uyumlu bir hale döner ve uygulamalara erişim izni verir.

Aşağıdaki olay örneği dizisi Koşullu Erişim'i nasıl işle ilgili olarak açıklar:

1. Kullanıcı kötü amaçlı bir dosya açar ve Uç Nokta için Defender cihazı yüksek risk altında bayrakla gösterir.
2. Yüksek riskli değerlendirme Intune'a geçirildi. Paralel olarak, tanımlanan tehdide düzeltmek için otomatik bir araştırma başlatılır. El ile düzeltme, tanımlanan tehdide düzeltmek için de yapılabilir.
3. Intune'da oluşturulan ilkeye bağlı olarak, cihaz uyumlu değil olarak işaretlenir. Değerlendirme, Intune Koşullu Erişim ilkesi tarafından Azure AD'ye ilet iletildi. Azure AD'de, uygulamalara erişimi engellemek için ilgili ilke uygulanır.
4. El ile veya otomatik olarak inceleme ve düzeltme tamamlanır ve tehdit kaldırılır. Uç Nokta için Defender cihazda hiçbir risk olmadığını görür ve Intune cihazı uyumlu bir durumda değerlendiriyor. Azure AD, uygulamalara erişime izin veren ilkeyi uygular.
5. Kullanıcılar artık uygulamalara erişebilirsiniz.

## <a name="related-topic"></a>İlgili konu

- [Uç Nokta için Microsoft Defender'da Koşullu Erişimi Yapılandırma](configure-conditional-access.md)
