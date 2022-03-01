---
title: Uç nokta uyarıları için Microsoft Defender'ı yönetme
description: Manage Alert menüsüyle uyarıların durumunu değiştirebilir, uyarıları gizlemek, açıklama göndermek ve tek tek uyarılar için değişiklik geçmişini gözden geçirmek için gizleme kuralları oluşturabilirsiniz.
keywords: uyarıları yönetme, yönetme, uyarılar, durum, yeni, sürüyor, çözümlendi, uyarıları çözümleme, gizleme, bastırma, sıkıştırma, kurallar, bağlam, geçmiş, açıklamalar, değişiklikler
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
ms.openlocfilehash: 5e0cde3a8a852fab426c1e0bf0290f9785aa0b40
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021674"
---
# <a name="manage-microsoft-defender-for-endpoint-alerts"></a>Uç nokta uyarıları için Microsoft Defender'ı yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-managealerts-abovefoldlink)

Uç Nokta için Defender size uyarılar aracılığıyla olası kötü amaçlı etkinliklerden, özniteliklerden ve bağlamsal bilgilerden haber sağlar. Güvenlik işlemleri panosunda yeni **uyarıların özeti görüntülenir** ve Uyarılar sırasındaki tüm uyarılara **erişebilirsiniz**.

Ayrı bir cihaz için Uyarılar sırasında bir uyarı **seçerek** veya Cihaz sayfasının Uyarılar sekmesini seçerek uyarıları  yönetebilirsiniz.

Bu yerlerden herhangi biri için uyarı seçerek Uyarı yönetimi **bölmesi görüntülenir**.

![Uyarı yönetimi bölmesinin ve uyarılar kuyruğu resmi.](images/atp-alerts-selected.png)

## <a name="link-to-another-incident"></a>Başka bir olayla bağlantı

Uyarıdan veya var olan bir olayın bağlantısından yeni bir olay oluşturabilirsiniz.

## <a name="assign-alerts"></a>Uyarı atama

Uyarı henüz atanmamışsa, uyarıyı kendinize **atamak için Bana** ata'yi seçin.

## <a name="suppress-alerts"></a>Uyarıların bastırılması

Birkaç farklı ekranda uyarıların görünmelerini gizlemeyi Microsoft 365 Defender. Uç Nokta için Defender, kuruluşlarda bilinen araçlar veya işlemler gibi belirsiz olduğu bilinen belirli uyarılar için gizleme kuralları oluşturmanıza olanak sağlar.

Var olan uyarıdan gizleme kuralları oluşturulabilir. Bunlar devre dışı bırakılabilir ve gerekirse yeniden kullanılabilir.

Bir gizleme kuralı oluşturulduğunda, kural oluşturulduğunda o noktadan itibaren etkili olur. Kural, kural oluşturmadan önce kuyrukta önceden var olan uyarıları etkilemez. Kural yalnızca kural oluşturulduktan sonra ayarlanmış koşulları karşılayan uyarılara uygulanır.

Seçimlerini bir gizleme kuralının iki bağlamı vardır:

- **Bu cihazda uyarının bastırılması**
- **Kuruluşumda uyarıyı gizleme**

Kuralın bağlamı, portalda nelerin ortaya çıkar yalnızca gerçek güvenlik uyarılarının portalda ortaya çıkarlır?

Aşağıdaki tabloda yer alan örnekleri, gösterme kuralının bağlamını seçmenize yardımcı olacak şekilde kullanabilirsiniz:

|Bağlam|Tanım|Örnek senaryolar|
|---|---|---|
|**Bu cihazda uyarının bastırılması**|Aynı uyarı başlığına sahip ve yalnızca belirli bir cihazda uyarı uyarıları engelilir. <p> Bu cihaza yapılan diğer tüm uyarılar engellanmaz.|<ul><li>Güvenlik araştırmacısı, kuruluşta diğer cihazlara saldırıda kullanılan kötü amaçlı bir betiği araştırıyor.</li><li>Bir geliştirici, ekipleri için PowerShell betiklerini düzenli olarak oluşturur.</li></ul>|
|**Kuruluşumda uyarıyı gizleme**|Herhangi bir cihazda aynı uyarı başlığına sahip uyarılar engel olur.|<ul><li>A administrative administrative tool is used by everyone in your organization.</li></ul>|

### <a name="suppress-an-alert-and-create-a-new-suppression-rule"></a>Uyarının ılması ve yeni bir gizleme kuralı oluşturma

Uyarıların ne zaman engel gerekme veya çözümlenmezse denetim için özel kurallar oluşturun. Uyarı başlığını, Güvenlik uyarısı göstergesini ve koşulları belirterek, uyarının ne zaman engel olaları olduğunu denetlemenin bir bağlamını kontrol etmek için kullanılabilirsiniz. Bağlamı belirtdikten sonra, uyarıyla ilgili eylemi ve kapsamı yapılandırabileceksiniz.

1. Gizlenmelerini istediğiniz uyarıyı seçin. Bu, Uyarı yönetimi **bölmesini getirir** .

2. Gizleme **kuralı oluştur'a seçin**.

    Bu öznitelikleri kullanarak bir gizleme koşulu oluşturabilirsiniz. Her koşul arasında AND işleci uygulandığı için, yalnızca tüm koşullar karşı uygulandığında gizleme gerçekleşir.

    - Dosya SHA1
    - Dosya adı - desteklenen joker karakter
    - Klasör yolu - desteklenen joker karakter
    - IP adresi
    - URL - desteklenen joker karakter
    - Komut satırı - desteklenen joker karakter

3. Tetikleyici **IOC'yi seçin**.

4. Uyarıda eylemi ve kapsamı belirtin.

   Bir uyarıyı otomatik olarak çözebilirsiniz veya portaldan gizleyebilirsiniz. Otomatik olarak çözümlenen uyarılar, uyarılar kuyruğu, uyarı sayfası ve cihaz zaman çizelgesinin çözümlenen bölümünde görünür ve Uç Nokta API'leri için Defender genelinde çözümlenmiş olarak görünür.

   Gizli olarak işaretlenen uyarılar, hem cihazın ilişkili uyarılarda hem de panodan tüm sistemden gizlenir ve Uç Nokta API'leri için Defender üzerinden akışla yayınlanmaz.

5. Kural adı ve açıklama girin.

6. **Kaydet**'e tıklayın.

#### <a name="view-the-list-of-suppression-rules"></a>Gizleme kuralları listesini görüntüleme

1. Gezinti bölmesinde Uyarı **göstermeyi Ayarlar** \> **seçin**.

2. Gizleme kuralları listesinde, kuruluşta kullanıcıların oluşturduğu tüm kurallar görüntülenir.

Gizleme kurallarını yönetme hakkında daha fazla bilgi için bkz. [Gizleme kurallarını yönetme](manage-suppression-rules.md)

## <a name="change-the-status-of-an-alert"></a>Uyarının durumunu değiştirme

Uyarıları kategorilere ayırarak ( **Yeni**, **Sürüyor** veya **Çözümlendi** olarak) araştırmanız ilerledikçe durumlarını değiştirerek bunları kategorilere ayırarak. Bu, ekiple birlikte uyarıların nasıl yanıt ver hemen düzenlensin ve yönetsin.

Örneğin, bir ekip lideri tüm Yeni uyarıları **gözden geçirmeyi** ve daha fazla çözümleme yapmak için bunları **Sürüyor kuyruğuna** atamaya karar verir.

Alternatif olarak, uyarının önemli olmayan bir cihazdan (örneğin, güvenlik yöneticisine ait bir cihazdan) geldiğini veya daha önceki bir uyarıyla ilgilenil olduğunu biliyorsa, ekip yöneticisi Çözümlendi kuyruğuna uyarıyı atebilir.

## <a name="alert-classification"></a>Uyarı sınıflandırması

Sınıflandırma ayarlamayı ya da uyarının doğru uyarı mı yoksa yanlış uyarı mı olduğunu belirtmeyi seçebilirsiniz. Doğru pozitif/yanlış pozitifin sınıflandırması sağlamak önemlidir. Bu sınıflandırma, uyarı kalitesini izlemek ve uyarıları daha doğru yapmak için kullanılır. "Karar" alanı, "gerçek pozitif" bir sınıflandırma için ek aslına uygunluk tanımlar.

## <a name="add-comments-and-view-the-history-of-an-alert"></a>Açıklama ekleme ve uyarının geçmişini görüntüleme

Uyarıda yapılan önceki değişiklikleri görmek için, uyarıyla ilgili açıklamalar ekleyebilir ve geçmiş olayları görüntüabilirsiniz.

Uyarıda değişiklik veya açıklama yapıldıklarında, açıklamalar ve **geçmiş bölümüne kaydedilir** .

Eklenen açıklamalar anında bölmede görünür.

## <a name="related-topics"></a>İlgili konular

- [Gizleme kurallarını yönetme](manage-suppression-rules.md)
- [Uç Nokta Uyarıları kuyruğu için Microsoft Defender'ı görüntüleme ve düzenleme](alerts-queue.md)
- [Uç nokta uyarıları için Microsoft Defender'ı araştırma](investigate-alerts.md)
- [Uç nokta için Microsoft Defender uyarısıyla ilişkilendirilmiş dosyayı araştırma](investigate-files.md)
- [Uç Nokta Cihazları için Microsoft Defender listesinde cihazları araştırma](investigate-machines.md)
- [Uç nokta için Microsoft Defender uyarısıyla ilişkilendirilmiş IP adresini araştırma](investigate-ip.md)
- [Uç nokta için Microsoft Defender uyarısıyla ilişkilendirilmiş etki alanını araştırma](investigate-domain.md)
- [Uç Nokta için Microsoft Defender'da kullanıcı hesabını araştırma](investigate-user.md)
