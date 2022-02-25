---
title: Windows güncelleştirmesi içgörüleri
description: ''
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: b3b1f43217b3be285f20925065bf9710a38f9606
ms.sourcegitcommit: cebbdd393dcfd93ff43a1ab66ad70115853f83e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2021
ms.locfileid: "62959646"
---
# <a name="windows-security-update-insights"></a>Windows güncelleştirmesi içgörüleri
Bu görünüm, Microsoft Yönetilen Masaüstü cihazlarınız için güvenlik güncelleştirmelerinin durumuna genel bir bakış sağlar. 

Kullanım verilerini görüntülemek için Güvenlik <strong>güncelleştirmeleri Windows seçin</strong>.

![Windows güncelleştirmeleri bölmesi: Sol sütunda cihaz durumunun çubuk grafikleri, orta sütunda zaman içinde dağıtımın ilerleme durumunu güncelleştirin, dağıtım grubu tarafından etkin cihazların yüzdesi ve doğru sütundaki %95 dağıtım hedefine ulaşmak için geçen gün sayısı.](../../media/update-insights.jpg)

## <a name="device-status"></a>Cihaz durumu

Cihazların Güncelleştirme Windows güncelleştiril ikisi sürekli olmak zorunda olmakla birlikte, en az altı saat hazırda bekleme modunda değil, İnternet'e bağlı olmalı. Bu gereksinimleri karşılamayan bir cihaz güncelleştirilebilir olsa da, bunları karşılaması en yüksek güncelleştirme olasılığına sahiptir. 

Cihaz etkinliğini şu şartlarla güncelleştirin Windows kategorilere ayırabilirsiniz:

- <strong>Etkin:</strong> En son güvenlik güncelleştirmesi sürümü için en düşük etkinlik ölçütlerini (altı saat, iki sürekli) karşımış ve en az beş günde bir Microsoft Intune olan cihazlar
- <strong>Eşitlenen:</strong> Intune ile son 28 gün içinde iade olan cihazlar
- <strong>Eşit değil:</strong> Son 28 <i></i> gün içinde Intune ile iade 112 saat içinde teslim 12 saat içinde teslim 12:




## <a name="update-version-status"></a>Sürüm durumunu güncelleştirme

Microsoft, güvenlik güncelleştirmelerini her ayın ikinci Salı günü yayımlar. Her sürüm, bilinen güvenlik açıkları için önemli güncelleştirmeler ekler. Microsoft Yönetilen Masaüstü, yönetilen cihazlarının %95'ini her ay kullanılabilen en son güvenlik güncelleştirmesi ile güncelleştirilir. Güvenlik güncelleştirmeleri bazen yeni tehditlere acil şekilde çözüm almak için bazen yayımlar. Microsoft Yönetilen Masaüstü bu güncelleştirmeleri benzer şekilde dağıtıyor.

Güvenlik güncelleştirme sürümlerinin durumunu şu koşullarla kategorilere ayırabiliyoruz:

- <strong>Geçerli:</strong> Geçerli ay içinde yayımlanan güncelleştirmeyi çalıştıran cihazlar
- <strong>Önceki:</strong> Geçen ay yayımlanan güncelleştirmeyi çalıştıran cihazlar
- <strong>Daha Eski:</strong> Geçen aydan önce yayımlanan tüm güvenlik güncelleştirmelerini çalıştıran cihazlar

Daha Eski kategorisinde birkaç cihaz görüyorsanız<strong></strong>, büyük veya büyüyen bir nüfus, büyük olasılıkla araştırmamız için Microsoft Yönetilen Masaüstü'ne bildirmeniz gereken sistemsel bir soruna işaret ediyordur.


## <a name="deployment-progress"></a>Dağıtım ilerleme durumu

Her güvenlik güncelleştirmesi sürüm döngüsünün başında, Microsoft Yönetilen Masaüstü cihaz nüfusunun bir anlık görüntüsünü alır ve dağıtım hedefini bu popülasyonın %95'inde ayarlar. Dağıtım <strong>ilerleme alanı</strong> , günlük olarak güncelleştirilen ve güncelleştirme dağıtımının her sürümde bu hedefe ne kadar yakın bir hedefle karşılanıyor takip eden geçmiş bir eğilimi gösterir. Bu grafik yalnızca Etkin durumdaki cihazları gösterir.

Bu verileri, sağ üstteki açılan menüyü kullanarak önceki güncelleştirme döngüleri için görüntüebilirsiniz. Bu menüden seçim dönemi tüm sayfa bilgileri için geçerlidir.

<strong>Dağıtıma göre güncelleştirilmiş etkin cihazlar grubu</strong> alanı, Microsoft Yönetilen Masaüstü dağıtım gruplarının her biri için güncelleştirme yükleme işleminin ilerlemesini göstererek farklı bir görünüm sunar.

Hedef <strong>alana ulaşacak günler</strong> , geçerli güvenlik güncelleştirmesi ile güncelleştirilen toplam cihaz sayısının %95'inin ne kadar uzun olduğunu gösterir. Dağıtım devam ederken, seçilen güncelleştirme için %95 <strong>hedefine</strong> ulaşana kadar bu alanda Güncelleştirme devam ediyor olarak görüntülenir.

## <a name="device-details-area"></a>Cihaz ayrıntıları alanı

Panonun en altında, Cihaz durumu ve Güncelleştirme sürümü durumu dahil olmak üzere cihazlarınız [için ayrıntılı](#device-status) [bilgiler gösteren bir tablo yer alır](#update-version-status). Bu listede arama veya listelenen herhangi bir değere göre filtre uygulama.


![Cihaz adı, atanan kullanıcı, cihaz durumu, güncelleştirme sürümü, işletim sistemi sürümü ve cihazın son eşitleme tarihiyle ilgili sütunları gösteren cihaz ayrıntıları tablosu.](../../media/security-update-insights-device-table-sterile.png)
