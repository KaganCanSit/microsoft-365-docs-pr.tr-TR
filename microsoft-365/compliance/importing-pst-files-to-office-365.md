---
title: Kuruluş PST dosyalarını içeri aktarma hakkında bilgi
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
description: E-posta verilerini (PST dosyaları) kullanıcı posta kutularına toplu olarak içeri Microsoft 365 uyumluluk merkezi için, İçeri Aktarma hizmetini nasıl kullanabileceğinizi öğrenin.
ms.openlocfilehash: b88cd9f6b12f382f8fdeb696af32c1fd95ad805d
ms.sourcegitcommit: 400ef9ac34247978e3de7ecc0b376c4abb6c99d8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/27/2022
ms.locfileid: "63010860"
---
# <a name="learn-about-importing-your-organizations-pst-files"></a>Kuruluş PST dosyalarını içeri aktarma hakkında bilgi

> [!NOTE]
> Bu makale yöneticilere aittir. PST dosyalarını kendi posta kutunuza içeri aktarmaya mı çalışıyorsunuz? Bkz[. E-postayı, kişileri ve takvimi Outlook .pst dosyasından içeri aktarma](https://go.microsoft.com/fwlink/p/?LinkID=785075).

PST dosyalarını hızla toplu olarak içeri ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">Microsoft 365 uyumluluk merkezi</a> posta kutularına toplu olarak içeri Exchange Online İçeri Aktarma hizmetini kullanabilirsiniz. PST dosyalarını başka bir klasöre aktarmanın iki Microsoft 365:

- **Ağ karşıya yükleme** ![ Bulut karşıya yükleme.](../media/54ab16ee-3822-4551-abef-3d926f4e1c01.png) - Upload PST dosyalarını Microsoft bulutunda geçici bir Azure Depolama konuma taşıyın. Ardından PST verilerini Microsoft 365 posta kutularına içeri aktarma işlemi yapmak için İçeri Aktarma Hizmeti'ne yönlendirilirsiniz.

- **Sürücü gönderimi** ![ Sabit disk.](../media/e72b76f3-1f73-4296-b749-c325d95d9ef6.png) - PST dosyalarını BitLocker şifreli bir sabit sürücüye kopyalayın ve ardından sürücüyü fiziksel olarak Microsoft'a gönderebilirsiniz. Microsoft sabit sürücüyü aldığında, veri merkezi personeli verileri Microsoft bulutunda geçici bir Azure Depolama konuma yükler. Ardından, verileri Microsoft 365 posta kutularına içeri aktarma işlemi yapmak için İçeri Aktarma Hizmeti'ne yönlendirilirsiniz.

## <a name="step-by-step-instructions"></a>Adım adım yönergeler

Kuruluş PST dosyalarını toplu olarak içeri aktarmanın ayrıntılı ve adım adım yönergeleri için, aşağıdaki konulardan birini Microsoft 365.

- [PST dosyalarını başka bir klasöre içeri yüklemek için ağ karşıya Microsoft 365](use-network-upload-to-import-pst-files.md)

- [PST dosyalarını içeri aktarma için sürücü gönderimi kullanma](use-drive-shipping-to-import-pst-files-to-office-365.md)

## <a name="how-importing-pst-files-works"></a>PST dosyalarını içeri aktarma nasıl çalışır?

Pst içeri aktarma işleminin eksiksiz bir çizimi ve açıklaması aşağıdadır. Çizimde birincil iş akışı gösterilmiştir ve ağ karşıya yükleme ile sürücü gönderim yöntemleri arasındaki farklar vurgulanır.

![PST içeri aktarma işleminin iş akışı.](../media/76997b69-67d7-433a-a0ca-9389f85a36a1.png)

1. **PST içeri aktarma** araçlarını ve anahtarını özel Azure Depolama konumu için indirin - İlk adım, PST dosyalarını karşıya yüklemek veya bunları sabit sürücüye kopyalamak için kullanılan aracı ve erişim anahtarını indirmektir. Bunları, çalışma **sayfasındaki İçeri** Aktar Microsoft 365 uyumluluk merkezi. Bu anahtar SIZE (sürücü gönderimi durumunda Microsoft veri merkezi personeline) PST dosyalarını özel ve güvenli bir Azure depolama yerine yüklemek için gerekli Depolama sağlar. Bu erişim anahtarı, sizin için benzersizdir ve Microsoft buluta yüklendikten sonra PST dosyalarınıza yetkisiz erişimin önlenmesine yardımcı olur. PST dosyalarını başka bir Microsoft 365 aktarma işlemi, kuruma ayrı bir Azure aboneliğinin olması gerektirmez.

2. **Upload seçin veya kopyalayın** - Sonraki adım PST dosyalarını içeri aktarmada ağ karşıya yükleme veya sürücü gönderimi mi kullandığınıza bağlıdır. Her iki durumda da, önceki adımda edinilen araç ve güvenli depolama anahtarını kullanıyabilirsiniz.

    - **Ağ karşıya yükleme:** Bu AzCopy.exe (1. adımda indirilen araç), PST dosyalarınızı Microsoft bulutunda bir Azure Depolama konuma yüklemek ve depolamak için kullanılır. PST Depolama yüklediğiniz Azure Depolama Konumu, kurumla aynı bölgesel Microsoft veri merkezinde yer alır.

      Bunları karşıya yüklemek için, içeri aktarma işlemi yapmak istediğiniz PST dosyalarının, kurumda bir dosya paylaşımında veya dosya sunucusunda yer almaları gerekir.

    - **Sürücü gönderimi:** Bu WAImportExport.exe (1. adımda indirilen araç), PST dosyalarınızı sabit sürücüye kopyalamak için kullanılır. Bu araç sabit sürücüyü BitLocker ile şifreler ve sonra PST'leri sabit sürücüye kopyalar. Ağ karşıya yükleme gibi, sabit sürücüye kopyalamak istediğiniz PST dosyalarının de, kurumda bir dosya paylaşımında veya dosya sunucusunda yer alıyor olması gerekir.

3. **PST** içeri aktarma eşleme dosyası oluşturma - PST dosyaları Azure Depolama konuma yüklendikten veya sabit sürücüye kopyalandıktan sonra, sonraki adım, PST dosyalarının hangi kullanıcı posta kutularına aktar alın olacağını (ve bir PST dosyasının kullanıcının birincil posta kutusuna veya kullanıcının arşiv posta kutusuna aktarıla olacağını) belirten bir virgülle ayrılmış değer (CSV) dosyası oluşturmaktır. [PST İçeri Aktarma eşleme dosyasının bir kopyasını indirin](https://go.microsoft.com/fwlink/p/?LinkId=544717). Veri Microsoft 365 hizmeti PST dosyalarını içeri aktarmada bu bilgileri kullanır.

4. **PST içeri aktarma işi** oluşturma - Sonraki adım, Microsoft 365 uyumluluk merkezi'de **PST** dosyalarını içeri aktar sayfasında bir PST içeri aktarma işi oluşturmak ve önceki adımda oluşturulan PST içeri aktarma eşleme dosyasını göndermektir. Ağ karşıya yükleme için (PST dosyaları Azure'a yük olduğundan) Microsoft 365, PST dosyalarında yer alan verileri analiz eder ve ardından size PST içeri aktarma eşleme dosyasında belirtilen posta kutularına gerçek olarak hangi verilerin içeri aktar yük olasını kontrol etmek üzere filtreler ayarlama fırsatı verir.

    Sürücü gönderimi için, bu noktada işlemde birkaç şey daha olur.

    - Sabit sürücüyü fiziksel olarak Bir Microsoft veri merkezine gönderebilirsiniz (içeri aktarma işi oluşturulduğunda Microsoft veri merkezinin sevkiyat adresi görüntülenir).

    - Microsoft sabit sürücüyü aldığında, veri merkezi personeli PST dosyalarını sabit sürücüde bulunan Azure Depolama konuma yükler. Daha önce de açıklanmıştır; PST dosyalarınız, Depolama aynı bölgesel Microsoft veri merkezinde yer alan bir Azure Veritabanı konuma yüklendi.

      > [!NOTE]
      > Sabit sürücüde yer alan PST dosyaları, Microsoft'un sabit sürücüyü aldığından 7 - 10 iş günü içinde Azure'a yükler.

      Ağ karşıya yükleme işlemi gibi, Microsoft 365 PST dosyalarında yer alan verileri de analiz eder ve size PST içeri aktarma eşleme dosyasında belirtilen posta kutularına gerçek olarak hangi verilerin içeri aktar yük olasını kontrol etmek üzere filtreler ayarlama fırsatı verir.

    - Sabit sürücü microsoft tarafından size geri gönderilir.

5. Posta kutularına aktaracak **PST** verilerini filtreleme - İçeri aktarma işi oluşturulduktan (ve bir sürücü gönderim işinden gelen PST dosyaları Azure Depolama'e yüklendikten sonra) Microsoft 365 PST dosyalarında yer alan öğelerin yaşını ve farklı ileti türlerini tanımarak PST dosyalarında bulunan verileri analiz eder (güvenli ve güvenli bir şekilde). Çözümleme tamamlandığında ve veriler içeri aktarmaya hazır olduğunda, PST dosyalarında yer alan tüm verileri içeri aktarma seçeneğiniz vardır veya içeri aktarılan verileri, hangi verilerin içeri aktar ayarlanacaklarını denetimi altına alan filtreler ayararak kırpabilirsiniz.

6. **PST** içeri aktarma işini başlatma - İçeri aktarma işi başlatıldıktan sonra, Microsoft 365 PST içeri aktarma eşleme dosyasındaki bilgileri kullanarak PST dosyalarını Azure Depolama posta kutularına aktarır. İşle ilgili durum bilgileri (içeri aktarılan her PST dosyasıyla ilgili bilgiler de dahil olmak üzere) pst  dosyalarını içeri aktar sayfasında Microsoft 365 uyumluluk merkezi. İçeri aktarma işi bittiğinde, işin durumu Tamamlandı olarak **ayarlanır**.

## <a name="why-import-email-data-to-microsoft-365"></a>E-posta verilerini neden başka bir Microsoft 365?

- Bu, arşivlemek için kuruluş mesajlaşma verilerini arşivlemek için iyi bir Microsoft 365.

- Akıllı İçeri Aktarma [özelliğini kullanarak](filter-data-when-importing-pst-files.md) , gerçek olarak hedef posta kutularına içeri aktarılan PST dosyalarında yer alan öğeleri filtreleebilirsiniz. Böylece, hangi verilerin alın alanlarını denetlemeye olanak sağlayan filtreler ayararak, aktarılan verileri kırpabilirsiniz.

- E-posta verilerini e-Microsoft 365, şunları size izin vererek kuruluş uyumluluk 2013'e uymasına yardımcı olur:

  - [Kullanıcılara ek posta kutusu](enable-archive-mailboxes.md) depolama [alanı sağlamak için arşiv posta kutularını](autoexpanding-archiving.md) etkinleştirin ve otomatik genişleyen arşivleme.

  - İçeriği korumak için posta [kutularını Mahkeme Tutma'ya](./create-a-litigation-hold.md) alın.

  - Posta kutusu [içeriği aramak için](content-search.md) İçerik Arama aracını kullanın.

  - [EBulma olaylarını](./get-started-core-ediscovery.md) kullanarak kuruluşla ilgili yasal incelemeleri yönetme

  - Posta [kutusu içeriğinin](retention.md) ne kadar Microsoft 365 uyumluluk merkezi tutularak korunarak, bekletme süresinin sona erdikten sonra da içeriği silmek için, bekletme ilkesinde bekletme ilkelerini kullanın.

  - [İletileri incelemek ve](communication-compliance.md) ileti standartlarıyla uyumlu olduğundan emin olmak ve sınıflandırma türü eklemek için İletişim uyumluluk ilkelerini kullanın.

- Verileri başka bir Microsoft 365 veri kaybına karşı korumaya yardımcı olur. E-postaya aktarılan e-Microsoft 365, verilerin yüksek kullanılabilirlik özelliklerini Exchange Online.

- E-posta verileri tüm cihazlardan kullanıcılara kullanılabilir, çünkü bunlar bulutta depolanıyordur.

## <a name="importing-sharepoint-data-to-microsoft-365"></a>Verileri SharePoint aktarma Microsoft 365

Ayrıca, dosyaları ve belgeleri tüm sitelere SharePoint ve OneDrive hesaplarınıza aktarabilirsiniz. Daha fazla bilgi için aşağıdaki makalelere bakın:

- [SharePoint Online'a geçiş](/sharepointmigration/migrate-to-sharepoint-online)

- [SharePoint Geçiş Aracı'nın tanıtımı](/sharepointmigration/introducing-the-sharepoint-migration-tool)

- [PowerShell kullanarak SharePoint Online'a geçiş](/sharepointmigration/overview-spmt-ps-cmdlets)

- [Azure Data Box'ı kullanarak dosya SharePoint Online'a dosya paylaşımı içeriğinizi geçirme](/sharepointmigration/how-to-migrate-file-share-content-to-spo-using-azuredatabox)

## <a name="frequently-asked-questions-about-importing-pst-files"></a>PST dosyalarını içeri aktarma hakkında sık sorulan sorular

PST dosyalarını posta kutularına toplu olarak içeri Microsoft 365 Için İçeri Aktarma hizmetini kullanma hakkında sık Microsoft 365 burada açık ve açık sorularınız vardır.

- [PST dosyalarını içeri yüklemek için ağ karşıya yükleme kullanma](#using-network-upload-to-import-pst-files)

- [PST dosyalarını içeri aktarma için sürücü gönderimi kullanma](#using-drive-shipping-to-import-pst-files)

### <a name="using-network-upload-to-import-pst-files"></a>PST dosyalarını içeri yüklemek için ağ karşıya yükleme kullanma

#### <a name="what-permissions-are-required-to-create-import-jobs-in-the-microsoft-365-import-service-using-network-upload"></a>Ağ karşıya yükleme kullanarak İçeri Aktarma Hizmeti'Microsoft 365 içeri aktarma işleri oluşturmak için hangi izinler gereklidir?

PST dosyalarını posta kutularına içeri aktarabilirsiniz ve bu Exchange Online Posta Kutusu İçeri/Dışarı Aktarma rolüne Microsoft 365 gerekir. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü Kuruluş Yönetimi rol grubuna  eklersiniz. Ya da yeni bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve ardından kendinizi veya diğer kullanıcıları üye olarak  ekleyin. Daha fazla bilgi için, Exchange Online'de rol gruplarını yönetme konusunda "Bir rol grubuna rol ekleme" veya "Rol grubu oluşturma" [bölümlerine Exchange Online](/Exchange/permissions-exo/role-groups).

Buna ek olarak, iş yerlerinde Microsoft 365 uyumluluk merkezi işleri oluşturmak için, aşağıdakilerden biri doğru olabilir:

- Posta'da Posta Alıcıları rolüne atanmış Exchange Online. Varsayılan olarak, bu rol Kuruluş Yönetimi ve Alıcı Yönetimi rol gruplarına atanır.

    Veya

- Kurumda genel yönetici olmak gerekir.

> [!TIP]
> Pst dosyalarını başka kullanıcılara Exchange Online özel olarak tasarlanmış yeni bir rol grubu oluşturmayı Microsoft 365. PST dosyalarını içeri aktarmanız için gereken minimum düzeydeki ayrıcalıklar için Posta Kutusunu İçeri/Dışarı Aktar ve Posta Alıcıları rollerini yeni rol grubuna atayın ve ardından üyeleri ekleyin.

#### <a name="where-is-network-upload-available"></a>Ağ karşıya yükleme nerede kullanılabilir?

Ağ karşıya yükleme şu anda şu bölgelerde kullanılabilir: ABD, Kanada, Brezilya, Birleşik Krallık, Fransa, Almanya, İsviçre, Norveç, Avrupa, Hindistan, Doğu Asya, Güneydoğu Asya, Japonya, Kore Cumhuriyeti, Avustralya ve Birleşik Arap Emirlikleri (BAE). Ağ karşıya yükleme gelecekte daha fazla bölgede kullanılabilir olacaktır.

#### <a name="what-is-the-pricing-for-importing-pst-files-by-using-network-upload"></a>PST dosyalarını ağ karşıya yükleme kullanarak içeri aktarmanın fiyatı nedir?

PST dosyalarını içeri yüklemek için ağ karşıya yükleme ücretsizdir.

Bu, PST dosyalarının Azure Depolama alanında silindikten sonra dosya listesinde, iş verileri üzerinde tamamlanmış içeri aktarma işlerinden [Microsoft 365 yönetim merkezi.](https://go.microsoft.com/fwlink/p/?linkid=2024339) Verileri şu ana kadar içeri aktarma sayfasında bir içeri aktarma işinin hala **Microsoft 365**, eski içeri aktarma işlerinin ayrıntılarına bakarak PST dosya listesi boş olabilir.

#### <a name="what-version-of-the-pst-file-format-is-supported-for-importing-to-microsoft-365"></a>PST dosya biçiminin hangi sürümü dosya biçimine içeri aktarmayı Microsoft 365?

PST dosya biçiminin iki sürümü vardır: ANSI ve Unicode. Unicode PST dosya biçimini kullanan dosyaları içeri aktarmanız önerilir. Bununla birlikte, çift byte karakter kümesi (DBCS) kullanan diller gibi ANSI PST dosya biçimini kullanan dosyalar da başka bir Microsoft 365. ANSI PST dosyalarını içeri aktarma hakkında daha fazla bilgi için PST dosyalarını başka bir [Microsoft 365.](./use-network-upload-to-import-pst-files.md)

Ayrıca, Outlook 2007 ve sonraki sürümlerden PST dosyaları da Microsoft 365.

#### <a name="after-i-upload-my-pst-files-to-the-azure-storage-area-how-long-are-they-kept-in-azure-before-theyre-deleted"></a>Azure Depolama alanına yükledikten sonra PST dosyalarım silinmeden ne kadar süre Azure'da tutulur?

PST dosyalarını içeri aktarma ağ karşıya yükleme yöntemini kullanarak, bu dosyaları adlı bir Azure blob kapsayıcısı üzerine yüklersiniz `ingestiondata`. Microsoft 365 uyumluluk merkezi'daki **PST** dosyalarını içeri aktar sayfasında devam eden bir içeri aktarma işi yoksa, Azure'da kapsayıcıda yer alan tüm PST `ingestiondata` dosyaları, iş sayfasında en son içeri aktarma işi oluşturulduktan 30 gün sonra Microsoft 365 uyumluluk merkezi. Bu aynı zamanda PST dosyalarını Azure'a yükledikten sonra 30 gün içinde Microsoft 365 uyumluluk merkezi'te yeni bir içeri aktarma işi oluşturmanız (ağ karşıya yükleme yönergelerinin 5. Adımında açıklanmıştır) anlamına da gelir.

Bu, PST dosyalarının Azure Depolama alanında silindikten sonra, iş yerlerinden tamamlanmış içeri aktarma işlerinden dosya listesinde de görüntülenmeymeyecekleri Microsoft 365 uyumluluk merkezi. pst dosyalarını içeri aktarma sayfasındaki **PST** dosyalarını içeri aktarma sayfasında bir içeri aktarma işi hala Microsoft 365 uyumluluk merkezi bulunsa da, eski içeri aktarma işlerinin ayrıntılarına bakarak PST dosya listesi boş olabilir.

#### <a name="how-long-does-it-take-to-import-a-pst-file-to-a-mailbox-using-network-upload"></a>Ağ karşıya yükleme kullanarak bir PST dosyasını posta kutusuna içeri aktarmanız ne kadar zaman alır?

Ağ kapasitesine bağlıdır, ancak her terabaytlık (TB) verinin kuruma uygun Azure Depolama alanına Depolama saat sürer. PST dosyaları Azure Depolama alanına kopyalandıktan sonra, bir PST dosyası günde yaklaşık 24 GB Microsoft 365 posta kutusuna içeri aktarılır<sup>\*</sup>. Bu hız sizin ihtiyaçlarını karşılamazsa, e-posta verilerini kendi verilerinize almak için diğer yöntemleri Microsoft 365. Daha fazla bilgi için birden [çok e-posta hesabını başka bir hesaba geçirmenin Microsoft 365](/Exchange/mailbox-migration/mailbox-migration).

Farklı PST dosyaları farklı hedef posta kutularına aktarılırsa, içeri aktarma süreci paralel olarak gerçekleşir; başka bir deyişle, her PST/posta kutusu çifti aynı anda içeri aktarılır. Aynı posta kutusuna birden çok PST dosyası aktarıldısa, bunlar aynı anda değil sırayla (bir defada) içeri aktarılmaz.

> [!NOTE]
> <sup>\*</sup> Bu oran garanti değildir. Sunucu iş yükü ve geçici performans sorunları bu oranı düşürebilir.

#### <a name="how-does-the-pst-import-process-handle-duplicate-email-items"></a>PST içeri aktarma işlemi yinelenen e-posta öğelerini nasıl işler?

PST içeri aktarma işlemi yinelenen öğeleri denetler ve eşleşen öğe hedef posta kutusunun veya hedef arşivin hedef klasöründe yer alan eşleşen bir öğe varsa, bu öğeleri PST dosyasından posta kutusuna veya arşive kopyalamaz. Aynı PST dosyasını yeniden içeri aktarır ve ÖNCEKI içeri aktarma işlerinden farklı bir hedef klasör belirtirsiniz (PST içeri aktarma eşleme dosyasında TargetRootFolder özelliğini kullanarak), PST dosyasındaki tüm öğeler yeniden aktarılmış olur.

#### <a name="is-there-a-message-size-limit-when-importing-pst-files-using-network-upload"></a>Ağ karşıya yükleme kullanarak PST dosyalarını içeri aktarma işlemi için bir ileti boyutu sınırı var mı?

Evet. PST dosyası 150 MB'tan büyük bir posta kutusu öğesi içeriyorsa, bu öğe içeri aktarma işlemi sırasında atlanır ve içeri aktarılmaz. 150 MB'den büyük öğeler aktarılmaz çünkü 150 MB bu büyüklükteki ileti boyutu Exchange Online. Daha fazla bilgi için bkz[. Alan için Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#message-limits).

#### <a name="are-message-properties-such-as-when-the-message-was-sent-or-received-the-list-of-recipients-and-other-properties-preserved-when-pst-files-are-imported-to-a-microsoft-365-mailbox-using-network-upload"></a>İletinin ne zaman gönderildiği veya alın aldığı, alıcı listesi ve diğer özellikler gibi ileti özellikleri PST dosyaları ağ karşıya yükleme kullanılarak bir Microsoft 365 kutusuna aktarıldı mı?

Evet. İçeri aktarma işlemi sırasında özgün ileti meta verileri değişmez.

#### <a name="is-there-a-limit-to-the-number-of-levels-in-a-folder-hierarchy-for-a-pst-file-that-i-want-to-import-to-a-mailbox-using-network-upload"></a>Ağ karşıya yükleme kullanarak posta kutusuna içeri aktarma işlemi yapmak istediğim PST dosyası için klasör hiyerarşisinde düzey sayısının bir sınırı var mı?

Evet. 300 veya daha fazla düzeyde iç içe klasörler içeren bir PST dosyasını içeri aktarabilirsiniz.

#### <a name="can-i-use-network-upload-to-import-pst-files-to-an-inactive-mailbox-in-microsoft-365"></a>PST dosyalarını outlook'ta etkin olmayan bir posta kutusuna içeri yüklemek için ağ karşıya Microsoft 365?

Evet, bu özellik artık kullanılabilir.

#### <a name="can-i-use-network-upload-to-import-pst-files-to-an-online-archive-mailbox-in-an-exchange-hybrid-deployment"></a>PST dosyalarını karma dağıtımda bir çevrimiçi arşiv posta kutusuna içeri yüklemek için ağ karşıya Exchange kullanabilir miyim?

Evet, bu özellik artık kullanılabilir.

#### <a name="can-i-use-network-upload-to-import-pst-files-to-public-folders-in-exchange-online"></a>PST dosyalarını başka bir klasörde yer alan ortak klasörlere içeri yüklemek için ağ karşıya Exchange Online?

Hayır, PST dosyalarını ortak klasörlere içeri aktarabilirsiniz.

### <a name="using-drive-shipping-to-import-pst-files"></a>PST dosyalarını içeri aktarma için sürücü gönderimi kullanma

#### <a name="what-permissions-are-required-to-create-import-jobs-in-the-microsoft-365-import-service-using-drive-shipping"></a>Sürücü gönderimi kullanarak Içeri Aktarma Hizmeti'Microsoft 365 içeri aktarma işleri oluşturmak için hangi izinler gereklidir?

PST dosyalarını bu posta kutularına içeri aktarabilirsiniz ve bu posta kutularına Posta Kutusu İçeri/Dışarı aktarma Microsoft 365 gerekir. Varsayılan olarak, bu rol herhangi bir rol grubuna Exchange Online. Posta Kutusu İçeri/Dışarı Aktarma rolünü Kuruluş Yönetimi rol grubuna  eklersiniz. Ya da yeni bir rol grubu oluşturabilir, Posta Kutusu İçeri/Dışarı Aktarma rolü atayabilirsiniz ve ardından kendinizi veya diğer kullanıcıları üye olarak  ekleyin. Daha fazla bilgi için, Exchange Online'de rol gruplarını yönetme konusunda "Bir rol grubuna rol ekleme" veya "Rol grubu oluşturma" [bölümlerine Exchange Online](/Exchange/permissions-exo/role-groups).

Buna ek olarak, iş yerlerinde Microsoft 365 uyumluluk merkezi işleri oluşturmak için, aşağıdakilerden biri doğru olabilir:

- Posta'da Posta Alıcıları rolüne atanmış Exchange Online. Varsayılan olarak, bu rol Kuruluş Yönetimi ve Alıcı Yönetimi rol gruplarına atanır.

    Veya

- Kurumda genel yönetici olmak gerekir.

> [!TIP]
> Pst dosyalarını başka kullanıcılara Exchange Online özel olarak tasarlanmış yeni bir rol grubu oluşturmayı Microsoft 365. PST dosyalarını içeri aktarmanız için gereken minimum düzeydeki ayrıcalıklar için Posta Kutusunu İçeri/Dışarı Aktar ve Posta Alıcıları rollerini yeni rol grubuna atayın ve ardından üyeleri ekleyin.

#### <a name="where-is-drive-shipping-available"></a>Sürücü gönderimi nereden kullanılabilir?

Sürücü gönderimi şu anda Amerika Birleşik Devletleri, Kanada, Brezilya, Birleşik Krallık, Avrupa, Hindistan, Doğu Asya, Güneydoğu Asya, Japonya, Kore Cumhuriyeti ve Avustralya'da kullanılabilir. Gelecekte daha fazla bölgede sürücü gönderimi  sağlanmaktadır.

> [!NOTE]
> Şu anda, PST dosyalarını içeri aktarmaya sürücü gönderimi Almanya ve İsviçre'de kullanılamıyor. Bu SSS bölümü, sürücü gönderimi bu ülkelerde kullanılabilir olduğunda güncelleştirilecek.

#### <a name="what-commercial-licensing-agreements-support-drive-shipping"></a>Hangi ticari lisans anlaşmaları sürücü gönderimlerini destekler?

PST dosyalarını Microsoft 365'a içeri Kurumsal Anlaşma sürücü gönderimi bir Microsoft Kurumsal Anlaşma . Sürücü gönderimi, bir Microsoft Ürün ve Hizmet Sözleşmesi (MPSA) ile kullanılamaz.

#### <a name="what-is-the-pricing-for-using-drive-shipping-to-import-pst-files-to-microsoft-365"></a>PST dosyalarını başka bir klasöre içeri aktararak sürücü gönderimi kullanmanın Microsoft 365?

PST dosyalarını bu posta kutularına içeri aktarma işlemi için sürücü gönderimi kullanımının Microsoft 365 GB veri başına $2 Amerikan Dolarıdır. Örneğin, 1.000 GB (1 TB) PST dosyası içeren bir sabit sürücüyü sevk maliyeti 2.000 Amerikan Dolarıdır. İçeri aktarma ücretini ödemek için bir iş ortağıyla çalışabilirsiniz. İş ortağı bulma hakkında daha fazla bilgi için bkz [. Microsoft iş ortağınızı veya satıcınızı bulma](../admin/manage/find-your-partner-or-reseller.md).

#### <a name="what-kind-of-hard-drives-are-supported-for-drive-shipping"></a>Sürücü gönderimi hangi tür sabit sürücüleri destekler?

Microsoft 365 İçeri Aktarma hizmeti için yalnızca 2,5 inç katı hal sürücülerin (CD'ler) ya da 2,5 inç veya 3,5 inç SATA II/III dahili sabit sürücülerin kullanımı desteklemektedir. 10 TB'a kadar sabit sürücü kullanabilirsiniz. İçeri aktarma işlerinde, yalnızca sabit sürücüde ilk veri birimi işlenir. Veri biriminin NTFS ile biçimlendirilmiş olması gerekir. Sabit sürücüye veri kopyalayıp 2,5 inç SSD veya 2,5 inç ya da 3,5 inç SATA II/III bağlayıcı kullanarak doğrudan sabit sürücüye iliştirebilirsiniz veya harici 2,5 inç SSD veya 2,5 inç ya da 3,5 inç SATA II/III USB bağdaştırıcısı kullanarak dışarıdan da iliştirebilirsiniz.

> [!IMPORTANT]
> Yerleşik USB bağdaştırıcısı olan harici sabit sürücüler, USB İçeri Aktarma hizmeti Microsoft 365 desteklemez. Ayrıca, bir harici sabit sürücü kasa içindeki disk de kullanılamaz. Lütfen harici sabit sürücüleri sevk etme.

#### <a name="how-many-hard-drives-can-i-ship-for-a-single-import-job"></a>Bir içeri aktarma işi için kaç tane sabit sürücü gönderebilirsiniz?

Bir içeri aktarma işi için en fazla 10 sabit sürücü gönderebilirsiniz.

#### <a name="after-i-ship-my-hard-drive-how-long-does-it-take-to-get-to-the-microsoft-datacenter"></a>Sabit sürücüm sevk edildikten sonra Microsoft veri merkezlerine ne kadar süreyle ulaşabilirsiniz?

Bu, Microsoft veri merkezine yakınlığınıza ve sabit sürücünizi hangi tür gönderim seçeneği ile sevk etmek istediğinize (sonraki gün teslim, iki gün içinde teslim veya yeri teslim gibi) göre değişir. Çoğu gönderici, gönderinizin durumunu takip numarasıyla takip etmek için kullanabilirsiniz.

#### <a name="after-my-hard-drive-arrives-at-the-microsoft-datacenter-how-long-does-it-take-to-upload-my-pst-files-to-azure"></a>Sabit sürücüm Microsoft veri merkezine gelince PST dosyalarımı Azure'a yüklemek ne kadar sürdü?

Sabit sürücün Microsoft veri merkezinde alındıktan sonra PST dosyalarının kurum için Azure Veri Merkezi'ne Depolama yüklemesi 7 - 10 iş günü kadar sürer. PST dosyaları, adlı bir Azure blob kapsayıcısı üzerine karşıya yükler `ingestiondata`.

#### <a name="how-long-does-it-take-to-import-a-pst-file-to-a-mailbox-using-drive-shipping"></a>Sürücü gönderimi kullanarak bir PST dosyasını posta kutusuna içeri aktarmanız ne kadar zaman alır?

PST dosyaları Azure Depolama alanına yüklendikten sonra, Microsoft 365 PST dosyalarında bulunan öğelerin yaşını ve farklı ileti türlerini tanımlamak için PST dosyalarında bulunan verileri analiz eder (güvenli bir şekilde). Bu çözümleme tamamlandığında, size PST dosyalarında yer alan tüm verileri içeri aktarma veya hangi verilerin içeri aktarılmaz olduğunu denetlemeye yönelik filtreler ayarlama seçeneği vardır. Siz içeri aktarma işini başladıktan sonra, PST dosyası günde yaklaşık 24 GB Microsoft 365 bir posta kutusuna aktarılır.<sup>\*</sup> Bu hız sizin ihtiyaçlarını karşılamazsa, e-posta verilerini kendi verilerinize almak için diğer yöntemleri Microsoft 365. Daha fazla bilgi için birden [çok e-posta hesabını başka bir hesaba geçirmenin Microsoft 365](/Exchange/mailbox-migration/mailbox-migration).

Farklı PST dosyaları farklı hedef posta kutularına aktarılırsa, içeri aktarma süreci paralel olarak gerçekleşir; başka bir deyişle, her PST/posta kutusu çifti aynı anda içeri aktarılır. Aynı posta kutusuna birden çok PST dosyası aktarıldısa, bunlar aynı anda değil sırayla (bir defada) içeri aktarılmaz.

> [!NOTE]
> <sup>\*</sup> Bu oran garanti değildir. Sunucu iş yükü ve geçici performans sorunları bu oranı düşürebilir.

#### <a name="after-microsoft-uploads-my-pst-files-to-azure-how-long-are-they-kept-in-azure-before-theyre-deleted"></a>Microsoft, PST dosyalarımı Azure'a yükledikten sonra bu dosyalar silinmeden ne kadar süre Azure'da tutulur?

Azure'un Azure Depolama konumdaki tüm PST dosyaları (adlı blob `ingestiondata`kapsayıcısında), en son içeri aktarma işi, dosyanın PST dosyalarını içeri aktarma sayfasında oluşturulduktan 30 gün sonra  Microsoft 365 uyumluluk merkezi.

Bu, PST dosyalarının Azure Depolama alanında silindikten sonra, iş yerlerinden tamamlanmış içeri aktarma işlerinden dosya listesinde de görüntülenmeymeyecekleri Microsoft 365 uyumluluk merkezi. pst dosyalarını içeri aktarma sayfasındaki **PST** dosyalarını içeri aktarma sayfasında bir içeri aktarma işi hala Microsoft 365 uyumluluk merkezi bulunsa da, eski içeri aktarma işlerinin ayrıntılarına bakarak PST dosya listesi boş olabilir.

#### <a name="what-version-of-the-pst-file-format-is-supported-for-importing-to-microsoft-365"></a>PST dosya biçiminin hangi sürümü dosya biçimine içeri aktarmayı Microsoft 365?

PST dosya biçiminin iki sürümü vardır: ANSI ve Unicode. Unicode PST dosya biçimini kullanan dosyaları içeri aktarmanız önerilir. Bununla birlikte, çift byte karakter kümesi (DBCS) kullanan diller gibi ANSI PST dosya biçimini kullanan dosyalar da başka bir Microsoft 365. ANSI PST dosyalarını içeri aktarma hakkında daha fazla bilgi için, 3. adıma bakın. Kuruluş [PST](use-drive-shipping-to-import-pst-files-to-office-365.md#step-3-create-the-pst-import-mapping-file) dosyalarınızı başka bir Microsoft 365.

Ayrıca, Outlook 2007 ve sonraki sürümlerden PST dosyaları da Microsoft 365.

#### <a name="is-there-a-message-size-limit-when-importing-pst-files-using-drive-shipping"></a>Sürücü gönderimi kullanarak PST dosyalarını içeri aktarma işlemi için ileti boyutu sınırı var mı?

Evet. PST dosyası 150 MB'tan büyük bir posta kutusu öğesi içeriyorsa, bu öğe içeri aktarma işlemi sırasında atlanır ve içeri aktarılmaz. 150 MB'den büyük öğeler aktarılmaz çünkü 150 MB bu büyüklükteki ileti boyutu Exchange Online. Daha fazla bilgi için bkz[. Alan için Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#message-limits).

  **PST içeri aktarma işlemi yinelenen e-posta öğelerini nasıl işler?

PST içeri aktarma işlemi yinelenen öğeleri denetler ve eşleşen öğe hedef posta kutusunun veya hedef arşivin hedef klasöründe yer alan eşleşen bir öğe varsa, bu öğeleri PST dosyasından posta kutusuna veya arşive kopyalamaz. Aynı PST dosyasını yeniden içeri aktarır ve ÖNCEKI içeri aktarma işlerinden farklı bir hedef klasör belirtirsiniz (PST içeri aktarma eşleme dosyasında TargetRootFolder özelliğini kullanarak), PST dosyasındaki tüm öğeler yeniden aktarılmış olur.

#### <a name="are-message-properties-such-as-when-the-message-was-sent-or-received-the-list-of-recipients-and-other-properties-preserved-when-pst-files-are-imported-to-a-microsoft-365-mailbox-using-drive-shipping"></a>İletinin ne zaman gönderildiği veya alınmış olduğu, alıcı listesi ve diğer özellikler gibi ileti özellikleri, PST dosyaları sürücü gönderimi kullanılarak bir Microsoft 365 kutusuna aktarıldı mı?

Evet. İçeri aktarma işlemi sırasında hiçbir özgün ileti meta verisi değişmez

#### <a name="is-there-a-limit-to-the-number-of-levels-in-a-folder-hierarchy-for-a-pst-file-that-i-want-to-import-to-a-mailbox-using-drive-shipping"></a>Sürücü gönderimi kullanarak posta kutusuna içeri aktarmayı istediğim PST dosyası için, klasör hiyerarşisi içinde düzey sayısı için bir sınır var mı?

Evet. 300 veya daha fazla düzeyde iç içe klasörler içeren bir PST dosyasını içeri aktarabilirsiniz.

#### <a name="can-i-use-drive-shipping-to-import-pst-files-to-an-inactive-mailbox-in-microsoft-365"></a>ETKIN olmayan bir posta kutusuna PST dosyalarını içeri aktarma işlemi için sürücü gönderimi ve Microsoft 365?

Evet, bu özellik artık kullanılabilir.

#### <a name="can-i-use-drive-shipping-to-import-pst-files-to-an-online-archive-mailbox-in-an-exchange-hybrid-deployment"></a>PST dosyalarını karma dağıtımda bir çevrimiçi arşiv posta kutusuna içeri aktarmak için sürücü gönderimini Exchange kullanabilir miyim?

Evet, bu özellik artık kullanılabilir.

#### <a name="can-i-use-drive-shipping-to-import-pst-files-to-public-folders-in-exchange-online"></a>EXCHANGE ONLINE'ta PST dosyalarını ortak klasörlere içeri aktarma için sürücü gönderimi Exchange Online?

Hayır, PST dosyalarını ortak klasörlere içeri aktarabilirsiniz.

#### <a name="can-microsoft-wipe-my-hard-drive-before-they-ship-it-back-to-me"></a>Microsoft bana geri gönderemeden önce sabit sürücüm temizlerini kullanabilir mi?

Hayır, sabit sürücüleri müşterilere geri göndermeden önce Microsoft temizamaz. Sabit sürücüleri, Microsoft'a aldıklarında olduğu şekilde size geri gönderilir.

#### <a name="can-microsoft-shred-my-hard-drive-instead-of-shipping-it-back-to-me"></a>Microsoft bana geri dönmek yerine sabit sürücüme parça parça atsa ne olur?

Hayır, sabit sürücüm Microsoft tarafından yok olabilir. Sabit sürücüleri, Microsoft'a aldıklarında olduğu şekilde size geri gönderilir.

#### <a name="what-courier-services-are-supported-for-return-shipping"></a>Geri gönderim için hangi kurye hizmetleri desteklemektedir?

Amerika Birleşik Devletleri veya Avrupa'da çalışıyorsanız, Microsoft sabit sürücülerinizi geri iade etmek için FedEx kullanır. Microsoft diğer tüm bölgeler için DHL kullanır.

#### <a name="what-are-the-return-shipping-costs"></a>Geri gönderim maliyeti ne kadardır?

Geri gönderim maliyetleri, sabit sürücülerinizi sevk edilen Microsoft veri merkezine olan yakınlığınıza bağlı olarak değişir. Microsoft, sabit sürücülerinizi geri iade etmek için FedEx veya DHL hesaplarınızı faturalandıracak. Geri gönderim maliyeti,  sorumluluğunuzdur.

#### <a name="can-i-use-a-custom-courier-shipping-service-such-as-fedex-custom-shipping-to-ship-my-hard-drive-to-microsoft"></a>Sabit sürücüm microsoft'a gönderilirken FedEx Custom Shipping gibi özel bir kurye gönderim hizmeti kullanabilir miyim?

Evet.

#### <a name="if-i-have-to-ship-my-hard-drive-to-another-country-is-there-anything-i-need-to-do"></a>Sabit sürücüm başka bir ülkeye gönder gerekirse, ihtiyacım olan bir şey var mı?

Microsoft'a sevk etmek için sabit sürücü, uluslararası sınırları geçmek zorunda olabilir. Öyleyse, sabit sürücü ve içerdiği verilerin ilgili yasalara uygun şekilde içe ve/veya dışarı aktarılmış olmasını sağlamak sizin sorumluluğundadır. Sabit sürücü göndermeden önce, sürücü ve verilerinizin yasal olarak belirtilen Microsoft veri merkezine gönderilebilir olduğunu doğrulamak için danışmanlarınıza danışmanız gerekir. Bu, microsoft'a zamanında ulaşmasına yardımcı olur.
