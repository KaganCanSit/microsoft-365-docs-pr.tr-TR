---
title: eBulma (Standart) servis taleplerini kapatma, yeniden açma ve silme
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Bu makalede, eBulma (Standart) servis taleplerinin nasıl yönetileceğini açıklanmaktadır. Bu, bir servis talebini kapatmayı, kapalı bir servis talebini yeniden açmayı ve bir servis talebini silmeyi içerir.
ms.openlocfilehash: 5c2efd96f563eb2947b17e1cc857613d27981dac
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66628869"
---
# <a name="close-reopen-and-delete-a-ediscovery-standard-case"></a>eBulma (Standart) servis talebini kapatma, yeniden açma ve silme

Bu makalede, Microsoft 365'te Microsoft Purview eKeşif (Standart) servis taleplerinin nasıl kapatıldığı, yeniden açıldığı ve silineceği açıklanır.

## <a name="close-a-case"></a>Servis talebini kapatma

Bir eBulma (Standart) olayı tarafından desteklenen yasal dava veya araştırma tamamlandığında, olayı kapatabilirsiniz. Bir olayı kapattığınızda şunlar olur:
  
- Servis talebi herhangi bir eBulma ayrı tutması içeriyorsa, bunlar kapatılır. Ayrı tutma kapatıldıktan sonra, beklemede olan içerik konumlarına 30 günlük yetkisiz kullanım süresi ( *gecikmeli saklama* olarak adlandırılır) uygulanır. Bu, içeriğin hemen silinmesini önlemeye yardımcı olur ve gecikme saklama süresi dolduktan sonra kalıcı olarak silinmeden önce yöneticilere içerik arama ve geri yükleme fırsatı sağlar. Daha fazla bilgi için bkz. [eBulma ayrılığından içerik konumlarını kaldırma](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold).

- Servis talebi kapatıldığında yalnızca bu servis talebiyle ilişkili ayrı tutmalar kapatılır. Diğer ayrı tutmalar bir içerik konumuna (Dava Ayrı Tutma, saklama ilkesi veya farklı bir eBulma (Standart) durumundan ayrı tutma gibi) yerleştirilirse, bu ayrı tutmalar yine korunur.

- Servis talebi, Microsoft Purview uyumluluk portalı eBulma (Standart) sayfasında listelenmeye devam etmektedir. Kapalı bir servis talebinin ayrıntıları, saklamaları, aramaları ve üyeleri korunur.

- Servis talebi kapandıktan sonra düzenleyebilirsiniz. Örneğin, üye ekleyebilir veya kaldırabilir, arama oluşturabilir ve arama sonuçlarını dışarı aktarabilirsiniz. Etkin ve kapalı servis talepleri arasındaki temel fark, servis talebi kapatıldığında eBulma tutmalarının kapalı olmasıdır.

Bir servis talebini kapatmak için:
  
1. Uyumluluk portalında, kuruluşunuzdaki **eBulma** > **(Standart)** servis taleplerinin listesini görüntülemek için eBulma eBulma (Standart) seçeneğine tıklayın.

2. Kapatmak istediğiniz servis talebinin adına tıklayın.

   ![Servis talebi giriş sayfasında büyük/küçük harf kapatma.](../media/eDiscoveryCaseHomePage.png)

3. Giriş sayfasındaki **Durum'un** altında Büyük **/küçük harf kapat'a** tıklayın.

    Servis talebiyle ilişkili ayrı tutmaların kapatılacağını belirten bir uyarı görüntülenir.

4. Servis talebini kapatmak için **Evet'e** tıklayın.

    Servis talebi giriş sayfasındaki durum **Etkin'den** **Kapanış'a** değiştirilir.

5. **eBulma (Standart)** sayfasında, kapatılan servis talebinin durumunu güncelleştirmek için **Yenile'ye** tıklayın. Kapanış işleminin tamamlanması 60 dakika kadar sürebilir.

    İşlem tamamlandığında, **eBulma (Standart)** sayfasında servis talebinin durumu **Kapalı** olarak değiştirilir.

## <a name="reopen-a-closed-case"></a>Kapatılan servis talebini yeniden açma

Bir servis talebini yeniden açtığınızda, servis talebi kapatıldığında geçerli olan tüm eBulma tutmaları otomatik olarak yeniden başlatılmaz. Servis talebi yeniden açıldıktan sonra **, Ayrı Tutmalar** sayfasına gitmeniz ve önceki ayrı tutmaları açmanız gerekir. Ayrı tutmayı açmak için açılır sayfayı görüntülemek için bu sayfayı seçin ve ardından **Durum** iki durumlu düğmesini **Açık** olarak ayarlayın.
  
1. Uyumluluk portalında, kuruluşunuzdaki **eBulma** >  (Standart) servis taleplerinin listesini görüntülemek için eBulma **Çekirdeği'ne** tıklayın.

2. Yeniden açmak istediğiniz servis talebinin adına tıklayın.

   ![Kapatılan bir olayı yeniden açın.](../media/eDiscoveryCaseHomePageReopen.png)

3. Giriş sayfasındaki **Durum'un** altında Servis **talebini yeniden aç'a** tıklayın.

    Kapatıldığında servis talebiyle ilişkili ayrı tutmaların otomatik olarak açılmayacağını belirten bir uyarı görüntülenir.

4. Servis talebini yeniden açmak için **Evet'e** tıklayın.

    Servis talebi giriş sayfası açılır sayfasının durumu **Kapalı** olandan **Etkin** olarak değiştirilir.

5. Yeniden açılan servis talebinin durumunu güncelleştirmek için **eBulma (Standart)** sayfasında **Yenile'ye** tıklayın. Yeniden açma işleminin tamamlanması 60 dakika kadar sürebilir. 

    İşlem tamamlandığında, servis talebinin durumu **eBulma (Standart)** sayfasında **Etkin** olarak değiştirilir.

6. (İsteğe bağlı) Yeniden açılan servis talebiyle ilişkili ayrı tutmaları açmak için **Ayrı Tutmalar** sekmesine gidin, ayrı tutmayı seçin ve ardından bekleme açılır sayfasındaki **Durum'un** altındaki onay kutusunu seçin.
  
## <a name="delete-a-case"></a>Servis talebini silme

Etkin ve kapalı eBulma (Standart) servis taleplerini de silebilirsiniz. Bir servis talebini sildiğinizde, servis talebindeki tüm aramalar ve dışarı aktarmalar silinir ve servis talebi uyumluluk portalındaki **eBulma (Standart)** sayfasındaki servis talebi listesinden kaldırılır. Silinen bir olayı yeniden açamazsınız.

Bir servis talebini silebilmeniz (etkin veya kapalı olması fark etmeksizin) önce servis talebiyle ilişkili *tüm* eBulma tutmalarını silmeniz gerekir. Bu durum **Kapalı** olan ayrı tutmaları silmeyi içerir. 

eBulma ayrı tutmasını silmek için:

1. Silmek istediğiniz durumda **Ayrı Tutmalar** sekmesine gidin.

2. Silmek istediğiniz ayrı tutmayı seçin.

3. Açılır sayfada **Sil'e** tıklayın.

      ![eBulma ayrı tutmasını silin.](../media/DeleteeDiscoveryHold.png)

Bir servis talebini silmek için:

1. Uyumluluk portalında, kuruluşunuzdaki **eBulma** > **(Standart)** servis taleplerinin listesini görüntülemek için eBulma eBulma (Standart) seçeneğine tıklayın.

2. Silmek istediğiniz servis talebinin adına tıklayın.

3. Servis talebi giriş sayfasındaki **Durum'un** altında Büyük **/küçük harf sil'e** tıklayın.

      ![Bir servis talebini silin.](../media/eDiscoveryCaseHomePageDelete.png)

Silmeye çalıştığınız durum eBulma ayrı tutmaları içeriyorsa bir hata iletisi alırsınız. Servis talebiyle ilişkili tüm ayrı tutmaları silmeniz ve ardından servis talebini silmeyi yeniden denemeniz gerekir.
