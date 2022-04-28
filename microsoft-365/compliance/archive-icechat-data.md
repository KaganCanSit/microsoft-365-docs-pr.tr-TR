---
title: ICE Chat verilerini arşivleye bağlayıcı ayarlama
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
description: Yöneticiler ICE Sohbet aracındaki verileri Microsoft 365 içeri aktarmak ve arşivlemesi için bir bağlayıcı ayarlayabilir. Bu, kuruluşunuzun üçüncü taraf verilerini yönetmek için yasal tutma, içerik arama ve bekletme ilkeleri gibi uyumluluk özelliklerini kullanabilmeniz için üçüncü taraf veri kaynaklarından verileri Microsoft 365 arşivleyebilmenizi sağlar.
ms.openlocfilehash: 1704795d28062bf6259129e2548e797b2f6bc7e9
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65090571"
---
# <a name="set-up-a-connector-to-archive-ice-chat-data"></a>ICE Chat verilerini arşivleye bağlayıcı ayarlama

[!include[Purview banner](../includes/purview-rebrand-banner.md)]V

ICE Chat işbirliği aracından finansal hizmetler sohbet verilerini içeri aktarmak ve arşivlemek için Microsoft Purview uyumluluk portalında yerel bir bağlayıcı kullanın. Bağlayıcıyı ayarlayıp yapılandırdıktan sonra, her gün bir kez kuruluşunuzun ICE Chat güvenli FTP (SFTP) sitesine bağlanır, sohbet iletilerinin içeriğini e-posta iletisi biçimine dönüştürür ve sonra bu öğeleri Microsoft 365'daki posta kutularına aktarır.

ICE sohbet verileri kullanıcı posta kutularında depolandıktan sonra, dava tutma, eBulma, arşivleme, denetim, iletişim uyumluluğu ve Microsoft 365 bekletme ilkeleri gibi Microsoft Purview özelliklerini ICE Chat verilerine uygulayabilirsiniz. Örneğin, içerik aramasını kullanarak ICE Chat iletilerinde arama yapabilir veya ICE Chat verilerini içeren posta kutusunu eBulma (Premium) olayındaki bir koruyucuyla ilişkilendirebilirsiniz. Microsoft 365'da verileri içeri aktarmak ve arşivlemek için ICE Chat bağlayıcısı kullanmak, kuruluşunuzun kamu ve mevzuat ilkeleriyle uyumlu kalmasına yardımcı olabilir.

## <a name="overview-of-archiving-ice-chat-data"></a>ICE Sohbet verilerini arşivleme hakkında genel bakış

Aşağıdaki genel bakış, MICROSOFT 365'da ICE sohbet verilerini arşivleyen bir bağlayıcı kullanma işlemini açıklar.

![ICE Sohbet arşivleme iş akışı.](../media/ICEChatConnectorWorkflow.png)

1. Kuruluşunuz BIR ICE Chat SFTP sitesi ayarlamak için ICE Chat ile birlikte çalışır. Ayrıca ICE Chat ile birlikte çalışarak ICE Chat'i sohbet iletilerini ICE Chat SFTP sitenize kopyalanacak şekilde yapılandıracaksınız.

2. 24 saatte bir ICE Chat'ten gelen sohbet iletileri ICE Chat SFTP sitenize kopyalanır.

3. Uyumluluk portalında oluşturduğunuz ICE Chat bağlayıcısı her gün ICE Chat SFTP sitesine bağlanır ve önceki 24 saat içindeki sohbet iletilerini Microsoft bulutunda güvenli bir Azure Depolama konumuna aktarır. Bağlayıcı ayrıca sohbet masajının içeriğini e-posta iletisi biçimine dönüştürür.

4. Bağlayıcı, sohbet iletisi öğelerini belirli kullanıcıların posta kutularına aktarır. Kullanıcı posta kutularında **ICE Chat** adlı yeni bir klasör oluşturulur ve sohbet iletisi öğeleri bu klasöre aktarılır. Bağlayıcı, *SenderEmail* ve *RecipientEmail* özelliklerinin değerini kullanarak yapar. Her sohbet iletisi, gönderenin ve sohbet iletisinin her alıcısının/katılımcısının e-posta adresiyle doldurulmuş bu özellikleri içerir.

   *SenderEmail* ve *RecipientEmail* özelliğinin değerlerini kullanan otomatik kullanıcı eşlemesine ek olarak (bağlayıcı bir sohbet iletisini gönderenin posta kutusuna ve her alıcının posta kutularına aktarır), csv eşleme dosyasını karşıya yükleyerek özel kullanıcı eşlemesi de tanımlayabilirsiniz. Bu eşleme dosyası ICE Chat *ImId'sini* ve kuruluşunuzdaki her kullanıcı için ilgili Microsoft 365 posta kutusu adresini içerir. Otomatik kullanıcı eşlemesini etkinleştirir ve özel eşleme dosyası sağlarsanız, bağlayıcı her sohbet öğesi için önce özel eşleme dosyasına bakar. Kullanıcının ICE Chat ImId'sine karşılık gelen geçerli bir Microsoft 365 kullanıcı hesabı bulamazsa bağlayıcı, öğeyi sohbet katılımcılarının posta kutularına aktarmak için sohbet öğesinin *SenderEmail* ve *RecipientEmail* özelliklerini kullanır. Bağlayıcı, özel eşleme dosyasında veya *SenderEmail* ve *RecipientEmail* özelliklerinde geçerli bir Microsoft 365 kullanıcısı bulamazsa, öğe içeri aktarılamaz.

## <a name="before-you-set-up-a-connector"></a>Bağlayıcıyı ayarlamadan önce

ICE Chat verilerini arşiv etmek için gereken uygulama adımlarından bazıları Microsoft 365 dışındadır ve bağlayıcıyı uyumluluk merkezinde oluşturabilmeniz için önce tamamlanması gerekir.

- ICE Chat, müşterilerinden dış uyumluluk için bir ücret alır. Kuruluşunuz, üzerinde tartışmak ve adresinden edinebileceğiniz [https://www.theice.com/publicdocs/agreements/ICE\_Data\_Services\_Agreement.pdf](https://www.theice.com/publicdocs/agreements/ICE\_Data\_Services\_Agreement.pdf)ICE Chat veri hizmetleri sözleşmesini imzalamak için ICE Chat satış grubuyla iletişime geçmelidir. Bu sözleşme ICE Chat ile kuruluşunuz arasında yer alır ve Microsoft'u içermez. 2. Adımda bir ICE Chat SFTP sitesi ayarladıktan sonra, ICE Chat FTP kimlik bilgilerini doğrudan kuruluşunuza sağlar. Ardından, 3. Adımda bağlayıcıyı ayarlarken bu kimlik bilgilerini Microsoft'a sağlayacak olan siz olursunuz.

- 3. Adımda bağlayıcıyı oluşturmadan önce bir ICE Chat SFTP sitesi ayarlamanız gerekir. SFTP sitesini ayarlamak için ICE Chat ile çalıştıktan sonra, ICE Chat'ten gelen veriler her gün SFTP sitesine yüklenir. 3. Adımda oluşturduğunuz bağlayıcı bu SFTP sitesine bağlanır ve sohbet verilerini Microsoft 365 posta kutularına aktarır. SFTP, aktarım işlemi sırasında posta kutularına gönderilen ICE Chat verilerini de şifreler.

- ICE Chat bağlayıcısı ayarlamak için Oldukça İyi Gizlilik (PGP) ve Secure Shell (SSH) için anahtarlar ve anahtar parolaları kullanmanız gerekir. Bu anahtarlar ICE Chat SFTP sitesini yapılandırmak için kullanılır ve bağlayıcı tarafından verileri Microsoft 365 içeri aktarmak üzere ICE Chat SFTP sitesine bağlanmak için kullanılır. PGP anahtarı, ICE Chat SFTP sitesinden Microsoft 365 aktarılan verilerin şifrelenmesini yapılandırmak için kullanılır. Bağlayıcı ICE Chat SFTP sitesine bağlandığında güvenli bir uzaktan oturum açmayı etkinleştirmek için güvenli kabuğu yapılandırmak için SSH anahtarı kullanılır.

  Bağlayıcıyı ayarlarken, Microsoft tarafından sağlanan ortak anahtarları ve anahtar parolalarını kullanma seçeneğiniz vardır veya kendi özel anahtarlarınızı ve parolalarınızı kullanabilirsiniz. Microsoft tarafından sağlanan ortak anahtarları kullanmanızı öneririz. Ancak, kuruluşunuz özel anahtarları kullanarak zaten bir ICE Chat SFTP sitesi yapılandırdıysa, aynı özel anahtarları kullanarak bir bağlayıcı oluşturabilirsiniz.

- ICE Chat bağlayıcısı tek bir günde toplam 200.000 öğeyi içeri aktarabilir. SFTP sitesinde 200.000'den fazla öğe varsa, bu öğelerin hiçbiri Microsoft 365 aktarılamaz.

- 3. Adımda ICE Chat bağlayıcısını oluşturan (ve 1. Adımda ortak anahtarları ve IP adresini indiren) yöneticiye Veri Bağlayıcısı Yönetici rolü atanmalıdır. Bu rol, uyumluluk portalındaki **Veri bağlayıcıları sayfasına bağlayıcı** eklemek için gereklidir. Bu rol varsayılan olarak birden çok rol grubuna eklenir. Bu rol gruplarının listesi için Güvenlik [& Uyumluluk Merkezi'ndeki İzinler bölümündeki "Güvenlik ve uyumluluk merkezlerindeki](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center) roller" bölümüne bakın. Alternatif olarak, kuruluşunuzdaki bir yönetici özel bir rol grubu oluşturabilir, Veri Bağlayıcısı Yönetici rolünü atayabilir ve ardından uygun kullanıcıları üye olarak ekleyebilir. Yönergeler için [Microsoft Purview uyumluluk portalındaki İzinler](microsoft-365-compliance-center-permissions.md#create-a-custom-role-group) bölümündeki "Özel rol grubu oluşturma" bölümüne bakın.

## <a name="set-up-a-connector-using-public-keys"></a>Ortak anahtarları kullanarak bağlayıcı ayarlama

Bu bölümdeki adımlarda, Pretty Good Privacy (PGP) ve Secure Shell (SSH) için ortak anahtarları kullanarak BIR ICE Chat bağlayıcısının nasıl ayarlanacağı gösterilir.

### <a name="step-1-obtain-pgp-and-ssh-public-keys"></a>1. Adım: PGP ve SSH ortak anahtarlarını alma

İlk adım, Oldukça İyi Gizlilik (PGP) ve Secure Shell (SSH) için ortak anahtarların bir kopyasını almaktır. Bağlayıcının (3. Adımda oluşturduğunuz) SFTP sitesine bağlanmasına ve ICE Chat verilerini Microsoft 365 posta kutularına aktarmasına izin verecek şekilde ICE Chat SFTP sitesini yapılandırmak için 2. Adımda bu anahtarları kullanırsınız. Bu adımda, ICE Chat SFTP sitesini yapılandırırken kullandığınız bir IP adresi de alırsınız.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** [https://compliance.microsoft.com](https://compliance.microsoft.com) gidin ve tıklayın.

2. **ICE Chat'in** altındaki **Veri bağlayıcıları** sayfasında **Görüntüle'ye** tıklayın.

3. **ICE Sohbet** sayfasında **Bağlayıcı ekle'ye** tıklayın.

4. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

5. **İçerik kaynağı için kimlik bilgileri ekle** sayfasında, **Microsoft tarafından sağlanan PGP ve SSH ortak anahtarlarını kullanmak istiyorum'a** tıklayın.

   ![Ortak anahtarları kullanma seçeneğini belirleyin.](../media/ICEChatPublicKeysOption.png)

6. 1. adım altında **SSH anahtarını indir**, **PGP anahtarını indir** ve **IP adresini indir** bağlantılarına tıklayarak her dosyanın bir kopyasını yerel bilgisayarınıza kaydedin.

   ![Ortak anahtarları ve IP adresini indirme bağlantıları.](../media/ICEChatPublicKeyDownloadLinks.png)

   Bu dosyalar, 2. Adımda ICE Chat SFTP sitesini yapılandırmak için kullanılan aşağıdaki öğeleri içerir:

   - PGP ortak anahtarı: Bu anahtar, ICE Chat SFTP sitesinden Microsoft 365 aktarılan verilerin şifrelenmesini yapılandırmak için kullanılır.

   - SSH ortak anahtarı: Bu anahtar, bağlayıcı ICE Chat SFTP sitesine bağlandığında güvenli bir uzaktan oturum açmayı etkinleştirmek için Güvenli SSH'yi yapılandırmak için kullanılır.

   - IP adresi: ICE Chat SFTP sitesi, yalnızca 3. Adımda oluşturduğunuz ICE Chat bağlayıcısı tarafından kullanılan bu IP adresinden gelen bir bağlantı isteğini kabul etmek üzere yapılandırılmıştır.

7. Sihirbazı kapatmak için **İptal'e** tıklayın. Bağlayıcıyı oluşturmak için 3. Adımda bu sihirbaza geri dönersiniz.

### <a name="step-2-configure-the-ice-chat-sftp-site"></a>2. Adım: ICE Chat SFTP sitesini yapılandırma

Sonraki adım, ICE Chat SFTP sitesi için PGP şifrelemesini ve SSH kimlik doğrulamasını yapılandırmak üzere 1. Adımda aldığınız PGP ve SSH ortak anahtarlarını ve IP adresini kullanmaktır. Bu, 3. Adımda oluşturduğunuz ICE Chat bağlayıcısının ICE Chat SFTP sitesine bağlanmasını ve ICE Chat verilerini Microsoft 365 aktarmasını sağlar. ICE Chat SFTP sitenizi ayarlamak için ICE Chat müşteri desteğiyle çalışmanız gerekir.

### <a name="step-3-create-an-ice-chat-connector"></a>3. Adım: ICE Chat bağlayıcısı oluşturma

Son adım, uyumluluk portalında bir ICE Chat bağlayıcısı oluşturmaktır. Bağlayıcı, ICE Chat SFTP sitesine bağlanmak ve sohbet iletilerini Microsoft 365 ilgili kullanıcı posta kutusu kutularına aktarmak için sağladığınız bilgileri kullanır.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** [https://compliance.microsoft.com](https://compliance.microsoft.com) gidin ve tıklayın.

2. **ICE Chat'in** altındaki **Veri bağlayıcıları** sayfasında **Görüntüle'ye** tıklayın.

3. **ICE Sohbet** sayfasında **Bağlayıcı ekle'ye** tıklayın.

4. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

5. **İçerik kaynağı için kimlik bilgileri ekle** sayfasında **PGP ve SSH ortak anahtarlarını kullanmak istiyorum'a** tıklayın.

6. 3. Adım'ın altında, aşağıdaki kutulara gerekli bilgileri girin ve Bağlantıyı **doğrula'ya** tıklayın.

   - **Firma kodu:** ICE Chat SFTP sitesinin kullanıcı adı olarak kullanılan kuruluşunuzun kimliği.

   - **Parola:** ICE Chat SFTP sitenizin parolası.

   - **SFTP URL'si:** ICE Chat SFTP sitesinin URL'si (örneğin, `sftp.theice.com`). Bu değer için bir IP adresi de kullanabilirsiniz.

   - **SFTP bağlantı noktası:** ICE Chat SFTP sitesinin bağlantı noktası numarası. Bağlayıcı, SFTP sitesine bağlanmak için bu bağlantı noktasını kullanır.

7. Bağlantı başarıyla doğrulandıktan sonra **İleri'ye** tıklayın.

8. **Kullanıcı tanımla** sayfasında, verilerini içeri aktaracak kullanıcıları belirtin.

     - **Kuruluşunuzdaki tüm kullanıcılar**. Tüm kullanıcılar için verileri içeri aktarmak için bu seçeneği belirleyin.

     - **Yalnızca Dava tutan kullanıcılar**. Yalnızca posta kutuları Dava tutmada yer alan kullanıcılar için verileri içeri aktarmak için bu seçeneği belirleyin. Bu seçenek, LitigationHoldEnabled özelliği True olarak ayarlanmış kullanıcı posta kutularına veri aktarır. Daha fazla bilgi için bkz. [Dava tutma oluşturma](create-a-litigation-hold.md).

9. **Dış kullanıcıları Microsoft 365 kullanıcılarla eşle** sayfasında otomatik kullanıcı eşlemesini etkinleştirin ve gerektiğinde özel kullanıcı eşlemesi sağlayın. Bu sayfada kullanıcı eşleme CSV dosyasının bir kopyasını indirebilirsiniz. Dosyaya kullanıcı eşlemeleri ekleyebilir ve sonra dosyayı karşıya yükleyebilirsiniz.

   > [!NOTE]
   > Daha önce açıklandığı gibi, özel eşleme dosyası CSV dosyası ICE Chat imid ve her kullanıcı için ilgili Microsoft 365 posta kutusu adresini içerir. Otomatik kullanıcı eşlemesini etkinleştirir ve her sohbet öğesi için özel bir eşleme sağlarsanız bağlayıcı önce özel eşleme dosyasına bakar. Kullanıcının ICE Chat kimliğine karşılık gelen geçerli bir Microsoft 365 kullanıcısı bulamazsa, bağlayıcı öğeyi sohbet öğesinin *SenderEmail* ve *RecipientEmail* özelliklerinde belirtilen kullanıcıların posta kutularına aktarır. Bağlayıcı otomatik veya özel kullanıcı eşlemesi ile geçerli bir Microsoft 365 kullanıcı bulamazsa, öğe içeri aktarılamaz.

10. **İleri'ye** tıklayın, ayarlarınızı gözden geçirin ve ardından **Son'a** tıklayarak bağlayıcıyı oluşturun.

11. Yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları** sayfasına gidin.

## <a name="set-up-a-connector-using-private-keys"></a>Özel anahtarlar kullanarak bağlayıcı ayarlama

Bu bölümdeki adımlarda, PGP ve SSH özel anahtarlarını kullanarak ICE Chat bağlayıcısının nasıl ayarlanacağı gösterilir. Bu bağlayıcı kurulum seçeneği, özel anahtarlar kullanarak bir ICE Chat SFTP sitesi yapılandırmış olan kuruluşlara yöneliktir.

### <a name="step-1-obtain-an-ip-address-to-configure-the-ice-chat-sftp-site"></a>1. Adım: ICE Chat SFTP sitesini yapılandırmak için bir IP adresi alma

Kuruluşunuz bir ICE Chat SFTP sitesi ayarlamak için PGP ve SSH özel anahtarlarını kullandıysa, bir IP adresi edinmeniz ve ICE Chat müşteri desteğine sağlamanız gerekir. ICE Chat SFTP sitesi, bu IP adresinden gelen bağlantı isteklerini kabul etmek üzere yapılandırılmalıdır. Aynı IP adresi, ICE Chat bağlayıcısı tarafından SFTP sitesine bağlanmak ve ICE Chat verilerini Microsoft 365 aktarmak için kullanılır.

IP adresini almak için:

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com> gidin ve tıklayın.

2. **ICE Chat'in** altındaki **Veri bağlayıcıları** sayfasında **Görüntüle'ye** tıklayın.

3. **ICE Chat** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın

4. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

5. **İçerik kaynağı için kimlik bilgileri ekle** sayfasında **PGP ve SSH özel anahtarlarını kullanmak istiyorum'a** tıklayın.

   ![Özel anahtarları kullanma seçeneğini belirleyin.](../media/ICEChatPrivateKeysOption.png)

6. 1. adım altında **IP adresi** dosyasının bir kopyasını yerel bilgisayarınıza kaydetmek için IP adresini indir'e tıklayın.

   ![IP adresini indirin.](../media/ICEChatConnectorIPAddress.png)

7. Sihirbazı kapatmak için **İptal'e** tıklayın. Bağlayıcıyı oluşturmak için 2. Adımda bu sihirbaza geri dönersiniz.

ICE Chat SFTP sitenizi bu IP adresinden gelen bağlantı isteklerini kabul edecek şekilde yapılandırmak için ICE Chat müşteri desteğiyle çalışmanız gerekir.

### <a name="step-2-create-an-ice-chat-connector"></a>2. Adım: ICE Chat bağlayıcısı oluşturma

ICE Chat SFTP siteniz yapılandırıldıktan sonra, sonraki adım uyumluluk portalında bir ICE Chat bağlayıcısı oluşturmaktır. Bağlayıcı, ICE Chat SFTP sitesine bağlanmak ve e-posta iletilerini Microsoft 365 ilgili kullanıcı posta kutusu kutularına aktarmak için sağladığınız bilgileri kullanır. Bu adımı tamamlamak için ICE Chat SFTP sitenizi ayarlamak için kullandığınız aynı özel anahtarların ve anahtar parolalarının kopyalarına sahip olduğunuzdan emin olun.

1. Sol gezinti bölmesinde **Veri bağlayıcıları'na** <https://compliance.microsoft.com> gidin ve tıklayın.

2. **ICE Chat'in** altındaki **Veri bağlayıcıları** sayfasında **Görüntüle'ye** tıklayın.

3. **ICE Chat** ürün açıklaması sayfasında **Bağlayıcı ekle'ye** tıklayın

4. **Hizmet koşulları** sayfasında **Kabul Et'e** tıklayın.

5. **İçerik kaynağı için kimlik bilgileri ekle** sayfasında **PGP ve SSH özel anahtarlarını kullanmak istiyorum'a** tıklayın.

6. 3. Adım'ın altında, aşağıdaki kutulara gerekli bilgileri girin ve Bağlantıyı **doğrula'ya** tıklayın.

      - **Adı:** Bağlayıcının adı. Kuruluşunuzda benzersiz olmalıdır.

      - **Firma kodu:** ICE Chat SFTP sitesinin kullanıcı adı olarak kullanılan kuruluşunuzun kimliği.

      - **Parola:** Kuruluşunuzun ICE Chat SFTP sitesinin parolası.

      - **SFTP URL'si:** ICE Chat SFTP sitesinin URL'si (örneğin, `sftp.theice.com`). Bu değer için bir IP adresi de kullanabilirsiniz.

      - **SFTP bağlantı noktası:** ICE Chat SFTP sitesinin bağlantı noktası numarası. Bağlayıcı, SFTP sitesine bağlanmak için bu bağlantı noktasını kullanır.

      - **PGP özel anahtarı:** ICE Chat SFTP sitesi için PGP özel anahtarı. Anahtar bloğunun başlangıç ve bitiş satırları da dahil olmak üzere özel anahtar değerinin tamamını eklediğinizden emin olun.

      - **PGP anahtar parolası:** PGP özel anahtarının parolası.

      - **SSH özel anahtarı:** ICE Chat SFTP sitesi için SSH özel anahtarı. Anahtar bloğunun başlangıç ve bitiş satırları da dahil olmak üzere özel anahtar değerinin tamamını eklediğinizden emin olun.

      - **SSH anahtarı parolası:** SSH özel anahtarının parolası.

7. Bağlantı başarıyla doğrulandıktan sonra **İleri'ye** tıklayın.

8. **Kullanıcı tanımla** sayfasında, verilerini içeri aktaracak kullanıcıları belirtin.

     - **Kuruluşunuzdaki tüm kullanıcılar**. Tüm kullanıcılar için verileri içeri aktarmak için bu seçeneği belirleyin.

     - **Yalnızca Dava tutan kullanıcılar**. Yalnızca posta kutuları Dava tutmada yer alan kullanıcılar için verileri içeri aktarmak için bu seçeneği belirleyin. Bu seçenek, LitigationHoldEnabled özelliği True olarak ayarlanmış kullanıcı posta kutularına veri aktarır. Daha fazla bilgi için bkz. [Dava tutma oluşturma](create-a-litigation-hold.md).

9. **ICE Chat kullanıcılarını Microsoft 365 kullanıcılara eşle** sayfasında otomatik kullanıcı eşlemesini etkinleştirin ve gerektiğinde özel kullanıcı eşlemesi sağlayın.

   > [!NOTE]
   > Daha önce açıklandığı gibi, özel eşleme dosyası CSV dosyası ICE Chat imid ve her kullanıcı için ilgili Microsoft 365 posta kutusu adresini içerir. Otomatik kullanıcı eşlemesini etkinleştirir ve her sohbet öğesi için özel bir eşleme sağlarsanız bağlayıcı önce özel eşleme dosyasına bakar. Kullanıcının ICE Chat kimliğine karşılık gelen geçerli bir Microsoft 365 kullanıcısı bulamazsa, bağlayıcı öğeyi sohbet öğesinin *SenderEmail* ve *RecipientEmail* özelliklerinde belirtilen kullanıcıların posta kutularına aktarır. Bağlayıcı otomatik veya özel kullanıcı eşlemesi ile geçerli bir Microsoft 365 kullanıcı bulamazsa, öğe içeri aktarılamaz.

10. **İleri'ye** tıklayın, ayarlarınızı gözden geçirin ve ardından **Son'a** tıklayarak bağlayıcıyı oluşturun.

11. Yeni bağlayıcının içeri aktarma işleminin ilerleme durumunu görmek için **Veri bağlayıcıları** sayfasına gidin. Bağlayıcı hakkında bilgi içeren açılır sayfayı görüntülemek için bağlayıcıya tıklayın.
