---
title: Bildirim Microsoft Defender Virüsten Koruma yapılandırma
description: Uç noktalarda hem standart hem de diğer kullanıcı bildirimlerini Microsoft Defender Virüsten Koruma ve özelleştirebileceğinizi öğrenin.
keywords: notifications, defender, antivirus, endpoint, management, admin
ms.prod: m365-security
ms.technology: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.topic: article
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2021
ms.reviewer: ''
manager: dansimp
ms.collection: M365-security-compliance
ms.openlocfilehash: 287e49a92032e725153065ef3d996e2b5c14baf9
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/29/2021
ms.locfileid: "62997048"
---
# <a name="configure-microsoft-defender-antivirus-notifications-that-appear-on-endpoints"></a>Uç Microsoft Defender Virüsten Koruma görünen kullanıcı bildirimlerini yapılandırma

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Windows 10 ve Windows 11'de, kötü amaçlı yazılım algılama ve düzeltmeyle ilgili uygulama bildirimleri daha güçlü, tutarlı ve kısadır. Microsoft Defender Virüsten Koruma taramalar tamamlandığında ve tehdit algılandığında uç noktalarda bildirim görüntülenir. Bildirimler, zamanlanmış ve elle tetiklenen taramaları takip eder. Bu bildirimler Bildirim Merkezi'nde **de görünür** ve tarama ve tehdit algılamalarının özeti düzenli aralıklarla görüntülenir.

Kuruluş güvenlik ekibinin bir parçasıysanız, sistemin yeniden başlatılmasını veya bir tehdit algılandığında ve düzeltişini belirten bildirimler gibi uç noktalarda bildirimlerin nasıl görüntülenmiş olduğunu yapılandırabilirsiniz.

## <a name="configure-antivirus-notifications-using-group-policy-or-the-windows-security-app"></a>Grup İlkesi'yi veya Windows Güvenliği uygulamasını kullanarak virüsten koruma Windows Güvenliği yapılandırma

Windows Güvenliği uygulamasında ve Grup İlkesi ile son tehdit algılama özetleri [gibi ek bildirimlerin](microsoft-defender-security-center-antivirus.md) görüntülenmelerini yapılandırabilirsiniz.

> [!NOTE]
> Özellik, Windows 10 1607 sürümünde Geliştirilmiş bildirimler olarak adlandırılan özellik, Windows Ayarlar Güncelleştirme  ve Güvenlik **&** \> **altında** \> **Windows Defender**. Grup İlke ve 11'Windows 10 tüm sürümleri için Grup Windows'de, bildirim özelliği Gelişmiş **bildirimler olarak adlandırılan özelliktir**.

### <a name="use-group-policy-to-disable-additional-notifications"></a>Ek bildirimleri devre dışı bırakmak için Grup İlkesi kullanma

1. Grup İlkesi yönetim bilgisayarınızda Grup İlkesi [Yönetim Konsolu'nu açın](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Yapılandırmak istediğiniz Grup İlkesi Nesnesi'ne sağ tıklayın ve Düzenle'yi **seçin**.

3. Grup İlkesi **Yönetim Düzenleyicisi'nde Bilgisayar** **yapılandırması'ne gidin**.

4. Yönetim **şablonları'ı seçin**.

5. Ağacı, rapor **Windows bileşenleri** \> **Microsoft Defender Virüsten Koruma** >  **genişletin**.

6. Gelişmiş bildirimleri **kapat'a çift tıklayın** ve seçeneği Etkin olarak **ayarlayın**. Sonra **Tamam**’ı seçin. Bu, ek bildirimlerin görünmesini önler.

> [!IMPORTANT]
> Ek bildirimleri devre dışı bırakmak tehdit algılama ve düzeltme uyarıları gibi kritik bildirimleri devre dışı bırakmaz.

### <a name="use-the-windows-security-app-to-disable-additional-notifications"></a>Ek Windows Güvenliği devre dışı bırakmak için Windows Güvenliği uygulamasını kullanma

1. Görev Windows Güvenliği kalkan simgesine tıklayarak veya başlat menüsünde Güvenlik'i arayarak Windows Güvenliği uygulamasını **açın**.

2. Virüs **koruması & kutucuğunu** (veya sol menü çubuğundaki kalkan simgesini) seçin ve ardından Virüs koruması & **ayarlarını seçin**

3. Bildirimler bölümüne kaydırın **ve Bildirim** ayarlarını **değiştir'i seçin**.

4. Ek bildirimleri devre dışı bırakmak **veya** etkinleştirmek **için** anahtarı Kapalı veya Açık olarak kaydırın.

> [!IMPORTANT]
> Ek bildirimleri devre dışı bırakmak tehdit algılama ve düzeltme uyarıları gibi kritik bildirimleri devre dışı bırakmaz.

## <a name="configure-standard-notifications-on-endpoints-using-group-policy"></a>Grup İlkesini kullanarak uç noktalarda standart bildirimleri yapılandırma

Grup İlkesi'ne kullanarak şunları kullanabilirsiniz:

- Kullanıcının bir eylem gerçekleştirmesi gerekirken uç noktalarda ek, özelleştirilmiş metin görüntüleme
- Uç noktalarda tüm bildirimleri gizleme
- Uç noktalarda yeniden başlatma bildirimlerini gizleme

Bildirimleri gizlemek, Microsoft Defender Virüsten Koruma arabiriminin tamamını gizley gizlen Microsoft Defender Virüsten Koruma olabilir. Daha [fazla bilgi için Bkz. Kullanıcıların kullanıcı arabirimini görmelerini Microsoft Defender Virüsten Koruma veya arabirimiyle](prevent-end-user-interaction-microsoft-defender-antivirus.md) etkileşim kurmasını engelleme. Bildirimlerin gizlenilmesi yalnızca ilkenin dağıtıldı olduğu uç noktalarda gerçekleşir. Izlenmesi gereken eylemlerle (örneğin, yeniden başlatma) ilgili bildirimler, pano ve raporları Microsoft Endpoint Manager Endpoint Protection [ekranda görünür](/configmgr/protect/deploy-use/monitor-endpoint-protection). 

Uç nokta bildirimlerine özel kişi bilgileri eklemek için bkz[. Windows Güvenliği uygulamayı özelleştirme](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center).

### <a name="use-group-policy-to-hide-notifications"></a>Bildirimleri gizlemek için Grup İlkesi kullanma

1. Grup İlkesi yönetim bilgisayarınızda Grup İlkesi [Yönetim Konsolu'nu açın](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Yapılandırmak istediğiniz Grup İlkesi Nesnesi'ne sağ tıklayın ve Düzenle'yi **seçin**.

3. Grup İlkesi **Yönetim Düzenleyicisi'nde Bilgisayar** **yapılandırması'ne gidin ve** Yönetim **şablonları'ı seçin**.

4. İstemci arabiriminin **bileşenlerine Windows ağacı** \> **Microsoft Defender Virüsten Koruma** \> **genişletin**. 

5. Tüm bildirimleri **gizleme'ye çift tıklayın** ve seçeneği Etkin olarak **ayarlayın**. 

6. **Tamam**'ı seçin. Bu, ek bildirimlerin görünmesini önler.

### <a name="use-group-policy-to-hide-reboot-notifications"></a>Yeniden başlatma bildirimlerini gizlemek için Grup İlkesi kullanma

1. Grup İlkesi yönetim bilgisayarınızda Grup İlkesi [Yönetim Konsolu'nu açın](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)).

2. Yapılandırmak istediğiniz Grup İlkesi Nesnesi'ne sağ tıklayın ve Düzenle'yi **seçin**.

2. Grup İlkesi **Yönetim Düzenleyicisi'nde Bilgisayar** **yapılandırması'ne gidin**.

3. Yönetim **şablonları'ne tıklayın**.

4. İstemci arabiriminin **bileşenlerine Windows ağacı** \> **Microsoft Defender Virüsten Koruma** \> **genişletin**.

5. Yeniden başlatma **bildirimlerini gizleme'ye çift tıklayın** ve seçeneği Etkin olarak **ayarlayın**. 

5. **Tamam**'ı seçin. Bu, ek bildirimlerin görünmesini önler.

