---
title: Grupları karşılaştırma
ms.reviewer: arvaradh
f1.keywords: CSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 758759ad-63ee-4ea9-90a3-39f941897b7d
description: Microsoft 365 üyeleri konuşmalar, dosyalar ve takvim olayları için bir grup e-postası ve paylaşılan çalışma alanı, Akış ve bir Planner alır.
ms.openlocfilehash: 72da8af8acd0725a5d7509b84f08e4220f7772d4
ms.sourcegitcommit: 33bc25167812b31c51cf096c728e3a5854e94f1c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/01/2022
ms.locfileid: "64594719"
---
# <a name="compare-groups"></a>Grupları karşılaştırma

Çalışma <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**gruplarının**</a> Gruplar Microsoft 365 yönetim merkezi, şu tür gruplar oluşturabilir ve yönetebilirsiniz: 

- **Microsoft 365 Grupları** şirket içinde ve dışında kullanıcılar arasında işbirliği için kullanılır. İş Birliği ve Planner gibi işbirliği hizmetlerini SharePoint içerirler.
- **Dağıtım grupları** , bir grup kişinin e-posta bildirimleri göndermek için kullanılır.
- **Güvenlik grupları**, e-posta siteleri gibi kaynaklara erişim SharePoint kullanılır.
- **Posta etkin güvenlik grupları**, e-posta hesabı gibi kaynaklara erişim SharePoint ve bu kullanıcılara e-posta bildirimleri göndermek için kullanılır.
- **Paylaşılan posta kutuları**, şirket bilgileri veya destek e-posta adresi gibi birden çok kişinin aynı posta kutusuna erişmesi gerektiğinde kullanılır.
- **Bir kuruluş içindeki e-posta** iletilerinin ve diğer bilgilerin toplu olarak gönderilmesini hızlandırmak için dinamik dağıtım grupları oluşturulur.

Bazı gruplar dinamik üyelik veya e-postaya olanak sağlar.

||Microsoft 365 Grupları|Dağıtım grupları|Güvenlik grupları|Posta özellikli güvenlik grupları|Paylaşılan posta kutuları|Dinamik dağıtım grupları|
|:----|:----|:----|:----|:----|:----|:----|
|**Posta etkin**|Evet|Evet|Hayır|Evet|Evet|Evet|
|**Azure AD'de dinamik üyelik**|Evet|Hayır|Evet|Hayır|Hayır|Hayır|

Bu grup türlerinin hepsi tek tek Power Automate.

## <a name="microsoft-365-groups"></a>Microsoft 365 Grupları

Microsoft 365 Grupları şirket içinde ve dışında kullanıcılar arasında işbirliği için kullanılır. Grup üyeleri Microsoft 365 konuşmalar, dosyalar ve takvim olayları için bir grup e-postası ve paylaşılan çalışma alanı alır, Akış ve bir Planner alırlar.

Yönetici tarafından etkinleştirilmiş olduğu sürece, bir gruba kuruluş dışından [kişi eklersiniz](manage-guest-access-in-groups.md). Artık, dış gönderenlerin de grup e-posta adreslerine e-posta göndermesine izin verebilirsiniz.

Microsoft 365 Grupları, grup üyelerine [bölüm, konum](/azure/active-directory/users-groups-roles/groups-change-type), unvan vb. kullanıcı özniteliklerine göre otomatik olarak eklenmelerine veya kaldırılmasına izin veren Azure Active Directory'de dinamik üyelik için ya yapılabiliyor.

Microsoft 365 Grupları uygulamalarına iOS için Outlook Android için Outlook gibi mobil uygulamalar aracılığıyla erişilebilir.

[Yönetici tarafından etkinleştirilirse](../../solutions/allow-members-to-send-as-or-send-on-behalf-of-group.md), ileti gönderebilir ya da grup üyeleri farklı olarak ya da grup e-posta adresi adına gönderim yapabilir. 

Microsoft 365 Grupları diğer iş gruplarıyla veya dağıtım veya güvenlik Microsoft 365 Grupları iç içe yerleştirmeyi desteklemez.

Microsoft 365 Grupları site üzerinde kullanıcılara izin vermek SharePoint gruplardan (Sahipler, Üyeler veya Ziyaretçiler) biri eklenebilir.

## <a name="distribution-groups"></a>Dağıtım grupları

[Dağıtım grupları](/exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups) bir kişi grubuna bildirim göndermek için kullanılır. Yönetici tarafından etkinleştirildiyse, dış e-posta alabilirler.

Dağıtım grupları, en çok da "A Binasındaki Kişiler" ya da "Contoso'daki herkes"gibi belirlenmiş bir grup kişiye bilgi yayınlamanız gereksinim duyduğunuz durumlar için uygundur.

Dağıtım grupları diğer [gruplara Microsoft 365 Grupları](../manage/upgrade-distribution-lists.md).

Dağıtım grupları grup içinde bir eklenmiştir Microsoft Teams, ancak grubun kendisinin değil, yalnızca üyeler eklenir.

Microsoft 365 Grupları grupların üyesi olamz.

## <a name="dynamic-distribution-groups"></a>Dinamik dağıtım grupları 

[Dinamik dağıtım grupları](/exchange/recipients-in-exchange-online/manage-dynamic-distribution-groups/manage-dynamic-distribution-groups) , bölüm veya konum gibi belirli öznitelikleri olan kişilerin posta göndermek için kullanılan, posta etkin gruplardır. Bu öznitelikler, Azure AD Exchange yönetim merkezinde tanımlanır.

Tanımlanmış bir üye kümesi içeren normal dağıtım gruplarından farklı olarak, dinamik dağıtım gruplarının üyelik listesi, tanımladığınız filtreler ve koşullar temel alarak gruba her ileti gönder gönder dosyalarıyla hesaplanır. Bir e-posta iletisi dinamik dağıtım grubuna gönderiğinde, kuruluşta bu grup için tanımlanan ölçütle uyan tüm alıcılara teslim edilir.

## <a name="security-groups"></a>Güvenlik grupları

[Güvenlik grupları](../email/create-edit-or-delete-a-security-group.md), çalışma grupları gibi Microsoft 365 kaynakları için erişim SharePoint. Her kaynağa ayrı ayrı kullanıcı eklemek yerine yalnızca grubu yönetmeniz gerektiğinde yönetimi kolaylaştırabilir.

Güvenlik grupları kullanıcıları veya cihazları içerebilir. Aygıtlar için bir güvenlik grubu oluşturma, Intune gibi mobil cihaz yönetim hizmetleriyle kullanılabilir.

Güvenlik grupları, [Azure Active Directory 'de dinamik üyelik için yapılandırılabilir](/azure/active-directory/users-groups-roles/groups-change-type), grup üyelerinin veya cihazların departman, konum veya ünvan gibi kullanıcı özniteliklerine; ya da işletim sistemi sürümü gibi aygıt özniteliklerinine dayalı olarak otomatik olarak eklenmesine veya kaldırılmasına izin verir.

Güvenlik grupları eklenmiştir.

Microsoft 365 Grupları grupların üyesi olması gerekir.

## <a name="mail-enabled-security-groups"></a>Posta özellikli güvenlik grupları

Posta özellikli güvenlik grupları, değişken olarak Azure Active Directory aracılığıyla yönetilmesi ve cihaz içeremeyeceği durumlar dışında normal güvenlik gruplarıyla aynı işlevi görür.

Bunlar grubun tüm üyelerine e-posta gönderme özelliğini içerir.

Posta özelliği etkin güvenlik grupları eklenmiştir.

## <a name="shared-mailboxes"></a>Paylaşılan posta kutuları

[Paylaşılan posta kutuları](../email/create-a-shared-mailbox.md), birden çok kişinin aynı posta kutusuna, örneğin şirket bilgileri veya e-posta adresi, alma masa veya birden fazla kişi tarafından paylaşılabilen başka bir işleve ulaşması gerektiğinde kullanılır.

Yönetici bu özelliği etkinleştirdiyse paylaşılan posta kutuları dış e-posta alabilir.

Paylaşılan posta kutuları, işbirliği için  kullanılan bir takvim içerir.

Yönetici bu kullanıcıya bunu yapma izni verdiyseniz, grup posta kutusu izinleri olan kullanıcılar posta kutusu e-posta adresi olarak veya bu adres adına gönderebilir. Bu, özellikle yardım ve destek posta kutuları için kullanışlıdır çünkü kullanıcılar "Contoso Desteği" veya "Resepsiyon Masası Inşa E-posta gönderebilir."

Paylaşılan bir posta kutusunu Paylaşılan Posta Kutusu Grubu'Microsoft 365 geçirilmez.

## <a name="related-content"></a>İlgili içerik

[Daha fazla bilgi Microsoft 365 Grupları](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

[Dağıtım listelerini Microsoft 365 Grupları'Outlook](/microsoft-365/admin/manage/upgrade-distribution-lists)

[Neden Outlook'ta dağıtım listelerinizi gruplara yükseltmelisiniz?](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188)
