---
title: Microsoft 365'da Çalışma Alanı'nı Facebook verilerinden arşivleyemek için bağlayıcı ayarlama
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
description: Yöneticiler, Veritas'ın Merge1 sitesinde arşivlenen Facebook'un Çalışma Alanı'ndan verileri Microsoft 365 içeri aktarmak ve arşivlemesi için bir bağlayıcı ayarlayabilir. Bağlayıcıyı ayarlamak için Veritas ile çalışmanız gerekir Bu bağlayıcı, kuruluşunuzun üçüncü taraf verilerini yönetmek için yasal saklama, içerik arama ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilmeniz için Microsoft 365'da üçüncü taraf veri kaynaklarından verileri arşivleyebilmenizi sağlar.
ms.openlocfilehash: 63fe30e8d8c264976c496480df056746b7b27ae5
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65317076"
---
# <a name="set-up-a-connector-to-archive-workplace-from-facebook-data"></a>Facebook verilerinden Workplace'i arşivleye bir bağlayıcı ayarlama

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

çalışma alanında bulunan verileri Facebook'tan Microsoft 365 kuruluşunuzdaki kullanıcı posta kutularına aktarmak ve arşivlemek için Microsoft Purview uyumluluk portalı bir Veritas bağlayıcısı kullanın. Veritas, üçüncü taraf veri kaynağından öğeleri yakalamak (düzenli olarak) ve bu öğeleri Microsoft 365'a aktarmak için yapılandırılmış bir [Facebook İş Yeri](https://globanet.com/workplace/) bağlayıcısı sağlar. Bağlayıcı, çalışma alanındaki sohbetler, ekler, gönderiler ve videolar gibi içeriği e-posta iletisi biçimine dönüştürür ve ardından bu öğeleri Microsoft 365'deki kullanıcı posta kutularına aktarır.

Çalışma Alanı verileri kullanıcı posta kutularında depolandıktan sonra, Dava Tutma, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi Microsoft Purview özellikleri uygulayabilirsiniz. Microsoft 365'da verileri içeri aktarmak ve arşivlemek için Facebook'tan Workplace bağlayıcısını kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-workplace-from-facebook-data"></a>Facebook verilerinden Çalışma Alanı'nın arşivlenmesine genel bakış

Aşağıdaki genel bakış, Microsoft 365'da Workplace verilerini arşivlerken bağlayıcı kullanma işlemini açıklar.

![Facebook verilerinden Çalışma Alanı için iş akışını arşivleme.](../media/WorkplaceConnectorWorkflow.png)

1. Kuruluşunuz, Bir Çalışma Alanı sitesi ayarlamak ve yapılandırmak için Facebook'tan Workplace ile birlikte çalışır.

2. 24 saatte bir Çalışma Alanı'ndan alınan öğeler Veritas Merge1 sitesine kopyalanır. Bağlayıcı ayrıca bu öğelerin içeriğini e-posta iletisi biçimine dönüştürür.

3. Uyumluluk portalında oluşturduğunuz Facebook'tan Çalışma Alanı bağlayıcısı, Veritas Merge1'e her gün bağlanır ve Workplace öğelerini Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır.

4. Bağlayıcı, 3. Adımda açıklandığı gibi otomatik kullanıcı eşlemesinin *Email* özelliğinin değerini kullanarak dönüştürülen öğeleri belirli kullanıcıların posta kutularına aktarır. Gelen Kutusu klasöründe **Facebook'tan Workplace** adlı bir alt klasör oluşturulur ve Çalışma Alanı öğeleri bu klasöre aktarılır. Bağlayıcı bunu *Email* özelliğinin değerini kullanarak yapar. Her Çalışma Alanı öğesi, her sohbetin veya gönderi katılımcısının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için bir Veritas Merge1 hesabı oluşturun. Bu hesabı oluşturmak için [Veritas Müşteri Desteği'ne](https://globanet.com/ms-connectors-contact) başvurun. 1. Adımda bağlayıcıyı oluştururken bu hesapta oturum açarsınız.

- Uyumluluk ve eBulma amacıyla API'ler aracılığıyla Workplace'den veri almak için adresinde https://my.workplace.com/work/admin/apps/ özel bir tümleştirme oluşturun.

   Tümleştirmeyi oluştururken Workplace platformu, kimlik doğrulaması için kullanılan belirteçleri oluşturmak için kullanılan bir dizi benzersiz kimlik bilgisi oluşturur. Bu belirteçler, 2. Adım'daki Facebook bağlayıcı yapılandırma sihirbazındaki Çalışma Alanı'nda kullanılır. Uygulamaları oluşturma hakkında adım adım yönergeler için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Workplace%20from%20Facebook%20User%20Guide%20.pdf).

- 1. Adımda Facebook bağlayıcısından Çalışma Alanı oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için, [Microsoft Purview uyumluluk portalı İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu Veritas veri bağlayıcısı, Microsoft 365 ABD Kamu bulutundaki GCC ortamlarda genel önizleme aşamasındadır. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerinin Microsoft 365 altyapısı dışında olan ve bu nedenle Microsoft Purview ve veri koruma taahhütleri kapsamında olmayan üçüncü taraf sistemlerde depolanmasını, iletilmesini ve işlenmesini içerebilir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="step-1-set-up-the-workplace-from-facebook-connector"></a>1. Adım: Facebook bağlayıcısından Çalışma Alanını ayarlama

İlk adım, uyumluluk portalındaki **Veri Bağlayıcıları** sayfasına erişmek ve Workplace verileri için bir bağlayıcı oluşturmaktır.

1. [https://compliance.microsoft.com](https://compliance.microsoft.com/) Adresine gidin ve **Ardından Veri bağlayıcıları** >  **Facebook'tan iş yeri'ne** tıklayın.

2. **Facebook'tan Çalışma Alanı** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın.

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve **İleri'ye** tıklayın.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızda oturum açın.

## <a name="step-2-configure-the-workplace-from-facebook-connector-on-the-veritas-merge1-site"></a>2. Adım: Veritas Merge1 sitesindeki Facebook bağlayıcısından Çalışma Alanını yapılandırma

İkinci adım, Merge1 sitesindeki Facebook'tan Çalışma Alanı bağlayıcısını yapılandırmaktır. Facebook bağlayıcısından Çalışma Alanı'nı yapılandırma hakkında bilgi için bkz. [Merge1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Workplace%20from%20Facebook%20User%20Guide%20.pdf).

**Kaydet & Son'a** tıkladıktan sonra, uyumluluk portalındaki bağlayıcı sihirbazındaki **Kullanıcı eşleme** sayfası görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve uyumluluk portalında bağlayıcı kurulumunu tamamlamak için şu adımları izleyin:

1. **Dış kullanıcıları Microsoft 365 kullanıcılarla eşle** sayfasında otomatik kullanıcı eşlemesini etkinleştirin. Çalışma alanı öğeleri, kuruluşunuzdaki kullanıcılar için *e-posta* adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir Microsoft 365 kullanıcıyla ilişkilendirebiliyorsa, öğeler söz konusu kullanıcının posta kutusuna aktarılır.

2. **İleri'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları** sayfasına gidin.

## <a name="step-4-monitor-the-workplace-from-facebook-connector"></a>4. Adım: Facebook bağlayıcısından Çalışma Alanını izleme

Facebook bağlayıcısından Çalışma Alanı'nı oluşturduktan sonra bağlayıcının durumunu uyumluluk portalında görüntüleyebilirsiniz.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** [https://compliance.microsoft.com](https://compliance.microsoft.com) gidin ve tıklayın.

2. **Bağlayıcılar** sekmesine tıklayın ve açılır sayfayı görüntülemek için **Facebook'tan Çalışma Alanı** bağlayıcısını seçin. Bu sayfa, bağlayıcı hakkındaki özellikleri ve bilgileri içerir.

3. Bağlayıcının durum günlüğünü açmak (veya kaydetmek) için **Kaynakla bağlayıcı durumu** altında **Günlüğü indir** bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan veriler hakkında bilgi içerir. Daha fazla bilgi için bkz. [Veri bağlayıcıları için yönetici günlüklerini görüntüleme](data-connector-admin-logs.md).

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.