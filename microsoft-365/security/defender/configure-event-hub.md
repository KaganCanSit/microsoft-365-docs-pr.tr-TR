---
title: Etkinlik Hub'ını yapılandırma
description: Etkinlik Hub'ını yapılandırmayı öğrenin
keywords: olay merkezi, yapılandırma, öngörüler
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
MS.technology: mde
ms.openlocfilehash: a842f9161aa823203354917326653b583e5fddb9
ms.sourcegitcommit: d32654bdfaf08de45715dd362a7d42199bdc1ee7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2022
ms.locfileid: "63754293"
---
# <a name="configure-your-event-hub"></a>Etkinlik Hub'ını yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Etkinlik Hub'ını, etkinlik etkinliklerini en iyi şekilde Microsoft 365 Defender.

## <a name="set-up-the-required-resource-provider-in-the-event-hub-subscription"></a>Olay Merkezi aboneliğinde gerekli Kaynak Sağlayıcısını ayarlama

1. [Azure portalda](https://portal.azure.com) oturum açın.
1. **Abonelikler** > **{'i seçin Olay hub'ların }** > Kaynak sağlayıcılarına dağıtılacağı **aboneliği seçin**.
1. **Microsoft.Analizler** Sağlayıcı kayıtlı. Aksi takdirde, kaydettirin.

:::image type="content" source="../../media/f893db7a7b1f7aa520e8b9257cc72562.png" alt-text="Microsoft Azure portalında hizmet Microsoft Azure listesi" lightbox="../../media/f893db7a7b1f7aa520e8b9257cc72562.png":::

## <a name="set-up-azure-active-directory-app-registration"></a>Uygulama Azure Active Directory ayarlama

> ! [NOT] Yönetici olmayanların uygulamaları kaydetmesine izin vermek Azure Active Directory (AAD) veya Yönetici rolüne (AAD) sahip olmak gerekir. Hizmet sorumlusuna rol atamak için ayrıca Sahip veya Kullanıcı Erişimi Yöneticisi rolünüz de olması gerekir. Daha fazla bilgi için portalda [hizmet sorumlusu olarak Azure AD & oluşturma - Microsoft Docs Microsoft kimlik platformu \| a bakın](/azure/active-directory/develop/howto-create-service-principal-portal).

1. Uygulama kayıtlarında yeni kayıt (yapısal olarak hizmet sorumlusu oluşturur) **Azure Active Directory** \> **Yeni kayıt** \> **.**

1. Formu yalnızca Ad ile doldurun (Yeniden Yönlendirme URI'si gerekmez).

    :::image type="content" source="../../media/336bc84e6be23900c43232b4ef0c253c.png" alt-text="Microsoft Azure portalında uygulama adı görüntüleme bölümü" lightbox="../../media/336bc84e6be23900c43232b4ef0c253c.png":::


    :::image type="content" source="../../media/06ac04c4ff713c2065cec2ef2f99a294.png" alt-text="Web portalında Genel bakış Microsoft Azure bölümü" lightbox="../../media/06ac04c4ff713c2065cec2ef2f99a294.png":::

1. Sertifikalar ve **gizliler'e & gizli yeni istemci** \> **sırrı:**

    :::image type="content" source="../../media/d2ef88d3d2310d2c60c294b569cdf02e.png" alt-text="Müşteri portalının müşteri Microsoft Azure bölümü" lightbox="../../media/d2ef88d3d2310d2c60c294b569cdf02e.png":::
    

> [!WARNING]
> **İstemci sırrına yeniden erişesiniz, bu nedenle dosyayı kaydetmeyi deneyin**.

## <a name="set-up-event-hub-namespace"></a>Olay Merkezi ad alanını ayarlama

1. Olay Merkezi Ad Alanı oluşturma:

    Etkinlik **Merkezi Ekleme'ye \> gidin** ve istediğiniz yüke uygun fiyatlandırma katmanını, aktarım hızı birimlerini ve Otomatik Inflate'yi seçin (standart fiyatlandırma ve özellikler gerektirir). Daha fazla bilgi için bkz[. Fiyatlandırma - Etkinlik Merkezi \| Microsoft Azure](https://azure.microsoft.com/pricing/details/event-hubs/)

    > [!NOTE]
    > Mevcut bir olay hub'ını kullanabilirsiniz, ancak aktarım hızı ve ölçeklendirme ad alanı düzeyinde ayarlanır; dolayısıyla bir olay hub'ını kendi ad alanına depolamanız önerilir.

   :::image type="content" source="../../media/ebc4ca37c342ad1da75c4aee4018e51a.png" alt-text="Etkinlik hub'ları bölümü Microsoft Azure tıklayın" lightbox="../../media/ebc4ca37c342ad1da75c4aee4018e51a.png":::

1. Ayrıca, bu Olay Merkezi Ad Alanı'nın Kaynak Kimliği'ne de ihtiyacınız olacaktır. Azure Olay Merkezi ad alanı sayfanız Özellikler'e \> gidin. Kaynak Kimliği'nin altındaki metni kopyalayın ve aşağıdaki Kaynak Yapılandırması Microsoft 365 boyunca kullanmak üzere kaydını uygulayın.

    :::image type="content" source="../../media/759498162a4e93cbf17c4130d704d164.png" alt-text="Etkinlik portalının etkinlik hub'ları Microsoft Azure." lightbox="../../media/759498162a4e93cbf17c4130d704d164.png":::


1. Olay Merkezi Ad Alanı oluşturulduktan sonra, Uygulama Kayıt Hizmeti Sorumlu'sını Okuyucu, Azure Olay Merkezi Veri Alıcısı olarak ve Microsoft 365 Defender'da Katılımcı olarak oturum açacak olan kullanıcıyı eklemeniz gerekir (bu işlemi Kaynak Grubu veya Abonelik düzeyinde de kullanabilirsiniz).

    Bu adımı Olay Merkezi Ad Alanı Erişim **Denetimi** \> **(IAM)** \> Rol atamaları altında ekleyin **ve doğrulayın**:

    :::image type="content" source="../../media/9c9c29137b90d5858920202d87680d16.png" alt-text="Microsoft Azure portalında bir uygulama kayıt Microsoft Azure bölümü" lightbox="../../media/9c9c29137b90d5858920202d87680d16.png":::

## <a name="set-up-event-hub"></a>Etkinlik Hub'ı ayarlama

**1. Seçenek:**

Ad Alanı'nız içinde bir Olay Merkezi oluşturabilirsiniz  ve dışarı aktarmayı seçerek tüm Olay Türleri (Tablolar) bu Olay **Merkezi'ne** yazılır.

**2. Seçenek:**

Tüm Olay Türlerini (Tablolar) tek bir Olay Merkezi'ne dışarı aktar yerine, her tabloyu Olay Merkezi Ad Alanı'nın içinde farklı Olay Hub'larına aktarabilirsiniz (Olay Türü başına bir Olay Hub'ı).

Bu seçenekte, Microsoft 365 Defender Hub'ı sizin için oluşturacak.

> [!NOTE]
> Olay Merkezi Kümesi'nin parçası değil de bir Etkinlik  Merkezi Ad Alanı kullanıyorsanız, Azure'da Olay Merkezi Ad Alanı başına 10 Olay Merkezi sınırlaması nedeniyle tanımladığınız her Dışarı Aktarma olayına en çok 10 Olay Türü (Tablo Ayarlar) aktarabilirsiniz.

Örneğin:

:::image type="content" source="../../media/005c1f6c10c34420d387f594987f9ffe.png" alt-text="Etkinlik portalının etkinlik Microsoft Azure." lightbox="../../media/005c1f6c10c34420d387f594987f9ffe.png":::

Bu seçeneği seçerseniz, E-posta tablolarını göndermek [için Microsoft 365 Defender yapılandırma bölümüne geçebilirsiniz](#configure-microsoft-365-defender-to-send-email-tables).

Etkinlik Merkezi + Olay Merkezi'ne seçerek Ad **Alanı'nız içinde** \> **Olay Merkezi oluşturun**.

Bölüm Sayısı paralellik yoluyla daha fazla performansa olanak sağlar, bu nedenle beklemediğiniz yüke bağlı olarak bu say ın artması önerilir. Varsayılan İleti Bekletme ve Yakalama 1 ve Kapalı değerleri önerilir.

:::image type="content" source="../../media/1db04b8ec02a6298d7cc70419ac6e6a9.png" alt-text="Yeni portalda etkinlik hub'ları Microsoft Azure bölümü" lightbox="../../media/1db04b8ec02a6298d7cc70419ac6e6a9.png":::
 

Bu Olay Merkezi için (ad alanı olarak değil) Gönderme, Talepleri Dinleme ile paylaşılan bir Erişim İlkesi yapılandırmanız gerekir. Etkinlik Merkezi Paylaşılan **erişim** \> ilkeleri **+** **Ekle'ye** \> tıklayın ve İlke adı (başka yerde kullanılmadı) verin ve Gönder **ve Dinle'yi** **seçin**.

:::image type="content" source="../../media/1867d13f46dc6a0f4cdae6cf00df24db.png" alt-text="Microsoft Azure portalında paylaşılan erişim ilkeleri sayfası" lightbox="../../media/1867d13f46dc6a0f4cdae6cf00df24db.png":::

## <a name="configure-microsoft-365-defender-to-send-email-tables"></a>E Microsoft 365 Defender ta tablo gönderecek şekilde yapılandırma

### <a name="set-up-microsoft-365-defender-send-email-tables-to-splunk-via-event-hub"></a>Etkinlik Merkezi Microsoft 365 Defender E-posta tablolarını Splunk'a gönderme hakkında bilgi ayarlama

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender'da</a>, tüm aşağıdaki rol gereksinimlerini karşılayacak bir hesap kullanarak oturum açın:

    - Dışarı aktaracağız Olay Merkezi için Olay Merkezi *Ad* Alanı Kaynağı düzeyinde veya daha yüksek bir düzeyde katılımcı rolü. Bu izin olmadan, ayarları kaydetmeyi deneyebilirsiniz.

    - Microsoft 365 Defender Azure'a bağlı kiracıda Genel Yönetici veya Güvenlik Microsoft 365 Defender rolü.

      :::image type="content" source="../../media/55d5b1c21dd58692fb12a6c1c35bd4fa.png" alt-text="Web Ayarlar portalının Microsoft 365 Defender sayfası" lightbox="../../media/55d5b1c21dd58692fb12a6c1c35bd4fa.png":::

1. Ham Veri **Dışarı Aktar +Ekle'ye \> tıklayın**.

    Şimdi yukarıda kayıtlı verileri kullanıcaz.

    **Ad**: Bu değer yereldir ve ortamınıza en iyi şekilde çalışıyor olması gerekir.

    **Olayları etkinlik hub'kutusuna iletme**: Bu onay kutusunu seçin.

    **Olay Merkezi Kaynak Kimliği**: Bu değer, Olay Hub'ını ayarlarken kaydettiğiniz Olay Merkezi Ad Alanı Kaynak Kimliğidir.

    **Olay Merkezi adı**: Olay Merkezi Ad Alanı içinde bir Olay Merkezi oluşturduysanız, yukarıya kayıtlı Olay Merkezi adını yapıştırın.

    Olay Türleri (Tablolar) başına Microsoft 365 Defender Hub'ı oluşturmanızı tercih ediyorsanız, bu alanı boş bırakın.

    **Etkinlik Türleri**: Etkinlik Merkezi'ne iletip özel uygulamanıza iletebilirsiniz Gelişmiş Av tablolarını seçin. Uyarı tabloları Diğer Microsoft 365 Defender, Cihazlar tabloları Uç Nokta için Microsoft Defender (EDR) ve E-posta tabloları Office 365. E-posta Olayları tüm E-posta İşlemlerini kayıtları. AYRıCA URL (Kasa Bağlantıları), Ek (Kasa Ekleri) ve Teslim Olayları Gönder (ZAP) de kaydedilir ve NetworkMessageId alanında E-posta Olayları'ne bir araya gönderilebilir.

    :::image type="content" source="../../media/3b2ad64b6ef0f88cf0175f8d57ef8b97.png" alt-text="Portalda Akış API'si Microsoft Azure sayfası" lightbox="../../media/3b2ad64b6ef0f88cf0175f8d57ef8b97.png":::

1. Gönder'e tıklamayı **seçin**.

### <a name="verify-that-the-events-are-being-exported-to-the-event-hub"></a>Etkinliklerin Olay Merkezi'ne aktarıldıklarını doğrulama

Temel Gelişmiş Av sorgusu çalıştırarak etkinliklerin Etkinlik Merkezi'ne gönderildiğini doğruabilirsiniz. Gelişmiş **Av** \> **Sorgusunu** **Avla'yi** \> seçin ve aşağıdaki sorguyu girin:

```console
EmailEvents
|joinkind=fullouterEmailAttachmentInfoonNetworkMessageId
|joinkind=fullouterEmailUrlInfoonNetworkMessageId
|joinkind=fullouterEmailPostDeliveryEventsonNetworkMessageId
|whereTimestamp\>ago(1h)
|count
```

Bu size, tüm diğer tablolarda bir araya gelen son saatte kaç e-posta alınmıştır? gösterir. Ayrıca, olay hub'lara aktarilebilecek olaylar görüyorsanız da bunu size gösterir. Bu sayı 0 sayısını gösteriyorsa, Etkinlik Merkezi'ne gidip gelen hiçbir veri görmeyebilirsiniz.

:::image type="content" source="../../media/c305e57dc6f72fa9eb035943f244738e.png" alt-text="Portalda gelişmiş Microsoft Azure sayfası" lightbox="../../media/c305e57dc6f72fa9eb035943f244738e.png":::

Dışarı aktarlanacak veri olduğunu doğruladıktan sonra, Olay Merkezi sayfasını görüntüleyebilirsiniz ve iletilerin gelen olduğunu doğrularsınız. Bu bir saat kadar zaman alabiliyor.

1. Azure'da, Olay **Merkezi'ne gidin**\>, Ad Alanı **Olay Merkezi'ne** \> **tıklayın** \> Olay **Merkezi'ne tıklayın**.
1. Genel **Bakış'ın** altında aşağı kaydırın ve İletiler grafiğinde Gelen İletiler'i görebilirsiniz. Hiçbir sonuç görmüyorsanız, özel uygulamanız için istediğiniz ileti olmayacaktır.

:::image type="content" source="../../media/e88060e315d76e74269a3fc866df047f.png" alt-text="Azure portalında Genel Microsoft 365 sayfası" lightbox="../../media/e88060e315d76e74269a3fc866df047f.png":::
