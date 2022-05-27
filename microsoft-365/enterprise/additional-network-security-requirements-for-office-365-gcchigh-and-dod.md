---
title: Office 365 GCC High ve DoD için ek ağ güvenlik gereksinimleri
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
description: 'Özet: Office 365 GCC Yüksek ve DoD ek ağ güvenlik gereksinimlerine sahiptir'
hideEdit: true
ms.openlocfilehash: 86d3eb3fb4db42eda2be0c2c66fc754fbfd35f1e
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65754278"
---
# <a name="additional-network-security-requirements-for-office-365-gcc-high-and-dod"></a>Office 365 GCC High ve DOD için ek ağ güvenliği gereksinimleri

*Bu makale Office 365 GCC High, Office 365 DOD, Microsoft 365 GCC High ve Microsoft 365 DOD için geçerlidir.*

Office 365 GCC High ve DOD, Birleşik Devletler Kamu'nun ve tedarikçilerinin ve yüklenicilerinin ihtiyaçlarını karşılamak için güvenli bulut ortamlarıdır.  Bu bulut ortamları, hizmetlerin erişmesine izin verilen dış uç noktalar üzerinde ek ağ kısıtlamalarına sahiptir.

GCC Federasyon kimliklerini veya karma bir arada bulunmayı planlayan Yüksek ve DOD müşterileri, Microsoft'un mevcut şirket içi dağıtımlarınıza gelen ve/veya giden erişime izin vermesini gerektirebilir.  Bu etkinliklere örnek olarak şunlar verilebilir:

* Federasyon kimliklerinin kullanımı (Active Directory Federasyon Hizmetleri (AD FS) veya desteklenen benzer STS ile)
* Şirket içi Exchange Server veya Skype Kurumsal dağıtımıyla karma birlikte bulunma
* Mevcut kullanıcı içeriğini şirket içi sistemden geçirme

Hizmetin şirket içi uç noktalarınızla iletişim kurmasına izin vermek için, ağ değişiklikleri için Office 365 mühendisliğine bir e-posta göndermeniz **gerekir**.

> [!WARNING]
> Tüm isteklerin **üç haftalık** bir SLA'sı vardır ve gerekli güvenlik ve uyumluluk denetimleri ile dağıtım işlem hatları nedeniyle hızlandırılamaz.  Bu, ilk ekleme ağ isteklerinin yanı sıra hizmete geçiş yaptıktan sonra yapılan değişiklikleri içerir.  Ağ ekiplerinizin bu zaman çizelgesinin farkında olduğundan ve planlama döngülerine dahil olduğundan emin olun.

[Office 365 Kamu Allow-List İsteklerine](mailto:o365gwlt@microsoft.com) aşağıdaki bilgileri içeren bir e-posta gönderin:

* **Son**: [İstekleri Office 365 Kamu Allow-List](mailto:o365gwlt@microsoft.com)
* **Kimden**: Kiracı yöneticisi - e-posta gönderme işleminin kiracınızdaki Genel Yönetici kişisi ile eşleşmesi **gerekir**
* **E-posta konusu**: Office 365 GCC Yüksek Ağ İsteği - contoso.onmicrosoft.us (kiracınızın adıyla değiştirin)

İletinizin gövdesi aşağıdaki verileri içermelidir:

* Microsoft Online Services kiracı adınız (örneğin, contoso.onmicrosoft.com, fabrikam.onmicrosoft.us)
* Microsoft'un ağ değişiklikleriyle ilgili devam eden iletişimler için iletişim kuracağı ve/veya geçersiz alt ağlar için takip edeceği bir e-posta dağıtım listesi
* Şirket içi dağıtımlarınızla karma birlikte Microsoft Teams kullanmayı planlayıp planlamayabileceğinizi belirtin
* Federasyon kimlik sistemi dışarıdan erişilebilir URL (örneğin, sts.contoso.com) ve CIDR gösterimindeki IP adresi aralığı (örneğin, . 10.1.1.0/28)
* CIDR gösteriminde Şirket İçi PKI Sertifika İptal Listesi URL'si ve IP adresi aralığı
* CIDR gösteriminde şirket içi Exchange Server dağıtımı için dışarıdan erişilebilir URL ve IP adresi aralığı
* CIDR gösteriminde Skype Kurumsal şirket içi dağıtım için dışarıdan erişilebilir URL ve IP adresi aralığı

Güvenlik ve uyumluluk nedenleriyle, isteğinizle ilgili aşağıdaki kısıtlamaları göz önünde bulundurun:

* Kiracı başına dört alt ağ sınırlaması vardır
* Alt ağlar CIDR Gösteriminde olmalıdır (örneğin, 10.1.1.0/28)
* Alt ağ aralıkları /24'den büyük olamaz
* Ticari bulut hizmetlerine (ticari Office 365, Google G-Suite, Amazon Web Services vb.) erişime izin verme isteklerini **karşılayamıyoruz**

İsteğiniz Microsoft tarafından alındıktan ve onaylandıktan sonra, uygulama için üç haftalık bir SLA vardır ve hızlandırılamaz.  İsteğinizi aldığımızda bir ilk bildirim ve tamamlandıktan sonra son bir bildirim alırsınız.
