---
title: Kimlik için Microsoft Defender algılama dışlamalarını Microsoft 365 Defender
description: Dışlamaların nasıl yapılandır Kimlik için Microsoft Defender dışlamaları Microsoft 365 Defender.
ms.date: 11/02/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: e2df92e44b323bd0555407d72ebd48a7e050c9a5
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473925"
---
# <a name="configure-defender-for-identity-detection-exclusions-in-microsoft-365-defender"></a>Dışlamada Kimlik algılama dışlamaları için Defender'ı Microsoft 365 Defender

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender
- Kimlik için Microsoft Defender

Bu makalede, dışlamaların [Kimlik için Microsoft Defender](/defender-for-identity) dışlamaların nasıl [yapılandırıldığından Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

> [!IMPORTANT]
> Kimlik Doğrulama ve Doğrulama Microsoft 365 Defender bir parçası olarak, kimlik için Defender portalında yer alan konumlarından bazı seçenekler ve ayrıntılar değiştirilmiştir. Hem tanıdık hem de yeni özellikleri nerede bulamıyorum? bulmak için lütfen aşağıdaki ayrıntıları okuyun.

[!INCLUDE [Product long](includes/product-long.md)] belirli IP adreslerinin, bilgisayarların, etki alanlarının veya kullanıcıların bir dizi algılamadan dışlanmasına olanak sağlar.

Örneğin, DNS'yi tarama mekanizması olarak kullanan bir güvenlik tarayıcısı DNS **Reconnaissance** uyarısını tetikler. Dışlama oluşturmak, Kimlik için Defender'ın bu tarayıcıları yoksaymasını ve hatalı pozitif sonuç sayısını azaltmasını sağlar.

>[!NOTE]
>Bu uyarılarda açılan [DNS](/defender-for-identity/exfiltration-alerts#suspicious-communication-over-dns-external-id-2031) uyarıları üzerinden şüpheli iletişim ile en yaygın etki alanları arasında, müşterilerin en çok uyarı dışında tutulacak etki alanlarını gözlemlemiştir. Bu etki alanları varsayılan olarak dışlamalar listesine eklenir, ancak bunları kolayca kaldırma seçeneğiniz vardır.

## <a name="how-to-add-detection-exclusions"></a>Algılama dışlamaları ekleme

1. Daha [Microsoft 365 Defender](https://security.microsoft.com/), Kimlikler'Ayarlar'e **gidin**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Ad sütunundaki Kimlikler seçeneği" lightbox="../../media/defender-identity/settings-identities.png":::

1. Sol menüde **Dışlanan varlıklar'ı** göreceğiz.

   :::image type="content" source="../../media/defender-identity/excluded-entities.png" alt-text="Dışlanan varlıklar bölmesi" lightbox="../../media/defender-identity/excluded-entities.png":::

Daha sonra iki yönteme göre dışlamalar oluşturabilirsiniz: Algılama **kuralıyla ve** Dışlanan genel varlıklarla **dışlamalar**.

## <a name="exclusions-by-detection-rule"></a>Algılama kuralına göre dışlamalar

1. Sol menüde, Algılama kuralına göre **dışlamalar'ı seçin**. Algılama kurallarının listesini görüntülenir.

   :::image type="content" source="../../media/defender-identity/exclusions-by-detection-rule.png" alt-text="Sol bölmede Dışlanan varlıklar öğesinde Algılama kuralıyla dışlamalar seçeneği" lightbox="../../media/defender-identity/exclusions-by-detection-rule.png":::

1. Yapılandırmak istediğiniz her algılama için aşağıdaki adımları uygulayın:

    1. Kuralı seçin. Arama çubuğunu kullanarak algılamaları arayabilirsiniz. Seçildikten sonra, algılama kuralı ayrıntılarının yer alan bir bölme açılır.

       :::image type="content" source="../../media/defender-identity/detection-rule-details.png" alt-text="Algılama kuralının ayrıntıları" lightbox="../../media/defender-identity/detection-rule-details.png":::

    1. Dışlama eklemek için Dışlanan varlıklar **düğmesini** seçin ve sonra da dışlama türünü seçin. Her kural için, dışarıda bırakılan farklı varlıklar vardır. Bunlar kullanıcıları, cihazları, etki alanlarını ve IP adreslerini içerir. Bu örnekte, seçenekler Cihazları dışla **ve** IP adreslerini **dışla'dır**.

       :::image type="content" source="../../media/defender-identity/exclude-devices-or-ip-addresses.png" alt-text="Cihazları veya IP adreslerini dışlama seçeneği" lightbox="../../media/defender-identity/exclude-devices-or-ip-addresses.png":::

    1. Dışlama türünü seçtikten sonra dışlamayı  eklersiniz. Açılan bölmede dışlama eklemek **+** için düğmeyi seçin.

       :::image type="content" source="../../media/defender-identity/add-exclusion.png" alt-text="Dışlama ekleme seçeneği" lightbox="../../media/defender-identity/add-exclusion.png":::

    1. Ardından dışlamak istediğiniz varlığı ekleyin. Varlığı **listeye eklemek** için + Ekle'yi seçin.

       :::image type="content" source="../../media/defender-identity/add-excluded-entity.png" alt-text="Hariç tutulacak varlık ekleme seçeneği" lightbox="../../media/defender-identity/add-excluded-entity.png":::

    1. Sonra, **dışlamayı tamamlamak için IP** adreslerini dışla (bu örnekte) öğesini seçin.

       :::image type="content" source="../../media/defender-identity/exclude-ip-addresses.png" alt-text="IP adreslerini dışlama seçeneği" lightbox="../../media/defender-identity/exclude-ip-addresses.png":::

    1. Dışlamaları ekledikten sonra, Dışlanan varlıklar düğmesine dönerek listeyi dışarı aktarabilirsiniz veya **dışlamaları kaldırabilirsiniz** . Bu örnekte, Cihazları **Dışla'ya geri döndük**. Listeyi dışarı aktarma için aşağı ok düğmesini seçin.

       :::image type="content" source="../../media/defender-identity/return-to-exclude-devices.png" alt-text="Cihazları Dışla'ya dön seçeneği" lightbox="../../media/defender-identity/return-to-exclude-devices.png":::

    1. Dışlama silmek için dışlamayı seçin ve çöp kutusu simgesini seçin.

       :::image type="content" source="../../media/defender-identity/delete-exclusion.png" alt-text="Dışlama sil seçeneği" lightbox="../../media/defender-identity/delete-exclusion.png":::

## <a name="global-excluded-entities"></a>Genel dışlanan varlıklar

Artık Dışlanan Genel varlıklar tarafından **dışlamaları da yapılandırebilirsiniz**. Genel dışlamalar, Belirli varlıkları (IP adresleri, alt ağlar, cihazlar veya etki alanları) Identity için Defender'ın sahip olduğu tüm algılamalarda hariç tutmanız için olanak tanır. Dolayısıyla, örneğin bir cihazı dışlarsanız, yalnızca algılamanın bir parçası olarak cihaz kimliği bulunan algılamalara uygulanır.

1. Sol menüde Genel dışlanan **varlıklar'ı seçin**. Hariç tutabilirsiniz varlıkların kategorilerini burada görüntülersiniz.

   :::image type="content" source="../../media/defender-identity/global-excluded-entities.png" alt-text="Genel dışlanan varlıklar alt menüsü öğesi" lightbox="../../media/defender-identity/global-excluded-entities.png":::

1. Bir dışlama türü seçin. Bu örnekte, Etki alanlarını **dışla'ya seçilmiştir**.

   :::image type="content" source="../../media/defender-identity/exclude-domains.png" alt-text="Etki Alanları sekmesi" lightbox="../../media/defender-identity/exclude-domains.png":::

1. Dışarıda bırakılacak etki alanını ekleyebilirsiniz bir bölme açılır. Dışarıda tutmak istediğiniz etki alanını ekleyin.

   :::image type="content" source="../../media/defender-identity/add-excluded-domain.png" alt-text="Hariç tutulacak bir etki alanı ekleme seçeneği" lightbox="../../media/defender-identity/add-excluded-domain.png":::

1. Etki alanı listeye eklenir. **Dışlamayı tamamlamak için Etki** alanlarını dışla'ya seçin.

   :::image type="content" source="../../media/defender-identity/select-exclude-domains.png" alt-text="Hariç tutulacak etki alanlarını seçme seçeneği" lightbox="../../media/defender-identity/select-exclude-domains.png":::

1. Ardından, tüm algılama kurallarından çıkarılacak varlıklar listesinde etki alanını gösterir. Varlıkları seçerek ve Kaldır düğmesine tıklayarak dışarı aktarabilirsiniz.

   :::image type="content" source="../../media/defender-identity/global-excluded-entries-list.png" alt-text="Genel dışlanan girdiler listesi" lightbox="../../media/defender-identity/global-excluded-entries-list.png":::

## <a name="see-also"></a>Ayrıca bkz.

- [Kimlik güvenlik uyarıları için Defender'ı yönetme](manage-security-alerts.md)
