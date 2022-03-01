---
title: MRS hizmet uyarıları
ms.author: markjjo
author: markjjo
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
description: Kurumdaki posta kutusu geçiş isteklerinde gecikmeleri izlemek için posta kutusu geçiş hizmeti uyarılarını kullanın.
ms.openlocfilehash: 25c569030bd5da914dc6eb7ec0e58ebadfe4d766
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63028451"
---
# <a name="service-alerts-for-mrs-source-delays-in-exchange-online-monitoring"></a>Sistem izlemesinde MRS kaynak gecikmeleri için Exchange Online uyarıları

Posta Kutusu Çoğaltma Hizmeti (MRS) kaynak gecikme hizmeti uyarıları, kiracı tarafında (geçiş kaynağı) yer alan ve kiracı tarafındaki (geçiş kaynağı) posta kutusu geçişlerini geciktiren depolama kısıtlamaları veya yüksek işlemcili kullanım sorunları hakkında sizi Microsoft 365 sağlar. Bu hizmet uyarıları, bu sorunları çözmenize yardımcı olacak Microsoft kaynaklarının bağlantılarını da içerir.

Bu hizmet uyarıları aşağıdaki Microsoft 365 yönetim merkezi. Bu hizmet uyarılarını görüntülemek için <a href="https://go.microsoft.com/fwlink/p/?linkid=842900" target="_blank">**HealthService health (HealthService**</a> >  health > ) Exchange Online sonra da **Etkin sorunlar sekmesine** tıklayın.

## <a name="what-do-these-service-alerts-indicate"></a>Bu hizmet uyarıları neleri gösteriyor?

Bu hizmet uyarısı, kurumdaki posta kutusu geçişleri için olası gecikmeler konusunda sizi bilgilir. Bu, ormanlar arası geçişleri, ekleme geçişlerini ve işe kapatma geçişlerini içerir. Hizmet uyarısı, kurumdaki geçerli geçişler hakkında bilgi içeren bir tablo içerir. Geçiş gecikmeleri hakkında bilgi edinen bir tablo örneği aşağıda verilmektedir.

| BatchName | ExchangeGuid | RequestGuid | DelayReason |QueuedHours | DelayInHours | SourceServer | RemoteDatabaseName |
|:---------|:---------|:---------|:---------|:---------|:---------|:---------|:---------|
|MRS Geçişi|246c21f7-ca3c-4bba-ab5d-23456558c52a|3d7fab16-7d8e-4c81-a849-e0795054292a|DiskLatency|35.2|27.3|RD1GBL01EXCH003|GBL01EDAG001-db002|
|MRS Kiracı İzleme|21e9a608-78c3-44ef-a4dd-d5e7222aae82|9974aeb4-2aa4-4a2c-aeb6-d94d78cc25c9|DiskLatency|0.4|0.9|RD1GBL01EXCH010|GBL01EDAG010-db003|

Aşağıdaki listede, önceki örnekteki her sütun açık başlığının bir örneği yer almaktadır.

- **BatchName**: Geçiş işinin benzersiz adı.

- **ExchangeGuid**: Geçirilirken kullanıcı posta kutusunun genel benzersiz tanımlayıcısı (GUID).

- **İstekYinesi**: Geçiş isteğinin GUID'si.

- **DelayReason**: Gecikmeli geçişin nedeni.

- **Sırada Bekleme** Süresi: Geçişin sıraya alınan ve bekleyen süresi.

- **DelayInHours**: Geçişin geciktirme süresi.

- **Kaynak Sunucusu**: Geçişin kaynaklandığı şirket içi sunucudur.

- **RemoteDatabaseName**: Geçişin kaynaklandığı veritabanı adı.

## <a name="more-information"></a>Daha fazla bilgi

MRS ve posta kutusu geçişleri hakkında daha fazla bilgi için aşağıdaki makalelere bakın:

- [Posta kutusu posta kutusu Exchange](/exchange/recipients/mailbox-moves)

- [Microsoft 365 performansını Office 365 en iyi yöntemleri uygulama ve yükseltme](/exchange/mailbox-migration/office-365-migration-best-practices)

- [Posta kutusu geçiş performansı çözümlemesi](https://techcommunity.microsoft.com/t5/exchange-team-blog/mailbox-migration-performance-analysis/ba-p/587134)

- [Yavaş geçiş sorunlarını giderme](https://techcommunity.microsoft.com/t5/exchange-team-blog/troubleshooting-slow-migrations/ba-p/1795706)

- [Birden çok e-posta hesabını başka bir hesaba Microsoft 365](/exchange/mailbox-migration/mailbox-migration)
