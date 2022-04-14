---
title: Office 365 için Microsoft Defender'de kimlik avı önleme ilkelerini yapılandırma
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Yöneticiler, Office 365 için Microsoft Defender sahip kuruluşlarda kullanılabilen gelişmiş kimlik avı önleme ilkelerini oluşturmayı, değiştirmeyi ve silmeyi öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: fa7b1519120e349ca2ca99f8bd2df1b21408404d
ms.sourcegitcommit: a7e1d155939e862337271fbe38bf26f62bd49bdd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/14/2022
ms.locfileid: "64847435"
---
# <a name="configure-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'de kimlik avı önleme ilkelerini yapılandırma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[Office 365 için Microsoft Defender'deki](defender-for-office-365.md) kimlik avı önleme ilkeleri, kuruluşunuzun kötü amaçlı kimliğe bürünme tabanlı kimlik avı saldırılarına ve diğer kimlik avı saldırılarına karşı korunmasına yardımcı olabilir. Exchange Online Protection(EOP) içindeki kimlik avı önleme ilkeleri ile Office 365 için Microsoft Defender kimlik avı önleme ilkeleri arasındaki farklar hakkında daha fazla bilgi için bkz. [Kimlik avı koruması](anti-phishing-protection.md).

Yöneticiler varsayılan kimlik avı önleme ilkesini görüntüleyebilir, düzenleyebilir ve yapılandırabilir (ancak silemez). Daha fazla ayrıntı düzeyi için, kuruluşunuzdaki belirli kullanıcılar, gruplar veya etki alanları için geçerli olan özel kimlik avı önleme ilkeleri de oluşturabilirsiniz. Özel ilkeler her zaman varsayılan ilkeden önceliklidir, ancak özel ilkelerinizin önceliğini (çalıştırma sırasını) değiştirebilirsiniz.

Kimlik avı önleme ilkelerini Microsoft 365 Defender portalındaki Office 365 için Defender veya powershell Exchange Online yapılandırabilirsiniz.

Exchange Online Protection 'de (yani Office 365 için Defender olmayan kuruluşlarda) kullanılabilen kimlik avı önleme ilkeleriyle ilgili daha sınırlı yapılandırma hakkında bilgi için bkz. [EOP'de kimlik avı önleme ilkelerini yapılandırma](configure-anti-phishing-policies-eop.md).

Kimlik avı önleme ilkesinin temel öğeleri şunlardır:

- **Kimlik avı önleme ilkesi**: Etkinleştirecek veya devre dışı bırakacağınız kimlik avı korumalarını ve seçeneklerin uygulanacağı eylemleri belirtir.
- **Kimlik avı önleme kuralı: Kimlik avı** önleme ilkesi için öncelik ve alıcı filtrelerini (ilkenin uygulandığı kişiler) belirtir.

Microsoft 365 Defender portalında kimlik avı önleme ilkelerini yönetirken bu iki öğe arasındaki fark belirgin değildir:

- İlke oluşturduğunuzda, aslında her ikisi için de aynı adı kullanarak bir kimlik avı önleme kuralı ve ilişkili kimlik avı önleme ilkesi oluşturursunuz.
- İlkeyi değiştirdiğinizde ad, öncelik, etkin veya devre dışı ile ilgili ayarlar ve alıcı filtreleri kimlik avı önleme kuralını değiştirir. Diğer tüm ayarlar ilişkili kimlik avı önleme ilkesini değiştirir.
- bir ilkeyi kaldırdığınızda, kimlik avı önleme kuralı ve ilişkili kimlik avı önleme ilkesi kaldırılır.

Exchange Online PowerShell'de ilkeyi ve kuralı ayrı ayrı yönetirsiniz. Daha fazla bilgi için bu makalenin devamında yer alan [Kimlik avı önleme ilkelerini yapılandırmak için PowerShell Exchange Online kullanma](#use-exchange-online-powershell-to-configure-anti-phishing-policies) bölümüne bakın.

Her Office 365 için Defender kuruluşun şu özelliklere sahip Office 365 AntiPhish Default adlı yerleşik bir kimlik avı önleme ilkesi vardır:

- İlkeyle ilişkilendirilmiş kimlik avı önleme kuralı (alıcı filtreleri) olmasa bile ilke kuruluştaki tüm alıcılara uygulanır.
- İlke, değiştiremezseniz **en düşük** özel öncelik değerine sahiptir (ilke her zaman en son uygulanır). Oluşturduğunuz tüm özel ilkeler her zaman daha yüksek önceliğe sahiptir.
- İlke varsayılan ilkedir ( **IsDefault** özelliği değerine `True`sahiptir) ve varsayılan ilkeyi silemezsiniz.

Office 365 için Defender'da kimlik avı korumasının verimliliğini artırmak için, belirli kullanıcılara veya kullanıcı gruplarına uygulanan daha katı ayarlara sahip özel kimlik avı önleme ilkeleri oluşturabilirsiniz.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını adresinde <https://security.microsoft.com>açarsınız. Doğrudan **Kimlik avı** önleme sayfasına gitmek için kullanın <https://security.microsoft.com/antiphishing>.

- Exchange Online PowerShell'e bağlanmak için bkz. [PowerShell'Exchange Online Bağlan](/powershell/exchange/connect-to-exchange-online-powershell).

- Bu makaledeki yordamları gerçekleştirebilmeniz için **önce Exchange Online'de** izinlerin atanmış olması gerekir:
  - Kimlik avı önleme ilkelerini eklemek, değiştirmek ve silmek için **Kuruluş Yönetimi** veya **Güvenlik Yöneticisi** rol gruplarının üyesi olmanız gerekir.
  - Kimlik avı önleme ilkelerine salt okunur erişim için **Genel Okuyucu** veya **Güvenlik Okuyucusu** rol gruplarının <sup>\*</sup> üyesi olmanız gerekir.

  Daha fazla bilgi için bkz. [Exchange Online'de İzinler](/exchange/permissions-exo/permissions-exo).

  **Notlar**:

  - kullanıcıları Microsoft 365 yönetim merkezi karşılık gelen Azure Active Directory rolüne eklemek, kullanıcılara Microsoft 365'deki diğer özellikler için gerekli izinleri _ve_ izinleri verir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  - [Exchange Online'daki](/Exchange/permissions-exo/permissions-exo#role-groups) **Yalnızca Görüntüleme Kuruluş Yönetimi** rol grubu da özelliğe salt okunur erişim sağlar.

- Office 365 için Defender'de kimlik avı önleme ilkeleri için önerilen ayarlarımız için Office 365 için Defender [ayarlarındaki Kimlik avı önleme ilkesi bölümüne](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365) bakın.

- Yeni veya güncelleştirilmiş bir ilkenin uygulanması için 30 dakikaya kadar bekleyin.

- Filtreleme işlem hattında kimlik avı önleme ilkelerinin nereye uygulandığı hakkında bilgi için bkz. [E-posta korumasının sırası ve önceliği](how-policies-and-protections-are-combined.md).

## <a name="use-the-microsoft-365-defender-portal-to-create-anti-phishing-policies"></a>Kimlik avı önleme ilkeleri oluşturmak için Microsoft 365 Defender portalını kullanma

Microsoft 365 Defender portalında özel kimlik avı önleme ilkesi oluşturmak, her ikisi için de aynı adı kullanarak kimlik avı önleme kuralını ve ilişkili kimlik avı önleme ilkesini aynı anda oluşturur.

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kimlik avı önleme** bölümüne gidin. Doğrudan **Kimlik avı** önleme sayfasına gitmek için kullanın <https://security.microsoft.com/antiphishing>.

2. **Kimlik avı önleme** sayfasında Oluştur simgesine tıklayın![.](../../media/m365-cc-sc-create-icon.png) **Oluştur'u seçin**.

3. İlke sihirbazı açılır. **İlke adı** sayfasında şu ayarları yapılandırın:
   - **Ad**: İlke için benzersiz, açıklayıcı bir ad girin.
   - **Açıklama**: İlke için isteğe bağlı bir açıklama girin.

   İşiniz bittiğinde **İleri'ye** tıklayın.

4. Görüntülenen **Kullanıcılar, gruplar ve etki alanları sayfasında,** ilkenin geçerli olduğu iç alıcıları tanımlayın (alıcı koşulları):
   - **Kullanıcılar**: Belirtilen posta kutuları, posta kullanıcıları veya posta kişileri.
   - **Gruplar**:
     - Belirtilen dağıtım gruplarının veya posta özellikli güvenlik gruplarının üyeleri.
     - Belirtilen Microsoft 365 Grupları.
   - **Etki alanları**: Kuruluşunuzda belirtilen [kabul edilen etki alanlarındaki](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) tüm alıcılar.

   Uygun kutuya tıklayın, bir değer yazmaya başlayın ve sonuçlardan istediğiniz değeri seçin. Bu işlemi gerektiği kadar tekrarlayın. Mevcut bir değeri kaldırmak için Kaldır'a tıklayın ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) öğesini seçin.

   Kullanıcılar veya gruplar için çoğu tanımlayıcıyı (ad, görünen ad, diğer ad, e-posta adresi, hesap adı vb.) kullanabilirsiniz, ancak sonuçlarda ilgili görünen ad gösterilir. Kullanıcılar için, tüm kullanılabilir değerleri görmek için tek başına bir yıldız işareti (\*) girin.

   Aynı koşuldaki birden çok değer OR mantığını kullanır (örneğin, _\<recipient1\>_ veya _\<recipient2\>_). Farklı koşullar AND mantığını kullanır (örneğin, _\<recipient1\>_ ve _\<member of group 1\>_).

   - **Bu kullanıcıları, grupları ve etki alanlarını dışlayın**: İlkenin geçerli olduğu iç alıcılara özel durumlar eklemek için (yeniden başlanan özel durumlar), bu seçeneği belirleyin ve özel durumları yapılandırın. Ayarlar ve davranış, koşullara tam olarak benzer.

   İşiniz bittiğinde **İleri'ye** tıklayın.

5. Görüntülenen **Kimlik Avı eşiği & koruma** sayfasında aşağıdaki ayarları yapılandırın:

   - **Kimlik avı e-posta eşiği**: Kaydırıcıyı kullanarak aşağıdaki değerlerden birini seçin:
     - **1 - Standart** (Bu varsayılan değerdir.)
     - **2 - Agresif**
     - **3 - Daha agresif**
     - **4 - En agresif**

     Daha fazla bilgi için bkz[. Office 365 için Microsoft Defender'de kimlik avı önleme ilkelerindeki gelişmiş kimlik avı eşikleri](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

   - **Kimliğe Bürünme**: Bu ayarlar, gelen iletilerin Kimden adresinde belirli gönderenleri (tek tek veya etki alanına göre) arayabilecekleri ilkenin bir koşuludur. Daha fazla bilgi için bkz[. Office 365 için Microsoft Defender kimlik avı önleme ilkelerindeki kimliğe bürünme ayarları](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

     > [!NOTE]
     >
     > - Her kimlik avı önleme ilkesinde en fazla 350 korumalı kullanıcı (gönderen e-posta adresleri) belirtebilirsiniz. Birden çok ilkede aynı korumalı kullanıcıyı belirtemezsiniz.
     > - Kullanıcı kimliğe bürünme koruması, gönderen ve alıcı daha önce e-posta yoluyla iletişim kurarsa çalışmaz. Gönderen ve alıcı e-posta yoluyla hiç iletişim kurmadıysa, ileti bir kimliğe bürünme girişimi olarak tanımlanır.

     - **Kullanıcıların korumasını etkinleştir**: Varsayılan değer kapalı (seçili değil). Açmak için onay kutusunu seçin ve ardından görüntülenen **Yönet (nn) gönderenler** bağlantısına tıklayın.

       Görüntülenen **Kimliğe bürünme koruması için gönderenleri yönet** açılır penceresinde aşağıdaki adımları uygulayın:

       - **İç gönderenler: İç** simge ekle'ye tıklayın ![.](../../media/m365-cc-sc-add-internal-icon.png) **İç'i seçin**. Görüntülenen **İç gönderen ekle** açılır penceresinde kutuya tıklayın ve listeden bir iç kullanıcı seçin. Kullanıcıyı yazıp sonuçlardan kullanıcıyı seçerek listeyi filtreleyebilirsiniz. Çoğu tanımlayıcıyı (ad, görünen ad, diğer ad, e-posta adresi, hesap adı vb.) kullanabilirsiniz, ancak sonuçlarda ilgili görünen ad gösterilir.

         Bu adımı gerektiği kadar tekrarlayın. Mevcut bir değeri kaldırmak için Kaldır'a tıklayın ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) öğesini seçin.

         İşiniz bittiğinde **Ekle'ye** tıklayın

       - **Dış gönderenler: Dış ekle** simgesine tıklayın ![.](../../media/m365-cc-sc-create-icon.png) **Dış'ı seçin**. Görüntülenen **Dış gönderen ekle** açılır öğesinde, **Ad ekle** kutusuna bir görünen ad ve Vaild e-posta ekle kutusuna bir **e-posta** adresi girin ve **Ekle'ye** tıklayın.

         Bu adımı gerektiği kadar tekrarlayın. Mevcut bir değeri kaldırmak için Kaldır'a tıklayın ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) öğesini seçin.

         İşiniz bittiğinde **Ekle'ye** tıklayın

       **Kimliğe bürünme için gönderenleri yönet** açılır listesine geri döndüğünüzde, listeden bir veya daha fazla girdi seçerek girdileri kaldırabilirsiniz. Ara simgesini kullanarak ![girdileri arayabilirsiniz.](../../media/m365-cc-sc-create-icon.png) **Arama** kutusu.

       En az bir girdi seçtikten sonra Seçili ![kullanıcıları kaldır simgesi.](../../media/m365-cc-sc-remove-selected-users-icon.png) Seçili girişleri kaldırmak için kullanabileceğiniz **Seçili kullanıcıları kaldır** simgesi görüntülenir.

       İşiniz bittiğinde **Bitti'ye** tıklayın.

     - **Etki alanlarının korunmasını etkinleştir**: Varsayılan değer kapalı (seçili değil). Açmak için onay kutusunu seçin ve ardından görüntülenen aşağıdaki ayarlardan birini veya her ikisini de yapılandırın:
       - **Sahip olduğum etki alanlarını ekle**: Bu ayarı açmak için onay kutusunu seçin. Sahip olduğunuz etki alanlarını görüntülemek için **Etki alanlarımı görüntüle'ye** tıklayın.
       - **Özel etki alanları ekle**: Bu ayarı açmak için onay kutusunu seçin ve ardından görüntülenen **Özel etki alanlarını yönet (nn)** bağlantısına tıklayın. Görüntülenen **Kimliğe bürünme koruması için özel etki alanlarını yönet** açılır penceresinde Etki alanı ekle simgesine tıklayın ![.](../../media/m365-cc-sc-create-icon.png) **Etki alanları ekleyin**.

         Görüntülenen **Özel etki alanları ekle** açılır penceresinde **Etki Alanı** kutusuna tıklayın, bir değer girin ve enter tuşuna basın veya kutunun altında görüntülenen değeri seçin. Bu adımı gerektiği kadar tekrarlayın. Varolan bir değeri kaldırmak için Kaldır ![simgesine tıklayın.](../../media/m365-cc-sc-remove-selection-icon.png) öğesini seçin.

         İşiniz bittiğinde **Etki alanı ekle'ye** tıklayın

         > [!NOTE]
         > Tüm kimlik avı önleme ilkelerinde en fazla 50 etki alanınız olabilir.

       **Kimliğe bürünme için özel etki alanlarını yönet** açılır listesine döndüğünüzde, listeden bir veya daha fazla girdi seçerek girişleri kaldırabilirsiniz. Ara simgesini kullanarak ![girdileri arayabilirsiniz.](../../media/m365-cc-sc-create-icon.png) **Arama** kutusu.

       En az bir girdi seçtikten sonra Etki ![alanlarını sil simgesi.](../../media/m365-cc-sc-delete-icon.png) **Seçili** girişleri kaldırmak için kullanabileceğiniz Sil simgesi görüntülenir.

   - **Güvenilen gönderenler ve etki alanları ekleyin**: **Yönet (nn) güvenilen gönderenler ve etki alanları'na** tıklayarak ilke için kimliğe bürünme koruması özel durumlarını belirtin. Görüntülenen **Kimliğe bürünme koruması için özel etki alanlarını yönet** açılır penceresinde aşağıdaki ayarları yapılandırın:
      - **Gönderenler**: **Gönderen** sekmesinin seçili olduğunu doğrulayın ve Gönderen ekle simgesine tıklayın![.](../../media/m365-cc-sc-create-icon.png) Görüntülenen **Güvenilir gönderen ekle** açılır öğesinde, kutuya bir e-posta adresi girin ve **Ekle'ye** tıklayın. Bu adımı gerektiği kadar tekrarlayın. Var olan bir girdiyi kaldırmak için, girdinin Sil simgesine](../../media/m365-cc-sc-close-icon.png) tıklayın![.

        İşiniz bittiğinde **Ekle'ye** tıklayın.

      - **Etki Alanları**: **Etki Alanı** sekmesini seçin ve Etki alanı ekle simgesine tıklayın ![.](../../media/m365-cc-sc-create-icon.png).

        Görüntülenen **Güvenilen etki alanları ekle** açılır penceresinde **, Etki Alanı** kutusuna tıklayın, bir değer girin ve enter tuşuna basın veya kutunun altında görüntülenen değeri seçin. Bu adımı gerektiği kadar tekrarlayın. Varolan bir değeri kaldırmak için Kaldır ![simgesine tıklayın.](../../media/m365-cc-sc-remove-selection-icon.png) öğesini seçin.

        İşiniz bittiğinde **Ekle'ye** tıklayın.

     **Kimliğe bürünme için özel etki alanlarını yönet** açılır listesine döndüğünüzde, listeden bir veya daha fazla girdi seçerek **Gönderen** ve **Etki Alanı** sekmelerindeki girdileri kaldırabilirsiniz. Ara simgesini kullanarak ![girdileri arayabilirsiniz.](../../media/m365-cc-sc-create-icon.png) **Arama** kutusu.

     En az bir girdiyi seçtikten sonra, seçili girişleri kaldırmak için kullanabileceğiniz **Sil** simgesi görüntülenir.

     İşiniz bittiğinde **Bitti'ye** tıklayın.

     > [!NOTE]
     > En fazla gönderen ve etki alanı girdisi sayısı 1024'tür.

   - **Posta kutusu zekasını etkinleştirme**: Varsayılan değer açık (seçili) ve açık bırakmanızı öneririz. Kapatmak için onay kutusunu temizleyin.

     - **Zeka tabanlı kimliğe bürünme korumasını etkinleştir**: Bu ayar yalnızca **Posta kutusu zekasını etkinleştir** açıksa (seçili) kullanılabilir. Bu ayar, kimliğe bürünme denemesi olarak tanımlanan iletilerde posta kutusu yönetim bilgilerinin eylem gerçekleştirmesini sağlar. Sonraki sayfadaki **Posta kutusu zekası kimliğine bürünülen bir kullanıcı algılarsa** ayarında gerçekleştireceğiniz eylemi belirtirsiniz.

       Onay kutusunu seçerek bu ayarı açmanızı öneririz. Bu ayarı kapatmak için onay kutusunu temizleyin.

   - **Kimlik sahtekarı**: Bu bölümde, kimlik **sahtekarlık zekasını** açmak veya kapatmak için Sahte zekayı etkinleştir onay kutusunu kullanın. Varsayılan değer açık (seçili) ve açık bırakmanızı öneririz. Engellenen sahte gönderenlerden gelen iletilerde gerçekleştireceğiniz eylemi sonraki sayfadaki **Sahte kimlik sahtekarı olarak algılanırsa** ayarında belirtirsiniz.

     Kimlik sahtekarlık zekasını kapatmak için onay kutusunu temizleyin.

     > [!NOTE]
     > MX kaydınız Microsoft 365 işaret etmiyorsa kimlik sahtekarlığı önleme korumasını kapatmanız gerekmez; bunun yerine Bağlayıcılar için Gelişmiş Filtreleme'yi etkinleştirirsiniz. Yönergeler için bkz. [Exchange Online'da Bağlayıcılar için Gelişmiş Filtreleme](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

   İşiniz bittiğinde **İleri'ye** tıklayın.

6. Görüntülenen **Eylemler** sayfasında aşağıdaki ayarları yapılandırın:

   - **İleti eylemleri**: Bu bölümdeki aşağıdaki eylemleri yapılandırın:
     - **İleti kimliğine bürünülen bir kullanıcı olarak algılanırsa**: Bu ayar yalnızca önceki sayfada **Kullanıcıların korunmasını etkinleştir'i** seçtiyseniz kullanılabilir. Gönderenin önceki sayfada belirttiğiniz korumalı kullanıcılardan biri olduğu iletiler için açılan listede aşağıdaki eylemlerden birini seçin:
       - **Hiçbir eylem uygulama**
       - **İletiyi diğer e-posta adreslerine yeniden yönlendirme**
       - **İletiyi alıcıların Gereksiz E-posta klasörlerine taşıma**
       - **İletiyi karantinaya alma**: Bu eylemi seçerseniz, kullanıcı kimliğe bürünme koruması tarafından karantinaya alınan iletilere uygulanan karantina ilkesini seçtiğiniz bir **Karantina ilkesi uygula** kutusu görüntülenir. Karantina ilkeleri, kullanıcıların karantinaya alınan iletilere neler yapabileceğini ve kullanıcıların karantina bildirimleri alıp almayacağını tanımlar. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md).

         Boş **Bir Karantina ilkesi değeri uygula** , varsayılan karantina ilkesinin kullanıldığı anlamına gelir (kullanıcı kimliğe bürünme algılamaları için DefaultFullAccessPolicy). Daha sonra kimlik avı önleme ilkesini düzenlediğinizde veya ayarları görüntülediğinizde varsayılan karantina ilkesi adı gösterilir.
  
       - **İletiyi teslim etme ve Gizli satırına başka adresler ekleme**
       - **İleti teslim etmeden önce silme**

     - **İleti kimliğine bürünülen bir etki alanı olarak algılanırsa**: Bu ayar yalnızca önceki sayfada **Korumak için etki alanlarını etkinleştir'i** seçtiyseniz kullanılabilir. Gönderenin e-posta adresinin önceki sayfada belirttiğiniz korumalı etki alanlarından birinde yer aldığı iletiler için açılan listede aşağıdaki eylemlerden birini seçin:
       - **Hiçbir eylem uygulama**
       - **İletiyi diğer e-posta adreslerine yeniden yönlendirme**
       - **İletiyi alıcıların Gereksiz E-posta klasörlerine taşıma**
       - **İletiyi karantinaya alma**: Bu eylemi seçerseniz, etki alanı kimliğe bürünme koruması tarafından karantinaya alınan iletilere uygulanan karantina ilkesini seçtiğiniz bir **Karantina ilkesi uygula** kutusu görüntülenir.

         Boş **Bir Karantina ilkesi değeri uygula** , varsayılan karantina ilkesinin kullanıldığı anlamına gelir (etki alanı kimliğe bürünme algılamaları için DefaultFullAccessPolicy). Daha sonra kimlik avı önleme ilkesini düzenlediğinizde veya ayarları görüntülediğinizde varsayılan karantina ilkesi adı gösterilir.

       - **İletiyi teslim etme ve Gizli satırına başka adresler ekleme**
       - **İleti teslim etmeden önce silme**

     - **Posta kutusu zekası kimliğine bürünülen bir kullanıcı algılarsa**: Bu ayar yalnızca önceki sayfada **Kimliğe bürünme koruması için zekayı etkinleştir'i** seçtiğinizde kullanılabilir. Posta kutusu zekası tarafından kimliğe bürünme girişimi olarak tanımlanan iletiler için açılan listede aşağıdaki eylemlerden birini seçin:
       - **Hiçbir eylem uygulama**
       - **İletiyi diğer e-posta adreslerine yeniden yönlendirme**
       - **İletiyi alıcıların Gereksiz E-posta klasörlerine taşıma**
       - **İletiyi karantinaya alma**: Bu eylemi seçerseniz, posta kutusu yönetim bilgileri koruması tarafından karantinaya alınan iletilere uygulanan karantina ilkesini seçtiğiniz bir **Karantina ilkesi uygula** kutusu görüntülenir. Karantina ilkeleri, kullanıcıların karantinaya alınan iletilere neler yapabileceğini ve kullanıcıların karantina bildirimleri alıp almayacağını tanımlar. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md).

         Boş **Bir Karantina ilkesi** uygula değeri, varsayılan karantina ilkesinin kullanıldığı anlamına gelir (posta kutusu yönetim bilgileri algılamaları için DefaultFullAccessPolicy). Daha sonra kimlik avı önleme ilkesini düzenlediğinizde veya ayarları görüntülediğinizde varsayılan karantina ilkesi adı gösterilir.

       - **İletiyi teslim etme ve Gizli satırına başka adresler ekleme**
       - **İleti teslim etmeden önce silme**

     - **İleti sahte olarak algılanırsa**: Bu ayar yalnızca önceki sayfada **Kimlik sahtekarlığına izin verin'i** seçtiğinizde kullanılabilir. Engellenen sahte gönderenlerden gelen iletiler için açılan listede aşağıdaki eylemlerden birini seçin:
       - **İletiyi alıcıların Gereksiz E-posta klasörlerine taşıma**
       - **İletiyi karantinaya alma**: Bu eylemi seçerseniz, **kimlik sahtekarlığına karşı koruma tarafından karantinaya** alınan iletilere uygulanan karantina ilkesini seçtiğiniz bir Karantina ilkesi uygula kutusu görüntülenir. Karantina ilkeleri, kullanıcıların karantinaya alınan iletilere neler yapabileceğini ve kullanıcıların karantina bildirimleri alıp almayacağını tanımlar. Daha fazla bilgi için bkz [. Karantina ilkeleri](quarantine-policies.md).

         Boş **Bir Karantina ilkesi değeri uygula** , varsayılan karantina ilkesinin kullanıldığı anlamına gelir (kimlik sahtekarlığı zekası algılamaları için DefaultFullAccessPolicy). Daha sonra kimlik avı önleme ilkesini düzenlediğinizde veya ayarları görüntülediğinizde varsayılan karantina ilkesi adı gösterilir.

   - **Güvenlik ipuçları & göstergeleri**: Aşağıdaki ayarları yapılandırın:
     - **İlk kişi güvenlik ipucu göster**: Daha fazla bilgi için bkz. [İlk kişi güvenlik ipucu](set-up-anti-phishing-policies.md#first-contact-safety-tip).
     - **Kullanıcı kimliğe bürünme güvenlik ipucu göster**: Bu ayar yalnızca önceki sayfada **Kullanıcıların korunmasını etkinleştir'i** seçtiyseniz kullanılabilir.
     - **Etki alanı kimliğe bürünme güvenlik ipucu göster**: Bu ayar yalnızca önceki sayfada **Korumak için etki alanlarını etkinleştir'i** seçtiyseniz kullanılabilir.
     - **Kullanıcı kimliğine bürünme olağan dışı karakterleri güvenlik ipucu Göster** Bu ayar yalnızca **Önceki sayfada Kullanıcıların korumasını etkinleştir** veya **Etki alanlarını korumak için etkinleştir'i** seçtiyseniz kullanılabilir.
     - Kimlik **sahtekarlığına yönelik kimliği doğrulanmamış gönderenler için göster (?)** : Bu ayar yalnızca önceki sayfada **Kimlik sahtekarı zekasını etkinleştir'i** seçtiyseniz kullanılabilir. İleti SPF veya DKIM denetimlerini geçmezse **ve** ileti DMARC veya [bileşik kimlik doğrulamasını](email-validation-and-authentication.md#composite-authentication) geçmezse, Outlook kimden kutusunda gönderenin fotoğrafına bir soru işareti (?) ekler.
     - **"Via" etiketini göster**: Bu ayar yalnızca önceki sayfada **Sahte zekayı etkinleştir'i** seçtiyseniz kullanılabilir. DKIM imzasında etki alanından veya **MAIL FROM** adresinden farklıysa Kimden adresine bir via etiketi (fabrikam.com aracılığıyla chris@contoso.com) ekler. Varsayılan değer açık (seçili). Kapatmak için onay kutusunu temizleyin.

     Bir ayarı açmak için onay kutusunu seçin. Kapatmak için onay kutusunu temizleyin.

   İşiniz bittiğinde **İleri'ye** tıklayın.

7. Görüntülenen **Gözden Geçir** sayfasında ayarlarınızı gözden geçirin. Bölümün içindeki ayarları değiştirmek için her bölümde **Düzenle'yi** seçebilirsiniz. Ya da **Geri'ye** tıklayabilir veya sihirbazdaki belirli bir sayfayı seçebilirsiniz.

   İşiniz bittiğinde **Gönder'e** tıklayın.

8. Görüntülenen onay sayfasında **Bitti'ye** tıklayın.

## <a name="use-the-microsoft-365-defender-portal-to-view-anti-phishing-policies"></a>Kimlik avı önleme ilkelerini görüntülemek için Microsoft 365 Defender portalını kullanma

1. Microsoft 365 Defender portalında, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kimlik avı önleme** bölümüne gidin.

2. **Kimlik avı önleme** sayfasında, kimlik avı önleme ilkeleri listesinde aşağıdaki özellikler görüntülenir:

   - **Ad**
   - **Durum**
   - **Öncelik**
   - **Son değiştirme**

3. Ada tıklayarak bir ilke seçtiğinizde, ilke ayarları açılır öğede görüntülenir.

## <a name="use-the-microsoft-365-defender-portal-to-modify-anti-phishing-policies"></a>Kimlik avı önleme ilkelerini değiştirmek için Microsoft 365 Defender portalını kullanma

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kimlik avı önleme** bölümüne gidin. Doğrudan **Kimlik avı** önleme sayfasına gitmek için kullanın <https://security.microsoft.com/antiphishing>.

2. **Kimlik avı önleme** sayfasında, ada tıklayarak listeden bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinde, bölümdeki ayarları değiştirmek için her bölümde **Düzenle'yi** seçin. Ayarlar hakkında daha fazla bilgi için bu [makalenin önceki bölümlerinde yer alan Microsoft 365 Defender portalını kullanarak kimlik avı önleme ilkeleri oluşturma](#use-the-microsoft-365-defender-portal-to-create-anti-phishing-policies) bölümüne bakın.

   Varsayılan kimlik avı önleme ilkesi için **Kullanıcılar, gruplar ve etki alanları** bölümü kullanılamaz (ilke herkes için geçerlidir) ve ilkeyi yeniden adlandıramazsınız.

bir ilkeyi etkinleştirmek veya devre dışı bırakmak ya da ilke öncelik sırasını ayarlamak için aşağıdaki bölümlere bakın.

### <a name="enable-or-disable-custom-anti-phishing-policies"></a>Özel kimlik avı önleme ilkelerini etkinleştirme veya devre dışı bırakma

Varsayılan kimlik avı önleme ilkesini devre dışı bırakamazsınız.

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kimlik avı önleme** bölümüne gidin. Doğrudan **Kimlik avı** önleme sayfasına gitmek için kullanın <https://security.microsoft.com/antiphishing>.

2. **Kimlik avı önleme** sayfasında, ada tıklayarak listeden özel bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinin en üstünde aşağıdaki değerlerden birini görürsünüz:
   - **İlke kapalı**: İlkeyi açmak için Aç simgesine tıklayın ![.](../../media/m365-cc-sc-turn-on-off-icon.png) **seçeneğini açın** .
   - **İlke açık**: İlkeyi kapatmak için Kapat simgesine tıklayın ![.](../../media/m365-cc-sc-turn-on-off-icon.png) **Kapat'a gidin**.

4. Görüntülenen onay iletişim kutusunda **Aç** veya **Kapat'a** tıklayın.

5. İlke ayrıntıları açılır öğesinde **Kapat'a** tıklayın.

Ana ilke sayfasına döndüğünüzde, ilkenin **Durum** değeri **Açık** veya **Kapalı** olur.

### <a name="set-the-priority-of-custom-anti-phishing-policies"></a>Özel kimlik avı önleme ilkelerinin önceliğini ayarlama

Varsayılan olarak, kimlik avı önleme ilkelerine oluşturuldukları sırayı temel alan bir öncelik verilir (daha yeni ilkeler eski ilkelerden daha düşük önceliklidir). Düşük öncelik numarası, ilke için daha yüksek bir önceliği gösterir (0 en yüksek önceliktir) ve ilkeler öncelik sırasına göre işlenir (yüksek öncelikli ilkeler düşük öncelikli ilkelerden önce işlenir). hiçbir iki ilke aynı önceliğe sahip olamaz ve ilke işleme ilk ilke uygulandıktan sonra durur.

İlkenin önceliğini değiştirmek için, ilkenin özelliklerinde **Önceliği artır** veya **Önceliği azalt'a** tıklayın (Microsoft 365 Defender portalında **Öncelik** numarasını doğrudan değiştiremezsiniz). İlkenin önceliğini değiştirmek yalnızca birden çok ilkeniz varsa mantıklıdır.

 **Notlar**:

- Microsoft 365 Defender portalında, kimlik avı önleme ilkesinin önceliğini yalnızca oluşturduktan sonra değiştirebilirsiniz. PowerShell'de, kimlik avı önleme kuralını oluştururken varsayılan önceliği geçersiz kılabilirsiniz (bu, mevcut kuralların önceliğini etkileyebilir).
- Kimlik avı önleme ilkeleri, görüntülendikleri sırayla işlenir (ilk **ilkenin Öncelik** değeri 0'dır). Varsayılan kimlik avı önleme ilkesi **En düşük** öncelik değerine sahiptir ve bunu değiştiremezsiniz.

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kimlik avı önleme** bölümüne gidin. Doğrudan **Kimlik avı** önleme sayfasına gitmek için kullanın <https://security.microsoft.com/antiphishing>.

2. **Kimlik avı önleme** sayfasında, ada tıklayarak listeden özel bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinin en üstünde, Geçerli öncelik değerine ve özel ilkelerin sayısına göre **Önceliği artır** veya **Önceliği azalt** seçeneğini görürsünüz:
   - **Öncelik** değeri **0** olan ilkede yalnızca **Önceliği azalt** seçeneği kullanılabilir.
   - En düşük **Öncelik** değerine sahip ilke (örneğin, **3**) yalnızca **Önceliği artır** seçeneği kullanılabilir.
   - Üç veya daha fazla ilkeniz varsa, en yüksek ve en düşük öncelik değerleri arasındaki ilkeler hem **Önceliği artır** hem de **Önceliği azalt** seçeneklerine sahiptir.

   Önceliği artır simgesine tıklayın ![.](../../media/m365-cc-sc-increase-icon.png) Öncelik **değerini değiştirmek** için **Önceliği artır** veya ![Önceliği azalt simgesi](../../media/m365-cc-sc-decrease-icon.png) Önceliği **azalt'ı** seçin.

4. İşiniz bittiğinde ilke ayrıntıları açılır öğesinde **Kapat'a** tıklayın.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-anti-phishing-policies"></a>Özel kimlik avı önleme ilkelerini kaldırmak için Microsoft 365 Defender portalını kullanma

Özel bir kimlik avı önleme ilkesini kaldırmak için Microsoft 365 Defender portalını kullandığınızda, kimlik avı önleme kuralı ve buna karşılık gelen kimlik avı önleme ilkesi silinir. Varsayılan kimlik avı önleme ilkesini kaldıramazsınız.

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>, **İlkeler** bölümünde **e-posta & İşbirliği** \> **İlkeleri & Kurallar** \> **Tehdit ilkeleri** \> **Kimlik avı önleme** bölümüne gidin. Doğrudan **Kimlik avı** önleme sayfasına gitmek için kullanın <https://security.microsoft.com/antiphishing>.

2. **Kimlik avı önleme** sayfasında, ilkenin adına tıklayarak listeden özel bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinin üst kısmında Diğer eylemler simgesine tıklayın ![.](../../media/m365-cc-sc-more-actions-icon.png) **Diğer eylemler** \> ![İlkeyi sil simgesi **İlkeyi**](../../media/m365-cc-sc-delete-icon.png) sil.

4. Görüntülenen onay iletişim kutusunda **Evet'e** tıklayın.

## <a name="use-exchange-online-powershell-to-configure-anti-phishing-policies"></a>Kimlik avı önleme ilkelerini yapılandırmak için Exchange Online PowerShell kullanma

Daha önce açıklandığı gibi, istenmeyen posta önleme ilkesi bir kimlik avı önleme ilkesinden ve kimlik avından koruma kuralından oluşur.

Exchange Online PowerShell'de kimlik avı önleme ilkeleriyle kimlik avı önleme kuralları arasındaki fark belirgindir. **-AntiPhishPolicy cmdlet'lerini kullanarak\*** kimlik avı önleme ilkelerini yönetirsiniz ve **-AntiPhishRule cmdlet'lerini kullanarak\*** kimlik avı önleme kurallarını yönetirsiniz.

- PowerShell'de önce kimlik avı önleme ilkesini oluşturursunuz, ardından kuralın uygulandığı ilkeyi tanımlayan kimlik avı önleme kuralını oluşturursunuz.
- PowerShell'de, kimlik avı önleme ilkesindeki ayarları ve kimlik avı önleme kuralını ayrı ayrı değiştirirsiniz.
- PowerShell'den kimlik avı önleme ilkesini kaldırdığınızda, buna karşılık gelen kimlik avı önleme kuralı otomatik olarak kaldırılmaz ve tam tersi de geçerlidir.

### <a name="use-powershell-to-create-anti-phishing-policies"></a>Kimlik avı önleme ilkeleri oluşturmak için PowerShell kullanma

PowerShell'de kimlik avı önleme ilkesi oluşturmak iki adımlı bir işlemdir:

1. Kimlik avı önleme ilkesini oluşturun.
2. Kuralın geçerli olduğu kimlik avı önleme ilkesini belirten kimlik avı önleme kuralını oluşturun.

 **Notlar**:

- Yeni bir kimlik avı önleme kuralı oluşturabilir ve bu kurala mevcut, ilişkilendirilmemiş bir kimlik avı önleme ilkesi atayabilirsiniz. Kimlik avı önleme kuralı birden fazla kimlik avı önleme ilkesiyle ilişkilendirilebilir.
- İlkeyi oluşturana kadar PowerShell'de Microsoft 365 Defender portalında bulunmayan yeni kimlik avı önleme ilkelerinde aşağıdaki ayarları yapılandırabilirsiniz:
  - Yeni ilkeyi devre dışı olarak oluşturun (**New-AntiPhishRule** cmdlet'inde _etkindir_`$false`).
  - **New-AntiPhishRule** cmdlet'inde oluşturma sırasında ilkenin _önceliğini_ _\<Number\>_ ayarlayın (Öncelik ).
- PowerShell'de oluşturduğunuz yeni bir kimlik avı önleme ilkesi, ilkeyi bir kimlik avı önleme kuralına atayana kadar Microsoft 365 Defender portalında görünmez.

#### <a name="step-1-use-powershell-to-create-an-anti-phish-policy"></a>1. Adım: Kimlik avı önleme ilkesi oluşturmak için PowerShell kullanma

Kimlik avı önleme ilkesi oluşturmak için şu söz dizimlerini kullanın:

```PowerShell
New-AntiPhishPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

Bu örnek, aşağıdaki ayarlarla Research Quarantine adlı bir kimlik avı önleme ilkesi oluşturur:

- İlke etkindir ( _Enabled_ parametresini kullanmıyoruz ve varsayılan değerdir `$true`).
- Açıklama: Araştırma departmanı ilkesi.
- Kimlik sahtekarlığı algılamaları için varsayılan eylemi Karantina olarak değiştirir ve karantinaya alınan iletiler için varsayılan [karantina ilkesini](quarantine-policies.md) kullanır ( _SpoofQuarantineTag_ parametresini kullanmıyoruz).
- Tüm kabul edilen etki alanları için kuruluş etki alanları korumasını ve fabrikam.com için hedeflenen etki alanları korumasını etkinleştirir.
- Etki alanı kimliğe bürünme algılamaları için eylem olarak Karantina'yı belirtir ve karantinaya alınan iletiler için varsayılan [karantina ilkesini](quarantine-policies.md) kullanır ( _TargetedDomainQuarantineTag_ parametresini kullanmıyoruz).
- Kimliğe bürünmeye karşı korunacak kullanıcı olarak Mai Fujito (mfujito@fabrikam.com) belirtir.
- Kullanıcı kimliğe bürünme algılamaları için eylem olarak Karantina'yı belirtir ve karantinaya alınan iletiler için varsayılan [karantina ilkesini](quarantine-policies.md) kullanır ( _TargetedUserQuarantineTag_ parametresini kullanmıyoruz).
- Posta kutusu zekasını etkinleştirir (_EnableMailboxIntelligence_), posta kutusu zekası korumasının iletilerde eylem gerçekleştirmesine izin verir (_EnableMailboxIntelligenceProtection_), algılanan iletiler için eylem olarak Karantina'yı belirtir ve karantinaya alınan iletiler için varsayılan [karantina ilkesini](quarantine-policies.md) kullanır ( _MailboxIntelligenceQuarantineTag_ parametresini kullanmıyoruz).
- Tüm güvenlik ipuçlarını etkinleştirir.

```powershell
New-AntiPhishPolicy -Name "Monitor Policy" -AdminDisplayName "Research department policy" -AuthenticationFailAction Quarantine -EnableOrganizationDomainsProtection $true -EnableTargetedDomainsProtection $true -TargetedDomainsToProtect fabrikam.com -TargetedDomainProtectionAction Quarantine -EnableTargetedUserProtection $true -TargetedUsersToProtect "Mai Fujito;mfujito@fabrikam.com" -TargetedUserProtectionAction Quarantine -EnableMailboxIntelligence $true -EnableMailboxIntelligenceProtection $true -MailboxIntelligenceProtectionAction Quarantine -EnableSimilarUsersSafetyTips $true -EnableSimilarDomainsSafetyTips $true -EnableUnusualCharactersSafetyTips $true
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-AntiPhishPolicy](/powershell/module/exchange/New-AntiPhishPolicy).

> [!NOTE]
> Kimlik avı önleme [ilkesinde kullanılacak karantina ilkelerini](quarantine-policies.md) belirtmeye yönelik ayrıntılı yönergeler için bkz. Kimlik [avı önleme ilkelerinde karantina ilkesini belirtmek için PowerShell kullanma](quarantine-policies.md#anti-phishing-policies).

#### <a name="step-2-use-powershell-to-create-an-anti-phish-rule"></a>2. Adım: Kimlik avı önleme kuralı oluşturmak için PowerShell kullanma

Kimlik avı önleme kuralı oluşturmak için şu sözdizimini kullanın:

```PowerShell
New-AntiPhishRule -Name "<RuleName>" -AntiPhishPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

Bu örnek, aşağıdaki koşullara sahip Araştırma Bölümü adlı bir kimlik avı önleme kuralı oluşturur:

- Kural, Araştırma Karantinası adlı kimlik avı önleme ilkesiyle ilişkilendirilir.
- Kural, Araştırma Bölümü adlı grubun üyeleri için geçerlidir.
- _Priority_ parametresini kullanmadığımız için varsayılan öncelik kullanılır.

```powershell
New-AntiPhishRule -Name "Research Department" -AntiPhishPolicy "Research Quarantine" -SentToMemberOf "Research Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [New-AntiPhishRule](/powershell/module/exchange/New-AntiPhishRule).

### <a name="use-powershell-to-view-anti-phish-policies"></a>Kimlik avı önleme ilkelerini görüntülemek için PowerShell kullanma

Mevcut kimlik avı önleme ilkelerini görüntülemek için aşağıdaki söz dizimini kullanın:

```PowerShell
Get-AntiPhishPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Bu örnek, belirtilen özelliklerle birlikte tüm kimlik avı önleme ilkelerinin özet listesini döndürür.

```PowerShell
Get-AntiPhishPolicy | Format-Table Name,IsDefault
```

Bu örnek, Yöneticiler adlı kimlik avı önleme ilkesinin tüm özellik değerlerini döndürür.

```PowerShell
Get-AntiPhishPolicy -Identity "Executives"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-AntiPhishPolicy](/powershell/module/exchange/Get-AntiPhishPolicy).

### <a name="use-powershell-to-view-anti-phish-rules"></a>Kimlik avı önleme kurallarını görüntülemek için PowerShell kullanma

Mevcut kimlik avı önleme kurallarını görüntülemek için aşağıdaki söz dizimini kullanın:

```PowerShell
Get-AntiPhishRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Bu örnek, belirtilen özelliklerle birlikte tüm kimlik avı önleme kurallarının özet listesini döndürür.

```PowerShell
Get-AntiPhishRule | Format-Table Name,Priority,State
```

Listeyi etkin veya devre dışı kurallara göre filtrelemek için aşağıdaki komutları çalıştırın:

```PowerShell
Get-AntiPhishRule -State Disabled | Format-Table Name,Priority
```

```PowerShell
Get-AntiPhishRule -State Enabled | Format-Table Name,Priority
```

Bu örnek, Contoso Executives adlı kimlik avı önleme kuralının tüm özellik değerlerini döndürür.

```PowerShell
Get-AntiPhishRule -Identity "Contoso Executives"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-AntiPhishRule](/powershell/module/exchange/Get-AntiPhishrule).

### <a name="use-powershell-to-modify-anti-phish-policies"></a>Kimlik avı önleme ilkelerini değiştirmek için PowerShell kullanma

Aşağıdaki öğeler dışında, PowerShell'de kimlik avı önleme ilkesini değiştirdiğinizde, ilkeyi [1. Adım: PowerShell kullanarak](#step-1-use-powershell-to-create-an-anti-phish-policy) bu makalenin önceki bölümlerinde açıklanan kimlik avı önleme ilkesi bölümünde açıklandığı gibi aynı ayarlar kullanılabilir.

- Belirtilen ilkeyi varsayılan ilkeye dönüştüren _MakeDefault_ anahtarı (herkese uygulanır, her zaman **En düşük** önceliklidir ve bunu silemezsiniz) yalnızca PowerShell'de kimlik avı önleme ilkesini değiştirdiğinizde kullanılabilir.

- Kimlik avı önleme ilkesini yeniden adlandıramazsınız ( **Set-AntiPhishPolicy** cmdlet'inde _Name_ parametresi yoktur). Microsoft 365 Defender portalında bir kimlik avı önleme ilkesini yeniden adlandırdığınızda, yalnızca kimlik avı önleme _kuralını_ yeniden adlandırırsınız.

Kimlik avı önleme ilkesini değiştirmek için şu söz dizimlerini kullanın:

```PowerShell
Set-AntiPhishPolicy -Identity "<PolicyName>" <Settings>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-AntiPhishPolicy](/powershell/module/exchange/Set-AntiPhishPolicy).

> [!NOTE]
> Kimlik avı önleme [ilkesinde kullanılacak karantina ilkelerini](quarantine-policies.md) belirtmeye yönelik ayrıntılı yönergeler için bkz. Kimlik [avı önleme ilkelerinde karantina ilkesini belirtmek için PowerShell kullanma](quarantine-policies.md#anti-phishing-policies).

### <a name="use-powershell-to-modify-anti-phish-rules"></a>Kimlik avı önleme kurallarını değiştirmek için PowerShell kullanma

PowerShell'de kimlik avı önleme kuralını değiştirdiğinizde kullanılamayabilecek tek ayar, devre dışı bırakılmış bir kural oluşturmanıza olanak tanıyan _Etkin_ parametresidir. Mevcut kimlik avı önleme kurallarını etkinleştirmek veya devre dışı bırakmak için sonraki bölüme bakın.

Aksi takdirde, PowerShell'de kimlik avı önleme kuralını değiştirdiğinizde ek ayar kullanılamaz. Bu makalenin önceki bölümlerinde yer alan [2. Adım: PowerShell kullanarak kimlik avı önleme kuralı oluşturma](#step-2-use-powershell-to-create-an-anti-phish-rule) bölümünde açıklandığı gibi bir kural oluşturduğunuzda da aynı ayarlar kullanılabilir.

Kimlik avı önleme kuralını değiştirmek için şu söz dizimlerini kullanın:

```PowerShell
Set-AntiPhishRule -Identity "<RuleName>" <Settings>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Set-AntiPhishRule](/powershell/module/exchange/set-antiphishrule).

### <a name="use-powershell-to-enable-or-disable-anti-phish-rules"></a>Kimlik avı önleme kurallarını etkinleştirmek veya devre dışı bırakmak için PowerShell kullanma

PowerShell'de kimlik avı önleme kuralının etkinleştirilmesi veya devre dışı bırakılması, kimlik avı önleme ilkesinin tamamını (kimlik avı önleme kuralı ve atanan kimlik avı önleme ilkesi) etkinleştirir veya devre dışı bırakır. Varsayılan kimlik avı önleme ilkesini etkinleştiremez veya devre dışı bırakamazsınız (her zaman tüm alıcılara uygulanır).

PowerShell'de kimlik avı önleme kuralını etkinleştirmek veya devre dışı bırakmak için şu sözdizimini kullanın:

```PowerShell
<Enable-AntiPhishRule | Disable-AntiPhishRule> -Identity "<RuleName>"
```

Bu örnek, Pazarlama Departmanı adlı kimlik avı önleme kuralını devre dışı bırakır.

```PowerShell
Disable-AntiPhishRule -Identity "Marketing Department"
```

Bu örnek aynı kuralı etkinleştirir.

```PowerShell
Enable-AntiPhishRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Enable-AntiPhishRule](/powershell/module/exchange/enable-antiphishrule) ve [Disable-AntiPhishRule](/powershell/module/exchange/disable-antiphishrule).

### <a name="use-powershell-to-set-the-priority-of-anti-phish-rules"></a>Kimlik avı önleme kurallarının önceliğini ayarlamak için PowerShell kullanma

Bir kuralda ayarlayabileceğiniz en yüksek öncelik değeri 0'dır. Ayarlayabileceğiniz en düşük değer, kural sayısına bağlıdır. Örneğin, beş kuralınız varsa, 0 ile 4 arasında öncelik değerlerini kullanabilirsiniz. Mevcut bir kuralın önceliğini değiştirmek, diğer kurallar üzerinde basamaklı bir etkiye sahip olabilir. Örneğin, beş özel kuralınız (öncelik 0 ile 4 arasında) varsa ve bir kuralın önceliğini 2 olarak değiştirirseniz, 2 önceliği olan mevcut kural öncelik 3'e, öncelik 3'e sahip kural ise öncelik 4 olarak değiştirilir.

PowerShell'de kimlik avı önleme kuralının önceliğini ayarlamak için aşağıdaki söz dizimini kullanın:

```PowerShell
Set-AntiPhishRule -Identity "<RuleName>" -Priority <Number>
```

Bu örnek, Pazarlama Departmanı adlı kuralın önceliğini 2 olarak ayarlar. Önceliğe 2'den küçük veya 2'ye eşit olan tüm mevcut kurallar 1 azaltılır (öncelik sayıları 1 artırılır).

```PowerShell
Set-AntiPhishRule -Identity "Marketing Department" -Priority 2
```

**Notlar**:

- Yeni kuralı oluştururken önceliği ayarlamak için, bunun yerine **New-AntiPhishRule** cmdlet'indeki _Priority_ parametresini kullanın.

- Varsayılan kimlik avı önleme ilkesinin karşılık gelen bir kimlik avı önleme kuralı yoktur ve her zaman **değiştirilemez öncelik değeri En Düşük'e** sahiptir.

### <a name="use-powershell-to-remove-anti-phish-policies"></a>Kimlik avı önleme ilkelerini kaldırmak için PowerShell kullanma

Bir kimlik avı önleme ilkesini kaldırmak için PowerShell kullandığınızda, buna karşılık gelen kimlik avı önleme kuralı kaldırılmaz.

PowerShell'de kimlik avı önleme ilkesini kaldırmak için şu sözdizimini kullanın:

```PowerShell
Remove-AntiPhishPolicy -Identity "<PolicyName>"
```

Bu örnek, Pazarlama Departmanı adlı kimlik avı önleme ilkesini kaldırır.

```PowerShell
Remove-AntiPhishPolicy -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-AntiPhishPolicy](/powershell/module/exchange/Remove-AntiPhishPolicy).

### <a name="use-powershell-to-remove-anti-phish-rules"></a>Kimlik avı önleme kurallarını kaldırmak için PowerShell kullanma

PowerShell kullanarak kimlik avı önleme kuralını kaldırdığınızda, ilgili kimlik avı önleme ilkesi kaldırılmaz.

PowerShell'de kimlik avı önleme kuralını kaldırmak için şu sözdizimini kullanın:

```PowerShell
Remove-AntiPhishRule -Identity "<PolicyName>"
```

Bu örnek, Pazarlama Departmanı adlı kimlik avı önleme kuralını kaldırır.

```PowerShell
Remove-AntiPhishRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-AntiPhishRule](/powershell/module/exchange/Remove-AntiPhishRule).

## <a name="how-do-you-know-these-procedures-worked"></a>Bu yordamların işe yaramış olduğunu nasıl anlarsınız?

Office 365 için Defender'de kimlik avı önleme ilkelerini başarıyla yapılandırdığınızdan emin olmak için aşağıdaki adımlardan birini yapın:

- konumundaki Microsoft 365 Defender portalındaki <https://security.microsoft.com/antiphishing>**Kimlik Avı önleme** sayfasında ilkelerin listesini, **Durum** değerlerini ve **Öncelik** değerlerini doğrulayın. Daha fazla ayrıntı görüntülemek için, ada tıklayıp görüntülenen açılır listede ayrıntıları görüntüleyerek ilkeyi seçin.

- Exchange Online PowerShell'de öğesini ilkenin veya kuralın adıyla değiştirin \<Name\> ve aşağıdaki komutu çalıştırıp ayarları doğrulayın:

  ```PowerShell
  Get-AntiPhishPolicy -Identity "<Name>"
  ```

  ```PowerShell
  Get-AntiPhishRule -Identity "<Name>"
  ```
