---
title: Posta akışı panosunda SMTP Kimlik Doğrulaması istemcileri içgörü ve raporu
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.localizationpriority: medium
ms.assetid: ''
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler, kuruluşlarında e-posta iletilerini göndermek için kimliği doğrulanmış SMTP (SMTP AUTH) kullanan e-posta gönderenleri izlemek için Güvenlik & Uyumluluk Merkezi'nde Posta akışı panosunda SMTP Kimlik Doğrulaması içgörü ve raporunu kullanmayı öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e21e9fae80880b479070b1920379b925bf7074c7
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63681138"
---
# <a name="smtp-auth-clients-insight-and-report-in-the-security--compliance-center"></a>Güvenlik ve Uyumluluk Merkezi'nde SMTP Kimlik Doğrulaması & raporu

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Güvenlik [& Uyumluluk](https://protection.office.com) Merkezi'nde Posta akışı [](mail-flow-insights-v2.md) panosunda ve ilişkili [SMTP Auth](#smtp-auth-clients-report) istemcileri raporunda **,** SMTP Auth istemcileri içgörüleri, kuruluşta kullanıcılar veya sistem hesapları tarafından SMTP AUTH istemci gönderim protokolünün kullanımını vurgular. Yalnızca Temel kimlik doğrulamasını kullanan bu eski protokol (uç nokta smtp.office365.com) sunar ve güvenliği tehlikeye atılmış hesapların e-posta göndermek için kullanımına duyarlıdır. Bilgi ve rapor, SMTP AUTH e-posta gönderimlerine olağan dışı etkinlikleri denetlemenizi sağlar. Smtp AUTH kullanan istemciler veya cihazlar için TLS kullanım verilerini de gösterir.

Widget, son 7 gün içinde SMTP Kimlik Doğrulaması protokolünü kullanan kullanıcıların veya hizmet hesaplarının sayısını gösterir.

![Güvenlik ve Uyumluluk Merkezi'nin Posta akışı panosunda SMTP & widget'ı.](../../media/mfi-smtp-auth-clients-report-widget.png)

Widget'ta ileti sayısına tıklarsanız, **bir SMTP Auth istemcileri** açılır öğesi görüntülenir. Uçarak çıkış, TLS kullanımı ve geçen hafta için hacimlerin toplu bir görünümünü sağlar.

![Posta akışı panosunda SMTP Auth istemcileri widget'ine tık olduktan sonra ayrıntılar çıktısı.](../../media/mfi-smtp-auth-clients-report-details.png)

Bir sonraki bölümde **açıklandığı gibi SMTP Kimlik** Doğrulaması istemcileri rapor bağlantısına tıklayarak SMTP Kimlik Doğrulaması istemcileri raporuna gidebilirsiniz.

## <a name="smtp-auth-clients-report"></a>SMTP Kimlik Doğrulaması istemcileri raporu

### <a name="report-view-for-the-smtp-auth-clients-report"></a>SMTP Kimlik Doğrulaması istemcileri raporu için rapor görünümü

Varsayılan olarak, rapor son 7 günle ilgili verileri gösterir ancak son 90 gün için veriler kullanılabilir.

Genel bakış bölümü aşağıdaki grafikleri içerir:

- **Verileri görüntüleme:** Birim gönderme: Varsayılan olarak grafikte, tüm etki alanlarından gönderilen SMTP Auth istemci iletilerinin sayısı görüntülenir (Verileri **göster:** Tüm gönderen etki alanları varsayılan olarak seçilidir). Verileri göster'i tıklatarak ve açılan listeden gönderen etki alanını  seçerek, sonuçları belirli bir gönderen etki alanı olarak filtreebilirsiniz. Belirli bir veri noktasını (gün) vurgularsanız, iletilerin sayısı gösterilir.

  ![Güvenlik ve Uyumluluk Merkezi'nde SMTP Auth istemcileri raporunda ses & gönderme.](../../media/mfi-smtp-auth-clients-report-sending-volume-view.png)

- **Verileri görüntüleme: TLS Kullanımı**: Grafik, seçilen dönem boyunca tüm SMTP Kimlik Doğrulaması istemci iletileri için TLS kullanımının yüzdesini gösterir. Bu grafik, TLS'nin daha eski sürümlerini kullanmaya devam olan kullanıcıları ve sistem hesaplarını tanımlamanıza ve bu hesaplar üzerinde eyleme geçebilirsiniz.

  ![Güvenlik ve Uyumluluk Merkezi'nde SMTP Kimlik Doğrulaması istemcileri raporunda TLS & görünümü.](../../media/mfi-smtp-auth-clients-report-tls-usage-view.png)

Rapor görünümünde **Filtreler'e** tıklarsanız, Başlangıç tarihi ve Bitiş tarihi **ile bir tarih** aralığı **belirtebilirsiniz**.

Bir **e-posta** iletisinde raporun daha ayrıntılı bir sürümünü almak için Rapor isteği'ne tıklayın. Tarih aralığını ve raporu alacak alıcıları belirtebilirsiniz.

### <a name="details-table-view-for-the-smtp-auth-clients-report"></a>SMTP Kimlik Doğrulaması istemcileri raporu için ayrıntılar tablosu görünümü

Ayrıntıları görüntüle **tablosu'nun üzerine** tıklarsanız, gösterilen bilgiler üzerinde şu bilgilere bakabilirsiniz:

- **Verileri görüntüleme: Ses düzeyi gönderme**: Tabloda aşağıdaki bilgiler gösterilir:

  - **Gönderen adresi**
  - **İleti sayısı**

  Bir satır seçerek çıkışta aynı ayrıntılar gösterilir.

- **Verileri görüntüleme: TLS Kullanımı**: Tabloda aşağıdaki bilgiler gösterilir:

  - **Gönderen adresi**
  - **TLS1,0%**<sup>\*</sup>
  - **TLS1,%1**<sup>\*</sup>
  - **TLS1,%2**<sup>\*</sup>
  - **İleti sayısı**

  <sup>\*</sup> Bu sütun gönderenden gelen iletilerin yüzdesini ve sayısını gösterir.

Ayrıntılar tablosu **görünümünde Filtreler'e** tıklarsanız, Başlangıç tarihi ve Bitiş tarihi ile bir **tarih** aralığı **belirtebilirsiniz**.

Bir satır seçersiniz, uçarak çıkışta benzer ayrıntılar gösterilir:

![SMTP Kimlik Doğrulaması istemcileri raporunda TLS kullanım görünümünün ayrıntılar tablosundan ayrıntılar çıktısı.](../../media/mfi-smtp-auth-clients-report-tls-usage-view-view-details-table-details.png)

Bir **e-posta** iletisinde raporun daha ayrıntılı bir sürümünü almak için Rapor isteği'ne tıklayın. Tarih aralığını ve raporu alacak alıcıları belirtebilirsiniz.

Raporlar görünümüne geri dönmek için Raporu **görüntüle'yi tıklatın**.

## <a name="related-topics"></a>İlgili konular

Posta akışı panosunda yer alan diğer içgörüler hakkında bilgi için, Güvenlik ve Uyumluluk Merkezi'nde [Posta & bakın](mail-flow-insights-v2.md).
