---
title: Cihaz koruma ilkelerini görüntüleme veya düzenleme
description: Mobil cihazda cihaz koruma ilkelerini görüntüleme, düzenleme, oluşturma ve Microsoft 365 İş Ekstra
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/08/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: ba322493b3900c099ab5525f052604604ef0ac23
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63705482"
---
# <a name="view-and-edit-your-device-protection-policies"></a>Cihaz koruma ilkelerinizi görüntüleme ve düzenleme

Daha Microsoft 365 İş Ekstra, yönetilen cihazların güvenlik ayarları cihaz koruma ilkeleri aracılığıyla yapılandırılır. Kurulum ve yapılandırma deneyiminizi basitleştirmeye yardımcı olmak için, önceden yapılandırılmış ilkeleriniz vardır ve bu ilkeler hazır bulundurur olmaz kuruluş cihazlarınızı korumaya yardımcı olabilir. Varsayılan ilkeleri kullanabilir, ilkeleri düzenleyebilir veya kendi ilkelerinizi oluşturabilirsiniz.

**Bu makalede şunların nasıl olduğu açıklanmıştır**:

- Varsayılan ilkelerinize genel bir bakış elde
- Var olan ilkelerinizi görüntüleme
- Var olan bir ilkeyi düzenleme
- Yeni ilke oluşturma

## <a name="default-device-protection-policies"></a>Varsayılan cihaz koruma ilkeleri

Microsoft 365 İş Ekstra, kuruluş cihazlarınızı korumak için iki ana ilke türü içerir:

- **Yeni nesil koruma ilkelerinin** nasıl yapılandır Microsoft Defender Virüsten Koruma diğer tehdit koruması özelliklerinin nasıl yapılandırıldığından emin olun

- **Hangi ağ** trafiğinin kuruluş cihazlarına ve bu cihazlardan akışa izin verdiğini belirleyen güvenlik duvarı ilkeleri

Bu ilkeler, Microsoft 365 İş Ekstra aboneliğinize dahil olan Microsoft Defender for Business'Microsoft 365 İş Ekstra vardır.

## <a name="view-your-existing-device-protection-policies"></a>Mevcut cihaz koruma ilkelerinizi görüntüleme

1. Microsoft 365 Defender portalına () gidin[https://security.microsoft.com](https://security.microsoft.com) ve oturum açın. 

2. Gezinti bölmesinde Cihaz **yapılandırması'ni seçin**. İlkeler, işletim sistemi (Windows **istemcisi** gibi) ve ilke türüne (Yeni nesil koruma ve Güvenlik Duvarı **gibi)** göre **düzenlenmiştir**. 

3. Bir işletim sistemi sekmesi seçin (örneğin, **Windows)** ve sonra Yeni Nesil Koruma ve Güvenlik Duvarı kategorileri altındaki **ilkeler** **listesini gözden** geçirebilirsiniz. 

4. İlke hakkında daha fazla ayrıntı görüntülemek için, ilkenin adını seçin. Bu ilke hakkında daha fazla bilgi sağlayan, örneğin bu ilke tarafından korunan cihazlar gibi bir yan bölme açılır.

## <a name="edit-an-existing-device-protection-policy"></a>Mevcut bir cihaz koruma ilkesi düzenleme

1. Microsoft 365 Defender portalına () gidin[https://security.microsoft.com](https://security.microsoft.com) ve oturum açın. 

2. Gezinti bölmesinde Cihaz **yapılandırması'ni seçin**. İlkeler, işletim sistemi (Windows **istemcisi** gibi) ve ilke türüne (Yeni nesil koruma ve Güvenlik Duvarı **gibi)** göre **düzenlenmiştir**. 

3. Bir işletim sistemi sekmesi seçin (örneğin, **Windows)** ve sonra Yeni Nesil Koruma ve Güvenlik Duvarı kategorileri altındaki **ilkeler** **listesini gözden** geçirebilirsiniz. 

4. Bir ilkeyi düzenlemek için, ilkenin adını seçin ve sonra da Düzenle'yi **seçin**.

5. Genel **bilgiler sekmesinde** bilgileri gözden geçirebilirsiniz. Gerekirse, açıklamayı düzenleyebilirsiniz. Sonra, **Sonraki'yi seçin**.

6. Cihaz grupları **sekmesinde** , bu ilkeyi hangi cihaz gruplarının alaları gerektiğini seçin.  

   - Seçili cihaz grubunu olduğu gibi tutmak için Sonraki'yi **seçin**.
   - Bir cihaz grubunu ilkeden kaldırmak için Kaldır'ı **seçin**.
   - Yeni bir cihaz grubu ayarlamak için Yeni grup **oluştur'a** ve ardından cihaz grubunızı ayarlayın. (Bu görevle ilgili yardım almak için bkz. [Microsoft 365 İş Ekstra](m365bp-device-groups-mdb.md).)
   - İlkeyi başka bir cihaz grubuna uygulamak için Varolan grubu **kullan'ı seçin**.

   hangi cihaz gruplarının ilkeyi alsı gerektiğini belirttikten sonra, Sonraki'yi **seçin**.

7. Yapılandırma **ayarları sekmesinde** ayarları gözden geçirin. Gerekirse, ilkenizin ayarlarını düzenleyebilirsiniz. Bu görevle ilgili yardım almak için aşağıdaki makalelere bakın: 

   - [Yeni nesil yapılandırma ayarlarını anlama](../security/defender-business/mdb-next-gen-configuration-settings.md)   
   - [Güvenlik duvarı ayarları](../security/defender-business/mdb-firewall.md)

   Yeni nesil koruma ayarlarınızı belirttikten sonra, Sonraki'yi **seçin**.

8. **İlkenizi gözden geçirme** sekmesinde genel bilgileri, hedefli cihazları ve yapılandırma ayarlarını gözden geçirebilirsiniz. 

   - Düzenle'yi seçerek gerekli değişiklikleri **yapın**.
   - Devam etmeye hazır olduğunda İlkeyi **güncelleştir'i seçin**.

## <a name="create-a-new-device-protection-policy"></a>Yeni bir cihaz koruma ilkesi oluşturma

1. Microsoft 365 Defender portalına () gidin[https://security.microsoft.com](https://security.microsoft.com) ve oturum açın. 

2. Gezinti bölmesinde Cihaz **yapılandırması'ni seçin**. İlkeler, işletim sistemi (Windows **istemcisi** gibi) ve ilke türüne (Yeni nesil koruma ve Güvenlik Duvarı **gibi)** göre **düzenlenmiştir**. 

3. Bir işletim sistemi sekmesi seçin (örneğin, **Windows)** ve sonra Yeni nesil koruma ilkeleri **listesini gözden** geçirebilirsiniz. 

4. Yeni **nesil koruma veya Güvenlik Duvarı'nın** **altında** **+ Ekle'yi seçin**.

5. Genel **bilgiler sekmesinde** aşağıdaki adımları izleyin:

   1. Ad ve açıklama belirtin. Bu bilgiler, sizin ve ekibinin daha sonra ilkeyi belirlemenize yardımcı olur.
   2. İlke sırayı gözden geçirin ve gerekirse düzenleyin. (Daha fazla bilgi için bkz. [İlke sırası](../security/defender-business/mdb-policy-order.md).)
   3. **İleri**'yi seçin. 

7. Cihaz **grupları sekmesinde** yeni bir cihaz grubu oluşturun veya varolan bir grubu kullanın. İlkeler cihaz grupları aracılığıyla cihazlara atanır. Şunları unutmayın:

   - Başlangıçta, yalnızca, kuruluş verilerinize ve e-postanıza erişmek için kuruluşta yer alan kişilerin cihazları içeren varsayılan cihaz grubunuz olabilir. Varsayılan cihaz grubunızı saklayarak kullanabilirsiniz.
   - Varsayılan ilkeden farklı olan belirli ayarlara sahip bir ilke uygulamak için yeni bir cihaz grubu oluşturun. 
   - Cihaz grubunızı ayar yukarıya doğru ayar ilk olarak işletim sistemi sürümü gibi belirli ölçütleri belirtirsiniz. Ölçütleri karşılanan cihazlar, siz dışlamadıysanız bu cihaz grubuna dahil edilir. 
   - Tanımladığınız varsayılan ve özel cihaz grupları dahil olmak üzere tüm cihaz grupları Azure Active Directory (Azure AD) içinde depolanır.

   Cihaz grupları hakkında daha fazla bilgi edinmek için bkz [. İş için Microsoft Defender'da cihaz grupları](../security/defender-business/mdb-create-edit-device-groups.md).

8. Yapılandırma **ayarları sekmesinde** , ilkenizin ayarlarını belirtin ve sonra da Sonraki'yi **seçin**. Tek tek ayarlar hakkında daha fazla bilgi için bkz. [İş için Microsoft Defender'da yeni nesil yapılandırma ayarlarını anlama](../security/defender-business/mdb-next-gen-configuration-settings.md).

9. **İlkenizi gözden geçirme** sekmesinde genel bilgileri, hedefli cihazları ve yapılandırma ayarlarını gözden geçirebilirsiniz. 

   - Düzenle'yi seçerek gerekli değişiklikleri **yapın**.
   - Devam etmeye hazır olduğunda İlke **oluştur'a seçin**.


## <a name="next-steps"></a>Sonraki adımlar

[Microsoft 365 İş Ekstra'da cihaz Microsoft 365 İş Ekstra](m365bp-device-groups-mdb.md)