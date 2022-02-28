---
title: Gözden geçirme kümesinden belgeleri dışarı aktarma
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
description: Bir gözden geçirme kümesinden sunular veya dış incelemeler Advanced eDiscovery içeriği seçmeyi ve dışarı aktarmayı öğrenin.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: dba9708bfda6d1b98a2861615e56518067822100
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984693"
---
# <a name="export-documents-from-a-review-set-in-advanced-ediscovery"></a>Belge kümesinde gözden geçirme kümesinden belgeleri Advanced eDiscovery

Dışarı Aktar, kullanıcıların Dosya Kitaplığı'daki bir gözden geçirme kümesinden belge dışarı aktarabilirsiniz ve bu pakette yer alan içeriği Advanced eDiscovery.

Gözden geçirme kümesinden belgeleri dışarı aktarma:

1. Görünüm Microsoft 365 uyumluluk merkezi büyük/Advanced eDiscovery açın, Gözden Geçir kümeleri sekmesini seçin ve sonra da dışarı  aktarma yapmak istediğiniz gözden geçirme kümesine tıklayın.

2. Gözden geçirme kümesinde **ActionExport'a** >  **tıklayın**.

   Dışarı Aktar aracı, dışarı aktarmayı yapılandırmak için ayarların olduğu dışarı aktarma sayfasını görüntüler. Bazı seçenekler varsayılan olarak seçilidir, ancak bunları değiştirebilirsiniz. Yapılandırabilirsiniz dışarı aktarma seçeneklerinin açıklamaları için aşağıdaki bölüme bakın.

   ![Gözden geçirme kümesinden öğe dışarı aktarmaya yönelik yapılandırma seçenekleri.](../media/bcfc72c7-4a01-4697-9e16-2965b7f04fdb.png)

3. Dışarı aktarmayı yapılandırdikten sonra, dışarı **aktarma işlemini başlatmak için** Dışarı Aktar'a tıklayın. Çıkış seçenekleri bölümünde seçtiğiniz seçen bilgilere bağlı olarak, dışarı aktarma dosyalarına doğrudan indirme veya kuruluşun Azure Depolama hesabıyla erişebilirsiniz.

> [!NOTE]
> Dışarı aktarma işleri, davanın ömrü boyunca korunur. Bununla birlikte, dışarı aktarma işi tamamlandıktan sonra 30 gün içinde dışarı aktarma işlerinden içeriği indirmeniz gerekir.

## <a name="export-options"></a>Dışarı aktarma seçenekleri

Dışarı aktarmayı yapılandırmak için aşağıdaki seçenekleri kullanın. BAZı çıkış seçenekleri için bazı çıkış seçeneklerine izin verilmez; en dikkati, PST biçimine dışarı aktarmada metin dosyalarını ve tam işlemli PDF'leri dışarı aktarmaya izin verilmez.

- **Dışarı aktarma** adı: Dışarı aktarma işinin adı. Bu, indirilecek ZIP dosyalarını isim etmek için kullanılır.

- **Açıklama**: Açıklama eklemek için ücretsiz metin alanı.

- **Bu belgeleri dışarı aktarma**

  - Yalnızca seçili belgeler: Bu seçenek yalnızca o anda seçili olan belgeleri dışarı aktarıyor. Bu seçenek yalnızca gözden geçirme kümesinde öğeler seçildiğinde kullanılabilir.
  
  - Tüm filtrelenmiş belgeler: Bu seçenek etkin bir filtrede yer alan belgeleri dışarı aktarıyor. Bu seçenek yalnızca gözden geçirme kümesine filtre uygulandığında kullanılabilir.
  
  - Gözden geçirme kümesinde yer alan tüm belgeler: Bu seçenek, gözden geçirme kümesinde yer alan tüm belgeleri dışarı aktarıyor.

- **Çıkış seçenekleri**: Dışarı aktarıldı içerik, web tarayıcısı aracılığıyla doğrudan indirilebilir veya bir Azure Depolama hesabına gönderebilirsiniz. İlk iki seçenek doğrudan indirmeyi etkinleştirir.
  
  - Yalnızca raporlar: Yalnızca özet ve yükleme dosyası oluşturulur.
  
  - Kayıp dosyalar ve PS'ler (e-posta, mümkün olduğunda PS'lere eklenir): Dosyalar, kullanıcıların yerel uygulamalarında görülen özgün dizin yapısına benzeyen bir biçimde dışarı aktarıldı.  Daha fazla bilgi için Serbest [dosyalar ve PST dışarı aktarma yapısı bölümüne](#loose-files-and-pst-export-structure) bakın.
  
  - Dizin yapısı: Dosyalar dışarı aktarıldı ve indirmeye dahil edildi.
  
  - Azure Depolama hesabınıza dışarı aktaran dizin yapısı: Dosyalar, kuruluşun Azure Depolama. Bu seçenek için, Azure posta hesabınıza kapsayıcının URL'sini Depolama dosyaları dışarı aktarmanız gerekir. Ayrıca, Azure Depolama hesabınız için paylaşılan erişim imzası (SAS) belirteci sağlamanız gerekir. Daha fazla bilgi için bkz[. Belgeleri Bir gözden geçirme kümesine Azure Depolama aktarma](download-export-jobs.md).

- **Dahil**
  
  - Etiketler: Seçildiğinde, etiketleme bilgileri yükleme dosyasına dahil edilir.
  
  - Metin dosyaları: Bu seçenek, dışarı aktarmada yerel dosyaların ayıklanan metin sürümlerini içerir.
  
  - Redacted natives'i dönüştürülmüş PDF'lerle değiştirme: Gözden geçirme sırasında redacted PDF dosyaları oluşturulursa, bu dosyalar dışarı aktarılamaz. Yalnızca yeniden işlem yapılan yerel dosyaları dışarı aktarmayı (bu seçeneği seçmeerek) veya gerçek redactions içeren PDF dosyalarını dışarı aktarmayı tercih etmek için bu seçeneği kullanabilirsiniz.

  - Tek tek sohbet iletileri yerine Konuşma PDF'leri: Sohbet konuşmalarını PDF dosyasında dışarı aktarabilirsiniz bu onay kutusunu seçin. Aynı konuşmadan gelen tüm sohbet iletileri aynı PDF dosyasında dışarı aktarıldı. Bu onay kutusunu seçilmemiş olarak bırakırsanız, sohbet görüşmesinde benzersiz her ileti tek başına bir öğe olarak dışarı aktarılacaktır. Dosya, posta kutusuyla aynı biçimde dışarı aktarıldı. Belirli bir konuşmada, birden çok .msg dosyası alırsınız.

Aşağıdaki bölümlerde, eksik dosyaların klasör yapısı ve dizin yapısı seçenekleri azaltıldı. Dışarı aktarmalar, sıkıştırılmamış içerik boyutu üst olarak 75 GB olan ZIP dosyalarında bölümlere ayrılmıştır. Dışarı aktarma boyutu 75 GB'den küçükse, dışarı aktarma bir özet dosyasından ve tek bir ZIP dosyasından oluşur. 75 GB'den büyük sıkıştırılmamış veriler dışarı aktarmalarda, birden çok ZIP dosyası oluşturulur. İndirdiğiniz ZIP dosyaları, tam dışarı aktarmayı yeniden oluşturmak için tek bir konuma sıkıştırılmamış olabilir.

### <a name="loose-files-and-pst-export-structure"></a>Dosya kayıplarının ve PST dışarı aktarma yapısı

Bu dışarı aktarma seçeneğini tercih ediyorsanız, dışarı aktaran içerik aşağıdaki yapıda düzenlenmiştir:

- Summary.csv: Gözden geçirme kümesinden dışarı aktarıldı içeriğin bir özetini içerir

- Kök klasör: [Dışarı Aktarma Adı] x / z.zip adlı bu klasör her ZIP dosyası bölümü için yinelenir.
  
  - Export_load_file_x: z.csv dosyası.
  
  - Uyarı ve hatalar x z.csv: Bu dosya, gözden geçirme kümesinden dışarı aktarmaya çalışırken karşılaşılan hatalar hakkında bilgi içerir.
  
  - Exchange: Bu klasör PST dosyalarında depolanan Exchange tüm içeriği içerir. Bu seçenekte, redacted PDF dosyaları ek kullanılamaz. Gözden geçirme kümesinde bir ek seçiliyse, ek iliştirilmiş olarak üst e-posta dışarı aktarıldı.
  
  - SharePoint: Bu klasör, dosya biçimindeki tüm yerel SharePoint yerel dosya biçiminde içerir. Bu seçenekte, redacted PDF dosyaları ek kullanılamaz.

### <a name="condensed-directory-structure"></a>Dizin yapısı sıkı

- Summary.csv: Gözden geçirme kümesinden dışarı aktarıldı içeriğin bir özetini içerir

- Kök klasör: [Dışarı Aktarma Adı] x / z.zip adlı bu klasör her ZIP dosyası bölümü için yinelenir.
  
  - Export_load_file_x z.csv: Meta veri dosyasıdır ve ZIP dosyasında depolanan her dosyanın konumunu da içerir.
  
  - Uyarı ve hatalar x z.csv: Bu dosya, gözden geçirme kümesinden dışarı aktarmaya çalışırken karşılaşılan hatalar hakkında bilgi içerir.

  - NativeFiles: Bu klasör, dışarı aktarıldı tüm yerel dosyaları içerir. Yerel dosyalar, *Redacted natives* dönüştüren PDF'lerle değiştir seçeneğini seçtiyseniz, yerel dosyalar kırmızı işlemli PDF'lerle değiştirilir.
  
  - Error_files: Bu klasörde ayıklama veya diğer işleme hatası olan dosyalar yer alır. Dosyalar, AyıklamaError veya İşlemeErroru gibi ayrı klasörlere yerleştirilir. Bu dosyalar yükleme dosyasında listelenir.

  - Extracted_text_files: Bu klasör, işlem sırasında oluşturulan tüm ayıklanan metin dosyalarını içerir.

### <a name="condensed-directory-structure-exported-to-your-azure-storage-account"></a>Azure Depolama Hesabınıza aktaran dizin Depolama.

Bu seçenek, Sıkıştırılmış dizin yapısıyla aynı genel yapıyı *kullanır, ancak* içerikler sıkıştırılır ve veriler Azure Depolama kaydedilir. Bu seçenek genellikle üçüncü taraf bir eBulma sağlayıcısıyla çalışırken kullanılır. Bu seçeneği kullanma hakkında ayrıntılı bilgi için bkz[. Gözden geçirme](download-export-jobs.md) için Azure Depolama.
