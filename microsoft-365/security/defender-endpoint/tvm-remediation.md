---
title: Güvenlik açıklarını düzeltmek Tehdit ve Güvenlik Açığı Yönetimi
description: Güvenlik önerileriyle bulunan güvenlik zayıflarını düzeltmek ve gerekirse, güvenlik önerilerini kullanarak özel durumlar Tehdit ve Güvenlik Açığı Yönetimi.
keywords: Uç nokta tvm düzeltmesi için Microsoft Defender, Uç nokta tvm için Microsoft Defender, Tehdit ve Güvenlik Açığı Yönetimi, tehdit & güvenlik açığı yönetimi, tehdit & güvenlik açığı yönetimi düzeltme, tvm düzeltme intune, tvm düzeltme sccm
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: c4f00e28e4dfa1c7806167c789a869be70c6fb78
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998055"
---
# <a name="remediate-vulnerabilities-with-threat-and-vulnerability-management"></a>Güvenlik açıklarını düzeltmek Tehdit ve Güvenlik Açığı Yönetimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Tehdit ve güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

## <a name="request-remediation"></a>Düzeltme isteği

Uç Tehdit ve Güvenlik Açığı Yönetimi için Microsoft Defender'daki düzeltme özelliği, düzeltme isteği iş akışı aracılığıyla Güvenlik ve IT yöneticileri arasındaki boşluğu köprüler. Sizin gibi güvenlik yöneticileri, Güvenlik önerisi sayfalarından Intune'a kadar olan bir güvenlik açığını **düzeltmek için IT** Yöneticisinden talepte bulunabilirsiniz.

### <a name="enable-microsoft-intune-connection"></a>Microsoft Intune bağlantısını etkinleştirme

Bu özelliği kullanmak için iş bağlantılarınızı Microsoft Intune etkinleştirin. Gelişmiş Microsoft 365 Defender Genel Gelişmiş **özellikler'Ayarlar** \> **gidin**\>. Ekranı aşağı kaydırın ve bağlantı **Microsoft Intune bakın**. Varsayılan olarak, iki durumlu düğme kapalıdır. Microsoft Intune **iki durumlu** düğmeyi **Açık olarak seçin**.

**Not**: Intune bağlantısı etkinleştirilmişse, düzeltme isteği oluştururken Intune güvenlik görevi oluşturma seçeneğiniz olur. Bağlantı ayarlanmazsa bu seçenek görünmez.

Ayrıntılar [için bkz. Uç Nokta için Microsoft Defender tarafından tanımlanan güvenlik açıklarını düzeltmek için Intune'u](/intune/atp-manage-vulnerabilities) kullanma.

### <a name="remediation-request-steps"></a>Düzeltme isteği adımları

1. Microsoft 365 Defender portalında tehdit ve  Güvenlik açığı yönetimi gezinti menüsüne gidin ve Güvenlik **önerileri'Öneriler** [**seçin**](tvm-security-recommendation.md).

2. Düzeltme isteğide kullanmak istediğiniz güvenlik önerilerini seçin ve sonra da Düzeltme **seçenekleri'ne tıklayın**.

3. Düzeltme isteğiniz, uygun cihaz grupları, öncelik, son tarih ve isteğe bağlı notlar da içinde olmak üzere formu doldurun.
    1. "Dikkat gerekiyor" düzeltme seçeneğini tercih ediyorsanız, belirli bir eylem olduğu için son tarih seçmeniz kullanılamaz.

4. İsteği **gönder'i seçin**. Bir düzeltme isteği gönderilen düzeltme etkinliği öğesi Tehdit ve Güvenlik Açığı Yönetimi içinde bir düzeltme etkinliği öğesi oluşturur ve bu önerinin düzeltme ilerlemesini izlemek için kullanılabilir. Bu, bir düzeltmeyi tetiklemez veya cihazlara herhangi bir değişiklik uygulamaz.

5. Yeni isteği IT Yöneticinize bilgilendirin ve isteği onaylaması veya reddetmesi ve paket dağıtımını başlatması için Intune'da oturum açmasını sunayın.

6. Düzeltme [**isteğinizin durumunu**](tvm-remediation.md) görüntülemek için Düzeltme sayfasına gidin.

Biletin Intune'da nasıl gösterip göstermesini kontrol etmek istemiyorsanız, ayrıntılar için bkz. Uç Nokta için Microsoft Defender tarafından tanımlanan güvenlik açıklarını düzeltmek için [Intune'u](/intune/atp-manage-vulnerabilities) kullanma.

> [!NOTE]
> İsteğiniz 10.000'den fazla cihazı düzeltmeyle ilgili olursa Intune'a düzeltme için yalnızca 10.000 cihaz gönderebiliriz.

Organizasyon un siber güvenlik güvenlik güveni zayıflığı tanımlandıktan ve eyleme edilebilir güvenlik önerilerine eş olduktan [sonra, güvenlik](tvm-security-recommendation.md) görevleri oluşturmaya başlama. Düzeltme biletlerinin oluşturulmuş olduğu Microsoft Intune ve tümleştirme yoluyla görevler oluşturabilirsiniz.

Güvenlik önerilerini düzelterek, güvenlik açıklarından daha düşük güvenlik açıkları ve güvenlik yapılandırmanızı artırma.

## <a name="view-your-remediation-activities"></a>Düzeltme etkinliklerinizi görüntüleme

Güvenlik önerileri sayfasından bir düzeltme isteği gönderdiğinizde, bir düzeltme etkinliği başladı. Birkaç gün içinde düzeltme sayfasında Tehdit ve Güvenlik Açığı Yönetimi **bir** güvenlik görevi oluşturulur ve bu sayfada bir düzeltme bileti Microsoft Intune.

"Dikkat gerekiyor" düzeltme seçeneğini tercih ettiyseniz, iz izdeleymiz gerçek bir eylem söz değilken ilerleme çubuğu, bilet durumu veya son tarih olmaz.

Düzeltme sayfasına olduktan sonra, görüntülemek istediğiniz düzeltme etkinliğini seçin. Düzeltme adımlarını izleyebilir, ilerlemeyi izleyebilir, ilgili öneriyi  bakabilirsiniz, CSV'ye aktarabilirsiniz veya tamamlandı olarak işaret alabilirsiniz.

:::image type="content" source="../../media/remediation-flyouteolswnew.png" lightbox="../../media/remediation-flyouteolswnew.png" alt-text="Seçilen bir düzeltme etkinliği ve bu etkinliğin açıklama, IT hizmeti ve cihaz yönetim araçları ve cihaz düzeltmesi listeli çıktısı ile Düzeltme sayfası örneği":::

> [!NOTE]
> Tamamlanmış düzeltme etkinlikleri için 180 günlük bir bekletme süresi vardır. Düzeltme sayfasının en iyi şekilde performans gösterirken bu sayfayı en iyi şekilde gerçekleştirmesini sağlamak için, düzeltme etkinliği tamamlandıktan 6 ay sonra kaldırılır.

### <a name="completed-by-column"></a>Sütuna göre tamamlandı

Düzeltme sayfasındaki "Tamamlanan" sütunuyla, düzeltme etkinliğini kimlerin kapatmış olduğunu izleme.

- **E-posta** adresi: Görevi el ile tamamlayan kişinin e-postası
- **Sistem onayı**: Görev otomatik olarak tamamlandı (tüm cihazlar düzeltildi)
- **Yok**: Bu eski görevin nasıl tamamlanmıştır, bilmiyorum çünkü bilgiler kullanılamaz

:::image type="content" alt-text="İki satırlı sütunlar tarafından oluşturulur ve tamamlanır. Tamamlanan satırın bir satırı e-posta örneği, diğer satırda sistem onayı var." source="images/tvm-completed-by.png":::

### <a name="top-remediation-activities-in-the-dashboard"></a>Panoda en iyi düzeltme etkinlikleri

Tehdit **ve Güvenlik Açığı yönetim panosunda** [en iyi **düzeltme etkinliklerini** görüntüleyebilirsiniz](tvm-dashboard-insights.md). Düzeltme sayfasına gitmek için herhangi bir **girdiyi** seçin. IT yönetici ekibi görevi düzelttirdikten sonra, düzeltme etkinliğini tamamlandı olarak işaretebilirsiniz.

![En iyi düzeltme etkinlikleri kartı örneği ve güvenlik önerilerinden oluşturulan en önemli etkinlikleri listeleen bir tablo.](images/tvm-remediation-activities-card.png)

## <a name="related-articles"></a>İlgili makaleler

- [Tehdit ve güvenlik açığı yönetimi genel bakış](next-gen-threat-and-vuln-mgt.md)
- [Pano](tvm-dashboard-insights.md)
- [Güvenlik önerileri](tvm-security-recommendation.md)