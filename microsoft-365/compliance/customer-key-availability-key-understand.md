---
title: Müşteri Anahtarı kullanılabilirliği anahtarı hakkında bilgi
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
description: Kaybolan Müşteri Anahtarlarını kurtarmak için kullanılan kullanılabilirlik anahtarı hakkında bilgi edinin.
ms.openlocfilehash: 72e66e9deb74400944c6ea65ea3ac167a703da26
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "62985706"
---
# <a name="learn-about-the-availability-key-for-customer-key"></a>Müşteri Anahtarı kullanılabilirliği anahtarı hakkında bilgi

Kullanılabilirlik anahtarı, veri şifreleme ilkesi  oluşturmanıza göre otomatik olarak oluşturulan ve sağlanan bir kök anahtardır. Microsoft 365 depolar ve kullanılabilirlik anahtarını korur. Kullanılabilirlik anahtarı işlevsel olarak, Müşteri Anahtarı ile hizmet şifrelemesi için tedarik etmekte olduğunuz iki kök anahtara benzer. Kullanılabilirlik tuşu, tuşları anahtar hiyerarşisinin bir alt katmanında kaydırr. Azure Anahtar Kasasında sağlamak ve yönetmekte olduğunuz anahtardan farklı olarak kullanılabilirlik anahtarına doğrudan erişebilirsiniz. Microsoft 365 hizmetleri, kullanılabilirlik anahtarını programlı olarak yönetir. Bu hizmetler, kullanılabilirlik anahtarına doğrudan erişimi hiçbir zaman içermeyen otomatik işlemleri başlatılır.

Kullanılabilirlik anahtarının birincil amacı, yönetiminiz tarafından belirlenemeyen kök anahtar kaybından kurtarma özelliği sağlamaktır. Kayıp, kötü amaçlı veya yanlış bir eyleme yol açabilir. Kök anahtarlarının kontrolünü kaybedersiniz, Microsoft Desteği'ne başvurun; Microsoft, kullanılabilirlik anahtarını kullanarak kurtarma sürecinde size yardımcı olur. Sağlanan yeni kök anahtarları olan yeni bir Veri Şifreleme İlkesine geçiş yapmak için kullanılabilirlik anahtarını kullanacaktır.

Depolama anahtarının durumu ve denetimi üç nedenle Azure Anahtar Kasası anahtarlarından kasıtlı olarak farklıdır:

- Kullanılabilirlik anahtarı, her iki Azure Anahtar Kasası anahtarı üzerinde denetim kaybolursa "camdan kesme" özelliği sağlar.
- Mantıksal denetimlerin ve güvenli depolama konumlarının ayrımı, tek bir saldırıya veya hata noktasına karşı savunma derinliği sağlar ve tüm anahtarların ve verilerinizin kaybına karşı koruma sağlar.
- Diğer hizmetler, geçici hatalar nedeniyle Azure Anahtar Microsoft 365'nde barındırılan tuşlara erişelamazsa, kullanılabilirlik anahtarı yüksek kullanılabilirlik özelliği sağlar. Bu kural yalnızca Exchange Online ve Skype Kurumsal şifreleme için geçerlidir. SharePoint Online, OneDrive İş ve Teams dosyalarınız, Microsoft'a kurtarma işlemini başlatması için açıkça bir talimat göstermedikçe hiçbir zaman kullanılabilirlik anahtarını kullanmaz.

Verilerinizi koruma sorumluluğunu paylaşmak, önemli yönetim için çeşitli korumaları ve süreçleri kullanmak, tüm anahtarların (ve dolayısıyla verilerinizin) kalıcı olarak kaybedilir veya yok edilmiş olması riskini son derece azaltır. Microsoft, hizmetten ayrılarak kullanılabilirlik anahtarının devre dışı bırakılacağı veya kabul edilmesiyle ilgili tüm yetkiyi size sağlar. Tasarım olarak, Microsoft'un hiç kimsenin kullanılabilirlik anahtarına erişimi yoktur: bu anahtara yalnızca Microsoft 365 koduyla erişilebilir.

Anahtarların [güvenliğini nasıl sağlarken daha](https://www.microsoft.com/trustcenter/Privacy/govt-requests-for-data) fazla bilgi için Microsoft Güven Merkezi'ne bakın.
  
## <a name="availability-key-uses"></a>Kullanılabilirlik anahtarı kullanımları

Kullanılabilirlik anahtarı, dış erkek faktör veya kötü niyetli insider'ın anahtar kasanız üzerinde kontrolü çaldır olduğu veya yanlışlıkla yanlış yapılan kök anahtar kaybına neden olduğu senaryolarda kurtarma özelliği sağlar. Bu kurtarma özelliği, Müşteri Anahtarı Microsoft 365 tüm hizmetler için geçerlidir. Tek tek hizmetler, kullanılabilirlik anahtarını farklı kullanır. Microsoft 365, kullanılabilirlik anahtarını yalnızca aşağıda açıklanan şekillerde kullanır.

### <a name="exchange-online-and-skype-for-business-uses"></a>Exchange Online ve Skype Kurumsal kullanımları

Kurtarma özelliğine ek olarak, Exchange Online ve Skype Kurumsal kök anahtarlara erişen hizmetle ilgili geçici veya aralıklı işlem sorunları sırasında veri kullanılabilirliğini sağlamak için kullanılabilirlik anahtarını kullanabilirsiniz. Geçici hatalar nedeniyle hizmet, Azure Anahtar Kasası'daki Müşteri Anahtarlarından herhangi birine ulaşama geldiğinde, hizmet otomatik olarak kullanılabilirlik anahtarını kullanır. Hizmet ASLA doğrudan kullanılabilirlik anahtarına gider.

Exchange Online ve Skype Kurumsal'daki otomatik sistemler, geçici hatalar sırasında kullanılabilirlik anahtarını kullanarak virüsten koruma, e-bulma, veri kaybını önleme, posta kutusu hareketleri ve veri dizini oluşturma gibi otomatik arka uç hizmetlerini destekleyabilmektedir.

### <a name="sharepoint-online-onedrive-for-business-and-teams-files-uses"></a>SharePoint Online, OneDrive İş ve Teams dosyaları

SharePoint Online, OneDrive İş ve Teams dosyaları için kullanılabilirlik anahtarı, kurtarma kapasitesinin dışında ASLA kullanılmaz ve müşterilerin Microsoft'a kurtarma senaryosu sırasında kullanılabilirlik anahtarının kullanımını başlatması için açıkça talimat göstermeleri gerekir. Otomatik hizmet işlemleri yalnızca Azure Anahtar kasasında yer alan Müşteri Anahtarlarınızı temel alır. Bu hizmetlerde anahtar hiyerarşisinin nasıl çalıştığını daha ayrıntılı bilgi için bkz. [SharePoint Online, OneDrive İş ve Teams dosyalarında kullanılabilirlik anahtarı kullanılır](#how-sharepoint-online-onedrive-for-business-and-teams-files-use-the-availability-key).

## <a name="availability-key-security"></a>Kullanılabilirlik anahtarı güvenliği

Microsoft, kullanılabilirlik anahtarının örneğini hazırlar ve bu anahtarı korumak için kapsamlı önlemler alarak veri korumanın sorumluluklarını size sunar. Microsoft, kullanılabilirlik anahtarının doğrudan kontrollerini müşterilere açığa çıkarmaz. Örneğin, yalnızca Azure Anahtar Kasasında sahip olduğunuz anahtarları döndürebilir (döndürün). Daha fazla bilgi için bkz [. Müşteri anahtarını veya uygunluk anahtarını döndürme veya döndürme](customer-key-availability-key-roll.md).

### <a name="availability-key-secret-stores"></a>Kullanılabilirlik anahtarı gizli depoları

Microsoft, kullanılabilirlik anahtarlarını müşteriye yönelik Azure Anahtar Kasası gibi erişim denetimli, iç gizli depolarda korur. Microsoft yöneticilerinin, içinde bulunan gizli bilgilere doğrudan erişmesini önlemek için erişim denetimleri uygulamamız gerekir. Tuş döndürme ve silme de dahil olmak üzere Gizli Depolama işlemleri, hiçbir zaman kullanılabilirlik anahtarına doğrudan erişimi içermeyen otomatik komutlar aracılığıyla gerçekleşir. Gizli depolama yönetim işlemleri belirli mühendisler ile sınırlıdır ve bir iç araç olan Lockbox üzerinden ayrıcalık yükseltmesi gerektirir. Ayrıcalık yükseltme için yönetici onayı ve gerekçelendirme gerekir. Kasa, erişimin süre sonu veya mühendisin oturumu kapatma süresinde otomatik erişim iptal süresiyle ilişkili olduğunu garantiler.

**Exchange Online ve Skype Kurumsal** anahtarları, Active Directory gizli Exchange Online bir depolamada depolanır. Kullanılabilirlik anahtarları, Active Directory Etki Alanı Denetleyicisi'nin içindeki kiracıya özgü kapsayıcılar içinde güvenli bir şekilde depolanır. Bu güvenli depolama konumu SharePoint Online, OneDrive İş ve Teams depolama alanından ayrıdır.

**SharePoint Online, OneDrive İş ve Teams kullanılabilirlik** anahtarları, hizmet ekibi tarafından yönetilen bir iç gizli depoda depolanır. Bu güvenli, gizli bilgi depolama hizmetinin uygulama uç noktaları olan ön uç sunucuları ve arka uç SQL Veritabanı bir adı vardır. Kullanılabilirlik anahtarları SQL Veritabanı içinde depolanır ve AES-256 ve HMAC birleşimini kullanarak saklanan kullanılabilirlik anahtarını şifrelemek için gizli depolama şifreleme anahtarları tarafından kaydır edilir (şifrelenmiş). Gizli depo şifreleme anahtarları, aynı SQL Veritabanı'in mantıksal olarak yalıtılmış bir bileşeninde depolanır ve Microsoft sertifika yetkilisi (CA) tarafından yönetilen sertifikalarda bulunan RSA-2048 anahtarları ile daha da şifrelenir. Bu sertifikalar, veritabanına yönelik işlemler gerçekleştirmek için gizli depo ön uç sunucularında depolanır.

### <a name="defense-in-depth"></a>Savunmada derinlikli

Microsoft, Microsoft Bulut'ta depolanan müşteri verilerinin gizliliğini, bütünlüğünü veya kullanılabilirliğini etkilemesini önlemek için kötü amaçlı kötü niyetli etkiyi önlemek üzere savunmada derinlikli bir strateji benimser. Gizli depo ve kullanılabilirlik anahtarının korunması için, hiyerarşik güvenlik stratejisinin bir parçası olarak özel koruma ve denetimler uygulanır.

Microsoft 365, kullanılabilirlik anahtarının yanlış kullanılmasını önlemek için yerleşik olarak sağlanır. Uygulama katmanı, kullanılabilirlik anahtarı da içinde olmak üzere, verilerin şifresini çözmek ve şifrelerini çözmek için kullanılacak tek yöntemdir. Yalnızca Microsoft 365 şifreleme ve şifre çözme etkinlikleri için anahtar hiyerarşisini yorumlama ve çapraz geçiş yapma özelliğine sahip olmalıdır. Müşteri Anahtarlarının depolama konumları, kullanılabilirlik anahtarları, diğer hiyerarşik anahtarlar ve müşteri verileri arasında mantıksal yalıtım vardır. Bu yalıtım, bir veya birden çok konumun güvenliği ihlal edilmiş durumda verilerin açığa kaldırılması riskini azalttı. Hiyerarşinin her katmanı, depolanan verileri ve gizli bilgileri korumak için 7 gün 24 izinsiz giriş algılama özellikleri yerleşik olarak bulunur.

Erişim denetimleri, kullanılabilirlik anahtarı gizli depoları da dahil olmak üzere iç sistemlere yetkisiz erişimi önlemek üzere uygulanır. Microsoft mühendislerinin kullanılabilirlik anahtarı gizli depolarına doğrudan erişimi yok. Erişim denetimleri hakkında ek ayrıntılar için, denetimler hakkında [daha fazla bilgi için Microsoft 365](/compliance/assurance/assurance-administrative-access-controls-overview).

Teknik denetimler, Microsoft personelinin yüksek derecede ayrıcalıklı hizmet hesaplarında oturum açmasını, aksi halde saldırganların kimliğine bürünmek için Microsoft hizmetleri. Örneğin, bu denetimler etkileşimli oturum açmayı önler.

Güvenlik günlüğü ve izleme denetimleri, verilerinizi ve verilerinizi toplama riskini azaltan bir diğer savunma Microsoft hizmetleri korumadır. Microsoft hizmet ekipleri, uyarılar ve denetim günlükleri oluşturan etkin izleme çözümleri dağıttı. Tüm hizmet ekipleri, günlüklerini toplanan ve işlenen merkezi bir depoya yükler. İç araçlar, hizmetlerin en uygun, güvenilir ve güvenli bir durumda çalışmasını onaylamak için kayıtları otomatik olarak inceler. Daha fazla inceleme için olağan dışı etkinlikler işaretlenir.

Microsoft Güvenlik İlkesinin olası ihlallerini belirten her günlük olayı hemen Microsoft güvenlik ekiplerinin dikkatini çeker. Microsoft 365, kullanılabilirlik anahtarı gizli depolarına erişim denen denenen uyarıları yapılandırmış olabilir. Microsoft personeli, erişim denetimleri tarafından yasaklanan ve korunan hizmet hesaplarında etkileşimli oturum açmayı denerse de uyarılar oluşturulur. Microsoft 365 ayrıca, normal temel işlemlerden gelen Microsoft 365 sapmaları üzerine uyarılar ve algılar. Bu hizmetlerde yanlış Microsoft 365 çalışan erkek faktörler, kırıcının Microsoft bulut ortamından çıkarıldığına neden olan uyarıları tetikler.

## <a name="use-the-availability-key-to-recover-from-key-loss"></a>Anahtar kaybından kurtarmak için kullanılabilirlik anahtarını kullanma

Müşteri Anahtarlarınız üzerinde denetimi kaybedersiniz, kullanılabilirlik anahtarı verilerinizi kurtarma ve yeniden şifreleme olanağı sağlar.

### <a name="recovery-procedure-for-exchange-online-and-skype-for-business"></a>E-Exchange Online kurtarma Skype Kurumsal

Müşteri Anahtarlarınız üzerindeki denetimi kaybedersiniz, kullanılabilirlik anahtarı verilerinizi kurtarma ve bu sorundan etkilenmeye devam etme Microsoft 365 yeniden çevrimiçi olma özelliği sağlar. Siz kurtarırken kullanılabilirlik anahtarı verilerinizi korumaya devam eder. Yüksek bir düzeyde, önemli bir kayıptan tamamen kurtarmak için yeni bir DEP oluşturmanız ve etkilenen kaynakları yeni ilkeye taşımanız gerekir.

Verilerinizi yeni Müşteri Anahtarları ile şifrelemek için Azure Anahtar Kasasında yeni anahtarlar oluşturun, yeni Müşteri Anahtarlarını kullanarak yeni bir DEP oluşturun, ardından yeni DEP'yi şu anda anahtarlarını kaybettiğiniz veya güvenliği ihlal edilmiş olan önceki DEP ile şifrelenmiş posta kutularına attayın.

Bu yeniden şifreleme işlemi 72 saat kadar sürebilir. BU, DEP'yi değiştir normal süredir.
  
### <a name="recovery-procedure-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>SharePoint Online, OneDrive İş ve Teams için kurtarma yordamı

SharePoint Online, OneDrive İş ve Teams dosyalarınız için, kullanılabilirlik anahtarı, kurtarma kapasitesinin dışında ASLA kullanılmaz. Microsoft'a kurtarma senaryosu sırasında kullanılabilirlik anahtarının kullanımını başlatması için açıkça talimatla belirtin. Kurtarma işlemini başlatmak için, Microsoft'a başvurarak kullanılabilirlik anahtarını etkinleştirin. Kullanılabilirlik anahtarı, etkinleştirildikten sonra otomatik olarak verilerinizin şifresini çözmek için kullanılır ve verileri yeni Müşteri Anahtarları ile ilişkilendirilmiş yeni oluşturulmuş bir DEP ile şifrelemenize olanak sağlar.  

Bu işlem, kuruluş site sayısıyla orantılıdır. Uygunluk anahtarını kullanmak için Microsoft'u aradıktan sonra, yaklaşık dört saat içinde tamamen çevrimiçi olursiniz.

## <a name="how-exchange-online-and-skype-for-business-use-the-availability-key"></a>Nasıl Exchange Online Skype Kurumsal kullanılabilirlik anahtarını kullanma

Müşteri Anahtarı ile DEP  oluşturan Microsoft 365, bu DEP ile ilişkilendirilmiş bir Veri Şifreleme İlkesi Anahtarı (DEP Anahtarı) üretir. Hizmet DEP Anahtarını üç kez şifreler: her müşteri anahtarıyla bir kez ve kullanılabilirlik anahtarıyla bir kez. DEP Anahtarının yalnızca şifreli sürümleri depolanır ve DEP Anahtarı yalnızca müşteri anahtarları veya kullanılabilirlik anahtarıyla şifresini çözebilir. Ardından DEP Anahtarı, tek tek posta kutularını şifrelenen Posta Kutusu Anahtarlarını şifrelemek için kullanılır.
  
Microsoft 365, şifresini çözmek ve müşterilerin hizmeti kullanırken veri sağlamak için bu işlemi izlersiniz:
  
1. Müşteri Anahtarını kullanarak DEP Anahtarının şifresini çözme.

2. Posta Kutusu Anahtarının şifresini çözmek için şifresi çözülmüş DEP Anahtarını kullanın.

3. Posta kutusunun şifresini çözmek için şifresi çözülmüş Posta Kutusu Anahtarını kullanarak posta kutusunun içindeki verilere erişebilirsiniz.

## <a name="how-sharepoint-online-onedrive-for-business-and-teams-files-use-the-availability-key"></a>Çevrimiçi SharePoint, OneDrive İş ve Teams dosyalarında kullanılabilirlik anahtarı nasıl kullanılır

Müşteri SharePoint için OneDrive İş Online ve çevrimiçi hizmet mimarisi ve uygulaması diğer özelliklerden Exchange Online ve Skype Kurumsal.
  
Kuruluş, müşteri tarafından yönetilen anahtarlar'a Microsoft 365 bir ara anahtar (TIK) oluşturur. Microsoft 365, her müşteri anahtarıyla birlikte TIK'i iki kez şifreler ve TIK'nin iki şifreli sürümünü depolar. Yalnızca TIK'nin şifreli sürümleri depolanır ve TIK yalnızca müşteri anahtarlarının şifresini çözebilir. Bundan sonra TIK, site anahtarlarını şifrelemek için kullanılır ve daha sonra blob tuşlarını şifrelemek için kullanılır (dosya öbek tuşları olarak da adlandırılan). Dosya boyutuna bağlı olarak, hizmet dosyayı her biri benzersiz bir anahtara sahip birden çok dosya öbeklerine bölüyor olabilir. Blobların (dosya öbekleri) kendileri blob tuşlarıyla şifrelenir ve Blob depolama Microsoft Azure depolanır.
  
Microsoft 365, müşterilerin hizmeti kullanırken şifresini çözmek ve müşteri dosyalarını sağlamak için bu süreci takip edersiniz:

1. Müşteri Anahtarını kullanarak TIK şifresini çözme.

2. Site anahtarının şifresini çözmek için şifresi çözülmüş TIK'i kullanın.

3. Blob anahtarının şifresini çözmek için şifresi çözülmüş site anahtarını kullanın.

4. Blob'un şifresini çözmek için şifresi çözülmüş blob anahtarını kullanın.

Microsoft 365, Azure Anahtar Kasaya hafif bir uzaklıkla iki şifre çözme isteği yayınarak TIK'nin şifresini çözebilir. İlk bitiren sonuç devam ediyor ve diğer istek iptal ediyor.
  
Müşteri anahtarlarınıza erişiminizi kaybetmeniz durumunda, Microsoft 365 de TIK'yi bir kullanılabilirlik anahtarıyla şifreler ve bunu her müşteri anahtarıyla şifrelenmiş TIK'larla birlikte depolar. Kullanılabilirlik anahtarıyla şifrelenmiş TIK, yalnızca müşteri anahtarlarına erişimi kaybettiğide veya yanlışlıkla kurtarma yoluna liste yapmak için Microsoft'u kullandığında kullanılır.
  
Kullanılabilirlik ve ölçek nedenleriyle, şifreleri çözülmüş TIK'lar zaman sınırlı bir bellek önbelleğinde önbelleğe alınmıştır. TIK önbelleğinin süresinin dolması için iki saat önce, Microsoft 365 çözmek için tüm TIK'lerin şifresini çözmeyi deneyin. TIK'lerin şifresini çözmek önbelleğin yaşam süresini uzatır. TIK şifre çözme işlemi önemli bir süre başarısız olursa, Microsoft 365 süresinin dolmadan önce mühendislik birimine bildirecek bir uyarı oluşturur. Ancak müşteri Microsoft'u ararsa Microsoft 365 işlemi başlatabilir. Bu işlem, Microsoft'un gizli mağazasında depolanan kullanılabilirlik anahtarıyla TIK'nin şifresini çözmeyi ve şifresini çözmüş TIK'ı ve müşteri tarafından sağlanan yeni bir Azure Anahtar Kasası anahtarları setlerini kullanarak kiracıyı yeniden eklemeyi içerir.
  
Bugünden sonra Müşteri Anahtarı, Azure blob depolama alanında depolanan SharePoint Online dosya verilerin şifreleme ve şifre çözme zincirinde yer alır, ancak SharePoint Online liste öğelerini veya SQL Veritabanı. Microsoft 365 yukarıda açıklanandan başka Exchange Online, Skype Kurumsal, SharePoint Online, OneDrive İş ve Teams dosyalarının kullanılabilirlik anahtarını müşteri tarafından başlatılana kadar kullanmaz. Müşteri verilerine insan erişimi Customer Lockbox tarafından korunur.

## <a name="availability-key-triggers"></a>Kullanılabilirlik anahtarı tetikleyicileri

Microsoft 365 durumlarda kullanılabilirlik anahtarını tetikler. Bu durumlar hizmete göre farklılık gösterir.

### <a name="triggers-for-exchange-online-and-skype-for-business"></a>Tetikler: Exchange Online ve Skype Kurumsal
  
1. Microsoft 365, Azure Anahtar Kasasında iki Müşteri Anahtarının konumunu belirlemek için posta kutusunun atandığı DEP'yi okur.

2. Microsoft 365 DEP'den iki Müşteri Anahtarından birini rastgele seçer ve Müşteri Anahtarını kullanarak DEP anahtarını kaydırmak için Azure Anahtar Kasaya bir istek gönderir.

3. Müşteri Anahtarını kullanarak DEP anahtarını kaydırma isteği başarısız olursa Microsoft 365 Azure Anahtar Kasası'ne ikinci bir istek gönderir. Bu kez alternatif (ikinci) Müşteri Anahtarını kullanma talimatı verilir.

4. İkinci istek Customer Key'i kullanarak DEP anahtarını kaydırmayı geri almak başarısız olursa, Microsoft 365 her iki isteğin sonuçlarını inceler.

    - İnceleme, isteklerin bir sistem HATASI döndürene karar verirse:

       - Microsoft 365 deP anahtarının şifresini çözmek için kullanılabilirlik anahtarını tetikler.

       - Microsoft 365 posta kutusu anahtarının şifresini çözmek ve kullanıcı isteğini tamamlamak için DEP anahtarını kullanır. 

       - Bu durumda, geçici bir HATAdan dolayı Azure Anahtar Kasası yanıt veremiyor veya ulaşamıyor.

    - Bu sorun, isteklerin ACCESS'in REDDEDİLDİ olarak döndüre olmadığını belirlerse:

       - Bu, müşteri anahtarlarının kullanılamaz duruma geldiğinin bilerek, yanlışlıkla veya kötü amaçlı bir eyleme neden olduğu anlamına gelir (örneğin, hizmetten ayrılma işleminin bir parçası olarak veri temizleme işlemi sırasında).

       - Bu durumda, kullanılabilirlik anahtarı yalnızca sistem eylemleri için kullanılır; kullanıcı eylemleri için kullanılamaz; kullanıcı isteği başarısız olur ve kullanıcı bir hata iletisi alır.

> [!IMPORTANT]
> Microsoft 365 ekleme bulut hizmetleri sağlamak için müşteri verileri üzerinde neden sağlama nedenlerine göre hizmet kodunda her zaman geçerli bir oturum açma belirteci vardır. Bu nedenle, kullanılabilirlik anahtarı silinene kadar arama dizini oluşturma veya posta kutularını taşıma gibi kullanıcı tarafından başlatılan veya şirket içinde yer alan Exchange Online ve Skype Kurumsal eylemlerde geri dönüş olarak kullanılabilir. Bu, hem geçici HATALAR hem de Azure Anahtar Kasası için ERIŞIM REDDEDILDI istekleri için geçerlidir.

### <a name="triggers-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>SharePoint Online, OneDrive İş ve Teams tetikleyicileri

SharePoint Online, OneDrive İş ve Teams dosyaları için kullanılabilirlik anahtarı, kurtarma kapasitesinin dışında ASLA kullanılmaz ve müşterilerin Microsoft'a kurtarma senaryosu sırasında kullanılabilirlik anahtarının kullanımını başlatması için açıkça talimat göstermeleri gerekir.

## <a name="audit-logs-and-the-availability-key"></a>Denetim günlükleri ve kullanılabilirlik anahtarı

Microsoft 365 otomatik sistemler, virüsten koruma, e-bulma, veri kaybını önleme ve veri dizin oluşturma gibi bulut hizmetleri sağlamak için tüm verileri sistem boyunca akar. Microsoft 365 bu etkinlik için müşteri tarafından görünür günlükler oluşturulmaz. Buna ek olarak, Microsoft personeli bu normal sistem işlemlerinin bir parçası olarak verilerinize erişmez.

### <a name="exchange-online-and-skype-for-business-availability-key-logging"></a>Exchange Online ve Skype Kurumsal anahtarı günlüğünü kaydetme

Hizmet Exchange Online için Skype Kurumsal anahtarına erişen kullanıcı, Microsoft 365 tarafından erişilebilir müşteri görünür günlüklerini Güvenlik ve Uyumluluk Merkezi'nde yayımlar. Hizmet kullanılabilirlik anahtarını her kullandığında, kullanılabilirlik anahtarı işlemi için bir denetim günlüğü kaydı oluşturulur. "Kullanılabilirlik Anahtarına Geri Dönüş" etkinlik türüne sahip "Müşteri Anahtar Hizmeti Şifrelemesi" adlı yeni bir kayıt türü yöneticilerin [](./search-the-audit-log-in-security-and-compliance.md) kullanılabilirlik anahtarı kayıtlarını görüntülemek için Birleşik Denetim Günlüğü arama sonuçlarını filtrelemesini sağlar.

Günlük kayıtları tarih, saat, etkinlik, kuruluş kimliği ve veri şifreleme ilkesi kimliği gibi öznitelikleri içerir. Kayıt, Birleşik Denetim Günlükleri kapsamında kullanılabilir ve Güvenlik ve Uyumluluk Merkezi Denetim & Günlüğü Araması sekmesinden erişilebilir.

![Kullanılabilirlik anahtarı olayları için denetim günlüğü araması](../media/customerkeyauditlogsearchavailabilitykeyloggingimage.png)

Exchange Online Skype Kurumsal için, kullanılabilirlik anahtarı kayıtları eklenen özel parametrelerle birlikte Office 365 Yönetimi Etkinliği ortak şemasını [](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema) kullanır: İlke Kimliği, Kapsam Anahtarı Sürüm Kimliği ve İstek Kimliği.

![Kullanılabilirlik anahtarı özel parametreleri](../media/customerkeyauditlogsearchavailabilitykeyloggingcustomparam.png)

### <a name="sharepoint-online-onedrive-for-business-and-teams-files-availability-key-logging"></a>SharePoint Online, OneDrive İş ve Teams kullanılabilirlik anahtarı günlüğü tutma

Kullanılabilirlik anahtarı günlüğü henüz bu hizmetlerde kullanılamaz. SharePoint Online, OneDrive İş ve Teams için, kullanılabilirlik anahtarı kurtarma amacıyla siz tarafından istenildiğinde yalnızca Microsoft tarafından etkinleştirilir. Sonuç olarak, bu hizmetler için kullanılabilirlik anahtarının kullanıldı olduğu her olayı zaten biliyorsunuz.

## <a name="availability-key-in-the-customer-key-hierarchy"></a>Müşteri Anahtarı hiyerarşisinde kullanılabilirlik anahtarı
  
Microsoft 365, kullanılabilirlik anahtarını kullanarak, anahtarların katmanını Müşteri Anahtarı hizmeti şifrelemesi için kurulan anahtar hiyerarşisinde daha alta kaydırıyor. Hizmetler arasında farklı anahtar hiyerarşileri vardır. Anahtar algoritmaları, her bir geçerli hizmetin hiyerarşisinde kullanılabilirlik anahtarları ile diğer tuşlar arasında da farklılık gösterir. Farklı hizmetler tarafından kullanılan kullanılabilirlik anahtarı algoritmaları şunlardır:

- Kullanılabilir Exchange Online ve Skype Kurumsal tuşları AES-256 kullanır.

- SharePoint Online, OneDrive İş ve Teams dosyaları için RSA-2048 kullanılır.

### <a name="encryption-ciphers-used-to-encrypt-keys-for-exchange-online-and-skype-for-business"></a>Şifreleme şifrelemesi, şifreleme ve şifreleme için Exchange Online için Skype Kurumsal

![Müşteri Anahtarı şifrelemesi Exchange Online şifreleme](../media/customerkeyencryptionhierarchiesexchangeskype.png)

### <a name="encryption-ciphers-used-to-encrypt-keys-for-sharepoint-online-and-onedrive-for-business"></a>SharePoint Online ve diğer kodlar için şifreleme şifrelemesi OneDrive İş

![Çevrimiçi Müşteri Anahtarı için SharePoint şifreleme şifrelemeleri](../media/customerkeyencryptionhierarchiessharepointonedriveteamsfiles.png)

## <a name="related-articles"></a>İlgili makaleler

- [Müşteri Anahtarı ile Hizmet şifrelemesi](customer-key-overview.md)

- [Müşteri Anahtarını Ayarlama](customer-key-set-up.md)

- [Müşteri Anahtarını Yönet](customer-key-manage.md)

- [Müşteri Anahtarını veya uygunluk anahtarını döndürme veya döndürme](customer-key-availability-key-roll.md)