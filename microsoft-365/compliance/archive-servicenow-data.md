---
title: ServiceNow verilerini arşivlemek için bir bağlayıcı ayarlayın ve Microsoft 365
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
description: Yöneticiler ServiceNow verilerini Veritas'tan içeri aktaracak ve arşivleyecek bir bağlayıcı Microsoft 365. Bu bağlayıcı, iş yerinde üçüncü taraf veri kaynaklarından verileri Microsoft 365. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: 34cca3d8988f25a6082a8a000335a311343fc76d
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021537"
---
# <a name="set-up-a-connector-to-archive-servicenow-data"></a>ServiceNow verilerini arşivlemek için bağlayıcı ayarlama

ServiceNow platformundan kendi Microsoft 365 uyumluluk merkezi posta kutularına veri içeri aktararak bu platformdan verileri arşivlemek için, veri kaynağında bir Veritas Microsoft 365 kullanın. Veritas, üçüncü taraf veri kaynağından öğeleri yakalayan ve bu öğeleri başka bir öğeye aktaran bir [ServiceNow](https://globanet.com/servicenow/) Microsoft 365. Bağlayıcı, ServiceNow'dan canlı iletiler, ekler ve gönderiler gibi içeriği e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri e-posta kutusunda kullanıcı posta kutularına Microsoft 365.

ServiceNow verileri kullanıcı posta kutularında depolanıyorsa, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri gibi uyumluluk özelliklerini uygulayabilirsiniz. Bir ServiceNow bağlayıcısı kullanarak verileri başka bir kuruluşta içeri aktarın ve Microsoft 365, kurum kurum ve mevzuat ilkeleriyle uyumlu çalışmanıza yardımcı olabilir.

## <a name="overview-of-archiving-servicenow-data"></a>ServiceNow verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Aşağıdaki tabloda ServiceNow verilerini arşivlemek için bağlayıcı kullanma Microsoft 365.

![ServiceNow verileri için arşivleme iş akışı.](../media/ServiceNowConnectorWorkflow.png)

1. Your organization works with ServiceNow to set up and configure a ServiceNow site.

2. ServiceNow öğeleri her 24 saatte bir VeriTas Merge1 sitesine kopyalanır. Bağlayıcı, ServiceNow öğelerini de e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi'ta oluşturdukları ServiceNow bağlayıcısı her gün Veritas Birleştirme1 sitesine bağlanır ve ServiceNow içeriğini Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı, dönüştürülmüş öğeleri, 3. Adımda açıklandığı gibi otomatik kullanıcı eşlemesinde *E-posta* özelliğinin değerini kullanarak belirli kullanıcıların posta [kutularına içeri aktarıyor](#step-3-map-users-and-complete-the-connector-setup). Gelen Kutusu klasöründe, **ServiceNow** adlı bir alt klasör kullanıcı posta kutularında oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her ServiceNow öğesi, öğenin her katılımcılarının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için bir Merge1 hesabı oluşturun. Hesap oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://www.veritas.com/content/support/). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- ServiceNow hesabından veri getirmek için ServiceNow uygulaması oluşturun. Uygulamayı oluşturma hakkında adım adım yönergeler için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20ServiceNow%20User%20Guide%20.pdf).

- 1. Adımda ServiceNow bağlayıcısı oluşturan (ve 3. Adımda tamamlayan) kullanıcı, çalışma alanı içinde Posta Kutusu İçeri/Dışarı Aktarma rolüne atan Exchange Online. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-servicenow-connector"></a>1. Adım: ServiceNow bağlayıcıyı ayarlama

İlk adım, dosyanın Veri **Bağlayıcıları sayfasına erişmek ve ServiceNow** Microsoft 365 uyumluluk merkezi bir bağlayıcı oluşturmaktır.

1. Veri bağlayıcılarıServiceNow'a [https://compliance.microsoft.com](https://compliance.microsoft.com/) **gidin ve** >  **bu öğeye tıklayın**.

2. **ServiceNow ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-servicenow-on-the-veritas-merge1-site"></a>2. Adım: Veritas Merge1 sitesinde ServiceNow'ı yapılandırma

İkinci adım, Veritas Merge1 sitesinde ServiceNow bağlayıcısı yapılandırmaktır. ServiceNow bağlayıcısı yapılandırma hakkında daha fazla bilgi için bkz. [Merge1 Third-Party Connectors User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20ServiceNow%20User%20Guide%20.pdf).

Son Olarak Kaydet **& i** tıklatmanın ardından, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi sayfası görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve aşağıdaki adımları takip etmek için Microsoft 365 uyumluluk merkezi izleyin:

1. Map **ServiceNow users to Microsoft 365 sayfasında**, otomatik kullanıcı eşlemesini etkinleştirin. ServiceNow öğeleri, kurumdaki *kullanıcıların e-posta* adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcıya yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-servicenow-connector"></a>4. Adım: ServiceNow bağlayıcılarını izleme

ServiceNow bağlayıcıyı oluşturdukktan sonra, bağlayıcının durumunu hemen Microsoft 365 uyumluluk merkezi.

1. Sol gezinti [https://compliance.microsoft.com](https://compliance.microsoft.com/) çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve **ardından ServiceNow** bağlayıcıyı seçerek bağlayıcıyla ilgili özellikleri ve bilgileri içeren açılır sayfayı görüntüleyin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.