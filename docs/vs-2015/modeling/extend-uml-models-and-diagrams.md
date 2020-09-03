---
title: Rozšiřování modelů a diagramů UML | Microsoft Docs
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
ms.openlocfilehash: ee4e307040f22078ed66f897eaa868ccfd259577
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "82586729"
---
# <a name="extend-uml-models-and-diagrams"></a>Rozšíření modelů a diagramů UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V tomto tématu jsou shrnuty různé způsoby, kterými můžete roztáhnout nástroje pro modelování UML, které jsou součástí sady Visual Studio. Chcete-li zjistit, které verze sady Visual Studio podporují jednotlivé typy modelů a nástroje, přečtěte si téma [podpora verzí pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 V následujícím ukázkovém scénáři vytvoří společnost Fabrikam vzory pro zpracování zavazadel a nainstaluje systémy na letiště. Z jednoho projektového projektu na další má mnoho podobností základní zařízení a software, který ho řídí. Existuje však také několik faktorů, které se velmi liší, jako je například konfigurace dopravníkových pásů, zařízení s vrácením se změnami, přihrádky úložiště a další vybavení pro zpracování balíčku.

 Při spuštění nového projektu tým společnosti Fabrikam vytvoří model UML, který jim umožní diskutovat o těchto požadavcích mezi sebou a zákazníkem. Používají diagramy aktivit k reprezentaci toku vaků s uzly objektů, které představují jednotlivé součásti vybavení. Model UML přímo nereprezentuje kód systému.

 Tým nástrojů společnosti Fabrikam přináší řadu vylepšení, která usnadňují vývojovým týmům. V následujících částech jsou popsány různé druhy rozšíření, která můžete definovat. Některé z těchto postupů můžete zkombinovat do jednoho rozšíření sady Visual Studio.

 Další informace najdete v tomto videu: ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo")[MSDN jak mám řady: nástroje a rozšiřitelnost UML](https://msdn.microsoft.com/vstudio/ff859492).

## <a name="requirements"></a><a name="Requirements"></a> Požadavků

- [Sada Visual Studio SDK](../extensibility/visual-studio-sdk.md).

- [Sada Modeling SDK pro Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48148).

## <a name="profiles"></a>Profily
 Profily umožňují definovat stereotypy a další vlastnosti prvků UML.

 Vývojáři nástrojů společnosti Fabrikam definují stereotypy na objektových uzlech diagramů činnosti, jako je «pásový pás» a «oddělení odregistrací». Když člen týmu vytvoří schéma pro zpracování zavazadel pomocí diagramu činnosti, může nyní nastavit stereotypy k určení toho, jaký typ zařízení každý uzel představuje. Vývojáři nástrojů definují další vlastnosti u některých stereotypů, aby mohli uživatelé zaznamenávat hodnoty, jako je kapacita dopravníkového pásu, a psaní rukou oddělení pro vrácení se změnami.

 Další informace najdete v tématu [Definování profilu pro rozšiřování UML](../modeling/define-a-profile-to-extend-uml.md).

## <a name="custom-toolbox-items"></a>Vlastní položky sady nástrojů
 Vlastní položka sady nástrojů vytvoří prvek nebo skupinu prvků z prototypu, který definujete v diagramu. Můžete například vytvořit nástroj, který vytváří případy použití v konkrétní barvě nebo stereotypu, nebo skupinu tříd a přidružení, které představují vzor návrhu. Tyto položky sady nástrojů můžete přidat do rozšíření aplikace Visual Studio a distribuovat je ostatním uživatelům.

 Další informace najdete v tématu [definice vlastní položky sady nástrojů pro modelování](../modeling/define-a-custom-modeling-toolbox-item.md).

## <a name="validation"></a>Ověřování
 Můžete definovat pravidla, aby se zajistilo, že model UML odpovídá zadaným omezením.

 Vývojáři nástrojů společnosti Fabrikam definují pravidla, která členům týmu umožní vyhnout se jednoduchým chybám v modelech zpracování zavazadel. Například služba Odregistrace nemůže být připojena přímo k přihrádce úložiště. Mezi nimi musí být aspoň pás dopravník.

 Další informace najdete v tématu [Definování omezení ověření pro modely UML](../modeling/define-validation-constraints-for-uml-models.md).

## <a name="menu-commands"></a>Příkazy nabídky
 Můžete definovat příkazy, které mohou uživatelé vyvolat kliknutím pravým tlačítkem myši na prvky v diagramu UML. Příkazy mohou aktualizovat model a diagramy nebo provádět jiné operace v [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] .

 Společnost Fabrikam definuje příkazy nabídky pro automatizaci často prováděných operací, jako je například vytvoření plochy pro vracení se změnami a připojení k vybranému pásovému pásu nebo změna uspořádání diagramu podle pravidel rozložení společnosti.

 Viz [Definování příkazu nabídky v diagramu modelování](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

## <a name="gestures"></a>Gesta
 Můžete definovat příkazy, které uživatelé spouštějí, dvojitým kliknutím na prvek diagramu nebo přetahováním na diagram nebo prvek v diagramu. Můžete definovat příkazy, které mohou řešit položky přetažené z jiných diagramů UML, z jiných částí sady Visual Studio nebo z jiných aplikací nebo Průzkumníka Windows (nebo Průzkumníka souborů.

 Členové týmu společnosti Fabrikam mohou přidružit soubor, jako je například specifikace s libovolným prvkem modelu, přetažením z plochy systému Windows. Vývojáři nástroje definovali stereotyp, který poskytuje libovolný prvek s vlastností cesta k souboru, a gesto, které nastaví stereotyp a cestu k souboru, když je soubor umístěn na prvek.

 Další informace naleznete v tématu [definice obslužné rutiny gesta v diagramu modelování](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).

## <a name="responding-to-changes"></a>Reakce na změny
 Můžete napsat kód, který reaguje na změny v modelu, ať už způsobené akcemi uživatelů, nebo jiným kódem programu.

 Vývojáři společnosti Fabrikam vytvoří kód, který automaticky nastaví barvu prvku závislého na jeho stereotypu. Díky tomu mohou uživatelé snadno odlišit různé role, které hrají prvky v modelech.

 Další informace naleznete v tématu [How to: reagovat na změny v modelu UML](../misc/how-to-respond-to-changes-in-a-uml-model.md).

## <a name="model-bus"></a>Sběrnice modelu
 Sběrnice modelů umožňuje přístup k diagramu nebo modelu z jiného diagramu nebo z jiného [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] rozšíření. Mimo jiné to umožňuje rozložit informace na více než jeden model, aby více uživatelů mohl pracovat současně na kombinovaném modelu.

 Společnost Fabrikam používá pro reprezentaci vybavení pro zpracování zavazadel prvky v diagramech činnosti. Každá položka zařízení může mít podrobnější specifikaci v jiném diagramu, který může být v jiném modelu. Omezení ověřování v diagramu flowu zavazadel můžou z ostatních diagramů načíst relevantní vlastnosti tohoto zařízení. Odkazy na ostatní diagramy jsou uloženy v dalších vlastnostech definovaných ve stereotypech.

 Další informace najdete v tématu [Integrace modelů UML s jinými modely a nástroji](../modeling/integrate-uml-models-with-other-models-and-tools.md).

## <a name="generation"></a>Nezbytných
 Z modelu můžete generovat kód programu, skripty, konfigurace, dokumenty, nové modely nebo jiné artefakty.

 V systémech zavazadel, které společnost Fabrikam navrhuje, je většina programového kódu stejná jako u jednoho projektu na další. Hlavním aspektem proměnné je plán toku zavazadel kolem letiště. Po tom, co tým návrhu má zkušenosti s několika prvními projekty, vývojáři nástroje vytvoří šablonu, která generuje, z modelu toku zavazadel, většinu programového kódu proměnné a dalších souborů, jako jsou například uživatelské dokumenty. To významně snižuje dobu vývoje a četnost chyb pro každý nový projekt.

 Další informace najdete v tématu [generování souborů z modelu UML](../modeling/generate-files-from-a-uml-model.md).

## <a name="team-foundation-server-integration"></a>Integrace Team Foundation Server
 Pracovní položky můžete propojit s prvky modelu a přistupovat k propojeným položkám programově.

 Vývojáři nástrojů společnosti Fabrikam napíší nástroj, který generuje pracovní plán pro každý projekt letiště. Pracovní položky v plánu jsou propojeny s prvky modelu.

 Další informace naleznete v tématu [definice obslužné rutiny propojení pracovní položky](../modeling/define-a-work-item-link-handler.md).

## <a name="tools-that-update-models"></a>Nástroje, které aktualizují modely
 Můžete vytvořit samostatné aplikace a rozšíření sady Visual Studio, které mohou načíst modely UML.

 Vývojáři společnosti Fabrikam vytvářejí nástroj, který čte model a generuje sestavy průběhu práce na jednotlivých prvcích modelu.

 Další informace najdete v tématu [čtení modelu UML v programovém kódu](../modeling/read-a-uml-model-in-program-code.md).

## <a name="domain-specific-languages"></a>Jazyky specifické pro doménu
 Pokud často používáte konkrétní typ modelu, může být užitečné vytvořit jazyk specifický pro doménu. To se dá udělat tak, aby lépe vyhovovalo vašim obchodním potřebám, než je model UML, ale vyžaduje více úsilí při jejich sestavování a údržbě. Další informace najdete v tématu [MODELING SDK for Visual Studio – jazyky specifické pro doménu](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).

## <a name="external-resources"></a>Externí zdroje

|**Kategorie**|**Odkazy**|
|------------------|---------------|
|**Videa**|![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") [MSDN postup I série: nástroje a rozšiřitelnost UML](https://msdn.microsoft.com/vstudio/ff859492)<br /><br /> ![odkaz na video](../data-tools/media/playvideo.gif "PlayVideo") [kanál 9: UML se sadou Visual Studio](https://channel9.msdn.com/posts/clinted/)|
|**Fóra**|-   [Nástroje pro vizualizaci sady Visual Studio & modelování](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Sada Visual Studio vizualizace & Modeling SDK (nástroje DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Blogy**|[Blog sady Visual Studio ALM + Team Foundation Server](https://devblogs.microsoft.com/devops/welcome-to-the-visual-studio-alm-team-foundation-server-blog/)|
|**Technické články a deníky**|[Centrum architektury MSDN](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>Viz také
 [Vytváření modelů pro](../modeling/create-models-for-your-app.md) [Reference k rozhraní API vaší aplikace pro rozšíření modelování UML](../modeling/api-reference-for-uml-modeling-extensibility.md)
