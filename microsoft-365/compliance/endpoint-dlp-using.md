---
title: Uç nokta veri kaybını önlemeyi kullanma
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MET150
description: Uç nokta veri kaybını önleme (EPDLP) konumlarında kullanmak üzere Microsoft 365 kaybı önleme (DLP) ilkelerini yapılandırmayı öğrenin.
ms.openlocfilehash: aeb85b883738e94f2d7161cb2bc3434edbb16428
ms.sourcegitcommit: b3530441288b2bc44342e00e9025a49721796903
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2022
ms.locfileid: "63680038"
---
# <a name="using-endpoint-data-loss-prevention"></a>Uç nokta veri kaybını önlemeyi kullanma

Uç Nokta DLP özelliklerini ve bunların DLP ilkeleriyle nasıl ortaya çıkar olduklarını tanımanıza yardımcı olmak için, takip etmek için bazı senaryoları bir araya getirdik.

> [!IMPORTANT]
> Bu Uç Nokta DLP senaryoları, DLP ilkelerini oluşturmaya ve ayarlamaya yönelik resmi yordamlar değildir. Genel durumlarda DLP ilkeleriyle çalışman gerekirken aşağıdaki konulara bakın:
>
>- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)
>- [Varsayılan DLP ilkesiyle çalışmaya başlama](get-started-with-the-default-dlp-policy.md)
>- [Şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md)
>- [DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md)

## <a name="scenario-1-create-a-policy-from-a-template-audit-only"></a>Senaryo 1: Şablondan ilke oluşturma, yalnızca denetleme

Bu senaryolar için etkinlik gezginine önceden cihaz ekleme ve raporlama cihazlarınız gerekir. Henüz cihaz eklemedıysanız bkz. Uç nokta [veri kaybı önleme ile çalışmaya başlama](endpoint-dlp-getting-started.md).

1. Veri kaybını [önleme sayfasını açın](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. İlke **oluştur'a seçin**.

3. Bu senaryo için **Gizlilik'i** ve ardından **ABD Kişisel Bilgileri (PII)** Verileri'ne ve ardından Sonraki'yi **seçin**.

4. Cihazlar dışındaki **tüm** konumlar için Durum alanını kapalı konuma **kapatın**. **İleri**'yi seçin.

5. Varsayılan Gözden Geçir **ve ayarları şablon seçiminden özelleştirin ve Ardından** Sonraki'yi **seçin**.

6. Varsayılan Koruma eylemleri **değerlerini kabul et** ve Sonraki'yi **seçin**.

7. Bu **cihazlarda etkinlikleri denetle veya kısıtla Windows ve** eylemleri Yalnızca denetim olarak **bırakın**. **İleri**'yi seçin.

8. İlk değeri **sınamak istiyorum varsayılan değerini kabul edin ve** test modundayken **ilke ipuçlarını göster'i seçin**. **İleri**'yi seçin.

9. Ayarlarınızı gözden geçirin ve Gönder'i **seçin**.

10. Yeni DLP ilkesi ilke listesinde görünür.

11. Etkinlik gezgininde izlenen uç noktalardan gelen verileri denetleme. Cihazlar için konum filtresini ayarlayın ve ilkeyi ekleyin, ardından bu ilkenin etkisini görmek için ilke adına göre filtre uygulama; Gerekirse [bkz. Etkinlik gezginiyle](data-classification-activity-explorer.md) çalışmaya başlama.

12. ABD'nin Kişisel Olarak Tanınmasına Neden Olacak Bilgiler (PII) Verileri koşulını tetikleyen içerik içeren bir test öğesi paylaşmayı denebilir. Bu, ilkeyi tetikler.

13. Etkinlik gezgininde olay olup denetleme.

## <a name="scenario-2-modify-the-existing-policy-set-an-alert"></a>Senaryo 2: Var olan ilkeyi değiştirme, uyarı ayarlama

1. Veri kaybını [önleme sayfasını açın](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Senaryo **1'de oluşturduğunuz ABD Kişisel Bilgileri (PII)** Veri politikasını seçin.

3. **İlkeyi düzenle'yi seçin**.

4. Gelişmiş **DLP kuralları sayfasına gidin** ve ABD'de algılanan Düşük hacimli içerik için Kişisel Olarak **Tanımlanabilen Inf'ı düzenleyin**.

5. Sayfayı Olay **raporları bölümüne kadar** aşağı kaydırın ve Kural eşleşmesi olduğunda **yöneticilere uyarı gönder'i Açık olarak** **ayarlayın**. E-posta uyarıları otomatik olarak yöneticiye ve alıcı listesine ekley istediğiniz herkese gönderilir. 

![turn-on-incident-reports.](../media/endpoint-dlp-2-using-dlp-incident-reports.png)
   
6. Bu senaryonun amaçları doğrultusunda, bir **etkinlik kuralla her eşleşmesinde Uyarı gönder'i seçin**.

7. **Kaydet**'i seçin.

8. Önceki tüm ayarlarınızı korumak için, **Sonraki'ye ve** ardından **İlke değişikliklerini** gönder'e tıklayın.

9. ABD'nin Kişisel Olarak Tanınmasına Neden Olacak Bilgiler (PII) Verileri koşulını tetikleyen içerik içeren bir test öğesi paylaşmayı denebilir. Bu, ilkeyi tetikler.

10. Etkinlik gezgininde olay olup denetleme.

## <a name="scenario-3-modify-the-existing-policy-block-the-action-with-allow-override"></a>Senaryo 3: Var olan ilkeyi değiştirme, geçersiz kılmaya izin ver ile eylemi engelleme

1. Veri kaybını [önleme sayfasını açın](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. Senaryo **1'de oluşturduğunuz ABD Kişisel Bilgileri (PII)** Veri politikasını seçin.

3. **İlkeyi düzenle'yi seçin**.

4. Gelişmiş **DLP kuralları sayfasına gidin** ve ABD'de algılanan Düşük hacimli içerik için Kişisel Olarak **Tanımlanabilen Inf'ı düzenleyin**.

5. Sayfayı Cihaz üzerinde **etkinlikleri denetleme veya kısıtlama bölümüne Windows** ve her etkinlik için ilgili eylemi Geçersiz kılma ile engelle **olarak ayarlayın**.

   > [!div class="mx-imgBorder"]
   > ![engellemeyi geçersiz kılma eylemiyle ayarlayın.](../media/endpoint-dlp-6-using-dlp-set-blocked-with-override.png)
   
6. **Kaydet**'i seçin.

7. ABD'de Kişisel Kimliği Belirlenebilir Inf algılanan yüksek hacimli içerik için 4-7 **arasındaki adımları yinelayın**.

8. Önceki tüm ayarlarınızı korumak için, **Sonraki'ye ve** ardından **İlke değişikliklerini** gönder'e tıklayın.

9. ABD'nin Kişisel Olarak Tanınmasına Neden Olacak Bilgiler (PII) Verileri koşulını tetikleyen içerik içeren bir test öğesi paylaşmayı denebilir. Bu, ilkeyi tetikler.

   İstemci cihazında bunun gibi bir açılır pencere görüyorsunuz:

   > [!div class="mx-imgBorder"]
   > ![uç nokta dlp istemcisi bildirimi geçersiz kılmayı engelledi.](../media/endpoint-dlp-3-using-dlp-client-blocked-override-notification.png)

10. Etkinlik gezgininde olay olup denetleme.

## <a name="scenario-4-avoid-looping-dlp-notifications-from-cloud-synchronization-apps-with-auto-quarantine-preview"></a>Senaryo 4: Bulut eşitleme uygulamalarına gelen DLP bildirimlerini otomatik karantina (önizleme) ile döngüye almaktan kaçının

### <a name="before-you-begin"></a>Başlamadan önce

Bu senaryoda, dosyaları Çok Gizli duyarlılık **etiketiyle** eşitlemek OneDrive engellenmiş olur. Bu, birden çok bileşeni ve yordamları olan karmaşık bir senaryodur. Gerekenler:

- Hedef AAD ve zaten yerel bir Windows 10 klasörle OneDrive bulut depolaması eşitlene bir OneDrive kullanıcı hesabı.
- Microsoft Word bilgisayarda Windows 10 yüklü
- Yapılandırılmış ve yayımlanmış duyarlılık etiketleri— bkz [. Duyarlılık](get-started-with-sensitivity-labels.md#get-started-with-sensitivity-labels) etiketleriyle çalışmaya başlama ve Duyarlılık [etiketlerini ve ilkelerini oluşturma ve yapılandırma](create-sensitivity-labels.md#create-and-configure-sensitivity-labels-and-their-policies).

Üç yordam vardır.

1. Uç Nokta DLP Otomatik karantina ayarlarını yapılandırma.
2. Çok Gizli duyarlılık etiketine sahip hassas öğeleri **engelleyen bir** ilke oluşturun.
3. İlkenin hedef Windows 10 cihazda bir Word belgesi oluşturun, etiketi ekleyin ve eşitlenen yerel OneDrive kullanıcı hesaplarına kopyalayın.  

### <a name="configure-endpoint-dlp-unallowed-app-and-auto-quarantine-settings"></a>Uç Nokta DLP izin verilmeyen uygulamayı ve Otomatik karantina ayarlarını yapılandırma

1. Uç [Nokta DLP ayarlarını açma](https://compliance.microsoft.com/datalossprevention?viewid=globalsettings)

2. Izin **verilmeyen uygulamalar'a genişletin**.

3. **Çok Gizli** etiketinin öğelerine erişmesini engellemek için, *Izin verilmeyen* uygulamaları ekle veya düzenle'yi OneDrive bir ** görünen ad ve yürütülebilir ad onedrive.exeonedrive.exeyürütülebilir dosya adı ekleyin.

4. Otomatik **karantinaya alın ve** **Kaydet'i seçin**.

5. Otomatik **karantina ayarları'nın altında Otomatik** karantina **ayarlarını düzenle'yi seçin**.

6. Izin **verilmeyen uygulamalar için Otomatik karantinayı etkinleştir**.

7. Yerel makinelerde özgün hassas dosyaların taşınmalarını istediğiniz klasörün yolunu girin. Örneğin:
   
    *Isaiah langer* kullanıcı adı için **'%homedrive%%homepath%\Microsoft DLP\Quarantine'** klasörü taşınan öğeleri şu adlı klasöre alır:  

    *C:\Users\IsaiahLanger\Microsoft DLP\Karantina\OneDrive*

    yazın ve özgün dosya adına bir tarih ve saat damgası ekler.
    
    > [!NOTE]
    > DLP Otomatik karantinası, izin verilmeyen her uygulama için dosyalar için alt klasörler oluşturur. Dolayısıyla, izin verilmeyen *uygulamalar listesinde Not Defteri* *OneDrive* uygulamalarınız varsa, **\OneDrive** için bir alt klasör ve **\Not Defteri** için başka bir alt klasör oluşturulur.

8. Dosyaları **aşağıdaki metni içeren .txt bir dosyayla değiştir'i seçin** ve yer tutucu dosyaya istediğiniz metni girin. Örneğin, otomatik dörtte *bir olarak adlandırılmış bir 1.docx*:
    
    > %%FileName%% kuruluşun veri kaybı önleme (DLP) ilkesi %%PolicyName%% ile koruduğu ve karantina klasörüne taşındığı hassas bilgileri içerir: %%KarantinaPath%%
    
    bu iletiyi içeren bir metin dosyası bırakır:
    
    > otomatik dörtte 1.docx, kurumnizin veri kaybı önleme (DLP) ilkesiyle koruduğu ve karantina klasörüne taşındığı hassas bilgileri içerir: C:\Users\IsaiahLanger\Microsoft DLP\Karantina\OneDrive\otomatik 1_20210728_151541.docx.

9. **Kaydet'i seçin**

### <a name="configure-a-policy-to-block-onedrive-synchronization-of-files-with-the-sensitivity-label-highly-confidential"></a>Dosyaların Yüksek Gizli duyarlılık OneDrive eşitlenmiş olarak eşitlenmiş olarak eşitlemeyi engellemek için bir ilke yapılandırma

1. Veri kaybını [önleme sayfasını açın](https://compliance.microsoft.com/datalossprevention?viewid=policies).

2. İlke **oluştur'a seçin**.

3. Bu senaryo için Özel'i, **Özel** **ilke'yi ve sonra da Sonraki'yi** **seçin**.

4. Ad ve Açıklama **alanlarını** doldurun **ve** Sonraki'yi **seçin**.

5. Cihazlar dışındaki **tüm** konumlar için Durum alanını kapalı konuma **kapatın**. Bunu test etmek istediğiniz belirli bir son kullanıcı hesabınız varsa, bu hesabı kapsamda seçmeye emin olun. **İleri**'yi seçin.

6. Varsayılan Gelişmiş **DLP kuralları oluştur veya özelleştir seçimini kabul et ve** İleri'yi **seçin**.

7. Şu değerlerle kural oluşturun:
    1. **Ad** >  *Senaryo 4 Otomatik karantinaya alın*.
    1. **Koşullar** >  **İçerik içeriği** >  **Duyarlılık etiketleri** >  **Çok Gizli**.
    1.  **Eylemler** >  **Tüm cihazlarda etkinlikleri denetleme veya Windows Eriştirilmeyen** >  **uygulamalarBlock ile** >  **erişin**. Bu senaryonun amacı doğrultusunda, diğer tüm etkinlikleri temizleyin.
    1. **Kullanıcı bildirimleri** >  **On.**
    1. **Uç nokta** cihazları > **Etkin değilken kullanıcılara ilke ipucu bildirimi göster'i** seçin.
    
8. **Kaydet'i ve** ardından **Sonraki'yi seçin**.

9. Hemen **aç'ı seçin**. **İleri**'yi seçin.

10. Ayarlarınızı gözden geçirin ve Gönder'i **seçin**.

    > [!NOTE]
    > Yeni ilkenin çoğaltılması ve hedef bilgisayara uygulanması için en az bir saat Windows 10 izin ver.

11. Yeni DLP ilkesi ilke listesinde görünür.

### <a name="test-auto-quarantine-on-the-windows-10-device"></a>Windows 10 cihazında Otomatik karantinaya Windows 10 sınama

1. Dosyaların duyarlılık Windows 10 fazla gizli adım 5 ile eşitlesini engellemek üzere bir ilke yapılandırma altında belirttiğiniz kullanıcı hesabıyla OneDrive [bilgisayarda oturum açın](#configure-a-policy-to-block-onedrive-synchronization-of-files-with-the-sensitivity-label-highly-confidential).

2. İçeriği bu klasörle eşitlenmayacak bir OneDrive. Örneğin:

    *C:\otomatik karantina kaynak klasörü*

3. Otomatik Microsoft Word'i açın ve kaynak klasörde bir dosya oluşturun. Çok **gizli duyarlılık** etiketini uygulama; bkz [. Office'da dosyalarınıza ve e-postanıza duyarlılık Office](https://support.microsoft.com/topic/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9).

4. Yeni oluşturduğunuz dosyayı eşitleme klasörünüze OneDrive kopyalayın. Eyleme izin verilmiyor ve dosyanın karantinaya alınmayacaklarını söyleyen bir kullanıcı bildirimi bildirimi görünmektedir. Örneğin, kullanıcı adı *Isaiah Langer* ve Belgeyi otomatik karantinaya *1.docxbaşlıklı bir* belge için şu iletiyi alırsınız:

    ![Belirtilen dosya için eşitleme eylemine izin verilmiyor OneDrive dosyanın karantinaya alın olacağını belirten veri kaybı önleme kullanıcı bildirimi açılır menüsü.](../media/auto-quarantine-user-notification-toast.png)
    
    İleti şu şekilde okunur:
    
    > Bu uygulamayla otomatik belge 1.docx açılmasına izin verilmez. Dosya 'C:\Users\IsaiahLanger\Microsoft DLP\OneDrive' klasörüne karantinaya alınır.

5. **Yok'a seçin**.

6. Yer tutucu metin dosyasını açın. Belge, belgeye **otomatik karantina 1.docx_ *date_time.txt***. 

7. Karantina klasörünü açın ve özgün dosyanın orada olduğunu onaylayın.
 
8. Etkinlik gezgininde izlenen uç noktalardan gelen verileri denetleme. Cihazlar için konum filtresini ayarlayın ve ilkeyi ekleyin, ardından bu ilkenin etkisini görmek için ilke adına göre filtre uygulama; Gerekirse [bkz. Etkinlik gezginiyle](data-classification-activity-explorer.md) çalışmaya başlama.

9. Etkinlik gezgininde olay olup denetleme.

## <a name="scenario-5-restrict-unintentional-sharing-to-unallowed-cloud-apps-and-services"></a>5. Senaryo: Izin verilmeyen bulut uygulamaları ve hizmetleriyle otomatik paylaşımı kısıtlama

Uç Nokta DLP ve Edge Web tarayıcısıyla, hassas öğelerin izin verilmeyen bulut uygulamaları ve hizmetleriyle istediğiniz zaman paylaşımı kısıtlayabilirsiniz. Edge, bir öğenin Uç Nokta DLP ilkesiyle ne zaman kısıtlanmış olduğunu anlar ve erişim kısıtlamalarını zorlar.

Cihazlar'ı  doğru yapılandırılmış bir DLP ilkesinde konum olarak ve Microsoft Edge tarayıcısını kullanırsanız, bu ayarlarda tanımmış olduğunuz izin verilmeyen tarayıcıların DLP ilkesi denetimlerinize uygun olan hassas öğelere erişimi engel olur. Bunun yerine, kullanıcılar DLP'nin dayatılan kısıtlamaları anlayan Microsoft Edge, DLP ilkesi koşullarına uygun olduğunda etkinlikleri engelleyebilir veya kısıtlayan ELP'i kullanmaya yeniden yönlendireceğiz.

Bu kısıtlamayı kullanmak için üç önemli parça yapılandırmanız gerekir:

1. Hassas öğelerin paylaşılmasını engellemek istediğiniz yerleri (hizmetler, etki alanları, IP adresleri) belirtin.

2. Bir DLP ilkesi eşleşmesi olduğunda belirli hassas öğelere erişmesine izin verilmiyor tarayıcıları ekleyin.

3. E-postayı bulut hizmetleri ve izin verilmeyen tarayıcıdan Access'i dönüştürerek, **yüklemenin bu alanlarla** sınırlandırılmış olması gereken hassas öğe türleri tanımlamak Upload DLP **ilkelerini yapılandırabilirsiniz**.

Yeni hizmetler, uygulamalar ve ilkeler eklemeye devam eder ve iş ihtiyaçlarına göre kısıtlamalarınızı genişletebilirsiniz ve hassas verileri koruyabilirsiniz. 

Bu yapılandırma, verilerinizin güvenli kalmasını sağlarken aynı zamanda kullanıcıların hassas olmayan öğelere erişmesini ve bu öğeleri paylaşmasını engelleyen veya kısıtlayan gereksiz kısıtlamaları önlemeye de yardımcı olur.
## <a name="see-also"></a>Ayrıca bkz.

- [Uç nokta veri kaybını önleme hakkında bilgi](endpoint-dlp-learn-about.md)
- [Uç nokta veri kaybını önlemeye başlama](endpoint-dlp-getting-started.md)
- [Veri kaybını önleme hakkında bilgi](dlp-learn-about-dlp.md)
- [DLP ilkesi oluşturma, sınama ve ayarlama](create-test-tune-dlp-policy.md)
- [Etkinlik gezgini ile çalışmaya başlama](data-classification-activity-explorer.md)
- [Uç Nokta için Microsoft Defender](/windows/security/threat-protection/)
- [11 Windows 10 cihaz Windows cihaz ekleme ve cihaz ekleme Microsoft 365 genel bakış](/microsoft-365/compliance/device-onboarding-overview)
- [Microsoft 365 aboneliği](https://www.microsoft.com/microsoft-365/compare-microsoft-365-enterprise-plans?rtc=1)
- [Azure Active Directory (AAD) bir araya](/azure/active-directory/devices/concept-azure-ad-join)
- [Temel Microsoft Edge yeni Chromium](https://support.microsoft.com/help/4501095/download-the-new-microsoft-edge-based-on-chromium)
- [Varsayılan DLP ilkesiyle çalışmaya başlama](get-started-with-the-default-dlp-policy.md)
- [Şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md)
