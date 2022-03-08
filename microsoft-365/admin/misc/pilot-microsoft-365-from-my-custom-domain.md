---
title: Özel Microsoft 365 alanımdan pilot uygulama
f1.keywords:
- CSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
- Adm_TOC
ms.custom:
- admindeeplinkMAC
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
- MOE150
description: Yalnızca iki test hesabı kullanarak özel etki alanımdan bir posta Microsoft 365 e-posta işlevselliğini pilot yapmayı öğrenin.
ms.openlocfilehash: cc977afd32c1b3b660ec01285c36132a8e1d27b2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63323745"
---
# <a name="pilot-microsoft-365-from-my-custom-domain"></a>Özel Microsoft 365 alanımdan pilot uygulama

Şu gereksinimler ve Microsoft 365 ile pilot uygulama konusunda pilot uygulama yapın:

- Geçerli e-posta sağlayıcınızın e-posta iletmesi gerekir.

- Bu kayıtları Microsoft 365 yönetmek yerine, Microsoft 365 DNS kayıtlarınızı Microsoft 365 DNS barındırma sağlayıcınızda yönetebilirsiniz.

    Daha fazla bilgi edinmek için bkz [. Etki alanınıza bağlanmak için DNS kayıtları ekleme](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

- Diğer e-posta sunucusundaki kullanıcılar için serbest/meşgul bilgisi kullanılamaz.

- Yöneticiler tüm kullanıcı hesaplarını tek bir konumdan yönetebilirsiniz.

- Kullanıcılar istenmeyen posta filtrelemeyi Microsoft 365 mümkün olabilir.

- Bu, çok az sayıda kullanıcı için önerilir ve yalnızca pilot için e-posta kullanımı için geçerlidir.

## <a name="set-up-a-microsoft-365-pilot"></a>Pilot Microsoft 365 ayarlama

Pilot uygulama ayarlamak için şu Microsoft 365 izleyin:

### <a name="step-1-sign-in-to-the-microsoft-365-admin-center"></a>1. Adım: Oturum açma Microsoft 365 yönetim merkezi

1. İş veya okul [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) okul hesabınızla oturum açın.

2. Sol **Ayarlar** >  **Bölmesinde Etki Alanları'Ayarlar** seçin.

### <a name="step-2-verify-that-you-own-the-domain-you-want-to-use"></a>2. Adım: Kullanmak istediğiniz etki alanının sahibi olduğunu doğrulama

1. Etki Alanları **sayfasında Etki** alanı **ekle'yi seçin**.

2. Kutuya etki alanı adını yazın, Bu etki alanını **kullan'ı seçin ve** sonra da Devam'ı **seçin**.

3. E-posta ve anlık ileti gibi, etki alanınız ile test etmek istediğiniz hizmetleri seçin.

4. Etki alanını **doğrulama** sayfasında adım adım yönergeleri izleyin, amd ve ardından Doğrula'ya **tıklayın**.

    DNS değişikliklerinin etkili etkili olmak için birkaç dakika ile 72 saat arasında sürer.

    Doğrulama başarılı olduğunda, DNS kayıtlarınızı değiştirmeniz istenmektedir.

### <a name="step-3-mark-the-domain-as-shared-in-exchange-online"></a>3. Adım: Etki alanını paylaşılan olarak Exchange Online

1. Yönetim Exchange, Posta akışı bölümünde Kabul edilen etki alanları'ı seçin ve sonra da değiştirmek istediğiniz etki alanını seçin.

2. Pencereyi açmak için çift tıklayın ve İç **Geçiş'i seçin**.

3. **Kaydet**'i seçin.

    Bu ayarın etkilik için birkaç dakika gerektirebilirsiniz.

### <a name="step-4-unblock-the-existing-email-server-optional"></a>4. Adım: Mevcut e-posta sunucusunun engellemesini kaldırma (isteğe bağlı)

Microsoft 365, istenmeyen Exchange Online Protection için Exchange Online Protection (EOP) kullanır. EOP, geçerli posta sunucunuz tarafından yüksek hacimde istenmeyen posta iletildi algılasa, var olan posta sunucularınızı engelleyebilir. Diğer e-posta sağlayıcınızın istenmeyen posta korumasına güveniyorsanız, e-posta sağlayıcınızda sunucunun engellemesini Microsoft 365.

> [!NOTE]
> Var olan e-posta sunucunuzdan gelen tüm istenmeyen postaların, özgün sunucunuzdan gelen tüm istenmeyen postaların Microsoft 365 gelen postaların engellemesini kaldırabilirsiniz ve istenmeyen postaların ne kadar iyi Microsoft 365 olduğunu değerlendiresiniz.

1. Exchange yönetim merkezi gezinti bölmesinde Koruma'ya **ve sonra** Bağlantı **filtresi'ne tıklayın**.

2. İzin Ver **IP'leri** listesinde, öğesini **+** seçin ve geçerli e-posta sağlayıcınızın posta sunucusu IP adresini ekleyin.

### <a name="step-5-create-user-accounts-and-set-the-primary-reply-to-address"></a>5. Adım: Kullanıcı hesapları oluşturma ve birincil yanıt adresini ayarlama

1. Sol gezinti Microsoft 365 yönetim merkezi <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**UsersActive users öğesini**</a> >  seçin.

2. Var olan iki kullanıcı ekleyerek iki test hesabı oluşturun.

    Her hesap için **, + Kullanıcı ekle'yi** seçin ve test etmek istediğiniz parola yöntemi de içinde olmak üzere gerekli bilgileri doldurun.

    Bir kullanıcının e-posta adresinin aynı kalmasını sağlamak için, Kullanıcı **adı** alanı kullanıcının geçerli e-posta adresiyle eşleşmeli.

3. Uygun lisansı seçin, **Sonraki'ye tıklayın ve** sonra da Eklemeyi **bitir'e tıklayın**.

4. Kullanıcı **adı'nın** yanındaki açılan listeden özel etki alanı adınızı seçin.

5. **Close Oluştur'a** >  seçin.

### <a name="step-6-configure-mail-to-flow-from-microsoft-365-or-office-365-to-email-server"></a>6. Adım: **Postayı e-posta sunucusundan Microsoft 365 veya Office 365 olarak yapılandırma

Bunun iki adımı gerekir:

1. Kendi ortamınızı Microsoft 365 veya Office 365 yapılandırma.

2. E-posta sunucunuza Microsoft 365 veya Office 365 bir bağlayıcı ayarlayın.

### <a name="1-configure-your-microsoft-365-or-office-365-environment"></a>1. Çalışma ortamınızı Microsoft 365 veya Office 365 yapılandırma

Aşağıdaki adımları tamamlamış olduğundan emin Microsoft 365 Office 365:

1. Bağlayıcıları ayarlamak için, başlamadan önce size atanmış izinler gerekir. Size hangi izinlerin gerekli olduğunu kontrol etmek için, Microsoft 365 ve Office 365 ilgili başlık başlıklarında yer alan Özellik [izinleri Exchange Online](/exchange/permissions-exo/feature-permissions) bakın.

2. EOP veya başka bir Exchange Online e-postayı e-posta sunucularından İnternet'e geçişi için de kullanın:

   - Başka bir e-postada kabul edilen etki alanıyla eşleşen konu adı ile Microsoft 365 Office 365. Sertifikanın ortak adının veya konu alternatif adının, kurumuz için birincil SMTP etki alanıyla eşleşmesi önerilir. Ayrıntılar için bkz. [Şirket içi e-posta ortamının önkoşulları](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#prerequisites-for-your-on-premises-email-environment).

   -VEYA-

   - Tüm kuruluş gönderen etki alanlarınızı ve alt etki alanlarınızı bu etki alanı veya etki alanlarında kabul edilen etki alanları olarak yapılandırıldığından emin Microsoft 365 Office 365.

   Kabul edilen etki alanlarını tanımlama hakkında daha fazla bilgi için [](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) bkz. Exchange Online'de kabul edilen etki alanlarını yönetme ve [Exchange Online.](/exchange/mail-flow-best-practices/manage-accepted-domains/enable-mail-flow-for-subdomains)

3. E-posta sunucularına posta göndermek için posta akış kurallarını (aktarım kuralları olarak da bilinir) veya etki alanı adlarını mı Microsoft 365 Office 365 karar verin. Çoğu işletme, tüm kabul edilen etki alanları için posta teslimi seçer. Daha fazla bilgi için bkz[. Senaryo: Koşullu posta yönlendirmesi Exchange Online](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/conditional-mail-routing).

> [!NOTE]
> Posta akış kurallarını, Aşağıdakiler makalesinde posta [akışı kuralı eylemlerini açıklandığı Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions). Örneğin, postanız şu anda dağıtım listeleri aracılığıyla birden çok siteye yönlendirildiyse, bağlayıcılarla posta akış kurallarını kullanmak istiyor olabileceğiniz gibi, bunu da kullanabilirsiniz.

### <a name="2-set-up-a-connector-from-microsoft-365-or-office-365-to-your-email-server"></a>2. E-posta sunucunuza Microsoft 365 veya Office 365 bir bağlayıcı ayarlayın

Microsoft 365 veya Office 365'da bağlayıcı oluşturmak için Yönetici  > **Exchange** yi seçerek Exchange gidin. Ardından, posta **akışıTaktörler'i** >  <a href="https://go.microsoft.com/fwlink/?linkid=2183136" target="_blank">**seçin**</a>.

Sihirbazı kullanarak bağlayıcıları ayarlayın.

Sihirbazı başlatmak için artı simgesine **+** tıklayın. İlk ekranda, Farklı bir **Office 365** **ve Kuruluş Posta sunucunuza'ı** seçin.

**Sonraki'ne** tıklayın ve sihirbazda yönergeleri izleyin. Daha fazla **bilgiye ihtiyacınız** **varsa Yardım veya** Daha Fazla Bilgi bağlantılarına tıklayın. Sihirbaz kurulum boyunca size yol sağlar. Sonunda bağlayıcının doğru olduğundan emin olun. Bağlayıcı doğrulanmazsa, daha fazla bilgi almak için görüntülenen iletiye çift tıklayın ve sorunları çözme konusunda yardım almak [için Bağlayıcıları](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/validate-connectors) doğrulama'ya bakın.



### <a name="step-7-update-dns-records-at-your-dns-hosting-provider"></a>7. Adım: DNS barındırma sağlayıcınızda DNS kayıtlarını güncelleştirme

DNS barındırma sağlayıcınızın web sitesinde oturum açma ve Etki alanınıza bağlanmak için [DNS kayıtları ekleme bağlantısında verilen yönergeleri izleyin](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).

**Aşağıdaki iki özel durumu yapma:**

- Yeni bir MX kaydı oluşturma veya var olan MX kaydınızı değiştirme.

- Önceki e-posta sağlayıcınız için bir Sender Policy Framework (SPF) kaydınız zaten varsa, Exchange Online için yeni bir SPF (TXT) kaydı oluşturmak yerine, "include:spf.protection.outlook.com" dosyasını geçerli TXT kaydına ekleyin.

    Örneğin, "v=spf1 mx include:adatum.com include:spf.protection.outlook.com ~all".

    SPF kaydınız yoksa, SPF kaydınız varsa, Microsoft 365 tarafından geçerli e-posta sağlayıcınız için etki alanını içerecek şekilde önerilen kaydı spf.protection.outlook.com. Bu her iki e-posta sistemlerinden giden iletileri yetkilendirmektedir.

### <a name="step-8-set-up-email-forwarding-at-your-current-provider"></a>8. Adım: Geçerli sağlayıcınızda e-posta iletmeyi ayarlama

Geçerli e-posta sağlayıcınızda, kullanıcılarınız için e-posta hesaplarının etki alanınıza ilet onmicrosoft.com ayarlayın:

- Forward User A mailbox to usera@yourcompany.onmicrosoft.com

- Kullanıcı B posta kutusunu posta kutusuna userb@yourcompany.onmicrosoft.com

Bu adımı tamamlarsanız, usera@yourcompany.com ve userb@yourcompany.com e-Microsoft 365.

> [!NOTE]
> E-posta iletmeyi ayarlamanın tam adımları için geçerli e-posta sağlayıcınıza başvurun.<br/>
> Geçerli e-posta sağlayıcısında iletilerin bir kopyasını tutmanız gerek değildir.<br/>
> Sağlayıcıların çoğu e-postayı, yanıtların özgün gönderene gidecek şekilde gönderenin Yanıtla adresine bozulmadan iletir.

### <a name="step-9-test-mail-flow"></a>9. Adım: Test posta akışı

1. A Kullanıcı Outlook Web App bilgilerini kullanarak oturum açma.

2. Şu testleri gerçekleştirin:

    - Yerel Microsoft e-postalarını, örneğin Kullanıcı B'ye bir e-posta göndererek test edin. E-posta hemen teslim edilir. Bu senaryoda, ileti özgün sunucunuzda Kullanıcı B'nin posta kutusuna yönlendirlanmaz çünkü posta Microsoft 365 yerel olur.

    - Var olan e-posta sisteminde bir kullanıcıya, örneğin Kullanıcı C'ye e-posta göndererek e-postayı test edin. E-posta, özgün posta sunucunuzda C Kullanıcısı için gelen kutusuna teslim edilir.

    - Iletmenin dışarıdan bir hesaptan veya var olan e-posta sisteminde çalışan e-posta hesabından doğru bir şekilde ayar olduğunu doğrulayın. Örneğin, Kullanıcı C'nin özgün sunucu hesabından veya bir Hotmail hesabından Kullanıcı A'ya bir e-posta gönderin ve A Kullanıcısı'nın Microsoft 365 kutusuna geldiğinden emin olun.

### <a name="step-10-move-mailbox-contents"></a>10. Adım: Posta kutusu içeriğini taşıma

Yalnızca iki test kullanıcısına sahip olduğunu ve hem A kullanıcısı hem de B Kullanıcısı'nın Outlook kullanıyor olduğundan, e-postayı eski . PST dosyası olarak yeni Outlook ve iletileri, takvim öğelerini, kişileri, diğer öğeleri kopyalar. Daha fazla bilgi için bkz[. E-postayı, kişileri ve takvimi Outlook .pst dosyasından içeri aktarma](https://support.microsoft.com/office/import-email-contacts-and-calendar-from-an-outlook-pst-file-431a8e9a-f99f-4d5f-ae48-ded54b3440ac).

Öğeler posta kutusunda uygun konumlara Microsoft 365 aktarıldıktan sonra, bu öğelere her cihazdan ve her yerden erişilebilir.
