---
title: Microsoft Purview Uyumluluk Yöneticisi'nde değerlendirme şablonları oluşturma
f1.keywords:
- NOCSH
ms.author: chvukosw
author: chvukosw
manager: laurawi
audience: Admin
ms.topic: article
ms.custom: admindeeplinkMAC
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365solution-compliancemanager
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: Microsoft Purview Uyumluluk Yöneticisi'nde değerlendirmeler için şablon oluşturmayı öğrenin. Biçimlendirilmiş bir Excel dosyası kullanarak şablon oluşturma ve değiştirme.
ms.openlocfilehash: f7198d9b7bb9c30d388924d9c1b16a79e86bb8ee
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638674"
---
# <a name="create-an-assessment-template-in-microsoft-purview-compliance-manager"></a>Microsoft Purview Uyumluluk Yöneticisi'nde değerlendirme şablonu oluşturma

Compliance Manager'da özel değerlendirmeler için kendi yeni şablonunuzu oluşturmak için, gerekli denetim verilerini bir araya getirmek üzere özel olarak biçimlendirilmiş bir Excel elektronik tablosu kullanacaksınız. Elektronik tabloyu tamamladıktan sonra Uyumluluk Yöneticisi'ne aktaracaksınız.

Elektronik tablonuzu biçimlendirme hakkında bilgi edinmek için bkz. [Değerlendirme şablonu verilerini Excel ile biçimlendirme](compliance-manager-templates-format-excel.md).

## <a name="required-roles"></a>Gerekli roller

Şablonları yalnızca Genel Yönetici veya Uyumluluk Yöneticisi Yönetimi rolüne sahip kullanıcılar oluşturabilir ve değiştirebilir. [Roller ve izinler](compliance-manager-setup.md#set-user-permissions-and-assign-roles) hakkında daha fazla bilgi edinin.

## <a name="create-new-template-in-compliance-manager"></a>Uyumluluk Yöneticisi'nde yeni şablon oluşturma

1. Uyumluluk Yöneticisi'ndeki **değerlendirme şablonları** sayfanıza gidin.
2. **Yeni şablon oluştur'u** seçin. Şablon oluşturma sihirbazı açılır.
3. Oluşturmak istediğiniz şablon türünü seçin. Bu durumda **Özel şablon oluştur'u** ve ardından **İleri'yi** seçin.
4. **Dosyayı karşıya yükle** ekranında **Gözat'ı** seçerek tüm gerekli şablon verilerini içeren biçimlendirilmiş Excel dosyanızı bulun ve karşıya yükleyin.
5. Dosyanızla ilgili bir sorun yoksa, karşıya yüklenen dosyanın adı görüntülenir. Devam etmek için **İleri'yi** seçin. (Dosyayı değiştirmeniz gerekiyorsa **Farklı bir dosya yükle'yi** seçin).
    - Dosyanızda bir hata varsa, en üstteki hata iletisi sorunun ne olduğunu açıklar. Dosyanızı düzeltmeniz ve yeniden karşıya yüklemeniz gerekir. Elektronik tablonuz yanlış biçimlendirilirse veya belirli alanlarda geçersiz bilgiler varsa hatalar oluşur.
6. **Gözden geçir ve bitir** ekranı, iyileştirme eylemlerinin ve denetimlerinin sayısını ve şablonun en yüksek puanını gösterir. Onaylamaya hazır olduğunuzda **Şablon oluştur'u seçin.** (Değişiklik yapmanız gerekiyorsa **Geri'yi** seçin.)
7. Son ekranda yeni bir şablon oluşturulduğu onaylanır. **Sihirbazdan çıkmak için Bitti'yi** seçin.
8. [Değerlendirmenizi oluşturabileceğiniz](compliance-manager-assessments.md#create-assessments) yeni şablonunuzun ayrıntılar sayfasına ulaşırsınız.
