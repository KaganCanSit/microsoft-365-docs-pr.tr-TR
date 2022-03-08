---
title: Cisco Cisco Ciscober'i oracle veri kaynağında arşivlemek için bir bağlayıcı Microsoft 365
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
description: Oracle'da Cisco Cisco Ciscober'den verileri içeri aktararak veya arşiv Microsoft 365 uyumluluk merkezi için bağlantıda bağlayıcı ayarlamayı ve kullanmayı Microsoft 365.
ms.openlocfilehash: d58d015e94050bc82b427ba450314b7bb447d4d1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320655"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-oracle-data"></a>Cisco Cisco Ciscober'i Oracle verisinde arşivlemek için bağlayıcı ayarlama

Oracle platformunda Cisco Cisco Ciscober platformundan kendi Microsoft 365 uyumluluk merkezi posta kutularına veri içeri aktarma ve arşivlemek için, veri kaynağında bir Veritas Microsoft 365 kullanın. Veritas, üçüncü taraf veri kaynağından (düzenli olarak) öğe yakalamak ve bu öğeleri belirli bir toplama kaynağına aktaracak şekilde yapılandırılan [Oracle](https://www.veritas.com/insights/merge1/jabber) Microsoft 365. Bağlayıcı, dosya ve dosya işlemleri, açıklamalar ve Oracle'daki Cisco Cisco Ciscober'dan paylaşılan içerik gibi içerikleri e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri Microsoft 365'da kullanıcının posta kutusuna aktarır.

Cisco Cisco Ciscober'in Oracle verileri kullanıcı posta kutularında depolandığı için Mahkeme Microsoft 365, eBulma, bekletme ilkeleri ve bekletme etiketleri gibi uyumluluk özelliklerini uygulayabilirsiniz. Oracle bağlayıcısı ile Cisco Cisco Ciscober'i kullanarak verileri kendi iş Microsoft 365 ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-cisco-jabber-on-oracle-data"></a>Oracle verisinde Cisco Ciscober'i arşivlemeye genel bakış

Aşağıdaki genel bakış, bağlayıcı kullanarak Oracle verilerini aynı dosyada Cisco Cisco Ciscober'e Microsoft 365.

![Oracle verisinde Cisco Ciscober için arşivleme iş akışı.](../media/CiscoJabberOnOracleConnectorWorkflow.png)

1. Organizasyonun Oracle sitesinde Cisco Cisco Ciscober'i ayarlamak ve yapılandırmak için Oracle'da Cisco Cisco ile çalışır.

2. Oracle öğeleri üzerinde Cisco Cisco Ciscober, 24 saatte bir Veritas Merge1 sitesine kopyalanır. Bağlayıcı, Cisco Cisco Ciscober'i oracle öğelerine de e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi'ta oluşturmakta olduğunu Oracle Cisco Ciscober bağlayıcısı, her gün Veritas Merge1 sitesine bağlanır ve Saatber içeriğini Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı, dönüştürülmüş öğeleri, 3. Adımda açıklandığı gibi otomatik kullanıcı eşlemesinde *E-posta* özelliğinin değerini kullanarak belirli kullanıcıların posta [kutularına içeri aktarıyor](#step-3-map-users-and-complete-the-connector-setup). Kullanıcı posta kutularında **Oracle'da Cisco Cisco Ciscober** adlı bir Gelen Kutusu klasöründe bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bunu, E-posta özelliğinin *değerini kullanarak* yapar. Her Bir Öğe bu özelliği içerir ve bu özellik, öğenin tüm katılımcılarının e-posta adresiyle doldurulur.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için bir Merge1 hesabı oluşturun. Bunu yapmak için [Veritas Müşteri Desteği'ne başvurun](https://www.veritas.com/content/support/en_US). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 1. Adımda Oracle bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yöneticisi rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-cisco-jabber-on-oracle-connector"></a>1. Adım: Cisco Cisco Ciscober'i Oracle bağlayıcısı üzerinde ayarlama

İlk adım, bağlantı sayfasındaki **Veri Bağlayıcıları** sayfasına erişmek ve Microsoft 365 uyumluluk merkezi Için Bir Bağlayıcı oluşturmaktır.

1. Oracle'da <https://compliance.microsoft.com> **Data connectorsCisco** >  **Oracleber'a gidin ve tıklayın**.

2. **Cisco Cisco Ciscober on Oracle ürün** açıklaması sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-cisco-jabber-on-oracle-on-the-veritas-merge1-site"></a>2. Adım: Veritas Merge1 sitesinde Cisco Cisco Ciscober'i Oracle'da yapılandırma

İkinci adım, Veritas Merge1 sitesinde Oracle bağlayıcısı cisco Cisco Ciscober'i yapılandırmaktır. Cisco Cisco Ciscober bağlayıcıyı Oracle bağlayıcısı üzerinde yapılandırma hakkında bilgi için bkz. [Merge1 Third-Party Connectors Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20Oracle%20User%20Guide.pdf).

Son Olarak Kaydet **& e tıklarken**, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve aşağıdaki adımları takip etmek için Microsoft 365 uyumluluk merkezi izleyin:

1. **Oracle users to Microsoft 365 Map Cisco Ciscober sayfasında**, otomatik kullanıcı eşlemesini etkinleştirin. Oracle öğelerinde Cisco Cisco Ciscober, kurumdaki *kullanıcıların* e-posta adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcıya yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-cisco-jabber-on-oracle-connector"></a>4. Adım: Cisco Cisco Ciscober'i Oracle bağlayıcısı üzerinde izleme

Oracle bağlayıcısı üzerinde Cisco Cisco Ciscober'i oluşturdukta, bağlayıcının durumunu hemen Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com/> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve ardından bağlayıcının özelliklerini ve bilgilerini içeren açılır sayfayı görüntülemek için **Oracle'da Cisco Ciscober** bağlayıcısı seçin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
