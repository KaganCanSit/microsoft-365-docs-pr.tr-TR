---
title: MS'de Cisco Cisco Ciscober'i arşiv SQL verilerini Microsoft 365
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
description: Yöneticiler CISCO Cisco Ciscober'i MS'de ve Veritas'SQL içeri aktarması ve arşivlemesi için bir bağlayıcı Microsoft 365. Bu bağlayıcı, iş yerinde üçüncü taraf veri kaynaklarından verileri Microsoft 365. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: 66f09f2fafcd33d8bc73bdaed61b41354e9633f7
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63319553"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-ms-sql-data"></a>MS veri kaynağında Cisco Cisco Ciscober'i arşivlemek SQL ayarlama

Cisco Cisco Ciscober platformundan kendi Microsoft 365 uyumluluk merkezi posta kutularına veri içeri aktararak veya bu platformdan kullanıcı posta kutularına veri Microsoft 365 kullanın. Veritas size, Bire bir sohbet iletileri ve grup sohbetleri gibi, Bire bir sohbet iletileri ve grup sohbetleri gibi, Yalçın'ın MS SQL Veritabanı'inden öğe yakalamak ve bu öğeleri içeri aktarmayı sağlayan [bir Cisco Cisco Microsoft 365](https://globanet.com/jabber/). Bağlayıcı Cisco Cisco Cisco Ciscober'in MS SQL Veritabanı'inden verileri alır, işler ve kullanıcının Cisco Cisco Ciscober hesabından gelen içeriği e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri Microsoft 365'te kullanıcının posta kutusuna dönüştürür.

Cisco Cisco Ciscober verileri kullanıcı posta kutularında depolandığı için Mahkeme Microsoft 365, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Cisco Cisco Ciscober bağlayıcısı kullanarak verileri başka bir kuruluşta içeri aktarın Microsoft 365 düzenlemeler ve devlet ilkeleriyle uyumlu kalmasınıza yardımcı olabilir.

## <a name="overview-of-archiving-cisco-jabber-data"></a>Cisco Ciscober verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Cisco Cisco Ciscober'i MS'de arşivlemek için bağlayıcı kullanma SQL verileri aynı Microsoft 365.

![Cisco Cisco Ciscober verileri için arşivleme iş akışı.](../media/CiscoJabberonMSSQLConnectorWorkflow.png)

1. Organizasyonun, MS'de Cisco Cisco Ciscober'i ayarlamak ve yapılandırmak için Cisco ile SQL Veritabanı.

2. Cisco Cisco Ciscober öğeleri, MS sitesinden Veritas Merge1 sitesine SQL Veritabanı her 24 saatte bir kopyalanır. Bağlayıcı sohbet iletilerinin içeriğini de e-posta iletisi biçimine dönüştürür.

3. Cisco Cisco Ciscober bağlayıcısı, Microsoft 365 uyumluluk merkezi her gün Veritas Merge1 sitesine bağlanır ve öğeleri Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı olarak otomatik kullanıcı eşlemesi, 3. Adımda açıklanan E-posta özelliğinin değerini kullanarak öğeleri belirli kullanıcıların posta  [kutularına içeri aktarıyor](#step-3-map-users-and-complete-the-connector-setup). Kullanıcı posta kutularında **, MS SQL üzerinde Cisco Cisco Ciscober** adlı bir Gelen Kutusu klasöründe bir alt klasör oluşturulur ve ileti öğeleri bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Tüm Cisco Cisco Ciscober öğesi, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için VeriTas Merge1 hesabı oluşturun. Bu hesabı oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://www.veritas.com/content/support/). 1. Adım'da bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- 1. Adım'da SQL Veritabanı Bağlayıcıyı oluşturmadan önce, Buber öğelerini almak için BIR MS kodu ayarlayın. 2. Adımda Cisco CiscoBer bağlayıcısını yapılandır SQL Veritabanı MS bağlantı ayarlarını siz belirtirsiniz. Daha fazla bilgi için Bkz. [Merge1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf).

- 1. Adımda Cisco Cisco Ciscober bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yöneticisi rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-cisco-jabber-on-ms-sql-connector"></a>1. Adım: Cisco Cisco Ciscober'i MS SQL ayarlama

İlk adım, otomatik bağlantıda **Veri** Bağlayıcıları'Microsoft 365 uyumluluk merkezi VE MS'de Cisco Cisco Ciscober için bir bağlayıcı SQL oluşturmaktır.

1. MS 2010'da [https://compliance.microsoft.com](https://compliance.microsoft.com/)**Data connectorsCisco** >  **Cabber'a gidin ve SQL**.

2. **MS'de Cisco Cisco Ciscober SQL** açıklaması sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-cisco-jabber-on-ms-sql-connector-on-the-veritas-merge1-site"></a>2. Adım: Veritas Merge1 sitesinde MS SQL Cisco Cisco Ciscober'i yapılandırma

İkinci adım, Veritas Merge1 sitesinde MS SQL Cisco CiscoBer'i yapılandırmaktır. CISCO Cisco Ciscober'i MS SQL bağlayıcısı üzerinde yapılandırma hakkında bilgi için bkz. [Merge1 Third-Party Connectors User Guide](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf).

Son Olarak Kaydet **& e tıklarken**, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve aşağıdaki bağlantıda ayarlanmış bağlayıcıyı Microsoft 365 uyumluluk merkezi şu adımları izleyin:

1. **MS'de Cisco Ciscober Haritası SQL kullanıcıların Microsoft 365 otomatik** kullanıcı eşlemesini etkinleştirin. MS'de Cisco Cisco SQL öğeleri, organizasyondaki kullanıcılar için e-posta adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ne** tıklayın, ayarlarınızı gözden geçirin ve yeni **bağlayıcıya** yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-cisco-jabber-connector"></a>4. Adım: Cisco Cisco Ciscober bağlayıcılarını izleme

MS SQL bağlayıcısı üzerinde Cisco Cisco Ciscober'i oluşturdukta, bağlayıcının durumunu en son Microsoft 365 uyumluluk merkezi.

1. Sol gezinti [https://compliance.microsoft.com](https://compliance.microsoft.com) çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve açılır sayfayı görüntülemek için **MS SQL Cisco Ciscober** bağlayıcısı seçin. Bu sayfa, bağlayıcının özelliklerini ve bilgilerini içerir.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
