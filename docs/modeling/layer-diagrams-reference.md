---
title: Odkaz na diagramů závislostí
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 1ef2d68cb0f8e3d6904bdf3f3ebbab321649c3e1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920923"
---
# <a name="dependency-diagrams-reference"></a>Diagramy závislostí: referenční dokumentace

V sadě Visual Studio, můžete použít *diagram závislostí* můžete vizualizovat vysoké úrovně, logickou architekturu systému. Diagram závislostí slouží k uspořádání fyzické artefaktů ve vašem systému do logických, abstraktních skupin nazvaných *vrstvy*. Tyto vrstvy popsat hlavní úlohy, které tyto artefakty provádějí nebo hlavní součásti systému. Každá vrstva může také obsahovat vnořené vrstvy, které popisují podrobnější úlohy.

Chcete-li zjistit, jaké edice sady Visual Studio podporují tuto funkci, přečtěte si téma [podpora edice nástroje architektury a modelování](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> Diagramy závislostí nejsou podporovány pro projekty .NET Core v sadě Visual Studio 2017.

Můžete určit zamýšlené nebo existující závislosti mezi vrstvami. Tyto závislosti, které jsou reprezentovány šipkami, označení, které vrstvy mohou použít nebo právě používají funkce představované ostatními vrstvami. Uspořádání vašeho systému do vrstev, které popisují různé role a funkce, diagram závislostí může pomoci bylo snazší porozumět, opakovaně používat a spravovat váš kód.

Použijte diagram závislostí můžete provádět následující úlohy:

-   Komunikaci existující, nebo určený logickou architekturu systému.

-   Zjištění konfliktu mezi váš stávající kód a zamýšlenou architekturu.

-   Vizualizujte dopad změn na zamýšlenou architekturu. při refaktorování, aktualizovat nebo vyvíjí vašeho systému.

-   Posílení zamýšlenou architekturu během vývoje a údržba kódu včetně ověření pomocí vrácení se změnami a operací sestavení.

Toto téma popisuje elementy, které můžete použít na diagram závislostí. Podrobné informace o tom, jak vytvořit a kreslit diagramy závislostí, přečtěte si [diagramy závislostí: pokyny](../modeling/layer-diagrams-guidelines.md). Další informace o vzorech vrstev najdete [vzory a postupy site](http://go.microsoft.com/fwlink/?LinkId=145794).

## <a name="reading-dependency-diagrams"></a>Čtení diagramů závislostí

![Prvky na diagramů závislostí](../modeling/media/uml_layerrefreading.png)

Následující tabulka popisuje prvky, které můžete použít na diagram závislostí.

|**Obrazec**|**Element**|**Popis**|
|-|-|-|
|1|**Vrstvy**|Logické skupiny fyzické artefaktů ve vašem systému. Tyto artefakty mohou být obory názvů, projekty, třídy, metody a tak dále.<br /><br /> Chcete-li zobrazit artefakty, které jsou propojeny s vrstvou, otevřete místní nabídku vrstvy a klikněte na tlačítko **zobrazit odkazy** otevřete **Průzkumník vrstev**.<br /><br /> Další informace najdete v tématu [Průzkumník vrstev](#Explorer).<br /><br /> -   **Je zakázané závislosti Namespace** – Určuje, že artefakty přidružené k této vrstvě nemůže záviset na zadaných oborů názvů trasy.<br />-   **Je zakázané obory názvů** – Určuje, že artefakty přidružené k této vrstvě nesměly patřit zadanému oboru názvů.<br />-   **Požadované obory názvů** – Určuje, že artefakty přidružené k této vrstvě musí patřit do jedné ze zadaných oborů názvů trasy.|
|2|**Závislost**|Označuje, že jedna vrstva může použít funkci v jiné vrstvě, ale ne naopak.<br /><br /> -   **Směr** -Určuje směr závislost.|
|3|**Obousměrná závislost**|Označuje, že jedna vrstva může použít funkci v jiné vrstvě a naopak.<br /><br /> -   **Směr** -Určuje směr závislost.|
|4|**Komentář**|Slouží k přidání obecné poznámky diagramu nebo prvku v diagramu.|
|5|**Odkaz na komentář**|Použijte k propojení komentářů k prvkům v diagramu.|

## <a name="Explorer"></a> Průzkumník vrstev

Můžete propojit s každou vrstvu artefaktů ve vašem řešení, jako jsou projekty, třídy, obory názvů, soubory projektu a jiné části vašeho softwaru. Číslo ve vrstvě zobrazuje počet artefaktů, které jsou spojeny s vrstvou. Ale při čtení počtu artefaktů ve vrstvě mějte na paměti následující:

-   Pokud vrstva odkazuje na artefakt, který obsahuje jiné artefakty, ale vrstva není propojena přímo s jiným artefaktem, pak číslo obsahuje pouze propojené artefakty. Jiné artefakty jsou však zahrnuty do analýzy během ověřování vrstvy.

     Pokud je vrstva například spojena s jedním oborem názvů, pak počet propojených artefaktů je 1, přestože obor názvů obsahuje třídy. Pokud vrstva obsahuje rovněž propojení s jednotlivými třídami v oboru názvů, bude počet zahrnovat propojené třídy.

-   Pokud například vrstva obsahuje jiné vrstvy, které jsou spojeny s artefakty, pak je vrstva kontejneru také propojena s těmito artefakty, i když číslo vrstvy kontejneru tyto artefakty neobsahuje.

Další informace o propojení vrstvami a artefakty naleznete v tématu:

-   [Diagramy závislostí: pokyny](../modeling/layer-diagrams-guidelines.md)

-   [Vytváření diagramů závislostí z kódu](../modeling/create-layer-diagrams-from-your-code.md)

### <a name="examine-the-linked-artifacts"></a>Prozkoumejte propojených artefaktů

Na diagram závislostí, otevřete místní nabídku pro jednu nebo více vrstev a klikněte na tlačítko **zobrazit odkazy**.

**Průzkumník vrstev** otevře a zobrazí artefakty, které jsou propojeny s vrstvami vybrané. **Průzkumník vrstev** má sloupec, který zobrazuje vlastnosti propojení artefaktů.

> [!NOTE]
> Pokud nevidíte všechny tyto vlastnosti, rozbalte **Průzkumník vrstev** okna.

|**Sloupec v Průzkumníku vrstev**|**Popis**|
|-|-|
|**Kategorie**|Druh artefaktu, jako jsou třídy, oboru názvů, zdrojový soubor a tak dále|
|**Vrstvy**|Vrstva, která odkazuje na artefakt|
|**Podporuje ověřování**|Pokud **True**, pak do procesu ověření vrstev můžete ověřit, že projekt odpovídá závislostí do nebo z tohoto elementu.<br /><br /> Pokud **False**, potom na odkaz není součástí procesu ověření vrstev.<br /><br /> Další informace najdete v tématu [diagramy závislostí: pokyny](../modeling/layer-diagrams-guidelines.md).|
|**identifikátor**|Odkaz na propojeného artefaktu|

## <a name="see-also"></a>Viz také:

- [Vytváření modelů pro aplikaci](../modeling/create-models-for-your-app.md)
