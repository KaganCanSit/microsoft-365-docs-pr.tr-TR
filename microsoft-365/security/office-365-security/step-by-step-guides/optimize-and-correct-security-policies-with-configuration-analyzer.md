---
title: Yapılandırma çözümleyicisi ile güvenlik ilkelerini iyileştirin ve düzeltin
description: Yapılandırma çözümleyicisi ile güvenlik ilkelerini iyileştirme ve düzeltme adımları. Yapılandırma çözümleyicisi, kiracınızda yapılandırdığınız e-posta güvenlik ilkelerini yönetmek ve görüntülemek için merkezi bir konum ve tek bölmedir.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: 765eaffd2f57687c0ee16ace30aff97ddd91462c
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66042166"
---
# <a name="optimize-and-correct-security-policies-with-configuration-analyzer"></a>Yapılandırma çözümleyicisi ile güvenlik ilkelerini iyileştirin ve düzeltin

Yapılandırma çözümleyicisi, kiracınızda yapılandırdığınız e-posta güvenlik ilkelerini yönetmek ve görüntülemek için merkezi bir konum ve tek bölmedir. Standart ve Katı önerilen ayarlarımızla ayarlarınızın yan yana karşılaştırmasını yapabilir, öneriler uygulayabilir ve duruşunuzu etkileyen geçmiş değişiklikleri görüntüleyebilirsiniz.

## <a name="what-youll-need"></a>İhtiyacınız olan şey
- Exchange Online Protection
- Yeterli izinler (Güvenlik Yöneticisi rolü)
- Aşağıdaki adımları gerçekleştirmek için 5 dakika.

## <a name="compare-settings-and-apply-recommendations"></a>Ayarları karşılaştırma ve önerileri uygulama
1. adresine [https://security.microsoft.com/configurationAnalyzer](https://security.microsoft.com/configurationAnalyzer)gidin.
1. Yapmak istediğiniz yan yana karşılaştırmaya göre üstteki menüden **Standart öneriler'i** veya **Katı öneriler'i** seçin.
1. İlke değişiklikleri için Öneriler görüntülenir. (Varsa)
1. Ardından bir öneri seçebilir, önerilen eylemi, önerinin uygulanabileceği ilkeyi, geçerli yapılandırmayı & adı ayarlayabilirsiniz.
1. Bir öneri seçiliyken, Görüntülenen onay iletisinde **Öneriyi uygula'ya** ve ardından **Tamam'a** basabilirsiniz.
1. bir ilkeyi el ile düzenlemek veya ayarları doğrudan ilke içinde onaylamak isterseniz, yeni bir sekme yükleyecek ve sizi doğrudan etkilenen ilkeye kolayca götürecek **öneriyi uygula** yerine **İlkeyi görüntüle'ye** basabilirsiniz.

## <a name="view-historical-configuration-changes"></a>Geçmiş yapılandırma değişikliklerini görüntüleme

**Yapılandırma çözümleyicisi'ndeyken** üst menü çubuğundan **Yapılandırma kayma analizi ve geçmişi'ni** seçebilirsiniz.

Yüklenen sayfa, filtreler tarafından seçilen zaman çerçevesi içinde güvenlik ilkelerinizde yapılan değişiklikleri ve değişiklikle ilgili verileri ve genel duruşunuzu artırıp artırmadığını veya azaltıp azaltmadığını gösterir.

Yapılandırma Çözümleyicisi hakkında daha fazla bilgi edinmek için bkz[. Güvenlik ilkeleri için yapılandırma çözümleyicisi - Office 365 | Microsoft Docs](../../office-365-security/configuration-analyzer-for-security-policies.md).
