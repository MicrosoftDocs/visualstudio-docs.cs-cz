---
title: Listovat vlákna – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c437b91fea5e3087de8b22cb72a2f20ad421bead
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610489"
---
# <a name="list-threads-command"></a>Listovat vlákna – příkaz
Zobrazí seznam vláken v aktuálním programu.

## <a name="syntax"></a>Syntaxe

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Arguments
`index`

Volitelné. Vybere vlákno podle jeho indexu, aby bylo aktuální vlákno.

## <a name="remarks"></a>Poznámky
Je-li tento parametr zadán, `index` argument označuje označené vlákno jako aktuální vlákno. V seznamu vedle aktuálního vlákna se zobrazí hvězdička (*).

## <a name="example"></a>Příklad

```
>Debug.ListThreads
```

## <a name="see-also"></a>Viz také

- [Příkaz Listovat zásobník volání](../../ide/reference/list-call-stack-command.md)
- [Příkaz Zobrazit zpětný překlad](../../ide/reference/list-disassembly-command.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)