---
title: Microsoft Yönetilen Masaüstü ve ITIL
description: ITIL aşamalarını Microsoft Yönetilen Masaüstü bilgileri ve makaleleriyle uyumlu yapıyor
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler, ITISM
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.openlocfilehash: b9984e308b6681512297e484817f95206283385e
ms.sourcegitcommit: a6651b841f111ea2776cab88bf2c80f805fa8e09
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2022
ms.locfileid: "63027291"
---
# <a name="microsoft-managed-desktop-and-itil"></a>Microsoft Yönetilen Masaüstü ve ITIL

Birçok kuruluş, [ITIL](https://www.axelos.com/best-practice-solutions/itil) gibi resmi bir IT Hizmet Modeli (ITSM) boyunca IT hizmetlerini yapılandırılmış olarak değerli bulur. 

Microsoft Yönetilen Masaüstü, bu tür resmi ITSM modellerinin birçok önemli özelliğine uyumlu hale getirildi. Bu makale, örnek olarak ITIL'in kullanımı, uygun olduğunda ortak ITIL aşamaları ve süreçleri ile eşdeğer Microsoft Yönetilen Masaüstü özellikleri arasındaki bağlantıları görmenizi sağlar. Bu bilgiler yalnızca, kuruluşun Microsoft Yönetilen Masaüstü bölümü için geçerlidir.

ITIL ve aşamaları ve süreci hakkında daha kapsamlı bilgi için, onların belgelerine [bakın](https://www.axelos.com/best-practice-solutions/itil).


## <a name="service-design"></a>Hizmet tasarımı

Bu tablo, önemli ITIL aşamalarını ve işlemlerini Microsoft Yönetilen Masaüstü özellikleriyle ve ayrıntılar için belgelerimizin bağlantılarını içerir:



|ITIL işlemi |Açıklama  |Belgeler |
|---------|---------|---------|
|Hizmet düzeyi yönetimi     | Yönetici destek istekleri ve olayları için yanıt süreleri tanımlanmıştır.  |  [Microsoft Yönetilen Masaüstü için yönetici desteği](working-with-managed-desktop/admin-support.md)  |
|Hizmet kataloğu yönetimi     | Hizmet bileşenlerinin ayrıntılarıyla ilgili hizmet açıklaması, geçerli ve ilgili tüm müşterilerin hizmetinin durumuna uygun olarak tutulur.<br><br>Hizmeti çalıştırmak için nelerin gerekli olduğunu anlamak için ayrıntılı önkullar.  | - [Microsoft Yönetilen Masaüstü hizmet açıklaması](service-description/index.md)<br><br>- [Microsoft Yönetilen Masaüstü'ne kayıt için hazır olun](get-ready/index.md)  |
|Bilgi güvenliği yönetimi     | Hizmetin bilgi güvenliği de dahil olmak üzere güvenlik bilgileri.<br><br> Güvenlikle ilgili ilkeler ve cihazların nasıl yapılandırıldıklarına ilişkin diğer bilgiler.   | - [Microsoft Yönetilen Masaüstü'ne Güvenlik](service-description/security.md)<br><br>- [Cihaz yapılandırması](service-description/device-policies.md)  |
|Kullanılabilirlik yönetimi     |  Microsoft Yönetilen Masaüstü, hizmetin kullanılabilir olduğundan emin olmak için organizasyonla olan sorumluluğu dengeler.<br><br>Hizmet veya kullanılabilirlik sorunları varsa, yöneticilerin ve kullanıcıların ilgili dedelere yönlendirmeleri vardır. | - [Microsoft Yönetilen Masaüstü işlemleri ve izleme](service-description/operations-and-monitoring.md)<br><br>- [Microsoft Yönetilen Masaüstü için yönetici desteği](working-with-managed-desktop/admin-support.md)<br>- [Kullanıcılar için yardım alma](working-with-managed-desktop/end-user-support.md)  |



## <a name="service-transition"></a>Hizmet geçişi


|ITIL işlemi |Açıklama  |Belgeler |
|---------|---------|---------|
|Değişiklik yönetimi     | Sorumluluk tanımlanmış bakiye, süreç genel görünümü ve değişiklik yönetimiyle ilgili türler kullanılabilir.  | [Microsoft Yönetilen Masaüstü işlemleri ve izleme](service-description/operations-and-monitoring.md#change-management) |
|Sürüm ve dağıtım yönetimi     |  Microsoft Yönetilen Masaüstü, hizmete kayıtlı cihazların güncelleştirmelerini yönetir.  | [Microsoft Yönetilen Masaüstü'de güncelleştirmeler nasıl yönetilir?](service-description/updates.md)        |
|Hizmet varlığı ve yapılandırma yönetimi     | Kuruluşun Microsoft Yönetilen Masaüstü dağıtımıyla ilgili bilgilere, IT yönetim portalından erişebilirsiniz.  | [Microsoft Yönetilen Masaüstü için yönetici desteği](working-with-managed-desktop/admin-support.md) |
|Bilgi yönetimi     | Bu sitede, Microsoft Yönetilen Masaüstü hizmetiyle ilgili bilgiler güncel tutulur.   | [Microsoft Yönetilen Masaüstü belgeleri için değişiklik geçmişi](change-history-managed-desktop.md)        |



## <a name="service-operation"></a>Hizmet işlemi


|ITIL işlemi |Açıklama  |Belgeler  |
|---------|---------|---------|
|Etkinlik yönetimi     |  Cihazların izlenmesiyle ilgili ayrıntılar sağlanır.<br><br>Microsoft Yönetilen Masaüstü hizmeti için standart işletim yordamları ayrıntılı olarak ve şekildedir. |  - [Microsoft Yönetilen Masaüstü'ne Güvenlik](service-description/security.md)<br>- [Microsoft Yönetilen Masaüstü işlemleri ve izleme](service-description/operations-and-monitoring.md)       |
|Olay yönetimi  | Microsoft Yönetilen Masaüstü tanımlı önem düzeyi tanımları başına olayları araştıracak ve bu olaylara karşı harekete geçecek.  |  [Destek isteği önem derecesi tanımları](working-with-managed-desktop/admin-support.md#support-request-severity-definitions)       |
|Ödeme yönetimi isteği     |  Microsoft Yönetilen Masaüstü hizmetiyle ilgili bilgi istekleri ve değişiklik istekleri işlemi tanımlanır.         |[Microsoft Yönetilen Masaüstü için yönetici desteği](working-with-managed-desktop/admin-support.md)         |
|Sorun yönetimi     | Hizmetle ilgili tüm sorunlar şu anda yerel hesap ekibinize yönlendirildi. | Geliştirme aşamasındaki belgeler |
|Erişim yönetimi     | işlevselliğin ayrıntılı olduğundan emin olmak için müşteriyle ilgili yönetim bileşenlerine ve sorumluluklarına erişin.  | [Kimlik ve erişim yönetimi](service-description/security.md#identity-and-access-management)        |
