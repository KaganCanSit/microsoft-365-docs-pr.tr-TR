---
title: Uç nokta için Microsoft Defender'daki cihazları dışla
description: Cihazları cihaz stok listesinden çıkar
keywords: dışla
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
ms.openlocfilehash: c17bea7b6a3decdb1cf20f21067c316366c2afed
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63705072"
---
# <a name="exclude-devices"></a>Cihazları dışla

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-respondmachine-abovefoldlink)

## <a name="exclude-devices-from-threat-and-vulnerability-management"></a>Cihazları diğer Tehdit ve Güvenlik Açığı Yönetimi

Etkin olmayan, yinelenen veya kapsam dışında kalan cihazlar hariç olmak üzere etkin cihazlarınız üzerinde riskleri keşfetmeye ve önceliklerini belirlemeye odaklanmanıza olanak tanır. Bu eylem, açık kalma Tehdit ve Güvenlik Açığı Yönetimi daha doğru bir şekilde yansıtmanıza da yardımcı olabilir, çünkü dışarıda bırakılan cihazlar Tehdit ve Güvenlik Açığı Yönetimi.

Cihazlar dışlandıktan sonra, bu cihazlardaki güvenlik açıkları ve yüklü yazılımla ilgili güncelleştirilmiş veya ilgili bilgileri görüntüemezsiniz. Gelişmiş avdaki tüm Tehdit ve Güvenlik Açığı Yönetimi sayfaları, raporları ve ilgili tabloları etkiler.

Cihaz dışlama özelliği sayfalar ve raporlardan güvenlik açığı yönetimi verileri kaldırsa da, cihazlar ağa bağlı kalır ve kuruluş için risk altında olabilir. Cihaz dışlama işlemini istediğiniz zaman iptal edebilirsiniz.

## <a name="how-to-exclude-a-device"></a>Cihaz dışlama

Tek bir cihazı veya birden çok cihazı aynı anda hariç tutabilirsiniz.

### <a name="exclude-a-single-device"></a>Tek bir cihazı dışla

1. Cihaz **envanteri sayfasına gidin** ve dışarıda bırakılacak cihazı seçin.
2. Cihaz **envanter** sayfasındaki eylem çubuğundan veya cihaz açılır öğesinde eylemler menüsünden Dışarıda Bırak'ı seçin.

![Cihazı dışla menü seçeneğinin resmi.](images/exclude-devices-menu.png)

 3. Bir gerekçelendirme seçin:

    - Etkin olmayan cihaz
    - Cihazı çoğalt
    - Cihaz mevcut değil
    - Kapsam dışında  
    - Diğer

4. Bir not yazın ve Cihazı **dışla'ya seçin**.

![Cihazı dışla'nın görüntüsü.](images/exclude-device.png)

Ayrıca bir cihazı cihaz sayfasından da çıkarabilirsiniz.

> [!NOTE]
> Etkin cihazların hariç olması önerilmez, çünkü özellikle güvenlik açığı bilgilerini görünürlüğü olmaz. Bir cihaz etkinse ve cihaz hariç tutmak istemiyorsanız, bir uyarı iletisi ve etkin bir cihazı dışarıda tutmak istediğinizden emin olup olamamanızı isteyen bir onay açılır iletisi alırsınız.

Bir cihazın görünümler ve verilerin tamamen dışlanmış olması 10 güvenlik açığı yönetimi kadar sürebilir.

Dışarıda bırakılan cihazlar, Cihaz envanteri listesinde görünmeye devam eder. Dışlanan cihazların görünümünü şu şekilde yönetebilirsiniz:

- Cihaz stok **görünümüne** Dışlama durumu sütunu ekleme.
- uygun  **cihaz listesini görüntülemek içinExclusion**  statefilter'ı kullanma.

![Dışlama durumunun resmi.](images/exclusion-state.png)

### <a name="bulk-device-exclusion"></a>Toplu cihaz dışlama

Ayrıca, aynı anda birden çok cihazı hariç tutmak da seçebilirsiniz:

1. Cihaz **envanteri sayfasına gidin** ve hariç tutulacak cihazları seçin.

2. Eylemler çubuğunda Dışla'ya **seçin**.

3. Bir gerekçelendirme seçin ve Cihazı **dışla'ya seçin**.

Cihaz listesinde farklı dışlama durumları olan birden fazla cihaz seçtiysiniz, seçili cihazların dışlama uçlaması seçili cihazların kaç cihazın zaten dışlanmış olduğuyla ilgili ayrıntıları sağlar. Cihazları yeniden hariç tutabilirsiniz, ancak gerekçe ve notlar geçersiz kılınır.

![Toplu hariç tutmak için resim](images/exclude-device-bulk.png)

Cihaz dışlandıktan sonra, dışarıda bırakılan bir cihazın cihaz sayfasına gidersanız, bulunan güvenlik açıkları, yazılım envanteri veya güvenlik önerileriyle ilgili verileri görüntüleyebilirsiniz. Veriler aynı zamanda kişisel sayfalarda, güvenlik açığı yönetimi gelişmiş av tablolarında ve korumasız cihazlar raporunda da yer almayacaktır.

## <a name="stop-excluding-a-device"></a>Cihaz hariç durma

Cihaz hariç tutulacak herhangi bir zamanda bunu durdurabilirsiniz. Cihazlar artık hariç tutulamazsa güvenlik açığı verileri sayfalarda, raporlarda ve gelişmiş güvenlik açığı yönetimi aramalarda görünür. Değişikliklerin yürürlüğe girecekleri 8 saat kadar sürebilir.

1. Cihaz envantere gidin, dışarıyı açmak için dışarıda bırakılan cihazı seçin ve ardından Dışlama **ayrıntıları'ı seçin**
2. **Dışlamayı durdur'ı seçin**

![Dışlama ayrıntılarının resmi](images/exclusion-details.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Cihaz envanteri](machines-view-overview.md)
