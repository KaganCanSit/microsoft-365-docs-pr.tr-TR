---
title: Lisans isteklerini yönetme
f1.keywords:
- CSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: sinakassaw, nicholak
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_licensing
- MACBillingLicensesRequests
- AdminSurgePortfolio
search.appverid: MET150
description: İşletmeler için Microsoft 365 aboneliğiniz için kullanıcılardan gelen lisans isteklerini gözden geçirmeyi ve onaylamayı veya reddetmeyi öğrenin.
ms.date: 04/22/2022
ms.openlocfilehash: 802b84445c83c2831e5fd88598cc00fb8b0ab867
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098702"
---
# <a name="manage-license-requests"></a>Lisans isteklerini yönetme

> [!NOTE]
> Bu makaledeki bilgiler yalnızca self servis satın alınan ürünler için geçerlidir. Daha fazla bilgi için bkz. [Self servis satın alma hakkında SSS](../subscriptions/self-service-purchase-faq.yml).

Kuruluşunuzda self servis satın alma işlemlerini devre dışı bırakırsanız, kullanıcılarınız için lisans isteği işlemini yönetmek için lisans isteklerini kullanabilirsiniz. Bir kullanıcı, engellediğiniz bir ürün için self servis satın alma işlemi yapmaya çalıştığında size lisans isteği gönderebilir. Bir istekte bulunduklarında, ürün için lisansa da ihtiyacı olan diğer kullanıcıların adlarını ekleyebilirler.

> [!NOTE]
> Kullanıcıların self servis satın almalarını engellerseniz, Microsoft onlara pazarlama e-postaları göndermez. Ayrıca ürünün deneme sürümünü kullanıyorlarsa satın alma istemlerini görmezler. Daha fazla bilgi için bkz. [Self servis satın almaları yönetme (Yönetici)](../subscriptions/manage-self-service-purchases-admins.md).

Yönetici, lisans isteklerini görmek ve yönetmek için **Lisanslama** sayfasındaki **İstekler** sekmesini kullanır. Listede, istenen ürünün adı, lisans isteyen kişinin adı, istenen tarih ve isteğin durumu gösterilir. Yöneticiler, bekleyen veya tamamlanan istekleri göstermek için listeyi filtreleyebilir. İstekler 30 gün boyunca tutulur.

## <a name="before-you-begin"></a>Başlamadan önce

Bu makaledeki görevleri gerçekleştirmek için Genel yönetici olmanız gerekir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).

## <a name="use-your-own-request-process"></a>Kendi istek işleminizi kullanma

Kuruluşunuzun kendi istek işlemi varsa, bunu kullanabilirsiniz. Kullanıcılar lisans istediğinde görüntülenen bir ileti oluşturursunuz.

> [!IMPORTANT]
> Kendi istek işleminizi kullanıyorsanız, İstekler sekmesinde hiçbir istek **görüntülenmez** . İletinizi eklemeden önce gelen mevcut istekler, siz onaylayana veya reddedene kadar gösterilmeye devam eder.

1. Yönetim merkezinde <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">BillingLicenses</a>  >  sayfasına gidin ve **İstekler** sekmesini seçin.
2. **Bunun yerine Mevcut istek işleminizi kullan'ı** seçin.
3. Sağ bölmedeki **İleti** kutusuna, kullanıcıların lisans istediğinde görmesini istediğiniz iletiyi yazın. Kuruluş ilkenizin veya diğer belgelerin bağlantısını da eklemek istiyorsanız **Belgelere bağlan (isteğe bağlı)** metin kutusuna URL'yi girin.
4. **Kaydet**'i seçin.

**İstekler** listesine döndüğünüzde **Kendi lisans isteği işleminizi kullanıyorsunuz** iletisini görürsünüz. Kullanıcılara gönderilen iletide değişiklik yapmak için Bunun **yerine Mevcut istek işleminizi kullan'ı** seçin.

## <a name="stop-using-your-own-request-process"></a>Kendi istek işleminizi kullanmayı durdurma

1. Yönetim merkezinde <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">BillingLicenses</a>  >  sayfasına gidin ve **İstekler** sekmesini seçin.
2. **Bunun yerine Mevcut istek işleminizi kullan'ı** seçin.
3. Sağ bölmede **Kuruluşumun istek işlemini kullan** onay kutusunu temizleyin.
4. **Kaydet**'i seçin.

## <a name="approve-or-deny-a-license-request"></a>Lisans isteğini onaylama veya reddetme

1. Yönetim merkezinde <a href="https://go.microsoft.com/fwlink/p/?linkid=842264" target="_blank">BillingLicenses</a>  >  sayfasına gidin ve **İstekler** sekmesini seçin.
2. Gözden geçirmek istediğiniz isteği içeren satırı seçin. Sağ bölmede, ürüne lisans isteyen kullanıcılarla ilgili ayrıntılar gösterilir.
3. İsteğin tamamını reddetmek için **Onaylama'yı** seçin ve iletişim kutusunda **Onaylama'yı** seçin.
4. İstek için bazı kullanıcıları reddetmek, ancak diğerlerini onaylamak için, kaldırmak istediğiniz kullanıcıların adına göre X işaretini seçin. Adları **Bu kullanıcılara atama'nın** altına taşınır.
5. Birden fazla ürününüz varsa, **Ürün seçin** altında lisans atamak için kullanmak istediğiniz ürünü seçin.
6. Kullanıcıların belirli uygulama ve hizmetlere erişimini engellemek için **Uygulamaları ve hizmetleri aç veya kapat'ı** genişletin, ardından hariç tutmak istediklerinize ilişkin onay kutularını temizleyin.
7. Bölmenin en altına, metin kutusuna isteğe bağlı bir ileti yazın.
8. İşiniz bittiğinde **Onayla'yı** seçin. Sağ bölmede isteğin ayrıntıları gösterilir.
9. Sağ bölmeyi kapatın.
    Kullanıcılar, isteklerinin onaylandığını veya reddedildiğini belirten bir e-posta alır.

## <a name="related-content"></a>İlgili içerik

[Kullanıcılara lisans atama](../../admin/manage/assign-licenses-to-users.md) (makale)\
[Kullanıcıları farklı bir aboneliğe taşıma](../subscriptions/move-users-different-subscription.md) (makale)\
[Abonelik lisanslarını satın alma veya kaldırma](buy-licenses.md) (makale)
