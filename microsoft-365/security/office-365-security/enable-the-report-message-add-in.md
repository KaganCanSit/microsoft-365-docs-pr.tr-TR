---
title: Rapor İletisi'yi veya Rapor Kimlik Avı eklentilerini etkinleştirme
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 4250c4bc-6102-420b-9e0a-a95064837676
ms.collection:
- M365-security-compliance
description: Tek tek kullanıcılar veya tüm kuruluş için Rapor İletisini veya Kimlik Avını Bildirme eklentilerini Outlook Web üzerinde Outlook etkinleştirebilirsiniz.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: dc4c03a0ed1f0a03d96776c841203c9131c3067c
ms.sourcegitcommit: 9af389e4787383cd97bc807f7799ef6ecf0664d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2022
ms.locfileid: "63468888"
---
# <a name="enable-the-report-message-or-the-report-phishing-add-ins"></a>Rapor İletisi'yi veya Rapor Kimlik Avı eklentilerini etkinleştirme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Geçerli olduğu yer:**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [1. plan Office 365 plan 2 için Microsoft Defender](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> Posta kutuları olan bir Microsoft 365 kuruluşunda Exchange Online iseniz, Microsoft 365 Defender portalında Gönderiler sayfasını kullanmanızı öneririz. Daha fazla bilgi için bkz. Yönetici Gönderimi'ni kullanarak şüpheli istenmeyen posta, kimlik avı [, URL'ler ve dosyaları Microsoft'a gönderme](admin-submission.md).

Outlook ve Web üzerinde Outlook için Rapor İletisi ve Rapor Kimlik Avı eklentileri (eski adı Outlook Web App), hatalı pozitif sonuçların (iyi e-posta kötü olarak işaretlenen iyi e-posta) veya yanlış negatifleri (izin verilen hatalı e-posta) Microsoft'a ve bağlı ortaklarına çözümleme yapmak için bildirmeyi kolaylaştırır.

Microsoft, e-posta koruma teknolojilerinin daha etkili olması için bu gönderileri kullanır. Örneğin, kişilerin Kimlik Avı Bildir eklentilerini kullanarak birçok ileti bildirdiklerini varsayalım. Bu bilgi, Güvenlik Panosunda ve diğer raporlarda yer almaktadır. Kuruluş güvenlik ekibi bu bilgileri kimlik avıyla mücadele ilkelerinin güncelleştirilebilir olabileceğinin göstergesi olarak kullanabilir.

Rapor İletisi'yi veya Rapor Kimlik Avı eklentilerini yükleyebilirsiniz. Kullanıcılarının hem istenmeyen postaları hem de kimlik avı iletilerini bildirmesini istemiyorsanız, Rapor İletisi eklentisini dağıtın.

Rapor İletisi eklentileri, hem istenmeyen postaları hem de kimlik avı iletilerini bildirme seçeneği sağlar. Yöneticiler Kuruluş için Rapor İletisi eklentilerini etkinleştirebilirsiniz ve tek tek kullanıcılar da bu eklentiyi kendileri yükleyebilir.

Rapor Kimlik Avı eklentisinde, yalnızca kimlik avı iletilerini bildirme seçeneği vardır. Yöneticiler kuruluş için Rapor Kimlik Avı eklentilerini etkinleştirebilirsiniz ve tek tek kullanıcılar da bu eklentiyi kendileri yükleyebilir.

Bireysel bir kullanıcıysanız, her iki eklentiyi de kendiniz için etkinleştirebilirsiniz.

Genel yönetici veya Exchange Online yöneticisiyseniz ve Exchange OAuth kimlik doğrulamasını kullanmak üzere yapılandırılmışsa, Rapor İletisi eklentinizi ve raporunuz için Kimlik Avı Bildir eklentinizi etkinleştirebilirsiniz. Her iki eklenti de artık Merkezi Dağıtım aracılığıyla [kullanılabilir](../../admin/manage/centralized-deployment-of-add-ins.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Rapor İletisi eklentileri ve Rapor Kimlik Avı eklentileri, diğer aboneliklerin çoğuyla Microsoft 365 aşağıdaki ürünlerle çalışır:
  - Web üzerinde Outlook
  - Outlook 2013 SP1 veya sonrası
  - Mac için Outlook 2016
  - Outlook için Microsoft 365 uygulamalarına dahil Enterprise
  - iOS Outlook Android için uygulama

- Paylaşılan posta kutuları için her iki eklenti de kullanılamaz.

- Her iki eklenti de şirket içi veya posta kutularında Exchange kullanılamaz. 

- Var olan web tarayıcınız, hem Rapor İletisi hem de Rapor Kimlik Avı eklentileriyle birlikte çalışır. Ancak, eklentinin kullanılabilir olmadığını veya beklendiği gibi çalışmadı olduğunu fark ettiysanız, farklı bir tarayıcı deneyin.

- Kuruluş yüklemelerinde, kuruluşun OAuth kimlik doğrulamasını kullanmak üzere yapılandırılması gerekir. Daha fazla bilgi için bkz [. Merkezi Dağıtım eklentilerinin kuruluşu için çalışır olup olmadığını belirleme](../../admin/manage/centralized-deployment-of-add-ins.md).

- Yöneticilerin Genel yöneticiler rol grubunun bir üyesi olması gerekir. Daha fazla bilgi için bkz[. Microsoft 365 Defender portalına.](permissions-microsoft-365-security-center.md)

- İletiyi Bildir özelliğini kullanarak iletiyi bildirme hakkında daha fazla bilgi için bkz. İletide hatalı pozitif [ve yanlış negatif Outlook](report-false-positives-and-false-negatives.md).

- Bir URL filtrelemesi veya güvenlik çözümü (proxy ve/veya güvenlik duvarı gibi) olan kuruluşlar, HTTPS protokolüyle erişime izin verilen ipagave.azurewebsites.net outlook.office.com uç noktalarına sahip olmalıdır.

### <a name="turn-off-the-built-in-reporting-experience"></a>Yerleşik raporlama deneyimini kapatma

Outlook'de yerleşik raporlama deneyimini önerilmez, çünkü kullanıcı gönderim ilkesi [kullanamaz](./user-submission.md). Bunun yerine Rapor İletisi eklentinizi veya Rapor Kimlik Avı eklentinizi öneririz.

Bu cmdlet'i çalıştırabilirsiniz. Kurumda herhangi bir cmdlet'i veya parametreyi çalıştırmak için gereken izinleri bulmak için bkz. [Herhangi bir cmdlet'i çalıştırmak için Exchange bulma](/powershell/exchange/find-exchange-cmdlet-permissions).

Yerleşik raporlama deneyimini devre dışı bırakmak için aşağıdaki PowerShell komutunu çalıştırın:

```powershell
Set-OwaMailboxPolicy -Identity OwaMailboxPolicy-Default -ReportJunkEmailEnabled $false
```

## <a name="get-the-report-message-add-in"></a>Rapor İletisi eklentilerini al

### <a name="get-the-report-message-add-in-for-yourself"></a>Rapor İletisi eklentisinde kendiniz için bir eklenti edinebilirsiniz

1. Rapor İletisi eklentisinde Microsoft AppSource'a <https://appsource.microsoft.com/marketplace/apps> gidin ve eklentiyi arayın. Doğrudan Rapor İletisi eklentinize gitmek için, gidin <https://appsource.microsoft.com/product/office/wa104381180>.

2. HEMEN **TIKLA'ya tıklayın**.

   ![İletiyi bildir: Şimdi al.](../../media/ReportMessageGETITNOW.png)

3. Görüntülenen iletişim kutusunda, kullanım koşulları ve gizlilik ilkesi'ne tıklayın ve sonra da Devam'a **tıklayın**.

4. İş veya okul hesabınızla (iş kullanımı için) veya Microsoft hesabınızla (kişisel kullanım için) oturum açın.

Eklenti yüklendikten ve etkinleştirildikten sonra, aşağıdaki simgeleri görebilirsiniz:

- Simge Outlook şöyle görünür:

    > [!div class="mx-imgBorder"]
    > ![Rapor İletisi eklentileri simgesi Outlook.](../../media/OutlookReportMessageIcon.png)

- Simge Web üzerinde Outlook şöyle görünür:

    > [!div class="mx-imgBorder"]
    > ![Web üzerinde Outlook İletisi eklenti simgesine dokunun.](../../media/owa-report-message-icon.png)

### <a name="get-the-report-message-add-in-for-your-organization"></a>Kurum için Rapor İletisi eklentinizi almak

> [!NOTE]
> Eklentinin kuruluşta görünmesi 12 saat kadar sürebilir.

1. Aşağıdaki [Microsoft 365 yönetim merkezi](https://admin.microsoft.com/AdminPortal/Home?#/homepage), **Tümleşik Ayarlar** \> **gidin**. Uygulamaları **al'a tıklayın**.

    > [!div class="mx-imgBorder"]
    > ![Microsoft 365 yönetim merkezi Tümleşik uygulamalar](../../media/microsoft-365-admin-center-integrated-apps.png)

2. Görüntülenen **Microsoft 365 Uygulamaları** Arama kutusuna tıklayın, **Rapor İletisi** girin ve Ara Ara **simgesine** ![tıklayın.](../../media/search-icon.png) Sonuç listesinde İletiyi Bildir'i bulup **seçin**. 

3. Uygulama ayrıntıları sayfası açılır. Şimdi **Al'ı seçin**. 

    > [!div class="mx-imgBorder"]
    > ![Rapor İletisi eklentisi](../../media/microsoft-365-admin-center-report-message.png)  

4. Temel profil bilgilerini tamamlandıktan sonra Devam'a **tıklayın**. 

    > [!div class="mx-imgBorder"]
    > ![Rapor İletisi eklenti profili kurulumu](../../media/microsoft-365-admin-center-profile-info.png)

5. Yeni **Uygulama Dağıtımı** açılır. Aşağıdaki ayarları yapılandırabilirsiniz. Kurulumu **tamamlamak** üzere bir sonraki sayfaya gitmek için Sonraki'ne tıklayın. 

   - **Kullanıcı ekleme**: Aşağıdaki değerlerden birini seçin:
     - **Sadece ben**
     - **Tüm kuruluş**
     - **Belirli kullanıcılar / gruplar**

   - **Dağıtım**:
     - **İzin isteklerini kabul etme**: Sonraki sayfaya gitmeden önce uygulama izinlerini ve özelliklerini dikkatle okuyun.

        > [!div class="mx-imgBorder"]
        > ![Uygulama izinleri](../../media/microsoft-365-admin-center-deploy-new-app.png)

     - **Dağıtımı bitir**: Eklentiyi gözden geçirip dağıtmayı bitirin. 
     - **Dağıtım tamamlandı**: Kurulumu **tamamlamak için** Bitti'yi seçin. 

        > [!div class="mx-imgBorder"]
        > ![Dağıtım tamamlandı](../../media/microsoft-365-admin-center-deployment-complete.png)

## <a name="edit-settings-for-the-report-message-add-in"></a>Rapor İletisi eklentisinde ayarları düzenleme

1. Aşağıdaki Microsoft 365 yönetim merkezi Tümleşik **uygulamalar'Ayarlar** \> **gidin** \. Ardından, Rapor **İletisi eklenti'yi** bulup seçin.

2. Görüntülenen açılır listeden, kullanıcı ayarlarını düzenlemek **için Kullanıcıları** düzenle'yi seçin.

    > [!div class="mx-imgBorder"]
    > ![Rapor İletisi uçarak çıkış](../../media/microsoft-365-admin-center-report-message-edit.png)

3. Eklentiyi kaldırmak için aynı çıkışta **Eylemler'in** **altında** Uygulamayı kaldır'ı seçin. 

## <a name="get-the-report-phishing-add-in"></a>Rapor Kimlik Avı eklentilerini almak

### <a name="get-the-report-phishing-add-in-for-yourself"></a>Rapor Kimlik Avı eklentini kendiniz için edinin

1. Microsoft AppSource'a gidin ve <https://appsource.microsoft.com/marketplace/apps> Rapor Kimlik Avı eklentinizi arayın.

2. HEMEN **TIKLA'ya tıklayın**.

3. Görüntülenen iletişim kutusunda, kullanım koşulları ve gizlilik ilkesi'ne tıklayın ve sonra da Devam'a **tıklayın**.

4. İş veya okul hesabınızla (iş kullanımı için) veya Microsoft hesabınızla (kişisel kullanım için) oturum açın.

Eklenti yüklendikten ve etkinleştirildikten sonra, aşağıdaki simgeleri görebilirsiniz:

- Simge Outlook şöyle görünür:

  ![Rapor Kimlik Avı eklentileri simgesi Outlook.](../../media/Outlook-ReportPhishing.png)

- Simge Web üzerinde Outlook şöyle görünür:

    > [!div class="mx-imgBorder"]
    > ![Web üzerinde Outlook Kimlik Avı Bildir eklenti simgesi.](../../media/OWA-ReportPhishing.png)

### <a name="get-the-report-phishing-add-in-for-your-organization"></a>Organizasyonunız için Rapor Kimlik Avı eklentinizi almak

> [!NOTE]
> Eklentinin kuruluşta görünmesi 12 saat kadar sürebilir.

1. Aşağıdaki [Microsoft 365 yönetim merkezi](https://admin.microsoft.com/AdminPortal/Home?#/homepage), **Tümleşik Ayarlar** \> **gidin**. Uygulamaları **al'a tıklayın**.

    > [!div class="mx-imgBorder"]
    > ![Microsoft 365 yönetim merkezi Tümleşik uygulamalar](../../media/microsoft-365-admin-center-integrated-apps.png)

2. Görüntülenen **Microsoft 365 Uygulamaları** Arama kutusuna tıklayın, Rapor Kimlik Avı girin ve Ara  Ara **simgesine** ![tıklayın.](../../media/search-icon.png) Sonuç listesinde Kimlik Avını **Bildir'i bulup seçin**. 
 
3. Uygulama ayrıntıları sayfası açılır. Şimdi **Al'ı seçin**.

4. Temel profil bilgilerini tamamlandıktan sonra Devam'a **tıklayın**.

5. Yeni **Uygulama Dağıtımı** açılır. Kurulumu tamamlamak [için yukarıda açıklanan](enable-the-report-message-add-in.md#get-the-report-message-add-in-for-your-organization) adımları izleyin. 

## <a name="edit-settings-for-the-report-phishing-add-in"></a>Rapor Kimlik Avı eklenti ayarları düzenleme

1. Aşağıdaki Microsoft 365 yönetim merkezi Tümleşik **uygulamalar'Ayarlar** \> **gidin** \. Ardından Kimlik Avı **Eklentilerini Bildir'i** bulup seçin.

2. Görüntülenen açılır listeden, kullanıcı ayarlarını düzenlemek **için Kullanıcıları** düzenle'yi seçin.

    > [!div class="mx-imgBorder"]
    > ![Rapor Kimlik Avı uçarak çıkış](../../media/microsoft-365-admin-center-report-phishing-edit.png)

3. Eklentiyi kaldırmak için aynı çıkışta **Eylemler'in** **altında** Uygulamayı kaldır'ı seçin. 
