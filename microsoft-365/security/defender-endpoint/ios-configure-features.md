---
title: iOS Uç Nokta için Microsoft Defender yapılandırma
description: iOS özellikleri üzerinde Uç Nokta için Microsoft Defender dağıtımı açıklarıdır.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, ios, yapılandırma, özellikler, ios
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
ms.openlocfilehash: c52fac7c5680d8e5f814098410dc2e1993328d2f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64476917"
---
# <a name="configure-microsoft-defender-for-endpoint-on-ios-features"></a>iOS Uç Nokta için Microsoft Defender yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

> [!NOTE]
> iOS'ta Uç Nokta için Defender, Web Koruma özelliğini sağlamak için VPN kullanıyor olabilir. Bu normal bir VPN değildir ve trafiği cihazın dışına almayan yerel/kendi kendine döngülü bir VPN'tir.

## <a name="conditional-access-with-defender-for-endpoint-on-ios"></a>iOS'ta Uç Nokta için Defender ile Koşullu Erişim

Uç Nokta için Microsoft Defender uyumluluk ve güvenlik Microsoft Intune Azure Active Directory, cihaz risk puanına göre Cihaz uyumluluğu ve Koşullu Erişim ilkelerinin zorlanmalarına olanak sağlar. Uç Nokta için Defender, bir Mobil Tehdit Savunma (MTD) çözümüdür ve diğer bir Intune.

iOS'ta Uç Nokta için Defender ile Koşullu Erişim'i ayarlama hakkında daha fazla bilgi için bkz. Uç Nokta [için Defender ve Intune](/mem/intune/protect/advanced-threat-protection).

### <a name="jailbreak-detection-by-microsoft-defender-for-endpoint"></a>Uç Nokta için Microsoft Defender'den jailbreak algılama

Uç Nokta için Microsoft Defender, yönetilemeyen ve yönetilen cihazlarabroklık (brok) sahip olmayan cihazları algılama özelliğine sahiptir. Bir cihazın bir cihaza izin verili olduğu algılanırsa, Microsoft 365 Defender portalına yüksek riskli bir uyarı bildirilir ve Koşullu Erişim cihaz risk puanına göre ayarlanırsa, cihazın şirket verilerine erişimi engellenir.

## <a name="web-protection-and-vpn"></a>Web Koruması ve VPN

Varsayılan olarak, iOS'ta Uç Nokta için Defender web koruma özelliğini içerir ve sağlar. [Web koruması,](web-protection-overview.md) cihazların web tehditlerine karşı güvenliğini korumaya ve kullanıcıları kimlik avı saldırılarından korumaya yardımcı olur. Web Koruması kapsamında Kimlik avıyla mücadele ve özel göstergelerin (URL ve IP adresleri) desteklenelerine dikkat edin. Web İçeriği Filtreleme şu anda iOS'ta desteklenmiyor.

iOS'ta Uç Nokta için Defender bu özelliği sağlamak için VPN kullanır. Bu yerel bir VPN'tir ve geleneksel VPN'den farklı olarak ağ trafiği cihazın dışına gönderilmez.

Varsayılan olarak etkin durumdayken VPN'yi devre dışı bırakmanızı gerektiren bazı durumlar olabilir. Örneğin, VPN yapılandırıldığında çalışmayan bazı uygulamaları çalıştırmak istiyor olun. Böyle durumlarda, aşağıdaki adımları takip edin ve VPN'yi cihazdan devre dışı bırakmayı seçebilirsiniz:

1. iOS aygıtınızda, **Genel'e ve Ayarlar** **VPN'ye** tıklayın **veya** dokunun.
1. "i" düğmesine tıklayarak veya dokunarak Uç Nokta için Microsoft Defender.
1. VPN'yi devre **Bağlan için On Demand özelliğini** kapatın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-vpn-config.png" alt-text="Isteğe bağlı VPN yapılandırma ve isteğe Bağlan iki durumlu düğmesi" lightbox="images/ios-vpn-config.png":::

> [!NOTE]
> VPN devre dışı bırakılmıştır, Web Koruması kullanılamaz. Web Koruması'yı yeniden etkinleştirmek için Uç Nokta için Microsoft Defender VPN'yi başlat'a tıklayın **veya dokunun**.

## <a name="co-existence-of-multiple-vpn-profiles"></a>Birden çok VPN profilinin birlikte varlığı

Apple iOS, aynı anda etkin olmak için cihaz genelinde birden çok VPN'i desteklemez. Cihazda birden çok VPN profili mevcut olabilir ama aynı anda yalnızca bir VPN etkin olabilir.

## <a name="configure-microsoft-defender-for-endpoint-risk-signal-in-app-protection-policy-mam"></a>Uygulama Uç Nokta için Microsoft Defender ilkesinde (MAM) risk sinyalini yapılandırma

Uç Nokta için Microsoft Defender, iOS/iPadOS'ta Uygulama Koruma İlkeleri'sinde (MAM olarak da bilinir) kullanılacak tehdit işaretleri göndermek üzere ya da yapılandırabilirsiniz. Bu özellik sayesinde, Uç Nokta için Microsoft Defender erişimi kaydı olmayan cihazlardan da korumak için Uç Nokta için Microsoft Defender'i kullanabilirsiniz.

Aşağıdaki adımları kullanarak uygulama koruma ilkelerini Uç Nokta için Microsoft Defender adımları verilmiştir:

1. Kiracınız ve kiracınız Microsoft Endpoint Manager bağlantısını Uç Nokta için Microsoft Defender. [Microsoft Uç](https://go.microsoft.com/fwlink/?linkid=2109431) Nokta Yöneticisi yönetim merkezinde Kiracı  \>  \> Yönetimi Bağlayıcıları ve belirteçleri **Uç Nokta için Microsoft Defender** (Platformlar arası altında)  \> veya Uç Nokta Güvenliği **Uç Nokta için Microsoft Defender'e** (Kurulum altında) **gidin ve iOS için Ayarlar Koruma İlkesi.**
1. Kaydet'i seçin. Bağlantı **durumu'nın artık Etkin** olarak ayar olduğunu **görüyor olun**.
1. Uygulama koruma ilkesi oluşturma: Uç Nokta için Microsoft Defender bağlayıcısı kurulumunu tamamlandıktan sonra,  \> Yeni bir ilke oluşturmak **veya var olan** bir ilkeyi güncelleştirmek için Uygulama ayarları Uygulama koruması ilkeleri'ne (İlke'nin altında) gidin.
1. İlkeniz için **kuruma gereken platform, Uygulamalar,** Veri koruması, Erişim gereksinimleri ayarlarını seçin.
1. Koşullu **başlatma Cihaz** \> **koşulları altında** İzin verilen en yüksek cihaz tehdit **düzeyi ayarını bulabilirsiniz**. Bunun Düşük, Orta, Yüksek veya Güvenli olarak yapılandırılması gerekir. Sizin için kullanılabilir eylemler Erişimi engelle **veya Verileri** **temizle'dir**. Bu ayar etkili olmadan önce bağlayıcınızı ayar tam olarak hazır bulunduracak bir bilgilendirme iletişim kutusu görüntüebilirsiniz. Bağlayıcınız zaten ayarlanmışsa bu iletişim kutusunu yoksayabilirsiniz.
1. Ödevler ile bitirin ve ilkenizi kaydedin.

MAM veya uygulama koruma ilkesi hakkında daha fazla ayrıntı için [bkz. iOS uygulama koruma ilkesi ayarları](/mem/intune/apps/app-protection-policy-settings-ios).

### <a name="deploying-microsoft-defender-for-endpoint-for-mam-or-on-unenrolled-devices"></a>KAYDı Uç Nokta için Microsoft Defender ve kaydı olmayan cihazlarda uygulama dağıtma

Uç Nokta için Microsoft Defender'daki kullanıcılar Uygulama Koruma İlkesi senaryosunu etkinleştirir ve Apple App Store'da kullanılabilir.

Son kullanıcıların uygulamanın en son sürümünü doğrudan Apple Uygulama Mağazası'dan yüklemeleri gerekir.

## <a name="privacy-controls"></a>Gizlilik Denetimleri

> [!IMPORTANT]
> iOS'ta Uç Nokta için Microsoft Defender için Gizlilik Denetimleri önizlemededir. Aşağıdaki bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilabilecek, önceden satın alınan ürünle ilgilidir. Microsoft, burada sağlanan bilgilerle ilgili olarak açık veya zımni hiçbir garanti vermez.

### <a name="configure-privacy-in-phish-alert-report"></a>Kimlik avı uyarı raporunda gizliliği yapılandırma

Müşteriler artık iOS'ta kimlik avı raporu tarafından gönderilen kimlik Uç Nokta için Microsoft Defender denetimi etkinleştirebilirsiniz. Bu, kimlik avı web sitesi bir kimlik avı web sitesi tarafından algılandığında ve engellandığında kimlik avı uyarısının bir parçası olarak etki alanı adının Uç Nokta için Microsoft Defender.

Gizliliği etkinleştirmek ve kimlik avı uyarı raporunun bir parçası olarak etki alanı adını toplamak için aşağıdaki adımları kullanın.

1. Bu [Microsoft Endpoint Manager ve](https://go.microsoft.com/fwlink/?linkid=2109431) **AppsApp** >  >  yapılandırma **ilkeleriAddManaged** >  **cihazlar'a gidin**.
1. İlkeye bir ad ver: **iOS/iPadOS >** Platform Ayarları, profil türünü seçin.
1. Hedef **Uç Nokta için Microsoft Defender** olarak Seç'i seçin.
1. Uygulama Ayarlar, Yapılandırma tasarımcısını **kullan'ı** seçin ve **DefenderExcludeURLInReport** öğesini anahtar ve değer türü **Boolean olarak ekleyin**.
   - Gizliliği etkinleştirmek ve etki alanı adını toplamak için, bu ilkeyi farklı `true` bir değer girin ve kullanıcılara attayabilirsiniz. Varsayılan olarak, bu değer olarak ayarlanır `false`.
   - Anahtar olarak ayarlanmış kullanıcılar için `true`, kötü amaçlı bir site Uç Nokta için Defender tarafından algılandığında ve engellandığında kimlik avı uyarısı etki alanı adı bilgilerini içermez.
1. **Sonraki'ne** tıklayın ve bu profili hedefli cihazlara/kullanıcılara attayin.

Yukarıdaki gizlilik denetimlerini açma veya kapatma, cihaz uyumluluğu denetimi veya koşullu erişimi etkilemez.

## <a name="configure-compliance-policy-against-jailbroken-devices"></a>Broken cihazlara karşı uyumluluk ilkesi yapılandırma

Şirket verilerini, bir yayından uzak iOS cihazlarında erişime karşı korumak için bu cihazlarda aşağıdaki uyumluluk Intune.

> [!NOTE]
> Jailbreak algılama, iOS'ta Uç Nokta için Microsoft Defender tarafından sağlanan bir özelliktir. Bununla birlikte, bu ilkeyi, jailbreak senaryolarına karşı ek bir savunma katmanı olarak ayarlamanız önerilir.

Aşağıdaki adımları takip edin vebroken cihazlara karşı bir uyumluluk ilkesi oluşturun.

1. Cihaz [Microsoft Endpoint Manager merkezinde](https://go.microsoft.com/fwlink/?linkid=2109431) **DevicesCompliance** ->  **policiesCreate** ->  **Policy (** İlkeYi) seçin. Platform olarak "iOS/iPadOS" öğesini seçin ve Oluştur'a **tıklayın**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-jb-policy.png" alt-text="İlke Oluştur sekmesi" lightbox="images/ios-jb-policy.png":::

2. İlkenin adını belirtin, örneğin "Jailbreak için Uyumluluk İlkesi".
3. Uyumluluk ayarları sayfasında Cihaz Durumu bölümünü genişletmek için **tıklayın ve** sonra da Block **forBroken devices** (Mobil cihaz ayarları için engelle) alanına tıklayın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-jb-settings.png" alt-text="Uyumluluk ayarları sekmesi" lightbox="images/ios-jb-settings.png":::

4. **Tamamlanamazlık eylemleri bölümünde**, gereksinimlerinize göre eylemleri seçin ve sonra da Sonraki'yi **seçin**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/ios-jb-actions.png" alt-text="Tamamlanamazlık için Eylemler sekmesi" lightbox="images/ios-jb-actions.png":::

5. Atamalar **bölümünde** , bu ilkeye dahil etmek istediğiniz kullanıcı gruplarını seçin ve sonra da Sonraki'yi **seçin**.
6. Gözden Geçir **+Oluştur bölümünde** , girilen tüm bilgilerin doğru olduğunu doğrulayın ve ardından Oluştur'a **tıklayın**.

## <a name="configure-custom-indicators"></a>Özel göstergeleri yapılandırma

iOS'ta Uç Nokta için Defender yöneticilerin iOS cihazlarda da özel göstergeler yapılandırmasını sağlar. Özel göstergeleri yapılandırma hakkında daha fazla bilgi için bkz. [Göstergeleri yönetme](/microsoft-365/security/defender-endpoint/manage-indicators).

> [!NOTE]
> iOS'ta Uç Nokta için Defender yalnızca IP adresleri ve URL'ler/etki alanları için özel göstergeler oluşturmayı destekler.

## <a name="configure-option-to-send-in-app-feedback"></a>Uygulama içinde geri bildirim gönderme seçeneğini yapılandırma 

Müşteriler artık Uç nokta için Defender uygulamasından Microsoft'a geri bildirim verileri gönderme olanağını yapılandırma seçeneğine sahip. Geri bildirim verileri Microsoft'un ürünleri geliştirmesine ve sorunları gidermesine yardımcı olur.

> [!NOTE]
> US Government cloud müşterileri için, geri bildirim veri toplama varsayılan **olarak devre dışı** bırakılmıştır. 

Microsoft'a geri bildirim verileri gönderme seçeneğini yapılandırmak için aşağıdaki adımları kullanın:

1. Bu [Microsoft Endpoint Manager ve](https://go.microsoft.com/fwlink/?linkid=2109431) **AppsApp** >  >  yapılandırma **ilkeleriAddManaged** >  **cihazlar'a gidin**.
1. İlkeye bir ad ver: **iOS/iPadOS >** Platform Ayarları, profil türünü seçin.
1. Hedef **Uç Nokta için Microsoft Defender** olarak Seç'i seçin.
1. Uygulama Ayarlar, Yapılandırma tasarımcısını **kullan'ı** seçin ve anahtar ve değer **türü olarak Boolean olarak DefenderSendFeedback'i** **ekleyin**.
   - Son kullanıcıların geri bildirim sağlama yeteneğini kaldırmak için, değeri bu ilke olarak `false` ayarlayın ve kullanıcılara attayın. Varsayılan olarak, bu değer olarak ayarlanır `true`. ABD Kamu müşterileri için varsayılan değer 'false' olarak ayarlanır.
   - Olarak ayarlanmış olan kullanıcılar için `true`uygulama içinde Microsoft'a Geri Bildirim verileri gönderme seçeneği olacaktır (Menü > Geri Bildirim & Microsoft'> Gönderme)
1. **Sonraki'ne** tıklayın ve bu profili hedefli cihazlara/kullanıcılara attayin.


## <a name="report-unsafe-site"></a>Güvenli olmayan siteyi bildirme

Kimlik avı web siteleri, kişisel veya finansal bilgilerinizi almak amacıyla güvenilir web sitelerinin kimliğine bürünüler. Kimlik avı [sitesi olabilir bir web sitesini](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) rapor etmek için Ağ koruması hakkında geri bildirim sağlama sayfasını ziyaret edin.
