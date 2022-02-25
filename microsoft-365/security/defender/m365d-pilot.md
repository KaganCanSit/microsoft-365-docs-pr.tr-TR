---
title: Pilot projenizi Microsoft 365 Defender çalıştırma
description: Bu avantajları ve Microsoft 365 Defender etkili bir şekilde belirlemek için üretimde pilot projenizi Microsoft 365 Defender.
keywords: Microsoft 365 Defender pilot çalışma, pilot Microsoft 365 Defender çalıştırma, üretimde Microsoft 365 Defender ve çalışma Microsoft 365 Defender  pilot proje, siber güvenlik, gelişmiş kalıcı tehdit, kurumsal güvenlik, cihazlar, cihaz, kimlik, kullanıcılar, veriler, uygulamalar, olaylar, otomatik araştırma ve düzeltme, gelişmiş tarama
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
- m365solution-overview
- m365solution-pilotmtpproject
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: fd84ef93d679be6e1e42f823dcac1f2d5181f1e9
ms.sourcegitcommit: 9856f86532bdcf0befbcdbdb7c6dc6bf89fe63b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2021
ms.locfileid: "62959674"
---
# <a name="run-your-pilot-microsoft-365-defender-project"></a>Pilot projenizi Microsoft 365 Defender çalıştırma 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender


Bu kılavuz, iyi yapılandırılmış bir planınız olduğundan emin olmak için işaretçiler sağlayarak bir pilot proje çalıştırmanıza yardımcı olur, saldırı benzetim özelliğini kullanarak size yol gösterir ve son olarak da pilotları önemli sonuçları yansıtacak şekilde geri alırsınız.

![Pilot çalışma Microsoft 365 Defender aşamaları](../../media/pilotphases.png)


Pilot çalıştırma, diğer çalışanlara destek olmak için pilot uygulamanın avantajlarını Microsoft 365 Defender. Üretim ortamı Microsoft 365 Defender bu görevleri etkinleştirmeden ve kullanım durumlarınızı başlatmadan önce, pilot projeniz için yerine belirleyecek görevleri belirlemeyi ve başarı ölçütlerini ayarlamayı planlamanız en iyisidir. 


## <a name="how-to-use-this-pilot-playbook"></a>Bu pilot oynatma kitabını kullanma

Bu kılavuz, pilot Microsoft 365 Defender nasıl kuracaklarına ilişkin adım adım yönergelere ve yönergelere genel bir bakış sağlar. 

Microsoft 365 Defender gelişmiş saldırılara karşı tümleşik koruma sağlamak için, uç noktalar, kimlikler, e-posta ve uygulamalar arasında yerel olarak koruma, algılama, önleme, soruşturma ve yanıt sağlayan birleşik bir ihlal öncesi ve ihlal sonrası kurumsal savunma paketidir. Bunu, aşağıdaki özellikleri birleştirerek ve birleştirerek tek bir güvenlik çözümüne dönüştürüyor:

- Uç Nokta için Microsoft Defender (uç noktalar)
- Office 365 için Microsoft Defender (e-posta)
- Kimlik (kimlik) için Microsoft Defender
- Microsoft Cloud App Security (uygulamalar)

![Image of_Microsoft 365 Defender çözümü, kullanıcılar için Microsoft Defender for Identity, for endpoints Microsoft Defender for Endpoint, for Cloud apps, Microsoft Cloud App Security, for data, Microsoft Defender for Office 365](../../media/mtp/m365pillars.png)

Tümleşik güvenlik Microsoft 365 Defender, güvenlik uzmanları Uç Nokta için Microsoft Defender, Office 365 için Microsoft Defender, Kimlik için Microsoft Defender ve diğer güvenlik işaretlerinin bir arada Microsoft Cloud App Security  tehditle ilgili tam kapsam ve etkiyi, ortamı nasıl gir yaptığını, bundan nasıl etkilendiğini ve şu anda kuruluşu nasıl etkilemektedir? Microsoft 365 Defender durumdan etkilenen posta kutularını, uç noktaları ve kullanıcı kimliklerini engellemek veya durdurmak için otomatik bir işlem gerekir. Ayrıntılar için [Microsoft 365 Defender genel](microsoft-365-defender.md) bakış bilgilerine bakın.

Aşağıdaki örnek zaman çizelgesi ortamınıza doğru kaynakların var durumuna bağlı olarak değişir. Bazı algılamalar ve iş akışları diğerlerine göre daha fazla öğrenme süresine ihtiyaç olabilir.

![Pilot çalışmada örnek Microsoft 365 Defender zaman çizelgesi](../../media/phase-diagrams/pilot-phases.png)

> [!IMPORTANT]
> En iyi sonuçları elde etmek için pilot yönergeleri mümkün olduğunca yakından izleyin.

### <a name="pilot-playbook-phases"></a>Pilot çalışma kitabı aşamaları

Üç aşamalı pilot çalıştırmanın dört Microsoft 365 Defender vardır:

|Aşama | Açıklama |
|:-------|:-----|
| [Planlama](m365d-pilot-plan.md)<br> ~ 1 gün| Pilot projenizi çalıştırmadan önce göz önünde bulundurarak Microsoft 365 Defender öğrenin: <br><br>- Kapsam <br> - Vakaları kullanma <br>- Gereksinimler <br>- Test planı <br> - Başarı ölçütleri <br> - Karne 
| [Hazırlık](m365d-evaluation.md) <br>~2 gün|  Pilot Microsoft 365 ayarlamak için Access Güvenlik Microsoft 365 Defender'ne erişin. Şu adımlara yönlendirildiniz:<br><br>- Pilotnuz için paydaşları belirleme ve oturum açma arama <br> - Ortamda dikkate alınacak noktalar <br>- Access <br>- Azure Active Directory kurma <br> - Yapılandırma sırası <br> - Deneme sürümüne Microsoft 365 E5 olun <br> - Etki alanını yapılandırma <br>- Microsoft 365 E5 atama <br> - Portalda kurulum sihirbazını tamamlama|
| [Saldırı benzetimi](m365d-pilot-simulate.md) <br>~2 gün| Bir saldırının benzetimini yapmak için şu adımlara yönlendirilmiş oluruz:<br><br>- Test ortamı gereksinimlerini doğrulayın <br>- Benzetimi çalıştırın <br>- Olayı araştırma <br>- olayı çözme 
| [Kapanış ve özet](m365d-pilot-close.md) <br>~ 1 gün| Bu işlemi sona ererken, size şu kılavuzun sağlandı:<br><br>- Son çıktınızı seçin<br>- Çıktınızı proje katılımcılarımıza sın <br>- Geri bildirim sağlama <br>- Sonraki adımları izleyin 

## <a name="next-step"></a>Sonraki adım

|[Planlama aşaması](m365d-pilot-plan.md) | Microsoft 365 Defender pilot projenizi planlama 
|:-------|:-----|
