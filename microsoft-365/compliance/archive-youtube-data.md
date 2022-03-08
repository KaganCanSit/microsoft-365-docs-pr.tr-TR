---
title: YouTube verilerini aynı dosyada arşivlemek için bir bağlayıcı Microsoft 365
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
description: Yöneticiler, YouTube verilerini Veritas'tan Veritas'a aktaracak ve arşivley için bir bağlayıcı Microsoft 365. Bu bağlayıcı, iş yerinde üçüncü taraf veri kaynaklarından verileri Microsoft 365. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal saklama, eKbulma ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: 0441299c7c0d58855685393526504e2e355343ad
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328239"
---
# <a name="set-up-a-connector-to-archive-youtube-data"></a>YouTube verilerini arşivlemek için bağlayıcı ayarlama

Microsoft 365 uyumluluk merkezi'da bir Veritas bağlayıcısı kullanarak YouTube'dan kendi Microsoft 365 ve kullanıcı posta kutularına veri aktarın. Veritas, üçüncü taraf bir veri kaynağından öğeleri yakalayan ve bu öğeleri başka bir kaynaktan içeri aktaracak şekilde yapılandırılmış bir Microsoft 365. Bağlayıcı, YouTube'dan sohbetler, ekler, görevler, notlar ve gönderiler gibi içerikleri bir e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri Microsoft 365'ta kullanıcı posta kutularına aktarıyor.

YouTube verileri kullanıcı posta kutularında depolendikten sonra, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri gibi uyumluluk özelliklerini uygulayabilirsiniz. YouTube bağlayıcısı kullanarak verileri başka bir kuruluşta içeri aktarın ve Microsoft 365, kurum kurum ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-youtube-data"></a>YouTube verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, YouTube verilerini otomatik olarak bir bağlayıcı kullanarak arşivleme işlemi Microsoft 365.

![YouTube verileri için iş akışı arşivleme.](../media/YouTubeConnectorWorkflow.png)

1. Your organization works with YouTube to set up and configure a YouTube site.

2. Her 24 saatte bir, YouTube öğeleri Veri Kaynağı Birleştirme1 sitesine kopyalanır. Bağlayıcı, YouTube öğelerini de e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi'ta oluşturdukları YouTube bağlayıcısı, her gün VeriTas Merge1 sitesine bağlanır ve YouTube içeriğini Microsoft Depolama güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı, dönüştürülmüş öğeleri, 3. Adımda açıklandığı gibi otomatik kullanıcı eşlemesinde *E-posta* özelliğinin değerini kullanarak belirli kullanıcıların posta [kutularına içeri aktarıyor](#step-3-map-users-and-complete-the-connector-setup). Kullanıcı posta kutularında **YouTube** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her YouTube öğesi, öğenin tüm katılımcılarının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir Merge1 hesabı oluşturun. Bu hesabı oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://www.veritas.com/form/requestacall/ms-connectors-contact). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- YouTube hesabından veri getirmek için bir YouTube uygulaması oluşturun. Uygulamayı oluşturma hakkında adım adım yönergeler için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20YouTube%20User%20Guide.pdf).

- 1. Adımda YouTube bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="step-1-set-up-the-youtube-connector"></a>1. Adım: YouTube bağlayıcıyı ayarlama

İlk adım, videonun son **sayfasındaki Veri Bağlayıcıları** sayfasına erişmek Microsoft 365 uyumluluk merkezi YouTube verileri için bir bağlayıcı oluşturmaktır.

1. Veri bağlayıcılarıYouTube'a <https://compliance.microsoft.com> **gidin ve bu öğeye** >  **tıklayın**.

2. **YouTube ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-youtube-on-the-veritas-merge1-site"></a>2. Adım: VeriTas Merge1 sitesinde YouTube'u yapılandırma

İkinci adım, Veritas Merge1 sitesinde YouTube bağlayıcıyı yapılandırmaktır. YouTube bağlayıcısı yapılandırma hakkında daha fazla bilgi için bkz. [Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20YouTube%20User%20Guide.pdf) Birleştirme.

Son Olarak Kaydet **& i** tıklatmanın ardından, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi sayfası görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve aşağıdaki adımları takip etmek için Microsoft 365 uyumluluk merkezi izleyin:

1. **YouTube kullanıcılarını kullanıcı eşleme Microsoft 365,** otomatik kullanıcı eşlemesini etkinleştirin. YouTube öğeleri, kurumdaki *kullanıcıların e-posta* adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcıya yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-youtube-connector"></a>4. Adım: YouTube bağlayıcılarını izleme

YouTube bağlayıcıyı oluşturdukktan sonra, bağlayıcının durumunu hemen Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com/> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve **ardından YouTube** bağlayıcıyı seçerek bağlayıcıyla ilgili özellikleri ve bilgileri içeren açılır sayfayı görüntüleyin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
