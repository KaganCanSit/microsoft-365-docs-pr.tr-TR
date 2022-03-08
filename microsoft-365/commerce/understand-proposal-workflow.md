---
title: Teklif iş akışını anlama
f1.keywords:
- CSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: presharm, jmueller
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_purchase
- AdminSurgePortfolio
search.appverid: MET150
description: Microsoft ürünleri ve hizmetlerini satın alamanıza yardımcı olacak teklifler hakkında bilgi alın.
ROBOTS: NOINDEX
ms.date: 03/17/2021
ms.openlocfilehash: 75674b03a1954c65fbb506baa2de3e37ee20ea5a
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63321089"
---
# <a name="understand-the-proposal-workflow"></a>Teklif iş akışını anlama

Teklif, Microsoft'un microsoft ürünleri ve hizmetlerini satın almaları için organizasyonu tarafından resmi bir tekliftir. Teklifinize ilişkin belirli ürünleri, hizmetleri ve koşulları belirlemek için doğrudan bir Microsoft temsilcisiyle birlikte çalışırsiniz.

Microsoft temsilcisi, sizin ve temsilcinizin tartıştığı öğeleri içeren bir teklifin taslağını hazırlar. Temsilci size, teklif sitesi bağlantısını içeren bir e-posta gönderir. Site, siz ve organizasyonunız için özel olarak hazırlanmış teklif içerir.

Bildirim e-postası size bildirdikten sonra, teklif sitesi bağlantısını izleyin. Sitede oturum girdikten sonra, teklifin gözden geçirme işlemini başlatabilirsiniz.

## <a name="prerequisites-for-buying-items-with-a-proposal"></a>Teklifle öğe satın almak için önkoşullar

Teklif için ürün satın almadan önce bir fatura hesabınız ve Microsoft ile bir sözleşmeniz olması gerekir.

### <a name="billing-account"></a>Fatura hesabı

Hesap ayarlarınızı, faturalarınızı, fatura profillerinizi ve ürün ve hizmetlerinizi yönetmek için bir fatura hesabı kullanırsınız. Henüz bir fatura hesabınız yoksa Microsoft temsilciniz sizin için bir hesap oluşturur. Aksi takdirde, siz bu fatura hesabını kullanma izniniz olduğu sürece onlar da sizin hesabınız için var olan bir fatura hesabını kullanırlar.

Fatura hesabı izinleri, faturalandırma hesabı sahibi tarafından yönetilir. Genel yöneticiler kendilerini faturalandırma hesabı sahibi rolüne atayarak diğer kişilerin fatura hesabı sahibi olabilir.

Fatura hesapları hakkında daha fazla bilgi için bkz. [Fatura hesaplarını yönetme](manage-billing-accounts.md).

### <a name="microsoft-customer-agreement"></a>Microsoft Müşteri Sözleşmesi

Microsoft Müşteri Sözleşmesi (MCA), bir kuruluşun Microsoft ürünleri ve hizmetleri satın almalarını sağlar. Daha fazla bilgi için [Microsoft Müşteri Sözleşmesi'ne bakın](https://www.microsoft.com/en-us/Licensing/how-to-buy/microsoft-customer-agreement).

## <a name="permissions-needed-to-sign-an-agreement-or-pay-for-items"></a>Sözleşme imzalamak veya ürünler için ödeme yapmak için gereken izinler

Fatura hesabında atanmış bir rolünüz yoksa, teklifi görüntüden sonra temel okuyucu rolüne atanır. Bu rol teklifi görüntülemenizi ancak herhangi bir işlemde yer almamanizi sağlar. Bir sözleşme imzalamadan veya ürün ve hizmet satın almadan önce, faturalandırma hesabı sahibi veya fatura hesabı katkıda bulunan rolüne atanmışsınızdır. Fatura hesabı sahibi bu rolü size atayabilirsiniz.

Fatura hesabı rolleri hakkında daha fazla bilgi için bkz. [Fatura hesaplarına erişimi anlama](manage-billing-accounts.md#understand-access-to-billing-accounts).

Bu yeni bir fatura hesabı ise ve kimse sözleşmeyi kabul etmese, size sağlanan otomatik olarak fatura hesabının sahibi olursanız:

- Teklifte adı aynı olan kişi **veya**
- Zaten Azure Active Directory [genel yöneticisisiniz](/azure/active-directory/roles/permissions-reference#global-administrator)

## <a name="what-is-the-overall-workflow"></a>Genel iş akışı nedir?

Genel teklif iş akışı şöyle görünüyor:

- Microsoft temsilciniz bir teklif oluşturur ve size bir bağlantı e-posta gönderir.
- Bağlantıyı kullanarak teklif oturum açma sayfasına gidersiniz.
- Kuruluş bilgilerini gözden geçirebilirsiniz.
- Teklifi gözden geçirip gerekirse MCA'yı kabul edersiniz ve ödeme işlemini tamamlarsanız.
  > [!IMPORTANT]
  > Bir MCA'yı organizasyonunuz adına imzalama yetkiniz olması gerekir. Bu yetkiye sahip değilsiniz, o zaman bu adımı yapacak biri gerekir.
- Ödeme tamam olduktan sonra, size ürünlerinizi ve hizmetlerinizi ayarlamak için ek bağlantılar verilir.

## <a name="proposal-terms"></a>Teklif koşulları

Aşağıdaki tablo, teklifinizin içinde ve teklif sitesinde görünen terimleri ve tanımları içerir.

| **Dönem** | **Tanım** |
|------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Fatura hesabı | Hesap ayarlarınızı, faturalarınızı, ödeme yöntemlerinizi ve ürünlerinizi yönetmek için kullanılan bir hesap. |
| Ödeme profili | Faturanıza hangi öğelerin dahil olduğunu ve faturalarınızı nasıl ödeyebileceğinizi özelleştirmenize olanak sağlayan, kuruluşlarınız hakkında bilgiler. Fatura profilinde fatura hesabı adı, belirli bir faturalama profili için kullanılan ödeme yöntemleri, iletişim bilgileri, fatura ayarları ve fatura profilini değiştirme, faturaları ödeme ve ürün ve hizmet satın alma izinlerini içerir. |
| Mevcut sözleşmeler | Microsoft ile zaten organizasyon arasında yapılan herhangi bir sözleşme. Bu, bir Sözleşme, Microsoft Ürün & Sözleşmesi veya Microsoft Kurumsal Anlaşma Sözleşmesi'ne dahildir ancak bunlarla sınırlı değildir. |
| Microsoft Müşteri Sözleşmesi (MCA) | Microsoft ile, organizasyon hesabınız tarafından sahip olunan hesabın hüküm ve koşullarını ana hatlarıyla özetlenen bir sözleşme. |
| Microsoft temsilcisi | Sizin ve organizasyonun için teklif hazırlayacak yetkili bir Microsoft temsilcisi. |
| Kuruluş | Microsoft ürünleri, teknolojileri veya hizmetlerini kullanan bir tüzel kişilik. |
| Hazır | Teklifi hazır eden Microsoft temsilcisinin e-posta adresi. |
| Ek şartlar | Organizasyona özgü terimleri içeren MCA'da yapılan değişiklikler. Ek koşulları kabul etmek için, DocuSign kullanarak elektronik imza kaydetmeniz gerekir. |

## <a name="step-1-review-organization-information"></a>1. Adım: Kuruluş bilgilerini gözden geçirme

Oturum katıldıktan sonra ilk olarak kuruluş bilgilerini gözden geçirebilirsiniz.

### <a name="your-organization"></a>Organizasyonunız

Your **organization section** displays the billing account associated with it. Fatura hesabı bilgileri mevcut bir ödeme hesabından çekilir veya sizin için Microsoft temsilcisi tarafından oluşturulur. Organizasyonunız başka bir kuruluşa bağlı bir kuruluşsa, o kuruluşun adını  ve adresini de bulunduran bir Lider kuruluş bölümü görüyorsunuz.

Kuruluşun Microsoft ile ilk kez ticari bir ilişki kurduğu ve henüz bir MCA imzalamadınız, Organizasyonun veya Liderlik Kuruluşu altındaki bilgiler yanlışsa, sizin için değişiklik yapmak  için temsilciye  başvurun. MCA'yı kabul ettikten sonra, aşağıdaki giriş sayfasının Fatura hesapları sayfasında, kuruluş adresinizi ve [iletişim bilgilerinizi gözden](https://go.microsoft.com/fwlink/p/?linkid=2084771) geçirebilirsiniz Microsoft 365 yönetim merkezi. Kuruluş adınız değişirse, güncelleştirilmiş bir hizmet isteği açın. [Hizmet isteğini açmayı öğrenin](../admin/get-help-support.md).

### <a name="your-information"></a>Bilgileriniz

Yeni müşteriysanız, Adınız, e-posta adresinizi ve telefon numaranızı Bilgilerim'in altına girin ve **Ardından** Kaydet'i **seçin**. Mevcut müşteriysiniz, bilgilerin doğru olduğunu doğrulayın. Herhangi bir düzeltmeyi yapmak için **Düzenle'yi seçin**, gerekli değişiklikleri yapın ve sonra Kaydet'i **seçin**.

Hazır olduğunda, sonraki adıma **geç** için Devam'ı seçin.

## <a name="step-2-review-proposal"></a>2. Adım: Teklifi gözden geçirme

Teklif, Microsoft temsilciniz ile tartışılan öğelerin ayrıntılarını içerir. E-postayı teklif bağlantısını kullanarak iletebilirsiniz ve bu bağlantıyı organizasyon siteniz üzerindeki diğer proje katılımcıları ile paylaşabilirsiniz. Bağlantıyı kullanan diğer herkesin teklifin salt okunur görünümü olur.

gözden geçirme sonrasında teklifte herhangi bir değişiklik yapmak için Microsoft temsilcinize başvurun.

### <a name="proposal-contents"></a>Teklif içeriği

Teklif aşağıdaki bilgileri içerir:

| Bölüm | Açıklama |
|---------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Kuruluş adı | Teklifin hazır olduğu kuruluşun adı. |
| Tarihe kadar geçerli | Teklif teklifinin süresinin dol olduğu tarih. Bu son kullanma tarihini kaçırırsanız, teklifle hala ilgilendiğinizi haber almak için Microsoft temsilcinize başvurun. |
| Para birimi | Teklifte öğelerin maliyetini hesaplamak için kullanılan para birimi. |
| Hazır | Teklifi isteyen kişinin fatura hesabı adı, adresi, iletişim e-posta adresi ve telefon numarası. |
| Hazır | Teklifi hazır eden Microsoft temsilcisinin e-posta adresi. |
| Özet | Teklifle ilişkili alt toplamı gösterir. Gerekirse, maliyetleri hesaplamak için kullanılan yabancı döviz (FX) oranını da gösterir. |
| Teklif satırı öğeleri | Bu bölümde, teklife dahil edilen tüm öğelerin miktarı, birim fiyatı ve alt toplamları yer almaktadır. |
| Sonraki adım | Bu bölüm, gerekli eylemi eylemin nasıl bir işlemle ilgili olduğunu gösterir. |

MCA imzalamak için Sonraki Adım'ın altındaki **düğmeyi seçin**. Ek koşulları imzalamanız gerekiyorsa, bir bağlantı sizi DocuSign sitesine alır ve burada belgeyi imzalama adımlarını takip edersiniz.

Gerekli sözleşme veya ek koşulları imza verdikten sonra, Ödemeye **git'i seçin**.

## <a name="step-3-checkout"></a>3. Adım: Ödeme

Çıkış sayfası aşağıdaki bölümleri içerir:

### <a name="sold-to"></a>Satıldığı yer

Bu bölümde, teklif için kullanılan fatura hesabı yer almaktadır. Herhangi bir bilgiyi değiştirmek için **Düzenle bağlantısını seçin** . Ayrıca, Düzenle bağlantısını **kullanarak** kurum vergi no'larını da eklemek için kullanabilirsiniz. Vergi No'lar, Satılan yer bölümünde listelenen **ülkeyle ilgili** olması gerekir. Vergi muafiyeti varsa, vergi muafiyeti durumu talep etmek için bir destek bileti açsanız gerekir.

Vergi kimlikleri ve vergi muafiyeti durumu hakkında daha fazla bilgi edinmek için Vergi [bilgileri'ne bakın](billing-and-payments/tax-information.md).

### <a name="billed-to"></a>Faturalandır

Bu bölümde, faturanıza hangi öğelerin dahil olduğunu ve faturalarınızı nasıl ödemenizi belirlemek için kullanılan ödeme profili yer almaktadır. Her ödeme döngüsünde, her ödeme profili için ayrı bir fatura alırsınız. Faturalara ödeme için çek veya havale ya da Azure ön ödemesini kullanabilirsiniz. Henüz bir fatura profiliniz yoksa, Microsoft temsilciniz sizin için bir profil oluşturur. Ödeme sırasında, varsa farklı bir ödeme profili seçerek fatura profilinin adını değiştirebilir veya P.O.  eklersiniz. numarasına iki 5000 Ayrıca yeni bir ödeme profili de oluşturabilirsiniz.

Fatura profilleri hakkında bilgi için bkz. [Fatura profillerini yönetme](billing-and-payments/manage-billing-profiles.md).

### <a name="proposal-items-in-this-order"></a>Bu siparişte teklif öğeleri

Bu bölümde, teklife dahil edilen tüm öğelerin listesi görüntülenir. Listede aşağıdaki kategorilerden biri veya daha fazlası yer alıyor olabilir:

- **Ek şartlar** A list of any amendments of the MCA that contain terms for your organization. Örneğin, bu liste HIPAA veya GDPR terimlerini içerebilir.
- **Şimdi satın alın** Teklif kabul iş akışının sonundaki ödeme sırasında ödemesi yapılan öğelerin listesi.
- **İndirimler (gelecekteki ücretler için uygulanır)** Teklifin bir parçası olarak size gelen indirimlerin listesi.
- **Dahil** Ek ücret ödemeden teklif paketine dahil edilen öğelerin listesi. Bu öğelerden bazılarının gelecekte bu öğelerle ilişkilendirilmiş bir maliyeti olabilir.

### <a name="summary"></a>Özet

Bu bölümde ödeme yapılan öğe sayısı, alt toplam, tahmini vergiler ve sipariş için toplam tutar gösterir.

Siparişi sipariş etmek için Sipariş **et'i veya Sözleşmeyi kabul** **et sipariş et'i &amp; seçin**.

Siparişi verdikten sonra, sonraki adımların yer alacak olan bir onay alırsınız. Bir Azure planı satın aldıysanız, bir sonraki adımınız Azure portalında fatura hesabını ayarlamaktır.

## <a name="step-4-set-up-your-new-billing-account-azure-customers-only"></a>4. Adım: Yeni fatura hesabını ayarlama (yalnızca Azure müşterileri)

Yeni bir müşteriysanız ve teklifin bir parçası olarak Azure ürünleri satın aldıysanız, bir sonraki adımınız yeni fatura hesabını ayarlamaktır. Nasıl olduğunu öğrenmek için bkz [. Microsoft Müşteri Sözleşmesi için fatura hesabını ayarlama](/azure/cost-management-billing/manage/mca-setup-account).

Kurumsal Anlaşma hesabı olan mevcut bir Azure müşterisiysiniz ve MCA'yı ilk kez imzalarsanız, sonraki adımınız sözleşmeler arasındaki değişiklikler ve yeni fatura hesabınızla görevlerin nasıl tamamlanacakları hakkında bilgi edinmektir. Daha fazla bilgi için bkz[. Microsoft Kurumsal Anlaşma Sözleşmesi için fatura hesaplarında görevleri tamamlama](/azure/cost-management-billing/manage/mca-enterprise-operations).

## <a name="understand-invoicing"></a>Faturalamayı anlama

Siparişinizi iade edin ve tamamlandıktan sonra 24-48 saat içinde bir ilk fatura gönderilir. Bundan sonra, her ayın 5'inde kadar fatura alırsınız. Aylık fatura, geçen aydan gelen ücretleri içerir. Hesabınız için herhangi bir krediniz varsa, bu krediler fatura profilinizin para kredilerinden düşüler ve fatura bakiyenize uygulanır. Kredi uygulandıktan sonra kalan bakiye, borç bakiyesi olur. Faturayı ödemek için fatura tarihine 30 gün kaldı.

Çek veya havale gönderme yerlerinin ödeme yönergeleri faturanın PDF kopyasında yer almaktadır. Faturanızı görüntülemek veya indirmek için bkz. [Faturanızı veya faturanızı görüntüleme](billing-and-payments/view-your-bill-or-invoice.md).
