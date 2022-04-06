---
title: Veri kaynağında belge meta Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Bu makalede, Microsoft 365'te bir gözden geçirme kümesinde yer alan Advanced eDiscovery meta veri alanlarını tanımlar.
ms.openlocfilehash: e07afbcfff0c6cae748ac6104879ec25f046cbf5
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680741"
---
# <a name="document-metadata-fields-in-advanced-ediscovery"></a>Veri kaynağında belge meta Advanced eDiscovery

Aşağıdaki tabloda, çalışma sayfalarındaki bir gözden geçirme kümesinde yer alan belgelerin meta veri alanları Advanced eDiscovery. Tablo aşağıdaki bilgileri sağlar:

- **Alan adı** **ve Görüntüleme alanı adı:** Meta veri alanı adı ve gözden geçirme kümesinde seçili belgenin dosya meta verilerini görüntülerken görüntülenen alanın adı. Belgenin dosya meta verilerini görüntülerken bazı meta veri alanları dahil değildir. Bu alanlar yıldız (*) ile vurgulanır.

- **Aranabilir alan adı:** Gözden geçirme kümesi sorgusu çalıştırmaya yönelik olarak arayabilirsiniz [özelliğin adı](review-set-search.md). Boş hücre, alanı gözden geçirme kümesi sorgusunda arayamazsınız anlamına gelir.

- **Alan adı dışarı aktarıldı:** Belgeler dışarı aktarıldıken dahil edilen meta veri alanı adı.  Boş hücre, alanın dışarı aktarıldı olan meta verilere dahil olmadığını anlamına gelir.

- **Açıklama:** Meta veri alanı açıklaması.

> [!NOTE]
> Gözden **geçirme kümesi** aramalarında [Anahtar Sözcükler alanı Anahtar](./review-set-search.md) Sözcük Sorgu Dili (KQL) kullanır. Aranabilir alan adı sütununda  listelenen alanlar, sorgu oluşturucusunu kullanmak zorunda kalmadan  karmaşık sorgular oluşturmak için gözden geçirme kümesi aramalarının Anahtar Sözcükler alanında kullanılabilir. KQL hakkında daha fazla bilgi için bkz. [Anahtar Sözcük Sorgusu Dili söz dizimi başvurusu](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference).

<br>

****

|Alan adı ve Görünen alan adı|Aranabilir alan adı|Alan adı dışarı aktarıldı|Açıklama|
|---|---|---|---|
|Ek İçerik Kimliği|AttachmentContentId||Ek içeriği Öğenin kimliği.|
|Avukat müşterisi ayrıcalık puanı|AttorneyClientPrivilegeScore||Avukat-istemci ayrıcalık modeli içerik puanı.|
|Yazar|Yazar|Doc_authors|Belge meta verilerinden yazar.|
|Gizli|Gizli|Email_bcc|İleti türleri için Gizli alanı. Biçim, **DisplayName 'tir \<SMTPAddress\>**.|
|BILGI|Bilgi|Email_cc|İleti türleri için Bilgi alanı. Biçim, **DisplayName 'tir \<SMTPAddress\>**.|
|Uyumluluk etiketleri|ComplianceLabels|Compliance_labels|[E-Office 365'de](retention.md) içeriğe uygulanmış bekletme Office 365.|
|Bileşik Yolu|CompoundPath|Compound_path|Öğenin kaynağını açıklayan, insanlar tarafından okunabilir yol.|
|İçerik*|İçerik||Öğenin metni ayıklandı.|
|Konuşma Gövdesi|Conversation Bire Bir||Öğenin konuşma gövdesi.|
|Konuşma Kimliği|ConversationId|Conversation_ID|İletiden Konuşma Kimliği. Bire Teams grup sohbetleri yapmak için tüm döküm dosyaları ve aynı konuşma içindeki aile öğeleri aynı Konuşma Kimliğini paylaşır. Daha fazla bilgi için bkz[. Advanced eDiscovery içeriği için iş akışını Microsoft Teams](teams-workflow-in-advanced-ediscovery.md).|
|Konuşma Ailesi Kimliği|ConversationFamilyID|ConversationFamilyID|Bir konuşmanın hem bağımsız öğelerini hem de konuşmadaki ilgili öğeleri tanımlayan kimlik.|
|Konuşma Dizini||Conversation_index|İletiden konuşma dizini.|
|Konuşma Adı||ConversationName|Bu alan içerik türüne bağlıdır.<br>**Teams:1 sohbeti seçin:** İlk iletinin ilk 40 karakteri.<br>**Teams:N sohbeti:** Grup sohbeti adı; kullanılamıyorsa ilk iletinin ilk 40 karakteri.<br>**Teams Gönderisi:** Başlık veya duyuru alt başlığı gönderin; yoksa, ilk iletinin ilk 40 karakteri.|
|Konuşma Pdf Süresi|ConversationPdfTime||Konuşmanın PDF sürümünün oluşturulma tarihi.|
|Konuşma Redaction Yazma Süresi|ConversationRedactionBurnTime||Sohbet için konuşmanın PDF sürümünün oluşturulma tarihi.|
|Konuşma Konusu|ConversationTopic||Öğenin konuşma konusu.|
|Konuşma Türü|ConversationType|ConversationType|Sohbet görüşme türü. Değerler: <br>**Teams bire bir sohbetler ve grup sohbetleri ve tüm Yammer konuşmalar: Grup**<br>**Teams kanalları ve özel kanallar:** Kanal|
|Silinmiş İletiyi Içerir|containsDeletedMessage|containsDeletedMessage|Sohbet döküm metninde silinen bir iletinin olup olduğunu gösterir|
|Düzenlenen İletiyi Içerir|containsEditedMessage|containsEditedMessage|Sohbet döküm metninde düzenlenmiş bir ileti olup olduğunu gösterir|
|Teams Duyuru Başlığı|TeamsAnnouncementTitle|TeamsAnnouncementTitle|Ekip duyurus [unvanları](https://support.microsoft.com/office/send-an-announcement-to-a-channel-8f244ea6-235a-4dcc-9143-9c5b801b4992).|
|||Converted_file_path|Dönüştürülmüş dışarı aktarma dosyasının yolu. Yalnızca Microsoft iç kullanımları için.|
|Custo bire bir|Custo bire bir|Custo bire bir|Öğenin ilişkilendirilen koruyucu adı.|
|Tarih|Tarih|Tarih|Tarih, dosya türüne bağlı olan hesaplanan alandır.<p>**E-posta**: Gönderilme tarihi<br>**E-posta ekleri**: Belgenin son değiştirilme tarihi; uygun değilse ebeveynin gönderme tarihi<br>**Eklenmiş belgeler**: Belgenin son değiştirilme tarihi; kullanılamıyorsa, ebeveynin son değiştirme tarihi<br>**SPO belgeleri (modern ekleri içerir)**: Belgenin son değiştirilme tarihi; kullanılamıyorsa son SharePoint tarihine göre<br>**Belge Office 365:** Son değiştirme tarihi<br>**Toplantılar**: Toplantı başlangıç tarihi<br>**Sesli Mesaj**: Gönderilme tarihi<br>**IM**: Gönderilme tarihi<br>**Teams**: Gönderme tarihi|
|Belge yorumları|DocComments|Doc_comments|Belge meta verilerinden açıklamalar.|
|Belge şirketi||Doc_company|Belge meta verilerinden şirket.|
|Oluşturulan belge tarihi|CreatedTime|Doc_date_created|Belge meta verilerinden tarih oluşturma.|
|DocIndex*|||Aile dizininde. **-1** veya **0** , kök anlamına gelir.|
|Belge anahtar sözcükleri||Doc_keywords|Belge meta verilerinden anahtar sözcükler.|
|Değiştiren belge||Doc_modified_by|Belge meta verilerinden belgeyi son değiştiren kullanıcı.|
|Belge düzeltmesi|Doc_Version|Doc_Version|Belge meta verilerinden düzeltme.|
|Belge konusu||Doc_subject|Belge meta verilerinden konu.|
|Belge şablonu||Doc_template|Belge meta verilerinden şablon.|
|DocLastSavedBy||Doc_last_saved_by|Belgeyi en son kaydeden kullanıcının adı.|
|Baskın tema|BaskınTheme|Dominant_theme|Analizler için hesaplanan olarak baskın tema.|
|Yinelenen alt küme||Duplicate_subset|Tam yinelenenler için grup kimliği.|
|EmailAction*||Email_action|Değerler **Yok,** **Yanıtla veya** **ilet'tir**; iletiyi konu satırına göre sıralar.|
|E-posta Teslim Bilgisi İsteği||Email_delivery_receipt|Teslim bilgisi için Internet Üst Bilgileri'ne sağlanan e-posta adresi.|
|Önem|EmailImportance|Email_importance|İletinin önem: **0** - Düşük; **1** - Normal; **2** - Yüksek|
|Yoksayılan işleme hataları|ErrorIgnored|Error_Ignored|Hata yoksayıldı ve düzeltimedi.|
|EmailInternetHeaders|EmailInternetHeaders|Email_internet_headers|E-posta iletisinden tam e-posta üst bilgileri kümesi|
|EmailLevel*||Email_level|Bir iletinin ait olduğu e-posta ileti dizi içindeki düzeyini gösterir; ekler, üst iletinin değerini devralır.|
|E-posta İleti Kimliği||Email_message_ID|İletinin Internet iletisi kimliği.|
|EmailReadReceiptRequested||Email_read_receipt|Okundu bilgisi için Internet Üst Bilgileri'ne sağlanan e-posta adresi.|
|E-posta Güvenliği|EmailSecurity|Email_security|İletinin güvenlik ayarı: **0** - Yok; **1** - İmzalı; **2** - Şifreli; **3** - Şifreli ve imzalanmış.|
|E-posta Duyarlılığı|EmailSensitivity|email_sensitivity|İletinin Duyarlılık ayarı: **0** - Yok; **1 Bireysel** ; **2** - Özel; **3** - ŞirketFiyat.|
|E-posta kümesi|EmailSet|Email_set|Aynı e-posta kümesinde yer alan tüm iletiler için grup kimliği.|
|EmailThread*||Email_thread|İletinin e-posta kümesi içindeki konumu; kökten geçerli iletiye kadar düğüm kimliklerinden oluşur ve noktalarla (.) ayrılır.|
|||Export_native_path|Dışarı aktarıldı dosyanın yolu.|
|Ayıklanan içerik türü||Native_type|Mime türü şeklinde ayıklanan içerik türü; örneğin, **image/jpeg**|
|||Extracted_text_path|Dışarı aktarmada ayıklanan metin dosyasının yolu.|
|ExtractedTextLength*||Extracted_text_length|Ayıklanan metindeki karakter sayısı.|
|FamilyDuplicateSet*||Family_duplicate_set|Birbirinin tam yinelemesi olan aileler için sayısal tanımlayıcı (aynı içerik ve aynı eklerin hepsi).|
|Aile Kimliği|FamilyId|Family_ID|Üst öğesiyle e-posta ve sohbetlerden ekleri ve ayıklanan öğeleri birlikte gruplara ekler. Bu, sohbeti veya e-postayı, tüm ekleri ve ayıklanan öğeleri içerir.|
|Aile Boyutu||Family_size|Ailede belge sayısı.|
|Dosya sınıfı|FileClass|File_class|İçerik türü ve SharePoint için OneDrive: **Belge**. <br>E-postanın içeriği Exchange: **E-posta** veya **Ek**. <br>konuşmalar veya Teams içerik Yammer: **Konuşmalar**.|
|Dosya Kimliği|FileId|File_ID|Olay içindeki benzersiz belge tanımlayıcısı.|
|Oluşturulan dosya sistemi tarihi||File_system_date_created|Dosya sisteminden oluşturulma tarihi (yalnızca veriye sahip olmayan Office 365 geçerlidir).|
|Dosya sistemi tarihi değiştirildi||File_system_date_modified|Dosya sisteminden değiştirme tarihi (yalnızca veriye sahip olmayan Office 365 geçerlidir).|
|Dosya Türü|FileType||Dosya uzantısına göre öğenin dosya türü.|
|Grup Kimliği|GroupId|Group_ID|E-posta ve belgeler için tüm öğeleri birlikte gruplara alın. E-posta için, iletiyle tüm ekleri ve ayıklanan öğeleri içerir. Belgelerde, belge ve ekli öğeler bu belgeye dahildir.|
|Eki var|EmailHasAttachment|Email_has_attachment|İletinin ekleri olup olmadığını gösterir.|
|Avukat var|HasAttorney||**Avukat** listesinde katılımcılardan en az biri bulunurken doğru; aksi takdirde değer **Yanlış olur**.|
|HasText*||Has_text|Öğenin metni olup olmadığını gösterir; olası değerler Doğru **ve** **Yanlış'tır**.|
|Değişmez Kimlik||Immutable_ID|Bu Kimlik, gözden geçirme kümesi içindeki bir belgeyi benzersiz bir şekilde tanımlamak için kullanılır. Bu alan gözden geçirme kümesi aramalarında kullanılamaz ve Belgeye yerel bulunduğu konumdan erişmek için Kimlik kullanılamaz.|
|Kapsayıcı tür|InclusiveType|Inclusive_type|Çözümleme için hesaplanan kapsayıcı tür: **0** - dahil değildir; **1** - dahil; **2** - dahil eksi; **3** - dahil kopya.|
|Yanıtla kimliğinde||In_reply_to_ID|İletiden Kimlik yanıtı olarak.|
|InputFileExtension||Original_file_extension|Dosyanın özgün dosya uzantısı.|
|InputFileID||Input_file_ID|Gözden geçirme kümesinde en üst düzey öğenin dosya kimliği. Ek için, bu kimlik ebeveynin kimliği olur. Bu, aileleri birlikte grupla birlikte grupla için kullanılabilir.|
|Modern ek|IsModernAttachment||Bu dosya modern bir ek veya bağlantılı dosyadır.|
|Belge sürümünden|IsFromDocumentVersion||Geçerli belge, başka bir belgenin farklı bir sürümünden farklıdır.|
|E-posta ekidir|IsEmailAttachment||Bu öğe, iletiye eklenmiş bir öğe olarak gösteren bir e-posta eklerindendir.|
|Satır içi ek|IsInlineAttachment||Bu satır içi eklidir ve iletinin gövdesinde gösterir.|
|Is Representative|IsRepresentative|Is_representative|Her bir tam yinelenenler kümesinde bir belge temsili olarak işaretlenir.|
|Öğe sınıfı|ItemClass|Item_class|Exchange sunucusu tarafından sağlanan öğe sınıfı; örneğin, **IPM. Not**|
|Son değiştirme tarihi|LastModifiedDate|Doc_date_modified|Belge meta verilerinden son değiştirme tarihi.|
|Yükleme Kimliği|LoadId|Load_ID|Öğenin gözden geçirme kümesine ekli olduğu yükleme kümesi kimliği.|
|Konum|Konum|Konum|Belgelerin kaynak olarak kaynak bulunduğu konumun türünü gösteren dize.<p>**Alınan Veriler** - Veri Office 365 değil<br>**Teams** - Microsoft Teams<br>**Exchange** - Exchange kutularının izinlerini alın<br>**SharePoint** - SharePoint siteleri<br>**OneDrive** - OneDrive hesapları|
|Konum adı|LocationName|Location_name|Öğenin kaynağını tanımlayan dize. Exchange için bu, posta kutusunun SMTP adresidir; site SharePoint ve OneDrive için, site koleksiyonunun URL'si.|
|||Marked_as_pivot|Bu dosya, yakın çoğaltılmış bir kümenin özet dosyasıdır.|
|Temsili olarak işaretlenmiş|MarkAsRepresentative||Her bir yineleme kümesinden bir belge temsilci olarak işaretlenir.|
|Toplantı Bitiş Tarihi|MeetingEndDate|Meeting_end_date|Toplantılar için toplantı bitiş tarihi.|
|Toplantı Başlangıç Tarihi|MeetingStartDate|Meeting_start_date|Toplantılar için toplantı başlangıç tarihi.|
|İletinin tür|MessageKind|Message_kind|Aranan iletinin türü. Olası değerler: **<p><br><br><br>kişiler belgeleri e-posta dış veri <br><br>faksları im <br><br><br>günlüklerini toplantı microsoftteams** (Microsoft Teams'ta sohbetlerden, toplantılardan ve aramalardan öğe döndürür) **<br><br><br>notlar gönderileri rssfeeds <br>görevleri <br>sesli** mesaj|
|Modern ekin üst kimliği||ModernAttachment_ParentId|Belgenin üst öğesi değişmez Kimliği.|
|Yerel Uzantı|NativeExtension|Native_extension|Öğenin yerel uzantısı.|
|Yerel dosya adı|NativeFileName|Native_file_name|Öğenin yerel dosya adı.|
|NativeMD5||Native_MD5|Dosya akışının MD5 karması (128 bit karma değeri).|
|NativeSHA256||Native_SHA_256|Dosya akışının SHA256 karması (256 bit karma değeri).|
|ND/ET Sıralama: Ekleri dışlama|NdEtSortExclAttach|ND_ET_sort_excl_attach|E-posta iş parçacığı (ET) kümesiyle Yakın yineleme (ND) kümesi bir concatenation. Bu alan, gözden geçirme zamanında verimli bir sıralama için kullanılır. ND **kümelerine** D, ET kümelerine **ise E** ekleri ekleri vardır.|
|ND/ET Sıralama: Ekleri dahil et|NdEtSortInclAttach|ND_ET_sort_incl_attach|E-posta iş parçacığı (ET) kümesiyle yakın yinelemeli (ND) kümeyi birlaştırma. Bu alan, gözden geçirme zamanında verimli bir sıralama için kullanılır. ND **kümelerine** D, ET kümelerine **ise E** ekleri ekleri vardır. Et kümesinde her e-posta öğesi, onu izleyen uygun ekleri görüntüler.|
|Yinelenen Küme'nin yakınında||ND_set|Özet belgeye benzeyen öğeler aynı belgeyi ND_set.|
|O365 yazarları||O365_authors|Yazar: SharePoint.|
|Oluşturan O365||O365_created_by|Oluşturan: SharePoint.|
|O365 oluşturulma tarihi||O365_date_created|Bir tarihten itibaren SharePoint.|
|O365ModifiedDate||O365_date_modified|Yeni belge veya dosyadan toplanan belgenin (veya SharePoint OneDrive İş tarihi. Bu, kullanıcı deneyiminde ve önceki sürüm geçmişinde görüntülenenle SharePoint OneDrive tarihidir.|
|Değiştiren O365||O365_modified_by|Siteden veya SharePoint tarafından OneDrive.|
|Diğer koruyucular|DedupedCustoozs|Deduped_custodians|Tam yinelenen (e-posta için, içeriğe dayalı olarak; karmaya dayalı belgeler için) belgelerin koruyucuları listesi.|
|Diğer dosya kimlikleri|DedupedFileIds|Deduped_file_IDs|Tam yinelenen belgelerin (içeriğe dayalı e-posta için; belgeler için karmaya dayalı) dosya kimliklerinin listesi.|
|Diğer yollar|Dedupedcompoundpath|Deduped_compound_path|Tam yinelenen belgelerin bileşik yollarının listesi (e-posta: içeriğe dayalı, belgeler: karmaya dayalı).|
|Üst Kimlik|ParentId|Parent_ID|Öğenin üst öğesinin kimliği.|
|ParentNode||Parent_node|E-posta ileti dizisinde önceki en yakın e-posta iletisi.|
|Katılımcı etki alanları|ParticipantDomains|Email_participant_domains|bir iletinin tüm katılımcıların etki alanlarının listesi.|
|Katılımcılar|Katılımcılar|Email_participants|İletinin tüm katılımcılarının listesi; örneğin, Gönderen, Son, Bilgi, Gizli.|
|Özet Kimlik|PivotId|Pivot_ID|Özet kimliği.|
|Ayrıca olma olasılığı|PotentiallyPrivileged|Potentially_privileged|Avukat-istemci ayrıcalık algılama modeli belgenin ayrıcalıklı olma olasılığı varsa doğru|
|İşleme durumu|ProcessingStatus|Error_code|Öğe gözden geçirme kümesine eklendikten sonra işleniyor.|
|Yüzdebirlik okuma|ReadPercentile||Belge için ilgi derecelerine göre yüzdebirlik okuma.|
|Alındı|Alındı|Email_date_received|E-postanın UTC'de alındığı tarih ve saat.|
|Alıcı Sayısı||Recipient_count|İletinin alıcı sayısı.|
|Alıcı etki alanları|RecipientDomains|Email_recipient_domains|İletinin tüm alıcıları etki alanlarının listesi.|
|Alıcılar|Alıcılar|Email_recipients|İletinin tüm alıcıları listesi (To, Bilgi, Gizli).|
|||Redacted_file_path|Dışarı aktarmada kırmızı işlemli değiştirme dosyasının yolu.|
|||Redacted_text_path|Dışarı aktarmada yerini alan tam metin dosyasının yolu. Yalnızca Microsoft iç kullanımları için.|
|İlgi Durumu etiketi Büyük/Harf Sorunu 1||Relevance_tag_case_issue_1|İlgi Düzeyi etiketi Büyük/Harf Sorunu, İlgi Düzeyi'ne göre 1.|
|İlgi puanı|İlgi Puanı||Bir belgenin Ilgi Düzeyi'ne dayalı ilgi düzeyi puanı.|
|İlgi Düzeyi etiketi|relevanceTag||Bir belgenin Ilgi Düzeyi'ne dayalı ilgi düzeyi puanı.|
|Temsili Kimlik|RepresentativeId||Her bir tam yineleme kümesi için sayısal tanımlayıcı.|
|||Row_number|Yükleme dosyasındaki öğenin satır numarası.|
|Gönderen|Gönderen|Email_sender|İleti türleri için Gönderen (Gönderen) alanı. Biçim, **DisplayName 'tir \<SmtpAddress>**.|
|Gönderen/Yazar|SenderAuthor||Öğenin gönderen veya yazarına özel hesaplanan alan.|
|Gönderen etki alanı|SenderDomain|Email_sender_domain|Gönderenin etki alanı.|
|Gönderildi|Gönderildi|Email_date_sent|İletinin gönderilme tarihi.<br>Sohbetler: Dökümden başlangıç tarihi|
|Sıra ayarla: Önce Dahil|SetOrderInclusivesFirst|Set_order_inclusives_first|Sıralama alanı - e-posta ve ekler: kronolojik sıra; belgeler: önce azalan benzerlik puanına göre özetler.|
|Kimlik Ayarla||Set_ID|Aynı e-posta dizisinde (ND_set) veya e-postaya benzeyen belgeler (Email_set) aynı içeriği Set_ID.|
|SimilarityPercent||Similarity_percent|Bir belgenin yakın yineleme kümesi özet durumuna ne kadar benzer olduğunu gösterir.|
|Yerel dosya boyutu|Boyut|Native_size|Yerel öğenin bayt sayısı.|
|Konu|Konu|Email_subject|İletinin konusu.|
|Konu/Başlık|SubjectTitle||Öğenin konusu veya başlığıyla ilgili hesaplanan alan.|
|Etiketler|Etiketler|Etiketler|Gözden geçirme kümesine uygulanan etiketler.|
|Kanal Adı|Kanal|ChannelName|Bu, Teams adıdır. Yalnızca belirli bir Microsoft Teams geçerlidir.|
|Ekip Adı|TeamName|TeamName|**Teams:** Ekibin adı<br>**Yammer:** Community ad|
|Temalar listesi|TemalarListesi|Themes_list|Analizler için hesaplanan temalar listesi.|
|Başlık|Başlık|Doc_title|Belge meta verilerinden başlık. Belge meta verilerinden başlık. Konuşma Teams Yammer konuşmalar için, KonuşmaAdı özelliğinden gelen değerdir.|
|Hedef|Hedef|Email_to|İleti türlerine göre To alanı. Biçim **DisplayName\<SmtpAddress>**|
|E-posta kümesinde benzersiz|UniqueInEmailSet||**E-posta** kümesinde ekin yinelenen bir kopyası varsa False.|
|Sürüm Grup Kimliği||Version_Group_Id|Aynı belgenin farklı sürümlerini birlikte grup sağlar.|
|SürümSayı||Version_Number|Belge kitaplığından veya dosyadan toplanan SharePoint sürüm OneDrive İş. Bu, kullanıcı deneyiminde ve önceki sürüm geçmişinde görüntülenen sürümle SharePoint OneDrive olur.|
|Düzeltildi|WasRemediated|Was_Remediated|**Öğe** düzeltildi ise Doğru, aksi **takdirde Yanlış**.|
|Sözcük sayısı|WordCount|Word_count|Öğenin sözcük sayısı.|
|||||

> [!NOTE]
> Bir olay için veri toplarken Office 365 konumlarında arama yapmak için aranabilir özellikler hakkında daha fazla bilgi Advanced eDiscovery bkz. İçerik Arama için Anahtar sözcük sorguları ve arama [koşulları](keyword-queries-and-search-conditions.md).
