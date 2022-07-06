---
title: Anlık Bloomberg verilerini arşivleye bir bağlayıcı ayarlama
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 04/06/2022
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection: M365-security-compliance
ms.custom: seo-marvel-apr2020
description: Yöneticilerin Anlık Bloomberg sohbet aracındaki verileri Microsoft 365'e aktarmak ve arşivlemesi için veri bağlayıcısını nasıl ayarlayıp kullanabileceğini öğrenin.
ms.openlocfilehash: 9cca5955248ca7bd992c00b769ed2f2fbd212f89
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66623419"
---
# <a name="set-up-a-connector-to-archive-instant-bloomberg-data"></a>Anlık Bloomberg verilerini arşivleye bir bağlayıcı ayarlama

[Anlık Bloomberg](https://www.bloomberg.com/professional/product/collaboration/) işbirliği aracından finansal hizmetler sohbet verilerini içeri aktarmak ve arşiv etmek için Microsoft Purview uyumluluk portalı yerel bağlayıcı kullanın. Bağlayıcıyı ayarlayıp yapılandırdıktan sonra, her gün bir kez kuruluşunuzun Bloomberg güvenli FTP sitesine (SFTP) bağlanır, sohbet iletilerinin içeriğini e-posta iletisi biçimine dönüştürür ve ardından bu öğeleri Microsoft 365'teki posta kutularına aktarır.

Anlık Bloomberg verileri kullanıcı posta kutularında depolandıktan sonra, Anında Bloomberg verilerine Dava Tutma, İçerik Arama, In-Place Arşivleme, Denetim, İletişim uyumluluğu ve Microsoft 365 bekletme ilkeleri gibi Microsoft Purview özelliklerini uygulayabilirsiniz. Örneğin, İçerik Arama'yı kullanarak Anlık Bloomberg sohbet iletilerinde arama yapabilir veya Instant Bloomberg verilerini içeren posta kutusunu Microsoft Purview eKeşif (Premium) durumdaki bir koruyucuyla ilişkilendirebilirsiniz. Microsoft 365'te verileri içeri aktarmak ve arşivlerken Anlık Bloomberg bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-instant-bloomberg-data"></a>Instant Bloomberg verilerini arşivleme genel bakış

Aşağıdaki genel bakış, Microsoft 365'te Instant Bloomberg sohbet verilerini arşivlerken bağlayıcı kullanma işlemini açıklar. 

![Anında Bloomberg içeri aktarma ve arşiv işlemi.](../media/InstantBloombergDataArchiving.png)

1. Kuruluşunuz Bloomberg ile birlikte çalışarak bir Bloomberg SFTP sitesi kuracak. Ayrıca Sohbet mesajlarını Bloomberg SFTP sitenize kopyalamak üzere Instant Bloomberg'i yapılandırmak için Bloomberg ile birlikte çalışacaksınız.

2. Her 24 saatte bir, Instant Bloomberg'den gelen sohbet mesajları Bloomberg SFTP sitesine kopyalanır.

3. Uyumluluk portalında oluşturduğunuz Instant Bloomberg bağlayıcısı her gün Bloomberg SFTP sitesine bağlanır ve önceki 24 saat içindeki sohbet iletilerini Microsoft Bulut'taki güvenli bir Azure Depolama alanına aktarır. Bağlayıcı ayrıca sohbet masajının içeriğini e-posta iletisi biçimine dönüştürür.

4. Bağlayıcı, sohbet iletisi öğelerini belirli bir kullanıcının posta kutusuna aktarır. Belirli bir kullanıcının posta kutusunda InstantBloomberg adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı bunu *CorporateEmailAddress* özelliğinin değerini kullanarak yapar. Her sohbet iletisi, sohbet iletisinin her katılımcısının e-posta adresiyle doldurulmuş olan bu özelliği içerir. *CorporateEmailAddress* özelliğinin değerini kullanarak otomatik kullanıcı eşlemesine ek olarak, csv eşleme dosyasını karşıya yükleyerek özel eşleme de tanımlayabilirsiniz. Bu eşleme dosyası bir Bloomberg UUID ve her kullanıcı için ilgili Microsoft 365 posta kutusu adresini içermelidir. Otomatik kullanıcı eşlemesini etkinleştirir ve özel bir eşleme sağlarsanız, bağlayıcı her sohbet öğesi için önce özel eşleme dosyasına bakar. Kullanıcının Bloomberg UUID'sine karşılık gelen geçerli bir Microsoft 365 kullanıcısı bulamazsa, bağlayıcı sohbet öğesinin *CorporateEmailAddress* özelliğini kullanır. Bağlayıcı özel eşleme dosyasında veya sohbet öğesinin *CorporateEmailAddress* özelliğinde geçerli bir Microsoft 365 kullanıcısı bulamazsa, öğe içeri aktarılamaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

Instant Bloomberg verilerini arşivlerken gereken uygulama adımlarından bazıları Microsoft 365'in dışındadır ve bağlayıcıyı uyumluluk merkezinde oluşturabilmeniz için önce tamamlanması gerekir.

- Anında Bloomberg bağlayıcısı ayarlamak için Oldukça İyi Gizlilik (PGP) ve Secure Shell (SSH) için anahtarlar ve anahtar parolaları kullanmanız gerekir. Bu anahtarlar Bloomberg SFTP sitesini yapılandırmak için kullanılır ve bağlayıcı tarafından Verileri Microsoft 365'e aktarmak üzere Bloomberg SFTP sitesine bağlanmak için kullanılır. PGP anahtarı, Bloomberg SFTP sitesinden Microsoft 365'e aktarılan verilerin şifrelenmesini yapılandırmak için kullanılır. Bağlayıcı Bloomberg SFTP sitesine bağlandığında güvenli bir uzaktan oturum açmayı etkinleştirmek için güvenli kabuğu yapılandırmak için SSH anahtarı kullanılır.

  Bağlayıcıyı ayarlarken, Microsoft tarafından sağlanan ortak anahtarları ve anahtar parolalarını kullanma seçeneğiniz vardır veya kendi özel anahtarlarınızı ve parolalarınızı kullanabilirsiniz. Microsoft tarafından sağlanan ortak anahtarları kullanmanızı öneririz. Ancak, kuruluşunuz özel anahtarlar kullanarak zaten bir Bloomberg SFTP sitesi yapılandırdıysa, aynı özel anahtarları kullanarak bir bağlayıcı oluşturabilirsiniz.

- [Bloomberg Anywhere'e abone olun](https://www.bloomberg.com/professional/product/remote-access/?bbgsum-page=DG-WS-PROF-PROD-BBA). Bu, ayarlamanız ve yapılandırmanız gereken Bloomberg SFTP sitesine erişmek için Bloomberg Anywhere'de oturum açabilmeniz için gereklidir.

- Bloomberg SFTP (Güvenli dosya aktarım protokolü) sitesi ayarlayın. SFTP sitesini kurmak için Bloomberg ile çalıştıktan sonra, Instant Bloomberg'den gelen veriler her gün SFTP sitesine yüklenir. 2. Adımda oluşturduğunuz bağlayıcı bu SFTP sitesine bağlanır ve sohbet verilerini Microsoft 365 posta kutularına aktarır. SFTP ayrıca aktarım işlemi sırasında posta kutularına gönderilen Anlık Bloomberg sohbet verilerini şifreler.

  Bloomberg SFTP ( *BB-SFTP* olarak da adlandırılır) hakkında bilgi için:

  - [Bloomberg Desteği'ndeki](https://www.bloomberg.com/professional/support/documentation/) "SFTP Bağlantı Standartları" belgesine bakın.

  - [Bloomberg müşteri desteğine](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc) başvurun.

  Bir SFTP sitesi kurmak için Bloomberg ile birlikte çalışırken, Bloomberg uygulama e-posta iletisine yanıt verdikten sonra Bloomberg size bazı bilgiler sağlayacaktır. Aşağıdaki bilgilerin bir kopyasını kaydedin. 3. Adımda bağlayıcı ayarlamak için bunu kullanırsınız.

  - Kuruluşunuz için bir kimlik olan ve Bloomberg SFTP sitesinde oturum açmak için kullanılan kesin kod.

  - Bloomberg SFTP sitenizin parolası

  - Bloomberg SFTP sitesinin URL'si (örneğin, sftp.bloomberg.com)

  - Bloomberg SFTP sitesi için bağlantı noktası numarası

- Instant Bloomberg bağlayıcısı tek bir günde toplam 200.000 öğeyi içeri aktarabilir. SFTP sitesinde 200.000'den fazla öğe varsa, bu öğelerin hiçbiri Microsoft 365'e aktarılamaz.

- 3. Adımda Anlık Bloomberg bağlayıcısı oluşturan (ve 1. Adımda ortak anahtarları ve IP adresini indiren) kullanıcıya Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için, [Microsoft Purview uyumluluk portalı İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

## <a name="set-up-a-connector-using-public-keys"></a>Ortak anahtarları kullanarak bağlayıcı ayarlama

Bu bölümdeki adımlarda, Pretty Good Privacy (PGP) ve Secure Shell (SSH) için ortak anahtarları kullanarak bir Instant Bloomberg bağlayıcısının nasıl ayarlanacağı gösterilir.

### <a name="step-1-obtain-pgp-and-ssh-and-public-keys"></a>1. Adım: PGP ve SSH ile ortak anahtarları alma

İlk adım, Oldukça İyi Gizlilik (PGP) ve Secure Shell (SSH) için ortak anahtarların bir kopyasını almaktır. Bağlayıcının (3. Adımda oluşturduğunuz) SFTP sitesine bağlanmasına ve Anlık Bloomberg sohbet verilerini Microsoft 365 posta kutularına aktarmasına izin verecek şekilde Bloomberg SFTP sitesini yapılandırmak için 2. Adımda bu anahtarları kullanırsınız. Bu adımda, Bloomberg SFTP sitesini yapılandırırken kullandığınız bir IP adresi de alırsınız.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com> gidin ve tıklayın.

2. **Hızlı Bloomberg** altındaki **Veri bağlayıcıları** sayfasında **Görüntüle'ye** tıklayın.

3. **Instant Bloomberg** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın

4. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

5. **İçerik kaynağı için kimlik bilgileri ekle** sayfasında, **Microsoft tarafından sağlanan PGP ve SSH ortak anahtarlarını kullanmak istiyorum'a** tıklayın.

   ![Ortak anahtarları kullanma seçeneğini belirleyin.](../media/InstantBloombergPublicKeysOption.png)

6. 1. adım altında **SSH anahtarını indir**, **PGP anahtarını indir** ve **IP adresini indir** bağlantılarına tıklayarak her dosyanın bir kopyasını yerel bilgisayarınıza kaydedin.

   ![Ortak anahtarları ve IP adresini indirme bağlantıları.](../media/InstantBloombergPublicKeyDownloadLinks.png)

   Bu dosyalar, 2. Adımda Bloomberg SFTP sitesini yapılandırmak için kullanılan aşağıdaki öğeleri içerir:

   - PGP ortak anahtarı: Bu anahtar, Bloomberg SFTP sitesinden Microsoft 365'e aktarılan verilerin şifrelenmesini yapılandırmak için kullanılır.

   - SSH ortak anahtarı: Bu anahtar, bağlayıcı Bloomberg SFTP sitesine bağlandığında güvenli bir uzaktan oturum açmayı etkinleştirmek için güvenli kabuğu yapılandırmak için kullanılır.

   - IP adresi: Bloomberg SFTP sitesi, bu IP adresinden gelen bağlantı isteklerini kabul etmek üzere yapılandırılmıştır. Aynı IP adresi, Instant Bloomberg bağlayıcısı tarafından SFTP sitesine bağlanmak ve Instant Bloomberg verilerini Microsoft 365'e aktarmak için kullanılır.

7. Sihirbazı kapatmak için **İptal'e** tıklayın. Bağlayıcıyı oluşturmak için 3. Adımda bu sihirbaza geri dönersiniz.

### <a name="step-2-configure-the-bloomberg-sftp-site"></a>2. Adım: Bloomberg SFTP sitesini yapılandırma

Sonraki adım, Bloomberg SFTP sitesi için PGP şifrelemesini ve SSH kimlik doğrulamasını yapılandırmak üzere 1. Adımda edindiğiniz PGP ve SSH ortak anahtarlarını ve IP adresini kullanmaktır. Bu, 3. Adımda oluşturduğunuz Instant Bloomberg bağlayıcısının Bloomberg SFTP sitesine bağlanmasını ve Instant Bloomberg verilerini Microsoft 365'e aktarmasını sağlar. Bloomberg SFTP sitenizi ayarlamak için Bloomberg müşteri desteğiyle çalışmanız gerekir. Yardım için [Bloomberg müşteri desteğine](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc) başvurun. 

> [!IMPORTANT]
> Bloomberg, 1. Adımda indirdiğiniz üç dosyayı bir e-posta iletisine eklemenizi ve Bloomberg SFTP sitenizi ayarlamak için onlarla çalışırken müşteri destek ekibine göndermenizi önerir.

### <a name="step-3-create-an-instant-bloomberg-connector"></a>3. Adım: Anında Bloomberg bağlayıcısı oluşturma

Son adım, uyumluluk portalında bir Instant Bloomberg bağlayıcısı oluşturmaktır. Bağlayıcı, Bloomberg SFTP sitesine bağlanmak ve sohbet iletilerini Microsoft 365'teki ilgili kullanıcı posta kutusu kutularına aktarmak için sağladığınız bilgileri kullanır.

1. <https://compliance.microsoft.com> Adresine gidip **Veri bağlayıcıları** > **Anlık Bloomberg'e** tıklayın.

2. **Instant Bloomberg** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın

3. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

4. **Bloomberg SFTP sitesi için kimlik bilgileri ekle** sayfasında, 3. Adım'ın altında aşağıdaki kutulara gerekli bilgileri girin ve **İleri'ye** tıklayın.

    - **Firma kodu:** Bloomberg SFTP sitesinin kullanıcı adı olarak kullanılan kuruluşunuzun kimliği.

    - **Parola:** Bloomberg SFTP sitesi için parola.

    - **SFTP URL'si:** Bloomberg SFTP sitesinin URL'si (örneğin, `sftp.bloomberg.com`). Bu değer için bir IP adresi de kullanabilirsiniz.

    - **SFTP bağlantı noktası:** Bloomberg SFTP sitesinin bağlantı noktası numarası. Bağlayıcı, SFTP sitesine bağlanmak için bu bağlantı noktasını kullanır.

5. **Kullanıcı tanımla** sayfasında, verilerini içeri aktarmak istediğiniz kullanıcıları belirtmek için aşağıdaki seçeneklerden birini belirleyin.

    - **Kuruluşunuzdaki tüm kullanıcılar**. Tüm kullanıcılar için verileri içeri aktarmak için bu seçeneği belirleyin.

    - **Yalnızca Dava tutan kullanıcılar**. Yalnızca posta kutuları Dava tutmada yer alan kullanıcılar için verileri içeri aktarmak için bu seçeneği belirleyin. Bu seçenek, LitigationHoldEnabled özelliği True olarak ayarlanmış kullanıcı posta kutularına veri aktarır. Daha fazla bilgi için bkz. [Dava tutma oluşturma](create-a-litigation-hold.md).

6. **İçeri aktarılacak veri türlerini seçin** sayfasında **, İletiler** dışında içeri aktarılacak gerekli veri türlerini seçin

7. **Anlık Bloomberg kullanıcılarını Microsoft 365 kullanıcıları ile eşle** sayfasında otomatik kullanıcı eşlemesini etkinleştirin ve gerektiğinde özel kullanıcı eşlemesi sağlayın

   > [!NOTE]
   > Bağlayıcı, sohbet iletisi öğelerini belirli bir kullanıcının posta kutusuna aktarır. Belirli bir kullanıcının posta kutusunda **InstantBloomberg** adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, *CorporateEmailAddress* özelliğinin değerini kullanarak yapar. Her sohbet iletisi bu özelliği içerir ve özellik, sohbet iletisinin her katılımcısının e-posta adresiyle doldurulur. *CorporateEmailAddress* özelliğinin değerini kullanarak otomatik kullanıcı eşlemesine ek olarak, csv eşleme dosyasını karşıya yükleyerek özel eşleme de tanımlayabilirsiniz. Eşleme dosyası Her kullanıcı için Bloomberg UUID ve ilgili Microsoft 365 posta kutusu adresini içermelidir. Otomatik kullanıcı eşlemesini etkinleştirir ve özel bir eşleme sağlarsanız, bağlayıcı her sohbet öğesi için önce özel eşleme dosyasına bakar. Kullanıcının Bloomberg UUID'sine karşılık gelen geçerli bir Microsoft 365 kullanıcısı bulamazsa, bağlayıcı sohbet öğesinin *CorporateEmailAddress* özelliğini kullanır. Bağlayıcı özel eşleme dosyasında veya sohbet öğesinin *CorporateEmailAddress* özelliğinde geçerli bir Microsoft 365 kullanıcısı bulamazsa, öğe içeri aktarılamaz.

7. **İleri'ye** tıklayın, ayarlarınızı gözden geçirin ve ardından **Son'a** tıklayarak bağlayıcıyı oluşturun.

8. Yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları** sayfasına gidin. Bağlayıcı hakkında bilgi içeren açılır sayfayı görüntülemek için bağlayıcıya tıklayın.

## <a name="set-up-a-connector-using-private-keys"></a>Özel anahtarlar kullanarak bağlayıcı ayarlama

Bu bölümdeki adımlarda, PGP ve SSH özel anahtarlarını kullanarak Anlık Bloomberg bağlayıcısının nasıl ayarlanacağı gösterilir. Bu bağlayıcı kurulum seçeneği, özel anahtarlar kullanarak zaten bir Bloomberg SFTP sitesi yapılandırmış olan kuruluşlara yöneliktir.

### <a name="step-1-obtain-an-ip-address-to-configure-the-bloomberg-sftp-site"></a>1. Adım: Bloomberg SFTP sitesini yapılandırmak için bir IP adresi alma

> [!NOTE]
> Kuruluşunuz daha önce PGP ve SSH özel anahtarlarını kullanarak Bloomberg Message verilerini arşivleme amacıyla bir Bloomberg SFTP sitesi yapılandırdıysa, başka bir tane yapılandırmanız gerekmez. 2. Adımda bağlayıcıyı oluştururken aynı SFTP sitesini belirtebilirsiniz.

Kuruluşunuz bir Bloomberg SFTP sitesi kurmak için PGP ve SSH özel anahtarlarını kullandıysa, bir IP adresi edinmeniz ve bunu Bloomberg müşteri desteğine sağlamanız gerekir. Bloomberg SFTP sitesi, bu IP adresinden gelen bağlantı isteklerini kabul etmek için yapılandırılmalıdır. Aynı IP adresi, Instant Bloomberg bağlayıcısı tarafından SFTP sitesine bağlanmak ve Instant Bloomberg verilerini Microsoft 365'e aktarmak için kullanılır.

IP adresini almak için:

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com> gidin ve tıklayın.

2. **Hızlı Bloomberg** altındaki **Veri bağlayıcıları** sayfasında **Görüntüle'ye** tıklayın.

3. **Instant Bloomberg** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın

4. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

5. **İçerik kaynağı için kimlik bilgileri ekle** sayfasında **PGP ve SSH özel anahtarlarını kullanmak istiyorum'a** tıklayın.

6. 1. adım altında **IP adresi** dosyasının bir kopyasını yerel bilgisayarınıza kaydetmek için IP adresini indir'e tıklayın.

   ![IP adresini indirin.](../media/InstantBloombergConnectorIPAddress.png)

7. Sihirbazı kapatmak için **İptal'e** tıklayın. Bağlayıcıyı oluşturmak için 2. Adımda bu sihirbaza geri dönersiniz.

Bloomberg SFTP sitenizi bu IP adresinden gelen bağlantı isteklerini kabul edecek şekilde yapılandırmak için Bloomberg müşteri desteğiyle çalışmanız gerekir. Yardım için [Bloomberg müşteri desteğine](https://service.bloomberg.com/portal/sessions/new?utm_source=bloomberg-menu&utm_medium=csc) başvurun.

### <a name="step-2-create-an-instant-bloomberg-connector"></a>2. Adım: Anında Bloomberg bağlayıcısı oluşturma

Bloomberg SFTP siteniz yapılandırıldıktan sonra, sonraki adım uyumluluk portalında bir Instant Bloomberg bağlayıcısı oluşturmaktır. Bağlayıcı, Bloomberg SFTP sitesine bağlanmak ve e-posta iletilerini Microsoft 365'teki ilgili kullanıcı posta kutusu kutularına aktarmak için sağladığınız bilgileri kullanır. Bu adımı tamamlamak için Bloomberg SFTP sitenizi ayarlamak için kullandığınız aynı özel anahtarların ve anahtar parolalarının kopyalarına sahip olduğunuzdan emin olun.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com> gidin ve tıklayın.

2. **Hızlı Bloomberg** altındaki **Veri bağlayıcıları** sayfasında **Görüntüle'ye** tıklayın.

3. **Instant Bloomberg** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın

4. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

5. **İçerik kaynağı için kimlik bilgileri ekle** sayfasında **PGP ve SSH özel anahtarlarını kullanmak istiyorum'a** tıklayın.

   ![Özel anahtarları kullanma seçeneğini belirleyin.](../media/InstantBloombergPrivateKeysOption.png)

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

8. **Kullanıcı tanımla** sayfasında, verilerini içeri aktarmak istediğiniz kullanıcıları belirtmek için aşağıdaki seçeneklerden birini belirleyin.

    - **Kuruluşunuzdaki tüm kullanıcılar**. Tüm kullanıcılar için verileri içeri aktarmak için bu seçeneği belirleyin.

    - **Yalnızca Dava tutan kullanıcılar**. Yalnızca posta kutuları Dava tutmada yer alan kullanıcılar için verileri içeri aktarmak için bu seçeneği belirleyin. Bu seçenek, LitigationHoldEnabled özelliği True olarak ayarlanmış kullanıcı posta kutularına veri aktarır. Daha fazla bilgi için bkz. [Dava tutma oluşturma](create-a-litigation-hold.md).

9. **Anlık Bloomberg kullanıcılarını Microsoft 365 kullanıcıları ile eşle** sayfasında otomatik kullanıcı eşlemesini etkinleştirin ve gerektiğinde özel kullanıcı eşlemesi sağlayın.

   > [!NOTE]
   > Bağlayıcı, sohbet iletisi öğelerini belirli bir kullanıcının posta kutusuna aktarır. Belirli bir kullanıcının posta kutusunda **InstantBloomberg** adlı yeni bir klasör oluşturulur ve öğeler bu klasöre aktarılır. Bağlayıcı, *CorporateEmailAddress* özelliğinin değerini kullanarak yapar. Her sohbet iletisi bu özelliği içerir ve özellik, sohbet iletisinin her katılımcısının e-posta adresiyle doldurulur. *CorporateEmailAddress* özelliğinin değerini kullanarak otomatik kullanıcı eşlemesine ek olarak, csv eşleme dosyasını karşıya yükleyerek özel eşleme de tanımlayabilirsiniz. Eşleme dosyası Her kullanıcı için Bloomberg UUID ve ilgili Microsoft 365 posta kutusu adresini içermelidir. Otomatik kullanıcı eşlemesini etkinleştirir ve özel bir eşleme sağlarsanız, bağlayıcı her sohbet öğesi için önce özel eşleme dosyasına bakar. Kullanıcının Bloomberg UUID'sine karşılık gelen geçerli bir Microsoft 365 kullanıcısı bulamazsa, bağlayıcı sohbet öğesinin *CorporateEmailAddress* özelliğini kullanır. Bağlayıcı özel eşleme dosyasında veya sohbet öğesinin *CorporateEmailAddress* özelliğinde geçerli bir Microsoft 365 kullanıcısı bulamazsa, öğe içeri aktarılamaz.

10. **İleri'ye** tıklayın, ayarlarınızı gözden geçirin ve ardından **Son'a** tıklayarak bağlayıcıyı oluşturun.

11. Yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları** sayfasına gidin. Bağlayıcı hakkında bilgi içeren açılır sayfayı görüntülemek için bağlayıcıya tıklayın.
