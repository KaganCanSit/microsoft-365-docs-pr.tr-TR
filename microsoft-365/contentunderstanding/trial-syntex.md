---
title: Microsoft SharePoint Syntex deneme sürümünü çalıştırma
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: lauris; jaeccles
ms.date: ''
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom:
- Adopt
- admindeeplinkMAC
search.appverid: ''
ms.localizationpriority: medium
description: Kuruluşunuzda SharePoint Syntex için bir deneme pilot programı planlamayı, kaydolmayı ve çalıştırmayı öğrenin.
ms.openlocfilehash: 5081c3877e005d1e014ad7520beeffd657a31f67
ms.sourcegitcommit: d9842a9fcaead280bb704e92d44c1f4c201f9eb4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65759812"
---
# <a name="run-a-trial-of-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex deneme sürümünü çalıştırma

Bu makalede, kuruluşunuzda SharePoint Syntex dağıtmak için bir deneme pilot programı ayarlama ve çalıştırma açıklanmaktadır. Ayrıca deneme için en iyi yöntemleri de önerir.

## <a name="sign-up-for-a-trial"></a>Deneme sürümüne kaydolma

SharePoint Syntex deneme sürümü 30 gün boyunca 300 kullanıcıya erişim sağlar.

> [!NOTE]
> 1 milyon AI Builder kredisinin otomatik olarak eklenmesini sağlamak için deneme sürümüne en fazla 300 kullanıcı dahil edilir. Deneme sürümünün başarılı olması için 300 kullanıcı eklemeniz gerekmez.

Deneme sürümünü aşağıdaki kaynaklardan birinden alabilirsiniz:

- [SharePoint Syntex ürün sayfası](https://www.microsoft.com/microsoft-365/enterprise/sharepoint-syntex?activetab=pivot:overviewtab)

- [Microsoft 365 yönetim merkezi](https://admin.microsoft.com)
    1. [Microsoft 365 yönetici merkezi](https://admin.microsoft.com)'nde oturum açın.
    2. **Faturalama** > <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">**Satın Alma Hizmetleri'ne**</a> gidin.
    3. Aşağı kaydırarak **Eklentiler** bölümüne gelin.
    4. SharePoint Syntex kutucuğunda **Ayrıntılar'ı** seçin.
    5. **Ücretsiz denemeyi başlat'ı** seçin.
    6. Deneme sürümünü onaylamak için kalan sihirbaz adımlarını izleyin.

Deneme sürümünü etkinleştirmek için Microsoft 365 genel yöneticisi veya faturalama yöneticisi olmanız gerekir.

### <a name="who-should-be-involved-in-a-trial"></a>Who bir denemede yer almalıdır

|Rol|Etkinlik|
|---|---|
|Genel yöneticiyi veya faturalama yöneticisini Microsoft 365|Deneme sürümünü etkinleştirme ve lisans atama|
|Genel yöneticiyi veya SharePoint yöneticiyi Microsoft 365|SharePoint Syntex yapılandırma ve içerik merkezleri oluşturma|
|İş kullanıcıları|Model oluşturma ve test etme|

### <a name="before-you-activate-a-trial"></a>Deneme sürümünü etkinleştirmeden önce

SharePoint Syntex deneme sürümünü başarıyla planlamak için aşağıdaki faktörleri göz önünde bulundurun:

- En anlamlı test , "gerçek dünya" senaryolarında ve verilerinde tamamlanır.
- SharePoint Syntex deneme sürümünü kiracı başına yalnızca bir kez etkinleştirebilirsiniz.

Bir test veya tanıtım kiracısı, etkinleştirme adımlarını ve yönetim denetimlerini gözden geçirmek için "kuru çalıştırma" olarak kullanılabilir. Ancak büyük olasılıkla bir üretim kiracısı üzerinde model oluşturmayı değerlendirmek en iyisidir.

Üretim kiracısının deneme sürümünün değerini en üst düzeye çıkarmak için planlama ve iş etkileşimi gereklidir. SharePoint Syntex tarafından ele alınabilecek üç veya altı kullanım örneğini belirlemek için bir veya daha fazla iş alanıyla etkileşime geçmeniz gerekir. Bu kullanım örnekleri şunları yapmalıdır:

- Form işleme veya belge anlama modeli tarafından çözülebilecek senaryolar ekleyin.
- Ayıklanan meta verilerin amacını net bir şekilde anlayın; örneğin, Power Automate kullanarak biçimlendirmeyi veya otomasyonu görüntüleyin. SharePoint Syntex belgeleri sınıflandırmaya ve meta verileri ayıklamaya odaklanmış olsa da, bu meta verilerin sağladığı miktar değeridir.
- Tanımlı bir veri kümesini temel alın; örneğin, belirli SharePoint siteleri veya kitaplıkları. SharePoint Syntex yaygın bir yanılgı, genel amaçlı modellerin tüm kuruluş içeriğine uygulanabilmesidir. Daha doğru bir görünüm, modellerin hedeflenen konumlardaki belirli iş sorunlarını çözmeye yardımcı olmak için oluşturulduğudur.

Bu kullanım örneklerinin tümü SharePoint Syntex için uygun olmayabilir. Kaliteli denemenin amacı, SharePoint Syntex tüm senaryolara uygun olacağını kanıtlamak değildir. Bunun yerine, deneme sürümü ürünün değerini daha iyi anlamanıza yardımcı olmalıdır.

Planlanan kullanım örneklerinin her biri için, ilgili içerik veya süreçte konu uzmanı olan kullanıcıları belirleyin. SharePoint Syntex modellerin oluşturulması, BT uzmanlarına veya geliştirici kaynaklarına değil içerikteki etki alanı uzmanlarına odaklanır.

## <a name="activate-a-trial"></a>Deneme sürümünü etkinleştirme

Deneme sürümünü başlattığınızda şunları yapmanız gerekir:

- İlgili kullanıcılara lisans atayın.
- [ek SharePoint Syntex kurulumu gerçekleştirin](set-up-content-understanding.md).
  - Daha [fazla içerik merkezi oluşturmak](create-a-content-center.md) isteyebilirsiniz.

Deneme sürümü etkinleştirildikten sonra modeller oluşturabilir ve dosyaları işleyebilirsiniz. [Model oluşturma yönergelerine](create-a-content-center.md) bakın.

## <a name="during-a-trial"></a>Deneme sırasında

Deneme süreleri sınırlıdır, bu nedenle başlangıçta SharePoint Syntex modellerin belgeleri sınıflandırıp sınıflandıramayacağına ve tanımlı kullanım örnekleri için meta verileri ayıklayıp ayıklayamayacağına odaklanmak en iyisidir. Deneme süresi sona erdikten sonra meta verilerin nasıl kullanılabileceğini değerlendirebilirsiniz.

## <a name="after-a-trial"></a>Denemeden sonra

Denemenin sonucuna bağlı olarak, SharePoint Syntex üretim kullanımına devam edip etmeyeceğinize karar vekleyebilirsiniz.

### <a name="proceed-to-production-use"></a>Üretim kullanımına geçin

Hizmetin sürekliliğini sağlamak için gerekli lisans sayısını satın almanız ve bu [lisansları](syntex-licensing.md) kullanıcılara atamanız gerekir. Deneme süresinin sonunda tam lisansı olmayan deneme kullanıcıları SharePoint Syntex tam olarak kullanamaz.

Beklenen sayıda AI Builder kredisi için öngörülen form işleme ve plan kullanımınızı tahmin etmek zorunda olabilirsiniz. Yardım için bkz. [Size uygun AI Builder kapasitesini tahmin](https://powerapps.microsoft.com/ai-builder-calculator/) etme.

### <a name="dont-proceed-to-production-use"></a>Üretim kullanımına devam etmeyin

Deneme sürümünden sonra lisans satın almıyorsanız:

- Yeni modeller oluşturamazsınız.
- Modelleri çalıştıran kitaplıklar artık dosyaları otomatik olarak sınıflandırmaz veya modelleri ayıklamaz.
- Daha önce sınıflandırılmış dosyalar veya ayıklanan meta veriler etkilenmez.
- İçerik merkezleri ve belge anlama modelleri otomatik olarak silinmez. Gelecekte lisans satın alma kararı alırsanız bunlar kullanılabilir durumda kalır.
- Form işleme modelleri, varsayılan Power Platform ortamının Dataverse (eski adı Common Data Service (CDS)) örneğinde depolanır. Bunlar, SharePoint Syntex için gelecekteki lisanslama ile veya Power Platform'daki AI Builder özellikleriyle kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

[SharePoint Syntex benimsenmesini Kullanmaya başlayın](adoption-getstarted.md)

[SharePoint Syntex için senaryolar ve kullanım örnekleri](adoption-scenarios.md)