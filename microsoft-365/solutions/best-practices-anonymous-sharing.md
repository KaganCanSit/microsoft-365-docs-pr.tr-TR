---
title: Kimliği doğrulanmamış paylaşım için en iyi yöntemler
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.collection:
- SPO_Content
- M365-collaboration
- m365solution-3tiersprotection
- m365solution-securecollab
- m365initiative-externalcollab
ms.custom:
- seo-marvel-apr2020
- admindeeplinkSPO
ms.localizationpriority: high
f1.keywords: NOCSH
recommendations: false
description: Bu makalede, kimliği doğrulanmamış kullanıcılarla dosya ve klasörleri paylaşmaya yönelik en iyi yöntemler hakkında bilgi edinebilirsiniz.
ms.openlocfilehash: ffe1219c468deef8c78e51e410e862ec52532483
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63323843"
---
# <a name="best-practices-for-sharing-files-and-folders-with-unauthenticated-users"></a>Kimliği doğrulanmamış kullanıcılarla dosya ve klasör paylaşmak için en iyi yöntemler

Kimliği doğrulanmamış paylaşım (*Herkes* bağlantıları) kullanışlı olabilir ve çeşitli senaryolarda kullanışlıdır. *Herkes* bağlantıları paylaşmanın en kolay yolutur: kişiler bağlantıyı kimlik doğrulaması olmadan açabilir ve başkalarına ücretsiz olarak iletir.

Genellikle, kuruluşta yer alan tüm içerik kimliği doğrulanmamış paylaşıma uygun değildir. Bu makale, kullanıcılarının dosya ve klasörlerin kimliği doğrulanmamış paylaşımını kullanabileceği ancak kuruluş içeriğini korumaya yardımcı olmak için korumanın bulunduğu bir ortam oluşturmanıza yardımcı olmak için kullanılabilir seçenekleri kapsar.

> [!NOTE]
> Kimliği doğrulanmamış paylaşımın çalışması için, bu özelliği hem organizasyonunız hem de kullanmakta olacağınız tek tek site veya ekip için etkinleştirmeniz gerekir. Etkinleştirmek [istediğiniz senaryo için bkz. Kuruluş](collaborate-with-people-outside-your-organization.md) dışındaki kişiler ile işbirliği.

## <a name="set-an-expiration-date-for-anyone-links"></a>Herkes bağlantıları için son kullanma tarihi ayarlama

Dosyalar çoğunlukla uzun süre sitelerde, gruplarda ve ekiplerde depolanır. Bazen dosyaların yıllar boyunca korunmasını gerektiren veri bekletme ilkeleri vardır. Bu tür dosyalar kimliği doğrulanmamış kişilerle paylaşılıyorsa, bu durum gelecekte beklenmedik dosyalara erişmeye ve dosyalarda değişikliklere neden olabilir. Bu olasılığı azaltmak için, Herkes bağlantıları için bir süre sonu *yapılandırabilirsiniz* .

Herkes *bağlantısının* süresi dolduğunda artık içeriğe erişmek için kullanılamaz.

Kuruluş genelindeki herkes bağlantıları için son kullanma tarihi ayarlamak için

1. Yönetim merkezini SharePoint, İlkeler'i **genişletin ve** sonra Paylaşım'ı <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**seçin**</a>.
1. Herkes **bağlantıları için süre sonu ve izin seçeneklerini belirleyin'in** altında Bu bağlantıların süresi bu kadar gün içinde **dolmaz onay** kutusunu seçin.</br>
   ![Kuruluş düzeyindeki SharePoint bağlantı süre sonu ayarlarının ekran görüntüsü.](../media/sharepoint-organization-anyone-link-expiration.png)
1. Kutuya gün sayısını yazın ve kaydet'e **tıklayın**.

Belirli bir siteki Herkes bağlantıları için son kullanma tarihi ayarlamak için

1. Site yönetim SharePoint açın, **Siteler'i genişletin ve** ardından Etkin <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**siteler'i seçin**</a>.
1. Değiştirmek istediğiniz siteyi ve sonra Paylaşım'ı **seçin**.
1. Herkes **bağlantıları için gelişmiş ayarlar'ın** altında, **Herkes bağlantılarının süre** sonu **altında, Kuruluş düzeyi ayarıyla aynı onay** kutusunu temizleyin.</br>
   ![Site düzeyinde SharePoint bağlantı süre sonu ayarlarının ekran görüntüsü.](../media/sharepoint-organization-anyone-link-expiration-site.png)
1. Bu **bağlantıların süresi bu kadar gün içinde dolacak** seçeneğini belirleyin ve kutuya gün sayısını yazın.
1. **Kaydet**'i seçin.

Herkes bağlantısının *süresi dolduğunda* dosya veya klasörün yeni bir Herkes bağlantısıyla yeniden *paylaşılana kadar olduğunu* unutmayın.

[Set-SPOSitesi'i kullanarak belirli bir OneDrive Herkes bağlantısının bitiş süresini ayarlayın](/powershell/module/sharepoint-online/set-sposite).

## <a name="set-link-permissions"></a>Bağlantı izinlerini ayarlama

Varsayılan olarak, *bir* dosyanın herkes bağlantıları, kişilerin dosyayı düzenlemesine izin ve Klasör  için herkes bağlantıları da kişilerin dosyaları düzenlemesine, görüntülemesine ve yeni dosyaları klasöre yüklemesine olanak sağlar. Dosyalar ve klasörler için bu izinleri bağımsız olarak yalnızca görüntüleme olarak değiştirebilirsiniz.

Kimliği doğrulanmamış paylaşıma izin vermek istiyor, ancak kimliği doğrulanmamış kişilerin kuruluş içeriğini değiştirme konusunda endişeleniyorsanız, dosya ve klasör izinlerini Görünüm olarak ayarlamayı **düşünebilirsiniz**.

Kuruluş genelindeki herkes bağlantısına izinler ayarlamak için

1. Yönetim SharePoint açın ve Paylaşım'ı <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**seçin**</a>.
1. " **Herkes" bağlantıları için gelişmiş ayarlar'ın** altında, kullanmak istediğiniz dosya ve klasör izinlerini seçin.</br>
   ![Kuruluş düzeyi SharePoint Bağlantı izinleri ayarlarının ekran görüntüsü.](../media/sharepoint-organization-anyone-link-permissions.png)

Herkes *bağlantısı* Görüntüle olarak **ayarlanmışsa**, kullanıcılar yine de dosyaları ve klasörleri konuklarla paylaşabilir ve belirli kişiler bağlantılarını kullanarak düzenleme *izinleri* düzenleyebilir. Bu bağlantılar, kuruluş dışından kişilerin konuk olarak kimlik doğrulamasını gerektirir ve bu bağlantılarla paylaşılan dosya ve klasörlerde konuk etkinliğini izleyebilir ve izleyebilirsiniz.

## <a name="set-default-link-type-to-only-work-for-people-in-your-organization"></a>Varsayılan bağlantı türünü yalnızca kuruluşta çalışan kişiler için çalışacak şekilde ayarlama

Herkes *paylaşımı* , sizin için etkinleştirildiğinde, varsayılan paylaşım bağlantısı normalde Herkes olarak **ayarlanır**. Bu, kullanıcılar için kullanışlı bir durumla birlikte, aslında doğrulanmamış paylaşım riskini artırabilir. Kullanıcı hassas bir belgeyi paylaştığınız sırada bağlantı türünü değiştirmeyi unutursa, yanlışlıkla kimlik doğrulaması gerektirmeyen bir paylaşım bağlantısı oluşturabilir.

Varsayılan bağlantı ayarını yalnızca kuruluş içindeki kişiler için işe yarar bir bağlantıyla değiştirerek bu riski azaltabilirsiniz. Kimliği doğrulanmamış kullanıcılarla paylaşmak isteyen kullanıcıların bu seçeneği özellikle seçmeleri gerekir.

Kuruluşun varsayılan dosya ve klasör paylaşımı bağlantısını ayarlamak için
1. Yönetim SharePoint açın ve Paylaşım'ı <a href="https://go.microsoft.com/fwlink/?linkid=2185222" target="_blank">**seçin**</a>.
1. Dosya **ve klasör bağlantıları'nın altında** Yalnızca **kuruluşta olan kişiler'i seçin**.

   ![Varsayılan bağlantı SharePoint ayarının ekran görüntüsü.](../media/sharepoint-default-sharing-link-company-link.png)

1. **Kaydet'i seçin**

Belirli bir site için varsayılan dosya ve klasör paylaşım bağlantısını ayarlamak için

1. Site yönetim SharePoint açın, **Siteler'i genişletin ve** ardından Etkin <a href="https://go.microsoft.com/fwlink/?linkid=2185220" target="_blank">**siteler'i seçin**</a>.
1. Değiştirmek istediğiniz siteyi ve sonra Paylaşım'ı **seçin**.
1. Varsayılan **paylaşım bağlantı türü'nin** altında Kuruluş **düzeyi ayarıyla aynı onay kutusunu** temizleyin.

   ![Site SharePoint bağlantı türü ayarlarının ekran görüntüsü.](../media/sharepoint-organization-anyone-link-permissions-site.png)

1. Yalnızca **kuruluşta olan kişiler'i seçin** ve sonra da Kaydet'i **seçin**.

## <a name="prevent-unauthenticated-sharing-of-sensitive-content"></a>Hassas içeriğin kimliği doğrulanmamış paylaşımını önleme

Hassas içeriğin [kimliği doğrulanmamış paylaşımını önlemek için veri kaybı önleme (DLP)](../compliance/dlp-learn-about-dlp.md) kullanabilirsiniz. Veri kaybını önleme özelliği, dosyanın kendisinde yer alan duyarlılık etiketine, bekletme etiketine veya hassas bilgilere dayalı olarak işlem gerçek dışı olabilir.

DLP kuralı oluşturmak için
1. Uyumluluk Microsoft 365 merkezinde Veri kaybı önleme [sayfasına gidin](https://compliance.microsoft.com/datalossprevention).
2. İlke **oluştur'a tıklayın**.
3. **Özel'i seçin** ve Sonraki'ne **tıklayın**.
4. İlke için bir ad yazın ve Sonraki'ye **tıklayın**.
5. **İlkenin uygulanıyor olduğu** konumlar sayfasında, site ve hesap ekleme  SharePoint tüm ayarları kapatın ve **OneDrive'e** **tıklayın**.
6. İlke **ayarlarını tanımla sayfasında** , Sonraki'ne **tıklayın**.
7. Gelişmiş **DLP kurallarını özelleştir sayfasında** Kural **oluştur'a tıklayın** ve kural için bir ad yazın.
8. **Koşullar'ın** altında Koşul **ekle'ye tıklayın** ve İçerik **içeriği'ne tıklayın**.
9. **Ekle'ye** tıklayın ve kimliği doğrulanmamış paylaşımını engellemek istediğiniz bilgi türünü seçin.

   ![Durum seçeneklerinin, hassas bilgi türlerinin, duyarlılık etiketlerinin ve bekletme etiketlerinin ekran görüntüsü.](../media/limit-accidental-exposure-dlp-conditions.png)

10. **Eylemler'in** altında **Eylem ekle'ye** tıklayın **ve Bu konumlarda erişimi kısıtla veya içeriği Microsoft 365 seçin**.
11. Microsoft 365 konumlarında erişimi kısıtla veya içeriği şifrele onay kutusunu seçin ve ardından "Bağlantıya sahip olan herkes" seçenekleriyle yalnızca içeriğe erişim izni verilen **kişiler'i** seçin.

      ![DLP kuralı eylem seçeneklerinin ekran görüntüsü.](../media/limit-accidental-exposure-dlp-anyone-links.png)

12. **Kaydet'e** ve sonra da Sonraki'ne **tıklayın**.
13. Test seçeneklerinizi seçin ve Sonraki'ye **tıklayın**.
14. **Gönder'e** ve ardından **Bitti'ye tıklayın**.

## <a name="protect-against-malicious-files"></a>Kötü amaçlı dosyalara karşı koruma

Anonim kullanıcıların dosyaları karşıya yüklemesine izin veri olduğunda, birinin kötü amaçlı dosyayı karşıya yükleme riski size artar. Daha Microsoft 365'de, *güvenli Kasa* olmayan karşıya yüklenen dosyaları otomatik olarak taramak ve karantinaya almak için Office 365 için Defender'daki Kasa Ekleri özelliğini kullanabilirsiniz.

Güvenli ekleri açmak için
1. Güvenlik [ve Uyumluluk Kasa AtP](https://protection.office.com/safeattachmentv2) Ekleri sayfasını açın.
2. Genel **ayarlar'a tıklayın**.
3. AtP'yi SharePoint, OneDrive için Microsoft Teams.

   ![Güvenlik ve Uyumluluk Merkezi'nde güvenli ekler ayarının ekran görüntüsü.](../media/safe-attachments-setting.png)

4. İsteğe bağlı olarak, Kasa'i de açabilirsiniz ve ardından Kaydet'e **tıklayın.**

Ek [rehberlik için SharePoint, OneDrive ve Microsoft Teams için ATP'ye](../security/office-365-security/mdo-for-spo-odb-and-teams.md) bakın SharePoint, OneDrive ve Microsoft Teams için [ATP'yi](../security/office-365-security/turn-on-mdo-for-spo-odb-and-teams.md) açma.

## <a name="add-copyright-information-to-your-files"></a>Dosyalarınıza telif hakkı bilgileri ekleme

Microsoft 365 Uyumluluk yönetim merkezinde duyarlılık etiketleri kullanıyorsanız, etiketlerinizi daha küçük belgelere filigran veya üst bilgi ya da alt bilgi eklemek için Office yapılandırabilirsiniz. Bu şekilde, paylaşılan dosyaların telif hakkı veya diğer sahiplik bilgilerini içerdiğindan emin olun.

Etiketli dosyaya alt bilgi eklemek için

1. Uyumluluk [Microsoft 365 merkezini açın](https://compliance.microsoft.com).
2. Sol gezintide, **Çözümler'in altında** Bilgi **koruma'ya tıklayın**.
3. Alt bilgi eklemek istediğiniz etikete tıklayın ve ardından Etiketi **düzenle'ye tıklayın**.
4. İçerik **işaretleme** sekmesine ulaşmak **için Sonraki'ne** tıklayın ve İçerik **işaretlemeyi aç'ı** açın.
5. Eklemek istediğiniz metin türünün onay kutusunu seçin ve Metni **özelleştir'e tıklayın**.
6. Belgelerinize eklemek istediğiniz metni yazın, istediğiniz metin seçeneklerini belirleyin ve ardından Kaydet'e **tıklayın**.</br>
   ![Duyarlılık etiketi için içerik işaretleme ayarlarının ekran görüntüsü.](../media/content-marking-for-anonymous-sharing.png)
7. **Sihirbazın** sonuna ulaşmak için Sonraki'ne tıklayın ve ardından Etiketi **kaydet'e tıklayın**.

Etiket için içerik işaretleme etkinleştirildiğinde, belirttiğiniz metin kullanıcı tarafından Office bir belgeye eklenir.

## <a name="see-also"></a>Ayrıca Bkz

[Duyarlılık etiketlerine genel bakış](/Office365/SecurityCompliance/sensitivity-labels)

[Konuklarla paylaşım sırasında dosyalarda yanlışlıkla açık kalma sürelerini sınırlama](share-limit-accidental-exposure.md)

[Güvenli bir konuk paylaşım ortamı oluşturma](create-secure-guest-sharing-environment.md)
