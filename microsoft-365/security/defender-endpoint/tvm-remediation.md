---
title: Güvenlik açıklarını düzeltmek Tehdit ve Güvenlik Açığı Yönetimi
description: Güvenlik önerileriyle bulunan güvenlik zayıflarını düzeltmek ve gerekirse, güvenlik önerilerini kullanarak özel durumlar Tehdit ve Güvenlik Açığı Yönetimi.
keywords: Uç Nokta için Microsoft Defender, tvm, Uç Nokta için Microsoft Defender, tvm, Tehdit ve Güvenlik Açığı Yönetimi, tehdit & güvenlik açığı yönetimi, tehdit & güvenlik açığı yönetimi düzeltme, tvm düzeltmesi intune, tvm düzeltmesi sccm
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
ms.openlocfilehash: 9631c38279fbcfcbc4d55b09409af9bb16c783f6
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476675"
---
# <a name="remediate-vulnerabilities-with-threat-and-vulnerability-management"></a>Güvenlik açıklarını düzeltmek Tehdit ve Güvenlik Açığı Yönetimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Tehdit ve güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

## <a name="request-remediation"></a>Düzeltme isteği

Sistem Tehdit ve Güvenlik Açığı Yönetimi özelliği, Uç Nokta için Microsoft Defender isteği iş akışı aracılığıyla Güvenlik ve IT yöneticileri arasındaki boşluğu köprüler. Sizin gibi güvenlik yöneticileri, Güvenlik öneri sayfalarındaki güvenlik açığını düzeltmek için IT Yöneticisi'Intune.

### <a name="enable-microsoft-intune-connection"></a>Microsoft Intune bağlantısını etkinleştirme

Bu özelliği kullanmak için iş bağlantılarınızı Microsoft Intune etkinleştirin. Gelişmiş Microsoft 365 Defender Genel Gelişmiş **özellikler'Ayarlar** \> **gidin**\>. Ekranı aşağı kaydırın ve bağlantı **Microsoft Intune bakın**. Varsayılan olarak, iki durumlu düğme kapalıdır. Microsoft Intune **iki durumlu** düğmeyi **Açık olarak seçin**.

**Not**: Intune bağlantınız etkinleştirilmişse, düzeltme isteği oluştururken Intune görev oluşturma seçeneğiniz vardır. Bağlantı ayarlanmazsa bu seçenek görünmez.

Ayrıntılar [için Intune güvenlik açıklarını düzeltmek üzere Uç Nokta için Microsoft Defender'i](/intune/atp-manage-vulnerabilities) kullanma'ya bakın.

### <a name="remediation-request-steps"></a>Düzeltme isteği adımları

1. Microsoft 365 Defender portalında tehdit ve  Güvenlik açığı yönetimi gezinti menüsüne gidin ve Güvenlik **önerileri'Öneriler** [**seçin**](tvm-security-recommendation.md).

2. Düzeltme isteğide kullanmak istediğiniz güvenlik önerilerini seçin ve sonra da Düzeltme **seçenekleri'ne tıklayın**.

3. Düzeltme isteğiniz, uygun cihaz grupları, öncelik, son tarih ve isteğe bağlı notlar da içinde olmak üzere formu doldurun.
    1. "Dikkat gerekiyor" düzeltme seçeneğini tercih ediyorsanız, belirli bir eylem olduğu için son tarih seçmeniz kullanılamaz.

4. İsteği **gönder'i seçin**. Bir düzeltme isteği gönderilen düzeltme etkinliği öğesi Tehdit ve Güvenlik Açığı Yönetimi içinde bir düzeltme etkinliği öğesi oluşturur ve bu önerinin düzeltme ilerlemesini izlemek için kullanılabilir. Bu, bir düzeltmeyi tetiklemez veya cihazlara herhangi bir değişiklik uygulamaz.

5. Yeni isteği ONAYLAMAK veya reddetmek ve paket dağıtımını başlatmak için, INTUNE yöneticinize yeni isteği haber vermelerini ve oturum açmalarını sebilirsiniz.

6. Düzeltme [**isteğinizin durumunu**](tvm-remediation.md) görüntülemek için Düzeltme sayfasına gidin.

Biletin iki gün içinde nasıl gösterip gösterile Intune, ayrıntılar için Intune güvenlik açıklarını düzeltmek [Uç Nokta için Microsoft Defender](/intune/atp-manage-vulnerabilities) bakın.

> [!NOTE]
> İsteğiniz 10.000'den fazla cihazı düzeltmeyle ilgili olursa düzeltme için yalnızca 10.000 cihaz gönderebiliriz Intune.

Organizasyon un siber güvenlik güvenlik güveni zayıflığı tanımlandıktan ve eyleme edilebilir güvenlik önerilerine eş olduktan [sonra, güvenlik](tvm-security-recommendation.md) görevleri oluşturmaya başlama. Düzeltme biletlerinin oluşturulmuş olduğu Microsoft Intune ve tümleştirme yoluyla görevler oluşturabilirsiniz.

Güvenlik önerilerini düzelterek, güvenlik açıklarından daha düşük güvenlik açıkları ve güvenlik yapılandırmanızı artırma.

## <a name="view-your-remediation-activities"></a>Düzeltme etkinliklerinizi görüntüleme

Güvenlik önerileri sayfasından bir düzeltme isteği gönderdiğinizde, bir düzeltme etkinliği başladı. Birkaç gün içinde düzeltme sayfasında Tehdit ve Güvenlik Açığı Yönetimi **bir** güvenlik görevi oluşturulur ve bu sayfada bir düzeltme bileti Microsoft Intune.

"Dikkat gerekiyor" düzeltme seçeneğini tercih ettiyseniz, iz izdeleymiz gerçek bir eylem söz değilken ilerleme çubuğu, bilet durumu veya son tarih olmaz.

Düzeltme sayfasına olduktan sonra, görüntülemek istediğiniz düzeltme etkinliğini seçin. Düzeltme adımlarını izleyebilir, ilerlemeyi izleyebilir, ilgili öneriyi  bakabilirsiniz, CSV'ye aktarabilirsiniz veya tamamlandı olarak işaret alabilirsiniz.

:::image type="content" source="../../media/remediation-flyouteolswnew.png" alt-text="Seçilen bir düzeltme etkinliğinin ve açıklamanın, IT hizmetinin ve cihaz yönetim araçlarının ve cihaz düzeltmenin liste listeli çıktısı olan Düzeltme sayfası" lightbox="../../media/remediation-flyouteolswnew.png":::

> [!NOTE]
> Tamamlanmış düzeltme etkinlikleri için 180 günlük bir bekletme süresi vardır. Düzeltme sayfasının en iyi şekilde performans gösterirken bu sayfayı en iyi şekilde gerçekleştirmesini sağlamak için, düzeltme etkinliği tamamlandıktan 6 ay sonra kaldırılır.

### <a name="completed-by-column"></a>Sütuna göre tamamlandı

Düzeltme sayfasındaki "Tamamlanan" sütunuyla, düzeltme etkinliğini kimlerin kapatmış olduğunu izleme.

- **E-posta** adresi: Görevi el ile tamamlayan kişinin e-postası
- **Sistem onayı**: Görev otomatik olarak tamamlandı (tüm cihazlar düzeltildi)
- **Yok**: Bu eski görevin nasıl tamamlanmıştır, bilmiyorum çünkü bilgiler kullanılamaz

:::image type="content" source="images/tvm-completed-by.png" alt-text="Oluşturan ve iki satırlı sütunlara göre tamamlandı" lightbox="images/tvm-completed-by.png":::

### <a name="top-remediation-activities-in-the-dashboard"></a>Panoda en iyi düzeltme etkinlikleri

Tehdit **ve Güvenlik Açığı yönetim panosunda** [en iyi **düzeltme etkinliklerini** görüntüleyebilirsiniz](tvm-dashboard-insights.md). Düzeltme sayfasına gitmek için herhangi bir **girdiyi** seçin. IT yönetici ekibi görevi düzelttirdikten sonra, düzeltme etkinliğini tamamlandı olarak işaretebilirsiniz.

:::image type="content" source="images/tvm-remediation-activities-card.png" alt-text="En İyi düzeltme etkinlikleri kartı" lightbox="images/tvm-remediation-activities-card.png":::

## <a name="related-articles"></a>İlgili makaleler

- [Tehdit ve güvenlik açığı yönetimi genel bakış](next-gen-threat-and-vuln-mgt.md)
- [Pano](tvm-dashboard-insights.md)
- [Güvenlik önerileri](tvm-security-recommendation.md)