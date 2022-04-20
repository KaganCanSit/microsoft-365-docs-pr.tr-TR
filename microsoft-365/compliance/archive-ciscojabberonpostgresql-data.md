---
title: Microsoft 365'de PostgreSQL verilerini arşivleme amacıyla Cisco Jabber'ı arşivleme bağlayıcısı ayarlama
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
description: PostgreSQL'de Cisco Jabber'dan Microsoft 365 verileri içeri aktarmak ve arşivlemek için Microsoft Purview uyumluluk portalında bağlayıcı ayarlamayı ve kullanmayı öğrenin.
ms.openlocfilehash: 2e573bcc6c39e9188ec09f05190c124bd904ef98
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64996338"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-postgresql-data"></a>PostgreSQL verilerinde Cisco Jabber'ı arşivleme bağlayıcısı ayarlama

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Cisco Jabber platformundaki verileri Microsoft 365 kuruluşunuzdaki kullanıcı posta kutularına aktarmak ve arşivlemek için Microsoft Purview uyumluluk portalında bir Veritas bağlayıcısı kullanın. Veritas, üçüncü taraf veri kaynağından öğeleri yakalamak (düzenli olarak) ve bu öğeleri Microsoft 365 içeri aktarmak için yapılandırılmış [postgreSQL üzerinde Cisco Jabber](https://www.veritas.com/insights/merge1/jabber) bağlayıcısı sağlar. Bağlayıcı, PostgreSQL üzerinde Cisco Jabber'dan gelen iletiler, sohbetler ve paylaşılan içerik gibi içerikleri e-posta iletisi biçimine dönüştürür ve ardından bu öğeleri Microsoft 365'de kullanıcının posta kutusuna aktarır.

PostgreSQL'deki Cisco Jabber verileri kullanıcı posta kutularında depolandıktan sonra, Dava Tutma, eBulma, bekletme ilkeleri ve bekletme etiketleri gibi Microsoft Purview özelliklerini uygulayabilirsiniz. Microsoft 365'da verileri içeri aktarmak ve arşivlemek için PostgreSQL üzerinde Cisco Jabber bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-cisco-jabber-on-postgresql-data"></a>PostgreSQL verilerinde Cisco Jabber'ı arşivleme işlemine genel bakış

Aşağıdaki genel bakış, Microsoft 365'de PostgreSQL'de Cisco Jabber verilerini arşivleme amacıyla bağlayıcı kullanma işlemini açıklar.

![PostgreSQL verilerinde Cisco Jabber için arşivleme iş akışı.](../media/CiscoJabberonPostgreSQLConnectorWorkflow.png)

1. Kuruluşunuz PostgreSQL'de Cisco Jabber ile birlikte çalışarak PostgreSQL sitesinde Cisco Jabber'ı ayarlayıp yapılandırıyor.

2. Her 24 saatte bir PostgreSQL üzerindeki Cisco Jabber öğeleri Veritas Merge1 sitesine kopyalanır. Bağlayıcı ayrıca PostgreSQL'de Cisco Jabber öğelerini e-posta iletisi biçimine dönüştürür.

3. Uyumluluk portalında oluşturduğunuz PostgreSQL üzerinde Cisco Jabber bağlayıcısı, her gün Veritas Merge1 sitesine bağlanır ve Jabber içeriğini Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır.

4. Bağlayıcı, [3. Adımda](#step-3-map-users-and-complete-the-connector-setup) açıklandığı gibi otomatik kullanıcı eşlemesinin *Email* özelliğinin değerini kullanarak dönüştürülen öğeleri belirli kullanıcıların posta kutularına aktarır. **PostgreSQL'de** Gelen Kutusu klasöründeki Cisco Jabber adlı bir alt klasör kullanıcı posta kutularında oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bunu *Email* özelliğinin değerini kullanarak yapar. Her Jabber öğesi, öğenin her katılımcısının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için bir Merge1 hesabı oluşturun. Bunu yapmak için [Veritas Müşteri Desteği'ne](https://www.veritas.com/content/support/en_US) başvurun. 1. Adımda bağlayıcıyı oluştururken bu hesapta oturum açmanız gerekir.

- 1. Adımda PostgreSQL'de Cisco Jabber bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için [Microsoft Purview uyumluluk portalındaki İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu Veritas veri bağlayıcısı, Microsoft 365 ABD Kamu bulutundaki GCC ortamlarda genel önizleme aşamasındadır. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerinin Microsoft 365 altyapısı dışında olan ve bu nedenle Microsoft Purview ve veri koruma taahhütleri kapsamında olmayan üçüncü taraf sistemlerde depolanmasını, iletilmesini ve işlenmesini içerebilir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="step-1-set-up-the-cisco-jabber-on-postgresql-connector"></a>1. Adım: PostgreSQL'de Cisco Jabber bağlayıcısını ayarlama

İlk adım, uyumluluk portalındaki **Veri Bağlayıcıları** sayfasına erişmek ve Jabber verileri için bir bağlayıcı oluşturmaktır.

1. **PostgreSQL'de** **Veri bağlayıcıları** &gt; Cisco Jabber'a <https://compliance.microsoft.com> gidin ve tıklayın.

2. **PostgreSQL'de Cisco Jabber** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın.

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve **İleri'ye** tıklayın.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızda oturum açın.

## <a name="step-2-configure-the-cisco-jabber-on-postgresql-on-the-veritas-merge1-site"></a>2. Adım: Veritas Merge1 sitesinde PostgreSQL'de Cisco Jabber'ı yapılandırma

İkinci adım, Veritas Merge1 sitesindeki PostgreSQL üzerinde Cisco Jabber bağlayıcısını yapılandırmaktır. PostgreSQL'de Cisco Jabber bağlayıcısını yapılandırma hakkında bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20PostgreSQL%20User%20Guide.pdf).

**Kaydet & Son'a** tıkladıktan sonra, uyumluluk portalındaki bağlayıcı sihirbazındaki **Kullanıcı eşleme** sayfası görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve uyumluluk portalında bağlayıcı kurulumunu tamamlamak için şu adımları izleyin:

1. **PostgreSQL kullanıcılarını Microsoft 365 için Cisco Jabber** harita sayfasında otomatik kullanıcı eşlemesini etkinleştirin. PostgreSQL üzerindeki Cisco Jabber öğeleri, kuruluşunuzdaki kullanıcıların *e-posta adreslerini içeren E-posta* adlı bir özellik içerir. Bağlayıcı bu adresi bir Microsoft 365 kullanıcıyla ilişkilendirebiliyorsa, öğeler söz konusu kullanıcının posta kutusuna aktarılır.

2. **İleri'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları** sayfasına gidin.

## <a name="step-4-monitor-the-cisco-jabber-on-postgresql-connector"></a>4. Adım: PostgreSQL üzerinde Cisco Jabber bağlayıcısını izleme

PostgreSQL üzerinde Cisco Jabber bağlayıcısını oluşturduktan sonra uyumluluk portalında bağlayıcı durumunu görüntüleyebilirsiniz.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com/> gidin ve tıklayın.

2. **Bağlayıcılar** sekmesine tıklayın ve ardından Bağlayıcı hakkındaki özellikleri ve bilgileri içeren açılır sayfayı görüntülemek için **PostgreSQL'de Cisco Jabber** bağlayıcısını seçin.

3. Bağlayıcının durum günlüğünü açmak (veya kaydetmek) için **Kaynakla bağlayıcı durumu** altında **Günlüğü indir** bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.
