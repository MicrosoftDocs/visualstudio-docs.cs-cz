---
title: Analýza a modelování vaší architektury
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Ultimate, exploring code
- Visual Studio Ultimate, visualizing code
- diagrams - modeling
- Visual Studio ALM, modeling
- application, design
- architecture
- code visualization
- application design
- applications, architecture
- code exploration
- Visual Studio ALM, exploring code
- modeling
- application architecture
- application, modeling
- applications, modeling
- architecture [Visual Studio ALM], modeling
- application modeling
- Visual Studio Ultimate, modeling
- architecture [Visual Studio Ultimate], modeling
- application, architecture
- Visual Studio ALM, visualizing code
- applications, designing
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4b32f5585c71f5767a907d9f3eb9c2dc8329ab97
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348875"
---
# <a name="analyze-and-model-your-architecture"></a>Analýza a modelování vaší architektury

Zajistěte, aby že vaše aplikace splňuje požadavky na architekturu pomocí sady Visual Studio architektura a modelování nástroje pro návrh a modelování vaší aplikace.

* Snadněji pochopit stávající kód programu pomocí sady Visual Studio můžete vizualizovat strukturu kódu, chování a vztahy.

* Informování týmu v potřebu respektování závislostí architektury.

* Vytvářejte modely s různými úrovněmi detailů v průběhu životního cyklu aplikací v rámci vašeho vývojového procesu.

Zobrazit [scénář: Změna návrhu pomocí vizualizace a modelování](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

## <a name="to"></a>Chcete-li

|||
|-|-|
|**Vizualizace kódu**:<br /><br /> – Podívejte organizaci a vztahy kódu vytvořením map kódu. Vizualizace závislostí mezi sestavení, oborů názvů, třídy, metody a tak dále.<br />– Podívejte na strukturu třídy a členy pro konkrétní projekt tak, že vytvoříte diagramů tříd z kódu.<br />-Vyhledání konfliktů mezi kódu a jeho návrhu tak, že vytvoříte diagramy závislostí za účelem ověření kódu.|-   [Vizualizace kódu](../modeling/visualize-code.md)<br />-   [Práce s třídami a ostatními typy (návrhář tříd)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Video: Porozumění celkové koncepci kódu pomocí map kódu Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)<br />-   [Video: Ověření závislostí architektury v reálném čase](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)|
|**Definice architektury**:<br /><br /> -Definovat a vynucovat omezení závislosti mezi komponentami váš kód tak, že vytvoříte diagramů závislostí.|-   [Video: Ověření závislosti architektury pomocí sady Visual Studio (kanál 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Ověřování systému s požadavky a určené návrhu:**<br /><br /> -Validate závislostí kódu pomocí diagramů závislostí, které popisují zamýšlenou architekturu a Neumožnit změny, které může být v konfliktu s návrhem.|-   [Video: Ověření závislosti architektury pomocí sady Visual Studio (kanál 9)](https://channel9.msdn.com/Events/Connect/2016/170)|
|**Přizpůsobení modelů a diagramů**:<br /><br /> -Vytvořte vlastní jazyky specifickými pro doménu.|-   [Sada Modeling SDK pro Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Generování textu s použitím šablony T4**:<br /><br /> – Použijte textové bloky a logiky ovládacího prvku uvnitř šablony pro vygenerování souborů založený na textu.<br /> – T4 šablony sestavení pomocí nástroje MSBuild součástí sady Visual Studio|-   [Generování kódu a textové šablony T4](../modeling/code-generation-and-t4-text-templates.md)|
|**Sdílení modelů, diagramy a map kódu pomocí správy verzí Team Foundation**:<br /><br /> -Map kódu, projekty a umístěte diagramů závislostí v rámci správy verzí Team Foundation, můžete je sdílet.| |

Jaké edice sady Visual Studio podporují jednotlivé funkce najdete v tématu [podpora edice nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="types-of-models-and-typical-uses"></a>Typy modelů a typické použití

### <a name="code-maps"></a>Mapy kódu
Mapy kódu vám umožní zjistit, organizaci a vztahy v kódu.

**Obvyklá využití:**

-   Zkontrolujte kód programu to vám umožní lépe pochopit jeho strukturu a její závislosti, jak ji aktualizovat a odhad nákladů na navrhované změny.

**Přejděte na téma:**

-   [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)
-   [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)
-   [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)

### <a name="dependency-diagram"></a>Diagram závislostí
Diagramy závislostí umožňují definovat strukturu aplikace jako sada vrstvy nebo bloky s explicitní závislosti. Můžete spustit ověření ke zjišťování konfliktů mezi závislostmi v kódu a závislostmi je popsaný na diagram závislostí.

**Obvyklá využití:**

-   Stabilizace struktury aplikace pomocí množství změn průběhu své životnosti.
-   Zjišťování konfliktů nechtěné závislosti před vrácením se změnami kódu.

**Přejděte na téma:**

-   [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)
-   [Diagramy závislostí: Referenční dokumentace](../modeling/layer-diagrams-reference.md)
-   [Ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)

### <a name="domain-specific-language-dsl"></a>Jazyka specifického pro doménu (DSL)
DSL je zápis, který návrh pro konkrétní účel. V sadě Visual Studio má obvykle grafickou podobu.

**Obvyklá využití:**

-   Vytvořit nebo nakonfigurovat částí aplikace. Práce je vyžadována k vývoji zápisem a nástroje. Výsledkem může být lepší vhodný k vaší doméně než přizpůsobení UML.
-   Pro velké projekty nebo řádky produktů, kde se investice do vývoje DSL a jeho nástrojů vrácený jeho použití ve více než jeden projekt.

**Přejděte na téma:**

-   [Sada Modeling SDK pro Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

## <a name="where-can-i-get-more-information"></a>Kde lze získat další informace?

[Visual Studio Visualization & Modeling fóra nástroje](http://go.microsoft.com/fwlink/?LinkId=184720)

## <a name="see-also"></a>Viz také:

- [Co je nového](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps a správa životního cyklu aplikací](/azure/devops/user-guide/devops-alm-overview)
