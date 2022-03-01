---
title: Uç Nokta için Microsoft Defender'da uyarıları gözden geçirme
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
ms.openlocfilehash: a156b2a4514c3dfa090bcf43285abfbcfaa1f46e
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011993"
---
# <a name="review-alerts-in-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'da uyarıları gözden geçirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-managealerts-abovefoldlink)

Ayrıntılı bir uyarı hikayesini oluşturmak üzere seçili uyarıyla ilgili saldırı sinyallerini ve uyarıları birleştirerek, Uç Nokta için Microsoft Defender'daki uyarı sayfası uyarıya tam bağlam sağlar.

Hızlı bir şekilde inceleme, inceleme ve kurumlarınızı etkileyen uyarılar üzerinde etkili bir işlem. Neden tetiklenen olduğunu ve tek konumdan etkilenmelerini anlıyoruz. Daha fazla bilgi edinmek için bu genel bakış'a bakın.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4yiO5]

## <a name="getting-started-with-an-alert"></a>Uyarıyla çalışmaya başlama

Uç nokta için Defender'da bir uyarının adını seçmek sizi uyarı sayfasına ayacaktır. Uyarı sayfasında, tüm bilgiler seçili uyarı bağlamında gösterilir. Her uyarı sayfası 4 bölümden oluşur:

1. **Uyarı başlığı uyarının** adını gösterir ve sayfada ne seçtiğinize bakılmaksızın geçerli araştırmanızı başlatan uyarıyı anımsatmaya yardımcı olur.
2. [**Etkilenen varlıklar**](#review-affected-assets) , bu uyarıdan etkilenen cihaz ve kullanıcıların kartlarını listeler. Bu uyarıdan etkilenen kullanıcılar, daha fazla bilgi ve eylem için tıklanabilir.
3. Uyarı **anlatısı** , uyarıyla ilgili tüm varlıkları bir ağaç görünümüyle bağlantılı olarak görüntüler. Seçili uyarının sayfasına ilk kez geldiğinde başlıkta uyarı odak noktası olur. Uyarı hikayesinde yer alan varlıklar, ek bilgi sağlamak ve uyarı sayfasının sağ bağlamı içinde işlemnizi hızlandırmak için genişletilebilir ve tıklanabilir durumda olur. Araştırmanızı başlatmak için uyarı hikayenizi kullanın. Nasıl olduğunu öğrenmek için [Microsoft Defender for Endpoint uyarılarını araştırma.](/microsoft-365/security/defender-endpoint/investigate-alerts)
4. Ayrıntılar **bölmesi,** ilk başta seçili uyarının ayrıntılarını ve bu uyarıyla ilgili ayrıntıları ve eylemleri gösterir. Uyarı hikayesinde etkilenen varlıklardan veya varlıklardan herhangi birini seçtiysanız, ayrıntılar bölmesi seçili nesne için bağlamsal bilgi ve eylemler sağlamak üzere değişir.

Uyarınız için algılama durumunu notun.

- Önlenir: Şüpheli eylem denendi. Örneğin, bir dosya diske yazmdı veya yürütülm yoktu.

  ![Tehdityi gösteren bir uyarı sayfası engelildi.](images/detstat-prevented.png)

- Engellendi: Şüpheli davranış yürütülür ve ardından engellenir. Örneğin, bir işlem yürütülür, ancak bundan sonra şüpheli davranışlar sergilesin diye işlem sonlandırıldı.

  ![Tehdidin engellenmiş olduğunu gösteren bir uyarı sayfası.](images/detstat-blocked.png)

- Algılandı: Bir saldırı algılandı ve hala etkin.

  ![Tehdit algılandı gösteren bir uyarı sayfası.](images/detstat-detected.png)

Daha sonra, uyarı ayrıntıları bölmesinde  otomatik soruşturma ayrıntılarını gözden geçirebilirsiniz; ayrıca hangi eylemlerin zaten gerçekleştir olduğunu görebilir ve önerilen eylemler için uyarı açıklamasını da inceleyebilirsiniz.

![Uyarı açıklamasının ve otomatik soruşturma bölümlerinin vurgulu olduğu ayrıntılar bölmesinden bir parçacık.](images/alert-air-and-alert-description.png)

Uyarı açıldığında ayrıntılar bölmesinde mevcut olan diğer bilgiler MİTRE tekniklerini, kaynağı ve ek bağlamsal ayrıntıları içerir.

## <a name="review-affected-assets"></a>Etkilenen varlıkları gözden geçirme

Etkilenen varlıklar bölümlerinde bir cihaz veya kullanıcı kartı seçerek ayrıntılar bölmesinde cihazın veya kullanıcının ayrıntılarına geçebilirsiniz.

- **Cihazlar için** ayrıntılar bölmesinde, cihazla ilgili Etki Alanı, İşletim Sistemi ve IP gibi bilgiler görüntülenir. Bu cihazda etkin uyarılar ve oturum açan kullanıcılar da kullanılabilir. Cihazı çıkararak, uygulama yürütmeyi kısıtarak veya virüsten koruma taraması çalıştırarak hemen harekete geçebilirsiniz. Alternatif olarak, bir araştırma paketi toplayabilirsiniz, otomatik bir araştırma başlatabilirsiniz veya cihazın görünüm noktasından araştırma yapmak için cihaz sayfasına gidebilirsiniz.

   ![Cihaz seçiliyken ayrıntılar bölmesiyle ilgili bir parçacık.](images/device-page-details.png)

- **Kullanıcılar için**, ayrıntılar bölmesinde kullanıcının SAM adı ve SID gibi ayrıntılı kullanıcı bilgileri ile bu kullanıcı tarafından gerçekleştirilen oturum açma türleri ve bu kullanıcıyla ilgili tüm uyarılar ve olaylar görüntülenir. Bu kullanıcının *bakış açısından incelemeye* devam etmek için Kullanıcı sayfasını aç'ı seçin.

   ![Kullanıcı seçildiğinde ayrıntılar bölmesinin küçük bir parçası.](images/user-page-details.png)

## <a name="related-topics"></a>İlgili konular

- [Olayları görüntüleme ve düzenleme](view-incidents-queue.md)
- [Olayları araştırma](investigate-incidents.md)
- [Olayları yönetme](manage-incidents.md)
