---
title: Novinky pro programátory v sadě Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 6f81cc32604abe6d90ac0d263574e97df35c63bd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593496"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Novinky pro programátory v sadě Visual Studio 2017

## <a name="live-dependency-validation"></a>Ověřování závislostí v reálném čase

Odebrání nechtěné závislosti je důležitou součástí správy technický dluh. Visual Studio poskytuje živé ověření závislostí, včetně podrobných informací o problémech, například místa, kde se nacházejí. Ověřování závislostí v reálném čase má plné výhody pro nové funkce Seznam chyb a editoru.

![Ověřování závislostí v reálném čase v akci](media/dep-validation-whatsnew-01.png)

Prostředí pro vytváření obsahu se změnilo tak, aby ověřování závislostí bylo více Zjistitelnější a bylo dostupné. Terminologie se změnila z "diagramu vrstev" na "Diagram závislostí".

**Architektura** nabídky teď obsahuje příkaz, který přímo vytvořit diagram závislostí:

![Položka závislostí v reálném čase na nabídku architektura](media/dep-validation-whatsnew-02.png)

Názvy vlastností vrstvy a popisy byly změněny, aby byly smysluplnější:

![Aktualizovat názvy vlastností závislostí v reálném čase](media/dep-validation-whatsnew-03.png)

Okamžitě uvidíte dopad změn ve výsledcích analýzy pro aktuální kód v řešení pokaždé, když diagram uložíte. Nemusíte čekat na dokončení příkazu **ověřit závislosti** .

Další podrobnosti najdete v tématu [tento příspěvek na blogu](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Byly odebrány návrhářů UML

Návrháři UML byly ze sady Visual Studio odebrány.

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

Podpora pro vizualizaci architektury rozhraní .NET a C++ kódu je k dispozici prostřednictvím [map kódu](map-dependencies-across-your-solutions.md).

Pokud jste uživatelem významné návrhářů UML, můžete nadále při rozhodování o alternativní nástroj pro vaše potřeby UML, použijte Visual Studio 2015 nebo starší verze.

Další podrobnosti najdete v tématu [tento příspěvek na blogu](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="a-nameversionsupport-edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Podpora edice nástroje architektury a modelování

Visual Studio je k dispozici v několika edicích. Ne všechny tyto poskytovat podporu pro architektury a nástroje modelování. V následující tabulce jsou uvedeny dostupnost jednotlivých nástrojích.

|**Funkce**|**Enterprise edition**|**Edice Professional**|**Edice Community**|
|-|-|-|-|
|**Mapy kódu**|Ano|Pouze filtrování kód mapuje podporuje čtení map kódu, přidává nové obecné uzly a vytvoření nového orientovaného grafu z výběru.|-|
|**Diagramy závislostí**|Ano|Podporuje čtení diagramů závislostí.|Podporuje čtení diagramů závislostí.|
|**Řízených grafů** (diagramy DGML)|Ano|Ano|Ano|
|**Klonování kódu**|Ano|-|-|
