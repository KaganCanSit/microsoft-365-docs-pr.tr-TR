---
title: Şifreli e-posta gönderme
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
ms.date: 03/08/2022
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- Core_O365Admin_Migration
- MiniMaven
- MSB365
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
ms.assetid: 496e690b-b75d-4ff5-bf34-cc32905d0364
description: Outlook kullanarak şifrelenmiş e-posta göndermeyi öğrenin.
ms.openlocfilehash: b9b2251114831bfe0b6364dc4327bd0c21da55e2
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65316842"
---
# <a name="encrypt-or-label-sensitive-email"></a>Hassas e-postayı şifreleme veya etiketleme

Verileriniz ve bilgileriniz önemlidir ve genellikle gizlidir. Buradaki amaç, e-posta alıcılarının bilgileri en yüksek hassasiyetle ele almaları için herkesin duyarlılık etiketlerini kullanmasını sağlayarak bu hassas bilgilerin korunmasına yardımcı olmaktır.

## <a name="best-practices"></a>En iyi uygulamalar

Kişiler gizli veya hassas bilgiler içeren e-posta göndermeden önce şunları açmayı düşünmelidir:

- **Şifreleme:** E-postadaki bilgilerin gizliliğini korumak için e-postanızı şifreleyebilirsiniz. Bir e-posta iletisini şifrelediğinizde, bu ileti okunabilir düz metinden karışık şifre metnine dönüştürülür. Yalnızca iletiyi şifrelemek için kullanılan ortak anahtarla eşleşen özel anahtara sahip olan alıcı, iletiyi okumak için çözebilir. Ancak, karşılık gelen özel anahtarı olmayan herhangi bir alıcı, şifrelenemez metin görür. Yöneticiniz belirli ölçütlere uyan iletileri otomatik olarak şifrelemek için kurallar tanımlayabilir. Örneğin, yöneticiniz kuruluşunuzun dışına gönderilen tüm iletileri veya belirli sözcüklerden veya tümceciklerden bahseden tüm iletileri şifreleyen bir kural oluşturabilir. Tüm şifreleme kuralları otomatik olarak uygulanır.

- **Duyarlılık etiketleri:** Kuruluşunuz bunu gerektiriyorsa, bunları kuruluşunuzun bilgi koruma ilkeleriyle uyumlu tutmak için dosyalarınıza ve e-postanıza uyguladığınız duyarlılık etiketlerini ayarlayabilirsiniz. Bir etiket ayarladığınızda, örneğin iletinizin üst bilgisi olarak görüntülenerek etiket e-postanız gönderildiğinde &mdash; bile e-postanızla birlikte kalır.

![Etiketler ve şifreleme için açıklama balonları içeren bir e-posta diyagramı.](../media/m365-campaign-email-encrypt.png)

## <a name="set-it-up"></a>Ayarlayın

Önceden tanımlanmış bir kurala uymayan bir iletiyi şifrelemek istiyorsanız veya yöneticiniz herhangi bir kural ayarlamadıysa, iletiyi göndermeden önce çeşitli farklı şifreleme kuralları uygulayabilirsiniz. Outlook 2013 veya 2016'dan veya Mac için Outlook 2016 şifrelenmiş ileti göndermek için **Seçenekler > İzinler'i** seçin ve ardından ihtiyacınız olan koruma seçeneğini belirleyin. Ayrıca Web üzerinde Outlook'de **Koru** düğmesini seçerek de şifreli bir ileti gönderebilirsiniz. Daha fazla bilgi için bkz. [Bilgisayar için Outlook şifrelenmiş iletileri gönderme, görüntüleme ve yanıtlama](https://support.microsoft.com/en-us/office/send-view-and-reply-to-encrypted-messages-in-outlook-for-pc-eaa43495-9bbb-4fca-922a-df90dee51980).

## <a name="admin-settings"></a>Yönetici ayarları

E-posta şifrelemeyi ayarlama hakkında her şeyi [Microsoft 365'de e-posta şifrelemesi](../compliance/email-encryption.md) bölümünden öğrenebilirsiniz.

### <a name="automatically-encrypt-email-messages"></a>E-posta iletilerini otomatik olarak şifreleme

Yöneticiler, bir kampanyadan veya işletmeden gönderilen ve alınan e-posta iletilerini otomatik olarak korumak için posta akışı kuralları oluşturabilir. Giden e-posta iletilerini şifrelemek için kurallar ayarlayın ve kuruluşunuzun içinden veya kuruluşunuzdan gönderilen şifrelenmiş iletilere verilen yanıtlardan gelen şifrelenmiş iletilerden şifrelemeyi kaldırın.

E-posta iletilerini Microsoft Purview İleti Şifrelemesi ile şifrelemek için posta akışı kuralları oluşturursunuz. <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezini (EAC)</a> kullanarak ileti şifrelemesini tetikleme için posta akışı kuralları tanımlayın.

1. Web tarayıcısında, genel yönetici izinleri verilmiş bir iş veya okul hesabı kullanarak oturum açın.
2. Yönetici kutucuğunu seçin.
3. Yönetim merkezinde Yönetim **merkezleri'ni > Exchange** seçin.

Daha fazla bilgi için bkz. [E-posta iletilerini şifrelemek için posta akışı kuralları tanımlama](../compliance/define-mail-flow-rules-to-encrypt-email.md).

### <a name="brand-your-encryption-messages"></a>Şifreleme iletilerinizi markala

E-posta iletilerindeki görünümü ve metni özelleştirmek için markalama da uygulayabilirsiniz. Daha fazla bilgi için bkz. [Şifrelenmiş iletilerinize kuruluşunuzun markasını ekleme](../compliance/email-encryption.md).

## <a name="next-mission"></a>Sonraki görev

Buraya kadar geldiyseniz, bir görevi daha başarıyla tamamladınız, tebrikler! Başarılarımızın üzerinde duracak zaman yok, bu nedenle ekibin güvenli bir [şekilde işbirliği](m365bp-collaborate-share-securely.md) yapabilecekleri güvenli ve güvenli bir ortam ayarlamaya başlayalım.