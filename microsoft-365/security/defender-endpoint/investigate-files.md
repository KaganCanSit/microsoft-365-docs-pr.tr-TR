---
title: Uç Nokta için Microsoft Defender dosyalarını araştırma
description: Uyarılar, davranışlar veya olaylarla ilişkili dosyaların ayrıntılarını almak için araştırma seçeneklerini kullanın.
keywords: araştırma, araştırma, dosya, kötü amaçlı etkinlik, saldırı motivasyonu, derin analiz, derin analiz raporu
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: c1f6fa058715f831b1c8ba594bf1604ad92e9ed2
ms.sourcegitcommit: 6c2ab5e8efe74d0dc2df610e2d9d2fdda8aaf074
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/25/2022
ms.locfileid: "65669374"
---
# <a name="investigate-a-file-associated-with-a-microsoft-defender-for-endpoint-alert"></a>Uç Nokta için Microsoft Defender uyarısıyla ilişkili bir dosyayı araştırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatefiles-abovefoldlink)

Dosyanın kötü amaçlı etkinlikler sergileyip sergilemediğini saptamaya yardımcı olmak, saldırı motivasyonunu belirlemek ve ihlalin olası kapsamını anlamak için belirli bir uyarı, davranış veya olayla ilişkili bir dosyanın ayrıntılarını araştırın.

Belirli bir dosyanın ayrıntılı profil sayfasına erişmenin birçok yolu vardır. Örneğin, arama özelliğini kullanabilir, **Uyarı işlem ağacından**, **Olay grafiğinden**, **Yapıt zaman çizelgesinden** bir bağlantıya tıklayabilir veya **Cihaz zaman çizelgesinde** listelenen bir olayı seçebilirsiniz.

Ayrıntılı profil sayfasına geçtikten sonra, yeni **Dosya sayfasını** değiştirerek yeni ve eski sayfa düzenleri arasında geçiş yapabilirsiniz. Bu makalenin geri kalanında daha yeni sayfa düzeni açıklanmaktadır.

Dosya görünümünde aşağıdaki bölümlerden bilgi alabilirsiniz:

- Dosya ayrıntıları, Kötü amaçlı yazılım algılama, Dosya yaygınlığı
- DOSYA PE meta verileri (varsa)
- Derinanaliz
- Uyarılar
- Kuruluşta gözlemlenen
- Derinanaliz
- Dosya adları

Bu sayfadan bir dosya üzerinde de işlem yapabilirsiniz.

## <a name="file-actions"></a>Dosya eylemleri

Profil sayfasının üst kısmında, dosya bilgileri kartlarının üzerinde. Burada gerçekleştirebileceğiniz eylemler şunlardır:

- Durdurma ve karantinaya al
- Gösterge ekle/düzenle
- Dosyayı indirme
- Tehdit uzmanına danışın
- İşlem merkezi

Bu eylemler hakkında daha fazla bilgi için bkz. [Dosyada yanıt eylemi gerçekleştirme](respond-file-alerts.md).

## <a name="file-details-malware-detection-and-file-prevalence"></a>Dosya ayrıntıları, Kötü amaçlı yazılım algılama ve Dosya yaygınlığı

Dosya ayrıntıları, olay, kötü amaçlı yazılım algılama ve dosya yaygınlık kartları dosyayla ilgili çeşitli öznitelikleri görüntüler.

Dosyanın MD5'i, Virüs Toplam algılama oranı, varsa Microsoft Defender AV algılaması ve dosyanın yaygınlığı gibi ayrıntıları görürsünüz.

Dosya yaygınlığı kartı, dosyanın kuruluştaki ve dünya çapındaki cihazlarda nerede görüldüğünü gösterir. Dosyanın görüldüğü ilk ve son cihazlara kolayca özetleyebilir ve araştırmaya cihaz zaman çizelgesinde devam edebilirsiniz. 

> [!NOTE]
> Farklı kullanıcılar, dosya yaygınlığı kartının *kuruluştaki cihazlarda* farklı değerler görebilir. Bunun nedeni kartın, kullanıcının sahip olduğu RBAC kapsamına göre bilgileri görüntülemesidir. Başka bir deyişle, bir kullanıcıya belirli bir cihaz kümesinde görünürlük verildiyse, bu cihazlarda yalnızca dosya kurumsal yaygınlığını görür.

:::image type="content" source="images/atp-file-information.png" alt-text="Dosya bilgileri" lightbox="images/atp-file-information.png":::

## <a name="alerts"></a>Uyarılar

**Uyarılar** sekmesi, dosyayla ilişkilendirilmiş uyarıların listesini ve uyarının bağlı olduğu olayı sağlar. Bu liste, etkilenen cihazın ait olduğu cihaz grubu dışında Uyarılar kuyruğuyla aynı bilgilerin çoğunu kapsar. Sütun üst bilgilerinin üstündeki araç çubuğunda Sütunları **özelleştir'i** seçerek ne tür bilgilerin gösterileceğini seçebilirsiniz.

:::image type="content" source="images/atp-alerts-related-to-file.png" alt-text="Dosya bölümüyle ilgili uyarılar" lightbox="images/atp-alerts-related-to-file.png":::

## <a name="observed-in-organization"></a>Kuruluşta gözlemlenen

**Kuruluşta gözlemlenen** sekmesi, dosyayla hangi cihazların gözlemlendiğini görmek için bir tarih aralığı belirtmenize olanak tanır.

> [!NOTE]
> Bu sekmede en fazla 100 cihaz gösterilir. Dosyaya sahip _tüm_ cihazları görmek için, sekmenin sütun üst bilgilerinin üstündeki eylem menüsünden **Dışarı Aktar'ı** seçerek sekmeyi CSV dosyasına aktarın.

:::image type="content" source="images/atp-observed-machines.png" alt-text="Dosyayla birlikte en son gözlemlenen cihazlar" lightbox="images/atp-observed-machines.png":::

Dosyayla ilgili olayları denetlemek istediğiniz zaman aralığını hızla belirtmek için kaydırıcıyı veya aralık seçiciyi kullanın. Aralıktaki uyarılar göstergesiyle yardım alabilirsiniz. Tek bir gün kadar küçük bir zaman penceresi belirtebilirsiniz. Bu, yalnızca o anda bu IP Adresi ile iletişim kuran dosyaları görmenize olanak tanıyarak gereksiz kaydırma ve aramayı önemli ölçüde azaltır.

## <a name="deep-analysis"></a>Derinanaliz

**Derin analiz** sekmesi, dosyanın davranışı ve kuruluşunuzdaki etkisi hakkında daha fazla ayrıntıyı ortaya çıkarmak [için dosyayı ayrıntılı analiz için göndermenize](respond-file-alerts.md#deep-analysis) olanak tanır. Dosyayı gönderdikten sonra, sonuçlar kullanılabilir olduğunda ayrıntılı analiz raporu bu sekmede görünür. Derin analiz hiçbir şey bulamadıysa rapor boş kalır ve sonuç alanı boş kalır.

:::image type="content" source="images/submit-file.png" alt-text="Derin analiz sekmesi" lightbox="images/submit-file.png":::

## <a name="file-names"></a>Dosya adları

**Dosya adları** sekmesi, kuruluşunuzda dosyanın kullanıldığı gözlemlenen tüm adları listeler.

:::image type="content" source="images/atp-file-names.png" alt-text="Dosya adları sekmesi" lightbox="images/atp-file-names.png":::

## <a name="action-center"></a>İşlem merkezi

**İşlem merkezi**, bekleyen eylemleri ve dosyada gerçekleştirilen eylemlerin geçmişini görebilmeniz için işlem merkezini belirli bir dosyada filtrelenmiş olarak görüntüler.

## <a name="related-topics"></a>İlgili konular

- [Uç Nokta için Microsoft Defender kuyruğu görüntüleme ve düzenleme](alerts-queue.md)
- [Uç Nokta için Microsoft Defender uyarılarını yönetme](manage-alerts.md)
- [Uç Nokta için Microsoft Defender uyarılarını araştırma](investigate-alerts.md)
- [Uç Nokta için Microsoft Defender Cihazlar listesindeki cihazları araştırma](investigate-machines.md)
- [Uç Nokta için Microsoft Defender uyarısıyla ilişkili IP adresini araştırma](investigate-ip.md)
- [Uç Nokta için Microsoft Defender uyarısıyla ilişkili bir etki alanını araştırma](investigate-domain.md)
- [Uç Nokta için Microsoft Defender'de kullanıcı hesabını araştırma](investigate-user.md)
- [Dosyada yanıt eylemleri gerçekleştirin](respond-file-alerts.md)
