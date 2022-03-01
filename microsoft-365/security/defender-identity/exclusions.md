---
title: Microsoft 365 Defender'ta Kimlik algılama dışlamaları için Microsoft Defender
description: Bir başka dosyada Kimlik algılama dışlamaları için Microsoft Defender'ı Microsoft 365 Defender.
ms.date: 11/02/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
manager: raynew
ms.openlocfilehash: feaa1743e00c515e02301090ce811afee5c26e74
ms.sourcegitcommit: dd6514ae173f1c821d4ec25298145df6cb232e2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2022
ms.locfileid: "63014031"
---
# <a name="configure-defender-for-identity-detection-exclusions-in-microsoft-365-defender"></a>Dışlamada Kimlik algılama dışlamaları için Defender'ı Microsoft 365 Defender

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender
- Kimlik için Defender

Bu makalede, Microsoft Defender'da Kimlik algılama [dışlamaları](/defender-for-identity) için nasıl yapılandır [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

> [!IMPORTANT]
> Kimlik Doğrulama ve Doğrulama Microsoft 365 Defender bir parçası olarak, kimlik için Defender portalında yer alan konumlarından bazı seçenekler ve ayrıntılar değiştirilmiştir. Hem tanıdık hem de yeni özellikleri nerede bulamıyorum? bulmak için lütfen aşağıdaki ayrıntıları okuyun.

[!INCLUDE [Product long](includes/product-long.md)] belirli IP adreslerinin, bilgisayarların, etki alanlarının veya kullanıcıların bir dizi algılamadan dışlanmasına olanak sağlar.

Örneğin, DNS'yi tarama mekanizması olarak kullanan bir güvenlik tarayıcısı DNS **Reconnaissance** uyarısını tetikler. Dışlama oluşturmak, Kimlik için Defender'ın bu tarayıcıları yoksaymasını ve hatalı pozitif sonuç sayısını azaltmasını sağlar.

>[!NOTE]
>Bu uyarılarda açılan [DNS](/defender-for-identity/exfiltration-alerts#suspicious-communication-over-dns-external-id-2031) uyarıları üzerinden şüpheli iletişim ile en yaygın etki alanları arasında, müşterilerin en çok uyarı dışında tutulacak etki alanlarını gözlemlemiştir. Bu etki alanları varsayılan olarak dışlamalar listesine eklenir, ancak bunları kolayca kaldırma seçeneğiniz vardır.

## <a name="how-to-add-detection-exclusions"></a>Algılama dışlamaları ekleme

1. Daha [Microsoft 365 Defender](https://security.microsoft.com/), Kimlikler'Ayarlar'e **gidin**.

    ![Kimlikler'Ayarlar ardından Kimlikler'e gidin.](../../media/defender-identity/settings-identities.png)

1. Sol menüde **Dışlanan varlıklar'ı** göreceğiz.

    ![Dışlanan varlıklar.](../../media/defender-identity/excluded-entities.png)

Daha sonra iki yönteme göre dışlamalar oluşturabilirsiniz: Algılama **kuralıyla ve** Dışlanan genel varlıklarla **dışlamalar**.

## <a name="exclusions-by-detection-rule"></a>Algılama kuralına göre dışlamalar

1. Sol menüde, Algılama kuralına göre **dışlamalar'ı seçin**. Algılama kurallarının listesini görüntülenir.

    ![Algılama kuralına göre dışlamalar.](../../media/defender-identity/exclusions-by-detection-rule.png)

1. Yapılandırmak istediğiniz her algılama için aşağıdaki adımları uygulayın:

    1. Kuralı seçin. Arama çubuğunu kullanarak algılamaları arayabilirsiniz. Seçildikten sonra, algılama kuralı ayrıntılarının yer alan bir bölme açılır.

        ![Algılama kuralı ayrıntıları.](../../media/defender-identity/detection-rule-details.png)

    1. Dışlama eklemek için Dışlanan varlıklar **düğmesini** seçin ve sonra da dışlama türünü seçin. Her kural için, dışarıda bırakılan farklı varlıklar vardır. Bunlar kullanıcıları, cihazları, etki alanlarını ve IP adreslerini içerir. Bu örnekte, seçenekler Cihazları dışla **ve** IP adreslerini **dışla'dır**.

        ![Cihazları veya IP adreslerini dışla.](../../media/defender-identity/exclude-devices-or-ip-addresses.png)

    1. Dışlama türünü seçtikten sonra dışlamayı  eklersiniz. Açılan bölmede dışlama eklemek **+** için düğmeyi seçin.

        ![Dışlama ekle.](../../media/defender-identity/add-exclusion.png)

    1. Ardından dışlamak istediğiniz varlığı ekleyin. Varlığı **listeye eklemek** için + Ekle'yi seçin.

        ![Hariç tutulacak bir varlık ekleyin.](../../media/defender-identity/add-excluded-entity.png)

    1. Sonra, **dışlamayı tamamlamak için IP** adreslerini dışla (bu örnekte) öğesini seçin.

        ![IP adreslerini dışla.](../../media/defender-identity/exclude-ip-addresses.png)

    1. Dışlamaları ekledikten sonra, Dışlanan varlıklar düğmesine dönerek listeyi dışarı aktarabilirsiniz veya **dışlamaları kaldırabilirsiniz** . Bu örnekte, Cihazları **Dışla'ya geri döndük**. Listeyi dışarı aktarma için aşağı ok düğmesini seçin.

        ![Cihazları dışla'ya geri dön.](../../media/defender-identity/return-to-exclude-devices.png)

    1. Dışlama silmek için dışlamayı seçin ve çöp kutusu simgesini seçin.

        ![Dışlama silme.](../../media/defender-identity/delete-exclusion.png)

## <a name="global-excluded-entities"></a>Genel dışlanan varlıklar

Artık Dışlanan Genel varlıklar tarafından **dışlamaları da yapılandırebilirsiniz**. Genel dışlamalar, Belirli varlıkları (IP adresleri, alt ağlar, cihazlar veya etki alanları) Identity için Defender'ın sahip olduğu tüm algılamalarda hariç tutmanız için olanak tanır. Dolayısıyla, örneğin bir cihazı dışlarsanız, yalnızca algılamanın bir parçası olarak cihaz kimliği bulunan algılamalara uygulanır.

1. Sol menüde Genel dışlanan **varlıklar'ı seçin**. Hariç tutabilirsiniz varlıkların kategorilerini burada görüntülersiniz.

    ![Genel dışlanan varlıklar.](../../media/defender-identity/global-excluded-entities.png)

1. Bir dışlama türü seçin. Bu örnekte, Etki alanlarını **dışla'ya seçilmiştir**.

    ![Etki alanlarını dışla.](../../media/defender-identity/exclude-domains.png)

1. Dışarıda bırakılacak etki alanını ekleyebilirsiniz bir bölme açılır. Dışarıda tutmak istediğiniz etki alanını ekleyin.

    ![Hariç tutulacak bir etki alanı ekleyin.](../../media/defender-identity/add-excluded-domain.png)

1. Etki alanı listeye eklenir. **Dışlamayı tamamlamak için Etki** alanlarını dışla'ya seçin.

    ![Etki alanlarını dışla'ya seçin.](../../media/defender-identity/select-exclude-domains.png)

1. Ardından, tüm algılama kurallarından çıkarılacak varlıklar listesinde etki alanını gösterir. Varlıkları seçerek ve Kaldır düğmesine tıklayarak dışarı aktarabilirsiniz.

    ![Genel dışlanan girdilerin listesi.](../../media/defender-identity/global-excluded-entries-list.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Kimlik güvenlik uyarıları için Defender'ı yönetme](manage-security-alerts.md)
