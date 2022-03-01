---
title: İş için Microsoft Defender'da güvenlik duvarı ilkeleri için özel kuralları yönetme
description: Özel kurallar, güvenlik duvarı ilkelerine özel durumlar sağlar. İş için Microsoft Defender'da belirli bağlantıları engellemek veya buna izin vermek için özel kurallar kullanabilirsiniz
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 2200c32d910a5afd20a8ff01c6e24625d72ae21c
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63016709"
---
# <a name="manage-your-custom-rules-for-firewall-policies-in-microsoft-defender-for-business-preview"></a>Microsoft Defender İş'te (önizleme) güvenlik duvarı ilkeleri için özel kurallarınızı yönetme

> [!IMPORTANT]
> İş için Microsoft Defender şu anda önizlemede ve istekte etmek için buraya kaydolan müşterilere ve IT [İş Ortaklarına aşamalı](https://aka.ms/mdb-preview) olarak aşamalı olarak aşamalı olarak sunulmaktadır. Önümüzdeki haftalarda bir ilk müşteri ve iş ortağı kümesi sunuyoruz ve genel kullanılabilirlik durumuna kadar önizlemeyi genişleteceğiz. Önizlemenin bir dizi ilk [senaryoyla başlat olacağını](mdb-tutorials.md#try-these-preview-scenarios) ve düzenli olarak özellikler ekley olacacaz.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 


İş için Microsoft Defender (önizleme), cihazlarınızı istenmeyen ağ trafiğinden korumaya yardımcı olan güvenlik duvarı ilkelerini içerir. Güvenlik duvarı ilkeleriniz için özel durumlar tanımlamak üzere özel kurallar kullanabilirsiniz. Başka bir ifadeyle, belirli bağlantıları engellemek veya buna izin vermek için özel kurallar kullanabilirsiniz.

Güvenlik duvarı ilkeleri ve ayarları hakkında daha fazla bilgi edinmek için bkz. [İş için Microsoft Defender'da (önizleme) Güvenlik Duvarı](mdb-firewall.md).

**Bu makalede şunların nasıl olduğu açıklanmıştır**:

- [Güvenlik duvarı ilkesi için özel kural oluşturma](#create-a-custom-rule-for-a-firewall-policy)
- [Güvenlik duvarı ilkesi için özel bir kural düzenleme](#edit-a-custom-rule-for-a-firewall-policy)
- [Özel kuralı silme](#delete-a-custom-rule)

## <a name="create-a-custom-rule-for-a-firewall-policy"></a>Güvenlik duvarı ilkesi için özel kural oluşturma

1. Erişim portalına Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com) ) ve oturum açın.

2. **EndpointsDevice** >  **yapılandırmasına gidin** ve ilke listesini gözden geçirin.

3. Güvenlik Duvarı **bölümünde** var olan bir ilkeyi seçin veya yeni bir ilke ekleyin.

4. Yapılandırma ayarları **adımını** gözden geçirebilirsiniz. Etki alanı ağı, Genel **ağ ve Özel** ağ **üzerinde gerekli** **değişiklikleri yapın**.

5. Özel bir kural oluşturmak için şu adımları izleyin: 

   1. Özel **kurallar'ın** altında **+ Kural ekle'yi seçin**. (En çok 150 özel kuralın olabilir.)
   2. Yeni **kural oluştur uçta** , kural için bir ad ve açıklama belirtin.
   3. Bir profil seçin. (Seçenekleriniz Etki **alanı ağı**, Genel **ağ veya** Özel **ağ'dır**.)
   4. Uzak **adres türü listesinde** IP'yi veya **Uygulama dosya** **yolunu seçin**.
   5. Değer **kutusunda** , uygun bir değer belirtin. 6. adımda ne seçtiğinize bağlı olarak, bir IP adresi, IP adresi aralığı veya uygulama dosyası yolu belirtebilirsiniz. (Bkz. [Güvenlik duvarı ayarları](mdb-firewall.md).)
   6. Yeni kural **oluştur uçta** , Kural **oluştur'a seçin**. 

6. Yapılandırma ayarları **ekranında Sonraki'yi** **seçin**.

7. **İlkenizi gözden geçirme** ekranında, güvenlik duvarı ilkesi ayarlarında yapılan değişiklikleri gözden geçirin. Gerekli değişiklikleri yapın ve ardından İlke **oluştur'a seçin**.

## <a name="edit-a-custom-rule-for-a-firewall-policy"></a>Güvenlik duvarı ilkesi için özel bir kural düzenleme

1. Erişim portalına Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com) ) ve oturum açın.

2. **EndpointsDevice** >  **yapılandırmasına gidin** ve ilke listesini gözden geçirin.

3. Güvenlik Duvarı **bölümünde** var olan bir ilkeyi seçin veya yeni bir ilke ekleyin.

4. Özel **kurallar'ın** altında kural listesini gözden geçirebilirsiniz.

5. Bir kural seçin ve sonra da Düzenle'yi **seçin**. Açılır.

6. Özel kuralınızı düzenlemek için şu adımları izleyin:

   1. Kuralı **düzenle uç uçta** , kuralın adını ve açıklamasını gözden geçirin ve düzenleyin.
   2. Kuralın profilini gözden geçirin ve gerekirse düzenleyin. (Seçenekleriniz Etki **alanı ağı**, Genel **ağ veya** Özel **ağ'dır**.)
   3. Uzak **adres türü listesinde** IP'yi veya **Uygulama dosya** **yolunu seçin**.
   4. Değer **kutusunda** , uygun bir değer belirtin. 6c. adımda ne seçtiğinize bağlı olarak, bir IP adresi, IP adresi aralığı veya uygulama dosyası yolu belirtebilirsiniz. (Bkz. [Güvenlik duvarı ayarları](mdb-firewall.md).)
   5. Kuralı **etkin hale etmek** **için Kuralı** etkinleştir ayarını Etkin olarak ayarlayın. Kuralı devre dışı bırakmak için de kapalı olarak **ayarlayın**.
   6. Kuralı düzenle **uç güncelleştirmede** Kuralı **güncelleştir'i seçin**. 

7. Yapılandırma ayarları **ekranında Sonraki'yi** **seçin**.

8. **İlkenizi gözden geçirme** ekranında, güvenlik duvarı ilkesi ayarlarında yapılan değişiklikleri gözden geçirin. Gerekli değişiklikleri yapın ve ardından İlke **oluştur'a seçin**.

## <a name="delete-a-custom-rule"></a>Özel kuralı silme

1. Erişim portalına Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com) ) ve oturum açın.

2. **EndpointsDevice** >  **yapılandırmasına gidin** ve ilke listesini gözden geçirin.

3. Güvenlik Duvarı **bölümünde** var olan bir ilkeyi seçin veya yeni bir ilke ekleyin.

4. Özel **kurallar'ın** altında kural listesini gözden geçirebilirsiniz.

5. Bir kural seçin ve sonra da Sil'i **seçin**. Açılır.

6. Onay ekranında Sil'i **seçin**. 

## <a name="next-steps"></a>Sonraki adımlar

- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme (önizleme)](mdb-view-manage-incidents.md)

- [Microsoft Defender İş'te (önizleme) tehditlere yanıt verme ve tehditlerini azaltmak](mdb-respond-mitigate-threats.md)

- [İşlem merkezinde düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)