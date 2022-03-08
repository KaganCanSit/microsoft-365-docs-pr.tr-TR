---
title: MS 2010'dan verileri arşivlemek için bağlayıcıyı SQL Veritabanı
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
description: Yöneticiler MS SQL Veritabanı'den veri içeri aktarma ve arşivlemek için bir bağlayıcı SQL Veritabanı. Bu bağlayıcı, iş yerinde üçüncü taraf veri kaynaklarından verileri Microsoft 365. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: f00b76cb2199d1af9daca58e86ad7cd2009c2031
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63315701"
---
# <a name="set-up-a-connector-to-archive-data-from-ms-sql-database"></a>MS 2010'dan verileri arşivlemek için bağlayıcıyı SQL Veritabanı

MS Microsoft 365 uyumluluk merkezi'dan verileri kendi SQL Veritabanı kullanıcı posta kutularına içeri aktarın ve Microsoft 365 veri kaynağında Veritas bağlayıcısı kullanın. Veritas size, XML yapılandırma dosyası kullanarak veritabanından öğe yakalamak ve bu öğeleri başka bir dosyaya içeri aktaracak şekilde yapılandırılmış bir MS SQL Veritabanı Aktarıcı Microsoft 365. Bağlayıcı MS dosyalarından gelen SQL Veritabanı bir e-posta ileti biçimine dönüştürür ve sonra bu öğeleri kendi posta kutularına Microsoft 365.

MS'den SQL Veritabanı kullanıcı posta kutularında depolanmış durumdaki içerikten sonra, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri gibi uyumluluk özellikleri uygulayabilirsiniz. MS SQL Veritabanı bağlayıcısı kullanarak verileri başka bir kuruluşta içeri aktarın ve Microsoft 365, kuruluş ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-the-ms-sql-data"></a>MS veri arşivlemeye SQL genel bakış

Aşağıdaki genel bakış makalesinde, MS'i veya bağlayıcı kullanarak verilerinizi SQL işlemi Microsoft 365.

![MS verileri için iş SQL arşivleme.](../media/MSSQLDatabaseConnectorWorkflow.png)

1. Organizasyon, ms siteyi ayarlamak SQL Veritabanı için MS hizmet sağlayıcısıyla birlikte SQL Veritabanı çalışır.

2. HER 24 saatte bir, MS SQL Veritabanı öğeleri Veri Görev Birleştirme1 sitesine kopyalanır. Bağlayıcı bu içeriği de e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi'ta SQL Veritabanı MS Veri Kaynağı Aktarıcısı bağlayıcısı, her gün VeriTas Merge1 sitesine bağlanır ve iletileri Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı, 3. Adımda açıklandığı SQL Veritabanı otomatik kullanıcı eşlemesinde E-posta özelliğinin değerini kullanarak dönüştürülmüş MS dosya öğelerini belirli kullanıcıların  posta kutularına [alır](#step-3-map-users-and-complete-the-connector-setup). Kullanıcı posta kutularında **MS SQL Veritabanı** Gelen Kutusu klasöründe bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. MS verilerinden her SQL Veritabanı, öğenin her katılımcılarının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için VeriTas Merge1 hesabı oluşturun. Hesap oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://www.veritas.com/content/support/). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 1. Adımda MS SQL Veritabanı bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yöneticisi rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-ms-sql-database-importer-connector"></a>1. Adım: MS Veri Aktarıcı SQL Veritabanı ayarlama

İlk adım, çalışma sayfasındaki **Veri Bağlayıcıları** sayfasına erişmek Microsoft 365 uyumluluk merkezi MS bağlayıcısı için bir bağlayıcı oluşturmak SQL Veritabanı.

1. Veri bağlayıcılarıMS [https://compliance.microsoft.com](https://compliance.microsoft.com) **ve Aktarıcı'ya** >  **SQL Veritabanı tıklayın**.

2. MS Veri **Aktarıcısı SQL Veritabanı sayfasında** Yeni bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-ms-sql-database-importer-connector-on-the-veritas-merge1-site"></a>2. Adım: Veritas Birleştirme1 SQL Veritabanı MS Veri Aktarıcısı bağlayıcılarını yapılandırma

İkinci adım, Merge1 sitesinde MS SQL Veritabanı Aktarıcı bağlayıcısı'nın yapılandırılmasıdır. MS Veri Aktarıcısı'nın nasıl yapılandır SQL Veritabanı için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20MS%20SQL%20Database%20Importer%20User%20Guide%20.pdf).

Son Olarak Kaydet **& e tıklarken**, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve bağlayıcı kurulumunu tamamlamak için şu adımları izleyin:

1. MS Veri **Aktarıcısı SQL Veritabanı Eşleme Microsoft 365 otomatik** kullanıcı eşlemesini etkinleştirin. MS SQL Veritabanı, e-posta *olarak adlandırılan ve* kurumdaki kullanıcıların e-posta adreslerini içeren bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ne** tıklayın, ayarlarınızı gözden geçirin ve yeni **bağlayıcıya** yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-ms-sql-database-importer-connector"></a>4. Adım: MS Veri Aktarıcı SQL Veritabanı izleme

MS Zaman Aktarıcı SQL Veritabanı oluşturdukta, bağlayıcının durumunu bağlayıcının son Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com/> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve **ardından MS SQL Veritabanı**  Aktarıcı bağlayıcısı'nın seçerek bağlayıcının özelliklerini ve bilgilerini içeren açılır sayfayı görüntüleyin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.