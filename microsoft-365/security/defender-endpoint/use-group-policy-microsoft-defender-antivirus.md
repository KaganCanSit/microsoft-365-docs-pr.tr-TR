---
title: Grup Microsoft Defender Virüsten Koruma ile yapılandırma
description: Uç Nokta için Microsoft Defender'da Grup İlkesi kullanarak uç Microsoft Defender Virüsten Koruma yapılandırmayı ve yönetmeyi öğrenin.
keywords: grup ilkesi, GPO, yapılandırma, ayarlar
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 01/04/2022
ms.reviewer: ksarens, jtoole, pahuijbr
manager: dansimp
ms.technology: mde
audience: ITPro
ms.topic: how-to
ms.collection: m365-security-compliance
ms.openlocfilehash: 3659f0f532b14babd256f3310c4e7da8dde67e3c
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032462"
---
# <a name="use-group-policy-settings-to-configure-and-manage-microsoft-defender-antivirus"></a>Grup İlkesi ayarlarını kullanarak grup ayarlarını yapılandırma ve Microsoft Defender Virüsten Koruma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**

- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)

Grup [İlkesi'yi kullanarak,](/windows/win32/srvnodes/group-policy) uç noktalarınıza Microsoft Defender Virüsten Koruma ve yönetebilirsiniz.

## <a name="configure-microsoft-defender-antivirus-using-group-policy"></a>Grup Microsoft Defender Virüsten Koruma kullanarak grup ayarlarını yapılandırma

Genel olarak, grup ilkesi ayarlarını yapılandırmak veya değiştirmek için Microsoft Defender Virüsten Koruma kullanabilirsiniz:

1. Grup İlkesi yönetim makinenizin Grup İlkesi Yönetim Konsolu'nu [açın, yapılandırmak](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) istediğiniz Grup İlkesi Nesnesine (GPO) sağ tıklayın ve Düzenle'ye **tıklayın**.

2. Grup İlkesi **Yönetim Düzenleyicisi'ni kullanarak** Bilgisayar **yapılandırması'ne gidin**.

3. Yönetim **şablonları'ne tıklayın**.

4. Bileşenleri ve bileşenleri Windows **için** \> **Microsoft Defender Virüsten Koruma**.

5. Yapılandırmak istediğiniz ayarı içeren bölümü genişletin (bu  konu başlığı altında, tabloda Konum olarak adlandırılır), ayarı çift tıklatın ve yapılandırma değişiklikleri yapın.

6. [Güncelleştirilmiş GPO'nun normalde olduğu gibi dağıtın](/windows/win32/srvnodes/group-policy).

## <a name="group-policy-settings-and-resources"></a>Grup İlkesi ayarları ve kaynakları

Aşağıdaki tabloda, iş yerlerinde kullanılabilen ve yaygın olarak kullanılan Grup İlkesi Windows 10.

> [!TIP]
> Grup İlkesi Başvuru Elektronik Tablosu'nda, Yönetim şablonu dosyalarına dahil edilen bilgisayar ve kullanıcı yapılandırmalarının ilke ayarlarının listelerle birlikte teslim Windows. Grup İlkesi Nesnelerini düzenlerken elektronik tablo için başvuru yapılandırabilirsiniz. <br/><br/> En son sürümler:
> - [Mayıs 2020 Ayarlar Için Grup İlkesi Windows 10 Başvuru Elektronik Tablosu (2004)](https://www.microsoft.com/download/details.aspx?id=101451)
> - [11 Ayarlar 2021 Güncelleştirmesi Windows Grup İlkesi Başvuru Elektronik Tablosu (21H2)](https://www.microsoft.com/download/details.aspx?id=103506)

<br/><br/>

|Konum|Ayar|Makale|
|---|---|---|
|İstemci arabirimi|Başsız kullanıcı arabirimi modunu etkinleştirme|[Kullanıcıların kullanıcı arabirimini görmelerini veya Microsoft Defender Virüsten Koruma engelleme](prevent-end-user-interaction-microsoft-defender-antivirus.md)|
|İstemci arabirimi|Bir eylem gerçekleştirmeleri gereken istemcilere ek metin görüntüleme|[Uç noktalarda görünen bildirimleri yapılandırma](configure-notifications-microsoft-defender-antivirus.md)|
|İstemci arabirimi|Tüm bildirimlerin ılması|[Uç noktalarda görünen bildirimleri yapılandırma](configure-notifications-microsoft-defender-antivirus.md)|
|İstemci arabirimi|Yeniden başlatma bildirimlerini bastırıyor|[Uç noktalarda görünen bildirimleri yapılandırma](configure-notifications-microsoft-defender-antivirus.md)|
|Dışlamalar|Uzantı Dışlamaları|[Taramalarda dışlamaları yapılandırma Microsoft Defender Virüsten Koruma doğrulama](configure-exclusions-microsoft-defender-antivirus.md)|
|Dışlamalar|Yol Dışlamaları|[Taramalarda dışlamaları yapılandırma Microsoft Defender Virüsten Koruma doğrulama](configure-exclusions-microsoft-defender-antivirus.md)|
|Dışlamalar|İşlem Dışlamaları|[Taramalarda dışlamaları yapılandırma Microsoft Defender Virüsten Koruma doğrulama](configure-exclusions-microsoft-defender-antivirus.md)|
|Dışlamalar|Otomatik Dışlamaları kapatma|[Taramalarda dışlamaları yapılandırma Microsoft Defender Virüsten Koruma doğrulama](configure-exclusions-microsoft-defender-antivirus.md)|
|HARITALAR|'İlk Görüşte Blok' özelliğini yapılandırma|[İlk görüşte engellemeyi etkinleştir](configure-block-at-first-sight-microsoft-defender-antivirus.md)|
|HARITALAR|Microsoft MAPS'a katılma|[Bulut teslimi korumasını etkinleştirme](enable-cloud-protection-microsoft-defender-antivirus.md)|
|HARITALAR|Daha fazla çözümleme gerektiğinde dosya örnekleri gönderme|[Bulut teslimi korumasını etkinleştirme](enable-cloud-protection-microsoft-defender-antivirus.md)|
|HARITALAR|Microsoft MAPS'a raporlama için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya buna izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|MpEngine|Genişletilmiş bulut denetimi yapılandırma|[Bulut engelleme zaman aşımı dönemini yapılandırma](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md)|
|MpEngine|Bulut koruma düzeyini seçme|[Bulut teslimi koruma düzeyini belirtme](specify-cloud-protection-level-microsoft-defender-antivirus.md)|
|Ağ denetleme sistemi|Ağ trafiği incelemesi için ek tanım kümeleri belirtme| Kullanılmadı (kullanımdan kullanımdan) |
|Ağ denetleme sistemi|Tanımın sonlarını kapatma| Kullanılmadı (kullanımdan kullanımdan)|
|Ağ denetleme sistemi|Protokol tanımayı açma| Kullanılmadı (kullanımdan kullanımdan)|
|Karantina|Öğeleri Karantina klasöründen kaldırma işlemi için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya buna izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Karantina|Öğeleri Karantina klasöründen kaldırmayı yapılandırma|[Taramalar için düzeltme Microsoft Defender Virüsten Koruma yapılandırma](configure-remediation-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|Bilgisayarınızda dosyayı ve program etkinliğini izlemek için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya buna izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|Gelen ve giden dosya etkinliğini izlemek için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya buna izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|İndirilen tüm dosyaları ve ekleri taramak için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya buna izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|Davranış izlemeyi açmak için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya buna izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|Gerçek zamanlı korumayı açmak için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya buna izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|İndirilen dosya ve eklerin taranacak en büyük boyutunu tanımlama|[Her zaman açık koruma Microsoft Defender Virüsten Koruma izlemeyi etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|Bilgisayarınızda dosya ve program etkinliğini izleme|[Her zaman açık koruma Microsoft Defender Virüsten Koruma izlemeyi etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|İndirilen tüm dosyaları ve ekleri tarama|[Her zaman açık koruma Microsoft Defender Virüsten Koruma izlemeyi etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|Gerçek zamanlı korumayı kapatma|[Her zaman açık koruma Microsoft Defender Virüsten Koruma izlemeyi etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|Davranış izlemeyi açma|[Her zaman açık koruma Microsoft Defender Virüsten Koruma izlemeyi etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|Gerçek zamanlı koruma etkinleştirildiğinde süreç taramasını açma|[Her zaman açık koruma Microsoft Defender Virüsten Koruma izlemeyi etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|Ham hacim yazma bildirimlerini açma|[Her zaman açık koruma Microsoft Defender Virüsten Koruma izlemeyi etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|Gelen ve giden dosya ve program etkinliği için izlemeyi yapılandırma|[Her zaman açık koruma Microsoft Defender Virüsten Koruma izlemeyi etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Düzeltme|Düzeltmeyi tamamlamak üzere zamanlanmış bir tam tarama çalıştırmak için günün saati için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya buna izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Düzeltme|Düzeltmeyi tamamlamak için zamanlanmış bir tam tarama çalıştırmak için haftanın günlerini belirtme|[Zamanlanmış taramaları Microsoft Defender Virüsten Koruma yapılandırma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Düzeltme|Düzeltmeyi tamamlamak için zamanlanmış bir tam tarama çalıştırmak için günün saatlerini belirtme|[Zamanlanmış taramaları Microsoft Defender Virüsten Koruma yapılandırma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Raporlama|Gelişmiş bildirimleri kapatma|[Uç noktalarda görünen bildirimleri yapılandırma](configure-notifications-microsoft-defender-antivirus.md)
|Kök|E-Microsoft Defender Virüsten Koruma|Kullanılmadı. Microsoft dışı bir virüsten koruma ürünü kullanıyor veya kullanmayı planlıyorsanız, diğer [güvenlik Microsoft Defender Virüsten Koruma uyumluluk sorunlarına bakın](microsoft-defender-antivirus-compatibility.md).|
|Kök|Proxy sunucusunu atlamak için adresleri tanımlama|[Cihaz ara sunucusunu ve İnternet bağlantısı ayarlarını yapılandırma](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|Kök|Ağa bağlanmak için proxy otomatik yapılandırmayı (.pac) tanımlama|[Cihaz ara sunucusunu ve İnternet bağlantısı ayarlarını yapılandırma](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|Kök|Ağa bağlanmak için ara sunucu tanımlama|[Cihaz ara sunucusunu ve İnternet bağlantısı ayarlarını yapılandırma](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|Kök|Listeler için yerel yönetici birleştirme davranışını yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya buna izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Kök|Kötü amaçlı yazılımdan koruma hizmetinin normal önceliğe sahip olarak başlamasına izin verme|[Taramalar için düzeltme Microsoft Defender Virüsten Koruma yapılandırma](configure-remediation-microsoft-defender-antivirus.md)|
|Kök|Kötü amaçlı yazılımdan koruma hizmetinin her zaman çalışıyor olmasına izin ver|[Taramalar için düzeltme Microsoft Defender Virüsten Koruma yapılandırma](configure-remediation-microsoft-defender-antivirus.md)|
|Kök|Düzenli düzeltmeyi kapatma|[Taramalar için düzeltme Microsoft Defender Virüsten Koruma yapılandırma](configure-remediation-microsoft-defender-antivirus.md)|
|Kök|Zamanlanmış görev zamanlarını rastgeleleştirme|[Arama için zamanlanmış taramaları Microsoft Defender Virüsten Koruma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Tarama|Kullanıcıların taramayı duraklatmalarına izin ver|[Kullanıcıların kullanıcı arabirimini görmelerini veya Microsoft Defender Virüsten Koruma etkileşim kurmasını](prevent-end-user-interaction-microsoft-defender-antivirus.md) engelleme (Kullanıcı arabiriminde Windows 10)|
|Tarama|Zamanlanmış taramayı çalıştırmadan önce en son virüs ve casus yazılım tanımlarını denetleme|[Olay tabanlı zorunlu güncelleştirmeleri yönetme](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Tarama|Bir taramanın kaç gün sonra zorlanacaklarını tanımlayın|[Güncel olan uç nokta güncelleştirmelerini yönetme](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Tarama|Tam taramayı yakalamayı aç|[Güncel olan uç nokta güncelleştirmelerini yönetme](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Tarama|Hızlı taramayı yakalamayı açma|[Güncel olan uç nokta güncelleştirmelerini yönetme](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Tarama|CPU kullanımının en yüksek yüzdesi için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya buna izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Tarama|Zamanlama tarama günü için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya buna izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Tarama|Zamanlanan hızlı tarama zamanı için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya buna izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Tarama|Zamanlanan tarama zamanı için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya buna izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Tarama|Zamanlanmış taramada kullanmak üzere tarama türü için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya buna izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Tarama|Sistem geri yükleme noktası oluşturma|[Taramalar için düzeltme Microsoft Defender Virüsten Koruma yapılandırma](configure-remediation-microsoft-defender-antivirus.md)|
|Tarama|Tarama geçmişi klasöründen öğeleri kaldırmayı açma|[Taramalar için düzeltme Microsoft Defender Virüsten Koruma yapılandırma](configure-remediation-microsoft-defender-antivirus.md)|
|Tarama|Heuristics'i açma|[Her zaman açık koruma Microsoft Defender Virüsten Koruma izlemeyi etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Tarama|E-posta taramayı açma|[E-postada tarama seçeneklerini Microsoft Defender Virüsten Koruma](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Tarama|Yeniden nokta taramayı açma|[E-postada tarama seçeneklerini Microsoft Defender Virüsten Koruma](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Tarama|Eşlenmiş ağ sürücülerinde tam taramayı çalıştırma|[E-postada tarama seçeneklerini Microsoft Defender Virüsten Koruma](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Tarama|Arşiv dosyalarını tarama|[E-postada tarama seçeneklerini Microsoft Defender Virüsten Koruma](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Tarama|Ağ dosyalarını tarama|[E-postada tarama seçeneklerini Microsoft Defender Virüsten Koruma](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Tarama|Paketlenmiş yürütülebilir dosyaları tarama|[E-postada tarama seçeneklerini Microsoft Defender Virüsten Koruma](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
| Tarama | Betikleri tarama | [E-postada tarama seçeneklerini Microsoft Defender Virüsten Koruma](configure-advanced-scan-types-microsoft-defender-antivirus.md) <p>Ayrıca bkz [. Defender/AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender).|
|Tarama|Çıkarılabilir sürücüleri tarama|[E-postada tarama seçeneklerini Microsoft Defender Virüsten Koruma](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Tarama|Arşiv dosyalarını taramak için en fazla derinlik belirtme|[E-postada tarama seçeneklerini Microsoft Defender Virüsten Koruma](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Tarama|Tarama sırasında CPU kullanımının en yüksek yüzdesini belirtme|[E-postada tarama seçeneklerini Microsoft Defender Virüsten Koruma](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Tarama|Taranacak arşiv dosyalarının boyut üst boyutunu belirtme|[E-postada tarama seçeneklerini Microsoft Defender Virüsten Koruma](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Tarama|Zamanlanmış taramayı çalıştırmak için haftanın günlerini belirtme|[Arama için zamanlanmış taramaları Microsoft Defender Virüsten Koruma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Tarama|Günde hızlı taramalar çalıştırmak için aralığı belirtme|[Arama için zamanlanmış taramaları Microsoft Defender Virüsten Koruma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Tarama|Zamanlanmış taramada kullanmak üzere tarama türünü belirtme|[Arama için zamanlanmış taramaları Microsoft Defender Virüsten Koruma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Tarama|Günlük hızlı tarama için saati belirtme|[Arama için zamanlanmış taramaları Microsoft Defender Virüsten Koruma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Tarama|Zamanlanmış taramayı çalıştırmak için günün saatlerini belirtme|[Arama için zamanlanmış taramaları Microsoft Defender Virüsten Koruma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Tarama|Zamanlanmış taramayı yalnızca bilgisayar üzerindeyken ama kullanımda değilken başlatma|[Arama için zamanlanmış taramaları Microsoft Defender Virüsten Koruma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Güvenlik zekası güncelleştirmeleri|Microsoft Update'in güvenlik zekası güncelleştirmelerine izin verme|[Mobil cihazlar ve sanal makineler (VM) güncelleştirmelerini yönetme](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)|
|Güvenlik zekası güncelleştirmeleri|Pil gücüyle çalışan güvenlik zekası güncelleştirmelerine izin ver|[Mobil cihazlar ve sanal makineler (VM) güncelleştirmelerini yönetme](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)|
|Güvenlik zekası güncelleştirmeleri|Microsoft MAPS'a tanım tabanlı raporları devre dışı bırakmak için bildirimlere izin verme|[Olay tabanlı zorunlu güncelleştirmeleri yönetme](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Güvenlik zekası güncelleştirmeleri|Microsoft HARITALAR'a raporlara dayalı olarak gerçek zamanlı güvenlik zekası güncelleştirmelerine izin verme|[Olay tabanlı zorunlu güncelleştirmeleri yönetme](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Güvenlik zekası güncelleştirmeleri|Başlangıçtaki en son virüs ve casus yazılım tanımlarını denetleme|[Olay tabanlı zorunlu güncelleştirmeleri yönetme](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Güvenlik zekası güncelleştirmeleri|Güvenlik zekası güncelleştirmelerini indirmek için dosya paylaşımlarını tanımlama|[Akıllı Microsoft Defender Virüsten Koruma ve güvenlik zekası güncelleştirmelerini yönetme](manage-protection-updates-microsoft-defender-antivirus.md)|
|Güvenlik zekası güncelleştirmeleri|Güvenlik zekası güncelleştirmesini yakalamak için kaç gün sonra gerek olduğunu tanımlayın|[Güncel olan uç nokta güncelleştirmelerini yönetme](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Güvenlik zekası güncelleştirmeleri|Casus yazılım tanımlarının tarihi geri alınmadan önceki gün sayısını tanımlama|[Güncel olan uç nokta güncelleştirmelerini yönetme](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Güvenlik zekası güncelleştirmeleri|Virüs tanımlarının tarihi geri alınmadan önceki gün sayısını tanımlama|[Güncel olan uç nokta güncelleştirmelerini yönetme](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Güvenlik zekası güncelleştirmeleri|Güvenlik zekası güncelleştirmelerini indirmek için kaynakların sıralamalarını tanımlama|[Akıllı Microsoft Defender Virüsten Koruma ve güvenlik zekası güncelleştirmelerini yönetme](manage-protection-updates-microsoft-defender-antivirus.md)|
|Güvenlik zekası güncelleştirmeleri|Başlatma sırasında güvenlik zekası güncelleştirmesini başlatma|[Olay tabanlı zorunlu güncelleştirmeleri yönetme](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Güvenlik zekası güncelleştirmeleri|Güvenlik zekası güncelleştirmelerini kontrol etmek için haftanın günlerini belirtme|[Koruma güncelleştirmelerinin ne zaman indirilecek ve uygulanmayacaklarını yönetme](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|Güvenlik zekası güncelleştirmeleri|Güvenlik zekası güncelleştirmelerini denetleme aralığını belirtme|[Koruma güncelleştirmelerinin ne zaman indirilecek ve uygulanmayacaklarını yönetme](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|Güvenlik zekası güncelleştirmeleri|Güvenlik zekası güncelleştirmelerini denetleme zamanı belirtme|[Koruma güncelleştirmelerinin ne zaman indirilecek ve uygulanmayacaklarını yönetme](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|Güvenlik zekası güncelleştirmeleri|Güvenlik zekası güncelleştirmesi sonrasında taramayı açma|[Arama için zamanlanmış taramaları Microsoft Defender Virüsten Koruma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Tehdit|Algılandığında varsayılan eylemin alınmayacak tehdit uyarı düzeylerini belirtme|[Taramalar için düzeltme Microsoft Defender Virüsten Koruma yapılandırma](configure-remediation-microsoft-defender-antivirus.md)|
|Tehdit|Algılandığında varsayılan eylemin alınmayacak tehditlerini belirtme|[Taramalar için düzeltme Microsoft Defender Virüsten Koruma yapılandırma](configure-remediation-microsoft-defender-antivirus.md)|


## <a name="see-also"></a>Ayrıca bkz.

- [Yönetim ve yapılandırma araçları için başvuru konuları](configuration-management-reference-microsoft-defender-antivirus.md)
- [Microsoft Defender Virüsten Koruma'da Windows 10](microsoft-defender-antivirus-in-windows-10.md)
