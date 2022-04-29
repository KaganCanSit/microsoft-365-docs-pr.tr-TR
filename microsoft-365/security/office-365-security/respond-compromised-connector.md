---
title: Microsoft 365'da güvenliği aşılmış bir bağlayıcıya yanıt verme
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
ms.assetid: ''
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Microsoft 365'de güvenliği aşılmış bağlayıcıyı tanımayı ve yanıtlamayı öğrenin.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d3aadcd44fcf2c6ab6665546a6335dd15997e3d2
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130282"
---
# <a name="respond-to-a-compromised-connector"></a>Güvenliği aşılmış bağlayıcıya yanıt verme

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**Uygulandığı öğe**

- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Office 365 için Microsoft Defender plan 1 ve plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Bağlayıcılar, şirket içi ortamınızdaki Microsoft 365 veya Office 365 ile e-posta sunucuları arasında posta akışını etkinleştirmek için kullanılır. Daha fazla bilgi için bkz[. Exchange Online'da bağlayıcıları kullanarak posta akışını yapılandırma](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).

Güvenliği aşılmış bir gelen bağlayıcı, yetkisiz bir kişinin mevcut gelen bağlayıcıya değişiklik uygulaması veya Microsoft 365 bir kiracıda istenmeyen posta veya kimlik avı e-postaları göndermek amacıyla yeni bir gelen bağlayıcı oluşturması olarak tanımlanır.  

## <a name="detect-a-compromised-connector"></a>Güvenliği aşılmış bağlayıcıyı algılama

Güvenliği aşılmış bağlayıcının özelliklerinden bazıları şunlardır:

- Giden posta hacminde ani ani artış. 

- Giden postalardaki P1 ve P2 gönderenleri arasındaki uyuşmazlık. P1 ve P2 gönderenleri hakkında daha fazla bilgi için bkz. [EOP, kimlik avının önlenmesi için Kimden adresini nasıl doğrular](how-office-365-validates-the-from-address.md#an-overview-of-email-message-standards)?

- Sağlanmamış veya kaydedilmemiş bir etki alanından gönderilen giden postalar. 

- Bağlayıcının geçiş postası göndermesi engellendi. 

- Gelen bağlayıcının varlığı, hedeflenen kullanıcı veya yönetici tarafından oluşturulmadı. 

- Ad, etki alanı adı ve IP adresi gibi mevcut bağlayıcı yapılandırmasında yetkisiz değişiklikler. 

- Kısa süre önce güvenliği aşılmış bir yönetici hesabı. Bağlayıcı yapılandırmasını yalnızca yönetici erişiminiz varsa düzenleyebileceğinizi unutmayın. 

## <a name="secure-and-restore-email-function-to-a-suspected-compromised-connector"></a>Güvenliği aşılmış olduğundan şüphelenilen bağlayıcıya e-posta işlevinin güvenliğini sağlama ve geri yükleme

Bağlayıcınıza yeniden erişim kazanmak için aşağıdaki tüm adımları tamamlamanız gerekir. Bu adımlar, bağlayıcınıza eklenmiş olabilecek tüm arka kapı girdilerini kaldırmanıza yardımcı olur.

### <a name="step-1-identify-if-an-inbound-connector-has-been-compromised"></a>1. Adım: Gelen bağlayıcının güvenliğinin aşılıp aşılmadığını belirleme 

#### <a name="review-recent-suspicious-connector-traffic-or-related-messages"></a>Son şüpheli bağlayıcı trafiğini veya ilgili iletileri gözden geçirme

[Office 365 için Microsoft Defender plan 2'niz](defender-for-office-365.md) varsa doğrudan adresine https://security.microsoft.com/threatexplorergidin. 

1. **Bağlayıcı'yı** seçin, **Bağlayıcı Adı** ekleyin, tarih aralığı'nı seçin ve **yenile'ye** tıklayın. 

    :::image type="content" source="../../media/connector-compromise-explorer.png" alt-text="Gelen bağlayıcı gezgini görünümü" lightbox="../../media/connector-compromise-explorer.png":::

2. E-posta trafiğinde anormal ani artış veya düşüş olup olmadığını belirleyin.

    :::image type="content" source="../../media/connector-compromise-abnormal-spike.png" alt-text="Gereksiz klasöre teslim edilen e-posta sayısı" lightbox="../../media/connector-compromise-abnormal-spike.png":::

3. Tanımlamak: 

    - **Gönderen IP'si** kuruluşunuzun şirket içi IP adresiyle eşleşiyorsa. 

    - Kısa süre önce **Gereksiz** klasörüne önemli sayıda e-posta gönderildiyse. Bu, istenmeyen posta göndermek için güvenliği aşılmış bir bağlayıcının kullanıldığının iyi bir göstergesidir. 

    - Kuruluşunuzun genellikle iletişimde kaldığı alıcılar alıcılarsa. 

    :::image type="content" source="../../media/connector-compromise-sender-ip.png" alt-text="Gönderen IP adresi ve kuruluşunuzun şirket içi IP adresi" lightbox="../../media/connector-compromise-sender-ip.png":::

[Plan 1 veya Exchange Online Protection Office 365 için Microsoft Defender](defender-for-office-365.md) varsa adresine gidin.[](exchange-online-protection-overview.md)https://admin-sdf.exchange.microsoft.com/#/messagetrace 

1. **şüpheli bağlayıcı etkinlik** uyarıyı içinde https://security.microsoft.com/alertsaçın.  

2. **Etkinlik listesi'nin** altında bir etkinlik seçin ve uyarıda algılanan şüpheli **bağlayıcı etki alanını** ve **IP adresini** kopyalayın.

    :::image type="content" source="../../media/connector-compromise-outbound-email-details.png" alt-text="Bağlayıcı güvenliği aşılmış giden e-posta ayrıntıları" lightbox="../../media/connector-compromise-outbound-email-details.png":::
    
3. [**İleti izlemesinde**](https://admin-sdf.exchange.microsoft.com/#/messagetrace) **bağlayıcı etki alanını** ve **IP adresini** kullanarak arama yapın. 

    :::image type="content" source="../../media/connector-compromise-new-message-trace.png" alt-text="Yeni ileti izleme açılır öğesi" lightbox="../../media/connector-compromise-new-message-trace.png":::
    
4. **İleti izleme** arama sonuçlarında şunları belirleyin: 

    - Kısa süre önce önemli sayıda e-posta **FilteredAsSpam olarak işaretlendiyse**.  Bu, istenmeyen posta göndermek için güvenliği aşılmış bir bağlayıcının kullanıldığının iyi bir göstergesidir. 

    - Kuruluşunuzun genellikle iletişimde kaldığı alıcılar alıcılarsa. 

    :::image type="content" source="../../media/connector-compromise-message-trace-results.png" alt-text="Yeni ileti izleme arama sonuçları" lightbox="../../media/connector-compromise-message-trace-results.png":::

#### <a name="investigate-and-validate-connector-related-activity"></a>Bağlayıcıyla ilgili etkinliği araştırma ve doğrulama 

Denetim günlüğündeki bir kullanıcının bağlayıcıyla ilgili etkinliğini araştırmak ve doğrulamak için PowerShell'de aşağıdaki komut satırını kullanın. Daha fazla bilgi için bkz. [Denetim günlüğünde arama yapmak için PowerShell betiği kullanma](/compliance/audit-log-search-script). 

```powershell
Search-UnifiedAuditLog -StartDate "<ExDateTime>" -EndDate "<ExDateTime>" -Operations "New-InboundConnector", "Set-InboundConnector", "Remove-InboundConnector
```

### <a name="step-2-review-and-revert-unauthorized-changes-in-a-connector"></a>2. Adım: Bağlayıcıdaki yetkisiz değişiklikleri gözden geçirme ve geri döndürme 

1. oturum açın https://admin.exchange.microsoft.com/. 

2. Yetkisiz bağlayıcı değişikliklerini gözden geçirin ve geri alın. 

### <a name="step-3-unblock-the-connector-to-re-enable-mail-flow"></a>3. Adım: Posta akışını yeniden etkinleştirmek için bağlayıcının engellemesini kaldırın 

1. oturum açın https://security.microsoft.com/restrictedentities. 

2. Bağlayıcının engelini kaldırmak için kısıtlanmış bağlayıcıyı seçin. 

### <a name="step-4-investigate-and-remediate-potentially-compromised-administrative-user-account"></a>4. Adım: Güvenliği aşılmış olabilecek yönetici kullanıcı hesabını araştırma ve düzeltme

Yetkisiz bağlayıcı etkinliği olan bir kullanıcı tanımlanırsa, bu kullanıcıyı olası risklere karşı araştırabilirsiniz. Daha fazla bilgi için bkz [. Güvenliği Aşılmış E-posta Hesabını Yanıtlama](responding-to-a-compromised-email-account.md).

## <a name="more-information"></a>Daha fazla bilgi

- [Engellenen bağlayıcıları kaldırma](remove-blocked-connectors.md)
- [Engellenen kullanıcıları kaldırma](removing-user-from-restricted-users-portal-after-spam.md)
