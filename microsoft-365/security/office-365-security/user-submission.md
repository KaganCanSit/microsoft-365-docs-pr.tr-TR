---
title: Kullanıcı tarafından bildirilen ileti ayarları
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Yöneticiler, kullanıcılar tarafından bildirilen istenmeyen posta ve kimlik avı e-postalarını toplamak için posta kutusunu yapılandırmayı öğrenebilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a4a46225b911c3272baa66772a0cf9ab63f1a1da
ms.sourcegitcommit: bfbe2574f487ced69e711b48ce140120bd99181b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2022
ms.locfileid: "66607597"
---
# <a name="user-reported-message-settings"></a>Kullanıcı tarafından bildirilen ileti ayarları

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Exchange Online posta kutularına sahip Microsoft 365 kuruluşlarında, kullanıcıların kötü amaçlı olarak bildirdiği veya kötü amaçlı olmadığı iletileri almak için bir posta kutusu belirtebilirsiniz. Kullanıcılar çeşitli raporlama seçeneklerini kullanarak iletileri raporladığında, iletileri kesmek (yalnızca özel posta kutusuna göndermek) veya iletilerin kopyalarını almak (özel posta kutusuna ve Microsoft'a göndermek) için bu posta kutusunu kullanabilirsiniz. Bu özellik aşağıdaki ileti raporlama seçenekleriyle çalışır:

- [Rapor İletisi eklentisi](enable-the-report-message-add-in.md)
- [Rapor Kimlik Avı eklentisi](enable-the-report-phish-add-in.md)
- [Üçüncü taraf raporlama araçları](#third-party-reporting-tools)

Kullanıcı tarafından bildirilen iletileri doğrudan Microsoft yerine özel bir posta kutusuna teslim etmek, yöneticilerinizin [Yönetici gönderimi](admin-submission.md) kullanarak iletileri seçerek ve el ile Microsoft'a bildirmesine olanak tanır. Bu ayarlar daha önce Kullanıcı gönderimleri ilkesi olarak biliniyordu.

  > [!NOTE]
  > [raporlama Web üzerinde Outlook devre dışı bırakıldıysa](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web), burada kullanıcı tarafından bildirilen iletilerin etkinleştirilmesi bu ayarı geçersiz kılar ve kullanıcıların iletileri Web üzerinde Outlook yeniden raporlamasına olanak tanır.

## <a name="custom-mailbox-prerequisites"></a>Özel posta kutusu önkoşulları

Kullanıcı tarafından bildirilen iletilerin özel posta kutunuza gitmesi için gerekli önkoşulları yapılandırmak için aşağıdaki makaleleri kullanın:

- [Özel posta kutusunu SecOps posta kutusu olarak tanımlayın](configure-advanced-delivery.md#use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy).

- Özel posta kutusu için [kötü amaçlı yazılımdan koruma ilkesi oluşturma](configure-your-spam-filter-policies.md#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies)
  - Kötü amaçlı yazılım için sıfır saatlik otomatik temizleme (ZAP) kapalıdır (**Koruma ayarları** > **Kötü amaçlı yazılım için sıfır saatlik otomatik temizlemeyi etkinleştir** seçeneği seçilmez).
  - Ortak ek filtresi seçeneği kapalıdır (**Koruma ayarları** bölümü > **Ortak ekler filtresini etkinleştir** seçili değildir).

Office 365 için Microsoft Defender varsa, gelişmiş filtrelememizin bildirilen iletileri etkilememesi için aşağıdaki ayarları da yapılandırmanız gerekir:

- Özel posta kutusunun [önceden ayarlanmış güvenlik ilkelerinin](preset-security-policies.md#use-the-microsoft-365-defender-portal-to-modify-the-assignments-of-standard-and-strict-preset-security-policies) bir parçası olmadığından emin olun

- Güvenli Bağlantılar taramasının kapalı olduğu özel posta kutusu için [bir Güvenli Bağlantılar ilkesi oluşturun](set-up-safe-links-policies.md) (**İletilerde bilinmeyen kötü amaçlı olabilecek URL'ler için eylemi seçin** > **Kapalı**).

- Dinamik Teslim de dahil olmak üzere Güvenli Ekler taramasının kapalı olduğu özel posta kutusu için [güvenli ekler ilkesi oluşturun](set-up-safe-attachments-policies.md) (**Güvenli Ekler bilinmeyen kötü amaçlı yazılım yanıtı** bölümü > **Kapalı**).

Posta kutunuzu tüm geçerli önkoşulları karşıladığını doğruladıktan sonra, kullanıcı gönderimleri posta kutusunu yapılandırmak için bu makaledeki yordamları kullanabilirsiniz.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını adresinde <https://security.microsoft.com>açarsınız. Doğrudan **Kullanıcı gönderimleri** sayfasına gitmek için kullanın <https://security.microsoft.com/userSubmissionsReportMessage>.

- Kullanıcı gönderimleri yapılandırmasını değiştirmek için aşağıdaki rol gruplarından birinin üyesi olmanız gerekir:

  - [Microsoft 365 Defender portalındaki İzinler'de](permissions-microsoft-365-security-center.md) **Kuruluş Yönetimi** veya **Güvenlik Yöneticisi**.

- Exchange Online PowerShell'e erişmeniz gerekir. Kullanmaya çalıştığınız hesabın Exchange Online PowerShell'e erişimi yoksa, gönderimler posta kutusunu belirtirken şuna benzer bir hata alırsınız:

  > Etki alanınızda bir e-posta adresi belirtme

  Exchange Online PowerShell'e erişimi etkinleştirme veya devre dışı bırakma hakkında daha fazla bilgi için aşağıdaki konulara bakın:

  - [Exchange Online PowerShell'e erişimi etkinleştirme veya devre dışı bırakma](/powershell/exchange/disable-access-to-exchange-online-powershell)
  - [Exchange Online'da İstemci Erişim Kuralları](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules)

## <a name="use-the-microsoft-365-defender-portal-to-configure-the-user-submissions-mailbox"></a>Kullanıcı gönderimleri posta kutusunu yapılandırmak için Microsoft 365 Defender portalını kullanma

1. konumundaki Microsoft 365 Defender portalında<https://security.microsoft.com>**, İlkeler & kuralları** > **Tehdit ilkeleri** >  **Diğerleri** bölümünde **Kullanıcı tarafından bildirilen ileti ayarları'na** gidin. Doğrudan **Kullanıcı gönderimleri** sayfasına gitmek için kullanın <https://security.microsoft.com/userSubmissionsReportMessage>.

2. **Kullanıcı gönderimleri** sayfasında, gördükleriniz **Microsoft Outlook Rapor İletisi düğme** ayarının **Kapalı** mı yoksa **Açık** mı olduğuna göre belirlenir:

   - **Microsoft Outlook Rapor İletisi düğmesi** >  **-Inı** ![ Açık.](../../media/scc-toggle-on.png): Web üzerinde Outlook Rapor İletisi eklentisini, Rapor Kimlik Avı eklentisini veya yerleşik raporlamayı kullanıyorsanız bu seçeneği belirleyin ve ardından aşağıdaki ayarları yapılandırın:
     - **Bildirilen iletileri gönder**: Aşağıdaki seçeneklerden birini belirleyin:
       - **Microsoft**: Kullanıcı gönderileri posta kutusu kullanılmaz (bildirilen tüm iletiler Microsoft'a gider).
       - **Microsoft ve kuruluşumun posta kutusu**: Görüntülenen kutuya mevcut bir Exchange Online posta kutusunun e-posta adresini girin. Dağıtım gruplarına izin verilmez. Kullanıcı gönderimleri analiz için hem Microsoft'a hem de yöneticinizin veya güvenlik operasyonları ekibinizin analiz edeceği özel posta kutusuna gider.
       - **Kuruluşumun posta kutusu**: Görüntülenen kutuya var olan bir Exchange Online posta kutusunun e-posta adresini girin. Dağıtım gruplarına izin verilmez. İletinin önce analiz için yalnızca bir yöneticiye veya güvenlik operasyonları ekibine gitmesini istiyorsanız bu seçeneği kullanın. Yönetici kendi iletmediği sürece iletiler Microsoft'a gitmez.

          > [!IMPORTANT]
          > ABD Kamu kuruluşları (GCC, GCC High ve DoD) yalnızca **Kuruluşumun posta kutusunu** yapılandırabilir. Diğer iki seçenek devre dışı bırakılır.
          >
          > Kuruluşlar, kullanıcı tarafından bildirilen iletileri yalnızca özel posta kutusuna gönderecek şekilde yapılandırılmışsa, bildirilen iletiler **Kullanıcı tarafından bildirilen iletiler'de** görünür ancak sonuçları her zaman boş olur (çünkü bunlar yeniden taramazlardı).
          >
          > [Saldırı simülasyonu eğitimini](attack-simulation-training-get-started.md) veya üçüncü taraf bir ürünü kullanarak kimlik avı simülasyonları yapıyorsanız[, bu posta kutusunu SecOps posta kutusu olarak yapılandırmanız](configure-advanced-delivery.md) gerekir. Bunu yapmazsanız, raporlama iletileri kimlik avı simülasyonu ürününde eğitim atamalarını tetikleyebilir.

       **Bildirilen iletileri gönderme** için seçtiğiniz değerden bağımsız olarak aşağıdaki ayarlar kullanılabilir:

       - **Kullanıcıların, iletilerini Microsoft'a bildirmek isteyip istemediklerini seçmesine izin verme**
       - **Kullanıcılar tarafından kullanılabilen raporlama seçeneklerini belirleme** bölümü: Aşağıdaki seçenekler arasından en az birini seçin:
         - **İletiyi göndermeden önce sor**
         - **İletiyi her zaman bildir**
         - **İletiyi hiçbir zaman bildirmeyin**

          > [!CAUTION]
          > Web üzerinde Outlook posta kutusu ilkelerini kullanarak [Web üzerinde Outlook'de gereksiz e-posta raporlamayı devre dışı bırakmış](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web) ancak iletileri Microsoft'a bildirmek için önceki ayarlardan herhangi birini yapılandırdıysanız, kullanıcılar iletileri Web üzerinde Outlook  Rapor İletisi eklentisini veya Rapor Kimlik Avı eklentisini kullanarak.

     Son kullanıcıların karantina portalından hatalı pozitif iletiler bildirmesine izin vermek için **Microsoft Outlook Rapor İletisi düğme** ayarını ![](../../media/scc-toggle-on.png) **Açık** bırakın.

     - **Kullanıcı raporlama deneyimi bölümü**
       - **Raporlamadan önce** sekmesi: **Başlık** ve **İleti gövdesi** kutularına, rapor iletisi eklentisini veya Rapor Kimlik Avı eklentisini kullanarak bir iletiyi bildirmeden önce kullanıcıların gördüğü açıklayıcı metni girin. Gönderme türünü (gereksiz, gereksiz değil, kimlik avı vb.) dahil etmek için %type% değişkenini kullanabilirsiniz.
       - **Raporlamadan sonra** sekmesi: **Başlık** ve **Onay ileti** kutularına, kullanıcıların Rapor İletisi eklentisini veya Rapor Kimlik Avı eklentisini kullanarak bir iletiyi bildirdikten sonra görecekleri açıklayıcı metni girin. Gönderim türünü eklemek için %type% değişkenini kullanabilirsiniz.
       - **Yalnızca kullanıcı kimlik avı bildirdiğinde görüntüle**: İletiyi yalnızca bir e-posta kimlik avı olarak bildirildiğinde görüntülemek istiyorsanız bu seçeneği işaretleyin. Aksi takdirde, herhangi bir rapor türü için denetlenen iletiler gösterilir.

       Sayfada gösterildiği gibi, bildirilen iletileri Microsoft'a gönderen bir seçenek seçerseniz bildirime aşağıdaki metin de eklenir:

          > E-postanız analiz için Olduğu gibi Microsoft'a gönderilir. Bazı e-postalar kişisel veya hassas bilgiler içerebilir.

   - **Microsoft Outlook Rapor İletisi düğmesi** >  **Kapalı** ![ Kapalı konuma getirin.](../../media/scc-toggle-off.png): Rapor İletisi eklentisi, Rapor Kimlik Avı eklentisi veya Web üzerinde Outlook yerleşik raporlama yerine üçüncü taraf raporlama araçlarını kullanıyorsanız bu seçeneği belirleyin ve ardından aşağıdaki ayarları yapılandırın:
     - **Kullanıcı tarafından bildirilen gönderimleri almak için Bu özel posta kutusunu kullan'ı** seçin. Görüntülenen kutuya, e-posta alabilen mevcut bir Exchange Online posta kutusunun e-posta adresini girin.

   - **Rapor iletisini karantinaya al düğmesi**: Son kullanıcıların karantinadan gelen iletileri bildirmesine izin vermek istiyorsanız bu özelliği etkinleştirin.

3. İşiniz bittiğinde **Onayla'ya** tıklayın. Bu değerleri temizlemek için **Geri Yükle'ye** tıklayın.

## <a name="third-party-reporting-tools"></a>Üçüncü taraf raporlama araçları

Bildirilen iletileri özel posta kutusuna göndermek için üçüncü taraf ileti raporlama araçlarını yapılandırabilirsiniz. Bunu yapmak için **Microsoft Outlook Rapor İletisi düğmesi** ayarını **Kapalı** ve **Kuruluşum'un posta kutusunu** istediğiniz Office 365 posta kutusuna ayarlarsınız.

Tek gereksinim, özgün iletinin olarak eklenmesidir. EML veya . Özel posta kutusuna gönderilen iletideki MSG eki (sıkıştırılmaz) (özgün iletiyi özel posta kutusuna iletmeyin).

 > [!NOTE]
 > E-postada birden çok e-posta eki varsa gönderim atılır. Yalnızca bir e-posta eki olan e-postaları destekliyoruz.

İleti biçimlendirme gereksinimleri sonraki bölümde açıklanmıştır. Biçimlendirme isteğe bağlıdır, ancak belirtilen biçime uymuyorsa raporlar her zaman kimlik avı olarak gönderilir.

## <a name="message-submission-format"></a>İleti gönderme biçimi

Özgün ekli iletileri doğru şekilde tanımlamak için özel posta kutusuna gönderilen iletiler belirli bir biçimlendirme gerektirir. İletiler bu biçimi kullanmıyorsa, özgün eklenen iletiler her zaman kimlik avı gönderimleri olarak tanımlanır.

Özgün ekli iletilerin bildirilen nedenini belirtmek istiyorsanız, özel posta kutusuna gönderilen iletilerin (eki değiştirmeyin) Konu (Zarf Başlığı) içindeki aşağıdaki ön eklerden biriyle başlaması gerekir:

- 1| veya Gereksiz:
- 2| veya Gereksiz değil:
- 3| veya Kimlik Avı:

Örneğin:

`3|This part is ignored by the system` <br>
`Not Junk:This part of the subject is ignored as well`

Bu biçimi izlemeyen iletiler Gönderimler portalında düzgün görüntülenmez.
