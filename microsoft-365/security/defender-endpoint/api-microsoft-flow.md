---
title: Power Automate Connector'ın olayları için bir Flow ayarlamak için kullanma
ms.reviewer: ''
description: Kiracı Uç Nokta için Microsoft Defender Flow bir olay oluştuğunda tetiklenen bir akış oluşturmak için bu bağlayıcıyı kullanın.
keywords: akış, desteklenen api'ler, api, Microsoft akışı, sorgu, otomasyon, güç otomatikleştirme
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
ms.topic: how-to
MS.technology: mde
ms.custom: api
ms.openlocfilehash: 63626978311b679d0f8b520e4b041d92942bd1fd
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468005"
---
# <a name="how-to-use-power-automate-connector-to-set-up-a-flow-for-events"></a>Power Automate Connector'ın olayları için bir Flow ayarlamak için kullanma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Güvenlik yordamlarını otomatik hale getirerek, her modern Güvenlik İşlemleri Merkezi'nin (SOC) standart bir gereksinimi vardır. SOC ekiplerinin en verimli şekilde çalışması için otomasyon gerekir. Microsoft Power Automate, otomatik iş akışları oluşturmanıza ve birkaç dakika içinde  uç yordam otomasyonu oluşturmanıza yardımcı olur. Microsoft Power Automate, tam olarak bunun için yerleşik olan farklı bağlayıcıları destekler.  

Kiracınıza yeni bir uyarının oluşturulduğunda olduğu gibi, bir olay tarafından tetiklenen otomasyonları oluştururken size yol göstermede bu makaleyi kullanın. Microsoft Defender API'nin birçok Power Automate resmi bir Uygulama Bağlayıcısı vardır. 

:::image type="content" source="images/api-flow-0.png" alt-text="Microsoft Defender 365 portalında Eylemler sayfası" lightbox="images/api-flow-0.png" :::

> [!NOTE]
> Premium bağlayıcılar lisans önkoşulları hakkında daha fazla ayrıntı için bkz. [Premium bağlayıcıları için lisanslama](/power-automate/triggers-introduction#licensing-for-premium-connectors).

## <a name="usage-example"></a>Kullanım örneği

Aşağıdaki örnekte, kiracınız için her Flow uyarı oluştuğunda tetiklenen yeni bir uyarının nasıl oluşturulacak olduğu göstermektedir. Akışı başlatan etkinliği ve bu tetikleyici ortaya geldiğinde bir sonraki eylemin ne zaman alın olacağını tanımlamada size yollenir.  

1. [Microsoft Power Automate'te oturum Power Automate](https://flow.microsoft.com).

2. Akışlarım **Yeni** **Otomatik-boş** \> \> **olarak'a gidin**.

    :::image type="content" source="images/api-flow-1.png" alt-text="Microsoft Defender 365 portalında, Akışlarım menü öğesi altındaki Yeni akış bölmesi" lightbox="images/api-flow-1.png":::

3. Dosyanız için bir ad Flow, tetikleyici olarak "Microsoft Defender ATP Tetikleyicileri" araması ve ardından yeni Uyarılar tetikleyicisini seçin.

    :::image type="content" source="images/api-flow-2.png" alt-text=" Microsoft Defender 365 portalında Akışlarınızı seçin tetikleyicisi bölümü" lightbox="images/api-flow-2.png" :::

Artık her Flow uyarı oluştuğunda tetiklenen bir uyarı uyarına sahipsiniz.

:::image type="content" source="images/api-flow-3.png" alt-text="Tetikleyici açıklaması" lightbox="images/api-flow-3.png":::

Şimdi tek gereken sonraki adımlarınızı seçmek.
Örneğin, Uyarının Önem Düzeyi Yüksekse cihazı yalıtabilirsiniz ve bu konuda bir e-posta gönderebilirsiniz.
Uyarı tetikleyicisi yalnızca Uyarı Kimliği'ne ve Makine Kimliği'ne sağlar. Bağlayıcıyı kullanarak bu varlıkları genişletebilirsiniz.

### <a name="get-the-alert-entity-using-the-connector"></a>Bağlayıcıyı kullanarak Uyarı varlıklarını al

1. Yeni **adım için Microsoft Defender ATP'yi** seçin.

2. Uyarılar **- Tek uyarı API'si edinin'i seçin**.

3. Son **adımdan Uyarı** Kimliğini Giriş olarak **ayarlayın**.

    :::image type="content" source="images/api-flow-4.png" alt-text="Uyarılar bölmesi"  lightbox="images/api-flow-4.png":::

### <a name="isolate-the-device-if-the-alerts-severity-is-high"></a>Uyarının önem düzeyi Yüksekse cihazı yalıtmak

1. **Koşul'a** yeni adım olarak ekleme.

2. Uyarı önem düzeyi'nin **Yüksek'e eşit olup olduğunu** kontrol edin.

   Aldıysanız, **Microsoft Defender ATP - Makine Kimliği ile makine** eylemlerini yalıtmak ve bir açıklama eklemek.

    :::image type="content" source="images/api-flow-5.png" alt-text="Eylemler bölmesi"  lightbox="images/api-flow-5.png":::

3. Uyarı ve Yalıtım hakkında e-posta göndermek için yeni bir adım ekleyin. E-posta bağlayıcısı kullanımı çok kolay olan birden çok e-posta bağlayıcısı Outlook Gmail gibi.

4. Akışınızı kaydedin.

Ayrıca, Gelişmiş Av **sorgularını** ve çok daha fazlasını çalıştıran bir zamanlanmış akış da oluşturabilirsiniz!

## <a name="related-topic"></a>İlgili konu
- [Uç Nokta için Microsoft Defender API'leri](apis-intro.md)
