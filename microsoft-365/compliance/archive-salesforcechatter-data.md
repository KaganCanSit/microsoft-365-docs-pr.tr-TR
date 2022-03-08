---
title: Salesforce Sohbettersi verilerini aynı dosyada arşivlemek için bağlayıcı Microsoft 365
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
description: Yöneticiler, Salesforce Sohbettersi verilerini Veritas'tan içeri aktaracak ve arşivleyecek bir bağlayıcı Microsoft 365. Bu bağlayıcı, iş yerinde üçüncü taraf veri kaynaklarından verileri Microsoft 365. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: bb52bd95d11a93c2bbb6816ed189ef5e0594ffac
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327428"
---
# <a name="set-up-a-connector-to-archive-salesforce-chatter-data"></a>Salesforce SohbetTersi verilerini arşivlemek için bağlayıcı ayarlama

Salesforce SohbetTersi platformundan Microsoft 365 uyumluluk merkezi kutunuzda kullanıcı posta kutularına veri içeri aktarmak ve arşivlemek için veritas Microsoft 365 kullanın. Veritas, üçüncü [taraf veri](http://globanet.com/chatter/) kaynağından öğeleri yakalayan ve bu öğeleri üçüncü taraf veri kaynağına aktaran bir Salesforce Sohbet Microsoft 365. Bağlayıcı, Salesforce Sohbetter'den sohbetler, ekler ve gönderiler gibi içerikleri bir e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri Microsoft 365'te kullanıcının posta kutusuna dönüştürür.

Salesforce Sohbetter verileri kullanıcı posta kutularında depolandığı için, Mahkeme Microsoft 365, eBulma, bekletme ilkeleri ve bekletme etiketleri gibi uyumluluk özelliklerini uygulayabilirsiniz. Verileri başka bir kuruluşta içeri aktarmanız ve arşivlemeniz için Salesforce Sohbetter bağlayıcısı kullanmak Microsoft 365 düzenleme ilkeleriyle uyumlu çalışmanıza yardımcı olabilir.

## <a name="overview-of-archiving-salesforce-chatter-data"></a>Salesforce Sohbetter verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, satış sırasında Salesforce Sohbetter verilerini arşivlemek için bağlayıcı kullanma Microsoft 365.

![Salesforce Sohbetter verileri için arşivleme iş akışı.](../media/SalesforceChatterConnectorWorkflow.png)

1. Organization works with Salesforce Chatter to set up and configure a Salesforce Chatter site.

2. Her 24 saatte bir, Salesforce SohbetTeri öğeleri VeriTas Merge1 sitesine kopyalanır. Ayrıca, Salesforce SohbetTersi öğelerini e-posta iletisi biçiminde de bağlayıcı alırsınız.

3. Microsoft 365 uyumluluk merkezi'ta oluşturmakta olduğunuz Salesforce Sohbetter bağlayıcısı, her gün Veritas Merge1 sitesine bağlanır ve Sohbetter içeriğini Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı, dönüştürülmüş öğeleri, 3. Adımda açıklandığı gibi otomatik kullanıcı eşlemesinde *E-posta* özelliğinin değerini kullanarak belirli kullanıcıların posta [kutularına içeri aktarıyor](#step-3-map-users-and-complete-the-connector-setup). Kullanıcı posta kutularında **Salesforce Sohbettersi** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her Sohbetter öğesi, öğenin tüm katılımcılarının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için bir Merge1 hesabı oluşturun. Hesap oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://www.veritas.com/content/support/). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- Bir Salesforce uygulaması oluşturun ve uygulamasında bir belirteç alın [https://salesforce.com](https://salesforce.com). Salesforce hesabında yönetici olarak oturum açmalı ve verileri içeri aktarabilirsiniz. Ayrıca, güncelleştirmeleri, silmeleri ve düzenlemeleri yakalamak için Tetikleyicilerin Sohbetter sitesinde yayımlandır olması gerekir. Bu tetikleyiciler bir kanalda bir gönderi oluşturacak ve Merge1 kanaldan bilgileri yakalar. Uygulamayı oluşturma ve belirteci edinme hakkında adım adım yönergeler için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcılar Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20SalesForce%20Chatter%20User%20Guide%20.pdf).

- 1. Adımda Salesforce SohbetTersi bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yöneticisi rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-salesforce-chatter-connector"></a>1. Adım: Salesforce Sohbetter bağlayıcısı ayarlama

İlk adım, site sayfasındaki **Veri Bağlayıcıları** sayfasına erişmek Microsoft 365 uyumluluk merkezi Sohbetter verileri için bir bağlayıcı oluşturmaktır.

1. Veri bağlayıcılarıSalesforce [https://compliance.microsoft.com](https://compliance.microsoft.com/) **Sohbetteri'ne** >  gidin **ve bu öğeye tıklayın**.

2. **Salesforce Sohbetter ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-salesforce-chatter-on-the-veritas-merge1-site"></a>2. Adım: Veritas Merge1 sitesinde Salesforce Sohbeti'yi yapılandırma

İkinci adım, Veritas Merge1 sitesinde Salesforce Chatter bağlayıcısı yapılandırmaktır. Salesforce Sohbetter bağlayıcısı yapılandırma hakkında bilgi için bkz. [Merge1 Third-Party Connectors User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20SalesForce%20Chatter%20User%20Guide%20.pdf).

Son Olarak Kaydet **& i** tıklatmanın ardından, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi sayfası görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve aşağıdaki adımları takip etmek için Microsoft 365 uyumluluk merkezi izleyin:

1. **Salesforce Sohbetter kullanıcılarını diğer kullanıcılarla eşleme Microsoft 365**, otomatik kullanıcı eşlemesini etkinleştirin. Salesforce SohbetTersi öğeleri, organizasyondaki kullanıcılar için *e-posta* adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. Ardından **,** ayarlarınızı gözden geçirin ve yeni bağlayıcıya yönelik içeri  aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-salesforce-chatter-connector"></a>4. Adım: Salesforce SohbetTersi bağlayıcılarını izleme

Salesforce Sohbetter bağlayıcısı oluşturduk tan sonra, bağlayıcının durumunu geçerli Microsoft 365 uyumluluk merkezi.

1. Sol gezinti [https://compliance.microsoft.com](https://compliance.microsoft.com/) çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve ardından **Salesforce Sohbetter** bağlayıcısı'ne tıklarsanız bağlayıcının özelliklerini ve bilgilerini içeren açılır sayfayı görüntüleyebilirsiniz.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.