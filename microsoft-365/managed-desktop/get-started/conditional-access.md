---
title: Kayıt sonrasında ayarları ayarlama
description: Belirli Microsoft hesaplarını dışarıda tutmak için
keywords: Microsoft Yönetilen Masaüstü, Microsoft 365, hizmet, belgeler
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: a5ff8a9a662eb442b7a18726463f14e914d4a133
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63317550"
---
# <a name="adjust-settings-after-enrollment"></a>Kayıt sonrasında ayarları ayarlama

Microsoft Yönetilen Masaüstü'ne kaydı tamamlandıktan sonra bazı yönetim ayarlarının ayarlanması gerekebilir. Gerekirse kontrol etmek ve ayarlamak için şu adımları izleyin:

1. Sonraki Microsoft Intune ve Azure Active Directory ayarları gözden geçirme.
2. Öğelerden herhangi biri ortamınıza uygulanıyorsa, ayarlamaları açıklandığı gibi yapma.
3. Tüm ayarların doğru olup olmadığını bir kez daha kontrol etmek gerekirse, Microsoft Yönetilen Masaüstü ile hiçbir [](https://aka.ms/mmdart) çakışma olmasını sağlamak için hazırlık değerlendirme aracını yeniden çalıştırabilirsiniz.

> [!NOTE]
> İşlemlerinizi sonraki aylarda da devam ettirdikten sonra Microsoft Yönetilen Masaüstü'nüzde Microsoft Intune, Azure Active Directory veya Microsoft 365 ilkelere kayıt sonrasında değişiklik yaptısanız, Microsoft Yönetilen Masaüstü'nun düzgün çalışması durdurabilir. Hizmetle ilgili sorunları önlemek için, orada listelenen ilkeleri değiştirmeden önce [](../get-ready/readiness-assessment-fix.md) hazırlık değerlendirme aracı tarafından bulunan sorunları çözme konusunda açıklanan belirli ayarlara göz yapın. Ayrıca, herhangi bir anda hazırlık değerlendirme aracını yeniden çalıştırabilirsiniz.

## <a name="microsoft-intune-settings"></a>Microsoft Intune ayarları

| Ayar | Açıklama |
| ------ | ------ |
| AutoPilot dağıtım profili | Herhangi bir AutoPilot ilkelerini kullanıyorsanız, modern Çalışma Alanı Cihazları -Tüm Azure AD grubunu **dışarıda tutmak için her birini** güncelleştirin. <br><br> **AutoPilot ilkelerini güncelleştirmek için:** <br><br> **Ödevler'in** altında, **Dışarıda bırakılan gruplarda**, Microsoft Yönetilen Masaüstü kaydı sırasında oluşturulan Modern Çalışma Alanı Cihazları **-** Tüm Azure AD grubunu seçin. <br><br> Microsoft Yönetilen Masaüstü ayrıca, adının içinde "Modern Workplace" (Modern workplace AutoPilot Profili) bulunan bir **AutoPilot profili de oluşturulmuş olur**. Kendi AutoPilot profillerinizi güncelleştirerek, Modern Çalışma Alanı Cihazları **-Tüm** Azure AD grubunu Microsoft Yönetilen Masaüstü tarafından oluşturulan **Modern workplace AutoPilot** Profili'nin dışında tutmaktan emin olun. |
| Koşullu Erişim ilkeleri | Microsoft Tarafından Yönetilen Masaüstü kaydından sonra Azure AD, Microsoft Intune veya Microsoft 365 Defender Uç Nokta ile ilgili yeni koşullu erişim ilkeleri oluşturmanız, Azure AD'nin **Modern Çalışma** Alanı Hizmet Hesapları Azure AD grubunu bu ilkelerden çıkarabilirsiniz. Daha fazla bilgi için bkz. [Koşullu Erişim: Kullanıcılar ve gruplar](/azure/active-directory/conditional-access/concept-conditional-access-users-groups). Microsoft Yönetilen Masaüstü, bu hesaplara erişimi kısıtlamak için ayrı koşullu erişim ilkeleri sağlar. <br><br> **Microsoft Yönetilen Masaüstü koşullu erişim politikasını (Modern çalışma alanı – Güvenli İş Istasyonu) gözden geçirmek için:** <br><br> Uç nokta Microsoft Endpoint Manager'da Koşullu **Erişim'e** **gidin**. Microsoft Yönetilen Masaüstü tarafından oluşturulan ve adının içinde "Modern Çalışma Alanı" bulunan Azure AD koşullu erişim ilkelerini değiştirmeyin. |
| Çok faktörlü kimlik doğrulaması | Azure AD, Intune veya Microsoft 365 Defender Microsoft Yönetilen Masaüstü kaydından sonra Uç Nokta için ile ilgili koşullu erişim ilkelerinde yeni çok faktörlü kimlik doğrulama gereksinimleri oluşturmanız, Azure AD'nin **Modern** Çalışma Alanı Hizmet Hesapları grubunu bu gruptan çıkarabilirsiniz. Daha fazla bilgi için bkz. [Koşullu Erişim: Kullanıcılar ve gruplar](/azure/active-directory/conditional-access/concept-conditional-access-users-groups). Microsoft Yönetilen Masaüstü, bu grubun üyelerine erişimi kısıtlamak için ayrı koşullu erişim ilkeleri sağlar. <br><br> **Microsoft Yönetilen Masaüstü koşullu erişim ilkesini gözden geçirmek için (Modern Çalışma Alanı -):** <br><br> Uç nokta Microsoft Endpoint Manager'da Koşullu **Erişim'e** **gidin**.
| Windows 10 güncelleştirme halkası | Oluşturduğunuz tüm Windows 10 güncelleştirme halkası ilkelerini, Modern Çalışma Alanı Cihazları **-Tüm** Azure AD grubunu her ilkeye dahil edin. Daha fazla bilgi için bkz [. Güncelleştirme halkaları oluşturma ve atama](/mem/intune/protect/windows-10-update-rings#create-and-assign-update-rings). <br><br> Microsoft Yönetilen Masaüstü de bazı güncelleştirme halkası ilkeleri oluşturdu ve bunların hepsinin adı "Modern Çalışma Alanı" olacak. Örneğin: <ul><li>Modern Çalışma Alanı Güncelleştirme İlkesi [Broad]</li><li>Modern Çalışma Alanı Güncelleştirme İlkesi [Hızlı]</li><li>Modern Çalışma Alanı Güncelleştirme İlkesi [İlk]</li><li>Modern Çalışma Alanı Güncelleştirme İlkesi [Test]</li></ul> <br>Kendi ilkelerinizi güncelleştiriyorsanız, Modern Çalışma Alanı Cihazları **-** Tüm Azure AD grubunu Microsoft Yönetilen *Masaüstü'tarafından* oluşturulanlar dışında tutmaktan emin olun. |

## <a name="azure-active-directory-settings"></a>Azure Active Directory ayarları

Self servis parola sıfırlama: Tüm kullanıcılarda self servis parola sıfırlamayı kullanıyorsanız, atamayı Microsoft Yönetilen Masaüstü hizmeti hesaplarını dışarıda bırakacak şekilde ayarlayın.

**Bu ödevi ayarlamak için:**

1. Microsoft Yönetilen Masaüstü hizmeti hesapları dışındaki tüm kullanıcılar *için* bir Azure AD dinamik grubu oluşturma
1. "Tüm kullanıcılar" yerine atama için bu grubu kullanın.

Hizmet hesaplarını bulamanıza ve dışarıda bırakmanıza yardımcı olmak için, kullanabileceğiniz dinamik sorgu örneği:

```Console
(user.objectID -ne null) and (user.userPrincipalName -ne "MSADMIN@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MSADMININT@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MWAAS_SOC_RO@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MWAAS_WDGSOC@TENANT.onmicrosoft.com") and (user.userPrincipalName -ne "MSTEST@TENANT.onmicrosoft.com")
```

Bu sorguda, kiracı `@TENANT` etki alanı adınızla değiştirin.

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Microsoft Yönetilen Masaüstü ile çalışmaya başlama adımları

1. Access [yönetici portalı](access-admin-portal.md).
1. [Yönetici portalında yönetici kişilerini ekleyin ve doğrulayın](add-admin-contacts.md).
1. Kayıt sonrasında ayarları ayarlayın (bu makale).
1. Dağıtım ve [Intune Şirket Portalı](company-portal.md).
1. [Lisans atama](assign-licenses.md).
1. [Uygulamaları dağıtın](deploy-apps.md).
1. [Cihazları hazırlayın](prepare-devices.md).
1. [AutoPilot ve Kayıt Durumu Sayfası ile ilk çalıştırma deneyimini ayarlayın](esp-first-run.md).
1. [Kullanıcı desteği özelliklerini etkinleştirin](enable-support.md).
1. [Kullanıcılarınızı cihazları kullanmaya hazır hale hazırlayın](get-started-devices.md).
1. [Uygulama denetimi ile çalışmaya başlama](get-started-app-control.md).
