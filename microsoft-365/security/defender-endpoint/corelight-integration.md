---
title: Windows'da Corelight tümleştirmesini Uç Nokta için Microsoft Defender
description: Ağın MDE dağıtınmamış alanlarında IoT/OT cihazlarına odaklanan görünürlük kazanmak için Corelight tümleştirmesini etkinleştirme
keywords: siem bağlayıcısı, siem, bağlayıcı, güvenlik bilgileri ve olayları etkinleştirme
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
ms.openlocfilehash: 3a7a4b7ab842baaadb276e60037451e8eb919bf9
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465497"
---
# <a name="enable-corelight-data-integration"></a>Corelight veri tümleştirmesini etkinleştirme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!include[Prerelease information](../../includes/prerelease.md)]

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

Microsoft, kurum genelinde IoT/OT cihazlarını keşfetmenize yardımcı olmak için sektörde lider açık ağ algılama ve yanıt (NDR) platformunun sağlayıcısı [olan Corelight](https://corelight.com/integrations/iot-security) ile ortak çalışma yaptı. Corelight ağ gereçlerinden gönderilen verileri kullanarak, Microsoft 365 Defender, diğer unmanaged cihazlar veya dış ağlarla iletişim de dahil olmak üzere, unmand cihazların ağ etkinlikleri üzerinde daha fazla görünürlük sağlar.

Bu veri kaynağı etkinleştirildiğinde, Corelight ağ gereçlerinden gelen tüm olaylar Microsoft 365 Defender. Bu etkinlikleri, cihaz envanterinde bulunan, yönetimi olmayan cihazlar zaman Uç Nokta için Microsoft Defender görebilirsiniz. Daha fazla bilgi için bkz. [Cihaz bulma](device-discovery.md).

## <a name="enabling-the-corelight-integration"></a>Corelight tümleştirmesini etkinleştirme

Corelight tümleştirmesini etkinleştirmek için aşağıdaki adımları izleyin:

[1. Adım: Veri kaynağı olarak Corelight'i açma](#step-1-turn-on-corelight-as-a-data-source)<br>
[2. Adım: Corelight'a etkinlik gönderme izni Microsoft 365 Defender](#step-2-provide-permission-for-corelight-to-send-events-to-microsoft-365-defender)<br>
[3. Adım: Corelight cihazınızı cihaza veri göndermek için Microsoft 365 Defender](#step-3-configure-your-corelight-appliance-to-send-data-to-microsoft-365-defender)

### <a name="step-1-turn-on-corelight-as-a-data-source"></a>1. Adım: Veri kaynağı olarak Corelight'i açma

1. Portalın gezinti bölmesinde Cihaz bulma [https://security.microsoft.com](https://security.microsoft.com/) **Veri** **Ayarlar'i** \> \> **seçin**.

   :::image type="content" source="images/enable-corelight.png" alt-text="Microsoft 365 Defender portalında veri kaynakları sayfası" lightbox="images/enable-corelight.png":::

2. **Corelight verilerini M365D'ye gönder'i ve ardından Kaydet'i** **seçin**.

### <a name="step-2-provide-permission-for-corelight-to-send-events-to-microsoft-365-defender"></a>2. Adım: Corelight'a etkinlik gönderme izni Microsoft 365 Defender

> [!NOTE]
> Corelight'a kuruluş kaynakları için erişim izni vermek için genel yönetici olmak gerekir.

1. Kiracı Genel Yöneticisi olarak, izin vermek için [bu](<https://login.microsoftonline.com/common/oauth2/authorize?prompt=consent&client_id=d8be544e-9d1a-4825-a5cb-fb447457f692&response_type=code&sso_reload=true>) bağlantıya gidin.
2. Portala [https://security.microsoft.com](https://security.microsoft.com/) gidin, Kiracı **Ayarlar** \> **Microsoft 365 Defender** seçin ve Kiracı **Kimliği'ne göz atabilirsiniz**. Corelight cihazı yapılandırmanız için bu bilgiye ihtiyacınız olacak.

### <a name="step-3-configure-your-corelight-appliance-to-send-data-to-microsoft-365-defender"></a>3. Adım: Corelight cihazınızı cihaza veri göndermek için Microsoft 365 Defender

> [!NOTE]
>  Tümleştirme, Corelight Sensor software v24 ve sonraki programlarda genel olarak 12/24 saat açık olacak. 

v23 veya v22.1'de `corelight-client configuration update --enable.adfiot 1` önizleme yapmak için GUI'de yapılandırma bölümünü etkinleştirmek için yürütmeniz gerekir.

Buna ek olarak, GUI doğrulaması için tüm v23 yayınlarında yapılandırma bölümünde bir aracı yapılandırıldığından emin olmak gerekir.  Sizin sağlayan aracı gereklidir, ancak aslında kullanılmaz. Veri `127.0.0.1:1234` gönderilmesini _etkinleştirmek amacıyla_ aşağıdaki adımları takip edene kadar başarılı bir doğrulama sağlamak için önce burada her zaman başarılı bir şekilde onay Microsoft 365 Defender.

> [!NOTE]
> Çözümün çalışması için algılayıcınız için Defender ve Corelight bulut hizmetlerinin her ikisinde de İnternet bağlantısı olması gerekir.

#### <a name="enabling-in-the-corelight-sensor-gui"></a>Corelight Algılayıcı GUI'sinde etkinleştirme

1. Corelight Algılayıcı GUI yapılandırması bölümünde Algılayıcı Dışarı **Aktarma'ya** \> **tıklayın**.
2. Listeden **, DEMİ'YE AKTAR'a** gidin ve açmak için anahtarı seçin.

   :::image type="content" source="images/exporttokafka.png" alt-text="burada dışarı aktarma" lightbox="images/exporttokafka.png":::

3. Ardından, **IOT IÇIN AZURE DEFENDER'A** AKTAR'ı seçin ve KIRACı Kimliği alanında 1. Adımda adı geçen kiracı kimliğinizi girin.

   :::image type="content" source="images/exporttodiot.png" alt-text="iot dışarı aktarma" lightbox="images/exporttodiot.png":::

4. Değişiklikleri **Uygula'ya seçin**.

   :::image type="content" source="images/corelightapply.png" alt-text="Değişiklikleri uygula simgesi" lightbox="images/corelightapply.png":::

> [!NOTE]
> Her Zaman'daki yapılandırma seçenekleri (Günlük Dışlama ve Filtreler hariç) değiştirilemez. Yapılan değişiklikler yoksayılır.

#### <a name="enabling-in-the-corelight-client"></a>corelight-client'de etkinleştirme

corelight-client'daki aşağıdaki komutu kullanarak **IOT IÇIN AZURE DEFENDER'A** AKTAR **veİ** AKTARMA'yı açabilirsiniz:

`corelight-client configuration update --bro.export.kafka.defender.enable true --bro.export.kafka.defender.tenant\_id <your tenant>`.

> [!IMPORTANT]
> Dışarı aktarma aracını Kullanıyorsanız, alternatif bir yapılandırma için Corelight Desteği'ne başvurun.

Yalnızca en az sayıda günlük gönderilmesini yapılandırmak için:

1. Corelight Algılayıcı GUI'sinde, Işık bölümüne gidin
2. Dışarıda tutmak **için Zeek günlüklerine gitme**
3. Select **All**
4. Ardından, **Microsoft'a** akmaya devam etmek için aşağıdaki günlüklerin yanında x'i seçin:  
    `dns  conn  files  http  ssl  ssh  x509  snmp  smtp  ftp  sip  dhcp  notice`
5. Değişiklikleri **Uygula'yi seçin**

Microsoft'a akan günlükler listesi zamanla genişler.

## <a name="see-also"></a>Ayrıca bkz.

- [Cihaz bulma hakkında SSS](device-discovery-faq.md)
