---
title: Adım 4. Cihazlarınız, bilgisayarlarınız ve diğer uç noktalarınız için uç nokta yönetimini dağıtma
f1.keywords:
- NOCSH
author: JoeDavies-MSFT
ms.author: josephd
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
- m365solution-remotework
- m365solution-scenario
ms.custom: ''
description: Cihazlarınızı Microsoft Endpoint Manager bilgisayarlarınızı ve diğer uç noktaları yönetmek için Diğer Uç Noktaları Yönet'i kullanın.
ms.openlocfilehash: 03d212071db686079a76115d7cb94d2abb4cde88
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2022
ms.locfileid: "63015348"
---
# <a name="step-4-deploy-endpoint-management-for-your-devices-pcs-and-other-endpoints"></a>Adım 4. Cihazlarınız, bilgisayarlarınız ve diğer uç noktalarınız için uç nokta yönetimini dağıtma

Karma çalışanlarla, giderek artan sayıda kişisel cihazı desteklemeniz gerekir. Uç nokta yönetimi, cihazların kaynaklara erişim izni verilmeden önce belirli ölçütlere uymalarını gerektiren, ilke tabanlı bir güvenlik yaklaşımıdır. Microsoft Endpoint Manager, verilerinizi bulutta ve şirket içinde güvende tutmak için modern yönetim özellikleri sunar. 

[Microsoft Endpoint Manager](/mem/endpoint-manager-overview) zaten biliyor ve kullanıyor olduğunuz aşağıdaki hizmetleri birleştirerek mobil cihazları, masaüstü bilgisayarları, sanal makineleri, ekli cihazları ve sunucuları yönetmek için hizmetler ve araçlar sağlar.

:::image type="content" source="../media/empower-people-to-work-remotely/endpoint-managment-step-grid.png" alt-text="Uç nokta yönetiminin bileşenleri Microsoft 365" lightbox="../media/empower-people-to-work-remotely/endpoint-managment-step-grid.png":::

## <a name="microsoft-intune"></a>Microsoft Intune

Microsoft Intune, mobil cihaz yönetimi (MDM) ve mobil uygulama yönetimine (MAM) odaklanan bulut tabanlı bir hizmettir ve Microsoft 365. 

- **MDM:** Kuruluşa ait cihazlar için, ayarlar, özellikler ve güvenlik gibi tam denetimler edinebilirsiniz. Cihazlar Intune'da "kayıtlı" olarak yer alır ve burada kurallar ve ayarlarla Intune ilkeleri alırlar. Örneğin, parola ve PIN gereksinimlerini ayarlama, VPN bağlantısı oluşturma, tehdit koruması ayarlama gibi daha fazlasını kullanabilirsiniz.

- **MAM:** Uzaktan çalışanlar kendi cihazlarınızı (BYOD) getir olarak da bilinen kişisel cihazları üzerinde tam denetim sahibi olmak istemeyebilirsiniz. Karma çalışanlarınıza seçenekler sağlıyor ve yine de organizasyonlarınızı koruyabilirsiniz. Örneğin, karma çalışanlar, kuruluş kaynaklarınıza tam erişime sahip olmak isterken cihazlarını kaydolabilirsiniz. Ya da bu kullanıcılar yalnızca e-postaya veya postaya Microsoft Teams, bu uygulamaları kullanmak için çok faktörlü kimlik doğrulaması (MFA) gerektiren uygulama koruma ilkelerini kullanın.

Daha fazla bilgi için [bkz. Intune Foundation çözümüyle](manage-devices-with-intune-overview.md) cihazları yönetme.

## <a name="configuration-manager"></a>Yapılandırma Yöneticisi

Configuration Manager ağ üzerinde veya internet tabanlı olan masaüstlerini, sunucuları ve dizüstü bilgisayarları yönetmek için şirket içi bir yönetim çözümüdür. Uygulamaları, yazılım güncelleştirmelerini ve işletim sistemlerini dağıtmak için Configuration Manager'i kullanın. Ayrıca, gerçek zamanlı olarak istemcilerin uyumluluğunu, sorgusunu ve üzerinde eylemde bulundurarak daha fazlasını da izleyebilirsiniz. Intune, Azure AD, Uç Nokta için Microsoft Defender ve diğer bulut hizmetleriyle tümleştirebilirsiniz. 

Daha fazla bilgi için, Configuration [Manager'a genel bakış bilgilerine bakın](/mem/configmgr/core/understand/introduction).

## <a name="co-management"></a>Birlikte yönetim

Birlikte yönetim, Intune ve diğer bulut hizmetlerini kullanarak mevcut şirket içi Configuration Manager yatırımını bulutla Microsoft 365 birleştirir. Farklı iş yükleri için yönetim yetkilisi Olarak Yapılandırma Yöneticisi mi yoksa Intune mu olduğunu seçersiniz. 

Birlikte yönetim, Koşullu Erişim ve cihaz uyumluluğunu zorlama da dahil olmak üzere Intune tabanlı bulut özelliklerini kullanır. Bazı görevleri şirket içinde saklayırken, bulutta başka görevleri de çalıştırabilirsiniz.

Daha fazla bilgi için, bu [birlikte yönetime genel bakış bilgilerine bakın](/mem/configmgr/comanage/overview).

## <a name="endpoint-analytics"></a>Endpoint Analytics

Uç nokta analizi, kullanıcı deneyimine ilişkin içgörüler sağlayarak kullanıcı verimliliğini artırmayı ve BT destek maliyetlerini düşürmeyi amaçlar. İçgörüler, BT'nin proaktif destekle son kullanıcı deneyimini iyileştirmesini ve yapılandırma değişikliklerinin kullanıcı etkisini değerlendirerek kullanıcı deneyimindeki gerilemeleri tespit etmesini sağlar.

Daha fazla bilgi için bkz. [Endpoint Analytics'e genel bakış](/mem/analytics/overview)

## <a name="windows-autopilot"></a>AutoPilot Windows'i çalıştırın

Windows AutoPilot sıfır dokunuşla, self servis ve Windows platformudur. Yeni cihazları ayarlamak ve önceden yapılandırmak, bu cihazları üretken kullanım için hazır hale getirirken kullanabileceğiniz bir teknoloji koleksiyonu içerir. Cihazları sıfırlamak, yeniden Windows etmek ve kurtarmak için AutoPilot'a da kullanabilirsiniz. 

Windows AutoPilot, altyapısı çok az olan ve altyapısı olmayan cihazları kolay ve basit bir işlemle önceden yapılandırmaya olanak tanır. 

- Kullanıcının bakış açısından bakıldığında, yalnızca birkaç basit işlemle cihazı kullanıma hazır hale getirildi. 
- IT profesyonellerinin bakış açısından bakıldığında, son kullanıcının tek gerekli etkileşimi bir ağa bağlanmak ve bu kullanıcının kimlik bilgilerini doğrulamaktır.

Daha fazla bilgi için Bkz. [AutoPilot'a Windows genel bakış](/windows/deployment/windows-autopilot/windows-autopilot).

## <a name="admin-technical-resources-for-endpoint-management"></a>Uç nokta yönetimi için yönetici teknik kaynakları

- [Mobil cihaz yönetimi yol Microsoft 365](../enterprise/device-management-roadmap-microsoft-365.md)
- [Mobil cihaz yönetimi için farklı cihaz türlerini kaydetme](/mem/intune/enrollment/device-enrollment)
- [Son kullanıcılarınızı yeni kullanıcılarla nasıl eğitebilirsiniz Microsoft Intune](/mem/intune/fundamentals/end-user-educate)
 
## <a name="results-of-step-4"></a>Adım 4'in sonuçları

Mobil cihazları, masaüstü bilgisayarları, sanal makineleri, ekli cihazları ve sunucuları yönetmek için Endpoint Manager özellikleri ve yetenekleri paketini kullanıyorsanız.

## <a name="next-step"></a>Sonraki adım

[![5. Adım: Uzaktan çalışan üretkenlik uygulamalarını ve hizmetlerini dağıtın.](../media/empower-people-to-work-remotely/remote-workers-step-grid-5.png)](empower-people-to-work-remotely-teams-productivity-apps.md)

Karma [çalışanlarınızı eğitim ve](empower-people-to-work-remotely-teams-productivity-apps.md) eğitim gibi üretkenlik uygulamalarını Microsoft 365 için 5. Adım Microsoft Teams.