---
title: Pokyny pro umístění příkazů | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, small command sets
- small command sets
- command sets
ms.assetid: 63b3478e-e08a-420b-a0ec-76767e0cb289
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 021a5fd9f9931e3041a431d211c8ab49978bbbab
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709571"
---
# <a name="command-placement-guidelines"></a>Pokyny pro umístění příkazů
Doporučené postupy pro umístění příkazů v integrovaném vývojovém prostředí sady Visual Studio (IDE) se liší v závislosti na velikosti sady příkazů. Příkazy jsou definovány a umístěny podle informací v *souborech .vsct.*

## <a name="best-practices-for-all-command-sets"></a>Doporučené postupy pro všechny sady příkazů
 Pro každou sadu příkazů postupujte podle následujících pokynů:

- Připravte graf struktury příkazů předem. Identifikujte příkazy, pole se seznamem, skupiny příkazů a místní nabídky, které budou použity na více než jednom místě.

- Příkazy, které se zobrazí ve stejné skupině, by měly souviset.

- Skupiny, které obsahují pouze jeden příkaz jsou přijatelné.

- Balíčky by neměly přidávat velké množství příkazů do existujících nabídek sady Visual Studio. Místo toho by měly vytvořit nabídky nebo podnabídky pro hostování nových příkazů.

- Když vložíte příkaz do existující nabídky, pojmenujte jej tak, aby jeho účel byl jasný a nebyl zaměňován s existujícími příkazy.

## <a name="best-practices-for-small-command-sets"></a>Doporučené postupy pro malé sady příkazů
 Pokud vyvíjíte VSPackage, který má jen několik příkazů, postupujte také podle těchto pokynů:

- Pokud je to možné, použijte [prvek Nadřazený](../../extensibility/parent-element.md) příkaz, pole se seznamem, skupinu nebo podřízenou nabídku, abyste jej umístili do příslušné skupiny.

- Přiřaďte tyto skupiny k nabídkám zobrazeným balíčkem VSPackage.

- Nadřazená podřízená nabídka nebo příkaz musí být prvek [Skupiny.](../../extensibility/group-element.md) Přiřaďte skupinám příkazy a podřízené nabídky a potom je přiřaďte k nadřazeným nabídkám.

- Příkaz můžete umístit do dalších skupin přidáním oddílu elementu [CommandPlacements](../../extensibility/commandplacements-element.md) za `CommandPlacements` definici příkazu a následným přidáním prvku [elementu CommandPlacement](../../extensibility/commandplacement-element.md) pro každou další skupinu.

## <a name="best-practices-for-large-command-sets"></a>Doporučené postupy pro velké sady příkazů
 Pokud váš VSPackage bude mít mnoho příkazů, které se zobrazí ve více kontextech, postupujte také podle těchto pokynů:

- Vytvořte nabídky, skupiny a příkazy self-parenting. To znamená nepřiřazovat `Parent` prvek v definici položky.

- Pomocí `CommandPlacement` položek prvků `CommandPlacements` v části prvku můžete nabídky, skupiny a příkazy umístit do nadřazených nabídek a skupin.

- V `CommandPlacements` části prvku by měly být položky, které naplní danou nabídku nebo skupinu, vedle sebe. To pomáhá čitelnost `Priority` a usnadňuje určování pořadí.

## <a name="see-also"></a>Viz také
- [Jak VSPackages přidat prvky uživatelského rozhraní](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Soubory příkazů sady Visual Studio (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
