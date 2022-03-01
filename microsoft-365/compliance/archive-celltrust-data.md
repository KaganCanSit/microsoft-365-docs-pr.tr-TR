---
title: CellTrust verilerini aynı dosyada arşivlemek için bir bağlayıcı Microsoft 365
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
description: Yöneticiler CellTrust verilerini Veritas'tan Veritas'tan içeri aktaracak ve arşivleyacak bir bağlayıcı Microsoft 365. Bu bağlayıcı, iş yerinde üçüncü taraf veri kaynaklarından verileri Microsoft 365. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: fd2ae7c905a1f0104112d30b8a4f195ccd146a07
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021520"
---
# <a name="set-up-a-connector-to-archive-celltrust-data"></a>CellTrust verilerini arşivlemek için bağlayıcı ayarlama

CellTrust platformundan kendi Microsoft 365 uyumluluk merkezi posta kutularına veri içeri aktarma ve bu dosyaları arşivlemek için, veri kaynağında bir Veri Microsoft 365 kullanın. Veritas, üçüncü taraf veri kaynağından öğeleri yakalayan ve bu öğeleri üçüncü taraf veri kaynağına aktaran bir [CellTrust](https://globanet.com/celltrust/) Microsoft 365. Bağlayıcı, CellTrust hesaplarından SMS iletilerinin içeriğini bir e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri aynı adreste kullanıcının posta kutusuna Microsoft 365.

CellTrust verileri kullanıcı posta kutularında depolandığı için, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. verileri başka bir kuruluşta içeri aktarın ve arşiv Microsoft 365 CellTrust bağlayıcısı kullanarak, kurumnizin devlet ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-celltrust-data"></a>CellTrust verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Bağlayıcı kullanarak CellTrust verilerini aynı dosyada arşivleme işlemi Microsoft 365.

![CellTrust verileri için arşivleme iş akışı.](../media/CellTrustConnectorWorkflow.png)

1. Kuruluşlarınız CellTrust sitesi ayarlamak ve yapılandırmak için CellTrust ile birlikte çalışır.

2. Her 24 saatte bir, CellTrust öğeleri Veri Kaynağı Birleştirme1 sitesine kopyalanır. Bağlayıcı, iletinin içeriğini de e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi'de oluştursanız CellTrust bağlayıcısı her gün VeriTas Merge1 sitesine bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı olarak otomatik kullanıcı eşlemesi, 3. Adımda açıklanan E-posta özelliğinin değerini kullanarak öğeleri belirli kullanıcıların posta  [kutularına içeri aktarıyor](#step-3-map-users-and-complete-the-connector-setup). Kullanıcı posta kutularında **CellTrust** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve ileti öğeleri bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her CellTrust öğesi, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için bir Merge1 hesabı oluşturun. Hesap oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://www.veritas.com/content/support/). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 1. Adımda CellTrust bağlayıcısı oluşturan (ve 3. Adımda bu bağlayıcıyı tamamlayan) kullanıcı, Güven'de Posta Kutusu İçeri/Dışarı Aktarma rolüne atan Exchange Online. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-celltrust-connector"></a>1. Adım: CellTrust bağlayıcıyı ayarlama

İlk adım, aşağıdaki bağlantıda Veri **Bağlayıcıları'Microsoft 365 uyumluluk merkezi** ve CellTrust verileri için bir bağlayıcı oluşturmaktır.

1. Veri bağlayıcıları [https://compliance.microsoft.com](https://compliance.microsoft.com/) **CellTrust'a gidin ve** **bu öğeye**\> tıklayın.

2. **CellTrust ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-celltrust-connector-on-the-veritas-merge1-site"></a>2. Adım: VeriTas Merge1 sitesinde CellTrust bağlayıcıyı yapılandırma

İkinci adım, VeriTas Merge1 sitesinde CellTrust bağlayıcısı'nın yapılandırılmasıdır. CellTrust bağlayıcısı'nın nasıl yapılandırıldığından emin olmak için bkz. [Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzunu Birleştirme](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20CellTrust%20User%20Guide%20.pdf).

Son Olarak Kaydet **& e tıklarken**, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve aşağıdaki bağlantıda ayarlanmış bağlayıcıyı Microsoft 365 uyumluluk merkezi şu adımları izleyin:

1. **CellTrust kullanıcılarını kullanıcı eşleme Microsoft 365,** otomatik kullanıcı eşlemesini etkinleştirin. CellTrust öğeleri, kurumdaki *kullanıcıların e-posta* adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ne** tıklayın, ayarlarınızı gözden geçirin ve yeni **bağlayıcıya** yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-celltrust-connector"></a>4. Adım: CellTrust bağlayıcılarını izleme

CellTrust bağlayıcıyı oluşturdukta, bağlayıcının durumunu bağlayıcının son Microsoft 365 uyumluluk merkezi.

1. Sol gezinti [https://compliance.microsoft.com](https://compliance.microsoft.com/) çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve **sonra CellTrust** bağlayıcıyı seçerek bağlayıcıyla ilgili özellikleri ve bilgileri içeren açılır sayfayı görüntüleyin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.