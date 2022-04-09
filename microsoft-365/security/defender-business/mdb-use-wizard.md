---
title: İş için Microsoft Defender'de kurulum sihirbazını kullanma
description: İş için Defender sihirbaz benzeri bir kurulum ve yapılandırma işlemi içerir. Zaman ve çabadan tasarruf etmek için sihirbazı kullanın.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 04/08/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.custom: intro-get-started
ms.openlocfilehash: ad070273567d350973037f1ac5a0192036d22187
ms.sourcegitcommit: dd5fc139affb4cba4089cbdb2c478968b680699a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2022
ms.locfileid: "64746655"
---
# <a name="use-the-setup-wizard-in-microsoft-defender-for-business"></a>İş için Microsoft Defender'da kurulum sihirbazını kullanma

> [!IMPORTANT]
> İş için Microsoft Defender, 1 Mart 2022'de başlayarak [Microsoft 365 İş Ekstra](../../business-premium/index.md) müşterilerine dağıtılıyor. Tek başına abonelik olarak İş için Defender önizleme aşamasındadır ve istekte bulunmak için [buraya kaydolan](https://aka.ms/mdb-preview) müşterilere ve BT İş Ortaklarına aşamalı olarak dağıtılacaktır. Önizleme, [bir dizi ilk senaryo](mdb-tutorials.md#try-these-preview-scenarios) içerir ve düzenli olarak özellikler ekleyeceğiz.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilebilen önceden yayımlanmış ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

İş için Microsoft Defender, küçük ve orta ölçekli işletmelere ilk kurulum ve yapılandırma için sihirbaz benzeri bir deneyimle zaman ve çaba tasarrufu sağlamak üzere tasarlanmıştır. Kurulum sihirbazı, güvenlik ekibinize erişim izni verme, güvenlik ekibiniz için e-posta bildirimleri ayarlama ve şirketinizin Windows cihazlarını ekleme konusunda size yol gösterir.

:::image type="content" source="media/mdb-wizard-start.png" alt-text="İş için Defender'ı ayarlamak için sihirbaz giriş ekranının ekran görüntüsü.":::

>
> **Bir dakikan var mı?**
> Lütfen <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">İş için Microsoft Defender hakkındaki kısa anketimize</a> katılın. Sizden haber almak isteriz!
>

## <a name="overview-of-the-setup-wizard"></a>Kurulum sihirbazına genel bakış

> [!IMPORTANT]
> Başlamadan önce, Microsoft 365 aboneliğinize zaten kullanıcı eklediğinizden emin olun. Bu görevle ilgili yardım almak için bkz. [Kullanıcı ekleme ve lisansları aynı anda atama](../../admin/add-users/add-users.md).

Sihirbaz, İş için Defender'ı hızlı ve verimli bir şekilde ayarlamanıza ve yapılandırmanıza yardımcı olacak şekilde tasarlanmıştır. Sihirbaz aşağıdaki adımlarda size yol göstermelidir:

1. **Kullanıcı izinleri atayın**. Bu adımda, güvenlik ekibinize Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com) ) erişim izni verirsiniz. Bu portal, sizin ve güvenlik ekibinizin güvenlik özelliklerinizi yöneteceğiniz, uyarıları görüntüleyebileceğiniz ve algılanan tehditler üzerinde gerekli eylemleri gerçekleştireceğiniz yerdir. Portal erişimi, belirli izinleri ima eden roller aracılığıyla verilir.

   İş için Defender'da güvenlik ekibinizin üyelerine üç rolden biri atanabilir:<br/>
   
      - **Genel Yönetici**: Genel yönetici, Microsoft 365 kiracınızdaki tüm ayarları görüntüleyebilir ve düzenleyebilir. Şirketinizin Microsoft 365 aboneliği için ilk kurulum ve yapılandırmayı genel yönetici yapar. 
      - **Güvenlik Yöneticisi: Güvenlik** yöneticisi güvenlik ayarlarını görüntüleyebilir ve düzenleyebilir ve tehditler algılandığında eylem gerçekleştirebilir.
      - **Güvenlik Okuyucusu: Güvenlik** okuyucusu raporlardaki bilgileri görüntüleyebilir ancak güvenlik ayarlarını değiştiremez. 
      
      [Roller ve izinler hakkında daha fazla bilgi edinin](mdb-roles-permissions.md). 

2. **E-posta bildirimlerini ayarlayın**. Bu adımda, güvenlik ekibiniz için e-posta bildirimleri ayarlayabilirsiniz. Ardından, bir uyarı oluşturulduğunda veya yeni bir güvenlik açığı bulunduğunda, güvenlik ekibiniz masalarından uzakta olsalar bile bu konuda bilgi vermez. 

   [E-posta bildirimleri hakkında daha fazla bilgi edinin](mdb-email-notifications.md). 

3. **Windows cihazları ekleme ve yapılandırma**. Bu adımda, şirketinizin Windows cihazlarını İş için Defender'a hızla ekleyebilirsiniz. Cihazları hemen eklemek, bu cihazların ilk günden korunmasına yardımcı olur. 

   - **Zaten Microsoft Endpoint Manager kullanıyorsanız** (Microsoft Intune dahil) ve şirketinizde Endpoint Manager kayıtlı cihazlar varsa, kayıtlı Windows cihazlarınızın bir kısmı veya tamamı için [otomatik ekleme](mdb-onboard-devices.md#automatic-onboarding-for-windows-devices-enrolled-in-microsoft-endpoint-manager) kullanmak isteyip istemediğiniz sorulur. Otomatik ekleme, Endpoint Manager ile İş için Defender arasında bir bağlantı kurar ve ardından cihazları İş için Defender'a sorunsuz bir şekilde ekler Windows. 
   - **Henüz Endpoint Manager kullanmıyorsanız**, [yerel bir betik kullanarak cihazları İş için Defender'a ekleyebilirsiniz](mdb-onboard-devices.md#local-script-in-defender-for-business). 
   
   Bkz. [cihazları İş için Microsoft Defender ekleme hakkında daha fazla bilgi edinin](mdb-onboard-devices.md).
   
4. **Güvenlik ilkelerinizi yapılandırın**. İş için Defender, şirketinizin cihazlarına uygulanabilecek yeni nesil koruma ve güvenlik duvarı koruması için varsayılan güvenlik ilkelerini içerir. Bu varsayılan ilkeler önerilen ayarları kullanır ve cihazlarınız için güçlü koruma sağlamak üzere tasarlanmıştır. Kendi güvenlik ilkelerinizi de oluşturabilirsiniz. Ayrıca, zaten Endpoint Manager kullanıyorsanız, güvenlik ilkelerinizi yönetmek için bunu kullanmaya devam edebilirsiniz.

   Daha fazla bilgi için bkz. [Güvenlik ilkelerinizi ve ayarlarınızı görüntüleme ve düzenleme](mdb-configure-security-settings.md). |

## <a name="what-happens-if-i-dont-use-the-wizard"></a>Sihirbazı kullanmazsam ne olur?

Kurulum sihirbazını kullanmak isteğe bağlıdır. Sihirbazı kullanmamayı seçerseniz veya kurulum işleminiz tamamlanmadan önce sihirbaz kapatılırsa, kurulum ve yapılandırma işlemini kendiniz tamamlayabilirsiniz. Aşağıdaki adımları izleyip [İş için Microsoft Defender ayarlama ve yapılandırma](mdb-setup-configuration.md) bölümüne bakın:

1. Güvenlik ekibinizin Microsoft 365 Defender portalına ([https://security.microsoft.com](https://security.microsoft.com) ) erişebilmesi ve kullanabilmesi için **[roller ve izinler atayın](mdb-roles-permissions.md)**.

2. Yeni uyarılar veya güvenlik açıklarıyla ilgili döngüde olmaları **[için güvenlik ekibiniz için e-posta bildirimleri ayarlayın](mdb-email-notifications.md)**.

3. **[Cihazları,](mdb-onboard-devices.md)** İş için Defender tarafından korunacak şekilde ekleme.

4. Yeni nesil koruma, güvenlik duvarı koruması ve web içeriği filtreleme gibi **[güvenlik ilkelerinizi yönetin](mdb-configure-security-settings.md)**.

## <a name="next-steps"></a>Sonraki adımlar

- [Güvenlik ekibiniz için e-posta bildirimlerini ayarlama](mdb-email-notifications.md)

- [Microsoft 365 Defender portalını kullanarak Kullanmaya başlayın](mdb-get-started.md)

- [Tehdit & Güvenlik Açığı Yönetimi panonuzu kullanma](mdb-view-tvm-dashboard.md)