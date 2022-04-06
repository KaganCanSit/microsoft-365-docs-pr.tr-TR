---
title: Android'de Uç Nokta için Microsoft Defender sorunları giderme
description: Android'de Uç Nokta için Microsoft Defender sorunları giderme
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mde, android, bulut, bağlantı, iletişim
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
ms.openlocfilehash: 574e02c837ce1f2e3639ed562ed52bacc0e67629
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64472231"
---
# <a name="troubleshooting-issues-on-microsoft-defender-for-endpoint-on-android"></a>Android'de Uç Nokta için Microsoft Defender sorunları giderme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Bu deneyimi Uç Nokta için Microsoft Defender? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Bir cihazı eklemeye başladıktan sonra uygulama yüklendikten sonra oturum açma sorunlarıyla karşı görüşebilirsiniz.

Ekleme sırasında, uygulama cihazınıza yüklendikten sonra oturum açma sorunlarıyla karşılaşabilirsiniz.

Bu makale, oturum açma sorunlarının çözümüne yardımcı olacak çözümler sunar.

## <a name="sign-in-failed---unexpected-error"></a>Oturum açma başarısız - beklenmeyen hata

**Oturum açma başarısız: Beklenmeyen** *hata, daha sonra deneyin*

:::image type="content" source="images/f9c3bad127d636c1f150d79814f35d4c.png" alt-text="Oturum açma hatası Microsoft Defender 365 portalının oturum açma sayfasında beklenmeyen hata." lightbox="images/f9c3bad127d636c1f150d79814f35d4c.png":::

**İleti:**

Beklenmeyen hata, daha sonra deneyin

**Neden:**

Aygıtınızda "Microsoft Authenticator" uygulamasının eski bir sürümü yüklü.

**Çözüm:**

Google Play Store'dan [Microsoft Authenticator](https://play.google.com/store/apps/details?id=com.azure.authenticator) sürümü ve diğer uygulamaları yükleyin ve yeniden deneyin.

## <a name="sign-in-failed---invalid-license"></a>Oturum açma başarısız - geçersiz lisans

**Oturum açma başarısız: Geçersiz** *lisans, lütfen yöneticiye başvurun*

:::image type="content" source="images/920e433f440fa1d3d298e6a2a43d4811.png" alt-text="Microsoft Defender 365 portalının oturum açma sayfasındaki yönergelerin ilgili kişi ayrıntıları" lightbox="images/920e433f440fa1d3d298e6a2a43d4811.png":::

**İleti:** *Geçersiz lisans, lütfen yöneticiye başvurun*

**Neden:**

Atanmış lisans Microsoft 365 yoksa veya kuruluş aboneliğiniz için lisans Microsoft 365 Kurumsal yok.

**Çözüm:**

Yardım için yöneticinize başvurun.

## <a name="report-unsafe-site"></a>Güvenli olmayan siteyi bildirme

Kimlik avı web siteleri, kişisel veya finansal bilgilerinizi almak amacıyla güvenilir web sitelerinin kimliğine bürünüler. Kimlik avı [sitesi olabilir bir web sitesini](https://www.microsoft.com/wdsi/filesubmission/exploitguard/networkprotection) rapor etmek için Ağ koruması hakkında geri bildirim sağlama sayfasını ziyaret edin.

## <a name="phishing-pages-arent-blocked-on-some-oem-devices"></a>Kimlik avı sayfaları bazı OEM cihazlarda engellenmiş değildir

**Aşağıdakiler için geçerlidir:** Yalnızca belirli OEM'ler

- **Xiaomi**

Android için Uç Nokta için Defender tarafından algılanan kimlik avı ve zararlı web tehditleri bazı Xiaomi cihazlarda engellanmaz. Aşağıdaki işlevler bu cihazlarda çalışmıyor.

:::image type="content" source="images/0c04975c74746a5cdb085e1d9386e713.png" alt-text="Sitenin güvenli olmayan bildirim iletisi" lightbox="images/0c04975c74746a5cdb085e1d9386e713.png":::

**Neden:**

Xiaomi cihazları yeni bir izin modeli içerir. Bu, Android için Uç Nokta Defender'ın arka planda çalışırken açılır pencereleri görüntülemesini önler.

Xiaomi cihazları izni: "Arka planda çalışırken açılır pencereleri görüntüle."

:::image type="content" source="images/6e48e7b29daf50afddcc6c8c7d59fd64.png" alt-text="Microsoft Defender 365 portalında açılır pencere ayarları bölmesi" lightbox="images/6e48e7b29daf50afddcc6c8c7d59fd64.png":::

**Çözüm:**

Xiaomi cihaz üzerinde gerekli izni etkinleştirin.

- Arka planda çalışırken açılır pencereleri görüntüleme.

## <a name="unable-to-allow-permission-for-permanent-protection-during-onboarding-on-some-oem-devices"></a>Bazı OEM cihazlarda ekleme sırasında "Kalıcı koruma" iznine izin veremiyor

**Aşağıdakiler için geçerlidir:** Yalnızca belirli OEM cihazları.

- **Android 11 ile Xiaomi**

Defender Uygulaması, uygulama eklemenin bir parçası olarak cihazlarda Pil İyileştirme/Kalıcı Koruma izni isterse ve İzin Ver'i seçmek, izin ayarlanana kadar bir hata verir. Yalnızca "Kalıcı Koruma" adlı son izni etkiler. 

**Neden:**

Xiaomi, Android 11'de pil iyileştirme izinlerini değiştirdi. Uç nokta için Defender'ın pil iyileştirmelerini yoksaymak üzere bu ayarı yapılandırmasına izin verilmiyor.

**Çözüm:**

Uygulama ekleme ekranından bu izni etkinleştirmeye olanak sağlayacak bir çözüm bulmak için OEM ile birlikte çalışıyoruz. Bu sorun çözul olduğunda belgeleri güncelleştiriz.
Kullanıcılar cihaz ayarlarından aynı izinleri etkinleştirmek için şu adımları izleyin: 

1. Cihazınızın **Ayarlar** Git'e gidin.

2. Pil İyileştirme'yi **ara ve seçin**.

   :::image type="content" source="images/search-battery-optimisation.png" alt-text="Aramanızı ve Pil İyimserleme'yi seçerek ilgili sayfa" lightbox="images/search-battery-optimisation.png":::

3. Özel **uygulama erişiminde Pil** **İyileştirme'yi seçin**.

   :::image type="content" source="images/special-app-access.png" alt-text="Pil İyiliği'ni seçerek ulaşabilirsiniz Özel uygulama erişim bölmesi" lightbox="images/special-app-access.png":::

4. Tüm Uygulamaları göstermek için Açılan **Liste'ye göz atabilirsiniz**.

   :::image type="content" source="images/show-all-apps-2.png" alt-text="Pil İyileştirilmiş Bölmesi'nin altında değeri Tüm Uygulamalar olarak değiştirebilirsiniz açılan liste" lightbox="images/show-all-apps-2.png":::

   :::image type="content" source="images/show-all-apps-1.png" alt-text="Pil İyileştirilmiş Bölmesi'nin altında Tüm Uygulamalar seçeneğini gösteren açılan liste" lightbox="images/show-all-apps-1.png":::

5. "Uç Nokta için Microsoft Defender" öğesini bulun ve **En İyi Duruma Getirme'yi seçin**.

   :::image type="content" source="images/select-dont-optimise.png" alt-text="En İyi Duruma Getirme seçeneğinin Uç Nokta için Microsoft Defender ve seçimine olanak sağlayan sayfa" lightbox="images/select-dont-optimise.png":::

Kullanıcı ekleme Uç Nokta için Microsoft Defender dönerek İzin Ver'i **seçin;** pano ekranına yönlendirildisiniz.

## <a name="send-in-app-feedback"></a>Uygulama içinde geri bildirim gönderme

Kullanıcı yukarıdaki bölümlerde henüz çözüme ulaşamayan veya listelenen adımların kullanamadığı bir sorunla karşı karşıya geliyorsa, kullanıcı tanılama verileriyle birlikte uygulama içinde  geri **bildirim de sağlar**. Bundan sonra ekibimiz doğru çözümü sağlamak için günlükleri inceler. Kullanıcılar aynı şeyi yapmak için aşağıdaki adımları takip eder:

1.  Aygıtınızda **MDE** uygulamasını açın ve sol **üst köşedeki** profil simgesine tıklayın.

    :::image type="content" source="images/select-profile-icon-1.jpg" alt-text="Portalda profil Uç Nokta için Microsoft Defender simgesi" lightbox="images/select-profile-icon-1.jpg":::

2.  "Yardım ve geri &" öğesini seçin.

    :::image type="content" source="images/selecthelpandfeedback2.png" alt-text="& Uç Nokta için Microsoft Defender portalında seçilecek Yardım ve geri Uç Nokta için Microsoft Defender seçeneği" lightbox="images/selecthelpandfeedback2.png":::

3.  "Microsoft'a geri bildirim gönder" öğesini seçin.

    :::image type="content" alt-text="Microsoft'a geri bildirim gönder'i seçin" source="images/send-feedback-to-microsoft-3.jpg":::

4.  Verilen seçeneklerden birini belirleyin. Bir sorunu rapor etmek için "Bir sorunu rapor etmek istiyorum" seçeneğini seçin.

    :::image type="content" source="images/report-issue-4.jpg" alt-text="Bir sorunu rapor etmek istiyorum seçeneği" lightbox="images/report-issue-4.jpg":::

5.  Karşılaştığınız sorunun ayrıntılarını iletin ve "Tanılama verilerini gönder" konusunu kontrol edin. Ekibin bir çözüm veya izleme ile size geri dönesin için "E-posta adresinizi dahil edin" ifadesini denetlemenizi öneririz.

    :::image type="content" source="images/finalsubmit5.png" alt-text="Ayrıntıları ek iliştirmek ve tanılama verilerini eklemek için bölme" lightbox="images/finalsubmit5.png":::

6.  Geri bildirimi başarıyla göndermek için "Gönder"e tıklayın.
