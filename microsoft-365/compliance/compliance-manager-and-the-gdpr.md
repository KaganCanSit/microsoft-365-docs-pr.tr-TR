---
title: Microsoft Uyumluluk Yöneticisi ve GDPR
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
ROBOTS: NOINDEX, NOFOLLOW
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Microsoft Uyumluluk Yöneticisi, Microsoft Hizmet Güveni Portalı'nın iş akışı tabanlı ücretsiz bir risk değerlendirme aracıdır. Uyumluluk Yöneticisi, Microsoft bulut hizmetleriyle ilgili mevzuata uygunluk etkinliklerini izlemenizi, atamanız ve doğrulamanız için olanak sağlar.
ms.openlocfilehash: b4a648c43fb20f557b85e24e9e67de036cc4f2e0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62984027"
---
# <a name="microsoft-compliance-manager-and-the-gdpr"></a>Microsoft Uyumluluk Yöneticisi ve GDPR

Avrupa Birliği tarafından yürürlüğe alınan Genel Veri Koruma Yönetmeliği (GDPR), Uyumluluk Yöneticisi'nde kullanılan kullanıcı ve müşteri bilgilerini yönetmek için uyumluluk stratejinizi ve vek veliye özel eylemlerinizi etkilemektedir.

## <a name="user-privacy-settings"></a>Kullanıcı Gizliliği ayarları

Bazı düzenlemeler, kuruluşun kullanıcı geçmişi verilerini sileme gerektirmektedir. Uyumluluk Yöneticisi, **yöneticilerin şunları Ayarlar** kullanıcı gizliliği ayarları işlevlerini sağlar:
  
- [Kullanıcı arama](#search-for-a-user)
- [Hesap veri geçmişinin raporunu dışarı aktarma](#export-a-report-of-account-data-history)
- [Kullanıcı veri geçmişini silme](#delete-user-data-history)
  
## <a name="search-for-a-user"></a>Kullanıcı arama

Kullanıcı hesabı aramak için:
  
1. Kullanıcı e-posta diğer adını (@ simgesinin sol bilgi) girin ve sağ tarafta yer alan etki alanı son ek listesinden etki alanı adını seçin. Birden çok kayıtlı etki alanına sahip kuruluşlarda, doğru olduğundan emin olmak için etki alanı adı son ekını bir kez daha denetleyin.

2. Kullanıcı adını doğru şekilde girdiyken Ara'ya **tıklayın**.

3. Döndürülen kullanıcı hesapları için sayfada Kullanıcı bulunamadı **görüntülenir**. Kullanıcının e-posta adresi bilgilerini kontrol edin ve gerekli düzeltmeleri yapın. Yeniden denemek için Ara'ya **seçin**.

4. Döndürülen kullanıcı hesapları için, düğme metni Ara'dan Temizle **olarak** **değişir**. Bu, döndürülen kullanıcı hesabının ek işlevlerin işletim bağlamı olduğunu ve bu işlevlerin bu kullanıcı hesabına uygulan olduğunu gösterir.

5. Arama sonuçlarını temizlemek ve farklı bir kullanıcı aramak için Temizle'yi **seçin**.

## <a name="export-a-report-of-account-data-history"></a>Hesap veri geçmişinin raporunu dışarı aktarma

Tanımlanan her kullanıcı hesabı için, hesaba bağlı bağımlılıkların bir raporunu oluşturabilirsiniz. Bu bilgiler, açık Eylem Öğeleri'nin yeniden atamasını sağlar veya önceden karşıya yüklenen kanıta erişimi sağlar.
  
 Rapor oluşturmak ve dışarı aktarma için:
  
1. Uyumluluk **Yöneticisi** denetimi Eylem Öğeleri'nin döndürülen kullanıcı hesabına atanmış durumdaki eylem öğelerinin ve bu kullanıcı tarafından karşıya yüklenen belgelerin listesini oluşturmak ve indirmek için Dışarı Aktar'ı seçin. Atanmış eylem veya karşıya yüklenen belge yoksa, bir hata iletisi "Bu kullanıcı için veri yok" hata iletisini görüntüler.

2. Rapor, etkin tarayıcı penceresinin arka planına indirilir. Tarayıcı indirme geçmişinizi kontrol etmek istediğiniz bir indirme açılan kutusu görmüyorsanız.

3. Rapor verilerini gözden geçirmek için belgeyi açın.

> [!IMPORTANT]
> Rapor verileri, Eylem Öğesi atama geçmişinde durum değişikliklerini görüntüleyen ve görüntüleyen geçmiş bir liste değildir. Oluşturulan rapor, raporun çalıştırıldığı zamanda atanan Eylem Öğeleri denetimin anlık görüntüsüdir (rapora tarih ve saat damgası yazılır). Örneğin, Eylem Öğeleri'nin sonraki tüm yeniden atamaları, rapor aynı kullanıcı için yeniden oluşturulsa farklı anlık görüntü raporu verilerine neden olur.
  
## <a name="delete-user-data-history"></a>Kullanıcı veri geçmişini silme

Döndürülen kullanıcıya atanan tüm denetim Eylem Öğelerini 'atanmamış' olarak ayarlar. Döndürülen kullanıcı **tarafından karşıya yüklenen** tüm belgeler için karşıya yüklenen değeri 'kullanıcı kaldırıldı' olarak ayarlar.
  
Kullanıcı hesabını silmek için Eylem Öğesi ve belge yükleme geçmişi:
  
1. **Sil'i seçin**.

    Bir onay iletişim kutusu görüntülenir: "*Bu, tüm denetim Eylem Öğesi atamalarını ve seçili kullanıcının belge karşıya yükleme geçmişini kaldırır. Bu eylem kalıcıdır. Devam etmek istediğinizden emin misiniz?"*

2. Devam etmek için **Tamam'ı seçin**, aksi takdirde **İptal'i seçin**.
