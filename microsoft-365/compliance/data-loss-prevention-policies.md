---
title: Veri Kaybı Önleme Başvurusu
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: ''
ms.collection:
- M365-security-compliance
- SPO_Content
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ROBOTS: NOINDEX, NOFOLLOW
feedback_system: None
description: veri kaybı önleme başvuru malzemesi
ms.openlocfilehash: 0c7fe1d3ccf1b74641be1d05506f1cc53b743218
ms.sourcegitcommit: bb493f12701f6d6ee7d5e64b541adb87470bc7bc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/18/2022
ms.locfileid: "63015504"
---
# <a name="data-loss-prevention-reference"></a>Veri kaybı önleme başvurusu

> [!IMPORTANT]
> Bu konu, artık veri kaybı önleme (DLP) Microsoft 365 ana kaynak değildir. DLP içerik kümesi güncelleştiriliyor ve yeniden yapılandır ediliyor. Bu makalede ele alan konular yeni, güncelleştirilmiş makalelere taşınacak. DLP hakkında daha fazla bilgi için bkz. [Veri kaybını önleme hakkında bilgi.](dlp-learn-about-dlp.md)

<!-- this topic needs to be split into smaller, more coherent ones. It is confusing as it is. -->
<!-- move this note to a more appropriate place, no topic should start with a note -->
> [!NOTE]
> Tek başına bir seçenek olarak kullanılabilen ve Microsoft Teams ve Office 365 Gelişmiş Uyumluluk lisansına sahip kullanıcılar için yeni sohbet ve kanal iletilerine veri kaybı önleme özellikleri Office 365 E5 Microsoft 365 E5 Uyumluluk. Lisans gereksinimleri hakkında daha fazla bilgi edinmek için [Lisanslama Microsoft 365 Tenant-Level'ne bakın](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance).



<!-- MOVED TO LEARN ABOUT To comply with business standards and industry regulations, organizations must protect sensitive information and prevent its inadvertent disclosure. Sensitive information can include financial data or personally identifiable information (PII) such as credit card numbers, social security numbers, or health records. With a data loss prevention (DLP) policy in the Office 365 Security &amp; Compliance Center, you can identify, monitor, and automatically protect sensitive information across Office 365.

With a DLP policy, you can:

- **Identify sensitive information across many locations, such as Exchange Online, SharePoint Online, OneDrive for Business, and Microsoft Teams.**

    For example, you can identify any document containing a credit card number that's stored in any OneDrive for Business site, or you can monitor just the OneDrive sites of specific people.

- **Prevent the accidental sharing of sensitive information**.

    For example, you can identify any document or email containing a health record that's shared with people outside your organization, and then automatically block access to that document or block the email from being sent.

- **Monitor and protect sensitive information in the desktop versions of Excel, PowerPoint, and Word.**

    Just like in Exchange Online, SharePoint Online, and OneDrive for Business, these Office desktop programs include the same capabilities to identify sensitive information and apply DLP policies. DLP provides continuous monitoring when people share content in these Office programs.

- **Help users learn how to stay compliant without interrupting their workflow.**

    You can educate your users about DLP policies and help them remain compliant without blocking their work. For example, if a user tries to share a document containing sensitive information, a DLP policy can both send them an email notification and show them a policy tip in the context of the document library that allows them to override the policy if they have a business justification. The same policy tips also appear in Outlook on the web, Outlook, Excel, PowerPoint, and Word.

- **View DLP alerts and reports showing content that matches your organization’s DLP policies.**

    To view alerts and metadata related to your DLP policies you can use the [DLP Alerts Management Dashboard](dlp-configure-view-alerts-policies.md). You can also view policy match reports to assess how your organization is complying with a DLP policy. If a DLP policy allows users to override a policy tip and report a false positive, you can also view what users have reported

-->
## <a name="create-and-manage-dlp-policies"></a>DLP ilkelerini oluşturma ve yönetme

DLP ilkelerini, Uyumluluk Merkezi'nde Veri kaybı önleme sayfasında Microsoft 365 yönetirsiniz.

![Uyumluluk Merkezi'nde veri Office 365 önleme &amp; sayfası.](../media/943fd01c-d7aa-43a9-846d-0561321a405e.png)

<!-- MOVED TO LEARN ABOUT ## What a DLP policy contains

A DLP policy contains a few basic things:

- Where to protect the content: **locations** such as Exchange Online, SharePoint Online, and OneDrive for Business sites, as well as Microsoft Teams chat and channel messages.

- When and how to protect the content by enforcing **rules** comprised of:

  - **Conditions** the content must match before the rule is enforced. For example, a rule might be configured to look only for content containing Social Security numbers that's been shared with people outside your organization.

  - **Actions** that you want the rule to take automatically when content matching the conditions is found. For example, a rule might be configured to block access to a document and send both the user and compliance officer an email notification.

You can use a rule to meet a specific protection requirement, and then use a DLP policy to group together common protection requirements, such as all of the rules needed to comply with a specific regulation.

For example, you might have a DLP policy that helps you detect the presence of information subject to the Health Insurance Portability and Accountability Act (HIPAA). This DLP policy could help protect HIPAA data (the what) across all SharePoint Online sites and all OneDrive for Business sites (the where) by finding any document containing this sensitive information that's shared with people outside your organization (the conditions) and then blocking access to the document and sending a notification (the actions). These requirements are stored as individual rules and grouped together as a DLP policy to simplify management and reporting.

![Diagram shows that DLP policy contains locations and rules.](../media/c006860c-2d00-42cb-aaa4-5b5638d139f7.png) -->

<!-- MOVED TO LEARN ABOUT ### Locations

DLP policies are applied to sensitive items across Microsoft 365 locations and can be further scoped as detailed in this table.


|Location | Include/exclude by|
|---------|---------|
|Exchange email| distribution groups|
|SharePoint sites |sites |
|OneDrive accounts |accounts |
|Teams chat and channel messages |accounts |
|Windows 10 devices |user or group |
|Microsoft Cloud App Security |instance |
 -->

<!-- moved to dlp-policy-reference.md
If you choose to include specific distribution groups in Exchange, the DLP policy will be scoped only to the members of that group. Similarly excluding a distribution group will exclude all the members of that distribution group from policy evaluation. You can choose to scope a policy to the members of distribution lists, dynamic distribution groups, and security groups. A DLP policy can contain no more than 50 such inclusions and exclusions.

If you choose to include or exclude specific SharePoint sites, a DLP policy can contain no more than 100 such inclusions and exclusions. Although this limit exists, you can exceed this limit by applying either an org-wide policy or a policy that applies to entire locations.

If you choose to include or exclude specific OneDrive accounts or groups, a DLP policy can contain no more than 100 user accounts or 50 groups as inclusion or exclusion.

### Rules

> [!NOTE]
> The default behavior of a DLP policy, when there is no alert configured, is not to alert or trigger. This applies only to default information types. For custom information types, the system will alert even if there is no action defined in the policy.

Rules are what enforce your business requirements on your organization's content. A policy contains one or more rules, and each rule consists of conditions and actions. For each rule, when the conditions are met, the actions are taken automatically. Rules are executed sequentially, starting with the highest-priority rule in each policy.

A rule also provides options to notify users (with policy tips and email notifications) and admins (with email incident reports) that content has matched the rule.

Here are the components of a rule, each explained below.

![Sections of the DLP rule editor.](../media/1859d504-b9c2-45ed-961b-a0092251acc2.png)

#### Conditions

Conditions are important because they determine what types of information you're looking for, and when to take an action. For example, you might choose to ignore content containing passport numbers unless the content contains more than 10 such numbers and is shared with people outside your organization.

Conditions focus on the **content**, such as what types of sensitive information you're looking for, and also on the **context**, such as who the document is shared with. You can use conditions to assign different actions to different risk levels. For example, sensitive content shared internally might be lower risk and require fewer actions than sensitive content shared with people outside the organization.

![List showing available DLP conditions.](../media/0fa43f90-d007-4506-ae93-43e8424fe103.png)

The conditions now available can determine if:

- Content contains a type of sensitive information.

- Content contains a label. For more information, see the below section [Using a retention label as a condition in a DLP policy](#using-a-retention-label-as-a-condition-in-a-dlp-policy).

- Content is shared with people outside or inside your organization.

  > [!NOTE]
  > Users who have non-guest accounts in a host organization's Active Directory or Azure Active Directory tenant are considered as people inside the organization.

#### Types of sensitive information

A DLP policy can help protect sensitive information, which is defined as a **sensitive information type**. Microsoft 365 includes definitions for many common sensitive information types across many different regions that are ready for you to use, such as a credit card number, bank account numbers, national ID numbers, and passport numbers.

![List of available sensitive information types.](../media/3eaa9911-bc94-44be-902f-363dbf3b07fe.png)

When a DLP policy looks for a sensitive information type such as a credit card number, it doesn't simply look for a 16-digit number. Each sensitive information type is defined and detected by using a combination of:

- Keywords.

- Internal functions to validate checksums or composition.

- Evaluation of regular expressions to find pattern matches.

- Other content examination.

This helps DLP detection achieve a high degree of accuracy while reducing the number of false positives that can interrupt peoples' work.

#### Actions

When content matches a condition in a rule, you can apply actions to automatically protect the content.

![List of available DLP actions.](../media/8aef17fc-1e99-4ac7-adfc-0f2c9c1a0697.png)

With the actions now available, you can:

- **Restrict access to the content** Depending on your need, you can restrict access to content in three ways:

  1. Restrict access to content for everyone.
  2. Restrict access to content for people outside the organization.
  3. Restrict access to "Anyone with the link."

  For site content, this means that permissions for the document are restricted for everyone except the primary site collection administrator, document owner, and person who last modified the document. These people can remove the sensitive information from the document or take other remedial action. When the document is in compliance, the original permissions are automatically restored. When access to a document is blocked, the document appears with a special policy tip icon in the library on the site.

  ![Policy tip showing access to document is blocked.](../media/b6cefed3-d212-43d7-8534-4b92b26ebd50.png)

  For email content, this action blocks the message from being sent. Depending on how the DLP rule is configured, the sender sees an NDR or (if the rule uses a notification) a policy tip and/or email notification.

  ![Warning that unauthorized recipients must be removed from the message.](../media/302f9994-912d-41e7-861f-8a4539b3c285.png)

#### User notifications and user overrides

You can use notifications and overrides to educate your users about DLP policies and help them remain compliant without blocking their work. For example, if a user tries to share a document containing sensitive information, a DLP policy can both send them an email notification and show them a policy tip in the context of the document library that allows them to override the policy if they have a business justification.

![User notifications and user overrides sections of DLP rule editor.](../media/37b560d4-6e4e-489e-9134-d4b9daf60296.png)

The email can notify the person who sent, shared, or last modified the content and, for site content, the primary site collection administrator and document owner. In addition, you can add or remove whomever you choose from the email notification.

In addition to sending an email notification, a user notification displays a policy tip:

- In Outlook and Outlook on the web.

- For the document on a SharePoint Online or OneDrive for Business site.

- In Excel, PowerPoint, and Word, when the document is stored on a site included in a DLP policy.

The email notification and policy tip explain why content conflicts with a DLP policy. If you choose, the email notification and policy tip can allow users to override a rule by reporting a false positive or providing a business justification. This can help you educate users about your DLP policies and enforce them without preventing people from doing their work. Information about overrides and false positives is also logged for reporting (see below about the DLP reports) and included in the incident reports (next section), so that the compliance officer can regularly review this information.

Here's what a policy tip looks like in a OneDrive for Business account.

![Policy tip for a document in a OneDrive account.](../media/f9834d35-94f0-4511-8555-0fe69855ce6d.png)

 To learn more about user notifications and policy tips in DLP policies, see [Use notifications and policy tips](use-notifications-and-policy-tips.md).

#### Alerts and Incident reports

When a rule is matched, you can send an alert email to your compliance officer (or any person(s) you choose) with details of the alert. This alert email will carry a link of the [DLP Alerts Management Dashboard](dlp-configure-view-alerts-policies.md) which the compliance officer can go to view the details of alert and events. The dashboard contains details of the event that triggered the alert along with details of the DLP policy matched and the sensitive content detected.

In addition, you can also send an incident report with details of the event. This report includes information about the item that was matched, the actual content that matched the rule, and the name of the person who last modified the content. For email messages, the report also includes as an attachment the original message that matches a DLP policy.

> [!div class="mx-imgBorder"]
> ![Page for configuring incident reports.](../media/Alerts-and-incident-report.png)

DLP scans email differently from items in SharePoint Online or OneDrive for Business. In SharePoint Online and OneDrive for Business, DLP scans existing items as well as new ones and generates an alert and incident report whenever a match is found. In Exchange Online, DLP only scans new email messages and generates a report if there is a policy match. DLP ***does not*** scan or match previously existing email items that are stored in a mailbox or archive.

## Grouping and logical operators

Often your DLP policy has a straightforward requirement, such as to identify all content that contains a U.S. Social Security Number. However, in other scenarios, your DLP policy might need to identify more loosely defined data.

For example, to identify content subject to the U.S. Health Insurance Act (HIPAA), you need to look for:

- Content that contains specific types of sensitive information, such as a U.S. Social Security Number or Drug Enforcement Agency (DEA) Number.

    AND

- Content that's more difficult to identify, such as communications about a patient's care or descriptions of medical services provided. Identifying this content requires matching keywords from very large keyword lists, such as the International Classification of Diseases (ICD-9-CM or ICD-10-CM).

You can easily identify such loosely defined data by using grouping and logical operators (AND, OR). When you create a DLP policy, you can:

- Group sensitive information types.

- Choose the logical operator between the sensitive information types within a group and between the groups themselves.

### Choosing the operator within a group

Within a group, you can choose whether any or all of the conditions in that group must be satisfied for the content to match the rule.

![Group showing the operators within the group.](../media/6a12f1e8-112d-48ee-9a73-82b3dd0542e7.png)

### Adding a group

You can quickly add a group, which can have its own conditions and operator within that group.

![Add group button.](../media/5f72f292-d1f3-4f11-a911-a9f71e10abf6.png)

### Choosing the operator between groups

Between groups, you can choose whether the conditions in just one group or all of the groups must be satisfied for the content to match the rule.

For example, the built-in **U.S. HIPAA** policy has a rule that uses an **AND** operator between the groups so that it identifies content that contains:

- from the group **PII Identifiers** (at least one SSN number **OR** DEA number)

    **AND**

- from the group **Medical Terms** (at least one ICD-9-CM keyword **OR** ICD-10-CM keyword)

![Groups showing the operator between groups.](../media/354aa77f-569c-4847-9dfe-605ee2bb28d1.png)

## The priority by which rules are processed

When you create rules in a policy, each rule is assigned a priority in the order in which it's created — meaning, the rule created first has first priority, the rule created second has second priority, and so on.

> [!div class="mx-imgBorder"]
> ![Rules in priority order.](../media/dlp-rules-in-priority-order.png)

After you have set up more than one DLP policy, you can change the priority of one or more policies. To do that, select a policy, choose **Edit policy**, and use the **Priority** list to specify its priority.

> [!div class="mx-imgBorder"]
> ![Set priority for a policy.](../media/dlp-set-policy-priority.png)

When content is evaluated against rules, the rules are processed in priority order. If content matches multiple rules, the rules are processed in priority order and the most restrictive action is enforced. For example, if content matches all of the following rules, Rule 3 is enforced because it's the highest priority, most restrictive rule:

- Rule 1: only notifies users

- Rule 2: notifies users, restricts access, and allows user overrides

- Rule 3: notifies users, restricts access, and does not allow user overrides

- Rule 4: only notifies users

- Rule 5: restricts access

- Rule 6: notifies users, restricts access, and does not allow user overrides

In this example, note that matches for all of the rules are recorded in the audit logs and shown in the DLP reports, even though only the most restrictive rule is enforced.

Regarding policy tips, note that:

- Only the policy tip from the highest priority, most restrictive rule will be shown. For example, a policy tip from a rule that blocks access to content will be shown over a policy tip from a rule that simply sends a notification. This prevents people from seeing a cascade of policy tips.

- If the policy tips in the most restrictive rule allow people to override the rule, then overriding this rule also overrides any other rules that the content matched.

-->

## <a name="tuning-rules-to-make-them-easier-or-harder-to-match"></a>Kuralların eşleşmelerini kolaylaştıracak veya zorlaştıracak şekilde ayarlama

Kişiler kendi DLP ilkelerini oluşturduklarından ve bu ilkeleri oluşturduklarından sonra, bazen şu sorunlar ile yüzleri ortaya atlar:

- Hassas bilgilerle **çok fazla içerik** kuralla eş, başka bir deyişle çok fazla yanlış pozitif sonuç var.

- Hassas bilgiler **kurallarla çok** az eşleşmeye neden olur. Başka bir deyişle, hassas bilgiler üzerinde koruyucu eylemler zorunlu kılınmaz.

Bu sorunları ele etmek için, içeriğin kurallarla eşleşmeyi zorlaştıracak veya kolaylaştıracak şekilde örnek sayısını ve doğruluğunu ayarlayarak kurallarınızı düzeltebilirsiniz. Bir kuralda kullanılan her hassas bilgi türünün, bir örneği sayısı ve doğruluk oranı vardır.

### <a name="instance-count"></a>Örnek sayısı

Örnek sayısı, yalnızca içeriğin kuralla eşleşmesi için belirli bir tür hassas bilgiden kaç kez yine olması gerektiğini ifade ediyor. Örneğin, benzersiz 1 ABD veya İngiltere ile 9 arasında ise, içerik aşağıdaki kuralla eşlenmiştir. pasaport numaraları tanımlanır.

> [!NOTE]
> Örnek sayısı yalnızca hassas bilgi **türleri** ve anahtar sözcükler için benzersiz eşleşmeleri içerir. Örneğin, e-postada aynı kredi kartı numarasının 10 tekrarı varsa, bu 10 tekrar, bir kredi kartı numarasının tek örneği olarak sayılır.

Kural ayarlamak üzere örnek sayısını kullanmak için, kılavuz açık bir şekilde anlaşılır:

- Kuralın eşleşmeyi kolaylaştırmak için, dakika sayısını **azaltarak** ve/veya en yüksek **s sayımı** artırarak. Sayısal değeri **silerek de** **herhangi bir en** büyük değere ayarlayabilirsiniz.

- Kuralın eşleşmeyi zorlaştırması için, **min sayısını** artırarak.

Normalde, daha düşük örnek sayısına sahip bir kuralda (örneğin, 1-9) kullanıcı bildirimleri gönderme gibi daha az kısıtlayıcı eylemler kullanırsınız. Daha yüksek örnek sayısına (örneğin, 10-any) sahip bir kuralda, kullanıcı geçersiz kılmalarına izin vermeden içeriğe erişimi kısıtlama gibi daha kısıtlayıcı eylemler kullanırsınız.

![Kural düzenleyicisinde örnek sayıları yer almaktadır.](../media/e7ea3c12-72c5-4bb3-9590-c924c665e84d.png)

### <a name="match-accuracy"></a>Eşleşme doğruluğu

Yukarıda da açıklandığı gibi, hassas bir bilgi türü farklı kanıt türleri birleşimi kullanılarak tanımlanır ve algılanır. Yaygın olarak, hassas bir bilgi türü desen adı verilen bu tür birden çok bileşim tarafından tanımlanır. Daha az kanıt gerektiren bir düzenin daha düşük bir eşleşme doğruluğu (veya güven düzeyi) varken, daha fazla kanıt gerektiren bir düzenin daha yüksek bir eşleşme doğruluğu (veya güven düzeyi) vardır. Her hassas bilgi türü tarafından kullanılan gerçek kalıplar ve güven düzeyleri hakkında daha fazla bilgi edinmek için bkz [. Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md).

Örneğin, Kredi Kartı Numarası adlı hassas bilgi türü iki modelle tanımlanır:

- %65 güven gerektiren bir desen:

  - Kredi kartı numarası biçimindeki bir numara.

  - Denetim toplamdan geçen bir sayıdır.

- %85 güven gerektiren bir desen:

  - Kredi kartı numarası biçimindeki bir numara.

  - Denetim toplamdan geçen bir sayıdır.

  - Doğru biçimde bir anahtar sözcük veya son kullanma tarihi.

Kurallarınız içinde bu güven düzeylerini (veya doğruluğu) kullanabilirsiniz. Normalde, daha düşük eşleşme doğruluğuna sahip bir kuralda kullanıcı bildirimleri gönderme gibi daha az kısıtlayıcı eylemler kullanırsınız. Ayrıca, daha yüksek eşleşme doğruluğuna sahip bir kuralda, kullanıcı geçersiz kılmalarına izin vermeden içeriğe erişimi kısıtlama gibi daha kısıtlayıcı eylemler kullanırsiniz.

İçerikte kredi kartı numarası gibi belirli türde hassas bilgiler tanım olduğunda, yalnızca tek bir güven düzeyi döndürülecek olması önemlidir:

- Eşleşmelerin hepsi tek bir desene göre ise, bu desenin güven düzeyi döndürülür.

- Birden fazla desende eşleşme varsa (yani, iki farklı güven düzeyiyle eşleşmeler vardır), tek başına tek kalıplardan herhangi birinin üzerinde bir güven düzeyi döndürülür. Bu biraz karmaşık bir bölüm. Örneğin, kredi kartı için hem %65 hem de %85 düzeni eşlediyse, bu hassas bilgi türü için döndürülen güven düzeyi %90'dan büyüktür çünkü daha fazla kanıt daha fazla güven anlamına gelir.

Dolayısıyla, kredi kartları için biri %65'inde eşleşme doğruluğu, biri de %85'inde eşleşme doğruluğu için olmak istediğiniz iki özel kural oluşturmak için, eşleşme doğruluğuna uygun aralıklar aşağıdakine benzer olur. İlk kural yalnızca %65 deseninin eşleşmelerini alır. İkinci kural en az %85 eşleşmeyle  eşleşmeleri seçer ve başka daha düşük güveni  olan eşleşmeler de olabilir.

![Eşleşme doğruluğu için farklı aralıklara sahip iki kural.](../media/21bdfe36-7a91-4347-8098-11809a92f9a4.png)

Bu nedenlerle, farklı eşleşmelere sahip kurallar oluşturma konusunda yol gösterici kurallar aşağıdakitir:

- En düşük güven düzeyi normalde en düşük ve en yüksek değer **(aralık için** **değil** ) için aynı değeri kullanır.

- En yüksek güven düzeyi genellikle, düşük güven düzeyinin hemen üstünde olan ve 100 olan bir aralıktır.

- Güven düzeyleri arasındaki herhangi bir in-between genel olarak, düşük güven düzeyinin hemen üstünden hemen sonra, daha yüksek güven düzeyinin hemen altına doğru sıralanmıştır.

## <a name="using-a-retention-label-as-a-condition-in-a-dlp-policy"></a>DLP ilkesinde bir bekletme etiketini koşul olarak kullanma

Daha önce oluşturulmuş ve yayımlanmış bir [bekletme etiketini](retention.md#retention-labels) bir DLP ilkesinde koşul olarak kullanırken, dikkatmesi gereken bazı şeyler vardır:

- Bekletme etiketinin, DLP ilkesinde bir koşul olarak kullanmayı denemeden önce oluşturulmuş ve yayımlanmış olması gerekir.
- Yayımlanmış bekletme etiketlerinin eşitlemesi bir ile yedi gün arasında zaman alabiliyor. Daha fazla bilgi için bkz[](create-apply-retention-labels.md#when-retention-labels-become-available-to-apply). Bekletme ilkesinde yayımlanan bekletme etiketleri için bekletme etiketleri ne zaman kullanılabilir hale geldiğinde ve otomatik [](apply-retention-labels-automatically.md#how-long-it-takes-for-retention-labels-to-take-effect) olarak yayımlanan bekletme etiketlerinin geçerlik olması bekletme etiketlerinin ne kadar sürer?
- **İlkede bekletme etiketi kullanmak yalnızca **'daki ve SharePoint öğeleri OneDrive***.

  ![Koşul olarak etiketler.](../media/5b1752b4-a129-4a88-b010-8dcf8a38bb09.png)

  Bekletme ve disposition altında olan öğeleriniz varsa ve ayrıca onlara başka denetimler uygulamak istiyorsanız, DLP ilkesinde bir bekletme etiketi kullanmak istiyor olabileceğiniz gibi, örneğin:

  - **2018** vergi yılı olarak adlandırılmış bir bekletme etiketi yayımladıniz. Bu etiket, SharePoint'de depolanan vergi belgelerine uygulandığında 10 yıl süreyle depolanmış ve sonra bunları atacak. Ayrıca, bu öğelerin kuruluş dışında paylaşılmalarını da istemiyorsunuz. Bunu bir DLP ilkesiyle de yapabiliriz.

  > [!IMPORTANT]
  > Bir bekletme etiketini DLP ilkesinde koşul olarak belirtir ve konum olarak da Exchange ve/veya Teams belirtirseniz bu hatayı alırsınız: "E-posta ve ekip iletilerinde etiketli içeriğin korunması **desteklenmiyor. Aşağıdaki etiketi kaldırın ya da Konum olarak Exchange'Teams kapatın."** Çünkü aktarım, Exchange gönderme ve teslim sırasında etiket meta verilerini değerlendirmez.

### <a name="using-a-sensitivity-label-as-a-condition-in-a-dlp-policy"></a>Duyarlılık etiketini DLP ilkesinde koşul olarak kullanma

[DLP ilkelerde](./dlp-sensitivity-label-as-condition.md) duyarlılık etiketini bir koşul olarak kullanma hakkında daha fazla bilgi edinmek için:

### <a name="how-this-feature-relates-to-other-features"></a>Bu özelliğin diğer özelliklerle olan ilişkilendirmesi

Hassas bilgiler içeren içeriğe çeşitli özellikler uygulanabilir:

- Bir [bekletme etiketi ve bekletme ilkesi, bu](retention.md) içerikte **bekletme** eylemlerini zorunlu bulundurabilirsiniz.

- DLP ilkesi, bu içerik **üzerinde** koruma eylemlerini zorunlu bulundurabilirsiniz. Bu eylemleri zorlamadan önce, etiket içeren içeriğe ek olarak bir DLP ilkesi de başka koşulların karşılandır gerektirir.

![Hassas bilgilere uygulanabilecek özellikler diyagramı.](../media/dd410f97-a3a3-455c-a1e9-7ed8ae6893d6.png)

DLP ilkesi, hassas bilgilere uygulanan etiket veya bekletme ilkesinden daha zengin bir algılama özelliğine sahiptir. DLP ilkesi, hassas bilgiler içeren içerik üzerinde koruyucu eylemleri zorunlu kılınır ve hassas bilgiler içerikten kaldırılırsa, içeriğin bir sonraki tarandığında bu koruyucu eylemler geri alınır. Ancak hassas bilgiler içeren içeriğe bir bekletme ilkesi veya etiket uygulanırsa, bu hassas bilgiler kaldırılmış olsa bile geri alınmayacak bir defalık bir eylemdir.

Bir etiketi bir DLP ilkesinde koşul olarak kullanarak, bu etiketle içerik üzerinde hem bekletme hem de koruma eylemlerini zorunlu kılınabilirsiniz. İçeriğin, hassas bilgiler içeren içeriklere tam olarak benzer olduğunu düşünebilirsiniz; hem etiket hem de hassas bilgi türü içeriği sınıflandırmak için kullanılan özelliklerdir; dolayısıyla bu içerik üzerinde eylem gerçekleştirebilirsiniz.

![Bir koşul olarak etiket kullanan DLP ilkesi diyagramı.](../media/4538fd8f-fb74-4743-bc22-a5de33adfebb.png)

## <a name="simple-settings-vs-advanced-settings"></a>Basit ayarlar ve gelişmiş ayarlar

Bir DLP ilkesi  oluşturmak için, basit veya gelişmiş ayarlar arasında seçim yapabilirsiniz:

- **Basit ayarlar** , kuralları oluşturmak veya değiştirmek için kural düzenleyicisini kullanmadan en yaygın DLP ilkesi türünü oluşturmanızı kolaylaştırır.

- **Gelişmiş ayarlar** , DLP ilkenizin tüm ayarları üzerinde tam denetim vermek için kural düzenleyicisini kullanır.

Merak etmeyin, basit ayarların ve gelişmiş ayarların tamamen aynı şekilde çalışması için, yalnızca basit ayarlarla kural ve eylemlerden oluşan kuralların zorlanması nedeniyle kural düzenleyicisini görmüyoruz. Bu, DLP ilkesi oluşturmanın hızlı bir yolutur.

### <a name="simple-settings"></a>Basit ayarlar

En yaygın DLP senaryosu, hassas bilgiler içeren içeriğin kuruluş dışındaki kullanıcılarla paylaşılmasını korumaya yardımcı olacak bir ilke oluşturmak ve içeriğe kimlerin eriş erişeni kısıtlama, son kullanıcı veya yönetici bildirimlerini gönderme ve daha sonra araştırılacak olayı denetleme gibi otomatik bir düzeltme eyleminin yer aldığı bir ilke oluşturmaktır. Kişiler DLP'i, hassas bilgilerin istemeden açıklanmasını önlemeye yardımcı olmak için kullanır.

Bu hedefe ulaşmayı basitleştirmek için, bir DLP ilkesi 2013'e kadar **olanda Basit ayarları kullan'ı seçebilirsiniz**. Bu ayarlar, kural düzenleyicisine gitmek zorunda kalmadan en yaygın DLP İlkesini uygulamak için ihtiyacınız olan her şeyi sağlar.

![Basit ve gelişmiş ayarlar için DLP seçenekleri.](../media/33c93824-ead5-43b6-9c3e-fd1630c92a7d.png)

### <a name="advanced-settings"></a>Gelişmiş ayarlar

Daha özelleştirilmiş DLP ilkeleri oluşturmanız gerekirse, Gelişmiş ayarları **kullan'ı seçebilirsiniz**.

Gelişmiş ayarlar, her kuralın örnek sayısı ve eşleşme doğruluğu (güven düzeyi) dahil olmak üzere tüm olası seçenekler üzerinde tam denetime sahip olduğunuz kural düzenleyicisini size sunar.

Bir bölüme hızla atlamak için, kural düzenleyicisinin üst gezinti bölmesinde bir öğeye tıklayıp aşağıdaki bölüme gidin.

![DLP kuralı düzenleyicisinin üst gezinti menüsü.](../media/c527b97f-ca53-4c79-ad19-1a63be8a8ecc.png)

## <a name="dlp-policy-templates"></a>DLP ilkesi şablonları

DLP ilkesi oluşturmanın ilk adımı, hangi bilgilerin korunmasını seçmektir. Bir DLP şablonuyla başlayarak, sıfırdan yeni bir dizi kural oluşturma ve varsayılan olarak hangi tür bilgilerin dahil olması gerektiğini anlama çalışmalarını kaydetebilirsiniz. Daha sonra kuralın belirli gereksinimlerini karşılayacak şekilde ayarlamalar yapmak için bu gereksinimleri ekleyebilir veya değiştirebilirsiniz.

Önceden yapılandırılmış bir DLP ilkesi şablonu HIPAA verileri, PCI-DSS verileri, Gramm-Leach-Bliley Act verileri, hatta yerel ayara özgü kişisel bilgileri (P.I.) gibi belirli tür hassas bilgileri algılamanıza yardımcı olabilir. Sık kullanılan hassas bilgi türlerini kolayca bulmanı ve korumayı kolaylaştırmaya yardımcı olmak için, Microsoft 365 ilke şablonları zaten sizin için gerekli olan en yaygın hassas bilgi türlerini içerir.

![ABD için şablonda odaklanan veri kaybı önleme ilkeleri için şablonların listesi. Act.](../media/791b2403-430b-4987-8643-cc20abbd8148.png)

Ayrıca, kuruma ait belirli gereksinimler olabilir. Bu durumda Özel ilke seçeneğini kullanarak sıfırdan bir DLP **ilkesi oluşturabilirsiniz** . Özel ilke boştur ve önceden kuralı yoktur.

<!-- ## Roll out DLP policies gradually with test mode

rehomed to Plan for DLP

When you create your DLP policies, you should consider rolling them out gradually to assess their impact and test their effectiveness before fully enforcing them. For example, you don't want a new DLP policy to unintentionally block access to thousands of documents that people require access to in order to get their work done.

If you're creating DLP policies with a large potential impact, we recommend following this sequence:

1. **Start in test mode without Policy Tips** and then use the DLP reports and any incident reports to assess the impact. You can use DLP reports to view the number, location, type, and severity of policy matches. Based on the results, you can fine tune the rules as needed. In test mode, DLP policies will not impact the productivity of people working in your organization.

2. **Move to Test mode with notifications and Policy Tips** so that you can begin to teach users about your compliance policies and prepare them for the rules that are going to be applied. At this stage, you can also ask users to report false positives so that you can further refine the rules.

3. **Start full enforcement on the policies** so that the actions in the rules are applied and the content's protected. Continue to monitor the DLP reports and any incident reports or notifications to make sure that the results are what you intend.

    ![Options for using test mode and turning on policy.](../media/49fafaac-c6cb-41de-99c4-c43c3e380c3a.png)

    You can turn off a DLP policy at any time, which affects all rules in the policy. However, each rule can also be turned off individually by toggling its status in the rule editor.

    ![Options for turning off a rule in a policy.](../media/f7b258ff-1b8b-4127-b580-83c6492f2bef.png)

    You can also change the priority of multiple rules in a policy. To do that, open a policy for editing. In a row for a rule, choose the ellipses (**...**), and then choose an option, such as **Move down** or **Bring to last**.

    > [!div class="mx-imgBorder"]
    > ![Set rule priority.](../media/dlp-set-rule-priority.png)-->

## <a name="dlp-reports"></a>DLP raporları

DLP ilkelerinizi oluşturduk ve bu ilkeleri oluşturdukktan sonra, bunların istediğiniz gibi çalıştığını doğrulamak ve uyumlu kalmanıza yardımcı olmak istemeniz gerekir. DLP raporlarıyla, zaman içinde DLP ilkesi ve kuralı eşleşmelerinin sayısını, hatalı pozitif sonuç ve geçersiz kılma sayısını hızlı şekilde görüntüabilirsiniz. Her raporda bu eşleşmeleri konuma, zaman çerçevesine göre filtresini oluşturabilir ve hatta belirli bir ilke, kural veya eyleme göre daraltabilirsiniz.

DLP raporlarıyla iş içgörüleri elde edin ve:

- Belirli zaman dönemleri üzerinde odaklanın ve depolar ile eğilimlerin nedenlerini an edin.

- Kuruluş uyumluluk ilkelerini ihlal eden iş süreçleri keşfedin.

- DLP ilkelerinin ticari etkisini anlıyoruz.

Buna ek olarak, DLP ilkelerini siz çalıştıracak şekilde ince ayar yapmak için DLP raporlarını kullanabilirsiniz.

![Güvenlik ve Uyumluluk Merkezi'nde Raporlar Panosu.](../media/6d741252-a0ce-4429-95ba-6c857ecc9a7e.png)

## <a name="how-dlp-policies-work"></a>DLP ilkeleri nasıl çalışır?

DLP, hassas bilgileri yalnızca basit bir metin taraması değil, derin içerik çözümlemesi kullanarak algılar. Bu derin içerik çözümlemesi, DLP ilkelerinize uygun içeriği algılamak için anahtar sözcük eşleşmelerini, sözlük eşleşmelerini, normal ifadeleri değerlendirmeyi, iç işlevleri ve diğer yöntemleri kullanır. Verilerinizin yalnızca küçük bir yüzdesi hassas olarak kabul edilir. DLP ilkesi, içeriğinizin geri kalanıyla çalışan verileri etkilemeden veya bu verileri etkilemeden yalnızca bu verileri tanımlayabilir, izleyebilir ve otomatik olarak koruyabilir.

### <a name="policies-are-synced"></a>İlkeler eşitlenen

Güvenlik Uyumluluk Merkezi'nde bir DLP &amp; ilkesi oluşturduklarından sonra, bu ilke merkezi bir ilke deposuna depolanır ve sonra aşağıdakiler gibi çeşitli içerik kaynaklarıyla eşitlenen:

- Exchange Online ve buradan da Web üzerinde Outlook ve Outlook.

- OneDrive İş sitelerini ziyaret edin.

- SharePoint Online siteleri.

- Office programlarını (Excel, PowerPoint Ve Word) kullanın.

- Microsoft Teams ve sohbet iletilerini gönderme.

İlke doğru konumlara eşitledikten sonra, içeriği değerlendirmeye ve eylemleri uygulamaya başlar.
<!-- what is the time delay for first deployment of a policy and what is the sync schedule? -->

### <a name="policy-evaluation-in-onedrive-for-business-and-sharepoint-online-sites"></a>Çevrimiçi sitelerde OneDrive İş ilke SharePoint değerlendirme

tüm SharePoint Online siteleriniz ve tüm OneDrive İş, belgeler sürekli değişiyor; bunlar sürekli olarak oluşturulmuş, düzenlenmiş, paylaşılıyor, gibi. Bu da, belgelerin herhangi bir zamanda çakış, DLP ilkesiyle uyumlu hale geldiğini ifade ediyor. Örneğin, bir kişi hassas bilgiler içeren bir belgeyi ekip sitesine yükleyebilir, ancak daha sonra farklı bir kişi aynı belgeyi düzenleyebilir ve ona hassas bilgiler ekleyebilir.

Bu nedenle, DLP ilkeleri, belgeleri ilke eşleşmeleri için sık sık arka planda kontrol eder. Bunu zaman uyumsuz ilke değerlendirmesi olarak düşünesiniz.
<!-- what is the frequency? looks like it is tied to the search crawl schedule -->

#### <a name="how-it-works"></a>Nasıl çalışır?

kişiler sitelerine belge ekley ettiyken veya sitelerinde değişiklik yaptıklarında, arama motoru içeriği tarar, böylece daha sonra arayabilirsiniz. Bu durum devam ederken, içerik hassas bilgileri de taranmış ve paylaşılıyor olup değildir. Bulunan tüm hassas bilgiler arama dizininde güvenli bir şekilde depolanır, böylece yalnızca uyumluluk ekibi bu bilgilere erişebilirsiniz ancak normal kullanıcılar erişemz. Açık olan her DLP ilkesi arka planda çalışır (zaman uyumsuz), bir ilkeyle eşleşen içerikleri sık sık denetleme ve yanlışlıkla sızdırılan sızıntılardan korumak için eylemleri uygulama.

![DLP ilkesi içeriği zaman uyumsuz olarak nasıl değerlendirirken gösterilen diyagram.](../media/bdf73099-039a-4909-ae89-ac12c41992ba.png)

<!-- conflict with a DLP policy is bad wording -->
Son olarak, belgeler DLP ilkesiyle çakışsa da, DLP ilkesiyle uyumlu da olabilir. Örneğin, bir kişi bir belgeye kredi kartı numaraları ekliyorsa, DLP ilkesi belgenin erişimini otomatik olarak engellemeye neden olabilir. Ancak bu kişi hassas bilgileri daha sonra kaldırırsa, belgenin ilkeye göre bir sonraki değerlendirilmesinde bu eylem (bu durumda engelleme) otomatik olarak geri alınır.

DLP, dizine alın diğer tüm içeriği değerlendirir. Hangi dosya türlerinde varsayılan olarak gezinilenler hakkında daha fazla bilgi için bkz. SharePoint Server'da varsayılan gezinilen dosya adı uzantıları [ve ayrıştırıldı dosya türleri](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types).

> [!NOTE]
> DLP ilkeleri belgeleri çözümleme fırsatına sahip olmadan belgelerin paylaşılmasını önlemek için, SharePoint'de yeni dosyaların paylaşımı içeriği dizine alana kadar engellenebilir. Ayrıntılı bilgi [için Bkz. Yeni dosyaları varsayılan olarak hassas](/sharepoint/sensitive-by-default) olarak işaretleme.

### <a name="policy-evaluation-in-exchange-online-outlook-and-outlook-on-the-web"></a>Çalışma, Exchange Online, Outlook ve ilke Web üzerinde Outlook

Konum olarak Exchange Online içeren bir DLP ilkesi seniz, ilke Office 365 &amp; Güvenlik Uyumluluk Merkezi'nde Exchange Online'den Exchange Online'e ve Web üzerinde Outlook Outlook.

Bu E-postada bir ileti Outlook, oluşturulan içerik DLP ilkelerine göre değerlendirildi olarak kullanıcı ilke ipuçlarını görebilir. Bir ileti gönderildikten sonra da, posta akışının normal bir parçası olarak DLP ilkelerine karşı, ayrıca Exchange posta akış kuralları (aktarım kuralları olarak da bilinir) ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange</a> yönetim merkezinde oluşturulmuş DLP ilkeleri değerlendirilir. DLP ilkeleri hem iletiyi hem de tüm ekleri tarar.

### <a name="policy-evaluation-in-the-office-desktop-programs"></a>Office masaüstü programlarında ilke değerlendirme

<!-- same capability to identify sensitive information line conflates sensitive information types and such -->
Excel, PowerPoint Word'de hassas bilgileri tanımlama ve DLP ilkelerini SharePoint Online ve OneDrive İş olarak uygulama özellikleri vardır. Bu Office programları DLP ilkelerini doğrudan merkezi ilke mağazasından eşitler ve sonra kişiler DLP ilkesinde yer alan bir siteden açılan belgelerle açıldığında DLP ilkelerine karşı içeriği sürekli olarak değerlendirir.

Office'de DLP ilkesi değerlendirme, programların performansını veya içerik üzerinde çalışan kişilerin üretkenliğini etkilememek üzere tasarlanmıştır. Bu kişi büyük bir belge üzerinde çalışıyorsa veya kullanıcının bilgisayarı meşgulse, ilke ipucunın görünmesi birkaç saniye sürebilir.

### <a name="policy-evaluation-in-microsoft-teams"></a>E-Microsoft Teams'de ilke değerlendirme
 <!--what do you mean that it's synched to user accounts?  I thought DLP policies were applied to locations not users like sensitivity labels are  -->

Konum olarak kullanıcı Microsoft Teams içeren bir DLP ilkesi oluşturabilirsiniz, ilke Office 365 Güvenlik Uyumluluk &amp; Merkezi'nde kullanıcı hesaplarıyla, Microsoft Teams ve sohbet iletileriyle eşitler. DLP ilkelerinin nasıl yapılandırılana bağlı olarak, birisi bir sohbette veya kanal mesajında hassas bilgileri Microsoft Teams, ileti engellenmiş veya iptal edilebilir. Ayrıca, hassas bilgiler içeren ve konuklarla (dış kullanıcılar) paylaşılan belgeler de bu kullanıcılar için açılmaz. Daha fazla bilgi edinmek için [bkz. Veri kaybı önleme ve Microsoft Teams](dlp-microsoft-teams.md).

## <a name="permissions"></a>İzinler

Varsayılan olarak, Genel yöneticiler, Güvenlik yöneticileri ve Uyumluluk yöneticilerinin DLP ilkesi oluşturma ve uygulama erişimi olur. DLP ilkeleri oluşturacak diğer uyumluluk ekibinin üyelerinin Güvenlik Uyumluluk Merkezi'ne izni &amp; olmalıdır. Varsayılan olarak, Kiracı yöneticiniz &amp; bu konuma erişim sahibi olur ve uyumluluk görevlilerine ve diğer kullanıcılara, Kiracı yöneticisinin tüm izinlerini vermeden Güvenlik Uyumluluk Merkezi'ne erişim izni vetir. Bunu yapmak için şunları öneririz:

1. Grup içinde bir Microsoft 365 oluşturun ve uyumluluk yetkililerini ekleyin.

2. Güvenlik Uyumluluk Merkezi'nin **İzinler** sayfasında bir rol &amp; grubu oluşturun.

3. Rol grubunu oluştururken, Rol Seçin **bölümünü kullanarak** Rol Grubuna aşağıdaki rolü ekleyin: **DLP Uyumluluk Yönetimi**.

4. Daha önce **oluşturduğunuz** üye grubunu rol Microsoft 365 için Üye Seç bölümünü kullanın.

Ayrıca, Yalnızca Görüntüleme DLP Uyumluluk Yönetimi rolüne sahip olarak, DLP ilkelerine ve DLP raporlarına yalnızca görüntüleme ayrıcalıklarına sahip bir **rol grubu oluşturabilirsiniz** .

Daha fazla bilgi için bkz[. Kullanıcılara Uyumluluk Merkezi'Office 365 erişme izni verme](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).

Bu izinler yalnızca DLP ilkesi oluşturmak ve uygulamak için gereklidir. İlke zorlama için içeriğe erişim gerekli değildir.

## <a name="find-the-dlp-cmdlets"></a>DLP cmdlet'lerini bulma

Güvenlik Uyumluluk Merkezi cmdlet'lerinin çoğunu kullanmak &amp; için:

1. [Bağlan PowerShell Office 365 Uyumluluk &amp; Merkezi'ne bağlanın](/powershell/exchange/connect-to-scc-powershell).

2. Bu ilke ve [uyumluluk-dlp cmdlet'lerini kullanın](/powershell/module/exchange/export-dlppolicycollection).

Bununla birlikte, DLP raporlarının farklı verilerden, Microsoft 365 verileri de Exchange Online. Bu nedenle, **DLP raporlarının cmdlet'leri Powershell'de &amp; Exchange Online, Güvenlik Uyumluluk Merkezi Powershell'de kullanılamaz**. Bu nedenle, DLP raporlarında cmdlet'leri kullanmak için şunları gerekir:

1. [Bağlan PowerShell Exchange Online'e bağlanın](/powershell/exchange/connect-to-exchange-online-powershell).

2. DLP raporları için şu cmdlet'lerden herhangi birini kullanın:

    - [Get-DlpDetectionsReport](/powershell/module/exchange/Get-DlpDetectionsReport)

    - [Get-DlpDetailReport](/powershell/module/exchange/Get-DlpDetailReport)

## <a name="more-information"></a>Daha fazla bilgi

- [Şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md)

- [Bildirim gönderme ve DLP ilkeleriyle ilgili ilke ipuçlarını gösterme](use-notifications-and-policy-tips.md)

- [Belgeleri FCI veya diğer özelliklerle korumak için DLP ilkesi oluşturma](protect-documents-that-have-fci-or-other-properties.md)

- [DLP ilkesi şablonlarının şunları içermesi](what-the-dlp-policy-templates-include.md)

- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)

- [Hassas bilgi türü işlevleri](sit-functions.md)

- [Özel hassas bilgi türü oluşturma](create-a-custom-sensitive-information-type.md)
