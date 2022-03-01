---
title: eBulma'da şifre çözme
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
description: eBulma araçlarının e Microsoft 365 e eklenmiş ve SharePoint Online'da depolanan şifrelenmiş belgeleri işleme hakkında bilgi OneDrive İş.
ms.openlocfilehash: aa6d6a72353378f98b9e567500233b4c26f6221c
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021676"
---
# <a name="decryption-in-microsoft-365-ediscovery-tools"></a>eK bulma Microsoft 365 şifre çözme

Şifreleme, dosya koruma ve bilgi koruma stratejinizin önemli bir bölümüdir. Her tür kuruluş, kuruluş içindeki hassas içeriği korumak ve yalnızca doğru kişilerin bu içeriğe erişimi olduğundan emin olmak için şifreleme teknolojisi kullanır.

Şifreli içerik üzerinde yaygın eBulma görevlerini yürütmek için, eBulma yöneticilerinin içerik aramalarından, Çekirdek eBulma olaylarından ve diğer olaylardan dışarı aktarıldıklarında e-posta iletisi içeriğinin şifresini çözmek Advanced eDiscovery gerekir. Microsoft şifreleme teknolojileriyle şifrelenen içerik, dışarı aktarana kadar gözden geçirilemmdi.

eBulma iş akışında şifreli içeriğin yönetimini kolaylaştırmak için Microsoft 365, eBulma araçları artık e-posta iletilerine eklenmiş ve Exchange Online'te gönderilen şifrelenmiş dosyaların şifresini çözme işlemlerini dahil Exchange Online.<sup> 1</sup> Ek olarak, SharePoint Online ve OneDrive İş şifreli belgelerin şifresini Advanced eDiscovery çözebilirsiniz.

Bu yeni özellik öncesinde, yalnızca hak yönetimi tarafından korunan e-posta iletisi içeriğinin (ekli dosyalar değil) şifresi çözülmüş. eBulma iş SharePoint OneDrive şifreli belgeler şifreleri çözülemedi. Artık Microsoft şifreleme teknolojisiyle şifrelenmiş dosyalar bir SharePoint veya OneDrive hesabında yer alıyor; arama sonuçları önizleme için hazır olduğunda, Advanced eDiscovery'te gözden geçirme kümesine ekleniyor ve dışarı aktarıldı. Buna ek olarak, e SharePoint OneDrive iletiye eklenmiş e-posta ve posta iletilerine eklenen şifrelenmiş belgelerde de arama özelliği kullanılabilir. Bu şifre çözme özelliği, eBulma yöneticilerinin arama sonuçlarını önizleme sırasında şifrelenmiş e-posta eklerinin ve site belgelerinin içeriğini görüntülemelerine ve Advanced eDiscovery'te bir gözden geçirme kümesine eklendikten sonra bunları incelemelerine olanak sağlar.

## <a name="supported-encryption-technologies"></a>Desteklenen şifreleme teknolojileri

Microsoft eBulma araçları, Microsoft şifreleme teknolojileriyle şifrelenmiş öğeleri destekler. Bu teknolojiler Azure Hak Yönetimi ve Microsoft Bilgi Koruması (özel duyarlılık etiketleri) teknolojileridir. Microsoft şifreleme teknolojileri hakkında daha fazla bilgi için bkz. [Şifreleme](encryption.md). Üçüncü taraf şifreleme teknolojileri tarafından şifrelenen içerikler desteklenmemektedir. Örneğin, Microsoft olmayan teknolojilerle şifrelenmiş içerikleri önizleme veya dışarı aktarma özelliği desteklenmemektedir.

> [!NOTE]
> Bir Office 365 İleti Şifrelemesi [(OME)](add-your-organization-brand-to-encrypted-messages.md) özel markalama şablonuyla gönderilen e-posta iletilerinin şifresini çözme aracı, Microsoft eKbulma araçları tarafından desteklenmiyor. Bir OME özel markalama şablonu kullanılırken, e-posta iletileri alıcının posta kutusu yerine OME portalına teslim edilir. Bu nedenle, oME şifreli iletileri aramak için eBulma araçlarını kullanaasınız çünkü bu iletiler alıcının posta kutusu tarafından hiçbir zaman alınmz.

## <a name="ediscovery-activities-that-support-encrypted-items"></a>Şifreli öğeleri destekleyen eBulma etkinlikleri

Aşağıdaki tabloda Microsoft 365, SharePoint ve OneDrive'de e-posta iletilerine ekli şifrelenmiş dosyalara eklenmiş şifrelenmiş dosyalar üzerinde eBulma araçları üzerinde SharePoint desteklenen görevler OneDrive. Bu desteklenen görevler, aramanın ölçütlerine uyan şifrelenmiş dosyalar üzerinde gerçekleştirilebilir. Bir değer `N/A` , ilgili eBulma aracında işlevin olmadığını gösterir.

|eBulma görevi  |İçerik arama  |Core eKovery  |Gelişmiş eKeşif  |
|:---------|:---------|:---------|:---------|
|Sitelerde ve e-posta eklerinin şifreli dosyalarında içerik <sup>arama1</sup>     |Hayır      |Hayır      |Evet      |
|E-postaya eklenmiş şifreli dosyaları önizleme     |Evet      |Evet     |Evet       |
|Dosya ve dosyalarda şifrelenmiş SharePoint önizleme OneDrive|Hayır      |Hayır    |Evet       |
|Gözden geçirme kümesinde şifrelenmiş dosyaları gözden geçirme    |Yok      |Yok        | Evet        |
|E-postaya eklenmiş şifrelenmiş dosyaları dışarı aktarma    |Evet       |Evet  |Evet    |
|Şifrelenmiş belgeleri posta ve SharePoint belgeleri OneDrive    |Hayır       |Hayır  |Evet    |
|||||

> [!NOTE]
> <sup>1</sup> Yerel bilgisayarda bulunan ve e-posta iletisine kopyalanan bulut ekleri şifrelenen dosyalar eBulma için şifrelenmez ve dizine alınamaz. Bu senaryolar için daha fazla bilgi ve geçici çözüm için, bu [](#decryption-limitations-with-email-attachments) makalenin E-posta ekleriyle birlikte şifre çözme sınırlamaları bölümüne bakın.

## <a name="decryption-limitations-with-sensitivity-labels-in-sharepoint-and-onedrive"></a>E-SharePoint'de duyarlılık etiketleriyle şifre çözme OneDrive

eBulma, şifrelemeyi uygulanan bir duyarlılık SharePoint ve OneDrive aşağıdaki ayarlardan biri ile yapılandırıldığında eKbul özelliği SharePoint ve OneDrive'de şifrelenmiş dosyaları desteklemez:

- Kullanıcılar, etiketi belgeye el ile uygulayabilecek izinler atayabilecektir. Bu bazen kullanıcı tanımlı *izinler olarak da adlandırılır*.

- Belgeye kullanıcı erişiminin Hiçbir zaman dışında bir değere ayarlanmış bir sona erme ayarı **vardır**.

Bu ayarlar hakkında daha fazla bilgi için, Şifrelemeyi uygulamak için duyarlılık etiketlerini kullanarak içeriğe erişimi kısıtlama bölümündeki "Şifreleme [ayarlarını yapılandırma" bölümüne bakın](encryption-sensitivity-labels.md#configure-encryption-settings).

Önceki ayarlarla şifrelenen belgeler yine de eBulma araması tarafından döndürülebilirsiniz. Bu durum, bir belge özelliği (başlık, yazar veya değiştirme tarihi gibi) arama ölçütleriyle eşleildiğinde olabilir. Bu belgeler arama sonuçlarına dahil olsa da önizleme veya gözden geçirılamaz. Bu belgeler, başka bir dosyada dışarı aktarıldıklarında da Advanced eDiscovery.

> [!IMPORTANT]
> Şifre çözme, yerel olarak şifrelenen ve daha sonra başka bir klasöre veya başka bir SharePoint OneDrive. Örneğin, Azure Information Protection (AIP) istemcisi tarafından şifrelenen ve sonra Azure Microsoft 365'a yüklenen yerel dosyalar desteklenmez. Şifre çözme için yalnızca SharePoint veya OneDrive dosyalarda şifrelenir.

## <a name="decryption-limitations-with-email-attachments"></a>E-posta ekleriyle ilgili şifre çözme sınırlamaları

Aşağıdaki senaryolarda, e-posta iletilerine eklenmiş dosyaların şifresini çözmeyle ilgili sınırlamalar açık almaktadır. Bu senaryo açıklamaları, bu sınırlamaları azaltmaya yönelik geçici çözümler de içerir.

- Yerel bir bilgisayarda bulunan (ve SharePoint sitesinde veya OneDrive hesabında depolanmayan) bir dosya e-posta iletisine iliştirilmişse ve e-posta iletisine şifrelemeyi içeren bir duyarlılık etiketi eklenmişse, ekli dosyanın şifresini eKbulma yoluyla çözülamaz. Bu, alıcının posta kutusunun anahtar sözcük arama sorgusunu çalıştırırsanız, şifrelenmiş dosya eklerinin bir anahtar sözcük arama sorgusuyla döndürül teslimi anlamına gelir.

  Bu sınırlamanın geçici çözümü, gönderenin posta kutusunda aynı dosya eki için arama yapmaktır. Bunun nedeni, e-posta iletisi aktarım sırasında duyarlılık etiketi tarafından uygulanan şifrelemenin uygulanmasıdır. Bu, e-posta iletisi gönderildiği zaman ekin şifrelenmiş olduğu anlamına gelir. Sonuçta, alıcının posta kutusunda aynı dosya şifrelese bile, gönderenin posta kutusunda ekli dosyanın örneği şifrelenmemiş olarak görüntülenir.

- Benzer şekilde, e-posta iletisine kopyalanan bulut ekleri (SharePoint sitesinde veya OneDrive hesabında depolanan dosyalar) (Outlook'te Kopya olarak ekle seçeneği kullanılarak) eBulma  ile şifreleri çözülamaz. Bunun nedeni, e-posta iletisi gönder uygulandığında duyarlılık etiketi tarafından uygulanan şifrelemenin de uygulanmasıdır. Bu sınırlamaya yönelik geçici çözüm, gönderenin posta kutusunda bulut eklerinin şifrelenmemiş örneğinin aranmasıdır.

Bu iki senaryoda da, bir e-posta özelliği (gönderilmiş tarih, gönderen, alıcı veya konu gibi) arama sorgusuyla eşlenirse, şifrelenmiş dosya ekleri olan e-posta iletileri eBulma araması tarafından döndürülebilirsiniz.

## <a name="requirements-for-decryption-in-ediscovery"></a>eBulma'da şifre çözme gereksinimleri

Microsoft şifreleme teknolojileriyle şifrelenmiş dosyaları önizlemek, gözden geçirmek ve dışarı aktarmak için RMS Şifre Çözme rolüne atanmış olması gerekir. Ayrıca, başka bir Advanced eDiscovery'de gözden geçirme kümesine eklenen şifrelenmiş dosyaları gözden geçirmek ve sorgulamak için bu role Advanced eDiscovery.

Bu rol varsayılan olarak, çalışma sayfasının İzinler sayfasındaki eBulma **Yöneticisi rol** grubuna Microsoft 365 uyumluluk merkezi. RMS Şifre Çözme rolü hakkında daha fazla bilgi için bkz. [eBulma izinleri atama](assign-ediscovery-permissions.md#rms-decrypt).

### <a name="decrypting-rms-protected-email-messages-and-encrypted-file-attachments-using-content-search-or-core-ediscovery"></a>İçerik arama veya Core eDiscovery kullanarak RMS korumalı e-posta iletilerinin ve şifreli dosya eklerin şifresini çözme

İçerik arama sonuçlarına dahil edilen hak korumalı (RMS korumalı) e-posta iletilerinin şifresini çözebilirsiniz. Buna ek olarak, [Microsoft](encryption.md) şifreleme teknolojisiyle şifrelenmiş ve arama sonuçlarına eklenmiş bir e-posta iletisine eklenen tüm dosyalar, dışarı aktarıldıklarında şifreleri çözüler. eBulma Yöneticisi rol grubunun üyeleri için bu şifre çözme özelliği varsayılan olarak etkindir. Bunun nedeni, RMS Şifre Çözme yönetimi rolüne varsayılan olarak bu rol grubuna atanmıştır. Şifreli e-posta iletilerini ve ekleri dışarı aktarmada aşağıdakini göz unutmayın:
  
- Daha önce de belirtildiği gibi, RMS korumalı iletileri dışarı aktarsanız bile, arama sonuçlarını tek tek iletiler olarak dışarı aktarmanız gerekir. Arama sonuçlarını bir PST dosyasına dışarı aktarırsanız, RMS korumalı iletiler şifrelenmiş olarak kalır.

- Şifresini çözülmüş iletiler **ResultsLog raporunda** tanımlanır. Bu raporda Kod Çözme Durumu adlı **bir sütun vardır** ve Kod Çözme **değerinin** değeri, şifresini çözen iletileri tanımlar.

- Arama sonuçlarını dışarı aktararak dosya eklerin şifresini çözmenin yanı sıra, arama sonuçlarının önizlemesini görüntülerken şifresi çözülen dosyanın önizlemesini de görüntüde görebilirsiniz. Hak korunan e-posta iletisi, ancak dışarı aktar olduktan sonra iletiyi görüntüebilirsiniz.

- Birinin RMS ile koruma iletilerinin ve şifreli dosya eklerinin şifresini çözmesini önlemeye gerek varsa, özel bir rol grubu oluşturmanız (yerleşik eBulma Yöneticisi rol grubunu kopyalayıp) ve ardından RMS Şifre Çözme yönetimi rolünü özel rol grubundan kaldırmanız gerekir. Ardından, iletilerin şifresini çözmek istediğiniz kişiyi özel rol grubunun bir üyesi olarak ekleyin.
