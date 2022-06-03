---
title: Temel Hareketlilik ve Güvenlik'i ayarlama
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- MET150
description: Bir cihazı uzaktan silme gibi eylemler gerçekleştirerek kullanıcılarınızın mobil cihazlarının güvenliğini sağlamak ve yönetmek için Basic Mobility ve Security'yi ayarlayın.
ms.openlocfilehash: 04480e59177dc9b51bc50e413715e0ad82c7f461
ms.sourcegitcommit: 1fa0b15f86470c49dddf0d6de59d553a38ae259b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65863183"
---
# <a name="set-up-basic-mobility-and-security"></a>Temel Hareketlilik ve Güvenlik'i ayarlama

Microsoft 365 için yerleşik Temel Mobilite ve Güvenlik, kullanıcıların iPhone, iPad, Android ve Windows telefonları gibi mobil cihazlarının güvenliğini sağlamanıza ve yönetmenize yardımcı olur. Cihaz güvenlik ilkeleri oluşturup yönetebilir, bir cihazı uzaktan silebilir ve ayrıntılı cihaz raporlarını görüntüleyebilirsiniz.

Sorularınız mı var? Sık sorulan soruların ele alınmasına yardımcı olacak bir SSS için bkz. [Temel Mobilite ve Güvenlik Hakkında Sık Sorulan Sorular (SSS)](frequently-asked-questions.yml). Basic Mobility ve Security'yi yönetmek için yönetici temsilcisi hesabı kullanamayacağınızı unutmayın. Daha fazla bilgi için bkz [. İş Ortakları: Temsilcili yönetim teklifi](https://support.microsoft.com/office/partners-offer-delegated-administration-26530dc0-ebba-415b-86b1-b55bc06b073e). 

Cihaz yönetimi, Güvenlik & Uyumluluk Merkezi'nin bir parçasıdır, bu nedenle Temel Mobilite ve Güvenlik kurulumuna başlamak için oraya gitmeniz gerekir.

## <a name="activate-the-basic-mobility-and-security-service"></a>Basic Mobility ve Security hizmetini etkinleştirme

1. Genel yönetici hesabınızla Microsoft 365 oturum açın.

2. [Temel Hareketliliği ve Güvenliği Etkinleştirme'ye](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx) gidin.

   Basic Mobility ve Security'yi etkinleştirmek biraz zaman alabilir. Tamamlandığında, atılması gereken sonraki adımları açıklayan bir e-posta alırsınız.

## <a name="set-up-mobile-device-management"></a>Mobil Cihaz Yönetimi ayarlama

Hizmet hazır olduğunda kurulumu tamamlamak için aşağıdaki adımları tamamlayın.

### <a name="step-1-required-configure-domains-for-basic-mobility-and-security"></a>1. Adım: (Gerekli) Temel Hareketlilik ve Güvenlik için etki alanlarını yapılandırma

Microsoft 365 ile ilişkilendirilmiş özel bir etki alanınız yoksa veya Windows cihazları yönetmiyorsanız bu bölümü atlayabilirsiniz. Aksi takdirde, DNS ana bilgisayarınızda etki alanı için DNS kayıtları eklemeniz gerekir. Kayıtları zaten eklediyseniz, etki alanınızı Microsoft 365 ayarlamanın bir parçası olarak hazırsınız demektir. Kayıtları ekledikten sonra, kuruluşunuzdaki Windows cihazında özel etki alanınızı kullanan bir e-posta adresiyle oturum açan Microsoft 365 kullanıcılar Temel Mobilite ve Güvenlik'e kaydolmak üzere yönlendirilir.

Kayıtları ayarlamayla ilgili yardıma mı ihtiyacınız var? Etki alanı kayıt şirketinizi bulun ve [etki alanınıza bağlanmak için DNS kayıtları ekleme](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) bölümünde sağlanan listede DNS kaydı oluşturmak için adım adım yardıma gitmek için kayıt şirketi adını seçin. Azure AD Premium [olmadan kaydı basitleştirme Windows](/mem/intune/enrollment/windows-enroll#simplify-windows-enrollment-without-azure-ad-premium) bölümünde açıklanan CNAME kayıtlarını oluşturmak için bu yönergeleri kullanın.

İki CNAME kaydını ekledikten sonra Güvenlik & Uyumluluk Merkezi'ne dönün ve sonraki adımı tamamlamak için **Veri kaybı önleme** > **Cihaz yönetimi'ne** gidin.

### <a name="step-2-required-configure-an-apns-certificate-for-ios-devices"></a>2. Adım: (Gerekli) iOS cihazlar için APNs Sertifikası yapılandırma

iPad ve iPhone gibi iOS cihazları yönetmek için bir APNs sertifikası oluşturmanız gerekir.

1. Genel yönetici hesabınızla Microsoft 365 oturum açın.

2. [Microsoft 365 yönetim merkezi](https://portal.office.com/adminportal/home?#/MifoDevices) gidin ve **iOS için APNs Sertifikası'nı** seçin.

4. Apple Anında İletme Bildirimi Sertifikası Ayarlar sayfasında **İleri'yi** seçin.

5. **CSR dosyanızı indirin'i** seçin ve Sertifika imzalama isteğini bilgisayarınızda anımsayacağınız bir yere kaydedin. **İleri**'yi seçin.

6. APNs sertifikası oluştur sayfasında:

   - Apple Anında İletme Sertifikaları Portalı'nı açmak için Apple APNS Portalı'nı seçin.
   - Apple Kimliği ile oturum açın.

     > [!IMPORTANT]
     > Hesabı yöneten kullanıcı ayrılsa bile kuruluşunuzda kalacak bir e-posta hesabıyla ilişkilendirilmiş bir şirket Apple Kimliği kullanın. Sertifikayı yenileme zamanı geldiğinde aynı kimliği kullanmanız gerektiğinden bu kimliği kaydedin.

   - Sertifika Oluştur'u seçin ve Kullanım Koşulları'nı kabul edin.
   - Microsoft 365'dan bilgisayarınıza indirdiğiniz Sertifika imzalama isteğine göz atın ve Yükle'yi seçin.
   - Apple Anında İletme Sertifikası Portalı tarafından oluşturulan APN sertifikasını bilgisayarınıza indirin.

     > [!TIP]
     > Sertifikayı indirirken sorun yaşıyorsanız tarayıcınızı yenileyin.

7. Microsoft 365 Geri dön ve **İleri'yi** seçin.

8. Apple Anında İletme Sertifikaları Portalı'ndan indirdiğiniz APN sertifikasına göz atın.

9. **Bitir'i** seçin.

### <a name="step-3-recommended-set-up-multi-factor-authentication"></a>3. Adım: (Önerilen) Çok faktörlü kimlik doğrulamasını ayarlama

MFA, ikinci bir kimlik doğrulama biçimi gerektirerek mobil cihaz kaydı için Microsoft 365 oturum açmanın güvenliğini sağlar. Kullanıcıların iş hesabı parolalarını doğru girdikten sonra mobil cihazlarında bir telefon araması, kısa mesaj veya uygulama bildirimini kabul etmeleri gerekir. Cihazlarını ancak bu ikinci kimlik doğrulama biçimi tamamlandıktan sonra kaydedebilirler. Kullanıcı cihazları Basic Mobility ve Security'ye kaydolduktan sonra, kullanıcılar Microsoft 365 kaynaklarına yalnızca iş hesaplarıyla erişebilir.

Azure AD portalında MFA'yı açmayı öğrenmek için bkz. [Çok faktörlü kimlik doğrulamasını ayarlama](../security-and-compliance/set-up-multi-factor-authentication.md).

MFA'yı ayarladıktan sonra Güvenlik & Uyumluluk Merkezi'ne dönün ve sonraki adımı tamamlamak için **Veri kaybı önleme** > **Cihaz yönetimi** > **Cihaz ilkeleri'ne** gidin.

### <a name="step-4-recommended-manage-device-security-policies"></a>4. Adım: (Önerilen) Cihaz güvenlik ilkelerini yönetme

Sonraki adım, Microsoft 365 kuruluş verilerinizi korumaya yardımcı olmak için cihaz güvenlik ilkeleri oluşturmak ve dağıtmaktır. Örneğin, beş dakikalık işlem yapılmadığında cihazları kilitlemek ve üç oturum açma hatasından sonra cihazları silmek için bir ilke oluşturarak bir kullanıcı cihazını kaybederse veri kaybını önlemeye yardımcı olabilirsiniz.

1. Genel yönetici hesabınızla Microsoft 365 oturum açın.

2. [Mobil Cihaz Yönetimi Etkinleştir'i](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx) seçin. Hizmet etkinleştirilirse, etkinleştirme adımları yerine [Cihazları Yönet](https://admin.microsoft.com/adminportal/home#/MifoDevices) bağlantısını görürsünüz.

3. **Cihaz ilkeleri'ne** gidin.

   :::image type="content" source="../../media/basic-mobility-security/basic-mobility-microsoft-purview.png" alt-text="Temel Güvenlik ve Hareketlilik ilkesi ayarları.":::

4. [Temel Mobilite ve Güvenlik'te cihaz güvenlik ilkeleri oluşturma](create-device-security-policies.md) bölümündeki adımları izleyerek kuruluşunuza uygun cihaz güvenlik ilkeleri oluşturun ve dağıtın.

> [!TIP]
>
> - Yeni bir ilke oluşturduğunuzda, kullanıcı cihazının ilkeyle uyumlu olmadığı durumlarda erişime izin vermek ve ilke ihlalini bildirmek için ilkeyi ayarlamak isteyebilirsiniz. Bu, Microsoft 365 erişimi engellemeden ilkeden kaç mobil cihazın etkilendiğini görmenizi sağlar.
>
> - Kuruluşunuzdaki herkese yeni bir ilke dağıtmadan önce, bunu az sayıda kullanıcı tarafından kullanılan cihazlarda test etmenizi öneririz.
>
> - Ayrıca, ilkeleri dağıtmadan önce kuruluşunuza bir cihazı Temel Mobilite ve Güvenlik'e kaydetmenin olası etkilerini bildirin. İlkeleri nasıl ayarladığınıza bağlı olarak, ilkelerle uyumlu olmayan cihazların (uyumlu olmayan cihazlar) Microsoft 365 erişmesi engellenebilir. Uyumlu olmayan cihazlarda, kayıtlı bir cihazda cihaz silinirse silinebilecek uygulamalar, fotoğraflar ve diğer kişisel bilgiler de yüklü olabilir. Daha fazla bilgi için bkz [. Basic Mobility and Security'de mobil cihazı temizleme](wipe-mobile-device.md).

## <a name="make-sure-users-enroll-their-devices"></a>Kullanıcıların cihazlarını kaydettiklerinden emin olun

Bir mobil cihaz yönetimi ilkesi oluşturup dağıttıktan sonra, kuruluşunuzdaki cihaz ilkesinin uyguladığı lisanslı Microsoft 365 her kullanıcı, mobil cihazından Microsoft 365 bir sonraki oturum açışında bir kayıt iletisi alır. Microsoft 365 e-posta ve belgelere erişebilmeleri için önce kayıt ve etkinleştirme adımlarını tamamlamaları gerekir. Daha fazla bilgi için bkz. [Mobil cihazınızı Temel Hareketlilik ve Güvenlik kullanarak kaydettirin](enroll-your-mobile-device.md).

> [!IMPORTANT]
> Kullanıcının tercih ettiği dil kayıt işlemi tarafından desteklenmiyorsa, kullanıcılar mobil cihazlarında kayıt bildirimi ve adımları başka bir dilde alabilir. Microsoft 365'de desteklenen tüm diller şu anda mobil cihazlarda kayıt işlemi için desteklenmemektedir.

Android veya iOS cihazları olan kullanıcıların kayıt işleminin bir parçası olarak Şirket Portalı uygulamasını yüklemesi gerekir.

## <a name="related-content"></a>İlgili içerik

[Temel Hareketlilik ve Güvenlik Özellikleri](capabilities.md) (makale)\
[Temel Mobilite ve Güvenlik'te cihaz güvenlik ilkeleri oluşturma](create-device-security-policies.md) (makale)
