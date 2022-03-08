---
title: Reuters'in Anlaşma verilerini aynı dosyada arşivlemek için bir bağlayıcı Microsoft 365
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
description: Yöneticiler, Veritas'tan Reuters'e Ilgilenme verilerini içeri aktaracak ve arşivleyacak bir bağlayıcı Microsoft 365. Bu bağlayıcı, iş yerinde üçüncü taraf veri kaynaklarından verileri Microsoft 365. Bu verileri arşivledikten sonra, üçüncü taraf verilerini yönetmek için yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilirsiniz.
ms.openlocfilehash: 7e978af3c0916b277fcf97d9fe58c9b7cea08d43
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63314623"
---
# <a name="set-up-a-connector-to-archive-reuters-dealing-data"></a>Reuters'in Ilgilenme verilerini arşivlemek için bağlayıcı ayarlama

Microsoft 365 uyumluluk merkezi'da Reuters Ilgilenme platformundan kendi Microsoft 365 posta kutularına veri içeri aktarma ve arşivlemek için veri kaynağında bir Veritas Microsoft 365 kullanın. Veritas size üçüncü taraf veri kaynağından (düzenli olarak) öğe yakalamak ve bu öğeleri düzenli olarak içeri aktaracak şekilde yapılandırılmış bir [Reuters](https://globanet.com/reuters-dealing/) Ilgilenme bağlayıcısı Microsoft 365. Bağlayıcı, Reuters Ilgilenme hesabından Satın Alma iletişimlerini bir e-posta iletisi biçimine dönüştürür ve bu öğeleri daha sonra da Microsoft 365.

Reuters'in Ilgilenme verileri kullanıcı posta kutularında depolandıktan sonra, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Bir Reuters Dealing bağlayıcısı kullanarak verileri başka bir kuruluşta içeri aktarın Microsoft 365 arşivler, kuruma devlet ve mevzuat ilkeleriyle uyumlu kalma konusunda yardımcı olabilir.

## <a name="overview-of-archiving-reuters-dealing-data"></a>Reuters'in Anlaşma verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Microsoft'ta Reuters'in Anlaşma verilerini arşivlemek için bağlayıcı kullanma Microsoft 365.

![Reuters'in Ilgilenme verileri için arşivleme iş akışı.](../media/ReuetersDealingConnectorWorkflow.png)

1. Organizasyonunız Reuters'e Karşı Bir Anlaşma sitesi ayarlamak ve yapılandırmak için Reuters Ile Çalışıyor.

2. Her 24 saatte bir, Reuters'in Ilgilenme öğeleri Veritas Merge1 sitesine kopyalanır. Bağlayıcı öğeleri de e-posta iletisi biçimine dönüştürür.

3. Microsoft 365 uyumluluk merkezi'ta oluşturdukları Reuters Ilgilenme bağlayıcısı, her gün Veritas Merge1 sitesine bağlanır ve içeriği Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı, otomatik kullanıcı eşlemesinde E-posta özelliğinin değerini 3. Adımda açıklandığı gibi kullanarak  öğeleri belirli kullanıcıların posta [kutularına içeri aktarıyor](#step-3-map-users-and-complete-the-connector-setup). Kullanıcı posta kutularında **Reuters** Ile Ilgilenme adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, E-posta özelliğinin değerini kullanarak hangi posta kutusuna öğe *aktarılamayacaklarını* belirler. Her Reuters Anlaşma öğesi, öğenin tüm katılımcılarının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için VeriTas Merge1 hesabı oluşturun. Hesap oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://globanet.com/contact-us). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 1. Adımda Reuters Ilgilenme bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yöneticisi rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-reuters-dealing-connector"></a>1. Adım: Reuters'i Ilgilenme bağlayıcısı ayarlama

İlk adım, iş sayfasındaki **Veri Bağlayıcıları** sayfasına erişmek ve Reuters Microsoft 365 verileri için bir bağlayıcı oluşturmaktır.

1. Veri bağlayıcılarıDiyazma'ya [https://compliance.microsoft.com](https://compliance.microsoft.com/) **gidin** >  **ve bu öğeye tıklayın**.

2. Reuters Ilgilenme **ürün açıklaması** sayfasında Bağlayıcı ekle'ye **tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-reuters-dealing-connector-on-the-veritas-merge1-site"></a>2. Adım: Veritas Merge1 sitesinde Reuters Dealing bağlayıcıyı yapılandırma

İkinci adım, Merge1 sitesinde Veritas üzerinde Reuters Dealing bağlayıcısı'nın yapılandırılmasıdır. Reuters Dealing bağlayıcısını yapılandırma hakkında bilgi için bkz. [Merge1 Third-Party Connectors Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Reuters%20Dealing%20User%20Guide%20.pdf).

Son Olarak Kaydet **& e tıklarken**, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve aşağıdaki adımları takip etmek için Microsoft 365 uyumluluk merkezi izleyin:

1. **Reuters Ile Ilgilenme kullanıcılarını Haritada Microsoft 365,** otomatik kullanıcı eşlemesini etkinleştirin.

   Reuters Ilgilenme öğeleri, kurumdaki kullanıcılar için *e-posta* adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ne** tıklayın, ayarlarınızı gözden geçirin ve yeni **bağlayıcıya** yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-reuters-dealing-connector"></a>4. Adım: Reuters Ilgilenme bağlayıcılarını izleme

Reuters Uğraşma bağlayıcısı oluşturdukta, bağlayıcının durumunu ilgili bağlayıcının Microsoft 365 uyumluluk merkezi.

1. Sol gezinti [https://compliance.microsoft.com](https://compliance.microsoft.com/) çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve **sonra Reuters'in** Ilgilenme bağlayıcısı öğesini seçerek bağlayıcıyla ilgili özellikleri ve bilgileri içeren açılır sayfayı görüntüleyin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.