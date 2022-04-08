---
title: Saldırı yüzeyini azaltma (ASR) kuralları dağıtımına genel bakış
description: Saldırı yüzeyi azaltma (ASR) kurallarını dağıtma hakkında genel bakış ve önkoşul yönergeleri sağlar.
keywords: Saldırı yüzeyi azaltma kuralları dağıtımı, ASR dağıtımı, ASR kurallarını etkinleştirme, ASR'yi yapılandırma, konak yetkisiz erişim önleme sistemi, koruma kuralları, açıktan yararlanma önleme kuralları, kötüye kullanıma karşı koruma kuralları, kötüye kullanma kuralları, bulaşma önleme kuralları, Uç Nokta için Microsoft Defender, ASR kurallarını yapılandırma
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection:
- m365solution-scenario
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: 8743d13939e73e25cefd08724d9a2f8d5a7fa410
ms.sourcegitcommit: 5c9137f98e688ab23c144e75687399e390bb2601
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/07/2022
ms.locfileid: "64705548"
---
# <a name="attack-surface-reduction-asr-rules-deployment-overview"></a>Saldırı yüzeyini azaltma (ASR) kuralları dağıtımına genel bakış

Saldırı yüzeyleri, kuruluşunuzun siber tehditlere ve saldırılara karşı savunmasız olduğu tüm yerlerdir. Kuruluşunuzun saldırı yüzeyleri, bir saldırganın kuruluşunuzun cihazlarını veya ağlarını tehlikeye atabileceği tüm yerleri içerir. Saldırı yüzeyinizi azaltmak, kuruluşunuzun cihazlarını ve ağını korumak anlamına gelir ve bu da saldırganlara saldırı için daha az yol bırakır. Uç Nokta için Microsoft Defender bulunan birçok güvenlik özelliğinden biri olan saldırı yüzeyi azaltma (ASR) kurallarının yapılandırılması yardımcı olabilir.

ASR kuralları aşağıdakiler gibi belirli yazılım davranışlarını hedefler:

- Dosyaları indirmeye veya çalıştırmaya çalışan yürütülebilir dosyaları ve betikleri başlatma
- Karartılmış veya başka bir şekilde şüpheli betikleri çalıştırma
- Uygulamaların genellikle normal gündelik çalışma sırasında gerçekleşmeyen davranışlar

Farklı saldırı yüzeylerini azaltarak saldırıların gerçekleşmesini önlemeye yardımcı olabilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

İlk hazırlığınız sırasında, yerleştireceğimiz sistemlerin özelliklerini anlamanız çok önemlidir. Özellikleri anlamak, kuruluşunuzu korumak için hangi ASR kurallarının en önemli olduğunu belirlemenize yardımcı olur. Ayrıca, ASR dağıtımınızın hazırlanmasında ilgilenmeniz gereken çeşitli önkoşullar vardır.

>[!IMPORTANT]
>Bu kılavuz, ASR kurallarını yapılandırmaya karar vermenize yardımcı olacak görüntüler ve örnekler sağlar; bu görüntüler ve örnekler ortamınız için en iyi yapılandırma seçeneklerini yansıtmayabilir.

Başlamadan önce, temel bilgiler için [Saldırı yüzeyi azaltmaya genel bakış](overview-attack-surface-reduction.md) ve [Saldırı yüzeyi azaltma kurallarını kaldırma - Bölüm 1'i](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420) gözden geçirin. Kapsam alanlarını ve olası etkiyi anlamak için, mevcut ASR kuralları kümesini tanıyın; [bkz. Saldırı yüzeyi azaltma kuralları başvurusu](attack-surface-reduction-rules-reference.md).  ASR kural kümesi hakkında bilgi sahibi olurken kural başına GUID eşlemelerini not edin; bkz. [ASR kuralları ve GUID matrisi](attack-surface-reduction-rules-reference.md#asr-rules-and-guids-matrix).

ASR kuralları, Uç Nokta için Microsoft Defender içindeki saldırı yüzeyi azaltma özelliklerinin yalnızca bir özelliğidir. Bu belge, insan tarafından çalıştırılan fidye yazılımı ve diğer tehditler gibi gelişmiş tehditleri durdurmak için ASR kurallarını etkili bir şekilde dağıtma hakkında daha ayrıntılı bilgi sağlayacaktır.  

### <a name="rules-by-category"></a>Kategoriye göre kurallar

[Kötü amaçlı yazılım bulaşmasını önlemek için saldırı yüzeyi azaltma kurallarını kullanma](attack-surface-reduction.md) bölümünde açıklandığı gibi, MDE'de kuruluşunuzu korumak için etkinleştirebileceğiniz birden çok saldırı yüzeyi azaltma kuralı vardır. Kategorilere göre ayrılmış kurallar şunlardır:

<br/>

| Çok biçimli tehditler | Yanal hareket & kimlik bilgisi hırsızlığı | Üretkenlik uygulamaları kuralları |  E-posta kuralları | Betik kuralları | Çeşitli kurallar |
|:---|:---|:---|:---|:---|:---|
| Bir yaygınlık (1000 makine), yaş (24 saat) veya güvenilir liste ölçütlerini karşılamadığı sürece yürütülebilir dosyaların çalışmasını engelleyin | PSExec ve WMI komutlarından kaynaklanan işlem oluşturma işlemlerini engelleme | Office uygulamaların yürütülebilir içerik oluşturmalarını engelleme | E-posta istemcisinden ve web postasından yürütülebilir içeriği engelleme | Karartılmış JS/VBS/PS/makro kodunu engelleme | Güvenlik açığı bulunan imzalı sürücülerin <sup>kötüye kullanımı engellendi [[1](#fn1)]<sup></sup>  |
| USB'den çalıştırılan güvenilmeyen ve imzalanmamış işlemleri engelleme | Windows yerel güvenlik yetkilisi alt sisteminden kimlik bilgilerinin çalınmalarını engelle (lsass.exe)<sup>[[2](#fn1)]<sup></sup>   | Office uygulamalarının alt işlemler oluşturmalarını engelleme |  Yalnızca Office iletişim uygulamalarının alt işlemler oluşturmalarını engelleyin | JS/VBS'nin indirilen yürütülebilir içeriği başlatmasını engelleme | |
| Fidye yazılımına karşı gelişmiş koruma kullanma | WMI olay aboneliği aracılığıyla kalıcılığı engelleme | Office uygulamaların diğer işlemlere kod eklemesini engelleme | Office iletişim uygulamalarının alt işlemler oluşturmalarını engelleme | | |
| | | Adobe Reader'ın alt işlemler oluşturmalarını engelleme | | | |

(<a id="fn1">1</a>) _Güvenlik açığı bulunan imzalı sürücülerin kötüye kullanımı engelleniyor_ , şu anda MEM Uç Noktası güvenliğinde kullanılamıyor. Bu kuralı [MEM OMA-URI](enable-attack-surface-reduction.md#mem) kullanarak yapılandırabilirsiniz.

(<a id="fn1">2</a>) Bazı ASR kuralları önemli miktarda kirlilik oluşturur, ancak işlevselliği engellemez. Örneğin, Chrome'ı güncelleştiriyorsanız; Chrome lsass.exe erişecek; parolalar cihazdaki lsass içinde depolanır. Ancak, Chrome yerel cihaz lsass.exe erişmemelidir. Lsass'e erişimi engellemek için kuralı etkinleştirirseniz, çok sayıda olay oluşturur. Yazılım güncelleştirme işleminin lsass.exe erişmemesi gerektiğinden bu olaylar iyi olaylardır. Bu kuralın etkinleştirilmesi Chrome güncelleştirmelerinin lsass'e erişmesini engeller ancak Chrome'un güncelleştirilmesini engellemez; bu, lsass.exe gereksiz çağrılar yapılan diğer uygulamalar için de geçerlidir. _lsass kuralına erişimi engelleme, lsass'a_ gereksiz çağrıları engeller, ancak uygulamanın çalışmasını engellemez.

### <a name="infrastructure-requirements"></a>Altyapı gereksinimleri

ASR kurallarını uygulamak için birden çok yöntem mümkün olsa da, bu kılavuz aşağıdakilerden oluşan bir altyapıyı temel alır:

- Azure Active Directory
- Microsoft Endpoint Management (MEM)
- cihazları Windows 10 ve Windows 11
- E5 veya Windows E5 lisanslarını Uç Nokta için Microsoft Defender

ASR kurallarından ve raporlamadan tam olarak yararlanmak için Microsoft 365 Defender E5 veya Windows E5 lisansı ve A5 kullanmanızı öneririz. Daha fazla bilgi edinin: [Uç Nokta için Microsoft Defender için en düşük gereksinimler](minimum-requirements.md).

>[!Note]
>ASR kurallarını yapılandırmak için birden çok yöntem vardır. ASR kuralları şu kullanılarak yapılandırılabilir: Microsoft Endpoint Manager (MEM), PowerShell, grup ilkesi, Microsoft System Center Configuration Manager (SCCM), MEM OMA-URI.
>_Altyapı gereksinimleri_ (yukarıda) için listelenenden farklı bir altyapı yapılandırması kullanıyorsanız, diğer yapılandırmaları kullanarak saldırı yüzeyi azaltma kurallarını dağıtma hakkında daha fazla bilgiyi burada bulabilirsiniz: [Saldırı yüzeyi azaltma kurallarını etkinleştirme](enable-attack-surface-reduction.md).  

### <a name="asr-rules-dependencies"></a>ASR kuralları bağımlılıkları

Microsoft Defender Virüsten Koruma birincil virüsten koruma çözümü olarak etkinleştirilmeli ve yapılandırılmalıdır ve aşağıdaki modda olmalıdır:

- Birincil virüsten koruma/kötü amaçlı yazılımdan koruma çözümü  
- Durum: Etkin mod

Microsoft Defender Virüsten Koruma aşağıdaki modlardan hiçbirinde olmamalıdır:

- Pasif
- Blok Modunda Uç Nokta algılama ve yanıt (EDR) ile Pasif Mod
- Sınırlı düzenli tarama (LPS)
- Kapalı

Bkz. [Bulut tabanlı koruma ve Microsoft Defender Virüsten Koruma](cloud-protection-microsoft-defender-antivirus.md).

### <a name="cloud-protection-maps-must-be-enabled"></a>Bulut Koruması (MAPS) etkinleştirilmelidir

Microsoft Defender Virüsten Koruma, Microsoft bulut hizmetleriyle sorunsuz çalışır. Microsoft Gelişmiş Koruma Hizmeti (MAPS) olarak da adlandırılan bu bulut koruma hizmetleri, standart gerçek zamanlı korumayı geliştirir ve muhtemelen en iyi virüsten koruma savunmasını sağlar. Bulut koruması, kötü amaçlı yazılım ihlallerini ve ASR kurallarının kritik bir bileşenini önleme açısından kritik öneme sahiptir.
[Microsoft Defender Virüsten Koruma'de bulut tabanlı korumayı açın](enable-cloud-protection-microsoft-defender-antivirus.md).

### <a name="microsoft-defender-antivirus-components-must-be-current-versions"></a>Microsoft Defender Virüsten Koruma bileşenleri geçerli sürümler olmalıdır

Aşağıdaki Microsoft Defender Virüsten Koruma bileşen sürümleri, şu anda en çok kullanılabilen sürümden en eski iki sürümden daha eski olmamalıdır:

- **Microsoft Defender Virüsten Koruma Platform güncelleştirme sürümü** - Microsoft Defender Virüsten Koruma platform aylık olarak güncelleştirilir.
- **Microsoft Defender Virüsten Koruma altyapısı sürümü** - Microsoft Defender Virüsten Koruma altyapısı aylık olarak güncelleştirilir.
- **Microsoft Defender Virüsten Koruma güvenlik bilgileri** - Microsoft, en son tehditleri ele almak ve algılama mantığını iyileştirmek için Microsoft Defender güvenlik zekasını (tanım ve imza olarak da bilinir) sürekli olarak güncelleştirir.

Microsoft Defender Virüsten Koruma sürümleri güncel tutmak ASR kurallarının hatalı pozitif sonuçları azaltmaya yardımcı olur ve Microsoft Defender Virüsten Koruma algılama özelliklerini geliştirir. Geçerli sürümler ve farklı Microsoft Defender Virüsten Koruma bileşenlerini güncelleştirme hakkında daha fazla bilgi için [Microsoft Defender Virüsten Koruma platform desteğini](manage-updates-baselines-microsoft-defender-antivirus.md) ziyaret edin.

### <a name="caveat"></a>Uyarı

İmzalanmamış, dahili olarak geliştirilmiş uygulama ve betikler yüksek kullanımdaysa bazı kurallar düzgün çalışmaz. Kod imzalama uygulanmazsa ASR kurallarını dağıtmak daha zordur.

## <a name="asr-rules-deployment-steps"></a>ASR kuralları dağıtım adımları

İş kolu operasyonlarınızı etkileyebilecek yeni, geniş ölçekli uygulamalarda olduğu gibi planlama ve uygulama konusunda da yöntemli olmak önemlidir. ASR kurallarının kötü amaçlı yazılımları önlemedeki güçlü özellikleri nedeniyle, benzersiz müşteri iş akışlarınız için en iyi şekilde çalıştıklarından emin olmak için bu kuralların dikkatli bir şekilde planlanması ve dağıtılması gerekir. Ortamınızda çalışmak için ASR kurallarını dikkatle planlamanız, test etmeniz, uygulamanız ve kullanıma hazır hale getirmeniz gerekir.  

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-rules-deployment-phases.png" alt-text="ASR kuralları dağıtım aşamaları" lightbox="images/asr-rules-deployment-phases.png":::

>[!Note]
>Microsoft olmayan bir HIPS kullanan ve Uç Nokta için Microsoft Defender saldırı yüzeyi azaltma kurallarına geçiş yapan Müşteriler için: Microsoft, siz Denetim modundan Blok moduna geçene kadar müşterilerin HIPS çözümünü ASR kuralları dağıtımıyla yan yana çalıştırmalarını önerir. Dışlama önerileri için üçüncü taraf virüsten koruma yazılımı satıcınıza ulaşmanız gerektiğini unutmayın.  

## <a name="additional-topics-in-this-deployment-collection"></a>Bu dağıtım koleksiyonundaki ek konular

[Test saldırı yüzeyi azaltma (ASR) kuralları](attack-surface-reduction-rules-deployment-test.md)

[Saldırı yüzeyi azaltma (ASR) kurallarını etkinleştirme](attack-surface-reduction-rules-deployment-implement.md)

[Saldırı yüzeyini azaltma (ASR) kurallarını kullanıma hazır hale getirme](attack-surface-reduction-rules-deployment-operationalize.md)

[Saldırı yüzeyi azaltma (ASR) kuralları başvurusu](attack-surface-reduction-rules-reference.md)

## <a name="reference"></a>Başvuru

### <a name="blogs"></a>Bloglar

[Saldırı yüzeyini azaltma kurallarını kaldırma - 1. Bölüm](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420)

[Saldırı yüzeyi azaltma kurallarını kaldırma - Bölüm 2](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-2/ba-p/1326565)

[Saldırı yüzeyini azaltma kurallarını kaldırma - Bölüm 3](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-3/ba-p/1360968)

[Saldırı yüzeyini azaltma kurallarını kaldırma - Bölüm 4](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-4/ba-p/1384425)

### <a name="asr-collection"></a>ASR koleksiyonu

[Saldırı yüzeyini azaltmaya genel bakış](overview-attack-surface-reduction.md)

[Kötü amaçlı yazılım bulaşmasını önlemek için saldırı yüzeyi azaltma kurallarını kullanma](attack-surface-reduction.md)

[Saldırı yüzeyi azaltma kurallarını etkinleştirme - alternatif yapılandırmalar](enable-attack-surface-reduction.md)

[Saldırı yüzeyi azaltma kuralları başvurusu](attack-surface-reduction-rules-reference.md)

[Saldırı yüzeyini azaltma ile ilgili SSS](attack-surface-reduction-faq.yml)

### <a name="microsoft-defender"></a>Microsoft Defender

[Uç Nokta için Microsoft Defender'da yanlış pozitifleri/negatifleri ele alın](defender-endpoint-false-positives-negatives.md)

[Bulut tabanlı koruma ve Microsoft Defender Virüsten Koruma](cloud-protection-microsoft-defender-antivirus.md)

[Microsoft Defender Virüsten Koruma'de bulut tabanlı korumayı açma](enable-cloud-protection-microsoft-defender-antivirus.md)

[Uzantı, ad veya konuma göre dışlamaları yapılandırma ve doğrulama](configure-extension-file-exclusions-microsoft-defender-antivirus.md)

[Microsoft Defender Virüsten Koruma platform desteği](manage-updates-baselines-microsoft-defender-antivirus.md)

[Microsoft 365 Uygulamaları yönetim merkezinde envantere genel bakış](/deployoffice/admincenter/inventory)

[Windows için dağıtım planı oluşturma](/windows/deployment/update/create-deployment-plan)

[Intune'de dağıtılmış BT için rol tabanlı erişim denetimi (RBAC) ve kapsam etiketlerini kullanma](/mem/intune/fundamentals/scope-tags)

[Microsoft Intune'de cihaz profilleri atama](/mem/intune/configuration/device-profile-assign#exclude-groups-from-a-profile-assignment)

### <a name="management-sites"></a>Yönetim siteleri

[yönetim merkezini Microsoft Endpoint Manager](https://endpoint.microsoft.com/#home)

[Saldırı yüzeyini azaltma](https://security.microsoft.com/asr?viewid=detections)

[ASR kuralları Yapılandırmalar](https://security.microsoft.com/asr?viewid=configuration)

[ASR kuralları Dışlamalar](https://security.microsoft.com/asr?viewid=exclusions)
