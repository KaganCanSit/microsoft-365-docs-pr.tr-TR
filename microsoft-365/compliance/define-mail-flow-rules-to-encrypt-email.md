---
title: E-posta iletilerini şifrelemek için posta akış kurallarını tanımlama
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
description: Yöneticiler, posta akış kurallarını (aktarım kuralları) kullanarak iletileri şifrelemeyi ve şifrelerini çözmeyi Office 365 İleti Şifrelemesi.
ms.openlocfilehash: c546c151b7bcb1720f9903d43b8d310650f92d35
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/13/2021
ms.locfileid: "63018755"
---
# <a name="define-mail-flow-rules-to-encrypt-email-messages"></a>E-posta iletilerini şifrelemek için posta akış kurallarını tanımlama

Posta akışlarını yöneten bir Exchange Online olarak, gönderttirdiği ve alan e-posta iletilerini korumaya yardımcı olmak için posta akışı kuralları (aktarım kuralları olarak da bilinir) oluşturabilirsiniz. Tüm giden e-posta iletilerini şifrelemek ve kuruluş içinden gelen şifrelenmiş iletilerden veya kuruluştan gönderilen şifrelenmiş iletilere gönderilen yanıtlardan şifrelemeyi kaldırmak için kurallar kurabilirsiniz. Bu kuralları oluşturmak <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">için Exchange merkezini (EAC)</a> veya Exchange Online PowerShell'i kullanabilirsiniz. Genel şifreleme kurallarına ek olarak, son kullanıcılar için tek tek ileti şifreleme seçeneklerini etkinleştirmeyi veya devre dışı bırakmayı da seçebilirsiniz.

Kuruluş dışındaki gönderenlerden gelen postayı şifreleyesiniz.

Active Directory RMS'den Azure Information Protection'a yeni geçiş yaptıysanız, yeni ortamında çalışmaya devam edeceklerinden emin olmak için var olan posta akış kurallarınızı gözden geçirmeniz gerekir. Ayrıca Azure Information Protection aracılığıyla size Office 365 İleti Şifrelemesi OME) yeni özelliklerden yararlanmak için mevcut posta akış kurallarınızı güncelleştirmeniz gerekir. Aksi takdirde, kullanıcılarınız yeni, sorunsuz OME deneyimi yerine önceki HTML ek biçimini kullanan şifrelenmiş posta almaya devam eder. OME'i henüz ayarlamadısanız, bilgi için bkz[. Yeni Office 365 İleti Şifrelemesi özellikleri](set-up-new-message-encryption-capabilities.md) ayarlama.

Posta akış kurallarını ve posta akış kurallarının nasıl çalışmasıyla ilgili bileşenler hakkında bilgi için, bu konudaki Posta akış kuralları [(aktarım kuralları) Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules). Posta akış kurallarının Azure Information Protection ile çalışma hakkında ek bilgi için bkz. Azure Information Protection etiketleri için [Exchange Online akış kurallarını yapılandırma](/azure/information-protection/deploy-use/configure-exo-rules).

> [!IMPORTANT]
> Karma Exchange ortamlarında, şirket içi kullanıcılar yalnızca e-posta OME kullanarak şifrelenmiş posta gönderebilir ve Exchange Online. Karma bir Exchange ortamında OME'yi yapılandırmak için, önce Karma Yapılandırma sihirbazını kullanarak [](/Exchange/exchange-hybrid) karma yapılandırmanız ve ardından postanın [Office 365'tan](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-1-configure-mail-to-flow-from-office-365-to-your-on-premises-email-server) e-posta sunucunuza akacak şekilde yapılandırılması ve postanın e-posta sunucunuzdan Office 365'a akacak şekilde yapılandırılması [gerekir.](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-2-configure-mail-to-flow-from-your-email-server-to-office-365) Postayı akış kılavuzu olarak yapılandır Office 365, bu kılavuzu kullanarak OME için posta akış kurallarını yapılandırabilirsiniz.

## <a name="create-mail-flow-rules-to-encrypt-email-messages-with-the-new-ome-capabilities"></a>Yeni OME özellikleriyle e-posta iletilerini şifrelemek için posta akış kuralları oluşturma

EAC kullanarak, yeni OME özellikleriyle ileti şifrelemeyi tetikleyen posta akış kuralları tanımlayabilirsiniz.

### <a name="use-the-eac-to-create-a-rule-for-encrypting-email-messages-with-the-new-ome-capabilities"></a>EAC kullanarak e-posta iletilerini yeni OME özellikleriyle şifrelemek için bir kural oluşturma

1. Web tarayıcısında, genel yönetici izinlerine sahip bir iş veya okul hesabı kullanarak [Office 365.](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser)

2. Yönetici **kutucuğunu** seçin.

3. Genel <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi Yönetim</a> **merkezleri'ni Exchange**\>.

4. EAC'de, Posta akışı **Kuralları'ne gidin** \> **ve** Yeni Yeni **simgesi'yi** ![seçin.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Yeni kural oluşturma**. EAC'nin kullanımı hakkında daha fazla bilgi için bkz[. Exchange Yönetim Merkezi'Exchange Online](/exchange/exchange-admin-center).

5. Ad **kutusuna** kural için Bir ad yazın; örneğin Posta şifreleme DrToniRamos@hotmail.com.

6. Bu **kuralı uygula altında,** bir koşul seçin ve gerekiyorsa bir değer girin. Örneğin, iletileri şifrelemek için şunları DrToniRamos@hotmail.com:

   1. Şu **durumda bu kuralı uygula'da** **alıcıyı seçin**.

   2. Kişi listesinden mevcut bir adı seçin veya onay adları kutusuna yeni bir **e-posta adresi** yazın.

      - Var olan bir adı seçmek için, listeden adı seçin ve ardından Tamam'a **tıklayın**.

      - Yeni bir ad girmek için, onay adları kutusuna bir **e-posta adresi yazın** ve adları onayla **Tamam'ı** \> **seçin**.

7. Daha fazla koşul eklemek için Diğer **seçenekler'i** , sonra koşul **ekle'yi seçin** ve listeden seçim yapabilirsiniz.

   Örneğin, kuralı yalnızca alıcı kuruluş dışında olursa uygulamak için koşul ekle'yi seçin ve sonra  Alıcı, Kuruluş dışında **/** \> şirket dışında **Tamam'ı** \> **seçin**.

8. Yeni OME özelliklerini kullanarak şifrelemeyi etkinleştirmek için, Aşağıdakini yapın'da İleti güvenliğini  değiştir'i seçin ve sonra Office 365 İleti Şifrelemesi **ve hak koruması uygula'ya seçin**. Listeden bir RMS şablonu seçin, Kaydet'i **ve** ardından Tamam'ı **seçin**.
  
  Şablon listesi, tüm varsayılan şablonları ve seçeneklerin yanı sıra kullanıcı tarafından kullanmak üzere oluşturduğunuz tüm özel şablonları Office 365. Liste boşsa, Yeni Veri Yönetimi özelliklerini Office 365 İleti Şifrelemesi yeni özellikleri ayarlama konusunda açıklandığı gibi yeni özelliklerle liste [Office 365 İleti Şifrelemesi emin olur.](set-up-new-message-encryption-capabilities.md) Varsayılan şablonlar hakkında bilgi için bkz. [Azure Information Protection için şablonları yapılandırma ve yönetme](/information-protection/deploy-use/configure-policy-templates). E-postalarda **İleri seçeneğini iletme** [seçeneği hakkında bilgi için bkz. E-postalar için iletme seçeneği](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). Yalnızca şifrele seçeneği **hakkında bilgi için** bkz. [E-postalar için yalnızca şifrele seçeneği](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

  Başka bir **eylem belirtmek** için eylem ekle'yi seçebilirsiniz.

### <a name="use-the-eac-to-update-an-existing-mail-flow-rule-to-use-the-new-ome-capabilities"></a>Var olan bir posta akışı kuralını yeni OME özelliklerini kullanmak üzere güncelleştirmek için EAC'i kullanma

1. Web tarayıcısında, genel yönetici izinlerine sahip bir iş veya okul hesabı kullanarak [Office 365.](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser)

2. Yönetici **kutucuğunu** seçin.

3. Genel <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi Yönetim</a> **merkezleri'ni Exchange**\>.

4. EAC'de, Posta akışı **Kuralları'ne** \> **gidin**.

5. Posta akışı kuralları listesinde, yeni OME özelliklerini kullanmak için değiştirmek istediğiniz kuralı seçin ve sonra da **Düzenle simgesini** ![seçin](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif).

6. Yeni OME özelliklerini kullanarak şifrelemeyi etkinleştirmek için, Aşağıdakileri yapın'da İleti güvenliğini  değiştir'i seçin ve sonra da Office 365 İleti Şifrelemesi **ve hak koruması uygula'ya seçin**. Listeden bir RMS şablonu seçin, Kaydet'i **ve sonra** Tamam'ı **seçin**.

   Şablon listesi, tüm varsayılan şablonları ve seçeneklerin yanı sıra kullanıcı tarafından kullanmak üzere oluşturduğunuz tüm özel şablonları Office 365. Liste boşsa, Azure Information Protection'ın Office 365 İleti Şifrelemesi yeni özellikler ayarlama konusunda açıklandığı gibi yeni özelliklerle liste [Office 365 İleti Şifrelemesi özellikler ayarlamayı sağlar.](set-up-new-message-encryption-capabilities.md) Varsayılan şablonlar hakkında bilgi için bkz. [Azure Information Protection için şablonları yapılandırma ve yönetme](/information-protection/deploy-use/configure-policy-templates). E-postalarda İleri seçeneğini iletme [seçeneği hakkında bilgi için bkz. E-postalar için iletme seçeneği](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). Yalnızca şifrele seçeneği hakkında bilgi için bkz. [E-postalar için Yalnızca Şifrele seçeneği](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

   Başka bir **eylem belirtmek** için eylem ekle'yi seçebilirsiniz.

7. Aşağıdakini **yapın listesinde**, İleti güvenliğini değiştirme OME'nin  \> önceki sürümünü uygulama **için atanmış tüm eylemleri kaldırın**.

8. **Kaydet**'i seçin.

## <a name="create-mail-flow-rules-to-remove-encryption-for-email-messages-with-the-new-ome-capabilities"></a>Yeni OME özellikleriyle e-posta iletilerinin şifrelemelerini kaldırmak için posta akış kuralları oluşturma

EAC kullanarak, yeni OME özellikleriyle ileti şifrelemeyi kaldırmayı tetikleyen posta akış kuralları tanımlayabilirsiniz.

### <a name="use-the-eac-to-create-a-rule-to-remove-encryption-from-email-messages-with-the-new-ome-capabilities"></a>Yeni OME özellikleriyle e-posta iletilerinden şifrelemeyi kaldırmak üzere bir kural oluşturmak için EAC'i kullanma

Organizasyonunız tarafından uygulanan şifrelemeyi kaldırarak bunları kaldırmanıza yardımcı olabilir.

1. Web tarayıcısında, genel yönetici izinlerine sahip bir iş veya okul hesabı kullanarak [Office 365.](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser)

2. Yönetici **kutucuğunu** seçin.

3. Genel <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi Yönetim</a> **merkezleri'ni Exchange**\>.

4. EAC'de, Posta akışı **Kuralları'ne gidin** \> **ve** Yeni Yeni **simgesi'yi** ![seçin.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Yeni kural oluşturma**. EAC'nin kullanımı hakkında daha fazla bilgi için bkz[. Exchange Yönetim Merkezi'Exchange Online](/exchange/exchange-admin-center).

5. Ad **kutusuna** kural için, Giden postadan şifrelemeyi kaldır gibi bir ad yazın.

6. Aşağıdaki **durumda bu kuralı uygula** altında, şifrelemenin iletilerden kaldırılması gereken koşulları seçin. Ekle **Gönderen, posta göndermek** \> **için kuruluşun** içinde veya Alıcı  **, posta** \> almak **için kuruluşun** içinde yer alıyor.

7. **Aşağıdakini yapın'da** İleti **güvenliğini değiştir'i seçin Office 365 İleti Şifrelemesi** \> **koruma'ya tıklayın**.

8. **Kaydet**'i seçin.

## <a name="create-mail-flow-rules-for-office-365-message-encryption-without-the-new-capabilities"></a>Yeni özelliklere sahip Office 365 İleti Şifrelemesi için posta akışı kuralları oluşturma

Organizasyonlarınızı henüz yeni OME özelliklerine taşımadıysanız, Microsoft, yeni OME özelliklerine kurum için uygun olduğu anda bir plan yapmanızı önerir. Yönergeler için bkz[. Azure Information Protection Office 365 İleti Şifrelemesi üzerine yerleşik yeni güvenlik özellikleri ayarlama](set-up-new-message-encryption-capabilities.md). Aksi takdirde, [yeni OME özelliklerini kullanmayan Office 365 İleti Şifrelemesi kullanıcı için posta akışı kurallarını tanımlama'ya bakın](legacy-information-for-message-encryption.md#defining-mail-flow-rules-for-office-365-message-encryption-that-dont-use-the-new-ome-capabilities).

## <a name="related-content"></a>İlgili içerik

[Şifreleme Office 365](encryption.md)

[Yeni özellik Office 365 İleti Şifrelemesi ayarlama](set-up-new-message-encryption-capabilities.md)

[Şifreli iletilere markalama ekleme](add-your-organization-brand-to-encrypted-messages.md)

[posta akışı kuralları (aktarım kuralları) Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)
