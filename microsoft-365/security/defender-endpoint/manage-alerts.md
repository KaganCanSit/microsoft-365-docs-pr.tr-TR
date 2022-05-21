---
title: Uç Nokta için Microsoft Defender uyarılarını yönetme
description: Uyarıları Yönet menüsüyle uyarıların durumunu değiştirin, uyarıları gizlemek, açıklamaları göndermek ve tek tek uyarıların değişiklik geçmişini gözden geçirmek için gizleme kuralları oluşturun.
keywords: uyarıları yönetme, yönetme, uyarılar, durum, yeni, devam ediyor, çözümlendi, uyarıları çözümleme, gizleme, baskı, kurallar, bağlam, geçmiş, açıklamalar, değişiklikler
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c14447301cfa6abf83c231361c020d261eeb87a9
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65623430"
---
# <a name="manage-microsoft-defender-for-endpoint-alerts"></a>Uç Nokta için Microsoft Defender uyarılarını yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Uç nokta için Defender'i deneyimlemek ister misiniz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-managealerts-abovefoldlink)

Uç Nokta için Defender, uyarılar aracılığıyla olası kötü amaçlı olayları, öznitelikleri ve bağlamsal bilgileri size bildirir. **Güvenlik işlemleri panosunda** yeni uyarıların özeti görüntülenir ve **Uyarılar kuyruğundaki** tüm uyarılara erişebilirsiniz.

**Uyarılar kuyruğunda** bir uyarıyı veya tek bir cihaz için Cihaz sayfasının **Uyarılar** sekmesini seçerek uyarıları yönetebilirsiniz.

Bu yerlerden herhangi birinde bir uyarı seçildiğinde **Uyarı yönetimi bölmesi** açılır.

:::image type="content" source="images/atp-alerts-selected.png" alt-text="Uyarı yönetimi bölmesi ve Uyarılar kuyruğu" lightbox="images/atp-alerts-selected.png":::

Yeni Uç Nokta için Microsoft Defender uyarı sayfasını kullanmayı öğrenmek için bu videoyu izleyin.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4yiO5]

## <a name="link-to-another-incident"></a>Başka bir olaya bağlantı

Uyarıdan yeni bir olay oluşturabilir veya mevcut bir olaya bağlanabilirsiniz.

## <a name="assign-alerts"></a>Uyarı atama

Henüz bir uyarı atanmamışsa, **uyarıyı kendinize atamak için Bana ata'yı** seçebilirsiniz.

## <a name="suppress-alerts"></a>Uyarıları gizleme

Uyarıların Microsoft 365 Defender görünmesini engellemeniz gereken senaryolar olabilir. Uç Nokta için Defender, kuruluşunuzdaki bilinen araçlar veya işlemler gibi zararsız olduğu bilinen belirli uyarılar için gizleme kuralları oluşturmanıza olanak tanır.

Gizleme kuralları mevcut bir uyarıdan oluşturulabilir. Gerekirse devre dışı bırakılabilir ve yeniden kullanılabilir.

Bir gizleme kuralı oluşturulduğunda, kuralın oluşturulduğu noktadan itibaren geçerli olur. Kural, kural oluşturulmadan önce kuyrukta bulunan mevcut uyarıları etkilemez. Kural yalnızca kural oluşturulduktan sonra ayarlanan koşulları karşılayan uyarılara uygulanır.

Gizleme kuralı için aralarından seçim yapabileceğiniz iki bağlam vardır:

- **Bu cihazda uyarıyı gizle**
- **Kuruluşumda uyarıyı gizleme**

Kuralın bağlamı, portala nelerin ortaya çıkarıldığını uyarlamanıza ve portalda yalnızca gerçek güvenlik uyarılarının ortaya çıkarıldığından emin olmanıza olanak tanır.

Gizleme kuralının bağlamını seçmenize yardımcı olması için aşağıdaki tabloda yer alan örnekleri kullanabilirsiniz:

|Bağlam|Tanım|Örnek senaryolar|
|---|---|---|
|**Bu cihazda uyarıyı gizle**|Aynı uyarı başlığına sahip ve yalnızca ilgili cihazda bulunan uyarılar gizlenecektir. <p> Bu cihazdaki diğer tüm uyarılar gizlenmeyecek.|<ul><li>Bir güvenlik araştırmacısı, kuruluşunuzdaki diğer cihazlara saldırmak için kullanılan kötü amaçlı bir betiği araştırıyor.</li><li>Bir geliştirici, ekibi için düzenli olarak PowerShell betikleri oluşturur.</li></ul>|
|**Kuruluşumda uyarıyı gizleme**|Herhangi bir cihazda aynı uyarı başlığına sahip uyarılar gizlenecektir.|<ul><li>İyi huylu bir yönetim aracı kuruluşunuzdaki herkes tarafından kullanılır.</li></ul>|

### <a name="suppress-an-alert-and-create-a-new-suppression-rule"></a>Uyarıyı gizleme ve yeni bir gizleme kuralı oluşturma

Uyarıların ne zaman gizleneceğini veya çözümlendiğini denetlemek için özel kurallar oluşturun. Uyarı başlığını, Risk göstergesini ve koşulları belirterek uyarının ne zaman gizleneceğinin bağlamını denetleyebilirsiniz. Bağlamı belirttikten sonra uyarıdaki eylemi ve kapsamı yapılandırabilirsiniz.

1. Bastırmak istediğiniz uyarıyı seçin. Bu, **Uyarı yönetimi** bölmesini getirir.

2. **Gizleme kuralı oluştur'u** seçin.

    Bu öznitelikleri kullanarak bir gizleme koşulu oluşturabilirsiniz. Her koşul arasında bir AND işleci uygulandığı için, gizleme yalnızca tüm koşullar karşılandığında gerçekleşir.

    - DOSYA SHA1
    - Dosya adı - joker karakter desteklenir
    - Klasör yolu - joker karakter desteklenir
    - IP adresi
    - URL - joker karakter desteklenir
    - Komut satırı - joker karakter desteklenir

3. **Tetikleme IOC'sini** seçin.

4. Uyarıdaki eylemi ve kapsamı belirtin.

   Uyarıyı otomatik olarak çözümleyebilir veya portaldan gizleyebilirsiniz. Otomatik olarak çözümlenen uyarılar, uyarı kuyruğunun, uyarı sayfasının ve cihaz zaman çizelgesinin çözümlenen bölümünde görünür ve Uç Nokta için Defender API'lerinde çözümlenmiş olarak görünür.

   Gizli olarak işaretlenen uyarılar, hem cihazın ilişkili uyarılarında hem de panodan sistemin tamamından gizlenir ve Uç Nokta için Defender API'leri arasında akışa alınmaz.

5. Bir kural adı ve açıklama girin.

6. **Kaydet**'e tıklayın.

#### <a name="view-the-list-of-suppression-rules"></a>Gizleme kurallarının listesini görüntüleme

1. Gezinti bölmesinde **Uyarı gizleme** **Ayarlar** \> seçin.

2. Engelleme kuralları listesi, kuruluşunuzdaki kullanıcıların oluşturduğu tüm kuralları gösterir.

Gizleme kurallarını yönetme hakkında daha fazla bilgi için bkz. [Gizleme kurallarını yönetme](manage-suppression-rules.md)

## <a name="change-the-status-of-an-alert"></a>Uyarının durumunu değiştirme

Araştırmanız ilerledikçe durumlarını değiştirerek uyarıları ( **Yeni**, **Devam Ediyor** veya **Çözümlendi** olarak) kategorilere ayırabilirsiniz. Bu, ekibinizin uyarılara nasıl yanıt vereceğini düzenlemenize ve yönetmenize yardımcı olur.

Örneğin, bir ekip lideri tüm **Yeni** uyarıları gözden geçirebilir ve bunları daha fazla analiz için **Devam Ediyor** kuyruğuna atamaya karar verebilir.

Alternatif olarak, ekip lideri uyarının zararsız olduğunu, ilgisiz bir cihazdan (örneğin bir güvenlik yöneticisine ait) geldiğini veya daha önceki bir uyarı aracılığıyla ele alındığını biliyorsa uyarıyı **Çözümlenmiş** kuyruğuna atayabilir.

## <a name="alert-classification"></a>Uyarı sınıflandırması

Sınıflandırma ayarlamamayı seçebilir veya bir uyarının gerçek uyarı mı yoksa yanlış uyarı mı olduğunu belirtebilirsiniz. Gerçek pozitif/yanlış pozitif sınıflandırmasını sağlamak önemlidir. Bu sınıflandırma uyarı kalitesini izlemek ve uyarıları daha doğru hale getirmek için kullanılır. "Belirleme" alanı, "gerçek pozitif" sınıflandırma için ek uygunluk tanımlar.

## <a name="add-comments-and-view-the-history-of-an-alert"></a>Açıklama ekleme ve uyarı geçmişini görüntüleme

Uyarıda yapılan önceki değişiklikleri görmek için açıklamalar ekleyebilir ve bir uyarıyla ilgili geçmiş olayları görüntüleyebilirsiniz.

Bir uyarıda her değişiklik veya açıklama yapıldığında, bu değişiklik **Açıklamalar ve geçmiş** bölümüne kaydedilir.

Eklenen açıklamalar bölmede anında görünür.

## <a name="related-topics"></a>İlgili konular

- [Yinelenen uyarıları engelleme kurallarını yönetin](manage-suppression-rules.md)
- [Uç Nokta için Microsoft Defender Uyarıları kuyruğu görüntüleme ve düzenleme](alerts-queue.md)
- [Uç Nokta için Microsoft Defender uyarılarını araştırma](investigate-alerts.md)
- [Uç Nokta için Microsoft Defender uyarısıyla ilişkili bir dosyayı araştırma](investigate-files.md)
- [Uç Nokta için Microsoft Defender Cihazlar listesindeki cihazları araştırma](investigate-machines.md)
- [Uç Nokta için Microsoft Defender uyarısıyla ilişkili IP adresini araştırma](investigate-ip.md)
- [Uç Nokta için Microsoft Defender uyarısıyla ilişkili bir etki alanını araştırma](investigate-domain.md)
- [Uç Nokta için Microsoft Defender'de kullanıcı hesabını araştırma](investigate-user.md)
