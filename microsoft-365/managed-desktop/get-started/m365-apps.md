---
title: Kurumlar için Microsoft 365 Uygulamaları
description: E-Microsoft 365 Uygulamaları nasıl dağıtabilirsiniz, bunların nasıl güncelleştiriliyor ve ayarların nasıl yönetiliyor
keywords: değişiklik geçmişi
ms.service: m365-md
ms.sitesec: library
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: 82a0bbc4811b3f2be23403717b0a0ffb485d7c74
ms.sourcegitcommit: 584b4757f715a3eedf748858461c568f45137438
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2022
ms.locfileid: "63495004"
---
# <a name="microsoft-365-apps-for-enterprise"></a>Microsoft 365 Kurumsal Uygulamaları

## <a name="initial-deployment"></a>İlk dağıtım

Microsoft Yönetilen Masaüstü Kurumlar için Microsoft 365 Uygulamaları (64 bit) tüm program cihazlarına resmin bir parçası olarak [yüklenmelerini sağlar](../service-description/device-list.md). Aşağıdaki tüm uygulamalar teslim edilirken cihazda mevcut olması gerekir:

- Word
- Excel
- PowerPoint
- Outlook
- Publisher
- Access
- Skype Kurumsal
- OneNote

Bu yaklaşım ağ etkisini en aza indirger ve kullanıcıların cihazlarını alır almaz üretken olacağını sağlar. Ardından, uygulamaları kullanım için ayarlamak üzere yönetilen cihazlara daha fazla ilke dağıtın.

> [!NOTE]
> Microsoft Teams, resimden ayrı Kurumlar için Microsoft 365 Uygulamaları dağıtılır ve temel görüntüye dahil değildir.

### <a name="available-deployment-to-users"></a>Kullanıcılara kullanılabilir dağıtım

Kullanıcının cihazında herhangi bir Microsoft 365 Uygulamaları cihazı yoksa, cihazı beklenen durumuna geri dönmek için paketi kullanabilirsiniz. Modern **Workplace-Office-Office365_Install** grubuna kullanıcı eklersiniz ve uygulamalar çalışma alanı içinde Şirket Portalı.

### <a name="microsoft-365-apps-for-enterprise-32-bit"></a>Kurumlar için Microsoft 365 Uygulamaları (32 bit)

Microsoft Yönetilen Masaüstü, masaüstü sürümünün 32 bit dağıtımını Kurumlar için Microsoft 365 Uygulamaları.

## <a name="updates-to-microsoft-365-apps"></a>Güncelleştirmeler Microsoft 365 Uygulamaları

Microsoft 365 Uygulamaları, Aylık Güncelleştirme [Kanalı'Enterprise ayarlanır](/deployoffice/overview-update-channels#monthly-enterprise-channel-overview). Bu uygulama, kullanıcılarınıza her Office yeni özellikler sağlar, ancak öngörülebilir bir sürüm zamanlamaları üzerine her ay yalnızca bir güncelleştirme alırlar. Güncelleştirmeler ayın ikinci Salı günü yayımlanacak; bu güncelleştirmeler özellik, güvenlik ve kalite güncelleştirmelerini içerebilir. Bu güncelleştirmeler otomatik olarak yapılır ve ilgili kanal Office CDN doğrudan açılır.

Microsoft Yönetilen Masaüstü basamakları, ortamınız içinde olası sorunları tanımlamak için her sürümü basamaklar. Bu uygulama ürün grubundan Microsoft 365 tamamlanmıştır. Microsoft Yönetilen Masaüstü, aşağıdaki gibi doğrulama ve test etme süresine izin vermek için güncelleştirme yayınlarını farklı gruplara zamanlar:

- Test: Sıfır gün
- İlk: Sıfır gün
- Hızlı: üç gün
- Geniş: yedi gün

Microsoft Yönetilen Masaüstü, cihazlar için yedi günlük [bir güncelleştirme son](/deployoffice/configure-update-settings-microsoft-365-apps) tarihi ayarlar. Güncelleştirme kullanılabilir olduktan sonra, yedi gün içinde yüklenmiş olması gerekir. Kullanıcılara [](/deployoffice/end-user-update-notifications-microsoft-365-apps#notifications-your-users-see-when-you-set-an-update-deadline-for-microsoft-365-apps) güncelleştirmelerin çeşitli konumlarda gerekli olduğu bildirilir: uygulama, sistem tepsisinde son tarihe 12 saat önce ve son tarihe 15 dakikalık bir uyarı alırlar. Güncelleştirmenin Microsoft 365 Uygulamaları için tüm güncelleştirmelerin kapatılmış olması gerekir.

### <a name="pausing-or-rolling-back-an-update"></a>Bir güncelleştirmeyi duraklatma veya geri dönme

Herhangi bir nedenle Uygulama güncelleştirmesini duraklatmanız veya geri Microsoft 365 gerekirse, Microsoft Yönetilen Masaüstü portalı aracılığıyla [](../working-with-managed-desktop/admin-support.md) bir yönetici destek isteği dosyalamanız gerekir.

Microsoft Yönetilen Masaüstü, sürüm sırasında tüm güncelleştirmelerin hata Microsoft 365 Uygulamaları. Yeni sürümle önceki sürüm arasında önemli bir kalite farkı görüyorsanız, size Microsoft Yönetilen Masaüstü Yöneticisi portalı üzerinden ulaşabilirsiniz.

Önem düzeyine bağlı olarak, aşağıdakiler de olur:

- Sürümü duraklatmak mı istediğinize sorun veya
- Bir sorunu azaltmak için bir işlem önlemi alınmış olduğunu size bildirin.

### <a name="delivery-optimization"></a>Teslimat iyileştirme

Teslim İyileştirme, aynı anda kullanılabilir eşler arası bir dağıtım Windows 10. Bu özellik, cihazların İnternet üzerinden Microsoft'tan indirilen güncelleştirmeler gibi içerikleri paylaşmalarını sağlar. Us Delivery Optimization can help reduce network bandwidth, because a device can get the portions of the update from another device on its local network instead download the update completely from Microsoft.

[Teslim İyileştirme](/deployoffice/delivery-optimization), en son sürümleri çalıştıran cihazlarda Windows 10 Enterprise Windows 10 Education etkinleştirilir.

## <a name="settings-managed-by-microsoft-managed-desktop"></a>Ayarlar Yönetilen Masaüstü tarafından yönetilen çalışma

Microsoft bazı ayarları hizmetin bir parçası olarak yönetir. Microsoft Yönetilen Masaüstü, güvenlik temeli Office yönetmez. Bununla birlikte, sizin yönetmenize yardımcı olan bölümdeki [rehbere Ayarlar kendiniz de kurabilirsiniz](#settings-you-manage).

### <a name="update-settings"></a>Ayarları güncelleştirme

Microsoft Yönetilen Masaüstü yönetilen cihazlar [için tüm güncelleştirme](/deployoffice/configure-update-settings-microsoft-365-apps) ayarlarını sağlar ve bu ayarları değiştirmeniz gerekir.

| Ayar | Varsayılan değer | Açıklama |
| ------ | ------ | ------ |
| Güncelleştirmeleri otomatik olarak olacak şekilde ayarlama | Etkin | Bu ilke, tüm cihaz ve cihazların buluttan Office emin olmak için yapılandırılır. |
| Güncelleştirmelerin uygulanması gereken son tarih ayarlama | Yedi gün | **UpdateDeadline ilkesi**, cihazda güncelleştirmenin zorunlu kılınmadan önce kullanıcıların sahip olduğu yetkisiz kullanım süresi yapılandırmak için kullanılır. Bu son tarih ilkesi ayrıca [, kullanıcıya](/deployoffice/end-user-update-notifications-microsoft-365-apps#notifications-your-users-see-when-you-set-an-update-deadline-for-microsoft-365-apps) cihazında gerekli değişiklikleri bildirmek için bildirimleri de tetikler. |
| Cihazda güncelleştirmeleri bir süre ertele | Açıklamaya bakın | Bu ilke, her güncelleştirme yönetimi cihaz grubu için farklı yapılandırılmıştır. Microsoft Yönetilen Masaüstü'nüz güncelleştirme hedeflerine uygun olarak gereklidir: <ul> <li> Test: Sıfır gün </li> <li>İlk: Sıfır gün</li><li>Hızlı yedi gün</li><li>Geniş: 21 gün</li></ul> |
| Bildirim ayarlarını güncelleştirme | False | Microsoft Yönetilen Masaüstü cihazlarda "güncelleştirme bildirimlerini gizle" ayarı, kullanıcılara güncelleştirmelerin gerekli olduğunu bildirerek en iyi güncelleştirme deneyimini sağlamak [](/deployoffice/end-user-update-notifications-microsoft-365-apps#notifications-your-users-see-when-you-set-an-update-deadline-for-microsoft-365-apps) için **False** olarak ayarlanır.|
| Güncelleştirmelerin konum belirtme | Aylık Enterprise Kanalı | Güncelleştirme zamanlaması elde **etmek** için **gerektiğinde UpdatePath ve UpdateChannel** ilkelerinin bir bileşimi kullanılır. Bu ilkeler, tüm cihazlarında, aylık Office Kanalı için güncelleştirmelerin doğrudan Yayından CDN sağlamak Enterprise ayarlanır.|
| Hedef Sürümü Microsoft 365 Uygulamaları | Açıklamaya bakın | Hedef Sürüm ilkesi bazen Microsoft Yönetilen Masaüstü tarafından belirli bir sürümü geri almak veya sabitlemek için Office kullanılır.|
| Otomatik güncelleştirmeleri etkinleştirme veya devre dışı bırakma Office gizleme | Etkin | Microsoft Yönetilen Masaüstü'ne, Microsoft 365 Uygulamaları'nın güncelleştirme hedeflerini karşılaması için bu ayar gereklidir. |
| İlk çalıştırma ayarları | Açıklamaya bakın | İlk kez çalıştır uygulamanın davranışını etkileyen birkaç Office vardır. |
| Son kullanıcı adına lisans koşullarını kabul etme | Devre dışı | Kullanıcı Microsoft 365 uygulamasını ilk kez açtığında, lisans koşullarını kabul etmeleri istenir. Kullanıcılarınızı adına lisans koşullarını kabul etmek için Microsoft Yönetilen Masaüstü İşlemleri ekibine bir destek isteği dosya açın ve bu ayarın etkinleştirilmesi için istekte bulunabilirsiniz. |
| Mobil Outlook kutusunu gizleme | Devre dışı | Kullanıcı e-posta Outlook ilk kez açıldığında Outlook Mobile'i yüklemesi istenir. Kullanıcılarınızı bu onay kutusunu görmelerini istemiyorsanız, Microsoft Yönetilen Masaüstü İşlemleri ekibine bir destek isteği dosya açın ve bu ayarın cihazlarınız için etkinleştirilmesi için istekte bulunabilirsiniz. |

## <a name="other-settings"></a>Diğer ayarlar

Microsoft Yönetilen Microsoft 365 sizin adına isteğe bağlı olarak yapılandırılan başka bazı uygulama ayarları da vardır.

| Ayar | Varsayılan değer | Açıklama |
| ------ | ------ | ------ |
| Kişisel bilgileri devre OneDrive | Devre dışı | Bazı kuruluşlar, kullanıcıların cihazlarında hem şirket hem de kişisel dosyalara erişimi olması konusunda kaygılar. Microsoft Yönetilen Masaüstü İşlemleri ekibine bir destek isteğinde bulunarak bu ayarın etkinleştirilmesi isteğinde bulunabilirsiniz. |

## <a name="settings-you-manage"></a>Ayarlar yönetme

Microsoft Yönetilen Masaüstü'nin henüz hizmetimizin bir parçası olarak ayarlamamış olduğu başka birçok ilke vardır. Bu ilkeleri, bulut ilkesi hizmetini Microsoft Intune bulut ilkesi Office [kullanarak yapılandırabilirsiniz](/DeployOffice/overview-office-cloud-policy-service#how-the-policy-configuration-is-applied). Bu ilkeleri ayarlamak için şu adımları izleyin:

1. Microsoft Endpoint Manager yönetim merkezinde oturum açın.
1. **Uygulamalar'ı seçin**.
1. **İlkeler ve Office'i seçin ve** sonra da **Oluştur'a seçin**.
1. İlke **yapılandırması** oluştur sayfasında şunları yapın:
    - Bir ad girin.
    - İsteğe bağlı bir açıklama girin.
    - **Atamalar'ın** altında, bu ilkenin kullanıcılarının tüm kullanıcıları için mi yoksa yalnızca Kurumlar için Microsoft 365 Uygulamaları kullanarak belgelere anonim olarak erişen kullanıcılar için Web için Office.
    - İlke **AAD tabanlı** güvenlik grubunu seçin. Her ilke yapılandırması yalnızca bir gruba atanabilir. Her gruba yalnızca bir ilke yapılandırması atanabilir.
    - İlke yapılandırmasına dahil edilecek ilke ayarlarını yapılandırabilirsiniz. Yapılandırmak istediğiniz ilke ayarını bulmak için, ilke ayarı adını arayabilirsiniz. Ayrıca, ilke önerilen bir güvenlik temeli ise ve ilke yapılandırılmışsa filtre de silmezsiniz. Platform sütunu ilkenin Kurumlar için Microsoft 365 Uygulamaları cihazlar, Windows tüm Web için Office uygulandığını gösterir.
1. Seçimlerinizi yaptıktan sonra Oluştur'a **seçin**.

> [!NOTE]
> Office İlkeleri yalnızca kullanıcı tabanlı dağıtımı destekler
