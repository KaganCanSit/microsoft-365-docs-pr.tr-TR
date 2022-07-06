---
title: Şirket içi tarayıcıda veri kaybını önlemeyi kullanma
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
description: Bekleyen verileri taramak ve şirket içi dosya paylaşımları ile şirket içi SharePoint klasörleri ve belge kitaplıkları için koruyucu eylemler uygulamak için şirket içi veri kaybı önleme tarayıcısını kullanmayı öğrenin.
ms.openlocfilehash: ae5ffce9e664ada6e7476bb02b40f4a5c279d441
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624189"
---
# <a name="use-the-data-loss-prevention-on-premises-scanner"></a>Veri kaybı önleme şirket içi tarayıcısını kullanma

Microsoft Purview Veri Kaybı Önleme şirket içi özellikleri ve bunların DLP ilkelerinde nasıl ortaya çıkaracağınız hakkında bilgi sahibi olmanıza yardımcı olmak için izlemeniz gereken bazı senaryoları bir araya topladık.

> [!IMPORTANT]
> Bu DLP şirket içi senaryoları, DLP ilkelerini oluşturmak ve ayarlamak için resmi prosedürler değildir. Genel durumlarda DLP ilkeleriyle çalışmanız gerektiğinde aşağıdaki konulara bakın:
>
> - [Veri kaybı önleme hakkında daha fazla bilgi edinme](dlp-learn-about-dlp.md)
> - [Varsayılan DLP ilkesini kullanmaya başlama](get-started-with-the-default-dlp-policy.md)
> - [Bir şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md)
> - [Bir DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md)

### <a name="scenario-discover-files-matching-dlp-rules"></a>Senaryo: DLP kurallarıyla eşleşen dosyaları bulma

DLP şirket içi tarayıcısından alınan veriler çeşitli alanlarda ortaya çıkar

#### <a name="activity-explorer"></a>Etkinlik gezgini

 Şirket içi için Microsoft DLP, DLP kuralı eşleşmelerini algılar ve bunları [Etkinlik Gezgini'ne](https://compliance.microsoft.com/dataclassification?viewid=activitiesexplorer) bildirir.

#### <a name="microsoft-365-audit-log"></a>Microsoft 365 Denetim günlüğü

DLP kuralı eşleşmeleri Denetim günlüğü kullanıcı arabiriminde kullanılabilir, bkz[. Microsoft Purview uyumluluk portalı denetim günlüğünde arama](search-the-audit-log-in-security-and-compliance.md) yapma veya [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) PowerShell tarafından erişilebilir.

#### <a name="aip"></a>AIP

Bulma verileri, aşağıdakiler altında depolanan csv biçimindeki bir yerel raporda kullanılabilir:

**%localappdata%\Microsoft\MSIP\Scanner\Reports\DetailedReport_%timestamp%.csv raporu**.

 Aşağıdaki sütunları arayın:

- DLP Modu
- DLP Durumu
- DLP Açıklaması
- DLP Kuralı Adı
- DLP Eylemleri
- Sahibi
- Geçerli NTFS İzinleri (SDDL)
- Uygulanan NTFS İzinleri (SDDL)
- NTFS izin türü

### <a name="scenario-enforce-dlp-rule"></a>Senaryo: DLP kuralını zorunlu kılma

Taranan dosyalar üzerinde DLP kurallarını zorunlu kılmak istiyorsanız, hem AIP'deki içerik tarama işinde hem de DLP'deki ilke düzeyinde zorlama etkinleştirilmelidir.

#### <a name="configure-dlp-to-enforce-policy-actions"></a>İlke eylemlerini zorunlu kılmak için DLP'yi yapılandırma

1. [Veri kaybı önleme sayfasını](https://compliance.microsoft.com/datalossprevention?viewid=policies) açın ve AIP'de yapılandırdığınız şirket içi konum depolarını hedefleyen DLP ilkesini seçin.
2. İlkeyi düzenleyin.
3. **İlkeyi test et veya aç** sayfasında **Evet, hemen aç'ı** seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [DLP şirket içi tarayıcısı hakkında bilgi edinin](dlp-on-premises-scanner-learn.md)
- [DLP şirket içi tarayıcıyı kullanmaya başlama](dlp-on-premises-scanner-get-started.md)
- [Veri kaybı önleme hakkında daha fazla bilgi edinme](dlp-learn-about-dlp.md)
- [Bir DLP ilkesi oluşturma, test etme ve ayarlama](create-test-tune-dlp-policy.md)
- [Etkinlik gezginini kullanmaya başlama](data-classification-activity-explorer.md)
