---
title: Microsoft SharePoint Syntex'da ayıklayıcı oluştururken terim deposu taksonomisini kullanma
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom: admindeeplinkSPO
ms.localizationpriority: medium
description: Microsoft SharePoint Syntex belge anlama modelinizde ayıklayıcı oluştururken terim deposu taksonomisini kullanın.
ms.openlocfilehash: d3f2acf32231558f9f56a62b18c6dd7ffbc4e20f
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64861498"
---
# <a name="leverage-term-store-taxonomy-when-creating-an-extractor-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'da ayıklayıcı oluştururken terim deposu taksonomisini kullanma

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GpJJ]  

</br>

SharePoint Syntex kullanarak belge anlama modelinizde bir ayıklayıcı oluşturduğunuzda, ayıkladığınız verilerin tercih edilen terimlerini görüntülemek için [terim deposundaki genel terim](/sharepoint/managed-metadata) kümelerinden yararlanabilirsiniz.  

Örneğin, modeliniz belge kitaplığına yüklenen tüm **Sözleşme** belgelerini tanımlar ve sınıflandırır.  Ayrıca model, her sözleşmeden bir **Sözleşme Hizmeti** değeri ayıklar ve bunu kitaplık görünümünüzdeki bir sütunda görüntüler. Sözleşmelerdeki çeşitli Sözleşme Hizmetleri değerleri arasında, şirketinizin artık kullanmadığını ve yeniden adlandırıldığı birkaç eski değer vardır. Örneğin *Tasarım,* Grafik veya *Topografi* sözleşme hizmetleri *terimlerine yapılan tüm başvurular* artık *Creative* olarak adlandırılmalıdır. Modeliniz bir sözleşme belgesinden güncel olmayan terimlerden birini ayıklasa, geçerli creative terimini kitaplık görünümünüzde görüntülemesini istersiniz. Aşağıdaki örnekte, modeli eğitirken bir örnek belgenin *eski Tasarım* terimini içerdiğini görüyoruz.

   ![Terim deposu.](../media/content-understanding/design.png)</br>

## <a name="use-a-managed-metadata-column-in-your-extractor"></a>Ayıklayıcınızda Yönetilen meta veri sütunu kullanma

Terim kümeleri, <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">SharePoint yönetim merkezindeki</a> Yönetilen Meta Veri hizmetleri (MMS) terim deposunda yapılandırılır. Aşağıdaki örnekte *Sözleşme Hizmetleri* [terim kümesi](/sharepoint/managed-metadata#term-set)*, Creative* dahil olmak üzere çeşitli terimler içerecek şekilde yapılandırılmıştır.  Bunun ayrıntıları, terimin üç eş anlamlıya (*Tasarım*, *Grafik* ve *Topografi*) sahip olduğunu ve eş anlamlıların *Creative'e* çevrilmesi gerektiğini gösterir. 

   ![Terim kümesi.](../media/content-understanding/term-store.png)</br>

Terim kümenizde eş anlamlı kullanmak istemenizin birçok nedeni olabilir. Örneğin, eski terimler, yeniden adlandırılmış terimler veya adlandırma konusunda kuruluşunuzun departmanları arasında çeşitlemeler olabilir.

Modelinizde ayıklayıcınızı oluştururken yönetilen meta veri alanını seçilebilir hale getirmek için, [bunu yönetilen meta veri site sütunu olarak eklemeniz](https://support.microsoft.com/office/8fad9e35-a618-4400-b3c7-46f02785d27f) gerekir. Site sütununu ekledikten sonra, modeliniz için ayıklayıcıyı oluştururken bunu seçebilirsiniz.

   ![Sözleşme hizmeti.](../media/content-understanding/contract-services.png)</br>

Modelinizi belge kitaplığına uyguladıktan sonra, belgeler kitaplığa yüklendiğinde, ayıklayıcı eş anlamlı değerlerden herhangi birini (*Tasarım*, *Grafikler* ve *Topografi*) bulduğunda *Creative Services* sütunu tercih edilen terimi (*Creative*) görüntüler.

   ![Sözleşme hizmeti sütunu.](../media/content-understanding/creative.png)</br>

> [!NOTE]
> Terim kümesi açıksa, tercih edilen terim veya eş anlamlı değerle eşleşmeyen ayıklanan değerler terim kümesinin köküne yeni bir terim olarak eklenir. Bu yeni terimler terim kümesinin bulunduğu terim deposunda taşınabilir, birleştirilebilir veya eş anlamlılar oluşturulabilir.

## <a name="see-also"></a>Ayrıca bkz.
[Yönetilen Meta Verilere Giriş](/sharepoint/managed-metadata#terms)

[Ayıklayıcı oluşturma](create-an-extractor.md)

[Yönetilen meta veri sütunu oluşturma](https://support.microsoft.com/office/create-a-managed-metadata-column-8fad9e35-a618-4400-b3c7-46f02785d27f?redirectSourcePath=%252farticle%252fc2a06717-8105-4aea-890d-3082853ab7b7&ui=en-US&rs=en-US&ad=US)