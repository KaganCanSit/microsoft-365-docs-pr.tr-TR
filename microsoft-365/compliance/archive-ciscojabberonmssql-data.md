---
title: Ms SQL verilerini Microsoft 365'da Cisco Jabber'ı arşivleme bağlayıcısı ayarlama
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
description: Yöneticiler, ms SQL verilerinde Cisco Jabber'ı Microsoft 365'da Veritas'tan içeri aktarmak ve arşivlemek için bir bağlayıcı ayarlayabilir. Bu bağlayıcı, Microsoft 365'da üçüncü taraf veri kaynaklarından verileri arşivleyabilmenizi sağlar. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal tutma, içerik arama ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: ef9586c0e860db727bea53651d70777e7c606498
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65099795"
---
# <a name="set-up-a-connector-to-archive-cisco-jabber-on-ms-sql-data"></a>MS SQL verilerinde Cisco Jabber'ı arşivleme için bağlayıcı ayarlama

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Cisco Jabber platformundaki verileri Microsoft 365 kuruluşunuzdaki kullanıcı posta kutularına aktarmak ve arşivlemek için Microsoft Purview uyumluluk portalında bir Veritas bağlayıcısı kullanın. Veritas, Jabber'ın MS SQL Veritabanı 1:1 sohbet iletileri ve grup sohbetleri gibi öğeleri yakalamak ve ardından bu öğeleri Microsoft 365'a aktarmak için yapılandırılmış bir [Cisco Jabber](https://globanet.com/jabber/) bağlayıcısı sağlar. Bağlayıcı, Cisco Jabber'ın MS SQL Veritabanı verileri alır, işler ve kullanıcının Cisco Jabber hesabındaki içeriği e-posta iletisi biçimine dönüştürür ve ardından bu öğeleri Microsoft 365 kullanıcının posta kutusuna aktarır.

Cisco Jabber verileri kullanıcı posta kutularında depolandıktan sonra, Dava Tutma, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi Microsoft Purview özelliklerini uygulayabilirsiniz. Microsoft 365'de verileri içeri aktarmak ve arşivlemek için Cisco Jabber bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-cisco-jabber-data"></a>Cisco Jabber verilerini arşivlemeyle ilgili genel bakış

Aşağıdaki genel bakış, ms SQL verilerini Microsoft 365'da arşivleme amacıyla bağlayıcı kullanma işlemini açıklar.

![Cisco Jabber verileri için arşivleme iş akışı.](../media/CiscoJabberonMSSQLConnectorWorkflow.png)

1. Kuruluşunuz, MS SQL Veritabanı üzerinde Cisco Jabber ayarlamak ve yapılandırmak için Cisco ile birlikte çalışır.

2. Cisco Jabber öğeleri 24 saatte bir MS SQL Veritabanı Veritas Merge1 sitesine kopyalanır. Bağlayıcı ayrıca sohbet iletilerinin içeriğini e-posta iletisi biçimine dönüştürür.

3. Uyumluluk portalında oluşturduğunuz Cisco Jabber bağlayıcısı her gün Veritas Merge1 sitesine bağlanır ve öğeleri Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır.

4. Bağlayıcı olarak otomatik kullanıcı eşlemesi [, 3. Adımda](#step-3-map-users-and-complete-the-connector-setup) açıklanan *e-posta* özelliğinin değerini kullanarak öğeleri belirli kullanıcıların posta kutularına aktarır. Kullanıcı posta kutularında **MS SQL cisco Jabber** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve ileti öğeleri bu klasöre aktarılır. Bağlayıcı, *E-posta* özelliğinin değerini kullanarak öğelerin hangi posta kutusuna aktarılacağını belirler. Her Cisco Jabber öğesi, her katılımcının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için bir Veritas Merge1 hesabı oluşturun. Bu hesabı oluşturmak için [Veritas Müşteri Desteği'ne](https://www.veritas.com/content/support/) başvurun. 1. Adımda bağlayıcıyı oluştururken bu hesapta oturum açarsınız.

- 1. Adımda bağlayıcıyı oluşturmadan önce Jabber öğelerini almak için bir MS SQL Veritabanı ayarlayın. 2. Adımda Cisco Jabber bağlayıcısını yapılandırırken MS SQL Veritabanı için bağlantı ayarlarını belirtirsiniz. Daha fazla bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf).

- 1. Adımda Cisco Jabber bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için [Microsoft Purview uyumluluk portalındaki İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu Veritas veri bağlayıcısı, Microsoft 365 ABD Kamu bulutundaki GCC ortamlarda genel önizleme aşamasındadır. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerinin Microsoft 365 altyapısı dışında olan ve bu nedenle Microsoft Purview ve veri koruma taahhütleri kapsamında olmayan üçüncü taraf sistemlerde depolanmasını, iletilmesini ve işlenmesini içerebilir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="step-1-set-up-the-cisco-jabber-on-ms-sql-connector"></a>1. Adım: MS SQL bağlayıcısı üzerinde Cisco Jabber'ı ayarlama

İlk adım, uyumluluk portalında **Veri Bağlayıcıları'na** erişmek ve MS SQL verilerinde Cisco Jabber için bir bağlayıcı oluşturmaktır.

1. MS **SQL'da Veri bağlayıcılarıCisco** >  **Jabber'a**[https://compliance.microsoft.com](https://compliance.microsoft.com/) gidin ve tıklayın.

2. **MS'de Cisco Jabber SQL** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın.

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve **İleri'ye** tıklayın.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızda oturum açın.

## <a name="step-2-configure-the-cisco-jabber-on-ms-sql-connector-on-the-veritas-merge1-site"></a>2. Adım: Veritas Merge1 sitesinde MS SQL bağlayıcısı üzerinde Cisco Jabber'ı yapılandırma

İkinci adım, Veritas Merge1 sitesindeki MS SQL bağlayıcısı üzerinde Cisco Jabber'ı yapılandırmaktır. MS SQL bağlayıcısı üzerinde Cisco Jabber'ı yapılandırma hakkında bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Cisco%20Jabber%20on%20MS%20SQL%20User%20Guide%20.pdf).

**Kaydet & Son'a** tıkladıktan sonra, uyumluluk portalındaki bağlayıcı sihirbazındaki **Kullanıcı eşleme** sayfası görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve uyumluluk portalında ayarlanan bağlayıcıyı tamamlamak için şu adımları izleyin:

1. **MS'de Cisco Jabber Eşlemesi SQL kullanıcıları Microsoft 365 sayfasında** otomatik kullanıcı eşlemesini etkinleştirin. MS SQL öğelerinde Cisco Jabber, kuruluşunuzdaki kullanıcıların *e-posta adreslerini içeren E-posta* adlı bir özellik içerir. Bağlayıcı bu adresi bir Microsoft 365 kullanıcıyla ilişkilendirebiliyorsa, öğeler söz konusu kullanıcının posta kutusuna aktarılır.

2. **İleri'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları** sayfasına gidin.

## <a name="step-4-monitor-the-cisco-jabber-connector"></a>4. Adım: Cisco Jabber bağlayıcısını izleme

MS SQL bağlayıcısında Cisco Jabber'ı oluşturduktan sonra uyumluluk portalında bağlayıcı durumunu görüntüleyebilirsiniz.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** [https://compliance.microsoft.com](https://compliance.microsoft.com) gidin ve tıklayın.

2. **Bağlayıcılar** sekmesine tıklayın ve açılır sayfayı görüntülemek için **MS SQL bağlayıcıda Cisco Jabber'ı** seçin. Bu sayfa, bağlayıcı hakkındaki özellikleri ve bilgileri içerir.

3. Bağlayıcının durum günlüğünü açmak (veya kaydetmek) için **Kaynakla bağlayıcı durumu** altında **Günlüğü indir** bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.
