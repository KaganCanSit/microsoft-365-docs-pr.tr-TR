---
title: iOS cihazları için APN sertifikası oluşturma
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
description: Basic Mobility ve Security'de iPad ve iPhone gibi iOS cihazları yönetmek için bir APNs sertifikası oluşturarak başlayın.
ms.openlocfilehash: 8bcbcdeac9f1cadd945c3f7c44e9192d57db7c82
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65435799"
---
# <a name="create-an-apns-certificate-for-ios-devices"></a>iOS cihazları için APN sertifikası oluşturma

Basic Mobility ve Security'de iPad ve iPhone gibi iOS cihazları yönetmek için bir APNs sertifikası oluşturun.

1. Genel yönetici hesabınızla Microsoft 365 oturum açın.

2. Tarayıcınızda yazın <https://protection.office.com/>.

3. **Veri kaybı önleme** \> **Cihaz yönetimi'ni** ve **iOS cihazlar için APNs Sertifikası'nı** seçin.

4. Apple Anında İletme Bildirimi Sertifikası Ayarlar sayfasında **İleri'yi** seçin.

5. CSR dosyanızı indirin'i seçin ve sertifika imzalama isteğini bilgisayarınızda anımsayacağınız bir yere kaydedin. **İleri**'yi seçin.

6. APNs sertifikası oluştur sayfasında:

    1. Apple Anında İletme Sertifikaları Portalı'nı açmak için Apple APNS Portalı'nı seçin.

    2. Apple Kimliği ile oturum açın.

       > [!IMPORTANT]
       > Hesabı yöneten kullanıcı ayrılsa bile kuruluşunuzda kalacak bir e-posta hesabıyla ilişkilendirilmiş bir şirket Apple Kimliği kullanın. Sertifikayı yenileme zamanı geldiğinde aynı kimliği kullanmanız gerektiğinden bu kimliği kaydedin.

    3. **Sertifika Oluştur'u** seçin ve Kullanım Koşulları'nı kabul edin.

    4. Microsoft 365 bilgisayarınıza indirdiğiniz sertifika imzalama isteğine göz atın ve **Upload'ı** seçin.

       Apple Anında İletme Sertifikası Portalı tarafından oluşturulan APNs sertifikasını bilgisayarınıza indirin.

       > [!TIP]
       > Sertifikayı indirirken sorun yaşıyorsanız tarayıcınızı yenileyin.

7. Microsoft 365 Geri dön ve **Upload APNS sertifika** sayfasına ulaşmak için **İleri'yi** seçin.

8. Apple Anında İletme Sertifikaları Portalı'ndan indirdiğiniz APN sertifikasına göz atın.

9. **Bitir'i** seçin.

Kurulumu tamamlamak için Güvenlik & Uyumluluk Merkezi \> **Güvenlik ilkeleri** \> **Cihaz yönetimi** \> **Ayarları yönet'e** geri dönün.
