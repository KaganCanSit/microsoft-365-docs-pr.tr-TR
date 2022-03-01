---
title: Linux'ta Uç Nokta için Microsoft Defender güncelleştirmelerini dağıtma
ms.reviewer: ''
description: Kurumsal ortamlarda Linux'ta Uç Nokta için Microsoft Defender güncelleştirmelerinin nasıl dağıtıl olduğunu açıklar.
keywords: microsoft, defender, Endpoint için Microsoft Defender, linux, güncelleştirmeler, dağıtma
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 71c689143feca3d8c87d219a55c4ea42b4f9d950
ms.sourcegitcommit: 6e90baef421ae06fd790b0453d3bdbf624b7f9c0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/12/2022
ms.locfileid: "63019433"
---
# <a name="deploy-updates-for-microsoft-defender-for-endpoint-on-linux"></a>Linux'ta Uç Nokta için Microsoft Defender güncelleştirmelerini dağıtma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**Aşağıdakiler için geçerlidir:**
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)

Microsoft, performansı, güvenliği geliştirmek ve yeni özellikler sunmak için düzenli olarak yazılım güncelleştirmeleri yayımlar.

> [!WARNING]
> Linux'ta Uç Nokta için Defender'ın her sürümünün bir son kullanma tarihi vardır ve bu tarihten sonra cihazınızı korumaya devam eder. Ürünü bu tarihten önce güncelleştirmeniz gerekir. Son kullanma tarihini kontrol etmek için aşağıdaki komutu çalıştırın:
> ```bash
> mdatp health --field product_expiration
> ```


Genel olarak Uç Nokta özellikleri için Microsoft Defender'ın kullanımına, dağıtımda kullanılan güncelleştirme kanalına bakılmaksızın eşdeğerdir (Beta (Insider), Önizleme (Dış), Geçerli (Üretim)).


Linux'ta Uç Nokta için Defender'ı el ile güncelleştirmek için aşağıdaki komutlardan birini yürütün:

## <a name="rhel-and-variants-centos-and-oracle-linux"></a>RHEL ve çeşitlemeler (CentOS ve Oracle Linux)

```bash
sudo yum update mdatp
```

## <a name="sles-and-variants"></a>SLES ve çeşitlemeler

```bash
sudo zypper update mdatp
```

## <a name="ubuntu-and-debian-systems"></a>Ubuntu ve Debian sistemleri

```bash
sudo apt-get install --only-upgrade mdatp
```

> [!IMPORTANT]
> Uç Nokta için Microsoft Defender ve Bulut için Defender tümleştirilirken, mdatp aracısı güncelleştirmeleri varsayılan olarak otomatik olarak alır.
