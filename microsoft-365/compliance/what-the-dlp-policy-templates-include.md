---
title: DLP ilkesi şablonlarının şunları içermesi
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
description: Güvenlik ve Uyumluluk Merkezi'nde veri kaybı önleme (DLP) Office 365 şablonlarının & öğrenin.
ms.openlocfilehash: cad7270fd60b0bce9febe90f25156bd27bdcee32
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2021
ms.locfileid: "63005020"
---
# <a name="what-the-dlp-policy-templates-include"></a>DLP ilkesi şablonlarının şunları içermesi

Güvenlik Uyumluluk Merkezi'nde veri kaybı önleme (DLP), &amp; ABD Sağlık Sigortası Yasası (HIPAA), ABD Gramm-Leach-Bliley Act (GLBA) veya Act . Bu konu başlığı altında, tüm ilke şablonları, ne tür hassas bilgiler için arama yaptıkları ve varsayılan koşullarla eylemlerin ne olduğu listelanmıştır. Bu konu, her ilke şablonunun nasıl yapılandırıldıklarının her bir ayrıntıyı içermemektedir; bunun yerine, konu başlığı size senaryo için en iyi başlangıç noktası olan şablona karar vermede yardımcı olacak yeterli bilgileri sunar. Unutmayın, bu ilke şablonlarını kendi özel gereksinimlerinizi karşılayacak şekilde özelleştirebilirsiniz.
  
## <a name="australia-financial-data"></a>Avustralya Finansal Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|Avustralya Finansal: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  SWIFT Kodu — En az sayı 1, En fazla sayı 9  <br/>  Avustralya Vergi Dosyası Numarası — En az sayı 1, En fazla 9 sayı  <br/>  Australia Bank Hesap Numarası — Min count 1, Max count 9  <br/>  Kredi Kartı Numarası — En az sayı 1, En fazla 9 sayı  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Avustralya Finansal: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  SWIFT Kodu — En az 10 sayı, En fazla 500  <br/>  Avustralya Vergi Dosyası Numarası — En az 10 sayım, En fazla 500  <br/>  Australia Bank Hesap Numarası — Min count 10, Max count 500  <br/>  Kredi Kartı Numarası — En az 10 sayım, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="australia-health-records-act-hrip-act"></a>Avustralya Sağlık Kayıtları Yasası (HRIP Yasası)

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|Avustralya HRIP: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Avustralya Vergi Dosyası Numarası — En az sayı 1, En fazla 9 sayı  <br/>  Avustralya Tıbbi Hesap Numarası — Min sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Avustralya HRIP: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Avustralya Vergi Dosyası Numarası — En az 10 sayım, En fazla 500  <br/>  Avustralya Tıbbi Hesap Numarası — Dakika sayısı 10, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="australia-personally-identifiable-information-pii-data"></a>Avustralya Kişisel Bilgileri (PII) Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|Avustralya PIN'i: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Avustralya Vergi Dosyası Numarası — En az sayı 1, En fazla 9 sayı  <br/>  Avustralya Sürücüsü Lisans Numarası — En Az sayı 1, En fazla 9 sayı  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Avustralya PIN'i: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Avustralya Vergi Dosyası Numarası — En az 10 sayım, En fazla 500  <br/>  Avustralya Sürücüsü Lisans Numarası — En az 10 sayım, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="australia-privacy-act"></a>Avustralya Gizlilik Yasası

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|Avustralya Gizliliği: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Avustralya Sürücüsü Lisans Numarası — En Az sayı 1, En fazla 9 sayı  <br/>  Avustralya Pasaport Numarası — En az sayı 1, En fazla 9 sayı  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Avustralya Gizliliği: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Avustralya Sürücüsü Lisans Numarası — En az 10 sayım, En fazla 500  <br/>  Avustralya Pasaport Numarası — En az 10 adet, En fazla 500 adet <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="canada-financial-data"></a>Kanada Finansal Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|Kanada Finansal Verileri: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası — En az sayı 1, En fazla 9 sayı  <br/>  Kanada Banka Hesap Numarası — En küçük sayım 1, En fazla sayım 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Kanada Finansal Verileri: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası — En az 10 sayım, En fazla 500  <br/>  Kanada Banka Hesap Numarası — Min count 10, Max count 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="canada-health-information-act-hia"></a>Kanada Sağlık Bilgileri Yasası (HIA)

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|Kanada HIA: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Pasaport Numarası — En az sayı 1, En fazla sayı 9  <br/>  Kanada Sosyal Sigorta Numarası — En az sayı 1, En fazla sayı 9  <br/>  Kanada Sistem Sağlığı Hizmeti Numarası — En Az sayı 1, En fazla sayı 9  <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) — En küçük sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Kanada HIA: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Pasaport Numarası — En az 10 adet, En fazla 500 adet  <br/>  Kanada Sosyal Sigorta Numarası — En az 10 sayı, En fazla 500  <br/>  Kanada Sistem Sağlığı Hizmeti Numarası — En küçük sayım 10, En fazla 500  <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) — En küçük sayı 10, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="canada-personal-health-act-phipa---ontario"></a>Kanada Kişisel Sağlık Yasası (PHIPA) - Ontario

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|Kanada PHIPA: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Pasaport Numarası — En az sayı 1, En fazla sayı 9  <br/>  Kanada Sosyal Sigorta Numarası — En az sayı 1, En fazla sayı 9  <br/>  Kanada Sistem Sağlığı Hizmeti Numarası — En Az sayı 1, En fazla sayı 9  <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) — En küçük sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Kanada PHIPA: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Pasaport Numarası — En az 10 adet, En fazla 500 adet  <br/>  Kanada Sosyal Sigorta Numarası — En az 10 sayı, En fazla 500  <br/>  Kanada Sistem Sağlığı Hizmeti Numarası — En küçük sayım 10, En fazla 500  <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) — En küçük sayı 10, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="canada-personal-health-information-act-phia---manitoba"></a>Kanada Kişisel Sağlık Bilgileri Yasası (PHIA) - Manitoba

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|Kanada PHIA: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Sosyal Sigorta Numarası — En az sayı 1, En fazla sayı 9  <br/>  Kanada Sistem Sağlığı Hizmeti Numarası — En Az sayı 1, En fazla sayı 9  <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) — En küçük sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Kanada PHIA: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Sosyal Sigorta Numarası — En az 10 sayı, En fazla 500  <br/>  Kanada Sistem Sağlığı Hizmeti Numarası — En küçük sayım 10, En fazla 500 <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) — En küçük sayı 10, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="canada-personal-information-protection-act-pipa"></a>Kanada Kişisel Bilgi Koruma Yasası (PIPA)

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|Kanada PIPA: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Pasaport Numarası — En az sayı 1, En fazla sayı 9  <br/>  Kanada Sosyal Sigorta Numarası — En az sayı 1, En fazla sayı 9  <br/>  Kanada Sistem Sağlığı Hizmeti Numarası — En Az sayı 1, En fazla sayı 9  <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) — En küçük sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Kanada PIPA: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Pasaport Numarası — En az 10 adet, En fazla 500 adet  <br/>  Kanada Sosyal Sigorta Numarası — En az 10 sayı, En fazla 500  <br/>  Kanada Sistem Sağlığı Hizmeti Numarası — En küçük sayım 10, En fazla 500  <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) — En küçük sayı 10, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="canada-personal-information-protection-act-pipeda"></a>Kanada Kişisel Bilgi Koruma Yasası (PIPEDA)

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|Kanada PIPEDA: Dışarı paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Sürücü Lisans Numarası — En Az sayı 1, En fazla 9 sayı  <br/>  Kanada Banka Hesap Numarası — En küçük sayım 1, En fazla sayım 9  <br/>  Kanada Pasaport Numarası — En az sayı 1, En fazla sayı 9  <br/>  Kanada Sosyal Sigorta Numarası — En az sayı 1, En fazla sayı 9  <br/>  Kanada Sistem Sağlığı Hizmeti Numarası — En Az sayı 1, En fazla sayı 9  <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) — En küçük sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Kanada PIPEDA: Dışarı paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Sürücü Lisans Numarası — En az 10 sayım, En fazla 500 <br/>  Kanada Banka Hesap Numarası — Min count 10, Max count 500 <br/>  Kanada Pasaport Numarası — En az 10 adet, En fazla 500 adet  <br/>  Kanada Sosyal Sigorta Numarası — En az 10 sayı, En fazla 500  <br/>  Kanada Sistem Sağlığı Hizmeti Numarası — En küçük sayım 10, En fazla 500  <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) — En küçük sayı 10, En fazla 500 <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="canada-personally-identifiable-information-pii-data"></a>Kanada Kişisel Bilgileri (PII) Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|Kanada PII'si: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Sürücü Lisans Numarası — En Az sayı 1, En fazla 9 sayı  <br/>  Kanada Banka Hesap Numarası — En küçük sayım 1, En fazla sayım 9  <br/>  Kanada Pasaport Numarası — En az sayı 1, En fazla sayı 9  <br/>  Kanada Sosyal Sigorta Numarası — En az sayı 1, En fazla sayı 9  <br/>  Kanada Sistem Sağlığı Hizmeti Numarası — En Az sayı 1, En fazla sayı 9  <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) — En küçük sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Kanada PII'si: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kanada Sürücü Lisans Numarası — En az 10 sayım, En fazla 500  <br/>  Kanada Banka Hesap Numarası — Min count 10, Max count 500  <br/>  Kanada Pasaport Numarası — En az 10 adet, En fazla 500 adet  <br/>  Kanada Sosyal Sigorta Numarası — En az 10 sayı, En fazla 500  <br/>  Kanada Sistem Sağlığı Hizmeti Numarası — En küçük sayım 10, En fazla 500  <br/>  Kanada Kişisel Sağlık Kimlik Numarası (PHIN) — En küçük sayı 10, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="france-data-protection-act"></a>Fransa Veri Koruma Yasası

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|Fransa DPA: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Fransa Ulusal Kimlik Kartı (CNI) — En az sayı 1, En fazla sayı 9  <br/>  Fransa Sosyal Güvenlik Numarası (INSEE) — En küçük sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Fransa DPA: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Fransa Ulusal Kimlik Kartı (CNI) — Min sayım 10, En fazla 500  <br/>  Fransa Sosyal Güvenlik Numarası (INSEE) — Min sayım 10, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="france-financial-data"></a>France Financial Data

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|France Financial: Scan content shared outside - low count  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası — En az sayı 1, En fazla 9 sayı  <br/>  AB Banka Kartı Numarası — En az sayı 1, En fazla 9 sayı  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|France Financial: Scan content shared outside - high count  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası — En az 10 sayım, En fazla 500  <br/>  AB Banka Kartı Numarası — En az 10 sayım, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="france-personally-identifiable-information-pii-data"></a>Fransa Kişisel Bilgileri (PII) Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|Fransa PII: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Fransa Sosyal Güvenlik Numarası (INSEE) — En küçük sayı 1, En fazla sayı 9  <br/>  Fransa Sürücü Lisans Numarası — En Az sayı 1, En fazla sayı 9  <br/>  Fransa Pasaport Numarası — Min count 1, Max count 9  <br/>  Fransa Ulusal Kimlik Kartı (CNI) — En az sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Fransa PII: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Fransa Sosyal Güvenlik Numarası (INSEE) — Min sayım 10, En fazla 500  <br/>  Fransa Sürücü Lisans Numarası — En az 10 sayı, En fazla 500  <br/>  Fransa Pasaport Numarası — Min count 10, Max count 500  <br/>  Fransa Ulusal Kimlik Kartı (CNI) — Min sayım 10, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="general-data-protection-regulation-gdpr"></a>Genel Veri Koruma Yönetmeliği (GDPR)

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|Düşük hacimli AB Duyarlı içerik bulundu  <br/> | İçerik hassas bilgiler içerir:  <br/>  AB Banka Kartı Numarası — En az sayı 1, En fazla 9 sayı  <br/>  EU Driver's License Number — Min count 1, Max count 9  <br/>  AB Ulusal Kimlik Numarası — En az sayı 1, En fazla sayı 9  <br/>  EU Passport Number — Min count 1, Max count 9  <br/>  EU Social Security Number (SSN) or Equivalent ID — Min count 1, Max count 9  <br/>  AB Vergi Tanımlama Numarası (TIN) — En küçük sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Yöneticiye olay raporları gönderme  <br/> |
|Yüksek hacimli AB'ye Duyarlı içerik bulundu  <br/> | İçerik hassas bilgiler içerir:  <br/>  AB Banka Kartı Numarası — En az 10 sayım, En fazla 500  <br/>  EU Driver's License Number — Min count 10, Max count 500  <br/>  AB Ulusal Kimlik Numarası — En az 10 sayı, En fazla 500  <br/>  EU Passport Number — Min count 10, Max count 500  <br/>  EU Social Security Number (SSN) or Equivalent ID — Min count 10, Max count 500  <br/>  AB Vergi Tanımlama Numarası (TIN) — En az 10 sayı, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | Dış kullanıcıların içeriğine erişimi kısıtlama  <br/>  Kullanıcıları e-posta ve ilke ipuçlarıyla bilgilendirin  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Yöneticiye olay raporları gönderme  <br/> |
   
## <a name="germany-financial-data"></a>Almanya Finansal Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|Almanya Finansal Verileri: Dışında paylaşılan içeriği tara - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası — En az sayı 1, En fazla 9 sayı  <br/>  AB Banka Kartı Numarası — En az sayı 1, En fazla 9 sayı  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Almanya Finansal Verileri: Dışında paylaşılan içeriği tara - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası — En az 10 sayım, En fazla 500  <br/>  AB Banka Kartı Numarası — En az 10 sayım, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="germany-personally-identifiable-information-pii-data"></a>Almanya Kişisel Bilgileri (PII) Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|Almanya PII: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Almanca Sürücü Lisans Numarası — En Az sayı 1, En fazla 9 sayı  <br/>  Almanca Pasaport Numarası — En az sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Almanya PII: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Almanca Sürücü Lisans Numarası — En az 10 sayı, En fazla 500  <br/>  Almanca Pasaport Numarası — En az 10 adet, En fazla 500 adet  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="israel-financial-data"></a>İsrail Finansal Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|İsrail Finansal Verileri: Dışında paylaşılan içeriği tara - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  İsrail Banka Hesap Numarası — En az sayı 1, En fazla sayı 9  <br/>  SWIFT Kodu — En az sayı 1, En fazla sayı 9  <br/>  Kredi Kartı Numarası — En az sayı 1, En fazla 9 sayı  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|İsrail Finansal Verileri: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  İsrail Banka Hesap Numarası — Min count 10, Max count 500  <br/>  SWIFT Kodu — En az 10 sayı, En fazla 500  <br/>  Kredi Kartı Numarası — En az 10 sayım, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="israel-personally-identifiable-information-pii-data"></a>İsrail Kişisel Bilgileri (PII) Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|İsrail PII'si: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  İsrail Ulusal Kimliği — En az sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|İsrail PII'si: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  İsrail Ulusal Kimliği — En az 10 sayı, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="israel-protection-of-privacy"></a>İsrail Gizliliği Koruma

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|İsrail Gizliliği: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  İsrail Ulusal Kimliği — En az sayı 1, En fazla sayı 9  <br/>  İsrail Banka Hesap Numarası — En az sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|İsrail Gizliliği: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  İsrail Ulusal Kimliği — En az 10 sayı, En fazla 500  <br/>  İsrail Banka Hesap Numarası — Min count 10, Max count 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="japan-financial-data"></a>Japonya Finansal Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|Japonya Finansal: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Japonya Banka Hesap Numarası — En az sayı 1, En fazla sayı 9  <br/>  Kredi Kartı Numarası — En az sayı 1, En fazla 9 sayı  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Japonya Finansal: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Japonya Banka Hesap Numarası — En az 10 sayım, En fazla 500  <br/>  Kredi Kartı Numarası — En az 10 sayım, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="japan-personally-identifiable-information-pii-data"></a>Japonya Kişisel Bilgileri (PII) Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|Japonya PII'si: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Japonya'daki Yerleşik Kayıt Numarası — Min sayı 1, En fazla sayı 9  <br/>  Japonya Sosyal Sigorta Numarası (SN) — En az sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Japonya PII'si: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Japonya'daki Yerleşik Kayıt Numarası — Min sayı 10, En fazla 500  <br/>  Japonya Sosyal Sigorta Numarası (SN) — En az 10 sayı, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="japan-protection-of-personal-information"></a>Japonya Kişisel Bilgilerin Korunması

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|Japonya PPI'si: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Japonya'daki Yerleşik Kayıt Numarası — Min sayı 1, En fazla sayı 9  <br/>  Japonya Sosyal Sigorta Numarası (SN) — En az sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Japonya PPI'si: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Japonya'daki Yerleşik Kayıt Numarası — Min sayı 10, En fazla 500  <br/>  Japonya Sosyal Sigorta Numarası (SN) — En az 10 sayı, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="pci-data-security-standard-pci-dss"></a>PCI Veri Güvenliği Standardı (PCI DSS)

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|PCI DSS: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası — En az sayı 1, En fazla 9 sayı  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|PCI DSS: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası — En az 10 sayım, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="saudi-arabia---anti-cyber-crime-law"></a>Suudi Arabistan - Siber Suç Önleme Yasası

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|Suudi Arabistan ACC: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  SWIFT Kodu — En az sayı 1, En fazla sayı 9  <br/>  Uluslararası Bankacılık Hesap Numarası (IBAN) — En küçük sayım 1, En fazla 9 sayma  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Suudi Arabistan ACC: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  SWIFT Kodu — En az 10 sayı, En fazla 500  <br/>  Uluslararası Bankacılık Hesap Numarası (IBAN) — Min sayım 10, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="saudi-arabia-financial-data"></a>Suudi Arabistan Mali Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|Suudi Arabistan Finansal: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası — En az sayı 1, En fazla 9 sayı  <br/>  SWIFT Kodu — En az sayı 1, En fazla sayı 9  <br/>  Uluslararası Bankacılık Hesap Numarası (IBAN) — En küçük sayım 1, En fazla 9 sayma  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Suudi Arabistan Finansal: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası — En az 10 sayım, En fazla 500  <br/>  SWIFT Kodu — En az 10 sayı, En fazla 500  <br/>  Uluslararası Bankacılık Hesap Numarası (IBAN) — Min sayım 10, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="saudi-arabia-personally-identifiable-information-pii-data"></a>Suudi Arabistan Kişisel Bilgileri (PII) Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|Suudi Arabistan PII'si: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Suudi Arabistan Ulusal Kimliği — Min count 1, Max count 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|Suudi Arabistan PII'si: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Suudi Arabistan Ulusal Kimliği — Min count 10, Max count 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="uk-access-to-medical-reports-act"></a>B.K. Tıbbi Raporlara Erişim Yasası

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|B.K. AMRA: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  B.K. Ulusal Sistem Sağlığı Hizmeti Sayısı — En küçük sayı 1, En fazla sayı 9  <br/>  B.K. Ulusal Sigorta Numarası (NINO) — En küçük sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|B.K. AMRA: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  B.K. Ulusal Sistem Sağlığı Hizmeti Sayısı — En küçük sayı 10, En fazla 500  <br/>  B.K. Ulusal Sigorta Numarası (NINO) — En küçük sayı 10, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="uk-data-protection-act"></a>B.K. Veri Koruma Yasası

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|B.K. DPA: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  B.K. Ulusal Sigorta Numarası (NINO) — En küçük sayı 1, En fazla sayı 9  <br/>  ABD / U.K. Pasaport Numarası — En küçük sayı 1, En fazla sayı 9  <br/>  SWIFT Kodu — En az sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|B.K. DPA: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  B.K. Ulusal Sigorta Numarası (NINO) — En küçük sayı 10, En fazla 500  <br/>  ABD / U.K. Pasaport Numarası — En az 10 adet, En fazla 500 adet  <br/>  SWIFT Kodu — En az 10 sayı, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="uk-financial-data"></a>B.K. Finansal Veriler

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|B.K. Finansal: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası — En az sayı 1, En fazla 9 sayı  <br/>  AB Banka Kartı Numarası — En az sayı 1, En fazla 9 sayı  <br/>  SWIFT Kodu —En az sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|B.K. Finansal: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası — En az 10 sayım, En fazla 500  <br/>  AB Banka Kartı Numarası — En az 10 sayım, En fazla 500  <br/>  SWIFT Kodu — En az 10 sayı, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="uk-personal-information-online-code-of-practice-piocp"></a>B.K. Kişisel Bilgiler Çevrimiçi Uygulama Kodu (PIOCP)

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|B.K. PIOCP: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  B.K. Ulusal Sigorta Numarası (NINO) — En küçük sayı 1, En fazla sayı 9  <br/>  B.K. Ulusal Sistem Sağlığı Hizmeti Sayısı — En küçük sayı 1, En fazla sayı 9  <br/>  SWIFT Kodu — En az sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|B.K. PIOCP: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  B.K. Ulusal Sigorta Numarası (NINO) — En küçük sayı 10, En fazla 500  <br/>  B.K. Ulusal Sistem Sağlığı Hizmeti Sayısı — En küçük sayı 10, En fazla 500  <br/>  SWIFT Kodu — En az 10 sayı, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="uk-personally-identifiable-information-pii-data"></a>B.K. Kişisel Kimliği Tanımlayıcı Bilgiler (PII) Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|B.K. PII: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  B.K. Ulusal Sigorta Numarası (NINO) — En küçük sayı 1, En fazla sayı 9  <br/>  ABD / U.K. Pasaport Numarası — En küçük sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|B.K. PII: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  B.K. Ulusal Sigorta Numarası (NINO) — En küçük sayı 10, En fazla 500  <br/>  ABD / U.K. Pasaport Numarası — En az 10 adet, En fazla 500 adet  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="uk-privacy-and-electronic-communications-regulations"></a>B.K. Gizlilik ve Elektronik İletişim Düzenlemeleri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|B.K. PECR: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  SWIFT Kodu — En az sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|B.K. PECR: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  SWIFT Kodu — En az 10 sayı, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="us-federal-trade-commission-ftc-consumer-rules"></a>ABD Federal Ticaret Komisyonu (FTC) Tüketici Kuralları

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|ABD FTC Kuralları: Dışarı paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası — En az sayı 1, En fazla 9 sayı  <br/>  ABD Banka Hesap Numarası — En az 1 sayım, En fazla 9 sayma  <br/>  ABA Yönlendirme Numarası — En küçük sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|ABD FTC Kuralları: Dışarı paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası — En az 10 sayım, En fazla 500  <br/>  ABD Banka Hesap Numarası — En az 10 sayım, En fazla 500  <br/>  ABA Yönlendirme Numarası — Min sayı 10, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="us-financial-data"></a>ABD Finansal Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|ABD Finansal: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası — En az sayı 1, En fazla 9 sayı  <br/>  ABD Banka Hesap Numarası — En az 1 sayım, En fazla 9 sayma  <br/>  ABA Yönlendirme Numarası — En küçük sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|ABD Finansal: Dışarı paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası — En az 10 sayım, En fazla 500  <br/>  ABD Banka Hesap Numarası — En az 10 sayım, En fazla 500  <br/>  ABA Yönlendirme Numarası — Min sayı 10, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="us-gramm-leach-bliley-act-glba"></a>ABD Gramm-Leach-Bliley Act (GLBA)

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|ABD GLBA: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası — En az sayı 1, En fazla 9 sayı  <br/>  ABD Banka Hesap Numarası — En az 1 sayım, En fazla 9 sayma  <br/>  ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN) — En az 1 sayım, En fazla 9 say  <br/>  ABD Sosyal Güvenlik Numarası (SSN) — En küçük sayı 1, En fazla 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|ABD GLBA: Dışarı paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası — En az 10 sayım, En fazla 500  <br/>  ABD Banka Hesap Numarası — En az 10 sayım, En fazla 500  <br/>  ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN) — En az 10 say, En fazla 500  <br/>  ABD Sosyal Güvenlik Numarası (SSN) — En az 10 sayı, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="us-health-insurance-act-hipaa"></a>ABD Sağlık Sigortası Yasası (HIPAA)

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|İçerik ABD HIPAA ile eşleri  <br/> | Aşağıdaki hassas bilgilerden herhangi birini içerir:  <br/>  ABD Sosyal Güvenlik Numarası (SSN) — Min sayım 1, En fazla herhangi birini sayma  <br/>  Enforcement Agency (DEA) Numarası — Min count 1, Max count any  <br/> **VE** <br/>  İçerik şu koşulları içerir:  <br/>  Uluslararası Hastalık Sınıflandırması (ICD-9-CM) — En az 1 sayı, En fazla herhangi birini sayma  <br/>  Uluslararası Hastalık Sınıflandırması (ICD-10-CM) — Min sayım 1, En fazla sayım  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
   
## <a name="us-patriot-act"></a>ABD S. Act

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|ABD'nin Harekete: Dışarı paylaşılan içeriği tara - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası — En az sayı 1, En fazla 9 sayı  <br/>  ABD Banka Hesap Numarası — En az 1 sayım, En fazla 9 sayma  <br/>  ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN) — En az 1 sayım, En fazla 9 say  <br/>  ABD Sosyal Güvenlik Numarası (SSN) — En küçük sayı 1, En fazla 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|ABD'nin Hareket: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası — En az 10 sayım, En fazla 500  <br/>  ABD Banka Hesap Numarası — En az 10 sayım, En fazla 500  <br/>  ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN) — En az 10 say, En fazla 500  <br/>  ABD Sosyal Güvenlik Numarası (SSN) — En az 10 sayı, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="us-personally-identifiable-information-pii-data"></a>ABD Kişisel Bilgileri (PII) Verileri

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|ABD PII: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN) — En az 1 sayım, En fazla 9 say  <br/>  ABD Sosyal Güvenlik Numarası (SSN) — En küçük sayı 1, En fazla 9  <br/>  ABD / U.K. Pasaport Numarası — En küçük sayı 1, En fazla sayı 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|ABD PII: Dışarı paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  ABD Bireysel Vergi Mükellefi Kimlik Numarası (ITIN) — En az 10 say, En fazla 500  <br/>  ABD Sosyal Güvenlik Numarası (SSN) — En az 10 sayı, En fazla 500  <br/>  ABD / U.K. Pasaport Numarası — En az 10 adet, En fazla 500 adet  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="us-state-breach-notification-laws"></a>ABD Eyaleti İhlal Bildirimi Yasaları

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|ABD Eyaleti İhlali: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası — En az sayı 1, En fazla 9 sayı  <br/>  ABD Banka Hesap Numarası — En az 1 sayım, En fazla 9 sayma  <br/>  ABD Sürücü Lisans Numarası — En az 1 sayım, En fazla 9 say  <br/>  ABD Sosyal Güvenlik Numarası (SSN) — En küçük sayı 1, En fazla 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|ABD Eyaleti İhlali: Dışarı paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  Kredi Kartı Numarası — En az 10 sayım, En fazla 500  <br/>  ABD Banka Hesap Numarası — En az 10 sayım, En fazla 500  <br/>  ABD Sürücü Lisans Numarası — En az 10 say, En fazla 500  <br/>  ABD Sosyal Güvenlik Numarası (SSN) — En az 10 sayı, En fazla 500 <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   
## <a name="us-state-social-security-number-confidentiality-laws"></a>ABD Eyaleti Sosyal Güvenlik Numarası Gizlilik Yasaları

|**Kural adı**|**Koşullar  <br/> (hassas bilgi türleri dahil)**|**Eylemler**|
|:-----|:-----|:-----|
|ABD SSN Yasaları: Dışında paylaşılan içeriği tarama - düşük sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  ABD Sosyal Güvenlik Numarası (SSN) — En küçük sayı 1, En fazla 9  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> |Bildirim gönderme  <br/> |
|ABD SSN Yasaları: Dışında paylaşılan içeriği tarama - yüksek sayı  <br/> | İçerik hassas bilgiler içerir:  <br/>  ABD Sosyal Güvenlik Numarası (SSN) — En az 10 sayı, En fazla 500  <br/>  İçerik şularla paylaşılır:  <br/>  Kuruluşum dışındaki kişiler  <br/> | İçerik erişimini engelleme  <br/>  Bildirim gönderme  <br/>  Geçersiz kılmaya izin ver  <br/>  İşletmenin gerekçesini gerektirme  <br/>  Olay raporu gönderme  <br/> |
   

