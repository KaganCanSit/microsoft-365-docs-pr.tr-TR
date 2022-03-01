---
title: Her ikisinde de Zaman verilerini arşivlemek için bir bağlayıcı Microsoft 365
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
description: Yöneticiler, Veritas Her Gün bölümünden verileri içeri aktaracak ve arşivleyştiracak bir bağlayıcı Microsoft 365. Bu bağlayıcı, iş yerinde üçüncü taraf veri kaynaklarından verileri Microsoft 365. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: 308448087481affae6a1de430c49e084b9ac681b
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021467"
---
# <a name="set-up-a-connector-to-archive-symphony-data"></a>Zaman verilerini arşivlemek için bağlayıcıyı ayarlama

Dosyada bir Veritas bağlayıcısı kullanarak Microsoft 365 uyumluluk merkezi veya kuruluşlarda yer alan kullanıcı posta kutularına Aktar ve Arşivle Microsoft 365 kullanın. Bu, finans hizmetleri sektöründe kullanılan bir mesajlaşma ve işbirliği platformudur. Veritas, üçüncü [](https://globanet.com/symphony) taraf veri kaynağından (düzenli olarak Microsoft 365 uyumluluk merkezi öğeleri yakalayan ve sonra bu öğeleri kullanıcı posta kutularına aktaracak şekilde yapılandırılan bir Veri Kaynağı veri bağlayıcısı sağlar. Bağlayıcı, Öğenin içeriklerini Tarih hesabından e-posta iletisi biçimine dönüştürür ve öğeyi Daha sonra Bu hesapta bir posta kutusuna Microsoft 365.

After Lit communications are stored in user mailboxes, you can apply Microsoft 365 compliance features such such as Litigation Hold, eDiscovery, retention policies and retention labels, and communication compliance. Verileri başka bir kuruluşta içeri aktararak veya arşiv Microsoft 365 bir Öğe bağlayıcısı kullanmak, kurum kuruluş ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-symphony-data"></a>Skpye verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Iş için Microsoft'ta Communications iletişimini arşivlemek için veri bağlayıcısı Microsoft 365.

![Arşivleme iş akışı.](../media/SymphonyConnectorWorkflow.png)

1. Organizasyonun, Bir Siteyi Ayarlamak ve yapılandırmak için Oya ile birlikte çalışır.

2. Her 24 saatte bir, Mete'den gelen sohbet iletileri Veritas Birleştirme1 sitesine kopyalanır. Bağlayıcı, sohbet mesajının içeriğini de e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi'ta Microsoft 365 uyumluluk merkezi Bağlayıcısı, her gün Veritas Merge1 sitesine bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı, dönüştürülmüş ileti öğelerini, 3. Adımda açıklandığı gibi otomatik kullanıcı eşlemesinde E-posta özelliğinin değerini  kullanarak belirli kullanıcıların posta kutularına içeri aktarıyor. Kullanıcı posta kutularında Gelen Kutusu **klasöründeKimlik** adlı yeni bir alt klasör oluşturulur ve ileti öğeleri bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her sohbet iletisi, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için VeriTas Merge1 hesabı oluşturun. Hesap oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://globanet.com/ms-connectors-contact). 1. Adım'da bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- 1. Adımda Bağlayıcı bağlayıcıyı oluşturan (ve 3. Adımda tamamlayan) kullanıcı, gelen kutusunda Posta Kutusu İçeri/Dışarı Aktarma rolüne atan Exchange Online. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol ilgili gruptaki bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-symphony-connector"></a>1. Adım: Öğe bağlayıcıyı ayarlama

İlk adım, proje sayfasındaki **Veri Bağlayıcıları** sayfasına erişmek ve Microsoft 365 uyumluluk merkezi Verileri için bir bağlayıcı oluşturmaktır.

1. Veri bağlayıcılarıSym [https://compliance.microsoft.com](https://compliance.microsoft.com/) **hermesle'ye** >  gidin **ve bu öğeye tıklayın**.

2. Ürün açıklaması **sayfasında** Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="configure-the-symphony-connector-on-the-veritas-merge1-site"></a>Veritas Merge1 sitesinde Bağlayıcı bağlayıcıyı yapılandırma

İkinci adım, Merge1 sitesinde Kablo bağlayıcısı'nın yapılandırılmasıdır. Veritas Birleştirme1 sitesinde Kablo bağlayıcısını yapılandırma hakkında bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Symphony%20User%20Guide%20.pdf).

Son Olarak Kaydet **& e tıklarken**, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve aşağıdaki adımları takip etmek için Microsoft 365 uyumluluk merkezi izleyin:

1. Dış kullanıcıları **kullanıcı eşleme Microsoft 365,** otomatik kullanıcı eşlemesini etkinleştirin. Kalem öğeleri, kurumdaki kullanıcılar için *e-posta* adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcıya yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-symphony-connector"></a>4. Adım: Kablo bağlayıcılarını izleme

Bağlayıcıyı oluşturdukktan sonra, Bağlayıcının durumunu bağlayıcının hemen Microsoft 365 uyumluluk merkezi.

1. Sol gezinti [https://compliance.microsoft.com](https://compliance.microsoft.com) çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve sonra Bağlayıcı **bağlayıcıyı** seçerek açılır sayfayı görüntüleyin. Bu sayfa, bağlayıcının özelliklerini ve bilgilerini içerir.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan veriler hakkında bilgi içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.