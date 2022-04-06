---
title: Kimlik için Microsoft Defender algılayıcı sağlığı ve ayarlarını Microsoft 365 Defender
description: Algılayıcıları yapılandırmayı ve Kimlik için Microsoft Defender durumlarını takip etmeyi Microsoft 365 Defender
ms.date: 06/07/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: 246fd5ca880ca2d7e187283d06f19d071f5d7e0e
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468533"
---
# <a name="microsoft-defender-for-identity-sensor-health-and-settings-in-microsoft-365-defender"></a>Kimlik için Microsoft Defender algılayıcı sağlığı ve ayarlarını Microsoft 365 Defender

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender
- Kimlik için Microsoft Defender

Bu makalede, algılayıcıların algılayıcılarını [Kimlik için Microsoft Defender ve](/defender-for-identity) [takip Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>Kimlik Doğrulama ve Doğrulama Microsoft 365 Defender bir parçası olarak, kimlik için Defender portalında yer alan konumlarından bazı seçenekler ve ayrıntılar değiştirilmiştir. Hem tanıdık hem de yeni özellikleri nerede bulamıyorum? bulmak için lütfen aşağıdaki ayrıntıları okuyun.

## <a name="view-defender-for-identity-sensor-settings-and-status"></a>Kimlik algılayıcısı ayarları ve durumu için Defender'ı görüntüleme

1. Daha <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, Kimlikler'Ayarlar'e **gidin**.

   :::image type="content" source="../../media/defender-identity/settings-identities.png" alt-text="Kimlikler sayfasındaki Kimlikler Ayarlar." lightbox="../../media/defender-identity/settings-identities.png":::

1. Kimlik **algılayıcıları** için Defender'nizin tüm görüntü olarak Algılayıcılar sayfasını seçin. Her algılayıcı için, algılayıcının adını, etki alanı üyeliğini, sürüm numarasını, güncelleştirmelerin gecikirse, hizmet durumunu, güncelleştirme durumunu, durum durumunu, sağlık sorunlarının sayısını ve algılayıcının ne zaman oluşturulduğunda onu oluşturduğunuzu gösterir.

    [![Algılayıcı sayfası.](../../media/defender-identity/sensor-page.png)](../../media/defender-identity/sensor-page.png#lightbox)

    >[!NOTE]
    >Kimlik için Defender portalında, algılayıcı ayarları ve sağlık bilgileri ayrı konumlarda yer alıyor. Not Microsoft 365 Defender şimdi aynı sayfada yer alan bir kişidir.

1. **Filtreler'i seçerseniz**, hangi filtrelerin kullanılabilir olacağını seçebilirsiniz. Daha sonra her filtre ile hangi algılayıcıların görüntüde görüntüleceklerini seçebilirsiniz.

    [![Algılayıcı filtreleri.](../../media/defender-identity/sensor-filters.png)](../../media/defender-identity/sensor-filters.png#lightbox)

    :::image type="content" source="../../media/defender-identity/filtered-sensor.png" alt-text="Filtrelenmiş algılayıcı" lightbox="../../media/defender-identity/filtered-sensor.png":::

1. Algılayıcılardan birini seçerek algılayıcı ve durumu hakkında bilgi edinen bir bölme görüntülenir.

    [![Algılayıcı ayrıntıları.](../../media/defender-identity/sensor-details.png)](../../media/defender-identity/sensor-details.png#lightbox)

1. Herhangi bir sağlık sorunuyla ilgili seçim yaparsanız, bu sorunlar hakkında daha fazla ayrıntıya sahip bir bölme elde edersiniz. Kapalı bir sorunu seçerseniz buradan yeniden açsanız iyi olur.

   :::image type="content" source="../../media/defender-identity/issue-details.png" alt-text="Sorun ayrıntıları" lightbox="../../media/defender-identity/issue-details.png":::
    

1. Algılayıcıyı **yönet'i** seçerek algılayıcı ayrıntılarını yapılandırabilirsiniz bir bölme açılır.

   :::image type="content" source="../../media/defender-identity/manage-sensor.png" alt-text="Algılayıcıyı yönet seçeneği" lightbox="../../media/defender-identity/manage-sensor.png":::

   :::image type="content" source="../../media/defender-identity/configure-sensor-details.png" alt-text="Algılayıcıya göre ayarları yapılandırılan sayfa" lightbox="../../media/defender-identity/configure-sensor-details.png":::

1. Algılayıcılar **sayfasında** , Dışarı Aktar'ı seçerek algılayıcılar listenizi bir .csv **aktarabilirsiniz**.

   :::image type="content" source="../../media/defender-identity/export-sensors.png" alt-text="Algılayıcıların listesini dışarı aktar" lightbox="../../media/defender-identity/export-sensors.png":::

## <a name="add-a-sensor"></a>Algılayıcı ekleyin

Algılayıcılar **sayfasından** yeni bir algılayıcı eklemeniz gerekir.

1. Algılayıcı **ekle'yi seçin**.

   :::image type="content" source="../../media/defender-identity/add-sensor.png" alt-text="Algılayıcı ekle seçeneği" lightbox="../../media/defender-identity/add-sensor.png":::

1. Algılayıcı yükleyicisini indirmeniz için bir düğme ve oluşturulan bir erişim anahtarı sağlayan bir bölme açılır.

   :::image type="content" source="../../media/defender-identity/installer-access-key.png" alt-text="Yükleyiciyi indirme ve anahtarı yeniden oluşturma seçenekleri" lightbox="../../media/defender-identity/installer-access-key.png":::

1. Paketi **yerel olarak kaydetmek** için Yükleyiciyi indir'i seçin. Zip dosyası aşağıdaki dosyaları içerir:

    - Kimlik için Defender algılayıcı yükleyicisi

    - Identity için Defender bulut hizmetine bağlanmak için gerekli bilgilerin yer olduğu yapılandırma ayar dosyası

1. **Access anahtarını kopyalayın**. Erişim anahtarı, Kimlik örneğinde Defender'a bağlanmak için Identity algılayıcısı için Defender'a gereklidir. Erişim anahtarı algılayıcı dağıtımı için bir defalık paroladır; bundan sonra tüm iletişimler kimlik doğrulaması ve TLS şifrelemesi için sertifikalar kullanılarak gerçekleştirilir. Yeni **erişim anahtarını yeniden oluşturmanız** gerekirse, Yeniden Oluştur anahtarı düğmesini kullanın. Daha önce dağıtılan algılayıcılardan herhangi birini etkilemez, çünkü yalnızca algılayıcının ilk kaydı için kullanılır.

1. Paketi, Identity algılayıcısı için Defender'ı yüklemekte olduğu adanmış sunucuya veya etki alanı denetleyicisine kopyalayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Kimlik güvenlik uyarıları için Defender'ı yönetme](manage-security-alerts.md)
