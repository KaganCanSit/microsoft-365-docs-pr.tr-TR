---
title: Bloomberg İleti verilerini arşivleye bir bağlayıcı ayarlama
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
description: Yöneticiler, Microsoft 365'daki Bloomberg Message e-posta aracından verileri içeri aktarmak ve arşivlemek için bir veri bağlayıcısı ayarlayabilir. Bu, kuruluşunuzun üçüncü taraf verilerini yönetmek için yasal tutma, İçerik Arama ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilmeniz için üçüncü taraf veri kaynaklarından verileri Microsoft 365 arşivleyebilmenizi sağlar.
ms.openlocfilehash: 781378ba30ccb7db44191764e050277fa4a239aa
ms.sourcegitcommit: caedcf7f16eed23596487d97c375d4bc4c8f3566
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2022
ms.locfileid: "64992839"
---
# <a name="set-up-a-connector-to-archive-bloomberg-message-data"></a>Bloomberg İleti verilerini arşivleye bir bağlayıcı ayarlama

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

[Bloomberg Message](https://www.bloomberg.com/professional/product/collaboration/) işbirliği aracından finansal hizmetler e-posta verilerini içeri aktarmak ve arşivlemek için Microsoft Purview uyumluluk portalında bir veri bağlayıcısı kullanın. Bağlayıcıyı ayarlayıp yapılandırdıktan sonra, her gün bir kez kuruluşunuzun Bloomberg güvenli FTP (SFTP) sitesine bağlanır ve e-posta öğelerini Microsoft 365 posta kutularına aktarır.

Bloomberg İleti verileri kullanıcı posta kutularında depolandıktan sonra, Dava tutma, içerik arama, Yerinde arşivleme, denetim, İletişim uyumluluğu ve Microsoft 365 bekletme ilkeleri gibi Microsoft Purview özelliklerini Bloomberg İleti verilerine uygulayabilirsiniz. Örneğin, içerik arama aracını kullanarak Bloomberg İleti e-postalarında arama yapabilir veya Bloomberg İleti verilerini içeren posta kutusunu eBulma (Premium) durumundaki bir koruyucuyla ilişkilendirebilirsiniz. Microsoft 365'da verileri içeri aktarmak ve arşivlerken Bloomberg Message bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-bloomberg-message-data"></a>Bloomberg İleti verilerini arşivleme hakkında genel bakış

Aşağıdaki genel bakış, bloomberg message verilerini Microsoft 365 arşivleye bağlayıcı kullanma işlemini açıklar.

![Bloomberg İleti içeri aktarma ve arşiv işlemi.](../media/BloombergMessageArchiving.png)

1. Kuruluşunuz Bloomberg ile birlikte çalışarak bir Bloomberg SFTP sitesi kuracak. E-posta iletilerini Bloomberg SFTP sitesine kopyalamak üzere Bloomberg Message'ı yapılandırmak için Bloomberg ile de çalışacaksınız.

2. Her 24 saatte bir Bloomberg Message'dan gelen e-posta iletileri Bloomberg SFTP sitesine kopyalanır.

3. Uyumluluk portalında oluşturduğunuz Bloomberg Message bağlayıcısı her gün Bloomberg SFTP sitesine bağlanır ve önceki 24 saat içindeki e-posta iletilerini Microsoft Cloud'daki güvenli bir Azure Depolama alanına aktarır.

4. Bağlayıcı, e-posta iletisi öğelerini belirli bir kullanıcının posta kutusuna aktarır. Belirli bir kullanıcının posta kutusunda BloombergMessage adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır.

   Bağlayıcı bunu CorporateEmailAddress özelliğinin değerini kullanarak yapar. Her e-posta iletisi, e-posta iletisinin her katılımcısının e-posta adresiyle doldurulmuş olan bu özelliği içerir. *CorporateEmailAddress* özelliğinin değerini kullanarak otomatik kullanıcı eşlemesine ek olarak, csv eşleme dosyasını karşıya yükleyerek özel eşleme de tanımlayabilirsiniz. Bu eşleme dosyası bir Bloomberg UUID ve kuruluşunuzdaki her kullanıcı için ilgili Microsoft 365 posta kutusu adresini içerir. Otomatik kullanıcı eşlemesini etkinleştirir ve özel bir eşleme sağlarsanız, bağlayıcı her e-posta öğesi için önce özel eşleme dosyasına bakar. Kullanıcının Bloomberg UUID'sine karşılık gelen geçerli bir Microsoft 365 kullanıcısı bulamazsa bağlayıcı, e-posta öğesinin *CorporateEmailAddress* özelliğini kullanır. Bağlayıcı, özel eşleme dosyasında veya e-posta öğesinin *CorporateEmailAddress* özelliğinde geçerli bir Microsoft 365 kullanıcısı bulamazsa, öğe içeri aktarılamaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

Bloomberg İleti verilerini arşivlerken gereken uygulama adımlarından bazıları Microsoft 365 dışındadır ve bağlayıcıyı uyumluluk merkezinde oluşturabilmeniz için önce tamamlanması gerekir.

- Bloomberg Message bağlayıcısı ayarlamak için Oldukça İyi Gizlilik (PGP) ve Secure Shell (SSH) için anahtarlar ve anahtar parolaları kullanmanız gerekir. Bu anahtarlar Bloomberg SFTP sitesini yapılandırmak için kullanılır ve bağlayıcı tarafından verileri Microsoft 365 içeri aktarmak için Bloomberg SFTP sitesine bağlanmak için kullanılır. PGP anahtarı, Bloomberg SFTP sitesinden Microsoft 365 aktarılan verilerin şifrelenmesini yapılandırmak için kullanılır. Bağlayıcı Bloomberg SFTP sitesine bağlandığında güvenli bir uzaktan oturum açmayı etkinleştirmek için güvenli kabuğu yapılandırmak için SSH anahtarı kullanılır.

  Bağlayıcıyı ayarlarken, Microsoft tarafından sağlanan ortak anahtarları ve anahtar parolalarını kullanma seçeneğiniz vardır veya kendi özel anahtarlarınızı ve parolalarınızı kullanabilirsiniz. Microsoft tarafından sağlanan ortak anahtarları kullanmanızı öneririz. Ancak, kuruluşunuz özel anahtarlar kullanarak zaten bir Bloomberg SFTP sitesi yapılandırdıysa, aynı özel anahtarları kullanarak bir bağlayıcı oluşturabilirsiniz.

- [Bloomberg Anywhere'e abone olun](https://www.bloomberg.com/professional/product/remote-access/?bbgsum-page=DG-WS-PROF-PROD-BBA). Bu, ayarlamanız ve yapılandırmanız gereken Bloomberg SFTP sitesine erişmek için Bloomberg Anywhere'de oturum açabilmeniz için gereklidir.

- Bloomberg SFTP (Güvenli dosya aktarım protokolü) sitesi ayarlayın. SFTP sitesini kurmak için Bloomberg ile çalıştıktan sonra Bloomberg Message'dan gelen veriler her gün SFTP sitesine yüklenir. 2. Adımda oluşturduğunuz bağlayıcı bu SFTP sitesine bağlanır ve e-posta verilerini Microsoft 365 posta kutularına aktarır. SFTP ayrıca aktarım işlemi sırasında posta kutularına gönderilen Bloomberg Message verilerini şifreler.

  Bloomberg SFTP ( *BB-SFTP* olarak da adlandırılır) hakkında bilgi için:

  - [Bloomberg Desteği'ndeki](https://www.bloomberg.com/professional/support/documentation/) "SFTP Bağlantı Standartları" belgesine bakın.

  - [Bloomberg müşteri desteğine](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc) başvurun.

- Bir SFTP sitesi kurmak için Bloomberg ile birlikte çalışırken, Bloomberg uygulama e-posta iletisine yanıt verdikten sonra Bloomberg size bazı bilgiler sağlayacaktır. Aşağıdaki bilgilerin bir kopyasını kaydedin. 3. Adımda bağlayıcı ayarlamak için bunu kullanırsınız.

  - Kuruluşunuz için bir kimlik olan ve Bloomberg SFTP sitesinde oturum açmak için kullanılan kesin kod.

  - Bloomberg SFTP sitenizin parolası

  - Bloomberg SFTP sitesinin URL'si (örneğin, sftp.bloomberg.com). Ek olarak, Bloomberg, bağlayıcıyı ayarlamak için de kullanılabilen Bloomberg SFTP sitesi için karşılık gelen bir IP adresi de sağlayabilir.

  - Bloomberg SFTP sitesi için bağlantı noktası numarası

- Bloomberg Message bağlayıcısı tek bir günde toplam 200.000 öğeyi içeri aktarabilir. SFTP sitesinde 200.000'den fazla öğe varsa, bu öğelerin hiçbiri Microsoft 365 aktarılamaz.

- 3. Adımda bir Bloomberg İleti bağlayıcısı oluşturan (ve 1. Adımda ortak anahtarları ve IP adresini indiren) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için [Microsoft Purview uyumluluk portalındaki İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

## <a name="set-up-a-connector-using-public-keys"></a>Ortak anahtarları kullanarak bağlayıcı ayarlama

Bu bölümdeki adımlarda Pretty Good Privacy (PGP) ve Secure Shell (SSH) için ortak anahtarları kullanarak Bloomberg Message bağlayıcısının nasıl ayarlanacağı gösterilir.

### <a name="step-1-obtain-pgp-and-ssh-public-keys"></a>1. Adım: PGP ve SSH ortak anahtarlarını alma

İlk adım, PGP ve SSH ortak anahtarlarının bir kopyasını almaktır. Bağlayıcının (3. Adımda oluşturduğunuz) SFTP sitesine bağlanmasına ve Bloomberg İletisi e-posta verilerini Microsoft 365 posta kutularına aktarmasına izin verecek şekilde Bloomberg SFTP sitesini yapılandırmak için 2. Adımda bu anahtarları kullanırsınız. Bu adımda, Bloomberg SFTP sitesini yapılandırırken kullandığınız bir IP adresi de alırsınız.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com> gidin ve tıklayın.

2. **Veri bağlayıcıları** sayfasında **Bloomberg İletisi'nin** altında **Görüntüle'ye** tıklayın.

3. **Bloomberg İletisi** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın

4. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

5. **İçerik kaynağı için kimlik bilgileri ekle** sayfasında, **Microsoft tarafından sağlanan PGP ve SSH ortak anahtarlarını kullanmak istiyorum'a** tıklayın.

   ![Ortak anahtarları kullanma seçeneğini belirleyin.](../media/BloombergMessagePublicKeysOption.png)

6. 1. adım altında **SSH anahtarını indir**, **PGP anahtarını indir** ve **IP adresini indir** bağlantılarına tıklayarak her dosyanın bir kopyasını yerel bilgisayarınıza kaydedin.

   ![Ortak anahtarları ve IP adresini indirme bağlantıları.](../media/BloombergMessagePublicKeyDownloadLinks.png)

   Bu dosyalar, 2. Adımda Bloomberg SFTP sitesini yapılandırmak için kullanılan aşağıdaki öğeleri içerir:

   - PGP ortak anahtarı: Bu anahtar, Bloomberg SFTP sitesinden Microsoft 365 aktarılan verilerin şifrelenmesini yapılandırmak için kullanılır.

   - SSH ortak anahtarı: Bu anahtar, bağlayıcı Bloomberg SFTP sitesine bağlandığında güvenli bir uzaktan oturum açmayı etkinleştirmek için güvenli kabuğu yapılandırmak için kullanılır.

   - IP adresi: Bloomberg SFTP sitesi, bu IP adresinden gelen bağlantı isteklerini kabul etmek üzere yapılandırılmıştır. Aynı IP adresi, Bloomberg Message bağlayıcısı tarafından SFTP sitesine bağlanmak ve Bloomberg Message verilerini Microsoft 365 aktarmak için kullanılır.

7. Sihirbazı kapatmak için **İptal'e** tıklayın. Bağlayıcıyı oluşturmak için 3. Adımda bu sihirbaza geri dönersiniz.

### <a name="step-2-configure-the-bloomberg-sftp-site"></a>2. Adım: Bloomberg SFTP sitesini yapılandırma

> [!NOTE]
> Kuruluşunuz daha önce genel PGP ve SSH anahtarlarını kullanarak Anlık Bloomberg verilerini arşivleme amacıyla bir Bloomberg SFTP sitesi ayarladıysa, başka bir tane ayarlamanız gerekmez. 3. Adımda bağlayıcıyı oluştururken aynı SFTP sitesini belirtebilirsiniz.

Sonraki adım, Bloomberg SFTP sitesi için PGP şifrelemesini ve SSH kimlik doğrulamasını yapılandırmak üzere 1. Adımda edindiğiniz PGP ve SSH ortak anahtarlarını ve IP adresini kullanmaktır. Bu, 3. Adımda oluşturduğunuz Bloomberg Message bağlayıcısının Bloomberg SFTP sitesine bağlanmasını ve Bloomberg Message verilerini Microsoft 365 aktarmasını sağlar. Bloomberg SFTP sitenizi ayarlamak için Bloomberg müşteri desteğiyle çalışmanız gerekir. Yardım için [Bloomberg müşteri desteğine](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc) başvurun.

> [!IMPORTANT]
> Bloomberg, 1. Adımda indirdiğiniz üç dosyayı bir e-posta iletisine eklemenizi ve Bloomberg SFTP sitenizi ayarlamak için onlarla çalışırken müşteri destek ekibine göndermenizi önerir.

### <a name="step-3-create-a-bloomberg-message-connector"></a>3. Adım: Bloomberg İleti bağlayıcısı oluşturma

Son adım, uyumluluk portalında bir Bloomberg İleti bağlayıcısı oluşturmaktır. Bağlayıcı, Bloomberg SFTP sitesine bağlanmak ve e-posta iletilerini Microsoft 365 ilgili kullanıcı posta kutusu kutularına aktarmak için sağladığınız bilgileri kullanır.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com> gidin ve tıklayın.

2. **Veri bağlayıcıları** sayfasında **Bloomberg İletisi'nin** altında **Görüntüle'ye** tıklayın.

3. **Bloomberg İletisi** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın

4. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

5. **İçerik kaynağı için kimlik bilgileri ekle** sayfasında, **Microsoft tarafından sağlanan PGP ve SSH ortak anahtarlarını kullanmak istiyorum'a** tıklayın.

6. 3. Adım'ın altında, aşağıdaki kutulara gerekli bilgileri girin ve Bağlantıyı **doğrula'ya** tıklayın.

      - **Adı:** Bağlayıcının adı. Kuruluşunuzda benzersiz olmalıdır.

      - **Firma kodu:** Bloomberg SFTP sitesinin kullanıcı adı olarak kullanılan kuruluşunuzun kimliği.

      - **Parola:** Kuruluşunuzun Bloomberg SFTP sitesinin parolası.

      - **SFTP URL'si:** Bloomberg SFTP sitesinin URL'si (örneğin, `sftp.bloomberg.com`). Bu değer için bir IP adresi de kullanabilirsiniz.

      - **SFTP bağlantı noktası:** Bloomberg SFTP sitesinin bağlantı noktası numarası. Bağlayıcı, SFTP sitesine bağlanmak için bu bağlantı noktasını kullanır.

7. Bağlantı başarıyla doğrulandıktan sonra **İleri'ye** tıklayın.

8. **Kullanıcı tanımla** sayfasında, verilerini içeri aktaracak kullanıcıları belirtin.

     - **Kuruluşunuzdaki tüm kullanıcılar**. Tüm kullanıcılar için verileri içeri aktarmak için bu seçeneği belirleyin.

     - **Yalnızca Dava tutan kullanıcılar**. Yalnızca posta kutuları Dava tutmada yer alan kullanıcılar için verileri içeri aktarmak için bu seçeneği belirleyin. Bu seçenek, LitigationHoldEnabled özelliği True olarak ayarlanmış kullanıcı posta kutularına veri aktarır. Daha fazla bilgi için bkz. [Dava tutma oluşturma](create-a-litigation-hold.md).

9. **Kullanıcıları Microsoft 365 için Eşleme Bloomberg İletisi sayfasında** otomatik kullanıcı eşlemesini etkinleştirin ve gerektiğinde özel kullanıcı eşlemesi sağlayın.

   > [!NOTE]
   > Bağlayıcı, ileti öğelerini belirli bir kullanıcının posta kutusuna aktarır. Belirli bir kullanıcının posta kutusunda **BloombergMessage** adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, *CorporateEmailAddress* özelliğinin değerini kullanarak yapar. Her sohbet iletisi bu özelliği içerir ve özellik, sohbet iletisinin her katılımcısının e-posta adresiyle doldurulur. *CorporateEmailAddress* özelliğinin değerini kullanarak otomatik kullanıcı eşlemesine ek olarak, csv eşleme dosyasını karşıya yükleyerek özel eşleme de tanımlayabilirsiniz. Eşleme dosyası Bloomberg UUID'sini ve her kullanıcı için ilgili Microsoft 365 posta kutusu adresini içermelidir. Otomatik kullanıcı eşlemesini etkinleştirir ve özel bir eşleme sağlarsanız, bağlayıcı her ileti öğesi için önce özel eşleme dosyasına bakar. Kullanıcının Bloomberg UUID'sine karşılık gelen geçerli bir Microsoft 365 kullanıcı bulamazsa, bağlayıcı sohbet öğesinin *CorporateEmailAddress* özelliğini kullanır. Bağlayıcı, özel eşleme dosyasında veya ileti öğesinin *CorporateEmailAddress* özelliğinde geçerli bir Microsoft 365 kullanıcısı bulamazsa, öğe içeri aktarılamaz.

10. **İleri'ye** tıklayın, ayarlarınızı gözden geçirin ve ardından **Son'a** tıklayarak bağlayıcıyı oluşturun.

11. Yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları** sayfasına gidin. Bağlayıcı hakkında bilgi içeren açılır sayfayı görüntülemek için bağlayıcıya tıklayın.

## <a name="set-up-a-connector-using-private-keys"></a>Özel anahtarlar kullanarak bağlayıcı ayarlama

Bu bölümdeki adımlarda, PGP ve SSH özel anahtarlarını kullanarak Bloomberg Message bağlayıcısının nasıl ayarlanacağı gösterilir. Bu bağlayıcı kurulum seçeneği, özel anahtarlar kullanarak zaten bir Bloomberg SFTP sitesi yapılandırmış olan kuruluşlara yöneliktir.

### <a name="step-1-obtain-an-ip-address-to-configure-the-bloomberg-sftp-site"></a>1. Adım: Bloomberg SFTP sitesini yapılandırmak için bir IP adresi alma

> [!NOTE]
> Kuruluşunuz daha önce PGP ve SSH özel anahtarlarını kullanarak Instant Bloomberg verilerini arşivleme amacıyla bir Bloomberg SFTP sitesi yapılandırdıysa, başka bir tane yapılandırmanız gerekmez. 2. Adımda bağlayıcıyı oluştururken aynı SFTP sitesini belirtebilirsiniz.

Kuruluşunuz bir Bloomberg SFTP sitesi kurmak için PGP ve SSH özel anahtarlarını kullandıysa, bir IP adresi edinmeniz ve bunu Bloomberg müşteri desteğine sağlamanız gerekir. Bloomberg SFTP sitesi, bu IP adresinden gelen bağlantı isteklerini kabul etmek için yapılandırılmalıdır. Aynı IP adresi, Bloomberg Message bağlayıcısı tarafından SFTP sitesine bağlanmak ve Bloomberg Message verilerini Microsoft 365 aktarmak için kullanılır.

IP adresini almak için:

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com> gidin ve tıklayın.

2. **Veri bağlayıcıları** sayfasında **Bloomberg İletisi'nin** altında **Görüntüle'ye** tıklayın.

3. **Bloomberg İletisi** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın

4. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

5. **İçerik kaynağı için kimlik bilgileri ekle** sayfasında **PGP ve SSH özel anahtarlarını kullanmak istiyorum'a** tıklayın.

6. 1. adım altında **IP adresi** dosyasının bir kopyasını yerel bilgisayarınıza kaydetmek için IP adresini indir'e tıklayın.

   ![IP adresini indirin.](../media/BloombergMessageConnectorIPAddress.png)

7. Sihirbazı kapatmak için **İptal'e** tıklayın. Bağlayıcıyı oluşturmak için 2. Adımda bu sihirbaza geri dönersiniz.

Bloomberg SFTP sitenizi bu IP adresinden gelen bağlantı isteklerini kabul edecek şekilde yapılandırmak için Bloomberg müşteri desteğiyle çalışmanız gerekir. Yardım için [Bloomberg müşteri desteğine](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc) başvurun.

### <a name="step-2-create-a-bloomberg-message-connector"></a>2. Adım: Bloomberg İleti bağlayıcısı oluşturma

Bloomberg SFTP siteniz yapılandırıldıktan sonra, sonraki adım uyumluluk portalında bir Bloomberg Message bağlayıcısı oluşturmaktır. Bağlayıcı, Bloomberg SFTP sitesine bağlanmak ve e-posta iletilerini Microsoft 365 ilgili kullanıcı posta kutusu kutularına aktarmak için sağladığınız bilgileri kullanır. Bu adımı tamamlamak için Bloomberg SFTP sitenizi ayarlamak için kullandığınız aynı özel anahtarların ve anahtar parolalarının kopyalarına sahip olduğunuzdan emin olun.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com> gidin ve tıklayın.

2. **Veri bağlayıcıları** sayfasında **Bloomberg İletisi'nin** altında **Görüntüle'ye** tıklayın.

3. **Bloomberg İletisi** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın

4. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

5. **İçerik kaynağı için kimlik bilgileri ekle** sayfasında **PGP ve SSH özel anahtarlarını kullanmak istiyorum'a** tıklayın.

   ![Özel anahtarları kullanma seçeneğini belirleyin.](../media/BloombergMessagePrivateKeysOption.png)

6. 3. Adım'ın altında, aşağıdaki kutulara gerekli bilgileri girin ve Bağlantıyı **doğrula'ya** tıklayın.

      - **Adı:** Bağlayıcının adı. Kuruluşunuzda benzersiz olmalıdır.

      - **Firma kodu:** Bloomberg SFTP sitesinin kullanıcı adı olarak kullanılan kuruluşunuzun kimliği.

      - **Parola:** Kuruluşunuzun Bloomberg SFTP sitesinin parolası.

      - **SFTP URL'si:** Bloomberg SFTP sitesinin URL'si (örneğin, `sftp.bloomberg.com`). Bu değer için bir IP adresi de kullanabilirsiniz.

      - **SFTP bağlantı noktası:** Bloomberg SFTP sitesinin bağlantı noktası numarası. Bağlayıcı, SFTP sitesine bağlanmak için bu bağlantı noktasını kullanır.

      - **PGP özel anahtarı:** Bloomberg SFTP sitesi için PGP özel anahtarı. Anahtar bloğunun başlangıç ve bitiş satırları da dahil olmak üzere özel anahtar değerinin tamamını eklediğinizden emin olun.

      - **PGP anahtar parolası:** PGP özel anahtarının parolası.

      - **SSH özel anahtarı:** Bloomberg SFTP sitesi için SSH özel anahtarı. Anahtar bloğunun başlangıç ve bitiş satırları da dahil olmak üzere özel anahtar değerinin tamamını eklediğinizden emin olun.

      - **SSH anahtarı parolası:** SSH özel anahtarının parolası.

7. Bağlantı başarıyla doğrulandıktan sonra **İleri'ye** tıklayın.

8. **Kullanıcı tanımla** sayfasında, verileri içeri aktaracak kullanıcıları belirtin

     - **Kuruluşunuzdaki tüm kullanıcılar**. Tüm kullanıcılar için verileri içeri aktarmak için bu seçeneği belirleyin.

     - **Yalnızca Dava tutan kullanıcılar**. Yalnızca posta kutuları Dava tutmada yer alan kullanıcılar için verileri içeri aktarmak için bu seçeneği belirleyin. Bu seçenek, LitigationHoldEnabled özelliği True olarak ayarlanmış kullanıcı posta kutularına veri aktarır. Daha fazla bilgi için bkz. [Dava tutma oluşturma](create-a-litigation-hold.md).

9. **Kullanıcıları Microsoft 365 için Eşleme Bloomberg İletisi sayfasında** otomatik kullanıcı eşlemesini etkinleştirin ve gerektiğinde özel kullanıcı eşlemesi sağlayın.

   > [!NOTE]
   > Bağlayıcı, ileti öğelerini belirli bir kullanıcının posta kutusuna aktarır. Belirli bir kullanıcının posta kutusunda **BloombergMessage** adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, *CorporateEmailAddress* özelliğinin değerini kullanarak yapar. Her sohbet iletisi bu özelliği içerir ve özellik, sohbet iletisinin her katılımcısının e-posta adresiyle doldurulur. *CorporateEmailAddress* özelliğinin değerini kullanarak otomatik kullanıcı eşlemesine ek olarak, csv eşleme dosyasını karşıya yükleyerek özel eşleme de tanımlayabilirsiniz. Eşleme dosyası Bloomberg UUID'sini ve her kullanıcı için ilgili Microsoft 365 posta kutusu adresini içermelidir. Otomatik kullanıcı eşlemesini etkinleştirir ve özel bir eşleme sağlarsanız, bağlayıcı her ileti öğesi için önce özel eşleme dosyasına bakar. Kullanıcının Bloomberg UUID'sine karşılık gelen geçerli bir Microsoft 365 kullanıcı bulamazsa, bağlayıcı sohbet öğesinin *CorporateEmailAddress* özelliğini kullanır. Bağlayıcı, özel eşleme dosyasında veya ileti öğesinin *CorporateEmailAddress* özelliğinde geçerli bir Microsoft 365 kullanıcısı bulamazsa, öğe içeri aktarılamaz.

10. **İleri'ye** tıklayın, ayarlarınızı gözden geçirin ve ardından **Son'a** tıklayarak bağlayıcıyı oluşturun.

11. Yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları** sayfasına gidin. Bağlayıcı hakkında bilgi içeren açılır sayfayı görüntülemek için bağlayıcıya tıklayın.

## <a name="known-issues"></a>Bilinen sorunlar

- Microsoft 365 içeri aktarılan Bloomberg İleti e-postasının yazışmaları desteklenmez. Bir kişiye gönderilen tek tek iletiler içeri aktarılır, ancak yazışma konuşmasında sunulmaz. Microsoft, Bloomberg Message veri bağlayıcısının sonraki sürümlerinde yazışmayı desteklemek için çalışmaktadır.
