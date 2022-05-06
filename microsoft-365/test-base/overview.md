---
title: Genel Bakış
description: Test Base’i Anlama
search.appverid: MET150
author: Tinacyt
ms.author: tinachen
manager: rshastri
audience: Software-Vendor
ms.topic: how-to
ms.date: 07/06/2021
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: mapatel
f1.keywords: NOCSH
ms.openlocfilehash: 13eaea1e62dd030f86e08d885ad743d673d6142c
ms.sourcegitcommit: b16520d8bfe04b29274f7a129d90ef116bb77f69
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2022
ms.locfileid: "65231703"
---
# <a name="what-is-test-base-for-microsoft-365"></a>Microsoft 365 için Test Base nedir?

Test Base, dünyanın her yerinden akıllı testlere kullanıcı erişimi sağlarken veri odaklı uygulama testine olanak tanıyan bir Azure hizmetidir.

Aşağıdaki varlıkların uygulamalarını, ikili dosyalarını ve test betiklerini Microsoft 365 için Test Base hizmetine eklemeleri önerilir: Uygulamalarını doğrulamak için Bağımsız Yazılım Satıcıları (ISV'ler), Sistem Tümleştiricileri (SI'ler) ve Microsoft Intune ile tümleştirme yoluyla iş kolu (LOB) uygulamalarını doğrulamak isteyen BT Uzmanları.

## <a name="why-test-your-application-with-test-base"></a>Uygulamanızı neden Test Base ile test etmelisiniz?

Microsoft 365 için Test Base hizmeti, uygulamalarınızın bütünlüğüne, uyumluluğuna ve kullanılabilirliğine güvenmeniz için test matrisinizin gerektiği şekilde genişletilmesini sağlayabilir.

Test Base, platform bağımlılıkları değişse ve Windows güncelleştirme hizmeti tarafından yeni güncelleştirmeler uygulansa bile uygulamanızın beklendiği gibi çalışmaya devam etmesini sağlar. Test Base ile uygulamalarınızı test etmek için karmaşık bir laboratuvar ortamı kurma ve sürdürme maliyetini, uzun süre taahhütlerini ve harcamalarını önleyebilirsiniz.

Ayrıca, güvenli sanal makineler (VM'ler) kullanarak Windows için güvenlik ve özellik güncelleştirmelerine karşı uyumluluğu otomatik olarak test edebilir ve aynı zamanda uygulamalarınızı test etmek için birinci sınıf zekaya erişim elde edebilirsiniz. Erişim almak için bir istek göndererek uygulamalarınızın yayın öncesi Windows güvenlik güncelleştirmelerine karşı uyumluluk açısından test edilmesini de sağlayabilirsiniz.

## <a name="how-does-test-base-work"></a>Test Base nasıl çalışır?

Test Base hizmetine kaydolmak için bkz. [Yeni bir Test Tabanı hesabı oluşturma](createAccount.md).

Bir müşteri Test Base hizmetine kaydolduktan sonra, test için uygulama paketlerini karşıya yüklemeye başlamak basit bir işlemdir.

Başarılı bir karşıya yüklemenin ardından paketler, Windows yayın öncesi güncelleştirmelerine karşı test edilir.

İlk testler başarıyla tamamlandıktan sonra müşteri, yayın öncesi içerik güncelleştirmelerinin uygulama performansını herhangi bir şekilde düşürüp düşürmediğini tespit etmek için performans ve regresyon analizine yönelik içgörülerle derin bir dalış yapabilir.

Ancak, paket herhangi bir testte başarısız olursa, müşteri, hatayı gidermek ve paketi gerektiği gibi güncelleştirmek için bellek veya CPU regresyonlarından İçgörüler’den de yararlanabilir.

Test Base ile müşteri, test edilmekte olan tüm paketleri yönetmek için tek bir konum kullanabilir; bu, gerektiğinde yeni uygulama sürümleri oluşturmak için paketlerin karşıya yüklenmesini ve güncelleştirilmesini de kolaylaştırabilir.

> [!NOTE]
> **Müşterilerin yayın öncesi güncelleştirme içeriğinden yararlanabilmeleri için, özel olarak bu içeriğe erişim istemeleri gerekir. Yayın öncesi güncelleştirmelere erişim isteğiniz onaylandıktan sonra, karşıya yüklediğiniz paketleriniz, katılım sırasında seçilen işletim sistemi sürümleri için yayın öncesi Windows güncelleştirmelerine karşı test edilmek üzere otomatik olarak programlanır**.

Ardından, yeni Windows yayın öncesi güncelleştirmeleri kullanıma sunulduğunda, uygulama paketleri yeni yayın öncesi içerikle otomatik olarak test edilir. Bundan sonra ek bir içgörü turu gerekebilir. Müşteriler özel olarak erişim isteğinde bulunmazsa, uygulama paketleri yalnızca Windows'un geçerli yayınlanmış sürümüne karşı test edilecek.

Paketler başarıyla test edildikten sonra müşteriler bunları yazılım müşterilerine ve son kullanıcılara Test Base'in işini yaptığına dair güven ve güvence ile teslim edebilir.

## <a name="next-steps"></a>Sonraki adımlar

Başlamak için bağlantıyı izleyin
> [!div class="nextstepaction"]
> [Yeni Test Base hesabı oluşturma | Microsoft Docs](createaccount.md)
