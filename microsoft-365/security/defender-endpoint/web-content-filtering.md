---
title: Web içeriği filtreleme
description: web sitelerine erişimi içerik kategorilerine göre izlemek ve düzenlemek için Uç Nokta için Microsoft Defender'de web içeriği filtrelemeyi kullanın.
keywords: web koruması, web tehdit koruması, web'e göz atma, izleme, raporlar, kartlar, etki alanı listesi, güvenlik, kimlik avı, kötü amaçlı yazılım, yararlanma, web siteleri, ağ koruması, Edge, Internet Explorer, Chrome, Firefox, web tarayıcısı
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 7b195f595592b5c3b284b6dee4fd65b66d80e06a
ms.sourcegitcommit: d1b60ed9a11f5e6e35fbaf30ecaeb9dfd6dd197d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/29/2022
ms.locfileid: "66489386"
---
# <a name="web-content-filtering"></a>Web içeriği filtreleme

**Şunlar için geçerlidir:**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [İş için Microsoft Defender](../defender-business/mdb-overview.md)

> [!TIP]
> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

## <a name="what-is-web-content-filtering"></a>Web içeriği filtreleme nedir?

Web içeriği filtreleme, Uç Nokta için Microsoft Defender ve [İş için Microsoft Defender'daki Web koruma](web-protection-overview.md) özelliklerinin bir parçasıdır. Web içeriği filtreleme, kuruluşunuzun web sitelerine erişimi içerik kategorilerine göre izlemesine ve düzenlemesine olanak tanır. Bu web sitelerinin çoğu (kötü amaçlı olmasalar bile) uyumluluk düzenlemeleri, bant genişliği kullanımı veya diğer endişeler nedeniyle sorunlu olabilir.

Belirli kategorileri engellemek için cihaz gruplarınız genelinde ilkeleri yapılandırın. Kategorinin engellenmesi, belirtilen cihaz grupları içindeki kullanıcıların kategoriyle ilişkili URL'lere erişmesini engeller. Engellenmeyen tüm kategoriler için URL'ler otomatik olarak denetlenür. Kullanıcılarınız URL'lere kesinti olmadan erişebilir ve daha özel bir ilke kararı oluşturmaya yardımcı olmak için erişim istatistiklerini toplarsınız. Görüntüledikleri sayfadaki bir öğe engellenen bir kaynağa çağrı yapıyorsa kullanıcılarınız bir engelleme bildirimi görür.

Web içeriği filtreleme, Windows Defender SmartScreen (Microsoft Edge) ve Ağ Koruması (Chrome, Firefox, Brave ve Opera) tarafından gerçekleştirilen bloklarla büyük web tarayıcılarında kullanılabilir. Tarayıcı desteği hakkında daha fazla bilgi için [önkoşullar](#prerequisites) bölümüne bakın.

## <a name="benefits-of-web-content-filtering"></a>Web içeriği filtrelemenin avantajları

- Kullanıcıların, ister şirket içinde ister dışarıda gezinirken engellenen kategorilerdeki web sitelerine erişmesi engellenir.
- Güvenlik ekibiniz, gerçek bloklar ve web kullanımı üzerinde görünürlük ile web raporlarına aynı merkezi konumda erişebilir.
- Uç Nokta için Defender kullanıyorsanız, güvenlik ekibiniz [Uç Nokta için Microsoft Defender rol tabanlı erişim denetimi ayarlarında](/microsoft-365/security/defender-endpoint/rbac) tanımlanan cihaz gruplarını kullanarak kullanıcı gruplarına kolayca ilke dağıtabilir.
- İş için Defender kullanıyorsanız, tüm kullanıcılara uygulanacak bir web içeriği filtreleme ilkesi tanımlayabilirsiniz. 

## <a name="prerequisites"></a>Önkoşullar

Bu özelliği denemeden önce aşağıdaki tabloda açıklanan gereksinimleri karşıladığınızdan emin olun:

| Gereksinim | Açıklama |
|:---|:---|
| Abonelik | Aboneliğiniz aşağıdakilerden birini içermelidir:<br/>- [Windows 10/11 Kurumsal E5](/windows/deployment/deploy-enterprise-licenses)<br/>- [Microsoft 365 E5](https://www.microsoft.com/microsoft-365/enterprise/e5?activetab=pivot%3aoverviewtab)<br/>- Microsoft 365 E5 Güvenlik<br/>- [Microsoft 365 E3](https://www.microsoft.com/microsoft-365/enterprise/e3?activetab=pivot%3aoverviewtab)<br/>- [Uç Nokta için Microsoft Defender Plan 1 veya Plan 2](../defender/eval-defender-endpoint-overview.md)<br/>- [İş için Microsoft Defender](../defender-business/mdb-overview.md)<br/>- [Microsoft 365 İş Ekstra](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium)|
| Portal erişimi | <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalına</a> erişiminiz olmalıdır. |
| İşletim sistemi | Kuruluşunuzun cihazları [en son virüsten koruma/kötü amaçlı yazılımdan koruma güncelleştirmeleriyle](manage-updates-baselines-microsoft-defender-antivirus.md) aşağıdaki işletim sistemlerinden birini çalıştırıyor olmalıdır: <br/>- Windows 11<br/>- Windows 10 Yıldönümü Güncelleştirmesi (sürüm 1607) veya üzeri |
| İlgili koruma | [Windows Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) ve [ağ koruması](network-protection.md) kuruluşunuzun cihazlarında etkinleştirilmelidir. |

## <a name="data-handling"></a>Veri işleme

Veriler, [Uç Nokta için Microsoft Defender veri işleme ayarlarınızın](data-storage-privacy.md) bir parçası olarak seçilen bölgede depolanır. Verileriniz o bölgedeki veri merkezinden ayrılmaz. Ayrıca verileriniz, veri sağlayıcılarımız da dahil olmak üzere hiçbir üçüncü tarafla paylaşılmaz.

## <a name="precedence-for-multiple-active-policies"></a>Birden çok etkin ilke için öncelik

Aynı cihaza birden çok farklı web içeriği filtreleme ilkesi uygulanması, her kategori için daha kısıtlayıcı ilkenin uygulanmasına neden olur. Aşağıdaki senaryoyu inceleyin:

- **İlke 1**: 1 ve 2 kategorilerini engeller ve gerisini denetler
- **İlke 2**: 3 ve 4 kategorilerini engeller ve gerisini denetler

Sonuç, 1 - 4 kategorilerinin tümünün engellenmesidir.  Bu, aşağıdaki görüntüde gösterilmiştir.

:::image type="content" source="images/web-content-filtering-policies-mode-precedence.png" alt-text="Web içeriği filtreleme ilkesi engelleme modunun denetim modu üzerindeki önceliğini gösterir":::

## <a name="turn-on-web-content-filtering"></a>Web içeriği filtrelemeyi açma

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalına</a> gidin ve oturum açın.

2. Gezinti bölmesinde **Ayarlar** \> **Uç Noktaları** \> **Genel** \> **Gelişmiş Özellikler'i** seçin. 

3. **Web içeriği filtrelemeyi görene** kadar aşağı kaydırın. 

4. İki durumlu düğmeyi **Açık** konuma getirin ve ardından **Tercihleri kaydet'i** seçin.

### <a name="configure-web-content-filtering-policies"></a>Web içeriği filtreleme ilkelerini yapılandırma

Web içeriği filtreleme ilkeleri hangi site kategorilerinin hangi cihaz gruplarında engelleneceğini belirtir. İlkeleri yönetmek için **Ayarlar** \> **Uç Noktaları** \> **Web içeriği filtreleme'ye** gidin ( **Kurallar'ın** altında).

İlkeler, aşağıdaki üst veya alt kategorilerden herhangi birini engellemek için dağıtılabilir:

<details>
<summary>Yetişkinlere özgü içerik</summary>

**Tarikatlar**: Üyeleri sosyal olarak kabul edilenlerden farklı bir inanç sistemine tutku gösteren gruplar veya hareketlerle ilgili siteler. 

**Kumar**: Çevrimiçi kumar ve kumar becerilerini ve uygulamalarını teşvik eden siteler.

**Çıplaklık**: Genellikle artistik biçimde tam ön ve yarı çıplak görüntüler veya videolar sağlayan ve bu tür malzemelerin indirilmesine veya satılmasına izin veren siteler.

**Pornografi / Cinsel açıdan açık**: Görüntü tabanlı veya metin biçiminde cinsel içerik içeren siteler. Cinsel yönelimli her türlü malzeme de burada listelenmiştir.

**Seks eğitimi**: Cinsellik ve cinselliği bilgilendirici ve röntgenci olmayan bir şekilde tartışan siteler, insan üremesi ve kontrasepsiyon hakkında eğitim veren siteler, cinsel hastalıklardan korunma tavsiyesi sunan siteler ve cinsel sağlık konuları hakkında tavsiyeler sunan siteler.

**Zevksiz**: Okul çocuklarının görmesi için uygun olmayan içeriğe yönelik siteler veya bir işverenin personelinin erişimi konusunda rahatsız olacağı, ancak mutlaka şiddet içeren veya pornografik olmadığı.

**Şiddet**: İnsanlara veya hayvanlara yönelik şiddet ile ilgili içeriği görüntüleyen veya teşvik eden siteler.

</details>

<details>
<summary>Yüksek bant genişliği</summary>

**Siteleri indirme**: Birincil işlevi kullanıcıların medya içeriğini veya bilgisayar programları gibi programları indirmesine izin vermek olan siteler.

**Görüntü paylaşımı**: Sosyal yönleri olanlar da dahil olmak üzere öncelikli olarak fotoğrafları aramak veya paylaşmak için kullanılan siteler.

**Eşler arası**: Eşler arası (P2P) yazılımları barındıran veya P2P yazılımı kullanarak dosyaların paylaşılmasını kolaylaştıran siteler.

**Akış medyası & indirmeleri**: Birincil işlevi akış medyasının dağıtımı olan siteler veya kullanıcıların akış medyasını aramasına, izlemesine veya dinlemesine olanak sağlayan siteler.
  
</details>

<details>
<summary>Yasal sorumluluk</summary>

**Çocuk istismarı görüntüleri: Çocuk** istismarı görüntülerini veya pornografiyi içeren siteler. 

**Suç faaliyeti**: Yasa dışı faaliyetler hakkında talimat veren, tavsiyede bulunan veya teşvik eden siteler.

**Hacking**: Kırılan telif hakkıyla korunan malzemeleri dağıtan siteler de dahil olmak üzere bilgisayar yazılımı veya donanımının yasa dışı veya sorgulanabilir kullanımı için kaynaklar sağlayan siteler.

**Nefret & hoşgörüsüzlüğü**: Nüfusun herhangi bir bölümü hakkında ırk, din, cinsiyet, yaş, milliyet, fiziksel engellilik, ekonomik durum, cinsel tercihler veya başka bir yaşam tarzı seçimiyle tanımlanabilecek agresif, aşağılayıcı veya kötüleyici görüşleri teşvik eden siteler.

**Yasadışı uyuşturucu: Yasa** dışı/kontrollü maddeler satan, madde kötüye kullanımını teşvik eden veya ilgili parafernalia satan siteler.

**Yasa dışı yazılım**: Kötü amaçlı yazılım, casus yazılım, botnet, kimlik avı dolandırıcılığı veya korsanlık & telif hakkı hırsızlığı içeren veya kullanımını teşvik eden siteler.

**Okul hilesi**: İntihal veya okul hilesi ile ilgili siteler. 

**Kendine zarar** verme: Kullanıcılara yönelik kötü amaçlı ve/veya tehdit içeren siber zorbalık içeren siteler de dahil olmak üzere kendine zarar vermeyi teşvik eden siteler.

**Silahlar: Silah** satan veya silah kullanımını savunan herhangi bir site, silahlar, bıçaklar ve mühimmat dahil ancak bunlarla sınırlı değildir.

</details>

<details>
<summary>Eğlence</summary>

**Sohbet**: Öncelikli olarak web tabanlı sohbet odaları olan siteler.

**Oyunlar**: Barındırma çevrimiçi hizmetler veya oyunla ilgili bilgiler aracılığıyla oyunları teşvik eden siteler de dahil olmak üzere video veya bilgisayar oyunlarıyla ilgili siteler.

**Anlık ileti: Anlık ileti** yazılımını veya istemci tabanlı anlık iletileri indirmek için kullanılabilecek siteler.

**Profesyonel ağ: Profesyonel** ağ hizmetleri sağlayan siteler.

**Sosyal ağ: Sosyal** ağ hizmetleri sağlayan siteler.

**Web tabanlı e-posta: Web** tabanlı posta hizmetleri sunan siteler.
  
</details>

<details>
<summary>Kategorilenmemiş</summary>

**Yeni kaydedilen etki alanları**: Son 30 gün içinde yeni kaydedilen ve henüz başka bir kategoriye taşınmamış siteler.

**Park edilmiş etki alanları**: İçeriği olmayan veya daha sonra kullanılmak üzere park edilmiş siteler.
  
**NOT**: Kategorilere ayrılmamış yalnızca yeni kaydedilen etki alanlarını ve park edilmiş etki alanlarını içerir ve bu kategorilerin dışındaki diğer tüm siteleri içermez.
  
</details>

### <a name="create-a-policy"></a>İlke oluşturma

Yeni ilke eklemek için şu adımları izleyin:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalında</a> **Ayarlar** > **Web içeriği filtreleme** > **+ İlke ekle'yi** seçin.

2. Bir ad belirtin.

3. Engellenmesi gereken kategorileri seçin. Her üst kategoriyi tamamen genişletmek ve belirli web içeriği kategorilerini seçmek için genişlet simgesini kullanın.

4. İlke kapsamını belirtin. İlkenin nereye uygulanacağını belirtmek için cihaz gruplarını seçin. Yalnızca seçili cihaz gruplarındaki cihazların seçilen kategorilerdeki web sitelerine erişmesi engellenir.

   > [!IMPORTANT]
   > Microsoft 365 İş Ekstra veya İş için Defender kullanıyorsanız, web içeriği filtreleme ilkeniz varsayılan olarak tüm kullanıcılara uygulanır. Kapsam belirleme geçerli değildir.

5. Özeti gözden geçirin ve ilkeyi kaydedin. İlke yenilemesinin seçili cihazlarınıza uygulanması 2 saat kadar sürebilir.

> [!NOTE]
> - Bir cihaz grubunda herhangi bir kategori seçmeden bir ilke dağıtabilirsiniz. Bu eylem, engelleme ilkesi oluşturmadan önce kullanıcı davranışını anlamanıza yardımcı olmak için yalnızca denetim ilkesi oluşturur.
> - Bir ilkeyi kaldırıyorsanız veya cihaz gruplarını aynı anda değiştiriyorsanız, bu durum ilke dağıtımında gecikmeye neden olabilir.
> - "Kategorilere Ayrılmamış" kategorisinin engellenmesi beklenmeyen ve istenmeyen sonuçlara yol açabilir.

## <a name="end-user-experience"></a>Son kullanıcı deneyimi

Üçüncü taraf desteklenen tarayıcılar için engelleme deneyimi, kullanıcıya engellenen bağlantıyı bildiren sistem düzeyinde bir ileti sağlayan ağ koruması tarafından sağlanır. Daha kullanıcı dostu ve tarayıcı içi bir deneyim için Microsoft Edge'i kullanmayı göz önünde bulundurun.

### <a name="allow-specific-websites"></a>Belirli web sitelerine izin ver

Özel bir gösterge ilkesi oluşturarak tek bir siteye izin vermek için web içeriği filtrelemesinde engellenen kategoriyi geçersiz kılmak mümkündür. Özel gösterge ilkesi, söz konusu cihaz grubuna uygulandığında web içeriği filtreleme ilkesinin yerini alır.

Özel bir gösterge tanımlamak için şu adımları izleyin:

1. <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalında</a> **Ayarlar** \> **Uç Noktaları** \> **Göstergeleri** \> **URL'si/Etki Alanı** \> **Öğe Ekle'ye** gidin.

2. Sitenin etki alanını girin.

3. İlke eylemini **İzin Ver** olarak ayarlayın.

### <a name="dispute-categories"></a>İhtilaf kategorileri

Yanlış kategorilere ayrılmış bir etki alanıyla karşılaşırsanız, kategoriye doğrudan Microsoft 365 Defender portalından itiraz edebilirsiniz.

Bir etki alanının kategorisine itiraz etmek için **Raporlar** \> **Web koruması** \> **Web İçeriği Filtreleme Ayrıntıları** \> **Etki Alanları'na** gidin. Web İçeriği Filtreleme raporlarının etki alanları sekmesinde, etki alanlarının her birinin yanında bir üç nokta görürsünüz. Bu üç noktanın üzerine gelin ve **İtiraz Kategorisi'ne** tıklayın.

Önceliği seçebileceğiniz ve yeniden kategorilere ayırmak için önerilen kategori gibi daha fazla ayrıntı ekleyebileceğiniz bir panel açılır. Formu tamamladıktan sonra **Gönder'i** seçin. Ekibimiz bir iş günü içinde isteği gözden geçirecek. Engellemeyi hemen kaldırmak için [özel bir izin verme göstergesi](indicator-ip-domain.md) oluşturun.

## <a name="web-content-filtering-cards-and-details"></a>Web içeriği filtreleme kartları ve ayrıntıları

Web içeriği filtreleme ve **web tehdit koruması** hakkındaki bilgileri içeren kartları görüntülemek için **Raporlar** \> Web koruması'na tıklayın. Aşağıdaki kartlar web içeriği filtreleme hakkında özet bilgiler sağlar.

### <a name="web-activity-by-category"></a>Kategoriye göre web etkinliği

Bu kart, erişim denemesi sayısındaki en büyük artış veya düşüşe sahip üst web içeriği kategorilerini listeler. Kuruluşunuzda son 30 gün, 3 ay veya 6 aydaki web etkinliği desenlerindeki önemli değişiklikleri anlayın. Daha fazla bilgi görüntülemek için bir kategori adı seçin.

Bu özelliği kullanmanın ilk 30 gününde, kuruluşunuzda bu bilgileri görüntülemek için yeterli veri olmayabilir.

:::image type="content" source="images/web-activity-by-category600.png" alt-text="Kategori kartına göre web etkinliği" lightbox="images/web-activity-by-category600.png":::

### <a name="web-content-filtering--summary-card"></a>Web içeriği filtreleme özet kartı

Bu kart, engellenen erişim denemelerinin farklı üst web içeriği kategorileri arasında dağılımını görüntüler. Belirli bir üst web kategorisi hakkında daha fazla bilgi görüntülemek için renkli çubuklardan birini seçin.

:::image type="content" source="images/web-content-filtering-summary.png" alt-text="Web içeriği filtreleme özet kartı" lightbox="images/web-content-filtering-summary.png":::

### <a name="web-activity-summary-card"></a>Web etkinliği özet kartı

Bu kart, tüm URL'lerdeki web içeriği için toplam istek sayısını görüntüler.

:::image type="content" source="images/web-activity-summary.png" alt-text="Web etkinliği özet kartı" lightbox="images/web-activity-summary.png":::

### <a name="view-card-details"></a>Kart ayrıntılarını görüntüleme

Karttaki grafikten bir tablo satırı veya renkli çubuk seçerek her kartın **Rapor ayrıntılarına** erişebilirsiniz. Her kartın rapor ayrıntıları sayfası web içeriği kategorileri, web sitesi etki alanları ve cihaz grupları hakkında kapsamlı istatistiksel veriler içerir.

:::image type="content" source="images/web-protection-report-details.png" alt-text="Web koruma raporu ayrıntıları" lightbox="images/web-protection-report-details.png":::

- **Web kategorileri**: Kuruluşunuzda erişim denemeleri olan web içeriği kategorilerini listeler. Özet açılır listesini açmak için belirli bir kategoriyi seçin.

- **Etki alanları**: Kuruluşunuzda erişilen veya engellenen web etki alanlarını listeler. Bu etki alanıyla ilgili ayrıntılı bilgileri görüntülemek için belirli bir etki alanını seçin.

- **Cihaz grupları**: Kuruluşunuzda web etkinliği oluşturan tüm cihaz gruplarını listeler

Zaman aralığı seçmek için sayfanın sol üst kısmındaki zaman aralığı filtresini kullanın. Ayrıca bilgileri filtreleyebilir veya sütunları özelleştirebilirsiniz. Seçili öğe hakkında daha fazla bilgi içeren bir açılır pencere bölmesi açmak için bir satır seçin.

### <a name="known-issues-and-limitations"></a>Bilinen sorunlar ve sınırlamalar

Yalnızca cihazınızın işletim sistemi yapılandırması Sunucu (**cmd** \> **Systeminfo** \> **İşletim Sistemi Yapılandırması**) ise Microsoft Edge desteklenir. Ağ Koruması yalnızca Desteklenen üçüncü taraf tarayıcılarda trafiğin güvenliğini sağlamakla sorumlu olan Sunucu cihazlarında İnceleme modunda desteklenir.

Azure Sanal Masaüstü çok oturumlu konaklarında yalnızca Microsoft Edge desteklenir ve ağ koruması Windows 10 desteklenmez.

Ağ koruması şu anda SSL incelemesini desteklememektedir ve bu da bazı sitelerin normalde engellenecek web içeriği filtrelemesine izin vermesine neden olabilir. TLS el sıkışması gerçekleştikten ve belirli yeniden yönlendirmelerin ayrıştırılamamasından sonra şifrelenmiş trafiğin görünür olmaması nedeniyle sitelere izin verilir.  Bu, bazı web tabanlı posta oturum açma sayfalarından posta kutusu sayfasına yeniden yönlendirmeleri içerir. Kabul edilen bir geçici çözüm olarak, hiçbir kullanıcının siteye erişemediğinden emin olmak için oturum açma sayfası için özel bir blok göstergesi oluşturabilirsiniz. Bunun aynı web sitesiyle ilişkili diğer hizmetlere erişimini engelleyebileceğini unutmayın. 

Microsoft 365 İş Ekstra veya İş için Microsoft Defender kullanıyorsanız, ortamınız için bir web içeriği filtreleme ilkesi tanımlayabilirsiniz. Bu ilke varsayılan olarak tüm kullanıcılara uygulanır.

## <a name="see-also"></a>Ayrıca bkz.

- [Web korumasına genel bakış](web-protection-overview.md)
- [Web tehdit koruması](web-threat-protection.md)
- [Web güvenliğini izleyin](web-protection-monitoring.md)
- [Web tehditlerine yanıt verin](web-protection-response.md)
- [Ağ Koruması gereksinimleri](web-content-filtering.md)
