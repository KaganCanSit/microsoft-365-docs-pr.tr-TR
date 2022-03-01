---
title: Cihaz bulma'yi yapılandırma
description: Temel veya standart bulma kullanarak Microsoft 365 Defender bulma'nın nasıl yapılandırıldığından emin olun
keywords: temel, standart, uç nokta bulma yapılandırma, cihaz bulma
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 7b98ebf38d0e2e5ab5ec086e75002d0d660cff4c
ms.sourcegitcommit: 986ea76ecaceb5fe6b9616e553003e3c5b0df2e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2022
ms.locfileid: "63010804"
---
# <a name="configure-device-discovery"></a>Cihaz bulma'yi yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


Bulma, standart veya temel modda olacak şekilde yalıtabilirsiniz. Ağ ınız içinde etkin bir şekilde cihazları bulmak için standart seçeneği kullanın. Bu seçenek, uç noktaları bulmanızı daha iyi garanti ve daha zengin bir cihaz sınıflandırması sağlar.

Standart keşif gerçekleştirmek için kullanılan cihazların listesini özelleştirebilirsiniz. Bu özelliği de destekleyen tüm yerleşik cihazlarda (şu anda - Windows 10 veya daha sonraki bir sürümü ve yalnızca Windows Server 2019 veya daha sonraki cihazlar) standart bulma özelliğini etkinleştirebilirsiniz veya cihaz etiketlerini belirterek cihazlarınızı bir alt küme veya alt küme olarak belirleyebilirsiniz.

## <a name="set-up-device-discovery"></a>Cihaz bulma'ya ayarlama

Cihaz bulma ayarlarını yapmak için, bu portalda aşağıdaki <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender izleyin</a>:

Ekran den **Ayarlar** >  **bulma'ya gidin**

1. Yerleşik cihazlarınıza kullanmak üzere bulma modu olarak Basic'i yapılandırmak için Temel'i ve ardından Kaydet'i **seçin.** 
2. Standart keşif'i kullanmayı seçtiysanız, etkin olasılıklar için hangi cihazları kullanıcaz: tüm cihazlar veya bir alt küme üzerinde cihaz etiketlerini belirterek seçin ve sonra da Kaydet'i **seçin**

> [!NOTE]
>Standart keşif, ağdaki etkin şekilde cihazlarında etkin olarak cihaz sağlamak için çeşitli PowerShell betikleri kullanır. Bu PowerShell betikleri Microsoft tarafından imzalanmış ve şu konumdan yürütülür: `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\*.ps`. Örneğin, `C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Downloads\UnicastScannerV1.1.0.ps1`.

## <a name="exclude-devices-from-being-actively-probed-in-standard-discovery"></a>Cihazları, standart keşiflerde etkin bir şekilde bulmanın dışında tutabilirsiniz

Ağ üzerinde etkin bir şekilde taranmaması gereken cihazlar (örneğin, başka bir güvenlik aracı için amasya olarak kullanılan cihazlar) varsa, taranmalarını önlemek için bir dışlama listesi de tanımlayabilirsiniz. Cihazlar yine Temel bulma modu kullanılarak bulunamaktadır ve her zaman tekrar bulma denemeleri yoluyla da bulunabilirsiniz. Bu cihazlar pasif olarak keşfeder ancak etkin bir şekilde sahip olunmaz.

Cihazları Dışlamalar sayfasında hariç tutulacak **şekilde yapılandırabilirsiniz** .

## <a name="select-networks-to-monitor"></a>Izlenir ağları seçme

 Uç Nokta için Microsoft Defender ağı analiz eder ve bunun izlenmesi gereken bir şirket ağı mı yoksa yoksayılabilir şirket dışı bir ağ mı olduğunu belirler. Şirket ağları genelde izleniyor olarak seçilir. Bununla birlikte, şirket dışı ağların bulunduğu cihazları izlemeyi seçerek bu kararı geçersiz kılabilirsiniz.

Hangi ağların iz olacağını belirterek, cihaz bulmanın nerede gerçekleştiril olacağını yapılandırabilirsiniz. Ağ izlenirken, bu ağ üzerinde cihaz bulma yapılabilir.

izlenen ağlar sayfasında cihaz bulmanın gerçekleştiril olduğu **ağların listesi** görüntülenir.

> [!NOTE]
> Listede, şirket ağları olarak tanımlanan ağlar görüntülenir. 50'den az ağ şirket ağı olarak tanımlandı ise, listede en çok kullanılan cihaza sahip 50 ağ yer adede kadar görüntülenir.

izlenen ağlar listesi, son 7 gün içinde ağ üzerinde görülen toplam cihaz sayısına göre sıralenir.

Aşağıdaki ağ bulma durumları arasında herhangi birini görüntülemek için filtre uygulayabilirsiniz:

- **izlenen ağlar** - Cihaz bulmanın gerçekleştir olduğu ağlar.
- **Yoksayılan** ağlar - Bu ağ yoksayılır ve bu ağ üzerinde cihaz bulma işlemi gerçekleştir won won't.
- **Hepsi** - Hem izlenen hem de yoksayılan ağlar görüntülenir.

### <a name="configure-the-network-monitor-state"></a>Ağ izleme durumunu yapılandırma

Cihaz bulmanın nerede olduğunu siz kontrol edebilirsiniz. izlenen ağlar, cihaz bulmanın gerçekleştiril genellikle şirket ağları olduğu ağlarıdır. Ayrıca ağları yoksayma veya durumu değiştirdikten sonra ilk bulma sınıflandırmayı seçmeyi de seçebilirsiniz.

İlk bulma sınıflandırması seçme, sistem tarafından yapılan varsayılan ağ izleme durumunu uygulama anlamına gelir. Varsayılan sistem tarafından yapılan ağ izleme durumunun seçimi, şirket olarak tanımlanan, şirket dışı olarak tanımlanan ağların ve şirket dışı olarak tanımlanan ağların otomatik olarak yok sayılacak olması anlamına gelir.

1. Cihaz **bulma Ayarlar > seçin**.
2. izlenen **ağlar'ı seçin**.
3. Ağ listesini görüntüleme.
4. Ağ adının yanındaki üç noktayı seçin.
5. İlk keşif sınıflandırmayı izlemek, yoksaymak veya kullanmak isteyip istemediknizi seçin.

    > [!WARNING]
    >
    > - Şirket ağı olarak Uç Nokta için Microsoft Defender tarafından tanımilmeyen bir ağı izlemenin izlenmesi, şirket ağınız dışında cihaz keşfine neden olabilir ve bu nedenle ev cihazlarını veya şirket dışı diğer cihazları algılanabilir.
    > - Ağı yoksaymak, o ağda cihazları izleme ve keşfetmeyi durdurur. Önceden keşfedilen cihazlar stoktan çıkarılamaz, ancak artık güncelleştirilmez ve uç nokta için Defender'ın veri bekletme süresi sona erinceye kadar ayrıntılar korunur.
    > - Şirket dışı ağları izlemeyi seçmeden önce, bunu yapma izniniz olduğundan emin olun. <br>

6. Değişikliği yapmak istediğinize onaylayın.

## <a name="explore-devices-in-the-network"></a>Ağ'daki cihazları keşfedin

Ağ listesinde açıklanan her ağ adı hakkında daha fazla bağlam elde etmek için aşağıdaki gelişmiş arama sorgusunu kullanabilirsiniz. Sorgu, son 7 gün içinde belirli bir ağa bağlı olan tüm yerleşik cihazları listeler.

```kusto
DeviceNetworkInfo
| where Timestamp > ago(7d)
| where ConnectedNetworks  != ""
| extend ConnectedNetworksExp = parse_json(ConnectedNetworks)
| mv-expand bagexpansion = array ConnectedNetworks=ConnectedNetworksExp
| extend NetworkName = tostring(ConnectedNetworks ["Name"]), Description = tostring(ConnectedNetworks ["Description"]), NetworkCategory = tostring(ConnectedNetworks ["Category"])
| where NetworkName == "<your network name here>"
| summarize arg_max(Timestamp, *) by DeviceId
```

## <a name="get-information-on-device"></a>Cihaz hakkında bilgi al

Belirli bir cihaza en son tam bilgileri almak için aşağıdaki gelişmiş arama sorgusunu kullanabilirsiniz.

```kusto
DeviceInfo
| where DeviceName == "<device name here>" and isnotempty(OSPlatform)
| summarize arg_max(Timestamp, *) by DeviceId
```

## <a name="see-also"></a>Ayrıca bkz.

- [Cihaz keşfine genel bakış](device-discovery.md)
- [Cihaz bulma SSS](device-discovery-faq.md)
