---
title: Cihaz etiketlerini oluşturma ve yönetme
description: Bağlam yakalamak ve bir olayın parçası olarak dinamik liste oluşturulmasını sağlamak için cihaz etiketlerini kullanarak cihazları grupla
keywords: etiketler, cihaz etiketleri, cihaz grupları, gruplar, düzeltme, düzey, kurallar, aad grubu, rol, atama, derece
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 65df8553f5ee3b7dd7876557398e0d4aa22c7bd5
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63323535"
---
# <a name="create-and-manage-device-tags"></a>Cihaz etiketlerini oluşturma ve yönetme

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender'ı mı deneyimliysiniz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

Mantıksal bir grup ilişkisi oluşturmak için cihazlara etiketler ekleyin. Cihaz etiketleri, ağın uygun şekilde eşlenmesini destekleyerek bağlamı yakalamak için farklı etiketler eklemenize ve bir olayın parçası olarak dinamik liste oluşturmayı etkinleştirmenizi sağlar. Etiketler, Cihaz envanteri görünümünde **filtre olarak veya** cihazları grupla için kullanılabilir. Cihaz grupları hakkında daha fazla bilgi için bkz. [Cihaz grupları oluşturma ve yönetme](machine-groups.md).

Cihazlara aşağıdaki yöntemleri kullanarak etiket ebilirsiniz:

- Portalı kullanma
- Kayıt defteri anahtarı değeri ayarlama

> [!NOTE]
> Etiketin cihaza eklenme zamanı ile cihaz listesinde ve cihaz sayfasında kullanılabilirliği arasında bir gecikme olabilir.

API kullanarak cihaz etiketleri eklemek için bkz. [Cihaz etiketleri API'si ekleme veya kaldırma](add-or-remove-machine-tags.md).

## <a name="add-and-manage-device-tags-using-the-portal"></a>Portalı kullanarak cihaz etiketleri ekleyin ve yönetin

1. Etiketleri yönetmek istediğiniz cihazı seçin. Aşağıdaki görünümlerden herhangi birinden bir cihaz seçebilir veya arayabilirsiniz:

   - **Güvenlik işlemleri panosu** - Etkin uyarıları olan en üstteki cihazlar bölümünden cihazın adını seçin.
   - **Uyarıları kuyruğu** - Uyarılar kuyruğundan cihaz simgesinin yanındaki cihaz adını seçin.
   - **Cihaz envanteri** - Cihazlar listesinden cihaz adını seçin.
   - **Arama kutusu** - Açılan menüden Cihaz'ı seçin ve cihaz adını girin.

     Ayrıca, uyarı sayfasına dosya ve IP görünümleri aracılığıyla da ulaşabilirsiniz.

2. Yanıt **eylemleri satırından** Etiketleri yönet'i seçin.

    :::image type="content" alt-text="Etiketleri yönet düğmesinin resmi." source="images/manage-tags-option.png":::

3. Etiketleri bulmak veya oluşturmak için yazın

    :::image type="content" alt-text="Cihaza etiket ekleme resmi1." source="images/create-new-tag.png":::

Etiketler cihaz görünümüne eklenir ve Cihazlar envanter görünümüne **de yansıt** yansıtılmaktadır. Daha sonra ilgili cihaz **listesini** görmek için Etiketler filtresini kullanabilirsiniz.

> [!NOTE]
> Filtreleme, parantez içeren etiket adlarına göre çalışmayabilirsiniz.
>
> Yeni etiket ekleyebilirsiniz, var olan etiketlerin listesi görüntülenir. Listede yalnızca portal aracılığıyla oluşturulan etiketler görüntülenir. İstemci cihazlarından oluşturulan mevcut etiketler görüntülenmez.

Ayrıca, etiketleri bu görünümden de silebilirsiniz.

:::image type="content" alt-text="Cihaz2'ye etiket ekleme görüntüsü." source="images/new-tag-label-display.png":::

## <a name="add-device-tags-by-setting-a-registry-key-value"></a>Kayıt defteri anahtarı değerini ayarerek cihaz etiketleri ekleme

> [!NOTE]
> Yalnızca aşağıdaki cihazlarda uygulanabilir:
>
> - Windows 11
> - Windows 10, sürüm 1709 veya sonrası
> - Windows Server, sürüm 1803 veya sonrası
> - Windows Server 2016
> - Windows Server 2012 R2
> - Windows Server 2008 R2 SP1
> - Windows 8.1
> - Windows 7 SP1

> [!NOTE]
> Etikette ayarlan en fazla karakter sayısı 200'tir.

Belirli bir cihaz listesine bağlamsal eylem uygulamanız gerekirken benzer etiketlere sahip cihazlar çok kullanışlıdır.

Cihaza etiket eklemek için aşağıdaki kayıt defteri anahtarı girdisini kullanın:

- Kayıt defteri anahtarı: `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection\DeviceTagging\`
- Kayıt defteri anahtarı değeri (REG_SZ): `Group`
- Kayıt defteri anahtarı verileri: `Name of the tag you want to set`

> [!NOTE]
> Cihaz etiketi, günde bir kez oluşturulan cihaz bilgileri raporunun bir bölümüdir. Alternatif olarak, yeni bir cihaz bilgi raporunu aktaran uç noktayı yeniden başlatmayı seçebilirsiniz.
>
> Yukarıdaki Kayıt Defteri anahtarı kullanılarak eklenmiş bir etiketi kaldırmanız gerekirse, 'Group' anahtarını kaldırmak yerine Kayıt Defteri anahtarı verilerinin içeriğini kaldırın.
