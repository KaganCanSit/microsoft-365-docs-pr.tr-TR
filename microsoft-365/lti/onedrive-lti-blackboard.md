---
title: Microsoft OneDrive LTI'yi Blackboard ile tümleştirme
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
description: Yeni Microsoft OneDrive Learning Tools Interoperability for Blackboard ile ödevler oluşturun ve notlayın, kurs içeriğini derleyin ve dosyalar üzerinde gerçek zamanlı olarak işbirliği yapın.
ms.openlocfilehash: 7e43ff51a069db55be06236fb0318aa4453d8feb
ms.sourcegitcommit: 195e4734d9a6e8e72bd355ee9f8bca1f18577615
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2022
ms.locfileid: "64824662"
---
# <a name="integrate-microsoft-onedrive-lti-with-blackboard"></a>Microsoft OneDrive LTI'yi Blackboard ile tümleştirme

Microsoft OneDrive LTI'yi Blackboard ile tümleştirmek iki adımlı bir işlemdir. İlk adım, Microsoft OneDrive LTI'yi Blackboard kurslarında kullanılabilir hale getirir ve ikinci adım Blackboard için Microsoft OneDrive açar.

> [!IMPORTANT]
> Bu tümleştirmeyi gerçekleştiren kişi Blackboard yöneticisi ve Microsoft 365 kiracısının yöneticisi olmalıdır.

## <a name="recommended-browser-settings"></a>Önerilen tarayıcı ayarları

- Microsoft OneDrive için tanımlama bilgilerine izin verilmelidir.
- Açılır pencereler Microsoft OneDrive için engellenmemelidir.

> [!NOTE]
>
> - Chrome tarayıcı gizli modunda tanımlama bilgilerine varsayılan olarak izin verilmez ve buna izin verilmelidir.
> - Microsoft OneDrive LTI, Microsoft Edge tarayıcıdaki özel modda çalışır. Tanımlama bilgilerini engellemediğinizden emin olun (varsayılan olarak izin verilir).

## <a name="register-the-onedrive-lti-13-tool-in-blackboard"></a>OneDrive LTI 1.3 aracını Blackboard'a kaydetme

1. Blackboard'un Yönetici Paneli'nden **LTI Araç Sağlayıcıları'nı** seçin.
2. **LTI 1.3 Aracını Kaydet'i** seçin.
3. İstemci Kimliği alanına şu kimliği yazın veya kopyalayıp yapıştırın: ``78cd1b1c-ccbd-4318-9f90-22241f63b1f5``

   > [!NOTE]
   > Bu istemci kimliğinin eklenmesi, Blackboard'da iki farklı yerleşim yapılandıracaktır: biri İçerik Pazarı, Kitaplar ve Araçlar ve Zengin metin düzenleyicisinden aracı erişime izin veren, diğeri ise Ultra kursları için çevrimiçi kurstaki İçerik Ekle menüsünden aracı erişim sağlar.

4. **Gönder'i** seçin.
5. **Araç Durumu** görünümünde önceden doldurulmuş tüm ayarları gözden geçirin ve **Araç Durumu** yuvarlak düğmesinin **Onaylandı** olduğundan emin olun.
6. **Kurum İlkeleri'nde**, gönderilecek kullanıcı **alanlarındaki Kurstaki rol** ve **Ad** onay kutularını seçin. Diğer tüm kullanıcı alanları isteğe bağlıdır, ancak OneDrive yüklemenizin gelecekteki kanıtı için bunları açık bırakmanız önerilir.
7. **Sınıf hizmet erişimine izin ver** ve **Üyelik hizmeti erişimine izin ver** de şu anda isteğe bağlıdır, ancak LTI aracında gelecekteki güncelleştirmeler için gerekli olabilir.
8. **Dağıtım Kimliğini** kopyalayın. Microsoft LTI Aracı'nı yapılandırmak için buna ihtiyacınız olacaktır.
9. Bitirmek için **Gönder** düğmesini seçin.

## <a name="configure-the-microsoft-lti-tool-to-work-with-blackboard"></a>Microsoft LTI Aracı'nı Blackboard ile çalışacak şekilde yapılandırma

1. [Microsoft OneDrive LTI Kayıt Portalı'na giriş](https://onedrivelti.microsoft.com/admin) yapın.
2. **Yönetici Onayı** düğmesini seçin ve izinleri kabul edin.

> [!CAUTION]
> Bu adım gerçekleştirilmezse, aşağıdaki adım size bir hata verir ve hatayı aldıktan sonra bu adımı bir saat boyunca gerçekleştiremezsiniz.

3. **Yeni LTI Kiracısı oluştur** düğmesini seçin.
4. LTI Kaydı sayfasında, LTI Tüketici Platformu açılan **listesinden Kara Tahta'yı** seçin ve ardından **İleri** düğmesini seçin.
5. Aracı Blackboard'a kaydederken kopyaladığınız **Dağıtım Kimliğini** yapıştırın ve **İleri'yi** seçin.
6. Değişikliklerinizi gözden geçirin ve kaydedin. Kayıt başarılı olduktan sonra bir ileti görüntülenir.
7. Kayıt ayrıntılarınız, giriş sayfasındaki **LTI Kiracılarını Görüntüle** düğmesi seçilerek de gözden geçirilebilir.

Bu adımları tamamladıktan sonra eğitmenleriniz, Kurs İçeriği sayfasındaki 'artı' menüsünü kullandıklarında OneDrive belgeleri açabilir.

## <a name="recommended-content"></a>Önerilen içerik

[Blackboard için Microsoft Tümleştirmeleri](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Microsoft)

[Microsoft Teams Sınıfları tümleştirmesi](https://help.blackboard.com/Learn/Administrator/SaaS/Integrations/Microsoft_Classes)
