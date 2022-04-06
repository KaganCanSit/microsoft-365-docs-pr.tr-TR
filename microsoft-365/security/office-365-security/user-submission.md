---
title: Kullanıcı ileti ayarlarını bildirdi
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
description: Yöneticiler, kullanıcılar tarafından bildirilen istenmeyen postayı ve kimlik avı e-postasını toplamak üzere bir posta kutusunun nasıl yapılandırıldığında bilgi edinebilirsiniz.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 9a38943b492e6bdae151a7906d1c8146a649949d
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64634041"
---
# <a name="user-reported-message-settings"></a>Kullanıcı ileti ayarlarını bildirdi

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Yeni Microsoft 365 kutusu olan Exchange Online, kullanıcıların kötü amaçlı olup olmadığını belirten iletileri almak için bir posta kutusu belirtebilirsiniz. Kullanıcılar çeşitli raporlama seçeneklerini kullanarak iletileri bildirseler, iletilerin kesişimini yapmak (yalnızca özel posta kutusuna göndermek) veya iletilerin kopyalarını almak (özel posta kutusuna ve Microsoft'a göndermek) için bu posta kutusunu kullanabilirsiniz. Bu özellik aşağıdaki ileti raporlama seçenekleriyle çalışır:

- [Rapor İletisi eklentisinde](enable-the-report-message-add-in.md)
- [Rapor Kimlik Avı eklentisi](enable-the-report-phish-add-in.md)
- [Üçüncü taraf raporlama araçları](#third-party-reporting-tools)

Kullanıcı tarafından bildirilen iletilerin doğrudan Microsoft yerine özel bir posta kutusuna teslimi, yöneticilerinizin iletileri Yönetici gönderimini kullanarak seçmeli ve el ile Microsoft'a [bildirmelerini sağlar](admin-submission.md). Bu ayarlar daha önce Kullanıcı gönderimleri ilkesi olarak biliniyor vardı.

  > [!NOTE]
  > Raporlama bu farklı bir Web üzerinde Outlook devre dışı [bırakıldı](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web) ise, kullanıcının burada bildirilen iletilerin etkinleştirilmesi bu ayarı geçersiz kılar ve kullanıcıların iletileri aynı Web üzerinde Outlook etkinleştirir.

## <a name="custom-mailbox-prerequisites"></a>Özel posta kutusu önkoşulları

Kullanıcı iletileri özel posta kutunuza gidecek şekilde gerekli önkoşulları yapılandırmak için aşağıdaki makaleleri kullanın:

- İstenmeyen posta güven düzeyini ayarlamak üzere bir Exchange posta akışı kuralı oluşturarak özel posta kutusunda istenmeyen posta filtrelemeyi atlayabilirsiniz. [SCL'nin istenmeyen](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl#use-the-eac-to-create-a-mail-flow-rule-that-sets-the-scl-of-a-message) posta filtresini atla olarak ayarlamak üzere iletinin SCL'sini ayarlayan bir posta akış kuralı oluşturmak için EAC **kullanma'ya bakın**.

- [Kötü amaçlı yazılım için](configure-your-spam-filter-policies.md#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) sıfır saatlik otomatik temizleme (ZAP) özelliğinin kapalı olduğu özel posta kutusunu içeren bir kötü amaçlı yazılımdan koruma ilkesi **oluşturun (Koruma** **ayarları bölümü** \> Kötü amaçlı yazılım için sıfır saatlik otomatik temizlemeyi etkinleştirme seçeneği seçili değildir).

- [İstenmeyen](configure-your-spam-filter-policies.md#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) posta için ZAP ve kimlik avı için ZAP'ın kapalı olduğu özel posta kutusunu içeren bir istenmeyen posta önleme ilkesi **oluşturun (** \> Sıfır saatlik otomatik temizleme bölümü Etkin **sıfır saatlik otomatik temizleme (ZAP)** seçili değil).

Filtrelemeniz Office 365 için Microsoft Defender, aşağıdaki ayarları da yapılandırarak, gelişmiş filtremizin iletileri bildirimini kullanıcıları etkilemesini şunları s gerekir:

- [Bağlantı tarama Kasa kapalı](set-up-safe-links-policies.md) olduğu özel posta kutusunu içeren bir Kasa Bağlantıları ilkesi oluşturun (İletilerde kötü amaçlı olabilecek bilinmeyen **URL'ler için eylemi** \> **kapalı seçin**).

- [Ekler tarama Kasa kapalı](set-up-safe-attachments-policies.md) olduğu özel posta kutusunu içeren bir Kasa Ekler ilkesi **oluşturun (Ekler** bilinmeyen kötü amaçlı yazılıma yanıt Kasa **Kapalı).**\>

Posta kutunuzda tüm geçerli önkoşulların karşılandığından emin olduktan sonra, kullanıcı gönderimleri posta kutusunu yapılandırmak için bu makaledeki yordamları kullanabilirsiniz.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açın<https://security.microsoft.com>. Doğrudan Kullanıcı gönderimleri **sayfasına gitmek için** , kullanın <https://security.microsoft.com/reportsubmission>.

- Kullanıcı gönderimlerinin yapılandırmasını değiştirmek için, aşağıdaki rol gruplarından birinin üyesi olmak gerekir:

  - **Portalda** yer **alan İzinler'deki** [Kuruluş Microsoft 365 Defender.](permissions-microsoft-365-security-center.md)

- Exchange Online PowerShell'e erişiminiz vardır. Kullanmaya çalışıyorsanız hesabın Exchange Online PowerShell erişimi yoksa, gönderiler posta kutusunu belirtirken aşağıdakine benzer bir hata alırsınız:

  > Etki alanınıza bir e-posta adresi belirtin

  PowerShell'de erişimi etkinleştirme veya devre dışı Exchange Online daha fazla bilgi için aşağıdaki konulara bakın:

  - [Exchange Online PowerShell'e erişimi etkinleştirme veya devre dışı bırakma](/powershell/exchange/disable-access-to-exchange-online-powershell)
  - [Web'de İstemci Erişimi Exchange Online](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules)

## <a name="use-the-microsoft-365-defender-portal-to-configure-the-user-submissions-mailbox"></a>Kullanıcı gönderimleri Microsoft 365 Defender yapılandırmak için Posta Kutusu portalını kullanma

1. Aşağıdaki Microsoft 365 Defender portalında İlkeler'e <https://security.microsoft.com>**& kuralları Tehdit** \>  \> ilkeleri **Kullanıcı diğer** bölümünde ileti **ayarlarını bildirdi**. Doğrudan Kullanıcı gönderimleri **sayfasına gitmek için** , kullanın <https://security.microsoft.com/reportsubmission>.

2. Kullanıcı **gönderimleri sayfasında** gördüğünüz, Microsoft Rapor İletisi düğmesi ayarının **Kapalı Outlook** Açık olup **olmadığıyla** **belirlenir**:

   - **Microsoft Outlook** \>  ![](../../media/scc-toggle-on.png)rapor iletisi düğmesi Geçiş açık durumda.: Rapor İletisi eklentinizi, Web üzerinde Outlook'te Rapor Kimlik Avı eklentinizi veya yerleşik raporlama eklentinizi kullanıyorsanız bu seçeneği belirtin ve sonra aşağıdaki ayarları yapılandırın:
     - **Bildirilen iletileri gönder**: Aşağıdaki seçeneklerden birini belirleyin:
       - **Microsoft**: Kullanıcı gönderimleri posta kutusu kullanılmaz (bildirilen tüm iletiler Microsoft'a gider).
       - **Microsoft ve kuruluşum posta kutusu**: Görüntülenen kutuya, var olan bir posta kutusunun e-posta Exchange Online girin. Dağıtım gruplarına izin verilmez. Kullanıcı gönderimleri çözümleme için hem Microsoft'a, hem de yöneticinizin veya güvenlik işlemleri ekibinin çözümlemek üzere özel posta kutusuna gider.
       - **Kuruluşum'un posta** kutusu: Görüntülenen kutuya, var olan posta kutusunun e-posta Exchange Online girin. Dağıtım gruplarına izin verilmez. İletinin önce yalnızca yöneticiye veya güvenlik işlemleri ekibine analiz için gitmelerini istiyorsanız bu seçeneği kullanın. İletiler, yönetici tarafından iletilene kadar Microsoft'a gider.

          > [!IMPORTANT]
          > ABD Kamu kuruluşları (GCC, GCC High ve DoD) yalnızca **Kuruluşum'un posta kutusunu yapılandırabilirsiniz**. Diğer iki seçenek devre dışı bırakılır.
          >
          > Kuruluşlar yalnızca özel posta kutusuna gönderecek şekilde yapılandırılmışsa, bildirilen iletiler yeniden gönderme için gönderilmez ve Kullanıcı tarafından bildirilen ileti portalın sonuçları her zaman boş olur.

       Bildirilen iletileri gönder için seçtiğiniz **değerden bağımsız olarak**, aşağıdaki ayarlar kullanılabilir:

       - **Kullanıcıların iletilerini Microsoft'a rapor etmek isterken tercihlerine izin verme**
       - **Kullanıcıların da seç olduğu raporlama seçeneklerini belirleyin** bölümü: Aşağıdaki seçenekler arasından en az birini seçin:
         - **İletiyi göndermeden önce bana sor**
         - **İletiyi her zaman bildir**
         - **hiçbir zaman iletiyi bildirme**

          > [!CAUTION]
          > [Web üzerinde Outlook'da Web üzerinde Outlook](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web) posta kutusu ilkelerini kullanarak gereksiz e-posta raporlamayı devre dışı bırakıldıysanız, ancak önceki ayarlardan herhangi birini Microsoft'a iletileri bildirecek şekilde yapılandırdınız, kullanıcılar aynı zamanda Microsoft'a gelen iletileri de Web üzerinde Outlook  Rapor İletisi eklentilerini veya Rapor Kimlik Avı eklentilerini kullanarak.

     Son kullanıcıların **karantina Outlook hatalı** ![](../../media/scc-toggle-on.png) pozitif iletileri bildirmesine izin vermek için, Microsoft İletiyi Bildir düğmesi ayarını Açık bırakın.

     - **Kullanıcı raporlama deneyimi bölümü**
       - **Raporlamadan** önce sekmesi: Başlık  ve İleti  gövdesi kutularına, Rapor İletisi eklentisini veya Rapor Kimlik Avı eklentisini kullanarak bir iletiyi bildirmeden önce kullanıcıların göreceği açıklayıcı metni girin. Gönderi türünü (gereksiz değil, kimlik avı vb.) eklemek için %type % değişkenlerini kullanabilirsiniz.
       - **Raporlama sekmesinden** sonra: Başlık  ve Onay  ileti kutularına, Rapor İletisi eklentisini veya Rapor Kimlik Avı eklentisini kullanarak bir iletiyi raporladikten sonra kullanıcıların göreceği açıklayıcı metni girin. Gönderi türünü eklemek için %type% değişkenlerini kullanabilirsiniz.
       - **Yalnızca kullanıcı kimlik avını raporlarken görüntüle**: İletiyi yalnızca bir e-posta kimlik avı olarak bildir geldiğinde görüntülemek için bu seçeneği işaretleyin. Gösterilmezse, denetlenen iletiler herhangi bir rapor için gösterilir.

       Sayfada gösterildiği gibi, bildirilen iletileri Microsoft'a gönderen bir seçenek belirtinse aşağıdaki metin de bildirime eklenir:

          > E-postanız, çözümleme için Microsoft'a olduğu gibi gönderilir. Bazı e-postalar kişisel veya hassas bilgiler içerebilir.

   - **Microsoft Outlook** \>  ![](../../media/scc-toggle-off.png)İletiyi Bildir düğmesi Kapalı Geçiş kapalı.: Web üzerinde Outlook'te Rapor İletisi eklenti, Rapor Kimlik Avı eklentileri veya yerleşik raporlama yerine üçüncü taraf raporlama araçlarını kullanıyorsanız, bu seçeneği belirtin ve sonra aşağıdaki ayarları yapılandırın:
     - Kullanıcı **tarafından bildirilen gönderileri almak için Bu özel posta kutusunu kullan'ı seçin**. Görüntülenen kutuya, var olan ve e-posta al Exchange Online posta kutusunun e-posta adresini girin.

   - **İletiyi karantinaya alın** düğmesi: Son kullanıcıların iletileri karantinadan bildirmesine izin vermelerini sağlamak için bu özelliği etkinleştirin.

   Bitirdikten sonra Onayla'ya **tıklayın**. Bu değerleri temizlemek için Geri Yükle'ye **tıklayın**

## <a name="third-party-reporting-tools"></a>Üçüncü taraf raporlama araçları

Bildirilen iletileri özel posta kutusuna göndermek için üçüncü taraf ileti raporlama araçlarını yapılandırabilirsiniz. Bunu yapmak için **Microsoft** Rapor Outlook düğmesi ayarını Kapalı olarak ve Kuruluşum **posta** kutusunu kendi Office 365  posta kutusuna ayarlarsınız.

Tek gereksinim, özgün iletinin bir . olarak dahil olmasıdır. EML veya . Özel posta kutusuna gönderilen iletide MSG eki (sıkıştırılmış değil) (yalnızca özgün iletiyi özel posta kutusuna iletmeyin).

İleti biçimlendirme gereksinimleri sonraki bölümde açıklanmıştır. Biçimlendirme isteğe bağlıdır, ancak bu biçimlendirme öngörülen biçime uymazsa, raporlar her zaman kimlik avı olarak gönderilen raporlardır.

## <a name="message-submission-format"></a>İleti gönderme biçimi

Özgün ekli iletileri doğru şekilde tanımlamak için, özel posta kutusuna gönderilen iletiler için belirli bir biçimlendirme gerekir. İletilerde bu biçim yoksa, özgün ekli iletiler her zaman kimlik avı gönderileri olarak tanımlanır.

Özgün ekli iletilerin bildirilen nedenini belirtmek için, özel posta kutusuna gönderilen iletilerin (eki değiştirme) Konu'da şu ön eklerden biri ile başlaması gerekir (Zarf Başlığı):

- 1| veya Gereksiz:
- 2| veya Gereksiz değil:
- 3| veya Kimlik Avı:

Örneğin:

`3|This part is ignored by the system` <br>
`Not Junk:This part of the subject is ignored as well`

- Her iki ileti de Konu'ya bağlı olarak Gereksiz Değil olarak bildiriliyor.
- Gerisi yoksayılır.


Bu biçimden sonra gelen iletiler Gönderiler portalında düzgün görüntülenmez.
