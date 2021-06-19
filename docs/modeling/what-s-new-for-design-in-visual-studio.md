---
title: Novinky pro programátory v sadě Visual Studio 2017
description: Seznamte se s novými funkcemi pro návrh kódu, jako je živé ověřování závislostí, které jsou k dispozici Visual Studio 2017.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: ed67836507d8328a4ba394986564820c6af7308f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388097"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Novinky pro programátory v sadě Visual Studio 2017

## <a name="live-dependency-validation"></a>Živé ověřování závislostí

Odstranění nežádoucích závislostí je důležitou součástí správy technického dluhu. Visual Studio poskytuje živé ověřování závislostí, včetně přesných informací o problémech, jako je například jejich umístění. Živé ověřování závislostí plně využívá nové funkce v Seznam chyb a editoru.

![Živé ověřování závislostí v akci](media/dep-validation-whatsnew-01.png)

Prostředí pro vytváření se změnilo, aby ověřování závislostí bylo zjistitelné a přístupnější. Terminologie se změnila z "diagramu vrstev" na "diagram závislostí".

Nabídka **Architektura** teď obsahuje příkaz pro přímé vytvoření diagramu závislostí:

![Živá položka závislosti v nabídce Architektura](media/dep-validation-whatsnew-02.png)

Názvy a popisy vlastností vrstev byly změněny, aby byly smysluplnější:

![Aktualizované názvy vlastností živých závislostí](media/dep-validation-whatsnew-03.png)

Pokaždé, když diagram uložíte, okamžitě uvidíte dopad změn ve výsledcích analýzy pro aktuální kód v řešení. Nemusíte čekat na dokončení příkazu **Ověřit** závislosti.

Další podrobnosti najdete v tomto [blogovém příspěvku.](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/)

## <a name="uml-designers-have-been-removed"></a>Návrháři UML byli odebráni.

Návrháři UML byli odebráni z Visual Studio.

* Diagramy UML jsou nyní prezentovány jako soubory XML
* Průzkumník modelů UML už neexistuje
* Odkazy na projekt modelování se už k ověřování závislostí už nebudou používat.
* Uzel "Odkazy na vrstvy" v Průzkumník řešení se už nezobrazuje
* Akce sestavení Ověřit v diagramu závislosti (vrstvy) se už nebude používat – úloha sestavení byla odebrána.
* Struktura projektu je udržovaná pro přecházování mezi verzemi.
* Stále můžete otevřít, vytvořit, upravit a uložit diagram závislostí (vrstev) ve formátu XML.
* Pracovní položky sady TFS propojené s diagramem závislostí (vrstev) nejsou na návrhové ploše přístupné
* Back linking from to DSL or a Layer is no longer supported
* Rozšiřitelnost UML v sadě Modeling SDK se už nepodporuje

Podpora pro vizualizaci architektury kódu .NET a C++ je dostupná prostřednictvím [map kódu](map-dependencies-across-your-solutions.md).

Pokud jste významný uživatel návrhářů UML, můžete i nadále používat Visual Studio 2015 nebo starší verze při rozhodování o alternativní nástroj pro vaše potřeby UML.

Další podrobnosti najdete v tomto [blogovém příspěvku.](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Podpora edicí pro nástroje pro architekturu a modelování

Visual Studio je k dispozici v několika edicích. Ne všechny tyto možnosti podporují nástroje pro architekturu a modelování. Dostupnost jednotlivých nástrojů je znázorněna v následující tabulce.

|**Funkce**|**Edice Enterprise**|**Edice Professional**|**Community Edition**|
|-|-|-|-|
|**Mapy kódu**|Yes|Podporuje jenom čtení map kódu, filtrování map kódu, přidávání nových obecných uzlů a vytváření nového řízeného grafu z výběru.|-|
|**Diagramy závislostí**|Yes|Podporuje pouze čtení diagramů závislostí.|Podporuje pouze čtení diagramů závislostí.|
|**Řízené grafy** (diagramy DGML)|Yes|Yes|Yes|
|**Klonování kódu**|Yes|-|-|
