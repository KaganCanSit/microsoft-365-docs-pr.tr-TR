---
title: XSLT/XML verilerini aynı dosyada arşivlemek için bağlayıcıyı Microsoft 365
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
description: Yöneticiler, XSLT/XML verilerini veritas biçiminde içeri aktaracak ve arşivleyabilecek bir bağlayıcı Microsoft 365. Bu bağlayıcı, üçüncü taraf veri kaynaklarından verileri Microsoft 365'te arşivlemenize olanak sağlar ve böylece yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanarak kuruluş üçüncü taraf verilerini yönetebilirsiniz.
ms.openlocfilehash: 6a34ab696fe2da6bd316e2a2da66b8b1cf0f9b6b
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021418"
---
# <a name="set-up-a-connector-to-archive-xsltxml-data"></a>XSLT/XML verilerini arşivlemek için bağlayıcı ayarlama

Web sayfası kaynağından verileri kendi Microsoft 365 uyumluluk merkezi kutunuzda kullanıcı posta kutularına içeri aktarmak ve arşivlemek için, veri kaynağında bir Veri Microsoft 365 kullanın. Veritas size, XML dosyalarını Microsoft 365'e aktarabilecek diğer dosya biçimlerine (HTML veya metin gibi) dönüştürmek için XSLT (Genişletilebilir Stil sayfası Dil Dönüşümleri) kullanılarak oluşturulan dosyaların hızlı bir şekilde geliştirilmesini sağlayan bir [XSLT/XML](https://globanet.com/xslt-xml) bağlayıcısı Microsoft 365. Bağlayıcı, XSLT/XML kaynağından bir öğenin içeriğini e-posta iletisi biçimine dönüştürür ve sonra dönüştürülmüş öğeyi Microsoft 365 alır.

XSLT/XML verileri kullanıcı posta kutularında depo olduktan sonra, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri gibi uyumluluk özelliklerini uygulayabilirsiniz. Verileri başka bir kuruluşta içeri aktararak ve arşivlerken XSLT/XML bağlayıcısı kullanmak Microsoft 365 organizasyona devlet ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-xsltxml-data"></a>XSLT/XML verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış veri kaynağında XSLT/XML kaynak verilerini arşivlemek için bağlayıcı kullanma Microsoft 365.

![XSLT/XML verileri için iş akışı arşivleme.](../media/XSLT-XMLConnectorWorkflow.png)

1. Bir XSLT/XML sitesi ayarlamak ve yapılandırmak için, organizasyonunız XSLT/XML kaynağıyla çalışır.

2. Her 24 saatte bir, XSLT/XML kaynağından gelen sohbet iletileri Veritas Birleştirme1 sitesine kopyalanır. Bağlayıcı, içeriği e-posta iletisi biçimine de dönüştürür.

3. Microsoft 365 uyumluluk merkezi'ta oluştursanız, XSLT/XML bağlayıcısı her gün Veritas Merge1 sitesine bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma gönderir.

4. Bağlayıcı, dönüştürülmüş ileti öğelerini, 3. Adımda açıklandığı gibi otomatik kullanıcı eşlemesinde E-posta özelliğinin değerini  kullanarak belirli kullanıcıların posta kutularına içeri aktarıyor. Kullanıcı posta kutularında **XSLT/XML** adlı Gelen Kutusu klasöründe yeni bir alt klasör oluşturulur ve ileti öğeleri bu klasöre aktarılır. Bağlayıcı bunu, E-posta özelliğinin *değerini kullanarak* yapar. Her iletide, iletinin tüm katılımcılarının e-posta adresiyle doldurulan bu özellik yer alır.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için VeriTas Merge1 hesabı oluşturun. Bu hesabı oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://www.veritas.com/content/support/). 1. Adım'da bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- XSLT/XML bağlayıcısını 1. Adımda oluşturan (ve 3. Adımda tamamlayan) kullanıcı, bu bağlayıcıda Posta Kutusu İçeri/Dışarı Aktarma rolüne atan Exchange Online. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol ilgili gruptaki bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-an-xsltxml-connector"></a>1. Adım: XSLT/XML bağlayıcısı ayarlama

İlk adım, veri kaynağında **Veri** Bağlayıcıları'na erişmek Microsoft 365 uyumluluk merkezi XSLT/XML verileri için bir bağlayıcı oluşturmaktır.

1. Veri bağlayıcılarıXSLT [https://compliance.microsoft.com](https://compliance.microsoft.com/)/**XML'ye** >  gidin **ve bu öğesini tıklatın**.

2. **XSLT/XML ürün** açıklaması sayfasında Yeni bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-an-xsltxml-connector"></a>2. Adım: XSLT/XML bağlayıcısını yapılandırma

İkinci adım, Merge1 sitesinde XSLT/XML bağlayıcısını yapılandırmaktır. Veritas Birleştirme1 sitesinde XSLT/XML bağlayıcısını yapılandırma hakkında bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20XSLT-XML%20User%20Guide%20.pdf).

Son Olarak Kaydet **& e tıklarken**, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

1. Kullanıcıları eşlemek ve bağlayıcı kurulumunu aşağıdaki Microsoft 365 uyumluluk merkezi izleyin:

2. **XSLT/XML kullanıcılarını kullanıcı eşleme Microsoft 365 otomatik** kullanıcı eşlemesini etkinleştirin. XSLT/XML öğeleri, organizasyondaki *kullanıcıların* e-posta adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

3. **Sonraki'ne** tıklayın, ayarlarınızı gözden geçirin ve yeni **bağlayıcıya** yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-xsltxml-connector"></a>4. Adım: XSLT/XML bağlayıcısını izleme

XSLT/XML bağlayıcısını oluşturdukktan sonra, bağlayıcının durumunu bağlayıcının Microsoft 365 uyumluluk merkezi.

1. Sol gezinti [https://compliance.microsoft.com](https://compliance.microsoft.com) çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve sonra **XSLT/XML** bağlayıcısını seçerek açılır sayfayı görüntüleyin. Bu sayfa, bağlayıcının özelliklerini ve bilgilerini içerir.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.