---
title: Twitter verilerini aynı dosyada arşivlemek için bağlayıcı Microsoft 365
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
description: Yöneticiler Twitter verilerini Veritas'tan Yeni Görev'e aktaracak ve arşivleyacak bir Microsoft 365. Bu bağlayıcı, iş yerinde üçüncü taraf veri kaynaklarından verileri Microsoft 365. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal saklama, eKbulma ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: 294dd933025c688e425badb6594c1aff968a9434
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021464"
---
# <a name="set-up-a-connector-to-archive-twitter-data-preview"></a>Twitter verilerini arşivlemek için bağlayıcı ayarlama (önizleme)

Twitter platformundan kendi Microsoft 365 uyumluluk merkezi posta kutularına veri içeri aktarma ve bu dosyaları arşivlemek için, aşağıdaki bağlantıda bir Veritas Microsoft 365 kullanın. Veritas, üçüncü taraf bir veri kaynağından öğeleri yakalamak ve bu öğeleri üçüncü taraf bir veri kaynağına aktaracak şekilde yapılandırılmış bir [Twitter](https://www.veritas.com/insights/merge1/twitter) Microsoft 365. Bağlayıcı Tweet'ler, hafta sonları ve Twitter'dan gelen yorumlar gibi içerikleri e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri Microsoft 365'ta kullanıcı posta kutularına aktarıyor.

Twitter verileri kullanıcı posta kutularında depolanıyorsa, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri gibi uyumluluk özelliklerini uygulayabilirsiniz. Twitter bağlayıcısı kullanarak verileri başka bir kuruluşta içeri aktarın Microsoft 365 arşivler, kuruluş ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-twitter-data"></a>Twitter verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Twitter verilerini aynı dosyada arşivlemek için bağlayıcı Microsoft 365.

![Twitter verileri için iş akışı arşivleme.](../media/VeritasTwitterConnectorWorkflow.png)

1. Twitter sitesi ayarlamak ve yapılandırmak için, twitter ile birlikte çalışıyor. Ayrıca, organizasyonunız Birleştirme1 sitesi ayarlamak için Veritas ile de çalışır.

2. Her 24 saatte bir, Twitter öğeleri VeriTas Merge1 sitesine kopyalanır. Bağlayıcı, Twitter öğelerini de e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi'ta Microsoft 365 uyumluluk merkezi Twitter bağlayıcısı, her gün Veritas Merge1 sitesine bağlanır ve Twitter içeriğini Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı, dönüştürülmüş öğeleri, 3. Adımda açıklandığı gibi otomatik kullanıcı eşlemesinde *E-posta* özelliğinin değerini kullanarak belirli kullanıcıların posta [kutularına içeri aktarıyor](#step-3-map-users-and-complete-the-connector-setup). Kullanıcı posta kutularında Twitter **adlı Gelen Kutusu** klasöründe bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her Twitter öğesi, öğenin tüm katılımcılarının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir Merge1 hesabı oluşturun. Bu hesabı oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://www.veritas.com/form/requestacall/ms-connectors-contact). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- Twitter hesabınızdan veri getirmek <https://developer.twitter.com> için Twitter uygulaması oluşturun. Uygulamayı oluşturma hakkında adım adım yönergeler için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Twitter%20User%20Guide.pdf).

- 1. Adımda YouTube bağlayıcısı oluşturan (ve 3. Adımda bunu tamamlayan) kullanıcı, YouTube'da Posta Kutusu İçeri/Dışarı Aktarma rolüne atan Exchange Online. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-twitter-connector"></a>1. Adım: Twitter bağlayıcıyı ayarlama

İlk adım, sayfanın en son **sayfasındaki Veri Bağlayıcıları** sayfasına erişmek Microsoft 365 uyumluluk merkezi Twitter verileri için bir bağlayıcı oluşturmaktır.

1. Veri bağlayıcılarıT <https://compliance.microsoft.com> herhangi **bir öğeye** >  **gidin ve bu öğeye tıklayın**.

2. Twitter ürün **açıklaması** sayfasında Bağlayıcı ekle'ye **tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-twitter-on-the-veritas-merge1-site"></a>2. Adım: VeriTas Merge1 sitesinde Twitter'ı yapılandırma

İkinci adım, Veritas Merge1 sitesinde Twitter bağlayıcıyı yapılandırmaktır. Twitter bağlayıcısı yapılandırma hakkında daha fazla bilgi için bkz. [Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu'larını Birleştirme](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Twitter%20User%20Guide.pdf).

Son Olarak Kaydet **& i** tıklatmanın ardından, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi sayfası görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve aşağıdaki adımları takip etmek için Microsoft 365 uyumluluk merkezi izleyin:

1. **Twitter kullanıcılarını kullanıcılarını kullanıcı Microsoft 365 sayfasında**, otomatik kullanıcı eşlemesini etkinleştirin. Twitter öğeleri, kurumdaki kullanıcılar için *e-posta* adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcıya yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-twitter-connector"></a>4. Adım: Twitter bağlayıcılarını izleme

Twitter bağlayıcınızı oluşturdukta, bağlayıcının durumunu ilgili bağlayıcının Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com/> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve **Ardından Twitter** bağlayıcısı'nın özelliklerini ve bağlayıcı hakkında bilgileri içeren açılır sayfayı görüntülemek için Seçin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
