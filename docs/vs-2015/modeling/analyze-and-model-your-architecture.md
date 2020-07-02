---
title: Analýza a modelování vaší architektury | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
ms.assetid: c9f04cfa-72bd-419d-a952-616eed01472e
caps.latest.revision: 129
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3e00735a180ec951a8afced0f5c74f7a9466e50b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534092"
---
# <a name="analyze-and-model-your-architecture"></a>Analýza a modelování vaší architektury
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ujistěte se, že vaše aplikace splňuje požadavky uživatelů pomocí architektury sady Visual Studio a nástrojů pro modelování pro návrh a modelování vaší aplikace. Snadnější pochopení stávajícího programového kódu pomocí sady Visual Studio k vizualizaci struktury kódu, chování a vztahů.

 Vytvářejte modely v rámci životního cyklu aplikace na různých úrovních v rámci svého procesu vývoje. Sledujte požadavky, úkoly, testovací případy, chyby a další práci, která je přidružena k vašim modelům, propojením prvků modelu s Team Foundation Server pracovními položkami a vaším plánem vývoje. Viz [scénář: Změna návrhu pomocí vizualizace a modelování](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

 Chcete-li zjistit, které verze aplikace Visual Studio podporují jednotlivé funkce, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="to"></a>Akce

|Scénář|Články|
|-|-|
|**Vizualizovat kód**:<br /><br /> – Podívejte se na organizaci a vztahy kódu vytvořením map kódu. Vizualizujte závislosti mezi sestaveními, obory názvů, třídami, metodami a tak dále.<br />– Podívejte se na strukturu třídy a členy pro konkrétní projekt vytvořením diagramů tříd z kódu.<br />– Vyhledejte konflikty mezi vaším kódem a jeho návrh vytvořením diagramů vrstev pro ověření kódu.<br /><br /> **Poznámka**: v této verzi sady Visual Studio se jako místo *grafu závislostí*používá pojem *Mapa kódu* . Výraz *grafu* , pokud se používá samostatně, se vztahuje na orientovaný graf nebo diagram DGML (nebo dokument). Mapy kódu jsou specializovaného typu diagramu DGML.|-   [Vizualizovat kód](../modeling/visualize-code.md)<br />-   [Práce s třídami a jinými typy (Návrhář tříd)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [Video: pochopení závislostí kódu pomocí vizualizace (Channel 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Understand-your-code-dependencies-through-visualization)<br />-   [Video: vizualizace dopadu změny (kanál 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Visualize-the-impact-of-a-change)|
|**Popište a sdělte požadavkům uživatelů**:<br /><br /> – Objasnění uživatelských scénářů, obchodních pravidel a dalších požadavků a zajištění jejich konzistence díky vykreslování diagramů UML, jako jsou případy použití, aktivity a diagramy tříd.|-   [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)<br />-   [Modelování uživatelských požadavků](../modeling/model-user-requirements.md)<br />-   [Video: vylepšení architektury prostřednictvím modelování (kanál 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Improving-architecture-through-modeling)|
|**Definovat architekturu**:<br /><br /> – Modelujte velkou škálu softwarového systému a vzorů návrhu vykreslením diagramů komponent, tříd a sekvencí UML.<br />– Definovat a vynutit omezení pro závislosti mezi komponentami vašeho kódu vytvořením diagramů vrstev.|-   [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)<br />-   [Modelování architektury aplikace](../modeling/model-your-app-s-architecture.md)<br />-   [Video: vylepšení architektury prostřednictvím modelování (kanál 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Improving-architecture-through-modeling)<br />-   [Video: použití diagramů vrstev k návrhu a ověření vaší architektury (kanál 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)|
|**Ověřte svůj systém s požadavky a zamýšleným návrhem:**<br /><br /> -Definujte testy přijetí nebo testy systému na základě modelů požadavků. Tím se vytvoří silný vztah mezi testy a požadavky vašich uživatelů a pomůže vám to při změně požadavků snadněji aktualizovat systém.<br />– Ověřte závislosti kódu pomocí diagramů vrstev, které popisují zamýšlenou architekturu a zabraňují změnám, které by mohly být v konfliktu s návrhem.|-   [Ověření systému během vývoje](../modeling/validate-your-system-during-development.md)<br />-   [Video: použití diagramů vrstev k návrhu a ověření vaší architektury (kanál 9)](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)|
|**Sdílení modelů, diagramů a map kódu pomocí správy verzí Team Foundation**:<br /><br /> – Vložte mapy kódu, projekty modelování, diagramy UML a diagramy vrstev v rámci správy verzí Team Foundation, abyste je mohli sdílet.|Pokud máte více uživatelů, kteří pracují s těmito položkami v rámci správy verzí Team Foundation, použijte tyto pokyny, které vám pomohou vyhnout se problémům s řízením verzí:<br /><br /> -   [Správa modelů a diagramů v rámci správy verzí](../modeling/manage-models-and-diagrams-under-version-control.md)|
|**Generování nebo konfigurace částí aplikace z jazyků UML nebo specifických pro doménu**:<br /><br /> – Udělejte svůj návrh větší reakce na změny požadavků a snadnou proměnnou v rámci řady produktů.|-   [Generování a konfigurace aplikace z modelů](../modeling/generate-and-configure-your-app-from-models.md)|
|**Přizpůsobení modelů a diagramů**:<br /><br /> – Přizpůsobte modely na to, jak je váš projekt používá, definováním dalších vlastností prvků UML, omezení ověření, aby se zajistilo, že vaše modely odpovídají vašim obchodním pravidlům a dalším příkazům nabídky a položkám nástrojů.<br />– Vytvořte vlastní jazyky specifické pro doménu.|-   [Rozšiřování modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md)<br />-   [Sada Modeling SDK pro Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Generovat text pomocí šablon T4**:<br /><br /> – Použijte textové bloky a ovládací logiku v šablonách k vygenerování textových souborů.|-   [Generování kódu a textové šablony T4](../modeling/code-generation-and-t4-text-templates.md)|

## <a name="types-of-models-and-their-uses"></a>Typy modelů a jejich použití

|**Typ modelu a typické použití**|
|-------------------------------------|
|**Mapy kódu**<br /><br /> Mapy kódu vám pomůžou vidět organizaci a vztahy v kódu.<br /><br /> Typická použití:<br /><br /> -Prověřte programový kód, abyste mohli lépe pochopit jeho strukturu a jejich závislosti, jak je aktualizovat a odhadnout náklady na navrhované změny.<br /><br /> Přečtěte si:<br /><br /> -   [Mapování závislostí napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)|
|**Diagram vrstev**<br /><br /> Diagramy vrstev umožňují definovat strukturu aplikace jako sadu vrstev nebo bloků s explicitními závislostmi. Můžete spustit ověřování pro zjištění konfliktů mezi závislostmi v kódu a závislostmi popsanými v diagramu vrstev.<br /><br /> Typická použití:<br /><br /> – Stabilizovat strukturu aplikace prostřednictvím mnoha změn během jejího života.<br />-Zjištění neúmyslného konfliktu závislostí před vrácením změn do kódu.<br /><br /> Přečtěte si:<br /><br /> -   [Vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy vrstev: Referenční dokumentace](../modeling/layer-diagrams-reference.md)<br />-   [Ověřování kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)|
|**Model UML**<br /><br /> Model UML obsahuje několik zobrazení, včetně tříd, komponent, případů použití, aktivit a sekvenčních diagramů. UML můžete přizpůsobit tak, aby vyhovovalo vaší doméně aplikace. Například můžete k prvkům modelu připojit značky, další informace a omezení. Můžete také definovat nástroje, které pracují s modely. Viz [vytvoření modelů pro vaši aplikaci](../modeling/create-models-for-your-app.md).<br /><br /> Typická použití:<br /><br /> -Popsat požadavky a navrhnout. Můžete rychle použít UML pro vývoj libovolné aplikace. Viz [použití modelů v procesu vývoje](../modeling/use-models-in-your-development-process.md).<br />– Generování nebo konfigurace testů nebo částí aplikace. K přizpůsobení zápisu a vývoji šablon generování nebo konfigurovatelné aplikace je potřeba některá práce. Viz téma [generování a konfigurace aplikace z modelů](../modeling/generate-and-configure-your-app-from-models.md).<br />– Pro obecné popisy a pro generování kódu nebo konfiguraci v menších projektech.|
|**Jazyk specifický pro doménu (DSL)**<br /><br /> DSL je zápis, který navrhujete pro určitý účel. V aplikaci Visual Studio je obvykle grafický.<br /><br /> Typická použití:<br /><br /> – Generování nebo konfigurace částí aplikace Práce je nutná pro vývoj zápisu a nástrojů. Výsledkem může být lepší přizpůsobení vaší doméně než přizpůsobení UML.<br />– Pro velké projekty nebo v řádcích produktů, kde investice do vývoje DSL a jejích nástrojů se vrátí pomocí jejího použití ve více než jednom projektu.<br /><br /> Přečtěte si:<br /><br /> -   [Sada Modeling SDK pro Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|

## <a name="where-can-i-get-more-information"></a>Zdroje dalších informací

|Prostředek|Odkazy|
|-|-|
|**Fóra**|-   [Nástroje pro vizualizaci sady Visual Studio & modelování](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Sada Visual Studio vizualizace & Modeling SDK (nástroje DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|

## <a name="see-also"></a>Viz také

- [Co je nového pro modelování v aplikaci Visual Studio 2015](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps a správa životního cyklu aplikací](https://msdn.microsoft.com/library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
