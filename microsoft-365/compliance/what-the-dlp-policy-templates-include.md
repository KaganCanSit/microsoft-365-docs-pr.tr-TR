---
title: DLP ilke şablonları neleri içerir?
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: reference
f1_keywords:
- ms.o365.cc.DLPNewPolicyFromTemplate
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
recommendations: false
description: Microsoft Purview uyumluluk portalı veri kaybı önleme (DLP) ilkesi şablonlarının neler içerdiğini öğrenin.
ms.openlocfilehash: 145f5b2a180023811afa8b5795bfa8b9d24f82f5
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753513"
---
# <a name="what-the-dlp-policy-templates-include"></a>DLP ilke şablonları neler içerir?

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview uyumluluk portalı Microsoft Purview Veri Kaybı Önleme (DLP), ABD Sağlık Sigortası Yasası'na (HIPAA), ABD Gramm-Leach-Bliley Yasası'na (GLBA) tabi hassas bilgileri korumanıza yardımcı olmak gibi yaygın uyumluluk gereksinimlerini karşılayan kullanıma hazır ilke şablonları içerir veya ABD Vatanseverlik Yasası. Bu makalede tüm ilke şablonları, aradıkları hassas bilgi türleri ve varsayılan koşulların ve eylemlerin ne olduğu listelenir. Bu makale, her ilke şablonunun nasıl yapılandırıldığına ilişkin tüm ayrıntıları içermez; bunun yerine makale, hangi şablonun senaryonuz için en iyi başlangıç noktası olduğuna karar vermenize yardımcı olacak kadar bilgi sunar. Bu ilke şablonlarını özel gereksinimlerinizi karşılayacak şekilde özelleştirebileceğinizi unutmayın.
  
## <a name="australia-financial-data"></a>Avustralya Finansal Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|Avustralya Finansal: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  SWIFT Kodu - En az sayı 1, Maksimum sayı 9  <br/>  Avustralya Vergi Dosya Numarası - En az sayı 1, Maksimum sayı 9  <br/>  Avustralya Banka Hesap Numarası - En az sayı 1, Maksimum sayı 9  <br/>  Kredi Kartı Numarası - En az sayı 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Australia Financial: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  SWIFT Kodu - En az 10, Maksimum sayı 500  <br/>  Avustralya Vergi Dosya Numarası - En az sayı 10, Maksimum sayı 500  <br/>  Avustralya Banka Hesap Numarası - En az 10, Maksimum sayı 500  <br/>  Kredi Kartı Numarası - En az 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="australia-health-records-act-hrip-act"></a>Avustralya Sağlık Kayıtları Yasası (HRIP Yasası)

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|Avustralya HRIP: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Avustralya Vergi Dosya Numarası - En az sayı 1, Maksimum sayı 9  <br/>  Avustralya Tıbbi Hesap Numarası - En az sayı 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Avustralya HRIP: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Avustralya Vergi Dosya Numarası - En az sayı 10, Maksimum sayı 500  <br/>  Avustralya Tıbbi Hesap Numarası - En az sayı 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="australia-personally-identifiable-information-pii-data"></a>Avustralya Kişisel Bilgiler (PII) Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|Avustralya PII: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Avustralya Vergi Dosya Numarası - En az sayı 1, Maksimum sayı 9  <br/>  Avustralya Sürücü Lisans Numarası - En az 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Avustralya PII: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Avustralya Vergi Dosya Numarası - En az sayı 10, Maksimum sayı 500  <br/>  Avustralya Sürücü Belgesi Numarası - En az 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="australia-privacy-act"></a>Avustralya Gizlilik Yasası

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|Avustralya Gizliliği: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Avustralya Sürücü Lisans Numarası - En az 1, Maksimum sayı 9  <br/>  Avustralya Pasaport Numarası - En az sayı 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Avustralya Gizliliği: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Avustralya Sürücü Belgesi Numarası - En az 10, Maksimum sayı 500  <br/>  Avustralya Pasaport Numarası - En az 10, Maksimum sayı 500 <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="canada-financial-data"></a>Kanada Finansal Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|Kanada Finansal Verileri: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası - En az sayı 1, Maksimum sayı 9  <br/>  Canada Bank Account Number - Min count 1, Max count 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Kanada Finansal Verileri: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası - En az 10, Maksimum sayı 500  <br/>  Canada Bank Account Number - Min count 10, Max count 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="canada-health-information-act-hia"></a>Kanada Sağlık Bilgileri Yasası (HIA)

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|Kanada HIA: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Pasaport Numarası - En az sayı 1, Maksimum sayı 9  <br/>  Kanada Sosyal Sigorta Numarası - En az sayı 1, Maksimum sayı 9  <br/>  Kanada Sistem Sağlığı Hizmeti Sayısı - En az sayı 1, Maksimum sayı 9  <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) - Min count 1, Max count 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Kanada HIA: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Pasaport Numarası - En az sayı 10, Maksimum sayı 500  <br/>  Kanada Sosyal Sigorta Numarası - Min count 10, Max count 500  <br/>  Kanada Sistem Sağlığı Hizmeti Sayısı - En az 10, Maksimum sayı 500  <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) - Min count 10, Max count 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="canada-personal-health-act-phipa---ontario"></a>Kanada Kişisel Sağlık Yasası (PHIPA) - Ontario

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|Kanada PHIPA: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Pasaport Numarası - En az sayı 1, Maksimum sayı 9  <br/>  Kanada Sosyal Sigorta Numarası - En az sayı 1, Maksimum sayı 9  <br/>  Kanada Sistem Sağlığı Hizmeti Sayısı - En az sayı 1, Maksimum sayı 9  <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) - Min count 1, Max count 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Kanada PHIPA: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Pasaport Numarası - En az sayı 10, Maksimum sayı 500  <br/>  Kanada Sosyal Sigorta Numarası - Min count 10, Max count 500  <br/>  Kanada Sistem Sağlığı Hizmeti Sayısı - En az 10, Maksimum sayı 500  <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) - Min count 10, Max count 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="canada-personal-health-information-act-phia---manitoba"></a>Kanada Kişisel Sağlık Bilgileri Yasası (PHIA) - Manitoba

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|Kanada PHIA: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Sosyal Sigorta Numarası - En az sayı 1, Maksimum sayı 9  <br/>  Kanada Sistem Sağlığı Hizmeti Sayısı - En az sayı 1, Maksimum sayı 9  <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) - Min count 1, Max count 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Kanada PHIA: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Sosyal Sigorta Numarası - Min count 10, Max count 500  <br/>  Kanada Sistem Sağlığı Hizmeti Sayısı - En az 10, Maksimum sayı 500 <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) - Min count 10, Max count 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="canada-personal-information-protection-act-pipa"></a>Kanada Kişisel Information Protection Yasası (PIPA)

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|Kanada PIPA: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Pasaport Numarası - En az sayı 1, Maksimum sayı 9  <br/>  Kanada Sosyal Sigorta Numarası - En az sayı 1, Maksimum sayı 9  <br/>  Kanada Sistem Sağlığı Hizmeti Sayısı - En az sayı 1, Maksimum sayı 9  <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) - Min count 1, Max count 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Kanada PIPA: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Pasaport Numarası - En az sayı 10, Maksimum sayı 500  <br/>  Kanada Sosyal Sigorta Numarası - Min count 10, Max count 500  <br/>  Kanada Sistem Sağlığı Hizmeti Sayısı - En az 10, Maksimum sayı 500  <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) - Min count 10, Max count 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="canada-personal-information-protection-act-pipeda"></a>Kanada Kişisel Information Protection Yasası (PIPEDA)

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|Kanada PIPEDA: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Sürücü Belgesi Numarası - En az 1, Maksimum sayı 9  <br/>  Canada Bank Account Number - Min count 1, Max count 9  <br/>  Kanada Pasaport Numarası - En az sayı 1, Maksimum sayı 9  <br/>  Kanada Sosyal Sigorta Numarası - En az sayı 1, Maksimum sayı 9  <br/>  Kanada Sistem Sağlığı Hizmeti Sayısı - En az sayı 1, Maksimum sayı 9  <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) - Min count 1, Max count 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Kanada PIPEDA: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Sürücü Belgesi Numarası - En az 10, Maksimum sayı 500 <br/>  Canada Bank Account Number - Min count 10, Max count 500 <br/>  Kanada Pasaport Numarası - En az sayı 10, Maksimum sayı 500  <br/>  Kanada Sosyal Sigorta Numarası - Min count 10, Max count 500  <br/>  Kanada Sistem Sağlığı Hizmeti Sayısı - En az 10, Maksimum sayı 500  <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) - Min count 10, Max count 500 <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="canada-personally-identifiable-information-pii-data"></a>Kanada Kişisel Bilgiler (PII) Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|Kanada PII: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Sürücü Belgesi Numarası - En az 1, Maksimum sayı 9  <br/>  Canada Bank Account Number - Min count 1, Max count 9  <br/>  Kanada Pasaport Numarası - En az sayı 1, Maksimum sayı 9  <br/>  Kanada Sosyal Sigorta Numarası - En az sayı 1, Maksimum sayı 9  <br/>  Kanada Sistem Sağlığı Hizmeti Sayısı - En az sayı 1, Maksimum sayı 9  <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) - Min count 1, Max count 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Kanada PII: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Sürücü Belgesi Numarası - En az 10, Maksimum sayı 500  <br/>  Canada Bank Account Number - Min count 10, Max count 500  <br/>  Kanada Pasaport Numarası - En az sayı 10, Maksimum sayı 500  <br/>  Kanada Sosyal Sigorta Numarası - Min count 10, Max count 500  <br/>  Kanada Sistem Sağlığı Hizmeti Sayısı - En az 10, Maksimum sayı 500  <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) - Min count 10, Max count 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="france-data-protection-act"></a>Fransa Veri Koruma Yasası

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|Fransa DPA: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Fransa Ulusal Kimlik Kartı (CNI) - En az 1, Maksimum sayı 9  <br/>  Fransa Sosyal Güvenlik Numarası (INSEE) - Min count 1, Max count 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Fransa DPA: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Fransa Ulusal Kimlik Kartı (CNI) - En az 10, Maksimum sayı 500  <br/>  Fransa Sosyal Güvenlik Numarası (INSEE) - Min count 10, Max count 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="france-financial-data"></a>Fransa Finansal Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|France Financial: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası - En az sayı 1, Maksimum sayı 9  <br/>  AB Banka Kartı Numarası - En az sayı 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|France Financial: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası - En az 10, Maksimum sayı 500  <br/>  AB Banka Kartı Numarası - En az 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="france-personally-identifiable-information-pii-data"></a>Fransa Kişisel Bilgiler (PII) Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|Fransa PII: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Fransa Sosyal Güvenlik Numarası (INSEE) - Min count 1, Max count 9  <br/>  Fransa Sürücü Belgesi Numarası - Min sayı 1, Maksimum sayı 9  <br/>  Fransa Pasaport Numarası - En az sayı 1, Maksimum sayı 9  <br/>  Fransa Ulusal Kimlik Kartı (CNI) - En az 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Fransa PII: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Fransa Sosyal Güvenlik Numarası (INSEE) - Min count 10, Max count 500  <br/>  Fransa Sürücü Belgesi Numarası - En az 10, Maksimum sayı 500  <br/>  Fransa Pasaport Numarası - En az sayı 10, Maksimum sayı 500  <br/>  Fransa Ulusal Kimlik Kartı (CNI) - En az 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="general-data-protection-regulation-gdpr"></a>Genel Veri Koruma Yönetmeliği (GDPR)

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|Düşük hacimli AB Hassas içeriği bulundu  <br/> | İçerik hassas bilgiler içerir:  <br/>  AB Banka Kartı Numarası - En az sayı 1, Maksimum sayı 9  <br/>  AB Sürücü Belgesi Numarası - Min sayı 1, Maksimum sayı 9  <br/>  AB Ulusal Kimlik Numarası - En az sayı 1, Maksimum sayı 9  <br/>  AB Pasaport Numarası - En az sayı 1, Maksimum sayı 9  <br/>  AB Sosyal Güvenlik Numarası (SSN) veya Eşdeğer Kimlik - En az sayı 1, Maksimum sayı 9  <br/>  AB Vergi Kimlik Numarası (TIN) - En az sayı 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Yöneticiye olay raporları gönderme  <br/> |
|Yüksek hacimli AB Hassas içeriği bulundu  <br/> | İçerik hassas bilgiler içerir:  <br/>  AB Banka Kartı Numarası - En az 10, Maksimum sayı 500  <br/>  AB Sürücü Belgesi Numarası - En az 10, Maksimum sayı 500  <br/>  AB Ulusal Kimlik Numarası - En az sayı 10, Maksimum sayı 500  <br/>  AB Pasaport Numarası - En az sayı 10, Maksimum sayı 500  <br/>  AB Sosyal Güvenlik Numarası (SSN) veya Eşdeğer Kimlik - En az sayı 10, Maksimum sayı 500  <br/>  AB Vergi Tanımlama Numarası (TIN) - En az 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | Dış kullanıcılar için içeriğe erişimi kısıtlama  <br/>  Kullanıcılara e-posta ve ilke ipuçlarıyla bildirme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Yöneticiye olay raporları gönderme  <br/> |
   
## <a name="germany-financial-data"></a>Almanya Finansal Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|Almanya Finansal Verileri: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası - En az sayı 1, Maksimum sayı 9  <br/>  AB Banka Kartı Numarası - En az sayı 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Almanya Finansal Verileri: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası - En az 10, Maksimum sayı 500  <br/>  AB Banka Kartı Numarası - En az 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="germany-personally-identifiable-information-pii-data"></a>Almanya Kişisel Bilgiler (PII) Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|Almanya PII: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Alman Sürücü Belgesi Numarası - Min sayı 1, Maksimum sayı 9  <br/>  Alman Pasaport Numarası - En az sayı 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Almanya PII: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Alman Sürücü Belgesi Numarası - En az 10, Maksimum sayı 500  <br/>  Alman Pasaport Numarası - En az 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="israel-financial-data"></a>İsrail Finansal Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|İsrail Finansal Verileri: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  İsrail Banka Hesap Numarası - Min count 1, Max count 9  <br/>  SWIFT Kodu - En az sayı 1, Maksimum sayı 9  <br/>  Kredi Kartı Numarası - En az sayı 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|İsrail Finansal Verileri: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  İsrail Banka Hesap Numarası - En az 10, Maksimum sayı 500  <br/>  SWIFT Kodu - En az 10, Maksimum sayı 500  <br/>  Kredi Kartı Numarası - En az 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="israel-personally-identifiable-information-pii-data"></a>İsrail Kişisel Bilgiler (PII) Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|İsrail PII: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  İsrail Ulusal Kimliği - En az sayı 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|İsrail PII: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  İsrail Ulusal Kimliği - En az sayı 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="israel-protection-of-privacy"></a>İsrail'de Gizliliğin Korunması

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|İsrail Gizliliği: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  İsrail Ulusal Kimliği - En az sayı 1, Maksimum sayı 9  <br/>  İsrail Banka Hesap Numarası - Min count 1, Max count 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|İsrail Gizliliği: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  İsrail Ulusal Kimliği - En az sayı 10, Maksimum sayı 500  <br/>  İsrail Banka Hesap Numarası - En az 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="japan-financial-data"></a>Japonya Finansal Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|Japan Financial: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Japan Bank Account Number - Min count 1, Max count 9  <br/>  Kredi Kartı Numarası - En az sayı 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Japan Financial: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Japan Bank Account Number - Min count 10, Max count 500  <br/>  Kredi Kartı Numarası - En az 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="japan-personally-identifiable-information-pii-data"></a>Japonya Kişisel Bilgiler (PII) Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|Japonya PII: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Japonya Yerleşik Kayıt Numarası - En az sayı 1, Maksimum sayı 9  <br/>  Japonya Sosyal Sigorta Numarası (SIN) - Min count 1, Max count 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Japonya PII: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Japonya Yerleşik Kayıt Numarası - Min count 10, Max count 500  <br/>  Japonya Sosyal Sigorta Numarası (SIN) - Min count 10, Max count 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="japan-protection-of-personal-information"></a>Japonya Kişisel Bilgilerin Korunması

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|Japonya PPI: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Japonya Yerleşik Kayıt Numarası - En az sayı 1, Maksimum sayı 9  <br/>  Japonya Sosyal Sigorta Numarası (SIN) - Min count 1, Max count 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Japonya PPI: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Japonya Yerleşik Kayıt Numarası - Min count 10, Max count 500  <br/>  Japonya Sosyal Sigorta Numarası (SIN) - Min count 10, Max count 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="pci-data-security-standard-pci-dss"></a>PCI Veri Güvenliği Standardı (PCI DSS)

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|PCI DSS: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası - En az sayı 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|PCI DSS: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası - En az 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="saudi-arabia---anti-cyber-crime-law"></a>Suudi Arabistan - Siber Suçlarla Mücadele Yasası

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|Suudi Arabistan ACC: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  SWIFT Kodu - En az sayı 1, Maksimum sayı 9  <br/>  Uluslararası Bankacılık Hesap Numarası (IBAN) - En az 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Suudi Arabistan ACC: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  SWIFT Kodu - En az 10, Maksimum sayı 500  <br/>  Uluslararası Bankacılık Hesap Numarası (IBAN) - En az 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="saudi-arabia-financial-data"></a>Suudi Arabistan Finansal Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|Suudi Arabistan Finansal: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası - En az sayı 1, Maksimum sayı 9  <br/>  SWIFT Kodu - En az sayı 1, Maksimum sayı 9  <br/>  Uluslararası Bankacılık Hesap Numarası (IBAN) - En az 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Suudi Arabistan Finansal: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası - En az 10, Maksimum sayı 500  <br/>  SWIFT Kodu - En az 10, Maksimum sayı 500  <br/>  Uluslararası Bankacılık Hesap Numarası (IBAN) - En az 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="saudi-arabia-personally-identifiable-information-pii-data"></a>Suudi Arabistan Kişisel Bilgiler (PII) Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|Suudi Arabistan PII: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Suudi Arabistan Ulusal Kimliği - En az sayı 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Suudi Arabistan PII: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Suudi Arabistan Ulusal Kimliği - En az sayı 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="uk-access-to-medical-reports-act"></a>INGİLTERE. Tıbbi Raporlara Erişim Yasası

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|INGİLTERE. AMRA: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  INGİLTERE. Ulusal Sistem Sağlığı Hizmeti Sayısı - En az sayı 1, Maksimum sayı 9  <br/>  INGİLTERE. Ulusal Sigorta Numarası (NINO) - En az sayı 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|INGİLTERE. AMRA: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  INGİLTERE. Ulusal Sistem Sağlığı Hizmeti Sayısı - En az 10, Maksimum sayı 500  <br/>  INGİLTERE. Ulusal Sigorta Numarası (NINO) - En az 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="uk-data-protection-act"></a>INGİLTERE. Veri Koruma Yasası

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|INGİLTERE. DPA: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  INGİLTERE. Ulusal Sigorta Numarası (NINO) - En az sayı 1, Maksimum sayı 9  <br/>  Birleşik Krallık / Birleşik Krallık Pasaport Numarası - En az sayı 1, Maksimum sayı 9  <br/>  SWIFT Kodu - En az sayı 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|INGİLTERE. DPA: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  INGİLTERE. Ulusal Sigorta Numarası (NINO) - En az 10, Maksimum sayı 500  <br/>  Birleşik Krallık / Birleşik Krallık Pasaport Numarası - En az sayı 10, Maksimum sayı 500  <br/>  SWIFT Kodu - En az 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="uk-financial-data"></a>INGİLTERE. Finansal Veriler

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|INGİLTERE. Finansal: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası - En az sayı 1, Maksimum sayı 9  <br/>  AB Banka Kartı Numarası - En az sayı 1, Maksimum sayı 9  <br/>  SWIFT Kodu -Min sayı 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|INGİLTERE. Finansal: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası - En az 10, Maksimum sayı 500  <br/>  AB Banka Kartı Numarası - En az 10, Maksimum sayı 500  <br/>  SWIFT Kodu - En az 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="uk-personal-information-online-code-of-practice-piocp"></a>INGİLTERE. Kişisel Bilgiler Çevrimiçi Uygulama Kodu (PIOCP)

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|INGİLTERE. PIOCP: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  INGİLTERE. Ulusal Sigorta Numarası (NINO) - En az sayı 1, Maksimum sayı 9  <br/>  INGİLTERE. Ulusal Sistem Sağlığı Hizmeti Sayısı - En az sayı 1, Maksimum sayı 9  <br/>  SWIFT Kodu - En az sayı 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|INGİLTERE. PIOCP: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  INGİLTERE. Ulusal Sigorta Numarası (NINO) - En az 10, Maksimum sayı 500  <br/>  INGİLTERE. Ulusal Sistem Sağlığı Hizmeti Sayısı - En az 10, Maksimum sayı 500  <br/>  SWIFT Kodu - En az 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="uk-personally-identifiable-information-pii-data"></a>INGİLTERE. Kişisel Bilgiler (PII) Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|INGİLTERE. PII: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  INGİLTERE. Ulusal Sigorta Numarası (NINO) - En az sayı 1, Maksimum sayı 9  <br/>  Birleşik Krallık / Birleşik Krallık Pasaport Numarası - En az sayı 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|INGİLTERE. PII: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  INGİLTERE. Ulusal Sigorta Numarası (NINO) - En az 10, Maksimum sayı 500  <br/>  Birleşik Krallık / Birleşik Krallık Pasaport Numarası - En az sayı 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="uk-privacy-and-electronic-communications-regulations"></a>INGİLTERE. Gizlilik ve Elektronik İletişim Düzenlemeleri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|INGİLTERE. PECR: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  SWIFT Kodu - En az sayı 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|INGİLTERE. PECR: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  SWIFT Kodu - En az 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="us-federal-trade-commission-ftc-consumer-rules"></a>ABD Federal Ticaret Komisyonu (FTC) Tüketici Kuralları

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|ABD FTC Kuralları: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası - En az sayı 1, Maksimum sayı 9  <br/>  ABD Banka Hesap Numarası - En az sayı 1, Maksimum sayı 9  <br/>  ABA Yönlendirme Numarası - En az sayı 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|ABD FTC Kuralları: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası - En az 10, Maksimum sayı 500  <br/>  ABD Banka Hesap Numarası - En az 10, Maksimum sayı 500  <br/>  ABA Yönlendirme Numarası - En az sayı 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="us-financial-data"></a>ABD Finansal Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|ABD Finansal: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası - En az sayı 1, Maksimum sayı 9  <br/>  ABD Banka Hesap Numarası - En az sayı 1, Maksimum sayı 9  <br/>  ABA Yönlendirme Numarası - En az sayı 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|ABD Finansal: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası - En az 10, Maksimum sayı 500  <br/>  ABD Banka Hesap Numarası - En az 10, Maksimum sayı 500  <br/>  ABA Yönlendirme Numarası - En az sayı 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="us-gramm-leach-bliley-act-glba"></a>ABD Gramm-Leach-Bliley Yasası (GLBA)

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|ABD GLBA: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası - En az sayı 1, Maksimum sayı 9  <br/>  ABD Banka Hesap Numarası - En az sayı 1, Maksimum sayı 9  <br/>  ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN) - En az sayı 1, Maksimum sayı 9  <br/>  ABD Sosyal Güvenlik Numarası (SSN) - Min count 1, Max count 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|ABD GLBA: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası - En az 10, Maksimum sayı 500  <br/>  ABD Banka Hesap Numarası - En az 10, Maksimum sayı 500  <br/>  ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN) - Min count 10, Max count 500  <br/>  ABD Sosyal Güvenlik Numarası (SSN) - En az 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="us-health-insurance-act-hipaa"></a>ABD Sağlık Sigortası Yasası (HIPAA)

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|İçerik ABD HIPAA ile eşleşir  <br/> | Aşağıdaki hassas bilgilerden herhangi birini içerir:  <br/>  ABD Sosyal Güvenlik Numarası (SSN) - En az 1, Maksimum sayı herhangi biri  <br/>  Uyuşturucu Uygulama Dairesi (DEA) Numarası - En az sayı 1, Maksimum sayı herhangi  <br/> **VE** <br/>  İçerik şu terimlerden herhangi birini içerir:  <br/>  Uluslararası Hastalık Sınıflandırması (ICD-9-CM) - En az sayı 1, Maksimum sayı herhangi biri  <br/>  Uluslararası Hastalık Sınıflandırması (ICD-10-CM) - En az sayı 1, Maksimum sayı herhangi biri  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
   
## <a name="us-patriot-act"></a>ABD Vatanseverlik Yasası

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|ABD Vatanseverlik Yasası: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası - En az sayı 1, Maksimum sayı 9  <br/>  ABD Banka Hesap Numarası - En az sayı 1, Maksimum sayı 9  <br/>  ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN) - En az sayı 1, Maksimum sayı 9  <br/>  ABD Sosyal Güvenlik Numarası (SSN) - Min count 1, Max count 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|ABD Vatanseverlik Yasası: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası - En az 10, Maksimum sayı 500  <br/>  ABD Banka Hesap Numarası - En az 10, Maksimum sayı 500  <br/>  ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN) - Min count 10, Max count 500  <br/>  ABD Sosyal Güvenlik Numarası (SSN) - En az 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="us-personally-identifiable-information-pii-data"></a>ABD Kişisel Bilgiler (PII) Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|ABD PII: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN) - En az sayı 1, Maksimum sayı 9  <br/>  ABD Sosyal Güvenlik Numarası (SSN) - Min count 1, Max count 9  <br/>  Birleşik Krallık / Birleşik Krallık Pasaport Numarası - En az sayı 1, Maksimum sayı 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|ABD PII: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN) - Min count 10, Max count 500  <br/>  ABD Sosyal Güvenlik Numarası (SSN) - En az 10, Maksimum sayı 500  <br/>  Birleşik Krallık / Birleşik Krallık Pasaport Numarası - En az sayı 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="us-state-breach-notification-laws"></a>ABD Eyalet İhlali Bildirim Yasaları

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|ABD Eyalet İhlali: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası - En az sayı 1, Maksimum sayı 9  <br/>  ABD Banka Hesap Numarası - En az sayı 1, Maksimum sayı 9  <br/>  ABD Sürücü Belgesi Numarası - En az 1, Maksimum sayı 9  <br/>  ABD Sosyal Güvenlik Numarası (SSN) - Min count 1, Max count 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|ABD Eyalet İhlali: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası - En az 10, Maksimum sayı 500  <br/>  ABD Banka Hesap Numarası - En az 10, Maksimum sayı 500  <br/>  ABD Sürücü Belgesi Numarası - En az 10, Maksimum sayı 500  <br/>  ABD Sosyal Güvenlik Numarası (SSN) - En az 10, Maksimum sayı 500 <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="us-state-social-security-number-confidentiality-laws"></a>ABD Devlet Sosyal Güvenlik Numarası Gizlilik Yasaları

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylem**|
|:-----|:-----|:-----|
|ABD SSN Yasaları: Dışarıda paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  ABD Sosyal Güvenlik Numarası (SSN) - Min count 1, Max count 9  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|ABD SSN Yasaları: Dışarıda paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  ABD Sosyal Güvenlik Numarası (SSN) - En az 10, Maksimum sayı 500  <br/>  İçerik şu kişilerle paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçeriğe erişimi engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İş gerekçesi gerektir  <br/>  Olay raporu gönderme  <br/> |
   

