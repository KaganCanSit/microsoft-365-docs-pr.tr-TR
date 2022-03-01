---
title: E-postada duyarlılık etiketleriyle şifrelenen belgeler için birlikte Microsoft 365
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
audience: Admin
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
ms.topic: article
description: Masaüstü uygulamalarda etiketli ve şifrelenmiş belgeler için masaüstü uygulamalarıyla birlikte yazma ve Otomatik Kaydetmeyi sağlayan ayarı SharePoint OneDrive.
ms.openlocfilehash: 8be6fc228a623f3a1f76efdf56354ba30beb9650
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63019445"
---
# <a name="enable-co-authoring-for-files-encrypted-with-sensitivity-labels"></a>Duyarlılık etiketleriyle şifrelenmiş dosyalar için birlikte yazma özelliği etkinleştirme

>*[Microsoft 365 uyumluluğu için lisans & kılavuzu.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance)*

Office masaüstü uygulamaları için birlikte [](https://support.office.com/article/ee1509b4-1f6e-401e-b04a-782d26f564a4) yazma desteği sağlayan ayarı etkinleştirin; böylelikle belgeler duyarlılık etiketleriyle etiketlenir ve şifrelenirken[, birden](sensitivity-labels.md) çok kullanıcı bu belgeleri aynı anda düzenleyebilir.

Kiracınız için bu ayar etkinleştirilmemişse, kullanıcıların Office masaüstü uygulamalarını kullanıyorken SharePoint veya OneDrive şifreli bir belgeyi Office gerekir. Sonuç olarak, gerçek zamanlı olarak işbirliği yap'lar. Duyarlılık etiketleri Web üzerinde Office ve Office dosyaları için [etkinleştirildiğinde](sensitivity-labels-sharepoint-onedrive-files.md) de SharePoint OneDrive.

Buna ek olarak, bu işlevselliğin etkinleştirilmesi, etiketli ve şifrelenmiş bu dosyalar için Otomatik Kaydetme işlevselliğinin de desteklenmesini sağlar.[](https://support.office.com/article/what-is-autosave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5)

Sürüm duyurularını okumak için, Şifrelenmiş belgeler artık genel kullanıma Microsoft Bilgi Koruması [birlikte yazma blog gönderisi'ne bakın](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/co-authoring-on-microsoft-information-protection-encrypted/ba-p/2693718).

## <a name="metadata-changes-for-sensitivity-labels"></a>Duyarlılık etiketleri için meta veri değişiklikleri

> [!IMPORTANT]
> Birlikte yazma ayarını etkinleştirdikten sonra, şifrelenmemiş dosyaların etiket bilgileri artık özel özelliklerde kayıtlı olmaz.
> 
> Meta verileri eski konuma etiketleen veya yazan uygulamalar, hizmetler, betikler veya araçlardan birini kullanıyorsanız, bu ayarı etkinleştirmeyin.

Office masaüstü uygulamaları için birlikte yazma desteği sağlayan ayarı etkinleştirmeden önce, bu eylemin, Office dosyalarına kaydedilen ve bu dosyalardan okunan etiket meta verisinde değişiklikler yapanı Office önemlidir.

Etiket meta verileri kiracınızı tanımlayan ve duyarlılık etiketinin uygulandığı bilgileri içerir. Bu ayarın 2013'e göre meta veri biçimi ve konumu, Word, Excel ve dosya PowerPoint olur. Şifreli dosyalar veya e-postalar için herhangi bir işlem yapmasanız; Şifrelenmiş dosyaların meta veri değişikliği geriye doğru uyumludur ve e-postalarda hiçbir değişiklik yoktur. Öte yandan, şifrelenmiş dosyaların otomatik olarak yükseltilse de geriye doğru uyumlu olmayan meta veri değişikliklerini de biliyor olmak gerekir.

Bu değişiklik hem yeni etiketli dosyaları hem de önceden etiketlenmiş dosyaları etkiler. Birlikte yazma ayarını destekleyen uygulamaları ve hizmetleri kullanıyorsanız:
- Yeni etiketlenen dosyalar için, meta verileri etiketlemek için yalnızca yeni biçim ve konum kullanılır.
- Zaten etiketlenmiş olan dosyalar için, dosya bir sonraki açılabilir ve kaydedkisinde, dosyada eski biçimde ve konumda meta veriler varsa, yeni biçim ve konuma kopyalanır.

Bu meta veri değişikliği hakkında aşağıdaki kaynaklardan daha fazla bilgi okuyabilirsiniz:

- Blog gönderisi: [Meta Veri Kaynağında Microsoft Bilgi Koruması Değişiklikler Depolama](https://techcommunity.microsoft.com/t5/microsoft-security-and/upcoming-changes-to-microsoft-information-protection-metadata/ba-p/1904418)

- Açık Belirtimler: [2.6.3 EtiketBilgisi ve Özel Belge Özellikleri](/openspecs/office_file_formats/ms-offcrypto/13939de6-c833-44ab-b213-e0088bf02341)

Bu değişiklikler nedeniyle, kuruluşta meta verileri eski konuma etiketleyeni veya yazan uygulamalarınız, hizmetleriniz, betikleriniz veya araçlarınız varsa, bu ayarı etkinleştirmeyebilirsiniz. Bunu biliyorsanız, bazı örnek sonuçlar:

- Etiketli bir belge etiketsiz olarak kullanıcılara görünür.

- Belgede kullanıcılara güncel olmayan etiket görüntülenir.

- Başka bir kullanıcı belgeyi yeni etiket meta verilerini desteklemeen bir Office masaüstü uygulamasında açtısa, birlikte yazma ve Otomatik Kaydetme özelliği etiketli ve şifrelenmiş belgelerde kullanılamaz. Dış kullanıcılar ve davet edilen konuklar dosyayı açtısa, bu senaryonun, kuruluş dışındaki kullanıcılar için de oluşabilir.

- Eklerin Exchange Online özellikler olarak tanımlayan bir posta akışı [kuralı Office e-postayı](/azure/information-protection/configure-exo-rules#example-2-rule-that-applies-the-encrypt-only-option-to-emails-when-they-have-attachments-that-are-labeled-confidential--partners-and-these-emails-are-sent-outside-the-organization) ve eki şifreleyemezse veya yanlış şekilde şifreler.

Bu ayarı destekleyen uygulama ve hizmetlerin listesi ve etiket meta verilerinde yapılan değişiklikler için aşağıdaki bölüme bakın.

## <a name="prerequisites"></a>Önkoşullar

> [!IMPORTANT]
> Bu özellik, tüm kullanıcıların e-posta Kurumlar için Microsoft 365 Uygulamaları. Bu birlikte yazma özelliği için destek, daha fazla güncelleştirme Semi-Annual Enterprise Kanalı'Office sunulmaktadır. Bu güncelleştirme kanalını Office kullanıyorsanız bunu Güncel Kanal veya Aylık Kanal olarak Enterprise.
> 
> Daha fazla bilgi için bkz [. Güncelleştirme kanallarını yapılandırma ve yönetme](/deployoffice/overview-update-channels#how-to-configure-and-manage-update-channels).

Bu özelliği açmadan önce aşağıdaki önkoşulları anlıyoruz.

- Bu özelliği açmak için genel yönetici üyesi olmak gerekir.

- Kiracı için, adres [ve Office dosyalarında SharePoint OneDrive](sensitivity-labels-sharepoint-onedrive-files.md) etiketlerinin etkinleştirilmesi gerekir. Bu özellik daha önce etkinleştirilmemişse, duyarlılık etiketleri olan dosyalar için birlikte yazma özelliğinin etkinleştirilmesi ayarını seçerek otomatik olarak etkinleştirilir.

- Kurumlar için Microsoft 365 Uygulamaları:
    - **Windows**: Güncel Kanal'dan En Az 2107 veya Aylık Kanaldan Enterprise.
    - **macOS**: En az sürüm 16.51
    - **iOS**: Henüz desteklenmiyor
    - **Android**: Henüz desteklenmiyor

- Kiracınıza gelen tüm uygulamalar, hizmetler ve işlem araçları yeni etiket meta [verilerini desteklemeli](#metadata-changes-for-sensitivity-labels). Aşağıdaki sürümlerden herhangi birini kullanıyorsanız, gerekli en düşük sürümleri kontrol edin:
    
    - **Azure Information Protection birleşik etiketleme istemcisi ve tarayıcısı:**
        - Microsoft İndirme [Merkezi'nden yük88.12.62.0](/information-protection/rms-client/unifiedlabelingclient-version-release-history#version-212620) [sürümünün en düşük sürümü](https://www.microsoft.com/en-us/download/details.aspx?id=53018)
    
    - **OneDrive eşitleme macOS veya Windows için bir uygulama:**
        - Minimum 19.002.0121.0008 sürümü
    
    - **Uç nokta veri kaybını önleme (Uç Nokta DLP):**
        - KB Windows 10 1809'a 4601383
        - Windows 10 KB-1903 ve 1909 4601380
        - KB Windows 10 2004 ile 4601382
        - Windows 2004'Windows 10 sonraki sürümler KB güncelleştirmeleri olmadan desteklene
    
    - **Microsoft Bilgi Koruması SDK'yı kullanan uygulamalar Microsoft Bilgi Koruması:** 
        - Minimum 1,7 sürümü 

Microsoft 365 özellik açılırken hizmetler yeni etiket meta verilerini otomatik olarak destekler. Örneğin:

- [Otomatik etiketleme ilkeleri](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange)
- [Duyarlılık etiketlerini koşullar olarak kullanan DLP ilkeleri](dlp-sensitivity-label-as-condition.md)
- [Duyarlılık etiketleri uygulamak üzere yapılandırılmış Bulut Uygulamaları için Microsoft Defender](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)

## <a name="limitations"></a>Sınırlamalar

Duyarlılık etiketleriyle şifrelenmiş dosyalar için kiracı ayarını etkinleştirmeden önce, bu özelliğin aşağıdaki sınırlamalarını anlamış olun.

- Meta veri [etiket değişiklikleri nedeniyle](#metadata-changes-for-sensitivity-labels), kiracınıza gelen tüm uygulamalar, hizmetler ve işlem araçları tutarlı ve güvenilir bir etiketleme deneyimi için yeni meta verileri etiketlemeyi desteklemesi gerekir.
    
    Excel'a özgü: Şifreleme uygulamaz bir duyarlılık etiketi için meta veriler, birisi dosyayı düzenler ve kaydederse Excel'in duyarlılık etiketleri için meta veri değişikliklerini desteklememiş bir sürümü kullanarak dosyadan silinebilir.

- Office Android ve iOS için uygulama uygulamaları şu anda desteklenmiyor.

- Birlikte yazma ve Otomatik Kaydetme desteklenmemektedir ve şifreleme için aşağıdaki yapılandırmalardan herhangi birini kullanan etiketli ve Office belgelerde [kullanılamaz](encryption-sensitivity-labels.md#configure-encryption-settings):
    - **Word,** PowerPoint ve Excel'da etiket ve onay kutusunu uygulayan kullanıcıların izin atamasına izin verin. PowerPoint onay **kutusunun seçili olduğunu** belirtin. Bu yapılandırma bazen "kullanıcı tanımlı izinler" olarak da adlandırılır.
    - **kullanıcının içeriğe erişiminin süresi hiçbir** zaman'dan farklı bir değere **ayarlanır**.
    - **Çift Anahtar Şifrelemesi** seçilidir.
    
    Bu şifreleme yapılandırmalarının herhangi birini içeren etiketler için, etiketler Office görüntülenir. Bununla birlikte, kullanıcılar bu etiketleri seçer ve belgeyi başka kimse düzenlemezken, birlikte yazma ve Otomatik Kaydetme özelliğinin kullanılamaz olduğu uyarısıyla uyarıldı. Başka biri belgeyi düzenliyorsa, kullanıcılar etiketlerin uygulana olmadığını haber içeren bir ileti görebilir.

- Azure Information Protection birleşik etiketleme istemcisini kullanıyorsanız: Daha fazla gereksinimler veya sınırlamalar için bu etiket istemcisinin [belgelerini inceleyin](/azure/information-protection/known-issues#known-issues-for-co-authoring). 
    > [!NOTE]
    > Birleştirilmiş etiket istemcisinin bu sınırlandırmaları, izinleri [seçmelerini](/azure/information-protection/known-issues#user-interface-changes-when-applying-labels) isteyen etiketler seçen kullanıcılar için bir iletişim kutusunun değişikliğini içerir.

## <a name="how-to-enable-co-authoring-for-files-with-sensitivity-labels"></a>Duyarlılık etiketleri olan dosyalar için birlikte yazma nasıl etkinleştir kullanılır?

> [!CAUTION]
> Bu ayarın açması tek yolli bir eylemdir. Bunu yalnızca bu sayfada belgelenmiş meta veri değişikliklerini, önkoşulları, sınırlamaları ve bilinen sorunları okuyun ve anladıktan sonra etkinleştirin.

Önizleme süresi boyunca bu ayarı zaten etkinleştirirseniz başka işlem gerekmez ve bu yordamı atlayabilirsiniz.

1. Kiracınız için [genel Microsoft 365 uyumluluk merkezi](https://compliance.microsoft.com) olarak kiracıda oturum açma.

2. Gezinti bölmesinde, Duyarlılık **Ayarlar** >  **Dosyalar için yazma'ya tıklayın**.

2. Duyarlılık etiketleri **olan** dosyalar için birlikte yazma sayfasında, özet açıklamasını, önkoşulları, neler beklemeniz gerekir ve bu ayarı siz açtıktan sonra kapatılamay uyarılarını okuyun.
    
    Ardından, **Duyarlılık etiketleri olan dosyalar için birlikte yazmayı aç'ı seçin ve** **Uygula:**
    
    ![Duyarlılık etiketleri olan dosyalar için birlikte yazma seçeneğini açma seçeneği.](../media/co-authoring-tenant-option-for-sensitivity-labels.png)

3. Birlikte yazma için bu yeni özelliği kullanmadan önce, bu ayarın ortamınız genelinde çoğaltılması için 24 saat bekleyin.

## <a name="contact-support-if-you-need-to-disable-this-feature"></a>Bu özelliği devre dışı bırakmanız gerekirse Destek'e başvurun

> [!IMPORTANT]
> Bu özelliği devre dışı bırakmanız gerekirse etiket bilgilerini kaybetmeyi dikkat edin.

Kiracınız için duyarlılık etiketleri olan dosyalar için birlikte yazma özelliğini etkinleştirdikten sonra, bu ayarı kendiniz devre dışı bırakamazsanız. İşte bu nedenle, bu ayarı etkinleştirmeden önce önkoşulları, sonuçları ve sınırlamaları denetlemeniz ve anlamanız çok önemlidir.

![Duyarlılık etiketleri için birlikte yazma seçeneğinin açık olduğunu gösterir.](../media/co-authoring-tenant-option-set-for-sensitivity-labels.png)

Bu ayar açıkken ekran görüntüsünde gördüğünüz gibi, [Microsoft](../admin/get-help-support.md) Desteği'ne başvurarak bu ayarı kapatmak için istekte bulundurabilirsiniz. Bu istek birkaç gün kadar zaman al götürseniz de, kiracınız için genel yönetici olduğunu kanıtlamanız gerekir. Her zamanki destek ücretlerini uygulayabilirsiniz. 

Bir destek mühendisi kiracınız için bu ayarı devre dışı bırakırsa:

- Yeni etiket meta verilerini destekleyen uygulamalar ve hizmetler için, artık etiketler okundu veya kaydedili olduğunda özgün meta veri biçimine ve konumuna geri dönerler.

- Ayar etkin durumdayken kullanılan Office belgeler için yeni meta veri biçimi ve konumu özgün biçim ve konuma kopyalanmaz. Sonuç olarak, şifrelenmemiş Word, Excel ve PowerPoint bilgileri kaybolur.

- Birlikte yazma ve Otomatik Kaydetme, etiketli ve şifrelenmiş belgeler için artık kiracınız üzerinde çalışmıyor.

- Duyarlılık etiketleri OneDrive ve Office dosyaları için etkin SharePoint.
