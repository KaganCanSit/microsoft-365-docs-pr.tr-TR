---
title: Microsoft SharePoint Syntex'ta bir ayıklaıcı oluştururken terim deposu taksonomisini SharePoint Syntex
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
description: Microsoft web sitesinde belgenizin anlama modelinde bir ayıklaıcı oluştururken terim deposu taksonomisini SharePoint Syntex.
ms.openlocfilehash: 909f26026ddf26163a12e1d14c1790f4af93a160
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63328813"
---
# <a name="leverage-term-store-taxonomy-when-creating-an-extractor-in-microsoft-sharepoint-syntex"></a>Microsoft SharePoint Syntex'ta bir ayıklaıcı oluştururken terim deposu taksonomisini SharePoint Syntex

</br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4GpJJ]  

</br>

SharePoint Syntex kullanarak belgenizin anlama modelinde bir ayıklaıcı ekleyebilirsiniz ve ayıklanan veriler için tercih edilen terimleri görüntülemek için terim deposu'daki genel [](/sharepoint/managed-metadata) terim kümelerinden yararlanabilirsiniz.  

Örnek olarak, modeliniz belge kitaplığına yüklenen tüm **Sözleşme** belgelerini tanımlar ve sınıflar.  Buna ek olarak, model **her sözleşmeden** bir Sözleşme Hizmeti değeri de ayıklar ve bunu kitaplık görünümde bir sütunda görüntüler. Sözleşmelerde yer alan çeşitli Sözleşme Hizmetleri değerleri arasında, şirketinizin artık kullanmayta kullandığı ve yeniden adlandırılmalarınıta olan birkaç eski değer vardır. Örneğin, Tasarım, Grafik veya Topografi *sözleşme* hizmetlerinin tüm *başvurularını artık* Yaratıcı olarak ifade *etmek gerekir*. Modeliniz bir sözleşme belgesinde güncel olmayan terimlerden birini ayıklasa, kitaplık görünümde geçerli terimi - Creative - görüntülemesini istersiniz. Aşağıdaki örnekte, modele eğitim yaparken, örnek belgelerden birinin Tasarım'ın süresi öncemiş terimini içerdiğini *görüyoruz*.

   ![Terim deposu.](../media/content-understanding/design.png)</br>

## <a name="use-a-managed-metadata-column-in-your-extractor"></a>Ayıklaıcıda Yönetilen meta veri sütunu kullanma

Terim kümeleri, yönetim merkezinin Yönetilen Meta Veri hizmetleri (MMS) <a href="https://go.microsoft.com/fwlink/?linkid=2185219" target="_blank">terim SharePoint yapılandırılır</a>. Aşağıdaki örnekte, Sözleşme *Hizmetleri* [terim kümesi](/sharepoint/managed-metadata#term-set) Creative gibi çeşitli terimleri içerecek şekilde *yapılandırılmıştır*.  Terimin üç eş anlamlısı *(Tasarım**, Grafik* ve *Topografi*) olduğunu ve eş anlamlıların Yaratıcı olarak çevril olması gerektiğini *ayrıntılarıyla gösterir*. 

   ![Terim kümesi.](../media/content-understanding/term-store.png)</br>

Terim kümeniz içinde eş anlamlı kullanmak istemenizin birçok nedeni olabilir. Örneğin, eski terimler, yeniden adlandırılmış terimler veya adlandırmayla ilgili kuruluş bölümlerinizi farklı kullanabilirsiniz.

Ayıklayıcınızı modelde 2013'te 7000 yer alan yönetilen meta veri alanını seçen bir hale çıkarmak için, bunu bir yönetilen meta [veri sitesi sütunu olarak eklemeniz gerekir](https://support.microsoft.com/office/8fad9e35-a618-4400-b3c7-46f02785d27f). Site sütununu ekledikten sonra, modeliniz için ayıklaıcıyı 2013'e eklerken sütunu da seçebilirsiniz.

   ![Sözleşme hizmeti.](../media/content-understanding/contract-services.png)</br>

Modelinizi belge kitaplığına yükledikten sonra, belgeler kitaplı kitaplara karşıya yüklendikten sonra, ayıklaıcı eş anlamlı değerlerden (*Tasarım, Grafik* ve *Topography*) herhangi birini bulduğunda *Creative Services* sütunu tercih edilen terimi (*Creative*) görüntüler.

   ![Sözleşmeli hizmet sütunu.](../media/content-understanding/creative.png)</br>


## <a name="see-also"></a>Ayrıca Bkz
[Yönetilen Meta Verilere Giriş](/sharepoint/managed-metadata#terms)

[Ayıklaıcı oluşturma](create-an-extractor.md)

[Yönetilen meta veri sütunu oluşturma](https://support.microsoft.com/office/create-a-managed-metadata-column-8fad9e35-a618-4400-b3c7-46f02785d27f?redirectSourcePath=%252farticle%252fc2a06717-8105-4aea-890d-3082853ab7b7&ui=en-US&rs=en-US&ad=US)