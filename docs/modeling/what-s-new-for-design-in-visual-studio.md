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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302950"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Novinky pro programátory v sadě Visual Studio 2017

## <a name="live-dependency-validation"></a>Ověření živé závislosti

Odstranění nežádoucích závislostí je důležitou součástí správy technického dluhu. Visual Studio poskytuje živé ověření závislostí, včetně přesných informací o problémech, například kde jsou umístěny. Ověření živé závislosti využívá plné výhody nových funkcí v seznamu chyb a v editoru.

![Ověření živé závislosti v akci](media/dep-validation-whatsnew-01.png)

Prostředí pro vytváření se změnilo tak, aby bylo ověřování závislostí více zjistitelné a přístupnější. Terminologie se změnila z "Diagram vrstev" na "Diagram závislostí".

Nabídka **Architektura** nyní obsahuje příkaz pro přímé vytvoření diagramu závislostí:

![Položka živé závislosti v nabídce Architektura](media/dep-validation-whatsnew-02.png)

Názvy a popisy vlastností vrstvy byly změněny tak, aby byly smysluplnější:

![Aktualizované názvy vlastností živé závislosti](media/dep-validation-whatsnew-03.png)

Okamžitě uvidíte dopad změn ve výsledcích analýzy pro aktuální kód v řešení při každém uložení diagramu. Nemusíte čekat na dokončení příkazu **Ověřit závislosti.**

Další podrobnosti naleznete v [tomto příspěvku blogu](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Návrháři UML byli odebráni.

Návrháři UML byly odebrány z sady Visual Studio.

* Diagramy UML jsou nyní prezentovány jako soubory XML
* Průzkumník modelů UML již neexistuje.
* Odkazy na projekty modelování se již nepoužívají pro ověření závislostí.
* Uzel Odkazy na vrstvy v Průzkumníku řešení se již nezobrazuje
* Akce sestavení "Ověřit" v diagramu závislostí (vrstva) se již nepoužívá – úloha sestavení byla odebrána
* Struktura projektu je udržována pro kruhové zakopnutí mezi verzemi
* Diagram závislostí (vrstva) můžete stále otevírat, vytvářet, upravovat a ukládat jako XML.
* Pracovní položky TFS propojené s diagramem závislostí (vrstva) nejsou přístupné na návrhové ploše
* Zpětné propojení z DSL nebo vrstvy již není podporováno
* Rozšiřitelnost UML v sada Model SDK již není podporována

Podpora pro vizualizaci architektury kódu .NET a C++ je k dispozici prostřednictvím [map kódu](map-dependencies-across-your-solutions.md).

Pokud jste významným uživatelem návrhářů UML, můžete pokračovat v používání visual studio 2015 nebo starší verze, zatímco se rozhodnete pro alternativní nástroj pro vaše potřeby UML.

Další podrobnosti naleznete v [tomto příspěvku blogu](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Podpora edice pro architekturu a nástroje pro modelování

Visual Studio je k dispozici v několika edicích. Ne všechny tyto poskytují podporu pro architekturu a modelování nástroje. V následující tabulce je uvedena dostupnost jednotlivých nástrojů.

|**Funkce**|**Edice Enterprise**|**Profesionální edice**|**Komunitní vydání**|
|-|-|-|-|
|**Mapy kódu**|Ano|Podporuje pouze čtení map kódu, filtrování map kódu, přidávání nových obecných uzlů a vytváření nového řízeného grafu z výběru.|-|
|**Diagramy závislostí**|Ano|Podporuje pouze čtení diagramů závislostí.|Podporuje pouze čtení diagramů závislostí.|
|**Orientované grafy** (diagramy DGML)|Ano|Ano|Ano|
|**Klon kódu**|Ano|-|-|
