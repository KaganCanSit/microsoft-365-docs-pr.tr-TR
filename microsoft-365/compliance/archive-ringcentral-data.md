---
title: RingCentral verilerini aynı dosyada arşivlemek için bağlayıcıyı Microsoft 365
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
description: Yöneticiler, RingCentral verilerini Veritas veri kaynağından içeri aktaracak ve arşivley çaldıracak bir bağlayıcı Microsoft 365. Bu bağlayıcı, iş yerinde üçüncü taraf veri kaynaklarından verileri Microsoft 365. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal saklama, eKbulma ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: 08d61fb21df099beb8b117d390ffe18a7145ecee
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327469"
---
# <a name="set-up-a-connector-to-archive-ringcentral-data"></a>RingCentral verilerini arşivlemek için bağlayıcı ayarlama

RingCentral platformundan kendi Microsoft 365 uyumluluk merkezi posta kutularına veri içeri aktararak bu platformda veri arşivlemek için veritas Microsoft 365 kullanın. Veritas, üçüncü taraf veri kaynağından öğeleri yakalayan ve bu öğeleri başka bir öğeye aktaracak şekilde yapılandırılmış bir [RingCentral](https://www.veritas.com/insights/merge1/ringcentral) Microsoft 365. Bağlayıcı RingCentral'dan sohbetler, ekler, görevler, notlar ve gönderiler gibi içerikleri bir e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri Aynı Microsoft 365'te kullanıcı posta kutularına dönüştürür.

RingCentral verileri kullanıcı posta kutularında depo olduktan sonra, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri gibi uyumluluk özelliklerini uygulayabilirsiniz. Verileri başka bir kuruluşta içeri aktararak ve arşivlenen bir RingCentral bağlayıcısı kullanmak Microsoft 365 düzenleme ve devlet ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-ringcentral-data"></a>RingCentral verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Genel Görünüm'de RingCentral verilerini arşivlemek için bağlayıcı Microsoft 365.

![RingCentral verileri için iş akışı arşivleme.](../media/RingCentralConnectorWorkflow.png)

1. Kuruluş, bir RingCentral sitesi ayarlamak ve yapılandırmak için RingCentral ile birlikte çalışır.

2. RingCentral öğeleri 24 saatte bir VeriTas Merge1 sitesine kopyalanır. Bağlayıcı RingCentral öğelerini de e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi'ta oluşturmakta istediğiniz RingCentral bağlayıcısı, her gün Veritas Merge1 sitesine bağlanır ve RingCentral içeriğini Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı, dönüştürülmüş öğeleri, 3. Adımda açıklandığı gibi otomatik kullanıcı eşlemesinde *E-posta* özelliğinin değerini kullanarak belirli kullanıcıların posta [kutularına içeri aktarıyor](#step-3-map-users-and-complete-the-connector-setup). Kullanıcı posta kutularında Gelen Kutusu klasöründe **RingCentral** adlı bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Tüm RingCentral öğesi, öğenin tüm katılımcılarının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir Merge1 hesabı oluşturun. Bu hesabı oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://www.veritas.com/form/requestacall/ms-connectors-contact). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- RingCentral hesabından veri getirmek için bir RingCentral uygulaması oluşturun. Uygulamayı oluşturma hakkında adım adım yönergeler için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20RingCentral%20User%20Guide.pdf).

- 1. Adımda RingCentral bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-ringcentral-connector"></a>1. Adım: RingCentral bağlayıcıyı ayarlama

İlk adım, ana sayfada Veri **Bağlayıcıları** sayfasına erişmek ve RingCentral verileri Microsoft 365 uyumluluk merkezi bağlayıcı oluşturmaktır.

1. Veri bağlayıcılarıRingCentral'a <https://compliance.microsoft.com> **gidin ve** >  **bu öğeye tıklayın**.

2. **RingCentral ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-ringcentral-on-the-veritas-merge1-site"></a>2. Adım: Veritas Merge1 sitesinde RingCentral'ı yapılandırma

İkinci adım, Veritas Merge1 sitesinde RingCentral bağlayıcısı yapılandırmaktır. RingCentral bağlayıcısı yapılandırma hakkında bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20RingCentral%20User%20Guide.pdf).

Son Olarak Kaydet **& i** tıklatmanın ardından, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi sayfası görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve aşağıdaki adımları takip etmek için Microsoft 365 uyumluluk merkezi izleyin:

1. **Kullanıcıları eşlemek için RingCentral kullanıcılarını Microsoft 365**, otomatik kullanıcı eşlemesini etkinleştirin. RingCentral öğeleri, kurumdaki *kullanıcıların e-posta* adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcıya yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-ringcentral-connector"></a>4. Adım: RingCentral bağlayıcıyı izleme

RingCentral bağlayıcıyı oluşturduktan sonra, bağlayıcının durumunu geçerli görünüm Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com/> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve **ardından RingCentral** bağlayıcıyı seçerek bağlayıcıyla ilgili özellikleri ve bilgileri içeren açılır sayfayı görüntüleyin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
