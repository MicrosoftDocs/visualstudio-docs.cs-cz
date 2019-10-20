---
title: Výpis vláken příkazu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.listthreads
helpviewer_keywords:
- ListThreads command
- list threads command
- Debug.ListThreads command
ms.assetid: 34b665c0-d46f-4c1a-a066-b678eba5ac54
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc11479901785b19235e0962d3ae90e552e5b33b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671142"
---
# <a name="list-threads-command"></a>Listovat vlákna – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zobrazí seznam vláken v aktuálním programu.

## <a name="syntax"></a>Syntaxe

```
Debug.ListThreads [index]
```

## <a name="arguments"></a>Arguments
 `index` volitelné. Vybere vlákno podle jeho indexu, aby bylo aktuální vlákno.

## <a name="remarks"></a>Poznámky
 Je-li tento parametr zadán, `index` argument označuje označené vlákno jako aktuální vlákno. V seznamu vedle aktuálního vlákna se zobrazí hvězdička (*).

## <a name="example"></a>Příklad

```
>Debug.ListThreads
```

## <a name="see-also"></a>Viz také
 [Seznam příkazů pro výpis zásobníku volání](../../ide/reference/list-call-stack-command.md) [příkazu](../../ide/reference/list-disassembly-command.md) příkazového řádku [pro příkaz v](../../ide/reference/command-window.md) sadě [Visual Studio příkazy](../../ide/reference/visual-studio-commands.md) [Najít/příkaz](../../ide/find-command-box.md) , [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
