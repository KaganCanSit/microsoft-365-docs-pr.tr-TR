---
title: Android'de Uç Nokta için Microsoft Defender - Gizlilik bilgileri
description: Gizlilik denetimleri, Android'de Uç Nokta için Microsoft Defender'da toplanan tanılama verileri hakkında gizliliği ve bilgileri etkileyen ilke ayarlarını yapılandırma.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, android, gizlilik, tanılama
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 6772539f4ca4ea819a0f8cd2a92a817fcea650f3
ms.sourcegitcommit: 7fd1bcbd8246501029837e3ea92adea64c3406e1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2022
ms.locfileid: "62974131"
---
# <a name="microsoft-defender-for-endpoint-on-android---privacy-information"></a>Android'de Uç Nokta için Microsoft Defender - Gizlilik bilgileri

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Android'de Uç Nokta için Defender yapılandırılmış Android cihazlarından bilgileri toplar ve bilgileri Uç Nokta için Defender'a sahip olduğu kiracıda depolar. Bilgiler, Android için Defender'ı güvenli, güncel, beklendiği şekilde performans gösteren ve hizmeti desteklemeye yardımcı olmak için toplanır.

Veri depolama hakkında daha fazla bilgi için bkz. Uç nokta [veri depolama ve gizlilik için Microsoft Defender](data-storage-privacy.md).

Bilgiler, Android için Defender'ın güvenli, güncel, beklendiği şekilde performans gösteren ve hizmeti desteklemesini sağlamak için toplanır.

Android ve iOS mobil cihazlarda Uç Nokta için Microsoft Defender hakkında en yaygın gizlilik soruları hakkında daha fazla bilgi için bkz. Uç Nokta için [Microsoft Defender ve Android ve iOS mobil cihazlarda gizliliğiniz](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-and-your-privacy-on-android-and-ios-mobile-devices-4109bc54-8ec5-4433-9c33-d359b75ac22a).

## <a name="required-data"></a>Gerekli Veriler

Gerekli veriler, Android için Uç Nokta için Defender'ın beklendiği gibi çalışması için gereken verilerden oluşur. Bu veriler hizmetin çalışması için çok önemlidir ve son kullanıcı, kuruluş, cihaz ve uygulamalarla ilgili verileri içerebilir. Toplanan veri türlerinin listesi:

### <a name="app-information"></a>Uygulama bilgileri

Cihazda kötü **amaçlı** Android uygulama paketleri (APK) hakkında bilgiler

- Kaynak yükle
- Depolama APK'nin konumlarını (dosya yolu)
- Yükleme zamanı, APK boyutu ve izinler

Android Enterprise Tam yönetilen cihazlar için - Cihazda yüklü Android uygulama paketleri (APK) hakkında bilgiler

- Uygulamanın adı ve paket adı
- Uygulamanın sürüm numarası
- Satıcı adı

İş profili Enterprise Android uygulamaları için - Cihazın İş profilinde yüklü Olan Android uygulama paketleri (APK'ler) hakkında bilgiler

- Uygulamanın adı ve paket adı
- Uygulamanın sürüm numarası
- Satıcı adı

*Ayrıca, kuruluşlarınız cihazda yüklü olan tüm uygulamalar hakkında bilgi göndermek üzere Uç Nokta için Defender'ı yapılandırmayı da seçebilir. Varsayılan olarak, bu bilgiler kuruluşa gönderilmez.*


### <a name="web-page--network-information"></a>Web sayfası / Ağ bilgileri

- Web sitesinin tam URL'si, ancak kötü amaçlı bir bağlantı veya web sayfası algılandığında ve engellenmişse.
- Bağlantı bilgileri
- Protokol türü (HTTP, HTTPS gibi)

### <a name="device-and-account-information"></a>Cihaz ve hesap bilgileri

- Tarih saat, Android &, OEM modeli, CPU bilgisi ve Cihaz tanımlayıcısı gibi cihaz bilgileri.
- Cihaz tanımlayıcısı aşağıdakilerden biridir:
  - Wi-Fi bağdaştırıcısı MAC adresi
  - [Android kimliği](https://developer.android.com/reference/android/provider/Settings.Secure#ANDROID_ID) (cihazın ilk önyüklemesinde Android tarafından oluşturulan şekilde).
  - Rastgele oluşturulmuş genel benzersiz tanımlayıcı (GUID).

- Kiracı, Cihaz ve Kullanıcı bilgileri
  - Azure Active Directory (AD) Cihaz Kimliği ve Azure Kullanıcı Kimliği: Cihazı, sırasıyla Azure Active Directory'deki Kullanıcı olarak benzersiz olarak tanımlar.
  - Azure kiracı kimliği: Kısa süre içinde kuruluş kimliğini tanımlayan GUID Azure Active Directory.
  - Uç nokta kuruluş kimliği için Microsoft Defender: Cihazın ait olduğu kuruluşla ilişkilendirilmiş benzersiz tanımlayıcı. Microsoft'un belirli bir kuruluş setlerini etkileyen sorunları ve kaç işletmeyi etkile ilgili olduğunu belirlemesi için Microsoft'a olanak sağlar.
  - Kullanıcı Asıl Adı: Kullanıcının e-posta kimliği

### <a name="product-and-service-usage-data"></a>Ürün ve hizmet kullanım verileri

Aşağıdaki bilgiler yalnızca cihazda yüklü Uç Nokta uygulaması için Microsoft Defender için toplanır. 

- Ad, sürüm ve uygulama yükseltme durumu dahil olmak üzere uygulama paketi bilgileri.
- Uygulamada gerçekleştirilen eylemler.
- Tehdit adı, kategori vb. tehdit algılama bilgileri
- Android tarafından oluşturulan kilitlenme raporu günlükleri.

## <a name="optional-data"></a>İsteğe Bağlı Veriler

İsteğe bağlı veriler tanılama verilerini ve geri bildirim verilerini içerir. İsteğe bağlı tanılama verileri ürün geliştirmeleri yapmamıza yardımcı olan ve sorunları algılamamıza, tanılamamıza ve çözmemize yardımcı olacak ileri düzey bilgi sağlayan ek verilerdir. İsteğe bağlı tanılama verileri şunları içerir:

- Uygulama, CPU ve ağ kullanımı.
- Cihazın durumu uygulama açısından bakıldığında, tarama durumu, tarama zamanlamaları, verilen uygulama izinleri ve yükseltme durumu gibi durumları içerir.
- Yönetici tarafından yapılandırılan özellikler.
- Cihaz üzerinde tarayıcılar hakkında temel bilgiler.

**Geri Bildirim** Verileri, kullanıcı tarafından sağlanan uygulama içinde geri bildirim aracılığıyla toplanır

- Sağlamayı tercih ettiyse kullanıcının e-posta adresi.
- Geri bildirim türü (gülümseme, kaş çatma, fikir) ve kullanıcı tarafından gönderilen tüm geri bildirim yorumları.
