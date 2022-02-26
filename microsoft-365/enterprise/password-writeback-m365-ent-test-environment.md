---
title: Test ortamınız için parola Microsoft 365 yazma
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/22/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- M365-identity-device-management
- Strat_O365_Enterprise
ms.custom:
- TLGS
- Ent_TLGs
ms.assetid: ''
description: 'Özet: Test ortamınız için parola Microsoft 365 yapılandırma.'
ms.openlocfilehash: 0c0660008aea4a676da4be3c13e8d5c15cb3a51d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62973718"
---
# <a name="password-writeback-for-your-microsoft-365-test-environment"></a>Test ortamınız için parola Microsoft 365 yazma

*Bu Test Laboratuvarı Kılavuzu, sadece kurumsal test Microsoft 365 test ortamları için kullanılabilir.*

Kullanıcılar, parola geri yazma kullanarak parolalarını daha sonra yerel Active Directory Etki Alanı Hizmetleri'Azure Active Directory (Azure AD) çoğaltılmış olan Ad(Azure AD) aracılığıyla güncelleştirabilir. Parola geri yazma ile, kullanıcıların kendi özgün kullanıcı hesaplarının depolandığı şirket içi AD DS'de parolalarını güncelleştirmek zorunda değildir. Bu, şirket içi ağlarına uzaktan erişim bağlantısı olmayan dolaşım veya uzak kullanıcılara yardımcı olur.

Bu makalede, parola geri yazma için Microsoft 365 yapılandırmanız açıklanmıştır.

Parola geri yazma için test ortamınızı yapılandırma iki aşama içerir:
- [Aşama 1: Parola karması eşitlemesini test ortamınız Microsoft 365 yapılandırma](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Aşama 2: TESTLAB AD DS etki alanı için parola geri yazmasını etkinleştirme](#phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain)
  
![Microsoft bulutu için Test Laboratuvarı Kılavuzları.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Kurumsal Test Laboratuvarı Kılavuzu yığınına Microsoft 365 görsel bir harita için, [Microsoft 365 Test Laboratuvarı Kılavuzu Yığını için Microsoft 365'e gidin](../downloads/Microsoft365EnterpriseTLGStack.pdf).

## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Aşama 1: Parola karması eşitlemesini test ortamınız Microsoft 365 yapılandırma

İlk olarak, parola karması [eşitlemesi yönergelerini izleyin](password-hash-sync-m365-ent-test-environment.md). Sonuçta elde edilen yapılandırmanız şöyle görünüyor:
  
![Parola karma eşitlemesi test ortamına sahip sanal kuruluş.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)
  
Bu yapılandırma şunları oluşur:
  
- Deneme Microsoft 365 E5 ücretli abonelik.
- İnternet'e bağlı, Azure sanal ağının alt ağına DC1, APP1 ve CLIENT1 sanal makinelerinden oluşan basitleştirilmiş bir kuruluş intraneti.
- Azure AD Bağlan, TESTLAB AD DS etki alanını Microsoft 365 aboneliğinizin Azure AD kiracısına eşitlemek için APP1'te çalışır.

## <a name="phase-2-enable-password-writeback-for-the-testlab-ad-ds-domain"></a>Aşama 2: TESTLAB AD DS etki alanı için parola geri yazmasını etkinleştirme

İlk olarak, Genel yönetici rolüne sahip Kullanıcı 1 hesabını yapılandırabilirsiniz.

1. Genel [Microsoft 365 yönetim merkezi](https://portal.microsoft.com) yönetici hesabınızla oturum açın.

2. Etkin **kullanıcılar'ı seçin**.
 
3. Etkin **kullanıcılar sayfasında** , **kullanıcı1 hesabını** seçin,

4. Kullanıcı1 **bölmesinde,** Roller'in yanındaki **Düzenle'yi** **seçin**.

5. Kullanıcı1 **için kullanıcı rollerini** düzenle bölmesinde Genel yönetici'yi, **Kaydet'i** ve **sonra** kapat'ı **seçin**.

Ardından, TestLAB AD DS etki alanındaki diğer kullanıcıların adına parolalarını değiştirmesine izin verecek güvenlik ayarlarıyla Kullanıcı 1 hesabını yapılandırabilirsiniz.

1. [Azure portalında](https://portal.azure.com), genel yönetici hesabınızla oturum açın ve SONRA TESTLAB\User1 hesabıyla APP1'e bağlanın.

2. UYGULAMA1 masaüstünden **Başlat'ı seçin**, etkin **girin ve** ardından **Active Directory Kullanıcıları ve Bilgisayarları'ı seçin**.

3. Menü çubuğunda Görünüm'e **tıklayın**. Gelişmiş **özellikler** etkinleştirilmediyse etkinleştirmek için bu özelliği seçin.

4. Ağaç bölmesinde etki alanınızı seçin ve tutun (veya sağ tıklayın), Özellikler'i **seçin** ve ardından Güvenlik **sekmesini** seçin.

5. **Gelişmiş'i seçin**.

6. İzinler **sekmesinde** Ekle'yi **seçin**.

7. **Anapara seç'i** seçin, **Kullanıcı1 girin** ve Tamam'ı **seçin**.

8. **Uygulanacağı yer: altında** Azalan **Kullanıcı nesneleri'ne seçin**.

9. **İzinler'in** altında şunları seçin:

    - **Parolayı değiştir**
    - **Parolayı sıfırlayın**

10. **Özellikler'in** altında şunları seçin:
    - **Write lockoutTime**
    - **Write pwdLastSet**

11. Değişiklikleri **kaydetmek** için üç kez Tamam'ı seçin.

12. **Active Directory Kullanıcıları ve Bilgisayarları'nın kapatın**.

Ardından, parola geri yazma için Bağlan App1'de Azure AD E-posta ayarlarını yapılandırın.

1. Gerekirse TESTLAB\User1 hesabıyla APP1'e bağlanabilirsiniz.

2. APP1'in masaüstünden **Azure AD Uygulama Ekle'ye Bağlan**.

3. Hoş Geldiniz **sayfasında Yapılandır'ı** **seçin**.

4. Ek görevler **sayfasında Eşitleme** seçeneklerini **özelleştir'i seçin ve** sonra da Sonraki'yi **seçin**.

5. **Azure AD'Bağlan** oturum açma sayfasında, genel yönetici hesabı kimlik bilgilerinizi girin ve Ardından Sonraki'yi **seçin**.

6. Dizinler **Bağlan Etki Alanı****/OU filtreleme sayfalarında,** Sonraki'yi **seçin**.

7. İsteğe **bağlı özellikler sayfasında** Parola geri **yazma'ya tıklayın ve** sonra da Sonraki'yi **seçin**.

8. Yapılandırmaya **hazır sayfasında Yapılandır'ı** **seçin** ve işlemi bitirmeyi bekleyin.

9. Yapılandırmanın bitişini gördüğünüzde Çıkış'ı **seçin**.

Artık sanal intranet'inizin sanal ağına bağlı olmayan bilgisayarlardaki kullanıcılar için parola geri yazma test etmeye hazırsınız.

Sonuçta elde edilen yapılandırmanız şöyle görünüyor:

![Geçişli kimlik doğrulama test ortamına sahip sanal kuruluş.](../media/pass-through-auth-m365-ent-test-environment/Phase1.png)

Bu yapılandırma şunları oluşur:

- DNS Microsoft 365 E5 TESTLAB ile deneme veya ücretli abonelikler.\<*your domain name*> kaydedildi.
- İnternet'e bağlı, Azure sanal ağının alt ağına DC1, APP1 ve CLIENT1 sanal makinelerinden oluşan basitleştirilmiş bir kuruluş intraneti.
- Azure AD Bağlan, Microsoft 365 aboneliğinizin Azure AD kiracısı olan hesap ve grupların listesini TESTLAB AD DS etki alanıyla eşitlemek için APP1'te çalışır.
- Parola geri yazma, kullanıcıların basitleştirilmiş intranet'e bağlanmadan Azure AD aracılığıyla parolalarını değiştirebillerini sağlar.

## <a name="next-step"></a>Sonraki adım

Test [ortamınıza](m365-enterprise-test-lab-guides.md#identity) başka kimlik özelliklerini ve özelliklerini keşfedin.

## <a name="see-also"></a>Ayrıca bkz.

[Microsoft 365 Test Laboratuvarı Kılavuzları için kılavuzlar](m365-enterprise-test-lab-guides.md)

[Microsoft 365 genel bakış için genel bakış](microsoft-365-overview.md)

[Microsoft 365 belgeleri için belgeler](/microsoft-365-enterprise/)