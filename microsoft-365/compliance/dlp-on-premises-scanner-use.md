---
title: Şirket Microsoft 365 kaybı önlemeyi kullanma
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: how-to
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: Yerinde verileri taramak ve şirket içi dosya paylaşımları ile şirket içi dosya paylaşımları ve belge kitaplıkları için koruyucu eylemler uygulamak için şirket içi tarayıcıda Microsoft 365 kaybı önlemeyi SharePoint öğrenin.
ms.openlocfilehash: d726bfccf7dff2e95e3ccf996544f1db26bf09a2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988167"
---
# <a name="use-the-microsoft-365-data-loss-prevention-on-premises-scanner"></a>Şirket Microsoft 365 kaybı önlemeyi kullanma

DLP şirket içi özelliklerini ve bunların DLP ilkeleriyle nasıl ortaya çıkar olduklarını tanımanıza yardımcı olmak için, takip etmek için bazı senaryoları bir araya getirdik.

> [!IMPORTANT]
> Bu DLP şirket içi senaryoları, DLP ilkelerini oluşturmaya ve ayarlamaya yönelik resmi yordamlar değildir. Genel durumlarda DLP ilkeleriyle çalışman gerekirken aşağıdaki konulara bakın:
>
> - [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)
> - [Varsayılan DLP ilkesiyle çalışmaya başlama](get-started-with-the-default-dlp-policy.md)
> - [Şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md)
> - [DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md)

### <a name="scenario-discover-files-matching-dlp-rules"></a>Senaryo: DLP kurallarıyla eşleşen dosyaları bulma

DLP şirket içi tarayıcıdan gelen veriler çeşitli alanlarda yer alıyor

#### <a name="activity-explorer"></a>Etkinlik gezgini

 Şirket içi için Microsoft DLP, DLP kuralı eşleşmelerini algılar ve Bunları Etkinlik [Gezgini'ne raporlar](https://compliance.microsoft.com/dataclassification?viewid=activitiesexplorer).

#### <a name="microsoft-365-audit-log"></a>Microsoft 365 günlüğü

DLP kuralı eşleşmeleri Denetim günlüğü kullanıcı arabiriminde kullanılabilir. Bkz. [](search-the-audit-log-in-security-and-compliance.md) Denetim günlüğünü uyumluluk merkezinde arama veya [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) PowerShell ile erişilebilir.

#### <a name="aip"></a>AIP

Bulma verileri, yerel bir raporda csv biçiminde kullanılabilir ve bu veriler şu altında depolanır:

**%localappdata%\Microsoft\MSIP\Scanner\Reports\DetailedReport_%timestamp%.csv raporu**.

 Aşağıdaki sütunları bakın:

- DLP Modu
- DLP Durumu
- DLP Açıklaması
- DLP Kuralı Adı
- DLP Eylemleri
- Sahip
- Geçerli NTFS İzinleri (SDDL)
- NTFS İzinleri (SDDL) uygulanmış
- NTFS izin türü

### <a name="scenario-enforce-dlp-rule"></a>Senaryo: DLP kuralını zorunlu kılın

Taranan dosyalarda DLP kurallarını zorunlu kılınacak şekilde uygulamak için, zorlamanın hem AIP'daki içerik tarama işi hem de DLP'nin ilke düzeyinde etkinleştirilmesi gerekir.

#### <a name="configure-dlp-to-enforce-policy-actions"></a>DLP'yi ilke eylemlerini zorunlu olacak şekilde yapılandırma

1. Veri [kaybı önleme sayfasını](https://compliance.microsoft.com/datalossprevention?viewid=policies) açın ve AIP'de yapılandırmış olduğunuz şirket içi konum depolarını hedef alan DLP ilkesi seçin.
2. İlkeyi düzenleyin.
3. **İlkeyi test edin veya aç sayfasında** Evet, hemen **aç'ı seçin**.

## <a name="see-also"></a>Ayrıca bkz.

- [DLP şirket içi tarayıcı hakkında bilgi](dlp-on-premises-scanner-learn.md)
- [DLP şirket içi tarayıcı ile çalışmaya başlama](dlp-on-premises-scanner-get-started.md)
- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)
- [DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md)
- [Etkinlik gezgini ile çalışmaya başlama](data-classification-activity-explorer.md)
