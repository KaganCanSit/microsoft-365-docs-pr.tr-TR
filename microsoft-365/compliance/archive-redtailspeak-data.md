---
title: Kırmızı kuyruklu Konuşma verilerini aynı dosyada arşivlemek için bir bağlayıcı Microsoft 365
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
description: Yöneticiler, Kırmızı kuyruklu Konuşma verilerini Veri görevlerinden içeri aktarıp arşivlemek ve verileri veri kaynağına arşivlemek için bir Microsoft 365. Bu bağlayıcı, iş yerinde üçüncü taraf veri kaynaklarından verileri Microsoft 365. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: 8c0e3c444bf285f951911a9de6e5ef3480eb6468
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63321061"
---
# <a name="set-up-a-connector-to-archive-redtail-speak-data"></a>Redtail Speak verilerini arşivlemek için bir bağlayıcı ayarlama

Microsoft 365 uyumluluk merkezi'da, Redtail Speak'tan kullanıcı posta kutularına veri içeri aktarma ve arşivlemek için, veri kaynağında bir Veri Microsoft 365 kullanın. Veritas size, kuruluş SFTP sunucusundaki öğeleri Redtail'den alınan öğeleri yakalamak için yapılandırılmış bir [Redtail Speak](https://globanet.com/redtail/) bağlayıcısı sağlar. Bağlayıcı, Redtail Konuşma'daki içeriği bir e-posta iletisi biçimine dönüştürür ve bu öğeleri Konuşma'da kullanıcının posta kutusuna Microsoft 365.

Redtail Speak verileri kullanıcı posta kutularında depo edildikten sonra, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri gibi uyumluluk özelliklerini uygulayabilirsiniz. Verileri başka bir kuruluşta içeri aktararak ve arşiv Microsoft 365 Redtail Speak bağlayıcısı kullanmak, kurum kuruluş ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-the-redtail-speak-data"></a>Redtail Speak verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, farklı bir tabloda Redtail Speak verilerini arşivlemek için bağlayıcı kullanma Microsoft 365.

![Redtail Speak verileri için arşivleme iş akışı.](../media/RedtailSpeakConnectorWorkflow.png)

1. Your organization works with Redtail Speak to set up and configure an SMTP gateway where messages are forwarded from Redtail Speak to your organization's SFTP server on a daily basis.

2. Her 24 saatte bir, Redtail Speak öğeleri Veritas Merge1 sitesine kopyalanır. Bağlayıcı, Redtail Konuşma öğelerini de e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi'ta oluştursanız Redtail Konuşma bağlayıcısı her gün Veritas Merge1 sitesine bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma aktarır.

4. Bağlayıcı, 3. Adımda açıklandığı gibi, otomatik kullanıcı eşlemesinde E-posta özelliğinin değerini kullanarak dönüştürülmüş Redtail Speak  öğelerini belirli kullanıcıların posta kutularına [içeri aktarır](#step-3-map-users-and-complete-the-connector-setup). Kullanıcı posta kutularında Gelen Kutusu klasöründe **Redtail Speak** adlı bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her Redtail Konuşma öğesi, öğenin tüm katılımcılarının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için VeriTas Merge1 hesabı oluşturun. Hesap oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://www.veritas.com/content/support/). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 2. Adım'da, kuruluşun SFTP sunucusunu belirtmeniz gerekir. Veri Görev Birleştirme1'in SFTP aracılığıyla Redtail Speak verilerini toplamak için bu adımla bağlantı kurabilirsiniz.

- 1. Adımda Redtail Konuşma Aktarıcısı bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yöneticisi rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-redtail-speak-connector"></a>1. Adım: Redtail Konuşma bağlayıcıyı ayarlama

İlk adım, ana sayfada Veri Bağlayıcıları  sayfasına erişmek Microsoft 365 uyumluluk merkezi Konuşma verileri için bir bağlayıcı oluşturmaktır.

1. Veri bağlayıcıları [https://compliance.microsoft.com](https://compliance.microsoft.com/) Redtail Speak **seçeneğine** &gt; **gidin ve seçin**.

2. Redtail **Speak ürün açıklaması** sayfasında Yeni bağlayıcı **ekle'yi seçin**.

3. Hizmet koşulları **sayfasında Kabul** Et'i **seçin**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'yi **seçin**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-redtail-speak-connector-on-the-veritas-merge1-site"></a>2. Adım: Veritas Merge1 sitesinde Redtail Speak bağlayıcıyı yapılandırma

İkinci adım, Merge1 sitesinde Redtail Speak bağlayıcıyı yapılandırmaktır. Redtail Speak bağlayıcısı yapılandırma hakkında bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Redtail%20Speak%20User%20Guide%20.pdf).

**Kaydet'i &, Son'a** tıklayın. Eşleme  sayfasındaki bağlayıcı sihirbazında Kullanıcı Microsoft 365 uyumluluk merkezi sayfası görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve bağlayıcı kurulumunu tamamlamak için şu adımları izleyin:

1. Kullanıcıları bu **kullanıcılarla eşleme KırmızıAyrıçları** konuş sayfasında Microsoft 365 kullanıcı eşlemesini etkinleştirin. Redtail Konuşma öğeleri, kurumdaki *kullanıcıların e-posta* adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'yi** seçin, ayarlarınızı gözden geçirin ve yeni **bağlayıcıya** yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-redtail-speak-connector"></a>4. Adım: Redtail Konuşma bağlayıcılarını izleme

Redtail Speak bağlayıcıyı oluşturdukktan sonra, bağlayıcının durumunu konuşmanın Microsoft 365 uyumluluk merkezi.

1. Sol gezinti [https://compliance.microsoft.com](https://compliance.microsoft.com/) çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcıları seçin.

2. Bağlayıcılar **sekmesini seçin** ve sonra da açılır **sayfayı görüntülemek için Redtail Speak** bağlayıcıyı seçin. Bu sayfada bağlayıcıyla ilgili özellikler ve bilgiler görüntülenir.

3. **Bağlayıcının kaynak durumunun** altında, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısını seçin. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.