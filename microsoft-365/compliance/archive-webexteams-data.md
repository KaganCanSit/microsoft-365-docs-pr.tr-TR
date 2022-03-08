---
title: Webex bağlayıcısı ayarlama ve Teams verileri Microsoft 365
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
description: Yöneticiler, veritas'ın Webex bağlayıcılarından verileri içeri aktaracak ve arşivley bağlayıcısı Teams bir bağlayıcı Microsoft 365. Bu bağlayıcı, üçüncü taraf veri kaynaklarından verileri Microsoft 365'te arşivlemenize olanak sağlar ve böylece yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanarak kuruluş üçüncü taraf verilerini yönetebilirsiniz.
ms.openlocfilehash: 0906156f5c0c796deaa5bd72738813d912e30b47
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63312313"
---
# <a name="set-up-a-connector-to-archive-webex-teams-data"></a>WebEx verilerini arşivlemek için bağlayıcıyı Teams ayarlama

WebEx Teams'dan kendi Microsoft 365 uyumluluk merkezi posta kutularına veri içeri aktarmak ve arşivlemek için, Microsoft 365 kullanın. Veritas, [Webex iletişim Teams](https://globanet.com/webex-teams/) öğelerini yakalamak ve içeri aktararak Webex iletişim öğelerini yakalamak Teams bir Webex Microsoft 365. Bağlayıcı, Webex Teams'dan alınan bire bir sohbetler, grup konuşmaları, kanal konuşmaları ve ekleri gibi içerikleri kurumnizin Webex Teams hesabından e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri Microsoft 365'da kullanıcının posta kutusuna dönüştürür.

Webex Teams verilerini kullanıcı posta kutularında depoladikten sonra, Microsoft 365 Saklama, eBulma, bekletme ilkeleri ve bekletme etiketleri ve iletişim uyumluluğu gibi uyumluluk özelliklerini uygulayabilirsiniz. Webex web Teams bağlayıcısı kullanarak verileri kendi web sitesinde içeri Microsoft 365 arşivlemek, kuruluşlarının resmi ve mevzuat ilkeleriyle uyumlu kalmasını sağlar.

## <a name="overview-of-archiving-webex-teams-data"></a>WebEx verilerini arşivlemeye Teams genel bakış

Aşağıdaki genel bakış makalesinde, WebEx'i arşivlerken bağlayıcı kullanma Teams açık Microsoft 365.

![WebEx için iş akışı Teams arşivleme.](../media/WebexTeamsConnectorWorkflow.png)

1. Webex web sitesi Teams ayarlamak ve yapılandırmak için, Webex web Teams çalışır.

2. Webex her 24 saatte bir, Teams Veri Görev Birleştirme1 sitesine kopyalanır. Bağlayıcı, Webex öğelerini Teams-posta iletisi biçimine de dönüştürür.

3. Microsoft 365 uyumluluk merkezi'ta Teams Webex Teams bağlayıcısı, her gün VeriTas Birleştirme1'e bağlanır ve Webex Teams öğelerini Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor.

4. Bağlayıcı, otomatik kullanıcı eşlemesinde E-posta özelliğinin değerini 3. Adımda açıklandığı gibi kullanarak  öğeleri belirli kullanıcıların posta [kutularına içeri aktarıyor](#step-3-map-users-and-complete-the-connector-setup). Kullanıcı posta kutularında **Webex Teams** Gelen Kutusu klasöründe bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bunu, E-posta özelliğinin *değerini kullanarak* yapar. Her Webex Teams bu özelliği içerir; bu özellik, öğenin tüm katılımcılarının e-posta adresiyle doldurulur.

## <a name="before-you-begin"></a>Başlamadan önce

- Microsoft bağlayıcıları için VeriTas Merge1 hesabı oluşturun. Bu hesabı oluşturmak için [Veritas Müşteri Desteği'ne başvurun](https://globanet.com/ms-connectors-contact). 1. Adım'da bağlayıcıyı  oluşturmak için bu hesapta oturum açın.

- WebEx Teams [https://developer.webex.com/](https://developer.webex.com) hesabından veri getirmek için Teams oluşturun. Uygulamayı oluşturma hakkında adım adım yönergeler için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Webex%20Teams%20User%20Guide%20.pdf)

   Bu uygulamayı  oluşturmak için, Webex platformu bir dizi benzersiz kimlik bilgisi üretir. Bu kimlik bilgileri, Genel Birleştirme1 sitesinde WebEx bağlayıcısı Teams 2. Adımda kullanılır.

- 1. Adımda Webex Teams bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanabilir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

- Bu Veritas veri bağlayıcısı, ABD Kamu bulutu GCC ortamlarda Microsoft 365 önizlemededir. Üçüncü taraf uygulamaları ve hizmetleri, kuruluş müşteri verilerini Microsoft 365 altyapısının dışında olan üçüncü taraf sistemlerde depolamayı, iletip işlemeyi ve bu nedenle de Microsoft 365 uyumluluk ve veri koruma taahhütleri kapsamında değildir. Microsoft, bu ürünün üçüncü taraf uygulamalara bağlanmak için kullanılabileceğiyle ilgili hiçbir beyanda yoktur ve bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu da ima eder.

## <a name="step-1-set-up-the-webex-teams-connector"></a>1. Adım: Webex bağlayıcısı Teams ayarlama

İlk adım, Veri **Bağlayıcıları'ne erişim kazanmak ve** [Webex bağlayıcısı bağlayıcısı'Teams](https://globanet.com/webex-teams/) ayarlamaktır.

1. Veri **bağlayıcılarıWebex**[https://compliance.microsoft.com](https://compliance.microsoft.com/) **Bağlantı'ya gidin ve** >  Teams.

2. **Webex Ürün Teams** ekle sayfasında Bağlayıcı **ekle'ye tıklayın**.

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızla oturum açın.

## <a name="step-2-configure-the-webex-teams-connector-on-the-veritas-merge1-site"></a>2. Adım: Veritas Birleştirme1 Teams WebEx webex bağlayıcısı bağlayıcısı yapılandırma

İkinci adım, Merge1 sitesinde Webex Teams bağlayıcıyı yapılandırmaktır. WebEx Bağlayıcısı Bağlayıcısı'nın nasıl yapılandır Teams için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Webex%20Teams%20User%20Guide%20.pdf).

Son Olarak Kaydet **& e tıklarken**, sihirbazın  Bağlayıcı sihirbazında Kullanıcı eşleme Microsoft 365 uyumluluk merkezi görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve aşağıdaki adımları takip etmek için Microsoft 365 uyumluluk merkezi izleyin:

1. **Webex Kullanıcılarını Eşle Teams eşleme Microsoft 365 otomatik** kullanıcı eşlemesini etkinleştirin. Webex Teams, organizasyondaki kullanıcıların *e-posta* adreslerini içeren E-posta adlı bir özellik içerir. Bağlayıcı bu adresi bir kullanıcıyla Microsoft 365, öğeler o kullanıcının posta kutusuna aktarılır.

2. **Sonraki'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcıya yönelik içeri aktarma işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="step-4-monitor-the-webex-teams-connector"></a>4. Adım: WebEx Teams izleme

Webex bağlayıcısı Teams, bağlayıcının durumunu bağlayıcının iki Microsoft 365 uyumluluk merkezi.

1. Sol gezinti [https://compliance.microsoft.com](https://compliance.microsoft.com) çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve açılır sayfayı **görüntülemek Teams WebEx** bağlayıcısı bağlayıcıyı seçin. Bu sayfa, bağlayıcının özelliklerini ve bilgilerini içerir.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan veriler hakkında bilgi içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.