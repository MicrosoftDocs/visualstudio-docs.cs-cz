---
title: Cesta k symbolu – příkaz | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d02d4cfede6ed3499d09ff58e4454c1ef9cbe0d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651007"
---
# <a name="symbol-path-command"></a>Cesta k symbolu – příkaz
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nastaví seznam adresářů ladicího programu pro hledání symbolů.

## <a name="syntax"></a>Syntaxe

```
Debug.SymbolPath pathname1;pathname2;... pathnameN
```

## <a name="arguments"></a>Arguments
 `pathname` volitelné. Středníkem oddělený seznam cest pro ladicí program pro hledání symbolů.

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

## <a name="see-also"></a>Viz také
 Příkazy [příkazového](../../ide/reference/command-window.md) řádku sady [Visual Studio](../../ide/reference/visual-studio-commands.md)
