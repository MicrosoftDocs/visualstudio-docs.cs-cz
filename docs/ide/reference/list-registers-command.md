---
title: Listovat registry – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a0e52f42e495c2bac5e80195d360096947210980
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748696"
---
# <a name="list-registers-command"></a>Listovat registry – příkaz
Zobrazí hodnotu vybraných registrů a umožňuje upravit seznam registrů, které se mají zobrazit.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Přepínače
/Display [{`register`&#124; `registerGroup`}...]

Zobrazí hodnoty zadaného `register` nebo `registerGroup`. Pokud není zadána žádná `register` ani `registerGroup`, zobrazí se výchozí seznam registrů. Pokud není zadán žádný přepínač, chování je stejné. Příklad:

`Debug.ListRegisters /Display eax`

je ekvivalentem

`Debug.ListRegisters eax`

/List

Zobrazí všechny skupiny registrů v seznamu.

/Watch [{`register`&#124; `registerGroup`}...]

Přidá do seznamu jednu nebo více `register` nebo `registerGroup` hodnot.

/Unwatch [{`register`&#124; `registerGroup`}...]

Odebere ze seznamu jednu nebo více `register` nebo `registerGroup` hodnot.

## <a name="remarks"></a>Poznámky
Alias `r` lze použít místo `Debug.ListRegisters`.

## <a name="example"></a>Příklad
V tomto příkladu se k zobrazení hodnot `Flags` skupiny registru používá `r` aliasu `Debug.ListRegisters`.

```cmd
r /Display Flags
```

## <a name="see-also"></a>Viz také:

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Základní informace k ladění: Okno Registry](../../debugger/debugging-basics-registers-window.md)
- [Postupy: Použití okna Registry](../../debugger/how-to-use-the-registers-window.md)