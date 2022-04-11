---
title: Müşteri Anahtarı için uygunluk anahtarı hakkında daha fazla bilgi edinme
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- MET150
description: Kayıp Müşteri Anahtarlarını kurtarmak için kullanılan kullanılabilirlik anahtarı hakkında bilgi edinin.
ms.openlocfilehash: 1fd80d23980957402ae7d5e79a91e57d28df38f9
ms.sourcegitcommit: 9ba00298cfa9ae293e4a57650965fdb3e8ffe07b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2022
ms.locfileid: "64761847"
---
# <a name="learn-about-the-availability-key-for-customer-key"></a>Müşteri Anahtarı için uygunluk anahtarı hakkında daha fazla bilgi edinme

Kullanılabilirlik anahtarı, veri şifreleme ilkesi oluşturduğunuzda otomatik olarak oluşturulan ve sağlanan bir kök anahtardır. Microsoft 365 kullanılabilirlik anahtarını depolar ve korur. Kullanılabilirlik anahtarı, Müşteri Anahtarı ile hizmet şifrelemesi için sağladığınız iki kök anahtara benzer. Kullanılabilirlik anahtarı, anahtarları anahtar hiyerarşisinde bir katmanın altında sarmalar. Azure Key Vault'da sağladığınız ve yönettiğiniz anahtarların aksine, kullanılabilirlik anahtarına doğrudan erişemezsiniz. Microsoft 365 otomatik hizmetler kullanılabilirlik anahtarını programlı olarak yönetir. Bu hizmetler, hiçbir zaman kullanılabilirlik anahtarına doğrudan erişim içermeyen otomatik işlemleri başlatır.

Kullanılabilirlik anahtarının birincil amacı, yönettiğiniz beklenmedik kök anahtar kaybından kurtarma özelliği sağlamaktır. Kayıp, yanlış yönetimin veya kötü amaçlı eylemin bir sonucu olabilir. Kök anahtarlarınızın denetimini kaybederseniz Microsoft Desteği ile iletişime geçin; Microsoft, kullanılabilirlik anahtarını kullanarak kurtarma işleminde size yardımcı olur. Sağladığınız yeni kök anahtarlarla yeni bir Veri Şifreleme İlkesine geçmek için kullanılabilirlik anahtarını kullanacaksınız.

Kullanılabilirlik anahtarının Depolama ve denetimi, azure Key Vault anahtarlarından üç nedenden dolayı kasıtlı olarak farklıdır:

- Kullanılabilirlik anahtarı, her iki Azure Key Vault anahtarı üzerindeki denetim kaybolursa kurtarma, "kesme" özelliği sağlar.
- Mantıksal denetimlerin ve güvenli depolama konumlarının ayrılması derinlemesine savunma sağlar ve tüm anahtarların ve verilerinizin tek bir saldırı veya hata noktasına karşı korunmasını sağlar.
- Kullanılabilirlik anahtarı, Microsoft 365 hizmetlerin geçici hatalar nedeniyle Azure Key Vault'da barındırılan anahtarlara ulaşamaması durumunda yüksek kullanılabilirlik özelliği sağlar. Bu kural yalnızca Exchange Online ve Skype Kurumsal hizmet şifrelemesi için geçerlidir. SharePoint Online, OneDrive İş ve Teams dosyaları, Microsoft'a kurtarma işlemini başlatmasını açıkça söylemediğiniz sürece hiçbir zaman kullanılabilirlik anahtarını kullanmaz.

Anahtar yönetimi için çeşitli korumaları ve işlemleri kullanarak verilerinizi koruma sorumluluğunu paylaşmak, sonuçta tüm anahtarların (ve dolayısıyla verilerinizin) kalıcı olarak kaybolması veya yok edilmesi riskini azaltır. Microsoft, hizmetten ayrıldığınızda kullanılabilirlik anahtarının devre dışı bırakılması veya yok edilmesi konusunda size tek yetki verir. Tasarım gereği, Microsoft'taki hiç kimsenin kullanılabilirlik anahtarına erişimi yoktur: yalnızca Microsoft 365 hizmet koduyla erişilebilir.

Anahtarların güvenliğini sağlama hakkında daha fazla bilgi için [bkz. Microsoft Güven Merkezi](https://www.microsoft.com/trustcenter/Privacy/govt-requests-for-data) .
  
## <a name="availability-key-uses"></a>Kullanılabilirlik anahtarı kullanımları

Kullanılabilirlik anahtarı, dış bir malefactor veya kötü amaçlı insider'ın anahtar kasanızın denetimini çaldığı veya yanlışlıkla yanlış yönetimin kök anahtar kaybına neden olduğu senaryolar için kurtarma özelliği sağlar. Bu kurtarma özelliği, Müşteri Anahtarı ile uyumlu tüm Microsoft 365 hizmetleri için geçerlidir. Tek tek hizmetler kullanılabilirlik anahtarını farklı kullanır. Microsoft 365 yalnızca aşağıda açıklanan yollarla kullanılabilirlik anahtarını kullanır.

### <a name="exchange-online-and-skype-for-business-uses"></a>Exchange Online ve Skype Kurumsal kullanımları

Kurtarma özelliğine ek olarak, Exchange Online ve Skype Kurumsal, kök anahtarlara erişen hizmetle ilgili geçici veya aralıklı operasyonel sorunlar sırasında veri kullanılabilirliğini sağlamak için kullanılabilirlik anahtarını kullanır. Hizmet, geçici hatalar nedeniyle Azure Key Vault'da Müşteri Anahtarlarınızdan herhangi birini ulaşamadığında, hizmet otomatik olarak kullanılabilirlik anahtarını kullanır. Hizmet ASLA doğrudan kullanılabilirlik anahtarına gider.

Exchange Online ve Skype Kurumsal'daki otomatik sistemler virüsten koruma, e-bulma, veri kaybı önleme, posta kutusu taşımaları ve veri dizini oluşturma gibi otomatik arka uç hizmetlerini desteklemek için geçici hatalar sırasında kullanılabilirlik anahtarını kullanabilir.

### <a name="sharepoint-online-onedrive-for-business-and-teams-files-uses"></a>SharePoint Online, OneDrive İş ve Teams dosyaları kullanır

SharePoint Online, OneDrive İş ve Teams dosyaları için, kullanılabilirlik anahtarı hiçbir zaman kurtarma özelliği dışında kullanılmaz ve müşteriler microsoft'a bir kurtarma senaryosu sırasında kullanılabilirlik anahtarının kullanımını başlatmasını açıkça bildirmelidir. Otomatik hizmet işlemleri yalnızca Azure Key Vault'taki Müşteri Anahtarlarınızı kullanır. Anahtar hiyerarşisinin bu hizmetler için nasıl çalıştığı hakkında ayrıntılı bilgi için bkz. [SharePoint Online, OneDrive İş ve Teams dosyaları kullanılabilirlik anahtarını kullanma](#how-sharepoint-online-onedrive-for-business-and-teams-files-use-the-availability-key).

## <a name="availability-key-security"></a>Kullanılabilirlik anahtarı güvenliği

Microsoft, kullanılabilirlik anahtarının örneğini oluşturarak ve bunu korumak için kapsamlı önlemler alarak veri koruma sorumluluğunu sizinle paylaşır. Microsoft, kullanılabilirlik anahtarının doğrudan denetimini müşterilere sunmaz. Örneğin, yalnızca Azure Key Vault sahip olduğunuz anahtarları yuvarlayabilir (döndürebilirsiniz). Daha fazla bilgi için bkz. [Müşteri anahtarını veya kullanılabilirlik anahtarını alma veya döndürme](customer-key-availability-key-roll.md).

### <a name="availability-key-secret-stores"></a>Kullanılabilirlik anahtarı gizli depoları

Microsoft, müşteriye yönelik Azure Key Vault gibi erişim denetimli iç gizli dizi depolarında kullanılabilirlik anahtarlarını korur. Microsoft yöneticilerinin içinde yer alan gizli dizilere doğrudan erişmesini önlemek için erişim denetimleri uygularız. Anahtar döndürme ve silme de dahil olmak üzere Gizli Dizi Deposu işlemleri, kullanılabilirlik anahtarına hiçbir zaman doğrudan erişim içermeyen otomatik komutlar aracılığıyla gerçekleşir. Gizli dizi deposu yönetim işlemleri belirli mühendislerle sınırlıdır ve bir iç araç olan Lockbox aracılığıyla ayrıcalık yükseltmesi gerektirir. Ayrıcalık yükseltme, verilmeden önce yönetici onayı ve gerekçe gerektirir. Kasa, süre sonu veya mühendis oturumu kapatılırken otomatik erişim iptali ile erişimin zamana bağlı olmasını sağlar.

**Exchange Online ve Skype Kurumsal** kullanılabilirlik anahtarları bir Exchange Online Active Directory gizli dizi deposunda depolanır. Kullanılabilirlik anahtarları, Active Directory Etki Alanı Denetleyicisi içindeki kiracıya özgü kapsayıcılarda güvenli bir şekilde depolanır. Bu güvenli depolama konumu, SharePoint Online, OneDrive İş ve Teams dosyaları gizli deposundan ayrı ve yalıtılır.

**SharePoint Online, OneDrive İş ve Teams dosyaları** kullanılabilirlik anahtarları hizmet ekibi tarafından yönetilen bir iç gizli dizi deposunda depolanır. Bu güvenli gizli dizi depolama hizmeti, uygulama uç noktalarına ve arka uç olarak SQL Veritabanı sahip ön uç sunuculara sahiptir. Kullanılabilirlik anahtarları SQL Veritabanı depolanır ve bekleyen kullanılabilirlik anahtarını şifrelemek için AES-256 ve HMAC'nin birleşimini kullanan gizli depolama şifreleme anahtarları tarafından sarmalanmıştır (şifrelenir). Gizli dizi deposu şifreleme anahtarları, aynı SQL Veritabanı mantıksal olarak yalıtılmış bir bileşeninde depolanır ve Microsoft sertifika yetkilisi (CA) tarafından yönetilen sertifikalarda bulunan RSA-2048 anahtarlarıyla daha da şifrelenir. Bu sertifikalar, veritabanına yönelik işlemler gerçekleştiren gizli dizi deposu ön uç sunucularında depolanır.

### <a name="defense-in-depth"></a>Derinlemesine savunma

Microsoft, kötü amaçlı aktörlerin Microsoft Bulut'ta depolanan müşteri verilerinin gizliliğini, bütünlüğünü veya kullanılabilirliğini etkilemesini önlemek için kapsamlı bir savunma stratejisi kullanmaktadır. Ayrıntılı güvenlik stratejisinin bir parçası olarak gizli depoyu ve kullanılabilirlik anahtarını korumak için belirli önleyici ve dedektif denetimleri uygulanır.

Microsoft 365, kullanılabilirlik anahtarının kötüye kullanılmasını önlemek için oluşturulmuş. Uygulama katmanı, kullanılabilirlik anahtarı da dahil olmak üzere anahtarların verileri şifrelemek ve şifresini çözmek için kullanabildiği tek yöntemdir. Yalnızca Microsoft 365 hizmet kodu şifreleme ve şifre çözme etkinlikleri için anahtar hiyerarşisini yorumlayıp geçiş yapma özelliğine sahiptir. Müşteri Anahtarlarının depolama konumları, kullanılabilirlik anahtarları, diğer hiyerarşik anahtarlar ve müşteri verileri arasında mantıksal yalıtım vardır. Bu yalıtım, bir veya daha fazla konumun gizliliğinin tehlikeye atıldığı durumlarda verilerin açığa çıkarma riskini azaltır. Hiyerarşideki her katman, depolanan verileri ve gizli dizileri korumak için 7/24 yetkisiz erişim algılama özelliklerine sahiptir.

Erişim denetimleri, kullanılabilirlik anahtarı gizli depoları dahil olmak üzere iç sistemlere yetkisiz erişimi önlemek için uygulanır. Microsoft mühendislerinin kullanılabilirlik anahtarı gizli dizi depolarına doğrudan erişimi yoktur. Erişim denetimleri hakkında daha fazla ayrıntı için [Microsoft 365'da Yönetim Erişim Denetimleri'ni](/compliance/assurance/assurance-administrative-access-controls-overview) gözden geçirin.

Teknik denetimler, Microsoft personelinin yüksek ayrıcalıklı hizmet hesaplarında oturum açmasını önler ve bu da saldırganlar tarafından Microsoft hizmetleri kimliğine bürünmek için kullanılabilir. Örneğin, bu denetimler etkileşimli oturum açmayı engeller.

Güvenlik günlüğü ve izleme denetimleri, Microsoft hizmetleri ve verilerinize yönelik riski azaltan bir diğer kapsamlı savunma korumasıdır. Microsoft hizmet ekipleri, uyarılar ve denetim günlükleri oluşturan etkin izleme çözümleri dağıttı. Tüm hizmet ekipleri günlüklerini günlüklerin toplandığı ve işlendiği merkezi bir depoya yükler. İç araçlar, hizmetlerin en uygun, dayanıklı ve güvenli bir durumda çalıştığını onaylamak için kayıtları otomatik olarak inceler. Daha fazla inceleme için olağan dışı etkinliklere bayrak eklendi.

Microsoft Güvenlik İlkesi'nin olası bir ihlalini gösteren tüm günlük olayları hemen Microsoft güvenlik ekiplerinin dikkatine getirilir. Microsoft 365 güvenliği, kullanılabilirlik anahtarı gizli depolarına erişim girişimini algılamak için uyarılar yapılandırdı. Ayrıca, Microsoft personeli erişim denetimleri tarafından yasaklanan ve korunan hizmet hesaplarında etkileşimli oturum açmayı denerse uyarılar da oluşturulur. Microsoft 365 güvenlik ayrıca Microsoft 365 hizmetinin normal temel işlemlerden sapmalarını algılar ve uyarır. Microsoft 365 hizmetlerini kötüye kullanma girişiminde bulunan malefactor'lar, uyarıları tetikleyerek suçlunun Microsoft bulut ortamından çıkarılmasına neden olur.

## <a name="use-the-availability-key-to-recover-from-key-loss"></a>Anahtar kaybından kurtarmak için kullanılabilirlik anahtarını kullanma

Müşteri Anahtarlarınızın denetimini kaybederseniz, kullanılabilirlik anahtarı verilerinizi kurtarmanızı ve yeniden şifrelemenizi sağlar.

### <a name="recovery-procedure-for-exchange-online-and-skype-for-business"></a>Exchange Online ve Skype Kurumsal için kurtarma yordamı

Müşteri Anahtarlarınızın denetimini kaybederseniz kullanılabilirlik anahtarı, verilerinizi kurtarma ve etkilenen Microsoft 365 kaynaklarınızı yeniden çevrimiçi yapma olanağı sağlar. Kullanılabilirlik anahtarı, kurtarma sırasında verilerinizi korumaya devam eder. Yüksek düzeyde, anahtar kaybından tamamen kurtulmak için yeni bir DEP oluşturmanız ve etkilenen kaynakları yeni ilkeye taşımanız gerekir.

Verilerinizi yeni Müşteri Anahtarları ile şifrelemek için Azure Key Vault yeni anahtarlar oluşturun, yeni Müşteri Anahtarlarını kullanarak yeni bir DEP oluşturun, ardından yeni DEP'yi anahtarların kaybolduğu veya güvenliğinin aşıldığı önceki DEP ile şifrelenmiş olan posta kutularına atayın.

Bu yeniden şifreleme işlemi 72 saate kadar sürebilir. Bu, DEP'yi değiştirdiğiniz standart süredir.
  
### <a name="recovery-procedure-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>SharePoint Online, OneDrive İş ve Teams dosyaları için kurtarma yordamı

SharePoint Online, OneDrive İş ve Teams dosyaları için kullanılabilirlik anahtarı kurtarma özelliğinin dışında ASLA kullanılmaz. Microsoft'a bir kurtarma senaryosu sırasında kullanılabilirlik anahtarının kullanımını başlatmasını açıkça bildirmelisiniz. Kurtarma işlemini başlatmak için Microsoft'a başvurarak kullanılabilirlik anahtarını etkinleştirin. Etkinleştirildikten sonra, kullanılabilirlik anahtarı verilerinizin şifresini çözmek için otomatik olarak kullanılır ve bu sayede verileri yeni Müşteri Anahtarları ile ilişkilendirilmiş yeni oluşturulan bir DEP ile şifreleyebilirsiniz.  

Bu işlem, kuruluşunuzdaki site sayısıyla orantılıdır. Kullanılabilirlik anahtarını kullanmak için Microsoft'u aradıktan sonra yaklaşık dört saat içinde tamamen çevrimiçi olmanız gerekir.

## <a name="how-exchange-online-and-skype-for-business-use-the-availability-key"></a>Exchange Online ve Skype Kurumsal kullanılabilirlik anahtarını kullanma

Müşteri Anahtarı ile bir DEP oluşturduğunuzda, Microsoft 365 bu DEP ile ilişkili bir Veri Şifreleme İlkesi Anahtarı (DEP Anahtarı) oluşturur. Hizmet, DEP Anahtarını üç kez şifreler: bir kez müşteri anahtarlarının her biriyle ve bir kez de kullanılabilirlik anahtarıyla. Yalnızca DEP Anahtarının şifrelenmiş sürümleri depolanır ve DEP Anahtarının şifresi yalnızca müşteri anahtarları veya kullanılabilirlik anahtarıyla çözülebilir. Ardından DEP Anahtarı, posta kutularını tek tek şifreleyen Posta Kutusu Anahtarlarını şifrelemek için kullanılır.
  
Microsoft 365 müşteriler hizmeti kullanırken verilerin şifresini çözmek ve veri sağlamak için bu işlemi izler:
  
1. Müşteri Anahtarını kullanarak DEP Anahtarının şifresini çözme.

2. Bir Posta Kutusu Anahtarının şifresini çözmek için şifresi çözülmüş DEP Anahtarını kullanın.

3. Posta kutusunun şifresini çözmek için şifresi çözülmüş Posta Kutusu Anahtarı'nı kullanarak posta kutusu içindeki verilere erişmenizi sağlayın.

## <a name="how-sharepoint-online-onedrive-for-business-and-teams-files-use-the-availability-key"></a>SharePoint Online, OneDrive İş ve Teams dosyaları kullanılabilirlik anahtarını nasıl kullanır?

Müşteri Anahtarı ve kullanılabilirlik anahtarı için SharePoint Online ve OneDrive İş mimarisi ve uygulaması, Exchange Online ve Skype Kurumsal farklıdır.
  
Bir kuruluş müşteri tarafından yönetilen anahtarlara geçtiğinde Microsoft 365 kuruluşa özgü bir ara anahtar (TIK) oluşturur. Microsoft 365, TIK'yi her müşteri anahtarıyla bir kez iki kez şifreler ve TIK'nin iki şifrelenmiş sürümünü depolar. Yalnızca TIK'nin şifrelenmiş sürümleri depolanır ve bir TIK'nin şifresi yalnızca müşteri anahtarlarıyla çözülebilir. TIK daha sonra blob anahtarlarını şifrelemek için kullanılan site anahtarlarını şifrelemek için kullanılır (dosya öbek anahtarları olarak da adlandırılır). Dosya boyutuna bağlı olarak, hizmet bir dosyayı benzersiz anahtara sahip birden çok dosya öbeklerine bölebilir. Blobların (dosya öbekleri) kendileri blob anahtarlarıyla şifrelenir ve Microsoft Azure Blob depolama hizmetinde depolanır.
  
Microsoft 365, müşteriler hizmeti kullanırken müşteri dosyalarının şifresini çözmek ve sağlamak için bu işlemi izler:

1. Müşteri Anahtarını kullanarak TIK'ın şifresini çöz.

2. Bir site anahtarının şifresini çözmek için şifresi çözülmüş TIK'yi kullanın.

3. Blob anahtarının şifresini çözmek için şifresi çözülmüş site anahtarını kullanın.

4. Blob'un şifresini çözmek için şifresi çözülmüş blob anahtarını kullanın.

Microsoft 365, Azure Key Vault'a küçük bir uzaklık ile iki şifre çözme isteği vererek bir TIK'ın şifresini çözer. Bitiren ilk kişi sonucu sağlayarak diğer isteği iptal eder.
  
Müşteri anahtarlarınıza erişiminizi kaybetmeniz durumunda Microsoft 365 ayrıca TIK'ı bir kullanılabilirlik anahtarıyla şifreler ve bunu her müşteri anahtarıyla şifrelenen TIK'larla birlikte depolar. Kullanılabilirlik anahtarıyla şifrelenen TIK, yalnızca müşteri, kötü amaçlı veya yanlışlıkla anahtarlarına erişimi kaybettiğinde kurtarma yolunu listelemek için Microsoft'u aradığında kullanılır.
  
Kullanılabilirlik ve ölçeklendirme nedenleriyle, şifresi çözülmüş SDK'lar sınırlı bir bellek önbelleğinde önbelleğe alınır. Bir TIK önbelleğinin süresi dolmadan iki saat önce, Microsoft 365 her TIK'ın şifresini çözmeyi dener. TIK'lerin şifresinin çözülmesi önbelleğin kullanım ömrünü uzatır. TIK şifre çözme işlemi önemli bir süre için başarısız olursa Microsoft 365 önbelleğin sona erme tarihinden önce mühendislere bildirimde bulunacağı bir uyarı oluşturur. Yalnızca müşterinin Microsoft'u çağırması Microsoft 365 kurtarma işlemini başlatır. Bu işlem, Microsoft'un gizli dizi deposunda depolanan kullanılabilirlik anahtarıyla TIK'ın şifresini çözmeyi ve şifresi çözülen TIK'yi ve müşteri tarafından sağlanan yeni bir Azure Key Vault anahtarı kümesini kullanarak kiracıyı yeniden eklemeyi içerir.
  
Bugün itibarıyla Müşteri Anahtarı, Azure blob deposunda depolanan SharePoint Online dosya verilerinin şifreleme ve şifre çözme zincirinde yer alır ancak SQL Veritabanı depolanan Çevrimiçi liste öğelerini veya meta verileri SharePoint. Microsoft 365 Exchange Online, Skype Kurumsal, SharePoint Online, OneDrive İş ve müşteri tarafından başlatılan yukarıda açıklanan servis talebi dışındaki Teams dosyaları için kullanılabilirlik anahtarını kullanmaz. Müşteri verilerine insan erişimi Müşteri Kasası tarafından korunur.

## <a name="availability-key-triggers"></a>Kullanılabilirlik anahtarı tetikleyicileri

Microsoft 365 yalnızca belirli durumlarda kullanılabilirlik anahtarını tetikler. Bu koşullar hizmete göre farklılık gösterir.

### <a name="triggers-for-exchange-online-and-skype-for-business"></a>Exchange Online ve Skype Kurumsal için tetikleyiciler
  
1. Microsoft 365, Azure Key Vault'da iki Müşteri Anahtarının konumunu belirlemek için posta kutusunun atandığı DEP'yi okur.

2. Microsoft 365, DEP'ten iki Müşteri Anahtarından birini rastgele seçer ve Müşteri Anahtarı'nı kullanarak DEP anahtarının teslimini kaldırmak için Azure Key Vault'a bir istek gönderir.

3. Müşteri Anahtarı'nı kullanarak DEP anahtarını açma isteği başarısız olursa Microsoft 365 Azure Key Vault'a ikinci bir istek gönderir ve bu kez alternatif (ikinci) Müşteri Anahtarını kullanma talimatını verirseniz.

4. Müşteri Anahtarı'nı kullanarak DEP anahtarını kaldırmaya yönelik ikinci istek başarısız olursa Microsoft 365 her iki isteğin sonuçlarını inceler.

    - İnceleme, isteklerin bir sistem HATASI döndüremediğini belirlerse:

       - Microsoft 365, DEP anahtarının şifresini çözmek için kullanılabilirlik anahtarını tetikler.

       - Microsoft 365 posta kutusu anahtarının şifresini çözmek ve kullanıcı isteğini tamamlamak için DEP anahtarını kullanır. 

       - Bu durumda Azure Key Vault geçici bir HATA nedeniyle yanıt veremiyor veya ulaşılamıyor.

    - İnceleme isteklerin ACCESS DENIED döndüremediğini belirlerse:

       - Bu, müşteri anahtarlarını kullanılamaz duruma getirmek için kasıtlı, yanlışlıkla veya kötü amaçlı bir eylem gerçekleştirilen anlamına gelir (örneğin, hizmetten ayrılmanın bir parçası olarak veri temizleme işlemi sırasında).

       - Bu durumda, kullanılabilirlik anahtarı kullanıcı eylemleri için değil yalnızca sistem eylemleri için kullanılır, kullanıcı isteği başarısız olur ve kullanıcı bir hata iletisi alır.

> [!IMPORTANT]
> Microsoft 365 hizmet kodunda her zaman değer katan bulut hizmetleri sağlamak için müşteri verileri üzerinde mantık yürütmeye yönelik geçerli bir oturum açma belirteci bulunur. Bu nedenle, kullanılabilirlik anahtarı silinene kadar arama dizini oluşturma veya posta kutularını taşıma gibi Exchange Online ve Skype Kurumsal tarafından veya şirket içinde başlatılan eylemler için geri dönüş olarak kullanılabilir. Bu hem geçici HATALAR hem de Azure Key Vault ERIŞIM REDDEDildi istekleri için geçerlidir.

### <a name="triggers-for-sharepoint-online-onedrive-for-business-and-teams-files"></a>SharePoint Online, OneDrive İş ve Teams dosyaları için tetikleyiciler

SharePoint Online, OneDrive İş ve Teams dosyaları için, kullanılabilirlik anahtarı hiçbir zaman kurtarma özelliği dışında kullanılmaz ve müşteriler microsoft'a bir kurtarma senaryosu sırasında kullanılabilirlik anahtarının kullanımını başlatmasını açıkça bildirmelidir.

## <a name="audit-logs-and-the-availability-key"></a>Denetim günlükleri ve kullanılabilirlik anahtarı

Microsoft 365'deki otomatik sistemler, virüsten koruma, e-bulma, veri kaybı önleme ve veri dizini oluşturma gibi bulut hizmetleri sağlamak için sistem üzerinden akan tüm verileri işler. Microsoft 365 bu etkinlik için müşteri tarafından görünen günlükler oluşturmaz. Ayrıca, Microsoft personeli bu normal sistem işlemlerinin bir parçası olarak verilerinize erişmez.

### <a name="exchange-online-and-skype-for-business-availability-key-logging"></a>kullanılabilirlik anahtarı günlüğünü Exchange Online ve Skype Kurumsal

Exchange Online ve Skype Kurumsal hizmet sağlamak için kullanılabilirlik anahtarına eriştiğinde, Microsoft 365 Güvenlik ve Uyumluluk Merkezi'nden erişilebilen müşteri görünür günlükleri yayımlar. Hizmet kullanılabilirlik anahtarını her kullandığında kullanılabilirlik anahtarı işlemi için bir denetim günlüğü kaydı oluşturulur. Etkinlik türü "Kullanılabilirlik Anahtarına Geri Dönüş" olan "Müşteri Anahtar Hizmeti Şifrelemesi" adlı yeni kayıt türü, yöneticilerin kullanılabilirlik anahtarı kayıtlarını görüntülemek için [Birleşik Denetim Günlüğü](./search-the-audit-log-in-security-and-compliance.md) arama sonuçlarını filtrelemesine olanak tanır.

Günlük kayıtları tarih, saat, etkinlik, kuruluş kimliği ve veri şifreleme ilkesi kimliği gibi öznitelikleri içerir. Kayıt Birleşik Denetim Günlükleri'nin bir parçası olarak kullanılabilir ve Güvenlik & Uyumluluk Merkezi Denetim Günlüğü Arama sekmesinden erişilebilir.

![Kullanılabilirlik anahtarı olayları için denetim günlüğü araması](../media/customerkeyauditlogsearchavailabilitykeyloggingimage.png)

Exchange Online ve Skype Kurumsal kullanılabilirlik anahtarı kayıtları, eklenen özel parametrelerle Office 365 Yönetim Etkinliği [ortak şemasını](/office/office-365-management-api/office-365-management-activity-api-schema#common-schema) kullanır: İlke Kimliği, Kapsam Anahtarı Sürüm Kimliği ve İstek Kimliği.

![Kullanılabilirlik anahtarı özel parametreleri](../media/customerkeyauditlogsearchavailabilitykeyloggingcustomparam.png)

### <a name="sharepoint-online-onedrive-for-business-and-teams-files-availability-key-logging"></a>SharePoint Çevrimiçi, OneDrive İş ve Teams dosyaları kullanılabilirlik anahtarı günlüğü

Kullanılabilirlik anahtarı günlüğü henüz bu hizmetler için kullanılamıyor. SharePoint Online, OneDrive İş ve Teams dosyaları için, kullanılabilirlik anahtarı yalnızca microsoft tarafından, sizin tarafınızdan talimat verildiğinde kurtarma amacıyla etkinleştirilir. Sonuç olarak, bu hizmetler için kullanılabilirlik anahtarının kullanıldığı her olayı zaten biliyorsunuz.

## <a name="availability-key-in-the-customer-key-hierarchy"></a>Müşteri Anahtarı hiyerarşisindeki kullanılabilirlik anahtarı
  
Microsoft 365 kullanılabilirlik anahtarını kullanarak Müşteri Anahtarı hizmeti şifrelemesi için oluşturulan anahtar hiyerarşisindeki alt anahtar katmanını sarmalar. Hizmetler arasında farklı anahtar hiyerarşileri vardır. Anahtar algoritmaları, kullanılabilirlik anahtarları ile ilgili her hizmetin hiyerarşisindeki diğer anahtarlar arasında da farklılık gösterir. Farklı hizmetler tarafından kullanılan kullanılabilirlik anahtarı algoritmaları aşağıdaki gibidir:

- Exchange Online ve Skype Kurumsal kullanılabilirlik anahtarları AES-256 kullanır.

- SharePoint Online, OneDrive İş ve Teams dosyaları kullanılabilirlik anahtarları RSA-2048 kullanır.

### <a name="encryption-ciphers-used-to-encrypt-keys-for-exchange-online-and-skype-for-business"></a>Exchange Online ve Skype Kurumsal anahtarlarını şifrelemek için kullanılan şifreleme şifreleri

![Exchange Online Müşteri Anahtarı için şifreleme şifreleri](../media/customerkeyencryptionhierarchiesexchangeskype.png)

### <a name="encryption-ciphers-used-to-encrypt-keys-for-sharepoint-online-and-onedrive-for-business"></a>SharePoint Online ve OneDrive İş için anahtarları şifrelemek için kullanılan şifreleme şifreleri

![SharePoint Çevrimiçi Müşteri Anahtarı için şifreleme şifreleri](../media/customerkeyencryptionhierarchiessharepointonedriveteamsfiles.png)

## <a name="related-articles"></a>İlgili makaleler

- [Müşteri Anahtarı ile hizmet şifrelemesi](customer-key-overview.md)

- [Müşteri Anahtarını Ayarlama](customer-key-set-up.md)

- [Müşteri Anahtarını Yönet](customer-key-manage.md)

- [Bir Müşteri Anahtarını veya uygunluk anahtarını toplama veya döndürme](customer-key-availability-key-roll.md)
