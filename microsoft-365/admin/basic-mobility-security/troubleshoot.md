---
title: Temel Mobilite ve Güvenlik Sorunlarını Giderme
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
description: Temel Hareketlilik ve Güvenlik sorunlarını izlemek için bu adımları deneyin
ms.openlocfilehash: 1b1b7d67eb07c67c320554c1d64701983da30e15
ms.sourcegitcommit: db1e48af88995193f15bbd5962f5101a6088074b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2022
ms.locfileid: "65636074"
---
# <a name="troubleshoot-basic-mobility-and-security"></a>Temel Mobilite ve Güvenlik Sorunlarını Giderme

Cihazı Basic Mobility ve Security'ye kaydetmeye çalışırken sorun yaşıyorsanız, sorunu izlemek için buradaki adımları deneyin. Genel adımlar sorunu çözmezse, cihaz türünüz için belirli adımları içeren sonraki bölümlerden birine bakın.

## <a name="steps-to-try-first"></a>Önce deneme adımları

Başlamak için aşağıdakileri denetleyin:

- Cihazın Intune gibi başka bir mobil cihaz yönetimi sağlayıcısına kayıtlı olmadığından emin olun.

- Cihazın doğru tarih ve saate ayarlandığından emin olun.

- Cihazda farklı bir WIFI'ye veya hücresel ağa geçin.

- Android veya iOS cihazlar için Intune Şirket Portalı uygulamasını kaldırıp cihaza yeniden yükleyin. 

## <a name="ios-phone-or-tablet"></a>telefon veya tablet iOS

- Bir APNs sertifikası ayarladığınızdan emin olun. Daha fazla bilgi için bkz. [iOS cihazlar için APNs Sertifikası oluşturma](create-an-apns-certificate-for-ios-devices.md).

- **Ayarlar** >  **GeneralProfile** >  **(veya Cihaz Yönetimi)** içinde, bir Yönetim Profili'nin zaten yüklü olmadığından emin olun. Varsa kaldırın.

- "Cihaz kaydedilemedi" hata iletisini görürseniz Microsoft 365 oturum açın ve cihazda oturum açan kullanıcıya Exchange Online içeren bir lisansın atandığından emin olun.

- "Profil yüklenemedi" hata iletisini görürseniz aşağıdakilerden birini deneyin:

    - Safari'nin cihazdaki varsayılan tarayıcı olduğundan ve tanımlama bilgilerinin devre dışı bırakılmadığından emin olun.

    - Cihazı yeniden başlatın ve portal.manage.microsoft.com gidin. Microsoft 365 kullanıcı kimliğiniz ve parolanızla oturum açın ve profili el ile yüklemeyi deneyin.

## <a name="windows-rt"></a>Windows RT

- Etki alanınızın temel mobilite ve güvenlik ile çalışacak şekilde Microsoft 365 ayarlandığından emin olun. Daha fazla bilgi için bkz. [Basic Mobility ve Security'yi ayarlama](set-up.md).
    
- Kullanıcının **Katıl'ın** yerine **Aç'ın** seçildiğinden emin olun.

## <a name="windows-10-pc"></a>Windows 10 bilgisayar

- Etki alanınızın temel mobilite ve güvenlik ile çalışacak şekilde Microsoft 365 ayarlandığından emin olun. Daha fazla bilgi için bkz. [Basic Mobility ve Security'yi ayarlama](set-up.md).
    
- Azure Active Directory Premium yoksa, kullanıcının Bağlan seçmek yerine **yalnızca Cihaz Yönetimi kaydol'ı** seçtiğinden emin olun.

## <a name="android-phone-or-tablet"></a>telefon veya tableti Android

- Cihazın Android çalıştığından emin olun.

- Chrome'un güncel olduğundan ve varsayılan tarayıcı olarak ayarlandığından emin olun.

- "Bu cihazı kaydedemedik" hata iletisini görürseniz, Microsoft 365 oturum açın ve cihazda oturum açan kullanıcıya Exchange Online içeren bir lisansın atandığından emin olun.

- Gerekli son kullanıcı eylemlerinin beklemede olup olmadığını görmek için cihazdaki Bildirim Alanı'nı denetleyin ve bekliyorsa eylemleri tamamlayın.