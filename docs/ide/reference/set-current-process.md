---
title: Nastavit aktuální proces
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Debug.SetCurrentProcess command
- Set Current Process command
ms.assetid: 1e016ebd-aadd-411f-a606-03bf69d3f8aa
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6545962f374ea850808c11a3c9c79e0a04602027
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655475"
---
# <a name="set-current-process"></a>Nastavit aktuální proces
Nastaví zadaný proces jako aktivní proces v ladicím programu.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.SetCurrentProcess index
```

## <a name="arguments"></a>Arguments
`index`

Požadováno. Index procesu.

## <a name="remarks"></a>Poznámky
Můžete se připojit k více procesům při ladění, ale v Dubber je v daném okamžiku aktivní pouze jeden proces. K nastavení aktivního procesu lze použít příkaz `SetCurrentProcess`.

## <a name="example"></a>Příklad

```cmd
>Debug.SetCurrentProcess 1
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)