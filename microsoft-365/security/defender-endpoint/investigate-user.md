---
title: E-postada kullanıcı hesabını Uç Nokta için Microsoft Defender
description: Güvenliği tehlikeye atılmış olası kimlik bilgileri için kullanıcı hesabını araştırabilirsiniz veya araştırma sırasında ilişkili kullanıcı hesabında özet atabilirsiniz.
keywords: araştır, hesap, kullanıcı, kullanıcı varlığı, uyarı, Uç Nokta için Microsoft Defender
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.date: 04/24/2018
ms.technology: mde
ms.openlocfilehash: 76b0b7405c8dc1c434fbc9f991903b25d8b9d4f4
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64469349"
---
# <a name="investigate-a-user-account-in-microsoft-defender-for-endpoint"></a>E-postada kullanıcı hesabını Uç Nokta için Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigatgeuser-abovefoldlink)

## <a name="investigate-user-account-entities"></a>Kullanıcı hesabı varlıklarını araştırma

En etkin uyarılarla kullanıcı hesaplarını tanımlayabilir (panoda "Risk altında kullanıcılar" olarak görüntülenir) ve güvenliği tehlikeye atılmış olası kimlik bilgileri olaylarını araştırabilir veya bir uyarıyı veya cihazı incelerken o kullanıcı hesabıyla cihazlar arasında olası uzlaşarak hareket olduğunu belirlemeye yönelik özetler yapabilirsiniz.

Kullanıcı hesabı bilgilerini aşağıdaki görünümlerde bulabilirsiniz:

- Pano
- Uyarı sırası
- Cihaz ayrıntıları sayfası

Bu görünümlerde tıklanabilir bir kullanıcı hesabı bağlantısı vardır ve bu bağlantı sizi kullanıcı hesabıyla ilgili diğer ayrıntıların gösterildiği kullanıcı hesabı ayrıntıları sayfasına götürebilirsiniz.

Bir kullanıcı hesabı varlığı incelenin, şunları bakın:

- Kullanıcı hesabı ayrıntıları, Kimlik için Microsoft Defender uyarıları ve oturum açmış cihazlar, rol, oturum açma türü ve diğer ayrıntılar
- Olaylara ve kullanıcının cihazlarına genel bakış
- Bu kullanıcıyla ilgili uyarılar
- Kuruluşta gözlemlenen (oturum açmış cihazlar)

:::image type="content" source="images/atp-user-details-view.png" alt-text="Kullanıcı hesabı varlık ayrıntıları sayfası" lightbox="images/atp-user-details-view.png":::

### <a name="user-details"></a>Kullanıcı ayrıntıları

Sol  tarafta yer alan Kullanıcı ayrıntıları bölmesi kullanıcı hakkında, ilgili açık olaylar, etkin uyarılar, SAM adı, SID, Kimlik için Microsoft Defender uyarıları, kullanıcının oturum açtığı cihaz sayısı, kullanıcının ilk ve son görülme sayısı, rol ve oturum açma türleri gibi bilgileri sağlar. Etkinleştirmiş olduğunuz tümleştirme özelliklerine bağlı olarak, diğer ayrıntıları da burada görüyorsunuz. Örneğin, İşletmeler için Skype tümleştirmeyi etkinleştirirsanız portaldan kullanıcıyla iletişim kurabilirsiniz. **Azure ATP uyarıları** bölümü, Kimlik için Microsoft Defender özelliğini etkinleştirdiyseniz ve kullanıcıyla ilgili uyarılar varsa sizi Kimlik için Microsoft Defender sayfasına götüren bir bağlantı içerir. Bu Kimlik için Microsoft Defender, uyarılar hakkında daha fazla bilgi sağlar.

> [!NOTE]
> Bu özelliği kullanmak için hem Uç Nokta için Kimlik için Microsoft Defender Defender'da tümleştirmeyi etkinleştirmeniz gerekir. Uç Nokta için Defender'da, gelişmiş özelliklerde bu özelliği etkinleştirebilirsiniz. Gelişmiş özellikleri etkinleştirme hakkında daha fazla bilgi için bkz [. Gelişmiş özellikleri açma](advanced-features.md).

Kuruluşta Genel Bakış, Uyarılar ve Gözlemlenen, kullanıcı hesabıyla ilgili çeşitli özniteliklerin görüntüleniyor farklı sekmelerdir.


>[!NOTE]
>Linux cihazlarında, oturum açmış kullanıcılarla ilgili bilgiler görüntülenmez.


### <a name="overview"></a>Genel bakış

Genel **Bakış** sekmesi olay ayrıntılarını ve kullanıcının oturum açtığı cihazların listesini gösterir. Her cihaza ilişkin oturum açma olaylarının ayrıntılarını görmek için bunları genişletebilirsiniz.

### <a name="alerts"></a>Uyarılar

Uyarılar **sekmesi** , kullanıcı hesabıyla ilişkili uyarıların listesini sağlar. Bu liste, Uyarı kuyruğuna ilişkin filtre uygulanmış [](alerts-queue.md)bir görünüm ve kullanıcı bağlamının seçilen kullanıcı hesabı olduğu uyarıları, son etkinliğin algılandığındaki tarihi, uyarıyla ilişkilendirilmiş cihazın kısa bir açıklamasını, uyarının önem derecesini, sırada uyarının durumunu ve uyarıya kimlerin atandığı gösterir.

### <a name="observed-in-organization"></a>Kuruluşta gözlemlenen

Kuruluşta gözlemlenen sekmesi, bir tarih aralığı belirterek bu kullanıcının oturum açtığı cihazların listesini, bu cihazların her biri için en sık ve en az oturum açan kullanıcı hesabını ve her cihazda toplam gözlemlenen kullanıcıları görmeyi sağlar.

Kuruluşta gözlemlenen tablosunda bir öğe seçerek öğeyi genişleterek cihaz hakkında daha fazla ayrıntıya neden olur. Bir öğe içindeki bağlantıyı doğrudan seçmek sizi ilgili sayfaya gönderir.

## <a name="search-for-specific-user-accounts"></a>Belirli kullanıcı hesaplarını arama

1. Arama **çubuğu** açılan **menüsünden Kullanıcı'ya** tıklayın.
2. Arama alanına kullanıcı **hesabını** girin.
3. Arama simgesine tıklayın veya Enter tuşuna **basın**.

Sorgu metniyle eşleşen kullanıcıların listesi görüntülenir. Kullanıcı hesabının etki alanını ve adını, kullanıcı hesabını en son ne zaman gördüğünüzi ve son 30 gün içinde oturum açtığı gözlemlenen cihazların toplam sayısını göreceğiz.

Sonuçları aşağıdaki dönemlere göre filtre yapabilirsiniz:

- 1 gün
- 3 gün
- 7 gün
- 30 gün
- 6 ay

## <a name="related-topics"></a>İlgili konular

- [Yeni Uyarı kuyruğu Uç Nokta için Microsoft Defender ve düzenleme](alerts-queue.md)
- [Uyarı Uç Nokta için Microsoft Defender yönetme](manage-alerts.md)
- [Uyarı Uç Nokta için Microsoft Defender araştırma](investigate-alerts.md)
- [Uç Nokta için Defender uyarısıyla ilişkilendirilmiş dosyayı araştırma](investigate-files.md)
- [Uç Nokta Cihazları için Defender listesinde cihazları araştırma](investigate-machines.md)
- [Uç Nokta için Defender uyarısıyla ilişkilendirilmiş IP adresini araştırma](investigate-ip.md)
- [Uç nokta için Defender uyarısıyla ilişkilendirilmiş etki alanını araştırma](investigate-domain.md)
