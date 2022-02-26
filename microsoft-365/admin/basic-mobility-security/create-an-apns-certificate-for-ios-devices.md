---
title: iOS cihazları için APNs sertifikası oluşturma
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
description: iOS cihazlarını Temel Mobil Kullanım ve Güvenlik'te yönetin.
ms.openlocfilehash: f2539ac1c27bd63c13766e197fc12fafc3906f07
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973709"
---
# <a name="create-an-apns-certificate-for-ios-devices"></a>iOS cihazları için APNs sertifikası oluşturma

Temel Hareketlilik ve Güvenlik nedeniyle iPad ve iPhone gibi iOS cihazlarını yönetmek için APNs sertifikası oluşturun.

1. Genel yönetici hesabınızla Microsoft 365 oturum açın.

2. Tarayıcınızda, yazın <https://protection.office.com/>.

3. Veri  **kaybı önlemeDevice** >  **yönetimi'ne ve** **iOS cihazları için APNs Sertifikası'nın seçeneğini seçin**.

4. Apple Anında Bildirim Sertifika Sertifikası Ayarlar  **Ekle'yi seçin**.

5. CSR dosyanızı indirin'i seçin ve sertifika imzalama isteğini bilgisayarınızda anımsayacak bir yere kaydedin.   **SelectNext**.

6. APNs sertifikası oluştur sayfasında:

    1. Apple Push Sertifikaları Portalı'nı açmak için Apple APNS Portalı'ı seçin.

    2. Apple ID ile oturum açma.

       > [!IMPORTANT]
       > Hesabı yöneten kullanıcı ayrılsa bile, kuruluşta kalacak bir e-posta hesabıyla ilişkilendirilmiş şirket Apple kimliği kullanın. Sertifikayı yenileme zamanı geldiğinde aynı kimliği kullanmak zorunda olduğunuz için bu kimliği kaydedin.

    3.   **SertifikaYıldır'ı**  seçin ve Kullanım Koşullarını kabul et'i seçin.

    4. Dosyadan bilgisayarınıza indirdiğiniz sertifika imzalama isteğine Microsoft 365 ve **tamam'ı Upload**.

       Apple Push Sertifika Portalı tarafından oluşturulan APNs sertifikasını bilgisayarınıza indirin.

       > [!TIP]
       > Sertifikayı indirmede sorun ediyorsanız, tarayıcınızı yenileyin.

7. APNS sertifika Microsoft 365 **gitmek için,**  Seçenekler'e   **Upload'ı**  seçin.

8. Apple Push Sertifikaları Portalı'dan indirdiğiniz APN sertifikasına göz atabilirsiniz.

9.   **Tamamla'ya seçin**.

Kurulumu tamamlamak için Güvenlik ve Uyumluluk Merkezi'ne & gidin > **Device** >  **managementManage** **** > ayarları.
