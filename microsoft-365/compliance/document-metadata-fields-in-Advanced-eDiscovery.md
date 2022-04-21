---
title: eBulma'da belge meta veri alanları (Premium)
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
description: Bu makale, Microsoft 365'de Microsoft Purview eKeşif (Premium) örneğinde bir inceleme kümesindeki belgelerin meta veri alanlarını tanımlar.
ms.openlocfilehash: 4e1efbf48cf4313682095b69eb97f52d00b9ceaf
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "65001114"
---
# <a name="document-metadata-fields-in-ediscovery-premium"></a>eBulma'da belge meta veri alanları (Premium)

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Aşağıdaki tabloda, Microsoft Purview eKeşif'te (Premium) bir servis talebi için bir inceleme kümesindeki belgelerin meta veri alanları listelenir. Tabloda aşağıdaki bilgiler sağlanır:

- **Alan adı** ve **Görünen alan adı:** Meta veri alanının adı ve seçili belgenin dosya meta verilerini gözden geçirme kümesinde görüntülerken görüntülenen alanın adı. Belgenin dosya meta verileri görüntülenirken bazı meta veri alanları dahil değildir. Bu alanlar yıldız (*) ile vurgulanır.

- **Aranabilir alan adı:** [Gözden geçirme kümesi sorgusunu](review-set-search.md) çalıştırırken arayabileceğiniz özelliğin adı. Boş hücre, bir gözden geçirme kümesi sorgusunda alanı arayabileceğiniz anlamına gelir.

- **Dışarı aktarılan alan adı:** Belgeler dışarı aktarıldığında dahil edilen meta veri alanının adı.  Boş hücre, alanın dışarı aktarılan meta veriye dahil olmadığı anlamına gelir.

- **Açıklama:** Meta veri alanının açıklaması.

> [!NOTE]
> [Gözden geçirme kümesi aramasında](./review-set-search.md) **Anahtar Sözcükler** alanında Anahtar Sözcük Sorgu Dili (KQL) kullanılır. **Aranabilir alan adı** sütununda listelenen alanlar, sorgu oluşturucusunu kullanmak zorunda kalmadan karmaşık **sorgular** oluşturmak için bir gözden geçirme kümesi aramasında Anahtar Sözcükler alanında kullanılabilir. KQL hakkında daha fazla bilgi için bkz[. Anahtar Sözcük Sorgu Dili söz dizimi başvurusu](/sharepoint/dev/general-development/keyword-query-language-kql-syntax-reference).

<br>

****

|Alan adı ve Görünen alan adı|Aranabilir alan adı|Dışarı aktarılan alan adı|Açıklama|
|---|---|---|---|
|Ek İçerik Kimliği|AttachmentContentId||Öğenin ek içerik kimliği.|
|Avukat müşteri ayrıcalık puanı|AttorneyClientPrivilegeScore||Avukat-istemci ayrıcalık modeli içerik puanı.|
|Yazar|Yazar|Doc_authors|Belge meta verilerinden yazar.|
|GİZLİ|Gizli|Email_bcc|İleti türleri için Gizli alanı. Biçim **DisplayName \<SMTPAddress\>** şeklindedir.|
|CC|Cc|Email_cc|İleti türleri için Bilgi alanı. Biçim **DisplayName \<SMTPAddress\>** şeklindedir.|
|Uyumluluk etiketleri|ComplianceLabels|Compliance_labels|Office 365 içeriğine uygulanan [bekletme etiketleri](retention.md).|
|Bileşik Yol|CompoundPath|Compound_path|Öğenin kaynağını açıklayan okunabilir yol.|
|İçerik*|İçerik||Öğenin ayıklanan metni.|
|Konuşma Gövdesi|ConversationBody||Öğenin konuşma gövdesi.|
|Konuşma Kimliği|ConversationId|Conversation_ID|İletideki konuşma kimliği. Teams 1:1 ve grup sohbetleri için, aynı konuşmadaki tüm transkript dosyaları ve bunların aile öğeleri aynı Konuşma Kimliğini paylaşır. Daha fazla bilgi için bkz. [Microsoft Teams içeriği için eBulma (Premium) iş akışı](teams-workflow-in-advanced-ediscovery.md).|
|Konuşma Aile Kimliği|ConversationFamilyID|ConversationFamilyID|Konuşmanın tek tek öğelerini ve konuşmadaki ilgili öğeleri tanımlayan kimlik.|
|Konuşma Dizini||Conversation_index|İletiden konuşma dizini.|
|Konuşma Adı||ConversationName|Bu alan içerik türüne bağlıdır.<br>**Teams 1:1 sohbeti:** ilk iletinin ilk 40 karakteri.<br>**Teams 1:N sohbet:** Grup sohbetinin adı; kullanılamıyorsa, ilk iletinin ilk 40 karakteri.<br>**Teams Kanal Gönderisi:** Gönderi başlığı veya duyuru alt başlığı; kullanılamıyorsa, ilk iletinin ilk 40 karakteri.|
|Konuşma Pdf Saati|ConversationPdfTime||Konuşmanın PDF sürümünün oluşturulduğu tarih.|
|Konuşma Redaksiyon Yazma Zamanı|ConversationRedactionBurnTime||Sohbet için konuşmanın PDF sürümünün oluşturulduğu tarih.|
|Konuşma Konusu|ConversationTopic||Öğenin konuşma konusu.|
|Konuşma Türü|ConversationType|ConversationType|Sohbet konuşmasının türü. Değerler şunlardır: <br>**Teams 1:1 ve grup sohbetleri ve tüm Yammer konuşmaları:** Grup<br>**Teams kanalları ve özel kanalları:** Kanal|
|Silinen İletiyi İçerir|ContainsDeletedMessage|ContainsDeletedMessage|Sohbet dökümünün silinmiş bir ileti içerip içermediğini gösterir|
|Düzenlenen İletiyi İçerir|ContainsEditedMessage|ContainsEditedMessage|Sohbet dökümünün düzenlenmiş bir ileti içerip içermediğini gösterir|
|Teams Duyuru Başlığı|TeamsAnnouncementTitle|TeamsAnnouncementTitle|[Ekip duyurusundan](https://support.microsoft.com/office/send-an-announcement-to-a-channel-8f244ea6-235a-4dcc-9143-9c5b801b4992) başlık.|
|||Converted_file_path|Dönüştürülen dışarı aktarma dosyasının yolu. Yalnızca iç Microsoft kullanımı için.|
|Veli|Veli|Veli|Öğenin ilişkilendirildiği koruyucunun adı.|
|Tarih|Tarih|Tarih|Tarih, dosya türüne bağlı olarak hesaplanan bir alandır.<p>**E-posta**: Gönderme tarihi<br>**E-posta ekleri**: Belgenin son değiştirilme tarihi; kullanılamıyorsa ebeveynin gönderilme tarihi<br>**Eklenmiş belgeler**: Belgenin son değiştirme tarihi; kullanılamıyorsa, üst öğe son değiştirme tarihi<br>**SPO belgeleri (modern ekler içerir)**: Belgenin son değiştirme tarihi; kullanılamıyorsa, son değiştirme tarihini SharePoint<br>**Office 365 olmayan belgeler**: Son değiştirme tarihi<br>**Toplantılar**: Toplantı başlangıç tarihi<br>**Sesli Mesaj**: Gönderme tarihi<br>**Anlık ileti**: Gönderme tarihi<br>**Teams**: Gönderme tarihi|
|Belge açıklamaları|DocComments|Doc_comments|Belge meta verilerinden açıklamalar.|
|Belge şirketi||Doc_company|Belge meta verilerinden şirket.|
|Belge oluşturulma tarihi|CreatedTime|Doc_date_created|Belge meta verilerinden tarih oluşturma.|
|DocIndex*|||Ailedeki dizin. **-1** veya **0** , kök olduğu anlamına gelir.|
|Belge anahtar sözcükleri||Doc_keywords|Belge meta verilerinden anahtar sözcükler.|
|Belge değiştiren||Doc_modified_by|Belgeyi belge meta verilerinden en son değiştiren kullanıcı.|
|Belge düzeltmesi|Doc_Version|Doc_Version|Belge meta verilerinden düzeltme.|
|Belge konusu||Doc_subject|Belge meta verilerinden konu.|
|Belge şablonu||Doc_template|Belge meta verilerinden şablon.|
|DocLastSavedBy||Doc_last_saved_by|Belgeyi son kaydeden kullanıcının adı.|
|Baskın tema|BaskınTheme|Dominant_theme|Analiz için hesaplanmış baskın tema.|
|Yinelenen alt küme||Duplicate_subset|Tam yinelemeler için grup kimliği.|
|EmailAction*||Email_action|Değerler **Yok**, **Yanıtla** veya **İlet**; bir iletinin konu satırına göre.|
|E-posta Teslim Bilgisi İstendi||Email_delivery_receipt|Teslim bilgisi için İnternet Üst Bilgileri'nde sağlanan e-posta adresi.|
|Önemi|EmailImportance|Email_importance|İletinin önemi: **0** - Düşük; **1** - Normal; **2** - Yüksek|
|Yoksayılan işleme hataları|ErrorIgnored|Error_Ignored|Hata yoksayıldı ve düzeltilmedi.|
|EmailInternetHeaders|EmailInternetHeaders|Email_internet_headers|E-posta iletisindeki tüm e-posta üst bilgileri kümesi|
|EmailLevel*||Email_level|İletinin ait olduğu e-posta yazışması içindeki düzeyini gösterir; ekler, üst iletinin değerini devralır.|
|E-posta İletiSi Kimliği||Email_message_ID|İletiden İnternet ileti kimliği.|
|EmailReadReceiptRequested||Email_read_receipt|Okundu bilgisi için İnternet Üst Bilgilerinde sağlanan e-posta adresi.|
|E-posta Güvenliği|EmailSecurity|Email_security|İletinin güvenlik ayarı: **0** - Yok; **1** - İmzalı; **2** - Şifrelenmiş; **3** - Şifreli ve imzalı.|
|E-posta Duyarlılığı|EmailSensitivity|email_sensitivity|İletinin duyarlılık ayarı: **0** - Yok; **1** Kişisel; **2** - Özel; **3** - CompanyConfidential.|
|E-posta kümesi|EmailSet|Email_set|Aynı e-posta kümesindeki tüm iletiler için grup kimliği.|
|EmailThread*||Email_thread|İletinin e-posta kümesi içindeki konumu; kökten geçerli iletiye düğüm kimliklerinden oluşur ve noktalarla (.) ayrılır.|
|||Export_native_path|Dışarı aktarılan dosyanın yolu.|
|Ayıklanan içerik türü||Native_type|Mime türü biçiminde ayıklanan içerik türü; örneğin, **image/jpeg**|
|||Extracted_text_path|Dışarı aktarmada ayıklanan metin dosyasının yolu.|
|ExtractedTextLength*||Extracted_text_length|Ayıklanan metindeki karakter sayısı.|
|FamilyDuplicateSet*||Family_duplicate_set|Birbirinin tam yinelemesi olan aileler için sayısal tanımlayıcı (aynı içerik ve tüm aynı ekler).|
|Aile Kimliği|FamilyId|Family_ID|E-posta ve sohbetlerdeki ekleri ve ayıklanan öğeleri üst öğesiyle birlikte gruplandırma. Buna sohbet veya e-posta ile tüm ekler ve ayıklanan öğeler dahildir.|
|Aile Boyutu||Family_size|Ailedeki belge sayısı.|
|Dosya sınıfı|FileClass|File_class|SharePoint ve OneDrive içeriği için: **Belge**. <br>Exchange içeriği için: **E-posta** veya **Ek**. <br>Teams veya Yammer içeriği için: **Konuşmalar**.|
|Dosya Kimliği|FileId|File_id|Servis talebi içinde benzersiz belge tanımlayıcısı.|
|Dosya sistemi oluşturulma tarihi||File_system_date_created|Dosya sisteminden oluşturulma tarihi (yalnızca Office 365 olmayan veriler için geçerlidir).|
|Dosya sistemi değiştirme tarihi||File_system_date_modified|Dosya sisteminden değiştirme tarihi (yalnızca Office 365 olmayan veriler için geçerlidir).|
|Dosya Türü|Filetype||Dosya uzantısını temel alan öğenin dosya türü.|
|Grup Kimliği|Groupıd|Group_ID|E-posta ve belgeler için tüm öğeleri gruplandırma. Bu, e-posta için iletiyi ve tüm ekleri ve ayıklanan öğeleri içerir. Belgeler için bu, belgeyi ve eklenmiş öğeleri içerir.|
|Eki var|EmailHasAttachment|Email_has_attachment|İletinin ekleri olup olmadığını gösterir.|
|Avukatı var|HasAttorney||Katılımcılardan en az biri avukat listesinde bulunduğunda **doğru**; aksi takdirde, değer **False'tur**.|
|HasText*||Has_text|Öğenin metni olup olmadığını gösterir; olası değerler **True** ve **False** değerleridir.|
|Sabit Kimlik||Immutable_ID|Bu Kimlik, bir gözden geçirme kümesindeki bir belgeyi benzersiz olarak tanımlamak için kullanılır. Bu alan gözden geçirme kümesi aramasında kullanılamaz ve kimlik, yerel konumundaki bir belgeye erişmek için kullanılamaz.|
|Kapsayıcı tür|InclusiveType|Inclusive_type|Analiz için hesaplanan kapsayıcı tür: **0** - dahil değil; **1** - dahil; **2** - dahil eksi; **3** - dahil kopya.|
|Kimliği Yanıtla'da||In_reply_to_ID|İletideki yanıt kimliğinde.|
|InputFileExtension||Original_file_extension|Dosyanın özgün dosya uzantısı.|
|InputFileID||Input_file_ID|Gözden geçirme kümesindeki en üst düzey öğenin dosya kimliği. Ek için bu kimlik üst öğe kimliği olacaktır. Bu, aileleri birlikte gruplandırmak için kullanılabilir.|
|Modern ektir|IsModernAttachment||Bu dosya modern bir ek veya bağlı dosyadır.|
|Belge sürümünden|IsFromDocumentVersion||Geçerli belge başka bir belgenin farklı bir sürümünden.|
|E-posta eki mi?|IsEmailAttachment||Bu öğe, iletiye iliştirilmiş öğe olarak gösterilen bir e-posta ekidir.|
|Satır içi ektir|IsInlineAttachment||Bu satır içinde eklenmiştir ve iletinin gövdesinde gösterilir.|
|Temsilcidir|IsRepresentative|Is_representative|Her yineleme kümesindeki bir belge temsili olarak işaretlenir.|
|Item sınıfı|ItemClass|Item_class|Exchange sunucusu tarafından sağlanan öğe sınıfı; örneğin **, IPM. Not**|
|Son değiştirme tarihi|LastModifiedDate|Doc_date_modified|Belge meta verilerinden son değiştirme tarihi.|
|Yük Kimliği|LoadId|Load_ID|Öğenin bir gözden geçirme kümesine eklendiği yük kümesinin kimliği.|
|Konum|Konum|Konum|Belgelerin kaynaklandığı konum türünü gösteren dize.<p>**İçeri Aktarılan Veriler** - Office 365 olmayan veriler<br>**Teams** - Microsoft Teams<br>**Exchange** - posta kutularını Exchange<br>**SharePoint** - siteleri SharePoint<br>**OneDrive** - hesapları OneDrive|
|Konum adı|LocationName|Location_name|Öğenin kaynağını tanımlayan dize. Exchange için, bu posta kutusunun SMTP adresi olacaktır; SharePoint ve OneDrive için site koleksiyonunun URL'si.|
|||Marked_as_pivot|Bu dosya, neredeyse yinelenen kümedeki özettir.|
|Temsilci olarak işaretlendi|MarkAsRepresentative||Her yineleme kümesinden bir belge temsilci olarak işaretlenir.|
|Toplantı Bitiş Tarihi|MeetingEndDate|Meeting_end_date|Toplantılar için toplantı bitiş tarihi.|
|Toplantı Başlangıç Tarihi|MeetingStartDate|Meeting_start_date|Toplantılar için toplantı başlangıç tarihi.|
|İleti türü|MessageKind|Message_kind|Aranacak iletinin türü. Olası değerler: **<p>kişiler <br>belgeleri <br>e-posta <br>dışveri <br>faksları <br>anlık <br>günlük toplantıları <br><br>microsoftteams** (Microsoft Teams'da sohbetlerden, toplantılardan ve aramalardan öğeleri döndürür) **<br>not <br>gönderileri <br>rssfeeds <br>görevleri <br>sesli mesaj**|
|Modern Ek Üst Kimliği||ModernAttachment_ParentId|Belgenin üst öğesinin sabit kimliği.|
|Yerel Uzantı|NativeExtension|Native_extension|Öğenin yerel uzantısı.|
|Yerel dosya adı|NativeFileName|Native_file_name|Öğenin yerel dosya adı.|
|NativeMD5||Native_MD5|Dosya akışının MD5 karması (128 bit karma değeri).|
|NativeSHA256||Native_SHA_256|Dosya akışının SHA256 karması (256 bit karma değeri).|
|ND/ET Sıralama: Ekleri dışlama|NdEtSortExclAttach|ND_ET_sort_excl_attach|E-posta iş parçacığı (ET) kümesinin ve Neredeyse yinelenen (ND) kümesinin birleştirilmişliği. Bu alan, gözden geçirme zamanında verimli sıralama için kullanılır. ND kümelerine **D** , ET kümelerine de **E** ön eki eklenir.|
|ND/ET Sıralama: Ekleri ekleme|NdEtSortInclAttach|ND_ET_sort_incl_attach|E-posta iş parçacığı (ET) kümesinin ve neredeyse yinelenen (ND) kümesinin birleştirilmesi. Bu alan, gözden geçirme zamanında verimli sıralama için kullanılır. ND kümelerine **D** , ET kümelerine de **E** ön eki eklenir. Et kümesindeki her e-posta öğesinin ardından uygun ekler eklenir.|
|Yinelenen Kümeye Yakın||ND_set|Özet belgeye benzer öğeler aynı ND_set paylaşır.|
|O365 yazarları||O365_authors|SharePoint yazar.|
|O365 oluşturan||O365_created_by|oluşturan SharePoint.|
|O365 oluşturulma tarihi||O365_date_created|SharePoint'den oluşturulma tarihi.|
|O365ModifiedDate||O365_date_modified|SharePoint veya OneDrive İş toplanan bir belgenin (veya belge sürümünün) değiştirildiği tarih. Bu, SharePoint ve OneDrive kullanıcı deneyimindeki sürüm geçmişinde görüntülenen değiştirme tarihiyle aynıdır.|
|O365 değiştiren||O365_modified_by|SharePoint veya OneDrive tarafından değiştirildi.|
|Diğer koruyucular|DedupedCustodians|Deduped_custodians|Tam olarak yinelenen belgelerin koruyucularının listesi (e-posta için, içeriğe göre; belgeler için karmaya dayalı).|
|Diğer dosya kimlikleri|YinelenenLeri KaldırılanFileId'ler|Deduped_file_IDs|Tam olarak yinelenen belgelerin dosya kimliklerinin listesi (e-posta için, içeriğe göre; belgeler için karmaya dayalı).|
|Diğer yollar|Yinelenenleri Kaldırcompoundpath|Deduped_compound_path|Tam yineleme olan belgelerin bileşik yollarının listesi (e-posta: içeriğe göre, belgeler: karma temelinde).|
|Üst Kimlik|Parentıd|Parent_ID|Öğenin üst öğesinin kimliği.|
|Parentnode||Parent_node|E-posta yazışmasında önceki en yakın e-posta iletisi.|
|Katılımcı etki alanları|ParticipantDomains|Email_participant_domains|bir iletinin katılımcılarının tüm etki alanlarının listesi.|
|Katılımcı|Katılımcı|Email_participants|İletinin tüm katılımcılarının listesi; örneğin, Gönderen, Kime, Bilgi, Gizli.|
|Özet Kimliği|PivotId|Pivot_ID|Özetin kimliği.|
|Potansiyel olarak ayrıcalıklı|Potansiyel Ayrıcalıklar|Potentially_privileged|Avukat-istemci ayrıcalık algılama modeli belgeyi potansiyel olarak ayrıcalıklı olarak değerlendiriyorsa true|
|İşlem durumu|ProcessingStatus|Hata_kodu|Öğe bir gözden geçirme kümesine eklendikten sonra işleme durumu.|
|Okuma yüzdebirliği|ReadPercentile||İlgiye göre belgenin yüzde birlik değerini okuyun.|
|Alınan|Alınan|Email_date_received|E-postanın UTC olarak alındığı tarih ve saat.|
|Alıcı Sayısı||Recipient_count|İletideki alıcı sayısı.|
|Alıcı etki alanları|RecipientDomains|Email_recipient_domains|İletinin alıcılarının tüm etki alanlarının listesi.|
|Alıcı|Alıcı|Email_recipients|İletinin tüm alıcılarının listesi (Kime, Bilgi, Gizli).|
|||Redacted_file_path|Dışarı aktarmadaki yeniden işlem yapılan değiştirme dosyasının yolu.|
|||Redacted_text_path|Dışarı aktarmada yeniden işlem yapılan metin dosyası değiştirme işleminin yolu. Yalnızca iç Microsoft kullanımı için.|
|İlgi etiketi Olay sorunu 1||Relevance_tag_case_issue_1|İlgi etiketi Servis Talebi sorunu 1 İlgi'den.|
|İlgi puanı|RelevanceScore||İlgi düzeyine göre bir belgenin ilgi puanı.|
|İlgi etiketi|İlgi Etiketi||İlgi düzeyine göre bir belgenin ilgi puanı.|
|Temsilci Kimliği|Temsilci Kimliği||Her yineleme kümesinin sayısal tanımlayıcısı.|
|||Row_number|Yük dosyasındaki öğenin satır numarası.|
|Gönderen|Gönderen|Email_sender|İleti türleri için Gönderen (Kimden) alanı. Biçim **DisplayName \<SmtpAddress>** şeklindedir.|
|Gönderen/Yazar|SenderAuthor||Öğenin göndereni veya yazarından oluşan hesaplanan alan.|
|Gönderen etki alanı|SenderDomain|Email_sender_domain|Gönderenin etki alanı.|
|Gönderilen|Gönderilen|Email_date_sent|İletinin gönderilme tarihi.<br>Sohbetler: Transkriptten başlangıç tarihi|
|Set Order: Inclusive First|SetOrderInclusivesFirst|Set_order_inclusives_first|Sıralama alanı - e-posta ve ekler: sayaç kronolojik; belgeler: Önce özetleyin, sonra azalan benzerlik puanıyla.|
|Kimliği Ayarla||Set_ID|Aynı e-posta yazışması (Email_set) içindeki benzer içerik (ND_set) veya e-posta belgeleri aynı Set_ID paylaşır.|
|SimilarityPercent||Similarity_percent|Belgenin, neredeyse yinelenen kümenin özetine ne kadar benzer olduğunu gösterir.|
|Yerel dosya boyutu|Boyutu|Native_size|Yerel öğenin bayt sayısı.|
|Konu|Konu|Email_subject|İletinin konusu.|
|Konu/Başlık|SubjectTitle||Öğenin konusu veya başlığından oluşan hesaplanan alan.|
|Etiketler|Etiketler|Etiketler|Bir gözden geçirme kümesine uygulanan etiketler.|
|Kanal Adı|Kanal|Channelname|Bu, Teams kanal adıdır. Yalnızca Microsoft Teams içerik için geçerlidir.|
|Ekip Adı|TeamName|TeamName|**Teams:** Takımın adı<br>**Yammer:** Community adı|
|Temalar listesi|Temalar Listesi|Themes_list|Analiz için hesaplanan temalar listesi.|
|Başlık|Başlık|Doc_title|Belge meta verilerinden başlık. Belge meta verilerinden başlık. Teams ve Yammer içeriği için bu, ConversationName özelliğindeki değerdir.|
|Hedef|Hedef|Email_to|İleti türleri için To alanı. Biçim **DisplayName\<SmtpAddress>**|
|E-posta kümesinde benzersiz|UniqueInEmailSet||E-posta kümesinde ekin bir kopyası varsa **False**.|
|Sürüm Grubu Kimliği||Version_Group_Id|Aynı belgenin farklı sürümlerini gruplandırma.|
|Sürümnumarası||Version_Number|SharePoint veya OneDrive İş toplanan belgenin sürüm numarası. Bu, SharePoint ve OneDrive kullanıcı deneyimindeki sürüm geçmişinde görüntülenen sürüm numarasıyla aynıdır.|
|Düzeltildi|WasRemediated|Was_Remediated|Öğe düzeltildiyse **True**, aksi takdirde **False**.|
|Sözcük sayısı|WordCount|Word_count|Öğedeki sözcük sayısı.|
|||||

> [!NOTE]
> eBulma (Premium) olayı için veri toplarken Office 365 içerik konumlarını ararken aranabilir özellikler hakkında daha fazla bilgi için bkz[. İçerik Arama için anahtar sözcük sorguları ve arama koşulları](keyword-queries-and-search-conditions.md).
