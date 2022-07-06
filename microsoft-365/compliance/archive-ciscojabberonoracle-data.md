---
title: Microsoft 365'te Oracle verilerinde Cisco Jabber'ı arşivleme bağlayıcısı ayarlama
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Oracle'da Cisco Jabber'dan Microsoft 365'e veri içeri aktarmak ve arşivlemek için Microsoft Purview uyumluluk portalı bağlayıcı ayarlamayı ve kullanmayı öğrenin.
ms.openlocfilehash: 9920ade2b025824fe7308142ac033872a656ff7a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636865"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-oracle-data"></a>Oracle verilerinde Cisco Jabber'ı arşivleme bağlayıcısı ayarlama

Oracle platformundaki Cisco Jabber'dan Microsoft 365 kuruluşunuzdaki kullanıcı posta kutularına verileri içeri aktarmak ve arşivlemek için Microsoft Purview uyumluluk portalı bir Veritas bağlayıcısı kullanın. Veritas, üçüncü taraf veri kaynağındaki öğeleri yakalamak (düzenli olarak) ve bu öğeleri Microsoft 365'e aktarmak için yapılandırılmış bir [Oracle üzerinde Cisco Jabber](https://www.veritas.com/insights/merge1/jabber) bağlayıcısı sağlar. Bağlayıcı, Oracle üzerinde Cisco Jabber'dan dosya ve dosya işlemleri, açıklamalar ve paylaşılan içerik gibi içerikleri e-posta iletisi biçimine dönüştürür ve ardından bu öğeleri Microsoft 365'te kullanıcının posta kutusuna aktarır.

Oracle'daki Cisco Jabber verileri kullanıcı posta kutularında depolandıktan sonra, Dava Tutma, eBulma, bekletme ilkeleri ve bekletme etiketleri gibi Microsoft Purview özelliklerini uygulayabilirsiniz. Microsoft 365'te verileri içeri aktarmak ve arşivlemek için Oracle bağlayıcısında Cisco Jabber kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-cisco-jabber-on-oracle-data"></a>Oracle verilerinde Cisco Jabber arşivlemesine genel bakış

Aşağıdaki genel bakış, Microsoft 365'te Oracle verilerini arşivleyen bir bağlayıcı kullanma işlemini açıklar.

![Oracle verilerinde Cisco Jabber için arşivleme iş akışı.](../media/CiscoJabberOnOracleConnectorWorkflow.png)

1. Kuruluşunuz Oracle'da Cisco Jabber ile birlikte çalışarak Oracle sitesinde Cisco Jabber'ı ayarlayıp yapılandırabilir.

2. 24 saatte bir Oracle'da Cisco Jabber öğeleri Veritas Merge1 sitesine kopyalanır. Bağlayıcı ayrıca Oracle öğelerindeki Cisco Jabber'ı e-posta iletisi biçimine dönüştürür.

3. Uyumluluk portalında oluşturduğunuz Oracle üzerinde Cisco Jabber bağlayıcısı, her gün Veritas Merge1 sitesine bağlanır ve Jabber içeriğini Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır.

4. Bağlayıcı, [3. Adımda](#step-3-map-users-and-complete-the-connector-setup) açıklandığı gibi otomatik kullanıcı eşlemesinin *Email* özelliğinin değerini kullanarak dönüştürülen öğeleri belirli kullanıcıların posta kutularına aktarır. Kullanıcı posta kutularında **Oracle üzerinde Cisco Jabber** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bunu *Email* özelliğinin değerini kullanarak yapar. Her Jabber öğesi, öğenin her katılımcısının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için bir Merge1 hesabı oluşturun. Bunu yapmak için [Veritas Müşteri Desteği'ne](https://www.veritas.com/content/support/en_US) başvurun. 1. Adımda bağlayıcıyı oluştururken bu hesapta oturum açmanız gerekir.

- 1. Adımda Oracle bağlayıcısında Cisco Jabber oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için, [Microsoft Purview uyumluluk portalı İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu Veritas veri bağlayıcısı, Microsoft 365 US Government bulutundaki GCC ortamlarında genel önizleme aşamasındadır. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerini Microsoft 365 altyapısının dışındaki üçüncü taraf sistemlerde depolamayı, iletmeyi ve işlemeyi içerebilir ve bu nedenle Microsoft Purview ve veri koruma taahhütleri kapsamında değildir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="step-1-set-up-the-cisco-jabber-on-oracle-connector"></a>1. Adım: Oracle bağlayıcısı üzerinde Cisco Jabber'ı ayarlama

İlk adım, uyumluluk portalındaki **Veri Bağlayıcıları** sayfasına erişmek ve Jabber verileri için bir bağlayıcı oluşturmaktır.

1. <https://compliance.microsoft.com> Adresine gidin ve Oracle'da **Veri bağlayıcıları** > **Cisco Jabber'a** tıklayın.

2. **Oracle'da Cisco Jabber** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın.

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve **İleri'ye** tıklayın.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızda oturum açın.

## <a name="step-2-configure-the-cisco-jabber-on-oracle-on-the-veritas-merge1-site"></a>2. Adım: Veritas Merge1 sitesinde Oracle'da Cisco Jabber'ı yapılandırma

İkinci adım, Veritas Merge1 sitesinde Oracle bağlayıcısı üzerinde Cisco Jabber'ı yapılandırmaktır. Oracle bağlayıcısı üzerinde Cisco Jabber'ı yapılandırma hakkında bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20Oracle%20User%20Guide.pdf).

**Kaydet & Son'a** tıkladıktan sonra, uyumluluk portalındaki bağlayıcı sihirbazındaki **Kullanıcı eşleme** sayfası görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve uyumluluk portalında bağlayıcı kurulumunu tamamlamak için şu adımları izleyin:

1. **Oracle kullanıcılarını Microsoft 365 kullanıcıları ile eşleme** sayfasında, otomatik kullanıcı eşlemesini etkinleştirin. Oracle öğelerindeki Cisco Jabber, kuruluşunuzdaki kullanıcıların *e-posta adreslerini içeren E-posta* adlı bir özellik içerir. Bağlayıcı bu adresi bir Microsoft 365 kullanıcısı ile ilişkilendirebiliyorsa, öğeler söz konusu kullanıcının posta kutusuna aktarılır.

2. **İleri'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları** sayfasına gidin.

## <a name="step-4-monitor-the-cisco-jabber-on-oracle-connector"></a>4. Adım: Oracle bağlayıcısı üzerinde Cisco Jabber'ı izleme

Oracle bağlayıcısında Cisco Jabber'ı oluşturduktan sonra bağlayıcının durumunu uyumluluk portalında görüntüleyebilirsiniz.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com/> gidin ve tıklayın.

2. **Bağlayıcılar** sekmesine tıklayın ve ardından **Oracle'da Cisco Jabber** bağlayıcısını seçerek bağlayıcının özelliklerini ve bilgilerini içeren açılır sayfayı görüntüleyin.

3. Bağlayıcının durum günlüğünü açmak (veya kaydetmek) için **Kaynakla bağlayıcı durumu** altında **Günlüğü indir** bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan veriler hakkında bilgi içerir. Daha fazla bilgi için bkz. [Veri bağlayıcıları için yönetici günlüklerini görüntüleme](data-connector-admin-logs.md).

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.
