---
title: Insider risk yönetimi bildirim şablonları
description: Microsoft Purview'da insider risk yönetimi bildirim şablonları hakkında bilgi edinin
keywords: Microsoft 365, Microsoft Purview, insider riski, risk yönetimi, uyumluluk
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
ms.openlocfilehash: 7af1152d1393aaaf9eeb242c78b280cf0e9d80e6
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66639808"
---
# <a name="insider-risk-management-notice-templates"></a>Insider risk yönetimi bildirim şablonları

Insider risk yönetimi bildirim şablonları, ilke eşleşmesi ve onaylanan uyarı oluşturan etkinlikler için bir servis talebi oluşturulduğunda kullanıcılara otomatik olarak e-posta iletileri göndermenizi sağlar. Vaka oluşturan uyarıların çoğu için kullanıcı eylemleri, hatalı amaçlara sahip olmayan hataların veya yanlışlıkla yapılan etkinliklerin sonucu olur. Bildirimler, kullanıcılara daha dikkatli olmaları, daha yenileyici eğitimle ilgili bilgilere bağlantılar sağlamaları veya şirket ilkesi kaynaklarına yönelik basit anımsatıcılar görevi görür. Bildirimler, iç uyumluluk eğitim programınızın önemli bir parçası olabilir ve yinelenen risk etkinlikleri olan kullanıcılar için belgelenmiş bir denetim kaydı oluşturmanıza yardımcı olabilir.

Kullanıcılara, servis talebi çözümleme sürecinin bir parçası olarak ilke eşleşmeleri için bir e-posta anımsatıcı bildirimi göndermek istiyorsanız bildirim şablonları oluşturun. Bildirimler yalnızca incelenmekte olan servis talebiyle ilişkili kullanıcı e-posta adresine gönderilebilir. İlke eşleşmesine uygulanacak bir bildirim şablonu seçerken, şablonda tanımlanan alan değerlerini kabul etmeyi veya gerektiğinde alanların üzerine yazmayı seçebilirsiniz

## <a name="notice-templates-dashboard"></a>Şablon panosuna dikkat edin

**Bildirimler şablonları panosu**, yapılandırılmış bildirim şablonlarının listesini görüntüler ve yeni bildirim şablonları oluşturmanıza olanak tanır. Bildirim şablonları, en son bildirim şablonunun ilk sırada listelendiği ters tarih sırasına göre listelenir.

![Insider risk yönetimi bildirim şablonu panosu.](../media/insider-risk-notices-dashboard.png)

## <a name="html-for-notices"></a>Bildirimler için HTML

Bildirimler için basit bir metin tabanlı e-posta iletisinden daha fazlasını oluşturmak isterseniz, bildirim şablonunun ileti gövdesi alanında HTML kullanarak daha ayrıntılı bir ileti oluşturabilirsiniz. Aşağıdaki örnek, temel HTML tabanlı e-posta bildirim şablonu için ileti gövdesi biçimini sağlar:

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
> Insider risk yönetimi bildirim şablonlarındaki HTML href özniteliği uygulaması şu anda URL başvuruları için çift tırnak işaretleri yerine yalnızca tek tırnak işaretlerini destekler.

## <a name="create-a-new-notice-template"></a>Yeni bildirim şablonu oluşturma

Yeni bir insider risk yönetimi bildirim şablonu oluşturmak için, Microsoft Purview uyumluluk portalı **Insider risk yönetimi** çözümünde bildirim oluşturma aracını kullanacaksınız.

Yeni bir insider risk yönetimi bildirim şablonu oluşturmak için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **Bildirim şablonları** sekmesini seçin.
2. Bildirim oluşturma aracını açmak için Bildirim **şablonu oluştur'u** seçin.
3. **Yeni bildirim şablonu oluştur** sayfasında aşağıdaki alanları doldurun:
    - **Şablon adı**: Bildirim için kolay bir ad girin. Bu ad, bildirim panosundaki bildirimler listesinde ve servis talebiyle ilgili bildirimler gönderilirken bildirim seçimi listesinde görünür.
    - **Gönderen**: Bildirim için gönderen e-posta adresini girin. Bu adres, servis talebi bildirimi gönderilirken değiştirilmediği sürece kullanıcılara gönderilen tüm bildirimlerde **Kimden:** alanında görünür.
    - **Bilgi ve Gizli** alanları: aboneliğiniz için Active Directory'den seçilen ilke eşleşmesinin bildirilmesi için isteğe bağlı kullanıcılar veya gruplar.
    - **Konu**: İletinin konu satırında görünen bilgiler metin karakterlerini destekler.
    - **İleti gövdesi: İleti** gövdesinde görünen bilgiler metin veya HTML değerlerini destekler.
4. Bildirim şablonunu oluşturup kaydetmek için **Oluştur'u** veya bildirim şablonunu kaydetmeden kapatmak için **İptal'i** seçin.

## <a name="update-a-notice-template"></a>Bildirim şablonunu güncelleştirme

Mevcut bir insider risk yönetimi bildirim şablonunu güncelleştirmek için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **Bildirim şablonları** sekmesini seçin.
2. Bildirim panosunda, yönetmek istediğiniz bildirim şablonunu seçin.
3. Bildirim ayrıntıları sayfasında **Düzenle'yi** seçin
4. **Düzenle** sayfasında, aşağıdaki alanları düzenleyebilirsiniz:
    - **Şablon adı**: Bildirim için yeni bir kolay ad girin. Bu ad, bildirim panosundaki bildirimler listesinde ve servis talebiyle ilgili bildirimler gönderilirken bildirim seçimi listesinde görünür.
    - **Gönderen:** Bildirim için gönderen e-posta adresini güncelleştirin. Bu adres, servis talebi bildirimi gönderilirken değiştirilmediği sürece kullanıcılara gönderilen tüm bildirimlerde **Kimden:** alanında görünür.
    - **Bilgi ve Gizli** alanları: aboneliğiniz için Active Directory'den seçilen ilke eşleşmesinin bildirilmesi için isteğe bağlı kullanıcıları veya grupları güncelleştirin.
    - **Konu**: İletinin konu satırında görünen bilgileri güncelleştirin, metin karakterlerini destekler.
    - **İleti gövdesi: İleti** gövdesinde görünen bilgileri güncelleştirin, metin veya HTML değerlerini destekler.
5. Bildirimi güncelleştirmek ve kaydetmek için **Kaydet'i** veya bildirim şablonunu kaydetmeden kapatmak için **İptal'i** seçin.

## <a name="delete-a-notice-template"></a>Bildirim şablonunu silme

Mevcut bir insider risk yönetimi bildirim şablonunu silmek için aşağıdaki adımları tamamlayın:

1. [Microsoft Purview uyumluluk portalı](https://compliance.microsoft.com) **Insider risk yönetimi'ne** gidin ve **Bildirim şablonları** sekmesini seçin.
2. Bildirim panosunda silmek istediğiniz bildirim şablonunu seçin.
3. Araç **çubuğunda Sil simgesini** seçin.
4. Bildirim şablonunu silmek için sil iletişim kutusunda **Evet'i** seçin. Silme işlemini iptal etmek için **İptal'i** seçin.
