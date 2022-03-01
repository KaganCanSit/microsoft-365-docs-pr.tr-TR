---
title: Metinde yeni büyük/Advanced eDiscovery
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
description: Kümeleri gözden geçirmek ve diğer artırılmış sınırlardan ve yeni işlevlerden yararlanmak için Advanced eDiscovery'de yeni vaka biçimini kullanın.
ms.openlocfilehash: 9b0e87e7d24565bb89444fe5b1e5cbf43d915e42
ms.sourcegitcommit: 7f0c5b55e2966c0c1ce6a153a4e6a7ec035bd818
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2021
ms.locfileid: "63007656"
---
# <a name="use-the-new-case-format-in-advanced-ediscovery"></a>Yeni büyük/yeni biçim biçimini Advanced eDiscovery

Kritik eBulma süreçleri için Advanced eDiscovery çözümlerini Microsoft 365 kuruluşlar bu çözümü kullanmaya devam ediyor. Bu düzenlemelere ilişkin taleplere, soruşturmalara ve mahkemelere yanıt vermeyi kapsar. Müşteri Advanced eDiscovery arttıkça, müşteri için yaygın bir gereksinim tek bir durumda yönetil binecek toplam içerik miktarını Advanced eDiscovery olur. Hem toplam veri hacmi hem de toplam öğe sayısı gibi büyük/küçük harf boyutlarında büyük/küçük harf büyük/küçük harfe dönüştürmeye yardımcı olmak için, büyük/küçük harf Advanced eDiscovery seçebilirsiniz.  

## <a name="create-a-case"></a>Vaka oluşturma

Yeni büyük/Advanced eDiscovery biçimiyle bir büyük/harf biçimi oluşturmak için:

1. Gidin ve <https://compliance.microsoft.com> oturum açma.

2. Gezinti bölmesinin sol bölmesinde, Microsoft 365 uyumluluk merkezi **eBulma'ya > tıklayın**.

3. Olay **Advanced eDiscovery** Vakalar sekmesine **tıklayın ve** sonra da Vaka **oluştur'a tıklayın**.

   Yeni **eBulma olay sayfası** görüntülenir. Büyük **/küçük harf** biçimi bölümünde, yeni biçimi kullanarak büyük/küçük harf oluşturma seçeneği vardır.

   ![Yeni eBulma olay sayfasındaki yeni büyük/harf biçimi seçeneği.](..\media\AeDNewCaseFormat1.png)

4. Vakayı adlandırdikten sonra, **Yeni seçeneğini belirleyin** ve ardından **Kaydet'e** tıklarsanız, büyük/yeni biçimi kullanarak vakayı oluşturun.

## <a name="benefits-of-the-new-case-format"></a>Yeni vaka biçiminin avantajları

Yeni vaka biçimi 40 milyondan fazla öğe içeren vakaları yönetmenize olanak sağlar. Bu özellik, eBulma iş akışının tamamı boyunca büyük hacimli vaka verilerini etkili bir şekilde yönetmenize yardımcı olur.

İşte iş akışında büyük davaların diğer Advanced eDiscovery.

- **Koleksiyon**: Yeni olay biçiminde, tek bir koleksiyon için 1 TB'a kadar veri toplayabilirsiniz.

   Her durumda, koleksiyon ayarları varsayılan olarak bulut Eklerini ve bağlamsal ekleri Teams içeriği Yammer ayarlar. Bu ayarlar, soruşturma içindeki dijital iletişimlerin tüm resmini toplamaya yardımcı olur. Konuşmalar Teams Yammer konuşmalar için, yeni olay biçimi konuşmaların bağlamını sağlamak ve sohbet tabanlı içerikle üretilen toplam öğe sayısını azaltmak için 1:1, 1: N ve Kanal konuşmalarının zaman tabanlı anlık görüntülerini HTML dökümlerine dönüştürür.  

- **Gözden** Geçir: Her gözden geçirme kümesi 1 TB'a kadar genişletme öncesi içeriği destekler. Filtreler ve sorgular için Ekip adı, kanal adı ve konuşma adı gibi diğer meta veriler Teams kullanılabilir. Her metin dökümü, yanıt veren öğenin önceki ve sonrası için zaman tabanlı içerik içerir. Kanal konuşmaları için, yanıt veren içerik için kök gönderi ve tüm yanıtlar toplanır. Daha fazla bilgi için bkz[. Advanced eDiscovery (önizleme) içeriği için Microsoft Teams akışı](teams-workflow-in-advanced-ediscovery.md)

- **Dışarı** Aktar: Tek bir dışarı aktarma işsinde büyük içerik kümelerini dışarı aktarabilirsiniz. Yeni büyük/küçük harf biçimi, bir dışarı aktarma işsinde daha küçük olan 5 milyon belgeyi veya 500 GB'lık bir alanı dışarı aktarmayı sağlar.

Buna ek olarak, yeni büyük/küçük harf biçimi, olaydaki her gözden geçirme kümesi toplam boyutunu görüntüleyen güncelleştirilmiş bir kullanıcı arabirimi içerir. Gözden geçirme kümesi boyutları, Gözden Geçir kümeleri sekmesindeki **bir sütunda** görüntülenir.

![Kullanıcı arabiriminde yeni gözden geçirme Advanced eDiscovery istatistikleri.](..\media\LargeCaseUI.png)

## <a name="frequently-asked-questions"></a>Sık sorulan sorular

**Tek bir koleksiyonda 1 TB'den fazla toplamaya çalışır musunuz?**

Performans olumsuz etki olur ve bazı durumlarda verimlere neden olabilir.

**Bulut ekleri varsayılan olarak büyük harf biçiminde dahil edilirse; Bu içeriği gözden geçirme deneyimimdan nasıl kaldırabilirsiniz?**  

İleti türe göre filtrelemek veya HasAttachment filtresini kullanarak bulut eklerini dışarıda tutmak için gözden geçirme kümesi filtrelerini kullanın. Daha fazla bilgi için bkz [. Gözden geçirme kümesinde içeriği sorgulama ve filtreleme](review-set-search.md).

**Sohbet görüşmesi dökümleri dışarı aktarıldı mı? Yükleme dosyası tüm genişletilmiş meta verileri ve her döküm için tek bir öğeyi mi içerir?**

Konuşmanın tüm meta verileri HTML döküm dosyasına eklidir.  Sık kullanılan alanların çoğu yükleme dosyasında kullanılabilir. Dışarı aktarıldı meta veriler hakkında daha fazla bilgi için bkz. Meta [veri alanlarını Advanced eDiscovery](document-metadata-fields-in-Advanced-eDiscovery.md).
