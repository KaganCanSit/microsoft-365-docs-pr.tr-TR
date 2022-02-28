---
title: Facebook verilerini arşivlemek için bağlayıcı ayarlama
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Verileri Facebook & sayfalarından Microsoft 365 uyumluluk merkezi verileri içeri & için bağlantı & ayarlamayı ve ayarlamayı Microsoft 365.
ms.openlocfilehash: b78a2ae168c896d525ad57bc986105e891f7dde9
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988191"
---
# <a name="set-up-a-connector-to-archive-facebook-data-preview"></a>Facebook verilerini arşivlemek için bağlayıcı ayarlama (önizleme)

Facebook business sayfalarından verileri içeri Microsoft 365 uyumluluk merkezi ve arşivlemek için bağlantı sayfalarında bir bağlayıcı Microsoft 365. Bağlayıcıyı ayardikten ve yapılandırdikten sonra, bağlayıcı Facebook İş sayfasına bağlanır (zamanlanmış bir temele göre), Facebook öğelerinin içeriğini e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri Microsoft 365'te bir posta kutusuna dönüştürür.

Facebook verileri aktarıldıktan sonra, Facebook verilerine Microsoft 365 Saklama, İçerik Araması, In-Place Arşivleme, Denetim, İletişim uyumluluğu Microsoft 365 bekletme ilkeleri gibi Microsoft 365 uyumluluk özelliklerini uygulayabilirsiniz. Örneğin, posta kutusu Mahkeme Tutma'ya yerleştirilse veya bir bekletme ilkesine atandığı zaman Facebook verileri korunur. İçerik Arama'yu kullanarak üçüncü taraf verilerde arama veya Facebook verilerinizin bir özel durumda depolandığı posta kutusunu bir özel dosya Advanced eDiscovery ilişkilendirilebilirsiniz. Facebook verilerini başka bir kuruluşta içeri aktarma ve Microsoft 365 bağlayıcı kullanmak, kuruma devlet ve mevzuat ilkeleriyle uyumlu kalmada yardımcı olabilir.

## <a name="prerequisites-for-setting-up-a-connector-for-facebook-business-pages"></a>Facebook İş sayfaları için bağlayıcı ayarlamanın önkoşulları

kuruluş Facebook İş sayfalarından verileri içeri aktaracak ve arşivleyen bir bağlayıcı Microsoft 365 uyumluluk merkezi önce aşağıdaki önkoşulları tamamlayın. 

- Kuruluşun iş sayfaları için bir Facebook hesabına ihtiyacınız vardır (bağlayıcıyı ayarlarken bu hesapta oturum açın). Şu anda yalnızca Facebook İş sayfalarından verileri arşivebilirsiniz; tek tek Facebook profillerinden veri arşivlemezsiniz.

- Kuruluşta geçerli bir Azure aboneliği olmalıdır. Mevcut Bir Azure aboneliğiniz yoksa, şu seçeneklerden biri için kaydolabilirsiniz:

    - [Ücretsiz bir yıllık Azure aboneliğine kaydolma](https://azure.microsoft.com/free)

    - [Olduğu Kadar Öde Azure aboneliğine kaydolma](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > Microsoft 365 [aboneliğinize](use-your-free-azure-ad-subscription-in-office-365.md) dahil olan ücretsiz Azure Active Directory aboneliği, oyun oyun bağlayıcılarını Microsoft 365 uyumluluk merkezi.

- Facebook Business sayfalarının bağlayıcısı, bir günde toplam 200.000 öğe içeri aktarabilirsiniz. Bir günde 200.000'den fazla Facebook İş öğesi varsa, bu öğelerin hiçbiri bu öğelere Microsoft 365.

- Bağlayıcı içinde özel bağlayıcıyı ayar eden kullanıcıya (5. adımda) Microsoft 365 uyumluluk merkezi'de Posta Kutusu İçeri/Dışarı Aktarma rolü atan Exchange Online. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>1. Adım: Azure Active Directory'de uygulama oluşturma

İlk adım, Azure Active Directory'a (yeni uygulama) yeni bir AAD. Bu uygulama, 4. Adımda ve Facebook bağlayıcısı için 5. Adımda gerçekleştirilen web uygulaması kaynağına karşılık karşılık gelen bir uygulamadır. 

Adım adım yönergeler için bkz. Mobil [Uygulamada uygulama Azure Active Directory](deploy-facebook-connector.md#step-1-create-an-app-in-azure-active-directory).

Bu adımın tamamlanması sırasında (önceki adım adım yönergeleri kullanarak), aşağıdaki bilgileri bir metin dosyasına kaydetebilirsiniz. Bu değerler dağıtım işleminin sonraki adımlarında kullanılır.

- AAD kimliği'ne tıklayın

- AAD gizli uygulama

- Kiracı Kimliği

## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>2. Adım: Bağlayıcı web hizmetini Azure GitHub doğru dağıtma

Sonraki adım, Facebook hesabınıza bağlanmak ve verileri ayıklamak için Facebook API'sini kullanan Facebook İş sayfaları bağlayıcı uygulamasının kaynak kodunu dağıtmak ve böylece bu kodu başka bir Microsoft 365. Organizasyonunız için dağıtan Facebook bağlayıcısı, Facebook İş sayfalarınıza bu adımda Depolama Azure Kurumsal'a öğeleri yükler. Microsoft 365 uyumluluk merkezi'ta bir Facebook iş sayfaları bağlayıcısı oluşturduktan sonra (5. Adımda), İçeri Aktarma hizmeti Azure Depolama konumdaki Facebook iş sayfaları verilerini Microsoft 365 posta kutusuna kopyalayacaktır. Önkoşullar bölümünde [de açıklanan gibi](#prerequisites-for-setting-up-a-connector-for-facebook-business-pages), Azure Depolama hesabı oluşturmak için geçerli bir Azure aboneliğiniz olmalıdır.

Adım adım yönergeler için bağlayıcı [web hizmetini Azure hesabınıza GitHub dağıtma bağlantısına bakın](deploy-facebook-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account).

Bu adımı tamamlamak için adım adım yönergelerde, aşağıdaki bilgileri sağlayacaksiniz:

- APISecretKey: Bu adımı tamamlarken bu gizliyi siz oluştururuz. 5. Adımda kullanılır.

- TenantId: 1. Adımda Microsoft 365 Facebook bağlayıcısı uygulamasını oluşturdukta kopyalanmış olan Azure Active Directory kiracı kimliği.

Bu adımı tamamladıktan sonra, Azure uygulama hizmeti URL'sini (örneğin, https://fbconnector.azurewebsites.net). 3. Adım, 4. Adım ve 5. Adım'a kadar bu URL'yi kullan gerekir).

## <a name="step-3-register-the-web-app-on-facebook"></a>3. Adım: Web uygulamasını Facebook'a kaydetme

Sonraki adım, Facebook'ta yeni bir uygulama oluşturmak ve yapılandırmak. 5. Adımda oluştursanız bile Facebook iş sayfaları bağlayıcısı, kuruluşun Facebook İş sayfalarından veri almak için Facebook API'si ile etkileşimde bulunmak için Facebook web uygulamasını kullanır.

Adım adım yönergeler için bkz. [Facebook uygulamasını kaydetme](deploy-facebook-connector.md#step-3-register-the-facebook-app).

Bu adımı tamamlandıktan sonra (adım adım yönergeleri izleyerek), aşağıdaki bilgileri bir metin dosyasına kaydedin. Bu değerler, Adım 4'te Facebook bağlayıcı uygulamasını yapılandırmak için kullanılır.

- Facebook uygulama kimliği

- Facebook uygulaması sırrı

- Facebook web sertifikalarını doğrulama belirteci

## <a name="step-4-configure-the-facebook-connector-app"></a>4. Adım: Facebook bağlayıcı uygulamasını yapılandırma

Sonraki adım, 1. Adımda Azure Web App kaynağını oluşturulduğunda karşıya yüklediğiniz Facebook bağlayıcı uygulamasına yapılandırma ayarları eklemektir. Bunu, bağlayıcı uygulamanız giriş sayfasına gidip yapılandırarak yapar.

Adım adım yönergeler için bkz. [Facebook bağlayıcı uygulamasını yapılandırma](archive-facebook-data-with-sample-connector.md#step-4-configure-the-facebook-connector-app).

Bu adımın tamamlanması sırasında (adım adım yönergeleri izleyerek), aşağıdaki bilgileri sağlar (önceki adımları tamamladıktan sonra metin dosyasına kopyaladıktan sonra):

- Facebook uygulaması kimliği (3. Adımda edinilen)

- Facebook uygulaması sırrı (3. Adımda elde edilir)

- Facebook web sertifikalarını doğrulama belirteci (3. Adımda elde edilir)

- Azure Active Directory kimliği (1. adımda AAD uygulama kimliği)

- Azure Active Directory gizlidir (1. adımda AAD gizli uygulama sırrı)

## <a name="step-5-set-up-a-facebook-business-pages-connector-in-the-microsoft-365-compliance-center"></a>5. Adım: Bağlantıda Facebook İş sayfaları bağlayıcısı Microsoft 365 uyumluluk merkezi

Son adım, bağlayıcıyı Facebook Microsoft 365 uyumluluk merkezi sayfalarınıza gelen verileri kendi posta kutusunda belirtilen bir posta kutusuna aktaracak şekilde Microsoft 365. Bu adımı tamamlandıktan sonra, Microsoft 365 Aktarma hizmeti Facebook Business sayfalarınıza verileri kendi Sitenize aktarmaya Microsoft 365.

Adım adım yönergeler için bkz. [5. Adım: Ekrandaki Facebook bağlayıcısı Microsoft 365 uyumluluk merkezi](deploy-facebook-connector.md#step-5-set-up-a-facebook-connector-in-the-microsoft-365-compliance-center). 

Bu adımın tamamlanması sırasında (adım adım yönergeleri izleyerek), aşağıdaki bilgileri sağlarsınız (adımları tamamladıktan sonra metin dosyasına kopyaladıktan sonra).

- AAD kodu (1. Adımda elde edilir)

- Azure uygulama hizmeti URL'si (1. Adım'da alınarak elde edilir; örneğin, https://fbconnector.azurewebsites.net)

- APISecretKey (2. Adımda oluşturduğunuz)