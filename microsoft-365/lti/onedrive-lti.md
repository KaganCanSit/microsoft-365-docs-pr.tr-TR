---
title: Birlikte Microsoft OneDrive Learning Birlikte Çalışabilirlik Araçlarını Kullanma
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
description: Yeni Birlikte Çalışma Araçları Birlikte Çalışma Uygulaması ile ödev oluşturun ve not edin, ders içeriğini oluşturun ve sergiyi oluşturun, dosyalar üzerinde gerçek Microsoft OneDrive Learning işbirliği yapın.
ms.openlocfilehash: 68622305e6a277b44538d4a05ee42a6b680749f3
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021675"
---
# <a name="integrate-microsoft-onedrive-lti-with-canvas"></a>LTI'Microsoft OneDrive Canvas ile tümleştirin

LTI Microsoft OneDrive Canvas ile tümleştirme, iki adımlı bir işlemdir. İlk adım Canvas'da Microsoft OneDrive ve ikinci adım da Canvas kurslarının Microsoft OneDrive olarak kullanılabilir.

## <a name="recommended-browser-settings"></a>Önerilen tarayıcı ayarları

- Tanımlama bilgileri, tanımlama bilgileri Microsoft OneDrive.
- Açılan pencerelerin bir yıl için engellenmiş Microsoft OneDrive.

> [!NOTE]
> - Tanımlama bilgileri Chrome tarayıcı incognito modunda varsayılan olarak etkin değildir ve bunun etkinleştirilmesi gerekir.
> - Microsoft OneDrive LTI, tarayıcıda özel modda Microsoft Edge çalışır. Tanımlama bilgilerini engellemediyseniz (varsayılan olarak etkindir) emin olun.

## <a name="enable-microsoft-onedrive-lti-in-canvas"></a>Canvas'Microsoft OneDrive LTI'yi etkinleştirme

> [!IMPORTANT]
> Bu tümleştirmeyi gerçekleştiren kişi Canvas yöneticisi ve kullanıcı kiracısı yöneticisi Microsoft 365 gerekir.

1. <a href="https://onedrivelti.microsoft.com/admin" target="_blank">LTI Kayıt Microsoft OneDrive oturum açma</a>
1. Yönetici Onayı **düğmesini seçin** ve izinleri kabul edin.

> [!CAUTION]
> Bu adım gerçekleştirile değilse, aşağıdaki adım size bir hata verir ve hatayı alırsanız bu adımı bir saat süreyle aşamazsınız.

3. Yeni **LTI Kiracısı Oluştur düğmesini** seçin. LTI Kayıt sayfasında açılan listeden **Tuval'i** seçin ve Canvas örneğinizin temel URL'sini girin.

> [!NOTE]
> Canvas örneğiniz , örneğin https://contoso.test.instructure.com]()https://contoso.test.instructure.com) ise, URL'nin tamamı girilir.

:::image type="content" source="media/OneDrive-LTI-07.png" alt-text="LTI tüketici platformu ve URL metin alanını seçmek için açılan alanla birlikte LTI kiracı yönetim sayfası.":::

4. Kopyala düğmesini (sağ üst kısmında iki sayfayı gösteren bir simge) seçerek JSON'u kopyalayın. Bu, Canvas'da anahtarı oluşturmak için kullanılır.

:::image type="content" source="media/OneDrive-LTI-08.png" alt-text="Görüntülenen JSON metnini kopyalayıp anahtar nesil Canvas'da görüntülenebilir hale gelecek kopyala düğmesini gösteren resim.":::

5. Canvas örneğinize yönetici olarak oturum açın ve **sayfanın sol** tarafındaki menüden Geliştirici Anahtarları'ı seçin. Açılan sayfada, sayfanın sağ üst köşesindeki açılan **listesinden LTI** Anahtarı'nın seçerek bir geliştirici anahtarı oluşturun.

:::image type="content" source="media/OneDrive-LTI-14.png" alt-text="Geliştirici Tuşları'nın seçili olduğu sol gezinti çubuğunu ve sayfanın sağında açılan bir açılan listesinden LTI tuşu girdisini gösteren ekran görüntüsü.":::

6. Yapılandır sayfasında, Yöntem açılan listesinde yöntem  olarak JSON Yapıştır'ı seçin ve 4. Adımda kopyalayıp görüntülenen metin alanına **JSON** metnini yapıştırın.

    > [!TIP]
    > **İsteğe Bağlı Adım:** Okullu eğitimciler kendi kendilerine ders gezintilerinde hangi bağlantıların görüntü olduğunu kontrol etmek isterseniz, ``default`` kopyalanan JSON'da parametreyi değiştirebilirsiniz. Parametre ``default`` otomatik olarak ayarlanır ``enabled`` ; öte yandan, parametrenin ``default`` ``disabled`` değiştirilmesi eğitimcilerin kendi derslerini gezintisini seçmelerine olanak sağlar.
    >
    > Eğitimciler kendi ders gezinti bağlantılarını nasıl değiştir olduğu hakkında daha fazla bilgi için Bkz. Kurs [Gezintisi bağlantılarını nasıl yönetirim?](https://community.canvaslms.com/t5/Instructor-Guide/How-do-I-manage-Course-Navigation-links/ta-p/1020)

7. Anahtarı kaydedin; Canvas'da Kapalı durumda **kullanılabilir duruma** gelir. Anahtarı Açık **olarak seçin** ve bir sonraki adımda **kullanılacak Ayrıntılar** sütununda verilen anahtarı kopyalayın.

:::image type="content" source="media/OneDrive-LTI-19.png" alt-text="Anahtar kapalı durumda ayarlanmış olarak Canvas sayfası. Anahtarın açık olması ve anahtarın bu sayfanın ayrıntılar sütunundan kopyalanmış olması gerekir.":::

8. LTI Kayıt Microsoft OneDrive dönmek ve anahtarı **Canvas Client ID alanına** yapıştırın. Hazır **olduğunda** , Sonraki'yi seçin.

:::image type="content" source="media/OneDrive-LTI-20.png" alt-text="JSON metninin ve anahtarın kopyalanan metin kutusunun olduğu LTI kiracı kayıt sayfası.":::

9. Değişikliklerinizi gözden geçirin ve kaydedin. Başarılı kayıtta bir ileti görüntülenir.
10. Kayıt ayrıntılarınız, giriş sayfasında **LTI** Kiracıları Görüntüle düğmesi seçerek de inceleyebilirsiniz.

## <a name="enable-microsoft-onedrive-lti-in-canvas-courses"></a>Canvas Microsoft OneDrive'da LTI'yi etkinleştirme

Canvas yöneticisi LTI'Microsoft OneDrive tüm kurslar için bu özelliği etkinleştir olabilir. Belirli Microsoft OneDrive bir kursta LTI gerekirse (tüm kurslar için değil), eğitimcinin kurs ayarları içindeki aynı adımları izlemesi gerekir.

1. Yönetici olarak oturum açın ve **Yönetici Ayarlar gidin**.
2. Uygulamalar bölümüne **gidin ve** Uygulama Yapılandırmalarını **Görüntüle düğmesini** seçin.
3. Uygulama **Ekle düğmesini** seçin.
4. Yapılandırma **Türü açılan** listesinde İstemci Kimliğine **Göre seçeneğini** belirtin.
5. Daha önce oluşturulan geliştirici anahtarının değerini İstemci Kimliği **alanına yapıştırın** ve Gönder **düğmesini** seçin.

:::image type="content" source="media/OneDrive-LTI-31.png" alt-text="Yapılandırma türü açılan menüsünün altındaki İstemci Kimliğine Göre seçeneğini gösteren uygulama ekle sayfası.":::

## <a name="collaboration-settings-for-microsoft-onedrive-lti-in-canvas-courses"></a>Canvas Ayarlar'da Microsoft OneDrive için LTI işbirliği çalışma

> [!NOTE]
> İşbirliğinin eğitimcilere ve öğrencilere yönelik çalışması için işbirliği ayarını etkinleştirmeniz gerekir. Ayarın etkinleştirilmemiş olduğundan emin olmak için aşağıdaki adımları izleyin.

1. Yönetici olarak oturum açma ve **Yönetici Ayarlar gidin**.
1. Özellik **Seçenekleri bölümüne** gidin ve ardından Kurs **bölümüne** gidin.
1. Dış İşbirliği **Aracı özelliğini etkinleştirilmemiş** olarak ayarlayın.

> [!NOTE]
> İşbirliği tek tek öğrencilere ve öğrenci gruplarına atanabilir. Tek tek öğrencilere atama varsayılan olarak çalışır. Öğrenci grubuna işbirliğini atay olmak için şu adımları izleyin:

1. Yönetici olarak oturum açma ve Geliştirici **Anahtarları bölümüne** gidin.
1. Değeri yüksek olan anahtarı 170000000000710 olarak **ayarlayın**.
