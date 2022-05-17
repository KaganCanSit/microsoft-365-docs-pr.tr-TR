---
title: Ağ cihazı bulma ve güvenlik açığı yönetimi
description: Güvenlik önerileri ve güvenlik açığı algılama artık anahtar, yönlendirici, WLAN denetleyicisi ve güvenlik duvarı işletim sistemleri için kullanılabilir.
keywords: ağ cihazları, ağ cihazları güvenlik açığı algılama, anahtar işletim sistemleri, yönlendiriciler, WLAN denetleyicileri ve güvenlik duvarları
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: levinec
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: f5c2f1c7c73f150c02192fa7e275a07b12c64c79
ms.sourcegitcommit: 9255a7e8b398f92d8dae09886ae95dc8577bf29a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/17/2022
ms.locfileid: "65438388"
---
# <a name="network-device-discovery-and-vulnerability-management"></a>Ağ cihazı bulma ve güvenlik açığı yönetimi

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**Şunlar için geçerlidir:**
- [Uç Nokta için Microsoft Defender Planı 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Tehdit ve güvenlik açığı yönetimi](next-gen-threat-and-vuln-mgt.md)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Uç Nokta için Microsoft Defender mı yaşamak istiyorsunuz? [Ücretsiz deneme için kaydolun.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-portaloverview-abovefoldlink)

> [!NOTE]
> [Ağ cihazı bulma ve güvenlik açığı değerlendirmeleri](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/network-device-discovery-and-vulnerability-assessments/ba-p/2267548) 04-13-2021'de\) yayımlanan Blog\(, Uç Nokta için Defender'daki yeni **Ağ cihazı bulma** özellikleri hakkında içgörüler sağlar. Bu makalede **Ağ cihazı bulma** işleminin ele almak için tasarlandığı sınamaya genel bir bakış ve bu yeni özellikleri kullanmaya başlama hakkında ayrıntılı bilgiler sağlanmaktadır.

Ağ bulma özellikleri, <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portalın</a> **cihaz envanteri** bölümünde ve Microsoft 365 Defender konsollarında kullanılabilir.

Önceden yapılandırılmış ağ cihazlarında düzenli aralıklarla kimliği doğrulanmış taramalar gerçekleştirmek için her ağ kesiminde belirlenmiş bir Uç Nokta için Microsoft Defender cihazı kullanılır. Uç Nokta için Defender'ın Tehdit ve Güvenlik Açığı Yönetimi özellikleri, bulunan anahtarları, yönlendiricileri, WLAN denetleyicilerini, güvenlik duvarlarını ve VPN ağ geçitlerini güvenli hale getirmek için tümleşik iş akışları sağlar.

Ağ cihazları keşfedilip sınıflandırıldıktan sonra, güvenlik yöneticileri en son güvenlik önerilerini alabilir ve kuruluşlarına dağıtılan ağ cihazlarında yakın zamanda bulunan güvenlik açıklarını gözden geçirebilir.

## <a name="approach"></a>Yaklaşım

Uç Nokta için Defender'ın ağ cihazlarında yerleşik bir algılayıcısı olmadığından, ağ cihazları standart uç nokta olarak yönetilmez. Bu tür cihazlar, uzaktan taramanın cihazlardan gerekli bilgileri edineceği aracısız bir yaklaşım gerektirir. Ağ topolojisine ve özelliklerine bağlı olarak, tek bir cihaz veya Uç Nokta için Microsoft Defender eklenen birkaç cihaz SNMP (salt okunur) kullanarak ağ cihazlarında kimliği doğrulanmış taramalar gerçekleştirir.

Göz önünde bulundurulması gereken iki tür cihaz olacaktır:

- **Değerlendirme cihazı**: Ağ cihazlarını taramak için kullanacağınız zaten ekli bir cihaz.
- **Ağ cihazları**: Taramayı ve eklemeyi planladığınız ağ cihazları.

### <a name="vulnerability-management-for-network-devices"></a>Ağ cihazları için güvenlik açığı yönetimi

Ağ cihazları keşfedilip sınıflandırıldıktan sonra, güvenlik yöneticileri en son güvenlik önerilerini alabilir ve kuruluşlarına dağıtılan ağ cihazlarında yakın zamanda bulunan güvenlik açıklarını gözden geçirebilir.

## <a name="operating-systems-that-are-supported"></a>Desteklenen işletim sistemleri

Şu anda aşağıdaki işletim sistemleri desteklenmektedir:

- Cisco IOS, IOS-XE, NX-OS
- Ardıç JUNOS
- HPE ArubaOS, Procurve Switch Yazılımı
- Palo Alto Networks PAN-OS

Müşteri kullanımından toplanan verilere bağlı olarak zaman içinde daha fazla ağ satıcısı ve işletim sistemi eklenecektir. Bu nedenle, bu listede belirtilmemiş olsalar bile tüm ağ cihazlarınızı yapılandırmanız teşvik edilir.

## <a name="how-to-get-started"></a>Nasıl başlarsınız?

İlk adımınız, kimliği doğrulanmış ağ taramalarını gerçekleştirecek bir cihaz seçmektir.

1. Taramayı planladığınız ağ cihazları için yönetim bağlantı noktasına ağ bağlantısı olan uç nokta için Defender ekli cihazına (istemci veya sunucu) karar verin.

2. Uç Nokta için Defender değerlendirme cihazı ile hedeflenen ağ cihazları arasındaki SNMP trafiğine izin verilmelidir (örneğin, Güvenlik Duvarı tarafından).

3. Hangi ağ cihazlarının güvenlik açıkları açısından değerlendirileceğine karar verin (örneğin: Cisco anahtarı veya Palo Alto Networks güvenlik duvarı).

4. Uç Nokta için Defender değerlendirme cihazının yapılandırılan ağ cihazlarını sorgulamasına izin vermek için SNMP'nin tüm yapılandırılmış ağ cihazlarında salt okunur özelliğinin etkinleştirildiğinden emin olun. Bu özelliğin düzgün işlevselliği için 'SNMP yazma' gerekli değildir.

5. Taranacak ağ cihazlarının (veya bu cihazların dağıtıldığı alt ağların) IP adreslerini alın.

6. Ağ cihazlarının SNMP kimlik bilgilerini alın (örneğin: Community Dizesi, noAuthNoPriv, authNoPriv, authPriv). Yeni bir değerlendirme işi yapılandırırken kimlik bilgilerini sağlamanız gerekir.

7. Ara sunucu istemci yapılandırması: Uç nokta için Defender cihaz proxy gereksinimleri dışında ek yapılandırma gerekmez.

8. Ağ tarayıcısının kimliğinin doğrulanması ve düzgün çalışması için aşağıdaki etki alanlarını/URL'leri eklemeniz önemlidir:

    - login.windows.net
    - \*.security.microsoft.com
    - login.microsoftonline.com
    - \*.blob.core.windows.net/networkscannerstable/\*

    > [!NOTE]
    > Uç Nokta için Defender belgelenmiş izin verilen veri toplama listesinde tüm URL'ler belirtilmez.

## <a name="permissions"></a>İzinler

Değerlendirme işlerini yapılandırmak için aşağıdaki kullanıcı izni seçeneği gereklidir: **Defender'da güvenlik ayarlarını yönetme**. **Ayarlar Roller'e** \> giderek izni bulabilirsiniz. Daha fazla bilgi için bkz. [Rol tabanlı erişim denetimi için roller oluşturma ve yönetme](user-roles.md).

## <a name="install-the-network-scanner"></a>Ağ tarayıcısını yükleme

1. **Microsoft 365 güvenlik** \> **Ayarlar** \> **Uç Nokta** \> **Değerlendirme işleri'ne** gidin (**Ağ değerlendirmeleri** altında).
    1. Microsoft 365 Defender portalında Ayarlar > Değerlendirme işleri sayfasına gidin.

2. Ağ tarayıcısını indirin ve belirlenen Uç Nokta için Defender değerlendirme cihazına yükleyin.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/assessment-jobs-download-scanner.png" alt-text="Tarayıcıyı indir düğmesi" lightbox="images/assessment-jobs-download-scanner.png":::

## <a name="network-scanner-installation--registration"></a>Ağ tarayıcısı yükleme & kaydı

Oturum açma işlemi, belirlenen değerlendirme cihazının kendisinde veya başka bir cihazda (örneğin, kişisel istemci cihazınız) tamamlanabilir.

> [!NOTE]
> Hem kullanıcının oturum açtığı hesap hem de oturum açma işlemini tamamlamak için kullanılan cihaz, cihazın Uç Nokta için Microsoft Defender eklendiği kiracıda olmalıdır.

Ağ tarayıcısı kayıt işlemini tamamlamak için:

1. Komut satırında görüntülenen URL'yi kopyalayıp izleyin ve kayıt işlemini tamamlamak için sağlanan yükleme kodunu kullanın.

    > [!NOTE]
    > URL'yi kopyalayabilmek için Komut İstemi ayarlarını değiştirmeniz gerekebilir.

2. Kodu girin ve "Defender'da güvenlik ayarlarını yönetme" adlı Uç Nokta için Defender iznine sahip bir Microsoft hesabı kullanarak oturum açın.

3. İşiniz bittiğinde oturum açtığınızı onaylayan bir ileti görmeniz gerekir.

## <a name="configure-a-new-assessment-job"></a>Yeni değerlendirme işini yapılandırma

**Ayarlar'daki** Değerlendirme işleri sayfasında **Ağ değerlendirme işi ekle'yi** seçin. Düzenli olarak taranacak ve cihaz envanterine eklenecek ağ cihazlarını seçmek için kurulum işlemini izleyin.

Ağ cihazı envanterinde cihaz yinelemesini önlemek için, her IP adresinin birden çok değerlendirme cihazında yalnızca bir kez yapılandırıldığından emin olun.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/assessment-jobs-add.png" alt-text="Ağ değerlendirmesi işi ekle düğmesi" lightbox="images/assessment-jobs-add.png":::

Ağ değerlendirme işi adımları ekleme:

1. Ağ tarayıcısının yüklendiği 'Değerlendirme işi' adını ve 'Değerlendirme cihazı'nı seçin. Bu cihaz düzenli aralıklarla kimliği doğrulanmış taramaları gerçekleştirir.

2. Taranacak hedef ağ cihazlarının IP adreslerini (veya bu cihazların dağıtıldığı alt ağları) ekleyin.

3. Hedef ağ cihazlarının gerekli SNMP kimlik bilgilerini ekleyin.

4. Düzenli ağ taramasını başlatmak için yeni yapılandırılan ağ değerlendirme işini kaydedin.

### <a name="scan-and-add-network-devices"></a>Ağ cihazlarını tarama ve ekleme

Kurulum işlemi sırasında, aşağıdakileri doğrulamak için bir kerelik test taraması gerçekleştirebilirsiniz:

- Uç Nokta için Defender değerlendirme cihazı ile yapılandırılan hedef ağ cihazları arasında bağlantı vardır.
- Yapılandırılan SNMP kimlik bilgileri doğru.

Her değerlendirme cihazı 1.500'e kadar başarılı IP adresi taramasını destekleyebilir. Örneğin, yalnızca 100 IP adresinin başarılı sonuçlar döndürdüğü 10 farklı alt ağı tararsanız, aynı değerlendirme cihazındaki diğer alt ağlardan 1.400 IP ek adresini tarayabilirsiniz.

Taranacak birden çok IP adresi aralığı/alt ağ varsa test tarama sonuçlarının gösterilmesi birkaç dakika sürer. En fazla 1.024 adres için test taraması kullanılabilir.

Sonuçlar gösterildikten sonra, periyodik taramaya hangi cihazların dahil olacağını seçebilirsiniz. Tarama sonuçlarını görüntülemeyi atlarsanız, yapılandırılan tüm IP adresleri ağ değerlendirme işine eklenir (cihazın yanıtı ne olursa olsun). Tarama sonuçları da dışarı aktarılabilir.

## <a name="device-inventory"></a>Cihaz envanteri

Yeni bulunan cihazlar **, Cihaz envanteri** sayfasındaki yeni **Ağ cihazları** sekmesinin altında gösterilir. Cihazlar güncelleştirilene kadar değerlendirme işi eklendikten sonra iki saat kadar sürebilir.

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/assessment-jobs-device-inventory.png" alt-text="Cihaz envanterindeki Ağ cihazları bölümü" lightbox="images/assessment-jobs-device-inventory.png":::

## <a name="troubleshooting"></a>Sorun giderme

### <a name="network-scanner-installation-has-failed"></a>Ağ tarayıcısı yüklemesi başarısız oldu

Güvenlik duvarı ayarlarınızdaki izin verilen etki alanlarına gerekli URL'lerin eklendiğini doğrulayın. Ayrıca, proxy ayarlarının [Cihaz ara sunucusu ve İnternet bağlantısı ayarlarını yapılandırma](configure-proxy-internet.md) başlığı altında açıklandığı gibi yapılandırıldığından emin olun.

### <a name="the-microsoftcomdevicelogin-web-page-did-not-show-up"></a>Microsoft.com/devicelogin web sayfası gösterilmedi

Gerekli URL'lerin güvenlik duvarınızdaki izin verilen etki alanlarına eklendiğini doğrulayın. Ayrıca, proxy ayarlarının [Cihaz ara sunucusu ve İnternet bağlantısı ayarlarını yapılandırma](configure-proxy-internet.md) başlığı altında açıklandığı gibi yapılandırıldığından emin olun.

### <a name="network-devices-are-not-shown-in-the-device-inventory-after-several-hours"></a>Ağ cihazları birkaç saat sonra cihaz envanterinde gösterilmez

Tarama sonuçları, değerlendirme işi yapılandırması tamamlandıktan sonra gerçekleşen ilk taramadan birkaç saat sonra güncelleştirilmelidir.

Cihazlar hala gösterilmiyorsa, ağ tarayıcısını yüklediğiniz değerlendirme cihazlarınızda 'MdatpNetworkScanService' hizmetinin çalıştığını doğrulayın ve ilgili değerlendirme işi yapılandırmasında bir "Tarama çalıştır" gerçekleştirin.

5 dakika sonra hala sonuç alamazsanız hizmeti yeniden başlatın.

### <a name="devices-last-seen-time-is-longer-than-24-hours"></a>Cihazların son görülme süresi 24 saatten uzun

Tarayıcının düzgün çalıştığını doğrulayın. Ardından tarama tanımına gidin ve "Testi çalıştır"ı seçin. İlgili IP adreslerinden hangi hata iletilerinin döndüğünü denetleyin.

### <a name="required-threat-and-vulnerability-management-user-permission"></a>Kullanıcı izni Tehdit ve Güvenlik Açığı Yönetimi gerekli

Kayıt şu hatayla tamamlandı: "Yeni aracı eklemek için yeterli izniniz yok gibi görünüyor. Gerekli izin 'Defender'da güvenlik ayarlarını yönet'tir."

Çıkmak için herhangi bir tuşa basın.

Sistem yöneticinizden size gerekli izinleri atamasını isteyin. Alternatif olarak, başka bir ilgili üyeden oturum açma kodunu ve bağlantısını sağlayarak oturum açma işleminde size yardımcı olmasını isteyin.

### <a name="registration-process-fails-using-provided-link-in-the-command-line-in-registration-process"></a>Kayıt işlemi, kayıt işlemindeki komut satırında sağlanan bağlantı kullanılarak başarısız oluyor

Farklı bir tarayıcı deneyin veya oturum açma bağlantısını ve kodu farklı bir cihaza kopyalayın.

### <a name="text-too-small-or-cant-copy-text-from-command-line"></a>Metin çok küçük veya komut satırından metin kopyalanamıyor

Kopyalamaya izin vermek ve metin boyutunu değiştirmek için cihazınızdaki komut satırı ayarlarını değiştirin.

## <a name="related-articles"></a>İlgili makaleler

- [Cihaz envanteri](machines-view-overview.md)
- [Gelişmiş özellikleri yapılandırın](advanced-features.md)
