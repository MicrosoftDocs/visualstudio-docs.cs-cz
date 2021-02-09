---
title: Listovat vlákna – příkaz
description: Přečtěte si o příkazu vypsat vlákna a o tom, jak zobrazuje seznam vláken v aktuálním programu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f3abcd7182c8bb5b94b2f35a9463f845cc6bb5bd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919384"
---
# <a name="list-threads-command"></a>Listovat vlákna – příkaz
Zobrazí seznam vláken v aktuálním programu.

## <a name="syntax"></a>Syntaxe

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Argumenty
`index`

Nepovinný parametr. Vybere vlákno podle jeho indexu, aby bylo aktuální vlákno.

## <a name="remarks"></a>Poznámky
Je-li tento `index` parametr zadán, argument označí označené vlákno jako aktuální vlákno. V seznamu vedle aktuálního vlákna se zobrazí hvězdička (*).

## <a name="example"></a>Příklad

```
>Debug.ListThreads
```

## <a name="see-also"></a>Viz také

- [Listovat zásobník volání – příkaz](../../ide/reference/list-call-stack-command.md)
- [Výpis zpětného překladu příkazu](../../ide/reference/list-disassembly-command.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Pole Najít/příkaz](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
