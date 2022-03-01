---
title: Raporlarla çalışma
description: Microsoft Yönetilen Masaüstü'nden kullanılabilen çeşitli raporlar
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 620e9d2bd95dc4782237af94966b5cb52579b656
ms.sourcegitcommit: 19e16b16f144159b55bb4c544403e3642b69e335
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2022
ms.locfileid: "63015264"
---
# <a name="work-with-reports"></a>Raporlarla çalışma

Bu Microsoft Endpoint Manager konsolu, Azure AD kuruluşunuzun ("kiracı") yapılandırması ve cihazlarıyla ilgili sorunları izlemenize ve araştırmanıza yardımcı olmak için çeşitli ürünlerden gelen raporları tek bir konumda bir araya getirir.

Microsoft Yönetilen Masaüstü'nin, Raporlar menüsünde **Microsoft** Yönetilen Masaüstü'ne özgü kayıtlı cihazların yönetimine özgü raporları bulamıyorum. Rapor genelinde çeşitli Microsoft Endpoint Manager, diğer ürün gruplarından gelen raporlara filtre ebilirsiniz. Microsoft Yönetilen Masaüstü tarafından yönetilen cihazları dahil veya hariç tutabilirsiniz.

## <a name="microsoft-managed-desktop-reports"></a>Microsoft Yönetilen Masaüstü raporları

Microsoft Yönetilen Masaüstü çeşitli raporlar ve panolar sağlar. Kuruluş içinde yer alan IT yöneticileri, cihaz popülasyonu hakkında çeşitli özellikleri anlamak için bu raporları ve panoları kullanabilir. Daha Microsoft Endpoint Manager Raporlar bölümüne gidin ve Microsoft Yönetilen Masaüstü altında Yönetilen cihazlar'ı seçin.

Özet **sekmesinde** , cihaz güncelleştirmeleri hakkında hızlı ölçümler bulabilirsiniz. **Metrik için temel** alınan veri kümesi de dahil olmak üzere çevrimdışı çözümlemeye ilişkin ek bilgileri indirmek üzere herhangi bir ölçümün ayrıntılarını görüntüle'yi seçin.

Raporlar sekmesini **seçerek** , kullanılabilir ayrıntılı raporların açıklamalarını görebilirsiniz. Bu raporlar portalda daha kapsamlı ve destek veri görselleştirme ve filtrelemedir. Çevrimdışı çözümleme veya dağıtım için temel alınan verileri de dışarı aktarabilirsiniz. Aşağıdaki raporlar bugün kullanılabilir:

| Rapor | Açıklama |
| ------ | ------ |
| [**Cihaz durumu** raporu](device-status-report.md) (*önizlemede*) | Bu rapor, cihaz etkinliği ve kullanımına bağlı olarak Microsoft Yönetilen Masaüstü hizmetini kullanımınızı gösterir. |
| **Cihaz durumu eğilimi** (*önizlemede*) | Bu, Microsoft Yönetilen Masaüstü cihazlarınız için cihaz durumundaki eğilimleri son 60 gün boyunca izler. Eğilimler, cihaz durumunu zaman içinde yapılan diğer değişikliklerle, örneğin yeni dağıtımlarla ilişkilendirmeye yardımcı olabilir. |
| [**Windows güncelleştirmeleri** raporu](security-updates-report.md) (*önizlemede*) | Bu rapor, Microsoft Windows tüm güvenlik güncelleştirmelerinin nasıl yayın olduğunu gösterir. |
| [**Uygulama kullanımı** raporu](app-usage-report.md) | Bu rapor, Microsoft Yönetilen Masaüstü cihazlarınız genelinde genel uygulama kullanımı hakkında bilgi sağlar. Cihazların bu rapora veri sağlayabiliyor olması için, bunların İsteğe bağlı tanılama veri düzeyine ayarlanmış olması gerekir. |
| [**Hizmet Ölçümleri Raporu**](service-metrics-report.md) (*önizlemede*) | Bu rapor, Microsoft Yönetilen Masaüstü ay-aya göre temel ölçümlerinin basit özetlerini sağlar. |

## <a name="endpoint-analytics"></a>Uç nokta analizi

Microsoft Yönetilen Masaüstü artık Uç nokta analiziyle [tümleştirilmiştir](/mem/analytics/overview). Bu raporlar, size kuruluşlarının çalışma ve kullanıcılarınızı ifade edilen deneyimin kalitesini ölçmeyle ilgili içgörüler sağlar. Uç nokta çözümlemelerini, raporlar **menüsünün Raporlar** menüsünde [Microsoft Endpoint Manager](https://endpoint.microsoft.com/). Puanı yalnızca Microsoft Yönetilen Masaüstü tarafından yönetilen cihazları içerecek şekilde özetlerken herhangi bir rapora gidin, Filtre açılan listesini  seçin ve ardından Microsoft Yönetilen Masaüstü **cihazları'nı seçin**.

Kayıt sırasında Uç nokta analizi Azure AD organizasyonunız ("kiracı") için otomatik olarak yapılandırılmamışsa, bunu kendiniz de kullanabilirsiniz. Daha fazla bilgi için bkz. [Uç nokta analizi portalına ekleme](/mem/analytics/enroll-intune#bkmk_onboard). Tüm cihazlarınızı kaydedebilirsiniz veya yalnızca Microsoft Yönetilen Masaüstü cihazlarını dahil etmek için Test, İlk, Hızlı ve Geniş çalışma alanı **için modern** çalışma alanı cihaz gruplarını seçin. Bu raporlar için farklı izinler gerekli olabilir. Daha fazla bilgi için bkz [. Uygun](/mem/analytics/overview#permissions) rollere sahip olmak için İzinler.

> [!NOTE]
> Kullanıcı gizliliğine daha iyi saygılı olmak için, bu filtreyi kullanmak üzere Uç nokta analizi ile kaydolan 10'dan fazla Microsoft Yönetilen Masaüstü cihazı olmalıdır.

## <a name="intune-reports"></a>Intune raporları

Microsoft Intune, cihazları sizin adına yönetmek için hizmetlerimizden biridir.

Bazı durumlarda, Intune raporlarını kullanarak Microsoft Yönetilen Masaüstü cihazlarınızı özel olarak izlemek yararlı olabilir. Diğer cihazları yönetmek için raporun dışında tutabilirsiniz. Aşağıdaki raporlar, Microsoft Yönetilen Masaüstü cihazlarını dahil etme veya hariç tutabilirsiniz.

- [Tüm cihazlar](/mem/intune/remote-actions/device-management#get-to-your-devices)
- [Cihaz uyumluluğu](/mem/intune/fundamentals/reports#device-compliance-report-organizational)
- [Uyumlu olmayan cihazlar](/mem/intune/fundamentals/reports#noncompliant-devices-report-operational)

> [!NOTE]
> Özel Microsoft Yönetilen Masaüstü rolleri yalnızca Microsoft Yönetilen Masaüstü raporlarına erişimi garantiler. Tüm cihazlar gibi Microsoft Endpoint Manager bölümlerine **erişmek** için bkz. [Microsoft Intune'de rol tabanlı erişim denetimi](/mem/intune/fundamentals/role-based-access-control).

## <a name="microsoft-managed-desktop-inventory-data"></a>Microsoft Yönetilen Masaüstü stok verileri

Diğer raporlara ek olarak, Microsoft Yönetilen Masaüstü tarafından yönetilen cihazlarla ilgili bilgileri de dışarı aktarabilirsiniz. Daha Microsoft Endpoint Manager, Microsoft Yönetilen Masaüstü altında Cihazlar'ı seçin ve Ayrıntılı stok raporunu indirmek için Tüm  cihazları [dışarı aktar sekmesini kullanın](device-inventory-report.md). 
