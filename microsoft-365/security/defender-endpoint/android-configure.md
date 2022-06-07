---
title: Android’de Uç Nokta için Microsoft Defender’ı yapılandırın
description: Android'de Uç Nokta için Microsoft Defender'ın nasıl yapılandırıldığı açıklanır
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mde, android, yapılandırma
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
ms.openlocfilehash: 1f4ebaadd22a14eb2a9b24194c43fb35a5382adf
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2022
ms.locfileid: "65923254"
---
# <a name="configure-defender-for-endpoint-on-android-features"></a>Android özelliklerinde Uç Nokta için Defender’ı yapılandırın

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="conditional-access-with-defender-for-endpoint-on-android"></a>Android'de Uç Nokta için Defender ile Koşullu Erişim

Android'de Uç Nokta için Microsoft Defender'ın yanı sıra Microsoft Intune ve Azure Active Directory, cihaz risk düzeylerine göre Cihaz uyumluluğu ve Koşullu Erişim ilkelerinin zorunlu tutmasını sağlar. Uç Nokta için Defender, Intune aracılığıyla bu özellikten yararlanmak için dağıtabileceğiniz bir Mobil Tehdit Savunması (MTD) çözümüdür.

Android ve Koşullu Erişim'de Uç Nokta için Defender'ı ayarlama hakkında daha fazla bilgi için bkz. [Uç Nokta için Defender ve Intune](/mem/intune/protect/advanced-threat-protection).

## <a name="configure-custom-indicators"></a>Özel göstergeleri yapılandırma

> [!NOTE]
> Android'de Uç Nokta için Defender yalnızca IP adresleri ve URL'ler/etki alanları için özel göstergeler oluşturmayı destekler.

Android'de Uç Nokta için Defender, yöneticilerin Android cihazlarını destekleyecek şekilde özel göstergeler yapılandırmasına da olanak tanır. Özel göstergeleri yapılandırma hakkında daha fazla bilgi için bkz. [Göstergeleri yönetme](manage-indicators.md).

## <a name="configure-web-protection"></a>Web korumasını yapılandırma
Android'de Uç Nokta için Defender, BT Yöneticilerinin web koruması özelliğini yapılandırmalarına olanak tanır. Bu özellik Microsoft Endpoint Manager Yönetim merkezinde kullanılabilir.

> [!NOTE]
> Android'de Uç Nokta için Defender, Web Koruması özelliğini sağlamak için bir VPN kullanır. Bu normal bir VPN değildir ve cihazın dışına trafiği almayan yerel/kendi kendini döngüye alan bir VPN'dir.
> Daha fazla bilgi için bkz. [Android çalıştıran cihazlarda web korumasını yapılandırma](/mem/intune/protect/advanced-threat-protection-manage-android).

## <a name="network-protection"></a>Ağ Koruması
>[!NOTE]
>Uç Nokta için Microsoft Defender'da Ağ Koruması artık genel önizleme aşamasındadır. Aşağıdaki bilgiler, ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilebilen önceden yayımlanmış ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Bu özellik, Wi-Fi ağları için birincil saldırı vektörleri olan Wi-Fi ilgili tehditlere ve sahte sertifikalara karşı koruma sağlar. Yöneticiler, Microsoft Endpoint Manager Yönetim merkezinde kök Sertifika Yetkilisi (CA) ve özel kök CA sertifikalarını listeleyebilir ve uç noktalarla güven kurabilir. Kullanıcıya güvenli ağlara bağlanmak için kılavuzlu bir deneyim sağlar ve ayrıca ilgili bir tehdit algılandığında bu kullanıcılara bildirir. 

Özelliği Microsoft Endpoint Manager Yönetim merkezinden yapılandırma ve güvenilen sertifikalar ekleme gibi esneklik sunmak için çeşitli yönetici denetimleri içerir. Yöneticiler, Android cihazlardan Uç Nokta için Defender tarafından gönderilen verileri yapılandırmak için [gizlilik denetimlerini](android-configure.md) de etkinleştirebilir.

Uç nokta için Microsoft Defender'da ağ koruması varsayılan olarak etkindir. Yöneticiler **, Android cihazlarda Ağ korumasını yapılandırmak** için aşağıdaki adımları kullanabilir.

1. Microsoft Endpoint Manager Yöneticisi'nde Uygulamalar > Uygulama yapılandırma ilkeleri'ne gidin. Yeni bir Uygulama yapılandırma ilkesi oluşturun.
    > [!div class="mx-imgBorder"]
    > ![İlke oluşturma resmi.](images/create-policy.png)
1. İlkeyi benzersiz olarak tanımlamak için bir ad ve açıklama sağlayın. Platform olarak **'Android Enterprise'ı** ve profil türü olarak **'Yalnızca kişisel iş profili'ni** ve Hedeflenen uygulama olarak **'Microsoft Defender'ı** seçin.
    > [!div class="mx-imgBorder"]
    > ![İlke ayrıntılarının görüntüsü.](images/appconfigdetails.png)
1. Ayarlar sayfasında **'Yapılandırma tasarımcısını kullan'ı** seçin ve anahtar olarak **'Microsoft Defender'da Ağ Korumasını Etkinleştir'i** ve bölünebilir Ağ Koruması'na **değeri '0'** olarak ekleyin. (Ağ koruması varsayılan olarak etkindir)
    > [!div class="mx-imgBorder"]
    > ![Ağ koruma ilkesini etkinleştirme seçeneğinin görüntüsü](images/selectnp.png)
    
    > [!div class="mx-imgBorder"]
    > ![Yapılandırma ilkesi ekleme görüntüsü.](images/npvalue.png)
1. Kuruluşunuzda özel olabilecek kök CA'lar kullanılıyorsa, Defender'ın bunları sahte sertifika olarak algılamaması için Intune (MDM çözümü) ile kullanıcının cihazları arasında açık güven oluşturulması gerekir.  

    Kök CA'lar için güven oluşturmak için anahtar olarak **'Ağ Koruması için Güvenilen CA sertifika listesi (Önizleme)'** kullanın ve değer olarak **'sertifika parmak izlerinin virgülle ayrılmış listesini'** ekleyin.
    > [!div class="mx-imgBorder"]
    > ![Güvenilen CA sertifikasının görüntüsü.](images/trustca.png)

1. Ağ korumasıyla ilgili diğer yapılandırmalar için aşağıdaki anahtarları ve uygun değeri ekleyin.
<br>

    | Yapılandırma Anahtarı| Açıklama|
    |---|---|
    |Ağ Koruması Gizliliğini Etkinleştirme|1 - etkinleştir , 0 - Devre dışı bırak ; Bu ayar, ağ korumasında gizliliği etkinleştirmek veya devre dışı bırakmak için BT yöneticileri tarafından yönetilir.|
    |Kullanıcıların Ağlara ve Sertifikalara Güvenmesini Sağlama|1 - etkinleştir , 0 - Devre dışı bırak ; Bu ayar BT yöneticileri tarafından güvenli olmayan ve şüpheli ağlara ve kötü amaçlı sertifikalara güvenmek ve güvensiz bırakmak için son kullanıcı uygulama içi deneyimini etkinleştirmek veya devre dışı bırakmak için kullanılır.|
    |Ağ Koruma Uyarılarının Otomatik Olarak Düzeltilmesi|1 - etkinleştir , 0 - Devre dışı bırak ; Bu ayar, bir kullanıcı daha güvenli bir Wi-Fi erişim noktasına geçme veya Defender tarafından algılanan şüpheli sertifikaları silme gibi düzeltme etkinlikleri gerçekleştirdiğinde gönderilen düzeltme uyarılarını etkinleştirmek veya devre dışı bırakmak için BT yöneticileri tarafından kullanılır|
1. İlkenin uygulanması gereken gerekli grupları ekleyin. İlkeyi gözden geçirin ve oluşturun.

## <a name="privacy-controls"></a>Gizlilik Denetimleri

> [!IMPORTANT]
> Android'de Uç Nokta için Microsoft Defender Gizlilik Denetimleri önizleme aşamasındadır. Aşağıdaki bilgiler, ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilebilen önceden yayımlanmış ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Android cihazlardan Uç Nokta için Defender tarafından gönderilen verileri yapılandırmak için aşağıdaki gizlilik denetimleri kullanılabilir:

|Tehdit Raporu     |Ayrıntılar      |
|--------------------|-------------|
|Kötü amaçlı yazılım raporu |Yöneticiler kötü amaçlı yazılım raporu için gizlilik denetimi ayarlayabilir - Gizlilik etkinleştirilirse, Uç Nokta için Defender kötü amaçlı yazılım uyarı raporunun bir parçası olarak kötü amaçlı yazılım uygulama adını ve diğer uygulama ayrıntılarını göndermez |
|Kimlik avı raporu |Yöneticiler kimlik avı raporu için gizlilik denetimi ayarlayabilir - Gizlilik etkinleştirilirse, Uç Nokta için Defender, kimlik avı uyarısı raporunun bir parçası olarak güvenli olmayan web sitesinin etki alanı adını ve ayrıntılarını göndermez |
|Uygulamaların güvenlik açığı değerlendirmesi (yalnızca Android) |Varsayılan olarak yalnızca iş profilinde yüklü uygulamalar hakkındaki bilgiler güvenlik açığı değerlendirmesi için gönderilir. Yöneticiler kişisel uygulamaları dahil etmek için gizliliği devre dışı bırakabilir|

## <a name="configure-vulnerability-assessment-of-apps-for-byod-devices"></a>KCG cihazları için uygulamaların güvenlik açığı değerlendirmesini yapılandırma

Android'de Uç Nokta için Microsoft Defender'ın 1.0.3425.0303 sürümünden, eklenen mobil cihazlarda yüklü işletim sistemi ve uygulamaların güvenlik açığı değerlendirmelerini çalıştırabilirsiniz.

> [!NOTE]
> Güvenlik açığı değerlendirmesi, Uç Nokta için [Microsoft Defender'da Microsoft Defender Güvenlik Açığı Yönetimi'nin](../defender-vulnerability-management/defender-vulnerability-management.md) bir parçasıdır. 

**Kişisel cihazlardan (KCG) gelen uygulamalarla ilgili gizlilikle ilgili notlar:**

- İş profili olan Android Kurumsal için yalnızca iş profilinde yüklü uygulamalar desteklenir.
- Diğer KCG modları için varsayılan olarak uygulamaların güvenlik açığı değerlendirmesi **etkinleştirilmez** . Ancak, cihaz yönetici modundayken, yöneticiler cihazda yüklü uygulamaların listesini almak için Microsoft Endpoint Manager aracılığıyla bu özelliği açıkça etkinleştirebilir. Daha fazla bilgi için aşağıdaki ayrıntılara bakın.

### <a name="configure-privacy-for-device-administrator-mode"></a>Cihaz yöneticisi modu için gizliliği yapılandırma

Hedeflenen kullanıcılar için **cihaz yöneticisi** modundaki **cihazlardan uygulamaların güvenlik açığı değerlendirmesini etkinleştirmek** için aşağıdaki adımları kullanın. 

> [!NOTE]
> Varsayılan olarak, cihaz yöneticisi moduna kayıtlı cihazlar için bu kapalıdır.

1. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) **Cihazlar** > **Yapılandırma profilleri** > **Profil oluştur'a** gidin ve aşağıdaki ayarları girin:

   - **Platform**: Android cihaz yöneticisini seçin
   - **Profil**: "Özel" öğesini seçin ve Oluştur'a tıklayın

2. **Temel Bilgiler** bölümünde profilin adını ve açıklamasını belirtin.

3. **Yapılandırma ayarlarında** **OMA-URI** ayarı ekle'yi seçin:

   - **Ad**: Daha sonra kolayca bulabilmeniz için bu OMA-URI ayarı için benzersiz bir ad ve açıklama girin.
   - OMA-URI: **./Vendor/MSFT/DefenderATP/DefenderTVMPrivacyMode**
   - Veri türü: Açılan listeden Tamsayı'yı seçin.
   - Değer: Gizlilik ayarını devre dışı bırakmak için 0 girin (Varsayılan olarak değer 1'dir)

4. **İleri'ye** tıklayın ve bu profili hedeflenen cihazlara/kullanıcılara atayın.

### <a name="configure-privacy-for-android-enterprise-work-profile"></a>Android Kurumsal iş profili için gizliliği yapılandırma

Uç Nokta için Defender, iş profilindeki uygulamaların güvenlik açığı değerlendirmesini destekler. Ancak, bu özelliği hedeflenen kullanıcılar için kapatmak istiyorsanız aşağıdaki adımları kullanabilirsiniz:

1. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) **Uygulamalar Uygulama** > **yapılandırma ilkeleri** > **Yönetilen cihazlar** **ekle'ye** >  gidin.
2. İlkeye bir ad verin; **Android Kurumsal> platform**; profil türünü seçin.
3. Hedef uygulama olarak **Uç Nokta için Microsoft Defender'ı** seçin.
4. Ayarlar sayfasında **Yapılandırma tasarımcısını kullan'ı** seçin ve anahtar ve değer türü olarak **DefenderTVMPrivacyMode** değerini **Tamsayı** olarak ekleyin
   - İş profilindeki uygulamaların güvenlik açığını devre dışı bırakmak için olarak `1` değer girin ve bu ilkeyi kullanıcılara atayın. Varsayılan olarak, bu değer olarak `0`ayarlanır.
   - anahtar kümesi olan `0`kullanıcılar için Uç Nokta için Defender, güvenlik açığı değerlendirmesi için uygulama listesini iş profilinden arka uç hizmetine gönderir.
5. **İleri'ye** tıklayın ve bu profili hedeflenen cihazlara/kullanıcılara atayın.

Yukarıdaki gizlilik denetimlerini açmak veya kapatmak, cihaz uyumluluk denetimini veya koşullu erişimi etkilemez.

## <a name="configure-privacy-for-phishing-alert-report"></a>Kimlik avı uyarısı raporu için gizliliği yapılandırma

Kimlik avı raporu için gizlilik denetimi, kimlik avı tehdit raporunda etki alanı adı veya web sitesi bilgilerinin toplanmasını devre dışı bırakmak için kullanılabilir. Bu, kuruluşlara, uç nokta için Defender tarafından kötü amaçlı veya kimlik avı web sitesi algılandığında ve engellendiğinde etki alanı adını toplamak isteyip istemediklerini seçme esnekliği sağlar.

### <a name="configure-privacy-for-phishing-alert-report-on-android-device-administrator-enrolled-devices"></a>Android Cihaz Yöneticisi kayıtlı cihazlarda kimlik avı uyarısı raporu için gizliliği yapılandırın:

Hedeflenen kullanıcılar için açmak için aşağıdaki adımları kullanın:

1. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) **Cihazlar** > **Yapılandırma profilleri** > **Profil oluştur'a** gidin ve aşağıdaki ayarları girin:

   - **Platform**: Android cihaz yöneticisi'ni seçin.
   - **Profil**: "Özel" öğesini seçin ve **Oluştur'a** tıklayın.

2. **Temel Bilgiler** bölümünde profilin adını ve açıklamasını belirtin.

3. **Yapılandırma ayarlarında** **OMA-URI** ayarı ekle'yi seçin:

   - **Ad**: Daha sonra kolayca bulabilmeniz için bu OMA-URI ayarı için benzersiz bir ad ve açıklama girin.
   - OMA-URI: **./Vendor/MSFT/DefenderATP/DefenderExcludeURLInReport**
   - Veri türü: Açılan listeden Tamsayı'yı seçin.
   - Değer: Gizlilik ayarını etkinleştirmek için 1 girin. Varsayılan değer: 0.

4. **İleri'ye** tıklayın ve bu profili hedeflenen cihazlara/kullanıcılara atayın.

Bu gizlilik denetiminin kullanılması cihaz uyumluluk denetimini veya koşullu erişimi etkilemez.

### <a name="configure-privacy-for-phishing-alert-report-on-android-enterprise-work-profile"></a>Android Kurumsal iş profilinde kimlik avı uyarı raporu için gizliliği yapılandırma

İş profilinde hedeflenen kullanıcılar için gizliliği açmak için aşağıdaki adımları kullanın:

1. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) **Uygulamalar Uygulama** > **yapılandırma ilkeleri** > **Yönetilen cihazlar** **ekle'ye** >  gidin.
2. İlkeye Bir ad verin( **Platform > Android Kurumsal**), profil türünü seçin.
3. Hedef uygulama olarak **Uç Nokta için Microsoft Defender'ı** seçin.
4. Ayarlar sayfasında **Yapılandırma tasarımcısını kullan'ı** seçin ve anahtar ve değer türü Olarak **DefenderExcludeURLInReport** değerini **Tamsayı** olarak ekleyin.
   - **Gizliliği etkinleştirmek için 1** girin. Varsayılan değer: 0.
5. **İleri'ye** tıklayın ve bu profili hedeflenen cihazlara/kullanıcılara atayın.

Yukarıdaki gizlilik denetimlerini açmak veya kapatmak, cihaz uyumluluk denetimini veya koşullu erişimi etkilemez.

## <a name="configure-privacy-for-malware-threat-report"></a>Kötü amaçlı yazılım tehdit raporu için gizliliği yapılandırma

Kötü amaçlı yazılım tehdit raporu için gizlilik denetimi, kötü amaçlı yazılım tehdit raporundan uygulama ayrıntılarının (ad ve paket bilgileri) toplanmasını devre dışı bırakmak için kullanılabilir. Bu, kuruluşlara kötü amaçlı bir uygulama algılandığında uygulama adını toplamak isteyip istemediklerini seçme esnekliği sağlar.

### <a name="configure-privacy-for-malware-alert-report-on-android-device-administrator-enrolled-devices"></a>Android Cihaz Yöneticisi tarafından kaydedilen cihazlarda kötü amaçlı yazılım uyarısı raporu için gizliliği yapılandırma:

Hedeflenen kullanıcılar için açmak için aşağıdaki adımları kullanın:

1. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) **Cihazlar** > **Yapılandırma profilleri** > **Profil oluştur'a** gidin ve aşağıdaki ayarları girin:

   - **Platform**: Android cihaz yöneticisi'ni seçin.
   - **Profil**: "Özel" öğesini seçin ve **Oluştur'a** tıklayın.

2. **Temel Bilgiler** bölümünde profilin adını ve açıklamasını belirtin.

3. **Yapılandırma ayarlarında** **OMA-URI** ayarı ekle'yi seçin:

   - **Ad**: Daha sonra kolayca bulabilmeniz için bu OMA-URI ayarı için benzersiz bir ad ve açıklama girin.
   - OMA-URI: **./Vendor/MSFT/DefenderATP/DefenderExcludeAppInReport**
   - Veri türü: Açılan listeden Tamsayı'yı seçin.
   - Değer: Gizlilik ayarını etkinleştirmek için 1 girin. Varsayılan değer: 0.

4. **İleri'ye** tıklayın ve bu profili hedeflenen cihazlara/kullanıcılara atayın.

Bu gizlilik denetiminin kullanılması cihaz uyumluluk denetimini veya koşullu erişimi etkilemez. Örneğin, kötü amaçlı bir uygulamaya sahip cihazlar her zaman "Orta" risk düzeyine sahip olur.

### <a name="configure-privacy-for-malware-alert-report-on-android-enterprise-work-profile"></a>Android Kurumsal iş profilinde kötü amaçlı yazılım uyarısı raporu için gizliliği yapılandırma

İş profilinde hedeflenen kullanıcılar için gizliliği açmak için aşağıdaki adımları kullanın:

1. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) **Uygulamalar Uygulama** > **yapılandırma ilkeleri** > **Yönetilen cihazlar** **ekle'ye** >  gidin.
2. İlkeye Bir ad verin( **Platform > Android Kurumsal**), profil türünü seçin.
3. Hedef uygulama olarak **Uç Nokta için Microsoft Defender'ı** seçin.
4. Ayarlar sayfasında **Yapılandırma tasarımcısını kullan'ı** seçin ve anahtar ve değer türü olarak **DefenderExcludeAppInReport** değerini **Tamsayı** olarak ekleyin
   - **Gizliliği etkinleştirmek için 1** girin. Varsayılan değer: 0.
5. **İleri'ye** tıklayın ve bu profili hedeflenen cihazlara/kullanıcılara atayın.

Bu gizlilik denetiminin kullanılması cihaz uyumluluk denetimini veya koşullu erişimi etkilemez. Örneğin, kötü amaçlı bir uygulamaya sahip cihazlar her zaman "Orta" risk düzeyine sahip olur.

## <a name="related-topics"></a>İlgili konular

- [Android'de Uç Nokta için Microsoft Defender’a genel bakış](microsoft-defender-endpoint-android.md)
- [Android’de Uç Nokta için Defender’ı Microsoft Intune ile dağıtın](android-intune.md)
