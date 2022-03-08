---
title: Otomatik bir incelemenin ayrıntılarını ve sonuçlarını görüntüleme
description: Otomatik bir araştırma sırasında ve sonrasında, sonuçları ve önemli bulguları görüntü
keywords: otomatik, araştırma, sonuçlar, çözümleme, ayrıntılar, düzeltme, autoair
search.appverid: met150
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
ms.openlocfilehash: 294722f3f79172e06752c5318bfef21dfc640eed
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327637"
---
# <a name="view-the-details-and-results-of-an-automated-investigation"></a>Otomatik bir incelemenin ayrıntılarını ve sonuçlarını görüntüleme

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Uç Nokta için Microsoft Defender ile, [otomatik](automated-investigations.md) bir araştırma çalıştırıldığı zaman, bu soruşturmayla ilgili ayrıntılar hem otomatik araştırma işlemi sırasında hem de sonrasında kullanılabilir. Gerekli izinlere sahipsiniz, bu ayrıntıları araştırma ayrıntıları görünümünde görüntüebilirsiniz. Araştırma ayrıntıları görünümü size güncel durumu ve bekleyen eylemleri onaylama olanağı sağlar.

## <a name="new-unified-investigation-page"></a>(Yenİ!) Birleşik araştırma sayfası

Araştırma sayfası yakın zamanda cihazlarınız, e-postanız ve işbirliği içeriğiniz arasında bilgi içerecek şekilde güncelleştirildi. Yeni, birleşik araştırma sayfası yaygın bir dil tanımlar ve Uç Nokta için [Microsoft Defender](microsoft-defender-endpoint.md) ve İş için [Microsoft Defender genelinde otomatik soruşturmalar için birleşik bir Office 365](/microsoft-365/security/office-365-security/office-365-atp).

> [!TIP]
> Değişenler hakkında daha fazla bilgi edinmek için bkz. [(Yenİ!) Birleşik araştırma sayfası](/microsoft-365/security/mtp/mtp-autoir-results).

## <a name="open-the-investigation-details-view"></a>Araştırma ayrıntıları görünümünü açma

Aşağıdaki yöntemlerden birini kullanarak araştırma ayrıntıları görünümünü açabilirsiniz:

- [İşlem merkezinde bir öğe seçme](#select-an-item-in-the-action-center)
- [Olay ayrıntıları sayfasından araştırma seçme](#open-an-investigation-from-an-incident-details-page)

### <a name="select-an-item-in-the-action-center"></a>İşlem merkezinde bir öğe seçme

Geliştirilmiş İşlem [Merkezi cihazlarınız](auto-investigation-action-center.md) [arasında düzeltme eylemleri](manage-auto-investigation.md#remediation-actions) , e-posta ve işbirliği & kimlikleri bir araya getirir. Listelenen eylemler, otomatik veya el ile yapılan düzeltme eylemlerini içerir. İşlem merkezinde, onay bekleyen eylemleri ve zaten onaylanmış veya tamamlanmış eylemleri görüntüabilirsiniz. Ayrıca, araştırma sayfası gibi daha fazla ayrıntıya da gezinebilirsiniz.

1. Oturum açma <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> gidin.
2. Gezinti bölmesinde İşlem **merkezi'ni seçin**.
3. Beklemede **veya Geçmiş** **sekmesinde** bir öğe seçin. Açılır bölmesi açılır.
4. Uçarak çıkış bölmesinde bilgileri gözden geçirin ve sonra aşağıdaki adımlardan birini uygulayın:
   - Araştırma **hakkında daha fazla ayrıntı** görüntülemek için Araştırma sayfasını aç'ı seçin.
   - Bekleyen **bir eylemi** başlatmak için Onayla'ya seçin.
   - Bekleyen **bir eylemin** askıya alınmasını önlemek için Reddet'i seçin.
   - Gelişmiş **ava gitmek** için Avına [git'i seçin](advanced-hunting-overview.md).

### <a name="open-an-investigation-from-an-incident-details-page"></a>Olay ayrıntıları sayfasından araştırma açma

Etkilenen cihazlar, kullanıcı hesapları veya posta kutularıyla ilgili tetiklenen uyarılar da dahil olmak üzere, olayla ilgili ayrıntılı bilgileri görüntülemek için olay ayrıntıları sayfasını kullanın.

1. Oturum açma <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> gidin.
2. Gezinti bölmesinde Olay Olayları **ve & seçin** \> **.**
3. Listeden bir öğe seçin ve sonra Olay sayfasını **aç'ı seçin**.
4. Araştırma **sekmesini seçin** ve sonra da listeden bir araştırma seçin. Açılır bölmesi açılır.
5. Araştırma **sayfasını aç'ı seçin**.

## <a name="investigation-details"></a>İnceleme ayrıntıları

Bir soruşturmayla ilgili geçmiş, geçerli ve bekleyen etkinlikleri görmek için araştırma ayrıntıları görünümünü kullanın. Araştırma ayrıntıları görünümü aşağıdaki görüntüye benzer:

Araştırma ayrıntıları görünümünde, aşağıdaki tabloda açıklanan Araştırma **grafiği, Uyarılar****,** **Cihazlar**, **Kimlikler**, **Anahtar** **bulguları, Varlıklar**, **Günlük** ve Bekleyen eylemler sekmelerinde bilgileri görebilirsiniz.

> [!NOTE]
> Araştırma ayrıntıları sayfasında gördüğünüz belirli sekmeler, aboneliğinizin içeriğine bağlıdır. Örneğin, aboneliğiniz Plan 2 için Microsoft Defender Office 365 yoksa, Posta Kutuları sekmesini **görmeyebilirsiniz**.

|Sekme|Açıklama|
|---|---|
|**İnceleme grafiği**|Araştırmanın görsel bir gösterimini sağlar. Bulunan varlıkları ve listeleri tehditlerle birlikte, uyarılar ve onay bekleyen eylemlerin olup olmadığını gösterir. <p> Daha fazla ayrıntı görüntülemek için grafikte bir öğe seçin. Örneğin, Kanıt **simgesini seçmek sizi** Kanıt sekmesine alır ve burada  algılanan varlıkları ve bunların kararlarını görebilirsiniz.|
|**Uyarılar**|Araştırmayla ilişkili uyarıları listeler. Uyarılar; kullanıcının cihazı, Office uygulamaları, Bulut Uygulamaları için Defender ve diğer güvenlik özelliklerinde tehdit koruması Microsoft 365 Defender gelebilir.|
|**Cihazlar**|İncelemeye dahil edilen cihazları düzeltme düzeyiyle birlikte listeler. (Düzeltme düzeyleri, cihaz gruplarının [otomasyon düzeyine karşılık geldi](automation-levels.md).)|
|**Posta Kutuları**|Algılanan tehditlerden etki alan posta kutularını listeler.|
|**Kullanıcılar**|Algılanan tehditlerden etkilenmesi olan kullanıcı hesaplarını listeler.|
|**Kanıt**|Uyarılar/soruşturmalar tarafından yükseltilmiş kanıt parçalarını listeler. Kararları (*Kötü Amaçlı*, *Şüpheli* veya *Tehdit bulunamadı*) ve düzeltme durumunu içerir.|
|**Varlıklar**|Her varlık türü (Kötü Amaçlı, Şüpheli veya Tehdit bulunamadı) *dahil olmak üzere**,* çözüme sahip olan her varlık *hakkında ayrıntılar sağlar*.|
|**Log**|Uyarıyı tetikledikten sonra  alınan tüm soruşturma eylemlerinin kronolojik ve ayrıntılı görünümünü sağlar.|
|**Bekleyen eylemler**|Devam etmek için onay gerektiren öğeleri listeler. Bekleyen eylemleri onaylamak için İşlem merkezi'ne (<https://security.microsoft.com/action-center>) gidin.|

## <a name="see-also"></a>Ayrıca bkz.

- [Otomatik bir soruşturmayı takip eden düzeltme eylemlerini gözden geçirme](manage-auto-investigation.md)
- [Uç Nokta Olayları için Microsoft Defender'ı görüntüleme ve düzenleme](view-incidents-queue.md)
