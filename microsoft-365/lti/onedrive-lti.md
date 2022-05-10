---
title: Microsoft OneDrive LTI'yi Tuval ile tümleştirme
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: Tuval için yeni Microsoft OneDrive Learning Araçları Birlikte Çalışabilirlik Uygulaması ile ödevler oluşturun ve notlayın, kurs içeriğini derleyin ve dosyalar üzerinde gerçek zamanlı olarak işbirliği yapın.
ms.openlocfilehash: 8a4e3a1fc1b1d19bed093d5e72bf66e1afb2f591
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/09/2022
ms.locfileid: "65285576"
---
# <a name="integrate-microsoft-onedrive-lti-with-canvas"></a>Microsoft OneDrive LTI'yi Tuval ile tümleştirme

Bu makale, Tuval için Microsoft OneDrive LTI'yi ayarlaması gereken eğitim BT yöneticilerine yöneliktir.

Tuvalde OneDrive LTI'yi kullanma yönergeleri için bkz. [LMS'nizle Microsoft OneDrive kullanma](https://support.microsoft.com/topic/use-microsoft-onedrive-with-your-lms-c2ddeb48-f695-4267-94f2-14f7ff1b7bdd).

Microsoft OneDrive LTI'yi Tuval ile tümleştirmek iki adımlı bir işlemdir. İlk adım Canvas'da Microsoft OneDrive etkinleştirir ve ikinci adım Microsoft OneDrive LTI'yi Tuval kurslarında kullanılabilir hale getirir.

## <a name="recommended-browser-settings"></a>Önerilen tarayıcı ayarları

- Tanımlama bilgileri Microsoft OneDrive için etkinleştirilmelidir.
- Açılır pencereler Microsoft OneDrive için engellenmemelidir.

> [!NOTE]
>
> - Tanımlama bilgileri Chrome tarayıcı gizli modunda varsayılan olarak etkin değildir ve etkinleştirilmesi gerekir.
> - Microsoft OneDrive LTI, Microsoft Edge tarayıcıdaki özel modda çalışır. Tanımlama bilgilerini engellemediğinizden emin olun (varsayılan olarak etkindir).

## <a name="enable-microsoft-onedrive-lti-in-canvas"></a>Tuvalde Microsoft OneDrive LTI'yi etkinleştirme

> [!IMPORTANT]
> Bu tümleştirmeyi gerçekleştiren kişi Tuval yöneticisi ve Microsoft 365 kiracısının yöneticisi olmalıdır.

1. <a href="https://onedrivelti.microsoft.com/admin" target="_blank">Microsoft OneDrive LTI Kayıt Portalı'na oturum</a> açın
2. **Yönetici Onayı** düğmesini seçin ve izinleri kabul edin.

   > [!CAUTION]
   > Bu adım gerçekleştirilmezse, aşağıdaki adım size bir hata verir ve hatayı aldıktan sonra bu adımı bir saat boyunca gerçekleştiremezsiniz.

3. **Yeni LTI Kiracısı oluştur** düğmesini seçin. LTI Kaydı sayfasında açılan **listeden Tuval'i** seçin ve Tuval örneğinizin temel URL'sini girin.

   > [!NOTE]
   > Tuval örneğininiz ise, `https://contoso.test.instructure.com`tam URL girilmelidir.

   :::image type="content" source="media/OneDrive-LTI-07.png" alt-text="LTI tüketici platformunu ve URL metin alanını seçmek için açılan alan içeren LTI kiracı yönetimi sayfası.":::

4. **Kopyala** düğmesini (sağdaki iki sayfayı üst üste gösteren bir simge) seçerek JSON'yi kopyalayın. Bu, Tuval'de anahtarı oluşturmak için kullanılır.

   :::image type="content" source="media/OneDrive-LTI-08.png" alt-text="Görüntülenen JSON metnini kopyalayacak ve Tuval'de anahtar oluşturma için kullanılabilir hale getiren kopyala düğmesini gösteren resim.":::

5. Tuval örneğinizde yönetici olarak oturum açın ve sayfanın sol tarafındaki menüden **Geliştirici Anahtarları'nı** seçin. Açılan listeden, sayfanın sağ üst kısmındaki açılan **listedeN LTI Anahtarı'nı** seçerek bir geliştirici anahtarı oluşturun.

   :::image type="content" source="media/OneDrive-LTI-14.png" alt-text="Geliştirici Anahtarları'nın seçili olduğu sol gezinti çubuğunu ve sayfanın sağındaki açılan listeden LTI anahtarı girişini gösteren ekran görüntüsü.":::

6. Yapılandır sayfasındaki **Yöntem** açılan menüsünde, yöntem olarak **JSON Yapıştır'ı** seçin ve 4. Adımda kopyaladığınız JSON metnini görüntülenen metin alanına yapıştırın.

    > [!TIP]
    > **İsteğe Bağlı Adım:** Okulunuzun eğitimcileri, kendi kurslarının gezintisinde hangi bağlantıların görüneceğini kendileri denetlemek isterse kopyalanan JSON'da parametresini değiştirebilirsiniz ``default`` . ``default`` Parametre otomatik olarak ayarlanır``enabled``; ancak parametresini ``default`` ``disabled`` olarak değiştirmek, eğitimcilerin kendi kurslarının gezintisini seçmesine olanak tanır.
    >
    > Eğitimcilerin kurs gezinti bağlantılarını nasıl değiştirebileceği hakkında daha fazla bilgi için bkz. [Kurs Gezintisi bağlantılarını yönetmek Nasıl yaparım??](https://community.canvaslms.com/t5/Instructor-Guide/How-do-I-manage-Course-Navigation-links/ta-p/1020)

7. Anahtarı kaydettiğinizde Tuval'de **Kapalı** durumda kullanılabilir duruma gelir. Anahtarı **Açık** duruma getirin ve sonraki adımda kullanılacak **Ayrıntılar** sütununda verilen anahtarı kopyalayın.

   :::image type="content" source="media/OneDrive-LTI-19.png" alt-text="Anahtarı kapalı durumda ayarlanmış Tuval sayfası. Bu özelliğin açık olması ve anahtarın bu sayfadaki ayrıntılar sütunundan kopyalanması gerekir.":::

8. Microsoft OneDrive LTI Kayıt portalına dönün ve anahtarı **Tuval İstemci Kimliği** alanına yapıştırın. Hazır olduğunuzda **İleri'yi** seçin.

   :::image type="content" source="media/OneDrive-LTI-20.png" alt-text="Anahtarın kopyalanması gereken JSON metnini ve metin kutusunu gösteren LTI kiracı kaydı sayfası.":::

9. Değişikliklerinizi gözden geçirin ve kaydedin. Başarılı kayıtta bir ileti görüntülenir.

10. Kayıt ayrıntılarınız, giriş sayfasındaki **LTI Kiracılarını Görüntüle** düğmesi seçilerek de gözden geçirilebilir.

Gelecekteki sürümler ek yönetici onayı gerektirebilir. Bu gibi durumlarda yalnızca 1. ve 2. adımları yinelemeniz gerekir.

## <a name="enable-microsoft-onedrive-lti-in-canvas-courses"></a>Tuval Kurslarında Microsoft OneDrive LTI'yi etkinleştirme

Tuval yöneticisi tüm kurslar için Microsoft OneDrive LTI'yi etkinleştirebilir. Belirli bir kursta (tüm kurslarda değil) Microsoft OneDrive LTI gerekiyorsa, kurs eğitimcisinin kurs ayarlarında aynı adımları izlemesi gerekir.

1. Yönetici olarak oturum açın ve **Ayarlar** bölümüne gidin.
2. **Uygulamalar** bölümüne gidin ve **Uygulama Yapılandırmalarını Görüntüle** düğmesini seçin.
3. **Uygulama Ekle** düğmesini seçin.
4. **Yapılandırma Türü** açılan listesinde **İstemci Kimliğine Göre** seçeneğini belirleyin.
5. Daha önce oluşturulan geliştirici anahtarının değerini **İstemci Kimliği** alanına yapıştırın ve **Gönder** düğmesini seçin.

:::image type="content" source="media/OneDrive-LTI-31.png" alt-text="Yapılandırma türü açılan menüsünün altında İstemci kimliğine göre seçeneğini gösteren uygulama ekle sayfası.":::

## <a name="collaboration-settings-for-microsoft-onedrive-lti-in-canvas-courses"></a>Tuval kurslarında Microsoft OneDrive LTI için işbirliği Ayarlar

> [!NOTE]
> İşbirliğinin eğitimciler ve öğrenciler için çalışması için işbirliği ayarını etkinleştirmemeniz gerekir. Ayarın etkinleştirilmediğinden emin olmak için aşağıdaki adımları izleyin.

1. Yönetici olarak oturum açın ve **Ayarlar** bölümüne gidin.
1. **Özellik Seçenekleri** bölümüne ve ardından **Kurs** bölümüne gidin.
1. **Dış İşbirliği Aracı** özelliğini etkinleştirilmemiş olarak ayarlayın.

> [!NOTE]
> İşbirliği tek tek öğrencilere ve öğrenci gruplarına atanabilir. Tek tek öğrencilere atama varsayılan olarak çalışır. Öğrenci grubuna işbirliği atayabilmek için şu adımları izleyin:

1. Yönetici olarak oturum açın ve **Geliştirici Anahtarları** bölümüne gidin.
1. 170000000000710 değerine sahip anahtarı bulun ve **Açık** olarak ayarlayın.
