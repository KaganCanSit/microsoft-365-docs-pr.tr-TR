---
title: MacOS Uç Nokta için Microsoft Defender Jamf'e Pro
description: MacOS Uç Nokta için Microsoft Defender Jamf'e Pro
keywords: microsoft, defender, Uç Nokta için Microsoft Defender, mac, yükleme, dağıtma, kaldırma, intune, jamfpro, macos, catalina, mojave, high sierra
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
ms.openlocfilehash: 6189b61826cd56e2a8652032998c3b2df8f980ce
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64468687"
---
# <a name="enroll-microsoft-defender-for-endpoint-on-macos-devices-into-jamf-pro"></a>MacOS Uç Nokta için Microsoft Defender Jamf'e Pro

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta için Microsoft Defender Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
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

   :::image type="content" source="images/a347307458d6a9bbfa88df7dbe15398f.png" alt-text="Yapılandırma ayarları1" lightbox="images/a347307458d6a9bbfa88df7dbe15398f.png":::

2. **+ Yeni'yi seçin**.

   :::image type="content" source="images/b6c7ad56d50f497c38fc14c1e315456c.png" alt-text="Logo açıklamasının otomatik olarak oluşturulma yakını" lightbox="images/b6c7ad56d50f497c38fc14c1e315456c.png":::

3. Davet **Adresi Için Alıcıları Belirtin** > E-posta Adresleri'nin altında alıcıların e-posta adreslerini(leri) girin.

    :::image type="content" source="images/718b9d609f9f77c8b13ba88c4c0abe5d.png" alt-text="Yapılandırma ayarları2" lightbox="images/718b9d609f9f77c8b13ba88c4c0abe5d.png":::

    :::image type="content" source="images/ae3597247b6bc7c5347cf56ab1e820c0.png" alt-text="Yapılandırma ayarları3" lightbox="images/ae3597247b6bc7c5347cf56ab1e820c0.png":::

    Örneğin: janedoe@contoso.com

    :::image type="content" source="images/4922c0fcdde4c7f73242b13bf5e35c19.png" alt-text="Yapılandırma ayarları4" lightbox="images/4922c0fcdde4c7f73242b13bf5e35c19.png":::

4. Davetin iletiyi yapılandırabilirsiniz.

   :::image type="content" source="images/ce580aec080512d44a37ff8e82e5c2ac.png" alt-text="Yapılandırma ayarları5" lightbox="images/ce580aec080512d44a37ff8e82e5c2ac.png":::

   :::image type="content" source="images/5856b765a6ce677caacb130ca36b1a62.png" alt-text="Yapılandırma ayarları6" lightbox="images/5856b765a6ce677caacb130ca36b1a62.png":::

   :::image type="content" source="images/3ced5383a6be788486d89d407d042f28.png" alt-text="Yapılandırma ayarları7" lightbox="images/3ced5383a6be788486d89d407d042f28.png":::

   :::image type="content" source="images/54be9c6ed5b24cebe628dc3cd9ca4089.png" alt-text="Yapılandırma ayarları8" lightbox="images/54be9c6ed5b24cebe628dc3cd9ca4089.png":::

## <a name="enrollment-method-2-prestage-enrollments"></a>Kayıt Yöntemi 2: Prestage Kayıtları

1. Jamf Pro panosunda **, Prestage kayıtları'ne gidin**.

   :::image type="content" source="images/6fd0cb2bbb0e60a623829c91fd0826ab.png" alt-text="Yapılandırma ayarları9" lightbox="images/6fd0cb2bbb0e60a623829c91fd0826ab.png":::

2. Bilgisayar Ön Görünümü [Kayıtları'nın yönergelerini izleyin](https://docs.jamf.com/9.9/casper-suite/administrator-guide/Computer_PreStage_Enrollments.html).

## <a name="enroll-macos-device"></a>macOS cihazı kaydetme

1. Sistem **Tercihleri** penceresinden Devam'ı seçin ve CA **sertifikasını** yükleyin.

   :::image type="content" source="images/jamfpro-ca-certificate.png" alt-text="Jamf Pro kaydı1" lightbox="images/jamfpro-ca-certificate.png":::

2. CA sertifikası yüklendikten sonra tarayıcı penceresine geri dönüp Devam'ı **seçin** ve MDM profilini yükleyin.

   :::image type="content" source="images/jamfpro-install-mdm-profile.png" alt-text="Jamf Pro kaydı2" lightbox="images/jamfpro-install-mdm-profile.png":::

3. **JAMF'den** indirmelere izin ver'i seçin.

   :::image type="content" source="images/jamfpro-download.png" alt-text="Jamf Pro kaydı3" lightbox="images/jamfpro-download.png":::

4. MDM **Profili** yüklemesi ile devam etmek için Devam'ı seçin.

   :::image type="content" source="images/jamfpro-install-mdm.png" alt-text="Jamf Pro 4" lightbox="images/jamfpro-install-mdm.png":::

5. MDM **Profilini yüklemek** için Devam'ı seçin.

   :::image type="content" source="images/jamfpro-mdm-unverified.png" alt-text="Jamf Pro kaydı5" lightbox="images/jamfpro-mdm-unverified.png":::

6. **Yapılandırmayı tamamlamak** için Devam'ı seçin.

   :::image type="content" source="images/jamfpro-mdm-profile.png" alt-text="Jamf Pro kaydı6" lightbox="images/jamfpro-mdm-profile.png":::
