---
title: Microsoft Purview'da eKeşif (Premium) çözümüne genel bakış
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: 04/08/2022
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- m365-security-compliance
- m365solution-aed
- m365initiative-compliance
- m365solution-overview
search.appverid:
- MOE150
- MET150
description: Microsoft Purview'da eBulma (Premium) çözümü hakkında bilgi edinin. Bu makalede, iç ve dış araştırmalarını yönetmenize yardımcı olacak bir araç olan Microsoft Purview'daki eKeşif (Premium) konusuna genel bir bakış sağlanır. Ayrıca, yasal araştırmalarınızı yönetmek için eKeşif (Premium) kullanmanın iş nedenlerini de çerçeveler.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 5331ada9baf364f62c44c63a5e2e5b2b4d060292
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66639852"
---
# <a name="overview-of-microsoft-purview-ediscovery-premium"></a>Microsoft Purview eKeşif genel bakış (Premium)

Microsoft Purview eKeşif (Premium) çözümü, mevcut Microsoft eKeşif ve analiz özelliklerini temel alır. eBulma (Premium), kuruluşunuzun iç ve dış araştırmalarına yanıt veren içeriği korumak, toplamak, analiz etmek, gözden geçirmek ve dışarı aktarmak için uçtan uca bir iş akışı sağlar. Ayrıca, yasal ekiplerin bir olaya dahil olan koruyucularla iletişim kurmak için yasal tutma bildirimi iş akışının tamamını yönetmesine olanak tanır.

## <a name="ediscovery-premium-capabilities"></a>eBulma (Premium) özellikleri

eKeşif (Premium), kuruluşunuzun bulunduğu yerdeki verileri keşfederek yasal konulara veya iç araştırmalara yanıt vermesine yardımcı olabilir. İlgi çekici kişileri ve veri kaynaklarını tanımlayarak eBulma iş akışlarını sorunsuz bir şekilde yönetebilir, verileri korumak için bekletmeleri sorunsuz bir şekilde uygulayabilir ve ardından yasal tutma iletişim sürecini yönetebilirsiniz. Kaynaktan veri toplayarak, ihtiyacınız olanları hızla bulmak için canlı Microsoft 365 platformunda arama yapabilirsiniz. Derin dizin oluşturma, e-posta iş parçacığı oluşturma ve neredeyse yinelenen algılama gibi akıllı makine öğrenmesi özellikleri, büyük hacimlerdeki verileri ilgili bir veri kümesine azaltmanıza da yardımcı olur.

Aşağıdaki bölümlerde bu eBulma (Premium) özelliklerinin kuruluşunuza nasıl yardımcı olabileceği açıklanmaktadır.

![eBulma (Premium) özellikleri.](../media/advanced-ediscovery-capabilities.png)

### <a name="discover-and-collect-data-in-place"></a>Verileri yerinde bulma ve toplama

Geleneksel olarak, birden çok üçüncü taraf eBulma çözümü kullanan kuruluşlar, yinelenen verileri işlemek ve barındırmak için Büyük hacimli verileri Microsoft 365'in dışına kopyalamayı gerektirir. Bu gereklilik, ilgili verileri bulma süresini ve birden çok çözümü yönetmenin riskini, maliyetini ve karmaşıklığını artırır.

Microsoft 365'teki eBulma (Premium), kaynaktaki verileri keşfetmenize ve Microsoft 365 güvenlik ve uyumluluk sınırınızda kalmanıza olanak tanır.  eBulma (Premium), canlı sistemden yerinde veri toplayarak kaynağa geri dönmenin sürtüşmesini azaltır ve eksik içeriği bulmak zorunda kalmanın gereksiz çalışmasını azaltır. Bu, genellikle geleneksel eBulma çözümlerinde gecikmeler günlüğe kaydedildiğinde ortaya çıkar.

Teams, Yammer, SharePoint Online, OneDrive İş ve Exchange Online'daki veriler için yerel arama ve toplama özellikleri, veri bulmayı daha da geliştirir. Örneğin, eBulma (Premium):

- Teams konuşmalarını yeniden derler (konuşmalardan tek tek iletileri döndürmek yerine).

- E-posta iletisinde ve Teams sohbetlerinde bağlantılar veya modern ekler kullanarak kullanıcılarla paylaşılan bulut tabanlı içeriği toplar.

- Microsoft 365 olmayan yüzlerce dosya türü için yerleşik desteğe sahiptir.

- Microsoft 365'te [veri bağlayıcıları](archiving-third-party-data.md) tarafından içeri aktarılan ve arşivlenen üçüncü taraf kaynaklardan (Bloomberg, Facebook, Slack ve Zoom Toplantıları gibi) veri toplar.

### <a name="manage-ediscovery-workflow-in-one-platform"></a>EBulma iş akışını tek bir platformda yönetme

eBulma (Premium), güvenmeniz gereken eBulma çözümlerinin sayısını azaltmanıza yardımcı olabilir. Tümü Microsoft 365'in içinde gerçekleşen kolaylaştırılmış, uçtan uca bir iş akışı sağlar. eBulma (Premium), benzersiz ve paylaşılan veri kaynaklarını ilgili kişiye ( *koruyucu* olarak bilinir) otomatik olarak eşleyerek ve analiz ve gözden geçirme amacıyla toplamadan önce ilgili olabilecek veriler üzerinde raporlama ve analiz sağlayarak ilgili bilgi kaynaklarını tanımlama ve toplama konusunda uyuşmaların azaltılmasına yardımcı olur.

Ayrıca, Microsoft Graph API'leri eBulma iş akışını otomatikleştirmenize ve özel çözümler için eKeşif'i (Premium) genişletmenize yardımcı olabilir.

### <a name="cull-data-intelligently"></a>Cull verileri akıllı bir şekilde

eKeşif (Premium) içindeki akıllı makine öğrenmesi özellikleri, gözden geçirilecek veri miktarını azaltmanıza yardımcı olur. Bu akıllı özellikler, büyük hacimli verileri ilgili bir kümeye azaltmanıza ve kaldırmanıza yardımcı olur. Örneğin, yerleşik bir gözden geçirme kümesi sorgusu, yakın yinelemeleri tanımlayarak yalnızca benzersiz içeriği filtrelemeye yardımcı olur. Bu özellik, gözden geçirilmesi gereken veri miktarını önemli ölçüde azaltabilir.

Ek makine öğrenmesi özellikleri, ilgi modülleri gibi akıllı etiketleri ve teknoloji destekli inceleme araçlarını kullanarak ilgili verileri daha da iyileştirebilir ve tanımlayabilir.

## <a name="ediscovery-premium-alignment-with-the-electronic-discovery-reference-model"></a>Elektronik Bulma Başvuru Modeli ile eBulma (Premium) hizalaması

Microsoft 365'teki yerleşik eBulma (Premium) iş akışı, Elektronik Bulma Başvuru Modeli (EDRM) tarafından özetlenen eBulma işlemiyle uyumlu olur.

![Elektronik Bulma Başvuru Modeli (EDRM).](../media/EDRMv2.png)

(edrm.net'da EDRM modelini temel alan görüntü)

Üst düzeyde, eBulma (Premium) EDRM iş akışını şu şekilde destekler:

- **Kimlik.** Bir soruşturmayla ilgilendiğiniz olası kişileri belirledikten sonra, onları bir eBulma (Premium) olayına koruyucu (araştırmayla ilgili bilgilere sahip olabilecekleri için *veri koruyucuları* olarak da adlandırılır) ekleyebilirsiniz. Kullanıcılar koruyucu olarak eklendikten sonra, koruyucu belgelerini korumak, toplamak ve gözden geçirmek kolaydır.

- **Koruma.** eKeşif (Premium), bir soruşturmayla ilgili verileri korumak ve korumak için, bir olayda koruyucularla ilişkili veri kaynaklarına yasal bir saklama yapmanızı sağlar. Ayrıca, gözetimsiz verileri beklemeye alabilirsiniz. eKeşif (Premium) ayrıca yerleşik bir iletişim iş akışına sahiptir, böylece koruyuculara yasal tutma bildirimleri gönderebilir ve onaylarını izleyebilirsiniz.

- **Koleksiyon.** Araştırmayla ilgili veri kaynaklarını tanımladıktan (ve koruduktan) sonra, eBulma'daki yerleşik arama aracını (Premium) kullanarak olayla ilgili olabilecek gözetim veri kaynakları (ve varsa gözetim dışı veri kaynakları) için canlı veri arayabilir ve toplayabilirsiniz.

- **Işleme.** Servis talebiyle ilgili tüm verileri topladıktan sonra, sonraki adım daha fazla inceleme ve analiz için bu verileri işlemektir. eBulma 'da (Premium) toplama aşamasında tanımladığınız yerinde veriler, servis talebi verilerinin statik bir görünümünü sağlayan bir Azure Depolama konumuna ( *inceleme kümesi* olarak adlandırılır) kopyalanır. 

- **Inceleme.** Veriler bir gözden geçirme kümesine eklendikten sonra, belirli belgeleri görüntüleyebilir ve verileri servis talebiyle en alakalı duruma düşürmek için ek sorgular çalıştırabilirsiniz. Ayrıca, belirli belgelere açıklama ekleyebilir ve bunları etiketleyebilir.

- **Analysis.** eBulma (Premium), araştırmayla ilgili olmadığını belirlediğiniz gözden geçirme kümesinden daha fazla veri kaldırmanıza yardımcı olan tümleşik analiz aracı sağlar. advance eDiscovery, ilgili verilerin hacmini azaltmanın yanı sıra, inceleme sürecini daha kolay ve verimli hale getirmek için içeriği düzenlemenize izin vererek yasal gözden geçirme maliyetlerinden tasarruf etmenizi de sağlar.

- **Üretim** ve **Sunum.** Hazır olduğunuzda, belgeleri yasal inceleme için bir gözden geçirme kümesinden dışarı aktarabilirsiniz. Belgeleri yerel biçimlerinde veya EDRM tarafından belirtilen biçimde dışarı aktararak üçüncü taraf gözden geçirme uygulamalarına aktarabilirsiniz.

## <a name="subscriptions-and-licensing"></a>Abonelikler ve lisanslama

eKeşif (Premium) için lisanslama için uygun kuruluş aboneliği ve kullanıcı başına lisanslama gerekir.

- **Kuruluş aboneliği:** Microsoft Purview uyumluluk portalı eBulma'ya (Premium) erişmek için kuruluşunuzun aşağıdakilerden birine sahip olması gerekir:

  - Microsoft 365 E5 veya Office 365 E5 aboneliği
  
  - E5 Uyumluluk eklentisini içeren Microsoft 365 E3 aboneliği

  - E5 eKeşif ve Denetim eklentisi ile aboneliği Microsoft 365 E3

  - A5 veya Office 365 Eğitim A5 aboneliğini Microsoft 365 Eğitim

   Mevcut bir Microsoft 365 E5 planınız yoksa ve eKeşif 'i (Premium) denemek istiyorsanız[, microsoft 365'i](/office365/admin/try-or-buy-microsoft-365) mevcut aboneliğinize ekleyebilir veya Microsoft 365 E5 [deneme sürümüne kaydolabilirsiniz](https://www.microsoft.com/microsoft-365/enterprise).

- **Kullanıcı başına lisanslama:** Bir kullanıcıyı Advance eDiscovery olayına koruyucu olarak eklemek için, kuruluş aboneliğinize bağlı olarak bu kullanıcıya aşağıdaki lisanslardan birinin atanması gerekir:

  - Microsoft 365: Kullanıcılara aşağıdakilerden biri atanmalıdır:
  
    - Microsoft 365 E5 lisansı, E5 Uyumluluk eklentisi lisansı veya E5 eKeşif ve Denetim eklentisi

    - Microsoft 365 Ön Hat kullanıcılarına bir F5 Uyumluluğu veya F5 Güvenlik & Uyumluluğu eklentisi atanmalıdır

    - Microsoft 365 Eğitim kullanıcılara A5 lisansı atanmalıdır

  - Office 365: Kullanıcılara Office 365 E5 veya Office 365 Eğitim A5 lisansı atanmalıdır.

Lisanslama hakkında bilgi için [Microsoft 365 Karşılaştırma tablosundaki](https://go.microsoft.com/fwlink/?linkid=2139145) "eBulma ve denetim" bölümüne bakın.

Lisans atama hakkında bilgi için bkz. [Kullanıcılara lisans atama](/microsoft-365/admin/manage/assign-licenses-to-users).

> [!NOTE]
> Kullanıcıların eBulma (Premium) olayına koruyucu olarak eklenmesi için yalnızca E5 veya A5 lisansına (veya uygun eklenti lisansına) ihtiyacı vardır. Bt yöneticileri, eBulma yöneticileri, avukatlar, yardımcılar veya vakaları yönetmek ve olay verilerini gözden geçirmek için eKeşif (Premium) kullanan araştırmacıların E5, A5 veya eklenti lisansına ihtiyacı yoktur.

## <a name="get-started-with-ediscovery-premium"></a>eKeşif'i kullanmaya başlama (Premium)

eKeşif 'i (Premium) kullanmaya başlamak için iki hızlı ve kolay adım vardır.

![eBulma (Premium) ile çalışmaya başlayan iş akışı.](../media/get-started-AeD.png)

|Adımlar  |Açıklama  |
|:---------|:---------|
|[eKeşif'i (Premium) ayarlama](get-started-with-advanced-ediscovery.md)| Abonelik ve lisanslama gereksinimlerini doğruladıktan sonra, izinleri atayabilir ve eKeşif (Premium) kullanmaya başlamak için kuruluş genelinde ayarları yapılandırabilirsiniz.|
|[Servis taleplerini oluşturma ve yönetme](create-and-manage-advanced-ediscoveryv2-case.md) | Kuruluşunuzdaki tüm yasal ve diğer araştırma türleri için eBulma (Premium) iş akışını yönetmek için servis talepleri oluşturun.|
|||

## <a name="ediscovery-premium-architecture"></a>eBulma (Premium) mimarisi

Burada, tek coğrafi bir ortamda ve çok coğrafi ortamda uçtan uca iş akışını ve [EDRM](#ediscovery-premium-alignment-with-the-electronic-discovery-reference-model) ile uyumlu uçtan uca veri akışını gösteren bir eBulma (Premium) mimari diyagramı yer alır.

[![Model posteri: Microsoft 365'te eKeşif (Premium) Mimarisi.](../media/solutions-architecture-center/ediscovery-poster-thumb.png)](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[Resim olarak görüntüle](../media/solutions-architecture-center/m365-advanced-ediscovery-architecture.png)

[PDF dosyası olarak indirme](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.pdf)

[Visio dosyası olarak indirme](https://download.microsoft.com/download/d/1/c/d1ce536d-9bcf-4d31-b75b-fcf0dc560665/m365-advanced-ediscovery-architecture.vsdx)

## <a name="training"></a>Eğitim

EKeşif (Premium) ile ilgili temel bilgiler konusunda BT yöneticilerinizi, eBulma yöneticilerinizi ve uyumluluk araştırma ekiplerinizi eğiterek kuruluşunuzun Microsoft 365 eKeşif araçlarını kullanarak daha hızlı bir şekilde çalışmaya başlamasına yardımcı olabilirsiniz. Microsoft 365, kuruluşunuzdaki bu kullanıcıların eBulma'ya başlamalarına yardımcı olmak için aşağıdaki kaynağı sağlar: [Microsoft 365'in eBulma ve denetim özelliklerini açıklama](/learn/modules/describe-ediscovery-capabilities-of-microsoft-365).
