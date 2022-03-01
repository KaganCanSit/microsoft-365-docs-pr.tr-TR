---
title: Etkinlik gezgininde bildirilen etiketleme eylemleri
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Etkinlik gezgininde kullanılabilen etiket etkinliklerinin listesi.
ms.openlocfilehash: feed9d29deb94263d242967bdef38209cda660e1
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "63006756"
---
# <a name="labeling-activities-that-are-available-in-activity-explorer"></a>Etkinlik gezgininde bulunan etkinlikleri etiketleme

## <a name="sensitivity-label-applied"></a>Duyarlılık etiketi uygulandı

Bu olay, etiketsiz bir belge her etiketli veya bir duyarlılık etiketi içeren bir e-posta gönder her gönder gönder iletişim durumunda oluşturulur.

- Yerel uygulamalarda ve web uygulamalarında Office zamanda yakalanır.
- Azure Information protection eklentilerinde olduğu sırada yakalanır.
- Etiket yükseltme ve düşürme eylemleri, Etiket olay türü alanı *ve filtresi aracılığıyla* da izlenir.

|Kaynak  |Etkinlik gezgininde bildirilen | Not  |
|---------|---------|---------|
| Word, Excel, PowerPoint|Evet |
|Outlook| Evet | |
|SharePoint çevrimiçi, OneDrive|Evet | |
|Exchange        |Evet         | |
|Azure Information Protection (AIP) birleşik istemcisi ve AIP birleşik tarayıcısı |Evet |AIP *yeni etiket eylemi* Etkinlik gezgininde *uygulanan etiketle* eşlenmiş   |
|Microsoft bilgi koruması (MIP) SDK         |Evet|AIP *yeni etiket eylemi* Etkinlik gezgininde *uygulanan etiketle* eşlenmiş|
|Hak Yönetimi Hizmeti (RMS)         |Geçerli değil         | |
|Power BI ve web'de        | Hayır| Denetim günlüklerinde Microsoft 365 erişilebilir         |
|Bulut Uygulamaları için Microsoft Defender         |Hayır|         |

## <a name="sensitivity-label-changed"></a>Duyarlılık etiketi değişti

Belge veya e-postada her duyarlılık etiketi güncelleştirildiğinde bu olay oluşturulur.

- AIP Birleşik istemcisi, Birleşik Tarayıcı ve MIP SDK kaynakları için, *AIP yükseltme* etiketi ve indirilen  etiket eylem eşlemeleri Etkinlik gezgini *etiketiyle değiştirildi*

- Yerel uygulamalar ve web uygulamalarında kaydetme Office noktasında yakalanır.
- Azure Information protection birleşik istemci eklentileri ve tarayıcı zorlamalarında ortaya olduğu sırada yakalanır
- Etiket yükseltme ve düşürme eylemleri, Etiket olay türü alanı *ve filtresi aracılığıyla* da izlenir. *Yaslama* metni, SharePoint Online ve OneDrive.
- Yerel uygulamalarda veya yerel Office yapılan duyarlılık Outlook kaydetme/e-posta gönderme eylemlerini önce oluşturulan son eylemi toplar. Örneğin, kullanıcı e-postanın etiketini göndermeden önce birkaç kez değiştirirse, gönderilen e-postada bulunan son etiket denetim günlüğünde yakalanır ve etkinlik gezgininde raporlanır.

|Kaynak  |Etkinlik gezgininde bildirilen|Not  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Evet         |
|Outlook         |Evet         |
|SharePoint Online, OneDrive         |Evet         |
|Exchange         |Evet         |
|AIP birleşik istemcisi         |Evet         |
|AIP birleşik tarayıcı         |Evet         |
|MIP SDK         |Evet         |
|RMS hizmeti         |Uygulanamaz         |
|Power BI ve Web         |Hayır         |Denetim günlüklerinde Microsoft 365 erişilebilir |
|Bulut Uygulamaları için Microsoft Defender     |Hayır         |         |

## <a name="sensitivity-label-removed"></a>Duyarlılık etiketi kaldırıldı

Dosyadan veya belgeden her duyarlılık etiketi kaldırıldığı zaman bu olay oluşturulur.

- Bu olay, yerel uygulamalarda ve web uygulamalarında Office sırasında yakalanır.
- Azure Information protection eklentilerinde olduğu sırada yakalanır.
- Yerel MIP etiketiyle duyarlılık Office, Outlook dosya kaydetme/e-posta gönderme eylemlerini göndermeden önce oluşturulan son etiket olaylarını toplar.

|Kaynak  |Etkinlik gezgininde bildirilen | Not  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Evet         |
|Outlook         |Evet         ||
|SharePoint Online, OneDrive         |Evet         |
|Exchange         |Evet         |
|AIP birleşik istemcisi         |Evet         |AIP *etiket kaldırma eylemi* Etkinlik gezgininde *etiket kaldırma* eylemiyle eşleniyor|
|AIP birleşik tarayıcı         |Evet         |AIP *etiket kaldırma eylemi* Etkinlik gezgininde *etiket kaldırma* eylemiyle eşleniyor |
|MIP SDK         |Evet         |AIP *etiket kaldırma eylemi* Etkinlik gezgininde *etiket kaldırma* eylemiyle eşleniyor |
|RMS hizmeti         |Uygulanamaz         |
|Power BI ve Web         |Hayır         |Denetim günlüklerinde Microsoft 365 erişilebilir |
|Bulut Uygulamaları için Microsoft Defender     |Hayır         |         |

## <a name="sensitivity-label-file-read"></a>Duyarlılık etiket dosyası okundu

Bu etkinlik, etiketli veya korumalı bir belge her açıldığında oluşturulur.

|Kaynak  |Etkinlik gezgininde bildirilen | Not  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Evet         |
|Outlook         |Hayır         |
|SharePoint Online, OneDrive         |Hayır         |
|Exchange         |Hayır         |
|AIP birleşik istemcisi         |Evet         |AIP *erişim eylemi* , Etkinlik gezgininde *dosya okuma* eylemiyle eşlenmiş|
|AIP birleşik tarayıcı         |Evet         |AIP *erişim eylemi* , Etkinlik gezgininde *dosya okuma* eylemiyle eşlenmiş|
|MIP SDK         |Evet         |AIP *erişim eylemi* , Etkinlik gezgininde *dosya okuma* eylemiyle eşlenmiş|
|RMS hizmeti         |Evet         |Erişim *eylemi* , Etkinlik gezgininde *dosya okuma* eylemiyle eşlenmiş |
|Power BI ve Web         |Hayır         |Denetim günlüklerinde Microsoft 365 erişilebilir |
|Bulut Uygulamaları için Microsoft Defender     |Hayır         |         |

## <a name="files-discovered"></a>Bulunan dosyalar

Bu olay, farklı konumlarda hassas verileri taramak ve dosyaları bulan AIP Tarayıcı'lar için her dosya keşfettiklerinde oluşturulur.

|Kaynak  |Etkinlik gezgininde bildirilen | Not  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Uygulanamaz         |
|Outlook         |Uygulanamaz         |
|SharePoint Online, OneDrive         |Geçerli değil         |
|Exchange         |Geçerli değil         |
|AIP birleşik istemcisi         |Uygulanamaz       |
|AIP birleşik tarayıcı         |Evet         |AIP *keşif eylemi* , Etkinlik gezgininde *bulunan* dosyalara eşleniyor|
|MIP SDK         |Evet         |AIP *keşif eylemi* , Etkinlik gezgininde *bulunan* dosyayla eşlenmiş|
|RMS hizmeti         |Geçerli değil         |
|Power BI ve Web         |Uygulanamaz         |
|Bulut Uygulamaları için Microsoft Defender     |Geçerli değil         |         |

## <a name="sensitivity-label-file-renamed"></a>Duyarlılık etiket dosyası yeniden adlandırıldı

Duyarlılık etiketi olan bir belge her yeniden adlandırıldında bu olay oluşturulur.

|Kaynak  | Etkinlik gezgininde bildirilen | Not  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Evet         |
|Outlook         |Uygulanamaz         |
|SharePoint Online, OneDrive         |Hayır        |
|Exchange         |Geçerli değil         |
|AIP birleşik istemcisi         |Hayır         |
|AIP birleşik tarayıcı         |Hayır         |
|MIP SDK         |Hayır         |
|RMS hizmeti         |Hayır      |
|Power BI ve Web         |Hayır         |
|Bulut Uygulamaları için Microsoft Defender     |Hayır         |         |

## <a name="file-removed"></a>Dosya kaldırıldı

AIP tarayıcı daha önce taranmış bir dosyanın kaldırılmış olduğunu her algıladığında bu olay oluşturulur.

|Kaynak  |Etkinlik gezgininde bildirilen | Not  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Uygulanamaz         |
|Outlook         |Geçerli değil         |
|SharePoint Online, OneDrive         |Uygulanamaz           |
|Exchange         |Geçerli değil         |
|AIP birleşik istemcisi         |Uygulanamaz            |
|AIP birleşik tarayıcı         |Evet         |
|MIP SDK         |Geçerli değil            |
|RMS hizmeti         |Uygulanamaz         |
|Power BI ve Web         |Uygulanamaz  |
|Bulut Uygulamaları için Microsoft Defender     |Uygulanamaz        |         |

### <a name="protection-applied"></a>Koruma uygulandı

Bu olay ilk kez koruma oluşturulur ve etiketi olmayan bir öğeye el ile eklenir.

|Kaynak  |Etkinlik gezgininde bildirilen | Not  |
|---------|---------|---------|
|Word, Excel, PowerPoint         |Hayır         |
|Outlook         |Hayır         |
|SharePoint Online, OneDrive         |Uygulanamaz           |
|Exchange         |Hayır       |
|AIP birleşik istemcisi         |Evet            |
|AIP birleşik tarayıcı         |Uygulanamaz         |
|MIP SDK         |Evet            |
|RMS hizmeti         |Uygulanamaz         |
|Power BI ve Web         |Geçerli değil            |
|Bulut Uygulamaları için Microsoft Defender     |Uygulanamaz        |         |

## <a name="protection-changed"></a>Koruma değiştirildi

Bu olay, etiketsiz bir belge koruma el ile değiştir her değiştirisinde oluşturulur.

|Kaynak  |Etkinlik gezgininde bildirilen |
|---------|---------|
|Word, Excel, PowerPoint         |Hayır         |
|Outlook         |Hayır         |
|SharePoint Online, OneDrive         |Uygulanamaz           |
|Exchange         |Hayır       |
|AIP birleşik istemcisi         |Evet            |
|AIP birleşik tarayıcı         |Geçerli değil         |
|MIP SDK         |Evet            |
|RMS hizmeti         |Uygulanamaz         |
|Power BI ve Web         |Uygulanamaz            |
|Bulut Uygulamaları için Microsoft Defender     |Geçerli değil        |

## <a name="protection-removed"></a>Koruma kaldırıldı

Bu olay, etiketsiz bir belge koruma el ile değiştir her değiştirisinde oluşturulur.

|Kaynak  |Etkinlik gezgininde bildirilen |
|---------|---------|
|Word, Excel, PowerPoint         |Hayır         |
|Outlook         |Hayır         |
|SharePoint Online, OneDrive         |Geçerli değil           |
|Exchange         |Hayır       |
|AIP birleşik istemcisi         |Evet            |
|AIP birleşik tarayıcı         |Geçerli değil         |
|MIP SDK         |Evet            |
|RMS hizmeti         |Uygulanamaz         |
|Power BI ve Web         |Geçerli değil            |
|Bulut Uygulamaları için Microsoft Defender     |Geçerli değil        |

## <a name="dlp-policy-matched"></a>DLP ilkesi eşleşmeli

Bu olay, bir belge veya e-postada her DLP ilkesi eşleşmesi sırasında oluşturulur.

|Kaynak  |Etkinlik gezgininde bildirilen |
|---------|---------|
|Exchange         |Evet       |
|SharePoint Online|Evet          |
|OneDrive |Evet|
|Teams |Evet   |
|Windows 10 cihazları         |Evet |
|MAC         |Hayır     |
|Şirket içi         |Hayır|
|Bulut Uygulamaları için Microsoft Defender     |Hayır        |

Cihazlar (Uç Windows 10 DLP) için olaylar:

- Dosya silindi
- Dosya oluşturuldu
- Panoya kopyalanan dosya
- Dosya değiştirildi
- Dosya okuma
- Dosya yazdırıldı
- Dosya yeniden adlandırıldı
- Ağ paylaşımına kopyalanan dosya
- Izin verilmeyen uygulama tarafından erişilen dosya

## <a name="retention-label-applied"></a>Uygulanan bekletme etiketi

Bu olay, etiketsiz bir belge her etiketli veya bekletme etiketi içeren bir e-posta gönder nin her göndernştsinde oluşturulur.

- Belgeyi kaydetme zamanında ve e-posta gönderme zamanında yakalanır.

|Kaynak  |Etkinlik gezgininde bildirilen |
|---------|---------|
|Exchange         |Hayır       |
|SharePoint Online|Evet          |
|OneDrive |Evet|

## <a name="retention-label-changed"></a>Bekletme etiketi değiştirildi

Bir belge veya e-postada her etiket güncelleştirildiğinde bu olay oluşturulur.

- Belgeyi kaydetme zamanında ve e-posta gönderme zamanında yakalanır.

|Kaynak  |Etkinlik gezgininde bildirilen |
|---------|---------|
|Exchange         |Hayır       |
|SharePoint Online|Evet          |
|OneDrive |Evet|

## <a name="retention-label-removed"></a>Bekletme etiketi kaldırıldı

Dosyadan veya belgeden her etiket kaldırıldığı zaman bu olay oluşturulur.

- Belgeyi kaydetme zamanında ve e-posta gönderme zamanında yakalanır.

|Kaynak  |Etkinlik gezgininde bildirilen |
|---------|---------|
|Exchange         |Hayır       |
|SharePoint Online|Evet          |
|OneDrive |Evet|

## <a name="known-issues"></a>Bilinen sorunlar
  
- Son kullanıcıya önerilen etiket aracı ipucu gösterildiğinde, bu etiket yakalanz. Ancak kullanıcı önerilen etiketi uygulamayı seçerse, etiket Önerilen Olarak Nasıl *Uygulandı alanında* *gösterilir*.

- Yaslama metni, şu anda duyarlılık etiketinin metinden ve metin SharePoint OneDrive.

- Hassas bilgi türleri şu anda Word, Excel, PowerPoint ve Outlook'ın yanı sıra SharePoint Online ve OneDrive'tan gelen otomatik SharePoint etkinlikleri için kullanılamaz.
