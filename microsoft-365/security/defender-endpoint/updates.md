---
title: Microsoft Defender güncelleştirmeleri için aşamalı olarak geçiş işlemini yönetme
description: Aşamalı güncelleştirme işlemi ve denetimleri hakkında bilgi
keywords: güncelleştirme, güncelleştirme işlemi, denetimler, sürüm
search.product: eADQiWindows 10XVcnh
search.appverid: met150
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
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 435a77432caa9d7335a22993f85cae69eff6cd38
ms.sourcegitcommit: 3e971b31435d17ceeaa9871c01e88e25ead560fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2021
ms.locfileid: "62959664"
---
#  <a name="manage-the-gradual-rollout-process-for-microsoft-defender-updates"></a>Microsoft Defender güncelleştirmeleri için aşamalı olarak geçiş işlemini yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint/)


kritik koruma özellikleri sağlamak ve saldırılardan korunmak için istemci bileşenlerinin güncel olduğundan emin olmak önemlidir.

Özellikler çeşitli bileşenler aracılığıyla sağlanır: 

- [Uç Nokta Algılama & Yanıtı](overview-endpoint-detection-response.md) 
- [Buluta teslim edilen korumayla](microsoft-defender-antivirus-in-windows-10.md#microsoft-defender-antivirus-your-next-generation-protection) [yeni nesil koruma](cloud-protection-microsoft-defender-antivirus.md) 
- [Saldırı Yüzeyini Azaltma](overview-attack-surface-reduction.md)

Güncelleştirmeler, aşamalı bir sürüm işlemi kullanılarak aylık olarak yayımlar. Bu işlem, erken hata algılamanın meydana gelen etkiyi yakalaması ve daha büyük bir rollamadan önce bu etkiyi hızlı bir şekilde ele almalarını sağlar. 

> [!NOTE]
> Günlük tanım güncelleştirmelerini denetleme hakkında daha fazla bilgi için bkz. Günlük [tanım güncelleştirmelerini Microsoft Defender Virüsten Koruma - Windows tanımlama | Microsoft Docs](manage-protection-update-schedule-microsoft-defender-antivirus.md). Tanım güncelleştirmeleri, bulut teslimi koruması uç noktada sağlanmazsa bile yeni nesil korumanın yeni tehditlere karşı savunmada olmasını sağlar.

## <a name="microsoft-gradual-rollout-model"></a>Microsoft aşamalı kademeli kademeli çıkış modeli

Aşağıdaki aşamalı kademeli kademeli kademeli çıkış modeli takip ediliyor:

1. İlk sürüm Beta kanalı abonelerine sunulacaktır.
2. Doğrulama, geri bildirim ve düzeltmelerden sonra aşamalı olarak ve kısıtlandıktan sonra önce Kanal abonelerini önizlemek için aşamalı olarak kademeli olarak kademeli olarak geçiş işlemini başlatacağız.
3. Daha sonra, güncelleştirmeyi genel popülasyonın geri kalanına serbest bırakmak ve %10-100 arasında ölçeklendirme yapmak için devam edeceğiz.

Mühendislerimiz gereken etkiyi sürekli izlemektedir ve bir düzeltme oluşturmak için tüm sorunları büyülemektedir.

## <a name="how-to-customize-your-internal-deployment-process"></a>İç dağıtım işleminizi özelleştirme

Makineniz Windows Update'Windows Defender güncelleştirmeleri alıyorsa aşamalı olarak kademeli bir geçiş işlemi, bazı makinenizin Defender güncelleştirmelerini diğerlerine göre daha çabuk almalarını neden olabilir. Aşağıdaki bölümde, güncelleştirme kanalı yapılandırmasından yararlanarak otomatik güncelleştirmelerin belirli cihaz gruplarına farklı aksına izin verecek bir stratejinin nasıl tanımlanacakları açıklanıyor.

> [!NOTE]
> Kendi aşamalı sürümünizi planken lütfen her zaman önizleme ve aşamalı kanallara abone olan farklı cihazlar seçmeyi unutmayın. Bu, hem organizasyon hem de Microsoft'a ortamınıza özgü sorunları önleme veya bulma ve düzeltme fırsatı sağlar.

Örneğin, Windows Server Update Services (WSUS) veya Microsoft Endpoint Configuration Manager (MECM) aracılığıyla güncelleştirme alan makinelerde, tüm Windows Için Microsoft Defender uç nokta güncelleştirmeleri de dahil olmak üzere başka seçenekler de vardır.

- WSUS, MECM gibi bir çözümü kullanarak güncelleştirmelerin dağıtımını ve uygulamasını yönetme konusunda daha fazla bilgi için, Microsoft Defender Virüsten Koruma güncelleştirmelerini yönetme ve taban çizgilerini uygulama - güvenlik Windows [makalesini | Microsoft Docs](manage-updates-baselines-microsoft-defender-antivirus.md#product-updates).

## <a name="update-channels-for-monthly-updates"></a>Aylık güncelleştirmeler için kanalları güncelleştirme

Makinenin aylık altyapı ve platform güncelleştirmelerini aldığı tempoyu tanımlamak için bir makineyi güncelleştirme kanalına atabilirsiniz.

Güncelleştirmeleri yapılandırma hakkında daha fazla bilgi için bkz [. Microsoft Defender güncelleştirmeleri için özel bir aşamalı kademeli uygulama işlemi oluşturma](configure-updates.md).

Aşağıdaki güncelleştirme kanalları kullanılabilir:

| Kanal adı  | Açıklama  | Uygulama  |
|-|-|-|
| Beta Kanalı - Prerelease  | Güncelleştirmeleri diğer kişiden önce test edin  | Bu kanal olarak ayarlanmış cihazlar, yeni aylık güncelleştirmeleri ilk alan olacaktır. Sorunları Microsoft'a belirlemek ve raporlamaya katılmak için Beta Kanal'ı seçin. Insider Programı Windows içindeki cihazlar varsayılan olarak bu kanala abonedir. Yalnızca test ortamlarında kullanım için.  |
| Güncel Kanal (Önizleme)  | Aşamalı sürüm sırasında güncel **Kanal güncelleştirmelerini** daha önce alın  | Bu kanala ayarlanmış cihazlara, aşamalı sürüm döngüsünde en erken güncelleştirmeler sunulacaktır. Üretim öncesi/doğrulama ortamları için önerilir.  |
| Güncel Kanal (Aşamalı)  | Güncel Kanal güncelleştirmelerini daha sonra aşamalı sürüm sırasında alın  | Cihazlara aşamalı sürüm döngüsünde daha sonra güncelleştirmeler sunulacaktır. Cihaz popülasyonu içinde küçük, temsili bir bölüme (~%10) uygulama önerilir.  |
| Güncel Kanal (Geniş) | Aşamalı sürüm sonunda güncelleştirmeleri alın  | Ancak aşamalı sürüm döngüsü tamamlandıktan sonra cihazlara güncelleştirmeler sunulacaktır. Üretim nüfuslu geniş bir cihaz kümesine (~%10-100) uygulama önerilir.  |
| (default)  |   | Bu ilkeyi devre dışı bırakır veya yapılandırmazsanız, cihaz Güncel Kanal'da (Varsayılan) kalır: Aşamalı sürüm döngüsü sırasında otomatik olarak güncel kalın. Çoğu cihaz için uygundur.  |

### <a name="update-channels-for-daily-definition-updates"></a>Günlük tanım güncelleştirmeleri için kanalları güncelleştirme

Bir makinenin günlük tanım güncelleştirmelerini aldığı tempoyu tanımlamak için bir makineyi güncelleştirme kanalına atabilirsiniz.
  
| Kanal adı  | Açıklama  | Uygulama  |
|-|-|-|
| Güncel Kanal (Aşamalı)  | Güncel Kanal güncelleştirmelerini daha sonra aşamalı sürüm sırasında alın  | Cihazlara aşamalı sürüm döngüsünde daha sonra güncelleştirmeler sunulacaktır. Cihaz popülasyonu içinde küçük, temsili bir bölüme (~%10) uygulama önerilir.  |
| Güncel Kanal (Geniş) | Aşamalı sürüm sonunda güncelleştirmeleri alın  | Aşamalı sürüm döngüsünde cihazlara güncelleştirmeler sunulacaktır. Yalnızca sınırlı güncelleştirmeler alan veri merkezi makineleri için en iyi. Not: Bu ayar tüm Defender güncelleştirmeleri için geçerlidir.  |
| (default)  |   | Bu ilkeyi devre dışı bırakır veya yapılandırmazsanız, cihaz Güncel Kanal'da (Varsayılan) kalır: Aşamalı sürüm döngüsü sırasında otomatik olarak güncel kalın. Çoğu cihaz için uygun  |

> [!NOTE]
> Zaman gecikmesi yerine en yeni imzaya güncellemeye zorlamak isterseniz, önce bu ilkeyi kaldırmanız gerekir.

## <a name="update-guidance"></a>Güncelleştirme kılavuzu

Çoğu durumda, Windows Update kullanırken önerilen yapılandırma, uç noktaların geldiğinde aylık Defender güncelleştirmelerini almalarına ve uygulamalarına izin vermektir. Bu, aralarındaki koruma ve ortaya olabilecek değişikliklerle ilişkili olası etki arasındaki en iyi dengeyi sağlar.

Otomatik Defender güncelleştirmelerinin daha fazla denetlenen aşamalı dağıtımına gerek olan ortamlarda, dağıtım gruplarında bir yaklaşımı göz önünde bulundurmalısınız:

1. Insider programına Windows ve Beta Kanalına bir cihaz grubu attayabilirsiniz.
2. Yeni güncelleştirmeleri erkenden almak için, Kanalı Önizleme Kanalını (genellikle doğrulama ortamları) kabul ediyor bir pilot grup atama.
3. Aşamalı kanaldan aşamalı olarak geçiş sırasında güncelleştirmeleri alacak bir makine grubu atatabilirsiniz. Normalde, popülasyonu temsili %10'olacak.
4. Aşamalı sürüm döngüsü tamamlandıktan sonra güncelleştirmeleri alan bir makine grubu atama. Bunlar genellikle önemli üretim sistemleridir.

Diğer cihazlar için varsayılan ayar, Microsoft aşamalı olarak uygulama işlemi sırasında edinilen yeni güncelleştirmeleri almaktır ve başka yapılandırma gerekmez. 

Bu modeli benimseme:
- Erken sürümler üretim ortamına ulaşmadan önce test olanak sağlar 
- Üretim ortamının düzenli güncelleştirmeleri hala aldığından ve kritik tehditlere karşı koruma sağlamakta olduğundan emin olun.

## <a name="management-tools"></a>Yönetim araçları
Aylık güncelleştirmeler için kendi özel aşamalı kademeli kademeli uygulama işleminizi oluşturmak için aşağıdaki araçları kullanabilirsiniz:

- Grup ilkesi
- Microsoft Endpoint Manager
- PowerShell

Bu araçların kullanımı hakkında ayrıntılı bilgi için bkz [. Microsoft Defender güncelleştirmeleri için özel bir aşamalı kademeli kademeli uygulama işlemi oluşturma](configure-updates.md).
