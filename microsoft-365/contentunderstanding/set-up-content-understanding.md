---
title: Ayarlama SharePoint Syntex
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
description: Ayarlama SharePoint Syntex
ms.openlocfilehash: 244038e4c49801cad59bd9cf8939c47291c5270f
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326951"
---
# <a name="set-up-sharepoint-syntex"></a>Ayarlama SharePoint Syntex

Yöneticiler bu Microsoft 365 yönetim merkezi Microsoft <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a> ayarlamak [için SharePoint Syntex](index.md). 

Başlamadan önce şunları göz önünde önünde yapın:

- Hangi SharePoint form işlemeyi etkinleştirecek? Bunların hepsi, bir bazıları veya belirli siteler?
- Varsayılan içerik merkezinizi nasıl isimlesiniz?

İlk kurulumdan sonra ayarlarınızı kurulumdan sonra <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a>.

Kurulumdan önce, ortamınıza içerik anını ayarlamanın ve yapılandırmanın en iyi yolunu planlamaya emin olun. Örneğin, aşağıdaki kararları alırsiniz:

- Form SharePoint etkinleştirmek istediğiniz tüm siteler, bazıları veya seçilen siteler gibi en son siteler
- İçerik merkezinizin adı ve yöneticileri

## <a name="requirements"></a>Gereksinimler 

> [!NOTE]
> Diğer kullanıcılara erişmek ve SharePoint için Genel yönetici veya Microsoft 365 yönetim merkezi izinlerine sahip SharePoint Syntex.

Yönetici olarak, kurulumdan sonra seçilen ayarları istediğiniz zaman ve genel ayarlarda içerik yönetim ayarlarını anlama genelinde <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Microsoft 365 yönetim merkezi</a>.

Özel bir Power Platform ortamı kullanmayı planlıyorsanız, form işleme modelleri oluşturamadan önce bu ortamda [*Cortex Projesi için AI Builder*](/power-platform/admin/manage-apps#install-an-app-in-the-environment-view) uygulamasını yüklemeniz ve [AI Builder](/power-platform/admin/capacity-add-on) kredisi ayırmanız gerekir.

### <a name="licensing"></a>Lisanslama

Bu SharePoint Syntex kullanmak için, kuruma abonelik SharePoint Syntex ve her kullanıcıya aşağıdaki lisansların atanmış olması gerekir:

- SharePoint Syntex
- SharePoint Syntex - SPO türü
- Veriler için Ortak Veri SharePoint Syntex

Form işlemeyi kullanmak için AI Builder kredisi de gerekir. 300 veya daha fazla lisanslı kullanıcınız varsa, her ay bir AI Builder kredisi tahsisi sağlanır.

Lisanslama hakkında SharePoint Syntex için [lisanslama SharePoint Syntex bakın](syntex-licensing.md)

## <a name="to-set-up-sharepoint-syntex"></a>Ayar yapmak SharePoint Syntex

1. İçerik <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**Microsoft 365 yönetim merkezi,Kurulum'u**</a> seçin ve dosyalar **ve içerik bölümünü** görüntüleme.

2. Dosyalar ve **içerik bölümünde İçeriğin** anlaşılmasını **otomatikleştir'i seçin**. Geçerli AI Builder kredi kullanılabilirliğinizin Bir bakışta bölümünde **gösterildiğini** unutmayın.<br/>

3. İçeriği anlama **işlemini otomatikleştirme** sayfasında, **Kurulum sürecini takip etmeye** başlama'ya tıklayın. <br/>

    > [!div class="mx-imgBorder"]
    > ![Kurulumu başlatın.](../media/content-understanding/admin-content-understanding-get-started.png)</br>

4. Form **İşlemeyi Yapılandır sayfasında**, kullanıcıların belirli veri kaynağında veya belge kitaplıklarında form işleme modelleri oluştur SharePoint seçebilirsiniz. Menü seçeneği, etkinleştirilen belge kitaplıklarında Form işleme **modeli** SharePoint seçeneğiyle belge kitaplığı şeridinde kullanılabilir.
 
     Hangi **SharePoint kitaplıkların form işleme modeli oluşturma seçeneğini göstermeleri gerekir**? seçeneği için:</br>
      - **Tüm sitelerde SharePoint kitaplıklar**; bunu tüm SharePoint kitaplıklarında kullanılabilir.</br>
      - **Seçili sitelerde SharePoint kitaplıklar** ve ardından içinde kullanılabilir yapmak istediğiniz siteleri seçin veya en çok 50 sitenin listesini karşıya yükleyin.</br>
      - **Hiçbir SharePoint tarafından** kullanılabilir yapmak istemiyorsanız, bu kitaplıkları değiştiremezsiniz (kurulumdan sonra bunu değiştirebilirsiniz).

   > [!div class="mx-imgBorder"]
   > ![Form işleme sitesi seçeneklerini yapılandırma.](../media/content-understanding/admin-configforms.png)

   > [!Note]
   > Site dahil edildikten sonra sitenin kaldırılması, bu sitenin kitaplıklarına uygulanan mevcut modelleri veya kitaplı kitaplara belge anlama modellerini uygulayabilme olanağını etkilemez. 
    
    Birden çok Power Platform ortamları yapılandırılmışsa, form işleme için hangisini kullanmak istediğinizi seçebilirsiniz. (Yalnızca bir ortamız varsa bu seçenek görünmez.)

    ![Form işleme Power Platform seçeneklerini yapılandırabilirsiniz.](../media/content-understanding/setup-power-platform-env.png)

    **Power Platform ortamı için** şunları seçin:
    - Varsayılan Power Platform **ortamınızı** kullanmak için varsayılan ortamı kullanın.
    - **Özel bir ortam kullanmak** için özel bir ortam kullanın. Listeden kullanmak istediğiniz ortamı seçin. ([Özel ortam gereksinimlerine bakın](/microsoft-365/contentunderstanding/set-up-content-understanding#requirements)).

    **İleri**'ye tıklayın.

5. İçerik **Merkezi Oluştur sayfasında**, kullanıcılarının belge anlama modellerini oluştur SharePoint yönetecekleri bir İçerik Merkezi sitesi oluşturabilirsiniz. Daha önce yönetim merkezinden bir içerik SharePoint, bu bilgiler burada görüntülenir ve Sonraki'yi seçmeniz **gerekir**.

    1. **Site adı olarak**, içerik merkezi sitenize vermek istediğiniz adı yazın.
    
    1. **Site adresi**, site adı için ne seçtiğinize bağlı olarak sitenizin URL'sini gösterir. Bu değişikliği yapmak için Düzenle'ye **tıklayın**.

       > [!div class="mx-imgBorder"]
       > ![İçerik merkezi oluşturma.](../media/content-understanding/admin-cu-create-cc.png)</br>

       **İleri**'yi seçin.

6. Gözden **Geçir ve bitiş sayfasında** , seçili ayarınıza bakıp değişiklik yapmak için seçim yapabilirsiniz. Seçimlerden memnunsanız Etkinleştir'i **seçin**.

7. Onay sayfasında Bitti'ye **tıklayın**.

8. İçeriği otomatikleştirme anlama **sayfanıza geri döndürülürsiniz** . Bu sayfada Yönet'i **seçerek** yapılandırma ayarlarınıza istediğiniz değişiklikleri yapabilirsiniz. 

## <a name="assign-licenses"></a>Lisans atama

SharePoint Syntex'i yapılandırdıktan sonra, bu özellikleri SharePoint Syntex atamanız gerekir.

Lisans atamak için:

1. Aşağıdaki Microsoft 365 yönetim merkezi altında Etkin <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**kullanıcılar'ı seçin**</a>.

2. Lisans eklemek istediğiniz kullanıcıları seçin ve Ürün lisanslarını **yönet'i seçin**.

3. Açılan **menüden** Uygulamalar'ı seçin.

4. Uygulamalar **için uygulamaları göster'i SharePoint Syntex**. **Uygulamalar'ın** altında, SPO, **SharePoint Syntex****, SharePoint Syntex** ve - **SharePoint Syntex için Ortak Veri Hizmeti'nin** seçili olduğundan emin olun.

    > [!div class="mx-imgBorder"]
    > ![SharePoint Syntex lisansları Microsoft 365 yönetim merkezi.](../media/content-understanding/sharepoint-syntex-licenses.png)

5. **Değişiklikleri kaydet**’e tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

[Form işleme modeline genel bakış](/ai-builder/form-processing-model-overview)

[Adım Adım: Belge Anlama Modeli Oluşturma (video)](https://www.youtube.com/watch?v=DymSHObD-bg)

[Power Platform yönetim merkezinde ortam oluşturma ve yönetme](/power-platform/admin/create-environment)
