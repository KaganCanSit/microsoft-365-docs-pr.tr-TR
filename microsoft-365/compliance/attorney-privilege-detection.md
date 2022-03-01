---
title: Advanced eDiscovery'de avukatlık ayrıcalık algılaması Advanced eDiscovery
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Bir davanın içeriğini gözden geçirerek makinede öğrenme tabanlı ayrıcalıklı içeriğin algılanması makinede kullanmak için avukatlık ayrıcalık algılama Advanced eDiscovery kullanın.
ms.openlocfilehash: 5e8a9e1ef0cf8cd8375cd6ce9a0b4d210840e838
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021732"
---
# <a name="set-up-attorney-client-privilege-detection-in-advanced-ediscovery"></a>Advanced eDiscovery'de avukatlık ayrıcalık algılaması Advanced eDiscovery

Herhangi bir eBulma işleminin gözden geçirme aşamasının önemli ve maliyetli bir yönü, ayrıcalıklı içeriğin belgelerini gözden geçirmektir. Advanced eDiscovery bu süreci daha verimli hale getirir. Bu özellik, *avukat-istemci ayrıcalık algılama olarak adlandırılan bir özelliktir*.

## <a name="how-does-it-work"></a>Nasıl çalışır?

Avukat-istemci ayrıcalık algılama etkinleştirildiğinde, inceleme kümesinde verileri çözümledikten sonra, gözden geçirme kümesinde yer alan tüm belgeler, avukatlık [](analyzing-data-in-review-set.md) ayrıcalık algılama modeli tarafından işlenir. Model iki şeyi gösterir:

- Ayrıcalıklı içerik – Model, belgenin doğada yasal içerik ekleme olasılığını belirlemek için makine öğrenimi kullanır.

- Katılımcılar – Avukatlık ayrıcalık algılaması ayarlamanın bir parçası olarak, organizasyonunız için bir avukat listesi göndermeniz gerekir. Daha sonra model, bir belgede en az bir avukat katılımcısı olup olmadığını belirlemek için belgenin katılımcılarını avukat listesiyle karşılaştırıldığında.

Model, her belge için aşağıdaki üç özelliği üretir:

- **AttorneyClientPrivilegeScore:** Belgenin doğayla ilgili yasal olma olasılığı; puanın değerleri **0** ile **1 arasındadır**.

- **HasAttorney:** Belge katılımcılarından biri **avukat** listesinde yer alıyorsa bu özellik doğru olarak ayarlanır; aksi takdirde değer **yanlış olur**. Ayrıca, organizasyonunız bir **avukat** listesi yüklemezse değer yanlış olarak ayarlanır.

- **IsPrivilege:** Bu özellik, **AvukatClientPrivilegeScore** değeri eşiğin üzerinde ise veya belgede bir avukat katılımcısı  varsa true olarak ayarlanır; aksi takdirde değer **false olarak ayarlanır**.

Bu özellikler (ve bunlara karşılık gelen değerler), aşağıdaki ekran görüntüsünde gösterildiği gibi, gözden geçirme kümesinde belgelerin dosya meta verilerine eklenir:

![Dosya meta verilerinde gösterilen avukat-istemci ayrıcalık özellikleri.](../media/AeDAttorneyClientPrivilegeMetadata.png)

Bu üç özellik de gözden geçirme kümesi içinde aranabilir. Daha fazla bilgi için bkz [. Gözden geçirme kümesinde verileri sorgulama](review-set-search.md).

## <a name="set-up-the-attorney-client-privilege-detection-model"></a>Avukat-istemci ayrıcalık algılama modelini ayarlama

Avukat-istemci ayrıcalık algılama modelini etkinleştirmek için, kuruluş bu modeli açmalı ve sonra bir avukat listesi yüklesin.

### <a name="step-1-turn-on-attorney-client-privilege-detection"></a>1. Adım: Avukat-müşteri ayrıcalık algılamayı açma

Kurumda eBulma Yöneticisi olan bir kişi (eBulma Yöneticisi rol grubunda eBulma Yöneticisi alt grubunun bir üyesi) modelin sizin veya Advanced eDiscovery tarafından kullanılabilir olması gerekir.

1. Sayfa Microsoft 365 uyumluluk merkezi, [Ayarlar'a Advanced eDiscovery](https://go.microsoft.com/fwlink/p/?linkid=2173764) ve Ayarları **Değiştir'Advanced eDiscovery tıklayın**.

   ![Advanced eDiscovery seçin](..\media\HistoricalVersions1.png)

2. Ekran **Ayarlar** Analiz **sekmesini seçin ve** ardından Avukatlık ayrıcalık **algılaması** iki durumlu düğmesini açık olarak ayarlayın.

   ![Avukatlık ayrıcalık algılamayı açmak için iki durumlu düğmeyi tıklatın](..\media\TurnOnAttorneyClientPrivilegeDetection.png)

3. Değişikliği **kaydetmek için** Kaydet'e tıklayın.

### <a name="step-2-upload-a-list-of-attorneys-optional"></a>2. Adım: Upload listesi (isteğe bağlı)

Avukat-istemci ayrıcalık algılama modelinden tam olarak yararlanmak ve daha önce açıklanan Avukata Sahip veya  Ayrıcalıklı Olabilecek algılama  sonuçlarını kullanmak için, kurum için çalışan personel ve personeli için bir e-posta adresi listesi yüklemenizi öneririz.

Avukat-istemci ayrıcalık algılama modeli tarafından kullanmak üzere bir avukat listesini karşıya yüklemek için:

1. Başlık .csv bir dosya oluşturun ve her uygun kişinin e-posta adresini ayrı bir satıra ekleyin. Bu dosyayı yerel bilgisayarınıza kaydedin.

2. Ana Advanced eDiscovery **Ayarlar** **Analiz sekmesini seçin**.

   **Avukat-istemci ayrıcalık** sayfası görüntülenir ve **Vekaletname ayrıcalık algılama** iki durumlu düğmeyi açık.

   ![Avukat-istemci ayrıcalık uçarak giriş sayfası](..\media\AeDUploadAttorneyList1.png)

3. Dosya **seç'i** seçin ve 1. .csv oluşturduğunuz dosyanın adını bulun ve seçin.

4. Avukat **listesini karşıya** yüklemek için Kaydet'i seçin.

## <a name="use-the-attorney-client-privilege-detection-model"></a>Avukat-istemci ayrıcalık algılama modelini kullanma

Bu bölümdeki adımları takip edin ve gözden geçirme kümesinde belgeler için avukatlık ayrıcalık algılamayı kullanın.

### <a name="step-1-create-a-smart-tag-group-with-attorney-client-privilege-detection-model"></a>1. Adım: Avukat-istemci ayrıcalık algılama modeliyle akıllı etiket grubu oluşturma

İnceleme süreciniz içinde avukatlık ayrıcalık algılama sonuçlarını görmenin başlıca yollarından biri akıllı etiket grubu kullanmaktır. Akıllı etiket grubu, avukat-istemci ayrıcalık algılama sonuçlarını gösterir ve akıllı etiket grubunda etiketlerin yanında sonuçları satır içinde gösterir. Bu, belgeyi gözden geçirme sırasında kolayca ayrıcalıklı olabilecek belgeleri tanımlamanıza olanak sağlar. Bunlara ek olarak, akıllı etiket grubunda etiketleri kullanarak belgeleri ayrıcalıklı veya ayrıcalıklı değil olarak etiketebilirsiniz. Akıllı etiketler hakkında daha fazla bilgi için bkz. Akıllı [etiketler için Advanced eDiscovery](smart-tags.md).

1. 1. Adım'da çözümley istediğiniz belgeleri içeren gözden geçirme kümesinde, Gözden geçirme  kümesi yönet'i ve sonra da Etiketleri **yönet'i seçin**.

2. **Etiketler'in** altında Grup ekle'nin yanındaki aşağı **çekin ve** ardından Akıllı etiket **grubu ekle'yi seçin**.

   !["Akıllı etiket grubu ekle"yi seçin.](../media/AeDCreateSmartTag.png)

3. Akıllı **etiketiniz için model seçin sayfasında** , Avukatlık **ayrıcalıklarının** yanındaki **Seç'i seçin**.

   Avukat-istemci **ayrıcalığı adlı bir etiket** grubu görüntülenir. Pozitif ve Negatif adlı iki **alt** etiket **içerir** ve bu etiket modelin ürettiği olası sonuçlara karşılık gelir.

   ![Avukat-istemci ayrıcalık akıllı etiket grubu.](../media/AeDAttorneyClientSmartTagGroup.png)

3. Etiket grubunu ve etiketleri gözden geçirmenize uygun şekilde yeniden adlandırabilirsiniz. Örneğin, Pozitif'i Ayrıcalıklı olarak **ve Negatif'i** **de Ayrıcalıklı** **Değil** **olarak yeniden adlandırsınız**.

### <a name="step-2-analyze-a-review-set"></a>2. Adım: Gözden geçirme kümesi çözümleme

İnceleme kümesinde belgeleri analiz etmenizde, avukat-istemci ayrıcalık algılama modeli de çalışır ve ilgili özellikler (Nasıl çalışır [?](#how-does-it-work)) gözden geçirme kümesinde her belgeye eklenir. Gözden geçirme kümesinde verileri çözümleme hakkında daha fazla bilgi için bkz. Gözden [geçirme kümesinde verileri çözümleme Advanced eDiscovery](analyzing-data-in-review-set.md).

### <a name="step-3-use-the-smart-tag-group-for-review-of-privileged-content"></a>3. Adım: Ayrıcalıklı içeriği gözden geçirmek için akıllı etiket grubunu kullanma

Akıllı etiketleri gözden geçirme ayarını ve ayarlamayı çözümledikten sonra, bir sonraki adım belgeleri gözden geçirmektir. Model, belgenin muhtemelen ayrıcalıklı olduğunu belirlediyse, Etiketleme panelindeki ilgili akıllı etiket,  avukat-istemci ayrıcalık algılaması tarafından üretilen aşağıdaki sonuçları gösterir:

- Belgenin doğanda yasal olan içeriği varsa, ilgili akıllı etiketin yanında Yasal  içerik etiketi görüntülenir (bu durumda varsayılan **Pozitif etikettir**).

- Belgede, kuruluşun avukat listesinde bulunan bir katılımcı varsa, ilgili akıllı etiketin yanında Avukat **etiketi görüntülenir (** bu durumda da varsayılan Pozitif etikettir).

- Belgede doğada yasal olan ve avukat listesinde bir katılımcısı  bulunan içerik varsa, hem Yasal içerik hem de **Avukat etiketleri** görüntülenir. 

Model bir belgenin doğayla ilgili yasal içerik içerme olmadığını veya avukatlık listesinden bir katılımcı içerme olmadığını belirlerse, etiketleme panelinde hiçbir etiket görüntülenmez.

Örneğin, aşağıdaki ekran görüntüleri iki belgeyi gösterir. İlk belge, doğada yasal olan ve avukat listesinde bulunan bir katılımcısı bulunan içeriği içeriyor. İkinci durumda da etiketlerin hiçbiri görüntülenmez.

![Avukat ve Yasal içerik etiketleri olan belge.](../media/AeDTaggingPanelLegalContentAttorney.png)

![Etiketsiz belge.](../media/AeDTaggingPanelNegative.png)

Bir belgeyi gözden geçirdikten sonra, ayrıcalıklı içerik içerdiğini görmek için belgeyi uygun etiketle etiketebilirsiniz.
