---
title: İstenmeyen posta önleme koruması
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 6a601501-a6a8-4559-b2e7-56b59c96a586
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Yöneticiler, EOP'de (EOP) istenmeyen postaları önlemeye yardımcı olacak istenmeyen posta önleme ayarları Exchange Online Protection bilgi edinebilirsiniz.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1bc5d81b1221b73bcb701345b8db2f160380ba37
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "62989920"
---
# <a name="anti-spam-protection-in-eop"></a>EOP'de istenmeyen posta önleme koruması

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender)

> [!NOTE]
> Bu konu yöneticilere yöneliktir. Son kullanıcı konuları için bkz. Gereksiz [E-posta Filtresine Genel Bakış ve Gereksiz](https://support.microsoft.com/office/5ae3ea8e-cf41-4fa0-b02a-3b96e21de089) [e-posta ve kimlik avı hakkında bilgi alın](https://support.microsoft.com/office/86c1d76f-4d5a-4967-9647-35665dc17c31).

Microsoft 365 kutusu olmayan Exchange Online veya tek başına Exchange Online Protection (EOP) kuruluşlarına posta kutusu olan Exchange Online e-posta iletileri, EOP tarafından istenmeyen postalara (gereksiz e-posta) karşı otomatik olarak korunur.

Microsoft'un e-posta güvenliği yol haritası eşleşmeyen bir çapraz ürün yaklaşımı içerir. Kullanıcılara ağ genelinde en son istenmeyen posta önleme, kimlik avı önleme araçları ve yenilikleri sunmak için EOP istenmeyen posta önleme ve kimlik avı önleme teknolojileri e-posta platformlarımız genelinde uygulanır. EOP'nin amacı, kullanıcıları gereksiz e-posta, sahte e-posta tehditleri (kimlik avı) ve kötü amaçlı yazılımlara karşı algılamaya ve bu tehditlere karşı korumaya yardımcı olan kapsamlı ve kullanılabilir bir e-posta hizmeti sunmaktır.

E-posta kullanımı artya arttı olarak e-posta kullanımı da kötüye kullanımına neden olabilir. İstenmeyen gereksiz e-postalar gelen kutularına ve ağlara tıkar, kullanıcı memnuniyetini ve yasal e-posta iletişimlerinin etkililiğini etkiler. Microsoft bu nedenle istenmeyen posta önleme teknolojilerine yatırım yapmaya devam ediyor. Basitçe ifade gerekirse, başlangıç olarak gereksiz e-postaları içeren ve filtre uygulanmış bir e-posta var.

> [!TIP]
> aşağıdaki istenmeyen posta önleme teknolojileri, ileti zarfı (örneğin, gönderenin etki alanı veya iletinin kaynak IP adresi) temel alan iletilere izin vermek veya bu iletileri engellemek için kullanışlıdır. Yük tabanlı iletilere (örneğin, iletide veya ekli dosyalarda yer alan URL'ler) izin vermek veya iletileri engellemek için Kiracı İzin [Ver/Engelleme Listesi portalını kullansanız gerekir](tenant-allow-block-list.md).

## <a name="anti-spam-technologies-in-eop"></a>EOP'de istenmeyen posta önleme teknolojileri

Gereksiz e-postaları azaltmaya yardımcı olmak için, EOP yasal e-postaları tanımlamak ve bu e-postaları ayırmak için özel istenmeyen posta filtreleme teknolojilerini kullanan gereksiz e-posta koruması içerir. EOP istenmeyen posta filtrelemesi, bilinen istenmeyen postalardan, kimlik avı tehditlerinden ve kullanıcı geri bildirimlerinden, tüketici platformumuz Outlook.com'dan öğrenir. Gereksiz e-posta sınıflandırma programında EOP kullanıcılarından sürekli geri bildirim almak, EOP teknolojilerinin sürekli olarak eğitime alınarak iyileştirilmelerini sağlar.

EOP'de istenmeyen posta önleme ayarları aşağıdaki teknolojilerden kullanılır:

- Bağlantı **filtreleme**: IP İzin Listesi, IP Engelleme Listesi ve güvenli *liste (Microsoft* tarafından sürdürülen dinamik, ancak düzenlenilmeyen bir güvenilir gönderenler listesi) aracılığıyla, gelen e-posta bağlantısının başlarında iyi ve kötü e-posta kaynak sunucularını tanımlar. Bağlantı filtresi ilkesinde bu ayarları yapılandırabilirsiniz. Bağlantı filtrelemeyi [yapılandırma bağlantısı bağlantısında daha fazla bilgi edinebilirsiniz](configure-the-connection-filter-policy.md).

- **İstenmeyen** posta filtreleme (içerik filtreleme): EOP, iletileri sınıflandırmak için istenmeyen posta filtreleme kararlarını **İstenmeyen** **posta, Yüksek** güven istenmeyen **posta, Toplu** e-posta **, Kimlik** avı e-postası ve Yüksek güvene sahip kimlik avı e-postası kararlarını kullanır. Bu kararlara dayalı olarak eylemleri yapılandırabilirsiniz ve kullanıcıların karantinaya alınmış iletilerde neler yapmalarına izin verilmiyor ve kullanıcı karantina ilkeleri kullanılarak karantina bildirimlerinin alınıp [alınamay ayarlarını yapılandırabilirsiniz](quarantine-policies.md). Daha fazla bilgi için bkz[. Microsoft 365'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

  > [!NOTE]
  > Varsayılan olarak, istenmeyen posta filtreleme alıcının Gereksiz E-posta klasörüne istenmeyen posta olarak işaretlenmiş iletileri gönderecek şekilde yapılandırılır. Bununla birlikte, EOP'nin şirket içi Exchange posta kutularını korumaya sahip olduğu karma ortamlarda, iletilere eklenen EOP istenmeyen posta üst bilgilerini tanımak için şirket içi Exchange kuruluş içinde iki posta akış kuralı (aktarım kuralları olarak da bilinir) yapılandırmanız gerekir. Ayrıntılar için bkz. [EOP'yi karma ortamlarda gereksiz E-posta klasörüne istenmeyen posta teslim edecek şekilde yapılandırma](/exchange/standalone-eop/configure-eop-spam-protection-hybrid).

- **Giden istenmeyen posta filtreleme**: EOP ayrıca, kullanıcılarının giden ileti içeriğine veya giden ileti sınırlarını aşarak istenmeyen posta göndermeymeyeceklerinden emin olmak için de denetler. Daha fazla bilgi için, [bu bağlantıda giden istenmeyen posta filtrelemesini Microsoft 365](configure-the-outbound-spam-policy.md).

- **Spoof Intelligence**: Daha fazla bilgi için bkz [. EOP'de anti-poing protection](anti-spoofing-protection.md).

## <a name="manage-errors-in-spam-filtering"></a>İstenmeyen posta filtreleme hatalarını yönetme

İyi iletiler istenmeyen posta olarak (hatalı pozitif sonuçlar olarak da bilinir) veya istenmeyen postaların Gelen Kutusu'na teslim edilebiliyor olması (hatalı negatifler olarak da bilinir) mümkündür. Ne olduğunu bulmak ve gelecekte bunun önlenmesine yardımcı olmak için aşağıdaki bölümlerdeki önerileri kullanabilirsiniz.

her iki senaryo için de geçerli olan bazı en iyi yöntemler:

- Her zaman, sınıflandırılmamış iletileri Microsoft'a bildir. Daha fazla bilgi için bkz [. İletileri ve dosyaları Microsoft'a bildirme](report-junk-email-messages-to-microsoft.md).

- **İstenmeyen posta önleme ileti** üst bilgilerini inceleme: Bu değerler, bir iletinin neden istenmeyen posta olarak işaretlendiğinden veya istenmeyen posta filtrelemesini neden atladİklerini size söyler. Daha fazla bilgi için bkz [. İstenmeyen posta iletisi üstbilgileri](anti-spam-message-headers.md).

- **MX kaydınızı şu adrese Microsoft 365**: EOP'nin en iyi korumayı sağlayması için, her zaman e-postanın önce E-postayı teslim Microsoft 365 öneririz. Yönergeler için bkz[. Etki alanı için herhangi bir DNS barındırma sağlayıcısında DNS Microsoft 365](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

  MX kaydı başka bir konuma (örneğin, üçüncü taraf istenmeyen posta önleme çözümü veya cihaz) işaret ediyorsa, EOP'nin doğru istenmeyen posta filtrelemesi sağlamak zordur. Bu senaryoda, bağlayıcılar için Geliştirilmiş Filtreleme'yi yapılandırmaniz gerekir (liste atlama _olarak da bilinir_). Yönergeler için bkz. [Exchange Online'ta Bağlayıcılar için İyileştirilmiş Filtreleme](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

- **E-posta kimlik** doğrulamasını kullanma: Bir e-posta etki alanınız varsa, bu etki alanındaki gönderenlerden gelen iletilerin yasal olduğunu doğrulamasına yardımcı olmak için DNS'i kullanabilirsiniz. EOP'de istenmeyen posta ve istenmeyen kimlik doğrulamasını önlemeye yardımcı olmak için, aşağıdaki e-posta kimlik doğrulama yöntemlerinin hepsini kullanın:

  - **SPF**: Sender Policy Framework, iletinin kaynak IP adresini gönderen etki alanının sahibiyle karşı doğrular. SPF'ye hızlı bir giriş yapmak ve SPF'yi hızla yapılandırmak için bkz Kimlik kimliklerini önlemeye yardımcı olmak için [SPF'yi ayarlama](set-up-spf-in-office-365-to-help-prevent-spoofing.md). Microsoft 365'un SPF'yi nasıl kullandığı hakkında daha ayrıntılı bilgi için veya sorun gidermek ya da karma dağıtımlar gibi standart olmayan dağıtımlarda, Microsoft 365, spoing'yi engellemek için [Sender Policy Framework'i (SPF)](how-office-365-uses-spf-to-prevent-spoofing.md) nasıl kullanır? ile başlayabilirsiniz.

  - **DKIM**: DomainKeys Tanımlanan Posta, etki alanınız üzerinden gönderilen iletilerin ileti üst bilginize dijital bir imza ekler. Bilgi için bkz. [Belirli bir yıl içinde özel etki alanınıza gönderilen giden e-postayı doğrulamak için DKIM Microsoft 365](use-dkim-to-validate-outbound-email.md).

  - **DMARC**: Etki alanı tabanlı İleti Kimlik Doğrulaması, Raporlama ve Uyumluluk, hedef e-posta sistemlerinin SPF veya DKIM'nin başarısız olan iletilerle ne yapacaklarını belirlemesine yardımcı olur ve e-posta iş ortaklarınız için başka bir güven düzeyi sağlar. Daha fazla bilgi için bkz[. DMARC kullanarak e-postayı doğrulamak için Microsoft 365](use-dmarc-to-validate-email.md).

- **Toplu e-posta** ayarlarınızı doğrulama: İstenmeyen posta önleme ilkelerde yapılandırılan toplu şikayet düzeyi (BCL) eşiği, toplu e-postanın (gri _posta olarak da_ bilinir) istenmeyen posta olarak işaret isteyip olmadığını belirler. Varsayılan olarak açık olan _PowerShell ayarı MarkAsSpamBulkMail_ de sonuçlara katkıda bulunmak için kullanılır. Daha fazla bilgi için bkz[. Microsoft 365'de istenmeyen posta önleme ilkelerini yapılandırma](configure-your-spam-filter-policies.md).

### <a name="prevent-the-delivery-of-spam-to-the-inbox"></a>İstenmeyen postanın Gelen Kutusu'na teslimsini engelleme

- **Kuruluş ayarlarınızı doğrulama**: İletilerin istenmeyen posta filtresini atlayıp atlamalarına izin verecek ayarlara dikkat edin (örneğin, istenmeyen posta önleme ilkelerde izin verilen etki alanları listesine kendi etki alanınızı eklersiniz). Önerilen ayarlarımız için bkz. [EOP ve Microsoft Defender için önerilen güvenlik Office 365 ve](recommended-settings-for-eop-and-office365.md) [Güvenilir gönderen listeleri oluşturma](create-safe-sender-lists-in-office-365.md).

- **Kullanılabilir engellenen gönderen listelerini kullanma: Bilgi** için bkz. [Engellenen gönderen listeleri oluşturma](create-block-sender-lists-in-office-365.md).

- **Toplu e-posta aboneliğinden çıkma** İleti kullanıcının kayıt olduğu bir ileti ise (bültenler, ürün duyuruları, vb.) ve güvenilir bir kaynaktan abonelikten çıkma bağlantısı içeriyorsa, bu kişiden aboneliğinizi iptal istemeyi düşünün.

- **Tek başına EOP: EOP** istenmeyen posta filtreleme kararları için şirket içi Exchange'te posta akış kuralları oluşturma: EOP'nin şirket içi Exchange posta kutularını koruma olduğu karma ortamlarda, şirket içi posta hizmetlerde posta akış kurallarını (aktarım kuralları olarak da bilinir) yapılandırmanız Exchange. Bu posta akış kuralları EOP istenmeyen posta filtreleme kararını çevirerek, posta kutusunda gereksiz e-posta kuralının iletiyi Gereksiz E-posta klasörüne taşımasini sağlar. Ayrıntılar için bkz. [EOP'yi karma ortamlarda gereksiz E-posta klasörüne istenmeyen posta teslim edecek şekilde yapılandırma](/exchange/standalone-eop/configure-eop-spam-protection-hybrid).

### <a name="prevent-good-email-from-being-identified-as-spam"></a>İyi bir e-postanın istenmeyen posta olarak tanımlarını önleme

İşte hatalı pozitif sonuçlardan önlemeye yardımcı olmak için atılacak bazı adımlar:

- **Kullanıcının gereksiz E-posta Outlook ayarlarını doğrulayın**:

  - Outlook Gereksiz E-posta Filtresi'nin devre dışı bırakılmıştır **: Outlook** Gereksiz E-posta Filtresi varsayılan değere ayarlanmışsa **Otomatik filtreleme** yok değerine ayarlanırsa, Outlook iletileri istenmeyen posta olarak sınıflandırmaya çalışmaz.  Düşük veya Yüksek olarak ayar yukarıya **geldiğinde, Outlook** Gereksiz E-posta Filtresi istenmeyen postaları tanımlamak ve Gereksiz E-posta klasörüne taşımak için kendi SmartScreen filtre teknolojisini kullanır, böylece hatalı pozitif sonuçlar elde edersiniz. Microsoft'un, 2016'nın Kasım ayında Exchange ve Outlook için istenmeyen posta tanımlama güncelleştirmelerini üretmeyi durdurmuş olduğunu unutmayın. Mevcut SmartScreen istenmeyen posta tanımları olduğu gibi kaldı, ancak bunların etkisinin zaman içinde düşük olması olasıdır.

  - **Outlook 'Kasa Listeleri'** ayarının devre dışı bırakılmıştır: Bu ayar etkinleştirildiğinde, yalnızca kullanıcının Kasa Gönderenler listesinde veya Kasa Alıcıları listesinden gelen iletiler Gelen Kutusu'na teslim edilir; diğer herkesten gelen e-postalar otomatik olarak Gereksiz E-posta klasörüne taşınır.

  Bu ayarlar hakkında daha fazla bilgi için bkz. [E-posta veya posta Exchange Online gereksiz e-posta Microsoft 365](configure-junk-email-settings-on-exo-mailboxes.md).

- **Kullanılabilir güvenilir gönderenler listelerini kullanma**: Bilgi için bkz. [Güvenilir gönderen listeleri oluşturma](create-safe-sender-lists-in-office-365.md).

- **Kullanıcıların, aşağıdaki hizmet açıklamasında açıklanan gönderme** ve alma [sınırları içinde](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#receiving-and-sending-limits) Exchange Online doğrulayın.

- **Tek başına EOP:** Dizin eşitlemesini kullanma: Şirket içi veya kuruluş içi ayarlarınızı korumaya yardımcı olması için tek başına E Exchange OP kullanıyorsanız, dizin eşitlemesini kullanarak kullanıcı ayarlarını hizmetle eşitlemeniz gerekir. Bunu yaparak kullanıcılarının Gönderenler listelerinin Kasa EOP tarafından kabul edildiklerine emin olur. Daha fazla bilgi için bkz [. Posta kullanıcılarını yönetmek için dizin eşitlemeyi kullanma](/exchange/standalone-eop/manage-mail-users-in-eop#synchronize-directories-with-azure-active-directory-connect-aad-connect).

## <a name="anti-spam-legislation"></a>İstenmeyen posta önleme yasaları

Microsoft'ta, yeni teknolojilerin ve otomatik düzenlemenin geliştirilmesinin, etkili bir kamu politikası ve yasal çerçeveleri desteği gerektirdiğine inanıyoruz. Dünya çapındaki istenmeyen postaların yayılması, ticari e-postaları düzenlemek için sayısız yasal gövdeye sahip. Birçok ülkede artık istenmeyen postayla mücadele yasaları vardır. ABD'de istenmeyen posta konusunda hem federal hem de eyalet yasaları vardır ve bu tamamlayıcı yaklaşım istenmeyen postaları frenlerken yasal e-ticarete de yardımcı oluyor. CAN-SPAM Yasası, sahte ve yanıltıcı e-posta iletilerini frenleyecek araçları genişlettir.
