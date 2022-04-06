---
title: Microsoft 365 Defender portalını kullanarak Kullanmaya başlayın
description: Microsoft 365 Defender portalını kullanmaya başlamayı öğrenin. Portalda gezinmeyi ve geçerli güvenlik durumunuzu ve önerilerinizi görüntülemeyi öğrenin
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 03/15/2022
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
ms.openlocfilehash: c5a940676eab6ae3a07c526ecb1bd910ed8751fe
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64667152"
---
# <a name="get-started-using-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalını kullanarak Kullanmaya başlayın

> [!IMPORTANT]
> İş için Microsoft Defender, 1 Mart 2022'de başlayarak [Microsoft 365 İş Ekstra](../../business-premium/index.md) müşterilerine dağıtılıyor. Tek başına abonelik olarak İş için Defender önizleme aşamasındadır ve istekte bulunmak için [buraya kaydolan](https://aka.ms/mdb-preview) müşterilere ve BT İş Ortaklarına aşamalı olarak dağıtılacaktır. Önizleme, [bir dizi ilk senaryo](mdb-tutorials.md#try-these-preview-scenarios) içerir ve düzenli olarak özellikler ekleyeceğiz.
> 
> Bu makaledeki bazı bilgiler, ticari olarak piyasaya sürülmeden önce önemli ölçüde değiştirilebilen önceden yayımlanmış ürünler/hizmetlerle ilgilidir. Microsoft, burada sağlanan bilgiler için açık veya zımni hiçbir garanti vermez. 

İş için Microsoft Defender kaydolduktan sonra Microsoft 365 Defender portalı ([https://security.microsoft.com](https://security.microsoft.com)) ile tanışmak istersiniz. Bu makale aşağıdaki bölümleri içerir:

- [Microsoft 365 Defender portalında gezinme](#navigate-the-microsoft-365-defender-portal)

- [Olaylar ve yanıt eylemleriyle ilgili modülleri Learning](#complete-a-learning-module-about-incidents-and-response-actions) 

- [Sonraki adımlar](#next-steps)

>
> **Bir dakikan var mı?**
> Lütfen <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">İş için Microsoft Defender hakkındaki kısa anketimize</a> katılın. Sizden haber almak isteriz!
>

## <a name="navigate-the-microsoft-365-defender-portal"></a>Microsoft 365 Defender portalında gezinme

Microsoft 365 Defender portalı ([https://security.microsoft.com](https://security.microsoft.com)) İş için Microsoft Defender kullanmak ve yönetmek için tek adresinizdir. Başlamanıza yardımcı olacak bir karşılama başlığı ve açıklama balonları, ilgili bilgileri ortaya çıkartan kartlar ve çeşitli özelliklere ve özelliklere kolayca erişmenizi sağlayan bir gezinti çubuğu içerir.
 
Microsoft 365 Defender portalınızla tanışmak için bir dakikanızı ayırın.

:::image type="content" source="../../media/defender-business/mdb-portal-home.png" alt-text="Microsoft 365 Defender portalı":::

### <a name="use-the-navigation-bar"></a>Gezinti çubuğunu kullanma

Olaylarınıza erişmek, raporları görüntülemek ve güvenlik ilkelerinizi yönetmek için ekranın sol tarafındaki gezinti çubuğunu kullanın. Aşağıdaki tabloda, gezinti çubuğunuzda göreceğiniz öğeler açıklanmaktadır.

| Öğe | Açıklama |
|:---|:---|
| **Giriş** | sizi Microsoft 365 Defender giriş sayfanıza götürür. Giriş sayfasında, algılanan etkin tehditleri vurgulayan kartların yanı sıra şirketinizin verilerinin ve cihazlarının güvenliğini sağlamaya yardımcı olacak öneriler bulunur. <br/><br/>İş için Defender'a dahil Öneriler güvenlik ekibinize zaman ve çaba kazandırabilir. Öneriler endüstrinin en iyi uygulamalarını temel alır. Öneriler hakkında daha fazla bilgi edinmek için bkz[. Güvenlik önerileri - Tehdit ve Güvenlik Açığı Yönetimi](../defender-endpoint/tvm-security-recommendation.md). |
| **Olaylar** | Sizi son olaylar listenize götürür. Uyarılar tetiklendiğinde olaylar oluşturulur. Bir olay birden çok uyarı içerebilir. Olaylarınızı düzenli olarak gözden geçirmeyi unutmayın. <br/><br/>Olaylar hakkında daha fazla bilgi edinmek için bkz. [İş için Microsoft Defender'de olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md).|
| **İşlem merkezi** | Tamamlanan veya bekleyen eylemler de dahil olmak üzere yanıt eylemleri listenize götürür. <br/>- Gerçekleştirilen eylemleri görmek için **Geçmiş** sekmesini seçin. Bazı eylemler otomatik olarak gerçekleştirilen; diğerleri el ile alınır veya onaylandıktan sonra tamamlanmıştır. <br/>- Devam etmek için onay gerektiren eylemleri görüntülemek için **Beklemede** sekmesini seçin. <br/><br/>İşlem merkezi hakkında daha fazla bilgi edinmek için bkz. [İşlem merkezindeki düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md). |
| **Tehdit analizi** | Sizi geçerli tehditlerin bir görünümüne götürür ve tehdit ortamınızın bir bakışta görünümünü sağlar. Tehdit analizi, Microsoft güvenlik araştırmacılarının raporlarını ve bilgilerini de içerir. <br/><br/>Tehdit analizi hakkında daha fazla bilgi edinmek için bkz. Tehdit [analizi aracılığıyla ortaya çıkan tehditleri izleme ve yanıtlama](../defender-endpoint/threat-analytics.md). |
| **Güvenlik puanı** | Şirketinizin güvenlik konumunun bir gösterimini sağlar ve bunu geliştirmek için öneriler sunar.<br/><br/>Güvenli Puan hakkında daha fazla bilgi edinmek için bkz. [Cihazlar için Microsoft Güvenli Puanı](../defender-endpoint/tvm-microsoft-secure-score-devices.md). |
| **Learning hub'ı** | Aboneliğinize dahil edilen öğrenme yolları aracılığıyla güvenlik eğitimine ve diğer kaynaklara erişim sağlar. Ürüne, beceri düzeyine, role ve daha fazlasına göre filtreleyebilirsiniz. Learning merkezi, güvenlik ekibinizin İş için Defender'daki güvenlik özellikleri & özelliklerine ve [Uç Nokta için Microsoft Defender](../defender-endpoint/microsoft-defender-endpoint.md) ve [Office 365 için Microsoft Defender](../office-365-security/defender-for-office-365.md) gibi daha fazla Microsoft teklifine odaklanmalarına yardımcı olabilir.  |
| **Bitiş noktası** >  **Arama** | İş için Microsoft Defender eklenen bir veya daha fazla cihazı aramanızı sağlar. |
| **Bitiş noktası** >  **Cihaz envanteri** | İş için Microsoft Defender eklenen bir veya daha fazla cihazı aramanızı sağlar. |
| **Bitiş noktası** >  **Güvenlik açığı yönetimi** | Size bir pano, öneriler, düzeltme etkinlikleri, yazılım envanteri ve şirketiniz içindeki olası zayıflıkların listesini sağlar. |
| **Bitiş noktası** >  **Öğreticiler** | Tehdit koruması özelliklerinizin nasıl çalıştığı hakkında daha fazla bilgi edinmenize yardımcı olmak için kılavuzlara ve simülasyonlara erişim sağlar. <br/><br/>Her öğretici için simülasyon dosyasını almaya çalışmadan önce **İzlenecek yol bağlantısını okuyun'u** seçin. Bazı simülasyonların izlenecek kılavuzu okuması için Microsoft Word gibi Office uygulamalar gerekir. |
| **Bitiş noktası** >  **Cihaz yapılandırması** | Güvenlik ilkelerinizi işletim sistemine ve türe göre listeler. <br/><br/>Güvenlik ilkeleriniz hakkında daha fazla bilgi edinmek için bkz. [İş için Microsoft Defender'da ilkeleri görüntüleme veya düzenleme](mdb-view-edit-policies.md). |
| **Raporlar** | Kullanılabilir güvenlik raporlarınızı listeler. Bu raporlar güvenlik eğilimlerinizi görmenizi, tehdit algılamaları ve uyarıları hakkındaki ayrıntıları görüntülemenizi ve şirketinizin savunmasız cihazları hakkında daha fazla bilgi edinmenizi sağlar. |
| **Hizmet Durumu** | Hizmet durumu durumunuzu görüntülemenizi ve yaklaşan değişiklikleri planlamanızı sağlar. <br/>- Şirketinizin aboneliğine dahil edilen **Microsoft 365** hizmetlerinin sistem durumunu görüntülemek için Hizmet durumu seçin. <br/>- Planlı değişiklikler ve bekleyebileceğiniz şeyler hakkında bilgi edinmek için **İleti merkezi'ne** tıklayın.  |
| **İzinler & rolleri** | Microsoft 365 Defender portalında güvenliğinizi yönetecek ve olayları ve raporları görüntüleyecek olan şirketinizdeki kişilere izin atamanızı sağlar. Ayrıca, şirketinizin cihazlarını eklemek ve tehdit koruması ilkelerinizi atamak için cihaz gruplarını ayarlamanıza ve yönetmenize olanak tanır.  |
| **Ayarlar** | Microsoft 365 Defender portalı ve İş için Microsoft Defender ayarlarını düzenlemenizi sağlar. Örneğin, şirketinizin cihazlarını (uç nokta olarak da adlandırılır) ekleyebilir (veya çıkarabilirsiniz). Ayrıca uyarı engelleme kuralları gibi kurallar tanımlayabilir ve belirli dosyaları veya işlemleri engelleyecek veya izin verecek göstergeleri ayarlayabilirsiniz.  |
| **Diğer kaynaklar** | Azure Active Directory gibi diğer portallara gidin. Microsoft 365 Defender portalının diğer portallara gitmenize gerek kalmadan gereksinimlerinizi karşılaması gerektiğini unutmayın. |

## <a name="complete-a-learning-module-about-incidents-and-response-actions"></a>Olaylar ve yanıt eylemleri hakkında öğrenme modülünü tamamlama

Olaylara ve yanıt eylemlerine genel bir bakış elde [etmek için Güvenlik sorunlarını algılama ve yanıtlama](/learn/modules/m365-detect-respond-security-issues-defender-endpoint/) öğrenme modülüne bakın. Gerçekleştirebileceğiniz olay kuyruğu, uyarılar ve yanıt eylemleri hakkında bilgi edineceksiniz. Bu kurs, İş için Defender'daki olaylarla çalışmaya başlamanıza yardımcı olur.

> [!NOTE]
> Öğrenme modülü ([Güvenlik sorunlarını algılama ve yanıtlama](/learn/modules/m365-detect-respond-security-issues-defender-endpoint/)) aslında Uç Nokta için Microsoft Defender için olsa da, temel kavramlar ve genel akış, İş için Defender'da gördüklerinize benzer.

## <a name="next-steps"></a>Sonraki adımlar

İş için Defender'a genel bir bakış elde ettiğinize göre, aşağıdaki görevlerden birini veya birkaçını deneyin:

- [İş için Microsoft Defender'de öğreticileri ve simülasyonları deneyin](mdb-tutorials.md)

- [İş için Microsoft Defender'de cihazları yönetme](mdb-manage-devices.md)

- [İş için Microsoft Defender'da olayları görüntüleme ve yönetme](mdb-view-manage-incidents.md)

- [İş için Microsoft Defender'da tehditlere yanıt verme ve tehditleri azaltma](mdb-respond-mitigate-threats.md)

- [İşlem merkezindeki düzeltme eylemlerini gözden geçirme](mdb-review-remediation-actions.md)

- [İş için Microsoft Defender'de ilkeleri görüntüleme veya düzenleme](mdb-view-edit-policies.md)