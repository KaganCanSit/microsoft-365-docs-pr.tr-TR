---
title: Adım 2. Sözleşme yönetimi kanalınızı oluşturmak için Microsoft Teams kullanma
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
description: Microsoft 365 çözümü kullanarak sözleşme yönetimi kanalınızı oluşturmak için Microsoft Teams kullanmayı öğrenin.
ms.openlocfilehash: 6020b6e57af285e96c7998454dc46e5eb19bc5f9
ms.sourcegitcommit: 344a254ca268a2f65cf199d9158a47e08861ffa5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2022
ms.locfileid: "65368055"
---
# <a name="step-2-use-microsoft-teams-to-create-your-contract-management-channel"></a>Adım 2. Sözleşme yönetimi kanalınızı oluşturmak için Microsoft Teams kullanma

Kuruluşunuz bir sözleşme yönetimi çözümü ayarlarken paydaşların sözleşmeleri gözden geçirebileceği ve yönetebileceği merkezi bir konuma ihtiyacınız vardır. Bu amaçla[, Microsoft Teams](/microsoftteams/) kullanarak bir Teams kanalı ayarlayabilir ve Teams özelliklerini kullanarak şunları yapabilirsiniz:

- **Eylem gerektiren tüm sözleşmeleri kolayca görmek için paydaşlar için bir konum oluşturun.** Örneğin, Teams Sözleşme Yönetimi kanalında üyelerin onay gerektiren tüm **sözleşmelerin** yararlı bir kutucuk görünümünü görebileceği bir Sözleşmeler sekmesi oluşturabilirsiniz. Ayrıca görünümü, her bir "kart"ın ilgilendiğiniz önemli verileri ( *İstemci*, *Yüklenici* ve *Ücret tutarı* gibi) listelemesi için yapılandırabilirsiniz.

     ![Sözleşmeler sekmesi.](../media/content-understanding/tile-view.png)

- **Üyelerin birbirleriyle etkileşim kuracakları ve önemli olayları görebilecekleri bir konum elde edin.** Örneğin, Teams'da **Gönderiler** sekmesi konuşma yapmak, güncelleştirmeleri almak ve eylemleri görmek (bir sözleşmeyi reddeden üye gibi) için kullanılabilir. Bir şey olduğunda (onay için gönderilen yeni bir sözleşme gibi), **Gönderiler** sekmesi yalnızca bunu duyurmak için değil, aynı zamanda kaydı tutmak için de kullanılabilir. Üyeler bildirimlere abone olursa, bir güncelleştirme olduğunda bildirim alır.

     ![Gönderiler sekmesi.](../media/content-understanding/posts.png)

- **Üyelerin ödeme için ne zaman gönderilebileceğini bilmesi için onaylanmış sözleşmeleri görmeleri için bir konum belirleyin.** SharePoint bir **Ödeme için** listesi oluşturmanız ve sütun türü olarak **Tek satır metni** seçerek **İstemci**, **Yüklenici** ve **Ücret tutarı** sütunlarını eklemeniz gerekir. Sözleşmeler sekmesinde [yaptığınıza](solution-manage-contracts-step2.md#attach-your-sharepoint-document-library-to-the-contracts-tab)benzer şekilde, **Ödeme İçin** listesini Sözleşme Yönetimi kanalında Teams sekmesi olarak eklemeniz gerekir. **Ödeme İçin** sekmesi, ödeme için gönderilmesi gereken tüm sözleşmeleri listeler. Bu çözümü kolayca genişleterek bu bilgileri doğrudan üçüncü taraf bir finansal uygulamaya (örneğin Dynamics CRM) yazabilirsiniz. 


## <a name="attach-your-sharepoint-document-library-to-the-contracts-tab"></a>SharePoint belge kitaplığınızı Sözleşmeler sekmesine ekleme

Sözleşme Yönetimi kanalınızda bir **Sözleşmeler** sekmesi oluşturduktan sonra [, SharePoint belge kitaplığınızı buna eklemeniz](https://support.microsoft.com/office/add-a-sharepoint-page-list-or-document-library-as-a-tab-in-teams-131edef1-455f-4c67-a8ce-efa2ebf25f0b) gerekir. Eklemek istediğiniz SharePoint belge kitaplığı, önceki bölümde SharePoint Syntex belge anlama modelinizi uyguladığınız kitaplıktır.

SharePoint belge kitaplığını ekledikten sonra, tüm sınıflandırılmış sözleşmeleri varsayılan liste görünümü aracılığıyla görüntüleyebilirsiniz.

   ![SharePoint kitaplığının liste görünümü.](../media/content-understanding/list-view.png)

## <a name="customize-your-contracts-tab-tile-view"></a>Sözleşmeler sekmesi kutucuk görünümünüzü özelleştirme

> [!NOTE]
> Bu bölümde, [Sözleşme Yönetimi Çözümü Varlıkları deposuna](https://github.com/pnp/syntex-samples/tree/main/scenario%20samples/Contracts%20Management) dahil edilen [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) dosyasında yer alan kod örneklerine başvuruda bulunulmaktadır.

Teams, sözleşmelerinizi kutucuk görünümünde görüntülemenize olanak tanırken, sözleşme kartında görünür hale getirmek istediğiniz sözleşme verilerini görüntülemek için özelleştirmek isteyebilirsiniz. Örneğin, **Sözleşmeler** sekmesinde, üyelerin sözleşme kartında müşteriyi, yükleniciyi ve ücret tutarını görmesi önemlidir. Bu alanların tümü, belge kitaplığınıza uygulanan SharePoint Syntex modeliniz aracılığıyla her sözleşmeden ayıklandı. Ayrıca, üyelerin sözleşmenin onay sürecinde nerede olduğunu kolayca görebilmesi için kutucuk üst bilgi çubuğunu her durum için farklı renklerle değiştirebilmek istiyorsunuz. Örneğin, onaylanan tüm sözleşmelerin mavi üst bilgi çubuğu olacaktır.

   ![SharePoint kitaplığının kutucuk görünümü.](../media/content-understanding/tile.png)

Kullandığınız özel kutucuk görünümü, geçerli kutucuk görünümünü biçimlendirmek için kullanılan JSON dosyasında değişiklik yapmanızı gerektirir. [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) dosyasına bakarak kart görünümünü oluşturmak için kullanılan JSON dosyasına başvurabilirsiniz. Aşağıdaki bölümlerde, sözleşme kartlarındaki özellikler için kodun belirli bölümlerini görürsünüz.

Teams kanalınızda görünümünüz için JSON kodunu görmek veya değiştirmek istiyorsanız, Teams kanalında görünüm açılan menüsünü ve ardından **Geçerli görünümü biçimlendir'i** seçin.

   ![Teams kanaldaki json biçiminin ekran görüntüsü.](../media/content-understanding/jason-format.png)

## <a name="card-size-and-shape"></a>Kart boyutu ve şekli

[ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) dosyasında, kartın boyutunun ve şeklinin nasıl biçimlendirildiğini gösteren kodu görmek için aşağıdaki bölüme bakın.

```JSON
                  {
                    "elmType": "div",
                    "style": {
                      "background-color": "#f5f5f5",
                      "padding": "5px",
                      "width": "180px"
                    },
                    "children": [
                      {
                        "elmType": "img",
                        "attributes": {
                          "src": "@thumbnail.large"
                        },
                        "style": {
                          "width": "185px",
                          "height": "248px"
                        }
                      }
```

## <a name="contract-status"></a>Sözleşme durumu

Aşağıdaki kod, her başlık kartının durumunu tanımlamanızı sağlar. Her durum değerinin (*Yeni*, *Gözden Geçirildi*, *Onaylandı* ve *Reddedildi*) her bir değer için farklı bir renk kodu görüntüleneceğini unutmayın. [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) dosyasında, durumu tanımlayan bölüme bakın.

```JSON
          {
            "elmType": "div",
            "children": [
              {
                "elmType": "div",
                "style": {
                  "color": "white",
                  "background-color": "=if([$Status] == 'New', '#00b7c3', if([$Status] == 'In review', '#ffaa44', if([$Status] == 'Approved', '#0078d4', if([$Status] == 'Rejected', '#d13438', '#8378de'))))",
                  "padding": "5px 15px",
                  "height": "auto",
                  "text-transform": "uppercase",
                  "font-size": "12.5px"
                },
                "txtContent": "[$Status]"
              }
```

## <a name="extracted-fields"></a>Ayıklanan alanlar

Her sözleşme kartında her sözleşme için ayıklanmış üç alan görüntülenir (*İstemci*, *Yüklenici* ve *Ücret Tutarı*). Ayrıca, dosyanın tanımlamak için kullanılan SharePoint Syntex modeli tarafından sınıflandırıldığı saati/tarihi de görüntülemek istiyorsunuz.

[ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20samples/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) dosyasında aşağıdaki bölümler bunların her birini tanımlar.

### <a name="client"></a>İstemci

Bu bölüm, "İstemci"nin kartta nasıl görüntüleneceğini tanımlar ve belirli bir sözleşmenin değerini kullanır.

```JSON
                      {
                        "elmType": "div",
                        "style": {
                          "color": "#767676",
                          "font-size": "12px"
                        },
                        "txtContent": "Client"
                      },
                      {
                        "elmType": "div",
                        "style": {
                          "margin-bottom": "12px",
                          "font-size": "16px",
                          "font-weight": "600"
                        },
                        "txtContent": "[$Client]"
                      },
```

### <a name="contractor"></a>Yüklenici

Bu bölüm, "Yüklenicinin" kartta nasıl görüntüleneceğini tanımlar ve belirli bir sözleşmenin değerini kullanır.

```JSON
                        {
                          "elmType": "div",
                          "txtContent": "Contractor",
                          "style": {
                            "color": "#767676",
                            "font-size": "12px",
                            "margin-bottom": "2px"
                          }
                        },
                        {
                          "elmType": "div",
                          "style": {
                            "margin-bottom": "12px",
                            "font-size": "14px"
                          },
                          "txtContent": "[$Contractor]"
                        },
```

### <a name="fee-amount"></a>Ücret tutarı

Bu bölüm kartta "Ücret Tutarı"nın nasıl görüntüleneceğini tanımlar ve belirli bir sözleşmenin değerini kullanır.

```JSON
                      {
                        "elmType": "div",
                        "txtContent": "Fee amount",
                        "style": {
                          "color": "#767676",
                          "font-size": "12px",
                          "margin-bottom": "2px"
                        }
                      },
                      {
                        "elmType": "div",
                        "style": {
                          "margin-bottom": "12px",
                          "font-size": "14px"
                        },
                        "txtContent": "[$FeeAmount]"
                      },
```

### <a name="classification-date"></a>Sınıflandırma tarihi

Bu bölüm, "Sınıflandırma"nın kartta nasıl görüntüleneceğini tanımlar ve belirli bir sözleşmenin değerini kullanır.

```JSON
                      {
                        "elmType": "div",
                        "txtContent": "Classified",
                        "style": {
                          "color": "#767676",
                          "font-size": "12px",
                          "margin-bottom": "2px"
                        }
                      },
                      {
                        "elmType": "div",
                        "style": {
                          "margin-bottom": "12px",
                          "font-size": "14px"
                        },
                        "txtContent": "[$PrimeLastClassified]"
                      }
```

## <a name="next-step"></a>Sonraki adım

[3. Adım. Sözleşmelerinizi işlemek üzere akış oluşturmak için Power Automate kullanma](solution-manage-contracts-step3.md)
