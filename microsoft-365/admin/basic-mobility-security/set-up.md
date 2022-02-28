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
description: Bir cihazı uzaktan silen gibi eylemler gerçekleştirerek kullanıcılarının mobil cihazlarını güvenlik altına almak ve yönetmek için Temel Mobil Kullanım ve Güvenlik'i ayarlayın.
ms.openlocfilehash: bbf7cf84dd996a0e548a76978e8fbba58f40c070
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983995"
---
# <a name="set-up-basic-mobility-and-security"></a>Temel Hareketlilik ve Güvenlik'i ayarlama

Microsoft 365 için yerleşik Temel Mobil Kullanım ve Güvenlik, kullanıcıların iPhone, iPad, Android ve telefon gibi mobil cihazlarını güvenlik altına alır ve Windows olur. Cihaz güvenlik ilkelerini oluşturabilir ve yönetebilir, cihazı uzaktan temizleyebilirsiniz ve ayrıntılı cihaz raporlarını görüntüleyebilirsiniz.

Sorularınız mı var? Sık sorulan sorulara yardımcı olacak SSS'ler için bkz. [Temel Hareketlilik ve Güvenlik Hakkında Sık Sorulan Sorular (SSS)](frequently-asked-questions.yml). Temel Hareketlilik ve Güvenlik'i yönetmek için yönetici temsilcisi hesabı kullanamayabilirsiniz. Daha fazla bilgi için bkz. [İş Ortakları: Temsili yönetim teklif edin](https://support.microsoft.com/office/partners-offer-delegated-administration-26530dc0-ebba-415b-86b1-b55bc06b073e). 

Cihaz yönetimi, Güvenlik ve & Merkezi'nin bir bölümü olduğu için Temel Mobil Kullanım ve Güvenlik kurulumunun başlatın.

## <a name="activate-the-basic-mobility-and-security-service"></a>Temel Hareketlilik ve Güvenlik hizmetini etkinleştirme

1. Genel yönetici hesabınızla Microsoft 365 oturum açın.

2. Temel Mobil Kullanım [ve Güvenlik'i Etkinleştirme'ye gidin](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx).

   Temel Hareketlilik ve Güvenlik'i etkinleştirmek biraz zaman alıyor. E-postanız tamam olduğunda, sonraki adımları açıklayan bir e-posta alırsınız.

## <a name="set-up-mobile-device-management"></a>Mobil Cihaz Yönetimi'i ayarlama

Hizmet hazır olduğunda, kurulumu bitirmek için aşağıdaki adımları tamamlayın.

### <a name="step-1-required-configure-domains-for-basic-mobility-and-security"></a>1. Adım: (Gerekli) Temel Hareketlilik ve Güvenlik için etki alanlarını yapılandırma

Microsoft 365 ile ilişkilendirilmiş özel bir etki alanınız yoksa veya Windows yönet noktada değilsanız, bu bölümü atlayabilirsiniz. Aksi takdirde, DNS ana dınıza etki alanı için DNS kayıtlarını eklemeniz gerekir. Kayıtları zaten eklediyseniz, etki alanınızı bu kayıtla ayarlamanın Microsoft 365, hazır olursanız. Kayıtları ekledikten sonra, Microsoft 365 etki alanınızı kullanan bir e-posta adresiyle Windows cihazlarında oturum alan tüm kullanıcılar, Basic Mobility ve Security'ye kaydolmaları için yeniden yönlendirildi.

Kayıtları ayarlamayla ilgili yardıma mı ihtiyacınız var? Etki alanı kayıt şirketinizi bulun ve etki alanınıza bağlanmak için DNS kayıtları ekleme altında sağlanan listede DNS kaydını oluşturmak için adım adım yardıma gitmek için etki alanı kayıt şirketi  [adını seçin](/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider). Bu yönergeleri kullanarak, CNAME kaydı oluşturmadan CNAME [Windows basitleştirme konusunda Azure AD Premium](/mem/intune/enrollment/windows-enroll#simplify-windows-enrollment-without-azure-ad-premium).

İki CNAME kaydından sonra, Güvenlik ve Uyumluluk Merkezi'ne &  >  sonraki adımı tamamlamak için Veri kaybı **önlemeDevice yönetimi'ne**  gidin.

### <a name="step-2-required-configure-an-apns-certificate-for-ios-devices"></a>2. Adım: (Gerekli) iOS cihazları için APNs Sertifikası yapılandırma

iPhone ve iPad iOS cihazlarını yönetmek için APNs sertifikası oluşturmanız gerekir.

1. Genel yönetici hesabınızla Microsoft 365 oturum açın.

2. Tarayıcı türüne: yazın [https://protection.office.com](https://protection.office.com/).

3. Veri  **kaybı önlemeSağlama** >  **yönetimi'ne** ve **iOS cihazları için APNs Sertifikası'nın seçeneğini seçin**.

4. Apple Anında Bildirim Sertifikası Bildirim Ayarlar  **Ekle'yi seçin**.

5.  **SELECTSR dosyanızı yükleyin**  ve Sertifika imzalama isteğini bilgisayarınızda anımsayacak bir yere kaydedin.  **SelectNext**.

6. APNs sertifikası oluştur sayfasında:

   - Apple Push Sertifikaları Portalı'nı açmak için Apple APNS Portalı'ı seçin.
   - Apple ID ile oturum açma.

     > [!IMPORTANT]
     > Hesabı yöneten kullanıcı ayrılsa bile, kuruluşta kalacak bir e-posta hesabıyla ilişkilendirilmiş şirket Apple kimliği kullanın. Sertifikayı yenileme zamanı geldiğinde aynı kimliği kullanmak zorunda olduğunuz için bu kimliği kaydedin.

   - Sertifika Oluştur'a seçin ve Kullanım Koşullarını kabul et.'i seçin.
   - Dosyadan bilgisayarınıza indirdiğiniz Sertifika imzalama isteğine göz Microsoft 365'yi seçin.
   - Apple Push Sertifika Portalı tarafından oluşturulan APN sertifikasını bilgisayarınıza indirin.

     > [!TIP]
     > Sertifikayı indirmede sorun ediyorsanız, tarayıcınızı yenileyin.

7. Seçeneklere geri dönüp Microsoft 365'ı **seçin**.

8. Apple Push Sertifikaları Portalı'dan indirdiğiniz APN sertifikasına göz atabilirsiniz.

9.   **Tamamla'ya seçin**.

### <a name="step-3-recommended-set-up-multi-factor-authentication"></a>3. Adım: (Önerilen) Çok faktörlü kimlik doğrulamasını ayarlama

MFA, ikinci bir kimlik doğrulama biçimi Microsoft 365 mobil cihaz kaydı için mobil cihaz kaydında oturum açma işleminin güvenliğini sağlar. Kullanıcıların, iş hesabı parolalarını doğru girdikten sonra mobil cihazlarında bir telefon aramasını, kısa mesajı veya uygulama bildirimini kabulleri gerekir. Ancak bu ikinci kimlik doğrulama işlemi tamamlandıktan sonra cihazlarını kaydedebilirsiniz. Kullanıcı cihazları Temel Hareketlilik ve Güvenlik'e kaydettikten sonra, Microsoft 365 kendi iş hesaplarıyla mobil kaynaklara erişebilirsiniz.

Azure AD portalında MFA'nın nasıl açılamaz olduğunu öğrenmek için bkz [. Multi-Factor Authentication'i açma](../security-and-compliance/set-up-multi-factor-authentication.md).

MFA'nın ayarlaması yapıldıktan sonra, Güvenlik & Merkezi'ne gidin  **veData kaybı** >  **önlemeDevice yönetimiDevice** >  **ilkeleri'ne**  gidip bir sonraki adımı tamamlamanız gerekir.

### <a name="step-4-recommended-manage-device-security-policies"></a>4. Adım: (Önerilen) Cihaz güvenliği ilkelerini yönetme

Sonraki adım, cihaz güvenliği ilkelerini oluşturmak ve dağıtarak kullanıcı ve kuruluş verilerinizin korunmasına Microsoft 365 olmaktır. Örneğin, bir kullanıcı beş dakika boyunca etkileşimde değilken cihazları kilitleyen ve üç oturum açma hatasının ardından cihazları temizleyen bir ilke oluşturarak, cihazlarını kaybettiğinde veri kaybını önlemeye yardımcı olabilirsiniz.

1. Genel yönetici hesabınızla Microsoft 365 oturum açın.

2. Mobil  [Cihaz Yönetimini Etkinleştir'i seçin](https://admin.microsoft.com/EAdmin/Device/IntuneInventory.aspx). Hizmet etkinleştirilirse, etkinleştirme adımları yerine CihazlarıYıldız  [bağlantısına ulaşabilirsiniz](https://admin.microsoft.com/adminportal/home#/MifoDevices) .

3. Device  **ilkeleri'ne gidin**.

   :::image type="content" source="../../media/basic-mobility-security/bms-4-policy.png" alt-text="Temel Güvenlik ve Mobil Kullanım ilkesi ayarları.":::

4. Temel Mobil Kullanım ve Güvenlik'te cihaz güvenliği ilkeleri oluşturma'daki adımları takip edin ve bu ilkeleri organizasyonunıza  [uygun şekilde dağıtın](create-device-security-policies.md).

> [!TIP]
>
> - Yeni ilke yken, erişime izin vermek ve kullanıcı cihazı ilkeyle uyumlu olmayan ilke ihlallerini bildirmeye izin vermek için ilkeyi ayarlamak istiyor olabilirsiniz. Bu, mobil cihazların erişimini engellemeden kaç mobil cihazı ilkeden etkilemektedir Microsoft 365.
>
> - Yeni bir ilkeyi kuruluşta yer alan herkese dağıtmadan önce, az sayıda kullanıcının kullandığı cihazlar üzerinde ilkeyi test edin.
>
> - Ayrıca ilkeleri dağıtmadan önce, Temel Mobil kullanım ve Güvenlik'e cihaz kaydetmenin olası etkilerini organizasyonunıza haber verirsiniz. İlkeleri nasıl ayar kullandığınıza bağlı olarak, ilkelerle uyumlu olmayan cihazlar (uyumlu olmayan cihazlar) bu cihazlara erişimi Microsoft 365. Uyumlu olmayan cihazlarda ayrıca yüklü uygulamalar, fotoğraflar ve diğer kişisel bilgiler olabilir ve bu bilgiler kayıtlı bir cihazda temizlenmişse silinebilir. Daha fazla bilgi için bkz [. Temel Mobil Kullanım ve Güvenlik'te mobil cihazı temizleme](wipe-mobile-device.md).

## <a name="make-sure-users-enroll-their-devices"></a>Kullanıcıların cihazlarını kaydettiklerinden emin olun

Mobil cihaz yönetim ilkesi oluşturduktan ve dağıtıldıktan sonra, aygıtınızda cihaz ilkesi uygulandığı her lisanslı Microsoft 365 kullanıcısı, mobil cihazlarından Microsoft 365'da bir sonraki oturum açmalarında bir kayıt iletisi alır. E-posta ve belgelerine erişemeden önce kayıt ve Microsoft 365 adımlarını tamamlamaları gerekir. Daha fazla bilgi için bkz [. Temel Mobil Kullanım ve Güvenlik kullanarak mobil cihazınızı kaydetme](enroll-your-mobile-device.md).

> [!IMPORTANT]
> Kullanıcının tercih ettiği dil kayıt sürecinde desteklenmiyorsa, kullanıcılar mobil cihazlarında farklı bir dilde kayıt bildirimi ve adımları alsalar bile. Microsoft 365'de desteklenen dillerin hepsi, şu anda mobil cihazlardaki kayıt işlemi için desteklemektedir.

Android veya iOS cihazları olan kullanıcıların, kayıt işlemi Şirket Portalı bir parçası olarak Şirket Portalı uygulamasını yüklemeleri gerekir.

## <a name="related-content"></a>İlgili içerik

[Temel Hareketlilik ve Güvenlik Özellikleri](capabilities.md) (makale)\
[Temel Hareketlilik ve Güvenlik makalesinde cihaz güvenliği](create-device-security-policies.md) ilkeleri oluşturma (makale)