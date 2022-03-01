---
title: Postanıza erişmek için temel izinleri Microsoft Defender Güvenlik Merkezi
description: Uç nokta için Microsoft Defender portalına erişim için temel izinleri nasıl kullanabileceğinizi öğrenin.
keywords: kullanıcı rollerini atama, okuma ve yazma erişimi atama, salt okunur erişim atama, kullanıcı, kullanıcı rolleri, roller
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 27c480a0d4c95e79619e10f8fa42efb2c268b18c
ms.sourcegitcommit: 2b9d40e888ff2f2b3385e2a90b50d719bba1e653
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2021
ms.locfileid: "62997022"
---
# <a name="use-basic-permissions-to-access-the-portal"></a>Portala erişmek için temel izinleri kullanma

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Aşağıdakiler için geçerlidir:**
- Azure Active Directory
- [Uç Nokta Planı 1 için Microsoft Defender](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Uç Nokta Planı 2 için Microsoft Defender](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Defender'ı deneyimli yapmak mı istiyor musunuz? [Ücretsiz deneme için kaydol'](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-basicaccess-abovefoldlink)

Temel izin yönetimini kullanmak için aşağıdaki yönergelere bakın.

Aşağıdaki çözümlerden birini kullanabilirsiniz:

- Azure PowerShell
- Azure portalı

İzinler üzerinde ayrıntılı denetim için rol [tabanlı erişim denetimine geçiş.](rbac.md)

## <a name="assign-user-access-using-azure-powershell"></a>E-posta kullanarak kullanıcı erişimi Azure PowerShell

Aşağıdaki izin düzeylerinden birini kullanan kullanıcılara atama yapabilirsiniz:

- Tam erişim (Okuma ve Yazma)
- Salt okunur erişim

### <a name="before-you-begin"></a>Başlamadan önce

- Yükleme Azure PowerShell. Daha fazla bilgi için bkz. [Posta e-postalarını yükleme Azure PowerShell](https://azure.microsoft.com/documentation/articles/powershell-install-configure/).

  > [!NOTE]
  > PowerShell cmdlet'lerini yükseltilmiş bir komut satırı içinde çalıştırmalısiniz.

- Bağlan'e Azure Active Directory. Daha fazla bilgi için bkz[. Bağlan-MsolService](/powershell/module/msonline/connect-msolservice).

  - **Tam erişim**: Tam erişime sahip kullanıcılar oturum açma, tüm sistem bilgilerini görüntüleme ve uyarıları çözümleme, derin çözümleme için dosyaları gönderme ve ekleme paketini indirme. Tam erişim hakları atamak için, kullanıcıları "Güvenlik Yöneticisi" veya "Genel Yönetici" AAD rollerini eklemeyi gerektirir.
  - **Salt okunur erişim**: Salt okunur erişime sahip kullanıcılar oturum açma iznine sahip olabilir, tüm uyarıları ve ilgili bilgileri bakabilirsiniz.

    Bu durumda uyarı durumlarını değiştiremez, derin çözümleme için dosya gönderemeyecek veya durum değiştirme işlemi gerçekleştirmeyecektir.

    Salt okunur erişim hakları atamak, kullanıcıları "Güvenlik Okuyucu" Azure AD'nin yerleşik rolüne eklemeyi gerektirir.

Güvenlik rolleri atamak için aşağıdaki adımları kullanın:

- Okuma **ve yazma** erişimi için, aşağıdaki komutu kullanarak kullanıcıları güvenlik yöneticisi rolüne attayabilirsiniz:

  ```PowerShell
  Add-MsolRoleMember -RoleName "Security Administrator" -RoleMemberEmailAddress "secadmin@Contoso.onmicrosoft.com"
  ```

- Salt **okunur erişim** için, aşağıdaki komutu kullanarak kullanıcıları güvenlik okuyucusu rolüne attayın:

  ```PowerShell
  Add-MsolRoleMember -RoleName "Security Reader" -RoleMemberEmailAddress "reader@Contoso.onmicrosoft.com"
  ```

Daha fazla bilgi için bkz[. Üyeleri kullanarak grup üyelerini Azure Active Directory](/azure/active-directory/fundamentals/active-directory-groups-members-azure-portal).

## <a name="assign-user-access-using-the-azure-portal"></a>Azure portalını kullanarak kullanıcı erişimi atama

Daha fazla bilgi için bkz[. Başka kullanıcılara yönetici ve yönetici olmayan roller Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal).

## <a name="related-topic"></a>İlgili konu

- [RBAC kullanarak portal erişimini yönetme](rbac.md)
