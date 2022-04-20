---
title: eBulma'da yeni büyük/küçük harf biçimi (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
ms.reviewer: ninachen
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
description: EBulma (Premium) içinde yeni büyük/küçük harf biçimini kullanarak kümeleri gözden geçirmek ve artan diğer sınırlardan ve yeni işlevlerden yararlanmak için daha fazla öğe ekleyebilirsiniz.
ms.openlocfilehash: 36650a369d2bac2742eb7f0d5ea76b3a530a1a03
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64947439"
---
# <a name="use-the-new-case-format-in-ediscovery-premium"></a>eBulma'da yeni servis talebi biçimini kullanma (Premium)

Daha fazla kuruluş eBulma (Premium) çözümünü kritik eBulma işlemleri için Microsoft 365 kullanıyor. Bu, mevzuat isteklerine, araştırmalara ve davalara yanıt vermeyi içerir. eBulma (Premium) kullanımı arttıkça, ortak bir müşteri gereksinimi tek bir eBulma (Premium) durumunda yönetilebilen toplam içerik miktarını genişletmektir. Hem toplam veri hacmi hem de toplam öğe sayısı için büyük/küçük harf boyutundaki önemli artışları karşılamak için artık eBulma (Premium) servis talebi oluştururken yeni servis talebi biçimini seçebilirsiniz.  

## <a name="create-a-case"></a>Servis talebi oluşturma

Yeni servis talebi biçimini kullanarak eBulma (Premium) olayı oluşturmak için:

1. <https://compliance.microsoft.com> adresine gidin ve oturum açın.

2. Microsoft Purview uyumluluk portalının sol gezinti bölmesinde **gelişmiş > eBulma'ya** tıklayın.

3. **eBulma (Premium)** sayfasında **Servis Talepleri** sekmesine ve ardından **Servis talebi oluştur'a** tıklayın.

   **Yeni eBulma servis talebi** açılır sayfası görüntülenir. **Servis Talebi biçimi** bölümü, yeni biçimi kullanarak bir servis talebi oluşturma seçeneği sağlar.

   ![Yeni eBulma servis talebi sayfasındaki yeni servis talebi biçimi seçeneği.](..\media\AeDNewCaseFormat1.png)

4. Olayı adlandırdıktan sonra **Yeni** seçeneğini belirleyin ve ardından **Kaydet'e** tıklayarak olayı yeni biçimi kullanarak oluşturun.

## <a name="benefits-of-the-new-case-format"></a>Yeni servis talebi biçiminin avantajları

Yeni servis talebi biçimi, 40 milyondan fazla öğe içeren servis taleplerini yönetmenize olanak tanır. Bu özellik, eBulma iş akışının tamamı boyunca büyük hacimli büyük/küçük harf verilerini etkili bir şekilde yönetmenize yardımcı olur.

Aşağıda, eBulma (Premium) iş akışındaki büyük servis taleplerinin diğer avantajlarının bir listesi yer alır.

- **Koleksiyon**: Yeni durum biçiminde, tek bir koleksiyon için en fazla 1 TB veri toplayabilirsiniz.

   Her durumda, koleksiyon ayarları varsayılan olarak bulut Eklerini ve bağlamsal Teams ve Yammer içeriği toplar. Bu ayarlar, bir araştırma içinde dijital iletişimlerin tam resmini toplamaya yardımcı olur. Teams ve Yammer bağlamsal konuşmalar için yeni durum biçimi, konuşma bağlamı sağlamaya ve sohbet tabanlı içerik tarafından üretilen toplam öğe sayısını azaltmaya yardımcı olmak için 1:1, 1: N ve Kanal konuşmalarının zamana dayalı anlık görüntülerini HTML transkriptlerine dönüştürür.  

- **Gözden geçirme**: Her gözden geçirme kümesi 1 TB'a kadar genişletme öncesi içeriği destekler. Ekip adı, kanal adı ve Teams içerik için konuşma adı gibi filtreler ve sorgular için ek meta veriler kullanılabilir. Her transkript, yanıt veren öğenin öncesi ve sonrası için zamana dayalı içerik içerir. Kanal konuşmaları için, yanıt veren içerik için kök gönderi ve tüm yanıtlar toplanır. Daha fazla bilgi için bkz[. Microsoft Teams (önizleme) içeriği için eBulma (Premium) iş akışı](teams-workflow-in-advanced-ediscovery.md)

- **Dışarı Aktarma**: Tek bir dışarı aktarma işinde büyük içerik kümelerini dışarı aktarabilirsiniz. Yeni servis talebi biçimi, dışarı aktarma işinde daha küçük olan 5 milyon belgeyi veya 500 GB'ı dışarı aktarabilmenizi sağlar.

Ayrıca, yeni servis talebi biçimi, servis talebindeki her gözden geçirme kümesinin toplam boyutunu görüntüleyen güncelleştirilmiş bir kullanıcı arabirimi içerir. Gözden geçirme kümesi boyutları, **Gözden geçirme kümeleri** sekmesindeki bir sütunda görüntülenir.

![eBulma (Premium) kullanıcı arabiriminde yeni gözden geçirme kümesi istatistikleri.](..\media\LargeCaseUI.png)

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

**Tek bir koleksiyonda 1 TB'ın üzerinde toplamaya çalışırsam çalışır mı?**

Performans olumsuz etkilenir ve bazı durumlarda dengesizliklere neden olabilir.

**Bulut ekleri büyük harf biçiminde varsayılan olarak dahil edilirse; bu içeriği gözden geçirme deneyimimden nasıl kaldırabilirim?**  

İleti türüne göre filtrelemek veya HasAttachment filtresini kullanarak bulut eklerini dışlamak için gözden geçirme kümesi filtrelerini kullanın. Daha fazla bilgi için bkz. [Gözden geçirme kümesindeki içeriği sorgulama ve filtreleme](review-set-search.md).

**Sohbet konuşması transkriptlerini dışarı aktarırken, yük dosyası tüm genişletilmiş meta verileri ve her transkript için tek bir öğeyi içerecek mi?**

Konuşmanın tüm meta verileri HTML transkript dosyasına eklenir.  Ortak alanların çoğu yükleme dosyasında kullanılabilir. Dışarı aktarılan meta veriler hakkında daha fazla bilgi için bkz[. eBulma'da (Premium) belge meta veri alanları](document-metadata-fields-in-Advanced-eDiscovery.md).
