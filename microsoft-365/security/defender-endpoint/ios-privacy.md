---
title: Gizlilik bilgileri - iOS'ta Uç Nokta için Microsoft Defender
ms.reviewer: ''
description: iOS'ta Uç Nokta için Microsoft Defender gizlilik bilgilerini açıklar
keywords: microsoft, defender, Endpoint için Microsoft Defender, ios, ilke, genel bakış
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
ms.openlocfilehash: 4fc5d4fb51170a70edc8664d5ccba0943b93353d
ms.sourcegitcommit: dfa9f28a5a5055a9530ec82c7f594808bf28d0dc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/29/2021
ms.locfileid: "62997032"
---
# <a name="privacy-information---microsoft-defender-for-endpoint-on-ios"></a>Gizlilik bilgileri - iOS'ta Uç Nokta için Microsoft Defender

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

> [!NOTE]
> iOS'ta Uç Nokta için Defender Web Koruma özelliğini sağlamak için VPN kullanır. Bu normal bir VPN değildir ve trafiği cihazın dışına almayan yerel veya kendi kendine döngülü bir VPN'tir. **Microsoft veya organizasyon, gözatma etkinliğinizi görmüyor.**

iOS'ta Uç Nokta için Defender, yapılandırılmış iOS cihazlarınız hakkında bilgi toplar ve bilgileri Uç Nokta için Defender'a sahip olduğunuz kiracıda depolar. Bilgiler iOS'ta Uç Nokta için Defender'ı güvenli, güncel, beklendiği şekilde performans gösteren ve hizmeti desteklemeye yardımcı olmak için toplanır.

Veri depolama hakkında daha fazla bilgi için bkz. Uç nokta [veri depolama ve gizlilik için Microsoft Defender](data-storage-privacy.md).

Android ve iOS mobil cihazlarda Uç Nokta için Microsoft Defender hakkında en yaygın gizlilik soruları hakkında daha fazla bilgi için bkz. Uç Nokta için [Microsoft Defender ve Android ve iOS mobil cihazlarda gizliliğiniz](https://support.microsoft.com/topic/microsoft-defender-for-endpoint-and-your-privacy-on-android-and-ios-mobile-devices-4109bc54-8ec5-4433-9c33-d359b75ac22a).

## <a name="required-data"></a>Gerekli veriler

Gerekli veriler, iOS'ta Uç Nokta için Defender'ın beklendiği gibi çalışması için gereken verilerden oluşur. Bu veriler hizmetin çalışması için çok önemlidir ve son kullanıcı, kuruluş, cihaz ve uygulamalarla ilgili verileri içerebilir.

Toplanan veri türlerinin listesi:

### <a name="web-page-or-network-information"></a>Web sayfası veya Ağ bilgileri

- Yalnızca kötü amaçlı bir bağlantı veya web sayfası algılandığında web sitesinin etki alanı adı ve IP adresi.

### <a name="device-and-account-information"></a>Cihaz ve hesap bilgileri

- Cihaz tanımlayıcısı aşağıdakilerden biri & saat, iOS sürümü, CPU bilgisi ve Cihaz tanımlayıcısı gibi cihaz bilgileri:
  - Wi-Fi bağdaştırıcısı MAC adresi
  - Rastgele oluşturulan genel benzersiz tanımlayıcı (GUID)
- Kiracı, Cihaz ve Kullanıcı bilgileri
  - Azure Active Directory (AD) Cihaz Kimliği ve Azure Kullanıcı Kimliği - Cihazı, sırasıyla Azure Active Directory'deki Kullanıcı olarak benzersiz olarak tanımlar.
  - Azure kiracı kimliği - iş yer alan ve organizasyon organizasyonlarınızı tanımlayan GUID Azure Active Directory.
  - Uç Nokta kuruluş kimliği için Microsoft Defender - Cihazın ait olduğu kuruluşla ilişkilendirilmiş benzersiz tanımlayıcı. Microsoft'un, belirli bir kuruluş dizisini etkileyen sorunlar olup olduğunu ve bundan etkilediği kuruluşların sayısını belirlemesini sağlar.
  - Kullanıcı Asıl Adı - Kullanıcının e-posta kimliği.

### <a name="product-and-service-usage-data"></a>Ürün ve hizmet kullanım verileri

Aşağıdaki bilgiler yalnızca cihazda yüklü Uç Nokta uygulaması için Microsoft Defender için toplanır.

- Ad, sürüm ve uygulama yükseltme durumu dahil olmak üzere uygulama paketi bilgileri.
- Uygulamada yapılan eylemler.
- iOS tarafından oluşturulan kilitlenme raporu günlükleri.
- Bellek kullanımı verileri.

## <a name="optional-data"></a>İsteğe Bağlı Veriler

İsteğe bağlı veriler tanılama verilerini ve istemciden gelen geri bildirim verilerini içerir. İsteğe bağlı tanılama verileri ürün geliştirmeleri yapmamıza yardımcı olan ve sorunları algılamamıza, tanılamamıza ve çözmemize yardımcı olacak ileri düzey bilgi sağlayan ek verilerdir. Bu veriler yalnızca tanılama amaçlıdır ve hizmetin kendisi için gerekli değildir.

İsteğe bağlı tanılama verileri şunları içerir:

- Uç Nokta için Defender'ın uygulama, CPU ve ağ kullanımı.
- Uç nokta için Defender yöneticisi tarafından yapılandırılan özellikler.

Geri Bildirim Verileri, kullanıcı tarafından sağlanan uygulama içinde geri bildirim aracılığıyla toplanır.

- Sağlamayı tercih ettiyse kullanıcının e-posta adresi.
- Geri bildirim türü (gülümseme, kaş çatma, fikir) ve kullanıcı tarafından gönderilen tüm geri bildirim yorumları.

Daha fazla bilgi için bkz. [Gizlilik hakkında daha fazla bilgi](https://aka.ms/mdatpiosprivacystatement).
