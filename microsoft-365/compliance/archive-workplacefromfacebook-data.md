---
title: çalışma yerinde Facebook verilerinden Çalışma Alanı'nın arşivini arşivlemek için bir bağlayıcı Microsoft 365
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
ms.collection: M365-security-compliance
description: Yöneticiler, Veritas'ın Merge1 sitesinde arşivlenen Facebook'tan Çalışma Yeri'ne verileri içeri aktarma ve arşivlemek için bir bağlayıcı Microsoft 365. Bağlayıcıyı ayarlama için Veritas ile çalışmanız gerekir Bu bağlayıcı, Microsoft 365'te üçüncü taraf veri kaynaklarından verileri arşivlemenize olanak sağlar ve böylece yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanarak kuruluş üçüncü taraf verilerini yönetebilirsiniz.
ms.openlocfilehash: ebf6f8f4aab2ac4290610458e10181d8e74181f2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63312271"
---
# <a name="set-up-a-connector-to-archive-workplace-from-facebook-data"></a>Facebook verilerinden Çalışma Alanı'nın arşivini arşivlemek için bağlayıcı ayarlama

İş Yerindeki verileri Facebook'tan Microsoft 365 uyumluluk merkezi kutusundan kendi Microsoft 365 posta kutularına içeri aktarmak ve arşivlemek için, çalışma Microsoft 365 kullanın. Veritas, üçüncü [taraf](https://globanet.com/workplace/) veri kaynağından öğeleri yakalamak (düzenli olarak) ve bu öğeleri diğer kullanıcılara aktaracak şekilde yapılandırılmış bir Facebook bağlayıcısı Microsoft 365. Bağlayıcı çalışma alanı'daki sohbetler, ekler, gönderiler ve videolar gibi içerikleri bir e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri çalışma alanı içinde kullanıcı posta kutularına Microsoft 365.

Çalışma alanı verileri kullanıcı posta kutularında depolendikten sonra, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Facebook bağlayıcısı'nın Çalışma Alanı'nın kullanarak verileri Microsoft 365 ve arşivle, kuruluş ilkeleriyle uyumlu çalışmanıza yardımcı olabilir.

## <a name="overview-of-archiving-workplace-from-facebook-data"></a>Facebook verilerinden Çalışma Alanı'nın arşivlenmesine genel bakış

Aşağıdaki genel bakış makalesinde, çalışma alanı veri kaynağında Çalışma alanı verilerini arşivlemek için bağlayıcı Microsoft 365.

![Facebook verilerinden Çalışma Alanı için iş akışı arşivleme.](../media/WorkplaceConnectorWorkflow.png)

1. Bir Çalışma Alanı sitesi ayarlamak ve yapılandırmak için, organizasyonun Facebook'tan Çalışma Alanı ile birlikte çalışıyor.

2. Her 24 saatte bir, Çalışma Alanı'nın öğeleri Veri Kaynağı Birleştirme1 sitesine kopyalanır. Bağlayıcı, bu öğelerin içeriğini de e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi'ta oluşturmakta olduğunu Facebook bağlayıcısı'nın Çalışma Alanı her gün Veri görev birleştirme1'e bağlanır ve Çalışma alanı öğelerini Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı, dönüştürülmüş öğeleri, 3. Adımda açıklandığı gibi otomatik kullanıcı eşlemesinde *E-posta* özelliğinin değerini kullanarak belirli kullanıcıların posta kutularına içeri aktarıyor. Facebook'tan Çalışma Alanı adlı Gelen Kutusu klasöründe  bir alt klasör oluşturulur ve Çalışma alanı öğeleri bu klasöre aktarılır. Bağlayıcı bunu, E-posta özelliğinin *değerini kullanarak* yapar. Her Çalışma alanı öğesi, her sohbet veya gönderi katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için VeriTas Merge1 hesabı oluşturun. Bu hesabı oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://globanet.com/ms-connectors-contact). 1. Adım'da bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- Uyumluluk ve eBulma https://my.workplace.com/work/admin/apps/ amacıyla API'ler aracılığıyla Workplace'dan veri almak için özel bir tümleştirme oluşturun.

   Tümleştirmeyi oluştururken, Çalışma Alanı platformu kimlik doğrulaması için kullanılan belirteçleri oluşturmak için kullanılan bir dizi benzersiz kimlik bilgisi üretir. Bu belirteçler, 2. Adım'da Facebook bağlayıcısı yapılandırma sihirbazının Çalışma Alanı'nda kullanılır. Uygulamaları oluşturma hakkında adım adım yönergeler için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Workplace%20from%20Facebook%20User%20Guide%20.pdf).

- 1. Adımda Facebook bağlayıcısı'nın Çalışma Alanı'sını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanıyor olması gerekir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-workplace-from-facebook-connector"></a>1. Adım: Facebook bağlayıcılarından Çalışma Alanı'nın ayarlama

İlk adım, çalışma sayfasındaki **Veri Bağlayıcıları** sayfasına erişmek ve çalışma Microsoft 365 uyumluluk merkezi için bir bağlayıcı oluşturmaktır.

1. Facebook'tan [https://compliance.microsoft.com](https://compliance.microsoft.com/) Veri **bağlayıcılarıSsık** >  **yeri'ne gidin ve bu öğesini tıklatın**.

2. Facebook ürün **açıklamasından çalışma alanı** sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-workplace-from-facebook-connector-on-the-veritas-merge1-site"></a>2. Adım: Veritas Birleştirme1 sitesinde Facebook'tan Çalışma Alanı bağlayıcıyı yapılandırma

İkinci adım, Birleştirme1 sitesinde Facebook'tan Çalışma Alanı bağlayıcısı'nın yapılandırılmasıdır. Facebook bağlayıcılarından Çalışma Alanı'nın yapılandırılması hakkında bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Workplace%20from%20Facebook%20User%20Guide%20.pdf).

Son Olarak Kaydet **& e tıklarken**, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve aşağıdaki adımları takip etmek için Microsoft 365 uyumluluk merkezi izleyin:

1. Dış kullanıcıları **kullanıcı eşleme Microsoft 365,** otomatik kullanıcı eşlemesini etkinleştirin. Çalışma alanı öğeleri, kurumdaki *kullanıcıların e-posta* adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcıya yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-workplace-from-facebook-connector"></a>4. Adım: Facebook bağlayıcılarından Çalışma Alanı'nın izlemesi

Facebook bağlayıcısı'nın Çalışma Alanı'nı oluşturduktan sonra, bağlayıcının durumunu çalışma Microsoft 365 uyumluluk merkezi.

1. Sol gezinti [https://compliance.microsoft.com](https://compliance.microsoft.com) çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve açılır sayfayı görüntülemek için **Facebook'tan** Çalışma Alanı bağlayıcısı'yı seçin. Bu sayfa, bağlayıcının özelliklerini ve bilgilerini içerir.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan veriler hakkında bilgi içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.