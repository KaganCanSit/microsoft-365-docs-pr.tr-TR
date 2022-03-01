---
title: Twitter verilerini arşivlemek için bağlayıcı ayarlama
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
description: Yöneticilerin Twitter verilerini yerel bir bağlayıcıya aktaracak yerel bir bağlayıcı ayarlamayı ve bu bağlayıcıyı Microsoft 365.
ms.openlocfilehash: 0be302a3e26b92ff08941720fad57b811922de3c
ms.sourcegitcommit: b1a2b09edbcfcc62ff3f1ecf5bd8adb1afa344c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2021
ms.locfileid: "63019142"
---
# <a name="set-up-a-microsoft-connector-to-archive-twitter-data-preview"></a>Twitter verilerini arşivlemek için bir Microsoft bağlayıcısı ayarlama (önizleme)

Twitter'dan twitter'Microsoft 365 uyumluluk merkezi verileri içeri aktarma ve arşivlemek için aşağıdaki bağlantı Microsoft 365. Bağlayıcıyı ayardikten ve yapılandırdikten sonra, bağlayıcı, kuruluş Twitter hesabına bağlanır (zamanlanmış bir şekilde), öğenin içeriğini e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri Microsoft 365'ta bir posta kutusuna dönüştürür.

Twitter verileri aktarıldıktan sonra, Twitter verilerine Microsoft 365 Saklama, İçerik Araması, In-Place Arşivleme, Denetim ve bekletme Microsoft 365 gibi uyumluluk özelliklerini uygulayabilirsiniz. Örneğin, posta kutusu Mahkeme Tutma'ya yerleştirilse veya bir bekletme ilkesine atansa, Twitter verileri korunur. İçerik Arama'yu kullanarak üçüncü taraf verilerde arama veya Twitter verilerinizin depolandığı posta kutusunu bir özel olayda bir özel dosyayla Advanced eDiscovery sabilirsiniz. Twitter verilerini aynı dosyada içeri aktarma ve arşivlemek için bağlayıcı Microsoft 365, kurum kurum ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

Twitter verileri alındıktan sonra, posta kutusunda depolanan verilere Microsoft 365 Bekletme, İçerik Araması, In-Place Arşivleme, Denetim, İletişim uyumluluğu Microsoft 365 bekletme ilkeleri gibi Microsoft 365 uyumluluk özelliklerini uygulayabilirsiniz. Örneğin, İçerik Arama'yu kullanarak Twitter verisinde arama veya verilerin depolandığı posta kutusunu bir özel durum durumunda bir koruyucuyla Advanced eDiscovery edebilirsiniz. Twitter verilerini aynı dosyada içeri aktarma ve arşivlemek için bağlayıcı Microsoft 365, kurum kurum ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

Kuruluş Twitter hesabından verileri içeri aktaracak ve arşivleyen bir bağlayıcı Microsoft 365 uyumluluk merkezi önce aşağıdaki önkoşulları tamamlayın.

- Hesabınız için bir Twitter hesabına ihtiyacınız vardır; bağlayıcıyı ayarlarken bu hesapta oturum açmanız gerekir.

- Kuruluşta geçerli bir Azure aboneliği olmalıdır. Mevcut Bir Azure aboneliğiniz yoksa, şu seçeneklerden biri için kaydolabilirsiniz:

    - [Ücretsiz bir yıllık Azure aboneliğine kaydolma](https://azure.microsoft.com/free) 

    - [Olduğu Kadar Öde Azure aboneliğine kaydolma](https://azure.microsoft.com/pricing/purchase-options/pay-as-you-go/)

    > [!NOTE]
    > Microsoft 365 [aboneliğinize](use-your-free-azure-ad-subscription-in-office-365.md) dahil olan ücretsiz Azure Active Directory aboneliği, oyun oyun bağlayıcılarını Microsoft 365 uyumluluk merkezi.

- Twitter bağlayıcısı, bir günde toplam 200.000 öğeyi içeri aktarabilirsiniz. Bir günde 200.000'den fazla Twitter öğesi varsa, bu öğelerden hiçbiri başka bir Microsoft 365.

- Twitter bağlayıcısı ayar yapan kullanıcıya Microsoft 365 uyumluluk merkezi (Adım 5'te) Twitter bağlayıcısında Posta Kutusu İçeri/Dışarı Aktarma rolü Exchange Online. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

## <a name="step-1-create-an-app-in-azure-active-directory"></a>1. Adım: Azure Active Directory'de uygulama oluşturma

İlk adım, Azure Active Directory'a (yeni uygulama) yeni bir AAD. Bu uygulama, Twitter bağlayıcısı için 2. Adımda gerçekleştirdiği web uygulaması kaynağına karşılık geliyor.

Adım adım yönergeler için bkz. Mobil [Uygulamada uygulama Azure Active Directory](deploy-twitter-connector.md#step-1-create-an-app-in-azure-active-directory).

Bu adımın tamamlanması sırasında (adım adım yönergeleri izleyerek), aşağıdaki bilgileri bir metin dosyasına kaydedecektir. Bu değerler dağıtım işleminin sonraki adımlarında kullanılacaktır.

- AAD kimliği'ne tıklayın

- AAD gizli uygulama

- Kiracı Kimliği

## <a name="step-2-deploy-connector-web-service-from-github-repository-to-your-azure-account"></a>2. Adım: Bağlayıcı web hizmetini GitHub depodan Azure hesabınıza dağıtma

Sıradaki adım, Twitter hesabınıza bağlanmak için Twitter API'sini kullanan Twitter bağlayıcı uygulamasının kaynak kodunu dağıtmak ve verileri ayıklayın, böylece bu kodu Başka bir Microsoft 365. Organizasyonunız için dağıtım yapan Twitter bağlayıcısı, bu adımda oluşturulmuş olan Azure Depolama hesabını, kuruluşun Twitter hesabından öğeleri karşıya yükler. Microsoft 365 uyumluluk merkezi'ta Twitter bağlayıcısı oluşturduktan sonra (5. Adımda), Microsoft 365 İçeri Aktarma hizmeti Azure Depolama konumdaki Twitter verilerini Microsoft 365'te bir posta kutusuna Microsoft 365. Daha önce Bağlayıcı ayarlamadan [önce bölümünde açıklanan](#before-you-set-up-a-connector) gibi, Azure Depolama hesabı oluşturmak için geçerli bir Azure aboneliğiniz olmalıdır.

Twitter bağlayıcı uygulamasının kaynak kodunu dağıtmak için:

1. Bu [GitHub gidin](https://github.com/microsoft/m365-sample-twitter-connector-csharp-aspnet).

2. **Azure'a Dağıt'a tıklayın**.

Adım adım yönergeler için bağlayıcı [web hizmetini Azure hesabınıza GitHub dağıtma bağlantısına bakın](deploy-twitter-connector.md#step-2-deploy-the-connector-web-service-from-github-to-your-azure-account).

Bu adımı tamamlamak için adım adım yönergeleri takip ederken, aşağıdaki bilgileri sağlar

- APISecretKey: Bu adımı tamamlarken bu gizliyi siz oluştururuz. 5. Adımda kullanılır.

- tenantId: 1. Adımda Microsoft 365 Twitter uygulamasını oluşturdukta kopyalanmış olan Azure Active Directory kiracı kimliği.

Bu adımı tamamladıktan sonra, uygulama Hizmeti URL'sini (örneğin, ) kopyaladıktan emin olun `https://twitterconnector.azurewebsites.net`. 3. Adım, 4. Adım ve 5. Adım'a kadar bu URL'yi kullan gerekir).

## <a name="step-3-create-developer-app-on-twitter"></a>3. Adım: Twitter'da geliştirici uygulaması oluşturma

Bir sonraki adım, Twitter'da bir geliştirici uygulaması oluşturmak ve yapılandırmak. 7. Adımda oluştursanız da özel bağlayıcı, twitter API'si ile etkileşimde bulunmak için Twitter uygulamasını kullanarak kurumnizin Twitter hesabından veri edinebilirsiniz.

Adım adım yönergeler için bkz. [Twitter uygulaması oluşturma](deploy-twitter-connector.md#step-3-create-the-twitter-app).

Bu adımı tamamlandıktan sonra (adım adım yönergeleri izleyerek), aşağıdaki bilgileri bir metin dosyasına kaydedin. Bu değerler, 4. Adımda Twitter bağlayıcı uygulamasını yapılandırmak için kullanılır.

- Twitter API Anahtarı

- Twitter API Gizli Anahtarı

- Twitter Erişim Belirteci

- Twitter Erişim Belirteci Sırrı

## <a name="step-4-configure-the-twitter-connector-app"></a>4. Adım: Twitter bağlayıcı uygulamasını yapılandırma

Sonraki adım, 2. Adımda dağıttıkları Twitter bağlayıcı uygulamasına yapılandırma ayarları eklemektir. Bunu, bağlayıcı uygulamanız giriş sayfasına gidip yapılandırarak yapar.

Adım adım yönergeler için bkz. [Bağlayıcı web uygulamasını yapılandırma](deploy-twitter-connector.md#step-4-configure-the-connector-web-app).

Bu adımın tamamlanması sırasında (adım adım yönergeleri izleyerek), aşağıdaki bilgileri (önceki adımları tamamladıktan sonra bir metin dosyasına kopyaladıktan) sağlayacaktır:

- Twitter API Anahtarı (3. Adımda edinilen)

- Twitter API Gizli Anahtarı (3. Adımda edinilen)

- Twitter Erişim Belirteci (3. Adımda edinilen)

- Twitter Erişim Belirteci Sırrı (3. Adımda alınmıştır)

- Azure Active Directory kimliği (1. adımda AAD uygulama kimliği)

- Azure Active Directory gizlidir (1. adımda AAD gizli uygulama sırrı)

## <a name="step-5-set-up-a-twitter-connector-in-the-microsoft-365-compliance-center"></a>5. Adım: İçerik bağlantılarında Twitter bağlayıcısı Microsoft 365 uyumluluk merkezi

Son adım, twitter bağlayıcınızı, Microsoft 365 uyumluluk merkezi'te, kuruluşun Twitter hesabından belirli bir posta kutusuna veri aktaracak şekilde ayarlamak Microsoft 365. Bu adımı tamamlandıktan sonra, Microsoft 365 Aktarma hizmeti, organizasyon un Twitter hesabından verileri Kendi Posta'ya aktarmaya Microsoft 365.

Adım adım yönergeler için aşağıdaki Bağlantıda [Twitter bağlayıcısı Microsoft 365 uyumluluk merkezi](deploy-twitter-connector.md#step-5-set-up-a-twitter-connector-in-the-microsoft-365-compliance-center). 

Bu adımın tamamlanması sırasında (adım adım yönergeleri izleyerek), aşağıdaki bilgileri (adımları tamamladıktan sonra bir metin dosyasına kopyaladıktan) sağlayacaksınız.

- Azure uygulama hizmeti URL'si (2. Adım'da edinilen; örneğin, `https://twitterconnector.azurewebsites.net`)

- APISecretKey (2. Adımda oluşturduğunuz)