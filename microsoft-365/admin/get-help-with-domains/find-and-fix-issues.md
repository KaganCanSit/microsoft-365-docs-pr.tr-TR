---
title: Kendi etki alanınızı veya DNS kayıtlarınızı ekledikten sonra sorunları bulma ve düzeltme
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 40398b0b-bdd0-4afd-ab5e-b5ae6b7990bf
description: Özel bir etki alanını ayarlarken DNS kayıtlarının doğru şekilde ayar olduğundan emin olarak, içinde bu sorunları çözebilirsiniz.
ms.openlocfilehash: 7fa5a18ff0e4b7f0db8749f5659fefdd89cb3fcd
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63316891"
---
# <a name="find-and-fix-issues-after-adding-your-domain-or-dns-records"></a>Kendi etki alanınızı veya DNS kayıtlarınızı ekledikten sonra sorunları bulma ve düzeltme

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**. 
  
Etki alanlarınızı bu etki alanıyla çalışmak Microsoft 365 zor olabilir. DNS sistemiyle çalışmak oldukça zordur ve etki alanınız için DNS kurulumu, e-posta gibi önemli iş etkinliklerinizi etkileyebilir!

> [!NOTE]
> Durumunu kontrol ederek etki alanınız ile ilgili sorunları kontrol edin. **SetupDomains'e**  >  gidin ve Durum sütununda bildirimleri görüntüleme. Bir sorun görüyorsanız, üç noktayı (diğer eylemler) ve ardından Durumu kontrol **edin'i seçin**. Açılan bölme, etki alanınıza ilişkin sorunları açıklar.
  
## <a name="whats-going-on"></a>Ne var ne yok?

- [Etki alanınızı doğrulayasınız mı?](#cant-verify-your-domain)
    
- [Outlook çalışmıyor mu?](#outlook-isnt-working)
    
- [Herkesin e-postası E-posta Microsoft 365 siz yalnızca E-postanız'ın geçişini istediniz mi?](#everyones-email-got-switched-to-microsoft-365-and-you-only-wanted-your-email-to-switch)

- [Kar amacı gütmeyen veya okul hesabı durumunu doğrulaya mısınız?](#cant-confirm-non-profit-or-school-account-status)

- [Etki alanınız ile hizmet çalışmıyor mu?](#services-not-working-with-your-domain)
    
- [Web sitenize erişirken sorun mu var?](#accessing-your-website-isnt-working)

## <a name="cant-verify-your-domain"></a>Etki alanınızı doğrulayamıyor musunuz?

Etki alanı doğrulamasının gerektiği gibi çalışmamasının birkaç yaygın nedeni vardır:
  
1. **Doğrulama kaydı değeri doğru olmayabilir.** DNS barındırıcınızda, değeri TXT doğrulama kaydına aynı şekilde kopyalayıp yapıştırdığınızı tekrar gözden geçirin. Yaygın sorunlardan biri de kaydın "MS=" kısmının dahil edilmemesidir. Bu kısmı da belirtmeniz gerekir! 
    
2. **Kayıt kaydedilmemiş olabilir.** Bazı DNS barındırıcılarında, İnternet'te güncelleştirilebilmesi için bölge dosyasını kaydetmek (DNS kaydının bulunduğu konuma) üzere ek bir adım uygulamanız gerekir. Kaydın görmelerini ve doğrulamalarını Microsoft 365 için değişikliklerinizi kaydetmeyi sağlar. 
    
3. **Kayıt İnternet'te güncelleştirilmemiş olabilir.** Yeni kaydı görmemiz genellikle yalnızca birkaç dakika sürer, ancak bazı durumlarda bu işlem birkaç saate kadar sürebilir. 
    
## <a name="outlook-isnt-working"></a>Outlook çalışmıyor mu?

Etki alanınız için MX kaydınızı ve diğer DNS kayıtlarınızı doğru ayarladığınız halde posta çalışmıyorsa [Outlook sorunlarınızı düzeltmenize](/exchange/troubleshoot/outlook-connectivity/outlook-connection-issues) yardımcı olmamız için bize ulaşın.
  
## <a name="everyones-email-got-switched-to-microsoft-365-and-you-only-wanted-your-email-to-switch"></a>Herkesin e-postası E-posta Microsoft 365 siz yalnızca E-postanız'ın geçişini istediniz mi?
<a name="BKMK_EmailSwitched"> </a>

Etki alanınızı Microsoft 365'e eklerken, normalde etki alanınıza gönderilen TÜM e-postaların Microsoft 365'a işaret etmek üzere etki alanı MX kaydı (siz veya Microsoft 365 tarafından) güncelleştirilir ve bu etki alanına gönderilen TÜM e-Microsoft 365. MX kaydını değiştirmeden ÖNCE, Microsoft 365 etki alanınıza e-postası olan herkes için posta kutuları oluşturduğunuzdan emin olun.
  
Etki alanınız içinde yer alan herkesin e-postalarını başka bir yere taşımak istemiyorsanız Microsoft 365? Bunun yerine yalnızca birkaç [e-Microsoft 365 e-posta adresiyle pilot uygulama adımlarını atabilirsiniz](../setup/domains-faq.yml).
  
## <a name="cant-confirm-non-profit-or-school-account-status"></a>Kar amacı gütmeyen veya okul hesabı durumunu doğrulaya mısınız?
<a name="BKMK_validateAcct"> </a>

Yalnızca kuruluşun etki alanını doğrulamanız ve herhangi bir hizmet ayarlamamanız gereken birkaç senaryo vardır. Örneğin, kuruluşlarının bir Microsoft 365 için uygun olduğunu kanıtlamaya yardımcı olmak için.
  
Sahipliği, kar amacı gütmeyen [kuruluş Microsoft 365](../setup/domains-faq.yml) eğitim durumunu kanıtlamak ya da gerekli tüm adımları tamamlamış olmak için Yammer etki alanını doğrulama konusunda yer alan kılavuza göz atabilirsiniz. Her durum için biraz farklıdır. 
  
## <a name="services-not-working-with-your-domain"></a>Etki alanınızdaki hizmetler çalışmıyor mu?

Etki alanınızın DNS kurulumuyla ilgili sorunları düzeltmenize yardımcı olabiliriz. Aynı dosyanın etki Microsoft 365 sorun gidericisi size düzeltmesi gereken tüm kayıtları ve kayıtların tam olarak ne olarak ayar gerektir olacağını gösterir. 

> [!TIP]
> DNS'iniz doğru ayarlanmış ama masaüstünüzde posta Outlook çalışmıyor mu? İşletmeniz [için doğru ayarlanmış şeyler olduğundan emin olmak için Microsoft 365](/exchange/mail-flow-best-practices/mail-flow-best-practices) posta kutusuyla birlikte sahip olanızay farklı posta akışı senaryoları göz atabilirsiniz. Veya burada e-postayla ilgili daha fazla sorun giderme yardımı alın: [Sorunları Outlook düzeltin](/exchange/troubleshoot/outlook-connectivity/outlook-connection-issues). 
  
## <a name="accessing-your-website-isnt-working"></a>Web sitenize erişemiyor musunuz?

Tüm DNS sorunlarını çözdüyseniz ve hala sorun yaşıyorsanız, aşağıdakilerden birini deneyin.
  
- Kişiler web sitenize şu anda *contoso.com:* [Web sitesi sorunlarını izleme](../setup/add-domain.md)
    
- A kaydınızı veya CNAME kaydınızı web sitenize işaret etmek üzere güncelleştiresiniz: kayıt sayfasında [özel DNS kayıtlarını Microsoft 365](../setup/add-domain.md)

## <a name="related-content"></a>İlgili içerik

[Sorun giderme: Doğrulanmış etki alanı değişikliğiyle ilgili verileri denetleme](/azure/active-directory/reports-monitoring/troubleshoot-audit-data-verified-domain) (makale)\
[Etki Alanları SSS](../setup/domains-faq.yml) (makale)

