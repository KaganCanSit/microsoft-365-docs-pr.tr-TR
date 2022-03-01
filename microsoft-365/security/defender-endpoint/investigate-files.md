---
title: Uç nokta dosyaları için Microsoft Defender'ı araştırma
description: Uyarılar, davranışlar veya olaylarla ilişkilendirilmiş dosyalar hakkında ayrıntılı bilgi almak için araştırma seçeneklerini kullanın.
keywords: araştırma, araştırma, dosya, kötü amaçlı etkinlik, saldırı motivasyonu, derin çözümleme, derin çözümleme raporu
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: b990c73f9cdb81d164bd57d1aff5b7ec61df714f
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63012001"
---
# <a name="investigate-a-file-associated-with-a-microsoft-defender-for-endpoint-alert"></a>Uç nokta için Microsoft Defender uyarısıyla ilişkilendirilmiş dosyayı araştırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatefiles-abovefoldlink)

Belirli bir uyarı, davranış veya olayla ilişkilendirilmiş dosyanın ayrıntılarını araştırarak dosyanın kötü amaçlı etkinlikleri sergileyeni, saldırı motivasyonunu tanımlamaya ve ihlalin olası kapsamını an etmeye yardımcı olun.

Belirli bir dosyanın ayrıntılı profil sayfasına erişmenin birçok yolu vardır. Örneğin, arama özelliğini kullanabilir, Uyarı işlemi ağacı, Olay grafiği, Yapı zaman çizelgesi'nde bir bağlantıya tıklar veya Cihaz zaman çizelgesinde listelenen bir **olayı seçin**.

Ayrıntılı profil sayfasına başladıktan sonra, yeni Dosya sayfasını iki kez kapatarak yeni ve eski sayfa **düzenleri arasında geçiş edebilirsiniz**. Bu makalenin kalan kalanında daha yeni olan sayfa düzeni açıklanmıştır.

Dosya görünümünde aşağıdaki bölümlerden bilgi edinebilirsiniz:

- Dosya ayrıntıları, Kötü amaçlı yazılım algılama, Dosya yaygınlığı
- Derin çözümleme
- Uyarılar
- Kuruluşta gözlemlenen
- Derin çözümleme
- Dosya adları

Bu sayfadan da dosya üzerinde eyleme geçebilirsiniz.

## <a name="file-actions"></a>Dosya eylemleri

Profil sayfasının üst kısmında, dosya bilgi kartlarının üzerinde. Burada gerçekleştir işlemler şunlardır:

- Durdurma ve karantina
- Ekle/düzenle göstergesi
- Dosyayı indir
- Tehdit uzmanına danışın
- İşlem merkezi

Bu eylemler hakkında daha fazla bilgi için bkz [. Dosya üzerinde yanıt eylemi alma](respond-file-alerts.md).

## <a name="file-details-malware-detection-and-file-prevalence"></a>Dosya ayrıntıları, Kötü amaçlı yazılım algılama ve Dosya yaygınlığı

Dosya ayrıntıları, olay, kötü amaçlı yazılım algılama ve dosya yaygınlık kartları dosyayla ilgili çeşitli öznitelikleri görüntüler.

Dosyanın MD5'i, Virüs Toplamı algılama oranı ve varsa Microsoft Defender AV algılaması ve dosyanın yaygınlık bilgileri gibi ayrıntıları burada bulunmaktadır.

Yaygın dosya yaygınlık kartı, dosyanın kuruluşta ve dünya genelindeki cihazlarda nerede olduğunu gösterir.

> [!NOTE]
> Farklı kullanıcılar, dosya yaygınlık kartının Kuruluş *bölümündeki* cihazlar bölümünde farklı değerler görebilir. Bunun nedeni kartın, kullanıcının sahip olduğu RBAC kapsamına göre bilgileri görüntülemesidir. Başka bir ifadeyle, bir kullanıcıya belirli bir cihaz kümesi üzerinde görünürlük verildiyse, yalnızca bu cihazlarda kuruluş tarafından yaygın olarak bulunan dosyaları görebilirler.

![Dosya bilgileri görüntüsü.](images/atp-file-information.png)

## <a name="alerts"></a>Uyarılar

Uyarılar **sekmesi** dosyayla ilişkili uyarıların listesini sağlar. Bu liste Uyarılar kuyruğuyla aynı bilgilerin büyük bir listesini içerir; cihaz grubu (varsa) etkilenen cihaz ait olduğu dışında. Sütun başlıklarının üstündeki araç çubuğundan Sütunları **özelleştir'i** seçerek ne tür bilgilerin göster birini seçebilirsiniz.

![Dosya bölümüyle ilgili uyarıların resmi.](images/atp-alerts-related-to-file.png)

## <a name="observed-in-organization"></a>Kuruluşta gözlemlenen

**Kuruluşta gözlemlenen sekmesi**, dosyayla birlikte hangi cihazların gözlemlenmiş olduğunu görmek için bir tarih aralığı belirtmenize olanak tanır.

> [!NOTE]
> Bu sekmede en fazla 100 cihaz görüntülenir. Dosyanın _bulunduğu_ tüm cihazları görmek için, sekmenin sütun başlıklarını yukarıdaki eylem menüsünden Dışarı Aktar'ı seçerek sekmeyi CSV dosyasına aktarın.

![Dosyayla birlikte en son gözlemlenen cihazın görüntüsü.](images/atp-observed-machines.png)

Dosyayı içeren olayları denetlemesini istediğiniz bir zaman aralığını hızla belirtmek için kaydırıcıyı veya aralık seçiciyi kullanın. Bir zaman penceresini tek bir gün kadar küçük olarak belirtebilirsiniz. Bu, gereksiz kaydırmayı ve aramayı azaltarak, yalnızca o anda bu IP Adresiyle iletişim geçen dosyaları görmene olanak sağlar.

## <a name="deep-analysis"></a>Derin çözümleme

Derin **çözümleme sekmesi**, hem dosyanın [](respond-file-alerts.md#deep-analysis)davranışı hem de kuruluşlarınız içindeki etkisi hakkında daha fazla ayrıntı ortaya çıkarmak için ayrıntılı çözümleme yapmak için dosyayı göndermenizi sağlar. Dosyayı gönderdikten sonra, sonuçlar elde edildikten sonra bu sekmede derin çözümleme raporu görüntülenir. Derin çözümleme hiçbir şey bulamazsa, rapor boş olur ve sonuç alanı boş kalır.

![Derin çözümleme sekmesinin resmi.](images/submit-file.png)

## <a name="file-names"></a>Dosya adları

Dosya **adları** sekmesi, kuruluş içinde dosyanın kullanımı için gözlemlenen tüm adları listeler.

![Dosya adları sekmesinin resmi.](images/atp-file-names.png)

## <a name="related-topics"></a>İlgili konular

- [Uç nokta kuyruğu için Microsoft Defender'ı görüntüleme ve düzenleme](alerts-queue.md)
- [Uç nokta uyarıları için Microsoft Defender'ı yönetme](manage-alerts.md)
- [Uç nokta uyarıları için Microsoft Defender'ı araştırma](investigate-alerts.md)
- [Uç Nokta Cihazları için Microsoft Defender listesinde cihazları araştırma](investigate-machines.md)
- [Uç nokta için Microsoft Defender uyarısıyla ilişkilendirilmiş IP adresini araştırma](investigate-ip.md)
- [Uç nokta için Microsoft Defender uyarısıyla ilişkilendirilmiş etki alanını araştırma](investigate-domain.md)
- [Uç Nokta için Microsoft Defender'da kullanıcı hesabını araştırma](investigate-user.md)
- [Dosyada yanıt eylemleri gerçekleştirin](respond-file-alerts.md)
