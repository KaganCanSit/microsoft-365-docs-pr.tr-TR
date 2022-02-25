---
title: Pilot projenizi Microsoft 365 Defender planlama
description: Beklentileri yönetmek Microsoft 365 Defender başarılı sonuçlar elde etmek için pilot projenizi paydaşlarla birlikte planlayın.
keywords: Microsoft 365 Defender pilot çalışma planı, pilot Microsoft 365 Defender planlama, üretim Microsoft 365 Defender planlama ve planlama Microsoft 365 Defender  pilot proje, siber güvenlik, gelişmiş kalıcı tehdit, kurumsal güvenlik, cihazlar, cihaz, kimlik, kullanıcılar, veriler, uygulamalar, olaylar, otomatik araştırma ve düzeltme, gelişmiş tarama
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dolmont
author: DulceMontemayor
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-pilotmtpproject
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 6a52df8035ce6f84770a2d06c3b8c127e426622e
ms.sourcegitcommit: 9856f86532bdcf0befbcdbdb7c6dc6bf89fe63b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2021
ms.locfileid: "62959678"
---
# <a name="planning-your-pilot-microsoft-365-defender-project"></a>Pilot projenizi Microsoft 365 Defender planlama 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender

|![Planlama](../../media/phase-diagrams/1-planning.png)<br/>Planlama|[![Hazırlama](../../media/phase-diagrams/2-prepare.png)](prepare-m365d-eval.md)<br/>[Hazırlık](prepare-m365d-eval.md) | [![Saldırıyı benzetin](../../media/phase-diagrams/3-simluate.png)](m365d-pilot-simulate.md)<br/>[Saldırıyı benzetin](m365d-pilot-simulate.md) | [![Kapatma ve özetleme](../../media/phase-diagrams/4-summary.png)](m365d-pilot-close.md)<br/>[Kapatma ve özetleme](m365d-pilot-close.md)|
|--|--|--|--|
|*Buradasınız!*| | | |

Şu anda planlama aşamasındayız.

Pilot projenizin başarıdan emin olmak için, en baştan proje katılımcılarınızı kapsamlı bir şekilde planlamak ve onay almak temel öneme sahip olur. Planlamanın öğeleri tanımlama kapsamı, kullanım örnekleri, gereksinimler ve başarı ölçütleridir.

Bu kılavuz, pilot projenizi planlamada size yollukluk ediyor. 

>[!IMPORTANT]
>En iyi sonuçları elde etmek için pilot yönergeleri mümkün olduğunca yakından izleyin.


## <a name="scope"></a>Kapsam

Pilot kapsamı, ortamınıza ve kabul edilebilir test yöntemlerine göre testin ne kadar geniş olacağını belirler. Aşağıdaki örnek kapsamları göz önünde bulundurarak göz önünde bulundurarak:

- Uç noktaları, sunucuları, etki alanı denetleyicilerini içeren geliştirme veya test ortamı.
- Microsoft 365, Azure, Active Directory hizmetleri, uç noktalar ve sunucularıyla üretim ortamı

>[!NOTE]
>Henüz tam lisanslara sahip değilsiniz, deneme lisanslarını edinerek pilot projenizi [Microsoft 365 Defender](m365d-evaluation.md?ocid=cx-docs-MTPtriallab), hazırlama, kurma, yapılandırma ve çalıştırma gibi deneme lisanslarını elde edin. Paydaşlar, süreci baştan sona kolaylaştırmanıza yardımcı olmak için büyük bir rol oynar.

Değerlendirilecek işletim sistemlerinin türleri de, kurumsal olarak buna dayalı olarak tanımlanmalıdır. Bu şunlardan bazıları olabilir: [Mac uç noktaları](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-mac#system-requirements), [Linux Sunucuları](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-atp-linux#system-requirements), [Windows 10 uç noktaları](/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements#supported-windows-versions), [Windows Server 2016](/windows/security/threat-protection/microsoft-defender-atp/minimum-requirements#supported-windows-versions).

## <a name="use-cases"></a>Vakaları kullanma

Kullanım örnekleri, test edilen aracın hedeflenen kullanıcıları tarafından nasıl tüketilmesi amaçlanan bir ifadedir. Bunlar, SOC analisti gibi belirli bir kişilik açısından kullanıcı öyküleri olarak formüle biçimlendirilmiş olabilir. Örneğin:

- SoC analisti olarak, ağımda cihazlar, kullanıcılar ve posta kutuları genelinde uyarıları ve olayları görüntülemem, bulerle bağlantılı bir şekilde değerlendirmem ve yönetmem gerekir. [Olay yönetimi]
- SoC analisti olarak, ağımda kötü amaçlı olayları otomatik olarak araştıracak ve yanıt verebilecek bir araç ve işlemem olmalıdır. [Otomatik IR]
- SoC analisti olarak, bilinen ve olası tehditleri ve şüpheli etkinlikleri bulmak için ortamımdan verileri aramam gerekir. [Gelişmiş Av]

Bu kullanım durumlarının, tanımlı kapsamın parametreleri içinde oluşturulacak şekilde olması gerektiğini unutmayın. Örneğin, test kapsamında TEST gibi araçlarla ilgili bir değerlendirme Microsoft Cloud App Security, bu veri kaynağı olarak buna güvenen örnekleri kullanmamalıdır.

## <a name="requirements"></a>Gereksinimler

Kullanım örnekleri listesinden, gereksinimleri oluşturmak için başlayabilirsiniz. Gereksinimler, bir aracın kullanım durumlarını karşılaması için sahip olması gereken özellikleri içerir. Bu gereksinimler yapılandırma ve bakım, tümleştirme desteği ve avlama özelliği ve özel uyarı oluşturma özelliği gibi özel gereksinimler gibi kategorilere ayrılır.

## <a name="test-plan"></a>Test planı

Gereksinimlere bağlı olarak, farklı test yöntemleri uygun olabilir. Örneğin, gereksinimin karşıtlık Otomatik Düzeltme'nin nasıl etkili olduğunu değerlendirmekse, test planının proje içinde otomatik bir düzeltme eylemini tetikleyen davranışları oluşturma adımlarını da Microsoft 365 Defender. Gereksinim belirli bir davranışı veya saldırıyı algılamaksa, test daha fazla adımdan oluşur. Burada asıl önemli olan, gereksinimlerinize karşı doğru test etmek için doğru bir plan yapmaktır.

## <a name="success-criteria"></a>Başarı ölçütleri

Başarı ölçütleri sonuçta, neyi test etmekte olduğunuz ile ilgili ölçmek için ayarlanmış bir çubuk taraktır. İster başka Microsoft 365 Defender, ister başka herhangi bir teknolojiyi) başka araçlarla ya da kendi başına test edersiniz, aracın sağladığı değeri belirlemek için ölçülebilir bazı ölçütler olması gerekir. Kapsam, gereksinimler ve test planına bağlı olarak, başarı ölçütleri testin nasıl puanla ilgili olduğunu belirler. Bu, puanlamadan az veya başarısız olmalı ve ihtiyaçlara göre ağırlık puanlamadan daha fazla olacaktır. Örneğin, başarılı olmak için, tanım yarıda kritik alanlarda bir aracın %80'in üzerinde puan at olması gerekir.

## <a name="scorecard"></a>Karne

Planınız için tüm öğeleri bir araya getirmenin bir yolu, karne oluşturmak olabilir. Aşağıda örnek bir karneye bakın:

| Kullanım durumu | Gereksinimler | Yapılandırma gereksinimleri | Test planı | Beklenen sonuç | Test durumu | Puan | Notlar |
|:-------|:-------|:-------|:-------|:-------|:-------|:-------|:-------|
|Olay yönetimi|- Microsoft 365 Defender </br></br>- Kimlik için Microsoft Defender </br></br>- Uç Nokta için Microsoft Defender </br></br>- Microsoft Cloud App Security (isteğe bağlı)|Ayrıntılar için [hazırlık](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) , ayarlama ve yapılandırmanın önkoşullarına bakın |[Saldırıyı benzetin](m365d-pilot-simulate.md) <br></br>[Olayı araştır](./m365d-pilot-simulate.md#investigate-an-incident) |İlkeler olayın kapsamını ve etkisini anlıyoruz ve olayı yönetebilir||||
|AutoIR|- Microsoft 365 Defender </br></br>- Kimlik için Microsoft Defender </br></br>- Uç Nokta için Microsoft Defender |Ayrıntılar için [hazırlık](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) , ayarlama ve yapılandırmanın önkoşullarına bakın <br>AutoIR'i etkinleştirme  |[Saldırıyı benzetin](m365d-pilot-simulate.md) <br></br>[Otomatik araştırma](m365d-pilot-simulate.md#automated-investigation-and-remediation) |Uyarılar ve olaylar kişi tarafından otomatik olarak Microsoft 365 Defender||||
|Gelişmiş av|- Microsoft 365 Defender </br></br>- Uç Nokta için Microsoft Defender </br></br>-Windows için Microsoft Defender Office 365 |Ayrıntılar için [hazırlık](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) , ayarlama ve yapılandırmanın önkoşullarına bakın|[Gelişmiş av senaryosu](./m365d-pilot-simulate.md#advanced-hunting-scenario) |Özel algılamalar oluşturarak, köpek köpeklerini gelişmiş avla bulabilir, etkide olan varlıklara dönerek verileri bulabilir||||

## <a name="next-step"></a>Sonraki adım

|![Hazırlık aşaması](../../media/mtp/prep.png) <br>[Hazırlık aşaması](prepare-m365d-eval.md) | Pilot ortamınızı Microsoft 365 Defender ortamınızı hazırlama
|:-------|:-----|
