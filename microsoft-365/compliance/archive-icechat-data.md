---
title: ICE Sohbet verilerini arşivlemek için bağlayıcı ayarlama
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
description: Yöneticiler, ICE Sohbet aracından verileri içeri aktaracak ve burada arşiv olacak şekilde bir bağlayıcı Microsoft 365. Bu, üçüncü taraf veri kaynaklarından verileri Microsoft 365'te arşivlemenize olanak sağlar ve böylece yasal saklama, içerik araması ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanarak kuruluş üçüncü taraf verilerini yönetebilirsiniz.
ms.openlocfilehash: c29a39c8c398a0d8721931cbcb770aa18d0f3c4b
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64568104"
---
# <a name="set-up-a-connector-to-archive-ice-chat-data"></a>ICE Sohbet verilerini arşivlemek için bağlayıcı ayarlama

BUZ Sohbeti işbirliği aracından Microsoft 365 uyumluluk merkezi hizmetleri sohbet verilerini içeri aktarma ve arşivlemek için belge içinde yerel bir bağlayıcı kullanın. Bağlayıcıyı ayardikten ve yapılandırdikten sonra, bağlayıcı, her gün, organizasyon un ICE Chat güvenli FTP (SFTP) sitesine bağlanır, sohbet iletilerinin içeriğini e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri Microsoft 365'ta posta kutularına içeri aktarın.

ICE sohbet verileri kullanıcı posta kutularında depolandıktan sonra, ICE Sohbeti verilerine mahkeme Microsoft 365 saklama, eBulma, arşivleme, denetim, iletişim uyumluluğu ve Microsoft 365 bekletme ilkeleri gibi uyumluluk özelliklerini uygulayabilirsiniz. Örneğin, içerik arama kullanarak BUZ Sohbeti iletisinde arama veya BUZ Sohbeti verilerini içeren posta kutusunu bir özel olayda bir özel dosyayla Advanced eDiscovery edebilirsiniz. Verileri kendi dosyalarında içeri aktararak ve arşiv Microsoft 365 bir ICE Sohbet bağlayıcısı kullanarak, organizasyonsunuz devlet ve mevzuat ilkeleriyle uyumlu kalmalarına yardımcı olabilir.

## <a name="overview-of-archiving-ice-chat-data"></a>ICE Sohbet verilerini arşivlemeye genel bakış

Aşağıdaki genel bakış, bir bağlayıcı kullanarak BUZ sohbeti verilerini hızlı bir şekilde arşivleme Microsoft 365.

![ICE Sohbeti arşivleme iş akışı.](../media/ICEChatConnectorWorkflow.png)

1. Organizasyon, bir ICE Sohbeti SFTP sitesi ayarlamak için ICE Sohbeti ile çalışır. Ayrıca, ICE Sohbeti'yi, sohbet iletilerini ICE SohbetI SFTP sitenize kopyalayıp kopyalamak için ICE Sohbeti'ne de çalışırsınız.

2. HER 24 saatte bir, ICE Sohbeti'den gelen sohbet iletileri ICE SohbetI SFTP sitenize kopyalanır.

3. Microsoft 365 uyumluluk merkezi'ta oluşturdukları ICE Sohbeti bağlayıcısı her gün ICE SohbetI SFTP sitesine bağlanır ve önceki 24 saat içinde alınan sohbet iletilerini Microsoft bulutunda güvenli bir Azure Depolama konuma aktarıyor. Ayrıca bağlayıcı, sohbet ileti iletisinde bir iletiye ileti içeriğini de dönüştürür.

4. Bağlayıcı, sohbet iletisi öğelerini belirli kullanıcıların posta kutularına içeri aktarıyor. Kullanıcı posta **kutularında BUZ** Sohbeti adlı yeni bir klasör oluşturulur ve sohbet iletisi öğeleri bu klasöre aktarılır. Bağlayıcı, *SenderEmail ve RecipientEmail özelliklerinin* *değerini kullanarak* bunu yapar. Her sohbet iletisi bu özellikleri içerir; bu özellikler, sohbet iletisi gönderenin e-posta adresiyle ve sohbet iletisi alıcılarının/katılımcılarının her biri ile doldurulur.

   *SenderEmail* ve *RecipientEmail* özelliğinin değerlerini kullanan otomatik kullanıcı eşlemeye ek olarak (bu, bağlayıcının sohbet mesajını gönderenin posta kutusuna ve her alıcının posta kutularına aktar olduğu anlamına gelir), CSV eşleme dosyası yükerek özel kullanıcı eşlemesi de tanımlayabilirsiniz. Bu eşleme dosyası, ICE *Sohbeti ImId'sini* ve Microsoft 365 her kullanıcı için ilgili posta kutusu adresini içerir. Otomatik kullanıcı eşlemeyi etkinleştirir ve özel eşleme dosyası sağlarsanız, bağlayıcının önce özel eşleme dosyasına bakacak her sohbet öğesi için bir özel eşleme dosyası görüntüler. Kullanıcının BUZ Sohbeti ImId'sine karşılık gelen geçerli bir Microsoft 365 kullanıcı hesabı bulamazsa bağlayıcı, öğeyi sohbet katılımcılarının posta kutularına içeri aktarmak için sohbet öğesinin *SenderEmail* ve *RecipientEmail* özelliklerini kullanır. Bağlayıcı, özel eşleme dosyasında veya *SenderEmail* Microsoft 365 *RecipientEmail* özelliklerinde geçerli bir kullanıcı bulamazsa, öğe aktarılmaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

ICE Sohbet verilerini arşivlemek için gereken bazı uygulama adımları, Microsoft 365 dışındadır ve uyumluluk merkezinde bağlayıcı oluşturamadan önce tamamlanması gerekir.

- ICE Chat, dış uyumluluk nedeniyle müşterilerinin ücretlerini ücretle karşılar. Bunun için, organizasyon kuruluşlarının BUZ Sohbeti satış grubuyla iletişime geçerek, buz Sohbeti veri hizmetleri sözleşmesi imzalaması gerekir. Bu sözleşmeyi burada edinebilirsiniz [https://www.theice.com/publicdocs/agreements/ICE\_Data\_Services\_Agreement.pdf](https://www.theice.com/publicdocs/agreements/ICE\_Data\_Services\_Agreement.pdf). Bu sözleşme, ICE Sohbeti ile organizasyon arasında yer alan ve Microsoft'u içermeyentir. 2. Adımda bir ICE SohbetI SFTP sitesi ayarlandıktan sonra, ICE Sohbeti, FTP kimlik bilgilerini doğrudan kuruluşa sağlar. Ardından, 3. Adımda bağlayıcıyı ayarlarken bu kimlik bilgilerini Microsoft'a sağlayacak kişisiniz.

- 3. Adımda bağlayıcıyı oluşturmadan önce bir ICE Chat SFTP sitesi ayarlayabilirsiniz. SFTP sitesini ayarlamak için ICE Sohbeti ile birlikte çalışıyorktan sonra, ICE Sohbeti'ne gelen veriler her gün SFTP sitesine yükler. 3. Adımda oluşturan bağlayıcı bu SFTP sitesine bağlanır ve sohbet verilerini bu posta Microsoft 365 aktarıyor. SFTP, aktarma işlemi sırasında posta kutularına gönderilen ICE Sohbeti verilerini de şifreler.

- BIR ICE Sohbet bağlayıcısı ayarlamak için oldukça İyi Gizlilik (PGP) ve Güvenli Kabuk (SSH) için tuşları ve tuş geçişlerini kullanasınız. Bu tuşlar, ICE SohbetI SFTP sitesini yapılandırmak için kullanılır ve bağlayıcı tarafından ICE Chat SFTP sitesine bağlanarak verileri buz sohbeti SFTP sitesine Microsoft 365. PGP anahtarı, ICE Chat SFTP sitesinden yeni bir siteye aktarılan verilerin şifrelemesi Microsoft 365. SSH tuşu, bağlayıcı ICE Sohbeti SFTP sitesine bağlandığında güvenli bir uzak oturum açma etkinleştirmek üzere güvenli kabuğu yapılandırmak için kullanılır.

  Bağlayıcıyı ayarlarken, Microsoft tarafından sağlanan ortak tuşları ve anahtar geçişlerini kullanma seçeneğiniz vardır veya kendi özel anahtarlarınızı ve geçiş tümcelerinizi kullanabilirsiniz. Microsoft tarafından sağlanan ortak anahtarları kullanmalarını öneririz. Ancak, organizasyonunız özel tuşları kullanarak bir ICE SohbetI SFTP sitesini zaten yapılandırmışsa, aynı özel anahtarları kullanarak bir bağlayıcı oluşturabilirsiniz.

- ICE Chat bağlayıcısı, bir günde toplam 200.000 öğe içeri aktarabilirsiniz. SFTP sitesinde 200.000'den fazla öğe varsa, bu öğelerin hiçbiri Microsoft 365.

- 3. Adımda ICE Sohbet bağlayıcısını oluşturan (ve 1. Adımda ortak anahtarları ve IP adresini indiren yönetici) Veri Bağlayıcısı Yöneticisi rolüne atanmış olması gerekir. Bu rol, sayfanın en son veri **bağlayıcıları sayfasına bağlayıcı** eklemek Microsoft 365 uyumluluk merkezi. Bu rol varsayılan olarak birden çok rol gruplarına eklenir. Bu rol gruplarının listesi için, Güvenlik ve Uyumluluk Merkezi'nde İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki roller" [& bakın](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center). Alternatif olarak, bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolü ata sonrasında uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için aşağıdaki İzinler bölümündeki "Özel bir rol grubu oluşturma" [bölümüne Microsoft 365 uyumluluk merkezi](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group).

## <a name="set-up-a-connector-using-public-keys"></a>Ortak tuşları kullanarak bağlayıcı ayarlama

Bu bölümdeki adımlar, Oldukça İyi Gizlilik (PGP) ve Güvenli Kabuk (SSH) için ortak anahtarları kullanarak bir ICE Sohbet bağlayıcısı ayarlamayı gösterir.

### <a name="step-1-obtain-pgp-and-ssh-public-keys"></a>1. Adım: PGP ve SSH ortak anahtarlarını alma

İlk adım, Oldukça İyi Gizlilik (PGP) ve Güvenli Kabuk (SSH) için ortak anahtarların bir kopyasını almaktır. 2. Adımda bu tuşları, ICE Sohbeti SFTP sitesini, bağlayıcının (3. Adımda oluşturdukları) SFTP sitesine bağlanmasına ve ICE Sohbeti verilerini bu posta kutularına aktarmasına izin verecek şekilde Microsoft 365 kullanırsiniz. Ayrıca, ICE SohbetI SFTP sitesini yapılandırarak bu adımda bir IP adresi edinebilirsiniz.

1. Sol gezinti [https://compliance.microsoft.com](https://compliance.microsoft.com) çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. BUZ **Sohbeti altındaki Veri bağlayıcıları** **sayfasında Görünüm'e** **tıklayın**.

3. ICE Sohbet **sayfasında Bağlayıcı** **ekle'ye tıklayın**.

4. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

5. İçerik kaynağı **için kimlik bilgileri ekle sayfasında** , Microsoft tarafından sağlanan **PGP ve SSH ortak anahtarlarını kullanmak istiyorum'a tıklayın**.

   ![Ortak tuşları kullanma seçeneğini belirtin.](../media/ICEChatPublicKeysOption.png)

6. 1. adımda, Her dosyanın bir kopyasını yerel bilgisayarınıza kaydetmek için **SSH** İndir, **PGP** anahtarını indir ve **IP** adresi bağlantılarını indir bağlantılarına tıklayın.

   ![Genel anahtarları ve IP adresini indirmek için bağlantılar.](../media/ICEChatPublicKeyDownloadLinks.png)

   Bu dosyalar, 2. Adımda ICE Chat SFTP sitesini yapılandırmak için kullanılan aşağıdaki öğeleri içerir:

   - PGP genel anahtarı: Bu anahtar, ICE Chat SFTP sitesinden havale edilen verilerin şifrelemesi yapılandırıldığında, Microsoft 365.

   - SSH ortak anahtarı: Bu anahtar, bağlayıcı ICE Chat SFTP sitesine bağlandığında güvenli bir uzaktan oturum açma etkinleştirmek üzere Güvenli SSH'yi yapılandırmak için kullanılır.

   - IP adresi: ICE SohbetIFTP sitesi, yalnızca 3. Adımda oluşturmış olunan BUZ Sohbeti bağlayıcısı tarafından kullanılan bu IP adresiyle bağlantı isteğini kabul etmek üzere yapılandırılır.

7. **İptal'e** tıklar ve sihirbazı kapatır. Bağlayıcıyı oluşturmak için 3. adımda bu sihirbaza dönersiniz.

### <a name="step-2-configure-the-ice-chat-sftp-site"></a>2. Adım: ICE SohbetI SFTP sitesini yapılandırma

Sonraki adım, ICE Chat SFTP sitesi için PGP şifrelemesini ve SSH kimlik doğrulamasını yapılandırmak için 1. Adımda edinilen PGP ve SSH ortak tuşlarını ve IP adresini kullanmaktır. Bu, 3. Adımda oluşturdukları ICE Sohbeti bağlayıcının ICE SohbetI SFTP sitesine bağlanmalarını ve ICE Sohbeti verilerini bu siteye aktarmalarını Microsoft 365. ICE Chat SFTP sitesini ayarlamak için ICE Chat müşteri desteğiyle birlikte çalışmanız gerekir.

### <a name="step-3-create-an-ice-chat-connector"></a>3. Adım: ICE Sohbet bağlayıcısı oluşturma

Son adım, ağ bağlantılarında bir BUZ Sohbeti bağlayıcısı Microsoft 365 uyumluluk merkezi. Bağlayıcı, buz Sohbeti SFTP sitesine bağlanmak ve sohbet iletilerini bu alanda ilgili kullanıcı posta kutusu kutularına aktarmak için Microsoft 365.

1. Sol gezinti [https://compliance.microsoft.com](https://compliance.microsoft.com) çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. BUZ **Sohbeti altındaki Veri bağlayıcıları** **sayfasında Görünüm'e** **tıklayın**.

3. ICE Sohbet **sayfasında Bağlayıcı** **ekle'ye tıklayın**.

4. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

5. İçerik kaynağı **için kimlik bilgileri ekle sayfasında** **PGP ve SSH ortak anahtarlarını kullanmak istiyorum'a tıklayın**.

6. 3. Adım'ın altında, aşağıdaki kutulara gerekli bilgileri girin ve Bağlantıyı **doğrula'ya tıklayın**.

   - **Firma kodu:** ICE Chat SFTP sitesinde kullanıcı adı olarak kullanılan, organizasyon kimlik.

   - **Parola:** ICE Chat SFTP sitenizin parolası.

   - **SFTP URL'SI:** ICE SohbetI SFTP sitesinin URL'si (örneğin, `sftp.theice.com`). Bu değer için bir IP adresi de kullanabilirsiniz.

   - **SFTP bağlantı noktası:** ICE Chat SFTP sitesi için bağlantı noktası numarası. Bağlayıcı bu bağlantı noktasını SFTP sitesine bağlanmak için kullanır.

7. Bağlantı başarıyla doğrulandıktan sonra, Sonraki'ne **tıklayın**.

8. Kullanıcı **tanımla sayfasında** , verileri içeri aktarıla kullanıcıları belirtin.

     - **Kuruluş 2013'te çalışan tüm kullanıcılar**. Tüm kullanıcıların verilerini içeri aktar için bu seçeneği belirtin.

     - **Yalnızca Mahkeme tutmada olan kullanıcılar**. Yalnızca posta kutuları Mahkeme tutmada bulunan kullanıcılara ait verileri içeri aktarmayı bu seçeneği belirtin. Bu seçenek, verileri LitigationHoldEnabled özelliği True olarak ayarlanmış kullanıcı posta kutularına içeri aktarmaktadır. Daha fazla bilgi için [bkz. Mahkeme tutma oluşturma](create-a-litigation-hold.md).

9. Dış kullanıcıları **kullanıcı eşleme Microsoft 365,** otomatik kullanıcı eşlemesini etkinleştirin ve gerektiğinde özel kullanıcı eşlemesi sağlar. Bu sayfada, kullanıcı eşleme CSV dosyasının bir kopyasını indirebilirsiniz. Dosyaya kullanıcı eşlemeleri ekleyebilir ve sonra dosyayı karşıya yükleyebilirsiniz.

   > [!NOTE]
   > Daha önce de açıklaması olan özel eşleme dosyası CSV dosyası, HER kullanıcı için ICE Sohbeti imid'ini ve Microsoft 365 posta kutusu adresini içerir. Otomatik kullanıcı eşlemesini etkinleştirir ve her sohbet öğesi için özel bir eşleme sağlarsanız, bağlayıcı önce özel eşleme dosyasına bakar. Kullanıcının ICE Chat imid'ine karşılık gelen geçerli bir Microsoft 365 kullanıcısı bulamazsa bağlayıcı, öğeyi sohbet öğesinin *SenderEmail* ve *RecipientEmail* özelliklerinde belirtilen kullanıcıların posta kutularına aktaracak. Bağlayıcı, otomatik veya özel kullanıcı eşlemesi Microsoft 365 geçerli bir kullanıcı bulamazsa, öğe aktarılmaz.

10. **Sonraki'ye** tıklayın, ayarlarınızı gözden geçirip bağlayıcıyı oluşturmak **için** Son'a tıklayın.

11. Yeni bağlayıcı **için içeri aktarma** işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin.

## <a name="set-up-a-connector-using-private-keys"></a>Özel tuşları kullanarak bağlayıcı ayarlama

Bu bölümdeki adımlar, PGP ve SSH özel tuşlarını kullanarak bir ICE Sohbet bağlayıcısı ayarlamayı gösterir. Bu bağlayıcı kurulum seçeneği, özel anahtarlar kullanılarak zaten bir ICE Chat SFTP sitesi yapılandırmış olan kuruluşlara yöneliktir.

### <a name="step-1-obtain-an-ip-address-to-configure-the-ice-chat-sftp-site"></a>1. Adım: ICE SohbetI SFTP sitesini yapılandırmak için bir IP adresi alma

Organizasyonunız ICE Chat SFTP sitesi ayarlamak için PGP ve SSH özel anahtarlarını kullandısa, bir IP adresi edinip ICE Sohbeti müşteri desteğine sağlamanız gerekir. ICE Chat SFTP sitesi, bu IP adresi üzerinden bağlantı isteklerini kabul etmek üzere yapılandırıldı. ICE Sohbet bağlayıcısı tarafından SFTP sitesine bağlanmak ve ICE Sohbeti verilerini bu siteye aktarımı için aynı IP adresi Microsoft 365.

IP adresini almak için:

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. BUZ **Sohbeti altındaki Veri bağlayıcıları** **sayfasında Görünüm'e** **tıklayın**.

3. ICE **Sohbeti ürün** açıklaması sayfasında Bağlayıcı **ekle'ye tıklayın**

4. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

5. İçerik kaynağı **için kimlik bilgileri ekle sayfasında** **PGP ve SSH özel anahtarlarını kullanmak istiyorum'a tıklayın**.

   ![Özel anahtarlar kullanma seçeneğini belirtin.](../media/ICEChatPrivateKeysOption.png)

6. 1. adım altında, **IP adresi dosyasının bir** kopyasını yerel bilgisayarınıza kaydetmek için IP adresini indir'e tıklayın.

   ![IP adresini indirin.](../media/ICEChatConnectorIPAddress.png)

7. **İptal'e** tıklar ve sihirbazı kapatır. Bağlayıcıyı oluşturmak için 2. Adım'da bu sihirbaza dönersiniz.

ICE Chat SFTP adresinizi bu IP adresi üzerinden bağlantı isteklerini kabul etmek üzere yapılandırmak için ICE Sohbet müşteri desteğiyle birlikte çalışmanız gerekir.

### <a name="step-2-create-an-ice-chat-connector"></a>2. Adım: ICE Sohbet bağlayıcısı oluşturma

ICE Chat SFTP siteniz yapılandırıldıktan sonra, sonraki adım bu sitede bir BUZ Sohbeti bağlayıcısı Microsoft 365 uyumluluk merkezi. Bağlayıcı, buz Sohbeti SFTP sitesine bağlanmak ve e-posta iletilerini bu alanda ilgili kullanıcı posta kutusu kutularına aktarımı için Microsoft 365. Bu adımı tamamlamak için, ICE Chat SFTP siteniz için ayar yapmak üzere kullanılan aynı özel anahtarların ve anahtar geçişlerinin kopyalarının olduğundan emin olun.

1. Sol gezinti <https://compliance.microsoft.com> çubuğunda **Veri bağlayıcıları'na** gidin ve bu bağlayıcılara tıklayın.

2. BUZ **Sohbeti altındaki Veri bağlayıcıları** **sayfasında Görünüm'e** **tıklayın**.

3. ICE **Sohbeti ürün** açıklaması sayfasında Bağlayıcı **ekle'ye tıklayın**

4. Hizmet Koşulları **sayfasında Kabul Et'e** **tıklayın**.

5. İçerik kaynağı **için kimlik bilgileri ekle sayfasında** **PGP ve SSH özel anahtarlarını kullanmak istiyorum'a tıklayın**.

6. 3. Adım'ın altında, aşağıdaki kutulara gerekli bilgileri girin ve Bağlantıyı **doğrula'ya tıklayın**.

      - **Ad:** Bağlayıcının adı. Bunun, kurum içinde benzersiz olması gerekir.

      - **Firma kodu:** ICE Chat SFTP sitesinde kullanıcı adı olarak kullanılan, organizasyon kimlik.

      - **Parola:** Kuruluşun ICE SohbetI SFTP sitesi için parola.

      - **SFTP URL'SI:** ICE SohbetI SFTP sitesinin URL'si (örneğin, `sftp.theice.com`). Bu değer için bir IP adresi de kullanabilirsiniz.

      - **SFTP bağlantı noktası:** ICE Chat SFTP sitesi için bağlantı noktası numarası. Bağlayıcı bu bağlantı noktasını SFTP sitesine bağlanmak için kullanır.

      - **PGP özel anahtarı:** ICE Chat SFTP sitesi için PGP özel anahtarı. Anahtar bloğun başlangıç ve bitiş satırları da dahil olmak üzere tüm özel anahtar değerini dahil etmeye emin olun.

      - **PGP tuşu geçiş tümlesi:** PGP özel anahtarı için geçiş tümlesi.

      - **SSH özel anahtarı:** ICE Chat SFTP sitesi için SSH özel anahtarı. Anahtar bloğun başlangıç ve bitiş satırları da dahil olmak üzere tüm özel anahtar değerini dahil etmeye emin olun.

      - **SSH tuşu geçiş tümlesi:** SSH özel anahtarı için geçiş tümlesi.

7. Bağlantı başarıyla doğrulandıktan sonra, Sonraki'ne **tıklayın**.

8. Kullanıcı **tanımla sayfasında** , verileri içeri aktarıla kullanıcıları belirtin.

     - **Kuruluş 2013'te çalışan tüm kullanıcılar**. Tüm kullanıcıların verilerini içeri aktar için bu seçeneği belirtin.

     - **Yalnızca Mahkeme tutmada olan kullanıcılar**. Yalnızca posta kutuları Mahkeme tutmada bulunan kullanıcılara ait verileri içeri aktarmayı bu seçeneği belirtin. Bu seçenek, verileri LitigationHoldEnabled özelliği True olarak ayarlanmış kullanıcı posta kutularına içeri aktarmaktadır. Daha fazla bilgi için [bkz. Mahkeme tutma oluşturma](create-a-litigation-hold.md).

9. Ice **Chat kullanıcılarını yeni kullanıcılarla Microsoft 365,** otomatik kullanıcı eşlemesini etkinleştirin ve gerektiğinde özel kullanıcı eşlemesi sağlar.

   > [!NOTE]
   > Daha önce de açıklaması olan özel eşleme dosyası CSV dosyası, HER kullanıcı için ICE Sohbeti imid'ini ve Microsoft 365 posta kutusu adresini içerir. Otomatik kullanıcı eşlemesini etkinleştirir ve her sohbet öğesi için özel bir eşleme sağlarsanız, bağlayıcı önce özel eşleme dosyasına bakar. Kullanıcının ICE Chat imid'ine karşılık gelen geçerli bir Microsoft 365 kullanıcısı bulamazsa bağlayıcı, öğeyi sohbet öğesinin *SenderEmail* ve *RecipientEmail* özelliklerinde belirtilen kullanıcıların posta kutularına aktaracak. Bağlayıcı, otomatik veya özel kullanıcı eşlemesi Microsoft 365 geçerli bir kullanıcı bulamazsa, öğe aktarılmaz.

10. **Sonraki'ye** tıklayın, ayarlarınızı gözden geçirip bağlayıcıyı oluşturmak **için** Son'a tıklayın.

11. Yeni bağlayıcı **için içeri aktarma** işleminin ilerlemesini görmek için Veri bağlayıcıları sayfasına gidin. Bağlayıcı hakkında bilgi içeren çıkış sayfasını görüntülemek için bağlayıcıya tıklayın.
