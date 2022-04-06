---
title: Canvas ile Microsoft Teams sınıflarını kullanma
ms.author: v-cichur
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
description: Tüm Microsoft Teams Canvas ile tümleştirin
ms.openlocfilehash: 08edb2065cd91ccb0e0d52290dfe83f8a3e60392
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569014"
---
# <a name="use-microsoft-teams-classes-with-canvas"></a>Canvas ile Microsoft Teams sınıflarını kullanma

Microsoft Teams sınıf, eğitimcilerin ve öğrencilerin Learning Yönetim Sistemi (LMS) ve diğer sistemlerde kolayca gezinmelerine yardımcı olan Learning Araçları Birlikte Çalışabilirlik (LTI) Teams. Kullanıcılar, kursuyla ilişkilendirilmiş sınıf ekiplerine doğrudan LMS'lerinin içinden erişim sağlar.

## <a name="prerequisites-before-deployment"></a>Dağıtımdan Önce Önkoşullar

> [!NOTE]
> Geçerli Teams LTI, Canvas kullanıcılarını yalnızca sınırlı bir kapsam Microsoft Azure Active Directory (AAD) ile eşitlemeyi destekler.
>
> - Kiracınız Bir Microsoft Eğitim lisansına (A1 veya daha yüksek) sahip olması gerekir.
> - Kullanıcıları Canvas ile Microsoft arasında eşlemek için yalnızca tek bir Microsoft kiracısı kullanılabilir.
> - Kiracınız Canvas alanı (e-posta, Benzersiz Kullanıcı Kimliği, SIS Kimliği veya Tümleştirme Kimliği) ile AAD'daki bir alan (Kullanıcı Asıl Adı (UPN), Birincil E-posta Adresi (Posta) veya E-posta Diğer Adı (mailNickname)) arasında tam eşleşmesi olmalıdır.
> - Sınıf ve grup oluşturmak için SDS kullanıyorsanız, sınıfların çoğaltılmasından kaçınmak için SDS'de Ekip Oluşturma Seçeneğini devre [](/schooldatasync/group-cleanup) dışı bırakmanızı ve Grup Temizleme işlemini gerçekleştirmenizi öneririz. SDS, kuruluş ve kullanıcı verilerini eşitlemek için kullanılabilir.

## <a name="enable-the-microsoft-teams-app-in-canvas"></a>Canvas'Microsoft Teams'yi etkinleştirme

Tümleştirmeye başlamak için geliştirici tuşlarını etkinleştirerek, Microsoft Teams Sync'i etkinleştirerek ve Microsoft-Teams-Sync-for-Canvas uygulamasını onayarak Uygulamayı Canvas'da etkinleştirmeniz gerekir. Uygulamanın onaylanması yalnızca uygulamaları onaylayan bir Microsoft kiracı yöneticisi tarafından gerçekleştiriliyor.

**Eşitlemeyi Microsoft Teams ve uygulamaya erişimi onaylamak için**:

1. Yönetici olarak Canvas'ta oturum açın.

2. Genel **gezinti bölmesinde** Yönetici bağlantısını seçin ve sonra da hesabınız'ı seçin.
3. Yönetici gezintisinde Geliştirici Tuşları **bağlantısını ve** sonra Devralınan **sekmesini** seçin.
4. Uygun uygulamaların her biri için ON durumunu seçerek dağıtmakta olacağınız LTI uygulamalarını etkinleştirin.

5. Yönetici gezintisinde, Önce **Ayarlar** sonra Tümleştirmeler **sekmesini** seçin.

6. Eşitlemeyi Microsoft Teams iki durumlu düğmeyi açık olarak etkinleştirin. Bu eşitleme, bir kursun kaydına Teams içinde sınıfların oluşturulmalarına olanak sağlar.

   ![Canvas'Teams Eşitleme Güncelleştirildi png dosyası.](https://user-images.githubusercontent.com/87142492/128225881-abdfc52d-dc9e-48ad-aec5-f6617c6436f3.png)

7. Uygun bilgilerle aşağıdaki alanları doldurun. Bu alanlar Canvas'ta bu alanları başka kullanıcılarla eşleşen kullanıcılarla AAD.
   - Kiracı **Adı,** Microsoft kiracı adınızdır.
   - Login **Özniteliği,** eşleme için kullanılan aşağıdaki Canvas kullanıcı özniteliklerinden biridir:
      - **E-posta** , Canvas kullanıcıs ın varsayılan e-posta adresidir. Kullanıcılar Canvas'daki varsayılan e-posta adreslerini değiştirirse, kursa kayıt işlemi, e-posta eşitlemesi Teams.
      - **Benzersiz Kullanıcı Kimliği** , kullanıcının Canvas oturum açma kimliğidir.
      - **SIS Kullanıcı** Kimliği, Öğrenci Bilgi Sistemi'nde (SIS) doldurulan ve kullanıcının profil sayfasında görüntülenebilir kimlik değeridir.
      - **Tümleştirme kimliği** yalnızca SIS içeri aktarmaları yoluyla doldurulur ve kullanıcının profil sayfasında değiştirilebilir. Normalde, bu benzersiz tanımlayıcı kuruluş tarafından sağlanır ve birden çok hesap genelindeki kullanıcıları tanımlamak için hesap güvenleri veya konsorsiyumu durumlarında kullanılır.

   - Son **ek alanı isteğe** bağlıdır ve Canvas öznitelikleriyle Microsoft AAD alanları arasında tam eşleme olmadığınız zaman etki alanını belirtmenize AAD sağlar. Örneğin, Microsoft AAD'daki UPN 'ad' ise Canvas e-postanız 'name@example.edu' ise, son ek alanına '@example.edu' girerek kullanıcıları eşebilirsiniz. Etki alanı, bu alana önceki @ değeriyle girilir.
   - Active Directory Arama Özniteliği, çalışma AAD Canvas özniteliklerinin eş eşlenen alandır. UPN, birincil e-posta adresi veya e-posta diğer adı arasında'ı seçin.

8. Güncelleştirme **ve Güncelleştirme Ayarlar**.

9. Canvas'ın **Microsoft-Teams-Sync-for-Canvas Azure uygulamasına** erişimi onaylamak için Kiracı erişimi ver **bağlantısını** seçin. Microsoft Kimlik Platformu Yönetici onayı Uç Noktasına yeniden yönlendirilecektir.

   ![izinlerini seçin.](media/permissions.png)

   > [!NOTE]
   > Bu adımın, uygulamaları onaylayan bir Microsoft kiracı yöneticisi tarafından gerçekleştiriliyor olması gerekir.

10. Kabul **Et'i seçin**.

## <a name="integrate-teams-classes-lti-in-canvas"></a>Canvas'Teams sınıf LTI'larını tümleştirin

Eşitlemeyi etkinleştirdikten ve Azure uygulamasını onayladikten sonra, Canvas yöneticisi artık Canvas ortamına Teams sınıfları LTI uygulamasını ekleyebilir, böylece Canvas kullanıcı arabiriminin gezintisinde görünür.

**Yeni sınıf Teams LTI uygulamasını Canvas ortamına eklemek için**:

1. Yönetici ayarlarında **Uygulamalar** sekmesinde **,** + **Uygulama'ya seçerek** LTI Teams ekleyin.

   ![dış uygulamalar.](media/external-apps.png)

2. Yapılandırma **Türü için** İstemci Kimliğine **Göre'yi seçin**.

   ![ekle'yi seçin.](media/add-app.png)

3. İstemci **Kimliği için**, LTI **170000000000570** sınıflara Microsoft Teams ve sonra Gönder'i **seçin**.

4. Görüntülenen onayda, uygulama adını (sınıflara göre) doğrulayın Microsoft Teams Yükle'yi **seçin**.

   En Microsoft Teams sınıf LTI uygulaması artık dış uygulamalar listesine eklendi.

## <a name="enabling-the-lti-app-for-canvas-courses"></a>Canvas kursları için LTI uygulamasını etkinleştirme

Bir kurs içinde LTI uygulamasını kullanmak için, Canvas kursunu bir eğitmenin tümleştirmeler eşitlemeyi etkinleştirmesi gerekir. Karşılık gelen bir ekibin oluşturul olması için her kursun bir eğitmen tarafından etkinleştirilmesi gerekir; ekip oluşturma için genel bir mekanizma yoktur. Bu, istenmeyen ekiplerin oluşturulmasını önlemek için önlem amaçlı bir önlem olarak tasarlanmıştır.

Her kurs için LTI [uygulamasını etkinleştirmek](https://support.microsoft.com/topic/use-microsoft-teams-classes-in-your-lms-preview-ac6a1e34-32f7-45e6-b83e-094185a1e78a#ID0EBD=Instructure_Canvas) ve tümleştirme kurulumunu tamamlamak için eğitmenlerinizi eğitimci belgelerine başvurun.
