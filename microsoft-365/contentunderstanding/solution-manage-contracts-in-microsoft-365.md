---
title: Yeni bir çözüm kullanarak Microsoft 365 yönetin
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.date: ''
ms.prod: microsoft-365-enterprise
ms.collection:
- m365solution-managecontracts
- m365solution-overview
search.appverid: ''
ms.localizationpriority: medium
ROBOTS: ''
description: Liste, posta listesi, liste Microsoft 365 çözümlerini SharePoint Syntex kullanarak SharePoint Microsoft Teams yönet Power Automate.
ms.openlocfilehash: 86ccbeef283b165e178b12debd3ae99f982afc04
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985154"
---
# <a name="manage-contracts-using-a-microsoft-365-solution"></a>Yeni bir çözüm kullanarak Microsoft 365 yönetin

Bu makalede, organizasyonlarının sözleşme ve bileşenlerini kullanarak SharePoint Syntex yönetim çözümünün nasıl oluşturul Microsoft 365. Bu hizmet size, benzersiz iş ihtiyaçlarına uygun bir çözüm planlamanıza ve oluşturmanıza yardımcı olacak bir çerçeve sağlar. Bu çözüm sözleşme yönetiminden konuşsa da, bunu uyarlanabilir ve iş veya fatura faturaları gibi başka belge yönetim çözümleri oluşturabilirsiniz.

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWJUR0]

</br>

## <a name="identify-the-business-problem"></a>İş sorununu belirleme

Sözleşme yönetim sistemini planlamanın ilk adımı, çözmeye çalıştığınızı anlamaktır. Bu çözüm için dört önemli sorunu ele alınması gerekir:

- **Sözleşmeleri tanımlama**. Organizasyonunız faturalar, sözleşmeler, iş faturaları gibi birçok belgeyle çalışır.  Bazıları e-postayla gönderilen dijital varlıklar, bazıları ise geleneksel posta yoluyla gönderilen kağıt varlıklardır. Diğer tüm belgelerden tüm müşteri sözleşmelerini tanımlama ve sonra bu şekilde sınıflendirme için bir yol gerekir.

- **Sözleşme onaylarının geçmişini izleyebilirsiniz**. Organizasyonun, sözleşmelerin onaylandıktan veya reddedilmiş olup olmadığını ve ödemenin işlendiğinden emin bir yol elde etmek için güvenilir bir yol gerekir. 

- **Sözleşme onaylarını yönetmek için site**. Kuruluş, tüm gerekli paydaşların sözleşmeleri kolayca gözden geçirebiliyor olduğu bir işbirliği sitesi ayarlamalı. Paydaşlar gerekirse sözleşmenin tamamını gözden geçirebiliyor olmalı, ancak çoğunlukla her sözleşmenin bazı önemli alanlarını (örneğin, müşteri adı, POSTA hizmetleri numarası ve toplam maliyeti) görmekte fayda vardır. Paydaşlar gelen sözleşmeleri kolayca onaylıyor veya reddedebiliyor olmalı.

- **Gözden geçirme sözleşmelerini yönlendir**. Onaylanan ve reddedilen sözleşmelerin belirli bir iş akışı aracılığıyla yönlendirilmesi gerekir. Onaylanan sözleşmelerin ödeme işlemleri için üçüncü taraf bir uygulamaya yönlendirn olması gerekir. Reddedilen sözleşmelerin ek inceleme için yönlendirilmesi gerekir.

## <a name="overview-of-the-solution"></a>Çözüme genel bakış

  ![Liste, liste veya SharePoint Syntex SharePoint kullanarak Teams diyagramı Power Automate.](../media/content-understanding/syntex-solution-manage-contracts-setup-steps.png)

Bu sözleşme yönetim çözümü kılavuzu, dört bileşeni Microsoft 365:

- **Microsoft SharePoint Syntex**: Sözleşme dosyalarınızı tanımlamak ve sınıflandırmak ve sonra da bu dosyalardan uygun verileri ayıklamak için modeller oluşturun.

- **Microsoft SharePoint listeleri**: Sözleşmeleri iş kullanımına uygun bir SharePoint sunmak için modern listelerde bulunan biçimlendirmeyi kullanın.

- **Microsoft Teams**: Proje katılımcılarının sözleşmeleri gözden geçirmesine ve yönetmesine Teams bir kanal ve ilişkili sekmelerin işlevselliğini kullanın.

- **Power Automate**: Onay sürecinde sözleşmelere ve sonra ödeme için üçüncü taraf bir uygulamaya yönlendiren akışlar kullanın.

### <a name="how-it-all-works"></a>Nasıl çalışır?

  ![Belgeleri karşıya yüklemek, veri ayıklamak, paydaşları bildirmek ve sözleşmeyi onaylamak veya reddetmek için iş akışını gösteren çözümün diyagramı.](../media/content-understanding/syntex-solution-manage-contracts-overview.png)

1. Belgeler bir belge kitaplığına SharePoint karşıya yüklenen. Belge SharePoint Syntex bir belge anlama modeli uygulanmıştır. Her dosyayı, eğitimleri olan bir "sözleşme" içerik türüyle eş olup eşleşmesi için denetler. Eşleşme bulursa, dosyayı "sözleşme" olarak sınıflandırır ve belgenin içerik türünü ler.

2. Model, proje katılımcılarının görmekle ilgilendiği her sözleşme dosyasından İstemci, Yüklenici ve Ücret tutarı *gibi belirli* *verileri de çeker*.

    Aşağıdaki sayfa, modelin tanımlayacak şekilde eğitilmiş bir sözleşme örneğidir.

      ![Sözleşme örneği.](../media/content-understanding/contract.png)

3. Proje Microsoft Teams tüm paydaşlar, belge kitaplığında tüm sözleşmelerin onay veya reddedilmek için görünür durumda olduğu güvenli bir Teams kanalının üyeleridir. Proje Teams kullanarak, yeni sözleşmelerin gözden geçirilecek olması gerekirken tüm paydaşlara bu durumu bildirin.

4. Sözleşmeler Power Automate, sözleşmeler onay süreci boyunca Sözleşmeler kanalında Teams taşınır. Bir üye bir sözleşmeyi onaylarsa, sözleşme durumu onaylanır, tüm üyelere bir Teams gönderisi üzerinden bilgi oluşturulur ve sözleşmenin ödeme için hazır olduğunu göstermek için bir satır öğesi oluşturulur. Bu işlem doğrudan üçüncü taraf bir mali uygulamaya yazılacak şekilde uzatılabilir.

5. Bir üye bir sözleşmeyi reddederse, durum reddedilmiş olarak değiştirilir ve tüm üyelere bir iş gönderisi üzerinden Teams olur.

6. Bu çözümün sonunda, işletmeniz için otomatik bir iş süreci elde edildi. Çalışanlar belgelerinizin onay iş akışını başlatmak Teams için Teams kutucuk görünümünü kolayca kullanabilir. 

     ![Sözleşmeler sekmesi.](../media/content-understanding/tile-view.png)

### <a name="licensing-requirements"></a>Lisans gereksinimleri

Bu çözüm, tüm bu işlevlerin bir Microsoft 365 Kurumsal (E1, E3, E5, F3) veya İş (Temel, Standart veya Premium) lisansı kapsamında sunulmaktadır:

- Microsoft SharePoint Syntex
- Microsoft Teams
- Power Automate

### <a name="learn-how-to-use-sharepoint-syntex"></a>SharePoint Syntex'i kullanmayı SharePoint Syntex

Yeni misiniz? SharePoint Syntex? AI kullanarak içeriği yönetmek SharePoint Syntex nasıl kullanabileceğinizi öğrenin.

[SharePoint Syntex ile](/learn/paths/syntex-get-started) çalışmaya başlama öğrenme yolu, belgeleri sınıflandırmak, metin ayıklamak ve hızlı ve kolay bilgi yönetimi için belgelerinizi etiketlemek için belge anlama ve form işleme modellerini nasıl kullanabileceğinizi öğretecek.

## <a name="create-the-solution"></a>Çözümü oluşturun

Sonraki bölümlerde sözleşme yönetim çözümlerinizi yapılandırma hakkında ayrıntılı bilgi ve olacaktır. Üç adıma bölünmüştir:

- [1. Adım. Sözleşme SharePoint Syntex tanımlamak ve veri ayıklamak için veri ayıklamayı kullanma](solution-manage-contracts-step1.md)
- [2. Adım. Sözleşme Microsoft Teams kanalınızı oluşturmak için Sözleşmeler'i kullanma](solution-manage-contracts-step2.md)
- [3. Adım. Sözleşmelerinizi Power Automate akışı oluşturmak için Sözleşmelerinizi kullanma](solution-manage-contracts-step3.md)
