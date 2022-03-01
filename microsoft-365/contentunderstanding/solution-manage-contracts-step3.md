---
title: Adım 3. Sözleşmelerinizi Power Automate akışı oluşturmak için Sözleşmelerinizi kullanma
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: ssquires
audience: admin
ms.topic: article
ms.date: ''
ms.prod: microsoft-365-enterprise
search.appverid: ''
ms.localizationpriority: medium
ROBOTS: ''
description: Sözleşmelerinizi işlemeye Power Automate için Hızlı Çözüm'den nasıl Microsoft 365 öğrenin.
ms.openlocfilehash: d83fb6e5ca911cbafc6f064c615ab15ae0f570c7
ms.sourcegitcommit: f3c912780bbcf5a5b47de192202adb3afbd5952b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2022
ms.locfileid: "63010824"
---
# <a name="step-3-use-power-automate-to-create-the-flow-to-process-your-contracts"></a>Adım 3. Sözleşmelerinizi Power Automate akışı oluşturmak için Sözleşmelerinizi kullanma

Sözleşme Yönetimi kanalınızı oluşturdunız ve belge kitaplığınıza SharePoint ekleyebilirsiniz. Sonraki adım, sözleşmelerinizi işlemeye Power Automate bir akış oluşturmak, SharePoint Syntex modelinizin tanımını ve sınıflarını oluşturmasıdır. Bu adımı, belge [kitaplığınıza bir Power Automate akışı oluşturarak SharePoint ebilirsiniz](https://support.microsoft.com/office/create-a-flow-for-a-list-or-library-in-sharepoint-or-onedrive-a9c3e03b-0654-46af-a254-20252e580d01).

Sözleşme yönetimi çözümünüz için, aşağıdaki eylemleri Power Automate bir sözleşme akışı oluşturmak istiyoruz:

-  Bir sözleşme, sınıf modeliniz tarafından SharePoint Syntex sonra, sözleşme durumunu Gözden geçirmede **olarak değiştirebilirsiniz**.
- Sözleşme daha sonra gözden geçirilir ve onaylanır veya reddedilir.
- Onaylanan sözleşmeler için sözleşme bilgileri, ödeme işlemeye ilişkin bir sekmeye yayınlanır.
- Reddedilen sözleşmeler için, ekip daha fazla çözümleme yapmak için bu durumu bilgilemektedir. 

Aşağıdaki diyagramda sözleşme yönetim Power Automate akış akışlarını gösterir.

![Flow gösteren bir diyagram oluşturun.](../media/content-understanding/flow-entire-process.png)

## <a name="prepare-your-contract-for-review"></a>Sözleşmenizi gözden geçirme için hazırlama

Bir sözleşme, belgenizi anlama modelinize göre tanımlandı SharePoint Syntex sınıflandırılmışsa, Power Automate akışı önce durumu Gözden geçirmede **olarak değiştirir**.

![Güncelleştirme durumu.](../media/content-understanding/flow-overview.png)

Dosyayı gözden geçirdikten sonra, durum değerini Gözden geçirildi **olarak değiştirebilirsiniz**.

![Gözden geçirme durumunda.](../media/content-understanding/in-review.png)

Sonraki adım, sözleşmenin gözden geçirmeyi bekleyen ve Sözleşme Yönetimi kanalına göndererek, uyarlanabilir bir kart oluşturmaktır.

![Sözleşme gözden geçirme gönderisi.](../media/content-understanding/contract-approval-post.png)


![Gözden geçirmek için uyarlanabilir kart oluşturun.](../media/content-understanding/adaptive-card.png)

Aşağıdaki kod, iş akışında bu adım için kullanılan JSON Power Automate dir.

```JSON
{
"$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
"type": "AdaptiveCard",
"version": "1.0",
"body": [
    {
    "type": "TextBlock",
    "text": "Contract approval request",
    "size": "large",
    "weight": "bolder",
     "wrap": true
    },
        {
            "type": "Container",
            "items": [
                {
                    "type": "FactSet",
                    "spacing": "Large",
                    "facts": [
                        {
                            "title": "Client",
                            "value": "@{triggerOutputs()?['body/Client']}"
                        },
                        {
                            "title": "Contractor",
                            "value": "@{triggerOutputs()?['body/Contractor']}"
                        },
                        {
                            "title": "Fee amount",
                            "value": "@{triggerOutputs()?['body/FeeAmount']}"
                        },
                        {
                            "title": "Date created",
                            "value": "@{triggerOutputs()?['body/Modified']} "
                        },
                        {
                            "title": "Link",
                            "value": "[@{triggerOutputs()?['body/{FilenameWithExtension}']}](@{triggerOutputs()?['body/{Link}']})"
                        }
                    ]
                }
            ]
         },
    {
    "type": "TextBlock",
    "text": "Comment:"
    },
        {
            "type": "Input.Text",
            "placeholder": "Enter comments",
            "id": "acComments"
        }
],
"actions": [
    {
    "type": "Action.Submit",
    "title": "Approve",
    "data": {
        "x": "Approve"
    }
    },
    {
    "type": "Action.Submit",
    "title": "Reject",
    "data": {
        "x": "Reject"
    }
    }
]
}
```


## <a name="conditional-context"></a>Koşullu bağlam

Akışınıza göre, bundan sonra sözleşmenizin onaylandırılacak veya reddedilecek bir  [koşul oluşturmanız](#if-the-contract-is-approved) [gerekir](#if-the-contract-is-rejected).

![Koşullu.](../media/content-understanding/condition.png)

## <a name="if-the-contract-is-approved"></a>Sözleşme onaylanırsa

Bir sözleşme onaylandıktan sonra aşağıdakiler gerçekleşir:

- Sözleşmeler **sekmesinde** , sözleşme kartının durumu Onaylandı olarak **değişir**.

   ![Kart durumu onaylandı.](../media/content-understanding/approved-contracts-tab.png)

- Akışınız içinde durum Onaylandı olarak **değiştirilir**.

   ![Flow onaylandı.](../media/content-understanding/status-approved.png)

- Bu çözümde, sözleşme verileri Ödeme için sekmesine **eklenir ve böylelikle** ödemelerin yönetilebilirsiniz. Bu işlem, akışın üçüncü taraf bir mali uygulama (örneğin, Dynamics CRM) ile ödeme sözleşmelerini göndermesine olanak verecek şekilde uzatılabilir.

   ![Sözleşme Ödeme'ye taşındı.](../media/content-understanding/for-payout.png)

- Akış içinde, onaylanan sözleşmeleri Ödeme sekmesine taşımak için aşağıdaki **öğeyi oluşturun** .

   ![Flow ödemeye taşımak için bir öğe seçin.](../media/content-understanding/ready-for-payout.png)

    Yeni karttan gereken bilgilerle ilgili ifadeleri Teams aşağıdaki tabloda gösterilen değerleri kullanın.
 
    |Name     |Expression |
    |---------|-----------|
    | Onay durumu  | body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response)? ['submitActionId']         |
    | Onaylandı     | body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response)? ['yanıtlayan'] ['displayName']        |
    | Onay tarihi     | body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response)? ['responseTime']         |
    | Açıklama ekleme     | body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response)? ['data']? ['acComments']         |
    
    Aşağıdaki örnekte, formül kutusunun bir ifade yazmak için Power Automate şekilde olduğu görüntülenir.

   ![Power Automate formülünü gösteren ekran görüntüsü.](../media/content-understanding/expression-formula-power-automate.png)    

- Sözleşmenin onaylandıktan sonra bir uyarlamalı kart oluşturulur ve Sözleşme Yönetimi kanalına gönderilen bir kart.

   ![Sözleşme onayı gönderildi.](../media/content-understanding/adaptive-card-approval.png)

   ![Uyarlamalı kart onayı.](../media/content-understanding/adaptive-card.png)


   Aşağıdaki kod, iş akışında bu adım için kullanılan JSON Power Automate dir.

```JSON
{ 
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "Container",
            "style": "emphasis",
            "items": [
                {
                    "type": "ColumnSet",
                    "columns": [
                        {
                            "type": "Column",
                            "items": [
                                {
                                    "type": "TextBlock",
                                    "size": "Large",
                                    "weight": "Bolder",
                                    "text": "CONTRACT APPROVED"
                                }
                            ],
                            "width": "stretch"
                        }
                    ]
                }
            ],
            "bleed": true
        },
        {
            "type": "Container",
            "items": [
                {
                    "type": "FactSet",
                    "spacing": "Large",
                    "facts": [
                        {
                            "title": "Client",
                            "value": "@{triggerOutputs()?['body/Client']}"
                        },
                        {
                            "title": "Contractor",
                            "value": "@{triggerOutputs()?['body/Contractor']}"
                        },
                        {
                            "title": "Fee amount",
                            "value": "@{triggerOutputs()?['body/FeeAmount']}"
                        },
                        {
                            "title": "Approval by",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responder']['displayName']}"
                        },
                        {
                            "title": "Approved date",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responseTime']}"
                        },
                        {
                            "title": "Approval comment",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['data']?['acComments']}"
                        },
                        {
                            "title": " ",
                            "value": " "
                        },
                        {
                            "title": "Status",
                            "value": "Ready for payout"
                        }
                    ]
                }
            ]
        }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2",
    "fallbackText": "This card requires Adaptive Cards v1.2 support to be rendered properly."
}
```

## <a name="if-the-contract-is-rejected"></a>Sözleşme reddedilirse

Bir sözleşme reddedilirse, aşağıdakiler gerçekleşir:

- Sözleşmeler **sekmesinde** , sözleşme kartının durumu Reddedildi olarak **değişir**.

   ![Kart durumu reddedildi.](../media/content-understanding/rejected-contracts-tab.png)

- Akışınıza göre, sözleşme dosyasını iade edin, durumu Reddedildi olarak **değiştirir ve sonra** da dosyayı yeniden iade edin.

   ![Flow dosyasında reddedildi durumunu gösterir.](../media/content-understanding/reject-flow.png)

- Akışınız içinde, sözleşmenin reddedilmiş olduğunu belirten uyarlanabilir bir kart oluşturun.

   ![Flow uyarlanabilir kartta reddedildi durumunu gösterir.](../media/content-understanding/reject-flow-item.png)

Aşağıdaki kod, iş akışında bu adım için kullanılan JSON Power Automate dir.

```JSON
{ 
    "type": "AdaptiveCard",
    "body": [
        {
            "type": "Container",
            "style": "attention",
            "items": [
                {
                    "type": "ColumnSet",
                    "columns": [
                        {
                            "type": "Column",
                            "items": [
                                {
                                    "type": "TextBlock",
                                    "size": "Large",
                                    "weight": "Bolder",
                                    "text": "CONTRACT REJECTED"
                                }
                            ],
                            "width": "stretch"
                        }
                    ]
                }
            ],
            "bleed": true
        },
        {
            "type": "Container",
            "items": [
                {
                    "type": "FactSet",
                    "spacing": "Large",
                    "facts": [
                        {
                            "title": "Client",
                            "value": "@{triggerOutputs()?['body/Client']}"
                        },
                        {
                            "title": "Contractor",
                            "value": "@{triggerOutputs()?['body/Contractor']}"
                        },
                        {
                            "title": "Fee amount",
                            "value": "@{triggerOutputs()?['body/FeeAmount']}"
                        },
                        {
                            "title": "Rejected by",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responder']['displayName']}"
                        },
                        {
                            "title": "Rejected date",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['responseTime']}"
                        },
                        {
                            "title": "Comment",
                            "value": "@{body('Post_an_Adaptive_Card_to_a_Teams_channel_and_wait_for_a_response')?['data']?['acComments']}"
                        },
                        {
                            "title": " ",
                            "value": " "
                        },
                        {
                            "title": "Status",
                            "value": "Needs review"
                        }
                    ]
                }
            ]
        }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.2",
    "fallbackText": "This card requires Adaptive Cards v1.2 support to be rendered properly."
}
```

- Kart Sözleşme Yönetimi kanalına gönderildi.

   ![Flow uyarlanabilir bir kart.](../media/content-understanding/rejected.png)
