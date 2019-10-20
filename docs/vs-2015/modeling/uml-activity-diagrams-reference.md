---
title: 'Diagramy činnosti UML: referenční informace | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3a882867720e9cca2d51419643ebe60e692817a1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658452"
---
# <a name="uml-activity-diagrams-reference"></a>Diagramy činnosti UML: referenční dokumentace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Diagram aktivity* znázorňuje obchodní proces nebo proces softwaru jako tok práce prostřednictvím řady akcí. Tyto akce mohou provádět osoby, softwarové komponenty nebo počítače.

 Diagram činnosti můžete použít k popisu procesů několika typů, například následujících příkladů:

- Obchodní proces nebo tok práce mezi uživateli a vaším systémem. Další informace najdete v tématu [Model požadavky uživatelů na uživatele](../modeling/model-user-requirements.md).

- Kroky provedené v případu použití. Další informace najdete v tématu [Diagramy případů použití UML: pokyny](../modeling/uml-use-case-diagrams-guidelines.md).

- Softwarový protokol, tedy povolené posloupnosti interakcí mezi komponentami.

- Softwarový algoritmus.

  Toto téma popisuje prvky, které můžete použít v diagramech aktivit. Podrobnější informace o diagramech činnosti kreslení najdete v tématu [diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md). Diagram činnosti UML vytvoříte tak, že v nabídce **Architektura** kliknete na **Nový UML nebo Diagram vrstev**. Další informace o tom, jak kreslit diagramy modelování obecně, najdete v tématu [Úprava modelů a diagramů UML](../modeling/edit-uml-models-and-diagrams.md).

## <a name="reading-activity-diagrams"></a>Čtení diagramů aktivit
 Tabulky v následujících částech popisují prvky, které můžete použít v diagramu činnosti a jejich hlavní vlastnosti. Úplný seznam vlastností prvků naleznete v tématu [Vlastnosti elementů v diagramech činnosti UML](../modeling/properties-of-elements-on-uml-activity-diagrams.md).

 Akce a další prvky, které se zobrazují v diagramu činnosti, tvoří jednu aktivitu. Aktivitu můžete zobrazit v Průzkumníku modelů UML. Vytvoří se při přidání prvního prvku do diagramu.

 Chcete-li si přečíst diagram, Představte si, že token nebo podproces řízení projde konektory od jedné akce k dalšímu.

### <a name="simple-control-flows"></a>Jednoduché toky ovládacích prvků
 Můžete zobrazit posloupnost akcí s větvemi a smyčkami. Další informace o tom, jak používat níže popsané prvky, naleznete v části popisující tok řízení v tématu [diagramy činnosti UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md).

 ![Jednoduchý tok řízení](../modeling/media/uml-actovsimple.png "UML_ActOvSimple")

||||
|-|-|-|
|**Automatického**|**Element**|**Popis a hlavní vlastnosti**|
|první|**Kroky**|Krok v aktivitě, ve kterém uživatelé nebo software provádějí určitou úlohu.<br /><br /> Akce se může spustit, když se token dokončí ve všech příchozích tocích. V případě, že skončí, tokeny se odesílají do všech odchozích toků.<br /><br /> -   **tělo** – určuje podrobnosti o akci.<br />**jazyk** -    – jazyk výrazu v těle.<br />-   **místní následné podmínky** – omezení, která musí být splněna při ukončení provádění. Cíl dosažený akcí.<br />-   **místní předběžné podmínky** – omezení, která musí být splněna před zahájením provádění.|
|odst|**Tok řízení**|Konektor, který zobrazuje tok řízení mezi akcemi. Chcete-li interpretovat diagram, Představte si, že token přetéká od jedné akce k dalšímu.<br /><br /> Chcete-li vytvořit tok řízení, použijte nástroj **konektor** .|
|3|**Počáteční uzel**|Označuje první akci nebo akce v aktivitě. Když se aktivita spustí, token se bude natékat z počátečního uzlu.|
|4|**Konečný uzel aktivity**|Konec aktivity. Při přijetí tokenu se aktivita ukončí.|
|5|**Uzel rozhodnutí**|Podmíněná větev v toku. Má jeden vstup a dva nebo více výstupů. Příchozí token se objeví pouze v jednom z výstupů.|
|6|**Chráněn**|Podmínka, která určuje, zda může token procházet podél konektoru. Nejčastěji se používá na odchozích tocích rozhodovacího uzlu.<br /><br /> Pokud chcete nastavit ochranu, klikněte pravým tlačítkem myši na tok, klikněte na **vlastnosti** a pak nastavte vlastnost **Guard** .|
|čl|**Uzel sloučení**|Vyžaduje se pro sloučení toků, které byly rozděleny s rozhodovacím uzlem. Má dva nebo více vstupů a jeden výstup. Na výstupu se objeví token na jakémkoli vstupu.|
|8|**Vytvořena**|Poskytuje další informace o prvcích, ke kterým je propojena.|
|9|**Akce volání chování**|Akce, která je definována podrobněji v jiném diagramu činnosti.<br /><br /> -    je-li**nastavena na hodnotu** true, akce počká, dokud nedojde k ukončení aktivity.<br />**chování** -    – vyvolaná aktivita.|
|(není zobrazeno)|**Akce volání operace**|Akce, která volá operaci na instanci třídy.|
||**Aktivita**|Průběh práce, která je znázorněna v diagramu činnosti. Chcete-li zobrazit vlastnosti aktivity, je nutné ji vybrat v **Průzkumníku modelů UML**.<br /><br /> -   **je pouze pro čtení – Pokud je nastaveno** na hodnotu true, aktivita by neměla měnit stav žádného objektu.<br />-   **je jedno spuštění** – Pokud je nastaveno na true, existuje více než jedno spuštění tohoto diagramu najednou.|
||**Diagram činnosti UML**|Diagram, který zobrazuje aktivitu. Chcete-li zobrazit jeho vlastnosti, klikněte na prázdnou část diagramu. **Poznámka:**  Všechny názvy diagramu činnosti, soubor obsahující diagram a aktivita zobrazená v diagramu se můžou lišit.|

### <a name="concurrent-flows"></a>Souběžné toky
 Můžete popsat sekvence akcí, které se spouštějí ve stejnou dobu. Další informace najdete v tématu kreslení souběžných toků.

 ![Diagram aktivity zobrazující souběžný tok](../modeling/media/uml-actovconcurrent.png "UML_ActovConcurrent")

||||
|-|-|-|
|**Automatického**|**Element**|**Popis**|
|odst|**Uzel rozvětvení**|Vydělí jeden tok do souběžných toků. Každý příchozí token vytvoří token u každého odchozího konektoru.|
|12,5|**Uzel připojení**|Kombinuje souběžné toky do jediného toku. Když má každý příchozí tok čekající token, vytvoří se na výstupu token.|
|13,5|**Akce odeslání signálu**|Akce, která odesílá zprávu nebo signál do jiné aktivity nebo do souběžného vlákna ve stejné aktivitě. Typ a obsah zprávy jsou odvozeny z názvu akce nebo zadané v dalších komentářích.<br /><br /> Akce může odesílat data v signálu, který se dá předat akci v toku objektu nebo vstupním PIN kódu (16).|
|čtrnáct|**Akce přijetí události**|Akce, která čeká na zprávu nebo signál předtím, než může tato akce pokračovat. Typ zprávy, na kterou se akce může přijmout, je odvozený podle názvu nebo zadaného v dalších komentářích.<br /><br /> Pokud akce nemá žádný příchozí tok řízení, vytvoří token vždy, když obdrží zprávu.<br /><br /> Akce může přijímat data v signálu, který je možné předat do toku objektu nebo výstupního kódu PIN (17).<br /><br /> -   **IsUnmarshall** – Pokud má hodnotu true, může existovat několik typových výstupních spojek a data se do nich nevztahují. V případě hodnoty false se všechna data zobrazí v jednom PIN kódu.|

### <a name="DataFlow"></a>Toky dat
 Můžete popsat tok dat z jedné akce do druhé. Další informace o prvcích používaných v této části najdete v části toky dat kreslení v tématu pokyny k vykreslení diagramu činnosti.

 ![Diagram aktivity znázorňující tok dat](../modeling/media/uml-actovdata.png "UML_ActOvData")

||||
|-|-|-|
|**Automatického**|**Element**|**Popis**|
|15|**Uzel objektu**|Představuje data, která jsou předávána podél toku.<br /><br /> **řazení** -    – způsob uložení více tokenů.<br />**výběr** -    – vyvolá proces, který může být definován v jiném diagramu, který filtruje data.<br />-   **horní mez** -0 znamená, že data musí být předána přímo spolu s tokem;  \* označuje, že data se můžou ukládat do toku.<br />**typ** -    – typ objektů uložených a odeslaných.|
|16bitovém|**Vstupní PIN kód**|Představuje data, která může akce přijmout, když se spustí.<br /><br /> **typ** -    – typ přenášených objektů.|
|sedmnáct|**Výstupní kód PIN**|Představuje data, která akce generuje, když se spustí.<br /><br /> **typ** -    – typ přenášených objektů.|
|let|**Uzel parametru aktivity**|Uzel objektu, jehož prostřednictvím je možné přijmout nebo vyprodukovat data aktivity.<br /><br /> Používá se při volání aktivity reprezentované diagramem z jiné aktivity, nebo když diagram popisuje operaci nebo funkci.<br /><br /> **typ** -    – typ přenášených objektů.|
|(není zobrazeno)|**Tok objektů**|Konektor, který zobrazuje tok dat mezi akcemi a uzly objektů.<br /><br /> Chcete-li vytvořit tok objektu, pomocí nástroje **konektoru** propojte vstupní nebo výstupní kód PIN nebo uzel objektu s jiným prvkem.<br /><br /> **výběr** -    – vyvolá proces, který může být definován v jiném diagramu, který filtruje data.<br />-   **Transformation** – vyvolá proces, který může být definován v jiném diagramu, který transformuje data.<br />-    typu "**vícesmìrového vysílání** " – označuje, že může existovat několik objektů nebo součástí příjemců.<br />-   **IsMultireceive** – označuje, že vstupy mohou být přijímány z několika objektů nebo komponent.|

## <a name="see-also"></a>Viz také
 Diagramy činnosti UML pro [Úpravy modelů a diagramů](../modeling/edit-uml-models-and-diagrams.md) [UML: pokyny](../modeling/uml-activity-diagrams-guidelines.md)
