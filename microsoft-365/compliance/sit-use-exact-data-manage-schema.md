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
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Tam veri eşleşme şemanızı düzenlemeyi veya kaldırmayı öğrenin.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: c3ce2620a95401fcd34d2a84378d2e544cd66e4d
ms.sourcegitcommit: 99067d5eb1fa7b094e7cdb1f7be65acaaa235a54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2022
ms.locfileid: "63010073"
---
# <a name="manage-your-exact-data-match-schema"></a>Tam veri eşleşme şemanızı yönetme

## <a name="editing-the-schema-for-edm-based-classification-manually"></a>EDM tabanlı sınıflandırma için şemayı el ile düzenleme

EDM şemanız üzerinde, örneğin **edm.xml** dosyasında, EDM tabanlı sınıflandırmada kullanılacak alanları değiştirmek gibi değişiklikler yapmak için aşağıdaki adımları izleyin:

> [!TIP]
> Yapılandırılabilir eşleşmeden yararlanmak için EDM şemanızı ve hassas bilgiler tablo kaynak **dosyanızı değiştirebilirsiniz**. Yapılandırıldığında, EDM bir öğeyi değerlendirirken büyük/küçük harf farklarını ve bazı sınırlayıcıları yoksayar. Bu, XML şemanızı ve hassas veri dosyalarınızı tanımlamayı kolaylaştırır. Daha fazla bilgi için bkz [. Büyük/harfe duyarlı değil ve yoksayılanDelimiters alanlarını kullanma](sit-get-started-exact-data-match-create-schema.md#using-the-caseinsensitive-and-ignoreddelimiters-fields).

1. Özel **dosyanızıedm.xml** (bu, Temel alınan hassas bilgi türlerine göre tam veri eşleşmesi için şema oluşturma konusunda [açıklanan dosyadır](sit-get-started-exact-data-match-create-schema.md#create-the-schema-for-exact-data-match-based-sensitive-information-types)).

2. [Bağlan ve Uyumluluk & PowerShell'e.](/powershell/exchange/connect-to-scc-powershell)

3. Veritabanı şemanızı güncelleştirmek için aşağıdaki komutu çalıştırın:

      ```powershell
      Set-DlpEdmSchema -FileData ([System.IO.File]::ReadAllBytes('.\\edm.xml')) -Confirm:$true
      ```

      Aşağıdaki gibi onaylamanız istenir:

      > Onayla
      >
      > Bu eylemi gerçekleştirmek istediğinizden emin misiniz?
      >
      > 'patientrecords' veri deposu için EDM Şeması güncelleştirilecek.
      >
      > \[Y\] Evet \[A\] Yes to All \[N No \[\] L\] No to All \[?\] Yardım (varsayılan değer "Y"dir):

      > [!TIP]
      > Değişikliklerinizin onay olmadan gerçekleşmesini istemiyorsanız, 3. `-Confirm:$true` Adım'da bu değişiklikleri kullanmayın.

      > [!NOTE]
      > EDMSchema'yı eklemelerle güncelleştirmek 10-60 dakika arasında sürebilir. Eklemeleri kullanan adımları yürütmeden önce güncelleştirmenin tamamlanması gerekir.

## <a name="removing-the-schema-for-edm-based-classification-manually"></a>EDM tabanlı sınıflandırma için şemayı el ile kaldırma

EDM tabanlı sınıflandırma için kullanmakta olduğunu şemayı kaldırmak için aşağıdaki adımları izleyin:

1. [Bağlan ve Uyumluluk & PowerShell'e.](/powershell/exchange/connect-to-scc-powershell)

2. Kaldırmak istediğiniz kayıtla "hasta kayıtları" veri deposu adını kullanarak (örnek olarak patientrecords depounu kullanarak) aşağıdaki komutu çalıştırın:

      ```powershell
      Remove-DlpEdmSchema -Identity 'patientrecords'
      ```

      Şunları onaylamanız istenir:

      > Onayla
      >
      > Bu eylemi gerçekleştirmek istediğinizden emin misiniz?
      >
      > 'patientrecords' veri deposu için EDM Şeması kaldırılacaktır.
      >
      > \[Y\] Evet \[A\] Yes to All \[N No \[\] L\] No to All \[?\] Yardım (varsayılan değer "Y"dir):

      > [!TIP]
      > Değişikliklerinizin onay olmadan gerçekleşmesini istemiyorsanız, 2. `-Confirm:$true` Adım'da bu değişiklikleri kullanmayın.

### <a name="edit-or-delete-the-edm-schema-with-the-wizard"></a>Sihirbazla EDM şemasını düzenleme veya silme

1. Uyumluluk **merkezi Veri** \> **sınıflandırması** \> **Tam veri eşleşmeleri'ne bakın**.

2. **EDM şemalarını seçin**.

3. Düzenlemek istediğiniz EDM SIT'i seçin.

4. **Çıktıdan EDM şemasını** **Düzenle veya EDM** şemasını sil'i seçin.

> [!IMPORTANT]
> Şemayı kaldırmak istiyorsanız ve zaten bir EDM duyarlı bilgi türüyle ilişkilendirilmişse, önce EDM duyarlı bilgi türünü silmeniz gerekir; ardından şemayı silebilirsiniz.
