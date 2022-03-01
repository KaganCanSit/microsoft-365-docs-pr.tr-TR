---
title: İleri gelen sunuculardan sonra oluşan bağlantı olaylarını araştırma
description: Proxy yerine gerçek bir hedef ortaya çıkaran Uç Nokta için Microsoft Defender'da ağ koruması aracılığıyla gelişmiş HTTP düzeyi izlemesini kullanmayı öğrenin.
keywords: proxy, ağ koruması, proxy'i iletme, ağ olayları, denetim, engelleme, etki alanı adları, etki alanı
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c0a2bdab641f0289975f1d8475627d3066ecf1f8
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021764"
---
# <a name="investigate-connection-events-that-occur-behind-forward-proxies"></a>İleri gelen sunuculardan sonra oluşan bağlantı olaylarını araştırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatemachines-abovefoldlink)

Uç Nokta için Defender, farklı ağ yığını düzeylerinden ağ bağlantısını izlemeyi destekler. Zorlu bir durum, ağın İnternet'e bir ağ geçidi olarak ileriye doğru ara sunucu kullandığı durumdur.

Ara sunucu, hedef uç nokta gibi davranır. Böyle durumlarda, basit ağ bağlantısı monitörleri doğru olan ancak daha düşük araştırma değerine sahip ara sunucuyla bağlantıları denetlemektedir.

Uç Nokta için Defender, ağ koruması aracılığıyla gelişmiş HTTP düzeyi izlemesini destekler. Açık olduğunda, gerçek hedef etki alanı adlarını ortaya çıkaran yeni bir olay türü ortaya çıkar.

## <a name="use-network-protection-to-monitor-network-connection-behind-a-firewall"></a>Güvenlik duvarının arkasında ağ bağlantısını izlemek için ağ korumasını kullanma

Ağ korumasından kaynaklanan diğer ağ olayları nedeniyle ileri proxy arkasında ağ bağlantısını izlemek mümkündür. Bunları bir cihaz zaman çizelgesinde görmek için ağ korumasını açın (en azından denetim modunda).

Ağ koruması aşağıdaki modlar kullanılarak denetlenabilir:

- **Engelle**: Kullanıcıların veya uygulamaların tehlikeli etki alanlarına bağlanması engellenir. Bu etkinliği aynı etkinlikte Microsoft 365 Defender.
- **Denetim**: Kullanıcılar veya uygulamaların tehlikeli etki alanlarına bağlanması engellanmaz. Bununla birlikte, bu etkinliği etkinlik etkinliklerini aynı Microsoft 365 Defender.


Ağ korumasını kapatsanız bile, kullanıcıların veya uygulamaların tehlikeli etki alanlarına bağlanması engellanmaz. E-Microsoft 365 Defender'de ağ Microsoft 365 Defender.

Bunu yapılandırmazsanız, ağ engelleme varsayılan olarak kapalı olur.

Daha fazla bilgi için bkz. [Ağ korumasını etkinleştirme](enable-network-protection.md).

## <a name="investigation-impact"></a>İncelemenin etkisi

Ağ koruması açıkken cihazın zaman çizelgesinde IP adresinin proxy'yi temsil ederken gerçek hedef adresin de proxy'yi temsil eder.

![Cihazın zaman çizelgesinde ağ olaylarının resmi.](images/atp-proxy-investigation.png)

Ağ koruma katmanı tarafından tetiklenen diğer olaylar artık gerçek etki alanı adlarını bir proxy arkasında bile ortaya çıkarabilirsiniz.

Etkinliğin bilgileri:

![Tek bir ağ olayı görüntüsü.](images/atp-proxy-investigation-event.png)

## <a name="hunt-for-connection-events-using-advanced-hunting"></a>Gelişmiş avı kullanarak bağlantı etkinliklerini arama

Tüm yeni bağlantı etkinlikleri, gelişmiş avı da takip etmek için kullanılabilir. Bu olaylar bağlantı olayları olduğu için, bunları DeviceNetworkEvents tablosunda eylem türünün altında `ConnecionSuccess` bulabilirsiniz.

Bu basit sorgunun kullanımı tüm ilgili olayları gösterir:

```console
DeviceNetworkEvents
| where ActionType == "ConnectionSuccess"
| take 10
```

![Gelişmiş arama sorgusu görüntüsü.](images/atp-proxy-investigation-ah.png)

Ayrıca, proxy'nin kendisine yönelik bağlantıyla ilgili olayları filtre de atabilirsiniz.

Ara sunucu bağlantılarını filtrelemek için aşağıdaki sorguyu kullanın:

```console
DeviceNetworkEvents
| where ActionType == "ConnectionSuccess" and RemoteIP != "ProxyIP"
| take 10
```

## <a name="related-topics"></a>İlgili konular

- [GP ile ağ koruması uygulama - ilke CSP](/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection)
