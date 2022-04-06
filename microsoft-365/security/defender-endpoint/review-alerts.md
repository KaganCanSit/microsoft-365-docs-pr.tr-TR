---
title: E-postada uyarıları Uç Nokta için Microsoft Defender
description: Zincirin her adımı için görselleştirilmiş uyarı hikayesini ve ayrıntıları da içeren uyarı bilgilerini gözden geçirebilirsiniz.
keywords: olay, olaylar, makineler, cihazlar, kullanıcılar, uyarılar, uyarı, soruşturma, grafik, kanıt
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
ms.openlocfilehash: 91cd06188a8337f3d0df0b9c67d7c98e389e4351
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64466780"
---
# <a name="review-alerts-in-microsoft-defender-for-endpoint"></a>E-postada uyarıları Uç Nokta için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-managealerts-abovefoldlink)

Uç Nokta için Microsoft Defender uyarı sayfası, seçili uyarıyla ilgili saldırı sinyallerini ve uyarıları birleştirerek ayrıntılı bir uyarı anlatısı oluşturmak üzere uyarıya tam bağlam sağlar.

Hızlı bir şekilde inceleme, inceleme ve kurumlarınızı etkileyen uyarılar üzerinde etkili bir işlem. Neden tetiklenen olduğunu ve tek konumdan etkilenmelerini anlıyoruz. Daha fazla bilgi edinmek için bu genel bakış'a bakın.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yiO5]

## <a name="getting-started-with-an-alert"></a>Uyarıyla çalışmaya başlama

Uç nokta için Defender'da bir uyarının adını seçmek sizi uyarı sayfasına ayacaktır. Uyarı sayfasında, tüm bilgiler seçili uyarı bağlamında gösterilir. Her uyarı sayfası 4 bölümden oluşur:

1. **Uyarı başlığı uyarının** adını gösterir ve sayfada ne seçtiğinize bakılmaksızın geçerli araştırmanızı başlatan uyarıyı anımsatmaya yardımcı olur.
2. [**Etkilenen varlıklar**](#review-affected-assets) , bu uyarıdan etkilenen cihaz ve kullanıcıların kartlarını listeler. Bu uyarıdan etkilenen kullanıcılar, daha fazla bilgi ve eylem için tıklanabilir.
3. Uyarı **anlatısı** , uyarıyla ilgili tüm varlıkları bir ağaç görünümüyle bağlantılı olarak görüntüler. Seçili uyarının sayfasına ilk kez geldiğinde başlıkta uyarı odak noktası olur. Uyarı hikayesinde yer alan varlıklar, ek bilgi sağlamak ve uyarı sayfasının sağ bağlamı içinde işlemnizi hızlandırmak için genişletilebilir ve tıklanabilir durumda olur. Araştırmanızı başlatmak için uyarı hikayenizi kullanın. [Uç Nokta için Microsoft Defender'de uyarıları araştırma Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/investigate-alerts).
4. Ayrıntılar **bölmesi,** ilk başta seçili uyarının ayrıntılarını ve bu uyarıyla ilgili ayrıntıları ve eylemleri gösterir. Uyarı hikayesinde etkilenen varlıklardan veya varlıklardan herhangi birini seçtiysanız, ayrıntılar bölmesi seçili nesne için bağlamsal bilgi ve eylemler sağlamak üzere değişir.

Uyarınız için algılama durumunu notun.

- Önlenir: Şüpheli eylem denendi. Örneğin, bir dosya diske yazmdı veya yürütülm yoktu.

  :::image type="content" source="images/detstat-prevented.png" alt-text="Bir tehdit önlemeyi gösteren sayfa" lightbox="images/detstat-prevented.png":::

- Engellendi: Şüpheli davranış yürütülür ve ardından engellenir. Örneğin, bir işlem yürütülür, ancak bundan sonra şüpheli davranışlar sergilesin diye işlem sonlandırıldı.

  :::image type="content" source="images/detstat-blocked.png" alt-text="Bir tehdidin engellenmiş olduğunu gösteren sayfa" lightbox="images/detstat-blocked.png":::

- Algılandı: Bir saldırı algılandı ve hala etkin.

  :::image type="content" source="images/detstat-detected.png" alt-text="Bir tehdit algılamayı gösteren sayfa" lightbox="images/detstat-detected.png":::

Daha sonra, uyarı ayrıntıları bölmesinde  otomatik soruşturma ayrıntılarını gözden geçirebilirsiniz; ayrıca hangi eylemlerin zaten gerçekleştir olduğunu görebilir ve önerilen eylemler için uyarı açıklamasını da inceleyebilirsiniz.

:::image type="content" source="images/alert-air-and-alert-description.png" alt-text="Uyarı açıklamasının ve otomatik soruşturma bölümlerinin vurgulu olduğu ayrıntılar bölmesi" lightbox="images/alert-air-and-alert-description.png":::

Uyarı açıldığında ayrıntılar bölmesinde mevcut olan diğer bilgiler MİTRE tekniklerini, kaynağı ve ek bağlamsal ayrıntıları içerir.

## <a name="review-affected-assets"></a>Etkilenen varlıkları gözden geçirme

Etkilenen varlıklar bölümlerinde bir cihaz veya kullanıcı kartı seçerek ayrıntılar bölmesinde cihazın veya kullanıcının ayrıntılarına geçebilirsiniz.

- **Cihazlar için** ayrıntılar bölmesinde, cihazla ilgili Etki Alanı, İşletim Sistemi ve IP gibi bilgiler görüntülenir. Bu cihazda etkin uyarılar ve oturum açan kullanıcılar da kullanılabilir. Cihazı çıkararak, uygulama yürütmeyi kısıtarak veya virüsten koruma taraması çalıştırarak hemen harekete geçebilirsiniz. Alternatif olarak, bir araştırma paketi toplayabilirsiniz, otomatik bir araştırma başlatabilirsiniz veya cihazın görünüm noktasından araştırma yapmak için cihaz sayfasına gidebilirsiniz.

   :::image type="content" source="images/device-page-details.png" alt-text="Cihaz seçiliyken ayrıntılar bölmesi" lightbox="images/device-page-details.png":::

- **Kullanıcılar için**, ayrıntılar bölmesinde kullanıcının SAM adı ve SID gibi ayrıntılı kullanıcı bilgileri ile bu kullanıcı tarafından gerçekleştirilen oturum açma türleri ve bu kullanıcıyla ilgili tüm uyarılar ve olaylar görüntülenir. Bu kullanıcının *bakış açısından incelemeye* devam etmek için Kullanıcı sayfasını aç'ı seçin.

   :::image type="content" source="images/user-page-details.png" alt-text="Bir kullanıcı seçildiğinde ayrıntılar bölmesi" lightbox="images/user-page-details.png":::

## <a name="related-topics"></a>İlgili konular

- [Olayları görüntüleme ve düzenleme](view-incidents-queue.md)
- [Olayları araştırın](investigate-incidents.md)
- [Olayları yönetin](manage-incidents.md)
