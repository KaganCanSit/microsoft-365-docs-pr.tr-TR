---
title: Veri yönetimi önerileri için içerik nasıl tanımlanır?
f1.keywords:
- NOCSH
ms.author: brendonb
author: cabailey
manager: laurawi
ms.date: 1/15/2019
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.collection:
- SPO_Content
ms.custom: admindeeplinkDEFENDER
ms.localizationpriority: high
search.appverid:
- MOE150
- MET150
ROBOTS: NOINDEX, NOFOLLOW
description: Aşağıdaki Microsoft 365 Defender portalı ve Microsoft 365 uyumluluk merkezi geçerli kurulumuna dayalı olarak veri idaresi için öneriler sağlar ve birkaç tıklamayla ayarlamalar yapabilirsiniz. Bu önerilerden bazıları, kurum içinde belirli içerikleri algılar ve ardından bu içeriği yönetmek için önerilen adımları sağlar. Örneğin, iş açısından kritik içerik (avukatlık ayrıcalıkları veya NDA bilgileri gibi) içeren öğeleri algılayan ve ardından gerektiğinde sınıflandırılmalarını ve saklamalarını sağlamak için bu öğelere otomatik olarak bir bekletme etiketi uygulamanız önerisinde bulunabilirsiniz. Bu konu başlığında, gördüğünüz veri yönetimi önerileri listelenir ve her birinin tetiklenirken hangi içeriğin algılandığından anlatabilirsiniz.
ms.openlocfilehash: cddd73fdd0c21605549450968db182883ab7e6ad
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/19/2021
ms.locfileid: "63006327"
---
# <a name="how-content-is-identified-for-data-governance-recommendations"></a>Veri yönetimi önerileri için içerik nasıl tanımlanır?

Aşağıdaki <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalı</a> <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">ve Microsoft 365 uyumluluk merkezi</a>, kuruluş mevcut kurulumuna dayalı olarak veri idaresi için öneriler sağlar ve birkaç tıklamayla ayarlamalar yapabilirsiniz. Bu önerilerden bazıları, kurum içinde belirli içerikleri algılar ve ardından bu içeriği yönetmek için önerilen adımları sağlar. Örneğin, iş açısından kritik içerik (avukatlık ayrıcalıkları veya NDA bilgileri gibi) içeren öğeleri algılayan ve ardından gerektiğinde sınıflandırılmalarını ve saklamalarını sağlamak için bu öğelere otomatik olarak bir bekletme etiketi uygulamanız önerisinde bulunabilirsiniz.

Bu konu başlığında, gördüğünüz veri yönetimi önerileri listelenir ve her birinin tetiklenirken hangi içeriğin algılandığından anlatabilirsiniz.

## <a name="clean-up-voicemail"></a>Sesli mesajı temizleme

Bu öneri, 'sesli mesaj' ileti türü olarak tanımlanan e-posta iletileri kullanıcıların posta kutularında algılandığında görünür. E-posta iletisi [özellikleri hakkında daha fazla bilgi Exchange](/exchange/policy-and-compliance/ediscovery/message-properties-and-search-operators#searchable-properties-in-exchange).

## <a name="label-attorney-client-privilege-content"></a>Avukat-müşteri ayrıcalık içeriğini etiketleme

Bu öneri, aşağıdaki ölçütlerden herhangi biri karşılendiğinde görüntülenir.

- Bu anahtar sözcüklerin herhangi bir bileşimi e-posta iletisi gövdesinde algılanır:
  - ACP
  - Avukat İstemcisi Ayrıcalıkları
  - Attorney-Client Ayrıcalıkları
  - Attorney-Client Ayrıcalıklı

- Bu anahtar sözcüklerin herhangi bir bileşimi SharePoint veya OneDrive algılanır:
  - ACP
  - Avukat İstemcisi Ayrıcalıkları*
  - AC Ayrıcalıkları

## <a name="retain-audio-files"></a>Ses dosyalarını koruma

Bu öneri, aşağıdaki dosya türlerinden herhangi biri E-SharePoint OneDrive.

- .MP3
- . WMA
- . WAV
- . RA
- . RAM
- .RM
- . MID
- . OGG
- . AIFF
- . PCM
- . AAC
- . FLAC
- . ALAC

## <a name="retain-cad-files"></a>CAD dosyalarını koruma

Bu öneri, aşağıdaki dosya türlerinden herhangi biri E-SharePoint OneDrive.

- .3DXML
- . ACIS
- . ARC
- . ASM
- .CAT*
- . CGR
- . DW*
- . DX*
- . EDRW
- . IAM
- . IGES
- . IGS
- . IPT
- . JT
- . MF1
- . NEU
- . PAR
- . PKG
- . ÇÇY
- . PRT
- . PSM
- . PWD
- . SLD*
- . ADIM
- . STL
- . STP
- . U3D
- . UNV
- . VRML
- . WRL
- . X_*
- . XAS
- . XMT*
- . XPR

## <a name="retain-image-files"></a>Resim dosyalarını koruma

Bu öneri, aşağıdaki dosya türlerinden herhangi biri E-SharePoint OneDrive.

- . JPEG
- .GIF
- . TIF*
- .BMP
- .PNG
- . RAW
- .PSD
- . PSP
- .JPG
- . EXIF
- . PPM
- . PGM
- . PBM
- . PNM
- . WEBP

## <a name="retain-nda-content"></a>NDA içeriğini koruma

Bu öneri, aşağıdaki ölçütlerden herhangi biri karşılendiğinde görüntülenir.

- Bu anahtar sözcüklerin herhangi bir bileşimi e-posta iletisi gövdesinde algılanır:
  - NDA
  - "Gizlilik Sözleşmesi"
  - "Gizlilik Sözleşmesi"

- Bu anahtar sözcüklerin herhangi bir bileşimi, .PDF veya .DOC dosyalarında SharePoint OneDrive:
  - NDA
  - Gizlilik Sözleşmesi

## <a name="retain-software-development-files"></a>Yazılım geliştirme dosyalarını koruma

Bu öneri, aşağıdaki dosya türlerinden herhangi biri E-SharePoint OneDrive.

- . ASAX
- . ASM
- . ASP*
- .BAT
- .CONFIG
- .CS
- . CSS
- . YERKARAKA
- .HTM*
- . INC
- . JAD
- . JAVA
- .JS*
- . LIB
- . O
- . PHP
- . RC
- . RESX
- . RPT
- . RSS
- . SCPT
- . SRC
- . VB*
- . WSF
- . XCODEPROJ
- .XML
- . XSD
- . XSL*

## <a name="retain-video-files"></a>Video dosyalarını koruma

Bu öneri, aşağıdaki dosya türlerinden herhangi biri E-SharePoint OneDrive.

- . AVCHD
- .AVI
- . FLV
- . MOV
- . MP2V
- .MP4
- . MP4V
- . MPE
- .MPEG
- . MPEG1
- . MPEG2
- . MPEG4
- .MPG
- . MPG2
- . MPG4
- . WMV
- . XMV
