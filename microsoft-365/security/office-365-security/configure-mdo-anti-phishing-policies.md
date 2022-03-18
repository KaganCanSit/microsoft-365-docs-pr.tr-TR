---
title: Kimlik avıyla mücadele ilkelerini Microsoft Defender'da Office 365
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
description: Yöneticiler, kimlik avı için Microsoft Defender'a sahip kuruluşlarda kullanılabilen gelişmiş kimlik avı ilkelerinin nasıl oluşturulsa, değiştirilebilir ve silin Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 5faf4533110fe5abad8606c9c859f82549dc2fce
ms.sourcegitcommit: 677dcc74aa898b2a17eb8430a32e675fea4e3fe5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63557929"
---
# <a name="configure-anti-phishing-policies-in-microsoft-defender-for-office-365"></a>Kimlik avıyla mücadele ilkelerini Microsoft Defender'da Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

[Office 365 için Microsoft Defender'daki](defender-for-office-365.md) kimlik avı koruma ilkeleri, organizasyonlarınızı kötü amaçlı kimliğe bürünme tabanlı kimlik avı saldırılarına ve diğer kimlik avı saldırılarına karşı korumaya yardımcı olabilir. Exchange Online Protection(EOP) ve Office 365 için Microsoft Defender'daki kimlik avı önleme ilkeleri arasındaki farklar hakkında daha fazla bilgi için [bkz. Kimlik](anti-phishing-protection.md) avından korunma.

Yöneticiler varsayılan kimlik avı önleme ilkesi  görüntüleyemez, düzenleyebilir ve yapılandırsa da (ancak silemez). Daha ayrıntılı bilgi için, aynı zamanda, kurumlu belirli kullanıcılara, gruplara veya etki alanlarına uygulanacak özel kimlik avı ilkeleri de oluşturabilirsiniz. Özel ilkeler her zaman varsayılan ilkeden önceliğe sahiptir, ancak özel ilkelerinizin önceliğini (çalışma sırası) değiştirebilirsiniz.

kimlik avı önleme ilkelerini, Microsoft 365 Defender portalında veya Exchange Online PowerShell'de Office 365 için Defender'da yapılandırabilirsiniz.

Exchange Online Protection'ta bulunan kimlik avı önleme ilkelerde (başka bir ifadeyle, Office 365 için Defender olmayan kuruluşlar) daha sınırlı kimlik avı ilkeleri yapılandırma hakkında bilgi için bkz. [EOP'de](configure-anti-phishing-policies-eop.md) kimlik avı önleme ilkelerini yapılandırma.

Kimlik avı önleme ilkesi için temel öğeler:

- **Kimlik avı koruma ilkesi**: Etkinleştirmek veya devre dışı bırakmak için kimlik avı korumalarını ve seçeneklerin uygulanacak eylemlerini belirtir.
- **Kimlik avı koruma kuralı**: Kimlik avı önleme ilkesi için önceliği ve alıcı filtrelerini (ilkenin geçerli olduğu) belirtir.

Bu iki öğe arasındaki fark, kimlik avı önleme ilkelerini aşağıdaki portalda yönetirken Microsoft 365 Defender değildir:

- Bir ilke  oluştururken, aslında bir kimlik avı koruma kuralı ve ilişkili kimlik avı önleme ilkesi de, ikisi için aynı adı kullanarak aynı anda oluşturulur.
- Bir ilkeyi değiştirdikten sonra ad, öncelik, etkin veya devre dışıyla ilgili ayarlar ve alıcı filtreleri kimlik avı koruma kuralını değiştirir. Diğer tüm ayarlar, ilişkili kimlik avı önleme ilkesine değişiklik sağlar.
- Bir ilkeyi kaldıran, kimlik avı önleme kuralı ve ilişkili kimlik avı önleme ilkesi kaldırılır.

PowerShell Exchange Online, ilkeyi ve kuralı ayrı ayrı yönetirsiniz. Daha fazla bilgi için, bu [makalenin devam Exchange Online kimlik](#use-exchange-online-powershell-to-configure-anti-phishing-policies) avı ilkelerini yapılandırmak için PowerShell kullanma bölümüne bakın.

Her kullanıcı için Office 365 Defender'ın, bu özelliklere sahip olan Office 365 AntiPhish Default adlı yerleşik bir kimlik avı önleme ilkesi vardır:

- İlkeyle ilişkilendirilmiş kimlik avı koruma kuralı (alıcı filtreleri) her ne kadar ilke kuruluşta yer alan tüm alıcılara uygulanır.
- İlke, değiştiriy **olmadığınız** en düşük özel öncelik değerine sahiptir (ilke her zaman en son uygulanır). Sizin kendi özel ilkeleriniz her zaman daha yüksek önceliğe sahiptir.
- İlke varsayılan ilkedir ( **değeri IsDefault** özelliğine `True`sahip) ve varsayılan ilkeyi silemezsiniz.

Office 365 için Defender'da kimlik avı korumasının etkisini artırmak için, belirli kullanıcılara veya kullanıcı gruplarına daha sıkı ayarlar uygulanmış özel kimlik avı önleme ilkeleri oluşturabilirsiniz.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açın<https://security.microsoft.com>. Doğrudan Kimlik avı önleme **sayfasına gitmek için** kullanın <https://security.microsoft.com/antiphishing>.

- Exchange Online PowerShell'e bağlanmak [için bkz. Bağlan PowerShell Exchange Online e bağlama](/powershell/exchange/connect-to-exchange-online-powershell).

- Bu makaledeki yordamları **yerine Exchange Online** önce Bu makalede izinlerin atanmamış olması gerekir:
  - Kimlik avı önleme ilkeleri eklemek, değiştirmek ve silmek için, Kuruluş Yönetimi veya Güvenlik Yöneticisi rol **gruplarının üyesi olun**.
  - Kimlik avı önleme ilkelerine salt okunur erişim için, Genel Okuyucu veya Güvenlik Okuyucusu rol **gruplarının üyesi** olun <sup>\*</sup>.

  Daha fazla bilgi için bkz. [Exchange Online](/exchange/permissions-exo/permissions-exo).

  **Notlar**:

  - Görev sırasında ilgili kullanıcı Azure Active Directory eklemek Microsoft 365 yönetim merkezi kullanıcılara çalışma sayfalarındaki diğer özellikler için gerekli izinleri ve izinleri Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  - **Görünüm'de Yalnızca Görüntüleme** [kuruluş Exchange Online rol](/Exchange/permissions-exo/permissions-exo#role-groups) grubu, özel salt okunur erişim de sağlar.

- Daha fazla bilgi için bkz. Office 365 için Defender'da kimlik avı önleme ilkeleri için önerilen ayarlarımız için, güvenlik ayarları için [Defender'da](recommended-settings-for-eop-and-office365.md#anti-phishing-policy-settings-in-microsoft-defender-for-office-365) kimlik Office 365 bakın.

- Yeni veya güncelleştirilmiş ilkenin uygulanması için 30 dakika kadar bekleyin.

- Kimlik avı önleme ilkelerinin filtre potansiyelinde nereye uygulandığı hakkında bilgi için bkz. [E-posta korumasının sırası ve önceliği](how-policies-and-protections-are-combined.md).

## <a name="use-the-microsoft-365-defender-portal-to-create-anti-phishing-policies"></a>Kimlik Microsoft 365 Defender ilkeleri oluşturmak için kimlik avı portalını kullanma

Microsoft 365 Defender portalında özel bir kimlik avı önleme ilkesi oluşturmak, hem kimlik avı önleme kuralını hem de her ikisi için aynı adı kullanarak ilişkili kimlik avı önleme ilkesi oluşturur.

1. Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler bölümünde **E-posta &** \> İşbirliği **İlkeleri'ne &** \> \> Kurallar Tehdit ilkeleri **Kimlik** avıyla **mücadele'ye** gidin. Doğrudan Kimlik avı önleme **sayfasına gitmek için** kullanın <https://security.microsoft.com/antiphishing>.

2. Kimlik avı **önleme sayfasında, Oluştur** simgesine ![tıklayın.](../../media/m365-cc-sc-create-icon.png) **Oluştur'a iki tablo da oluşturabilirsiniz**

3. İlke sihirbazı açılır. İlke **adı sayfasında** şu ayarları yapılandırabilirsiniz:
   - **Ad**: İlke için benzersiz, açıklayıcı bir ad girin.
   - **Açıklama**: İlke için isteğe bağlı bir açıklama girin.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

4. Görüntülenen **Kullanıcılar, gruplar ve etki** alanları sayfasında, ilkenin geçerli olduğu iç alıcıları (alıcı koşulları) bulun:
   - **Kullanıcılar**: Belirtilen posta kutuları, posta kullanıcıları veya kuruluşta posta kişileri.
   - **Gruplar**: Belirtilen dağıtım grupları, posta etkin güvenlik grupları veya Microsoft 365 Grupları.
   - **Etki** alanları: Belirtilen kabul edilen etki [alanlarındaki tüm](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) alıcılar.

   Uygun kutuya tıklayın, bir değer yazmaya başlayın ve sonuçlardan istediğiniz değeri seçin. Bu işlemi gereken sayıda yineler. Var olan bir değeri kaldırmak için kaldır'a tıklayın. ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) seçin.

   Kullanıcılar veya gruplar için çoğu tanımlayıcıyı (ad, görünen ad, diğer ad, e-posta adresi, hesap adı, vb.) kullanabilirsiniz, ancak sonuçlarda buna karşılık gelen görünen ad gösterilir. Kullanıcılar için, tüm kullanılabilir değerleri görmek için tek başına bir yıldız işareti (\*) girin.

   Aynı koşulda birden çok değer IÇIN VEYA mantığını kullanın (örneğin, _\<recipient1\>_ veya _\<recipient2\>_). Farklı koşullar, AND mantığını (örneğin, _\<recipient1\>_ ve ) kullanır _\<member of group 1\>_.

   - **Bu kullanıcıları, grupları** ve etki alanlarını dışla: İlkenin geçerli olduğu iç alıcılara özel durumlar (geçerli özel durumlar) eklemek için, bu seçeneği belirtin ve özel durumları yapılandırabilirsiniz. Ayarlar ve davranış, tam olarak koşullar gibi olur.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

5. Görüntülenen **Kimlik Avı &** koruma sayfasında, aşağıdaki ayarları yapılandırın:

   - **Kimlik avı e-posta eşiği**: Aşağıdaki değerlerden birini seçmek için kaydırıcıyı kullanın:
     - **1 - Standart** (Varsayılan değerdir.)
     - **2 - Saldırgan**
     - **3 - Daha agresif**
     - **4 - En agresif**

     Daha fazla bilgi için bkz[. Kimlik avıyla mücadele ilkeleri için Microsoft Defender'daki gelişmiş kimlik avı eşikleri Office 365](set-up-anti-phishing-policies.md#advanced-phishing-thresholds-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

   - **Kimliğe** Bürünme: Bu ayarlar, belirli gönderenleri tanımlayan ilkenin gelen iletilerin From adreslerinde (tek tek veya etki alanına göre) aramalarını belirleyen bir koşuldur. Daha fazla bilgi için bkz. Kimlik avı önleme ilkeleri için [Microsoft Defender'da kimliğe bürünme Office 365](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

     > [!NOTE]
     >
     > - Her kimlik avı önleme ilkesinde, en çok 350 korumalı kullanıcı (gönderen e-posta adresleri) belirtebilirsiniz. Aynı korumalı kullanıcıyı birden çok ilkede belirtemezseniz.
     > - Gönderen ve alıcı daha önce e-posta yoluyla iletişim kursa, kullanıcı kimliğine bürünme koruması işe yaramadı. Gönderen ve alıcı e-postayla hiçbir zaman iletişim kurmadı ise, ileti kimliğe bürünme girişimi olarak tanımlanır.

     - **Kullanıcıların korumalarını etkinleştirme**: Varsayılan değer kapalıdır (seçili değildir). Açmak için onay kutusunu seçin ve görüntülenen Yönet **(nn) gönderenleri** bağlantısına tıklayın.

       Görüntülenen **Kimliğe bürünme koruma için gönderenleri** yönet açılır iletisinde aşağıdaki adımları izleyin:

       - **İç gönderenler**: İç simge ![ekle'ye tıklayın.](../../media/m365-cc-sc-add-internal-icon.png) **İç'i seçin**. Görüntülenen **İç gönderenler ekle** açılır listesinde, kutuya tıklayın ve listeden bir iç kullanıcı seçin. Listeyi filtrelemek için, kullanıcı yazarak ve ardından sonuçlardan kullanıcı seçebilirsiniz. Çoğu tanımlayıcıyı (ad, görünen ad, diğer ad, e-posta adresi, hesap adı, vb.) kullanabilirsiniz, ancak sonuçlarda buna karşılık gelen görünen ad gösterilir.

         Bu adımı gereken sayıda yinelayın. Var olan bir değeri kaldırmak için kaldır'a tıklayın. ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) seçin.

         Bitirdikten sonra Ekle'ye **tıklayın.**

       - **Dış gönderenler**: Dış simge ekle'ye ![tıklayın.](../../media/m365-cc-sc-create-icon.png) **Dış öğesini seçin**. Görüntülenen **Dış** gönderenler ekle açılır kutusuna Ad ekle kutusuna bir görünen ad ve **Vaild** e-posta ekle kutusuna bir e-posta adresi girin ve Ekle'ye **tıklayın**.

         Bu adımı gereken sayıda yinelayın. Var olan bir değeri kaldırmak için kaldır'a tıklayın. ![Kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) seçin.

         Bitirdikten sonra Ekle'ye **tıklayın.**

       Kimliğe **bürünme için gönderenleri** yönet uç penceresinde, listeden bir veya birden çok girdi seçerek girdileri kaldırabilirsiniz. Girdileri Aramak simgesini kullanarak arayabilirsiniz ![.](../../media/m365-cc-sc-create-icon.png) **Arama** kutusu.

       En az bir girdi seçtikten sonra Seçili ![kullanıcıları kaldır simgesi.](../../media/m365-cc-sc-remove-selected-users-icon.png) **Seçili kullanıcıları** kaldır simgesi görüntülenir; bu simgeyi seçili girdileri kaldırmak için kullanabilirsiniz.

       Bitirdikten sonra Bitti'ye **tıklayın**.

     - **Korumak için etki alanlarını etkinleştirin**: Varsayılan değer kapalıdır (seçili değildir). Açmak için onay kutusunu seçin ve ardından aşağıdaki ayarlardan birini veya her ikisini de yapılandırarak görünür:
       - **Sahibim olan etki alanlarını** dahil edin: Bu ayarı açmak için onay kutusunu seçin. Sahibi olduğunuz etki alanlarını görüntülemek için Etki alanlarımı **görüntüle'ye tıklayın**.
       - **Özel etki alanlarını** ekle: Bu ayarı açmak için onay kutusunu seçin ve görüntülenen Yönet **(nn) özel etki alanları bağlantısını** tıklatın. Görüntülenen **Kimliğe bürünme koruma için özel etki alanlarını** yönet açılır sayfasında Etki alanı ekle simgesine ![tıklayın.](../../media/m365-cc-sc-create-icon.png) **Etki alanı ekleyin**.

         Görüntülenen **Özel etki alanları** ekle açılır sayfasında Etki Alanı kutusuna tıklayın, bir  değer girin ve sonra Enter tuşuna basın veya kutunun altında görüntülenen değeri seçin. Bu adımı gereken sayıda yinelayın. Var olan bir değeri kaldırmak için Kaldır simgesine ![tıklayın.](../../media/m365-cc-sc-remove-selection-icon.png) seçin.

         Bitirdikten sonra Etki alanı **ekle'ye tıklayın**

         > [!NOTE]
         > Tüm kimlik avı önleme ilkelerde en çok 50 etki alanınız olabilir.

       Kimliğe **bürünme için özel etki alanlarını** yönet uç penceresinde, listeden bir veya birden çok girdi seçerek girdileri kaldırabilirsiniz. Girdileri Aramak simgesini kullanarak arayabilirsiniz ![.](../../media/m365-cc-sc-create-icon.png) **Arama** kutusu.

       En az bir girdiyi seçdikten sonra, Etki alanlarını ![sil simgesi.](../../media/m365-cc-sc-delete-icon.png) **Seçili** girdileri kaldırmak için kullanabileceğiniz Sil simgesi görüntülenir.

   - **Güvenilen gönderenleri ve** etki alanlarını ekleme: Yönet **(nn)** güvenilen gönderenler ve etki alanları'nın üzerine tıklayarak ilke için kimliğe bürünme koruması özel durumları belirtin. Görüntülenen **Kimliğe bürünme koruma için özel** etki alanlarını yönetin açılır sayfasında aşağıdaki ayarları yapılandırın:
      - **Gönderenler**: Gönderen **sekmesinin seçili** olduğunu doğrulayın ve Gönderenleri ekle ![simgesine tıklayın](../../media/m365-cc-sc-create-icon.png). Görüntülenen **Güvenilir gönderenler ekle** açılır kutusunda, kutuya bir e-posta adresi girin ve Ekle'ye **tıklayın**. Bu adımı gereken sayıda yinelayın. Var olan bir girdiyi kaldırmak için, girdinin ![Sil](../../media/m365-cc-sc-close-icon.png) simgesine tıklayın.

        Bitirdikten sonra Ekle'ye **tıklayın**.

      - **Etki** Alanları: Etki Alanı **sekmesini seçin** ve Etki alanı ekle ![simgesine tıklayın](../../media/m365-cc-sc-create-icon.png).

        Görüntülenen **Güvenilen etki alanları** ekle açılır kutusunda Etki Alanı kutusuna tıklayın, bir  değer girin ve sonra Enter tuşuna basın veya kutunun altında görüntülenen değeri seçin. Bu adımı gereken sayıda yinelayın. Var olan bir değeri kaldırmak için Kaldır simgesine ![tıklayın.](../../media/m365-cc-sc-remove-selection-icon.png) seçin.

        Bitirdikten sonra Ekle'ye **tıklayın**.

     Kimliğe **bürünme için** özel etki alanlarını yönet açılır penceresinde, listeden bir veya birden çok girdi seçerek Gönderen  ve Etki Alanı sekmelerinden girdileri kaldırabilirsiniz. Girdileri Aramak simgesini kullanarak arayabilirsiniz ![.](../../media/m365-cc-sc-create-icon.png) **Arama** kutusu.

     En az bir girdi seçtikten sonra **, seçili** girdileri kaldırmak için kullanabileceğiniz Sil simgesi görüntülenir.

     Bitirdikten sonra Bitti'ye **tıklayın**.

     > [!NOTE]
     > En fazla gönderen ve etki alanı girdisi sayısı 1024'tir.

   - **Posta kutusu zekası** etkinleştirme: Varsayılan değer açık (seçili) ve bunu açık bırakmanızı öneririz. Kapatmak için onay kutusunu temizleyin.

     - **Zeka tabanlı kimliğe bürünme korumasını** etkinleştir: Bu ayar yalnızca Posta kutusu zekasını **etkinleştir seçeneği açık** (seçili) olduğunda kullanılabilir. Bu ayar, posta kutusu zekası kimliğine bürünme girişimleri olarak tanımlanan iletiler üzerinde eyleme geçülmelerini sağlar. Posta kutusu zekası bir sonraki sayfada **Kimliğine bürünülen bir** kullanıcı ayarı algılarsa, eylemi siz belirtirsiniz.

       Onay kutusunu seçerek bu ayarı açmanizi öneririz. Bu ayarı kapatmak için onay kutusunu temizleyin.

   - **E-posta**: Bu bölümde, akıllı ifadeyi  açmak veya kapatmak için Akıllı ifadeyi etkinleştir onay kutusunu kullanın. Varsayılan değer açık (seçili) ve bu değeri açık bırakmanız önerilir. Bir sonraki sayfada Eğer iletisi kimliği doğrulanmadı olarak algılanırsa, engellenen gönderenlerden gelen iletilere yapılan  eylemi belirtirsiniz.

     Akıllı ifadeyi kapatmak için onay kutusunu temizleyin.

     > [!NOTE]
     > MX kaydınız Ilkeler'e işaret Microsoft 365, bunun yerine Bağlayıcılar için Geliştirilmiş Filtreleme'yi etkinleştirirsiniz. Yönergeler için bkz. [Exchange Online'ta Bağlayıcılar için İyileştirilmiş Filtreleme](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

6. Görüntülenen **Eylemler** sayfasında aşağıdaki ayarları yapılandırabilirsiniz:

   - **İleti eylemleri**: Bu bölümdeki aşağıdaki eylemleri yapılandırma:
     - **İleti kimliğine bürünülen bir kullanıcı** olarak algılanırsa: Bu ayar yalnızca önceki sayfada Kullanıcıların korunmasını **etkinleştir'i** seçtiyseniz kullanılabilir. Gönderenin önceki sayfada belirttiğiniz korumalı kullanıcılardan biri olduğu iletiler için açılan listede aşağıdaki eylemlerden birini seçin:
       - **Hiçbir eylem uygulama**
       - **İletiyi diğer e-posta adreslerine yeniden yönlendirme**
       - **İletiyi alıcıların Gereksiz E-posta klasörlerine taşıma**
       - **İletiyi karantinaya** alın: Bu eylemi seçerseniz,  kullanıcı kimliğe bürünme koruması tarafından karantinaya alınan iletilere uygulanan karantina ilkesi seçenen bir Karantina ilkesi uygula kutusu görüntülenir. Karantina ilkeleri, kullanıcıların karantinaya alınmış iletiler için neler yapalır ve kullanıcılar karantina bildirimlerinin alınıp alınamayabileceklerini tanımlar. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md).

         Boş Karantina **ilkesi uygula değeri** , varsayılan karantina ilkesi 'nin alındığı anlamına gelir (kullanıcı kimliğe bürünme algılamaları için DefaultFullAccessPolicy). Daha sonra kimlik avı koruma ilkesi düzenlense veya ayarları görüntüseniz, varsayılan karantina ilkesi adı gösterilir.
  
       - **İletiyi teslim etmek ve Gizli satırına başka adresler ekleme**
       - **İleti teslim edilene kadar silin**

     - **İleti kimliğine bürünülen bir** etki alanı olarak algılanırsa: Bu ayar yalnızca, önceki sayfada Etki alanlarını korumak üzere **etkinleştir'i** seçtiyseniz kullanılabilir. Gönderenin e-posta adresinin önceki sayfada belirttiğiniz korumalı etki alanlarından birinin içinde olduğu iletiler için açılan listede aşağıdaki eylemlerden birini seçin:
       - **Hiçbir eylem uygulama**
       - **İletiyi diğer e-posta adreslerine yeniden yönlendirme**
       - **İletiyi alıcıların Gereksiz E-posta klasörlerine taşıma**
       - **İletiyi karantinaya** alın: Bu eylemi belirtirseniz,  etki alanı kimliğe bürünme koruması tarafından karantinaya alınan iletilere uygulanan karantina ilkesi seçenen bir Karantina ilkesi uygula kutusu görüntülenir.

         Boş karantina **ilkesi uygula değeri** , varsayılan karantina ilkesi kullanılacak anlamına gelir (etki alanı kimliğe bürünme algılamaları için DefaultFullAccessPolicy). Daha sonra kimlik avı koruma ilkesi düzenlense veya ayarları görüntüseniz, varsayılan karantina ilkesi adı gösterilir.

       - **İletiyi teslim etmek ve Gizli satırına başka adresler ekleme**
       - **İleti teslim edilene kadar silin**

     - **Posta kutusu zekası kimliğine bürünülen bir kullanıcı** algılarsa: Bu ayar yalnızca önceki sayfada Kimliğe bürünme koruması için zekayı **etkinleştir'i** seçtiyseniz kullanılabilir. Posta kutusu zekası tarafından kimliğe bürünme girişimleri olarak tanımlanan iletiler için açılan listede aşağıdaki eylemlerden birini seçin:
       - **Hiçbir eylem uygulama**
       - **İletiyi diğer e-posta adreslerine yeniden yönlendirme**
       - **İletiyi alıcıların Gereksiz E-posta klasörlerine taşıma**
       - **İletiyi karantinaya** alın: Bu eylemi seçerseniz,  posta kutusu zekası koruması tarafından karantinaya alınan iletilere uygulanan karantina ilkesi seçenen bir Karantina ilkesi uygula kutusu görüntülenir. Karantina ilkeleri, kullanıcıların karantinaya alınmış iletiler için neler yapalır ve kullanıcılar karantina bildirimlerinin alınıp alınamayabileceklerini tanımlar. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md).

         Boş Karantina **ilkesi uygula değeri** , varsayılan karantina ilkesi'nin kullanıldı olduğu anlamına gelir (posta kutusu zekası algılamaları için DefaultFullAccessPolicy). Daha sonra kimlik avı koruma ilkesi düzenlense veya ayarları görüntüseniz, varsayılan karantina ilkesi adı gösterilir.

       - **İletiyi teslim etmek ve Gizli satırına başka adresler ekleme**
       - **İleti teslim edilene kadar silin**

     - **İleti, ifade olarak algılanırsa**: Bu ayar yalnızca önceki sayfada Bilgi yok olarak etkinleştir'i **seçtiyseniz** kullanılabilir. Engellenen engellenen gönderenlerden gelen iletiler için açılan listede aşağıdaki eylemlerden birini seçin:
       - **İletiyi alıcıların Gereksiz E-posta klasörlerine taşıma**
       - **İletiyi karantinaya** alın: Bu eylemi seçerseniz,  akıllı durum korumasıyla karantinaya alınan iletilere uygulanan karantina ilkesi seçen bir Karantina ilkesi uygula kutusu görüntülenir. Karantina ilkeleri, kullanıcıların karantinaya alınmış iletiler için neler yapalır ve kullanıcılar karantina bildirimlerinin alınıp alınamayabileceklerini tanımlar. Daha fazla bilgi için bkz. [Karantina ilkeleri](quarantine-policies.md).

         Boş karantina **ilkesi değeri uygula** değeri, varsayılan karantina ilkesi'nin kullanıldı olduğu anlamına gelir (akıllı ifade algılamaları için DefaultFullAccessPolicy). Daha sonra kimlik avı koruma ilkesi düzenlense veya ayarları görüntüseniz, varsayılan karantina ilkesi adı gösterilir.

   - **Güvenlik ipuçları & göstergeleri**: Aşağıdaki ayarları yapılandırma:
     - **İlk kişi bilgilerini güvenlik ipucu**: Daha fazla bilgi için bkz. [İlk kişi güvenlik ipucu](set-up-anti-phishing-policies.md#first-contact-safety-tip).
     - **Kullanıcı kimliğe bürünme güvenlik ipucu**: Bu ayar yalnızca Önceki sayfada Kullanıcıların korunmasını **etkinleştir'i** seçtiyseniz kullanılabilir.
     - **Etki alanı kimliğe bürünme güvenlik ipucu**: Bu ayar yalnızca, etki alanlarını önceki sayfada korumak üzere **etkinleştir'i** seçtiyseniz kullanılabilir.
     - **Kullanıcı kimliğe bürünme alışılmadık karakterleri güvenlik ipucu** Bu ayar yalnızca Önceki sayfada Kullanıcıların korunmasını etkinleştir  veya Etki alanlarını koruma için **etkinleştir'i** seçtiyseniz kullanılabilir.
     - **Kimlik doğrulaması için kimliği doğrulanmamış gönderenler için (?)** göster: Bu ayar yalnızca kimliksız kimlik doğrulamayı önceki sayfada **etkinleştir'i seçtiyseniz** kullanılabilir. İleti SPF veya DKIM denetimlerini geçelamazsa ve ileti DMARC veya bileşik kimlik doğrulamasını geçese, Outlook'deki Gönderen kutusunda gönderenin  fotoğrafına bir soru işareti (?) [ekler](email-validation-and-authentication.md#composite-authentication).
     - **"Aracılığıyla" etiketini göster**: Bu ayar yalnızca önceki sayfada Akıllı e-postayı **etkinleştir'i** seçtiyseniz kullanılabilir. DKIM imzası veya MAIL **FROM** chris@contoso.com farklı ise, Gönderen adresine aracılığıyla etiketi (chris@contoso.com fabrikam.com aracılığıyla gönder) ekler. Varsayılan değer açıktır (seçili). Kapatmak için onay kutusunu temizleyin.

     Ayarı açmak için onay kutusunu seçin. Kapatmak için onay kutusunu temizleyin.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

7. Görüntülenen **Gözden Geçir** sayfasında ayarlarınızı gözden geçirebilirsiniz. Bölümün içindeki **ayarları değiştirmek** için her bölümde Düzenle'yi seçebilirsiniz. Geri'ye **tıklar** veya sihirbazda belirli bir sayfayı seçersiniz.

   Bitirdikten sonra Gönder'e **tıklayın**.

8. Görüntülenen onay sayfasında Bitti'ye **tıklayın**.

## <a name="use-the-microsoft-365-defender-portal-to-view-anti-phishing-policies"></a>Kimlik Microsoft 365 Defender ilkelerini görüntülemek için kimlik avı portalını kullanma

1. Microsoft 365 Defender portalında, İlkeler bölümünde  E **-****&** \> İşbirliği **İlkeleri &** \> \> Kurallar Tehdit İlkeleri Kimlik **avıyla mücadele'ye** gidin.

2. Kimlik **avı önleme sayfasında** , kimlik avı önleme ilkeleri listesinde aşağıdaki özellikler görüntülenir:

   - **Ad**
   - **Durum**
   - **Öncelik**
   - **Son değiştirme**

3. Adına tıklayarak bir ilkeyi seçince, ilke ayarları bir çıkışta görüntülenir.

## <a name="use-the-microsoft-365-defender-portal-to-modify-anti-phishing-policies"></a>Kimlik Microsoft 365 Defender ilkelerini değiştirmek için Kimlik avı portalını kullanma

1. Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler bölümünde **E-posta &** \> İşbirliği **İlkeleri'ne &** \> \> Kurallar Tehdit ilkeleri **Kimlik** avıyla **mücadele'ye** gidin. Doğrudan Kimlik avı önleme **sayfasına gitmek için** kullanın <https://security.microsoft.com/antiphishing>.

2. Kimlik **avı koruması sayfasında** , adı tıklatarak listeden bir ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır sayfasında, bölümün **içindeki ayarları değiştirmek** için Her bölümde düzenle'yi seçin. Ayarlar hakkında daha fazla bilgi için, bu makalenin önceki [Microsoft 365 Defender](#use-the-microsoft-365-defender-portal-to-create-anti-phishing-policies) kimlik avı ilkeleri oluşturmak için Kimlik avı portalını kullanma bölümüne bakın.

   Varsayılan kimlik avı önleme ilkesi için, **Kullanıcılar,** gruplar ve etki alanları bölümü kullanılamaz (ilke herkes için geçerlidir) ve ilkeyi yeniden adlandırılamaz.

Bir ilkeyi etkinleştirmek veya devre dışı bırakmak ya da ilke öncelik sırası ayarlamak için aşağıdaki bölümlere bakın.

### <a name="enable-or-disable-custom-anti-phishing-policies"></a>Özel kimlik avı önleme ilkelerini etkinleştirme veya devre dışı bırakma

Varsayılan kimlik avı önleme ilkesi devre dışı bırakılamaz.

1. Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler bölümünde **E-posta &** \> İşbirliği **İlkeleri'ne &** \> \> Kurallar Tehdit ilkeleri **Kimlik** avıyla **mücadele'ye** gidin. Doğrudan Kimlik avı önleme **sayfasına gitmek için** kullanın <https://security.microsoft.com/antiphishing>.

2. Kimlik **avı önleme sayfasında** , adı tıklatarak listeden bir özel ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır iletisinin en üstünde, aşağıdaki değerlerden birini görüyorsunuz:
   - **İlke** kapalı: İlkeyi açmak için Aç simgesine ![tıklayın.](../../media/m365-cc-sc-turn-on-off-icon.png) **'i açma.**
   - **İlke**: İlkeyi kapatmak için Kapat simgesine ![tıklayın.](../../media/m365-cc-sc-turn-on-off-icon.png) **Kapatma**.

4. Görüntülenen onay iletişim kutusunda Aç veya **Kapat'a tıklayın**.

5. **İlke ayrıntıları** uçarak çıkışta Kapat'a tıklayın.

Ana ilke sayfasına dönüp, **ilkenin** Durum değeri **Açık veya Kapalı** **olur**.

### <a name="set-the-priority-of-custom-anti-phishing-policies"></a>Özel kimlik avı önleme ilkelerinin önceliğini ayarlama

Varsayılan olarak, kimlik avı önleme ilkelerine, oluşturulduklarına dayalı olarak öncelik verilir (daha yeni ilkeler, eski ilkelerden daha düşük önceliklidir). Daha düşük öncelik numarası, ilke için daha yüksek bir öncelik olduğunu (0 en yüksek) gösterir ve ilkeler öncelik sırasına göre işlenir (daha yüksek öncelikli ilkeler, daha düşük öncelikli ilkeler önce işlenir). İki ilke aynı önceliğe sahip olabilir ve ilk ilke uygulandıktan sonra ilke işleme durur.

Bir ilkenin önceliğini değiştirmek için, ilke özelliklerinde Önceliğe  artır'a veya Önceliği azalt'a tıklarsınız (Microsoft 365 Defender portalında Öncelik  numarasını doğrudan değiştiremezsiniz). Bir ilkenin önceliğini değiştirmek, ancak birden çok ilkeniz varsa anlamlıdır.

 **Notlar**:

- Microsoft 365 Defender portalında, kimlik avı önleme ilkesi önceliğini, oluşturduklardan sonra değiştirebilirsiniz. PowerShell'de, kimlik avı önleme kuralı 2007'de 00.000'de (mevcut kuralların önceliğini etkileyebilecek) varsayılan önceliği geçersiz kılabilirsiniz.
- Kimlik avı önleme ilkeleri, görüntülenme sırasına göre işlenir (ilk ilkenin Öncelik değeri 0'dır). Varsayılan kimlik avı önleme ilkesi En düşük **öncelik değerine** sahiptir ve bunu değiştiremezsiniz.

1. Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler bölümünde **E-posta &** \> İşbirliği **İlkeleri'ne &** \> \> Kurallar Tehdit ilkeleri **Kimlik** avıyla **mücadele'ye** gidin. Doğrudan Kimlik avı önleme **sayfasına gitmek için** kullanın <https://security.microsoft.com/antiphishing>.

2. Kimlik **avı önleme sayfasında** , adı tıklatarak listeden bir özel ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır çizgisinin en üstünde, geçerli öncelik değerine ve özel ilke  sayısına göre  Önceliği artır veya Önceliği azalt'a bakın:
   - Öncelik değeri 0 **olan** ilke **yalnızca** Önceliğe azalt **seçeneğine** sahiptir.
   - En düşük Öncelik **değerine (** örneğin, 3) sahip **ilke** yalnızca Öncelik **artır seçeneğine** sahiptir.
   - Üç veya daha fazla ilkeniz varsa, en yüksek ve en düşük öncelikli değerler arasındaki ilkeler hem Önceliğe **artır** hem de Öncelik azalt **seçeneklerine** sahiptir.

   Önceliğe ![artır simgesine tıklayın.](../../media/m365-cc-sc-increase-icon.png) **Öncelik değerini** değiştirmek için ![Önceliği artır **veya**](../../media/m365-cc-sc-decrease-icon.png) Önceliği azalt simgesi Önceliği **azalt simgesi**.

4. Bitirdikten sonra, ilke ayrıntıları **uç giriş** bilgisinde Kapat'a tıklayın.

## <a name="use-the-microsoft-365-defender-portal-to-remove-custom-anti-phishing-policies"></a>Özel kimlik Microsoft 365 Defender ilkelerini kaldırmak için Kimlik avı portalını kullanma

Özel bir kimlik Microsoft 365 Defender ilkeyi kaldırmak için Kimlik avı önleme portalını kullanırken, kimlik avı önleme kuralı ve buna karşılık gelen kimlik avı önleme ilkesi de silinir. Varsayılan kimlik avı önleme ilkesi kaldıramayr.

1. Microsoft 365 Defender portalında<https://security.microsoft.com>, İlkeler bölümünde **E-posta &** \> İşbirliği **İlkeleri'ne &** \> \> Kurallar Tehdit ilkeleri **Kimlik** avıyla **mücadele'ye** gidin. Doğrudan Kimlik avı önleme **sayfasına gitmek için** kullanın <https://security.microsoft.com/antiphishing>.

2. Kimlik **avı önleme sayfasında** , ilkenin adına tıklayarak listeden bir özel ilke seçin.

3. Görüntülenen ilke ayrıntıları açılır öğesinin üst kısmında Diğer eylemler simgesine ![tıklayın.](../../media/m365-cc-sc-more-actions-icon.png) **Diğer eylemler** \> ![İlkeyi sil simgesi](../../media/m365-cc-sc-delete-icon.png) **İlkeyi sil'i seçin**.

4. Görüntülenen onay iletişim kutusunda Evet'e **tıklayın**.

## <a name="use-exchange-online-powershell-to-configure-anti-phishing-policies"></a>Kimlik Exchange Online ilkelerini yapılandırmak için PowerShell'i kullanma

Daha önce açıklandığı gibi, istenmeyen posta önleme ilkesi bir kimlik avı koruma ilkesi ve kimlik avı önleme kuralıdan oluşur.

Bir Exchange Online PowerShell'de, kimlik avı koruma ilkeleriyle kimlik avı koruma kuralları arasındaki fark görünür. Kimlik avı önleme **\*ilkelerini, -AntiPhishPolicy** cmdlet'lerini ve kimlik avı önleme kurallarını **da -AntiPhishRule cmdlet'lerini\*** kullanarak yönetirsiniz.

- PowerShell'de önce kimlik avı önleme ilkesi oluşturun, sonra da kuralın geçerli olduğu ilkeyi tanımlayan kimlik avı önleme kuralını oluşturun.
- PowerShell'de, kimlik avı önleme ilkesi ve kimlik avı koruma kuralı ayarlarını ayrı ayrı değiştirirsiniz.
- PowerShell'den bir kimlik avı koruma ilkesi kaldırılmışsa, buna karşılık gelen kimlik avı önleme kuralı otomatik olarak kaldırılamaz ve bunun tersi de geçerlidir.

### <a name="use-powershell-to-create-anti-phishing-policies"></a>PowerShell kullanarak kimlik avı önleme ilkeleri oluşturma

PowerShell'de kimlik avına karşı koruma ilkesi oluşturmak iki adımlı bir işlemdir:

1. Kimlik avı önleme ilkesi oluşturun.
2. Kuralın geçerli olduğu kimlik avı önleme ilkesine yönelik kimlik avı önleme kuralını oluşturun.

 **Notlar**:

- Yeni bir kimlik avı önleme kuralı oluşturabilir ve bu kurala var olan, ilişkilendirilmemiş bir kimlik avı koruma ilkesi atfingingniz olabilir. Kimlik avı koruma kuralı birden çok kimlik avı önleme ilkesiyle ilişkilendirilz.
- İlkeyi oluşturmadan önce, PowerShell'de Microsoft 365 Defender portalında olmayan yeni kimlik avı önleme ilkelerde aşağıdaki ayarları yapılandırabilirsiniz:
  - Yeni ilkeyi devre dışı olarak _oluşturun (_ `$false` **New-AntiPhishRule cmdlet'inde** etkin).
  - Yeni-AntiPhishRule cmdlet'inde oluşturma sırasında **ilkenin önceliğini** _ayarlayın (__\<Number\>_ Öncelik).
- PowerShell'de yeni bir kimlik avı koruma ilkesi, siz bu ilkeyi bir kimlik avı koruma kuralına atayana kadar Microsoft 365 Defender portalında görünmez.

#### <a name="step-1-use-powershell-to-create-an-anti-phish-policy"></a>1. Adım: Kimlik avı önleme ilkesi oluşturmak için PowerShell kullanma

Kimlik avı önleme ilkesi oluşturmak için şu söz dizimlerini kullanın:

```PowerShell
New-AntiPhishPolicy -Name "<PolicyName>" [-AdminDisplayName "<Comments>"] <Additional Settings>
```

Bu örnek, aşağıdaki ayarlarla Araştırma Karantinası adlı bir kimlik avı koruma ilkesi oluşturur:

- İlke etkindir ( _Enabled_ parametresi bizim değil ve varsayılan değer: `$true`).
- Açıklama şöyledir: Araştırma bölümü ilkesi.
- Kullanıcı adı kullanma algılamaları için varsayılan eylemi Karantina olarak değiştirir ve karantinaya alınmış iletiler için varsayılan [](quarantine-policies.md) karantina ilkesi kullanır (_SpoofQuarantineTag parametresi_ kullanacağız).
- Tüm kabul edilen etki alanları için kuruluş etki alanları korumasını ve etki alanları için hedefli etki alanlarını korumayı fabrikam.com.
- Etki alanı kimliğe bürünme algılamaları için eylem olarak Karantina'yı belirtir ve karantinaya alınan iletiler için varsayılan karantina ilkesi kullanır (_TargetedDomainQuarantineTag parametresi_ kullanacağız).[](quarantine-policies.md)
- Kimliğe bürünme kuralına karşı korumak mfujito@fabrikam.com Mai Maito'nun (mfujito@fabrikam.com) olduğunu belirtir.
- Kullanıcı kimliğe bürünme algılamaları için eylem olarak Karantina'yı belirtir ve karantinaya [](quarantine-policies.md) alınan iletiler için varsayılan karantina ilkesi kullanır (_TargetedUserQuarantineTag_ parametresini kullanacağız).
- Posta kutusu zekasını etkinleştirir (_EnableMailboxIntelligence_), iletilerde posta kutusu zekası korumasının eyleme dönüşe izin verir (_EnableMailboxIntelligenceProtection_), algılanan iletiler için eylem olarak Karantina'yı [](quarantine-policies.md) belirtir ve karantinaya alınan iletiler için varsayılan karantina ilkesi kullanır (_MailboxIntelligenceQuarantineTag_ parametresini kullanacağız).
- Tüm güvenlik ipuçlarını sağlar.

```powershell
New-AntiPhishPolicy -Name "Monitor Policy" -AdminDisplayName "Research department policy" -AuthenticationFailAction Quarantine -EnableOrganizationDomainsProtection $true -EnableTargetedDomainsProtection $true -TargetedDomainsToProtect fabrikam.com -TargetedDomainProtectionAction Quarantine -EnableTargetedUserProtection $true -TargetedUsersToProtect "Mai Fujito;mfujito@fabrikam.com" -TargetedUserProtectionAction Quarantine -EnableMailboxIntelligence $true -EnableMailboxIntelligenceProtection $true -MailboxIntelligenceProtectionAction Quarantine -EnableSimilarUsersSafetyTips $true -EnableSimilarDomainsSafetyTips $true -EnableUnusualCharactersSafetyTips $true
```

Ayrıntılı söz dizimi ve parametre bilgileri için [bkz. New-AntiPhishPolicy](/powershell/module/exchange/New-AntiPhishPolicy).

> [!NOTE]
> Kimlik avı önleme ilkesinde [kullanmak üzere](quarantine-policies.md) karantina ilkelerini belirtmeye yönelik ayrıntılı yönergeler için bkz. [PowerShell kullanarak](quarantine-policies.md#anti-phishing-policies) kimlik avı koruma ilkesinde karantina ilkesi belirtme.

#### <a name="step-2-use-powershell-to-create-an-anti-phish-rule"></a>2. Adım: PowerShell kullanarak kimlik avına karşı koruma kuralı oluşturma

Kimlik avı önleme kuralı oluşturmak için şu söz dizimlerini kullanın:

```PowerShell
New-AntiPhishRule -Name "<RuleName>" -AntiPhishPolicy "<PolicyName>" <Recipient filters> [<Recipient filter exceptions>] [-Comments "<OptionalComments>"]
```

Bu örnek, aşağıdaki koşulların yer alan Araştırma Bölümü adlı bir kimlik avına karşı koruma kuralı oluşturur:

- Kural, Araştırma Karantinası adlı kimlik avı koruma ilkesiyle ilişkilendirildi.
- Kural, Araştırma Bölümü adlı grubun üyeleri için geçerlidir.
- Öncelik parametresi kullanılmay _olduğundan,_ varsayılan öncelik kullanılır.

```powershell
New-AntiPhishRule -Name "Research Department" -AntiPhishPolicy "Research Quarantine" -SentToMemberOf "Research Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için [bkz. New-AntiPhishRule](/powershell/module/exchange/New-AntiPhishRule).

### <a name="use-powershell-to-view-anti-phish-policies"></a>Kimlik avı koruma ilkelerini görüntülemek için PowerShell kullanma

Var olan kimlik avı koruma ilkelerini görüntülemek için aşağıdaki söz dizimlerini kullanın:

```PowerShell
Get-AntiPhishPolicy [-Identity "<PolicyIdentity>"] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Bu örnek, belirtilen özelliklerle birlikte tüm kimlik avı koruma ilkelerinin özet bir listesini döndürür.

```PowerShell
Get-AntiPhishPolicy | Format-Table Name,IsDefault
```

Bu örnek, Yöneticiler adlı kimlik avı önleme ilkesi için tüm özellik değerlerini döndürür.

```PowerShell
Get-AntiPhishPolicy -Identity "Executives"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-AntiPhishPolicy](/powershell/module/exchange/Get-AntiPhishPolicy).

### <a name="use-powershell-to-view-anti-phish-rules"></a>Kimlik avı koruma kurallarını görüntülemek için PowerShell kullanma

Var olan kimlik avı koruma kurallarını görüntülemek için aşağıdaki söz dizimlerini kullanın:

```PowerShell
Get-AntiPhishRule [-Identity "<RuleIdentity>"] [-State <Enabled | Disabled] [| <Format-Table | Format-List> <Property1,Property2,...>]
```

Bu örnek, belirtilen özelliklerle birlikte tüm kimlik avı kurallarının özet bir listesini döndürür.

```PowerShell
Get-AntiPhishRule | Format-Table Name,Priority,State
```

Etkinleştirilmiş veya devre dışı bırakılmış kurallara göre listeyi filtrelemek için aşağıdaki komutları çalıştırın:

```PowerShell
Get-AntiPhishRule -State Disabled | Format-Table Name,Priority
```

```PowerShell
Get-AntiPhishRule -State Enabled | Format-Table Name,Priority
```

Bu örnekte, Contoso Yöneticiler adlı kimlik avı koruma kuralı için tüm özellik değerleri döndürür.

```PowerShell
Get-AntiPhishRule -Identity "Contoso Executives"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [Get-AntiPhishRule](/powershell/module/exchange/Get-AntiPhishrule).

### <a name="use-powershell-to-modify-anti-phish-policies"></a>Kimlik avı koruma ilkelerini değiştirmek için PowerShell kullanma

Aşağıdaki öğeler dışında, PowerShell'de kimlik avı önleme ilkesinde değişiklik yapmak için 1. Adım [: PowerShell](#step-1-use-powershell-to-create-an-anti-phish-policy) kullanarak kimlik avı koruması ilkesi bölümü oluşturma konusunda açıklandığı gibi aynı ayarlar kullanılabilir.

- Belirtilen ilkeyi varsayılan ilkeye dönüştüren _MakeDefault_ anahtarı (herkese uygulanır **, her zaman** En düşük öncelikli ve bunu silemezsiniz) yalnızca PowerShell'de kimlik avı önleme ilkesinde değişiklik yapmak için kullanılabilir.

- Kimlik avı koruma ilkesi yeniden adlandırılamaz ( **Set-AntiPhishPolicy** cmdlet'in _Name_ parametresi yoktur). Bu portalda kimlik avı önleme ilkesine Microsoft 365 Defender, yalnızca kimlik avı koruma kuralını yeniden _adlandırıyor olursunuz_.

Kimlik avı önleme ilkesi değiştirmek için şu söz dizimlerini kullanın:

```PowerShell
Set-AntiPhishPolicy -Identity "<PolicyName>" <Settings>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [AntiPhishPolicy Ayarlama](/powershell/module/exchange/Set-AntiPhishPolicy).

> [!NOTE]
> Kimlik avı önleme ilkesinde [kullanmak üzere](quarantine-policies.md) karantina ilkelerini belirtmeye yönelik ayrıntılı yönergeler için bkz. [PowerShell kullanarak](quarantine-policies.md#anti-phishing-policies) kimlik avı koruma ilkesinde karantina ilkesi belirtme.

### <a name="use-powershell-to-modify-anti-phish-rules"></a>Kimlik avı koruma kurallarını değiştirmek için PowerShell kullanma

PowerShell'de kimlik avı koruma kuralını değiştirirken kullanılabilen tek ayar, devre dışı bırakılmış bir kural oluşturmanıza  olanak sağlayan Enabled parametresidir. Kimlik avı koruma kurallarını etkinleştirmek veya devre dışı bırakmak için sonraki bölüme bakın.

Aksi takdirde, PowerShell'de kimlik avı koruma kuralını değiştirerek ek ayarlar kullanılamaz. 2. Adım: Bu makalenin önceki kısımlarında kimlik avına karşı koruma kuralı oluşturmak için [PowerShell](#step-2-use-powershell-to-create-an-anti-phish-rule) kullanarak bir kural 2. adımda açıklandığı gibi aynı ayarları kullanabilirsiniz.

Kimlik avı önleme kuralını değiştirmek için şu söz dizimi kullanın:

```PowerShell
Set-AntiPhishRule -Identity "<RuleName>" <Settings>
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [AntiPhishRule Ayarlama](/powershell/module/exchange/set-antiphishrule).

### <a name="use-powershell-to-enable-or-disable-anti-phish-rules"></a>Kimlik avı koruma kurallarını etkinleştirmek veya devre dışı bırakmak için PowerShell kullanma

PowerShell'de kimlik avı koruma kuralının etkinleştirilmesi veya devre dışı bırakılması, tüm kimlik avı koruma ilkesi (kimlik avı koruma kuralı ve atanmış kimlik avı önleme ilkesi) etkinleştir veya devre dışı bırak. Varsayılan kimlik avı önleme ilkesi (her zaman tüm alıcılara uygulanır) etkinleştir veya devre dışı bırakasınız.

PowerShell'de kimlik avı önleme kuralını etkinleştirmek veya devre dışı bırakmak için şu söz dizimlerini kullanın:

```PowerShell
<Enable-AntiPhishRule | Disable-AntiPhishRule> -Identity "<RuleName>"
```

Bu örnekte, Pazarlama Departmanı adlı kimlik avı önleme kuralı devre dışı bırak).

```PowerShell
Disable-AntiPhishRule -Identity "Marketing Department"
```

Bu örnek aynı kuralı sağlar.

```PowerShell
Enable-AntiPhishRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz. [AntiPhishRule'yi etkinleştirme ve](/powershell/module/exchange/enable-antiphishrule) [Disable-AntiPhishRule](/powershell/module/exchange/disable-antiphishrule).

### <a name="use-powershell-to-set-the-priority-of-anti-phish-rules"></a>Kimlik avı önleme kurallarının önceliğini ayarlamak için PowerShell kullanma

Bir kuralda ayar şubat 2010 en yüksek öncelik değeri 0'dır. Ayary değerinin en düşük değeri, kuralların sayısına bağlıdır. Örneğin, beş kuralız varsa, 0 ile 4 arasında öncelik değerlerini kullanabilirsiniz. Var olan bir kuralın önceliğini değiştirmenin diğer kurallar üzerinde basamaklı bir etkisi olabilir. Örneğin, beş özel kuralınız varsa (0'dan 4'e kadar olan) ve kuralın önceliğini 2 olarak değiştirirsiniz, 2. önceliğe sahip var olan kural önceliğe 3 olarak değiştirilir ve 3. önceliğe sahip kural ise 4. öncelik olarak değiştirilir.

PowerShell'de kimlik avı önleme kuralının önceliğini ayarlamak için aşağıdaki söz dizimi kullanın:

```PowerShell
Set-AntiPhishRule -Identity "<RuleName>" -Priority <Number>
```

Bu örnek, Pazarlama Bölümü adlı kuralın önceliğini 2 olarak ayarlar. Önceliği 2'ye eşit veya daha az olan mevcut kuralların hepsi 1 azaltılmıştır (öncelik sayıları 1 artırılmıştır).

```PowerShell
Set-AntiPhishRule -Identity "Marketing Department" -Priority 2
```

**Notlar**:

- Yeni kuralı irken önceliğini ayarlamak için, bunun yerine **New-AntiPhishRule** cmdlet'inin Öncelik parametresini kullanın.

- Varsayılan kimlik avı önleme ilkesine karşılık gelen kimlik avı önleme kuralı yoktur ve her zaman En Düşük değiştirilmez öncelik **değerine sahiptir**.

### <a name="use-powershell-to-remove-anti-phish-policies"></a>Kimlik avı önleme ilkelerini kaldırmak için PowerShell kullanma

Kimlik avı önleme ilkesi kaldırmak için PowerShell'i kullanırseniz, buna karşılık gelen kimlik avı önleme kuralı kaldırılamaz.

PowerShell'de kimlik avı önleme ilkesi kaldırmak için şu söz dizimlerini kullanın:

```PowerShell
Remove-AntiPhishPolicy -Identity "<PolicyName>"
```

Bu örnekte, Pazarlama Departmanı adlı kimlik avı önleme ilkesi kaldır).

```PowerShell
Remove-AntiPhishPolicy -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. Remove-AntiPhishPolicy](/powershell/module/exchange/Remove-AntiPhishPolicy).

### <a name="use-powershell-to-remove-anti-phish-rules"></a>Kimlik avı koruma kurallarını kaldırmak için PowerShell kullanma

Kimlik avı koruma kuralını kaldırmak için PowerShell'i kullanırseniz, buna karşılık gelen kimlik avı önleme ilkesi kaldırılamaz.

PowerShell'de kimlik avı önleme kuralını kaldırmak için şu söz dizimlerini kullanın:

```PowerShell
Remove-AntiPhishRule -Identity "<PolicyName>"
```

Bu örnekte, Pazarlama Departmanı adlı kimlik avı önleme kuralı kaldır).

```PowerShell
Remove-AntiPhishRule -Identity "Marketing Department"
```

Ayrıntılı söz dizimi ve parametre bilgileri için bkz [. AntiPhishRule'i kaldırma](/powershell/module/exchange/Remove-AntiPhishRule).

## <a name="how-do-you-know-these-procedures-worked"></a>Bu yordamların çalıştığını nasıl biliyorsunuz?

Kimlik avı önleme ilkelerini kimlik avı için Defender'da başarıyla yapılandırmış Office 365 için, aşağıdaki adımlardan birini uygulayın:

- Microsoft 365 Defender portalında kimlik avıyla mücadele sayfasında, ilkelerin listesini, Durum değerlerini ve **Öncelik değerlerini doğrulayın**.  <https://security.microsoft.com/antiphishing> Daha fazla ayrıntı görüntülemek için, adı tıklatarak ve beliren açılır listede ayrıntıları görüntüerek listeden ilkeyi seçin.

- PowerShell Exchange Online, ilke \<Name\> veya kuralın adıyla değiştirin ve aşağıdaki komutu çalıştırarak ayarları doğrulayın:

  ```PowerShell
  Get-AntiPhishPolicy -Identity "<Name>"
  ```

  ```PowerShell
  Get-AntiPhishRule -Identity "<Name>"
  ```
