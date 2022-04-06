---
title: Ekleme veya işe kapatma bildirim kuralı oluşturma
description: Yerel bir ekleme veya işe kapatma betiği kullanılırken bildirim alırsınız.
keywords: ekleme, çıkarma, yerel, betik, bildirim, kural
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 0208e21394e350c2b5ffffdca6f8e14ebba227c8
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476059"
---
# <a name="create-a-notification-rule-when-a-local-onboarding-or-offboarding-script-is-used"></a>Yerel bir ekleme veya çıkarma betiği kullanılırken bildirim kuralı oluşturma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

[!include[Microsoft Defender for Endpoint API URIs for US Government](../../includes/microsoft-defender-api-usgov.md)]

[!include[Improve request performance](../../includes/improve-request-performance.md)]


Yerel bir ekleme veya işe kapatma betiği kullanılırken size bildirilmesi için bir bildirim kuralı oluşturun.

## <a name="before-you-begin"></a>Başlamadan önce

Şu bilgilere erişiminiz gerekir:

- Power Automate (Kullanıcı başına plan en az). Daha fazla bilgi için, [Power Automate bakın](https://flow.microsoft.com/pricing/).
- Azure Tablosu veya SharePoint Listesi veya Kitaplığı / SQL DB.

## <a name="create-the-notification-flow"></a>Bildirim akışı oluşturma

1. [Flow.microsoft.com.](https://flow.microsoft.com/)

2. Boştan **, Yeni > - Zamanlanmış> Akışlarım'a gidin**.

   :::image type="content" source="images/new-flow.png" alt-text="Akış" lightbox="images/new-flow.png":::


3. Zamanlanmış bir akış oluşturma.
   1. Bir akış adı girin.
   2. Başlangıç ve saati belirtin.
   3. Sıklığı belirtin. Örneğin, her 5 dakikada bir.

   :::image type="content" source="images/build-flow.png" alt-text="Bildirim akışı" lightbox="images/build-flow.png":::

4. Yeni eylem eklemek için + düğmesini seçin. Yeni eylem, Uç nokta güvenlik merkezi cihaz(lar) API'si için Defender'a bir HTTP isteği olur. Ayrıca, bunu hazır gelen "WDATP Bağlayıcısı" (eylem: "Makineler - Makinelerin listesini alın") ile de değiştirebilirsiniz.

   :::image type="content" source="images/recurrence-add.png" alt-text="Yineleme ve eylem ekleme" lightbox="images/recurrence-add.png":::

5. Aşağıdaki HTTP alanlarını girin:

   - Yöntem: Cihazların listesini almak için bir değer olarak "GET".
   - URI: Enter `https://api.securitycenter.microsoft.com/api/machines`.
   - Kimlik Doğrulaması: "Active Directory OAuth" öğesini seçin.
   - Kiracı: Oturum açın ve Uygulama https://portal.azure.com Kayıtlarını **Azure Active Directory > gidin ve** Kiracı Kimliği değerini alın.
   - Hedef kitle: `https://securitycenter.onmicrosoft.com/windowsatpservice\`
   - İstemci Kimliği: Oturum açın ve kayıt https://portal.azure.com Azure Active Directory > **gidin ve** İstemci Kimliği değerini alın.
   - Kimlik Bilgileri Türü: "Gizli" öğesini seçin.
   - Gizli: Oturum açın ve Uygulama https://portal.azure.com Kayıtlarını **Azure Active Directory > gidin ve** Kiracı Kimliği değerini alın.

    :::image type="content" source="images/http-conditions.png" alt-text="HTTP koşulları" lightbox="images/http-conditions.png":::

6. Yeni eylem ekle'yi seçerek yeni **bir adım ekleyin, ardından** Veri **İşlemleri'i arayın** ve **Parse JSON'u seçin**.

   :::image type="content" source="images/data-operations.png" alt-text="Veri işlemleri girdisi" lightbox="images/data-operations.png":::

7. İçerik alanına Gövde **Ekle.'yi** seçin.

   :::image type="content" source="images/parse-json.png" alt-text="Parse JSON bölümü" lightbox="images/parse-json.png":::

8. Şema bağlantısı **oluşturmak için örnek yük kullan'ı** seçin.

   :::image type="content" source="images/parse-json-schema.png" alt-text="Yükli JSON ayrıştırma" lightbox="images/parse-json-schema.png":::

9. Aşağıdaki JSON parçacığını kopyalayıp yapıştırın:

    ```json
    {
        "type": "object",
        "properties": {
            "@@odata.context": {
                "type": "string"
            },
            "value": {
                "type": "array",
                "items": {
                    "type": "object",
                    "properties": {
                        "id": {
                            "type": "string"
                        },
                        "computerDnsName": {
                            "type": "string"
                        },
                        "firstSeen": {
                            "type": "string"
                        },
                        "lastSeen": {
                            "type": "string"
                        },
                        "osPlatform": {
                            "type": "string"
                        },
                        "osVersion": {},
                        "lastIpAddress": {
                            "type": "string"
                        },
                        "lastExternalIpAddress": {
                            "type": "string"
                        },
                        "agentVersion": {
                            "type": "string"
                        },
                        "osBuild": {
                            "type": "integer"
                        },
                        "healthStatus": {
                            "type": "string"
                        },
                        "riskScore": {
                            "type": "string"
                        },
                        "exposureScore": {
                            "type": "string"
                        },
                        "aadDeviceId": {},
                        "machineTags": {
                            "type": "array"
                        }
                    },
                    "required": [
                        "id",
                        "computerDnsName",
                        "firstSeen",
                        "lastSeen",
                        "osPlatform",
                        "osVersion",
                        "lastIpAddress",
                        "lastExternalIpAddress",
                        "agentVersion",
                        "osBuild",
                        "healthStatus",
                        "rbacGroupId",
                        "rbacGroupName",
                        "riskScore",
                        "exposureScore",
                        "aadDeviceId",
                        "machineTags"
                    ]
                }
            }
        }
    }

    ```

10. JSON aramalarından değerleri ayıkla ve örnek olarak, yerleşik cihazın / olduğunu ya da SharePoint kaydedip kayıtlı olduğunu kontrol edin:

    - Evet ise, hiçbir bildirim tetikli olmaz
    - Hayırsa, yeni cihaz (veya cihaz) cihaz listesini SharePoint uç nokta yöneticisi için Defender'a bir bildirim gönderilir.

    :::image type="content" source="images/flow-apply.png" alt-text="Her öğeye akış uygulaması" lightbox="images/flow-apply.png":::

    :::image type="content" source="images/apply-to-each.png" alt-text="Öğeleri al öğesine akışın uygulaması" lightbox="images/apply-to-each.png":::

11. Koşul **altında**, şu ifadeyi ekleyin: "length(body('Get_items')?[' value'])" değerini seçin ve koşulu 0'a eşit olarak ayarlayın.

    :::image type="content" source="images/apply-to-each-value.png" alt-text="Her koşula akışın uygulaması" lightbox="images/apply-to-each-value.png":::
    :::image type="content" source="images/conditions-2.png" alt-text="Koşul-1" lightbox="images/conditions-2.png":::
    :::image type="content" source="images/condition3.png" alt-text="Koşul-2" lightbox="images/condition3.png":::
    :::image type="content" source="images/send-email.png" alt-text="E-posta gönderme bölümü" lightbox="images/send-email.png":::

## <a name="alert-notification"></a>Uyarı bildirimi

Aşağıdaki resim bir e-posta bildirimi örneğidir.

:::image type="content" source="images/alert-notification.png" alt-text="E-posta bildirim ekranı" lightbox="images/alert-notification.png":::

## <a name="tips"></a>İpuçları

- Burada yalnızca sonEnen ifadesini kullanarak filtreyi  filtrelemeniz gerekir:
  - Her 60 dak:
    - Son 7 gün içinde görülen tüm cihazları alır.

- Her cihaz için:
  - Son görülen özellik [-7 gün, -7 gün + 60 dakika ] -> alan için uyarı.
  - İlk kez son saat -son saatte görülürse > Uyarısı.

Bu çözümde yinelenen uyarılarınız olmaz: Çok sayıda cihazı olan kiracılar vardır. Tüm bu cihazları almak çok pahalı olabilir ve diskte işlem gerektirir.

Bunu iki sorguya bölüyoruz:

1. Çıkararak çalışma için yalnızca bu zaman aralığı OData $filter ve yalnızca koşulların karşı şartlara uygun olduğunu bildirerek devam edin.
2. Son saat içinde görülen tüm cihazları alıp ilk görülme özelliğini kontrol edin (ilk görülen özellik son saatte ise son görülen özelliğin de orada olması gerekir).
