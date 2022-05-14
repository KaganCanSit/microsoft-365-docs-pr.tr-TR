---
title: Microsoft Defender Virüsten Koruma'de bulut koruması ve örnek gönderme
description: Bulut tabanlı koruma ve Microsoft Defender Virüsten Koruma hakkında bilgi edinin
keywords: Microsoft Defender Virüsten Koruma, yeni nesil teknolojiler, virüsten koruma örnek gönderimi, yeni nesil av, makine öğrenmesi, kötü amaçlı yazılımdan koruma, güvenlik, defender, bulut, bulut tabanlı koruma
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.date: 02/24/2022
ms.collection: M365-security-compliance
ms.openlocfilehash: 08f8e0c861bfd19f11c5b011d0a8db41ce3e73bc
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419956"
---
# <a name="cloud-protection-and-sample-submission-at-microsoft-defender-antivirus"></a>Microsoft Defender Virüsten Koruma'de bulut koruması ve örnek gönderme

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Microsoft Defender Virüsten Koruma kötü amaçlı yazılımları algılamak için birçok akıllı mekanizma kullanır. En güçlü özelliklerden biri, kötü amaçlı yazılımları algılamak ve hızlı analiz gerçekleştirmek için bulutun gücünü uygulama özelliğidir. Bulut koruması ve otomatik örnek gönderimi, yeni ve yeni tehditlere karşı korunmaya yardımcı olmak için Microsoft Defender Virüsten Koruma birlikte çalışır. 

Şüpheli veya kötü amaçlı bir dosya algılanırsa, Microsoft Defender Virüsten Koruma dosyayı engellerken analiz için bulut hizmetine bir örnek gönderilir. Hızla gerçekleşen bir belirleme yapılır yapılmaz, dosya Microsoft Defender Virüsten Koruma tarafından serbest bırakılır veya engellenir. 

Bu makalede, Microsoft Defender Virüsten Koruma'da bulut korumasına ve otomatik örnek göndermeye genel bir bakış sağlanır. Bulut koruması hakkında daha fazla bilgi edinmek için bkz. [Bulut koruması ve Microsoft Defender Virüsten Koruma](cloud-protection-microsoft-defender-antivirus.md).

## <a name="how-cloud-protection-and-sample-submission-work-together"></a>Bulut koruması ve örnek gönderim birlikte nasıl çalışır?

Bulut korumasının örnek gönderimle birlikte nasıl çalıştığını anlamak için Uç Nokta için Defender'ın tehditlere karşı nasıl koruma koruyabileceğini anlamak yararlı olabilir. Microsoft Intelligent Security Graph, geniş bir algılayıcı ağından gelen tehdit verilerini izler. Microsoft, istemciden gelen sinyallere ve Akıllı Güvenlik Graph geniş algılayıcı ve veri ağına göre dosyaları değerlendirebilen bulut tabanlı makine öğrenmesi modellerini katmanlar. Bu yaklaşım, Uç Nokta için Defender'a daha önce görülmemiş birçok tehdidi engelleme olanağı sağlar. 

Aşağıdaki görüntüde bulut korumasının akışı ve Microsoft Defender Virüsten Koruma ile örnek gönderim gösterilir:

:::image type="content" source="images/cloud-protection-flow.png" alt-text="Bulut tabanlı koruma akışı" lightbox="images/cloud-protection-flow.png":::

Microsoft Defender Virüsten Koruma ve bulut koruması, aşağıdaki yöntemleri kullanarak ilk bakışta en yeni, hiç görülmemiş tehditleri otomatik olarak engeller:

1. Yeni ve bilinmeyen kötü amaçlı yazılımları engelleyen basit istemci tabanlı makine öğrenmesi modelleri.

2. Yerel davranış analizi, dosya tabanlı ve dosyasız saldırıları durdurma.

3. Genel ve buluşsal teknikler aracılığıyla yaygın kötü amaçlı yazılımları algılayan yüksek duyarlıklı virüsten koruma.

4. Uç noktada çalışan Microsoft Defender Virüsten Koruma şüpheli bir dosyanın amacını doğrulamak için daha fazla zekaya ihtiyaç duyduğu durumlar için gelişmiş bulut tabanlı koruma sağlanır.

   1. Microsoft Defender Virüsten Koruma net bir belirleme yapamazsa, dosya meta verileri bulut koruma hizmetine gönderilir. Bulut koruma hizmeti genellikle milisaniye içinde meta verileri temel alarak dosyanın kötü amaçlı olup olmadığını belirleyebilir.  

      - Dosya meta verilerinin bulut sorgusu davranış, web işareti veya net bir kararın belirlenmediği diğer özelliklerin bir sonucu olabilir.
      - Kötü amaçlı yazılım kararına ulaşma veya tehdit oluşturmama hedefiyle küçük bir meta veri yükü gönderilir. Meta veriler kişisel bilgileri (PII) içermez. Dosya adları gibi bilgiler karma olarak sağlanır.
      - Zaman uyumlu veya zaman uyumsuz olabilir. Zaman uyumlu olarak, bulut bir karar işleyene kadar dosya açılmaz. Zaman uyumsuz olarak, bulut koruması analizini gerçekleştirirken dosya açılır.
      - Meta veriler PE öznitelikleri, statik dosya öznitelikleri, dinamik ve bağlamsal öznitelikler ve daha fazlasını içerebilir (bkz. [Bulut koruma hizmetine gönderilen meta veriler örnekleri](#examples-of-metadata-sent-to-the-cloud-protection-service)).

   2. Meta verileri inceledikten sonra, Microsoft Defender Virüsten Koruma bulut koruması kesin bir karara ulaşamazsa, daha fazla inceleme için dosyanın bir örneğini isteyebilir. Bu istek, örnek gönderim için ayarlar yapılandırmasını yerine getirmektedir:

      1. **Güvenli örnekleri otomatik olarak gönderme** (varsayılan)
         - Kasa örneklerin yaygın olarak pii verileri içermediği kabul edilir: .bat, .scr, .dll, .exe.
         - Dosya büyük olasılıkla PII içeriyorsa, kullanıcı dosya örneği gönderimine izin vermek için bir istek alır.
         - Bu seçenek Windows, macOS ve Linux'ta varsayılan seçenektir.

      2. **Her Zaman İste**
         - Yapılandırılırsa, dosya göndermeden önce kullanıcıdan her zaman onay istenir
         - Bu ayar macOS bulut korumasında kullanılamaz

      3. **Tüm örnekleri otomatik olarak gönderme**
         - Yapılandırılırsa, tüm örnekler otomatik olarak gönderilir
         - Örnek gönderimin Word belgelerine eklenmiş makrolar içermesini istiyorsanız, "Tüm örnekleri otomatik olarak gönder" seçeneğini belirlemeniz gerekir
         - Bu ayar macOS bulut korumasında kullanılamaz

      4. **Gönderme**
         - Dosya örneği analizine göre "ilk bakışta engelle" ifadesini önler
         - "Gönderme", macOS ilkesindeki "Devre dışı" ayarıyla eşdeğerdir
         - Örnek gönderim devre dışı bırakıldığında bile algılamalar için meta veriler gönderilir

   3. Meta veriler ve/veya dosyalar bulut korumasına gönderildikten sonra, bir karara ulaşmak için **örnekleri**, **patlamayı** veya **büyük veri analizi** makine öğrenmesi modellerini kullanabilirsiniz. Bulut tabanlı korumayı kapatmak, analizi yalnızca istemcinin yerel makine öğrenmesi modelleri ve benzer işlevler aracılığıyla sağlayabilecekleri ile sınırlandıracaktır.

> [!IMPORTANT]
> [İlk bakışta engelle (BAFS),](configure-block-at-first-sight-microsoft-defender-antivirus.md) bir dosyanın veya işlemin güvenli olup olmadığını belirlemek için patlama ve analiz sağlar. BAFS, bir karara varılana kadar dosyanın açılmasını bir süre geciktirebilir. Örnek gönderimi devre dışı bırakırsanız BAFS de devre dışı bırakılır ve dosya analizi yalnızca meta veriyle sınırlıdır. Örnek gönderimi ve BAFS'yi etkin tutmanızı öneririz. Daha fazla bilgi edinmek için bkz. ["İlk bakışta engelle" nedir?](configure-block-at-first-sight-microsoft-defender-antivirus.md#what-is-block-at-first-sight)

## <a name="cloud-protection-levels"></a>Bulut koruma düzeyleri

Bulut koruması varsayılan olarak Microsoft Defender Virüsten Koruma etkindir. Kuruluşunuz için koruma düzeyini yapılandırabilmenize rağmen bulut korumasını etkin tutmanızı öneririz. Bkz. [Microsoft Defender Virüsten Koruma için bulut tabanlı koruma düzeyini belirtme](specify-cloud-protection-level-microsoft-defender-antivirus.md).

## <a name="sample-submission-settings"></a>Örnek gönderim ayarları

Bulut koruma düzeyinizi yapılandırmanın yanı sıra örnek gönderim ayarlarınızı da yapılandırabilirsiniz. Çeşitli seçenekler arasından seçim yapabilirsiniz:

- **Güvenli örnekleri otomatik olarak gönderme**  (varsayılan davranış)
- **Tüm örnekleri otomatik olarak gönderme**  
- **Örnek gönderme**  

Intune, Configuration Manager, GPO veya PowerShell kullanan yapılandırma seçenekleri hakkında bilgi için bkz[. Microsoft Defender Virüsten Koruma'de bulut korumasını açma](enable-cloud-protection-microsoft-defender-antivirus.md).

## <a name="examples-of-metadata-sent-to-the-cloud-protection-service"></a>Bulut koruma hizmetine gönderilen meta veri örnekleri

:::image type="content" source="images/cloud-protection-metadata-sample.png" alt-text="Microsoft Defender Virüsten Koruma portalında bulut korumasına gönderilen meta veri örnekleri" lightbox="images/cloud-protection-metadata-sample.png":::

Aşağıdaki tabloda bulut koruması tarafından analiz için gönderilen meta veri örnekleri listeilmektedir:

| Tür | Öznitelik |
|:---|:---|
| Makine öznitelikleri | `OS version` <br/> `Processor` <br/> `Security settings` |
| Dinamik ve bağlamsal öznitelikler | **İşlem ve yükleme** <br/> `ProcessName` <br/> `ParentProcess` <br/> `TriggeringSignature` <br/> `TriggeringFile` <br/> `Download IP and url` <br/> `HashedFullPath` <br/> `Vpath` <br/> `RealPath` <br/> `Parent/child relationships` <br/><br/>**Davranış** <br/> `Connection IPs` <br/> `System changes` <br/> `API calls` <br/> `Process injection` <br/><br/>**Yerel ayar** <br/> `Locale setting` <br/> `Geographical location` |
| Statik dosya öznitelikleri | **Kısmi ve tam karmalar** <br/> `ClusterHash` <br/> `Crc16` <br/> `Ctph` <br/> `ExtendedKcrcs` <br/> `ImpHash` <br/> `Kcrc3n` <br/> `Lshash` <br/> `LsHashs` <br/> `PartialCrc1` <br/> `PartialCrc2` <br/> `PartialCrc3` <br/> `Sha1` <br/> `Sha256` <br/><br/>**Dosya özellikleri** <br/>`FileName` <br/> `FileSize` <br/><br/> **İmzalayan bilgileri** <br/> `AuthentiCodeHash` <br/> `Issuer` <br/> `IssuerHash` <br/> `Publisher` <br/> `Signer` <br/> `SignerHash` |

## <a name="samples-are-treated-as-customer-data"></a>Örnekler müşteri verileri olarak değerlendirilir

Örnek gönderimlerde ne olduğunu merak ediyorsanız Uç Nokta için Defender tüm dosya örneklerini müşteri verileri olarak kabul eder. Microsoft, Uç Nokta için Defender'a eklerken kuruluşunuzun seçtiği coğrafi ve veri saklama seçimlerini yerine getirmektedir. 

Buna ek olarak, Uç Nokta için Defender birden çok uyumluluk sertifikası aldı ve gelişmiş bir uyumluluk denetimleri kümesine sürekli bağlı kalmayı gösterir:

- ISO 27001
- ISO 27018
- SOC I, II, III
- PCI

Daha fazla bilgi için aşağıdaki kaynaklara bakın:

- [Azure Uyumluluk Teklifleri](/azure/storage/common/storage-compliance-offerings) 
- [Hizmet Güveni Portalı](https://servicetrust.microsoft.com)
- [veri depolama ve gizliliği Uç Nokta için Microsoft Defender](data-storage-privacy.md#data-storage-location)

## <a name="other-file-sample-submission-scenarios"></a>Diğer dosya örneği gönderme senaryoları

Uç Nokta için Defender'ın Microsoft Defender Virüsten Koruma bulut korumasıyla ilgili olmayan bir dosya örneği isteyebileceği iki senaryo daha vardır. Bu senaryolar aşağıdaki tabloda açıklanmıştır:

| Senaryo | Açıklama |
|:---|:---|
|Microsoft 365 Defender portalında el ile dosya örneği koleksiyonu | Uç Nokta için Defender'a cihaz eklerken[, uç noktada algılama ve yanıtlama (EDR)](overview-endpoint-detection-response.md) ayarlarını yapılandırabilirsiniz. Örneğin, cihazdan örnek koleksiyonları etkinleştirmeye yönelik bir ayar vardır ve bu ayar bu makalede açıklanan örnek gönderim ayarlarıyla kolayca karıştırılabilir. <br/><br/>EDR ayarı, Microsoft 365 Defender portalı üzerinden istendiğinde cihazlardan dosya örneği toplamayı denetler ve önceden oluşturulmuş rollere ve izinlere tabidir. Bu ayar, Microsoft 365 Defender portalında ayrıntılı analiz gibi özellikler için uç noktadan dosya toplamaya izin verebilir veya bunları engelleyebilir. Bu ayar yapılandırılmamışsa, varsayılan değer örnek koleksiyonu etkinleştirmektir. <br/><br/>Uç Nokta için Defender yapılandırma ayarları hakkında bilgi edinin, bkz. [Uç Nokta için Defender'da Windows 10 cihazlar için ekleme araçları ve yöntemleri](configure-endpoints.md) |
| Otomatik araştırma ve yanıt içeriği analizi | Cihazlarda [otomatik araştırma çalıştırıldığında](automated-investigations.md) (bir uyarıya yanıt olarak otomatik olarak çalışacak veya el ile çalıştırılacak şekilde yapılandırıldığında), şüpheli olarak tanımlanan dosyalar daha fazla inceleme için uç noktalardan toplanabilir. Gerekirse, otomatik araştırmalara yönelik dosya içeriği analizi özelliği Microsoft 365 Defender portalında devre dışı bırakılabilir. <br/><br/> Dosya uzantısı adları, otomatik araştırma sırasında otomatik olarak gönderilecek diğer dosya türleri için uzantı eklemek veya kaldırmak için de değiştirilebilir. <br/><br/> Daha fazla bilgi edinmek için bkz. [Otomasyon dosyası yüklemelerini yönetme](manage-automation-file-uploads.md). |

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)

## <a name="see-also"></a>Ayrıca bkz.

[Yeni nesil korumaya genel bakış](next-generation-protection.md)

[Microsoft Defender Virüsten Koruma algılamaları için düzeltmeyi yapılandırın.](configure-remediation-microsoft-defender-antivirus.md)
