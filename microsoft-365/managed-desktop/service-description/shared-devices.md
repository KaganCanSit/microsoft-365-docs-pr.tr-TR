---
title: Paylaşılan cihazlar
description: Paylaşılan cihaz modunun nasıl ve ne zaman kullanımı
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
ms.openlocfilehash: 45729a40ecab2548b3125559ac3a971e5134f190
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320809"
---
# <a name="shared-devices"></a>Paylaşılan cihazlar

Microsoft Yönetilen Masaüstü, paylaşılan kullanıcıların sunduğu paylaşılan cihaz moduna benzer şekilde cihazları "paylaşılan cihaz modunda" [kaydetmenizi Microsoft Intune](/mem/intune/configuration/shared-user-device-settings).

Bu moddaki cihazlar, kullanıcıların tek bir masanın üzerine bağlı olmadığını ve cihazları sık sık değiştir olduğu durumlar için en iyi duruma getirilmiş durumdadır. Örneğin, banka veli veya personel gibi ön satır çalışanları. Bu modda tüm Microsoft Yönetilen Masaüstü [profillerini](profiles.md) cihazlara uygulayabilirsiniz. Bu modda kaydedilen cihazların bazı önemli farklılıkları vardır:

- [Cihaz depolaması](#device-storage) paylaşılan kullanıcılar için en iyi duruma getirilmiş.
- [Etkin olmayan hesaplar](#deletion-of-inactive-accounts) silinir.
- [Konuk hesapları](#guest-accounts) varsayılan olarak destek değildir.
- [Microsoft 365 Lisanslama](#microsoft-365-apps-for-enterprise) uygulamaları paylaşılan cihazlar için en iyi duruma getirilmiş.

Microsoft Yönetilen Masaüstü'nde kayıt sırasında paylaşılan cihaz modunu kullanma seçiminiz olduğundan, daha sonra bu modu değiştirmek için modu geri almak ve yeniden kaydetmek gerekir.

## <a name="when-to-use-shared-device-mode"></a>Paylaşılan cihaz modu ne zaman kullanılabilir?

Kullanıcıların cihazları sık sık değiştir olduğu durumlar.

Örneğin, bankamasaya yatırılan paraları yöneten tek bir konumda yer almakla birlikte, kredi ödemesi yapılan müşterilere yardımcı olmak için geri ofislere mi taşınabilirsiniz? Bu konumların her biri, cihaz farklı uygulamalar çalıştırır ve bu görevler için en iyi duruma getirilmiş olsa da, bunlar birden çok kişi tarafından kullanılır.

Personel genellikle hastalar ile etkileşim kurarak odalar ve ofisler arasında hareket eder. İş istasyonuna bağlanarak uzak masaüstüne bağlanarak not almalarını sağlar ve farklı bir hasta ile farklı bir odada bu işlemi tekrarlarlar.

## <a name="when-not-to-use-shared-device-mode"></a>Paylaşılan cihaz modu ne zaman kullanılamaz?

Paylaşılan cihaz modu şu durumlarda iyi bir tercih değildir:

- Kullanıcının dosyalarının bulutta değil yerel olarak depolanmış olması gerekirse
- Cihaz üzerinde farklı kullanıcılar için kullanıcı deneyiminin farklı olması gerekirse
- Her kullanıcının ihtiyacı olan uygulamalar kümesi birbirinden çok farklı ise

## <a name="enroll-new-devices-in-shared-device-mode"></a>Paylaşılan cihaz modunda yeni cihazları kaydetme

İster siz ister bir iş ortağının kaydı işlemektedir, paylaşılan cihaz modunu kullanmayı seçebilirsiniz.

Cihazları kendiniz kaydedıyorsanız, El ile kayıt'daki adımları izleyin [](../get-started/manual-registration.md)ve ardından bunları Modern Çalışma Alanı Cihazları **- Paylaşılan Cihaz Modu grubuna** ekleyin.

> [!WARNING]
> Var olan Microsoft Yönetilen Masaüstü cihazlarını yalnızca bu gruba ekleyerek paylaşılan cihaz moduna dönüştürmeye çalışmayın. Uygulanan ilkeler, olası OneDrive kalıcı olarak kaybolabilir.

Cihazları iş ortağı kaydı için aldıysanız, aşağıdaki tabloda gösterildiği gibi İş [](../get-started/partner-registration.md)ortağı kaydı ama **-Shared'ın** grup etiketine eklemesi adımlarını izleyin:

| Cihaz profili | AutoPilot grup etiketi (standart mod) | Grup etiketi (paylaşılan cihaz modu) |
| ----- | ----- | ----- |
| Hassas veriler | Microsoft365Managed_SensitiveData |  Microsoft365Managed_SensitiveData-Shared |
| Güçlü kullanıcı | Microsoft365Managed_PowerUser | Desteklenmiyor |
| Standard  | Microsoft365Managed_Standard | Microsoft365Managed_Standard-Shared |

## <a name="consequences-of-shared-device-mode"></a>Paylaşılan cihaz modunun sonuçları

### <a name="device-storage"></a>Cihaz depolama alanı

Paylaşılan cihazların kullanıcıları, diğer cihazlara takip etmek için verilerini buluta depolamalı. Cihazları paylaşılan cihaz modunda kaydettiktan sonra, bu cihazın Files [On-Demand](https://support.microsoft.com/office/save-disk-space-with-onedrive-files-on-demand-for-windows-10-0e6860d3-d9f3-4971-b321-7092438fb38e#:~:text=%20Turn%20on%20Files%20On-Demand%20%201%20Make,files%20as%20you%20use%20them%20box.%20More%20) OneDrive bilinen klasör yeniden yönlendirme özelliklerini etkinleştirmeyi [de sağlarsınız](/onedrive/redirect-known-folders). Bu yaklaşım, her kullanıcı profilinin cihaz depolama alanı üzerindeki etkisini en aza indirger. Paylaşılan cihaz modundaki cihazlar, boş disk alanı %25'in altına düştüğünde kullanıcı profillerini otomatik olarak siler. Depolama alanı kritik bir sınır olmadığı sürece, bu etkinlik, cihazın yerel saatiyle gece yarısına zamanlandı.

Microsoft Yönetilen Masaüstü bu [işlemleri yapmak için SharedPC](/mem/intune/configuration/shared-user-device-settings-windows) CSP'yi kullanır, bu nedenle bu CSP'leri kendiniz kullanmayabilirsiniz.

> [!IMPORTANT]
> Kullanıcılarınıza, büyük bir dosya indirdikten sonra, oturumlarını imzalamadan önce dosyada yeşil onay simgesini görmeleri gerektiğini onaylamaları gerektiğini eğitin. Temizleme işlemlerinin bir parçası olarak hesapları silinirse ve dosya başka bir hesaba tamamen yüklenmemişse OneDrive, dosya kalıcı olarak kaybolur.

### <a name="deletion-of-inactive-accounts"></a>Etkin olmayan hesapları silme

Paylaşılan cihaz modu, 30 gündür oturum alıkan hesapları kaldırır.

### <a name="guest-accounts"></a>Konuk hesapları

Paylaşılan cihaz modundaki cihazlar yalnızca etki alanına katılmış hesaplara izin verir. Bir cihazda konuk hesabına ihtiyacınız varsa, etkinleştirmelerini talep etmek için [bir](../working-with-managed-desktop/admin-support.md) değişiklik isteğinde bulunabilirsiniz.

### <a name="microsoft-365-apps-for-enterprise"></a>Microsoft 365 Kurumsal Uygulamaları

[Kurumlar için Microsoft 365 Uygulamaları](/microsoft-365/managed-desktop/get-started/m365-apps) belirli bir kullanıcının bu uygulamaları yalnızca beş cihaza aynı anda yüklemelerine izin verir. Paylaşılan cihaz modunda uygulamalar sınıra göre sayılmaz, dolayısıyla cihazlar arasında dolaşım sırasında bu uygulamaları kullanabilirler. Dağıtım ve güncelleştirmeler Kurumlar için Microsoft 365 Uygulamaları şekilde çalışır.

### <a name="device-profiles"></a>Cihaz profilleri

Paylaşılan cihaz modunda, verilen bir cihazda yalnızca [bir](profiles.md) cihaz profiliniz olabilir. Ayrıca, Power kullanıcı cihaz profili şu anda paylaşılan cihaz modunda desteklenmiyor.

### <a name="apps-and-policies-assigned-to-users"></a>Kullanıcılara atanmış uygulamalar ve ilkeler

Paylaşılan cihazlarda, kendinizi yönetmekte olduğu tüm uygulamaları veya ilkeleri kullanıcı gruplarına değil *cihaz gruplarına* atamanız gerekir. Cihaz gruplarına atama, her kullanıcının daha tutarlı bir deneyime sahip olması için emin olun. Bunun tek istisnası [Şirket Portalı](#deploying-apps-with-company-portal).

## <a name="limitations-of-shared-device-mode"></a>Paylaşılan cihaz modunun sınırlamaları

### <a name="windows-hello"></a>Windows Hello

Windows Hello PIN'lerini güvenli bir şekilde önbelleğe almak için akıllı kart emulation [kullanır ve kullanıcıların](/windows/security/identity-protection/hello-for-business/hello-faq) kimlik doğrulama yapma sayısını en aza indirer. Ancak Windows bir cihazda aynı anda yalnızca 10 akıllı karta izin verilir. 11. kullanıcı ilk kez oturum asınca, var olan hesaplardan biri akıllı kartını kaybeder. Oturum açmalarına izin ve pin'leri önbelleğe alınmaz.

### <a name="universal-print"></a>Evrensel yazdırma

Universal print paylaşılan bir cihaza tek bir kullanıcı için bir yazıcı yüklense, bu yazıcı o cihazın tüm kullanıcıları tarafından kullanılabilir duruma gelir. Paylaşılan cihazlardaki kullanıcılar arasında yazıcıları yalıtmak için hiçbir yol yoktur.

## <a name="limitations-of-shared-device-mode-in-the-public-preview-release"></a>Genel önizleme sürümüne göre paylaşılan cihaz modunun sınırlamaları

### <a name="primary-user"></a>Birincil kullanıcı

Her Microsoft Intune bir kullanıcının birincil kullanıcısı vardır ve bu kullanıcı AutoPilot tarafından bir cihaz ayarlanırken atanır. Ancak cihazlar paylaşıldığı zaman Intune birincil kullanıcının kaldırılmasını gerektirir.

> [!IMPORTANT]
> Paylaşılan cihaz modu genel önizlemedeyken birincil kullanıcıyı kaldırmayı şu adımları izleyin: Microsoft Endpoint Manager yönetim merkezinde oturum açın, **Tüm**> cihazlar'ı **seçin, bir** cihaz seçin, ardından **PropertiesRemove**> birincil kullanıcıyı seçin ve burada listelenen kullanıcıyı silin.

### <a name="deploying-apps-with-company-portal"></a>Uygulamaları birden çok Şirket Portalı

Bazı uygulamaların büyük olasılıkla tüm cihazlarda mevcut olması gerekmayy; bu nedenle kullanıcıların bu uygulamaları yalnızca mobil cihazlardan ihtiyaçları olduğunda [yüklemelerini Şirket Portalı](/mem/intune/user-help/install-apps-cpapp-windows).

Microsoft Yönetilen Masaüstü paylaşılan Şirket Portalı modundaki cihazlar için varsayılan olarak bu özelliği devre dışı bıraktır. Dosyanın etkinleştirilmesini Şirket Portalı, değişiklik isteğini [dosyaabilirsiniz](../working-with-managed-desktop/admin-support.md). Bununla birlikte, bu genel önizlemede bu özellikle ilgili bazı sınırlamalar olduğunu unutmayın:

- Intune'da bir uygulamanın kullanıcılara [Şirket Portalı için,](/mem/intune/apps/apps-deploy) Intune'da o uygulamaya bir kullanıcı grubu atrin ve sonra her bir kullanıcı grubunu bu kullanıcı grubuna ekleyin.
- Cihazlar birincil [kullanıcıya sahip olabilir](#primary-user).
- Kullanıcının Şirket Portalı aracılığıyla yüklemiş olduğu bir uygulamayı kaldırmak için, uygulamayı o cihaza sahip tüm kullanıcılardan kaldırmanız gerekir.

> [!CAUTION]
> Şirket Portalı uygulamaları, cihaz gruplarına atanan uygulamaları kullanılabilir olarak desteklemez.

### <a name="redeployment-of-microsoft-365-apps-for-enterprise"></a>Microsoft 365 Uygulamaları için Microsoft 365 Uygulamaları yeniden Enterprise

Genel önizleme sırasında, Microsoft 365 Uygulamaları yeniden dağıtılması gerekirse, kullanıcıların aracı yüklemesini ve bu cihaza yüklemesini Kurumlar için Microsoft 365 Uygulamaları için yerel destek personeliyle iletişime geçleri gerekir.

### <a name="microsoft-teams"></a>Microsoft Teams

Kullanıcı hesabı Teams başladığında, uygulamayı kullanamadan önce güncelleştirmeleri istenir. Güncelleştirmeye izin verdiklerde, Teams arka planda kendisini güncel tutacak.
