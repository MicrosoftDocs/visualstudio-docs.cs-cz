---
title: Nástroje pro modelování & analýzy architektury
description: Navrhovat a modelovat aplikaci, abyste se ujistili, že vaše aplikace splňuje požadavky architektury.
ms.custom: SEO-VS-2020
ms.date: 06/04/2021
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
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 542b74e7d3bb73847303fa4215651eea7e110e91
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384873"
---
# <a name="analyze-and-model-your-architecture"></a>Analýza a modelování vaší architektury

Zajistěte, aby vaše aplikace splňovala požadavky architektury, Visual Studio architektury a nástrojů pro modelování k návrhu a modelování aplikace.

1. Lepší pochopení stávajícího kódu programu [vizualizací struktury](visualize-code.md) kódu, chování a relací pomocí map kódu a diagramů závislostí
    - Vytvořením map kódu si můžete zobrazit uspořádání kódu a **vztahy.** 
    - Vizualizujte závislosti mezi sestaveními, obory názvů, třídami, metodami atd.
    - Vyhledejte konflikty mezi kódem a jeho návrhem vytvořením **diagramů závislostí** pro ověření kódu.
    - Prohlédněte si strukturu třídy a členy pro konkrétní projekt [vytvořením diagramů tříd z kódu](../ide/class-designer/designing-and-viewing-classes-and-types.md).
    - [Generování textu pomocí šablon T4 s](../modeling/code-generation-and-t4-text-templates.md) bloky textu a řídicí logiky uvnitř šablon pro generování textových souborů 
    
1. Učte svůj tým o tísnění architektonických závislostí.

1. V rámci procesu vývoje můžete vytvářet modely na různých úrovních podrobností v průběhu životního cyklu aplikace.

Viz [Scénář: Změna návrhu pomocí vizualizace a modelování](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

## <a name="code-maps"></a>Mapy kódu

Mapy kódu jsou jedním typem modelu, který vám pomůže vidět organizaci a vztahy v kódu.

Mapy můžete použít k prozkoumání kódu programu, abyste lépe porozuměli jeho struktuře a závislostem, jak ho aktualizovat a odhadnout náklady na navrhované změny.

Další informace:
- [Instalace nástrojů pro kód architektury](install-architecture-tools.md)
- [Mapování závislostí napříč vaším řešením](../modeling/map-dependencies-across-your-solutions.md)
- [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)
- [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="dependency-diagrams"></a>Diagramy závislostí

Diagramy závislostí umožňují definovat strukturu aplikace jako sadu vrstev nebo bloků s explicitními závislostmi. Živé ověřování ukazuje konflikty mezi závislostmi v kódu a závislostmi popsanými v diagramu závislostí.

Diagramy závislostí slouží k: 
- Stabilizujte strukturu aplikace prostřednictvím mnoha změn v průběhu jejího života.
- Před kontrolou změn kódu zjistěte neúmyslné konflikty závislostí.

Další informace:
- [Instalace nástrojů pro kód architektury](install-architecture-tools.md)
- [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)
- [Diagramy závislostí: Referenční dokumentace](../modeling/layer-diagrams-reference.md)
- [Ověřování kódu pomocí diagramů závislostí](../modeling/validate-code-with-layer-diagrams.md)

## <a name="domain-specific-language-dsl-models"></a>Jazykové modely specifické pro doménu (DSL)

DSL je notace, kterou navrhujete pro konkrétní účel. V Visual Studio je to obvykle grafické rozhraní.

Pomocí jazyka specifického pro doménu můžete: 
- Vygenerujte nebo nakonfigurujte části aplikace. Při vývoji notace a nástrojů se vyžaduje práce. Výsledek může být pro vaši doménu lepší než přizpůsobení UML.
- Pro velké projekty nebo v produktových linkách, kde se investice do vývoje DSL a jeho nástrojů vrací jeho použitím ve více než jednom projektu.

Další informace:
- [Sada Modeling SDK pro Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)


## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Podpora edicí pro nástroje pro architekturu a modelování

Visual Studio je k dispozici v několika edicích. Ne všechny tyto možnosti podporují nástroje pro architekturu a modelování. Dostupnost jednotlivých nástrojů je znázorněna v následující tabulce.

|**Funkce**|**Edice Enterprise**|**Edice Professional**|**Community Edition**|
|-|-|-|-|
|**Mapy kódu**|Yes|Podporuje jenom čtení map kódu, filtrování map kódu, přidávání nových obecných uzlů a vytváření nového řízeného grafu z výběru.|-|
|**Diagramy závislostí**|Yes|Podporuje pouze čtení diagramů závislostí.|Podporuje pouze čtení diagramů závislostí.|
|**Řízené grafy** (diagramy DGML)|Yes|Yes|Yes|
|**Klonování kódu**|Yes|-|-|
