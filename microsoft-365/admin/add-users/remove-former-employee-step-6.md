---
title: 6. Adım - Eski bir Microsoft 365 lisansını kaldırma ve silme
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
description: Eski bir çalışanın lisansını Microsoft 365 için bu adımları izleyin.
ms.openlocfilehash: 52ab851c88d05c33de58d28d566a46b5e8b1710b
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2022
ms.locfileid: "63019451"
---
# <a name="step-6---remove-the-microsoft-365-license-from-a-former-employee"></a>6. Adım - Eski Microsoft 365 kullanıcı lisansını kaldırma

Birisi organizasyondan ayrıldığında lisans için ödeme yapmak istemiyorsanız bu kişinin Microsoft 365 lisansını kaldırmanız ve sonra aboneliğiniz üzerinden silmeniz gerekir. Silmedığınız bir lisansı başka bir kullanıcıya attebilirsiniz.

Posta kutusuna uyumluluk veya yasal nedenlerle eBulma izinleri verilmiş yetkili kişiler tarafından erişilebilir olması gerekirse, posta kutusuna bir Exchange Online Plan 2 lisansı (veya başka bir kullanıcıyla birlikte Exchange Online Plan 1 lisansı) atan Exchange Online Arşivleme  eklenti lisansını kullanabilirsiniz. Böylelikle, posta kutusu silinmeden önce posta kutusuna tutma uygulanabilir. Kullanıcı hesabı silindikten sonra, Exchange Online hesabıyla ilişkilendirilmiş tüm lisanslar yeni bir kullanıcıya atanacak.
  
Lisansı kaldırdığınızda, bu kullanıcının tüm verileri 30 gün süreyle tutulur. Verilere [erişebilir](get-access-to-and-back-up-a-former-user-s-data.md) veya kullanıcı geri dönerse hesabı [geri yükleyebilirsiniz](restore-user.md). 30 gün sonra, kullanıcının tüm verileri (SharePoint Online'da depolanan belgeler dışında) Microsoft 365 kalıcı olarak silinir ve kurtarılamaz.

1. Yönetici merkezinde, **Kullanıcılar** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Etkin kullanıcılar</a> sayfasına gidin.
2. Engellemek istediğiniz çalışanın adını seçin ve sonra Lisanslar ve **Uygulamalar sekmesini** seçin.
3. Kaldırmak istediğiniz lisansların onay kutularını temizleyin ve ardından Değişiklikleri **kaydet'i seçin**.

**Başka birini işe alıncaya kadar ödeme yaptığınız lisans** sayısını azaltmak için aşağıdaki adımları izleyin:

1. Yönetim merkezinde Ürünlerinizi Faturalama **sayfasına** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">gidin</a> ve **Ürünler sekmesini seçin** .
2. Lisansları kaldırmak istediğiniz aboneliği seçin.
3. Ayrıntılar sayfasında Lisansları **kaldır'ı seçin**.
4. Lisansları **kaldır** bölmesindeki Yeni miktar'ın altında, Toplam lisanslar  kutusuna bu abonelik için istediğiniz toplam lisans sayısını girin. Örneğin, 25 lisansınız varsa ve bunlardan birini kaldırmak için 24 girin.
5. **Kaydet**'i seçin.

İşletmenize [başka bir](add-users.md) kişi eklerken, aynı anda yalnızca bir adımla lisans satın almak istenir!

Microsoft 365 İş için kullanıcı lisanslarını yönetme hakkında daha fazla bilgi için bkz. [Microsoft 365](../manage/assign-licenses-to-users.md) İş'te kullanıcılara lisans atama ve Microsoft 365 İş'te kullanıcılardan lisans [atamalarını iptal.](../manage/remove-licenses-from-users.md)
  
## <a name="how-the-deleted-employee-account-affects-skype-for-business"></a>Silinen çalışan hesabının Skype Kurumsal üzerindeki etkisi

Kullanıcının lisansını Office 365'ten kaldırdığınızda, kullanıcıyla ilişkilendirilmiş PSTN çağrı numarası serbest bırakılır. Bu numarayı başka bir kullanıcıya atayabilirsiniz.
  
Kullanıcı bir kuyruk grubunda yer alıyorsa, artık çağrı kuyruğu aracıları için uygun bir hedef olmaktan çıkar. Bu nedenle, kullanıcının çağrı kuyruğuyla ilişkilendirilmiş gruplardan da çıkarılmasını öneririz.

## <a name="set-up-call-forwarding-to-people-in-your-organization"></a>Kuruluşta kişi arama iletmeyi ayarlama

Sonlandırılan çalışanın telefon numarası için arama iletmeyi ayarlamanız gerekirse, arama ilkelerinin altındaki arama iletme ayarı, gelen aramaların diğer kullanıcılara iletilmelerinin bulunduğu iletmeyi veya aynı anda başka bir kişiyi çaldırma ayarını da yapılandırabilirsiniz. Daha fazla bilgi için bkz[. Microsoft Teams](/microsoftteams/teams-calling-policy).
