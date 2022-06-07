---
title: Canvas ile Microsoft Teams sınıflarını kullanma
ms.author: danismith
author: cichur
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
description: Microsoft Teams sınıflarını Canvas ile tümleştirme
ms.openlocfilehash: 10024e124ce50ab542e6e68a5c237a47e1f7af83
ms.sourcegitcommit: 8a0de6240facfe26ee391a14076b7fe534ee6598
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2022
ms.locfileid: "65923029"
---
# <a name="use-microsoft-teams-classes-with-canvas"></a>Canvas ile Microsoft Teams sınıflarını kullanma

Microsoft Teams sınıfları, eğitimcilerin ve öğrencilerin Öğrenme Yönetim Sistemi (LMS) ile Teams arasında kolayca gezinmelerine yardımcı olan bir Öğrenme Araçları Birlikte Çalışabilirliği (LTI) uygulamasıdır. Kullanıcılar, kendi kurslarıyla ilişkili sınıf ekiplerine doğrudan LMS'lerinin içinden erişebilir.

## <a name="prerequisites-before-deployment"></a>Dağıtım Öncesi Önkoşullar

> [!NOTE]
> Geçerli Teams sınıfları LTI yalnızca Tuval kullanıcılarının sınırlı bir kapsamda Microsoft Azure Active Directory (AAD) ile eşitlenmesini destekler.
>
> - Kiracınızın bir Microsoft Education lisansı (A1 veya üzeri) olması gerekir.
> - Tuval ve Microsoft arasında kullanıcıları eşlemek için yalnızca tek bir Microsoft kiracısı kullanılabilir.
> - Kiracınızın Tuval alanı (e-posta, Benzersiz Kullanıcı Kimliği, SIS Kimliği veya Tümleştirme Kimliği) ile AAD'deki bir alan (Kullanıcı Asıl Adı (UPN), Birincil E-posta Adresi (Posta) veya E-posta Diğer Adı (mailNickname)) arasında tam eşleşmesi olmalıdır.
> - Sınıf ve grup oluşturmak için SDS kullanıyorsanız, sınıfların çoğaltılmasını önlemek için SDS'de Takım Oluşturma Seçeneğini devre dışı bırakmanızı ve [Grup Temizleme](/schooldatasync/group-cleanup) gerçekleştirmenizi öneririz. SDS, kuruluş ve kullanıcı verilerini eşitlemek için hala kullanılabilir.

## <a name="enable-the-microsoft-teams-app-in-canvas"></a>Tuval'de Microsoft Teams uygulamasını etkinleştirme

Tümleştirmeye başlamak için geliştirici anahtarlarını etkinleştirerek, Microsoft Teams Eşitleme'yi etkinleştirerek ve Microsoft-Teams-Sync-for-Canvas uygulamasını onaylayarak uygulamayı Canvas'da etkinleştirmeniz gerekir. Uygulamayı onaylamanın yalnızca uygulamaları onaylayan bir Microsoft kiracı yöneticisi tarafından gerçekleştirilebileceğini unutmayın.

**Microsoft Teams Eşitleme'yi etkinleştirmek ve uygulama erişimini onaylamak için**:

1. Canvas'da yönetici olarak oturum açın.

2. Genel gezinti bölmesinde **Yönetici** bağlantısını ve ardından hesabınızı seçin.
3. Yönetici gezintisinde **Geliştirici Anahtarları** bağlantısını ve ardından **Devralınmış** sekmesini seçin.
4. Uygun uygulamaların her biri için **ON** durumunu seçerek dağıtacağınız LTI uygulamalarını etkinleştirin.

5. Yönetici gezintisinde **Ayarlar** bağlantısını ve ardından **Tümleştirmeler** sekmesini seçin.

6. İki durumlu düğmeyi açarak Microsoft Teams Eşitleme'yi etkinleştirin. Bu eşitleme, sınıfların bir kursun kaydına göre Teams'de oluşturulmasını sağlar.

   ![Tuval Ekipleri Eşitleme Güncelleştirildi png.](https://user-images.githubusercontent.com/87142492/128225881-abdfc52d-dc9e-48ad-aec5-f6617c6436f3.png)

7. Aşağıdaki alanları uygun bilgilerle doldurun. Bu alanlar Tuval'deki kullanıcıları AAD'deki kullanıcılarla eşleştirmek için kullanılır.
   - **Kiracı Adı**, Microsoft kiracı adınızdır.
   - **Login Özniteliği**, eşleme için kullanılan aşağıdaki Tuval kullanıcı özniteliklerinden biridir:
      - **E-posta** , Tuval kullanıcısının varsayılan e-posta adresidir. Kullanıcılar Tuval'de varsayılan e-posta adreslerini değiştirirse kurstaki kayıtlarının Teams ile eşitlenmesi engellenebilir.
      - **Benzersiz Kullanıcı Kimliği** , kullanıcının Tuval oturum açma kimliğidir.
      - **SIS Kullanıcı Kimliği** , Öğrenci Bilgi Sistemi'nden (SIS) doldurulan ve kullanıcının profil sayfasında görüntülenebilir kimlik değeridir.
      - **Tümleştirme Kimliği** yalnızca SIS içeri aktarma işlemleriyle doldurulur ve kullanıcının profil sayfasında görüntülenebilir. Bu benzersiz tanımlayıcı genellikle kurum tarafından sağlanır ve birden çok hesaptaki kullanıcıları tanımlamak için hesap güvenlerinde veya konsorsiyum durumlarında kullanılır.

   - **Sonek** alanı isteğe bağlıdır ve Canvas öznitelikleri ile Microsoft AAD alanları arasında tam eşleme olmadığında bir etki alanı belirtmenize olanak tanır. Örneğin, Tuval e-postanız 'name@example.edu' ise, Microsoft AAD'deki UPN 'ad' ise, sonek alanına '@example.edu' girerek kullanıcıları eşleştirebilirsiniz. Etki alanı bu alana önceki @ ile girilmelidir.
   - Active Directory Arama Özniteliği, AAD'de Tuval özniteliklerinin eşleştirildiği alandır. UPN, birincil e-posta adresi veya e-posta diğer adı arasında seçim yapın.

8. **Ayarları Güncelleştir'i** seçin.

9. Canvas'ın **Microsoft-Teams-Sync-for-Canvas Azure uygulamasına** erişimi onaylamak için **Kiracı erişimi ver** bağlantısını seçin. Microsoft Kimlik Platformu Yönetici Onayı Uç Noktası'na yönlendirilirsiniz.

   ![Izin.](media/permissions.png)

   > [!NOTE]
   > Bu adımın uygulamaları onaylayan bir Microsoft kiracı yöneticisi tarafından gerçekleştirilmesi gerekir.

10. **Kabul Et'i** seçin.

## <a name="integrate-teams-classes-lti-in-canvas"></a>Teams sınıflarını Tuvalde LTI ile tümleştirme

Eşitlemeyi etkinleştirdikten ve Azure uygulamasını onayladıktan sonra, Tuval yöneticisi artık Teams sınıfları LTI uygulamasını Tuval ortamına ekleyebilir, böylece Tuval kullanıcı arabiriminin gezintisinde görünür.

**Teams sınıfları LTI uygulamasını Tuval ortamına eklemek için**:

1. **Yönetici ayarları'ndaki** **Uygulamalar** sekmesinde **+ Uygulama'yı** seçerek Teams LTI uygulamalarını ekleyin.

   ![dış uygulamalar.](media/external-apps.png)

2. **Yapılandırma Türü** için **İstemci Kimliğine Göre'yi** seçin.

   ![uygulama ekleyin.](media/add-app.png)

3. **İstemci Kimliği** için Microsoft Teams sınıfları LTI için **170000000000570** girin ve **gönder'i** seçin.

4. Görüntülenen onayda uygulama adını (Microsoft Teams sınıfları) doğrulayın ve **yükle'yi** seçin.

   Microsoft Teams sınıf LTI uygulaması artık dış uygulamalar listesine eklenmiştir.

## <a name="enabling-the-lti-app-for-canvas-courses"></a>Tuval kursları için LTI uygulamasını etkinleştirme

LTI uygulamasını bir kurs içinde kullanmak için Canvas kursunun eğitmeninin tümleştirme eşitlemesini etkinleştirmesi gerekir. İlgili ekibin oluşturulması için her kursun bir eğitmen tarafından etkinleştirilmesi gerekir; ekip oluşturma için genel bir mekanizma yoktur. Bu, istenmeyen ekiplerin oluşturulmasını önlemek için bir önlem olarak tasarlanmıştır.

Her kurs için LTI uygulamasını etkinleştirmek ve tümleştirme kurulumunu tamamlamak için eğitmenlerinize [eğitimci belgelerine](https://support.microsoft.com/topic/use-microsoft-teams-classes-in-your-lms-preview-ac6a1e34-32f7-45e6-b83e-094185a1e78a#ID0EBD=Instructure_Canvas) başvurun.
