---
title: Verileri tek bir dosyada Skype Kurumsal için bağlayıcıyı Microsoft 365
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
description: Bağlayıcı ayarlamayı ve bu bağlayıcıyı kullanarak bir bağlayıcıyı Microsoft 365 uyumluluk merkezi kaynak dosyadan içeri aktarmayı ve Skype Kurumsal Microsoft 365.
ms.openlocfilehash: 68d89fc4dc71fb3426170efd5005455172f30e9b
ms.sourcegitcommit: 36a19d80fe3f053df0fec398a7ff2dfc777f9730
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2021
ms.locfileid: "63021495"
---
# <a name="set-up-a-connector-to-archive-skype-for-business-data"></a>Verilerinizi arşivlemek için bağlayıcıyı Skype Kurumsal ayarlama

Skype Kurumsal platformundan kendi Microsoft 365 uyumluluk merkezi posta kutularına veri içeri aktarmak ve Microsoft 365 için veritas bağlayıcısı kullanın. Veritas, [Skype Kurumsal](https://www.veritas.com/en/au/insights/merge1/skype-for-business) üçüncü taraf veri kaynağından öğeleri yakalamak ve bu öğeleri belirli bir toplama kaynağına aktaracak şekilde yapılandırılmış bir Microsoft 365. Bağlayıcı, kullanıcılar arasındaki iletiler, kalıcı sohbetler ve konferans iletileri gibi içerikleri Skype Kurumsal'tan e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri Microsoft 365'te kullanıcının posta kutusuna Microsoft 365.

Verileri Skype Kurumsal posta kutularında depoladikten sonra, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri gibi uyumluluk özelliklerini uygulayabilirsiniz. Skype Kurumsal'da verileri içeri aktarma ve arşivlemek için Microsoft 365 düzenleyici bağlayıcısı kullanmak, kurum kuruluş ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-skype-for-business-data"></a>Verileri arşivlemeye Skype Kurumsal genel bakış

Aşağıdaki genel bakış makalesinde, bağlayıcı kullanarak verileri tek bir Skype Kurumsal arşivleme işlemi Microsoft 365.

![Verileri arşivlemek için iş Skype Kurumsal.](../media/SkypeforBusinessConnectorWorkflow.png)

1. Organizasyonunız, en son Skype Kurumsal siteyi ayarlamak ve yapılandırmak için Skype Kurumsal çalışır.

2. Her 24 saatte bir, Skype Kurumsal Veri Görev Birleştirme1 sitesine kopyalanır. Bağlayıcı, öğeleri Skype Kurumsal-posta iletisi biçimine de dönüştürür.

3. Microsoft 365 uyumluluk merkezi'da Skype Kurumsal, veritas Birleştirme1 sitesine her gün bağlanır ve Skype Kurumsal içeriğini Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı, dönüştürülmüş öğeleri, 3. Adımda açıklandığı gibi otomatik kullanıcı eşlemesinde *E-posta* özelliğinin değerini kullanarak belirli kullanıcıların posta [kutularına içeri aktarıyor](#step-3-map-users-and-complete-the-connector-setup). Kullanıcı posta kutularında Gelen Kutusu **klasöründe Skype Kurumsal** adlı bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bunu, E-posta özelliğinin *değerini kullanarak* yapar. Her Skype Kurumsal öğe, öğenin tüm katılımcılarının e-posta adresiyle doldurulan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir Merge1 hesabı oluşturun. Bunu yapmak için [Veritas Müşteri Desteği'ne başvurun](https://www.veritas.com/form/requestacall/ms-connectors-contact.html). Bağlayıcıyı 1. Adımda  oluşturdukta bu hesapta oturum açın.

- 1. Adımda Skype Kurumsal bağlayıcıyı oluşturan (ve 3. Adımda tamamlayan) kullanıcı, Exchange Online'te Posta Kutusu İçeri/Dışarı Aktarma rolüne atan Exchange Online. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-skype-for-business-connector"></a>1. Adım: Yeni bağlayıcıyı Skype Kurumsal ayarlama

İlk adım, ana sayfada Veri **Bağlayıcıları** sayfasına erişmek ve Microsoft 365 uyumluluk merkezi verileri için bir bağlayıcı Skype Kurumsal oluşturmaktır.

1. Veri bağlayıcıları'ne <https://compliance.microsoft.com> **gidin ve Skype Kurumsal** > **.**

2. Ürün **Skype Kurumsal ekle** sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-skype-for-business-on-the-veritas-merge1-site"></a>2. Adım: Veri Skype Kurumsal Birleştirme1 sitesinde belgeyi yapılandırma

İkinci adım, VeriTas Merge1 Skype Kurumsal bağlayıcıyı yapılandırmaktır. Son bağlayıcının nasıl yapılandırıldığından Skype Kurumsal için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Skype%20for%20Business%20%20User%20Guide.pdf).

Son Olarak Kaydet **& e tıklarken**, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve aşağıdaki adımları takip etmek için Microsoft 365 uyumluluk merkezi izleyin:

1. Kullanıcıları **kullanıcı Skype Kurumsal eşleme sayfasında Microsoft 365** eşlemeyi etkinleştirin. En Skype Kurumsal, organizasyondaki *kullanıcıların e-posta* adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcıya yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-skype-for-business-connector"></a>4. Adım: Bağlayıcının Skype Kurumsal izleme

Bağlayıcıyı oluşturduk Skype Kurumsal, bağlayıcının durumunu en son Microsoft 365 uyumluluk merkezi.

1. Sol gezinti <https://compliance.microsoft.com/> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve **Skype Kurumsal özellikleri ve** bağlayıcıyla ilgili bilgileri içeren açılır sayfayı görüntülemek için Bağlayıcılar sekmesini seçin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
