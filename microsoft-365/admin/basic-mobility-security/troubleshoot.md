---
title: Temel Mobil Kullanım ve Güvenlik Sorunlarını Giderme
f1.keywords: NOCSH
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
ms.custom: AdminSurgePortfolio
description: Temel Mobil Kullanım ve Güvenlik sorunlarını takip etmek için bu adımları deneyin
ms.openlocfilehash: f625fbc642392ee575b35f225f5e65b942362c4a
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983990"
---
# <a name="troubleshoot-basic-mobility-and-security"></a>Temel Mobil Kullanım ve Güvenlik Sorunlarını Giderme

Temel Mobil Kullanım ve Güvenlik'te bir cihazı kaydetmeye çalışmanız sorun oluyorsa, sorunu takip etmek için buradaki adımları deneyin. Genel adımlar sorunu çözeni, cihazınızın türüne özel adımlar için sonraki bölümlerden birini görmenizi sağlar.

## <a name="steps-to-try-first"></a>İlk önce deneme adımları

Başlamak için şunları kontrol edin:

- Cihazın, önceden başka bir mobil cihaz yönetim sağlayıcısına (örneğin Intune) kaydolmamış olduğundan emin olun.

- Cihazın doğru tarih ve saate ayarlanmış olduğundan emin olun.

- Cihazda farklı bir WiFi veya hücresel ağa geçiş.

- Android veya iOS cihazlarda, Intune Şirket Portalı uygulamayı kaldırın ve yeniden yükleyin. 

## <a name="ios-phone-or-tablet"></a>iOS telefon veya tablet

- APNs sertifikası ayar mutlaka ayarlayın. Daha fazla bilgi için bkz [. iOS cihazları için APNs Sertifikası oluşturma](create-an-apns-certificate-for-ios-devices.md).

- In  **Ayarlar** >  **GeneralProfile** >  **(veya Cihaz Yönetimi)**), önceden bir Yönetim Profili'nin yüklenmemiş olduğundan emin olun. Varsa kaldırın.

- "Cihaz kaydedemedi" hata iletisini görüyorsanız, Microsoft 365'de oturum açın ve cihazda oturum Exchange Online içeren bir lisansın atanmış olduğundan emin olun.

- "Profil yüklenemedi" hata iletisini görüyorsanız, aşağıdakilerden birini deneyin:

    - Cihazda varsayılan tarayıcının Safari olduğundan ve tanımlama bilgilerinin devre dışı bırakılmış olduğundan emin olun.

    - Cihazı yeniden başlatın ve ardından Yeniden Başlat'a portal.manage.microsoft.com. E-posta Microsoft 365 kimliği ve parolayla oturum açma ve profili el ile yükleme girişimi.

## <a name="windows-rt"></a>Windows RT

- Temel Hareketlilik ve Güvenlik ile çalışmak için etki Microsoft 365'de ayarlanmış olduğundan emin olun. Daha fazla bilgi için bkz [. Temel Mobil Kullanım ve Güvenlik'i ayarlama](set-up.md).
    
- Kullanıcının, Katılma'yı  **seçmeden,Turn** Onrather'i   **seçtiğinden emin olun**.

## <a name="windows-10-pc"></a>Windows 10 PC'de

- Temel Hareketlilik ve Güvenlik ile çalışmak için etki Microsoft 365'de ayarlanmış olduğundan emin olun. Daha fazla bilgi için bkz [. Temel Mobil Kullanım ve Güvenlik'i ayarlama](set-up.md).
    
- Bu seçeneği Azure Active Directory Premium, kullanıcının Cihaz ****  Yönetimi'nin yalnızca Kayıt'Azure Active Directory Premium seçtiğinden  **emin** olun Bağlan.

## <a name="android-phone-or-tablet"></a>Android telefon veya tablet

- Cihazın Android 4.4 veya sonraki bir sürümü çalıştır olduğundan emin olun.

- Chrome'un güncel olduğundan ve varsayılan tarayıcı olarak ayar olduğundan emin olun.

- "Bu cihazı kaydettiremedik" hata iletisini görüyorsanız, Microsoft 365'te oturum açın ve cihazda oturum Exchange Online içeren bir lisansın atan olduğundan emin olun.

- Cihazda Bildirim Alanı'ne bakarak gerekli son kullanıcı eylemlerinin beklemede olup olduğunu kontrol edin ve varsa eylemleri gerçekleştirin.