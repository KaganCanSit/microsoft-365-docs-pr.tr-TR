---
title: Office 365 için Microsoft Defender'daki kullanıcı Office 365
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
description: Yöneticiler, Plan 2'de yer alan Microsoft Defender'da kullanıcı etiketleriyle belirli kullanıcı Office 365 öğrenebilir. Etiket filtreleme, etiketli kullanıcıları hızla tanımlamak için Office 365 Için Microsoft Defender'daki uyarılar, raporlar ve soruşturmalar genelinde kullanılabilir.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f6a5262b184e5785695d73be32080adb8b44109c
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021784"
---
# <a name="user-tags-in-microsoft-defender-for-office-365"></a>Office 365 için Microsoft Defender'daki kullanıcı Office 365

Kullanıcı etiketleri, Microsoft Defender'daki kullanıcı gruplarının [tanımlayıcılarıdır ve Office 365](defender-for-office-365.md). İki tür kullanıcı etiketi vardır:

- **Sistem etiketleri**: Şu anda [, tek](../../admin/setup/priority-accounts.md) sistem etiketi türü Öncelik hesaplarıdır.
- **Özel etiketler**: Bu kullanıcı etiketlerini kendiniz oluştursunuz.

Organizasyonda Plan 2 için Defender Office 365 (aboneliğinize veya eklenti olarak) varsa, öncelik hesapları etiketini kullanmanın yanı sıra özel kullanıcı etiketleri de oluşturabilirsiniz.

> [!NOTE]
> Şu anda, posta kutusu kullanıcılarına yalnızca kullanıcı etiketleri uygulayabilirsiniz.

Kullanıcılara sistem etiketlerini veya özel etiketleri kaydettikten sonra, bu etiketleri uyarılarda, raporlarda ve soruşturmalarda filtre olarak kullanabilirsiniz:

- [Uyarılar](alerts.md)
- [Özel uyarı ilkeleri](../../compliance/alert-policies.md#viewing-alerts)
- [Tehdit Gezgini ve gerçek zamanlı algılamalar](threat-explorer.md)
- [E-posta varlık sayfası](mdo-email-entity-page.md#other-innovations)
- [Tehdit koruması durum raporu](view-email-security-reports.md#threat-protection-status-report)
- [Kampanya Görünümleri](campaigns.md)
- [Yönetici ve kullanıcı gönderimleri](admin-submission.md)
- [Karantina](quarantine.md)
- Öncelik hesapları için, yönetim merkezinde (EAC[](/exchange/monitoring/mail-flow-reports/mfr-email-issues-for-priority-accounts-report)) öncelik hesapları için E Exchange sorunları raporunu kullanabilirsiniz.

Bu makalede, Microsoft 365 Defender portalında kullanıcı etiketlerinin nasıl Microsoft 365 Defender açıklanmıştır. Bu portalda kullanıcı etiketlerini yönetecek Microsoft 365 Defender cmdlet'i yoktur.

Kullanıcı etiketlerinin çok etkili kullanıcı hesaplarının korunmasına yardımcı olmak için stratejinin nasıl bir parçası olduğunu görmek için bkz. Etki alanı içinde öncelik [hesapları için Microsoft 365](security-recommendations-for-priority-accounts.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Başlamadan önce bilmeniz gerekenler

- Microsoft 365 Defender portalını açın<https://security.microsoft.com>. Doğrudan Kullanıcı etiketleri sayfasına **gitmek için** , ' kullanın <https://security.microsoft.com/securitysettings/userTags>.

- Bu makaledeki yordamları yerine Microsoft 365 Defender portalında izinlerin atanmamış olması gerekir:
  - Özel kullanıcı etiketleri oluşturmak, değiştirmek ve silmek için, Kuruluş Yönetimi veya Güvenlik Yöneticisi **rol gruplarının** **üyesi olmak** gerekir.
  - Öncelik Hesabı sistem etiketine üye eklemek ve bu üyelerden kaldırmak için, Güvenlik Yöneticisi'nin üyesi Exchange  **yönetici rol gruplarını eklemeniz** gerekir.
  - Var olan özel kullanıcı etiketlerinden üye eklemek ve kaldırmak için, Kuruluş Yönetimi veya Güvenlik Yöneticisi rol **gruplarının üyesi olmak** gerekir.
  - Kullanıcı etiketlerine salt okunur erişim için, **Genel Okuyucu****, Güvenlik** İşleci veya Güvenlik Okuyucusu **rol gruplarının üyesi** olmak gerekir.

  Daha fazla bilgi için bkz[. Microsoft 365 Defender portalına.](permissions-microsoft-365-security-center.md)

  > [!NOTE]
  >
  > - Kullanıcı atamasında ilgili Azure Active Directory rolüne Microsoft 365 yönetim merkezi, kullanıcılara _Microsoft 365 Defender portalında_ gerekli izinleri ve Microsoft 365. Daha fazla bilgi için bkz. [Yönetici rolleri hakkında](../../admin/add-users/about-admin-roles.md).
  >
  > - Kullanıcı etiket yönetimi Etiket Okuyucu ve **Etiket Yöneticisi** **rolleri tarafından denetleniyor** .

- Ayrıca, ilk oturumda öncelik hesaplarını yönetebilir ve Microsoft 365 yönetim merkezi. Yönergeler için bkz [. Öncelik hesaplarını yönetme ve izleme](../../admin/setup/priority-accounts.md).

- Ayrıcalıklı hesapların ( _yönetici hesapları_ ) güvenliğini sağlama hakkında bilgi için bu [konuya bakın](/azure/architecture/framework/security/critical-impact-accounts).

## <a name="use-the-microsoft-365-defender-portal-to-create-user-tags"></a>Kullanıcı Microsoft 365 Defender etiketleri oluşturmak için Kullanıcı Portalı'nın kullanımı

1. Aşağıdaki Microsoft 365 Defender portalında E-posta <https://security.microsoft.com>ve **Ayarlar-posta** \> **& Etiketleri'ne** \> **gidin**. Doğrudan Kullanıcı etiketleri sayfasına **gitmek için** , ' kullanın <https://security.microsoft.com/securitysettings/userTags>.

2. Kullanıcı etiketleri **sayfasında Etiket** oluştur simgesine ![tıklayın.](../../media/m365-cc-sc-create-icon.png) **Etiket oluştur'a**.

3. Etiket **oluştur sihirbazı** yeni bir açılır pencere açar. Etiket **tanımla sayfasında** aşağıdaki ayarları yapılandırabilirsiniz:
   - **Ad**: Etiket için benzersiz, açıklayıcı bir ad girin. Bu, göreceğiniz ve kullanabileceğiniz değerdir. Etiketi oluşturduk sonra yeniden adlandıramayabilirsiniz.
   - **Açıklama**: Etiket için isteğe bağlı bir açıklama girin.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

4. Üye **atama sayfasında** , aşağıdaki adımlardan birini uygulayın:
   - Üye ekle ![simgesine tıklayın.](../../media/m365-cc-sc-create-icon.png) **Üye ekleyin**. Görüntülenen açılır adımda, tek tek kullanıcıları veya grupları eklemek için aşağıdaki adımlardan birini uygulayın:
     - Kutuya tıklayın ve listeyi kaydırarak bir kullanıcı veya grup seçin.
     - Kutuya tıklayın ve listeyi filtrelemek için yazmaya başlayın ve bir kullanıcı veya grup seçin.
     - Ek değerler eklemek için kutuda boş bir alana tıklayın.
     - Tek tek girişleri kaldırmak için ![Girdiyi kaldır simgesi.](../../media/m365-cc-sc-remove-selection-icon.png) yazın.
     - Tüm girdileri kaldırmak için Girdiyi kaldır ![simgesine tıklayın.](../../media/m365-cc-sc-remove-selection-icon.png) on the **Selected nn users and nn groups item** below the box.

     Bitirdikten sonra Ekle'ye **tıklayın**.

     Üye atama **sayfasına geri dönerek** , Simgeyi sil'e tıklayarak girdileri kaldırabilirsiniz ![.](../../media/m365-cc-sc-delete-icon.png) seçin.

   - Kullanıcıların **veya** grupların e-posta adreslerini içeren bir metin dosyası seçmek için İçeri Aktar'a tıklayın. Metin dosyasında satır başına bir giriş olduğundan emin olun.

   Bitirdikten sonra, Sonraki'ne **tıklayın**.

5. Görüntülenen **Gözden Geçir etiket** sayfasında, ayarlarınızı gözden geçirin. Bölümün içindeki **ayarları değiştirmek** için her bölümde Düzenle'yi seçebilirsiniz. Geri'ye **tıklar** veya sihirbazda belirli bir sayfayı seçersiniz.

   Bitirdikten sonra Gönder'e **ve** ardından Bitti'ye **tıklayın**.

## <a name="use-the-microsoft-365-defender-portal-to-view-user-tags"></a>Kullanıcı etiketlerini Microsoft 365 Defender için kullanıcı portalını kullanma

1. Aşağıdaki Microsoft 365 Defender portalında E-posta <https://security.microsoft.com>ve **Ayarlar-posta** \> **& Etiketleri'ne** \> **gidin**. Doğrudan Kullanıcı etiketleri sayfasına **gitmek için** , ' kullanın <https://security.microsoft.com/securitysettings/userTags>.

2. Kullanıcı **etiketleri sayfasında** , kullanıcı etiketleri listesinde aşağıdaki özellikler görüntülenir:

   - **Etiket**: Kullanıcı etiketinin adı. Buna, yerleşik Öncelik hesabı sistem **etiketinin de dahil olduğunu** unutmayın.
   - **Şu kişi** için uygulanır: Üye sayısı
   - **Son değiştirme**
   - **Oluşturulma günü**

3. Adı tıklatarak bir kullanıcı etiketi görüntülendiğinde, ayrıntılar bir çıkışta görüntülenir.

## <a name="use-the-microsoft-365-defender-portal-to-modify-user-tags"></a>Kullanıcı etiketlerini Microsoft 365 Defender için kullanıcı portalını kullanma

1. Aşağıdaki Microsoft 365 Defender portalında E-posta <https://security.microsoft.com>ve **Ayarlar-posta** \> **& Etiketleri'ne** \> **gidin**. Doğrudan Kullanıcı etiketleri sayfasına **gitmek için** , ' kullanın <https://security.microsoft.com/securitysettings/userTags>.

2. Kullanıcı **etiketleri sayfasında** , listeden kullanıcı etiketini seçin ve ardından Etiket simgesini düzenle'ye ![tıklayın.](../../media/m365-cc-sc-edit-icon.png) **Etiketi düzenle'yi seçin**.

3. Görüntülenen ayrıntılar açılır sayfasında, bu makalenin başlarındaki Kullanıcı etiketleri oluşturmak için [Microsoft 365 Defender portalını](#use-the-microsoft-365-defender-portal-to-create-user-tags) kullanma bölümünde açıklanan sihirbaz ve ayarlar yer almaktadır.

   **Notlar**:

   - Etiket **tanımla** sayfası, yerleşik Öncelik hesabı sistemi etiketi için kullanılamaz,  dolayısıyla bu etiketi yeniden adlandırılamaz veya açıklamayı değiştiremezsiniz.
   - Özel etiketi yeniden adlandırılamaz, ancak açıklamayı değiştirebilirsiniz.

## <a name="use-the-microsoft-365-defender-portal-to-remove-user-tags"></a>Kullanıcı Microsoft 365 Defender kaldırmak için kullanıcı portalını kullanma

> [!NOTE]
> Yerleşik Öncelik hesap sistemi etiketini **kaldıraasınız** .

1. Aşağıdaki Microsoft 365 Defender portalında E-posta <https://security.microsoft.com>ve **Ayarlar-posta** \> **& Etiketleri'ne** \> **gidin**. Doğrudan Kullanıcı etiketleri sayfasına **gitmek için** , ' kullanın <https://security.microsoft.com/securitysettings/userTags>.

2. Kullanıcı **etiketleri sayfasında** , listeden kullanıcı etiketini seçin ve ardından Etiket simgesini sil'e ![tıklayın.](../../media/m365-cc-sc-delete-icon.png) **Etiketi sil'i seçin**.

3. Görüntülenen onay iletişim kutusunda uyarıyı okuyun ve Sonra Evet, **kaldır'a tıklayın**.
