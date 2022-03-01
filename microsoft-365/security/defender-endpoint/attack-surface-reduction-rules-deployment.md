---
title: ASR kuralları dağıtım önkoşulları
description: Saldırı yüzeyini azaltma (ASR) kurallarını dağıtma hakkında genel bakış ve önkoşul kılavuzu sağlar.
keywords: Saldırı yüzeyini azaltma kuralları dağıtımı, ASR dağıtımı, asr kurallarını etkinleştirme, ASR'yi yapılandırma, izinsiz giriş engelleme sistemi, koruma kuralları, istismardan koruma kuralları, istismardan koruma kuralları, bulaşma önleme kuralları, Uç nokta için Microsoft Defender, ASR kurallarını yapılandırma
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
ms.collection: m365solution-scenario
ms.date: 1/18/2022
ms.openlocfilehash: 7a05d2712adb37121b1e625ab5c4774a60af3e81
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63012005"
---
# <a name="asr-rules-deployment-prerequisites"></a>ASR kuralları dağıtım önkoşulları

## <a name="before-you-begin"></a>Başlamadan önce

Saldırı yüzeyleri, kuruluşlarının siber tehditlere ve saldırılara açık olduğu tüm yerlerdir. Kuruluş saldırı yüzeyleri, bir saldırganın, kuruluş cihazları veya ağlarının güvenliğini tehlikeye at olduğu tüm yerleri içerir. Saldırı yüzeyinizi azaltmak, kuruluş cihazlarınızı ve ağın korunması anlamına gelir; bu da saldırganları saldırıya daha az yol bırakır. Saldırı yüzeyini azaltma (ASR) kurallarını (Uç Nokta için Microsoft Defender'da bulunan birçok güvenlik özelliği) yapılandırmanıza yardımcı olabilir.

ASR kuralları, şu tür belirli yazılım davranışlarını hedefler:

- Yürütülebilir dosyaları ve dosyaları indirmeye veya çalıştırmaya çalışan betikleri başlatma
- Obfuscated veya başka türlü şüpheli betikleri çalıştırma
- Uygulamaların çoğunlukla günlük normal çalışma sırasında oluşmayacak davranışlar

Farklı saldırı yüzeylerini azaltarak ilk başta saldırıların önlenmesine yardımcı olursiniz.

İlk hazırlığınız sırasında, yerine koyacakları sistemlerin özelliklerini anlamanız çok önemlidir. Yeteneklerin anlaşılması, kurumlarınızı koruma açısından en önemli ASR kurallarını belirlemenize yardımcı olur. Buna ek olarak, ASR dağıtımınızı hazırlığı için katılmanız gereken bazı önkoşullar vardır.

>[!IMPORTANT]
>Bu kılavuz, ASR kurallarının nasıl yapılandırı olduğuna karar vermede size yardımcı olacak resimler ve örnekler sağlar; bu resim ve örnekler ortamınız için en iyi yapılandırma seçeneklerini yansıtmayabilirsiniz.

Başlamadan önce Saldırı yüzeyini [azaltmaya genel bakış ve](overview-attack-surface-reduction.md) Saldırı yüzeyini azaltma kurallarının yeniden ortaya çıkarımı - Temel bilgiler için [Bölüm 1'i](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420) gözden geçirebilirsiniz. Kapsam alanlarını ve olası etkiyi anlamak için, geçerli ASR kuralları kümesine aşinalık sahibi olursunuz; Saldırı [yüzeyini azaltma kuralları başvuru kılavuzuna bakın](attack-surface-reduction-rules-reference.md).

ASR kuralları, Uç Nokta için Microsoft Defender'da saldırı yüzeyini azaltma özelliğinin yalnızca bir özelliğidir. Bu belge, insan tarafından işletilen fidye yazılımı ve diğer tehditlere benzer gelişmiş tehditleri durdurmak için ASR kurallarının etkili bir şekilde dağıtımı hakkında daha ayrıntılı bilgi içerir.  

### <a name="rules-by-category"></a>Kategoriye göre kurallar

Kötü amaçlı yazılım bulaşmasını önlemek için saldırı [alanı](attack-surface-reduction.md) azaltma kurallarını kullanma'da ana hatlarıyla açıklandı; MDE içinde, kurumlarınızı korumak için etkinleştir kullanabileceğiniz birçok saldırı alanı azaltma kuralı vardır. Aşağıda, kategoriye göre bozuk kurallar ve ardından ve sonra da şöyledir:

<br/>

| Polimorphik tehditler | Lateral movement & credential theft | Üretkenlik uygulamaları kuralları |  E-posta kuralları | Betik kuralları | Çeşitli kurallar |
|:---|:---|:---|:---|:---|:---|
| Yürütülebilir dosyaların yaygın (1000 makine), yaş (24 sa) veya güvenilir liste ölçütlerine uygun olmadığı sürece çalıştırulmalarını engelin | PSExec ve WMI komutlarından kaynaklanan süreç oluşturma işlemlerini engelleme | Yürütülebilir Office yürütülebilir içerik oluşturmalarını engelleme | E-posta istemcisi ve web postası yürütülebilir içeriğini engelleme | Obfuscated JS/VBS/PS/macro kodunu engelleme | Açıklardan yararlanan ve imzalı sürücüler için kötüye kullanımı engelleme <sup>[[1](#fn1)]<sup></sup>  |
| USB'den çalıştıran güvenilmeyen ve imzalanmamış işlemleri engelleme | Yerel güvenlik yetkilisi alt sisteminden (Windows) kimlik bilgilerini çalarak engelleme (lsass.exe)<sup>[[2](#fn1)]<sup></sup>   | Diğer Office alt işlemleri oluşturmalarını engelleme |  Yalnızca Office uygulamalarının alt işlemleri oluşturmalarını engelleme | JS/VBS'nin indirilen yürütülebilir içeriği başlatmalarını engelleme | |
| Fidye yazılımlarına karşı gelişmiş koruma kullanın | WMI olay aboneliği aracılığıyla kalıcılığı engelleme | Diğer Office başka işlemlere kod eklemelerini engelleme | Alt Office uygulamalarının alt işlemleri oluşturmalarını engelleme | | |
| | | Adobe Reader'ın alt işlemleri oluşturmalarını engelleme | | | |

(<a id="fn1">1</a>) _Açıklardan yararlanan açık sürücü_ kullanımına engel olun, şu anda MEM Uç Noktası güvenliğinde kullanılamıyor. Bu kuralı [MEM OMA-URI kullanarak yapılandırsanız.](enable-attack-surface-reduction.md#mem)

(<a id="fn1">2</a>) Bazı ASR kuralları önemli miktarda gürültü üretir, ancak işlevselliği engellemez. Örneğin, Chrome'u güncelleştiriyorsanız; Chrome lsass.exe erişecek; parolaları cihaz üzerinde lsass'ta saklanır. Ancak Chrome, yerel cihaza veya cihaza erişe lsass.exe. Kuralın lsass'a erişimini engellemeye olanak sağlarsanız çok fazla olay oluşturulur. Bu olaylar iyi bir olaydır çünkü yazılım güncelleştirme işlemi veritabanına erişme lsass.exe. Bu kuralın etkinleştirilmesi Chrome güncelleştirmelerinin lsass'a erişimini engelleyecek, ancak Chrome'un güncelleştirmesini engellemez; bu durum, başka uygulamalara gereksiz çağrılar yapmak için lsass.exe. _lsass kuralına erişimi_ engelleme kuralı, lsass'a yapılan gereksiz aramaları engelleyecek, ancak uygulamanın çalışmalarını engellemez.

### <a name="infrastructure-requirements"></a>Altyapı gereksinimleri

ASR kurallarını uygulamanın birden çok yöntemi mümkün olsa da, bu kılavuzda aşağıdakilerden oluşan bir altyapı temel almaktadır:

- Azure Active Directory
- Microsoft Uç Nokta Yönetimi (MEM)
- Windows 10 ve Windows 11 cihaz
- Uç Nokta E5 veya Windows E5 lisansları için Microsoft Defender

ASR kuralları ve raporlamadan tam olarak yararlanmak için, Microsoft 365 Defender E5 lisansı ve A5 Windows A5 kullanmanız önerilir. Daha fazla bilgi: [Uç nokta için Microsoft Defender'a gereken en düşük gereksinimler](minimum-requirements.md).

>[!Note]
>ASR kurallarını yapılandırmanın birden çok yöntemi vardır. ASR kuralları şu şekilde ya yapılandırabilirsiniz: Microsoft Endpoint Manager (MEM), PowerShell, Grup İlkesi, Microsoft System Center Configuration Manager (SCCM), MEM OMA-URI.
>Altyapı _gereksinimleri (yukarıda_ ) için listelenenden farklı bir altyapı yapılandırması kullanıyorsanız, diğer yapılandırmaları kullanarak saldırı yüzeyini azaltma kurallarını dağıtma hakkında daha fazla bilgi edinmek için buradan [öğrenebilirsiniz](enable-attack-surface-reduction.md): Saldırı yüzeyini azaltma kurallarını etkinleştirme.  

### <a name="asr-rules-dependencies"></a>ASR kuralları bağımlılıkları

Microsoft Defender Virüsten Koruma virüsten koruma çözümü olarak etkinleştiril olmalı ve yapılandırıldı olmalı ve aşağıdaki modda olmalıdır:

- Birincil virüsten koruma/kötü amaçlı yazılımdan koruma çözümü  
- Durum: Etkin mod

Microsoft Defender Virüsten Koruma aşağıdaki modlardan hiçbirsinde yer alamama gerekir:

- Edilgen
- Engelleme Modunda Uç nokta algılama ve yanıt (EDR) ile Pasif Modu
- Sınırlı düzenli tarama (LPS)
- Kapalı

Bkz. [Buluta teslim edilen koruma ve Microsoft Defender Virüsten Koruma](cloud-protection-microsoft-defender-antivirus.md).

### <a name="cloud-protection-maps-must-be-enabled"></a>Bulut Koruması (HARITALAR) etkinleştirilmelidir

Microsoft Defender Virüsten Koruma, Microsoft bulut hizmetleriyle sorunsuz çalışır. Microsoft Gelişmiş Koruma Hizmeti (HARITALAR) olarak da adlandırılan bu bulut koruma hizmetleri, standart gerçek zamanlı korumayı geliştirerek, muhtemelen en iyi virüsten koruma savunmasını sağlar. Bulut koruması, kötü amaçlı yazılımdan ihlalleri önlemede ve ASR kurallarının kritik bir bileşeni açısından çok önemlidir.
[Bulutta teslim edilen korumayı bulutta Microsoft Defender Virüsten Koruma](enable-cloud-protection-microsoft-defender-antivirus.md).

### <a name="microsoft-defender-antivirus-components-must-be-current-versions"></a>Microsoft Defender Virüsten Koruma geçerli sürümler olmalı

Aşağıdaki Microsoft Defender Virüsten Koruma bileşen sürümlerinin, en çok kullanılabilen sürümden önceki iki sürümden daha eski olması gerekir:

- **Microsoft Defender Virüsten Koruma Platform güncelleştirmesi sürümü** - Microsoft Defender Virüsten Koruma platform aylık olarak güncelleştirilir.
- **Microsoft Defender Virüsten Koruma sürümü - Microsoft Defender Virüsten Koruma** sürümü aylık olarak güncelleştirilir.
- **Microsoft Defender Virüsten Koruma zekası** kullanımı - Microsoft, en son tehditlere karşı ve algılama mantığını geliştirmek için Microsoft Defender güvenlik zekası'nın (tanım ve imza olarak da bilinir) güncelleştirmesini sürekli olarak günceller.

Geçerli Microsoft Defender Virüsten Koruma tutmak, HATALı pozitif sonuçların ASR kurallarını azaltmaya yardımcı olur ve Microsoft Defender Virüsten Koruma özelliklerini iyiler. Geçerli sürümler hakkında daha fazla ayrıntı ve farklı sistem bileşenlerinin nasıl Microsoft Defender Virüsten Koruma platform [Microsoft Defender Virüsten Koruma ziyaret edin](manage-updates-baselines-microsoft-defender-antivirus.md).

### <a name="caveat"></a>Uyarı

İmzalanmamış, şirket içinde geliştirilmiş uygulama ve betiklerin yüksek kullanım süresi varsa, bazı kurallar işe yaramadı. Kod imzalama zorunlu kılınmazsa ASR kurallarını dağıtmak daha zordur.

## <a name="asr-rules-deployment-steps"></a>ASR kuralları dağıtım adımları

İşletmeler için iş alanı işlemlerinizi etkiabilecek tüm yeni ve geniş ölçekli uygulamalar gibi, planlama ve uygulama yöntemleriniz açısından da önemlidir. Kötü amaçlı yazılımları önlemeye yönelik ASR kurallarının güçlü özellikleri nedeniyle, benzersiz müşteri iş akışlarınıza en uygun şekilde çalışmalarını sağlamak için bu kuralların dikkatli bir şekilde planlanmaları ve dağıtımı gereklidir. Ortamınıza çalışmak için, ASR kurallarını dikkatle planlamanız, test edin, uygulaymalısınız ve faaliyete geçirmelisiniz.  

> [!div class="mx-imgBorder"]
> ![ASR kuralları dağıtım aşamaları](images/asr-rules-deployment-phases.png)

>[!Note]
>Microsoft'a yönelik olmayan bir HIPS kullanan ve Uç nokta saldırı yüzeyini azaltma kuralları için Microsoft Defender'a geçiş yapan Müşteriler için: Microsoft, denetimden Engelleme moduna geçiş yapana kadar müşterilerin HIPS çözümlerini ASR kuralları dağıtımıyla yan yana çalıştırmalarını tavsiye eder. Dışlama önerileri için üçüncü taraf virüsten koruma satıcınıza ulaşmanız gerektiğini unutmayın.  

## <a name="additional-topics-in-this-deployment-collection"></a>Bu dağıtım koleksiyonunda yer alan ek konular

[Aşama 1: Planlama](attack-surface-reduction-rules-deployment-plan.md)

[Aşama 2: Test](attack-surface-reduction-rules-deployment-test.md)

[Aşama 3: Uygulama](attack-surface-reduction-rules-deployment-implement.md)

[Aşama 4: İşlemsellik](attack-surface-reduction-rules-deployment-operationalize.md)

## <a name="reference"></a>Başvuru

### <a name="blogs"></a>Bloglar

[Saldırı yüzeyini azaltma kurallarının yeniden ortaya çıkarımı - Bölüm 1](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420)

[Saldırı yüzeyini azaltma kurallarının yeniden ortaya çıkarımı - Bölüm 2](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-2/ba-p/1326565)

[Saldırı yüzeyini azaltma kurallarının yeniden ortaya çıkarımı - Bölüm 3](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-3/ba-p/1360968)

[Saldırı yüzeyini azaltma kurallarının yeniden ortaya çıkarımı - Bölüm 4](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-4/ba-p/1384425)

### <a name="asr-collection"></a>ASR koleksiyonu

[Saldırı yüzeyini azaltmaya genel bakış](overview-attack-surface-reduction.md)

[Kötü amaçlı yazılım bulaşmasını önlemek için saldırı yüzeyini azaltma kurallarını kullanın](attack-surface-reduction.md)

[Saldırı yüzeyini azaltma kurallarını etkinleştirin](enable-attack-surface-reduction.md)

[Saldırı yüzeyini azaltma kuralları başvurusu](attack-surface-reduction-rules-reference.md)

[Saldırı yüzeyini azaltma hakkında SSS](attack-surface-reduction-faq.yml)

### <a name="microsoft-defender"></a>Microsoft Defender

[Uç nokta için Microsoft Defender'da hatalı pozitif/negatifleri adresle](defender-endpoint-false-positives-negatives.md)

[Bulut teslimi koruma ve Microsoft Defender Virüsten Koruma](cloud-protection-microsoft-defender-antivirus.md)

[Buluttan teslim edilen korumayı Microsoft Defender Virüsten Koruma](enable-cloud-protection-microsoft-defender-antivirus.md)

[Uzantı, ad veya konuma dayalı olarak dışlamaları yapılandırma ve doğrulama](configure-extension-file-exclusions-microsoft-defender-antivirus.md)

[Microsoft Defender Virüsten Koruma platformu desteği](manage-updates-baselines-microsoft-defender-antivirus.md)

[Yönetim merkezinde envantere Microsoft 365 Uygulamaları genel bakış](/deployoffice/admincenter/inventory)

[Dağıtım planı oluşturma Windows](/windows/deployment/update/create-deployment-plan)

[Intune'da dağıtılan IT için rol tabanlı erişim denetimi (RBAC) ve kapsam etiketlerini kullanma](/mem/intune/fundamentals/scope-tags)

[E-Microsoft Intune'de cihaz Microsoft Intune](/mem/intune/configuration/device-profile-assign#exclude-groups-from-a-profile-assignment)

### <a name="management-sites"></a>Yönetim siteleri

[Microsoft Endpoint Manager merkezi](https://endpoint.microsoft.com/#home)

[Saldırı yüzeyini azaltma](https://security.microsoft.com/asr?viewid=detections)

[ASR kuralları Yapılandırmaları](https://security.microsoft.com/asr?viewid=configuration)

[ASR kuralları Dışlamaları](https://security.microsoft.com/asr?viewid=exclusions)
