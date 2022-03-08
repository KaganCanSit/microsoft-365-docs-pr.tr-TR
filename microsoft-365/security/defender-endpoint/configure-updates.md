---
title: Microsoft Defender güncelleştirmeleri için özel aşamalı bir uygulama işlemi oluşturma
description: Desteklenen araçları kullanarak güncelleştirmeler için özel bir aşamalı kademeli kademeli uygulama işlemi yapmayı öğrenin
keywords: update tools, gpo, intune, mdm, microsoft endpoint manager, policy, powershell
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
- m365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 4261e32721da86233a0a929a435c318904d6ac12
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324151"
---
# <a name="create-a-custom-gradual-rollout-process-for-microsoft-defender-updates"></a>Microsoft Defender güncelleştirmeleri için özel aşamalı bir uygulama işlemi oluşturma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> [!NOTE]
> Bu işlev, Microsoft Defender Virüsten Koruma 4.18.2106.X veya daha yeni bir sürümünü gerektirir.

Defender güncelleştirmeleri için kendi özel aşamalı kademeli kademeli uygulama işleminizi oluşturmak için Grup İlkesi, Microsoft Endpoint Manager ve PowerShell'i kullanabilirsiniz.

Aşağıdaki tabloda, güncelleştirme kanallarını yapılandırmak için kullanılabilen grup ilkesi ayarları listelemektedir:

<br>

****

|Başlığı ayarlama|Açıklama|Konum|
|---|---|---|
|Aşamalı Microsoft Defender aylık platform güncelleştirmesi kanalını seçin|Aylık aşamalı geçiş sırasında cihazların Microsoft Defender platform güncelleştirmelerini ne zaman alacaklarını belirlemek için bu ilkeyi etkinleştirin. <p> Beta Kanalı: Bu kanala ayarlanmış cihazlar yeni güncelleştirmeleri ilk alan olacak. Sorunları Microsoft'a belirlemek ve raporlamaya katılmak için Beta Kanal'ı seçin. Windows Insider Programı'nın cihazları varsayılan olarak bu kanala abonedir. Yalnızca (el ile) test ortamlarında ve sınırlı sayıda cihazda kullanım için. <p> Güncel Kanal (Önizleme): Bu kanala ayarlanmış cihazlar, güncelleştirmelerin en erken aylık aşamalı sürüm döngüsü sırasında sunulacaktır. Üretim öncesi/doğrulama ortamları için önerilir. <p> Güncel Kanal (Aşamalı): Aylık aşamalı sürüm döngüsünde cihazlara güncelleştirmeler sunulacaktır. Üretim nüfusunun küçük, temsili bir parçasına (~%10) uygulama önerilir. <p> Güncel Kanal (Geniş): Cihazlar yalnızca aşamalı sürüm döngüsü tamamlandıktan sonra güncelleştirmeler sunulacaktır. Üretim nüfuslu geniş bir cihaz kümesine (~%10-100) uygulama önerilir. <p> Kritik- Süre Gecikmesi: Cihazlara 48 saatlik gecikmeli güncelleştirmeler sunulacaktır. Yalnızca kritik ortamlar için önerilir. <p>Bu ilkeyi devre dışı bırakır veya yapılandırmazsanız, aşamalı sürüm döngüsü sırasında cihaz otomatik olarak güncel kalır. Çoğu cihaz için uygundur.|Windows Components\Microsoft Defender Virüsten Koruma|
|Aşamalı Microsoft Defender aylık altyapısı güncelleştirmesi kanalını seçin|Aylık aşamalı geçiş sırasında cihazların Microsoft Defender altyapısı güncelleştirmelerini ne zaman alacaklarını belirlemek için bu ilkeyi etkinleştirin. <p> Beta Kanalı: Bu kanala ayarlanmış cihazlar yeni güncelleştirmeleri ilk alan olacak. Sorunları Microsoft'a belirlemek ve raporlamaya katılmak için Beta Kanal'ı seçin. Windows Insider Programı'nın cihazları varsayılan olarak bu kanala abonedir. Yalnızca (el ile) test ortamlarında ve sınırlı sayıda cihazda kullanım için. <p> Güncel Kanal (Önizleme): Bu kanala ayarlanmış cihazlar, güncelleştirmelerin en erken aylık aşamalı sürüm döngüsü sırasında sunulacaktır. Üretim öncesi/doğrulama ortamları için önerilir. <p> Güncel Kanal (Aşamalı): Aylık aşamalı sürüm döngüsünde cihazlara güncelleştirmeler sunulacaktır. Üretim nüfusunun küçük, temsili bir parçasına (~%10) uygulama önerilir. <p> Güncel Kanal (Geniş): Cihazlar yalnızca aşamalı sürüm döngüsü tamamlandıktan sonra güncelleştirmeler sunulacaktır. Üretim nüfuslu geniş bir cihaz kümesine (~%10-100) uygulama önerilir. <p> Kritik- Süre Gecikmesi: Cihazlara 48 saatlik gecikmeli güncelleştirmeler sunulacaktır. Yalnızca kritik ortamlar için önerilir.<p> Bu ilkeyi devre dışı bırakır veya yapılandırmazsanız, aşamalı sürüm döngüsü sırasında cihaz otomatik olarak güncel kalır. Çoğu cihaz için uygundur.|Windows Components\Microsoft Defender Virüsten Koruma|
|Aşamalı Microsoft Defender günlük güvenlik zekası güncelleştirmeleri kanalını seçme|Günlük aşamalı geçiş sırasında cihazların Microsoft Defender güvenlik zekası güncelleştirmelerini ne zaman alacaklarını belirlemek için bu ilkeyi etkinleştirin. <p> Güncel Kanal (Aşamalı): Cihazlara yayın döngüsünün ardından güncelleştirmeler sunulacaktır. Üretim nüfusunun küçük, temsili bir parçasına (~%10) uygulama önerilir. <p> Güncel Kanal (Geniş): Cihazlar yalnızca aşamalı sürüm döngüsü tamamlandıktan sonra güncelleştirmeler sunulacaktır. Üretim nüfuslu geniş bir cihaz kümesine (~%10-100) uygulama önerilir. <p>  Bu ilkeyi devre dışı bırakır veya yapılandırmazsanız, günlük sürüm döngüsü sırasında cihaz otomatik olarak güncel kalır. Çoğu cihaz için uygundur.|Windows Components\Microsoft Defender Virüsten Koruma|
|Microsoft Defender güncelleştirmelerinin aşamalı olarak geçişlerini devre dışı bırakma|Defender güncelleştirmelerinin aşamalı olarak kademeli olarak yuvarlansını devre dışı bırakmak için bu ilkeyi etkinleştirin. <p> Güncel Kanal (Geniş): Bu kanala ayarlanmış cihazlara aşamalı sürüm döngüsü boyunca en son güncelleştirmeler sunulacaktır. Yalnızca sınırlı güncelleştirmeler alan veri merkezi makineleri için en iyi. <p> Not: Bu ayar hem aylık hem de günlük Defender güncelleştirmeleri için geçerlidir ve platform ve altyapı güncelleştirmeleri için önceden yapılandırılmış kanal seçimlerini geçersiz kılar. <p> Bu ilkeyi devre dışı bırakır veya yapılandırmazsanız, platform ve altyapı güncelleştirmeleri için belirli kanallarda aksi belirtilmedikçe cihaz Geçerli Kanal'da (Varsayılan) kalır. Aşamalı sürüm döngüsü sırasında otomatik olarak güncel kalın. Çoğu cihaz için uygundur.|Windows Components\Microsoft Defender Virüsten Koruma|
|

## <a name="group-policy"></a>Grup İlkesi

> [!NOTE]
> Güncelleştirilmiş bir Defender ADMX şablonu, yayınlanacak 21H2 sürümüyle birlikte Windows 10. Yerelleştirilmiş olmayan bir sürüm indirilebilir: https://github.com/microsoft/defender-updatecontrols.

Grup [İlkesi'yi kullanarak,](/windows/win32/srvnodes/group-policy?redirectedfrom=MSDN) uç noktalarınıza Microsoft Defender Virüsten Koruma ve yönetebilirsiniz.

Genel olarak, grup ilkesi ayarlarını yapılandırmak veya değiştirmek için Microsoft Defender Virüsten Koruma kullanabilirsiniz:

1. Grup İlkesi yönetim makinenizin Grup İlkesi Yönetim Konsolu'nu **açın, yapılandırmak** istediğiniz Grup İlkesi Nesnesine **(** GPO) sağ tıklayın ve Düzenle'ye **tıklayın**.

2. Grup İlkesi Yönetim Düzenleyicisi'ni kullanarak Bilgisayar **yapılandırması'ne gidin**.

3. Yönetim **şablonları'ne tıklayın**.

4. Bileşenleri ve bileşenleri Windows **için > Microsoft Defender Virüsten Koruma**.

5. Yapılandırmak istediğiniz ayarı içeren bölümü genişletin (bu  konu başlığı altında, tabloda Konum olarak adlandırılır), ayarı çift tıklatın ve yapılandırma değişiklikleri yapın.

6. [Güncelleştirilmiş GPO'nun normalde olduğu gibi dağıtın](https://msdn.microsoft.com/library/ee663280(v=vs.85).aspx).

## <a name="intune"></a>Intune

Intune'da özel bir ilke oluşturmak için aşağıdaki bağlantıda verilen yönergeleri izleyin:

[Microsoft Intune'Windows 10 cihazlar için özel ayarlar ekleme - Azure \|Microsoft Docs](/mem/intune/configuration/custom-settings-windows-10)

Aşamalı kademeli kademeli geçiş işlemi için kullanılan Defender CSP hakkında daha fazla bilgi için bkz. [Defender CSP](/windows/client-management/mdm/defender-csp).

## <a name="powershell"></a>PowerShell

Aşamalı güncelleştirmeleri `Set-MpPreference` yapılandırmak için cmdlet'i kullanın.

Aşağıdaki parametreleri kullanın:

```powershell
Set-MpPreference
-PlatformUpdatesChannel Beta|Preview|Staged|Broad|Delayed|NotConfigured
-EngineUpdatesChannel Beta|Preview|Staged|Broad|Delayed|NotConfigured
-DisableGradualRelease True|False
-SignaturesUpdatesChannel Staged|Broad|NotConfigured
```

Örneğin:

Beta `Set-MpPreference -PlatformUpdatesChannel Beta` Kanalından gelecek platform güncelleştirmelerini yapılandırmak için kullanın.

Parametreler ve bunları yapılandırma hakkında daha fazla bilgi için bkz. [Set-MpPreference (Microsoft Defender Virüsten Koruma)| Microsoft Docs](/powershell/module/defender/set-mppreference).
