---
title: Microsoft 365'da Skype Kurumsal verileri arşivleye bir bağlayıcı ayarlama
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
description: Skype Kurumsal'dan Microsoft 365 verileri içeri aktarmak ve arşivlerken Microsoft Purview uyumluluk portalı bağlayıcıyı ayarlamayı ve kullanmayı öğrenin.
ms.openlocfilehash: 8b824a8ac0db74d639c402bdec9e0894078b2dea
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65415958"
---
# <a name="set-up-a-connector-to-archive-skype-for-business-data"></a>Skype Kurumsal verilerini arşivleye bir bağlayıcı ayarlama

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Microsoft 365 kuruluşunuzdaki kullanıcı posta kutularına Skype Kurumsal platformundaki verileri içeri aktarmak ve arşivlerken Microsoft Purview uyumluluk portalı bir Veritas bağlayıcısı kullanın. Veritas, üçüncü taraf veri kaynağından öğeleri yakalamak (düzenli olarak) ve bu öğeleri [Microsoft 365](https://www.veritas.com/en/au/insights/merge1/skype-for-business) aktarmak için yapılandırılmış bir Skype Kurumsal bağlayıcısı sağlar. Bağlayıcı, kullanıcılar arasındaki iletiler, kalıcı sohbetler ve konferans iletileri gibi içerikleri Skype Kurumsal e-posta iletisi biçimine dönüştürür ve ardından bu öğeleri Microsoft 365'da kullanıcının posta kutusuna aktarır.

Skype Kurumsal veriler kullanıcı posta kutularında depolandıktan sonra, Dava Tutma, eBulma, bekletme ilkeleri ve bekletme etiketleri gibi Microsoft Purview özellikleri uygulayabilirsiniz. Microsoft 365'de verileri içeri aktarmak ve arşivlerken Skype Kurumsal bağlayıcı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-skype-for-business-data"></a>Skype Kurumsal verileri arşivlemeye genel bakış

Aşağıdaki genel bakış, Skype Kurumsal verilerini Microsoft 365'de arşivleyemek için bağlayıcı kullanma işlemini açıklar.

![Skype Kurumsal veriler için iş akışı arşivleme.](../media/SkypeforBusinessConnectorWorkflow.png)

1. Kuruluşunuz bir Skype Kurumsal sitesi ayarlamak ve yapılandırmak için Skype Kurumsal ile çalışır.

2. Her 24 saatte bir, Skype Kurumsal öğeler Veritas Merge1 sitesine kopyalanır. Bağlayıcı ayrıca Skype Kurumsal öğeleri e-posta iletisi biçimine dönüştürür.

3. Uyumluluk portalında oluşturduğunuz Skype Kurumsal bağlayıcısı her gün Veritas Merge1 sitesine bağlanır ve Skype Kurumsal içeriğini Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır.

4. Bağlayıcı, [3. Adımda](#step-3-map-users-and-complete-the-connector-setup) açıklandığı gibi otomatik kullanıcı eşlemesinin *Email* özelliğinin değerini kullanarak dönüştürülen öğeleri belirli kullanıcıların posta kutularına aktarır. Kullanıcı posta kutularında **Skype Kurumsal** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bunu *Email* özelliğinin değerini kullanarak yapar. Her Skype Kurumsal öğesi, öğenin her katılımcısının e-posta adresiyle doldurulmuş olan bu özelliği içerir.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Microsoft bağlayıcıları için bir Merge1 hesabı oluşturun. Bunu yapmak için [Veritas Müşteri Desteği'ne](https://www.veritas.com/form/requestacall/ms-connectors-contact.html) başvurun. 1. Adımda bağlayıcıyı oluştururken bu hesapta oturum açmanız gerekir.

- 1. Adımda Skype Kurumsal bağlayıcısını oluşturan (ve 3. Adımda tamamlayan) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için, [Microsoft Purview uyumluluk portalı İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

- Bu Veritas veri bağlayıcısı, Microsoft 365 ABD Kamu bulutundaki GCC ortamlarda genel önizleme aşamasındadır. Üçüncü taraf uygulamalar ve hizmetler, kuruluşunuzun müşteri verilerinin Microsoft 365 altyapısı dışında olan ve bu nedenle Microsoft Purview ve veri koruma taahhütleri kapsamında olmayan üçüncü taraf sistemlerde depolanmasını, iletilmesini ve işlenmesini içerebilir. Microsoft, üçüncü taraf uygulamalara bağlanmak için bu ürünün kullanıldığının, bu üçüncü taraf uygulamaların FEDRAMP uyumlu olduğunu ifade ettiğini ifade etmemektedir.

## <a name="step-1-set-up-the-skype-for-business-connector"></a>1. Adım: Skype Kurumsal bağlayıcısını ayarlama

İlk adım, uyumluluk portalındaki **Veri Bağlayıcıları** sayfasına erişmek ve Skype Kurumsal veriler için bir bağlayıcı oluşturmaktır.

1. Adresine gidin ve **Veri bağlayıcıları** >  **Skype Kurumsal'na**<https://compliance.microsoft.com> tıklayın.

2. **Skype Kurumsal** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın.

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve **İleri'ye** tıklayın.

5. Bağlayıcıyı yapılandırmak için Merge1 hesabınızda oturum açın.

## <a name="step-2-configure-the-skype-for-business-on-the-veritas-merge1-site"></a>2. Adım: Veritas Merge1 sitesinde Skype Kurumsal yapılandırma

İkinci adım, Veritas Merge1 sitesinde Skype Kurumsal bağlayıcısını yapılandırmaktır. Skype Kurumsal bağlayıcısını yapılandırma hakkında bilgi için bkz. [Birleştirme1 Üçüncü Taraf Bağlayıcıları Kullanıcı Kılavuzu](https://docs.ms.merge1.globanetportal.com/Merge1%20Third-Party%20Connectors%20Skype%20for%20Business%20%20User%20Guide.pdf).

**Kaydet & Son'a** tıkladıktan sonra, uyumluluk portalındaki bağlayıcı sihirbazındaki **Kullanıcı eşleme** sayfası görüntülenir.

## <a name="step-3-map-users-and-complete-the-connector-setup"></a>3. Adım: Kullanıcıları eşleme ve bağlayıcı kurulumunu tamamlama

Kullanıcıları eşlemek ve uyumluluk portalında bağlayıcı kurulumunu tamamlamak için şu adımları izleyin:

1. **Kullanıcıları Microsoft 365 kullanıcılarla eşleme Skype Kurumsal** sayfasında otomatik kullanıcı eşlemesini etkinleştirin. Skype Kurumsal öğeleri, kuruluşunuzdaki kullanıcıların *e-posta adreslerini içeren E-posta* adlı bir özellik içerir. Bağlayıcı bu adresi bir Microsoft 365 kullanıcıyla ilişkilendirebiliyorsa, öğeler söz konusu kullanıcının posta kutusuna aktarılır.

2. **İleri'ye** tıklayın, ayarlarınızı gözden geçirin ve yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları** sayfasına gidin.

## <a name="step-4-monitor-the-skype-for-business-connector"></a>4. Adım: Skype Kurumsal bağlayıcısını izleme

Skype Kurumsal bağlayıcısını oluşturduktan sonra bağlayıcının durumunu uyumluluk portalında görüntüleyebilirsiniz.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com/> gidin ve tıklayın.

2. **Bağlayıcılar** sekmesine tıklayın ve bağlayıcı hakkındaki özellikleri ve bilgileri içeren açılır sayfayı görüntülemek için **Skype Kurumsal** bağlayıcısını seçin.

3. Bağlayıcının durum günlüğünü açmak (veya kaydetmek) için **Kaynakla bağlayıcı durumu** altında **Günlüğü indir** bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan veriler hakkında bilgi içerir. Daha fazla bilgi için bkz. [Veri bağlayıcıları için yönetici günlüklerini görüntüleme](data-connector-admin-logs.md).

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.
