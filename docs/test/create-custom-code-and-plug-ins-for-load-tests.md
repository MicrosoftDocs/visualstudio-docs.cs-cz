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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590095"
---
# <a name="create-custom-code-and-plug-ins-for-load-tests"></a>Vytvoření vlastního kódu a modulů plugin pro zátěžové testování

Vlastní modul plug-in používá kód, který lze vytvořit a připojit k zátěžovému testu nebo testu výkonnosti webu. Rozhraní API zátěžového testu a API výkonnostních testů webu můžete použít k vytvoření vlastních modulů plug-in pro rozšíření integrovaných funkcí. Můžete přidat více modulů plug-in do zátěžového testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Tasks

|Tasks|Související témata|
|-|-----------------------|
|**Vytvořit vlastní modul plug-in pro zátěžový test**: můžete vytvořit vlastní modul plug-in pro přidání další funkce testování k zátěžovému testu můžete použít rozhraní API zátěžového testu.|-   [Postupy: použití rozhraní API zátěžového testu](../test/how-to-use-the-load-test-api.md)<br />-   [Postupy: vytvoření modulu Plugin pro zátěžový test](../test/how-to-create-a-load-test-plug-in.md)|
|**Vytvořit vlastní modul plug-in pro test výkonnosti webu:** API výkonnostních testů webu můžete vytvořit vlastní modul plug-in pro přidání do testu výkonnosti webu, včetně webu další funkce testování. Můžete také vytvořit testu webové služby.<br /><br /> Kromě toho můžete vytvořit webového modulu plug-in rekordéru, který můžete upravit test výkonnosti webu poté, co je zaznamenán, ale předtím, než se zobrazí v prohlížeči výsledků testů webového výkonu.|-   [Postupy: použití API testu výkonnosti webu](../test/how-to-use-the-web-performance-test-api.md)<br />-   [Postupy: vytvoření modulu Plugin pro test výkonnosti webu](../test/how-to-create-a-web-performance-test-plug-in.md)<br />-   [Postupy: vytvoření modulu Plugin úrovni požadavků](../test/how-to-create-a-request-level-plug-in.md)<br />-   [Postupy: vytvoření testu webové služby](../test/how-to-create-a-web-service-test.md)<br />-   [Postupy: vytvoření modulu Plugin rekordéru](../test/how-to-create-a-recorder-plug-in.md)|
|**Přidání funkcí uživatelského rozhraní do prohlížeče výsledků testu výkonu webu:** přidáte další funkce uživatelského rozhraní do doplňku sady Visual Studio pomocí prohlížeče výsledků testu webového výkonu.|-   [Postupy: Vytvoření doplňku sady Visual Studio pro web výsledků testu výkonnosti prohlížeč](../test/how-to-create-an-add-in-for-the-web-performance-test-results-viewer.md)|
|**Vytvoření vlastní těla protokolu HTTP editoru:** můžete vytvořit vlastní editor pro úpravu binárních nebo řetězcových odpovědí ve formátu XML z webové služby.|-   [Postupy: vytvoření vlastní těla protokolu HTTP editoru editoru testu výkonnosti webu](../test/how-to-create-a-custom-http-body-editor-for-the-web-performance-test-editor.md)|

## <a name="reference"></a>Odkaz

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting.ILoadTestPlugin>

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>

<xref:Microsoft.VisualStudio.TestTools.LoadTesting>

## <a name="see-also"></a>Viz také:

- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Generování a spuštění programový test výkonnosti webu](../test/generate-and-run-a-coded-web-performance-test.md)
