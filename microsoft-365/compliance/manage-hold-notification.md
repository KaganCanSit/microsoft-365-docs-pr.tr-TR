---
title: Bekletme bildirimlerini yönetme
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Yasal tutma bildirimlerinizin durumunu izlemek ve gerekirse bunları güncelleştirip yeniden göndermek için eBulma (Premium) içindeki iletişim iş akışını kullanın.
ms.openlocfilehash: 83e5331aaea59893f06cfa0629d627e500cfe1b1
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64996184"
---
# <a name="manage-hold-notifications"></a>Bekletme bildirimlerini yönetme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Yasal tutma bildirimi iş akışınızı başlattıktan sonra, iletişimlerinizin durumunu izlemek için Microsoft Purview eKeşif 'teki (Premium) iletişim iş akışını kullanabilirsiniz. İletişimler sekmesi, eBulma (Premium) servis talebinizdeki tüm bildirimlerin listesini içerir. Atanmış veya bildirimi kabul etmiş olan koruyucuların sayısı gibi ayrıntıları görebilirsiniz.

## <a name="monitor-acknowledgments"></a>Onayları izleme

**İletişimler** sekmesinden bir iletişim seçtikten sonra, ayrı tutma bildirimini kabul eden koruyucuların listesini görüntüleyebilirsiniz. 

1. Uyumluluk merkezinde **eBulma > eBulma (Premium)** bölümüne gidin.

2. Bir servis talebi seçin ve **İletişimler** sekmesine tıklayın.

3. Koruyucu iletişim açılır sayfasını görüntülemek için bir **iletişim** seçin.

İletişim açılır sayfasında seçili iletişimle ilişkilendirilmiş koruyucuların listesi görüntülenir. Bu sayfada ayrıca içgörüler ve kaç onay alındığı ve kaç tane kabul edildiği hakkında bilgiler de görüntülenir. Sayfa ayrıca hangi koruyucuların bekletme bildirimi aldıklarını belirten bir bildirim gönderdiğini de gösterir.

## <a name="re-send-a-hold-notice"></a>Ayrı tutma bildirimini yeniden gönderme

Bazen, koruyucular günlük işlerinde e-posta iletilerinin izini kaybeder. Ya da uzun süre devam eden bir dava için, bir koruyucu sizinle veya diğer kişilerle iletişim kurabilir ve yeniden bildirim göndermenizi isteyebilir. Yasal tutma bildirimleri için iletişim iş akışını yönetirken, bunu "kullanıcının posta kutusunun en üstüne" getirmek için bir bildirimi yeniden göndermeniz gerekebilir.

Bir saklama bildirimini bir koruyucuya yeniden göndermek için:

1. eBulma'da (Premium), bir servis talebi seçin ve **İletişimler** sekmesine tıklayın.

2. Koruyucu iletişim açılır sayfasını görüntülemek için bir **iletişim** seçin.

3. **Daha fazla > Bekletme bildirimini yeniden gönder'e** tıklayın.

4. **Ayrı tutma bildirimini yeniden gönder** açılır sayfasında, bildirimi yeniden göndermek istediğiniz koruyucuları seçin ve isteğe bağlı bir neden yazın.

5. Bildirimi seçilen koruyuculara göndermek için **Yeniden gönder'e** tıklayın.

Bir koruyucu bekletme bildirimini kabul etmediyse, anımsatıcı ve yükseltme iş akışı yeniden başlatılır. Bir koruyucu saklama bildirimini kabul ettiyse, koruyucu orijinal saklama bildiriminin bir kopyasını alır.

> [!NOTE]
> Yasal bir saklama bildirimini yalnızca iletişime atanan koruyuculara yeniden gönderebilirsiniz. 

## <a name="update-preservation-requirements"></a>Koruma gereksinimlerini güncelleştirme
  
Olay ilerledikçe, koruyucuların daha önce belirtilenden daha fazla veya daha az veriyi korumaları gerekebilir. eBulma terimleriyle, güncelleştirilmiş içerikle ayrı tutma bildirimini yeniden düzenlemeniz gerekir.

İlk ayrı tutma bildiriminin içeriğini güncelleştirmek için:

1. eBulma'da (Premium), bir servis talebi seçin ve **İletişimler** sekmesine tıklayın.

2. Güncelleştirmek istediğiniz ayrı tutma bildirimini seçin ve **Koruyucu iletişim** açılır sayfasında **Düzenle'ye** tıklayın.

3. **İletişimi Düzenle** sihirbazında, sihirbazın sol bölmesinde **Portal İçeriği Tanımla'ya** tıklayın ve bildirimin içeriğini güncelleştirin.

4. **Kaydet**'e tıklayın.

Yeniden verme bildirimi, yasal saklama bildirimine atanan tüm koruyuculara gönderilir. Buna ek olarak, Anımsatıcı veya Yükseltme bildirimi etkinleştirilirse, bu tür bildirimlerin iş akışları yeniden başlatılır.

## <a name="update-legal-hold-notifications-and-settings"></a>Yasal tutma bildirimlerini ve ayarlarını güncelleştirme

Verme, Yayın, Yeniden Verme, Anımsatıcı veya Yükseltme bildiriminin içeriğini veya ayarlarını güncelleştirdiğinizde, bu değişiklikler iş akışı tarafından oluşturulan gelecekteki tüm iletişimler için geçerli olur.

## <a name="more-information"></a>Daha fazla bilgi

- [Bir vakaya yediemin ekleme](add-custodians-to-case.md)

- [Yasal tutma bildirimi oluşturma](create-hold-notification.md)

- [Bekletme bildirimini onaylama](acknowledge-hold-notification.md)
