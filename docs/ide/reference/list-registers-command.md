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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e87b10a7827b5365b507abb2c72a21506e59c19e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568682"
---
# <a name="list-registers-command"></a>Listovat registry – příkaz
Zobrazí hodnotu vybraných registrů a umožní vám upravit seznam registrů, které se mají zobrazit.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Přepínače
/Zobrazit`register` [{ `registerGroup`&#124;}...]

Zobrazí hodnoty zadaného `register` `registerGroup`nebo . Pokud `register` není `registerGroup` zadán nebo je zadán, zobrazí se výchozí seznam registrů. Pokud není zadán žádný přepínač, chování je stejné. Například:

`Debug.ListRegisters /Display eax`

je ekvivalentem

`Debug.ListRegisters eax`

/Seznam

Zobrazí všechny skupiny registrů v seznamu.

/Watch`register` [{ `registerGroup`&#124;}...]

Přidá do `register` seznamu `registerGroup` jednu nebo více hodnot nebo hodnot.

/Zrušit sledování`register` [{&#124;`registerGroup`}...]

Odebere ze `register` seznamu `registerGroup` jednu nebo více hodnot nebo hodnoty.

## <a name="remarks"></a>Poznámky
Alias `r` lze použít místo `Debug.ListRegisters`.

## <a name="example"></a>Příklad
Tento příklad `Debug.ListRegisters` používá `r` alias k zobrazení hodnot `Flags`skupiny registrů .

```cmd
r /Display Flags
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Základní informace k ladění: okno registrů](../../debugger/debugging-basics-registers-window.md)
- [Postupy: Použití okna Registry](../../debugger/how-to-use-the-registers-window.md)
