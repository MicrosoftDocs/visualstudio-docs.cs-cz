---
title: Refaktoring Python Code
description: Visual Studio usnadňuje refaktorující kód v jazyce Python přejmenováním identifikátorů, extrakcí metod, přidáním importů a odebráním nepoužívaných importů.
ms.date: 03/13/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 8eb46f324359549d7f74e8edd90d3056820e234e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902389"
---
# <a name="refactor-python-code"></a>Refaktoring Python Code

Visual Studio poskytuje několik příkazů pro automatické transformování a mazání zdrojového kódu v Pythonu:

- [Přejmenování](#rename) Přejmenuje vybranou třídu, metodu nebo název proměnné.
- [Metoda Extract](#extract-method) vytvoří novou metodu z vybraného kódu.
- [Přidat import](#add-import) poskytuje inteligentní značku pro přidání chybějícího importu.
- [Odebrání nepoužívaných importů](#remove-unused-imports) odebere nepoužívané importy.

## <a name="rename"></a>přejmenování

1. Klikněte pravým tlačítkem myši na identifikátor, který chcete přejmenovat, vyberte možnost **Přejmenovat**, nebo umístěte blikající kurzor do tohoto identifikátoru a vyberte příkaz **Upravit**  >  **refaktor**  >  **Rename** nabídky (**F2**).
2. V zobrazeném dialogovém okně pro **přejmenování** zadejte nový název identifikátoru a vyberte **OK**:

   ![Přejmenování výzvy k zadání nového názvu identifikátorem](media/code-refactor-rename-1.png)

3. V dalším dialogovém okně vyberte soubory a instance v kódu, pro které chcete použít přejmenování. Vyberte jakoukoli jednotlivou instanci, pro kterou chcete zobrazit náhled konkrétní změny:

   ![Dialogové okno Přejmenovat pro výběr, kde se mají změny použít](media/code-refactor-rename-2.png)

4. Chcete-li provést změny v souborech zdrojového kódu, vyberte možnost **použít** . (Tuto akci je možné vrátit zpět.)

## <a name="extract-method"></a>Extrahování metody

1. Vyberte řádky kódu nebo výraz, který se má extrahovat do samostatné metody.
2. Vyberte příkaz nabídky **Upravit**  >  **Refaktorovat**  >  **extrakci metody** nebo zadejte **CTRL** + **R**  >  **M**.
3. V dialogovém okně, které se zobrazí, zadejte nový název metody, určete, kam se má extrahovat, a vyberte všechny proměnné ukončení. Proměnné, které nejsou vybrány pro uzavření, jsou přeměněny na argumenty metody:

   ![Dialogové okno extrakce metody](media/code-refactor-extract-method-1.png)

4. Vyberte **OK** a kód se upraví odpovídajícím způsobem:

   ![Účinek extrakce metody](media/code-refactor-extract-method-2.png)

## <a name="add-import"></a>Přidat import

Když umístíte blikající kurzor na identifikátor, který neobsahuje informace o typu, poskytuje Visual Studio inteligentní značku (ikona žárovky vlevo od kódu), jejíž příkazy přidávají potřebný `import` `from ... import` příkaz nebo:

![Přidat inteligentní značku importu](media/code-refactor-add-import-1.png)

Visual Studio nabízí `import` dokončování pro balíčky nejvyšší úrovně a moduly v aktuálním projektu a ve standardní knihovně. Sada Visual Studio také nabízí `from ... import` dokončování pro dílčí moduly a dílčí balíčky i členy modulů. Doplňování zahrnují funkce, třídy nebo exportovaná data. Když vyberete jednu z možností, přidá se příkaz do horní části souboru po ostatních importech nebo do existujícího `from ... import` příkazu, pokud je už stejný modul naimportovaný.

![Výsledek přidání importu](media/code-refactor-add-import-2.png)

Visual Studio se pokusí odfiltrovat členy, které nejsou ve skutečnosti definované v modulu, například moduly, které jsou importované do jiného, ale nejsou podřízené modulu, který provádí import. Mnoho modulů například používá `import sys` spíše než `from xyz import sys` , takže se nezobrazuje dokončování pro import `sys` z jiných modulů, a to i v případě, že v modulech chybí `__all__` člen, který je vyloučený `sys` .

Podobně aplikace Visual Studio filtruje funkce, které jsou importovány z jiných modulů nebo z předdefinovaného oboru názvů. Například pokud modul importuje `settrace` funkci z `sys` modulu, pak je možné, že ji naimportujete z tohoto modulu. Je ale nejvhodnější použít `import settrace from sys` přímo, takže Visual Studio nabízí tento příkaz konkrétně.

Nakonec, pokud by se něco normálně vyloučilo, ale má další hodnoty, které by se měly zahrnout (protože byl tomuto názvu přiřazena hodnota v modulu), Visual Studio přesto import vyloučí. Toto chování předpokládá, že hodnota by neměla být exportována, protože je definována v jiném modulu, a proto je další přiřazení pravděpodobně fiktivní hodnota, která je také exportována.

## <a name="remove-unused-imports"></a>Odebrat nepoužívané importy

Při psaní kódu je snadné ukončit `import` příkazy pro moduly, které nejsou používány vůbec. Vzhledem k tomu, že Visual Studio analyzuje váš kód, může automaticky určit, zda je `import` třeba použít importovaný název v rámci následujícího oboru, kde se vyskytuje příkaz.

V Editoru klikněte pravým tlačítkem myši a vyberte možnost **Odebrat importy**, které vám umožní odebrat ze **všech oborů** nebo jenom z **aktuálního rozsahu**:

![Nabídka odebrat importy](media/code-refactor-remove-imports-1.png)

Visual Studio pak provede příslušné změny kódu:

![Efekt odebírání importů](media/code-refactor-remove-imports-2.png)

Všimněte si, že Visual Studio nezohledňuje tok řízení; použití názvu před provedením `import` příkazu, jako by byl název skutečně použit. Visual Studio také ignoruje všechny `from __future__` importy, importy prováděné uvnitř definice třídy a také z `from ... import *` příkazů.
