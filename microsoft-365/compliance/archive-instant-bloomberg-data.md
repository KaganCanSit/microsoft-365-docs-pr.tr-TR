---
title: Instant Bloomberg verilerini arşivlemek için bir bağlayıcı ayarlama
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
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Yöneticilerin Hızlı Bloomberg sohbet aracından Hızlı Bloomberg sohbet aracından içeri aktarma ve arşivlemek için veri bağlayıcısı ayarlamayı ve bu bağlayıcıyı Microsoft 365.
ms.openlocfilehash: 14495a219ce73b8d0cd4e937b4feae9aa2210da1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63313335"
---
# <a name="set-up-a-connector-to-archive-instant-bloomberg-data"></a>Instant Bloomberg verilerini arşivlemek için bir bağlayıcı ayarlama

Hızlı [Bloomberg](https://www.bloomberg.com/professional/product/collaboration/) işbirliği aracından Microsoft 365 uyumluluk merkezi hizmetleri sohbet verilerini içeri aktararak arşivlemek için iletişim araçlarında yerel bir bağlayıcı kullanın. Bağlayıcıyı ayardikten ve yapılandırdikten sonra, bağlayıcı her gün bir kez organizasyon un Bloomberg güvenli FTP sitesine (SFTP) bağlanır, sohbet iletilerinin içeriğini e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri Microsoft 365'ta posta kutularına içeri aktarıyor.

Instant Bloomberg verileri kullanıcı posta kutularında depo edildikten sonra, Instant Bloomberg verilerine Microsoft 365 Saklama, İçerik Araması, In-Place Arşivleme, Denetim, İletişim uyumluluğu Microsoft 365 bekletme ilkeleri gibi uyumluluk özelliklerini uygulayabilirsiniz. Örneğin, İçerik Arama'yu kullanarak Instant Bloomberg sohbet iletilerde arama veya Anlık Bloomberg verilerini içeren posta kutusunu bir özel durumunda özel bir Advanced eDiscovery ilişkilendirilebilirsiniz. Büyük bir kurumda verileri içeri aktararak ve arşivlenen bir Instant Bloomberg bağlayıcısı Microsoft 365, kurum kurum ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-instant-bloomberg-data"></a>Instant Bloomberg verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış makalesinde, Hızlı Bloomberg sohbet verilerini aynı anda arşivlemek için bağlayıcı kullanma Microsoft 365. 

![Instant Bloomberg içeri aktarma ve arşivleme işlemi.](../media/InstantBloombergDataArchiving.png)

1. Organizasyonunız Bloomberg SFTP sitesi ayarlamak için Bloomberg ile birlikte çalışır. Ayrıca, Sohbet mesajlarını Bloomberg SFTP sitenize kopyalayacak şekilde Bloomberg ile birlikte çalışırsınız.

2. Her 24 saatte bir, Instant Bloomberg'den gelen sohbet iletileri Bloomberg SFTP sitesine kopyalanır.

3. Microsoft 365 uyumluluk merkezi'ta oluşturdukları Instant Bloomberg bağlayıcısı her gün Bloomberg SFTP sitesine bağlanır ve önceki 24 saat içinde alınan sohbet mesajlarını Microsoft Bulut'ta güvenli bir Azure Depolama alanına aktarıyor. Ayrıca bağlayıcı, sohbet ileti iletisinde bir iletiye ileti içeriğini de dönüştürür.

4. Bağlayıcı, sohbet iletisi öğelerini belirli bir kullanıcının posta kutusuna içeri aktarıyor. Belirli bir kullanıcının posta kutusunda InstantBloomberg adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bunu *, CorporateEmailAddress özelliğinin değerini kullanarak* yapar. Her sohbet iletisi bu özelliği içerir; bu özellik, sohbet iletisi her katılımcının e-posta adresiyle doldurulur. *CorporateEmailAddress* özelliğinin değerini kullanarak otomatik kullanıcı eşlemeye ek olarak, CSV eşleme dosyasını karşıya yükerek özel eşleme de tanımlayabilirsiniz. Bu eşleme dosyası bir Bloomberg UUID'sini ve her kullanıcı için Microsoft 365 posta kutusu adresini içerir. Otomatik kullanıcı eşlemesini etkinleştirir ve özel eşleme sağlarsanız, bağlayıcı önce özel eşleme dosyasına bakar. Kullanıcının Bloomberg UUID'sine karşılık gelen geçerli bir kullanıcı Microsoft 365 bulamazsa, bağlayıcıda sohbet *öğesinin CorporateEmailAddress* özelliği kullanılır. Bağlayıcı özel eşleme dosyasında veya sohbet Microsoft 365 *CorporateEmailAddress* özelliğinde geçerli bir kullanıcı bulamazsa, öğe içe aktarılmaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

Instant Bloomberg verilerini arşivlemek için gereken bazı uygulama adımlarının Microsoft 365 dışıdır ve uyumluluk merkezinde bağlayıcı oluşturamadan önce tamamlanması gerekir.

- Anında Bloomberg bağlayıcısı ayarlamak için oldukça İyi Gizlilik (PGP) ve Güvenli Kabuk (SSH) için tuşları ve anahtar geçişlerini kullanasınız. Bu anahtarlar Bloomberg SFTP sitesini yapılandırmak için kullanılır ve bağlayıcı tarafından Bloomberg SFTP sitesine bağlanarak verileri bu siteye Microsoft 365. PGP anahtarı, Bloomberg SFTP sitesinden yeni bir siteye aktarılan verilerin şifrelemesi yapılandırmak için Microsoft 365. Bağlayıcı Bloomberg SFTP sitesine bağlandığında güvenli bir uzak oturum açma etkinleştirmek üzere güvenli kabuk yapılandırmak için SSH tuşu kullanılır.

  Bağlayıcıyı ayarlarken, Microsoft tarafından sağlanan ortak tuşları ve anahtar geçişlerini kullanma seçeneğiniz vardır veya kendi özel anahtarlarınızı ve geçiş tümcelerinizi kullanabilirsiniz. Microsoft tarafından sağlanan ortak anahtarları kullanmalarını öneririz. Ancak, organizasyonunız zaten özel anahtarları kullanarak Bloomberg SFTP sitesini yapılandırmışsa, aynı özel anahtarları kullanarak bir bağlayıcı oluşturabilirsiniz.

- Her Yerden [Bloomberg'e abone olun](https://www.bloomberg.com/professional/product/remote-access/?bbgsum-page=DG-WS-PROF-PROD-BBA). Bu, ayarlamak ve yapılandırmak istediğiniz Bloomberg SFTP sitesine erişmek için Her Yerden Bloomberg'de oturum açabilirsiniz.

- Bloomberg SFTP (Güvenli dosya aktarım protokolü) sitesi ayarlayın. SFTP sitesini ayarlamak için Bloomberg ile birlikte çalışıyorktan sonra, Instant Bloomberg'den gelen veriler her gün SFTP sitesine yükler. 2. Adımda oluşturan bağlayıcı bu SFTP sitesine bağlanır ve sohbet verilerini bu posta kutularına Microsoft 365 sağlar. SFTP ayrıca, aktarma işlemi sırasında posta kutularına gönderilen Instant Bloomberg sohbet verilerini de şifreler.

  Bloomberg *SFTP (BB-SFTP olarak da adlandırılan) hakkında bilgi için*:

  - Bloomberg Desteği'nde "SFTP Bağlantı Standartları" [belgesine bakın](https://www.bloomberg.com/professional/support/documentation/).

  - [Bloomberg müşteri desteği ile iletişime geçin](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc).

  Bloomberg ile birlikte bir SFTP sitesi ayarlamak için çalışıyorsanız, siz Bloomberg uygulama e-posta iletisine yanıt verdikten sonra Bloomberg size bazı bilgiler sağlayacaktır. Aşağıdaki bilgilerin bir kopyasını kaydedin. Bunu, 3. Adım'da bir bağlayıcı ayarlamak için kullanırsiniz.

  - Firma kodu, kuruluşun kimliğidir ve Bloomberg SFTP sitesinde oturum açmak için kullanılır.

  - Bloomberg SFTP sitenizin parolası

  - Bloomberg SFTP sitesinin URL'si (örneğin, sftp.bloomberg.com)

  - Bloomberg SFTP sitesi için bağlantı noktası numarası

- Instant Bloomberg bağlayıcısı, bir günde toplam 200.000 öğe içeri aktarabilirsiniz. SFTP sitesinde 200.000'den fazla öğe varsa, bu öğelerin hiçbiri Microsoft 365.

- 3. Adımda Instant Bloomberg bağlayıcısı oluşturan (ve 1. adımda ortak anahtarları ve IP adresini indiren kullanıcı) Veri Bağlayıcısı Yöneticisi rolüne atanmıştır. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="set-up-a-connector-using-public-keys"></a>Ortak tuşları kullanarak bağlayıcı ayarlama

Bu bölümdeki adımlar, Oldukça İyi Gizlilik (PGP) ve Güvenli Kabuk (SSH) için ortak anahtarları kullanarak Anında Bloomberg bağlayıcısı ayarlamayı gösterir.

### <a name="step-1-obtain-pgp-and-ssh-and-public-keys"></a>1. Adım: PGP ve SSH ve ortak anahtarlar alma

İlk adım, Oldukça İyi Gizlilik (PGP) ve Güvenli Kabuk (SSH) için ortak anahtarların bir kopyasını almaktır. 2. Adımda bu tuşları, Bloomberg SFTP sitesini, bağlayıcının (3. Adımda oluşturdukları) SFTP sitesine bağlanmasına ve Instant Bloomberg sohbet verilerini bu posta kutularına aktarmasına izin verecek şekilde Microsoft 365 kullanırsiniz. Bu adımda, Bloomberg SFTP sitesini yapılandırarak kullanabileceğiniz bir IP adresi de elde edebilirsiniz.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Anında **Çiçekler'in altındaki** Veri bağlayıcıları **sayfasında Görünüm'e** **tıklayın**.

3. Anında **Bloomberg ürün** açıklaması sayfasında Bağlayıcı **ekle'ye tıklayın**

4. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

5. İçerik kaynağı **için kimlik bilgileri ekle sayfasında** , Microsoft tarafından sağlanan **PGP ve SSH ortak anahtarlarını kullanmak istiyorum'a tıklayın**.

   ![Ortak tuşları kullanma seçeneğini belirtin.](../media/InstantBloombergPublicKeysOption.png)

6. 1. adımda, Her dosyanın bir kopyasını yerel bilgisayarınıza kaydetmek için **SSH** İndir, **PGP** anahtarını indir ve **IP** adresi bağlantılarını indir bağlantılarına tıklayın.

   ![Genel anahtarları ve IP adresini indirmek için bağlantılar.](../media/InstantBloombergPublicKeyDownloadLinks.png)

   Bu dosyalar, 2. Adımda Bloomberg SFTP sitesini yapılandırmak için kullanılan aşağıdaki öğeleri içerir:

   - PGP ortak anahtarı: Bu anahtar, Bloomberg SFTP sitesinden Bloomberg SFTP sitesinden yeni bir siteye aktarılan verilerin şifrelemesi Microsoft 365.

   - SSH ortak anahtarı: Bu anahtar, bağlayıcı Bloomberg SFTP sitesine bağlandığında güvenli bir uzak oturum açma etkinleştirmek üzere güvenli kabuk yapılandırmak için kullanılır.

   - IP adresi: Bloomberg SFTP sitesi, bu IP adresi üzerinden bağlantı isteklerini kabul etmek üzere yapılandırılmıştır. Aynı IP adresi Instant Bloomberg bağlayıcısı tarafından SFTP sitesine bağlanmak ve Instant Bloomberg verilerini Hızlı Erişim'e Microsoft 365.

7. **İptal'e** tıklar ve sihirbazı kapatır. Bağlayıcıyı oluşturmak için 3. adımda bu sihirbaza dönersiniz.

### <a name="step-2-configure-the-bloomberg-sftp-site"></a>2. Adım: Bloomberg SFTP sitesini yapılandırma

Sonraki adım, PGP ve SSH ortak tuşlarını ve 1. Adımda edinilen IP adresini KULLANARAK BLOOMberg SFTP sitesi için PGP şifrelemesini ve SSH kimlik doğrulamasını yapılandırmaktır. Bu, 3. Adımda açtığınız Instant Bloomberg bağlayıcının Bloomberg SFTP sitesine bağlanmalarını ve Instant Bloomberg verilerini Anında Bloomberg'e aktarmalarını Microsoft 365. Bloomberg SFTP sitesinizi ayarlamak için Bloomberg müşteri desteğiyle birlikte çalışmanız gerekir. Yardım [için Bloomberg müşteri desteğine](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc) başvurun. 

> [!IMPORTANT]
> Bloomberg, 1. Adımda indirdiğiniz üç dosyayı bir e-posta iletisine eklemenizi ve Bloomberg SFTP adresinizi ayarlamak için bu dosya üzerinde birlikte çalışırken müşteri destek ekibine göndermenizi önermektedir.

### <a name="step-3-create-an-instant-bloomberg-connector"></a>3. Adım: Anında Bloomberg bağlayıcısı oluşturma

Son adım, bu bağlantıda bir Instant Bloomberg bağlayıcısı Microsoft 365 uyumluluk merkezi. Bağlayıcı, sizin sağlamakta olduğu bilgileri Bloomberg SFTP sitesine bağlanmak ve sohbet mesajlarını iletişim kutusunda ilgili kullanıcı posta kutusu kutularına Microsoft 365.

1. Veri bağlayıcılarıInstant <https://compliance.microsoft.com>  > **Bloomberg'e gidin ve tıklayın**.

2. Anında **Bloomberg ürün** açıklaması sayfasında Bağlayıcı **ekle'ye tıklayın**

3. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

4. **Bloomberg SFTP sitesi** için kimlik bilgileri ekle sayfasında, 3. Adım'ın altında aşağıdaki kutulara gerekli bilgileri girin ve ardından Sonraki'ye **tıklayın**.

    - **Firma kodu:** Bloomberg SFTP sitesinde kullanıcı adı olarak kullanılan, organizasyon kimlik.

    - **Parola:** Bloomberg SFTP sitesi parolası.

    - **SFTP URL'SI:** Bloomberg SFTP sitesinin URL'si (örneğin, `sftp.bloomberg.com`). Bu değer için bir IP adresi de kullanabilirsiniz.

    - **SFTP bağlantı noktası:** Bloomberg SFTP sitesi bağlantı noktası numarası. Bağlayıcı bu bağlantı noktasını SFTP sitesine bağlanmak için kullanır.

5. İçeri **aktaracak veri türlerini seçin sayfasında** , İletiler'den ayrı olarak içeri aktaracak gerekli veri türlerini **seçin**

6. Hızlı **Bloomberg kullanıcılarını Yeni kullanıcılarla eşleme Microsoft 365**, otomatik kullanıcı eşlemesini etkinleştirin ve gerektiğinde özel kullanıcı eşlemesi sağlama

   > [!NOTE]
   > Bağlayıcı, sohbet iletisi öğelerini belirli bir kullanıcının posta kutusuna içeri aktarıyor. Belirli bir kullanıcının posta **kutusunda InstantBloomberg** adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, *CorporateEmailAddress özelliğinin değerini kullanarak* bunu yapar. Her sohbet iletisi bu özelliği içerir ve özellik, sohbet iletisi her katılımcının e-posta adresiyle doldurulur. *CorporateEmailAddress* özelliğinin değerini kullanarak otomatik kullanıcı eşlemeye ek olarak, CSV eşleme dosyasını karşıya yükerek özel eşleme de tanımlayabilirsiniz. Eşleme dosyası, her kullanıcı için Bloomberg UUID'sini Microsoft 365 posta kutusu adresini içerir. Otomatik kullanıcı eşlemesini etkinleştirir ve özel eşleme sağlarsanız, bağlayıcının önce özel eşleme dosyasına bakacak her sohbet öğesi için özel eşleme dosyası görüntüler. Kullanıcının Bloomberg UUID'sine karşılık gelen geçerli bir kullanıcı Microsoft 365 bulamazsa, bağlayıcıda sohbet *öğesinin CorporateEmailAddress* özelliği kullanılır. Bağlayıcı, özel eşleme dosyasında veya Microsoft 365 öğenin *CorporateEmailAddress* özelliğinde geçerli bir kullanıcı bulamazsa, öğe aktarılmaz.

7. **Sonraki'ye** tıklayın, ayarlarınızı gözden geçirip bağlayıcıyı oluşturmak **için** Son'a tıklayın.

8. Yeni bağlayıcı **için içeri aktarma** işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin. Bağlayıcı hakkında bilgi içeren çıkış sayfasını görüntülemek için bağlayıcıya tıklayın.

## <a name="set-up-a-connector-using-private-keys"></a>Özel tuşları kullanarak bağlayıcı ayarlama

Bu bölümdeki adımlar, PGP ve SSH özel tuşlarını kullanarak Anında Bloomberg bağlayıcısı ayarlamayı gösterir. Bu bağlayıcı kurulum seçeneği, özel anahtarlar kullanılarak zaten bir Bloomberg SFTP sitesi yapılandırmış olan kuruluşlara yöneliktir.

### <a name="step-1-obtain-an-ip-address-to-configure-the-bloomberg-sftp-site"></a>1. Adım: Bloomberg SFTP sitesini yapılandırmak için bir IP adresi alma

> [!NOTE]
> Organizasyonunız daha önce PGP ve SSH özel tuşlarını kullanarak Bloomberg Message verilerini arşivlemek için Bloomberg SFTP sitesini yapılandırmışsa, başka bir site yapılandırmanız gerek değildir. 2. Adım'da bağlayıcıyı 2. adımda  oluşturdukken aynı SFTP sitesini belirtebilirsiniz.

Organizasyonunız Bloomberg SFTP sitesi ayarlamak için PGP ve SSH özel anahtarlarını kullandısa, BIR IP adresi edinip Bloomberg müşteri desteğine vermeniz gerekir. Bloomberg SFTP sitesi, bu IP adresi üzerinden bağlantı isteklerini kabul etmek üzere yapılandırıldı. Aynı IP adresi Instant Bloomberg bağlayıcısı tarafından SFTP sitesine bağlanmak ve Instant Bloomberg verilerini Hızlı Erişim'e Microsoft 365.

IP adresini almak için:

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Anında **Çiçekler'in altındaki** Veri bağlayıcıları **sayfasında Görünüm'e** **tıklayın**.

3. Anında **Bloomberg ürün** açıklaması sayfasında Bağlayıcı **ekle'ye tıklayın**

4. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

5. İçerik kaynağı **için kimlik bilgileri ekle sayfasında** **PGP ve SSH özel anahtarlarını kullanmak istiyorum'a tıklayın**.

6. 1. adım altında, **IP adresi dosyasının bir** kopyasını yerel bilgisayarınıza kaydetmek için IP adresini indir'e tıklayın.

   ![IP adresini indirin.](../media/InstantBloombergConnectorIPAddress.png)

7. **İptal'e** tıklar ve sihirbazı kapatır. Bağlayıcıyı oluşturmak için 2. Adım'da bu sihirbaza dönersiniz.

Bloomberg SFTP adresinizi bu IP adresi üzerinden bağlantı isteklerini kabul etmek üzere yapılandırmak için Bloomberg müşteri desteğiyle birlikte çalışmanız gerekir. Yardım [için Bloomberg müşteri desteğine](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc) başvurun.

### <a name="step-2-create-an-instant-bloomberg-connector"></a>2. Adım: Anında Bloomberg bağlayıcısı oluşturma

Bloomberg SFTP siteniz yapılandırıldıktan sonra, sıradaki adım bu bağlantıda hızlı bir Bloomberg bağlayıcısı Microsoft 365 uyumluluk merkezi. Bağlayıcı, sizin sağlamakta olduğu bilgileri Bloomberg SFTP sitesine bağlanmak ve e-posta iletilerini, O365'te ilgili kullanıcı posta kutusu kutularına Microsoft 365. Bu adımı tamamlamak için Bloomberg SFTP siteniz için önceden ayarlanmış olan aynı özel anahtarların ve anahtar geçişlerinin kopyalarının olduğundan emin olun.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. Anında **Çiçekler'in altındaki** Veri bağlayıcıları **sayfasında Görünüm'e** **tıklayın**.

3. Anında **Bloomberg ürün** açıklaması sayfasında Bağlayıcı **ekle'ye tıklayın**

4. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

5. İçerik kaynağı **için kimlik bilgileri ekle sayfasında** **PGP ve SSH özel anahtarlarını kullanmak istiyorum'a tıklayın**.

   ![Özel anahtarlar kullanma seçeneğini belirtin.](../media/InstantBloombergPrivateKeysOption.png)

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

8. Hızlı **Bloomberg kullanıcılarını Harita Microsoft 365 sayfasında** otomatik kullanıcı eşlemesini etkinleştirin ve gerektiğinde özel kullanıcı eşlemesi sağlar.

   > [!NOTE]
   > Bağlayıcı, sohbet iletisi öğelerini belirli bir kullanıcının posta kutusuna içeri aktarıyor. Belirli bir kullanıcının posta **kutusunda InstantBloomberg** adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, *CorporateEmailAddress özelliğinin değerini kullanarak* bunu yapar. Her sohbet iletisi bu özelliği içerir ve özellik, sohbet iletisi her katılımcının e-posta adresiyle doldurulur. *CorporateEmailAddress* özelliğinin değerini kullanarak otomatik kullanıcı eşlemeye ek olarak, CSV eşleme dosyasını karşıya yükerek özel eşleme de tanımlayabilirsiniz. Eşleme dosyası, her kullanıcı için Bloomberg UUID'sini Microsoft 365 posta kutusu adresini içerir. Otomatik kullanıcı eşlemesini etkinleştirir ve özel eşleme sağlarsanız, bağlayıcının önce özel eşleme dosyasına bakacak her sohbet öğesi için özel eşleme dosyası görüntüler. Kullanıcının Bloomberg UUID'sine karşılık gelen geçerli bir kullanıcı Microsoft 365 bulamazsa, bağlayıcıda sohbet *öğesinin CorporateEmailAddress* özelliği kullanılır. Bağlayıcı, özel eşleme dosyasında veya Microsoft 365 öğenin *CorporateEmailAddress* özelliğinde geçerli bir kullanıcı bulamazsa, öğe aktarılmaz.

9. **Sonraki'ye** tıklayın, ayarlarınızı gözden geçirip bağlayıcıyı oluşturmak **için** Son'a tıklayın.

10. Yeni bağlayıcı **için içeri aktarma** işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin. Bağlayıcı hakkında bilgi içeren çıkış sayfasını görüntülemek için bağlayıcıya tıklayın.
