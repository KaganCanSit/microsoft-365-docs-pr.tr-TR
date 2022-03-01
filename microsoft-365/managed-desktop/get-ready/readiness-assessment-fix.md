---
title: Hazırlık değerlendirme aracı tarafından bulunan sorunları düzeltme
description: Aracın bulduğu her sorun için ayrıntılı işlemler
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: badf2d65f2b29e265a1312cb1d5f4802a44f3cb3
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011953"
---
# <a name="fix-issues-found-by-the-readiness-assessment-tool"></a>Hazırlık değerlendirme aracı tarafından bulunan sorunları düzeltme

Her denetimde, araç dört olası sonuçdan birini bildirecek:

| Sonuç  | Anlamı |
| ----- | ----- |
| Hazır | Kaydı tamamlamadan önce herhangi bir işlem gerekmez. |
| Danışma | Kayıt ve kullanıcılar için en iyi deneyimi yaşamak için araç adımlarını veya bu makaleyi izleyin. <br><br> Kaydı *tamamabilirsiniz* , ancak ilk cihazınızı dağıtmadan önce bu sorunları çözmeniz gerekir. |
| Hazır değil | **Bu sorunları çözesiniz kayıt başarısız olur.** <br><br> Bunları çözmek için araçta veya bu makaledeki adımları izleyin. |
| Error | Kullanmak Azure Active Directory ad) rolü bu denetimi çalıştırmak için yeterli izinlere sahip değil. |

> [!NOTE]
> Bu araç tarafından bildirilen sonuçlar, ayarlarınızın durumunu yalnızca aracı son kez aramanız zamanında gösterir. Daha sonra E-Microsoft Intune, Azure Active Directory veya Microsoft 365 ilkelerde değişiklik olursa, "Hazır" olan öğeler "Hazır değil" olabilir. Microsoft Yönetilen Masaüstü işlemleriyle ilgili sorunları önlemek için, ilkeleri değiştirmeden önce bu makalede açıklanan belirli ayarlara bakın.

## <a name="microsoft-intune-settings"></a>Microsoft Intune ayarları

Intune ayarlarına, yönetim Microsoft Endpoint Manager [erişebilirsiniz](https://endpoint.microsoft.com).

### <a name="autopilot-deployment-profile"></a>AutoPilot dağıtım profili

Microsoft Yönetilen Masaüstü cihazlarıyla atanmış veya dinamik grupları hedef alan mevcut AutoPilot profilleriniz olmaması gerekir. Microsoft Yönetilen Masaüstü, yeni cihazları yapılandırmak için AutoPilot'u kullanır. Mevcut bir AutoPilot dağıtım profiliniz varsa, Microsoft Yönetilen Masaüstü AutoPilot hazırlık testinin başarılı olması için Tüm hedefli cihazları **Autopilot'a** dönüştür ayarının Hayır olarak ayarlanmış olması gerekir.

| Sonuç  | Anlamı |
| ----- | ----- |
| Hazır değil | Tüm cihazlara atanmış bir AutoPilot profiliniz var. <br><br> Daha fazla bilgi için bkz[. AutoPilot Windows kullanarak Intune'da Windows.](/mem/autopilot/enrollment-autopilot) Microsoft Yönetilen Masaüstü kaydı'nın ardından AutoPilot ilkenizi Modern Çalışma Alanı Cihazları - Tüm Azure AD **grubunu dışarıda bırakacak** şekilde ayarlayın.
| Danışma | AutoPilot profillerinizi Microsoft Yönetilen Masaüstü cihazları dahil değil, atanmış veya dinamik Azure AD grubunun hedef olduğundan emin olun. <br><br> Daha fazla bilgi için bkz[. AutoPilot Windows kullanarak Intune'da Windows.](/mem/autopilot/enrollment-autopilot) Microsoft Yönetilen Masaüstü kaydı sonrasında AutoPilot profillerinizi Modern Çalışma Alanı Cihazları - Tüm Azure AD **grubunu dışarıda bırakacak** şekilde ayarlayın. |

### <a name="certificate-connectors"></a>Sertifika bağlayıcıları

Microsoft Yönetilen Masaüstü'ne kaydetmek istediğiniz cihazlar tarafından kullanılacak sertifika bağlayıcınız varsa, bağlayıcıların hiçbir hatası olmaması gerekir. Aşağıdaki tavsiyelerden yalnızca biri sizin durumunuz için geçerli olacaktır, bu nedenle dikkatle kontrol edin.

| Sonuç  | Anlamı |
| ----- | ----- |
| Danışma | Sertifika bağlayıcısı yoktur. Herhangi bir bağlayıcıya ihtiyacınız yok olabilir, ancak Microsoft Yönetilen Masaüstü cihazlarınız üzerinde ağ bağlantısı için bir bağlayıcıya ihtiyaç olup olmadığını değerlendirmeniz gerekir. <br><br> Daha fazla bilgi için bkz [. Microsoft Yönetilen Masaüstü için sertifikaları ve ağ profillerini hazırlama](certs-wifi-lan.md). |
| Danışma | En az bir sertifika bağlayıcısı hatayla karşılaştı. Microsoft Yönetilen Masaüstü cihazlarına sertifika sağlamak için bu bağlayıcıya ihtiyacınız varsa, hatayı çözmeniz gerekir. <br><br> Daha fazla bilgi için bkz [. Microsoft Yönetilen Masaüstü için sertifikaları ve ağ profillerini hazırlama](certs-wifi-lan.md). |
| Danışma | En az bir sertifika bağlayıcınız var ve herhangi bir hata bildiriliyor. Ancak dağıtım hazırlığında, Microsoft Yönetilen Masaüstü cihazları için bağlayıcıyı yeniden kullanmak üzere bir profil oluşturmanız gerekir. <br><br> Daha fazla bilgi için bkz [. Microsoft Yönetilen Masaüstü için sertifikaları ve ağ profillerini hazırlama](certs-wifi-lan.md). |

### <a name="company-portal"></a>Şirket Portalı

Microsoft Yönetilen Masaüstü için, IT yöneticilerinin Microsoft Intune Şirket Portalı cihazları olan kullanıcıları için yönetici yüklemesi gerekir.

| Sonuç  | Anlamı |
| ----- | ----- |
| Hazır değil | Kullanıcılarınız için Şirket Portalı yüklememişsiniz. Satın Şirket Portalı ve Intune ile eşitlemeyi zorlar İş İçin Microsoft Store. <br><br> Daha fazla bilgi için bkz[. Intune Şirket Portalı yükleme](../get-started/company-portal.md).

### <a name="conditional-access-policies"></a>Koşullu erişim ilkeleri

Koşullu erişim ilkeleri Microsoft'un Yönetilen Masaüstü'nüz tarafından Intune ve Azure AD'de Azure AD organizasyonlarınızı (kiracı) yönetmesini engelleyebilirsiniz.

| Sonuç  | Anlamı |
| ----- | ----- |
| Hazır değil | Tüm kullanıcıları hedef alan en az bir koşullu erişim ilkeniz vardır. <br><br> Kayıt sırasında, Microsoft Yönetilen Masaüstü hizmeti hesaplarını ilgili koşullu erişim ilkelerinin dışında tutacağız ve bu hesaplara erişimi kısıtlamak için yeni koşullu erişim ilkeleri uygulamamız gerekir. <br><br> Kayıt sonrasında, Microsoft Yönetilen Masaüstü koşullu erişim Microsoft Endpoint Manager. Bu hizmet hesapları hakkında daha fazla bilgi için bkz. [Standart işletim yordamları](../service-description/operations-and-monitoring.md#standard-operating-procedures). |
| Danışma | Microsoft Yönetilen Masaüstü'nin Microsoft Yönetilen Masaüstü hizmetini yönetmesini engelleyen koşullu erişim ilkeleriniz var. <br><br> Kayıt sırasında, Microsoft Yönetilen Masaüstü hizmeti hesaplarını ilgili koşullu erişim ilkelerinin dışında tutacağız ve bu hesaplara erişimi kısıtlamak için yeni koşullu erişim ilkeleri uygulamamız gerekir. <br><br> Bu hizmet hesapları hakkında daha fazla bilgi için bkz. [Standart işletim yordamları](../service-description/operations-and-monitoring.md#standard-operating-procedures). |
| Error | Intune Yönetici rolü, bu denetim için yeterli izinlere sahip değildir. Bu denetimi çalıştırmak için ayrıca şu Azure AD rollerinin atanmış olduğu da gerekir: <ul><li>Güvenlik Okuyucu</li><li>Güvenlik Yöneticisi</li><li>Koşullu Erişim Yöneticisi</li><li>Genel Okuyucu</li><li>Cihaz Yöneticisi</li></ul>
### <a name="device-compliance-policies"></a>Cihaz Uyumluluğu ilkeleri

Azure AD'nizin Intune Cihaz Uyumluluğu ilkeleri Microsoft Tarafından Yönetilen Masaüstü cihazlarını etkileyebilir.

| Sonuç  | Anlamı |
| ----- | ----- |
| Danışma | Tüm kullanıcıları kullanan en az bir uyumluluk ilkeye sahipsiniz. Microsoft Yönetilen Masaüstü, Microsoft Yönetilen Masaüstü cihazlarınıza uygulanacak uyumluluk ilkelerini de içerir. Çakışmalar olduğundan emin olmak için, kuruluş tarafından oluşturulan ve Microsoft Yönetilen Masaüstü cihazlarına yönelik uyumluluk ilkelerinin hepsini gözden geçirebilirsiniz. <br><br> Daha fazla bilgi için bkz[. 2013'te uyumluluk Microsoft Intune](/mem/intune/protect/create-compliance-policy). |

### <a name="device-configuration-profiles"></a>Cihaz Yapılandırması profilleri

Azure AD'nizin Intune Cihaz Yapılandırması profilleri hiçbir Microsoft Masaüstü aygıtını veya kullanıcıyı yönetecek durumda değil.

| Sonuç  | Anlamı |
| ----- | ----- |
| Hazır değil | Tüm kullanıcılar, tüm cihazlar veya her ikisi için geçerli en az bir yapılandırma profiliniz vardır. Microsoft Yönetilen Masaüstü cihazları olmayan belirli bir Azure AD grubuna uygulamak için profili sıfırlayın. <br><br> Daha fazla bilgi için bkz[. Bu bağlantıda özel ayarlarla profil Microsoft Intune](/mem/intune/configuration/custom-settings-configure). |
| Danışma | Sahip olunan tüm yapılandırma ilkelerinin Microsoft Yönetilen Masaüstü cihazlarını veya kullanıcılarını içermey olduğundan emin olun. <br><br> Daha fazla bilgi için bkz[. Bu bağlantıda özel ayarlarla profil Microsoft Intune](/mem/intune/configuration/custom-settings-configure). |

### <a name="device-type-restrictions"></a>Cihaz türü kısıtlamaları

Microsoft Yönetilen Masaüstü cihazlarının Intune'a kaydolmasına izin ver gerekir.

| Sonuç  | Anlamı |
| ----- | ----- |
| Hazır değil | Şu anda, kullanıcıların Intune'da kayıt Windows için en az bir kayıt kısıtlama ilkesini yapılandırmış durumdanız. <br><br> Microsoft Yönetilen [Masaüstü kullanıcılarını](/mem/intune/enrollment/enrollment-restrictions-set) hedef alan her kayıt kısıtlama ilkesi için kayıt kısıtlamalarını ayarlama'daki adımları izleyin ve Windows **(MDM)** ayarını İzin Ver olarak **ayarlayın**. Öte yandan, kişisel olarak sahip **olunan tüm cihaz** **Windows (MDM) cihazlarını Engelle olarak** **ayarlayın.** |

### <a name="enrollment-status-page"></a>Kayıt Durumu Sayfası

Kayıt Durumu Sayfası (ESP) şu anda etkinleştirilmiş durumdadır. Bu özelliğin Microsoft Yönetilen Masaüstü genel önizlemesine katılmak için bu öğeyi yoksayabilirsiniz. Daha fazla bilgi için bkz [. AutoPilot ile ilk çalıştırma deneyimi ve Kayıt Durumu Sayfası](../get-started/esp-first-run.md).

| Sonuç  | Anlamı |
| ----- | ----- |
| Hazır değil | ESP varsayılan profili, Uygulama ve profil yapılandırma **ilerlemesini göster olarak ayarlanmıştır**. <br><br> Kayıt Durumu Sayfasını ayarlama'daki adımları takiperek bu ayarı devre dışı bırakır veya Azure AD gruplarında yapılan ödevlerin Microsoft Yönetilen Masaüstü cihazlarını [içermey olduğundan emin olun](/mem/intune/enrollment/windows-enrollment-status). |
| Danışma | Uygulama ve profil yapılandırması ilerleme durumu ayarının göster  ayarına sahip profillerin Microsoft Yönetilen Masaüstü cihazları içeren hiçbir Azure AD grubuna atanmay olduğundan emin olun. <br><br> Daha fazla bilgi için bkz [. Kayıt Durumu Sayfasını Ayarlama](/mem/intune/enrollment/windows-enrollment-status). |

### <a name="microsoft-store-for-business"></a>İş İçin Microsoft Store

Microsoft Yönetilen İş İçin Microsoft Store'de Şirket Portalı'i kullanıyor ve dağıtabilirsiniz. Bu yöntem, isteğe bağlı olarak kullanıcıların Microsoft Project ve Microsoft Visio (izin verilen durumlarda) gibi bazı uygulamaları yüklemesine olanak sağlar.

| Sonuç  | Anlamı |
| ----- | ----- |
| Hazır değil | İş İçin Microsoft Store etkinleştirilmemiş veya Intune ile eşit değildir. <br><br> Daha fazla bilgi için bkz[.](/mem/intune/apps/windows-store-for-business) İş İçin Microsoft Store ile satın alınan toplu uygulamaları Microsoft Intune [ve Intune Şirket Portalı'i cihazlara yükleme](../get-started/company-portal.md). |

### <a name="multi-factor-authentication"></a>Çok faktörlü kimlik doğrulaması

Çok faktörlü kimlik doğrulaması Microsoft Yönetilen Masaüstü'nun Intune ve Azure AD'de Azure AD organizasyonlarınızı (kiracı) yönetmesini engelley.

| Sonuç  | Anlamı |
| ----- | ----- |
| Hazır değil | Tüm kullanıcılara atanmış koşullu erişim ilkeleri için gerekli **olarak** ayarlanmış bazı çok faktörlü kimlik doğrulama ilkeleriniz vardır. <br><br> Kayıt sırasında, Microsoft Yönetilen Masaüstü hizmeti hesaplarını ilgili koşullu erişim ilkelerinin dışında tutacağız ve bu hesaplara erişimi kısıtlamak için yeni koşullu erişim ilkeleri uygulamamız gerekir. <br><br> Bu hizmet hesapları hakkında daha fazla bilgi için bkz. [Standart işletim yordamları](../service-description/operations-and-monitoring.md#standard-operating-procedures). |
| Danışma | Microsoft Yönetilen Masaüstü'ünün Microsoft Yönetilen Masaüstü hizmetini yönetmesini önleyen koşullu erişim ilkelerinde çok faktörlü kimlik doğrulaması gereklidir. <br><br> Kayıt sırasında, Microsoft Yönetilen Masaüstü hizmeti hesaplarını ilgili koşullu erişim ilkelerinin dışında tutabilirsiniz ve bu hesaplara erişimi kısıtlamak için yeni koşullu erişim ilkeleri uygulayabilirsiniz. Bu hizmet hesapları hakkında daha fazla bilgi için bkz. [Standart işletim yordamları](../service-description/operations-and-monitoring.md#standard-operating-procedures). |
| Error | Intune Yönetici rolü, bu denetim için yeterli izinlere sahip değildir. Bu denetimi çalıştırmak için ayrıca şu Azure AD rollerinin atanmış olduğu da gerekir: <ul><li>Güvenlik Okuyucu</li><li>Güvenlik Yöneticisi</li><li>Koşullu Erişim Yöneticisi</li><li>Genel Okuyucu</li><li>Cihaz Yöneticisi</li></ul>

### <a name="powershell-scripts"></a>PowerShell betikleri

Windows PowerShell betikleri, Microsoft Yönetilen Masaüstü cihazlarını hedef alan bir şekilde atanabilir.

| Sonuç  | Anlamı |
| ----- | ----- |
| Danışma | Azure AD Windows PowerShell tüm betiklerin microsoft Masaüstü cihazlarını veya kullanıcılarını yönetmey olduğundan emin olun. Tüm kullanıcıları, tüm cihazları veya her ikisini birden hedeflemek için PowerShell betiği atayın. İlkeyi değiştirarak Microsoft Yönetilen Masaüstü cihazı veya kullanıcı içermesi olmayan belirli bir Azure AD grubunu hedef alan bir Atama kullanın. <br><br> Daha fazla bilgi için bkz[. Intune'daki tüm Windows 10 PowerShell betiklerini kullanma](/mem/intune/apps/intune-management-extension). |

### <a name="region"></a>Bölge

Bölgeniz Microsoft Tarafından Yönetilen Masaüstü tarafından destek desteklensin.

| Sonuç  | Anlamı |
| ----- | ----- |
| Hazır değil | Azure AD kuruluş bölgeniz şu anda Microsoft Yönetilen Masaüstü tarafından desteklenmiyor. <br><br> Daha fazla bilgi için [bkz. Microsoft Yönetilen Masaüstü'de desteklenen bölgeler ve diller](../service-description/regions-languages.md). |
| Danışma | Azure AD kuruluşlarının bulunduğu ülkelerin biri veya birden fazlası Microsoft Yönetilen Masaüstü tarafından desteklenmiyor. <br><br> Daha fazla bilgi için [bkz. Microsoft Yönetilen Masaüstü'de desteklenen bölgeler ve diller](../service-description/regions-languages.md). |

### <a name="security-baselines"></a>Güvenlik taban çizgilerini

Güvenlik taban çizgisi ilkeleri hiçbir Microsoft Yönetilen Masaüstü cihazına hedef olmaması gerekir.

| Sonuç  | Anlamı |
| ----- | ----- |
| Hazır değil | Tüm kullanıcıları, tüm cihazları veya her ikisini de hedef alan bir güvenlik temeli profiliniz vardır. Microsoft Yönetilen Masaüstü cihazları olmayan belirli bir Azure AD grubunu hedef alan bir atamayı kullanmak için ilkeyi değiştirebilirsiniz. <br><br> Daha fazla bilgi için bkz[. Intune'da güvenlik Windows 10 için güvenlik taban çizgilerini kullanma](/mem/intune/protect/security-baselines). Kayıt sırasında, tüm Microsoft Yönetilen Masaüstü cihazlarına yeni bir güvenlik temeli uygulanır. Kayıt sonrasında, TT'nin Yapılandırma ilkesi alanında Microsoft Yönetilen Masaüstü **güvenlik** temeli Microsoft Endpoint Manager. |
| Danışma | Microsoft Yönetilen Masaüstü cihazları hariç tutmak için tüm güvenlik temeli ilkelerinin geçerli olduğundan emin olun. Daha fazla bilgi için bkz[. Intune'da güvenlik Windows 10 için güvenlik taban çizgilerini kullanma](/mem/intune/protect/security-baselines). <br><br> Kayıt sırasında, tüm Microsoft Yönetilen Masaüstü cihazlarına yeni bir güvenlik temeli uygulanır. **Modern Çalışma Alanı Cihazları - Tüm** Azure AD grubu, Microsoft Yönetilen Masaüstü'ne kaydolan dinamik bir grupdur. Kayıt sonrasında bu grubu dışarıda tutmak için geri dönmelisiniz. |

### <a name="unlicensed-admins"></a>Lisanssız yöneticiler

Azure AD organizasyonuyla etkileşime geçildiğinde "izin olmaması" hatasını önlemek için bu ayarın etkinleştirilmesi gerekir.

| Sonuç  | Anlamı |
| ----- | ----- |
| Hazır değil | **Lisanssız yöneticilere erişim izninin etkinleştirilmesi** gerekir. Daha fazla bilgi için bkz. [Konuk hesaplarının önkoşulları](/microsoft-365/managed-desktop/get-ready/guest-accounts). |

### <a name="windows-apps"></a>Windows uygulamaları

Microsoft Yönetilen Masaüstü kullanıcılarınızı almak istediğiniz uygulamaları gözden geçirebilirsiniz.

| Sonuç  | Anlamı |
| ----- | ----- |
| Danışma | Microsoft Yönetilen Masaüstü kullanıcılarınızı satın almak istediğiniz uygulamaların envanterini hazırlamanız gerekir. Bu uygulamaların Intune tarafından dağıtılması gerekir, çünkü mevcut Intune uygulamalarının yeniden kullanılabilir olduğunu değerlendirin. Kullanıcılarınıza uygulama [Şirket Portalı için Intune Şirket Portalı](../get-started/company-portal.md) Bilgisayar Yükleme ve Kayıt Durumu Sayfası (ESP) sayfasına (ESP) göz atın. <br><br> Daha fazla bilgi için bkz [. Microsoft Yönetilen](apps.md) Masaüstü ve [İlk çalıştırma deneyiminde Autopilot ile uygulamalar ve Kayıt Durumu Sayfası](../get-started/esp-first-run.md). <br><br> Microsoft hesap temsilcinize, Intune'a geçirilirken hazır olan veya ayarlamaya gerek olan uygulamaları tanımlamak için Microsoft Endpoint Configuration Manager'daki bir sorguyu sorabilirsiniz. |

### <a name="windows-hello-for-business"></a>Windows Hello Kurumsal

Microsoft Yönetilen Masaüstü için Windows Hello için Microsoft Kurumsal'ın etkinleştirilmesi gerekir.

| Sonuç  | Anlamı |
| ----- | ----- |
| Danışma | Windows Hello Kurumsal devre dışı veya ayarlanmaz. bunu etkinleştirmek için İş için Windows Hello [ilkesi oluşturma'daki adımları izleyin](/mem/intune/protect/windows-hello#create-a-windows-hello-for-business-policy). |

### <a name="windows-10-update-rings"></a>Windows 10 güncelleştirme halkaları

Intune Windows 10 ta "güncelleştirme halkası" ilkeniz hiçbir Microsoft Yönetilen Masaüstü cihazı hedefleyemmektedir.

| Sonuç  | Anlamı |
| ----- | ----- |
| Hazır değil | Tüm cihazları, tüm kullanıcıları veya her ikisini hedef alan bir "güncelleştirme halkası" ilkeniz var. İlkeyi değiştirarak Microsoft Yönetilen Masaüstü cihazı olmayan belirli bir Azure AD grubunu hedef alan bir Atama kullanın. <br><br> Daha fazla bilgi için bkz[. Intune'Windows 10 güncelleştirmelerini yönetme](/mem/intune/protect/windows-update-for-business-configure). |
| Danışma | Sahip olduğu tüm güncelleştirme halkası ilkelerini Modern Çalışma Alanı Cihazları **- Tüm Azure AD grubunu dışlayanın** . Bu ilkelere Azure AD kullanıcı grupları atadınız, sizin de modern çalışma alanı **-** Microsoft Yönetilen Masaüstü kullanıcılarınızı ekley istediğiniz tüm Azure AD grubunu (veya eşdeğer bir gruba) hariç tutmak istediğiniz tüm güncelleştirme halkası ilkelerinin olduğundan emin olun. <br><br> Daha fazla bilgi için bkz[. Intune'Windows 10 güncelleştirmelerini yönetme](/mem/intune/protect/windows-update-for-business-configure). Hem **Modern Çalışma Alanı Cihazları - Tüm hem** **de Modern Çalışma Alanı -** Tüm Azure AD grupları, Microsoft Yönetilen Masaüstü'ne kaydolarak bizim oluşturlarımızdır. Kayıt sonrasında bu grubu dışarıda tutmak için geri dönmelisiniz. |

## <a name="azure-active-directory-settings"></a>Azure Active Directory ayarları

Azure portalında Azure Active Directory ayarlarına [erişebilirsiniz](https://portal.azure.com).

### <a name="intune-enrollment"></a>Intune kaydı

Windows 10 Azure AD kuruluş cihazları otomatik olarak Intune'a kaydedebilir.

| Sonuç  | Anlamı |
| ----- | ----- |
| Danışma | **MDM Kullanıcı kapsamının Hiçbiri değil**, Bazıları veya **Hepsi olarak** **ayarlanmış** olduğundan emin **olun**. <br><br> Bazı **öğesini seçerseniz,** kayıt sonrasında geri gelin ve Modern Çalışma Alanı **-** Gruplar için Tüm Azure AD grubunu veya  Microsoft Yönetilen Masaüstü kullanıcılarının hepsini hedef alan eşdeğer bir grubu seçin. <br><br> Daha fazla bilgi için bkz[. Windows kullanarak cihazlarınız için kayıt Microsoft Intune](/mem/intune/enrollment/windows-enroll#enable-windows-10-automatic-enrollment). |

### <a name="ad-hoc-subscriptions"></a>Geçici abonelikler

"Yanlış" olarak ayarlanmışsa, Durum Dolaşım'ın düzgün Enterprise bir ayar denetlemeyi önerir.

| Sonuç  | Anlamı |
| ----- | ----- |
| Danışma | **AllowAdHocSubscriptions'ın** True olarak ayar olduğundan emin **olmak**. Aksi takdirde, Enterprise Dolaşım çalışmayabilirsiniz. <br><br> Daha fazla bilgi için [bkz. Set-MsolCompanySettings](/powershell/module/msonline/set-msolcompanysettings). |

### <a name="enterprise-state-roaming"></a>Enterprise Durum Dolaşım

Enterprise Dolaşım etkinleştirilmelidir.

| Sonuç  | Anlamı |
| ----- | ----- |
| Danışma | Tüm gruplar veya Enterprise için Durum Dolaşım'ın **etkinleştirildiğinden** **emin** olun. <br><br> Daha fazla bilgi için bkz[. Enterprise'te Durum Dolaşım'Azure Active Directory](/azure/active-directory/devices/enterprise-state-roaming-enable). |

### <a name="guest-invitation-settings"></a>Konuk daveti ayarları

Microsoft Yönetilen Masaüstü konuk daveti ayarlarının ayarlanmasını öneren bir öneridir, çünkü varsayılan ayar dizininizin tüm kullanıcılarının ve konukların konukları davet etmelerini sağlar.

| Sonuç  | Anlamı |
| ----- | ----- |
| Danışma | **Belirli yönetici rollerine atanan üye kullanıcılar ve kullanıcılar, konuk (üye izinleri olan konuklar dahil) etkinleştirilmelidir** . <br><br> Daha fazla bilgi için bkz. [Konuk hesaplarının önkoşulları](/microsoft-365/managed-desktop/get-ready/guest-accounts). |

### <a name="guest-user-access"></a>Konuk kullanıcı erişimi

Microsoft Yönetilen Masaüstü konuk erişimini ayarlamayı öneren bir öneridir, çünkü varsayılan ayar dizinde yer alan tüm konuğun üyelerle aynı erişime sahip olmasına izin verir.

| Sonuç  | Anlamı |
| ----- | ----- |
| Danışma | **Konuk kullanıcıların dizin nesnelerinin özelliklerine ve üyeliklerine erişimi sınırlı olmalıdır** . <br><br> Daha fazla bilgi için bkz. [Konuk hesaplarının önkoşulları](/microsoft-365/managed-desktop/get-ready/guest-accounts). |

### <a name="licenses"></a>Lisanslar

Microsoft Yönetilen Masaüstü'nü kullanmak için birçok lisans gereklidir.

| Sonuç  | Anlamı |
| ----- | ----- |
| Hazır Değil | Microsoft Yönetilen Masaüstü'ne kullanmak için ihtiyacınız olan tüm lisanslara sahip değilsiniz. <br><br> Daha fazla bilgi için bkz [. Microsoft Yönetilen Masaüstü teknolojileri ve](../intro/technologies.md) [Lisanslar hakkında daha fazla bilgi](prerequisites.md#more-about-licenses). |

### <a name="microsoft-managed-desktop-service-accounts"></a>Microsoft Yönetilen Masaüstü hizmeti hesapları

Bazı hesap adları, Microsoft Yönetilen Masaüstü hizmetini yönetmek için Microsoft Yönetilen Masaüstü tarafından oluşturulan hesap adlarla çakışabilirsiniz.

| Sonuç  | Anlamı |
| ----- | ----- |
| Hazır değil | Microsoft Yönetilen Masaüstü tarafından oluşturulan hesap adlarla çakışacak en az bir hesap adınız var. Bu hesap adlarını dışarıda tutmak için Microsoft hesap temsilciniz ile birlikte çalışabilirsiniz. Güvenlik riskini en aza indirmek için hesap adları genel kullanıma açık olarak listelemz.

### <a name="security-administrator-roles"></a>Güvenlik yöneticisi rolleri

Belirli güvenlik rollerine sahip kullanıcıların, uç nokta için Microsoft Defender'da atanmış rolleri olmalıdır.

| Sonuç  | Anlamı |
| ----- | ----- |
| Danışma | Azure AD kuruluşunda bu rollerden herhangi birini atanmış kullanıcılarınız varsa, bunların uç nokta için Microsoft Defender'da da atanmış olduğundan emin olun. Aksi takdirde, bu rollere sahip yöneticiler Yönetici portalına erişamaz. <ul><li>Güvenlik İşleci</li><li>Genel Okuyucu</li></ul> <br> Daha fazla bilgi için bkz [. Rol tabanlı erişim denetimi için roller oluşturma ve yönetme](/windows/security/threat-protection/microsoft-defender-atp/user-roles).

### <a name="security-default"></a>Varsayılan güvenlik

Azure Active Directory'daki güvenlik varsayılanları Microsoft Yönetilen Masaüstü'nizin cihazlarınızı yönetmesini engellemektedir.

| Sonuç  | Anlamı |
| ----- | ----- |
| Hazır değil | Güvenlik varsayılanları açık. Güvenlik varsayılanlarını kapatın ve koşullu erişim ilkelerini ayarlayın. <br><br> Daha fazla bilgi için bkz [. Ortak Koşullu Erişim ilkeleri](/azure/active-directory/conditional-access/concept-conditional-access-policy-common). |

### <a name="self-service-password-reset"></a>Self Servis Parola Sıfırlama

Kendi kendine Parola Sıfırlama (SSPR) Microsoft Yönetilen Masaüstü hizmeti hesapları dışında tüm Microsoft Yönetilen Masaüstü kullanıcıları için etkinleştirilebilir. <br><br> Daha fazla bilgi için bkz. Öğretici: Kullanıcıların kendi kendine parola sıfırlama kullanarak hesaplarının kilidini açmalarını [Azure Active Directory parolaları sıfırlama.](/azure/active-directory/authentication/tutorial-enable-sspr)

| Sonuç  | Anlamı |
| ----- | ----- |
| Danışma | SSPR Selected ayarının Microsoft **Yönetilen** Masaüstü kullanıcılarını da dahil olduğundan, ancak Microsoft Yönetilen Masaüstü hizmeti hesaplarını dışlamalarından emin olun. SSPR etkinleştirildiğinde Microsoft Yönetilen Masaüstü hizmeti hesapları beklendiği gibi çalışabilirsiniz. |

### <a name="standard-user-role"></a>Standart kullanıcı rolü

Microsoft Yönetilen Masaüstü kullanıcıları, Genel yönetici ve Cihaz yöneticisi Azure Active Directory atanan kullanıcılar dışında, yerel yönetici ayrıcalıklarına sahip standart kullanıcılar olur. Microsoft Yönetilen Masaüstü cihazı başlatan diğer tüm kullanıcılara standart bir kullanıcı rolü atanır.

| Sonuç  | Anlamı |
| ----- | ----- |
| Danışma | Kayıt sonrasında, Microsoft Yönetilen Masaüstü kullanıcıları Microsoft Yönetilen Masaüstü cihazlarında yerel yönetici ayrıcalıklarına sahip olmayacaktır. |

## <a name="microsoft-365-apps-for-enterprise"></a>Microsoft 365 Kurumsal Uygulamaları

### <a name="onedrive"></a>OneDrive

Yalnızca **belirli etki alanlarına katılmış bilgisayarlarda eşitlemeye izin ver ayarı** Microsoft Yönetilen Masaüstü ile çakışacak. Bu OneDrive yönetim merkezinden OneDrive [erişebilirsiniz](https://admin.onedrive.com).

| Sonuç  | Anlamı |
| ----- | ----- |
| Danışma | Yalnızca belirli etki alanlarına **katılmış bilgisayarlarda eşitlemeye izin ver ayarını kullanıyorsanız** . Bu ayar Microsoft Yönetilen Masaüstü ile çalışmaz. Bu ayarı devre dışı bırak. Bunun yerine, OneDrive ilkesi kullanmak için kuralları ayarlayın. <br><br> Daha fazla bilgi için bkz [. Yardım için Koşullu Erişim dağıtımı](/azure/active-directory/conditional-access/plan-conditional-access) planlama. |
