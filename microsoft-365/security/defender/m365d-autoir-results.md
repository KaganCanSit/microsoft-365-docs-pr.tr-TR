---
title: Otomatik bir incelemenin ayrıntıları ve sonuçları
description: Bu çalışmalarda sonuçları ve önemli arama sonuçlarını Microsoft 365 Defender
keywords: otomatik, araştırma, sonuçlar, çözümleme, ayrıntılar, düzeltme, autoair
search.appverid: met150
ms.prod: m365-security
ms.technology: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
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
ms.openlocfilehash: e38de9e864fa063e3e56dc99c1d9c671b6409023
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63033340"
---
# <a name="details-and-results-of-an-automated-investigation"></a>Otomatik bir incelemenin ayrıntıları ve sonuçları

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

Otomatik Microsoft 365 Defender ile[, otomatik bir](m365d-autoir.md) araştırma çalıştırıldığı zaman, bu soruşturmayla ilgili ayrıntılar hem otomatik araştırma işlemi sırasında hem de sonrasında kullanılabilir. Gerekli izinlere [sahipsiniz](m365d-action-center.md#required-permissions-for-action-center-tasks), size güncel durum ve bekleyen eylemleri onaylama olanağı sağlayan bir soruşturma ayrıntıları görünümünde bu ayrıntıları görüntüebilirsiniz. 

## <a name="new-unified-investigation-page"></a>(NEW) Birleşik araştırma sayfası

Araştırma sayfası yakın zamanda cihazlarınız, e-postanız ve işbirliği içeriğiniz arasında bilgi içerecek şekilde güncelleştirildi. Yeni, birleşik araştırma sayfası yaygın bir dil tanımlar ve Uç Nokta için [Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) ve İş için [Microsoft Defender genelinde otomatik soruşturmalar için birleşik bir Office 365](../office-365-security/defender-for-office-365.md). Birleştirilmiş araştırma sayfasına erişmek için, göreceğin sarı başlıkta bağlantıyı seçin:

- Güvenlik ve Uyumluluk <a href="https://go.microsoft.com/fwlink/p/?linkid=2077143" target="_blank">Merkezi'Office 365 herhangi & sayfası</a>
- Portalda herhangi bir Microsoft 365 Defender sayfası ([https://security.microsoft.com](https://security.microsoft.com))
- Portalda herhangi bir olay veya <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender deneyimi</a>

## <a name="open-the-investigation-details-view"></a>Araştırma ayrıntıları görünümünü açma

Aşağıdaki yöntemlerden birini kullanarak araştırma ayrıntıları görünümünü açabilirsiniz:

- [İşlem merkezinde bir öğe seçme](#select-an-item-in-the-action-center)
- [Olay ayrıntıları sayfasından araştırma seçme](#open-an-investigation-from-an-incident-details-page)

### <a name="select-an-item-in-the-action-center"></a>İşlem merkezinde bir öğe seçme

Geliştirilmiş [İşlem Merkezi](m365d-action-center.md) ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)), cihazlarınız arasında düzeltme eylemleri[](m365d-remediation-actions.md), e-posta ve işbirliği & kimlikleri bir araya getirir. Listelenen eylemler, otomatik veya el ile yapılan düzeltme eylemlerini içerir. İşlem merkezinde, onay bekleyen eylemleri ve zaten onaylanmış veya tamamlanmış eylemleri görüntüabilirsiniz. Ayrıca, araştırma sayfası gibi daha fazla ayrıntıya da gezinebilirsiniz.

> [!TIP]
> Eylemleri onaylamak, [reddetmek veya](m365d-action-center.md#required-permissions-for-action-center-tasks) geri almak için belirli izinlere sahip olmak gerekir.

1. Portala <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender ve</a> oturum açın. 

2. Gezinti bölmesinde İşlem **merkezi'ni seçin**. 

3. Beklemede **veya Geçmiş** **sekmesinde** bir öğe seçin. Açılır bölmesi açılır.

4. Uçarak çıkış bölmesinde bilgileri gözden geçirin ve sonra aşağıdaki adımlardan birini uygulayın:
   - Araştırma **hakkında daha fazla ayrıntı** görüntülemek için Araştırma sayfasını aç'ı seçin.
   - Bekleyen **bir eylemi** başlatmak için Onayla'ya seçin.
   - Bekleyen **bir eylemin** askıya alınmasını önlemek için Reddet'i seçin.
   - Gelişmiş **ava gitmek** için Avına [git'i seçin](advanced-hunting-overview.md).

### <a name="open-an-investigation-from-an-incident-details-page"></a>Olay ayrıntıları sayfasından araştırma açma

Etkilenen cihazlar, kullanıcı hesapları veya posta kutularıyla ilgili tetiklenen uyarılar da dahil olmak üzere, olayla ilgili ayrıntılı bilgileri görüntülemek için olay ayrıntıları sayfasını kullanın.

1. Portala <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender ve</a> oturum açın. 

2. Gezinti bölmesinde Olaylar ve **uyarılarIncidents****& seçin** > . 

3. Listeden bir öğe seçin ve sonra Olay sayfasını **aç'ı seçin**.

4. Araştırma **sekmesini seçin** ve sonra da listeden bir araştırma seçin. Açılır bölmesi açılır.

5. Araştırma **sayfasını aç'ı seçin**. 

İşte bir örnek.

:::image type="content" source="../../media/mtp-incidentdetails-tabs.png" alt-text="Araştırma sayfası örneği." lightbox="../../media/mtp-incidentdetails-tabs.png":::

## <a name="investigation-details"></a>İnceleme ayrıntıları

Bir soruşturmayla ilgili geçmiş, geçerli ve bekleyen etkinlikleri görmek için araştırma ayrıntıları görünümünü kullanın. İşte bir örnek.

:::image type="content" source="../../media/mtp-air-investdetails.png" alt-text="Soruşturma ayrıntıları örneği." lightbox="../../media/mtp-air-investdetails.png":::

Araştırma ayrıntıları görünümünde, aşağıdaki tabloda açıklanan Araştırma **grafiği, Uyarılar****,** **Cihazlar**, **Kimlikler**, **Anahtar** **bulguları, Varlıklar**, **Günlük** ve Bekleyen eylemler sekmelerinde bilgileri görebilirsiniz.

> [!NOTE]
> Araştırma ayrıntıları sayfasında gördüğünüz belirli sekmeler, aboneliğinizin içeriğine bağlıdır. Örneğin, aboneliğiniz Plan 2 için Microsoft Defender Office 365 yoksa, Posta Kutuları sekmesini **görmeyebilirsiniz**.

| Sekme | Açıklama |
|:--------|:--------|
| **İnceleme grafiği** | Araştırmanın görsel bir gösterimini sağlar. Bulunan varlıkları ve listeleri tehditlerle birlikte, uyarılar ve onay bekleyen eylemlerin olup olmadığını gösterir.<br/>Daha fazla ayrıntı görüntülemek için grafikte bir öğe seçin. Örneğin, Kanıt **simgesini seçmek sizi** Kanıt sekmesine alır ve burada  algılanan varlıkları ve bunların kararlarını görebilirsiniz. |
| **Uyarılar** | Araştırmayla ilişkili uyarıları listeler. Uyarılar; kullanıcının cihazı, Office uygulamaları, Bulut Uygulamaları için Microsoft Defender ve diğer güvenlik özelliklerinde tehdit koruması Microsoft 365 Defender gelebilir.|
| **Cihazlar** | İncelemeye dahil edilen cihazları düzeltme düzeyiyle birlikte listeler. (Düzeltme düzeyleri, cihaz [gruplarının otomasyon düzeyine karşılık geldi](m365d-configure-auto-investigation-response.md#review-or-change-the-automation-level-for-device-groups).) |
| **Posta Kutuları** |Algılanan tehditlerden etki alan posta kutularını listeler.  |
| **Kullanıcılar**  | Algılanan tehditlerden etkilenmesi olan kullanıcı hesaplarını listeler. |
| **Kanıt** | Uyarılar veya soruşturmalar tarafından yükseltilmiş kanıt parçalarını listeler. Kararları (*Kötü Amaçlı*, *Şüpheli*, *Bilinmeyen* veya Tehdit *bulunamadı*) ve düzeltme durumunu içerir. |
| **Varlıklar** | Her varlık türü (Kötü Amaçlı, Şüpheli veya Tehdit bulunamadı) *dahil olmak üzere**,* çözüme sahip olan her varlık *hakkında ayrıntılar sağlar*.|
|**Log** | Uyarıyı tetikledikten sonra  alınan tüm soruşturma eylemlerinin kronolojik ve ayrıntılı görünümünü sağlar.|
| **Bekleyen eylemler geçmişi** | Devam etmek için onay gerektiren öğeleri listeler. Bekleyen eylemleri onaylamak için İşlem merkezi'ne ([https://security.microsoft.com/action-center](https://security.microsoft.com/action-center)) gidin. |

## <a name="next-steps"></a>Sonraki adımlar

- [Düzeltme eylemlerini görüntüleme ve yönetme](m365d-autoir-actions.md)
- [Düzeltme eylemleri hakkında daha fazla bilgi](m365d-remediation-actions.md)
