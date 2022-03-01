---
title: İş için Microsoft Defender'da düzeltme eylemlerini gözden Office 365
keywords: AIR, autoIR, Uç Nokta için Microsoft Defender, otomatik, araştırma, yanıt, düzeltme, tehdit, gelişmiş, tehdit, koruma
f1.keywords:
- NOCSH
author: JoeDavies-MSFT
ms.author: josephd
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Plan 2'ye ilişkin Microsoft Defender'da otomatik soruşturma ve yanıt özelliklerinde düzeltme Office 365 öğrenin.
ms.technology: mdo
ms.prod: m365-security
ms.date: 06/10/2021
ms.openlocfilehash: bc8c99a547e4f30e10575e8353afd6ca02bf233b
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021701"
---
# <a name="review-and-manage-remediation-actions-in-office-365"></a>E-postada düzeltme eylemlerini gözden Office 365

**Geçerli olduğu yer:**
- [Office 365 için Microsoft Defender plan 2](defender-for-office-365.md)

E-posta üzerinde otomatik & işbirliği içeriği kötü amaçlı veya Şüpheli gibi kararlara neden *olur; bazı* düzeltme  eylemleri oluşturulur. Düzeltme eylemleri, Office 365 için Microsoft Defender'da şunlar olabilir:

- E-posta iletilerini veya kümelerini geçici olarak silme
- Dış posta iletmeyi kapatma

Bu düzeltme eylemleri, güvenlik işlemleri ekipleriniz onaylamadıkça ve onaylamadıkça gerçekleştirlanmaz. Otomatik soruşturmaların zamanında tamamlanması için beklemedeki eylemleri en kısa zamanda incelemenizi ve onaylamanızı öneririz. Bazı durumlarda, gönderilen eylemleri yeniden gözden geçirabilirsiniz.  Herhangi bir işlemden önce Arama & rolün bir parçası olmak gerekir.

## <a name="approve-or-reject-pending-actions"></a>Bekleyen eylemleri onaylama (veya reddetme)

Otomatik soruşturma eylemlerini bulmanın ve almanın dört farklı yolu vardır:

- [Olay sırası](https://security.microsoft.com/incidents)
- araştırmanın kendisi (Olay yoluyla veya bir uyarıdan erişilir)
- [İşlem merkezi](https://security.microsoft.com/action-center/pending)
- [Araştırma ve düzeltme soruşturmaları sırası](https://security.microsoft.com/airinvestigation)

## <a name="incident-queue"></a>Olay sırası

1. 'daki Microsoft 365 Defender portalında<https://security.microsoft.com>, Olaylar ve Olayları'nda  **Olaylar &** \> **gidin**. Doğrudan Olaylar sayfasına **gitmek için** kullanın <https://security.microsoft.com/incidents>.
2. Olaylar **sayfasında,** özet sayfasını açmak için bir olay adı seçin.
3. Kanıt ve **Yanıt sekmesini** seçin.
4. Listeden bir öğe seçin. Yan bölmesi açılır.
5. Yan bölmede, onaylama veya reddetme eylemlerini gerçekleştirin.

## <a name="action-center"></a>İşlem merkezi

1. Microsoft 365 Defender portalında, <https://security.microsoft.com>İşlem **merkezi'yi** seçerek İşlem merkezi **sayfasına gidin**. Doğrudan İşlem merkezi **sayfasına gitmek için** , 'i kullanın <https://security.microsoft.com/action-center/pending>.
2. İşlem **merkezi sayfasında** , Beklemede **sekmesinin seçili** olduğunu doğrulayın ve onay bekleyen eylemler listesini gözden geçirin.
   - Araştırma **hakkında daha fazla ayrıntı** görüntülemek için Araştırma sayfasını aç'ı seçin.
   - Bekleyen **bir eylemi** başlatmak için Onayla'ya seçin.
   - Bekleyen **bir eylemin** askıya alınmasını önlemek için Reddet'i seçin.

## <a name="investigation-and-remediation-investigations-queue"></a>Araştırma ve düzeltme soruşturmaları sırası

1. Microsoft 365 Defender portalında, E-posta <https://security.microsoft.com>ve işbirliği **Soruşturmaları'nda** **Tehdit &** \> **sayfasına gidin**. Doğrudan Tehdit soruşturması **sayfasına gitmek** için kullanın <https://security.microsoft.com/airinvestigation>.
2. Tehdit **soruşturma sayfasında** , durumu Beklemede eylem olan bir öğeyi listeden **bulun ve bulun**.
3. Yeni ![pencerede aç simgesine tıklayın.](../../media/m365-cc-sc-open-icon.png) **Liste süresinde yeni** pencerede aç (Kimlik ile **Durum arasında****).**
4. Açılan sayfada, onaylama veya reddetme eylemlerini gerçekleştirin.

## <a name="change-or-undo-one-remediation-action"></a>Bir düzeltme eylemsini değiştirme veya geri alma

Yeniden gönderilen eylemleri yeniden gözden geçirmenin iki farklı yolu vardır:

- Birleşik işlem [merkezi aracılığıyla](https://security.microsoft.com/action-center).
- Her ne [Office merkezidir](https://security.microsoft.com/threatincidents).

## <a name="change-or-undo-through-the-unified-action-center"></a>Birleştirilmiş işlem merkezini değiştirme veya geri alma

1. aşağıdaki Microsoft 365 Defender portalında<https://security.microsoft.com>, İşlem merkezi'yi seçerek birleşik işlem **merkezine gidin**. Doğrudan birleşik işlem merkezine gitmek için, kullanın <https://security.microsoft.com/action-center/>.
2. İşlem **merkezi sayfasında** Geçmiş sekmesini **seçin ve** sonra da değiştirmek ya da geri almak istediğiniz eylemi seçin.
3. Ekranın sağ tarafındaki bölmede uygun **eylemi seçin (** Gelen Kutusu'na **taşı,** gereksiz'e **taşı, silinmiş** öğelere **taşı, yumuşak** sil veya kalıcı **olarak sil**).

## <a name="change-or-undo-through-the-office-action-center"></a>İşlem merkezini değiştirme veya Office geri alma

1. Microsoft 365 Defender portalında, E-posta <https://security.microsoft.com>ve işbirliği **Office'daki & Merkezi'ne** \>  \> **gidin**. İşlem merkezine doğrudan gitmek Office için , kullanın<https://security.microsoft.com/threatincidents>.
2. İşlem **merkezi sayfasında** , uygun düzeltmeyi seçin.
3. Yan panelde, posta gönderimleri girdisini tıklatın ve listenin yüklenmesini bekleyin.
4. Etkinleştirmek için üst sıralarda yer alan Eylem düğmesini bekleyin ve eylem türünü değiştirmek için Eylem düğmesini seçin.
5. Bu, uygun eylemleri oluşturacak.

## <a name="next-steps"></a>Sonraki adımlar

- [Threat Explorer'ı kullanma](threat-explorer.md)
- [Yönetici /El ile Yapılan Eylemler](remediate-malicious-email-delivered-office-365.md)
- [Otomatik araştırma ve yanıt yeteneklerinde hatalı pozitif/negatifleri bildirme](air-report-false-positives-negatives.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Bir ekipte otomatik bir soruşturmanın ayrıntılarını ve sonuçlarını Office 365](air-view-investigation-results.md)
