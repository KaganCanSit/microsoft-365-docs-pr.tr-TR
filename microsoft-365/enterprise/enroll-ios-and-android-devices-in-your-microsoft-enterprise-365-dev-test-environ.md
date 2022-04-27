---
title: Kurumsal test ortamınız için iOS/iPadOS ve Android cihazlarını Microsoft 365 kaydetme
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/19/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom: Ent_TLGs
ms.assetid: 49c7758a-1c01-4153-9b63-5eae3f6305ce
description: Cihazları Microsoft 365 test ortamınıza kaydetmek ve uzaktan yönetmek için bu Test Laboratuvarı Kılavuzu'nu kullanın.
ms.openlocfilehash: 5cefabf6b995754f6febe117776ad2de97443df0
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092943"
---
# <a name="enroll-ios-and-android-devices-in-your-microsoft-365-for-enterprise-test-environment"></a>Kurumsal test ortamınız için iOS ve Android cihazları Microsoft 365 kaydetme

*Bu Test Laboratuvarı Kılavuzu yalnızca kurumsal test ortamları için Microsoft 365 için kullanılabilir.*

Bu makalede, kurumsal test ortamı için Microsoft 365 iOS/iPadOS ve Android cihazlar için temel mobil cihaz yönetimi özelliklerini kaydetme ve test etme işlemleri açıklanmaktadır.

iOS/iPadOS ve Android cihazlarını test ortamınıza kaydetmek üç aşamayı içerir:
- [1. Aşama: Kurumsal test ortamı için Microsoft 365 oluşturma](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [2. Aşama: iOS/iPadOS ve Android cihazlarınızı kaydetme](#phase-2-enroll-your-ios-and-android-devices)
- [3. Aşama: iOS/iPadOS ve Android cihazlarınızı uzaktan yönetme](#phase-3-manage-your-ios-and-android-devices-remotely)

![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınındaki Microsoft 365 tüm makalelere yönelik görsel bir harita için [kurumsal Test Laboratuvarı Kılavuzu Yığını için Microsoft 365](../downloads/Microsoft365EnterpriseTLGStack.pdf) bölümüne gidin.

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>1. Aşama: Kurumsal test ortamı için Microsoft 365 oluşturma

iOS/iPadOS ve Android cihazları minimum gereksinimlerle basit bir şekilde kaydetmek istiyorsanız [Basit temel yapılandırma](lightweight-base-configuration-microsoft-365-enterprise.md) yönergelerini izleyin.
  
iOS/iPadOS ve Android cihazlarını sanal bir kuruluşa kaydetmek istiyorsanız Doğrudan [kimlik doğrulamasındaki](pass-through-auth-m365-ent-test-environment.md) yönergeleri izleyin.
  
> [!NOTE]
> Otomatik lisanslama ve grup üyeliğinin test edilmesi için İnternet'e bağlı bir sanal intranet ve bir Active Directory Domain Services (AD DS) ormanı için dizin eşitlemesi içeren sanal kurumsal test ortamı gerekmez. Burada, otomatik lisanslama ve grup üyeliğini test edebilmeniz ve tipik bir kuruluşu temsil eden bir ortamda denemeler yapabileceğiniz bir seçenek olarak sağlanır.

## <a name="phase-2-enroll-your-ios-and-android-devices"></a>2. Aşama: iOS ve Android cihazlarınızı kaydetme

Cihazlarınızı yönetmek için bir mobil cihaz yönetimi (MDM) çözümü kullanmayı düşünüyorsanız Microsoft Intune kullanabilirsiniz. Intune dahil olmak üzere herhangi bir MDM sağlayıcısıyla çalışırken cihazlar "kaydedilir". Kaydolduğunda, yapılandırdığınız özellikleri ve ayarları alır. 

Intune'da iOS/iPadOS ve Android cihazlarınızı kaydetmenin birkaç yolu vardır. Kuruluşunuz için en uygun kayıt seçeneğini belirleyebilirsiniz. Daha fazla bilgi ve rehberlik için aşağıdaki makalelere bakın:

- [Dağıtım kılavuzu: iOS ve iPadOS cihazlarını Microsoft Intune kaydetme](/mem/intune/fundamentals/deployment-guide-enrollment-ios-ipados)
- [Dağıtım kılavuzu: Android cihazlarını Microsoft Intune kaydetme](/mem/intune/fundamentals/deployment-guide-enrollment-android)

Cihaz yönetimi için Intune kullanmaya hazırsanız ve bazı yönergeler istiyorsanız, aşağıdaki bilgiler yardımcı olabilir:

- [Cihaz yönetimine genel bakış](/mem/intune/fundamentals/what-is-device-management)
- [Öğretici: Microsoft Endpoint Manager'da izlenecek yol Intune](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager)
- [Dağıtım kılavuzu: Kurulum veya Microsoft Intune taşıma](/mem/intune/fundamentals/deployment-guide-intune-setup)

## <a name="phase-3-manage-your-ios-and-android-devices-remotely"></a>3. Aşama: iOS ve Android cihazlarınızı uzaktan yönetme

Microsoft Intune uzaktan kilitleme ve geçiş kodu sıfırlama özelliği sağlar. Birisi cihazını kaybederse cihazı uzaktan kilitleyebilirsiniz. Birisi geçiş kodunu unutursa, uzaktan sıfırlayabilirsiniz.

- Bir iOS/iPadOS veya Android cihazı uzaktan kilitlemek için bkz. [cihazları Intune ile uzaktan kilitleme](/mem/intune/remote-actions/device-remote-lock).
- Geçiş kodunu uzaktan sıfırlamak için bkz. [Intune cihaz geçiş kodunu sıfırlama veya kaldırma](/mem/intune/remote-actions/device-passcode-reset).

Uzaktan çalıştırabileceğiniz ek görevler için [bkz. kullanılabilir cihaz eylemleri](/mem/intune/remote-actions/device-management#available-device-actions).
    
## <a name="next-step"></a>Sonraki adım

Test ortamınızdaki ek [mobil cihaz yönetimi](m365-enterprise-test-lab-guides.md#mobile-device-management) özelliklerini ve özelliklerini keşfedin.

## <a name="see-also"></a>Ayrıca Bkz

[Kurumsal Test Laboratuvarı Kılavuzları için Microsoft 365](m365-enterprise-test-lab-guides.md)
  
[Kurumsal test ortamınız için Microsoft 365 cihaz uyumluluk ilkeleri](mam-policies-for-your-microsoft-365-enterprise-dev-test-environment.md)
  
[Microsoft 365 Kurumsal’a genel bakış](microsoft-365-overview.md)
