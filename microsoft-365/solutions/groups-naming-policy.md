---
title: Microsoft 365 grupları adlandırma ilkesi
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
ms.assetid: 6ceca4d3-cad1-4532-9f0f-d469dfbbb552
recommendations: false
description: Grup adlandırma grupları için adlandırma Microsoft 365 öğrenin.
ms.openlocfilehash: acc521dd5be1dcf630b4801eeb914c45e765e00f
ms.sourcegitcommit: c2b5ce3150ae998e18a51bad23277cedad1f06c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/17/2021
ms.locfileid: "63005431"
---
# <a name="microsoft-365-groups-naming-policy"></a>Microsoft 365 grupları adlandırma ilkesi

Grup adlandırma ilkesi kullanarak, kuruluşta kullanıcılar tarafından oluşturulan gruplar için tutarlı bir adlandırma stratejisinin zorunlu tutulabilirsiniz. Adlandırma ilkesi sizin ve kullanıcılarının grubun, üyelikin, coğrafi bölgenin veya grubu oluşturan kullanıcının işlevini belirlemenize yardımcı olabilir. Adlandırma ilkesi, adres defterine grupları kategorilere ayırmanıza da yardımcı olabilir. İlkeyi, grup adlarında ve diğer adlarında belirli sözcüklerin kullanımını engellemek için kullanabilirsiniz.

Adlandırma ilkesi tüm grup iş yükleri (Outlook, Microsoft Teams, SharePoint, Planner, Yammer vb.) genelinde oluşturulan gruplara uygulanır. Hem grup adına hem de grup diğer adına uygulanır. Ayrıca, kullanıcı bir grup oluşturduğunda ve var olan bir grup için grup adı, diğer ad, açıklama veya avatar düzenlenemez.

> [!TIP]
> Grup Microsoft 365 adlandırma ilkesi yalnızca grup Microsoft 365 için geçerlidir. Yeni gruplarda oluşturulmuş dağıtım grupları için Exchange Online. Dağıtım grupları için adlandırma ilkesi oluşturmak için bkz. [Dağıtım grubu adlandırma ilkesi oluşturma](/exchange/recipients-in-exchange-online/manage-distribution-groups/create-group-naming-policy).

Grup adlandırma ilkesi aşağıdaki özelliklerden oluşur:

- **Önek-Son ek adlandırma ilkesi**: Grupların adlandırma kuralını tanımlamak için önekler veya sonekler kullanabilirsiniz (örneğin: "USMy\_ GroupEngineering\_"). Önekler/sonekler, grubu oluştururken kullanıcıya göre değiştirilecek sabit dizeler veya [Department] gibi kullanıcı öznitelikleri olabilir.

- **Özel Engellenen Sözcükler**: Kullanıcılar tarafından oluşturulan gruplarda engellenmiş, belirli bir grup engellenen sözcük yükleyebilirsiniz. (Örneğin: "CEO, Bordro, İk").

## <a name="licensing-requirements"></a>Lisans gereksinimleri

Microsoft 365 Grupları için Azure AD adlandırma ilkesi kullanmak, bir veya birden çok kullanıcı grubunun üyesi olan her benzersiz kullanıcıya (konuklar dahil Microsoft 365) bir Azure Active Directory Premium P1 lisansı veya Azure AD Basic EDU lisansı atamanız zorunlu değildir.

Bu ayrıca, grupları adlandırma ilkesi oluşturan yönetici için de gereklidir.

## <a name="prefix-suffix-naming-policy"></a>Prefix-Suffix adlandırma ilkesi

Önekler ve sonekler sabit dizeler veya kullanıcı öznitelikleri olabilir.

### <a name="fixed-strings"></a>Sabit dizeler

GAL'de grupları ayırt etmeye ve grup iş yüklerinin sol gezintisinde size yardımcı olacak kısa dizeler kullanabilirsiniz. Yaygın ön eklerden bazıları 'GrpName\_' , 'Ad', '\#Ad' gibi anahtar\_ sözcüklerdir

### <a name="attributes"></a>Öznitelikler

Grubu kimin [Departman] gibi oluşturduğunı ve [Ülke] gibi nereden oluşturulmuş olduğunu belirlemeye yardımcı olacak öznitelikler kullanabilirsiniz.

Örnekler:

- İlke = "GRP [GrupAdı] [Bölüm]"
- Kullanıcının bölümü = Mühendislik
- Grup adı = "GRP Grubum Mühendislik" oluşturuldu

Desteklenen Azure Active Directory (Azure AD) öznitelikleri [Department], [Company], [Office], [StateOrProvince], [CountryOrRegion] ve [Title] öznitelikleridir.

- Desteklenmeyen kullanıcı öznitelikleri sabit dize olarak kabul edilir, örneğin [postalCode].

- Uzantı öznitelikleri ve özel öznitelikler desteklenmiyor.

Kuruluşta tüm kullanıcılar için doldurulan değerlere sahip öznitelikler kullanılması ve daha uzun değerlere sahip özniteliklerin kullanılması önerilmez.

### <a name="things-to-look-out-for"></a>Dikkat gerekenler

- İlke oluşturma sırasında, toplam ön ek ve soneklerin dize uzunluğu 53 karakterle sınırlandırılmıştır.

- Önekler ve sonekler, grup adı ve grup diğer adı için desteklenen özel karakterler içerebilir. Önekler ve sonekler grup diğer adlarında izin verilmiyor özel karakterler içeriyorsa, bunlar yalnızca grup adına uygulanır. Bu durumda, grup adına uygulanan önekler ve sonekleri, grup diğer adına uygulananlardan farklı olabilir.

  > [!NOTE]
  > Grup adının başında veya sonunda hariç, grup adının herhangi bir yerinde nokta (.) veya kısa çizgi (-) işaretine izin verilir. Grup adının herhangi bir yerinde, adın başında veya sonunda da alt çizgiye (_) izin verilir.

- Bağlı gruplara Yammer Office 365, adlandırma ilkenize şu karakterleri kullanmaktan kaçının: @, \#, , \]\[\<, and \>. Bu karakterler adlandırma ilkesinde yer Yammer kullanıcılar grup oluşturamaz.

> [!Tip]
> - Sonek olarak kısa dizeler kullanın.
> - Değerlerle öznitelikleri kullanın.
> - Fazla yaratıcı olun; toplam ad uzunluğu en fazla 264 karakter olabilir.
> - Upload kısıtlamak için, özel olarak engellenen sözcükleri kullanın.

## <a name="custom-blocked-words"></a>Özel engellenen sözcükler

Grup adlarında ve diğer adlarında engellenen sözcüklerin virgülle ayrılmış listesini girebilirsiniz.

Hiçbir alt dize arama gerçekleştir yapılmaz; Özel olarak, başarısızlığı tetiklemek için kullanıcı tarafından girilen adla özel engellenen sözcükler arasında tam bir eşleşme olması gerekir.

**Dikkat gerekenler**:

- Engellenen sözcükler büyük/harfe duyarlı değildir.

- Kullanıcı engellenen bir sözcüğü girerken, grup istemcisi engellenen sözcüğün olduğu bir hata iletisi gösterir.

- Kullanılan engellenen sözcüklerde karakter kısıtlaması yoktur.

- Engellenmiş sözcükler olarak ayarlan sözcük sayısı 5000 sözcük sınırlaması vardır.

## <a name="admin-override"></a>Yöneticiyi geçersiz kılma

Bazı yöneticiler tüm grup iş yüklerinde ve uç noktalarında bu ilkelerden muaftır; böylelikle, bu engellenen sözcüklerle ve kendi istenen adlandırma kurallarıyla gruplar oluşturabilirler. Aşağıda, grup adlandırma ilkesinden muaf olan yönetici rollerinin listesi ve listenin bir listesi ve daha sonra ve daha sonraları ve daha sonra görünür.

- Genel yönetici

- İş Ortağı Katman 1 Desteği

- İş Ortağı Katman 2 Desteği

- Kullanıcı hesabı yöneticisi

## <a name="how-to-set-up-the-naming-policy"></a>Adlandırma ilkesi nasıl ayarlanır

Adlandırma ilkesi ayarlamak için:

1. Gruplar [Azure Active Directory](https://aad.portal.azure.com) **Yönet'in altında** Gruplar'a **tıklayın**.
2. **Adlandırma Ayarlar** adlandırma **ilkesi'ne tıklayın**.
3. Grup adlandırma **ilkesi sekmesini** seçin.
4. Geçerli **ilke'nin** altında, önek veya son ek ya da her ikisini birden gerektirmeyi seçin ve uygun onay kutularını seçin.
5. Her satır **için** Öznitelik **ve** Dize'yi seçin ve özniteliği veya dizeyi belirtin.
6. Size gereken ön ekleri ve sonekleri eklediyken, Kaydet'i **tıklatın**.

![Grup grup adlandırma ilkesi ayarlarının ekran Azure Active Directory.](../media/groups-naming-policy-azure.png)

## <a name="related-topics"></a>İlgili konular

[İşbirliği yönetim planlaması önerileri](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[İşbirliği yönetim planınızı oluşturma](collaboration-governance-first.md)

[Azure Active Directory ayarlarını yapılandırmak için cmdlet'leri yapılandırma](/azure/active-directory/enterprise-users/groups-settings-cmdlets)