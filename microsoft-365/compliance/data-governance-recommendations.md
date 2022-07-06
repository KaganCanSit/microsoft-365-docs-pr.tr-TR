---
title: veri idaresi önerileri için içerik nasıl tanımlanır?
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
description: Microsoft 365 Defender portalı ve Microsoft Purview uyumluluk portalı kuruluşunuzun geçerli kurulumuna göre veri idaresi için öneriler sağlar ve birkaç tıklamayla ayarlamanızı sağlar. Bu önerilerden bazıları kuruluşunuzdaki belirli içeriği algılar ve ardından bu içeriği yönetmek için önerilen adımları sağlar. Örneğin, bir öneri iş açısından kritik içerik (avukat-müşteri ayrıcalığı veya NDA bilgileri gibi) içeren öğeleri algılayabilir ve sonra gerektiğinde sınıflandırılıp saklanmalarını sağlamak için bu öğelere otomatik olarak bir bekletme etiketi uygulamanıza izin verebilir. Bu konu başlığı altında, görebileceğiniz veri idaresi önerileri listelenir ve her birini tetikleyen hangi içeriğin algılandığı açıklanır.
ms.openlocfilehash: 27fcc5dd07695be355fc15ba2145ffa5540673ca
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66637317"
---
# <a name="how-content-is-identified-for-data-governance-recommendations"></a>veri idaresi önerileri için içerik nasıl tanımlanır?

<a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalı</a> ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalı</a> kuruluşunuzun geçerli kurulumuna göre veri idaresi için öneriler sağlar ve birkaç tıklamayla ayarlamanızı sağlar. Bu önerilerden bazıları kuruluşunuzdaki belirli içeriği algılar ve ardından bu içeriği yönetmek için önerilen adımları sağlar. Örneğin, bir öneri iş açısından kritik içerik (avukat-müşteri ayrıcalığı veya NDA bilgileri gibi) içeren öğeleri algılayabilir ve sonra gerektiğinde sınıflandırılıp saklanmalarını sağlamak için bu öğelere otomatik olarak bir bekletme etiketi uygulamanıza izin verebilir.

Bu konu başlığı altında, görebileceğiniz veri idaresi önerileri listelenir ve her birini tetikleyen hangi içeriğin algılandığı açıklanır.

## <a name="clean-up-voicemail"></a>Sesli mesajı temizleme

Bu öneri, kullanıcıların posta kutularında 'sesli mesaj' ileti türü olarak tanımlanan e-posta iletileri algılandığında görünür. [Exchange'de ileti özellikleri](/exchange/policy-and-compliance/ediscovery/message-properties-and-search-operators#searchable-properties-in-exchange) hakkında daha fazla bilgi edinin.

## <a name="label-attorney-client-privilege-content"></a>Etiket avukat-istemci ayrıcalık içeriği

Bu öneri, aşağıdaki ölçütlerden biri karşılandığında görüntülenir.

- E-posta iletisinin gövdesinde bu anahtar sözcüklerin herhangi bir bileşimi algılanır:
  - ACP
  - Avukat İstemci Ayrıcalığı
  - Attorney-Client Ayrıcalığı
  - Attorney-Client Privileged

- SharePoint veya OneDrive dosyalarında bu anahtar sözcüklerin herhangi bir bileşimi algılanır:
  - ACP
  - Avukat İstemci Ayrıcalığı*
  - AC Ayrıcalığı

## <a name="retain-audio-files"></a>Ses dosyalarını saklama

SharePoint veya OneDrive'da aşağıdaki dosya türlerinden herhangi biri algılandığında bu öneri görüntülenir.

- .MP3
- . WMA
- . WAV
- . RA
- . RAM
- RM
- . ORTA
- . OGG
- . AIFF
- . PCM
- . AAC
- . FLAC
- . ALAC

## <a name="retain-cad-files"></a>CAD dosyalarını saklama

SharePoint veya OneDrive'da aşağıdaki dosya türlerinden herhangi biri algılandığında bu öneri görüntülenir.

- .3DXML
- . ACİS
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
- . ÇHC
- . PRT
- . PSM
- . PWD
- . SLD*
- . ADIM
- . STL
- . STP
- . U3D
- . ÜNV
- . VRML
- . WRL
- . X_*
- . XAS
- . XMT*
- . XPR

## <a name="retain-image-files"></a>Görüntü dosyalarını koruma

SharePoint veya OneDrive'da aşağıdaki dosya türlerinden herhangi biri algılandığında bu öneri görüntülenir.

- . JPEG
- .GIF
- . TIF*
- .BMP
- .PNG
- . HAM
- .PSD
- . PSP
- .JPG
- . EXIF
- . PPM
- . PGM
- . PBM
- . PNM
- . WEBP

## <a name="retain-nda-content"></a>NDA içeriğini saklama

Bu öneri, aşağıdaki ölçütlerden biri karşılandığında görüntülenir.

- E-posta iletisinin gövdesinde bu anahtar sözcüklerin herhangi bir bileşimi algılanır:
  - NDA
  - "Gizlilik Sözleşmesi"
  - "Gizlilik Sözleşmesi"

- SharePoint veya OneDrive'daki .PDF veya .DOC dosyalarında bu anahtar sözcüklerin herhangi bir bileşimi algılanır:
  - NDA
  - Gizlilik Sözleşmesi

## <a name="retain-software-development-files"></a>Yazılım geliştirme dosyalarını koruma

SharePoint veya OneDrive'da aşağıdaki dosya türlerinden herhangi biri algılandığında bu öneri görüntülenir.

- . ASAX
- . ASM
- . ASP*
- .BAT
- .CONFIG
- CS
- . CSS
- . DİSKO
- .HTM*
- . INC
- . JAD
- . JAVA
- .JS*
- . LİB
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

## <a name="retain-video-files"></a>Video dosyalarını tutma

SharePoint veya OneDrive'da aşağıdaki dosya türlerinden herhangi biri algılandığında bu öneri görüntülenir.

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
