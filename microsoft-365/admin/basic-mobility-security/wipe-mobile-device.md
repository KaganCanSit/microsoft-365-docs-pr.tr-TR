---
title: Temel Mobil Kullanım ve Güvenlik'te mobil cihazı temizleme
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
description: Kayıtlı cihazlardan bilgileri kaldırmak için yerleşik Temel Mobil Kullanım ve Güvenlik'i kullanın.
ms.openlocfilehash: d5f610e2a9180f1d147f68e6aabf4a7291787033
ms.sourcegitcommit: cdb90f28e59f36966f8751fa8ba352d233317fc1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63400176"
---
# <a name="wipe-a-mobile-device-in-basic-mobility-and-security"></a>Temel Mobil Kullanım ve Güvenlik'te mobil cihazı temizleme

Microsoft 365 için yerleşik Temel Mobil Kullanım ve Güvenlik'i kullanarak yalnızca kuruluş bilgilerini kaldırabilir veya bir mobil cihazdan tüm bilgileri silebilir ve fabrika ayarlarına geri yüklemek için fabrika sıfırlaması yapabilirsiniz.

## <a name="before-you-begin"></a>Başlamadan önce

Mobil cihazlar hassas kurumsal bilgileri depolar ve kuruluşun güvenlik kaynakları için Microsoft 365 sağlar. Kuruluş bilgilerini korumaya yardımcı olmak için Fabrika sıfırlaması veya Şirket verilerini kaldır'ı yapabilirim:

- **Fabrika sıfırlaması**: Yüklü uygulamalar, fotoğraflar ve kişisel bilgiler de içinde olmak üzere kullanıcının mobil cihazıdaki tüm verileri siler. Temizleme işlemi tamamlandığında, cihaz fabrika ayarlarına geri yüklenir.

- **Şirket verilerini kaldırma**: Kullanıcının mobil cihazında yalnızca kuruluş verilerini kaldırır, yüklü uygulamaları, fotoğrafları ve kişisel bilgileri bırakır.

- **Bir cihaz temizlenmiş durumdayken (Fabrika Sıfırlaması veya Şirket Verilerini Kaldır)** cihaz, yönetilen cihazlar listesinden kaldırılır.
    
- **Cihazı otomatik olarak** sıfırlama: Kullanıcının cihaz parolasını belirli sayıda kez girmeyi denemesi başarısız olduktan sonra cihazı otomatik olarak sıfırlanacak bir Temel Mobil kullanım ve Güvenlik ilkesi oluşturabilirsiniz. Bunu yapmak için Temel mobil kullanım ve güvenlik  [için cihaz güvenliği ilkeleri yapma'daki adımları izleyin](create-device-security-policies.md).
    
- **Cihazı temizlerken kullanıcı** deneyimini bilmek için bkz   [. Kullanıcı ve cihazı nasıl etkiler?](#whats-the-user-and-device-impact)

## <a name="wipe-a-mobile-device"></a>Mobil cihazı temizleme

1. Büyük/ [yeni Microsoft 365 yönetim merkezi](../../admin/admin-overview/about-the-admin-center.md).

2. Arama alanına Mobil Cihaz Yönetimi yazın ve sonuç **listesinden Mobil Cihaz** Yönetimi'ne tıklayın.

    :::image type="content" source="../../media/basic-mobility-security/bms-6-mobile-device-management-option.png" alt-text="Temel Mobil Kullanım ve Gizlilik mobil cihaz yönetim seçeneği.":::

3. Cihazları **yönet'i seçin**.

4. Silmek istediğiniz cihazı seçin.

5. **Yönet'i seçin**.

6. Yapmak istediğiniz uzaktan silme türünü seçin.

    - Tam temizleme işlemi yapmak ve cihazı fabrika ayarlarına geri yüklemek için Fabrika **sıfırlaması'yı seçin**.
    - Seçmeli temizleme yapmak ve yalnızca kuruluş bilgilerini Microsoft 365 için Şirket verilerini **kaldır'ı seçin**.
    - Cihazı kuruluştan kaldırmak için Cihazı **kaldır'ı seçin**.

7. Onaylamak için **Evet**'i seçin.

## <a name="how-do-i-know-it-worked"></a>Çalıştığını nasıl bilim?

Artık yönetilen cihazlar listesinde mobil cihazı görmüyorsanız.

## <a name="why-would-you-want-to-wipe-a-device"></a>Cihazı neden temizlemek istemeniz gerekir?

Cihazı temizleme nedenleri:

- Akıllı telefon ve tablet gibi mobil cihazlar her zaman daha fazla öne çıkan ürün haline geliyor. Bu da, kullanıcılarının kimlik bilgileri veya gizli iletişimler gibi hassas şirket bilgilerini depolayanın ve ilerlerken bu bilgilere erişmelerini daha kolay hale getirir. Bu mobil cihazlardan biri kaybolur veya çalınırsa, cihazın silin hepsi kuruluşun bilgilerini yanlış ellere bulamanıza yardımcı olabilir.
- Bir kullanıcı Temel Hareketlilik ve Güvenlik'e kayıtlı kişisel bir cihazla kuruluştan ayrıldığında, fabrika sıfırlaması yaparak kuruluş bilgilerini bu kullanıcıyla birlikte hareket etmeye yardımcı olabilir.
- Organizasyonunız kullanıcılara mobil cihazlar sunuyorsa, zaman zaman cihazları yeniden atamanız gerekiyor olabilir. Bir cihazı yeni bir kullanıcıya atamadan önce Fabrika Sıfırlaması yapılması, önceki sahibinden gelen hassas bilgilerin silinmesini sağlar.

## <a name="whats-the-user-and-device-impact"></a>Kullanıcı ve cihazı nasıl etkiler?

Temizleme hemen mobil cihaza gönderilir ve cihaz Azure Active Directory'de uyumlu değil olarak işaretlenir. Cihaz fabrika varsayılanlara sıfırlana kadar tüm veriler kaldırılırken, aşağıdaki tabloda, şirket verilerini kaldıran bir cihaz için her cihaz türü için hangi içeriğin kaldırıldığı açıklanıyor.

|**İçerik üzerindeki etkisi**|**iOS**|**Android**|
|:-----|:-----|:-----|
|Microsoft 365 Intune Uygulama Koruması ilkeleri tarafından korundu ise uygulama verileri temizlenmiş olur. Uygulamalar kaldırılamaz. Mobil Uygulama Yönetimi (MAM) ilkeleri tarafından korunmayan cihazlar için, Outlook OneDrive ilkeleri önbelleğe alınmış verileri kaldırmaz.<br/>**Not** Intune Uygulama koruma ilkelerini uygularken Intune lisansınız olmalıdır.|Evet|Evet|
|Cihazlara Temel Mobil Kullanım ve Güvenlik tarafından uygulanan ilke ayarları artık zorunlu kılınamaz; kullanıcılar ayarları değiştirebilir.|Evet|Evet|
|Basic Mobility and Security tarafından oluşturulan e-posta profilleri kaldırılır ve cihazda önbelleğe alınan e-posta silinir.|Evet|Yok|

> [!NOTE]
> Şirket Portalı uygulaması iOS için App Store'da ve Android cihazlar için Play Store'da mevcuttur.
