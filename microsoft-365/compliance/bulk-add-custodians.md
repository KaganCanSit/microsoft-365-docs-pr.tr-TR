---
title: Koruyucuları bir vakaya Advanced eDiscovery aktarma
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Bir vakaya çeşitli koruyucuları ve ilişkili veri kaynaklarını hızla eklemek için içeri aktarma aracını Advanced eDiscovery.
ms.openlocfilehash: 5e2ce53a227462a1fddd7785faf83355ca70611c
ms.sourcegitcommit: 2e05865beeb2051fd9ece212a46179310b946a46
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2021
ms.locfileid: "63008074"
---
# <a name="import-custodians-to-an-advanced-ediscovery-case"></a>Koruyucuları bir vakaya Advanced eDiscovery aktarma

Birçok Advanced eDiscovery koruyucu içeren diğer durumlarda, bir vakaya eklemek için gerekli bilgileri içeren bir CSV dosyası kullanarak birden çok koruyucuları bir kerede içeri aktarabilirsiniz.

## <a name="import-custodians"></a>Koruyucuları içeri aktarma

1. Büyük/Advanced eDiscovery açın ve Veri **kaynakları sekmesini** seçin.

2. Veri **kaynağı ekleEkleçleri** >  **sınırla'ya tıklayın**.

3. Koruyucuları **içeri aktar sayfasında** , Özel şablon CSV **dosyasını** indirmek için Boş şablon indir'e tıklayın.

   ![Koruyucuları içeri aktarma sayfasından bir CSV şablonu indirin.](../media/ImportCustodians1.png)

4. ÖZEL bilgileri CSV dosyasına ekleyin ve yerel bilgisayarınıza kaydedin. CSV [dosyasındaki gerekli özellikler hakkında bilgi için Custo csv](#custodian-csv-file) dosyası bölümüne bakın.

5. CSV dosyasını özel kişi bilgileriyle hazır açtıktan sonra,  >  Veri kaynakları sekmesine geri gidin ve Veri  kaynağı **ekleM custod bilgilerini** yeniden içeri aktar'a tıklayın.

6. Koruyucuları **içeri aktar uç** sayfasında Gözat'a tıklayın ve  koruyucu bilgilerini içeren CSV dosyasını karşıya yükleyin.

   CSV dosyası karşıya yüklendikten sonra, **BulkAddCusto bu** adlı bir iş oluşturulur ve **İş sekmesinde görüntülenir** . İş, koruyucuları ve ilişkili veri kaynaklarını doğrular ve sonra bunları durum sayfasının **Veri** kaynakları sayfasına ekler.

## <a name="custodian-csv-file"></a>Custo bir CSV dosyası

CSV koruyucu şablonunu indirdikten sonra, her satıra koruyucuları ve bunların veri kaynağını indirebilirsiniz. Üst bilgi satırdaki sütun adlarını değiştirmeyebilirsiniz. Diğer veri kaynaklarını bir özel dosyayla ilişkilendirmek için iş yükü türü ve iş yükü konumu sütunlarını kullanın.

| Sütun adı|Açıklama|
|:------- |:------------------------------------------------------------|
|**Custo custo custo custemail**     |Custo bir UPN e-posta adresi. Örneğin, sarad@contoso.onmicrosoft.com.           |
|**Exchange Etkin** | Custo posta kutusunu eklemek veya dahil etmek için DOĞRU/YANLIŞ değeri.      |
|**OneDrive Etkin** | Custo custo OneDrive İş için DOĞRU/YANLIŞ değeri. |
|**Is OnHold**        | Koruyucu veri kaynaklarının yerinde basılı olup olmadığını göstermek için DOĞRU/YANLIŞ değeri. <sup>1</sup>     |
|**workload1 tür**         |Custo ortak veri kaynağı türünü belirten dize değeri. Olası değerler şunlardır: <br/>- ExchangeMailbox<br/> - SharePointSitesi<br/>- <sup>TeamsMailbox2</sup><br/>- <sup>YammerMailbox2</sup>| 
|**Workload1 Location**     | İş yükünüz bağlı olarak, veri kaynağının konumu bu olur. Örneğin, bir posta kutusunun e-Exchange adresi veya posta kutusunun URL'si SharePoint olabilir. |
|||

> [!NOTE]
> <sup>1</sup> 1.000'den fazla posta kutusunu veya 100 siteyi ayrı tutmanız gerektiğinde sistem eBulma ayrımlarını otomatik olarak ölçeklendirin. Bu, sistemin veri konumlarını tek bir tutma yerine otomatik olarak birden çok  tutma için ekleyecek olduğu anlamına gelir. Bununla birlikte, kuruluş başına 10.000 vaka sınırlaması yine de geçerlidir. Tutma sınırları hakkında daha fazla bilgi için bkz. Tutma [Advanced eDiscovery](limits-ediscovery20.md#hold-limits).
<br>
> <sup>2</sup> CSV dosyasına TeamsMailbox ve YammerMailbox iş yüklerini dahil edersiniz, grup sitesi (Ekip Sitesi ve Yammer Sitesi) varsayılan olarak otomatik olarak eklenir. CSV dosyasında TeamsSite ve YammerSitesi'i ayrı olarak belirtmeniz gerekmez.

Aşağıda, koruyucu bilgileri olan bir CSV dosyası örneği ve şöyledir:<br/><br/>

|Custo custo custo custemail      | Exchange Etkin | OneDrive Etkin | Is OnHold | workload1 tür | Workload1 Location             |
| ----------------- | ---------------- | ---------------- | --------- | -------------- | ------------------------------ |
|robinc@contoso.onmicrosoft.com | TRUE             | TRUE             | TRUE      | SharePointSitesi | https://contoso.sharepoint.com |
|pillarp@contoso.onmicrosoft.com | TRUE             | TRUE             | TRUE      | |  |
|.johnj@contoso.onmicrosoft.com|TRUE|TRUE|TRUE||
|sarad@contoso.onmicrosoft.com|TRUE|TRUE|TRUE|ExchangeMailbox|.saradavis@contoso.onmicrosoft.com
||||||

> [!NOTE]
> Etkin olmayan bir posta kutusunu koruyucu olarak içeri aktararak veya etkin olmayan bir posta kutusunu başka bir custo custo ortak yapmak için, etkin olmayan posta kutusunun UPN adresine bir "." öneki ekleyin.

## <a name="custodian-and-data-source-validation"></a>Custo bira ve veri kaynağı doğrulaması

Custo csv dosyasını karşıya yükledikten sonra, Advanced eDiscovery şunları yapın:

1. Koruyucuları ve onların veri kaynaklarını doğrular.

2. Her koruyucu için tüm veri kaynaklarını dizine alır ve bunları ayrı tutar (CSV **dosyasındaki Is OnHold** özelliği TRUE olarak ayarlanmışsa).

### <a name="custodian-validation"></a>Custo bir doğrulama

Şu anda yalnızca kuruluş kuruluşlarının çalışma alanlarına (Azure AD) dahil olan koruyucuları içeri Azure Active Directory destekliyoruz.

Custo bir içeri aktarma aracı, CSV dosyasındaki **Custo bir contactEmail** sütunundaki UPN değerini kullanarak koruyucuları bulur ve doğrular. Doğrulanmış olan koruyucular vakaya otomatik olarak eklenir ve vakanın **Veri kaynakları** sekmesinde listelenir. Koruyucu doğrulanamıyorsa, bunlar, bu durumda işler sekmesinde listelenen BulkAddCusto ötele işinin hata günlüğünde listelenir. Kayıt dışı koruyucular, vakaya eklenmez veya Veri kaynakları **sekmesinde listelenmiyor** .

### <a name="data-source-validation"></a>Veri kaynağı doğrulaması

Koruyucular doğrulandıktan ve vakaya eklendikten sonra, her birincil posta kutusu OneDrive bir custo OneDrive hesabı eklenir.

Öte yandan, bir custo ortak ile ilişkili diğer veri kaynaklarından (SharePoint siteleri, Microsoft Teams, Microsoft 365 Grupları veya Yammer grupları gibi) herhangi biri bulunamazsa, custo custo ortaklarına hiçbiri atanmaz ve Veri kaynakları üzerinde custo ortaklarının yanındaki Durum sütununda Doğrulanmadı değeri **görüntülenir**    sekmesini seçin.

Custo custo bir için doğrulanmış veri kaynakları eklemek için:

1. Veri **kaynakları sekmesinde** , doğrulanmadı veri kaynaklarını içeren bir özel dosya seçin.

2. Custo flyout sayfasında, custo ötelek konumlar bölümüne kaydırarak hem doğrulanmış hem de doğrulanmamış custo ötelenmiş veri kaynaklarını görüntüleyebilirsiniz.

3. Geçersiz **veri** kaynaklarını kaldırmak veya yeni veri kaynakları eklemek için, çıkış sayfasının en üstünde Düzenle'ye tıklayın.

4. Henüz doğru olmayan veri kaynaklarını kaldıran veya yeni bir veri kaynağı eklendiğinde, Veri kaynakları sekmesindeki custo  custo veri sütununda **Etkin** **değeri** görüntülenir. Daha önce geçersiz gibi görünen kaynakları eklemek için, aşağıdaki düzeltme adımlarını izleyin ve bunları custo veriye el ile ekleyin.

### <a name="remediating-invalid-data-sources"></a>Geçersiz veri kaynaklarını düzeltme

Daha önce geçersiz olan bir veri kaynağını el ile eklemek ve ilişkilendirmek için:

1. Veri kaynakları **sekmesinde** , daha önce geçersiz olan bir veri kaynağını el ile eklemek ve ilişkilendirmek için bir özel kişi seçin.

2. Posta **kutularını**, siteleri, posta kutularını, posta kutularını veya posta gruplarını özel kullanıcı Teams ilişkilendirmek için, uç Yammer Düzenle'ye tıklayın. Bunu yapmak için, uygun **veri** konumu türünün yanındaki Düzenle'ye tıklayın.

3. Tutma **ayarları** sayfasını görüntülemek **ve eklenen veri** kaynaklarının tutma ayarını yapılandırmak için Sonraki'ne tıklayın.

4. Gözden **geçir** koruyucular **sayfasını görüntülemek için Sonraki'ne** tıklayın ve sonra da **değişikliklerinizi kaydetmek için** Gönder'e tıklayın.
