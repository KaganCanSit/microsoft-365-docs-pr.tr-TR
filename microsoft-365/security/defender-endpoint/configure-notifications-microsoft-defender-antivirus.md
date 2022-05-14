---
title: Microsoft Defender Virüsten Koruma bildirimlerini yapılandırma
description: Uç noktalarda hem standart hem de diğer Microsoft Defender Virüsten Koruma bildirimlerini yapılandırmayı ve özelleştirmeyi öğrenin.
keywords: bildirimler, defender, virüsten koruma, uç nokta, yönetim, yönetici
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
ms.openlocfilehash: 6c9dfd603a128de4a94c9cf49faa6ba9ca940d9b
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418192"
---
# <a name="configure-microsoft-defender-antivirus-notifications-that-appear-on-endpoints"></a>Uç noktalarda görünen Microsoft Defender Virüsten Koruma bildirimlerini yapılandırma

**Şunlar için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

Windows 10 ve Windows 11,kötü amaçlı yazılım algılama ve düzeltme hakkında uygulama bildirimleri daha sağlam, tutarlı ve kısadır. taramalar tamamlandığında ve tehditler algılandığında uç noktalarda Microsoft Defender Virüsten Koruma bildirimleri görüntülenir. Bildirimler hem zamanlanmış hem de el ile tetiklenen taramaları izler. Bu bildirimler **Bildirim Merkezi'nde** de görünür ve taramaların ve tehdit algılamalarının bir özeti düzenli aralıklarla görüntülenir.

Kuruluşunuzun güvenlik ekibinin bir parçasıysanız, sistemin yeniden başlatılmasını isteyen veya bir tehdidin algılanıp düzeltildiğini belirten bildirimler gibi bildirimlerin uç noktalarda nasıl görüneceğini yapılandırabilirsiniz.

## <a name="configure-antivirus-notifications-using-group-policy-or-the-windows-security-app"></a>grup ilkesi veya Windows Güvenliği uygulamasını kullanarak virüsten koruma bildirimlerini yapılandırma

Son tehdit algılama özetleri gibi ek bildirimlerin görüntülenmesini [Windows Güvenliği uygulamasında ve grup ilkesi](microsoft-defender-security-center-antivirus.md) ile yapılandırabilirsiniz.

> [!NOTE]
> Windows 10 sürüm 1607'de özellik **Gelişmiş bildirimler** olarak adlandırıldı ve **Windows Ayarlar** \> **Güncelleştirme & güvenlik** \> **Windows Defender** altında yapılandırıldı. tüm Windows 10 ve Windows 11 sürümleri için grup ilkesi ayarlarında, bildirim özelliği **Gelişmiş bildirimler** olarak adlandırılır.

### <a name="use-group-policy-to-disable-additional-notifications"></a>Ek bildirimleri devre dışı bırakmak için grup ilkesi kullanma

1. grup ilkesi yönetim bilgisayarınızda [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın.

2. Yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **düzenle'yi** seçin.

3. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na** gidin.

4. **Yönetim şablonları'nı** seçin.

5. Microsoft Defender Virüsten Koruma **Reporting** **bileşenlerini** \> **Windows** >  için ağacı genişletin.

6. **Gelişmiş bildirimleri kapat'a** çift tıklayın ve seçeneği **Etkin** olarak ayarlayın. Sonra **Tamam**’ı seçin. Bu, ek bildirimlerin görünmesini engeller.

> [!IMPORTANT]
> Ek bildirimleri devre dışı bırakmak, tehdit algılama ve düzeltme uyarıları gibi kritik bildirimleri devre dışı bırakmaz.

### <a name="use-the-windows-security-app-to-disable-additional-notifications"></a>Ek bildirimleri devre dışı bırakmak için Windows Güvenliği uygulamasını kullanma

1. Görev çubuğundaki kalkan simgesine tıklayarak veya başlangıç menüsünde **Güvenlik** araması yaparak Windows Güvenliği uygulamasını açın.

2. **Virüs & tehdit koruması** kutucuğunu (veya sol menü çubuğundaki kalkan simgesini) ve ardından **Virüs & tehdit koruması ayarları'nı** seçin

3. **Bildirimler** bölümüne gidin ve **Bildirim ayarlarını değiştir'i** seçin.

4. Ek bildirimleri devre dışı bırakmak veya etkinleştirmek için anahtarı **Kapalı** veya **Açık** olarak kaydırın.

> [!IMPORTANT]
> Ek bildirimleri devre dışı bırakmak, tehdit algılama ve düzeltme uyarıları gibi kritik bildirimleri devre dışı bırakmaz.

## <a name="configure-standard-notifications-on-endpoints-using-group-policy"></a>grup ilkesi kullanarak uç noktalarda standart bildirimleri yapılandırma

grup ilkesi kullanarak:

- Kullanıcının bir eylem gerçekleştirmesi gerektiğinde uç noktalarda ek, özelleştirilmiş metin görüntüleme
- Uç noktalardaki tüm bildirimleri gizleme
- Uç noktalarda yeniden başlatma bildirimlerini gizleme

Bildirimleri gizlemek, Microsoft Defender Virüsten Koruma arabiriminin tamamını gizleyememenize neden olan durumlarda yararlı olabilir. Daha fazla bilgi için bkz. [Kullanıcıların Microsoft Defender Virüsten Koruma kullanıcı arabirimini görmesini veya bunlarla etkileşim kurmasını engelleme](prevent-end-user-interaction-microsoft-defender-antivirus.md). Bildirimleri gizleme işlemi yalnızca ilkenin dağıtıldığı uç noktalarda gerçekleşir. Yapılması gereken eylemlerle ilgili bildirimler (yeniden başlatma gibi) [Microsoft Endpoint Manager Endpoint Protection izleme panosunda ve raporlarda görünmeye](/configmgr/protect/deploy-use/monitor-endpoint-protection) devam eder. 

Uç nokta bildirimlerine özel kişi bilgileri eklemek için bkz. [Kuruluşunuz için Windows Güvenliği uygulamasını özelleştirme](/windows/security/threat-protection/windows-defender-security-center/windows-defender-security-center).

### <a name="use-group-policy-to-hide-notifications"></a>Bildirimleri gizlemek için grup ilkesi kullanma

1. grup ilkesi yönetim bilgisayarınızda [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın.

2. Yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **düzenle'yi** seçin.

3. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na** gidin ve **ardından Yönetim şablonları'nı** seçin.

4. **İstemci arabirimi** **Microsoft Defender Virüsten Koruma bileşenleri** \> **Windows** \> için ağacı genişletin. 

5. **Tüm bildirimleri gizle'ye** çift tıklayın ve seçeneği **Etkin** olarak ayarlayın. 

6. **Tamam**'ı seçin. Bu, ek bildirimlerin görünmesini engeller.

### <a name="use-group-policy-to-hide-reboot-notifications"></a>Yeniden başlatma bildirimlerini gizlemek için grup ilkesi kullanma

1. grup ilkesi yönetim bilgisayarınızda [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın.

2. Yapılandırmak istediğiniz grup ilkesi Nesnesine sağ tıklayın ve **düzenle'yi** seçin.

2. **grup ilkesi Yönetim Düzenleyicisi'nde** **Bilgisayar yapılandırması'na** gidin.

3. **Yönetim şablonları'nı** tıklatın.

4. **İstemci arabirimi** **Microsoft Defender Virüsten Koruma bileşenleri** \> **Windows** \> için ağacı genişletin.

5. **Yeniden başlatma bildirimlerini gizle'ye** çift tıklayın ve seçeneği **Etkin** olarak ayarlayın. 

5. **Tamam**'ı seçin. Bu, ek bildirimlerin görünmesini engeller.

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [MacOS'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender için macOS Virüsten Koruma ilke ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Uç Nokta için Microsoft Defender tercihlerini ayarlayın](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android özelliklerinde Uç Nokta için Defender’ı yapılandırın](android-configure.md)
> - [iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın](ios-configure-features.md)