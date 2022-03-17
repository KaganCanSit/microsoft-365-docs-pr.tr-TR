---
title: Hazırlık değerlendirme araçları
description: İki aracı, çalıştıracakları denetimleri ve sonuçların anlamını açıklar
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 8d949b13203aaeab51d2518f16650ba6df832195
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63525646"
---
# <a name="readiness-assessment-tools"></a>Hazırlık değerlendirme araçları

Microsoft Yönetilen Masaüstü'ne kaydolarak mümkün olan en rahat deneyimi elde etmek için, öncesinde ayarlamanız gereken ayarlar ve diğer parametreler ve karşılamak üzere bazı cihaz ve ağ gereksinimleri vardır.

Microsoft Yönetilen Masaüstü Yöneticisi portalı üzerinden erişilen bir araç, yönetimle ilgili ayarları denetler. İndirilebilir olan başka bir araç, tek tek cihaz gereksinimlerini ve ağ ayarlarını denetler. Bu araçları kullanarak bu ayarları kontrol edebilirsiniz ve doğru olmayanları düzeltmeye yönelik ayrıntılı adımları alırsınız.

## <a name="downloadable-readiness-assessment-checker-for-devices-and-network"></a>Cihazlar ve ağ için indirilebilir hazırlık değerlendirme denetleyicisi

İndirilebilir hazırlık değerlendirme denetleyicisini kullanma hakkında ayrıntılı bilgi için bkz. [İndirilebilir hazırlık değerlendirme denetleyicisi](readiness-assessment-downloadable.md).

## <a name="online-readiness-assessment-tool-for-management-settings"></a>Yönetim ayarları için çevrimiçi hazırlık değerlendirme aracı

Çevrimiçi [araç,](https://aka.ms/mmdart) Microsoft Yönetilen Masaüstü ile Microsoft Endpoint Manager için Microsoft Intune), Azure Active Directory (Azure AD) ve Microsoft 365'daki ayarları denetler.

Microsoft Yönetilen Masaüstü, Azure AD kurumda (kiracı) son denetim çalıştırmadan sonra, bu denetimlerle ilişkilendirilmiş verileri 12 ay süreyle korur. 12 ay sonra, tanımları belirlenemeyen bir şekilde koruruz. Topladığımız verileri silmeyi seçebilirsiniz.

En azından Genel Okuyucu veya Intune Yöneticisi rolüne sahip olan herkes bu aracı çalıştırabilecektir, ancak denetimlerden ikisi ([Koşullu](readiness-assessment-fix.md#conditional-access-policies) erişim ilkeleri ve [Çok](readiness-assessment-fix.md#multi-factor-authentication) faktörlü kimlik doğrulaması) fazladan izin gerektirir.

> [!IMPORTANT]  
> Çevrimiçi hazırlık değerlendirme aracı, Microsoft Yönetilen Masaüstü'ne ilk kez kaydolma hazırlığınızı denetlemenize yardımcı olur. Organizasyonunız Microsoft Yönetilen Masaüstü'ne zaten kayıtlı ise, bu aracı kullanmayın.

Değerlendirme aracı şu öğeleri denetler:

## <a name="microsoft-intune-settings"></a>Microsoft Intune ayarları

Aşağıdaki adımları takip Microsoft Intune gerekir:

| Çek | Açıklama |
| ------ | ------ |
| AutoPilot dağıtım profili | AutoPilot dağıtım profili atamanın tüm cihazlar için geçerli olmadığını doğrular. <br><br> Profil **hiçbir Microsoft** Yönetilen Masaüstü cihazına atanmamalı. |
| Sertifika bağlayıcıları | Etkin olduğundan emin olmak için sertifika bağlayıcılarının durumunu denetler. |
| Koşullu erişim | Koşullu erişim ilkelerinin tüm kullanıcılara atanmamış olduğunu doğrular. <br><br> Koşullu **erişim ilkeleri Microsoft** Yönetilen Masaüstü hizmeti hesaplarına atanmamalıdır. |
| Cihaz Uyumluluğu ilkeleri | Intune uyumluluk ilkelerinin tüm kullanıcılara atanmamış olduğunu denetler. <br><br> İlkeler **hiçbir** Microsoft Yönetilen Masaüstü cihazına atanmamalıdır. |
| Cihaz Yapılandırması profilleri | Yapılandırma profillerini tüm kullanıcılara veya tüm cihazlara atanmamış olduğunu onaylar. <br><br> Yapılandırma **profilleri hiçbir Microsoft** Yönetilen Masaüstü cihazına atanmamalı. |
| Cihaz türü kısıtlamaları | Kuruluş Windows 10 cihazlarının Intune'a kaydolmasına izin verilmiyor mu? kontrol edin. |
| Kayıt Durumu Sayfası | Kayıt Durumu Sayfasının etkin olmadığını onaylar. |
| Intune kaydı | Azure AD Windows 10 cihazlarınız Intune'a otomatik olarak kaydedilir. |
| İş İçin Microsoft Store | Bu özelliğin İş İçin Microsoft Store ve Intune ile eşit olduğunu onaylar. |
| Çok faktörlü kimlik doğrulaması | Çok faktörlü kimlik doğrulamasının Microsoft Yönetilen Masaüstü hizmeti hesaplarına uygulanma olmadığını doğrular. |
| PowerShell betikleri | Bu Windows PowerShell Microsoft **Yönetilen Masaüstü** cihazlarını hedef alan bir şekilde atanmamış olduğunu denetler. |
| Bölge | Bölgenizin Microsoft Yönetilen Masaüstü tarafından destek geçirilmiyor olduğunu denetler. |
| Güvenlik taban çizgilerini | Güvenlik taban çizgisi profilinin tüm kullanıcıları veya tüm cihazları hedeflene olmadığını denetler. <br><br> Güvenlik taban çizgisi **ilkeleri hiçbir Microsoft** Yönetilen Masaüstü cihazına hedeflenemmektedir. |
| Windows uygulamaları | Microsoft Yönetilen Masaüstü cihazlarına atamak istediğiniz uygulamaları gözden geçirebilirsiniz. |
| Windows Hello Kurumsal | İş için Windows Hello etkinleştirildikten sonra etkinleştirilmiş olup değildir. |
| Windows 10 güncelleştirme halkası | Intune'un "güncelleştirme Windows 10" ilkesinde tüm kullanıcıları veya tüm cihazları hedeflemez. <br><br> İlke, **Herhangi bir** Microsoft Yönetilen Masaüstü cihazına hedeflenemmektedir. |

## <a name="azure-active-directory-settings"></a>Azure Active Directory ayarları

Aşağıdaki adımları takip Azure Active Directory gerekir:

| Çek | Açıklama |
| ----- | ----- |
| Enterprise State Roaming için "geçici" abonelikler | "Yanlış" olarak ayarlanmışsa, Durum Dolaşım'ın düzgün Enterprise bir ayar denetlemeyi önerir. |
| Enterprise Durum Dolaşım | Durum Dolaşım'ın Enterprise denetlemeyi önerir. |
| Lisanslar | Gerekli lisansları elde etmek için gereken lisansları [denetler](prerequisites.md#more-about-licenses). |
| Çok faktörlü kimlik doğrulaması | Çok faktörlü kimlik doğrulamasının tüm kullanıcılara uygulanmadısını denetler. <br><br> Çok faktörlü kimlik **doğrulaması yanlışlıkla** Microsoft Yönetilen Masaüstü hizmeti hesaplarına uygulanmamalıdır. |
| Güvenlik hesabı adları | Hiçbir kullanıcı adlarının Microsoft Yönetilen Masaüstü tarafından kendi kullanımı için rezerve edildikleriyle çakışmasını denetler. |
| Güvenlik yöneticisi rolleri | Güvenlik Okuyucusu, Güvenlik İşleci veya Genel Okuyucu rollerine sahip kullanıcılara Uç Nokta için Microsoft Defender'da bu roller atandığı onaylar. |
| Güvenlik varsayılanları | Azure AD kuruluşlarının Güvenlik Varsayılanları'nın etkin olup olmadığını denetler Azure Active Directory. |
| Kendi kendine parola sıfırlama | Kendi kendine parola sıfırlamanın etkinleştirildiğinden onaylar. |
| Standart kullanıcı rolü | Kullanıcıların standart kullanıcı olduğunu ve yerel yönetici haklarına sahip olmadığını doğrular. |

## <a name="microsoft-365-apps-for-enterprise-settings"></a>Microsoft 365 Uygulamaları ayarları Enterprise değiştirme

Aşağıdaki adımları takip Microsoft 365 Uygulamaları ve Enterprise gerekir:

| Çek | Açıklama |
| ----- | ----- |
| OneDrive İş | Bu OneDrive İş desteklenmeyen ayarlar kullanıp kullanmadı bunu denetler. |

Her denetimde, araç dört olası sonuçdan birini bildirecek:

| Sonuç | Anlamı |
| ----- | ----- |
| Hazır | Kaydı tamamlamadan önce herhangi bir işlem gerekmez. |
| Danışma | Kayıt ve kullanıcılar için en iyi deneyimi yaşamak için araçta yer alan adımları izleyin. <br><br> Kaydı *tamamabilirsiniz* , ancak ilk cihazınızı dağıtmadan önce bu sorunları çözmeniz gerekir. |
| Hazır değil | **Bu sorunları** çözesiniz kayıt başarısız olur. <br><br> Bunları çözmek için araçta olan adımları izleyin. |
| Error | Kullanmakta olduğunuz Azure Active Director (AD) rolü, bu denetimi çalıştırmak için yeterli izinlere sahip değil. |

## <a name="after-enrollment"></a>Kayıt sonrasında

Microsoft Yönetilen Masaüstü'ne kaydı tamamlandıktan sonra, geri dönüp belirli Intune ve Azure AD ayarlarını ayarlamayı unutmayın. Daha fazla bilgi için bkz [. Kayıttan sonra ayarları ayarlama](../get-started/conditional-access.md).

## <a name="steps-to-get-ready-for-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü için hazır adımlar

1. [Microsoft Yönetilen Masaüstü için önkoşulları gözden geçirebilirsiniz](prerequisites.md).
2. Hazırlık değerlendirme araçlarını çalıştırın (bu makale).
3. Satın [Şirket Portalı](../get-started/company-portal.md).
4. Konuk [hesapları için önkoşulları gözden geçirebilirsiniz](guest-accounts.md).
5. Ağ [yapılandırmasını denetleme](network.md).
6. [Sertifikaları ve ağ profillerini hazırlayın](certs-wifi-lan.md).
7. [Verileri kullanıcı erişimini hazırlama](authentication.md).
8. [Uygulamaları hazırlama](apps.md).
9. [Eşlenmiş sürücüleri hazırlama](mapped-drives.md).
10. [Yazdırma kaynaklarını hazırlama](printing.md).
11. Cihaz [adlarını adresle](address-device-names.md).
