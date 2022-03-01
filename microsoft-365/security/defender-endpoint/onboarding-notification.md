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
ms.openlocfilehash: 36713496b5885866dd21a3402dcfe66b4af5b76e
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998254"
---
# <a name="create-a-notification-rule-when-a-local-onboarding-or-offboarding-script-is-used"></a>Yerel bir ekleme veya çıkarma betiği kullanılırken bildirim kuralı oluşturma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

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

    ![Akış görüntüsü.](images/new-flow.png)

3. Zamanlanmış bir akış oluşturma.
   1. Bir akış adı girin.
   2. Başlangıç ve saati belirtin.
   3. Sıklığı belirtin. Örneğin, her 5 dakikada bir.

    ![Bildirim akışının resmi.](images/build-flow.png)

4. Yeni eylem eklemek için + düğmesini seçin. Yeni eylem, Uç nokta güvenlik merkezi cihaz(lar) API'si için Defender'a bir HTTP isteği olur. Ayrıca, bunu hazır gelen "WDATP Bağlayıcısı" (eylem: "Makineler - Makinelerin listesini alın") ile de değiştirebilirsiniz.

    ![Yineleme ve eylem ekleme resmi.](images/recurrence-add.png)

5. Aşağıdaki HTTP alanlarını girin:

   - Yöntem: Cihazların listesini almak için bir değer olarak "GET".
   - URI: Enter `https://api.securitycenter.microsoft.com/api/machines`.
   - Kimlik Doğrulaması: "Active Directory OAuth" öğesini seçin.
   - Kiracı: Oturum açın ve Uygulama https://portal.azure.com Kayıtlarını **Azure Active Directory > gidin ve** Kiracı Kimliği değerini alın.
   - Hedef kitle: `https://securitycenter.onmicrosoft.com/windowsatpservice\`
   - İstemci Kimliği: Oturum açın ve kayıt https://portal.azure.com Azure Active Directory > **gidin ve** İstemci Kimliği değerini alın.
   - Kimlik Bilgileri Türü: "Gizli" öğesini seçin.
   - Gizli: Oturum açın ve Uygulama https://portal.azure.com Kayıtlarını **Azure Active Directory > gidin ve** Kiracı Kimliği değerini alın.

    ![HTTP koşullarının resmi.](images/http-conditions.png)

6. Yeni eylem ekle'yi seçerek yeni **bir adım ekleyin, ardından** Veri **İşlemleri'i arayın** ve **Parse JSON'u seçin**.

    ![Veri işlemlerinin görüntüsü.](images/data-operations.png)

7. İçerik alanına Gövde **Ekle.'yi** seçin.

    ![parse JSON görüntüsü.](images/parse-json.png)

8. Şema bağlantısı **oluşturmak için örnek yük kullan'ı** seçin.

    ![Yükli parse json resmi.](images/parse-json-schema.png)

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

    ![Her biri için geçerli olan resim.](images/flow-apply.png)

    ![Get items ile her biri için geçerli olan resmi.](images/apply-to-each.png)

11. Koşul **altında**, şu ifadeyi ekleyin: "length(body('Get_items')?[' value'])" değerini seçin ve koşulu 0'a eşit olarak ayarlayın.

    ![Her koşula uygulama resmi.](images/apply-to-each-value.png)
    ![ Koşul1'in görüntüsü.](images/conditions-2.png)
    ![ Koşul2'nin resmi.](images/condition3.png)
    ![ E-posta gönderme resmi.](images/send-email.png)

## <a name="alert-notification"></a>Uyarı bildirimi

Aşağıdaki resim bir e-posta bildirimi örneğidir.

![E-posta bildiriminin resmi.](images/alert-notification.png)

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
