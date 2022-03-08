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
ms.openlocfilehash: d49ef6b31e6446f3452d0efdce2e918813eabcc6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327553"
---
# <a name="investigate-users-in-microsoft-365-defender"></a>E-postada kullanıcıları Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender

Olay incelemenizin bir parçası kullanıcı hesaplarını içerebilir. Microsoft 365 Defender portalında, Olaylar veya _Kullanıcılar uyarılarından bir olayla ilgili uyarılarda & **hesap** \> **_ayrıntılarını_*\>* bulabilirsiniz**. İşte bir örnek.

:::image type="content" source="../../media/investigate-incidents/incident-users.png" alt-text="Olay için Kullanıcılar sayfası örneği." lightbox="../../media/investigate-incidents/incident-users.png":::

Olayın kullanıcı hesabının hızlı bir özetini almak için, kullanıcı hesabı adının yanındaki onay işaretini seçin. İşte bir örnek.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-pane.png" alt-text="Olay için kullanıcı hesabı özet bölmesi örneği." lightbox="../../media/investigate-users/incidents-ss-user-pane.png":::

> [!NOTE]
> Kullanıcı sayfasında, Azure Active Directory (Azure AD) kuruluşlarının yanı sıra grupları da gösterir ve kullanıcıyla ilişkilendirilmiş grupları ve izinleri anlamanıza yardımcı olur.

Bu bölmede, mevcut olaylar, etkin uyarılar ve risk düzeyinin yanı sıra kullanıcıya maruz kalma, hesaplar, cihazlar ve çok daha fazlası dahil olmak üzere kullanıcı tehdit bilgilerini gözden geçirebilirsiniz.

Buna ek olarak, güvenliği tehlikeye atılmış bir Microsoft 365 Defender ele almaya yönelik, örneğin kullanıcı hesabının ihlal edilmiş olduğunu onaylama veya yeni bir oturum açma gerektirme gibi işlemleri doğrudan Microsoft 365 Defender portalında kabul edebilirsiniz.

Buradan, kullanıcı hesabının **ayrıntılarını görmek için Kullanıcı** sayfasına git'i seçin. İşte bir örnek.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-details.png" alt-text="Olay için kullanıcı hesabı sayfası örneği." lightbox="../../media/investigate-users/incidents-ss-user-details.png":::

Kullanıcılar sayfasındaki listeden kullanıcı hesabının adını seçerek de bu sayfayı **görebilirsiniz** .

Gruplar'ın altındaki numarayı seçerek kullanıcı için grup üyeliğini **görebilirsiniz**.

:::image type="content" source="../../media/investigate-users/user-group-membership.png" alt-text="Bir kullanıcı için grup üyeliği örneği." lightbox="../../media/investigate-users/user-group-membership.png":::

Yönetici'nin altındaki **simgeyi** seçerek, kullanıcının kuruluş ağacının içinde nerede olduğunu görebilirsiniz.

Microsoft 365 Defender portalı kullanıcı sayfası Uç Nokta için Microsoft Defender, Kimlik için Microsoft Defender ve Bulut Uygulamaları için Microsoft Defender'dan (sahip olduğunuz lisanslara bağlı olarak) alınan bilgileri birleştirir.

Bu sayfada, bir kullanıcı hesabının güvenlik riskiyle ilgili olarak belirli bilgiler görüntülenir ve bu bilgiler, riskin genel olarak riski değerlendirmesine yardımcı olan bir puan ile en son etkinliklere ve uyarılara yardımcı olur.

Bu sayfadan, şu ek eylemleri gerçekleştirebilirsiniz:

- Kullanıcı hesabını güvenliği ihlal edilmiş olarak işaretleme
- Kullanıcının yeniden oturum açmasını gerektir
- Kullanıcı hesabını askıya alma
- Azure AD kullanıcı hesabı ayarlarına bakın
- Kullanıcı hesabının sahip olduğu dosyaları görüntüleme
- Bu kullanıcıyla paylaşılan dosyaları görüntüleme.

İşte bir örnek.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-details-actions.png" alt-text="Bir olay için kullanıcı hesabı üzerinde eylemler örneği." lightbox="../../media/investigate-users/incidents-ss-user-details-actions.png":::

## <a name="view-lateral-movement-paths"></a>Lateral movement paths

**Eşkenar** hareket yolları sekmesini seçerek, bu kullanıcıya gelen ve ağın pekiyi olması için değiştirilebilir eşkenar hareket yollarının görsel bir gösterimini sağlayan tamamen dinamik ve tıklanabilir bir harita görüntüleyebilirsiniz.

Harita size, bir saldırganın hassas bir hesabı tehlikeye atabilmesi için bu kullanıcıdan gelen ve bilgisayarlar arasındaki atlamaların listesini sağlar. Kullanıcının hassas bir hesabı varsa, kaç kaynak ve hesabın doğrudan bağlı olduğunu görebilirsiniz.

Son iki gün içinde varlık için olası bir hareket yolu algılanmadı ise grafik görüntülenmez. Bu varlık için bulunan eski hareket yolları grafiklerini görüntülemek için Farklı bir tarih görüntüle seçeneğini kullanarak farklı bir tarih seçin. Yan tümce hareket yolu raporu, bulunan olası  yan tümceler hakkında size bilgi sağlamak için her zaman kullanılabilir ve zamanla özelleştirilebilir.

:::image type="content" source="../../media/investigate-users/lateral-movement-path.png" alt-text="Bir kullanıcı için yan tümkenar hareket yolu örneği." lightbox="../../media/investigate-users/lateral-movement-path.png":::

Daha fazla bilgi için bkz [. Yer hareket yolları](/defender-for-identity/use-case-lateral-movement-path).

## <a name="next-steps"></a>Sonraki adımlar

Süreç içinde yaşanan olaylarda olduğu gibi, incelemenize devam [edersiniz](investigate-incidents.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Olaylara genel bakış](incidents-overview.md)
- [Olayları önceliklendirme](incident-queue.md)
- [Olayları yönetme](manage-incidents.md)
