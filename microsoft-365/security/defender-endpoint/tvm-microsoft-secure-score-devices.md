---
title: Cihazlar için Microsoft Güvenli Puan
description: Cihazlar için puanınız, cihazlarınızı uygulama, işletim sistemi, ağ, hesaplar ve güvenlik denetimleri genelindeki toplu güvenlik yapılandırma durumunu gösterir.
keywords: Cihazlar için Microsoft Güvenli Puanı, Uç Nokta için Microsoft Defender Microsoft Güvenli Puanı, güvenli puan, yapılandırma puanı, Tehdit ve Güvenlik Açığı Yönetimi, güvenlik denetimleri, geliştirme fırsatları, zaman içinde güvenlik yapılandırması puanı, güvenlik sonrası, taban çizgisi
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 1d63e240c0698273807421a4121061630b8f3951
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64499539"
---
# <a name="microsoft-secure-score-for-devices"></a>Cihazlar için Microsoft Güvenli Puan

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**

- [Uç Nokta için Microsoft Defender Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Tehdit ve güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-pullalerts-abovefoldlink)

> [!NOTE]
> Yapılandırma puanı artık Cihazlar için Microsoft Tehdit ve Güvenlik Açığı Yönetimi Puanı olarak ikinci bir sayıdır.

Cihazlar için puanınız [portalda Tehdit ve Güvenlik Açığı Yönetimi panoda](tvm-dashboard-insights.md) Microsoft 365 Defender görünür. Cihazlar için daha yüksek bir Microsoft Güvenli Puanı, uç noktaların siber güvenlik tehdit saldırılarına karşı daha güvenilir olduğu anlamına gelir. Aşağıdaki kategoriler arasında cihazlarınızı kolektif güvenlik yapılandırması durumunu gösterir:

- Uygulama
- İşletim sistemi
- Ağ
- Hesaplar
- Güvenlik denetimleri

Güvenlik önerileri sayfasına gitmek ve [**ilgili önerileri görüntülemek**](tvm-security-recommendation.md) için bir kategori seçin.

## <a name="how-it-works"></a>Nasıl çalışır?

> [!NOTE]
> Cihazlar için Microsoft Güvenli Puan şu anda Cihazlar aracılığıyla ayarlanmış yapılandırmaları grup ilkesi. Geçerli kısmi destek Intune nedeniyle, yapılandırmalar aracılığıyla Intune yapılandırmalar yanlış yapılandırılmış olarak gösterebilirsiniz. Güvenli yapılandırma yönetimi için, kuruluş tarafından Intune için gerçek yapılandırma durumunu doğrulamak için, INTUNE başvurun.

Cihazlar için Microsoft Güvenli Puanı kartında yer alan veriler, çok titiz ve sürekli açık açığı bulma işleminin bir ürünüdür. Sürekli olarak şu yapılandırma keşif değerlendirmeleriyle bir araya toplanır:

- Yanlış yapılandırılmış varlıkları bulmak için toplanan yapılandırmaları toplanan karşılaştırmalarla karşılaştırın
- Düzeltilen veya kısmen düzeltilen güvenlik açıklarına yönelik yapılandırmaları eşleme (risk azaltma)
- En iyi uygulama yapılandırma karşılaştırmalarını (satıcılar, güvenlik akışları, iç araştırma ekipleri) toplama ve koruma
- Tüm varlıklardan güvenlik denetimi yapılandırma durumunun değişikliklerini toplama ve izleme

## <a name="improve-your-security-configuration"></a>Güvenlik yapılandırmanızı geliştirme

Güvenlik önerileri listesinden sorunları düzelterek güvenlik yapılandırmanızı geliştirin. Siz bunu yapar gibi, Cihazlar için Microsoft Güvenli Puanınız da iyileşir ve organizasyonunız siber güvenlik tehditlerine ve güvenlik açıklarına karşı daha güçlü bir hale gelir.

1. Panoda yer alan Cihazlar için Microsoft Güvenli Tehdit ve Güvenlik Açığı Yönetimi kartından kategorilerden birini seçin. Bu kategoriyle ilgili önerilerin listesini görüntüleyin. Sizi Güvenlik önerileri [**sayfasına götürebilirsiniz**](tvm-security-recommendation.md) . Tüm güvenlik önerilerini görmek için Güvenlik önerileri sayfasına gidin ve arama alanını temizleyebilirsiniz.

2. Listeden bir öğe seçin. Açılır panel, öneriyle ilgili ayrıntılarıyla birlikte açılır. Düzeltme **seçenekleri'ne tıklayın**.

   :::image type="content" source="images/security-controls.png" alt-text="Güvenlik denetimleriyle ilgili güvenlik önerileri" lightbox="images/security-controls.png":::

3. Sorunun bağlamını ve bundan sonra ne yapmak olduğunu anlamak için açıklamayı okuyun. Bir son tarih seçin, notlar ekleyin ve Tüm düzeltme etkinliği verilerini **CSV'ye** aktar'ı seçin, böylece izleme için bir e-postaya ekleyebilirsiniz.

4. **İsteği gönder'i seçin**. Düzeltme görevinin oluşturulmuş olduğunu onay iletisi alırsınız.

   :::image type="content" source="images/remediation-task-created.png" alt-text="Düzeltme görevi oluşturma onayı" lightbox="images/remediation-task-created.png":::

5. CSV dosyanızı kaydedin.

   :::image type="content" source="images/tvm_save_csv_file.png" alt-text="CSV dosyasını kaydetme seçeneğini içeren sayfa" lightbox="images/tvm_save_csv_file.png":::

6. IT Yöneticinize bir izleme e-postası gönderin ve düzeltmenin sistemde yayılması için size ne kadar süre verildiye izin ver.

7. Panoda **Cihazlar için Microsoft Güvenli Puanı** kartını yeniden gözden geçirin. Güvenlik denetimleri önerilerinin sayısı azalır. Güvenlik önerileri **sayfasına** dönmek için Güvenlik **denetimleri'ne** geri dönüp Güvenlik denetimleri'ne baksanız bile, ele istediğiniz öğe artık orada listelenmiyor. Cihazlar için Microsoft Güvenli Puanınız artıracaktır.

> [!IMPORTANT]
>Güvenlik açığı değerlendirme oranlarınızı artırmak için aşağıdaki zorunlu güvenlik güncelleştirmelerini indirin ve bunları ağ içinde dağıtın:
>
> - 19H1 müşterileri | [KB 4512941](https://support.microsoft.com/help/4512941/windows-10-update-kb4512941)
> - RS5 müşterileri | [KB 4516077](https://support.microsoft.com/help/4516077/windows-10-update-kb4516077)
> - RS4 müşterileri | [KB 4516045](https://support.microsoft.com/help/4516045/windows-10-update-kb4516045)
> - RS3 müşterileri | [KB 4516071](https://support.microsoft.com/help/4516071/windows-10-update-kb4516071)
>
> Güvenlik güncelleştirmelerini indirmek için:
>
> 1. [Microsoft Update Kataloğu'ne gidin](https://www.catalog.update.microsoft.com/home.aspx).
> 2. İndirmeniz gereken güvenlik güncelleştirmesi KB numarasının anahtarını girin ve Ara'ya **tıklayın**.

## <a name="related-topics"></a>İlgili konular

- [Tehdit ve güvenlik açığı yönetimi genel bakış](next-gen-threat-and-vuln-mgt.md)
- [Pano](tvm-dashboard-insights.md)
- [Pozlama puanı](tvm-exposure-score.md)
- [Güvenlik önerileri](tvm-security-recommendation.md)
