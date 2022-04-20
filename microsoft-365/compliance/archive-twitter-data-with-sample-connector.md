---
title: Twitter verilerini arşivleye bir bağlayıcı ayarlama
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: 04/08/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Yöneticilerin Twitter verilerini Microsoft 365 içeri aktarmak için yerel bağlayıcıyı nasıl ayarlayıp kullanabileceğini öğrenin.
ms.openlocfilehash: d025de04060184a6bd39fcef5ab68acdde65bc01
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64940565"
---
# <a name="set-up-a-microsoft-connector-to-archive-twitter-data-preview"></a>Twitter verilerini arşivleme (önizleme) için Bir Microsoft bağlayıcısı ayarlama

Twitter'dan Microsoft 365 verileri içeri aktarmak ve arşivlemek için Microsoft Purview uyumluluk portalında bir bağlayıcı kullanın. Bağlayıcıyı ayarlayıp yapılandırdıktan sonra, kuruluşunuzun Twitter hesabına bağlanır (zamanlanmış olarak), bir öğenin içeriğini e-posta iletisi biçimine dönüştürür ve ardından bu öğeleri Microsoft 365 bir posta kutusuna aktarır.

Twitter verileri içeri aktarıldıktan sonra, Twitter verilerine Dava Tutma, İçerik Arama, In-Place Arşivleme, Denetim ve Microsoft 365 bekletme ilkeleri gibi Microsoft Purview özelliklerini uygulayabilirsiniz. Örneğin, bir posta kutusu Dava Tutma'ya yerleştirildiğinde veya bir bekletme ilkesine atandığında Twitter verileri korunur. İçerik Arama'yı kullanarak üçüncü taraf verilerinde arama yapabilir veya Twitter verilerinin depolandığı posta kutusunu Microsoft Purview eKeşif (Premium) olayındaki bir koruyucuyla ilişkilendirebilirsiniz. Microsoft 365'da Twitter verilerini içeri aktarmak ve arşivlerken bağlayıcı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

Twitter verileri içeri aktarıldıktan sonra, posta kutusunda depolanan verilere Dava Tutma, İçerik Arama, In-Place Arşivleme, Denetim, İletişim uyumluluğu ve Microsoft 365 bekletme ilkeleri gibi Microsoft Purview özelliklerini uygulayabilirsiniz. Örneğin, İçerik Arama'yı kullanarak Twitter verilerinde arama yapabilir veya verilerin depolandığı posta kutusunu eBulma (Premium) durumundaki bir koruyucuyla ilişkilendirebilirsiniz. Microsoft 365'da Twitter verilerini içeri aktarmak ve arşivlerken bağlayıcı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

Uyumluluk portalında kuruluşunuzun Twitter hesabından verileri içeri aktaracak ve arşivleyen bir bağlayıcı ayarlamadan ve yapılandırmadan önce aşağıdaki önkoşulları tamamlayın.

- Kuruluşunuz için bir Twitter hesabına ihtiyacınız var; bağlayıcıyı ayarlarken bu hesapta oturum açmanız gerekir.

- Kuruluşunuzun geçerli bir Azure aboneliği olmalıdır. Mevcut bir Azure aboneliğiniz yoksa şu seçeneklerden birine kaydolabilirsiniz:

    - [Ücretsiz bir yıllık Azure aboneliğine kaydolma](https://azure.microsoft.com/free) 

    - [Kullandıkça Öde Azure aboneliğine kaydolma](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > [Microsoft 365 aboneliğinize](use-your-free-azure-ad-subscription-in-office-365.md) dahil olan ücretsiz Azure Active Directory aboneliği, uyumluluk portalındaki bağlayıcıları desteklemez.

- Twitter bağlayıcısı tek bir günde toplam 200.000 öğeyi içeri aktarabilir. Bir günde 200.000'den fazla Twitter öğesi varsa, bu öğelerin hiçbiri Microsoft 365 aktarılamaz.

- Uyumluluk portalında (5. Adımda) Twitter bağlayıcısını ayarlayan kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için [Microsoft Purview uyumluluk portalındaki İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>1. Adım: Azure Active Directory'de uygulama oluşturma

İlk adım, yeni bir uygulamayı Azure Active Directory'a (AAD) kaydetmektir. Bu uygulama, Twitter bağlayıcısı için 2. Adımda uyguladığınız web uygulaması kaynağına karşılık gelir.

Adım adım yönergeler için bkz. [Azure Active Directory'de uygulama oluşturma](deploy-twitter-connector.md#step-1-create-an-app-in-azure-active-directory).

Bu adımın tamamlanması sırasında (adım adım yönergeleri izleyerek) aşağıdaki bilgileri bir metin dosyasına kaydedersiniz. Bu değerler dağıtım işleminin sonraki adımlarında kullanılacaktır.

- uygulama kimliğini AAD

- Uygulama gizli dizi AAD

- Kiracı Kimliği

## <a name="step-2-deploy-connector-web-service-from-github-repository-to-your-azure-account"></a>2. Adım: Bağlayıcı web hizmetini GitHub deposundan Azure hesabınıza dağıtma

Sonraki adım, Twitter hesabınıza bağlanmak ve verileri Microsoft 365 içeri aktarabilmeniz için verileri ayıklamak için Twitter API'sini kullanacak Twitter bağlayıcı uygulamasının kaynak kodunu dağıtmaktır. Kuruluşunuz için dağıttığınız Twitter bağlayıcısı, öğeleri kuruluşunuzun Twitter hesabından bu adımda oluşturulan Azure Depolama konumuna yükler. Uyumluluk portalında bir Twitter bağlayıcısı oluşturduktan sonra (5. Adımda), Microsoft 365 İçeri Aktarma hizmeti Azure Depolama konumundaki Twitter verilerini Microsoft 365'daki bir posta kutusuna kopyalar. [Bağlayıcıyı ayarlamadan önce](#before-you-set-up-a-connector) bölümünde açıklandığı gibi, Azure Depolama hesabı oluşturmak için geçerli bir Azure aboneliğiniz olmalıdır.

Twitter bağlayıcı uygulamasının kaynak kodunu dağıtmak için:

1. [Bu GitHub sitesine](https://github.com/microsoft/m365-sample-twitter-connector-csharp-aspnet) gidin.

2. **Azure'a Dağıt'a** tıklayın.

Adım adım yönergeler için bkz. [Bağlayıcı web hizmetini GitHub Azure hesabınıza dağıtma](deploy-twitter-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account).

Bu adımı tamamlamak için adım adım yönergeleri izleseniz de aşağıdaki bilgileri sağlarsınız

- APISecretKey: Bu adımın tamamlanması sırasında bu gizli diziyi oluşturursunuz. 5. Adımda kullanılır.

- tenantId: 1. Adımda Azure Active Directory twitter uygulamasını oluşturduktan sonra kopyaladığınız Microsoft 365 kuruluşunuzun kiracı kimliği.

Bu adımı tamamladıktan sonra app Service URL'sini kopyaladığınızdan emin olun (örneğin, `https://twitterconnector.azurewebsites.net`). 3. Adım, Adım 4 ve 5. Adımı tamamlamak için bu URL'yi kullanmanız gerekir).

## <a name="step-3-create-developer-app-on-twitter"></a>3. Adım: Twitter'da geliştirici uygulaması oluşturma

Bir sonraki adım, Twitter'da bir geliştirici uygulaması oluşturmak ve yapılandırmaktır. 7. Adımda oluşturduğunuz özel bağlayıcı, kuruluşunuzun Twitter hesabından veri almak üzere Twitter API'siyle etkileşim kurmak için Twitter uygulamasını kullanır.

Adım adım yönergeler için bkz. [Twitter uygulamasını oluşturma](deploy-twitter-connector.md#step-3-create-the-twitter-app).

Bu adımın tamamlanması sırasında (adım adım yönergeleri izleyerek), aşağıdaki bilgileri bir metin dosyasına kaydedersiniz. Bu değerler, 4. Adımda Twitter bağlayıcı uygulamasını yapılandırmak için kullanılacaktır.

- Twitter API Anahtarı

- Twitter API Gizli Anahtarı

- Twitter Erişim Belirteci

- Twitter Erişim Belirteci Gizli Anahtarı

## <a name="step-4-configure-the-twitter-connector-app"></a>4. Adım: Twitter bağlayıcı uygulamasını yapılandırma

Sonraki adım, 2. Adımda dağıttığınız Twitter bağlayıcı uygulamasına yapılandırma ayarları eklemektir. Bunu, bağlayıcı uygulamanızın giriş sayfasına gidip yapılandırarak yaparsınız.

Adım adım yönergeler için bkz. [Bağlayıcı web uygulamasını yapılandırma](deploy-twitter-connector.md#step-4-configure-the-connector-web-app).

Bu adımın tamamlanması sırasında (adım adım yönergeleri izleyerek), aşağıdaki bilgileri (önceki adımları tamamladıktan sonra bir metin dosyasına kopyaladığınız) sağlayacaksınız:

- Twitter API Anahtarı (3. Adımda elde edilir)

- Twitter API Gizli Anahtarı (3. Adımda elde edilir)

- Twitter Erişim Belirteci (3. Adımda elde edilir)

- Twitter Erişim Belirteci Gizli Anahtarı (3. Adımda elde edilir)

- Azure Active Directory uygulama kimliği (1. Adımda alınan AAD uygulama kimliği)

- Azure Active Directory uygulama gizli dizisi (1. Adımda elde edilen AAD uygulama gizli dizisi)

## <a name="step-5-set-up-a-twitter-connector-in-the-compliance-portal"></a>5. Adım: Uyumluluk portalında Twitter bağlayıcısı ayarlama

Son adım, uyumluluk portalında kuruluşunuzun Twitter hesabından verileri Microsoft 365'deki belirli bir posta kutusuna aktaracak Twitter bağlayıcısını ayarlamaktır. Bu adımı tamamladıktan sonra İçeri Aktarma Microsoft 365 hizmeti kuruluşunuzun Twitter hesabından Microsoft 365 verileri içeri aktarmaya başlar.

Adım adım yönergeler için bkz. [Microsoft Purview uyumluluk portalında Twitter bağlayıcısı ayarlama](deploy-twitter-connector.md#step-5-set-up-a-twitter-connector-in-the-compliance-portal).

Bu adımın tamamlanması sırasında (adım adım yönergeleri izleyerek), aşağıdaki bilgileri (adımları tamamladıktan sonra bir metin dosyasına kopyaladığınız) sağlayacaksınız.

- Azure uygulama hizmeti URL'si (2. Adım'da elde edilir; örneğin, `https://twitterconnector.azurewebsites.net`)

- APISecretKey (2. Adımda oluşturduğunuz)