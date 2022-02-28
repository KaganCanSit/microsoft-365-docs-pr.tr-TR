---
title: Kurumsal test ortamı için ağ Microsoft 365 ayrıcalıklı erişim yönetimi
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-security-compliance
ms.custom: Ent_TLGs
description: Kurumsal test ortamı için test test ortamınıza erişimin ayrıcalıklı bir şekilde Microsoft 365 için bu Test Laboratuvarı Kılavuzunu kullanın.
ms.openlocfilehash: 424b7c09a89b20d134654293a1e9c9abd69d6ff2
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62988624"
---
# <a name="privileged-access-management-for-your-microsoft-365-for-enterprise-test-environment"></a>Kurumsal test ortamı için ağ Microsoft 365 ayrıcalıklı erişim yönetimi

*Bu Test Laboratuvarı Kılavuzu, hem kurumsal hem de Microsoft 365 test ortamları için Office 365 Kurumsal kullanılabilir.*

Bu makalede, kurumsal test ortamınız için ağ ağ güvenliğinizi artırmak üzere ayrıcalıklı erişim Microsoft 365 yapılandırmanız açıklanmıştır.

Ayrıcalıklı erişim yönetimini yapılandırmak üç aşama içerir:

- [Aşama 1: Kurumsal test Microsoft 365 yapınızı oluşturma](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Aşama 2: Ayrıcalıklı erişim yönetimini yapılandırma](#phase-2-configure-privileged-access-management)
- [Aşama 3: Yükseltilmiş ve ayrıcalıklı görevler için onay gerektir olduğunu doğrulama](#phase-3-verify-that-approval-is-required-for-elevated-and-privileged-tasks)

![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınına Microsoft 365 görsel bir harita için Kurumsal Test Laboratuvarı Kılavuzu Yığını [için Microsoft 365'e gidin](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Aşama 1: Kurumsal test Microsoft 365 yapınızı oluşturma

Ayrıcalıklı erişim yönetimini en düşük gereksinimlerle basit bir şekilde yapılandırmak için, Basit temel [yapılandırma'daki yönergeleri izleyin](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Sanal bir kuruluşta ayrıcalıklı erişim yönetimini yapılandırmak için, Doğrudan kimlik doğrulama'daki [yönergeleri izleyin](pass-through-auth-m365-ent-test-environment.md).
  
>[!NOTE]
>Ayrıcalıklı erişim yönetimini sınamak, Active Directory Etki Alanı Hizmetleri ormanı için İnternet ve dizin eşitlemesi bağlantılı sanal bir intranet içeren sanal kurumsal test ortamını gerektirmez. Burada, ayrıcalıklı erişim yönetimini test etmek ve tipik bir kuruluşu temsil eden bir ortamda bu erişimle denemeler yapmak için bir seçenek olarak sağlanır.

## <a name="phase-2-configure-privileged-access-management"></a>Aşama 2: Ayrıcalıklı erişim yönetimini yapılandırma

Bu aşamada bir onaylayanlar grubu yapılandırarak kurumsal test ortamınız için Microsoft 365 yönetimine olanak tanıyın. Ek ayrıntılar ve ayrıcalıklı erişim yönetimine genel bakış için bkz. [Ayrıcalıklı erişim yönetimi](../compliance/privileged-access-management-overview.md).

Kuruluşta ayrıcalıklı erişimi ayarlamak ve kullanmak için aşağıdaki adımları uygulayın.

#### <a name="step-1-create-an-approvers-group"></a>[1. Adım: Onaylayan grubu oluşturma](../compliance/privileged-access-management-configuration.md#step-1-create-an-approvers-group)

Ayrıcalıklı erişimi kullanmaya başlamadan önce, yükseltilmiş ve ayrıcalıklı görevlere erişim için gelen istekler için kimlerin onay yetkisine sahip olacaklarını belirleme. Onaylayanlar grubunun parçası olan tüm kullanıcılar erişim isteklerini onaylar. Ayrıcalıklı erişimi kullanmak için, bu konumda posta özellikli bir güvenlik grubu Microsoft 365. Test ortamınıza yeni güvenlik grubunu "Ayrıcalıklı Erişim Onaylayanlar" olarak ad girin ve önceki test laboratuvarı kılavuzu adımlarında daha önce oluşturulmuş olan "Kullanıcı 3"ü ekleyin.

#### <a name="step-2-enable-privileged-access"></a>[2. Adım: Ayrıcalıklı erişimi etkinleştirme](../compliance/privileged-access-management-configuration.md#step-2-enable-privileged-access)

Ayrıcalıklı erişimin, Microsoft 365'da varsayılan onaylayan grupla açıkça açık olarak açık olması ve ayrıca erişim yönetimi erişim denetimi dışında tutmak istediğiniz bir dizi sistem hesabı içermesi gerekir. Bu kılavuzun 3. Aşamasına başlamadan önce, organizasyonda ayrıcalıklı erişimi etkinleştirmeye emin olun.

## <a name="phase-3-verify-that-approval-is-required-for-elevated-and-privileged-tasks"></a>Aşama 3: Yükseltilmiş ve ayrıcalıklı görevler için onay gerektir olduğunu doğrulama

Bu aşamada, ayrıcalıklı erişim ilkesi'nin çalıştığını ve kullanıcıların tanımlı yükseltilmiş ve ayrıcalıklı görevleri yürütmek için onay gerektirmelerini doğrulayın.

### <a name="test-the-ability-to-execute-a-task-not-defined-in-a-privileged-access-policy"></a>Ayrıcalıklı erişim ilkesinde tanımlanmamış bir görevi yürütme becerisini test etme

İlk olarak, Exchange ortamınıza Exchange Rol Yönetimi rolüyle yapılandırılmış bir kullanıcının kimlik bilgileriyle Exchange Yönetimi PowerShell'e bağlanın ve yeni bir Günlük kuralı oluşturma girişiminde bulundurabilirsiniz. [New-JournalRule](/powershell/module/exchange/new-journalrule) görevi şu anda, kuruluşu için ayrıcalıklı bir erişim ilkesinde tanımlanmamıştır.

1. Yerel bilgisayarınızda, test ortamınız için Exchange Online Rol Yönetimi rolüne sahip kimlik bilgilerini kullanarak **Microsoft Corporation** >  **Microsoft Exchange Online uzak PowerShell** Modülü'nde Exchange Uzak PowerShell Modülü'nde oturum açın.
2. PowerShell Exchange'de, organizasyonunız için yeni bir Günlük kuralı oluşturun:

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule1" -Recipient joe@contoso.onmicrosoft.com -JournalEmailAddress barbara@adatum.com -Scope Global -Enabled $true
   ```

3. Yeni Günlük Kuralının PowerShell Yönetimi'nde başarıyla Exchange görünümü.

### <a name="create-a-new-privileged-access-policy-for-the-new-journalrule-task"></a>Hızlı erişim görevi için yeni bir ayrıcalıklı New-JournalRule ilkesi oluşturma

>[!NOTE]
>Bu kılavuzun Aşama 2'den 1. ve 2. Adımlarını henüz tamamlanmadıysanız, test ortamınıza ayrıcalıklı erişimi etkinleştirmek için onaylayanların "Ayrıcalık Erişim Onaylayanlar" adlı grubunu oluşturmak için adımları takip edin.

1. Test ortamınız için [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) ve Rol Yönetimi rolü Exchange kimlik bilgilerini kullanarak oturum açma.
2. Yönetim Merkezi'nde Ayarlar  > **Security &** **PrivacyPrivileged** >  access'e gidin.
3. Erişim **ilkelerini ve isteklerini yönet'i seçin**.
4. **İlkeleri yapılandır'ı** ve sonra İlke **ekle'yi seçin**.
5. Açılan alanlarda, aşağıdaki değerleri seçin veya girin:

    **İlke türü**: Görev **İlkesi kapsamı**: Exchange **Policy adı**: Yeni Günlük Kuralı **Onay türü**: El ile **Onay grubu**: Ayrıcalıklı Erişim Onaylayanlar  

6. **Oluştur'a** ve sonra Kapat'a **seçin**. İlkenin tam olarak yapılandırılması ve etkinleştirilmesi birkaç dakika sürebilir. Onay gereksinimini test etmek için sonraki adımda ilkenin tam olarak etkinleştirilmesine izin verildiğinden emin olun.

### <a name="test-approval-requirement-for-the-new-journalrule-task-defined-in-a-privileged-access-policy"></a>Ayrıcalıklı bir erişim ilkesinde New-JournalRule görev için onay gereksinimini test etmek

1. Yerel bilgisayarınızda, test ortamınız için Exchange Online Rol Yönetimi rolüne sahip kimlik bilgilerini kullanarak **Microsoft Corporation** >  **Microsoft Exchange Online uzak PowerShell** Modülü'nde Exchange Uzak PowerShell Modülü'nde oturum açın.

2. PowerShell Exchange'de, organizasyonunız için yeni bir Günlük kuralı oluşturun:

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
   ```

3. PowerShell Yönetimi'nin "yetersiz Exchange" hatasını görüntüleme:

   ```ExchangeManagementPowerShell
   Insufficient permissions. Please raise an elevated access request for this task.
       + CategoryInfo          : NotSpecified: (:) [], LocalizedException
       + FullyQualifiedErrorId : [Server=CY1PR00MB0220,RequestId=7b8c7470-ddd0-4528-a01e-5e20ecc9bd54,TimeStamp=9/19/2018
       7:38:34 PM] [FailureCategory=Cmdlet-LocalizedException] 882BD051
       + PSComputerName        : outlook.office365.com
   ```

### <a name="request-access-to-create-a-new-journal-rule-using-the-new-journalrule-task"></a>Özel görev kullanarak yeni bir Günlük Kuralı oluşturmak için New-JournalRule isteğinde New-JournalRule isteğinde

1. Test ortamınız için [Microsoft 365 yönetim merkezi](https://admin.microsoft.com) ve Rol Yönetimi rolü Exchange kimlik bilgilerini kullanarak oturum açma.

2. Yönetim Merkezi'nde Ayarlar  > **Security &** **PrivacyPrivileged** >  access'e gidin.

3. Erişim **ilkelerini ve isteklerini yönet'i seçin**.

4. Yeni **istek'i seçin**. Açılan alanlardan, organizasyonunız için uygun değerleri seçin:

    **İstek türü**: Görev **İsteği kapsamı**: Exchange **Yazdır**: Yeni Günlük Kuralı Süresi **(saat)****: 2 Açıklama**: Yeni bir Günlük Kuralı oluşturmak için izin isteği  

5. **Kaydet'i** ve sonra Kapat'ı **seçin**. İsteğiniz, e-posta yoluyla onaylayan grubuna gönderilir.

### <a name="approve-privileged-access-request-for-the-creation-of-a-new-journal-rule"></a>Yeni Günlük Kuralı oluşturmak için ayrıcalıklı erişim isteğini onaylama

1. Test [ortamı Microsoft 365 yönetim merkezi 3](https://admin.microsoft.com) Kullanıcı'nın kimlik bilgilerini kullanarak oturum açma (test ortamınıza "Ayrıcalıklı Erişim Onaylayanlar" güvenlik grubunun üyesi).

2. Yönetim Merkezi'nde Ayarlar  > **Security &** **PrivacyPrivileged** >  access'e gidin.

3. Erişim **ilkelerini ve isteklerini yönet'i seçin**.

4. Bekleyen isteği seçin ve sonra yeni **bir Günlük Kuralı oluşturmak** üzere kullanıcı hesabına erişim vermek için Onayla'ya seçin. Hesap (istekte olan kullanıcı) onay verilmiş bir e-posta onayı alır.

### <a name="test-creating-a-new-journal-rule-with-privileged-access-approved-for-the-new-journalrule-task"></a>Bu görev için ayrıcalıklı erişimle yeni bir Günlük Kuralı New-JournalRule test

1. Yerel bilgisayarınızda, test ortamınız için Exchange Online Rol Yönetimi rolüne sahip kimlik bilgilerini kullanarak **Microsoft Corporation** >  **Microsoft Exchange Online uzak PowerShell** Modülü'nde Exchange Uzak PowerShell Modülü'nde oturum açın.

2. PowerShell Exchange'de, organizasyonunız için yeni bir Günlük kuralı oluşturun:

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
   ```

3. Yeni Günlük Kuralının PowerShell Yönetimi'nde başarıyla Exchange görünümü.

## <a name="next-step"></a>Sonraki adım

Test [ortamınıza ek](m365-enterprise-test-lab-guides.md#information-protection) bilgi koruma özelliklerini ve özelliklerini keşfedin.

## <a name="see-also"></a>Ayrıca bkz.

- [Microsoft 365 Test Laboratuvarı Kılavuzları için kılavuzlar](m365-enterprise-test-lab-guides.md)
- [Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)
- [Microsoft 365 belgeleri için belgeler](/microsoft-365-enterprise/)
