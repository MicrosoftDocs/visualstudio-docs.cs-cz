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
ms.openlocfilehash: 38a65a98c1dca5542d3e0e667cb623283bb164c7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602427"
---
# <a name="analyze-and-model-your-architecture"></a>Analýza a modelování vaší architektury
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ujistěte se, že vaše aplikace splňuje požadavky uživatelů pomocí architektury sady Visual Studio a nástrojů pro modelování pro návrh a modelování vaší aplikace. Snadnější pochopení stávajícího programového kódu pomocí sady Visual Studio k vizualizaci struktury kódu, chování a vztahů.

 Vytvářejte modely v rámci životního cyklu aplikace na různých úrovních v rámci svého procesu vývoje. Sledujte požadavky, úkoly, testovací případy, chyby a další práci, která je přidružena k vašim modelům, propojením prvků modelu s Team Foundation Server pracovními položkami a vaším plánem vývoje. Viz [scénář: Změna návrhu pomocí vizualizace a modelování](../modeling/scenario-change-your-design-using-visualization-and-modeling.md).

 Chcete-li zjistit, které verze aplikace Visual Studio podporují jednotlivé funkce, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)

## <a name="to"></a>Chcete-li

|||
|-|-|
|**Vizualizovat kód**:<br /><br /> – Podívejte se na organizaci a vztahy kódu vytvořením map kódu. Vizualizujte závislosti mezi sestaveními, obory názvů, třídami, metodami a tak dále.<br />– Podívejte se na strukturu třídy a členy pro konkrétní projekt vytvořením diagramů tříd z kódu.<br />– Vyhledejte konflikty mezi vaším kódem a jeho návrh vytvořením diagramů vrstev pro ověření kódu.<br /><br /> **Poznámka**: v této verzi sady Visual Studio se jako místo *grafu závislostí*používá pojem *Mapa kódu* . Výraz *grafu* , pokud se používá samostatně, se vztahuje na orientovaný graf nebo diagram DGML (nebo dokument). Mapy kódu jsou specializovaného typu diagramu DGML.|-   [vizualizace kódu](../modeling/visualize-code.md)<br />-   [práce s třídami a jinými typy (návrhář tříd)](../ide/working-with-classes-and-other-types-class-designer.md)<br />-   [video: pochopení závislostí kódu pomocí vizualizace (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252065)<br />-   [video: vizualizace dopadu změny (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252068)|
|**Popište a sdělte požadavkům uživatelů**:<br /><br /> – Objasnění uživatelských scénářů, obchodních pravidel a dalších požadavků a zajištění jejich konzistence díky vykreslování diagramů UML, jako jsou případy použití, aktivity a diagramy tříd.|-   [vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)<br />[požadavky uživatelů -    modelu](../modeling/model-user-requirements.md)<br />-   [video: vylepšení architektury prostřednictvím modelování (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252078)|
|**Definovat architekturu**:<br /><br /> – Modelujte velkou škálu softwarového systému a vzorů návrhu vykreslením diagramů komponent, tříd a sekvencí UML.<br />– Definovat a vynutit omezení pro závislosti mezi komponentami vašeho kódu vytvořením diagramů vrstev.|-   [vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)<br />-   [modelování architektury vaší aplikace](../modeling/model-your-app-s-architecture.md)<br />-   [video: vylepšení architektury prostřednictvím modelování (Channel 9)](http://go.microsoft.com/fwlink/?LinkID=252078)<br />-   [video: použití diagramů vrstev k návrhu a ověření vaší architektury (kanál 9)](http://go.microsoft.com/fwlink/?LinkID=252073)|
|**Ověřte svůj systém s požadavky a zamýšleným návrhem:**<br /><br /> -Definujte testy přijetí nebo testy systému na základě modelů požadavků. Tím se vytvoří silný vztah mezi testy a požadavky vašich uživatelů a pomůže vám to při změně požadavků snadněji aktualizovat systém.<br />– Ověřte závislosti kódu pomocí diagramů vrstev, které popisují zamýšlenou architekturu a zabraňují změnám, které by mohly být v konfliktu s návrhem.|-   [ověřit systém během vývoje](../modeling/validate-your-system-during-development.md)<br />-   [video: použití diagramů vrstev k návrhu a ověření vaší architektury (kanál 9)](http://go.microsoft.com/fwlink/?LinkID=252073)|
|**Sdílení modelů, diagramů a map kódu pomocí správy verzí Team Foundation**:<br /><br /> – Vložte mapy kódu, projekty modelování, diagramy UML a diagramy vrstev v rámci správy verzí Team Foundation, abyste je mohli sdílet.|Pokud máte více uživatelů, kteří pracují s těmito položkami v rámci správy verzí Team Foundation, použijte tyto pokyny, které vám pomohou vyhnout se problémům s řízením verzí:<br /><br /> -   [Správa modelů a diagramů v rámci správy verzí](../modeling/manage-models-and-diagrams-under-version-control.md)|
|**Generování nebo konfigurace částí aplikace z jazyků UML nebo specifických pro doménu**:<br /><br /> – Udělejte svůj návrh větší reakce na změny požadavků a snadnou proměnnou v rámci řady produktů.|-   [generování a konfigurace vaší aplikace z modelů](../modeling/generate-and-configure-your-app-from-models.md)|
|**Přizpůsobení modelů a diagramů**:<br /><br /> – Přizpůsobte modely na to, jak je váš projekt používá, definováním dalších vlastností prvků UML, omezení ověření, aby se zajistilo, že vaše modely odpovídají vašim obchodním pravidlům a dalším příkazům nabídky a položkám nástrojů.<br />– Vytvořte vlastní jazyky specifické pro doménu.|-   [rozšiřování modelů a diagramů UML](../modeling/extend-uml-models-and-diagrams.md)<br />[sada SDK pro -    Modeling pro Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|
|**Generovat text pomocí šablon T4**:<br /><br /> – Použijte textové bloky a ovládací logiku v šablonách k vygenerování textových souborů.|-   [generování kódu a textové šablony T4](../modeling/code-generation-and-t4-text-templates.md)|

## <a name="types-of-models-and-their-uses"></a>Typy modelů a jejich použití

|**Typ modelu a typické použití**|
|-------------------------------------|
|**Mapy kódu**<br /><br /> Mapy kódu vám pomůžou vidět organizaci a vztahy v kódu.<br /><br /> Typická použití:<br /><br /> -Prověřte programový kód, abyste mohli lépe pochopit jeho strukturu a jejich závislosti, jak je aktualizovat a odhadnout náklady na navrhované změny.<br /><br /> Další informace:<br /><br /> -   [závislosti map napříč vašimi řešeními](../modeling/map-dependencies-across-your-solutions.md)<br />-   [použití map kódu k ladění aplikací](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [nalezení potenciálních problémů pomocí analyzátorů mapy kódu](../modeling/find-potential-problems-using-code-map-analyzers.md)|
|**Diagram vrstev**<br /><br /> Diagramy vrstev umožňují definovat strukturu aplikace jako sadu vrstev nebo bloků s explicitními závislostmi. Můžete spustit ověřování pro zjištění konfliktů mezi závislostmi v kódu a závislostmi popsanými v diagramu vrstev.<br /><br /> Typická použití:<br /><br /> – Stabilizovat strukturu aplikace prostřednictvím mnoha změn během jejího života.<br />-Zjištění neúmyslného konfliktu závislostí před vrácením změn do kódu.<br /><br /> Další informace:<br /><br /> -   [vytváření diagramů vrstev z kódu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [diagramy vrstev: referenční](../modeling/layer-diagrams-reference.md) dokumentace<br />-   [ověřování kódu pomocí diagramů vrstev](../modeling/validate-code-with-layer-diagrams.md)|
|**Model UML**<br /><br /> Model UML obsahuje několik zobrazení, včetně tříd, komponent, případů použití, aktivit a sekvenčních diagramů. UML můžete přizpůsobit tak, aby vyhovovalo vaší doméně aplikace. Například můžete k prvkům modelu připojit značky, další informace a omezení. Můžete také definovat nástroje, které pracují s modely. Viz [vytvoření modelů pro vaši aplikaci](../modeling/create-models-for-your-app.md).<br /><br /> Typická použití:<br /><br /> -Popsat požadavky a navrhnout. Můžete rychle použít UML pro vývoj libovolné aplikace. Viz [použití modelů v procesu vývoje](../modeling/use-models-in-your-development-process.md).<br />– Generování nebo konfigurace testů nebo částí aplikace. K přizpůsobení zápisu a vývoji šablon generování nebo konfigurovatelné aplikace je potřeba některá práce. Viz téma [generování a konfigurace aplikace z modelů](../modeling/generate-and-configure-your-app-from-models.md).<br />– Pro obecné popisy a pro generování kódu nebo konfiguraci v menších projektech.|
|**Jazyk specifický pro doménu (DSL)**<br /><br /> DSL je zápis, který navrhujete pro určitý účel. V aplikaci Visual Studio je obvykle grafický.<br /><br /> Typická použití:<br /><br /> – Generování nebo konfigurace částí aplikace Práce je nutná pro vývoj zápisu a nástrojů. Výsledkem může být lepší přizpůsobení vaší doméně než přizpůsobení UML.<br />– Pro velké projekty nebo v řádcích produktů, kde investice do vývoje DSL a jejích nástrojů se vrátí pomocí jejího použití ve více než jednom projektu.<br /><br /> Další informace:<br /><br /> [sada SDK pro -    Modeling pro Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)|

## <a name="where-can-i-get-more-information"></a>Kde lze získat další informace?

|||
|-|-|
|**Fóra**|-   [nástrojů pro modelování sady Visual Studio pro vizualizaci &](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Sada Visual Studio vizualizace & Modeling SDK (nástroje DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|

## <a name="see-also"></a>Viz také

- [Co je nového pro modelování v aplikaci Visual Studio 2015](../modeling/what-s-new-for-design-in-visual-studio.md)
- [DevOps a správa životního cyklu aplikací](https://msdn.microsoft.com/library/74a1f71d-7f23-4c71-8fd7-89ede614fab6)
