---
title: Microsoft 365'de Salesforce Chatter verilerini arşivleye bir bağlayıcı ayarlama
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
description: Yöneticiler, Salesforce Chatter verilerini Veritas'tan Microsoft 365 içeri aktarmak ve arşivlemek için bir bağlayıcı ayarlayabilir. Bu bağlayıcı, Microsoft 365'da üçüncü taraf veri kaynaklarından verileri arşivleyabilmenizi sağlar. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal tutma, içerik arama ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: 8d86b4fcddcdf4a0f9b169b32df152873e8211c7
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64758629"
---
# <a name="set-up-a-connector-to-archive-salesforce-chatter-data"></a>Salesforce Chatter verilerini arşivleye bağlayıcı ayarlama

Salesforce Chatter platformundaki verileri Microsoft 365 kuruluşunuzdaki kullanıcı posta kutularına aktarmak ve arşivlerken Microsoft 365 uyumluluk merkezi bir Veritas bağlayıcısı kullanın. Veritas, üçüncü taraf veri kaynağından öğeleri yakalayan ve bu öğeleri Microsoft 365 aktaran bir [Salesforce Chatter](http://globanet.com/chatter/) bağlayıcısı sağlar. Bağlayıcı sohbetler, ekler ve gönderiler gibi içeriği Salesforce Chatter'dan e-posta iletisi biçimine dönüştürür ve ardından bu öğeleri Microsoft 365'da kullanıcının posta kutusuna aktarır.

Salesforce Chatter verileri kullanıcı posta kutularında depolandıktan sonra, Dava Tutma, eBulma, bekletme ilkeleri ve bekletme etiketleri gibi Microsoft 365 uyumluluk özelliklerini uygulayabilirsiniz. Microsoft 365'de verileri içeri aktarmak ve arşivlerken Salesforce Chatter bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-salesforce-chatter-data"></a>Salesforce Chatter verilerini arşivlemeyle ilgili genel bakış

Aşağıdaki genel bakışta, Microsoft 365'da Salesforce Chatter verilerini arşivleyen bir bağlayıcı kullanma işlemi açıklanmaktadır.

![Salesforce Chatter verileri için iş akışı arşivleme.](../media/SalesforceChatterConnectorWorkflow.png)

1. Kuruluşunuz bir Salesforce Chatter sitesi ayarlamak ve yapılandırmak için Salesforce Chatter ile birlikte çalışır.

2. 24 saatte bir Salesforce Chatter öğeleri Veritas Merge1 sitesine kopyalanır. Bağlayıcı ayrıca Salesforce Chatter öğelerini de e-posta iletisi biçiminde görüntüler.

3. Microsoft 365 uyumluluk merkezi oluşturduğunuz Salesforce Chatter bağlayıcısı her gün Veritas Merge1 sitesine bağlanır ve Chatter içeriğini Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır.

4. Bağlayıcı, [3. Adımda](#step-3-map-users-and-complete-the-connector-setup) açıklandığı gibi otomatik kullanıcı eşlemesinin *Email* özelliğinin değerini kullanarak dönüştürülen öğeleri belirli kullanıcıların posta kutularına aktarır. Kullanıcı posta kutularında **Salesforce Chatter** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, *E-posta* özelliğinin değerini kullanarak öğelerin hangi posta kutusuna aktarılacağını belirler. Her Chatter öğesi, öğenin her katılımcısının e-posta adresiyle doldurulmuş olan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için bir Merge1 hesabı oluşturun. Hesap oluşturmak için [Veritas Müşteri Desteği'ne](https://www.veritas.com/content/support/) başvurun. 1. Adımda bağlayıcıyı oluştururken bu hesapta oturum açmanız gerekir.

- Bir Salesforce uygulaması oluşturun ve adresinde [https://salesforce.com](https://salesforce.com)bir belirteç alın. Salesforce hesabında yönetici olarak oturum açmanız ve verileri içeri aktarmak için bir kullanıcı kişisel belirteci almanız gerekir. Ayrıca güncelleştirmeleri, silmeleri ve düzenlemeleri yakalamak için tetikleyicilerin Chatter sitesinde yayımlanması gerekir. Bu tetikleyiciler kanalda bir gönderi oluşturur ve Merge1 kanaldaki bilgileri yakalar. Uygulamayı oluşturma ve belirteci alma hakkında adım adım yönergeler için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20SalesForce%20Chatter%20User%20Guide%20.pdf).

- 1. Adımda Salesforce Chatter bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, Microsoft 365 uyumluluk merkezi **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için, [Microsoft 365 uyumluluk merkezi İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu Veritas veri bağlayıcısı, Microsoft 365 ABD Kamu bulutundaki GCC ortamlarda genel önizleme aşamasındadır. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerinin Microsoft 365 altyapısının dışındaki üçüncü taraf sistemlerde depolanmasını, iletilmesini ve işlenmesini içerebilir ve bu nedenle Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="step-1-set-up-the-salesforce-chatter-connector"></a>1. Adım: Salesforce Chatter bağlayıcısını ayarlama

İlk adım, Microsoft 365 uyumluluk merkezi **Veri Bağlayıcıları** sayfasına erişmek ve Chatter verileri için bir bağlayıcı oluşturmaktır.

1. **Veri bağlayıcılarıSalesforce** >  **Chatter'a**[https://compliance.microsoft.com](https://compliance.microsoft.com/) gidin ve tıklayın.

2. **Salesforce Chatter** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın.

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve **İleri'ye** tıklayın.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızda oturum açın.

## <a name="step-2-configure-the-salesforce-chatter-on-the-veritas-merge1-site"></a>2. Adım: Veritas Merge1 sitesinde Salesforce Chatter'ı yapılandırma

İkinci adım, Veritas Merge1 sitesinde Salesforce Chatter bağlayıcısını yapılandırmaktır. Salesforce Chatter bağlayıcısını yapılandırma hakkında bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20SalesForce%20Chatter%20User%20Guide%20.pdf).

**Son & Kaydet'e** tıkladıktan sonra, Microsoft 365 uyumluluk merkezi bağlayıcı sihirbazındaki **Kullanıcı eşleme** sayfası görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve Microsoft 365 uyumluluk merkezi bağlayıcı kurulumunu tamamlamak için şu adımları izleyin:

1. **Salesforce Chatter kullanıcılarını Microsoft 365 kullanıcılarla eşle** sayfasında otomatik kullanıcı eşlemesini etkinleştirin. Salesforce Chatter öğeleri, kuruluşunuzdaki kullanıcıların *e-posta adreslerini içeren E-posta* adlı bir özellik içerir. Bağlayıcı bu adresi bir Microsoft 365 kullanıcıyla ilişkilendirebiliyorsa, öğeler söz konusu kullanıcının posta kutusuna aktarılır.

2. **İleri'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları** sayfasına gidin.

## <a name="step-4-monitor-the-salesforce-chatter-connector"></a>4. Adım: Salesforce Chatter bağlayıcısını izleme

Salesforce Chatter bağlayıcısını oluşturduktan sonra bağlayıcının durumunu Microsoft 365 uyumluluk merkezi görüntüleyebilirsiniz.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** [https://compliance.microsoft.com](https://compliance.microsoft.com/) gidin ve tıklayın.

2. **Bağlayıcılar** sekmesine tıklayın ve ardından **Salesforce Chatter** bağlayıcısına tıklayarak bağlayıcı hakkındaki özellikleri ve bilgileri içeren açılır sayfayı görüntüleyin.

3. Bağlayıcının durum günlüğünü açmak (veya kaydetmek) için **Kaynakla bağlayıcı durumu** altında **Günlüğü indir** bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.