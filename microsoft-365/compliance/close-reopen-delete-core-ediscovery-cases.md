---
title: Çekirdek eK bulma olaylarını kapatma, yeniden açma ve silme
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Bu makalede, Çekirdek eKbulma servis durumlarının nasıl yönetil olduğu açıklanmıştır. Buna büyük/küçük harf kapatma, kapalı bir vakayı yeniden açma ve vakayı silme dahildir.
ms.openlocfilehash: a210a06da2effb0b17d526a09499a65fa59bfeb4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62983604"
---
# <a name="close-reopen-and-delete-a-core-ediscovery-case"></a>Core eBulma vakalarını kapatma, yeniden açma ve silme

Bu makalede, bu durumlarda Core eKovery olaylarını kapatma, yeniden açma ve silme Microsoft 365.

## <a name="close-a-case"></a>Vakayı kapatma

Core eKovery davalarının destekteki dava veya soruşturma tamamlandıktan sonra, vakayı kapatmış oluruz. Bir vakayı kapatarak neler olduğunu burada açıklarız:
  
- Olayda eBulma  ayrıcatıları varsa, bunlar kapat olur. Tutma kapat edildikten sonra, içeriğin tut olduğu konumlara 30 günlük bir yetkisiz kullanım süresi (gecikme süresi olarak *adlandırılan) uygulanır*. Bu, içeriğin hemen silinmesini önlemeye yardımcı olur ve yöneticilere, gecikme süresi sona erdikten sonra kalıcı olarak silinmeden önce içeriği arama ve geri yükleme fırsatı sağlar. Daha fazla bilgi için bkz [. eBulma tutmadan içerik konumlarını kaldırma](create-ediscovery-holds.md#removing-content-locations-from-an-ediscovery-hold).

- Vakayı kapatma, yalnızca bu vakayla ilişkilendirilmiş olan tılaları kapatır. İçerik yerine başka bekletmeler yerleştirilirse (Mahkeme Tutma, bekletme ilkesi veya farklı bir Çekirdek eKbulma durumundan bekletme gibi) bu bekletmeler yine korunur.

- Olay, çalışma sayfasındaki Core eKbulma sayfasında Microsoft 365 uyumluluk merkezi. Kapalı durumdaki bir vakanın ayrıntıları, tutma, aramalar ve üyeleri korunur.

- Bir vakayı kapattıktan sonra düzenleyebilirsiniz. Örneğin üyeleri ekp veya kaldırabilir, arama oluşturabilir ve arama sonuçlarını dışarı aktarabilirsiniz. Etkin ve kapalı vakalar arasındaki en önemli fark, bir vaka kapatılanda eKbulma'da ayrı kalmanın kapalı olmasıdır.

Vakayı kapatmak için:
  
1. Çalışma Microsoft 365 uyumluluk merkezi, **eBulma** >  **Puanı'ne** tıklayın ve kurumuzda Çekirdek eKbulma servis durumlarının listesini görüntülemek için.

2. Kapatmak istediğiniz vakanın adına tıklayın.

   ![Vaka giriş sayfasında vakayı kapat.](../media/eDiscoveryCaseHomePage.png)

3. Giriş sayfasında, Durum'ın **altında Vakayı** **kapat'a tıklayın**.

    Olayla ilişkilendirilmiş olan 10'un kapatılamayacaklarını söyleyen bir uyarı görüntülenir.

4. **Vakayı** kapatmak için Evet'e tıklayın.

    Olay giriş sayfasındaki durum, Etkin'den **Kapanış'a** **değiştirilir**.

5. Core **eDiscovery sayfasında** , kapatılan **vakanın** durumunu güncelleştirmek için Yenile'yi tıklatın. Kapatma işleminin tamamlanması 60 dakika kadar sürebilir.

    İşlem tamamlandığında, Çekirdek eKbulma sayfasında **vakanın** **durumu Kapalı olarak** değiştirilir.

## <a name="reopen-a-closed-case"></a>Kapalı durumdaki bir vakayı yeniden açma

Bir vakayı yeniden açtığnda, servis nedeniyle kapatılan eBulma çıtaları otomatik olarak yeniden geçerli olmayacaktır. Olay yeniden açıldıktan sonra, 10.000'de 10. Bir basılı tutunmayı açmak için, bunu seçerek çıkış sayfasını görüntüleyebilirsiniz ve sonra Durum iki **durumlu düğmeyi** Açık olarak **ayarlayın**.
  
1. Çalışma Microsoft 365 uyumluluk merkezi, **eBulma** >  **Puanı'ne** tıklayın ve kurumuzda Çekirdek eKbulma servis durumlarının listesini görüntülemek için.

2. Yeniden açmak istediğiniz vakanın adına tıklayın.

   ![Kapalı durumdaki bir vakayı yeniden açma.](../media/eDiscoveryCaseHomePageReopen.png)

3. Giriş sayfasında, Durum'ın altında **Büyük/küçük** harfe yeniden **aç'a tıklayın**.

    Kapatılan olayla ilişkilendirilmiş uzlaydın otomatik olarak açık olmadığını söyleyen bir uyarı görüntülenir.

4. **Vakayı yeniden** açmak için Evet'e tıklayın.

    Büyük/yeni olay giriş sayfası çıkış sayfasındaki durum, Kapalı'dan **Etkin'e** **değiştirilir**.

5. Core **eDiscovery sayfasında** , yeniden **açılan** vakanın durumunu güncelleştirmek için Yenile'yi tıklatın. Yeniden açma işleminin tamamlanması 60 dakika kadar sürebilir. 

    İşlem tamamlandığında, Çekirdek eBulma sayfasında vakanın **durumu Etkin olarak** değiştirilir.

6. (İsteğe bağlı) Yeniden açılan vakayla ilişkilendirilmiş 10.000 01.000'i açmak için, Sındır sekmesine  gidin, bir tutma seçin ve sonra da Tutma sayfası üzerinde Durum'un altındaki onay kutusunu seçin.
  
## <a name="delete-a-case"></a>Vakayı silme

Etkin ve kapalı durumdaki Çekirdek eKbulma servis durumlarını da silebilirsiniz. Bir vakayı sildikten sonra, olayda yapılan tüm aramalar ve dışarı aktarmalar silinir ve olay, durum listesinden Çekirdek **eBulma** sayfasındaki servis Microsoft 365 uyumluluk merkezi. Silinen bir vakayı yeniden açemezsiniz.

Bir vakayı silebilirsiniz (etkin veya kapalı olsa da), önce olayla ilişkilendirilmiş *tüm* eBulma 10'larını silebilirsiniz. Bu durum, Kapalı durumuyla birlikte silmeyi **de içerir**. 

eBulma ayrımlarını silmek için:

1. Silmek istediğiniz **durumda** 10 A0 sekmesine gidin.

2. Silmek istediğiniz  basılı tutun.

3. Uçarak çıkış sayfasında Sil'e **tıklayın**.

      ![eBulma ayrımlarını silme.](../media/DeleteeDiscoveryHold.png)

Vakayı silmek için:

1. Çalışma Microsoft 365 uyumluluk merkezi, **eBulma** >  **Puanı'ne** tıklayın ve kurumuzda Çekirdek eKbulma servis durumlarının listesini görüntülemek için.

2. Silmek istediğiniz vakanın adına tıklayın.

3. Vaka giriş sayfasında, Durum altında **, Büyük/** küçük harf **sil'e tıklayın**.

      ![Vakayı silme.](../media/eDiscoveryCaseHomePageDelete.png)

Silmeye çalıştığınız olayda eBulma  ayrıcalıkları varsa, bir hata iletisi alırsınız. Vakayla ilişkilendirilmiş tüm dırmaları silmeniz ve ardından vakayı silmeyi yeniden denemeniz gerekir.
