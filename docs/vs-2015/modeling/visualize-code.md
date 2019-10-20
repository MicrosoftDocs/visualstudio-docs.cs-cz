---
title: Vizualizovat kód | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
ms.assetid: 0dd7d438-393a-4cd3-b417-9bf37379e1b0
caps.latest.revision: 49
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 51b546e953cae80b7a1871b72a1f0b0613c77342
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659339"
---
# <a name="visualize-code"></a>Vizualizace kódu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pomocí nástrojů pro vizualizaci a modelování v aplikaci Visual Studio můžete pochopit existující kód a popsat svou aplikaci. To vám umožní vizuálně zjistit, jak změny můžou ovlivnit kód, a pomohou vám posoudit práci a rizika vyplývající z těchto změn. Příklad:

- Chcete-li pochopit vztahy v kódu, namapujte tyto vztahy vizuálně.

- K popisu architektury systému a udržování kódu v souladu s návrhem, vytváření diagramů vrstev a ověřování kódu proti těmto diagramům.

- Chcete-li popsat struktury tříd, vytvořte diagramy tříd.

- Pokud chcete modelovat a komunikovat s různými aspekty systému, nakreslete jazyk UML (Unified Modeling Language) (UML) diagramy. Můžete například modelovat součásti systému, typy, interakce a procesy.

  Tyto nástroje také usnadňují komunikaci s lidmi, které se podílejí na vašem projektu. Diagramy tříd UML můžete například použít k vytvoření společného glosáře pro diskuzi systému se zúčastněnými stranami projektu, uživateli a členy týmu.

  Chcete-li zjistit, které verze aplikace Visual Studio podporují jednotlivé funkce, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

|||
|-|-|
|**Pochopení kódu a jeho vztahů:**<br /><br /> Mapování vztahů mezi určitými částmi kódu.<br /><br /> Podívejte se na přehled vztahů v kódu pro celé řešení.<br /><br /> **Poznámka**: v této verzi sady Visual Studio se jako místo *grafu závislostí*používá pojem *Mapa kódu* .|-   [závislosti map napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md)<br />-   [použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [metody map v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Porozumění strukturám tříd:**<br /><br /> Vizualizujte strukturu tříd v projektu vytvořením diagramů tříd z kódu.|[Postupy: Přidání diagramů tříd do projektů (Návrhář tříd)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|
|**Popište návrh systému vysoké úrovně a ověřte kód pro tento návrh:**<br /><br /> Popište návrh systému vysoké úrovně a jeho zamýšlené závislosti vytvořením diagramů vrstev. Ověřte kód pro tento návrh a ujistěte se, že závislosti v kódu zůstávají v souladu s návrhem.|-   [vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [diagramy vrstev: referenční](../modeling/layer-diagrams-reference.md) dokumentace<br />-   [diagramy vrstev: pokyny](../modeling/layer-diagrams-guidelines.md)<br />-   [ověřování kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)|
|**Komunikace s požadavky a architekturou uživatele:**<br /><br /> Vykreslením následujících diagramů UML můžete modelovat požadavky uživatelů a architekturu softwarového systému: aktivita, komponenta, třída, sekvence a případ použití.|-   [vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)<br />[požadavky uživatelů -    modelu](../modeling/model-user-requirements.md)<br />-   [modelování architektury vaší aplikace](../modeling/model-your-app-s-architecture.md)|

## <a name="external-resources"></a>Externí zdroje

|**Kategorií**|**Odkazy**|
|------------------|---------------|
|**Fóra**|-   [nástrojů pro modelování sady Visual Studio pro vizualizaci &](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Sada Visual Studio vizualizace & Modeling SDK (nástroje DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|
|**Blogy**|[Blog sady Visual Studio ALM + Team Foundation Server](http://go.microsoft.com/fwlink/?LinkID=201340)|
|**Technické články a deníky**|[Fórum architektury MSDN](http://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>Viz také
 [Scénář: Změna návrhu pomocí vizualizace a modelování](../modeling/scenario-change-your-design-using-visualization-and-modeling.md) [analýzy a modelování](../modeling/analyze-and-model-your-architecture.md) [vytváření modelů pro](../modeling/create-models-for-your-app.md) model [požadavků na uživatele](../modeling/model-user-requirements.md) modelu aplikace použití modelů [vaší aplikace](../modeling/model-your-app-s-architecture.md) [ve vaší architektuře proces vývoje](../modeling/use-models-in-your-development-process.md)
