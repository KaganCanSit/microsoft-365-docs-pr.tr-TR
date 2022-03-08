---
title: Microsoft 365'te Çekirdek eKbulma servis Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MOE150
- MET150
description: Bu makalede, Core eKovery'i kullanmaya nasıl Microsoft 365. eBulma izinlerini atadığınız ve vakayı oluşturduktan sonra, üyeleri ekleyebilir, eBulma dırları oluşturabilir ve sonra araştırmanıza uygun içeriği arayabilir ve dışarı aktarabilirsiniz.
ms.openlocfilehash: ff2baf1e4844532ba53f3aa32ae02b7a7c49f00e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63320529"
---
# <a name="get-started-with-core-ediscovery-in-microsoft-365"></a>Microsoft 365'de Core eKover'ı Microsoft 365

Microsoft 365'daki çekirdek eBulma, kuruluşların içerik aramak ve dışarı aktararak içerikte arama yapmak ve dışarı aktarması için kullanabileceği temel bir eBulma aracı Microsoft 365 Office 365. Ayrıca, Core eKovery'i Exchange posta kutuları, SharePoint siteleri, OneDrive hesapları ve diğer içerik konumlarını içerik konumlarını Microsoft Teams. Core eKover'ı dağıtmak için hiçbir şey gerekli değildir, ancak bir IT yöneticisinin ve eBulma yöneticisinin, kurum içeriği aramak, dışarı aktarmak ve korumak için Core eKbulma'yi kullanmaya başlay önce tamamlaması gereken bazı önkoşul görevleri vardır.

Bu makalede, Core eKover'ı ayarlamak için gereken adımlar açıklanmıştır. Bu, Çekirdek eBulma'ya erişmek ve içerik konumlarında eBulma için uygun lisanslamanın gerekli olmasını sağlamanın yanı sıra, davalara erişmesi ve yönetmesi için IT, yasal ve soruşturma ekibimize izinler atamayı da içerir. Bu makalede ayrıca, içeriği aramak ve dışarı aktararak vakaları kullanmaya ilişkin üst düzey bir genel bakış da ve bilgi bulabilirsiniz.

## <a name="step-1-verify-and-assign-appropriate-licenses"></a>1. Adım: Uygun lisansları doğrulama ve atama

Core eDiscovery için Lisanslama için uygun kuruluş aboneliği ve kullanıcı başına lisanslama gerekir.

- **Kuruluş aboneliği:** Microsoft 365 uyumluluk merkezi'de Çekirdek eBulma'ya erişmek ve tutma ve dışarı aktarma özelliklerini kullanmak için, kuruluşta Microsoft 365 E3 veya Office 365 E3 üst bir aboneliği olması gerekir. Microsoft 365 Frontline kuruluşlarının F5 aboneliği olması gerekir.

- **Kullanıcı başına lisanslama:** Posta kutularına ve sitelere eBulma'ya yerinde yerinde kullanım için, kullanıcıların kuruluş aboneliğinize bağlı olarak aşağıdaki lisanslardan biri atanmaları gerekir:

  - Lisans Microsoft 365 E3 veya Office 365 E3 lisansı veya üstleri

   VEYA

  - Office 365 E1 Plan 2 veya Exchange Online eklenti lisansı Exchange Online Arşivleme lisansınız var

   VEYA

  - Microsoft 365 F5 Uyumluluğu veya F5 Güvenlik & Uyumluluk eklenti lisansı  

  VE

  - Office 365 E1 Online Plan 2 veya SharePoint Plan 2 eklenti lisansına OneDrive İş lisansınız var
  
  Lisans atama hakkında bilgi için bkz. [Kullanıcılara lisans atama](../admin/manage/assign-licenses-to-users.md).

Güvenlik ve uyumluluk hakkında bilgi ve rehberlik için:

- Karşılaştırma tablosunda eBulma ve denetim Microsoft 365 [indirin ve bakın](https://aka.ms/M365EnterprisePlans).

- Güvenlik [Microsoft 365 uyumluluğu için en iyi & - Hizmet Açıklamaları ve | Microsoft Docs](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).

## <a name="step-2-assign-ediscovery-permissions"></a>2. Adım: eBulma izinleri atama

Çekirdek eBulma'ya erişmek veya Core eKover'a üye olarak eklen erişmek için, kullanıcıya uygun izinler atanabilir. Özel olarak, ilgili grupta bir kullanıcının eBulma Yöneticisi rol grubuna üye olarak Microsoft 365 uyumluluk merkezi. Bu rol grubunun üyeleri Çekirdek eKbulma serviseleri oluşturabilir ve yönetebilir. Bu kullanıcılar üye ekleyemez ve kaldırabilir, kullanıcılara eBulma yerlerinden arama oluşturabilir ve düzenleyebilir ve Core eKovery durumundan içerik dışarı aktarabilirsiniz.

eBulma Yöneticisi rol grubuna kullanıcı eklemek için aşağıdaki adımları tamamlayın:

1. Etki Microsoft 365 uyumluluk merkezi gidin ve Microsoft 365 veya Office 365 yönetici hesabının kimlik bilgilerini kullanarak oturum açın.

2. İzinler <a href="https://go.microsoft.com/fwlink/p/?linkid=2173597" target="_blank">**sayfasında**</a> eBulma **Yöneticisi rol grubunu** seçin.

3. eBulma Yöneticisi uç sayfasında, eBulma **Yöneticisi bölümünün** yanında **Düzenle'ye** tıklayın.

4. Rol grubunu **düzenleme sihirbazının eBulma Yöneticisi** Seç sayfasında, Bulma **Yöneticisi'ni seçin öğesini tıklatın**.

5. **Ekle'ye** tıklayın ve rol grubuna eklemek istediğiniz tüm kullanıcıların onay kutusunu seçin.

6. Seçili **kullanıcıları eklemek** için Ekle'ye tıklayın ve sonra da Bitti'ye **tıklayın**.

7. Kullanıcıları **rol** grubuna eklemek için Kaydet'e tıklayın ve ardından adımı tamamlamak **için Kapat'a** tıklayın.

### <a name="more-information-about-the-ediscovery-manager-role-group"></a>eBulma Yöneticisi rol grubu hakkında daha fazla bilgi

eBulma Yöneticisi rol grubunda iki alt grup vardır. Bu alt gruplar arasındaki fark, kapsamı temel almaktadır.

- **eBulma Yöneticisi**: Kendi oluşturdukları veya üyesi olduğu Çekirdek eKbulma servis durumlarını görüntülemek ve yönetmek için. Başka bir eBulma Yöneticisi bir vaka oluşturur, ancak bu vakanın üyesi olarak ikinci bir eBulma Yöneticisi ekleyeni ise, ikinci eBulma Yöneticisi, uyumluluk merkezinde Core eKovery sayfasında vakayı görüntüde veya açılamaz. Genel olarak, organizasyonlu çoğu kişi eBulma Yöneticisi alt grubunu eklenebilir.

- **eBulma Yöneticisi**: Bir eBulma Yöneticisi'nin gerçekleştirebilir tüm olay yönetimi görevlerini gerçekleştirebilir. Buna ek olarak, eBulma Yöneticisi şunları da olabilir:

  - Core eDiscovery sayfasında listelenen tüm vakaları görüntüleme.
  
  - Kendilerini davanın üyesi olarak ekledikten sonra kuruluşta herhangi bir vakayı yönetin.

  - Kuruluşta herhangi bir vaka için vaka verilerine erişin ve verileri dışarı aktarın.
  
  - eBulma durumundan üyeleri kaldırma. Yalnızca eBulma Yöneticisi vakadan üyeleri kaldırabilir. eBulma Yöneticisi alt grubu üyesi olan kullanıcılar, durumu kullanıcı oluşturduğunda bile vakadan üye kaldıramıyor.

  Geniş erişim kapsamı nedeniyle, kuruluşun yalnızca birkaç yöneticisi eBulma Yöneticileri alt grubunun üyesi olması gerekir.

eBulma izinleri hakkında daha fazla bilgi ve eBulma Yöneticisi rol grubuna atanan her rolün açıklaması için bkz. [eBulma izinleri atama](assign-ediscovery-permissions.md).

## <a name="step-3-create-a-core-ediscovery-case"></a>3. Adım: Çekirdek eKbulma durumu oluşturma

Sıradaki adım bir olay oluşturmak ve Core eKovery'i kullanmaya başlamaktır. Vaka oluşturmak ve üye eklemek için aşağıdaki adımları tamamlayın. Vakayı oluşturan kullanıcı otomatik olarak üye olarak eklenir.

1. Başka <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">bir Microsoft 365 uyumluluk merkezi</a> gidin ve uygun eBulma izinleri atanmış olan bir kullanıcı hesabının kimlik bilgilerini kullanarak oturum açın. Kuruluş Yönetimi rol grubunun üyeleri, Çekirdek eKbulma örnekleri de oluşturabilir.

2. Gezinti bölmesinin sol bölmesinde, **Microsoft 365 uyumluluk merkezi'e tıklayın** ve sonra **da eBulma Puanı'ne** >  <a href="https://go.microsoft.com/fwlink/p/?linkid=2174007" target="_blank">**tıklayın**</a>.

3. Çekirdek **eBulma sayfasında Olay** **oluştur'a tıklayın**.

4. Yeni **büyük/küçük harf** çıkış sayfasında, büyük/küçük harfe bir ad (gerekli) ekleyin ve sonra isteğe bağlı bir açıklama yazın. Olay adı, kurum içinde benzersiz olmalıdır.

5. **Vakayı oluşturmak** için Kaydet'e tıklayın.

   Yeni vaka oluşturulur ve Core eKovery sayfasında görüntülenir. Yeni vakayı görüntülemek **için Yenile'ye** tıklamanız gerekir.

## <a name="step-4-optional-add-members-to-a-core-ediscovery-case"></a>4. Adım (isteğe bağlı): Çekirdek eKbulma durumuna üye ekleme

3. Adımda bir olay oluşturmanız ve bu vakayı tek kullanan kişi siz olursanız, bu adımı gerçekleştirmeniz zorunda değildir. eBulma ayrımları oluşturmak, içerik aramak ve arama sonuçlarını dışarı aktarmak için vakayı kullanmaya başlayabilirsiniz. Diğer kullanıcılara (veya roller grubuna) bu vakaya erişim vermek için bu adımı gerçekleştirin.

1. Çalışma **sayfasının Çekirdek eBulma** Microsoft 365 uyumluluk merkezi üye eklemek istediğiniz vakanın adına tıklayın.

2. Olay giriş sayfasında Seçenekler sekmesini **Ayarlar Access** izinlerini değiştir'**& seçin**.

3. Access Veri **Sayfası &,** Üyeler altında, vakaya üye **eklemek için** Ekle'ye tıklayın.

    Ayrıca, rol gruplarını bir vakanın üyeleri olarak da  eklemeyi seçebilirsiniz. Rol **grupları'nın altında** **Ekle'ye tıklayın**. Yalnızca bir vakaya üyesi olduğunuz rol gruplarını at at at başlatıldı. Bunun nedeni, rol gruplarının eBulma vakalarına kimlerin üye ataytaya bir denetiminde yer atay diğer bir nedenidir.

4. Vakanın üyesi olarak eklenilen kişiler veya rol grupları listesinde, eklemek istediğiniz kişilerin (veya rol gruplarının) adının sollarına tıklayın. Üye olarak eklen isteyen çok sayıda kişi veya rol grubunuz varsa, listede belirli bir kişiyi veya rol  grubunu aramak için Ara kutusunu kullanın.
  
5. Vakanın üyesi olarak eklemek istediğiniz kişi veya rol gruplarını seçin ve ardından Kaydet'e tıklarken yeni üyeleri veya rol gruplarını kaydedin.

> [!IMPORTANT]
>
>- Bir rol, davanın üyesi olarak ekleyseniz veya bu gruptan çıkarılırsa, rol grubu otomatik olarak davanın üyesi olarak kaldırılır (veya rol grubunun üyesi olduğu herhangi bir durum). Bunun nedeni, kurumlarınızı bir davanın üyelerine yanlışlıkla ek izinler sağlamaktan korumaktır. Benzer şekilde, bir rol grubu silinirse, üyesi olduğu tüm durumlarda gruptan kaldırılır. Daha fazla bilgi için bkz [. eBulma izinleri atama](assign-ediscovery-permissions.md#adding-role-groups-as-members-of-ediscovery-cases). 
>
>- Daha önce de belirtildiği gibi, yalnızca eBulma Yöneticisi bir vakadan üye kaldırabilir. eBulma Yöneticisi alt grubu üyesi olan kullanıcılar, durumu kullanıcı oluşturduğunda bile vakadan üye kaldıramıyor.
>

## <a name="explore-the-core-ediscovery-workflow"></a>Çekirdek eBulma iş akışını keşfetme

Temel eBulma'ya başlamanız için, ilgi alanlarına sahip kişiler için eBulma oluşturma, araştırmanız ile ilgili içeriği arama ve sonra bu verileri daha fazla gözden geçirmek için dışarı aktarmaya yönelik basit bir iş akışı vardır. Bu adımların her biri, keşfedebilirsiniz bazı genişletilmiş Core eKover işlevselliğini de vurgulaacağız.

![Temel eBulma iş akışı.](../media/CoreEdiscoveryWorkflow.png)

1. **[eBulma ayrımı oluşturma](create-ediscovery-holds.md)**. Olay oluşturduklardan sonra ilk adım, araştırmanıza ilginizi olan kişilerin içerik konumlarını yerinde tutmaktır ( *eBulma* amaçlı tutma olarak da adlandırılan bu konumlar). İçerik konumları posta Exchange, SharePoint siteleri, OneDrive hesaplarını, ayrıca Microsoft Teams ve Microsoft 365 gruplarıyla ilişkilendirilmiş posta kutularını ve siteleri içerir. Bu adım isteğe bağlıyken, eBulma tutma durumu inceleme sırasında olayla ilgili olabilir içeriği korur. eBulma ayrımı  oluştururken, belirli içerik konumlarında yer alan tüm içeriği koruyabilirsiniz veya yalnızca bir tutma sorgusuyla eşleşen içeriği korumak için sorgu tabanlı bir tutma oluşturabilirsiniz. İçeriği tutmanın yanı sıra, eBulma 1. oluşturmanın bir diğer iyi nedeni de, sonraki adımda arama yapmak ve arama yapmak için her konumu seçmek yerine, ayrı ayrı içerik konumlarında arama yapmaktır. Araştırmanızı tamamlandıktan sonra, oluşturduğunuz her yerinde tutma işlemini serbest  tutarak serbest siniz.

2. **[İçerik arama](search-for-content-in-core-ediscovery.md)**. eBulma uzdikten sonra, yerleşik arama aracını kullanarak içeriğin tutarak aranma konumlarını arama. Olayla ilgili veriler için diğer içerik konumlarını da arayabilirsiniz. Vakayla ilişkili farklı aramalar oluşturabilir ve çalıştırabilirsiniz. Arama sonuçlarını, büyük olasılıkla [olayla ilgili olan](keyword-queries-and-search-conditions.md) verilerle birlikte geri dönen arama sorguları oluşturmak için anahtar sözcükler, özellikler ve koşullar kullanırsınız. Şunları da yapabilirsiniz:

   - Sonuçları daraltmak için bir arama sorgusunu daraltmanıza yardımcı olacak arama istatistiklerini görüntüleme.

   - İlgili verilerin bulunıp buluna olmadığını hızlıca doğrulamak için arama sonuçlarının önizlemesini görüntüde görebilirsiniz.

   - Bir sorguyu düzeltin ve arama yeniden çalıştırabilirsiniz.

3. **[Arama sonuçlarını dışarı aktarın ve indirin](export-content-in-core-ediscovery.md)**. Araştırmanız ile ilgili verileri aratır ve bu verileri bulan kişiler tarafından araştırma Office 365 gözden geçirikten sonra dışarı aktarabilirsiniz. Verileri dışarı aktarma, iki adımlı bir işlemdir. İlk adım, arama sonuçlarının tam olarak doğru şekilde dışarı Office 365. Bu işlem, aramanın sonuçlarını Microsoft tarafından sağlanan bir Azure Bulut Depolama Depolama musunuz? Sıradaki adım, içeriği yerel bir bilgisayara indirmek için eBulma Dışarı Aktarma aracını kullanmaktır. Dışarı aktarıldı veri dosyalarına ek olarak, dışarı aktarma paketi bir dışarı aktarma raporu, özet rapor ve bir hata raporu içerir.
