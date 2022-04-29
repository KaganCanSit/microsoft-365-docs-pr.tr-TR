---
title: Basic Mobility ve Security'de mobil cihazı silme
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- admindeeplinkMAC
search.appverid:
- MET150
description: Kayıtlı cihazlardan bilgileri kaldırmak için yerleşik Basic Mobility ve Security'yi kullanın.
ms.openlocfilehash: 959e785958dd6d447713507ee9c48763b814db78
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65129100"
---
# <a name="wipe-a-mobile-device-in-basic-mobility-and-security"></a>Basic Mobility ve Security'de mobil cihazı silme

Yalnızca kuruluş bilgilerini kaldırmak veya bir mobil cihazdan tüm bilgileri silmek ve fabrika ayarlarına geri yüklemek üzere fabrika sıfırlaması gerçekleştirmek için Microsoft 365 için yerleşik Temel Mobilite ve Güvenlik'i kullanabilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

Mobil cihazlar hassas kuruluş bilgilerini depolayabilir ve kuruluşunuzun Microsoft 365 kaynaklarına erişim sağlayabilir. Kuruluşunuzun bilgilerinin korunmasına yardımcı olmak için Fabrika ayarlarına sıfırlama veya Şirket verilerini kaldırma işlemi gerçekleştirebilirsiniz:

- **Fabrika sıfırlaması**: Yüklü uygulamalar, fotoğraflar ve kişisel bilgiler de dahil olmak üzere kullanıcının mobil cihazındaki tüm verileri siler. Temizleme işlemi tamamlandığında cihaz fabrika ayarlarına geri yüklenir.

- **Şirket verilerini kaldırma**: Yalnızca kuruluş verilerini kaldırır ve yüklü uygulamaları, fotoğrafları ve kişisel bilgileri kullanıcının mobil cihazında bırakır.

- **Cihaz silindiğinde (Fabrika Sıfırlaması veya Şirket Verilerini Kaldırma)** cihaz yönetilen cihazlar listesinden kaldırılır.

- **Cihazı otomatik olarak sıfırla**: Kullanıcı cihaz parolasını belirli bir sayıda girmeye çalıştıktan sonra cihazı otomatik olarak sıfırlayan bir Temel Hareket ve Güvenlik ilkesi ayarlayabilirsiniz. Bunu yapmak için [Temel hareket ve güvenlikte cihaz güvenlik ilkeleri oluşturma bölümündeki](create-device-security-policies.md) adımları izleyin.

- Cihazını silerken **kullanıcı deneyimini öğrenmek istiyorsanız** bkz. [Kullanıcı ve cihaz etkisi nedir?](#whats-the-user-and-device-impact).

## <a name="wipe-a-mobile-device"></a>Mobil cihazı silme

1. [Microsoft 365 yönetim merkezi](../../admin/admin-overview/admin-center-overview.md) gidin.

2. Arama alanına Mobile Cihaz Yönetimi yazın ve sonuç listesinden **Mobil Cihaz Yönetimi'ı** seçin.

    :::image type="content" source="../../media/basic-mobility-security/bms-6-mobile-device-management-option.png" alt-text="Temel Hareketlilik ve Gizlilik mobil cihaz yönetimi seçeneği.":::

3. **Cihazları yönet'i** seçin.

4. Silmek istediğiniz cihazı seçin.

5. **Yönet'i** seçin.

6. Yapmak istediğiniz uzaktan silme türünü seçin.

    - Tam silme işlemi yapmak ve cihazı fabrika ayarlarına geri yüklemek için **Fabrika ayarlarına sıfırla'yı** seçin.
    - Seçmeli silme işlemi yapmak ve yalnızca Microsoft 365 kuruluş bilgilerini silmek için **Şirket verilerini kaldır'ı** seçin.
    - Cihazı kuruluşunuzdan kaldırmak için **Cihazı kaldır'ı** seçin.

7. Onaylamak için **Evet**'i seçin.

## <a name="how-do-i-know-it-worked"></a>Nasıl yaparım? çalıştığını biliyor musun?

Mobil cihazı artık yönetilen cihazlar listesinde görmezsiniz.

## <a name="why-would-you-want-to-wipe-a-device"></a>Bir cihazı neden silmek istiyorsunuz?

Bir cihazı şu nedenlerle silin:

- Akıllı telefonlar ve tabletler gibi mobil cihazlar her zaman daha fazla tam özellikli hale geliyor. Bu, kullanıcılarınızın kişisel kimlik veya gizli iletişim gibi hassas kurumsal bilgileri depolamasının ve harekette bunlara erişmesinin daha kolay olduğu anlamına gelir. Bu mobil cihazlardan biri kaybolur veya çalınırsa, cihazın silinmesi kuruluşunuzun bilgilerinin yanlış ellere geçmesini önlemeye yardımcı olabilir.
- Bir kullanıcı, Temel Mobilite ve Güvenlik'e kayıtlı bir kişisel cihazla kuruluştan ayrıldığında, fabrika sıfırlaması yaparak kuruluş bilgilerinin bu kullanıcıyla birlikte olmasını önlemeye yardımcı olabilirsiniz.
- Kuruluşunuz kullanıcılara mobil cihazlar sağlıyorsa, zaman zaman cihazları yeniden atamanız gerekebilir. Yeni bir kullanıcıya atamadan önce cihazda Fabrika Sıfırlaması yapmak, önceki sahibin hassas bilgilerinin silinmesine yardımcı olur.

## <a name="whats-the-user-and-device-impact"></a>Kullanıcı ve cihaz etkisi nedir?

Temizleme hemen mobil cihaza gönderilir ve cihaz Azure Active Directory'de uyumlu değil olarak işaretlenir. Bir cihaz fabrika varsayılanlarına sıfırlandığında tüm veriler kaldırılsa da, şirket verilerini kaldırdığınızda her cihaz türü için hangi içeriğin kaldırıldığı aşağıdaki tabloda açıklanmaktadır.

|İçerik etkisi|iOS|Android|
|---|---|---|
|Microsoft 365 uygulama verileri, cihaz Intune Uygulama Koruma ilkeleri tarafından korunuyorsa silinir. Uygulamalar kaldırılmaz. Mobil Uygulama Yönetimi (MAM) ilkeleriyle korunmayan cihazlar için Outlook ve OneDrive önbelleğe alınan verileri kaldırmaz.<br/>**Not** Intune Uygulama koruması ilkeleri uygulamak için Intune lisansına sahip olmanız gerekir.|Evet|Evet|
|Temel Mobilite ve Güvenlik tarafından cihazlara uygulanan ilke ayarları artık zorunlu değildir; kullanıcılar ayarları değiştirebilir.|Evet|Evet|
|Basic Mobility ve Security tarafından oluşturulan e-posta profilleri kaldırılır ve cihazdaki önbelleğe alınmış e-posta silinir.|Evet|Yok|

> [!NOTE]
> Şirket Portalı uygulaması iOS için App Store ve Android cihazlar için Play Store'da kullanılabilir.
