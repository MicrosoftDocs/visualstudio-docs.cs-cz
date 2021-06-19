---
title: Vizualizace kódu
description: Přečtěte si, jak můžete pomocí nástrojů pro vizualizaci a modelování v aplikaci Visual Studio pochopit existující kód a popsat svoji aplikaci.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 90c180bf9d910227013c2e089001ce5332cd1bd3
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388344"
---
# <a name="visualize-code"></a>Vizualizace kódu

Pomocí nástrojů pro vizualizaci a modelování v aplikaci Visual Studio můžete pochopit existující kód a popsat svou aplikaci. To vám umožní vizuálně zjistit, jak změny můžou ovlivnit kód, a pomohou vám posoudit práci a rizika vyplývající z těchto změn. Příklad:

- Chcete-li pochopit vztahy v kódu, namapujte tyto vztahy vizuálně.

- K popisu architektury systému a udržování kódu v souladu s návrhem, vytváření diagramů závislostí a ověřování kódu proti těmto diagramům.

- Chcete-li popsat struktury tříd, vytvořte diagramy tříd.

Tyto nástroje také usnadňují komunikaci s lidmi, které se podílejí na vašem projektu.

Pokud chcete zjistit, které edice sady Visual Studio podporují jednotlivé funkce, přečtěte si téma [Podpora edice pro nástroje pro architekturu a modelování](../modeling/analyze-and-model-your-architecture.md#VersionSupport) .

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

|Scenario|Články|
|-|-|
|**Pochopení kódu a jeho vztahů:**<br /><br /> Mapování vztahů mezi určitými částmi kódu.<br /><br /> Podívejte se na přehled vztahů v kódu pro celé řešení.|- [Mapování závislostí napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md)<br />- [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)<br />- [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />- [Mapování metod v zásobníku volání při ladění](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|
|**Porozumění strukturám tříd:**<br /><br /> Vizualizujte strukturu tříd v projektu vytvořením diagramů tříd z kódu.|[Postupy: Přidání diagramů tříd do projektů (Návrhář tříd)](../ide/class-designer/how-to-add-class-diagrams-to-projects.md)|
|**Popište návrh systému vysoké úrovně a ověřte kód pro tento návrh:**<br /><br /> Popište návrh systému vysoké úrovně a jeho zamýšlené závislosti vytvořením diagramů závislostí. Ověřte kód pro tento návrh a ujistěte se, že závislosti v kódu zůstávají v souladu s návrhem.|- [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />- [Diagramy závislostí: Referenční dokumentace](../modeling/layer-diagrams-reference.md)<br />- [Diagramy závislostí: pokyny](../modeling/layer-diagrams-guidelines.md)<br />- [Ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)|

## <a name="see-also"></a>Viz také

- [Nainstalovat nástroje kódu architektury](install-architecture-tools.md)
- [Scénář: Změna návrhu pomocí vizualizace a modelování](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)
- [Analýza a modelování architektury](../modeling/analyze-and-model-your-architecture.md)
- [Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)
- [Použití modelů ve vývojových procesech](../modeling/use-models-in-your-development-process.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
