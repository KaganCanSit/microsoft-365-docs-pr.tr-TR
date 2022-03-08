---
title: İş için Microsoft Defender'da güvenlik duvarı ilkeleri için özel kuralları yönetme
description: Özel kurallar, güvenlik duvarı ilkelerine özel durumlar sağlar. İş için Microsoft Defender'da belirli bağlantıları engellemek veya buna izin vermek için özel kurallar kullanabilirsiniz
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 7df23c9f823f5c3c0435743f7a05cf4421704b32
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329803"
---
# <a name="manage-your-custom-rules-for-firewall-policies-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'da güvenlik duvarı ilkeleri için özel kurallarınızı yönetme

> [!IMPORTANT]
> İş için Microsoft Defender 1 Mart 2022'den itibaren Microsoft 365 İş Ekstra müşterilerine sunulmaktadır. Tek başına bir abonelik olarak İş için Defender önizlemededir ve istekte etmek için buraya kaydolan müşterilere ve IT İş Ortaklarına [aşamalı](https://aka.ms/mdb-preview) olarak tüm müşterilere aşamalı olarak tüm müşterilere aşamalı olarak ve tek başına bir abonelik sunar. Önizleme bir [dizi senaryo içerir ve](mdb-tutorials.md#try-these-preview-scenarios) düzenli olarak özellikler ekleycek.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 


İş için Microsoft Defender, cihazlarınızı istenmeyen ağ trafiğine karşı korumaya yardımcı olan güvenlik duvarı ilkeleri içerir. Güvenlik duvarı ilkeleriniz için özel durumlar tanımlamak üzere özel kurallar kullanabilirsiniz. Başka bir ifadeyle, belirli bağlantıları engellemek veya buna izin vermek için özel kurallar kullanabilirsiniz.

Güvenlik duvarı ilkeleri ve ayarları hakkında daha fazla bilgi edinmek için bkz. [İş için Microsoft Defender'da Güvenlik Duvarı](mdb-firewall.md).

**Bu makalede şunların nasıl olduğu açıklanmıştır**:

- [Güvenlik duvarı ilkesi için özel kural oluşturma](#create-a-custom-rule-for-a-firewall-policy)
- [Güvenlik duvarı ilkesi için özel bir kural düzenleme](#edit-a-custom-rule-for-a-firewall-policy)
- [Özel kuralı silme](#delete-a-custom-rule)

>
> **Bir dakika mı kaldı?**
> Lütfen İş için <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">Microsoft Defender ile ilgili kısa ankete göz atyın</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

## <a name="create-a-custom-rule-for-a-firewall-policy"></a>Güvenlik duvarı ilkesi için özel kural oluşturma

1. Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com)) gidin ve oturum açın.

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

1. Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com)) gidin ve oturum açın.

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

1. Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com)) gidin ve oturum açın.

2. **EndpointsDevice** >  **yapılandırmasına gidin** ve ilke listesini gözden geçirin.

3. Güvenlik Duvarı **bölümünde** var olan bir ilkeyi seçin veya yeni bir ilke ekleyin.

4. Özel **kurallar'ın** altında kural listesini gözden geçirebilirsiniz.

5. Bir kural seçin ve sonra da Sil'i **seçin**. Açılır.

6. Onay ekranında Sil'i **seçin**. 

## <a name="next-steps"></a>Sonraki adımlar

- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md)

- [İş için Microsoft Defender'da tehditleri yanıtlama ve azaltmak](mdb-respond-mitigate-threats.md)

- [İşlem merkezinde düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)