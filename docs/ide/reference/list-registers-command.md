---
title: Listovat registry – příkaz
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listregisters
helpviewer_keywords:
- list registers command
- Debug.ListRegisters command
- ListRegisters command
ms.assetid: 19a9d789-f6c9-46b3-b1f6-4934fc33e055
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce91abde91edf989b33c476b042abaf16c685df0
ms.sourcegitcommit: fe5a72bc4c291500f0bf4d6e0778107eb8c905f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33704899"
---
# <a name="list-registers-command"></a>Listovat registry – příkaz
Zobrazí hodnotu vybrané zaregistruje a umožňuje upravit seznam registruje zobrazit.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.ListRegisters [/Display [{register|registerGroup}...]] [/List]
[/Watch [{register|registerGroup}...]]
[/Unwatch [{register|registerGroup}...]]
```

## <a name="switches"></a>Přepínače
 / Zobrazení [{`register`&#124;`registerGroup`}...]

 Zobrazí hodnoty zadaného `register` nebo `registerGroup`. Pokud žádné `register` nebo `registerGroup` je zadán, zobrazí se výchozí seznam Registry. Pokud není zadán žádný přepínač, chování je stejné. Příklad:

 `Debug.ListRegisters /Display eax`

 je ekvivalentem

 `Debug.ListRegisters eax`

 Nebo jejich výpisu

 Zobrazí všechny skupiny registru v seznamu.

 Nebo si pusťte [{`register`&#124;`registerGroup`}...]

 Přidá jeden nebo více `register` nebo `registerGroup` hodnoty do seznamu.

 / Unwatch [{`register`&#124;`registerGroup`}...]

 Odebere jeden nebo více `register` nebo `registerGroup` hodnoty ze seznamu.

## <a name="remarks"></a>Poznámky
 Alias `r` lze místě `Debug.ListRegisters`.

## <a name="example"></a>Příklad
 Tento příklad používá `Debug.ListRegisters` alias `r` k zobrazení hodnot registrace skupiny `Flags`.

```cmd
r /Display Flags
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Základní informace k ladění: Okno registrů](../../debugger/debugging-basics-registers-window.md)
- [Postupy: použití okna registry](../../debugger/how-to-use-the-registers-window.md)