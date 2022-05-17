---
title: 6. Adım - Eski bir çalışandan Microsoft 365 lisansını kaldırma ve silme
f1.keywords:
- NOCSH
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
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- m365solution-removeemployee
search.appverid:
- BCS160
- MET150
- MOE150
description: Eski bir çalışanın Microsoft 365 lisansını kaldırabilir ve aboneliğinizden silebilir veya lisansı başka bir kullanıcıya atayabilirsiniz.
ms.openlocfilehash: 95f95403a316e176f91c7f120ce5a26487a7a59f
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65436239"
---
# <a name="step-6---remove-and-delete-the-microsoft-365-license-from-a-former-employee"></a>6. Adım - Eski bir çalışandan Microsoft 365 lisansını kaldırma ve silme

Birisi kuruluşunuzdan ayrıldıktan sonra lisans için ödeme yapmak istemiyorsanız, Microsoft 365 lisansını kaldırmanız ve ardından aboneliğinizden silmeniz gerekir. Silmezseniz başka bir kullanıcıya lisans atayabilirsiniz.

Posta kutusuna uyumluluk veya yasal nedenlerle eBulma izinleri verilmiş yetkili kişiler tarafından erişilmesi gerekiyorsa, Exchange Online Plan 2 lisansına (veya Exchange Online Arşivleme sahip Exchange Online Plan 1 lisansına) atanması gerekir  eklenti lisansı) seçerek saklamanın silinmeden önce posta kutusuna uygulanabilmesini sağlar. Kullanıcı hesabı silindikten sonra, kullanıcı hesabıyla ilişkili tüm Exchange Online lisansları yeni bir kullanıcıya atanabilecektir.
  
Lisansı kaldırdığınızda, bu kullanıcının tüm verileri 30 gün süreyle tutulur. Verilere [erişebilir](get-access-to-and-back-up-a-former-user-s-data.md) veya kullanıcı geri dönerse hesabı [geri yükleyebilirsiniz](restore-user.md). 30 gün sonra, kullanıcının tüm verileri (SharePoint Online'da depolanan belgeler hariç) Microsoft 365 kalıcı olarak silinir ve kurtarılamaz.

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.
2. Engellemek istediğiniz çalışanın adını seçin ve ardından **Lisanslar ve Uygulamalar** sekmesini seçin.
3. Kaldırmak istediğiniz lisansların onay kutularını temizleyin ve değişiklikleri **kaydet'i** seçin.

Başka bir kişiyi işe **alana kadar ödediğiniz lisans sayısını azaltmak için** aşağıdaki adımları uygulayın:

1. Yönetim merkezinde <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">Ürünlerinizi</a> **Faturalama** \> sayfasına gidin ve **Ürünler** sekmesini seçin.
2. Lisansları kaldırmak istediğiniz aboneliği seçin.
3. Ayrıntılar sayfasında **Lisansları kaldır'ı** seçin.
4. **Lisansları kaldır** bölmesindeki Yeni miktar'ın altında, **Toplam lisanslar** kutusuna bu abonelik için istediğiniz toplam lisans sayısını girin. Örneğin, 25 lisansınız varsa ve bunlardan birini kaldırmak istiyorsanız 24 girin.
5. **Kaydet**'i seçin.

İşletmenize [başka bir kişi eklediğinizde](add-users.md) , tek bir adımla aynı anda lisans satın almanız istenir!

İşletmeler için Microsoft 365 kullanıcı lisanslarını yönetme hakkında daha fazla bilgi için bkz. [İşletmeler için Microsoft 365'de kullanıcılara lisans atama ve İş için Microsoft 365](../manage/assign-licenses-to-users.md) [kullanıcıların lisanslarını kaldırma](../manage/remove-licenses-from-users.md).
  
## <a name="how-the-deleted-employee-account-affects-skype-for-business"></a>Silinen çalışan hesabının Skype Kurumsal üzerindeki etkisi

Kullanıcının lisansını Office 365'ten kaldırdığınızda, kullanıcıyla ilişkilendirilmiş PSTN çağrı numarası serbest bırakılır. Bu numarayı başka bir kullanıcıya atayabilirsiniz.
  
Kullanıcı bir kuyruk grubunda yer alıyorsa, artık çağrı kuyruğu aracıları için uygun bir hedef olmaktan çıkar. Bu nedenle, kullanıcının çağrı kuyruğuyla ilişkilendirilmiş gruplardan da çıkarılmasını öneririz.

## <a name="set-up-call-forwarding-to-people-in-your-organization"></a>Kuruluşunuzdaki kişilere arama iletmeyi ayarlama

Sonlandırılan çalışanın telefon numarası için arama iletmeyi ayarlamanız gerekiyorsa, arama ilkeleri altındaki arama iletme ayarı, gelen aramaların diğer kullanıcılara iletilebileceği veya aynı anda başka bir kişiyi çaldırabileceği iletmeyi ayarlayabilir. Daha fazla bilgi için bkz[. Microsoft Teams'de ilkeleri çağırma](/microsoftteams/teams-calling-policy).
