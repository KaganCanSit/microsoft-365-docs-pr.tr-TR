---
title: Bloomberg İleti verilerini arşivlemek için bağlayıcı ayarlama
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Yöneticiler, aynı gün içinde Bloomberg İletisi e-posta aracından verileri içeri aktaracak ve arşivlayacak bir veri bağlayıcısı Microsoft 365. Bu, üçüncü taraf veri kaynaklarından verileri Microsoft 365'da arşivlemenize olanak sağlar ve böylece yasal saklama, İçerik Arama ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanarak kurumnizin üçüncü taraf verilerini yönetebilirsiniz.
ms.openlocfilehash: 5b1f32760542bf9ace2adaa8640571f665ba3ffb
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569875"
---
# <a name="set-up-a-connector-to-archive-bloomberg-message-data"></a>Bloomberg İleti verilerini arşivlemek için bağlayıcı ayarlama

Bloomberg İletisi işbirliği aracından finansal Microsoft 365 uyumluluk merkezi e-posta verilerini içeri aktararak arşivlemek için aşağıdaki [bağlantıda bir veri](https://www.bloomberg.com/professional/product/collaboration/) bağlayıcısı kullanın. Siz bağlayıcıyı ayardikten ve yapılandırdikten sonra, bağlayıcı, her gün organizasyon un Bloomberg güvenli FTP (SFTP) sitesine bağlanır ve e-posta öğelerini İnternet'te posta kutularına Microsoft 365.

Bloomberg İleti verileri kullanıcı posta kutularında depo edildikten sonra, Bloomberg İleti verilerine Mahkeme Microsoft 365 saklama, içerik araması, Yerinde arşivleme, denetim, İletişim uyumluluğu ve Microsoft 365 bekletme ilkeleri gibi uyumluluk özelliklerini uygulayabilirsiniz. Örneğin, içerik arama aracını kullanarak Bloomberg İleti e-postalarında arama veya Bloomberg Message verilerini içeren posta kutusunu bir özel durumunda bir özel durum bilgi Advanced eDiscovery ilişkilendirilebilirsiniz. Bloomberg Message bağlayıcısı kullanarak verileri başka bir kuruluşta içeri aktarın Microsoft 365 bu bağlayıcıları kullanarak organizasyon un kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-bloomberg-message-data"></a>Bloomberg Message verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde Bloomberg İleti verilerini aynı dosyada arşivlemek için bağlayıcı kullanma Microsoft 365.

![Bloomberg message import and archive process.](../media/BloombergMessageArchiving.png)

1. Organizasyonunız Bloomberg SFTP sitesi ayarlamak için Bloomberg ile birlikte çalışır. Ayrıca, Bloomberg İletisi'yi e-posta iletilerini Bloomberg SFTP sitesine kopyalayacak şekilde yapılandırmak için Bloomberg ile birlikte çalışacaksınız.

2. Her 24 saatte bir, Bloomberg İletisi'den gelen e-posta iletileri Bloomberg SFTP sitesine kopyalanır.

3. Microsoft 365 uyumluluk merkezi'ta oluşturdukları Bloomberg İleti bağlayıcısı her gün Bloomberg SFTP sitesine bağlanır ve önceki 24 saat içinde gönderilen e-posta iletilerini Microsoft Bulut'un güvenli bir Azure Depolama alanına aktarıyor.

4. Bağlayıcı, e-posta iletisi öğelerini belirli bir kullanıcının posta kutusuna aktarıyor. Belirli bir kullanıcının posta kutusunda BloombergMessage adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır.

   Bağlayıcı bunu, CorporateEmailAddress özelliğinin değerini kullanarak yapar. Her e-posta iletisi, e-posta iletisi her katılımcının e-posta adresiyle doldurulan bu özelliği içerir. *CorporateEmailAddress* özelliğinin değerini kullanarak otomatik kullanıcı eşlemeye ek olarak, CSV eşleme dosyasını karşıya yükerek özel eşleme de tanımlayabilirsiniz. Bu eşleme dosyası, bir Bloomberg UUID'sini ve Microsoft 365 her kullanıcı için ilgili posta kutusu adresini içerir. Otomatik kullanıcı eşlemesini etkinleştirir ve özel eşleme sağlarsanız, bağlayıcının önce özel eşleme dosyasına bakacak her e-posta öğesi için özel eşleme dosyası görüntüler. Kullanıcının Bloomberg UUID'sine karşılık gelen Microsoft 365 kullanıcı değilse, bağlayıcı, e-posta öğesinin *CorporateEmailAddress* özelliğini kullanır. Bağlayıcı özel eşleme dosyasında veya Microsoft 365 öğenin *CorporateEmailAddress* özelliğinde geçerli bir kullanıcı bulamazsa, öğe aktarılmaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

Bloomberg İleti verilerini arşivlemek için gereken bazı uygulama adımları Microsoft 365 dışındadır ve uyumluluk merkezinde bağlayıcı oluşturamadan önce tamamlanması gerekir.

- Bloomberg message bağlayıcısı ayarlamak için oldukça İyi Gizlilik (PGP) ve Güvenli Kabuk (SSH) için tuşları ve anahtar geçişlerini kullansanız gerekir. Bu anahtarlar Bloomberg SFTP sitesini yapılandırmak için kullanılır ve bağlayıcı tarafından Bloomberg SFTP sitesine bağlanarak verileri bu siteye Microsoft 365. PGP anahtarı, Bloomberg SFTP sitesinden yeni bir siteye aktarılan verilerin şifrelemesi yapılandırmak için Microsoft 365. Bağlayıcı Bloomberg SFTP sitesine bağlandığında güvenli bir uzak oturum açma etkinleştirmek üzere güvenli kabuk yapılandırmak için SSH tuşu kullanılır.

  Bağlayıcıyı ayarlarken, Microsoft tarafından sağlanan ortak tuşları ve anahtar geçişlerini kullanma seçeneğiniz vardır veya kendi özel anahtarlarınızı ve geçiş tümcelerinizi kullanabilirsiniz. Microsoft tarafından sağlanan ortak anahtarları kullanmalarını öneririz. Ancak, organizasyonunız zaten özel anahtarları kullanarak Bloomberg SFTP sitesini yapılandırmışsa, aynı özel anahtarları kullanarak bir bağlayıcı oluşturabilirsiniz.

- Her Yerden [Bloomberg'e abone olun](https://www.bloomberg.com/professional/product/remote-access/?bbgsum-page=DG-WS-PROF-PROD-BBA). Bu, ayarlamak ve yapılandırmak istediğiniz Bloomberg SFTP sitesine erişmek için Her Yerden Bloomberg'de oturum açabilirsiniz.

- Bloomberg SFTP (Güvenli dosya aktarım protokolü) sitesi ayarlayın. Bloomberg'in SFTP sitesini ayarlaması için Bloomberg'den gelen veriler her gün SFTP sitesine yüklendi. 2. Adımda oluştursanız, bağlayıcı bu SFTP sitesine bağlanır ve e-posta verilerini bu Microsoft 365 aktarıyor. SFTP, aktarım işlemi sırasında posta kutularına gönderilen Bloomberg İleti verilerini de şifreler.

  Bloomberg *SFTP (BB-SFTP olarak da adlandırılan) hakkında bilgi için*:

  - Bloomberg Desteği'nde "SFTP Bağlantı Standartları" [belgesine bakın](https://www.bloomberg.com/professional/support/documentation/).

  - [Bloomberg müşteri desteği ile iletişime geçin](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc).

- Bloomberg ile birlikte bir SFTP sitesi ayarlamak için çalışıyorsanız, siz Bloomberg uygulama e-posta iletisine yanıt verdikten sonra Bloomberg size bazı bilgiler sağlayacaktır. Aşağıdaki bilgilerin bir kopyasını kaydedin. Bunu, 3. Adım'da bir bağlayıcı ayarlamak için kullanırsiniz.

  - Firma kodu, kuruluşun kimliğidir ve Bloomberg SFTP sitesinde oturum açmak için kullanılır.

  - Bloomberg SFTP sitenizin parolası

  - Bloomberg SFTP sitesinin URL'si (örneğin, sftp.bloomberg.com). Bunun yanı sıra, Bloomberg SFTP sitesi için uygun bir IP adresi de kullanabilir ve bağlayıcıyı ayarlamak için de kullanılabilir.

  - Bloomberg SFTP sitesi için bağlantı noktası numarası

- Bloomberg Message bağlayıcısı, bir günde toplam 200.000 öğe içeri aktarabilirsiniz. SFTP sitesinde 200.000'den fazla öğe varsa, bu öğelerin hiçbiri Microsoft 365.

- 3. Adımda Bloomberg İleti bağlayıcısı oluşturan (ve 1. adımda ortak anahtarları ve IP adresini indiren kullanıcı) Veri Bağlayıcısı Yöneticisi rolüne atanmıştır. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="set-up-a-connector-using-public-keys"></a>Ortak tuşları kullanarak bağlayıcı ayarlama

Bu bölümdeki adımlar, Oldukça İyi Gizlilik (PGP) ve Güvenli Kabuk (SSH) için ortak anahtarları kullanarak Bloomberg İleti bağlayıcısı ayarlamayı gösterir.

### <a name="step-1-obtain-pgp-and-ssh-public-keys"></a>1. Adım: PGP ve SSH ortak anahtarlarını alma

İlk adım PGP ve SSH ortak anahtarlarının bir kopyasını almaktır. 2. Adımda bu tuşları, Bloomberg SFTP sitesini, bağlayıcının (3. Adımda oluşturdukları) SFTP sitesine bağlanmasına ve Bloomberg İletisi e-posta verilerini bu posta kutularına aktarmasına izin verecek şekilde Microsoft 365 kullanırsınız. Bu adımda, Bloomberg SFTP sitesini yapılandırarak kullanabileceğiniz bir IP adresi de elde edebilirsiniz.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bloomberg **İletisi'nin** altındaki Veri **bağlayıcıları sayfasında Görünüm'e** **tıklayın**.

3. Bloomberg **İletisi ürün** açıklaması sayfasında Bağlayıcı ekle'ye **tıklayın**

4. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

5. İçerik kaynağı **için kimlik bilgileri ekle sayfasında** , Microsoft tarafından sağlanan **PGP ve SSH ortak anahtarlarını kullanmak istiyorum'a tıklayın**.

   ![Ortak tuşları kullanma seçeneğini belirtin.](../media/BloombergMessagePublicKeysOption.png)

6. 1. adımda, Her dosyanın bir kopyasını yerel bilgisayarınıza kaydetmek için **SSH** İndir, **PGP** anahtarını indir ve **IP** adresi bağlantılarını indir bağlantılarına tıklayın.

   ![Genel anahtarları ve IP adresini indirmek için bağlantılar.](../media/BloombergMessagePublicKeyDownloadLinks.png)

   Bu dosyalar, 2. Adımda Bloomberg SFTP sitesini yapılandırmak için kullanılan aşağıdaki öğeleri içerir:

   - PGP ortak anahtarı: Bu anahtar, Bloomberg SFTP sitesinden Bloomberg SFTP sitesinden yeni bir siteye aktarılan verilerin şifrelemesi Microsoft 365.

   - SSH ortak anahtarı: Bu anahtar, bağlayıcı Bloomberg SFTP sitesine bağlandığında güvenli bir uzak oturum açma etkinleştirmek üzere güvenli kabuk yapılandırmak için kullanılır.

   - IP adresi: Bloomberg SFTP sitesi, bu IP adresi üzerinden bağlantı isteklerini kabul etmek üzere yapılandırılmıştır. Bloomberg Message bağlayıcısı tarafından SFTP sitesine bağlanmak ve Bloomberg Message verilerini Posta'ya aktarmak için aynı IP Microsoft 365.

7. **İptal'e** tıklar ve sihirbazı kapatır. Bağlayıcıyı oluşturmak için 3. adımda bu sihirbaza dönersiniz.

### <a name="step-2-configure-the-bloomberg-sftp-site"></a>2. Adım: Bloomberg SFTP sitesini yapılandırma

> [!NOTE]
> Organizasyonunız daha önce genel PGP ve SSH tuşlarını kullanarak Instant Bloomberg verilerini arşivlemek için bir Bloomberg SFTP sitesi ayarladısa, başka bir site ayarlamak zorunda değildir. 3. Adımda bağlayıcıyı 2013'te yken de aynı SFTP sitesini belirtebilirsiniz.

Sonraki adım, PGP ve SSH ortak tuşlarını ve 1. Adımda edinilen IP adresini KULLANARAK BLOOMberg SFTP sitesi için PGP şifrelemesini ve SSH kimlik doğrulamasını yapılandırmaktır. Bu, 3. Adımda açtığınız Bloomberg İleti bağlayıcının Bloomberg SFTP sitesine bağlanmalarını ve Bloomberg İleti verilerini Bloomberg İletisi'ne aktarmalarını Microsoft 365. Bloomberg SFTP sitesinizi ayarlamak için Bloomberg müşteri desteğiyle birlikte çalışmanız gerekir. Yardım [için Bloomberg müşteri desteğine](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc) başvurun.

> [!IMPORTANT]
> Bloomberg, 1. Adımda indirdiğiniz üç dosyayı bir e-posta iletisine eklemenizi ve Bloomberg SFTP adresinizi ayarlamak için bu dosya üzerinde birlikte çalışırken müşteri destek ekibine göndermenizi önermektedir.

### <a name="step-3-create-a-bloomberg-message-connector"></a>3. Adım: Bloomberg İleti bağlayıcısı oluşturma

Son adım, bu bağlantıda bir Bloomberg İletisi bağlayıcısı Microsoft 365 uyumluluk merkezi. Bağlayıcı, sizin sağlamakta olduğu bilgileri Bloomberg SFTP sitesine bağlanmak ve e-posta iletilerini, O365'te ilgili kullanıcı posta kutusu kutularına Microsoft 365.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bloomberg **İletisi'nin** altındaki Veri **bağlayıcıları sayfasında Görünüm'e** **tıklayın**.

3. Bloomberg **İletisi ürün** açıklaması sayfasında Bağlayıcı ekle'ye **tıklayın**

4. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

5. İçerik kaynağı **için kimlik bilgileri ekle sayfasında** , Microsoft tarafından sağlanan **PGP ve SSH ortak anahtarlarını kullanmak istiyorum'a tıklayın**.

6. 3. Adım'ın altında, aşağıdaki kutulara gerekli bilgileri girin ve Bağlantıyı **doğrula'ya tıklayın**.

      - **Ad:** Bağlayıcının adı. Bunun, kurum içinde benzersiz olması gerekir.

      - **Firma kodu:** Bloomberg SFTP sitesinde kullanıcı adı olarak kullanılan, organizasyon kimlik.

      - **Parola:** Organizasyon un Bloomberg SFTP sitesi için parola.

      - **SFTP URL'SI:** Bloomberg SFTP sitesinin URL'si (örneğin, `sftp.bloomberg.com`). Bu değer için bir IP adresi de kullanabilirsiniz.

      - **SFTP bağlantı noktası:** Bloomberg SFTP sitesi bağlantı noktası numarası. Bağlayıcı bu bağlantı noktasını SFTP sitesine bağlanmak için kullanır.

7. Bağlantı başarıyla doğrulandıktan sonra, Sonraki'ne **tıklayın**.

8. Kullanıcı **tanımla sayfasında** , verileri içeri aktarıla kullanıcıları belirtin.

     - **Kuruluş 2013'te çalışan tüm kullanıcılar**. Tüm kullanıcıların verilerini içeri aktar için bu seçeneği belirtin.

     - **Yalnızca Mahkeme tutmada olan kullanıcılar**. Yalnızca posta kutuları Mahkeme tutmada bulunan kullanıcılara ait verileri içeri aktarmayı bu seçeneği belirtin. Bu seçenek, verileri LitigationHoldEnabled özelliği True olarak ayarlanmış kullanıcı posta kutularına içeri aktarmaktadır. Daha fazla bilgi için [bkz. Mahkeme tutma oluşturma](create-a-litigation-hold.md).

9. Map **Bloomberg Message users to Microsoft 365 sayfasında**, otomatik kullanıcı eşlemesini etkinleştirin ve gerektiğinde özel kullanıcı eşlemesi sağlar.

   > [!NOTE]
   > Bağlayıcı ileti öğelerini belirli bir kullanıcının posta kutusuna içeri aktarıyor. Belirli bir kullanıcının posta **kutusunda BloombergMessage** adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, *CorporateEmailAddress özelliğinin değerini kullanarak* bunu yapar. Her sohbet iletisi bu özelliği içerir ve özellik, sohbet iletisi her katılımcının e-posta adresiyle doldurulur. *CorporateEmailAddress* özelliğinin değerini kullanarak otomatik kullanıcı eşlemeye ek olarak, CSV eşleme dosyasını karşıya yükerek özel eşleme de tanımlayabilirsiniz. Eşleme dosyası, her kullanıcı için Bloomberg UUID'sini Microsoft 365 posta kutusu adresini içerir. Otomatik kullanıcı eşlemesini etkinleştirir ve özel eşleme sağlarsanız, bağlayıcının önce özel eşleme dosyasına bakacak her ileti öğesi için özel eşlemesi olur. Kullanıcının Bloomberg UUID'sine karşılık gelen geçerli bir kullanıcı Microsoft 365 bulamazsa, bağlayıcıda sohbet *öğesinin CorporateEmailAddress* özelliği kullanılır. Bağlayıcı, özel eşleme dosyasında veya ileti Microsoft 365 *CorporateEmailAddress* özelliğinde geçerli bir kullanıcı bulamazsa, öğe aktarılmaz.

10. **Sonraki'ye** tıklayın, ayarlarınızı gözden geçirip bağlayıcıyı oluşturmak **için** Son'a tıklayın.

11. Yeni bağlayıcı **için içeri aktarma** işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin. Bağlayıcı hakkında bilgi içeren çıkış sayfasını görüntülemek için bağlayıcıya tıklayın.

## <a name="set-up-a-connector-using-private-keys"></a>Özel tuşları kullanarak bağlayıcı ayarlama

Bu bölümdeki adımlar, PGP ve SSH özel tuşlarını kullanarak Bloomberg message bağlayıcısı ayarlamayı gösterir. Bu bağlayıcı kurulum seçeneği, özel anahtarlar kullanılarak zaten bir Bloomberg SFTP sitesi yapılandırmış olan kuruluşlara yöneliktir.

### <a name="step-1-obtain-an-ip-address-to-configure-the-bloomberg-sftp-site"></a>1. Adım: Bloomberg SFTP sitesini yapılandırmak için bir IP adresi alma

> [!NOTE]
> Organizasyonunız daha önce PGP ve SSH özel tuşlarını kullanarak Instant Bloomberg verilerini arşivlemek için bir Bloomberg SFTP sitesi yapılandırmışsa, başka bir site yapılandırmanız gerek değildir. 2. Adım'da bağlayıcıyı 2. adımda  oluşturdukken aynı SFTP sitesini belirtebilirsiniz.

Organizasyonunız Bloomberg SFTP sitesi ayarlamak için PGP ve SSH özel anahtarlarını kullandısa, BIR IP adresi edinip Bloomberg müşteri desteğine vermeniz gerekir. Bloomberg SFTP sitesi, bu IP adresi üzerinden bağlantı isteklerini kabul etmek üzere yapılandırıldı. Bloomberg Message bağlayıcısı tarafından SFTP sitesine bağlanmak ve Bloomberg Message verilerini Posta'ya aktarmak için aynı IP Microsoft 365.

IP adresini almak için:

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bloomberg **İletisi'nin** altındaki Veri **bağlayıcıları sayfasında Görünüm'e** **tıklayın**.

3. Bloomberg **İletisi ürün** açıklaması sayfasında Bağlayıcı ekle'ye **tıklayın**

4. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

5. İçerik kaynağı **için kimlik bilgileri ekle sayfasında** **PGP ve SSH özel anahtarlarını kullanmak istiyorum'a tıklayın**.

6. 1. adım altında, **IP adresi dosyasının bir** kopyasını yerel bilgisayarınıza kaydetmek için IP adresini indir'e tıklayın.

   ![IP adresini indirin.](../media/BloombergMessageConnectorIPAddress.png)

7. **İptal'e** tıklar ve sihirbazı kapatır. Bağlayıcıyı oluşturmak için 2. Adım'da bu sihirbaza dönersiniz.

Bloomberg SFTP adresinizi bu IP adresi üzerinden bağlantı isteklerini kabul etmek üzere yapılandırmak için Bloomberg müşteri desteğiyle birlikte çalışmanız gerekir. Yardım [için Bloomberg müşteri desteğine](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc) başvurun.

### <a name="step-2-create-a-bloomberg-message-connector"></a>2. Adım: Bloomberg İleti bağlayıcısı oluşturma

Bloomberg SFTP siteniz yapılandırıldıktan sonra, sıradaki adım bu sitede bir Bloomberg Message bağlayıcısı Microsoft 365 uyumluluk merkezi. Bağlayıcı, sizin sağlamakta olduğu bilgileri Bloomberg SFTP sitesine bağlanmak ve e-posta iletilerini, O365'te ilgili kullanıcı posta kutusu kutularına Microsoft 365. Bu adımı tamamlamak için Bloomberg SFTP siteniz için önceden ayarlanmış olan aynı özel anahtarların ve anahtar geçişlerinin kopyalarının olduğundan emin olun.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Bloomberg **İletisi'nin** altındaki Veri **bağlayıcıları sayfasında Görünüm'e** **tıklayın**.

3. Bloomberg **İletisi ürün** açıklaması sayfasında Bağlayıcı ekle'ye **tıklayın**

4. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

5. İçerik kaynağı **için kimlik bilgileri ekle sayfasında** **PGP ve SSH özel anahtarlarını kullanmak istiyorum'a tıklayın**.

   ![Özel anahtarlar kullanma seçeneğini belirtin.](../media/BloombergMessagePrivateKeysOption.png)

6. 3. Adım'ın altında, aşağıdaki kutulara gerekli bilgileri girin ve Bağlantıyı **doğrula'ya tıklayın**.

      - **Ad:** Bağlayıcının adı. Bunun, kurum içinde benzersiz olması gerekir.

      - **Firma kodu:** Bloomberg SFTP sitesinde kullanıcı adı olarak kullanılan, organizasyon kimlik.

      - **Parola:** Organizasyon un Bloomberg SFTP sitesi için parola.

      - **SFTP URL'SI:** Bloomberg SFTP sitesinin URL'si (örneğin, `sftp.bloomberg.com`). Bu değer için bir IP adresi de kullanabilirsiniz.

      - **SFTP bağlantı noktası:** Bloomberg SFTP sitesi bağlantı noktası numarası. Bağlayıcı bu bağlantı noktasını SFTP sitesine bağlanmak için kullanır.

      - **PGP özel anahtarı:** Bloomberg SFTP sitesi için PGP özel anahtarı. Anahtar bloğun başlangıç ve bitiş satırları da dahil olmak üzere tüm özel anahtar değerini dahil etmeye emin olun.

      - **PGP tuşu geçiş tümlesi:** PGP özel anahtarı için geçiş tümlesi.

      - **SSH özel anahtarı:** Bloomberg SFTP sitesi için SSH özel anahtarı. Anahtar bloğun başlangıç ve bitiş satırları da dahil olmak üzere tüm özel anahtar değerini dahil etmeye emin olun.

      - **SSH tuşu geçiş tümlesi:** SSH özel anahtarı için geçiş tümlesi.

7. Bağlantı başarıyla doğrulandıktan sonra, Sonraki'ne **tıklayın**.

8. Kullanıcı **tanımla sayfasında** , verilerini içeri aktar

     - **Kuruluş 2013'te çalışan tüm kullanıcılar**. Tüm kullanıcıların verilerini içeri aktar için bu seçeneği belirtin.

     - **Yalnızca Mahkeme tutmada olan kullanıcılar**. Yalnızca posta kutuları Mahkeme tutmada bulunan kullanıcılara ait verileri içeri aktarmayı bu seçeneği belirtin. Bu seçenek, verileri LitigationHoldEnabled özelliği True olarak ayarlanmış kullanıcı posta kutularına içeri aktarmaktadır. Daha fazla bilgi için [bkz. Mahkeme tutma oluşturma](create-a-litigation-hold.md).

9. Map **Bloomberg Message users to Microsoft 365 sayfasında**, otomatik kullanıcı eşlemesini etkinleştirin ve gerektiğinde özel kullanıcı eşlemesi sağlar.

   > [!NOTE]
   > Bağlayıcı ileti öğelerini belirli bir kullanıcının posta kutusuna içeri aktarıyor. Belirli bir kullanıcının posta **kutusunda BloombergMessage** adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, *CorporateEmailAddress özelliğinin değerini kullanarak* bunu yapar. Her sohbet iletisi bu özelliği içerir ve özellik, sohbet iletisi her katılımcının e-posta adresiyle doldurulur. *CorporateEmailAddress* özelliğinin değerini kullanarak otomatik kullanıcı eşlemeye ek olarak, CSV eşleme dosyasını karşıya yükerek özel eşleme de tanımlayabilirsiniz. Eşleme dosyası, her kullanıcı için Bloomberg UUID'sini Microsoft 365 posta kutusu adresini içerir. Otomatik kullanıcı eşlemesini etkinleştirir ve özel eşleme sağlarsanız, bağlayıcının önce özel eşleme dosyasına bakacak her ileti öğesi için özel eşlemesi olur. Kullanıcının Bloomberg UUID'sine karşılık gelen geçerli bir kullanıcı Microsoft 365 bulamazsa, bağlayıcıda sohbet *öğesinin CorporateEmailAddress* özelliği kullanılır. Bağlayıcı, özel eşleme dosyasında veya ileti Microsoft 365 *CorporateEmailAddress* özelliğinde geçerli bir kullanıcı bulamazsa, öğe aktarılmaz.

10. **Sonraki'ye** tıklayın, ayarlarınızı gözden geçirip bağlayıcıyı oluşturmak **için** Son'a tıklayın.

11. Yeni bağlayıcı **için içeri aktarma** işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin. Bağlayıcı hakkında bilgi içeren çıkış sayfasını görüntülemek için bağlayıcıya tıklayın.

## <a name="known-issues"></a>Bilinen sorunlar

- Bloomberg Message e-postalarının Microsoft 365 ileti dizileri desteklenmez. Bir kişiye gönderilen tek tek iletiler içe aktarılır, ancak bunlar bir zincir konuşmada gönderilmez. Microsoft, Bloomberg Message veri bağlayıcılarının sonraki sürümlerinde iş parçacığını desteklemeye çalışıyor.
