---
title: Microsoft Purview'da eKeşif (Premium) ayarlama
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Bu makalede, servis taleplerini oluşturmaya ve yönetmeye başlayabilmeniz için eBulma (Premium) özelliğinin nasıl ayarlanacağı açıklanır. Ayrıca gerekli Microsoft abonelikleri ve lisanslama işlemleri de açıklanmaktadır. Birkaç hızlı adımı tamamladıktan sonra eBulma (Premium) aracı kullanıma hazır olur.
ms.openlocfilehash: 0b96506c9a7b52b6e4aa1e9d14f1e5d2330fee19
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622865"
---
# <a name="set-up-microsoft-purview-ediscovery-premium"></a>Microsoft Purview eKeşif ayarlama (Premium)

Microsoft Purview eKeşif (Premium), kuruluşunuzun iç ve dış araştırmalarına yanıt veren verileri korumak, toplamak, gözden geçirmek, analiz etmek ve dışarı aktarmak için uçtan uca bir iş akışı sağlar. eKeşif (Premium) dağıtımı için hiçbir şey gerekmez, ancak kuruluşunuzun araştırmalarınızı yönetmek için eKeşif (Premium) olayları oluşturmaya ve kullanmaya başlayabilmesi için önce BIR BT yöneticisinin ve eBulma yöneticisinin tamamlaması gereken bazı önkoşul görevleri vardır.

Bu makalede, eBulma 'yı (Premium) ayarlamak için gereken aşağıdaki adımlar açıklanır.

![eKeşif 'i (Premium) ayarlama adımları.](../media/set-up-advanced-ediscovery.png)

Bu, eBulma'ya (Premium) erişmek ve servis taleplerine koruyucu eklemek için gereken uygun lisanslamanın sağlanmasını ve davalara erişebilmeleri ve bunları yönetebilmeleri için yasal ve araştırma ekibinize izinler atamayı içerir.

## <a name="step-1-verify-and-assign-appropriate-licenses"></a>1. Adım: Uygun lisansları doğrulama ve atama

eKeşif (Premium) için lisanslama için uygun kuruluş aboneliği ve kullanıcı başına lisanslama gerekir. eBulma (Premium) için lisans gereksinimlerinin listesi için bkz. [Abonelikler ve lisanslama](overview-ediscovery-20.md#subscriptions-and-licensing).

## <a name="step-2-assign-ediscovery-permissions"></a>2. Adım: eBulma izinlerini atama

eBulma (Premium) hizmetine erişmek veya eBulma (Premium) olayının üyesi olarak eklemek için kullanıcıya uygun izinlerin atanması gerekir. Özellikle, kullanıcının Microsoft Purview uyumluluk portalı eBulma Yöneticisi rol grubunun bir üyesi olarak eklenmesi gerekir. Bu rol grubunun üyeleri eBulma (Premium) servis taleplerini oluşturabilir ve yönetebilir. Üyeleri ekleyip kaldırabilir, koruyucuları ve içerik konumlarını ayrı tutabilir, yasal saklama bildirimlerini yönetebilir, bir servis talebiyle ilişkili aramalar oluşturup düzenleyebilir, bir inceleme kümesine arama sonuçları ekleyebilir, gözden geçirme kümesindeki verileri analiz edebilir ve eBulma (Premium) servis talebine aktarıp indirebilirler.

Kullanıcıları eBulma Yöneticisi rol grubuna eklemek için aşağıdaki adımları tamamlayın:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">Uyumluluk portalına</a>gidin ve Microsoft 365 kuruluşunuzdaki bir yönetici hesabının kimlik bilgilerini kullanarak oturum açın.

2. **İzinler** sayfasında **eBulma Yöneticisi** rol grubunu seçin.

3. eBulma Yöneticisi açılır sayfasında, **eBulma Yöneticisi** bölümünün yanındaki **Düzenle'ye** tıklayın.

4. Rol grubunu düzenleme sihirbazının **eBulma Yöneticisi seç** sayfasında **eBulma Yöneticisi Seç'e** tıklayın.

5. **Ekle'ye** tıklayın ve rol grubuna eklemek istediğiniz tüm kullanıcılar için onay kutusunu seçin.

6. Seçili kullanıcıları eklemek için **Ekle'ye** tıklayın ve ardından **Bitti'ye** tıklayın.

7. Kullanıcıları rol grubuna eklemek için **Kaydet'e** tıklayın ve ardından adımı tamamlamak için **Kapat'a** tıklayın.

### <a name="more-information-about-the-ediscovery-manager-role-group"></a>eBulma Yöneticisi rol grubu hakkında daha fazla bilgi

eBulma Yöneticisi rol grubunda iki alt grup vardır. Bu alt gruplar arasındaki fark kapsama bağlıdır.

- **eBulma Yöneticisi**: Oluşturdukları veya üyesi oldukları eBulma (Premium) servis taleplerini görüntüleyebilir ve yönetebilir. Başka bir eBulma Yöneticisi bir servis talebi oluşturur ancak bu durumun üyesi olarak ikinci bir eBulma Yöneticisi eklemezse, ikinci eBulma Yöneticisi uyumluluk merkezindeki eBulma (Premium) sayfasında olayı görüntüleyemez veya açamaz. Genel olarak, kuruluşunuzdaki çoğu kişi eBulma Yöneticisi alt grubuna eklenebilir.

- **eBulma Yöneticisi**: eBulma Yöneticisi'nin gerçekleştirebileceği tüm servis talebi yönetim görevlerini gerçekleştirebilir. Ayrıca, eBulma Yöneticisi şunları yapabilir:

  - eBulma (Premium) sayfasında listelenen tüm servis taleplerini görüntüleyin.
  
  - Kendilerini olayın üyesi olarak ekledikten sonra kuruluştaki herhangi bir olayı yönetin.

  - Kuruluştaki her servis talebi için servis talebi verilerine erişin ve verileri dışarı aktarın.

  Geniş erişim kapsamı nedeniyle, bir kuruluşun eBulma Yöneticileri alt grubunun üyesi olan yalnızca birkaç yöneticisi olmalıdır.

eBulma izinleri ve eBulma Yöneticisi rol grubuna atanan her rolün açıklaması hakkında daha fazla bilgi için bkz. [eBulma izinleri atama](assign-ediscovery-permissions.md).

## <a name="step-3-configure-global-settings-for-ediscovery-premium"></a>3. Adım: eBulma için genel ayarları yapılandırma (Premium)

Kuruluşunuzdaki kişiler örnek oluşturmaya ve kullanım örnekleri oluşturmaya başlamadan önce tamamlamanız gereken son adım, kuruluşunuzdaki tüm servis talepleri için geçerli olan genel ayarları yapılandırmaktır. Şu anda tek genel ayar *avukat-istemci ayrıcalık algılamadır* (gelecekte daha fazla genel ayar sağlanacaktır). Bu ayar, bir gözden geçirme kümesindeki verileri analiz ettiğinizde avukat-istemci ayrıcalık modelinin çalışmasını sağlar. Model, bir belgenin doğası gereği yasal içerik içerme olasılığını belirlemek için makine öğrenmesini kullanır. Ayrıca belge katılımcılarını bir avukat listesiyle (modeli ayarlarken gönderdiğiniz) karşılaştırarak belgenin avukat olan en az bir katılımcısı olup olmadığını belirler.

Avukat-istemci ayrıcalık algılama modelini ayarlama ve kullanma hakkında daha fazla bilgi için bkz. [eBulma'da (Premium) avukat-istemci ayrıcalık algılamasını ayarlama](attorney-privilege-detection.md).

> [!NOTE]
> Bu, istediğiniz zaman gerçekleştirebileceğiniz isteğe bağlı bir adımdır. Avukat-istemci ayrıcalık algılama modelinin uygulanmaması, eBulma (Premium) vakaları oluşturmanızı ve kullanmanızı engellemez.

## <a name="next-steps"></a>Sonraki adımlar

eBulma'yı (Premium) ayarladıktan sonra [bir servis talebi oluşturmaya](create-and-manage-advanced-ediscoveryv2-case.md) hazırsınız demektir.