---
title: Office 365 için Microsoft Defender kullanıcı etiketleri
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 12/17/2021
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Yöneticiler, Office 365 için Microsoft Defender Plan 2'de kullanıcı etiketleri olan belirli kullanıcı gruplarını tanımlamayı öğrenebilir. Etiket filtreleme, etiketlenen kullanıcıları hızlı bir şekilde tanımlamak için Office 365 için Microsoft Defender uyarılarda, raporlarda ve araştırmalarda kullanılabilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e7b9584b41ded7edd28fb1501ee4e5c3a1febd74
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/09/2022
ms.locfileid: "65286416"
---
# <a name="user-tags-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender kullanıcı etiketleri

Kullanıcı etiketleri, [Office 365 için Microsoft Defender'deki](defender-for-office-365.md) belirli kullanıcı gruplarının tanımlayıcılarıdır. İki tür kullanıcı etiketi vardır:

- **Sistem etiketleri**: Şu anda tek sistem etiketi türü [Öncelik hesaplarıdır](../../admin/setup/priority-accounts.md) .
- **Özel etiketler**: Bu kullanıcı etiketlerini kendiniz oluşturursunuz.

Kuruluşunuzda Office 365 için Defender Plan 2 (aboneliğinize dahil veya eklenti olarak) varsa, öncelik hesapları etiketini kullanmanın yanı sıra özel kullanıcı etiketleri de oluşturabilirsiniz.

> [!NOTE]
> Şu anda yalnızca posta kutusu kullanıcılarına kullanıcı etiketleri uygulayabilirsiniz.

Kullanıcılara sistem etiketleri veya özel etiketler uyguladıktan sonra, bu etiketleri uyarılarda, raporlarda ve araştırmalarda filtre olarak kullanabilirsiniz:

- [Uyarılar](alerts.md)
- [Özel uyarı ilkeleri](../../compliance/alert-policies.md#viewing-alerts)
- [Tehdit Gezgini ve gerçek zamanlı algılamalar](threat-explorer.md)
- [Güvenliği aşılmış kullanıcı raporu](view-email-security-reports.md#compromised-users-report)
- [E-posta varlık sayfası](mdo-email-entity-page.md#other-innovations)
- [Tehdit koruması durum raporu](view-email-security-reports.md#threat-protection-status-report)
- [En çok gönderenler ve alıcılar raporu](view-email-security-reports.md#top-senders-and-recipients-report)
- [Saldırı benzetimi](attack-simulation-training.md#target-users)
- [Kampanya Görünümleri](campaigns.md)
- [Yönetici ve kullanıcı gönderimleri](admin-submission.md)
- [Karantina](quarantine.md)
- Öncelik hesapları için, Exchange yönetim merkezinde (EAC) [öncelik hesapları için e-posta sorunları raporunu](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report) kullanabilirsiniz.

Bu makalede, Microsoft 365 Defender portalında kullanıcı etiketlerini yapılandırma açıklanmaktadır. Microsoft 365 Defender portalında kullanıcı etiketlerini yönetmek için cmdlet yoktur.

Kullanıcı etiketlerinin yüksek etkili kullanıcı hesaplarını korumaya yardımcı olan stratejinin bir parçası olduğunu görmek için bkz. [Microsoft 365'da öncelik hesapları için güvenlik önerileri](security-recommendations-for-priority-accounts.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını adresinde <https://security.microsoft.com>açarsınız. Doğrudan **Kullanıcı etiketleri** sayfasına gitmek için kullanın <https://security.microsoft.com/securitysettings/userTags>.

- Bu makaledeki yordamları gerçekleştirebilmeniz için önce Microsoft 365 Defender portalında size izinler atanmalıdır:
  - Özel kullanıcı etiketleri oluşturmak, değiştirmek ve silmek için **Kuruluş Yönetimi** veya **Güvenlik Yöneticisi** rol gruplarının üyesi olmanız gerekir.
  - Öncelik Hesabı sistem etiketine üye eklemek ve kaldırmak için **Güvenlik Yöneticisi'nin** ve **Exchange Yönetici** rol gruplarının üyesi olmanız gerekir.
  - Mevcut özel kullanıcı etiketlerine üye eklemek ve kaldırmak için **Kuruluş Yönetimi** veya **Güvenlik Yöneticisi** rol gruplarının üyesi olmanız gerekir.
  - Kullanıcı etiketlerine salt okunur erişim için **Genel Okuyucu**, **Güvenlik operatörü** veya **Güvenlik Okuyucusu** rol gruplarının üyesi olmanız gerekir.

  Daha fazla bilgi için bkz. [Microsoft 365 Defender portalında İzinler](permissions-microsoft-365-security-center.md).

  > [!NOTE]
  >
  > - kullanıcıları Microsoft 365 yönetim merkezi karşılık gelen Azure Active Directory rolüne eklemek, kullanıcılara Microsoft 365 Defender portalında gerekli izinleri _ve_ Microsoft 365'deki diğer özellikler için izinleri verir. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  >
  > - Kullanıcı etiketi yönetimi, **Etiket Okuyucusu** ve **Etiket Yöneticisi** rolleri tarafından denetlenilir.

- Ayrıca Microsoft 365 yönetim merkezi öncelik hesaplarını yönetebilir ve izleyebilirsiniz. Yönergeler için bkz. [Öncelik hesaplarını yönetme ve izleme](../../admin/setup/priority-accounts.md).

- _Ayrıcalıklı hesapların (yönetici hesaplarının_) güvenliğini sağlama hakkında bilgi için [bu konuya](/azure/architecture/framework/security/critical-impact-accounts) bakın.

## <a name="use-the-microsoft-365-defender-portal-to-create-user-tags"></a>Kullanıcı etiketleri oluşturmak için Microsoft 365 Defender portalını kullanma

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**Ayarlar** \> **E-posta & işbirliği** \> **Kullanıcı etiketleri'ne** gidin. Doğrudan **Kullanıcı etiketleri** sayfasına gitmek için kullanın <https://security.microsoft.com/securitysettings/userTags>.

2. **Kullanıcı etiketleri** sayfasında Etiket oluştur simgesine tıklayın![.](../../media/m365-cc-sc-create-icon.png) **Etiket oluşturun**.

3. **Etiket oluşturma** sihirbazı yeni bir açılır pencerede açılır. **Etiket tanımla** sayfasında aşağıdaki ayarları yapılandırın:
   - **Ad**: Etiket için benzersiz, açıklayıcı bir ad girin. Bu, göreceğiniz ve kullanacağınız değerdir. Bir etiketi oluşturduktan sonra yeniden adlandıramazsınız.
   - **Açıklama**: Etiket için isteğe bağlı bir açıklama girin.

   İşiniz bittiğinde **İleri'ye** tıklayın.

4. **Üye ata** sayfasında aşağıdaki adımlardan birini yapın:
   - Üye ekle simgesine tıklayın ![.](../../media/m365-cc-sc-create-icon.png) **Üye ekleyin**. Görüntülenen açılır öğede, tek tek kullanıcıları veya grupları eklemek için aşağıdaki adımlardan herhangi birini yapın:
     - Kutuya tıklayın ve listeyi kaydırarak bir kullanıcı veya grup seçin.
     - Kutuya tıklayın ve listeyi filtrelemek ve bir kullanıcı veya grup seçmek için yazmaya başlayın.
     - Ek değerler eklemek için kutuda boş bir alana tıklayın.
     - Tek tek girdileri kaldırmak için ![Girdiyi kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) öğesini seçin.
     - Tüm girişleri kaldırmak için Girdiyi kaldır simgesine tıklayın ![.](../../media/m365-cc-sc-remove-selection-icon.png) kutusunun altındaki **Seçili nn kullanıcıları ve nn grupları** öğesinde.

     İşiniz bittiğinde **Ekle'ye** tıklayın.

     **Üye ata** sayfasına geri döndüğünüzde Sil simgesine tıklayarak ![da girişleri kaldırabilirsiniz.](../../media/m365-cc-sc-delete-icon.png) öğesini seçin.

   - Kullanıcıların veya grupların e-posta adreslerini içeren bir metin dosyası seçmek için **İçeri Aktar'a** tıklayın. Metin dosyasının satır başına bir girdi içerdiğinden emin olun.

   İşiniz bittiğinde **İleri'ye** tıklayın.

5. Görüntülenen **Etiketi gözden geçir** sayfasında ayarlarınızı gözden geçirin. Bölümün içindeki ayarları değiştirmek için her bölümde **Düzenle'yi** seçebilirsiniz. Ya da **Geri'ye** tıklayabilir veya sihirbazdaki belirli bir sayfayı seçebilirsiniz.

   İşiniz bittiğinde **Gönder'e** ve ardından **Bitti'ye** tıklayın.

## <a name="use-the-microsoft-365-defender-portal-to-view-user-tags"></a>Kullanıcı etiketlerini görüntülemek için Microsoft 365 Defender portalını kullanma

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**Ayarlar** \> **E-posta & işbirliği** \> **Kullanıcı etiketleri'ne** gidin. Doğrudan **Kullanıcı etiketleri** sayfasına gitmek için kullanın <https://security.microsoft.com/securitysettings/userTags>.

2. **Kullanıcı etiketleri** sayfasında, kullanıcı etiketleri listesinde aşağıdaki özellikler görüntülenir:

   - **Etiket**: Kullanıcı etiketinin adı. Bunun yerleşik **Öncelik hesabı** sistem etiketini içerdiğini unutmayın.
   - **Uygulandığı** yer: Üye sayısı
   - **Son değiştirme**
   - **Oluşturma tarihi:**

3. Ada tıklayarak bir kullanıcı etiketi seçtiğinizde, ayrıntılar açılır öğede görüntülenir.

## <a name="use-the-microsoft-365-defender-portal-to-modify-user-tags"></a>Kullanıcı etiketlerini değiştirmek için Microsoft 365 Defender portalını kullanma

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**Ayarlar** \> **E-posta & işbirliği** \> **Kullanıcı etiketleri'ne** gidin. Doğrudan **Kullanıcı etiketleri** sayfasına gitmek için kullanın <https://security.microsoft.com/securitysettings/userTags>.

2. **Kullanıcı etiketleri** sayfasında, listeden kullanıcı etiketini seçin ve etiketi düzenle simgesine tıklayın![.](../../media/m365-cc-sc-edit-icon.png) **Etiketi düzenle'yi seçin**.

3. Görüntülenen ayrıntılar açılır penceresinde, bu makalenin önceki bölümlerinde yer alan [Microsoft 365 Defender portalını kullanarak kullanıcı etiketleri oluşturma](#use-the-microsoft-365-defender-portal-to-create-user-tags) bölümünde açıklandığı gibi aynı sihirbaz ve ayarlar sağlanır.

   **Notlar**:

   - **Etiket tanımla** sayfası yerleşik **Öncelik hesabı** sistem etiketi için kullanılamaz, bu nedenle bu etiketi yeniden adlandıramaz veya açıklamayı değiştiremezsiniz.
   - Özel etiketi yeniden adlandıramazsınız, ancak açıklamayı değiştirebilirsiniz.

## <a name="use-the-microsoft-365-defender-portal-to-remove-user-tags"></a>Kullanıcı etiketlerini kaldırmak için Microsoft 365 Defender portalını kullanma

> [!NOTE]
> Yerleşik **Öncelik hesabı** sistem etiketini kaldıramazsınız.

1. konumundaki Microsoft 365 Defender portalında <https://security.microsoft.com>**Ayarlar** \> **E-posta & işbirliği** \> **Kullanıcı etiketleri'ne** gidin. Doğrudan **Kullanıcı etiketleri** sayfasına gitmek için kullanın <https://security.microsoft.com/securitysettings/userTags>.

2. **Kullanıcı etiketleri** sayfasında, listeden kullanıcı etiketini seçin ve ardından Etiketi sil simgesine tıklayın![.](../../media/m365-cc-sc-delete-icon.png) **Etiketi silin**.

3. Görüntülenen onay iletişim kutusundaki uyarıyı okuyun ve ardından **Evet, kaldır'a** tıklayın.

## <a name="more-information"></a>Daha fazla bilgi

[Office 365 için Microsoft Defender'da öncelik hesaplarını yapılandırma ve gözden geçirme](configure-review-priority-account.md)
