---
title: eBulma'da desteklenen dosya türleri (Premium)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: eBulma'da (Premium) OCR işlevselliği tarafından desteklenen görüntü dosyası türleri de dahil olmak üzere Microsoft 365 eBulma'da (Premium) desteklenen dosya türlerinin listesi.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 95adaf84f5281b943720be595b0e0e4aababd91f
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64996756"
---
# <a name="supported-file-types-in-ediscovery-premium"></a>eBulma'da desteklenen dosya türleri (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft Purview eKeşif (Premium) birçok farklı düzeyde birçok dosya türünü destekler. Destek dosyaları türleri bu makaledeki aşağıdaki tablolarda açıklanmıştır. Bu liste sonlandırılmamıştır ve doğrulama testimize devam ettiğimizde yeni dosya türleri ekleyeceğiz. Bu tablolar, metin ayıklama (ve görüntü dosyaları için Optik Karakter Tanıma veya OCR metin ayıklama) için bir dosya türünün desteklenip desteklenmediğini, yerel görüntüleyicide görüntülenebilir olduğunu ve ayrıca eBulma'da (Premium) Ek Açıklama görüntüleyicisinde desteklenip desteklenmediğini gösterir.

## <a name="archive--container"></a>Arşiv / Kapsayıcı

<br>

****

|Mime türü|Dosya tanımlama|Meta veri ayıklama|Kapsayıcı ayıklama|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|
|application/x-7z-compressed|Evet|Evet|Evet|.7z|
|application/x-rar-compressed|Evet|Evet|Evet|.rar|
|application/x-tar|Evet|Evet|Evet|.tar|
|application/zip|Evet|Evet|Evet|.zip|
|

## <a name="audio--video"></a>Ses / Video

<br>

****

|Mime türü|Dosya tanımlama|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Görüntüleyiciye açıklama ekleme|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/mp4|Evet|Evet|Hayır|Evet|Hayır|.f4v; .m4a; .m4v; .mp4; .mp4v; .mpeg; .mpeg4|
|audio/mpeg|Evet|Evet|Hayır|Evet|Hayır|.mpeg|
|video/3gpp|Evet|Evet|Hayır|Evet|Hayır|.3gp|
|video/3gpp2|Evet|Evet|Hayır|Evet|Hayır|.3g2; .3gp2|
|video/quicktime|Evet|Evet|Hayır|Evet|Hayır|.moov; .mov; .qt|
|video/x-m4v|Evet|Evet|Hayır|Evet|Hayır|.m4v|
|

## <a name="database"></a>Veritabanı

<br>

****

|Mime türü|Dosya tanımlama|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Görüntüleyiciye açıklama ekleme|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/x-msaccess|Evet|Evet|Evet|Hayır|Hayır|Mdb|
|

## <a name="email"></a>E-posta

<br>

****

|Mime türü|Dosya tanımlama|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Görüntüleyiciye açıklama ekleme|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-outlook|Evet|Evet|Evet|Evet|Evet|Msg|
|message/rfc822|Evet|Evet|Evet|Evet|Evet|Eml|
|text/vcard-contact|Evet|Evet|Evet|Evet|Evet|Vcf|
|

## <a name="email-container"></a>E-posta Kapsayıcısı

<br>

****

|Mime türü|Dosya tanımlama|Meta veri ayıklama|Kapsayıcı ayıklama|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|
|application/mbox|Evet|Evet|Evet|Mbox|
|application/vnd.ms-outlook-pst|Evet|Evet|Evet|Pst|
|

## <a name="html"></a>HTML

<br>

****

|Mime türü|Dosya tanımlama|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Görüntüleyiciye açıklama ekleme|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/xhtml+xml|Evet|Evet|Evet|Evet|Evet|.xhtml|
|application/xml|Evet|Evet|Evet|Evet|Evet|.xml|
|metin/html|Evet|Evet|Evet|Evet|Evet|.htm; .html; .shtml|
|

## <a name="image"></a>Görüntü

<br>

****

|Mime türü|Dosya tanımlama|Meta veri ayıklama|OCR metin ayıklama|Yerel görüntüleyici|Görüntüleyiciye açıklama ekleme|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|image/bmp|Evet|Evet|Evet|Evet|Evet|.bmp|
|image/emf|Evet|Evet|Evet|Evet|Evet|Emf|
|resim/gif|Evet|Evet|Evet|Evet|Evet|.gif|
|image/jpeg|Evet|Evet|Evet|Evet|Evet|.jpeg; .jpg|
|resim/png|Evet|Evet|Evet|Evet|Evet|.png|
|image/svg+xml|Evet|Evet|Evet|Evet|Hayır|.svg|
|image/tiff|Evet|Evet|Evet|Evet|Evet|Tif|
|image/vnd.dwg|Evet|Evet|Evet|Evet|Evet|.dwg; .dxf|
|image/wmf|Evet|Evet|Evet|Evet|Evet|Wmf|
|

## <a name="microsoft-excel"></a>Microsoft Excel

<br>

****

|Mime türü|Dosya tanımlama|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Görüntüleyiciye açıklama ekleme|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-excel|Evet|Evet|Evet|Evet|Evet|.dat; .xls|
|application/vnd.ms-excel.sheet.binary.macroenabled.12|Evet|Evet|Evet|Evet|Hayır|Xlsb|
|application/vnd.ms-excel.sheet.macroenabled.12|Evet|Evet|Evet|Evet|Evet|Xlsm|
|application/vnd.ms-excel.template.macroenabled.12|Evet|Evet|Evet|Hayır|Hayır|Xltm|
|application/vnd.openxmlformats-officedocument.spreadsheetml.sheet|Evet|Evet|Evet|Evet|Evet|.xlsx|
|application/vnd.openxmlformats-officedocument.spreadsheetml.template|Evet|Evet|Evet|Evet|Evet|Xltx|
|

## <a name="microsoft-onenote"></a>Microsoft OneNote

<br>

****

|Mime türü|Dosya tanımlama|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Görüntüleyiciye açıklama ekleme|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/onenote|Evet|Evet|Evet|Hayır|Hayır|.one|
|

## <a name="microsoft-powerpoint"></a>Microsoft PowerPoint

<br>

****

|Mime türü|Dosya tanımlama|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Görüntüleyiciye açıklama ekleme|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-powerpoint|Evet|Evet|Evet|Evet|Evet|.pot; .pps; .ppt|
|application/vnd.openxmlformats-officedocument.presentationml.presentation|Evet|Evet|Evet|Evet|Evet|.pptx|
|application/vnd.openxmlformats-officedocument.presentationml.slideshow|Evet|Evet|Evet|Evet|Evet|Ppsx|
|application/vnd.openxmlformats-officedocument.presentationml.template|Evet|Evet|Evet|Evet|Evet|Potx|
|

## <a name="microsoft-project"></a>Microsoft Project

<br>

****

|Mime türü|Dosya tanımlama|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Görüntüleyiciye açıklama ekleme|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-project|Evet|Evet|Evet|Hayır|Evet|Mpp|
|

## <a name="microsoft-publisher"></a>Microsoft Publisher

<br>

****

|Mime türü|Dosya tanımlama|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Görüntüleyiciye açıklama ekleme|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/x-mspublisher|Evet|Evet|Evet|Evet|Evet|.pub|
|

## <a name="microsoft-visio"></a>Microsoft Visio

<br>

****

|Mime türü|Dosya tanımlama|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Görüntüleyiciye açıklama ekleme|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-visio.drawing|Evet|Evet|Evet|Evet|Hayır||
|application/vnd.visio|Evet|Evet|Evet|Evet|Evet|.vsd|
|

## <a name="microsoft-word"></a>Microsoft Word

<br>

****

|Mime türü|Dosya tanımlama|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Görüntüleyiciye açıklama ekleme|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/msword|Evet|Evet|Evet|Evet|Evet|.dat; .doc|
|application/rtf|Evet|Evet|Evet|Evet|Evet|.doc; .rtf|
|application/vnd.ms-word.document.macroenabled.12|Evet|Evet|Evet|Evet|Evet|Docm|
|application/vnd.ms-word.template.macroenabled.12|Evet|Evet|Evet|Evet|Evet|Dotm|
|application/vnd.openxmlformats-officedocument.wordprocessingml.document|Evet|Evet|Evet|Evet|Evet|.docx|
|application/vnd.openxmlformats-officedocument.wordprocessingml.template|Evet|Evet|Evet|Evet|Evet|Dotx|
|

## <a name="microsoft-works"></a>Microsoft Works

<br>

****

|Mime türü|Dosya tanımlama|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Görüntüleyiciye açıklama ekleme|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-works-ss|Evet|Evet|Hayır|Hayır|Hayır|Wps|
|application/vnd.ms-works-wp|Evet|Evet|Hayır|Hayır|Hayır|Wps|
|

## <a name="open-document-format"></a>Belge Biçimini Aç

<br>

****

|Mime türü|Dosya tanımlama|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Görüntüleyiciye açıklama ekleme|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.oasis.opendocument.text|Evet|Evet|Evet|Evet|Evet|Odt|
|

## <a name="other"></a>Diğer

<br>

****

|Mime türü|Dosya tanımlama|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Görüntüleyiciye açıklama ekleme|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/json|Evet|Evet|Evet|Evet|Evet|yok|
|application/octet-stream|Evet|Hayır|Hayır|Hayır|Hayır|.fluid|
|application/vnd.ms-graph|Evet|Evet|Hayır|Hayır|Hayır||
|application/winhlp|Evet|Evet|Hayır|Hayır|Hayır|Hlp|
|application/x-tnef|Evet|Evet|Hayır|Hayır|Hayır||
|

## <a name="plain-text"></a>Düz Metin

<br>

****

|Mime türü|Dosya tanımlama|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Görüntüleyiciye açıklama ekleme|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|metin/csv|Evet|Evet|Evet|Evet|Evet|.csv|
|metin/düz|Evet|Evet|Evet|Evet|Evet|.con; .css; .csv; .dat; .pl; .txt|
|

## <a name="portable-document-format"></a>Taşınabilir Belge Biçimi

<br>

****

|Mime türü|Dosya tanımlama|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Görüntüleyiciye açıklama ekleme|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|uygulama/pdf|Evet|Evet|Evet|Evet|Evet|.pdf|
|

## <a name="word-perfect"></a>Word Perfect

<br>

****

|Mime türü|Dosya tanımlama|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Görüntüleyiciye açıklama ekleme|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.wordperfect; version=5.0|Evet|Evet|Evet|Hayır|Hayır|.wpd|
|application/vnd.wordperfect; version=5.1|Evet|Evet|Evet|Hayır|Hayır|.wpd|
|application/vnd.wordperfect; version=6.x|Evet|Evet|Evet|Hayır|Hayır|.wpd|
|

## <a name="word-pro"></a>Word Pro

<br>

****

|Mime türü|Dosya tanımlama|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Görüntüleyiciye açıklama ekleme|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.lotus-wordpro|Evet|Evet|Hayır|Hayır|Hayır|.lwp|
|
