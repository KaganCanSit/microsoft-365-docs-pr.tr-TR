---
title: Ödeme profillerini anlama
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: jkinma, jmueller
audience: Admin
ms.topic: article
f1.keywords:
- MACBillingBillsPaymentsBillingProfiles
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_billing
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid: MET150
description: Fatura profillerini nasıl destekleyeceklerini öğrenin.
ms.date: 04/02/2021
ms.openlocfilehash: 472b5c4754d686877077133467e33592b5c0b85e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63311879"
---
# <a name="understand-billing-profiles"></a>Ödeme profillerini anlama

Fatura profili bir ödeme yöntemi, Fatura bilgileri ve satın alma siparişi numarası ve e-posta fatura tercihi gibi diğer fatura ayarlarını içerir. Microsoft'tan satın alan ürünlerin ödemelerini yapmak için ödeme profili kullanırsanız. Bir kullanıcı self servis alışveriş oluşturduğunda otomatik olarak bir ödeme profili oluşturulur. Her ödeme profili ayrı fatura edilir.

> [!NOTE]
>
> Fatura profilleri, satın alma sayfasındaki ürünler ve hizmetleri Microsoft.com satın alan veya ilgili **sayfanın Hizmet satın** al sayfasından Microsoft 365 yönetim merkezi.

## <a name="what-are-billing-profile-roles"></a>Fatura profili rolleri nedir?

Ödeme profillerinde roller, satın almaları kontrol etmek, faturaları görüntülemek ve yönetmek için izinlere sahiptir. Faturaları takip eden, düzenleyen ve ödeyen kullanıcılara bu rolleri attayabilirsiniz. Örneğin, tedarik ekibi üyeleri kurum içindedir.

| Rol                         | Açıklama                                                                      |
|----------------------------- |--------------------------------------------------------------------------------- |
| Ödeme profili sahibi        | Ödeme profili için her şeyi yönetme                                          |
| Ödeme profili katılımcısı  | Ödeme profilinde izinler dışında her şeyi yönetme                        |
| Ödeme profili okuyucusu       | Fatura profilinde her şeyin salt okunur görünümü                                |
| Fatura yöneticisi              | Faturaları görüntüleme ve ödeme, faturalandırma profilinde her şeyin salt okunur görünümünü sağlar  |

## <a name="view-my-billing-profiles"></a>Fatura profillerimi görüntüle

> [!NOTE]
>
> Bu adımları izlersiniz ve fatura profilleri listesi boşsa bu, fatura profiliniz olmadığını ve bu özelliği kullana olmadığınız anlamına gelir.

1. Yönetim merkezinde, **Faturalar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2102895" target="_blank">Fatura ve ödemeler</a> sayfasına gidin.
2. Ödeme **profili sekmesini** seçin ve sonra da listeden bir fatura profili seçin.

Her ödeme profili aşağıdaki bilgileri içerir:

- **Ödeme profili adı ve durumu** &ndash; Fatura profilinin benzersiz adı ve fatura profilinin satın alma için etkin mi yoksa devre dışı mı olduğu.
- **Fatura ayarları** &ndash; Fatura hesabının ülkeye göre para birimi, fatura sıklığı ve tarihi hakkında bilgiler, faturaları e-posta eki olarak alma seçeneği ve isteğe bağlı po numarası alanı
- **Ödeme yöntemleri** &ndash; Profilin birincil ve yedek ödeme yöntemini (varsa) gösterir
- **Fatura hesabı** &ndash; Profilin ilişkili olduğu fatura hesabının adı. Fatura hesapları hakkında daha fazla bilgi için bkz. [Fatura hesaplarını anlama](../manage-billing-accounts.md).
- **İletişim bilgileri** &ndash; Fatura adresi, kişi adı ve e-posta adresi
- **Ödeme profili rolleri** &ndash; Bu profilde yapılacak işleri yapmak için fatura profili rollerinden biri atanan kişilerin listesi. Örneğin, faturaları ödeyin, SATıN ALMA SIPARIŞI numarası ekleyin veya satın almalar yapmak için kullanılan ödeme yöntemini değiştirin.

> [!NOTE]
>
> Ödeme profili rollerini yalnızca kuruluşta yer alan kullanıcılara atabilirsiniz.

## <a name="need-help-contact-support"></a>Yardıma mı ihtiyacınız var? Destek ekibine başvurun

Azure ücretleriniz hakkında sorularınız varsa veya yardıma ihtiyacınız varsa Azure <a href="https://portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest" target="_blank">desteği ile bir destek isteği oluşturun</a>.

Sorularınız varsa veya fatura profilinizle ilgili yardıma ihtiyacınız varsa Microsoft 365 yönetim merkezi [başvurun](../../admin/get-help-support.md).

## <a name="related-content"></a>İlgili içerik

[Aboneliğiniz için ödeme bir fatura profiliyle ödeme](pay-for-subscription-billing-profile.md) (makale)\
[Fatura hesaplarını anlama](../manage-billing-accounts.md) (makale)\
[Ödeme yöntemlerini yönetme](manage-payment-methods.md) (makale)
