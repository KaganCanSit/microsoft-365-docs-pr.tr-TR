---
title: Kimlik için Microsoft Defender güvenlik uyarılarını Microsoft 365 Defender
description: Aynı e-postada güvenlik uyarılarını yönetmeyi ve Kimlik için Microsoft Defender gözden Microsoft 365 Defender
ms.date: 05/20/2021
ms.topic: how-to
author: dcurwin
ms.author: dacurwin
ms.service: microsoft-defender-for-identity
ms.custom: admindeeplinkDEFENDER
manager: raynew
ms.collection: M365-security-compliance
ms.openlocfilehash: 3023dc05550aeee5a9d47bb7561eb221c6d1c588
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64465827"
---
# <a name="defender-for-identity-security-alerts-in-microsoft-365-defender"></a>Microsoft 365 Defender'ta Kimlik güvenlik uyarıları için Defender

**Aşağıdakiler için geçerlidir:**

- Microsoft 365 Defender
- Kimlik için Microsoft Defender

Bu makalede, güvenlik uyarılarında güvenlik uyarılarının [Kimlik için Microsoft Defender](/defender-for-identity) temelleri [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

Kimlik uyarıları için Defender, özel bir Kimlik <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">uyarısı Microsoft 365 Defender</a> biçimiyle yerel olarak tümleşiktir. Bu, kullanıcı deneyimine tam kullanıcı deneyimini [tanıtma yolculuğun Kimlik için Microsoft Defender adımlarını Microsoft 365 Defender](/defender-for-identity/defender-for-identity-in-microsoft-365-defender).

Yeni Kimlik uyarı sayfası, müşterilere Kimlik için Microsoft Defender etki alanı arası sinyal zenginleştirmeyi ve yeni otomatik kimlik yanıtı özelliklerini daha iyi bir şekilde sunar. Güvende kalmanızı sağlar ve güvenlik işlemlerinizin verimliliğini artırmaya yardımcı olur.

Microsoft 365 Defender aracılığıyla uyarıları incelemenin faydalarından biri, [Kimlik için Microsoft Defender](/microsoft-365/security/defender/microsoft-365-defender) uyarılarının pakette yer alan diğer ürünlerin her biri ile alınan bilgilerle daha fazla ilişkili olduğudır. Bu iyileştirilmiş uyarılar, en son Microsoft 365 Defender kaynaklarından kaynaklanan diğer uyarı [biçimleriyle Office 365 için Microsoft Defender](/microsoft-365/security/office-365-security) [Uç Nokta için Microsoft Defender](/microsoft-365/security/defender-endpoint). Yeni sayfa, kimlikle ilişkili uyarıları araştırmak için başka bir ürün portalına gezinme ihtiyacı ortadan kalkmış olur.

Identity için Defender'dan başlatılan uyarılar, artık Microsoft 365 Defender düzeltme ve şüpheli etkinliklere katkıda bulun sağlayacak araç ve işlemlerin azaltılması da dahil olmak üzere Microsoft 365 Defender otomatik soruşturma ve yanıt [(AIR)](/microsoft-365/security/defender/m365d-autoir) özelliklerini tetikley kullanılabilmektedir.

> [!IMPORTANT]
> Kimlik Doğrulama ve Doğrulama Microsoft 365 Defender bir parçası olarak, kimlik için Defender portalında yer alan konumlarından bazı seçenekler ve ayrıntılar değiştirilmiştir. Hem tanıdık hem de yeni özellikleri nerede bulamıyorum? bulmak için lütfen aşağıdaki ayrıntıları okuyun.

## <a name="review-security-alerts"></a>Güvenlik uyarılarını gözden geçirme

Uyarılar sayfası, Olaylar sayfası, tek tek Cihazlar sayfaları ve Gelişmiş  av sayfası gibi birden çok  konumdan **uyarılara erişilebilir**. Bu örnekte, Uyarılar sayfasını **gözden geçirledik**.

Daha <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>' gidin **, Uyarı & Olaylar'a** **gidin**.

:::image type="content" source="../../media/defender-identity/incidents-alerts.png" alt-text="Uyarılar menü öğesi" lightbox="../../media/defender-identity/incidents-alerts.png":::

Kimlik için Defender'dan gelen uyarıları görmek için sağ üst sağdan Filtre'yi ve sonra Hizmet kaynakları'nın altında Kimlik için Microsoft Defender Uygula'ya **seçin**:

:::image type="content" source="../../media/defender-identity/filter-defender-for-identity.png" alt-text="Identity olayları için Defender filtresi" lightbox="../../media/defender-identity/filter-defender-for-identity.png":::

Uyarılar, şu sütunlarda bilgilerle birlikte **görüntülenir: Uyarı** **adı, Etiketler****, Önem** **Derecesi,** Araştırma durumu, **Durum**, **Kategori**, **Algılama kaynağı****,** Etkileniyor **varlıklar, İlk** etkinlik ve **Son etkinlik**.

:::image type="content" source="../../media/defender-identity/filtered-alerts.png" alt-text="Kimlik olayları için Defender" lightbox="../../media/defender-identity/filtered-alerts.png":::

## <a name="manage-alerts"></a>Uyarıları yönetme

Uyarılardan **biri için** Uyarı adına tıklarsanız, uyarıyla ilgili ayrıntıların yer olduğu sayfaya gidersiniz. Sol bölmede, Ne oldu? **özetini görebilirsiniz**:

:::image type="content" source="../../media/defender-identity/what-happened.png" alt-text="Ne oldu bölmesi" lightbox="../../media/defender-identity/what-happened.png":::

Neler oldu **kutusunun üstünde** , uyarının **Hesaplar,** Hedef Ana **Bilgisayar ve** **Kaynak Ana Bilgisayarı düğmeleri** bulunur. Diğer uyarılarda, diğer ana bilgisayarlarla, hesaplarla, IP adresleriyle, etki alanlarıyla ve güvenlik gruplarıyla ilgili ayrıntılara sahip düğmelere bakabilirsiniz. Katılan varlıklar hakkında daha fazla ayrıntı almak için bu seçeneklerden herhangi birini seçin.

Sağ bölmede Uyarı ayrıntılarını **görebilirsiniz**. Burada daha fazla ayrıntı görebilir ve çeşitli görevleri gerçekleştirebilirsiniz:

- **Bu uyarıyı sınıflandırın** - Burada, bu uyarıyı Doğru uyarı veya **Yanlış uyarı** **olarak**

    :::image type="content" source="../../media/defender-identity/classify-alert.png" alt-text="Uyarıyı sınıflandırabilirsiniz" lightbox="../../media/defender-identity/classify-alert.png":::

- **Uyarı durumu** - Sınıflandırma **Kümesi'nde** uyarıyı Doğru veya Yanlış **olarak** **sınıflandırın**. **Atanan'da** uyarıyı kendinize ataabilir veya atamayı geri atabilirsiniz.

    :::image type="content" source="../../media/defender-identity/alert-state.png" alt-text="Uyarı durumu bölmesi" lightbox="../../media/defender-identity/alert-state.png":::

- **Uyarı** ayrıntıları - Uyarı ayrıntıları'nın **altında, belirli** uyarı hakkında daha fazla bilgi bulabilir, uyarı türüyle ilgili belgelere ulaşacak bir bağlantıyı takip eder, uyarının hangi olayla ilişkilendiril olduğunu görebilir, bu uyarı türüyle bağlantılı tüm otomatik soruşturmaları gözden geçirebilirsiniz ve etkilenen cihazları ve kullanıcıları görebilirsiniz.

   :::image type="content" source="../../media/defender-identity/alert-details.png" alt-text="Uyarı ayrıntıları sayfası" lightbox="../../media/defender-identity/alert-details.png":::

- **Açıklamalar & -** Burada uyarıya yorumlarınızı ekleyebilir ve uyarıyla ilişkili tüm eylemlerin geçmişini bakabilirsiniz.

    :::image type="content" source="../../media/defender-identity/comments-history.png" alt-text="Açıklamalar & sayfası" lightbox="../../media/defender-identity/comments-history.png":::

- **Uyarıyı** yönetme - **Uyarıyı yönet'i** seçerek şunları düzenlemenizi sağlayan bir bölmeye gidersiniz:
  - **Durum** - Yeni, **Çözümlendi** **veya** **Sürüyor'ı seçebilirsiniz**.
  - **Sınıflandırma** - Doğru uyarı **veya Yanlış uyarı'ya** **seçebilirsiniz**.
  - **Açıklama** - Uyarıyla ilgili bir açıklama ekleyin.

    Manage alert öğesinin yanındaki üç noktayı seçerek bir tehdit uzmanına danışabilirsiniz **,** uyarıyı bir  Excel dosyasına aktarın veya Başka bir **olayla bağlantı açın**.

    :::image type="content" source="../../media/defender-identity/manage-alert.png" alt-text="Uyarıyı yönet seçeneği" lightbox="../../media/defender-identity/manage-alert.png":::

    > [!NOTE]
    > Excel artık iki bağlantınız vardır: Dosyada görüntüle ve **Kimlik için Microsoft Defender'de görüntüle Microsoft 365 Defender**.  Her bağlantı sizi ilgili portala getirir ve uyarı hakkında orada bilgi sağlar.

## <a name="see-also"></a>Ayrıca bkz.

- [E-postada uyarıları Microsoft 365 Defender](../defender/investigate-alerts.md)
