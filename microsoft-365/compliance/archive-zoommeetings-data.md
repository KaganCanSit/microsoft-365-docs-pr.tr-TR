---
title: Toplantı Yakınlaştırma verilerini aynı dosyada arşivlemek için bir bağlayıcı Microsoft 365
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
description: Yöneticiler, Veritas Zoom Toplantıları'larından verileri içeri aktarıp arşiv için bir bağlayıcı ayar Microsoft 365. Bu, üçüncü taraf veri kaynaklarından verileri Microsoft 365'te arşivlemenize olanak sağlar ve böylece yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanarak kuruluş üçüncü taraf verilerini yönetebilirsiniz.
ms.openlocfilehash: a616010349456cc7cba5c42d5a0a3bf5d4173d9a
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021561"
---
# <a name="set-up-a-connector-to-archive-zoom-meetings-data"></a>Yakınlaştırma Toplantıları verilerini arşivlemek için bağlayıcı ayarlama

Yakınlaştırma Toplantıları'Microsoft 365 uyumluluk merkezi kendi Microsoft 365 kutularına veri içeri aktarıp arşivlemek için görev sayfasında bir Veri Microsoft 365 kullanın. Veritas, [üçüncü taraf](https://globanet.com/zoom/) veri kaynağından (düzenli olarak) öğe yakalamak ve bu öğeleri belirli bir toplama kaynağına aktaracak şekilde yapılandırılmış bir Yakınlaştırma Toplantıları Microsoft 365. Bağlayıcı, Toplantıları Yakınlaştır hesabından toplantıların içeriğini (sohbetler, kayıtlı dosyalar ve meta veriler dahil) bir e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri Microsoft 365'ta kullanıcı posta kutularına içeri Microsoft 365.

Yakınlaştırma Toplantıları verileri kullanıcı posta kutularında depolanıyorsa, mahkeme Microsoft 365, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Verileri başka bir kuruluşta içeri aktarıp Microsoft 365 yakınlaştırma Toplantıları bağlayıcısı kullanmak, kurum kuruluş ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-zoom-meetings-data"></a>Toplantıları Yakınlaştırma verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Toplantıları Yakınlaştırma verilerini aynı dosyada arşivlemek için bağlayıcı Microsoft 365.

![Toplantıları arşivleme iş akışı.](../media/ZoomMeetingsConnectorWorkflow.png)

1. Organizasyonunız, yakınlaştırma Toplantıları sitesi ayarlamak ve yapılandırmak için Toplantılar'la birlikte çalışır.

2. Yakınlaştırma Toplantıları'nın toplantı öğeleri 24 saatte bir Veri Görev Birleştirme1 sitesine kopyalanır. Bağlayıcı toplantıların içeriğini de e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi'ta oluştursanız, Toplantılar Bağlayıcısı her gün Veri Görev Birleştirme1'e bağlanır ve toplantı iletilerini Microsoft bulutunda güvenli bir Azure Depolama konuma iletir.

4. Bağlayıcı, dönüştürülen toplantı öğelerini 3. Adımda açıklandığı gibi E-posta özelliğinin ve otomatik kullanıcı eşleme değerini  kullanarak belirli kullanıcıların posta kutularına içeri aktarmaktadır. Kullanıcı posta kutularında Gelen Kutusu klasöründe Yakınlaştır Toplantıları  adlı yeni bir alt klasör oluşturulur ve toplantı öğeleri bu klasöre aktarılır. Bağlayıcı bunu, E-posta özelliğinin *değerini kullanarak* yapar. Her toplantı öğesi, toplantının tüm katılımcılarının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için VeriTas Merge1 hesabı oluşturun. Bu hesabı oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://globanet.com/ms-connectors-contact). 1. Adım'da bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- Kuruluşun Yakınlaştırma İş veya Yakınlaştırma hesabı için kullanıcı adı ve Enterprise alın. Toplantıları Yakınlaştır bağlayıcısını yapılandırarak 2. Adımda bu hesapta oturum açın.

- Zoom Marketi'de aşağıdaki [uygulamaları oluşturun](https://marketplace.zoom.us):

  - OAuth uygulaması

  - JWT uygulaması

  Bu uygulamaları oluşturdukktan sonra, Yakınlaştırma platformu belirteçleri oluşturmak için kullanılan bir dizi benzersiz kimlik bilgisi üretir. Bu belirteçler, Yakınlaştırma hesabınıza bağlanıp öğeleri Birleştirme1 sitesine kopyalarken bağlayıcının kimliğini doğrulamak için kullanılır. 2. Adımda Yakınlaştırma bağlayıcısı yapılandırıldığında bu belirteçleri kullanıcaz.

  OAuth ve JWT uygulamalarını oluşturma hakkında adım adım yönergeler için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Zoom%20Meetings%20User%20Guide%20.pdf).

- 1. Adımda Toplantıları Yakınlaştır bağlayıcısı oluşturan (ve 3. Adımda tamamlayan) kullanıcı, toplantılarda Posta Kutusu İçeri/Dışarı Aktarma rolüne atan Exchange Online. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol ilgili gruptaki bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-zoom-meetings-connector"></a>1. Adım: Toplantıları Yakınlaştır bağlayıcıyı ayarlama

İlk adım, yakın zaman içinde **Veri Bağlayıcıları'Microsoft 365 uyumluluk merkezi** ve bir Yakınlaştırma Toplantıları bağlayıcısı oluşturmaktır.

1. Veri bağlayıcılarına [https://compliance.microsoft.com](https://compliance.microsoft.com/) gidin ve **bu öğeye** **tıklayınOom** >  Toplantıları.

2. Toplantıları **Yakınlaştır ürün** açıklaması sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-zoom-meetings-connector"></a>2. Adım: Toplantıları Yakınlaştır bağlayıcıyı yapılandırma

İkinci adım, Birleştirme1 sitesinde Toplantıları Yakınlaştır bağlayıcıyı yapılandırmaktır. Veritas Birleştirme1 sitesinde Toplantıları Yakınlaştır bağlayıcısı hakkında daha fazla bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Zoom%20Meetings%20User%20Guide%20.pdf).

Son Olarak Kaydet **& e tıklarken**, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

1. Dış kullanıcıları **kullanıcı eşleme Microsoft 365,** otomatik kullanıcı eşlemesini etkinleştirin.

   Yakınlaştırma Toplantıları öğeleri, kurumdaki kullanıcılar için *e-posta* adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır

2. **Sonraki'ne** tıklayın, ayarlarınızı gözden geçirin ve yeni **bağlayıcıya** yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-zoom-meetings-connector"></a>4. Adım: Toplantıları Yakınlaştır bağlayıcılarını izleme

Toplantıları Yakınlaştır bağlayıcısı oluşturdukta, bağlayıcının durumunu yakınlaştırılmış Microsoft 365 uyumluluk merkezi.

1. Sol gezinti [https://compliance.microsoft.com](https://compliance.microsoft.com) çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve açılır sayfayı **görüntülemek için** Toplantıları Yakınlaştır bağlayıcıyı seçin. Bu sayfa, bağlayıcının özelliklerini ve bilgilerini içerir.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan veriler hakkında bilgi içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.

- Toplantıları Yakınlaştır bağlayıcının çalışması için, Toplantıları Yakınlaştır özelliğini ayarlarken kayıtları etkinleştirmeniz gerekir.