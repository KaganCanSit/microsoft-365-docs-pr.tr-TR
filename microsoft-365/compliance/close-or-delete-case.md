---
title: Bir vakayı kapatma veya silme
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Microsoft Purview eKeşif (Premium) olayı tarafından desteklenen bir araştırma veya yasal olay kapatıldığında veya silindiğinde ne olacağını öğrenin.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: f6428360c76862a0c4ff0c81b1cb83fb8760d789
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096088"
---
# <a name="close-or-delete-an-ediscovery-premium-case"></a>eBulma (Premium) servis talebini kapatma veya silme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview eBulma (Premium) olayı tarafından desteklenen yasal dava veya araştırma tamamlandığında, bir servis talebini kapatabilir veya silebilirsiniz. Kapatılan bir olayı da yeniden açabilirsiniz.

## <a name="close-a-case"></a>Servis talebini kapatma

eBulma (Premium) servis talebini kapattığınızda şunlar olur:

- Servis talebi ayrı tutmada herhangi bir içerik konumu içeriyorsa, bu ayrı tutmalar kapatılır. Ayrı tutma kapatıldıktan sonra, beklemede olan içerik konumlarına 30 günlük yetkisiz kullanım süresi ( *gecikmeli saklama* olarak adlandırılır) uygulanır. Bu, içeriğin hemen silinmesini önlemeye yardımcı olur ve yöneticilere gecikme saklama süresi dolduktan sonra kalıcı olarak silinecek içeriği arama veya kurtarma fırsatı verir. Daha fazla bilgi için bkz. [eBulma ayrılığından içerik konumlarını kaldırma](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold).

- Servis talebi kapatıldığında yalnızca bu servis talebiyle ilişkili ayrı tutmalar kapatılır. Diğer ayrı tutmalar bir içerik konumuna (Dava Ayrı Tutma, Microsoft Purview eBulma (Standart) ayrı tutma veya farklı bir eBulma (Premium) durumundan ayrı tutma gibi) yerleştiriliyorsa bu ayrı tutmalar yine korunur.

- Servis talebi, Microsoft Purview uyumluluk portalındaki eBulma sayfasında listelenmeye devam etmektedir. Kapalı bir servis talebinin ayrıntıları, saklamaları, aramaları ve üyeleri korunur.

- Servis talebi kapandıktan sonra düzenleyebilirsiniz. Örneğin, eBulma'da (Premium) üyeleri ekleyebilir veya kaldırabilir, arama oluşturabilir, arama sonuçlarını dışarı aktarabilir ve arama sonuçlarını analiz için hazırlayabilirsiniz. Etkin ve kapalı servis talepleri arasındaki temel fark, servis talebi kapatıldığında tutmaların kapalı olmasıdır.

Bir servis talebini kapatmak için:

1. **eBulma (Premium)** sayfasında kapatmak istediğiniz servis talebini seçin.

2. **Ayarlar** sekmesinde, **Servis Talebi Bilgileri'nin** altında **Seç'e** tıklayın.

   ![eBulma (Premium) durumunda servis talebi bilgileri açılır sayfasına erişin.](..\media\AeDSelectCaseInformation.png) 

3. **Servis Talebi Bilgileri** açılır sayfasının en altında **Eylemler'e** ve ardından **Büyük/küçük harf kapat'a** tıklayın.

   Kapanış işleminin tamamlanması 60 dakika kadar sürebilir.

## <a name="reopen-a-closed-case"></a>Kapatılan servis talebini yeniden açma

Bir eBulma (Premium) servis talebini yeniden açtığınızda, servis talebi kapatıldığında geçerli olan tüm tutmalar otomatik olarak yeniden başlatılmaz. Servis talebi yeniden açıldıktan sonra **, Ayrı Tutmalar** sekmesine gitmeniz ve önceki ayrı tutmaları açmanız gerekir. Ayrı tutmayı açmak için açılır sayfayı görüntülemek için bu sayfayı seçin ve ardından **Durum** iki durumlu düğmesini **Açık** olarak ayarlayın.

Kapalı bir olayı yeniden açmak için:

1. **eBulma (Premium)** sayfasında yeniden açmak istediğiniz servis talebini seçin.

2. **Ayarlar** sekmesinde, **Servis Talebi Bilgileri'nin** altında **Seç'e** tıklayın.

3. **Servis Talebi Bilgileri** açılır sayfasının en altında **Eylemler'e** ve ardından **Servis talebi yeniden aç'a** tıklayın.

   Yeniden açma işleminin tamamlanması 60 dakika kadar sürebilir.

## <a name="delete-a-case"></a>Servis talebini silme

Hem etkin hem de kapalı eBulma (Premium) servis taleplerini silebilirsiniz. Bir servis talebini sildiğinizde, servis talebiyle ilişkili tüm bileşenler (koruyucuların listesi, iletişimler, aramalar, gözden geçirme kümeleri ve dışarı aktarma işi gibi) silinir. Servis talebi, Microsoft Purview uyumluluk portalındaki **eBulma (Premium)** sayfasındaki servis talebi listesinden kaldırılır. Silinen bir olayı kurtaramaz veya yeniden açamazsınız.

> [!NOTE]
> Veri taşması senaryolarında, bir gözden geçirme kümesindeki öğeleri kaldırmanın tek yolu eBulma (Premium) servis talebini silmektir. Diğer "arama ve temizleme" yöntemleri, gözden geçirme kümesindeki öğeleri kaldırmaz.

Bir servis talebini silebilmeniz (etkin veya kapalı olması fark etmeksizin) önce servis talebiyle ilişkili *tüm* ayrı tutmaları silmeniz gerekir. Bu durum **Kapalı** olan ayrı tutmaları silmeyi içerir.

Bir servis talebiyle ilişkili ayrı tutmaları silmek için:

1. Silmek istediğiniz eBulma (Premium) servis talebinin **Ayrı Tutmalar** sekmesine gidin.

2. Silmek istediğiniz ayrı tutmaya tıklayın.

3. Açılır sayfada **Sil bekletme'ye** tıklayın.

Bir servis talebini silmek için:

1. **eBulma (Premium)** sayfasında silmek istediğiniz servis talebini seçin.

2. **Ayarlar** sekmesinde, **Servis Talebi Bilgileri'nin** altında **Seç'e** tıklayın.

3. **Servis Talebi Bilgileri** açılır sayfasının en altında **Eylemler'e** ve ardından **Büyük/küçük harf sil'e** tıklayın.

