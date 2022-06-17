---
title: Önceden ayarlanmış güvenlik ilkeleriyle her zaman en uygun güvenlik denetimlerine sahip olmanızı sağlayarak
description: Önceden ayarlanmış güvenlik ilkeleriyle her zaman en iyi güvenlik denetimlerine sahip olduğunuzdan emin olmak için adımlar. Önceden ayarlanmış ilkeler, Standart veya Katı bir güvenlik profili seçmenize olanak verir. Microsoft, Office 365 için Microsoft Defender genelinde güvenlik denetimlerini sizin için yönetir ve korur.
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
ms.openlocfilehash: 534e548dbd0950b387e757bfb81ebb446f617086
ms.sourcegitcommit: 7ac54e1952383d5cd5f084c6a9d247eb747d4904
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66139462"
---
# <a name="ensuring-you-always-have-the-optimal-security-controls-with-preset-security-policies"></a>Önceden ayarlanmış güvenlik ilkeleriyle her zaman en uygun güvenlik denetimlerine sahip olmanızı sağlayarak

Önceden ayarlanmış güvenlik ilkeleri Standart veya Katı güvenlik profili seçmenize ve Microsoft'un sizin için Office 365 için Microsoft Defender genelinde güvenlik denetimlerini yönetmesini ve korumasını sağlar.

Yeni denetimler eklendikçe veya bir güvenlik denetimi için en iyi yöntem ayarı gelişen tehdit ortamıyla değişirse Microsoft, Standart veya Katı ön ayarlı güvenlik ilkesine atanan kullanıcılar için güvenlik denetimi ayarlarını otomatik olarak güncelleştirir. Güvenlik Hazır Ayarı ilkelerini kullanarak, kullanıcılarınız için her zaman Microsoft'un önerdiği en iyi yöntem yapılandırmasına sahip olursunuz.

## <a name="what-you-will-need"></a>İhtiyacınız olan şey
- Office 365 için Microsoft Defender Plan 1 veya üzeri (E5'e dahildir)
- Yeterli izinler (Güvenlik Yöneticisi rolü)
- Aşağıdaki adımları gerçekleştirmek için 5 dakika.

## <a name="choosing-between-standard-and-strict-policies"></a>Standart ve Katı ilkeler arasında seçim

Katı ön ayarlı güvenlik ilkemiz, daha agresif algılamalara neden olacak ve yöneticinin son kullanıcılara hangi engellenen e-postaların yayımlanacağına karar vermesine neden olacak güvenlik denetimleri için daha agresif sınırlar ve ayarlara sahiptir.

- Daha iyi postaların şüpheli olarak işaretlenmeleri anlamına gelse bile daha agresif algılamalar gerektiren kullanıcılarınızın listesini toplayın. Bunlar genellikle yönetici personeliniz, yönetici destek personeliniz ve geçmişte yüksek oranda hedeflenen kullanıcılardır.

- Son kullanıcı postanın iyi olabileceğini düşünüyorsa ve iletinin kendilerine yayımlanmasını isterse, seçili kullanıcıların e-postaları gözden geçirmek ve yayınlamak için yönetici kapsamına sahip olduğundan emin olun.

- Yukarıdaki ölçütler karşılanırsa, kullanıcı Katı önceden ayarlanmış güvenlik ilkesine yerleştirilmelidir. Aksi takdirde kullanıcı Standart önceden ayarlanmış güvenlik ilkesine yerleştirilmelidir.

> [!TIP]
> Standart ve Katı güvenlik ilkelerinin ne olduğu hakkında bilgi için bu [makaleye](../../office-365-security/recommended-settings-for-eop-and-office365.md) bakın.

## <a name="enable-security-presets"></a>Güvenlik Ön Ayarlarını Etkinleştirme

Kullanıcılarınız için Standart ve Katı güvenlik önayar ilkeleri arasında seçim yaptıktan sonra, kullanıcıları her ön ayara atamak birkaç adım daha sürer.

1. Standart ve Katı güvenlik ön ayarlarına eklemek istediğiniz kullanıcıları, grupları veya etki alanlarını belirleyin.
1. adresinden Microsoft Güvenlik portalında https://security.microsoft.comoturum açın.
1. Sol gezinti bölmesindeki **E-posta & işbirliği** bölümünde **İlkeler & kuralları'nı** seçin.
1. **Tehdit ilkeleri'ne tıklayın**.
1. Şablonlu ilkeler başlığının altında **Önceden Ayarlanmış Güvenlik** **İlkeleri'ni** seçin
1. Standart koruma ön ayarının altında **Yönet'i** seçin.
1. Kiracı genelinde Exchange Online Protection uygulamak için **Tüm Alıcılar'ı** seçin veya koruma ilkesini uygulamak istediğiniz kullanıcıları, grupları veya etki alanlarını el ile eklemek için **Belirli alıcılar'ı** seçin. **İleri** düğmesine tıklayın.
1. Office 365 için Defender Koruması kiracısı genelinde uygulamak için **Tüm Alıcılar'ı** seçin veya koruma ilkesini uygulamak istediğiniz kullanıcıları, grupları veya etki alanlarını el ile eklemek için **Belirli alıcılar'ı** seçin. **İleri** düğmesine tıklayın.
1. **Kimliğe Bürünme Koruması bölümünde, kimliğe bürünme** saldırılarından korunmak için e-posta adreslerini & etki alanları ekleyin, ardından kimliğe bürünme korumasının uygulanmasını istemediğiniz güvenilen gönderenleri ve etki alanlarını ekleyin ve **ardından İleri'ye** basın
3. **Onayla** düğmesine tıklayın.
4. Katı koruma ön ayarında **Yönet** bağlantısını seçin.
5. 7-10 arası adımları tekrarlayın, ancak kullanıcılar için sıkı koruma uygulanmalıdır. (varsa)
7. **Onayla** düğmesine tıklayın.

> [!TIP]
> Önceden ayarlanmış polcies hakkında daha fazla bilgi edinmek için [buraya](../../office-365-security/preset-security-policies.md) tıklayın

## <a name="next-steps"></a>Sonraki Adımlar

Kullanıcılarınızın Microsoft'un en iyi yöntemlerine göre yapılandırılıp yapılandırılmadığını belirlemek için yapılandırma çözümleyicisini kullanın.

> [!TIP]
> Yapılandırma çözümleyicisi yöneticilerin, ayarların önceden ayarlanmış güvenlik ilkelerindeki Standart veya Katı koruma profili ayarlarının altında olduğu güvenlik ilkelerini bulmasını ve düzeltmesini sağlar. Yapılandırma çözümleyicisi hakkında daha fazla bilgi [için buraya bakın](../../office-365-security/configuration-analyzer-for-security-policies.md).

Microsoft'un en iyi yöntemlerini her zaman kullandığınızdan emin olduğundan, Güvenli Ön Ayarlar her zaman önerilir. Ancak bazı durumlarda özelleştirilmiş yapılandırmalar gereklidir. Özel ilkeler hakkında [buradan](../../office-365-security/tenant-wide-setup-for-increased-security.md) bilgi edinin.

