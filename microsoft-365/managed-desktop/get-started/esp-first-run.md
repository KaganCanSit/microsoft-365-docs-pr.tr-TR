---
title: AutoPilot ve Kayıt Durumu Sayfası ile ilk çalıştırma deneyimi
description: ESP deneyiminin dağıtımı, kullanılan ayarlar ve yapılandırma değişiklikleri
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
audience: ITpro
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: ff4e7dc306ea3a017cb94261673d1325bc7cf94e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324599"
---
# <a name="first-run-experience-with-autopilot-and-the-enrollment-status-page"></a>AutoPilot ve Kayıt Durumu Sayfası ile ilk çalıştırma deneyimi

Microsoft Yönetilen Masaüstü, kullanıcılarınıza Windows ilk çalıştırma Microsoft Intune en iyi deneyimi sağlamak için [hem AutoPilot'un](/windows/deployment/windows-autopilot/windows-autopilot) hem de Microsoft Intune'un Kayıt Durumu Sayfasını [(ESP)](/windows/deployment/windows-autopilot/enrollment-status) kullanır.

## <a name="initial-deployment"></a>İlk dağıtım

ESP deneyimini sağlamak için cihazları Microsoft Yönetilen Masaüstü hizmetine kaydetmelisiniz. Kayıt hakkında daha fazla bilgi için bkz. [El ile kayıt](../get-started/manual-registration.md) veya [İş ortağı kaydı](../get-started/partner-registration.md).
Kayıt Durumu Sayfası ve Önceden sağlanan dağıtım için AutoPilot, Microsoft Yönetilen Masaüstü'de varsayılan olarak etkindir.

## <a name="autopilot-profile-settings"></a>AutoPilot profil ayarları

Microsoft Yönetilen Masaüstü, kullanıcılarının cihazları için kullanılan AutoPilot profilinde şu ayarları kullanır:

| Ayar | Değer |
| ----- | ----- |
| Dağıtım modu | Kullanıcı Tarafından Yönlendir |
| Azure AD'ye farklı katılma | Azure AD katıldı |
| Dil (Bölge) | Kullanıcı Seçimi |
| Klavyeyi otomatik olarak yapılandırma | Hayır |
| Microsoft Yazılımı Lisans Koşulları | Gizle |
| Gizlilik ayarları | Gizle |
| Hesap değiştirme seçeneklerini gizle | Göster |
| Kullanıcı hesap türü| Standard |
| Boş Beyaz Beyaz Deneyime İzin Ver (OOBE) | Evet |
| Cihaz adı şablonu uygulama | Evet |
| Ad girin | `MMD-%RAND:11%` |

## <a name="enrollment-status-page-settings"></a>Kayıt Durumu Sayfası ayarları

Microsoft Yönetilen Masaüstü, Kayıt Durumu Sayfası deneyimi için şu ayarları kullanır:

| Ayar | Değer |
| ------ | ------ |
| Uygulama ve profil yapılandırmasının ilerlemesini gösterme | Evet |
| Yükleme belirtilen dakika sayısından uzun sürerken hata göster | 60 |
| Süre sınırı hatası oluştuğunda özel iletiyi göster | Hayır |
| Kullanıcıların yükleme hataları hakkında günlük toplamasına izin verme| Evet |
| Sayfayı yalnızca ilk önce sağlanan cihazlara gösterme deneyimi (OOBE) | Evet |
| Tüm uygulamalar ve profiller yükleninceye kadar cihaz kullanımını engelleme | Evet |
| Yükleme hatası oluşursa kullanıcıların cihazı sıfırlamasına izin ver | Evet |
| Yükleme hatası oluşursa kullanıcıların cihazı kullanmasına izin ver | Evet |
| Kullanıcıya/cihaza atanana kadar bu gerekli uygulamalar yükleninceye kadar cihaz kullanımını engelle <ul><li> Modern Çalışma Alanı - Saat Düzeltmesi</li><li>Modern Çalışma Alanı - İstemci Kitaplığı</li></ul> | Evet |

Kayıt Durumu Sayfası deneyimi üç aşamada  gerçekleşir. Daha fazla bilgi için [bkz. Kayıt Durumu Sayfası izleme bilgileri](/mem/intune/enrollment/windows-enrollment-status#enrollment-status-page-tracking-information).

Deneyim aşağıdaki gibi devam eder:

1. AutoPilot deneyimi başlatılır ve kullanıcı kimlik bilgilerini girer.
2. Cihaz Kayıt Durumu Sayfasını açar ve Cihaz Hazırlama ve Cihaz Ayarlama aşamalarıyla devam eder. Üçüncü adım (Hesap Kurulumu), *şu anda Microsoft Yönetilen* Masaüstü yapılandırmasında atlanır çünkü Kullanıcı ESP devre dışı bırakılır. Cihaz yeniden başlatılır.
3. Yeniden başlatmanın ardından, cihaz Diğer Windows oturum açma **sayfasında oturum açma sayfasını açar**.
4. Kullanıcılar kimlik bilgilerini yeniden girerken masaüstü açılır.

> [!NOTE]
> Win32 uygulamaları, yalnızca 1903 veya daha sonraki bir Windows 10, ESP sırasında dağıtılır.

!["Cihaz hazırlama" ve "cihaz kurulumu" aşamalarını gösteren AutoPilot kurulumunun Başlangıç sayfası.](../../media/mmd-autopilot-screenshot.png)

## <a name="additional-prerequisites-for-autopilot-for-pre-provisioned-deployment"></a>Önceden sağlanan dağıtım için AutoPilot'a ek önkoşullar

- Cihazın kablolu bir ağ bağlantısı olmalıdır.
- Microsoft Yönetilen Masaüstü portalı kullanılarak Ağustos 2020'den önce kaydedilmiş cihazlarınız varsa cihazları yeniden kaydettirin ve yeniden kaydedin.
- Cihazlar, Kasım 2020 toplu güncelleştirmesi [19H1/19H2 2020.11C](https://support.microsoft.com/topic/november-19-2020-kb4586819-os-builds-18362-1237-and-18363-1237-preview-25cbb849-74af-b8b8-29b8-68aa925e8cc3) veya [20H1 2020.11C](https://support.microsoft.com/topic/november-30-2020-kb4586853-os-builds-19041-662-and-19042-662-preview-8fb07fb8-a7dd-ea62-d65e-3305da09f92e) yüklü olan bir fabrika resmine sahip olmalı veya en son Microsoft Tarafından Yönetilen Masaüstü resmiyle yeniden yüklenmiş olmalı.
- Fiziksel cihazlar TPM 2.0'ı ve cihaz attestation'ı desteklemeli. Sanal makineler desteklenmiyor. Önceden sağlama işlemi Autopilot'Windows kendi kendine dağıtma özelliklerini kullandığı için TPM 2.0 gereklidir. TPM attestation işlemi, her TPM sağlayıcısı için benzersiz olan bir dizi HTTPS URL'si için de erişim gerektirir. Daha fazla bilgi için, AutoPilot kendi kendine dağıtım modu ve AutoPilot ağ gereksinimleri altında [AutoPilot'ın önceden Windows girdilerine bakın](/mem/autopilot/networking-requirements#tpm).

## <a name="sequence-of-events-in-autopilot-for-pre-provisioned-deployment"></a>Önceden sağlanan dağıtım için AutoPilot'daki olay dizisi

1. IT Yöneticisi gerekirse cihazı yeniden gösterir veya sıfırlar.
2. IT Admin cihazı her zaman ilk kez istiyor, ilk kez istiyor ve Windows kez basıyor.
3. IT Yöneticisi, Otomatik Windows'i seçer ve sonra da Devam'ı **seçer**. AutoPilot Windows yapılandırma ekranında, cihaz hakkında bilgiler görüntülenir.
4. IT yöneticisi, sağlama **işlemini** başlatmak için Sağlama'ya karar verdi.
5. Cihaz ESP'i başlatır ve cihaz hazırlığı ve kurulum aşamalarını tamamlar. Cihaz kurulumu aşamasında, Uygulama yükleme **x / x** görüntülenir (ESP profilinin tam yapılandırmasına bağlı olarak).
6. Kullanıcı ESP'yi devre dışı bırakıyoruz ve bu nedenle hesap kurulumu adımı şu anda Microsoft Yönetilen Masaüstü yapılandırmasında atlanır.
7. Cihaz yeniden başlatılır.

Cihaz yeniden başlatıldıktan sonra, yeniden bak düğmesiyle birlikte yeşil **durum ekranı gösterir** .

> [!IMPORTANT]
> Bilinen sorunlar:
>
> - ÖNCEDEN sağlanan dağıtım yeniden sağlama işlevi için AutoPilot'ın ardından ESP yeniden çalışmıyor.
> - Cihaz, önceden sağlanan dağıtım için AutoPilot tarafından yeniden adlandırılamaz. Cihaz yalnızca ESP kullanıcı akışı üzerinden değiştirildikten sonra yeniden adlandırılır.

## <a name="change-to-autopilot-and-enrollment-status-page-settings"></a>AutoPilot ve Kayıt Durumu Sayfası ayarlarına değiştirme

Microsoft Yönetilen Masaüstü tarafından kullanılan kurulum sizin ihtiyaçlarınıza tam olarak uygunsa, Yönetim Portalı'nı kullanarak destek bileti [açabilirsiniz](https://portal.azure.com/). Aşağıda, ihtiyacınız olabilir yapılandırma türlerine bazı örnekler verilmiştir:

### <a name="autopilot-settings-change"></a>AutoPilot ayarları değişti

Farklı bir cihaz adı şablonu istemeniz iyi olabilir. Bununla birlikte, Dağıtım Modunu, Azure AD'ye Katıl' veya Gizlilik Ayarları'Ayarlar Kullanıcı Hesabı Türünü değiştiremezsiniz.

### <a name="enrollment-status-page-settings-change"></a>Kayıt Durumu Sayfası ayarları değişti

- "Yükleme, belirtilen dakika sayısından uzun sürerken hata göster" ayarı için dakika sayısı daha uzun.
- Görüntülenen hata iletisi.
- "Cihaz kullanımına atanana kadar bu gerekli uygulamalar yükleninceye kadar cihaz kullanımını engelle" ayarında uygulamaları ekleme veya kaldırma.

## <a name="required-applications"></a>Gerekli uygulamalar

- Modern Çalışma Alanı cihaz grupları Test *, İlk,* Hızlı ve Geniş'te uygulamaları hedeflemeniz gerekir. Uygulamaların "Sistem" bağlamında yüklü olması gerekir. Tüm gruplara atamadan önce Test grubunda ESP ile test işlemini tamamlayın.
- Hiçbir uygulamanın cihazın yeniden başlatılmasını gerektirmez. Cihazın yeniden başlatılmasını gerektiriyorsa uygulama paketini  derlemeniz için uygulamaların "Hiçbir şey yapma" olarak ayarlanmış olması önerilir.
- Gerekli uygulamaları, yalnızca kullanıcının cihazda oturum a gerektiğinde hemen ihtiyacı olan temel uygulamalarla sınırlandırın.
- Uygulama yükleme aşamasında zaman aşımından kaçınmak için, tüm uygulamaların toplam boyutunu toplu olarak 1 GB'nin altında tutabilirsiniz.
- İdeal olan, uygulamaların bağımlılıkları olmamasıdır. Bağımlılıkları olması gereken *uygulamalarınız* varsa, ESP değerlendirmeniz kapsamında bunları yapılandırmış, test edin ve doğrulayın.
- Microsoft Teams ESP'ye dahil değildir.

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü ile çalışmaya başlama adımları

1. Access [yönetici portalı](access-admin-portal.md).
1. [Yönetici portalında yönetici kişilerini ekleyin ve doğrulayın](add-admin-contacts.md).
1. [Kayıt sonrasında ayarları ayarlayın](conditional-access.md).
1. Dağıtım ve [Intune Şirket Portalı](company-portal.md).
1. [Lisans atama](assign-licenses.md).
1. [Uygulamaları dağıtın](deploy-apps.md).
1. [Cihazları hazırlayın](prepare-devices.md).
1. AutoPilot ve Kayıt Durumu Sayfası ile ilk çalıştırma deneyimini ayarlayın (bu makale).
1. [Kullanıcı desteği özelliklerini etkinleştirin](enable-support.md).
1. [Kullanıcılarınızı cihazları kullanmaya hazır hale hazırlayın](get-started-devices.md).
1. [Uygulama denetimi ile çalışmaya başlama](get-started-app-control.md).
