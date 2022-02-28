---
title: Kurumsal test ortamı için iOS/iPadOS ve Android Microsoft 365 ortamınıza kaydetme
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/19/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: Test ortamınıza cihazları kaydetmek ve uzaktan yönetmek için Microsoft 365 Test Laboratuvarı Kılavuzunu kullanın.
ms.openlocfilehash: 7610348febcc8c2054c50d7f7a6f1433e9b62306
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985148"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-for-enterprise-test-environment"></a>Kurumsal test ortamına iOS ve Android Microsoft 365 cihazları kaydetme

*Bu Test Laboratuvarı Kılavuzu yalnızca kurumsal test Microsoft 365 test ortamları için kullanılabilir.*

Bu makalede, kurumsal test ortamınıza iOS/iPadOS ve Android cihazları için temel mobil cihaz yönetimi özelliklerini Microsoft 365 ve test edebilirsiniz.

Test ortamınıza iOS/iPadOS ve Android cihazlarını kaydetmek üç aşama içerir:
- [Aşama 1: Kurumsal test Microsoft 365 yapınızı oluşturma](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Aşama 2: iOS/iPadOS ve Android cihazlarınızı kaydetme](#phase-2-enroll-your-ios-and-android-devices)
- [Aşama 3: iOS/iPadOS ve Android cihazlarınızı uzaktan yönetme](#phase-3-manage-your-ios-and-android-devices-remotely)

![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınına Microsoft 365 görsel bir harita için Kurumsal Test Laboratuvarı Kılavuzu Yığını [için Microsoft 365'e gidin](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Aşama 1: Kurumsal test Microsoft 365 yapınızı oluşturma

iOS/iPadOS ve Android cihazlarını minimum gereksinimlerle hafif bir şekilde kaydetmek için Hafif taban yapılandırma [yönergelerini izleyin](lightweight-base-configuration-microsoft-365-enterprise.md).
  
iOS/iPadOS ve Android cihazlarını sanal bir kuruluşa kaydetmek için, Geçişli kimlik [doğrulama'daki yönergeleri izleyin](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Otomatik lisanslama ve grup üyeliğini test etmek, Active Directory Etki Alanı Hizmetleri (AD DS) ormanı için İnternet ve dizin eşitlemeye bağlı sanal bir intranet içeren sanal kurumsal test ortamını gerektirmez. Burada, otomatik lisanslama ve grup üyeliğini test etmek ve normal bir kuruluşu temsil eden bir ortamda bu üyelikle denemeler yapmak için bir seçenek olarak sağlanmıştır.

## <a name="phase-2-enroll-your-ios-and-android-devices"></a>Aşama 2: iOS ve Android cihazlarınızı kaydetme

Cihazlarınızı yönetmek için bir mobil cihaz yönetimi (MDM) çözümü kullanmayı düşünüyorsanız, cihaz yönetimi ve Microsoft Intune. Intune dahil herhangi bir MDM sağlayıcısıyla çalışırken cihazlar "kayıtlı" olur. Kaydolıldığında, yapılandırılan özellikleri ve ayarları alırlar. 

Intune'da, iOS/iPadOS ve Android cihazlarınızı kaydetmenin birkaç yolu vardır. Organizasyonunıza en uygun kayıt seçeneğini seçebilirsiniz. Daha fazla bilgi ve rehberlik için aşağıdaki makalelere bakın:

- [Dağıtım kılavuzu: Microsoft Intune'de iOS ve iPadOS cihazlarını Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-ios-ipados)
- [Dağıtım kılavuzu: Android cihazlarını Microsoft Intune](/mem/intune/fundamentals/deployment-guide-enrollment-android)

Intune'ı cihaz yönetimi için kullanmaya hazırsanız ve biraz yol göstermeyi istiyorsanız, aşağıdaki bilgiler yardımcı olabilir:

- [Cihaz yönetimine genel bakış](/mem/intune/fundamentals/what-is-device-management)
- [Öğretici: Microsoft Endpoint Manager'te Adım Adım Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager)
- [Dağıtım kılavuzu: Kurulum veya Dağıtım'a Microsoft Intune](/mem/intune/fundamentals/deployment-guide-intune-setup)

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>Aşama 3: iOS ve Android cihazlarınızı uzaktan yönetme

Microsoft Intune uzaktan kilit ve geçiş kodu sıfırlama özelliği sağlar. Cihaz biri tarafından kaybedilirse, cihazı uzaktan kilitleyebilirsiniz. Birisi geçiş kodunu unutursa, kodu uzaktan sıfırlayabilirsiniz.

- iOS/iPadOS veya Android cihazı uzaktan kilitlemek için bkz. [Intune ile cihazları uzaktan kilitleme](/mem/intune/remote-actions/device-remote-lock).
- Geçiş kodunu uzaktan sıfırlamak için bkz. [Intune'da cihaz geçiş kodunu sıfırlama veya kaldırma](/mem/intune/remote-actions/device-passcode-reset).

Uzaktan çalıştırabilirsiniz diğer görevler için kullanılabilir cihaz [eylemlerine bakın](/mem/intune/remote-actions/device-management#available-device-actions).
    
## <a name="next-step"></a>Sonraki adım

Test [ortamınıza ek mobil](m365-enterprise-test-lab-guides.md#mobile-device-management) cihaz yönetim özelliklerini ve özelliklerini keşfedin.

## <a name="see-also"></a>Ayrıca Bkz

[Microsoft 365 Test Laboratuvarı Kılavuzları için kılavuzlar](m365-enterprise-test-lab-guides.md)
  
[Kurumsal test ortamınız için Microsoft 365 uyumluluk ilkeleri](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)
