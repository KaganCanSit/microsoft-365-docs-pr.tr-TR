---
title: Slack eKbulma verilerini aynı dosyada arşivlemek için bir bağlayıcı Microsoft 365
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
description: Yöneticiler, Veritas Slack eKbulma'dan veri içeri aktaracak ve bu verileri Microsoft 365. Bu bağlayıcı, iş yerinde üçüncü taraf veri kaynaklarından verileri Microsoft 365. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: 8369cc4ec14bece267febe57c1f7f6fdf22e4377
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021536"
---
# <a name="set-up-a-connector-to-archive-slack-ediscovery-data"></a>Slack eKbulma verilerini arşivlemek için bir bağlayıcı ayarlama

Sosyal medya, anlık ileti ve belge işbirliği platformlarından Microsoft 365 uyumluluk merkezi'daki posta kutularına üçüncü taraf verilerini içeri aktarma ve arşivlemek için veritas Microsoft 365 bağlayıcısı kullanın. Veritas, üçüncü taraf veri kaynağından (düzenli olarak) öğe yakalamak ve bu öğeleri düzenli olarak içeri aktaracak şekilde yapılandırılmış bir [Slack](https://globanet.com/slack/) bağlayıcısı Microsoft 365. Slack, Slack API'sine ileti ve dosya alır, bunları e-posta iletisi biçimine dönüştürür ve sonra öğeyi kullanıcı posta kutularına içeri aktarıyor.

Slack eBulma verileri kullanıcı posta kutularında depolandığı için, mahkeme Microsoft 365, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Slack bağlayıcısı kullanarak verileri kendi web'de içeri aktarın Microsoft 365 da, kurumnizin devlet ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-slack-ediscovery-data"></a>Slack eKbulma verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Aşağıdaki tabloda, Slack bilgilerini arşivlemek için bağlayıcı Microsoft 365.

![Slack arşivleme iş akışı.](../media/SlackConnectorWorkflow.png)

1. Organizasyonunız Slack sitesi ayarlamak ve yapılandırmak için Slack ile birlikte çalışıyor.

2. Slack eKbulma'dan gelen sohbet iletileri 24 saatte bir Veritas Merge1 sitesine kopyalanır. Bağlayıcı, sohbet mesajının içeriğini de e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi'te oluşturdukları Slack eKbulma bağlayıcısı, her gün Veritas Merge1 sitesine bağlanır ve sohbet iletilerini Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı, 3. Adımda açıklandığı gibi, E-posta özelliğinin ve otomatik kullanıcı eşleme değerini kullanarak dönüştürülmüş sohbet iletisi  öğelerini belirli kullanıcıların posta kutularına alır. Kullanıcı posta kutularında **Slack eKbulma** adlı Gelen Kutusu klasöründe yeni bir alt klasör oluşturulur ve sohbet iletisi öğeleri bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her sohbet iletisi bu özelliği içerir; bu özellik, sohbet iletisi her katılımcının e-posta adresiyle doldurulur.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için VeriTas Merge1 hesabı oluşturun. Hesap oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://globanet.com/ms-connectors-contact). 1. Adım'da bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- Kuruluşun Slack kurumsal hesabının kullanıcı adını ve parolasını alın. Slack'i yapılandırarak 2. Adımda bu hesapta oturum açın.

- 1. Adımda Slack eKbulma bağlayıcısı oluşturan (ve 3. Adımda bu bağlayıcıyı tamamlayan) kullanıcı, uygulama içinde Posta Kutusu İçeri/Dışarı Aktarma rolüne atan Exchange Online. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol ilgili gruptaki bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-slack-ediscovery-connector"></a>1. Adım: Slack eKbulma bağlayıcısı'nın ayarlama

İlk adım, ana sayfada Veri **Bağlayıcıları** sayfasına erişmek ve Slack Microsoft 365 uyumluluk merkezi için bir bağlayıcı oluşturmaktır.

1. Veri bağlayıcılarıSlack [https://compliance.microsoft.com](https://compliance.microsoft.com/)  > **eKbulma'ya gidin ve bu öğeye tıklayın**.

2. **Slack eBulma ürün açıklaması sayfasında** Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-slack-ediscovery"></a>2. Adım: Slack eKbulma'yi yapılandırma

İkinci adım, Merge1 sitesinde Slack eKbulma bağlayıcısı'nın yapılandırılmasıdır. Veritas Birleştirme1 sitesinde Slack eKbulma bağlayıcısı yapılandırma hakkında daha fazla bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Slack%20eDiscovery%20User%20Guide.pdf).

Son Olarak Kaydet **& e tıklarken**, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

1. Dış kullanıcıları **kullanıcı eşleme Microsoft 365,** otomatik kullanıcı eşlemesini etkinleştirin.

   Slack eBulma öğeleri, organizasyondaki *kullanıcıların* e-posta adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ne** tıklayın, ayarlarınızı gözden geçirin ve yeni **bağlayıcıya** yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-slack-ediscovery-connector"></a>4. Adım: Slack eKbulma bağlayıcılarını izleme

Slack eK bulma bağlayıcısı oluşturdukta, bağlayıcının durumunu çalışma Microsoft 365 uyumluluk merkezi.

1. Sol gezinti [https://compliance.microsoft.com](https://compliance.microsoft.com) çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve sonra çıkış sayfasını **görüntülemek için Slack eKızı** bağlayıcısı öğesini seçin. Bu sayfa, bağlayıcının özelliklerini ve bilgilerini içerir.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan veriler hakkında bilgi içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.