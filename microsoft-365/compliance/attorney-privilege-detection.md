---
title: eBulma'da avukat-istemci ayrıcalık algılamayı ayarlama (Premium)
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
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
description: Bir Microsoft Purview eKeşif (Premium) olaydaki içeriği gözden geçirirken makine öğrenmesi tabanlı ayrıcalıklı içerik algılamasını kullanmak için avukat-istemci ayrıcalık algılama modelini kullanın.
ms.openlocfilehash: 9f81ff216ecf0045aec69191b3a61916b6ea3081
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624641"
---
# <a name="set-up-attorney-client-privilege-detection-in-ediscovery-premium"></a>eBulma'da avukat-istemci ayrıcalık algılamayı ayarlama (Premium)

Herhangi bir eBulma işleminin gözden geçirme aşamasının önemli ve maliyetli bir yönü, ayrıcalıklı içerik için belgeleri gözden geçirmektir. Microsoft Purview eKeşif (Premium), bu süreci daha verimli hale getirmek için makine öğrenmesi tabanlı ayrıcalıklı içerik algılaması sağlar. Bu özellik *, avukat-istemci ayrıcalık algılama* olarak adlandırılır.

## <a name="how-does-it-work"></a>Nasıl çalışır?

Avukat-istemci ayrıcalık algılama etkinleştirildiğinde, gözden geçirme kümesindeki [verileri analiz](analyzing-data-in-review-set.md) ettiğinizde, bir gözden geçirme kümesindeki tüm belgeler avukat-istemci ayrıcalık algılama modeli tarafından işlenir. Model iki şeyi arar:

- Ayrıcalıklı içerik – Model, belgenin doğası gereği yasal içerik içerme olasılığını belirlemek için makine öğrenmesini kullanır.

- Katılımcılar – Avukat-müşteri ayrıcalık algılamasını ayarlamanın bir parçası olarak, kuruluşunuz için bir avukat listesi göndermeniz gerekir. Model daha sonra belgenin katılımcılarını avukat listesiyle karşılaştırarak belgenin en az bir avukat katılımcısı olup olmadığını belirler.

Model, her belge için aşağıdaki üç özelliği üretir:

- **AttorneyClientPrivilegeScore:** Belgenin doğası gereği yasal olma olasılığı; puanının değerleri **0** ile **1** arasındadır.

- **HasAttorney:** Bu özellik, belge katılımcılarından biri avukat listesinde listeleniyorsa **true** olarak ayarlanır; aksi takdirde değer **false'tur**. Kuruluşunuz bir avukat listesi **yüklemediyse değer** false olarak da ayarlanır.

- **IsPrivilege:** **Bu özellik, AttorneyClientPrivilegeScore** değeri eşiğin üzerindeyse *veya* belgenin bir avukat katılımcısı varsa **true** olarak ayarlanır; aksi takdirde değer **false** olarak ayarlanır.

Bu özellikler (ve bunlara karşılık gelen değerler), aşağıdaki ekran görüntüsünde gösterildiği gibi, bir gözden geçirme kümesindeki belgelerin dosya meta verilerine eklenir:

![Dosya meta verilerinde gösterilen avukat-istemci ayrıcalık özellikleri.](../media/AeDAttorneyClientPrivilegeMetadata.png)

Bu üç özellik bir gözden geçirme kümesi içinde de aranabilir. Daha fazla bilgi için bkz. [Gözden geçirme kümesindeki verileri sorgulama](review-set-search.md).

## <a name="set-up-the-attorney-client-privilege-detection-model"></a>Avukat-istemci ayrıcalık algılama modelini ayarlama

Avukat-istemci ayrıcalık algılama modelini etkinleştirmek için kuruluşunuzun bunu açıp bir avukat listesi yüklemesi gerekir.

### <a name="step-1-turn-on-attorney-client-privilege-detection"></a>1. Adım: Avukat-istemci ayrıcalık algılamayı açma

Kuruluşunuzda eBulma Yöneticisi olan bir kişi (eBulma Yöneticisi rol grubundaki eBulma Yöneticisi alt grubunun üyesi) modeli eBulma (Premium) durumlarınızda kullanılabilir hale getirmelidir.

1. Microsoft Purview uyumluluk portalı [, eBulma (Premium)](https://go.microsoft.com/fwlink/p/?linkid=2173764) seçeneğine gidin ve **ardından eBulma (Premium) ayarları'na** tıklayın.

   ![eBulma (Premium) ayarlarını seçin](..\media\HistoricalVersions1.png)

2. **Ayarlar** sayfasında **Analiz** sekmesini seçin ve **ardından Avukat-istemci ayrıcalık algılama** iki durumlu düğmesini açık konuma getirin.

   ![Avukat-istemci ayrıcalık algılamasını açmak için iki durumlu düğmeyi tıklatın](..\media\TurnOnAttorneyClientPrivilegeDetection.png)

3. Değişikliği kaydetmek için **Kaydet'e** tıklayın.

### <a name="step-2-upload-a-list-of-attorneys-optional"></a>2. Adım: Avukat listesini karşıya yükleme (isteğe bağlı)

Avukat-istemci ayrıcalık algılama modelinden tam olarak yararlanmak ve daha önce açıklanan **Has Attorney** veya **Potansiyel Ayrıcalıklı** algılama sonuçlarını kullanmak için, kuruluşunuzda çalışan avukatlar ve hukuk personeli için e-posta adreslerinin bir listesini karşıya yüklemenizi öneririz.

Avukat-istemci ayrıcalık algılama modeli tarafından kullanılmak üzere bir avukat listesi yüklemek için:

1. Bir .csv dosyası oluşturun (üst bilgi satırı olmadan) ve her uygun kişinin e-posta adresini ayrı bir satıra ekleyin. Bu dosyayı yerel bilgisayarınıza kaydedin.

2. eBulma (Premium) **Ayarları** sayfasında **Analiz** sekmesini seçin.

   **Avukat-istemci ayrıcalık** sayfası görüntülenir ve **Avukat-müşteri ayrıcalık algılama** iki durumlu düğmesi açılır.

   ![Avukat-istemci ayrıcalık açılır sayfası](..\media\AeDUploadAttorneyList1.png)

3. **Dosya seç'i** seçin ve ardından 1. adımda oluşturduğunuz .csv dosyasını bulun ve seçin.

4. Avukat listesini karşıya yüklemek için **Kaydet'i** seçin.

## <a name="use-the-attorney-client-privilege-detection-model"></a>Avukat-istemci ayrıcalık algılama modelini kullanma

Gözden geçirme kümesindeki belgeler için avukat-istemci ayrıcalık algılamasını kullanmak için bu bölümdeki adımları izleyin.

### <a name="step-1-create-a-smart-tag-group-with-attorney-client-privilege-detection-model"></a>1. Adım: Avukat-istemci ayrıcalık algılama modeliyle akıllı etiket grubu oluşturma

Gözden geçirme sürecinizde avukat-istemci ayrıcalık algılamasının sonuçlarını görmenin birincil yollarından biri akıllı etiket grubu kullanmaktır. Akıllı etiket grubu, avukat-istemci ayrıcalık algılamasının sonuçlarını gösterir ve sonuçları bir akıllı etiket grubundaki etiketlerin yanında satır içinde gösterir. Bu, belge gözden geçirme sırasında ayrıcalıklı olabilecek belgeleri hızla belirlemenize olanak tanır. Ayrıca, belgeleri ayrıcalıklı veya ayrıcalıklı olmayan olarak etiketlemek için akıllı etiket grubundaki etiketleri de kullanabilirsiniz. Akıllı etiketler hakkında daha fazla bilgi için bkz. [eBulma'da akıllı etiketleri ayarlama (Premium)](smart-tags.md).

1. 1. Adımda çözümlediğiniz belgeleri içeren gözden geçirme kümesinde **Gözden geçirme kümesini yönet'i** ve ardından **Etiketleri yönet'i** seçin.

2. **Etiketler'in** altında, **Grup ekle'nin** yanındaki açılan listeden **Akıllı etiket grubu ekle'yi** seçin.

   !["Akıllı etiket grubu ekle"yi seçin.](../media/AeDCreateSmartTag.png)

3. **Akıllı etiketiniz için model seçin** sayfasında **Avukat-istemci ayrıcalığının** yanındaki **Seç'i** seçin.

   **Avukat-istemci ayrıcalığı** adlı bir etiket grubu görüntülenir. Model tarafından üretilen olası sonuçlara karşılık gelen **Pozitif** ve **Negatif** adlı iki alt etiket içerir.

   ![Avukat-istemci ayrıcalık akıllı etiket grubu.](../media/AeDAttorneyClientSmartTagGroup.png)

3. Etiket grubunu ve etiketleri gözden geçirmenize uygun şekilde yeniden adlandırın. Örneğin, **Pozitif'i** Ayrıcalıklı olarak, **Negatif'i** **ayrıcalıklı** **değil** olarak yeniden adlandırabilirsiniz.

### <a name="step-2-analyze-a-review-set"></a>2. Adım: Gözden geçirme kümesini analiz etme

Belgeleri bir gözden geçirme kümesinde analiz ettiğinizde, avukat-istemci ayrıcalık algılama modeli de çalışır ve ilgili özellikler ( [nasıl çalışır?](#how-does-it-work)) gözden geçirme kümesindeki her belgeye eklenir. Gözden geçirme kümesindeki verileri analiz etme hakkında daha fazla bilgi için bkz. [eBulma (Premium)'da bir gözden geçirme kümesindeki verileri analiz](analyzing-data-in-review-set.md) etme.

### <a name="step-3-use-the-smart-tag-group-for-review-of-privileged-content"></a>3. Adım: Ayrıcalıklı içeriği gözden geçirmek için akıllı etiket grubunu kullanma

Gözden geçirme kümesini analiz ettikten ve akıllı etiketleri ayarladıktan sonra, sonraki adım belgeleri gözden geçirmektir. Model belgenin potansiyel olarak ayrıcalıklı olduğunu belirlemişse Etiketleme **panelindeki** ilgili akıllı etiket, avukat-istemci ayrıcalık algılaması tarafından üretilen aşağıdaki sonuçları gösterir:

- Belgenin doğası gereği yasal olabilecek içeriği varsa, ilgili akıllı etiketin yanında **Yasal içerik** etiketi görüntülenir (bu durumda varsayılan **Pozitif** etikettir).

- Belge, kuruluşunuzun avukat listesinde bulunan bir katılımcıya sahipse, ilgili akıllı etiketin yanında **Avukat** etiketi görüntülenir (bu durumda varsayılan **Pozitif** etiket de budur).

- Belgenin doğası gereği yasal olabilecek içeriği varsa *ve* avukat listesinde bulunan bir katılımcı varsa, hem **Yasal içerik**  hem de **Avukat** etiketleri görüntülenir. 

Model, belgenin doğası gereği yasal içerik içermediğini veya avukat listesinden bir katılımcı içermediğini belirlerse, etiketleme panelinde iki etiket de görüntülenmez.

Örneğin, aşağıdaki ekran görüntülerinde iki belge gösterilir. İlki, doğası gereği yasal olan ve avukat listesinde bulunan bir katılımcısı olan içeriği içerir. İkincisi hiçbirini içermez ve bu nedenle herhangi bir etiket görüntülemez.

![Avukat ve Yasal içerik etiketleri içeren belge.](../media/AeDTaggingPanelLegalContentAttorney.png)

![Etiket içermeyen belge.](../media/AeDTaggingPanelNegative.png)

Ayrıcalıklı içerik içeren bir belgeyi gözden geçirdikten sonra, belgeyi uygun etiketle etiketleyebilirsiniz.
