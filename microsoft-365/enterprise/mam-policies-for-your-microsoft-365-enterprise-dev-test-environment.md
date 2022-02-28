---
title: Kurumsal test ortamınız için Microsoft 365 uyumluluk ilkeleri
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
ms.assetid: 1aa9639b-2862-49c4-bc33-1586dda636b8
description: Kurumsal test ortamı için test ortamınıza Intune cihaz uyumluluk ilkelerini eklemek Microsoft 365 Test Laboratuvarı Kılavuzunu kullanın.
ms.openlocfilehash: ec73211a21e9e064b729b93d9e88b7c5c69b21fe
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977676"
---
# <a name="device-compliance-policies-for-your-microsoft-365-for-enterprise-test-environment"></a>Kurumsal test ortamınız için Microsoft 365 uyumluluk ilkeleri

*Bu Test Laboratuvarı Kılavuzu yalnızca kurumsal test Microsoft 365 test ortamları için kullanılabilir.*

Bu makalede, Kurumsal test ortamı için Mobil Cihaz Yönetiminize ve Windows 10 için Intune cihaz Kurumlar için Microsoft 365 Uygulamaları ilkesi Microsoft 365 ilkenin nasıl ekli olduğu açıklanmıştır.

Intune cihaz uyumluluk ilkesi ekleme iki aşamadan sonrasını içerir:
- [Aşama 1: Kurumsal test Microsoft 365 yapınızı oluşturma](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Aşama 2: Mobil cihazlarınız için cihaz Windows 10 ilkesi oluşturma](#phase-2-create-a-device-compliance-policy-for-windows-10-devices)

![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınına Microsoft 365 görsel bir harita için Kurumsal Test Laboratuvarı Kılavuzu Yığını [için Microsoft 365'e gidin](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Aşama 1: Kurumsal test Microsoft 365 yapınızı oluşturma

MAM ilkelerini en düşük gereksinimleri olan basit bir yolla yapılandırmak için Hafif temel yapılandırma [yönergelerini izleyin](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Sanal bir kuruluşta MAM ilkelerini yapılandırmak için, Geçişli kimlik [doğrulama'daki yönergeleri izleyin](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Otomatik lisanslama ve grup üyeliğini test etmek, Active Directory Etki Alanı Hizmetleri (AD DS) ormanı için İnternet ve dizin eşitlemeye bağlı sanal bir intranet içeren sanal kurumsal test ortamını gerektirmez. Burada, otomatik lisanslama ve grup üyeliğini test etmek ve normal bir kuruluşu temsil eden bir ortamda bu üyelikle denemeler yapmak için bir seçenek olarak sağlanmıştır.
>  

## <a name="phase-2-create-a-device-compliance-policy-for-windows-10-devices"></a>Aşama 2: Mobil cihazlarınız için cihaz Windows 10 ilkesi oluşturma

Bu aşamada, tüm cihazlarınız için bir cihaz Windows 10 oluştursunuz. Bu aşama Microsoft Intune ve [Microsoft Endpoint Manager yönetim](https://go.microsoft.com/fwlink/?linkid=2109431) merkezini kullanarak grup ekler ve uyumluluk ilkesi oluşturabilir.

1. Genel [Microsoft 365 yönetim merkezi gidin,](https://admin.microsoft.com) genel yönetici hesabınızla Microsoft 365 test laboratuvarı aboneliğinde oturum açın ve genel <a href="https://go.microsoft.com/fwlink/?linkid=2109431" target="_blank">Endpoint Manager seçin</a>.

    Cihaz yönetimini henüz **etkinleştirmediyseniz benzer bir ileti** gösteriliyorsa, MDM yetkilisi olarak Intune'ı seçin. Belirli adımlar için bkz. [Mobil cihaz yönetim yetkilisini ayarlama](/mem/intune/fundamentals/mdm-authority-set).

    Yönetim Endpoint Manager yönetim merkezi, cihaz yönetimi ve uygulama yönetimine odaklanır. Bu yönetim merkezi turu için bkz. [Öğretici: Gezinti Merkezi'nde Adım Adım Microsoft Endpoint Manager](/mem/intune/fundamentals/tutorial-walkthrough-endpoint-manager).

2. **Gruplar'a**, atanan üyelik **Microsoft 365** **yönetilen cihaz** kullanıcıları **Windows 10** yönetilen kullanıcı adı ve Güvenlik **grubu** ekleyin. Sonraki adımlarda, uyumluluk ilkenizi bu gruba atayacağız. 

    Belirli adımlar ve güvenlik grupları hakkında bilgi **Microsoft 365** **için bkz**. [Kullanıcıları ve cihazları düzenlemek için grup ekleme](/mem/intune/fundamentals/groups-add).

3. **Cihazlar'da** bir uyumluluk Windows 10 oluşturun. Bu ilkeyi, oluşturduğunuz **Windows 10 Yönetilen Cihaz Kullanıcıları** grubuna attayabilirsiniz.

    İlkenize göre, basit parolaları engelleyebilir, güvenlik duvarına gerek engelleyebilir, Microsoft Defender Kötü Amaçlı Yazılımdan Koruma hizmetinin çalışıyor olması ve daha fazlasını kullanabilirsiniz. Uyumluluk ilkesi normalde her cihazın sahip olması gereken temel ayarları veya minimum minimum ayarı içerir.

    Belirli adımlar ve yapılandırabilirsiniz kullanılabilir uyumluluk ayarları hakkında bilgi için bkz. Yönetmek istediğiniz cihazlara yönelik kurallar ayarlamak [için uyumluluk ilkelerini kullanma](/mem/intune/protect/device-compliance-get-started).

Tamamlandığında, Yönetilen Cihaz Kullanıcıları grubunda üyeleri test etmek için cihaz **Windows 10 ilkeye sahip olursunuz**.
  
## <a name="next-step"></a>Sonraki adım

Test [ortamınıza ek mobil](m365-enterprise-test-lab-guides.md#mobile-device-management) cihaz yönetim özelliklerini ve özelliklerini keşfedin.

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 Test Laboratuvarı Kılavuzları için kılavuz.](m365-enterprise-test-lab-guides.md)
  
[Kurumsal test ortamına iOS ve Android Microsoft 365 cihazları kaydetme](enroll-ios-and-android-devices-in-your-microsoft-enterprise-365-dev-test-environ.md)
  
[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Enterprise Mobility + Security (EMS)](https://www.microsoft.com/cloud-platform/enterprise-mobility-security)
