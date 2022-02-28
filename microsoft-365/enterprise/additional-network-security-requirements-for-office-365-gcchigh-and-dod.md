---
title: Yüksek ve DoD hizmet Office 365 GCC ek ağ güvenlik gereksinimleri
ms.author: dzazzo
author: dzazzo
manager: dzazzo
ms.date: 05/19/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- OGA150m
- OGC150
- OGD150
- MOE150
ms.assetid: ''
description: "Özet: Office 365 GCC DoD ve DoD'nin ek ağ güvenlik gereksinimleri vardır"
hideEdit: true
ms.openlocfilehash: c4fbfc52085b634329130c2785ce683109b8febe
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985691"
---
# <a name="additional-network-security-requirements-for-office-365-gcc-high-and-dod"></a>Yüksek ve DOD hizmet Office 365 GCC ek ağ güvenlik gereksinimleri

*Bu makale Office 365 GCC High, Office 365 DOD, Microsoft 365 GCC High ve Microsoft 365 DOD için geçerlidir.*

Office 365 GCC Yüksek ve DOD, ABD Kamu'nın ve tedarikçileriyle yüklenicilerinin  ihtiyaçlarını karşılamak için güvenli bulut ortamlarıdır.  Bu bulut ortamlarının, hizmetlerin erişime izin verdiği dış uç noktalarla ilgili ek ağ kısıtlamaları vardır.

GCC Şirket dışında kimlikler veya karma birlikte kullanım planlarına sahip olan yüksek ve DOD müşterileri, Microsoft'un şirket içi dağıtımlar için gelen ve/veya giden erişime izin vermesini gerektirir.  Bu etkinliklere örnek olarak şunlar yer almaktadır:

* Federasyon kimliklerinin kullanımı (Active Directory Federasyon Hizmetleri veya desteklenen benzer STS ile)
* Şirket içi dağıtım veya şirket içi dağıtımla Exchange Server Skype Kurumsal birlikte kullanılabilirlik
* Var olan kullanıcı içeriğini şirket içi bir sistemden geçirme

Hizmetin şirket içi uç noktalarınız ile iletişim kurmasına izin ver olmak için, ağ  değişiklikleri için Office 365-posta göndermeniz gerekir.

> [!WARNING]
> Tüm istekler üç **haftalık** SLA'lara sahiptir ve gerekli güvenlik ve uyumluluk denetimleri ile dağıtım potansiyelleri nedeniyle hızlandır işlemi tamamamaz.  Bu, ilk ekleme ağ isteklerini ve hizmete geçiş sonrasında yapılan tüm değişiklikleri içerir.  Ağ ekiplerinin bu zaman çizelgesinin farkında olduğundan ve planlama döngülerine dahil olduğundan emin olun.

Aşağıdaki bilgilerin yer Office 365 Kamu Allow-List [E-posta](mailto:o365gwlt@microsoft.com) gönderin:

* **Son**: [Office 365 Kamu Allow-List'i kabul etmek](mailto:o365gwlt@microsoft.com)
* **İlk**: Kiracı yöneticisi: E-posta gönderme, **kiracı bir** Genel Yönetici kişisi ile eşleşmeli
* **E-posta** Office 365 GCC: Yüksek Ağ İsteği - contoso.onmicrosoft.us (kiracı adınızla değiştirme)

İletinizin gövdesi aşağıdaki verileri içermeli:

* Microsoft Online Services kiracı adınız (örneğin, contoso.onmicrosoft.com, fabrikam.onmicrosoft.us)
* Microsoft'un ağ değişiklikleri ve/veya geçersiz alt ağlarla ilgili devam edecek iletişimler için iletişim kuracakları e-posta dağıtım listesi
* Şirket içi dağıtımlarınız ile Microsoft Teams bir karma birlikte kullanmayı planla işaretle
* Federasyon kimlik sisteminin dışarıdan erişilebilir URL'si (örneğin, sts.contoso.com) ve IP adresi aralığı (örneğin,. 10.1.1.0/28)
* CIDR notasyonunda Şirket İçi PKI Sertifika İptal Listesi URL'si ve IP adresi aralığı
* CIDR bildiriminde şirket içi dağıtım Exchange Server için dışarıdan erişilebilir URL ve IP adresi aralığı
* CIDR bildiriminde şirket içi dağıtım Skype Kurumsal dış erişilebilir URL ve IP adresi aralığı

Güvenlik ve uyumluluk nedenleriyle, isteğiniz ile ilgili aşağıdaki kısıtlamaları unutmayın:

* Kiracı başına dört alt ağ sınırlaması vardır
* Alt ağların CIDR Notasyonu'na bağlı olması gerekir (örneğin, 10.1.1.0/28)
* Alt ağ aralıkları ağdan büyük /24
* Ticari **bulut** hizmetlerinin (ticari bulut hizmetleri, Google G-Suite, Amazon Web Hizmetleri Office 365 vb.) erişimine izin verme isteklerine yer ve vermiyoruz.

İsteğiniz Microsoft tarafından alınarak onaylandıktan sonra, uygulama için üç haftalık bir SLA vardır ve bu sürenin tamamlanamaz.  İsteğinizi aldıkktan sonra bir ilk bildirim ve tamamlandıktan sonra son bir bildirim alırsınız.
