---
title: Olay Hub'ınızı yapılandırma
description: Olay Hub'ınızı yapılandırmayı öğrenin
keywords: olay hub'ı, yapılandırma, içgörüler
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
ms.openlocfilehash: 40211d37b8b036f93b826a383d9d0aa87f44fc68
ms.sourcegitcommit: 292de1a7e5ecc2e9e6187126aebba6d3b9416dff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2022
ms.locfileid: "65243084"
---
# <a name="configure-your-event-hub"></a>Olay Hub'ınızı yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Olay Hub'ınızı, olayları Microsoft 365 Defender alabilmesi için yapılandırmayı öğrenin.

## <a name="set-up-the-required-resource-provider-in-the-event-hub-subscription"></a>Event Hub aboneliğinde gerekli Kaynak Sağlayıcısını ayarlama

1. [Azure portalda](https://portal.azure.com) oturum açın.
1. **Abonelikler** > **{Olay hub'larının }** > **Kaynak sağlayıcılarına** dağıtılacağı aboneliği seçin.
1. **Microsoft.Analizler** Sağlayıcı kaydedildi. Aksi takdirde kaydedin.

:::image type="content" source="../../media/f893db7a7b1f7aa520e8b9257cc72562.png" alt-text="Microsoft Azure portalındaki hizmet sağlayıcıları listesi sayfası" lightbox="../../media/f893db7a7b1f7aa520e8b9257cc72562.png":::

## <a name="set-up-azure-active-directory-app-registration"></a>Azure Active Directory Uygulama Kaydını Ayarlama

> ! [NOT] Yönetici rolüne sahip olmanız veya yönetici olmayanların uygulamaları kaydetmesine izin vermek için Azure Active Directory (AAD) ayarlanmalıdır. Hizmet sorumlusuna bir rol atamak için Sahip veya Kullanıcı Erişimi Yöneticisi rolüne de sahip olmanız gerekir. Daha fazla bilgi için bkz. [Portalda hizmet sorumlusu & Azure AD uygulaması oluşturma - Microsoft Docs Microsoft kimlik platformu\|](/azure/active-directory/develop/howto-create-service-principal-portal).

1. **Azure Active Directory Uygulama kayıtları Yeni kayıt'ta**  \>  \> yeni bir kayıt oluşturun (doğal olarak bir hizmet sorumlusu oluşturur).

1. Formu yalnızca Ad ile doldurun (Yeniden Yönlendirme URI'sine gerek yoktur).

    :::image type="content" source="../../media/336bc84e6be23900c43232b4ef0c253c.png" alt-text="Microsoft Azure portalındaki uygulama adı görüntüleme bölümü" lightbox="../../media/336bc84e6be23900c43232b4ef0c253c.png":::


    :::image type="content" source="../../media/06ac04c4ff713c2065cec2ef2f99a294.png" alt-text="Microsoft Azure portalındaki Genel Bakış bilgileri bölümü" lightbox="../../media/06ac04c4ff713c2065cec2ef2f99a294.png":::

1. **Sertifikalar & gizli diziler** **Yeni istemci gizli** dizisi'ne tıklayarak gizli dizi \> oluşturun:

    :::image type="content" source="../../media/d2ef88d3d2310d2c60c294b569cdf02e.png" alt-text="Microsoft Azure portalındaki İstemci gizli dizisi bölümü" lightbox="../../media/d2ef88d3d2310d2c60c294b569cdf02e.png":::
    

> [!WARNING]
> **İstemci gizli dizisine yeniden erişemeyeceksiniz, bu nedenle gizli diziyi kaydettiğinizden emin olun**.

## <a name="set-up-event-hub-namespace"></a>Olay Hub'ı ad alanını ayarlama

1. Olay Hub'ı Ad Alanı Oluşturma:

    **Olay Hub'ı \> Ekle'ye** gidin ve beklediğiniz yüke uygun fiyatlandırma katmanını, aktarım hızı birimlerini ve Otomatik Şişirme'yi (standart fiyatlandırma ve özellikler altında gerektirir) seçin. Daha fazla bilgi için bkz[. Fiyatlandırma - Olay Hub'ı \| Microsoft Azure](https://azure.microsoft.com/pricing/details/event-hubs/)

    > [!NOTE]
    > Mevcut bir olay hub'ını kullanabilirsiniz, ancak aktarım hızı ve ölçeklendirme ad alanı düzeyinde ayarlanır, bu nedenle bir olay hub'ını kendi ad alanına yerleştirmeniz önerilir.

   :::image type="content" source="../../media/ebc4ca37c342ad1da75c4aee4018e51a.png" alt-text="Microsoft Azure portalındaki event hubs bölümü" lightbox="../../media/ebc4ca37c342ad1da75c4aee4018e51a.png":::

1. Ayrıca bu Olay Hub'ı Ad Alanının Kaynak Kimliğine de ihtiyacınız olacaktır. Azure Olay Hub'ı ad alanı sayfanızın Özellikler bölümüne \> gidin. Kaynak Kimliği altındaki metni kopyalayın ve aşağıdaki Microsoft 365 Yapılandırması bölümünde kullanmak üzere kaydedin.

    :::image type="content" source="../../media/759498162a4e93cbf17c4130d704d164.png" alt-text="Microsoft Azure portalındaki event hubs özellikleri bölümü" lightbox="../../media/759498162a4e93cbf17c4130d704d164.png":::


1. Olay Hub'ı Ad Alanı oluşturulduktan sonra Uygulama Kayıt Hizmeti Sorumlusunu Okuyucu, Azure Event Hubs Veri Alıcısı ve katkıda bulunan olarak Microsoft 365 Defender oturum açacak kullanıcıyı eklemeniz gerekir (bunu Kaynak Grubu veya Abonelik düzeyinde de yapabilirsiniz).

    Bu adımı **Olay Hub'ı Ad Alanı** \> **Access Control (IAM)** \> **Rol atamaları** altında **Ekleme** ve doğrulama bölümünde yaparsınız:

    :::image type="content" source="../../media/9c9c29137b90d5858920202d87680d16.png" alt-text="Microsoft Azure portalında uygulama kaydı hizmet sorumlusu bölümü" lightbox="../../media/9c9c29137b90d5858920202d87680d16.png":::

## <a name="set-up-event-hub"></a>Olay Hub'ı ayarlama

**Seçenek 1:**

Ad Alanınızda bir Olay Hub'ı oluşturabilirsiniz ve dışarı aktarmak için seçtiğiniz **tüm** Olay Türleri (Tablolar **) bu olay** hub'ına yazılır.

**Seçenek 2:**

Tüm Olay Türlerini (Tabloları) tek bir Olay Hub'ına aktarmak yerine, her tabloyu Olay Hub'ı Ad Alanınızın içindeki farklı Olay Hub'ına (Olay Türü başına bir Olay Hub'ı) dışarı aktarabilirsiniz.

Bu seçenekte Microsoft 365 Defender sizin için Olay Hub'ı oluşturur.

> [!NOTE]
> Olay Hub'ı Kümesinin parçası **olmayan** bir Olay Hub'ı Ad Alanı kullanıyorsanız, Olay Hub'ı Ad Alanı başına 10 Olay Hub'ı sınırlaması nedeniyle tanımladığınız her Dışarı Aktarma Ayarlar dışarı aktarmak için en fazla 10 Olay Türü (Tablo) seçebilirsiniz.

Örneğin:

:::image type="content" source="../../media/005c1f6c10c34420d387f594987f9ffe.png" alt-text="Microsoft Azure portalında olay hub'ları bölümü" lightbox="../../media/005c1f6c10c34420d387f594987f9ffe.png":::

Bu seçeneği belirlerseniz, [E-posta tablolarını göndermek için Microsoft 365 Defender yapılandırma](#configure-microsoft-365-defender-to-send-email-tables) bölümüne atlayabilirsiniz.

Olay Hub'ı + Olay Hub'ı seçerek Ad Alanınızda **Olay** \> **Hub'ı** oluşturun.

Bölüm Sayısı paralellik aracılığıyla daha fazla aktarım hızı sağlar, bu nedenle beklediğiniz yüke göre bu sayıyı artırmanız önerilir. Varsayılan İleti Saklama ve Yakalama değerleri 1 ve Kapalı önerilir.

:::image type="content" source="../../media/1db04b8ec02a6298d7cc70419ac6e6a9.png" alt-text="Microsoft Azure portalında olay hub'ları oluşturma bölümü" lightbox="../../media/1db04b8ec02a6298d7cc70419ac6e6a9.png":::
 

Bu Olay Hub'ı (ad alanı değil) için Gönder, Talepleri Dinle ile Paylaşılan Erişim İlkesi yapılandırmanız gerekir. **Olay Hub'ı** \> **Paylaşılan erişim ilkeleri** \> **+ Ekle'ye** tıklayın ve bir İlke adı verin (başka bir yerde kullanılmaz) ve Gönder ve **Dinle'yi** işaretleyin.

:::image type="content" source="../../media/1867d13f46dc6a0f4cdae6cf00df24db.png" alt-text="Microsoft Azure portalındaki Paylaşılan erişim ilkeleri sayfası" lightbox="../../media/1867d13f46dc6a0f4cdae6cf00df24db.png":::

## <a name="configure-microsoft-365-defender-to-send-email-tables"></a>E-posta tablolarını göndermek için Microsoft 365 Defender yapılandırma

### <a name="set-up-microsoft-365-defender-send-email-tables-to-splunk-via-event-hub"></a>Event Hub aracılığıyla Splunk'a E-posta tabloları göndermek Microsoft 365 Defender ayarlama

1. Aşağıdaki tüm rol gereksinimlerini karşılayan bir hesapla <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> oturum açın:

    - Dışarı aktaracağınız Olay Hub'ı için Olay *Hub'ı Ad Alanı* Kaynak düzeyinde veya daha üst düzeyde katkıda bulunan rolü. Bu izin olmadan, ayarları kaydetmeye çalıştığınızda dışarı aktarma hatası alırsınız.

    - Microsoft 365 Defender ve Azure'a bağlı kiracıda Genel Yönetici veya Güvenlik Yöneticisi Rolü.

      :::image type="content" source="../../media/55d5b1c21dd58692fb12a6c1c35bd4fa.png" alt-text="Microsoft 365 Defender portalının Ayarlar sayfası" lightbox="../../media/55d5b1c21dd58692fb12a6c1c35bd4fa.png":::

1. **Ham Veri Dışarı Aktarma \> +Ekle'ye** tıklayın.

    Şimdi yukarıda kaydettiğiniz verileri kullanacaksınız.

    **Ad**: Bu değer yereldir ve ortamınızda çalışan her şey olmalıdır.

    **Olayları olay hub'ına iletme**: Bu onay kutusunu seçin.

    **Event-Hub Kaynak Kimliği**: Bu değer, Olay Hub'ını ayarlarken kaydettiğiniz Olay Hub'ı Ad Alanı Kaynak Kimliğidir.

    **Event-Hub adı**: Olay Hub'ı Ad Alanınızın içinde bir Olay Hub'ı oluşturduysanız, yukarıda kaydettiğiniz Olay Hub'ı adını yapıştırın.

    Microsoft 365 Defender sizin için Olay Türleri (Tablolar) başına Olay Hub'ı oluşturmasına izin vermeyi seçerseniz, bu alanı boş bırakın.

    **Olay Türleri**: Olay Hub'ına iletmek istediğiniz Gelişmiş Tehdit Avcılığı tablolarını seçin ve ardından özel uygulamanıza iletin. Uyarı tabloları Microsoft 365 Defender, Cihazlar tabloları Uç Nokta için Microsoft Defender (EDR) ve E-posta tabloları da Office 365 için Microsoft Defender. E-posta Olayları tüm E-posta İşlemlerini kaydeder. URL (Kasa Bağlantıları), Ek (Kasa Ekler) ve Teslim Sonrası Olayları (ZAP) da kaydedilir ve NetworkMessageId alanındaki E-posta Olaylarına eklenebilir.

    :::image type="content" source="../../media/3b2ad64b6ef0f88cf0175f8d57ef8b97.png" alt-text="Microsoft Azure portalındaki Akış API'sinin ayarları sayfası" lightbox="../../media/3b2ad64b6ef0f88cf0175f8d57ef8b97.png":::

1. **Gönder'e** tıkladığından emin olun.

### <a name="verify-that-the-events-are-being-exported-to-the-event-hub"></a>Olayların Olay Hub'ına aktarıldığını doğrulayın

Basit bir Gelişmiş Tehdit Avcılığı sorgusu çalıştırarak olayların Olay Hub'ına gönderildiğini doğrulayabilirsiniz. **Tehdit Avcılığı** \> **Gelişmiş Tehdit Avcılığı** \> **Sorgusu'na** tıklayın ve aşağıdaki sorguyu girin:

```console
EmailEvents
|joinkind=fullouterEmailAttachmentInfoonNetworkMessageId
|joinkind=fullouterEmailUrlInfoonNetworkMessageId
|joinkind=fullouterEmailPostDeliveryEventsonNetworkMessageId
|whereTimestamp\>ago(1h)
|count
```

Bu, son bir saatte diğer tüm tablolarda kaç e-posta alındığını gösterir. Ayrıca olay hub'larına aktarılabilir olaylar görüp görmediğinizi de gösterir. Bu sayı 0 gösteriyorsa Olay Hub'ına giden hiçbir veri görmezsiniz.

:::image type="content" source="../../media/c305e57dc6f72fa9eb035943f244738e.png" alt-text="Microsoft Azure portalındaki gelişmiş avcılık sayfası" lightbox="../../media/c305e57dc6f72fa9eb035943f244738e.png":::

Dışarı aktarabileceğiniz veriler olduğunu doğruladıktan sonra, iletilerin geldiğini doğrulamak için Olay Hub'ı sayfasını görüntüleyebilirsiniz. Bu işlem bir saate kadar sürebilir.

1. Azure'da **Olay** Hub'ı'na \> gidin **Ad Alanı** \> **Olay Hub'ına** tıklayın **Olay Hub'ına**\> tıklayın.
1. **Genel Bakış'ın** altında aşağı kaydırın ve İletiler grafiğinde Gelen İletiler'i görmeniz gerekir. Herhangi bir sonuç görmüyorsanız, özel uygulamanızın alacağı hiçbir ileti olmayacaktır.

:::image type="content" source="../../media/e88060e315d76e74269a3fc866df047f.png" alt-text="Microsoft 365 Azure portal Genel Bakış sayfası" lightbox="../../media/e88060e315d76e74269a3fc866df047f.png":::
