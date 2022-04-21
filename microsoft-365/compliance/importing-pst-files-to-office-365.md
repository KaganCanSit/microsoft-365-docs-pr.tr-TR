---
title: Kuruluş PST dosyalarını içeri aktarma hakkında bilgi edinin
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.IngestionHelp
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid: MET150
ms.assetid: ba688e0a-0fcb-4bd7-8e57-2b669564ea84
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
description: E-posta verilerini (PST dosyaları) kullanıcı posta kutularına toplu olarak aktarmak için Microsoft Purview uyumluluk portalında İçeri Aktarma hizmetini kullanmayı öğrenin.
ms.openlocfilehash: a1720b51a57569d676aeac37933f1dce3075e7ed
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "65001026"
---
# <a name="learn-about-importing-your-organizations-pst-files"></a>Kuruluşunuzun PST dosyalarını içeri aktarma hakkında bilgi edinin

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

> [!NOTE]
> Bu makale yöneticilere yöneliktir. PST dosyalarını kendi posta kutunuza aktarmaya mı çalışıyorsunuz? Bkz[. Outlook .pst dosyasından e-postayı, kişileri ve takvimi içeri aktarma](https://go.microsoft.com/fwlink/p/?LinkID=785075).

PST dosyalarını kuruluşunuzdaki posta kutularına hızla toplu olarak aktarmak için <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft Purview uyumluluk portalındaki</a> İçeri Aktarma hizmetini Exchange Online. PST dosyalarını Microsoft 365 içeri aktarmanın iki yolu vardır:

- **Ağ karşıya yükleme** ![ Buluta yükleme.](../media/54ab16ee-3822-4551-abef-3d926f4e1c01.png) - PST dosyalarını ağ üzerinden Microsoft bulutunda geçici bir Azure Depolama konumuna Upload. Ardından pst verilerini kuruluşunuzdaki posta kutularına aktarmak için İçeri Aktarma Microsoft 365 hizmetini kullanırsınız.

- **Sürücü gönderimi** ![ Sabit disk.](../media/e72b76f3-1f73-4296-b749-c325d95d9ef6.png) - PST dosyalarını BitLocker ile şifrelenmiş bir sabit sürücüye kopyalayın ve ardından sürücüyü fiziksel olarak Microsoft'a sevk edin. Microsoft sabit sürücüyü aldığında, veri merkezi personeli verileri Microsoft bulutunda geçici bir Azure Depolama konumuna yükler. Ardından verileri kuruluşunuzdaki posta kutularına aktarmak için İçeri Aktarma Microsoft 365 hizmetini kullanırsınız.

## <a name="step-by-step-instructions"></a>Adım adım yönergeler

Kuruluşunuzun PST dosyalarını Microsoft 365 toplu olarak içeri aktarmaya yönelik ayrıntılı ve adım adım yönergeler için aşağıdaki konulardan birine bakın.

- [PST dosyalarını Microsoft 365 aktarmak için ağ karşıya yükleme özelliğini kullanma](use-network-upload-to-import-pst-files.md)

- [PST dosyalarını almak için sürücü gönderimini kullanma](use-drive-shipping-to-import-pst-files-to-office-365.md)

## <a name="how-importing-pst-files-works"></a>PST dosyalarını içeri aktarma nasıl çalışır?

Aşağıda, PST içeri aktarma işleminin tamamının çizimi ve açıklaması yer alır. Çizimde birincil iş akışı gösterilmekte ve ağ yükleme ve sürücü gönderim yöntemleri arasındaki farklar vurgulanmaktadır.

![PST içeri aktarma işleminin iş akışı.](../media/76997b69-67d7-433a-a0ca-9389f85a36a1.png)

1. **PST içeri aktarma araçlarını ve anahtarını özel Azure Depolama konumuna indirme** - İlk adım, PST dosyalarını karşıya yüklemek veya bir sabit sürücüye kopyalamak için kullanılan aracı ve erişim anahtarını indirmektir. Bunları uyumluluk portalındaki **İçeri Aktar** sayfasından alırsınız. Anahtar size (veya sürücü gönderimi durumunda Microsoft veri merkezi personeline) PST dosyalarını özel ve güvenli bir Azure Depolama konumuna yüklemek için gerekli izinleri sağlar. Bu erişim anahtarı kuruluşunuza özgüdür ve PST dosyalarınıza Microsoft buluta yüklendikten sonra yetkisiz erişimi önlemeye yardımcı olur. PST dosyalarını Microsoft 365'a aktarmak, kuruluşunuzun ayrı bir Azure aboneliğine sahip olmasını gerektirmez.

2. **PST dosyalarını Upload veya kopyalama** - Sonraki adım, PST dosyalarını içeri aktarmak için ağ yükleme veya sürücü gönderimi kullanıp kullanmadığınıza bağlıdır. Her iki durumda da, önceki adımda aldığınız aracı ve güvenli depolama anahtarını kullanacaksınız.

    - **Ağ karşıya yükleme:** AzCopy.exe aracı (1. adımda indirilir) PST dosyalarınızı Microsoft bulutunda bir Azure Depolama konumunda karşıya yüklemek ve depolamak için kullanılır. PST dosyalarınızı karşıya yüklediğiniz Azure Depolama konumu, kuruluşunuzla aynı bölgesel Microsoft veri merkezinde bulunur.

      Bunları karşıya yüklemek için içeri aktarmak istediğiniz PST dosyalarının kuruluşunuzdaki bir dosya paylaşımında veya dosya sunucusunda bulunması gerekir.

    - **Sürücü gönderimi:** pst dosyalarınızı sabit sürücüye kopyalamak için WAImportExport.exe aracı (1. adımda indirilir) kullanılır. Bu araç sabit sürücüyü BitLocker ile şifreler ve ardından PST'leri sabit sürücüye kopyalar. Ağ yüklemesi gibi, sabit sürücüye kopyalamak istediğiniz PST dosyalarının da kuruluşunuzdaki bir dosya paylaşımında veya dosya sunucusunda bulunması gerekir.

3. **PST içeri aktarma eşleme dosyası oluşturma** - PST dosyaları Azure Depolama konumuna yüklendikten veya sabit sürücüye kopyalandıktan sonra, sonraki adım PST dosyalarının hangi kullanıcı posta kutularına aktarılacağını belirten virgülle ayrılmış bir değer (CSV) dosyası oluşturmaktır (ve bir PST dosyası kullanıcının birincil posta kutusuna veya arşiv posta kutusuna aktarılabilir). [PST İçeri Aktarma eşleme dosyasının bir kopyasını indirin](https://go.microsoft.com/fwlink/p/?LinkId=544717). Microsoft 365 İçeri Aktarma hizmeti, PST dosyalarını içeri aktarmak için bu bilgileri kullanır.

4. **PST içeri aktarma işi oluşturma** - Sonraki adım, uyumluluk portalındaki **PST dosyalarını içeri aktar** sayfasında bir PST içeri aktarma işi oluşturmak ve önceki adımda oluşturulan PST içeri aktarma eşleme dosyasını göndermektir. Ağ yüklemesi için (PST dosyaları Azure'a yüklendiğinden) Microsoft 365 PST dosyalarındaki verileri analiz eder ve ardından pst içeri aktarma eşleme dosyasında belirtilen posta kutularına hangi verilerin gerçekten içeri aktarılacağını denetleyebilen filtreler ayarlama fırsatı verir.

    Sürücü gönderimi için sürecin bu noktasında birkaç şey daha gerçekleşir.

    - Sabit sürücüyü fiziksel olarak bir Microsoft veri merkezine gönderirsiniz (içeri aktarma işi oluşturulduğunda Microsoft veri merkezinin sevkiyat adresi görüntülenir).

    - Microsoft sabit sürücüyü aldığında, veri merkezi personeli PST dosyalarını sabit sürücüye kuruluşunuz için Azure Depolama konumuna yükler. Daha önce açıklandığı gibi PST dosyalarınız, kuruluşunuzun bulunduğu bölgesel Microsoft veri merkezinde bulunan bir Azure Depolama konumuna yüklenir.

      > [!NOTE]
      > Sabit sürücüdeki PST dosyaları, Microsoft sabit sürücüyü aldıktan sonraki 7-10 iş günü içinde Azure'a yüklenir.

      Ağ karşıya yükleme işlemi gibi, Microsoft 365 ardından PST dosyalarındaki verileri analiz eder ve pst içeri aktarma eşleme dosyasında belirtilen posta kutularına gerçekte hangi verilerin içeri aktarılacağını denetleyebilen filtreler ayarlama fırsatı verir.

    - Microsoft sabit sürücüyü size geri gönderir.

5. **Posta kutularına aktarılacak PST verilerini filtreleme** - İçeri aktarma işi oluşturulduktan sonra (ve bir sürücü gönderim işinden PST dosyaları Azure Depolama konumuna yüklendikten sonra) Microsoft 365 öğelerin yaşını ve PST dosyalarına dahil edilen farklı ileti türlerini belirleyerek PST dosyalarındaki verileri analiz eder (güvenli ve güvenli bir şekilde). Analiz tamamlandığında ve veriler içeri aktarmaya hazır olduğunda, PST dosyalarında yer alan tüm verileri içeri aktarma seçeneğiniz olur veya hangi verilerin içeri aktarılacağını denetleye filtreler ayarlayarak içeri aktarılan verileri kırpabilirsiniz.

6. **PST içeri aktarma işini başlatma** - İçeri aktarma işi başlatıldıktan sonra, Microsoft 365 PST dosyalarını Azure Depolama konumundan kullanıcı posta kutularına aktarmak için PST içeri aktarma eşleme dosyasındaki bilgileri kullanır. İçeri aktarma işiyle ilgili durum bilgileri (içeri aktarılan her PST dosyası hakkındaki bilgiler dahil) uyumluluk portalındaki **PST dosyalarını içeri aktar** sayfasında görüntülenir. İçeri aktarma işi tamamlandığında, işin durumu **Tamamlandı** olarak ayarlanır.

## <a name="why-import-email-data-to-microsoft-365"></a>E-posta verilerini neden Microsoft 365 içeri aktarasın?

- Kuruluşunuzun arşiv mesajlaşma verilerini Microsoft 365 aktarmak için iyi bir yoldur.

- Hedef posta kutularına aktarılan PST dosyalarındaki öğeleri filtrelemek için [Akıllı İçeri Aktarma](filter-data-when-importing-pst-files.md) özelliğini kullanabilirsiniz. Bu, hangi verilerin içeri aktarılacağını denetleye filtreler ayarlayarak içeri aktarılan verileri kırpmanıza olanak tanır.

- E-posta verilerini Microsoft 365 içeri aktarmak, kuruluşunuzun uyumluluk gereksinimlerini karşılamanıza yardımcı olarak şunları sağlar:

  - Kullanıcılara ek posta kutusu depolama alanı sağlamak için [arşiv posta kutularını](enable-archive-mailboxes.md) ve [arşivlemeyi otomatik olarak genişletmeyi](autoexpanding-archiving.md) etkinleştirin.

  - İçeriği korumak için posta kutularını [Dava Tutma'ya](./create-a-litigation-hold.md) yerleştirin.

  - Posta kutusu içeriğini aramak için [İçerik Arama aracını](content-search.md) kullanın.

  - Kuruluşunuzun yasal araştırmalarını yönetmek için [eBulma servis taleplerini](./get-started-core-ediscovery.md) kullanma

  - Posta kutusu içeriğinin ne kadar süreyle tutulacaklarını denetlemek için uyumluluk portalında bekletme [ilkelerini](retention.md) kullanın ve bekletme süresi dolduktan sonra içeriği silin.

  - İletilerin ileti standartlarıyla uyumlu olduğundan emin olmak ve bir sınıflandırma türü eklemek üzere iletileri incelemek için [İletişim uyumluluk ilkelerini](communication-compliance.md) kullanın.

- verileri Microsoft 365'a aktarmak, veri kaybına karşı korunmaya yardımcı olur. Microsoft 365'a aktarılan e-posta verileri, Exchange Online yüksek kullanılabilirlik özelliklerini devralır.

- E-posta verileri bulutta depolandığından tüm cihazlardan kullanıcılar tarafından kullanılabilir.

## <a name="importing-sharepoint-data-to-microsoft-365"></a>SharePoint verileri Microsoft 365'a aktarma

Ayrıca, dosyaları ve belgeleri kuruluşunuzdaki SharePoint sitelere ve OneDrive hesaplarına da aktarabilirsiniz. Daha fazla bilgi için aşağıdaki makalelere bakın:

- [SharePoint Online'a geçiş](/sharepointmigration/migrate-to-sharepoint-online)

- [SharePoint Geçiş Aracı'na giriş](/sharepointmigration/introducing-the-sharepoint-migration-tool)

- [PowerShell kullanarak SharePoint Online'a geçiş](/sharepointmigration/overview-spmt-ps-cmdlets)

- [Azure Data Box kullanarak dosya paylaşımı içeriğinizi SharePoint Online'a geçirme](/sharepointmigration/how-to-migrate-file-share-content-to-spo-using-azuredatabox)

## <a name="frequently-asked-questions-about-importing-pst-files"></a>PST dosyalarını içeri aktarma hakkında sık sorulan sorular

Pst dosyalarını Microsoft 365 posta kutularına toplu olarak aktarmak için Microsoft 365 İçeri Aktarma hizmetini kullanma hakkında sık sorulan bazı sorular aşağıdadır.

- [PST dosyalarını içeri aktarmak için ağ karşıya yükleme kullanma](#using-network-upload-to-import-pst-files)

- [PST dosyalarını içeri aktarmak için sürücü gönderimi kullanma](#using-drive-shipping-to-import-pst-files)

### <a name="using-network-upload-to-import-pst-files"></a>PST dosyalarını içeri aktarmak için ağ karşıya yükleme kullanma

#### <a name="what-permissions-are-required-to-create-import-jobs-in-the-microsoft-365-import-service-using-network-upload"></a>Microsoft 365 İçeri Aktarma Hizmeti'nde ağ karşıya yüklemesini kullanarak içeri aktarma işleri oluşturmak için hangi izinler gereklidir?

PST dosyalarını Microsoft 365 posta kutularına aktarmak için Exchange Online'da Posta Kutusu İçeri Aktarma Dışarı Aktarma rolüne atanmış olmanız gerekir. Varsayılan olarak, bu rol Exchange Online'daki hiçbir rol grubuna atanmaz. Posta Kutusu İçeri Aktarma Dışarı Aktarma rolünü Kuruluş Yönetimi rol grubuna ekleyebilirsiniz. Ya da yeni bir rol grubu oluşturabilir, Posta Kutusu İçeri Aktarma Dışarı Aktarma rolünü atayabilir ve ardından kendinizi veya diğer kullanıcıları üye olarak ekleyebilirsiniz. Daha fazla bilgi için, Exchange Online rol gruplarını yönetme bölümündeki "Rol grubuna rol ekleme" veya "[Rol](/Exchange/permissions-exo/role-groups) grubu oluşturma" bölümlerine bakın.

Ayrıca, uyumluluk portalında içeri aktarma işleri oluşturmak için aşağıdakilerden biri doğru olmalıdır:

- Exchange Online'de Posta Alıcıları rolüne atanmış olmanız gerekir. Varsayılan olarak, bu rol Kuruluş Yönetimi ve Alıcı Yönetimi rol gruplarına atanır.

    Veya

- Kuruluşunuzda genel yönetici olmanız gerekir.

> [!TIP]
> Exchange Online'da PST dosyalarını Microsoft 365 içeri aktarmaya yönelik yeni bir rol grubu oluşturmayı göz önünde bulundurun. PST dosyalarını içeri aktarmak için gereken en düşük ayrıcalık düzeyi için, Posta Kutusu İçeri Aktarma Dışarı Aktarma ve Posta Alıcıları rollerini yeni rol grubuna atayın ve ardından üye ekleyin.

#### <a name="where-is-network-upload-available"></a>Ağ karşıya yükleme nerede kullanılabilir?

Ağ yükleme şu anda şu bölgelerde kullanılabilir: Birleşik Devletler, Kanada, Brezilya, Birleşik Krallık, Fransa, Almanya, İsviçre, Norveç, Avrupa, Hindistan, Doğu Asya, Güneydoğu Asya, Japonya, Kore Cumhuriyeti, Avustralya ve Birleşik Arap Emirlikleri (BAE). Ağ yüklemesi gelecekte daha fazla bölgede kullanılabilir olacak.

#### <a name="what-is-the-pricing-for-importing-pst-files-by-using-network-upload"></a>Ağ karşıya yüklemesini kullanarak PST dosyalarını içeri aktarmanın fiyatlandırması nedir?

PST dosyalarını içeri aktarmak için ağ yüklemesini kullanmak ücretsizdir.

Bu, PST dosyalarının Azure Depolama alanından silindikten sonra artık [Microsoft 365 yönetim merkezi](https://go.microsoft.com/fwlink/p/?linkid=2024339) tamamlanmış bir içeri aktarma işinin dosya listesinde görüntülenmediği anlamına gelir. verileri **Microsoft 365 içeri aktarma** sayfasında bir içeri aktarma işi listelenmeye devam ediyor olsa da, eski içeri aktarma işlerinin ayrıntılarını görüntülediğinizde PST dosyalarının listesi boş olabilir.

#### <a name="what-version-of-the-pst-file-format-is-supported-for-importing-to-microsoft-365"></a>pst dosya biçiminin Microsoft 365 içeri aktarma için hangi sürümü desteklenir?

PST dosya biçiminin iki sürümü vardır: ANSI ve Unicode. Unicode PST dosya biçimini kullanan dosyaları içeri aktarmanızı öneririz. Ancak, çift baytlık karakter kümesi (DBCS) kullanan diller gibi ANSI PST dosya biçimini kullanan dosyalar da Microsoft 365'a aktarılabilir. ANSI PST dosyalarını içeri aktarma hakkında daha fazla bilgi için bkz. [PST dosyalarını Microsoft 365 aktarmak için ağ yüklemesini kullanma](./use-network-upload-to-import-pst-files.md) konusundaki 4. Adım.

Ayrıca, Outlook 2007 ve sonraki sürümlerden PST dosyaları Microsoft 365 aktarılabilir.

#### <a name="after-i-upload-my-pst-files-to-the-azure-storage-area-how-long-are-they-kept-in-azure-before-theyre-deleted"></a>PST dosyalarımı Azure Depolama alanına yükledikten sonra silinmeden önce Azure'da ne kadar süreyle tutulurlar?

PST dosyalarını içeri aktarmak için ağ karşıya yükleme yöntemini kullandığınızda, bunları adlı `ingestiondata`bir Azure blob kapsayıcısına yüklersiniz. Uyumluluk portalındaki **PST dosyalarını içeri aktar** sayfasında devam eden içeri aktarma işi yoksa, uyumluluk portalında `ingestiondata` en son içeri aktarma işi oluşturulduktan 30 gün sonra Azure'daki kapsayıcıdaki tüm PST dosyaları silinir. Bu, PST dosyalarını Azure'a yükledikten sonra 30 gün içinde uyumluluk portalında yeni bir içeri aktarma işi oluşturmanız (ağ karşıya yükleme yönergelerinin 5. adımında açıklanmıştır) anlamına gelir.

Bu, PST dosyalarının Azure Depolama alanından silindikten sonra uyumluluk portalında tamamlanmış bir içeri aktarma işinin dosya listesinde görüntülenmediği anlamına da gelir. Uyumluluk portalındaki **PST dosyalarını içeri aktar** sayfasında bir içeri aktarma işi listelenmeye devam ediyor olsa da, eski içeri aktarma işlerinin ayrıntılarını görüntülediğinizde PST dosyalarının listesi boş olabilir.

#### <a name="how-long-does-it-take-to-import-a-pst-file-to-a-mailbox-using-network-upload"></a>Bir PST dosyasının ağ karşıya yüklemesini kullanarak posta kutusuna aktarılması ne kadar sürer?

Ağınızın kapasitesine bağlıdır, ancak her terabayt (TB) verinin kuruluşunuzun Azure Depolama alanına yüklenmesi genellikle birkaç saat sürer. PST dosyaları Azure Depolama alanına kopyalandıktan sonra, pst dosyası bir Microsoft 365 posta kutusuna günde<sup>\*</sup> yaklaşık 24 GB hızında içeri aktarılır. Bu oran gereksinimlerinizi karşılamıyorsa, e-posta verilerini Microsoft 365 almak için diğer yöntemleri göz önünde bulundurabilirsiniz. Daha fazla bilgi için bkz. [Birden çok e-posta hesabını Microsoft 365 geçirmenin yolları](/Exchange/mailbox-migration/mailbox-migration).

Farklı PST dosyaları farklı hedef posta kutularına aktarılırsa, içeri aktarma işlemi paralel olarak gerçekleşir; başka bir deyişle, her PST/posta kutusu çifti aynı anda içeri aktarılır. Aynı posta kutusuna birden çok PST dosyası içeri aktarılırsa, bunlar aynı anda değil sırayla (birer birer) içeri aktarılır.

> [!NOTE]
> <sup>\*</sup> Bu oran garanti değildir. Sunucu iş yükü ve geçici performans sorunları bu hızı düşürebilir.

#### <a name="how-does-the-pst-import-process-handle-duplicate-email-items"></a>PST içeri aktarma işlemi yinelenen e-posta öğelerini nasıl işler?

PST içeri aktarma işlemi yinelenen öğeleri denetler ve hedef posta kutusunda veya hedef arşivde hedef klasörde eşleşen bir öğe varsa öğeleri PST dosyasından posta kutusuna veya arşive kopyalamaz. Aynı PST dosyasını yeniden içeri aktarır ve önceki içeri aktarma işinde belirttiğinizden farklı bir hedef klasör (PST içeri aktarma eşleme dosyasında TargetRootFolder özelliğini kullanarak) belirtirseniz, PST dosyasındaki tüm öğeler yeniden içeri aktarılır.

#### <a name="is-there-a-message-size-limit-when-importing-pst-files-using-network-upload"></a>Ağ yüklemesini kullanarak PST dosyalarını içeri aktarırken ileti boyutu sınırı var mı?

Evet. PST dosyası 150 MB'tan büyük bir posta kutusu öğesi içeriyorsa, öğe atlanır ve içeri aktarma işlemi sırasında içeri aktarılmaz. 150 MB'tan büyük öğeler, Exchange Online ileti boyutu sınırı olduğundan içeri aktarılamaz. Daha fazla bilgi için bkz. [Exchange Online'de ileti sınırları](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#message-limits).

#### <a name="are-message-properties-such-as-when-the-message-was-sent-or-received-the-list-of-recipients-and-other-properties-preserved-when-pst-files-are-imported-to-a-microsoft-365-mailbox-using-network-upload"></a>İletinin ne zaman gönderildiği veya alındığı, alıcı listesi ve diğer özellikler gibi ileti özellikleri, PST dosyaları ağ yüklemesi kullanılarak bir Microsoft 365 posta kutusuna aktarıldığında korunuyor mu?

Evet. İçeri aktarma işlemi sırasında özgün ileti meta verileri değiştirilmez.

#### <a name="is-there-a-limit-to-the-number-of-levels-in-a-folder-hierarchy-for-a-pst-file-that-i-want-to-import-to-a-mailbox-using-network-upload"></a>Ağ karşıya yüklemesini kullanarak posta kutusuna aktarmak istediğim bir PST dosyası için klasör hiyerarşisindeki düzey sayısı sınırı var mı?

Evet. 300 veya daha fazla iç içe klasör düzeyine sahip bir PST dosyasını içeri aktaramazsınız.

#### <a name="can-i-use-network-upload-to-import-pst-files-to-an-inactive-mailbox-in-microsoft-365"></a>PST dosyalarını Microsoft 365'daki etkin olmayan bir posta kutusuna aktarmak için ağ yükleme özelliğini kullanabilir miyim?

Evet, bu özellik artık kullanılabilir.

#### <a name="can-i-use-network-upload-to-import-pst-files-to-an-online-archive-mailbox-in-an-exchange-hybrid-deployment"></a>PST dosyalarını Exchange karma dağıtımdaki bir çevrimiçi arşiv posta kutusuna aktarmak için ağ yükleme özelliğini kullanabilir miyim?

Evet, bu özellik artık kullanılabilir.

#### <a name="can-i-use-network-upload-to-import-pst-files-to-public-folders-in-exchange-online"></a>PST dosyalarını Exchange Online ortak klasörlere aktarmak için ağ yükleme özelliğini kullanabilir miyim?

Hayır, PST dosyalarını ortak klasörlere aktaramazsınız.

### <a name="using-drive-shipping-to-import-pst-files"></a>PST dosyalarını içeri aktarmak için sürücü gönderimi kullanma

#### <a name="what-permissions-are-required-to-create-import-jobs-in-the-microsoft-365-import-service-using-drive-shipping"></a>Sürücü gönderimini kullanarak Microsoft 365 İçeri Aktarma Hizmeti'nde içeri aktarma işleri oluşturmak için hangi izinler gereklidir?

PST dosyalarını Microsoft 365 posta kutularına aktarmak için Posta Kutusu İçeri Aktarma Dışarı Aktarma rolüne atanmış olmanız gerekir. Varsayılan olarak, bu rol Exchange Online'daki hiçbir rol grubuna atanmaz. Posta Kutusu İçeri Aktarma Dışarı Aktarma rolünü Kuruluş Yönetimi rol grubuna ekleyebilirsiniz. Ya da yeni bir rol grubu oluşturabilir, Posta Kutusu İçeri Aktarma Dışarı Aktarma rolünü atayabilir ve ardından kendinizi veya diğer kullanıcıları üye olarak ekleyebilirsiniz. Daha fazla bilgi için, Exchange Online rol gruplarını yönetme bölümündeki "Rol grubuna rol ekleme" veya "[Rol](/Exchange/permissions-exo/role-groups) grubu oluşturma" bölümlerine bakın.

Ayrıca, uyumluluk portalında içeri aktarma işleri oluşturmak için aşağıdakilerden biri doğru olmalıdır:

- Exchange Online'de Posta Alıcıları rolüne atanmış olmanız gerekir. Varsayılan olarak, bu rol Kuruluş Yönetimi ve Alıcı Yönetimi rol gruplarına atanır.

    Veya

- Kuruluşunuzda genel yönetici olmanız gerekir.

> [!TIP]
> Exchange Online'da PST dosyalarını Microsoft 365 içeri aktarmaya yönelik yeni bir rol grubu oluşturmayı göz önünde bulundurun. PST dosyalarını içeri aktarmak için gereken en düşük ayrıcalık düzeyi için, Posta Kutusu İçeri Aktarma Dışarı Aktarma ve Posta Alıcıları rollerini yeni rol grubuna atayın ve ardından üye ekleyin.

#### <a name="where-is-drive-shipping-available"></a>Sürücü gönderimi nerede kullanılabilir?

Drive shipping şu anda Birleşik Devletler, Kanada, Brezilya, Birleşik Krallık, Avrupa, Hindistan, Doğu Asya, Güneydoğu Asya, Japonya, Kore Cumhuriyeti ve Avustralya'da kullanılabilir. Sürücü gönderimi gelecekte daha fazla bölgede kullanılabilir olacak.

> [!NOTE]
> Şu anda, PST dosyalarını içeri aktarmak için sürücü gönderimi Almanya ve İsviçre'de kullanılamaz. Bu SSS, bu ülkelerde sürücü gönderimi kullanılabilir olduğunda güncelleştirilir.

#### <a name="what-commercial-licensing-agreements-support-drive-shipping"></a>Hangi ticari lisans sözleşmeleri sürücü gönderimini destekler?

PST dosyalarını Microsoft 365'a aktarmak için sürücü gönderimi bir Microsoft Kurumsal Anlaşma (EA) aracılığıyla kullanılabilir. Sürücü gönderimi, Microsoft Ürün ve Hizmet Sözleşmesi (MPSA) aracılığıyla kullanılamaz.

#### <a name="what-is-the-pricing-for-using-drive-shipping-to-import-pst-files-to-microsoft-365"></a>PST dosyalarını Microsoft 365 aktarmak için sürücü gönderimini kullanmanın fiyatlandırması nedir?

PST dosyalarını Microsoft 365 posta kutularına aktarmak için sürücü gönderimini kullanmanın maliyeti, GB veri başına 2 ABD Doları'dır. Örneğin, 1.000 GB (1 TB) PST dosyası içeren bir sabit sürücü gönderirseniz, maliyet 2.000 ABD dolarıdır. İthalat ücretini ödemek için bir iş ortağıyla çalışabilirsiniz. İş ortağı bulma hakkında bilgi için bkz. [Microsoft iş ortağınızı veya kurumsal bayinizi bulma](../admin/manage/find-your-partner-or-reseller.md).

#### <a name="what-kind-of-hard-drives-are-supported-for-drive-shipping"></a>Sürücü gönderimi için ne tür sabit sürücüler desteklenir?

yalnızca 2,5 inç katı hal sürücüleri (SSD) veya 2,5 inç veya 3,5 inç SATA II/III dahili sabit sürücüler, Microsoft 365 İçeri Aktarma hizmetiyle kullanılmak üzere desteklenir. 10 TB'a kadar sabit sürücüleri kullanabilirsiniz. İçeri aktarma işleri için yalnızca sabit sürücüdeki ilk veri birimi işlenir. Veri birimi NTFS ile biçimlendirilmelidir. Bir sabit sürücüye veri kopyalarken, doğrudan 2,5 inç SSD veya 2,5 inç veya 3,5 inç SATA II/III bağlayıcı kullanarak veya harici 2,5 inç SSD veya 2,5 inç veya 3,5 inç SATA II/III USB bağdaştırıcısı kullanarak harici olarak takabilirsiniz.

> [!IMPORTANT]
> Yerleşik USB bağdaştırıcısıyla birlikte gelen harici sabit sürücüler, Microsoft 365 İçeri Aktarma hizmeti tarafından desteklenmez. Ayrıca, harici bir sabit sürücünün kasası içindeki disk kullanılamaz. Lütfen harici sabit sürücüleri göndermeyin.

#### <a name="how-many-hard-drives-can-i-ship-for-a-single-import-job"></a>Tek bir içeri aktarma işi için kaç sabit sürücü gönderebilirim?

Tek bir içeri aktarma işi için en fazla 10 sabit sürücü gönderebilirsiniz.

#### <a name="after-i-ship-my-hard-drive-how-long-does-it-take-to-get-to-the-microsoft-datacenter"></a>Sabit sürücümü gönderdikten sonra Microsoft veri merkezine gitmek ne kadar sürer?

Bu, Microsoft veri merkezine yakınlığınız ve sabit sürücünüzü göndermek için kullandığınız sevkiyat seçeneği (sonraki gün teslimat, iki günlük teslimat veya yer teslimi gibi) gibi birkaç şeye bağlıdır. Çoğu nakliyecide, teslimatınızın durumunu izlemek için takip numarasını kullanabilirsiniz.

#### <a name="after-my-hard-drive-arrives-at-the-microsoft-datacenter-how-long-does-it-take-to-upload-my-pst-files-to-azure"></a>Sabit sürücüm Microsoft veri merkezine geldikten sonra PST dosyalarımı Azure'a yüklemek ne kadar sürer?

Sabit sürücünüz Microsoft veri merkezine alındıktan sonra PST dosyalarının kuruluşunuz için Azure Depolama konumuna yüklenmesi 7 ila 10 iş günü arasında sürer. PST dosyaları adlı `ingestiondata`bir Azure blob kapsayıcısına yüklenir.

#### <a name="how-long-does-it-take-to-import-a-pst-file-to-a-mailbox-using-drive-shipping"></a>Pst dosyasının sürücü gönderimi kullanılarak posta kutusuna aktarılması ne kadar sürer?

PST dosyaları Azure Depolama alanına yüklendikten sonra, Microsoft 365 öğelerin yaşını ve PST dosyalarına dahil edilen farklı ileti türlerini tanımlamak için PST dosyalarındaki verileri analiz eder (güvenli ve güvenli bir şekilde). Bu analiz tamamlandığında, PST dosyalarındaki tüm verileri içeri aktarma veya hangi verilerin içeri aktarılacağını denetleyebilen filtreler ayarlama seçeneğiniz olur. İçeri aktarma işini başlattıktan sonra, pst dosyası bir Microsoft 365 posta kutusuna günde yaklaşık 24 GB hızında içeri aktarılır.<sup>\*</sup> Bu oran gereksinimlerinizi karşılamıyorsa, e-posta verilerini Microsoft 365 almak için diğer yöntemleri göz önünde bulundurabilirsiniz. Daha fazla bilgi için bkz. [Birden çok e-posta hesabını Microsoft 365 geçirmenin yolları](/Exchange/mailbox-migration/mailbox-migration).

Farklı PST dosyaları farklı hedef posta kutularına aktarılırsa, içeri aktarma işlemi paralel olarak gerçekleşir; başka bir deyişle, her PST/posta kutusu çifti aynı anda içeri aktarılır. Aynı posta kutusuna birden çok PST dosyası içeri aktarılırsa, bunlar aynı anda değil sırayla (birer birer) içeri aktarılır.

> [!NOTE]
> <sup>\*</sup> Bu oran garanti değildir. Sunucu iş yükü ve geçici performans sorunları bu hızı düşürebilir.

#### <a name="after-microsoft-uploads-my-pst-files-to-azure-how-long-are-they-kept-in-azure-before-theyre-deleted"></a>Microsoft PST dosyalarımı Azure'a yükledikten sonra silinmeden önce Azure'da ne kadar süre tutulur?

Kuruluşunuzun Azure Depolama konumundaki tüm PST dosyaları (adlı `ingestiondata`blob kapsayıcısında), uyumluluk portalındaki **PST dosyalarını içeri aktar** sayfasında en son içeri aktarma işi oluşturulduktan 30 gün sonra silinir.

Bu, PST dosyalarının Azure Depolama alanından silindikten sonra uyumluluk portalında tamamlanmış bir içeri aktarma işinin dosya listesinde görüntülenmediği anlamına da gelir. Uyumluluk portalındaki **PST dosyalarını içeri aktar** sayfasında bir içeri aktarma işi listelenmeye devam ediyor olsa da, eski içeri aktarma işlerinin ayrıntılarını görüntülediğinizde PST dosyalarının listesi boş olabilir.

#### <a name="what-version-of-the-pst-file-format-is-supported-for-importing-to-microsoft-365"></a>pst dosya biçiminin Microsoft 365 içeri aktarma için hangi sürümü desteklenir?

PST dosya biçiminin iki sürümü vardır: ANSI ve Unicode. Unicode PST dosya biçimini kullanan dosyaları içeri aktarmanızı öneririz. Ancak, çift baytlık karakter kümesi (DBCS) kullanan diller gibi ANSI PST dosya biçimini kullanan dosyalar da Microsoft 365'a aktarılabilir. ANSI PST dosyalarını içeri aktarma hakkında daha fazla bilgi için bkz. [Kuruluşunuzun PST dosyalarını Microsoft 365 aktarmak için sürücü gönderimini kullanma](use-drive-shipping-to-import-pst-files-to-office-365.md#step-3-create-the-pst-import-mapping-file) konusundaki 3. Adım.

Ayrıca, Outlook 2007 ve sonraki sürümlerden PST dosyaları Microsoft 365 aktarılabilir.

#### <a name="is-there-a-message-size-limit-when-importing-pst-files-using-drive-shipping"></a>Sürücü gönderimini kullanarak PST dosyalarını içeri aktarırken ileti boyutu sınırı var mı?

Evet. PST dosyası 150 MB'tan büyük bir posta kutusu öğesi içeriyorsa, öğe atlanır ve içeri aktarma işlemi sırasında içeri aktarılmaz. 150 MB'tan büyük öğeler, Exchange Online ileti boyutu sınırı olduğundan içeri aktarılamaz. Daha fazla bilgi için bkz. [Exchange Online'de ileti sınırları](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#message-limits).

  **PST içeri aktarma işlemi yinelenen e-posta öğelerini nasıl işler?

PST içeri aktarma işlemi yinelenen öğeleri denetler ve hedef posta kutusunda veya hedef arşivde hedef klasörde eşleşen bir öğe varsa öğeleri PST dosyasından posta kutusuna veya arşive kopyalamaz. Aynı PST dosyasını yeniden içeri aktarır ve önceki içeri aktarma işinde belirttiğinizden farklı bir hedef klasör (PST içeri aktarma eşleme dosyasında TargetRootFolder özelliğini kullanarak) belirtirseniz, PST dosyasındaki tüm öğeler yeniden içeri aktarılır.

#### <a name="are-message-properties-such-as-when-the-message-was-sent-or-received-the-list-of-recipients-and-other-properties-preserved-when-pst-files-are-imported-to-a-microsoft-365-mailbox-using-drive-shipping"></a>İletinin ne zaman gönderildiği veya alındığı, alıcı listesi ve diğer özellikler gibi ileti özellikleri, PST dosyaları sürücü gönderimi kullanılarak bir Microsoft 365 posta kutusuna aktarıldığında korunuyor mu?

Evet. İçeri aktarma işlemi sırasında özgün ileti meta verileri değiştirilmez

#### <a name="is-there-a-limit-to-the-number-of-levels-in-a-folder-hierarchy-for-a-pst-file-that-i-want-to-import-to-a-mailbox-using-drive-shipping"></a>Sürücü gönderimini kullanarak posta kutusuna aktarmak istediğim pst dosyası için klasör hiyerarşisindeki düzey sayısı sınırı var mı?

Evet. 300 veya daha fazla iç içe klasör düzeyine sahip bir PST dosyasını içeri aktaramazsınız.

#### <a name="can-i-use-drive-shipping-to-import-pst-files-to-an-inactive-mailbox-in-microsoft-365"></a>PST dosyalarını Microsoft 365'deki etkin olmayan bir posta kutusuna aktarmak için sürücü gönderimi kullanabilir miyim?

Evet, bu özellik artık kullanılabilir.

#### <a name="can-i-use-drive-shipping-to-import-pst-files-to-an-online-archive-mailbox-in-an-exchange-hybrid-deployment"></a>PST dosyalarını Exchange karma dağıtımdaki çevrimiçi arşiv posta kutusuna aktarmak için sürücü gönderimi kullanabilir miyim?

Evet, bu özellik artık kullanılabilir.

#### <a name="can-i-use-drive-shipping-to-import-pst-files-to-public-folders-in-exchange-online"></a>PST dosyalarını Exchange Online ortak klasörlere aktarmak için sürücü gönderimi kullanabilir miyim?

Hayır, PST dosyalarını ortak klasörlere aktaramazsınız.

#### <a name="can-microsoft-wipe-my-hard-drive-before-they-ship-it-back-to-me"></a>Microsoft sabit sürücümü bana geri göndermeden önce silebilir mi?

Hayır, Microsoft sabit sürücüleri müşterilere geri göndermeden önce temizleyemez. Sabit sürücüler, Microsoft tarafından alındığında bulundukları durumda size döndürülür.

#### <a name="can-microsoft-shred-my-hard-drive-instead-of-shipping-it-back-to-me"></a>Microsoft sabit sürücümü bana geri göndermek yerine parçalayabilir mi?

Hayır, Microsoft sabit sürücünüzü yok etmez. Sabit sürücüler, Microsoft tarafından alındığında bulundukları durumda size döndürülür.

#### <a name="what-courier-services-are-supported-for-return-shipping"></a>İade gönderimi için hangi kurye hizmetleri desteklenir?

Birleşik Devletler veya Avrupa'da müşteriyseniz Microsoft, sabit sürücünüzü iade etmek için FedEx kullanır. Microsoft, diğer tüm bölgeler için DHL kullanır.

#### <a name="what-are-the-return-shipping-costs"></a>İade gönderim maliyetleri nelerdir?

İade gönderim maliyetleri, sabit sürücünüzü sevk ettiğiniz Microsoft veri merkezine yakınlığınıza bağlı olarak değişir. Microsoft, sabit sürücünüzü iade etmek için FedEx veya DHL hesabınızı faturalandıracaktır. İade gönderiminin maliyeti sizin sorumluluğunuzdadır.

#### <a name="can-i-use-a-custom-courier-shipping-service-such-as-fedex-custom-shipping-to-ship-my-hard-drive-to-microsoft"></a>Sabit sürücümü Microsoft'a göndermek için FedEx Custom Shipping gibi özel bir kurye gönderim hizmetini kullanabilir miyim?

Evet.

#### <a name="if-i-have-to-ship-my-hard-drive-to-another-country-is-there-anything-i-need-to-do"></a>Sabit diskimi başka bir ülkeye göndermek zorunda kalırsam yapmam gereken bir şey var mı?

Microsoft'a sevk ettiğiniz sabit sürücünün uluslararası sınırları aşması gerekebilir. Bu durumda, sabit sürücünün ve içerdiği verilerin ilgili yasalara uygun olarak içeri ve/veya dışarı aktarılmasını sağlamak sizin sorumluluğundadır. Sabit sürücüyü göndermeden önce, sürücünüzün ve verilerinizin belirtilen Microsoft veri merkezine yasal olarak gönderilebildiğini doğrulamak için danışmanlarınıza danışın. Bu, Microsoft'a zamanında ulaşmasını sağlamaya yardımcı olur.
