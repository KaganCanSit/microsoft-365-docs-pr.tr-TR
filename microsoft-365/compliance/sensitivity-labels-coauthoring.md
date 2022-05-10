---
title: Şifrelenmiş belgeler için birlikte yazmayı etkinleştirme
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
description: SharePoint ve OneDrive etiketlenmiş ve şifrelenmiş belgeler için masaüstü uygulamalarında birlikte yazma ve Otomatik Kaydetme'yi etkinleştiren bir ayarı açın.
ms.openlocfilehash: 72935a58931c1458466f145c17a9e423e6b6d31c
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/09/2022
ms.locfileid: "65287000"
---
# <a name="enable-co-authoring-for-files-encrypted-with-sensitivity-labels"></a>Duyarlılık etiketleriyle şifrelenmiş dosyalar için birlikte yazmayı etkinleştirme

>*[Güvenlik & uyumluluğu için lisanslama yönergelerini Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Belgeler [duyarlılık etiketleriyle](sensitivity-labels.md) etiketlendiğinde ve şifrelendiğinde birden çok kullanıcının aynı anda bu belgeleri düzenleyebilmesi için Office masaüstü uygulamaları için [birlikte yazmayı](https://support.office.com/article/ee1509b4-1f6e-401e-b04a-782d26f564a4) desteklemek üzere ayarı etkinleştirin.

Kiracınız için bu ayar etkinleştirilmeden, kullanıcılar Office masaüstü uygulamalarını kullandıklarında SharePoint veya OneDrive depolanan şifrelenmiş bir belgeyi kullanıma almalıdır. Sonuç olarak, gerçek zamanlı olarak işbirliği yapamazlar. Veya SharePoint [ve OneDrive Office dosyaları için duyarlılık etiketleri etkinleştirildiğinde Web üzerinde Office](sensitivity-labels-sharepoint-onedrive-files.md) kullanmalıdır.

Ayrıca, bu işlevselliğin etkinleştirilmesi, etiketlenmiş ve şifrelenmiş dosyalar için [Otomatik Kaydetme](https://support.office.com/article/what-is-autosave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5) işlevinin desteklenmesine neden olur.

Yayın duyurusunu okumak için [şifrelenmiş Microsoft Bilgi Koruması belgelerde birlikte yazma genel kullanıma sunuldu](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/co-authoring-on-microsoft-information-protection-encrypted/ba-p/2693718) blog gönderisine bakın.

## <a name="metadata-changes-for-sensitivity-labels"></a>Duyarlılık etiketleri için meta veri değişiklikleri

> [!IMPORTANT]
> Birlikte yazma ayarını etkinleştirdikten sonra, şifrelenmemiş dosyalar için etiketleme bilgileri artık özel özelliklere kaydedilmez.
> 
> Meta verileri eski konuma okuyan veya yazan herhangi bir uygulama, hizmet, betik veya araç kullanıyorsanız bu ayarı etkinleştirmeyin.

Office masaüstü uygulamaları için birlikte yazmayı desteklemek üzere ayarı etkinleştirmeden önce, bu eylemin Office dosyalarına kaydedilen ve dosyalardan okunan etiketleme meta verilerinde değişiklik yaptığını anlamanız önemlidir.

Etiketleme meta verileri, kiracınızı tanımlayan ve duyarlılık etiketi uygulanan bilgileri içerir. Bu ayarın yaptığı değişiklik, Word, Excel ve PowerPoint dosyalarının meta veri biçimi ve konumudur. Şifrelenmiş dosyalar için meta veri değişikliği geriye dönük olarak uyumlu olduğundan ve e-postalarda değişiklik olmadığından şifrelenmiş dosyalar veya e-postalar için herhangi bir işlem yapmanız gerekmez. Ancak, otomatik olarak yükseltilebilen ancak geriye dönük olarak uyumlu olmayan şifrelenmiş dosyalar için meta veri değişikliklerini bilmeniz gerekir.

Bu değişiklik hem yeni etiketlenmiş dosyaları hem de zaten etiketlenmiş dosyaları etkiler. Birlikte yazma ayarını destekleyen uygulama ve hizmetleri kullandığınızda:
- Yeni etiketlenen dosyalar için, etiketleme meta verileri için yalnızca yeni biçim ve konum kullanılır.
- Zaten etiketlenmiş dosyalar için, dosyanın bir sonraki açılıp kaydedilişinde, dosyada eski biçimde ve konumda meta veriler varsa, bu bilgiler yeni biçime ve konuma kopyalanır.

Bu meta veri değişikliği hakkında daha fazla bilgiyi aşağıdaki kaynaklardan okuyabilirsiniz:

- Blog gönderisi: [Microsoft Bilgi Koruması Meta Veri Depolama Yaklaşan Değişiklikler](https://techcommunity.microsoft.com/t5/microsoft-security-and/upcoming-changes-to-microsoft-information-protection-metadata/ba-p/1904418)

- Açık Belirtimler: [2.6.3 LabelInfo ve Özel Belge Özellikleri](/openspecs/office_file_formats/ms-offcrypto/13939de6-c833-44ab-b213-e0088bf02341)

Bu değişiklikler nedeniyle, kuruluşunuzda meta verileri eski konuma okuyan veya yazan uygulamalar, hizmetler, betikler veya araçlar varsa bu ayarı etkinleştirmeyin. Bunu yaparsanız, bazı örnek sonuçlar:

- Etiketli bir belge, kullanıcılara etiketsiz olarak görünür.

- Belge, kullanıcılara güncel olmayan bir etiket görüntüler.

- Başka bir kullanıcı yeni etiketleme meta verilerini desteklemeyen bir Office masaüstü uygulamasında açıksa, etiketlenmiş ve şifrelenmiş bir belge için birlikte yazma ve Otomatik Kaydetme çalışmaz. Dış kullanıcılar ve davet edilen konuklar dosya açıksa bu senaryonun kuruluşunuz dışındaki kullanıcılar için de gerçekleşebileceğini unutmayın.

- [Etiketleri Office eklerde özel özellikler olarak tanımlayan bir Exchange Online](/azure/information-protection/configure-exo-rules#example-2-rule-that-applies-the-encrypt-only-option-to-emails-when-they-have-attachments-that-are-labeled-confidential--partners-and-these-emails-are-sent-outside-the-organization) posta akışı kuralı e-postayı ve eki şifreleyemiyor veya yanlış şifreler.

Bu ayarı destekleyen uygulamaların ve hizmetlerin listesi ve etiketleme meta verisinde yapılan değişiklikler için aşağıdaki bölüme bakın.

## <a name="prerequisites"></a>Önkoşullar

Bu özelliği açmadan önce aşağıdaki önkoşulları anladığınızdan emin olun.

- Bu özelliği açmak için genel yönetici olmanız gerekir.

- Kiracı [için SharePoint ve OneDrive Office dosyaları](sensitivity-labels-sharepoint-onedrive-files.md) için duyarlılık etiketleri etkinleştirilmelidir. Bu özellik henüz etkinleştirilmemişse, duyarlılık etiketlerine sahip dosyalar için birlikte yazmayı açma ayarını seçtiğinizde otomatik olarak etkinleştirilir.

- Kurumlar için Microsoft 365 Uygulamaları:
    - **Windows**: Geçerli Kanal veya Aylık Enterprise Kanalı'ndan en düşük sürüm 2107 veya Semi-Annual Enterprise Kanalından en düşük sürüm 2202 (Önizleme)
    - **macOS**: En düşük sürüm 16.51
    - **iOS**: En düşük sürüm 2.58'i [kabul](#opt-in-to-the-preview-of-co-authoring-for-ios-and-android) ettiğinizde önizlemede
    - **Android**: En düşük sürüm 16.0.14931'i [kabul](#opt-in-to-the-preview-of-co-authoring-for-ios-and-android) ettiğinizde önizlemede

- Kiracınızdaki tüm uygulamalar, hizmetler ve işletimsel araçlar yeni [etiketleme meta verilerini](#metadata-changes-for-sensitivity-labels) desteklemelidir. Aşağıdakilerden birini kullanıyorsanız gereken en düşük sürümleri denetleyin:
    
    - **Azure Information Protection birleşik etiketleme istemcisi ve tarayıcısı:**
        - [Microsoft İndirme Merkezi'nden](https://www.microsoft.com/en-us/download/details.aspx?id=53018) yükleyebileceğiniz en düşük sürüm [2.12.62.0](/information-protection/rms-client/unifiedlabelingclient-version-release-history#version-212620)
    
    - **Windows veya macOS için OneDrive eşitleme uygulaması:**
        - En düşük 19.002.0121.0008 sürümü
    
    - **Uç nokta veri kaybı önleme (Uç Nokta DLP):**
        - KB 4601383 ile Windows 10 1809
        - KB 4601380 ile 1903 ve 1909 Windows 10
        - KB 4601382 ile Windows 10 2004
        - Windows 10 2004'ten sonraki Windows sürümleri KB güncelleştirmeleri olmadan desteklenir
    
    - **Microsoft Bilgi Koruması SDK'sını kullanan uygulamalar ve hizmetler:** 
        - En düşük 1.7 sürümü 

Microsoft 365 hizmetleri, bu özelliği açtığınızda yeni etiketleme meta verilerini otomatik olarak destekler. Örneğin:

- [Otomatik etiketleme ilkeleri](apply-sensitivity-label-automatically.md#how-to-configure-auto-labeling-policies-for-sharepoint-onedrive-and-exchange)
- [Duyarlılık etiketlerini koşul olarak kullanan DLP ilkeleri](dlp-sensitivity-label-as-condition.md)
- [duyarlılık etiketlerini uygulamak için yapılandırılmış Microsoft Defender for Cloud Apps](/cloud-app-security/best-practices#discover-classify-label-and-protect-regulated-and-sensitive-data-stored-in-the-cloud)

### <a name="opt-in-to-the-preview-of-co-authoring-for-ios-and-android"></a>iOS ve Android için birlikte yazma önizlemesine katılma

iOS ve Android için birlikte yazma önizlemesini denemek için, önceki bölümde belirtilen en düşük sürümlere sahip olmanız ve ayrıca kiracınızın önizlemeye eklenmesini istemeniz gerekir: [Mobil cihazlarda duyarlılık etiketleriyle şifrelenmiş dosyalar için birlikte yazmayı etkinleştirme onayı](https://ncv.microsoft.com/5Oob3oDj1O)

Daha fazla bilgi için şu blog gönderisi duyurusunu inceleyin: [Şifrelenmiş Microsoft Bilgi Koruması belgelerde birlikte yazma özelliği artık mobil cihazlarda genel önizleme aşamasındadır](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/co-authoring-on-microsoft-information-protection-encrypted/ba-p/3081369)

## <a name="limitations"></a>Sınırlamalar

Duyarlılık etiketleriyle şifrelenmiş dosyalar için birlikte yazma için kiracı ayarını etkinleştirmeden önce, bu özelliğin aşağıdaki sınırlamalarını anladığınızdan emin olun.

- [Etiketleme meta verileri değişiklikleri](#metadata-changes-for-sensitivity-labels) nedeniyle kiracınızdaki tüm uygulamalar, hizmetler ve işletimsel araçlar tutarlı ve güvenilir bir etiketleme deneyimi için yeni etiketleme meta verilerini desteklemelidir.
    
    Excel özgü: Birisi duyarlılık etiketleri için meta veri değişikliklerini desteklemeyen bir Excel sürümünü kullanarak dosyayı düzenler ve kaydederse, şifreleme uygulanmayan bir duyarlılık etiketine ait meta veriler dosyadan silinebilir.

- iOS ve Android için Office uygulamalarının desteklenmesi şu anda [önizleme](https://office.com/insider) aşamasındadır.

- Birlikte yazma ve Otomatik Kaydetme desteklenmez ve [şifreleme için aşağıdaki yapılandırmalardan](encryption-sensitivity-labels.md#configure-encryption-settings) herhangi birini kullanan etiketli ve şifrelenmiş Office belgelerde çalışmaz:
    - **Word, PowerPoint ve Excel'da etiket ve** onay kutusunu **uygularken kullanıcıların izinleri atamasına izin verin**. Bu yapılandırma bazen "kullanıcı tanımlı izinler" olarak adlandırılır.
    - **İçeriğe kullanıcı erişiminin süresi doluyor** , **Hiçbir Zaman** dışında bir değere ayarlanır.
    - **Çift Anahtar Şifrelemesi** seçildi.
    
    Bu şifreleme yapılandırmalarından herhangi birine sahip etiketler için etiketler Office uygulamalarında görüntülenir. Ancak, kullanıcılar bu etiketleri seçtiğinde ve belgeyi başka kimse düzenlemediğinde, birlikte yazma ve Otomatik Kaydetme'nin kullanılamayacağı konusunda uyarılırlar. Belgeyi başka biri düzenliyorsa, kullanıcılar etiketlerin uygulanamadığını belirten bir ileti görür.

- Azure Information Protection birleşik etiketleme istemcisini kullanıyorsanız: [Daha fazla gereksinim veya sınırlama](/azure/information-protection/known-issues#known-issues-for-co-authoring) için bu etiketleme istemcisinin belgelerine bakın. 
    > [!NOTE]
    > Birleştirilmiş etiketleme istemcisinin bu sınırlamaları, etiketleri seçen kullanıcılar için izin seçmelerini isteyen [bir iletişim kutusu değişikliği](/azure/information-protection/known-issues#user-interface-changes-when-applying-labels) içerir.

## <a name="how-to-enable-co-authoring-for-files-with-sensitivity-labels"></a>Duyarlılık etiketleri olan dosyalar için birlikte yazmayı etkinleştirme

> [!CAUTION]
> Bu ayarı açmak tek yönlü bir işlemdir. Yalnızca meta veri değişikliklerini, önkoşulları, sınırlamaları ve bu sayfada belgelenen bilinen sorunları okuduktan ve anladıktan sonra etkinleştirin.

Önizleme döneminde bu ayarı zaten açtıysanız başka bir eylem gerekmez ve bu yordamı atlayabilirsiniz.

1. [Microsoft Purview uyumluluk portalında](https://compliance.microsoft.com) kiracınız için genel yönetici olarak oturum açın.

2. Gezinti bölmesinde duyarlılık **dosyalarına sahip dosyalar için** **Ayarlar** >  Co-authoring öğesini seçin.

2. **Duyarlılık etiketleri olan dosyalar için birlikte yazma** sayfasında özet açıklamasını, önkoşulları, beklenmesi gerekenleri ve etkinleştirdikten sonra bu ayarı kapatamazsınız uyarısını okuyun.
    
    Ardından **Duyarlılık etiketleri olan dosyalar için birlikte yazmayı aç'ı** ve **Uygula'yı** seçin:
    
    ![Duyarlılık etiketleri olan dosyalar için birlikte yazmayı açma seçeneği.](../media/co-authoring-tenant-option-for-sensitivity-labels.png)

3. Birlikte yazma için bu yeni özelliği kullanmadan önce bu ayarın ortamınızda çoğaltılması için 24 saat bekleyin.

## <a name="contact-support-if-you-need-to-disable-this-feature"></a>Bu özelliği devre dışı bırakmanız gerekiyorsa Desteğe başvurun

> [!IMPORTANT]
> Bu özelliği devre dışı bırakmanız gerekiyorsa etiketleme bilgilerinin kaybolabileceğini unutmayın.

Kiracınız için duyarlılık etiketleri olan dosyalar için birlikte yazmayı etkinleştirdikten sonra, bu ayarı kendiniz devre dışı bırakamazsınız. Bu nedenle, bu ayarı etkinleştirmeden önce önkoşulları, sonuçları ve sınırlamaları denetlemeniz ve anlamanız çok önemlidir.

![Duyarlılık etiketleri için birlikte yazma özelliğinin açık olduğunu gösteren seçenek.](../media/co-authoring-tenant-option-set-for-sensitivity-labels.png)

Bu ayar açıkken ekran görüntüsünde gördüğünüz gibi[, Microsoft Desteği](../admin/get-help-support.md) iletişim kurabilir ve bu ayarın kapatılmasını isteyebilirsiniz. Bu istek birkaç gün sürebilir ve kiracınız için genel yönetici olduğunuzu kanıtlamanız gerekir. Her zamanki destek ücretlerinin uygulanmasını bekleyin. 

Bir destek mühendisi kiracınız için bu ayarı devre dışı bırakırsa:

- Yeni etiketleme meta verilerini destekleyen uygulamalar ve hizmetler artık etiketler okunduğunda veya kaydedildiğinde özgün meta veri biçimine ve konumuna geri döner.

- Ayar etkinken kullanılan Office belgelerin yeni meta veri biçimi ve konumu özgün biçime ve konuma kopyalanmaz. Sonuç olarak, şifrelenmemiş Word, Excel ve PowerPoint dosyaları için bu etiketleme bilgileri kaybolur.

- Birlikte yazma ve Otomatik Kaydetme artık kiracınızda etiketli ve şifrelenmiş belgeler için çalışmaz.

- Duyarlılık etiketleri OneDrive ve SharePoint Office dosyaları için etkin kalır.
