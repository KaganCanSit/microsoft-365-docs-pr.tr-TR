---
title: İş için Microsoft Defender'da tehditlere yanıt verme ve tehditleri azaltma
description: İş için Defender'da tehditler algılandığından, bu tehditlere yanıt vermek için eylemler gerçekleştirebilirsiniz. Cihaz envanteri görünümünü nasıl kullanacağınızı görün.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: how-to
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: b7a911991935407f9d512213c9d76c92106b74c8
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66089572"
---
# <a name="respond-to-and-mitigate-threats-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'da tehditlere yanıt verme ve tehditleri azaltma

Microsoft 365 Defender portalı, güvenlik ekibinizin algılanan tehditlere yanıt vermesini ve tehditleri azaltmasını sağlar. Bu makalede, İş için Defender'ı nasıl kullanabileceğinize ilişkin bir örnek açıklanabilir.


## <a name="view-detected-threats"></a>Algılanan tehditleri görüntüleme

1. Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com)) gidin ve oturum açın.

2. Giriş sayfasındaki kartlara dikkat edin. Kartlarda kaç tehdit algılandığı ve kaç kullanıcı hesabının, uç noktanın (cihazın) ve diğer varlıkların etkilendiği bir bakışta gösterilir. Aşağıdaki görüntüde görebileceğiniz bir kart örneği verilmiştir:

   :::image type="content" source="../../media/defender-business/mdb-examplecards.png" alt-text="Microsoft 365 Defender portalındaki kartların ekran görüntüsü":::

3. Daha fazla bilgi görüntülemek ve işlem yapmak için kartta bir düğme veya bağlantı seçin. Örnek olarak, **Risk altındaki cihazlar** kartımızda **Ayrıntıları görüntüle** düğmesi bulunur. Bu düğmeyi seçmek, aşağıdaki görüntüde gösterildiği gibi bizi **Cihaz envanteri** sayfasına götürür:

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory.png" alt-text="Cihaz envanterinin ekran görüntüsü":::

   **Cihaz envanteri** sayfası, şirket cihazlarının yanı sıra risk düzeylerini ve maruz kalma düzeylerini listeler.

4. Cihaz gibi bir öğe seçin. Bir açılır pencere bölmesi açılır ve aşağıdaki görüntüde gösterildiği gibi bu öğe için oluşturulan uyarılar ve olaylar hakkında daha fazla bilgi görüntüler:  

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout.png" alt-text="Seçili cihaz için açılır pencere bölmesinin ekran görüntüsü":::

5. Açılır öğede görüntülenen bilgileri görüntüleyin. Aşağıdaki görüntüde gösterildiği gibi kullanılabilir eylemlerin listelendiğini belirten bir menü açmak için üç noktayı (...) seçin: 

   :::image type="content" source="../../media/defender-business/mdb-deviceinventory-selecteddeviceflyout-menu.png" alt-text="Seçili cihaz için kullanılabilir eylemlerin ekran görüntüsü":::

6. Kullanılabilir bir eylem seçin. Örneğin **Virüsten koruma taraması çalıştır'ı** seçebilirsiniz ve bu da Microsoft Defender Virüsten Koruma cihazda hızlı bir tarama başlatmasına neden olur. Alternatif olarak, cihazda otomatik bir araştırma tetikleme için **Otomatik Araştırma Başlat'ı** da seçebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

- [İşlem merkezindeki düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)
- [İş için Microsoft Defender'de cihazları yönetme](mdb-manage-devices.md)
- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md)
