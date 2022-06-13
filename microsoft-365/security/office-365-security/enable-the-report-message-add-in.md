---
title: Rapor İletisini veya Rapor Kimlik Avı eklentilerini etkinleştirme
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
description: Outlook ve Web üzerinde Outlook için, tek tek kullanıcılar için veya kuruluşunuzun tamamı için Rapor İletisi veya Rapor Kimlik Avı eklentilerini etkinleştirmeyi öğrenin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b0882a37161989248b8c970a5dbe01efc0bcff65
ms.sourcegitcommit: a7c1acfb3d2cbba913e32493b16ebd8cbfeee456
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/13/2022
ms.locfileid: "66043773"
---
# <a name="enable-the-report-message-or-the-report-phishing-add-ins"></a>Rapor İletisini veya Rapor Kimlik Avı eklentilerini etkinleştirme

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**Uygulandığı öğe**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!NOTE]
> Exchange Online posta kutuları olan bir Microsoft 365 kuruluşunda yöneticiyseniz, Microsoft 365 Defender portalındaki **Gönderimler** sayfasını kullanmanızı öneririz. Daha fazla bilgi için bkz. [Şüpheli istenmeyen postaları, kimlik avı, URL'leri ve dosyaları Microsoft'a göndermek için Yönetici Gönderimi'ni kullanma](admin-submission.md).

Outlook ve Web üzerinde Outlook (eski adıyla Outlook Web App) için Rapor İletisi ve Rapor Kimlik Avı eklentileri, hatalı pozitif (kötü olarak işaretlenmiş iyi e-posta) veya hatalı negatifleri (hatalı e-postalara izin verilir) analiz için Microsoft'a ve bağlı kuruluşlarına bildirmeyi kolaylaştırır.

Microsoft, e-posta koruma teknolojilerinin verimliliğini artırmak için bu gönderimleri kullanır. Örneğin, kişilerin Rapor Kimlik Avı eklentisini kullanarak birçok ileti bildirdiğini varsayalım. Bu bilgiler Güvenlik Panosu'nda ve diğer raporlarda görünür. Kuruluşunuzun güvenlik ekibi, kimlik avına karşı koruma ilkelerinin güncelleştirilmiş olması gerekebileceğinin göstergesi olarak bu bilgileri kullanabilir.

Rapor İletisi'ni veya Rapor Kimlik Avı eklentisini yükleyebilirsiniz. Kullanıcılarınızın hem istenmeyen posta hem de kimlik avı iletilerini bildirmesini istiyorsanız, Kuruluşunuzda Rapor İletisi eklentisini dağıtın.

Rapor İletisi eklentisi, hem istenmeyen posta hem de kimlik avı iletilerini raporlama seçeneği sağlar. Yöneticiler kuruluş için Rapor İletisi eklentisini etkinleştirebilir ve tek tek kullanıcılar bu eklentiyi kendileri yükleyebilir.

Kimlik Avı Bildir eklentisi yalnızca kimlik avı iletilerini raporlama seçeneği sağlar. Yöneticiler kuruluş için Kimlik Avı Raporu eklentisini etkinleştirebilir ve tek tek kullanıcılar bu eklentiyi kendileri yükleyebilir.

Tek bir kullanıcıysanız, her iki eklentiyi de kendiniz etkinleştirebilirsiniz.

Genel yönetici veya Exchange Online yöneticisiyseniz ve Exchange OAuth kimlik doğrulamasını kullanacak şekilde yapılandırılmışsa, kuruluşunuz için Rapor İletisi eklentisini ve Kimlik Avı Bildir eklentisini etkinleştirebilirsiniz. Her iki eklenti de artık [Merkezi Dağıtım](../../admin/manage/centralized-deployment-of-add-ins.md) aracılığıyla kullanılabilir.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Hem Rapor İletisi eklentisi hem de Rapor Kimlik Avı eklentisi, çoğu Microsoft 365 aboneliği ve aşağıdaki ürünlerle çalışır:
  - Web üzerinde Outlook
  - Outlook 2013 SP1 veya üzeri
  - Mac için Outlook 2016
  - Enterprise için Microsoft 365 uygulamalarına dahil Outlook
  - iOS ve Android için Outlook uygulaması

- Paylaşılan, gruplandırılmış veya temsilci olarak atanan posta kutuları için her iki eklenti de kullanılamaz (eklentiler gri görünür).

- Her iki eklenti de şirket içi Exchange posta kutuları için kullanılamaz.

- Mevcut web tarayıcınız hem Rapor İletisi hem de Rapor Kimlik Avı eklentileriyle çalışmalıdır. Ancak eklentinin kullanılabilir olmadığını veya beklendiği gibi çalışmadığını fark ederseniz farklı bir tarayıcı deneyin.

- Kuruluş yüklemeleri için kuruluşun OAuth kimlik doğrulamasını kullanacak şekilde yapılandırılması gerekir. Daha fazla bilgi için bkz. [Eklentilerin Merkezi Dağıtımının kuruluşunuzda çalışıp çalışmadığını belirleme](../../admin/manage/centralized-deployment-of-add-ins.md).

- Yöneticilerin Genel yöneticiler rol grubunun üyesi olması gerekir. Daha fazla bilgi için bkz. [Microsoft 365 Defender portalında İzinler](permissions-microsoft-365-security-center.md).

- İletiYi Raporla özelliğini kullanarak bir iletiyi bildirme hakkında daha fazla bilgi için bkz. [Outlook hatalı pozitifleri ve hatalı negatifleri](report-false-positives-and-false-negatives.md) raporlama.

- URL filtreleme veya güvenlik çözümü (ara sunucu ve/veya güvenlik duvarı gibi) olan kuruluşların HTTPS protokolünde ipagave.azurewebsites.net ve outlook.office.com uç noktalarına erişmesine izin verilmelidir.

## <a name="get-the-report-message-add-in"></a>Rapor İletisi eklentisini alma

### <a name="get-the-report-message-add-in-for-yourself"></a>Rapor İletisi eklentisini kendiniz alın

1. adresinden Microsoft AppSource'a <https://appsource.microsoft.com/marketplace/apps> gidin ve Rapor İletisi eklentisini arayın. Doğrudan Rapor İletisi eklentisine gitmek için <https://appsource.microsoft.com/product/office/wa104381180>adresine gidin.

2. **ŞİmDİ ALA'YA** TıKLAYıN.

   :::image type="content" source="../../media/ReportMessageGETITNOW.png" alt-text="Şimdi Al rapor iletisi." lightbox="../../media/ReportMessageGETITNOW.png":::

3. Görüntülenen iletişim kutusunda kullanım koşullarını ve gizlilik ilkesini gözden geçirin ve **ardından Devam'a** tıklayın.

4. İş veya okul hesabınızı (iş kullanımı için) veya Microsoft hesabınızı (kişisel kullanım için) kullanarak oturum açın.

Eklenti yüklenip etkinleştirildikten sonra aşağıdaki simgeleri görürsünüz:

- Outlook simgesi şöyle görünür:

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/OutlookReportMessageIcon.png" alt-text="Outlook için Rapor İletisi eklenti simgesi." lightbox="../../media/OutlookReportMessageIcon.png":::

- Web üzerinde Outlook simgesi şöyle görünür:

    > [!div class="mx-imgBorder"]
    > ![Web üzerinde Outlook Rapor İletisi eklenti simgesi.](../../media/owa-report-message-icon.png)

### <a name="get-the-report-message-add-in-for-your-organization"></a>Kuruluşunuz için Rapor İletisi eklentisini alma

> [!NOTE]
> Eklentinin kuruluşunuzda görünmesi 12 saat kadar sürebilir.

1. [Microsoft 365 yönetim merkezi](https://admin.microsoft.com/AdminPortal/Home?#/homepage) Ayarlar **Tümleşik uygulamalar'a** \> gidin. **Uygulama al'a** tıklayın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-integrated-apps.png" alt-text="Microsoft 365 yönetim merkezi Tümleşik uygulamalar." lightbox="../../media/microsoft-365-admin-center-integrated-apps.png":::

2. Görüntülenen **Microsoft 365 Uygulamaları** sayfasında **, Arama** kutusuna tıklayın, **Rapor İletisi** yazın ve Arama **Ara** ![simgesine tıklayın.](../../media/search-icon.png). Sonuç listesinde **Rapor İletisi'ni** bulun ve seçin.

3. Uygulama ayrıntıları sayfası açılır. **Şimdi Al'ı** seçin.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-report-message.png" alt-text="Rapor İletisi eklentisi." lightbox="../../media/microsoft-365-admin-center-report-message.png":::

4. Temel profil bilgilerini tamamlayın ve **devam'a** tıklayın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-profile-info.png" alt-text="Rapor İletisi eklenti profili kurulumu." lightbox="../../media/microsoft-365-admin-center-profile-info.png":::

5. **Yeni Uygulama Dağıt** açılır öğesi açılır. Aşağıdaki ayarları yapılandırın. Kurulumu tamamlamak için sonraki sayfaya gitmek için **İleri'ye** tıklayın.

   - **Kullanıcı ekle**: Aşağıdaki değerlerden birini seçin:
     - **Sadece ben**
     - **Kuruluşun tamamı**
     - **Belirli kullanıcılar / gruplar**

   - **Dağıtım**:
     - **İzin isteklerini kabul et**: Sonraki sayfaya geçmeden önce uygulama izinlerini ve özelliklerini dikkatle okuyun.

        > [!div class="mx-imgBorder"]
        > :::image type="content" source="../../media/microsoft-365-admin-center-deploy-new-app.png" alt-text="İzinleri kabul et istekleri sayfası." lightbox="../../media/microsoft-365-admin-center-deploy-new-app.png":::

     - **Dağıtımı bitir**: Eklentiyi gözden geçirin ve dağıtmayı tamamlayın.
     - **Dağıtım tamamlandı**: Kurulumu tamamlamak için **Bitti'yi** seçin.

        > [!div class="mx-imgBorder"]
        > :::image type="content" source="../../media/microsoft-365-admin-center-deployment-complete.png" alt-text="Dağıtımın bildirim iletisi tamamlandı." lightbox="../../media/microsoft-365-admin-center-deployment-complete.png":::

## <a name="edit-settings-for-the-report-message-add-in"></a>Rapor İletisi eklentisinin ayarlarını düzenleme

1. Microsoft 365 yönetim merkezi **tümleşik uygulamalar** **Ayarlar** \> gidin \. Ardından **Rapor İletisi eklentisini** bulup seçin.

2. Görüntülenen açılır öğede **Kullanıcıları düzenle'yi** seçerek kullanıcı ayarlarını düzenleyin.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-report-message-edit.png" alt-text="Rapor İletisi açılır öğesi." lightbox="../../media/microsoft-365-admin-center-report-message-edit.png":::

3. Eklentiyi kaldırmak için aynı açılır öğedeki **Eylemler'in** altında **Uygulamayı kaldır'ı** seçin.

## <a name="get-the-report-phishing-add-in"></a>Rapor Kimlik Avı eklentisini edinin

### <a name="get-the-report-phishing-add-in-for-yourself"></a>Rapor Kimlik Avı eklentisini kendiniz edinin

1. adresinden Microsoft AppSource'a <https://appsource.microsoft.com/marketplace/apps> gidin ve Rapor Kimlik Avı eklentisini arayın.

2. **ŞİmDİ ALA'YA** TıKLAYıN.

3. Görüntülenen iletişim kutusunda kullanım koşullarını ve gizlilik ilkesini gözden geçirin ve **ardından Devam'a** tıklayın.

4. İş veya okul hesabınızı (iş kullanımı için) veya Microsoft hesabınızı (kişisel kullanım için) kullanarak oturum açın.

Eklenti yüklenip etkinleştirildikten sonra aşağıdaki simgeleri görürsünüz:

- Outlook simgesi şöyle görünür:

  ![Outlook için Rapor Kimlik Avı eklentisi simgesi.](../../media/Outlook-ReportPhishing.png)

- Web üzerinde Outlook simgesi şöyle görünür:

    > [!div class="mx-imgBorder"]
    > ![Web üzerinde Outlook Kimlik Avı Eklentisini Bildir simgesi.](../../media/OWA-ReportPhishing.png)

### <a name="get-the-report-phishing-add-in-for-your-organization"></a>Kuruluşunuz için Kimlik Avı Raporu eklentisini edinin

> [!NOTE]
> Eklentinin kuruluşunuzda görünmesi 12 saat kadar sürebilir.

1. [Microsoft 365 yönetim merkezi](https://admin.microsoft.com/AdminPortal/Home?#/homepage) Ayarlar **Tümleşik uygulamalar'a** \> gidin. **Uygulama al'a** tıklayın.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-integrated-apps.png" alt-text="Microsoft 365 yönetim merkezi Tümleşik uygulamalar." lightbox="../../media/microsoft-365-admin-center-integrated-apps.png":::

2. Görüntülenen **Microsoft 365 Uygulamaları** sayfasında **, Arama** kutusuna tıklayın, **Rapor Kimlik Avı** yazın ve Arama **Ara** ![simgesine tıklayın.](../../media/search-icon.png). Sonuç listesinde **Kimlik Avı Bildir'i** bulun ve seçin.

3. Uygulama ayrıntıları sayfası açılır. **Şimdi Al'ı** seçin.

4. Temel profil bilgilerini tamamlayın ve **devam'a** tıklayın.

5. **Yeni Uygulama Dağıt** açılır öğesi açılır. Kurulumu tamamlamak için [yukarıda açıklanan](enable-the-report-message-add-in.md#get-the-report-message-add-in-for-your-organization) adımları izleyin.

## <a name="edit-settings-for-the-report-phishing-add-in"></a>Rapor Kimlik Avı eklentisi ayarlarını düzenleme

1. Microsoft 365 yönetim merkezi **tümleşik uygulamalar** **Ayarlar** \> gidin \. Ardından **Kimlik Avı Eklentisini Raporla'yı** bulup seçin.

2. Görüntülenen açılır öğede **Kullanıcıları düzenle'yi** seçerek kullanıcı ayarlarını düzenleyin.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/microsoft-365-admin-center-report-phishing-edit.png" alt-text="Rapor Kimlik Avı açılır öğesi." lightbox="../../media/microsoft-365-admin-center-report-phishing-edit.png":::

3. Eklentiyi kaldırmak için aynı açılır öğedeki **Eylemler'in** altında **Uygulamayı kaldır'ı** seçin.
