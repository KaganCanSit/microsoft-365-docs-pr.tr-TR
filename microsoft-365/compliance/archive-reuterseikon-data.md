---
title: Reuters E ayrıca verilerini aynı dosyada arşivlemek için bağlayıcı Microsoft 365
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
description: Yöneticiler Reuters E ayrıca, Veritas verilerini Kendi Veritas'ında içeri aktaracak ve arşivacak bir bağlayıcı Microsoft 365. Bu bağlayıcı, iş yerinde üçüncü taraf veri kaynaklarından verileri Microsoft 365. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: 9210467d390cf383795ea6b012c83b8b57bc6009
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021477"
---
# <a name="set-up-a-connector-to-archive-reuters-eikon-data"></a>Reuters E ekin verilerini arşivlemek için bağlayıcı ayarlama

Microsoft 365 uyumluluk merkezi'da Bir Veritas bağlayıcısı kullanarak Reuters E kutunuzdan kendi Microsoft 365 posta kutularına veri aktarın ve bu Microsoft 365 kullanın. Veritas, üçüncü taraf veri kaynağından (düzenli olarak) öğe yakalamak ve bu öğeleri üçüncü taraf veri kaynağına aktaracak şekilde yapılandırılmış bir [Reuters E ayrıca](https://globanet.com/eikon/) Microsoft 365. Bağlayıcı, bir kullanıcının Reuters E diski gibi içerikleri bir e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri Microsoft 365'da kullanıcının posta kutusuna aktarabilir.

Reuters Eclen verileri kullanıcı posta kutularında depolandığı için Mahkeme Microsoft 365, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Aynı kuruluşta verileri içeri ve arşivlemek için Reuters E ilgili bağlayıcısı Microsoft 365, kurum kurum ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-reuters-eikon-data"></a>Reuters E gereksinimleri verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Reuters E ayrıcanı verilerini şirket içinde arşivlemek için bağlayıcı kullanma Microsoft 365.

![Reuters Evrizi verileri için arşivleme iş akışı.](../media/ReutersEikonConnectorWorkflow.png)

1. Organizasyonunız Reuters E bu siteyi ayarlamak ve yapılandırmak için Reuters E bu siteyle çalışır.

2. Reuters E öğeleri 24 saatte bir Veritas Merge1 sitesine kopyalanır. Bağlayıcı aynı zamanda Reuters E ayrıca e-posta iletisi biçimine de dönüştürür.

3. Microsoft 365 uyumluluk merkezi'ta oluşturdukları Reuters E ilgili bağlayıcısı her gün Veritas Merge1 sitesine bağlanır ve içeriği Microsoft bulutunda güvenli bir Azure Depolama konuma aktarabilir.

4. Bağlayıcı, otomatik kullanıcı eşlemesinde E-posta özelliğinin değerini 3. Adımda açıklandığı gibi kullanarak  öğeleri belirli kullanıcıların posta [kutularına içeri aktarıyor](#step-3-map-users-and-complete-the-connector-setup). Kullanıcı posta kutularında **Reuters E ayrıcat** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her Reuters E bu özelliği içerir; bu özellik, öğenin tüm katılımcılarının e-posta adresiyle doldurulur.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için VeriTas Merge1 hesabı oluşturun. Hesap oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://globanet.com/ms-connectors-contact). 1. Adım'da bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- 1. Adımda Reuters E ayrıca bağlayıcısı oluşturan (ve 3. Adımda bu bağlayıcıyı tamamlayan) kullanıcı, Aynı Yıl içinde Posta Kutusu İçeri/Dışarı Aktarma rolüne atan Exchange Online. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol ilgili gruptaki bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-reuters-eikon-connector"></a>1. Adım: Reuters E ilgili bağlayıcıyı ayarlama

İlk adım, en son **sayfasındaki Veri Bağlayıcıları** sayfasına erişmek Microsoft 365 uyumluluk merkezi Reuters E herhangi bir veri için bağlayıcı oluşturmaktır.

1. Veri **bağlayıcılarıYeni'ye** > [https://compliance.microsoft.com](https://compliance.microsoft.com/) gidin **ve bu öğeye tıklayın**.

2. **Reuters E herhangi bir ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-reuters-eikon-connector-on-the-veritas-merge1-site"></a>2. Adım: Veritas Merge1 sitesinde Reuters E ayrıca bağlayıcıyı yapılandırma

İkinci adım, Merge1 sitesinde Reuters E bu bağlayıcıyı yapılandırmaktır. Veritas Merge1 sitesinde Reuters E belirli bir bağlayıcıyı yapılandırma hakkında bilgi için bkz. [Merge1 Third-Party Connectors Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Reuters%20Eikon%20User%20Guide%20.pdf).

Son Olarak Kaydet **& e tıklarken**, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve aşağıdaki adımları takip etmek için Microsoft 365 uyumluluk merkezi izleyin:

1. Dış kullanıcıları **kullanıcı eşleme Microsoft 365,** otomatik kullanıcı eşlemesini etkinleştirin. Reuters E bu öğeleri, kurumdaki kullanıcılar *için e-posta* adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcıya yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-reuters-eikon-connector"></a>4. Adım: Reuters E ilgili bağlayıcıyı izleme

Reuters E herhangi bir bağlayıcıyı oluşturduktan sonra bağlayıcının durumunu hemen Microsoft 365 uyumluluk merkezi.

1. Sol gezinti [https://compliance.microsoft.com](https://compliance.microsoft.com) çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve sonra açılır sayfayı **görüntülemek için Reuters E ilgili** bağlayıcıyı seçin. Bu sayfa, bağlayıcının özelliklerini ve bilgilerini içerir.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan veriler hakkında bilgi içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.