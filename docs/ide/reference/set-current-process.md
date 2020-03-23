---
title: Nastavit aktuální proces
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a3440c66d79fef3eac3744681870c9ce1ed0e97b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593548"
---
# <a name="set-current-process"></a>Nastavit aktuální proces
Nastaví zadaný proces jako aktivní proces v ladicím programu.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Argumenty
`index`

Povinná hodnota. Index procesu.

## <a name="remarks"></a>Poznámky
Při ladění můžete připojit k více procesům, ale v dubberu je v daném okamžiku aktivní pouze jeden proces. Pomocí příkazu `SetCurrentProcess` můžete nastavit aktivní proces.

## <a name="example"></a>Příklad

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
