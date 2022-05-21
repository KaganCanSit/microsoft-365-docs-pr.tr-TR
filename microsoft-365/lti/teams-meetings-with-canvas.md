---
title: Canvas ile Microsoft Teams toplantılarını kullanma
ms.author: danismith
author: DaniEASmith
manager: serdars
ms.reviewer: sovaish
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
description: Microsoft Teams toplantıları Canvas ile tümleştirme
ms.openlocfilehash: cbb24972dba7fafe60cb460e514a0fede64a08fb
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65621466"
---
# <a name="use-microsoft-teams-meetings-with-canvas"></a>Canvas ile Microsoft Teams toplantılarını kullanma

Microsoft Teams toplantılar, eğitimcilerin ve öğrencilerin Learning Yönetim Sistemi (LMS) ile Teams arasında kolayca gezinmelerine yardımcı olan bir Learning Araçları Birlikte Çalışabilirliği (LTI) uygulamasıdır. Kullanıcılar, kendi kurslarıyla ilişkili sınıf ekiplerine doğrudan LMS'lerinin içinden erişebilir.

## <a name="prerequisites-before-deployment"></a>Dağıtım Öncesi Önkoşullar

> [!NOTE]
> Geçerli Teams Toplantıları LTI yalnızca sınırlı kapsamda Microsoft Azure Active Directory (AAD) ile Canvas kullanıcıların eşitlenmesini destekler.
>
> - Kiracınızın bir Microsoft Education lisansı olmalıdır.
> - Kullanıcıları Canvas ile Microsoft arasında eşlemek için yalnızca tek bir Microsoft kiracısı kullanılabilir.
> - Grupların çoğaltılmasını önlemek için Sınıf Teams LTI'yi kullanmadan önce School Data Sync (SDS) kapatmanız gerekir.

## <a name="microsoft-office-365-admin"></a>Microsoft Office 365 Yöneticisi

Instructure Canvas içindeki Microsoft Teams tümleştirmesini yönetmeden önce, kuruluşunuzun Microsoft Office 365 yöneticisi tarafından onaylanan Canvas **Microsoft-Teams-Sync-for-Canvas** Azure uygulamasının Canvas yöneticisi kurulumunu tamamlamadan önce kiracıyı Microsoft Azure.

1. Canvas oturum açın.

2. Genel gezinti bölmesinde **Yönetici** bağlantısını ve ardından hesabınızı seçin.

3. Yönetici gezintisinde **Ayarlar** bağlantısını ve ardından **Tümleştirmeler** sekmesini seçin.

   ![Canvas Teams Eşitle Güncelleştirildi png.](https://user-images.githubusercontent.com/87142492/128552407-78cb28e9-47cf-4026-954d-12dc3553af6f.png)

4. Microsoft kiracı adınızı, oturum açma özniteliğinizi, etki alanı sonekini ve AAD arama özniteliğinizi girin. Bu alanlar, Canvas içindeki kullanıcıları Microsoft Azure Active Directory'daki kullanıcılarla eşleştirmek için kullanılır.
   - Login Özniteliği, eşleştirme için kullanılan Canvas kullanıcı özniteliğidir.
   - Sonek alanı isteğe bağlıdır ve Canvas öznitelikleri ile Microsoft AAD alanları arasında tam eşleme olmadığında bir etki alanı belirtmenize olanak tanır. Örneğin, Canvas e-postanız 'name@example.edu' ise, Microsoft AAD'deki UPN 'ad' ise, sonek alanına 'example.edu' girerek kullanıcıları eşleştirebilirsiniz.
   - Active Directory Arama Özniteliği, Microsoft tarafında Canvas özniteliklerinin eşleştirildiği alandır. UPN, birincil e-posta adresi veya e-posta diğer adı arasında seçim yapın.

5. İşiniz bittiğinde **Ayarlar güncelleştir'i** seçin.

6. **Canvas'ın Microsoft-Teams-Sync-for-Canvas Azure uygulamasına** erişimi onaylamak için **Kiracı erişimi ver** bağlantısını seçin. Microsoft Kimlik Platformu Yönetici Onayı Uç Noktası'na yönlendirilirsiniz.

   ![Izin.](media/permissions.png)

7. **Kabul Et'i** seçin.

   > [!NOTE]
   > Eşitleme, LMS iş ortağı tarafından yönetilen ve Microsoft graph API'lerini kullanarak kurs düzeyinde üyeliği Teams ekibiyle eşitlemek için kullanılan bir işlevdir. Bu öncelikle eğitimcinin kurs düzeyinde doğru olarak geçiş yaptığı bir işlevdir. Daha sonra, üyelerin eklenmesi veya silinmesi için LMS tarafında yapılan tüm üyelik değişiklikleri, LMS iş ortağı tarafından uygulanan Eşitleme kullanılarak yansıtılır. Bu işlem bir Eğitimci için etkinleştirilmeden önce bile M365 eğitim enstitüsü yöneticisi, eğitimcilerinin aşağıda bulunan Eşitleme izin modalitesini kullanarak eşitlemeye erişmesine izin verir. Bu izinler, eğitimcilerin LMS kursu ile Teams Sınıf ekipleri arasında üyeliği eşitlemesini sağlamak için LMS iş ortağına verilir.

8. İki durumlu düğmeyi açarak Microsoft Teams eşitlemeyi etkinleştirin.

   ![teams-sync.](media/teams-sync.png)

## <a name="canvas-admin"></a>Canvas Yöneticisi

Microsoft Teams LTI 1.3 Tümleştirmesini ayarlayın.

Canvas Yöneticisi olarak ortamınıza Microsoft Teams toplantıları LTI uygulamasını eklemeniz gerekir. Uygulamanın LTI İstemci Kimliğini not edin.

 - Microsoft Teams toplantıları - 170000000000703

1. **Erişim Yöneticisi** **ayarlarıUygulamalar** > .

2. Teams LTI uygulamalarını eklemek için **+ Uygulama'ya** tıklayın.

   ![dış uygulamalar.](media/external-apps.png)

3. Yapılandırma türü için **İstemci Kimliğine Göre'yi** seçin.

   ![uygulama ekleyin.](media/add-app.png)

4. Sağlanan İstemci Kimliğini girin ve **Gönder'i** seçin.

   Onay için İstemci Kimliği için Microsoft Teams toplantılarıN LTI uygulama adını fark edeceksiniz.

5. **Yükle**’yi seçin.

   Microsoft Teams toplantıları LTI uygulaması dış uygulamalar listesine eklenir.

6. Canvas yönetici hesabındaki geliştirici anahtarlarına giderek, devralınmış'ı seçerek ve Microsoft Teams Toplantıları için "açık" düğmesini açarak uygulamayı etkinleştirin.

## <a name="enable-for-canvas-courses"></a>Canvas Kursları için etkinleştirme

LTI'yi bir kurs içinde kullanabilmek için Canvas kurs eğitmeninin tümleştirme eşitlemesini etkinleştirmesi gerekir. İlgili Teams oluşturulması için her kursun bir eğitmen tarafından etkinleştirilmesi gerekir; Teams oluşturulması için genel bir mekanizma yoktur. Bu, istenmeyen Teams oluşturulmasını önlemek için dikkatli bir şekilde tasarlanmıştır.

Her kurs için LTI'yi etkinleştirme ve tümleştirme kurulumunu tamamlama konusunda eğitmen [belgelerine](https://support.microsoft.com/topic/use-microsoft-teams-classes-in-your-lms-preview-ac6a1e34-32f7-45e6-b83e-094185a1e78a#ID0EBD=Instructure_Canvas) lütfen eğitmenlerinize başvurun.
