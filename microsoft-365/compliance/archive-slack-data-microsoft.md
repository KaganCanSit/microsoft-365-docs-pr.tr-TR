---
title: Microsoft tarafından sağlanan bir veri bağlayıcısı kullanarak Microsoft 365 Slack eKbul verilerini arşivleme
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
description: Microsoft tarafından sağlanan Slack eKbulma veri bağlayıcısı ayar kullanmayı ve anlık ileti verilerini içeri aktarmayı ve arşivlemeyi öğrenin.
ms.openlocfilehash: 71369f2330193120f252d108641e99434c9fba78
ms.sourcegitcommit: 27eb93a7d46bcbb9c948a50b0a8481ffd3832ca0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/28/2021
ms.locfileid: "63019148"
---
# <a name="set-up-a-connector-to-archive-slack-ediscovery-data-preview"></a>Slack eK bulma verilerini arşivlemek için bağlayıcı ayarlama (önizleme)

Microsoft tarafından sağlanan Slack eK bulma veri bağlayıcısı, anlık ileti verilerini (iletiler, ekler, bağlantılar ve düzeltmeler gibi) organizasyonlu Slack çalışma alanlarından içeri aktarmanıza ve bu çalışma alanlarından bu verileri Microsoft 365. Veri bağlayıcısı Slack API'sinde verileri alır, bunu e-posta iletisi biçimine dönüştürür ve sonra da bu öğeleri kendi Microsoft 365. Slack verileri aktarıldıktan sonra, Slack içeriğine Mahkeme tutma, uyumluluk Advanced eDiscovery, İletişim uyumluluğu ve bekletme ayarları gibi uyumluluk çözümleri uygulayabilirsiniz. Kendi uygulamanıza veri içeri aktarma ve arşivlemek için Slack eKbul veri bağlayıcısı Microsoft 365, kuruma devlet ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-slack-ediscovery-data"></a>Slack eKbulma verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Microsoft veri bağlayıcısı kullanarak Slack verilerini aynı dosyada arşivleme işlemi Microsoft 365.

![Slack eKbulma arşivleme iş akışı.](../media/SlackMSFTConnectorWorkflow.png)

1. Organizasyonunız Slack ile birlikte, bir Slack çalışma alanı ayarlamak ve yapılandırmak için çalışıyor.

2. Veri bağlayıcısı ayar başlatıldıktan sonra, kuruluşlarının Slack çalışma alanlarındaki iletiler Microsoft 365.'de kullanıcı posta kutularına kopyalanır. Veri bağlayıcısı sohbet mesajının içeriğini de e-posta iletisi biçimine dönüştürür.

3. Bağlayıcı, dönüştürülmüş sohbet iletilerini belirli kullanıcıların posta kutularına içeri aktarıyor. Kullanıcı posta kutularında **Slack eKbulma** adlı Gelen Kutusu klasöründe bir alt klasör oluşturulur ve sohbet iletisi öğeleri bu klasöre aktarılır.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

- Kuruluş, Slack için Enterprise Grid aboneliğine ihtiyacı var. Daha fazla bilgi için bkz. [Slack abonelikleri ve özellikleri](https://slack.com/intl/en-gb/help/articles/115003205446-Slack-subscriptions-and-features-).

- Veri bağlayıcısı oluşturan kullanıcıya Slack kuruluşunda **Kuruluş sahipleri** uygulama rolü atanmalıdır. Daha fazla bilgi için bkz [. Slack'te rol türleri](https://slack.com/intl/en-gb/help/articles/360018112273-Types-of-roles-in-Slack).

- Kuruluşun Slack kurumsal hesabının kullanıcı adını ve parolasını alın. Bu kimlik bilgilerini, veri bağlayıcısını  oluşturmada bu hesapta oturum açma için kullanırsınız. Ayrıca, Slack kuruluşunda çoklu oturum açma (SSO) kullanmak üzere yapılandırılan otomatik kullanıcı hazırlamayı yapılandırmanız da önerilir.

- Slack eKbulma bağlayıcısı oluşturan kullanıcının, aynı programda Posta Kutusu İçeri/Dışarı Aktarma rolüne atan Exchange Online. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Varsayılan olarak, bu rol ilgili gruptaki bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü, aynı kuruluşta Kuruluş Yönetimi rol grubuna Exchange Online. Veya bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve sonra da uygun kullanıcıları üye olarak  eklersiniz. Daha fazla bilgi için,"[Rol gruplarını](/Exchange/permissions-exo/role-groups#create-role-groups) farklı bir [](/Exchange/permissions-exo/role-groups#modify-role-groups) grupta yönetme" makalesinde Rol grupları oluşturma veya Rol gruplarını değiştirme Exchange Online.

## <a name="step-1-create-a-slack-ediscovery-connector"></a>1. Adım: Slack eK bulma bağlayıcısı oluşturma

1. Sol gezinti <https://compliance.microsoft.com> bölmesinde **Veri bağlayıcıları'nın** üzerine gidin ve bu bağlayıcılara tıklayın.

2. Genel Bakış **sekmesinde** Filtre'ye **tıklayın,** **Microsoft'a Göre'yi** seçin ve filtreyi uygula'yı seçin.

3. **Slack eKbulma (önizleme)'ye tıklayın**.

4. **Slack eKbulma (önizleme) ürün açıklaması** sayfasında Bağlayıcı **ekle'ye tıklayın**.

5. Hizmet koşulları **sihirbazı sayfasında Kabul** Et'e **tıklayın**.

6. Bağlayıcıyı tanımlayan benzersiz bir ad girin ve Ardından Sonraki'ye **tıklayın**. Siz girdikten sonra, bağlayıcıyı **Veri bağlayıcıları** sayfasında girersiniz.

## <a name="step-2-sign-into-your-slack-organization"></a>2. Adım: Slack kuruluşta oturum açma

1. Kuruluşun Slack **çalışma alanında oturum** açması için, **Slack'de** oturum açma sihirbazı sayfasında Slack'e tıklayın.

2. Slack Çalışma **alanınıza oturum açma** sayfasında, verileri arşivlemek istediğiniz çalışma alanının adını yazın ve Devam'a **tıklayın**.

   Slack çalışma alanı adı ve oturum açma istemiyle bir sayfa görüntülenir.

3. Kuruluş Sahipleri de burada oturum **aabiliyor dizesinde yer alan bağlantıya tıklayın**.

4. Çalışma alanı oturum açma sayfasında, kuruluşun Slack kurumsal hesabının e-posta adresini ve parolasını girin ve Oturum **aç'a tıklayın**.

   Başarıyla oturum açmanızı tamamlayan bir sayfa görüntülenir ve bağlayıcı uygulamasıyla Slack organizasyonunuza erişim izni isteği görüntülenir.

5. **Uygulamanın kuruluşu** yönetmesine izin vermek için İzin Ver'e tıklayın.

   İzin **Ver'e** tıklarsınız, Slack sayfası kapanır ve **Slack eKızı** kullanıcılarını bağlayıcı sihirbazında Microsoft 365 sayfasına eşle sayfası görüntülenir.

## <a name="step-3-map-users-and-select-data-types-to-import"></a>3. Adım: Kullanıcıları eşleme ve içeri aktarıla veri türlerini seçme

1. Slack kullanıcılarını kendi posta kutularına eşlemek için aşağıdaki seçeneklerden birini Microsoft 365 yapılandırabilirsiniz.

   - **Otomatik kullanıcı eşlemesi**. Slack kullanıcı adlarını otomatik olarak bu posta kutularına eşlemek Microsoft 365 seçin. Bağlayıcı, her Slack iletisi veya öğesinin *içerdiği E-posta* özelliğinin değerini kullanarak bunu yapar. Bu özellik, iletinin tüm katılımcılarının e-posta adresiyle doldurulur. Bağlayıcı e-posta adreslerini ilgili kullanıcılarla Microsoft 365, öğe bu kullanıcıların Microsoft 365 posta kutusuna aktarılır. Bu seçeneği kullanmak için, Slack organizasyonu için SSO'nun yapılandırılmış olması gerekir.

   - **Özel kullanıcı eşlemesi**. Ayrıca, otomatik kullanıcı eşlemesi yerine (veya buna ek olarak) özel kullanıcı eşlemesi kullanma seçeneğiniz de vardır. Bu seçenekle, kullanıcıların Slack üye kimliğini kendi kullanıcı e-posta adreslerine eşleyene bir CSV Microsoft 365 yükleyebilirsiniz. Bunu yapmak için **CSV** eşleme şablonunu indir'e tıklayın, CSV dosyasını Slack üye kimliğiyle ve Microsoft 365 tüm kullanıcılar için e-posta adresiyle yazın, ardından CSV dosyasını seçin ve sihirbaza yükleyin. CSV dosyasındaki sütun başlıklarını değiştirmeden emin olun. Csv eşleme dosyası örneği:

     |**ExternalUserId**  | **O365UserMailbox**   |
     |:-------------------|:-----------------------|
     | U01MDTF0QV6        | alexjones@contoso.onmicrosoft.com |
     | U02MDTF1RW7| pilarp@contoso.onmicrosoft.com|
     | U03MDTF2SX8 | sarad@contoso.onmicrosoft.com|
     |||

   > [!TIP]
   > Kullanıcılar için üye kimlikleri, şu bağlantıya tıklayarak elde edilir: ... Kullanıcının profilinde Diğer düğmesi ve ardından Üye kimliğini **kopyala'ya tıklayın**. Alternatif olarak, Slack ekibinin tüm üyeleri için kimlikleri almak üzere Slack [users.list API](https://api.slack.com/methods/users.list) yöntemini kullanabilirsiniz.

   Otomatik kullanıcı eşlemesini etkinleştirir ve özel eşleme dosyası sağlarsanız, bağlayıcı önce özel eşleme dosyasına bakarak Slack kullanıcısını kendi posta kutunuzla Microsoft 365 sağlar. Bağlayıcı, Slack kullanıcıya karşılık gelen Microsoft 365 geçerli bir kullanıcı bulamazsa, bağlayıcı, Slack öğesinin *E-posta* özelliğini kullanır. Bağlayıcı, kullanıcıya özel Microsoft 365 veya ileti öğesinin E-posta özelliğinde geçerli bir kullanıcı bulamazsa, öğe  aktarılmaz.

2. İçeri **aktar yer alan veri türlerini seçin** sihirbazı sayfasında, içeri aktarmak istediğiniz Slack veri türlerini seçin. Tüm kanallardan iletileri içeri aktarın, sonra da tüm seçenekleri belirleyin. Aksi takdirde, yalnızca içeri aktarma işlemi yapmak istediğiniz veri türlerini seçin.

     Slack iletilerine ek olarak, bu iletilerin içeri aktar yer alan diğer Slack içerik türlerini de Microsoft 365. 

3. Veri türlerini içeri aktar olacak şekilde yapılandırdikten sonra, **Sonraki'ne** tıklayın, bağlayıcı ayarlarını gözden geçirip **Bağlayıcıyı oluşturmak** için Son'a tıklayın.

## <a name="step-4-monitor-the-slack-ediscovery-connector"></a>4. Adım: Slack eKbulma bağlayıcılarını izleme

Slack eK bulma bağlayıcısı oluşturdukta, bağlayıcının durumunu çalışma Microsoft 365 uyumluluk merkezi.

1. Sol gezinti [https://compliance.microsoft.com](https://compliance.microsoft.com/) çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bağlayıcılar **sekmesine** tıklayın ve **ardından Slack eKızlı** bağlayıcıyı seçerek bağlayıcının özelliklerini ve bilgilerini içeren açılır sayfayı görüntüleyin.

3. **Bağlayıcının kaynak durumunun altında**, **Bağlayıcının durum günlüğünü** açmak (veya kaydetmek) için Günlüğü indir bağlantısına tıklayın. Bu günlük, Microsoft buluta aktarılan verileri içerir.

## <a name="known-issues"></a>Bilinen sorunlar

- Şu anda ekleri veya 10 MB'den büyük öğeleri içeri aktarmayı desteklemez. Daha büyük öğeler için destek daha sonraki bir tarihte kullanılabilir.
