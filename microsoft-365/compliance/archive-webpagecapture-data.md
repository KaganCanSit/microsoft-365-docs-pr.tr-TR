---
title: Web sayfası verilerini web sayfasında arşivlemek için bağlayıcıyı Microsoft 365
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
description: Yöneticiler, Web Sayfasında Veritas'tan Veritas'tan veri yakalamak için bir bağlayıcı ayar Microsoft 365. Bu bağlayıcı, üçüncü taraf veri kaynaklarından verileri Microsoft 365'te arşivlemenize olanak sağlar ve böylece yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanarak kuruluş üçüncü taraf verilerini yönetebilirsiniz.
ms.openlocfilehash: de6d00c9835f850dfef779cbff207694ffddd716
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021463"
---
# <a name="set-up-a-connector-to-archive-webpage-data"></a>Web sayfası verilerini arşivlemek için bağlayıcı ayarlama

Web sayfalarından verileri kendi Microsoft 365 uyumluluk merkezi kutunuzda kullanıcı posta kutularına içeri aktarmak ve arşivlemek için görev sayfasında bir Veri Microsoft 365 kullanın. Veritas, belirli [bir web sitesinde](https://globanet.com/webpage-capture) veya etki alanının tamamına belirli web sayfalarını (ve bu sayfalarda bulunan tüm bağlantıları) yakalayan bir Web Sayfası Yakalama bağlayıcısı sağlar. Bağlayıcı web sayfası içeriğini PDF, PNG veya özel dosya biçimine dönüştürür ve dönüştürülen dosyaları e-posta iletisine iliştirer ve sonra bu e-posta öğelerini Microsoft 365'te kullanıcı posta kutularına Microsoft 365.

Web sayfası içeriği kullanıcı posta kutularında depolandığı için, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri gibi uyumluluk özelliklerini uygulayabilirsiniz. Web Sayfasındaki verileri içeri aktararak ve arşivlenen bir Web Sayfası Yakalama bağlayıcısı Microsoft 365 düzenleme ilkeleriyle uyumlu çalışmanıza yardımcı olabilir.

## <a name="overview-of-archiving-webpage-data"></a>Web sayfası verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış sayfasında web sayfası içeriğini arşivlemek için bağlayıcı kullanma işlemini Microsoft 365.

![Web sayfası verileri için iş akışı arşivleme.](../media/WebPageCaptureConnectorWorkflow.png)

1. Organizasyonunız, Web Sayfası Yakalama sitesini ayarlamak ve yapılandırmak için web sayfası kaynağıyla birlikte çalışır.

2. Her 24 saatte bir, web sayfası kaynakları öğeleri Veri Kaynağı Birleştirme1 sitesine kopyalanır. Bağlayıcı ayrıca, bir web sayfasının içeriğini e-posta iletisine de dönüştürür ve iliştirer.

3. Microsoft 365 uyumluluk merkezi'ta oluşturdukları Web Sayfası Yakalama bağlayıcısı, her gün Veritas Merge1 sitesine bağlanır ve web sayfası öğelerini Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı, 3. Adımda açıklandığı gibi, otomatik kullanıcı eşlemesinde E-posta özelliğinin değerini kullanarak dönüştürülmüş web sayfası  öğelerini belirli kullanıcıların posta kutularına [içeri aktarıyor](#step-3-map-users-and-complete-the-connector-setup). Kullanıcı posta kutularında Web Sayfası Yakalama adlı Gelen  Kutusu klasöründe bir alt klasör oluşturulur ve web sayfası öğeleri bu klasöre aktarılır. Bağlayıcı bunu, E-posta özelliğinin *değerini kullanarak* yapar. Her web sayfası öğesi, 2. Adımda Web Sayfası Yakalama bağlayıcısı yapılandırıldığında sağlanan e-posta adresleriyle doldurulan [bu özelliği içerir](#step-2-configure-the-webpage-capture-connector-on-the-veritas-merge1-site).

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için VeriTas Merge1 hesabı oluşturun. Bu hesabı oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://www.veritas.com/content/support/). 1. Adım'da bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- Web sayfası öğelerini dönüştürecek özel bir dosya biçimi ayarlamak için Veritas desteğiyle birlikte çalışmanız gerekir. Daha fazla bilgi için Bkz. [Merge1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Web%20Page%20Capture%20User%20Guide%20.pdf).

- 1. Adımda Web Sayfası Yakalama bağlayıcısı oluşturan (ve 3. Adımda bu bağlayıcıyı tamamlayan) kullanıcı, web sayfasındaki Posta Kutusu İçeri/Dışarı Aktarma rolüne Exchange Online. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol ilgili gruptaki bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-webpage-capture-connector"></a>1. Adım: Web Sayfası Yakalama bağlayıcısı'nın ayarlama

İlk adım, Veri Bağlayıcıları'ne **erişmek ve** Web Sayfası kaynak verileri için bir bağlayıcı oluşturmaktır.

1. Veri bağlayıcılarıWebpage [https://compliance.microsoft.com](https://compliance.microsoft.com/) **Capture'a gidin ve** >  **tıklayın**.

2. Web Sayfası **Yakalama ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-webpage-capture-connector-on-the-veritas-merge1-site"></a>2. Adım: VeriTas Merge1 sitesinde Web Sayfası Yakalama bağlayıcısı yapılandırma

İkinci adım, Veritas Birleştirme1 sitesinde Web Sayfası Yakalama bağlayıcısı'nın yapılandırılmasıdır. Web Sayfası Yakalama bağlayıcısı yapılandırma hakkında bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Web%20Page%20Capture%20User%20Guide%20.pdf).

Son Olarak Kaydet **& e tıklarken**, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve bağlayıcı kurulumunu aşağıdaki Microsoft 365 uyumluluk merkezi izleyin:

1. Eşleme Web **Sayfası Yakalama kullanıcılarını kullanıcı Microsoft 365 sayfasında** otomatik kullanıcı eşlemesini etkinleştirin. Web Sayfası Yakalama öğeleri, kurumdaki kullanıcılar için *e-posta* adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ne** tıklayın, ayarlarınızı gözden geçirin ve yeni **bağlayıcıya** yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-webpage-capture-connector"></a>4. Adım: Web Sayfası Yakalama bağlayıcılarını izleme

Web Sayfası Yakalama bağlayıcısı oluşturdukta, bağlayıcının durumunu hemen Microsoft 365 uyumluluk merkezi.

1. Sol gezinti [https://compliance.microsoft.com](https://compliance.microsoft.com) çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve sonra açılır sayfayı görüntülemek **için Web** Sayfası Yakalama bağlayıcısı öğesini seçin. Bu sayfa, bağlayıcının özelliklerini ve bilgilerini içerir.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.