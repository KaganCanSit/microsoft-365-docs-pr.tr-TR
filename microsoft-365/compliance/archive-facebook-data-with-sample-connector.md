---
title: Facebook verilerini arşivleyemek için bağlayıcı ayarlama
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
description: Microsoft Purview uyumluluk portalında bağlayıcıyı ayarlamayı & facebook iş sayfalarından Microsoft 365 & arşiv verilerini içeri aktarmayı öğrenin.
ms.openlocfilehash: 6db2bd474cd2920b4b067563377bbe85084aeeaf
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64947241"
---
# <a name="set-up-a-connector-to-archive-facebook-data-preview"></a>Facebook verilerini arşivleme (önizleme) için bağlayıcı ayarlama

Facebook business sayfalarından Microsoft 365 verileri içeri aktarmak ve arşivlemek için Microsoft Purview uyumluluk portalında bir bağlayıcı kullanın. Bağlayıcıyı ayarladıktan ve yapılandırdıktan sonra, Facebook İş sayfasına bağlanır (zamanlanmış olarak), Facebook öğelerinin içeriğini e-posta iletisi biçimine dönüştürür ve ardından bu öğeleri Microsoft 365 bir posta kutusuna aktarır.

Facebook verileri içeri aktarıldıktan sonra, Facebook verilerine Dava Tutma, İçerik Arama, In-Place Arşivleme, Denetim, İletişim uyumluluğu ve Microsoft 365 saklama ilkeleri gibi Microsoft Purview özelliklerini uygulayabilirsiniz. Örneğin, bir posta kutusu Dava Tutma'ya yerleştirildiğinde veya bir saklama ilkesine atandığında, Facebook verileri korunur. İçerik Arama'yı kullanarak üçüncü taraf verilerinde arama yapabilir veya Facebook verilerinin depolandığı posta kutusunu Microsoft Purview eKeşif (Premium) olayındaki bir koruyucuyla ilişkilendirebilirsiniz. Microsoft 365'da Facebook verilerini içeri aktarmak ve arşivlerken bağlayıcı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="prerequisites-for-setting-up-a-connector-for-facebook-business-pages"></a>Facebook business sayfaları için bağlayıcı ayarlama önkoşulları

Uyumluluk portalında kuruluşunuzun Facebook business sayfalarından verileri içeri aktaracak ve arşivleyen bir bağlayıcı ayarlamadan ve yapılandırmadan önce aşağıdaki önkoşulları tamamlayın. 

- Kuruluşunuzun iş sayfaları için bir Facebook hesabına ihtiyacınız vardır (bağlayıcıyı ayarlarken bu hesapta oturum açmanız gerekir). Şu anda yalnızca Facebook business sayfalarından verileri arşivleyebilirsiniz; verileri tek tek Facebook profillerinden arşivleyemezsiniz.

- Kuruluşunuzun geçerli bir Azure aboneliği olmalıdır. Mevcut bir Azure aboneliğiniz yoksa şu seçeneklerden birine kaydolabilirsiniz:

    - [Ücretsiz bir yıllık Azure aboneliğine kaydolma](https://azure.microsoft.com/free)

    - [Kullandıkça Öde Azure aboneliğine kaydolma](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > [Microsoft 365 aboneliğinize](use-your-free-azure-ad-subscription-in-office-365.md) dahil olan ücretsiz Azure Active Directory aboneliği, uyumluluk portalındaki bağlayıcıları desteklemez.

- Facebook Business sayfalarının bağlayıcısı tek bir günde toplam 200.000 öğeyi içeri aktarabilir. Bir günde 200.000'den fazla Facebook İş öğesi varsa, bu öğelerin hiçbiri Microsoft 365 aktarılamaz.

- Uyumluluk portalında (5. Adımda) özel bağlayıcıyı ayarlayan kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için [Microsoft Purview uyumluluk portalındaki İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>1. Adım: Azure Active Directory'de uygulama oluşturma

İlk adım, yeni bir uygulamayı Azure Active Directory'a (AAD) kaydetmektir. Bu uygulama, Facebook bağlayıcısı için 4. Ve 5. Adım'da uyguladığınız web uygulaması kaynağına karşılık gelir.

Adım adım yönergeler için bkz. [Azure Active Directory'de uygulama oluşturma](deploy-facebook-connector.md#step-1-create-an-app-in-azure-active-directory).

Bu adımın tamamlanması sırasında (önceki adım adım yönergeleri kullanarak) aşağıdaki bilgileri bir metin dosyasına kaydedersiniz. Bu değerler dağıtım işleminin sonraki adımlarında kullanılır.

- uygulama kimliğini AAD

- Uygulama gizli dizi AAD

- Kiracı Kimliği

## <a name="step-2-deploy-the-connector-web-service-from-github-to-your-azure-account"></a>2. Adım: Bağlayıcı web hizmetini GitHub Azure hesabınıza dağıtma

Bir sonraki adım, Facebook hesabınıza bağlanmak ve verileri Microsoft 365 içeri aktarabilmeniz için verileri ayıklamak için Facebook API'sini kullanacak Facebook business sayfaları bağlayıcı uygulamasının kaynak kodunu dağıtmaktır. Kuruluşunuz için dağıttığınız Facebook bağlayıcısı, Facebook İş sayfalarınızdaki öğeleri bu adımda oluşturulan Azure Depolama konumuna yükler. Uyumluluk portalında (5. Adımda) bir Facebook iş sayfaları bağlayıcısı oluşturduktan sonra İçeri Aktarma hizmeti, Facebook iş sayfaları verilerini Azure Depolama konumundan Microsoft 365 kuruluşunuzdaki bir posta kutusuna kopyalar. [Önkoşullar](#prerequisites-for-setting-up-a-connector-for-facebook-business-pages) bölümünde açıklandığı gibi, Azure Depolama hesabı oluşturmak için geçerli bir Azure aboneliğiniz olmalıdır.

Adım adım yönergeler için bkz. [Bağlayıcı web hizmetini GitHub Azure hesabınıza dağıtma](deploy-facebook-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account).

Bu adımı tamamlamak için adım adım yönergelerde aşağıdaki bilgileri sağlayacaksınız:

- APISecretKey: Bu adımın tamamlanması sırasında bu gizli diziyi oluşturursunuz. 5. Adımda kullanılır.

- TenantId: 1. Adımda Azure Active Directory'da Facebook bağlayıcı uygulamasını oluşturduktan sonra kopyaladığınız Microsoft 365 kuruluşunuzun kiracı kimliği.

Bu adımı tamamladıktan sonra Azure app service URL'sini (örneğin, https://fbconnector.azurewebsites.net)) kopyaladığınızdan emin olun. 3. Adım, Adım 4 ve 5. Adımı tamamlamak için bu URL'yi kullanmanız gerekir).

## <a name="step-3-register-the-web-app-on-facebook"></a>3. Adım: Web uygulamasını Facebook'a kaydetme

Sonraki adım, Facebook'ta yeni bir uygulama oluşturup yapılandırmaktır. 5. Adımda oluşturduğunuz Facebook iş sayfaları bağlayıcısı, kuruluşunuzun Facebook İş sayfalarından veri almak üzere Facebook API'siyle etkileşim kurmak için Facebook web uygulamasını kullanır.

Adım adım yönergeler için bkz. [Facebook uygulamasını kaydetme](deploy-facebook-connector.md#step-3-register-the-facebook-app).

Bu adımın tamamlanması sırasında (adım adım yönergeleri izleyerek), aşağıdaki bilgileri bir metin dosyasına kaydedersiniz. Bu değerler, 4. Adımda Facebook bağlayıcı uygulamasını yapılandırmak için kullanılır.

- Facebook uygulama kimliği

- Facebook uygulama gizli dizisi

- Facebook web kancaları doğrulama belirteci

## <a name="step-4-configure-the-facebook-connector-app"></a>4. Adım: Facebook bağlayıcı uygulamasını yapılandırma

Sonraki adım, 1. Adımda Azure web uygulaması kaynağını oluştururken karşıya yüklediğiniz Facebook bağlayıcı uygulamasına yapılandırma ayarları eklemektir. Bunu, bağlayıcı uygulamanızın giriş sayfasına gidip yapılandırarak yaparsınız.

Adım adım yönergeler için bkz. [Facebook bağlayıcı uygulamasını yapılandırma](archive-facebook-data-with-sample-connector.md#step-4-configure-the-facebook-connector-app).

Bu adımın tamamlanması sırasında (adım adım yönergeleri izleyerek), aşağıdaki bilgileri (önceki adımları tamamladıktan sonra bir metin dosyasına kopyaladığınız) sağlarsınız:

- Facebook uygulama kimliği (3. Adımda elde edilir)

- Facebook uygulama gizli dizisi (3. Adımda elde edildi)

- Facebook web kancaları doğrulama belirteci (3. Adımda elde edilir)

- Azure Active Directory uygulama kimliği (1. Adımda alınan AAD uygulama kimliği)

- Azure Active Directory uygulama gizli dizisi (1. Adımda elde edilen AAD uygulama gizli dizisi)

## <a name="step-5-set-up-a-facebook-business-pages-connector-in-the-compliance-portal"></a>5. Adım: Uyumluluk portalında Facebook Business sayfaları bağlayıcısı ayarlama

Son adım, uyumluluk portalında Facebook business sayfalarınızdaki verileri Microsoft 365'daki belirli bir posta kutusuna aktaracak bağlayıcıyı ayarlamaktır. Bu adımı tamamladıktan sonra, İçeri Aktarma Microsoft 365 hizmeti Facebook business sayfalarınızdaki verileri Microsoft 365 aktarmaya başlar.

Adım adım yönergeler için bkz. [Uyumluluk portalında 5. Adım: Facebook bağlayıcısı ayarlama](deploy-facebook-connector.md#step-5-set-up-a-facebook-connector-in-the-compliance-portal).

Bu adımın tamamlanması sırasında (adım adım yönergeleri izleyerek), aşağıdaki bilgileri (adımları tamamladıktan sonra bir metin dosyasına kopyaladığınız) sağlarsınız.

- AAD uygulama kimliği (1. Adımda elde edilir)

- Azure uygulama hizmeti URL'si (1. Adımda elde edilir; örneğin, https://fbconnector.azurewebsites.net)

- APISecretKey (2. Adımda oluşturduğunuz)
