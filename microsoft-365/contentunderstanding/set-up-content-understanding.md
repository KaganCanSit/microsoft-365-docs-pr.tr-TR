---
title: SharePoint Syntex ayarlama
ms.author: mikeplum
author: MikePlumleyMSFT
ms.reviewer: ssquires
manager: serdars
audience: admin
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.custom:
- admindeeplinkMAC
search.appverid: MET150
ms.localizationpriority: high
description: SharePoint Syntex ayarlama
ms.openlocfilehash: 3511719e4f396141217a2b4711f642c675ac781e
ms.sourcegitcommit: 44ece87e3e0c0c851dfc1e77211ac3e5e4a5b973
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/05/2022
ms.locfileid: "66617248"
---
# <a name="set-up-sharepoint-syntex"></a>SharePoint Syntex ayarlama

Yöneticiler <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">microsoft SharePoint Syntex</a> ayarlamak için [Microsoft 365 yönetim merkezi](index.md) kullanabilir. 

Başlamadan önce aşağıdakileri göz önünde bulundurun:

- Form işlemeyi hangi SharePoint sitelerinde etkinleştireceksiniz? Bunların tümü, bazıları veya belirli siteler mi?
- Varsayılan içerik merkezinize ne ad vereceksiniz?

İlk kurulumdan sonra <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> ayarlarınızı değiştirebilirsiniz.

Kurulumdan önce ortamınızda içerik anlama özelliğini ayarlamanın ve yapılandırmanın en iyi yolunu planladığınızdan emin olun. Örneğin, aşağıdaki kararları vermeniz gerekir:

- Form işlemeyi etkinleştirmek istediğiniz SharePoint siteleri - bunların tümü, bazıları veya seçili siteler
- İçerik merkezinizin adı ve yöneticileri

## <a name="requirements"></a>Gereksinimler 

> [!NOTE]
> Microsoft 365 yönetim merkezi erişebilmek ve SharePoint Syntex ayarlamak için Genel yönetici veya SharePoint yönetici izinlerine sahip olmanız gerekir.

Yönetici olarak, kurulumdan sonra istediğiniz zaman ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> içerik anlama yönetimi ayarları boyunca seçtiğiniz ayarlarda değişiklik yapabilirsiniz.

### <a name="custom-power-platform-environments"></a>Özel Power Platform ortamları

Özel bir Power Platform ortamı kullanmayı planlıyorsanız, bu ortamda *Cortex Projesi için AI Builder* uygulamasını yüklemeniz gerekir. Ayrıntılar için [bkz. Dynamics 365 uygulamalarını yönetme](/power-platform/admin/manage-apps#install-an-app-in-the-environment-view) ve Dynamics 365 uygulamaları listesinde *Cortex Projesi için AI Builder* uygulamasını arama.

Form işleme modelleri oluşturabilmeniz için önce özel ortama [AI Builder kredileri ayırmanız](/power-platform/admin/capacity-add-on) da gerekir. 

Özel bir ortam kullanırken, model oluşturuculara Ortam Oluşturucu güvenlik rolü atanmalı ve model kullanıcılarına Temel Kullanıcı güvenlik rolü atanmalıdır. Daha fazla bilgi için bkz. [Kullanıcıya güvenlik rolü atama](/power-platform/admin/assign-security-roles) .

[İçerik merkezi sitesinde](/microsoft-365/contentunderstanding/create-a-content-center) model oluşturan kullanıcıların site üyesi olması gerekir. İçerik merkezi dışında yerel olarak model oluşturan kullanıcıların bu sitelerin site sahipleri olması gerekir.

### <a name="licensing"></a>Lisanslama

SharePoint Syntex kullanmak için kuruluşunuzun SharePoint Syntex aboneliği ve her kullanıcının atanmış bir lisansı olmalıdır. SharePoint Syntex lisansları, tümü atanması gereken aşağıdaki uygulamaları içerir:

- SharePoint Syntex
- SharePoint Syntex - SPO türü
- SharePoint Syntex için Common Data Service

Form işlemeyi kullanmak için AI Builder kredilerine de ihtiyacınız vardır. SharePoint Syntex lisanslı her kullanıcı için her ay bir AI Builder kredisi ayırması sağlanır.

SharePoint Syntex lisanslama hakkında ayrıntılı bilgi için bkz. [lisanslama SharePoint Syntex](syntex-licensing.md)

## <a name="to-set-up-sharepoint-syntex"></a>SharePoint Syntex ayarlamak için

1. Microsoft 365 yönetim merkezi <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**Kurulum'u**</a> seçin ve ardından **Dosyalar ve içerik** bölümünü görüntüleyin.

2. **Dosyalar ve içerik** bölümünde **İçerik anlama işlemini otomatikleştir'i** seçin. Geçerli AI Builder kredi kullanılabilirliğinizin **Bir bakışta** bölümünde gösterildiğini unutmayın.<br/>

3. **İçerik anlama işlemini otomatikleştir** sayfasında, Kurulum işleminde izlenmek için **Başlarken'e** tıklayın. <br/>

    > [!div class="mx-imgBorder"]
    > ![Kurulumu başlatın.](../media/content-understanding/admin-content-understanding-get-started.png)</br>

4. **Form İşlemeyi Yapılandır** sayfasında, kullanıcıların belirli SharePoint belge kitaplıklarında form işleme modelleri oluşturmasına izin vermek isteyip istemediğinizi seçebilirsiniz. Belge kitaplığı şeridinde, etkin olduğu SharePoint belge kitaplıklarında **form işleme modeli oluşturma** seçeneği sağlanacaktır.
 
     **Form işleme modeli oluşturma seçeneği hangi SharePoint kitaplıkları tarafından gösterilmelidir**? için şunları seçebilirsiniz:</br>
      - **Kuruluşunuzdaki tüm SharePoint kitaplıklarının** kullanımına açmak için tüm SharePoint sitelerindeki kitaplıklar.</br>
      - **Seçili SharePoint sitelerindeki kitaplıklar** ve kullanılabilir hale getirmek istediğiniz siteleri seçin veya en fazla 50 sitenin listesini karşıya yükleyin.</br>
      - Herhangi bir sitenin kullanımına açmak istemiyorsanız **SharePoint kitaplığı** yok (kurulumdan sonra bunu değiştirebilirsiniz).

   > [!div class="mx-imgBorder"]
   > ![Form işleme sitesi seçeneklerini yapılandırın.](../media/content-understanding/admin-configforms.png)

   > [!Note]
   > Site eklendikten sonra kaldırılması, sitedeki kitaplıklara uygulanan mevcut modelleri veya bir kitaplığa belge anlama modelleri uygulama özelliğini etkilemez. 
    
    Yapılandırılmış birden çok Power Platform ortamınız varsa, form işleme için hangisini kullanmak istediğinizi seçebilirsiniz. (Yalnızca bir ortamınız varsa bu seçenek görünmez.)

    ![Form işleme Power Platform seçeneklerini yapılandırın.](../media/content-understanding/setup-power-platform-env.png)

    **Power Platform ortamı** için şunları seçebilirsiniz:
    - Varsayılan Power Platform **ortamınızı** kullanmak için varsayılan ortamı kullanın.
    - **Özel ortam** kullanmak için özel bir ortam kullanın. Listeden kullanmak istediğiniz ortamı seçin. ([Özel ortam gereksinimlerine bakın](/microsoft-365/contentunderstanding/set-up-content-understanding#requirements)).

    **İleri**'ye tıklayın.

5. **İçerik Merkezi Oluştur** sayfasında, kullanıcılarınızın belge anlama modelleri oluşturup yönetebileceği bir SharePoint içerik merkezi sitesi oluşturabilirsiniz. Daha önce SharePoint yönetim merkezinden bir içerik merkezi oluşturduysanız, bu bilgiler burada görüntülenir ve **İleri'yi** seçebilirsiniz.

    1. **Site adı** alanına, içerik merkezi sitenize vermek istediğiniz adı yazın.
    
    1. **Site adresi**, site adı için seçtiklerinize bağlı olarak sitenizin URL'sini gösterir. Değiştirmek istiyorsanız **Düzenle'ye** tıklayın.

       > [!div class="mx-imgBorder"]
       > ![İçerik merkezi oluşturma.](../media/content-understanding/admin-cu-create-cc.png)</br>

       **İleri**'yi seçin.

6. **Gözden geçir ve bitir** sayfasında, seçtiğiniz ayara bakabilir ve değişiklik yapmayı seçebilirsiniz. Seçimlerinizden memnunsanız **Etkinleştir'i** seçin.

7. Onay sayfasında **Bitti'ye** tıklayın.

8. **Otomatik içerik anlama** sayfanıza geri dönersiniz. Bu sayfada **Yönet'i** seçerek yapılandırma ayarlarınızda herhangi bir değişiklik yapabilirsiniz. 

## <a name="assign-licenses"></a>Lisans atama

SharePoint Syntex yapılandırdıktan sonra, SharePoint Syntex özellikleri kullanacak kullanıcılara lisans atamanız gerekir.

Lisans atamak için:

1. Microsoft 365 yönetim merkezi, **Kullanıcılar'ın** altında <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**Etkin kullanıcılar'ı**</a> seçin.

2. Lisanslamak istediğiniz kullanıcıları seçin ve **Ürün lisanslarını yönet'i** seçin.

3. Açılan menüden **Uygulamalar'ı** seçin.

4. **SharePoint Syntex için uygulamaları göster'i** seçin. **Uygulamalar'ın** altında SharePoint Syntex, **SharePoint Syntex** ve **SharePoint Syntex - SPO türü** **için Common Data Service'in** seçili olduğundan emin olun.

    > [!div class="mx-imgBorder"]
    > ![Microsoft 365 yönetim merkezi lisansları SharePoint Syntex.](../media/content-understanding/sharepoint-syntex-licenses.png)

5. **Değişiklikleri kaydet**’e tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

[Form işleme modeline genel bakış](/ai-builder/form-processing-model-overview)

[Adım Adım: Belge Anlama Modeli Oluşturma (video)](https://www.youtube.com/watch?v=DymSHObD-bg)

[Power Platform yönetim merkezinde ortam oluşturma ve yönetme](/power-platform/admin/create-environment)
