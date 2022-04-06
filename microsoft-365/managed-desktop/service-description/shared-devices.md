---
title: Paylaşılan cihazlar
description: Paylaşılan cihaz modunu kullanma ve kullanma
keywords: Microsoft Managed Desktop, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
ms.openlocfilehash: ad9cb5e69585f0c014050b51b719e539111cf9fa
ms.sourcegitcommit: 2f6a0096038d09f0e43e1231b01c19e0b40fb358
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64687195"
---
# <a name="shared-devices"></a>Paylaşılan cihazlar

Microsoft Managed Desktop, cihazları [Microsoft Intune](/mem/intune/configuration/shared-user-device-settings) tarafından sunulan paylaşılan cihaz moduna benzer şekilde "paylaşılan cihaz modunda" kaydetmenizi sağlar.

Bu moddaki cihazlar, kullanıcıların tek bir masaya bağlı olmadığı ve cihazları sık sık değiştirdiği durumlar için iyileştirilmiştir. Örneğin, banka veznesi veya hemşirelik personeli gibi ön cephe çalışanları. bu modda Microsoft Managed Desktop [profillerinden](profiles.md) herhangi birini cihazlara uygulayabilirsiniz. Bu modda kayıtlı cihazların bazı önemli farklılıkları vardır:

- [Cihaz depolama](#device-storage) , paylaşılan kullanıcılar için iyileştirilmiştir.
- [Etkin olmayan hesaplar](#deletion-of-inactive-accounts) silinir.
- [Konuk hesapları](#guest-accounts) varsayılan olarak desteklenmez.
- [Microsoft 365 Kurumsal lisanslama uygulamaları](#microsoft-365-apps-for-enterprise) paylaşılan cihazlar için iyileştirilmiştir.

Microsoft Managed Desktop'da kayıt noktasında paylaşılan cihaz modunu kullanmayı tercih ettiğiniz için, daha sonra bu moddan çıkmak istiyorsanız, bu modun kaydını kaldırmanız ve yeniden kaydetmeniz gerekir.

## <a name="when-to-use-shared-device-mode"></a>Paylaşılan cihaz modu ne zaman kullanılır?

Kullanıcıların cihazları sık sık değiştirdiği durumlar.

Örneğin, banka vezneleri, depozitoları yöneten tek bir konumda olabilir, ancak müşterilere ipotek konusunda yardımcı olmak için bir arka ofise geçebilir. Bu konumların her birinde cihaz farklı uygulamalar çalıştırır ve bu görevler için iyileştirilmiştir ancak bunlar birden çok kişi tarafından kullanılır.

Hemşirelik personeli genellikle hastalarla etkileşime geçtikçe odalar ve ofisler arasında hareket eder. Bir ofisteki iş istasyonunda oturum açabilir, ancak uzak masaüstüne bağlanabilir ve not alabilir ve bu işlemi farklı bir odada farklı bir hastayla tekrarlayabilirler.

## <a name="when-not-to-use-shared-device-mode"></a>Paylaşılan cihaz modu kullanılmadığında

Paylaşılan cihaz modu şu durumlarda iyi bir seçenek değildir:

- Kullanıcının dosyalarının bulutta değil yerel olarak depolanması gerektiğinde
- Cihazdaki farklı kullanıcılar için kullanıcı deneyiminin farklı olması gerekiyorsa
- Her kullanıcının ihtiyaç duyduğu uygulama kümesi büyük ölçüde farklıysa

## <a name="register-new-devices-in-shared-device-mode"></a>Yeni cihazları paylaşılan cihaz moduna kaydetme

2203 yılından itibaren, cihaz kaydını siz veya iş ortağınız işlemeye devam edin, [Microsoft Managed Desktop'da Windows Autopilot kendi kendine dağıtım modu](/mem/autopilot/self-deploying) profilini kullanmayı seçebilirsiniz.

Cihazları kendiniz kaydediyorsanız, yeni cihazları Windows Autopilot Cihazları dikey penceresine aktarmanız gerekir.

**Yeni cihazları Windows Autopilot Cihazları dikey penceresine aktarmak için:**

1. Windows Autopilot Kendi kendine dağıtım modu profilini atamak istediğiniz yeni cihazlar için [donanım karmasını](../get-started/manual-registration.md#obtain-the-hardware-hash) toplayın.
2. [Microsoft Endpoint Manager portalına](https://endpoint.microsoft.com) gidin.
2. Sol gezinti **menüsünden Cihazlar'ı** seçin.
3. **Platforma göre** bölümünde **Windows'ı** seçin. Ardından **Kayıt Windows'ı** seçin.
4. **Windows Autopilot Deployment Programı** bölümünde **Cihazlar'ı** seçin.
5. 1. adımda toplanan tüm donanım karmalarını içeren .CSV dosyasını [içeri aktarın](../get-started/manual-registration.md#register-devices-by-using-the-admin-portal).
6. Windows Autopilot cihazlarını karşıya yükledikten sonra, Microsoft Managed Desktop Windows Autopilot kendi kendine dağıtım modu profilini kullanarak kaydedebilmesi için içeri aktarılan cihazların grup etiketi özniteliğini düzenlemeniz gerekir. Grup etiketi öznitelikleri için aşağıya bakın. Aşağıdaki tabloda gösterildiği gibi **-Shared** öğesini grup etiketine eklemeniz gerekir:

| Cihaz profili | Autopilot grup etiketi (standart mod) | Grup etiketi (paylaşılan cihaz modu) |
| ----- | ----- | ----- |
| Hassas veriler | Microsoft365Managed_SensitiveData |  Microsoft365Managed_SensitiveData-Shared |
| Power user | Microsoft365Managed_PowerUser | Desteklenmiyor |
| Standard  | Microsoft365Managed_Standard | Microsoft365Managed_Standard-Shared |

> [!WARNING]
> Daha önce Windows Autopilot'a aktarılmış cihazlara **-Shared** ifadesini ekleyerek grup sekmesi özniteliğini düzenlemeye çalışmayın. Microsoft365Managed_ ile başlayan Microsoft Managed Desktop grup etiketlerinden biri kullanılarak Windows Autopilot'a zaten içeri *aktarılan ancak* **başlangıçta -Shared** eklenmemiş cihazlar zaten farklı bir Azure Active Directory grubunun parçasıdır. Bu Azure Active Directory grubuna Windows Autopilot kendi kendine dağıtım modu profili atanmamış. Mevcut bir cihazı paylaşılan cihaz olarak yeniden hedeflemeniz gerekiyorsa, cihazı silmeniz ve Windows Autopilot'a yeniden kaydetmeniz gerekir.

İş ortağı kayıt cihazlarınız varsa, yukarıdaki tabloda gösterildiği gibi [İş ortağı kaydı'ndaki](../get-started/partner-registration.md) adımları izleyin, ancak grup etiketine **-Shared** ifadesini ekleyin.

## <a name="consequences-of-shared-device-mode"></a>Paylaşılan cihaz modunun sonuçları

### <a name="device-storage"></a>Cihaz depolama

Paylaşılan cihazların kullanıcılarının verilerinin diğer cihazlara kadar takip edebilmesi için verilerinin buluta yedeklenmiş olması gerekir. Cihazları paylaşılan cihaz moduna kaydettikten sonra, OneDrive [İsteğe Bağlı Dosyalar](https://support.microsoft.com/office/save-disk-space-with-onedrive-files-on-demand-for-windows-10-0e6860d3-d9f3-4971-b321-7092438fb38e#:~:text=%20Turn%20on%20Files%20On-Demand%20%201%20Make,files%20as%20you%20use%20them%20box.%20More%20) ve [bilinen klasör yeniden yönlendirme](/onedrive/redirect-known-folders) özelliklerini etkinleştirdiğinizden emin olun. Bu yaklaşım, her kullanıcı profilinin cihaz depolaması üzerindeki etkisini en aza indirir. Paylaşılan cihaz modundaki cihazlar, boş disk alanı %25'in altına düşerse kullanıcı profillerini otomatik olarak siler. Depolama kritik düzeyde sınırlanmadığı sürece bu etkinlik cihazın yerel saatinde gece yarısı için zamanlanır.

Microsoft Managed Desktop bu işlemleri yapmak için [SharedPC](/mem/intune/configuration/shared-user-device-settings-windows) CSP kullanır, bu nedenle bu CSP'leri kendiniz kullanmadığınızdan emin olun.

> [!IMPORTANT]
> Kullanıcılarınızı, büyük bir dosyayı indirdikten sonra, oturumu kapatmadan önce dosyada yeşil onay simgesini gördüklerini onaylamaları gerektiği konusunda eğitin. Temizleme işlemlerinin bir parçası olarak hesapları silinirse ve dosya OneDrive tamamen karşıya yüklenmezse, dosya kalıcı olarak kaybolur.

### <a name="deletion-of-inactive-accounts"></a>Etkin olmayan hesapları silme

Paylaşılan cihaz modu, 30 günden uzun süredir oturum açmamış tüm hesapları kaldırır.

### <a name="guest-accounts"></a>Konuk hesapları

Paylaşılan cihaz modundaki cihazlar yalnızca bir etki alanına katılmış hesaplara izin verir. Bir cihazda konuk hesaplarına ihtiyacınız varsa, etkinleştirilmelerini istemek için [bir değişiklik isteğinde](../working-with-managed-desktop/admin-support.md) bulunabilirsiniz.

### <a name="microsoft-365-apps-for-enterprise"></a>Microsoft 365 Kurumsal Uygulamaları

[Kurumlar için Microsoft 365 Uygulamaları](/microsoft-365/managed-desktop/get-started/m365-apps) genellikle belirli bir kullanıcının bu uygulamaları aynı anda yalnızca beş cihaza yüklemesine izin verir. Paylaşılan cihaz modunda uygulamalar sınıra göre sayılmaz, bu nedenle cihazlar arasında gezinirken bunları kullanabilirler. Kurumlar için Microsoft 365 Uygulamaları dağıtımı ve güncelleştirmeleri her zamanki gibi çalışır.

### <a name="device-profiles"></a>Cihaz profilleri

Paylaşılan cihaz modunda, belirli bir cihazda yalnızca bir [cihaz profiliniz](profiles.md) olabilir. Ayrıca, Power kullanıcı cihaz profili şu anda paylaşılan cihaz modunda desteklenmiyor.

### <a name="apps-and-policies-assigned-to-users"></a>Kullanıcılara atanan uygulamalar ve ilkeler

Paylaşılan cihazlarda, kendi yönettiğiniz uygulamaları veya ilkeleri kullanıcı *gruplarına değil cihaz gruplarına* atamanız gerekir. Cihaz gruplarına atamak, her kullanıcının daha tutarlı bir deneyime sahip olmasını sağlar. Özel durum [Şirket Portalı](#deploying-apps-with-company-portal).

## <a name="limitations-of-shared-device-mode"></a>Paylaşılan cihaz modunun sınırlamaları

### <a name="windows-hello"></a>Windows Hello

Windows Hello[, kullanıcı PIN'lerini](/windows/security/identity-protection/hello-for-business/hello-faq) güvenli bir şekilde önbelleğe almak için akıllı kart öykünmesini kullanır ve kullanıcıların kimlik doğrulama sayısını en aza indirir. Ancak Windows belirli bir cihazda aynı anda yalnızca 10 akıllı karta izin verir. 11. kullanıcı ilk kez oturum açtığında, mevcut hesaplardan biri akıllı kartını kaybeder. Oturum açabilecekler, ancak PIN'leri önbelleğe alınmaz.

### <a name="universal-print"></a>Evrensel yazdırma

Evrensel yazdırma paylaşılan bir cihaza tek bir kullanıcı için yazıcı yüklediğinde, bu yazıcı bu cihazın tüm kullanıcıları tarafından kullanılabilir hale gelir. Paylaşılan cihazlardaki kullanıcılar arasında yazıcıları yalıtmak mümkün değildir.

## <a name="limitations-of-shared-device-mode-in-the-public-preview-release"></a>Genel önizleme sürümünde paylaşılan cihaz modunun sınırlamaları

### <a name="primary-user"></a>Birincil kullanıcı

Her Microsoft Intune cihazın, autopilot tarafından bir cihaz ayarlandığında atanan bir birincil kullanıcısı vardır. Ancak cihazlar paylaşıldığında, Intune birincil kullanıcının kaldırılmasını gerektirir.

> [!IMPORTANT]
> Paylaşılan cihaz modu genel önizleme aşamasındayken, şu adımları izleyerek birincil kullanıcıyı kaldırdığınızdan emin olun: Microsoft Endpoint Manager yönetim merkezinde oturum açın, **CihazlarTüm**> cihazlar'ı seçin, bir cihaz seçin, ardından **Özellikler**> **Birincil kullanıcıyı** geri al'ı seçin ve burada listelenen kullanıcıyı silin.

### <a name="deploying-apps-with-company-portal"></a>uygulamaları Şirket Portalı ile dağıtma

Bazı uygulamaların büyük olasılıkla tüm cihazlarda mevcut olması gerekmez, bu nedenle kullanıcıların bu uygulamaları yalnızca [Şirket Portalı](/mem/intune/user-help/install-apps-cpapp-windows) ihtiyaç duyduklarında yüklemesini tercih edebilirsiniz.

Microsoft Managed Desktop, paylaşılan cihaz modundaki cihazlar için varsayılan olarak Şirket Portalı devre dışı bırakır. Şirket Portalı etkinleştirilmesini istiyorsanız, [değişiklik isteğinde](../working-with-managed-desktop/admin-support.md) bulunabilirsiniz. Ancak, bu genel önizlemede bu özellikte bazı sınırlamaların farkında olmanız gerekir:

- Bir uygulamayı Şirket Portalı kullanıcıların kullanımına açmak için, Intune'da bu uygulamaya [bir kullanıcı grubu atayın](/mem/intune/apps/apps-deploy) ve sonra her kullanıcıyı bu kullanıcı grubuna ekleyin.
- Cihazların [birincil kullanıcısı](#primary-user) olamaz.
- Kullanıcının Şirket Portalı aracılığıyla yüklemiş olduğu bir uygulamayı kaldırmak için uygulamayı bu cihazdaki tüm kullanıcılardan kaldırmanız gerekir.

> [!CAUTION]
> Şirket Portalı, cihaz gruplarına uygun olarak atanan uygulamaları desteklemez.

### <a name="redeployment-of-microsoft-365-apps-for-enterprise"></a>Enterprise için Microsoft 365 Uygulamaları yeniden dağıtma

Genel önizleme sırasında, Microsoft 365 Uygulamaları yeniden dağıtılması gerekiyorsa, kullanıcıların bir aracı yükseltmesi istemek ve Kurumlar için Microsoft 365 Uygulamaları bu cihaza yeniden yüklemek için yerel destek personeline başvurması gerekir.

### <a name="microsoft-teams"></a>Microsoft Teams

Bir kullanıcı Teams ilk kez başlattığında, uygulamayı kullanabilmesi için önce güncelleştirmeleri istenir. Güncelleştirmeye izin verdikten sonra Teams arka planda kendini güncel tutar.
