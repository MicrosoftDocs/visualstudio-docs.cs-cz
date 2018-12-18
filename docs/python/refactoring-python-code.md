---
title: Refaktorování kódu Pythonu
description: Visual Studio umožňuje snadno Refaktorujte kód Pythonu přejmenováním identifikátory, extrahování metody, přidání importy a odebrání nepoužívaných importuje.
ms.date: 11/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7293e966f937368df62dc9fa0049ac1d75a19b45
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063014"
---
# <a name="refactor-python-code"></a>Refaktorování kódu Pythonu

Visual Studio obsahuje několik příkazů pro automaticky transformaci a čištění zdrojový kód Pythonu:

- [Přejmenovat](#rename) Přejmenuje vybrané třídy, metody nebo název proměnné
- [Extrahovat metodu](#extract-method) vytvoří novou metodu z vybraného kódu
- [Přidat import](#add-import) poskytuje inteligentní značky, chcete-li přidat chybějící importu
- [Odebere nevyužité importy](#remove-unused-imports) odebere nevyužité importy

## <a name="rename"></a>přejmenování

1. Klikněte pravým tlačítkem na identifikátor, který chcete přejmenovat a vyberte **přejmenovat**, nebo umístěte blikající kurzor do identifikátoru a vyberte **upravit** > **Refaktorovat**  >  **Přejmenovat** příkazu nabídky (**F2**).
2. V **přejmenovat** dialogové okno, které se zobrazí, zadejte nový název pro identifikátor, vyberte **OK**:

   ![Přejmenovat výzva k zadání nového názvu identifikátor](media/code-refactor-rename-1.png)

3. V dalším dialogovém okně vyberte soubory a instancí ve vašem kódu, pro kterou chcete použít přejmenování; Vyberte všechny jednotlivé instance na konkrétní změně ve verzi preview:

   ![Přejmenování dialogového okna a vyberte umístění pro použití změn](media/code-refactor-rename-2.png)

4. Vyberte **použít** provést změny souborů se zdrojovým kódem. (Tato akce může být vrátit zpět.)

## <a name="extract-method"></a>Extrahování metody

1. Vyberte řádky kódu nebo výraz, který se extrahuje do samostatné metodě.
2. Vyberte **upravit** > **Refaktorovat** > **extrahovat metodu** příkaz nabídky nebo typ **Ctrl** + **R** > **M**.
3. V dialogovém okně, které se zobrazí zadejte nový název metody, uveďte, kam extrahujte ho do a vyberte všechny proměnné uzavření. Proměnné není vybrána pro uzavření jsou převedena na argumenty metody:

   ![Extrahovat metodu dialogového okna](media/code-refactor-extract-method-1.png)

4. Vyberte **OK** a kód je odpovídajícím způsobem upravit:

   ![Účinek extrahování metody](media/code-refactor-extract-method-2.png)

## <a name="add-import"></a>Přidat import

Když umístíte blikající kurzor na identifikátor, chybí typ informací, Visual Studio poskytuje inteligentní značky (ikonu žárovky nalevo od kódu), jehož příkazy přidat nezbytné `import` nebo `from ... import` – příkaz:

![Přidání inteligentních značek importu](media/code-refactor-add-import-1.png)

Visual Studio nabízí `import` dokončování pro nejvyšší úrovně balíčky a moduly v aktuálním projektu a standardní knihovny. Visual Studio také nabízí `from ... import` dokončování pro dílčí moduly a dílčí balíčky, jakož i modul členy. Dokončování zahrnují funkce, třídy nebo exportovaná data. Vyberte jednu z možností přidá příkaz tak, aby v horní části souboru po další imports nebo do existujícího `from ... import` příkazu, pokud již byla naimportována stejného modulu.

![Výsledkem přidání importu](media/code-refactor-add-import-2.png)

Visual Studio se pokusí vyfiltrovat členy, které nejsou ve skutečnosti definovány v modulu, jako jsou moduly, které jsou importovány do jiné, ale nejsou podřízené objekty daného modulu to import. Například mnoho moduly se řídí `import sys` spíše než `from xyz import sys`, takže se nezobrazí dokončení pro import `sys` z jiných modulů, i když nebyly nalezeny moduly `__all__` člena, který vylučuje `sys`.

Podobně Visual Studio filtry funkce, které jsou importovány z jiných modulů nebo z předdefinovaných oboru názvů. Například pokud importuje modul `settrace` funkci `sys` modulu, pak teoreticky naimportovat z tohoto modulu. Je nejvhodnější použít, ale `import settrace from sys` přímo, a proto nabízí Visual Studio, který tento příkaz konkrétně.

Nakonec, pokud se něco by normálně vyloučeny, ale má jiné hodnoty, které budou vloženy (protože název byla přidělena hodnota v modulu, třeba), Visual Studio stále vyloučí importu. Toto chování se předpokládá, že hodnota by neměla možné exportovat, protože je definována v jiném modulu, a proto je pravděpodobně fiktivní hodnoty, které se exportují také další přiřazení.

## <a name="remove-unused-imports"></a>Odebere nevyužité importy

Při psaní kódu, je snadné skončit s `import` příkazy pro moduly, které nejsou vůbec nepoužívá. Vzhledem k tomu, že sada Visual Studio analyzuje váš kód, může automaticky zjistit, jestli `import` příkazu je potřeba pro pohledu na tom, jestli importované název se používá v rámci oboru níže, kde dochází k příkazu.

Klikněte pravým tlačítkem na libovolné místo v editoru a vyberte **odebrat importy**, který poskytuje možnosti odebrání **všechny obory** nebo jenom **aktuální obor**:

![Odebrat příkaz imports](media/code-refactor-remove-imports-1.png)

Visual Studio pak provede odpovídající změny kódu:

![Efekt odebrat importy](media/code-refactor-remove-imports-2.png)

Všimněte si, že pro tok řízení; není účet sady Visual Studio pomocí názvu před `import` příkaz je zpracováván stejně, jako název ve skutečnosti byl použit. Visual Studio také ignoruje všechny `from __future__` importy, importy, které se provádí v rámci definice třídy, také z `from ... import *` příkazy.
