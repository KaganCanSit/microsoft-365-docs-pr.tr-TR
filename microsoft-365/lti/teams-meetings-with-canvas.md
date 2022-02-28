---
title: Canvas ile Microsoft Teams kullanma
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
ms.openlocfilehash: 2bd004c86a7d6d2ee5a671d30d98e0af71990a81
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62977691"
---
# <a name="use-microsoft-teams-meetings-with-canvas"></a>Canvas ile Microsoft Teams kullanma

Microsoft Teams toplantıları, eğitimcilerin ve öğrencilerin Learning Yönetim Sistemi (LMS) ve diğer sistemlerde kolayca gezinmelerine yardımcı olan Learning Araçları Birlikte Çalışabilirlik (LTI) Teams. Kullanıcılar, kursuyla ilişkilendirilmiş sınıf ekiplerine doğrudan LMS'lerinin içinden erişim sağlar.

## <a name="prerequisites-before-deployment"></a>Dağıtımdan Önce Önkoşullar

> [!NOTE]
> Geçerli toplantı Teams LTI yalnızca Canvas kullanıcılarını sınırlı bir kapsam Microsoft Azure Active Directory (AAD) ile eşitlemeyi destekler. 
> - Kiracınız Bir Microsoft Eğitim lisansına sahip olmalı.
> - Kullanıcıları Canvas ile Microsoft arasında eşlemek için yalnızca tek bir Microsoft kiracısı kullanılabilir.
> - Grupların çoğaltılmasından School Data Sync için Sınıf Sınıf Teams LTI'yi (SDS) kullanmadan önce SDS'yi kapatmaniz gerekir.

## <a name="microsoft-office-365-admin"></a>Microsoft Office 365 Yöneticisi

Instructure Canvas içinde Microsoft Teams tümleştirmesi yönetmeden önce, Canvas yönetici kurulumunu tamamlamadan önce Canvas'ın **Microsoft-Teams-Sync-for-Canvas** Azure uygulamasının Microsoft Azure kiracınıza kurumunuz Microsoft Office 365 yöneticisi tarafından onaylanması önemlidir.

1. Canvas'ta oturum açma.

2. Genel **gezinti bölmesinde** Yönetici bağlantısını seçin ve sonra da hesabınız'ı seçin.

3. Yönetici gezintisinde, Önce **Ayarlar** sonra Tümleştirmeler **sekmesini** seçin.

![Canvas'Teams Eşitleme Güncelleştirildi png dosyası.](https://user-images.githubusercontent.com/87142492/128552407-78cb28e9-47cf-4026-954d-12dc3553af6f.png)

4. Microsoft kiracı adınızı, oturum açma özniteliğinizi, etki alanı son ekini ve AAD özniteliğinizi girin. Bu alanlar Canvas'ta bu alanları başka kullanıcılarla eşleşen kullanıcılarla Microsoft Azure Active Directory. 
   * Oturum Açma Özniteliği, eşleştirme için kullanılan Canvas kullanıcı özniteliğidir.
   * Son ek alanı isteğe bağlıdır ve Canvas öznitelikleriyle Microsoft AAD alanları arasında tam eşlemeler olmayan bir etki alanı belirtmenize olanak verir. Örneğin, Microsoft AAD'daki UPN'nin 'ad' olduğu sırada Canvas e-postanız 'name@example.edu' ise, son ek alanına 'example.edu' girerek kullanıcıları eşebilirsiniz.
   * Active Directory Arama Özniteliği, Microsoft tarafında Canvas özniteliklerinin eşlenilen alandır. UPN, birincil e-posta adresi veya e-posta diğer adı arasında'ı seçin.

5. Güncelleştirme **ve Ayarlar'yi** seçin.

6. Canvas'ın **Microsoft-Teams-Sync-for-Canvas Azure uygulamasına** erişimi onaylamak için Kiracı erişimi ver **bağlantısını** seçin. Microsoft Kimlik Platformu Yönetici onayı Uç Noktasına yeniden yönlendirilecektir.

   ![izinlerini seçin.](media/permissions.png)

7. Kabul **Et'i seçin**. 

> [!NOTE]
> Eşitleme, LMS iş ortağı tarafından yönetilen ve bir ders düzeyinde üyeliği Microsoft Graph API'lerini kullanan Teams ekibiyle eşitlemek için kullanılan bir işlevdir. Bu öncelikle bir eğitimcinin ders düzeyinde doğru olarak açık bir işlevdir. Ardından, LMS tarafında üyelerin ek ya da silinmesiyle ilgili yapılan üyelik değişikliği, LMS iş ortağı tarafından uygulanan Eşitleme kullanılarak yansıtıldı. Bu işlem bir Eğitimci için etkinleştirilmeden önce bile M365 eğitim enstitüsü yöneticisi, eğitimcilerinin aşağıda bulunan Eşitleme izni kalıcı olarak eşitlemeye erişmelerine izin verir. Bu izinler, eğitimcilerin LMS kursuyla Sınıf ekipleri arasında üyelikleri eşitlemelerine olanak sağlamak için LMS Teams verilenler.

8. Geçiş Microsoft Teams açıp eşitlemeyi etkinleştirme.

   ![teams-sync.](media/teams-sync.png)

## <a name="canvas-admin"></a>Canvas Yöneticisi

LTI 1.3 tümleştirmesi Microsoft Teams için ayarlama.

Canvas Admin olarak, ortamınız içinde en iyi Microsoft Teams LTI uygulamasını eklemeniz gerekir. Uygulama için LTI İstemci Kimliği'ne not edin.

 - Microsoft Teams- 170000000000703

1. Access **Yönetici** **ayarlarıApps** > .

2. En **iyi** LTI uygulamalarını eklemek Teams + Uygulama'ya tıklayın.

   ![dış uygulamalar.](media/external-apps.png)

3. Yapılandırma **türü için İstemci Kimliğine** Göre'yi seçin.

   ![ekle'yi seçin.](media/add-app.png)

4. Sağlanan İstemci Kimliğini girin ve sonra Gönder'i **seçin**.

   Onay için İstemci Kimliği Microsoft Teams toplantı LTI uygulama adını fark edin.

5. **Yükle**’yi seçin.

   En Microsoft Teams LTI uygulaması dış uygulamalar listesine eklenir.

6. Canvas yönetici hesabında geliştirici tuşlarına giderek, devralınan'ı seçerek ve Toplantılarda "açık" ayarını etkinleştirerek Microsoft Teams etkinleştirin.
   
## <a name="enable-for-canvas-courses"></a>Canvas Kursları için Etkinleştirme

LTI'yi bir kurs içinde kullanmak için, Canvas kursunu bir eğitmenin tümleştirmelerin eşitleni etkinleştirmesi gerekir. Her kursun, ilgili bir öğretim üyesinin oluşturulması Teams bir eğitmen tarafından etkinleştirilmesi gerekir; bu çalışma üzerinde genel Teams yoktur. İstenmeyen postaların oluşturulduğunda bu şekilde Teams dikkati önlemektedir.

Her kurs için [LTI'yı etkinleştirmek ve](https://support.microsoft.com/en-us/topic/use-microsoft-teams-classes-in-your-lms-preview-ac6a1e34-32f7-45e6-b83e-094185a1e78a#ID0EBD=Instructure_Canvas) tümleştirme kurulumunu bitirmek için lütfen eğitmenlerinizi eğitimci belgelerine başvurun.
