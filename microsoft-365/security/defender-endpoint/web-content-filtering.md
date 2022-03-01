---
title: Web içeriği filtreleme
description: Web sitelerine erişimi içerik kategorilerine göre izlemek ve düzenlemek için Uç Nokta için Microsoft Defender'da web içeriği filtrelemeyi kullanın.
keywords: web koruması, web tehdit koruması, web'e gözatma, izleme, raporlar, kartlar, etki alanı listesi, güvenlik, kimlik avı, kötü amaçlı yazılım, exploit, web siteleri, ağ koruması, Edge, Internet Explorer, Chrome, Firefox, web tarayıcısı
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 2bf43507b624cc1dae78534d579d01c1f2cef096
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2021
ms.locfileid: "62997510"
---
# <a name="web-content-filtering"></a>Web içeriği filtreleme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

Web içeriği filtreleme, Uç Nokta için Microsoft [Defender'daki Web](web-protection-overview.md) koruma özellikleri kapsamındadır. Bu özellik, kuruluşlarının kendi içerik kategorilerine göre web sitelerine erişimi izlemesini ve düzenlemesini sağlar. Kötü amaçlı değilken, bu web sitelerinin birçoğu uyumluluk mevzuatı, bant genişliği kullanımı veya diğer endişelerden dolayı sorun yaratabilir.

Cihaz gruplarınız genelinde ilkeleri belirli kategorileri engellemek üzere yapılandırabilirsiniz. Kategorinin engellenmesi, belirtilen cihaz gruplarında yer alan kullanıcıların kategoriyle ilişkili URL'lere erişmesini sağlar. Engellenmiş durumdaki herhangi bir kategori için URL'ler otomatik olarak denetlenmektedir. Kullanıcılarınız KESINTI olmadan URL'lere erişebilirsiniz ve daha özel bir ilke kararı atayabilirsiniz. Kullanıcılarınız, görüntülemekte olduğu sayfada yer alan bir öğe engellenen bir kaynağı arıyorsa engellenen bir bildirim görebilirler.

Web içeriği filtreleme, başlıca web tarayıcılarında Windows Defender SmartScreen (Microsoft Edge) ve Ağ Koruması (Chrome, Firefox, Doğru ve Opera) tarafından gerçekleştirilen bloklarla kullanılabilir. Tarayıcı desteği hakkında daha fazla bilgi için önkoşullar bölümüne bakın.

## <a name="benefits-of-web-content-filtering"></a>Web içeriği filtrelemenin avantajları

- İster şirket içinde ister uzakta olsunlar, kullanıcıların engellenen kategorilerde web sitelerine erişimi engellenir.

- Güvenlik ekibinin, uç nokta rol tabanlı erişim denetimi ayarları için Microsoft Defender'da tanımlanan cihaz gruplarını kullanarak kullanıcı gruplarına [ilkeleri rahatça dağıtabilirsiniz](/microsoft-365/security/defender-endpoint/rbac).

- Güvenlik ekibinin aynı merkezi konumdaki web raporlarına erişebilirsiniz ve gerçek bloklar ve web kullanımıyla ilgili görünürlük sağlar.

## <a name="prerequisites"></a>Önkoşullar

Bu özelliği denmeden önce, aşağıdaki gereksinimleri karşılamıyor olun:

- Aboneliğiniz şunları içerir: Windows 10 Enterprise E5, Microsoft 365 E5, Microsoft 365 E5 Güvenlik, Microsoft 365 E3 + Microsoft 365 E5 Güvenlik  eklentisini veya Endpoint tek başına lisansı için Microsoft Defender'ı seçin. 

- Bu portala <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender vardır</a>.

- En son virüsten koruma/kötü amaçlı yazılımdan koruma güncelleştirmeleriyle, Windows 10 Yıldönümü Güncelleştirmesi (sürüm 1607) veya Windows 11'i çalıştıran cihazları [çalışıyor](manage-updates-baselines-microsoft-defender-antivirus.md).

- Windows Defender SmartScreen ve Ağ Koruması, kuruluş cihazlarında etkindir.

## <a name="data-handling"></a>Veri işleme

Veriler, Uç nokta veri işleme ayarları için [Microsoft Defender'ın bir parçası olarak seçilen bölgede depolanır](data-storage-privacy.md). Verileriniz bu bölgedeki veri merkezinden ayrılmaz. Buna ek olarak, verileriniz veri sağlayıcılarımız da dahil olmak üzere hiçbir üçüncü tarafla paylaşılmaz.

## <a name="turn-on-web-content-filtering"></a>Web içeriği filtrelemeyi açma

Web portalında sol gezintiden <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">, Microsoft 365 Defender</a> Genel **Gelişmiş Ayarlar** **Uç** \> **Noktalar'ı** \> \> **seçin**. Web içeriği filtreleme girdisini görene **kadar aşağı kaydırın**. Düğmeyi Açık ve Kaydetme **tercihlerine** **geçiş.**

### <a name="configure-web-content-filtering-policies"></a>Web içeriği filtreleme ilkelerini yapılandırma

Web içeriği filtreleme ilkeleri, hangi site kategorilerinin hangi cihaz gruplarında engellenmiş olduğunu belirtir. İlkeleri yönetmek için, Uç **Ayarlar** \> **Web içeriği** \> **filtrelemesi'ne** gidin (Kurallar'ın **altında**).

İlkeler, aşağıdaki üst veya alt kategorilerden herhangi birini engellemek için dağıtılabilir:

<details>
<summary>Yetişkin içeriği</summary>

**Özelkler**: Üyeleri sosyal olarak kabul edilenlerden farklı bir ima sistemi tutkusunu gösterdiği gruplarla veya hareketlerle ilgili siteler. 

**Yaygın**: Çevrimiçi teşvik becerileri ve alıştırmalar geliştiren siteler.

**Çıplaklık**: Normalde artistik formda, tam ön ve yarı renkli resimler veya videolar sağlayan ve bu tür malzemelerin indir veya satışına izin ver sahne olan siteler.

**Pornografi / Cinsel olan:** Görüntü tabanlı veya metinsel bir biçimde cinsel içerik içeren siteler. Cinsel yönelimli her tür malzeme burada listelenmiştir.

**Cinsiyet eğitimi**: İnsan yeniden üretme ve hile hakkında eğitim sağlayan siteler, cinsellik bulaşmasını önlemeye yönelik öneriler sunan siteler ve cinsel cinsel sağlık konuları hakkında öneriler sunan siteler ve cinsel sağlık konuları hakkında öneriler sunan, bilgilendirici ve voyeurist olmayan bir şekilde cinsiyeti ve cinselliği tartışan siteler.

**Zevksiz**: Okul çocukları için uygun olmayan içeriklere yönelen siteler ya da işverenin personeline erişmesi ile birlikte, pornografik veya pornografik olması zorunlu değildir.

**Şiddet**: İnsanlara veya hayvanlara yönelik şiddet ile ilgili içeriklerin görüntüleniyor veya tanıt yer alıyor siteler.

</details>

<details>
<summary>Yüksek bant genişliği</summary>

**Siteleri indirme**: Birincil işlevi kullanıcıların medya içeriğini veya bilgisayar programları gibi programları indirmesine izin vermek olan siteler.

**Resim paylaşımı**: Sosyal açıdan özellikleri olan siteler dahil olmak üzere, öncelikle fotoğraf aramak veya paylaşmak için kullanılan siteler.

**Eşler arası**: Eşler arası (P2P) yazılım barındıran veya P2P yazılımını kullanarak dosya paylaşımını kolaylaştıran siteler.

**Medya akışı & indirmeleri**: Birincil işlevi akış medyası dağıtımı olan siteler veya kullanıcıların medya aramasına, izlemesine veya dinlemesine olanak sağlayan siteler.
  
</details>

<details>
<summary>Yasal sorumluluk</summary>

**Çocuğun kötüye kullanımı resimleri**: Çocuğun kötüye kullanımı görüntüleri veya pornografisi içeren siteler. 

**Suç etkinlikleri**: Yasa dışı etkinliklere yönelik yönerge, öneriler veya promosyonda bulunduran siteler.

**Hacking**: Bilgisayar yazılımının veya donanımın yasa dışı ya da şüpheli kullanımına yönelik kaynaklar sağlayan siteler ve telif hakkıyla korunan malzemeyi dağıtan siteler de buna dahil.

**Nefret &** rahatsızlığı: Yarış, din, cinsiyet, yaş, millilik, fiziksel engellilik, ekonomik durum, cinsel tercihler veya diğer yaşam biçimi tercihleri ile belirlenen, popülasyonda herhangi bir bölümü hakkında saldırgan, kötü amaçlı görüşler tanıtan siteler.

**Yasa dışı ihlal**: Yasa dışı/denetimli ihlaller satan, tacize teşvik eden veya ilgili paraphernalia satışı yapılan siteler.

**Yasa dışı yazılım**: Kötü amaçlı yazılım, casus yazılım, botnet, kimlik avı dolandırıcılığı veya korsan kullanımı içeren veya telif hakkı hırsızlığını & siteler.

**Okul hilesi**: Aşıma veya okul hilesi ile ilgili siteler. 

**Kendine zarar verme**: Kullanıcılara yönelik kötü amaçlı ve/veya tehdit içeren siber tehdit içeren siteler dahil, kendine zarar veren siteler.

**İşte**: Avukat veya avukat kullanımına sahip olan herhangi bir site; bu, bilgili, özelk ve tirnaklar dahil ancak bunlarla sınırlı değildir.

</details>

<details>
<summary>Boş zaman</summary>

**Sohbet**: Temelde web tabanlı sohbet odaları olan siteler.

**Oyunlar**: Çevrimiçi hizmetleri veya oyunlarla ilgili bilgileri barındırma yoluyla oyunların reklamını yapan siteler dahil, video veya bilgisayar oyunlarıyla ilgili siteler.

**Anlık mesajlaşma**: Anlık ileti yazılımını veya istemci tabanlı anlık mesajlaşmayı indirmek için kullanılmaktadır.

**Professional ağı**: Profesyonel ağ hizmetleri sağlayan siteler.

**Sosyal ağ**: Sosyal ağ hizmetleri sağlayan siteler.

**Web tabanlı e-posta**: Web tabanlı posta hizmetleri sunan siteler.
  
</details>

<details>
<summary>Uncategorized</summary>

**Yeni kaydedilen etki** alanları: Son 30 gün içinde yeni kaydedilen ve henüz başka bir kategoriye taşınmamış siteler.

**Park halindeki etki** alanları: İçerikleri yok olan veya daha sonra kullanmak üzere parka alınan siteler.
  
**NOT**: Kategorilere kapatılmamış etki alanları yalnızca yeni kayıtlı etki alanlarını ve beklemede olan etki alanlarını içerir ve bu kategorilerin dışındaki tüm diğer siteleri içermemektedir.
  
</details>

### <a name="create-a-policy"></a>İlke oluşturma

Yeni ilke eklemek için şu adımları izleyin:

1. Web Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Web içerik</a> filtreleme **+ İlke ekle Ayarlar** >  >  **yi seçin**.

2. Bir ad belirtin.

3. Engellenecek kategorileri seçin. Her üst kategoriyi tamamen genişletmek ve belirli web içeriği kategorilerini seçmek için genişletme simgesini kullanın.

4. İlke kapsamını belirtin. İlkenin uygulanacak yeri belirtmek için cihaz gruplarını seçin. Yalnızca seçili cihaz gruplarında yer alan cihazların seçili kategorilerde web sitelerine erişimi engellenebilir.

5. Özeti gözden geçirme ve ilkeyi kaydetme. İlke yenilemenin seçili cihazlarınıza geçerlik üzere 2 saat kadar sürebilir.

> [!NOTE]
>
> - Cihaz grubunda herhangi bir kategori seçmeden ilkeyi dağıtabilirsiniz. Bu eylem, engelleme ilkesi oluşturmadan önce kullanıcı davranışını anlamanıza yardımcı olmak için yalnızca denetim ilkesi oluşturacak.
> - Aynı anda bir ilkeyi veya cihaz gruplarını değiştiriyorsanız, bu ilke dağıtımının gecikmeye neden olabilir.
> - "Kategorilere Açık" kategorisinin engellenmesi beklenmedik ve istenmeyen sonuçlara neden olabilir.

## <a name="end-user-experience"></a>Son kullanıcı deneyimi

Üçüncü taraf desteklenen tarayıcılar için engelleme deneyimi Ağ Koruması tarafından sağlanır ve kullanıcıya engellenen bağlantı hakkında bildirim veren sistem düzeyinde bir ileti sağlanır. Daha kullanıcı dostu, tarayıcı deneyimi için bu deneyimi Microsoft Edge.

### <a name="allow-specific-websites"></a>Belirli web sitelerine izin verme

Özel bir gösterge ilkesi oluşturarak tek bir siteye izin vermek için, web içeriği filtrelemesinde engellenen kategoriyi geçersiz kılmak mümkündür. Söz konusu cihaz grubuna uygulanan web içeriği filtreleme ilkesi, özel gösterge ilkesinde yer alır.

Özel bir gösterge tanımlamak için şu adımları izleyin:

1. Microsoft 365 Defender <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Uç Ayarlar</a> **Url** \> **/** \> Etki Alanı **Öğe** **Ekle'ye** \> \> **gidin**.

2. Sitenin etki alanını girin.

3. İlke eyleme İzin **Ver'i ayarlayın**.

### <a name="dispute-categories"></a>İhtilaf kategorileri

Yanlış kategorilere ayrılmış bir etki alanıyla karşılaşırsanız, kategoriye doğrudan portaldan itiraz edebilirsiniz.

Etki alanının kategorisine itiraz etmek için, Raporlar Web  Koruması \> **Web İçeriği** \> **Filtreleme Ayrıntıları Etki Alanları'nın gidin** \> **.** Web İçeriği Filtreleme raporlarının etki alanları sekmesinde, etki alanlarının her biri yanında bir üç nokta görebilirsiniz. Bu üç noktanın üzerine gelin ve İhtilaf **Kategorisi'ne seçin**.

Önceliği seçerek ve geri alan için önerilen kategori gibi daha fazla ayrıntı ekleyebilirsiniz. Formu tamamlandıktan sonra Gönder'i **seçin**. Ekibimiz isteği bir iş günü içinde inceler. Hemen engellemeyi kaldırmak için özel bir [izin göstergesi oluşturun](indicator-ip-domain.md).

### <a name="url-category-lookup"></a>URL kategori araması

Web sitesinin kategorisini belirlemek için, Uç Noktalar Araması'nın altındaki Web sitesi portalında (<https://security.microsoft.com>) Microsoft 365 Defender URL **arama işlevini kullanabilirsiniz**\>. URL arama sonuçlarında, web içeriği filtreleme kategorisi **URL/Etki alanı ayrıntıları altında görünür**. Aşağıdaki resimde gösterildiği gibi, yöneticiler doğrudan bu sayfadan etki alanının kategorisine de itiraz edebilirsiniz. Kategori sonucu göster gösterilmezse, URL şu anda var olan bir web içeriği filtreleme kategorisine atanmadı.

![Web içeriği filtreleme kategori arama sonuçlarının görüntüsü.](../../media/web-content-filtering-category-lookup.png)

## <a name="web-content-filtering-cards-and-details"></a>Web içeriği filtreleme kartları ve ayrıntıları

Web **içeriği filtreleme** \> **ve web** tehdit koruması hakkında bilgiler olan kartları görüntülemek için Raporlar Web koruması'ı seçin. Aşağıdaki kartlarda, web içeriği filtreleme hakkında özet bilgiler sağlanmaktadır.

### <a name="web-activity-by-category"></a>Kategoriye göre web etkinliği

Bu kartta, erişim denemelerinin sayısında en fazla artış veya en az olan üst web içeriği kategorileri liste bulunmaktadır. Son 30 gün, 3 ay veya 6 aydan itibaren, kuruluşta web etkinliği düzenleri içerisinde önemli değişiklikleri anlıyoruz. Daha fazla bilgi görüntülemek için bir kategori adı seçin.

Bu özelliğin kullanımına ilişkin ilk 30 gün içinde, bu bilgileri görüntülemek için yeterli veriniz olmuyor olabilir.

![Kategori kartına göre web etkinliğinin resmi.](images/web-activity-by-category600.png)

### <a name="web-content-filtering--summary-card"></a>Web içeriği filtreleme özet kartı

Bu kartta, engellenmiş erişim girişimleri farklı üst web içeriği kategorileri genelinde dağıtıldı. Belirli bir üst web kategorisi hakkında daha fazla bilgi görüntülemek için renkli çubuklardan birini seçin.

![Web içeriği filtreleme özet kartının görüntüsü.](images/web-content-filtering-summary.png)

### <a name="web-activity-summary-card"></a>Web etkinliği özet kartı

Bu kart, tüm URL'lerde web içeriği isteklerinin toplam sayısını görüntüler.

![Web etkinliği özet kartının görüntüsü.](images/web-activity-summary.png)

### <a name="view-card-details"></a>Kart ayrıntılarını görüntüleme

Kartta yer **alan grafikten** bir tablo satırı veya renkli çubuk seçerek her kartın Rapor ayrıntılarına erişebilirsiniz. Her kartın rapor ayrıntıları sayfası web içeriği kategorileri, web sitesi etki alanları ve cihaz grupları hakkında kapsamlı istatistiksel veriler içerir.

![Web koruma raporu ayrıntılarının resmi.](images/web-protection-report-details.png)

- **Web kategorileri**: Kurumda erişim denemelerine sahip olan web içeriği kategorilerini listeler. Özet açılır öğesini açmak için belirli bir kategori seçin.

- **Etki** alanları: Kurumda erişilen veya engellenen web etki alanlarını listeler. Belirli bir etki alanıyla ilgili ayrıntılı bilgileri görüntülemek için o etki alanını seçin.

- **Cihaz grupları**: Kurumda web etkinliği oluşturan tüm cihaz gruplarını listeler

Bir zaman aralığı seçmek için sayfanın sol üst kısmında yer alan zaman aralığı filtresini kullanın. Bilgileri filtrenin yanı sıra sütunları özelleştirebilirsiniz. Seçili öğe hakkında daha fazla bilgi de olan açılır pencereyi açmak için bir satır seçin.

### <a name="known-issues-and-limitations"></a>Bilinen sorunlar ve sınırlamalar

Yalnızca Microsoft Edge OS yapılandırması Sunucu (**cmd** \> **SystemInfo** \> **OS Yapılandırması) ise yalnızca bu yapılandırmayı destekler**. Ağ Koruması yalnızca, desteklenen üçüncü taraf tarayıcılarda trafiğin güvenliğini sağlamaktan sorumlu olan Sunucu cihazlarında Denetleme modunda desteklenir.

Ağ Koruması şu anda SSL incelemesini desteklememektedir ve bunun sonucunda web sitelerine Web İçeriği Filtreleme tarafından izin verilen ve normalde engellenmiş olabilir. TLS el sıkışması gerçekleştikten sonra şifrelenmiş trafikte görünürlüğün olmamasından ve bazı yönlendirmelerin ayrıştırılama kabiliyetinden dolayı sitelere izin verilmeyecektir.  Bu, bazı web tabanlı posta oturum açma sayfalarından posta kutusu sayfasına yeniden yönlendirmeleri içerir. Kabul edilen geçici çözüm olarak, kullanıcıların siteye erişe olduğundan emin olmak için oturum açma sayfası için özel bir engelleme göstergesi oluşturabilirsiniz. Bu, onların aynı web sitesiyle ilişkilendirilmiş diğer hizmetlere erişimini engell olabilir. 

## <a name="see-also"></a>Ayrıca bkz.

- [Web korumasına genel bakış](web-protection-overview.md)
- [Web tehdit koruması](web-threat-protection.md)
- [Web güvenliğini izleme](web-protection-monitoring.md)
- [Web tehditlerine yanıt verme](web-protection-response.md)
- [Ağ Koruması gereksinimleri](web-content-filtering.md)
