---
title: Pivot verilerini aynı dosyada arşivlemek için bağlayıcıyı Microsoft 365
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
description: Yöneticiler, veri kaynağında Veritas'tan Pivot verilerini içeri aktaracak ve arşivleyacak bir Microsoft 365. Bu bağlayıcı, üçüncü taraf veri kaynaklarından verileri Microsoft 365'te arşivlemenize olanak sağlar ve böylece yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanarak kuruluş üçüncü taraf verilerini yönetebilirsiniz.
ms.openlocfilehash: 76f18c80ed9c1c4ee8fa9c20fd19a75d6022ff61
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021478"
---
# <a name="set-up-a-connector-to-archive-pivot-data"></a>Pivot verilerini arşivlemek için bağlayıcıyı ayarlama

Pivot platformundan verileri Microsoft 365 uyumluluk merkezi ve Microsoft 365 için veri kaynağında Veritas bağlayıcısı kullanın. Veritas size üçüncü taraf veri kaynağından öğeleri yakalayan (düzenli olarak) ve bu öğeleri düzenli olarak içeri aktaracak şekilde yapılandırılmış bir [Pivot](https://globanet.com/pivot/) bağlayıcısı Microsoft 365. Pivot, finansal pazar katılımcıları ile işbirliğine olanak sağlayan bir anlık ileti platformudur. Bağlayıcı, kullanıcıların Pivot hesaplarından sohbet iletileri gibi öğeleri e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri Microsoft 365.

Özet verileri kullanıcı posta kutularında depolanıyorsa, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Pivot bağlayıcısı kullanarak verileri başka bir kuruluşta içeri aktarın Microsoft 365 mevzuat ilkeleriyle uyumlu çalışmanıza yardımcı olabilir.

## <a name="overview-of-archiving-pivot-data"></a>Özet verileri arşivlemeye genel bakış

Aşağıdaki genel bakış sayfasında Pivot data'larını arşivlemek için bağlayıcı kullanma işlemi Microsoft 365.

![Özet veriler için iş akışı arşivleme.](../media/PivotConnectorWorkflow.png)

1. Organizasyonunız Pivot ile birlikte çalışır ve bir Pivot kaynak sitesi ayarları ve yapılandırr.

2. Her 24 saatte bir, Özet öğeler Veri Kaynağı Birleştirme1 sitesine kopyalanır. Bağlayıcı, Özet öğeleri de e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi'ta oluşturmakta istediğiniz Pivot bağlayıcısı, her gün VeriTas Merge1 sitesine bağlanır ve Pivot öğelerini Microsoft bulutundaki güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı, Pivot öğelerini 3. Adımda açıklandığı gibi otomatik kullanıcı eşlemesinde *E-posta* özelliğinin değerini kullanarak belirli kullanıcıların posta kutularına [aktarıyor](#step-3-map-users-and-complete-the-connector-setup). Kullanıcı posta kutularında Gelen Kutusu klasöründe **özet** adlı bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bunu, E-posta özelliğinin *değerini kullanarak* yapar. Her Özet öğesi, öğenin tüm katılımcılarının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için VeriTas Merge1 hesabı oluşturun. Bu hesabı oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://www.veritas.com/content/support/). 1. Adım'da bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- 1. Adımda Pivot bağlayıcısı oluşturan (ve 3. Adımda bunu tamamlayan) kullanıcı, Pivot'ta Posta Kutusu İçeri/Dışarı Aktarma rolüne atan Exchange Online. Bu rol, sayfanın veri bağlayıcıları sayfasında bağlayıcı eklemek Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol ilgili gruptaki bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-pivot-connector"></a>1. Adım: Pivot bağlayıcısı'nı ayarlama

İlk adım, Microsoft uyumluluk merkezinde **Veri Bağlayıcıları** sayfasına erişmek ve Pivot verileri için bir bağlayıcı oluşturmaktır.

1. Veri bağlayıcılarıPivot'a [https://compliance.microsoft.com](https://compliance.microsoft.com/) **gidin ve** >  **bu öğeye tıklayın**.

2. Ürün açıklamasını **özetle** sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-pivot-connector-on-the-veritas-merge1-site"></a>2. Adım: VeriTas Merge1 sitesinde Pivot bağlayıcısı yapılandırma

İkinci adım, Merge1 sitesinde Pivot bağlayıcısı'nı yapılandırmaktır. Veritas Birleştirme1 sitesinde Pivot bağlayıcısı'nı yapılandırma hakkında bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Pivot%20User%20Guide%20.pdf).

Son Olarak Kaydet **& e tıklarken**, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve Microsoft 356 uyumluluk merkezinde bağlayıcı kurulumunu tamamlamak için şu adımları izleyin:

1. Özet kullanıcıları **kullanıcı eşleme Microsoft 365 otomatik** kullanıcı eşlemesini etkinleştirin. Özet öğeleri, kurumdaki kullanıcıların *e-posta* adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ne** tıklayın, ayarlarınızı gözden geçirin ve yeni **bağlayıcıya** yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-pivot-connector"></a>4. Adım: Özet bağlayıcıyı izleme

Pivot bağlayıcıyı oluşturdukta, bağlayıcının durumunu bağlayıcının son Microsoft 365 uyumluluk merkezi.

1. Sol gezinti [https://compliance.microsoft.com](https://compliance.microsoft.com) çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve sonra açılır **sayfayı** görüntülemek için Pivot bağlayıcısı'nı seçin. Bu sayfa, bağlayıcının özelliklerini ve bilgilerini içerir.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.