---
title: Uç nokta yanıt API'leri için desteklenen Microsoft Defender
description: Uç nokta API çağrıları için yanıtla ilgili belirli Microsoft Defender hakkında bilgi edinin.
keywords: yanıt api'leri, grafik api'leri, desteklenen api'ler, Actor, alerts, device, kullanıcı, etki alanı, ip, dosya
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: w10
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.openlocfilehash: dcf73669ab780ec23cbd5551039dc8c74f0502ef
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62998205"
---
# <a name="supported-microsoft-defender-for-endpoint-query-apis"></a>Uç nokta sorgu API'leri için desteklenen Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

> [!TIP]
> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-supported-response-apis-abovefoldlink)

Çalıştırabilirsiniz desteklenen yanıtla ilgili API çağrıları ve gerekli istek üst bilgileri ve aramalardan beklenen yanıt gibi ayrıntılar hakkında bilgi edinin.

## <a name="in-this-section"></a>Bu bölümde

<br>

****

|Konu|Açıklama|
|---|---|
|Soruşturma paketini topla|Bir cihazdan araştırma paketi toplamak için bu API'yi çalıştırın.|
|Cihazı yalıt|Bir cihazı ağdan ayırmak için bu API'yi çalıştırın.|
|Tek çözümli cihaz|Cihazı yalıtma tarafından kaldırma.|
|Kod yürütmeyi kısıtlama|Kötü amaçlı işlemleri durdurarak bir saldırıya neden olmak için bu API'yi çalıştırın. Ayrıca, cihazı kilitleyip sonraki olası kötü amaçlı olabilecek programların çalışmasını önebilirsiniz.|
|Kod yürütmeyi durdurma|Güvenliği ihlal edilmiş cihazın düzelt ihlal edilmiş olduğunu doğruladıktan sonra uygulama ilkesi kısıtlamasını tersine çevirmek için bu ayarı çalıştırın.|
|Virüsten koruma taraması çalıştırma|Güvenliği tehlikeye atılmış bir cihazda var olan kötü amaçlı yazılımları belirlemeye ve düzeltmeye yardımcı olmak için virüsten koruma taraması başlatabilirsiniz.|
|Dosyayı durdurma ve karantinaya alın|Işlemleri çalıştırmayı durdurmak, dosyaları karantinaya almak ve kayıt defteri anahtarları gibi kalıcılığı silmek için bu çağrıyı çalıştırın.|
|İstek örneği|Belirli bir cihazdan dosya örneği talep etmek için bu çağrıyı çalıştırın. Dosya cihazdan toplanır ve güvenli bir depolama alanına karşıya yükler.|
|Dosyayı engelle|Kötü amaçlı olabilecek dosyaları veya kötü amaçlı yazılımdan şüphelenilenleri yasaklamanız ile organizasyonda bir saldırının daha fazla yayılmasını önlemek için bu API'yi çalıştırın.|
|Dosyanın engellemesini kaldırma|Dosyaları kullanarak kuruluşta bir dosyanın yürütülmesine Microsoft Defender Virüsten Koruma.|
|Paket SAS URI'lerini al|Araştırma paketini indirmeye izin veren bir URI almak için bu API'yi çalıştırın.|
|MakineAction nesnesini al|MakineAction nesnesini almak için bu API'yi çalıştırın.|
|MachineActions koleksiyonu al|MakineAction koleksiyonunu almak için bunu çalıştırın.|
|FileActions koleksiyonunu al|FileActions koleksiyonunu almak için bu API'yi çalıştırın.|
|FileMachineAction nesnesini al|FileMachineAction nesnesini almak için bu API'yi çalıştırın.|
|FileMachineActions koleksiyonunu al|FileMachineAction koleksiyonunu almak için bu API'yi çalıştırın.|
|
