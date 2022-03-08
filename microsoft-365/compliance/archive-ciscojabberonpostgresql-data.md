---
title: Cisco Cisco Ciscober'i Iş Ortağı'nın PostgreSQL verisinde arşivlemek için bir bağlayıcı Microsoft 365
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
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: PostgreSQL'de Cisco Cisco Ciscober'den verileri içeri Microsoft 365 uyumluluk merkezi ve arşiv için bağlantıda bağlayıcı ayarlamayı ve kullanmayı Microsoft 365.
ms.openlocfilehash: 946a43155ed085575e9aef97b04f0828338963e5
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328841"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-postgresql-data"></a>PostgreSQL verisinde Cisco Cisco Ciscober'ı arşivlemek için bir bağlayıcı ayarlama

Cisco Cisco Ciscober platformundan kendi Microsoft 365 uyumluluk merkezi posta kutularına veri içeri aktararak veya bu platformdan kullanıcı posta kutularına veri Microsoft 365 kullanın. Veritas, üçüncü taraf veri kaynağından öğeleri yakalamak ve bu öğeleri düzenli olarak üçüncü taraf veri kaynağından içeri aktaracak şekilde yapılandırılmış bir [PostgreSQL](https://www.veritas.com/insights/merge1/jabber) bağlayıcısı ile Cisco Cisco Microsoft 365. Bağlayıcı, PostgreSQL'daki Cisco Ciscober'dan gelen iletiler, sohbetler ve paylaşılan içerik gibi içerikleri e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri Microsoft 365'ta kullanıcının posta kutusuna aktarıyor.

PostgreSQL'daki Cisco Cisco Ciscober verileri kullanıcı posta kutularında depolandığı için Mahkeme Microsoft 365, eBulma, bekletme ilkeleri ve bekletme etiketleri gibi uyumluluk özellikleri uygulayabilirsiniz. PostgreSQL bağlayıcısı ile Cisco Cisco Ciscober'ı kullanarak verileri başka bir kuruluşta içeri aktarın ve arşiv Microsoft 365, kurumnizin devlet ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-cisco-jabber-on-postgresql-data"></a>PostgreSQL verisinde Cisco CiscoBer'i arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, PostgreSQL'de Cisco Cisco CiscoQL verilerini aynı dosyada arşivlemek için bağlayıcı kullanma Microsoft 365.

![PostgreSQL verisinde Cisco Cisco Ciscober için iş akışı arşivleme.](../media/CiscoJabberonPostgreSQLConnectorWorkflow.png)

1. Organizasyonun PostgreSQL'de Cisco Cisco Ciscober ile birlikte, PostgreSQL sitesinde Cisco Cisco Ciscober'i ayarlama ve yapılandırma üzerinde çalışıyor.

2. PostgreSQL'de Cisco Cisco Cisco her 24 saatte bir, Veritas Merge1 sitesine kopyalanır. Bağlayıcı, PostgreSQL öğeleri üzerinde Cisco Cisco Cisco'yu da e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi'ta oluşturmakta olduğunuz PostgreSQL'daki Cisco Ciscober bağlayıcısı, her gün Veritas Merge1 sitesine bağlanır ve Bu içerikLeber içeriğini Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı, dönüştürülmüş öğeleri, 3. Adımda açıklandığı gibi otomatik kullanıcı eşlemesinde *E-posta* özelliğinin değerini kullanarak belirli kullanıcıların posta [kutularına içeri aktarıyor](#step-3-map-users-and-complete-the-connector-setup). Kullanıcı posta kutularında **PostgreSQL üzerinde Cisco Cisco Ciscober** adlı bir Gelen Kutusu klasöründe bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bunu, E-posta özelliğinin *değerini kullanarak* yapar. Her Bir Öğe bu özelliği içerir ve bu özellik, öğenin tüm katılımcılarının e-posta adresiyle doldurulur.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için bir Merge1 hesabı oluşturun. Bunu yapmak için [Veritas Müşteri Desteği'ne başvurun](https://www.veritas.com/content/support/en_US). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 1. Adımda PostgreSQL bağlayıcısını Oluşturan (ve 3. Adımda tamamlayan) Cisco Cisco Ciscober'e, Veri Bağlayıcısı Yöneticisi rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-cisco-jabber-on-postgresql-connector"></a>1. Adım: PostgreSQL bağlayıcısı üzerinde Cisco Cisco Ciscober'i ayarlama

İlk adım, bağlantı sayfasındaki **Veri Bağlayıcıları** sayfasına erişmek ve Microsoft 365 uyumluluk merkezi Için Bir Bağlayıcı oluşturmaktır.

1. <https://compliance.microsoft.com> **PostgreSQL'de Cisco Cisco Ciscober'e gidip bu bağlayıcılara tıklayın**. &gt;

2. **PostgreSQL ürün açıklamasında Cisco CiscoBer'de** Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-cisco-jabber-on-postgresql-on-the-veritas-merge1-site"></a>2. Adım: Veritas Merge1 sitesinde PostgreSQL üzerinde Cisco Cisco Ciscober'i yapılandırma

İkinci adım, Veritas Merge1 sitesinde PostgreSQL bağlayıcısı üzerinde Cisco Cisco Ciscober'i yapılandırmaktır. PostgreSQL bağlayıcısı üzerinde Cisco Cisco Ciscober'i yapılandırma hakkında bilgi için bkz. [Merge1 Third-Party Connectors Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20PostgreSQL%20User%20Guide.pdf).

Son Olarak Kaydet **& e tıklarken**, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve aşağıdaki adımları takip etmek için Microsoft 365 uyumluluk merkezi izleyin:

1. **PostgreSQL kullanıcılarına Cisco Ciscober Haritası sayfasında Microsoft 365 eşlemeyi** etkinleştirin. PostgreSQL'daki Cisco Cisco CiscoBer *öğeleri,* kurumdaki kullanıcılar için e-posta adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcıya yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-cisco-jabber-on-postgresql-connector"></a>4. Adım: PostgreSQL bağlayıcısı üzerinde Cisco Cisco Ciscober'i izleme

PostgreSQL bağlayıcısı üzerinde Cisco Cisco Ciscober'i oluşturdukta, bağlayıcının durumunu en son Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com/> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve ardından Özellikler ve bağlayıcı hakkında bilgi içeren açılır sayfayı görüntülemek için **PostgreSQL bağlayıcısı üzerinde Cisco Cisco Ciscober'i** seçin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
