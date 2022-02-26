---
title: Betik Office ayarlarını yönetme
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
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
- AdminTemplateSet
- admindeeplinkMAC
search.appverid: MET150
description: Tüm Betikler ayarlarını Office yönetmeyi öğrenin.
ms.openlocfilehash: f03ee34e0ff41c3eb082beca79127cd609496564
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973759"
---
# <a name="manage-office-scripts-settings"></a>Betik Office ayarlarını yönetme

[Office Betikleri](/office/dev/scripts), kullanıcıların çalışma sayfalarındaki betikleri kaydederek, düzenleyerek ve çalıştırarak görevleri otomatik Web üzerinde Excel. Office Betikler alanlarla Power Automate ve kullanıcılar da Excel Online (İş) bağlayıcısı kullanarak çalışma kitaplarında betikler çalıştırmaya çalışır. Microsoft 365, komut dosyaları Office Betik ayarlarını Microsoft 365 yönetim merkezi.

## <a name="before-you-begin"></a>Başlamadan önce

- Tüm Betik Office yönetmek için Genel yönetici olmak gerekir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../add-users/about-admin-roles.md).

- Aşağıdaki planlardan biri gibi, organizasyonlu kullanıcıların Office masaüstü uygulamalarına erişimi olan bir Microsoft 365 veya Office 365 ticari veya EDU planı için geçerli bir lisansa sahip olduğundan emin olun:

- Microsoft 365 Business Standard
- Microsoft 365 Kurumsal Uygulamaları
- Microsoft 365 Kurumsal Uygulamaları
- Office 365 E3
- Office 365 E5
- Office 365 A3
- Office 365 A5

## <a name="manage-availability-of-office-scripts-and-sharing-of-scripts"></a>Betiklerin kullanılabilirliğini Office Betikleri ve betikleri paylaşma

1. Kuruluş Microsoft 365 yönetim merkezi, Kuruluş ayarları **Ayarlar** \> **sekmesine** \> gidin.**[](https://go.microsoft.com/fwlink/p/?linkid=2053743)**

2. **Betikleri Office seçin**.

3. Office Betikler özelliği varsayılan olarak açıktır ve bu özellik ve betikleri tüm kuruluşta herkes erişebilir ve kullanabilir. Bu Betikleri Office için, Bu komut dosyalarında kullanıcıların görevlerini otomatik hale **Web üzerinde Excel temizleyin.**

4. Office Betikleri'Office daha önce kapattıysanız ve bu özelliği yeniden açmak için Kullanıcıların **Web üzerinde Excel'da** görevlerini otomatikleştirmesine izin ver'i seçin ve ardından özelle ilgili kimlerin erişerek kullana bir özellik kullanabileceğini belirtin:

    - Tüm kuruluş kullanıcılarının Komut Dosyalarına erişmesine ve bu Betikleri kullanmasına izin Office, **Herkes** (varsayılan) seçili bırakın.

    - Yalnızca belirli bir Office grubun üyelerinin Komut Betiklerine erişmesine ve bu komut betiklerini kullanmasına izin vermek için, Belirli grup'a tıklayın ve ardından grubun adını veya e-posta diğer adını girerek izin listesine ekleyin. İzin listesine yalnızca bir grup ekleyebilirsiniz ve bu grup aşağıdaki türlerden biri gerekir:
        - Microsoft 365 grubu
        - Dağıtım grubu
        - Güvenlik grubu
        - Posta etkin güvenlik grubu

        Farklı grup türleri hakkında daha fazla bilgi edinmek için bkz. [Grupları karşılaştırma](../create-groups/compare-groups.md).

5. Office Betiklerine erişimi olan kullanıcıların betiklerini kuruluşta başkalarıyla paylaşmalarına olanak vermek için Betiklere erişimi olan kullanıcıların Office betiklerini kuruluşta başkalarıyla paylaşmasına izin ver'i **seçin**. Betikleri kuruluş dışında paylaşmaya izin verilmez.

    > [!NOTE]
    > Daha sonra kuruluşunda betik paylaşımını kapatsanız bile, kullanıcılar daha önce paylaşılan betikleri çalıştırabilecektir.

6. Betiklere erişimi olan kullanıcıları Office Betiklerini paylaşabilir:

    - Betiklerine erişimi olan tüm kullanıcıların Office betiklerini paylaşmasına izin vermek için, **Herkes** 'i (varsayılan) seçili bırakın.

    - Office Betiklerine erişim izni olan belirli bir grubun üyelerine kendi betiklerini paylaşma izni vermek için, Belirli grup'a tıklayın ve ardından grubun adını veya e-posta diğer adını girerek izin listesine ekleyin. İzin listesine yalnızca bir grup ekleyebilirsiniz ve bu grup aşağıdaki türlerden biri gerekir:
        - Microsoft 365 grubu
        - Dağıtım grubu
        - Güvenlik grubu
        - Posta etkin güvenlik grubu

        Farklı grup türleri hakkında daha fazla bilgi edinmek için bkz. [Grupları karşılaştırma](../create-groups/compare-groups.md).

7. Kullanıcıların kendi Betiklerini kendi Office betiklerini kendi akışlarında çalıştırmasına izin Power Automate, Betiklere erişimi olan kullanıcıların Office Betiklerini kendi betikleriyle **birlikte çalıştırmasına izin Power Automate**. Bu, kullanıcıların [Excel Online (İş) Bağlayıcısı'nın Çalıştır betik seçeneğiyle akış adımları](/connectors/excelonlinebusiness) **eklemelerini** sağlar.

    - Betiklere erişim izni olan tüm Office betiklerini akışlarda kullanmasına izin vermek için **, Herkes'i** (varsayılan) seçili bırakın.

    - Betiklerini akışlarda kullanmak üzere yalnızca belirli bir grubun üyelerine izin vermek için Office Betikleri'ne erişim izni vermek için, Belirli grup'a tıklayın ve ardından grubun adını veya e-posta diğer adını girerek izin listesine ekleyin. İzin listesine yalnızca bir grup ekleyebilirsiniz ve bu grup aşağıdaki türlerden biri gerekir:
        - Microsoft 365 grubu
        - Dağıtım grubu
        - Güvenlik grubu
        - Posta etkin güvenlik grubu

        Farklı grup türleri hakkında daha fazla bilgi edinmek için bkz. [Grupları karşılaştırma](../create-groups/compare-groups.md).

    - Büyük Betikleri birlikte kullanma hakkında daha fazla Office için bkz. Power Automate [Betiklerini Office Betikleri Power Automate](/office/dev/scripts/develop/power-automate-integration).

8. **Kaydet**'i seçin.

    Office Betikleri ayarlarında yapılan değişikliklerin etkili olması 48 saate kadar sürebilir.

## <a name="next-steps"></a>Sonraki adımlar

Office Betikleri Power Automate ile birlikte çalışır, çünkü kullanıcılar Office Betiklerini kullanarken, kuruluş verilerinizin korunmasını sağlamak için var olan veri kaybı önleme (DLP) ilkelerinizi gözden geçirmenizi öneririz. Daha fazla bilgi için bkz. [Veri kaybı önleme (DLP) ilkeleri](/power-automate/prevent-data-loss).

## <a name="related-content"></a>İlgili içerik

[Office Betikleri teknik belgeleri](/office/dev/scripts/) (bağlantı sayfası)\
[Excel'Office Betiklere](https://support.microsoft.com/office/9fbe283d-adb8-4f13-a75b-a81c6baf163a) Giriş (makale)\
[Web Office'Excel Betiklerini Paylaşma](https://support.microsoft.com/office/226eddbc-3a44-4540-acfe-fccda3d1122b) (makale)\
[Metinde Betikleri kaydetme Office düzenleme ve Web üzerinde Excel](/office/dev/scripts/tutorials/excel-tutorial) (makale)
