---
title: Analýza a modelování vaší architektury
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- diagrams - modeling
- architecture
- code visualization
- application design
- code exploration
- modeling
- application architecture
- architecture [Visual Studio ALM], modeling
- application modeling
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e1db28867ea47752aa74b7898c44e797c0704594
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544219"
---
# <a name="analyze-and-model-your-architecture"></a>Analýza a modelování vaší architektury

Zajistěte, aby vaše aplikace splňovala požadavky na architekturu pomocí architektury sady Visual Studio a nástrojů pro modelování pro návrh a modelování vaší aplikace.

* Snadnější pochopení stávajícího programového kódu pomocí sady Visual Studio k vizualizaci struktury kódu, chování a vztahů.

* Informujte tým o nutnosti respektovat závislosti architektury.

* Vytvářejte modely v rámci životního cyklu aplikace na různých úrovních v rámci svého procesu vývoje.

Viz [scénář: Změna návrhu pomocí vizualizace a modelování](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

## <a name="article-reference"></a>Reference k článku

|Scénář|Články|
|-|-|
|**Vizualizovat kód**:<br /><br />– Podívejte se na organizaci a vztahy kódu vytvořením map kódu. Vizualizujte závislosti mezi sestaveními, obory názvů, třídami, metodami a tak dále.<br />– Podívejte se na strukturu třídy a členy pro konkrétní projekt vytvořením diagramů tříd z kódu.<br />– Vyhledejte konflikty mezi vaším kódem a jeho návrh vytvořením diagramů závislostí pro ověření kódu.|- [Vizualizovat kód](../modeling/visualize-code.md)<br />- [Práce s třídami a jinými typy (Návrhář tříd)](../ide/class-designer/designing-and-viewing-classes-and-types.md)<br />- [Video: Principy návrhu z kódu pomocí map kódu Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />- [Video: ověření závislostí architektury v reálném čase](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|
|**Definovat architekturu**:<br /><br />– Definovat a vynutit omezení závislostí mezi komponentami vašeho kódu vytvořením diagramů závislostí.|- [Video: ověření závislostí architektury pomocí sady Visual Studio (kanál 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Ověřte svůj systém s požadavky a zamýšleným návrhem:**<br /><br />– Ověřte závislosti kódu pomocí diagramů závislostí, které popisují zamýšlenou architekturu a zabraňují změnám, které by mohly být v konfliktu s návrhem.|- [Video: ověření závislostí architektury pomocí sady Visual Studio (kanál 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Přizpůsobení modelů a diagramů**:<br /><br />– Vytvořte vlastní jazyky specifické pro doménu.|- [Sada Modeling SDK pro Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Generovat text pomocí šablon T4**:<br /><br />– Použijte textové bloky a ovládací logiku v šablonách k vygenerování textových souborů.<br /> -T4 šablona sestavení pomocí nástroje MSBuild, který je součástí sady Visual Studio|- [Generování kódu a textové šablony T4](../modeling/code-generation-and-t4-text-templates.md)|
|**Sdílení modelů, diagramů a map kódu pomocí správy verzí Team Foundation**:<br /><br />– Vložte mapy kódu, projekty a diagramy závislosti v rámci správy verzí Team Foundation, abyste je mohli sdílet.| |

Pokud chcete zjistit, které edice sady Visual Studio podporují jednotlivé funkce, přečtěte si téma [Podpora edice pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport) .

## <a name="types-of-models-and-typical-uses"></a>Typy modelů a typické použití

### <a name="code-maps"></a>Mapy kódu

Mapy kódu vám pomůžou vidět organizaci a vztahy v kódu.

**Typická použití:**

- Projděte si kód programu, abyste mohli lépe pochopit jeho strukturu a její závislosti, jak je aktualizovat a odhadnout náklady na navrhované změny.

**Si**

- [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)
- [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)
- [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)

### <a name="dependency-diagrams"></a>Diagramy závislostí

Diagramy závislostí umožňují definovat strukturu aplikace jako sadu vrstev nebo bloků s explicitními závislostmi. Při živém ověřování se zobrazí konflikty mezi závislostmi v kódu a závislostmi popsanými v diagramu závislostí.

**Typická použití:**

- Stabilizací struktury aplikace prostřednictvím mnoha změn během jejího života.
- Před vrácením změn kódu se objevují neúmyslné konflikty závislostí.

**Si**

- [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)
- [Diagramy závislostí: Referenční dokumentace](../modeling/layer-diagrams-reference.md)
- [Ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)

### <a name="domain-specific-language-dsl"></a>Jazyk specifický pro doménu (DSL)

DSL je zápis, který navrhujete pro určitý účel. V aplikaci Visual Studio je obvykle grafický.

**Typická použití:**

- Generování nebo konfigurace částí aplikace Práce je nutná pro vývoj zápisu a nástrojů. Výsledkem může být lepší přizpůsobení vaší doméně než přizpůsobení UML.
- Pro velké projekty nebo v řádcích produktů, kde investice do vývoje DSL a jejích nástrojů se vrátí pomocí jejího použití ve více než jednom projektu.

**Si**

- [Sada Modeling SDK pro Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

## <a name="see-also"></a>Viz také

- [Co je nového pro modelování v aplikaci Visual Studio 2017](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps a správa životního cyklu aplikací](/azure/devops/user-guide/devops-alm-overview)
