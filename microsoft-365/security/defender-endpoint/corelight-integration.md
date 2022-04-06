---
title: Uç Nokta için Microsoft Defender'de Corelight tümleştirmesini etkinleştirme
description: Ağın MDE'nin dağıtılmadığı alanlarda IoT/OT cihazlarına odaklanan görünürlük elde etmek için Corelight tümleştirmesini etkinleştirin
keywords: siem bağlayıcısını, siem'i, bağlayıcıyı, güvenlik bilgilerini ve olayları etkinleştirme
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: siosulli
author: siosulli
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: bf3095b9178b4ff2e71d4ee5f652d9316f233746
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664600"
---
# <a name="enable-corelight-data-integration"></a>Corelight veri tümleştirmesini etkinleştirin

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Microsoft, kuruluşunuz genelinde IoT/OT cihazlarını keşfetmenize yardımcı olmak için sektörün önde gelen açık ağ algılama ve yanıt (NDR) platformunun sağlayıcısı [Corelight](https://corelight.com/integrations/iot-security) ile iş ortaklığı yaptı. Corelight ağ gereçlerinden gönderilen verilerin kullanılması Microsoft 365 Defender, yönetilmeyen diğer cihazlarla veya dış ağlarla iletişim de dahil olmak üzere yönetilmeyen cihazların ağ etkinliklerine daha fazla görünürlük sağlar.

Bu veri kaynağı etkinleştirildiğinde Corelight ağ gereçlerinden gelen tüm olaylar Microsoft 365 Defender gönderilir. Bu etkinlikleri, Uç Nokta için Microsoft Defender cihaz envanterinde bulunan yönetilmeyen cihazlar zaman çizelgesinde görüntüleyebilirsiniz. Daha fazla bilgi için bkz [. Cihaz bulma](device-discovery.md).

## <a name="enabling-the-corelight-integration"></a>Corelight tümleştirmesini etkinleştirme

Corelight tümleştirmesini etkinleştirmek için aşağıdaki adımları uygulamanız gerekir:

[1. Adım: Corelight'ı veri kaynağı olarak açma](#step-1-turn-on-corelight-as-a-data-source)<br>
[2. Adım: Corelight'ın olayları Microsoft 365 Defender göndermesine izin verme](#step-2-provide-permission-for-corelight-to-send-events-to-microsoft-365-defender)<br>
[3. Adım: Corelight gerecinizi Microsoft 365 Defender'a veri gönderecek şekilde yapılandırma](#step-3-configure-your-corelight-appliance-to-send-data-to-microsoft-365-defender)

### <a name="step-1-turn-on-corelight-as-a-data-source"></a>1. Adım: Corelight'ı veri kaynağı olarak açma

1. Portalın gezinti bölmesinde [https://security.microsoft.com](https://security.microsoft.com/) **Cihaz bulma** \> **Veri** **kaynakları'nı Ayarlar** \> seçin.

   :::image type="content" source="images/enable-corelight.png" alt-text="Microsoft 365 Defender portalındaki veri kaynakları sayfası" lightbox="images/enable-corelight.png":::

2. **Corelight verilerini M365D'ye gönder'i** ve **ardından Kaydet'i** seçin.

### <a name="step-2-provide-permission-for-corelight-to-send-events-to-microsoft-365-defender"></a>2. Adım: Corelight'ın olayları Microsoft 365 Defender göndermesine izin verme

> [!NOTE]
> Corelight'a kuruluşunuzdaki kaynaklara erişim izni vermek için genel yönetici olmanız gerekir.

1. Kiracı Genel Yöneticisi olarak, izin vermek için bu [bağlantıya](<https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=d8be544e-9d1a-4825-a5cb-fb447457f692&response_type=code&sso_reload=true>) gidin.
2. Portala [https://security.microsoft.com](https://security.microsoft.com/) gidin, **Ayarlar Microsoft 365 Defender** \> seçin ve **Kiracı Kimliğini** not alın. Corelight gerecinizi yapılandırırken bu bilgilere ihtiyacınız olacaktır.

### <a name="step-3-configure-your-corelight-appliance-to-send-data-to-microsoft-365-defender"></a>3. Adım: Corelight gerecinizi Microsoft 365 Defender'a veri gönderecek şekilde yapılandırma

> [!NOTE]
>  Tümleştirme Corelight Sensor yazılımı v24 ve sonraki sürümlerde genel kullanıma sunulacaktır. 

v23 veya v22.1'de önizleme yapmak için GUI'deki yapılandırma bölümünü etkinleştirmek için yürütmeniz `corelight-client configuration update --enable.adfiot 1` gerekir.

Buna ek olarak, GUI doğrulaması tüm v23 sürümlerinde yapılandırma bölümünde bir aracının yapılandırılmasını gerektirir.  Sağladığınız aracı gereklidir ancak aslında kullanılmaz. Microsoft 365 Defender'a veri göndermeyi etkinleştirmek için aşağıdaki adımları uygulamadan önce doğrulamanın başarılı olduğundan emin olmak için _kafka aracısı_ alanına girin`127.0.0.1:1234`.

> [!NOTE]
> Çözümün çalışması için algılayıcınızın hem Defender hem de Corelight bulut hizmetlerine ulaşması için İnternet bağlantısına ihtiyacınız olacaktır.

#### <a name="enabling-in-the-corelight-sensor-gui"></a>Corelight Algılayıcı GUI'sinde etkinleştirme

1. Corelight Algılayıcı GUI yapılandırması bölümünde **Algılayıcı** \> **Dışarı Aktarma'yı** seçin.
2. Listeden **KAFKA'YA AKTAR'a** gidin ve açmak için anahtarı seçin.

   :::image type="content" source="images/exporttokafka.png" alt-text="Kafka dışarı aktarma" lightbox="images/exporttokafka.png":::

3. Ardından, **IOT için AZURE DEFENDER'A AKTAR'ı** açın ve 1. Adım'da belirtilen kiracı kimliğinizi KIRACı Kimliği alanına girin.

   :::image type="content" source="images/exporttodiot.png" alt-text="Iot dışarı aktarma" lightbox="images/exporttodiot.png":::

4. **Değişiklikleri Uygula'yı** seçin.

   :::image type="content" source="images/corelightapply.png" alt-text="Değişiklikleri uygula simgesi" lightbox="images/corelightapply.png":::

> [!NOTE]
> Kafka'daki yapılandırma seçenekleri (Günlük Dışlama ve Filtreler hariç) değiştirilmemelidir. Yapılan değişiklikler yoksayılır.

#### <a name="enabling-in-the-corelight-client"></a>corelight-client'da etkinleştirme

corelight-client içindeki aşağıdaki komutu kullanarak **KAFKA'YA AKTAR** ve **IOT için AZURE DEFENDER'A AKTAR'ı** açabilirsiniz:

`corelight-client configuration update --bro.export.kafka.defender.enable true --bro.export.kafka.defender.tenant\_id <your tenant>`.

> [!IMPORTANT]
> Kafka dışarı aktarmayı zaten kullanıyorsanız alternatif bir yapılandırma için Corelight Desteği'ne başvurun.

Yalnızca en az günlük kümesinin gönderilmesini yapılandırmak için:

1. Corelight Algılayıcı GUI'sinde Kafka bölümüne gidin
2. **Dışlamak için Zeek günlüklerine** gidin
3. **Tümünü** Seç
4. Ardından, Microsoft'a akmaya devam ettiğinden emin olmak için aşağıdaki günlüklerin yanındaki **x** işaretini seçin:  
    `dns  conn  files  http  ssl  ssh  x509  snmp  smtp  ftp  sip  dhcp  notice`
5. **Değişiklikleri Uygula'yı** seçin

Microsoft'a akan günlüklerin listesi zaman içinde genişleyebilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Cihaz keşfi hakkında SSS](device-discovery-faq.md)
