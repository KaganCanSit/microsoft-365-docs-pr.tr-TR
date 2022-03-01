---
title: Microsoft Yönetilen Masaüstü'de güncelleştirmeler nasıl yönetilir?
description: Microsoft Yönetilen Masaüstü'nü güncel tutmak bir hız ve kararlılık dengesidir.
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: bf6ead692a82d485f6a8e3b3148bc05484c887a8
ms.sourcegitcommit: 9f0e84835121ce6228fdc69182c24be7ad1cb20e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015461"
---
# <a name="how-updates-are-handled-in-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü'de güncelleştirmeler nasıl yönetilir?

<!--This topic is the target for a "Learn more" link in the Admin Portal (aka.ms/update-rings); do not delete.-->

<!--Update management -->

Microsoft Yönetilen Masaüstü tüm cihazları modern bir bulut tabanlı altyapıya bağlar.

Sistem Windows, Office, üretici yazılımı ve İş İçin Microsoft Store uygulamalarını güncel tutmak bir hız ve kararlılık dengesidir. İşletim sistemi güncelleştirmelerinin ve ilkelerinin güvenli bir şekilde sağlanması için güncelleştirme gruplarını kullanıyoruz. Daha fazla bilgi için Microsoft Yönetilen Masaüstü [Değişikliği ve Sürüm Süreci videosunu izleyin](https://www.microsoft.com/videoplayer/embed/RE4mWqP).

Microsoft tarafından yayımlanan güncelleştirmeler kümülatiftir ve kalite veya özellik güncelleştirmeleri olarak kategorilere ayrılmıştır. Daha fazla bilgi için bkz. [Windows Güncelleştirme: Güncelleştirme türleri](/windows/deployment/update/waas-manage-updates-wufb#update-types).

## <a name="update-groups"></a>Grupları güncelleştirme

Microsoft Yönetilen Masaüstü güncelleştirmeleri yönetmek için dört Azure AD grubu kullanır:

| Grup | Açıklama |
| ------ | ------ |
| Test | Microsoft Yönetilen Masaüstü ilkesi değişikliklerini, işletim sistemi güncelleştirmelerini, özellik güncelleştirmelerini ve Azure AD kuruluşuna gönderilirken yapılan diğer değişiklikleri doğrulamak ("kiracı") için kullanılır. Test grubu şöyledir: <br><ul><li>Test etmek veya erken geri bildirim sağlay kullanıcılar için en iyisidir.</li><li>Herhangi bir hizmet düzeyi sözleşmesi ve kullanıcı desteği dışında tutulabilirsiniz.</li><li>Uygulamaların uyumluluğunu yeni ilke veya işletim sistemi değişiklikleriyle doğrulamak için kullanılabilir.</li></ul> |
| Birinci | Yayın öncesi güncelleştirmelere tabi olan erken yazılım benimseyenleri ve cihazları içerir. <br><br> Test halkası içinde test sırasında kapsamı ele olmayan senaryolar varsa, bu gruptaki cihazlar kesintiler ile karşılanmış olabilir. |
| Hızlı | Kararlılık üzerinden hızı önceliklendirme. Hızlı grubu: <br><ul><li>Broad grubuna teklifte gelmeden önce kalite sorunlarını algılamak için yararlıdır.</li> <li>Bir sonraki doğrulama katmanıdır ve normalde Test ve Birinci gruplardan daha kararlıdır.</li></ul> |
| Geniş | Bu grup, özellik ve kalite güncelleştirmelerini edinen son gruptur. <br><br> Broad grubu, Azure AD kuruluşunda çoğu kullanıcının yer alır ve dolayısıyla dağıtım hızına olumlu bir tercih sağlar. Ortam en kararlı olduğundan, uygulama testi bu grupla yapılabilir. |

### <a name="moving-devices-between-update-groups"></a>Cihazları güncelleştirme grupları arasında taşıma

Bazı cihazların güncelleştirmeleri en son almalarını ve bazılarının ise önce gitmek istemelerini sebilirsiniz. Bu cihazları uygun güncelleştirme grubuna taşımak için bkz. [Dağıtım grubuna cihazlar atama](../working-with-managed-desktop/assign-deployment-group.md).

Bu dağıtım grupları içindeki roller ve sorumluluklar hakkında daha fazla bilgi için [bkz. Microsoft Yönetilen Masaüstü Rolleri ve sorumlulukları](../intro/roles-and-responsibilities.md)

### <a name="using-microsoft-managed-desktop-update-groups"></a>Microsoft Yönetilen Masaüstü güncelleştirme gruplarını kullanma

Hizmetin, uygulama dağıtımı gibi yönetmekle ilgili bazı bölümleri vardır ve bu bölümlerin tüm yönetilen cihazları hedeflemesi gerekebilir.

## <a name="update-deployment"></a>Dağıtımı güncelleştirme

Aşağıda, güncelleştirme dağıtımının nasıl çalıştığını açıklanmıştır.

| Adım | Açıklama |
| ------ | ------ |
| 1. Adım | Microsoft Yönetilen Masaüstü, aşağıdaki tabloda belirtilen zamanlamayı göre yeni bir özellik veya kalite güncelleştirmesi dağıtıyor.|
| 2. Adım | Dağıtım sırasında Microsoft Yönetilen Masaüstü, tanılama verilerine ve kullanıcı destek sistemine bağlı hata veya kesinti işaretleri için izler. Herhangi bir algılanırsa, dağıtımı mevcut ve gelecek tüm gruplarda hemen duraklatırz.<br><br> Örneğin, Kalite güncelleştirmesini İlk grubuna dağıtırken bir sorun keşfederse, sorun azaltana kadar dağıtımları İlk, Hızlı ve Geniş gruplar olarak güncelleştirin. <br><br> Microsoft Yönetilen Masaüstü Yöneticisi portalında bilet dosyalamayla uyumluluk sorunlarını bildirebilirsiniz. <br><br> Özellik ve kalite güncelleştirmeleri bağımsız olarak duraklatılır. Duraklatma varsayılan olarak 35 gün boyunca etkilidir. Bununla birlikte, sorunun risk azaltmaya yönelik olup olmadığını bağlı olarak azaltılabilir veya uzatılabilir. |
| 3. Adım | Gruplar kullanılabilir değilken, dağıtım özgeçmişleri tablodaki zamanlamayı uygun olarak kullanır. |
| 4. Adım| Kullanıcılar, ayarlanmış bir süre için bildirimleri yeniden başlatmaya yanıt verme gücü verir. Bu dönem son tarih olarak bilinir ve güncelleştirmenin cihaza sunulan süreden itibaren ölçülür. <br><br> Bu süre boyunca cihaz yalnızca etkin saatler dışında otomatik olarak yeniden başlatılacaktır. Son tarihe ulaşıldıktan sonra, son tarihe ulaşıldı ve etkin saatler ne olursa olsun cihaz bir sonraki fırsatta yeniden başlatılacaktır. <br><br> Kalite güncelleştirmelerinin son tarihi üç gündür; özellik güncelleştirmeleri için beş gün sürer. |

> [!NOTE]
> Bu dağıtım işlemi hem özellik hem de kalite güncelleştirmeleri için geçerlidir, ancak zaman çizelgesi her biri için değişir.

## <a name="deployment-settings"></a>Dağıtım ayarları

Aşağıda listelenen dağıtım ayarlarını güncelleştirin:

| Güncelleştirme türü | Test | Birinci | Hızlı | Geniş |
| ------ | ------ | ------ | ------ | ------ |
| İşletim sistemi için kalite güncelleştirmeleri | Sıfır gün | Sıfır gün | Sıfır gün | Yedi gün |
| İşletim sistemi için özellik güncelleştirmeleri | Sıfır gün | 30 gün | 60 gün | 90 gün |
| Sürücüler/üretici yazılımı | Kalite güncelleştirmeleri zamanlaması izler. | Kalite güncelleştirmeleri zamanlaması izler. | Kalite güncelleştirmeleri zamanlaması izler. | Kalite güncelleştirmeleri zamanlaması izler. |
| Virüsten koruma tanımı | Her taramayla güncelleştirilir. | Her taramayla güncelleştirilir. | Her taramayla güncelleştirilir. | Her taramayla güncelleştirilir. |
| Microsoft 365 Uygulamaları için Enterprise | [Daha fazla bilgi edinin](../get-started/m365-apps.md#updates-to-microsoft-365-apps) | [Daha fazla bilgi edinin](../get-started/m365-apps.md#updates-to-microsoft-365-apps) | [Daha fazla bilgi edinin](../get-started/m365-apps.md#updates-to-microsoft-365-apps) | [Daha fazla bilgi edinin](../get-started/m365-apps.md#updates-to-microsoft-365-apps) |
| Microsoft Edge | [Daha fazla bilgi edinin](../get-started/edge-browser-app.md#updates-to-microsoft-edge) | [Daha fazla bilgi edinin](../get-started/edge-browser-app.md#updates-to-microsoft-edge) | [Daha fazla bilgi edinin](../get-started/edge-browser-app.md#updates-to-microsoft-edge) | [Daha fazla bilgi edinin](../get-started/edge-browser-app.md#updates-to-microsoft-edge) |
| Microsoft Teams | [Daha fazla bilgi edinin](../get-started/teams.md#updates) | [Daha fazla bilgi edinin](../get-started/teams.md#updates) | [Daha fazla bilgi edinin](../get-started/teams.md#updates) | [Daha fazla bilgi edinin](../get-started/teams.md#updates) |

>[!NOTE]
>Bu erteleme dönemleri, bilerek tüm kullanıcılar için yüksek güvenlik ve performans standartları sağlamak üzere tasarlanmıştır.<br><br> Microsoft Yönetilen Masaüstü cihazlarında toplanmış veriler ve güncelleştirmelerin değişen kapsamına ve etkilerine bağlı olarak, Microsoft Yönetilen Masaüstü geçici olarak tüm dağıtım grupları için ve tüm dağıtım gruplarında yukarıdaki erteleme sürelerinin uzunluğunu değiştirme esnekliği sunar.
>
>Microsoft Yönetilen Masaüstü, yönetilen kiracıları için zorunlu Windows kullanışlılığını değerlendirmek üzere her bir özellik sürümü için bağımsız bir değerlendirme yürüter. Sonuç olarak, Microsoft Yönetilen Masaüstü diğer tüm özellik güncelleştirmelerini dağıt Windows dağıtabilirsiniz.

## <a name="windows-insider-program"></a>Windows Insider Programı

Microsoft Yönetilen Masaüstü, desteklenen Insider programının bir parçası Windows desteklemez.

Aşağıdaki Windows Insider programı, yazılımla birlikte yayın öncesi sürüm Windows kullanılır. Görev açısından kritik olmayan cihazlara yöneliktir. Bu önemli bir Microsoft girişimi olduğu gibi, üretim ortamlarında geniş dağıtıma yönelik değildir.

Insider derlemeleri Windows cihazlar Test grubuna yer olabilir. Bu cihazlar, güncelleştirme hizmet düzeyi sözleşmelerinden ve Microsoft Yönetilen Masaüstü kullanıcı desteğinden muaftır.

## <a name="bandwidth-management"></a>Bant genişliği yönetimi

Tüm işletim [sistemi ve sürücü](/windows/deployment/update/waas-delivery-optimization) güncelleştirmeleri için Teslim İyileştirme'ye kullanıyoruz. Teslim İyileştirme, şirket ağı içindeki meslektaşlarından güncelleştirmeler Windows Güncelleştirme hizmetinin indirme boyutunu en aza indirir.
