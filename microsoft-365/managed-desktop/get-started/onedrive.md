---
title: Microsoft OneDrive
description: Microsoft Yönetilen Masaüstü, kaydolan OneDrive için e-postayı nasıl ayarlar?
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler, uygulamalar, iş hattı uygulamaları, LOB uygulamaları
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 89d1851b3a2a7358a36d6a1ddd6f7db24dd2e1cf
ms.sourcegitcommit: 6c57f1e90339d5a95c9e7875599dac9d3e032c3a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2022
ms.locfileid: "63016437"
---
# <a name="microsoft-onedrive"></a>Microsoft OneDrive

Microsoft Yönetilen [Masaüstü OneDrive İş Microsoft](/onedrive/plan-onedrive-enterprise) Yönetilen Masaüstü cihazları için bulut depolama hizmeti olarak kullanır. Bu seçenek, cihazların mümkün olduğunca durumlarını en iyi şekilde uygulamalarını sağlar. Kullanıcılar hangi cihazda oturum yaptıklarına bakın, dosyalarını bulabilir. Örneğin, Microsoft Yönetilen Masaüstü cihazı yerine yeni bir cihaz kullanırsanız dosyalar otomatik olarak yeni cihazla eşitlenir.

Microsoft Yönetilen Cihazlarda bu ayarları varsayılan olarak otomatik olarak yapılandır ayarlarız:

| Özellik | Açıklama |
| ------ | ------ |
| Sessiz yapılandırma | OneDrive hesap, kullanıcı hesabıyla sessizce yapılandırılır. Kullanıcı etkileşimleri olmadan, hesaplarında oturum a açmada kullanılan kullanıcı hesabında otomatik olarak Windows. Daha fazla bilgi için [bkz. Kullanıcı hesaplarını sessiz yapılandırma - OneDrive](/onedrive/use-silent-account-configuration) |
| Files-on-Demand | Files-On-Demand özelliği kullanıcıların gereksiz yere disk alanı kullanmak zorunda kalmadan OneDrive'daki bulut depolamalarından dosyalara erişmelerini sağlar. Daha fazla bilgi için bkz[. OneDrive Files On-Demand ile disk alanı Windows 10](https://support.microsoft.com/office/save-disk-space-with-onedrive-files-on-demand-for-windows-10-0e6860d3-d9f3-4971-b321-7092438fb38e). |
| Bilinen Klasör Taşıma | Bilinen Klasör Taşıma özelliği, kullanıcıların dosyalarını herhangi bir cihazdan erişmelerini sağlar ve bu sayede verilerini bulutta sessizce destekler. Daha fazla bilgi için [bkz. Belgelerinizi, Resimlerinizi ve Masaüstü klasörlerinizi kendi OneDrive](https://support.microsoft.com/office/back-up-your-documents-pictures-and-desktop-folders-with-onedrive-d61a7930-a6fb-4b95-b28a-6552e77c3057). <p> Kullanıcılar, Microsoft Yönetilen Masaüstü cihazları arasında tutarlı bir deneyim elde etmek için Bilinen Klasör Taşıma özelliğini devre dışı bırakarak veya bilinen klasörlerin konumunu değiştiremezler.</p>|

## <a name="user-experience"></a>Kullanıcı deneyimi

Microsoft Yönetilen Masaüstü kullanıcıları yeni bir cihaz edinirken Azure kimlik bilgilerini girerek ve cihazı ayarerek ilk çalıştırma deneyimine girerler. Bu işlem tamamlandıktan sonra masaüstüne erişebilirsiniz ve OneDrive edinebilirsiniz.

1. Sistem, kullanıcılara OneDrive yapılandırıldıklarını ve oturumlarının otomatik olarak yenisinde olduğunu OneDrive.

:::image type="content" source="media/onedrive-sync.png" alt-text="Artık eşitlemeye devam ediyor ve OneDrive başka bir OneDrive düzenleyebilirsiniz. Dosyalarınızı görüntülemek için buraya tıklayın.":::

2. Sistem, kullanıcılara bilinen OneDrive taşımanın onlar için yapılandırıldığından emin olduğunu söyler.

:::image type="content" source="media/onedrive-folders.png" alt-text="ÖNEMLI klasörlerinizin bilgi bölümü tarafından silindi bildirimi. Klasörler artık en çok OneDrive ve diğer cihazlarda kullanılabilir.":::

3. Cihazlar sıfırlanır veya yeniden yüklenirken masaüstünde yinelenen simgeleri önlemek için sistem masaüstünden Microsoft Edge ve Microsoft Teams simgelerini otomatik olarak OneDrive eşitleme. Bu bilgiler Dosya Gezgini'nde gösterilir.

:::image type="content" source="media/onedrive-teams.png" alt-text="Temizlenen onay Teams ve vurgu metni okumanın Eşit dışında tutularak vurgu metinlerini gösteren Dosya Gezgini.":::

## <a name="onedrive-sync-restrictions"></a>OneDrive eşitleme kısıtlamaları

Bu erişimi kısıtlamak OneDrive eşitleme, Azure Active Directory koşullu erişim ilkesiyle denetlemenizi öneririz. Daha fazla bilgi için bkz[. OneDrive eşitleme uygulamasında koşullu erişim desteğini etkinleştirme](/onedrive/enable-conditional-access).

Kuruluşta Azure AD koşullu erişim ilkesi kullanasanız bile, IT Yöneticiniz şu adımları izlemesi gerekir:

1. Henüz bilmiyorsanız, Kiracı kimliğinizi bulma konusunda açıklandığı gibi kiracı [Microsoft 365 bakın](/onedrive/find-your-office-365-tenant-id).
1. OneDrive yönetim merkezinde oturum açma.
1. Sol bölmede Eşitle'yi **seçin**.
1. Yalnızca belirli **etki alanlarına katılmış bilgisayarlarda eşitlemeye** izin ver onay kutusunu seçin ve kiracı kimliğini etki alanları listesine ekleyin. Daha fazla bilgi için bkz. [Yalnızca belirli etki alanlarına katılmış bilgisayarlarda eşitlemeye izin verme](/onedrive/allow-syncing-only-on-specific-domains).

> [!NOTE]
> Bu kılavuz yalnızca Microsoft Yönetilen Masaüstü'nden kiracılara yöneliktir. Kullanımda bu makalede ele alın kullanmayan başka ayarlar da vardır.
