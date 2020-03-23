---
title: Rozšíření modelů a diagramů UML | Dokumenty společnosti Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: b5bfa61e-ea59-4c3b-b5af-53475d7d13cd
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f4c490abbcd5b970c5bf9586ea881be4c5d62a4
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302327"
---
# <a name="extend-uml-models-and-diagrams"></a>Rozšíření modelů a diagramů UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Toto téma shrnuje různé způsoby, kterými můžete rozšířit nástroje modelování UML součástí sady Visual Studio. Informace o tom, které verze sady Visual Studio podporují každý typ modelu a nástroj, naleznete [v tématu Podpora verzí pro architekturu a nástroje pro modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 V následujícím příkladu scénáře společnost Fabrikam navrhuje a instaluje letištní systémy pro manipulaci se zavazadly. Z jednoho projektu letiště na další, existuje mnoho podobností v základním vybavení a software, který ji ovládá. Existuje však také několik faktorů, které se značně liší, jako je konfigurace dopravníkových pásů, odbavovacích přepážek, skladovacích přihrádek a dalších zařízení pro manipulaci s taškami.

 Při spuštění nového projektu vytvoří tým společnosti Fabrikam model UML, který jim pomůže diskutovat o těchto požadavcích mezi sebou a se svým zákazníkem. Používají diagramy činnosti k reprezentaci toku pytlů, s uzly objektu představující mise každého zařízení. Model UML nepředstavuje přímo kód systému.

 Tým nástrojů společnosti Fabrikam provádí řadu vylepšení, která pomáhají vývojovým týmům. Následující části popisují různé druhy rozšíření, které můžete definovat. Můžete kombinovat několik z těchto technik do jedné rozšíření sady Visual Studio.

 Další informace naleznete v tomto videu: ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo")[MSDN Jak do i series: UML nástroje a rozšiřitelnost](https://msdn.microsoft.com/vstudio/ff859492).

## <a name="requirements"></a><a name="Requirements"></a>Požadavky

- [Sada Visual Studio SDK](../extensibility/visual-studio-sdk.md).

- [Modelování sady SDK pro Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48148).

## <a name="profiles"></a>Profily
 Profily umožňují definovat stereotypy a další vlastnosti na prvky UML.

 Vývojáři nástrojů společnosti Fabrikam definují stereotypy na uzlech aktivit, jako je například "dopravní pás" a "checkin desk". Když člen týmu vytvoří schéma zpracování zavazadel pomocí diagramu aktivity, může nyní nastavit stereotypy, které označují, jaký typ zařízení každý uzel představuje. Vývojáři nástrojů definovat další vlastnosti na některé stereotypy, takže uživatelé mohou zaznamenávat hodnoty, jako je kapacita dopravního pásu a handness vrácení pokladny.

 Další informace naleznete [v tématu Definování profilu pro rozšíření uml](../modeling/define-a-profile-to-extend-uml.md).

## <a name="custom-toolbox-items"></a>Vlastní položky panelu nástrojů
 Vlastní položka panelu nástrojů vytvoří prvek nebo skupinu prvků z prototypu, který definujete v diagramu. Můžete například vytvořit nástroj, který vytvoří případy použití v určité barvě nebo stereotypu, nebo skupinu tříd a přidružení, která představuje návrhový vzor. Tyto položky panelu nástrojů můžete přidat do rozšíření sady Visual Studio a distribuovat je ostatním uživatelům.

 Další informace naleznete [v tématu Definování položky panelu nástrojů vlastního modelování](../modeling/define-a-custom-modeling-toolbox-item.md).

## <a name="validation"></a>Ověřování
 Můžete definovat pravidla, která zajistí, že model UML splňuje zadaná omezení.

 Vývojáři nástrojů společnosti Fabrikam definují pravidla, která členům týmu pomáhají vyhnout se jednoduchým chybám v modelech manipulace se zavazadly. Například vrácení se změnami nelze připojit přímo k přihrádce úložiště. Musí mezi nimi být alespoň dopravní pás.

 Další informace naleznete v [tématu Definování omezení ověření pro modely UML](../modeling/define-validation-constraints-for-uml-models.md).

## <a name="menu-commands"></a>Příkazy nabídky
 Můžete definovat příkazy, které mohou uživatelé vyvolat kliknutím pravým tlačítkem myši na prvky v diagramu UML. Příkazy můžete aktualizovat model a diagramy nebo [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]provádět jiné operace v aplikaci .

 Společnost Fabrikam definuje příkazy nabídky pro automatizaci často prováděných operací, jako je například vytvoření odbavovací přepážky a připojení k vybranému dopravnímu pásu nebo změna uspořádání diagramu podle pravidel rozvržení společnosti.

 Viz [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

## <a name="gestures"></a>Gesta
 Příkazy, které uživatelé iniciují, můžete definovat poklepáním na prvek diagramu nebo přetažením do diagramu nebo prvku v diagramu. Můžete definovat příkazy, které mohou zůrek zůrek zprostředkovat položky přetažené z jiných diagramů UML, z jiných částí sady Visual Studio nebo z jiných aplikací nebo Průzkumníka Windows (nebo Průzkumníka souborů.

 Členové týmu společnosti Fabrikam mohou přidružit soubor, například specifikaci, k libovolnému prvku modelu jeho přetažením z plochy systému Windows. Vývojáři nástrojů definovali stereotyp, který poskytuje libovolný prvek s vlastností cesty k souboru, a gesto, které nastaví stereotyp a cestu k souboru při přepnuto na prvek.

 Další informace naleznete [v tématu Definování obslužné rutiny gest v diagramu modelování](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).

## <a name="responding-to-changes"></a>Reakce na změny
 Můžete napsat kód, který reaguje na změny v modelu, ať už způsobené akcemi uživatele nebo jiným programovým kódem.

 Vývojáři společnosti Fabrikam vytvářejí kód, který automaticky nastaví barvu prvku v závislosti na jeho stereotypu. To usnadňuje uživatelům rozlišit různé role, které hrají prvky v modelech.

 Další informace naleznete v [tématu How to: Respond to Changes in a UML Model](../misc/how-to-respond-to-changes-in-a-uml-model.md).

## <a name="model-bus"></a>Model Bus
 Model Bus umožňuje přístup k diagramu nebo modelu [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] z jiného diagramu nebo z jiného rozšíření. Mimo jiné to umožňuje šířit informace mezi více než jeden model, takže několik lidí může pracovat na kombinovaném modelu současně.

 Společnost Fabrikam používá prvky na diagramech činnosti k reprezentaci zařízení pro manipulaci se zavazadly. Každá položka zařízení může mít podrobnější specifikaci v jiném diagramu, který může být v jiném modelu. Ověřovací omezení na diagramu toku zavazadel mohou načíst příslušné vlastnosti zařízení z ostatních diagramů. Odkazy na ostatní diagramy jsou uloženy v další vlastnosti definované v stereotypy.

 Další informace naleznete [v tématu Integrace modelů UML s jinými modely a nástroji](../modeling/integrate-uml-models-with-other-models-and-tools.md).

## <a name="generation"></a>Generace
 Z modelu můžete generovat programový kód, skripty, konfigurace, dokumenty, nové modely nebo jiné artefakty.

 V zavazadlových systémech, které společnost Fabrikam navrhuje, je velká část programového kódu stejná z jednoho projektu na druhý. Hlavním proměnlivým aspektem je plán toku zavazadel kolem letiště. Poté, co návrhářský tým má zkušenosti z několika prvních projektů, vývojáři nástrojů vytvoří šablonu, která generuje z modelu toku zavazadel velkou část kódu proměnné programu a další soubory, jako jsou uživatelské dokumenty. To výrazně snižuje dobu vývoje a míru chyb pro každý nový projekt.

 Další informace naleznete v [tématu Generování souborů z modelu UML](../modeling/generate-files-from-a-uml-model.md).

## <a name="team-foundation-server-integration"></a>Integrace serveru Team Foundation
 Pracovní položky můžete propojit s prvky modelu a přístup k propojeným položkám programově.

 Vývojáři nástrojů společnosti Fabrikam napíší nástroj, který generuje pracovní plán pro každý projekt letiště. Pracovní položky v plánu jsou propojeny s prvky modelu.

 Další informace naleznete [v tématu Definování obslužné rutiny propojení pracovních položek](../modeling/define-a-work-item-link-handler.md).

## <a name="tools-that-update-models"></a>Nástroje, které aktualizují modely
 Můžete vytvořit samostatné aplikace a rozšíření sady Visual Studio, které lze načíst modely UML.

 Vývojáři společnosti Fabrikam vytvoří nástroj, který přečte model a vygeneruje sestavy průběhu práce na každém prvku modelu.

 Další informace naleznete [v tématu Čtení modelu UML v kódu programu](../modeling/read-a-uml-model-in-program-code.md).

## <a name="domain-specific-languages"></a>Jazyky specifické pro doménu
 Pokud často používáte určitý typ modelu, může být užitečné vytvořit jazyk specifický pro doménu. To může být provedeno tak, aby vyhovovalo vašim obchodním potřebám více než model UML, ale vyžaduje větší úsilí k jeho vytvoření a údržbě. Další informace naleznete v [tématu Modelování sady SDK pro sady Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).

## <a name="external-resources"></a>Externí zdroje

|**Kategorie**|**Odkazy**|
|------------------|---------------|
|**Videa**|![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") [MSDN Jak do mám series: UML nástroje a rozšiřitelnost](https://msdn.microsoft.com/vstudio/ff859492)<br /><br /> ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") [Kanál 9: UML s Visual Studio](https://channel9.msdn.com/posts/clinted/)|
|**Fóra**|-   [Nástroje pro vizualizaci & visual studia Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visualization Visualization & Modelování SDK (NÁSTROJE DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Blogy**|[Visual Studio ALM + Team Foundation Server Blog](https://blogs.msdn.com/b/visualstudioalm)|
|**Technické články a časopisy**|[Centrum architektury MSDN](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>Viz také
 [Vytvoření modelů pro](../modeling/create-models-for-your-app.md) odkaz na rozhraní API aplikace [pro rozšiřitelnost modelování UML](../modeling/api-reference-for-uml-modeling-extensibility.md)
