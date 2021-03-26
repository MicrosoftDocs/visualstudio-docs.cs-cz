---
title: Pokyny pro umístění příkazů | Microsoft Docs
description: Seznamte se s pokyny a osvědčenými postupy pro umisťování příkazů v integrovaném vývojovém prostředí (IDE) sady Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 46aa6c341313a9d7c9d0a6d1666130d799ddc277
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057322"
---
# <a name="command-placement-guidelines"></a>Pokyny pro umístění příkazů
Osvědčené postupy pro umístění příkazů v integrovaném vývojovém prostředí (IDE) sady Visual Studio se liší v závislosti na velikosti sady příkazů. Příkazy jsou definovány a umístěny podle informací v souborech *. vsct* .

## <a name="best-practices-for-all-command-sets"></a>Osvědčené postupy pro všechny sady příkazů
 Pro každou sadu příkazů postupujte podle těchto pokynů:

- Připravte graf struktury příkazu předem. Identifikujte příkazy, pole se seznamem, skupiny příkazů a místní nabídky, které budou použity ve více než jednom umístění.

- Příkazy, které se zobrazují ve stejné skupině, by měly souviset.

- Přijatelné jsou skupiny, které obsahují jenom jeden příkaz.

- Balíčky by neměly přidávat spoustu příkazů do stávajících nabídek sady Visual Studio. Místo toho by se měly vytvořit nabídky nebo podnabídky pro hostování nových příkazů.

- Když zadáte příkaz do existující nabídky, pojmenujte příkaz tak, aby jeho účel byl jasný a nebude zaměněn s existujícími příkazy.

## <a name="best-practices-for-small-command-sets"></a>Osvědčené postupy pro malé sady příkazů
 Pokud vyvíjíte VSPackage, který obsahuje pouze několik příkazů, postupujte také podle následujících pokynů:

- Pokud je to možné, použijte [nadřazený](../../extensibility/parent-element.md) element příkazu, pole se seznamem, skupinu nebo podřízenou nabídku k umístění do příslušné skupiny.

- Přiřaďte tyto skupiny k nabídkám, které zobrazuje VSPackage.

- Nadřazený objekt podřízené nabídky nebo příkazu musí být prvek [skupiny](../../extensibility/group-element.md) . Přiřaďte příkazy a podřízené nabídky do skupin a potom přiřaďte skupiny k nadřazeným nabídkám.

- Příkaz můžete umístit do dalších skupin přidáním oddílu prvku [CommandPlacements](../../extensibility/commandplacements-element.md) po definování příkazu a následným přidáním do `CommandPlacements` prvku element [CommandPlacement](../../extensibility/commandplacement-element.md) pro každou další skupinu.

## <a name="best-practices-for-large-command-sets"></a>Osvědčené postupy pro velké sady příkazů
 Pokud VSPackage bude mít mnoho příkazů, které se zobrazí v několika kontextech, postupujte také podle těchto pokynů:

- Vytváření nabídek, skupin a příkazů pro samoobslužné vytváření nadřazených objektů. To znamená, že nepřiřazujte `Parent` element v definici položky.

- Použijte `CommandPlacement` položky prvků v `CommandPlacements` oddílu element pro vložení nabídek, skupin a příkazů do svých nadřazených nabídek a skupin.

- V `CommandPlacements` oddílu element by měly být položky, které naplňují danou nabídku nebo skupinu, sousedící s sebou. Tato pomůcka pomáhá číst a usnadňuje `Priority` určování pořadí.

## <a name="see-also"></a>Viz také
- [Jak prvky VSPackage přidávají prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Soubory tabulek příkazů sady Visual Studio (. vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
