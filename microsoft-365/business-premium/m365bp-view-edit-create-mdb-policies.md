---
title: Cihaz koruma ilkelerini görüntüleme veya düzenleme
description: Microsoft 365 İş Ekstra'da cihaz koruma ilkelerini görüntüleme, düzenleme, oluşturma ve silme
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/14/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 816b425fbbd511b68d2c21f313b497bbd4b77f8a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65087057"
---
# <a name="view-and-edit-your-device-protection-policies"></a>Cihaz koruma ilkelerinizi görüntüleme ve düzenleme

Microsoft 365 İş Ekstra'de, yönetilen cihazlar için güvenlik ayarları cihaz koruma ilkeleri aracılığıyla yapılandırılır. Kurulum ve yapılandırma deneyiminizi basitleştirmeye yardımcı olmak için, kuruluşunuzun cihazlarının eklenir eklenmez korunmasına yardımcı olacak önceden yapılandırılmış ilkelere sahipsiniz. Varsayılan ilkeleri kullanın, mevcut ilkeleri düzenleyin veya kendi ilkelerinizi oluşturun.

**Bu kılavuzda aşağıdakilerin nasıl yapılacağını açıklar**:

- Varsayılan ilkelerinize genel bakış elde edin
- Mevcut ilkelerinizi görüntüleme
- Var olan bir ilkeyi düzenleme
- Yeni ilke oluşturma

## <a name="default-device-protection-policies"></a>Varsayılan cihaz koruma ilkeleri

Microsoft 365 İş Ekstra, kuruluşunuzun cihazlarını korumak için iki ana ilke türü içerir:

- Microsoft Defender Virüsten Koruma ve diğer tehdit koruma özelliklerinin nasıl yapılandırıldığını belirleyen **yeni nesil koruma ilkeleri**

- Kuruluşunuzun cihazlarına hangi ağ trafiğinin akışına izin verileceğini belirleyen **güvenlik duvarı ilkeleri**

Bu ilkeler, Microsoft 365 İş Ekstra aboneliğinize dahil edilen İş için Microsoft Defender bir parçasıdır.

## <a name="view-your-existing-device-protection-policies"></a>Mevcut cihaz koruma ilkelerinizi görüntüleme

1. Microsoft 365 Defender portalına ()[https://security.microsoft.com](https://security.microsoft.com) gidin ve oturum açın. 

2. Gezinti bölmesinde **Cihaz yapılandırması'nı** seçin. İlkeler işletim sistemine (**Windows istemcisi** gibi) ve ilke türüne (**Yeni nesil koruma** ve **Güvenlik Duvarı** gibi) göre düzenlenir. 

    :::image type="content" source="../media/mdb-deviceconfiguration.png" lightbox="../media/mdb-deviceconfiguration.png" alt-text="Cihaz Yapılandırması sayfası.":::

3. bir işletim sistemi sekmesi (örneğin, **Windows istemcileri**) seçin ve ardından **Yeni nesil koruma** ve **Güvenlik Duvarı** kategorilerinin altındaki ilke listesini gözden geçirin. 

4. İlke hakkında daha fazla ayrıntı görüntülemek için adını seçin. İlkeyle korunan cihazlar gibi bu ilke hakkında daha fazla bilgi sağlayan bir yan bölme açılır.

   :::image type="content" source="../media/mdb-deviceconfig-selectedpolicy.png" lightbox="../media/mdb-deviceconfig-selectedpolicy.png" alt-text="Cihaz Yapılandırması sayfasında seçilen ilkenin ekran görüntüsü..":::

## <a name="edit-an-existing-device-protection-policy"></a>Mevcut cihaz koruma ilkesini düzenleme

1. Microsoft 365 Defender portalına ()[https://security.microsoft.com](https://security.microsoft.com) gidin ve oturum açın. 

2. Gezinti bölmesinde **Cihaz yapılandırması'nı** seçin. İlkeler işletim sistemine (**Windows istemcisi** gibi) ve ilke türüne (**Yeni nesil koruma** ve **Güvenlik Duvarı** gibi) göre düzenlenir. 

3. bir işletim sistemi sekmesi (örneğin, **Windows istemcileri**) seçin ve ardından **Yeni nesil koruma** ve **Güvenlik Duvarı** kategorilerinin altındaki ilke listesini gözden geçirin. 

4. İlkeyi düzenlemek için, ilkenin adını ve ardından **Düzenle'yi** seçin.

5. **Genel bilgiler** sekmesinde bilgileri gözden geçirin. Gerekirse açıklamayı düzenleyebilirsiniz. Ardından **İleri'yi** seçin.

6. **Cihaz grupları** sekmesinde, hangi cihaz gruplarının bu ilkeyi alması gerektiğini belirleyin.  

   - Seçili cihaz grubunu olduğu gibi tutmak için **İleri'yi** seçin.
   - İlkeden bir cihaz grubunu kaldırmak için **Kaldır'ı** seçin.
   - Yeni bir cihaz grubu ayarlamak için **Yeni grup oluştur'u** seçin ve ardından cihaz grubunuzu ayarlayın. (Bu görevle ilgili yardım almak için bkz[. Microsoft 365 İş Ekstra cihaz grupları](m365bp-device-groups-mdb.md).)
   - İlkeyi başka bir cihaz grubuna uygulamak için **Var olan grubu kullan'ı** seçin.

   İlkeyi hangi cihaz gruplarının alacağını belirttikten sonra **İleri'yi** seçin.

7. **Yapılandırma ayarları** sekmesinde ayarları gözden geçirin. Gerekirse, ilkenizin ayarlarını düzenleyebilirsiniz. Bu görevle ilgili yardım almak için aşağıdaki makalelere bakın: 

   - [Yeni nesil yapılandırma ayarlarını anlama](../security/defender-business/mdb-next-gen-configuration-settings.md)   
   - [Güvenlik duvarı ayarları](../security/defender-business/mdb-firewall.md)

   Yeni nesil koruma ayarlarınızı belirttikten sonra **İleri'yi** seçin.

8. **İlkenizi gözden geçirin** sekmesinde genel bilgileri, hedeflenen cihazları ve yapılandırma ayarlarını gözden geçirin. 

   - **Düzenle'yi** seçerek gerekli değişiklikleri yapın.
   - Devam etmeye hazır olduğunuzda **İlkeyi güncelleştir'i** seçin.

## <a name="create-a-new-device-protection-policy"></a>Yeni cihaz koruma ilkesi oluşturma

1. Microsoft 365 Defender portalına ()[https://security.microsoft.com](https://security.microsoft.com) gidin ve oturum açın. 

2. Gezinti bölmesinde **Cihaz yapılandırması'nı** seçin. İlkeler işletim sistemine (**Windows istemcisi** gibi) ve ilke türüne (**Yeni nesil koruma** ve **Güvenlik Duvarı** gibi) göre düzenlenir. 

3. bir işletim sistemi sekmesi (örneğin, **Windows istemcileri**) seçin ve **yeni nesil koruma** ilkeleri listesini gözden geçirin. 

4. **Yeni nesil koruma** veya **Güvenlik Duvarı** altında **+ Ekle'yi** seçin.

5. **Genel bilgiler** sekmesinde aşağıdaki adımları izleyin:

   1. Bir ad ve açıklama belirtin. Bu bilgiler, sizin ve ekibinizin ilkeyi daha sonra tanımlamanıza yardımcı olur.
   2. İlke sırasını gözden geçirin ve gerekirse düzenleyin. (Daha fazla bilgi için bkz. [İlke sırası](../security/defender-business/mdb-policy-order.md).)
   3. **İleri**'yi seçin. 

7. **Cihaz grupları** sekmesinde yeni bir cihaz grubu oluşturun veya mevcut bir grubu kullanın. İlkeler cihazlara cihaz grupları aracılığıyla atanır. Aklınızda bulundurmak istediğiniz bazı şeyler şunlardır:

   - Başlangıçta, yalnızca kuruluşunuzdaki kişilerin kuruluş verilerine ve e-postasına erişmek için kullandığı cihazları içeren varsayılan cihaz grubunuz olabilir. Varsayılan cihaz grubunuzu tutabilir ve kullanabilirsiniz.
   - Varsayılan ilkeden farklı olan belirli ayarlara sahip bir ilke uygulamak için yeni bir cihaz grubu oluşturun. 
   - Cihaz grubunuzu ayarlarken işletim sistemi sürümü gibi belirli ölçütleri belirtirsiniz. Ölçütleri karşılayan cihazlar, siz hariç tutmadığınız sürece bu cihaz grubuna dahil edilir. 
   - Tanımladığınız varsayılan ve özel cihaz grupları dahil olmak üzere tüm cihaz grupları Azure Active Directory(Azure AD) içinde depolanır.

   Cihaz grupları hakkında daha fazla bilgi edinmek için bkz. [İş için Microsoft Defender'da cihaz grupları](../security/defender-business/mdb-create-edit-device-groups.md).

8. **Yapılandırma ayarları** sekmesinde ilkenizin ayarlarını belirtin ve ardından **İleri'yi** seçin. Tek tek ayarlar hakkında daha fazla bilgi için bkz. [İş için Microsoft Defender'de yeni nesil yapılandırma ayarlarını anlama](../security/defender-business/mdb-next-gen-configuration-settings.md).

9. **İlkenizi gözden geçirin** sekmesinde genel bilgileri, hedeflenen cihazları ve yapılandırma ayarlarını gözden geçirin. 

   - **Düzenle'yi** seçerek gerekli değişiklikleri yapın.
   - Devam etmeye hazır olduğunuzda **İlke oluştur'u** seçin.

## <a name="next-objective"></a>Sonraki hedef

[Cihaz gruplarını](m365bp-device-groups-mdb.md) ayarlama ve yönetme.

