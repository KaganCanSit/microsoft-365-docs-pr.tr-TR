---
title: Windows 10 cihazlara yönelik uygulama koruma ayarlarını belirleme
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
f1_keywords:
- Win10AppPolicy
- O365E_Win10AppPolicy
- BCS365_Win10AppPolicy
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- M365-identity-device-management
ms.custom:
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- OKR_SMB_M365
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 02e74022-44af-414b-9d74-0ebf5c2197f0
description: Windows 10 cihazlarında uygulama yönetimi ilkesi oluşturmayı ve çalışma dosyalarını nasıl koruyacağınızı öğrenin.
ms.openlocfilehash: 0e1221e533418166b80afd94431414016774f247
ms.sourcegitcommit: bd52f7b662887f552f90c46f69d6a2a42fb66914
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2019
ms.locfileid: "37575788"
---
# <a name="set-application-protection-settings-for-windows-10-devices"></a><span data-ttu-id="b87c1-103">Windows 10 cihazlara yönelik uygulama koruma ayarlarını belirleme</span><span class="sxs-lookup"><span data-stu-id="b87c1-103">Set application protection settings for Windows 10 devices</span></span>

## <a name="create-an-app-management-policy-for-windows-10"></a><span data-ttu-id="b87c1-104">Windows 10 için uygulama yönetimi ilkesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="b87c1-104">Create an app management policy for Windows 10</span></span>

<span data-ttu-id="b87c1-105">Kullanıcılarınızın işle ilgili görevleri gerçekleştirdikleri kişisel Windows 10 cihazları varsa, verilerinizi bu cihazlarda da koruma altına alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b87c1-105">If your users have personal Windows 10 devices on which they perform work tasks, you can protect your data on those devices as well.</span></span>
  
1. <span data-ttu-id="b87c1-106">'deki <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>yönetici merkezine gidin.</span><span class="sxs-lookup"><span data-stu-id="b87c1-106">Go to the admin center at <a href="https://go.microsoft.com/fwlink/p/?linkid=837890" target="_blank">https://admin.microsoft.com</a>.</span></span> 
    
2. <span data-ttu-id="b87c1-107">Sol daki gezinmede, **Aygıt** \> **İlkeleri** \> **Ekle'yi**seçin.</span><span class="sxs-lookup"><span data-stu-id="b87c1-107">On the left nav, choose **Devices** \> **Policies** \> **Add**.</span></span>

3. <span data-ttu-id="b87c1-108">**İlke ekle** bölmesinde bu ilke için benzersiz bir ad girin.</span><span class="sxs-lookup"><span data-stu-id="b87c1-108">On the **Add policy** pane, enter a unique name for this policy.</span></span> 
    
4. <span data-ttu-id="b87c1-109">**İlke türü**'nün altında **Windows 10 için Uygulama Yönetimi**'ni seçin.</span><span class="sxs-lookup"><span data-stu-id="b87c1-109">Under **Policy type**, choose **Application Management for Windows 10**.</span></span>
    
5. <span data-ttu-id="b87c1-110">**Cihaz türü altında,** **Kişisel** veya **Şirket Owned**seçin.</span><span class="sxs-lookup"><span data-stu-id="b87c1-110">Under **Device type**, choose either **Personal** or **Company Owned**.</span></span>
    
6. <span data-ttu-id="b87c1-111">**İş dosyalarını şifrele** seçeneği otomatik olarak açılır.</span><span class="sxs-lookup"><span data-stu-id="b87c1-111">The **Encrypt work files** is turned on automatically.</span></span> 
    
7. <span data-ttu-id="b87c1-112">Kullanıcıların çalışma dosyalarını kendi bilgisayarlarına kaydetmelerini istemiyorsanız, **Kullanıcıların şirket verilerini kişisel dosyalara kopyalamasını engelle ve çalışma dosyalarını OneDrive İş'e kaydetmelerini zorla** ilkesini **Açık** olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b87c1-112">Set **Prevent users from copying company data to personal files and force them to save work files to OneDrive for Business** to **On** if you don't want the users to save work files on their PC.</span></span> 
    
9. <span data-ttu-id="b87c1-113">**Windows cihazlarındaki verileri kurtar** seçeneğini genişletin; bu seçeneği **Açık** duruma getirmeniz önerilir.</span><span class="sxs-lookup"><span data-stu-id="b87c1-113">Expand **Recover data on Windows devices** and it is recommended that you turn it **On**.</span></span>
    
    <span data-ttu-id="b87c1-p101">Veri Kurtarma Aracısı sertifikasının konumuna göz atabilmeniz için, önce bir sertifika oluşturmanız gerekir. Yönergeler için bkz. [Şifreleme Dosya Sistemi (EFS) Veri Kurtarma Aracısı (DRA) sertifikasını oluşturma ve doğrulama](https://go.microsoft.com/fwlink/p/?linkid=853700).</span><span class="sxs-lookup"><span data-stu-id="b87c1-p101">Before you can browse to the location of the Data Recovery Agent certificate, you have to first create one. For instructions see, [Create and verify an Encrypting File System (EFS) Data Recovery Agent (DRA) certificate](https://go.microsoft.com/fwlink/p/?linkid=853700).</span></span>
    
    <span data-ttu-id="b87c1-p102">Varsayılan olarak iş dosyalarınız, cihazda depolanan ve kullanıcının profili ile ilişkilendirilmiş bir gizli anahtar kullanılarak şifrelenir. Yalnızca kullanıcı dosyanın şifresini çözebilir ve dosyayı açabilir. Bununla birlikte, cihaz kaybolursa veya kullanıcı kaldırılırsa, dosya şifrelenmiş halde kalabilir. Dosyanın şifresini çözmek için yönetici, Veri Kurtarma Aracısı (DRA) sertifikası kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="b87c1-p102">By default, work files are encrypted using a secret key that is stored on the device and associated with the user's profile. Only the user can open and decrypt the file. However, if a device is lost or a user is removed, a file can be stuck in an encrypted state. The Data Recovery Agent (DRA) certificate can be used by an admin to decrypt the file.</span></span>
    
    ![Browse to Data Recovery Agent certificate.](media/7d7d664f-b72f-4293-a3e7-d0fa7371366c.png)
  
10. <span data-ttu-id="b87c1-p103">Listelenen tüm uygulamalardaki dosyaların korunduğundan emin olmak için başka etki alanları veya SharePoint Online konumları eklemek istiyorsanız, **Ek ağ ve bulut konumlarını koru** seçeneğini genişletin. Alanlara birden çok öğe girmeniz gerekiyorsa, öğeler arasında noktalı virgül (;) kullanın.</span><span class="sxs-lookup"><span data-stu-id="b87c1-p103">Expand **Protect additional network and cloud locations** if you want to add additional domains or SharePoint Online locations to make sure that files in all the listed apps will be protected. If you need to enter more than one item for either field, use a semicolon (;) between the items.</span></span>
    
    ![Expand Protect additional network and cloud locations, and enter domains or SharePoint Online sites you own.](media/7afaa0c7-ba53-456d-8c61-312c45e09625.png)
  
11. <span data-ttu-id="b87c1-p104">Next decide **Who will get these settings?** If you don't want to use the default **All Users** security group, choose **Change**, choose the security groups who will get these settings \> **Select**.</span><span class="sxs-lookup"><span data-stu-id="b87c1-p104">Next decide **Who will get these settings?** If you don't want to use the default **All Users** security group, choose **Change**, choose the security groups who will get these settings \> **Select**.</span></span>
    
12. <span data-ttu-id="b87c1-126">Son olarak, **Ekle**'yi seçerek ilkeyi kaydedin ve cihazlarınıza atayın.</span><span class="sxs-lookup"><span data-stu-id="b87c1-126">Finally, choose **Add** to save the policy, and assign it to devices.</span></span> 