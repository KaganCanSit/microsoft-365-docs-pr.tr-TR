---
title: Microsoft Defender for Identity sensor health and settings in Microsoft 365 Defender
description: Microsoft Defender for Identity algılayıcıları için yapılandırarak sistem durumunu nasıl takip Microsoft 365 Defender
ms.date: 06/07/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: f55cb36d9960fef2da977a2c50ebab5a9e0e9122
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63682030"
---
# <a name="microsoft-defender-for-identity-sensor-health-and-settings-in-microsoft-365-defender"></a>Microsoft Defender for Identity sensor health and settings in Microsoft 365 Defender

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender
- Kimlik için Defender

Bu makalede, Windows'da Kimlik algılayıcıları için [Microsoft Defender'ı](/defender-for-identity) yapılandırma [ve Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

>[!IMPORTANT]
>Kimlik Doğrulama ve Doğrulama Microsoft 365 Defender bir parçası olarak, kimlik için Defender portalında yer alan konumlarından bazı seçenekler ve ayrıntılar değiştirilmiştir. Hem tanıdık hem de yeni özellikleri nerede bulamıyorum? bulmak için lütfen aşağıdaki ayrıntıları okuyun.

## <a name="view-defender-for-identity-sensor-settings-and-status"></a>Kimlik algılayıcısı ayarları ve durumu için Defender'ı görüntüleme

1. Daha <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>, Kimlikler'Ayarlar'e **gidin**.

    ![Kimlikler'Ayarlar ardından Kimlikler'e gidin.](../../media/defender-identity/settings-identities.png)

1. Kimlik **algılayıcıları** için Defender'nizin tüm görüntü olarak Algılayıcılar sayfasını seçin. Her algılayıcı için, algılayıcının adını, etki alanı üyeliğini, sürüm numarasını, güncelleştirmelerin gecikirse, hizmet durumunu, güncelleştirme durumunu, durum durumunu, sağlık sorunlarının sayısını ve algılayıcının ne zaman oluşturulduğunda onu oluşturduğunuzu gösterir.

    [![Algılayıcı sayfası.](../../media/defender-identity/sensor-page.png)](../../media/defender-identity/sensor-page.png#lightbox)

    >[!NOTE]
    >Kimlik için Defender portalında, algılayıcı ayarları ve sağlık bilgileri ayrı konumlarda yer alıyor. Not Microsoft 365 Defender şimdi aynı sayfada yer alan bir kişidir.

1. **Filtreler'i seçerseniz**, hangi filtrelerin kullanılabilir olacağını seçebilirsiniz. Daha sonra her filtre ile hangi algılayıcıların görüntüde görüntüleceklerini seçebilirsiniz.

    [![Algılayıcı filtreleri.](../../media/defender-identity/sensor-filters.png)](../../media/defender-identity/sensor-filters.png#lightbox)

    ![Filtrelenmiş algılayıcı.](../../media/defender-identity/filtered-sensor.png)

1. Algılayıcılardan birini seçerek algılayıcı ve durumu hakkında bilgi edinen bir bölme görüntülenir.

    [![Algılayıcı ayrıntıları.](../../media/defender-identity/sensor-details.png)](../../media/defender-identity/sensor-details.png#lightbox)

1. Herhangi bir sağlık sorunuyla ilgili seçim yaparsanız, bu sorunlar hakkında daha fazla ayrıntıya sahip bir bölme elde edersiniz. Kapalı bir sorunu seçerseniz buradan yeniden açsanız iyi olur.

    ![Sorunun ayrıntıları.](../../media/defender-identity/issue-details.png)

1. Algılayıcıyı **yönet'i** seçerek algılayıcı ayrıntılarını yapılandırabilirsiniz bir bölme açılır.

    ![Algılayıcıyı yönetin.](../../media/defender-identity/manage-sensor.png)

    ![Algılayıcı ayrıntılarını yapılandırabilirsiniz.](../../media/defender-identity/configure-sensor-details.png)

1. Algılayıcılar **sayfasında** , Dışarı Aktar'ı seçerek algılayıcılar listenizi bir .csv **aktarabilirsiniz**.

    ![Algılayıcı listesini dışarı aktar.](../../media/defender-identity/export-sensors.png)

## <a name="add-a-sensor"></a>Algılayıcı ekleyin

Algılayıcılar **sayfasından** yeni bir algılayıcı eklemeniz gerekir.

1. Algılayıcı **ekle'yi seçin**.

    ![Algılayıcı ekleyin.](../../media/defender-identity/add-sensor.png)

1. Algılayıcı yükleyicisini indirmeniz için bir düğme ve oluşturulan bir erişim anahtarı sağlayan bir bölme açılır.

    ![Yükleyici ve erişim anahtarını indirin.](../../media/defender-identity/installer-access-key.png)

1. Paketi **yerel olarak kaydetmek** için Yükleyiciyi indir'i seçin. Zip dosyası aşağıdaki dosyaları içerir:

    - Kimlik için Defender algılayıcı yükleyicisi

    - Identity için Defender bulut hizmetine bağlanmak için gerekli bilgilerin yer olduğu yapılandırma ayar dosyası

1. **Access anahtarını kopyalayın**. Erişim anahtarı, Kimlik örneğinde Defender'a bağlanmak için Identity algılayıcısı için Defender'a gereklidir. Erişim anahtarı algılayıcı dağıtımı için bir defalık paroladır; bundan sonra tüm iletişimler kimlik doğrulaması ve TLS şifrelemesi için sertifikalar kullanılarak gerçekleştirilir. Yeni **erişim anahtarını yeniden oluşturmanız** gerekirse, Yeniden Oluştur anahtarı düğmesini kullanın. Daha önce dağıtılan algılayıcılardan herhangi birini etkilemez, çünkü yalnızca algılayıcının ilk kaydı için kullanılır.

1. Paketi, Identity algılayıcısı için Defender'ı yüklemekte olduğu adanmış sunucuya veya etki alanı denetleyicisine kopyalayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Kimlik güvenlik uyarıları için Defender'ı yönetme](manage-security-alerts.md)
