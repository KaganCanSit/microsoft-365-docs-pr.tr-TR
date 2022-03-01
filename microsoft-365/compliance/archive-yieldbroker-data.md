---
title: Verimbroker verilerini aynı dosyada arşivlemek için bağlayıcı Microsoft 365
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
description: Yöneticiler, Veritas verilerinden Veribroker verilerini içeri aktarma ve arşivlemek için bir bağlayıcı Microsoft 365. Bu bağlayıcı, iş yerinde üçüncü taraf veri kaynaklarından verileri Microsoft 365. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: 8e7ed4034bf2c0d3805cc3896a5986aaddd99305
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021494"
---
# <a name="set-up-a-connector-to-archive-yieldbroker-data"></a>Ödemebroker verilerini arşivlemek için bağlayıcı ayarlama

Ödemebroker'dan kendi Microsoft 365 uyumluluk merkezi posta kutularına veri içeri aktarmak ve arşivlemek için veri kaynağında bir Veritas Microsoft 365 kullanın. Veritas size üçüncü taraf veri kaynağından öğeleri yakalamak ve bu öğeleri üçüncü taraf veri kaynağına aktaracak şekilde yapılandırılmış bir [Yieldbroker](https://globanet.com/yieldbroker/) bağlayıcısı Microsoft 365. Bağlayıcı, Yieldbroker'dan içeriği e-posta ileti biçimine dönüştürür ve sonra bu öğeleri Daha Sonra'da kullanıcının posta kutusuna Microsoft 365.

Yieldbroker kullanıcı posta kutularında depo edildikten sonra, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri gibi uyumluluk özelliklerini uygulayabilirsiniz. Aynı kuruluşta verileri içeri aktararak ve arşivlenen bir Yieldbroker bağlayıcısı kullanmak Microsoft 365 kuruluş ve mevzuat ilkeleriyle uyumlu çalışmanıza yardımcı olabilir.

## <a name="overview-of-archiving-yieldbroker-data"></a>Ödemebroker verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Verimbroker verilerini bir bağlayıcı kullanarak arşivleme işlemi Microsoft 365.

![Ödemebroker verileri için arşivleme iş akışı.](../media/YieldbrokerConnectorWorkflow.png)

1. Organizasyonunız, Bir ÖdemeBroker sitesi ayarlamak ve yapılandırmak için ÖdemeBroker ile çalışır.

2. Ödemebroker öğeleri her 24 saatte bir Veritas Birleştirme1 sitesine kopyalanır. Bağlayıcı, içeriği e-posta iletisi biçimine de dönüştürür.

3. Microsoft 365 uyumluluk merkezi'te oluşturmış olunan Yieldbroker bağlayıcısı, her gün Veritas Merge1 sitesine bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı, 3. Adımda açıklandığı gibi, otomatik kullanıcı eşlemesinde *E-posta* özelliğinin değerini kullanarak dönüştürülmüş ÖdemeBroker öğelerini belirli kullanıcıların posta [kutularına içeri aktarmaktadır](#step-3-map-users-and-complete-the-connector-setup). Kullanıcı posta kutularında **Yieldbroker** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her Yieldbroker, öğenin tüm katılımcılarının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için VeriTas Merge1 hesabı oluşturun. Hesap oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://www.veritas.com/content/support/). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 1. Adımda Yieldbroker bağlayıcısı oluşturan (ve 3. Adımda bu bağlayıcıyı tamamlayan) kullanıcı, Veri Kutusunda Posta Kutusu İçeri/Dışarı Aktarma rolüne atan Exchange Online. Bu rol, sayfanın veri bağlayıcıları sayfasında bağlayıcı eklemek Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-yieldbroker-connector"></a>1. Adım: Yieldbroker bağlayıcıyı ayarlama

İlk adım, ana sayfada Veri **Bağlayıcıları** sayfasına erişmek ve Ödeme Microsoft 365 uyumluluk merkezi bağlayıcısı oluşturmaktır.

1. Veri bağlayıcıları [https://compliance.microsoft.com](https://compliance.microsoft.com/) **ÖdemeBroker'e gidin ve** &gt; **bu öğeye tıklayın**.

2. **Ödemebroker ürün açıklaması** sayfasında Yeni bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-yieldbroker-connector-on-the-veritas-merge1-site"></a>2. Adım: Veritas Merge1 sitesinde Yieldbroker bağlayıcısı yapılandırma

İkinci adım, Merge1 sitesinde Yieldbroker bağlayıcısı yapılandırmaktır. ÖdemeBror'ünü yapılandırma hakkında bilgi için bkz. [Merge1 Third-Party Connectors User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Yieldbroker%20User%20Guide%20.pdf).

Son Olarak Kaydet **& e tıklarken**, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve bağlayıcı kurulumunu tamamlamak için şu adımları izleyin:

1. Map **Yieldbroker users to Microsoft 365 sayfasında**, otomatik kullanıcı eşlemesini etkinleştirin. Ödemebroker öğeleri, organizasyondaki *kullanıcıların* e-posta adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ne** tıklayın, ayarlarınızı gözden geçirin ve yeni **bağlayıcıya** yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-yieldbroker-connector"></a>4. Adım: ÖdemeBroker bağlayıcılarını izleme

Ödemebroker bağlayıcısı oluşturdukta, bağlayıcının durumunu bağlayıcının son Microsoft 365 uyumluluk merkezi.

1. Sol gezinti [https://compliance.microsoft.com](https://compliance.microsoft.com/) çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve ardından Bağlayıcı hakkında özellikleri ve bilgileri içeren açılır sayfayı görüntülemek için **Yieldbroker** bağlayıcısı öğesini seçin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.