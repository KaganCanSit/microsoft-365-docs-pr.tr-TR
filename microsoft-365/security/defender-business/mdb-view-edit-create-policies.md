---
title: İş için Microsoft Defender'da ilkeleri görüntüleme veya düzenleme (önizleme)
description: İş için Microsoft Defender'da (önizleme) yeni nesil koruma ilkelerini görüntülemeyi, düzenlemeyi, oluşturmayı ve silmeyi öğrenin
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/03/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 81cd2774115478f4d85fa1878d7ce8a598600e7f
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63027526"
---
# <a name="view-or-edit-policies-in-microsoft-defender-for-business-preview"></a>İş için Microsoft Defender'da ilkeleri görüntüleme veya düzenleme (önizleme)

> [!IMPORTANT]
> İş için Microsoft Defender şu anda önizlemede ve istekte etmek için buraya kaydolan müşterilere ve IT [İş Ortaklarına aşamalı](https://aka.ms/mdb-preview) olarak aşamalı olarak aşamalı olarak sunulmaktadır. Önümüzdeki haftalarda bir ilk müşteri ve iş ortağı kümesi sunuyoruz ve genel kullanılabilirlik durumuna kadar önizlemeyi genişleteceğiz. Önizlemenin bir dizi ilk [senaryoyla başlat olacağını](mdb-tutorials.md#try-these-preview-scenarios) ve düzenli olarak özellikler ekley olacacaz.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

İş için Microsoft Defender(önizleme) içinde, güvenlik ayarları cihazlara uygulanan ilkeler aracılığıyla yapılandırılır. Kurulum ve yapılandırma deneyiminizi basitleştirmeye yardımcı olmak için, Defender İş (önizleme), dahil edildik anda kuruluş cihazlarınızı korumaya yardımcı olacak önceden yapılandırılmış ilkeler içerir. Varsayılan ilkeleri kullanabilir, ilkeleri düzenleyebilir veya kendi ilkelerinizi oluşturabilirsiniz.

**Bu makalede şunların nasıl olduğu açıklanmıştır**:

- [Varsayılan ilkelerinize genel bir bakış elde](#default-policies-in-defender-for-business)
- [Var olan ilkelerinizi görüntüleme](#view-your-existing-policies)
- [Var olan bir ilkeyi düzenleme](#edit-an-existing-policy)
- [Yeni ilke oluşturma](#create-a-new-policy)

>
> **Bir dakika mı kaldı?**
> Lütfen İş için <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">Microsoft Defender ile ilgili kısa ankete göz atyın</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

## <a name="default-policies-in-defender-for-business"></a>İş için Defender'da varsayılan ilkeler

İş için Defender'da (önizleme), kuruluş cihazlarınızı korumak için iki ana ilke türü vardır:

- **Yeni nesil koruma ilkelerinin** nasıl yapılandır Microsoft Defender Virüsten Koruma diğer tehdit koruması özelliklerinin nasıl yapılandırıldığından emin olun
- **Hangi ağ** trafiğinin kuruluş cihazlarına ve bu cihazlardan akışa izin verdiğini belirleyen güvenlik duvarı ilkeleri


## <a name="view-your-existing-policies"></a>Var olan ilkelerinizi görüntüleme

1. Microsoft 365 Defender portalına () gidin[https://security.microsoft.com](https://security.microsoft.com) ve oturum açın. 

2. Gezinti bölmesinde Cihaz **yapılandırması'ni seçin**. İlkeler, işletim sistemi (Windows **istemcisi** gibi) ve ilke türüne (Yeni nesil koruma ve Güvenlik Duvarı **gibi)** göre **düzenlenmiştir**. 

3. Bir işletim sistemi sekmesi seçin (örneğin, **Windows)** ve sonra Yeni Nesil Koruma ve Güvenlik Duvarı kategorileri altındaki **ilkeler** **listesini gözden** geçirebilirsiniz. 

4. İlke hakkında daha fazla ayrıntı görüntülemek için, ilkenin adını seçin. Bu ilke hakkında daha fazla bilgi sağlayan, örneğin bu ilke tarafından korunan cihazlar gibi bir yan bölme açılır.

## <a name="edit-an-existing-policy"></a>Var olan bir ilkeyi düzenleme

1. Microsoft 365 Defender portalına () gidin[https://security.microsoft.com](https://security.microsoft.com) ve oturum açın. 

2. Gezinti bölmesinde Cihaz **yapılandırması'ni seçin**. İlkeler, işletim sistemi (Windows **istemcisi** gibi) ve ilke türüne (Yeni nesil koruma ve Güvenlik Duvarı **gibi)** göre **düzenlenmiştir**. 

3. Bir işletim sistemi sekmesi seçin (örneğin, **Windows)** ve sonra Yeni Nesil Koruma ve Güvenlik Duvarı kategorileri altındaki **ilkeler** **listesini gözden** geçirebilirsiniz. 

4. Bir ilkeyi düzenlemek için, ilkenin adını seçin ve sonra da Düzenle'yi **seçin**.

5. Genel **bilgiler sekmesinde** bilgileri gözden geçirebilirsiniz. Gerekirse, açıklamayı düzenleyebilirsiniz. Sonra, **Sonraki'yi seçin**.

6. Cihaz grupları **sekmesinde** , bu ilkeyi hangi cihaz gruplarının alaları gerektiğini seçin.  

   - Seçili cihaz grubunu olduğu gibi tutmak için Sonraki'yi **seçin**.
   - Bir cihaz grubunu ilkeden kaldırmak için Kaldır'ı **seçin**.
   - Yeni bir cihaz grubu ayarlamak için Yeni grup **oluştur'a** ve ardından cihaz grubunızı ayarlayın. (Bu görevle ilgili yardım almak için bkz [. Microsoft Defender İş'te cihaz grupları (önizleme))](mdb-create-edit-device-groups.md))
   - İlkeyi başka bir cihaz grubuna uygulamak için Varolan grubu **kullan'ı seçin**.

   hangi cihaz gruplarının ilkeyi alsı gerektiğini belirttikten sonra, Sonraki'yi **seçin**.

7. Yapılandırma **ayarları sekmesinde** ayarları gözden geçirin. Gerekirse, ilkenizin ayarlarını düzenleyebilirsiniz. Bu görevle ilgili yardım almak için aşağıdaki makalelere bakın: 

   - [Yeni nesil yapılandırma ayarlarını anlama](mdb-next-gen-configuration-settings.md)   
   - [Güvenlik duvarı ayarları](mdb-firewall.md)

   Yeni nesil koruma ayarlarınızı belirttikten sonra, Sonraki'yi **seçin**.

8. **İlkenizi gözden geçirme** sekmesinde genel bilgileri, hedefli cihazları ve yapılandırma ayarlarını gözden geçirebilirsiniz. 

   - Düzenle'yi seçerek gerekli değişiklikleri **yapın**.
   - Devam etmeye hazır olduğunda İlkeyi **güncelleştir'i seçin**.

## <a name="create-a-new-policy"></a>Yeni ilke oluşturma

1. Microsoft 365 Defender portalına () gidin[https://security.microsoft.com](https://security.microsoft.com) ve oturum açın. 

2. Gezinti bölmesinde Cihaz **yapılandırması'ni seçin**. İlkeler, işletim sistemi (Windows **istemcisi** gibi) ve ilke türüne (Yeni nesil koruma ve Güvenlik Duvarı **gibi)** göre **düzenlenmiştir**. 

3. Bir işletim sistemi sekmesi seçin (örneğin, **Windows)** ve sonra Yeni nesil koruma ilkeleri **listesini gözden** geçirebilirsiniz. 

4. Yeni **nesil koruma veya Güvenlik Duvarı'nın** **altında** **+ Ekle'yi seçin**.

5. Genel **bilgiler sekmesinde** aşağıdaki adımları izleyin:

   1. Ad ve açıklama belirtin. Bu bilgiler, sizin ve ekibinin daha sonra ilkeyi belirlemenize yardımcı olur.
   2. İlke sırayı gözden geçirin ve gerekirse düzenleyin. (Daha fazla bilgi için bkz. [İlke sırası](mdb-policy-order.md).)
   3. **İleri**'yi seçin. 

7. Cihaz **grupları sekmesinde** yeni bir cihaz grubu oluşturun veya varolan bir grubu kullanın. İlkeler cihaz grupları aracılığıyla cihazlara atanır. Şunları unutmayın:

   - Başlangıçta, yalnızca, kuruluş verilerinize ve e-postanıza erişmek için kuruluşta yer alan kişilerin cihazları içeren varsayılan cihaz grubunuz olabilir. Varsayılan cihaz grubunızı saklayarak kullanabilirsiniz.
   - Varsayılan ilkeden farklı olan belirli ayarlara sahip bir ilke uygulamak için yeni bir cihaz grubu oluşturun. 
   - Cihaz grubunızı ayar yukarıya doğru ayar ilk olarak işletim sistemi sürümü gibi belirli ölçütleri belirtirsiniz. Ölçütleri karşılanan cihazlar, siz dışlamadıysanız bu cihaz grubuna dahil edilir. 
   - Tanımladığınız varsayılan ve özel cihaz grupları dahil olmak üzere tüm cihaz grupları Azure Active Directory (Azure AD) içinde depolanır.

   Cihaz grupları hakkında daha fazla bilgi edinmek için bkz [. İş için Defender'da (önizleme) cihaz grupları](mdb-create-edit-device-groups.md).

8. Yapılandırma **ayarları sekmesinde** , ilkenizin ayarlarını belirtin ve sonra da Sonraki'yi **seçin**. Tek tek ayarlar hakkında daha fazla bilgi için bkz [. İş için Microsoft Defender'ın yapılandırma ayarları (önizleme).](mdb-next-gen-configuration-settings.md).

9. **İlkenizi gözden geçirme** sekmesinde genel bilgileri, hedefli cihazları ve yapılandırma ayarlarını gözden geçirebilirsiniz. 

   - Düzenle'yi seçerek gerekli değişiklikleri **yapın**.
   - Devam etmeye hazır olduğunda İlke **oluştur'a seçin**.


## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki görevlerden birini veya daha fazlasını seçin:

- [Cihazları yönet](mdb-manage-devices.md)

- [İş için Microsoft Defender'da (önizleme) yeni ilke oluşturma](mdb-create-new-policy.md)

- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme (önizleme)](mdb-view-manage-incidents.md)

- [Microsoft Defender İş'te (önizleme) tehditlere yanıt verme ve tehditlerini azaltmak](mdb-respond-mitigate-threats.md)

- [İşlem merkezinde düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)