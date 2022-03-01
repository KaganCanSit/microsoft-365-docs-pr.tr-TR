---
title: macOS cihazlarda Uç Nokta için Microsoft Defender'ı Jamf hizmetine Pro
description: macOS cihazlarda Uç Nokta için Microsoft Defender'ı Jamf hizmetine Pro
keywords: microsoft, defender, Endpoint için Microsoft Defender, mac, yükleme, dağıtma, kaldırma, intune, jamfpro, macos, catalina, mojave, high sierra
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: ab3db2e2b64261ae00008aef448a214cd235bda9
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63011823"
---
# <a name="enroll-microsoft-defender-for-endpoint-on-macos-devices-into-jamf-pro"></a>macOS cihazlarda Uç Nokta için Microsoft Defender'ı Jamf hizmetine Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

## <a name="enroll-macos-devices"></a>macOS cihazlarını kaydetme

JamF'e kaydolmanın birden çok yöntemi vardır.

Bu makale sizi iki yönteme göre yönlendirecek:

- [Yöntem 1: Kayıt Davetleri](#enrollment-method-1-enrollment-invitations)
- [Yöntem 2: Prestage Kayıtları](#enrollment-method-2-prestage-enrollments)

Tam liste için bkz. [Bilgisayar Kaydı Hakkında](https://docs.jamf.com/9.9/casper-suite/administrator-guide/About_Computer_Enrollment.html).

## <a name="enrollment-method-1-enrollment-invitations"></a>Kayıt Yöntemi 1: Kayıt Davetleri

1. Jamf Kayıt Pro, Kayıt **davetleri'ne gidin**.

    ![Yapılandırma ayarları1 görüntüsü.](images/a347307458d6a9bbfa88df7dbe15398f.png)

2. **+ Yeni'yi seçin**.

    ![A close up of a logo Description automatically generated.](images/b6c7ad56d50f497c38fc14c1e315456c.png)

3. Davet **Adresi Için Alıcıları Belirtin** > E-posta Adresleri'nin altında alıcıların e-posta adreslerini(leri) girin.

    ![Yapılandırma ayarları2 görüntüsü.](images/718b9d609f9f77c8b13ba88c4c0abe5d.png)

    ![Yapılandırma ayarları3 görüntüsü.](images/ae3597247b6bc7c5347cf56ab1e820c0.png)

    Örneğin: janedoe@contoso.com

    ![Yapılandırma ayarları4 görüntüsü.](images/4922c0fcdde4c7f73242b13bf5e35c19.png)

4. Davetin iletiyi yapılandırabilirsiniz.

    ![Yapılandırma ayarları5 görüntüsü.](images/ce580aec080512d44a37ff8e82e5c2ac.png)

    ![Yapılandırma ayarları6'nın görüntüsü.](images/5856b765a6ce677caacb130ca36b1a62.png)

    ![Yapılandırma ayarları7'nin görüntüsü.](images/3ced5383a6be788486d89d407d042f28.png)

    ![Yapılandırma ayarları8'in görüntüsü.](images/54be9c6ed5b24cebe628dc3cd9ca4089.png)

## <a name="enrollment-method-2-prestage-enrollments"></a>Kayıt Yöntemi 2: Prestage Kayıtları

1. Jamf Pro panosunda **, Prestage kayıtları'ne gidin**.

    ![Yapılandırma ayarları9 resmi.](images/6fd0cb2bbb0e60a623829c91fd0826ab.png)

2. Bilgisayar Ön Görünümü [Kayıtları'nın yönergelerini izleyin](https://docs.jamf.com/9.9/casper-suite/administrator-guide/Computer_PreStage_Enrollments.html).

## <a name="enroll-macos-device"></a>macOS cihazı kaydetme

1. Sistem **Tercihleri** penceresinden Devam'ı seçin ve CA **sertifikasını** yükleyin.

    ![Jamf Kayıt Pro görüntüsü.](images/jamfpro-ca-certificate.png)

2. CA sertifikası yüklendikten sonra tarayıcı penceresine geri dönüp Devam'ı **seçin** ve MDM profilini yükleyin.

    ![Jamf kayıt2 Pro görüntüsü.](images/jamfpro-install-mdm-profile.png)

3. **JAMF'den** indirmelere izin ver'i seçin.

    ![Jamf Kayıt Pro görüntüsü.](images/jamfpro-download.png)

4. MDM **Profili** yüklemesi ile devam etmek için Devam'ı seçin.

    ![Jamf Pro kaydı4 resmi.](images/jamfpro-install-mdm.png)

5. MDM **Profilini yüklemek** için Devam'ı seçin.

    ![Jamf kayıt Pro resmi.](images/jamfpro-mdm-unverified.png)

6. **Yapılandırmayı tamamlamak** için Devam'ı seçin.

    ![Jamf kayıt6 Pro resmi.](images/jamfpro-mdm-profile.png)
