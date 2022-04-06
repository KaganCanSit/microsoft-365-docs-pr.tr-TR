---
title: E-postada kullanıcıları Microsoft 365 Defender
description: Portalda bir olay için kullanıcıları Microsoft 365 Defender araştırabilirsiniz.
keywords: güvenlik, kötü amaçlı yazılım, Microsoft 365, M365, güvenlik merkezi, monitör, rapor, kimlikler, veriler, cihazlar, uygulamalar, olay, çözümleme, yanıt
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
search.appverid: met150
ms.custom: seo-marvel-jun2020
ms.technology: m365d
ms.openlocfilehash: 51bb4f451329a74417c21db0a64aadae6dccbce6
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500881"
---
# <a name="investigate-users-in-microsoft-365-defender"></a>E-postada kullanıcıları Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender

Olay incelemenizin bir parçası kullanıcı hesaplarını içerebilir. Microsoft 365 Defender portalında, Olaylar veya _Kullanıcılar uyarılarından bir olayla ilgili uyarılarda & **hesap** \> **_ayrıntılarını_*\>* bulabilirsiniz**. İşte bir örnek.

:::image type="content" source="../../media/investigate-incidents/incident-users.png" alt-text="Portalda yer alan bir olayın Kullanıcılar Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incident-users.png":::

Olayın kullanıcı hesabının hızlı bir özetini almak için, kullanıcı hesabı adının yanındaki onay işaretini seçin. İşte bir örnek.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-pane.png" alt-text="Microsoft 365 Defender portalında bir olayın Kullanıcılar sekmesi" lightbox="../../media/investigate-users/incidents-ss-user-pane.png":::

> [!NOTE]
> Kullanıcı sayfasında, Azure Active Directory (Azure AD) kuruluşlarının yanı sıra grupları da gösterir ve kullanıcıyla ilişkilendirilmiş grupları ve izinleri anlamanıza yardımcı olur.

Bu bölmede, mevcut olaylar, etkin uyarılar ve risk düzeyinin yanı sıra kullanıcıya maruz kalma, hesaplar, cihazlar ve çok daha fazlası dahil olmak üzere kullanıcı tehdit bilgilerini gözden geçirebilirsiniz.

Buna ek olarak, güvenliği tehlikeye atılmış bir Microsoft 365 Defender ele almaya yönelik, örneğin kullanıcı hesabının ihlal edilmiş olduğunu onaylama veya yeni bir oturum açma gerektirme gibi işlemleri doğrudan Microsoft 365 Defender portalında kabul edebilirsiniz.

Buradan, kullanıcı hesabının **ayrıntılarını görmek için Kullanıcı** sayfasına git'i seçin. İşte bir örnek.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-details.png" alt-text="Microsoft 365 Defender portalında kullanıcı hesabının ayrıntıları" lightbox="../../media/investigate-users/incidents-ss-user-details.png":::

Kullanıcılar sayfasındaki listeden kullanıcı hesabının adını seçerek de bu sayfayı **görebilirsiniz** .

Gruplar'ın altındaki numarayı seçerek kullanıcı için grup üyeliğini **görebilirsiniz**.

:::image type="content" source="../../media/investigate-users/user-group-membership.png" alt-text="Grup portalında yer alan bir kullanıcının grup Microsoft 365 Defender." lightbox="../../media/investigate-users/user-group-membership.png":::

Yönetici'nin altındaki **simgeyi** seçerek, kullanıcının kuruluş ağacının içinde nerede olduğunu görebilirsiniz.

Aşağıdaki Microsoft 365 Defender portalı kullanıcı sayfası Posta, Uç Nokta için Microsoft Defender, Kimlik için Microsoft Defender ve Microsoft Defender for Cloud Apps (sahip olduğunuz lisanslara bağlı olarak).

Bu sayfada, bir kullanıcı hesabının güvenlik riskiyle ilgili olarak belirli bilgiler görüntülenir ve bu bilgiler, riskin genel olarak riski değerlendirmesine yardımcı olan bir puan ile en son etkinliklere ve uyarılara yardımcı olur.

Bu sayfadan, şu ek eylemleri gerçekleştirebilirsiniz:

- Kullanıcı hesabını güvenliği ihlal edilmiş olarak işaretleme
- Kullanıcının yeniden oturum açmasını gerektir
- Kullanıcı hesabını askıya alma
- Azure AD kullanıcı hesabı ayarlarına bakın
- Kullanıcı hesabının sahip olduğu dosyaları görüntüleme
- Bu kullanıcıyla paylaşılan dosyaları görüntüleme.

İşte bir örnek.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-details-actions.png" alt-text="Portalda bir olay için bir kullanıcı hesabı üzerinde eylemleri açıklayan Microsoft 365 Defender." lightbox="../../media/investigate-users/incidents-ss-user-details-actions.png":::

## <a name="view-lateral-movement-paths"></a>Lateral movement paths

**Eşkenar** hareket yolları sekmesini seçerek, bu kullanıcıya gelen ve ağın pekiyi olması için değiştirilebilir eşkenar hareket yollarının görsel bir gösterimini sağlayan tamamen dinamik ve tıklanabilir bir harita görüntüleyebilirsiniz.

Harita size, bir saldırganın hassas bir hesabı tehlikeye atabilmesi için bu kullanıcıdan gelen ve bilgisayarlar arasındaki atlamaların listesini sağlar. Kullanıcının hassas bir hesabı varsa, kaç kaynak ve hesabın doğrudan bağlı olduğunu görebilirsiniz.

Son iki gün içinde varlık için olası bir hareket yolu algılanmadı ise grafik görüntülenmez. Bu varlık için bulunan eski hareket yolları grafiklerini görüntülemek için Farklı bir tarih görüntüle seçeneğini kullanarak farklı bir tarih seçin. Yan tümce hareket yolu raporu, bulunan olası  yan tümceler hakkında size bilgi sağlamak için her zaman kullanılabilir ve zamanla özelleştirilebilir.

:::image type="content" source="../../media/investigate-users/lateral-movement-path.png" alt-text="Microsoft 365 Defender portalında yer alan bir kullanıcı için Microsoft 365 Defender yolu" lightbox="../../media/investigate-users/lateral-movement-path.png":::

Daha fazla bilgi için bkz [. Yer hareket yolları](/defender-for-identity/use-case-lateral-movement-path).

## <a name="next-steps"></a>Sonraki adımlar

Süreç içinde yaşanan olaylarda olduğu gibi, incelemenize devam [edersiniz](investigate-incidents.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Olaylara genel bakış](incidents-overview.md)
- [Olaylara öncelik belirleyin](incident-queue.md)
- [Olayları yönetin](manage-incidents.md)
