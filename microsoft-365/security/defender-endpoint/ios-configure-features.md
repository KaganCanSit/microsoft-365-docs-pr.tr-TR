---
title: iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın
description: Uç Nokta için Microsoft Defender iOS özelliklerine nasıl dağıtılacağı açıklanır.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, ios, configure, features, ios
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 8defbb5d1a72afd13110d3c76a4770e40ac1c469
ms.sourcegitcommit: 66228a5506fdceb4cbf0d55b9de3f2943740134f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66089317"
---
# <a name="configure-microsoft-defender-for-endpoint-on-ios-features"></a>iOS özelliklerinde Uç Nokta için Microsoft Defender’ı yapılandırın

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> iOS'da Uç Nokta için Defender, Web Koruması özelliğini sağlamak için bir VPN kullanır. Bu normal bir VPN değildir ve cihazın dışına trafiği almayan yerel/kendi kendini döngüye alan bir VPN'dir.

## <a name="conditional-access-with-defender-for-endpoint-on-ios"></a>iOS'de Uç Nokta için Defender ile Koşullu Erişim

Microsoft Intune ve Azure Active Directory ile birlikte iOS Uç Nokta için Microsoft Defender, cihaz risk puanına göre Cihaz uyumluluğu ve Koşullu Erişim ilkelerinin zorunlu tutmasını sağlar. Uç Nokta için Defender, Intune aracılığıyla bu özelliği kullanmak için dağıtabileceğiniz bir Mobile Threat Defense (MTD) çözümüdür.

iOS'da Uç Nokta için Defender ile Koşullu Erişim ayarlama hakkında daha fazla bilgi için bkz. [Uç Nokta için Defender ve Intune](/mem/intune/protect/advanced-threat-protection).

### <a name="jailbreak-detection-by-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender tarafından jailbreak algılama

Uç Nokta için Microsoft Defender, jailbreak uygulanmış yönetilmeyen ve yönetilen cihazları algılama özelliğine sahiptir. Bir cihazın jailbreak gerçekleştirildiği algılanırsa, Microsoft 365 Defender portalına **yüksek** riskli bir uyarı bildirilir ve Koşullu Erişim cihaz risk puanına göre ayarlanırsa cihazın şirket verilerine erişimi engellenir.

## <a name="web-protection-and-vpn"></a>Web Koruması ve VPN

Varsayılan olarak, iOS'da Uç Nokta için Defender web koruma özelliğini içerir ve etkinleştirir. [Web koruması](web-protection-overview.md) , cihazların web tehditlerine karşı korunmasına ve kullanıcıların kimlik avı saldırılarına karşı korunmasına yardımcı olur. Web Koruması'nın bir parçası olarak kimlik avı önleme ve özel göstergelerin (URL ve IP adresleri) desteklendiğini unutmayın. Web İçeriği Filtreleme şu anda iOS'da desteklenmiyor.

iOS'de Uç Nokta için Defender bu özelliği sağlamak için bir VPN kullanır. Bunun yerel bir VPN olduğunu ve geleneksel VPN'nin aksine ağ trafiğinin cihazın dışına gönderilmediğini lütfen unutmayın.

Varsayılan olarak etkinleştirildiğinde VPN'yi devre dışı bırakmanızı gerektiren bazı durumlar olabilir. Örneğin, VPN yapılandırıldığında çalışmayan bazı uygulamaları çalıştırmak istiyorsunuz. Bu gibi durumlarda, aşağıdaki adımları izleyerek cihazdaki uygulamadan VPN'i devre dışı bırakabilirsiniz:

1. iOS cihazınızda **Ayarlar** uygulamasını açın, **Genel'e** ve ardından **VPN'e** tıklayın veya dokunun.

2. Uç Nokta için Microsoft Defender için "i" düğmesine tıklayın veya dokunun.

3. VPN'yi devre dışı bırakmak için **İsteğe Bağlı Bağlan** kapatın. 

   :::image type="content" source="images/ios-vpn-config.png" alt-text="VPN yapılandırmasının iki durumlu düğmesi isteğe bağlı olarak Bağlan seçeneği" lightbox="images/ios-vpn-config.png":::

> [!NOTE]
> VPN devre dışı bırakıldığında Web Koruması kullanılamaz. Web Koruması'nı yeniden etkinleştirmek için cihazda Uç Nokta için Microsoft Defender uygulamasını açın ve **VPN Başlat'a** tıklayın veya dokunun.

## <a name="configure-network-protection"></a>Ağ Korumasını Yapılandırma
>[!NOTE] 
>Uç Nokta için Microsoft Defender'da Ağ Koruması artık genel önizleme aşamasındadır. Aşağıdaki bilgiler, ürünün ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilebilen ön sürümüyle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

Uç nokta için Microsoft Defender'da ağ koruması varsayılan olarak etkindir. Yöneticiler, iOS cihazlarda Ağ koruması için MAM desteğini yapılandırmak için aşağıdaki adımları kullanabilir.

1. Microsoft Endpoint Manager Yönetici'da Uygulamalar > Uygulama yapılandırma ilkeleri'ne gidin. Yeni bir Uygulama yapılandırma ilkesi oluşturun.
   :::image type="content" source="images/addiosconfig.png" alt-text="Yapılandırma ilkesi ekleyin." lightbox="images/addiosconfig.png":::
   
2. İlkeyi benzersiz olarak tanımlamak için bir ad ve açıklama sağlayın. Ardından 'Genel uygulamaları seç'e tıklayın ve Platform iOS/IPadOS için 'Microsoft Defender'ı seçin:::image type="content" source="images/nameiosconfig.png" alt-text=". Yapılandırmayı adlandırın." lightbox="images/nameiosconfig.png":::
   
3. Ayarlar sayfasında, Ağ Koruması'nı devre dışı bırakmak için anahtar olarak 'DefenderNetworkProtectionEnable' değerini ve 'false' olarak değeri ekleyin. (Ağ koruması varsayılan olarak etkindir) :::image type="content" source="images/addiosconfigvalue.png" alt-text="Yapılandırma değeri ekleyin." lightbox="images/addiosconfigvalue.png":::
   
4. Ağ korumasıyla ilgili diğer yapılandırmalar için aşağıdaki anahtarları ve uygun değeri ekleyin.

    |Tuş| Varsayılan (true-enable, false-disable)|Açıklama|
    |---|---|---|
    |DefenderEndUserTrustFlowEnable| False | Kullanıcıların Ağlara ve Sertifikalara Güvenmesini Sağlama|
    |DefenderNetworkProtectionAutoRemediation| True |Bu ayar, bir kullanıcı daha güvenli bir WIFI erişim noktasına geçme veya Defender tarafından algılanan şüpheli sertifikaları silme gibi düzeltme etkinlikleri gerçekleştirdiğinde gönderilen düzeltme uyarılarını etkinleştirmek veya devre dışı bırakmak için BT yöneticisi tarafından kullanılır|
    |DefenderNetworkProtectionPrivacy| True |Bu ayar, ağ korumasında gizliliği etkinleştirmek veya devre dışı bırakmak için BT yöneticisi tarafından yönetilir|
  
5. Atamalar bölümünde yönetici, ilkeye dahil etmek ve ilkeden dışlamak için kullanıcı gruplarını seçebilir.
   :::image type="content" source="images/assigniosconfig.png" alt-text="Yapılandırmayı atayın." lightbox="images/assigniosconfig.png":::
   
6. Yapılandırma ilkesini gözden geçirin ve oluşturun.

## <a name="co-existence-of-multiple-vpn-profiles"></a>Birden çok VPN profilinin birlikte bulunması

Apple iOS, cihaz genelinde birden çok VPN'in aynı anda etkin olmasını desteklemez. Cihazda birden çok VPN profili bulunabilir ancak aynı anda yalnızca bir VPN etkin olabilir.

## <a name="configure-microsoft-defender-for-endpoint-risk-signal-in-app-protection-policy-mam"></a>Uygulama koruma ilkesinde (MAM) Uç Nokta için Microsoft Defender risk sinyalini yapılandırma

Uç Nokta için Microsoft Defender, iOS/iPadOS'ta Uygulama Koruma İlkeleri'nde (MAM olarak da bilinir) kullanılacak tehdit sinyalleri gönderecek şekilde yapılandırılabilir. Bu özellik sayesinde, şirket verilerine erişimi kayıtlı olmayan cihazlardan korumak için de Uç Nokta için Microsoft Defender kullanabilirsiniz.

Uç Nokta için Microsoft Defender ile uygulama koruma ilkelerini ayarlama adımları aşağıdadır:

1. Microsoft Endpoint Manager kiracınızdan Uç Nokta için Microsoft Defender bağlantısını ayarlayın. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) **Kiracı Yönetim** \> **Bağlayıcıları ve belirteçleri Uç Nokta için Microsoft Defender (Platformlar** \> arası altında) veya **Endpoint Security** \> **Uç Nokta için Microsoft Defender** (Kurulum altında) bölümüne gidin ve  **iOS için Uygulama Koruma İlkesi Ayarlar**.

2. Kaydet'i seçin. **Bağlantı durumunun** artık **Etkin** olarak ayarlandığını görmeniz gerekir.

3. Uygulama koruma ilkesi oluşturma: Uç Nokta için Microsoft Defender bağlayıcı kurulumunuz tamamlandıktan sonra, yeni bir ilke oluşturmak veya var olan bir ilkeyi güncelleştirmek için **Uygulamalar** \> **Uygulama koruması ilkeleri'ne** gidin (İlke'nin altında).

4. Kuruluşunuzun ilkeniz için gerektirdiği platform, **Uygulamalar, Veri koruması, Erişim gereksinimleri** ayarlarını seçin.

5. **Koşullu başlatma** \> **Cihaz koşulları** altında **İzin verilen en fazla cihaz tehdit düzeyi** ayarını bulacaksınız. Bunun Düşük, Orta, Yüksek veya Güvenli olarak yapılandırılması gerekir. Kullanabileceğiniz eylemler **Erişimi engelle** veya **Verileri sil** olacaktır. Bağlayıcınızın bu ayardan önce ayarlandığından emin olmak için bilgilendirici bir iletişim kutusu görebilirsiniz. Bağlayıcınız zaten ayarlanmışsa, bu iletişim kutusunu yoksayabilirsiniz.

6. Ödevler ile bitirin ve ilkenizi kaydedin.

MAM veya uygulama koruma ilkesi hakkında daha fazla bilgi için bkz. [uygulama koruma ilkesi ayarlarını iOS](/mem/intune/apps/app-protection-policy-settings-ios).

### <a name="deploying-microsoft-defender-for-endpoint-for-mam-or-on-unenrolled-devices"></a>MAM için veya kaydı kaldırılmış cihazlarda Uç Nokta için Microsoft Defender dağıtma

iOS'da Uç Nokta için Microsoft Defender, Uygulama Koruma İlkesi senaryosuna olanak tanır ve Apple uygulama mağazasında kullanılabilir. Son kullanıcılar uygulamanın en son sürümünü doğrudan Apple uygulama mağazasından yüklemelidir.

## <a name="privacy-controls"></a>Gizlilik Denetimleri

> [!IMPORTANT]
> iOS'da Uç Nokta için Microsoft Defender için Gizlilik Denetimleri önizleme aşamasındadır. Aşağıdaki bilgiler, ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilebilen önceden yayımlanmış ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

### <a name="configure-privacy-in-phish-alert-report"></a>Kimlik avı uyarısı raporunda gizliliği yapılandırma

Müşteriler artık iOS Uç Nokta için Microsoft Defender tarafından gönderilen kimlik avı raporu için gizlilik denetimini etkinleştirebilir. Bu, bir kimlik avı web sitesi algılandığında ve Uç Nokta için Microsoft Defender tarafından engellendiğinde etki alanı adının kimlik avı uyarısının bir parçası olarak gönderilmemesini sağlar.

Gizliliği etkinleştirmek ve kimlik avı uyarısı raporunun bir parçası olarak etki alanı adını toplamamak için aşağıdaki adımları kullanın.

1. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) **Uygulamalar** > **Uygulama yapılandırma ilkeleri** > **Yönetilen cihazlar** **ekle'ye** >  gidin.

2. İlkeye **Platform > iOS/iPadOS** adını verin, profil türünü seçin.

3. Hedef uygulama olarak **Uç Nokta için Microsoft Defender'ı** seçin.

4. Ayarlar sayfasında **Yapılandırma tasarımcısını kullan'ı** seçin ve anahtar ve değer türü olarak **DefenderExcludeURLInReport** değerini **Boole olarak** ekleyin.

   - Gizliliği etkinleştirmek ve etki alanı adını toplamamak için olarak `true` değer girin ve bu ilkeyi kullanıcılara atayın. Varsayılan olarak, bu değer olarak `false`ayarlanır.

   - olarak ayarlanmış `true`anahtara sahip kullanıcılar için, kötü amaçlı bir site algılandığında ve Uç Nokta için Defender tarafından engellendiğinde kimlik avı uyarısı etki alanı adı bilgilerini içermez.

5. **İleri'ye** tıklayın ve bu profili hedeflenen cihazlara/kullanıcılara atayın.

Yukarıdaki gizlilik denetimlerini açmak veya kapatmak, cihaz uyumluluk denetimini veya koşullu erişimi etkilemez.

## <a name="configure-compliance-policy-against-jailbroken-devices"></a>Jailbreak uygulanmış cihazlara karşı uyumluluk ilkesini yapılandırma

Şirket verilerinin jailbreak uygulanmış iOS cihazlarda erişilmeye karşı korunması için Intune'de aşağıdaki uyumluluk ilkesini ayarlamanızı öneririz.

> [!NOTE]
> Jailbreak algılama, iOS Uç Nokta için Microsoft Defender tarafından sağlanan bir özelliktir. Ancak, bu ilkeyi jailbreak senaryolarına karşı ek bir savunma katmanı olarak ayarlamanızı öneririz.

Jailbreak uygulanmış cihazlara karşı uyumluluk ilkesi oluşturmak için aşağıdaki adımları izleyin.

1. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) **Cihaz** -> **Uyumluluk ilkeleri** -> **İlke Oluştur'a** gidin. Platform olarak "iOS/iPadOS" öğesini seçin ve **Oluştur'a** tıklayın.

   :::image type="content" source="images/ios-jb-policy.png" alt-text="İlke Oluştur sekmesi" lightbox="images/ios-jb-policy.png":::

1. İlkenin adını belirtin, örneğin "Jailbreak için Uyumluluk İlkesi".

1. Uyumluluk ayarları sayfasında **Cihaz Durumu** bölümünü genişletmek için tıklayın ve **Jailbreak uygulanmış cihazlar** için **engelle** alanına tıklayın.

   :::image type="content" source="images/ios-jb-settings.png" alt-text="Uyumluluk ayarları sekmesi" lightbox="images/ios-jb-settings.png":::

1. **Uyumsuzluk eylemleri** bölümünde, gereksinimlerinize göre eylemleri seçin ve **İleri'yi** seçin.

   :::image type="content" source="images/ios-jb-actions.png" alt-text="Uyumsuzluk eylemleri sekmesi" lightbox="images/ios-jb-actions.png":::

1. **Atamalar** bölümünde, bu ilke için eklemek istediğiniz kullanıcı gruplarını seçin ve ardından **İleri'yi** seçin.

1. **Gözden Geçir+Oluştur** bölümünde, girilen tüm bilgilerin doğru olduğunu doğrulayın ve **Oluştur'u** seçin.

## <a name="configure-custom-indicators"></a>Özel göstergeleri yapılandırma

iOS'de Uç Nokta için Defender, yöneticilerin iOS cihazlarda da özel göstergeler yapılandırmasına olanak tanır. Özel göstergeleri yapılandırma hakkında daha fazla bilgi için bkz. [Göstergeleri yönetme](/microsoft-365/security/defender-endpoint/manage-indicators).

> [!NOTE]
> iOS'de Uç Nokta için Defender, yalnızca IP adresleri ve URL'ler/etki alanları için özel göstergeler oluşturmayı destekler.

## <a name="configure-option-to-send-in-app-feedback"></a>Uygulama içi geri bildirim gönderme seçeneğini yapılandırma 

Müşteriler artık Uç Nokta için Defender uygulamasında Microsoft'a geri bildirim verileri gönderme özelliğini yapılandırma seçeneğine sahiptir. Geri bildirim verileri, Microsoft'un ürünleri geliştirmelerine ve sorunları gidermelerine yardımcı olur.

> [!NOTE]
> ABD Kamu bulut müşterileri için geri bildirim veri toplama varsayılan olarak **devre dışıdır** . 

Microsoft'a geri bildirim verileri gönderme seçeneğini yapılandırmak için aşağıdaki adımları kullanın:

1. [Microsoft Endpoint Manager yönetim merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) **Uygulamalar** > **Uygulama yapılandırma ilkeleri** > **Yönetilen cihazlar** **ekle'ye** >  gidin.

1. İlkeye **Platform > iOS/iPadOS** adını verin, profil türünü seçin.

1. Hedef uygulama olarak **Uç Nokta için Microsoft Defender'ı** seçin.

1. Ayarlar sayfasında **Yapılandırma tasarımcısını kullan'ı** seçin ve anahtar ve değer türü olarak **DefenderSendFeedback** değerini **Boole olarak** ekleyin.
   
   - Son kullanıcıların geri bildirim sağlama becerisini kaldırmak için değeri olarak `false` ayarlayın ve bu ilkeyi kullanıcılara atayın. Varsayılan olarak, bu değer olarak `true`ayarlanır. US Government müşterileri için varsayılan değer 'false' olarak ayarlanır.
   
   - anahtar kümesi olan `true`kullanıcılar için, uygulama içinde Microsoft'a Geri Bildirim verileri gönderme seçeneği vardır (Menü > Geri Bildirim & Yardım > Microsoft'a Geri Bildirim Gönder)

1. **İleri'ye** tıklayın ve bu profili hedeflenen cihazlara/kullanıcılara atayın.

## <a name="report-unsafe-site"></a>Güvenli olmayan siteyi bildir

Kimlik avı web siteleri, kişisel veya finansal bilgilerinizi almak amacıyla güvenilir web sitelerini taklit ediyor. Kimlik avı sitesi olabilecek bir web sitesini bildirmek istiyorsanız [Ağ koruması hakkında geri bildirim sağlayın](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) sayfasını ziyaret edin.
