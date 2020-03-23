---
title: Refaktorovat kód Pythonu
description: Visual Studio usnadňuje refaktorování kódu Pythonu přejmenováním identifikátorů, extrahováním metod, přidáním importů a odebráním nepoužívaných importů.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: db1a551e20c597f98052471910bcb696c878675f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62429850"
---
# <a name="refactor-python-code"></a>Refaktorovat kód Pythonu

Visual Studio poskytuje několik příkazů pro automatickou transformaci a vyčištění zdrojového kódu Pythonu:

- [Přejmenování](#rename) přejmenuje vybranou třídu, metodu nebo název proměnné
- [Metoda Extrakce](#extract-method) vytvoří novou metodu z vybraného kódu.
- [Přidání importu](#add-import) poskytuje inteligentní značku pro přidání chybějícího importu
- [Odebrání nepoužitých importů](#remove-unused-imports) odstraní nevyužité importy.

## <a name="rename"></a>Přejmenovat

1. Klepněte pravým tlačítkem myši na identifikátor, který chcete přejmenovat, a vyberte možnost **Přejmenovat**, nebo umístěte stříšku do tohoto identifikátoru a vyberte příkaz **Upravit** > **přejmenování** > **Rename** **(F2).**
2. V zobrazeném dialogovém okně **Přejmenovat** zadejte nový název identifikátoru a vyberte **OK**:

   ![Přejmenovat výzvu pro nový název identiferu](media/code-refactor-rename-1.png)

3. V dalším dialogu vyberte soubory a instance v kódu, na které chcete přejmenovat; vyberte libovolnou jednotlivou instanci, abyste zobrazili náhled konkrétní změny:

   ![Přejmenovat dialogové okno pro výběr, kde se mají změny použít](media/code-refactor-rename-2.png)

4. Chcete-li provést změny v souborech zdrojového kódu, vyberte **použít.** (Tuto akci lze vrátit zpět.)

## <a name="extract-method"></a>Extrahování metody

1. Vyberte řádky kódu nebo výraz, který chcete extrahovat do samostatné metody.
2. Vyberte příkaz příkaz metody **Upravit** > **refaktorování** > **nebo** zadejte **Ctrl**+**R** > **M**.
3. V zobrazeném dialogovém okně zadejte nový název metody, označte, kam ji extrahovat, a vyberte všechny proměnné uzavření. Proměnné, které nejsou vybrány pro uzavření, se změní na argumenty metody:

   ![Dialogové okno Extrahovat metodu](media/code-refactor-extract-method-1.png)

4. Vyberte **OK** a kód je odpovídajícím způsobem upraven:

   ![Účinek extrakce metody](media/code-refactor-extract-method-2.png)

## <a name="add-import"></a>Přidat import

Když umístíte stříšku na identifikátor, který nemá informace o typu, Visual Studio poskytuje inteligentní značku (ikonu `import` žárovky vlevo od kódu), jejíž příkazy přidávají potřebné nebo `from ... import` příkazy:

![Přidání inteligentní značky importu](media/code-refactor-add-import-1.png)

Visual Studio `import` nabízí dokončení pro balíčky nejvyšší úrovně a moduly v aktuálním projektu a standardní knihovny. Visual Studio `from ... import` také nabízí dokončení pro podmoduly a podbalíčky, stejně jako členy modulu. Dokončení zahrnují funkce, třídy nebo exportovaná data. Výběrem jedné z možností přidáte příkaz do horní části souboru `from ... import` po jiných importech nebo do existujícího příkazu, pokud je stejný modul již importován.

![Výsledek přidání importu](media/code-refactor-add-import-2.png)

Visual Studio se pokusí odfiltrovat členy, které nejsou ve skutečnosti definovány v modulu, jako jsou moduly, které jsou importovány do jiného, ale nejsou podřízené modulu provádění importu. Například mnoho modulů `import sys` použít `from xyz import sys`spíše než , takže nevidíte `sys` dokončení pro import z jiných modulů `__all__` i v `sys`případě, že moduly chybí člen, který vylučuje .

Podobně Visual Studio filtruje funkce, které jsou importovány z jiných modulů nebo z předdefinovaného oboru názvů. Například pokud modul importuje `settrace` `sys` funkci z modulu, pak teoreticky můžete importovat z tohoto modulu. Ale je nejlepší použít `import settrace from sys` přímo, a tak Visual Studio nabízí toto prohlášení konkrétně.

Nakonec pokud by něco normálně být vyloučeny, ale má jiné hodnoty, které by byly zahrnuty (protože název byl přiřazen hodnotu v modulu, například), Visual Studio stále vylučuje import. Toto chování předpokládá, že hodnota by neměla být exportována, protože je definována v jiném modulu, a proto je další přiřazení pravděpodobně fiktivní hodnota, která také není exportována.

## <a name="remove-unused-imports"></a>Odebrání nepoužitých importů

Při psaní kódu je snadné skončit `import` s příkazy pro moduly, které nejsou používány vůbec. Vzhledem k tomu, že Visual Studio `import` analyzuje váš kód, může automaticky určit, zda je potřebný příkaz, a to tak, že se zobrazí, zda se importovaný název používá v rámci níže uvedeného oboru, kde k příkazu dochází.

Klepněte pravým tlačítkem myši na libovolné místo v editoru a vyberte **odebrat importy**, což vám dává možnost odebrat ze **všech oborů** nebo jen **aktuální obor**:

![Nabídka Odebrat importy](media/code-refactor-remove-imports-1.png)

Visual Studio pak provede příslušné změny kódu:

![Účinek odstranění dovozů](media/code-refactor-remove-imports-2.png)

Všimněte si, že Visual Studio neúčtuje pro tok řízení; použití názvu před `import` příkaz je zacházeno, jako kdyby název byl skutečně použit. Visual Studio také `from __future__` ignoruje všechny importy, importy, které jsou prováděny `from ... import *` uvnitř definice třídy, také z příkazů.
