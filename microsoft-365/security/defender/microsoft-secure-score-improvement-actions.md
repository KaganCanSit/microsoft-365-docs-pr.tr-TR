---
title: Microsoft Güvenli Puanı ile güvenlik nedenlerinizi değerlendirin
description: Güvenlik portalında Microsoft Güvenli Puanınızı geliştirmek için nasıl Microsoft 365 Defender açıklar.
keywords: microsoft güvenli puan, güvenli puan, office 365 güvenli puanı, microsoft güvenlik puanı, Microsoft 365 Defender portalı, geliştirme eylemleri
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.technology: m365d
ms.openlocfilehash: 8991c2aca277d2a08e5f8924a5e5cb354df6dc1f
ms.sourcegitcommit: a4729532278de62f80f2160825d446f6ecd36995
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2022
ms.locfileid: "64569448"
---
# <a name="assess-your-security-posture-with-microsoft-secure-score"></a>Microsoft Güvenli Puanı ile güvenlik nedenlerinizi değerlendirin

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Microsoft Güvenli Puanı, kuruluşun güvenlik mezralarının bir ölçümüdür ve yapılan daha fazla geliştirme eylemine işaret eden daha yüksek bir sayıdır. Microsoft 365 Defender https://security.microsoft.com/securescore [portalında bulunabilir](microsoft-365-defender.md).

Gereksinen bilgileri daha hızlı bu gerektirmenizi yardımcı olmak için, Microsoft geliştirme eylemleri gruplar halinde düzenlenmiştir:

- Kimlik (Azure Active Directory hesapları & rolleri)
- Cihaz (Uç Nokta için Microsoft Defender [Için Microsoft Güvenli Puanı olarak bilinir](/windows/security/threat-protection/microsoft-defender-atp/tvm-microsoft-secure-score-devices))
- Uygulamalar (e-posta ve bulut uygulamaları, Office 365 ve bulut Microsoft Defender for Cloud Apps)

>[!NOTE]
>Microsoft Secure Score'ın son sürümüyle, Microsoft Secure Score'ın Kimlik Güvenliği Puanı ve kimlik puanıyla geçici olarak uyumsuz hale gelen geliştirilmiş bir puanlama modeli Graph API. [Ayrıntıları görüntüle](microsoft-secure-score-whats-new.md)

Microsoft Güvenli Puanı genel bakış sayfasında, bu gruplar arasında puanların nasıl bölün olduğunu ve hangi noktaların kullanılabilir olduğunu görebilirsiniz. Ayrıca, karşılaştırma karşılaştırmaları ile toplam puanın, güvenli puanınıza genel eğilimin ve puanınızı geliştirmek için alınacak öncelikleri alınmış geliştirme eylemlerinin hepsini kullanabilirsiniz.

:::image type="content" source="../../media/secure-score/secure-score-home-page.png" alt-text="Web sitesi portalında Güvenli Microsoft 365 Defender sayfası" lightbox="../../media/secure-score/secure-score-home-page.png":::

## <a name="check-your-current-score"></a>Geçerli puanınızı denetleme

Geçerli puanınızı kontrol etmek için Microsoft Güvenli Puanı genel bakış sayfasına gidin ve Güvenli puanınız **kutucuğuna bakın**. Puanınız, toplam olası puanın üzerinde elde edilen puanlarla birlikte yüzde olarak gösterilir.

Buna ek olarak, **puanının yanındaki** Dahil düğmesini seçerseniz, puanınız için farklı görünümler seçebilirsiniz. Bu farklı puan görünümleri, puan kutucuğunun ve puan çözümleme grafiğinin grafikte görüntülenir.

Aşağıda, genel puanınızı görünümünüze ek olarak, genel not resmin tam görünümü elde etmek için şu puanlar yer gelir:

- **Planlı puan**: Planlanan eylemler tamamlandığında, planlanan puanı göster
- **Geçerli lisans puanı**: Geçerli Microsoft lisansınız ile elde edilebilir puanı gösterme
- **Ulaşılabilir puan**: Microsoft lisansları ve geçerli risk kabulü ile elde edilebilir puanı gösterme

Bu görünüm, tüm olası puan görünümlerini dahil ettiysanız görünümün görünümüne benzer:

:::image type="content" source="../../media/secure-score/secure-score-achievable.png" alt-text="Planlanan puan, geçerli lisans puanı ve portalda ulaşılabilir puanlar dahil güvenli Microsoft 365 Defender puanınız" lightbox="../../media/secure-score/secure-score-achievable.png":::

## <a name="take-action-to-improve-your-score"></a>Puanınızı geliştirmek için harekete geç

Geliştirme **eylemleri sekmesi** , olası saldırı yüzeylerine karşı askıya alan güvenlik önerilerini listeler. Ayrıca durumlarını da (ele almak, planlanan, kabul edilen, üçüncü taraf aracılığıyla çözülen, alternatif risk azaltma yoluyla çözülen ve tamamlanan) içerir. Tüm geliştirme eylemlerini arayabilir, filtre yer ve grupabilirsiniz.  

### <a name="ranking"></a>Derecelendirme

Sıralama, ulaşacak puan sayısına, uygulama zorluğuna, kullanıcı etkisine ve karmaşıklığına dayalıdır. En yüksek dereceli geliştirme eylemleri, düşük zorlukla, kullanıcı etkisiyle ve karmaşıklıkla çok fazla sayıda puana sahiptir.

### <a name="view-improvement-action-details"></a>Geliştirme eylem ayrıntılarını görüntüleme

Belirli bir geliştirme eylemlerini seçin, tam sayfa açılır sayfası görüntülenir.  

:::image type="content" source="../../media/secure-score/secure-score-improvement-action-details.png" alt-text="Microsoft 365 Defender portalında geliştirme eyleminin uçarak çıkış" lightbox="../../media/secure-score/secure-score-improvement-action-details.png":::

Eylemi tamamlamak için birkaç seçenek vardır:

- Yapılandırma **ekranına Microsoft 365 Defender** değişikliği yapmak için Aşağıdaki ekranda yönet'i seçin. Bundan sonra, eylemin değer olduğu noktaları uçarak çıkışta görünür hale gelirsiniz. Puanların güncelleştirilsi genellikle yaklaşık 24 saat sürer.

- Geliştirme **eyleminin** doğrudan bağlantısını kopyalamak için Paylaş'ı seçin. Bağlantıyı paylaşmak için e-posta, e-posta adresi veya posta Microsoft Teams da Microsoft Planner.

**İlerlemeyi** veya açıklama eklemek istediğiniz başka herhangi bir şeyi izlemek için Notlar ekleyin. Geliştirme eylemine kendi **etiketlerinizi** eklersiniz, bu etiketlere göre filtre uygulamanız gerekir.

### <a name="choose-an-improvement-action-status"></a>Geliştirme eylemi durumunu seçme

Herhangi bir durumu seçin ve iyileştirme işlemiyle ilgili notları kaydedin.

- **Adres** - Geliştirme eyleminin gerekli olduğunu biliyor ve bunu gelecekte bir noktada ele ayacak şekilde planlamayı planlıyoruz. Bu durum, kısmen algılandı ancak tamamlanmadı olarak algılanan eylemler için de geçerlidir.
- **Planlanan** - Geliştirme işlemini tamamlamak üzere beton planları vardır.
- **Risk kabul edildi** - Güvenlik her zaman kullanılabilirlik ile dengelenmeli, ortamınız için her öneri işe yaramadı. Böyle bir durumda, riski veya kalan riski kabul etmeye seçebilir ve iyileştirme eylemlerini atmayacak şekilde devam etmeye devam edersiniz. Size puan verilmez, ancak iyileştirme eylemleri listesinde eylem artık görünmez. Bu eylemi geçmişte  görüntüde veya geri almak için, ne zaman olursa bunu geri alabilirsiniz.
- **Üçüncü taraf aracılığıyla çözümlenen** **ve** Alternatif risk azaltma yoluyla çözümlenen - Geliştirme eylemi, üçüncü taraf bir uygulama veya yazılım ya da dahili araç tarafından zaten ele alındı. Eylemin değerinde puanlar kazanırsınız, bu yüzden puanınız genel güvenlik gerilenizi daha iyi yansıttır. Üçüncü taraf veya iç araç artık denetimi kapsıyorsa, başka bir durum seçebilirsiniz. Geliştirme eylemi bu durumlardan biri olarak işaretlenirse, Microsoft'un uygulamanın eksiksizliği konusunda hiçbir görünürlüğü olmayacaktır.

#### <a name="threat--vulnerability-management-improvement-actions"></a>Tehdit & güvenlik açığı yönetimi geliştirme eylemleri

"Cihaz" kategorisindeki geliştirme eylemleri için durumları seçesiniz. Bunun yerine, işlem yapmak için gereken güvenlik [Tehdit ve Güvenlik Açığı Yönetimi ilgili güvenlik](/windows/security/threat-protection/microsoft-defender-atp/tvm-security-recommendation) Microsoft 365 Defender yönlendirildiniz. Seçtiğiniz özel durum ve gerekçelendirme, bu portala özeldir. Microsoft Güvenli Puanı portalında sunumz.

#### <a name="completed-improvement-actions"></a>Tamamlanmış geliştirme eylemleri

Geliştirme eyleminin tüm olası noktaları sağlandıktan sonra geliştirme eylemleri "tamamlandı" durumuna sahip olur. Tamamlanan geliştirme eylemleri Microsoft verileri olsa da onaylanır ve durumu değiştiremezsiniz.

### <a name="assess-information-and-review-user-impact"></a>Bilgileri değerlendirin ve kullanıcının etkisini gözden geçirme

Bir bakışta **adlı bölüm size** kategoriyi, bu kategoriyi, bu kategoriyi ve ürünü koruma altında bulunduracak.

**Geliştirme** eyleminin işlemde yer alan kullanıcılar ve etkilenen kullanıcılar, etkilenecek olan kişiler de kullanıcı üzerindeki  etkisidir.

### <a name="implement-the-improvement-action"></a>Geliştirme eylemlerini uygulama

Uygulama **bölümünde** önkoşullar, geliştirme eylemlerini tamamlamak için adım adım sonraki adımlar, geliştirme eyleminin geçerli uygulama durumu ve daha fazla bilgi içeren diğer bağlantılar yer almaktadır.

Önkoşullar, geliştirme işlemi ele alınmadan önce gerekli lisansları veya tamamlanması gereken eylemleri içerir. Geliştirme eylemini tamamlamak için lisansınıza yeterli lisansların olduğundan ve bu lisansların gerekli kullanıcılara uygulandığından emin olun.  

## <a name="we-want-to-hear-from-you"></a>Bize haber almak için

Herhangi bir sorun varsa, Güvenlik, Gizlilik ve Uyumluluk topluluğuna [göndererek & sağlayın](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) . Topluluğu izliyoruz ve yardım sağacağız.

## <a name="related-resources"></a>İlgili kaynaklar

- [Microsoft Güvenli Puanına genel bakış](microsoft-secure-score.md)
- [Microsoft Güvenli Puan geçmişinizi izleme ve hedefleri karşılama](microsoft-secure-score-history-metrics-trends.md)
- [Yapılacak yenilikler](microsoft-secure-score-whats-coming.md)
- [Yeni gelenler](microsoft-secure-score-whats-new.md)
