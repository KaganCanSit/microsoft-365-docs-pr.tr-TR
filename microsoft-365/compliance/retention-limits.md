---
title: Bekletme ilkeleri ve bekletme etiketi ilkeleri için sınırlar
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
hideEdit: true
description: Bekletme ilkeleri ve bekletme etiketi ilkeleri için ilke başına en fazla ilke ve öğe sayısını anlama
ms.openlocfilehash: fba8d0385831b4f05bbf0a967072d64eead5644a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66633421"
---
# <a name="limits-for-retention-policies-and-retention-label-policies"></a>Bekletme ilkeleri ve bekletme etiketi ilkeleri için sınırlar

>*[Güvenlik & uyumluluğu için Microsoft 365 lisanslama kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

Kuruluşunuzda verileri otomatik olarak saklamak veya silmek için [bekletme ilkeleri ve bekletme etiketi ilkeleri](retention.md#retention-policies-and-retention-labels) kullandığınızda, dikkat etmeniz gereken bazı maksimum sayılar vardır.

## <a name="maximum-number-of-retention-labels-per-tenant"></a>Kiracı başına en fazla bekletme etiketi sayısı

Kiracı başına en fazla 1.000 bekletme etiketi desteklenir.

## <a name="maximum-number-of-policies-per-tenant"></a>Kiracı başına en fazla ilke sayısı

Tek bir kiracı en fazla 10.000 ilkeye (herhangi bir yapılandırma) sahip olabilir. Bu maksimum sayı, saklamaya yönelik farklı ilkeleri ve DLP ilkeleri, bilgi engelleri, eBulma tutmaları, Dava tutmaları, In-Place Tutmalar ve duyarlılık etiketleri gibi diğer uyumluluk ilkelerini içerir. Ancak bu üst sınır şunları dışlar:

- Bulut ekleri için olmadığı sürece SharePoint ve OneDrive için otomatik etiketleme ilkeleri.
- SharePoint ve OneDrive için yayımlanan ve yalnızca saklama yerine yalnızca silme veya saklama ve silme ilkeleri.
- [Mesajlaşma kayıtları yönetiminden (MRM)](/exchange/security-and-compliance/messaging-records-management/messaging-records-management) exchange bekletme ilkeleri.

Bu 10.000 ilke sınırı içinde, iş yükü başına saklama için maksimum ilke sayısıyla ilgili bazı sınırlar da vardır:

- Exchange (herhangi bir yapılandırma): 1.800
  - Posta kutusu başına: Performans etkilenmeden önce önerilen maksimum değer 25'tir; Desteklenen sınır 50'dir.
- SharePoint veya OneDrive: (otomatik olarak eklenen tüm siteler): 13
- SharePoint veya OneDrive (dahil edilen veya hariç tutulan belirli konumlar): 2.600

> [!NOTE]
> Exchange ve SharePoint için bu maksimum sayılar saklama için özel değildir, ancak eBulma tutmaları, Dava tutmaları ve In-Place Tutmaları içeren diğer saklama ilkeleri türleriyle paylaşılır.

Microsoft Teams ve Yammer için bekletme ilkeleri, verileri saklama amacıyla depolamak için posta kutularını kullansa da, Exchange Online için maksimum ilke sayısı Teams ve Yammer için bekletme ilkelerini dışlar.

## <a name="maximums-for-adaptive-policy-scopes"></a>Uyarlamalı ilke kapsamları için maksimum değerler

Bekletme için bir [ilkeye ekleyebileceğiniz uyarlamalı ilke kapsamlarının](retention.md#adaptive-or-static-policy-scopes-for-retention) sayısıyla ilgili bir sınır yoktur, ancak her uyarlamalı kapsamı tanımlayan sorgu için bazı üst sınırlar vardır:

- Öznitelik veya özellik değerleri için dize uzunluğu: 200
- Grup olmayan veya grup içindeki özniteliklerin veya özelliklerin sayısı: 10
- Grup sayısı: 10
- Gelişmiş sorgudaki karakter sayısı: 10.000

Grup içindeki öznitelikleri veya özellikleri gruplandırma desteklenmez. Bu, tek bir uyarlamalı kapsamda desteklenen en fazla özellik veya öznitelik sayısının 100 olduğu anlamına gelir.

## <a name="maximum-number-of-items-per-policy"></a>İlke başına en fazla öğe sayısı

> [!IMPORTANT]
> Yalnızca [uyarlamalı ilke kapsamları yerine statik ilke kapsamları](retention.md#adaptive-or-static-policy-scopes-for-retention) kullanıyorsanız geçerlidir.

Belirli kullanıcıları, belirli Microsoft 365 gruplarını veya belirli siteleri dahil etmek veya hariç tutmak için statik kapsamlar ve isteğe bağlı yapılandırma kullanırsanız, ilke başına dikkat etmeniz gereken bazı sınırlar vardır.

Statik kapsamlar için bekletme için ilke başına en fazla öğe sayısı:

- Exchange posta kutuları: 1.000
- Microsoft 365 Grupları: 1.000
- Teams kanal iletileri: 1.000
- Teams sohbetleri: 1.000
- Yammer topluluk iletileri: 1.000
- Yammer kullanıcı iletileri: 1.000
- SharePoint siteleri: 100
- OneDrive hesapları: 100

Skype Kurumsal kapsamı belirli kullanıcılara göre belirlenmiştir ve ilke başına desteklenen en fazla sayı 1.000'dir.

Bu sınırlamalar ilkeye göre olduğundan, bu sayıların üzerinden geçilirken ortaya çıkan belirli eklemeleri veya dışlamaları kullanmanız gerekiyorsa, aynı bekletme ayarlarına sahip ek ilkeler oluşturabilirsiniz. Bu nedenle birden çok bekletme ilkesi kullanan bazı [örnek senaryolar ve çözümler](#examples-of-using-multiple-policies-to-avoid-exceeding-maximum-numbers) için sonraki bölüme bakın.

Ancak, birden çok ilke daha yüksek yönetim ek yüklerine neden olur. Dahil ve dışlamalarla birden çok ilke oluşturmak ve korumak yerine uyarlamalı kapsamları kullanmayı göz önünde bulundurun.

### <a name="examples-of-using-multiple-policies-to-avoid-exceeding-maximum-numbers"></a>En fazla sayının aşılmasını önlemek için birden çok ilke kullanma örnekleri

Aşağıdaki örnekler statik kapsamlara yöneliktir ve bir bekletme ilkesinin yalnızca konumunu belirtemezseniz ve önceki bölümde belgelenen en fazla öğe sayısını dikkate almanız gerektiğinde bazı tasarım çözümleri sağlar.

Exchange örneği:

- **Gereksinim**: 40.000'den fazla kullanıcı posta kutusu olan bir kuruluşta, kullanıcıların çoğu e-postalarını yedi yıl boyunca saklamalı, ancak tanımlanan kullanıcıların bir alt kümesinin (425) e-postaları yalnızca beş yıl boyunca tutulmalıdır.

- **Çözüm**: Exchange e-postası için bekletme süresi 7 yıl olan bir bekletme ilkesi oluşturun ve kullanıcıların alt kümesini hariç tutun. Ardından Exchange e-postası için bekletme süresi 5 yıl olan ikinci bir bekletme ilkesi oluşturun ve kullanıcıların alt kümesini ekleyin.

    Her iki durumda da, eklenen ve dışlanan sayı, tek bir ilke için belirtilen posta kutusu sayısı üst sınırının altındadır ve ikinci ilkeden [daha uzun bir saklama süresine](retention.md#the-principles-of-retention-or-what-takes-precedence) sahip olduğundan, kullanıcıların alt kümesinin ilk ilkeden açıkça dışlanması gerekir. Kullanıcıların alt kümesi daha uzun bir bekletme ilkesi gerektiriyorsa, bunları ilk ilkenin dışında tutmanız gerekmez.

    Bu çözümle, kuruluşa yeni katılan herhangi biri varsa, posta kutusu 7 yıl boyunca ilk ilkeye otomatik olarak eklenir ve desteklenen en fazla sayı üzerinde hiçbir etkisi yoktur. Ancak, 5 yıllık saklama süresi gerektiren yeni kullanıcılar dahil etme ve hariç tutma numaralarına eklenir ve bu sınır 1.000'e ulaşılabilir.

SharePoint örneği:

- **Gereksinim**: Bir kuruluşun birkaç bin SharePoint sitesi vardır, ancak yalnızca 2.000 site 10 yıllık bir saklama süresi gerektirir ve 8.000 site dört yıllık bir saklama süresi gerektirir.

- **Çözüm**: SharePoint için 100 belirli site içeren 10 yıllık saklama süresiyle 20 bekletme ilkesi oluşturun ve SharePoint için 100 belirli site içeren 4 yıllık saklama süresiyle 80 bekletme ilkesi oluşturun.

    Tüm SharePoint sitelerini tutmanız gerekmeyen bir nedenle, belirli siteleri belirten bekletme ilkeleri oluşturmanız gerekir. Bekletme ilkesi 100'den fazla belirtilen siteyi desteklemediğinden, iki bekletme dönemi için birden çok ilke oluşturmanız gerekir. Bu bekletme ilkeleri dahil edilen site sayısı üst sınırına sahiptir, bu nedenle saklaması gereken bir sonraki yeni site, saklama süresi ne olursa olsun yeni bir bekletme ilkesi gerektirir.

## <a name="maximum-number-of-items-for-disposition"></a>Değerlendirme için en fazla öğe sayısı

[İçeriğin eğilimi için](disposition.md) dikkate alınması gereken bazı sınırlar vardır:

- Kiracı başına en fazla sayı sayısı:
  - Şu değerlendirme gözden geçirme durumlarından birinde 16.000.000 öğe var: beklemede bırakma veya onaylı değerlendirme
  - Kayıt olarak işaretlenmiş 16.000.000 öğe otomatik olarak atılır (değerlendirme yok)

- Her bekletme etiketi için maksimum sayı sayısı:
  - Her bekletme etiketi için aşama başına bekleyen 1.000.000 öğe
  - Öğenin atılmasından sonraki yedi yıla kadar edat kanıtı ve bu süre için saklama etiketi başına 1.000.000 öğe sınırı vardır.

    Kayıt olarak işaretlenmiş öğeler için bu sınır olan 1.000.000'den yüksek bir konum kanıtına ihtiyacınız varsa[, Microsoft Desteği](../admin/get-help-support.md) başvurun.
