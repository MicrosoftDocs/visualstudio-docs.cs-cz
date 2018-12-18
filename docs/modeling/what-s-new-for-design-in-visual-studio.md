---
title: Co je nového pro návrh
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- what's new [VIsual Studio ALM], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio ALM], What's New
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ebe304cafa5e8ed4eae287750aeb8e2db02fbc31
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062280"
---
# <a name="whats-new-for-design-in-visual-studio"></a>Novinky pro programátory ve Visual Studiu

## <a name="live-dependency-validation"></a>Ověřování závislostí v reálném čase

Odebrání nechtěné závislosti je důležitou součástí správy technický dluh. Živé ověření závislosti je teď zahrnutá, poskytuje přesné informace o problémech a plně čerpat výhody nových funkcí v editoru a seznamu chyb.

![Ověřování závislostí v reálném čase v akci](media/dep-validation-whatsnew-01.png)

Prostředí pro vytváření změnil provádět ověřování závislostí zjistitelnější a dostupnější, změně terminologie z "Diagramu vrstev" k "Diagram závislostí".

**Architektura** nabídky teď obsahuje příkaz, který přímo vytvořit diagram závislostí:

![Položka závislostí v reálném čase na nabídku architektura](media/dep-validation-whatsnew-02.png)

... a názvy vlastností vrstvy v diagramu závislostí a jejich popisy, se změnily tak, aby byly lépe vystihuje:

![Aktualizovat názvy vlastností závislostí v reálném čase](media/dep-validation-whatsnew-03.png)

Nyní uvidíte dopad změny okamžitě v výsledky analýzy zadání stávajícího kódu v řešení pokaždé, když uložíte diagram. Nemusíte už čekat na dokončení příkazu "Ověřte závislosti".

Další podrobnosti najdete v tématu [tento příspěvek na blogu](https://blogs.msdn.microsoft.com/devops/2016/10/07/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Byly odebrány návrhářů UML

Návrhářů UML byly odebrány z této verze sady Visual Studio Enterprise.

* Diagramy UML se nyní zobrazují jako soubory XML
* V Průzkumníku modelu UML již existuje.
* Modelování projektu, které odkazy se už nebude používat pro ověřování závislostí
* "Odkazy vrstvy" uzlu v Průzkumníkovi řešení se už nebude zobrazovat.
* Akce sestavení "Ověřit" na diagram závislostí (vrstvy) se už používá – úloha sestavení byla odebrána.
* Struktura projektu je zachován z důvodu verzemi mezi verzemi
* Můžete stále otevřít, vytvořit, upravit a uložení diagram závislostí (Layer) ve formátu XML
* Pracovní položky sady TFS propojené s diagram závislostí (vrstvy) nejsou dostupné na návrhové ploše
* Propojení zpět z DSL nebo vrstvě se už nepodporuje.
* Rozšíření UML v sadě SDK modelování se už nepodporuje.

Ale podporují pro vizualizaci architektury .NET a C++ kód je k dispozici prostřednictvím [map kódu](map-dependencies-across-your-solutions.md)a významná vylepšení ověřování závislostí je popsáno výše.

Pokud jste uživatelem významné návrhářů UML, můžete nadále při rozhodování o alternativní nástroj pro vaše potřeby UML, použijte Visual Studio 2015 nebo starší verze.

Další podrobnosti najdete v tématu [tento příspěvek na blogu](https://blogs.msdn.microsoft.com/devops/2016/10/14/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="a-nameversionsupport-edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Podpora edice nástroje architektury a modelování

Visual Studio 2017 je k dispozici v několika edicích. Ne všechny tyto poskytovat podporu pro architektury a nástroje modelování. V následující tabulce jsou uvedeny dostupnost jednotlivých nástrojích.

|**Funkce**|**Enterprise edition**|**Edice Professional**|**Edice Community**|
|-|-|-|-|
|**Mapy kódu**|Ano|Pouze filtrování kód mapuje podporuje čtení map kódu, přidává nové obecné uzly a vytvoření nového orientovaného grafu z výběru.|-|
|**Diagramy závislostí**|Ano|Podporuje čtení diagramů závislostí.|Podporuje čtení diagramů závislostí.|
|**Řízených grafů** (diagramy DGML)|Ano|Ano|Ano|
|**Klonování kódu**|Ano|-|-|