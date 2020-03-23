---
title: Spustit – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6138c4cff33f0b2a4211439a01a058da59da811
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590277"
---
# <a name="start-command"></a>Spustit – příkaz
Začne ladit projekt po spuštění.

## <a name="syntax"></a>Syntaxe

```cmd
Debug.Start [address]
```

## <a name="arguments"></a>Argumenty
`address`

Nepovinný parametr. Adresa, na které program pozastaví provádění, podobně jako zarážka ve zdrojovém kódu. Tento argument je platný pouze v režimu ladění.

## <a name="remarks"></a>Poznámky
Příkaz **Start** při spuštění provede operaci RunToCursor na zadanou adresu.

## <a name="example"></a>Příklad
Tento příklad spustí ladicí program a ignoruje všechny výjimky, ke kterým dochází.

```cmd
>Debug.Start
```

## <a name="see-also"></a>Viz také

- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Příkazové okno](../../ide/reference/command-window.md)
- [Najít/Příkazové pole](../../ide/find-command-box.md)
- [Aliasy příkazů sady Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
