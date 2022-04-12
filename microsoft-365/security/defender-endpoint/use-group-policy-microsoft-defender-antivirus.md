---
title: grup ilkesi ile Microsoft Defender Virüsten Koruma yapılandırma
description: Pertahanan Microsoft untuk Titik Akhir uç noktalarınızda Microsoft Defender Virüsten Koruma yapılandırmak ve yönetmek için grup ilkesi kullanmayı öğrenin.
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
ms.openlocfilehash: e8cda6f387814ed6ec613db8cb53ff030243a92b
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64789438"
---
# <a name="use-group-policy-settings-to-configure-and-manage-microsoft-defender-antivirus"></a>Microsoft Defender Virüsten Koruma yapılandırmak ve yönetmek için grup ilkesi ayarlarını kullanma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Şunlar için geçerlidir:**

- [Pertahanan Microsoft untuk Titik Akhir Plan 1](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- Microsoft Defender Virüsten Koruma

**Platform**
- Windows

uç noktalarınızdaki [Microsoft Defender Virüsten Koruma](/windows/win32/srvnodes/group-policy) yapılandırmak ve yönetmek için grup ilkesi kullanabilirsiniz.

## <a name="configure-microsoft-defender-antivirus-using-group-policy"></a>grup ilkesi kullanarak Microsoft Defender Virüsten Koruma yapılandırma

Genel olarak, Microsoft Defender Virüsten Koruma grup ilkesi ayarlarını yapılandırmak veya değiştirmek için aşağıdaki yordamı kullanabilirsiniz:

1. grup ilkesi yönetim makinenizde [grup ilkesi Yönetim Konsolu'nu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)) açın, yapılandırmak istediğiniz grup ilkesi Nesnesine (GPO) sağ tıklayın ve **Düzenle'ye** tıklayın.

2. **grup ilkesi Yönetim Düzenleyicisi'ni** kullanarak **Bilgisayar yapılandırması'na** gidin.

3. **Yönetim şablonları'nı** tıklatın.

4. Microsoft Defender Virüsten Koruma **bileşenleri** \> Windows için ağacı **genişletin.**

5. Yapılandırmak istediğiniz ayarı içeren bölümü (bu konudaki tabloda **Konum** olarak adlandırılır) genişletin, açmak için ayara çift tıklayın ve yapılandırma değişiklikleri yapın.

6. [Güncelleştirilmiş GPO'ları normalde yaptığınız gibi dağıtın](/windows/win32/srvnodes/group-policy).

## <a name="group-policy-settings-and-resources"></a>grup ilkesi ayarları ve kaynakları

Aşağıdaki tabloda, Windows 10'de yaygın olarak kullanılan grup ilkesi ayarları listelenir.

> [!TIP]
> Windows için teslim edilen Yönetim şablonu dosyalarına dahil edilen bilgisayar ve kullanıcı yapılandırmaları için ilke ayarlarını listeleyen grup ilkesi Başvuru Elektronik Tablosu'nı indirin. grup ilkesi Nesneleri düzenlerken elektronik tabloya başvurmayı yapılandırabilirsiniz. <br/><br/> En son sürümler şunlardır:
> - [Windows 10 Mayıs 2020 Güncelleştirmesi (2004) için grup ilkesi Ayarlar Başvuru Elektronik Tablosu](https://www.microsoft.com/download/details.aspx?id=101451)
> - [Windows 11 Ekim 2021 Güncelleştirmesi (21H2) için grup ilkesi Ayarlar Başvuru Elektronik Tablosu](https://www.microsoft.com/download/details.aspx?id=103506)

<br/><br/>

|Konum|Ayar|Makale|
|---|---|---|
|İstemci arabirimi|Başsız kullanıcı arabirimi modunu etkinleştirme|[Kullanıcıların Microsoft Defender Virüsten Koruma kullanıcı arabirimini görmesini veya bu arabirimle etkileşim kurmasını engelleme](prevent-end-user-interaction-microsoft-defender-antivirus.md)|
|İstemci arabirimi|Bir eylem gerçekleştirmeleri gerektiğinde istemcilere ek metin görüntüleme|[Uç noktalarda görünen bildirimleri yapılandırın](configure-notifications-microsoft-defender-antivirus.md)|
|İstemci arabirimi|Tüm bildirimleri gizleme|[Uç noktalarda görünen bildirimleri yapılandırın](configure-notifications-microsoft-defender-antivirus.md)|
|İstemci arabirimi|Yeniden başlatma bildirimlerini gizler|[Uç noktalarda görünen bildirimleri yapılandırın](configure-notifications-microsoft-defender-antivirus.md)|
|Dışlamalar|Uzantı Dışlamaları|[Microsoft Defender Virüsten Koruma taramalarında dışlamaları yapılandırma ve doğrulama](configure-exclusions-microsoft-defender-antivirus.md)|
|Dışlamalar|Yol Dışlamaları|[Microsoft Defender Virüsten Koruma taramalarında dışlamaları yapılandırma ve doğrulama](configure-exclusions-microsoft-defender-antivirus.md)|
|Dışlamalar|İşlem Dışlamaları|[Microsoft Defender Virüsten Koruma taramalarında dışlamaları yapılandırma ve doğrulama](configure-exclusions-microsoft-defender-antivirus.md)|
|Dışlamalar|Otomatik Dışlamaları kapatma|[Microsoft Defender Virüsten Koruma taramalarında dışlamaları yapılandırma ve doğrulama](configure-exclusions-microsoft-defender-antivirus.md)|
|HARİTALAR|'İlk Bakışta Engelle' özelliğini yapılandırma|[İlk bakışta bloğu etkinleştir](configure-block-at-first-sight-microsoft-defender-antivirus.md)|
|HARİTALAR|Microsoft MAPS'e katılma|[Bulut tabanlı korumayı etkinleştirme](enable-cloud-protection-microsoft-defender-antivirus.md)|
|HARİTALAR|Daha fazla analiz gerektiğinde dosya örnekleri gönderme|[Bulut tabanlı korumayı etkinleştirme](enable-cloud-protection-microsoft-defender-antivirus.md)|
|HARİTALAR|Microsoft MAPS'e raporlama için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|MpEngine|Genişletilmiş bulut denetimini yapılandırma|[Bulut engelleme zaman aşımı dönemini yapılandırın](configure-cloud-block-timeout-period-microsoft-defender-antivirus.md)|
|MpEngine|Bulut koruma düzeyini seçin|[Bulut tabanlı koruma düzeyini belirtme](specify-cloud-protection-level-microsoft-defender-antivirus.md)|
|Ağ inceleme sistemi|Ağ trafiği denetimi için ek tanım kümeleri belirtme| Kullanılmıyor (kullanım dışı) |
|Ağ inceleme sistemi|Tanımın kullanımdan kaldırılmasını açma| Kullanılmıyor (kullanım dışı)|
|Ağ inceleme sistemi|Protokol tanımayı açma| Kullanılmıyor (kullanım dışı)|
|Karantina|Öğelerin Karantina klasöründen kaldırılması için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Karantina|Karantina klasöründeki öğelerin kaldırılmasını yapılandırma|[Microsoft Defender Virüsten Koruma taramaları için düzeltmeyi yapılandırma](configure-remediation-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|Bilgisayarınızda dosya ve program etkinliğini izlemek için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|Gelen ve giden dosya etkinliği için izleme için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|İndirilen tüm dosya ve ekleri taramak için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|Davranış izlemeyi açmak için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|Gerçek zamanlı korumayı açmak için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|Taranacak indirilen dosyaların ve eklerin en büyük boyutunu tanımlama|[Microsoft Defender Virüsten Koruma her zaman açık korumayı ve izlemeyi etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|Bilgisayarınızda dosya ve program etkinliğini izleme|[Microsoft Defender Virüsten Koruma her zaman açık korumayı ve izlemeyi etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|İndirilen tüm dosyaları ve ekleri tara|[Microsoft Defender Virüsten Koruma her zaman açık korumayı ve izlemeyi etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|Gerçek zamanlı korumayı kapatma|[Microsoft Defender Virüsten Koruma her zaman açık korumayı ve izlemeyi etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|Davranış izlemeyi açma|[Microsoft Defender Virüsten Koruma her zaman açık korumayı ve izlemeyi etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|Gerçek zamanlı koruma etkinleştirildiğinde işlem taramasını açma|[Microsoft Defender Virüsten Koruma her zaman açık korumayı ve izlemeyi etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|Ham birim yazma bildirimlerini açma|[Microsoft Defender Virüsten Koruma her zaman açık korumayı ve izlemeyi etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Gerçek zamanlı koruma|Gelen ve giden dosya ve program etkinliği için izlemeyi yapılandırma|[Microsoft Defender Virüsten Koruma her zaman açık korumayı ve izlemeyi etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Düzeltme|Düzeltmeyi tamamlamak için zamanlanmış bir tam tarama çalıştırmak üzere günün saati için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Düzeltme|Düzeltmeyi tamamlamak için zamanlanmış bir tam tarama çalıştırmak için haftanın gününü belirtin|[Zamanlanmış Microsoft Defender Virüsten Koruma taramalarını yapılandırma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Düzeltme|Düzeltmeyi tamamlamak için zamanlanmış bir tam tarama çalıştırmak için günün saatini belirtin|[Zamanlanmış Microsoft Defender Virüsten Koruma taramalarını yapılandırma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Raporlama|Gelişmiş bildirimleri kapatma|[Uç noktalarda görünen bildirimleri yapılandırın](configure-notifications-microsoft-defender-antivirus.md)
|Kök|Microsoft Defender Virüsten Koruma kapatma|Kullanılmıyor. Microsoft dışı bir virüsten koruma ürünü kullanıyorsanız veya kullanmayı planlıyorsanız bkz. [Diğer güvenlik ürünleriyle uyumluluk Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-compatibility.md).|
|Kök|Proxy sunucusunu atlamak için adresleri tanımlama|[Cihaz ara sunucusu ve İnternet bağlantısı ayarlarını yapılandırma](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|Kök|Ağa bağlanmak için ara sunucu otomatik yapılandırması (.pac) tanımlama|[Cihaz ara sunucusu ve İnternet bağlantısı ayarlarını yapılandırma](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|Kök|Ağa bağlanmak için ara sunucu tanımlama|[Cihaz ara sunucusu ve İnternet bağlantısı ayarlarını yapılandırma](configure-proxy-internet.md#configure-a-static-proxy-for-microsoft-defender-antivirus)|
|Kök|Listeler için yerel yönetici birleştirme davranışını yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Kök|Kötü amaçlı yazılımdan koruma hizmetinin normal öncelikle başlatılmasına izin ver|[Microsoft Defender Virüsten Koruma taramaları için düzeltmeyi yapılandırma](configure-remediation-microsoft-defender-antivirus.md)|
|Kök|Kötü amaçlı yazılımdan koruma hizmetinin her zaman çalışır durumda kalmasına izin ver|[Microsoft Defender Virüsten Koruma taramaları için düzeltmeyi yapılandırma](configure-remediation-microsoft-defender-antivirus.md)|
|Kök|Rutin düzeltmeyi kapatma|[Microsoft Defender Virüsten Koruma taramaları için düzeltmeyi yapılandırma](configure-remediation-microsoft-defender-antivirus.md)|
|Kök|Zamanlanmış görev sürelerini rastgele belirleme|[Microsoft Defender Virüsten Koruma için zamanlanmış taramaları yapılandırma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Tarama|Kullanıcıların taramayı duraklatmasına izin ver|[Kullanıcıların Microsoft Defender Virüsten Koruma kullanıcı arabirimini görmesini veya bunlarla etkileşim kurmasını engelleme](prevent-end-user-interaction-microsoft-defender-antivirus.md) (Windows 10 desteklenmez)|
|Tarama|Zamanlanmış tarama çalıştırmadan önce en son virüs ve casus yazılım tanımlarını denetleyin|[Olay tabanlı zorunlu güncelleştirmeleri yönetin](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Tarama|Yakalama taramasının zorlandığı gün sayısını tanımlama|[Güncel olmayan uç noktalar için güncelleştirmeleri yönetme](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Tarama|Tam taramayı yakalama özelliğini açma|[Güncel olmayan uç noktalar için güncelleştirmeleri yönetme](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Tarama|Hızlı taramayı yakalama özelliğini açma|[Güncel olmayan uç noktalar için güncelleştirmeleri yönetme](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Tarama|Cpu kullanım yüzdesi üst sınırı için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Tarama|Zamanlama tarama günü için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Tarama|Zamanlanmış hızlı tarama süresi için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Tarama|Zamanlanmış tarama süresi için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Tarama|Zamanlanmış tarama için kullanılacak tarama türü için yerel ayarı geçersiz kılmayı yapılandırma|[Kullanıcıların ilke ayarlarını yerel olarak değiştirmesini engelleme veya izin verme](configure-local-policy-overrides-microsoft-defender-antivirus.md)|
|Tarama|Sistem geri yükleme noktası oluşturma|[Microsoft Defender Virüsten Koruma taramaları için düzeltmeyi yapılandırma](configure-remediation-microsoft-defender-antivirus.md)|
|Tarama|Tarama geçmişi klasöründeki öğelerin kaldırılmasını açma|[Microsoft Defender Virüsten Koruma taramaları için düzeltmeyi yapılandırma](configure-remediation-microsoft-defender-antivirus.md)|
|Tarama|Buluşsal yöntemleri açma|[Microsoft Defender Virüsten Koruma her zaman açık korumayı ve izlemeyi etkinleştirme ve yapılandırma](configure-real-time-protection-microsoft-defender-antivirus.md)|
|Tarama|E-posta taramayı açma|[Microsoft Defender Virüsten Koruma'de tarama seçeneklerini yapılandırma](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Tarama|Yeniden ayrıştırma noktası taramayı açma|[Microsoft Defender Virüsten Koruma'de tarama seçeneklerini yapılandırma](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Tarama|Eşlenen ağ sürücülerinde tam tarama çalıştırma|[Microsoft Defender Virüsten Koruma'de tarama seçeneklerini yapılandırma](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Tarama|Arşiv dosyalarını tarama|[Microsoft Defender Virüsten Koruma'de tarama seçeneklerini yapılandırma](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Tarama|Ağ dosyalarını tarama|[Microsoft Defender Virüsten Koruma'de tarama seçeneklerini yapılandırma](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Tarama|Paketlenmiş yürütülebilir dosyaları tarama|[Microsoft Defender Virüsten Koruma'de tarama seçeneklerini yapılandırma](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
| Tarama | Betikleri tarama | [Microsoft Defender Virüsten Koruma'de tarama seçeneklerini yapılandırma](configure-advanced-scan-types-microsoft-defender-antivirus.md) <p>Ayrıca bkz [. Defender/AllowScriptScanning](/windows/client-management/mdm/policy-csp-defender).|
|Tarama|Çıkarılabilir sürücüleri tarama|[Microsoft Defender Virüsten Koruma'de tarama seçeneklerini yapılandırma](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Tarama|Arşiv dosyalarını taramak için maksimum derinliği belirtin|[Microsoft Defender Virüsten Koruma'de tarama seçeneklerini yapılandırma](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Tarama|Tarama sırasında en yüksek CPU kullanım yüzdesini belirtme|[Microsoft Defender Virüsten Koruma'de tarama seçeneklerini yapılandırma](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Tarama|Taranacak arşiv dosyalarının en büyük boyutunu belirtin|[Microsoft Defender Virüsten Koruma'de tarama seçeneklerini yapılandırma](configure-advanced-scan-types-microsoft-defender-antivirus.md)|
|Tarama|Zamanlanmış taramanın çalıştırıldığı haftanın gününü belirtme|[Microsoft Defender Virüsten Koruma için zamanlanmış taramaları yapılandırma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Tarama|Her gün hızlı tarama çalıştırmak için aralığı belirtin|[Microsoft Defender Virüsten Koruma için zamanlanmış taramaları yapılandırma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Tarama|Zamanlanmış tarama için kullanılacak tarama türünü belirtme|[Microsoft Defender Virüsten Koruma için zamanlanmış taramaları yapılandırma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Tarama|Günlük hızlı tarama süresini belirtme|[Microsoft Defender Virüsten Koruma için zamanlanmış taramaları yapılandırma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Tarama|Zamanlanmış taramanın çalıştırıldığı günün saatini belirtme|[Microsoft Defender Virüsten Koruma için zamanlanmış taramaları yapılandırma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Tarama|Zamanlanmış taramayı yalnızca bilgisayar açıkken ancak kullanımda değilken başlatın|[Microsoft Defender Virüsten Koruma için zamanlanmış taramaları yapılandırma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Güvenlik bilgileri güncelleştirmeleri|Microsoft Update'ten güvenlik bilgileri güncelleştirmelerine izin ver|[Mobil cihaz ve sanal makine (VM) güncelleştirmelerini yönetin](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)|
|Güvenlik bilgileri güncelleştirmeleri|Pil gücüyle çalışırken güvenlik zekası güncelleştirmelerine izin ver|[Mobil cihaz ve sanal makine (VM) güncelleştirmelerini yönetin](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)|
|Güvenlik bilgileri güncelleştirmeleri|Tanım tabanlı raporları Microsoft MAPS'e devre dışı bırakmak için bildirimlere izin ver|[Olay tabanlı zorunlu güncelleştirmeleri yönetin](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Güvenlik bilgileri güncelleştirmeleri|Microsoft MAPS raporlarına göre gerçek zamanlı güvenlik bilgileri güncelleştirmelerine izin ver|[Olay tabanlı zorunlu güncelleştirmeleri yönetin](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Güvenlik bilgileri güncelleştirmeleri|Başlangıçta en son virüs ve casus yazılım tanımlarını denetleyin|[Olay tabanlı zorunlu güncelleştirmeleri yönetin](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Güvenlik bilgileri güncelleştirmeleri|Güvenlik bilgileri güncelleştirmelerini indirmek için dosya paylaşımlarını tanımlama|[Microsoft Defender Virüsten Koruma koruma ve güvenlik bilgileri güncelleştirmelerini yönetme](manage-protection-updates-microsoft-defender-antivirus.md)|
|Güvenlik bilgileri güncelleştirmeleri|Güvenlik bilgileri güncelleştirmesinin gerekli olduğu gün sayısını tanımlayın|[Güncel olmayan uç noktalar için güncelleştirmeleri yönetme](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Güvenlik bilgileri güncelleştirmeleri|Casus yazılım tanımlarının güncel olmayan olarak değerlendirilmeden önce geçmesi gereken gün sayısını tanımlayın|[Güncel olmayan uç noktalar için güncelleştirmeleri yönetme](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Güvenlik bilgileri güncelleştirmeleri|Virüs tanımlarının güncel olmayan olarak kabul edilmesinden önceki gün sayısını tanımlama|[Güncel olmayan uç noktalar için güncelleştirmeleri yönetme](manage-outdated-endpoints-microsoft-defender-antivirus.md)|
|Güvenlik bilgileri güncelleştirmeleri|Güvenlik bilgileri güncelleştirmelerini indirmek için kaynakların sırasını tanımlama|[Microsoft Defender Virüsten Koruma koruma ve güvenlik bilgileri güncelleştirmelerini yönetme](manage-protection-updates-microsoft-defender-antivirus.md)|
|Güvenlik bilgileri güncelleştirmeleri|Başlangıçta güvenlik bilgileri güncelleştirmesini başlatma|[Olay tabanlı zorunlu güncelleştirmeleri yönetin](manage-event-based-updates-microsoft-defender-antivirus.md)|
|Güvenlik bilgileri güncelleştirmeleri|Güvenlik bilgileri güncelleştirmelerini denetlemek için haftanın gününü belirtin|[Koruma güncelleştirmelerinin ne zaman indirileceğini ve uygulanacağını yönetme](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|Güvenlik bilgileri güncelleştirmeleri|Güvenlik bilgileri güncelleştirmelerinin denetlenme aralığını belirtin|[Koruma güncelleştirmelerinin ne zaman indirileceğini ve uygulanacağını yönetme](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|Güvenlik bilgileri güncelleştirmeleri|Güvenlik bilgileri güncelleştirmelerinin denetlenme zamanını belirtin|[Koruma güncelleştirmelerinin ne zaman indirileceğini ve uygulanacağını yönetme](manage-protection-update-schedule-microsoft-defender-antivirus.md)|
|Güvenlik bilgileri güncelleştirmeleri|Güvenlik bilgileri güncelleştirmesinin ardından taramayı açma|[Microsoft Defender Virüsten Koruma için zamanlanmış taramaları yapılandırma](scheduled-catch-up-scans-microsoft-defender-antivirus.md)|
|Tehdit|Algılandığında varsayılan eylemin gerçekleştirilmemesi gereken tehdit uyarısı düzeylerini belirtin|[Microsoft Defender Virüsten Koruma taramaları için düzeltmeyi yapılandırma](configure-remediation-microsoft-defender-antivirus.md)|
|Tehdit|Algılandığında varsayılan eylemin gerçekleştirilmemesi gereken tehditleri belirtin|[Microsoft Defender Virüsten Koruma taramaları için düzeltmeyi yapılandırma](configure-remediation-microsoft-defender-antivirus.md)|

> [!TIP]
> Diğer platformlar için Virüsten Koruma ile ilgili bilgileri arıyorsanız bkz:
> - [macOS'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](mac-preferences.md)
> - [Mac'te Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-mac.md)
> - [Intune için Microsoft Defender Virüsten Koruma macOS Virüsten Koruma ilkesi ayarları](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Linux'ta Pertahanan Microsoft untuk Titik Akhir tercihlerini ayarlama](linux-preferences.md)
> - [Linux'ta Uç Nokta için Microsoft Defender](microsoft-defender-endpoint-linux.md)
> - [Android'de Uç Nokta için Defender özelliklerini yapılandırma](android-configure.md)
> - [iOS özelliklerinde Pertahanan Microsoft untuk Titik Akhir yapılandırma](ios-configure-features.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Yönetim ve yapılandırma araçları için başvuru konuları](configuration-management-reference-microsoft-defender-antivirus.md)
- [Windows 10'da Microsoft Defender Virüsten Koruma](microsoft-defender-antivirus-in-windows-10.md)
