---
title: Vytvoření vlastního kódu a modulů plugin pro zátěžové testování
ms.date: 10/19/2016
ms.topic: conceptual
f1_keywords:
- vs.test.dialog.recorderplugin
helpviewer_keywords:
- Web performance tests, plug-ins
- load tests, plug-ins
ms.assetid: 0c0fcc99-673b-4ea0-a268-0475f66e5cb6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3519a593182c199cc9f7a92cfb77e9c79bd1a9ee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590095"
---
# <a name="create-custom-code-and-plug-ins-for-load-tests"></a>Vytvoření vlastního kódu a modulů plugin pro zátěžové testování

Vlastní modul plug-in používá kód, který napíšete a připojíte k zátěžovému testu nebo testu výkonu webu. Rozhraní API zátěžového testu a rozhraní API pro testování výkonu webu můžete použít k vytvoření vlastních modulů plug-in pro testy, které se rozšíří na vestavěné funkce. Do zátěžového testu můžete přidat více modulů plug-in.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Úlohy

|Úlohy|Přidružená témata|
|-|-----------------------|
|**Vytvořte vlastní modul plug-in pro zátěžový test**: Pomocí rozhraní API zátěžového testu můžete vytvořit vlastní modul plug-in a přidat do zátěžového testu další funkce testování.|-   [Postup: Použití rozhraní API zátěžového testu](../test/how-to-use-the-load-test-api.md)<br />-   [Postup: Vytvoření modulu plug-in zátěžového testu](../test/how-to-create-a-load-test-plug-in.md)|
|**Vytvořte vlastní modul plug-in pro test výkonu webu:** Pomocí rozhraní API pro testování výkonu webu můžete vytvořit vlastní modul plug-in a přidat další funkce testování do testu výkonu webu, a to i na úrovni požadavku. Můžete také vytvořit test webové služby.<br /><br /> Kromě toho můžete vytvořit modul plug-in webového rekordéru, který může po zaznamenání upravit test výkonu webu, ale předtím, než se zobrazí v prohlížeči výsledků testu výkonnosti webu.|-   [Postup: Použití rozhraní API pro testování výkonu webu](../test/how-to-use-the-web-performance-test-api.md)<br />-   [Postup: Vytvoření modulu plug-in test výkonu webu](../test/how-to-create-a-web-performance-test-plug-in.md)<br />-   [Postup: Vytvoření modulu plug-in na úrovni požadavku](../test/how-to-create-a-request-level-plug-in.md)<br />-   [Postup: Vytvoření testu webové služby](../test/how-to-create-a-web-service-test.md)<br />-   [Postup: Vytvoření modulu plug-in rekordéru](../test/how-to-create-a-recorder-plug-in.md)|
|**Přidání funkcí uživatelského uživatelského prostředí do prohlížeče výsledků testů výkonu webu:** Pomocí doplňku Visual Studio můžete do prohlížeče výsledků testů výkonu webu přidat další funkce uživatelského prostředí.|-   [Postup: Vytvoření doplňku sady Visual Studio pro prohlížeč výsledků testů výkonu webu](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)|
|**Vytvořte vlastní editor těla HTTP:** Můžete vytvořit vlastní editor pro úpravu binárních nebo řetězcových odpovědí XML http z webové služby.|-   [Postup: Vytvoření vlastního editoru těla HTTP pro editor testů výkonu webu](../test/how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor.md)|

## <a name="reference"></a>Referenční informace

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting>

## <a name="see-also"></a>Viz také

- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Generování a spuštění programového testu výkonnosti webu](../test/generate-and-run-a-coded-web-performance-test.md)
