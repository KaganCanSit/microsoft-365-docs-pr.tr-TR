---
title: Metinle sınırlandırılmış verileri aynı dosyada arşivlemek için bağlayıcıyı Microsoft 365
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
description: Yöneticiler, verilerde yer alan metinle sınırlandırılmış verileri veri kaynağında içeri aktaracak ve bu verileri başka bir Microsoft 365. Bu bağlayıcı, iş yerinde üçüncü taraf veri kaynaklarından verileri Microsoft 365. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: 0d1175c51be57845f39d16b9522862b2d63d666c
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313251"
---
# <a name="set-up-a-connector-to-archive-text-delimited-data"></a>Metinle sınırlandırılmış verileri arşivlemek için bağlayıcı ayarlama

Metinle sınırlandırılmış verileri kendi Microsoft 365 uyumluluk merkezi posta kutularına içeri aktarmak ve arşivlemek için veri kaynağında bir Veritas Microsoft 365 kullanın. Veritas, [üçüncü](https://globanet.com/text-delimited) taraf bir veri kaynağından (düzenli olarak) öğe yakalamak ve bu öğeleri içeri aktararak veri kaynağına aktaracak şekilde yapılandırılmış bir metinle Microsoft 365. Bağlayıcı, metinle sınırlandırılmış veri kaynağından gelen içeriği e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri kendi posta kutusunda kullanıcının posta kutusuna Microsoft 365.

Metinle sınırlandırılmış veriler kullanıcı posta kutularında depolandıktan sonra, mahkeme Microsoft 365, eBulma, bekletme ilkeleri ve bekletme etiketleri gibi uyumluluk özelliklerini uygulayabilirsiniz. Verileri başka bir kuruluşta içeri aktararak veya arşivlerken metinle ayrılmış bir veri bağlayıcısı kullanmak Microsoft 365 kuruma devlet ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-the-text-delimited-data"></a>Metinle sınırlandırılmış verileri arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, bağlayıcı kullanarak metinle sınırlandırılmış kaynak bilgilerini arşivleme işlemi açık Microsoft 365.

![Metinle sınırlandırılmış veriler için iş akışı arşivleme.](../media/TextDelimitedConnectorWorkflow.png)

1. Organizasyonunız, metinle sınırlandırılmış bir siteyi ayarlamak ve yapılandırmak için metinle sınırlandırılmış kaynakla çalışır.

2. Her 24 saatte bir, metinle sınırlandırılmış kaynaktan gelen sohbet iletileri Veritas Birleştirme1 sitesine kopyalanır. Bağlayıcı, içeriği e-posta iletisi biçimine de dönüştürür.

3. Microsoft 365 uyumluluk merkezi'ta oluşturmakta olduğunuz metinle sınırlandırılmış bağlayıcı, her gün Veritas Birleştirme1 sitesine bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı, dönüştürülmüş ileti öğelerini, 3. Adımda açıklandığı gibi otomatik kullanıcı eşlemesinde E-posta özelliğinin değerini  kullanarak belirli kullanıcıların posta kutularına içeri aktarıyor. Kullanıcı posta kutularında Gelen Kutusu klasöründe **Metin -** Sınırlandırılmış adlı yeni bir alt klasör oluşturulur ve ileti öğeleri bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her iletide, her katılımcının e-posta adresiyle doldurulan bu özellik yer alır.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için VeriTas Merge1 hesabı oluşturun. Bu hesabı oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://globanet.com/ms-connectors-contact). 1. Adım'da bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- 1. Adımda metinle sınırlandırılmış bağlayıcıyı oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-text-delimited-connector"></a>1. Adım: Metinle sınırlandırılmış bağlayıcıyı ayarlama

İlk adım, ana sayfada Veri **Bağlayıcıları** sayfasına erişmek ve Microsoft 365 uyumluluk merkezi sınırlandırılmış veriler için bir bağlayıcı oluşturmaktır.

1. Veri bağlayıcılarıMetnli [https://compliance.microsoft.com](https://compliance.microsoft.com/) **Olarak Ayrılmış'a** >  **gidin ve bu öğeye tıklayın**.

2. Metinle **sınırlandırılmış ürün açıklaması sayfasında** Bağlayıcı ekle'ye **tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-text-delimited-connector-on-the-veritas-merge1-site"></a>2. Adım: VeriTas Merge1 sitesinde Metinle ayrılmış bağlayıcıyı yapılandırma

İkinci adım, Birleştirme1 sitesinde metinle ayrılmış bağlayıcıyı yapılandırmaktır. Veritas Birleştirme1 sitesinde metinle sınırlandırılmış bağlayıcıyı yapılandırma hakkında bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20text-delimited%20User%20Guide%20.pdf).

Son Olarak Kaydet **& e tıklarken**, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve aşağıdaki adımları takip etmek için Microsoft 365 uyumluluk merkezi izleyin:

1. Dış kullanıcıları **kullanıcı eşleme Microsoft 365,** otomatik kullanıcı eşlemesini etkinleştirin. Metin - Sınırlandırılmış kaynak öğeleri, kurumdaki kullanıcıların *e-posta* adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcıya yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-text-delimited-connector"></a>4. Adım: Metinle sınırlandırılmış bağlayıcıyı izleme

Metin - Sınırlandırılmış bağlayıcıyı oluşturdukta, bağlayıcının durumunu en son Microsoft 365 uyumluluk merkezi.

1. Sol gezinti [https://compliance.microsoft.com](https://compliance.microsoft.com) çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve sonra **da açılır** sayfayı görüntülemek için Metin - Sınırlandırılmış bağlayıcıyı seçin. Bu sayfa, bağlayıcının özelliklerini ve bilgilerini içerir.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan veriler hakkında bilgi içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.