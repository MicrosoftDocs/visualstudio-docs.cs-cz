---
title: Reference diagramů závislostí
ms.date: 09/28/2018
ms.topic: reference
f1_keywords:
- vs.teamarch.layerdiagram.layerexplorer.artifactlink
- vs.teamarch.layerdiagram.layerexplorer.artifactlink.properties
- vs.teamarch.layerdiagram.diagram
- vs.teamarch.UMLModelExplorer.layerdiagram
- vs.teamarch.layerdiagram.layerexplorer
- vs.teamarch.layerdiagram.shapes.properties
- vs.teamarch.layerdiagram.toolbox
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7711d0b0f369f43cc7becf92cbdcfc986cd3a6a8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661485"
---
# <a name="dependency-diagrams-reference"></a>Diagramy závislostí: Referenční dokumentace

V aplikaci Visual Studio můžete použít *Diagram závislostí* k vizualizaci logické architektury systému vysoké úrovně. Diagram závislosti uspořádá fyzické artefakty ve vašem systému do logických abstraktních skupin nazývaných *vrstvy*. Tyto vrstvy popisují hlavní úlohy, které artefakty provádějí, nebo hlavní součásti systému. Každá vrstva může také obsahovat vnořené vrstvy, které popisují podrobnější úkoly.

Pokud chcete zjistit, které edice sady Visual Studio podporují tuto funkci, přečtěte si téma [Podpora edice pro nástroje pro architekturu a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Diagramy závislostí pro projekty .NET Core jsou podporovány počínaje verzí Visual Studio 2019 verze 16,2.

Můžete určit zamýšlené nebo existující závislosti mezi vrstvami. Tyto závislosti, které jsou reprezentovány jako šipky, označují, které vrstvy mohou používat nebo aktuálně používají funkce reprezentované jinými vrstvami. Uspořádáním systému do vrstev, které popisují různé role a funkce, diagram závislosti vám pomůže pochopit, znovu použít a spravovat kód.

Použijte diagram závislosti, který vám umožní provádět následující úlohy:

- Sdělit existující nebo zamýšlenou logickou architekturu vašeho systému.

- Objevte konflikty mezi vaším existujícím kódem a zamýšlenou architekturou.

- Vizualizujte dopad změn zamýšlené architektury při refaktorování, aktualizaci nebo vývoj systému.

- Posílit zamýšlenou architekturu během vývoje a údržby kódu tím, že zahrnete ověření pomocí operací vrácení se změnami a sestavování.

Toto téma popisuje prvky, které lze použít v diagramu závislostí. Podrobnější informace o vytváření a vykreslování diagramů závislostí najdete v tématu [diagramy závislostí: pokyny](../modeling/layer-diagrams-guidelines.md). Další informace o vzorech vrstvení najdete na [webu vzory & postupy](http://go.microsoft.com/fwlink/?LinkId=145794).

## <a name="reading-dependency-diagrams"></a>Čtení diagramů závislostí

![Prvky v diagramech závislostí](../modeling/media/uml_layerrefreading.png)

Následující tabulka popisuje prvky, které můžete použít v diagramu závislostí.

|**Automatického**|**Element**|**Popis**|
|-|-|-|
|první|**Vrstvení**|Logická skupina fyzických artefaktů ve vašem systému. Tyto artefakty mohou být obory názvů, projekty, třídy, metody a tak dále.<br /><br /> Chcete-li zobrazit artefakty, které jsou propojeny s vrstvou, otevřete místní nabídku pro vrstvu a pak zvolte možnost **Zobrazit odkazy** a otevřete **Průzkumníka vrstev**.<br /><br /> Další informace naleznete v tématu [Průzkumník vrstev](#Explorer).<br /><br /> -   **zakázané závislosti oboru názvů** – určuje, že artefakty přidružené k této vrstvě nemůžou záviset na zadaných oborech názvů.<br />-   **zakázané obory názvů** – určuje, že artefakty přidružené k této vrstvě nesmí patřit do zadaných oborů názvů.<br />-   **požadované obory názvů** – určuje, že artefakty přidružené k této vrstvě musí patřit do jednoho ze zadaných oborů názvů.|
|odst|**Závislosti**|Označuje, že jedna vrstva může použít funkci v jiné vrstvě, ale ne naopak.<br /><br /> -   **směr** – určuje směr závislosti.|
|3|**Obousměrná závislost**|Označuje, že jedna vrstva může používat funkci v jiné vrstvě a naopak.<br /><br /> -   **směr** – určuje směr závislosti.|
|4|**Vytvořena**|Slouží k přidání obecných poznámek do diagramu nebo prvků v diagramu.|
|5|**Odkaz na komentář**|Slouží k propojení komentářů s prvky v diagramu.|

## <a name="Explorer"></a>Průzkumník vrstev

Jednotlivé vrstvy můžete propojit s artefakty ve vašem řešení, jako jsou projekty, třídy, obory názvů, soubory projektu a další části softwaru. Číslo ve vrstvě znázorňuje počet artefaktů, které jsou propojeny s vrstvou. Při čtení počtu artefaktů ve vrstvě ale pamatujte na následující:

- Pokud vrstva odkazuje na artefakt, který obsahuje jiné artefakty, ale vrstva není propojena přímo s jiným artefaktem, pak číslo obsahuje pouze propojené artefakty. Jiné artefakty jsou však zahrnuty do analýzy během ověřování vrstvy.

     Pokud je vrstva například spojena s jedním oborem názvů, pak počet propojených artefaktů je 1, přestože obor názvů obsahuje třídy. Pokud vrstva obsahuje rovněž propojení s jednotlivými třídami v oboru názvů, bude počet zahrnovat propojené třídy.

- Pokud například vrstva obsahuje jiné vrstvy, které jsou spojeny s artefakty, pak je vrstva kontejneru také propojena s těmito artefakty, i když číslo vrstvy kontejneru tyto artefakty neobsahuje.

Další informace o propojování vrstev a artefaktů naleznete v tématu:

- [Diagramy závislostí: pokyny](../modeling/layer-diagrams-guidelines.md)

- [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)

### <a name="examine-the-linked-artifacts"></a>Kontrola propojených artefaktů

V diagramu závislostí otevřete místní nabídku pro jednu nebo více vrstev a pak zvolte možnost **Zobrazit odkazy**.

**Průzkumník vrstev** otevře a zobrazí artefakty, které jsou propojeny s vybranými vrstvami. **Průzkumník vrstev** má sloupec, který zobrazuje všechny vlastnosti propojení artefaktů.

> [!NOTE]
> Pokud nevidíte všechny tyto vlastnosti, rozbalte okno **Průzkumník vrstev** .

|**Sloupec v Průzkumníkovi vrstev**|**Popis**|
|-|-|
|**Kategorie**|Typ artefaktu, jako je například třída, obor názvů, zdrojový soubor a tak dále|
|**Vrstvení**|Vrstva, která odkazuje na artefakt|
|**Podporuje ověřování**|Je-li **nastavena hodnota true**, proces ověření vrstvy může ověřit, zda projekt odpovídá závislostem na nebo z tohoto prvku.<br /><br /> Je-li nastavena **hodnota false**, odkaz se neúčastní procesu ověřování vrstvy.<br /><br /> Další informace najdete v tématu [diagramy závislostí: pokyny](../modeling/layer-diagrams-guidelines.md).|
|**RID**|Odkaz na propojený artefakt|

## <a name="see-also"></a>Viz také:

- [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)
