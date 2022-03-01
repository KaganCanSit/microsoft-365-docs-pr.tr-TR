---
title: Insider risk yönetimi bildirimi şablonları
description: Insider risk yönetimi bildirimi şablonları hakkında daha fazla bilgi Microsoft 365
keywords: Microsoft 365, insider risk yönetimi, risk yönetimi, uyumluluk
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: cfa9628861e592b1e8cf235fe5c68e538be354ba
ms.sourcegitcommit: efb333ce0772265da91632110acba39acfbe0bde
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2021
ms.locfileid: "62997097"
---
# <a name="insider-risk-management-notice-templates"></a>Insider risk yönetimi bildirimi şablonları

Insider risk yönetimi bildirimi şablonları, bir ilke eşleşmesi ve onaylandı uyarısı oluşturan etkinlikler için olay oluşturulduğunda kullanıcılara otomatik olarak e-posta iletileri göndermenizi sağlar. Vaka oluşturan çoğu uyarı için, kullanıcı eylemleri kötü amaçlı olmayan hataların veya yanlışlıkla etkinliklerin sonucu olur. Bildirimler, kullanıcıların daha dikkatli olması, bilgileri tazeleme eğitimi veya kurumsal ilke kaynaklarına bağlantılar sağlamak için basit anımsatıcılar olarak kullanılabilir. Bildirimler, iç uyumluluk eğitim programınız için önemli bir parçası olabilir ve yinelenen risk etkinliklerine sahip kullanıcılar için belgeli bir denetim izi oluşturmanıza yardımcı olabilir.

Kullanıcılara, olay çözümleme sürecinin bir parçası olarak ilke eşleşmeleri için e-posta anımsatıcı bildirimi göndermek için bildirim şablonları oluşturun. Bildirimler yalnızca gözden geçen olayla ilişkilendirilmiş olan kullanıcı e-posta adresine gönderebilirsiniz. İlke eşleşmesi için uygulanacak bildirim şablonunu seçerseniz, şablonda tanımlanan alan değerlerini kabul etme veya gereken alanların üzerine yazmayı seçebilirsiniz

## <a name="notice-templates-dashboard"></a>Bildirim şablonları panosu

Bildirimler **şablonları panosu, yapılandırılmış** bildirim şablonlarının listesini görüntüler ve yeni bildirim şablonları oluşturmanıza olanak sağlar. Bildirim şablonları, en son bildirim şablonu ilk sırada, ters tarih sırasına göre listelenir.

![Insider risk yönetimi bildirimi şablon panosu.](../media/insider-risk-notices-dashboard.png)

## <a name="html-for-notices"></a>Bildirimler için HTML

Bildirimler için metin tabanlı basit bir e-posta iletisinden daha fazlasını oluşturmak için, bildirim şablonunun ileti gövdesi alanında HTML kullanarak daha ayrıntılı bir ileti oluşturabilirsiniz. Aşağıdaki örnekte, temel HTML tabanlı bir e-posta bildirim şablonu için ileti gövdesi biçimi ve şöyledir:

```HTML
<!DOCTYPE html>
<html>
<body>
<h2>Action Required: Contoso User Code of Conduct Policy Training</h2>
<p>A recent activity you've performed has generated a risk alert prohibited by the Contoso User <a href='https://www.contoso.com'>Code of Conduct Policy</a>.</p>
<p>You are required to attend the Contoso User Code of Conduct <a href='https://www.contoso.com'>training</a> within the next 14 days. Please contact <a href='mailto:hr@contoso.com'>Human Resources</a> with any questions about this training request.</p>
<p>Thank you,</p>
<p><em>Human Resources</em></p>
</body>
</html>
```

> [!NOTE]
> Insider risk yönetimi bildirim şablonlarında HTML href özniteliği uygulaması şu anda URL başvuruları için çift tırnak yerine yalnızca tek tırnak işaretlerini destekler.

## <a name="create-a-new-notice-template"></a>Yeni bildirim şablonu oluşturma

Yeni bir Insider risk yönetimi bildirimi şablonu oluşturmak için, aşağıdaki çalışma sayfalarındaki **Insider risk yönetimi** çözümünde bildirim oluşturma aracını Microsoft 365 uyumluluk merkezi.

Yeni bir Insider risk yönetimi bildirimi şablonu oluşturmak için aşağıdaki adımları tamamlayın:

1. Giriş [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin** ve Bildirim şablonları **sekmesini** seçin.
2. Bildirim **oluşturma aracını açmak için** Bildirim şablonu oluştur'a seçin.
3. Yeni **bildirim şablonu oluştur sayfasında** , aşağıdaki alanları doldurun:
    - **Şablon adı**: Bildirim için kolay bir ad girin. Bu ad, bir vakadan bildirim gönderirken bildirim panosunda ve bildirim seçim listesinde bildirimler listesinde görünür.
    - **Gönderen:** Bildirim için gönderenin e-posta adresini girin. Bu adres, bir **vakadan bildirim** gönderirken değiştirmedikçe kullanıcılara gönderilen tüm bildirimlerde Gönderen: alanında görünür.
    - **Bilgi ve Gizli alanları** : Aboneliğiniz için Active Directory'den seçilen, ilke eşleşmesi hakkında bilgi alınacak isteğe bağlı kullanıcılar veya gruplar.
    - **Konu**: İletinin konu satırlarında görüntülenen bilgiler metin karakterlerini destekler.
    - **İleti gövdesi**: İleti gövdesinde görünen bilgiler metin veya HTML değerlerini destekler.
4. Bildirim **şablonunu oluşturmak** ve kaydetmek için Oluştur'a veya bildirim şablonunu **kaydetmeden** kapatmak için İptal'i seçin.

## <a name="update-a-notice-template"></a>Bildirim şablonunu güncelleştirme

Var olan bir Insider risk yönetimi bildirimi şablonunu güncelleştirmek için aşağıdaki adımları tamamlayın:

1. Giriş [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin** ve Bildirim şablonları **sekmesini** seçin.
2. Bildirim panosunda, yönetmek istediğiniz bildirim şablonunu seçin.
3. Bildirim ayrıntıları sayfasında Düzenle'yi **seçin**
4. Düzenle **sayfasında** , aşağıdaki alanları düzenleyebilirsiniz:
    - **Şablon adı**: Bildirim için yeni bir kolay ad girin. Bu ad, bir vakadan bildirim gönderirken bildirim panosunda ve bildirim seçim listesinde bildirimler listesinde görünür.
    - **Gönderen:** Bildirim için gönderenin e-posta adresini güncelleştirin. Bu adres, bir **vakadan bildirim** gönderirken değiştirmedikçe kullanıcılara gönderilen tüm bildirimlerde Gönderen: alanında görünür.
    - **Bilgi ve Gizli alanları** : Aboneliğiniz için Active Directory'den seçilecek ilke eşleşmesi hakkında bilgi edinilecek isteğe bağlı kullanıcıları veya grupları güncelleştirin.
    - **Konu**: İletinin konu satırlarında görünen bilgileri güncelleştirin, metin karakterlerini desteklemektedir.
    - **İleti gövdesi**: İleti gövdesinde görünen bilgileri güncelleştirin; metin veya HTML değerlerini destekler.
5. **Güncellemek** için Kaydet'i seçin ve bildirimi kaydedin veya bildirim **şablonunu kaydetmeden** kapatmak için İptal'i seçin.

## <a name="delete-a-notice-template"></a>Bildirim şablonunu silme

Var olan bir Insider risk yönetimi bildirimi şablonunu silmek için aşağıdaki adımları tamamlayın:

1. Giriş [Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) **Insider risk yönetimi'ne gidin** ve Bildirim şablonları **sekmesini** seçin.
2. Bildirim panosunda, silmek istediğiniz bildirim şablonunu seçin.
3. Araç çubuğunda **Sil** simgesini seçin.
4. Bildirim şablonunu silmek için sil iletişim **kutusunda Evet'i** seçin. Silme işlemini iptal etmek için İptal'i **seçin**.
