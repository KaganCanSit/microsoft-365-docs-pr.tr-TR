---
title: Microsoft 365 yönetim merkezi kutusu kullanım raporlarını kullanma
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: beffbe01-ce2d-4614-9ae5-7898868e2729
description: Kullanıcı posta kutusu kullanan kullanıcıların etkinlikleri hakkında bilgi edinmek için Posta kutusu kullanım raporunu nasıl edinebilirsiniz?
ms.openlocfilehash: 6a28b6aed8721872a31af57d4c00cd82a89c06bc
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63400902"
---
# <a name="microsoft-365-reports-in-the-admin-center---mailbox-usage"></a>Microsoft 365 Merkezinde Raporlar - Posta Kutusu kullanımı

Posta **Kutusu kullanım** raporu, kullanıcı posta kutusuna sahip kullanıcılar hakkında ve her biri gönderme, okuma, randevu oluşturma, toplantı gönderme, toplantıyı kabul etme, reddetme ve toplantı etkinliğini iptal etme e-postalarını temel alan etkinlik düzeyi hakkında bilgi sağlar. Ayrıca her kullanıcı posta kutusunun ne kadar depolama alanı kullandığı ve kaçının depolama kotalarına yaklaştığı hakkında bilgiler de sunar. 
 
## <a name="how-to-get-to-the-mailbox-usage-report"></a>Posta kutusu kullanım raporunu alma

1. Yönetim merkezinde, **Raporlar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2074756" target="_blank">Kullanımı</a> sayfasına gidin.
2. **E-posta etkinliği'nin altında** Daha **Fazlasını Görüntüle'yi seçin**. 
3. **E-posta etkinliği açılan** listesinde Posta kutusu kullanımına **Exchange** \> **seçin**.

## <a name="interpret-the-mailbox-usage-report"></a>Posta kutusu kullanım raporunu yorumlama

**Posta Kutusu**, **Depolama** ve **Kota** grafiklerine bakarak kuruluşunuzun **Posta kutusu kullanımının** bir görünümünü elde edebilirsiniz.
  
:::image type="content" alt-text="Posta kutusu kullanım raporu." source="../../media/9f610e91-cbc1-4e59-b824-7b1ddd84b738.png" lightbox="../../media/9f610e91-cbc1-4e59-b824-7b1ddd84b738.png":::

|Öğe|Açıklama|
|:-----|:-----|
|1.  |**Posta Kutusu kullanımı** raporu, son 7 gün, 30 gün, 90 gün veya 180 günlük eğilimler için görüntülenebilir. Ancak rapordaki belirli bir günü seçersiniz, tablo geçerli tarihten (raporun oluşturulma tarihine değil) itibaren 28 güne kadar olan verileri gösterir. |
|2.  |Her raporda yer alan veriler genellikle son 24 - 48 saati kapsar. |
|3.  |Posta Kutusu grafiği, kuruluşunuzdaki kullanıcı posta kutularının toplam sayısını ve raporlama dönemi içinde belirli bir günde etkin olanların toplam sayısını gösterir. Bir kullanıcı posta kutusu, e-posta gönderme, okuma, randevu oluşturma, toplantı talebinde bulunma, toplantı kabul etme, reddetme ve toplantı etkinliğini iptal etme durumları varsa etkin kabul edilir. |
|4.  |**Depolama** grafiği, kuruluşunuzda kullanılan depolama miktarını gösterir. Depolama Grafiği arşiv posta kutuları içermez. Otomatik genişleyen arşivleme hakkında daha fazla bilgi için bkz. E-postada otomatik genişleyen [arşivlemeye Microsoft 365](../../compliance/autoexpanding-archiving.md). |
|5.  | **Kota** grafiği, her kota kategorisindeki kullanıcı posta kutularının sayısını gösterir. Dört kota kategorisi vardır:  <br/>  İyi - kullanılan depolaması sorun uyarı kotasının altında olan kullanıcıların sayısı.  <br/>  Uyarı - kullanılan depolaması sorun uyarısında veya üstünde olan ancak göndermeyi yasaklama kotasının altında kalan kullanıcıların sayısı  <br/>  Gönderemez - kullanılan depolaması göndermeyi yasaklama kotasının üstünde olan ancak göndermeyi/almayı yasaklama kotasının altında kalan kullanıcıların sayısı  <br/>  Gönderemez/alamaz - kullanılan depolaması göndermeyi/almayı yasaklama kotasının üstünde olan kullanıcıların sayısı |
|6.  | **Posta Kutusu** grafiğinde Y ekseni, kullanıcı posta kutularının sayısıdır.  <br/>  **Depolama** grafiğinde, Y ekseni kuruluşunuzdaki kullanıcı posta kutuları tarafından kullanılmakta olan depolama miktarıdır.  <br/>  **Kota** grafiğinde Y ekseni, her depolama kotasındaki kullanıcı posta kutularının sayısıdır.  <br/>  Posta Kutusu ve Depolama grafiklerindeki X ekseni, söz konusu rapora ait seçilen tarih aralığıdır.  <br/>  Kota grafiklerindeki X ekseni kota kategorisidir. |
|7.  |Göstergede bir öğe seçerek grafiklere filtre ekleyebilirsiniz. |
|8.  | Tabloda, kullanıcı başına posta kutusu kullanımının dökümünü gösterir. Tabloya başka sütunlar da ekleyebilirsiniz.  <br/> **Kullanıcı adı**, kullanıcının e-posta adresidir.  <br/> **Görünen Ad**, kullanıcının tam adıdır.  <br/> **Silinmiş**, geçerli durumu silinmiş olan ancak raporun raporlama döneminin bir bölümünde etkin olan posta kutusuna karşılık gelir.  <br/> **Silinme tarihi**, posta kutusunun silindiği tarihtir.  <br/> **Oluşturma tarihi**, posta kutusunun oluşturulduğu tarihtir.  <br/> **Son etkinlik tarihi**, posta kutusunda e-posta gönderme veya alma etkinliğinin gerçekleştiği tarihe karşılık gelir.  <br/> **Öğe sayısı**, posta kutusundaki öğelerin toplam sayısına karşılık gelir.  <br/> **Kullanılan depolama alanı (MB)**, kullanılan toplam depolamaya karşılık gelir.  <br/> **Silinmiş Öğe Sayısı** , posta kutusunda silinen öğelerin toplam sayısına başvurur. <br/> **Silinmiş Öğe Boyutu (MB),** posta kutusudaki tüm silinmiş öğelerin toplam boyutuna göre ifade eder. <br/> **Sorun uyarısı kotası (MB)**, posta kutusu sahibinin depolama kotasını doldurmak üzere olduğuna ilişkin uyarı alacağı depolama sınırına karşılık gelir.  <br/> **Göndermeyi yasaklama kotası (MB)**, posta kutusunun artık e-posta gönderemeyeceği depolama sınırına karşılık gelir.  <br/> **Göndermeyi/almayı yasaklama kotası (MB)**, posta kutusunun artık e-posta gönderemeyeceği veya alamayacağı depolama sınırına karşılık gelir.  <br/> **Kurtarılabilir Öğe Kotası (MB),** posta kutusu artık e-postaları silemez durumda olduğunda posta kutusunda kurtarılabilir (silinmiş) öğelerin depolama sınırına başvurur.  <br/> **Arşiv özelliği** , posta kutusunun çevrimiçi arşivi etkinleştir olup olduğunu gösterir.  <br/>  Kuruluşunuzun ilkeleri nedeniyle kişisel kullanıcı bilgilerinin bulunduğu raporları görüntüleyemiyorsanız bu raporların gizlilik ayarını değiştirebilirsiniz. Raporlarda **yer alan Etkinlik Raporları bölümünde Yer** alan [raporlarda kullanıcı ayrıntılarını gizleme Microsoft 365 yönetim merkezi](activity-reports.md). |
|9.  |Raporda **sütun eklemek** veya kaldırmak için Sütunları seç'i seçin.  <br/> :::image type="content" alt-text="Posta kutusu kullanım raporu - Sütunları seçin." source="../../media/ea3d0b18-6ac6-41b0-9bb9-4844f040ea75.png":::|
|10. |Ayrıca, Dışarı Aktar bağlantısını seçerek rapor Excel .csv bir çalışma dosyasına da **aktarabilirsiniz**. |
|||
