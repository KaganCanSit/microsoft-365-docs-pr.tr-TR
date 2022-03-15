---
title: Temel Microsoft 365 Lighthouse dağıtma
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: MICROSOFT 365 LIGHTHOUSE kullanarak Yönetilen Hizmet Sağlayıcıları (MSP)'ler için, temelleri Microsoft 365 Lighthouse öğrenin.
ms.openlocfilehash: 0e19843ee6cfebaf9b37e10929884d0671608451
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2022
ms.locfileid: "63504498"
---
# <a name="deploy-microsoft-365-lighthouse-baselines"></a>Temel Microsoft 365 Lighthouse dağıtma

Microsoft 365 Lighthouse, kullanıcıların, cihazların ve verilerin müşteri kiracıları içinde güvenliğini sağlamak için standart yönetilen kiracı yapılandırmalarını dağıtmanız olanak tanır. Deniz Feneri [ile standart olarak gelen](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) yedi varsayılan temel yapılandırma vardır. Deniz feneri dağıtım planı özelliğini kullanarak tüm kiracılarınız için güvenlik yapılandırmalarını sınıyor, test ediyor ve dağıtabilirsiniz. Dağıtım planı yalnızca etkin kiracılar tarafından kullanılabilir. Kiracı alındıktan sonra, müşterinizin geçerli yapılandırmasını varsayılan temel yapılandırmayla karşılaştırarak uygun eylemleri gerçekleştirin.

## <a name="before-you-begin"></a>Başlamadan önce

Sizin ve müşteri kiracıların, Kiracı gereksinimleri altında listelenen [gereksinimleri karşı Microsoft 365 Lighthouse](m365-lighthouse-requirements.md).

## <a name="view-a-deployment-plan"></a>Dağıtım planını görüntüleme

1. Sol gezinti sayfasında Kiracılar'ı **seçin**.

2. Kiracı listesinde, görüntülemek istediğiniz kiracıyı seçin.

3. Dağıtım **Planı sekmesini** seçin.

    Dağıtım Planı sekmesi, kiracının dağıtım planında yer alan ve her dağıtım adımı için aşağıdaki bilgileri içeren, arama edilebilir ve dışarı aktarılabilir bir liste sağlar:

    | Sütun            | Açıklama |
    |-----------------|-------------------------------------------------------------------------------------|
    | Dağıtım adımı | Dağıtım adımının açıklaması.                                                     |
    | Durum          | Dağıtım adımının durumu.                                                  |
    | Taban çizgisi        | Dağıtım adımının türetilen temeli.                             |
    | Kategori        | Dağıtım adımının Cihazlar, Kimlik veya Veri yönetimiyle ilişkili olup olmadığı. |
    | Son güncelleştirme    | Dağıtım adımının son güncelleştirme tarihi.                             |

4. Listeden gözden geçirmek istediğiniz dağıtım adımını seçin.

    Dağıtım Adımı sayfası aşağıdaki bilgileri sağlar:

    | Sütun            | Açıklama |
    |-------------------|-----------------------------------------------------------------------------------------------|
    | Özet        | Dağıtım Adımı'nın amacının özeti.                                         |
    | Taban çizgisi       | Dağıtım adımının türetilen temeli.                             |
    | Kategori       | Dağıtım adımının Cihazlar, Kimlik veya Veri yönetimiyle ilişkili olup olmadığı. |
    | Gerekli SKU   | Dağıtım adımını tamamlamak için gereken SK'lar.                                      |
    | Kullanıcının etkisi    | Adımı kiracının kullanıcılarına dağıtmanın etkisi.                             |
    | Kullanıcılarınız için | Kiracının kullanıcılarının yararlı olduğu kaynaklara bağlantılar.                             |
    | Sonraki adımlar     | Uygulanabilir herhangi bir sonraki adımla ilgili bağlantılar ve kılavuzlar.                                |

    Dağıtım adımları, dağıtım adımının gereksinimlerini karşılamak için tamamlanması gereken bir veya daha fazla işlemden oluşur. Dağıtım Adımı sayfası, dağıtım adımına dahil edilen her işlemi listeleyen ve aşağıdaki bilgileri sağlayan işlem tablosu içerir:

    | Sütun            | Açıklama |
    |-------------------|-------------------------------------------------------------|
    | İşlem adı      | Seçildiğinde geçerli İşlem sekmesini açacak olan işlem adı.          |
    | Durum            | Dağıtım sürecinde bulunan bu ayar yapılandırmalarının algılandı durumu.           |
    | Yönetim portalı | Süreçle ilişkili yapılandırma ayarlarının yönetilleren portal. |

## <a name="deploy-a-deployment-step"></a>Dağıtım adımını dağıtma

1. Sol gezinti sayfasında Kiracılar'ı **seçin**.

2. Kiracı listesinde, görüntülemek istediğiniz kiracıyı seçin.

3. Dağıtım **Planı sekmesini** seçin.

4. Dağıtım Adımı listesinden, dağıtmak istediğiniz dağıtım adımını seçin.

5. Gözden Geçir **ve dağıt'ı seçin**.

6. Yapılandırmaları **Onayla bölmesinde** Dağıt'ı **seçin**.

## <a name="test-a-deployment-step"></a>Dağıtım adımını test edin

Koşullu Erişim ilkeleri aracılığıyla dağıtılan dağıtım adımları için, ayarları kiracıya dağıtmadan dağıtım adımının yapılandırma ayarlarını var olan ilkelerde yer alan ayarlarla karşılaştırabilirsiniz.

1. Sol gezinti sayfasında Kiracılar'ı **seçin**.

2. Kiracı listesinde, görüntülemek istediğiniz kiracıyı seçin.

3. Dağıtım **Planı sekmesini** seçin.

4. Dağıtım Adımı listesinden, dağıtmak istediğiniz dağıtım adımını seçin.

5. Gözden Geçir **ve dağıt'ı seçin**.

6. Yapılandırmaları **Onayla bölmesinde** Bu ayarları **dağıtım olmadan test edin'i seçin**.

7. **Sına'ya seçin**.

Yapılandırmaları Onayla bölmesi kapanır ve ilke karşılaştırması görüntülenir. Var olan kiracıdaki her ilke Algılanan ayarlar tablosunda listelenir.

Algılanan ayarlar tablosu, var olan her ilkeyi listeler ve ayarların sayısını ve parantez içinde aşağıdaki durumlardan birini kullanan kullanıcı sayısını özetler:

| Durum         | Açıklama
|-------------|------------------------------------------------------------|
| Eşit ayarlar       | Kiracıda eşdeğer değere sahip dağıtım planı yapılandırma ayarlarının toplam sayısı.      |
| Eksik ayarlar     | Dağıtım planında, kiracıda değer eksik olan yapılandırma ayarlarının toplam sayısı.      |
| Çakışan ayarlar | Kiracıda çakışan bir değere sahip dağıtım planı yapılandırma ayarlarının toplam sayısı. |

Algılanan ayarlar, ayar ve kullanıcı düzeyinde her ilke için yapılandırma ayarı ayrıntıları sağlayan modüler bir tabloda da  görünüme sahip olabilir ve aşağıdaki ayarlar durumlarının her biri ile sıra edilebilir:

| Durum         | Açıklama
|-------------|------------------------------------------------------------|
| Toplam ayarlar       | Dağıtım sürecine dahil edilen toplam yapılandırma ayarlarının sayısı.                        |
| Eşit ayarlar       | Kiracıda eşdeğer değere sahip dağıtım planı yapılandırma ayarlarının toplam sayısı.      |
| Eksik ayarlar     | Dağıtım planında, kiracıda değer eksik olan yapılandırma ayarlarının toplam sayısı.      |
| Çakışan ayarlar | Kiracıda çakışan bir değere sahip dağıtım planı yapılandırma ayarlarının toplam sayısı. |
| Ek ayarlar       | Kiracıda değeri olan ancak dağıtım planında değer gören toplam yapılandırma ayarlarının sayısı.     |

Bu karşılaştırma yapılırken, Deniz Feneri Algılandı durumunu, Dağıtım durumu ve Dağıtım Adımı durumunu otomatik olarak güncelleştirecek.

Karşılaştırmak istediğiniz ilke yoksa, Yapılandırmaları onayla bölmesini yeniden açmak için Gözden geçir ve dağıt'ı seçin ve ardından Dağıt'ı seçin.

Karşılaştırıla bir ilke varsa, şunları da kullanabilirsiniz:

- Dağıtım planının yapılandırma ayarlarını düzenleyin ve bunları var olan ilkelere göre yeniden test edin, Gözden  Geçir ve dağıt'ı seçerek Yapılandırmaları onayla bölmesini yeniden açın, istediğiniz yapılandırma ayarlarını yapın, onay kutusunu yeniden seçin  ve bölmenin altındaki Sına'ya tıklayın.

- Aşağıdaki farkları benimsererek, geçerli yönetim portalında var olan ilkeleri düzenleyin:
  - Eksik ayarları uygulama
  - Çakışan ayarları düzenleme
  - Var olan ilkeleri silme

Deniz Feneri aracılığıyla otomatik hale edilemedi her dağıtım işlemi için hem dağıtım durumu hem de algılandı durumu vardır.

- Algılanan durum, bu işlemde yer alan ayarların şu anda ne ölçüde dağıtıldı olduğunu gösterir.
- Dağıtım durumu, kiracıya son dağıtımın durumu olur.

Dağıtım adımları var olan ilkelerden bağımsız olarak dağıtılabilir, ancak çakışan bir ayar olmayana kadar tam olarak kabul edilir. Bu çakışan ayarların çözüme kavuşturmalığı kullanıcı deneyimini etkileyebilirsiniz. 

Kiracıda var olan bir ilkeden eşit ayarlar olduğunda, dağıtım adımının dağıtımı, kiracı içinde var olan ayarların çoğaltılmasıyla sonuçlanmayacak ancak kullanıcı deneyimini etkilemeyecek. 

Farkındalığınız için fazladan ayarlar sağlanır, ancak herhangi bir işlemle işlemnizi gerektirmez.

İlke çakışması yönetimi hakkında daha fazla bilgi için [bkz. Azure AD Koşullu Erişim belgeleri](/azure/active-directory/conditional-access/).

## <a name="update-deployment-step-status"></a>Dağıtım adımı durumunu güncelleştirme

1. Sol gezinti sayfasında Kiracılar'ı **seçin**.

2. Kiracı listesinde, görüntülemek istediğiniz kiracıyı seçin.

3. Dağıtım **Planı sekmesini** seçin.

4. Dağıtım adımı listesinde güncelleştirmek istediğiniz dağıtım adımını seçin.

5. Son **adres açılan** listesinden bir eylem durumu seçin.

    | Eylem durumu                        | Açıklama      |
    |---------------------------------------|----------------------------------------|
    | Adres                        | Birden çok dağıtım adımı işlemi içermeen tüm dağıtım adımlarının varsayılan durumu.      |
    | Planlı                           | Dağıtım adımı planlanmıştır, ancak henüz tamamlanmamıştır.                                      |
    | Risk kabul edildi                     | Kullanıcı, aksi takdirde dağıtım adımının uygulanmasıyla geri çevirilabilecek riski kabul etmiştir. |
    | Üçüncü Taraf aracılığıyla çözülen risk | Bu risk, üçüncü taraf bir uygulama veya yazılımın uygulanmasıyla çözülür.             |
    | Alternatif yollarla çözümlendi  | Risk, iç aracın uygulanması gibi alternatif araçlarla çözülür.    |
    | El ile yapılandırma uygulandı      | Dağıtım planında belli olan yapılandırma el ile uygulanmıştır.                         |

## <a name="share-deployment-step"></a>Dağıtım adımı paylaşma

1. Sol gezinti sayfasında Kiracılar'ı **seçin**.

2. Kiracı listesinde, görüntülemek istediğiniz kiracıyı seçin.

3. Dağıtım **Planı sekmesini** seçin.

4. Dağıtım Adımı listesinden paylaşmak istediğiniz dağıtım adımını seçin.

5. Paylaş **açılan** listesinde, aşağıdaki seçeneklerden birini belirleyin.

    | Seçenek  | Açıklama |
    |-----------|-------------------------------------------------------------------------|
    | Kopyala  | Dağıtım adımının bağlantısını panoya kopyalar.                                     |
    | E-posta | Yeni e-posta iletinizi yerel makinede açar ve dağıtım adımının bağlantısını ekler. |

    Bağlantı, kuruluş izinleri olan herkesin kiracının dağıtım planını görüntülemesine olanak sağlar.


## <a name="related-content"></a>İlgili içerik

[Standart kiracı yapılandırmalarını dağıtmak için taban çizgilerini kullanmaya genel bakış](m365-lighthouse-deploy-standard-tenant-configurations-overview.md) (makale)\
[Microsoft 365 Kiracılar sayfasına genel bakış](m365-lighthouse-tenants-page-overview.md) (makale)\
[Microsoft 365 Lighthouse SSS](m365-lighthouse-faq.yml) (makale)\
[Portal Microsoft 365 Lighthouse yapılandırma](m365-lighthouse-configure-portal-security.md) (makale) 