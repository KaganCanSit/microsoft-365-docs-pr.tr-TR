---
title: Bir inceleme setinden belgeleri dışa aktarma
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
description: Sunular veya dış incelemeler için eBulma (Premium) gözden geçirme kümesinden içerik seçmeyi ve dışarı aktarmayı öğrenin.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: a2cc2b5f528c7573c255e05cea4b512416711462
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65096974"
---
# <a name="export-documents-from-a-review-set-in-ediscovery-premium"></a>eBulma'da (Premium) bir gözden geçirme kümesinden belgeleri dışarı aktarma

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Dışarı aktarma, eBulma(Premium) içindeki bir gözden geçirme kümesinden belgeyi dışarı aktardığınızda kullanıcıların indirme paketine dahil edilen içeriği özelleştirmesine olanak tanır.

Gözden geçirme kümesindeki belgeleri dışarı aktarmak için:

1. Microsoft Purview uyumluluk portalında eBulma (Premium) servis talebini açın, **Gözden geçirme kümeleri** sekmesini seçin ve ardından dışarı aktarmak istediğiniz gözden geçirme kümesini seçin.

2. Gözden geçirme kümesinde **ActionExport'a** >  tıklayın.

   Dışarı Aktarma aracı, dışarı aktarmayı yapılandırma ayarlarıyla birlikte açılır sayfayı görüntüler. Bazı seçenekler varsayılan olarak seçilidir, ancak bunları değiştirebilirsiniz. Yapılandırabileceğiniz dışarı aktarma seçeneklerinin açıklamaları için aşağıdaki bölüme bakın.

   ![Gözden geçirme kümesindeki öğeleri dışarı aktarmak için yapılandırma seçenekleri.](../media/bcfc72c7-4a01-4697-9e16-2965b7f04fdb.png)

3. Dışarı aktarmayı yapılandırdıktan sonra dışarı aktarma işlemini başlatmak için **Dışarı Aktar'a** tıklayın. **Çıkış seçenekleri** bölümünde seçtiğiniz seçeneğe bağlı olarak, dışarı aktarma dosyalarına doğrudan indirme yoluyla veya kuruluşunuzun Azure Depolama hesabından erişebilirsiniz.

> [!NOTE]
> Dışarı aktarma işleri, servis talebinin ömrü boyunca saklanır. Ancak, dışarı aktarma işi tamamlandıktan sonraki 30 gün içinde bir dışarı aktarma işinden içeriği indirmeniz gerekir.

## <a name="export-options"></a>Dışarı aktarma seçenekleri

Dışarı aktarmayı yapılandırmak için aşağıdaki seçenekleri kullanın. Bazı çıkış seçenekleri için tüm seçeneklere izin verilmez; en önemlisi, PST biçimine dışarı aktarma sırasında metin dosyalarının ve redakte edilmiş PDF'lerin dışarı aktarılmalarına izin verilmez.

- **Dışarı aktarma adı**: Dışarı aktarma işinin adı. Bu, indirilecek ZIP dosyalarını adlandırmak için kullanılır.

- **Açıklama**: Açıklama eklemeniz için serbest metin alanı.

- **Bu belgeleri dışarı aktar**

  - Yalnızca seçili belgeler: Bu seçenek yalnızca seçili durumdaki belgeleri dışarı aktarır. Bu seçenek yalnızca bir gözden geçirme kümesinde öğeler seçildiğinde kullanılabilir.
  
  - Tüm filtrelenmiş belgeler: Bu seçenek, etkin bir filtredeki belgeleri dışarı aktarır. Bu seçenek yalnızca gözden geçirme kümesine filtre uygulandığında kullanılabilir.
  
  - Gözden geçirme kümesindeki tüm belgeler: Bu seçenek, gözden geçirme kümesindeki tüm belgeleri dışarı aktarır.

- **Çıkış seçenekleri**: Dışarı aktarılan içerik doğrudan bir web tarayıcısı üzerinden indirilebilir veya bir Azure Depolama hesabına gönderilebilir. İlk iki seçenek doğrudan indirmeyi etkinleştirir.
  
  - Yalnızca raporlar: Yalnızca özet ve yükleme dosyası oluşturulur.
  
  - Gevşek dosyalar ve PST'ler (mümkün olduğunda PST'lere e-posta eklenir): Dosyalar, yerel uygulamalarında kullanıcılar tarafından görülen özgün dizin yapısına benzeyen bir biçimde dışarı aktarılır.  Daha fazla bilgi için [Gevşek dosyalar ve PST dışarı aktarma yapısı](#loose-files-and-pst-export-structure) bölümüne bakın.
  
  - Sıkıştırılmış dizin yapısı: Dosyalar dışarı aktarılır ve indirmeye dahil edilir.
  
  - Azure Depolama hesabınıza aktarılan sıkıştırılmış dizin yapısı: Dosyalar kuruluşunuzun Azure Depolama hesabına aktarılır. Bu seçenek için, dosyaları dışarı aktarmak için Azure Depolama hesabınızdaki kapsayıcının URL'sini sağlamanız gerekir. Azure Depolama hesabınız için paylaşılan erişim imzası (SAS) belirtecini de sağlamanız gerekir. Daha fazla bilgi için bkz. [Gözden geçirme kümesindeki belgeleri Azure Depolama hesabına](download-export-jobs.md) aktarma.

- **Içerir**
  
  - Etiketler: Seçildiğinde, etiketleme bilgileri yük dosyasına eklenir.
  
  - Metin dosyaları: Bu seçenek, dışarı aktarma işlemindeki yerel dosyaların ayıklanan metin sürümlerini içerir.
  
  - Yeniden düzenlenen yerel dosyaları dönüştürülen PDF'lerle değiştirin: Gözden geçirme sırasında yeniden düzenlenen PDF dosyaları oluşturulursa, bu dosyalar dışarı aktarma için kullanılabilir. Yalnızca yeniden işlem yapılmış yerel dosyaları dışarı aktarmayı seçebilir (bu seçeneği belirtmeyerek) veya gerçek redaksiyonları içeren PDF dosyalarını dışarı aktarmak için bu seçeneği belirleyebilirsiniz.

  - Tek tek sohbet iletileri yerine konuşma PDF'leri: Sohbet konuşmalarını PDF dosyasında dışarı aktarmak için bu onay kutusunu seçin. Aynı konuşmadaki tüm sohbet iletileri aynı PDF dosyasında dışarı aktarılır. Bu onay kutusunu seçili olarak bırakırsanız, sohbet konuşmasında yer alan her benzersiz ileti tek başına bir öğe olarak dışarı aktarılır. Dosya, posta kutusuna kaydedildiği biçimde dışarı aktarılır. Belirli bir konuşma için birden çok .msg dosyası alırsınız.

Aşağıdaki bölümlerde gevşek dosyalar için klasör yapısı ve sıkıştırılmış dizin yapısı seçenekleri açıklanmaktadır. Dışarı aktarmalar, sıkıştırılmamış içerik boyutu üst sınırı 75 GB olan ZIP dosyalarına bölümlenir. Dışarı aktarma boyutu 75 GB'tan küçükse, dışarı aktarma işlemi bir özet dosyadan ve tek bir ZIP dosyasından oluşur. 75 GB'tan büyük sıkıştırılmamış veri dışarı aktarma işlemleri için birden çok ZIP dosyası oluşturulur. İndirildikten sonra, zip dosyaları tek bir konuma sıkıştırılabilir ve tam dışarı aktarmayı yeniden oluşturabilir.

### <a name="loose-files-and-pst-export-structure"></a>Gevşek dosyalar ve PST dışarı aktarma yapısı

Bu dışarı aktarma seçeneğini seçerseniz, dışarı aktarılan içerik aşağıdaki yapıda düzenlenir:

- Summary.csv: Gözden geçirme kümesinden dışarı aktarılan içeriğin özetini içerir

- Kök klasör: z.zip [Dışarı Aktarma Adı] x adlı bu klasör ve her ZIP dosyası bölümü için yinelenecektir. Kök klasör aşağıdakileri içerir:
  
  - z.csv Export_load_file_x: Meta veri dosyası.
  
  - Uyarılar ve hatalar x / z.csv: Bu dosya, gözden geçirme kümesinden dışarı aktarmaya çalışırken karşılaşılan hatalar hakkında bilgi içerir.
  
  - Exchange: Bu klasör, PST dosyalarında depolanan Exchange tüm içeriği içerir. Redakte edilmiş PDF dosyaları bu seçeneğe eklenemez. Gözden geçirme kümesinde bir ek seçilirse, üst e-posta iletisi ek eklenmiş olarak dışarı aktarılır.
  
    Exchange klasörü, aşağıdaki öğeleri içeren mailboxname_loosefiles.zip adlı bir alt klasör de içerebilir:

    - Kodu çözülen Bilgi Hakları Yönetimi (IRM) korumalı iletileri.
    - Hata düzeltilmiş iletiler.
    - İletilerde başvuruda bulunan modern ekler veya bağlantılar.
    - Şifrelenmiş öğeler (Exchange klasöründeki PST dosyalarına dahil değildir).
  
  - SharePoint: Bu klasör, SharePoint yerel dosya biçimindeki tüm yerel içeriği içerir. Redakte edilmiş PDF dosyaları bu seçeneğe eklenemez.

### <a name="condensed-directory-structure"></a>Sıkıştırılmış dizin yapısı

- Summary.csv: Gözden geçirme kümesinden dışarı aktarılan içeriğin özetini içerir

- Kök klasör: z.zip [Dışarı Aktarma Adı] x adlı bu klasör ve her ZIP dosyası bölümü için yinelenecektir.
  
  - z.csv Export_load_file_x: Meta veri dosyası ve ayrıca ZIP dosyasında depolanan her dosyanın konumunu içerir.
  
  - Uyarılar ve hatalar x / z.csv: Bu dosya, gözden geçirme kümesinden dışarı aktarmaya çalışırken karşılaşılan hatalar hakkında bilgi içerir.

  - NativeFiles: Bu klasör dışarı aktarılan tüm yerel dosyaları içerir. Yeniden yapılandırılmış yerel öğeleri dönüştürülen PDF'lerle değiştir seçeneğini belirlediyseniz yerel dosyalar, yeniden *yapılandırılmış PDF'lerle* değiştirilir.
  
  - Error_files: Bu klasör, ayıklama veya başka bir işleme hatası olan dosyaları içerir. Dosyalar, ExtractionError veya ProcessingError gibi ayrı klasörlere yerleştirilir. Bu dosyalar yük dosyasında listelenir.

  - Extracted_text_files: Bu klasör, işlenirken oluşturulan ayıklanan tüm metin dosyalarını içerir.

### <a name="condensed-directory-structure-exported-to-your-azure-storage-account"></a>Azure Depolama Hesabınıza dışarı aktarılan sıkıştırılmış dizin yapısı

Bu seçenek *, Sıkıştırılmış dizin yapısıyla aynı genel yapıyı* kullanır, ancak içerik sıkıştırmaz ve veriler Azure Depolama hesabınıza kaydedilir. Bu seçenek genellikle üçüncü taraf bir eBulma sağlayıcısıyla çalışırken kullanılır. Bu seçeneğin nasıl kullanılacağı hakkında ayrıntılı bilgi için bkz. [Belgeleri Azure Depolama hesabına ayarlanmış bir gözden geçirmede](download-export-jobs.md) dışarı aktarma.
