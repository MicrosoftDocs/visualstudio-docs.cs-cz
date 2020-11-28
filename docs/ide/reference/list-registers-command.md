---
title: Listovat registry – příkaz
description: Přečtěte si o příkazu seznam registrů a o tom, jak zobrazuje hodnotu vybraných registrů, a umožňuje upravit seznam registrů, které se mají zobrazit.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 5459ded60ea90ae00a3f943f829065a82548d160
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305298"
---
# <a name="list-registers-command"></a>Listovat registry – příkaz
Zobrazí hodnotu vybraných registrů a umožňuje upravit seznam registrů, které se mají zobrazit.

## <a name="syntax"></a>Syntax

```cmd
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Přepínače
/Display [{ `register`&#124;`registerGroup` }...]

Zobrazí hodnoty zadaného `register` nebo `registerGroup` . Pokud `register` `registerGroup` není zadán, nebo je zadán, zobrazí se výchozí seznam registrů. Pokud není zadán žádný přepínač, chování je stejné. Příklad:

`Debug.ListRegisters /Display eax`

je ekvivalentem

`Debug.ListRegisters eax`

/List

Zobrazí všechny skupiny registrů v seznamu.

/Watch [{ `register`&#124;`registerGroup` }...]

Přidá do seznamu jednu nebo více `register` `registerGroup` hodnot nebo.

/Unwatch [{ `register`&#124;`registerGroup` }...]

Odebere ze seznamu jednu nebo více `register` `registerGroup` hodnot nebo.

## <a name="remarks"></a>Poznámky
Alias `r` lze použít místo `Debug.ListRegisters` .

## <a name="example"></a>Příklad
Tento příklad používá `Debug.ListRegisters` alias `r` k zobrazení hodnot skupiny registrů `Flags` .

```cmd
r /Display Flags
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Základní informace k ladění: okno registrů](../../debugger/debugging-basics-registers-window.md)
- [Postupy: Použití okna Registry](../../debugger/how-to-use-the-registers-window.md)
