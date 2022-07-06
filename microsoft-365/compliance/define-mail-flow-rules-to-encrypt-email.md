---
title: E-posta iletilerini şifrelemek için posta akışı kurallarını tanımlama
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 9b7daf19-d5f2-415b-bc43-a0f5f4a585e8
ms.collection:
- M365-security-compliance
ms.custom:
- admindeeplinkMAC
- admindeeplinkEXCHANGE
description: Yöneticiler, Microsoft Purview İleti Şifrelemesi kullanarak iletileri şifrelemek ve şifresini çözmek için posta akışı kuralları (aktarım kuralları) oluşturmayı öğrenebilir.
ms.openlocfilehash: 75abd302bf661fda50b144f431572c8c6dfc8bcc
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66635709"
---
# <a name="define-mail-flow-rules-to-encrypt-email-messages"></a>E-posta iletilerini şifrelemek için posta akışı kurallarını tanımlama

Exchange Online yöneten bir yönetici olarak, gönderdiğiniz ve aldığınız e-posta iletilerini korumaya yardımcı olmak için posta akışı kuralları (taşıma kuralları olarak da bilinir) oluşturabilirsiniz. Giden e-posta iletilerini şifrelemek ve kuruluşunuzun içinden gelen veya kuruluşunuzdan gönderilen şifrelenmiş iletilere verilen yanıtlardan şifrelemeyi kaldırmak için kurallar ayarlayabilirsiniz. Bu kuralları oluşturmak için <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezini (EAC)</a> veya PowerShell'i Exchange Online kullanabilirsiniz. Genel şifreleme kurallarına ek olarak, son kullanıcılar için tek tek ileti şifreleme seçeneklerini etkinleştirmeyi veya devre dışı bırakmayı da seçebilirsiniz.

Kuruluşunuzun dışındaki gönderenlerden gelen postaları şifreleyemezsiniz.

Kısa süre önce Active Directory RMS'den Azure Information Protection'ye geçiş yaparsanız, yeni ortamınızda çalışmaya devam etmelerini sağlamak için mevcut posta akışı kurallarınızı gözden geçirmeniz gerekir. Ayrıca azure Information Protection ile Microsoft Purview İleti Şifrelemesi kullanmak için mevcut posta akışı kurallarınızı güncelleştirmeniz gerekir. Aksi takdirde, kullanıcılarınız yeni ve sorunsuz deneyim yerine önceki HTML ek biçimini kullanan şifreli postalar almaya devam eder. İleti şifrelemesini henüz ayarlamadıysanız, bilgi için bkz. [Microsoft Purview İleti Şifrelemesi ayarlama](set-up-new-message-encryption-capabilities.md).

Posta akışı kurallarını oluşturan bileşenler ve posta akışı kurallarının nasıl çalıştığı hakkında bilgi için bkz. [Exchange Online'de Posta akışı kuralları (aktarım kuralları).](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) Posta akışı kurallarının Azure Information Protection ile nasıl çalıştığı hakkında ek bilgi için bkz. [Azure Information Protection etiketleri için Exchange Online posta akışı kurallarını yapılandırma](/azure/information-protection/deploy-use/configure-exo-rules).

> [!IMPORTANT]
> Karma Exchange ortamları için, şirket içi kullanıcılar yalnızca e-posta Exchange Online üzerinden yönlendirildiğinde ileti şifrelemesi kullanarak şifreli posta gönderip alabilir. İleti şifrelemesini karma Exchange ortamında yapılandırmak için önce [Karma Yapılandırma sihirbazını kullanarak karma](/Exchange/exchange-hybrid) yapılandırmanız ve ardından [postayı Office 365'dan e-posta sunucunuza akacak şekilde yapılandırmanız ve e-posta sunucunuzdan](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-1-configure-mail-to-flow-from-office-365-to-your-on-premises-email-server) [Office 365'a akacak şekilde yapılandırmanız](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-2-configure-mail-to-flow-from-your-email-server-to-office-365) gerekir. Postayı Office 365 akacak şekilde yapılandırdıktan sonra, bu kılavuzu kullanarak ileti şifrelemesi için posta akışı kurallarını yapılandırabilirsiniz.

## <a name="create-mail-flow-rules-to-encrypt-email-messages-with-microsoft-purview-message-encryption"></a>Microsoft Purview İleti Şifrelemesi ile e-posta iletilerini şifrelemek için posta akışı kuralları oluşturma

EAC kullanarak ile ileti şifrelemesini tetikleme için posta akışı kuralları tanımlayabilirsiniz.

### <a name="use-the-eac-to-create-a-rule-for-encrypting-email-messages-with-microsoft-purview-message-encryption"></a>EAC kullanarak e-posta iletilerini Microsoft Purview İleti Şifrelemesi ile şifrelemek için bir kural oluşturma

1. Web tarayıcısında, genel yönetici izinleri verilmiş bir iş veya okul hesabı kullanarak [Office 365 oturum açın](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. **Yönetici** kutucuğunu seçin.

3. <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> Yönetici **merkezleri** \> **Exchange'i** seçin.

4. EAC'de **Posta akışı** \> **Kuralları'na** gidin ve **Yeni Yeni simgesi'ni** ![seçin.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Yeni bir kural oluşturun**. EAC'yi kullanma hakkında daha fazla bilgi için bkz. [Exchange Online'de Exchange yönetim merkezi](/exchange/exchange-admin-center).

5. **Ad** alanına kural için DrToniRamos@hotmail.com için posta şifreleme gibi bir ad yazın.

6. **Bu kuralı uygula** alanında bir koşul seçin ve gerekirse bir değer girin. Örneğin, DrToniRamos@hotmail.com giden iletileri şifrelemek için:

   1. **Bu kuralı uygula** alanında **alıcıyı** seçin.

   2. Kişi listesinden var olan bir adı seçin veya **onay adları** kutusuna yeni bir e-posta adresi yazın.

      - Var olan bir adı seçmek için listeden seçin ve **ardından Tamam'a** tıklayın.

      - Yeni bir ad girmek için, **onay adları** kutusuna bir e-posta adresi yazın ve ardından **adları** \> **denetle Tamam'ı** seçin.

7. Daha fazla koşul eklemek için **Diğer seçenekler'i** ve ardından **Koşul ekle'yi** seçin ve listeden seçin.

   Örneğin, kuralı yalnızca alıcı kuruluşunuzun dışındaysa uygulamak için **Koşul ekle'yi** ve ardından Alıcı **kuruluş** \> **dışından/kuruluş** \> dışında **Tamam'ı** seçin.

8. İleti şifrelemesini etkinleştirmek için **Aşağıdakileri yapın** bölümünde **İleti güvenliğini değiştir'i** ve ardından **İleti Şifrelemesi ve hak koruması Office 365 uygula'yı** seçin. Listeden bir RMS şablonu seçin, **Kaydet'i** ve ardından **Tamam'ı** seçin.
  
  Şablon listesi, tüm varsayılan şablonları ve seçeneklerin yanı sıra Office 365 tarafından kullanılmak üzere oluşturduğunuz tüm özel şablonları içerir. Liste boşsa, Microsoft Purview İleti Şifrelemesi ayarlama bölümünde açıklandığı gibi [Microsoft Purview İleti Şifrelemesi ayarladığınızdan](set-up-new-message-encryption-capabilities.md) emin olun. Varsayılan şablonlar hakkında bilgi için bkz. [Azure Information Protection için şablonları yapılandırma ve yönetme](/information-protection/deploy-use/configure-policy-templates). **İletme** seçeneği hakkında bilgi için bkz. [E-postalar için İletme seçeneği](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). **Yalnızca şifrele** seçeneği hakkında bilgi için bkz. [E-postalar için yalnızca şifreleme seçeneği](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

  Başka bir eylem belirtmek istiyorsanız **Eylem ekle'yi** seçebilirsiniz.

### <a name="use-the-eac-to-update-an-existing-mail-flow-rule-to-use-microsoft-purview-message-encryption"></a>Mevcut bir posta akışı kuralını Microsoft Purview İleti Şifrelemesi kullanacak şekilde güncelleştirmek için EAC kullanma

1. Web tarayıcısında, genel yönetici izinleri verilmiş bir iş veya okul hesabı kullanarak [Office 365 oturum açın](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. **Yönetici** kutucuğunu seçin.

3. <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> Yönetici **merkezleri** \> **Exchange'i** seçin.

4. EAC'de **Posta akışı** \> **Kuralları'na** gidin.

5. Posta akışı kuralları listesinde, Microsoft Purview İleti Şifrelemesi ile kullanmak üzere değiştirmek istediğiniz **kuralı seçin** ![ve sonra Düzenle Düzenle simgesi..](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).

6. Microsoft Purview İleti Şifrelemesi kullanarak şifrelemeyi etkinleştirmek için **Aşağıdakileri yapın** bölümünde **İleti güvenliğini değiştir'i** ve ardından **İleti Şifrelemesi ve hak koruması Office 365 uygula'yı** seçin. Listeden bir RMS şablonu seçin, **Kaydet'i** ve ardından **Tamam'ı** seçin.

   Şablon listesi, tüm varsayılan şablonları ve seçeneklerin yanı sıra Office 365 tarafından kullanılmak üzere oluşturduğunuz tüm özel şablonları içerir. Liste boşsa, Microsoft Purview İleti Şifrelemesi ayarlama bölümünde açıklandığı gibi [Microsoft Purview İleti Şifrelemesi ayarladığınızdan](set-up-new-message-encryption-capabilities.md) emin olun. Varsayılan şablonlar hakkında bilgi için bkz. [Azure Information Protection için şablonları yapılandırma ve yönetme](/information-protection/deploy-use/configure-policy-templates). İletme seçeneği hakkında bilgi için bkz. [E-postalar için İletme seçeneği](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). Yalnızca şifrele seçeneği hakkında bilgi için bkz. [E-postalar için Yalnızca Şifrele seçeneği](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

   Başka bir eylem belirtmek istiyorsanız **Eylem ekle'yi** seçebilirsiniz.

7. **Aşağıdakini yap** listesinden İleti **güvenliğini** \> değiştirme **OME'nin önceki sürümünü uygula'ya** atanan tüm eylemleri kaldırın.

8. **Kaydet**'i seçin.

## <a name="create-mail-flow-rules-to-remove-encryption-for-email-messages-with-microsoft-purview-message-encryption"></a>Microsoft Purview İleti Şifrelemesi ile e-posta iletilerinin şifrelemesini kaldırmak için posta akışı kuralları oluşturma

EAC kullanarak Microsoft Purview İleti Şifrelemesi ile ileti şifrelemesini kaldırmak için posta akışı kuralları tanımlayabilirsiniz.

### <a name="use-the-eac-to-create-a-rule-to-remove-encryption-from-email-messages-with-microsoft-purview-message-encryption"></a>EAC kullanarak Microsoft Purview İleti Şifrelemesi ile e-posta iletilerinden şifrelemeyi kaldırma kuralı oluşturma

Kuruluşunuz tarafından uygulanan iletilerden şifrelemeyi kaldırabilirsiniz. Ayrıca, tüm e-posta iletisinin herhangi bir koruma olmadan olduğundan emin olmak için şifrelenmiş eklerden şifrelemeyi kaldırabilirsiniz.

1. Web tarayıcısında, genel yönetici izinleri verilmiş bir iş veya okul hesabı kullanarak [Office 365 oturum açın](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. **Yönetici** kutucuğunu seçin.

3. <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> Yönetici **merkezleri** \> **Exchange'i** seçin.

4. EAC'de **Posta akışı** \> **Kuralları'na** gidin ve **Yeni Yeni simgesi'ni** ![seçin.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Yeni bir kural oluşturun**. EAC'yi kullanma hakkında daha fazla bilgi için bkz. [Exchange Online'de Exchange yönetim merkezi](/exchange/exchange-admin-center).

5. **Ad** alanına kural için gibi `Remove encryption from outgoing mail`bir ad yazın.

6. **Bu kuralı uygula altında**, iletilerden şifrelemenin kaldırılması gereken koşulları seçin. **Ekle Gönderen,** posta göndermek için **kuruluşun içinde** _veya_ \> Alıcı, posta almak üzere **kuruluşun içinde** **bulunur**\>.

7. **Aşağıdakileri yapın** bölümünde **İleti güvenliğini** \> değiştir **Office 365 İleti Şifrelemesini kaldır'ı ve kuruluş tarafından uygulanan hak korumasını** seçin.

8. (İsteğe bağlı) **Aşağıdakileri yapın** bölümünde İleti **güvenliğini** \> değiştir **Kuruluş tarafından uygulanan ek hakları korumasını kaldır'ı** seçin.

Kuralı kaydedin.

## <a name="create-mail-flow-rules-for-office-365-message-encryption-without-microsoft-purview-message-encryption"></a>Microsoft Purview İleti Şifrelemesi olmadan Office 365 İleti Şifrelemesi için posta akışı kuralları oluşturma

Kuruluşunuzu henüz Microsoft Purview İleti Şifrelemesi taşımadıysanız Microsoft, kuruluşunuz için makul olduğu anda taşınacak bir plan yapmanızı önerir. Yönergeler için bkz[. Microsoft Purview İleti Şifrelemesi ayarlama](set-up-new-message-encryption-capabilities.md). Aksi takdirde, Microsoft Purview İleti Şifrelemesi [kullanmayan Office 365 İleti Şifrelemesi için posta akışı kurallarını tanımlama](legacy-information-for-message-encryption.md#defining-mail-flow-rules-for-office-365-message-encryption-that-dont-use-microsoft-purview-message-encryption) bölümüne bakın.

## <a name="related-content"></a>İlgili içerik

[Office 365'de şifreleme](encryption.md)

[Microsoft Purview İleti Şifreleme'yi ayarlama](set-up-new-message-encryption-capabilities.md)

[Şifrelenmiş iletilere marka ekleme](add-your-organization-brand-to-encrypted-messages.md)

[Exchange Online'da posta akışı kuralları (aktarım kuralları)](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)
