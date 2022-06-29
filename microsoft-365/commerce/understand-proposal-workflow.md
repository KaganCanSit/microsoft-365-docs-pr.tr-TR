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
description: Microsoft ürün ve hizmetlerini satın almanıza yardımcı olacak teklifler hakkında bilgi edinin.
ROBOTS: NOINDEX
ms.date: 04/28/2022
ms.openlocfilehash: e54b68b5090287d7a61e9dea70726b7ec9e83c72
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66485989"
---
# <a name="understand-the-microsoft-proposal-workflow"></a>Microsoft teklif iş akışını anlama

Teklif, kuruluşunuzun Microsoft ürün ve hizmetlerini satın alması için Microsoft tarafından sunulan resmi bir tekliftir. Teklifinizin belirli ürünlerini, hizmetlerini ve koşullarını belirlemek için doğrudan bir Microsoft temsilcisiyle birlikte çalışırsınız.

Microsoft temsilcisi, sizin ve temsilcinizin tartıştığı öğeleri içeren bir teklif taslağı hazırlar. Temsilci, Azure market portalının bağlantısını içeren bir e-posta gönderir. Site, siz ve kuruluşunuz için özel olarak hazırlanmış teklifi içerir.

Bildirim e-postasını aldıktan sonra teklif sitesinin bağlantısını izleyin. Sitede oturum açtığınızda teklif gözden geçirme işlemini başlatabilirsiniz.

## <a name="prerequisites-for-buying-items-with-a-proposal"></a>Teklifle ürün satın almak için önkoşullar

Teklif için ürün satın alabilmeniz için önce bir ödeme hesabınız ve Microsoft ile sözleşmeniz olmalıdır.

### <a name="billing-account"></a>Ödeme hesabı

Hesap ayarlarınızı, faturalarınızı, faturalama profillerinizi ve ürün ve hizmetlerinizi yönetmek için bir ödeme hesabı kullanırsınız. Henüz bir ödeme hesabınız yoksa Microsoft temsilciniz sizin için bir ödeme hesabı oluşturur. Aksi takdirde, bu ödeme hesabını kullanma izniniz olduğu sürece kuruluşunuz için mevcut bir ödeme hesabını kullanırlar.

Ödeme hesabı izinleri, ödeme hesabı sahibi tarafından yönetilir. Genel yöneticiler kendilerini ödeme hesabı sahibi rolüne atayabilir ve ardından diğer kişilerin ödeme hesabı sahibi olmasını sağlayabilir.

Ödeme hesapları hakkında daha fazla bilgi için bkz. [Ödeme hesaplarını yönetme](manage-billing-accounts.md).

### <a name="microsoft-customer-agreement"></a>Microsoft Müşteri Sözleşmesi

Microsoft Müşteri Sözleşmesi (MCA), bir kuruluşun Microsoft ürün ve hizmetlerini satın almasına olanak tanır. Daha fazla bilgi için bkz. [Microsoft Müşteri Sözleşmesi](https://www.microsoft.com/Licensing/how-to-buy/microsoft-customer-agreement).

## <a name="permissions-needed-to-sign-an-agreement-or-pay-for-items"></a>Sözleşme imzalamak veya öğeler için ödeme yapmak için gereken izinler

Bir sözleşmeyi başarıyla imzalamak veya ürün ve hizmet satın almak için ödeme hesabı sahibi veya ödeme hesabı katkıda bulunanı olmanız gerekir. Genel yöneticiyseniz ancak bu rollerden birine sahip değilseniz, rolleri kendinize atayabilirsiniz. Genel yönetici değilseniz, Genel yöneticinizden veya ödeme hesabı sahibinizden size rollerden birini atamasını isteyin.

Ödeme hesabı sahibi ve ödeme hesabı katkıda bulunanı rolleri aşağıdaki yöntemlerden biri kullanılarak atanır.

### <a name="assign-roles-in-the-microsoft-365-admin-center"></a>Microsoft 365 yönetim merkezi rol atama

1. Microsoft 365 yönetim merkezi **Faturalama** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2084771" target="_blank">hesapları</a> sayfasına gidin.
2. **Faturalama hesapları** sayfasındaki **Ödeme hesabı rolleri** bölümünde **Rol ata'yı** seçin.
3. **Rol ata** bölmesinde, rol atamak istediğiniz kişinin adını arayın.
4. Kişinin sahip olmasını istediğiniz rol adının kutusunu seçin ve ardından **Ata'yı** seçin.

### <a name="assign-roles-in-the-azure-portal"></a>Azure portal rol atama

1. Azure portal <a href="https://portal.azure.com/#blade/Microsoft_Azure_GTM/ModernBillingMenuBlade/Overview" target="_blank">Erişim denetimi (IAM)</a> sayfasına gidin.
2. **Erişim denetimi (IAM)** sayfasında **Ekle'yi** seçin.
3. **İzin ekle** bölmesinde kullanıcıya atanacak **rolü** seçin.
4. Kullanıcıyı ve ardından **Kaydet'i** seçin.

Ödeme hesabı rolleri hakkında daha fazla bilgi için bkz. [Ödeme hesaplarına erişimi anlama](manage-billing-accounts.md#understand-access-to-billing-accounts).

Bu yeni bir ödeme hesabıysa ve kimse sözleşmeyi kabul etmediyse, aşağıdakiler koşuluyla otomatik olarak ödeme hesabı sahibi olursunuz:

- Teklifte adı geçen kişi **mi yoksa**
- Kuruluşunuz için zaten [bir Azure Active Directory genel yöneticisi](/azure/active-directory/roles/permissions-reference#global-administrator) misiniz?

## <a name="what-is-the-overall-workflow"></a>Genel iş akışı nedir?

Genel teklif iş akışı şöyle görünür:

- Microsoft temsilciniz bir teklif oluşturur ve size e-postayla bir bağlantı gönderir.
- Teklif oturum açma sayfasına gitmek için bağlantıyı kullanırsınız.
- Kuruluşunuzun bilgilerini gözden geçirirsiniz.
- Teklifi gözden geçirir, gerekirse MCA'yı kabul edip ödeme işlemini tamamlarsınız.
  > [!IMPORTANT]
  > Kuruluşunuz adına bir MCA imzalama yetkiniz olmalıdır. Bu yetkiye sahip değilseniz, bunu yapan birinin bu adımı gerçekleştirmesi gerekir.
- Ödeme tamamlandıktan sonra ürün ve hizmetlerinizi ayarlamak için size ek bağlantılar verilir.

## <a name="proposal-terms"></a>Teklif koşulları

Aşağıdaki tabloda, teklifinizde ve teklif sitesinde görünen terimler ve tanımlar yer alır.

| Terim | Tanım |
|---|---|
| Ödeme hesabı | Hesap ayarlarınızı, faturalarınızı, ödeme yöntemlerinizi ve ürünlerinizi yönetmek için kullanılan bir hesap. |
| Faturalama profili | Kuruluşunuz hakkında, faturanıza hangi öğelerin dahil olduğunu ve faturalarınız için ödeme yönteminizi özelleştirmenize olanak tanıyan bilgiler. Faturalama profili faturalama hesabı adını, belirli faturalama profili için kullanılan ödeme yöntemlerini, iletişim bilgilerini, fatura ayarlarını ve faturalama profilini değiştirmenize, faturaları ödemenize ve ürün ve hizmet satın almanıza olanak sağlayan izinleri içerir. |
| Mevcut sözleşmeler | Kuruluşunuzun Microsoft ile önceden var olan tüm sözleşmeleri. Bu, bir Kurumsal Anlaşma, Microsoft Ürün & Hizmet Sözleşmesi veya Microsoft Müşteri Sözleşmesi içerebilir ancak bunlarla sınırlı değildir. |
| Microsoft Müşteri Sözleşmesi (MCA) | Kuruluşunuz tarafından Microsoft ile tutulan hesabın hüküm ve koşullarını özetleyen bir sözleşme. |
| Microsoft temsilcisi | Siz ve kuruluşunuz için bir teklif hazırlayan yetkili bir Microsoft temsilcisi. |
| Organizasyon | Microsoft ürünlerini, teknolojilerini veya hizmetlerini kullanan bir tüzel kişilik. |
| Hazırlayan | Teklifi hazırlayan Microsoft temsilcisinin e-posta adresi. |
| Ek koşullar | MCA'da kuruluşunuza özgü terimler içeren değişiklikler. Ek koşulları kabul etmek için DocuSign kullanarak elektronik imza kaydetmeniz gerekir. |

## <a name="step-1-review-organization-information"></a>1. Adım: Kuruluş bilgilerini gözden geçirme

Oturum açdıktan sonra, ilk yapmanız gereken kuruluşunuzun bilgilerini gözden geçirmektir.

### <a name="your-organization"></a>Kuruluşunuz

**Kuruluşunuz** bölümünde kendisiyle ilişkilendirilmiş ödeme hesabı görüntülenir. Ödeme hesabı bilgileri mevcut bir ödeme hesabından çekilir veya Microsoft temsilcisi tarafından sizin için oluşturulur. Kuruluşunuz başka bir kuruluşun bağlı kuruluşuysa, söz konusu kuruluşun adını ve adresini içeren bir **Müşteri Adayı kuruluşu** bölümü de görürsünüz.

Kuruluşunuz Microsoft ile ilk kez ticari bir ilişki kuruyorsa ve henüz bir MCA **imzalamadıysanız, Kuruluşunuz** veya **Müşteri Adayı kuruluşunuz** altındaki bilgiler yanlışsa, sizin için değişiklik yapmak için temsilciye başvurun. MCA'yı kabul ettikten sonra, Microsoft 365 yönetim merkezi ödeme [hesapları](https://go.microsoft.com/fwlink/p/?linkid=2084771) sayfasında kuruluşunuzun adresini ve iletişim bilgilerini gözden geçirebilir ve değiştirebilirsiniz. Kuruluşunuzun adı değişirse, güncelleştirilmiş olması için bir hizmet isteği açın. [Hizmet isteğini açmayı öğrenin](../admin/get-help-support.md).

### <a name="your-information"></a>Bilgileriniz

Yeni bir müşteriyseniz **Bilgileriniz bölümüne adınızı**, e-posta adresinizi ve telefon numaranızı girin, ardından **Kaydet'i** seçin. Mevcut bir müşteriyseniz bilgilerinizin doğru olduğundan emin olun. Herhangi bir düzeltme yapmak için **Düzenle'yi** seçin, gerekli değişiklikleri yapın ve ardından **Kaydet'i** seçin.

Hazır olduğunuzda **Devam'ı** seçerek sonraki adıma geçin.

## <a name="step-2-review-proposal"></a>2. Adım: Teklifi gözden geçirme

Teklif, Microsoft temsilcinizle tartıştığınız öğelerin ayrıntılarını içerir. E-postayı teklif bağlantısıyla ileterek kuruluşunuzdaki diğer paydaşlarla paylaşabilirsiniz. Bağlantıyı kullanan diğer herkes teklifin salt okunur bir görünümüne sahiptir.

Gözden geçirdikten sonra teklifte herhangi bir değişiklik yapmak istiyorsanız Microsoft temsilcinize başvurun.

### <a name="proposal-contents"></a>Teklif içeriği

Teklif aşağıdaki bilgileri içerir:

| Bölüm | Açıklama |
|---|---|
| Kuruluş adı | Teklifin hazırlandığı kuruluşun adı. |
| Tarihe kadar geçerli | Teklif teklifinin süresinin dolacağı tarih. Bu son kullanma tarihini kaçırırsanız, teklifle hala ilgilendiğinizi bildirmek için Microsoft temsilcinizle iletişime geçin. |
| Para birimi | Teklifteki maddelerin maliyetini hesaplamak için kullanılan para birimi. |
| Için hazırlandı | Teklifi isteyen kişinin ödeme hesabı adı, adresi, iletişim e-posta adresi ve telefon numarası. |
| Hazırlayan | Teklifi hazırlayan Microsoft temsilcisinin e-posta adresi. |
| Özet | Teklifle ilişkili alt toplamı gösterir. Gerekirse, maliyetleri hesaplamak için kullanılan döviz (FX) oranını da gösterir. |
| Teklif satırı öğeleri | Bu bölüm teklife dahil edilen tüm maddelerin miktarını, birim fiyatını ve alt toplamını içerir. |
| Sonraki adım | Bu bölüm, gerçekleştirmeniz gereken eylemi gösterir. |

MCA imzalamak için **Sonraki Adım'ın** altındaki düğmeyi seçin. Ek koşulları imzalamanız gerekiyorsa, docuSign sitesine bir bağlantı göndererek belgeyi imzalama adımlarını izleyin.

Gerekli sözleşmeleri veya ek koşulları imzaladıktan sonra **Ödemeye git'i** seçin.

## <a name="step-3-checkout"></a>3. Adım: Kullanıma Alma

Kullanıma alma sayfasında aşağıdaki bölümler yer alır:

### <a name="sold-to"></a>Alıcıya satıldı

Bu bölümde teklif için kullanılan ödeme hesabı gösterilir. Herhangi bir bilgiyi değiştirmeniz gerekiyorsa **Düzenle** bağlantısını seçin. Kuruluşunuzun Vergi Kimliğini eklemek için **Düzenle** bağlantısını da kullanabilirsiniz. Vergi Kimliği **, Alıcı** bölümünde listelenen ülkeyle ilgili olmalıdır. Vergi muafiyetiniz varsa, vergi muafiyeti durumunu istemek için bir destek bileti açmanız gerekir.

Vergi kimlikleri ve vergi muafiyeti durumuna başvurma hakkında daha fazla bilgi edinmek için bkz. [Vergi bilgileri](billing-and-payments/tax-information.md).

### <a name="billed-to"></a>Faturalanan

Bu bölümde, faturanıza hangi öğelerin dahil olduğunu ve faturalarınızı nasıl ödediğinizi belirlemek için kullanılan faturalama profili gösterilir. Her faturalama döngüsü, her faturalama profili için ayrı bir fatura alırsınız. Faturalar için çek veya havale ya da Azure ön ödemesi kullanarak ödeme yapabilirsiniz. Henüz bir faturalama profiliniz yoksa Microsoft temsilciniz sizin için bir faturalama profili oluşturur. Ödeme sırasında farklı bir faturalama profili seçebilir, varsa faturalama profilinin adını değiştirebilir veya bir P.O ekleyebilirsiniz. Numarası. Yeni bir faturalama profili de oluşturabilirsiniz.

Faturalama profilleri hakkında bilgi için bkz. [Faturalama profillerini yönetme](billing-and-payments/manage-billing-profiles.md).

### <a name="proposal-items-in-this-order"></a>Bu siparişteki teklif öğeleri

Bu bölümde teklife dahil edilen tüm öğelerin listesi gösterilir. Liste aşağıdaki kategorilerden birini veya daha fazlasını içerebilir:

- **Ek koşullar** MCA'da kuruluşunuza ait koşulları içeren değişikliklerin listesi. Örneğin, bu liste HIPAA veya GDPR koşullarını içerebilir.
- **Şimdi satın alın** Teklif kabul iş akışının sonundaki ödeme sırasında ödeme yaptığınız öğelerin listesi.
- **İndirimler (gelecekteki ücretlere uygulanır)** Teklifin bir parçası olarak aldığınız indirimlerin listesi.
- **Dahil** Teklif paketine ek ücret ödemeden dahil edilen öğelerin listesi. Bu öğelerden bazılarının gelecekte bunlarla ilişkili bir maliyeti olabilir.

> [!NOTE]
> Teklifiniz, gelecekteki başlangıç tarihine sahip abonelikleri içerebilir. Daha fazla bilgi için bkz. [Gelecekteki başlangıç tarihleri için faturalamayı anlama](billing-and-payments/future-start-date.md).

### <a name="summary"></a>Özet

Bu bölümde ödenmekte olan öğelerin sayısı, alt toplam, tahmini vergiler ve siparişin toplam tutarı gösterilir.

Siparişi vermek için **Sipariş ver'i** veya **Anlaşma &amp; siparişi kabul et'i** seçin.

Siparişi verdikten sonra, atılması gereken sonraki adımları içeren bir onay alırsınız. Bir Azure planı satın aldıysanız, sonraki adımınız Azure portal ödeme hesabınızı ayarlamaktır.

## <a name="step-4-set-up-your-new-billing-account-azure-customers-only"></a>4. Adım: Yeni ödeme hesabınızı ayarlama (yalnızca Azure müşterileri)

Yeni bir müşteriyseniz ve teklifin bir parçası olarak Azure ürünleri satın aldıysanız, sonraki adımınız yeni ödeme hesabınızı ayarlamaktır. Nasıl yapılacağını öğrenmek için bkz. [Microsoft Müşteri Sözleşmesi için ödeme hesabınızı ayarlama](/azure/cost-management-billing/manage/mca-setup-account).

Kurumsal Anlaşma olan mevcut bir Azure müşterisiyseniz ve ilk kez bir MCA imzalıyorsanız, sonraki adımınız sözleşmeler arasındaki değişiklikler ve yeni ödeme hesabınızla görevlerin nasıl tamamlayacağı hakkında bilgi edinmektir. Daha fazla bilgi edinmek için bkz. [Microsoft Müşteri Sözleşmesi için ödeme hesabınızdaki görevleri tamamlama Kurumsal Anlaşma](/azure/cost-management-billing/manage/mca-enterprise-operations).

## <a name="understand-invoicing"></a>Faturalamayı anlama

Siparişinizi kullanıma alıp tamamladıktan sonra 24-48 saat içinde ilk fatura gönderilir. Bundan sonra, her ayın 5'inde fatura alırsınız. Aylık fatura, önceki aya ait ücretleri içerir. Hesabınız için kredileriniz varsa, bunlar faturalama profilinizin para kredilerinden düşülür ve fatura bakiyenize uygulanır. Krediler uygulandıktan sonra kalan bakiye vadesi geçmiş bakiyedir. Faturayı ödemek için faturalama tarihinden itibaren 30 gününüz vardır.

Çek veya havalelerin nereye gönderileceğine ilişkin ödeme yönergeleri faturanızın PDF kopyasına eklenir. Faturanızı görüntülemek veya indirmek için bkz. [Faturanızı veya faturanızı görüntüleme](billing-and-payments/view-your-bill-or-invoice.md).
