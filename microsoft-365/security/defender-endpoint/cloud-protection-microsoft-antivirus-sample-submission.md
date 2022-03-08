---
title: E-postada bulut koruması ve örnek Microsoft Defender Virüsten Koruma
description: Buluta teslim edilen koruma ve teslim Microsoft Defender Virüsten Koruma
keywords: Microsoft Defender Virüsten Koruma, yeni nesil teknolojiler, virüsten koruma örnek gönderimi, yeni nesil av, makine öğrenimi, kötü amaçlı yazılımlardan koruma, güvenlik, defender, bulut, buluta teslim edilen koruma
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
ms.openlocfilehash: 9df9c387f24671d6790d9219590eeac490f2f1aa
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328141"
---
# <a name="cloud-protection-and-sample-submission-in-microsoft-defender-antivirus"></a>E-postada bulut koruması ve örnek Microsoft Defender Virüsten Koruma

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

Microsoft Defender Virüsten Koruma kötü amaçlı yazılımları algılamak için birçok akıllı mekanizma kullanır. En güçlü özelliklerden biri, kötü amaçlı yazılımları tespit etmek ve hızlı çözümleme yapmak için bulutun gücünü uygulayabilme özelliğidir. Bulut koruması ve otomatik örnek gönderim, yeni ve ortaya çıkan tehditlere Microsoft Defender Virüsten Koruma için bulut koruması ve otomatik örnek gönderimle birlikte çalışır. 

Şüpheli veya kötü amaçlı bir dosya algılanırsa, çözümleme için bulut hizmetine bir örnek gönderilir ve Microsoft Defender Virüsten Koruma engeller. Hızlı bir şekilde yapılan bir belirleme belirlemesi yapılır olmaz dosya yayınlanacak veya bir Microsoft Defender Virüsten Koruma. 

Bu makalede, Çalışma Kitaplarında bulut koruması ve otomatik örnek gönderim Microsoft Defender Virüsten Koruma. Bulut koruması hakkında daha fazla bilgi edinmek için bkz[. Bulut koruması ve Microsoft Defender Virüsten Koruma](cloud-protection-microsoft-defender-antivirus.md).

## <a name="how-cloud-protection-and-sample-submission-work-together"></a>Bulut koruması ve örnek gönderim birlikte nasıl çalışır?

Bulut korumasının örnek gönderimle birlikte nasıl çalıştığını anlamak için, Uç Nokta için Defender'ın tehditlere karşı nasıl korunacı olduğunu anlamak yararlı olabilir. Microsoft Akıllı Güvenlik Graph muazzam bir algılayıcı ağın verilerini tehdit ediyor. Microsoft, istemciden gelen sinyallere ve Akıllı Güvenlik 2013'te muazzam algılayıcılar ve veri ağına dayalı olarak dosyaları değerlendiren bulut tabanlı makine öğrenme modellerini Graph. Bu yaklaşım, Uç Nokta için Defender'a önceden olmayan birçok tehdityi engelleme olanağı verir. 

Aşağıdaki resimde, bulut korumasının akışı ve aşağıdaki adımları takip eden örnek Microsoft Defender Virüsten Koruma:

:::image type="content" source="images/cloud-protection-flow.png" alt-text="Bulut teslimi koruma akışı":::

Microsoft Defender Virüsten Koruma ve bulut koruması, aşağıdaki yöntemleri kullanarak en yeni, önceden asla görülmeyen tehditlerin çoğunu ilk görüşte otomatik olarak engelleyebilir:

1. Yeni ve bilinmeyen kötü amaçlı yazılımları engelleyen basit istemci tabanlı makine öğrenme modelleri.

2. Dosya tabanlı ve dosya az saldırılarını durduran yerel davranış çözümlemesi.

3. Yüksek duyarlıklı virüsten koruma, genel ve heistist tekniklerle yaygın kötü amaçlı yazılımları algılama.

4. Şüpheli bir dosyanın amacını doğrulamak için Microsoft Defender Virüsten Koruma uç noktada daha fazla zekaya ihtiyaç duyuyorsanız, gelişmiş bulut tabanlı koruma sağlanır.

   1. Aşağıdaki olay Microsoft Defender Virüsten Koruma belirlemeyi açıkça yapmada, dosya meta verileri bulut koruma hizmetine gönderilir. Bulut koruma hizmeti, çoğu zaman meta verileri temel alarak dosyanın kötü amaçlı olup olmadığını belirler.  

      - Dosya meta verilerini bulut sorgusu davranışın, web'in işaretinin veya net bir karar alınan kararların belirlen düzenlemenin başka özelliklerinin sonucu olabilir.
      - Kötü amaçlı yazılım kararına ulaşmak veya bir tehdit değil, küçük bir meta veri yükü gönderilir. Meta veriler, kişisel olarak tanınmayı sağlayacak bilgileri (PII) içermemektedir. Dosya adı gibi bilgiler karma olur.
      - Zaman uyumlu veya zaman uyumsuz olabilir. Zaman uyumlu olması için, bulut karara varana kadar dosya açılmaz. Zaman uyumsuz ise bulut koruması çözümlemesini yaparken dosya açılır.
      - Meta veriler PE özniteliklerini, statik dosya özniteliklerini, dinamik ve bağlamsal öznitelikleri ve daha fazlasını içerebilir (bkz. Bulut koruma hizmetine gönderilen meta [veri örnekleri](#examples-of-metadata-sent-to-the-cloud-protection-service)).

   2. Meta verileri inceledikten sonra, Microsoft Defender Virüsten Koruma bulut koruması kesin bir karara ulaşamazsa, ek denetim için dosyanın bir örneğini talep olabilir. Bu istek, örnek gönderim için ayarlar yapılandırmasına uyar:

      1. **Güvenli örnekleri otomatik olarak gönderme** (varsayılan)
         - Kasa, yaygın olarak PII verileri içerme kabul edilen örneklerdir: .bat, .scr, .dll, .exe.
         - Dosyanın PII içerme olasılığı varsa, kullanıcıya dosya örnek gönderimi için izin verme isteği olur.
         - Bu seçenek Windows, macOS ve Linux'ta varsayılandır.

      2. **Her Zaman Sor**
         - Yapılandırıldığında, dosya göndermeden önce kullanıcıdan her zaman izin istenir
         - Bu ayar macOS bulut koruması için kullanılamaz

      3. **Tüm örnekleri otomatik olarak gönderme**
         - Yapılandırılırsa, tüm örnekler otomatik olarak gönderilir
         - Örnek gönderimin Word belgelerine eklenmiş makrolar içermesi için, "Tüm örnekleri otomatik olarak gönder"
         - Bu ayar macOS bulut koruması için kullanılamaz

      4. **Gönderme**
         - Dosya örnek çözümlemesi temel alınarak "ilk görüşte blok" formüllerini önler
         - "Do not send", macOS ilkesinde "Devre Dışı" ayarıyla eşdeğerdir
         - Örnek gönderme devre dışı bırak olsa bile algılamalar için meta veriler gönderilir

   3. Meta veriler ve/veya dosyalar bulut korumasına gönderildikten sonra, karara var etmek için örnekler,  **detonasyonu** veya büyük veri çözümleme makinesi öğrenme modellerini kullanabilirsiniz. Buluta teslim edilen korumayı kapatarak çözümlemeyi yalnızca istemcinin yerel makine öğrenme modelleri ve benzer işlevler aracılığıyla sağ neyi sağlay ulaşacaklarını sınırlatır.

> [!IMPORTANT]
> [İlk görüşte engelle (BAFS),](configure-block-at-first-sight-microsoft-defender-antivirus.md) dosya veya sürecin güvenli olup olmadığını belirlemek içintonasyonu ve çözümlemeyi sağlar. BAFS, bir karara varana kadar dosyanın açılmasını anlık olarak geciktirir. Örnek gönderimi devre dışı bıraksanız, BAFS de devre dışı bırakılır ve dosya çözümleme yalnızca meta veriyle sınırlıdır. Örnek gönderimi ve BAFS'yi etkin tutmanız önerilir. Daha fazla bilgi edinmek için bkz [. "İlk görüşte blok" nedir?](configure-block-at-first-sight-microsoft-defender-antivirus.md#what-is-block-at-first-sight)

## <a name="cloud-protection-levels"></a>Bulut koruma düzeyleri

Bulut koruması bu dosyada varsayılan olarak Microsoft Defender Virüsten Koruma. Kurum için koruma düzeyini yapılandırabilirsiniz, ancak bulut korumasını etkin tutmanızı öneririz. Daha [fazla bilgi için bkz. Bulut teslimi koruma Microsoft Defender Virüsten Koruma](specify-cloud-protection-level-microsoft-defender-antivirus.md).

## <a name="sample-submission-settings"></a>Örnek gönderme ayarları

Bulut koruma düzeyinizi yapılandırmaya ek olarak, örnek gönderme ayarlarınızı da yapılandırabilirsiniz. Birkaç seçenekten birini seçebilirsiniz:

- **Güvenli örnekleri otomatik olarak gönderme**  (varsayılan davranış)
- **Tüm örnekleri otomatik olarak gönderme**  
- **Örnek göndermeyin**  

Intune, Configuration Manager, GPO veya PowerShell kullanarak yapılandırma seçenekleri hakkında bilgi için bkz. Windows'da bulut [korumasını Microsoft Defender Virüsten Koruma](enable-cloud-protection-microsoft-defender-antivirus.md).

## <a name="examples-of-metadata-sent-to-the-cloud-protection-service"></a>Bulut koruma hizmetine gönderilen meta veri örnekleri

:::image type="content" source="images/cloud-protection-metadata-sample.png" alt-text="Microsoft Defender Virüsten Koruma'ta bulut korumasına gönderilen meta veri örneklerini gösteren Microsoft Defender Virüsten Koruma":::

Aşağıdaki tabloda, bulut koruması tarafından çözümleme için gönderilen meta veri örnekleri listelemektedir:

| Tür | Öznitelik |
|:---|:---|
| Makine öznitelikleri | `OS version` <br/> `Processor` <br/> `Security settings` |
| Dinamik ve bağlamsal öznitelikler | **İşlem ve yükleme** <br/> `ProcessName` <br/> `ParentProcess` <br/> `TriggeringSignature` <br/> `TriggeringFile` <br/> `Download IP and url` <br/> `HashedFullPath` <br/> `Vpath` <br/> `RealPath` <br/> `Parent/child relationships` <br/><br/>**Davranış** <br/> `Connection IPs` <br/> `System changes` <br/> `API calls` <br/> `Process injection` <br/><br/>**Locale** <br/> `Locale setting` <br/> `Geographical location` |
| Statik dosya öznitelikleri | **Kısmi ve tam karmalar** <br/> `ClusterHash` <br/> `Crc16` <br/> `Ctph` <br/> `ExtendedKcrcs` <br/> `ImpHash` <br/> `Kcrc3n` <br/> `Lshash` <br/> `LsHashs` <br/> `PartialCrc1` <br/> `PartialCrc2` <br/> `PartialCrc3` <br/> `Sha1` <br/> `Sha256` <br/><br/>**Dosya özellikleri** <br/>`FileName` <br/> `FileSize` <br/><br/> **İmzacı bilgileri** <br/> `AuthentiCodeHash` <br/> `Issuer` <br/> `IssuerHash` <br/> `Publisher` <br/> `Signer` <br/> `SignerHash` |

## <a name="samples-are-treated-as-customer-data"></a>Örnekler müşteri verileri olarak kabul edilir

Örnek gönderilerde neler olduğunu merak ediyorsanız, Uç Nokta için Defender tüm dosya örneklerini müşteri verileri olarak kabul eder. Microsoft, Uç Nokta için Defender'a ekli olduğunda, kuruluşun seçtiğiniz coğrafi ve veri bekletme seçeneklerine de uygun. 

Ayrıca, Uç Nokta için Defender birden çok uyumluluk sertifikası aldı ve gelişmiş bir uyumluluk denetimleri kümesine bağlı olmaya devam ediyor:

- ISO 27001
- ISO 27018
- SOC I, II, III
- ve PCI

Daha fazla bilgi için aşağıdaki kaynaklara bakın:

- [Azure Uyumluluk Teklifleri](/azure/storage/common/storage-compliance-offerings) 
- [Hizmet Güveni Portalı](https://servicetrust.microsoft.com)
- [Uç nokta veri depolaması ve gizliliği için Microsoft Defender](data-storage-privacy.md#data-storage-location)

## <a name="other-file-sample-submission-scenarios"></a>Diğer dosya örnek gönderme senaryoları

Uç Nokta için Defender'ın, diğer senaryolarda bulut korumasıyla ilgili bir dosya örneği isteğinde bulun olabileceği iki Microsoft Defender Virüsten Koruma. Bu senaryolar aşağıdaki tabloda açıklanmıştır:

| Senaryo | Açıklama |
|:---|:---|
|Microsoft 365 Defender portalında el ile dosya Microsoft 365 Defender koleksiyonu | Uç nokta için Defender'a cihaz eklemeye devam etmek için Cihaz Ayarları'uç noktada algılama ve yanıtlama [(EDR)](overview-endpoint-detection-response.md). Örneğin, cihazdan örnek koleksiyonları etkinleştirmeye olanak sağlayan bir ayar vardır ve bu ayar bu makalede açıklanan örnek gönderme ayarlarıyla kolayca karıştırılabiliyor. <br/><br/>Bu EDR, mobil cihaz portalında istenerek cihazlardan dosya örnek koleksiyonunu kontrol eder Microsoft 365 Defender ve zaten var olan rollere ve izinlere konur. Bu ayar, dosya portalında derin çözümleme gibi özellikler için dosya koleksiyonuna uç noktadan izin Microsoft 365 Defender olabilir. Bu ayar yapılandırılmazsa, varsayılan ayar örnek koleksiyonu etkinleştirmektir. <br/><br/>Uç nokta yapılandırma ayarları için Defender hakkında bilgi edinmek için bkz. Uç nokta için [Defender'da Windows 10 cihazlar için ekleme araçları ve yöntemleri](configure-endpoints.md) |
| Otomatik araştırma ve yanıt içeriği çözümleme | Cihazlarda [otomatik soruşturmalar](automated-investigations.md) çalıştırıldığında (uyarıya yanıt olarak otomatik olarak çalıştıracak şekilde yapılandırıldığında veya el ile çalıştırıldığında), şüpheli olarak tanımlanan dosyalar daha fazla inceleme için uç noktalardan toplanabilir. Gerekirse, otomatik soruşturmalar için dosya içeriği çözümleme özelliği portalda Microsoft 365 Defender devre dışı bırakılabilir. <br/><br/> Dosya uzantısı adları, otomatik bir soruşturma sırasında otomatik olarak gönderilen diğer dosya türlerinin uzantılarını eklemek veya kaldırmak için de değiştirilebilir. <br/><br/> Daha fazla bilgi edinmek için bkz [. Otomasyon dosyası yüklemelerini yönetme](manage-automation-file-uploads.md). |

## <a name="see-also"></a>Ayrıca bkz.

[Yeni nesil korumaya genel bakış](next-generation-protection.md)

[Düzeltme algılamaları için Microsoft Defender Virüsten Koruma yapılandırma.](configure-remediation-microsoft-defender-antivirus.md)
