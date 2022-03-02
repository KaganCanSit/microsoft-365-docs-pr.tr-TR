---
title: Siber güvenlik Privileged Identity Management için Microsoft Defender'da Azure Office 365'i (PIM) kullanın.
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 09/03/2021
audience: ITPro
ms.topic: article
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 56fee1c7-dc37-470e-9b09-33fff6d94617
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
description: Office 365 için Microsoft Defender'da yükseltilmiş ayrıcalık görevleri gerçekleştirmek amacıyla kullanıcılara tam zamanlı ve sınırlı erişim vermek için Azure PIM'i tümleştirin ve verilerinize riski düşürebilirsiniz.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3be90ff1113e25ea418aaf1a25b12574b3bbbe1f
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "63032509"
---
<!--A-->
# <a name="privileged-identity-management-pim-and-why-to-use-it-with-microsoft-defender-for-office-365"></a>Privileged Identity Management için Microsoft Defender ile birlikte neden PIM Office 365

Privileged Identity Management (PIM), ayarlamalar yapıldıktan sonra kullanıcıların belirli bir görevin yapılması için sınırlı bir süre (bazen zaman kutusu kullanım süresi olarak da adlandırılan) verilere erişmelerini sağlar. Bu erişim, gerekli olan eylemi yapmak için 'tam zamanında' verilir ve sonra iptal edilir. PIM, verilerin ve diğer ayarlara uzun süreli erişimi olan ayrıcalıklı yönetim hesaplarıyla karşılaştırıldığında, kullanıcının hassas verilere erişimini ve süresini sınırlar. Peki bu özelliği (PIM) iş için Microsoft Defender ile birlikte Office 365?

> [!TIP]
> PIM erişimi, rol ve kimlik düzeyi kapsamındadır ve birden çok görevi tamamlamaya olanak sağlar. Bu, Görev düzeyinde kapsamı bulunan Ayrıcalıklı Erişim Yönetimi (PAM) ile karıştırılmamalıdır.

## <a name="steps-to-use-pim-to-grant-just-in-time-access-to-defender-for-office-365-related-tasks"></a>İlgili görevlerde Defender'a tam zamanlı erişim vermek üzere PIM Office 365 adımları

Yöneticiler, PIM'i Office 365 Defender'la çalışacak şekilde ayarerek, bir kullanıcının ihtiyaçları olan eylemleri gerçekleştirsin ve erişim isteğide bulunduracakları bir süreç oluşturabilir. Kullanıcı, *ayrıcalıklarını yükseltme* ihtiyacını haklı çıkarmalı.

Bu örnekte, güvenlik ekibimizin bir üyesi olan ve Office 365'de ayakta duran erişimi sıfır olan ancak Tehdit Arama gibi günlük normal işlemler için gereken normal bir role yükseltebilecek olan bir üye olan "Alex"i yapılandıracak ve ardından kötü amaçlı teslim [](threat-hunting-in-threat-explorer.md) edilen e-postaları düzeltme gibi daha az sık ama hassas işlemler gerektiğinde daha yüksek bir ayrıcalık düzeyine yükseltebilecekiz.[](remediate-malicious-email-delivered-office-365.md)

> [!NOTE]
> Bu, Office 365 için Microsoft Defender'da Threat Explorer'ı kullanarak e-postaları temizlemeyi gerektiren Güvenlik Analisti IÇIN PIM'yi ayarlamada gereken adımlarda size yol sağlar, ancak aynı adımlar Güvenlik ve Uyumluluk portalı içindeki diğer RBAC rolleri için de kullanılabilir. Örneğin bu işlem, eBulma'da arama ve vaka çalışması yapmak için günlük erişim gerektiren, ancak ara sıra kiracıdan verileri dışarı aktarma hakkı olan bir bilgi çalışanı için kullanılabilir.

***1. Adım***. Aboneliğinizin Azure PIM konsolunda, azure güvenlik okuyucusu rolüne kullanıcı (Alex) ekleyin ve etkinleştirmeyle ilgili güvenlik ayarlarını yapılandırın.

1. [Azure AD Yönetim Merkezi'nde oturum açın](https://aad.portal.azure.com/) ve **Azure Active Directory** >  **Ve yöneticiler'i seçin**.
2. Roller **listesinde Güvenlik** Okuyucu'ya tıklayın ve sonra **Ayarlar** >  **Edit**
3. Azure **MFA'nın gerekli olması için** 'Etkinleştirme süresi (saat)' normal bir iş günü olarak ve 'Etkinleştirme açık' **olarak ayarlayın**.
4. Bu, Alex'in günlük işlemler için normal ayrıcalık düzeyi olduğu için Etkinleştirme için gerekçe gerektir'in Güncelleştirme'ye yönelik olarak > **işaretini kaldırmış oluruz**.
5. Atama **Ekle Üye** **ekle'yi** >  > üyeyi aramak için bu adı seçin veya yazın.
6. PIM  ayrıcalıkları için eklemeniz gereken üyeyi seçmek için Seç düğmesine tıklayın > Ekle'ye **tıklayın > Atama** Ekle sayfasında hiçbir değişiklik yapma (hem atama türü Uygun hem de süre *Kalıcı* Olarak Uygun  varsayılan olacaktır ) ve Ata'ya **tıklayın.**

Kullanıcı adı (burada 'Alex') bir sonraki sayfada Uygun atamalar altında görünür, bu da daha önce yapılandırılan ayarlarla PIM rolüne PIM girebilecekleri anlamına gelir.

> [!NOTE]
> Bu videonun hızlı bir Privileged Identity Management için [bu videoyu izleyin](https://www.youtube.com/watch?v=VQMAg0sa_lE).

:::image type="content" source="../../media/pim-mdo-role-setting-details-for-security-reader-show-8-hr-duration.png" alt-text="Ayrıcalıklı Erişim Yönetimi'nin Güvenlik Okuyucusu rolü ayarlarını tarayın. Burada PIM etkinleştirme süresinin en uzun süresinin 8 saat olduğunu görüyorsunuz.":::

***2. Adım***. Ek görevler için gerekli ikinci (yükseltilmiş) izin grubunu oluşturun ve uygunluğu attayabilirsiniz.

Privileged [Access gruplarını kullanarak](/azure/active-directory/privileged-identity-management/groups-features) artık kendi özel gruplarımızı oluşturabilir ve izinlerini bir araya kullanabilir veya kurumsal uygulamalarınızı ve ihtiyaçlarını karşılamanız gerektiğinde ayrıntıyı artırabilirsiniz.

### <a name="create-a-role-group-requiring-the-permissions-we-need"></a>Gereken izinleri gerektiren bir rol grubu oluşturma

Microsoft 365 Defender portalında, istediğiniz izinleri içeren özel bir rol grubu oluşturun.

1. aşağıdaki Microsoft 365 Defender portalında İzinler Rollerine <https://security.microsoft.com>& **ve** ardından E-posta **ve İşbirliği'nin** altında **Roller'i seçin**. Doğrudan İzinler sayfasına **gitmek** için kullanın <https://security.microsoft.com/emailandcollabpermissions>.
2. İzinler **sayfasında** Simge oluştur'a ![tıklayın.](../../media/m365-cc-sc-create-icon.png) **Oluştur'a iki tablo da oluşturabilirsiniz**
3. Grubu, amacını yansıtacak şekilde 'PİMİ'de Ara ve Temizle' gibi bir ad girin.
4. Üye eklemeden grubu kaydedin ve bir sonraki bölüme geçin!

### <a name="create-the-security-group-in-azure-ad-for-elevated-permissions"></a>Yükseltilmiş izinler için Azure AD'de güvenlik grubu oluşturma

1. [Azure AD Yönetim Merkezi'ne geri gidin ve](https://aad.portal.azure.com/) **Azure** **ADGroupsNew** >  >  **Group'a gidin**.
2. Azure AD grubunızı amacını yansıtacak şekilde ad kullanın; şu anda sahip **veya üye** gerekmez.
3. **Azure AD rollerini gruba Evet olarak** **atanabilir**.
4. Hiçbir rol, üye veya sahip eklemeden grubu oluşturun.
5. Yeni oluşturduğunuz gruba geri gidin ve Privileged **AccessEnable** >  **Privileged Access öğesini seçin**.
6. Grup içinde Uygun **atamalar'ı** >  seçin **Ödevleri** ekle'yi > Arama özelliği & Üyesinin rolü olarak **Temizleme'yi seçin**.
7. Grubun **Ayarlar** Erişimi bölmesinde yer alan gezinti bölmesini yapılandırabilirsiniz. Üyenin **rolüyle** ilgili ayarları Düzenle'yi **seçin**.
8. Etkinleştirme sürenizi, organizasyonunıza uygun olarak değiştirebilirsiniz. Bu örnekte, *Güncelleştir'i seçmeden önce Azure MFA*, *gerekçelendirme ve* bilet bilgileri **gerekir**. 

### <a name="nest-the-newly-created-security-group-into-the-role-group"></a>Yeni oluşturulan güvenlik grubunu rol grubuna iç içe yerleştirme

1. [Bağlan ve Uyumluluk & PowerShell'e doğru](/powershell/exchange/connect-to-scc-powershell) devam edin ve aşağıdaki komutu çalıştırın:

   ```powershell
   Add-RoleGroupMember "<<Role Group Name>>" -Member "<<Azure Security Group>>"`
   ```

## <a name="test-your-configuration-of-pim-with-defender-for-office-365"></a>PiM yapılandırmanızı Test etmek için Defender ile Office 365

1. Bu noktada portalda yönetici erişimine sahip olması gereken test kullanıcısı [(Alex Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center) ile oturum açın.
2. Kullanıcı günlük güvenlik okuyucu rolünü etkinleştiren PIM'e gidin.
3. Threat Explorer'ı kullanarak e-postayı temizlemeye çalışırsanız, ek izinlere ihtiyacınız olduğunu belirten bir hata alırsınız.
4. PIM'i ikinci kez daha yükseltilmiş role dönüştürebilirsiniz; kısa bir gecikmeden sonra artık e-postaları sorun olmadan temiz tutabilirsiniz.

   :::image type="content" source="../../media/pim-mdo-add-the-search-and-purge-role-assignment-to-this-pim-role.PNG" alt-text="Güvenlik Okuyucu PIM rolü aracılığıyla eklenen kullanıcı şüpheli bir e-postayı silebilir ve &quot;Bu e-posta üzerinde işlem yapmak için Arama ve Temizleme rolüne ihtiyacınız var&quot; iletisi alır. Rol ataması almak veya e-postayı bir olayına eklemek için yöneticinize başvurun.":::

Yönetim rollerinin ve Arama ve Temizleme Rolü gibi izinlerin kalıcı olarak ataması Sıfır Güven güvenlik girişimiyle yerine gelir, ancak sizin de gördüğünüz gibi PIM, gerekli araçlara tam zamanlı erişim vermek için kullanılabilir.

*Bu içerik için kullanılan blog gönderilerine ve kaynaklara erişim için Müşteri Mühendisi Ben Bire bir teşekkür ederiz.*

<!--A-->