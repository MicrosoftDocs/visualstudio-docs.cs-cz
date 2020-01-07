---
title: Cesta k symbolu – příkaz
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed8ec8e7f990a4a2c5d943a15a105faa5ab23572
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589380"
---
# <a name="symbol-path-command"></a>Cesta k symbolu – příkaz
Nastaví seznam adresářů pro ladicí program pro hledání symbolů.

## <a name="syntax"></a>Syntaxe

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Arguments
`pathname`

Volitelné. Středníkem oddělený seznam cest pro ladicí program pro hledání symbolů.

## <a name="remarks"></a>Poznámky
Pokud není zadán žádný `pathname`, příkaz vypíše aktuální cesty k symbolům.

## <a name="example"></a>Příklad
Tento příklad přidá dvě cesty do seznamu adresářů symbolů.

```
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2
```

## <a name="example"></a>Příklad
V tomto příkladu se zobrazí seznam aktuálních cest k symbolům oddělený středníkem.

```
Debug.SymbolPath
```

## <a name="see-also"></a>Viz také:

- [Příkazové okno](../../ide/reference/command-window.md)
- [Příkazy sady Visual Studio](../../ide/reference/visual-studio-commands.md)
