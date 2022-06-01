---
title: MRS hizmeti uyarıları
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: ''
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
search.appveyor:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- NOCSH
description: Kuruluşunuzdaki posta kutusu geçiş isteklerindeki gecikmeleri izlemek için posta kutusu geçiş hizmeti önerilerini kullanın.
ms.openlocfilehash: fe6f60b75fb7d27781d442faf82ff981ac54808a
ms.sourcegitcommit: aff1732dfa21e9283b173d8e5ca5bcbeeaaa26d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2022
ms.locfileid: "65810747"
---
# <a name="service-advisories-for-mrs-source-delays-in-exchange-online-monitoring"></a>Exchange Online izlemedeki MRS kaynak gecikmeleri için hizmet önerileri

Posta Kutusu Çoğaltma Hizmeti (MRS) kaynak gecikme hizmeti önerileri, kiracı tarafında (geçiş kaynağı) Microsoft 365 kuruluşunuzda posta kutusu geçişlerini geciktirebilecek depolama sınırlamaları veya yüksek işlemci kullanımı sorunları hakkında sizi bilgilendirmektedir. Bu hizmet önerileri, bu sorunları çözmenize yardımcı olmak için Microsoft kaynaklarına bağlantılar da içerir.

Bu hizmet önerileri Microsoft 365 yönetim merkezi görüntülenir. Bu hizmet önerilerini görüntülemek için **Sistem Durumu** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**Hizmet durumu Exchange Online'na**</a> >  gidin ve **Etkin sorunlar** sekmesine tıklayın.

## <a name="what-do-these-service-advisories-indicate"></a>Bu hizmet önerileri neleri gösteriyor?

Bu hizmet önerisi, kuruluşunuzdaki posta kutusu geçişlerinde olası gecikmeler konusunda sizi bilgilendirmektedir. Buna ormanlar arası geçişler, ekleme geçişleri ve çıkarma geçişleri dahildir. Hizmet önerisi, kuruluşunuzdaki geçerli geçişler hakkında bilgi içeren bir tablo içerir. Geçiş gecikmeleri hakkında bilgi içeren bir tablo örneği aşağıda verilmiştir.

| BatchGuid | ExchangeGuid | RequestGuid | DelayReason |QueuedHours | DelayInHours | Sourceserver | RemoteDatabaseName |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|12345678-1234-1234-1234-1234567891011|246c21f7-ca3c-4bba-ab5d-23456558c52a|3d7fab16-7d8e-4c81-a849-e0795054292a|DiskLatency|35.2|27.3|RD1GBL01EXCH003|GBL01EDAG001-db002|
|87654321-4321-4321-4321-1101987654321|21e9a608-78c3-44ef-a4dd-d5e7222aae82|9974aeb4-2aa4-4a2c-aeb6-d94d78cc25c9|DiskLatency|0.4|0.9|RD1GBL01EXCH010|GBL01EDAG010-db003|

Aşağıdaki listede, önceki örnekteki her sütun açıklanmaktadır.

- **BatchGuid**: Geçiş işi için benzersiz GUID.

- **ExchangeGuid**: Geçirilmekte olan kullanıcı posta kutusunun genel benzersiz tanımlayıcısı (GUID).

- **RequestGuid**: Geçiş isteğinin GUID'i.

- **DelayReason**: Gecikmeli geçişin nedeni.

- **QueueHours**: Geçişin kuyruğa alınıp bekleme süresi.

- **DelayInHours**: Geçişin gecikme süresi.

- **SourceServer**: Geçişin kaynaklandığı şirket içi sunucu.

- **RemoteDatabaseName**: Geçişin kaynaklandığı veritabanı adı.

## <a name="more-information"></a>Daha fazla bilgi

MRS ve posta kutusu geçişleri hakkında daha fazla bilgi için aşağıdaki makalelere bakın:

- [posta kutusu Exchange](/exchange/recipients/mailbox-moves)

- [Geçiş performansını ve en iyi yöntemlerini Microsoft 365 ve Office 365](/exchange/mailbox-migration/office-365-migration-best-practices)

- [Posta kutusu geçişi performans analizi](https://techcommunity.microsoft.com/t5/exchange-team-blog/mailbox-migration-performance-analysis/ba-p/587134)

- [Yavaş geçiş sorunlarını giderme](https://techcommunity.microsoft.com/t5/exchange-team-blog/troubleshooting-slow-migrations/ba-p/1795706)

- [Birden çok e-posta hesabını Microsoft 365 geçirmenin yolları](/exchange/mailbox-migration/mailbox-migration)
