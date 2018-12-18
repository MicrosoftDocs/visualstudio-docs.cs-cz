---
title: 'Diagramy činnosti UML: Referenční | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.activitydiagram.diagram
- vs.teamarch.activitydiagram.toolbox
- vs.teamarch.UMLModelExplorer.activitydiagram
helpviewer_keywords:
- UML diagrams, activity
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- activity diagrams
- UML, activity diagrams
- behaviors, UML
ms.assetid: 07efcd17-2a96-4052-9957-6dcccbb725ee
caps.latest.revision: 50
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2dcfa13a7ac97a5afd3e315fcef13a706c5f4bce
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51810465"
---
# <a name="uml-activity-diagrams-reference"></a>Diagramy činnosti UML: referenční dokumentace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Diagram činnosti* ukazuje obchodní proces nebo proces softwaru jako tok práci prostřednictvím obnáší sérii akcí. Lidé, softwarové součásti nebo počítače mohou provádět tyto akce.  
  
 Diagram činnosti můžete použít k popisu procesy z několika typů, jako jsou následující příklady:  
  
- Obchodních procesů nebo toku práce mezi uživateli a systému. Další informace najdete v tématu [modelování uživatelských požadavků](../modeling/model-user-requirements.md).  
  
- Provést kroky v případu použití. Další informace najdete v tématu [diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md).  
  
- Protokol software, tedy povolených sekvence interakcí mezi komponentami.  
  
- Algoritmus softwaru.  
  
  Toto téma popisuje elementy, které můžete použít v diagramech aktivit. Podrobnější informace o vykreslování aktivit najdete v článku diagramy [diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md). Chcete-li vytvořit diagram činností UML, na **architektura** nabídky, klikněte na tlačítko **nové UML nebo diagramu vrstev**. Další informace o tom, jak nakreslit diagramy modelování obecně naleznete v tématu [modelů a diagramů UML upravit](../modeling/edit-uml-models-and-diagrams.md).  
  
## <a name="reading-activity-diagrams"></a>Čtení diagramy činnosti  
 Tabulky v následujících částech popisují prvky, které můžete použít v diagramu činnosti a jejich hlavní vlastnosti. Úplný seznam vlastnosti prvků, naleznete v tématu [vlastnosti elementů v diagramech činnosti UML](../modeling/properties-of-elements-on-uml-activity-diagrams.md).  
  
 Akce a další prvky, které se zobrazí v diagramu činnosti tvoří jednu aktivitu. Můžete vidět aktivitu v Průzkumníku modelů UML. Vytvoří se při přidání prvního prvku diagramu.  
  
 Další diagram, představte si, že token, nebo vlákna ovládací prvek, předá konektory ze jednu akci na další.  
  
### <a name="simple-control-flows"></a>Jednoduché řízení toků  
 Můžete zobrazit posloupnost akcí se větve a smyčky. Další informace o tom, jak používat zde popsané prvky naleznete v části popisující tok řízení tématu [diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md).  
  
 ![Jednoduchý tok řízení](../modeling/media/uml-actovsimple.png "UML_ActOvSimple")  
  
||||  
|-|-|-|  
|**Obrazec**|**Element**|**Popis a hlavní vlastnosti**|  
|1|**Akce**|Krok v aktivitě, ve kterém software nebo uživatelé provádět určité operace.<br /><br /> Akci můžete spustit, když token dorazila na všech příchozích toků. Při jeho ukončení, tokeny jsou odeslány na všechny odchozí toky.<br /><br /> -   **Tělo** -Určuje akci, která podrobně.<br />-   **Jazyk** – jazyk výrazů v těle.<br />-   **Místní vstupních** – omezení, která musí být splněny, při ukončení provádění. Cílem dosáhnout akce.<br />-   **Místní předpoklady** – omezení, která musí být splněny, než začne provádění.|  
|2|**Tok řízení**|Konektor, který zobrazuje tok řízení mezi akcemi. Interpretace diagramu, představte si, že token toky z jednu akci na další.<br /><br /> Pokud chcete vytvořit tok řízení, použijte **konektor** nástroj.|  
|3|**Počáteční uzel**|Označuje první akci nebo akce v rámci aktivity. Při spuštění aktivity toků token od počátečního uzlu.|  
|4|**Poslední uzel aktivity**|Skončí na aktivitu. Po přijetí tokenu aktivity se ukončí.|  
|5|**Uzel rozhodnutí**|Podmíněná větev v toku. Má jeden vstup a dva nebo více výstupů. Příchozí token splatit na právě jeden z výstupů.|  
|6|**Guard**|Podmínka, která určuje, zda token byl zajištěn tok podél konektor. Nejčastěji používané u odchozích toků uzlů rozhodnutí.<br /><br /> Pokud chcete nastavit ochranu, klikněte pravým tlačítkem na toku, klikněte na tlačítko **vlastnosti** a pak nastavte **Guard** vlastnost.|  
|7|**Sloučit uzlu**|Je potřeba sloučit toky, které byly rozdělení s uzlem rozhodnutí. Má dvě nebo více vstupů a jeden výstup. Token na jakýkoli vstup splatit na výstupu.|  
|8|**Komentář**|Poskytuje další informace o prvcích, ke kterým je spojen.|  
|9|**Volat akci chování**|Akce, která je definována v další podrobnosti o jiného diagramu činnosti.<br /><br /> -   **IsSynchronous** – Pokud je nastavena hodnota true a akce počká, až do doby ukončení aktivity.<br />-   **Chování** -vyvolaná aktivita.|  
|(není vidět)|**Volání operace akce**|Akce, která volá operace v instanci třídy.|  
||**Aktivita**|Postup, který je znázorněný v diagramu činnosti. Pokud chcete zobrazit vlastnosti aktivity, musíte vybrat v **Průzkumníku modelů UML**.<br /><br /> -   **Je jen pro čtení** – Pokud je nastavena hodnota true, aktivita by neměly měnit stav libovolného objektu.<br />-   **Je jedno provedení** – Pokud je nastavena hodnota true a bylo nanejvýš jedno provedení tohoto diagramu současně.|  
||**Diagram činností UML**|Diagram zobrazující aktivity. Pokud chcete zobrazit její vlastnosti, klikněte na prázdnou část diagramu. **Poznámka:** názvy diagramu činnosti, soubor, který obsahuje diagram a zobrazuje diagram aktivity mohou být jiný.|  
  
### <a name="concurrent-flows"></a>Souběžné toků  
 Můžete popsat pořadí akcí, které jsou spouštěny ve stejnou dobu. Další informace najdete v tématu kreslení souběžných toků.  
  
 ![Aktivita diagram znázorňující tok souběžných](../modeling/media/uml-actovconcurrent.png "UML_ActovConcurrent")  
  
||||  
|-|-|-|  
|**Obrazec**|**Element**|**Popis**|  
|11|**Uzly rozvětvení**|Dělí jeden tok do souběžných toků. Každý příchozí token vytvoří token pro každou odchozí konektor.|  
|12|**Připojte se k uzlu**|Kombinuje souběžných toků do jediného toku. Token čekání po každé příchozí tok je token vytvořen na výstupu.|  
|13|**Odesílat signál akce**|Akce, která odesílá zprávy nebo signál pro jinou aktivitu nebo souběžných vláken do stejné aktivity. Typ a obsah zprávy je implicitní podle názvu akce nebo zadaný v další komentáře.<br /><br /> Tato akce může odesílat data v signál, který může být předán akcí v toku objektu nebo vstupní kód pin (16).|  
|14|**Přijmout akci události**|Akce, která čeká na zprávu nebo signál před pokračováním v akci. Typ zprávy, které můžou přijímat akce je odvozené od názvu nebo podle dalších komentáře.<br /><br /> Pokud se akce nemá žádné příchozí tok řízení, vytvoří token pokaždé, když dostane zprávu.<br /><br /> Akce můžou přijímat data signálu, které mohou být předána objektu toku nebo výstup kódu pin (17).<br /><br /> -   **IsUnmarshall** – Pokud je nastavena hodnota true, může existovat několik typem výstupní spojky a data jsou unmarshalled na ně. Pokud má hodnotu false, se zobrazí všechna data na jeden pin.|  
  
###  <a name="DataFlow"></a> Datové toky  
 Popíšete toku dat z jedné akce. Další informace o prvků, které slouží v této části najdete v části kreslení Data proudí tématu pokyny pro náčrt diagramu aktivit.  
  
 ![Aktivita diagram znázorňující tok dat](../modeling/media/uml-actovdata.png "UML_ActOvData")  
  
||||  
|-|-|-|  
|**Obrazec**|**Element**|**Popis**|  
|15|**Uzel objektu**|Představuje data, která předá toku.<br /><br /> -   **Řazení** – způsob, jakým se ukládají více tokenů.<br />-   **Výběr** – spustí proces, který může být definován do jiného diagramu, který filtruje data.<br />-   **Horní mez** -0 znamená, že přímo máte tok; musí předat data \* označuje, že data mohou být uložena v toku.<br />-   **Typ** – typ objektu, uložených a odesílané informace.|  
|16|**Vstupní kód Pin**|Představuje data, která akci, dostanou při provádění.<br /><br /> -   **Typ** – typ objektů přenášených.|  
|17|**Výstupní spojky**|Představuje data, která vytváří akci při provádění.<br /><br /> -   **Typ** – typ objektů přenášených.|  
|18|**Uzel parametru aktivity**|Uzel objektu, jehož prostřednictvím dat přijatých nebo produkované aktivitou.<br /><br /> Použít, když aktivita reprezentována diagramu je volána z jiné aktivity, nebo když diagram popisuje operace nebo funkce.<br /><br /> -   **Typ** – typ objektů přenášených.|  
|(není vidět)|**Objekt toku**|Konektor, který znázorňuje tok dat mezi akcemi a uzly objektu.<br /><br /> Chcete-li vytvořit tok, který objekt, použijte **konektor** nástroje pro propojení vstupní nebo výstupní spojky nebo uzel objektu na jiný element.<br /><br /> -   **Výběr** – spustí proces, který může být definován do jiného diagramu, který filtruje data.<br />-   **Transformace** – spustí proces, který může být definován do jiného diagramu, který transformuje data.<br />-   **IsMulticast** – označuje, že může existovat několik příjemců objekty nebo komponenty.<br />-   **IsMultiReceive** – označuje, že vstupy může dostat k několika objektů nebo komponenty.|  
  
## <a name="see-also"></a>Viz také  
 [Úpravy modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagramy činnosti UML: Pokyny](../modeling/uml-activity-diagrams-guidelines.md)



