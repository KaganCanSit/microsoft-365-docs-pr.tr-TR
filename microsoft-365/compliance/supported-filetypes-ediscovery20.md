---
title: Dosyalarda desteklenen dosya Advanced eDiscovery
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
description: Web'de OCR işlevinin Microsoft 365 Advanced eDiscovery resim dosyası türleri de dahil olmak üzere bu dosya türlerinin Advanced eDiscovery.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 96d469d861be3392108b53811478f94d0e59f40b
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63016465"
---
# <a name="supported-file-types-in-advanced-ediscovery"></a>Dosyalarda desteklenen dosya Advanced eDiscovery

Advanced eDiscovery çok farklı düzeyde birçok dosya türü destekler. Destek dosyası türleri bu makalede aşağıdaki tablolarda açıklanmıştır. Bu liste henüz sonuç olarak değil ve doğrulama testimiz devam ettiği sürece yeni dosya türleri ekley edeceğiz. Bu tablolarda, bir dosya türünün metin ayıklama (ve görüntü dosyaları için Optik Karakter Tanıma veya OCR metin ayıklama) desteği olup olmadığını, yerel görüntüleyicide değiştirilebilir olup olmadığını ve aynı zamanda dosya üzerinde Ek Açıklama görüntüleyicisinde destek Advanced eDiscovery.

## <a name="archive--container"></a>Arşiv / Kapsayıcı

<br>

****

|Mime türü|Dosya kimliği|Meta veri ayıklama|Kapsayıcı ayıklama|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|
|application/x-7z-compressed|Evet|Evet|Evet|0,7z|
|application/x-rar-compressed|Evet|Evet|Evet|.rar|
|application/x-tar|Evet|Evet|Evet|.tar|
|application/zip|Evet|Evet|Evet|.zip|
|

## <a name="audio--video"></a>Ses / Görüntü

<br>

****

|Mime türü|Dosya kimliği|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Açıklama görüntüleyicisi|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|uygulama/mp4|Evet|Evet|Hayır|Evet|Hayır|.f4v; .m4a; .m4v; .mp4; .mp4v; .mpeg; .mpeg4|
|ses/mpeg|Evet|Evet|Hayır|Evet|Hayır|.mpeg|
|video/3gpp|Evet|Evet|Hayır|Evet|Hayır|.3gp|
|video/3gpp2|Evet|Evet|Hayır|Evet|Hayır|.3g2; .3gp2|
|video/quicktime|Evet|Evet|Hayır|Evet|Hayır|.moov; .mov; .qt|
|video/x-m4v|Evet|Evet|Hayır|Evet|Hayır|.m4v|
|

## <a name="database"></a>Veritabanı

<br>

****

|Mime türü|Dosya kimliği|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Açıklama görüntüleyicisi|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/x-msaccess|Evet|Evet|Evet|Hayır|Hayır|.mdb|
|

## <a name="email"></a>E-posta

<br>

****

|Mime türü|Dosya kimliği|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Açıklama görüntüleyicisi|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-outlook|Evet|Evet|Evet|Evet|Evet|.msg|
|ileti/rfc822|Evet|Evet|Evet|Evet|Evet|.eml|
|text/vcard-contact|Evet|Evet|Evet|Evet|Evet|.vcf|
|

## <a name="email-container"></a>E-posta Kapsayıcısı

<br>

****

|Mime türü|Dosya kimliği|Meta veri ayıklama|Kapsayıcı ayıklama|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|
|uygulama/mbox|Evet|Evet|Evet|.mbox|
|application/vnd.ms-outlook-pst|Evet|Evet|Evet|.pst|
|

## <a name="html"></a>HTML

<br>

****

|Mime türü|Dosya kimliği|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Açıklama görüntüleyicisi|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/xhtml+xml|Evet|Evet|Evet|Evet|Evet|.xhtml|
|application/xml|Evet|Evet|Evet|Evet|Evet|.xml|
|metin/html|Evet|Evet|Evet|Evet|Evet|.htm; .html; .shtml|
|

## <a name="image"></a>Görüntü

<br>

****

|Mime türü|Dosya kimliği|Meta veri ayıklama|OCR metin ayıklama|Yerel görüntüleyici|Açıklama görüntüleyicisi|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|image/bmp|Evet|Evet|Evet|Evet|Evet|.bmp|
|image/emf|Evet|Evet|Evet|Evet|Evet|.emf|
|resim/gif|Evet|Evet|Evet|Evet|Evet|.gif|
|resim/jpeg|Evet|Evet|Evet|Evet|Evet|.jpeg; .jpg|
|image/png|Evet|Evet|Evet|Evet|Evet|.png|
|image/svg+xml|Evet|Evet|Evet|Evet|Hayır|.svg|
|image/tiff|Evet|Evet|Evet|Evet|Evet|.tif|
|image/vnd.dwg|Evet|Evet|Evet|Evet|Evet|.dwg; .dxf|
|image/wmf|Evet|Evet|Evet|Evet|Evet|.wmf|
|

## <a name="microsoft-excel"></a>Microsoft Excel

<br>

****

|Mime türü|Dosya kimliği|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Açıklama görüntüleyicisi|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-excel|Evet|Evet|Evet|Evet|Evet|.dat; .xls|
|application/vnd.ms-excel.sheet.binary.macroenabled.12|Evet|Evet|Evet|Evet|Hayır|.xlsb|
|application/vnd.ms-excel.sheet.macroenabled.12|Evet|Evet|Evet|Evet|Evet|.xlsm|
|application/vnd.ms-excel.template.macroenabled.12|Evet|Evet|Evet|Hayır|Hayır|.xltm|
|application/vnd.openxmlformats-officedocument.spreadsheetml.sheet|Evet|Evet|Evet|Evet|Evet|.xlsx|
|application/vnd.openxmlformats-officedocument.spreadsheetml.template|Evet|Evet|Evet|Evet|Evet|.xltx|
|

## <a name="microsoft-onenote"></a>Microsoft OneNote

<br>

****

|Mime türü|Dosya kimliği|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Açıklama görüntüleyicisi|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/onenote|Evet|Evet|Evet|Hayır|Hayır|.one|
|

## <a name="microsoft-powerpoint"></a>Microsoft PowerPoint

<br>

****

|Mime türü|Dosya kimliği|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Açıklama görüntüleyicisi|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-powerpoint|Evet|Evet|Evet|Evet|Evet|.pot; .pps; .ppt|
|application/vnd.openxmlformats-officedocument.presentationml.presentation|Evet|Evet|Evet|Evet|Evet|.pptx|
|application/vnd.openxmlformats-officedocument.presentationml.slideshow|Evet|Evet|Evet|Evet|Evet|.ppsx|
|application/vnd.openxmlformats-officedocument.presentationml.template|Evet|Evet|Evet|Evet|Evet|.potx|
|

## <a name="microsoft-project"></a>Microsoft Project

<br>

****

|Mime türü|Dosya kimliği|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Açıklama görüntüleyicisi|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-project|Evet|Evet|Evet|Hayır|Evet|.mpp|
|

## <a name="microsoft-publisher"></a>Microsoft Publisher

<br>

****

|Mime türü|Dosya kimliği|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Açıklama görüntüleyicisi|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/x-mspublisher|Evet|Evet|Evet|Evet|Evet|.pub|
|

## <a name="microsoft-visio"></a>Microsoft Visio

<br>

****

|Mime türü|Dosya kimliği|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Açıklama görüntüleyicisi|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-visio.drawing|Evet|Evet|Evet|Evet|Hayır||
|application/vnd.visio|Evet|Evet|Evet|Evet|Evet|.vsd|
|

## <a name="microsoft-word"></a>Microsoft Word

<br>

****

|Mime türü|Dosya kimliği|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Açıklama görüntüleyicisi|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/msword|Evet|Evet|Evet|Evet|Evet|.dat; .doc|
|application/rtf|Evet|Evet|Evet|Evet|Evet|.doc; .rtf|
|application/vnd.ms-word.document.macroenabled.12|Evet|Evet|Evet|Evet|Evet|.docm|
|application/vnd.ms-word.template.macroenabled.12|Evet|Evet|Evet|Evet|Evet|.dotm|
|application/vnd.openxmlformats-officedocument.wordprocessingml.document|Evet|Evet|Evet|Evet|Evet|.docx|
|application/vnd.openxmlformats-officedocument.wordprocessingml.template|Evet|Evet|Evet|Evet|Evet|.dotx|
|

## <a name="microsoft-works"></a>Microsoft Works

<br>

****

|Mime türü|Dosya kimliği|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Açıklama görüntüleyicisi|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.ms-works-ss|Evet|Evet|Hayır|Hayır|Hayır|.wps|
|application/vnd.ms-works-wp|Evet|Evet|Hayır|Hayır|Hayır|.wps|
|

## <a name="open-document-format"></a>Belge Biçimini Aç

<br>

****

|Mime türü|Dosya kimliği|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Açıklama görüntüleyicisi|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.oasis.opendocument.text|Evet|Evet|Evet|Evet|Evet|.odt|
|

## <a name="other"></a>Diğer

<br>

****

|Mime türü|Dosya kimliği|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Açıklama görüntüleyicisi|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/json|Evet|Evet|Evet|Evet|Evet|yok|
|uygulama/octet-stream|Evet|Hayır|Hayır|Hayır|Hayır|.fluid|
|application/vnd.ms-graph|Evet|Evet|Hayır|Hayır|Hayır||
|application/winhlp|Evet|Evet|Hayır|Hayır|Hayır|.hlp|
|application/x-tnef|Evet|Evet|Hayır|Hayır|Hayır||
|

## <a name="plain-text"></a>Düz Metin

<br>

****

|Mime türü|Dosya kimliği|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Açıklama görüntüleyicisi|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|text/csv|Evet|Evet|Evet|Evet|Evet|.csv|
|metin/düz|Evet|Evet|Evet|Evet|Evet|.con; .css; .csv; .dat; .pl; .txt|
|

## <a name="portable-document-format"></a>Taşınabilir Belge Biçimi

<br>

****

|Mime türü|Dosya kimliği|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Açıklama görüntüleyicisi|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/pdf|Evet|Evet|Evet|Evet|Evet|.pdf|
|

## <a name="word-perfect"></a>Word Mükemmel

<br>

****

|Mime türü|Dosya kimliği|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Açıklama görüntüleyicisi|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.wordperfect; version=5.0|Evet|Evet|Evet|Hayır|Hayır|.wpd|
|application/vnd.wordperfect; version=5.1|Evet|Evet|Evet|Hayır|Hayır|.wpd|
|application/vnd.wordperfect; version=6.x|Evet|Evet|Evet|Hayır|Hayır|.wpd|
|

## <a name="word-pro"></a>Word Pro

<br>

****

|Mime türü|Dosya kimliği|Meta veri ayıklama|Metin ayıklama|Yerel görüntüleyici|Açıklama görüntüleyicisi|Olası Uzantılar|
|---|:---:|:---:|:---:|:---:|:---:|:---:|
|application/vnd.lotus-wordpro|Evet|Evet|Hayır|Hayır|Hayır|.lwp|
|
