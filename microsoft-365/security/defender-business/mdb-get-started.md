---
title: Microsoft 365 Defender portalını kullanmaya başlama
description: Portalda yer alan bu portalı kullanmaya Microsoft 365 Defender bakın. Portalda gezinmeyi, geçerli güvenlik durumunu ve önerileri görüntülemeyi öğrenin
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.custom: intro-get-started
ms.openlocfilehash: 15fbed00484497c7d1dd9f8fa217529bddc1cf51
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2022
ms.locfileid: "63016669"
---
# <a name="get-started-using-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalını kullanmaya başlama

> [!IMPORTANT]
> İş için Microsoft Defender şu anda önizlemede ve istekte etmek için buraya kaydolan müşterilere ve IT [İş Ortaklarına aşamalı](https://aka.ms/mdb-preview) olarak aşamalı olarak aşamalı olarak sunulmaktadır. Önümüzdeki haftalarda bir ilk müşteri ve iş ortağı kümesi sunuyoruz ve genel kullanılabilirlik durumuna kadar önizlemeyi genişleteceğiz. Önizlemenin bir dizi ilk [senaryoyla başlat olacağını](mdb-tutorials.md#try-these-preview-scenarios) ve düzenli olarak özellikler ekley olacacaz.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürmeden önce önemli ölçüde değiştirilmiş olabileceği önceden satın alınan ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

İş için Microsoft Defender(önizleme) için oturum açın ve bu portalı () Microsoft 365 Defender.[https://security.microsoft.com](https://security.microsoft.com) Bu makale aşağıdaki bölümleri içerir:

- [Microsoft 365 Defender portalında gezinme](#navigate-the-microsoft-365-defender-portal)
- [Learning ve yanıt eylemleriyle ilgili modüller hakkında bilgi](#complete-a-learning-module-about-incidents-and-response-actions) 
- [Sonraki adımlar](#next-steps)

>
> **Bir dakika mı kaldı?**
> Lütfen İş için <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">Microsoft Defender ile ilgili kısa ankete göz atyın</a>. Ne olduğunu duymaktan çok büyük bir habermiz var!
>

## <a name="navigate-the-microsoft-365-defender-portal"></a>Portalda Microsoft 365 Defender gezinme

Uygulama Microsoft 365 Defender (), İş için Microsoft Defender ([https://security.microsoft.com](https://security.microsoft.com)önizleme) kullanmak ve yönetmek için tek alışveriş merkezinizdir. Başlamanıza yardımcı olacak bir hoş geldiniz başlığı ve callouts, ilgili bilgileri ortaya çıkaran kartlar ve çeşitli özelliklerle özelliklere kolayca erişmeniz için gezinti çubuğu içerir.
 
Web portalınızı yakından tanımak için Microsoft 365 Defender zaman tanıyın.

:::image type="content" source="../../media/defender-business/mdb-portal-home.png" alt-text="Microsoft 365 Defender portalı":::

### <a name="use-the-navigation-bar"></a>Gezinti çubuğunu kullanma

Olaylarınıza erişmek, raporları görüntülemek ve güvenlik ilkelerinizi yönetmek için ekranın sol tarafındaki gezinti çubuğunu kullanın. Aşağıdaki tabloda, gezinti çubuğunuzda göreceğiniz öğeler açık bulunmaktadır.

| Öğe | Açıklama |
|:---|:---|
| **Giriş** | Sizi Ana Sayfa'daki giriş Microsoft 365 Defender. Giriş sayfasında, algılanan tüm etkin tehditleri vurgulayan kartların yanı sıra, kuruluş verilerinizin ve cihazlarının güvenliğini sağlamanıza yardımcı olacak öneriler de yer almaktadır. <br/><br/>Öneriler Defender for Business (önizleme) sürümüne dahil edilen ekipler, güvenlik ekibinin zaman ve emeklerinden tasarruf sağlar. Öneriler, endüstrinin en iyi yöntemlerine dayalıdır. Öneriler hakkında daha fazla bilgi edinmek için bkz[. Güvenlik önerileri - Daha fazla Tehdit ve Güvenlik Açığı Yönetimi](../defender-endpoint/tvm-security-recommendation.md). |
| **Olaylar** | Sizi en son olaylar listesine alır. Uyarılar tetiklendiğinde olay oluşturulur. Bir olay birden çok uyarı içerebilir. Olaylarınızı düzenli olarak gözden geçirmeyi emin olun. <br/><br/>Olaylar hakkında daha fazla bilgi edinmek için bkz [. İş için Microsoft Defender'da (önizleme) olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md).|
| **İşlem merkezi** | Sizi, tamamlanmış veya bekleyen eylemler de dahil olmak üzere yanıt eylemleri listesine alır. <br/>- Yapılan **eylemleri** görmek için Geçmiş sekmesini seçin. Bazı eylemler otomatik olarak yapılır; başkaları el ile alınır veya onaylandıktan sonra tamamlanır. <br/>- Devam etmek **için** onay gerektiren eylemleri görüntülemek için Beklemede sekmesini seçin. <br/><br/>İşlem merkezi hakkında daha fazla bilgi edinmek için bkz. [İşlem Merkezi'nde düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md). |
| **Tehdit analizleri** | Sizi mevcut tehditlerin bir görünümüne alır ve tehdit ortamınıza bir bakışta göz atmanızı sağlar. Tehdit analizleri, Microsoft güvenlik araştırmacısı raporlarını ve bilgilerini de içerir. <br/><br/>Tehdit analizi hakkında daha fazla bilgi edinmek için bkz [. Tehdit analizi aracılığıyla ortaya çıkan tehditleri izleme ve yanıtlama](../defender-endpoint/threat-analytics.md). |
| **Skoru güvenli hale** | Size, kurum güvenlik konumunun bir gösterimini sağlar ve bunu geliştirmeye yönelik öneriler sunar.<br/><br/>Güvenli Puan hakkında daha fazla bilgi edinmek için bkz. [Cihazlar için Microsoft Güvenli Puanı](../defender-endpoint/tvm-microsoft-secure-score-devices.md). |
| **Learning hub** | Aboneliğinize dahil olan öğrenme yolları aracılığıyla güvenlik eğitimine ve diğer kaynaklara erişim sağlar. Ürüne, beceri düzeyine, role ve daha fazlasına göre filtre uygulama. Learning & merkezi, güvenlik ekibinin İş için Defender (önizleme) ve Uç Nokta için [Microsoft Defender](../defender-endpoint/microsoft-defender-endpoint.md) ve Office 365 için [Microsoft Defender](../office-365-security/defender-for-office-365.md) gibi diğer Microsoft tekliflarında güvenlik özellikleri ve Office 365.  |
| **Uç noktalar** >  **Arama** | İş için Microsoft Defender'a (önizleme) ekli bir veya daha fazla cihaz aramanızı sağlar. |
| **Uç noktalar** >  **Cihaz envanteri** | İş için Microsoft Defender'a (önizleme) ekli bir veya daha fazla cihaz aramanızı sağlar. |
| **Uç noktalar** >  **Güvenlik açığı yönetimi** | Size bir pano, öneriler, düzeltme etkinlikleri, yazılım envanteri ve kurum içindeki olası zayıf noktaların listesi sağlar. |
| **Uç noktalar** >  **Öğreticiler** | Tehdit koruması özelliklerinizin nasıl olduğu hakkında daha fazla bilgi edinmenize yardımcı olmak için, adım adım kılavuzlara ve benzetimlere erişim sağlar. <br/><br/>Her **öğreticinin benzetim dosyasını** elde etmek için denemeden önce Yolu oku bağlantısını seçin. Bazı benzetimler, Office şekilde Microsoft Word gibi ek uygulamalar gerektirir. |
| **Uç noktalar** >  **Cihaz yapılandırması** | Güvenlik ilkelerinizi işletim sistemine ve türe göre listeler. <br/><br/>Güvenlik ilkeleriniz hakkında daha fazla bilgi edinmek için bkz [. İş için Microsoft Defender'da (önizleme) ilkeleri görüntüleme veya düzenleme](mdb-view-edit-policies.md). |
| **Raporlar** | Kullanılabilir güvenlik raporlarınızı listeler. Bu raporlar, güvenlik eğilimlerinizi görmenizi, tehdit algılamaları ve uyarılar ile ilgili ayrıntıları görüntülemenizi ve kurumnizin korumasız cihazları hakkında daha fazla bilgi edinmanızı sağlar. |
| **Hizmet Durumu** | Hizmet durumunu görüntülemenizi ve yaklaşan değişiklikleri planlamanızı sağlar. <br/>- **Hizmet durumu'nun** görünümünü, Microsoft 365 aboneliğine dahil olan hizmet durumunu görüntülemek için Hizmet durumu'nun seçin. <br/>- Planlanan **değişiklikler ve neler** beklemeleri hakkında bilgi edinmek için İleti merkezi'ne seçin.  |
| **İzinler & rolleri** | Kuruluş portalında güvenliğinizi yönetecek ve olayları ve raporları görüntüleyenlere, organizasyonda izinler Microsoft 365 Defender sağlar. Ayrıca, kuruluş cihazlarınızı ek olarak ayarlamak ve yönetmek ve tehdit koruması ilkelerinizi atamak için cihaz gruplarını ayarlamanızı ve yönetmenizi sağlar.  |
| **Ayarlar** | Web sitesi portalı ve İş için Microsoft Defender Microsoft 365 Defender (önizleme) ayarlarını düzenlemenizi sağlar. Örneğin, uç noktalar olarak da adlandırılan cihazları ve kuruluş cihazlarını (uç noktalar olarak da adlandırılır) kullanabilirsiniz. Ayrıca, uyarı engelleme kuralları gibi kurallar tanımlayabilir ve belirli dosya veya işlemleri engellemek veya buna izin vermek için göstergeler kurabilirsiniz.  |
| **Diğer kaynaklar** | Giriş gibi diğer portallara Azure Active Directory. Diğer portallara Microsoft 365 Defender gerek kalmadan, portalda yer alan portalın sizin  gereklerinizi karşılaması gerektiğini unutmayın. |

## <a name="complete-a-learning-module-about-incidents-and-response-actions"></a>Olaylar ve yanıt eylemleri hakkında bir öğrenme modülü tamamlama

Olaylara ve yanıt [eylemlerine genel bir bakış için](/learn/modules/m365-detect-respond-security-issues-defender-endpoint/) öğrenme modülüne bakın, Güvenlik sorunlarını algıla ve yanıtla. Olay sırası, uyarılar ve yanıt eylemleri hakkında bilgi alırsiniz. Bu kurs, İş için Defender'da (önizleme) olaylarla çalışmaya başlamanıza yardımcı olur.

> [!NOTE]
> Öğrenme [modülü (Güvenlik](/learn/modules/m365-detect-respond-security-issues-defender-endpoint/) sorunlarını algıla ve yanıtla) aslında Uç Nokta için Microsoft Defender için olsa da, temel kavramlar ve genel akış, İş için Defender'da (önizleme) gördüğünüze benzer.

## <a name="next-steps"></a>Sonraki adımlar

Artık Defender For Business (önizleme) özelliğine genel bir bakışa sahip olduğunuz için, aşağıdaki görevlerden birini veya daha fazlasını deneyin:

- [İş için Microsoft Defender'da öğreticileri ve benzetimleri deneme (önizleme)](mdb-tutorials.md)

- [İş için Microsoft Defender'da cihazları yönetme (önizleme)](mdb-manage-devices.md)

- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme (önizleme)](mdb-view-manage-incidents.md)

- [Microsoft Defender İş'te (önizleme) tehditlere yanıt verme ve tehditlerini azaltmak](mdb-respond-mitigate-threats.md)

- [İşlem merkezinde düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)

- [İş için Microsoft Defender'da ilkeleri görüntüleme veya düzenleme (önizleme)](mdb-view-edit-policies.md)