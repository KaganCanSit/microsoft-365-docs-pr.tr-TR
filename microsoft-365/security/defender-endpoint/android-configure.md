---
title: Android'de Uç Nokta için Microsoft Defender özelliklerini yapılandırma
description: Android'de Uç Nokta için Microsoft Defender'ın nasıl yapılandırıldığından emin olun
keywords: microsoft, defender, Endpoint için Microsoft Defender, mde, android, yapılandırma
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 22e0eed3becebdcb3dee4c31ddc7659651bac71f
ms.sourcegitcommit: e3bff611439354e6339bb666a88682078f32ec13
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/03/2022
ms.locfileid: "62974151"
---
# <a name="configure-defender-for-endpoint-on-android-features"></a>Android'de Uç Nokta özellikleri için Defender'ı yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="conditional-access-with-defender-for-endpoint-on-android"></a>Android'de Uç Nokta için Defender ile Koşullu Erişim

Microsoft Intune ve Azure Active Directory ile birlikte Android'de Uç Nokta için Microsoft Defender cihaz risk düzeylerine göre Cihaz uyumluluğu ve Koşullu Erişim ilkelerinin zorlanmalarını sağlar. Uç Nokta için Defender, Intune aracılığıyla bu özellikten yararlanarak dağıtımlarda yararlan yararlanan bir Mobil Tehdit Savunma (MTD) çözümüdür.

Android ve Koşullu Erişim'de Uç Nokta için Defender'ı ayarlama hakkında daha fazla bilgi için bkz. Uç Nokta [ve Intune için Defender](/mem/intune/protect/advanced-threat-protection).

## <a name="configure-custom-indicators"></a>Özel göstergeleri yapılandırma

> [!NOTE]
> Android'de Uç Nokta için Defender yalnızca IP adresleri ve URL'ler/etki alanları için özel göstergeler oluşturmayı destekler.

Android'de Uç Nokta için Defender yöneticilerin Android cihazlarını da destekleyecek özel göstergeler yapılandırmasını sağlar. Özel göstergeleri yapılandırma hakkında daha fazla bilgi için bkz. [Göstergeleri yönetme](manage-indicators.md).

## <a name="configure-web-protection"></a>Web korumasını yapılandırma
Android'de Uç Nokta için Defender, IT Yöneticilerinin web koruma özelliğini yapılandırabilmelerini sağlar. Bu özellik, Microsoft Endpoint Manager Yönetim merkezinde yer almaktadır.

> [!NOTE]
> Android'de Uç Nokta için Defender Web Koruma özelliğini sağlamak üzere VPN kullanıyor olabilir. Bu normal bir VPN değildir ve trafiği cihazın dışına almayan yerel/kendi kendine döngülü bir VPN'tir.
> Daha fazla bilgi için bkz [. Android çalıştırılan cihazlarda web korumasını yapılandırma](/mem/intune/protect/advanced-threat-protection-manage-android).

## <a name="privacy-controls"></a>Gizlilik Denetimleri

> [!IMPORTANT]
> Android'de Uç Nokta için Microsoft Defender Gizlilik Denetimleri önizlemede. Aşağıdaki bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilabilecek, önceden satın alınan ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Android cihazlardan Uç Nokta için Defender tarafından gönderilen verileri yapılandırmak için aşağıdaki gizlilik denetimleri kullanılabilir:

|Tehdit Raporu     |Ayrıntılar      |
|--------------------|-------------|
|Kötü amaçlı yazılım raporu |Yöneticiler kötü amaçlı yazılım raporu için gizlilik denetimi kurabilirsiniz - Gizlilik etkinse, uç nokta için Defender kötü amaçlı yazılım uygulama adını ve diğer uygulama ayrıntılarını kötü amaçlı yazılım uyarı raporunun bir parçası olarak göndermez |
|Kimlik avı raporu |Yöneticiler kimlik avı raporu için gizlilik denetimi kurabilirsiniz - Gizlilik etkinse, uç nokta için Defender etki alanı adını ve güvenli olmayan web sitesinin ayrıntılarını kimlik avı uyarı raporunun bir parçası olarak göndermez |
|Uygulamaların Güvenlik Açığı Değerlendirmesi (yalnızca Android) |Varsayılan olarak yalnızca iş profilinde yüklü uygulamalar hakkında bilgiler güvenlik açığı değerlendirmesi için gönderilir. Yöneticiler kişisel uygulamaları dahil etmek için gizliliği devre dışı bırakabilirsiniz|

## <a name="configure-vulnerability-assessment-of-apps-for-byod-devices"></a>BYOD cihazları için uygulamaların güvenlik açığı değerlendirmesi yapılandır

Android'de Uç Nokta için Microsoft Defender'ın 1.0.3425.0303 sürümünden, yerleşik olarak bulunan mobil cihazlarda yüklü işletim sistemi ve uygulamalarla ilgili güvenlik açığı değerlendirmesi çalıştırabilirsiniz.

> [!NOTE]
> Güvenlik Açığı değerlendirmesi, Uç Nokta için Microsoft [Defender'daki Tehdit](next-gen-threat-and-vuln-mgt.md) ve Güvenlik Açığı yönetiminin bir parçasıdır. 

**Kişisel cihazlardan (BYOD) uygulamalarla ilgili gizlilikle ilgili notlar:**

- Bir Enterprise olan Android kullanıcıları için yalnızca iş profilinde yüklü olan uygulamalar desteklenene.
- Diğer BYOD modları için, varsayılan olarak, uygulamaların güvenlik **açığı değerlendirmesi** etkinleştirilmez. Bununla birlikte, cihaz yönetici modundayken, yöneticiler cihaza yüklenmiş uygulamaların listesini almak için Microsoft Endpoint Manager Office aracılığıyla bu özelliği açıkça etkinleştirebilirsiniz. Daha fazla bilgi için aşağıdaki ayrıntılara bakın.

### <a name="configure-privacy-for-device-administrator-mode"></a>Cihaz yöneticisi modu için gizliliği yapılandırma

Hedefli kullanıcılar için **cihaz yöneticisi modunda cihazlara** ilişkin uygulamaların güvenlik açığı **değerlendirmesine** olanak sağlamak üzere aşağıdaki adımları kullanın. 

> [!NOTE]
> Cihaz yöneticisi moduyla kaydolan cihazlar için varsayılan olarak bu kapalıdır.

1. Microsoft Endpoint Manager [merkezinde Cihazlar](https://go.microsoft.com/fwlink/?linkid=2109431)  >  Yapılandırma profilleri **Profile oluşturun'a** >  gidin **ve** aşağıdaki ayarları girin:

   - **Platform**: Android cihaz yöneticisini seçin
   - **Profil**: "Özel" öğesini seçin ve Oluştur'a tıklayın

2. Temel **Bilgiler bölümünde** , profilin adını ve açıklamasını belirtin.

3. Yapılandırma ayarlarında **OMA-URI ayarı ekle'yi** seçin:

   - **Ad**: Daha sonra kolayca bulmak için bu OMA-URI ayarı için benzersiz bir ad ve açıklama girin.
   - OMA-URI: **./Vendor/MSFT/DefenderATP/DefenderTVMPrivacyMode**
   - Veri türü: Açılan listeden Tamsayı'ya tıklayın.
   - Değer: Gizlilik ayarını devre dışı bırakmak için 0 girin (Varsayılan olarak değer 1'dir)

4. **Sonraki'ne** tıklayın ve bu profili hedefli cihazlara/kullanıcılara attayin.

### <a name="configure-privacy-for-android-enterprise-work-profile"></a>Android kullanıcı profili için Enterprise yapılandırma

Uç Nokta için Defender, iş profilinde uygulamaların güvenlik açığı değerlendirmesine destek olur. Öte yandan, hedeflenen kullanıcılar için bu özelliği kapatmak istemeniz durumunda aşağıdaki adımları kullanabilirsiniz:

1. Uygulama [Microsoft Endpoint Manager ve](https://go.microsoft.com/fwlink/?linkid=2109431) **AppsApp** >  >  yapılandırma **ilkeleriAddManaged** >  **cihazlar'a gidin**.
2. İlkeye bir ad verme; **Android > Enterprise** platformları; profil türünü seçin.
3. Hedef **uygulama olarak Uç Nokta için Microsoft Defender'ı** seçin.
4. Yeni Ayarlar, Yapılandırma **tasarımcısını kullan'ı seçin** ve **DefenderTVMPrivacyMode'yu** anahtar ve değer türü olarak **Tamsayı olarak ekleyin**
   - İş profilinde uygulamaların güvenlik açığını devre dışı bırakmak için, bu ilke `1` olarak değer girin ve kullanıcılara bu ilkeyi attayin. Varsayılan olarak, bu değer olarak ayarlanır `0`.
   - Anahtar olarak ayarlanmış anahtara `0`sahip kullanıcılar için, Uç Nokta için Defender güvenlik açığı değerlendirmesi için iş profilinden arka uç hizmetine uygulama listesi gönderir.
5. **Sonraki'ne** tıklayın ve bu profili hedefli cihazlara/kullanıcılara attayin.

Yukarıdaki gizlilik denetimlerini açma veya kapatma, cihaz uyumluluğu denetimi veya koşullu erişimi etkilemez.

## <a name="configure-privacy-for-phishing-alert-report"></a>Kimlik avı uyarı raporu için gizliliği yapılandırma

Kimlik avı raporu için gizlilik denetimi, kimlik avı tehdit raporunda etki alanı adı veya web sitesi bilgileri koleksiyonunu devre dışı bırakmak için kullanılabilir. Bu, kuruluşlara, uç nokta için Defender tarafından kötü amaçlı bir web sitesi veya kimlik avı web sitesi algılandığında ve engellandığında etki alanı adını toplamak isteyip istemediklerini seçme esnekliği sağlar.

### <a name="configure-privacy-for-phishing-alert-report-on-android-device-administrator-enrolled-devices"></a>Android Cihaz Yöneticisi tarafından kayıtlı cihazlarda kimlik avı uyarı raporu için gizliliği yapılandırma:

Hedefli kullanıcılarda açmak için aşağıdaki adımları kullanın:

1. Microsoft Endpoint Manager [merkezinde Cihazlar](https://go.microsoft.com/fwlink/?linkid=2109431)  >  Yapılandırma profilleri **Profile oluşturun'a** >  gidin **ve** aşağıdaki ayarları girin:

   - **Platform**: Android cihaz yöneticisini seçin.
   - **Profil**: "Özel" öğesini seçin ve Oluştur'a **tıklayın**.

2. Temel **Bilgiler bölümünde** , profilin adını ve açıklamasını belirtin.

3. Yapılandırma ayarlarında **OMA-URI ayarı ekle'yi** seçin:

   - **Ad**: Daha sonra kolayca bulmak için bu OMA-URI ayarı için benzersiz bir ad ve açıklama girin.
   - OMA-URI: **./Vendor/MSFT/DefenderATP/DefenderExcludeURLInReport**
   - Veri türü: Açılan listeden Tamsayı'ya tıklayın.
   - Değer: Gizlilik ayarını etkinleştirmek için 1 girin. Varsayılan değer: 0.

4. **Sonraki'ne** tıklayın ve bu profili hedefli cihazlara/kullanıcılara attayin.

Bu gizlilik denetimi kullanmak cihaz uyumluluğu denetimi veya koşullu erişimi etkilenmez.

### <a name="configure-privacy-for-phishing-alert-report-on-android-enterprise-work-profile"></a>Android iş profilinde kimlik avı uyarı raporu için Enterprise yapılandırma

İş profilinde hedeflenen kullanıcılar için gizliliği açmak üzere aşağıdaki adımları kullanın:

1. Uygulama [Microsoft Endpoint Manager ve](https://go.microsoft.com/fwlink/?linkid=2109431) **AppsApp** >  >  yapılandırma **ilkeleriAddManaged** >  **cihazlar'a gidin**.
2. İlkeye bir ad girin, **Android > Platform Enterprise** profil türünü seçin.
3. Hedef **uygulama olarak Uç Nokta için Microsoft Defender'ı** seçin.
4. Yeni Ayarlar, Yapılandırma tasarımcısını **kullan'ı seçin** ve **defenderExcludeURLInReport öğesini anahtar** ve değer türü olarak **Tamsayı olarak ekleyin**.
   - Gizliliği **etkinleştirmek için 1 girin**. Varsayılan değer: 0.
5. **Sonraki'ne** tıklayın ve bu profili hedefli cihazlara/kullanıcılara attayin.

Yukarıdaki gizlilik denetimlerini açma veya kapatma, cihaz uyumluluğu denetimi veya koşullu erişimi etkilemez.

## <a name="configure-privacy-for-malware-threat-report"></a>Kötü amaçlı yazılım tehdit raporu için gizliliği yapılandırma

Kötü amaçlı yazılım tehdit raporu için gizlilik denetimi, kötü amaçlı yazılım tehdit raporundan uygulama ayrıntıları (ad ve paket bilgileri) koleksiyonunu devre dışı bırakmak için kullanılabilir. Bu, kuruluşlara kötü amaçlı bir uygulama algılandığında uygulama adını toplamak isteyip istemediklerini seçme esnekliği sağlar.

### <a name="configure-privacy-for-malware-alert-report-on-android-device-administrator-enrolled-devices"></a>Android Cihaz Yöneticisi tarafından kayıt yapılan cihazlarda kötü amaçlı yazılım uyarısı raporu için gizliliği yapılandırma:

Hedefli kullanıcılarda açmak için aşağıdaki adımları kullanın:

1. Cihaz [Microsoft Endpoint Manager merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) **Cihazlar** >  Yapılandırma profilleri Profile **oluşturun'a** >  gidin ve aşağıdaki ayarları girin:

   - **Platform**: Android cihaz yöneticisini seçin.
   - **Profil**: "Özel" öğesini seçin ve Oluştur'a **tıklayın**.

2. Temel **Bilgiler bölümünde** , profilin adını ve açıklamasını belirtin.

3. Yapılandırma ayarlarında **OMA-URI ayarı ekle'yi** seçin:

   - **Ad**: Daha sonra kolayca bulmak için bu OMA-URI ayarı için benzersiz bir ad ve açıklama girin.
   - OMA-URI: **./Vendor/MSFT/DefenderATP/DefenderExcludeAppInReport**
   - Veri türü: Açılan listeden Tamsayı'ya tıklayın.
   - Değer: Gizlilik ayarını etkinleştirmek için 1 girin. Varsayılan değer: 0.

4. **Sonraki'ne** tıklayın ve bu profili hedefli cihazlara/kullanıcılara attayin.

Bu gizlilik denetimi kullanmak cihaz uyumluluğu denetimi veya koşullu erişimi etkilenmez. Örneğin, kötü amaçlı bir uygulamaya sahip cihazlar her zaman "Orta" risk düzeyine sahip olur.

### <a name="configure-privacy-for-malware-alert-report-on-android-enterprise-work-profile"></a>Android iş profilinde kötü amaçlı yazılım uyarısı raporu Enterprise yapılandırma

İş profilinde hedeflenen kullanıcılar için gizliliği açmak üzere aşağıdaki adımları kullanın:

1. Uygulama [Microsoft Endpoint Manager ve](https://go.microsoft.com/fwlink/?linkid=2109431) **AppsApp** >  >  yapılandırma **ilkeleriAddManaged** >  **cihazlar'a gidin**.
2. İlkeye Bir Ad Ver: **Android > Platform Enterprise**, profil türünü seçin.
3. Hedef **uygulama olarak Uç Nokta için Microsoft Defender'ı** seçin.
4. Yeni Ayarlar, Yapılandırma tasarımcısını **kullan'ı seçin** ve **DefenderExcludeAppInReport** öğesini anahtar ve değer türü Tamsayı olarak **ekleyin**.
   - Gizliliği **etkinleştirmek için 1 girin**. Varsayılan değer: 0.
5. **Sonraki'ne** tıklayın ve bu profili hedefli cihazlara/kullanıcılara attayin.

Bu gizlilik denetimi kullanmak cihaz uyumluluğu denetimi veya koşullu erişimi etkilenmez. Örneğin, kötü amaçlı bir uygulamaya sahip cihazlar her zaman "Orta" risk düzeyine sahip olur.

## <a name="related-topics"></a>İlgili konular

- [Android'de Uç Nokta için Microsoft Defender'a Genel Bakış](microsoft-defender-endpoint-android.md)
- [Android'de Uç Nokta için Microsoft Defender'ı Microsoft Intune](android-intune.md)
