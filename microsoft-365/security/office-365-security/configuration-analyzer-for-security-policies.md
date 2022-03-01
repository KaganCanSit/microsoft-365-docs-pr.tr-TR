---
title: Güvenlik ilkeleri için yapılandırma çözümleyicisi
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: ''
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Yöneticiler, önceden ayarlanmış güvenlik ilkeleri içinde Standart koruma ve Katı koruma ayarlarında yer alan ayarların altında yer alan güvenlik ilkelerini bulmak ve düzeltmek için yapılandırma çözümleyicisi'ni kullanmayı öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0acdf6d300984c00bb1b1b060d3e36562983ebca
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021663"
---
# <a name="configuration-analyzer-for-protection-policies-in-eop-and-microsoft-defender-for-office-365"></a>EOP'de ve Office 365 için Microsoft Defender'da koruma ilkeleri için yapılandırma çözümleyicisi

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft 365 Defender portalında yapılandırma çözümleyicisi, önceden ayarlanmış güvenlik ilkelerde ayarların Standart koruma ve Katı koruma profili ayarlarının altında yer alan güvenlik ilkelerini bulmak ve düzeltmek için merkezi [bir konum sağlar](preset-security-policies.md).

Aşağıdaki ilke türleri yapılandırma çözümleyicisi tarafından çözümlendi:

- **Exchange Online Protection ilkeleri:** Bu, Microsoft 365 posta kutuları olan Exchange Online ve posta kutusu olmayan tek Exchange Online EOP kuruluşlarını içerir:
  - [İstenmeyen posta önleme ilkeleri](configure-your-spam-filter-policies.md).
  - [Kötü amaçlı yazılımdan koruma ilkeleri](configure-anti-malware-policies.md).
  - [EOP kimlik avı önleme ilkeleri](set-up-anti-phishing-policies.md#spoof-settings).

- **İlkeler için Microsoft Defender Office 365 ilkeleri**: Bu, Microsoft 365 E5 veya Office 365 için Defender'a sahip olan kuruluşları içerir:
  - Office 365 için Microsoft Defender'da kimlik avıyla mücadele ilkeleri şunlardır:
    - EOP [kimlik avı önleme](set-up-anti-phishing-policies.md#spoof-settings) ilkelerde bulunan kimlik sahtesi ayarlarıyla aynıdır.
    - [Kimliğe bürünme ayarları](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
    - [Gelişmiş kimlik avı eşikleri](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
  - [Kasa Bağlantıları ilkeleri.](set-up-safe-links-policies.md)
  - [Kasa İlkeleri'ne tıklayın](set-up-safe-attachments-policies.md).

Taban çizgisi olarak kullanılan Standart ve Katı ilke ayarı değerleri, EOP için önerilen ayarlar ve Güvenlik için [Microsoft Defender'da Office 365 açıklanmıştır](recommended-settings-for-eop-and-office365.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açın<https://security.microsoft.com>. Doğrudan Yapılandırma **çözümleyicisi sayfasına gitmek** için, kullanın <https://security.microsoft.com/configurationAnalyzer>.

- Exchange Online PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online e bağlama](/powershell/exchange/connect-to-exchange-online-powershell).

- Bu makaledeki yordamları yerine Microsoft 365 Defender portalında izinlerin atanmamış olması gerekir:
  - Yapılandırma **çözümleyiciyi kullanmak** ve güvenlik ilkelerine güncelleştirmeler yapmak için, Kuruluş Yönetimi veya Güvenlik **Yöneticisi rol** **gruplarının üyesi olun** .
  - Yapılandırma çözümleyicisine salt okunur erişim için, Genel Okuyucu veya Güvenlik Okuyucusu **rol gruplarının** **üyesi** olmak gerekir.

  Daha fazla bilgi için bkz[. Microsoft 365 Defender portalına.](permissions-microsoft-365-security-center.md)

  > [!NOTE]
  >
  > - İlgili kullanıcı rolüne kullanıcı Azure Active Directory, kullanıcılara portalda gerekli izinleri Microsoft 365 Defender bu portalda yer alan diğer özellikler  için Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  > - **Görünüm'de Yalnızca Görüntüleme** [kuruluş Exchange Online rol](/Exchange/permissions-exo/permissions-exo#role-groups) grubu, özel salt okunur erişim de sağlar.

## <a name="use-the-configuration-analyzer-in-the-microsoft-365-defender-portal"></a>Yeni portalda yapılandırma çözümleyici Microsoft 365 Defender kullanma

aşağıdaki Microsoft 365 Defender portalında<https://security.microsoft.com>, Şablon  ilkeleri bölümündeki **&** \> İşbirliği  **İlkeleri** \> \>'& Kurallar Tehdit ilkeleri Yapılandırması çözümleyicisi'ne gidin. Doğrudan Yapılandırma **çözümleyicisi sayfasına gitmek** için, kullanın <https://security.microsoft.com/configurationAnalyzer>.

Yapılandırma **çözümleyicisi** sayfasının üç ana sekmesi vardır:

- **Standart öneriler**: Var olan güvenlik ilkelerinizi Standart önerilerle karşılaştırın. Ayar değerlerinizi Standart değerlerle aynı düzeye getirmek için ayarlayabilirsiniz.
- **Kesin öneriler**: Var olan güvenlik ilkelerinizi Katı önerilerle karşılaştırın. Ayarların değerlerini Katı ile aynı düzeye getirmek için ayarlayabilirsiniz.
- **Yapılandırma değişikliği çözümlemesi ve geçmişi**: Zaman içinde ilke değişikliklerini denetleme ve izleme.

### <a name="standard-recommendations-and-strict-recommendations-tabs-in-the-configuration-analyzer"></a>Standart öneriler ve yapılandırma çözümleyicisinde Katı öneriler sekmeleri

Varsayılan olarak, yapılandırma çözümleyicisi **Standart öneriler sekmesinde** açılır. Katı öneriler **sekmesine geçebilirsiniz** . Ayarlar, düzen ve eylemler her iki sekmede de aynıdır.

![Ayarlar çözümleyicisinde daha fazla bilgi ve öneriler görünümü sağlar.](../../media/configuration-analyzer-settings-and-recommendations-view.png)

Sekmenin ilk bölümünde, Standart veya Katı koruma ile karşılaştırıldığında, her tür ilke için geliştirme gereken ayarlar görüntülenir. İlke türleri:

- **İstenmeyen posta önleme**
- **Kimlik avı önleme**
- **Kötü amaçlı yazılımdan koruma**
- **Kasa Ekle (** aboneliğiniz Windows için Microsoft Defender'ı da Office 365)
- **Kasa Bağlantılarını Paylaş** (aboneliğiniz Microsoft Defender for Office 365)

İlke türü ve numarası gösterilmezse, bu türle ilgili tüm ilkeleriniz Standart veya Katı korumanın önerilen ayarlarına uygun olur.

Sekmenin kalan kalanında, Standart veya Katı koruma düzeyine getirmeniz gereken ayarlar tablosu yer alır. Tablo aşağıdaki sütunları içerir:

- **Öneriler**: Standart veya Katı koruma profilinde ayarın değeri.
- **İlke**: Ayarı içeren etkilenen ilkenin adı.
- **İlke grubu/ayar** adı: Sizin dikkat gerektiren ayarın adı.
- **İlke türü**: İstenmeyen posta önleme, Kimlik avından koruma, Kötü amaçlı yazılımdan koruma, Kasa Veya Ekleri Engelleme Kasa.
- **Geçerli yapılandırma**: Ayarın geçerli değeridir.
- **Son değiştirme**: İlkenin son değiştirilma tarihi.
- **Durum**: Normalde, bu değer **Başlamaz**.

### <a name="change-a-policy-setting-to-the-recommended-value"></a>İlke ayarını önerilen değerle değiştirme

Yapılandırma **çözümleyicisi'nin** **Standart** koruma veya Katı koruma sekmesinde, tabloda satırı seçin. Aşağıdaki düğmeler görüntülenir:

- **Öneri uygulama**
- **İlkeyi görüntüleme**
- **Yenile**:

Bir satır seçer ve Öneri **uygula'ya tıklarsanız**, bir onay iletişim kutusu (iletişim kutusunu yeniden gösterme seçeneğiyle birlikte) görüntülenir. **Tamam'a tıklarsanız** aşağıdaki şeyler olur:

- Ayar önerilen değere güncelleştirilir.
- Öneri **uygula ve** **Görünüm ilkesi kaybolur** (yalnızca **Yenile** düğmesi kalır).
- **Satırın** Durum değeri Tamamlandı olarak **değişir**.

Bir satır seçer ve İlkeyi  görüntüle'ye tıklarsanız, ayarı el ile güncelleştirebilirsiniz ve bu portalda etkilenen ilkenin ayrıntılar ayrıntılarına Microsoft 365 Defender.

Ayarı otomatik olarak veya el ile güncelleştirdikten sonra,  azaltılmış sayıda öneri görmek ve güncelleştirilmiş satırın sonuçlardan kaldırılmasını görmek için Yenile'ye tıklayın.

### <a name="configuration-drift-analysis-and-history-tab-in-the-configuration-analyzer"></a>Yapılandırma çözümleyicisinde yapılandırma gerindi çözümlemesi ve geçmiş sekmesi

Bu sekme, güvenlik ilkelerinize yapılan değişiklikleri ve bu değişikliklerin Standart veya Katı ayarlarıyla karşılaştırmalarını izlemenizi sağlar. Varsayılan olarak aşağıdaki bilgiler görüntülenir:

- **Son değiştirme**
- **Değiştiren**
- **Ayar Adı**
- **İlke**: Etkilenen ilkenin adı.
- **Tür**: İstenmeyen posta önleme, Kimlik avı önleme, Kötü amaçlı yazılımdan koruma, Kasa Bağlantılar veya Kasa tıklatın.
- **Yapılandırma değişikliği**: Eski değer ve ayarın yeni değeri
- **Yapılandırma azaltma****: Ayarın** önerilen **Standart veya Katı** ayarına göre güvenliği artırdı veya azalttığını gösteren Artır veya Azalt değeri.

Sonuçları filtrelemek için Filtre'ye **tıklayın**. Görüntülenen **Filtreler** açılır yapısında, aşağıdaki filtrelerden birini seçebilirsiniz:

- **Başlangıç saati** **ve Bitiş saati** (tarih): Bugünden itibaren 90 gün geriye gidebilirsiniz.
- **Standart koruma** veya **Katı koruma**

Bitirdikten sonra Uygula'ya **tıklayın**.

Sonuçları bir dosya dosyasına dışarı .csv Dışarı Aktar'a **tıklayın**.

Sonuçları değiştiren belirli bir değere, **Ayar adı** **veya** Tür **değerine göre** filtrelemek için Arama **kutusunu** kullanın.

![Yapılandırma çözümleyicisinde yapılandırma gerindi çözümlemesi ve geçmiş görünümü.](../../media/configuration-analyzer-configuration-drift-analysis-view.png)
