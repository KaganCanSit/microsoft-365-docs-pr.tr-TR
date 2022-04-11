---
title: Microsoft tarafından sağlanan veri bağlayıcısını kullanarak Slack eKeşif verilerini Microsoft 365 arşivle
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
description: Microsoft tarafından sağlanan Slack eKeşif veri bağlayıcısını ayarlamayı ve kullanarak anlık ileti verilerini içeri aktarmayı ve arşivlemeyi öğrenin.
ms.openlocfilehash: 7ff8140ee75c146f79f14fbd474ab4e6780156ad
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64760899"
---
# <a name="set-up-a-connector-to-archive-slack-ediscovery-data-preview"></a>Slack eKeşif verilerini arşivleme (önizleme) için bağlayıcı ayarlama

Microsoft tarafından sağlanan Slack eKeşif veri bağlayıcısı, kuruluşunuzun Slack çalışma alanlarından Microsoft 365 anlık ileti verilerini (iletiler, ekler, bağlantılar ve düzeltmeler gibi) içeri aktarmanıza ve arşivlenize yardımcı olur. Veri bağlayıcısı Slack API'sinden verileri çeker, e-posta iletisi biçimine dönüştürür ve ardından bu öğeleri Microsoft 365'deki kullanıcı posta kutularına aktarır. Slack verileri içeri aktarıldıktan sonra, Slack içeriğine Dava tutma, Advanced eDiscovery, İletişim uyumluluğu ve bekletme ayarları gibi uyumluluk çözümleri uygulayabilirsiniz. Microsoft 365'de verileri içeri aktarmak ve arşivlemek için Slack eKeşif veri bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-slack-ediscovery-data"></a>Slack eKeşif verilerini arşivleme işlemine genel bakış

Aşağıdaki genel bakış, Slack verilerini Microsoft 365'da arşivlerken Microsoft veri bağlayıcısı kullanma işlemini açıklar.

![Slack eBulma arşivleme iş akışı.](../media/SlackMSFTConnectorWorkflow.png)

1. Kuruluşunuz Slack çalışma alanını ayarlamak ve yapılandırmak için Slack ile birlikte çalışır.

2. Veri bağlayıcısı ayarlandıktan sonra, kuruluşunuzun Slack çalışma alanlarından gelen iletiler Microsoft 365'daki kullanıcı posta kutularına kopyalanır. Veri bağlayıcısı ayrıca bir sohbet iletisinin içeriğini e-posta iletisi biçimine dönüştürür.

3. Bağlayıcı, dönüştürülen sohbet iletilerini belirli kullanıcıların posta kutularına aktarır. Kullanıcı posta kutularında Gelen Kutusu klasöründe **Slack eKeşif** adlı bir alt klasör oluşturulur ve sohbet iletisi öğeleri bu klasöre aktarılır.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Kuruluşunuzun Slack için Enterprise Grid aboneliğine ihtiyacı vardır. Daha fazla bilgi için bkz [. Slack abonelikleri ve özellikleri](https://slack.com/intl/en-gb/help/articles/115003205446-Slack-subscriptions-and-features-).

- Veri bağlayıcısını oluşturan kullanıcıya Slack kuruluşunda **Kuruluş sahipleri** uygulama rolü atanmalıdır. Daha fazla bilgi için bkz. [Slack'teki rol türleri](https://slack.com/intl/en-gb/help/articles/360018112273-Types-of-roles-in-Slack).

- Kuruluşunuzun Slack kurumsal hesabının kullanıcı adını ve parolasını alın. Veri bağlayıcısını oluştururken bu hesapta oturum açmak için bu kimlik bilgilerini kullanırsınız. Slack kuruluşunuzda otomatik kullanıcı sağlama özelliğinin çoklu oturum açma (SSO) kullanacak şekilde yapılandırılmış olması da önerilir. [Güvenlik & Uyumluluk Merkezi'ndeki roller](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Slack eKeşif bağlayıcısını oluşturan kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, Microsoft 365 uyumluluk merkezi **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için, [Microsoft 365 uyumluluk merkezi İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

## <a name="step-1-create-a-slack-ediscovery-connector"></a>1. Adım: Slack eKeşif bağlayıcısı oluşturma

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com> gidin ve tıklayın.

2. **Genel Bakış** sekmesinde **Filtre'ye** tıklayın ve **Microsoft'a Göre'yi** seçin ve ardından filtreyi uygulayın.

3. **Slack eKeşif (önizleme) seçeneğine** tıklayın.

4. **Slack eKeşif (önizleme)** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın.

5. **Hizmet koşulları** sihirbazı sayfasında **Kabul Et'e** tıklayın.

6. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve **İleri'ye** tıklayın. Girdiğiniz ad, bağlayıcıyı oluşturduktan sonra **Veri bağlayıcıları** sayfasında tanımlar.

## <a name="step-2-sign-into-your-slack-organization"></a>2. Adım: Slack kuruluşunuzda oturum açın

1. **Kuruluşunuzun Slack** çalışma alanında oturum açmak için **Slack'te oturum açma sihirbazı sayfasında Slack'te oturum aç'a** tıklayın.

2. Slack **Çalışma alanınızda oturum açın** sayfasında, verileri arşivlemesini istediğiniz çalışma alanının adını yazın ve **Devam'a** tıklayın.

   Slack çalışma alanınızın adını ve oturum açma istemini içeren bir sayfa görüntülenir.

3. **Kuruluş Sahipleri de burada oturum açabilir** dizesindeki bağlantıya tıklayın.

4. Çalışma alanı oturum açma sayfasında, kuruluşunuzun Slack kurumsal hesabının e-posta adresini ve parolasını girin ve oturum **aç'a** tıklayın.

   Başarıyla oturum açtığınızda, bağlayıcı uygulaması tarafından Slack kuruluşunuza erişim izni isteyen bir sayfa görüntülenir.

5. Uygulamanın kuruluşunuzu yönetmesine izin vermek için **İzin Ver'e** tıklayın.

   **İzin Ver'e** tıkladıktan sonra Slack sayfası kapatılır ve Bağlayıcı sihirbazında **Slack eKeşif kullanıcılarını Microsoft 365 kullanıcılarla eşle** sayfası görüntülenir.

## <a name="step-3-specify-the-users-to-import-data-for"></a>3. Adım: Verileri içeri aktaracak kullanıcıları belirtin

Slack eBulma verilerini içeri aktarmak istediğiniz kullanıcıları belirtmek için aşağıdaki seçeneklerden birini belirleyin.

- **Kuruluşunuzdaki tüm kullanıcılar**. Tüm kullanıcılar için verileri içeri aktarmak için bu seçeneği belirleyin.

- **Yalnızca Dava tutan kullanıcılar**. Yalnızca posta kutuları Dava tutmada yer alan kullanıcılar için verileri içeri aktarmak için bu seçeneği belirleyin. Bu seçenek, LitigationHoldEnabled özelliği True olarak ayarlanmış kullanıcı posta kutularına veri aktarır. Daha fazla bilgi için bkz. [Dava tutma oluşturma](create-a-litigation-hold.md).

## <a name="step-4-map-users-and-select-data-types-to-import"></a>4. Adım: Kullanıcıları eşleme ve içeri aktaracak veri türlerini seçme

1. Slack kullanıcılarını Microsoft 365 posta kutularına eşlemek için aşağıdaki seçeneklerden birini veya her ikisini yapılandırın.

   - **Otomatik kullanıcı eşlemesi**. Slack kullanıcı adlarını Microsoft 365 posta kutularına otomatik olarak eşlemek için bu seçeneği belirleyin. Bağlayıcı, her Slack iletisinin veya öğesinin içerdiği *Email* özelliğinin değerini kullanarak yapar. Bu özellik, iletinin her katılımcısının e-posta adresiyle doldurulur. Bağlayıcı e-posta adreslerini ilgili Microsoft 365 kullanıcılarla ilişkilendirebiliyorsa, öğe bu kullanıcıların Microsoft 365 posta kutusuna aktarılır. Bu seçeneği kullanmak için Slack kuruluşunuz için SSO'nun yapılandırılmış olması gerekir.

   - **Özel kullanıcı eşlemesi**. Ayrıca, otomatik kullanıcı eşlemesi yerine (veya buna ek olarak) özel kullanıcı eşlemesi kullanma seçeneğiniz de vardır. Bu seçenekle, kullanıcıların Slack üye kimliğini Microsoft 365 e-posta adreslerine eşleyen bir CSV dosyası oluşturup karşıya yüklemeniz gerekir. Bunu yapmak için **CSV eşleme şablonunu indir'e** tıklayın, CSV dosyasını Slack üye kimliğiyle doldurun ve kuruluşunuzdaki tüm kullanıcılar için e-posta adresini Microsoft 365, ardından CSV dosyasını seçip sihirbaza yükleyin. CSV dosyasındaki sütun başlıklarını değiştirmediğinizden emin olun. AŞAĞıDA CSV eşleme dosyasının bir örneği verilmişti:

     |**ExternalUserId**  | **O365UserMailbox**   |
     |:-------------------|:-----------------------|
     | U01MDTF0QV6        | alexjones@contoso.onmicrosoft.com |
     | U02MDTF1RW7| pilarp@contoso.onmicrosoft.com|
     | U03MDTF2SX8 | sarad@contoso.onmicrosoft.com|
     |||

   > [!TIP]
   > Kullanıcılar için üye kimlikleri,... Kullanıcının profilindeki Diğer düğmesi ve ardından **Üye kimliğini kopyala'yı** seçin. Alternatif olarak, Slack ekibinin tüm üyelerine ait kimlikleri almak için Slack [users.list API yöntemini](https://api.slack.com/methods/users.list) kullanabilirsiniz.

   Otomatik kullanıcı eşlemesini etkinleştirir ve özel bir eşleme dosyası sağlarsanız bağlayıcı, Slack kullanıcısını bir Microsoft 365 posta kutusuna eşlemek için önce özel eşleme dosyasına bakar. Bağlayıcı Slack kullanıcısına karşılık gelen geçerli bir Microsoft 365 kullanıcısı bulamazsa, bağlayıcı Slack öğesinin *Email* özelliğini kullanır. Bağlayıcı, özel eşleme dosyasında veya ileti öğesinin *Email* özelliğinde geçerli bir Microsoft 365 kullanıcısı bulamazsa, öğe içeri aktarılamaz.

2. **İçeri aktaracak veri türlerini seçin** sihirbazı sayfasında, içeri aktarmak istediğiniz Slack veri türlerini seçin. Tüm kanallardan iletileri içeri aktarmak istiyorsanız tüm seçenekleri belirleyin. Aksi takdirde, yalnızca içeri aktarmak istediğiniz veri türlerini seçin.

     Slack iletilerine ek olarak, Microsoft 365 içeri aktarılacak diğer Slack içeriği türlerini de belirtebilirsiniz. 

3. İçeri aktaracak veri türlerini yapılandırdıktan sonra **İleri'ye** tıklayın, bağlayıcı ayarlarını gözden geçirin ve **son'a** tıklayarak bağlayıcıyı oluşturun.

## <a name="step-5-monitor-the-slack-ediscovery-connector"></a>5. Adım: Slack eKeşif bağlayıcısını izleme

Slack eKeşif bağlayıcısını oluşturduktan sonra bağlayıcının durumunu Microsoft 365 uyumluluk merkezi görüntüleyebilirsiniz.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** [https://compliance.microsoft.com](https://compliance.microsoft.com/) gidin ve tıklayın.

2. **Bağlayıcılar** sekmesine tıklayın ve ardından **Slack eKeşif** bağlayıcısını seçerek bağlayıcının özelliklerini ve bilgilerini içeren açılır sayfayı görüntüleyin.

3. Bağlayıcının durum günlüğünü açmak (veya kaydetmek) için **Kaynakla bağlayıcı durumu** altında **Günlüğü indir** bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda 10 MB'tan büyük eklerin veya öğelerin içeri aktarılmasını desteklemiyoruz. Daha büyük öğeler için destek daha sonraki bir tarihte sağlanacaktır.
