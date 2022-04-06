---
title: Uç Nokta için Microsoft Defender'de cihazları dışlama
description: Cihazları cihaz envanter listesinden dışlama
keywords: Dışlamak
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
ms.openlocfilehash: cbfc82f56cc1922a663c31defe30dc61c2d3dd9b
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664160"
---
# <a name="exclude-devices"></a>Cihazları dışlayın

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimlemek mi istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-respondmachine-abovefoldlink)

## <a name="exclude-devices-from-threat-and-vulnerability-management"></a>Cihazları Tehdit ve Güvenlik Açığı Yönetimi dışında tutma

Etkin olmayan, yinelenen veya kapsamı dışında olan cihazları dışlamak, etkin cihazlarınızdaki riskleri keşfetmeye ve önceliklendirmeye odaklanmanıza olanak tanır. Dışlanan cihazlar Tehdit ve Güvenlik Açığı Yönetimi raporlarınızda görünmeyebileceği için bu eylem daha doğru bir Tehdit ve Güvenlik Açığı Yönetimi maruz kalma puanını yansıtmaya da yardımcı olabilir.

Cihazlar dışlandıktan sonra, bu cihazlarda güvenlik açıkları ve yüklü yazılımlar hakkında güncelleştirilmiş veya ilgili bilgileri görüntüleyemezsiniz. Gelişmiş avcılıkta tüm Tehdit ve Güvenlik Açığı Yönetimi sayfaları, raporları ve ilgili tabloları etkiler.

Cihaz dışlama özelliği cihaz verilerini güvenlik açığı yönetimi sayfalardan ve raporlardan kaldırsa da, cihazlar ağa bağlı kalır ve kuruluş için bir risk olmaya devam edebilir. İstediğiniz zaman cihaz dışlama işlemini iptal edebilirsiniz.

## <a name="how-to-exclude-a-device"></a>Cihazı dışlama

Tek bir cihazı veya birden çok cihazı aynı anda dışlamamayı seçebilirsiniz.

### <a name="exclude-a-single-device"></a>Tek bir cihazı dışlama

1. **Cihaz envanteri** sayfasına gidin ve dışlamak istediğiniz cihazı seçin.
2. Cihaz envanteri sayfasındaki eylem çubuğundan veya cihaz açılır öğesindeki eylemler menüsünden **Dışla'yı** seçin.

   ![Cihazı dışla menü seçeneğinin görüntüsü.](images/exclude-devices-menu.png)

3. Bir gerekçe seçin:

    - Etkin olmayan cihaz
    - Yinelenen cihaz
    - Cihaz yok
    - Kapsam dışı
    - Diğer

4. Bir not yazın ve **Cihazı dışla'yı** seçin.

![Cihazı dışlama görüntüsü.](images/exclude-device.png)

Ayrıca bir cihazı cihaz sayfasından dışlayabilirsiniz.

> [!NOTE]
> Etkin cihazların dışlanması önerilmez, çünkü güvenlik açığı bilgilerine görünürlük sağlamamak özellikle risklidir. Bir cihaz etkinse ve cihazı dışlamaya çalışırsanız, etkin bir cihazı dışlamak istediğinizden emin olup olmadığınız sorusunu soran bir uyarı iletisi ve bir onay açılır penceresi alırsınız.

Bir cihazın güvenlik açığı yönetimi görünümlerden ve verilerden tamamen dışlanması 10 saate kadar sürebilir.

Dışlanan cihazlar, Cihaz envanteri listesinde görünmeye devam ediyor. Dışlanan cihazlar görünümünüzü şu şekilde yönetebilirsiniz:

- **Dışlama durumu** sütununu cihaz envanter görünümüne ekleme.
- İlgili cihaz listesini görüntülemek için **Dışlama durumu** filtresini kullanma.

![Dışlama durumunun görüntüsü.](images/exclusion-state.png)

### <a name="bulk-device-exclusion"></a>Toplu cihaz dışlama

Aynı anda birden çok cihazı dışlama seçeneğini de belirleyebilirsiniz:

1. **Cihaz envanteri** sayfasına gidin ve hariç tutulacak cihazları seçin.

2. Eylemler çubuğunda **Dışla'yı** seçin.

3. Bir gerekçe seçin ve **Cihazı dışla'yı** seçin.

Cihaz listesinde farklı dışlama durumlarına sahip birden çok cihaz seçerseniz, seçili cihazların dışlanması açılır öğesi, seçili cihazların kaçının zaten dışlandığının ayrıntılarını sağlar. Cihazları yeniden dışlayabilirsiniz, ancak gerekçe ve notlar geçersiz kılınacaktır.

![Toplu dışlama görüntüsü](images/exclude-device-bulk.png)

Bir cihaz dışlandıktan sonra, dışlanan bir cihazın cihaz sayfasına giderseniz bulunan güvenlik açıklarına, yazılım envanterine veya güvenlik önerilerine ilişkin verileri göremezsiniz. Veriler güvenlik açığı yönetimi sayfalarında, ilgili gelişmiş tehdit avcılığı tablolarında ve güvenlik açığı bulunan cihazlar raporunda da gösterilmez.

## <a name="stop-excluding-a-device"></a>Cihazı dışlamayı durdurma

İstediğiniz zaman bir cihazı dışlamayı durdurabilirsiniz. Cihazlar artık dışlanmadıktan sonra güvenlik açığı verileri güvenlik açığı yönetimi sayfalarda, raporlarda ve gelişmiş tehdit avcılığında görünür. Değişikliklerin geçerli olması 8 saat kadar sürebilir.

1. Cihaz envanterine gidin, dışlanan cihazı seçerek açılır öğeyi açın ve ardından **Dışlama ayrıntıları'nı** seçin
2. **Dışlamayı durdur'u** seçin

![Dışlama ayrıntılarının resmi](images/exclusion-details.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Cihaz envanteri](machines-view-overview.md)
