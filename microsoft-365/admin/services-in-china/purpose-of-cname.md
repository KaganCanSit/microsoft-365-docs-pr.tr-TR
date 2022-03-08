---
title: MSOID için Office 365 CNAME kaydının amacı nedir?
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.collection:
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
ms.service: o365-administration
ms.localizationpriority: medium
search.appverid:
- BCS160
- MET150
- MOE150
ROBOTS: NOINDEX
description: Sizi kimlik doğrulama işlemleri için en iyi sunucuya yönlendiren Office 365'de 'MSOID' CNAME kaydı hakkında daha fazla bilgi edinmek, böylece daha hızlı yanıt alasınız.
monikerRange: o365-21vianet
ms.openlocfilehash: 1b053ac0df7cd770b5627b688e90641688f94141
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63325131"
---
# <a name="whats-the-purpose-of-the-office-365-cname-record-for-msoid"></a>MSOID için Office 365 CNAME kaydının amacı nedir?

 Aradığınızı bulamazsanız, **[Etki Alanları SSS sayfasını inceleyin](../setup/domains-faq.yml)**. 
> [!NOTE]
> Aşağıdakiler yalnızca 21Vianet tarafından Office 365 **Office 365 için geçerlidir.
  
Office 365'te "MSOID" CNAME kaydını neden eklemeniz gerektiğini merak ediyor olabilirsiniz. Hangi aboneliği kullanıyor olursanız olun, tüm özel etki alanları için bu kayıt eklenmelidir. Bu kayıt neden gerekiyor? Biraz teknik bir konu olmakla birlikte, temelde bazı kimlik doğrulama işlemlerinde daha hızlı yanıt alabilmeniz için en iyi sunucuya yönlendirilmenizi sağlar.
  
Teknik Ayrıntılar: Office 365 ile çalışan Skype Kurumsal Çevrimiçi, Outlook, Windows PowerShell veya Microsoft Azure Active Directory Eşitleme aracı gibi bir istemci uygulaması çalıştırıyorsanız, kimlik bilgilerinizin doğrulanması gerekir. Office 365, konumunuz için doğru kimlik doğrulama uç noktasına işaret eden bir CNAME kaydı kullanır ve bu da kimlik doğrulamasında yanıt süresinin kısalmasını sağlar.
  
Etki alanınız için bu CNAME kaydı bu yoksa, söz konusu uygulamalar ABD'de varsayılan kimlik doğrulama uç noktasını kullanır ve bu da kimlik doğrulamasının daha yavaş olabileceği anlamına gelir. Bu CNAME kaydı düzgün yapılandırılmazsa; örneğin, **İşaret edilen adres** alanında yazım hatası yaparsanız, söz konusu uygulamalar kimlik doğrulaması yapamaz.
  
 **Etki Office 365 DNS kayıtlarını siz yönetirse,** Office 365 CNAME kaydını sizin için ayarlar. 
  
 **Etki alanınıza ilişkin DNS kayıtlarını DNS** barındırma barındırma makinende yönetiyorsanız, bu kaydı kendiniz DNS barındırma [barındırması için verilen yönergeleri izleyerek oluşturabilirsiniz](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).
  
Office 365 dağıtımı planlıyorsanız ve eklemeniz veya güncelleştirmeniz gereken tüm DNS kayıtları hakkında daha fazla bilgi edinmek için başvuru: Dış Etki Alanı Adı Sistemi kayıtları makalesinde bu konudaki bilgileri [Office 365](../../enterprise/external-domain-name-system-records.md).
