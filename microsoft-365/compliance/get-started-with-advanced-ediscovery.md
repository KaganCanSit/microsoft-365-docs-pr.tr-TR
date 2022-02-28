---
title: Microsoft 365'Advanced eDiscovery ayarlama
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-aed
- m365initiative-compliance
- m365solution-scenario
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Bu makalede, davaları oluşturmaya ve yönetmeye Advanced eDiscovery için e-Advanced eDiscovery ayar tarihi açıklanmıştır. Ayrıca gerekli Microsoft abonelikleri ve lisansları da açıklarıdır. Birkaç hızlı adımı tamamlandıktan sonra, Advanced eDiscovery araç kullanıma hazırdır.
ms.openlocfilehash: cf2d7c6bc770dd6125777c895771b3b61c8ee593
ms.sourcegitcommit: ab5368888876d8796da7640553fc8426d040f470
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/04/2021
ms.locfileid: "62990603"
---
# <a name="set-up-microsoft-365-advanced-ediscovery"></a>Ayarlama Microsoft 365 Advanced eDiscovery

Advanced eDiscovery'Microsoft 365 şirket içi ve dış araştırmalarında yanıt veren verileri korumak, toplamak, gözden geçirmek, çözümlemek ve dışarı aktarmaya yönelik  uç-uç iş akışı sağlar. Advanced eDiscovery'i dağıtmak için hiçbir şey gerekli değildir, ancak bazı önkoşul görevleri vardır ve bu görevler kuruluş, araştırmalarınızı yönetmek üzere bir Advanced eDiscovery başlamadan önce bir IT yöneticisinin ve eBulma yöneticisinin tamamlaması gerekir.

Bu makalede, kaynak kodlar için gereken aşağıdaki Advanced eDiscovery.

![E-Advanced eDiscovery.](../media/set-up-advanced-ediscovery.png)

Bu, postalara erişmek ve vakalara koruyucular eklemek Advanced eDiscovery lisanslamanın gerekli olmasını sağlamayı ve vakalara erişmek ve vakaları yönetecek şekilde yasal ve soruşturma takımınıza izinler atamayı içerir.

## <a name="step-1-verify-and-assign-appropriate-licenses"></a>1. Adım: Uygun lisansları doğrulama ve atama

Lisanslama Advanced eDiscovery kuruluş aboneliği ve kullanıcı başına lisans gerektirir. Lisanslama gereksinimlerinin listesi için, Advanced eDiscovery [ve lisanslama'ya bakın](overview-ediscovery-20.md#subscriptions-and-licensing).

## <a name="step-2-assign-ediscovery-permissions"></a>2. Adım: eBulma izinleri atama

Kullanıcıya Advanced eDiscovery veya bir davanın üyesi olarak Advanced eDiscovery için, kullanıcıya uygun izinler atanabilir. Özel olarak, ilgili grupta bir kullanıcının eBulma Yöneticisi rol grubuna üye olarak Microsoft 365 uyumluluk merkezi. Bu rol grubunun üyeleri olay oluşturabilir ve Advanced eDiscovery yönetebilir. Bu ekip üyeleri ekleyemez ve kaldırabilir, koruyucuları ve içerik konumlarını yerinde tutabilir, yasal tutma bildirimlerini yönetebilir, bir durumla ilişkilendirilmiş aramaları oluşturabilir ve düzenleyebilir, gözden geçirme kümesine arama sonuçları ekleyebilir, gözden geçirme kümesinde verileri çözümleyemez ve bir Advanced eDiscovery durumundan dışarı aktararak indirebilir.

eBulma Yöneticisi rol grubuna kullanıcı eklemek için aşağıdaki adımları tamamlayın:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">Microsoft 365 uyumluluk merkezi'a</a> gidin ve kendi Microsoft 365 yönetici hesabının kimlik bilgilerini kullanarak oturum açın.

2. İzinler **sayfasında** eBulma **Yöneticisi rol grubunu** seçin.

3. eBulma Yöneticisi uç sayfasında, eBulma **Yöneticisi bölümünün** yanında **Düzenle'ye** tıklayın.

4. Rol grubunu **düzenle sihirbazının eBulma Yöneticisi** Seç sayfasında, **eBulma Yöneticisi Seç'e tıklayın**.

5. **Ekle'ye** tıklayın ve rol grubuna eklemek istediğiniz tüm kullanıcıların onay kutusunu seçin.

6. Seçili **kullanıcıları eklemek** için Ekle'ye tıklayın ve sonra da Bitti'ye **tıklayın**.

7. Kullanıcıları **rol** grubuna eklemek için Kaydet'e tıklayın ve ardından adımı tamamlamak **için Kapat'a** tıklayın.

### <a name="more-information-about-the-ediscovery-manager-role-group"></a>eBulma Yöneticisi rol grubu hakkında daha fazla bilgi

eBulma Yöneticisi rol grubunda iki alt grup vardır. Bu alt gruplar arasındaki fark, kapsamı temel almaktadır.

- **eBulma Yöneticisi**: Oluşturdukları veya üyesi Advanced eDiscovery durumlarını görüntüp yönetebilir. Başka bir eBulma Yöneticisi bir vaka oluşturur, ancak bu vakanın üyesi olarak ikinci bir eBulma Yöneticisi'ni ekleyene kadar ikinci eBulma Yöneticisi, uyumluluk merkezinde Advanced eDiscovery sayfasında vakayı görüntüde veya açılamaz. Genel olarak, organizasyonlu çoğu kişi eBulma Yöneticisi alt grubunu eklenebilir.

- **eBulma Yöneticisi**: Bir eBulma Yöneticisi'nin gerçekleştirebilir tüm olay yönetimi görevlerini gerçekleştirebilir. Buna ek olarak, eBulma Yöneticisi şunları da olabilir:

  - Dosya sayfasında listelenen tüm vakaları Advanced eDiscovery.
  
  - Kendilerini davanın üyesi olarak ekledikten sonra kuruluşta herhangi bir vakayı yönetin.

  - Kuruluşta herhangi bir vaka için vaka verilerine erişin ve verileri dışarı aktarın.

  Geniş erişim kapsamı nedeniyle, kuruluşun yalnızca birkaç yöneticisi eBulma Yöneticileri alt grubunun üyesi olması gerekir.

eBulma izinleri hakkında daha fazla bilgi ve eBulma Yöneticisi rol grubuna atanan her rolün açıklaması için bkz. [eBulma izinleri atama](assign-ediscovery-permissions.md).

## <a name="step-3-configure-global-settings-for-advanced-ediscovery"></a>3. Adım: Posta için genel Advanced eDiscovery

Organizasyon durumdaki kişilerin vakaları oluşturmaya ve kullanmaya başlamasına başlamadan önce tamamlamanız gereken son adım, kuruluşun tüm vakaları için geçerli olan genel ayarları yapılandırmaktır. Şu anda tek genel ayar avukat-istemci ayrıcalık algılaması *özelliğidir* (gelecekte daha fazla genel ayar kullanılabilir). Bu ayar, inceleme kümesinde verileri analiz etmenize olanak sağlayan bir avukatlık ayrıcalık modelinin çalışmasına olanak sağlar. Model, belgenin doğada yasal olan içerik ekleme olasılığını belirlemek için makine öğrenimi kullanır. Ayrıca bir belgede avukat olarak en az bir katılımcının olup olmadığını belirlemek için belgelerin katılımcılarını bir avukat listesiyle (modeli ayarlarken gönderdiğiniz belgeler) karşılaştırıldığında.

Avukatlık ayrıcalık algılama modelini ayarlama ve kullanma hakkında daha fazla bilgi için bkz. Advanced eDiscovery'te avukatlık [ayrıcalık algılamayı ayarlama](attorney-privilege-detection.md).

> [!NOTE]
> Bu, istediğiniz zaman gerçekleştirebilirsiniz ve isteğe bağlı bir adımdır. Avukat-istemci ayrıcalık algılama modelinin uygulanmaması, farklı durumlar oluşturmasını ve bu Advanced eDiscovery engellemez.

## <a name="next-steps"></a>Sonraki adımlar

Dosya ve Advanced eDiscovery, vakayı oluşturmak [için hazır oluruz](create-and-manage-advanced-ediscoveryv2-case.md).