---
title: Uç Nokta için Pilot Microsoft Defender
description: Pilot grubu doğrulama ve özellikleri çalıştırma da dahil olmak üzere, Endpoint (MDE) için Microsoft Defender için bir pilot çalıştırmayı öğrenin.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: v-jweston
author: jweston-1
ms.date: 07/09/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 4fff094b06dfa265f9fc44c568216582083ce1d9
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2022
ms.locfileid: "63755464"
---
# <a name="pilot-microsoft-defender-for-endpoint"></a>Uç Nokta için Pilot Microsoft Defender

Bu makale, Uç Nokta için Microsoft Defender'da pilot çalıştırma sürecinde size yol sağlar. 

Uç Nokta için Microsoft Defender'da pilot ayarlama ve yapılandırma için aşağıdaki adımları kullanın. 

:::image type="content" source="../../media/defender/m365-defender-endpoint-pilot-steps.png" alt-text="Microsoft Defender değerlendirme ortamına Identity için Microsoft Defender ekleme adımları" lightbox="../../media/defender/m365-defender-endpoint-pilot-steps.png":::

- Adım 1. Pilot grubu doğrulama
- Adım 2. Özellikleri deneyin

Uç Nokta için Microsoft Defender'ı pilot olarak sunarken, tüm kuruluşu eklemeden önce hizmete birkaç cihaz eklemeyi seçebilirsiniz.  

Ardından saldırı benzetimlerini çalıştırma ve Uç nokta için Defender'ın kötü amaçlı etkinlikleri nasıl ortaya çıkararak etkili bir yanıt yürütmene olanak verdiği gibi özellikleri deneyebilirsiniz. 

## <a name="step-1-verify-pilot-group"></a>Adım 1. Pilot grubu doğrulama
Değerlendirmeyi etkinleştir bölümünde açıklanan ekleme adımlarını tamamladıktan sonra[](eval-defender-endpoint-enable-eval.md), cihaz envanteri listesinde yaklaşık bir saat sonra cihazları görmeniz gerekir. 

Ekli cihazlarınızı gördüğünüzde, özellikleri deniyorum. 

## <a name="step-2-try-out-capabilities"></a>Adım 2. Özellikleri deneyin
Artık bazı cihazları eklemeyi tamamladıktan ve hizmete rapor yaptıklarına göre, hemen hazır bulunan güçlü özellikleri denerek ürünü tanımaya hazır olun.

Pilot çalışma sırasında, karmaşık yapılandırma adımlarını atmadan ürünü çalışırken görmek için bazı özellikleri kolayca çalışmaya başlatabilirsiniz.

Panoları kontrol ederek başlayalım.

### <a name="view-the-device-inventory"></a>Cihaz envanterini görüntüleme
Cihaz envanteri, ağ ağınız için uç noktaların, ağ cihazlarının ve IoT cihazlarının listesini göreceğiniz yerdir. Ağ ağınız için yalnızca cihazları görüntülemenizi sağlamakla aynı zamanda etki alanı, risk düzeyi, işletim sistemi platformu ve en çok risk altında olan cihazların kolayca tanımlanmasını sağlayacak diğer ayrıntılar gibi bu cihazlar hakkında derinlemesine bilgi sağlar.

### <a name="view-the-threat-and-vulnerability-management-dashboard"></a>Tehdit ve Güvenlik güvenlik açığı yönetimi görüntüleme 
Tehdit ve güvenlik açığı yönetimi, kuruluşa en acil ve en yüksek riski veren zayıf noktaların üzerine odaklanmanıza yardımcı olur. Panodan, kuruluşun pozlama puanının üst düzey bir görünümünü, Cihazlar için Microsoft Güvenli Puanı, cihaz açığa çıkarma dağılımını, en iyi güvenlik önerilerini, en korumasız yazılımları, en iyi düzeltme etkinliklerini ve en iyi şekilde açığa çıkaran cihaz verilerini elde edin. 

### <a name="run-a-simulation"></a>Benzetim çalıştırma
Uç Nokta için Microsoft Defender, pilot [cihazlarında çalıştırabilirsiniz "Do It Yourself"](https://securitycenter.windows.com/tutorials) saldırı senaryolarıyla birlikte gelir.  Her belgede işletim sistemi ve uygulama gereksinimlerinin yanı sıra saldırı senaryosuna özgü ayrıntılı yönergeler de yer almaktadır. Bu betikler güvenli, belgelenmiş ve kullanımı kolaydır. Bu senaryolar, Uç Nokta için Defender özelliklerini yansıtacak ve araştırma deneyimi boyunca size yol sunar.

Sağlanan benzetimleri çalıştırmak için, en az bir yerleşik [cihaza ihtiyacınız vardır](../defender-endpoint/onboard-configure.md).

1.  > **YardımSimulations & içinde**, benzetim yapmak istediğiniz mevcut saldırı senaryolarını seçin:

   - **Senaryo 1: Belge geri dönmez- sosyal** olarak mühendislik yapılan bir belge teslimini benzetimler. Belge, saldırganlara denetim veren özel olarak hazırlanmış bir arka kapı başlatıyor.

   - **Senaryo 2:** Dosyasız saldırıdaki PowerShell betiği, PowerShell'e dayanan dosyasız bir saldırının benzetimini yaptı, saldırı yüzeyini azaltmayı ve kötü amaçlı bellek etkinliğini algıla ile ilgili cihaz öğrenmeyi gösterir.

   - **Senaryo 3: Otomatik olay** yanıtı - Olay yanıt kapasitenizi ölçeklendirmek için ihlal yapıtlarını otomatik olarak uyaran otomatik soruşturmayı tetikler.

2. Seçtiğiniz senaryoyla birlikte verilen ilgili adım adım belgeyi indirin ve okuyun.

3. Benzetim dosyasını indirin veya öğreticilerde **YardımSimulations'a** >  giderek benzetim & kopyalayın. Dosyayı veya betiği test cihazına indirmeyi seçebilirsiniz, ancak bu zorunlu değildir.

4. Benzetim dosyasını veya betiği, adım adım belgede anlatımlı olarak test cihazında çalıştırın.

> [!NOTE]
> Benzetim dosyaları veya betikler saldırı etkinliğini taklit ediyor ancak aslında bu, test cihazına zarar vermeyecek veya tehlikeye atmayacak.

## <a name="next-steps"></a>Sonraki adımlar
[Bulut Uygulamaları için Microsoft Defender'ı Değerlendirme](eval-defender-mcas-overview.md)

Uç Nokta için [Microsoft Defender'ı Değerlendir'e genel bakış](eval-defender-endpoint-overview.md)

Değerlendirme ve pilot uygulama için [genel bakış Microsoft 365 Defender](eval-overview.md)
