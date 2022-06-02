---
title: Microsoft 365 Defender'de Tehdit Gezgini'nde e-postaları arama ve tehditleri düzeltme
description: Microsoft 365 Defender'da Tehdit Gezgini'nde el ile düzeltme gerçekleştirme adımları, en iyi performansı elde etme ve düzeltmeyi çağıran senaryolar da dahil olmak üzere.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: article
ms.technology: mdo
ms.openlocfilehash: 6bce250add79d4119f82730c05f3042f3e3dbafe
ms.sourcegitcommit: 7ab324551afac4fd82abc015247371ebfe6ccac2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65842487"
---
# <a name="steps-to-use-manual-email-remediation-in-threat-explorer"></a>Tehdit Gezgini'nde el ile e-posta düzeltmeyi kullanma adımları

E-posta düzeltme, yöneticilerin tehdit olan e-postalar üzerinde işlem yapmalarına yardımcı olan zaten mevcut bir özelliktir.

## <a name="what-youll-need"></a>İhtiyacınız olan şey
- Office 365 için Microsoft Defender Plan 2
- Yeterli izinler (hesaba [Arama ve Temizleme](https://sip.security.microsoft.com/securitypermissions) rolü verdiğinden emin olun)

## <a name="create-and-track-the-remediation"></a>Düzeltmeyi oluşturma ve izleme

1. [Tehdit Gezgini'nde](https://security.microsoft.com/threatexplorer) **düzeltilecek bir tehdit seçin** ve Geçici *Silme* veya *Sabit Silme* gibi seçenekler sunan **İleti Eylemleri** düğmesini seçin.
1. Yan bölme açılır ve düzeltme, önem derecesi ve açıklama için ad gibi ayrıntılar istenir. Bilgiler gözden geçirildikten sonra **Gönder'e** basın.
1. Yönetici bu eylemi onaylar onaylamaz Onay Kimliği'ni ve [burada](https://security.microsoft.com/action-center/history) Microsoft 365 Defender İşlem Merkezi'nin bağlantısını görür. Bu sayfa **, eylemlerin izlenebileceği** yerdir.

    1. **eylem uyarısı Yönetici** - Uyarı kuyruğunda 'Yönetici tarafından gönderilen yönetim eylemi' adlı bir sistem uyarısı gösterilir. Bu, bir yöneticinin varlığı düzeltme eylemini aldığını gösterir. Eylemi gerçekleştiren yöneticinin adı, araştırma bağlantısı ve zamanı gibi ayrıntılar sağlar. Bu, yöneticilerin varlıklar üzerinde gerçekleştirilen düzeltme gibi her önemli eylemi fark etmelerini sağlar.
    1. **eylem araştırması Yönetici** - Varlıklardaki analiz yönetici tarafından zaten yapıldığından ve gerçekleştirilen eyleme bu neden olduğundan, sistem tarafından ek analiz yapılmaz. İlgili uyarı, düzeltme için seçilen varlık, gerçekleştirilen eylem, düzeltme durumu, varlık sayısı ve eylemi onaylayan gibi ayrıntıları gösterir. Bu, yöneticilerin *el ile* gerçekleştirilen araştırmayı ve eylemleri (yönetici eylemi araştırması) izlemesine olanak tanır.
1. **Birleşik işlem merkezindeki eylem günlükleri** - Geçici silme ve silinmiş öğeler klasörüne taşıma gibi e-posta eylemlerine yönelik geçmiş ve eylem günlüklerinin tümü, birleşik **İşlem Merkezi** > **Geçmişi sekmesinin** altındaki *merkezi bir görünümde kullanılabilir*. 
1. **Birleşik işlem merkezindeki filtreler** - Düzeltme adı, onay kimliği, Araştırma Kimliği, durum, eylem kaynağı ve eylem türü gibi birden çok filtre vardır. Bunlar, birleşik İşlem merkezinde e-posta eylemlerini bulmak ve izlemek için kullanışlıdır.

> [!IMPORTANT]
> Performans Daha iyi performans için düzeltme *50.000 veya daha az* toplu işlemle yapılmalıdır. *En son teslim konumunu* kullanarak arama sonucunu daraltın ve e-posta Gelen Kutusu, Gereksiz, Silinmiş gibi düzeltilebilir bir klasördeyse e-posta düzeltmesini tetikleyin.

## <a name="scenarios-that-call-for-email-remediation"></a>E-posta düzeltmeyi çağıran senaryolar

E-posta düzeltme senaryoları şunlardır:

1. Araştırmanın bir parçası olarak SecOps, son kullanıcının posta kutusunda bir tehdit tanımlar ve sorun e-postalarını temizlemek ister.
1. Otomatik Araştırma ve Yanıt (AIR) içindeki önerilen e-posta eylemleri SecOps tarafından onaylandığında, düzeltme eylemi verilen e-posta veya e-posta kümesi için otomatik olarak tetiklenir.

İki el ile e-posta düzeltme senaryosu:

1. Ana senaryo:
    1. E-postalarda el ile gerçekleştirilen eylemler (örneğin, Tehdit Gezgini veya Gelişmiş Tehdit Avcılığı kullanarak) yalnızca eski Office 365 için Defender İşlem Merkezi'nde görünür (E-posta ve İşbirliği > İşlem merkezinde > İşlem Merkezi'ni gözden geçirme - Microsoft 365 güvenlik).  
1. İki aşamalı onay senaryosu:
    1. İki aşamalı onay işlemini kullanarak onay bekleyen el ile eylemler (1. E-posta bir analist tarafından düzeltmeye eklendi, 2. E-posta başka bir analist tarafından incelendi ve onaylandı).

Yaygın senaryolar göz önünde bulundurulduğunda, e-posta düzeltmesi üç farklı yolla tetiklenebilir.

1. **Sorgu tabanlı düzeltme**: Sorgu içeren tüm arama sonuçlarını seçerek (en fazla 200.000 e-posta gönderilebilir).
1. **El ile yapılan düzeltme**: Onay kutusuna tıklayarak e-postaları tek tek seçme (bir kerede 100 e-posta gönderilebilir).
1. **Dışlamalarla sorgu tabanlı düzeltme**: Tüm e-postaları seçme ve ardından birkaç iletiyi el ile kaldırma (sorgu en fazla 1.000 e-posta içerebilir ve en fazla dışlama sayısı 100'dür).

## <a name="next-steps"></a>Sonraki Adımlar
1. [Microsoft 365 Defender portalına](https://security.microsoft.com) gidin ve oturum açın.
1. Gezinti bölmesinde **İşlem merkezi'ni** seçin.
1. **Geçmiş** sekmesine gidin, bekleyen herhangi bir onay listesine tıklayın. Bir yan bölme açılır.  
1. Birleşik işlem merkezinde eylem durumunu izleyin.

## <a name="more-information"></a>Daha fazla bilgi

[E-posta düzeltme hakkında daha fazla bilgi edinin](../../office-365-security/air-review-approve-pending-completed-actions.md)
