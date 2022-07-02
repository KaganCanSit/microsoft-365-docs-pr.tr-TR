---
title: Uç Nokta için Microsoft Defender'da uyarıları gözden geçirme
description: Görselleştirilmiş bir uyarı hikayesi ve zincirin her adımına ilişkin ayrıntılar da dahil olmak üzere uyarı bilgilerini gözden geçirin.
keywords: olay, olaylar, makineler, cihazlar, kullanıcılar, uyarılar, uyarı, araştırma, grafik, kanıt
ms.prod: m365-security
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.date: 5/1/2020
ms.technology: mde
ms.openlocfilehash: 76503c180dfdd2314254efc9315235c0802ab7f8
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607553"
---
# <a name="review-alerts-in-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'da uyarıları gözden geçirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-managealerts-abovefoldlink)

Uç Nokta için Microsoft Defender'daki uyarı sayfası, ayrıntılı bir uyarı hikayesi oluşturmak için seçilen uyarıyla ilgili saldırı sinyallerini ve uyarıları birleştirerek uyarıya tam bağlam sağlar.

Kuruluşunuzu etkileyen uyarıları hızla önceliklendirme, araştırma ve etkin eylem gerçekleştirme. Bunların neden tetiklendiklerini ve bunların tek bir konumdan etkilerini anlayın. Bu genel bakış hakkında daha fazla bilgi edinin.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yiO5]

## <a name="getting-started-with-an-alert"></a>Uyarıyı kullanmaya başlama

Uç Nokta için Defender'da bir uyarının adını seçtiğinizde uyarı sayfası açılır. Uyarı sayfasında, tüm bilgiler seçilen uyarı bağlamında gösterilir. Her uyarı sayfası 4 bölümden oluşur:

1. **Uyarı başlığı** uyarının adını gösterir ve sayfada ne seçtiğinizden bağımsız olarak geçerli araştırmanızı başlatan uyarıyı anımsatmak için vardır.
2. [**Etkilenen varlıklar**](#review-affected-assets) , bu uyarıdan etkilenen cihazların ve kullanıcıların daha fazla bilgi ve eylem için tıklanabilir kartlarını listeler.
3. **Uyarı hikayesi**, uyarıyla ilgili tüm varlıkları bir ağaç görünümüyle birbirine bağlı olarak görüntüler. Seçtiğiniz uyarının sayfasına ilk kez girdiğinizde başlıktaki uyarı odaktaki uyarı olacaktır. Uyarı hikayesindeki varlıklar, ek bilgi sağlamak ve doğrudan uyarı sayfası bağlamında eylem gerçekleştirmenize olanak tanıyarak yanıtı hızlandırmak için genişletilebilir ve tıklanabilir. Araştırmanızı başlatmak için uyarı hikayesini kullanın. [Uç Nokta için Microsoft Defender'de uyarıları araştırma bölümünden](/microsoft-365/security/defender-endpoint/investigate-alerts) nasıl yapılacağını öğrenin.
4. **Ayrıntılar bölmesi** ilk başta seçili uyarının ayrıntılarını ve bu uyarıyla ilgili ayrıntıları ve eylemleri gösterir. Uyarı yazısında etkilenen varlıklardan veya varlıklardan herhangi birini seçerseniz, ayrıntılar bölmesi seçili nesne için bağlamsal bilgiler ve eylemler sağlayacak şekilde değişir.

Uyarınızın algılama durumunu not edin.

- Engellendi: Şüpheli eylem girişiminden kaçınıldı. Örneğin, bir dosya diske yazılmadı veya yürütülmedi.

  :::image type="content" source="images/detstat-prevented.png" alt-text="Bir tehdidin önlenmesini gösteren sayfa" lightbox="images/detstat-prevented.png":::

- Engellendi: Şüpheli davranış yürütüldü ve engellendi. Örneğin, bir işlem yürütüldü ancak daha sonra şüpheli davranışlar sergilediğinden işlem sonlandırıldı.

  :::image type="content" source="images/detstat-blocked.png" alt-text="Bir tehdidin engelini gösteren sayfa" lightbox="images/detstat-blocked.png":::

- Algılandı: Bir saldırı algılandı ve hala etkin olabilir.

  :::image type="content" source="images/detstat-detected.png" alt-text="Tehdit algılamayı gösteren sayfa" lightbox="images/detstat-detected.png":::

Daha sonra uyarınızın ayrıntılar bölmesinde otomatik *araştırma ayrıntılarını* gözden geçirerek hangi eylemlerin gerçekleştirildiğini görebilir ve önerilen eylemler için uyarının açıklamasını okuyabilirsiniz.

:::image type="content" source="images/alert-air-and-alert-description.png" alt-text="Uyarı açıklaması ve otomatik araştırma bölümlerinin vurgulandığı ayrıntılar bölmesi" lightbox="images/alert-air-and-alert-description.png":::

Uyarı açıldığında ayrıntılar bölmesinde bulunan diğer bilgiler MITRE tekniklerini, kaynağını ve ek bağlamsal ayrıntıları içerir.

> [!NOTE]
> *Desteklenmeyen uyarı türü* uyarı durumu görüyorsanız, bu otomatik araştırma özelliklerinin otomatik araştırma çalıştırmak için bu uyarıyı alamayacağı anlamına gelir. Ancak [, bu uyarıları el ile araştırabilirsiniz](../defender/investigate-incidents.md#alerts).

## <a name="review-affected-assets"></a>Etkilenen varlıkları gözden geçirme

Etkilenen varlıklar bölümlerinde bir cihaz veya kullanıcı kartı seçildiğinde, ayrıntılar bölmesinde cihazın veya kullanıcının ayrıntılarına geçilecektir.

- **Cihazlar için**, ayrıntılar bölmesinde cihazın kendisi hakkında Etki Alanı, İşletim Sistemi ve IP gibi bilgiler görüntülenir. Etkin uyarılar ve bu cihazdaki oturum açmış kullanıcılar da kullanılabilir. Cihazı yalıtarak, uygulama yürütmeyi kısıtlayarak veya virüsten koruma taraması çalıştırarak hemen işlem yapabilirsiniz. Alternatif olarak, bir araştırma paketi toplayabilir, otomatik araştırma başlatabilir veya cihazın bakış açısından araştırma yapmak için cihaz sayfasına gidebilirsiniz.

   :::image type="content" source="images/device-page-details.png" alt-text="Cihaz seçildiğinde ayrıntılar bölmesi" lightbox="images/device-page-details.png":::

- **Kullanıcılar için**, ayrıntılar bölmesinde kullanıcının SAM adı ve SID gibi ayrıntılı kullanıcı bilgilerinin yanı sıra bu kullanıcı tarafından gerçekleştirilen oturum açma türleri ve bununla ilgili uyarılar ve olaylar görüntülenir. Araştırmaya o kullanıcının bakış açısından devam etmek için *Kullanıcı sayfasını aç'ı* seçebilirsiniz.

   :::image type="content" source="images/user-page-details.png" alt-text="Kullanıcı seçildiğinde ayrıntılar bölmesi" lightbox="images/user-page-details.png":::

## <a name="related-topics"></a>İlgili konular

- [Olaylar sırasını görüntüleme ve düzenleme](view-incidents-queue.md)
- [Olayları araştırın](investigate-incidents.md)
- [Olayları yönetin](manage-incidents.md)
