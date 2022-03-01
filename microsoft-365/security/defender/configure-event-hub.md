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
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom: admindeeplinkDEFENDER
ms.topic: article
MS.technology: mde
ms.openlocfilehash: 71149412285d7d9540c80ef3ad89dc3b0a6a6208
ms.sourcegitcommit: 542e6b5d12a8d400c3b9be44d849676845609c5f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2021
ms.locfileid: "63004993"
---
# <a name="configure-your-event-hub"></a>Etkinlik Hub'ını yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Etkinlik Hub'ını, etkinlik etkinliklerini en iyi şekilde Microsoft 365 Defender.

## <a name="set-up-the-required-resource-provider-in-the-event-hub-subscription"></a>Olay Merkezi aboneliğinde gerekli Kaynak Sağlayıcısını ayarlama

1. [Azure portalda](https://portal.azure.com) oturum açın.
1. **Abonelikler** > **{'i seçin Etkinlik hub'ın }Kaynak sağlayıcılarına dağıtılacağı** >  **aboneliği seçin**.
1. **Microsoft.Analizler** Sağlayıcı kayıtlı. Aksi takdirde, kaydettirin.

![Kaynak sağlayıcılarının Microsoft Azure.](../../media/f893db7a7b1f7aa520e8b9257cc72562.png)

## <a name="set-up-azure-active-directory-app-registration"></a>Uygulama Azure Active Directory ayarlama

> ! [NOT] Yönetici olmayanların uygulamaları kaydetmesine izin vermek Azure Active Directory (AAD) veya Yönetici rolüne (AAD) sahip olmak gerekir. Hizmet sorumlusuna rol atamak için ayrıca Sahip veya Kullanıcı Erişimi Yöneticisi rolünüz de olması gerekir. Daha fazla bilgi için portalda [hizmet sorumlusu olarak Azure AD & oluşturma - Microsoft Docs Microsoft kimlik platformu \| a bakın](/azure/active-directory/develop/howto-create-service-principal-portal).

1. Uygulama kayıtlarında yeni kayıt (yapısal olarak hizmet sorumlusu oluşturur) **Azure Active Directory** \> **Yeni kayıt** \> **.**

1. Formu yalnızca Ad ile doldurun (Yeniden Yönlendirme URI'si gerekmez).

    ![Uygulama kaydetme resmi.](../../media/336bc84e6be23900c43232b4ef0c253c.png)

    ![Genel Bakış bilgileri görüntüsü.](../../media/06ac04c4ff713c2065cec2ef2f99a294.png)

1. Sertifikalar ve **gizliler'e & gizli yeni istemci** \> **sırrı:**

    ![Sertifika ve sır resmi.](../../media/d2ef88d3d2310d2c60c294b569cdf02e.png)

> [!WARNING]
> **İstemci sırrına yeniden erişesiniz, bu nedenle dosyayı kaydetmeyi deneyin**.

## <a name="set-up-event-hub-namespace"></a>Olay Merkezi ad alanını ayarlama

1. Olay Merkezi Ad Alanı oluşturma:

    Etkinlik **Hub'ları \>** Ekleme'ye gidin ve istediğiniz yüke uygun fiyatlandırma katmanını, aktarım hızı birimlerini ve Otomatik Inflate'yi seçin (standart fiyatlandırma ve özellikler altında gerekir). Daha fazla bilgi için bkz[. Fiyatlandırma - Etkinlik Hub'ları \| Microsoft Azure](https://azure.microsoft.com/pricing/details/event-hubs/)

    > [!NOTE]
    > Var olan bir olay hub'ını kullanabilirsiniz, ancak aktarım hızı ve ölçeklendirme ad alanı düzeyinde ayarlanır; dolayısıyla bir olay hub'ını kendi ad alanına depolamanız önerilir.

   ![Olay Merkezi ad alanı resmi.](../../media/ebc4ca37c342ad1da75c4aee4018e51a.png)

1. Ayrıca, bu Olay Merkezi Ad Alanı'nın Kaynak Kimliği'ne de ihtiyacınız olacaktır. Azure Olay Hub'ları ad alanı sayfası Özellikleri'ne \> gidin. Kaynak Kimliği'nin altındaki metni kopyalayın ve aşağıdaki Kaynak Yapılandırması Microsoft 365 boyunca kullanmak üzere kaydını uygulayın.

    ![Özelliklerin resmi.](../../media/759498162a4e93cbf17c4130d704d164.png)

1. Olay Merkezi Ad Alanı oluşturulduktan sonra, Uygulama Kayıt Hizmeti Sorumlu'sını Okuyucu, Azure Olay Hub'ları Veri Alıcısı olarak ve Microsoft 365 Defender'ta Katılımcı olarak oturum açacak olan kullanıcıyı eklemeniz gerekir (bu işlemi Kaynak Grubu veya Abonelik düzeyinde de kullanabilirsiniz).

     Bu adımı Olay **Hub'ları Ad Alanı** \> **Erişim Denetimi (IAM)** \> Rol atamaları altında ekleyin **ve doğrulayın**:

    ![Erişim denetimi görüntüsü.](../../media/9c9c29137b90d5858920202d87680d16.png)

## <a name="set-up-event-hub"></a>Etkinlik Hub'ı ayarlama

**1. Seçenek:**

Ad Alanı'nız içinde bir Olay Merkezi oluşturabilirsiniz  ve dışarı aktarmayı seçerek tüm Olay Türleri (Tablolar) bu Olay **Merkezi'ne** yazılır.

**2. Seçenek:**

Tüm Olay Türlerini (Tablolar) tek bir Olay Hub'ını dışarı aktar yerine, her tabloyu Olay Merkezi Ad Alanı'nız içinde farklı bir Olay Merkezi'ne aktarabilirsiniz (Olay Türü başına bir Olay Hub'ı).

Bu seçenekte, Microsoft 365 Defender Hub'ları sizin için oluşturacak.

> [!NOTE]
> Olay Merkezi Kümesi'nin parçası değil de bir Etkinlik  Merkezi Ad Alanı kullanıyorsanız, Azure'da Olay Merkezi Ad Alanı başına 10 Olay Hub'ı sınırlaması nedeniyle tanımladığınız her Dışarı Aktarma olayına en çok 10 Olay Türü (Tablo Ayarlar) aktarabilirsiniz.

Örneğin:

![Örnek Olay Merkezi görüntüsü.](../../media/005c1f6c10c34420d387f594987f9ffe.png)

Bu seçeneği seçerseniz, E-posta tablolarını göndermek [için Microsoft 365 Defender yapılandırma bölümüne geçebilirsiniz](#configure-microsoft-365-defender-to-send-email-tables).

Etkinlik Hub'ları + Olay Merkezi'ne seçerek Ad **Alanınız içinde bir** \> **Olay Merkezi oluşturun**.

Bölüm Sayısı paralellik yoluyla daha fazla performansa olanak sağlar, bu nedenle beklemediğiniz yüke bağlı olarak bu say ın artması önerilir. Varsayılan İleti Bekletme ve Yakalama 1 ve Kapalı değerleri önerilir.

![Etkinlik Merkezi oluşturma resmi.](../../media/1db04b8ec02a6298d7cc70419ac6e6a9.png)

Bu Olay Merkezi için (ad alanı olarak değil) Gönderme, Talepleri Dinleme ile paylaşılan bir Erişim İlkesi yapılandırmanız gerekir. Etkinlik Merkezi Paylaşılan **erişim** \> ilkeleri **+** **Ekle'ye** \> tıklayın ve İlke adı (başka yerde kullanılmadı) verin ve Gönder **ve Dinle'yi** **seçin**.

![Paylaşılan erişim ilkelerinin resmi.](../../media/1867d13f46dc6a0f4cdae6cf00df24db.png)

## <a name="configure-microsoft-365-defender-to-send-email-tables"></a>E Microsoft 365 Defender ta tablo gönderecek şekilde yapılandırma

### <a name="set-up-microsoft-365-defender-send-email-tables-to-splunk-via-event-hub"></a>Etkinlik Merkezi Microsoft 365 Defender E-posta tablolarını Splunk'a gönderme hakkında bilgi ayarlama

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender'da</a>, tüm aşağıdaki rol gereksinimlerini karşılayacak bir hesap kullanarak oturum açın:

    - Dışarı aktaracağız Olay Merkezi için Olay Merkezi *Ad* Alanı Kaynağı düzeyinde veya daha yüksek bir düzeyde katılımcı rolü. Bu izin olmadan, ayarları kaydetmeyi deneyebilirsiniz.

    - Microsoft 365 Defender Azure'a bağlı kiracıda Genel Yönetici veya Güvenlik Microsoft 365 Defender rolü.

    ![Güvenlik portalının resmi.](../../media/55d5b1c21dd58692fb12a6c1c35bd4fa.png)

1. Ham Veri **Dışarı Aktar +Ekle'ye \> tıklayın**.

    Şimdi yukarıda kayıtlı verileri kullanıcaz.

    **Ad**: Bu değer yereldir ve ortamınıza en iyi şekilde çalışıyor olması gerekir.

    **Olayları etkinlik hub'kutusuna iletme**: Bu onay kutusunu seçin.

    **Olay Merkezi Kaynak Kimliği**: Bu değer, Olay Hub'ını ayarlarken kaydettiğiniz Olay Merkezi Ad Alanı Kaynak Kimliğidir.

    **Olay Merkezi adı**: Olay Merkezi Ad Alanı içinde bir Olay Merkezi oluşturduysanız, yukarıya kayıtlı Olay Merkezi adını yapıştırın.

    Olay Türleri (Tablolar) başına Microsoft 365 Defender Hub'ları oluşturmanızı tercih ediyorsanız, bu alanı boş bırakın.

    **Etkinlik Türleri**: Etkinlik Merkezi'ne iletip özel uygulamanıza iletebilirsiniz Gelişmiş Av tablolarını seçin. Uyarı tabloları Diğer Microsoft 365 Defender, Cihazlar tabloları Uç Nokta için Microsoft Defender (EDR) ve E-posta tabloları Office 365. E-posta Olayları tüm E-posta İşlemlerini kayıtları. AYRıCA URL (Kasa Bağlantıları), Ek (Kasa Ekleri) ve Teslim Olayları Gönder (ZAP) de kaydedilir ve NetworkMessageId alanında E-posta Olayları'ne bir araya gönderilebilir.

    ![Akış API ayarları görüntüsü.](../../media/3b2ad64b6ef0f88cf0175f8d57ef8b97.png)

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

Bu size, tüm diğer tablolarda bir araya gelen son saatte kaç e-posta alınmıştır? gösterir. Ayrıca, olay hub'ını dışarı aktaracak olayları görüyorsanız da bunu size gösterir. Bu sayı 0 sayısını gösteriyorsa, Etkinlik Merkezi'ne gidip gelen hiçbir veri görmeyebilirsiniz.

![Gelişmiş av görüntüsü.](../../media/c305e57dc6f72fa9eb035943f244738e.png)

Dışarı aktarlanacak veriler olduğunu doğruladıktan sonra, Olay Merkezi'ne bakarak iletilerin gelen olduğunu doğrularsınız. Bu bir saat kadar zaman alabiliyor.

1. Azure'da Olay **Hub'ları'ne gidin** \> **Ad Alanı** \> **Olay Hub'ları'nın** \> üzerine **tıklayın Olay Hub'ını tıklatın**.
1. Genel **Bakış'ın** altında aşağı kaydırın ve İletiler grafiğinde Gelen İletiler'i görebilirsiniz. Hiçbir sonuç görmüyorsanız, özel uygulamanız için istediğiniz ileti olmayacaktır.

    ![İletilerle birlikte genel bakış sekmesinin resmi.](../../media/e88060e315d76e74269a3fc866df047f.png)
