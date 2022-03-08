---
title: Android'de Uç Nokta için Microsoft Defender'daki güncelleştirmeler
description: Android'de Uç Nokta için Microsoft Defender'ın önceki sürümlerine yapılan önemli değişiklikler hakkında bilgi öğrenin.
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mac, yükleme, macos, whatsnew
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: reference
ms.technology: mde
ms.openlocfilehash: d250fefbdcc2c268563b6321ee7d91eca4881063
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328701"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-android"></a>Android'de Uç Nokta için Microsoft Defender'daki güncelleştirmeler

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="microsoft-defender-for-endpoint-is-now-microsoft-defender-in-the-play-store"></a>Uç Nokta için Microsoft Defender artık Play Store'da Microsoft Defender oldu

Uç Nokta için Microsoft Defender artık play **Store'da Microsoft Defender** olarak kullanılabilir. Bu güncelleştirmeyle uygulama, ABD bölgesinde tüketiciler için önizleme olarak satışa sunulmaktadır. Uygulamada iş veya kişisel hesabınızla nasıl oturum açtırdınıza bağlı olarak, Uç Nokta için Microsoft Defender özelliklerine veya bireyler için Microsoft Defender'ın özelliklerine erişebilirsiniz. Daha fazla bilgi [için lütfen bu bloga](https://www.microsoft.com/en-us/microsoft-365/microsoft-defender-for-individuals) bakın.

## <a name="threat-and-vulnerability-management"></a>Tehdit ve Güvenlik Açığı Yönetimi

25 Ocak 2022'de, Android ve iOS'ta Tehdit ve Güvenlik Açığı yönetiminin genel olarak kullanılabilir olduğunu duyurmuştuk. Daha fazla ayrıntı için buradaki [techcommunity gönderisi'ne bakın](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/announcing-general-availability-of-vulnerability-management/ba-p/3071663).

## <a name="upcoming-permission-changes-for-microsoft-defender-for-endpoint-running-android-11-or-later-nov-2021"></a>Android 11 veya sonraki sürümü çalıştıran Uç nokta için Microsoft Defender'da yaklaşan izin değişiklikleri (Kasım 2021)

Sürüm Derlemesi: 1.0.3501.0301 Sürüm ayı: Uç Nokta için Kasım 2021 Microsoft Defender, [Google'ın](https://developer.android.com/distribute/play-policies#APILevel30) Android API 30'a yükseltmek için gerekli olan bu güncelleştirmeyi yayınlandı. Bu değişiklik, Android 11 veya [daha sonraki bir sürümü](https://developer.android.com/training/data-storage/manage-all-files#all-files-access-google-play) çalıştıran cihazlar için yeni depolama izni isteyen kullanıcılara soracak. Kullanıcıların Defender uygulamasını sürüm 1.0.3501.0301 veya daha yeni bir sürümle güncelleştirecekleri zaman bu yeni depolama iznini kabul etmeleri gerekir. Bu, uç noktanın uygulama güvenlik özelliği için Defender'ın hiçbir kesinti olmadan çalışmasını sağlar. Daha fazla bilgi için aşağıdaki bölümleri gözden geçirebilirsiniz.

**Bu, organizasyonlarınızı nasıl etkiler:** Bu değişiklikler, Android 11 veya sonraki bir sürümü çalıştıran cihazlarda Uç Nokta için Microsoft Defender'ı ve 1.0.3501.0301 veya daha sonraki derlemeleri yayım yapmak için Uç Nokta için Defender'ı kullanıyorsanız yürürlüğe girecektir.

> [!NOTE]
> Yeni depolama izinleri, yönetici tarafından izinler aracılığıyla "Otomatik Onayla" olarak yapılandır Microsoft Endpoint Manager. Kullanıcının bu izine erişim sağlamak için işlem ihtiyacı vardır.

- **Kullanıcı deneyimi:** Kullanıcılar, uygulama güvenliği için izinlerin eksik olduğunu belirten bir bildirim alır. Kullanıcı bu izni yoksayıyorsa, cihazda 'Uygulama güvenliği' işlevi kapalı olur. Kullanıcı izni kabul etmez veya reddetmezse, cihazı kilitlerken veya uygulamayı aken onay olana kadar istem almaya devam eder.

> [!NOTE]
> Organizasyonunız 'Tamper protection' özelliğinin önizlemesini görüntüleniyorsa ve kullanıcıya en son sürüme güncelleştirmeden sonra 7 gün içinde yeni depolama izinleri verilmezse, kullanıcı şirket kaynaklarına erişimi kaybedebilir.

**Hazırlanmak için gerekenler:**

1.0.3501.0301 veya daha sonraki bir sürümü oluşturmak için Uç Nokta için Defender'ı güncelleştirildikten sonra istendiğinde kullanıcılarınızı ve yardım masasına (uygulan uygulansa) bilgilendirin. İzinleri kabul etmek için kullanıcıların:

1. Uç nokta için Defender uygulama içinde bildirimine dokunun veya Uç nokta için Defender uygulamasını açın. Kullanıcılar gereken izinleri listeen bir ekran görebilirler. Bu iznin yanında yeşil bir onay Depolama eksik.

2. **Başlat'a dokunun**.

3. Tüm dosyaların yönetimi için **erişime izin ver iki durumlu düğmesine dokunun.**

4. Cihaz artık korunuyor.

  > [!NOTE]
  > Bu izin, Uç Nokta için Microsoft Defender'ın kötü amaçlı ve istenmeyen uygulamaları algılamaya ve kaldırmaya yardımcı olan kullanıcının cihazında depolamaya erişmesini sağlar. Yalnızca Uç Nokta erişimi için Microsoft Defender Android uygulama paketi dosyasına (.apk) erişer/tarar. İş Profili olan cihazlarda, Uç Nokta için Defender yalnızca işle ilgili dosyaları tarar.
