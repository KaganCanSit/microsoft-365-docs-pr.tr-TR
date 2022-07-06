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
ms.openlocfilehash: 5a52d79a073a9735d5c32ce3a9646ccacf1a0dcb
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636479"
---
# <a name="data-loss-prevention-reference"></a>Veri kaybı önleme başvurusu

> [!IMPORTANT]
> Bu başvuru konusu artık Microsoft Purview Veri Kaybı Önleme (DLP) bilgileri için ana kaynak değildir. DLP içerik kümesi güncelleştiriliyor ve yeniden yapılandırılıyor. Bu makalede ele alınan konular yeni, güncelleştirilmiş makalelere taşınacaktır. DLP hakkında daha fazla bilgi için bkz. [Veri kaybını önleme hakkında bilgi edinin](dlp-learn-about-dlp.md).

<!-- this topic needs to be split into smaller, more coherent ones. It is confusing as it is. -->
<!-- move this note to a more appropriate place, no topic should start with a note -->
> [!NOTE]
> Veri kaybı önleme özellikleri kısa süre önce Office 365 Gelişmiş Uyumluluk lisansına sahip kullanıcılar için Microsoft Teams sohbetine ve kanal iletilerine eklendi. Bu, tek başına bir seçenek olarak kullanılabilir ve Office 365 E5 ve Microsoft 365 E5 Uyumluluk dahil edilir. Lisans gereksinimleri hakkında daha fazla bilgi edinmek için bkz. [Microsoft 365 Tenant-Level Hizmetleri Lisanslama Kılavuzu](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance).



<!-- MOVED TO LEARN ABOUT To comply with business standards and industry regulations, organizations must protect sensitive information and prevent its inadvertent disclosure. Sensitive information can include financial data or personally identifiable information (PII) such as credit card numbers, social security numbers, or health records. With a data loss prevention (DLP) policy in the Microsoft Purview compliance portal, you can identify, monitor, and automatically protect sensitive information across Office 365.

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
## <a name="create-and-manage-dlp-policies"></a>DLP ilkeleri oluşturma ve yönetme

DLP ilkelerini Microsoft Purview uyumluluk portalı veri kaybı önleme sayfasında oluşturur ve yönetirsiniz.

![Microsoft Purview uyumluluk portalı veri kaybı önleme sayfası](../media/943fd01c-d7aa-43a9-846d-0561321a405e.png)

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

## <a name="tuning-rules-to-make-them-easier-or-harder-to-match"></a>Eşleştirmeyi kolaylaştırmak veya zorlaştırmak için kuralları ayarlama

İnsanlar DLP ilkelerini oluşturduktan ve açtıktan sonra bazen şu sorunlarla karşılaşırlar:

- Hassas bilgi **olmayan** çok fazla içerik kurallarla eşleşir; başka bir deyişle çok fazla hatalı pozitif sonuç.

- Hassas bilgi **olan** çok az içerik kurallarla eşleşir. Başka bir deyişle, hassas bilgiler üzerinde koruyucu eylemler uygulanmaz.

Bu sorunları gidermek için, içeriğin kurallarla eşleşmesini zorlaştırmak veya kolaylaştırmak için örnek sayısını ve eşleşme doğruluğunu ayarlayarak kurallarınızı ayarlayabilirsiniz. Bir kuralda kullanılan her hassas bilgi türünün hem örnek sayısı hem de eşleşme doğruluğu vardır.

### <a name="instance-count"></a>Örnek sayısı

Örnek sayısı, içeriğin kuralla eşleşmesi için belirli bir hassas bilgi türünün kaç kez bulunması gerektiği anlamına gelir. Örneğin içerik, 1 ile 9 arasında benzersiz ABD veya Birleşik Krallık arasındaysa aşağıda gösterilen kuralla eşleşir. pasaport numaraları belirlenir.

> [!NOTE]
> Örnek sayısı yalnızca hassas bilgi türleri ve anahtar sözcükler için **benzersiz** eşleşmeler içerir. Örneğin, bir e-posta aynı kredi kartı numarasının 10 örneğini içeriyorsa, bu 10 yineleme, kredi kartı numarasının tek bir örneği olarak sayılır.

Kuralları ayarlamak için örnek sayısını kullanmak için kılavuz basittir:

- Kuralın eşleşmesini kolaylaştırmak için **en az** sayıyı azaltın ve/veya **maksimum** sayıyı artırın. Ayrıca sayısal değeri silerek **maksimum** değerini **herhangi birine** ayarlayabilirsiniz.

- Kuralın eşleşmesini zorlaştırmak için **minimum** sayıyı artırın.

Genellikle, daha düşük örnek sayısı olan bir kuralda (örneğin, 1-9) kullanıcı bildirimleri gönderme gibi daha az kısıtlayıcı eylemler kullanırsınız. Ayrıca daha yüksek örnek sayısı olan bir kuralda (örneğin, 10-herhangi bir) kullanıcı geçersiz kılmalarına izin vermeden içeriğe erişimi kısıtlama gibi daha kısıtlayıcı eylemler kullanırsınız.

![Kural düzenleyicisinde örnek sayıları.](../media/e7ea3c12-72c5-4bb3-9590-c924c665e84d.png)

### <a name="match-accuracy"></a>Eşleşme doğruluğu

Yukarıda açıklandığı gibi, farklı kanıt türlerinin bir bileşimi kullanılarak hassas bir bilgi türü tanımlanır ve algılanır. Genellikle, hassas bir bilgi türü desen olarak adlandırılan bu tür birden çok birleşimle tanımlanır. Daha az kanıt gerektiren bir desen daha düşük eşleşme doğruluğuna (veya güvenilirlik düzeyine), daha fazla kanıt gerektiren bir desen ise daha yüksek eşleşme doğruluğuna (veya güvenilirlik düzeyine) sahiptir. Her hassas bilgi türü tarafından kullanılan gerçek desenler ve güvenilirlik düzeyleri hakkında daha fazla bilgi edinmek için bkz [. Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md).

Örneğin, Kredi Kartı Numarası adlı hassas bilgi türü iki desenle tanımlanır:

- %65 güven gerektiren bir desen:

  - Kredi kartı numarası biçiminde bir sayı.

  - Sağlama toplamını geçiren bir sayı.

- %85 güvenilirlik gerektiren bir desen:

  - Kredi kartı numarası biçiminde bir sayı.

  - Sağlama toplamını geçiren bir sayı.

  - Doğru biçimde bir anahtar sözcük veya son kullanma tarihi.

Kurallarınızda bu güvenilirlik düzeylerini (veya eşleşme doğruluğunu) kullanabilirsiniz. Genellikle, daha düşük eşleşme doğruluğuna sahip bir kuralda kullanıcı bildirimleri gönderme gibi daha az kısıtlayıcı eylemler kullanırsınız. Ayrıca daha yüksek eşleşme doğruluğuna sahip bir kuralda kullanıcı geçersiz kılmalarına izin vermeden içeriğe erişimi kısıtlama gibi daha kısıtlayıcı eylemler kullanırsınız.

kredi kartı numarası gibi belirli bir hassas bilgi türü içerikte tanımlandığında yalnızca tek bir güvenilirlik düzeyinin döndürüldüğünü anlamak önemlidir:

- Tüm eşleşmeler tek bir desen içinse, bu desen için güvenilirlik düzeyi döndürülür.

- Birden fazla desen için eşleşmeler varsa (yani iki farklı güvenilirlik düzeyiyle eşleşmeler varsa), tek başına tüm desenlerden daha yüksek bir güvenilirlik düzeyi döndürülür. İşin zor kısmı da bu. Örneğin, kredi kartı için hem %65 hem de %85 desenleri eşleştirilirse, bu hassas bilgi türü için döndürülen güvenilirlik düzeyi %90'dan fazladır çünkü daha fazla kanıt daha fazla güvenilirlik anlamına gelir.

Bu nedenle, kredi kartları için biri %65 eşleşme doğruluğu, biri de %85 eşleşme doğruluğu için olmak üzere birbirini dışlayan iki kural oluşturmak istiyorsanız, eşleşme doğruluğu aralıkları şöyle görünür. İlk kural yalnızca %65 deseninin eşleşmelerini alır. İkinci kural **, en az** %85 eşleşmesi olan eşleşmeleri alır ve diğer düşük güvenilirlikli eşleşmelere **sahip olabilir** .

![Eşleşme doğruluğu için farklı aralıklara sahip iki kural.](../media/21bdfe36-7a91-4347-8098-11809a92f9a4.png)

Bu nedenlerle, farklı eşleşme doğruluğuna sahip kurallar oluşturma yönergeleri şunlardır:

- En düşük güvenilirlik düzeyi genellikle **min** ve **max** (aralık değil) için aynı değeri kullanır.

- En yüksek güvenilirlik düzeyi genellikle düşük güvenilirlik düzeyinin hemen üstünden 100'e kadar olan bir aralıktır.

- Aralarındaki güven düzeyleri genellikle düşük güvenilirlik düzeyinin hemen üstünden daha yüksek güvenilirlik düzeyinin hemen altına kadar değişir.

## <a name="using-a-retention-label-as-a-condition-in-a-dlp-policy"></a>DLP ilkesinde koşul olarak bekletme etiketi kullanma

DLP ilkesinde koşul olarak önceden oluşturulmuş ve yayımlanmış bir [bekletme etiketi](retention.md#retention-labels) kullandığınızda, bilmeniz gereken bazı şeyler vardır:

- Bekletme etiketi, bir DLP ilkesinde koşul olarak kullanılmaya çalışılmadan önce oluşturulup yayımlanmalıdır.
- Yayımlanan bekletme etiketlerinin eşitlenmesi bir ila yedi gün sürebilir. Daha fazla bilgi için bkz [. Bekletme etiketleri bir bekletme](create-apply-retention-labels.md#when-retention-labels-become-available-to-apply) ilkesinde yayımlanan bekletme etiketleri için geçerli olduğunda ve Bekletme etiketlerinin otomatik olarak yayımlanan bekletme etiketleri için [geçerli olması ne kadar sürer](apply-retention-labels-automatically.md#how-long-it-takes-for-retention-labels-to-take-effect) ?
- İlkede bekletme etiketi kullanma **, yalnızca SharePoint ve OneDrive'daki öğeler için desteklenir**.

  ![Koşul olarak etiketler.](../media/5b1752b4-a129-4a88-b010-8dcf8a38bb09.png)

  Bekletme ve kullanımda olan öğeleriniz varsa ve bunlara başka denetimler uygulamak istiyorsanız, DLP ilkesinde bekletme etiketi kullanmak isteyebilirsiniz, örneğin:

  - **2018'den** itibaren SharePoint'te depolanan vergi belgelerine uygulandığında bunları 10 yıl boyunca saklayan vergi yılı 2018 adlı bir bekletme etiketi yayımladınız ve bunları attınız. Ayrıca bu öğelerin kuruluşunuzun dışında paylaşılmasını da istemezsiniz. Bunu bir DLP ilkesiyle yapabilirsiniz.

  > [!IMPORTANT]
  > DLP ilkesinde koşul olarak bir bekletme etiketi belirtirseniz ve konum olarak Exchange ve/veya Teams'i de eklerseniz bu hatayı alırsınız: **"E-posta ve ekip iletilerinde etiketlenmiş içeriğin korunması desteklenmez. Aşağıdaki etiketi kaldırın veya Konum olarak Exchange ve Teams'i kapatın."** Bunun nedeni, Exchange aktarım işleminin ileti gönderme ve teslim sırasında etiket meta verilerini değerlendirmemesidir.

### <a name="using-a-sensitivity-label-as-a-condition-in-a-dlp-policy"></a>DLP ilkesinde koşul olarak duyarlılık etiketi kullanma

DLP ilkelerinde duyarlılık etiketini koşul olarak kullanma hakkında [daha fazla bilgi edinin](./dlp-sensitivity-label-as-condition.md).

### <a name="how-this-feature-relates-to-other-features"></a>Bu özelliğin diğer özelliklerle ilişkisi

Hassas bilgiler içeren içeriğe çeşitli özellikler uygulanabilir:

- [Bekletme etiketi ve bekletme ilkesi](retention.md), bu içerikte **bekletme** eylemlerini zorunlu kılabilir.

- DLP ilkesi bu içerikte **koruma** eylemlerini zorunlu kılabilir. Bu eylemleri uygulamadan önce, bir DLP ilkesi etiket içeren içeriğe ek olarak başka koşulların da karşılanmasını gerektirebilir.

![Hassas bilgilere uygulanabilecek özelliklerin diyagramı.](../media/dd410f97-a3a3-455c-a1e9-7ed8ae6893d6.png)

DLP ilkesinin, hassas bilgilere uygulanan bir etiket veya saklama ilkesinden daha zengin bir algılama özelliğine sahip olduğunu unutmayın. DLP ilkesi, hassas bilgiler içeren içerik üzerinde koruyucu eylemler uygulayabilir ve hassas bilgiler içerikten kaldırılırsa, içerik bir sonraki taranışında bu koruyucu eylemler geri alınır. Ancak hassas bilgiler içeren içeriğe bekletme ilkesi veya etiket uygulanırsa, bu hassas bilgiler kaldırılsa bile geri alınmayacak tek seferlik bir eylemdir.

Bir etiketi bir DLP ilkesinde koşul olarak kullanarak, bu etikete sahip içerikte hem bekletme hem de koruma eylemlerini zorunlu kılabilirsiniz. Etiket içeren içeriği hassas bilgiler içeren içerik gibi düşünebilirsiniz. Hem etiket hem de hassas bilgi türü, içeriği sınıflandırmak için kullanılan özelliklerdir, böylece bu içerik üzerinde eylemleri zorunlu kılabilirsiniz.

![Koşul olarak etiket kullanan DLP ilkesinin diyagramı.](../media/4538fd8f-fb74-4743-bc22-a5de33adfebb.png)

## <a name="simple-settings-vs-advanced-settings"></a>Basit ayarlar ve gelişmiş ayarlar karşılaştırması

DLP ilkesi oluşturduğunuzda, basit veya gelişmiş ayarlar arasında seçim yaparsınız:

- **Basit ayarlar** , kuralları oluşturmak veya değiştirmek için kural düzenleyicisini kullanmadan en yaygın DLP ilkesi türünü oluşturmayı kolaylaştırır.

- **Gelişmiş ayarlar** , DLP ilkenizin her ayarı üzerinde tam denetim sağlamak için kural düzenleyicisini kullanır.

Endişelenmeyin, kapakların altında, basit ayarlar ve gelişmiş ayarlar, koşullar ve eylemlerden oluşan kuralları zorunlu kılarak tam olarak aynı şekilde çalışır; yalnızca basit ayarlarla kural düzenleyicisini görmezsiniz. Bu, DLP ilkesi oluşturmanın hızlı bir yoludur.

### <a name="simple-settings"></a>Basit ayarlar

Açık arayla en yaygın DLP senaryosu, hassas bilgileri içeren içeriğin kuruluşunuz dışındaki kişilerle paylaşılmasını önlemeye yardımcı olacak bir ilke oluşturmak ve içeriğe kimlerin erişebileceğini kısıtlama, son kullanıcı veya yönetici bildirimleri gönderme ve olayı daha sonra araştırmak üzere denetleme gibi otomatik bir düzeltme eylemi uygulamaktır. Kişiler, hassas bilgilerin yanlışlıkla açıklanmasını önlemeye yardımcı olmak için DLP kullanır.

Bu hedefe ulaşmayı basitleştirmek için bir DLP ilkesi oluşturduğunuzda **Basit ayarları kullan'ı** seçebilirsiniz. Bu ayarlar, kural düzenleyicisine gitmek zorunda kalmadan en yaygın DLP ilkesini uygulamak için ihtiyacınız olan her şeyi sağlar.

![Basit ve gelişmiş ayarlar için DLP seçenekleri.](../media/33c93824-ead5-43b6-9c3e-fd1630c92a7d.png)

### <a name="advanced-settings"></a>Gelişmiş ayarlar

Daha özelleştirilmiş DLP ilkeleri oluşturmanız gerekiyorsa **Gelişmiş ayarları kullan'ı** seçebilirsiniz.

Gelişmiş ayarlar, her kural için örnek sayısı ve eşleşme doğruluğu (güvenilirlik düzeyi) dahil olmak üzere her olası seçenek üzerinde tam denetime sahip olduğunuz kural düzenleyicisini sunar.

Bir bölüme hızla atlamak için kural düzenleyicisinin üst gezinti bölmesindeki bir öğeye tıklayarak aşağıdaki bölüme gidin.

![DLP kural düzenleyicisinin üst gezinti menüsü.](../media/c527b97f-ca53-4c79-ad19-1a63be8a8ecc.png)

## <a name="dlp-policy-templates"></a>DLP ilke şablonları

DLP ilkesi oluşturmanın ilk adımı, hangi bilgilerin korunacağını seçmektir. Bir DLP şablonuyla başlayarak, sıfırdan yeni bir kural kümesi oluşturma ve varsayılan olarak hangi tür bilgilerin dahil edilmesi gerektiğini belirleme işini kaydedersiniz. Daha sonra, kuruluşunuzun özel gereksinimlerini karşılamak üzere kurala ince ayar yapmak için bu gereksinimleri ekleyebilir veya değiştirebilirsiniz.

Önceden yapılandırılmış bir DLP ilke şablonu HIPAA verileri, PCI-DSS verileri, Gramm-Leach-Bliley Yasası verileri ve hatta yerel ayara özgü kişisel bilgiler (P.I.) gibi belirli hassas bilgi türlerini algılamanıza yardımcı olabilir. Yaygın hassas bilgi türlerini bulmanızı ve korumanızı kolaylaştırmak için, Microsoft 365'te bulunan ilke şablonları, kullanmaya başlamanız için gereken en yaygın hassas bilgi türlerini içerir.

![ABD Vatanseverlik Yasası şablonuna odaklanan veri kaybı önleme ilkelerine yönelik şablonların listesi.](../media/791b2403-430b-4987-8643-cc20abbd8148.png)

Kuruluşunuzun kendi özel gereksinimleri de olabilir. Bu durumda **Özel ilke** seçeneğini belirleyerek sıfırdan bir DLP ilkesi oluşturabilirsiniz. Özel ilke boş ve önceden hazırlanmış kural içermiyor.

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

DLP ilkelerinizi oluşturup açtıktan sonra, bunların istediğiniz gibi çalıştığını ve uyumlu kalmanıza yardımcı olduğunu doğrulamanız gerekir. DLP raporlarıyla, zaman içindeki DLP ilkesi ve kural eşleşmelerinin sayısını ve hatalı pozitif sonuçların ve geçersiz kılmaların sayısını hızla görüntüleyebilirsiniz. Her rapor için bu eşleşmeleri konuma, zaman çerçevesine göre filtreleyebilir ve hatta belirli bir ilke, kural veya eyleme göre daraltabilirsiniz.

DLP raporlarıyla iş içgörüleri elde edebilir ve:

- Belirli zaman aralıklarına odaklanın ve ani artışların ve eğilimlerin nedenlerini anlayın.

- Kuruluşunuzun uyumluluk ilkelerini ihlal eden iş süreçlerini keşfedin.

- DLP ilkelerinin iş üzerindeki etkisini anlayın.

Ayrıca, DLP raporlarınızı çalıştırırken DLP ilkelerinize ince ayar yapmak için de kullanabilirsiniz.

![Güvenlik ve Uyumluluk Merkezi'ndeki Raporlar Panosu.](../media/6d741252-a0ce-4429-95ba-6c857ecc9a7e.png)

## <a name="how-dlp-policies-work"></a>DLP ilkeleri nasıl çalışır?

DLP, derin içerik analizi (yalnızca basit bir metin taraması değil) kullanarak hassas bilgileri algılar. Bu derin içerik analizi, DLP ilkelerinizle eşleşen içeriği algılamak için anahtar sözcük eşleşmelerini, sözlük eşleşmelerini, normal ifadelerin değerlendirilmesini, iç işlevleri ve diğer yöntemleri kullanır. Büyük olasılıkla verilerinizin yalnızca küçük bir yüzdesi hassas olarak kabul edilir. DLP ilkesi, içeriğinizin geri kalanıyla çalışan kişileri engellemeden veya etkilemeden yalnızca bu verileri tanımlayabilir, izleyebilir ve otomatik olarak koruyabilir.

### <a name="policies-are-synced"></a>İlkeler eşitlenir

Microsoft Purview uyumluluk portalı bir DLP ilkesi oluşturduktan sonra, bu ilke merkezi bir ilke deposunda depolanır ve ardından aşağıdakiler gibi çeşitli içerik kaynaklarıyla eşitlenir:

- Exchange Online ve oradan Web üzerinde Outlook ve Outlook'a.

- siteleri OneDrive İş.

- SharePoint Online siteleri.

- Office masaüstü programları (Excel, PowerPoint ve Word).

- Microsoft Teams kanalları ve sohbet iletileri.

İlke doğru konumlara eşitlendikten sonra içeriği değerlendirmeye ve eylemleri zorlamaya başlar.
<!-- what is the time delay for first deployment of a policy and what is the sync schedule? -->

### <a name="policy-evaluation-in-onedrive-for-business-and-sharepoint-online-sites"></a>OneDrive İş ve SharePoint Online sitelerinde ilke değerlendirmesi

Tüm SharePoint Online sitelerinizde ve OneDrive İş sitelerinizde belgeler sürekli değişiyor; bunlar sürekli oluşturuluyor, düzenleniyor, paylaşılıyor vb. Bu, belgelerin herhangi bir zamanda bir DLP ilkesiyle çakışabileceği veya uyumlu hale gelebileceği anlamına gelir. Örneğin, bir kişi ekip sitesine hassas bilgiler içermeyen bir belgeyi karşıya yükleyebilir, ancak daha sonra farklı bir kişi aynı belgeyi düzenleyip hassas bilgiler ekleyebilir.

Bu nedenle, DLP ilkeleri belgelerde ilke eşleşmelerini arka planda sık sık denetler. Bunu zaman uyumsuz ilke değerlendirmesi olarak düşünebilirsiniz.
<!-- what is the frequency? looks like it is tied to the search crawl schedule -->

#### <a name="how-it-works"></a>Nasıl çalışır?

Kişiler sitelerine belge ekler veya değiştirirken, arama motoru içeriği tarar ve böylece daha sonra arama yapabilirsiniz. Bu durum yaşanırken, içerik ayrıca hassas bilgiler için taranır ve paylaşılıp paylaşılmadığını denetler. Bulunan tüm hassas bilgiler arama dizininde güvenli bir şekilde depolanır, böylece yalnızca uyumluluk ekibi erişebilir, ancak normal kullanıcılara erişemez. Açtığınız her DLP ilkesi arka planda (zaman uyumsuz olarak) çalışır, bir ilkeyle eşleşen içeriği sık sık arar ve yanlışlıkla sızıntılara karşı korumak için eylemler uygular.

![DLP ilkesinin içeriği zaman uyumsuz olarak nasıl değerlendireceğini gösteren diyagram.](../media/bdf73099-039a-4909-ae89-ac12c41992ba.png)

<!-- conflict with a DLP policy is bad wording -->
Son olarak, belgeler bir DLP ilkesiyle çakışabilir, ancak bir DLP ilkesiyle de uyumlu hale gelebilir. Örneğin, bir kişi belgeye kredi kartı numaraları eklerse, bu bir DLP ilkesinin belgeye otomatik olarak erişimi engellemesine neden olabilir. Ancak, kişi daha sonra hassas bilgileri kaldırırsa, belge ilkeye göre bir sonraki değerlendirildiğinde eylem (bu durumda engelleme) otomatik olarak geri alınır.

DLP, dizine alınabilecek tüm içeriği değerlendirir. Hangi dosya türlerinin varsayılan olarak gezindiği hakkında daha fazla bilgi için bkz. [SharePoint Server'da varsayılan gezilen dosya adı uzantıları ve ayrıştırılmış dosya türleri](/SharePoint/technical-reference/default-crawled-file-name-extensions-and-parsed-file-types).

> [!NOTE]
> DLP ilkeleri bunları analiz etme fırsatına sahip olmadan önce belgelerin paylaşılmasını önlemek için, içeriği dizine alınana kadar SharePoint'te yeni dosyaların paylaşımı engellenebilir. Ayrıntılı bilgi için bkz. [Yeni dosyaları varsayılan olarak hassas olarak işaretleme](/sharepoint/sensitive-by-default) .

### <a name="policy-evaluation-in-exchange-online-outlook-and-outlook-on-the-web"></a>Exchange Online, Outlook ve Web üzerinde Outlook'da ilke değerlendirmesi

Konum olarak Exchange Online içeren bir DLP ilkesi oluşturduğunuzda, ilke Microsoft Purview uyumluluk portalı Exchange Online ve ardından Exchange Online ile Web üzerinde Outlook eşitlenir  ve Outlook'u seçin.

Outlook'ta bir ileti oluşturulurken, oluşturulan içerik DLP ilkelerine göre değerlendirildikçe kullanıcı ilke ipuçlarını görebilir. İleti gönderildikten sonra, exchange posta akışı kuralları (aktarım kuralları olarak da bilinir) ve <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange yönetim merkezinde</a> oluşturulan DLP ilkeleriyle birlikte posta akışının normal bir parçası olarak DLP ilkelerine göre değerlendirilir. DLP ilkeleri hem iletiyi hem de ekleri tarar.

### <a name="policy-evaluation-in-the-office-desktop-programs"></a>Office masaüstü programlarında ilke değerlendirmesi

<!-- same capability to identify sensitive information line conflates sensitive information types and such -->
Excel, PowerPoint ve Word, hassas bilgileri tanımlamak ve DLP ilkelerini SharePoint Online ve OneDrive İş olarak uygulamak için aynı özelliği içerir. Bu Office programları, DLP ilkelerini doğrudan merkezi ilke deposundan eşitler ve kullanıcılar DLP ilkesine dahil edilen bir siteden açılan belgelerle çalışırken içeriği DLP ilkelerine karşı sürekli olarak değerlendirir.

Office'te DLP ilkesi değerlendirmesi, programların performansını veya içerik üzerinde çalışan kişilerin üretkenliğini etkilemeyecek şekilde tasarlanmıştır. Büyük bir belge üzerinde çalışıyorsa veya kullanıcının bilgisayarı meşgulse, ilke ipucunun görünmesi birkaç saniye sürebilir.

### <a name="policy-evaluation-in-microsoft-teams"></a>Microsoft Teams'de ilke değerlendirmesi
 <!--what do you mean that it's synched to user accounts?  I thought DLP policies were applied to locations not users like sensitivity labels are  -->

Konum olarak Microsoft Teams'i içeren bir DLP ilkesi oluşturduğunuzda, ilke Microsoft Purview uyumluluk portalı kullanıcı hesaplarıyla, Microsoft Teams kanallarıyla ve sohbet iletileriyle eşitlenir. DLP ilkelerinin nasıl yapılandırıldığına bağlı olarak, birisi bir Microsoft Teams sohbetinde veya kanal iletisinde hassas bilgileri paylaşmayı denediğinde, ileti engellenebilir veya iptal edilebilir. Ayrıca, hassas bilgiler içeren ve konuklarla (dış kullanıcılar) paylaşılan belgeler bu kullanıcılar için açılmaz. Daha fazla bilgi edinmek için bkz. [Veri kaybı önleme ve Microsoft Teams](dlp-microsoft-teams.md).

## <a name="permissions"></a>İzinler

Varsayılan olarak, Genel yöneticiler, Güvenlik yöneticileri ve Uyumluluk yöneticileri DLP ilkesi oluşturma ve uygulama erişimine sahip olur. DLP ilkeleri oluşturacak uyumluluk ekibinizin diğer üyelerinin Microsoft Purview uyumluluk portalı izinlerine sahip olması gerekir. Varsayılan olarak, Kiracı yöneticiniz bu konuma erişebilir ve uyumluluk görevlilerine ve diğer kişilere kiracı yöneticisinin tüm izinlerini vermeden Microsoft Purview uyumluluk portalı erişim izni verebilir. Bunu yapmak için şunları yapmanızı öneririz:

1. Microsoft 365'te bir grup oluşturun ve gruba uyumluluk görevlileri ekleyin.

2. Microsoft Purview uyumluluk portalı **İzinler** sayfasında bir rol grubu oluşturun.

3. Rol grubunu oluştururken **Rol Seç** bölümünü kullanarak Rol Grubuna şu rolü ekleyin: **DLP Uyumluluk Yönetimi**.

4. Daha önce oluşturduğunuz Microsoft 365 grubunu rol grubuna eklemek için **Üyeleri Seç** bölümünü kullanın.

Ayrıca **, Yalnızca Görüntüleme DLP Uyumluluk Yönetimi** rolü vererek DLP ilkeleri ve DLP raporları için yalnızca görüntüleme ayrıcalıklarına sahip bir rol grubu da oluşturabilirsiniz.

Daha fazla bilgi için bkz. [Kullanıcılara Office 365 Uyumluluk Merkezi'ne erişim verme](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).

Bu izinler yalnızca DLP ilkesi oluşturmak ve uygulamak için gereklidir. İlke uygulama, içeriğe erişim gerektirmez.

## <a name="find-the-dlp-cmdlets"></a>DLP cmdlet'lerini bulma

Microsoft Purview uyumluluk portalı cmdlet'lerinin çoğunu kullanmak için şunları yapmanız gerekir:

1. [Güvenlik & Uyumluluğu PowerShell'e bağlanın](/powershell/exchange/connect-to-scc-powershell).

2. Bu [ilke ve uyumluluk-dlp cmdlet'lerinden](/powershell/module/exchange/export-dlppolicycollection) herhangi birini kullanın.

Ancak DLP raporlarının Exchange Online dahil olmak üzere Microsoft 365 genelinden veri çekmesi gerekir. Bu nedenle ***, DLP raporlarına yönelik cmdlet'ler Microsoft Purview uyumluluk portalı PowerShell'de değil Exchange Online PowerShell'de kullanılabilir***. Bu nedenle, DLP raporları için cmdlet'leri kullanmak için şunları yapmanız gerekir:

1. [Exchange Online PowerShell’e bağlanma](/powershell/exchange/connect-to-exchange-online-powershell).

2. DLP raporları için şu cmdlet'lerden birini kullanın:

    - [Get-DlpDetectionsReport](/powershell/module/exchange/Get-DlpDetectionsReport)

    - [Get-DlpDetailReport](/powershell/module/exchange/Get-DlpDetailReport)

## <a name="more-information"></a>Daha fazla bilgi

- [Bir şablondan DLP ilkesi oluşturma](create-a-dlp-policy-from-a-template.md)

- [DLP ilkeleri için bildirim gönderme ve ilke ipuçlarını gösterme](use-notifications-and-policy-tips.md)

- [FCI veya diğer özellikler ile belgeleri korumak için bir DLP ilkesi oluşturma](protect-documents-that-have-fci-or-other-properties.md)

- [DLP ilke şablonları neler içerir?](what-the-dlp-policy-templates-include.md)

- [Hassas bilgi türü varlık tanımları](sensitive-information-type-entity-definitions.md)

- [Hassas bilgi türü işlevleri](sit-functions.md)

- [Özel hassas bilgi türü oluşturma](create-a-custom-sensitive-information-type.md)
