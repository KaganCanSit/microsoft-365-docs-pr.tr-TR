---
title: Adım 2. Sözleşme Microsoft Teams kanalınızı oluşturmak için Sözleşmeler'i kullanma
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
description: Microsoft Teams çözüm Microsoft Teams sözleşme yönetim kanalınızı oluşturmak için nasıl Microsoft 365 öğrenin.
ms.openlocfilehash: a5a42bedcb6acba4caf8f6f114812c63869ee92e
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985558"
---
# <a name="step-2-use-microsoft-teams-to-create-your-contract-management-channel"></a>Adım 2. Sözleşme Microsoft Teams kanalınızı oluşturmak için Sözleşmeler'i kullanma

Organizasyonunız sözleşme yönetim çözümünü ayarlarken, proje katılımcılarının sözleşmeleri gözden geçirtecek ve yönetecekleri merkezi bir konuma ihtiyacınız vardır. Bu amaçla, Microsoft Teams [kanalını](/microsoftteams/) ayarlamak ve Teams özellikleri kullanmak için Teams:

- **Eylem gerektiren tüm sözleşmeleri kolayca görmek için proje katılımcıları için bir konum oluşturun.** Örneğin, Teams Sözleşme Yönetimi kanalında bir Sözleşmeler sekmesi oluşturabilirsiniz ve bu sekmede üyelerin onay gereken tüm sözleşmelerin yararlı kutucuk görünümlerini görebilirler. Görünümü, her "kart" sizin için önemli olan önemli verileri (*İstemci, Yüklenici* ve Ücret tutarı gibi) listeleyecek şekilde *de yapılandırabilirsiniz*.

     ![Sözleşmeler sekmesi.](../media/content-understanding/tile-view.png)

- **Üyelerin birbiriyle etkileşim kurarak önemli olayları görmeleri için bir konum bulundurabilirsiniz.** Örneğin, Teams'de Gönderiler sekmesi konuşmalar  yapmak, güncelleştirmeleri almak ve eylemleri görmek için kullanılabilir (bir üyenin sözleşmeyi reddetmesi gibi). Bir şey olduğunda (örneğin, onay için gönderilen yeni bir sözleşme), Gönderiler sekmesi  yalnızca bunu duyurmak için değil, aynı zamanda kaydını tutmak için de kullanılabilir. Üyeler bildirimlere abone olursa, güncelleştirme olduğunda bildirim alırlar.

     ![Gönderiler sekmesi.](../media/content-understanding/posts.png)

- **Üyelerin ne zaman ödeme için gönderabileceklerini bilmek üzere onaylanmış sözleşmeleri göreceği bir konum seçin.** Daha SharePoint'de, Ödeme için bir liste oluşturmanız ve Sütun türü  olarak Tek metin satırı'nın seçerek **İstemci, Yüklenici** ve Ücret tutarı sütunlarını içermeniz  gerekir.  Sözleşmeler sekmesindeki gibi, Ödeme  için Teams sekmesini Sözleşme Yönetimi kanalına eklemeniz [gerekir](solution-manage-contracts-step2.md#attach-your-sharepoint-document-library-to-the-contracts-tab). Ödeme **için sekmesi**, ödeme için gönderilmeniz gereken tüm sözleşmeleri listelemektedir. Bunun yerine bu bilgileri doğrudan üçüncü taraf bir mali uygulamaya (örneğin, Dynamics CRM) yazmak için bu çözümü kolayca genişletebilirsiniz. 


## <a name="attach-your-sharepoint-document-library-to-the-contracts-tab"></a>Sözleşmeler SharePoint kitaplığınızı Sözleşmeler sekmesine ekleme

Sözleşme Yönetimi **kanalınıza bir** Sözleşmeler sekmesi oluşturduktaktan sonra, Sözleşmeler SharePoint [kitaplığınızı bu sekmeye ekleyebilirsiniz](https://support.microsoft.com/office/add-a-sharepoint-page-list-or-document-library-as-a-tab-in-teams-131edef1-455f-4c67-a8ce-efa2ebf25f0b). Eklemek SharePoint belge kitaplığı, belge anlama modelinizi önceki bölümde SharePoint Syntex belge anlama modelinize uyguladık olan belge kitaplığıdır.

Belge kitaplığını SharePoint sonra, varsayılan liste görünümü aracılığıyla sınıflandırılmış tüm sözleşmeleri görüntüebilirsiniz.

   ![Liste görünümü SharePoint.](../media/content-understanding/list-view.png)

## <a name="customize-your-contracts-tab-tile-view"></a>Sözleşmeler sekme kutucuğunu görünümünü özelleştirme

> [!NOTE]
> Bu bölümde, Sözleşmeler Yönetimi Çözümü Varlıkları deposuna dahil edilen [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) dosyasında yer alan kod [örnekleri referans olarak verilmiştir](https://github.com/pnp/syntex-samples/tree/main/scenario%20assets/Contracts%20Management).

Sözleşmeler Teams sözleşmelerinizi kutucuk görünümünde görüntülemenize olanak sağlarken, sözleşme kartında görünür yapmak istediğiniz sözleşme verilerini görüntülemek için sözleşmeyi özelleştirebilirsiniz. Örneğin, Sözleşmeler **sekmesi** için üyelerin sözleşme kartında müşteri, yüklenici ve ücret tutarını görmeleri önemlidir. Bu alanların hepsi, belge kitaplığınıza uygulanmış olan SharePoint Syntex modeliniz aracılığıyla her sözleşmeden ayıklanır. Üyelerin sözleşmenin onay sürecinin hangi iş üzerinde olduğunu kolayca görmeleri için kutucuk üst bilgisi çubuğunu her durum için farklı renklerle değiştirmek de istiyor oluruz. Örneğin, onaylanan tüm sözleşmelerde mavi bir üst bilgi çubuğu olur.

   ![Kutucuk kitaplığının SharePoint görünümü.](../media/content-understanding/tile.png)

Kullanmakta olan özel kutucuk görünümü, geçerli kutucuk görünümünü biçimlendirmek için kullanılan JSON dosyasında değişiklik yapmanızı gerektirir. [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) dosyasına bakarak, kart görünümünü oluşturmak için kullanılan JSON dosyasına başvurabilirsiniz. Aşağıdaki bölümlerde, sözleşme kartlarında yer alan özellikler için kodun belirli bölümlerini görüyorsunuz.

Teams kanalında görünümünüz için JSON kodunu görmek veya bu kod üzerinde değişiklik yapmak için Teams kanalında görünüm açılan menüsünü ve sonra Geçerli görünümü **biçimlendir'i seçin**.

   ![Kanalda json biçiminin Teams görüntüsü.](../media/content-understanding/jason-format.png)

## <a name="card-size-and-shape"></a>Kart boyutu ve şekli

[ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) dosyasında, kartın boyutunun ve şeklinin nasıl biçimlendirildi kodunu görmek için aşağıdaki bölüme bakın.

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

Aşağıdaki kod, her başlık kartının durumunu tanımlamanız için olanak sağlar. Her durum değerinin (*Yeni*, Gözden *Geçirmede*, *Onaylandı* ve *Reddedildi) her* biri için farklı bir renk kodu görüntüleyecektir. [ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) dosyasında, durumu tanımlayan bölüme bakın.

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

Her sözleşme kartında, her sözleşme için ayıklanan üç *alan (İstemci**, Yüklenici* ve Ücret Tutarı *) görüntülenir*. Ayrıca, dosyayı tanımlamak için kullanılan veri modeline göre sınıflandırılmış olduğu SharePoint Syntex/tarihi de görüntülemek istiyorsanız.

[ContractTileFormatting.json](https://github.com/pnp/syntex-samples/blob/main/scenario%20assets/Contracts%20Management/View%20Formatter/ContractTileFormatting.json) dosyasında, aşağıdaki bölümler bunların her birini tanımlar.

### <a name="client"></a>İstemci

Bu bölümde, "İstemci" kartta nasıl görüntüleniyor ve ilgili sözleşmenin değeri nasıl kullandığı tanımlandı.

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

Bu bölümde, "Yüklenici" kartta nasıl görüntüleniyor ve ilgili sözleşmenin değeri gösterilir.

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

Bu bölümde, "Ücret Tutarı" kartta nasıl görüntüleniyor ve ilgili sözleşmenin değeri gösterilir.

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

Bu bölümde, "Sınıflandırma" özelliği kartta nasıl görüntüleniyor ve ilgili sözleşmenin değeri nasıl kullandığı tanımlandı.

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

[3. Adım. Sözleşmelerinizi Power Automate akışı oluşturmak için Sözleşmelerinizi kullanma](solution-manage-contracts-step3.md)
