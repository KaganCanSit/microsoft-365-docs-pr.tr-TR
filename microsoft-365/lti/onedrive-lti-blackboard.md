---
title: LTI'Microsoft OneDrive Blackboard ile tümleştirin
ms.author: danismith
author: DaniEASmith
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: Yeni Blackboard için Microsoft OneDrive Learning Araçları Birlikte Çalışabilirliği ile ödev oluşturun ve not edin, ders içeriğini oluşturun ve sergiyi oluşturun, dosyalar üzerinde gerçek zamanlı olarak işbirliği yapın.
ms.openlocfilehash: 94e77181244bbf02115bd706e86751a9382b906b
ms.sourcegitcommit: a9266e4e7470e8c1e8afd31fef8d266f7849d781
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2022
ms.locfileid: "63705302"
---
# <a name="integrate-microsoft-onedrive-lti-with-blackboard"></a>LTI'Microsoft OneDrive Blackboard ile tümleştirin

LTI Microsoft OneDrive Blackboard ile tümleştirme, iki adımlı bir işlemdir. İlk adım tüm LTI'Microsoft OneDrive Blackboard kurslarının içinde kullanılabilir olduğunu ve ikinci adım da Microsoft OneDrive Blackboard için kullanılabilir.

> [!IMPORTANT]
> Bu tümleştirmeyi gerçekleştiren kişi Blackboard yöneticisi ve kullanıcı kiracısı yöneticisi Microsoft 365 gerekir.

## <a name="recommended-browser-settings"></a>Önerilen tarayıcı ayarları

- Tanımlama bilgilerine izin ver Microsoft OneDrive.
- Açılır pencerelerin, açılan pencerelerin bir Microsoft OneDrive.

> [!NOTE]
>
> - Chrome tarayıcı gizli modunda tanımlama bilgilerine varsayılan olarak izin verilmez ve bu moda izin verilmeleri gerekir.
> - Microsoft OneDrive LTI, tarayıcıda özel modda Microsoft Edge çalışır. Tanımlama bilgilerini engellememenizin (varsayılan olarak izin verilen tanımlama bilgileri) olduğundan emin olur.

## <a name="register-the-onedrive-lti-13-tool-in-blackboard"></a>Blackboard'OneDrive LTI 1.3 aracını kaydetme

1. Blackboard'un Yönetici Paneli'den,LTI  **Araç Sağlayıcıları'nı seçin**.
2.  **SelectRegister LTI 1.3 Tool**.
3. İstemci Kimliği alanında, şu kimliği yazın veya kopyalayıp yapıştırın: ``78cd1b1c-ccbd-4318-9f90-22241f63b1f5``

  > [!NOTE]
  > Bu istemci kimliği, Blackboard'da iki farklı yerleşim yapılandıracak: Bunlardan biri İçerik Marketi, Kitaplar ve Araçlar ile Zengin metin düzenleyicisinden ara sunucuya erişim sağlar, diğeri ise Ultra dersler için çevrimiçi kursta bulunan İçerik Ekle menüsünden aracida erişim sağlar.

4. **Gönder'i seçin**.
5. Araç Durumu görünümü'ne önceden doldurulmuş tüm  **ayarları gözden**  geçirip Araç Durumu yuvarlak düğmesinin Seçili  **olduğundan emin olun**.
6.  **InStitution Policies,** select the **Role in course** and **the Name** onay kutularını da in user fields to send. Diğer tüm kullanıcı alanları isteğe bağlıdır, ancak gelecekte bu alanları yeniden yüklemenizi denetlemeleri için OneDrive önerilir.
7. **Sınıf hizmeti erişimine izin ver**   **andAllow üyelik hizmeti erişimi** de şu anda isteğe bağlıdır, ancak LTI aracının gelecek güncelleştirmeleri için gerekli olabilir.
8. Dağıtım **Kimliğini kopyalayın**. Microsoft LTI Aracını yapılandırmak için ona ihtiyacınız vardır.
9. Bitirmek **için Gönder** düğmesini seçin.

## <a name="configure-the-microsoft-lti-tool-to-work-with-blackboard"></a>Microsoft LTI Aracını Blackboard ile çalışacak şekilde yapılandırma

1. [Portalda LTI Microsoft OneDrive oturum açın](https://onedrivelti.microsoft.com/admin).
2. Yönetici Onayı **düğmesini seçin** ve izinleri kabul edin.

> [!CAUTION]
> Bu adım gerçekleştirile değilse, aşağıdaki adım size bir hata verir ve hatayı alırsanız bu adımı bir saat süreyle aşamazsınız.

3. Yeni **LTI Kiracısı Oluştur düğmesini** seçin.
4. LTI Kayıt sayfasında, LTI Tüketici **Platformu açılan listesinden Blackboard'ı** seçin ve sonra da Sonraki **düğmesini** seçin.
5. Aracı **Blackboard'a** kaydettirirken kopyalanan Dağıtım Kimliği'ne yapıştırın ve Ardından Sonraki'yi **seçin**.
6. Değişikliklerinizi gözden geçirin ve kaydedin. Başarılı kayıt işlemi sırasında bir ileti görüntülenir.
7. Kayıt ayrıntılarınız, giriş sayfasında **LTI** Kiracıları Görüntüle düğmesi seçerek de inceleyebilirsiniz.

Bu adımları tamamlandıktan sonra, eğitmeniniz Ders İçeriği sayfasındaki 'OneDrive' menüsünü kullandıktan sonra belgeleri OneDrive'den açabilirler.

## <a name="recommended-content"></a>Önerilen içerik

[Blackboard için Microsoft Tümleştirmeleri](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Microsoft)

[Microsoft Teams Sınıfları tümleştirmesi](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Microsoft_Classes)
