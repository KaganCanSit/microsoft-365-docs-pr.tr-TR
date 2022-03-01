---
title: Güvenliği Tehlikeye E-posta Hesabını Yanıtla
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.collection:
- o365_security_incident_response
- M365-security-compliance
- m365solution-smb
ms.custom:
- TopSMBIssues
- seo-marvel-apr2020
ms.localizationpriority: high
search.appverid:
- MET150
description: Güvenliği tehlikeye atılmış bir e-posta hesabını tanımayı ve yanıtlamayı öğrenmek için E-posta'da Microsoft 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bdce44bc54c71d03e8064fa10187c06237d38b5b
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63033362"
---
# <a name="responding-to-a-compromised-email-account"></a>Güvenliği Tehlikeye E-posta Hesabını Yanıtla

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

**Özet** E-posta hesaplarında güvenliği tehlikeye atılmış bir e-posta hesabını tanımayı ve Microsoft 365.

## <a name="what-is-a-compromised-email-account-in-microsoft-365"></a>Bir hesapta Güvenliği Ihlal Edilmiş E-posta Microsoft 365?

Posta kutularına Microsoft 365 verilere ve diğer hizmetlere erişim, kullanıcı adı ve parola veya PIN gibi kimlik bilgileri kullanılarak denetlenır. Hedeflenen kullanıcı dışında bir kişi bu kimlik bilgilerini çaldığı zaman çalınmış kimlik bilgilerinin güvenliği ihlal edilmiş olarak kabul edilir. Bu kişi ile saldırgan, özgün kullanıcı olarak oturum açmalı ve resmi olmayan eylemler gerçekleştirebiliyor.

Saldırgan, çalınmış kimlik bilgilerini kullanarak kullanıcının posta kutusuna, Microsoft 365 kutusundan, SharePoint veya dosyalara OneDrive. En sık görülen eylemlerden biri, alıcının hem kuruluş içindeki hem de dışındaki alıcılara özgün kullanıcı olarak e-posta göndermesidir. Saldırgan verileri dış alıcılara e-postayla yanıtlasa, buna veri sızıntıları denir.

## <a name="symptoms-of-a-compromised-microsoft-email-account"></a>Güvenliği Tehlikeye Bir Microsoft E-posta Hesabının Belirtileri

Kullanıcılar en son gelen posta kutularında olağan dışı etkinlikleri fark Microsoft 365 bildirebilirsiniz. Yaygın belirtilerden bazıları:

- Eksik veya silinen e-postalar gibi şüpheli etkinlikler.
- Diğer kullanıcılar güvenliği tehlikeye atılmış hesaptan e-postaları, ilgili e-postayı gönderenin **Gönderilmiş Öğeler** klasöründe olmadan alabilirsiniz.
- Hedeflenen kullanıcı veya yönetici tarafından oluşturulmaan gelen kutusu kurallarının iletişim durumu. Bu kurallar, bilinmeyen adreslere otomatik olarak e-posta iletebilirsiniz ya da bunları **Notlar, Gereksiz** E-posta veya **RSS Abonelikleri klasörlerine** taşıyabilirsiniz.
- Genel Adres Listesi'ne kullanıcının görünen adı değiştirilebilir.
- Kullanıcının posta kutusunun e-posta göndermesi engellendi.
- Microsoft Outlook veya Web üzerinde Outlook'daki (eski adı Outlook Web App) Gönderilmiş veya Silinmiş Öğeler klasörleri, "Londra'da takılıp kalmış durumdayım, para gönder" gibi sık karşılaşılan ele elemiş hesap iletilerini içerir.
- Ad, telefon numarası veya posta kodu gibi sıra dışı profil değişiklikleri güncelleştirildi.
- Birden çok parola değişikliği gibi olağan dışı kimlik bilgileri değişiklikleri gereklidir.
- Posta iletme yakın zamanda eklenmiştir.
- Kısa süre önce sahte banka imzası veya imzalı bir imza gibi sıra dışı bir imza eklenmiştir.

Bir kullanıcı yukarıdaki belirtilerden herhangi birini raporlarsa, daha fazla araştırma gerçekleştirin. Güvenlik Microsoft 365 Defender Azure portalı, güvenliği ihlal edilmiş olabilir diye şüpheli bir kullanıcı hesabının etkinliğini araştırmanıza yardımcı olan araçlar sunar.

- **Microsoft 365 Defender portalında** birleşik denetim günlükleri: Şüpheli etkinliğin geçerli tarihe kadar olan tarih aralığına yönelik sonuçları filtreleerek, şüpheli hesabın tüm etkinliklerini gözden geçirebilirsiniz. Arama sırasında etkinliklere filtre uygulama. Daha fazla bilgi için [bkz. Uyumluluk merkezinde denetim günlüğünde arama.](../../compliance/search-the-audit-log-in-security-and-compliance.md)

- **Azure AD Portalında Azure AD Oturum Açma günlükleri ve diğer risk** raporları: Bu sütunlarda yer alan değerleri incele:
  - IP adresini gözden geçirme
  - oturum açma konumları
  - oturum açma saatleri
  - oturum açma başarılı veya başarısız

## <a name="how-to-secure-and-restore-email-function-to-a-suspected-compromised-microsoft-365-account-and-mailbox"></a>E-posta işlevinin güvenliğini sağlama ve hesap ve posta kutusunda güvenliği ihlal edilmiş Microsoft 365 olarak geri yükleme

> [!VIDEO https://videoplayercdn.osi.office.net/hub/?csid=ux-cms-en-us-msoffice&uuid=RE2jvOb&AutoPlayVideo=false]

Hesabınıza yeniden erişim kazansanız bile, saldırgan, saldırganın hesabın kontrolünü sürdürmesi için arka kapı girdileri eklemış olabilir.

Ele geçiricinin hesabını kontrol altına devam etmey olduğundan emin olmak için, hesabınıza yeniden erişim kazanmak için aşağıdaki adımların hepsini o kadar kısa sürede gerçekleştirin. Bu adımlar, korsanın hesabınıza ekli olduğu tüm arka kapı girdilerini kaldırmanıza yardımcı olur. Bu adımları tamamladikten sonra, bilgisayarınızın güvenliğin ihlal edilmiş olduğundan emin olmak için bir virüs taraması çalıştırmanızı öneririz.

### <a name="step-1-reset-the-users-password"></a>1. Adım Kullanıcının parolasını sıfırlama

Bir kişi için iş [parolasını sıfırlama'daki yordamları izleyin](../../admin/add-users/reset-passwords.md#reset-my-admin-password).

> [!IMPORTANT]
>
> - Yeni parolayı hedeflenen kullanıcıya e-posta yoluyla göndermeyin çünkü saldırgan bu noktada posta kutusuna erişmeye devam ediyor.
>
> - Parolanın güçlü olduğundan ve büyük ve küçük harf (en az bir sayı ve en az bir özel karakter) içerdiğindan emin olun.
>
> - Son beş paroladan herhangi birini yeniden kullanmayın. Parola geçmişi gereksinimi daha yeni bir parolayı yeniden kullanmanıza izinse de, saldırganin tahmin  boyunca tahmin edemey başka bir şey seçmeniz gerekir.
>
> - Şirket içi kimliğiniz şirket içi kimlik Microsoft 365, parolanızı şirket içinde değiştirmeli ve sonra da yöneticinizi bu güvenliğinin tehlikeye at olduğunu bildirmiş olasınız.
>
> - Uygulama parolalarını güncelleştirin. Kullanıcı hesabı parolası sıfırlanıyorsa uygulama parolaları otomatik olarak iptal edilmez. Kullanıcı, var olan uygulama parolalarını silebilir ve yeni parolalar oluşturmalı. Yönergeler için Ek [güvenlik doğrulama sayfasında uygulama parolaları oluşturma ve silme sayfasına bakın](/azure/active-directory/user-help/multi-factor-authentication-end-user-app-passwords#create-and-delete-app-passwords-from-the-additional-security-verification-page).
>
> - Özellikle yönetici ayrıcalıklarına sahip hesaplarda güvenliğin tehlikeye atması için Multi-Factor Authentication'i (MFA) etkinleştirmenizi kesinlikle öneririz. MFA hakkında daha fazla bilgi edinmek için, Çok [faktörlü kimlik doğrulamasını ayarlama'ya gidin](../../admin/security-and-compliance/set-up-multi-factor-authentication.md).

### <a name="step-2-remove-suspicious-email-forwarding-addresses"></a>2. Adım Şüpheli e-posta iletme adreslerini kaldırma

1. Aşağıdaki Microsoft 365 yönetim merkezi , Kullanıcılar <https://admin.microsoft.com>Etkin **Kullanıcılar'a** \> **gidin**. Doğrudan Etkin kullanıcılar sayfasına **gitmek için** , kullanın <https://admin.microsoft.com/Adminportal/Home#/users>.

2. Etkin **kullanıcılar sayfasında** söz konusu kullanıcı hesabını bulun ve onay kutusunu seçmeden kullanıcı (satır) öğesini seçin.

3. Görüntülenen ayrıntılar açılır iletisinde **Posta sekmesini seçin** .

4. E-posta iletme bölümündeki **değer Uygulandı ise** , **E-posta** **iletmeyi yönet'e tıklayın**. Görüntülenen **E-posta iletmeyi yönet** açılır iletisinde, Bu posta kutusuna gönderilen tüm e-postaları ilet seçeneğinin ardından Değişiklikleri **kaydet'e tıklayın**.

### <a name="step-3-disable-any-suspicious-inbox-rules"></a>3. Adım Şüpheli gelen kutusu kurallarını devre dışı bırakma

1. E-posta kutusunu kullanarak kullanıcının posta kutusunda Web üzerinde Outlook.

2. Dişli simgesine ve ardından Posta'ya **tıklayın**.

3. Gelen **kutusu ve süpürme kuralları'na** tıklayın ve kuralları gözden geçirin.

4. Şüpheli kuralları devre dışı bırakma veya silme.

### <a name="step-4-unblock-the-user-from-sending-mail"></a>4. Adım Kullanıcının posta gönderme engellemesini kaldırma

Güvenliği ihlal edilmiş olan posta kutusu istenmeyen posta göndermek için resmi olarak kullanılmışsa, büyük olasılıkla posta kutusunun posta göndermesi engellenmiştir.

Posta kutusunun posta gönderme engelini kaldırmak için, İstenmeyen posta gönderen bir kullanıcının Kısıtlanmış Kullanıcılar [portalından kaldırılması ile ilgili yordamları izleyin](removing-user-from-restricted-users-portal-after-spam.md).

### <a name="step-5-optional-block-the-user-account-from-signing-in"></a>5. Adım İsteğe bağlı: Kullanıcı hesabının oturum açmasını engelleme

> [!IMPORTANT]
> Güvenliği ihlal edilmiş olduğu şüphe edilen hesabın, erişimi yeniden etkinleştirmenin güvenli olduğunu bulana kadar oturum açmasını engelleyebilirsiniz.

1. Aşağıdaki Microsoft 365 yönetim merkezi , Kullanıcılar <https://admin.microsoft.com>Etkin **Kullanıcılar'a** \> **gidin**. Doğrudan Etkin kullanıcılar sayfasına **gitmek için** , kullanın <https://admin.microsoft.com/Adminportal/Home#/users>.

2. Etkin kullanıcılar **sayfasında,** kullanıcı hesabını bulup seçin, ![](../../media/ITPro-EAC-MoreOptionsIcon.png)Diğer simgesine tıklayın ve sonra oturum açma durumunu **düzenle'yi seçin**.

3. Görüntülenen **Oturum açma engelleme bölmesinde** Bu kullanıcının oturum açmasını **engelle'yi seçin ve** ardından Değişiklikleri kaydet'e **tıklayın**.

4. Aşağıdaki Exchange Yönetim Merkezi'nde (EAC) <https://admin.exchange.microsoft.com>Alıcılar Posta **Kutuları'ne** \> **gidin**. Doğrudan Posta Kutuları **sayfasına gitmek için** kullanın <https://admin.exchange.microsoft.com/#/mailboxes>.

5. Posta **Kutuları sayfasında** , kullanıcı bulun ve seçin. Açılan posta kutusu ayrıntıları açılır kutusunda aşağıdaki adımları izleyin:
   - **E-posta uygulamaları bölümünde** E-posta **uygulamalarının ayarlarını yönet'i seçin**. Görüntülenen **E-posta uygulamalarının** ayarlarını yönet açılır sayfasında, iki durumlu düğmeyi sağ Devre dışı bırak'a değiştirerek kullanılabilir tüm ayarları ![engelin.](../../media/scc-toggle-on.png):
     - **Web üzerinde Outlook**
     - **Outlook masaüstü (MAPI)**
     - **Exchange Web Hizmetleri**
     - **Mobil (Exchange ActiveSync)**
     - **IMAP**
     - **POP3**

   Bitirdikten sonra Kaydet'e ve **ardından** Kapat'a **tıklayın**.

### <a name="step-6-optional-remove-the-suspected-compromised-account-from-all-administrative-role-groups"></a>6. Adım İsteğe bağlı: Güvenliği ihlal edilmiş şüpheli hesabı tüm yönetim rol gruplarından kaldırma

> [!NOTE]
> Hesabın güvenliği sağlandıktan sonra, yönetim rolü grubu üyeliği geri yüklenebilir.

1. aşağıdaki Microsoft 365 yönetim merkezi <https://admin.microsoft.com>adımlarını uygulayın:
   1. **Kullanıcılar** \> **Etkin kullanıcılar**'a gidin. Doğrudan Etkin kullanıcılar sayfasına **gitmek için** , kullanın <https://admin.microsoft.com/Adminportal/Home#/users>.
   2. Etkin kullanıcılar **sayfasında,** kullanıcı hesabını bulup seçin, Diğer simgesine ![](../../media/ITPro-EAC-MoreOptionsIcon.png)tıklayın ve sonra da Rolleri yönet'i **seçin**.
   3. Hesaba atanmış olan tüm yönetici rollerini kaldırın. Bitirdikten sonra Değişiklikleri **kaydet'e tıklayın**.

2. 'Microsoft 365 Defender portalında <https://security.microsoft.com>aşağıdaki adımları uygulayın:
   1. Şu roller **için İzinler& e gidin** \> **: E-& işbirliği rolleri** \> **rolleri**. Doğrudan İzinler sayfasına **gitmek** için kullanın <https://security.microsoft.com/emailandcollabpermissions>.
   2. İzinler  sayfasında, listeden her rol grubunu seçin ve görüntülenen ayrıntılar açılır öğesinin **Üyeler bölümünde** kullanıcı hesabını bulun. Rol grubu kullanıcı hesabını içeriyorsa, aşağıdaki adımları izleyin:
      1. **Üyeler** bölümünde **Düzenle**'ye tıklayın.
      2. Görüntülenen **Düzenleme Üyeleri seç açılır** menüsünde Düzenle'ye **tıklayın**.
      3. Görüntülenen **Üye seç açılır** menüsünde Kaldır'a **tıklayın**.
      4. Görüntülenen açılır listeden kullanıcı hesabını seçin ve kaldır'a **tıklayın**.

         Bitirdikten sonra Bitti, Kaydet **ve** **Kapat'a** **tıklayın**.

3. 'daki Exchange merkezinde <https://admin.exchange.microsoft.com/>aşağıdaki adımları uygulayın:
   1. Roller **Yönetici** **rolleri'ni**\> seçin. Doğrudan Yönetici rolleri **sayfasına gitmek için** , ' kullanın <https://admin.exchange.microsoft.com/#/adminRoles>.
   2. Yönetici **rolleri sayfasında** her rol grubunu el ile seçin ve ayrıntılar bölmesinde Atanan sekmesini seçerek kullanıcı hesaplarını doğrulayın. Rol grubu kullanıcı hesabını içeriyorsa, aşağıdaki adımları izleyin:
      1. Kullanıcı hesabını seçin.
      2. Ardından ![Sil simgesi.](../../media/m365-cc-sc-delete-icon.png).

         Bitirdiğinizde, **Kaydet**'i tıklatın.

### <a name="step-7-optional-additional-precautionary-steps"></a>7. Adım İsteğe bağlı: Ek önlem adımları

1. Gönderilmiş öğelerinizi doğrulayın. Kişi listeniz kişileri, hesap güvenliğinizin ihlal edilmiş olduğu konusunda bilgilendirmeniz gerekiyor olabilir. Saldırgan para veya örneğin farklı bir ülkede yolda kaldığınız ve para gereken para istedi olabilir ya da saldırgan bilgisayarlarını da ele geçirtsin diye ona bir virüs gönderebilir.

2. Bu e-posta hesabını Exchange e-posta hesabı olarak tüm diğer hizmetler tehlikeye atılmış olabilir. İlk olarak, bu adımları Microsoft 365 ve sonra diğer hesaplarınız için bu adımları uygulayın.

3. Telefon numaraları ve adresler gibi kişi bilgilerinizin doğru olduğundan emin olun.

## <a name="secure-microsoft-365-like-a-cybersecurity-pro"></a>Siber Microsoft 365 gibi güvenliği sağlama

Microsoft 365 aboneliğiniz, verilerinizi ve kullanıcılarınızı korumak için kullanabileceğiniz güçlü bir güvenlik özellikleri kümesiyle gelir.  Güvenlik [Microsoft 365 kullanın - İlk 30 gün, 90](security-roadmap.md) gün ve bundan sonra Microsoft'un kiracı kiracının güvenliğini sağlamak için önerilen en iyi yöntemleri uygulamak için Microsoft 365 vardır.

- İlk 30 gün içinde yerine gelen görevler. Bunlar hemen etkiler ve kullanıcılarınız için düşük etki sağlar.
- 90 gün içinde yapılacak görevler. Bunlar planlamak ve uygulamak için biraz daha zaman alır ama güvenlik performansını büyük ölçüde geliştirin.
- 90 gün dışında. Bu iyileştirmeler ilk 90 gün çalışmanıza dahil.

## <a name="see-also"></a>Ayrıca bkz.

- [Yeni Bir Görünümde Kuralları Outlook Özel Form Ekleme Saldırılarını Algıla ve Microsoft 365](detect-and-remediate-outlook-rules-forms-attack.md)
- [İnternet Suç Şikayet Merkezi](https://www.ic3.gov/Home/Ransomware)
- [Securities and Exchange Commission - "Phishing" Fraud](https://www.sec.gov/investor/pubs/phishing.htm)
- İstenmeyen e-postayı doğrudan Microsoft'a ve yöneticinize bildirme [Rapor İletisi eklentinizi kullanın](https://support.microsoft.com/office/b5caa9f1-cdf3-4443-af8c-ff724ea719d2)
