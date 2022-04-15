---
title: İş için Microsoft Defender'de ilkeleri görüntüleme veya düzenleme
description: İş için Microsoft Defender'de yeni nesil koruma ilkelerini görüntülemeyi, düzenlemeyi, oluşturmayı ve silmeyi öğrenin
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: ba7f6846809009b8bb9df258b8ac18536a910b6d
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64862136"
---
# <a name="view-or-edit-policies-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'de ilkeleri görüntüleme veya düzenleme

> [!NOTE]
> İş için Microsoft Defender artık [Microsoft 365 İş Ekstra](../../business-premium/index.md) dahil edilir. 

İş için Microsoft Defender'da, güvenlik ayarları cihazlara uygulanan ilkeler aracılığıyla yapılandırılır. İş için Defender, kurulum ve yapılandırma deneyiminizi basitleştirmeye yardımcı olmak için şirketinizin cihazlarının eklendikleri anda korunmasına yardımcı olmak için önceden yapılandırılmış ilkeler içerir. Varsayılan ilkeleri kullanabilir, ilkeleri düzenleyebilir veya kendi ilkelerinizi oluşturabilirsiniz.

**Bu makalede şunların nasıl yapılacağını açıklar**:

- [Varsayılan ilkelerinize genel bakış elde edin](#default-policies-in-defender-for-business)
- [Mevcut ilkelerinizi görüntüleme](#view-your-existing-policies)
- [Var olan bir ilkeyi düzenleme](#edit-an-existing-policy)
- [Yeni ilke oluşturma](#create-a-new-policy)

>
> **Bir dakikan var mı?**
> Lütfen <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">güvenlikle ilgili kısa anketimize</a> katılın. Sizden haber almak isteriz!
>

## <a name="default-policies-in-defender-for-business"></a>İş için Defender'da varsayılan ilkeler

İş için Defender'da, şirketinizin cihazlarını korumaya yönelik iki ana ilke türü vardır:

- Microsoft Defender Virüsten Koruma ve diğer tehdit koruma özelliklerinin nasıl yapılandırıldığını belirleyen **yeni nesil koruma ilkeleri**
- Şirketinizin cihazlarına hangi ağ trafiğinin akışına izin verileceğini belirleyen **güvenlik duvarı ilkeleri**


## <a name="view-your-existing-policies"></a>Mevcut ilkelerinizi görüntüleme

1. Microsoft 365 Defender portalına ()[https://security.microsoft.com](https://security.microsoft.com) gidin ve oturum açın. 

2. Gezinti bölmesinde **Cihaz yapılandırması'nı** seçin. İlkeler işletim sistemine (**Windows istemcisi** gibi) ve ilke türüne (**Yeni nesil koruma** ve **Güvenlik Duvarı** gibi) göre düzenlenir. 

3. bir işletim sistemi sekmesi (örneğin, **Windows istemcileri**) seçin ve ardından **Yeni nesil koruma** ve **Güvenlik Duvarı** kategorilerinin altındaki ilke listesini gözden geçirin. 

4. İlke hakkında daha fazla ayrıntı görüntülemek için adını seçin. İlkeyle korunan cihazlar gibi bu ilke hakkında daha fazla bilgi sağlayan bir yan bölme açılır.

## <a name="edit-an-existing-policy"></a>Var olan bir ilkeyi düzenleme

1. Microsoft 365 Defender portalına ()[https://security.microsoft.com](https://security.microsoft.com) gidin ve oturum açın. 

2. Gezinti bölmesinde **Cihaz yapılandırması'nı** seçin. İlkeler işletim sistemine (**Windows istemcisi** gibi) ve ilke türüne (**Yeni nesil koruma** ve **Güvenlik Duvarı** gibi) göre düzenlenir. 

3. bir işletim sistemi sekmesi (örneğin, **Windows istemcileri**) seçin ve ardından **Yeni nesil koruma** ve **Güvenlik Duvarı** kategorilerinin altındaki ilke listesini gözden geçirin. 

4. İlkeyi düzenlemek için, ilkenin adını ve ardından **Düzenle'yi** seçin.

5. **Genel bilgiler** sekmesinde bilgileri gözden geçirin. Gerekirse açıklamayı düzenleyebilirsiniz. Ardından **İleri'yi** seçin.

6. **Cihaz grupları** sekmesinde, hangi cihaz gruplarının bu ilkeyi alması gerektiğini belirleyin.  

   - Seçili cihaz grubunu olduğu gibi tutmak için **İleri'yi** seçin.
   - İlkeden bir cihaz grubunu kaldırmak için **Kaldır'ı** seçin.
   - Yeni bir cihaz grubu ayarlamak için **Yeni grup oluştur'u** seçin ve ardından cihaz grubunuzu ayarlayın. (Bu görevle ilgili yardım almak için bkz[. İş için Microsoft Defender cihaz grupları](mdb-create-edit-device-groups.md).)
   - İlkeyi başka bir cihaz grubuna uygulamak için **Var olan grubu kullan'ı** seçin.

   İlkeyi hangi cihaz gruplarının alacağını belirttikten sonra **İleri'yi** seçin.

7. **Yapılandırma ayarları** sekmesinde ayarları gözden geçirin. Gerekirse, ilkenizin ayarlarını düzenleyebilirsiniz. Bu görevle ilgili yardım almak için aşağıdaki makalelere bakın: 

   - [Yeni nesil yapılandırma ayarlarını anlama](mdb-next-gen-configuration-settings.md)   
   - [Güvenlik duvarı ayarları](mdb-firewall.md)

   Yeni nesil koruma ayarlarınızı belirttikten sonra **İleri'yi** seçin.

8. **İlkenizi gözden geçirin** sekmesinde genel bilgileri, hedeflenen cihazları ve yapılandırma ayarlarını gözden geçirin. 

   - **Düzenle'yi** seçerek gerekli değişiklikleri yapın.
   - Devam etmeye hazır olduğunuzda **İlkeyi güncelleştir'i** seçin.

## <a name="create-a-new-policy"></a>Yeni ilke oluşturma

1. Microsoft 365 Defender portalına ()[https://security.microsoft.com](https://security.microsoft.com) gidin ve oturum açın. 

2. Gezinti bölmesinde **Cihaz yapılandırması'nı** seçin. İlkeler işletim sistemine (**Windows istemcisi** gibi) ve ilke türüne (**Yeni nesil koruma** ve **Güvenlik Duvarı** gibi) göre düzenlenir. 

3. bir işletim sistemi sekmesi (örneğin, **Windows istemcileri**) seçin ve **yeni nesil koruma** ilkeleri listesini gözden geçirin. 

4. **Yeni nesil koruma** veya **Güvenlik Duvarı** altında **+ Ekle'yi** seçin.

5. **Genel bilgiler** sekmesinde aşağıdaki adımları izleyin:

   1. Bir ad ve açıklama belirtin. Bu bilgiler, sizin ve ekibinizin ilkeyi daha sonra tanımlamanıza yardımcı olur.
   2. İlke sırasını gözden geçirin ve gerekirse düzenleyin. (Daha fazla bilgi için bkz. [İlke sırası](mdb-policy-order.md).)
   3. **İleri**'yi seçin. 

7. **Cihaz grupları** sekmesinde yeni bir cihaz grubu oluşturun veya mevcut bir grubu kullanın. İlkeler cihazlara cihaz grupları aracılığıyla atanır. Aklınızda bulundurmak istediğiniz bazı şeyler şunlardır:

   - Başlangıçta, yalnızca şirketinizdeki kişilerin şirket verilerine ve e-postasına erişmek için kullandığı cihazları içeren varsayılan cihaz grubunuz olabilir. Varsayılan cihaz grubunuzu tutabilir ve kullanabilirsiniz.
   - Varsayılan ilkeden farklı olan belirli ayarlara sahip bir ilke uygulamak için yeni bir cihaz grubu oluşturun. 
   - Cihaz grubunuzu ayarlarken işletim sistemi sürümü gibi belirli ölçütleri belirtirsiniz. Ölçütleri karşılayan cihazlar, siz hariç tutmadığınız sürece bu cihaz grubuna dahil edilir. 
   - Tanımladığınız varsayılan ve özel cihaz grupları dahil olmak üzere tüm cihaz grupları Azure Active Directory(Azure AD) içinde depolanır.

   Cihaz grupları hakkında daha fazla bilgi edinmek için bkz. [İş için Defender'da cihaz grupları](mdb-create-edit-device-groups.md).

8. **Yapılandırma ayarları** sekmesinde ilkenizin ayarlarını belirtin ve ardından **İleri'yi** seçin. Tek tek ayarlar hakkında daha fazla bilgi için bkz[. İş için Microsoft Defender yapılandırma ayarları](mdb-next-gen-configuration-settings.md).

9. **İlkenizi gözden geçirin** sekmesinde genel bilgileri, hedeflenen cihazları ve yapılandırma ayarlarını gözden geçirin. 

   - **Düzenle'yi** seçerek gerekli değişiklikleri yapın.
   - Devam etmeye hazır olduğunuzda **İlke oluştur'u** seçin.


## <a name="next-steps"></a>Sonraki adımlar

Aşağıdaki görevlerden birini veya daha fazlasını seçin:

- [Cihazları yönetme](mdb-manage-devices.md)
- [İş için Microsoft Defender'da yeni ilke oluşturma](mdb-create-new-policy.md)
- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md)
- [İş için Microsoft Defender'da tehditlere yanıt verme ve tehditleri azaltma](mdb-respond-mitigate-threats.md)
- [İşlem merkezindeki düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)