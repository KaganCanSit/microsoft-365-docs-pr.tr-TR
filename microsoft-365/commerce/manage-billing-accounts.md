---
title: Fatura hesaplarını anlama
f1.keywords:
- NOCSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: tugu, jmueller
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_billing
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkMAC
search.appverid: MET150
description: Fatura hesapları ve bunların hesap ayarlarını, faturaları, ödeme yöntemlerini ve satın almaları yönetmek için nasıl kullanıldıklarını öğrenin.
ms.date: 03/17/2021
ms.openlocfilehash: 8d80e94cbb415f93015673065e47d2fe36194bc0
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63315785"
---
# <a name="understand-billing-accounts"></a>Fatura hesaplarını anlama

Microsoft ürünlerini denemek veya satın almak için kaydolarak bir fatura hesabı oluşturulur. Hesap ayarlarınızı, faturalarınızı, ödeme yöntemlerinizi ve satın almalarınızı yönetmek için fatura hesabını kullanırsınız. Birden çok ödeme hesabına erişebilirsiniz. Örneğin, doğrudan Microsoft 365 için oturum veya kuruluşun Microsoft Ürün Kurumsal Anlaşma Hizmet Sözleşmesi'ne veya & Microsoft Müşteri Sözleşmesi'ne erişiminiz olabilir. Bu senaryoların her biri için ayrı bir fatura hesabınız olur.

Aşağıdaki <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> hesapları şu anda desteklemektedir:

- Microsoft Online Services Programı: Bu fatura hesabı, doğrudan bir kullanıcı aboneliğine Microsoft 365 oluşturulur.
- Microsoft Ürün & Hizmet Sözleşmesi (MPSA) Programı: Bu fatura hesabı, kuruluş yazılım ve çevrimiçi hizmet satın almak için MPSA Toplu Lisanslama sözleşmesi imzala geldiğinde oluşturulur.
- Microsoft Müşteri Sözleşmesi: Bu fatura hesabı, organizasyonunız bağımsız olarak bir Microsoft temsilcisiyle, yetkili bir iş ortağıyla veya satın almalarla birlikte geldiğinde oluşturulur.

Fatura <a href="https://go.microsoft.com/fwlink/p/?linkid=2084771" target="_blank">hesapları sayfası</a> , Microsoft ile ticari hesaplarınızı görüntülemenizi sağlar. Varsayılan olarak, kuruluşta doğrudan satın alma zamanı veya Toplu Lisans düzenlemesi aracılığıyla kabul edilen bir sözleşmeyle ilişkilendirilmiş en az bir fatura hesabı vardır.

## <a name="understand-billing-account-details"></a>Fatura hesabı ayrıntılarını anlama

Fatura hesapları ayrıntı **sayfasının en üstünde** , hesap profiliniz vardır ve hesabınızla ilgili yasal ve vergi bilgilerini içerir. Yasal adresinizi ve telefon numaranızı değiştirmek için profilinizi güncelleştirebilirsiniz. Bu hesap, satın aldığınız ürünlerin ödemelerini alan tüzel kişidir.

Aşağıdaki tabloda, Fatura hesapları ayrıntı sayfasında gördüğünüz **önemli terimler** listelanmaktadır.

| Alan adı | Açıklama |
|------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Satılacak adres | Ödemeden sorumlu olan tüzel kişi ve faturada kimlik. Burada sağlanan adres, satın alma sırasında alternatif bir sevkiyat adresi sağlamayı tercih olmadığınız sürece vergi oranınızı belirlemek için kullanılır. Daha fazla bilgi için bkz. [Vergi bilgileri](billing-and-payments/tax-information.md). |
| Segment | Kuruluşun iş segmentini tanımlayan salt okunur bir alan (Ticari, Eğitim, Kamu veya Kar amacı gütmeyen kuruluş). |
| Hesap durumu | Microsoft ile ticari hesabınız durumunu belirten salt okunur bir alan. |
| Vergi No | ABD dışındansanız KDV veya yerel eşdeğeri sağlaymanız gerekir. Daha fazla bilgi için bkz. [Vergi bilgileri](billing-and-payments/tax-information.md). |
| Sözleşme | Doğrudan satın alma ya da Toplu Lisans düzenlemesi aracılığıyla bir fatura hesabı oluşturulduğunda, kuruluşun bir belgeyi kabul veya imzalaması, hesabın koşullarıyla ilgili koşulları & bir sözleşme kabul eder veya imzalar. Uygunsa, bu görünümde sözleşme geçmişi listelene. Güncelleştirilmiş şartları kabul etmek zorundaysanız, Sözleşmeyi onayla **bağlantısı** görüntülenir. |
| Ödeme profilleri | Fatura profili faturanızı, faturayı kimin aldığı, faturanın nasıl teslim aldığı, ödeme koşulları ve PO numarası gibi özelliklerini tanımlar. Faturalamayı tüm organizasyona dağıtmak için, birden çok fatura profili oluşturabilir ve satın alma zamanında uygun ödeme profilini tanımlayabilirsiniz. Fatura profilleri ve bunları kullanarak organizasyonunız için daha esnek faturalama seçenekleri oluşturmak üzere nasıl kullanabileceğiniz hakkında daha fazla bilgi için Fatura [profillerini anlama.](billing-and-payments/manage-billing-profiles.md) |

> [!NOTE]
> Satılacak kişi adını veya **adresini** değiştirmeniz gerekiyor, ancak Düzenleme bağlantısını görmüyorsanız, değiştirmek için [deha](../admin/get-help-support.md) başvurun. Satılacak ad **değişikliği isteği** için kredi denetimi gerekir. Bu [formu doldurun](https://www.microsoft.com/download/details.aspx?id=102732) ve destek ile iletişim kurarak aşağıdaki belgelerden birini Microsoft ile paylaşmaya hazır olun:
>
> - Resmi olarak verilen belge veya kayıt mektubu
> - Yerel şirketin kayıt defterinin çıktısını çıktısı
>
> Destek, yalnızca müşteri adı değişikliklerinin olduğu ancak varlığın aynı kalmasıyla birlikte ad ve adres değişikliklerinde yardımcı olabilir. Sağlanan belgelerde, yalnızca varlığın adının değiştiğini açıkça gösterlanmalıdır. Değişiklik, satış satışları, denetimler değişikliği veya Müşteri Bağlı Kuruluşlarının ayrım yapma ya da "geri çevirme" gibi bir işlem sonucu elde edildiyse, lütfen Microsoft Satıcınıza ulaşın.

## <a name="shipping-addresses"></a>Sevkiyat adresleri

Bu bölümde, fatura hesabınızla ilişkilendirilmiş sevkiyat adresleri listelemektedir. Bir satın almada, satın alma adresinizin nereye sevk edildiği veya nerede olduğunu belirlemek için bu adresi kullanabilirsiniz. Sevkiyat adresi düzenlenebilir. Sevkiyat adresi ekleyebilir veya mevcut adresi güncelleştirebilirsiniz. Bu adres, alışverişin vergi oranını belirlemek için kullanılır.

## <a name="understand-access-to-billing-accounts"></a>Fatura hesaplarına erişimi anlama

Diğer kullanıcılara, rol ve izinler aracılığıyla fatura <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> erişim sabilirsiniz. Fatura hesabı sahibi, faturalandırma hesabına erişim iznini yalnızca bir faturalama hesabı sahibine verebilirsiniz. Kullanıcılara aşağıdaki rollerden birini atabilirsiniz:

- **Fatura hesabı sahibi** &mdash; İzinleri atayın, hesapları düzenleyin, sözleşmeleri imzalar ve hesapları görüntüleyemez.
- **Fatura hesabı katkıda bulunanı** &mdash; Hesapları düzenleyebilir, sözleşme imzalar ve hesapları  görüntüleyemez.
- **Fatura hesabı okuyucu** &mdash; Hesapları  bakabilirsiniz.

> [!Note]
> Fatura hesabı rolleri yalnızca fatura hesapları için geçerlidir ve diğer ödeme senaryoları Microsoft 365 yönetim merkezi değildir.

## <a name="related-content"></a>İlgili içerik

[Vergi bilgileri](billing-and-payments/tax-information.md) (makale) \
[Ödeme profillerini anlama](billing-and-payments/manage-billing-profiles.md) (makale)
