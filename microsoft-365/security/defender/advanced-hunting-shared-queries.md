---
title: Gelişmiş avlarda paylaşılan Microsoft 365 Defender kullanma
description: Önceden tanımlanmış ve paylaşılan sorgularla tehdit aramalarına hemen başlayabilirsiniz. Sorgularınızı genel olarak veya kuruluşla paylaşın.
keywords: gelişmiş av, tehdit avı, siber tehdit avı, Microsoft 365 Defender, Microsoft 365, m365, arama, sorgu, telemetri, özel algılamalar, şema, kusto, github repo, sorgularım, paylaşılan sorgular
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 06952be112f4eb28867a4a0cd4bffbee0c664b5c
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63021810"
---
# <a name="use-shared-queries-in-advanced-hunting"></a>Gelişmiş avlarda paylaşılan sorguları kullanma

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- Microsoft 365 Defender
- Uç Nokta için Microsoft Defender



[Gelişmiş arama](advanced-hunting-overview.md) sorguları aynı kuruluşta yer alan kullanıcılar arasında paylaşabilirsiniz. Ayrıca, e-GitHub.com'da herkesle paylaşılan GitHub. Bu sorgular, sıfırdan sorgu yazmak zorunda kalmadan belirli tehdit avı senaryolarını hızla takip etmek için kullanılabilir.

![Paylaşılan sorguların resmi.](../../media/shared-query-1.png)

## <a name="save-modify-and-share-a-query"></a>Sorgu kaydetme, değiştirme ve paylaşma
Yeni veya var olan bir sorguyu, yalnızca sizin erişilsin veya diğer kullanıcılarla paylaşılacak şekilde kaydedebilirsiniz. 

1. Sorgu oluşturma veya değiştirme. 

2. Sorguyu **kaydet açılan** düğmesine tıklayın ve Farklı **kaydet'i seçin**.
    
3. Sorgu için bir ad girin. 

   ![Sorgu kaydetme resmi.](../../media/shared-query-2.png)

4. Sorguyu kaydetmek istediğiniz klasörü seçin.
    - **Paylaşılan sorgular** — kuruluşun tüm kullanıcılarına paylaşılan
    - **Sorgularım** : yalnızca sizin için erişilebilir
    
5. **Kaydet**'i seçin. 

## <a name="delete-or-rename-a-query"></a>Sorguyu silme veya yeniden adlandırma
1. Yeniden adlandırmak veya silmek istediğiniz sorgunun sağ üç noktayı seçin.

    ![Silme sorgusunun resmi.](../../media/shared-query-3.png)

2. **Sil'i seçin** ve silme işlemini onaylayın. Veya Yeniden **Adlandır'ı** seçin ve sorgu için yeni bir ad girin.

## <a name="create-a-direct-link-to-a-query"></a>Sorguya doğrudan bağlantı oluşturma
Sorguyu doğrudan gelişmiş arama sorgusu düzenleyicisinde açan bir bağlantı oluşturmak için sorguyu sonlaştırın ve Bağlantıyı **paylaş'ı seçin**.

## <a name="access-queries-in-the-github-repository"></a>Veri deposundaki GitHub erişme  
Microsoft güvenlik araştırmacısı, özel bir yer için belirlenen genel depoda [gelişmiş av sorgularını düzenli GitHub](https://aka.ms/hunting-queries). Bu depo katkılara açık. Katkıda bulunmak için [GitHub ücretsiz katılın](https://github.com/).

>[!tip]
>Microsoft güvenlik araştırmacısı yeni ortaya çıkan tehditlerle ilişkilendirilmiş etkinlikleri ve göstergeleri bulmak için kullanabileceğiniz gelişmiş arama sorguları da sağlar. Bu sorgular, raporlarda tehdit [çözümlemesi](/windows/security/threat-protection/microsoft-defender-atp/threat-analytics) raporlarının bir Microsoft 365 Defender.


## <a name="related-topics"></a>İlgili konular
- [Gelişmiş ava genel bakış](advanced-hunting-overview.md)
- [Sorgu dilini öğrenme](advanced-hunting-query-language.md)
- [Sorgu sonuçlarıyla çalışma](advanced-hunting-query-results.md)
- [Cihazlar, e-postalar, uygulamalar ve kimlikler arasında iş avı](advanced-hunting-query-emails-devices.md)
- [Şemayı anlama](advanced-hunting-schema-tables.md)
- [Sorguyla ilgili en iyi yöntemleri uygulama](advanced-hunting-best-practices.md)