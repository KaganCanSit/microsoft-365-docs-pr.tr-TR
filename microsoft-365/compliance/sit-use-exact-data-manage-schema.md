---
title: Tam veri eşleşme şemanızı yönetme
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: how-to
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Tam veri eşleştirme şemanızı düzenlemeyi veya kaldırmayı öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 29cfefbd6bf9bb9f92fe5ed7664575ec75adfa12
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014684"
---
# <a name="manage-your-exact-data-match-schema"></a>Tam veri eşleşme şemanızı yönetme

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

## <a name="editing-the-schema-for-edm-based-classification-manually"></a>EDM tabanlı sınıflandırma için şemayı el ile düzenleme

EDM şemanızda, örneğin **edm.xml** dosyasında, EDM tabanlı sınıflandırma için kullanılan alanları değiştirme gibi değişiklikler yapmak istiyorsanız şu adımları izleyin:

> [!TIP]
> **Yapılandırılabilir eşleşmeden** yararlanmak için EDM şemanızı ve hassas bilgiler tablosu kaynak dosyanızı değiştirebilirsiniz. Yapılandırıldığında, EDM bir öğeyi değerlendirirken büyük/küçük harf farklarını ve bazı sınırlayıcıları yoksayar. Bu, xml şemanızı ve hassas veri dosyalarınızı tanımlamayı kolaylaştırır. Daha fazla bilgi edinmek için bkz. [caseInsensitive ve ignoredDelimiters alanlarını kullanma](sit-get-started-exact-data-match-create-schema.md#using-the-caseinsensitive-and-ignoreddelimiters-fields).

1. **edm.xml** dosyanızı düzenleyin (bu dosya, [Tam veri eşleştirmeye dayalı hassas bilgi türleri için şema oluşturma](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types) bölümünde açıklanan dosyadır.

2. [Güvenlik & Uyumluluğu PowerShell'e Bağlan](/powershell/exchange/connect-to-scc-powershell).

3. Veritabanı şemanızı güncelleştirmek için aşağıdaki komutu çalıştırın:

      ```powershell
      Set-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
      ```

      Aşağıdaki gibi onaylamanız istenir:

      > Onaylamak
      >
      > Bu eylemi gerçekleştirmek istediğinizden emin misiniz?
      >
      > 'patientrecords' veri deposu için EDM Şeması güncelleştirilecektir.
      >
      > \[Y\] Evet \[\] Tümüne \[Evet N\] Hayır \[L\] Tümüne \[Hayır?\] Yardım (varsayılan olarak "Y"dir):

      > [!TIP]
      > Değişikliklerinizin onay olmadan gerçekleşmesini istiyorsanız 3. Adım'da kullanmayın `-Confirm:$true` .

      > [!NOTE]
      > EDMSchema'nın eklenmesi 10-60 dakika arasında sürebilir. Eklemeleri kullanan adımları yürütmeden önce güncelleştirmenin tamamlanması gerekir.

## <a name="removing-the-schema-for-edm-based-classification-manually"></a>EDM tabanlı sınıflandırma için şemayı el ile kaldırma

EDM tabanlı sınıflandırma için kullandığınız şemayı kaldırmak istiyorsanız şu adımları izleyin:

1. [Güvenlik & Uyumluluğu PowerShell'e Bağlan](/powershell/exchange/connect-to-scc-powershell).

2. Kaldırmak istediğiniz "hasta kayıtlarının" veri deposu adını (örnek olarak patientrecords deposunu kullanarak) değiştirerek aşağıdaki komutu çalıştırın:

      ```powershell
      Remove-DlpEdmSchema -Identity 'patientrecords'
      ```

      Sizden şunu onaylamanız istenir:

      > Onaylamak
      >
      > Bu eylemi gerçekleştirmek istediğinizden emin misiniz?
      >
      > 'patientrecords' veri deposu için EDM Şeması kaldırılır.
      >
      > \[Y\] Evet \[\] Tümüne \[Evet N\] Hayır \[L\] Tümüne \[Hayır?\] Yardım (varsayılan olarak "Y"dir):

      > [!TIP]
      > Değişikliklerinizin onay olmadan gerçekleşmesini istiyorsanız 2. Adım'da kullanmayın `-Confirm:$true` .

### <a name="edit-or-delete-the-edm-schema-with-the-wizard"></a>Sihirbazla EDM şemasını düzenleme veya silme

1. **Uyumluluk merkezi** \> **Veri sınıflandırması** \> **Tam veri eşleşmelerini** açın.

2. **EDM şemaları'nı** seçin.

3. Düzenlemek istediğiniz EDM SIT'i seçin.

4. **Açılır menüden EDM şemasını düzenle** veya **EDM şemasını sil'i** seçin.

> [!IMPORTANT]
> Bir şemayı kaldırmak istiyorsanız ve zaten bir EDM hassas bilgi türüyle ilişkiliyse, önce EDM hassas bilgi türünü silmeniz gerekir, ardından şemayı silebilirsiniz.
